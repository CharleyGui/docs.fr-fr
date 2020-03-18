---
title: Créer des bibliothèques de clients gRPC - gRPC pour WCF Developers
description: Discussion des bibliothèques/forfaits clients partagés pour les services gRPC.
ms.date: 09/02/2019
ms.openlocfilehash: bb58cb3cda4b0cbb3a5d34129961349bcb0093e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79401668"
---
# <a name="create-grpc-client-libraries"></a>Créer des bibliothèques de clients gRPC

Il n’est pas nécessaire de distribuer des bibliothèques clients pour une application gRPC. Vous pouvez créer une `.proto` bibliothèque partagée de fichiers au sein de votre organisation, et d’autres équipes peuvent utiliser ces fichiers pour générer du code client dans leurs propres projets. Mais si vous avez un référentiel NuGet privé et que de nombreuses autres équipes utilisent .NET Core, vous pouvez créer et publier des forfaits NuGet clients dans le cadre de votre projet de service. Cela peut être un bon moyen de partager et de promouvoir votre service.

Un avantage de la distribution d’une bibliothèque cliente est que vous pouvez améliorer les classes générées gRPC et Protobuf avec des méthodes et des propriétés utiles de « commodité ». Dans le code client, comme dans le serveur, toutes les classes sont déclarées comme `partial`, de sorte que vous pouvez les étendre sans modifier le code généré. Cela signifie qu’il est facile d’ajouter des constructeurs, des méthodes et des propriétés calculées aux types de base.

> [!CAUTION]
> Vous ne devriez pas utiliser le code personnalisé pour fournir des fonctionnalités essentielles. Vous ne voulez pas limiter cette fonctionnalité essentielle aux équipes .NET qui utilisent la bibliothèque partagée, et ne pas la fournir aux équipes qui utilisent d’autres langues ou plates-formes, telles que Python ou Java.

Assurez-vous que le plus grand nombre possible d’équipes peuvent accéder à votre service gRPC. La meilleure façon de le `.proto` faire est de partager des fichiers afin que les développeurs puissent générer leurs propres clients. Cela est particulièrement vrai dans un environnement multiplateforme, où différentes équipes utilisent fréquemment différents langages et cadres de programmation, ou où votre API est accessible à l’extérieur.

## <a name="useful-extensions"></a>Extensions utiles

Il existe deux interfaces couramment utilisées en .NET <xref:System.Collections.Generic.IEnumerable%601> pour <xref:System.IObservable%601>traiter les flux d’objets: et . En commençant par .NET Core 3.0 et C 8.0, il ya une <xref:System.Collections.Generic.IAsyncEnumerable%601> interface `await foreach` pour traiter les flux asynchrone, et une syntaxe pour l’utilisation de l’interface. Cette section présente un code réutilisable pour l’application de ces interfaces sur les flux gRPC.

Avec les bibliothèques de clients .NET Core `ReadAllAsync` gRPC, il existe une méthode d’extension pour `IAsyncStreamReader<T>` créer une `IAsyncEnumerable<T>` interface. Pour les développeurs utilisant une programmation réactive, `IObservable<T>` une méthode d’extension équivalente pour créer une interface peut ressembler à l’exemple dans la section suivante.

### <a name="iobservable"></a>Iobservable

L’interface `IObservable<T>` est l’inverse `IEnumerable<T>`"réactif" de . Plutôt que de retirer des éléments d’un flux, l’approche réactive permet au flux de pousser les éléments vers un abonné. Ceci est très similaire aux flux gRPC, et `IObservable<T>` il est `IAsyncStreamReader<T>` facile d’envelopper une interface autour d’une interface.

Ce code est `IAsyncEnumerable<T>` plus long que le code, car le C n’a pas de support intégré pour travailler avec des observables. Vous devez créer la classe d’implémentation manuellement. Il s’agit d’une classe générique, cependant, de sorte qu’une seule implémentation fonctionne à tous les types.

```csharp
using System;
using System.Diagnostics;
using System.Threading;
using System.Threading.Tasks;

namespace Grpc.Core
{
    public class GrpcStreamObservable<T> : IObservable<T>
    {
        private readonly IAsyncStreamReader<T> _reader;
        private readonly CancellationToken _token;
        private int _used;

        public Observable(IAsyncStreamReader<T> reader, CancellationToken token = default)
        {
            _reader = reader;
            _token = token;
            _used = 0;
        }

        public IDisposable Subscribe(IObserver<T> observer) =>
            Interlocked.Exchange(ref _used, 1) == 0
                ? new GrpcStreamSubscription(_reader, observer, _token)
                : throw new InvalidOperationException("Subscribe can only be called once.");

    }
}
```

> [!IMPORTANT]
> Cette implémentation `Subscribe` observable permet à la méthode d’être appelée qu’une seule fois, parce que le fait d’avoir plusieurs abonnés essayant de lire à partir du flux entraînerait le chaos. Il y a `Replay` des opérateurs, comme dans le [System.Reactive.Linq](https://www.nuget.org/packages/System.Reactive.Linq), qui permettent la mise en mémoire tampon et le partage répétable des observables, qui peuvent être utilisés avec cette implémentation.

La `GrpcStreamSubscription` classe gère l’énumération `IAsyncStreamReader`de la :

```csharp
public class GrpcStreamSubscription : IDisposable
{
    private readonly Task _task;
    private readonly CancellationTokenSource _tokenSource;
    private bool _completed;

    public Subscription(IAsyncStreamReader<T> reader, IObserver<T> observer, CancellationToken token)
    {
        Debug.Assert(reader != null);
        Debug.Assert(observer != null);
        _tokenSource = new CancellationTokenSource();
        token.Register(_tokenSource.Cancel);
        _task = Run(reader, observer, _tokenSource.Token);
    }

    private async Task Run(IAsyncStreamReader<T> reader, IObserver<T> observer, CancellationToken token)
    {
        while (!token.IsCancellationRequested)
        {
            try
            {
                if (!await reader.MoveNext(token)) break;
            }
            catch (RpcException e) when (e.StatusCode == Grpc.Core.StatusCode.NotFound)
            {
                break;
            }
            catch (OperationCanceledException)
            {
                break;
            }
            catch (Exception e)
            {
                observer.OnError(e);
                _completed = true;
                return;
            }

            observer.OnNext(reader.Current);
        }

        _completed = true;
        observer.OnCompleted();
    }

    public void Dispose()
    {
        if (!_completed && !_tokenSource.IsCancellationRequested)
        {
            _tokenSource.Cancel();
        }

        _tokenSource.Dispose();
        _task.Dispose();
    }

}
```

Tout ce qui est nécessaire maintenant est une méthode d’extension simple pour créer le observable à partir du lecteur de flux.

```csharp
using System;
using System.Diagnostics;
using System.Threading;
using System.Threading.Tasks;

namespace Grpc.Core
{
    public static class AsyncStreamReaderObservableExtensions
    {
        public static IObservable<T> AsObservable<T>(this IAsyncStreamReader<T> reader) =>
            new GrpcStreamObservable<T>(reader);
    }
}
```

## <a name="summary"></a>Résumé

Les `IAsyncEnumerable` `IObservable` modèles et les modèles sont à la fois des moyens bien soutenus et bien documentés de traiter les flux asynchrones de données en .NET. GRPC diffuse bien la carte aux deux paradigmes, offrant une intégration étroite avec .NET Core, et des styles de programmation réactifs et asynchrones.

>[!div class="step-by-step"]
>[Suivant précédent](streaming-versus-repeated.md)
>[Next](security.md)
