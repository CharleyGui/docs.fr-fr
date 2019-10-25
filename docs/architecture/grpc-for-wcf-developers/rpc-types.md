---
title: Types de RPC-gRPC pour les développeurs WCF
description: Examen des types d’appel de procédure distante pris en charge par WCF et de leurs équivalents dans gRPC
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: ce5bf03b01dff3f7bb201ff08c9065abc2e58360
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846229"
---
# <a name="types-of-rpc"></a>Types de RPC

En tant que développeur Windows Communication Foundation (WCF), vous êtes probablement employé pour traiter les types d’appel de procédure distante (RPC) suivants :

- Demande/réponse
- Duplex
  - Duplex unidirectionnel avec session
  - Full duplex avec session
- Unidirectionnel

Il est possible de mapper ces types RPC assez naturellement à des concepts gRPC existants. ce chapitre examine chacun de ces domaines à leur tour. Des exemples similaires seront explorés plus en détail dans le [Chapitre 5](migrate-wcf-to-grpc.md).

| WCF | gRPC |
| --- | ---- |
| Demande/réponse régulière | Unaire |
| Service duplex avec session utilisant une interface de rappel client | Streaming de serveur |
| Service Full duplex avec session | Diffusion bidirectionnelle |
| Opérations unidirectionnelles | Diffusion en continu du client |

## <a name="requestreply"></a>Demande/réponse

Pour les méthodes de requête/réponse simples qui acceptent et retournent de petites quantités de données, utilisez le modèle gRPC le plus simple, le RPC unaire.

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

Comme vous pouvez le voir, l’implémentation d’une méthode de service RPC unaire gRPC est très semblable à l’implémentation d’une opération WCF, à la différence près qu’avec gRPC, vous substituez une méthode de classe de base au lieu d’implémenter une interface. Notez que sur le serveur, les méthodes de base gRPC retournent toujours un <xref:System.Threading.Tasks.Task%601>, bien que le client fournisse des méthodes Async et Blocking pour appeler le service.

## <a name="wcf-duplex-one-way-to-client"></a>Duplex WCF, unidirectionnel pour le client

Les applications WCF (avec certaines liaisons) peuvent créer une connexion permanente entre le client et le serveur, et le serveur peut envoyer de manière asynchrone des données au client jusqu’à ce que la connexion soit fermée, à l’aide d’une *interface de rappel* spécifiée dans le <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> propriété.

les services gRPC offrent des fonctionnalités similaires à celles des flux de messages. Les flux ne sont pas mappés *exactement* aux services duplex WCF en termes d’implémentation, mais les mêmes résultats peuvent être obtenus.

### <a name="grpc-streaming"></a>diffusion en continu gRPC

gRPC prend en charge la création de flux persistants entre le client et le serveur, et du serveur au client. Les deux types de flux peuvent être actifs simultanément. C’est ce que l’on appelle la diffusion bidirectionnelle. Les flux peuvent être utilisés pour la messagerie asynchrone arbitraire dans le temps, ou pour transmettre des jeux de données volumineux qui sont trop volumineux pour être générés et envoyés dans une requête ou une réponse unique.

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

Ce flux de serveur peut être consommé à partir d’une application cliente, comme illustré dans le code suivant :

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
> Les RPC de streaming de serveur sont utiles pour les services de type abonnement, ainsi que pour l’envoi de jeux de données très volumineux lorsqu’il est inefficace ou impossible de générer l’ensemble du jeu de données en mémoire. Toutefois, les réponses de diffusion en continu ne sont pas aussi rapides que l’envoi de `repeated` champs dans un message unique, de sorte que la diffusion en continu des règles ne doit pas être utilisée pour les petits jeux de données.

### <a name="differences-to-wcf"></a>Différences avec WCF

Un service duplex WCF utilise une interface de rappel client qui peut avoir plusieurs méthodes. Un service de diffusion en continu gRPC Server peut uniquement envoyer des messages sur un seul flux. Si vous avez besoin de plusieurs méthodes, utilisez un type de message avec un [champ any ou](protobuf-any-oneof.md) un champ pour envoyer des messages différents et écrire du code sur le client pour les gérer.

Dans WCF, la classe [ServiceContract](xref:System.ServiceModel.ServiceContractAttribute) avec la session reste active jusqu’à ce que la connexion soit fermée, et plusieurs méthodes peuvent être appelées dans la session. Dans gRPC, le `Task` retourné par la méthode d’implémentation ne doit pas se terminer tant que la connexion n’est pas fermée.

## <a name="wcf-one-way-operations-and-grpc-client-streaming"></a>Opérations unidirectionnelles WCF et diffusion en continu du client gRPC

WCF fournit des opérations unidirectionnelles (marquées avec `[OperationContract(IsOneWay = true)]`) qui retournent un accusé de réception spécifique au transport. les méthodes de service gRPC retournent toujours une réponse, même si elles sont vides, et le client doit toujours attendre cette réponse. Pour la messagerie de style « Fire-and-oublier » dans gRPC, vous pouvez créer un service de diffusion en continu client.

### <a name="thing_logproto"></a>thing_log. proto

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

### <a name="thinglog-client-example"></a>Exemple de client ThingLog

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

Là encore, les RPC de la diffusion en continu des clients peuvent être utilisés pour la messagerie de déclenchement et d’oubli, comme indiqué dans l’exemple précédent, mais également pour l’envoi de jeux de données très volumineux au serveur. Le même avertissement sur les performances s’applique : pour les jeux de données plus petits, utilisez `repeated` champs dans des messages ordinaires.

## <a name="wcf-full-duplex-services"></a>Services duplex intégral WCF

La liaison duplex WCF prend en charge plusieurs opérations unidirectionnelles sur l’interface de service et l’interface de rappel client, ce qui permet des conversations continues entre le client et le serveur. gRPC prend en charge des appels de manière similaire avec les RPC de diffusion bidirectionnelle, où les deux paramètres sont marqués avec le modificateur `stream`.

### <a name="chatproto"></a>conversation. proto

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

Dans l’exemple précédent, vous pouvez voir que la méthode d’implémentation reçoit à la fois un flux de demande (`IAsyncStreamReader<MessageRequest>`) et un flux de réponse (`IServerStreamWriter<MessageResponse>`), et peut lire et écrire des messages jusqu’à ce que la connexion soit fermée.

### <a name="chatter-client"></a>Client chatter

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
>[Précédent](wcf-bindings.md)
>[Suivant](metadata.md)
