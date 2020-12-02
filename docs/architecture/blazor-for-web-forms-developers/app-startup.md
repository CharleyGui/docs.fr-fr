---
title: Démarrage des applications
description: Découvrez comment définir la logique de démarrage de votre application.
author: csharpfritz
ms.author: jefritz
ms.date: 11/20/2020
ms.openlocfilehash: d812079f84f67409334d07c4c10c5577446503be
ms.sourcegitcommit: 2f485e721f7f34b87856a51181b5b56624b31fd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2020
ms.locfileid: "96509700"
---
# <a name="app-startup"></a><span data-ttu-id="a7314-103">Démarrage des applications</span><span class="sxs-lookup"><span data-stu-id="a7314-103">App startup</span></span>

<span data-ttu-id="a7314-104">Les applications écrites pour ASP.NET ont généralement un `global.asax.cs` fichier qui définit l' `Application_Start` événement qui contrôle quels services sont configurés et mis à disposition pour le rendu HTML et le traitement .net.</span><span class="sxs-lookup"><span data-stu-id="a7314-104">Applications that are written for ASP.NET typically have a `global.asax.cs` file that defines the `Application_Start` event that controls which services are configured and made available for both HTML rendering and .NET processing.</span></span> <span data-ttu-id="a7314-105">Ce chapitre explique en quoi les choses sont légèrement différentes avec ASP.NET Core et le serveur éblouissant.</span><span class="sxs-lookup"><span data-stu-id="a7314-105">This chapter looks at how things are slightly different with ASP.NET Core and Blazor Server.</span></span>

## <a name="application_start-and-web-forms"></a><span data-ttu-id="a7314-106">Application_Start et Web Forms</span><span class="sxs-lookup"><span data-stu-id="a7314-106">Application_Start and Web Forms</span></span>

<span data-ttu-id="a7314-107">La méthode Web Forms par défaut `Application_Start` a cessé de s’adapter à plusieurs années pour gérer de nombreuses tâches de configuration.</span><span class="sxs-lookup"><span data-stu-id="a7314-107">The default web forms `Application_Start` method has grown in purpose over years to handle many configuration tasks.</span></span>  <span data-ttu-id="a7314-108">Un nouveau projet Web Forms avec le modèle par défaut dans Visual Studio 2019 contient désormais la logique de configuration suivante :</span><span class="sxs-lookup"><span data-stu-id="a7314-108">A fresh web forms project with the default template in Visual Studio 2019 now contains the following configuration logic:</span></span>

- <span data-ttu-id="a7314-109">`RouteConfig` -Routage des URL de l’application</span><span class="sxs-lookup"><span data-stu-id="a7314-109">`RouteConfig` - Application URL routing</span></span>
- <span data-ttu-id="a7314-110">`BundleConfig` -CSS et regroupement JavaScript et minimisation</span><span class="sxs-lookup"><span data-stu-id="a7314-110">`BundleConfig` - CSS and JavaScript bundling and minification</span></span>

<span data-ttu-id="a7314-111">Chacun de ces fichiers se trouve dans le `App_Start` dossier et ne s’exécute qu’une seule fois au démarrage de notre application.</span><span class="sxs-lookup"><span data-stu-id="a7314-111">Each of these individual files resides in the `App_Start` folder and run only once at the start of our application.</span></span>  <span data-ttu-id="a7314-112">`RouteConfig` dans le modèle de projet par défaut, ajoute le `FriendlyUrlSettings` pour les Web Forms afin d’autoriser les URL d’application à omettre l' `.ASPX` extension de fichier.</span><span class="sxs-lookup"><span data-stu-id="a7314-112">`RouteConfig` in the default project template adds the `FriendlyUrlSettings` for web forms to allow application URLs to omit the `.ASPX` file extension.</span></span>  <span data-ttu-id="a7314-113">Le modèle par défaut contient également une directive qui fournit des codes d’état de redirection HTTP permanents (HTTP 301) pour les `.ASPX` pages vers l’URL conviviale avec le nom de fichier qui omet l’extension.</span><span class="sxs-lookup"><span data-stu-id="a7314-113">The default template also contains a directive that provides permanent HTTP redirect status codes (HTTP 301) for the `.ASPX` pages to the friendly URL with the file name that omits the extension.</span></span>

<span data-ttu-id="a7314-114">Avec ASP.NET Core et éblouissant, ces méthodes sont soit simplifiées et consolidées dans la `Startup` classe, soit supprimées en faveur des technologies Web courantes.</span><span class="sxs-lookup"><span data-stu-id="a7314-114">With ASP.NET Core and Blazor, these methods are either simplified and consolidated into the `Startup` class or they are eliminated in favor of common web technologies.</span></span>

## <a name="blazor-server-startup-structure"></a><span data-ttu-id="a7314-115">Structure de démarrage du serveur éblouissant</span><span class="sxs-lookup"><span data-stu-id="a7314-115">Blazor Server Startup Structure</span></span>

<span data-ttu-id="a7314-116">Les applications serveur éblouissantes résident sur une version ASP.NET Core 3,0 ou ultérieure.</span><span class="sxs-lookup"><span data-stu-id="a7314-116">Blazor Server applications reside on top of an ASP.NET Core 3.0 or later version.</span></span>  <span data-ttu-id="a7314-117">ASP.NET Core applications Web sont configurées à l’aide d’une paire de méthodes dans la `Startup.cs` classe sur le dossier racine de l’application.</span><span class="sxs-lookup"><span data-stu-id="a7314-117">ASP.NET Core web applications are configured through a pair of methods in the `Startup.cs` class on the root folder of the application.</span></span>  <span data-ttu-id="a7314-118">Le contenu par défaut de la classe Startup est indiqué ci-dessous</span><span class="sxs-lookup"><span data-stu-id="a7314-118">The Startup class's default content is listed below</span></span>

```csharp
public class Startup
{
  public Startup(IConfiguration configuration)
  {
    Configuration = configuration;
  }

  public IConfiguration Configuration { get; }

  // This method gets called by the runtime. Use this method to add services to the container.
  // For more information on how to configure your application, visit https://go.microsoft.com/fwlink/?LinkID=398940
  public void ConfigureServices(IServiceCollection services)
  {
    services.AddRazorPages();
    services.AddServerSideBlazor();
    services.AddSingleton<WeatherForecastService>();
  }

  // This method gets called by the runtime. Use this method to configure the HTTP request pipeline.
  public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
  {
    if (env.IsDevelopment())
    {
      app.UseDeveloperExceptionPage();
    }
    else
    {
      app.UseExceptionHandler("/Error");
      // The default HSTS value is 30 days. You may want to change this for production scenarios, see https://aka.ms/aspnetcore-hsts.
      app.UseHsts();
    }

    app.UseHttpsRedirection();
    app.UseStaticFiles();

    app.UseRouting();

    app.UseEndpoints(endpoints =>
    {
      endpoints.MapBlazorHub();
      endpoints.MapFallbackToPage("/_Host");
   });
  }
 }
```

<span data-ttu-id="a7314-119">À l’instar du reste de ASP.NET Core, la classe Startup est créée avec des principes d’injection de dépendances.</span><span class="sxs-lookup"><span data-stu-id="a7314-119">Like the rest of ASP.NET Core, the Startup class is created with dependency injection principles.</span></span>  <span data-ttu-id="a7314-120">Le `IConfiguration` est fourni au constructeur et est inclus dans une propriété publique pour un accès ultérieur pendant la configuration.</span><span class="sxs-lookup"><span data-stu-id="a7314-120">The `IConfiguration` is provided to the constructor and stashed in a public property for later access during configuration.</span></span>

<span data-ttu-id="a7314-121">La `ConfigureServices` méthode introduite dans ASP.net Core permet de configurer les différents services d’infrastructure ASP.net Core pour le conteneur d’injection de dépendances intégré du Framework.</span><span class="sxs-lookup"><span data-stu-id="a7314-121">The `ConfigureServices` method introduced in ASP.NET Core allows for the various ASP.NET Core framework services to be configured for the framework's built-in dependency injection container.</span></span>  <span data-ttu-id="a7314-122">Les différentes `services.Add*` méthodes ajoutent des services qui activent des fonctionnalités telles que l’authentification, les pages Razor, le routage de contrôleur MVC, signalr et les interactions de serveurs éblouissantes entre autres.</span><span class="sxs-lookup"><span data-stu-id="a7314-122">The various `services.Add*` methods add services that enable features such as authentication, razor pages, MVC controller routing, SignalR, and Blazor Server interactions among many others.</span></span>  <span data-ttu-id="a7314-123">Cette méthode n’était pas nécessaire dans Web Forms, car l’analyse et la gestion des fichiers ASPX, ASCX, ASHX et ASMX étaient définies en référençant ASP.NET dans le fichier de configuration web.config.</span><span class="sxs-lookup"><span data-stu-id="a7314-123">This method was not needed in web forms, as the parsing and handling of the ASPX, ASCX, ASHX, and ASMX files were defined by referencing ASP.NET in the web.config configuration file.</span></span>  <span data-ttu-id="a7314-124">Vous trouverez plus d’informations sur l’injection de dépendances dans ASP.NET Core dans la [documentation en ligne](/aspnet/core/fundamentals/dependency-injection).</span><span class="sxs-lookup"><span data-stu-id="a7314-124">More information about dependency injection in ASP.NET Core is available in the [online documentation](/aspnet/core/fundamentals/dependency-injection).</span></span>

<span data-ttu-id="a7314-125">La `Configure` méthode introduit le concept de pipeline HTTP pour ASP.net core.</span><span class="sxs-lookup"><span data-stu-id="a7314-125">The `Configure` method introduces the concept of the HTTP pipeline to ASP.NET Core.</span></span>  <span data-ttu-id="a7314-126">Dans cette méthode, nous déclarons de haut en bas l' [intergiciel](middleware.md) qui gère chaque demande envoyée à notre application.</span><span class="sxs-lookup"><span data-stu-id="a7314-126">In this method, we declare from top to bottom the [Middleware](middleware.md) that will handle every request sent to our application.</span></span> <span data-ttu-id="a7314-127">La plupart de ces fonctionnalités dans la configuration par défaut ont été disséminées dans les fichiers de configuration Web Forms et sont maintenant dans un emplacement unique pour faciliter la référence.</span><span class="sxs-lookup"><span data-stu-id="a7314-127">Most of these features in the default configuration were scattered across the web forms configuration files and are now in one place for ease of reference.</span></span>

<span data-ttu-id="a7314-128">Ne correspond plus à la configuration de la page d’erreurs personnalisée placée dans un `web.config` fichier, mais elle est désormais configurée pour toujours s’afficher si l’environnement de l’application n’est pas étiqueté `Development` .</span><span class="sxs-lookup"><span data-stu-id="a7314-128">No longer is the configuration of the custom error page placed in a `web.config` file, but now is configured to always be shown if the application environment is not labeled `Development`.</span></span>  <span data-ttu-id="a7314-129">En outre, les applications ASP.NET Core sont désormais configurées pour traiter les pages sécurisées avec TLS par défaut avec l' `UseHttpsRedirection` appel de méthode.</span><span class="sxs-lookup"><span data-stu-id="a7314-129">Additionally, ASP.NET Core applications are now configured to serve secure pages with TLS by default with the `UseHttpsRedirection` method call.</span></span>

<span data-ttu-id="a7314-130">Ensuite, une méthode de configuration inattendue est présentée à `UseStaticFiles` .</span><span class="sxs-lookup"><span data-stu-id="a7314-130">Next, an unexpected configuration method is listed to `UseStaticFiles`.</span></span>  <span data-ttu-id="a7314-131">Dans ASP.NET Core, la prise en charge des demandes de fichiers statiques (tels que les fichiers JavaScript, CSS et image) doit être explicitement activée, et seuls les fichiers du dossier *wwwroot* de l’application sont adressables par défaut.</span><span class="sxs-lookup"><span data-stu-id="a7314-131">In ASP.NET Core, support for requests for static files (like JavaScript, CSS, and image files) must be explicitly enabled, and only files in the app's *wwwroot* folder are publicly addressable by default.</span></span>

<span data-ttu-id="a7314-132">La ligne suivante est la première qui réplique l’une des options de configuration à partir de Web Forms : `UseRouting` .</span><span class="sxs-lookup"><span data-stu-id="a7314-132">The next line is the first that replicates one of the configuration options from web forms: `UseRouting`.</span></span>  <span data-ttu-id="a7314-133">Cette méthode ajoute le routeur ASP.NET Core au pipeline et peut être configurée ici ou dans les fichiers individuels sur lesquels le routage peut être envisagé.</span><span class="sxs-lookup"><span data-stu-id="a7314-133">This method adds the ASP.NET Core router to the pipeline and it can be either configured here or in the individual files that it can consider routing to.</span></span>  <span data-ttu-id="a7314-134">Vous trouverez plus d’informations sur la configuration du routage dans la [section routage](pages-routing-layouts.md).</span><span class="sxs-lookup"><span data-stu-id="a7314-134">More information about routing configuration can be found in the [Routing section](pages-routing-layouts.md).</span></span>

<span data-ttu-id="a7314-135">La dernière instruction de cette méthode définit les points de terminaison sur lesquels ASP.NET Core écoute.</span><span class="sxs-lookup"><span data-stu-id="a7314-135">The final statement in this method defines the endpoints that ASP.NET Core is listening on.</span></span>  <span data-ttu-id="a7314-136">Ces itinéraires sont les emplacements accessibles sur le Web auxquels vous pouvez accéder sur le serveur Web et qui reçoivent du contenu géré par .NET et qui vous sont renvoyés.</span><span class="sxs-lookup"><span data-stu-id="a7314-136">These routes are the web accessible locations that you can access on the web server and receive some content handled by .NET and returned to you.</span></span>  <span data-ttu-id="a7314-137">La première entrée `MapBlazorHub` configure un concentrateur signalr à utiliser pour fournir la connexion permanente et en temps réel au serveur sur lequel l’État et le rendu des composants éblouissants sont gérés.</span><span class="sxs-lookup"><span data-stu-id="a7314-137">The first entry, `MapBlazorHub` configures a SignalR hub for use in providing the real-time and persistent connection to the server where the state and rendering of Blazor components is handled.</span></span>  <span data-ttu-id="a7314-138">L' `MapFallbackToPage` appel de méthode indique l’emplacement accessible via le Web de la page qui démarre l’application éblouissante et configure l’application pour gérer les demandes de liaison profonde du côté client.</span><span class="sxs-lookup"><span data-stu-id="a7314-138">The `MapFallbackToPage` method call indicates the web-accessible location of the page that starts the Blazor application and also configures the application to handle deep-linking requests from the client-side.</span></span>  <span data-ttu-id="a7314-139">Vous verrez cette fonctionnalité au travail si vous ouvrez un navigateur et accédez directement à l’itinéraire géré par éblouissant dans votre application, par exemple `/counter` dans le modèle de projet par défaut.</span><span class="sxs-lookup"><span data-stu-id="a7314-139">You will see this feature at work if you open a browser and navigate directly to Blazor handled route in your application, such as `/counter` in the default project template.</span></span> <span data-ttu-id="a7314-140">La requête est gérée par la page de secours *_Host. cshtml* , qui exécute ensuite le routeur éblouissant et affiche la page de compteur.</span><span class="sxs-lookup"><span data-stu-id="a7314-140">The request gets handled by the *_Host.cshtml* fallback page, which then runs the Blazor router and renders the counter page.</span></span>

## <a name="upgrading-the-bundleconfig-process"></a><span data-ttu-id="a7314-141">Mise à niveau du processus BundleConfig</span><span class="sxs-lookup"><span data-stu-id="a7314-141">Upgrading the BundleConfig Process</span></span>

<span data-ttu-id="a7314-142">Les technologies de regroupement des ressources, telles que les feuilles de style CSS et les fichiers JavaScript, ont considérablement évolué, avec d’autres technologies fournissant des outils et des techniques en constante évolution pour la gestion de ces ressources.</span><span class="sxs-lookup"><span data-stu-id="a7314-142">Technologies for bundling assets like CSS stylesheets and JavaScript files have evolved significantly, with other technologies providing quickly evolving tools and techniques for managing these resources.</span></span>  <span data-ttu-id="a7314-143">À cette fin, nous vous recommandons d’utiliser un outil de ligne de commande de nœud tel que grunt/Gulp/WebPack pour empaqueter vos ressources statiques.</span><span class="sxs-lookup"><span data-stu-id="a7314-143">To this end, we recommend using a Node command-line tool such as Grunt / Gulp / WebPack to package your static assets.</span></span>

<span data-ttu-id="a7314-144">Les outils en ligne de commande Grunt, Gulp et WebPack et leurs configurations associées peuvent être ajoutés à votre application et ASP.NET Core ignore ces fichiers pendant le processus de génération de l’application.</span><span class="sxs-lookup"><span data-stu-id="a7314-144">The Grunt, Gulp, and WebPack command-line tools and their associated configurations can be added to your application and ASP.NET Core will quietly ignore those files during the application build process.</span></span>  <span data-ttu-id="a7314-145">Vous pouvez ajouter un appel pour exécuter leurs tâches en ajoutant un à `Target` l’intérieur de votre fichier projet avec une syntaxe similaire à celle qui déclencherait un script Gulp et la `min` cible à l’intérieur de ce script.</span><span class="sxs-lookup"><span data-stu-id="a7314-145">You can add a call to run their tasks by adding a `Target` inside your project file with syntax similar to the following that would trigger a gulp script and the `min` target inside that script</span></span>

```xml
<Target Name="MyPreCompileTarget" BeforeTargets="Build">
  <Exec Command="gulp min" />
</Target>
```

<span data-ttu-id="a7314-146">Vous trouverez plus de détails sur les stratégies de gestion de vos fichiers CSS et JavaScript dans le [Bundle et les ressources statiques réduire dans ASP.net Core](/aspnet/core/client-side/bundling-and-minification) documentation.</span><span class="sxs-lookup"><span data-stu-id="a7314-146">More details about both strategies to manage your CSS and JavaScript files are available in the [Bundle and minify static assets in ASP.NET Core](/aspnet/core/client-side/bundling-and-minification) documentation.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="a7314-147">[Précédent](project-structure.md) 
> [Suivant](components.md)</span><span class="sxs-lookup"><span data-stu-id="a7314-147">[Previous](project-structure.md)
[Next](components.md)</span></span>
