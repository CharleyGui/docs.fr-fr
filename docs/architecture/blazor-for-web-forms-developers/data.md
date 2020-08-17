---
title: Gestion et accès aux données
description: Découvrez comment accéder aux données et les gérer dans ASP.NET Web Forms et Blazor .
author: csharpfritz
ms.author: jefritz
no-loc:
- Blazor
ms.date: 04/26/2020
ms.openlocfilehash: 8bd326e6952708b2099c3a575d6811990335df17
ms.sourcegitcommit: 0100be20fcf23f61dab672deced70059ed71bb2e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88267592"
---
# <a name="work-with-data"></a><span data-ttu-id="9f34a-103">Utilisation des données</span><span class="sxs-lookup"><span data-stu-id="9f34a-103">Work with data</span></span>

<span data-ttu-id="9f34a-104">L’accès aux données est le segment principal d’une application Web Forms ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="9f34a-104">Data access is the backbone of an ASP.NET Web Forms app.</span></span> <span data-ttu-id="9f34a-105">Si vous créez des formulaires pour le Web, que se passe-t-il pour ces données ?</span><span class="sxs-lookup"><span data-stu-id="9f34a-105">If you're building forms for the web, what happens to that data?</span></span> <span data-ttu-id="9f34a-106">Avec Web Forms, plusieurs techniques d’accès aux données peuvent être utilisées pour interagir avec une base de données :</span><span class="sxs-lookup"><span data-stu-id="9f34a-106">With Web Forms, there were multiple data access techniques you could use to interact with a database:</span></span>

- <span data-ttu-id="9f34a-107">Sources de données</span><span class="sxs-lookup"><span data-stu-id="9f34a-107">Data Sources</span></span>
- <span data-ttu-id="9f34a-108">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="9f34a-108">ADO.NET</span></span>
- <span data-ttu-id="9f34a-109">Entity Framework</span><span class="sxs-lookup"><span data-stu-id="9f34a-109">Entity Framework</span></span>

<span data-ttu-id="9f34a-110">Les sources de données étaient des contrôles que vous pouviez placer sur une page de Web Forms et configurer comme d’autres contrôles.</span><span class="sxs-lookup"><span data-stu-id="9f34a-110">Data Sources were controls that you could place on a Web Forms page and configure like other controls.</span></span> <span data-ttu-id="9f34a-111">Visual Studio a fourni un ensemble convivial de boîtes de dialogue pour configurer et lier les contrôles à vos pages de Web Forms.</span><span class="sxs-lookup"><span data-stu-id="9f34a-111">Visual Studio provided a friendly set of dialogs to configure and bind the controls to your Web Forms pages.</span></span> <span data-ttu-id="9f34a-112">Les développeurs qui bénéficient d’une approche « code faible » ou « sans code » favorisent cette technique lors de la première publication de Web Forms.</span><span class="sxs-lookup"><span data-stu-id="9f34a-112">Developers who enjoy a "low code" or "no code" approach preferred this technique when Web Forms was first released.</span></span>

![Sources de données](media/data/datasources.png)

<span data-ttu-id="9f34a-114">ADO.NET est l’approche de bas niveau pour interagir avec une base de données.</span><span class="sxs-lookup"><span data-stu-id="9f34a-114">ADO.NET is the low-level approach to interacting with a database.</span></span> <span data-ttu-id="9f34a-115">Vos applications peuvent créer une connexion à la base de données avec des commandes, des jeux d’enregistrements et des jeux de données pour interagir.</span><span class="sxs-lookup"><span data-stu-id="9f34a-115">Your apps could create a connection to the database with Commands, Recordsets, and Datasets for interacting.</span></span> <span data-ttu-id="9f34a-116">Les résultats peuvent ensuite être liés à des champs sur l’écran sans trop de code.</span><span class="sxs-lookup"><span data-stu-id="9f34a-116">The results could then be bound to fields on screen without much code.</span></span> <span data-ttu-id="9f34a-117">L’inconvénient de cette approche était que chaque ensemble d’objets ADO.NET ( `Connection` , `Command` et `Recordset` ) était lié aux bibliothèques fournies par un fournisseur de base de données.</span><span class="sxs-lookup"><span data-stu-id="9f34a-117">The drawback of this approach was that each set of ADO.NET objects (`Connection`, `Command`, and `Recordset`) was bound to libraries provided by a database vendor.</span></span> <span data-ttu-id="9f34a-118">L’utilisation de ces composants rend le code rigide et difficile à migrer vers une autre base de données.</span><span class="sxs-lookup"><span data-stu-id="9f34a-118">Use of these components made the code rigid and difficult to migrate to a different database.</span></span>

## <a name="entity-framework"></a><span data-ttu-id="9f34a-119">Entity Framework</span><span class="sxs-lookup"><span data-stu-id="9f34a-119">Entity Framework</span></span>

<span data-ttu-id="9f34a-120">Entity Framework (EF) est l’infrastructure de mappage objet/relationnel Open source gérée par .NET Foundation.</span><span class="sxs-lookup"><span data-stu-id="9f34a-120">Entity Framework (EF) is the open source object-relational mapping framework maintained by the .NET Foundation.</span></span> <span data-ttu-id="9f34a-121">Initialement publiée avec .NET Framework, EF permet de générer du code pour les connexions de base de données, les schémas de stockage et les interactions.</span><span class="sxs-lookup"><span data-stu-id="9f34a-121">Initially released with .NET Framework, EF allows for generating code for the database connections, storage schemas, and interactions.</span></span> <span data-ttu-id="9f34a-122">Avec cette abstraction, vous pouvez vous concentrer sur les règles d’entreprise de votre application et autoriser la gestion de la base de données par un administrateur de base de données approuvé.</span><span class="sxs-lookup"><span data-stu-id="9f34a-122">With this abstraction, you can focus on your app's business rules and allow the database to be managed by a trusted database administrator.</span></span> <span data-ttu-id="9f34a-123">Dans .NET Core, vous pouvez utiliser une version mise à jour d’EF appelée EF Core.</span><span class="sxs-lookup"><span data-stu-id="9f34a-123">In .NET Core, you can use an updated version of EF called EF Core.</span></span> <span data-ttu-id="9f34a-124">EF Core permet de générer et de gérer les interactions entre votre code et la base de données avec une série de commandes qui sont disponibles pour vous à l’aide de l' `dotnet ef` outil en ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="9f34a-124">EF Core helps generate and maintain the interactions between your code and the database with a series of commands that are available for you using the `dotnet ef` command-line tool.</span></span> <span data-ttu-id="9f34a-125">Jetons un coup d’œil à quelques exemples pour vous aider à utiliser une base de données.</span><span class="sxs-lookup"><span data-stu-id="9f34a-125">Let's take a look at a few samples to get you working with a database.</span></span>

### <a name="ef-code-first"></a><span data-ttu-id="9f34a-126">Code First EF</span><span class="sxs-lookup"><span data-stu-id="9f34a-126">EF Code First</span></span>

<span data-ttu-id="9f34a-127">Un moyen rapide de commencer à créer vos interactions de base de données consiste à commencer par les objets de classe que vous souhaitez utiliser.</span><span class="sxs-lookup"><span data-stu-id="9f34a-127">A quick way to get started building your database interactions is to start with the class objects you want to work with.</span></span> <span data-ttu-id="9f34a-128">EF fournit un outil pour vous aider à générer le code de base de données approprié pour vos classes.</span><span class="sxs-lookup"><span data-stu-id="9f34a-128">EF provides a tool to help generate the appropriate database code for your classes.</span></span> <span data-ttu-id="9f34a-129">Cette approche est appelée développement « Code First ».</span><span class="sxs-lookup"><span data-stu-id="9f34a-129">This approach is called "Code First" development.</span></span> <span data-ttu-id="9f34a-130">Considérons la `Product` classe suivante pour un exemple d’application vitrine que nous voulons stocker dans une base de données relationnelle comme Microsoft SQL Server.</span><span class="sxs-lookup"><span data-stu-id="9f34a-130">Consider the following `Product` class for a sample storefront app that we want to store in a relational database like Microsoft SQL Server.</span></span>

```csharp
public class Product
{
    public int Id { get; set; }

    [Required]
    public string Name { get; set; }

    [MaxLength(4000)]
    public string Description { get; set; }

    [Range(0, 99999,99)]
    [DataType(DataType.Currency)]
    public decimal Price { get; set; }
}
```

<span data-ttu-id="9f34a-131">Le produit a une clé primaire et trois champs supplémentaires qui seraient créés dans notre base de données :</span><span class="sxs-lookup"><span data-stu-id="9f34a-131">Product has a primary key and three additional fields that would be created in our database:</span></span>  

- <span data-ttu-id="9f34a-132">EF identifie la `Id` propriété en tant que clé primaire par Convention.</span><span class="sxs-lookup"><span data-stu-id="9f34a-132">EF will identify the `Id` property as a primary key by convention.</span></span>
- <span data-ttu-id="9f34a-133">`Name` seront stockées dans une colonne configurée pour le stockage de texte.</span><span class="sxs-lookup"><span data-stu-id="9f34a-133">`Name` will be stored in a column configured for text storage.</span></span> <span data-ttu-id="9f34a-134">L' `[Required]` attribut qui décorer cette propriété ajoute une `not null` contrainte pour permettre l’application de ce comportement déclaré de la propriété.</span><span class="sxs-lookup"><span data-stu-id="9f34a-134">The `[Required]` attribute decorating this property will add a `not null` constraint to help enforce this declared behavior of the property.</span></span>
- <span data-ttu-id="9f34a-135">`Description` sont stockées dans une colonne configurée pour le stockage de texte et ont une longueur maximale configurée de 4000 caractères, comme imposé par l' `[MaxLength]` attribut.</span><span class="sxs-lookup"><span data-stu-id="9f34a-135">`Description` will be stored in a column configured for text storage, and have a maximum length configured of 4000 characters as dictated by the `[MaxLength]` attribute.</span></span> <span data-ttu-id="9f34a-136">Le schéma de base de données sera configuré avec une colonne nommée `MaxLength` à l’aide du type de données `varchar(4000)` .</span><span class="sxs-lookup"><span data-stu-id="9f34a-136">The database schema will be configured with a column named `MaxLength` using data type `varchar(4000)`.</span></span>
- <span data-ttu-id="9f34a-137">La `Price` propriété sera stockée en tant que devise.</span><span class="sxs-lookup"><span data-stu-id="9f34a-137">The `Price` property will be stored as currency.</span></span> <span data-ttu-id="9f34a-138">L' `[Range]` attribut génère des contraintes appropriées pour empêcher le stockage de données en dehors des valeurs minimales et maximales déclarées.</span><span class="sxs-lookup"><span data-stu-id="9f34a-138">The `[Range]` attribute will generate appropriate constraints to prevent data storage outside of the minimum and maximum values declared.</span></span>

<span data-ttu-id="9f34a-139">Nous devons ajouter cette `Product` classe à une classe de contexte de base de données qui définit les opérations de connexion et de traduction avec notre base de données.</span><span class="sxs-lookup"><span data-stu-id="9f34a-139">We need to add this `Product` class to a database context class that defines the connection and translation operations with our database.</span></span>

```csharp
public class MyDbContext : DbContext
{
    public DbSet<Product> Products { get; set; }
}
```

<span data-ttu-id="9f34a-140">La `MyDbContext` classe fournit la propriété qui définit l’accès et la traduction de la `Product` classe.</span><span class="sxs-lookup"><span data-stu-id="9f34a-140">The `MyDbContext` class provides the one property that defines the access and translation for the `Product` class.</span></span>  <span data-ttu-id="9f34a-141">Votre application configure cette classe pour l’interaction avec la base de données à l’aide des entrées suivantes dans la `Startup` méthode de la classe `ConfigureServices` :</span><span class="sxs-lookup"><span data-stu-id="9f34a-141">Your application configures this class for interaction with the database using the following entries in the `Startup` class's `ConfigureServices` method:</span></span>

```csharp
services.AddDbContext<MyDbContext>(options =>
    options.UseSqlServer("MY DATABASE CONNECTION STRING"));
```

<span data-ttu-id="9f34a-142">Le code précédent se connecte à une base de données SQL Server avec la chaîne de connexion spécifiée.</span><span class="sxs-lookup"><span data-stu-id="9f34a-142">The preceding code will connect to a SQL Server database with the specified connection string.</span></span> <span data-ttu-id="9f34a-143">Vous pouvez placer la chaîne de connexion dans votre *appsettings.jssur* un fichier, des variables d’environnement ou d’autres emplacements de stockage de configuration, et remplacer cette chaîne incorporée de manière appropriée.</span><span class="sxs-lookup"><span data-stu-id="9f34a-143">You can place the connection string in your *appsettings.json* file, environment variables, or other configuration storage locations and replace this embedded string appropriately.</span></span>

<span data-ttu-id="9f34a-144">Vous pouvez ensuite générer la table de base de données appropriée pour cette classe à l’aide des commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="9f34a-144">You can then generate the database table appropriate for this class using the following commands:</span></span>

```dotnetcli
dotnet ef migrations add 'Create Product table'
dotnet ef database update
```

<span data-ttu-id="9f34a-145">La première commande définit les modifications que vous apportez au schéma de base de données en tant que nouvelle migration EF appelée `Create Product table` .</span><span class="sxs-lookup"><span data-stu-id="9f34a-145">The first command defines the changes you're making to the database schema as a new EF Migration called `Create Product table`.</span></span>  <span data-ttu-id="9f34a-146">Une migration définit comment appliquer et supprimer vos nouvelles modifications de base de données.</span><span class="sxs-lookup"><span data-stu-id="9f34a-146">A Migration defines how to apply and remove your new database changes.</span></span>

<span data-ttu-id="9f34a-147">Une fois l’application appliquée, vous disposez d’une `Product` table simple dans votre base de données et de nouvelles classes ajoutées au projet pour aider à gérer le schéma de base de données.</span><span class="sxs-lookup"><span data-stu-id="9f34a-147">Once applied, you have a simple `Product` table in your database and some new classes added to the project that help manage the database schema.</span></span>  <span data-ttu-id="9f34a-148">Vous trouverez ces classes générées, par défaut, dans un nouveau dossier nommé *migrations*.</span><span class="sxs-lookup"><span data-stu-id="9f34a-148">You can find these generated classes, by default, in a new folder called *Migrations*.</span></span>  <span data-ttu-id="9f34a-149">Lorsque vous apportez des modifications à la `Product` classe ou ajoutez des classes connexes que vous souhaitez interagir avec votre base de données, vous devez réexécuter les commandes de ligne de commande avec un nouveau nom de migration.</span><span class="sxs-lookup"><span data-stu-id="9f34a-149">When you make changes to the `Product` class or add more related classes you would like interacting with your database, you need to run the command-line commands again with a new name of the migration.</span></span>  <span data-ttu-id="9f34a-150">Cette commande génère un autre ensemble de classes de migration pour mettre à jour votre schéma de base de données.</span><span class="sxs-lookup"><span data-stu-id="9f34a-150">This command will generate another set of migration classes to update your database schema.</span></span>

### <a name="ef-database-first"></a><span data-ttu-id="9f34a-151">Database First EF</span><span class="sxs-lookup"><span data-stu-id="9f34a-151">EF Database First</span></span>

<span data-ttu-id="9f34a-152">Pour les bases de données existantes, vous pouvez générer les classes pour EF Core à l’aide des outils en ligne de commande .NET.</span><span class="sxs-lookup"><span data-stu-id="9f34a-152">For existing databases, you can generate the classes for EF Core by using the .NET command-line tools.</span></span> <span data-ttu-id="9f34a-153">Pour générer un modèle de structure des classes, utilisez une variante de la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="9f34a-153">To scaffold the classes, use a variation of the following command:</span></span>

```dotnetcli
dotnet ef dbcontext scaffold "CONNECTION STRING" Microsoft.EntityFrameworkCore.SqlServer -c MyDbContext -t Product -t Customer
```

<span data-ttu-id="9f34a-154">La commande précédente se connecte à la base de données à l’aide de la chaîne de connexion et du fournisseur spécifiés `Microsoft.EntityFrameworkCore.SqlServer` .</span><span class="sxs-lookup"><span data-stu-id="9f34a-154">The preceding command connects to the database using the specified connection string and the `Microsoft.EntityFrameworkCore.SqlServer` provider.</span></span> <span data-ttu-id="9f34a-155">Une fois connecté, une classe de contexte de base de données nommée `MyDbContext` est créée.</span><span class="sxs-lookup"><span data-stu-id="9f34a-155">Once connected, a database context class named `MyDbContext` is created.</span></span> <span data-ttu-id="9f34a-156">En outre, les classes de prise en charge sont créées pour les `Product` `Customer` tables et qui ont été spécifiées avec les `-t` options.</span><span class="sxs-lookup"><span data-stu-id="9f34a-156">Additionally, supporting classes are created for the `Product` and `Customer` tables that were specified with the `-t` options.</span></span> <span data-ttu-id="9f34a-157">Il existe de nombreuses options de configuration pour cette commande afin de générer la hiérarchie de classes appropriée pour votre base de données.</span><span class="sxs-lookup"><span data-stu-id="9f34a-157">There are many configuration options for this command to generate the class hierarchy appropriate for your database.</span></span> <span data-ttu-id="9f34a-158">Pour obtenir une référence complète, consultez [la documentation de la commande](/ef/core/miscellaneous/cli/dotnet#dotnet-ef-dbcontext-scaffold).</span><span class="sxs-lookup"><span data-stu-id="9f34a-158">For a complete reference, see [the command's documentation](/ef/core/miscellaneous/cli/dotnet#dotnet-ef-dbcontext-scaffold).</span></span>

<span data-ttu-id="9f34a-159">Vous trouverez plus d’informations sur [EF Core](/ef/core/) sur le site Microsoft docs.</span><span class="sxs-lookup"><span data-stu-id="9f34a-159">More information about [EF Core](/ef/core/) can be found on the Microsoft Docs site.</span></span>

## <a name="interact-with-web-services"></a><span data-ttu-id="9f34a-160">Interagir avec les services Web</span><span class="sxs-lookup"><span data-stu-id="9f34a-160">Interact with web services</span></span>

<span data-ttu-id="9f34a-161">Lorsque ASP.NET a été publié pour la première fois, les services SOAP étaient le meilleur moyen pour les serveurs Web et les clients d’échanger des données.</span><span class="sxs-lookup"><span data-stu-id="9f34a-161">When ASP.NET was first released, SOAP services were the preferred way for web servers and clients to exchange data.</span></span> <span data-ttu-id="9f34a-162">De nombreuses modifications ont été apportées depuis ce moment, et les interactions préférées avec les services ont été déplacées vers les interactions directes du client HTTP.</span><span class="sxs-lookup"><span data-stu-id="9f34a-162">Much has changed since that time, and the preferred interactions with services have shifted to direct HTTP client interactions.</span></span> <span data-ttu-id="9f34a-163">Avec ASP.NET Core et Blazor , vous pouvez inscrire la configuration de votre `HttpClient` dans la `Startup` méthode de la classe `ConfigureServices` .</span><span class="sxs-lookup"><span data-stu-id="9f34a-163">With ASP.NET Core and Blazor, you can register the configuration of your `HttpClient` in the `Startup` class's `ConfigureServices` method.</span></span> <span data-ttu-id="9f34a-164">Utilisez cette configuration lorsque vous devez interagir avec le point de terminaison HTTP.</span><span class="sxs-lookup"><span data-stu-id="9f34a-164">Use that configuration when you need to interact with the HTTP endpoint.</span></span> <span data-ttu-id="9f34a-165">Considérez le code de configuration suivant :</span><span class="sxs-lookup"><span data-stu-id="9f34a-165">Consider the following configuration code:</span></span>

```csharp
services.AddHttpClient("github", client =>
{
    client.BaseAddress = new Uri("http://api.github.com/");
    // Github API versioning
    client.DefaultRequestHeaders.Add("Accept", "application/vnd.github.v3+json");
    // Github requires a user-agent
    client.DefaultRequestHeaders.Add("User-Agent", "BlazorWebForms-Sample");
});
```

<span data-ttu-id="9f34a-166">Chaque fois que vous devez accéder aux données à partir de GitHub, créez un client avec le nom `github` .</span><span class="sxs-lookup"><span data-stu-id="9f34a-166">Whenever you need to access data from GitHub, create a client with a name of `github`.</span></span> <span data-ttu-id="9f34a-167">Le client est configuré avec l’adresse de base et les en-têtes de demande sont correctement définis.</span><span class="sxs-lookup"><span data-stu-id="9f34a-167">The client is configured with the base address, and the request headers are set appropriately.</span></span> <span data-ttu-id="9f34a-168">Injectez `IHttpClientFactory` dans vos Blazor composants avec la `@inject` directive ou un `[Inject]` attribut sur une propriété.</span><span class="sxs-lookup"><span data-stu-id="9f34a-168">Inject the `IHttpClientFactory` into your Blazor components with the `@inject` directive or an `[Inject]` attribute on a property.</span></span> <span data-ttu-id="9f34a-169">Créez votre client nommé et interagissez avec les services à l’aide de la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="9f34a-169">Create your named client and interact with services using the following syntax:</span></span>

```razor
@inject IHttpClientFactory factory

...

@code {
    protected override async Task OnInitializedAsync()
    {
        var client = factory.CreateClient("github");
        var response = await client.GetAsync("repos/dotnet/docs/issues");
        response.EnsureStatusCode();
        var content = async response.Content.ReadAsStringAsync();
    }
}
```

<span data-ttu-id="9f34a-170">Cette méthode retourne la chaîne décrivant la collection de problèmes dans le référentiel GitHub *dotnet/docs* .</span><span class="sxs-lookup"><span data-stu-id="9f34a-170">This method returns the string describing the collection of issues in the *dotnet/docs* GitHub repository.</span></span> <span data-ttu-id="9f34a-171">Elle retourne le contenu au format JSON et est désérialisée en objets de problème GitHub appropriés.</span><span class="sxs-lookup"><span data-stu-id="9f34a-171">It returns content in JSON format and is deserialized into appropriate GitHub issue objects.</span></span> <span data-ttu-id="9f34a-172">Il existe de nombreuses façons de configurer le `HttpClientFactory` pour fournir des objets préconfigurés `HttpClient` .</span><span class="sxs-lookup"><span data-stu-id="9f34a-172">There are many ways that you can configure the `HttpClientFactory` to deliver preconfigured `HttpClient` objects.</span></span> <span data-ttu-id="9f34a-173">Essayez de configurer plusieurs `HttpClient` instances avec des noms et des points de terminaison différents pour les différents services Web que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="9f34a-173">Try configuring multiple `HttpClient` instances with different names and endpoints for the various web services you work with.</span></span> <span data-ttu-id="9f34a-174">Cette approche rendra vos interactions avec ces services plus faciles à utiliser sur chaque page.</span><span class="sxs-lookup"><span data-stu-id="9f34a-174">This approach will make your interactions with those services easier to work with on each page.</span></span> <span data-ttu-id="9f34a-175">Pour plus d’informations, consultez [la documentation de IHttpClientFactory](/aspnet/core/fundamentals/http-requests).</span><span class="sxs-lookup"><span data-stu-id="9f34a-175">For more details, read [the documentation for the IHttpClientFactory](/aspnet/core/fundamentals/http-requests).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="9f34a-176">[Précédent](forms-validation.md) 
> [Suivant](middleware.md)</span><span class="sxs-lookup"><span data-stu-id="9f34a-176">[Previous](forms-validation.md)
[Next](middleware.md)</span></span>
