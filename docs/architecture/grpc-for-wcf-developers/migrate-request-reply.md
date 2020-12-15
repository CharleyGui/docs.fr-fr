---
title: Migrer un service de demande-réponse WCF vers gRPC-gRPC pour les développeurs WCF
description: Découvrez comment migrer un service de requête-réponse simple de WCF vers gRPC.
ms.date: 09/02/2019
ms.openlocfilehash: 29a7bc77bc3a4becd767fc7a50adff5b746f54bc
ms.sourcegitcommit: d0990c1c1ab2f81908360f47eafa8db9aa165137
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97512695"
---
# <a name="migrate-a-wcf-request-reply-service-to-a-grpc-unary-rpc"></a>Migrer un service de requête-réponse WCF vers un RPC unaire gRPC

Cette section explique comment migrer un service de requête-réponse de base dans WCF vers un service RPC unaire dans ASP.NET Core gRPC. Ces services sont les types de service les plus simples dans Windows Communication Foundation (WCF) et gRPC. il s’agit donc d’un excellent point de départ. Après la migration du service, vous apprendrez à générer une bibliothèque cliente à partir du même `.proto` fichier afin de consommer le service à partir d’une application cliente .net.

## <a name="the-wcf-solution"></a>La solution WCF

La [solution PortfoliosSample](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/PortfoliosSample/wcf/TraderSys) comprend un service de portefeuille demande-réponse simple pour télécharger un ou plusieurs portefeuilles pour un commerçant donné. Le service est défini dans l’interface `IPortfolioService` avec un `ServiceContract` attribut :

```csharp
[ServiceContract]
public interface IPortfolioService
{
    [OperationContract]
    Task<Portfolio> Get(Guid traderId, int portfolioId);

    [OperationContract]
    Task<List<Portfolio>> GetAll(Guid traderId);
}
```

Le `Portfolio` modèle est une classe C# simple marquée avec [DataContract](xref:System.Runtime.Serialization.DataContractAttribute) et incluant une liste d' `PortfolioItem` objets. Ces modèles sont définis dans le `TraderSys.PortfolioData` projet avec une classe de référentiel qui représente une abstraction d’accès aux données.

```csharp
[DataContract]
public class Portfolio
{
    [DataMember]
    public int Id { get; set; }

    [DataMember]
    public Guid TraderId { get; set; }

    [DataMember]
    public List<PortfolioItem> Items { get; set; }
}

[DataContract]
public class PortfolioItem
{
    [DataMember]
    public int Id { get; set; }

    [DataMember]
    public int ShareId { get; set; }

    [DataMember]
    public int Holding { get; set; }

    [DataMember]
    public decimal Cost { get; set; }
}
```

L' `ServiceContract` implémentation utilise une classe de référentiel fournie via l’injection de dépendances qui retourne des instances des `DataContract` types :

```csharp
public class PortfolioService : IPortfolioService
{
    private readonly IPortfolioRepository _repository;

    public PortfolioService(IPortfolioRepository repository)
    {
        _repository = repository;
    }

    public async Task<Portfolio> Get(Guid traderId, int portfolioId)
    {
        return await _repository.GetAsync(traderId, portfolioId);
    }

    public async Task<List<Portfolio>> GetAll(Guid traderId)
    {
        return await _repository.GetAllAsync(traderId);
    }
}
```

## <a name="the-portfoliosproto-file"></a>Le fichier portefeuilles. proto

Si vous avez suivi les instructions de la section précédente, vous devez avoir un projet gRPC avec un `portfolios.proto` fichier qui ressemble à ceci :

```protobuf
syntax = "proto3";

option csharp_namespace = "TraderSys.Portfolios.Protos";

package PortfolioServer;

service Portfolios {
  // RPCs will go here
}
```

La première étape consiste à migrer les `DataContract` classes vers leurs équivalents Protobuf.

## <a name="convert-the-datacontract-classes-to-grpc-messages"></a>Convertir les classes DataContract en messages gRPC

La `PortfolioItem` classe sera tout d’abord convertie en message Protobuf, car la `Portfolio` classe en dépend. La classe est simple, et trois des propriétés sont mappées directement aux types de données gRPC. La `Cost` propriété, qui représente le prix payé pour les partages à l’achat, est un `decimal` champ. gRPC prend uniquement en charge `float` ou `double` pour les nombres réels, qui ne sont pas adaptés à la devise. Étant donné que les prix de partage varient d’un cent au minimum, le coût peut être exprimé en `int32` cents.

> [!NOTE]
> N’oubliez pas d’utiliser `snake_case` pour les noms de champ dans votre `.proto` fichier. Le générateur de code C# les convertira en `PascalCase` pour vous, et les utilisateurs d’autres langages vous remercient de respecter leurs différentes normes de codage.

```protobuf
message PortfolioItem {
    int32 id = 1;
    int32 share_id = 2;
    int32 holding = 3;
    int32 cost_cents = 4;
}
```

La `Portfolio` classe est un peu plus compliquée. Dans le code WCF, le développeur a utilisé un `Guid` pour la `TraderId` propriété et contient un `List<PortfolioItem>` . Dans Protobuf, qui n’a pas de type de première classe `UUID` , vous devez utiliser un `string` pour le `traderId` champ et l’analyser dans votre propre code. Pour obtenir la liste des éléments, utilisez le `repeated` mot clé sur le champ.

```protobuf
message Portfolio {
    int32 id = 1;
    string trader_id = 2;
    repeated PortfolioItem items = 3;
}
```

Maintenant que vous disposez des messages de données, vous pouvez déclarer les points de terminaison RPC du service.

## <a name="convert-servicecontract-to-a-grpc-service"></a>Convertir ServiceContract en service gRPC

La `Get` méthode WCF accepte deux paramètres : `Guid traderId` et `int portfolioId` . les méthodes de service gRPC ne peuvent prendre qu’un seul paramètre. vous devez donc créer un message pour contenir les deux valeurs. Il est courant de nommer ces objets de requête avec le même nom que la méthode suivie du suffixe `Request` . Là encore, `string` est utilisé pour le `traderId` champ à la place de `Guid` .

Le service peut simplement retourner un `Portfolio` message directement, mais là encore, cela peut affecter la compatibilité descendante à l’avenir. Il est conseillé de définir des messages distincts `Request` et `Response` pour chaque méthode dans un service, même si beaucoup d’entre eux sont les mêmes pour le moment. Par conséquent, déclarez un `GetResponse` message avec un seul `Portfolio` champ.

Cet exemple illustre la déclaration de la méthode de service gRPC avec le `GetRequest` message suivant :

```protobuf
message GetRequest {
    string trader_id = 1;
    int32 portfolio_id = 2;
}

message GetResponse {
    Portfolio portfolio = 1;
}

service Portfolios {
    rpc Get(GetRequest) returns (GetResponse);
}
```

La `GetAll` méthode WCF prend un seul paramètre, `traderId` , ce qui signifie que vous pouvez spécifier `string` comme type de paramètre. Toutefois, gRPC nécessite un type de message défini. Cette exigence permet de mettre en œuvre la pratique consistant à utiliser des messages personnalisés pour toutes les entrées et sorties, en vue d’une compatibilité descendante future.

La méthode WCF retourne également un `List<Portfolio>` , mais pour la même raison, il n’autorise pas les types de paramètres simples, gRPC n’autorise pas `repeated Portfolio` comme type de retour. Au lieu de cela, créez un `GetAllResponse` type pour encapsuler la liste.

> [!WARNING]
> Vous pouvez être tenté de créer un `PortfolioList` message ou un nom similaire et de l’utiliser sur plusieurs méthodes de service, mais vous devez résister à cette tentation. Il est impossible de savoir comment les différentes méthodes d’un service évoluent, de sorte à conserver les messages spécifiques et à les séparer correctement.

```protobuf
message GetAllRequest {
    string trader_id = 1;
}

message PortfolioList {
    repeated Portfolio portfolios = 1;
}

service Portfolios {
    rpc Get(GetRequest) returns (Portfolio);
    rpc GetAll(GetAllRequest) returns (GetAllResponse);
}
```

Si vous enregistrez votre projet avec ces modifications, la cible de génération gRPC s’exécute en arrière-plan et génère tous les types de messages Protobuf et une classe de base que vous pouvez hériter pour implémenter le service.

Ouvrez la `Services/GreeterService.cs` classe et supprimez l’exemple de code. Vous pouvez maintenant ajouter l’implémentation du service de portefeuille. La classe de base générée se trouve dans l' `Protos` espace de noms et est générée comme une classe imbriquée. gRPC crée une classe statique portant le même nom que le service dans le `.proto` fichier et une classe de base avec le suffixe `Base` à l’intérieur de cette classe statique. par conséquent, l’identificateur complet du type de base est `TraderSys.Portfolios.Protos.Portfolios.PortfoliosBase` .

```csharp
namespace TraderSys.Portfolios.Services
{
    public class PortfolioService : Protos.Portfolios.PortfoliosBase
    {
    }
}
```

La classe de base déclare `virtual` des méthodes pour `Get` et `GetAll` qui peuvent être substituées pour implémenter le service. Les méthodes sont `virtual` plutôt que `abstract` si vous ne les implémentez pas, le service peut retourner un code d' `Unimplemented` État gRPC explicite, comme vous pouvez lever une `NotImplementedException` dans du code C# normal.

La signature de toutes les méthodes de service unaires gRPC dans ASP.NET Core est cohérente. Il existe deux paramètres : le premier est le type de message déclaré dans le `.proto` fichier, et le second est un `ServerCallContext` qui fonctionne de la même façon que le `HttpContext` de ASP.net core. En fait, il existe une méthode d’extension appelée `GetHttpContext` sur la `ServerCallContext` classe que vous pouvez utiliser pour accéder au sous-jacent `HttpContext` , même si vous n’avez pas besoin de l’utiliser souvent. Nous examinerons `ServerCallContext` plus loin dans ce chapitre et également dans le chapitre traitant de l’authentification.

Le type de retour de la méthode est un `Task<T>` , où `T` est le type de message de réponse. Toutes les méthodes de service gRPC sont asynchrones.

## <a name="migrate-the-portfoliodata-library-to-net-core"></a>Migrer la bibliothèque PortfolioData vers .NET Core

À ce stade, le projet a besoin du référentiel de portefeuille et des modèles contenus dans la `TraderSys.PortfolioData` bibliothèque de classes de la solution WCF. Le moyen le plus simple de les placer consiste à créer une nouvelle bibliothèque de classes à l’aide de la boîte de dialogue **nouveau projet** de Visual Studio avec le modèle Bibliothèque de classes (.NET standard), ou à partir de la ligne de commande à l’aide de la CLI .net Core, en exécutant les commandes suivantes à partir du répertoire qui contient le `TraderSys.sln` fichier :

```dotnetcli
dotnet new classlib -o src/TraderSys.PortfolioData
dotnet sln add src/TraderSys.PortfolioData
```

Une fois que vous avez créé la bibliothèque et que vous l’avez ajoutée à la solution, supprimez le `Class1.cs` fichier généré et copiez les fichiers de la bibliothèque de la solution WCF dans le dossier de la nouvelle bibliothèque de classes, en conservant la structure de dossiers :

```
Models
  Portfolio.cs
  PortfolioItem.cs
IPortfolioRepository.cs
PortfolioRepository.cs
```

Les projets .NET de type SDK incluent automatiquement tous les `.cs` fichiers dans ou sous leur propre répertoire. vous n’avez donc pas besoin de les ajouter explicitement au projet. La seule étape restante consiste à supprimer les `DataContract` `DataMember` attributs et `Portfolio` des `PortfolioItem` classes et afin qu’ils soient des classes C# simples :

```csharp
public class Portfolio
{
    public int Id { get; set; }
    public Guid TraderId { get; set; }
    public List<PortfolioItem> Items { get; set; }
}

public class PortfolioItem
{
    public int Id { get; set; }
    public int ShareId { get; set; }
    public int Holding { get; set; }
    public decimal Cost { get; set; }
}
```

## <a name="use-aspnet-core-dependency-injection"></a>Utiliser ASP.NET Core l’injection de dépendances

Vous pouvez maintenant ajouter une référence à cette bibliothèque au projet d’application gRPC et utiliser la `PortfolioRepository` classe en utilisant l’injection de dépendances dans l’implémentation du service gRPC. Dans l’application WCF, l’injection de dépendances a été fournie par le conteneur IoC Autofac. ASP.NET Core intègre une injection de dépendances. Vous pouvez inscrire le référentiel dans la `ConfigureServices` méthode de la `Startup` classe :

```csharp
public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
        // Register the repository class as a scoped service (instance per request)
        services.AddScoped<IPortfolioRepository, PortfolioRepository>();

        services.AddGrpc();
    }

    // ...
}
```

L' `IPortfolioRepository` implémentation peut maintenant être spécifiée en tant que paramètre de constructeur dans la `PortfolioService` classe, comme suit :

```csharp
public class PortfolioService : Protos.Portfolios.PortfoliosBase
{
    private readonly IPortfolioRepository _repository;

    public PortfolioService(IPortfolioRepository repository)
    {
        _repository = repository;
    }
}
```

## <a name="implement-the-grpc-service"></a>Implémenter le service gRPC

Maintenant que vous avez déclaré vos messages et votre service dans le `portfolios.proto` fichier, vous devez implémenter les méthodes de service dans la `PortfolioService` classe qui hérite de la classe générée par gRPC `Portfolios.PortfoliosBase` . Les méthodes sont déclarées comme `virtual` dans la classe de base. Si vous ne les remplacez pas, ils retournent un code d’État gRPC « non implémenté » par défaut.

Commencez par implémenter la `Get` méthode. La substitution par défaut se présente comme dans l’exemple suivant :

```csharp
public override Task<GetResponse> Get(GetRequest request, ServerCallContext context)
{
    return base.Get(request, context);
}
```

Le premier problème est qu’il `request.TraderId` s’agit d’une chaîne, et le service requiert un `Guid` . Même si le format attendu pour la chaîne est `UUID` , le code doit gérer la possibilité qu’un appelant ait envoyé une valeur non valide et réponde de manière appropriée. Le service peut répondre avec des erreurs en levant un `RpcException` et en utilisant le `InvalidArgument` code d’état standard pour exprimer le problème :

```csharp
public override Task<GetResponse> Get(GetRequest request, ServerCallContext context)
{
    if (!Guid.TryParse(request.TraderId, out var traderId))
    {
        throw new RpcException(new Status(StatusCode.InvalidArgument, "traderId must be a UUID"));
    }

    return base.Get(request, context);
}
```

Une fois que la valeur est correcte `Guid` pour `traderId` , vous pouvez utiliser le référentiel pour récupérer le portefeuille et le renvoyer au client :

```csharp
    var response = new GetResponse
    {
        Portfolio = await _repository.GetAsync(request.TraderId, request.PortfolioId)
    };
```

### <a name="map-internal-models-to-grpc-messages"></a>Mapper les modèles internes aux messages gRPC

Le code précédent ne fonctionne pas réellement, car le référentiel retourne son propre modèle POCO `Portfolio` , mais gRPC a besoin de son propre message Protobuf `Portfolio` . Comme lorsque vous mappez des types de Entity Framework à des types de transfert de données, la meilleure solution consiste à fournir une conversion entre les deux. Un bon emplacement pour mettre le code pour cette conversion se trouve dans la classe générée par Protobuf, qui est déclarée en tant que `partial` classe afin de pouvoir être étendue :

```csharp
namespace TraderSys.Portfolios.Protos
{
    public partial class PortfolioItem
    {
        public static PortfolioItem FromRepositoryModel(PortfolioData.Models.PortfolioItem source)
        {
            if (source is null) return null;

            return new PortfolioItem
            {
                Id = source.Id,
                ShareId = source.ShareId,
                Holding = source.Holding,
                CostCents = (int)(source.Cost * 100)
            };
        }
    }

    public partial class Portfolio
    {
        public static Portfolio FromRepositoryModel(PortfolioData.Models.Portfolio source)
        {
            if (source is null) return null;

            var target = new Portfolio
            {
                Id = source.Id,
                TraderId = source.TraderId.ToString(),
            };

            target.Items.AddRange(source.Items.Select(PortfolioItem.FromRepositoryModel));

            return target;
        }
    }
}
```

> [!NOTE]
> Vous pouvez utiliser une bibliothèque comme [AutoMapper](https://automapper.org/) pour gérer cette conversion des classes de modèle internes en types Protobuf, à condition de configurer les conversions de type de niveau inférieur comme `string` / `Guid` ou `decimal` / `double` et le mappage de liste.

Maintenant que le code de conversion est en place, vous pouvez terminer l' `Get` implémentation de la méthode :

```csharp
public override async Task<GetResponse> Get(GetRequest request, ServerCallContext context)
{
    if (!Guid.TryParse(request.TraderId, out var traderId))
    {
        throw new RpcException(new Status(StatusCode.InvalidArgument, "traderId must be a UUID"));
    }

    var portfolio = await _repository.GetAsync(traderId, request.PortfolioId);

    return new GetResponse
    {
        Portfolio = Portfolio.FromRepositoryModel(portfolio)
    };
}

```

L’implémentation de la `GetAll` méthode est similaire. Notez que les `repeated` champs des messages Protobuf sont générés en tant que `readonly` Propriétés de type `RepeatedField<T>` , de sorte que vous devez leur ajouter des éléments à l’aide de la `AddRange` méthode, comme dans cet exemple :

```csharp
public override async Task<GetAllResponse> GetAll(GetAllRequest request, ServerCallContext context)
{
    if (!Guid.TryParse(request.TraderId, out var traderId))
    {
        throw new RpcException(new Status(StatusCode.InvalidArgument, "traderId must be a UUID"));
    }

    var portfolios = await _repository.GetAllAsync(traderId);

    var response = new GetAllResponse();
    response.Portfolios.AddRange(portfolios.Select(Portfolio.FromRepositoryModel));

    return response;
}
```

Après avoir migré le service WCF Request-Reply vers gRPC, nous allons maintenant créer un client à partir du `.proto` fichier.

## <a name="generate-client-code"></a>Générer le code client

Créez une bibliothèque de classes .NET Standard dans la même solution pour contenir le client. Il s’agit principalement d’un exemple de création de code client, mais vous pouvez empaqueter une telle bibliothèque à l’aide de NuGet et la distribuer sur un référentiel interne pour que d’autres équipes .NET puissent les utiliser. Continuez et ajoutez une nouvelle bibliothèque de classes .NET Standard appelée `TraderSys.Portfolios.Client` à la solution et supprimez le `Class1.cs` fichier.

> [!CAUTION]
> Le package NuGet [.net. client GRPC](https://www.nuget.org/packages/Grpc.Net.Client) nécessite .net Core 3,0 (ou un .NET standard autre Runtime conforme à 2,1). Les versions antérieures de .NET Framework et .NET Core sont prises en charge par le package NuGet [GRPC. Core](https://www.nuget.org/packages/Grpc.Core) .

Dans Visual Studio 2019, vous pouvez ajouter des références aux services gRPC de la même façon que vous ajoutez des références de service aux projets WCF dans les versions antérieures de Visual Studio. Les références de service et les services connectés sont tous gérés sous la même interface utilisateur maintenant. Vous pouvez accéder à l’interface utilisateur en cliquant avec le bouton droit sur le nœud **dépendances** dans le `TraderSys.Portfolios.Client` projet dans Explorateur de solutions et en sélectionnant **Ajouter un service connecté**. Dans la fenêtre outil qui s’affiche, sélectionnez la section **références de service** , puis sélectionnez **Ajouter une nouvelle référence de service gRPC**:

![Interface utilisateur Services connectés dans Visual Studio 2019](media/migrate-request-reply/add-connected-service.png)

Accédez au `portfolios.proto` fichier dans le `TraderSys.Portfolios` projet, laissez **client** sous **sélectionnez le type de classe à générer**, puis sélectionnez **OK**:

![Boîte de dialogue Ajouter une nouvelle référence de service gRPC dans Visual Studio 2019](media/migrate-request-reply/add-new-grpc-service-reference.png)

> [!TIP]
> Notez que cette boîte de dialogue fournit également un champ d’URL. Si votre organisation gère un répertoire Web de `.proto` fichiers, vous pouvez créer des clients simplement en définissant cette adresse URL.

Lorsque vous utilisez la fonctionnalité **Ajouter un service connecté** de Visual Studio, le `portfolios.proto` fichier est ajouté au projet de bibliothèque de classes en tant que *fichier lié* plutôt que copié, de sorte que les modifications apportées au fichier dans le projet de service sont automatiquement appliquées dans le projet client. L' `<Protobuf>` élément dans le `csproj` fichier se présente comme suit :

```xml
<Protobuf Include="..\TraderSys.Portfolios\Protos\portfolios.proto" GrpcServices="Client">
  <Link>Protos\portfolios.proto</Link>
</Protobuf>
```

> [!TIP]
> Si vous n’utilisez pas Visual Studio ou si vous préférez travailler à partir de la ligne de commande, vous pouvez utiliser l' `dotnet-grpc` outil global pour gérer les références Protobuf dans un projet .net gRPC. Pour plus d’informations, consultez la [ `dotnet-grpc` documentation](/aspnet/core/grpc/dotnet-grpc).

### <a name="use-the-portfolios-service-from-a-client-application"></a>Utiliser le service portefeuilles à partir d’une application cliente

Le code suivant est un bref exemple illustrant comment utiliser le client généré dans une application console. Une exploration plus détaillée du code client gRPC est à la fin de ce chapitre.

```csharp
public class Program
{
    public async Task Main(string[] args)
    {
        GetResponse response;

        using (var channel = GrpcChannel.ForAddress("https://localhost:5001"))
        {
            var client = new Protos.Portfolios.PortfoliosClient(channel);

            response = await client.GetAsync(new GetRequest
            {
                TraderId = args[0],
                PortfolioId = int.Parse(args[1])
            });
        }

        foreach (var item in response.Portfolio.Items)
        {
            Console.WriteLine($"Holding {item.Holding} of Share ID {item.ShareId}.");
        }
    }
}
```

Vous avez maintenant migré une application WCF de base vers un service ASP.NET Core gRPC et créé un client pour consommer le service à partir d’une application .NET. La section suivante couvre les services duplex plus impliqués.

>[!div class="step-by-step"]
>[Précédent](create-project.md) 
> [Suivant](migrate-duplex-services.md)
