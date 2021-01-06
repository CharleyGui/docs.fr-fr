---
title: Migrer un service de demande-réponse WCF vers gRPC-gRPC pour les développeurs WCF
description: Découvrez comment migrer un service de requête-réponse simple de WCF vers gRPC.
ms.date: 12/15/2020
ms.openlocfilehash: 38c6e33e7588dd7c1b263d813d06c088ab484948
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938570"
---
# <a name="migrate-a-wcf-request-reply-service-to-a-grpc-unary-rpc"></a><span data-ttu-id="9f5eb-103">Migrer un service de requête-réponse WCF vers un RPC unaire gRPC</span><span class="sxs-lookup"><span data-stu-id="9f5eb-103">Migrate a WCF request-reply service to a gRPC unary RPC</span></span>

<span data-ttu-id="9f5eb-104">Cette section explique comment migrer un service de requête-réponse de base dans WCF vers un service RPC unaire dans ASP.NET Core gRPC.</span><span class="sxs-lookup"><span data-stu-id="9f5eb-104">This section covers how to migrate a basic request-reply service in WCF to a unary RPC service in ASP.NET Core gRPC.</span></span> <span data-ttu-id="9f5eb-105">Ces services sont les types de service les plus simples dans Windows Communication Foundation (WCF) et gRPC. il s’agit donc d’un excellent point de départ.</span><span class="sxs-lookup"><span data-stu-id="9f5eb-105">These services are the simplest service types in both Windows Communication Foundation (WCF) and gRPC, so it's an excellent place to start.</span></span> <span data-ttu-id="9f5eb-106">Après la migration du service, vous apprendrez à générer une bibliothèque cliente à partir du même `.proto` fichier afin de consommer le service à partir d’une application cliente .net.</span><span class="sxs-lookup"><span data-stu-id="9f5eb-106">After migrating the service, you'll learn how to generate a client library from the same `.proto` file to consume the service from a .NET client application.</span></span>

## <a name="the-wcf-solution"></a><span data-ttu-id="9f5eb-107">La solution WCF</span><span class="sxs-lookup"><span data-stu-id="9f5eb-107">The WCF solution</span></span>

<span data-ttu-id="9f5eb-108">La [solution PortfoliosSample](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/PortfoliosSample/wcf/TraderSys) comprend un service de portefeuille demande-réponse simple pour télécharger un ou plusieurs portefeuilles pour un commerçant donné.</span><span class="sxs-lookup"><span data-stu-id="9f5eb-108">The [PortfoliosSample solution](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/PortfoliosSample/wcf/TraderSys) includes a simple request-reply Portfolio service to download either a single portfolio or all portfolios for a given trader.</span></span> <span data-ttu-id="9f5eb-109">Le service est défini dans l’interface `IPortfolioService` avec un `ServiceContract` attribut :</span><span class="sxs-lookup"><span data-stu-id="9f5eb-109">The service is defined in the interface `IPortfolioService` with a `ServiceContract` attribute:</span></span>

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

<span data-ttu-id="9f5eb-110">Le `Portfolio` modèle est une classe C# simple marquée avec [DataContract](xref:System.Runtime.Serialization.DataContractAttribute) et incluant une liste d' `PortfolioItem` objets.</span><span class="sxs-lookup"><span data-stu-id="9f5eb-110">The `Portfolio` model is a simple C# class marked with [DataContract](xref:System.Runtime.Serialization.DataContractAttribute) and including a list of `PortfolioItem` objects.</span></span> <span data-ttu-id="9f5eb-111">Ces modèles sont définis dans le `TraderSys.PortfolioData` projet avec une classe de référentiel qui représente une abstraction d’accès aux données.</span><span class="sxs-lookup"><span data-stu-id="9f5eb-111">These models are defined in the `TraderSys.PortfolioData` project along with a repository class that represents a data access abstraction.</span></span>

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

<span data-ttu-id="9f5eb-112">L' `ServiceContract` implémentation utilise une classe de référentiel fournie via l’injection de dépendances qui retourne des instances des `DataContract` types :</span><span class="sxs-lookup"><span data-stu-id="9f5eb-112">The `ServiceContract` implementation uses a repository class provided via dependency injection that returns instances of the `DataContract` types:</span></span>

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

## <a name="the-portfoliosproto-file"></a><span data-ttu-id="9f5eb-113">Le fichier portefeuilles. proto</span><span class="sxs-lookup"><span data-stu-id="9f5eb-113">The portfolios.proto file</span></span>

<span data-ttu-id="9f5eb-114">Si vous avez suivi les instructions de la section précédente, vous devez avoir un projet gRPC avec un `portfolios.proto` fichier qui ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="9f5eb-114">If you followed the instructions in the previous section, you should have a gRPC project with a `portfolios.proto` file that looks like this:</span></span>

```protobuf
syntax = "proto3";

option csharp_namespace = "TraderSys.Portfolios.Protos";

package PortfolioServer;

service Portfolios {
  // RPCs will go here
}
```

<span data-ttu-id="9f5eb-115">La première étape consiste à migrer les `DataContract` classes vers leurs équivalents Protobuf.</span><span class="sxs-lookup"><span data-stu-id="9f5eb-115">The first step is to migrate the `DataContract` classes to their Protobuf equivalents.</span></span>

## <a name="convert-the-datacontract-classes-to-grpc-messages"></a><span data-ttu-id="9f5eb-116">Convertir les classes DataContract en messages gRPC</span><span class="sxs-lookup"><span data-stu-id="9f5eb-116">Convert the DataContract classes to gRPC messages</span></span>

<span data-ttu-id="9f5eb-117">La `PortfolioItem` classe sera tout d’abord convertie en message Protobuf, car la `Portfolio` classe en dépend.</span><span class="sxs-lookup"><span data-stu-id="9f5eb-117">The `PortfolioItem` class will be converted to a Protobuf message first, because the `Portfolio` class depends on it.</span></span> <span data-ttu-id="9f5eb-118">La classe est simple, et trois des propriétés sont mappées directement aux types de données gRPC.</span><span class="sxs-lookup"><span data-stu-id="9f5eb-118">The class is simple, and three of the properties map directly to gRPC data types.</span></span> <span data-ttu-id="9f5eb-119">La `Cost` propriété, qui représente le prix payé pour les partages à l’achat, est un `decimal` champ.</span><span class="sxs-lookup"><span data-stu-id="9f5eb-119">The `Cost` property, which represents the price paid for the shares at purchase, is a `decimal` field.</span></span> <span data-ttu-id="9f5eb-120">gRPC prend uniquement en charge `float` ou `double` pour les nombres réels, qui ne sont pas adaptés à la devise.</span><span class="sxs-lookup"><span data-stu-id="9f5eb-120">gRPC supports only `float` or `double` for real numbers, which aren't suitable for currency.</span></span> <span data-ttu-id="9f5eb-121">Étant donné que les prix de partage varient d’un cent au minimum, le coût peut être exprimé en `int32` cents.</span><span class="sxs-lookup"><span data-stu-id="9f5eb-121">Because share prices vary by a minimum of one cent, the cost can be expressed as an `int32` of cents.</span></span>

> [!NOTE]
> <span data-ttu-id="9f5eb-122">N’oubliez pas d’utiliser `snake_case` pour les noms de champ dans votre `.proto` fichier.</span><span class="sxs-lookup"><span data-stu-id="9f5eb-122">Remember to use `snake_case` for field names in your `.proto` file.</span></span> <span data-ttu-id="9f5eb-123">Le générateur de code C# les convertira en `PascalCase` pour vous, et les utilisateurs d’autres langages vous remercient de respecter leurs différentes normes de codage.</span><span class="sxs-lookup"><span data-stu-id="9f5eb-123">The C# code generator will convert them to `PascalCase` for you, and users of other languages will thank you for respecting their different coding standards.</span></span>

```protobuf
message PortfolioItem {
    int32 id = 1;
    int32 share_id = 2;
    int32 holding = 3;
    int32 cost_cents = 4;
}
```

<span data-ttu-id="9f5eb-124">La `Portfolio` classe est un peu plus compliquée.</span><span class="sxs-lookup"><span data-stu-id="9f5eb-124">The `Portfolio` class is a little more complicated.</span></span> <span data-ttu-id="9f5eb-125">Dans le code WCF, le développeur a utilisé un `Guid` pour la `TraderId` propriété et contient un `List<PortfolioItem>` .</span><span class="sxs-lookup"><span data-stu-id="9f5eb-125">In the WCF code, the developer used a `Guid` for the `TraderId` property, and contains a `List<PortfolioItem>`.</span></span> <span data-ttu-id="9f5eb-126">Dans Protobuf, qui n’a pas de type de première classe `UUID` , vous devez utiliser un `string` pour le `traderId` champ et l’analyser dans votre propre code.</span><span class="sxs-lookup"><span data-stu-id="9f5eb-126">In Protobuf, which doesn't have a first-class `UUID` type, you should use a `string` for the `traderId` field and parse it in your own code.</span></span> <span data-ttu-id="9f5eb-127">Pour obtenir la liste des éléments, utilisez le `repeated` mot clé sur le champ.</span><span class="sxs-lookup"><span data-stu-id="9f5eb-127">For the list of items, use the `repeated` keyword on the field.</span></span>

```protobuf
message Portfolio {
    int32 id = 1;
    string trader_id = 2;
    repeated PortfolioItem items = 3;
}
```

<span data-ttu-id="9f5eb-128">Maintenant que vous disposez des messages de données, vous pouvez déclarer les points de terminaison RPC du service.</span><span class="sxs-lookup"><span data-stu-id="9f5eb-128">Now that you have the data messages, you can declare the service RPC endpoints.</span></span>

## <a name="convert-servicecontract-to-a-grpc-service"></a><span data-ttu-id="9f5eb-129">Convertir ServiceContract en service gRPC</span><span class="sxs-lookup"><span data-stu-id="9f5eb-129">Convert ServiceContract to a gRPC service</span></span>

<span data-ttu-id="9f5eb-130">La `Get` méthode WCF accepte deux paramètres : `Guid traderId` et `int portfolioId` .</span><span class="sxs-lookup"><span data-stu-id="9f5eb-130">The WCF `Get` method takes two parameters: `Guid traderId` and `int portfolioId`.</span></span> <span data-ttu-id="9f5eb-131">les méthodes de service gRPC ne peuvent prendre qu’un seul paramètre. vous devez donc créer un message pour contenir les deux valeurs.</span><span class="sxs-lookup"><span data-stu-id="9f5eb-131">gRPC service methods can take only a single parameter, so you need to create a message to hold the two values.</span></span> <span data-ttu-id="9f5eb-132">Il est courant de nommer ces objets de requête avec le même nom que la méthode suivie du suffixe `Request` .</span><span class="sxs-lookup"><span data-stu-id="9f5eb-132">It's common practice to name these request objects with the same name as the method followed by the suffix `Request`.</span></span> <span data-ttu-id="9f5eb-133">Là encore, `string` est utilisé pour le `traderId` champ à la place de `Guid` .</span><span class="sxs-lookup"><span data-stu-id="9f5eb-133">Again, `string` is being used for the `traderId` field instead of `Guid`.</span></span>

<span data-ttu-id="9f5eb-134">Le service peut simplement retourner un `Portfolio` message directement, mais là encore, cela peut affecter la compatibilité descendante à l’avenir.</span><span class="sxs-lookup"><span data-stu-id="9f5eb-134">The service could just return a `Portfolio` message directly, but again, this could affect backward compatibility in the future.</span></span> <span data-ttu-id="9f5eb-135">Il est conseillé de définir des messages distincts `Request` et `Response` pour chaque méthode dans un service, même si beaucoup d’entre eux sont les mêmes pour le moment.</span><span class="sxs-lookup"><span data-stu-id="9f5eb-135">It's a good practice to define separate `Request` and `Response` messages for every method in a service, even if many of them are the same right now.</span></span> <span data-ttu-id="9f5eb-136">Par conséquent, déclarez un `GetResponse` message avec un seul `Portfolio` champ.</span><span class="sxs-lookup"><span data-stu-id="9f5eb-136">So declare a `GetResponse` message with a single `Portfolio` field.</span></span>

<span data-ttu-id="9f5eb-137">Cet exemple illustre la déclaration de la méthode de service gRPC avec le `GetRequest` message suivant :</span><span class="sxs-lookup"><span data-stu-id="9f5eb-137">This example shows the declaration of the gRPC service method with the `GetRequest` message:</span></span>

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

<span data-ttu-id="9f5eb-138">La `GetAll` méthode WCF prend un seul paramètre, `traderId` , ce qui signifie que vous pouvez spécifier `string` comme type de paramètre.</span><span class="sxs-lookup"><span data-stu-id="9f5eb-138">The WCF `GetAll` method takes only a single parameter, `traderId`, so it might seem that you could specify `string` as the parameter type.</span></span> <span data-ttu-id="9f5eb-139">Toutefois, gRPC nécessite un type de message défini.</span><span class="sxs-lookup"><span data-stu-id="9f5eb-139">But gRPC requires a defined message type.</span></span> <span data-ttu-id="9f5eb-140">Cette exigence permet de mettre en œuvre la pratique consistant à utiliser des messages personnalisés pour toutes les entrées et sorties, en vue d’une compatibilité descendante future.</span><span class="sxs-lookup"><span data-stu-id="9f5eb-140">This requirement helps to enforce the practice of using custom messages for all inputs and outputs, for future backward compatibility.</span></span>

<span data-ttu-id="9f5eb-141">La méthode WCF retourne également un `List<Portfolio>` , mais pour la même raison, il n’autorise pas les types de paramètres simples, gRPC n’autorise pas `repeated Portfolio` comme type de retour.</span><span class="sxs-lookup"><span data-stu-id="9f5eb-141">The WCF method also returns a `List<Portfolio>`, but for the same reason it doesn't allow simple parameter types, gRPC won't allow `repeated Portfolio` as a return type.</span></span> <span data-ttu-id="9f5eb-142">Au lieu de cela, créez un `GetAllResponse` type pour encapsuler la liste.</span><span class="sxs-lookup"><span data-stu-id="9f5eb-142">Instead, create a `GetAllResponse` type to wrap the list.</span></span>

> [!WARNING]
> <span data-ttu-id="9f5eb-143">Vous pouvez être tenté de créer un `PortfolioList` message ou un nom similaire et de l’utiliser sur plusieurs méthodes de service, mais vous devez résister à cette tentation.</span><span class="sxs-lookup"><span data-stu-id="9f5eb-143">You might be tempted to create a `PortfolioList` message or something similar and use it across multiple service methods, but you should resist this temptation.</span></span> <span data-ttu-id="9f5eb-144">Il est impossible de savoir comment les différentes méthodes d’un service évoluent, de sorte à conserver les messages spécifiques et à les séparer correctement.</span><span class="sxs-lookup"><span data-stu-id="9f5eb-144">It's impossible to know how the various methods on a service will evolve, so keep their messages specific and cleanly separated.</span></span>

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

<span data-ttu-id="9f5eb-145">Si vous enregistrez votre projet avec ces modifications, la cible de génération gRPC s’exécute en arrière-plan et génère tous les types de messages Protobuf et une classe de base que vous pouvez hériter pour implémenter le service.</span><span class="sxs-lookup"><span data-stu-id="9f5eb-145">If you save your project with these changes, the gRPC build target will run in the background and generate all the Protobuf message types and a base class that you can inherit to implement the service.</span></span>

<span data-ttu-id="9f5eb-146">Ouvrez la `Services/GreeterService.cs` classe et supprimez l’exemple de code.</span><span class="sxs-lookup"><span data-stu-id="9f5eb-146">Open the `Services/GreeterService.cs` class and delete the example code.</span></span> <span data-ttu-id="9f5eb-147">Vous pouvez maintenant ajouter l’implémentation du service de portefeuille.</span><span class="sxs-lookup"><span data-stu-id="9f5eb-147">Now you can add the Portfolio service implementation.</span></span> <span data-ttu-id="9f5eb-148">La classe de base générée se trouve dans l' `Protos` espace de noms et est générée comme une classe imbriquée.</span><span class="sxs-lookup"><span data-stu-id="9f5eb-148">The generated base class will be in the `Protos` namespace and is generated as a nested class.</span></span> <span data-ttu-id="9f5eb-149">gRPC crée une classe statique portant le même nom que le service dans le `.proto` fichier et une classe de base avec le suffixe `Base` à l’intérieur de cette classe statique. par conséquent, l’identificateur complet du type de base est `TraderSys.Portfolios.Protos.Portfolios.PortfoliosBase` .</span><span class="sxs-lookup"><span data-stu-id="9f5eb-149">gRPC creates a static class with the same name as the service in the `.proto` file and a base class with the suffix `Base` inside that static class, so the full identifier for the base type is `TraderSys.Portfolios.Protos.Portfolios.PortfoliosBase`.</span></span>

```csharp
namespace TraderSys.Portfolios.Services
{
    public class PortfolioService : Protos.Portfolios.PortfoliosBase
    {
    }
}
```

<span data-ttu-id="9f5eb-150">La classe de base déclare `virtual` des méthodes pour `Get` et `GetAll` qui peuvent être substituées pour implémenter le service.</span><span class="sxs-lookup"><span data-stu-id="9f5eb-150">The base class declares `virtual` methods for `Get` and `GetAll` that can be overridden to implement the service.</span></span> <span data-ttu-id="9f5eb-151">Les méthodes sont `virtual` plutôt que `abstract` si vous ne les implémentez pas, le service peut retourner un code d' `Unimplemented` État gRPC explicite, comme vous pouvez lever une `NotImplementedException` dans du code C# normal.</span><span class="sxs-lookup"><span data-stu-id="9f5eb-151">The methods are `virtual` rather than `abstract` so that if you don't implement them, the service can return an explicit gRPC `Unimplemented` status code, much like you might throw a `NotImplementedException` in regular C# code.</span></span>

<span data-ttu-id="9f5eb-152">La signature de toutes les méthodes de service unaires gRPC dans ASP.NET Core est cohérente.</span><span class="sxs-lookup"><span data-stu-id="9f5eb-152">The signature for all gRPC unary service methods in ASP.NET Core is consistent.</span></span> <span data-ttu-id="9f5eb-153">Il existe deux paramètres : le premier est le type de message déclaré dans le `.proto` fichier, et le second est un `ServerCallContext` qui fonctionne de la même façon que le `HttpContext` de ASP.net core.</span><span class="sxs-lookup"><span data-stu-id="9f5eb-153">There are two parameters: the first is the message type declared in the `.proto` file, and the second is a `ServerCallContext` that works similarly to the `HttpContext` from ASP.NET Core.</span></span> <span data-ttu-id="9f5eb-154">En fait, il existe une méthode d’extension appelée `GetHttpContext` sur la `ServerCallContext` classe que vous pouvez utiliser pour accéder au sous-jacent `HttpContext` , même si vous n’avez pas besoin de l’utiliser souvent.</span><span class="sxs-lookup"><span data-stu-id="9f5eb-154">In fact, there's an extension method called `GetHttpContext` on the `ServerCallContext` class that you can use to get the underlying `HttpContext`, although you shouldn't need to use it often.</span></span> <span data-ttu-id="9f5eb-155">Nous examinerons `ServerCallContext` plus loin dans ce chapitre et également dans le chapitre traitant de l’authentification.</span><span class="sxs-lookup"><span data-stu-id="9f5eb-155">We'll take a look at `ServerCallContext` later in this chapter, and also in the chapter that discusses authentication.</span></span>

<span data-ttu-id="9f5eb-156">Le type de retour de la méthode est un `Task<T>` , où `T` est le type de message de réponse.</span><span class="sxs-lookup"><span data-stu-id="9f5eb-156">The method's return type is a `Task<T>`, where `T` is the response message type.</span></span> <span data-ttu-id="9f5eb-157">Toutes les méthodes de service gRPC sont asynchrones.</span><span class="sxs-lookup"><span data-stu-id="9f5eb-157">All gRPC service methods are asynchronous.</span></span>

## <a name="migrate-the-portfoliodata-library-to-net"></a><span data-ttu-id="9f5eb-158">Migrer la bibliothèque PortfolioData vers .NET</span><span class="sxs-lookup"><span data-stu-id="9f5eb-158">Migrate the PortfolioData library to .NET</span></span>

<span data-ttu-id="9f5eb-159">À ce stade, le projet a besoin du référentiel de portefeuille et des modèles contenus dans la `TraderSys.PortfolioData` bibliothèque de classes de la solution WCF.</span><span class="sxs-lookup"><span data-stu-id="9f5eb-159">At this point, the project needs the Portfolio repository and models contained in the `TraderSys.PortfolioData` class library in the WCF solution.</span></span> <span data-ttu-id="9f5eb-160">Le moyen le plus simple de les placer consiste à créer une nouvelle bibliothèque de classes à l’aide de la boîte de dialogue **nouveau projet** de Visual Studio avec le modèle Bibliothèque de classes (.NET standard), ou à partir de la ligne de commande à l’aide de la CLI .net Core, en exécutant les commandes suivantes à partir du répertoire qui contient le `TraderSys.sln` fichier :</span><span class="sxs-lookup"><span data-stu-id="9f5eb-160">The easiest way to bring them across is to create a new class library by using either the Visual Studio **New project** dialog box with the Class Library (.NET Standard) template, or from the command line by using the .NET Core CLI, running these commands from the directory that contains the `TraderSys.sln` file:</span></span>

```dotnetcli
dotnet new classlib -o src/TraderSys.PortfolioData
dotnet sln add src/TraderSys.PortfolioData
```

<span data-ttu-id="9f5eb-161">Une fois que vous avez créé la bibliothèque et que vous l’avez ajoutée à la solution, supprimez le `Class1.cs` fichier généré et copiez les fichiers de la bibliothèque de la solution WCF dans le dossier de la nouvelle bibliothèque de classes, en conservant la structure de dossiers :</span><span class="sxs-lookup"><span data-stu-id="9f5eb-161">After you've created the library and added it to the solution, delete the generated `Class1.cs` file and copy the files from the WCF solution's library into the new class library's folder, keeping the folder structure:</span></span>

```
Models
  Portfolio.cs
  PortfolioItem.cs
IPortfolioRepository.cs
PortfolioRepository.cs
```

<span data-ttu-id="9f5eb-162">Les projets .NET de type SDK incluent automatiquement tous les `.cs` fichiers dans ou sous leur propre répertoire. vous n’avez donc pas besoin de les ajouter explicitement au projet.</span><span class="sxs-lookup"><span data-stu-id="9f5eb-162">SDK-style .NET projects automatically include any `.cs` files in or under their own directory, so you don't need to explicitly add them to the project.</span></span> <span data-ttu-id="9f5eb-163">La seule étape restante consiste à supprimer les `DataContract` `DataMember` attributs et `Portfolio` des `PortfolioItem` classes et afin qu’ils soient des classes C# simples :</span><span class="sxs-lookup"><span data-stu-id="9f5eb-163">The only step remaining is to remove the `DataContract` and `DataMember` attributes from the `Portfolio` and `PortfolioItem` classes so they're plain old C# classes:</span></span>

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

## <a name="use-aspnet-core-dependency-injection"></a><span data-ttu-id="9f5eb-164">Utiliser ASP.NET Core l’injection de dépendances</span><span class="sxs-lookup"><span data-stu-id="9f5eb-164">Use ASP.NET Core dependency injection</span></span>

<span data-ttu-id="9f5eb-165">Vous pouvez maintenant ajouter une référence à cette bibliothèque au projet d’application gRPC et utiliser la `PortfolioRepository` classe en utilisant l’injection de dépendances dans l’implémentation du service gRPC.</span><span class="sxs-lookup"><span data-stu-id="9f5eb-165">Now you can add a reference to this library to the gRPC application project and consume the `PortfolioRepository` class by using dependency injection in the gRPC service implementation.</span></span> <span data-ttu-id="9f5eb-166">Dans l’application WCF, l’injection de dépendances a été fournie par le conteneur IoC Autofac.</span><span class="sxs-lookup"><span data-stu-id="9f5eb-166">In the WCF application, dependency injection was provided by the Autofac IoC container.</span></span> <span data-ttu-id="9f5eb-167">ASP.NET Core intègre une injection de dépendances.</span><span class="sxs-lookup"><span data-stu-id="9f5eb-167">ASP.NET Core has dependency injection baked in.</span></span> <span data-ttu-id="9f5eb-168">Vous pouvez inscrire le référentiel dans la `ConfigureServices` méthode de la `Startup` classe :</span><span class="sxs-lookup"><span data-stu-id="9f5eb-168">You can register the repository in the `ConfigureServices` method in the `Startup` class:</span></span>

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

<span data-ttu-id="9f5eb-169">L' `IPortfolioRepository` implémentation peut maintenant être spécifiée en tant que paramètre de constructeur dans la `PortfolioService` classe, comme suit :</span><span class="sxs-lookup"><span data-stu-id="9f5eb-169">The `IPortfolioRepository` implementation can now be specified as a constructor parameter in the `PortfolioService` class, as follows:</span></span>

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

## <a name="implement-the-grpc-service"></a><span data-ttu-id="9f5eb-170">Implémenter le service gRPC</span><span class="sxs-lookup"><span data-stu-id="9f5eb-170">Implement the gRPC service</span></span>

<span data-ttu-id="9f5eb-171">Maintenant que vous avez déclaré vos messages et votre service dans le `portfolios.proto` fichier, vous devez implémenter les méthodes de service dans la `PortfolioService` classe qui hérite de la classe générée par gRPC `Portfolios.PortfoliosBase` .</span><span class="sxs-lookup"><span data-stu-id="9f5eb-171">Now that you've declared your messages and your service in the `portfolios.proto` file, you have to implement the service methods in the `PortfolioService` class that inherits from the gRPC-generated `Portfolios.PortfoliosBase` class.</span></span> <span data-ttu-id="9f5eb-172">Les méthodes sont déclarées comme `virtual` dans la classe de base.</span><span class="sxs-lookup"><span data-stu-id="9f5eb-172">The methods are declared as `virtual` in the base class.</span></span> <span data-ttu-id="9f5eb-173">Si vous ne les remplacez pas, ils retournent un code d’État gRPC « non implémenté » par défaut.</span><span class="sxs-lookup"><span data-stu-id="9f5eb-173">If you don't override them, they'll return a gRPC "Not Implemented" status code by default.</span></span>

<span data-ttu-id="9f5eb-174">Commencez par implémenter la `Get` méthode.</span><span class="sxs-lookup"><span data-stu-id="9f5eb-174">Start by implementing the `Get` method.</span></span> <span data-ttu-id="9f5eb-175">La substitution par défaut se présente comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="9f5eb-175">The default override looks like this example:</span></span>

```csharp
public override Task<GetResponse> Get(GetRequest request, ServerCallContext context)
{
    return base.Get(request, context);
}
```

<span data-ttu-id="9f5eb-176">Le premier problème est qu’il `request.TraderId` s’agit d’une chaîne, et le service requiert un `Guid` .</span><span class="sxs-lookup"><span data-stu-id="9f5eb-176">The first problem is that `request.TraderId` is a string, and the service requires a `Guid`.</span></span> <span data-ttu-id="9f5eb-177">Même si le format attendu pour la chaîne est `UUID` , le code doit gérer la possibilité qu’un appelant ait envoyé une valeur non valide et réponde de manière appropriée.</span><span class="sxs-lookup"><span data-stu-id="9f5eb-177">Even though the expected format for the string is `UUID`, the code has to deal with the possibility that a caller has sent an invalid value and respond appropriately.</span></span> <span data-ttu-id="9f5eb-178">Le service peut répondre avec des erreurs en levant un `RpcException` et en utilisant le `InvalidArgument` code d’état standard pour exprimer le problème :</span><span class="sxs-lookup"><span data-stu-id="9f5eb-178">The service can respond with errors by throwing an `RpcException` and use the standard `InvalidArgument` status code to express the problem:</span></span>

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

<span data-ttu-id="9f5eb-179">Une fois que la valeur est correcte `Guid` pour `traderId` , vous pouvez utiliser le référentiel pour récupérer le portefeuille et le renvoyer au client :</span><span class="sxs-lookup"><span data-stu-id="9f5eb-179">After there's a proper `Guid` value for `traderId`, you can use the repository to retrieve the Portfolio and return it to the client:</span></span>

```csharp
    var response = new GetResponse
    {
        Portfolio = await _repository.GetAsync(request.TraderId, request.PortfolioId)
    };
```

### <a name="map-internal-models-to-grpc-messages"></a><span data-ttu-id="9f5eb-180">Mapper les modèles internes aux messages gRPC</span><span class="sxs-lookup"><span data-stu-id="9f5eb-180">Map internal models to gRPC messages</span></span>

<span data-ttu-id="9f5eb-181">Le code précédent ne fonctionne pas réellement, car le référentiel retourne son propre modèle POCO `Portfolio` , mais gRPC a besoin de son propre message Protobuf `Portfolio` .</span><span class="sxs-lookup"><span data-stu-id="9f5eb-181">The previous code doesn't actually work because the repository is returning its own POCO model `Portfolio`, but gRPC needs its own Protobuf message `Portfolio`.</span></span> <span data-ttu-id="9f5eb-182">Comme lorsque vous mappez des types de Entity Framework à des types de transfert de données, la meilleure solution consiste à fournir une conversion entre les deux.</span><span class="sxs-lookup"><span data-stu-id="9f5eb-182">As when you map Entity Framework types to data transfer types, the best solution is to provide a conversion between the two.</span></span> <span data-ttu-id="9f5eb-183">Un bon emplacement pour mettre le code pour cette conversion se trouve dans la classe générée par Protobuf, qui est déclarée en tant que `partial` classe afin de pouvoir être étendue :</span><span class="sxs-lookup"><span data-stu-id="9f5eb-183">A good place to put the code for this conversion is in the Protobuf-generated class, which is declared as a `partial` class so it can be extended:</span></span>

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
> <span data-ttu-id="9f5eb-184">Vous pouvez utiliser une bibliothèque comme [AutoMapper](https://automapper.org/) pour gérer cette conversion des classes de modèle internes en types Protobuf, à condition de configurer les conversions de type de niveau inférieur comme `string` / `Guid` ou `decimal` / `double` et le mappage de liste.</span><span class="sxs-lookup"><span data-stu-id="9f5eb-184">You could use a library like [AutoMapper](https://automapper.org/) to handle this conversion from internal model classes to Protobuf types, as long as you configure the lower-level type conversions like `string`/`Guid` or `decimal`/`double` and the list mapping.</span></span>

<span data-ttu-id="9f5eb-185">Maintenant que le code de conversion est en place, vous pouvez terminer l' `Get` implémentation de la méthode :</span><span class="sxs-lookup"><span data-stu-id="9f5eb-185">Now that you have the conversion code in place, you can complete the `Get` method implementation:</span></span>

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

<span data-ttu-id="9f5eb-186">L’implémentation de la `GetAll` méthode est similaire.</span><span class="sxs-lookup"><span data-stu-id="9f5eb-186">The implementation of the `GetAll` method is similar.</span></span> <span data-ttu-id="9f5eb-187">Notez que les `repeated` champs des messages Protobuf sont générés en tant que `readonly` Propriétés de type `RepeatedField<T>` , de sorte que vous devez leur ajouter des éléments à l’aide de la `AddRange` méthode, comme dans cet exemple :</span><span class="sxs-lookup"><span data-stu-id="9f5eb-187">Note that the `repeated` fields on Protobuf messages are generated as `readonly` properties of type `RepeatedField<T>`, so you have to add items to them by using the `AddRange` method, like in this example:</span></span>

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

<span data-ttu-id="9f5eb-188">Après avoir migré le service WCF Request-Reply vers gRPC, nous allons maintenant créer un client à partir du `.proto` fichier.</span><span class="sxs-lookup"><span data-stu-id="9f5eb-188">Having successfully migrated the WCF request-reply service to gRPC, let's look at creating a client for it from the `.proto` file.</span></span>

## <a name="generate-client-code"></a><span data-ttu-id="9f5eb-189">Générer le code client</span><span class="sxs-lookup"><span data-stu-id="9f5eb-189">Generate client code</span></span>

<span data-ttu-id="9f5eb-190">Créez une bibliothèque de classes .NET Standard dans la même solution pour contenir le client.</span><span class="sxs-lookup"><span data-stu-id="9f5eb-190">Create a .NET Standard class library in the same solution to contain the client.</span></span> <span data-ttu-id="9f5eb-191">Il s’agit principalement d’un exemple de création de code client, mais vous pouvez empaqueter une telle bibliothèque à l’aide de NuGet et la distribuer sur un référentiel interne pour que d’autres équipes .NET puissent les utiliser.</span><span class="sxs-lookup"><span data-stu-id="9f5eb-191">This is primarily an example of creating client code, but you could package such a library by using NuGet and distribute it on an internal repository for other .NET teams to consume.</span></span> <span data-ttu-id="9f5eb-192">Continuez et ajoutez une nouvelle bibliothèque de classes .NET Standard appelée `TraderSys.Portfolios.Client` à la solution et supprimez le `Class1.cs` fichier.</span><span class="sxs-lookup"><span data-stu-id="9f5eb-192">Go ahead and add a new .NET Standard class library called `TraderSys.Portfolios.Client` to the solution and delete the `Class1.cs` file.</span></span>

> [!CAUTION]
> <span data-ttu-id="9f5eb-193">Le package NuGet [.net. client GRPC](https://www.nuget.org/packages/Grpc.Net.Client) nécessite .net Core 3,0 ou une version ultérieure (ou .NET standard un autre Runtime conforme à 2,1).</span><span class="sxs-lookup"><span data-stu-id="9f5eb-193">The [Grpc.Net.Client](https://www.nuget.org/packages/Grpc.Net.Client) NuGet package requires .NET Core 3.0 or later (or another .NET Standard 2.1-compliant runtime).</span></span> <span data-ttu-id="9f5eb-194">Les versions antérieures de .NET Framework et .NET Core sont prises en charge par le package NuGet [GRPC. Core](https://www.nuget.org/packages/Grpc.Core) .</span><span class="sxs-lookup"><span data-stu-id="9f5eb-194">Earlier versions of .NET Framework and .NET Core are supported by the [Grpc.Core](https://www.nuget.org/packages/Grpc.Core) NuGet package.</span></span>

<span data-ttu-id="9f5eb-195">Dans Visual Studio 2019, vous pouvez ajouter des références aux services gRPC de la même façon que vous ajoutez des références de service aux projets WCF dans les versions antérieures de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9f5eb-195">In Visual Studio 2019, you can add references to gRPC services in a way that's similar to how you'd add service references to WCF projects in earlier versions of Visual Studio.</span></span> <span data-ttu-id="9f5eb-196">Les références de service et les services connectés sont tous gérés sous la même interface utilisateur maintenant.</span><span class="sxs-lookup"><span data-stu-id="9f5eb-196">Service references and connected services are all managed under the same UI now.</span></span> <span data-ttu-id="9f5eb-197">Vous pouvez accéder à l’interface utilisateur en cliquant avec le bouton droit sur le nœud **dépendances** dans le `TraderSys.Portfolios.Client` projet dans Explorateur de solutions et en sélectionnant **Ajouter un service connecté**.</span><span class="sxs-lookup"><span data-stu-id="9f5eb-197">You can access the UI by right-clicking the **Dependencies** node in the `TraderSys.Portfolios.Client` project in Solution Explorer and selecting **Add Connected Service**.</span></span> <span data-ttu-id="9f5eb-198">Dans la fenêtre outil qui s’affiche, sélectionnez la section **références de service** , puis sélectionnez **Ajouter une nouvelle référence de service gRPC**:</span><span class="sxs-lookup"><span data-stu-id="9f5eb-198">In the tool window that appears, select the **Service References** section and then select **Add new gRPC service reference**:</span></span>

![Interface utilisateur Services connectés dans Visual Studio 2019](media/migrate-request-reply/add-connected-service.png)

<span data-ttu-id="9f5eb-200">Accédez au `portfolios.proto` fichier dans le `TraderSys.Portfolios` projet, laissez **client** sous **sélectionnez le type de classe à générer**, puis sélectionnez **OK**:</span><span class="sxs-lookup"><span data-stu-id="9f5eb-200">Browse to the `portfolios.proto` file in the `TraderSys.Portfolios` project, leave **Client** under **Select the type of class to be generated**, and then select **OK**:</span></span>

![Boîte de dialogue Ajouter une nouvelle référence de service gRPC dans Visual Studio 2019](media/migrate-request-reply/add-new-grpc-service-reference.png)

> [!TIP]
> <span data-ttu-id="9f5eb-202">Notez que cette boîte de dialogue fournit également un champ d’URL.</span><span class="sxs-lookup"><span data-stu-id="9f5eb-202">Notice that this dialog box also provides a URL field.</span></span> <span data-ttu-id="9f5eb-203">Si votre organisation gère un répertoire Web de `.proto` fichiers, vous pouvez créer des clients simplement en définissant cette adresse URL.</span><span class="sxs-lookup"><span data-stu-id="9f5eb-203">If your organization maintains a web-accessible directory of `.proto` files, you can create clients just by setting this URL address.</span></span>

<span data-ttu-id="9f5eb-204">Lorsque vous utilisez la fonctionnalité **Ajouter un service connecté** de Visual Studio, le `portfolios.proto` fichier est ajouté au projet de bibliothèque de classes en tant que *fichier lié* plutôt que copié, de sorte que les modifications apportées au fichier dans le projet de service sont automatiquement appliquées dans le projet client.</span><span class="sxs-lookup"><span data-stu-id="9f5eb-204">When you use the Visual Studio **Add Connected Service** feature, the `portfolios.proto` file is added to the class library project as a *linked file* rather than copied, so changes to the file in the service project will automatically be applied in the client project.</span></span> <span data-ttu-id="9f5eb-205">L' `<Protobuf>` élément dans le `csproj` fichier se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="9f5eb-205">The `<Protobuf>` element in the `csproj` file looks like this:</span></span>

```xml
<Protobuf Include="..\TraderSys.Portfolios\Protos\portfolios.proto" GrpcServices="Client">
  <Link>Protos\portfolios.proto</Link>
</Protobuf>
```

> [!TIP]
> <span data-ttu-id="9f5eb-206">Si vous n’utilisez pas Visual Studio ou si vous préférez travailler à partir de la ligne de commande, vous pouvez utiliser l' `dotnet-grpc` outil global pour gérer les références Protobuf dans un projet .net gRPC.</span><span class="sxs-lookup"><span data-stu-id="9f5eb-206">If you're not using Visual Studio or prefer to work from the command line, you can use the `dotnet-grpc` global tool to manage Protobuf references in a .NET gRPC project.</span></span> <span data-ttu-id="9f5eb-207">Pour plus d’informations, consultez la [ `dotnet-grpc` documentation](/aspnet/core/grpc/dotnet-grpc).</span><span class="sxs-lookup"><span data-stu-id="9f5eb-207">For more information, see the [`dotnet-grpc` documentation](/aspnet/core/grpc/dotnet-grpc).</span></span>

### <a name="use-the-portfolios-service-from-a-client-application"></a><span data-ttu-id="9f5eb-208">Utiliser le service portefeuilles à partir d’une application cliente</span><span class="sxs-lookup"><span data-stu-id="9f5eb-208">Use the Portfolios service from a client application</span></span>

<span data-ttu-id="9f5eb-209">Le code suivant est un bref exemple illustrant comment utiliser le client généré dans une application console.</span><span class="sxs-lookup"><span data-stu-id="9f5eb-209">The following code is a brief example of how to use the generated client in a console application.</span></span> <span data-ttu-id="9f5eb-210">Une exploration plus détaillée du code client gRPC est à la fin de ce chapitre.</span><span class="sxs-lookup"><span data-stu-id="9f5eb-210">A more detailed exploration of the gRPC client code is at the end of this chapter.</span></span>

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

<span data-ttu-id="9f5eb-211">Vous avez maintenant migré une application WCF de base vers un service ASP.NET Core gRPC et créé un client pour consommer le service à partir d’une application .NET.</span><span class="sxs-lookup"><span data-stu-id="9f5eb-211">You've now migrated a basic WCF application to an ASP.NET Core gRPC service and created a client to consume the service from a .NET application.</span></span> <span data-ttu-id="9f5eb-212">La section suivante couvre les services duplex plus impliqués.</span><span class="sxs-lookup"><span data-stu-id="9f5eb-212">The next section will cover the more involved duplex services.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="9f5eb-213">[Précédent](create-project.md) 
> [Suivant](migrate-duplex-services.md)</span><span class="sxs-lookup"><span data-stu-id="9f5eb-213">[Previous](create-project.md)
[Next](migrate-duplex-services.md)</span></span>
