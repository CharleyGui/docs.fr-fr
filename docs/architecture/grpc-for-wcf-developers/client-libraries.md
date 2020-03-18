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
# <a name="create-grpc-client-libraries"></a><span data-ttu-id="02c7b-103">Créer des bibliothèques de clients gRPC</span><span class="sxs-lookup"><span data-stu-id="02c7b-103">Create gRPC client libraries</span></span>

<span data-ttu-id="02c7b-104">Il n’est pas nécessaire de distribuer des bibliothèques clients pour une application gRPC.</span><span class="sxs-lookup"><span data-stu-id="02c7b-104">It isn't necessary to distribute client libraries for a gRPC application.</span></span> <span data-ttu-id="02c7b-105">Vous pouvez créer une `.proto` bibliothèque partagée de fichiers au sein de votre organisation, et d’autres équipes peuvent utiliser ces fichiers pour générer du code client dans leurs propres projets.</span><span class="sxs-lookup"><span data-stu-id="02c7b-105">You can create a shared library of `.proto` files within your organization, and other teams can use those files to generate client code in their own projects.</span></span> <span data-ttu-id="02c7b-106">Mais si vous avez un référentiel NuGet privé et que de nombreuses autres équipes utilisent .NET Core, vous pouvez créer et publier des forfaits NuGet clients dans le cadre de votre projet de service.</span><span class="sxs-lookup"><span data-stu-id="02c7b-106">But if you have a private NuGet repository and many other teams are using .NET Core, you can create and publish client NuGet packages as part of your service project.</span></span> <span data-ttu-id="02c7b-107">Cela peut être un bon moyen de partager et de promouvoir votre service.</span><span class="sxs-lookup"><span data-stu-id="02c7b-107">This can be a good way of sharing and promoting your service.</span></span>

<span data-ttu-id="02c7b-108">Un avantage de la distribution d’une bibliothèque cliente est que vous pouvez améliorer les classes générées gRPC et Protobuf avec des méthodes et des propriétés utiles de « commodité ».</span><span class="sxs-lookup"><span data-stu-id="02c7b-108">One advantage of distributing a client library is that you can enhance the generated gRPC and Protobuf classes with helpful "convenience" methods and properties.</span></span> <span data-ttu-id="02c7b-109">Dans le code client, comme dans le serveur, toutes les classes sont déclarées comme `partial`, de sorte que vous pouvez les étendre sans modifier le code généré.</span><span class="sxs-lookup"><span data-stu-id="02c7b-109">In the client code, as in the server, all the classes are declared as `partial`, so you can extend them without editing the generated code.</span></span> <span data-ttu-id="02c7b-110">Cela signifie qu’il est facile d’ajouter des constructeurs, des méthodes et des propriétés calculées aux types de base.</span><span class="sxs-lookup"><span data-stu-id="02c7b-110">This means it's easy to add constructors, methods, and calculated properties to the basic types.</span></span>

> [!CAUTION]
> <span data-ttu-id="02c7b-111">Vous ne devriez pas utiliser le code personnalisé pour fournir des fonctionnalités essentielles.</span><span class="sxs-lookup"><span data-stu-id="02c7b-111">You shouldn't use custom code to provide essential functionality.</span></span> <span data-ttu-id="02c7b-112">Vous ne voulez pas limiter cette fonctionnalité essentielle aux équipes .NET qui utilisent la bibliothèque partagée, et ne pas la fournir aux équipes qui utilisent d’autres langues ou plates-formes, telles que Python ou Java.</span><span class="sxs-lookup"><span data-stu-id="02c7b-112">You don't want to restrict that essential functionality to .NET teams that use the shared library, and not provide it to teams that use other languages or platforms, such as Python or Java.</span></span>

<span data-ttu-id="02c7b-113">Assurez-vous que le plus grand nombre possible d’équipes peuvent accéder à votre service gRPC.</span><span class="sxs-lookup"><span data-stu-id="02c7b-113">Ensure that as many teams as possible can access your gRPC service.</span></span> <span data-ttu-id="02c7b-114">La meilleure façon de le `.proto` faire est de partager des fichiers afin que les développeurs puissent générer leurs propres clients.</span><span class="sxs-lookup"><span data-stu-id="02c7b-114">The best way to do this is to share `.proto` files so developers can generate their own clients.</span></span> <span data-ttu-id="02c7b-115">Cela est particulièrement vrai dans un environnement multiplateforme, où différentes équipes utilisent fréquemment différents langages et cadres de programmation, ou où votre API est accessible à l’extérieur.</span><span class="sxs-lookup"><span data-stu-id="02c7b-115">This is particularly true in a multi-platform environment, where different teams frequently use different programming languages and frameworks, or where your API is externally accessible.</span></span>

## <a name="useful-extensions"></a><span data-ttu-id="02c7b-116">Extensions utiles</span><span class="sxs-lookup"><span data-stu-id="02c7b-116">Useful extensions</span></span>

<span data-ttu-id="02c7b-117">Il existe deux interfaces couramment utilisées en .NET <xref:System.Collections.Generic.IEnumerable%601> pour <xref:System.IObservable%601>traiter les flux d’objets: et .</span><span class="sxs-lookup"><span data-stu-id="02c7b-117">There are two commonly used interfaces in .NET for dealing with streams of objects: <xref:System.Collections.Generic.IEnumerable%601> and <xref:System.IObservable%601>.</span></span> <span data-ttu-id="02c7b-118">En commençant par .NET Core 3.0 et C 8.0, il ya une <xref:System.Collections.Generic.IAsyncEnumerable%601> interface `await foreach` pour traiter les flux asynchrone, et une syntaxe pour l’utilisation de l’interface.</span><span class="sxs-lookup"><span data-stu-id="02c7b-118">Starting with .NET Core 3.0 and C# 8.0, there's an <xref:System.Collections.Generic.IAsyncEnumerable%601> interface for processing streams asynchronously, and an `await foreach` syntax for using the interface.</span></span> <span data-ttu-id="02c7b-119">Cette section présente un code réutilisable pour l’application de ces interfaces sur les flux gRPC.</span><span class="sxs-lookup"><span data-stu-id="02c7b-119">This section presents reusable code for applying these interfaces to gRPC streams.</span></span>

<span data-ttu-id="02c7b-120">Avec les bibliothèques de clients .NET Core `ReadAllAsync` gRPC, il existe une méthode d’extension pour `IAsyncStreamReader<T>` créer une `IAsyncEnumerable<T>` interface.</span><span class="sxs-lookup"><span data-stu-id="02c7b-120">With the .NET Core gRPC client libraries, there's a `ReadAllAsync` extension method for `IAsyncStreamReader<T>` that creates an `IAsyncEnumerable<T>` interface.</span></span> <span data-ttu-id="02c7b-121">Pour les développeurs utilisant une programmation réactive, `IObservable<T>` une méthode d’extension équivalente pour créer une interface peut ressembler à l’exemple dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="02c7b-121">For developers using reactive programming, an equivalent extension method to create an `IObservable<T>` interface might look like the example in the following section.</span></span>

### <a name="iobservable"></a><span data-ttu-id="02c7b-122">Iobservable</span><span class="sxs-lookup"><span data-stu-id="02c7b-122">IObservable</span></span>

<span data-ttu-id="02c7b-123">L’interface `IObservable<T>` est l’inverse `IEnumerable<T>`"réactif" de .</span><span class="sxs-lookup"><span data-stu-id="02c7b-123">The `IObservable<T>` interface is the "reactive" inverse of `IEnumerable<T>`.</span></span> <span data-ttu-id="02c7b-124">Plutôt que de retirer des éléments d’un flux, l’approche réactive permet au flux de pousser les éléments vers un abonné.</span><span class="sxs-lookup"><span data-stu-id="02c7b-124">Rather than pulling items from a stream, the reactive approach lets the stream push items to a subscriber.</span></span> <span data-ttu-id="02c7b-125">Ceci est très similaire aux flux gRPC, et `IObservable<T>` il est `IAsyncStreamReader<T>` facile d’envelopper une interface autour d’une interface.</span><span class="sxs-lookup"><span data-stu-id="02c7b-125">This is very similar to gRPC streams, and it's easy to wrap an `IObservable<T>` interface around an `IAsyncStreamReader<T>` interface.</span></span>

<span data-ttu-id="02c7b-126">Ce code est `IAsyncEnumerable<T>` plus long que le code, car le C n’a pas de support intégré pour travailler avec des observables.</span><span class="sxs-lookup"><span data-stu-id="02c7b-126">This code is longer than the `IAsyncEnumerable<T>` code, because C# doesn't have built-in support for working with observables.</span></span> <span data-ttu-id="02c7b-127">Vous devez créer la classe d’implémentation manuellement.</span><span class="sxs-lookup"><span data-stu-id="02c7b-127">You have to create the implementation class manually.</span></span> <span data-ttu-id="02c7b-128">Il s’agit d’une classe générique, cependant, de sorte qu’une seule implémentation fonctionne à tous les types.</span><span class="sxs-lookup"><span data-stu-id="02c7b-128">It's a generic class, though, so a single implementation works across all types.</span></span>

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
> <span data-ttu-id="02c7b-129">Cette implémentation `Subscribe` observable permet à la méthode d’être appelée qu’une seule fois, parce que le fait d’avoir plusieurs abonnés essayant de lire à partir du flux entraînerait le chaos.</span><span class="sxs-lookup"><span data-stu-id="02c7b-129">This observable implementation allows the `Subscribe` method to be called only once, because having multiple subscribers trying to read from the stream would result in chaos.</span></span> <span data-ttu-id="02c7b-130">Il y a `Replay` des opérateurs, comme dans le [System.Reactive.Linq](https://www.nuget.org/packages/System.Reactive.Linq), qui permettent la mise en mémoire tampon et le partage répétable des observables, qui peuvent être utilisés avec cette implémentation.</span><span class="sxs-lookup"><span data-stu-id="02c7b-130">There are operators, such as `Replay` in the [System.Reactive.Linq](https://www.nuget.org/packages/System.Reactive.Linq), that enable buffering and repeatable sharing of observables, which can be used with this implementation.</span></span>

<span data-ttu-id="02c7b-131">La `GrpcStreamSubscription` classe gère l’énumération `IAsyncStreamReader`de la :</span><span class="sxs-lookup"><span data-stu-id="02c7b-131">The `GrpcStreamSubscription` class handles the enumeration of the `IAsyncStreamReader`:</span></span>

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

<span data-ttu-id="02c7b-132">Tout ce qui est nécessaire maintenant est une méthode d’extension simple pour créer le observable à partir du lecteur de flux.</span><span class="sxs-lookup"><span data-stu-id="02c7b-132">All that is required now is a simple extension method to create the observable from the stream reader.</span></span>

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

## <a name="summary"></a><span data-ttu-id="02c7b-133">Résumé</span><span class="sxs-lookup"><span data-stu-id="02c7b-133">Summary</span></span>

<span data-ttu-id="02c7b-134">Les `IAsyncEnumerable` `IObservable` modèles et les modèles sont à la fois des moyens bien soutenus et bien documentés de traiter les flux asynchrones de données en .NET.</span><span class="sxs-lookup"><span data-stu-id="02c7b-134">The `IAsyncEnumerable` and `IObservable` models are both well-supported and well-documented ways of dealing with asynchronous streams of data in .NET.</span></span> <span data-ttu-id="02c7b-135">GRPC diffuse bien la carte aux deux paradigmes, offrant une intégration étroite avec .NET Core, et des styles de programmation réactifs et asynchrones.</span><span class="sxs-lookup"><span data-stu-id="02c7b-135">gRPC streams map well to both paradigms, offering close integration with .NET Core, and reactive and asynchronous programming styles.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="02c7b-136">[Suivant précédent](streaming-versus-repeated.md)
>[Next](security.md)</span><span class="sxs-lookup"><span data-stu-id="02c7b-136">[Previous](streaming-versus-repeated.md)
[Next](security.md)</span></span>
