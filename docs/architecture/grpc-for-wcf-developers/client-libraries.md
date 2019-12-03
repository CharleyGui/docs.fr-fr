---
title: Créer des bibliothèques clientes gRPC-gRPC pour les développeurs WCF
description: Discussion sur les bibliothèques/packages client partagés pour les services gRPC.
ms.date: 09/02/2019
ms.openlocfilehash: bb58cb3cda4b0cbb3a5d34129961349bcb0093e9
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74711457"
---
# <a name="create-grpc-client-libraries"></a>Créer des bibliothèques clientes gRPC

Il n’est pas nécessaire de distribuer les bibliothèques clientes pour une application gRPC. Vous pouvez créer une bibliothèque partagée de fichiers `.proto` au sein de votre organisation, et d’autres équipes peuvent utiliser ces fichiers pour générer le code client dans leurs propres projets. Toutefois, si vous disposez d’un référentiel NuGet privé et que de nombreuses autres équipes utilisent .NET Core, vous pouvez créer et publier des packages NuGet clients dans le cadre de votre projet de service. Il peut s’agir d’un bon moyen de partager et de promouvoir votre service.

L’un des avantages de la distribution d’une bibliothèque cliente est que vous pouvez améliorer les classes gRPC et Protobuf générées avec des méthodes et des propriétés pratiques. Dans le code client, comme dans le serveur, toutes les classes sont déclarées en tant que `partial`, de sorte que vous pouvez les étendre sans modifier le code généré. Cela signifie qu’il est facile d’ajouter des constructeurs, des méthodes et des propriétés calculées aux types de base.

> [!CAUTION]
> Vous ne devez pas utiliser de code personnalisé pour fournir des fonctionnalités essentielles. Vous ne souhaitez pas restreindre les fonctionnalités essentielles aux équipes .NET qui utilisent la bibliothèque partagée et ne pas les fournir aux équipes qui utilisent d’autres langages ou plateformes, tels que Python ou Java.

Assurez-vous que autant d’équipes que possible peuvent accéder à votre service gRPC. La meilleure façon de procéder consiste à partager des fichiers `.proto` pour que les développeurs puissent générer leurs propres clients. Cela est particulièrement vrai dans un environnement multiplateforme, où différentes équipes utilisent fréquemment différents langages de programmation et infrastructures, ou où votre API est accessible en externe.

## <a name="useful-extensions"></a>Extensions utiles

Il existe deux interfaces couramment utilisées dans .NET pour gérer les flux d’objets : <xref:System.Collections.Generic.IEnumerable%601> et <xref:System.IObservable%601>. À compter de .NET Core 3,0 C# et 8,0, il existe une interface <xref:System.Collections.Generic.IAsyncEnumerable%601> pour le traitement asynchrone des flux, et une syntaxe `await foreach` pour l’utilisation de l’interface. Cette section présente le code réutilisable pour l’application de ces interfaces aux flux gRPC.

Avec les bibliothèques clientes gRPC .NET Core, il existe une méthode d’extension `ReadAllAsync` pour `IAsyncStreamReader<T>` qui crée une interface `IAsyncEnumerable<T>`. Pour les développeurs qui utilisent la programmation réactive, une méthode d’extension équivalente pour créer une interface `IObservable<T>` peut se présenter comme dans l’exemple de la section suivante.

### <a name="iobservable"></a>IObservable

L’interface `IObservable<T>` est l’inverse « réactif » de `IEnumerable<T>`. Plutôt que d’extraire des éléments d’un flux, l’approche réactive permet au flux de transmettre des éléments à un abonné. Cela est très similaire aux flux gRPC, et il est facile d’encapsuler une interface `IObservable<T>` autour d’une interface `IAsyncStreamReader<T>`.

Ce code est plus long que le code `IAsyncEnumerable<T>`, C# car ne dispose pas d’une prise en charge intégrée pour travailler avec observables. Vous devez créer la classe d’implémentation manuellement. Toutefois, il s’agit d’une classe générique, de sorte qu’une seule implémentation fonctionne sur tous les types.

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
> Cette implémentation observable permet à la méthode `Subscribe` d’être appelée une seule fois, car le fait que plusieurs abonnés essaient de lire à partir du flux entraîne un chaos. Il existe des opérateurs, tels que `Replay` dans [System. Reactive. Linq](https://www.nuget.org/packages/System.Reactive.Linq), qui activent la mise en mémoire tampon et le partage reproductible de observables, qui peuvent être utilisés avec cette implémentation.

La classe `GrpcStreamSubscription` gère l’énumération des `IAsyncStreamReader`:

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

Tout ce qui est nécessaire maintenant est une méthode d’extension simple pour créer l’observable à partir du lecteur de flux.

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

## <a name="summary"></a>Récapitulatif

Les modèles `IAsyncEnumerable` et `IObservable` sont des méthodes bien prises en charge et bien documentées pour gérer les flux de données asynchrones dans .NET. les flux gRPC sont correctement mappés aux deux paradigmes, offrant une intégration étroite avec .NET Core et des styles de programmation réactifs et asynchrones.

>[!div class="step-by-step"]
>[Précédent](streaming-versus-repeated.md)
>[Suivant](security.md)
