---
title: Créer des bibliothèques clientes gRPC-gRPC pour les développeurs WCF
description: Discussion sur les bibliothèques/packages client partagés pour les services gRPC.
ms.date: 01/06/2021
ms.openlocfilehash: c55b6d1da2377af0b687e32e7776f12b96b0a2ba
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970126"
---
# <a name="create-grpc-client-libraries"></a><span data-ttu-id="51029-103">Créer des bibliothèques clientes gRPC</span><span class="sxs-lookup"><span data-stu-id="51029-103">Create gRPC client libraries</span></span>

<span data-ttu-id="51029-104">Il n’est pas nécessaire de distribuer les bibliothèques clientes pour une application gRPC.</span><span class="sxs-lookup"><span data-stu-id="51029-104">It isn't necessary to distribute client libraries for a gRPC application.</span></span> <span data-ttu-id="51029-105">Vous pouvez créer une bibliothèque partagée de `.proto` fichiers au sein de votre organisation, et d’autres équipes peuvent utiliser ces fichiers pour générer le code client dans leurs propres projets.</span><span class="sxs-lookup"><span data-stu-id="51029-105">You can create a shared library of `.proto` files within your organization, and other teams can use those files to generate client code in their own projects.</span></span> <span data-ttu-id="51029-106">Toutefois, si vous disposez d’un référentiel NuGet privé et que de nombreuses autres équipes utilisent .NET, vous pouvez créer et publier des packages NuGet clients dans le cadre de votre projet de service.</span><span class="sxs-lookup"><span data-stu-id="51029-106">But if you have a private NuGet repository and many other teams are using .NET, you can create and publish client NuGet packages as part of your service project.</span></span> <span data-ttu-id="51029-107">Cette approche peut être un bon moyen de partager et de promouvoir votre service.</span><span class="sxs-lookup"><span data-stu-id="51029-107">This approach can be a good way of sharing and promoting your service.</span></span>

<span data-ttu-id="51029-108">L’un des avantages de la distribution d’une bibliothèque cliente est que vous pouvez améliorer les classes gRPC et Protobuf générées avec des méthodes et des propriétés pratiques.</span><span class="sxs-lookup"><span data-stu-id="51029-108">One advantage of distributing a client library is that you can enhance the generated gRPC and Protobuf classes with helpful "convenience" methods and properties.</span></span> <span data-ttu-id="51029-109">Dans le code client, comme dans le serveur, toutes les classes sont déclarées comme `partial` , vous pouvez donc les étendre sans modifier le code généré.</span><span class="sxs-lookup"><span data-stu-id="51029-109">In the client code, as in the server, all the classes are declared as `partial`, so you can extend them without editing the generated code.</span></span> <span data-ttu-id="51029-110">Ce comportement signifie qu’il est facile d’ajouter des constructeurs, des méthodes et des propriétés calculées aux types de base.</span><span class="sxs-lookup"><span data-stu-id="51029-110">This behavior means it's easy to add constructors, methods, and calculated properties to the basic types.</span></span>

> [!CAUTION]
> <span data-ttu-id="51029-111">Vous ne devez pas utiliser de code personnalisé pour fournir des fonctionnalités essentielles.</span><span class="sxs-lookup"><span data-stu-id="51029-111">You shouldn't use custom code to provide essential functionality.</span></span> <span data-ttu-id="51029-112">Vous ne souhaitez pas restreindre les fonctionnalités essentielles aux équipes .NET qui utilisent la bibliothèque partagée et ne pas les fournir aux équipes qui utilisent d’autres langages ou plateformes, tels que Python ou Java.</span><span class="sxs-lookup"><span data-stu-id="51029-112">You don't want to restrict that essential functionality to .NET teams that use the shared library, and not provide it to teams that use other languages or platforms, such as Python or Java.</span></span>

<span data-ttu-id="51029-113">Assurez-vous que autant d’équipes que possible peuvent accéder à votre service gRPC.</span><span class="sxs-lookup"><span data-stu-id="51029-113">Ensure that as many teams as possible can access your gRPC service.</span></span> <span data-ttu-id="51029-114">La meilleure façon d’effectuer cette fonctionnalité est de partager `.proto` des fichiers pour que les développeurs puissent générer leurs propres clients.</span><span class="sxs-lookup"><span data-stu-id="51029-114">The best way to do this functionality is to share `.proto` files so developers can generate their own clients.</span></span> <span data-ttu-id="51029-115">Cette approche est particulièrement vraie dans un environnement multi-plateforme, où différentes équipes utilisent fréquemment différents langages de programmation et infrastructures, ou où votre API est accessible en externe.</span><span class="sxs-lookup"><span data-stu-id="51029-115">This approach is particularly true in a multi-platform environment, where different teams frequently use different programming languages and frameworks, or where your API is externally accessible.</span></span>

## <a name="useful-extensions"></a><span data-ttu-id="51029-116">Extensions utiles</span><span class="sxs-lookup"><span data-stu-id="51029-116">Useful extensions</span></span>

<span data-ttu-id="51029-117">Il existe deux interfaces couramment utilisées dans .NET pour gérer les flux d’objets : <xref:System.Collections.Generic.IEnumerable%601> et <xref:System.IObservable%601> .</span><span class="sxs-lookup"><span data-stu-id="51029-117">There are two commonly used interfaces in .NET for dealing with streams of objects: <xref:System.Collections.Generic.IEnumerable%601> and <xref:System.IObservable%601>.</span></span> <span data-ttu-id="51029-118">À compter de .NET Core 3,0 et C# 8,0, il existe une <xref:System.Collections.Generic.IAsyncEnumerable%601> interface pour traiter les flux de façon asynchrone et une `await foreach` syntaxe pour l’utilisation de l’interface.</span><span class="sxs-lookup"><span data-stu-id="51029-118">Starting with .NET Core 3.0 and C# 8.0, there's an <xref:System.Collections.Generic.IAsyncEnumerable%601> interface for processing streams asynchronously, and an `await foreach` syntax for using the interface.</span></span> <span data-ttu-id="51029-119">Cette section présente le code réutilisable pour l’application de ces interfaces aux flux gRPC.</span><span class="sxs-lookup"><span data-stu-id="51029-119">This section presents reusable code for applying these interfaces to gRPC streams.</span></span>

<span data-ttu-id="51029-120">Avec les bibliothèques clientes .NET gRPC, il existe une `ReadAllAsync` méthode d’extension pour `IAsyncStreamReader<T>` qui crée une `IAsyncEnumerable<T>` interface.</span><span class="sxs-lookup"><span data-stu-id="51029-120">With the .NET gRPC client libraries, there's a `ReadAllAsync` extension method for `IAsyncStreamReader<T>` that creates an `IAsyncEnumerable<T>` interface.</span></span> <span data-ttu-id="51029-121">Pour les développeurs qui utilisent la programmation réactive, une méthode d’extension équivalente pour créer une `IObservable<T>` interface peut ressembler à l’exemple de la section suivante.</span><span class="sxs-lookup"><span data-stu-id="51029-121">For developers using reactive programming, an equivalent extension method to create an `IObservable<T>` interface might look like the example in the following section.</span></span>

### <a name="iobservable"></a><span data-ttu-id="51029-122">IObservable</span><span class="sxs-lookup"><span data-stu-id="51029-122">IObservable</span></span>

<span data-ttu-id="51029-123">L' `IObservable<T>` interface est l’inverse « REACTIF » de `IEnumerable<T>` .</span><span class="sxs-lookup"><span data-stu-id="51029-123">The `IObservable<T>` interface is the "reactive" inverse of `IEnumerable<T>`.</span></span> <span data-ttu-id="51029-124">Plutôt que d’extraire des éléments d’un flux, l’approche réactive permet au flux de transmettre des éléments à un abonné.</span><span class="sxs-lookup"><span data-stu-id="51029-124">Rather than pulling items from a stream, the reactive approach lets the stream push items to a subscriber.</span></span> <span data-ttu-id="51029-125">Ce comportement est très similaire aux flux gRPC, et il est facile d’encapsuler une `IObservable<T>` interface autour d’une `IAsyncStreamReader<T>` interface.</span><span class="sxs-lookup"><span data-stu-id="51029-125">This behavior is very similar to gRPC streams, and it's easy to wrap an `IObservable<T>` interface around an `IAsyncStreamReader<T>` interface.</span></span>

<span data-ttu-id="51029-126">Ce code est plus long que le `IAsyncEnumerable<T>` code, car C# ne prend pas en charge l’utilisation de observables.</span><span class="sxs-lookup"><span data-stu-id="51029-126">This code is longer than the `IAsyncEnumerable<T>` code, because C# doesn't have built-in support for working with observables.</span></span> <span data-ttu-id="51029-127">Vous devez créer la classe d’implémentation manuellement.</span><span class="sxs-lookup"><span data-stu-id="51029-127">You have to create the implementation class manually.</span></span> <span data-ttu-id="51029-128">Toutefois, il s’agit d’une classe générique, de sorte qu’une seule implémentation fonctionne sur tous les types.</span><span class="sxs-lookup"><span data-stu-id="51029-128">It's a generic class, though, so a single implementation works across all types.</span></span>

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
> <span data-ttu-id="51029-129">Cette implémentation observable permet à la `Subscribe` méthode d’être appelée une seule fois, car le fait que plusieurs abonnés essaient de lire à partir du flux entraîne un chaos.</span><span class="sxs-lookup"><span data-stu-id="51029-129">This observable implementation allows the `Subscribe` method to be called only once, because having multiple subscribers trying to read from the stream would result in chaos.</span></span> <span data-ttu-id="51029-130">Il existe des opérateurs, tels que `Replay` dans [System. Reactive. Linq](https://www.nuget.org/packages/System.Reactive.Linq), qui activent la mise en mémoire tampon et le partage reproductible de observables, qui peuvent être utilisés avec cette implémentation.</span><span class="sxs-lookup"><span data-stu-id="51029-130">There are operators, such as `Replay` in the [System.Reactive.Linq](https://www.nuget.org/packages/System.Reactive.Linq), that enable buffering and repeatable sharing of observables, which can be used with this implementation.</span></span>

<span data-ttu-id="51029-131">La `GrpcStreamSubscription` classe gère l’énumération de `IAsyncStreamReader` :</span><span class="sxs-lookup"><span data-stu-id="51029-131">The `GrpcStreamSubscription` class handles the enumeration of the `IAsyncStreamReader`:</span></span>

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

<span data-ttu-id="51029-132">Tout ce qui est nécessaire maintenant est une méthode d’extension simple pour créer l’observable à partir du lecteur de flux.</span><span class="sxs-lookup"><span data-stu-id="51029-132">All that is required now is a simple extension method to create the observable from the stream reader.</span></span>

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

## <a name="summary"></a><span data-ttu-id="51029-133">Résumé</span><span class="sxs-lookup"><span data-stu-id="51029-133">Summary</span></span>

<span data-ttu-id="51029-134">Les <xref:System.Collections.Generic.IAsyncEnumerable%601> <xref:System.IObservable%601> modèles et sont des méthodes bien prises en charge et bien documentées pour gérer les flux de données asynchrones dans .net.</span><span class="sxs-lookup"><span data-stu-id="51029-134">The <xref:System.Collections.Generic.IAsyncEnumerable%601> and <xref:System.IObservable%601> models are both well-supported and well-documented ways of dealing with asynchronous streams of data in .NET.</span></span> <span data-ttu-id="51029-135">les flux gRPC sont correctement mappés aux deux paradigmes, offrant une intégration étroite avec .NET et des styles de programmation réactifs et asynchrones.</span><span class="sxs-lookup"><span data-stu-id="51029-135">gRPC streams map well to both paradigms, offering close integration with .NET, and reactive and asynchronous programming styles.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="51029-136">[Précédent](streaming-versus-repeated.md) 
> [Suivant](security.md)</span><span class="sxs-lookup"><span data-stu-id="51029-136">[Previous](streaming-versus-repeated.md)
[Next](security.md)</span></span>
