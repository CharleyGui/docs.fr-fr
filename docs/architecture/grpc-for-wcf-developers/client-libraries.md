---
title: Créer des bibliothèques clientes gRPC-gRPC pour les développeurs WCF
description: Discussion sur les bibliothèques/packages client partagés pour les services gRPC.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 12c628d2b58199a8103c60aa123bb75a34e0797d
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846701"
---
# <a name="create-grpc-client-libraries"></a>Créer des bibliothèques clientes gRPC

Il n’est pas nécessaire de distribuer les bibliothèques clientes pour une application gPRC. Vous pouvez créer une bibliothèque partagée de fichiers `.proto` au sein de votre organisation, et d’autres équipes peuvent utiliser ces fichiers pour générer le code client dans leurs propres projets. Toutefois, si vous disposez d’un référentiel NuGet privé et que de nombreuses autres équipes utilisent .NET Core, la création et la publication de packages NuGet client dans le cadre de votre projet de service peuvent être un bon moyen de partager et de promouvoir votre service.

L’un des avantages de la distribution d’une bibliothèque cliente est que vous pouvez améliorer les classes gRPC et Protobuf générées avec des méthodes et des propriétés pratiques. Dans le code client, comme dans le serveur, toutes les classes sont déclarées comme `partial` afin que vous puissiez les étendre sans modifier le code généré. Cela signifie qu’il est facile d’ajouter des constructeurs, des méthodes, des propriétés calculées, etc., aux types de base.

> [!CAUTION]
> Vous **ne devez pas** utiliser de code personnalisé pour fournir des fonctionnalités essentielles, car cela signifierait que les fonctionnalités seraient limitées aux équipes .net utilisant la bibliothèque partagée, et non aux équipes utilisant d’autres langages ou plateformes, tels que Python ou Java.

Dans un environnement multiplateforme où différentes équipes utilisent fréquemment des langages de programmation et des frameworks différents, ou où votre API est accessible en externe, le partage de fichiers `.proto` pour que les développeurs puissent générer leurs propres clients, c’est le meilleur moyen de s’assurer autant d’équipes que possible peuvent accéder à votre service gRPC.

## <a name="useful-extensions"></a>Extensions utiles

Il existe deux interfaces couramment utilisées dans .NET pour gérer les flux d’objets : <xref:System.Collections.Generic.IEnumerable%601> et <xref:System.IObservable%601>. À compter de .NET Core 3,0 C# et 8,0, il existe une interface<xref:System.Collections.Generic.IAsyncEnumerable%601>pour le traitement asynchrone des flux, et une syntaxe`await foreach`pour l’utilisation de l’interface. Cette section présente le code réutilisable pour l’application de ces interfaces aux flux gRPC.

Avec les bibliothèques clientes gRPC .NET Core, il existe une méthode d’extension `ReadAllAsync` pour `IAsyncStreamReader<T>` qui crée une `IAsyncEnumerable<T>`. Pour les développeurs qui utilisent la programmation réactive, une méthode d’extension équivalente pour créer un `IObservable<T>` peut se présenter comme suit.

### <a name="iobservable"></a>IObservable

L’interface `IObservable<T>` est l’inverse « réactif » de `IEnumerable<T>`. Plutôt que d’extraire des éléments d’un flux, l’approche réactive permet au flux de transmettre des éléments à un abonné. Cela est très similaire aux flux gRPC, et il est facile d’encapsuler un `IObservable<T>` autour d’une `IAsyncStreamReader<T>`.

Ce code est plus long que le code `IAsyncEnumerable<T>` C# , car ne dispose pas d’une prise en charge intégrée de l’utilisation de observables. la classe d’implémentation doit donc être créée manuellement. Toutefois, il s’agit d’une classe générique, de sorte qu’une seule implémentation fonctionnera sur tous les types.

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
> Cette implémentation observable permet uniquement à la méthode `Subscribe` d’être appelée une seule fois, car le fait que plusieurs abonnés essaient de lire à partir du flux entraîne un chaos. Il existe des opérateurs tels que `Replay` dans [System. Reactive. Linq](https://www.nuget.org/packages/System.Reactive.Linq) qui activent la mise en mémoire tampon et le partage reproductible de observables, qui peut être utilisé avec cette implémentation.

La classe `GrpcStreamSubscription` gère l’énumération du `IAsyncStreamReader`.

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

Les modèles `IAsyncEnumerable` et `IObservable` sont des méthodes bien prises en charge et bien documentées pour gérer les flux de données asynchrones dans .NET. les flux gRPC sont bien mappés aux deux paradigmes, offrant une intégration étroite avec l’infrastructure .NET Core moderne et des styles de programmation réactifs/asynchrones.

>[!div class="step-by-step"]
>[Précédent](streaming-versus-repeated.md)
>[Suivant](security.md)
