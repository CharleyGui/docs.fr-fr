---
title: Migrer un service de demande-réponse WCF vers gRPC-gRPC pour les développeurs WCF
description: Découvrez comment migrer un service de requête-réponse simple de WCF vers gRPC.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 12e042e8e7e3683cc4da1fedce2482e7199b04a7
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846610"
---
# <a name="migrate-a-wcf-request-reply-service-to-a-grpc-unary-rpc"></a><span data-ttu-id="2e3b3-103">Migrer un service de requête-réponse WCF vers un RPC unaire gRPC</span><span class="sxs-lookup"><span data-stu-id="2e3b3-103">Migrate a WCF request-reply service to a gRPC unary RPC</span></span>

<span data-ttu-id="2e3b3-104">Cette section explique comment migrer un service de requête-réponse de base dans WCF vers un service RPC unaire dans ASP.NET Core gRPC.</span><span class="sxs-lookup"><span data-stu-id="2e3b3-104">This section covers how to migrate a basic request-reply service in WCF to a unary RPC service in ASP.NET Core gRPC.</span></span> <span data-ttu-id="2e3b3-105">Ces services sont les types de service les plus simples dans Windows Communication Foundation (WCF) et gRPC. il s’agit donc d’un excellent point de départ.</span><span class="sxs-lookup"><span data-stu-id="2e3b3-105">These services are the simplest service types in both Windows Communication Foundation (WCF) and gRPC, so it's an excellent place to start.</span></span> <span data-ttu-id="2e3b3-106">Après la migration du service, vous apprendrez à générer une bibliothèque cliente à partir du même fichier de `.proto` pour utiliser le service à partir d’une application cliente .NET.</span><span class="sxs-lookup"><span data-stu-id="2e3b3-106">After migrating the service, you'll learn how to generate a client library from the same `.proto` file to consume the service from a .NET client application.</span></span>

## <a name="the-wcf-solution"></a><span data-ttu-id="2e3b3-107">La solution WCF</span><span class="sxs-lookup"><span data-stu-id="2e3b3-107">The WCF solution</span></span>

<span data-ttu-id="2e3b3-108">La [solution PortfoliosSample](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/PortfoliosSample/wcf/TraderSys) comprend un service de portefeuille demande-réponse simple pour télécharger un seul portefeuille, ou tous les portefeuilles pour un commerçant donné.</span><span class="sxs-lookup"><span data-stu-id="2e3b3-108">The [PortfoliosSample solution](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/PortfoliosSample/wcf/TraderSys) includes a simple Request-Reply Portfolio service to download a single portfolio, or all portfolios for a given Trader.</span></span> <span data-ttu-id="2e3b3-109">Le service est défini dans l’interface `IPortfolioService` avec un attribut `ServiceContract` :</span><span class="sxs-lookup"><span data-stu-id="2e3b3-109">The service is defined in the interface `IPortfolioService` with a `ServiceContract` attribute:</span></span>

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

<span data-ttu-id="2e3b3-110">Le modèle de `Portfolio` est une C# classe simple marquée avec [DataContract](xref:System.Runtime.Serialization.DataContractAttribute), y compris une liste d’objets `PortfolioItem`.</span><span class="sxs-lookup"><span data-stu-id="2e3b3-110">The `Portfolio` model is a simple C# class marked with [DataContract](xref:System.Runtime.Serialization.DataContractAttribute), including a list of `PortfolioItem` objects.</span></span> <span data-ttu-id="2e3b3-111">Ces modèles sont définis dans le projet `TraderSys.PortfolioData`, ainsi qu’une classe de référentiel représentant une abstraction d’accès aux données.</span><span class="sxs-lookup"><span data-stu-id="2e3b3-111">These models are defined in the `TraderSys.PortfolioData` project, along with a repository class representing a data access abstraction.</span></span>

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

<span data-ttu-id="2e3b3-112">L’implémentation de `ServiceContract` utilise une classe de référentiel fournie via l’injection de dépendances qui retourne des instances des types de `DataContract`.</span><span class="sxs-lookup"><span data-stu-id="2e3b3-112">The `ServiceContract` implementation uses a repository class provided via dependency injection that returns instances of the `DataContract` types.</span></span>

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

## <a name="the-portfoliosproto-file"></a><span data-ttu-id="2e3b3-113">Le fichier portefeuilles. proto</span><span class="sxs-lookup"><span data-stu-id="2e3b3-113">The portfolios.proto file</span></span>

<span data-ttu-id="2e3b3-114">Si vous avez suivi les instructions de la section précédente, vous devez avoir un projet gRPC avec un fichier `portfolios.proto` qui ressemble à ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="2e3b3-114">If you followed the instructions in the previous section, you should have a gRPC project with a `portfolios.proto` file that looks like this.</span></span>

```protobuf
syntax = "proto3";

option csharp_namespace = "TraderSys.Portfolios.Protos";

package PortfolioServer;

service Portfolios {
  // RPCs will go here
}
```

<span data-ttu-id="2e3b3-115">La première étape consiste à migrer les classes `DataContract` vers leurs équivalents Protobuf.</span><span class="sxs-lookup"><span data-stu-id="2e3b3-115">The first step is to migrate the `DataContract` classes to their Protobuf equivalents.</span></span>

## <a name="convert-the-datacontracts-to-grpc-messages"></a><span data-ttu-id="2e3b3-116">Convertir le DataContracts en messages gRPC</span><span class="sxs-lookup"><span data-stu-id="2e3b3-116">Convert the DataContracts to gRPC messages</span></span>

<span data-ttu-id="2e3b3-117">La classe `PortfolioItem` sera d’abord convertie en message Protobuf, car la classe `Portfolio` en dépend.</span><span class="sxs-lookup"><span data-stu-id="2e3b3-117">The `PortfolioItem` class will be converted to a Protobuf message first, as the `Portfolio` class depends on it.</span></span> <span data-ttu-id="2e3b3-118">La classe est très simple, et trois des propriétés sont mappées directement aux types de données gRPC.</span><span class="sxs-lookup"><span data-stu-id="2e3b3-118">The class is very simple, and three of the properties map directly to gRPC data types.</span></span> <span data-ttu-id="2e3b3-119">La propriété `Cost`, qui représente le prix payé pour les partages à l’achat, est un champ `decimal` et gRPC prend uniquement en charge les `float` ou `double` pour les nombres réels, ce qui n’est pas adapté à la devise.</span><span class="sxs-lookup"><span data-stu-id="2e3b3-119">The `Cost` property, representing the price paid for the shares at purchase, is a `decimal` field, and gRPC only supports `float` or `double` for real numbers, which aren't suitable for currency.</span></span> <span data-ttu-id="2e3b3-120">Étant donné que les prix de partage varient d’un cent au minimum, le coût peut être exprimé sous la forme d’un `int32` de centimes.</span><span class="sxs-lookup"><span data-stu-id="2e3b3-120">Since share prices vary by a minimum of one cent, the cost can be expressed as an `int32` of cents.</span></span>

> [!NOTE]
> <span data-ttu-id="2e3b3-121">N’oubliez pas d’utiliser `camelCase` pour les noms de champ dans votre fichier `.proto` ; le C# générateur de code les convertira en `PascalCase` pour vous, et les utilisateurs d’autres langages vous remercient de respecter leurs différentes normes de codage.</span><span class="sxs-lookup"><span data-stu-id="2e3b3-121">Remember to use `camelCase` for field names in your `.proto` file; the C# code generator will convert them to `PascalCase` for you, and users of other languages will thank you for respecting their different coding standards.</span></span>

```protobuf
message PortfolioItem {
    int32 id = 1;
    int32 share_id = 2;
    int32 holding = 3;
    int32 cost_cents = 4;
}
```

<span data-ttu-id="2e3b3-122">La classe `Portfolio` est un peu plus compliquée.</span><span class="sxs-lookup"><span data-stu-id="2e3b3-122">The `Portfolio` class is a little more complicated.</span></span> <span data-ttu-id="2e3b3-123">Dans le code WCF, le développeur a utilisé une `Guid` pour la propriété `TraderId` et contient un `List<PortfolioItem>`.</span><span class="sxs-lookup"><span data-stu-id="2e3b3-123">In the WCF code, the developer used a `Guid` for the `TraderId` property, and contains a `List<PortfolioItem>`.</span></span> <span data-ttu-id="2e3b3-124">Dans Protobuf, qui n’a pas de type de `UUID` de première classe, vous devez utiliser une `string` pour le champ `traderId` et l’analyser dans votre propre code.</span><span class="sxs-lookup"><span data-stu-id="2e3b3-124">In Protobuf, which doesn't have a first-class `UUID` type, you should use a `string` for the `traderId` field and parse it in your own code.</span></span> <span data-ttu-id="2e3b3-125">Pour la liste des éléments, utilisez le mot clé `repeated` sur le champ.</span><span class="sxs-lookup"><span data-stu-id="2e3b3-125">For the list of items, use the `repeated` keyword on the field.</span></span>

```protobuf
message Portfolio {
    int32 id = 1;
    string trader_id = 2;
    repeated PortfolioItem items = 3;
}
```

<span data-ttu-id="2e3b3-126">Maintenant que nous avons nos messages de données, nous pouvons déclarer les points de terminaison RPC du service.</span><span class="sxs-lookup"><span data-stu-id="2e3b3-126">Now we have our data messages, we can declare the service RPC endpoints.</span></span>

## <a name="convert-the-servicecontract-to-a-grpc-service"></a><span data-ttu-id="2e3b3-127">Convertir le ServiceContract en service gRPC</span><span class="sxs-lookup"><span data-stu-id="2e3b3-127">Convert the ServiceContract to a gRPC service</span></span>

<span data-ttu-id="2e3b3-128">La méthode de `Get` WCF accepte deux paramètres : `Guid traderId` et `int portfolioId`.</span><span class="sxs-lookup"><span data-stu-id="2e3b3-128">The WCF `Get` method takes two parameters: `Guid traderId` and `int portfolioId`.</span></span> <span data-ttu-id="2e3b3-129">les méthodes de service gRPC peuvent uniquement accepter un seul paramètre, de sorte qu’un message doit être créé pour contenir les deux valeurs.</span><span class="sxs-lookup"><span data-stu-id="2e3b3-129">gRPC service methods can only take a single parameter, so a message must be created to hold the two values.</span></span> <span data-ttu-id="2e3b3-130">Il est courant de nommer ces objets de requête avec le même nom que la méthode et le suffixe `Request`.</span><span class="sxs-lookup"><span data-stu-id="2e3b3-130">It's common practice to name these request objects with the same name as the method and the suffix `Request`.</span></span> <span data-ttu-id="2e3b3-131">Là encore, `string` est utilisé pour le champ `traderId` au lieu de `Guid`.</span><span class="sxs-lookup"><span data-stu-id="2e3b3-131">Again, `string` is being used for the `traderId` field instead of `Guid`.</span></span>

<span data-ttu-id="2e3b3-132">Le service peut simplement retourner un message `Portfolio`, mais là encore, cela peut avoir un impact sur la compatibilité descendante à l’avenir.</span><span class="sxs-lookup"><span data-stu-id="2e3b3-132">The service could just return a `Portfolio` message directly, but again, this could impact backward compatibility in the future.</span></span> <span data-ttu-id="2e3b3-133">Nous vous conseillons de définir des `Request` et des messages `Response` distincts pour chaque méthode dans un service, même si beaucoup d’entre eux sont identiques pour l’instant, déclarez un message `GetResponse` avec un seul champ de `Portfolio`.</span><span class="sxs-lookup"><span data-stu-id="2e3b3-133">It's a good practice to define separate `Request` and `Response` messages for every method in a service, even if many of them are the same right now, so declare a `GetResponse` message with a single `Portfolio` field.</span></span>

<span data-ttu-id="2e3b3-134">L’exemple suivant illustre la déclaration de la méthode de service gRPC à l’aide du message `GetRequest` :</span><span class="sxs-lookup"><span data-stu-id="2e3b3-134">The following example shows the declaration of the gRPC service method using the `GetRequest` message:</span></span>

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

<span data-ttu-id="2e3b3-135">La méthode de `GetAll` WCF n’accepte qu’un seul paramètre, `traderId`. il est donc possible que vous puissiez spécifier `string` comme type de paramètre, mais gRPC nécessite un type de message défini.</span><span class="sxs-lookup"><span data-stu-id="2e3b3-135">The WCF `GetAll` method only takes a single parameter, `traderId`, so it might seem that one could specify `string` as the parameter type, but gRPC requires a defined message type.</span></span> <span data-ttu-id="2e3b3-136">Cette exigence permet de mettre en œuvre la pratique consistant à utiliser des messages personnalisés pour toutes les entrées et sorties, en vue d’une compatibilité descendante future.</span><span class="sxs-lookup"><span data-stu-id="2e3b3-136">This requirement helps to enforce the practice of using custom messages for all inputs and outputs, for future backward compatibility.</span></span>

<span data-ttu-id="2e3b3-137">La méthode WCF a également retourné une `List<Portfolio>`, mais pour la même raison, elle n’autorise pas les types de paramètres simples, gRPC n’autorise pas `repeated Portfolio` comme type de retour.</span><span class="sxs-lookup"><span data-stu-id="2e3b3-137">The WCF method also returned a `List<Portfolio>`, but for the same reason it doesn't allow simple parameter types, gRPC won't allow `repeated Portfolio` as a return type.</span></span> <span data-ttu-id="2e3b3-138">Au lieu de cela, créez un type de `GetAllResponse` pour encapsuler la liste.</span><span class="sxs-lookup"><span data-stu-id="2e3b3-138">Instead, create a `GetAllResponse` type to wrap the list.</span></span>

> [!WARNING]
> <span data-ttu-id="2e3b3-139">Vous pouvez être tenté de créer un `PortfolioList` message ou similaire et de l’utiliser dans plusieurs méthodes de service, mais vous devez résister à cette tentation.</span><span class="sxs-lookup"><span data-stu-id="2e3b3-139">You may be tempted to create a `PortfolioList` message or similar and use it across multiple service methods, but you should resist this temptation.</span></span> <span data-ttu-id="2e3b3-140">Il est impossible de savoir comment les différentes méthodes d’un service peuvent évoluer à l’avenir, afin de conserver les messages spécifiques et séparés.</span><span class="sxs-lookup"><span data-stu-id="2e3b3-140">It's impossible to know how the various methods on a service may evolve in the future, so keep their messages specific and cleanly separated.</span></span>

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

<span data-ttu-id="2e3b3-141">Si vous enregistrez votre projet avec ces modifications, la cible de génération gRPC s’exécute en arrière-plan et génère tous les types de messages Protobuf et une classe de base que vous pouvez hériter pour implémenter le service.</span><span class="sxs-lookup"><span data-stu-id="2e3b3-141">If you save your project with these changes, the gRPC build target will run in the background and generate all the Protobuf message types and a base class you can inherit to implement the service.</span></span>

<span data-ttu-id="2e3b3-142">Ouvrez la classe `Services/GreeterService.cs` et supprimez l’exemple de code.</span><span class="sxs-lookup"><span data-stu-id="2e3b3-142">Open up the `Services/GreeterService.cs` class and delete the example code.</span></span> <span data-ttu-id="2e3b3-143">Vous pouvez maintenant ajouter l’implémentation du service de portefeuille.</span><span class="sxs-lookup"><span data-stu-id="2e3b3-143">Now you can add the Portfolio service implementation.</span></span> <span data-ttu-id="2e3b3-144">La classe de base générée se trouve dans l’espace de noms `Protos` et est générée comme une classe imbriquée.</span><span class="sxs-lookup"><span data-stu-id="2e3b3-144">The generated base class will be in the `Protos` namespace and is generated as a nested class.</span></span> <span data-ttu-id="2e3b3-145">gRPC crée une classe statique portant le même nom que le service dans le fichier `.proto`, puis une classe de base avec le suffixe `Base` à l’intérieur de cette classe statique, de sorte que l’identificateur complet du type de base est `TraderSys.Portfolios.Protos.Portfolios.PortfoliosBase`.</span><span class="sxs-lookup"><span data-stu-id="2e3b3-145">gRPC creates a static class with the same name as the service in the `.proto` file, and then a base class with the suffix `Base` inside that static class, so the full identifier for the base type is `TraderSys.Portfolios.Protos.Portfolios.PortfoliosBase`.</span></span>

```csharp
namespace TraderSys.Portfolios.Services
{
    public class PortfolioService : Protos.Portfolios.PortfoliosBase
    {
    }
}
```

<span data-ttu-id="2e3b3-146">La classe de base déclare `virtual` méthodes pour `Get` et `GetAll` qui peuvent être substituées pour implémenter le service.</span><span class="sxs-lookup"><span data-stu-id="2e3b3-146">The base class declares `virtual` methods for `Get` and `GetAll` that can be overridden to implement the service.</span></span> <span data-ttu-id="2e3b3-147">Les méthodes sont `virtual` plutôt que `abstract`. ainsi, si vous ne les implémentez pas, le service peut retourner un code d’État `Unimplemented` gRPC explicite, comme vous pouvez lever une C# `NotImplementedException` dans du code normal.</span><span class="sxs-lookup"><span data-stu-id="2e3b3-147">The methods are `virtual` rather than `abstract` so that if you don't implement them, the service can return an explicit gRPC `Unimplemented` status code, much like you might throw a `NotImplementedException` in regular C# code.</span></span>

<span data-ttu-id="2e3b3-148">La signature de toutes les méthodes de service unaires gRPC dans ASP.NET Core est cohérente.</span><span class="sxs-lookup"><span data-stu-id="2e3b3-148">The signature for all gRPC unary service methods in ASP.NET Core is consistent.</span></span> <span data-ttu-id="2e3b3-149">Il y a deux paramètres : le premier est le type de message déclaré dans le fichier `.proto`, tandis que le second est un `ServerCallContext` qui fonctionne de la même façon que le `HttpContext` de ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="2e3b3-149">There are two parameters: the first is the message type declared in the `.proto` file, and the second is a `ServerCallContext` that works similarly to the `HttpContext` from ASP.NET Core.</span></span> <span data-ttu-id="2e3b3-150">En fait, il existe une méthode d’extension appelée `GetHttpContext` sur la classe `ServerCallContext` que vous pouvez utiliser pour récupérer les `HttpContext` sous-jacentes, bien que vous n’ayez pas besoin de l’utiliser souvent.</span><span class="sxs-lookup"><span data-stu-id="2e3b3-150">In fact, there's an extension method called `GetHttpContext` on the `ServerCallContext` class that you can use to get the underlying `HttpContext`, although you shouldn't need to use it often.</span></span> <span data-ttu-id="2e3b3-151">Nous examinerons `ServerCallContext` plus loin dans ce chapitre et également dans le chapitre traitant de l’authentification.</span><span class="sxs-lookup"><span data-stu-id="2e3b3-151">We'll take a look at `ServerCallContext` later in this chapter, and also in the chapter that discusses authentication.</span></span>

<span data-ttu-id="2e3b3-152">Le type de retour de la méthode est un `Task<T>` où `T` est le type de message de réponse.</span><span class="sxs-lookup"><span data-stu-id="2e3b3-152">The method's return type is a `Task<T>` where `T` is the response message type.</span></span> <span data-ttu-id="2e3b3-153">Toutes les méthodes de service gRPC sont asynchrones.</span><span class="sxs-lookup"><span data-stu-id="2e3b3-153">All gRPC service methods are asynchronous.</span></span>

## <a name="migrate-the-portfoliodata-library-to-net-core"></a><span data-ttu-id="2e3b3-154">Migrer la bibliothèque PortfolioData vers .NET Core</span><span class="sxs-lookup"><span data-stu-id="2e3b3-154">Migrate the PortfolioData library to .NET Core</span></span>

<span data-ttu-id="2e3b3-155">À ce stade, le projet a besoin du référentiel de portefeuille et des modèles contenus dans la bibliothèque de classes `TraderSys.PortfolioData` de la solution WCF.</span><span class="sxs-lookup"><span data-stu-id="2e3b3-155">At this point, the project needs the Portfolio repository and models contained in the `TraderSys.PortfolioData` class library in the WCF solution.</span></span> <span data-ttu-id="2e3b3-156">Le moyen le plus simple de les placer consiste à créer une bibliothèque de classes à l’aide de la boîte de dialogue **nouveau projet** de Visual Studio avec le modèle *bibliothèque de classes (.NET standard)* , ou à partir de la ligne de commande à l’aide de l’CLI .net Core, en exécutant les commandes suivantes : à partir du répertoire contenant le fichier `TraderSys.sln`.</span><span class="sxs-lookup"><span data-stu-id="2e3b3-156">The easiest way to bring them across is to create a new class library using either the Visual Studio **New project** dialog with the *Class Library (.NET Standard)* template, or from the command line using the .NET Core CLI, running the following commands from the directory containing the `TraderSys.sln` file.</span></span>

```dotnetcli
dotnet new classlib -o src/TraderSys.PortfolioData
dotnet sln add src/TraderSys.PortfolioData
```

<span data-ttu-id="2e3b3-157">Une fois la bibliothèque créée et ajoutée à la solution, supprimez le fichier de `Class1.cs` généré et copiez les fichiers de la bibliothèque de la solution WCF dans le dossier de la nouvelle bibliothèque de classes, en conservant la structure des dossiers.</span><span class="sxs-lookup"><span data-stu-id="2e3b3-157">Once the library has been created and added to the solution, delete the generated `Class1.cs` file and copy the files from the WCF solution's library into the new class library's folder, keeping the folder structure.</span></span>

```
Models
  Portfolio.cs
  PortfolioItem.cs
IPortfolioRepository.cs
PortfolioRepository.cs
```

<span data-ttu-id="2e3b3-158">Les projets .NET de type SDK incluent automatiquement tous les fichiers de `.cs` dans ou sous leur propre répertoire. il n’est donc pas nécessaire de les ajouter explicitement au projet.</span><span class="sxs-lookup"><span data-stu-id="2e3b3-158">SDK-style .NET projects automatically include any `.cs` files in or under their own directory, so there's no need to explicitly add them to the project.</span></span> <span data-ttu-id="2e3b3-159">La seule étape restante consiste à supprimer les attributs `DataContract` et `DataMember` des classes `Portfolio` et `PortfolioItem` afin qu’elles soient C# de simples classes.</span><span class="sxs-lookup"><span data-stu-id="2e3b3-159">The only step remaining is to remove the `DataContract` and `DataMember` attributes from the `Portfolio` and `PortfolioItem` classes so they're plain old C# classes.</span></span>

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

## <a name="use-aspnet-core-dependency-injection"></a><span data-ttu-id="2e3b3-160">Utiliser ASP.NET Core l’injection de dépendances</span><span class="sxs-lookup"><span data-stu-id="2e3b3-160">Use ASP.NET Core dependency injection</span></span>

<span data-ttu-id="2e3b3-161">Vous pouvez maintenant ajouter une référence à cette bibliothèque au projet d’application gRPC et utiliser la classe `PortfolioRepository` à l’aide de l’injection de dépendances dans l’implémentation du service gRPC.</span><span class="sxs-lookup"><span data-stu-id="2e3b3-161">Now you can add a reference to this library to the gRPC application project and consume the `PortfolioRepository` class using dependency injection in the gRPC service implementation.</span></span> <span data-ttu-id="2e3b3-162">Dans l’application WCF, l’injection de dépendances a été fournie par le conteneur IoC Autofac.</span><span class="sxs-lookup"><span data-stu-id="2e3b3-162">In the WCF application, dependency injection was provided by the Autofac IoC container.</span></span> <span data-ttu-id="2e3b3-163">ASP.NET Core a une injection de dépendances intégrée ; le référentiel peut être enregistré dans la méthode `ConfigureServices` de la classe `Startup`.</span><span class="sxs-lookup"><span data-stu-id="2e3b3-163">ASP.NET Core has dependency injection baked in; the repository can be registered in the `ConfigureServices` method in the `Startup` class.</span></span>

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

<span data-ttu-id="2e3b3-164">L’implémentation de `IPortfolioRepository` peut maintenant être spécifiée en tant que paramètre de constructeur dans la classe `PortfolioService`, comme suit :</span><span class="sxs-lookup"><span data-stu-id="2e3b3-164">The `IPortfolioRepository` implementation can now be specified as a constructor parameter in the `PortfolioService` class, as follows:</span></span>

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

## <a name="implement-the-grpc-service"></a><span data-ttu-id="2e3b3-165">Implémenter le service gRPC</span><span class="sxs-lookup"><span data-stu-id="2e3b3-165">Implement the gRPC service</span></span>

<span data-ttu-id="2e3b3-166">Maintenant que vous avez déclaré vos messages et votre service dans le fichier `portfolios.proto`, vous devez implémenter les méthodes de service dans la classe `PortfolioService` qui hérite de la classe `Portfolios.PortfoliosBase` générée par gRPC.</span><span class="sxs-lookup"><span data-stu-id="2e3b3-166">Now that you've declared your messages and your service in the `portfolios.proto` file, you have to implement the service methods in the `PortfolioService` class that inherits from the gRPC-generated `Portfolios.PortfoliosBase` class.</span></span> <span data-ttu-id="2e3b3-167">Les méthodes sont déclarées en tant que `virtual` dans la classe de base.</span><span class="sxs-lookup"><span data-stu-id="2e3b3-167">The methods are declared as `virtual` in the base class.</span></span> <span data-ttu-id="2e3b3-168">Si vous ne les remplacez pas, ils retournent un code d’État gRPC « non implémenté » par défaut.</span><span class="sxs-lookup"><span data-stu-id="2e3b3-168">If you don't override them, they'll return a gRPC "Not Implemented" status code by default.</span></span>

<span data-ttu-id="2e3b3-169">Commencez par implémenter la méthode `Get`.</span><span class="sxs-lookup"><span data-stu-id="2e3b3-169">Start by implementing the `Get` method.</span></span> <span data-ttu-id="2e3b3-170">La substitution par défaut se présente comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="2e3b3-170">The default override looks like the following example:</span></span>

```csharp
public override Task<GetResponse> Get(GetRequest request, ServerCallContext context)
{
    return base.Get(request, context);
}
```

<span data-ttu-id="2e3b3-171">Le premier problème est que `request.TraderId` est une chaîne et que le service requiert un `Guid`.</span><span class="sxs-lookup"><span data-stu-id="2e3b3-171">The first issue is that `request.TraderId` is a string, and the service requires a `Guid`.</span></span> <span data-ttu-id="2e3b3-172">Bien que le format attendu pour la chaîne soit un `UUID`, le code doit gérer la possibilité qu’un appelant ait envoyé une valeur non valide et réponde de manière appropriée.</span><span class="sxs-lookup"><span data-stu-id="2e3b3-172">Even though the expected format for the string is a `UUID`, the code has to deal with the possibility that a caller has sent an invalid value and respond appropriately.</span></span> <span data-ttu-id="2e3b3-173">Le service peut répondre avec des erreurs en levant une `RpcException` et utiliser le code d’État `InvalidArgument` standard pour exprimer le problème.</span><span class="sxs-lookup"><span data-stu-id="2e3b3-173">The service can respond with errors by throwing an `RpcException`, and use the standard `InvalidArgument` status code to express the problem.</span></span>

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

<span data-ttu-id="2e3b3-174">Une fois qu’il y a une valeur de `Guid` correcte pour `traderId`, le référentiel peut être utilisé pour récupérer le portefeuille et le renvoyer au client.</span><span class="sxs-lookup"><span data-stu-id="2e3b3-174">Once there's a proper `Guid` value for `traderId`, the repository can be used to retrieve the Portfolio and return it to the client.</span></span>

```csharp
    var response = new GetResponse
    {
        Portfolio = await _repository.GetAsync(request.TraderId, request.PortfolioId)
    };
```

### <a name="map-internal-models-to-grpc-messages"></a><span data-ttu-id="2e3b3-175">Mapper les modèles internes aux messages gRPC</span><span class="sxs-lookup"><span data-stu-id="2e3b3-175">Map internal models to gRPC messages</span></span>

<span data-ttu-id="2e3b3-176">Le code précédent ne fonctionne pas réellement, car le référentiel retourne son propre modèle POCO `Portfolio`, mais gRPC a besoin de *son* propre `Portfolio` de message Protobuf.</span><span class="sxs-lookup"><span data-stu-id="2e3b3-176">The previous code doesn't actually work because the repository is returning its own POCO model `Portfolio`, but gRPC needs *its* own Protobuf message `Portfolio`.</span></span> <span data-ttu-id="2e3b3-177">À l’instar du mappage des types de Entity Framework aux types de transfert de données, la meilleure solution consiste à fournir une conversion entre les deux.</span><span class="sxs-lookup"><span data-stu-id="2e3b3-177">Much like mapping Entity Framework types to data transfer types, the best solution is to provide conversion between the two.</span></span> <span data-ttu-id="2e3b3-178">Pour ce faire, il convient de placer le code dans la classe générée par Protobuf, qui est déclarée en tant que classe `partial` pour pouvoir être étendue.</span><span class="sxs-lookup"><span data-stu-id="2e3b3-178">A good place to put the code for this is in the Protobuf-generated class, which is declared as a `partial` class so it can be extended.</span></span>

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
> <span data-ttu-id="2e3b3-179">Vous pouvez utiliser une bibliothèque comme [AutoMapper](https://automapper.org/) pour gérer cette conversion des classes de modèle internes en types Protobuf, à condition de configurer les conversions de type de niveau inférieur comme `string` / `Guid` ou `decimal` / `double` et le mappage de liste.</span><span class="sxs-lookup"><span data-stu-id="2e3b3-179">You could use a library like [AutoMapper](https://automapper.org/) to handle this conversion from internal model classes to Protobuf types, as long as you configure the lower-level type conversions like `string`/`Guid` or `decimal`/`double` and the list mapping.</span></span>

<span data-ttu-id="2e3b3-180">Une fois le code de conversion en place, l’implémentation de la méthode `Get` peut être terminée.</span><span class="sxs-lookup"><span data-stu-id="2e3b3-180">With the conversion code in place, the `Get` method implementation can be completed.</span></span>

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

<span data-ttu-id="2e3b3-181">L’implémentation de la méthode `GetAll` est similaire.</span><span class="sxs-lookup"><span data-stu-id="2e3b3-181">The implementation of the `GetAll` method is similar.</span></span> <span data-ttu-id="2e3b3-182">Notez que les champs `repeated` sur les messages Protobuf sont générés comme des propriétés de `readonly` de type `RepeatedField<T>`, donc vous devez leur ajouter des éléments à l’aide de la méthode `AddRange`, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="2e3b3-182">Note that the `repeated` fields on Protobuf messages are generated as `readonly` properties of type `RepeatedField<T>`, so you have to add items to them using the `AddRange` method, like in the following example:</span></span>

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

<span data-ttu-id="2e3b3-183">Après avoir migré le service WCF Request-Reply vers gRPC, nous allons maintenant créer un client à partir du fichier `.proto`.</span><span class="sxs-lookup"><span data-stu-id="2e3b3-183">Having successfully migrated the WCF request-reply service to gRPC, let's look at creating a client for it from the `.proto` file.</span></span>

## <a name="generate-client-code"></a><span data-ttu-id="2e3b3-184">Générer le code client</span><span class="sxs-lookup"><span data-stu-id="2e3b3-184">Generate client code</span></span>

<span data-ttu-id="2e3b3-185">Créez une bibliothèque de classes .NET Standard dans la même solution pour contenir le client.</span><span class="sxs-lookup"><span data-stu-id="2e3b3-185">Create a .NET Standard class library in the same solution to contain the client.</span></span> <span data-ttu-id="2e3b3-186">Il s’agit principalement d’un exemple de création de code client, mais vous pouvez empaqueter une telle bibliothèque à l’aide de NuGet et la distribuer sur un référentiel interne pour que d’autres équipes .NET puissent les utiliser.</span><span class="sxs-lookup"><span data-stu-id="2e3b3-186">This is primarily an example of creating client code, but you could package such a library using NuGet and distribute it on an internal repository for other .NET teams to consume.</span></span> <span data-ttu-id="2e3b3-187">Continuez et ajoutez une nouvelle bibliothèque de classes .NET Standard appelée `TraderSys.Portfolios.Client` à la solution et supprimez le fichier `Class1.cs`.</span><span class="sxs-lookup"><span data-stu-id="2e3b3-187">Go ahead and add a new .NET Standard Class Library called `TraderSys.Portfolios.Client` to the solution and delete the `Class1.cs` file.</span></span>

> [!CAUTION]
> <span data-ttu-id="2e3b3-188">Le package NuGet [.net. client GRPC](https://www.nuget.org/packages/Grpc.Net.Client) nécessite .net Core 3,0 (ou un .NET standard autre Runtime conforme à 2,1).</span><span class="sxs-lookup"><span data-stu-id="2e3b3-188">The [Grpc.Net.Client](https://www.nuget.org/packages/Grpc.Net.Client) NuGet package requires .NET Core 3.0 (or another .NET Standard 2.1-compliant runtime).</span></span> <span data-ttu-id="2e3b3-189">Les versions antérieures de .NET Framework et .NET Core sont prises en charge par le package NuGet [GRPC. Core](https://www.nuget.org/packages/Grpc.Core) .</span><span class="sxs-lookup"><span data-stu-id="2e3b3-189">Earlier versions of .NET Framework and .NET Core are supported by the [Grpc.Core](https://www.nuget.org/packages/Grpc.Core) NuGet package.</span></span>

<span data-ttu-id="2e3b3-190">Dans Visual Studio 2019, vous pouvez ajouter des références aux services gRPC de la même façon que vous ajoutez des références de service aux projets WCF dans les versions antérieures de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2e3b3-190">In Visual Studio 2019, you can add references to gRPC services similar to the way you'd add Service References to WCF projects in earlier versions of Visual Studio.</span></span> <span data-ttu-id="2e3b3-191">Les références de service et les Services connectés sont tous gérés sous la même interface utilisateur maintenant, auxquels vous pouvez accéder en cliquant avec le bouton droit sur le nœud **dépendances** dans le projet `TraderSys.Portfolios.Client` dans Explorateur de solutions et en sélectionnant **Ajouter un service connecté**.</span><span class="sxs-lookup"><span data-stu-id="2e3b3-191">Service References and Connected Services are all managed under the same UI now, which you can access by right-clicking the **Dependencies** node in the `TraderSys.Portfolios.Client` project in Solution Explorer and selecting **Add Connected Service**.</span></span> <span data-ttu-id="2e3b3-192">Dans la fenêtre outil qui s’affiche, sélectionnez la section **références de service** , puis cliquez sur **Ajouter une nouvelle référence de service gRPC**.</span><span class="sxs-lookup"><span data-stu-id="2e3b3-192">In the tool window that appears, select the **Service References** section and click **Add new gRPC service reference**.</span></span>

![Interface utilisateur Services connectés dans Visual Studio 2019](media/migrate-request-reply/add-connected-service.png)

<span data-ttu-id="2e3b3-194">Accédez au fichier `portfolios.proto` dans le projet `TraderSys.Portfolios`, laissez le **type de classe à générer** en tant que **client**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="2e3b3-194">Browse to the `portfolios.proto` file in the `TraderSys.Portfolios` project, leave the **type of class to be generated** as **Client**, and click **OK**.</span></span>

![Boîte de dialogue Ajouter une nouvelle référence de service gRPC dans Visual Studio 2019](media/migrate-request-reply/add-new-grpc-service-reference.png)

> [!TIP]
> <span data-ttu-id="2e3b3-196">Notez que cette boîte de dialogue fournit également un champ d’URL.</span><span class="sxs-lookup"><span data-stu-id="2e3b3-196">Notice that this dialog also provides a URL field.</span></span> <span data-ttu-id="2e3b3-197">Si votre organisation gère un répertoire accessible via le Web de fichiers `.proto`, vous pouvez créer des clients simplement en définissant cette adresse URL.</span><span class="sxs-lookup"><span data-stu-id="2e3b3-197">If your organization maintains a web-accessible directory of `.proto` files, you can create clients just by setting this URL address.</span></span>

<span data-ttu-id="2e3b3-198">Lorsque vous utilisez la fonctionnalité **Ajouter un service connecté** de Visual Studio, le fichier `portfolios.proto` est ajouté au projet de bibliothèque de classes en tant que *fichier lié*, au lieu d’être copié, de sorte que les modifications apportées au fichier dans le projet de service s’appliquent automatiquement au client. projection.</span><span class="sxs-lookup"><span data-stu-id="2e3b3-198">When using the Visual Studio **Add Connected Service** feature, the `portfolios.proto` file is added to the Class Library project as a *linked file*, rather than copied, so changes to the file in the service project will automatically be applied in the client project.</span></span> <span data-ttu-id="2e3b3-199">L’élément `<Protobuf>` dans le fichier `csproj` se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="2e3b3-199">The `<Protobuf>` element in the `csproj` file looks like this:</span></span>

```xml
<Protobuf Include="..\TraderSys.Portfolios\Protos\portfolios.proto" GrpcServices="Client">
  <Link>Protos\portfolios.proto</Link>
</Protobuf>
```

> [!TIP]
> <span data-ttu-id="2e3b3-200">Si vous n’utilisez pas Visual Studio ou si vous préférez travailler à partir de la ligne de commande, vous pouvez utiliser l’outil Global **dotnet-GRPC** pour gérer les références Protobuf dans un projet .net GRPC.</span><span class="sxs-lookup"><span data-stu-id="2e3b3-200">If you are not using Visual Studio or prefer to work from the command line, you can use the **dotnet-grpc** global tool to manage Protobuf references within a .NET gRPC project.</span></span> <span data-ttu-id="2e3b3-201">[Pour plus d’informations, reportez-vous à la documentation **dotnet-GRPC** ](https://docs.microsoft.com/aspnet/core/grpc/dotnet-grpc).</span><span class="sxs-lookup"><span data-stu-id="2e3b3-201">[Refer to the **dotnet-grpc** documentation for more information](https://docs.microsoft.com/aspnet/core/grpc/dotnet-grpc).</span></span>

### <a name="use-the-portfolios-service-from-a-client-application"></a><span data-ttu-id="2e3b3-202">Utiliser le service portefeuilles à partir d’une application cliente</span><span class="sxs-lookup"><span data-stu-id="2e3b3-202">Use the Portfolios service from a client application</span></span>

<span data-ttu-id="2e3b3-203">Le code suivant est un bref exemple d’utilisation du client généré dans une application console.</span><span class="sxs-lookup"><span data-stu-id="2e3b3-203">The following code is a brief example of using the generated client in a console application.</span></span> <span data-ttu-id="2e3b3-204">Une exploration plus détaillée du code client gRPC est à la fin de ce chapitre.</span><span class="sxs-lookup"><span data-stu-id="2e3b3-204">A more detailed exploration of the gRPC client code is at the end of this chapter.</span></span>

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

<span data-ttu-id="2e3b3-205">À présent, vous avez migré une application WCF de base vers un service ASP.NET Core gRPC et créé un client pour consommer le service à partir d’une application .NET.</span><span class="sxs-lookup"><span data-stu-id="2e3b3-205">Now, you've migrated a basic WCF application to an ASP.NET Core gRPC service and created a client to consume the service from a .NET application.</span></span> <span data-ttu-id="2e3b3-206">La section suivante couvre les services « duplex » plus impliqués.</span><span class="sxs-lookup"><span data-stu-id="2e3b3-206">The next section will cover the more involved "duplex" services.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="2e3b3-207">[Précédent](create-project.md)
>[Suivant](migrate-duplex-services.md)</span><span class="sxs-lookup"><span data-stu-id="2e3b3-207">[Previous](create-project.md)
[Next](migrate-duplex-services.md)</span></span>
