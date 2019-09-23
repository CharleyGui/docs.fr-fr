---
title: Migrer un service de demande-réponse WCF vers gRPC-gRPC pour les développeurs WCF
description: Découvrez comment migrer un service de requête-réponse simple de WCF vers gRPC.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: ac9eecf66a7ac37a1df9714e6383f7eaebae4781
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184308"
---
# <a name="migrate-a-wcf-request-reply-service-to-a-grpc-unary-rpc"></a>Migrer un service de requête-réponse WCF vers un RPC unaire gRPC

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Cette section explique comment migrer un service de requête-réponse de base dans WCF vers un service RPC unaire dans ASP.NET Core gRPC. Ces services sont les types de service les plus simples dans Windows Communication Foundation (WCF) et gRPC. il s’agit donc d’un excellent point de départ. Après la migration du service, vous apprendrez à générer une bibliothèque cliente à `.proto` partir du même fichier afin de consommer le service à partir d’une application cliente .net.

## <a name="the-wcf-solution"></a>La solution WCF

La [solution PortfoliosSample](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/PortfoliosSample/wcf/TraderSys) comprend un service de portefeuille demande-réponse simple pour télécharger un seul portefeuille, ou tous les portefeuilles pour un commerçant donné. Le service est défini dans l’interface `IPortfolioService` avec un `ServiceContract` attribut :

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

Le `Portfolio` modèle est une classe C# simple marquée avec [DataContract](xref:System.Runtime.Serialization.DataContractAttribute), y compris une liste `PortfolioItem` d’objets. Ces modèles sont définis dans le `TraderSys.PortfolioData` projet, ainsi qu’une classe de référentiel représentant une abstraction d’accès aux données.

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

L' `ServiceContract` implémentation utilise une classe `DataContract` de référentiel fournie via l’injection de dépendances qui retourne des instances des types.

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

Si vous avez suivi les instructions de la section précédente, vous devez avoir un projet gRPC avec `portfolios.proto` un fichier similaire à celui-ci.

```protobuf
syntax = "proto3";

option csharp_namespace = "TraderSys.Portfolios.Protos";

package PortfolioServer;

service Portfolios {
  // RPCs will go here
}
```

La première étape consiste à migrer `DataContract` les classes vers leurs équivalents Protobuf.

## <a name="convert-the-datacontracts-to-grpc-messages"></a>Convertir le DataContracts en messages gRPC

La `PortfolioItem` classe sera tout d’abord convertie en un message Protobuf `Portfolio` , car la classe en dépend. La classe est très simple, et trois des propriétés sont mappées directement aux types de données gRPC. La `Cost` propriété, qui représente le prix payé pour les partages à l’achat `decimal` , est un champ, et `float` gRPC `double` prend uniquement en charge ou pour les nombres réels, ce qui n’est pas adapté à la devise. Étant donné que les prix de partage varient d’un cent au minimum, le coût peut être `int32` exprimé en cents.

> [!NOTE]
> N’oubliez pas `camelCase` d’utiliser pour les noms `.proto` de champ dans C# votre fichier ; le générateur de `PascalCase` code les convertira en pour vous, et les utilisateurs d’autres langages vous remercieront pour respecter leurs différentes normes de codage.

```protobuf
message PortfolioItem {
    int32 id = 1;
    int32 shareId = 2;
    int32 holding = 3;
    int32 costCents = 4;
}
```

La `Portfolio` classe est un peu plus compliquée. Dans le code WCF, le développeur a utilisé `Guid` un pour `TraderId` la propriété et contient un `List<PortfolioItem>`. Dans Protobuf, qui n’a pas de type de `UUID` première classe, vous devez utiliser `string` un pour `traderId` le champ et l’analyser dans votre propre code. Pour obtenir la liste des éléments, utilisez `repeated` le mot clé sur le champ.

```protobuf
message Portfolio {
    int32 id = 1;
    string traderId = 2;
    repeated PortfolioItem items = 3;
}
```

Maintenant que nous avons nos messages de données, nous pouvons déclarer les points de terminaison RPC du service.

## <a name="convert-the-servicecontract-to-a-grpc-service"></a>Convertir le ServiceContract en service gRPC

La méthode `Get` WCF accepte deux paramètres : `Guid traderId` et `int portfolioId`. les méthodes de service gRPC peuvent uniquement accepter un seul paramètre, de sorte qu’un message doit être créé pour contenir les deux valeurs. Il est courant de nommer ces objets de requête avec le même nom que la méthode et le suffixe `Request`. Là encore `string` , est utilisé pour le `traderId` champ à la `Guid`place de.

Le service peut simplement retourner un `Portfolio` message directement, mais là encore, cela peut avoir un impact sur la compatibilité descendante à l’avenir. Il est conseillé de définir des messages distincts `Request` et `Response` pour chaque méthode dans un service, même si beaucoup d’entre eux sont les mêmes pour le moment, il est `GetResponse` donc préférable de déclarer `Portfolio` un message avec un seul champ.

L’exemple suivant illustre la déclaration de la méthode de service gRPC à `GetRequest` l’aide du message :

```protobuf
message GetRequest {
    string traderId = 1;
    int32 portfolioId = 2;
}

message GetResponse {
    Portfolio portfolio = 1;
}

service Portfolios {
    rpc Get(GetRequest) returns (GetResponse);
}
```

La méthode `GetAll` WCF n’accepte qu’un seul paramètre `traderId`,. il peut donc sembler que l’un `string` d’eux peut être spécifié comme type de paramètre, mais gRPC nécessite un type de message défini. Cette exigence permet de mettre en œuvre la pratique consistant à utiliser des messages personnalisés pour toutes les entrées et sorties, en vue d’une compatibilité descendante future.

La méthode WCF a également retourné `List<Portfolio>`un, mais pour la même raison, elle n’autorise pas les types de paramètres `repeated Portfolio` simples, gRPC n’autorise pas comme type de retour. Au lieu de cela `GetAllResponse` , créez un type pour encapsuler la liste.

> [!WARNING]
> Vous pouvez être tenté de créer un `PortfolioList` message ou similaire et de l’utiliser dans plusieurs méthodes de service, mais vous devez résister à cette tentation. Il est impossible de savoir comment les différentes méthodes d’un service peuvent évoluer à l’avenir, afin de conserver les messages spécifiques et séparés.

```protobuf
message GetAllRequest {
    string traderId = 1;
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

Ouvrez la `Services/GreeterService.cs` classe et supprimez l’exemple de code. Vous pouvez maintenant ajouter l’implémentation du service de portefeuille. La classe de base générée se trouve dans `Protos` l’espace de noms et est générée comme une classe imbriquée. gRPC crée une classe statique portant le même nom que le service dans le `.proto` fichier, puis une classe de base avec le suffixe `Base` à l’intérieur de cette classe statique. ainsi, l’identificateur complet du `TraderSys.Portfolios.Protos.Portfolios.PortfoliosBase`type de base est.

```csharp
namespace TraderSys.Portfolios.Services
{
    public class PortfolioService : Protos.Portfolios.PortfoliosBase
    {
    }
}
```

La classe de base déclare `virtual` des méthodes `Get` pour `GetAll` et qui peuvent être substituées pour implémenter le service. Les méthodes sont `virtual` `abstract` plutôt que si vous ne les implémentez pas, le service peut retourner un code d' `Unimplemented` État gRPC explicite, comme vous pouvez lever une `NotImplementedException` dans du C# code normal.

La signature de toutes les méthodes de service unaires gRPC dans ASP.NET Core est cohérente. Il existe deux paramètres : le premier est le type de message déclaré dans `.proto` le fichier, et le second est `ServerCallContext` un qui fonctionne de la même `HttpContext` façon que le de ASP.net core. En fait, il existe une méthode d’extension `GetHttpContext` appelée sur `ServerCallContext` la classe que vous pouvez utiliser pour accéder au `HttpContext`sous-jacent, même si vous n’avez pas besoin de l’utiliser souvent. Nous examinerons `ServerCallContext` plus loin dans ce chapitre et également dans le chapitre traitant de l’authentification.

Le type de retour de la méthode `Task<T>` est `T` un où est le type de message de réponse. Toutes les méthodes de service gRPC sont asynchrones.

## <a name="migrate-the-portfoliodata-library-to-net-core"></a>Migrer la bibliothèque PortfolioData vers .NET Core

À ce stade, le projet a besoin du référentiel de portefeuille et des modèles contenus dans `TraderSys.PortfolioData` la bibliothèque de classes de la solution WCF. Le moyen le plus simple de les placer consiste à créer une bibliothèque de classes à l’aide de la boîte de dialogue **nouveau projet** de Visual Studio avec le modèle *bibliothèque de classes (.NET standard)* , ou à partir de la ligne de commande à l’aide de l’CLI .net Core, en exécutant les commandes suivantes : à partir du répertoire contenant `TraderSys.sln` le fichier.

```dotnetcli
dotnet new classlib -o src/TraderSys.PortfolioData
dotnet sln add src/TraderSys.PortfolioData
```

Une fois la bibliothèque créée et ajoutée à la solution, supprimez le fichier `Class1.cs` généré et copiez les fichiers de la bibliothèque de la solution WCF dans le dossier de la nouvelle bibliothèque de classes, en conservant la structure des dossiers.

```
Models
  Portfolio.cs
  PortfolioItem.cs
IPortfolioRepository.cs
PortfolioRepository.cs
```

Les fichiers de projet .net modernes incluent `.cs` automatiquement tous les fichiers dans ou sous leur propre répertoire. il n’est donc pas nécessaire de les ajouter explicitement au projet. La seule étape restante consiste à `DataContract` supprimer `DataMember` les attributs et `Portfolio` des `PortfolioItem` classes et afin qu’ils soient C# des classes anciennes.

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

Vous pouvez maintenant ajouter une référence à cette bibliothèque au projet d’application gRPC et utiliser la `PortfolioRepository` classe à l’aide de l’injection de dépendances dans l’implémentation du service gRPC. Dans l’application WCF, l’injection de dépendances a été fournie par le conteneur IoC Autofac. ASP.NET Core a une injection de dépendances intégrée ; le référentiel peut être enregistré dans la `ConfigureServices` méthode de la `Startup` classe.

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

L' `IPortfolioRepository` implémentation peut maintenant être spécifiée en tant que paramètre de constructeur `PortfolioService` dans la classe, comme suit :

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

Maintenant que vous avez déclaré vos messages et votre service dans le `portfolios.proto` fichier, vous devez implémenter les méthodes de service dans `PortfolioService` la classe qui hérite de la classe générée `Portfolios.PortfoliosBase` par gRPC. Les méthodes sont déclarées `virtual` comme dans la classe de base. Si vous ne les remplacez pas, ils retournent un code d’État gRPC « non implémenté » par défaut.

Commencez par implémenter `Get` la méthode. La substitution par défaut se présente comme dans l’exemple suivant :

```csharp
public override Task<GetResponse> Get(GetRequest request, ServerCallContext context)
{
    return base.Get(request, context);
}
```

Le premier problème est qu' `request.TraderId` il s’agit d’une chaîne, et le `Guid`service requiert un. Bien que le format attendu pour la chaîne soit un `UUID`, le code doit gérer la possibilité qu’un appelant ait envoyé une valeur non valide et réponde de manière appropriée. Le service peut répondre avec des erreurs en levant `RpcException`un et utiliser le code `InvalidArgument` d’état standard pour exprimer le problème.

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

Une fois que la valeur `Guid` est correcte `traderId`pour, le référentiel peut être utilisé pour récupérer le portefeuille et le renvoyer au client.

```csharp
    var response = new GetResponse
    {
        Portfolio = await _repository.GetAsync(request.TraderId, request.PortfolioId)
    };
```

### <a name="map-internal-models-to-grpc-messages"></a>Mapper les modèles internes aux messages gRPC

Le code précédent ne fonctionne pas réellement, car le référentiel retourne son propre modèle `Portfolio`poco, mais gRPC a besoin de *son* propre message `Portfolio`Protobuf. À l’instar du mappage des types de Entity Framework aux types de transfert de données, la meilleure solution consiste à fournir une conversion entre les deux. Pour ce faire, il convient de placer le code dans la classe générée par Protobuf, qui est déclarée en `partial` tant que classe afin de pouvoir être étendue.

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
> Vous pouvez utiliser une bibliothèque comme [AutoMapper](https://automapper.org/) pour gérer cette conversion des classes de modèle internes en types Protobuf, à condition de `string` configurer les conversions / `Guid` de type de niveau inférieur comme ou `decimal` /et le mappage de liste. `double`

Une fois le code de conversion en place `Get` , l’implémentation de la méthode peut être terminée.

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

L’implémentation de la `GetAll` méthode est similaire. Notez que les `repeated` champs des messages Protobuf sont générés `readonly` en tant que `RepeatedField<T>`propriétés de type. vous devez donc leur ajouter des éléments `AddRange` à l’aide de la méthode, comme dans l’exemple suivant :

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

Créez une bibliothèque de classes .NET Standard dans la même solution pour contenir le client. Il s’agit principalement d’un exemple de création de code client, mais vous pouvez empaqueter une telle bibliothèque à l’aide de NuGet et la distribuer sur un référentiel interne pour que d’autres équipes .NET puissent les utiliser. Continuez et ajoutez une nouvelle bibliothèque de classes .NET standard appelée `TraderSys.Portfolios.Client` à la solution et supprimez `Class1.cs` le fichier.

> [!CAUTION]
> Le package NuGet [.net. client GRPC](https://www.nuget.org/packages/Grpc.Net.Client) nécessite .net Core 3,0 (ou un .NET standard autre Runtime conforme à 2,1). Les versions antérieures de .NET Framework et .NET Core sont prises en charge par le package NuGet [GRPC. Core](https://www.nuget.org/packages/Grpc.Core) .

Dans Visual Studio 2019, vous pouvez ajouter des références aux services gRPC de la même façon que vous ajoutez des références de service aux projets WCF dans les versions antérieures de Visual Studio. Les références de service et les services connectés sont tous gérés sous la même interface utilisateur maintenant, auxquels vous pouvez accéder en cliquant avec le bouton `TraderSys.Portfolios.Client` droit sur le nœud **dépendances** dans le projet dans Explorateur de solutions et en sélectionnant **Ajouter un service connecté**. Dans la fenêtre outil qui s’affiche, sélectionnez la section **références de service** , puis cliquez sur **Ajouter une nouvelle référence de service gRPC**.

![Interface utilisateur Services connectés dans Visual Studio 2019](media/migrate-request-reply/add-connected-service.png)

Accédez au `portfolios.proto` fichier dans le `TraderSys.Portfolios` projet, laissez le **type de classe à générer** comme **client**, puis cliquez sur **OK**.

![Boîte de dialogue Ajouter une nouvelle référence de service gRPC dans Visual Studio 2019](media/migrate-request-reply/add-new-grpc-service-reference.png)

> [!TIP]
> Notez que cette boîte de dialogue fournit également un champ d’URL. Si votre organisation gère un répertoire Web de fichiers, `.proto` vous pouvez créer des clients simplement en définissant cette adresse URL.

Lorsque vous utilisez la fonctionnalité **Ajouter un service connecté** de Visual `portfolios.proto` Studio, le fichier est ajouté au projet de bibliothèque de classes en tant que *fichier lié*, au lieu d’être copié, si bien que les modifications apportées au fichier dans le projet de service sont automatiquement appliquées dans le projet client. L' `<Protobuf>` élément dans le `csproj` fichier se présente comme suit :

```xml
<Protobuf Include="..\TraderSys.Portfolios\Protos\portfolios.proto" GrpcServices="Client">
  <Link>Protos\portfolios.proto</Link>
</Protobuf>
```

### <a name="use-the-portfolios-service-from-a-client-application"></a>Utiliser le service portefeuilles à partir d’une application cliente

Le code suivant est un bref exemple d’utilisation du client généré dans une application console. Une exploration plus détaillée du code client gRPC est à la fin de ce chapitre.

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

À présent, vous avez migré une application WCF de base vers un service ASP.NET Core gRPC et créé un client pour consommer le service à partir d’une application .NET. La section suivante couvre les services « duplex » plus impliqués.

>[!div class="step-by-step"]
>[Précédent](create-project.md)
>[Suivant](migrate-duplex-services.md)
