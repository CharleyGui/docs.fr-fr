---
title: Types de RPC - gRPC pour les développeurs WCF
description: Examen des types d’appels de procédure à distance soutenus par WCF et leurs équivalents dans gRPC
ms.date: 09/02/2019
ms.openlocfilehash: b9d4ce7cae693ed7904229483cbccfe3b299b640
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79401682"
---
# <a name="types-of-rpc"></a><span data-ttu-id="c3d36-103">Types de RPC</span><span class="sxs-lookup"><span data-stu-id="c3d36-103">Types of RPC</span></span>

<span data-ttu-id="c3d36-104">En tant que développeur de la Windows Communication Foundation (WCF), vous êtes probablement habitué à traiter les types suivants d’appel de procédure à distance (RPC) :</span><span class="sxs-lookup"><span data-stu-id="c3d36-104">As a Windows Communication Foundation (WCF) developer, you're probably used to dealing with the following types of remote procedure call (RPC):</span></span>

- <span data-ttu-id="c3d36-105">Demande/réponse</span><span class="sxs-lookup"><span data-stu-id="c3d36-105">Request/reply</span></span>
- <span data-ttu-id="c3d36-106">Duplex:</span><span class="sxs-lookup"><span data-stu-id="c3d36-106">Duplex:</span></span>
  - <span data-ttu-id="c3d36-107">Duplex à sens unique avec session</span><span class="sxs-lookup"><span data-stu-id="c3d36-107">One-way duplex with session</span></span>
  - <span data-ttu-id="c3d36-108">Duplex complet avec session</span><span class="sxs-lookup"><span data-stu-id="c3d36-108">Full duplex with session</span></span>
- <span data-ttu-id="c3d36-109">Unidirectionnel</span><span class="sxs-lookup"><span data-stu-id="c3d36-109">One-way</span></span>

<span data-ttu-id="c3d36-110">Il est possible de cartographier ces types RPC assez naturellement aux concepts gRPC existants.</span><span class="sxs-lookup"><span data-stu-id="c3d36-110">It's possible to map these RPC types fairly naturally to existing gRPC concepts.</span></span> <span data-ttu-id="c3d36-111">Ce chapitre examinera chacun de ces domaines à tour de rôle.</span><span class="sxs-lookup"><span data-stu-id="c3d36-111">This chapter will look at each of these areas in turn.</span></span> <span data-ttu-id="c3d36-112">[Le chapitre 5](migrate-wcf-to-grpc.md) explorera plus en profondeur des exemples similaires.</span><span class="sxs-lookup"><span data-stu-id="c3d36-112">[Chapter 5](migrate-wcf-to-grpc.md) will explore similar examples in greater depth.</span></span>

| <span data-ttu-id="c3d36-113">WCF</span><span class="sxs-lookup"><span data-stu-id="c3d36-113">WCF</span></span> | <span data-ttu-id="c3d36-114">gRPC (en)</span><span class="sxs-lookup"><span data-stu-id="c3d36-114">gRPC</span></span> |
| --- | ---- |
| <span data-ttu-id="c3d36-115">Demande/réponse régulière</span><span class="sxs-lookup"><span data-stu-id="c3d36-115">Regular request/reply</span></span> | <span data-ttu-id="c3d36-116">Unaire</span><span class="sxs-lookup"><span data-stu-id="c3d36-116">Unary</span></span> |
| <span data-ttu-id="c3d36-117">Service Duplex avec session à l’aide d’une interface de rappel client</span><span class="sxs-lookup"><span data-stu-id="c3d36-117">Duplex service with session using a client callback interface</span></span> | <span data-ttu-id="c3d36-118">Streaming serveur</span><span class="sxs-lookup"><span data-stu-id="c3d36-118">Server streaming</span></span> |
| <span data-ttu-id="c3d36-119">Service en duplex complet avec session</span><span class="sxs-lookup"><span data-stu-id="c3d36-119">Full duplex service with session</span></span> | <span data-ttu-id="c3d36-120">Streaming bidirectionnel</span><span class="sxs-lookup"><span data-stu-id="c3d36-120">Bidirectional streaming</span></span> |
| <span data-ttu-id="c3d36-121">Opérations à sens unique</span><span class="sxs-lookup"><span data-stu-id="c3d36-121">One-way operations</span></span> | <span data-ttu-id="c3d36-122">Streaming client</span><span class="sxs-lookup"><span data-stu-id="c3d36-122">Client streaming</span></span> |

## <a name="requestreply"></a><span data-ttu-id="c3d36-123">Demande/réponse</span><span class="sxs-lookup"><span data-stu-id="c3d36-123">Request/reply</span></span>

<span data-ttu-id="c3d36-124">Pour les méthodes simples de demande/réponse qui prennent et retournent de petites quantités de données, utilisez le modèle gRPC le plus simple, le RPC unary.</span><span class="sxs-lookup"><span data-stu-id="c3d36-124">For simple request/reply methods that take and return small amounts of data, use the simplest gRPC pattern, the unary RPC.</span></span>

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

<span data-ttu-id="c3d36-125">Comme vous pouvez le voir, la mise en œuvre d’une méthode de service RPC nonaire gRPC est similaire à la mise en œuvre d’une opération WCF.</span><span class="sxs-lookup"><span data-stu-id="c3d36-125">As you can see, implementing a gRPC unary RPC service method is similar to implementing a WCF operation.</span></span> <span data-ttu-id="c3d36-126">La différence est qu’avec gRPC, vous remplacez une méthode de classe de base au lieu de mettre en œuvre une interface.</span><span class="sxs-lookup"><span data-stu-id="c3d36-126">The difference is that with gRPC, you override a base class method instead of implementing an interface.</span></span> <span data-ttu-id="c3d36-127">Sur le serveur, les méthodes <xref:System.Threading.Tasks.Task%601>de base gRPC reviennent toujours, bien que le client fournisse à la fois des async et des méthodes de blocage pour appeler le service.</span><span class="sxs-lookup"><span data-stu-id="c3d36-127">On the server, gRPC base methods always return <xref:System.Threading.Tasks.Task%601>, although the client provides both async and blocking methods to call the service.</span></span>

## <a name="wcf-duplex-one-way-to-client"></a><span data-ttu-id="c3d36-128">Duplex WCF, une façon de client</span><span class="sxs-lookup"><span data-stu-id="c3d36-128">WCF duplex, one way to client</span></span>

<span data-ttu-id="c3d36-129">Les applications WCF (avec certaines liaisons) peuvent créer une connexion persistante entre le client et le serveur.</span><span class="sxs-lookup"><span data-stu-id="c3d36-129">WCF applications (with certain bindings) can create a persistent connection between client and server.</span></span> <span data-ttu-id="c3d36-130">Le serveur peut envoyer asynchronement des données au client jusqu’à ce <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> que la connexion soit fermée, en utilisant une interface de *rappel* spécifiée dans la propriété.</span><span class="sxs-lookup"><span data-stu-id="c3d36-130">The server can asynchronously send data to the client until the connection is closed, by using a *callback interface* specified in the <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> property.</span></span>

<span data-ttu-id="c3d36-131">les services gRPC offrent des fonctionnalités similaires avec des flux de messages.</span><span class="sxs-lookup"><span data-stu-id="c3d36-131">gRPC services provide similar functionality with message streams.</span></span> <span data-ttu-id="c3d36-132">Les flux ne sont pas *exactement* cartographiés pour les services duplex WCF en termes de mise en œuvre, mais vous pouvez obtenir les mêmes résultats.</span><span class="sxs-lookup"><span data-stu-id="c3d36-132">Streams don't map *exactly* to WCF duplex services in terms of implementation, but you can achieve the same results.</span></span>

### <a name="grpc-streaming"></a><span data-ttu-id="c3d36-133">gRPC streaming</span><span class="sxs-lookup"><span data-stu-id="c3d36-133">gRPC streaming</span></span>

<span data-ttu-id="c3d36-134">gRPC prend en charge la création de flux persistants d’un client à l’autre, et d’un serveur à l’autre.</span><span class="sxs-lookup"><span data-stu-id="c3d36-134">gRPC supports the creation of persistent streams from client to server, and from server to client.</span></span> <span data-ttu-id="c3d36-135">Les deux types de flux peuvent être actifs en même temps.</span><span class="sxs-lookup"><span data-stu-id="c3d36-135">Both types of stream can be active concurrently.</span></span> <span data-ttu-id="c3d36-136">Cette capacité est appelée streaming bidirectionnel.</span><span class="sxs-lookup"><span data-stu-id="c3d36-136">This ability is called bidirectional streaming.</span></span>

<span data-ttu-id="c3d36-137">Vous pouvez utiliser des flux pour des messages arbitraires et asynchrones au fil du temps.</span><span class="sxs-lookup"><span data-stu-id="c3d36-137">You can use streams for arbitrary, asynchronous messaging over time.</span></span> <span data-ttu-id="c3d36-138">Ou vous pouvez les utiliser pour passer de grands ensembles de données qui sont trop grands pour générer et envoyer une seule demande ou réponse.</span><span class="sxs-lookup"><span data-stu-id="c3d36-138">Or you can use them for passing large datasets that are too big to generate and send in a single request or response.</span></span>

<span data-ttu-id="c3d36-139">L’exemple suivant montre un RPC de streaming de serveur.</span><span class="sxs-lookup"><span data-stu-id="c3d36-139">The following example shows a server-streaming RPC.</span></span>

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

<span data-ttu-id="c3d36-140">Ce flux serveur peut être consommé à partir d’une application client, comme indiqué dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="c3d36-140">This server stream can be consumed from a client application, as shown in the following code:</span></span>

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
> <span data-ttu-id="c3d36-141">Les RPC en streaming de serveurs sont utiles pour les services de type abonnement.</span><span class="sxs-lookup"><span data-stu-id="c3d36-141">Server-streaming RPCs are useful for subscription-style services.</span></span> <span data-ttu-id="c3d36-142">Ils sont également utiles pour l’envoi de grands ensembles de données quand il serait inefficace ou impossible de construire l’ensemble des données en mémoire.</span><span class="sxs-lookup"><span data-stu-id="c3d36-142">They're also useful for sending large datasets when it would be inefficient or impossible to build the entire dataset in memory.</span></span> <span data-ttu-id="c3d36-143">Cependant, les réponses en streaming n’est pas aussi rapide que l’envoi de `repeated` champs dans un seul message.</span><span class="sxs-lookup"><span data-stu-id="c3d36-143">However, streaming responses isn't as fast as sending `repeated` fields in a single message.</span></span> <span data-ttu-id="c3d36-144">En règle générale, le streaming ne devrait pas être utilisé pour de petits jeux de données.</span><span class="sxs-lookup"><span data-stu-id="c3d36-144">As a rule, streaming shouldn't be used for small datasets.</span></span>

### <a name="differences-from-wcf"></a><span data-ttu-id="c3d36-145">Différences par rapport à WCF</span><span class="sxs-lookup"><span data-stu-id="c3d36-145">Differences from WCF</span></span>

<span data-ttu-id="c3d36-146">Un service en duplex WCF utilise une interface de rappel client qui peut avoir plusieurs méthodes.</span><span class="sxs-lookup"><span data-stu-id="c3d36-146">A WCF duplex service uses a client callback interface that can have multiple methods.</span></span> <span data-ttu-id="c3d36-147">Un service de streaming de serveurs gRPC ne peut envoyer des messages que sur un seul flux.</span><span class="sxs-lookup"><span data-stu-id="c3d36-147">A gRPC server-streaming service can only send messages over a single stream.</span></span> <span data-ttu-id="c3d36-148">Si vous avez besoin de plusieurs méthodes, utilisez un type de message avec [un champ ou un champ quelconque](protobuf-any-oneof.md) pour envoyer différents messages, et écrivez du code dans le client pour les manipuler.</span><span class="sxs-lookup"><span data-stu-id="c3d36-148">If you need multiple methods, use a message type with either [an Any field or a oneof field](protobuf-any-oneof.md) to send different messages, and write code in the client to handle them.</span></span>

<span data-ttu-id="c3d36-149">Dans WCF, la classe [ServiceContract](xref:System.ServiceModel.ServiceContractAttribute) avec la session est maintenue en vie jusqu’à ce que la connexion soit fermée.</span><span class="sxs-lookup"><span data-stu-id="c3d36-149">In WCF, the [ServiceContract](xref:System.ServiceModel.ServiceContractAttribute) class with the session is kept alive until the connection is closed.</span></span> <span data-ttu-id="c3d36-150">Plusieurs méthodes peuvent être appelées au cours de la session.</span><span class="sxs-lookup"><span data-stu-id="c3d36-150">Multiple methods can be called within the session.</span></span> <span data-ttu-id="c3d36-151">Dans gRPC, `Task` le rendement de la méthode de mise en œuvre ne doit pas se terminer jusqu’à ce que la connexion soit fermée.</span><span class="sxs-lookup"><span data-stu-id="c3d36-151">In gRPC, the `Task` that the implementation method returns shouldn't finish until the connection is closed.</span></span>

## <a name="wcf-one-way-operations-and-grpc-client-streaming"></a><span data-ttu-id="c3d36-152">Opérations à sens unique WCF et flux de clients gRPC</span><span class="sxs-lookup"><span data-stu-id="c3d36-152">WCF one-way operations and gRPC client streaming</span></span>

<span data-ttu-id="c3d36-153">WCF fournit des opérations à `[OperationContract(IsOneWay = true)]`sens unique (marquées par ) qui renvoient une reconnaissance spécifique au transport.</span><span class="sxs-lookup"><span data-stu-id="c3d36-153">WCF provides one-way operations (marked with `[OperationContract(IsOneWay = true)]`) that return a transport-specific acknowledgement.</span></span> <span data-ttu-id="c3d36-154">les méthodes de service gRPC retournent toujours une réponse, même si elle est vide.</span><span class="sxs-lookup"><span data-stu-id="c3d36-154">gRPC service methods always return a response, even if it's empty.</span></span> <span data-ttu-id="c3d36-155">Le client doit toujours attendre cette réponse.</span><span class="sxs-lookup"><span data-stu-id="c3d36-155">The client should always await that response.</span></span> <span data-ttu-id="c3d36-156">Pour le style de messagerie « fire-and-forget » dans gRPC, vous pouvez créer un service de streaming client.</span><span class="sxs-lookup"><span data-stu-id="c3d36-156">For the "fire-and-forget" style of messaging in gRPC, you can create a client streaming service.</span></span>

### <a name="thing_logproto"></a><span data-ttu-id="c3d36-157">thing_log.proto</span><span class="sxs-lookup"><span data-stu-id="c3d36-157">thing_log.proto</span></span>

```protobuf
service ThingLog {
  rpc OpenConnection(stream Thing) returns (ConnectionClosedResponse);
}
```

### <a name="thinglogservicecs"></a><span data-ttu-id="c3d36-158">ThingLogService.cs</span><span class="sxs-lookup"><span data-stu-id="c3d36-158">ThingLogService.cs</span></span>

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

### <a name="thinglog-client-example"></a><span data-ttu-id="c3d36-159">Exemple du client ThingLog</span><span class="sxs-lookup"><span data-stu-id="c3d36-159">ThingLog client example</span></span>

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

<span data-ttu-id="c3d36-160">Vous pouvez utiliser des RPC en streaming client pour la messagerie fire-and-forget, comme le montre l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="c3d36-160">You can use client-streaming RPCs for fire-and-forget messaging, as shown in the previous example.</span></span> <span data-ttu-id="c3d36-161">Vous pouvez également les utiliser pour envoyer de très grands jeux de données sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="c3d36-161">You can also use them for sending very large datasets to the server.</span></span> <span data-ttu-id="c3d36-162">Le même avertissement sur les performances s’applique : pour les jeux de données plus petits, utilisez `repeated` des champs dans les messages réguliers.</span><span class="sxs-lookup"><span data-stu-id="c3d36-162">The same warning about performance applies: for smaller datasets, use `repeated` fields in regular messages.</span></span>

## <a name="wcf-full-duplex-services"></a><span data-ttu-id="c3d36-163">WCF services en duplex complet</span><span class="sxs-lookup"><span data-stu-id="c3d36-163">WCF full-duplex services</span></span>

<span data-ttu-id="c3d36-164">La liaison en duplex WCF prend en charge plusieurs opérations aller simple sur l’interface de service et l’interface de rappel client.</span><span class="sxs-lookup"><span data-stu-id="c3d36-164">WCF duplex binding supports multiple one-way operations on both the service interface and the client callback interface.</span></span> <span data-ttu-id="c3d36-165">Ce support permet des conversations continues entre le client et le serveur.</span><span class="sxs-lookup"><span data-stu-id="c3d36-165">This support allows ongoing conversations between client and server.</span></span> <span data-ttu-id="c3d36-166">gRPC prend en charge quelque chose de similaire avec les CRP en streaming bidirectionnel, où les deux paramètres sont marqués avec le `stream` modificateur.</span><span class="sxs-lookup"><span data-stu-id="c3d36-166">gRPC supports something similar with bidirectional streaming RPCs, where both parameters are marked with the `stream` modifier.</span></span>

### <a name="chatproto"></a><span data-ttu-id="c3d36-167">chat.proto</span><span class="sxs-lookup"><span data-stu-id="c3d36-167">chat.proto</span></span>

```protobuf
service Chatter {
    rpc Connect(stream IncomingMessage) returns (stream OutgoingMessage);
}
```

### <a name="chatterservicecs"></a><span data-ttu-id="c3d36-168">ChatterService.cs</span><span class="sxs-lookup"><span data-stu-id="c3d36-168">ChatterService.cs</span></span>

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

<span data-ttu-id="c3d36-169">Dans l’exemple précédent, vous pouvez voir que la`IAsyncStreamReader<MessageRequest>`méthode de mise`IServerStreamWriter<MessageResponse>`en œuvre reçoit à la fois un flux de demande ( ) et un flux de réponse ( ).</span><span class="sxs-lookup"><span data-stu-id="c3d36-169">In the previous example, you can see that the implementation method receives both a request stream (`IAsyncStreamReader<MessageRequest>`) and a response stream (`IServerStreamWriter<MessageResponse>`).</span></span> <span data-ttu-id="c3d36-170">La méthode peut lire et écrire des messages jusqu’à ce que la connexion soit fermée.</span><span class="sxs-lookup"><span data-stu-id="c3d36-170">The method can read and write messages until the connection is closed.</span></span>

### <a name="chatter-client"></a><span data-ttu-id="c3d36-171">Client De chatter</span><span class="sxs-lookup"><span data-stu-id="c3d36-171">Chatter client</span></span>

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
><span data-ttu-id="c3d36-172">[Suivant précédent](wcf-bindings.md)
>[Next](metadata.md)</span><span class="sxs-lookup"><span data-stu-id="c3d36-172">[Previous](wcf-bindings.md)
[Next](metadata.md)</span></span>
