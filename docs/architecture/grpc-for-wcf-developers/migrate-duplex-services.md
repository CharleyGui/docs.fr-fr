---
title: Migrer les services duplex WCF vers gRPC-gRPC pour les développeurs WCF
description: Découvrez comment migrer différentes formes de service duplex WCF vers des services de streaming gRPC.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 525dc3006c45f773242ab08b112dba72087a2e3f
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834517"
---
# <a name="migrate-wcf-duplex-services-to-grpc"></a>Migrer les services duplex WCF vers gRPC

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Maintenant que les concepts de base sont en place, cette section aborde les services gRPC de *diffusion en continu* plus compliqués.

Il existe plusieurs façons d’utiliser les services duplex dans Windows Communication Foundation (WCF). Certains services sont initiés par le client, puis diffusent en continu des données à partir du serveur. D’autres services duplex intégral peuvent impliquer une communication bidirectionnelle continue comme l’exemple « calculatrice » classique dans la documentation WCF. Ce chapitre prend en compte deux implémentations de « cotations boursières » WCF possibles et les migre vers gRPC : l’un à l’aide d’un RPC de diffusion de serveur et l’autre à l’aide d’un RPC de streaming bidirectionnel.

## <a name="server-streaming-rpc"></a>RPC de streaming de serveur

Dans l' [exemple de solution WCF SimpleStockTicker](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/SimpleStockTickerSample/wcf/SimpleStockTicker), *SimpleStockPriceTicker*, il existe un service duplex dans lequel le client démarre la connexion avec une liste de symboles boursiers, et le serveur utilise l' *interface de rappel* pour envoyer des mises à jour en tant qu' deviennent disponibles. Le client implémente cette interface pour répondre aux appels à partir du serveur.

### <a name="the-wcf-solution"></a>La solution WCF

La solution WCF est implémentée en tant que serveur NetTCP auto-hébergé dans une application console .NET Framework 4. x.

#### <a name="the-servicecontract"></a>ServiceContract

```csharp
[ServiceContract(SessionMode = SessionMode.Required, CallbackContract = typeof(ISimpleStockTickerCallback))]
public interface ISimpleStockTickerService
{
    [OperationContract(IsOneWay = true)]
    void Subscribe(string[] symbols);
}
```

Le service a une méthode unique sans type de retour, car il utilisera l’interface `ISimpleStockTickerCallback` de rappel pour envoyer des données au client en temps réel.

#### <a name="the-callback-interface"></a>Interface de rappel

```csharp
[ServiceContract]
public interface ISimpleStockTickerCallback
{
    [OperationContract(IsOneWay = true)]
    void Update(string symbol, decimal price);
}
```

Les implémentations de ces interfaces se trouvent dans la solution, ainsi que les dépendances externes factices pour fournir des données de test.

### <a name="grpc-streaming"></a>diffusion en continu gRPC

La méthode gRPC pour gérer les données en temps réel est différente. Un appel du client au serveur peut créer un flux persistant, qui peut être surveillé pour les messages arrivant de manière asynchrone. Malgré la différence, les flux peuvent être un moyen plus intuitif de traiter ces données et sont plus pertinents dans la programmation moderne avec l’accent sur LINQ, les flux réactifs, la programmation fonctionnelle, etc.

La définition de service a besoin de deux messages : un pour la demande et un pour le flux. Le service retourne un flux du `StockTickerUpdate` message à l’aide du `stream` mot clé `return` dans sa déclaration. Il est recommandé d’ajouter un `Timestamp` à la mise à jour pour afficher l’heure exacte à laquelle le prix a changé.

#### <a name="simple_stock_tickerproto"></a>simple_stock_ticker. proto

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
  int32 priceCents = 2;
  google.protobuf.Timestamp time = 3;
}
```

### <a name="implement-the-simplestockticker"></a>Implémenter SimpleStockTicker

Réutilisez le `StockPriceSubscriber` substitut du projet WCF en copiant les trois classes de la `TraderSys.StockMarket` bibliothèque de classes dans une nouvelle bibliothèque de classes .NET standard dans la solution cible. Pour mieux suivre les meilleures pratiques, ajoutez `Factory` un type pour créer des instances de celui- `IStockPriceSubscriberFactory` ci et enregistrez le avec les services d’injection de dépendances de ASP.net core.

#### <a name="the-factory-implementation"></a>Implémentation de la fabrique

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

#### <a name="registering-the-factory"></a>Inscription de la fabrique

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddGrpc();
    services.AddSingleton<IStockPriceSubscriberFactory, StockPriceSubscriberFactory>();
}
```

À présent, cette classe peut être utilisée pour implémenter le service gRPC StockTicker.

#### <a name="stocktickerservicecs"></a>StockTickerService.cs

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

Comme vous pouvez le voir, bien que la Déclaration `.proto` dans le fichier indique que la méthode retourne un flux `StockTickerUpdate` de messages, en fait, elle retourne `Task`une vanille. Le travail de création du flux est géré par le code généré et les bibliothèques d’exécution gRPC, qui fournissent `IServerStreamWriter<StockTickerUpdate>` le flux de réponse, prêt à être utilisé.

Contrairement à un service duplex WCF, où l’instance de la classe de service reste active pendant que la connexion est ouverte, le service gRPC utilise la tâche retournée pour maintenir le service actif. La tâche ne peut pas se terminer tant que la connexion n’est pas fermée.

Le service peut savoir à quel moment le client a fermé la connexion à `CancellationToken` l’aide `ServerCallContext`de l’de l'. Une méthode statique simple, `AwaitCancellation`, est utilisée pour créer une tâche qui se termine lorsque le jeton est annulé.

Dans la `Subscribe` méthode, récupérez un `StockPriceSubscriber` et ajoutez un gestionnaire d’événements qui écrit dans le flux de réponse. Attendez ensuite que la connexion soit fermée avant de supprimer immédiatement la `subscriber` pour empêcher la tentative d’écriture de données dans le flux fermé.

La `WriteUpdateAsync` méthode a un `try` / blocpourgérerleserreursquipeuventseproduirelorsdel’écritured’unmessagedansleflux.`catch` Il s’agit d’un point important à prendre en compte dans les connexions persistantes sur les réseaux, qui peuvent être interrompues à n’importe quelle milliseconde, que ce soit intentionnellement ou en raison d’une défaillance.

### <a name="using-the-stocktickerservice-from-a-client-application"></a>Utilisation du StockTickerService à partir d’une application cliente

Suivez les mêmes étapes de la section précédente pour créer une bibliothèque de classes de client partageable `.proto` à partir du fichier. Dans l’exemple, il existe une application console .NET Core 3,0 qui montre comment utiliser le client.

#### <a name="example-programcs"></a>Exemple de Program.cs

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

Dans ce cas, la `Subscribe` méthode sur le client généré n’est pas asynchrone. Le flux est créé et utilisable immédiatement, car sa `MoveNext` méthode est asynchrone et la première fois qu’il est appelé, il ne se termine pas tant que la connexion n’est pas active.

Le flux est passé à une méthode `DisplayAsync` Async ; l’application attend ensuite que l’utilisateur appuie sur une touche, puis annule la `DisplayAsync` méthode et attend la fin de la tâche avant de quitter.

> [!NOTE]
> Ce code utilise la nouvelle C# syntaxe 8 « using DECLARATION » pour supprimer le flux et le canal quand la `Main` méthode se termine. C’est une petite modification, mais une bonne chose qui réduit les retraits et les lignes vides.

#### <a name="consume-the-stream"></a>Utiliser le flux

WCF utilisait des interfaces de rappel pour permettre au serveur d’appeler des méthodes directement sur le client. les flux gRPC fonctionnent différemment. Le client itère au sein du flux retourné et traite les messages, comme s’ils étaient retournés par une méthode locale `IEnumerable`retournant un.

Le `IAsyncStreamReader<T>` type fonctionne très bien comme `IEnumerator<T>`un : il existe `MoveNext` une méthode qui retourne la valeur true tant qu’il y a plus de données `Current` , et une propriété qui retourne la valeur la plus récente. La seule différence est que la `MoveNext` méthode retourne un `Task<bool>` au lieu d’un `bool`seul. La `ReadAllAsync` méthode d’extension encapsule le flux dans une C# norme `IAsyncEnumerable` 8 qui peut être utilisée avec la `await foreach` nouvelle syntaxe.

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
> La section sur les [bibliothèques clientes](client-libraries.md#iobservable) à la fin de ce chapitre explique comment ajouter une méthode d’extension et des classes `IAsyncStreamReader<T>` pour encapsuler un `IObservable<T>` pour les développeurs qui utilisent des modèles de programmation réactifs.

Là encore, veillez à intercepter les exceptions ici en <xref:System.OperationCanceledException> raison de la possibilité d’une défaillance du réseau, ainsi qu’à lever inévitablement, car le code utilise un <xref:System.Threading.CancellationToken> pour rompre la boucle. Le `RpcException` type contient de nombreuses informations utiles sur les erreurs d’exécution gRPC, y `StatusCode`compris le. Pour plus d’informations, consultez [ *gestion des erreurs* dans le chapitre 4](error-handling.md).

## <a name="bidirectional-streaming"></a>Diffusion bidirectionnelle

Un service WCF Full-duplex permet une messagerie asynchrone et en temps réel dans les deux sens. Dans l’exemple de diffusion en continu du serveur, le client démarre une demande, puis reçoit un flux de mises à jour. Une meilleure version de ce service permettrait au client d’ajouter et de supprimer des actions de la liste sans avoir à arrêter et à créer un nouvel abonnement. Cette fonctionnalité a été implémentée dans l' [exemple de solution FullStockTicker](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/wcf/FullStockTicker).

L' `IFullStockTickerService` interface fournit trois méthodes :

- `Subscribe`démarre la connexion.
- `AddSymbol`Ajoute un symbole de cotations boursières à surveiller.
- `RemoveSymbol`supprime un symbole de la liste de suivi.

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

L’interface de rappel reste la même.

L’implémentation de ce modèle dans gRPC est moins simple, car il existe désormais deux flux de données avec des messages transmis : un du client au serveur et un autre du serveur au client. Il n’est pas possible d’utiliser plusieurs méthodes pour implémenter l’opération d’ajout et de suppression, mais plusieurs types de messages peuvent être transmis sur un seul flux, `Any` en utilisant `oneof` le type ou le mot clé qui ont été traités dans le [chapitre 3](protobuf-any-oneof.md).

Pour un cas où un ensemble spécifique de types est acceptable, `oneof` est une meilleure façon de le faire. Utilisez un `ActionMessage` qui peut contenir un `AddSymbolRequest` ou un `RemoveSymbolRequest`.

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

Déclarez un service de streaming bidirectionnel qui prend un flux de `ActionMessage` messages.

```protobuf
service FullStockTicker {
  rpc Subscribe (stream ActionMessage) returns (stream StockTickerUpdate);
}
```

L’implémentation de ce service est similaire à l’exemple précédent, sauf que le premier paramètre de `Subscribe` la méthode est désormais `IAsyncStreamReader<ActionMessage>`un, qui peut être utilisé pour gérer `Add` les `Remove` requêtes et.

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

La `ActionMessage` classe que gRPC a générée pour nous garantit qu’une seule `Add` des propriétés et `Remove` peut être définie, et que la recherche n’est `null` pas un moyen valide de trouver le type de message utilisé, mais il existe un meilleur moyen . La génération de code a également `enum ActionOneOfCase` créé un `ActionMessage` dans la classe, qui ressemble à ceci :

```csharp
public enum ActionOneofCase {
    None = 0,
    Add = 1,
    Remove = 2,
}
```

La propriété `ActionCase` sur l' `ActionMessage` objet peut être utilisée avec une `switch` instruction pour déterminer quel champ est défini.

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
> L' `switch` instruction a un `default` cas qui enregistre un avertissement en cas de `ActionOneOfCase` détection d’une valeur inconnue. Cela peut être utile pour indiquer qu’un client utilise une version plus récente du `.proto` fichier qui a ajouté d’autres actions. C’est l’une des raisons pour `switch` lesquelles l’utilisation d’un `null` est mieux que le test de sur des champs connus.

### <a name="use-the-fullstocktickerservice-from-a-client-application"></a>Utiliser FullStockTickerService à partir d’une application cliente

Il existe une simple application WPF .NET Core 3,0 pour illustrer l’utilisation de ce client plus complexe. L’application complète est disponible [sur GitHub](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTicker).

Le client est utilisé dans la `MainWindowViewModel` classe, qui obtient une instance `FullStockTicker.FullStockTickerClient` du type à partir de l’injection de dépendances.

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

L’objet retourné par la `client.Subscribe()` méthode est maintenant une instance du type `AsyncDuplexStreamingCall<TRequest, TResponse>`de bibliothèque gRPC, qui fournit un `RequestStream` pour l’envoi de demandes au serveur et un `ResponseStream` pour la gestion des réponses.

Le flux de requête est utilisé à partir `ICommand` de certaines méthodes WPF pour ajouter et supprimer des symboles. Pour chaque opération, définissez le champ approprié sur un `ActionMessage` objet :

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
> La définition de la valeur d’un champdansunmessageeffaceautomatiquementtousleschampsquiontétédéfinisprécédemment.`oneof`

Le flux de réponses est géré dans une `async` méthode, et le `Task` retourne est conservé pour être supprimé lorsque la fenêtre est fermée.

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

### <a name="client-clean-up"></a>Nettoyage du client

Lorsque la fenêtre est fermée et que `MainWindowViewModel` le est supprimé (à partir de `Closed` l’événement `MainWindow`de), il est recommandé de supprimer correctement l' `AsyncDuplexStreamingCall` objet. En particulier, la `CompleteAsync` méthode `RequestStream` sur doit être appelée pour fermer correctement le flux sur le serveur. L’exemple suivant illustre la `DisposeAsync` méthode de l’exemple de modèle d’affichage :

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

La fermeture des flux de requête permet au serveur de supprimer ses propres ressources en temps opportun. Cela améliore l’efficacité et l’évolutivité des services et empêche les exceptions.

>[!div class="step-by-step"]
>[Précédent](migrate-request-reply.md)
>[Suivant](streaming-versus-repeated.md)
