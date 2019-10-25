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
# <a name="create-grpc-client-libraries"></a><span data-ttu-id="feeb5-103">Créer des bibliothèques clientes gRPC</span><span class="sxs-lookup"><span data-stu-id="feeb5-103">Create gRPC client libraries</span></span>

<span data-ttu-id="feeb5-104">Il n’est pas nécessaire de distribuer les bibliothèques clientes pour une application gPRC.</span><span class="sxs-lookup"><span data-stu-id="feeb5-104">It isn't necessary to distribute client libraries for a gPRC application.</span></span> <span data-ttu-id="feeb5-105">Vous pouvez créer une bibliothèque partagée de fichiers `.proto` au sein de votre organisation, et d’autres équipes peuvent utiliser ces fichiers pour générer le code client dans leurs propres projets.</span><span class="sxs-lookup"><span data-stu-id="feeb5-105">You can create a shared library of `.proto` files within your organization, and other teams can use those files to generate client code in their own projects.</span></span> <span data-ttu-id="feeb5-106">Toutefois, si vous disposez d’un référentiel NuGet privé et que de nombreuses autres équipes utilisent .NET Core, la création et la publication de packages NuGet client dans le cadre de votre projet de service peuvent être un bon moyen de partager et de promouvoir votre service.</span><span class="sxs-lookup"><span data-stu-id="feeb5-106">But if you have a private NuGet repository and many other teams are using .NET Core, creating and publishing client NuGet packages as part of your service project may be a good way of sharing and promoting your service.</span></span>

<span data-ttu-id="feeb5-107">L’un des avantages de la distribution d’une bibliothèque cliente est que vous pouvez améliorer les classes gRPC et Protobuf générées avec des méthodes et des propriétés pratiques.</span><span class="sxs-lookup"><span data-stu-id="feeb5-107">One advantage of distributing a client library is that you can enhance the generated gRPC and Protobuf classes with helpful "convenience" methods and properties.</span></span> <span data-ttu-id="feeb5-108">Dans le code client, comme dans le serveur, toutes les classes sont déclarées comme `partial` afin que vous puissiez les étendre sans modifier le code généré.</span><span class="sxs-lookup"><span data-stu-id="feeb5-108">In the client code, as in the server, all the classes are declared as `partial` so you can extend them without editing the generated code.</span></span> <span data-ttu-id="feeb5-109">Cela signifie qu’il est facile d’ajouter des constructeurs, des méthodes, des propriétés calculées, etc., aux types de base.</span><span class="sxs-lookup"><span data-stu-id="feeb5-109">This means it's easy to add constructors, methods, calculated properties, and more to the basic types.</span></span>

> [!CAUTION]
> <span data-ttu-id="feeb5-110">Vous **ne devez pas** utiliser de code personnalisé pour fournir des fonctionnalités essentielles, car cela signifierait que les fonctionnalités seraient limitées aux équipes .net utilisant la bibliothèque partagée, et non aux équipes utilisant d’autres langages ou plateformes, tels que Python ou Java.</span><span class="sxs-lookup"><span data-stu-id="feeb5-110">You should **not** use custom code to provide essential functionality, as this would mean that functionality would be restricted to .NET teams using the shared library, and not to teams using other languages or platforms such as Python or Java.</span></span>

<span data-ttu-id="feeb5-111">Dans un environnement multiplateforme où différentes équipes utilisent fréquemment des langages de programmation et des frameworks différents, ou où votre API est accessible en externe, le partage de fichiers `.proto` pour que les développeurs puissent générer leurs propres clients, c’est le meilleur moyen de s’assurer autant d’équipes que possible peuvent accéder à votre service gRPC.</span><span class="sxs-lookup"><span data-stu-id="feeb5-111">In a multi-platform environment where different teams frequently use different programming languages and frameworks, or where your API is externally accessible, simply sharing `.proto` files so developers can generate their own clients is the best way to ensure as many teams as possible can access your gRPC service.</span></span>

## <a name="useful-extensions"></a><span data-ttu-id="feeb5-112">Extensions utiles</span><span class="sxs-lookup"><span data-stu-id="feeb5-112">Useful extensions</span></span>

<span data-ttu-id="feeb5-113">Il existe deux interfaces couramment utilisées dans .NET pour gérer les flux d’objets : <xref:System.Collections.Generic.IEnumerable%601> et <xref:System.IObservable%601>.</span><span class="sxs-lookup"><span data-stu-id="feeb5-113">There are two commonly used interfaces in .NET for dealing with streams of objects: <xref:System.Collections.Generic.IEnumerable%601> and <xref:System.IObservable%601>.</span></span> <span data-ttu-id="feeb5-114">À compter de .NET Core 3,0 C# et 8,0, il existe une interface<xref:System.Collections.Generic.IAsyncEnumerable%601>pour le traitement asynchrone des flux, et une syntaxe`await foreach`pour l’utilisation de l’interface.</span><span class="sxs-lookup"><span data-stu-id="feeb5-114">Starting with .NET Core 3.0 and C# 8.0, there's an <xref:System.Collections.Generic.IAsyncEnumerable%601> interface for processing streams asynchronously, and an `await foreach` syntax for using the interface.</span></span> <span data-ttu-id="feeb5-115">Cette section présente le code réutilisable pour l’application de ces interfaces aux flux gRPC.</span><span class="sxs-lookup"><span data-stu-id="feeb5-115">This section presents reusable code for applying these interfaces to gRPC streams.</span></span>

<span data-ttu-id="feeb5-116">Avec les bibliothèques clientes gRPC .NET Core, il existe une méthode d’extension `ReadAllAsync` pour `IAsyncStreamReader<T>` qui crée une `IAsyncEnumerable<T>`.</span><span class="sxs-lookup"><span data-stu-id="feeb5-116">With the .NET Core gRPC client libraries, there's a `ReadAllAsync` extension method for `IAsyncStreamReader<T>` that creates an `IAsyncEnumerable<T>`.</span></span> <span data-ttu-id="feeb5-117">Pour les développeurs qui utilisent la programmation réactive, une méthode d’extension équivalente pour créer un `IObservable<T>` peut se présenter comme suit.</span><span class="sxs-lookup"><span data-stu-id="feeb5-117">For developers using reactive programming, an equivalent extension method to create an `IObservable<T>` might look like this.</span></span>

### <a name="iobservable"></a><span data-ttu-id="feeb5-118">IObservable</span><span class="sxs-lookup"><span data-stu-id="feeb5-118">IObservable</span></span>

<span data-ttu-id="feeb5-119">L’interface `IObservable<T>` est l’inverse « réactif » de `IEnumerable<T>`.</span><span class="sxs-lookup"><span data-stu-id="feeb5-119">The `IObservable<T>` interface is the "reactive" inverse of `IEnumerable<T>`.</span></span> <span data-ttu-id="feeb5-120">Plutôt que d’extraire des éléments d’un flux, l’approche réactive permet au flux de transmettre des éléments à un abonné.</span><span class="sxs-lookup"><span data-stu-id="feeb5-120">Rather than pulling items from a stream, the reactive approach lets the stream push items to a subscriber.</span></span> <span data-ttu-id="feeb5-121">Cela est très similaire aux flux gRPC, et il est facile d’encapsuler un `IObservable<T>` autour d’une `IAsyncStreamReader<T>`.</span><span class="sxs-lookup"><span data-stu-id="feeb5-121">This is very similar to gRPC streams, and it's easy to wrap an `IObservable<T>` around an `IAsyncStreamReader<T>`.</span></span>

<span data-ttu-id="feeb5-122">Ce code est plus long que le code `IAsyncEnumerable<T>` C# , car ne dispose pas d’une prise en charge intégrée de l’utilisation de observables. la classe d’implémentation doit donc être créée manuellement.</span><span class="sxs-lookup"><span data-stu-id="feeb5-122">This code is longer than the `IAsyncEnumerable<T>` code because C# doesn't have built-in support for working with observables, so the implementation class has to be created manually.</span></span> <span data-ttu-id="feeb5-123">Toutefois, il s’agit d’une classe générique, de sorte qu’une seule implémentation fonctionnera sur tous les types.</span><span class="sxs-lookup"><span data-stu-id="feeb5-123">It's a generic class, though, so a single implementation will work across all types.</span></span>

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
> <span data-ttu-id="feeb5-124">Cette implémentation observable permet uniquement à la méthode `Subscribe` d’être appelée une seule fois, car le fait que plusieurs abonnés essaient de lire à partir du flux entraîne un chaos.</span><span class="sxs-lookup"><span data-stu-id="feeb5-124">This observable implementation only allows the `Subscribe` method to be called once, as having multiple subscribers trying to read from the stream would result in chaos.</span></span> <span data-ttu-id="feeb5-125">Il existe des opérateurs tels que `Replay` dans [System. Reactive. Linq](https://www.nuget.org/packages/System.Reactive.Linq) qui activent la mise en mémoire tampon et le partage reproductible de observables, qui peut être utilisé avec cette implémentation.</span><span class="sxs-lookup"><span data-stu-id="feeb5-125">There are operators such as `Replay` in the [System.Reactive.Linq](https://www.nuget.org/packages/System.Reactive.Linq) that enable buffering and repeatable sharing of observables, which can be used with this implementation.</span></span>

<span data-ttu-id="feeb5-126">La classe `GrpcStreamSubscription` gère l’énumération du `IAsyncStreamReader`.</span><span class="sxs-lookup"><span data-stu-id="feeb5-126">The `GrpcStreamSubscription` class handles the enumeration of the `IAsyncStreamReader`.</span></span>

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

<span data-ttu-id="feeb5-127">Tout ce qui est nécessaire maintenant est une méthode d’extension simple pour créer l’observable à partir du lecteur de flux.</span><span class="sxs-lookup"><span data-stu-id="feeb5-127">All that is required now is a simple extension method to create the observable from the stream reader.</span></span>

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

## <a name="summary"></a><span data-ttu-id="feeb5-128">Récapitulatif</span><span class="sxs-lookup"><span data-stu-id="feeb5-128">Summary</span></span>

<span data-ttu-id="feeb5-129">Les modèles `IAsyncEnumerable` et `IObservable` sont des méthodes bien prises en charge et bien documentées pour gérer les flux de données asynchrones dans .NET.</span><span class="sxs-lookup"><span data-stu-id="feeb5-129">The `IAsyncEnumerable` and `IObservable` models are both well-supported and well-documented ways of dealing with asynchronous streams of data in .NET.</span></span> <span data-ttu-id="feeb5-130">les flux gRPC sont bien mappés aux deux paradigmes, offrant une intégration étroite avec l’infrastructure .NET Core moderne et des styles de programmation réactifs/asynchrones.</span><span class="sxs-lookup"><span data-stu-id="feeb5-130">gRPC streams map well to both paradigms, offering close integration with the modern .NET Core framework and reactive/asynchronous programming styles.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="feeb5-131">[Précédent](streaming-versus-repeated.md)
>[Suivant](security.md)</span><span class="sxs-lookup"><span data-stu-id="feeb5-131">[Previous](streaming-versus-repeated.md)
[Next](security.md)</span></span>
