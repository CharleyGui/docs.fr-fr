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
# <a name="types-of-rpc"></a>Types de RPC

En tant que développeur de la Windows Communication Foundation (WCF), vous êtes probablement habitué à traiter les types suivants d’appel de procédure à distance (RPC) :

- Demande/réponse
- Duplex:
  - Duplex à sens unique avec session
  - Duplex complet avec session
- Unidirectionnel

Il est possible de cartographier ces types RPC assez naturellement aux concepts gRPC existants. Ce chapitre examinera chacun de ces domaines à tour de rôle. [Le chapitre 5](migrate-wcf-to-grpc.md) explorera plus en profondeur des exemples similaires.

| WCF | gRPC (en) |
| --- | ---- |
| Demande/réponse régulière | Unaire |
| Service Duplex avec session à l’aide d’une interface de rappel client | Streaming serveur |
| Service en duplex complet avec session | Streaming bidirectionnel |
| Opérations à sens unique | Streaming client |

## <a name="requestreply"></a>Demande/réponse

Pour les méthodes simples de demande/réponse qui prennent et retournent de petites quantités de données, utilisez le modèle gRPC le plus simple, le RPC unary.

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

Comme vous pouvez le voir, la mise en œuvre d’une méthode de service RPC nonaire gRPC est similaire à la mise en œuvre d’une opération WCF. La différence est qu’avec gRPC, vous remplacez une méthode de classe de base au lieu de mettre en œuvre une interface. Sur le serveur, les méthodes <xref:System.Threading.Tasks.Task%601>de base gRPC reviennent toujours, bien que le client fournisse à la fois des async et des méthodes de blocage pour appeler le service.

## <a name="wcf-duplex-one-way-to-client"></a>Duplex WCF, une façon de client

Les applications WCF (avec certaines liaisons) peuvent créer une connexion persistante entre le client et le serveur. Le serveur peut envoyer asynchronement des données au client jusqu’à ce <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> que la connexion soit fermée, en utilisant une interface de *rappel* spécifiée dans la propriété.

les services gRPC offrent des fonctionnalités similaires avec des flux de messages. Les flux ne sont pas *exactement* cartographiés pour les services duplex WCF en termes de mise en œuvre, mais vous pouvez obtenir les mêmes résultats.

### <a name="grpc-streaming"></a>gRPC streaming

gRPC prend en charge la création de flux persistants d’un client à l’autre, et d’un serveur à l’autre. Les deux types de flux peuvent être actifs en même temps. Cette capacité est appelée streaming bidirectionnel.

Vous pouvez utiliser des flux pour des messages arbitraires et asynchrones au fil du temps. Ou vous pouvez les utiliser pour passer de grands ensembles de données qui sont trop grands pour générer et envoyer une seule demande ou réponse.

L’exemple suivant montre un RPC de streaming de serveur.

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

Ce flux serveur peut être consommé à partir d’une application client, comme indiqué dans le code suivant :

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
> Les RPC en streaming de serveurs sont utiles pour les services de type abonnement. Ils sont également utiles pour l’envoi de grands ensembles de données quand il serait inefficace ou impossible de construire l’ensemble des données en mémoire. Cependant, les réponses en streaming n’est pas aussi rapide que l’envoi de `repeated` champs dans un seul message. En règle générale, le streaming ne devrait pas être utilisé pour de petits jeux de données.

### <a name="differences-from-wcf"></a>Différences par rapport à WCF

Un service en duplex WCF utilise une interface de rappel client qui peut avoir plusieurs méthodes. Un service de streaming de serveurs gRPC ne peut envoyer des messages que sur un seul flux. Si vous avez besoin de plusieurs méthodes, utilisez un type de message avec [un champ ou un champ quelconque](protobuf-any-oneof.md) pour envoyer différents messages, et écrivez du code dans le client pour les manipuler.

Dans WCF, la classe [ServiceContract](xref:System.ServiceModel.ServiceContractAttribute) avec la session est maintenue en vie jusqu’à ce que la connexion soit fermée. Plusieurs méthodes peuvent être appelées au cours de la session. Dans gRPC, `Task` le rendement de la méthode de mise en œuvre ne doit pas se terminer jusqu’à ce que la connexion soit fermée.

## <a name="wcf-one-way-operations-and-grpc-client-streaming"></a>Opérations à sens unique WCF et flux de clients gRPC

WCF fournit des opérations à `[OperationContract(IsOneWay = true)]`sens unique (marquées par ) qui renvoient une reconnaissance spécifique au transport. les méthodes de service gRPC retournent toujours une réponse, même si elle est vide. Le client doit toujours attendre cette réponse. Pour le style de messagerie « fire-and-forget » dans gRPC, vous pouvez créer un service de streaming client.

### <a name="thing_logproto"></a>thing_log.proto

```protobuf
service ThingLog {
  rpc OpenConnection(stream Thing) returns (ConnectionClosedResponse);
}
```

### <a name="thinglogservicecs"></a>ThingLogService.cs

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

### <a name="thinglog-client-example"></a>Exemple du client ThingLog

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

Vous pouvez utiliser des RPC en streaming client pour la messagerie fire-and-forget, comme le montre l’exemple précédent. Vous pouvez également les utiliser pour envoyer de très grands jeux de données sur le serveur. Le même avertissement sur les performances s’applique : pour les jeux de données plus petits, utilisez `repeated` des champs dans les messages réguliers.

## <a name="wcf-full-duplex-services"></a>WCF services en duplex complet

La liaison en duplex WCF prend en charge plusieurs opérations aller simple sur l’interface de service et l’interface de rappel client. Ce support permet des conversations continues entre le client et le serveur. gRPC prend en charge quelque chose de similaire avec les CRP en streaming bidirectionnel, où les deux paramètres sont marqués avec le `stream` modificateur.

### <a name="chatproto"></a>chat.proto

```protobuf
service Chatter {
    rpc Connect(stream IncomingMessage) returns (stream OutgoingMessage);
}
```

### <a name="chatterservicecs"></a>ChatterService.cs

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

Dans l’exemple précédent, vous pouvez voir que la`IAsyncStreamReader<MessageRequest>`méthode de mise`IServerStreamWriter<MessageResponse>`en œuvre reçoit à la fois un flux de demande ( ) et un flux de réponse ( ). La méthode peut lire et écrire des messages jusqu’à ce que la connexion soit fermée.

### <a name="chatter-client"></a>Client De chatter

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
>[Suivant précédent](wcf-bindings.md)
>[Next](metadata.md)
