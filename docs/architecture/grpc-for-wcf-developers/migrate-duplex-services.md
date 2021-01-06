---
title: Migrer les services duplex WCF vers gRPC-gRPC pour les développeurs WCF
description: Découvrez comment migrer diverses formes de services duplex WCF vers des services de streaming gRPC.
ms.date: 12/15/2020
ms.openlocfilehash: 4741e5ad5c12fa358853381d4f2c286add14f8f5
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938024"
---
# <a name="migrate-wcf-duplex-services-to-grpc"></a><span data-ttu-id="ccdd7-103">Migrer les services duplex WCF vers gRPC</span><span class="sxs-lookup"><span data-stu-id="ccdd7-103">Migrate WCF duplex services to gRPC</span></span>

<span data-ttu-id="ccdd7-104">Maintenant que vous avez un sens des concepts de base, dans cette section, vous allez examiner les services gRPC de *diffusion en continu* plus compliqués.</span><span class="sxs-lookup"><span data-stu-id="ccdd7-104">Now that you have a sense of the basic concepts, in this section, you'll look at the more complicated *streaming* gRPC services.</span></span>

<span data-ttu-id="ccdd7-105">Il existe plusieurs façons d’utiliser les services duplex dans Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="ccdd7-105">There are multiple ways to use duplex services in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="ccdd7-106">Certains services sont initiés par le client, puis diffusent en continu des données à partir du serveur.</span><span class="sxs-lookup"><span data-stu-id="ccdd7-106">Some services are initiated by the client and then they stream data from the server.</span></span> <span data-ttu-id="ccdd7-107">D’autres services duplex intégral peuvent impliquer une communication bidirectionnelle continue, comme l’exemple de calculatrice classique dans la documentation WCF.</span><span class="sxs-lookup"><span data-stu-id="ccdd7-107">Other full-duplex services might involve more ongoing two-way communication, like the classic Calculator example in the WCF documentation.</span></span> <span data-ttu-id="ccdd7-108">Ce chapitre prend en compte deux implémentations possibles de l’application de cotations boursières WCF et les migre vers gRPC : une qui utilise un RPC de streaming de serveur et une autre qui utilise un RPC de streaming bidirectionnel.</span><span class="sxs-lookup"><span data-stu-id="ccdd7-108">This chapter will take two possible WCF stock ticker implementations and migrate them to gRPC: one that uses a server streaming RPC and another one that uses a bidirectional streaming RPC.</span></span>

## <a name="server-streaming-rpc"></a><span data-ttu-id="ccdd7-109">RPC de streaming de serveur</span><span class="sxs-lookup"><span data-stu-id="ccdd7-109">Server streaming RPC</span></span>

<span data-ttu-id="ccdd7-110">Dans l' [exemple de solution WCF SimpleStockTicker](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/SimpleStockTickerSample/wcf/SimpleStockTicker), SimpleStockPriceTicker, il existe un service duplex pour lequel le client démarre la connexion avec une liste de symboles boursiers, et le serveur utilise l' *interface de rappel* pour envoyer des mises à jour dès qu’elles sont disponibles.</span><span class="sxs-lookup"><span data-stu-id="ccdd7-110">In the [sample SimpleStockTicker WCF solution](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/SimpleStockTickerSample/wcf/SimpleStockTicker), SimpleStockPriceTicker, there's a duplex service for which the client starts the connection with a list of stock symbols, and the server uses the *callback interface* to send updates as they become available.</span></span> <span data-ttu-id="ccdd7-111">Le client implémente cette interface pour répondre aux appels à partir du serveur.</span><span class="sxs-lookup"><span data-stu-id="ccdd7-111">The client implements that interface to respond to calls from the server.</span></span>

### <a name="the-wcf-solution"></a><span data-ttu-id="ccdd7-112">La solution WCF</span><span class="sxs-lookup"><span data-stu-id="ccdd7-112">The WCF solution</span></span>

<span data-ttu-id="ccdd7-113">La solution WCF est implémentée en tant que serveur net. TCP auto-hébergé dans un .NET Framework 4. *x* application console.</span><span class="sxs-lookup"><span data-stu-id="ccdd7-113">The WCF solution is implemented as a self-hosted Net.TCP server in a .NET Framework 4.*x* console application.</span></span>

#### <a name="servicecontract"></a><span data-ttu-id="ccdd7-114">ServiceContract</span><span class="sxs-lookup"><span data-stu-id="ccdd7-114">ServiceContract</span></span>

```csharp
[ServiceContract(SessionMode = SessionMode.Required, CallbackContract = typeof(ISimpleStockTickerCallback))]
public interface ISimpleStockTickerService
{
    [OperationContract(IsOneWay = true)]
    void Subscribe(string[] symbols);
}
```

<span data-ttu-id="ccdd7-115">Le service a une méthode unique sans type de retour, car il utilise l’interface `ISimpleStockTickerCallback` de rappel pour envoyer des données au client en temps réel.</span><span class="sxs-lookup"><span data-stu-id="ccdd7-115">The service has a single method with no return type because it uses the callback interface `ISimpleStockTickerCallback` to send data to the client in real time.</span></span>

#### <a name="the-callback-interface"></a><span data-ttu-id="ccdd7-116">Interface de rappel</span><span class="sxs-lookup"><span data-stu-id="ccdd7-116">The callback interface</span></span>

```csharp
[ServiceContract]
public interface ISimpleStockTickerCallback
{
    [OperationContract(IsOneWay = true)]
    void Update(string symbol, decimal price);
}
```

<span data-ttu-id="ccdd7-117">Vous pouvez trouver les implémentations de ces interfaces dans la solution, ainsi que les dépendances externes factices pour fournir des données de test.</span><span class="sxs-lookup"><span data-stu-id="ccdd7-117">You can find the implementations of these interfaces in the solution, along with faked external dependencies to provide test data.</span></span>

### <a name="grpc-streaming"></a><span data-ttu-id="ccdd7-118">diffusion en continu gRPC</span><span class="sxs-lookup"><span data-stu-id="ccdd7-118">gRPC streaming</span></span>

<span data-ttu-id="ccdd7-119">Le processus de gRPC pour le traitement des données en temps réel est différent du processus WCF.</span><span class="sxs-lookup"><span data-stu-id="ccdd7-119">The gRPC process for handling real-time data is different from the WCF process.</span></span> <span data-ttu-id="ccdd7-120">Un appel du client au serveur peut créer un flux persistant, qui peut être surveillé pour les messages arrivant de manière asynchrone.</span><span class="sxs-lookup"><span data-stu-id="ccdd7-120">A call from client to server can create a persistent stream, which can be monitored for messages that arrive asynchronously.</span></span> <span data-ttu-id="ccdd7-121">Malgré la différence, les flux peuvent être un moyen plus intuitif de traiter ces données et sont plus pertinents dans la programmation moderne, qui met l’accent sur LINQ, les flux réactifs, la programmation fonctionnelle, etc.</span><span class="sxs-lookup"><span data-stu-id="ccdd7-121">Despite the difference, streams can be a more intuitive way of dealing with this data and are more relevant in modern programming, which emphasizes LINQ, Reactive Streams, functional programming, and so on.</span></span>

<span data-ttu-id="ccdd7-122">La définition de service a besoin de deux messages : un pour la demande et un pour le flux.</span><span class="sxs-lookup"><span data-stu-id="ccdd7-122">The service definition needs two messages: one for the request and one for the stream.</span></span> <span data-ttu-id="ccdd7-123">Le service retourne un flux du `StockTickerUpdate` message avec le `stream` mot clé dans sa `return` déclaration.</span><span class="sxs-lookup"><span data-stu-id="ccdd7-123">The service returns a stream of the `StockTickerUpdate` message with the `stream` keyword in its `return` declaration.</span></span> <span data-ttu-id="ccdd7-124">Nous vous recommandons d’ajouter un `Timestamp` à la mise à jour pour afficher l’heure exacte de la modification du prix.</span><span class="sxs-lookup"><span data-stu-id="ccdd7-124">We recommend that you add a `Timestamp` to the update to show the exact time of the price change.</span></span>

#### <a name="simple_stock_tickerproto"></a><span data-ttu-id="ccdd7-125">simple_stock_ticker. proto</span><span class="sxs-lookup"><span data-stu-id="ccdd7-125">simple_stock_ticker.proto</span></span>

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

### <a name="implement-simplestockticker"></a><span data-ttu-id="ccdd7-126">Implémenter SimpleStockTicker</span><span class="sxs-lookup"><span data-stu-id="ccdd7-126">Implement SimpleStockTicker</span></span>

<span data-ttu-id="ccdd7-127">Réutilisez le substitut du `StockPriceSubscriber` projet WCF en copiant les trois classes de la `TraderSys.StockMarket` bibliothèque de classes dans une nouvelle bibliothèque de classes .NET standard dans la solution cible.</span><span class="sxs-lookup"><span data-stu-id="ccdd7-127">Reuse the fake `StockPriceSubscriber` from the WCF project by copying the three classes from the `TraderSys.StockMarket` class library into a new .NET Standard class library in the target solution.</span></span> <span data-ttu-id="ccdd7-128">Pour mieux suivre les meilleures pratiques, ajoutez un `Factory` type pour créer des instances de celui-ci, puis inscrivez-vous `IStockPriceSubscriberFactory` auprès du ASP.net Core Services d’injection de dépendances.</span><span class="sxs-lookup"><span data-stu-id="ccdd7-128">To better follow best practices, add a `Factory` type to create instances of it, and register the `IStockPriceSubscriberFactory` with the ASP.NET Core dependency injection services.</span></span>

#### <a name="the-factory-implementation"></a><span data-ttu-id="ccdd7-129">Implémentation de la fabrique</span><span class="sxs-lookup"><span data-stu-id="ccdd7-129">The factory implementation</span></span>

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

#### <a name="register-the-factory"></a><span data-ttu-id="ccdd7-130">Inscrire la fabrique</span><span class="sxs-lookup"><span data-stu-id="ccdd7-130">Register the factory</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddGrpc();
    services.AddSingleton<IStockPriceSubscriberFactory, StockPriceSubscriberFactory>();
}
```

<span data-ttu-id="ccdd7-131">Cette classe peut maintenant être utilisée pour implémenter le gRPC `StockTickerService` .</span><span class="sxs-lookup"><span data-stu-id="ccdd7-131">This class can now be used to implement the gRPC `StockTickerService`.</span></span>

#### <a name="stocktickerservicecs"></a><span data-ttu-id="ccdd7-132">StockTickerService.cs</span><span class="sxs-lookup"><span data-stu-id="ccdd7-132">StockTickerService.cs</span></span>

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
            // Handle any errors caused by broken connection, etc.
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

<span data-ttu-id="ccdd7-133">Comme vous pouvez le voir, bien que la déclaration dans le `.proto` fichier indique que la méthode retourne un flux de `StockTickerUpdate` messages, elle retourne en fait un `Task` .</span><span class="sxs-lookup"><span data-stu-id="ccdd7-133">As you can see, although the declaration in the `.proto` file says the method returns a stream of `StockTickerUpdate` messages, it actually returns a `Task`.</span></span> <span data-ttu-id="ccdd7-134">Le travail de création du flux est géré par le code généré et les bibliothèques d’exécution gRPC, qui fournissent le `IServerStreamWriter<StockTickerUpdate>` flux de réponse, prêt à être utilisé.</span><span class="sxs-lookup"><span data-stu-id="ccdd7-134">The job of creating the stream is handled by the generated code and the gRPC runtime libraries, which provide the `IServerStreamWriter<StockTickerUpdate>` response stream, ready to use.</span></span>

<span data-ttu-id="ccdd7-135">Contrairement à un service duplex WCF, où l’instance de la classe de service reste active pendant que la connexion est ouverte, le service gRPC utilise la tâche retournée pour maintenir le service actif.</span><span class="sxs-lookup"><span data-stu-id="ccdd7-135">Unlike a WCF duplex service, where the instance of the service class is kept alive while the connection is open, the gRPC service uses the returned task to keep the service alive.</span></span> <span data-ttu-id="ccdd7-136">La tâche ne peut pas se terminer tant que la connexion n’est pas fermée.</span><span class="sxs-lookup"><span data-stu-id="ccdd7-136">The task shouldn't complete until the connection is closed.</span></span>

<span data-ttu-id="ccdd7-137">Le service peut savoir à quel moment le client a fermé la connexion à l’aide de l' `CancellationToken` de l' `ServerCallContext` .</span><span class="sxs-lookup"><span data-stu-id="ccdd7-137">The service can tell when the client has closed the connection by using the `CancellationToken` from the `ServerCallContext`.</span></span> <span data-ttu-id="ccdd7-138">Une méthode statique simple, `AwaitCancellation` , est utilisée pour créer une tâche qui se termine lorsque le jeton est annulé.</span><span class="sxs-lookup"><span data-stu-id="ccdd7-138">A simple static method, `AwaitCancellation`, is used to create a task that completes when the token is canceled.</span></span>

<span data-ttu-id="ccdd7-139">Dans la `Subscribe` méthode, récupérez un `StockPriceSubscriber` et ajoutez un gestionnaire d’événements qui écrit dans le flux de réponse.</span><span class="sxs-lookup"><span data-stu-id="ccdd7-139">In the `Subscribe` method, then, get a `StockPriceSubscriber` and add an event handler that writes to the response stream.</span></span> <span data-ttu-id="ccdd7-140">Attendez ensuite que la connexion soit fermée avant de supprimer immédiatement la `subscriber` pour l’empêcher d’essayer d’écrire des données dans le flux fermé.</span><span class="sxs-lookup"><span data-stu-id="ccdd7-140">Then wait for the connection to be closed before immediately disposing the `subscriber` to prevent it from trying to write data to the closed stream.</span></span>

<span data-ttu-id="ccdd7-141">La `WriteUpdateAsync` méthode a un `try` / `catch` bloc pour gérer les erreurs qui peuvent se produire lorsqu’un message est écrit dans le flux.</span><span class="sxs-lookup"><span data-stu-id="ccdd7-141">The `WriteUpdateAsync` method has a `try`/`catch` block to handle any errors that might happen when a message is written to the stream.</span></span> <span data-ttu-id="ccdd7-142">Cette considération est importante dans les connexions persistantes sur les réseaux, qui peuvent être interrompues à n’importe quelle milliseconde, que ce soit intentionnellement ou en raison d’une défaillance quelque part.</span><span class="sxs-lookup"><span data-stu-id="ccdd7-142">This consideration is important in persistent connections over networks, which could be broken at any millisecond, whether intentionally or because of a failure somewhere.</span></span>

### <a name="use-stocktickerservice-from-a-client-application"></a><span data-ttu-id="ccdd7-143">Utiliser StockTickerService à partir d’une application cliente</span><span class="sxs-lookup"><span data-stu-id="ccdd7-143">Use StockTickerService from a client application</span></span>

<span data-ttu-id="ccdd7-144">Suivez les mêmes étapes de la section précédente pour créer une bibliothèque de classes de client partageable à partir du `.proto` fichier.</span><span class="sxs-lookup"><span data-stu-id="ccdd7-144">Follow the same steps in the previous section to create a shareable client class library from the `.proto` file.</span></span> <span data-ttu-id="ccdd7-145">Dans l’exemple, il existe une application console .NET qui montre comment utiliser le client.</span><span class="sxs-lookup"><span data-stu-id="ccdd7-145">In the sample, there's a .NET console application that demonstrates how to use the client.</span></span>

#### <a name="example-programcs"></a><span data-ttu-id="ccdd7-146">Exemple avec Program.cs</span><span class="sxs-lookup"><span data-stu-id="ccdd7-146">Example Program.cs</span></span>

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

<span data-ttu-id="ccdd7-147">Dans ce cas, la `Subscribe` méthode sur le client généré n’est pas asynchrone.</span><span class="sxs-lookup"><span data-stu-id="ccdd7-147">In this case, the `Subscribe` method on the generated client isn't asynchronous.</span></span> <span data-ttu-id="ccdd7-148">Le flux est créé et utilisable immédiatement, car sa `MoveNext` méthode est asynchrone et la première fois qu’il est appelé, il ne se termine pas tant que la connexion n’est pas active.</span><span class="sxs-lookup"><span data-stu-id="ccdd7-148">The stream is created and usable right away because its `MoveNext` method is asynchronous and the first time it's called it won't complete until the connection is alive.</span></span>

<span data-ttu-id="ccdd7-149">Le flux est passé à une `DisplayAsync` méthode asynchrone.</span><span class="sxs-lookup"><span data-stu-id="ccdd7-149">The stream is passed to an asynchronous `DisplayAsync` method.</span></span> <span data-ttu-id="ccdd7-150">L’application attend ensuite que l’utilisateur appuie sur une touche, puis annule la `DisplayAsync` méthode et attend la fin de la tâche avant de quitter.</span><span class="sxs-lookup"><span data-stu-id="ccdd7-150">The application then waits for the user to press a key, and then cancels the `DisplayAsync` method and waits for the task to complete before exiting.</span></span>

> [!NOTE]
> <span data-ttu-id="ccdd7-151">Ce code utilise la nouvelle syntaxe de `using` déclaration C# 8 pour supprimer le flux et le canal quand la `Main` méthode se termine.</span><span class="sxs-lookup"><span data-stu-id="ccdd7-151">This code uses the new C# 8 `using` declaration syntax to dispose of the stream and the channel when the `Main` method exits.</span></span> <span data-ttu-id="ccdd7-152">C’est une petite modification, mais une bonne chose qui réduit les retraits et les lignes vides.</span><span class="sxs-lookup"><span data-stu-id="ccdd7-152">It's a small change, but a nice one that reduces indentations and empty lines.</span></span>

#### <a name="consume-the-stream"></a><span data-ttu-id="ccdd7-153">Utiliser le flux</span><span class="sxs-lookup"><span data-stu-id="ccdd7-153">Consume the stream</span></span>

<span data-ttu-id="ccdd7-154">WCF utilise des interfaces de rappel pour permettre au serveur d’appeler des méthodes directement sur le client.</span><span class="sxs-lookup"><span data-stu-id="ccdd7-154">WCF uses callback interfaces to allow the server to call methods directly on the client.</span></span> <span data-ttu-id="ccdd7-155">les flux gRPC fonctionnent différemment.</span><span class="sxs-lookup"><span data-stu-id="ccdd7-155">gRPC streams work differently.</span></span> <span data-ttu-id="ccdd7-156">Le client itère au sein du flux retourné et traite les messages, comme s’ils étaient retournés par une méthode locale retournant un `IEnumerable` .</span><span class="sxs-lookup"><span data-stu-id="ccdd7-156">The client iterates over the returned stream and processes messages, just as though they were returned from a local method returning an `IEnumerable`.</span></span>

<span data-ttu-id="ccdd7-157">Le `IAsyncStreamReader<T>` type fonctionne très bien comme un `IEnumerator<T>` .</span><span class="sxs-lookup"><span data-stu-id="ccdd7-157">The `IAsyncStreamReader<T>` type works much like an `IEnumerator<T>`.</span></span> <span data-ttu-id="ccdd7-158">Il existe une `MoveNext` méthode qui retourne la valeur true tant qu’il y a plus de données, et une `Current` propriété qui retourne la valeur la plus récente.</span><span class="sxs-lookup"><span data-stu-id="ccdd7-158">There's a `MoveNext` method that returns true as long as there's more data, and a `Current` property that returns the latest value.</span></span> <span data-ttu-id="ccdd7-159">La seule différence est que la `MoveNext` méthode retourne un `Task<bool>` au lieu d’un seul `bool` .</span><span class="sxs-lookup"><span data-stu-id="ccdd7-159">The only difference is that the `MoveNext` method returns a `Task<bool>` instead of just a `bool`.</span></span> <span data-ttu-id="ccdd7-160">La `ReadAllAsync` méthode d’extension encapsule le flux dans un standard C# 8 `IAsyncEnumerable` qui peut être utilisé avec la nouvelle `await foreach` syntaxe.</span><span class="sxs-lookup"><span data-stu-id="ccdd7-160">The `ReadAllAsync` extension method wraps the stream in a standard C# 8 `IAsyncEnumerable` that can be used with the new `await foreach` syntax.</span></span>

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
> <span data-ttu-id="ccdd7-161">Pour les développeurs qui utilisent des modèles de programmation réactifs, la section sur les [bibliothèques clientes](client-libraries.md#iobservable) à la fin de ce chapitre montre comment ajouter une méthode d’extension et des classes à inclure `IAsyncStreamReader<T>` dans un wrapper dans un `IObservable<T>` .</span><span class="sxs-lookup"><span data-stu-id="ccdd7-161">For developers using reactive programming patterns, the section on [client libraries](client-libraries.md#iobservable) at the end of this chapter shows how to add an extension method and classes to wrap `IAsyncStreamReader<T>` in an `IObservable<T>`.</span></span>

<span data-ttu-id="ccdd7-162">Là encore, veillez à intercepter les exceptions ici en raison de la possibilité d’une défaillance du réseau, et en raison de la <xref:System.OperationCanceledException> levée inévitable du fait que le code utilise un <xref:System.Threading.CancellationToken> pour rompre la boucle.</span><span class="sxs-lookup"><span data-stu-id="ccdd7-162">Again, be sure to catch exceptions here because of the possibility of network failure, and because of the <xref:System.OperationCanceledException> that will inevitably be thrown because the code is using a <xref:System.Threading.CancellationToken> to break the loop.</span></span> <span data-ttu-id="ccdd7-163">Le `RpcException` type contient de nombreuses informations utiles sur les erreurs d’exécution gRPC, y compris le `StatusCode` .</span><span class="sxs-lookup"><span data-stu-id="ccdd7-163">The `RpcException` type has a lot of useful information about gRPC runtime errors, including the `StatusCode`.</span></span> <span data-ttu-id="ccdd7-164">Pour plus d’informations, consultez [ *gestion des erreurs* dans le chapitre 4](error-handling.md).</span><span class="sxs-lookup"><span data-stu-id="ccdd7-164">For more information, see [*Error handling* in Chapter 4](error-handling.md).</span></span>

## <a name="bidirectional-streaming"></a><span data-ttu-id="ccdd7-165">Diffusion bidirectionnelle</span><span class="sxs-lookup"><span data-stu-id="ccdd7-165">Bidirectional streaming</span></span>

<span data-ttu-id="ccdd7-166">Un service WCF Full-duplex permet une messagerie asynchrone et en temps réel dans les deux sens.</span><span class="sxs-lookup"><span data-stu-id="ccdd7-166">A WCF full-duplex service allows for asynchronous, real-time messaging in both directions.</span></span> <span data-ttu-id="ccdd7-167">Dans l’exemple de diffusion en continu du serveur, le client démarre une demande, puis reçoit un flux de mises à jour.</span><span class="sxs-lookup"><span data-stu-id="ccdd7-167">In the server streaming example, the client starts a request and then receives a stream of updates.</span></span> <span data-ttu-id="ccdd7-168">Une meilleure version de ce service permettrait au client d’ajouter et de supprimer des actions de la liste sans avoir à arrêter et à créer un nouvel abonnement.</span><span class="sxs-lookup"><span data-stu-id="ccdd7-168">A better version of that service would allow the client to add and remove stocks from the list without having to stop and create a new subscription.</span></span> <span data-ttu-id="ccdd7-169">Cette fonctionnalité a été implémentée dans l' [exemple de solution FullStockTicker](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/wcf/FullStockTicker).</span><span class="sxs-lookup"><span data-stu-id="ccdd7-169">That functionality has been implemented in the [FullStockTicker sample solution](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/wcf/FullStockTicker).</span></span>

<span data-ttu-id="ccdd7-170">L' `IFullStockTickerService` interface fournit trois méthodes :</span><span class="sxs-lookup"><span data-stu-id="ccdd7-170">The `IFullStockTickerService` interface provides three methods:</span></span>

- <span data-ttu-id="ccdd7-171">`Subscribe` démarre la connexion.</span><span class="sxs-lookup"><span data-stu-id="ccdd7-171">`Subscribe` starts the connection.</span></span>
- <span data-ttu-id="ccdd7-172">`AddSymbol` Ajoute un symbole de cotations boursières à surveiller.</span><span class="sxs-lookup"><span data-stu-id="ccdd7-172">`AddSymbol` adds a stock symbol to watch.</span></span>
- <span data-ttu-id="ccdd7-173">`RemoveSymbol` supprime un symbole de la liste de suivi.</span><span class="sxs-lookup"><span data-stu-id="ccdd7-173">`RemoveSymbol` removes a symbol from the watched list.</span></span>

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

<span data-ttu-id="ccdd7-174">L’interface de rappel reste la même.</span><span class="sxs-lookup"><span data-stu-id="ccdd7-174">The callback interface remains the same.</span></span>

<span data-ttu-id="ccdd7-175">L’implémentation de ce modèle dans gRPC est moins simple, car il existe désormais deux flux de données avec des messages transmis : un du client au serveur et un autre du serveur au client.</span><span class="sxs-lookup"><span data-stu-id="ccdd7-175">Implementing this pattern in gRPC is less straightforward because there are now two streams of data with messages being passed: one from client to server and another from server to client.</span></span> <span data-ttu-id="ccdd7-176">Il n’est pas possible d’utiliser plusieurs méthodes pour implémenter les opérations d’ajout et de suppression, mais vous pouvez passer plusieurs types de messages sur un seul flux en utilisant le `Any` type ou le `oneof` mot clé, qui a été abordé dans le [chapitre 3](protobuf-any-oneof.md).</span><span class="sxs-lookup"><span data-stu-id="ccdd7-176">It isn't possible to use multiple methods to implement the add and remove operations, but you can pass more than one type of message on a single stream by using either the `Any` type or the `oneof` keyword, which were covered in [Chapter 3](protobuf-any-oneof.md).</span></span>

<span data-ttu-id="ccdd7-177">Dans le cas où il existe un ensemble spécifique de types acceptables, `oneof` la meilleure façon de le faire.</span><span class="sxs-lookup"><span data-stu-id="ccdd7-177">In a case where there's a specific set of types that are acceptable, `oneof` is a better way to go.</span></span> <span data-ttu-id="ccdd7-178">Utilisez un `ActionMessage` qui peut contenir un `AddSymbolRequest` ou un `RemoveSymbolRequest` :</span><span class="sxs-lookup"><span data-stu-id="ccdd7-178">Use an `ActionMessage` that can hold either an `AddSymbolRequest` or a `RemoveSymbolRequest`:</span></span>

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

<span data-ttu-id="ccdd7-179">Déclarer un service de streaming bidirectionnel qui prend un flux de `ActionMessage` messages :</span><span class="sxs-lookup"><span data-stu-id="ccdd7-179">Declare a bidirectional streaming service that takes a stream of `ActionMessage` messages:</span></span>

```protobuf
service FullStockTicker {
  rpc Subscribe (stream ActionMessage) returns (stream StockTickerUpdate);
}
```

<span data-ttu-id="ccdd7-180">L’implémentation de ce service est similaire à celle de l’exemple précédent, sauf que le premier paramètre de la `Subscribe` méthode est désormais un `IAsyncStreamReader<ActionMessage>` , qui peut être utilisé pour gérer `Add` les `Remove` requêtes et :</span><span class="sxs-lookup"><span data-stu-id="ccdd7-180">The implementation for this service is similar to that of the previous example, except the first parameter of the `Subscribe` method is now an `IAsyncStreamReader<ActionMessage>`, which can be used to handle the `Add` and `Remove` requests:</span></span>

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
        // Handle any errors caused by broken connection, etc.
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

<span data-ttu-id="ccdd7-181">La `ActionMessage` classe générée par gRPC garantit qu’une seule des `Add` `Remove` Propriétés et peut être définie.</span><span class="sxs-lookup"><span data-stu-id="ccdd7-181">The `ActionMessage` class that gRPC has generated guarantees that only one of the `Add` and `Remove` properties can be set.</span></span> <span data-ttu-id="ccdd7-182">La recherche d’une `null` méthode n’est pas valide pour déterminer le type de message utilisé, mais il existe un meilleur moyen de le faire.</span><span class="sxs-lookup"><span data-stu-id="ccdd7-182">Finding which one isn't `null` is a valid way to determine which type of message is used, but there's a better way.</span></span> <span data-ttu-id="ccdd7-183">La génération de code a également créé un `enum ActionOneOfCase` dans la `ActionMessage` classe, qui ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="ccdd7-183">The code generation also created an `enum ActionOneOfCase` in the `ActionMessage` class, which looks like this:</span></span>

```csharp
public enum ActionOneofCase {
    None = 0,
    Add = 1,
    Remove = 2,
}
```

<span data-ttu-id="ccdd7-184">La propriété `ActionCase` sur l' `ActionMessage` objet peut être utilisée avec une `switch` instruction pour déterminer quel champ est défini :</span><span class="sxs-lookup"><span data-stu-id="ccdd7-184">The property `ActionCase` on the `ActionMessage` object can be used with a `switch` statement to determine which field is set:</span></span>

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
> <span data-ttu-id="ccdd7-185">L' `switch` instruction a un `default` cas qui enregistre un avertissement si elle rencontre une `ActionOneOfCase` valeur inconnue.</span><span class="sxs-lookup"><span data-stu-id="ccdd7-185">The `switch` statement has a `default` case that logs a warning if it encounters an unknown `ActionOneOfCase` value.</span></span> <span data-ttu-id="ccdd7-186">Cela peut être utile pour indiquer qu’un client utilise une version plus récente du `.proto` fichier qui a ajouté d’autres actions.</span><span class="sxs-lookup"><span data-stu-id="ccdd7-186">This could be useful to indicate that a client is using a later version of the `.proto` file that has added more actions.</span></span> <span data-ttu-id="ccdd7-187">C’est l’une des raisons pour lesquelles l’utilisation d’un `switch` est mieux que le test de `null` sur des champs connus.</span><span class="sxs-lookup"><span data-stu-id="ccdd7-187">This is one reason why using a `switch` is better than testing for `null` on known fields.</span></span>

### <a name="use-fullstocktickerservice-from-a-client-application"></a><span data-ttu-id="ccdd7-188">Utiliser FullStockTickerService à partir d’une application cliente</span><span class="sxs-lookup"><span data-stu-id="ccdd7-188">Use FullStockTickerService from a client application</span></span>

<span data-ttu-id="ccdd7-189">Il existe une simple application WPF .NET qui illustre l’utilisation de ce client plus complexe.</span><span class="sxs-lookup"><span data-stu-id="ccdd7-189">There's a simple .NET WPF application that demonstrates the use of this more complex client.</span></span> <span data-ttu-id="ccdd7-190">Vous pouvez trouver l’application complète sur [GitHub](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTicker).</span><span class="sxs-lookup"><span data-stu-id="ccdd7-190">You can find the full application on [GitHub](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTicker).</span></span>

<span data-ttu-id="ccdd7-191">Le client est utilisé dans la `MainWindowViewModel` classe, qui obtient une instance du `FullStockTicker.FullStockTickerClient` type à partir de l’injection de dépendances :</span><span class="sxs-lookup"><span data-stu-id="ccdd7-191">The client is used in the `MainWindowViewModel` class, which gets an instance of the `FullStockTicker.FullStockTickerClient` type from dependency injection:</span></span>

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

<span data-ttu-id="ccdd7-192">L’objet retourné par la `client.Subscribe()` méthode est maintenant une instance du type de bibliothèque gRPC `AsyncDuplexStreamingCall<TRequest, TResponse>` , qui fournit un `RequestStream` pour l’envoi de demandes au serveur et un `ResponseStream` pour la gestion des réponses.</span><span class="sxs-lookup"><span data-stu-id="ccdd7-192">The object returned by the `client.Subscribe()` method is now an instance of the gRPC library type `AsyncDuplexStreamingCall<TRequest, TResponse>`, which provides a `RequestStream` for sending requests to the server and a `ResponseStream` for handling responses.</span></span>

<span data-ttu-id="ccdd7-193">Le flux de requête est utilisé à partir de certaines `ICommand` méthodes WPF pour ajouter et supprimer des symboles.</span><span class="sxs-lookup"><span data-stu-id="ccdd7-193">The request stream is used from some WPF `ICommand` methods to add and remove symbols.</span></span> <span data-ttu-id="ccdd7-194">Pour chaque opération, définissez le champ approprié sur un `ActionMessage` objet :</span><span class="sxs-lookup"><span data-stu-id="ccdd7-194">For each operation, set the relevant field on an `ActionMessage` object:</span></span>

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
> <span data-ttu-id="ccdd7-195">La définition de la `oneof` valeur d’un champ dans un message efface automatiquement tous les champs qui ont été définis précédemment.</span><span class="sxs-lookup"><span data-stu-id="ccdd7-195">Setting a `oneof` field's value on a message automatically clears any fields that have been set previously.</span></span>

<span data-ttu-id="ccdd7-196">Le flux de réponses est géré dans une `async` méthode.</span><span class="sxs-lookup"><span data-stu-id="ccdd7-196">The stream of responses is handled in an `async` method.</span></span> <span data-ttu-id="ccdd7-197">Le `Task` retour est conservé pour être supprimé lorsque la fenêtre est fermée :</span><span class="sxs-lookup"><span data-stu-id="ccdd7-197">The `Task` it returns is held to be disposed when the window is closed:</span></span>

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

### <a name="client-cleanup"></a><span data-ttu-id="ccdd7-198">Nettoyage du client</span><span class="sxs-lookup"><span data-stu-id="ccdd7-198">Client cleanup</span></span>

<span data-ttu-id="ccdd7-199">Lorsque la fenêtre est fermée et que le `MainWindowViewModel` est supprimé (à partir `Closed` de l’événement de `MainWindow` ), nous vous recommandons de supprimer correctement l' `AsyncDuplexStreamingCall` objet.</span><span class="sxs-lookup"><span data-stu-id="ccdd7-199">When the window is closed and the `MainWindowViewModel` is disposed (from the `Closed` event of `MainWindow`), we recommend that you properly dispose the `AsyncDuplexStreamingCall` object.</span></span> <span data-ttu-id="ccdd7-200">En particulier, la `CompleteAsync` méthode sur `RequestStream` doit être appelée pour fermer correctement le flux sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="ccdd7-200">In particular, the `CompleteAsync` method on the `RequestStream` should be called to gracefully close the stream on the server.</span></span> <span data-ttu-id="ccdd7-201">Cet exemple illustre la `DisposeAsync` méthode de l’exemple de modèle d’affichage :</span><span class="sxs-lookup"><span data-stu-id="ccdd7-201">This example shows the `DisposeAsync` method from the sample view-model:</span></span>

```csharp
public async ValueTask DisposeAsync()
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

<span data-ttu-id="ccdd7-202">La fermeture des flux de requête permet au serveur de supprimer ses propres ressources en temps opportun.</span><span class="sxs-lookup"><span data-stu-id="ccdd7-202">Closing request streams enables the server to dispose of its own resources in a timely way.</span></span> <span data-ttu-id="ccdd7-203">Cela améliore l’efficacité et l’évolutivité des services et empêche les exceptions.</span><span class="sxs-lookup"><span data-stu-id="ccdd7-203">This improves the efficiency and scalability of services and prevents exceptions.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="ccdd7-204">[Précédent](migrate-request-reply.md) 
> [Suivant](streaming-versus-repeated.md)</span><span class="sxs-lookup"><span data-stu-id="ccdd7-204">[Previous](migrate-request-reply.md)
[Next](streaming-versus-repeated.md)</span></span>
