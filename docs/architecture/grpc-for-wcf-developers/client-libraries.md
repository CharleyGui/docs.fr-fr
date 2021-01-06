---
title: Créer des bibliothèques clientes gRPC-gRPC pour les développeurs WCF
description: Discussion sur les bibliothèques/packages client partagés pour les services gRPC.
ms.date: 12/15/2020
ms.openlocfilehash: b1233bb40a5fa2119a325be2657b500a4c626c18
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938427"
---
# <a name="create-grpc-client-libraries"></a>Créer des bibliothèques clientes gRPC

Il n’est pas nécessaire de distribuer les bibliothèques clientes pour une application gRPC. Vous pouvez créer une bibliothèque partagée de `.proto` fichiers au sein de votre organisation, et d’autres équipes peuvent utiliser ces fichiers pour générer le code client dans leurs propres projets. Toutefois, si vous disposez d’un référentiel NuGet privé et que de nombreuses autres équipes utilisent .NET, vous pouvez créer et publier des packages NuGet clients dans le cadre de votre projet de service. Cette approche peut être un bon moyen de partager et de promouvoir votre service.

L’un des avantages de la distribution d’une bibliothèque cliente est que vous pouvez améliorer les classes gRPC et Protobuf générées avec des méthodes et des propriétés pratiques. Dans le code client, comme dans le serveur, toutes les classes sont déclarées comme `partial` , vous pouvez donc les étendre sans modifier le code généré. Ce comportement signifie qu’il est facile d’ajouter des constructeurs, des méthodes et des propriétés calculées aux types de base.

> [!CAUTION]
> Vous ne devez pas utiliser de code personnalisé pour fournir des fonctionnalités essentielles. Vous ne souhaitez pas restreindre les fonctionnalités essentielles aux équipes .NET qui utilisent la bibliothèque partagée et ne pas les fournir aux équipes qui utilisent d’autres langages ou plateformes, tels que Python ou Java.

Assurez-vous que autant d’équipes que possible peuvent accéder à votre service gRPC. La meilleure façon d’effectuer cette fonctionnalité est de partager `.proto` des fichiers pour que les développeurs puissent générer leurs propres clients. Cette approche est particulièrement vraie dans un environnement multi-plateforme, où différentes équipes utilisent fréquemment différents langages de programmation et infrastructures, ou où votre API est accessible en externe.

## <a name="useful-extensions"></a>Extensions utiles

Il existe deux interfaces couramment utilisées dans .NET pour gérer les flux d’objets : <xref:System.Collections.Generic.IEnumerable%601> et <xref:System.IObservable%601> . À compter de .NET Core 3,0 et C# 8,0, il existe une <xref:System.Collections.Generic.IAsyncEnumerable%601> interface pour traiter les flux de façon asynchrone et une `await foreach` syntaxe pour l’utilisation de l’interface. Cette section présente le code réutilisable pour l’application de ces interfaces aux flux gRPC.

Avec les bibliothèques clientes .NET gRPC, il existe une `ReadAllAsync` méthode d’extension pour `IAsyncStreamReader<T>` qui crée une `IAsyncEnumerable<T>` interface. Pour les développeurs qui utilisent la programmation réactive, une méthode d’extension équivalente pour créer une `IObservable<T>` interface peut ressembler à l’exemple de la section suivante.

### <a name="iobservable"></a>IObservable

L' `IObservable<T>` interface est l’inverse « REACTIF » de `IEnumerable<T>` . Plutôt que d’extraire des éléments d’un flux, l’approche réactive permet au flux de transmettre des éléments à un abonné. Ce comportement est très similaire aux flux gRPC, et il est facile d’encapsuler une `IObservable<T>` interface autour d’une `IAsyncStreamReader<T>` interface.

Ce code est plus long que le `IAsyncEnumerable<T>` code, car C# ne prend pas en charge l’utilisation de observables. Vous devez créer la classe d’implémentation manuellement. Toutefois, il s’agit d’une classe générique, de sorte qu’une seule implémentation fonctionne sur tous les types.

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

        public GrpcStreamObservable(IAsyncStreamReader<T> reader, CancellationToken token = default)
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
> Cette implémentation observable permet à la `Subscribe` méthode d’être appelée une seule fois, car le fait que plusieurs abonnés essaient de lire à partir du flux entraîne un chaos. Il existe des opérateurs, tels que `Replay` dans [System. Reactive. Linq](https://www.nuget.org/packages/System.Reactive.Linq), qui activent la mise en mémoire tampon et le partage reproductible de observables, qui peuvent être utilisés avec cette implémentation.

La `GrpcStreamSubscription` classe gère l’énumération de `IAsyncStreamReader` :

```csharp
public class GrpcStreamSubscription : IDisposable
{
    private readonly Task _task;
    private readonly CancellationTokenSource _tokenSource;
    private bool _completed;

    public GrpcStreamSubscription(IAsyncStreamReader<T> reader, IObserver<T> observer, CancellationToken token)
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

## <a name="summary"></a>Résumé

Les <xref:System.IAsyncDisposable> <xref:System.IObservable%601> modèles et sont des méthodes bien prises en charge et bien documentées pour gérer les flux de données asynchrones dans .net. les flux gRPC sont correctement mappés aux deux paradigmes, offrant une intégration étroite avec .NET et des styles de programmation réactifs et asynchrones.

>[!div class="step-by-step"]
>[Précédent](streaming-versus-repeated.md) 
> [Suivant](security.md)
