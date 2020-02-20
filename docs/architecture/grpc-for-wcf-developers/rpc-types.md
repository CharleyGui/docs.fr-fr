---
title: Types de RPC-gRPC pour les développeurs WCF
description: Examen des types d’appel de procédure distante pris en charge par WCF et de leurs équivalents dans gRPC
ms.date: 09/02/2019
ms.openlocfilehash: 58f097bac61395e6810155e8ae9a6bbf2219ec5e
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503443"
---
# <a name="types-of-rpc"></a><span data-ttu-id="f7200-103">Types de RPC</span><span class="sxs-lookup"><span data-stu-id="f7200-103">Types of RPC</span></span>

<span data-ttu-id="f7200-104">En tant que développeur Windows Communication Foundation (WCF), vous êtes probablement employé pour traiter les types d’appel de procédure distante (RPC) suivants :</span><span class="sxs-lookup"><span data-stu-id="f7200-104">As a Windows Communication Foundation (WCF) developer, you're probably used to dealing with the following types of remote procedure call (RPC):</span></span>

- <span data-ttu-id="f7200-105">Demande/réponse</span><span class="sxs-lookup"><span data-stu-id="f7200-105">Request/reply</span></span>
- <span data-ttu-id="f7200-106">Duplex</span><span class="sxs-lookup"><span data-stu-id="f7200-106">Duplex:</span></span>
  - <span data-ttu-id="f7200-107">Duplex unidirectionnel avec session</span><span class="sxs-lookup"><span data-stu-id="f7200-107">One-way duplex with session</span></span>
  - <span data-ttu-id="f7200-108">Full duplex avec session</span><span class="sxs-lookup"><span data-stu-id="f7200-108">Full duplex with session</span></span>
- <span data-ttu-id="f7200-109">Unidirectionnel</span><span class="sxs-lookup"><span data-stu-id="f7200-109">One-way</span></span>

<span data-ttu-id="f7200-110">Il est possible de mapper ces types RPC assez naturellement à des concepts gRPC existants.</span><span class="sxs-lookup"><span data-stu-id="f7200-110">It's possible to map these RPC types fairly naturally to existing gRPC concepts.</span></span> <span data-ttu-id="f7200-111">Ce chapitre aborde chacun de ces domaines.</span><span class="sxs-lookup"><span data-stu-id="f7200-111">This chapter will look at each of these areas in turn.</span></span> <span data-ttu-id="f7200-112">Le [Chapitre 5](migrate-wcf-to-grpc.md) présente des exemples similaires de manière plus approfondie.</span><span class="sxs-lookup"><span data-stu-id="f7200-112">[Chapter 5](migrate-wcf-to-grpc.md) will explore similar examples in greater depth.</span></span>

| <span data-ttu-id="f7200-113">WCF</span><span class="sxs-lookup"><span data-stu-id="f7200-113">WCF</span></span> | <span data-ttu-id="f7200-114">gRPC</span><span class="sxs-lookup"><span data-stu-id="f7200-114">gRPC</span></span> |
| --- | ---- |
| <span data-ttu-id="f7200-115">Demande/réponse régulière</span><span class="sxs-lookup"><span data-stu-id="f7200-115">Regular request/reply</span></span> | <span data-ttu-id="f7200-116">Unaire</span><span class="sxs-lookup"><span data-stu-id="f7200-116">Unary</span></span> |
| <span data-ttu-id="f7200-117">Service duplex avec session utilisant une interface de rappel client</span><span class="sxs-lookup"><span data-stu-id="f7200-117">Duplex service with session using a client callback interface</span></span> | <span data-ttu-id="f7200-118">Streaming de serveur</span><span class="sxs-lookup"><span data-stu-id="f7200-118">Server streaming</span></span> |
| <span data-ttu-id="f7200-119">Service Full duplex avec session</span><span class="sxs-lookup"><span data-stu-id="f7200-119">Full duplex service with session</span></span> | <span data-ttu-id="f7200-120">Diffusion bidirectionnelle</span><span class="sxs-lookup"><span data-stu-id="f7200-120">Bidirectional streaming</span></span> |
| <span data-ttu-id="f7200-121">Opérations unidirectionnelles</span><span class="sxs-lookup"><span data-stu-id="f7200-121">One-way operations</span></span> | <span data-ttu-id="f7200-122">Diffusion en continu du client</span><span class="sxs-lookup"><span data-stu-id="f7200-122">Client streaming</span></span> |

## <a name="requestreply"></a><span data-ttu-id="f7200-123">Demande/réponse</span><span class="sxs-lookup"><span data-stu-id="f7200-123">Request/reply</span></span>

<span data-ttu-id="f7200-124">Pour les méthodes de requête/réponse simples qui acceptent et retournent de petites quantités de données, utilisez le modèle gRPC le plus simple, le RPC unaire.</span><span class="sxs-lookup"><span data-stu-id="f7200-124">For simple request/reply methods that take and return small amounts of data, use the simplest gRPC pattern, the unary RPC.</span></span>

```protobuf
service Things {
    rpc Get(GetThingRequest) returns (GetThingResponse);
}
```

```csharp
public class ThingService : Things.ThingsBase
{
    public override async Task<GetThingResponse> Get(GetThingRequest request, ServerCallContext context)
    {
        // Get thing from database
        return new GetThingResponse { Thing = thing };
    }
}
```

```csharp
public async Task ShowThing(int thingId)
{
    var thing = await _thingsClient.GetAsync(new GetThingRequest { ThingId = thingId });
    Console.WriteLine($"{thing.Name}");
}
```

<span data-ttu-id="f7200-125">Comme vous pouvez le voir, l’implémentation d’une méthode de service RPC unaire gRPC est semblable à l’implémentation d’une opération WCF.</span><span class="sxs-lookup"><span data-stu-id="f7200-125">As you can see, implementing a gRPC unary RPC service method is similar to implementing a WCF operation.</span></span> <span data-ttu-id="f7200-126">La différence réside dans le fait qu’avec gRPC, vous substituez une méthode de classe de base au lieu d’implémenter une interface.</span><span class="sxs-lookup"><span data-stu-id="f7200-126">The difference is that with gRPC, you override a base class method instead of implementing an interface.</span></span> <span data-ttu-id="f7200-127">Sur le serveur, les méthodes de base gRPC retournent toujours <xref:System.Threading.Tasks.Task%601>, bien que le client fournisse des méthodes Async et Blocking pour appeler le service.</span><span class="sxs-lookup"><span data-stu-id="f7200-127">On the server, gRPC base methods always return <xref:System.Threading.Tasks.Task%601>, although the client provides both async and blocking methods to call the service.</span></span>

## <a name="wcf-duplex-one-way-to-client"></a><span data-ttu-id="f7200-128">Duplex WCF, une solution pour le client</span><span class="sxs-lookup"><span data-stu-id="f7200-128">WCF duplex, one way to client</span></span>

<span data-ttu-id="f7200-129">Les applications WCF (avec certaines liaisons) peuvent créer une connexion permanente entre le client et le serveur.</span><span class="sxs-lookup"><span data-stu-id="f7200-129">WCF applications (with certain bindings) can create a persistent connection between client and server.</span></span> <span data-ttu-id="f7200-130">Le serveur peut envoyer de manière asynchrone des données au client jusqu’à ce que la connexion soit fermée, à l’aide d’une *interface de rappel* spécifiée dans la propriété <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f7200-130">The server can asynchronously send data to the client until the connection is closed, by using a *callback interface* specified in the <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> property.</span></span>

<span data-ttu-id="f7200-131">les services gRPC offrent des fonctionnalités similaires à celles des flux de messages.</span><span class="sxs-lookup"><span data-stu-id="f7200-131">gRPC services provide similar functionality with message streams.</span></span> <span data-ttu-id="f7200-132">Les flux ne sont pas mappés *exactement* aux services duplex WCF en termes d’implémentation, mais vous pouvez obtenir les mêmes résultats.</span><span class="sxs-lookup"><span data-stu-id="f7200-132">Streams don't map *exactly* to WCF duplex services in terms of implementation, but you can achieve the same results.</span></span>

### <a name="grpc-streaming"></a><span data-ttu-id="f7200-133">diffusion en continu gRPC</span><span class="sxs-lookup"><span data-stu-id="f7200-133">gRPC streaming</span></span>

<span data-ttu-id="f7200-134">gRPC prend en charge la création de flux persistants entre le client et le serveur, et du serveur au client.</span><span class="sxs-lookup"><span data-stu-id="f7200-134">gRPC supports the creation of persistent streams from client to server, and from server to client.</span></span> <span data-ttu-id="f7200-135">Les deux types de flux peuvent être actifs simultanément.</span><span class="sxs-lookup"><span data-stu-id="f7200-135">Both types of stream can be active concurrently.</span></span> <span data-ttu-id="f7200-136">Cette capacité est appelée diffusion bidirectionnelle.</span><span class="sxs-lookup"><span data-stu-id="f7200-136">This ability is called bidirectional streaming.</span></span> 

<span data-ttu-id="f7200-137">Vous pouvez utiliser des flux pour la messagerie asynchrone arbitraire dans le temps.</span><span class="sxs-lookup"><span data-stu-id="f7200-137">You can use streams for arbitrary, asynchronous messaging over time.</span></span> <span data-ttu-id="f7200-138">Vous pouvez également les utiliser pour transmettre des jeux de données volumineux qui sont trop volumineux pour être générés et envoyés dans une requête ou une réponse unique.</span><span class="sxs-lookup"><span data-stu-id="f7200-138">Or you can use them for passing large datasets that are too big to generate and send in a single request or response.</span></span>

<span data-ttu-id="f7200-139">L’exemple suivant montre un RPC de streaming de serveur.</span><span class="sxs-lookup"><span data-stu-id="f7200-139">The following example shows a server-streaming RPC.</span></span>

```protobuf
service ClockStreamer {
    rpc Subscribe(ClockSubscribeRequest) returns (stream ClockMessage);
}
```

```csharp
public class ClockStreamerService : ClockStreamer.ClockStreamerBase
{
    public override async Task Subscribe(ClockSubscribeRequest request,
        IServerStreamWriter<ClockMessage> responseStream,
        ServerCallContext context)
    {
        while (!context.CancellationToken.IsCancellationRequested)
        {
            var time = DateTimeOffset.UtcNow;
            await responseStream.WriteAsync(new ClockMessage { message = $"The time is {time:t}." });
            await Task.Delay(TimeSpan.FromSeconds(10), context.CancellationToken);
        }
    }
}
```

<span data-ttu-id="f7200-140">Ce flux de serveur peut être consommé à partir d’une application cliente, comme illustré dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="f7200-140">This server stream can be consumed from a client application, as shown in the following code:</span></span>

```csharp
public async Task TellTheTimeAsync(CancellationToken token)
{
    var channel = GrpcChannel.ForAddress("https://localhost:5001");
    var client = new ClockStreamer.ClockStreamerClient(channel);

    var request = new ClockSubscribeRequest();
    var response = client.Subscribe(request);

    await foreach (var update in response.ResponseStream.ReadAllAsync(token))
    {
        Console.WriteLine(update.Message);
    }
}
```

> [!NOTE]
> <span data-ttu-id="f7200-141">Les RPC de streaming de serveur sont utiles pour les services de type abonnement.</span><span class="sxs-lookup"><span data-stu-id="f7200-141">Server-streaming RPCs are useful for subscription-style services.</span></span> <span data-ttu-id="f7200-142">Elles sont également utiles pour l’envoi de jeux de données volumineux lorsqu’il est inefficace ou impossible de générer l’ensemble du jeu de données en mémoire.</span><span class="sxs-lookup"><span data-stu-id="f7200-142">They're also useful for sending large datasets when it would be inefficient or impossible to build the entire dataset in memory.</span></span> <span data-ttu-id="f7200-143">Toutefois, les réponses de diffusion en continu ne sont pas aussi rapides que l’envoi de `repeated` champs dans un seul message.</span><span class="sxs-lookup"><span data-stu-id="f7200-143">However, streaming responses isn't as fast as sending `repeated` fields in a single message.</span></span> <span data-ttu-id="f7200-144">En règle générale, la diffusion en continu ne doit pas être utilisée pour les petits jeux de données.</span><span class="sxs-lookup"><span data-stu-id="f7200-144">As a rule, streaming shouldn't be used for small datasets.</span></span>

### <a name="differences-from-wcf"></a><span data-ttu-id="f7200-145">Différences par rapport à WCF</span><span class="sxs-lookup"><span data-stu-id="f7200-145">Differences from WCF</span></span>

<span data-ttu-id="f7200-146">Un service duplex WCF utilise une interface de rappel client qui peut avoir plusieurs méthodes.</span><span class="sxs-lookup"><span data-stu-id="f7200-146">A WCF duplex service uses a client callback interface that can have multiple methods.</span></span> <span data-ttu-id="f7200-147">Un service de diffusion en continu gRPC Server peut uniquement envoyer des messages sur un seul flux.</span><span class="sxs-lookup"><span data-stu-id="f7200-147">A gRPC server-streaming service can only send messages over a single stream.</span></span> <span data-ttu-id="f7200-148">Si vous avez besoin de plusieurs méthodes, utilisez un type de message avec un [champ any ou](protobuf-any-oneof.md) un champ pour envoyer des messages différents et écrire du code sur le client pour les gérer.</span><span class="sxs-lookup"><span data-stu-id="f7200-148">If you need multiple methods, use a message type with either [an Any field or a oneof field](protobuf-any-oneof.md) to send different messages, and write code in the client to handle them.</span></span>

<span data-ttu-id="f7200-149">Dans WCF, la classe [ServiceContract](xref:System.ServiceModel.ServiceContractAttribute) avec la session reste active jusqu’à ce que la connexion soit fermée.</span><span class="sxs-lookup"><span data-stu-id="f7200-149">In WCF, the [ServiceContract](xref:System.ServiceModel.ServiceContractAttribute) class with the session is kept alive until the connection is closed.</span></span> <span data-ttu-id="f7200-150">Plusieurs méthodes peuvent être appelées dans la session.</span><span class="sxs-lookup"><span data-stu-id="f7200-150">Multiple methods can be called within the session.</span></span> <span data-ttu-id="f7200-151">Dans gRPC, la `Task` que la méthode d’implémentation retourne ne doit pas se terminer tant que la connexion n’est pas fermée.</span><span class="sxs-lookup"><span data-stu-id="f7200-151">In gRPC, the `Task` that the implementation method returns shouldn't finish until the connection is closed.</span></span>

## <a name="wcf-one-way-operations-and-grpc-client-streaming"></a><span data-ttu-id="f7200-152">Opérations unidirectionnelles WCF et diffusion en continu du client gRPC</span><span class="sxs-lookup"><span data-stu-id="f7200-152">WCF one-way operations and gRPC client streaming</span></span>

<span data-ttu-id="f7200-153">WCF fournit des opérations unidirectionnelles (marquées avec `[OperationContract(IsOneWay = true)]`) qui retournent un accusé de réception spécifique au transport.</span><span class="sxs-lookup"><span data-stu-id="f7200-153">WCF provides one-way operations (marked with `[OperationContract(IsOneWay = true)]`) that return a transport-specific acknowledgement.</span></span> <span data-ttu-id="f7200-154">les méthodes de service gRPC retournent toujours une réponse, même si elle est vide.</span><span class="sxs-lookup"><span data-stu-id="f7200-154">gRPC service methods always return a response, even if it's empty.</span></span> <span data-ttu-id="f7200-155">Le client doit toujours attendre cette réponse.</span><span class="sxs-lookup"><span data-stu-id="f7200-155">The client should always await that response.</span></span> <span data-ttu-id="f7200-156">Pour le style de messagerie « Fire-and-oublier » dans gRPC, vous pouvez créer un service de diffusion en continu client.</span><span class="sxs-lookup"><span data-stu-id="f7200-156">For the "fire-and-forget" style of messaging in gRPC, you can create a client streaming service.</span></span>

### <a name="thing_logproto"></a><span data-ttu-id="f7200-157">thing_log. proto</span><span class="sxs-lookup"><span data-stu-id="f7200-157">thing_log.proto</span></span>

```protobuf
service ThingLog {
  rpc OpenConnection(stream Thing) returns (ConnectionClosedResponse);
}
```

### <a name="thinglogservicecs"></a><span data-ttu-id="f7200-158">ThingLogService.cs</span><span class="sxs-lookup"><span data-stu-id="f7200-158">ThingLogService.cs</span></span>

```csharp
public class ThingLogService : Protos.ThingLog.ThingLogBase
{
    private static readonly ConnectionClosedResponse EmptyResponse = new ConnectionClosedResponse();
    private readonly ILogger<ThingLogService> _logger;
    public ThingLogService(ILogger<ThingLogService> logger)
    {
        _logger = logger;
    }

    public override async Task<CompletedResponse> OpenConnection(IAsyncStreamReader<Thing> requestStream, ServerCallContext context)
    {
        while (await requestStream.MoveNext(context.CancellationToken))
        {
            _logger.LogInformation(requestStream.Current.Description);
        }
        return EmptyResponse;
    }
}
```

### <a name="thinglog-client-example"></a><span data-ttu-id="f7200-159">Exemple de client ThingLog</span><span class="sxs-lookup"><span data-stu-id="f7200-159">ThingLog client example</span></span>

```csharp
public class ThingLogger : IAsyncDisposable
{
    private readonly ThingLog.ThingLogClient _client;
    private readonly AsyncClientStreamingCall<ThingLogRequest, CompletedResponse> _stream;

    public ThingLogger(ThingLog.ThingLogClient client)
    {
        _client = client;
        _stream = client.OpenConnection();
    }

    public async Task WriteAsync(string description)
    {
        await _stream.RequestStream.WriteAsync(new Thing
        {
            Description = description,
            Time = Timestamp.FromDateTimeOffset(DateTimeOffset.UtcNow)
        });
    }

    public async ValueTask DisposeAsync()
    {
        await _stream.RequestStream.CompleteAsync();
        _stream.Dispose();
    }
}
```

<span data-ttu-id="f7200-160">Vous pouvez utiliser les RPC de streaming client pour la messagerie de déclenchement et d’oubli, comme illustré dans l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="f7200-160">You can use client-streaming RPCs for fire-and-forget messaging, as shown in the previous example.</span></span> <span data-ttu-id="f7200-161">Vous pouvez également les utiliser pour envoyer des jeux de données très volumineux au serveur.</span><span class="sxs-lookup"><span data-stu-id="f7200-161">You can also use them for sending very large datasets to the server.</span></span> <span data-ttu-id="f7200-162">Le même avertissement sur les performances s’applique : pour les jeux de données plus petits, utilisez `repeated` champs dans des messages ordinaires.</span><span class="sxs-lookup"><span data-stu-id="f7200-162">The same warning about performance applies: for smaller datasets, use `repeated` fields in regular messages.</span></span>

## <a name="wcf-full-duplex-services"></a><span data-ttu-id="f7200-163">Services en duplex intégral WCF</span><span class="sxs-lookup"><span data-stu-id="f7200-163">WCF full-duplex services</span></span>

<span data-ttu-id="f7200-164">La liaison duplex WCF prend en charge plusieurs opérations unidirectionnelles sur l’interface de service et l’interface de rappel du client.</span><span class="sxs-lookup"><span data-stu-id="f7200-164">WCF duplex binding supports multiple one-way operations on both the service interface and the client callback interface.</span></span> <span data-ttu-id="f7200-165">Cette prise en charge autorise les conversations en cours entre le client et le serveur.</span><span class="sxs-lookup"><span data-stu-id="f7200-165">This support allows ongoing conversations between client and server.</span></span> <span data-ttu-id="f7200-166">gRPC prend en charge des appels de manière similaire avec les RPC de diffusion bidirectionnelle, où les deux paramètres sont marqués avec le modificateur `stream`.</span><span class="sxs-lookup"><span data-stu-id="f7200-166">gRPC supports something similar with bidirectional streaming RPCs, where both parameters are marked with the `stream` modifier.</span></span>

### <a name="chatproto"></a><span data-ttu-id="f7200-167">conversation. proto</span><span class="sxs-lookup"><span data-stu-id="f7200-167">chat.proto</span></span>

```protobuf
service Chatter {
    rpc Connect(stream IncomingMessage) returns (stream OutgoingMessage);
}
```

### <a name="chatterservicecs"></a><span data-ttu-id="f7200-168">ChatterService.cs</span><span class="sxs-lookup"><span data-stu-id="f7200-168">ChatterService.cs</span></span>

```csharp
public class ChatterService : Chatter.ChatterBase
{
    private readonly IChatHub _hub;

    public ChatterService(IChatHub hub)
    {
        _hub = hub;
    }

    public override async Task Connect(IAsyncStreamReader<MessageRequest> requestStream, IServerStreamWriter<MessageResponse> responseStream, ServerCallContext context)
    {
        _hub.MessageReceived += async (sender, args) =>
            await responseStream.WriteAsync(new MessageResponse {Text = args.Message});

        while (await requestStream.MoveNext(context.CancellationToken))
        {
            await _hub.SendAsync(requestStream.Current.Text);
        }
    }
}
```

<span data-ttu-id="f7200-169">Dans l’exemple précédent, vous pouvez voir que la méthode d’implémentation reçoit à la fois un flux de demande (`IAsyncStreamReader<MessageRequest>`) et un flux de réponse (`IServerStreamWriter<MessageResponse>`).</span><span class="sxs-lookup"><span data-stu-id="f7200-169">In the previous example, you can see that the implementation method receives both a request stream (`IAsyncStreamReader<MessageRequest>`) and a response stream (`IServerStreamWriter<MessageResponse>`).</span></span> <span data-ttu-id="f7200-170">La méthode peut lire et écrire des messages jusqu’à ce que la connexion soit fermée.</span><span class="sxs-lookup"><span data-stu-id="f7200-170">The method can read and write messages until the connection is closed.</span></span>

### <a name="chatter-client"></a><span data-ttu-id="f7200-171">Client chatter</span><span class="sxs-lookup"><span data-stu-id="f7200-171">Chatter client</span></span>

```csharp
public class Chat : IAsyncDisposable
{
    private readonly Chatter.ChatterClient _client;
    private readonly AsyncDuplexStreamingCall<MessageRequest, MessageResponse> _stream;
    private readonly CancellationTokenSource _cancellationTokenSource;
    private readonly Task _readTask;

    public Chat(Chatter.ChatterClient client)
    {
        _client = client;
        _stream = _client.Connect();
        _cancellationTokenSource = new CancellationTokenSource();
        _readTask = ReadAsync(_cancellationTokenSource.Token);
    }

    public async Task SendAsync(string message)
    {
        await _stream.RequestStream.WriteAsync(new MessageRequest {Text = message});
    }

    private async Task ReadAsync(CancellationToken token)
    {
        while (await _stream.ResponseStream.MoveNext(token))
        {
            Console.WriteLine(_stream.ResponseStream.Current.Text);
        }
    }

    public async ValueTask DisposeAsync()
    {
        await _stream.RequestStream.CompleteAsync();
        await _readTask;
        _stream.Dispose();
    }
}
```

>[!div class="step-by-step"]
><span data-ttu-id="f7200-172">[Précédent](wcf-bindings.md)
>[Suivant](metadata.md)</span><span class="sxs-lookup"><span data-stu-id="f7200-172">[Previous](wcf-bindings.md)
[Next](metadata.md)</span></span>
