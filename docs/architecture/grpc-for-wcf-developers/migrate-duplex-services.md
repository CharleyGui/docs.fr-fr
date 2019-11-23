---
title: Migrer les services duplex WCF vers gRPC-gRPC pour les développeurs WCF
description: Découvrez comment migrer différentes formes de service duplex WCF vers des services de streaming gRPC.
ms.date: 09/02/2019
ms.openlocfilehash: e2248df20e5c2d8f96055d42ba684749251154bd
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73971882"
---
# <a name="migrate-wcf-duplex-services-to-grpc"></a><span data-ttu-id="26e8a-103">Migrer les services duplex WCF vers gRPC</span><span class="sxs-lookup"><span data-stu-id="26e8a-103">Migrate WCF duplex services to gRPC</span></span>

<span data-ttu-id="26e8a-104">Maintenant que les concepts de base sont en place, cette section aborde les services gRPC de *diffusion en continu* plus compliqués.</span><span class="sxs-lookup"><span data-stu-id="26e8a-104">Now that the basic concepts are in place, this section will look at the more complicated *streaming* gRPC services.</span></span>

<span data-ttu-id="26e8a-105">Il existe plusieurs façons d’utiliser les services duplex dans Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="26e8a-105">There are multiple ways to use duplex services in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="26e8a-106">Certains services sont initiés par le client, puis diffusent en continu des données à partir du serveur.</span><span class="sxs-lookup"><span data-stu-id="26e8a-106">Some services are initiated by the client and then they stream data from the server.</span></span> <span data-ttu-id="26e8a-107">D’autres services duplex intégral peuvent impliquer une communication bidirectionnelle continue comme l’exemple « calculatrice » classique dans la documentation WCF.</span><span class="sxs-lookup"><span data-stu-id="26e8a-107">Other full-duplex services might involve more ongoing two-way communication like the classic "Calculator" example from the WCF documentation.</span></span> <span data-ttu-id="26e8a-108">Ce chapitre prend en compte deux implémentations de « cotations boursières » WCF possibles et les migre vers gRPC : l’un à l’aide d’un RPC de diffusion de serveur et l’autre à l’aide d’un RPC de streaming bidirectionnel.</span><span class="sxs-lookup"><span data-stu-id="26e8a-108">This chapter will take two possible WCF "Stock Ticker" implementations and migrate them to gRPC: one using a server streaming RPC, and the other one using a bidirectional streaming RPC.</span></span>

## <a name="server-streaming-rpc"></a><span data-ttu-id="26e8a-109">RPC de streaming de serveur</span><span class="sxs-lookup"><span data-stu-id="26e8a-109">Server streaming RPC</span></span>

<span data-ttu-id="26e8a-110">Dans l' [exemple de solution SIMPLESTOCKTICKER WCF](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/SimpleStockTickerSample/wcf/SimpleStockTicker), *SimpleStockPriceTicker*, il existe un service duplex dans lequel le client démarre la connexion avec une liste de symboles boursiers, et le serveur utilise l' *interface de rappel* pour envoyer des mises à jour dès qu’elles sont disponibles.</span><span class="sxs-lookup"><span data-stu-id="26e8a-110">In the [sample SimpleStockTicker WCF solution](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/SimpleStockTickerSample/wcf/SimpleStockTicker), *SimpleStockPriceTicker*, there's a duplex service where the client starts the connection with a list of stock symbols, and the server uses the *callback interface* to send updates as they become available.</span></span> <span data-ttu-id="26e8a-111">Le client implémente cette interface pour répondre aux appels à partir du serveur.</span><span class="sxs-lookup"><span data-stu-id="26e8a-111">The client implements that interface to respond to calls from the server.</span></span>

### <a name="the-wcf-solution"></a><span data-ttu-id="26e8a-112">La solution WCF</span><span class="sxs-lookup"><span data-stu-id="26e8a-112">The WCF solution</span></span>

<span data-ttu-id="26e8a-113">La solution WCF est implémentée en tant que serveur NetTCP auto-hébergé dans une application console .NET Framework 4. x.</span><span class="sxs-lookup"><span data-stu-id="26e8a-113">The WCF solution is implemented as a self-hosted NetTCP server in a .NET Framework 4.x console application.</span></span>

#### <a name="the-servicecontract"></a><span data-ttu-id="26e8a-114">ServiceContract</span><span class="sxs-lookup"><span data-stu-id="26e8a-114">The ServiceContract</span></span>

```csharp
[ServiceContract(SessionMode = SessionMode.Required, CallbackContract = typeof(ISimpleStockTickerCallback))]
public interface ISimpleStockTickerService
{
    [OperationContract(IsOneWay = true)]
    void Subscribe(string[] symbols);
}
```

<span data-ttu-id="26e8a-115">Le service a une méthode unique sans type de retour, car il utilisera l’interface de rappel `ISimpleStockTickerCallback` pour envoyer des données au client en temps réel.</span><span class="sxs-lookup"><span data-stu-id="26e8a-115">The service has a single method with no return type, because it will be using the callback interface `ISimpleStockTickerCallback` to send data to the client in real time.</span></span>

#### <a name="the-callback-interface"></a><span data-ttu-id="26e8a-116">Interface de rappel</span><span class="sxs-lookup"><span data-stu-id="26e8a-116">The callback interface</span></span>

```csharp
[ServiceContract]
public interface ISimpleStockTickerCallback
{
    [OperationContract(IsOneWay = true)]
    void Update(string symbol, decimal price);
}
```

<span data-ttu-id="26e8a-117">Les implémentations de ces interfaces se trouvent dans la solution, ainsi que les dépendances externes factices pour fournir des données de test.</span><span class="sxs-lookup"><span data-stu-id="26e8a-117">The implementations of these interfaces can be found in the solution, along with faked external dependencies to provide test data.</span></span>

### <a name="grpc-streaming"></a><span data-ttu-id="26e8a-118">diffusion en continu gRPC</span><span class="sxs-lookup"><span data-stu-id="26e8a-118">gRPC streaming</span></span>

<span data-ttu-id="26e8a-119">La méthode gRPC pour gérer les données en temps réel est différente.</span><span class="sxs-lookup"><span data-stu-id="26e8a-119">The gRPC way of handling real-time data is different.</span></span> <span data-ttu-id="26e8a-120">Un appel du client au serveur peut créer un flux persistant, qui peut être surveillé pour les messages arrivant de manière asynchrone.</span><span class="sxs-lookup"><span data-stu-id="26e8a-120">A call from client to server can create a persistent stream, which can be monitored for messages arriving asynchronously.</span></span> <span data-ttu-id="26e8a-121">Malgré la différence, les flux peuvent être un moyen plus intuitif de traiter ces données et sont plus pertinents dans la programmation moderne avec l’accent sur LINQ, les flux réactifs, la programmation fonctionnelle, etc.</span><span class="sxs-lookup"><span data-stu-id="26e8a-121">Despite the difference, streams can be a more intuitive way of dealing with this data and are more relevant in modern programming with the emphasis on LINQ, Reactive Streams, functional programming, and so on.</span></span>

<span data-ttu-id="26e8a-122">La définition de service a besoin de deux messages : un pour la demande et un pour le flux.</span><span class="sxs-lookup"><span data-stu-id="26e8a-122">The service definition needs two messages: one for the request, and one for the stream.</span></span> <span data-ttu-id="26e8a-123">Le service retourne un flux de `StockTickerUpdate` message à l’aide du mot clé `stream` dans sa déclaration de `return`.</span><span class="sxs-lookup"><span data-stu-id="26e8a-123">The service returns a stream of the `StockTickerUpdate` message using the `stream` keyword in its `return` declaration.</span></span> <span data-ttu-id="26e8a-124">Il est recommandé d’ajouter une `Timestamp` à la mise à jour pour afficher l’heure exacte du changement de prix.</span><span class="sxs-lookup"><span data-stu-id="26e8a-124">It's recommended that you add a `Timestamp` to the update to show the exact time the price changed.</span></span>

#### <a name="simple_stock_tickerproto"></a><span data-ttu-id="26e8a-125">simple_stock_ticker. proto</span><span class="sxs-lookup"><span data-stu-id="26e8a-125">simple_stock_ticker.proto</span></span>

```protobuf
syntax = "proto3";

option csharp_namespace = "TraderSys.SimpleStockTickerServer.Protos";

import "google/protobuf/timestamp.proto";

package SimpleStockTickerServer;

service SimpleStockTicker {
  rpc Subscribe (SubscribeRequest) returns (stream StockTickerUpdate);
}

message SubscribeRequest {
  repeated string symbols = 1;
}

message StockTickerUpdate {
  string symbol = 1;
  int32 price_cents = 2;
  google.protobuf.Timestamp time = 3;
}
```

### <a name="implement-the-simplestockticker"></a><span data-ttu-id="26e8a-126">Implémenter SimpleStockTicker</span><span class="sxs-lookup"><span data-stu-id="26e8a-126">Implement the SimpleStockTicker</span></span>

<span data-ttu-id="26e8a-127">Réutilisez le `StockPriceSubscriber` factice du projet WCF en copiant les trois classes de la bibliothèque de classes `TraderSys.StockMarket` dans une nouvelle bibliothèque de classes .NET Standard dans la solution cible.</span><span class="sxs-lookup"><span data-stu-id="26e8a-127">Reuse the fake `StockPriceSubscriber` from the WCF project by copying the three classes from the `TraderSys.StockMarket` class library into a new .NET Standard class library in the target solution.</span></span> <span data-ttu-id="26e8a-128">Pour mieux suivre les meilleures pratiques, ajoutez un type de `Factory` pour créer des instances de ce dernier et inscrire le `IStockPriceSubscriberFactory` avec les services d’injection de dépendances de ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="26e8a-128">To better follow best practices, add a `Factory` type to create instances of it and register the `IStockPriceSubscriberFactory` with ASP.NET Core's dependency injection services.</span></span>

#### <a name="the-factory-implementation"></a><span data-ttu-id="26e8a-129">Implémentation de la fabrique</span><span class="sxs-lookup"><span data-stu-id="26e8a-129">The factory implementation</span></span>

```csharp
public interface IStockPriceSubscriberFactory
{
    IStockPriceSubscriber GetSubscriber(string[] symbols);
}

public class StockPriceSubscriberFactory : IStockPriceSubscriberFactory
{
    public IStockPriceSubscriber GetSubscriber(string[] symbols)
    {
        return new StockPriceSubscriber(symbols);
    }
}
```

#### <a name="registering-the-factory"></a><span data-ttu-id="26e8a-130">Inscription de la fabrique</span><span class="sxs-lookup"><span data-stu-id="26e8a-130">Registering the factory</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddGrpc();
    services.AddSingleton<IStockPriceSubscriberFactory, StockPriceSubscriberFactory>();
}
```

<span data-ttu-id="26e8a-131">À présent, cette classe peut être utilisée pour implémenter le service gRPC StockTicker.</span><span class="sxs-lookup"><span data-stu-id="26e8a-131">Now, this class can be used to implement the gRPC StockTicker service.</span></span>

#### <a name="stocktickerservicecs"></a><span data-ttu-id="26e8a-132">StockTickerService.cs</span><span class="sxs-lookup"><span data-stu-id="26e8a-132">StockTickerService.cs</span></span>

```csharp
public class StockTickerService : Protos.SimpleStockTicker.SimpleStockTickerBase
{
    private readonly IStockPriceSubscriberFactory _subscriberFactory;

    public StockTickerService(IStockPriceSubscriberFactory subscriberFactory)
    {
        _subscriberFactory = subscriberFactory;
    }

    public override async Task Subscribe(SubscribeRequest request, IServerStreamWriter<StockTickerUpdate> responseStream, ServerCallContext context)
    {
        var subscriber = _subscriberFactory.GetSubscriber(request.Symbols.ToArray());

        subscriber.Update += async (sender, args) =>
            await WriteUpdateAsync(responseStream, args.Symbol, args.Price);

        await AwaitCancellation(context.CancellationToken);
    }

    private async Task WriteUpdateAsync(IServerStreamWriter<StockTickerUpdate> stream, string symbol, decimal price)
    {
        try
        {
            await stream.WriteAsync(new StockTickerUpdate
            {
                Symbol = symbol,
                PriceCents = (int)(price * 100),
                Time = Timestamp.FromDateTimeOffset(DateTimeOffset.UtcNow)
            });
        }
        catch (Exception e)
        {
            // Handle any errors due to broken connection etc.
            _logger.LogError($"Failed to write message: {e.Message}");
        }
    }

    private static Task AwaitCancellation(CancellationToken token)
    {
        var completion = new TaskCompletionSource<object>();
        token.Register(() => completion.SetResult(null));
        return completion.Task;
    }
}
```

<span data-ttu-id="26e8a-133">Comme vous pouvez le voir, bien que la déclaration dans le fichier `.proto` indique que la méthode retourne un flux de messages `StockTickerUpdate`, en fait, elle retourne un `Task`vanille.</span><span class="sxs-lookup"><span data-stu-id="26e8a-133">As you can see, although the declaration in the `.proto` file says the method "returns" a stream of `StockTickerUpdate` messages, in fact it returns a vanilla `Task`.</span></span> <span data-ttu-id="26e8a-134">Le travail de création du flux est géré par le code généré et les bibliothèques Runtime gRPC, qui fournissent le flux de réponse `IServerStreamWriter<StockTickerUpdate>`, prêt à être utilisé.</span><span class="sxs-lookup"><span data-stu-id="26e8a-134">The job of creating the stream is handled by the generated code and the gRPC runtime libraries, which provide the `IServerStreamWriter<StockTickerUpdate>` response stream, ready to use.</span></span>

<span data-ttu-id="26e8a-135">Contrairement à un service duplex WCF, où l’instance de la classe de service reste active pendant que la connexion est ouverte, le service gRPC utilise la tâche retournée pour maintenir le service actif.</span><span class="sxs-lookup"><span data-stu-id="26e8a-135">Unlike a WCF duplex service, where the instance of the service class is kept alive while the connection is open, the gRPC service uses the returned Task to keep the service alive.</span></span> <span data-ttu-id="26e8a-136">La tâche ne peut pas se terminer tant que la connexion n’est pas fermée.</span><span class="sxs-lookup"><span data-stu-id="26e8a-136">The Task shouldn't complete until the connection is closed.</span></span>

<span data-ttu-id="26e8a-137">Le service peut indiquer à quel moment le client a fermé la connexion à l’aide de l' `CancellationToken` à partir du `ServerCallContext`.</span><span class="sxs-lookup"><span data-stu-id="26e8a-137">The service can tell when the client has closed the connection by using the `CancellationToken` from the `ServerCallContext`.</span></span> <span data-ttu-id="26e8a-138">Une méthode statique simple, `AwaitCancellation`, est utilisée pour créer une tâche qui se termine lorsque le jeton est annulé.</span><span class="sxs-lookup"><span data-stu-id="26e8a-138">A simple static method, `AwaitCancellation`, is used to create a Task that completes when the token is canceled.</span></span>

<span data-ttu-id="26e8a-139">Dans la méthode `Subscribe`, récupérez un `StockPriceSubscriber` et ajoutez un gestionnaire d’événements qui écrit dans le flux de réponse.</span><span class="sxs-lookup"><span data-stu-id="26e8a-139">In the `Subscribe` method, then, get a `StockPriceSubscriber` and add an event handler that writes to the response stream.</span></span> <span data-ttu-id="26e8a-140">Attendez ensuite que la connexion soit fermée, avant de supprimer immédiatement le `subscriber` pour empêcher qu’il tente d’écrire des données dans le flux fermé.</span><span class="sxs-lookup"><span data-stu-id="26e8a-140">Then wait for the connection to be closed, before immediately disposing the `subscriber` to prevent it trying to write data to the closed stream.</span></span>

<span data-ttu-id="26e8a-141">La méthode `WriteUpdateAsync` a un `try`bloc /`catch` pour gérer les erreurs qui peuvent se produire lors de l’écriture d’un message dans le flux.</span><span class="sxs-lookup"><span data-stu-id="26e8a-141">The `WriteUpdateAsync` method has a `try`/`catch` block to handle any errors that might happen when writing a message to the stream.</span></span> <span data-ttu-id="26e8a-142">Il s’agit d’un point important à prendre en compte dans les connexions persistantes sur les réseaux, qui peuvent être interrompues à n’importe quelle milliseconde, que ce soit intentionnellement ou en raison d’une défaillance.</span><span class="sxs-lookup"><span data-stu-id="26e8a-142">This is an important consideration in persistent connections over networks, which could be broken at any millisecond, whether intentionally or because of a failure somewhere.</span></span>

### <a name="using-the-stocktickerservice-from-a-client-application"></a><span data-ttu-id="26e8a-143">Utilisation du StockTickerService à partir d’une application cliente</span><span class="sxs-lookup"><span data-stu-id="26e8a-143">Using the StockTickerService from a client application</span></span>

<span data-ttu-id="26e8a-144">Suivez les mêmes étapes de la section précédente pour créer une bibliothèque de classes de client partageable à partir du fichier `.proto`.</span><span class="sxs-lookup"><span data-stu-id="26e8a-144">Follow the same steps in the previous section to create a shareable client class library from the `.proto` file.</span></span> <span data-ttu-id="26e8a-145">Dans l’exemple, il existe une application console .NET Core 3,0 qui montre comment utiliser le client.</span><span class="sxs-lookup"><span data-stu-id="26e8a-145">In the sample, there's a .NET Core 3.0 console application that demonstrates how to use the client.</span></span>

#### <a name="example-programcs"></a><span data-ttu-id="26e8a-146">Exemple de Program.cs</span><span class="sxs-lookup"><span data-stu-id="26e8a-146">Example Program.cs</span></span>

```csharp
class Program
{
    static async Task Main(string[] args)
    {
        using var channel = GrpcChannel.ForAddress("https://localhost:5001");
        var client = new SimpleStockTicker.SimpleStockTickerClient(channel);

        var request = new SubscribeRequest();
        request.Symbols.AddRange(args);

        using var stream = client.Subscribe(request);

        var tokenSource = new CancellationTokenSource();

        var task = DisplayAsync(stream.ResponseStream, tokenSource.Token);

        WaitForExitKey();

        tokenSource.Cancel();
        await task;
    }
}
```

<span data-ttu-id="26e8a-147">Dans ce cas, la méthode `Subscribe` sur le client généré n’est pas asynchrone.</span><span class="sxs-lookup"><span data-stu-id="26e8a-147">In this case, the `Subscribe` method on the generated client isn't asynchronous.</span></span> <span data-ttu-id="26e8a-148">Le flux est créé et utilisable immédiatement, car sa méthode `MoveNext` est asynchrone et la première fois qu’il est appelé, il ne se termine pas tant que la connexion n’est pas active.</span><span class="sxs-lookup"><span data-stu-id="26e8a-148">The stream is created and usable right away, because its `MoveNext` method is asynchronous and the first time it's called it won't complete until the connection is alive.</span></span>

<span data-ttu-id="26e8a-149">Le flux est passé à une méthode `DisplayAsync` Async ; l’application attend ensuite que l’utilisateur appuie sur une touche, puis annule la méthode `DisplayAsync` et attend la fin de la tâche avant de quitter.</span><span class="sxs-lookup"><span data-stu-id="26e8a-149">The stream is passed to an async `DisplayAsync` method; the application then waits for the user to press a key, then cancels the `DisplayAsync` method and waits for the task to complete before exiting.</span></span>

> [!NOTE]
> <span data-ttu-id="26e8a-150">Ce code utilise la nouvelle C# syntaxe 8 « using DECLARATION » pour supprimer le flux et le canal quand la méthode `Main` se termine.</span><span class="sxs-lookup"><span data-stu-id="26e8a-150">This code is using the new C# 8 "using declaration" syntax to dispose of the stream and the channel when the `Main` method exits.</span></span> <span data-ttu-id="26e8a-151">C’est une petite modification, mais une bonne chose qui réduit les retraits et les lignes vides.</span><span class="sxs-lookup"><span data-stu-id="26e8a-151">It's a small change, but a nice one that reduces indentations and empty lines.</span></span>

#### <a name="consume-the-stream"></a><span data-ttu-id="26e8a-152">Utiliser le flux</span><span class="sxs-lookup"><span data-stu-id="26e8a-152">Consume the stream</span></span>

<span data-ttu-id="26e8a-153">WCF utilisait des interfaces de rappel pour permettre au serveur d’appeler des méthodes directement sur le client.</span><span class="sxs-lookup"><span data-stu-id="26e8a-153">WCF used callback interfaces to allow the server to call methods directly on the client.</span></span> <span data-ttu-id="26e8a-154">les flux gRPC fonctionnent différemment.</span><span class="sxs-lookup"><span data-stu-id="26e8a-154">gRPC streams work differently.</span></span> <span data-ttu-id="26e8a-155">Le client itère au sein du flux retourné et traite les messages, comme s’ils étaient retournés par une méthode locale retournant un `IEnumerable`.</span><span class="sxs-lookup"><span data-stu-id="26e8a-155">The client iterates over the returned stream and processes messages, just as though they were returned from a local method returning an `IEnumerable`.</span></span>

<span data-ttu-id="26e8a-156">Le type de `IAsyncStreamReader<T>` fonctionne très bien comme un `IEnumerator<T>`: il existe une méthode `MoveNext` qui retourne la valeur true tant qu’il y a plus de données, et une propriété `Current` qui retourne la valeur la plus récente.</span><span class="sxs-lookup"><span data-stu-id="26e8a-156">The `IAsyncStreamReader<T>` type works much like an `IEnumerator<T>`: there's a `MoveNext` method that will return true as long as there's more data, and a `Current` property that returns the latest value.</span></span> <span data-ttu-id="26e8a-157">La seule différence est que la méthode `MoveNext` retourne un `Task<bool>` au lieu d’une seule `bool`.</span><span class="sxs-lookup"><span data-stu-id="26e8a-157">The only difference is that the `MoveNext` method returns a `Task<bool>` instead of just a `bool`.</span></span> <span data-ttu-id="26e8a-158">La méthode d’extension `ReadAllAsync` encapsule le flux dans une C# `IAsyncEnumerable` standard de 8 qui peut être utilisée avec la nouvelle syntaxe de `await foreach`.</span><span class="sxs-lookup"><span data-stu-id="26e8a-158">The `ReadAllAsync` extension method wraps the stream in a standard C# 8 `IAsyncEnumerable` that can be used with the new `await foreach` syntax.</span></span>

```csharp
static async Task DisplayAsync(IAsyncStreamReader<StockTickerUpdate> stream, CancellationToken token)
{
    try
    {
        await foreach (var update in stream.ReadAllAsync(token))
        {
            Console.WriteLine($"{update.Symbol}: {update.Price}");
        }
    }
    catch (RpcException e) when (e.StatusCode == StatusCode.Cancelled)
    {
        return;
    }
    catch (OperationCanceledException)
    {
        Console.WriteLine("Finished.");
    }
}
```

> [!TIP]
> <span data-ttu-id="26e8a-159">La section sur les [bibliothèques clientes](client-libraries.md#iobservable) à la fin de ce chapitre explique comment ajouter une méthode d’extension et des classes pour encapsuler `IAsyncStreamReader<T>` dans une `IObservable<T>` pour les développeurs qui utilisent des modèles de programmation réactifs.</span><span class="sxs-lookup"><span data-stu-id="26e8a-159">The section on [client libraries](client-libraries.md#iobservable) at the end of this chapter looks at how to add an extension method and classes to wrap `IAsyncStreamReader<T>` in an `IObservable<T>` for developers using reactive programming patterns.</span></span>

<span data-ttu-id="26e8a-160">Là encore, veillez à intercepter les exceptions ici en raison de la possibilité d’une défaillance du réseau, ainsi que des <xref:System.OperationCanceledException> qui seront inévitablement levées, car le code utilise un <xref:System.Threading.CancellationToken> pour rompre la boucle.</span><span class="sxs-lookup"><span data-stu-id="26e8a-160">Again, be careful to catch exceptions here because of the possibility of network failure, as well as the <xref:System.OperationCanceledException> that will inevitably be thrown because the code is using a <xref:System.Threading.CancellationToken> to break the loop.</span></span> <span data-ttu-id="26e8a-161">Le type de `RpcException` contient de nombreuses informations utiles sur les erreurs d’exécution gRPC, y compris les `StatusCode`.</span><span class="sxs-lookup"><span data-stu-id="26e8a-161">The `RpcException` type has a lot of useful information about gRPC runtime errors, including the `StatusCode`.</span></span> <span data-ttu-id="26e8a-162">Pour plus d’informations, consultez [ *gestion des erreurs* dans le chapitre 4](error-handling.md).</span><span class="sxs-lookup"><span data-stu-id="26e8a-162">For more information, see [*Error handling* in Chapter 4](error-handling.md).</span></span>

## <a name="bidirectional-streaming"></a><span data-ttu-id="26e8a-163">Diffusion bidirectionnelle</span><span class="sxs-lookup"><span data-stu-id="26e8a-163">Bidirectional streaming</span></span>

<span data-ttu-id="26e8a-164">Un service WCF Full-duplex permet une messagerie asynchrone et en temps réel dans les deux sens.</span><span class="sxs-lookup"><span data-stu-id="26e8a-164">A WCF full-duplex service allows for asynchronous, real-time messaging in both directions.</span></span> <span data-ttu-id="26e8a-165">Dans l’exemple de diffusion en continu du serveur, le client démarre une demande, puis reçoit un flux de mises à jour.</span><span class="sxs-lookup"><span data-stu-id="26e8a-165">In the server streaming example, the client starts a request, then receives a stream of updates.</span></span> <span data-ttu-id="26e8a-166">Une meilleure version de ce service permettrait au client d’ajouter et de supprimer des actions de la liste sans avoir à arrêter et à créer un nouvel abonnement.</span><span class="sxs-lookup"><span data-stu-id="26e8a-166">A better version of that service would allow the client to add and remove stocks from the list without having to stop and create a new subscription.</span></span> <span data-ttu-id="26e8a-167">Cette fonctionnalité a été implémentée dans l' [exemple de solution FullStockTicker](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/wcf/FullStockTicker).</span><span class="sxs-lookup"><span data-stu-id="26e8a-167">That functionality has been implemented in the [FullStockTicker sample solution](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/wcf/FullStockTicker).</span></span>

<span data-ttu-id="26e8a-168">L’interface `IFullStockTickerService` fournit trois méthodes :</span><span class="sxs-lookup"><span data-stu-id="26e8a-168">The `IFullStockTickerService` interface provides three methods:</span></span>

- <span data-ttu-id="26e8a-169">`Subscribe` démarre la connexion.</span><span class="sxs-lookup"><span data-stu-id="26e8a-169">`Subscribe` starts the connection.</span></span>
- <span data-ttu-id="26e8a-170">`AddSymbol` ajoute un symbole de stock à surveiller.</span><span class="sxs-lookup"><span data-stu-id="26e8a-170">`AddSymbol` adds a stock symbol to watch.</span></span>
- <span data-ttu-id="26e8a-171">`RemoveSymbol` supprime un symbole de la liste de suivi.</span><span class="sxs-lookup"><span data-stu-id="26e8a-171">`RemoveSymbol` removes a symbol from the watched list.</span></span>

```csharp
[ServiceContract(SessionMode = SessionMode.Required, CallbackContract = typeof(IFullStockTickerCallback))]
public interface IFullStockTickerService
{
    [OperationContract(IsOneWay = true)]
    void Subscribe();

    [OperationContract(IsOneWay = true)]
    void AddSymbol(string symbol);

    [OperationContract(IsOneWay = true)]
    void RemoveSymbol(string symbol);
}
```

<span data-ttu-id="26e8a-172">L’interface de rappel reste la même.</span><span class="sxs-lookup"><span data-stu-id="26e8a-172">The callback interface remains the same.</span></span>

<span data-ttu-id="26e8a-173">L’implémentation de ce modèle dans gRPC est moins simple, car il existe désormais deux flux de données avec des messages transmis : un du client au serveur et un autre du serveur au client.</span><span class="sxs-lookup"><span data-stu-id="26e8a-173">Implementing this pattern in gRPC is less straightforward, because there are now two streams of data with messages being passed: one from client to server, and another from server to client.</span></span> <span data-ttu-id="26e8a-174">Il n’est pas possible d’utiliser plusieurs méthodes pour implémenter l’opération d’ajout et de suppression, mais plusieurs types de messages peuvent être transmis sur un seul flux, en utilisant le type `Any` ou `oneof` mot clé, qui a été traité dans le [chapitre 3](protobuf-any-oneof.md).</span><span class="sxs-lookup"><span data-stu-id="26e8a-174">It isn't possible to use multiple methods to implement the Add and Remove operation, but more than one type of message can be passed on a single stream, using either the `Any` type or `oneof` keyword, which were covered in [Chapter 3](protobuf-any-oneof.md).</span></span>

<span data-ttu-id="26e8a-175">Dans le cas d’un ensemble spécifique de types acceptables, `oneof` est une meilleure façon de le faire.</span><span class="sxs-lookup"><span data-stu-id="26e8a-175">For a case where there's a specific set of types that are acceptable, `oneof` is a better way to go.</span></span> <span data-ttu-id="26e8a-176">Utilisez une `ActionMessage` qui peut contenir un `AddSymbolRequest` ou un `RemoveSymbolRequest`.</span><span class="sxs-lookup"><span data-stu-id="26e8a-176">Use an `ActionMessage` that can hold either an `AddSymbolRequest` or a `RemoveSymbolRequest`.</span></span>

```protobuf
message ActionMessage {
  oneof action {
    AddSymbolRequest add = 1;
    RemoveSymbolRequest remove = 2;
  }
}

message AddSymbolRequest {
  string symbol = 1;
}

message RemoveSymbolRequest {
  string symbol = 1;
}
```

<span data-ttu-id="26e8a-177">Déclarez un service de streaming bidirectionnel qui prend un flux de messages `ActionMessage`.</span><span class="sxs-lookup"><span data-stu-id="26e8a-177">Declare a bi-directional streaming service that takes a stream of `ActionMessage` messages.</span></span>

```protobuf
service FullStockTicker {
  rpc Subscribe (stream ActionMessage) returns (stream StockTickerUpdate);
}
```

<span data-ttu-id="26e8a-178">L’implémentation de ce service est similaire à l’exemple précédent, sauf que le premier paramètre de la méthode `Subscribe` est désormais un `IAsyncStreamReader<ActionMessage>`, qui peut être utilisé pour gérer les demandes `Add` et `Remove`.</span><span class="sxs-lookup"><span data-stu-id="26e8a-178">The implementation for this service is similar to the previous example, except the first parameter of the `Subscribe` method is now an `IAsyncStreamReader<ActionMessage>`, which can be used to handle the `Add` and `Remove` requests.</span></span>

```csharp
public override async Task Subscribe(IAsyncStreamReader<ActionMessage> requestStream, IServerStreamWriter<StockTickerUpdate> responseStream, ServerCallContext context)
{
    using var subscriber = _subscriberFactory.GetSubscriber();

    subscriber.Update += async (sender, args) =>
        await WriteUpdateAsync(responseStream, args.Symbol, args.Price);

    var actionsTask = HandleActions(requestStream, subscriber, context.CancellationToken);

    _logger.LogInformation("Subscription started.");
    await AwaitCancellation(context.CancellationToken);

    try { await actionsTask; } catch { /* Ignored */ }

    _logger.LogInformation("Subscription finished.");
}

private async Task WriteUpdateAsync(IServerStreamWriter<StockTickerUpdate> stream, string symbol, decimal price)
{
    try
    {
        await stream.WriteAsync(new StockTickerUpdate
        {
            Symbol = symbol,
            PriceCents = (int)(price * 100),
            Time = Timestamp.FromDateTimeOffset(DateTimeOffset.UtcNow)
        });
    }
    catch (Exception e)
    {
        // Handle any errors due to broken connection etc.
        _logger.LogError($"Failed to write message: {e.Message}");
    }
}

private static Task AwaitCancellation(CancellationToken token)
{
    var completion = new TaskCompletionSource<object>();
    token.Register(() => completion.SetResult(null));
    return completion.Task;
}
```

<span data-ttu-id="26e8a-179">La classe `ActionMessage` que gRPC a généré pour nous garantit qu’une seule des propriétés `Add` et `Remove` peut être définie, et la recherche de celle qui n’est pas `null` est un moyen valide de trouver le type de message utilisé, mais il existe une meilleure méthode.</span><span class="sxs-lookup"><span data-stu-id="26e8a-179">The `ActionMessage` class that gRPC has generated for us guarantees that only one of the `Add` and `Remove` properties can be set, and finding which one isn't `null` is a valid way of finding which type of message is used, but there's a better way.</span></span> <span data-ttu-id="26e8a-180">La génération de code a également créé une `enum ActionOneOfCase` dans la classe `ActionMessage`, qui ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="26e8a-180">The code generation also created an `enum ActionOneOfCase` in the `ActionMessage` class, which looks like this:</span></span>

```csharp
public enum ActionOneofCase {
    None = 0,
    Add = 1,
    Remove = 2,
}
```

<span data-ttu-id="26e8a-181">La propriété `ActionCase` sur l’objet `ActionMessage` peut être utilisée avec une instruction `switch` pour déterminer quel champ est défini.</span><span class="sxs-lookup"><span data-stu-id="26e8a-181">The property `ActionCase` on the `ActionMessage` object can be used with a `switch` statement to determine which field is set.</span></span>

```csharp
private async Task HandleActions(IAsyncStreamReader<ActionMessage> requestStream, IFullStockPriceSubscriber subscriber, CancellationToken token)
{
    await foreach (var action in requestStream.ReadAllAsync(token))
    {
        switch (action.ActionCase)
        {
            case ActionMessage.ActionOneofCase.None:
                _logger.LogWarning("No Action specified.");
                break;
            case ActionMessage.ActionOneofCase.Add:
                subscriber.Add(action.Add.Symbol);
                break;
            case ActionMessage.ActionOneofCase.Remove:
                subscriber.Remove(action.Remove.Symbol);
                break;
            default:
                _logger.LogWarning($"Unknown Action '{action.ActionCase}'.");
                break;
        }
    }
}
```

> [!TIP]
> <span data-ttu-id="26e8a-182">L’instruction `switch` a un cas `default` qui enregistre un avertissement en cas de détection d’une valeur de `ActionOneOfCase` inconnue.</span><span class="sxs-lookup"><span data-stu-id="26e8a-182">The `switch` statement has a `default` case that logs a warning if an unknown `ActionOneOfCase` value is encountered.</span></span> <span data-ttu-id="26e8a-183">Cela peut être utile pour indiquer qu’un client utilise une version plus récente du fichier `.proto` qui a ajouté d’autres actions.</span><span class="sxs-lookup"><span data-stu-id="26e8a-183">This could be useful in indicating that a client is using a later version of the `.proto` file which has added more actions.</span></span> <span data-ttu-id="26e8a-184">C’est l’une des raisons pour lesquelles l’utilisation d’un `switch` est meilleure que le test de `null` sur des champs connus.</span><span class="sxs-lookup"><span data-stu-id="26e8a-184">This is one reason why using a `switch` is better than testing for `null` on known fields.</span></span>

### <a name="use-the-fullstocktickerservice-from-a-client-application"></a><span data-ttu-id="26e8a-185">Utiliser FullStockTickerService à partir d’une application cliente</span><span class="sxs-lookup"><span data-stu-id="26e8a-185">Use the FullStockTickerService from a client application</span></span>

<span data-ttu-id="26e8a-186">Il existe une simple application WPF .NET Core 3,0 pour illustrer l’utilisation de ce client plus complexe.</span><span class="sxs-lookup"><span data-stu-id="26e8a-186">There's a simple .NET Core 3.0 WPF application to demonstrate use of this more complex client.</span></span> <span data-ttu-id="26e8a-187">L’application complète est disponible [sur GitHub](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTicker).</span><span class="sxs-lookup"><span data-stu-id="26e8a-187">The full application can be found [on GitHub](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTicker).</span></span>

<span data-ttu-id="26e8a-188">Le client est utilisé dans la classe `MainWindowViewModel`, qui obtient une instance du type `FullStockTicker.FullStockTickerClient` à partir de l’injection de dépendances.</span><span class="sxs-lookup"><span data-stu-id="26e8a-188">The client is used in the `MainWindowViewModel` class, which gets an instance of the `FullStockTicker.FullStockTickerClient` type from dependency injection.</span></span>

```csharp
public class MainWindowViewModel : IAsyncDisposable, INotifyPropertyChanged
{
    private readonly FullStockTicker.FullStockTickerClient _client;
    private readonly AsyncDuplexStreamingCall<ActionMessage, StockTickerUpdate> _duplexStream;
    private readonly CancellationTokenSource _cancellationTokenSource;
    private readonly Task _responseTask;
    private string _addSymbol;

    public MainWindowViewModel(FullStockTicker.FullStockTickerClient client)
    {
        _cancellationTokenSource = new CancellationTokenSource();
        _client = client;
        _duplexStream = _client.Subscribe();
        _responseTask = HandleResponsesAsync(_cancellationTokenSource.Token);

        AddCommand = new AsyncCommand(Add, CanAdd);
    }
```

<span data-ttu-id="26e8a-189">L’objet retourné par la méthode `client.Subscribe()` est désormais une instance du type de bibliothèque gRPC `AsyncDuplexStreamingCall<TRequest, TResponse>`, qui fournit une `RequestStream` pour l’envoi de demandes au serveur et une `ResponseStream` pour la gestion des réponses.</span><span class="sxs-lookup"><span data-stu-id="26e8a-189">The object returned by the `client.Subscribe()` method is now an instance of the gRPC library type `AsyncDuplexStreamingCall<TRequest, TResponse>`, which provides a `RequestStream` for sending requests to the server, and a `ResponseStream` for handling responses.</span></span>

<span data-ttu-id="26e8a-190">Le flux de requête est utilisé à partir de certaines méthodes de `ICommand` WPF pour ajouter et supprimer des symboles.</span><span class="sxs-lookup"><span data-stu-id="26e8a-190">The request stream is used from some WPF `ICommand` methods to add and remove symbols.</span></span> <span data-ttu-id="26e8a-191">Pour chaque opération, définissez le champ approprié sur un objet `ActionMessage` :</span><span class="sxs-lookup"><span data-stu-id="26e8a-191">For each operation, set the relevant field on an `ActionMessage` object:</span></span>

```csharp
private async Task Add()
{
    if (CanAdd())
    {
        await _duplexStream.RequestStream.WriteAsync(new ActionMessage {Add = new AddSymbolRequest {Symbol = AddSymbol}});
    }
}

public async Task Remove(PriceViewModel priceViewModel)
{
    await _duplexStream.RequestStream.WriteAsync(new ActionMessage {Remove = new RemoveSymbolRequest {Symbol = priceViewModel.Symbol}});
    Prices.Remove(priceViewModel);
}
```

> [!IMPORTANT]
> <span data-ttu-id="26e8a-192">La définition de la valeur d’un champ `oneof` sur un message efface automatiquement tous les champs qui ont été définis précédemment.</span><span class="sxs-lookup"><span data-stu-id="26e8a-192">Setting a `oneof` field's value on a message automatically clears any fields that have been previously set.</span></span>

<span data-ttu-id="26e8a-193">Le flux de réponses est géré dans une méthode `async`, et la `Task` retourne est conservée pour être supprimée lorsque la fenêtre est fermée.</span><span class="sxs-lookup"><span data-stu-id="26e8a-193">The stream of responses is handled in an `async` method, and the `Task` it returns is held to be disposed when the window is closed.</span></span>

```csharp
private async Task HandleResponsesAsync(CancellationToken token)
{
    var stream = _duplexStream.ResponseStream;

    try
    {
        await foreach (var update in stream.ReadAllAsync(token))
        {
            var price = Prices.FirstOrDefault(p => p.Symbol.Equals(update.Symbol));
            if (price == null)
            {
                price = new PriceViewModel(this) {Symbol = update.Symbol, Price = update.PriceCents / 100m};
                Prices.Add(price);
            }
            else
            {
                price.Price = update.PriceCents / 100m;
            }
        }
    }
    catch (OperationCancelledException) { }
}
```

### <a name="client-clean-up"></a><span data-ttu-id="26e8a-194">Nettoyage du client</span><span class="sxs-lookup"><span data-stu-id="26e8a-194">Client clean-up</span></span>

<span data-ttu-id="26e8a-195">Lorsque la fenêtre est fermée et que le `MainWindowViewModel` est supprimé (à partir de l’événement `Closed` de `MainWindow`), il est recommandé de supprimer correctement l’objet `AsyncDuplexStreamingCall`.</span><span class="sxs-lookup"><span data-stu-id="26e8a-195">When the window is closed and the `MainWindowViewModel` is disposed (from the `Closed` event of `MainWindow`), it's recommended that you properly dispose the `AsyncDuplexStreamingCall` object.</span></span> <span data-ttu-id="26e8a-196">En particulier, la méthode `CompleteAsync` sur le `RequestStream` doit être appelée pour fermer correctement le flux sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="26e8a-196">In particular, the `CompleteAsync` method on the `RequestStream` should be called to gracefully close the stream on the server.</span></span> <span data-ttu-id="26e8a-197">L’exemple suivant illustre la méthode `DisposeAsync` de l’exemple de modèle d’affichage :</span><span class="sxs-lookup"><span data-stu-id="26e8a-197">The following example shows the `DisposeAsync` method from the sample view-model:</span></span>

```csharp
public ValueTask DisposeAsync()
{
    try
    {
        await _duplexStream.RequestStream.CompleteAsync().ConfigureAwait(false);
        await _responseTask.ConfigureAwait(false);
    }
    finally
    {
        _duplexStream.Dispose();
    }
}
```

<span data-ttu-id="26e8a-198">La fermeture des flux de requête permet au serveur de supprimer ses propres ressources en temps opportun.</span><span class="sxs-lookup"><span data-stu-id="26e8a-198">Closing request streams enables the server to dispose of its own resources in a timely manner.</span></span> <span data-ttu-id="26e8a-199">Cela améliore l’efficacité et l’évolutivité des services et empêche les exceptions.</span><span class="sxs-lookup"><span data-stu-id="26e8a-199">This improves the efficiency and scalability of services and prevents exceptions.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="26e8a-200">[Précédent](migrate-request-reply.md)
>[Suivant](streaming-versus-repeated.md)</span><span class="sxs-lookup"><span data-stu-id="26e8a-200">[Previous](migrate-request-reply.md)
[Next](streaming-versus-repeated.md)</span></span>
