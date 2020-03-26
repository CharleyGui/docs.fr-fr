---
title: Migrer de ASP.NET formulaires Web à Blazor
description: Apprenez à aborder la migration d’une application Web Forms ASP.NET existante à Blazor.
author: twsouthwick
ms.author: tasou
ms.date: 09/19/2019
ms.openlocfilehash: 0a10a9a3d5ab32e16cb59a68da57116e20c53e49
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134088"
---
# <a name="migrate-from-aspnet-web-forms-to-blazor"></a><span data-ttu-id="afa1a-103">Migrer de ASP.NET formulaires Web à Blazor</span><span class="sxs-lookup"><span data-stu-id="afa1a-103">Migrate from ASP.NET Web Forms to Blazor</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="afa1a-104">La migration d’une base de code de ASP.NET Web Forms à Blazor est une tâche qui prend beaucoup de temps et nécessite une planification.</span><span class="sxs-lookup"><span data-stu-id="afa1a-104">Migrating a code base from ASP.NET Web Forms to Blazor is a time-consuming task that requires planning.</span></span> <span data-ttu-id="afa1a-105">Ce chapitre décrit le processus.</span><span class="sxs-lookup"><span data-stu-id="afa1a-105">This chapter outlines the process.</span></span> <span data-ttu-id="afa1a-106">Quelque chose qui peut faciliter la transition est de s’assurer que l’application adhère à une architecture de *niveau N,* dans lequel le modèle d’application (dans ce cas, Web Forms) est séparé de la logique métier.</span><span class="sxs-lookup"><span data-stu-id="afa1a-106">Something that can ease the transition is to ensure the app adheres to an *N-tier* architecture, wherein the app model (in this case, Web Forms) is separate from the business logic.</span></span> <span data-ttu-id="afa1a-107">Cette séparation logique des couches indique clairement ce qui doit passer à .NET Core et Blazor.</span><span class="sxs-lookup"><span data-stu-id="afa1a-107">This logical separation of layers makes it clear what needs to move to .NET Core and Blazor.</span></span>

<span data-ttu-id="afa1a-108">Pour cet exemple, l’application eShop disponible sur [GitHub](https://github.com/dotnet-architecture/eShopOnBlazor) est utilisée.</span><span class="sxs-lookup"><span data-stu-id="afa1a-108">For this example, the eShop app available on [GitHub](https://github.com/dotnet-architecture/eShopOnBlazor) is used.</span></span> <span data-ttu-id="afa1a-109">eShop est un service de catalogue qui fournit des capacités CRUD via l’entrée et la validation du formulaire.</span><span class="sxs-lookup"><span data-stu-id="afa1a-109">eShop is a catalog service that provides CRUD capabilities via form entry and validation.</span></span>

<span data-ttu-id="afa1a-110">Pourquoi une application de travail devrait-elle être migrée vers Blazor ?</span><span class="sxs-lookup"><span data-stu-id="afa1a-110">Why should a working app be migrated to Blazor?</span></span> <span data-ttu-id="afa1a-111">Plusieurs fois, il n’y a pas besoin.</span><span class="sxs-lookup"><span data-stu-id="afa1a-111">Many times, there's no need.</span></span> <span data-ttu-id="afa1a-112">ASP.NET formulaires Web continueront d’être soutenus pendant de nombreuses années.</span><span class="sxs-lookup"><span data-stu-id="afa1a-112">ASP.NET Web Forms will continue to be supported for many years.</span></span> <span data-ttu-id="afa1a-113">Cependant, bon nombre des fonctionnalités que Blazor fournit ne sont prises en charge que sur une application migrée.</span><span class="sxs-lookup"><span data-stu-id="afa1a-113">However, many of the features that Blazor provides are only supported on a migrated app.</span></span> <span data-ttu-id="afa1a-114">Ces caractéristiques comprennent :</span><span class="sxs-lookup"><span data-stu-id="afa1a-114">Such features include:</span></span>

- <span data-ttu-id="afa1a-115">Amélioration du rendement dans le cadre, comme`Span<T>`</span><span class="sxs-lookup"><span data-stu-id="afa1a-115">Performance improvements in the framework such as `Span<T>`</span></span>
- <span data-ttu-id="afa1a-116">Capacité à fonctionner comme WebAssembly</span><span class="sxs-lookup"><span data-stu-id="afa1a-116">Ability to run as WebAssembly</span></span>
- <span data-ttu-id="afa1a-117">Support multiplateforme pour Linux et macOS</span><span class="sxs-lookup"><span data-stu-id="afa1a-117">Cross-platform support for Linux and macOS</span></span>
- <span data-ttu-id="afa1a-118">Déploiement App-local ou déploiement de cadres partagés sans impact sur d’autres applications</span><span class="sxs-lookup"><span data-stu-id="afa1a-118">App-local deployment or shared framework deployment without impacting other apps</span></span>

<span data-ttu-id="afa1a-119">Si ces nouvelles fonctionnalités ou d’autres sont assez convaincantes, il peut y avoir de la valeur dans la migration de l’application.</span><span class="sxs-lookup"><span data-stu-id="afa1a-119">If these or other new features are compelling enough, there may be value in migrating the app.</span></span> <span data-ttu-id="afa1a-120">La migration peut prendre différentes formes; il peut s’agir de l’application entière, ou seulement de certains paramètres qui nécessitent les modifications.</span><span class="sxs-lookup"><span data-stu-id="afa1a-120">The migration can take different shapes; it can be the entire app, or only certain endpoints that require the changes.</span></span> <span data-ttu-id="afa1a-121">La décision de migrer est finalement basée sur les problèmes d’affaires à résoudre par le développeur.</span><span class="sxs-lookup"><span data-stu-id="afa1a-121">The decision to migrate is ultimately based on the business problems to be solved by the developer.</span></span>

## <a name="server-side-versus-client-side-hosting"></a><span data-ttu-id="afa1a-122">Serveur-côté contre l’hébergement côté client</span><span class="sxs-lookup"><span data-stu-id="afa1a-122">Server-side versus client-side hosting</span></span>

<span data-ttu-id="afa1a-123">Comme décrit dans le chapitre [des modèles d’hébergement,](hosting-models.md) une application Blazor peut être hébergée de deux façons différentes : côté serveur et côté client.</span><span class="sxs-lookup"><span data-stu-id="afa1a-123">As described in the [hosting models](hosting-models.md) chapter, a Blazor app can be hosted in two different ways: server-side and client-side.</span></span> <span data-ttu-id="afa1a-124">Le modèle côté serveur utilise ASP.NET connexions Core SignalR pour gérer les mises à jour DOM tout en exécutant n’importe quel code réel sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="afa1a-124">The server-side model uses ASP.NET Core SignalR connections to manage the DOM updates while running any actual code on the server.</span></span> <span data-ttu-id="afa1a-125">Le modèle côté client fonctionne sous forme de WebAssembly dans un navigateur et ne nécessite aucune connexion serveur.</span><span class="sxs-lookup"><span data-stu-id="afa1a-125">The client-side model runs as WebAssembly within a browser and requires no server connections.</span></span> <span data-ttu-id="afa1a-126">Il existe un certain nombre de différences qui peuvent affecter qui est le mieux pour une application spécifique:</span><span class="sxs-lookup"><span data-stu-id="afa1a-126">There are a number of differences that may affect which is best for a specific app:</span></span>

- <span data-ttu-id="afa1a-127">En cours d’exécution comme WebAssembly est encore en développement et peut ne pas prendre en charge toutes les fonctionnalités (comme le threading) à l’heure actuelle</span><span class="sxs-lookup"><span data-stu-id="afa1a-127">Running as WebAssembly is still in development and may not support all features (such as threading) at the current time</span></span>
- <span data-ttu-id="afa1a-128">La communication bavarde entre le client et le serveur peut causer des problèmes de latence en mode serveur</span><span class="sxs-lookup"><span data-stu-id="afa1a-128">Chatty communication between the client and server may cause latency issues in server-side mode</span></span>
- <span data-ttu-id="afa1a-129">L’accès aux bases de données et aux services internes ou protégés nécessite un service distinct avec un hébergement côté client</span><span class="sxs-lookup"><span data-stu-id="afa1a-129">Access to databases and internal or protected services require a separate service with client-side hosting</span></span>

<span data-ttu-id="afa1a-130">Au moment d’écrire ces lignes, le modèle côté serveur ressemble plus étroitement aux formulaires Web.</span><span class="sxs-lookup"><span data-stu-id="afa1a-130">At the time of writing, the server-side model more closely resembles Web Forms.</span></span> <span data-ttu-id="afa1a-131">La plupart de ce chapitre se concentre sur le modèle d’hébergement côté serveur, car il est prêt à la production.</span><span class="sxs-lookup"><span data-stu-id="afa1a-131">Most of this chapter focuses on the server-side hosting model, as it's production-ready.</span></span>

## <a name="create-a-new-project"></a><span data-ttu-id="afa1a-132">Création d'un projet</span><span class="sxs-lookup"><span data-stu-id="afa1a-132">Create a new project</span></span>

<span data-ttu-id="afa1a-133">Cette première étape migratoire consiste à créer un nouveau projet.</span><span class="sxs-lookup"><span data-stu-id="afa1a-133">This initial migration step is to create a new project.</span></span> <span data-ttu-id="afa1a-134">Ce type de projet est basé sur les projets de style SDK de .NET Core et simplifie une grande partie de la plaque chauffante qui a été utilisée dans les formats de projet précédents.</span><span class="sxs-lookup"><span data-stu-id="afa1a-134">This project type is based on the SDK style projects of .NET Core and simplifies much of the boilerplate that was used in previous project formats.</span></span> <span data-ttu-id="afa1a-135">Pour plus de détails, veuillez consulter le chapitre sur [la structure du projet](project-structure.md).</span><span class="sxs-lookup"><span data-stu-id="afa1a-135">For more detail, please see the chapter on [Project Structure](project-structure.md).</span></span>

<span data-ttu-id="afa1a-136">Une fois le projet créé, installez les bibliothèques qui ont été utilisées dans le projet précédent.</span><span class="sxs-lookup"><span data-stu-id="afa1a-136">Once the project has been created, install the libraries that were used in the previous project.</span></span> <span data-ttu-id="afa1a-137">Dans d’anciens projets Web Forms, vous avez peut-être utilisé le fichier *packages.config* pour énumérer les paquets NuGet requis.</span><span class="sxs-lookup"><span data-stu-id="afa1a-137">In older Web Forms projects, you may have used the *packages.config* file to list the required NuGet packages.</span></span> <span data-ttu-id="afa1a-138">Dans le nouveau projet de style SDK, *packages.config* a été remplacé par `<PackageReference>` des éléments dans le dossier du projet.</span><span class="sxs-lookup"><span data-stu-id="afa1a-138">In the new SDK-style project, *packages.config* has been replaced with `<PackageReference>` elements in the project file.</span></span> <span data-ttu-id="afa1a-139">Un avantage à cette approche est que toutes les dépendances sont installées de façon transitive.</span><span class="sxs-lookup"><span data-stu-id="afa1a-139">A benefit to this approach is that all dependencies are installed transitively.</span></span> <span data-ttu-id="afa1a-140">Vous n’énumérez que les dépendances de haut niveau qui vous tiennent à cœ place.</span><span class="sxs-lookup"><span data-stu-id="afa1a-140">You only list the top-level dependencies you care about.</span></span>

<span data-ttu-id="afa1a-141">Bon nombre des dépendances que vous utilisez sont disponibles pour .NET Core, y compris Entity Framework 6 et log4net.</span><span class="sxs-lookup"><span data-stu-id="afa1a-141">Many of the dependencies you're using are available for .NET Core, including Entity Framework 6 and log4net.</span></span> <span data-ttu-id="afa1a-142">S’il n’y a pas de version standard .NET ou .NET disponible, la version cadre .NET peut souvent être utilisée.</span><span class="sxs-lookup"><span data-stu-id="afa1a-142">If there's no .NET Core or .NET Standard version available, the .NET Framework version can often be used.</span></span> <span data-ttu-id="afa1a-143">Votre kilométrage peut varier.</span><span class="sxs-lookup"><span data-stu-id="afa1a-143">Your mileage may vary.</span></span> <span data-ttu-id="afa1a-144">Toute API utilisée qui n’est pas disponible en .NET Core provoque une erreur de temps d’exécution.</span><span class="sxs-lookup"><span data-stu-id="afa1a-144">Any API used that isn't available in .NET Core causes a runtime error.</span></span> <span data-ttu-id="afa1a-145">Visual Studio vous informe de ces paquets.</span><span class="sxs-lookup"><span data-stu-id="afa1a-145">Visual Studio notifies you of such packages.</span></span> <span data-ttu-id="afa1a-146">Une icône jaune apparaît sur le nœud **Références** du projet dans **Solution Explorer**.</span><span class="sxs-lookup"><span data-stu-id="afa1a-146">A yellow icon appears on the project's **References** node in **Solution Explorer**.</span></span>

<span data-ttu-id="afa1a-147">Dans le projet eShop basé à Blazor, vous pouvez voir les paquets qui sont installés.</span><span class="sxs-lookup"><span data-stu-id="afa1a-147">In the Blazor-based eShop project, you can see the packages that are installed.</span></span> <span data-ttu-id="afa1a-148">Auparavant, le fichier *packages.config* énumérait tous les paquets utilisés dans le projet, ce qui a donné lieu à un fichier de près de 50 lignes de long.</span><span class="sxs-lookup"><span data-stu-id="afa1a-148">Previously, the *packages.config* file listed every package used in the project, resulting in a file almost 50 lines long.</span></span> <span data-ttu-id="afa1a-149">Un extrait de *packages.config* est :</span><span class="sxs-lookup"><span data-stu-id="afa1a-149">A snippet of *packages.config* is:</span></span>

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

<span data-ttu-id="afa1a-150">L’élément `<packages>` comprend toutes les dépendances nécessaires.</span><span class="sxs-lookup"><span data-stu-id="afa1a-150">The `<packages>` element includes all necessary dependencies.</span></span> <span data-ttu-id="afa1a-151">Il est difficile d’identifier lequel de ces paquets sont inclus parce que vous en avez besoin.</span><span class="sxs-lookup"><span data-stu-id="afa1a-151">It's difficult to identify which of these packages are included because you require them.</span></span> <span data-ttu-id="afa1a-152">Certains `<package>` éléments sont énumérés simplement pour satisfaire les besoins des dépendances dont vous avez besoin.</span><span class="sxs-lookup"><span data-stu-id="afa1a-152">Some `<package>` elements are listed simply to satisfy the needs of dependencies you require.</span></span>

<span data-ttu-id="afa1a-153">Le projet Blazor répertorie les `<ItemGroup>` dépendances dont vous avez besoin dans un élément du dossier du projet :</span><span class="sxs-lookup"><span data-stu-id="afa1a-153">The Blazor project lists the dependencies you require within an `<ItemGroup>` element in the project file:</span></span>

```xml
<ItemGroup>
    <PackageReference Include="Autofac" Version="4.9.3" />
    <PackageReference Include="EntityFramework" Version="6.3.0-preview9-19423-04" />
    <PackageReference Include="log4net" Version="2.0.8" />
</ItemGroup>
```

<span data-ttu-id="afa1a-154">Un paquet NuGet qui simplifie la vie des développeurs Web Forms est le [Pack de Compatibilité Windows](../../core/porting/windows-compat-pack.md).</span><span class="sxs-lookup"><span data-stu-id="afa1a-154">One NuGet package that simplifies the life of Web Forms developers is the [Windows Compatibility Pack](../../core/porting/windows-compat-pack.md).</span></span> <span data-ttu-id="afa1a-155">Bien que .NET Core est multi-plateforme, certaines fonctionnalités ne sont disponibles que sur Windows.</span><span class="sxs-lookup"><span data-stu-id="afa1a-155">Although .NET Core is cross-platform, some features are only available on Windows.</span></span> <span data-ttu-id="afa1a-156">Les fonctionnalités spécifiques à Windows sont mises à disposition en installant le pack de compatibilité.</span><span class="sxs-lookup"><span data-stu-id="afa1a-156">Windows-specific features are made available by installing the compatibility pack.</span></span> <span data-ttu-id="afa1a-157">Les services d’annuaire, de l’IMC et des services d’annuaire, en sont des exemples.</span><span class="sxs-lookup"><span data-stu-id="afa1a-157">Examples of such features include the Registry, WMI, and Directory Services.</span></span> <span data-ttu-id="afa1a-158">Le paquet ajoute environ 20.000 API et active de nombreux services avec lesquels vous pouvez déjà être familier.</span><span class="sxs-lookup"><span data-stu-id="afa1a-158">The package adds around 20,000 APIs and activates many services with which you may already be familiar.</span></span> <span data-ttu-id="afa1a-159">Le projet eShop ne nécessite pas le pack de compatibilité; mais si vos projets utilisent des fonctionnalités spécifiques à Windows, le paquet facilite les efforts de migration.</span><span class="sxs-lookup"><span data-stu-id="afa1a-159">The eShop project doesn't require the compatibility pack; but if your projects use Windows-specific features, the package eases the migration efforts.</span></span>

## <a name="enable-startup-process"></a><span data-ttu-id="afa1a-160">Activer le processus de démarrage</span><span class="sxs-lookup"><span data-stu-id="afa1a-160">Enable startup process</span></span>

<span data-ttu-id="afa1a-161">Le processus de démarrage de Blazor a changé de Web Forms et suit une configuration similaire pour d’autres services ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="afa1a-161">The startup process for Blazor has changed from Web Forms and follows a similar setup for other ASP.NET Core services.</span></span> <span data-ttu-id="afa1a-162">Lorsqu’ils sont hébergés côté serveur, les composants Blazor sont exécutés dans le cadre d’une application standard ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="afa1a-162">When hosted server-side, Blazor components are run as part of a normal ASP.NET Core app.</span></span> <span data-ttu-id="afa1a-163">Lorsqu’ils sont hébergés dans le navigateur avec WebAssembly, les composants Blazor utilisent un modèle d’hébergement similaire.</span><span class="sxs-lookup"><span data-stu-id="afa1a-163">When hosted in the browser with WebAssembly, Blazor components use a similar hosting model.</span></span> <span data-ttu-id="afa1a-164">La différence est que les composants sont exécutés comme un service distinct de l’un des processus backend.</span><span class="sxs-lookup"><span data-stu-id="afa1a-164">The difference is the components are run as a separate service from any of the backend processes.</span></span> <span data-ttu-id="afa1a-165">Quoi qu’il en soit, la startup est similaire.</span><span class="sxs-lookup"><span data-stu-id="afa1a-165">Either way, the startup is similar.</span></span>

<span data-ttu-id="afa1a-166">Le *fichier Global.asax.cs* est la page de démarrage par défaut pour les projets Web Forms.</span><span class="sxs-lookup"><span data-stu-id="afa1a-166">The *Global.asax.cs* file is the default startup page for Web Forms projects.</span></span> <span data-ttu-id="afa1a-167">Dans le projet eShop, ce fichier configure le conteneur Inversion of Control (IoC) et gère les différents événements du cycle de vie de l’application ou de la demande.</span><span class="sxs-lookup"><span data-stu-id="afa1a-167">In the eShop project, this file configures the Inversion of Control (IoC) container and handles the various lifecycle events of the app or request.</span></span> <span data-ttu-id="afa1a-168">Certains de ces événements sont traités avec `Application_BeginRequest`middleware (comme ).</span><span class="sxs-lookup"><span data-stu-id="afa1a-168">Some of these events are handled with middleware (such as `Application_BeginRequest`).</span></span> <span data-ttu-id="afa1a-169">D’autres événements nécessitent la suppression de services spécifiques par injection de dépendance (DI).</span><span class="sxs-lookup"><span data-stu-id="afa1a-169">Other events require the overriding of specific services via dependency injection (DI).</span></span>

<span data-ttu-id="afa1a-170">À titre d’exemple, le *fichier Global.asax.cs* pour eShop, contient le code suivant :</span><span class="sxs-lookup"><span data-stu-id="afa1a-170">By way of example, the *Global.asax.cs* file for eShop, contains the following code:</span></span>

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
    /// http://docs.autofac.org/en/latest/integration/webforms.html
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

<span data-ttu-id="afa1a-171">Le fichier précédent `Startup` devient la classe dans Le serveur-côté Blazor:</span><span class="sxs-lookup"><span data-stu-id="afa1a-171">The preceding file becomes the `Startup` class in server-side Blazor:</span></span>

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

<span data-ttu-id="afa1a-172">Un changement important que vous pouvez remarquer à partir de formulaires Web est la proéminence de DI.</span><span class="sxs-lookup"><span data-stu-id="afa1a-172">One significant change you may notice from Web Forms is the prominence of DI.</span></span> <span data-ttu-id="afa1a-173">DI a été un principe directeur dans la conception ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="afa1a-173">DI has been a guiding principle in the ASP.NET Core design.</span></span> <span data-ttu-id="afa1a-174">Il soutient la personnalisation de presque tous les aspects du cadre ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="afa1a-174">It supports customization of almost all aspects of the ASP.NET Core framework.</span></span> <span data-ttu-id="afa1a-175">Il y a même un fournisseur de services intégré qui peut être utilisé pour de nombreux scénarios.</span><span class="sxs-lookup"><span data-stu-id="afa1a-175">There's even a built-in service provider that can be used for many scenarios.</span></span> <span data-ttu-id="afa1a-176">Si une personnalisation plus grande est nécessaire, elle peut être soutenue par les nombreux projets communautaires.</span><span class="sxs-lookup"><span data-stu-id="afa1a-176">If more customization is required, it can be supported by the many community projects.</span></span> <span data-ttu-id="afa1a-177">Par exemple, vous pouvez reporter votre investissement de bibliothèque DI tiers.</span><span class="sxs-lookup"><span data-stu-id="afa1a-177">For example, you can carry forward your third-party DI library investment.</span></span>

<span data-ttu-id="afa1a-178">Dans l’application eShop originale, il y a une certaine configuration pour la gestion de session.</span><span class="sxs-lookup"><span data-stu-id="afa1a-178">In the original eShop app, there's some configuration for session management.</span></span> <span data-ttu-id="afa1a-179">Étant donné que Blazor utilise ASP.NET Core SignalR pour la communication, l’état de session n’est pas pris en charge car les connexions peuvent se produire indépendamment d’un contexte HTTP.</span><span class="sxs-lookup"><span data-stu-id="afa1a-179">Since server-side Blazor uses ASP.NET Core SignalR for communication, session state isn't supported as the connections may occur independent of an HTTP context.</span></span> <span data-ttu-id="afa1a-180">Une application qui utilise l’état de session nécessite un backchitecting avant de fonctionner comme une application Blazor.</span><span class="sxs-lookup"><span data-stu-id="afa1a-180">An app that uses session state requires rearchitecting before running as a Blazor app.</span></span>

<span data-ttu-id="afa1a-181">Pour plus d’informations sur le démarrage de l’application, voir [App startup](app-startup.md).</span><span class="sxs-lookup"><span data-stu-id="afa1a-181">For more information about app startup, see [App startup](app-startup.md).</span></span>

## <a name="migrate-http-modules-and-handlers-to-middleware"></a><span data-ttu-id="afa1a-182">Migrer les modules et les gestionnaires HTTP vers middleware</span><span class="sxs-lookup"><span data-stu-id="afa1a-182">Migrate HTTP modules and handlers to middleware</span></span>

<span data-ttu-id="afa1a-183">Les modules ET les gestionnaires HTTP sont des modèles courants dans les formulaires Web pour contrôler le pipeline de demande HTTP.</span><span class="sxs-lookup"><span data-stu-id="afa1a-183">HTTP modules and handlers are common patterns in Web Forms to control the HTTP request pipeline.</span></span> <span data-ttu-id="afa1a-184">Classes qui `IHttpModule` `IHttpHandler` mettent en œuvre ou pourraient être enregistrées et traitent les demandes entrantes.</span><span class="sxs-lookup"><span data-stu-id="afa1a-184">Classes that implement `IHttpModule` or `IHttpHandler` could be registered and process incoming requests.</span></span> <span data-ttu-id="afa1a-185">Web Forms configure des modules et des gestionnaires dans le fichier *web.config.*</span><span class="sxs-lookup"><span data-stu-id="afa1a-185">Web Forms configures modules and handlers in the *web.config* file.</span></span> <span data-ttu-id="afa1a-186">Web Forms est également fortement basé sur la gestion des événements du cycle de vie de l’application.</span><span class="sxs-lookup"><span data-stu-id="afa1a-186">Web Forms is also heavily based on app lifecycle event handling.</span></span> <span data-ttu-id="afa1a-187">ASP.NET Core utilise plutôt middleware.</span><span class="sxs-lookup"><span data-stu-id="afa1a-187">ASP.NET Core uses middleware instead.</span></span> <span data-ttu-id="afa1a-188">Middleware est enregistré `Configure` dans `Startup` la méthode de la classe.</span><span class="sxs-lookup"><span data-stu-id="afa1a-188">Middleware is registered in the `Configure` method of the `Startup` class.</span></span> <span data-ttu-id="afa1a-189">L’ordre d’exécution De Middleware est déterminé par l’ordre d’enregistrement.</span><span class="sxs-lookup"><span data-stu-id="afa1a-189">Middleware execution order is determined by the registration order.</span></span>

<span data-ttu-id="afa1a-190">Dans la section [Processus de démarrage Enable,](#enable-startup-process) un événement `Application_BeginRequest` de cycle de vie a été soulevé par Web Forms comme méthode.</span><span class="sxs-lookup"><span data-stu-id="afa1a-190">In the [Enable startup process](#enable-startup-process) section, a lifecycle event was raised by Web Forms as the `Application_BeginRequest` method.</span></span> <span data-ttu-id="afa1a-191">Cet événement n’est pas disponible dans ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="afa1a-191">This event isn't available in ASP.NET Core.</span></span> <span data-ttu-id="afa1a-192">Une façon d’atteindre ce comportement est de mettre en œuvre middleware comme on le voit dans *l’exemple de* fichier Startup.cs.</span><span class="sxs-lookup"><span data-stu-id="afa1a-192">One way to achieve this behavior is to implement middleware as seen in the *Startup.cs* file example.</span></span> <span data-ttu-id="afa1a-193">Ce middleware fait la même logique, puis transfère le contrôle au prochain gestionnaire dans le pipeline middleware.</span><span class="sxs-lookup"><span data-stu-id="afa1a-193">This middleware does the same logic and then transfers control to the next handler in the middleware pipeline.</span></span>

<span data-ttu-id="afa1a-194">Pour plus d’informations sur les modules et les gestionnaires de migration, voir [les gestionnaires et modules Migrate HTTP pour ASP.NET Core middleware](/aspnet/core/migration/http-modules).</span><span class="sxs-lookup"><span data-stu-id="afa1a-194">For more information on migrating modules and handlers, see [Migrate HTTP handlers and modules to ASP.NET Core middleware](/aspnet/core/migration/http-modules).</span></span>

## <a name="migrate-static-files"></a><span data-ttu-id="afa1a-195">Migrer les fichiers statiques</span><span class="sxs-lookup"><span data-stu-id="afa1a-195">Migrate static files</span></span>

<span data-ttu-id="afa1a-196">Pour servir des fichiers statiques (par exemple, HTML, CSS, images et JavaScript), les fichiers doivent être exposés par middleware.</span><span class="sxs-lookup"><span data-stu-id="afa1a-196">To serve static files (for example, HTML, CSS, images, and JavaScript), the files must be exposed by middleware.</span></span> <span data-ttu-id="afa1a-197">L’appel de la `UseStaticFiles` méthode permet de servir des fichiers statiques à partir du chemin de racine web.</span><span class="sxs-lookup"><span data-stu-id="afa1a-197">Calling the `UseStaticFiles` method enables the serving of static files from the web root path.</span></span> <span data-ttu-id="afa1a-198">Le répertoire par défaut de racine web est *wwwroot*, mais il peut être personnalisé.</span><span class="sxs-lookup"><span data-stu-id="afa1a-198">The default web root directory is *wwwroot*, but it can be customized.</span></span> <span data-ttu-id="afa1a-199">Comme inclus `Configure` dans la méthode `Startup` de la classe eShop:</span><span class="sxs-lookup"><span data-stu-id="afa1a-199">As included in the `Configure` method of eShop's `Startup` class:</span></span>

```csharp
public void Configure(IApplicationBuilder app)
{
    ...

    app.UseStaticFiles();

    ...
}
```

<span data-ttu-id="afa1a-200">Le projet eShop permet un accès statique de base aux fichiers.</span><span class="sxs-lookup"><span data-stu-id="afa1a-200">The eShop project enables basic static file access.</span></span> <span data-ttu-id="afa1a-201">De nombreuses personnalisations sont disponibles pour l’accès statique aux fichiers.</span><span class="sxs-lookup"><span data-stu-id="afa1a-201">There are many customizations available for static file access.</span></span> <span data-ttu-id="afa1a-202">Pour obtenir des informations sur l’activation de fichiers par défaut ou d’un navigateur de fichiers, consultez [les fichiers statiques dans ASP.NET Core](/aspnet/core/fundamentals/static-files).</span><span class="sxs-lookup"><span data-stu-id="afa1a-202">For information on enabling default files or a file browser, see [Static files in ASP.NET Core](/aspnet/core/fundamentals/static-files).</span></span>

## <a name="migrate-runtime-bundling-and-minification-setup"></a><span data-ttu-id="afa1a-203">Migrer le regroupement et la minification de l’exécution</span><span class="sxs-lookup"><span data-stu-id="afa1a-203">Migrate runtime bundling and minification setup</span></span>

<span data-ttu-id="afa1a-204">Le regroupement et la minification sont des techniques d’optimisation des performances pour réduire le nombre et la taille des demandes de serveur pour récupérer certains types de fichiers.</span><span class="sxs-lookup"><span data-stu-id="afa1a-204">Bundling and minification are performance optimization techniques for reducing the number and size of server requests to retrieve certain file types.</span></span> <span data-ttu-id="afa1a-205">JavaScript et CSS subissent souvent une forme quelconque de regroupement ou de minification avant d’être envoyés au client.</span><span class="sxs-lookup"><span data-stu-id="afa1a-205">JavaScript and CSS often undergo some form of bundling or minification before being sent to the client.</span></span> <span data-ttu-id="afa1a-206">Dans ASP.NET formulaires Web, ces optimisations sont traitées au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="afa1a-206">In ASP.NET Web Forms, these optimizations are handled at runtime.</span></span> <span data-ttu-id="afa1a-207">Les conventions d’optimisation sont *définies App_Start/BundleConfig.cs.*</span><span class="sxs-lookup"><span data-stu-id="afa1a-207">The optimization conventions are defined an *App_Start/BundleConfig.cs* file.</span></span> <span data-ttu-id="afa1a-208">Dans ASP.NET Core, une approche plus déclarative est adoptée.</span><span class="sxs-lookup"><span data-stu-id="afa1a-208">In ASP.NET Core, a more declarative approach is adopted.</span></span> <span data-ttu-id="afa1a-209">Un fichier répertorie les fichiers à minifier, ainsi que des paramètres de minification spécifiques.</span><span class="sxs-lookup"><span data-stu-id="afa1a-209">A file lists the files to be minified, along with specific minification settings.</span></span>

<span data-ttu-id="afa1a-210">Pour plus d’informations sur le regroupement et la minification, voir [Bundle et minifier les actifs statiques dans ASP.NET Core](/aspnet/core/client-side/bundling-and-minification).</span><span class="sxs-lookup"><span data-stu-id="afa1a-210">For more information on bundling and minification, see [Bundle and minify static assets in ASP.NET Core](/aspnet/core/client-side/bundling-and-minification).</span></span>

## <a name="migrate-aspx-pages"></a><span data-ttu-id="afa1a-211">Migrer les pages ASPX</span><span class="sxs-lookup"><span data-stu-id="afa1a-211">Migrate ASPX pages</span></span>

<span data-ttu-id="afa1a-212">Une page d’une application Web Forms est un fichier avec l’extension *.aspx.*</span><span class="sxs-lookup"><span data-stu-id="afa1a-212">A page in a Web Forms app is a file with the *.aspx* extension.</span></span> <span data-ttu-id="afa1a-213">Une page Web Forms peut souvent être cartographiée sur un composant de Blazor.</span><span class="sxs-lookup"><span data-stu-id="afa1a-213">A Web Forms page can often be mapped to a component in Blazor.</span></span> <span data-ttu-id="afa1a-214">Un composant Blazor est rédigé dans un fichier avec l’extension *.razor.*</span><span class="sxs-lookup"><span data-stu-id="afa1a-214">A Blazor component is authored in a file with the *.razor* extension.</span></span> <span data-ttu-id="afa1a-215">Pour le projet eShop, cinq pages sont converties en une page Razor.</span><span class="sxs-lookup"><span data-stu-id="afa1a-215">For the eShop project, five pages are converted to a Razor page.</span></span>

<span data-ttu-id="afa1a-216">Par exemple, la vue des détails est composée de trois fichiers dans le projet Web Forms: *Details.aspx*, *Details.aspx.cs*, et *Details.aspx.designer.cs*.</span><span class="sxs-lookup"><span data-stu-id="afa1a-216">For example, the details view is comprised of three files in the Web Forms project: *Details.aspx*, *Details.aspx.cs*, and *Details.aspx.designer.cs*.</span></span> <span data-ttu-id="afa1a-217">Lors de la conversion à Blazor, le code-derrière et le balisage sont combinés en *Details.razor*.</span><span class="sxs-lookup"><span data-stu-id="afa1a-217">When converting to Blazor, the code-behind and markup are combined into *Details.razor*.</span></span> <span data-ttu-id="afa1a-218">La compilation Razor (équivalente à ce qu’il y a dans les fichiers *.designer.cs)* est stockée dans le répertoire *obj* et ne sont pas, par défaut, visible dans **Solution Explorer**.</span><span class="sxs-lookup"><span data-stu-id="afa1a-218">Razor compilation (equivalent to what's in *.designer.cs* files) is stored in the *obj* directory and aren't, by default, viewable in **Solution Explorer**.</span></span> <span data-ttu-id="afa1a-219">La page Formulaires Web se compose de la balisage suivante :</span><span class="sxs-lookup"><span data-stu-id="afa1a-219">The Web Forms page consists of the following markup:</span></span>

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

<span data-ttu-id="afa1a-220">Le code de balisage précédent comprend le code suivant :</span><span class="sxs-lookup"><span data-stu-id="afa1a-220">The preceding markup's code-behind includes the following code:</span></span>

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

<span data-ttu-id="afa1a-221">Lorsqu’elle est convertie en Blazor, la page Web Forms se traduit par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="afa1a-221">When converted to Blazor, the Web Forms page translates to the following code:</span></span>

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

<span data-ttu-id="afa1a-222">Notez que le code et le balisage sont dans le même fichier.</span><span class="sxs-lookup"><span data-stu-id="afa1a-222">Notice that the code and markup are in the same file.</span></span> <span data-ttu-id="afa1a-223">Tous les services requis `@inject` sont rendus accessibles avec l’attribut.</span><span class="sxs-lookup"><span data-stu-id="afa1a-223">Any required services are made accessible with the `@inject` attribute.</span></span> <span data-ttu-id="afa1a-224">Selon `@page` la directive, cette page peut `Catalog/Details/{id}` être consultée à l’itinéraire.</span><span class="sxs-lookup"><span data-stu-id="afa1a-224">Per the `@page` directive, this page can be accessed at the `Catalog/Details/{id}` route.</span></span> <span data-ttu-id="afa1a-225">La valeur du propriétaire `{id}` de la place de l’itinéraire a été limitée à un intégriste.</span><span class="sxs-lookup"><span data-stu-id="afa1a-225">The value of the route's `{id}` placeholder has been constrained to an integer.</span></span> <span data-ttu-id="afa1a-226">Tel que décrit dans la section [de routage,](pages-routing-layouts.md) contrairement aux formulaires Web, un composant Razor indique explicitement son itinéraire et tous les paramètres qui sont inclus.</span><span class="sxs-lookup"><span data-stu-id="afa1a-226">As described in the [routing](pages-routing-layouts.md) section, unlike Web Forms, a Razor component explicitly states its route and any parameters that are included.</span></span> <span data-ttu-id="afa1a-227">De nombreux contrôles sur les formulaires Web peuvent ne pas avoir de contreparties exactes à Blazor.</span><span class="sxs-lookup"><span data-stu-id="afa1a-227">Many Web Forms controls may not have exact counterparts in Blazor.</span></span> <span data-ttu-id="afa1a-228">Il ya souvent un extrait HTML équivalent qui servira le même but.</span><span class="sxs-lookup"><span data-stu-id="afa1a-228">There's often an equivalent HTML snippet that will serve the same purpose.</span></span> <span data-ttu-id="afa1a-229">Par exemple, `<asp:Label />` le contrôle peut `<label>` être remplacé par un élément HTML.</span><span class="sxs-lookup"><span data-stu-id="afa1a-229">For example, the `<asp:Label />` control can be replaced with an HTML `<label>` element.</span></span>

### <a name="model-validation-in-blazor"></a><span data-ttu-id="afa1a-230">Validation du modèle à Blazor</span><span class="sxs-lookup"><span data-stu-id="afa1a-230">Model validation in Blazor</span></span>

<span data-ttu-id="afa1a-231">Si votre code Formulaires Web inclut la validation, vous pouvez transférer une grande partie de ce que vous avez avec peu ou pas de modifications.</span><span class="sxs-lookup"><span data-stu-id="afa1a-231">If your Web Forms code includes validation, you can transfer much of what you have with little-to-no changes.</span></span> <span data-ttu-id="afa1a-232">Un avantage à courir dans Blazor est que la même logique de validation peut être exécutée sans avoir besoin de JavaScript personnalisé.</span><span class="sxs-lookup"><span data-stu-id="afa1a-232">A benefit to running in Blazor is that the same validation logic can be run without needing custom JavaScript.</span></span> <span data-ttu-id="afa1a-233">Les annotations de données permettent une validation facile du modèle.</span><span class="sxs-lookup"><span data-stu-id="afa1a-233">Data annotations enable easy model validation.</span></span>

<span data-ttu-id="afa1a-234">Par exemple, la page *Create.aspx* a un formulaire de saisie de données avec validation.</span><span class="sxs-lookup"><span data-stu-id="afa1a-234">For example, the *Create.aspx* page has a data entry form with validation.</span></span> <span data-ttu-id="afa1a-235">Un exemple d’extrait ressemblerait à ceci :</span><span class="sxs-lookup"><span data-stu-id="afa1a-235">An example snippet would look like this:</span></span>

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

<span data-ttu-id="afa1a-236">Dans Blazor, la majoration équivalente est fournie dans un fichier *Create.razor* :</span><span class="sxs-lookup"><span data-stu-id="afa1a-236">In Blazor, the equivalent markup is provided in a *Create.razor* file:</span></span>

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

<span data-ttu-id="afa1a-237">Le `EditForm` contexte comprend un support de validation et peut être enroulé autour de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="afa1a-237">The `EditForm` context includes validation support and can be wrapped around input.</span></span> <span data-ttu-id="afa1a-238">Les annotations de données sont un moyen commun d’ajouter la validation.</span><span class="sxs-lookup"><span data-stu-id="afa1a-238">Data annotations are a common way to add validation.</span></span> <span data-ttu-id="afa1a-239">Un tel support de `DataAnnotationsValidator` validation peut être ajouté via le composant.</span><span class="sxs-lookup"><span data-stu-id="afa1a-239">Such validation support can be added via the `DataAnnotationsValidator` component.</span></span> <span data-ttu-id="afa1a-240">Pour plus d’informations sur ce mécanisme, voir [ASP.NET formulaires Core Blazor et la validation](/aspnet/core/blazor/forms-validation).</span><span class="sxs-lookup"><span data-stu-id="afa1a-240">For more information on this mechanism, see [ASP.NET Core Blazor forms and validation](/aspnet/core/blazor/forms-validation).</span></span>

## <a name="migrate-built-in-web-forms-controls"></a><span data-ttu-id="afa1a-241">Migrer les commandes intégrées des formulaires Web</span><span class="sxs-lookup"><span data-stu-id="afa1a-241">Migrate built-in Web Forms controls</span></span>

<span data-ttu-id="afa1a-242">*Ce contenu est à venir.*</span><span class="sxs-lookup"><span data-stu-id="afa1a-242">*This content is coming soon.*</span></span>

## <a name="migrate-configuration"></a><span data-ttu-id="afa1a-243">Migrer une configuration</span><span class="sxs-lookup"><span data-stu-id="afa1a-243">Migrate configuration</span></span>

<span data-ttu-id="afa1a-244">Dans un projet Web Forms, les données de configuration sont le plus souvent stockées dans le fichier *web.config.*</span><span class="sxs-lookup"><span data-stu-id="afa1a-244">In a Web Forms project, configuration data is most commonly stored in the *web.config* file.</span></span> <span data-ttu-id="afa1a-245">Les données de configuration `ConfigurationManager`sont accessibles avec .</span><span class="sxs-lookup"><span data-stu-id="afa1a-245">The configuration data is accessed with `ConfigurationManager`.</span></span> <span data-ttu-id="afa1a-246">Les services étaient souvent nécessaires pour analyser les objets.</span><span class="sxs-lookup"><span data-stu-id="afa1a-246">Services were often required to parse objects.</span></span> <span data-ttu-id="afa1a-247">Avec .NET Framework 4.7.2, la composition `ConfigurationBuilders`a été ajoutée à la configuration via .</span><span class="sxs-lookup"><span data-stu-id="afa1a-247">With .NET Framework 4.7.2, composability was added to configuration via `ConfigurationBuilders`.</span></span> <span data-ttu-id="afa1a-248">Ces constructeurs ont permis aux développeurs d’ajouter diverses sources de configuration qui ont ensuite été composées au moment de l’exécution pour récupérer les valeurs nécessaires.</span><span class="sxs-lookup"><span data-stu-id="afa1a-248">These builders allowed developers to add various sources for configuration that was then composed at runtime to retrieve the necessary values.</span></span>

<span data-ttu-id="afa1a-249">ASP.NET Core a introduit un système de configuration flexible qui vous permet de définir la source de configuration ou les sources utilisées par votre application et votre déploiement.</span><span class="sxs-lookup"><span data-stu-id="afa1a-249">ASP.NET Core introduced a flexible configuration system that allows you to define the configuration source or sources used by your app and deployment.</span></span> <span data-ttu-id="afa1a-250">L’infrastructure `ConfigurationBuilder` que vous utilisez peut-être dans votre application Web Forms a été calquée sur les concepts utilisés dans le système de configuration ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="afa1a-250">The `ConfigurationBuilder` infrastructure that you may be using in your Web Forms app was modeled after the concepts used in the ASP.NET Core configuration system.</span></span>

<span data-ttu-id="afa1a-251">L’extrait suivant montre comment le projet Web Forms eShop utilise *web.config* pour stocker les valeurs de configuration :</span><span class="sxs-lookup"><span data-stu-id="afa1a-251">The following snippet demonstrates how the Web Forms eShop project uses *web.config* to store configuration values:</span></span>

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

<span data-ttu-id="afa1a-252">Il est courant que les secrets, tels que les chaînes de connexion de base de données, soient stockés dans le *web.config*. Les secrets sont inévitablement persistants dans des endroits non sécurisés, tels que le contrôle des sources.</span><span class="sxs-lookup"><span data-stu-id="afa1a-252">It's common for secrets, such as database connection strings, to be stored within the *web.config*. The secrets are inevitably persisted in unsecure locations, such as source control.</span></span> <span data-ttu-id="afa1a-253">Avec Blazor sur ASP.NET Core, la configuration XML précédente est remplacée par le JSON suivant :</span><span class="sxs-lookup"><span data-stu-id="afa1a-253">With Blazor on ASP.NET Core, the preceding XML-based configuration is replaced with the following JSON:</span></span>

```json
{
  "ConnectionStrings": {
    "CatalogDBContext": "Data Source=(localdb)\\MSSQLLocalDB; Initial Catalog=Microsoft.eShopOnContainers.Services.CatalogDb; Integrated Security=True; MultipleActiveResultSets=True;"
  },
  "UseMockData": true,
  "UseCustomizationData": false
}
```

<span data-ttu-id="afa1a-254">JSON est le format de configuration par défaut; cependant, ASP.NET Core prend en charge de nombreux autres formats, y compris XML.</span><span class="sxs-lookup"><span data-stu-id="afa1a-254">JSON is the default configuration format; however, ASP.NET Core supports many other formats, including XML.</span></span> <span data-ttu-id="afa1a-255">Il existe également plusieurs formats soutenus par la communauté.</span><span class="sxs-lookup"><span data-stu-id="afa1a-255">There are also several community-supported formats.</span></span>

<span data-ttu-id="afa1a-256">Le constructeur de la classe du `Startup` projet Blazor accepte une instance par le biais d’une `IConfiguration` technique DI connue sous le nom d’injection de constructeurs :</span><span class="sxs-lookup"><span data-stu-id="afa1a-256">The constructor in the Blazor project's `Startup` class accepts an `IConfiguration` instance through a DI technique known as constructor injection:</span></span>

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

<span data-ttu-id="afa1a-257">Par défaut, variables de l’environnement, fichiers JSON *(appsettings.json* et *appsettings. Les*options de ligne de commande et d’environnement sont enregistrées comme sources de configuration valides dans l’objet de configuration.</span><span class="sxs-lookup"><span data-stu-id="afa1a-257">By default, environment variables, JSON files (*appsettings.json* and *appsettings.{Environment}.json*), and command-line options are registered as valid configuration sources in the configuration object.</span></span> <span data-ttu-id="afa1a-258">Les sources de configuration `Configuration[key]`peuvent être consultées via .</span><span class="sxs-lookup"><span data-stu-id="afa1a-258">The configuration sources can be accessed via `Configuration[key]`.</span></span> <span data-ttu-id="afa1a-259">Une technique plus avancée consiste à lier les données de configuration aux objets utilisant le modèle d’options.</span><span class="sxs-lookup"><span data-stu-id="afa1a-259">A more advanced technique is to bind the configuration data to objects using the options pattern.</span></span> <span data-ttu-id="afa1a-260">Pour plus d’informations sur la configuration et le modèle d’options, voir [Configuration dans ASP.NET modèle de base](/aspnet/core/fundamentals/configuration/) et [d’options dans ASP.NET Core](/aspnet/core/fundamentals/configuration/options), respectivement.</span><span class="sxs-lookup"><span data-stu-id="afa1a-260">For more information on configuration and the options pattern, see [Configuration in ASP.NET Core](/aspnet/core/fundamentals/configuration/) and [Options pattern in ASP.NET Core](/aspnet/core/fundamentals/configuration/options), respectively.</span></span>

## <a name="migrate-data-access"></a><span data-ttu-id="afa1a-261">Migrer l’accès aux données</span><span class="sxs-lookup"><span data-stu-id="afa1a-261">Migrate data access</span></span>

<span data-ttu-id="afa1a-262">L’accès aux données est un aspect important de toute application.</span><span class="sxs-lookup"><span data-stu-id="afa1a-262">Data access is an important aspect of any app.</span></span> <span data-ttu-id="afa1a-263">Le projet eShop stocke les informations de catalogue dans une base de données et récupère les données avec Entity Framework (EF) 6.</span><span class="sxs-lookup"><span data-stu-id="afa1a-263">The eShop project stores catalog information in a database and retrieves the data with Entity Framework (EF) 6.</span></span> <span data-ttu-id="afa1a-264">Étant donné que EF 6 est pris en charge dans .NET Core 3.0, le projet peut continuer à l’utiliser.</span><span class="sxs-lookup"><span data-stu-id="afa1a-264">Since EF 6 is supported in .NET Core 3.0, the project can continue to use it.</span></span>

<span data-ttu-id="afa1a-265">Les changements suivants liés à l’EF étaient nécessaires pour eShop :</span><span class="sxs-lookup"><span data-stu-id="afa1a-265">The following EF-related changes were necessary to eShop:</span></span>

- <span data-ttu-id="afa1a-266">Dans .NET Framework, l’objet `DbContext` accepte une chaîne du nom de *formulaire-ConnectionString* et utilise la chaîne de connexion à partir de `ConfigurationManager.AppSettings[ConnectionString]` se connecter.</span><span class="sxs-lookup"><span data-stu-id="afa1a-266">In .NET Framework, the `DbContext` object accepts a string of the form *name=ConnectionString* and uses the connection string from `ConfigurationManager.AppSettings[ConnectionString]` to connect.</span></span> <span data-ttu-id="afa1a-267">Dans .NET Core, ce n’est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="afa1a-267">In .NET Core, this isn't supported.</span></span> <span data-ttu-id="afa1a-268">La chaîne de connexion doit être fournie.</span><span class="sxs-lookup"><span data-stu-id="afa1a-268">The connection string must be supplied.</span></span>
- <span data-ttu-id="afa1a-269">La base de données a été consultée de façon synchrone.</span><span class="sxs-lookup"><span data-stu-id="afa1a-269">The database was accessed in a synchronous way.</span></span> <span data-ttu-id="afa1a-270">Bien que cela fonctionne, l’évolutivité peut en souffrir.</span><span class="sxs-lookup"><span data-stu-id="afa1a-270">Though this works, scalability may suffer.</span></span> <span data-ttu-id="afa1a-271">Cette logique doit être déplacée à un modèle asynchrone.</span><span class="sxs-lookup"><span data-stu-id="afa1a-271">This logic should be moved to an asynchronous pattern.</span></span>

<span data-ttu-id="afa1a-272">Bien qu’il n’y ait pas le même support natif pour la liaison de dataset, Blazor fournit la flexibilité et la puissance avec son support C dans une page Razor.</span><span class="sxs-lookup"><span data-stu-id="afa1a-272">Although there isn't the same native support for dataset binding, Blazor provides flexibility and power with its C# support in a Razor page.</span></span> <span data-ttu-id="afa1a-273">Par exemple, vous pouvez effectuer des calculs et afficher le résultat.</span><span class="sxs-lookup"><span data-stu-id="afa1a-273">For example, you can perform calculations and display the result.</span></span> <span data-ttu-id="afa1a-274">Pour plus d’informations sur les modèles de données dans Blazor, consultez le chapitre [d’accès aux données.](data.md)</span><span class="sxs-lookup"><span data-stu-id="afa1a-274">For more information on data patterns in Blazor, see the [Data access](data.md) chapter.</span></span>

## <a name="architectural-changes"></a><span data-ttu-id="afa1a-275">Changements architecturaux</span><span class="sxs-lookup"><span data-stu-id="afa1a-275">Architectural changes</span></span>

<span data-ttu-id="afa1a-276">Enfin, il y a quelques différences architecturales importantes à considérer lors de la migration vers Blazor.</span><span class="sxs-lookup"><span data-stu-id="afa1a-276">Finally, there are some important architectural differences to consider when migrating to Blazor.</span></span> <span data-ttu-id="afa1a-277">Bon nombre de ces modifications s’appliquent à tout ce qui est basé sur .NET Core ou ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="afa1a-277">Many of these changes are applicable to anything based on .NET Core or ASP.NET Core.</span></span>

<span data-ttu-id="afa1a-278">Parce que Blazor est construit sur .NET Core, il ya des considérations à assurer le soutien sur .NET Core.</span><span class="sxs-lookup"><span data-stu-id="afa1a-278">Because Blazor is built on .NET Core, there are considerations in ensuring support on .NET Core.</span></span> <span data-ttu-id="afa1a-279">Voici quelques-uns des principaux changements:</span><span class="sxs-lookup"><span data-stu-id="afa1a-279">Some of the major changes include the removal of the following features:</span></span>

- <span data-ttu-id="afa1a-280">AppDomains multiples</span><span class="sxs-lookup"><span data-stu-id="afa1a-280">Multiple AppDomains</span></span>
- <span data-ttu-id="afa1a-281">Communication à distance</span><span class="sxs-lookup"><span data-stu-id="afa1a-281">Remoting</span></span>
- <span data-ttu-id="afa1a-282">Sécurité d'accès du code</span><span class="sxs-lookup"><span data-stu-id="afa1a-282">Code Access Security (CAS)</span></span>
- <span data-ttu-id="afa1a-283">Transparence de la sécurité</span><span class="sxs-lookup"><span data-stu-id="afa1a-283">Security Transparency</span></span>

<span data-ttu-id="afa1a-284">Pour plus d’informations sur les techniques pour identifier les changements nécessaires pour soutenir l’exécution sur .NET Core, voir [Port votre code de .NET Framework à .NET Core](/dotnet/core/porting).</span><span class="sxs-lookup"><span data-stu-id="afa1a-284">For more information on techniques to identify necessary changes to support running on .NET Core, see [Port your code from .NET Framework to .NET Core](/dotnet/core/porting).</span></span>

<span data-ttu-id="afa1a-285">ASP.NET Core est une version réinventée de ASP.NET et a quelques changements qui peuvent ne pas sembler évidents au départ.</span><span class="sxs-lookup"><span data-stu-id="afa1a-285">ASP.NET Core is a reimagined version of ASP.NET and has some changes that may not initially seem obvious.</span></span> <span data-ttu-id="afa1a-286">Les principaux changements sont les :</span><span class="sxs-lookup"><span data-stu-id="afa1a-286">The main changes are:</span></span>

- <span data-ttu-id="afa1a-287">Pas de contexte de synchronisation, ce `HttpContext.Current` `Thread.CurrentPrincipal`qui signifie qu’il n’y a pas, ou d’autres accesseurs statiques</span><span class="sxs-lookup"><span data-stu-id="afa1a-287">No synchronization context, which means there's no `HttpContext.Current`, `Thread.CurrentPrincipal`, or other static accessors</span></span>
- <span data-ttu-id="afa1a-288">Pas de copie d’ombre</span><span class="sxs-lookup"><span data-stu-id="afa1a-288">No shadow copying</span></span>
- <span data-ttu-id="afa1a-289">Pas de file d’attente de demande</span><span class="sxs-lookup"><span data-stu-id="afa1a-289">No request queue</span></span>

<span data-ttu-id="afa1a-290">De nombreuses opérations dans ASP.NET Core sont asynchrones, ce qui permet un déchargement plus facile des tâches I/O-bound.</span><span class="sxs-lookup"><span data-stu-id="afa1a-290">Many operations in ASP.NET Core are asynchronous, which allows easier off-loading of I/O-bound tasks.</span></span> <span data-ttu-id="afa1a-291">Il est important de ne `Task.Wait()` `Task.GetResult()`jamais bloquer en utilisant ou , qui peut rapidement épuiser les ressources de piscine de fil.</span><span class="sxs-lookup"><span data-stu-id="afa1a-291">It's important to never block by using `Task.Wait()` or `Task.GetResult()`, which can quickly exhaust thread pool resources.</span></span>

## <a name="migration-conclusion"></a><span data-ttu-id="afa1a-292">Conclusion migratoire</span><span class="sxs-lookup"><span data-stu-id="afa1a-292">Migration conclusion</span></span>

<span data-ttu-id="afa1a-293">À ce stade, vous avez vu de nombreux exemples de ce qu’il faut pour déplacer un projet Web Forms à Blazor.</span><span class="sxs-lookup"><span data-stu-id="afa1a-293">At this point, you've seen many examples of what it takes to move a Web Forms project to Blazor.</span></span> <span data-ttu-id="afa1a-294">Pour un exemple complet, voir le projet [eShopOnBlazor.](https://github.com/dotnet-architecture/eShopOnBlazor)</span><span class="sxs-lookup"><span data-stu-id="afa1a-294">For a full example, see the [eShopOnBlazor](https://github.com/dotnet-architecture/eShopOnBlazor) project.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="afa1a-295">Précédent</span><span class="sxs-lookup"><span data-stu-id="afa1a-295">Previous</span></span>](security-authentication-authorization.md)
