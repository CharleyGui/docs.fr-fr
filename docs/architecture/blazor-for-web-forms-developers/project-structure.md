---
title: Structure de projet pour les Blazor applications
description: Découvrez comment les structures de projet de ASP.NET Web Forms et des Blazor projets sont comparées.
author: danroth27
ms.author: daroth
no-loc:
- Blazor
- WebAssembly
ms.date: 11/20/2020
ms.openlocfilehash: ba7113c88db728f30812821deaf7c06a80663d1f
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98189087"
---
# <a name="project-structure-for-no-locblazor-apps"></a><span data-ttu-id="8118a-103">Structure de projet pour les Blazor applications</span><span class="sxs-lookup"><span data-stu-id="8118a-103">Project structure for Blazor apps</span></span>

<span data-ttu-id="8118a-104">Malgré leurs différences de structure de projet, ASP.NET Web Forms et Blazor partagent un grand nombre de concepts similaires.</span><span class="sxs-lookup"><span data-stu-id="8118a-104">Despite their significant project structure differences, ASP.NET Web Forms and Blazor share many similar concepts.</span></span> <span data-ttu-id="8118a-105">Ici, nous allons examiner la structure d’un Blazor projet et le comparer à un projet de Web Forms ASP.net.</span><span class="sxs-lookup"><span data-stu-id="8118a-105">Here, we'll look at the structure of a Blazor project and compare it to an ASP.NET Web Forms project.</span></span>

<span data-ttu-id="8118a-106">Pour créer votre première Blazor application, suivez les instructions fournies dans les [ Blazor étapes de mise](/aspnet/core/blazor/get-started)en route.</span><span class="sxs-lookup"><span data-stu-id="8118a-106">To create your first Blazor app, follow the instructions in the [Blazor getting started steps](/aspnet/core/blazor/get-started).</span></span> <span data-ttu-id="8118a-107">Vous pouvez suivre les instructions pour créer une Blazor application serveur ou une Blazor WebAssembly application hébergée dans ASP.net core.</span><span class="sxs-lookup"><span data-stu-id="8118a-107">You can follow the instructions to create either a Blazor Server app or a Blazor WebAssembly app hosted in ASP.NET Core.</span></span> <span data-ttu-id="8118a-108">À l’exception de la logique spécifique au modèle d’hébergement, la majeure partie du code dans les deux projets est identique.</span><span class="sxs-lookup"><span data-stu-id="8118a-108">Except for the hosting model-specific logic, most of the code in both projects is the same.</span></span>

## <a name="project-file"></a><span data-ttu-id="8118a-109">Fichier projet</span><span class="sxs-lookup"><span data-stu-id="8118a-109">Project file</span></span>

<span data-ttu-id="8118a-110">Blazor Les applications serveur sont des projets .NET.</span><span class="sxs-lookup"><span data-stu-id="8118a-110">Blazor Server apps are .NET projects.</span></span> <span data-ttu-id="8118a-111">Le fichier projet pour l' Blazor application serveur est à la fois aussi simple que possible :</span><span class="sxs-lookup"><span data-stu-id="8118a-111">The project file for the Blazor Server app is about as simple as it can get:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>net5.0</TargetFramework>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="8118a-112">Le fichier projet pour une Blazor WebAssembly application semble un peu plus complexe (les numéros de version exacts peuvent varier) :</span><span class="sxs-lookup"><span data-stu-id="8118a-112">The project file for a Blazor WebAssembly app looks slightly more involved (exact version numbers may vary):</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.BlazorWebAssembly">

  <PropertyGroup>
    <TargetFramework>net5.0</TargetFramework>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="Microsoft.AspNetCore.Components.WebAssembly" Version="5.0.0" />
    <PackageReference Include="Microsoft.AspNetCore.Components.WebAssembly.DevServer" Version="5.0.0" PrivateAssets="all" />
    <PackageReference Include="System.Net.Http.Json" Version="5.0.0" />
  </ItemGroup>

</Project>
```

<span data-ttu-id="8118a-113">BlazorWebAssemblyProject targets `Microsoft.NET.Sdk.BlazorWebAssembly` au lieu du `Microsoft.NET.Sdk.Web` Kit de développement logiciel (SDK), car ils s’exécutent dans le navigateur sur un WebAssembly Runtime .net basé sur.</span><span class="sxs-lookup"><span data-stu-id="8118a-113">Blazor WebAssembly project targets `Microsoft.NET.Sdk.BlazorWebAssembly` instead of `Microsoft.NET.Sdk.Web` sdk because they run in the browser on a WebAssembly-based .NET runtime.</span></span> <span data-ttu-id="8118a-114">Vous ne pouvez pas installer .NET dans un navigateur Web comme vous le pouvez sur un serveur ou un ordinateur de développement.</span><span class="sxs-lookup"><span data-stu-id="8118a-114">You can't install .NET into a web browser like you can on a server or developer machine.</span></span> <span data-ttu-id="8118a-115">Par conséquent, le projet fait référence Blazor à l’infrastructure à l’aide de références de package individuelles.</span><span class="sxs-lookup"><span data-stu-id="8118a-115">Consequently, the project references the Blazor framework using individual package references.</span></span>

<span data-ttu-id="8118a-116">Par comparaison, un projet ASP.NET Web Forms par défaut comprend près de 300 lignes de code XML dans son fichier *. csproj* , dont la plupart répertorient explicitement les différents fichiers de code et de contenu du projet.</span><span class="sxs-lookup"><span data-stu-id="8118a-116">By comparison, a default ASP.NET Web Forms project includes almost 300 lines of XML in its *.csproj* file, most of which is explicitly listing the various code and content files in the project.</span></span> <span data-ttu-id="8118a-117">Avec la version de `.NET 5` `Blazor Server` et l' `Blazor WebAssembly` application, vous pouvez facilement partager un seul Runtime unifié.</span><span class="sxs-lookup"><span data-stu-id="8118a-117">With the release of `.NET 5` both `Blazor Server` and `Blazor WebAssembly` app can easily share one unified runtime.</span></span>

<span data-ttu-id="8118a-118">Bien qu’elles soient prises en charge, les références d’assembly individuelles sont moins fréquentes dans les projets .NET.</span><span class="sxs-lookup"><span data-stu-id="8118a-118">Although they're supported, individual assembly references are less common in .NET projects.</span></span> <span data-ttu-id="8118a-119">La plupart des dépendances de projet sont gérées en tant que références de package NuGet.</span><span class="sxs-lookup"><span data-stu-id="8118a-119">Most project dependencies are handled as NuGet package references.</span></span> <span data-ttu-id="8118a-120">Il vous suffit de référencer les dépendances de package de niveau supérieur dans les projets .NET.</span><span class="sxs-lookup"><span data-stu-id="8118a-120">You only need to reference top-level package dependencies in .NET projects.</span></span> <span data-ttu-id="8118a-121">Les dépendances transitives sont incluses automatiquement.</span><span class="sxs-lookup"><span data-stu-id="8118a-121">Transitive dependencies are included automatically.</span></span> <span data-ttu-id="8118a-122">Au lieu d’utiliser le fichier *packages.config* couramment trouvé dans les projets ASP.NET Web Forms pour référencer des packages, des références de package sont ajoutées au fichier projet à l’aide de l' `<PackageReference>` élément.</span><span class="sxs-lookup"><span data-stu-id="8118a-122">Instead of using the *packages.config* file commonly found in ASP.NET Web Forms projects to reference packages, package references are added to the project file using the `<PackageReference>` element.</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="12.0.2" />
</ItemGroup>
```

## <a name="entry-point"></a><span data-ttu-id="8118a-123">Point d’entrée</span><span class="sxs-lookup"><span data-stu-id="8118a-123">Entry point</span></span>

<span data-ttu-id="8118a-124">Le Blazor point d’entrée de l’application serveur est défini dans le fichier *Program.cs* , comme vous pouvez le voir dans une application console.</span><span class="sxs-lookup"><span data-stu-id="8118a-124">The Blazor Server app's entry point is defined in the *Program.cs* file, as you would see in a Console app.</span></span> <span data-ttu-id="8118a-125">Lorsque l’application s’exécute, elle crée et exécute une instance d’hôte Web à l’aide des valeurs par défaut spécifiques aux applications Web.</span><span class="sxs-lookup"><span data-stu-id="8118a-125">When the app executes, it creates and runs a web host instance using defaults specific to web apps.</span></span> <span data-ttu-id="8118a-126">L’hôte Web gère le Blazor cycle de vie de l’application serveur et configure les services de niveau hôte.</span><span class="sxs-lookup"><span data-stu-id="8118a-126">The web host manages the Blazor Server app's lifecycle and sets up host-level services.</span></span> <span data-ttu-id="8118a-127">La configuration, la journalisation, l’injection de dépendances et le serveur HTTP sont des exemples de ces services.</span><span class="sxs-lookup"><span data-stu-id="8118a-127">Examples of such services are configuration, logging, dependency injection, and the HTTP server.</span></span> <span data-ttu-id="8118a-128">Ce code est principalement réutilisable et reste souvent inchangé.</span><span class="sxs-lookup"><span data-stu-id="8118a-128">This code is mostly boilerplate and is often left unchanged.</span></span>

```csharp
public class Program
{
    public static void Main(string[] args)
    {
        CreateHostBuilder(args).Build().Run();
    }

    public static IHostBuilder CreateHostBuilder(string[] args) =>
        Host.CreateDefaultBuilder(args)
            .ConfigureWebHostDefaults(webBuilder =>
            {
                webBuilder.UseStartup<Startup>();
            });
}
```

<span data-ttu-id="8118a-129">Blazorles WebAssembly applications définissent également un point d’entrée dans *Program.cs*.</span><span class="sxs-lookup"><span data-stu-id="8118a-129">Blazor WebAssembly apps also define an entry point in *Program.cs*.</span></span> <span data-ttu-id="8118a-130">Le code semble légèrement différent.</span><span class="sxs-lookup"><span data-stu-id="8118a-130">The code looks slightly different.</span></span> <span data-ttu-id="8118a-131">Le code est similaire en ce qu’il configure l’hôte d’application pour fournir les mêmes services de niveau hôte à l’application.</span><span class="sxs-lookup"><span data-stu-id="8118a-131">The code is similar in that it's setting up the app host to provide the same host-level services to the app.</span></span> <span data-ttu-id="8118a-132">WebAssemblyToutefois, l’hôte d’application ne configure pas un serveur http, car il s’exécute directement dans le navigateur.</span><span class="sxs-lookup"><span data-stu-id="8118a-132">The WebAssembly app host doesn't, however, set up an HTTP server because it executes directly in the browser.</span></span>

<span data-ttu-id="8118a-133">Blazor les applications ont une `Startup` classe au lieu d’un fichier *global. asax* pour définir la logique de démarrage de l’application.</span><span class="sxs-lookup"><span data-stu-id="8118a-133">Blazor apps have a `Startup` class instead of a *Global.asax* file to define the startup logic for the app.</span></span> <span data-ttu-id="8118a-134">La `Startup` classe est utilisée pour configurer l’application et tous les services spécifiques à l’application.</span><span class="sxs-lookup"><span data-stu-id="8118a-134">The `Startup` class is used to configure the app and any app-specific services.</span></span> <span data-ttu-id="8118a-135">Dans l' Blazor application serveur, la `Startup` classe est utilisée pour configurer le point de terminaison de la connexion en temps réel utilisée par Blazor entre les navigateurs clients et le serveur.</span><span class="sxs-lookup"><span data-stu-id="8118a-135">In the Blazor Server app, the `Startup` class is used to set up the endpoint for the real-time connection used by Blazor between the client browsers and the server.</span></span> <span data-ttu-id="8118a-136">Dans l' Blazor WebAssembly application, la `Startup` classe définit les composants racine pour l’application et l’emplacement où elles doivent être rendues.</span><span class="sxs-lookup"><span data-stu-id="8118a-136">In the Blazor WebAssembly app, the `Startup` class defines the root components for the app and where they should be rendered.</span></span> <span data-ttu-id="8118a-137">Nous examinerons plus en détail la `Startup` classe dans la section démarrage de l' [application](./app-startup.md) .</span><span class="sxs-lookup"><span data-stu-id="8118a-137">We'll take a deeper look at the `Startup` class in the [App startup](./app-startup.md) section.</span></span>

## <a name="static-files"></a><span data-ttu-id="8118a-138">Fichiers statiques</span><span class="sxs-lookup"><span data-stu-id="8118a-138">Static files</span></span>

<span data-ttu-id="8118a-139">Contrairement aux projets ASP.NET Web Forms, tous les fichiers d’un Blazor projet ne peuvent pas être demandés en tant que fichiers statiques.</span><span class="sxs-lookup"><span data-stu-id="8118a-139">Unlike ASP.NET Web Forms projects, not all files in a Blazor project can be requested as static files.</span></span> <span data-ttu-id="8118a-140">Seuls les fichiers du dossier *wwwroot* sont adressables par le Web.</span><span class="sxs-lookup"><span data-stu-id="8118a-140">Only the files in the *wwwroot* folder are web-addressable.</span></span> <span data-ttu-id="8118a-141">Ce dossier est appelé « racine Web » de l’application.</span><span class="sxs-lookup"><span data-stu-id="8118a-141">This folder is referred to the app's "web root".</span></span> <span data-ttu-id="8118a-142">Tout ce qui se trouve en dehors de la racine Web de l’application *n’est pas* adressable par le Web.</span><span class="sxs-lookup"><span data-stu-id="8118a-142">Anything outside of the app's web root *isn't* web-addressable.</span></span> <span data-ttu-id="8118a-143">Ce programme d’installation fournit un niveau supplémentaire de sécurité qui empêche l’exposition accidentelle de fichiers projet sur le Web.</span><span class="sxs-lookup"><span data-stu-id="8118a-143">This setup provides an additional level of security that prevents accidental exposing of project files over the web.</span></span>

## <a name="configuration"></a><span data-ttu-id="8118a-144">Configuration</span><span class="sxs-lookup"><span data-stu-id="8118a-144">Configuration</span></span>

<span data-ttu-id="8118a-145">La configuration dans ASP.NET Web Forms Apps est généralement gérée à l’aide d’un ou plusieurs fichiers *web.config* .</span><span class="sxs-lookup"><span data-stu-id="8118a-145">Configuration in ASP.NET Web Forms apps is typically handled using one or more *web.config* files.</span></span> <span data-ttu-id="8118a-146">Blazor les applications n’ont généralement pas de fichiers *web.config* .</span><span class="sxs-lookup"><span data-stu-id="8118a-146">Blazor apps don't typically have *web.config* files.</span></span> <span data-ttu-id="8118a-147">Dans ce cas, le fichier est utilisé uniquement pour configurer les paramètres spécifiques à IIS lorsqu’ils sont hébergés sur IIS.</span><span class="sxs-lookup"><span data-stu-id="8118a-147">If they do, the file is only used to configure IIS-specific settings when hosted on IIS.</span></span> <span data-ttu-id="8118a-148">Au lieu de cela, Blazor les applications serveur utilisent le ASP.net Core abstractions de la configuration (les Blazor WebAssembly applications ne prennent pas en charge les mêmes abstractions de configuration, mais il peut s’agir d’une fonctionnalité ajoutée à l’avenir).</span><span class="sxs-lookup"><span data-stu-id="8118a-148">Instead, Blazor Server apps use the ASP.NET Core configuration abstractions (Blazor WebAssembly apps don't currently support the same configuration abstractions, but that may be a feature added in the future).</span></span> <span data-ttu-id="8118a-149">Par exemple, l' Blazor application serveur par défaut stocke certains paramètres dans *appsettings.jssur*.</span><span class="sxs-lookup"><span data-stu-id="8118a-149">For example, the default Blazor Server app stores some settings in *appsettings.json*.</span></span>

```json
{
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft": "Warning",
      "Microsoft.Hosting.Lifetime": "Information"
    }
  },
  "AllowedHosts": "*"
}
```

<span data-ttu-id="8118a-150">Pour plus d’informations sur la configuration dans ASP.NET Core projets, consultez la section [configuration](./config.md) .</span><span class="sxs-lookup"><span data-stu-id="8118a-150">We'll learn more about configuration in ASP.NET Core projects in the [Configuration](./config.md) section.</span></span>

## <a name="razor-components"></a><span data-ttu-id="8118a-151">Composants Razor</span><span class="sxs-lookup"><span data-stu-id="8118a-151">Razor components</span></span>

<span data-ttu-id="8118a-152">La plupart des fichiers dans Blazor les projets sont des fichiers *. Razor* .</span><span class="sxs-lookup"><span data-stu-id="8118a-152">Most files in Blazor projects are *.razor* files.</span></span> <span data-ttu-id="8118a-153">Razor est un langage de création de modèles basé sur HTML et C# qui est utilisé pour générer dynamiquement l’interface utilisateur Web.</span><span class="sxs-lookup"><span data-stu-id="8118a-153">Razor is a templating language based on HTML and C# that is used to dynamically generate web UI.</span></span> <span data-ttu-id="8118a-154">Les fichiers *. Razor* définissent les composants qui composent l’interface utilisateur de l’application.</span><span class="sxs-lookup"><span data-stu-id="8118a-154">The *.razor* files define components that make up the UI of the app.</span></span> <span data-ttu-id="8118a-155">Pour l’essentiel, les composants sont identiques pour le Blazor serveur et les Blazor WebAssembly applications.</span><span class="sxs-lookup"><span data-stu-id="8118a-155">For the most part, the components are identical for both the Blazor Server and Blazor WebAssembly apps.</span></span> <span data-ttu-id="8118a-156">Les composants de Blazor sont analogues aux contrôles utilisateur dans ASP.NET Web Forms.</span><span class="sxs-lookup"><span data-stu-id="8118a-156">Components in Blazor are analogous to user controls in ASP.NET Web Forms.</span></span>

<span data-ttu-id="8118a-157">Chaque fichier de composant Razor est compilé dans une classe .NET lorsque le projet est généré.</span><span class="sxs-lookup"><span data-stu-id="8118a-157">Each Razor component file is compiled into a .NET class when the project is built.</span></span> <span data-ttu-id="8118a-158">La classe générée capture l’état du composant, la logique de rendu, les méthodes de cycle de vie, les gestionnaires d’événements et d’autres logiques.</span><span class="sxs-lookup"><span data-stu-id="8118a-158">The generated class captures the component's state, rendering logic, lifecycle methods, event handlers, and other logic.</span></span> <span data-ttu-id="8118a-159">Nous allons examiner les composants de création de composants de l' [interface utilisateur réutilisables avec Blazor ](./components.md) la section.</span><span class="sxs-lookup"><span data-stu-id="8118a-159">We'll look at authoring components in the [Building reusable UI components with Blazor](./components.md) section.</span></span>

<span data-ttu-id="8118a-160">Les fichiers *_Imports. Razor* ne sont pas des fichiers de composants Razor.</span><span class="sxs-lookup"><span data-stu-id="8118a-160">The *_Imports.razor* files aren't Razor component files.</span></span> <span data-ttu-id="8118a-161">Au lieu de cela, ils définissent un ensemble de directives Razor à importer dans d’autres fichiers *. Razor* dans le même dossier et dans ses sous-dossiers.</span><span class="sxs-lookup"><span data-stu-id="8118a-161">Instead, they define a set of Razor directives to import into other *.razor* files within the same folder and in its subfolders.</span></span> <span data-ttu-id="8118a-162">Par exemple, un fichier *_Imports. Razor* est un moyen conventionnel d’ajouter `using` des directives pour les espaces de noms couramment utilisés :</span><span class="sxs-lookup"><span data-stu-id="8118a-162">For example, a *_Imports.razor* file is a conventional way to add `using` directives for commonly used namespaces:</span></span>

```razor
@using System.Net.Http
@using Microsoft.AspNetCore.Authorization
@using Microsoft.AspNetCore.Components.Authorization
@using Microsoft.AspNetCore.Components.Forms
@using Microsoft.AspNetCore.Components.Routing
@using Microsoft.AspNetCore.Components.Web
@using Microsoft.JSInterop
@using BlazorApp1
@using BlazorApp1.Shared
```

## <a name="pages"></a><span data-ttu-id="8118a-163">Pages</span><span class="sxs-lookup"><span data-stu-id="8118a-163">Pages</span></span>

<span data-ttu-id="8118a-164">Où se trouvent les pages dans les Blazor applications ?</span><span class="sxs-lookup"><span data-stu-id="8118a-164">Where are the pages in the Blazor apps?</span></span> <span data-ttu-id="8118a-165">Blazor ne définit pas d’extension de fichier distincte pour les pages adressables, comme les fichiers *. aspx* dans ASP.NET Web Forms apps.</span><span class="sxs-lookup"><span data-stu-id="8118a-165">Blazor doesn't define a separate file extension for addressable pages, like the *.aspx* files in ASP.NET Web Forms apps.</span></span> <span data-ttu-id="8118a-166">Au lieu de cela, les pages sont définies en affectant des itinéraires aux composants.</span><span class="sxs-lookup"><span data-stu-id="8118a-166">Instead, pages are defined by assigning routes to components.</span></span> <span data-ttu-id="8118a-167">Un itinéraire est généralement affecté à l’aide de la `@page` directive Razor.</span><span class="sxs-lookup"><span data-stu-id="8118a-167">A route is typically assigned using the `@page` Razor directive.</span></span> <span data-ttu-id="8118a-168">Par exemple, le `Counter` composant créé dans le fichier *pages/Counter. Razor* définit l’itinéraire suivant :</span><span class="sxs-lookup"><span data-stu-id="8118a-168">For example, the `Counter` component authored in the *Pages/Counter.razor* file defines the following route:</span></span>

```razor
@page "/counter"
```

<span data-ttu-id="8118a-169">Le routage dans Blazor est géré côté client et non sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="8118a-169">Routing in Blazor is handled client-side, not on the server.</span></span> <span data-ttu-id="8118a-170">Lorsque l’utilisateur navigue dans le navigateur, Blazor intercepte la navigation, puis restitue le composant avec l’itinéraire correspondant.</span><span class="sxs-lookup"><span data-stu-id="8118a-170">As the user navigates in the browser, Blazor intercepts the navigation and then renders the component with the matching route.</span></span>

<span data-ttu-id="8118a-171">Les itinéraires des composants ne sont pas actuellement déduits par l’emplacement des fichiers du composant, comme par exemple avec les pages *. aspx* .</span><span class="sxs-lookup"><span data-stu-id="8118a-171">The component routes aren't currently inferred by the component's file location like they are with *.aspx* pages.</span></span> <span data-ttu-id="8118a-172">Cette fonctionnalité peut être ajoutée à l’avenir.</span><span class="sxs-lookup"><span data-stu-id="8118a-172">This feature may be added in the future.</span></span> <span data-ttu-id="8118a-173">Chaque itinéraire doit être spécifié explicitement sur le composant.</span><span class="sxs-lookup"><span data-stu-id="8118a-173">Each route must be specified explicitly on the component.</span></span> <span data-ttu-id="8118a-174">Le stockage de composants routables dans un dossier *pages* n’a aucune signification particulière et constitue purement une convention.</span><span class="sxs-lookup"><span data-stu-id="8118a-174">Storing routable components in a *Pages* folder has no special meaning and is purely a convention.</span></span>

<span data-ttu-id="8118a-175">Nous examinerons plus en détail le routage dans Blazor dans la section [pages, routage et dispositions](./pages-routing-layouts.md) .</span><span class="sxs-lookup"><span data-stu-id="8118a-175">We'll look in greater detail at routing in Blazor in the [Pages, routing, and layouts](./pages-routing-layouts.md) section.</span></span>

## <a name="layout"></a><span data-ttu-id="8118a-176">Layout</span><span class="sxs-lookup"><span data-stu-id="8118a-176">Layout</span></span>

<span data-ttu-id="8118a-177">Dans ASP.NET Web Forms Apps, une mise en page courante est gérée à l’aide de pages maîtres (*site. Master*).</span><span class="sxs-lookup"><span data-stu-id="8118a-177">In ASP.NET Web Forms apps, a common page layout is handled using master pages (*Site.Master*).</span></span> <span data-ttu-id="8118a-178">Dans Blazor les applications, la mise en page est gérée à l’aide de composants de disposition (*Shared/MainLayout. Razor*).</span><span class="sxs-lookup"><span data-stu-id="8118a-178">In Blazor apps, the page layout is handled using layout components (*Shared/MainLayout.razor*).</span></span> <span data-ttu-id="8118a-179">Les composants de disposition seront abordés plus en détail dans la section [page, routage et dispositions](./pages-routing-layouts.md) .</span><span class="sxs-lookup"><span data-stu-id="8118a-179">Layout components will be discussed in more detail in [Page, routing, and layouts](./pages-routing-layouts.md) section.</span></span>

## <a name="bootstrap-no-locblazor"></a><span data-ttu-id="8118a-180">Démarrage Blazor</span><span class="sxs-lookup"><span data-stu-id="8118a-180">Bootstrap Blazor</span></span>

<span data-ttu-id="8118a-181">Pour Blazor le démarrage, l’application doit :</span><span class="sxs-lookup"><span data-stu-id="8118a-181">To bootstrap Blazor, the app must:</span></span>

- <span data-ttu-id="8118a-182">Spécifiez l’emplacement de la page où le composant racine (*app. Razor*) doit être rendu.</span><span class="sxs-lookup"><span data-stu-id="8118a-182">Specify where on the page the root component (*App.Razor*) should be rendered.</span></span>
- <span data-ttu-id="8118a-183">Ajoutez le Blazor script d’infrastructure correspondant.</span><span class="sxs-lookup"><span data-stu-id="8118a-183">Add the corresponding Blazor framework script.</span></span>

<span data-ttu-id="8118a-184">Dans l' Blazor application serveur, la page hôte du composant racine est définie dans le fichier *_Host. cshtml* .</span><span class="sxs-lookup"><span data-stu-id="8118a-184">In the Blazor Server app, the root component's host page is defined in the *_Host.cshtml* file.</span></span> <span data-ttu-id="8118a-185">Ce fichier définit une page Razor, et non un composant.</span><span class="sxs-lookup"><span data-stu-id="8118a-185">This file defines a Razor Page, not a component.</span></span> <span data-ttu-id="8118a-186">Razor Pages utiliser syntaxe Razor pour définir une page adressable par le serveur, à l’instar d’une page *. aspx* .</span><span class="sxs-lookup"><span data-stu-id="8118a-186">Razor Pages use Razor syntax to define a server-addressable page, very much like an *.aspx* page.</span></span> <span data-ttu-id="8118a-187">La `Html.RenderComponentAsync<TComponent>(RenderMode)` méthode est utilisée pour définir l’emplacement où un composant de niveau racine doit être restitué.</span><span class="sxs-lookup"><span data-stu-id="8118a-187">The `Html.RenderComponentAsync<TComponent>(RenderMode)` method is used to define where a root-level component should be rendered.</span></span> <span data-ttu-id="8118a-188">L' `RenderMode` option indique la manière dont le composant doit être rendu.</span><span class="sxs-lookup"><span data-stu-id="8118a-188">The `RenderMode` option indicates the manner in which the component should be rendered.</span></span> <span data-ttu-id="8118a-189">Le tableau suivant présente les options prises en charge `RenderMode` .</span><span class="sxs-lookup"><span data-stu-id="8118a-189">The following table outlines the supported `RenderMode` options.</span></span>

|<span data-ttu-id="8118a-190">Option</span><span class="sxs-lookup"><span data-stu-id="8118a-190">Option</span></span>                        |<span data-ttu-id="8118a-191">Description</span><span class="sxs-lookup"><span data-stu-id="8118a-191">Description</span></span>       |
|------------------------------|------------------|
|`RenderMode.Server`           |<span data-ttu-id="8118a-192">Rendu interactif une fois qu’une connexion avec le navigateur est établie</span><span class="sxs-lookup"><span data-stu-id="8118a-192">Rendered interactively once a connection with the browser is established</span></span>|
|`RenderMode.ServerPrerendered`|<span data-ttu-id="8118a-193">Premier prérendu puis rendu interactif</span><span class="sxs-lookup"><span data-stu-id="8118a-193">First prerendered and then rendered interactively</span></span>|
|`RenderMode.Static`           |<span data-ttu-id="8118a-194">Rendu en tant que contenu statique</span><span class="sxs-lookup"><span data-stu-id="8118a-194">Rendered as static content</span></span>|

<span data-ttu-id="8118a-195">La référence de script à *_framework/blazor.server.js* établit la connexion en temps réel avec le serveur, puis traite toutes les interactions utilisateur et les mises à jour de l’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="8118a-195">The script reference to *_framework/blazor.server.js* establishes the real-time connection with the server and then deals with all user interactions and UI updates.</span></span>

```razor
@page "/"
@namespace BlazorApp1.Pages
@addTagHelper *, Microsoft.AspNetCore.Mvc.TagHelpers

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>BlazorApp1</title>
    <base href="~/" />
    <link rel="stylesheet" href="css/bootstrap/bootstrap.min.css" />
    <link href="css/site.css" rel="stylesheet" />
</head>
<body>
    <app>
        @(await Html.RenderComponentAsync<App>(RenderMode.ServerPrerendered))
    </app>

    <script src="_framework/blazor.server.js"></script>
</body>
</html>
```

<span data-ttu-id="8118a-196">Dans l' Blazor WebAssembly application, la page hôte est un simple fichier HTML statique sous *wwwroot/index.html*.</span><span class="sxs-lookup"><span data-stu-id="8118a-196">In the Blazor WebAssembly app, the host page is a simple static HTML file under *wwwroot/index.html*.</span></span> <span data-ttu-id="8118a-197">L' `<div>` élément avec l’ID nommé `app` est utilisé pour indiquer l’emplacement où le composant racine doit être restitué.</span><span class="sxs-lookup"><span data-stu-id="8118a-197">The `<div>` element with id named `app` is used to indicate where the root component should be rendered.</span></span>

```html
<!DOCTYPE html>
<html>

<head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no" />
    <title>BlazorApp2</title>
    <base href="/" />
    <link href="css/bootstrap/bootstrap.min.css" rel="stylesheet" />
    <link href="css/app.css" rel="stylesheet" />
    <link href="blazor-web.styles.css" rel="stylesheet" />
</head>

<body>
    <div id="app">Loading...</div>

    <div id="blazor-error-ui">
        An unhandled error has occurred.
        <a href="" class="reload">Reload</a>
        <a class="dismiss">🗙</a>
    </div>
    <script src="_framework/blazor.webassembly.js"></script>
</body>

</html>

```

<span data-ttu-id="8118a-198">Le composant racine à restituer est spécifié dans la méthode de l’application, `Program.Main` avec la flexibilité nécessaire pour inscrire les services via l’injection de dépendances.</span><span class="sxs-lookup"><span data-stu-id="8118a-198">The root component to render is specified in the app's `Program.Main` method with the flexibility to register services through dependency injection.</span></span> <span data-ttu-id="8118a-199">Pour plus d’informations, consultez [ASP.net Core Blazor injection de dépendances](/aspnet/core/blazor/fundamentals/dependency-injection?pivots=webassembly).</span><span class="sxs-lookup"><span data-stu-id="8118a-199">For more information, see [ASP.NET Core Blazor dependency injection](/aspnet/core/blazor/fundamentals/dependency-injection?pivots=webassembly).</span></span>

```csharp
public class Program
{
    public static async Task Main(string[] args)
    {
        var builder = WebAssemblyHostBuilder.CreateDefault(args);
        builder.RootComponents.Add<App>("#app");

        ....
        ....
    }
}
```

## <a name="build-output"></a><span data-ttu-id="8118a-200">Sortie de la génération</span><span class="sxs-lookup"><span data-stu-id="8118a-200">Build output</span></span>

<span data-ttu-id="8118a-201">Lorsqu’un Blazor projet est généré, tous les fichiers de code et de composant Razor sont compilés dans un assembly unique.</span><span class="sxs-lookup"><span data-stu-id="8118a-201">When a Blazor project is built, all Razor component and code files are compiled into a single assembly.</span></span> <span data-ttu-id="8118a-202">Contrairement aux projets ASP.NET Web Forms, Blazor ne prend pas en charge la compilation du runtime de la logique d’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="8118a-202">Unlike ASP.NET Web Forms projects, Blazor doesn't support runtime compilation of the UI logic.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="8118a-203">Exécuter l’application</span><span class="sxs-lookup"><span data-stu-id="8118a-203">Run the app</span></span>

<span data-ttu-id="8118a-204">Pour exécuter l' Blazor application serveur, appuyez sur `F5` dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8118a-204">To run the Blazor Server app, press `F5` in Visual Studio.</span></span> <span data-ttu-id="8118a-205">Blazor les applications ne prennent pas en charge la compilation du Runtime.</span><span class="sxs-lookup"><span data-stu-id="8118a-205">Blazor apps don't support runtime compilation.</span></span> <span data-ttu-id="8118a-206">Pour afficher les résultats des modifications du balisage du code et des composants, régénérez et redémarrez l’application avec le débogueur attaché.</span><span class="sxs-lookup"><span data-stu-id="8118a-206">To see the results of code and component markup changes, rebuild and restart the app with the debugger attached.</span></span> <span data-ttu-id="8118a-207">Si vous exécutez sans le débogueur attaché ( `Ctrl+F5` ), Visual Studio surveille les modifications apportées aux fichiers et redémarre l’application à mesure que des modifications sont apportées.</span><span class="sxs-lookup"><span data-stu-id="8118a-207">If you run without the debugger attached (`Ctrl+F5`), Visual Studio watches for file changes and restarts the app as changes are made.</span></span> <span data-ttu-id="8118a-208">Vous actualisez manuellement le navigateur à mesure que des modifications sont apportées.</span><span class="sxs-lookup"><span data-stu-id="8118a-208">You manually refresh the browser as changes are made.</span></span>

<span data-ttu-id="8118a-209">Pour exécuter l' Blazor WebAssembly application, choisissez l’une des approches suivantes :</span><span class="sxs-lookup"><span data-stu-id="8118a-209">To run the Blazor WebAssembly app, choose one of the following approaches:</span></span>

- <span data-ttu-id="8118a-210">Exécutez le projet client directement à l’aide du serveur de développement.</span><span class="sxs-lookup"><span data-stu-id="8118a-210">Run the client project directly using the development server.</span></span>
- <span data-ttu-id="8118a-211">Exécutez le projet serveur lors de l’hébergement de l’application avec ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="8118a-211">Run the server project when hosting the app with ASP.NET Core.</span></span>

<span data-ttu-id="8118a-212">BlazorWebAssemblyles applications peuvent être déboguées dans le navigateur et dans Visual Studio. pour plus d’informations, consultez [ASP.net Core Blazor WebAssembly de débogage](/aspnet/core/blazor/debug) .</span><span class="sxs-lookup"><span data-stu-id="8118a-212">Blazor WebAssembly apps can be debugged in both browser and Visual Studio.See [Debug ASP.NET Core Blazor WebAssembly](/aspnet/core/blazor/debug) for details.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="8118a-213">[Précédent](hosting-models.md) 
> [Suivant](app-startup.md)</span><span class="sxs-lookup"><span data-stu-id="8118a-213">[Previous](hosting-models.md)
[Next](app-startup.md)</span></span>
