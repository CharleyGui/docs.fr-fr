---
title: Migrer de ASP.NET Web Forms vers Blazor
description: Découvrez comment aborder la migration d’une application Web Forms ASP.NET existante vers Blazor .
author: twsouthwick
ms.author: tasou
no-loc:
- Blazor
- WebAssembly
ms.date: 09/19/2019
ms.openlocfilehash: ca3d8747b02602c89aec187ea0826e658fb0cbc4
ms.sourcegitcommit: 0100be20fcf23f61dab672deced70059ed71bb2e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88267800"
---
# <a name="migrate-from-aspnet-web-forms-to-no-locblazor"></a><span data-ttu-id="1f4e3-103">Migrer de ASP.NET Web Forms vers Blazor</span><span class="sxs-lookup"><span data-stu-id="1f4e3-103">Migrate from ASP.NET Web Forms to Blazor</span></span>

<span data-ttu-id="1f4e3-104">La migration d’une base de code à partir de ASP.NET Web Forms vers Blazor est une tâche longue qui nécessite une planification.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-104">Migrating a code base from ASP.NET Web Forms to Blazor is a time-consuming task that requires planning.</span></span> <span data-ttu-id="1f4e3-105">Ce chapitre décrit le processus.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-105">This chapter outlines the process.</span></span> <span data-ttu-id="1f4e3-106">Une opération qui peut faciliter la transition consiste à s’assurer que l’application adhère à une architecture *multiniveau* , dans laquelle le modèle d’application (dans ce cas, Web Forms) est séparé de la logique métier.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-106">Something that can ease the transition is to ensure the app adheres to an *N-tier* architecture, wherein the app model (in this case, Web Forms) is separate from the business logic.</span></span> <span data-ttu-id="1f4e3-107">Cette séparation logique des couches permet de clarifier ce qui doit être déplacé vers .NET Core et Blazor .</span><span class="sxs-lookup"><span data-stu-id="1f4e3-107">This logical separation of layers makes it clear what needs to move to .NET Core and Blazor.</span></span>

<span data-ttu-id="1f4e3-108">Pour cet exemple, l’application eShop disponible sur [GitHub](https://github.com/dotnet-architecture/eShopOnBlazor) est utilisée.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-108">For this example, the eShop app available on [GitHub](https://github.com/dotnet-architecture/eShopOnBlazor) is used.</span></span> <span data-ttu-id="1f4e3-109">eShop est un service de catalogue qui fournit des fonctionnalités CRUD via la saisie et la validation de formulaire.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-109">eShop is a catalog service that provides CRUD capabilities via form entry and validation.</span></span>

<span data-ttu-id="1f4e3-110">Pourquoi une application de travail doit-elle être migrée vers Blazor ?</span><span class="sxs-lookup"><span data-stu-id="1f4e3-110">Why should a working app be migrated to Blazor?</span></span> <span data-ttu-id="1f4e3-111">Bien souvent, il n’y a aucun besoin.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-111">Many times, there's no need.</span></span> <span data-ttu-id="1f4e3-112">ASP.NET Web Forms sera toujours pris en charge depuis de nombreuses années.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-112">ASP.NET Web Forms will continue to be supported for many years.</span></span> <span data-ttu-id="1f4e3-113">Toutefois, la plupart des fonctionnalités Blazor fournies par ne sont prises en charge que sur une application migrée.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-113">However, many of the features that Blazor provides are only supported on a migrated app.</span></span> <span data-ttu-id="1f4e3-114">Ces fonctionnalités sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="1f4e3-114">Such features include:</span></span>

- <span data-ttu-id="1f4e3-115">Améliorations des performances dans l’infrastructure, telles que `Span<T>`</span><span class="sxs-lookup"><span data-stu-id="1f4e3-115">Performance improvements in the framework such as `Span<T>`</span></span>
- <span data-ttu-id="1f4e3-116">Possibilité de s’exécuter en tant que WebAssembly</span><span class="sxs-lookup"><span data-stu-id="1f4e3-116">Ability to run as WebAssembly</span></span>
- <span data-ttu-id="1f4e3-117">Prise en charge multiplateforme pour Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="1f4e3-117">Cross-platform support for Linux and macOS</span></span>
- <span data-ttu-id="1f4e3-118">Déploiement local de l’application ou déploiement d’infrastructure partagée sans impact sur les autres applications</span><span class="sxs-lookup"><span data-stu-id="1f4e3-118">App-local deployment or shared framework deployment without impacting other apps</span></span>

<span data-ttu-id="1f4e3-119">Si ces nouvelles fonctionnalités ou d’autres sont suffisamment intéressantes, il peut y avoir une valeur pour la migration de l’application.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-119">If these or other new features are compelling enough, there may be value in migrating the app.</span></span> <span data-ttu-id="1f4e3-120">La migration peut prendre différentes formes. Il peut s’agir de l’application entière, ou uniquement de certains points de terminaison qui requièrent des modifications.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-120">The migration can take different shapes; it can be the entire app, or only certain endpoints that require the changes.</span></span> <span data-ttu-id="1f4e3-121">La décision de migrer est en fin de compte sur les problèmes d’entreprise à résoudre par le développeur.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-121">The decision to migrate is ultimately based on the business problems to be solved by the developer.</span></span>

## <a name="server-side-versus-client-side-hosting"></a><span data-ttu-id="1f4e3-122">Côté serveur et hébergement côté client</span><span class="sxs-lookup"><span data-stu-id="1f4e3-122">Server-side versus client-side hosting</span></span>

<span data-ttu-id="1f4e3-123">Comme décrit dans le chapitre [modèles d’hébergement](hosting-models.md) , une Blazor application peut être hébergée de deux façons différentes : côté serveur et côté client.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-123">As described in the [hosting models](hosting-models.md) chapter, a Blazor app can be hosted in two different ways: server-side and client-side.</span></span> <span data-ttu-id="1f4e3-124">Le modèle côté serveur utilise des connexions ASP.NET Core Signalr pour gérer les mises à jour du modèle DOM tout en exécutant du code réel sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-124">The server-side model uses ASP.NET Core SignalR connections to manage the DOM updates while running any actual code on the server.</span></span> <span data-ttu-id="1f4e3-125">Le modèle côté client s’exécute comme WebAssembly dans un navigateur et ne nécessite pas de connexion au serveur.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-125">The client-side model runs as WebAssembly within a browser and requires no server connections.</span></span> <span data-ttu-id="1f4e3-126">Il existe un certain nombre de différences qui peuvent affecter la meilleure solution pour une application spécifique :</span><span class="sxs-lookup"><span data-stu-id="1f4e3-126">There are a number of differences that may affect which is best for a specific app:</span></span>

- <span data-ttu-id="1f4e3-127">L’exécution de en tant que WebAssembly est toujours en cours de développement et peut ne pas prendre en charge toutes les fonctionnalités (telles que le Threading) à l’heure actuelle.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-127">Running as WebAssembly is still in development and may not support all features (such as threading) at the current time</span></span>
- <span data-ttu-id="1f4e3-128">Une communication bavard entre le client et le serveur peut entraîner des problèmes de latence en mode côté serveur</span><span class="sxs-lookup"><span data-stu-id="1f4e3-128">Chatty communication between the client and server may cause latency issues in server-side mode</span></span>
- <span data-ttu-id="1f4e3-129">L’accès aux bases de données et aux services internes ou protégés requiert un service distinct avec l’hébergement côté client</span><span class="sxs-lookup"><span data-stu-id="1f4e3-129">Access to databases and internal or protected services require a separate service with client-side hosting</span></span>

<span data-ttu-id="1f4e3-130">Au moment de l’écriture, le modèle côté serveur ressemble davantage à Web Forms.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-130">At the time of writing, the server-side model more closely resembles Web Forms.</span></span> <span data-ttu-id="1f4e3-131">La majeure partie de ce chapitre se concentre sur le modèle d’hébergement côté serveur, car il est prêt pour la production.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-131">Most of this chapter focuses on the server-side hosting model, as it's production-ready.</span></span>

## <a name="create-a-new-project"></a><span data-ttu-id="1f4e3-132">Créer un projet</span><span class="sxs-lookup"><span data-stu-id="1f4e3-132">Create a new project</span></span>

<span data-ttu-id="1f4e3-133">Cette étape de migration initiale consiste à créer un nouveau projet.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-133">This initial migration step is to create a new project.</span></span> <span data-ttu-id="1f4e3-134">Ce type de projet est basé sur les projets de style SDK de .NET Core et simplifie la plupart des modèles utilisés dans les formats de projet précédents.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-134">This project type is based on the SDK style projects of .NET Core and simplifies much of the boilerplate that was used in previous project formats.</span></span> <span data-ttu-id="1f4e3-135">Pour plus d’informations, consultez le chapitre sur la [structure de projet](project-structure.md).</span><span class="sxs-lookup"><span data-stu-id="1f4e3-135">For more detail, please see the chapter on [Project Structure](project-structure.md).</span></span>

<span data-ttu-id="1f4e3-136">Une fois le projet créé, installez les bibliothèques qui ont été utilisées dans le projet précédent.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-136">Once the project has been created, install the libraries that were used in the previous project.</span></span> <span data-ttu-id="1f4e3-137">Dans les projets de Web Forms plus anciens, vous avez peut-être utilisé le fichier *packages.config* pour répertorier les packages NuGet requis.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-137">In older Web Forms projects, you may have used the *packages.config* file to list the required NuGet packages.</span></span> <span data-ttu-id="1f4e3-138">Dans le nouveau projet de type SDK, *packages.config* a été remplacé par des `<PackageReference>` éléments dans le fichier projet.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-138">In the new SDK-style project, *packages.config* has been replaced with `<PackageReference>` elements in the project file.</span></span> <span data-ttu-id="1f4e3-139">L’avantage de cette approche est que toutes les dépendances sont installées de manière transitive.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-139">A benefit to this approach is that all dependencies are installed transitively.</span></span> <span data-ttu-id="1f4e3-140">Vous répertoriez uniquement les dépendances de niveau supérieur qui vous intéressent.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-140">You only list the top-level dependencies you care about.</span></span>

<span data-ttu-id="1f4e3-141">La plupart des dépendances que vous utilisez sont disponibles pour .NET Core, y compris Entity Framework 6 et log4net.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-141">Many of the dependencies you're using are available for .NET Core, including Entity Framework 6 and log4net.</span></span> <span data-ttu-id="1f4e3-142">Si aucune version de .NET Core ou de .NET Standard n’est disponible, la version .NET Framework peut souvent être utilisée.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-142">If there's no .NET Core or .NET Standard version available, the .NET Framework version can often be used.</span></span> <span data-ttu-id="1f4e3-143">Votre kilométrage peut varier.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-143">Your mileage may vary.</span></span> <span data-ttu-id="1f4e3-144">Toute API utilisée qui n’est pas disponible dans .NET Core provoque une erreur d’exécution.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-144">Any API used that isn't available in .NET Core causes a runtime error.</span></span> <span data-ttu-id="1f4e3-145">Visual Studio vous avertit de ces packages.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-145">Visual Studio notifies you of such packages.</span></span> <span data-ttu-id="1f4e3-146">Une icône jaune apparaît sur le nœud **références** du projet dans **Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-146">A yellow icon appears on the project's **References** node in **Solution Explorer**.</span></span>

<span data-ttu-id="1f4e3-147">Dans le Blazor projet eShop basé sur, vous pouvez voir les packages qui sont installés.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-147">In the Blazor-based eShop project, you can see the packages that are installed.</span></span> <span data-ttu-id="1f4e3-148">Précédemment, le fichier *packages.config* répertorie chaque package utilisé dans le projet, ce qui a pour résultat un fichier d’une longueur de 50 lignes.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-148">Previously, the *packages.config* file listed every package used in the project, resulting in a file almost 50 lines long.</span></span> <span data-ttu-id="1f4e3-149">Un extrait de *packages.config* est :</span><span class="sxs-lookup"><span data-stu-id="1f4e3-149">A snippet of *packages.config* is:</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<packages>
  ...
  <package id="Microsoft.ApplicationInsights.Agent.Intercept" version="2.4.0" targetFramework="net472" />
  <package id="Microsoft.ApplicationInsights.DependencyCollector" version="2.9.1" targetFramework="net472" />
  <package id="Microsoft.ApplicationInsights.PerfCounterCollector" version="2.9.1" targetFramework="net472" />
  <package id="Microsoft.ApplicationInsights.Web" version="2.9.1" targetFramework="net472" />
  <package id="Microsoft.ApplicationInsights.WindowsServer" version="2.9.1" targetFramework="net472" />
  <package id="Microsoft.ApplicationInsights.WindowsServer.TelemetryChannel" version="2.9.1" targetFramework="net472" />
  <package id="Microsoft.AspNet.FriendlyUrls" version="1.0.2" targetFramework="net472" />
  <package id="Microsoft.AspNet.FriendlyUrls.Core" version="1.0.2" targetFramework="net472" />
  <package id="Microsoft.AspNet.ScriptManager.MSAjax" version="5.0.0" targetFramework="net472" />
  <package id="Microsoft.AspNet.ScriptManager.WebForms" version="5.0.0" targetFramework="net472" />
  ...
  <package id="System.Memory" version="4.5.1" targetFramework="net472" />
  <package id="System.Numerics.Vectors" version="4.4.0" targetFramework="net472" />
  <package id="System.Runtime.CompilerServices.Unsafe" version="4.5.0" targetFramework="net472" />
  <package id="System.Threading.Channels" version="4.5.0" targetFramework="net472" />
  <package id="System.Threading.Tasks.Extensions" version="4.5.1" targetFramework="net472" />
  <package id="WebGrease" version="1.6.0" targetFramework="net472" />
</packages>
```

<span data-ttu-id="1f4e3-150">L' `<packages>` élément comprend toutes les dépendances nécessaires.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-150">The `<packages>` element includes all necessary dependencies.</span></span> <span data-ttu-id="1f4e3-151">Il est difficile d’identifier les packages qui sont inclus, car vous en avez besoin.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-151">It's difficult to identify which of these packages are included because you require them.</span></span> <span data-ttu-id="1f4e3-152">Certains `<package>` éléments sont répertoriés simplement pour répondre aux besoins des dépendances dont vous avez besoin.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-152">Some `<package>` elements are listed simply to satisfy the needs of dependencies you require.</span></span>

<span data-ttu-id="1f4e3-153">Le Blazor projet répertorie les dépendances dont vous avez besoin dans un `<ItemGroup>` élément du fichier projet :</span><span class="sxs-lookup"><span data-stu-id="1f4e3-153">The Blazor project lists the dependencies you require within an `<ItemGroup>` element in the project file:</span></span>

```xml
<ItemGroup>
    <PackageReference Include="Autofac" Version="4.9.3" />
    <PackageReference Include="EntityFramework" Version="6.3.0-preview9-19423-04" />
    <PackageReference Include="log4net" Version="2.0.8" />
</ItemGroup>
```

<span data-ttu-id="1f4e3-154">Un package NuGet qui simplifie la vie des développeurs Web Forms est le [Pack de compatibilité Windows](../../core/porting/windows-compat-pack.md).</span><span class="sxs-lookup"><span data-stu-id="1f4e3-154">One NuGet package that simplifies the life of Web Forms developers is the [Windows Compatibility Pack](../../core/porting/windows-compat-pack.md).</span></span> <span data-ttu-id="1f4e3-155">Bien que .NET Core soit multiplateforme, certaines fonctionnalités sont uniquement disponibles sur Windows.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-155">Although .NET Core is cross-platform, some features are only available on Windows.</span></span> <span data-ttu-id="1f4e3-156">Les fonctionnalités spécifiques à Windows sont mises à disposition en installant le Pack de compatibilité.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-156">Windows-specific features are made available by installing the compatibility pack.</span></span> <span data-ttu-id="1f4e3-157">Le registre, WMI et les services d’annuaire sont des exemples de ces fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-157">Examples of such features include the Registry, WMI, and Directory Services.</span></span> <span data-ttu-id="1f4e3-158">Le package ajoute environ 20 000 API et active de nombreux services que vous connaissez peut-être déjà.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-158">The package adds around 20,000 APIs and activates many services with which you may already be familiar.</span></span> <span data-ttu-id="1f4e3-159">Le projet eShop ne nécessite pas le Pack de compatibilité. Toutefois, si vos projets utilisent des fonctionnalités propres à Windows, le package facilite les efforts de migration.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-159">The eShop project doesn't require the compatibility pack; but if your projects use Windows-specific features, the package eases the migration efforts.</span></span>

## <a name="enable-startup-process"></a><span data-ttu-id="1f4e3-160">Activer le processus de démarrage</span><span class="sxs-lookup"><span data-stu-id="1f4e3-160">Enable startup process</span></span>

<span data-ttu-id="1f4e3-161">Le processus de démarrage de Blazor a été modifié à partir de Web Forms et suit une configuration similaire pour d’autres services ASP.net core.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-161">The startup process for Blazor has changed from Web Forms and follows a similar setup for other ASP.NET Core services.</span></span> <span data-ttu-id="1f4e3-162">Lorsqu’ils sont hébergés côté serveur, les Blazor composants sont exécutés dans le cadre d’une application ASP.net Core normale.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-162">When hosted server-side, Blazor components are run as part of a normal ASP.NET Core app.</span></span> <span data-ttu-id="1f4e3-163">Lorsqu’ils sont hébergés dans le navigateur avec WebAssembly , les Blazor composants utilisent un modèle d’hébergement similaire.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-163">When hosted in the browser with WebAssembly, Blazor components use a similar hosting model.</span></span> <span data-ttu-id="1f4e3-164">La différence réside dans le fait que les composants sont exécutés en tant que service distinct à partir de l’un des processus principaux.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-164">The difference is the components are run as a separate service from any of the backend processes.</span></span> <span data-ttu-id="1f4e3-165">Dans les deux cas, le démarrage est similaire.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-165">Either way, the startup is similar.</span></span>

<span data-ttu-id="1f4e3-166">Le fichier *global.asax.cs* est la page de démarrage par défaut pour les projets Web Forms.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-166">The *Global.asax.cs* file is the default startup page for Web Forms projects.</span></span> <span data-ttu-id="1f4e3-167">Dans le projet eShop, ce fichier configure le conteneur d’inversion de contrôle (IoC, inversion of Control) et gère les différents événements de cycle de vie de l’application ou de la demande.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-167">In the eShop project, this file configures the Inversion of Control (IoC) container and handles the various lifecycle events of the app or request.</span></span> <span data-ttu-id="1f4e3-168">Certains de ces événements sont gérés avec l’intergiciel (par exemple, `Application_BeginRequest` ).</span><span class="sxs-lookup"><span data-stu-id="1f4e3-168">Some of these events are handled with middleware (such as `Application_BeginRequest`).</span></span> <span data-ttu-id="1f4e3-169">D’autres événements requièrent la substitution de services spécifiques par le biais de l’injection de dépendances (DI).</span><span class="sxs-lookup"><span data-stu-id="1f4e3-169">Other events require the overriding of specific services via dependency injection (DI).</span></span>

<span data-ttu-id="1f4e3-170">Par exemple, le fichier *global.asax.cs* pour eShop contient le code suivant :</span><span class="sxs-lookup"><span data-stu-id="1f4e3-170">By way of example, the *Global.asax.cs* file for eShop, contains the following code:</span></span>

```csharp
public class Global : HttpApplication, IContainerProviderAccessor
{
    private static readonly ILog _log = LogManager.GetLogger(System.Reflection.MethodBase.GetCurrentMethod().DeclaringType);

    static IContainerProvider _containerProvider;
    IContainer container;

    public IContainerProvider ContainerProvider
    {
        get { return _containerProvider; }
    }

    protected void Application_Start(object sender, EventArgs e)
    {
        // Code that runs on app startup
        RouteConfig.RegisterRoutes(RouteTable.Routes);
        BundleConfig.RegisterBundles(BundleTable.Bundles);
        ConfigureContainer();
        ConfigDataBase();
    }

    /// <summary>
    /// Track the machine name and the start time for the session inside the current session
    /// </summary>
    protected void Session_Start(Object sender, EventArgs e)
    {
        HttpContext.Current.Session["MachineName"] = Environment.MachineName;
        HttpContext.Current.Session["SessionStartTime"] = DateTime.Now;
    }

    /// <summary>
    /// https://autofaccn.readthedocs.io/en/latest/integration/webforms.html
    /// </summary>
    private void ConfigureContainer()
    {
        var builder = new ContainerBuilder();
        var mockData = bool.Parse(ConfigurationManager.AppSettings["UseMockData"]);
        builder.RegisterModule(new ApplicationModule(mockData));
        container = builder.Build();
        _containerProvider = new ContainerProvider(container);
    }

    private void ConfigDataBase()
    {
        var mockData = bool.Parse(ConfigurationManager.AppSettings["UseMockData"]);

        if (!mockData)
        {
            Database.SetInitializer<CatalogDBContext>(container.Resolve<CatalogDBInitializer>());
        }
    }

    protected void Application_BeginRequest(object sender, EventArgs e)
    {
        //set the property to our new object
        LogicalThreadContext.Properties["activityid"] = new ActivityIdHelper();

        LogicalThreadContext.Properties["requestinfo"] = new WebRequestInfo();

        _log.Debug("Application_BeginRequest");
    }
}
```

<span data-ttu-id="1f4e3-171">Le fichier précédent devient la `Startup` classe côté serveur Blazor :</span><span class="sxs-lookup"><span data-stu-id="1f4e3-171">The preceding file becomes the `Startup` class in server-side Blazor:</span></span>

```csharp
public class Startup
{
    public Startup(IConfiguration configuration, IWebHostEnvironment env)
    {
        Configuration = configuration;
        Env = env;
    }

    public IConfiguration Configuration { get; }

    public IWebHostEnvironment Env { get; }

    // This method gets called by the runtime. Use this method to add services to the container.
    // For more information on how to configure your application, visit https://go.microsoft.com/fwlink/?LinkID=398940
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddRazorPages();
        services.AddServerSideBlazor();

        if (Configuration.GetValue<bool>("UseMockData"))
        {
            services.AddSingleton<ICatalogService, CatalogServiceMock>();
        }
        else
        {
            services.AddScoped<ICatalogService, CatalogService>();
            services.AddScoped<IDatabaseInitializer<CatalogDBContext>, CatalogDBInitializer>();
            services.AddSingleton<CatalogItemHiLoGenerator>();
            services.AddScoped(_ => new CatalogDBContext(Configuration.GetConnectionString("CatalogDBContext")));
        }
    }

    // This method gets called by the runtime. Use this method to configure the HTTP request pipeline.
    public void Configure(IApplicationBuilder app, ILoggerFactory loggerFactory)
    {
        loggerFactory.AddLog4Net("log4Net.xml");

        if (Env.IsDevelopment())
        {
            app.UseDeveloperExceptionPage();
        }
        else
        {
            app.UseExceptionHandler("/Home/Error");
        }

        // Middleware for Application_BeginRequest
        app.Use((ctx, next) =>
        {
            LogicalThreadContext.Properties["activityid"] = new ActivityIdHelper(ctx);
            LogicalThreadContext.Properties["requestinfo"] = new WebRequestInfo(ctx);
            return next();
        });

        app.UseStaticFiles();

        app.UseRouting();

        app.UseEndpoints(endpoints =>
        {
            endpoints.MapBlazorHub();
            endpoints.MapFallbackToPage("/_Host");
        });

        ConfigDataBase(app);
    }

    private void ConfigDataBase(IApplicationBuilder app)
    {
        using (var scope = app.ApplicationServices.CreateScope())
        {
            var initializer = scope.ServiceProvider.GetService<IDatabaseInitializer<CatalogDBContext>>();

            if (initializer != null)
            {
                Database.SetInitializer(initializer);
            }
        }
    }
}
```

<span data-ttu-id="1f4e3-172">L’une des modifications importantes que vous pouvez remarquer à partir de Web Forms est l’importance de DI.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-172">One significant change you may notice from Web Forms is the prominence of DI.</span></span> <span data-ttu-id="1f4e3-173">DI est un principe de GUID dans la conception de la ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-173">DI has been a guiding principle in the ASP.NET Core design.</span></span> <span data-ttu-id="1f4e3-174">Il prend en charge la personnalisation de presque tous les aspects de l’infrastructure ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-174">It supports customization of almost all aspects of the ASP.NET Core framework.</span></span> <span data-ttu-id="1f4e3-175">Il existe même un fournisseur de services intégré qui peut être utilisé pour de nombreux scénarios.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-175">There's even a built-in service provider that can be used for many scenarios.</span></span> <span data-ttu-id="1f4e3-176">Si une personnalisation supplémentaire est nécessaire, elle peut être prise en charge par les nombreux projets de la communauté.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-176">If more customization is required, it can be supported by the many community projects.</span></span> <span data-ttu-id="1f4e3-177">Par exemple, vous pouvez transférer votre investissement de bibliothèque DI tiers.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-177">For example, you can carry forward your third-party DI library investment.</span></span>

<span data-ttu-id="1f4e3-178">Dans l’application eShop d’origine, il existe une certaine configuration pour la gestion des sessions.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-178">In the original eShop app, there's some configuration for session management.</span></span> <span data-ttu-id="1f4e3-179">Étant donné que Blazor l’utilisation côté serveur ASP.net Core signalr pour la communication, l’état de session n’est pas pris en charge, car les connexions peuvent se produire indépendamment d’un contexte http.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-179">Since server-side Blazor uses ASP.NET Core SignalR for communication, session state isn't supported as the connections may occur independent of an HTTP context.</span></span> <span data-ttu-id="1f4e3-180">Une application qui utilise l’état de session doit être remaniée avant d’être exécutée en tant qu' Blazor application.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-180">An app that uses session state requires rearchitecting before running as a Blazor app.</span></span>

<span data-ttu-id="1f4e3-181">Pour plus d’informations sur le démarrage de l’application, consultez démarrage de l' [application](app-startup.md).</span><span class="sxs-lookup"><span data-stu-id="1f4e3-181">For more information about app startup, see [App startup](app-startup.md).</span></span>

## <a name="migrate-http-modules-and-handlers-to-middleware"></a><span data-ttu-id="1f4e3-182">Migrer des modules et gestionnaires HTTP vers des intergiciels (middleware)</span><span class="sxs-lookup"><span data-stu-id="1f4e3-182">Migrate HTTP modules and handlers to middleware</span></span>

<span data-ttu-id="1f4e3-183">Les modules et gestionnaires HTTP sont des modèles courants dans Web Forms pour contrôler le pipeline de requête HTTP.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-183">HTTP modules and handlers are common patterns in Web Forms to control the HTTP request pipeline.</span></span> <span data-ttu-id="1f4e3-184">Les classes qui implémentent `IHttpModule` ou `IHttpHandler` peuvent être inscrites et traiter les demandes entrantes.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-184">Classes that implement `IHttpModule` or `IHttpHandler` could be registered and process incoming requests.</span></span> <span data-ttu-id="1f4e3-185">Web Forms configure des modules et des gestionnaires dans le fichier *web.config* .</span><span class="sxs-lookup"><span data-stu-id="1f4e3-185">Web Forms configures modules and handlers in the *web.config* file.</span></span> <span data-ttu-id="1f4e3-186">Web Forms est également fortement basé sur la gestion des événements du cycle de vie des applications.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-186">Web Forms is also heavily based on app lifecycle event handling.</span></span> <span data-ttu-id="1f4e3-187">ASP.NET Core utilise à la place intergiciel.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-187">ASP.NET Core uses middleware instead.</span></span> <span data-ttu-id="1f4e3-188">L’intergiciel est inscrit dans la `Configure` méthode de la `Startup` classe.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-188">Middleware is registered in the `Configure` method of the `Startup` class.</span></span> <span data-ttu-id="1f4e3-189">L’ordre d’exécution des intergiciels est déterminé par l’ordre d’enregistrement.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-189">Middleware execution order is determined by the registration order.</span></span>

<span data-ttu-id="1f4e3-190">Dans la section [activer le processus de démarrage](#enable-startup-process) , un événement de cycle de vie a été déclenché par Web Forms comme `Application_BeginRequest` méthode.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-190">In the [Enable startup process](#enable-startup-process) section, a lifecycle event was raised by Web Forms as the `Application_BeginRequest` method.</span></span> <span data-ttu-id="1f4e3-191">Cet événement n’est pas disponible dans ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-191">This event isn't available in ASP.NET Core.</span></span> <span data-ttu-id="1f4e3-192">Pour ce faire, il est possible d’implémenter un intergiciel (middleware) comme indiqué dans l’exemple de fichier *Startup.cs* .</span><span class="sxs-lookup"><span data-stu-id="1f4e3-192">One way to achieve this behavior is to implement middleware as seen in the *Startup.cs* file example.</span></span> <span data-ttu-id="1f4e3-193">Cet intergiciel (middleware) fait la même logique, puis transfère le contrôle au gestionnaire suivant dans le pipeline d’intergiciel (middleware).</span><span class="sxs-lookup"><span data-stu-id="1f4e3-193">This middleware does the same logic and then transfers control to the next handler in the middleware pipeline.</span></span>

<span data-ttu-id="1f4e3-194">Pour plus d’informations sur la migration des modules et des gestionnaires, consultez [migrer des modules et des gestionnaires HTTP vers ASP.net Core intergiciel](/aspnet/core/migration/http-modules).</span><span class="sxs-lookup"><span data-stu-id="1f4e3-194">For more information on migrating modules and handlers, see [Migrate HTTP handlers and modules to ASP.NET Core middleware](/aspnet/core/migration/http-modules).</span></span>

## <a name="migrate-static-files"></a><span data-ttu-id="1f4e3-195">Migrer des fichiers statiques</span><span class="sxs-lookup"><span data-stu-id="1f4e3-195">Migrate static files</span></span>

<span data-ttu-id="1f4e3-196">Pour servir des fichiers statiques (par exemple, HTML, CSS, images et JavaScript), les fichiers doivent être exposés par un intergiciel (middleware).</span><span class="sxs-lookup"><span data-stu-id="1f4e3-196">To serve static files (for example, HTML, CSS, images, and JavaScript), the files must be exposed by middleware.</span></span> <span data-ttu-id="1f4e3-197">L’appel `UseStaticFiles` de la méthode permet le service des fichiers statiques à partir du chemin d’accès racine Web.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-197">Calling the `UseStaticFiles` method enables the serving of static files from the web root path.</span></span> <span data-ttu-id="1f4e3-198">Le répertoire racine Web par défaut est *wwwroot*, mais il peut être personnalisé.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-198">The default web root directory is *wwwroot*, but it can be customized.</span></span> <span data-ttu-id="1f4e3-199">Comme inclus dans la `Configure` classe de eShop `Startup` :</span><span class="sxs-lookup"><span data-stu-id="1f4e3-199">As included in the `Configure` method of eShop's `Startup` class:</span></span>

```csharp
public void Configure(IApplicationBuilder app)
{
    ...

    app.UseStaticFiles();

    ...
}
```

<span data-ttu-id="1f4e3-200">Le projet eShop active l’accès aux fichiers statiques de base.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-200">The eShop project enables basic static file access.</span></span> <span data-ttu-id="1f4e3-201">De nombreuses personnalisations sont disponibles pour l’accès aux fichiers statiques.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-201">There are many customizations available for static file access.</span></span> <span data-ttu-id="1f4e3-202">Pour plus d’informations sur l’activation des fichiers par défaut ou d’un Explorateur de fichiers, consultez [fichiers statiques dans ASP.net Core](/aspnet/core/fundamentals/static-files).</span><span class="sxs-lookup"><span data-stu-id="1f4e3-202">For information on enabling default files or a file browser, see [Static files in ASP.NET Core](/aspnet/core/fundamentals/static-files).</span></span>

## <a name="migrate-runtime-bundling-and-minification-setup"></a><span data-ttu-id="1f4e3-203">Migrer le regroupement et la minimisation du Runtime</span><span class="sxs-lookup"><span data-stu-id="1f4e3-203">Migrate runtime bundling and minification setup</span></span>

<span data-ttu-id="1f4e3-204">Le regroupement et la minimisation sont des techniques d’optimisation des performances pour réduire le nombre et la taille des demandes de serveur pour récupérer certains types de fichiers.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-204">Bundling and minification are performance optimization techniques for reducing the number and size of server requests to retrieve certain file types.</span></span> <span data-ttu-id="1f4e3-205">JavaScript et CSS subissent souvent une certaine forme de regroupement ou de minimisation avant d’être envoyés au client.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-205">JavaScript and CSS often undergo some form of bundling or minification before being sent to the client.</span></span> <span data-ttu-id="1f4e3-206">Dans ASP.NET Web Forms, ces optimisations sont gérées au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-206">In ASP.NET Web Forms, these optimizations are handled at runtime.</span></span> <span data-ttu-id="1f4e3-207">Les conventions d’optimisation sont définies comme un fichier *App_Start/bundleconfig.cs* .</span><span class="sxs-lookup"><span data-stu-id="1f4e3-207">The optimization conventions are defined an *App_Start/BundleConfig.cs* file.</span></span> <span data-ttu-id="1f4e3-208">Dans ASP.NET Core, une approche plus déclarative est adoptée.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-208">In ASP.NET Core, a more declarative approach is adopted.</span></span> <span data-ttu-id="1f4e3-209">Un fichier répertorie les fichiers à minimisésr, ainsi que les paramètres de minimisation spécifiques.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-209">A file lists the files to be minified, along with specific minification settings.</span></span>

<span data-ttu-id="1f4e3-210">Pour plus d’informations sur le regroupement et la minimisation, consultez [regrouper et réduire des ressources statiques dans ASP.net Core](/aspnet/core/client-side/bundling-and-minification).</span><span class="sxs-lookup"><span data-stu-id="1f4e3-210">For more information on bundling and minification, see [Bundle and minify static assets in ASP.NET Core](/aspnet/core/client-side/bundling-and-minification).</span></span>

## <a name="migrate-aspx-pages"></a><span data-ttu-id="1f4e3-211">Migrer des pages ASPX</span><span class="sxs-lookup"><span data-stu-id="1f4e3-211">Migrate ASPX pages</span></span>

<span data-ttu-id="1f4e3-212">Une page dans une application Web Forms est un fichier avec l’extension *. aspx* .</span><span class="sxs-lookup"><span data-stu-id="1f4e3-212">A page in a Web Forms app is a file with the *.aspx* extension.</span></span> <span data-ttu-id="1f4e3-213">Une page de Web Forms peut souvent être mappée à un composant dans Blazor .</span><span class="sxs-lookup"><span data-stu-id="1f4e3-213">A Web Forms page can often be mapped to a component in Blazor.</span></span> <span data-ttu-id="1f4e3-214">Un Blazor composant est créé dans un fichier avec l’extension *. Razor* .</span><span class="sxs-lookup"><span data-stu-id="1f4e3-214">A Blazor component is authored in a file with the *.razor* extension.</span></span> <span data-ttu-id="1f4e3-215">Pour le projet eShop, cinq pages sont converties en page Razor.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-215">For the eShop project, five pages are converted to a Razor page.</span></span>

<span data-ttu-id="1f4e3-216">Par exemple, la vue Détails comprend trois fichiers dans le projet Web Forms : *Details. aspx*, *Details.aspx.cs*et *Details.aspx.Designer.cs*.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-216">For example, the details view comprises three files in the Web Forms project: *Details.aspx*, *Details.aspx.cs*, and *Details.aspx.designer.cs*.</span></span> <span data-ttu-id="1f4e3-217">Lors de la conversion en Blazor , le code-behind et le balisage sont combinés dans *Details. Razor*.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-217">When converting to Blazor, the code-behind and markup are combined into *Details.razor*.</span></span> <span data-ttu-id="1f4e3-218">La compilation Razor (équivalente aux fichiers *. Designer.cs* ) est stockée dans le répertoire *obj* et n’est pas, par défaut, visible dans **Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-218">Razor compilation (equivalent to what's in *.designer.cs* files) is stored in the *obj* directory and isn't, by default, viewable in **Solution Explorer**.</span></span> <span data-ttu-id="1f4e3-219">La page Web Forms se compose du balisage suivant :</span><span class="sxs-lookup"><span data-stu-id="1f4e3-219">The Web Forms page consists of the following markup:</span></span>

```aspx-csharp
<%@ Page Title="Details" Language="C#" MasterPageFile="~/Site.Master" AutoEventWireup="true" CodeBehind="Details.aspx.cs" Inherits="eShopLegacyWebForms.Catalog.Details" %>

<asp:Content ID="Details" ContentPlaceHolderID="MainContent" runat="server">
    <h2 class="esh-body-title">Details</h2>

    <div class="container">
        <div class="row">
            <asp:Image runat="server" CssClass="col-md-6 esh-picture" ImageUrl='<%#"/Pics/" + product.PictureFileName%>' />
            <dl class="col-md-6 dl-horizontal">
                <dt>Name
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.Name%>' />
                </dd>

                <dt>Description
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.Description%>' />
                </dd>

                <dt>Brand
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.CatalogBrand.Brand%>' />
                </dd>

                <dt>Type
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.CatalogType.Type%>' />
                </dd>
                <dt>Price
                </dt>

                <dd>
                    <asp:Label CssClass="esh-price" runat="server" Text='<%#product.Price%>' />
                </dd>

                <dt>Picture name
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.PictureFileName%>' />
                </dd>

                <dt>Stock
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.AvailableStock%>' />
                </dd>

                <dt>Restock
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.RestockThreshold%>' />
                </dd>

                <dt>Max stock
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.MaxStockThreshold%>' />
                </dd>

            </dl>
        </div>

        <div class="form-actions no-color esh-link-list">
            <a runat="server" href='<%# GetRouteUrl("EditProductRoute", new {id =product.Id}) %>' class="esh-link-item">Edit
            </a>
            |
            <a runat="server" href="~" class="esh-link-item">Back to list
            </a>
        </div>

    </div>
</asp:Content>
```

<span data-ttu-id="1f4e3-220">Le code-behind du balisage précédent comprend le code suivant :</span><span class="sxs-lookup"><span data-stu-id="1f4e3-220">The preceding markup's code-behind includes the following code:</span></span>

```csharp
using eShopLegacyWebForms.Models;
using eShopLegacyWebForms.Services;
using log4net;
using System;
using System.Web.UI;

namespace eShopLegacyWebForms.Catalog
{
    public partial class Details : System.Web.UI.Page
    {
        private static readonly ILog _log = LogManager.GetLogger(System.Reflection.MethodBase.GetCurrentMethod().DeclaringType);

        protected CatalogItem product;

        public ICatalogService CatalogService { get; set; }

        protected void Page_Load(object sender, EventArgs e)
        {
            var productId = Convert.ToInt32(Page.RouteData.Values["id"]);
            _log.Info($"Now loading... /Catalog/Details.aspx?id={productId}");
            product = CatalogService.FindCatalogItem(productId);

            this.DataBind();
        }
    }
}
```

<span data-ttu-id="1f4e3-221">En cas de conversion en Blazor , la page Web Forms se traduit par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="1f4e3-221">When converted to Blazor, the Web Forms page translates to the following code:</span></span>

```razor
@page "/Catalog/Details/{id:int}"
@inject ICatalogService CatalogService
@inject ILogger<Details> Logger

<h2 class="esh-body-title">Details</h2>

<div class="container">
    <div class="row">
        <img class="col-md-6 esh-picture" src="@($"/Pics/{_item.PictureFileName}")">

        <dl class="col-md-6 dl-horizontal">
            <dt>
                Name
            </dt>

            <dd>
                @_item.Name
            </dd>

            <dt>
                Description
            </dt>

            <dd>
                @_item.Description
            </dd>

            <dt>
                Brand
            </dt>

            <dd>
                @_item.CatalogBrand.Brand
            </dd>

            <dt>
                Type
            </dt>

            <dd>
                @_item.CatalogType.Type
            </dd>
            <dt>
                Price
            </dt>

            <dd>
                @_item.Price
            </dd>

            <dt>
                Picture name
            </dt>

            <dd>
                @_item.PictureFileName
            </dd>

            <dt>
                Stock
            </dt>

            <dd>
                @_item.AvailableStock
            </dd>

            <dt>
                Restock
            </dt>

            <dd>
                @_item.RestockThreshold
            </dd>

            <dt>
                Max stock
            </dt>

            <dd>
                @_item.MaxStockThreshold
            </dd>

        </dl>
    </div>

    <div class="form-actions no-color esh-link-list">
        <a href="@($"/Catalog/Edit/{_item.Id}")" class="esh-link-item">
            Edit
        </a>
        |
        <a href="/" class="esh-link-item">
            Back to list
        </a>
    </div>

</div>

@code {
    private CatalogItem _item;

    [Parameter]
    public int Id { get; set; }

    protected override void OnInitialized()
    {
        Logger.LogInformation("Now loading... /Catalog/Details/{Id}", Id);

        _item = CatalogService.FindCatalogItem(Id);
    }
}
```

<span data-ttu-id="1f4e3-222">Notez que le code et le balisage se trouvent dans le même fichier.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-222">Notice that the code and markup are in the same file.</span></span> <span data-ttu-id="1f4e3-223">Tous les services requis sont rendus accessibles avec l' `@inject` attribut.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-223">Any required services are made accessible with the `@inject` attribute.</span></span> <span data-ttu-id="1f4e3-224">Pour la `@page` directive, cette page est accessible au niveau de l' `Catalog/Details/{id}` itinéraire.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-224">Per the `@page` directive, this page can be accessed at the `Catalog/Details/{id}` route.</span></span> <span data-ttu-id="1f4e3-225">La valeur de l’espace réservé de l’itinéraire `{id}` a été restreinte à un entier.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-225">The value of the route's `{id}` placeholder has been constrained to an integer.</span></span> <span data-ttu-id="1f4e3-226">Comme décrit dans la section [routage](pages-routing-layouts.md) , contrairement à Web Forms, un composant Razor indique explicitement son itinéraire et tous les paramètres qui sont inclus.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-226">As described in the [routing](pages-routing-layouts.md) section, unlike Web Forms, a Razor component explicitly states its route and any parameters that are included.</span></span> <span data-ttu-id="1f4e3-227">De nombreux contrôles de Web Forms peuvent ne pas avoir des équivalents exacts dans Blazor .</span><span class="sxs-lookup"><span data-stu-id="1f4e3-227">Many Web Forms controls may not have exact counterparts in Blazor.</span></span> <span data-ttu-id="1f4e3-228">Il existe souvent un extrait de code HTML équivalent qui servira le même objectif.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-228">There's often an equivalent HTML snippet that will serve the same purpose.</span></span> <span data-ttu-id="1f4e3-229">Par exemple, le `<asp:Label />` contrôle peut être remplacé par un `<label>` élément HTML.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-229">For example, the `<asp:Label />` control can be replaced with an HTML `<label>` element.</span></span>

### <a name="model-validation-in-no-locblazor"></a><span data-ttu-id="1f4e3-230">Validation de modèle dans Blazor</span><span class="sxs-lookup"><span data-stu-id="1f4e3-230">Model validation in Blazor</span></span>

<span data-ttu-id="1f4e3-231">Si votre code Web Forms comprend une validation, vous pouvez transférer une grande partie de ce que vous avez avec des modifications minimes.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-231">If your Web Forms code includes validation, you can transfer much of what you have with little-to-no changes.</span></span> <span data-ttu-id="1f4e3-232">L’un des avantages de l’exécution de dans Blazor est que la même logique de validation peut être exécutée sans avoir besoin de JavaScript personnalisé.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-232">A benefit to running in Blazor is that the same validation logic can be run without needing custom JavaScript.</span></span> <span data-ttu-id="1f4e3-233">Les annotations de données facilitent la validation du modèle.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-233">Data annotations enable easy model validation.</span></span>

<span data-ttu-id="1f4e3-234">Par exemple, la page *Create. aspx* possède un formulaire de saisie de données avec validation.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-234">For example, the *Create.aspx* page has a data entry form with validation.</span></span> <span data-ttu-id="1f4e3-235">Voici un exemple d’extrait de code :</span><span class="sxs-lookup"><span data-stu-id="1f4e3-235">An example snippet would look like this:</span></span>

```aspx
<div class="form-group">
    <label class="control-label col-md-2">Name</label>
    <div class="col-md-3">
        <asp:TextBox ID="Name" runat="server" CssClass="form-control"></asp:TextBox>
        <asp:RequiredFieldValidator runat="server" ControlToValidate="Name" Display="Dynamic"
            CssClass="field-validation-valid text-danger" ErrorMessage="The Name field is required." />
    </div>
</div>
```

<span data-ttu-id="1f4e3-236">Dans Blazor , le balisage équivalent est fourni dans un fichier *Create. Razor* :</span><span class="sxs-lookup"><span data-stu-id="1f4e3-236">In Blazor, the equivalent markup is provided in a *Create.razor* file:</span></span>

```razor
<EditForm Model="_item" OnValidSubmit="@...">
    <DataAnnotationsValidator />

    <div class="form-group">
        <label class="control-label col-md-2">Name</label>
        <div class="col-md-3">
            <InputText class="form-control" @bind-Value="_item.Name" />
            <ValidationMessage For="(() => _item.Name)" />
        </div>
    </div>

    ...
</EditForm>
```

<span data-ttu-id="1f4e3-237">Le `EditForm` contexte comprend la prise en charge de la validation et peut être encapsulé autour de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-237">The `EditForm` context includes validation support and can be wrapped around input.</span></span> <span data-ttu-id="1f4e3-238">Les annotations de données sont une méthode courante pour ajouter une validation.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-238">Data annotations are a common way to add validation.</span></span> <span data-ttu-id="1f4e3-239">Une telle prise en charge de la validation peut être ajoutée via le `DataAnnotationsValidator` composant.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-239">Such validation support can be added via the `DataAnnotationsValidator` component.</span></span> <span data-ttu-id="1f4e3-240">Pour plus d’informations sur ce mécanisme, consultez [ASP.net Core Blazor Forms and validation](/aspnet/core/blazor/forms-validation).</span><span class="sxs-lookup"><span data-stu-id="1f4e3-240">For more information on this mechanism, see [ASP.NET Core Blazor forms and validation](/aspnet/core/blazor/forms-validation).</span></span>

## <a name="migrate-built-in-web-forms-controls"></a><span data-ttu-id="1f4e3-241">Migrer des contrôles de Web Forms intégrés</span><span class="sxs-lookup"><span data-stu-id="1f4e3-241">Migrate built-in Web Forms controls</span></span>

<span data-ttu-id="1f4e3-242">*Ce contenu sera bientôt disponible.*</span><span class="sxs-lookup"><span data-stu-id="1f4e3-242">*This content is coming soon.*</span></span>

## <a name="migrate-configuration"></a><span data-ttu-id="1f4e3-243">Migrer une configuration</span><span class="sxs-lookup"><span data-stu-id="1f4e3-243">Migrate configuration</span></span>

<span data-ttu-id="1f4e3-244">Dans un projet Web Forms, les données de configuration sont le plus souvent stockées dans le fichier *web.config* .</span><span class="sxs-lookup"><span data-stu-id="1f4e3-244">In a Web Forms project, configuration data is most commonly stored in the *web.config* file.</span></span> <span data-ttu-id="1f4e3-245">Les données de configuration sont accessibles à l’aide de `ConfigurationManager` .</span><span class="sxs-lookup"><span data-stu-id="1f4e3-245">The configuration data is accessed with `ConfigurationManager`.</span></span> <span data-ttu-id="1f4e3-246">Les services étaient souvent requis pour analyser des objets.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-246">Services were often required to parse objects.</span></span> <span data-ttu-id="1f4e3-247">Avec .NET Framework 4.7.2, la composabilité a été ajoutée à la configuration via `ConfigurationBuilders` .</span><span class="sxs-lookup"><span data-stu-id="1f4e3-247">With .NET Framework 4.7.2, composability was added to configuration via `ConfigurationBuilders`.</span></span> <span data-ttu-id="1f4e3-248">Ces générateurs permettaient aux développeurs d’ajouter différentes sources pour la configuration qui était ensuite composée au moment de l’exécution pour récupérer les valeurs nécessaires.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-248">These builders allowed developers to add various sources for configuration that was then composed at runtime to retrieve the necessary values.</span></span>

<span data-ttu-id="1f4e3-249">ASP.NET Core a introduit un système de configuration flexible qui vous permet de définir la ou les sources de configuration utilisées par votre application et votre déploiement.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-249">ASP.NET Core introduced a flexible configuration system that allows you to define the configuration source or sources used by your app and deployment.</span></span> <span data-ttu-id="1f4e3-250">L' `ConfigurationBuilder` infrastructure que vous utilisez peut-être dans votre application Web Forms a été modélisée après les concepts utilisés dans le système de configuration ASP.net core.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-250">The `ConfigurationBuilder` infrastructure that you may be using in your Web Forms app was modeled after the concepts used in the ASP.NET Core configuration system.</span></span>

<span data-ttu-id="1f4e3-251">L’extrait de code suivant montre comment le projet Web Forms eShop utilise *web.config* pour stocker les valeurs de configuration :</span><span class="sxs-lookup"><span data-stu-id="1f4e3-251">The following snippet demonstrates how the Web Forms eShop project uses *web.config* to store configuration values:</span></span>

```xml
<configuration>
  <configSections>
    <section name="entityFramework" type="System.Data.Entity.Internal.ConfigFile.EntityFrameworkSection, EntityFramework, Version=6.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" requirePermission="false" />
  </configSections>
  <connectionStrings>
    <add name="CatalogDBContext" connectionString="Data Source=(localdb)\MSSQLLocalDB; Initial Catalog=Microsoft.eShopOnContainers.Services.CatalogDb; Integrated Security=True; MultipleActiveResultSets=True;" providerName="System.Data.SqlClient" />
  </connectionStrings>
  <appSettings>
    <add key="UseMockData" value="true" />
    <add key="UseCustomizationData" value="false" />
  </appSettings>
</configuration>
```

<span data-ttu-id="1f4e3-252">Il est courant que les secrets, tels que les chaînes de connexion de base de données, soient stockés dans le *web.config*. Les secrets sont inévitablement conservés dans des emplacements non sécurisés, tels que le contrôle de code source.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-252">It's common for secrets, such as database connection strings, to be stored within the *web.config*. The secrets are inevitably persisted in unsecure locations, such as source control.</span></span> <span data-ttu-id="1f4e3-253">Avec Blazor sur ASP.net Core, la configuration XML précédente est remplacée par le code JSON suivant :</span><span class="sxs-lookup"><span data-stu-id="1f4e3-253">With Blazor on ASP.NET Core, the preceding XML-based configuration is replaced with the following JSON:</span></span>

```json
{
  "ConnectionStrings": {
    "CatalogDBContext": "Data Source=(localdb)\\MSSQLLocalDB; Initial Catalog=Microsoft.eShopOnContainers.Services.CatalogDb; Integrated Security=True; MultipleActiveResultSets=True;"
  },
  "UseMockData": true,
  "UseCustomizationData": false
}
```

<span data-ttu-id="1f4e3-254">JSON est le format de configuration par défaut ; Toutefois, ASP.NET Core prend en charge de nombreux autres formats, y compris XML.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-254">JSON is the default configuration format; however, ASP.NET Core supports many other formats, including XML.</span></span> <span data-ttu-id="1f4e3-255">Il existe également plusieurs formats pris en charge par la communauté.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-255">There are also several community-supported formats.</span></span>

<span data-ttu-id="1f4e3-256">Le constructeur dans la Blazor classe du projet `Startup` accepte une `IConfiguration` instance par le biais d’une technique di appelée injection de constructeur :</span><span class="sxs-lookup"><span data-stu-id="1f4e3-256">The constructor in the Blazor project's `Startup` class accepts an `IConfiguration` instance through a DI technique known as constructor injection:</span></span>

```csharp
public class Startup
{
    public Startup(IConfiguration configuration, IWebHostEnvironment env)
    {
        Configuration = configuration;
        Env = env;
    }

    ...
}
```

<span data-ttu-id="1f4e3-257">Par défaut, les variables d’environnement, les fichiers JSON (*appsettings.jssur* et *appSettings. { Environment}. JSON*), et les options de ligne de commande sont inscrites en tant que sources de configuration valides dans l’objet de configuration.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-257">By default, environment variables, JSON files (*appsettings.json* and *appsettings.{Environment}.json*), and command-line options are registered as valid configuration sources in the configuration object.</span></span> <span data-ttu-id="1f4e3-258">Vous pouvez accéder aux sources de configuration via `Configuration[key]` .</span><span class="sxs-lookup"><span data-stu-id="1f4e3-258">The configuration sources can be accessed via `Configuration[key]`.</span></span> <span data-ttu-id="1f4e3-259">Une technique plus avancée consiste à lier les données de configuration aux objets à l’aide du modèle d’options.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-259">A more advanced technique is to bind the configuration data to objects using the options pattern.</span></span> <span data-ttu-id="1f4e3-260">Pour plus d’informations sur la configuration et le modèle d’options, consultez [configuration in ASP.net Core](/aspnet/core/fundamentals/configuration/) and [options pattern in ASP.net Core](/aspnet/core/fundamentals/configuration/options), respectivement.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-260">For more information on configuration and the options pattern, see [Configuration in ASP.NET Core](/aspnet/core/fundamentals/configuration/) and [Options pattern in ASP.NET Core](/aspnet/core/fundamentals/configuration/options), respectively.</span></span>

## <a name="migrate-data-access"></a><span data-ttu-id="1f4e3-261">Migrer l’accès aux données</span><span class="sxs-lookup"><span data-stu-id="1f4e3-261">Migrate data access</span></span>

<span data-ttu-id="1f4e3-262">L’accès aux données est un aspect important de toute application.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-262">Data access is an important aspect of any app.</span></span> <span data-ttu-id="1f4e3-263">Le projet eShop stocke les informations de catalogue dans une base de données et récupère les données avec Entity Framework (EF) 6.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-263">The eShop project stores catalog information in a database and retrieves the data with Entity Framework (EF) 6.</span></span> <span data-ttu-id="1f4e3-264">Comme EF 6 est pris en charge dans .NET Core 3,0, le projet peut continuer à l’utiliser.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-264">Since EF 6 is supported in .NET Core 3.0, the project can continue to use it.</span></span>

<span data-ttu-id="1f4e3-265">Les modifications suivantes liées à EF étaient nécessaires à eShop :</span><span class="sxs-lookup"><span data-stu-id="1f4e3-265">The following EF-related changes were necessary to eShop:</span></span>

- <span data-ttu-id="1f4e3-266">Dans .NET Framework, l' `DbContext` objet accepte une chaîne sous la forme *nom = ConnectionString* et utilise la chaîne de connexion de `ConfigurationManager.AppSettings[ConnectionString]` pour se connecter.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-266">In .NET Framework, the `DbContext` object accepts a string of the form *name=ConnectionString* and uses the connection string from `ConfigurationManager.AppSettings[ConnectionString]` to connect.</span></span> <span data-ttu-id="1f4e3-267">Dans .NET Core, cela n’est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-267">In .NET Core, this isn't supported.</span></span> <span data-ttu-id="1f4e3-268">La chaîne de connexion doit être fournie.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-268">The connection string must be supplied.</span></span>
- <span data-ttu-id="1f4e3-269">L’accès à la base de données a été effectué de façon synchrone.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-269">The database was accessed in a synchronous way.</span></span> <span data-ttu-id="1f4e3-270">Bien que cela fonctionne, l’évolutivité peut en pâtir.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-270">Though this works, scalability may suffer.</span></span> <span data-ttu-id="1f4e3-271">Cette logique doit être déplacée vers un modèle asynchrone.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-271">This logic should be moved to an asynchronous pattern.</span></span>

<span data-ttu-id="1f4e3-272">Bien qu’il n’y ait pas la même prise en charge native pour la liaison de jeu de données, Blazor offre la flexibilité et la puissance avec sa prise en charge C# dans une page Razor.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-272">Although there isn't the same native support for dataset binding, Blazor provides flexibility and power with its C# support in a Razor page.</span></span> <span data-ttu-id="1f4e3-273">Par exemple, vous pouvez effectuer des calculs et afficher le résultat.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-273">For example, you can perform calculations and display the result.</span></span> <span data-ttu-id="1f4e3-274">Pour plus d’informations sur les modèles de données dans Blazor , consultez le chapitre relatif [à l’accès aux données](data.md) .</span><span class="sxs-lookup"><span data-stu-id="1f4e3-274">For more information on data patterns in Blazor, see the [Data access](data.md) chapter.</span></span>

## <a name="architectural-changes"></a><span data-ttu-id="1f4e3-275">Modifications architecturales</span><span class="sxs-lookup"><span data-stu-id="1f4e3-275">Architectural changes</span></span>

<span data-ttu-id="1f4e3-276">Enfin, il existe quelques différences architecturales importantes à prendre en compte lors de la migration vers Blazor .</span><span class="sxs-lookup"><span data-stu-id="1f4e3-276">Finally, there are some important architectural differences to consider when migrating to Blazor.</span></span> <span data-ttu-id="1f4e3-277">La plupart de ces modifications sont applicables à tout ce qui est basé sur .NET Core ou ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-277">Many of these changes are applicable to anything based on .NET Core or ASP.NET Core.</span></span>

<span data-ttu-id="1f4e3-278">Étant donné que Blazor repose sur .net Core, il existe des éléments à prendre en compte pour garantir la prise en charge de .net core.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-278">Because Blazor is built on .NET Core, there are considerations in ensuring support on .NET Core.</span></span> <span data-ttu-id="1f4e3-279">Parmi les principales modifications, citons la suppression des fonctionnalités suivantes :</span><span class="sxs-lookup"><span data-stu-id="1f4e3-279">Some of the major changes include the removal of the following features:</span></span>

- <span data-ttu-id="1f4e3-280">AppDomains multiples</span><span class="sxs-lookup"><span data-stu-id="1f4e3-280">Multiple AppDomains</span></span>
- <span data-ttu-id="1f4e3-281">Communication à distance</span><span class="sxs-lookup"><span data-stu-id="1f4e3-281">Remoting</span></span>
- <span data-ttu-id="1f4e3-282">Sécurité d'accès du code</span><span class="sxs-lookup"><span data-stu-id="1f4e3-282">Code Access Security (CAS)</span></span>
- <span data-ttu-id="1f4e3-283">Transparence de la sécurité</span><span class="sxs-lookup"><span data-stu-id="1f4e3-283">Security Transparency</span></span>

<span data-ttu-id="1f4e3-284">Pour plus d’informations sur les techniques permettant d’identifier les modifications nécessaires à la prise en charge de l’exécution sur .NET Core, consultez [porter votre code d' .NET Framework vers .net Core](/dotnet/core/porting).</span><span class="sxs-lookup"><span data-stu-id="1f4e3-284">For more information on techniques to identify necessary changes to support running on .NET Core, see [Port your code from .NET Framework to .NET Core](/dotnet/core/porting).</span></span>

<span data-ttu-id="1f4e3-285">ASP.NET Core est une version repensée de ASP.NET et contient des modifications qui peuvent ne pas paraître évidentes.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-285">ASP.NET Core is a reimagined version of ASP.NET and has some changes that may not initially seem obvious.</span></span> <span data-ttu-id="1f4e3-286">Les principales modifications sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="1f4e3-286">The main changes are:</span></span>

- <span data-ttu-id="1f4e3-287">Aucun contexte de synchronisation, ce qui signifie qu’il n’y a aucun `HttpContext.Current` , `Thread.CurrentPrincipal` ou d’autres accesseurs statiques</span><span class="sxs-lookup"><span data-stu-id="1f4e3-287">No synchronization context, which means there's no `HttpContext.Current`, `Thread.CurrentPrincipal`, or other static accessors</span></span>
- <span data-ttu-id="1f4e3-288">Pas de clichés instantanés</span><span class="sxs-lookup"><span data-stu-id="1f4e3-288">No shadow copying</span></span>
- <span data-ttu-id="1f4e3-289">Aucune file d’attente de demandes</span><span class="sxs-lookup"><span data-stu-id="1f4e3-289">No request queue</span></span>

<span data-ttu-id="1f4e3-290">De nombreuses opérations dans ASP.NET Core sont asynchrones, ce qui permet de faciliter le chargement des tâches liées aux e/s.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-290">Many operations in ASP.NET Core are asynchronous, which allows easier off-loading of I/O-bound tasks.</span></span> <span data-ttu-id="1f4e3-291">Il est important de ne jamais bloquer à l’aide de `Task.Wait()` ou de `Task.GetResult()` , ce qui peut épuiser rapidement les ressources du pool de threads.</span><span class="sxs-lookup"><span data-stu-id="1f4e3-291">It's important to never block by using `Task.Wait()` or `Task.GetResult()`, which can quickly exhaust thread pool resources.</span></span>

## <a name="migration-conclusion"></a><span data-ttu-id="1f4e3-292">Conclusion de la migration</span><span class="sxs-lookup"><span data-stu-id="1f4e3-292">Migration conclusion</span></span>

<span data-ttu-id="1f4e3-293">À ce stade, vous avez vu de nombreux exemples de ce qu’il faut pour déplacer un projet Web Forms vers Blazor .</span><span class="sxs-lookup"><span data-stu-id="1f4e3-293">At this point, you've seen many examples of what it takes to move a Web Forms project to Blazor.</span></span> <span data-ttu-id="1f4e3-294">Pour obtenir un exemple complet, consultez le projet [eShopOn Blazor ](https://github.com/dotnet-architecture/eShopOnBlazor) .</span><span class="sxs-lookup"><span data-stu-id="1f4e3-294">For a full example, see the [eShopOnBlazor](https://github.com/dotnet-architecture/eShopOnBlazor) project.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="1f4e3-295">Précédent</span><span class="sxs-lookup"><span data-stu-id="1f4e3-295">Previous</span></span>](security-authentication-authorization.md)
