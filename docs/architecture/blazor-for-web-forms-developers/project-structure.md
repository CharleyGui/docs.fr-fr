---
title: Structure de projet pour les Blazor applications
description: Découvrez comment les structures de projet de ASP.NET Web Forms et des Blazor projets sont comparées.
author: danroth27
ms.author: daroth
no-loc:
- Blazor
- WebAssembly
ms.date: 09/11/2019
ms.openlocfilehash: 473b708a9b58fa88844bc6f79a898943d5a7db71
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86173040"
---
# <a name="project-structure-for-blazor-apps"></a><span data-ttu-id="5f62e-103">Structure de projet pour les Blazor applications</span><span class="sxs-lookup"><span data-stu-id="5f62e-103">Project structure for Blazor apps</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="5f62e-104">Malgré leurs différences de structure de projet, ASP.NET Web Forms et Blazor partagent un grand nombre de concepts similaires.</span><span class="sxs-lookup"><span data-stu-id="5f62e-104">Despite their significant project structure differences, ASP.NET Web Forms and Blazor share many similar concepts.</span></span> <span data-ttu-id="5f62e-105">Ici, nous allons examiner la structure d’un Blazor projet et le comparer à un projet de Web Forms ASP.net.</span><span class="sxs-lookup"><span data-stu-id="5f62e-105">Here, we'll look at the structure of a Blazor project and compare it to an ASP.NET Web Forms project.</span></span>

<span data-ttu-id="5f62e-106">Pour créer votre première Blazor application, suivez les instructions fournies dans les [ Blazor étapes de mise](/aspnet/core/blazor/get-started)en route.</span><span class="sxs-lookup"><span data-stu-id="5f62e-106">To create your first Blazor app, follow the instructions in the [Blazor getting started steps](/aspnet/core/blazor/get-started).</span></span> <span data-ttu-id="5f62e-107">Vous pouvez suivre les instructions pour créer une Blazor application serveur ou une Blazor WebAssembly application hébergée dans ASP.net core.</span><span class="sxs-lookup"><span data-stu-id="5f62e-107">You can follow the instructions to create either a Blazor Server app or a Blazor WebAssembly app hosted in ASP.NET Core.</span></span> <span data-ttu-id="5f62e-108">À l’exception de la logique spécifique au modèle d’hébergement, la majeure partie du code dans les deux projets est identique.</span><span class="sxs-lookup"><span data-stu-id="5f62e-108">Except for the hosting model-specific logic, most of the code in both projects is the same.</span></span>

## <a name="project-file"></a><span data-ttu-id="5f62e-109">Fichier projet</span><span class="sxs-lookup"><span data-stu-id="5f62e-109">Project file</span></span>

Blazor<span data-ttu-id="5f62e-110">Les applications serveur sont des projets .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5f62e-110"> Server apps are .NET Core projects.</span></span> <span data-ttu-id="5f62e-111">Le fichier projet pour l' Blazor application serveur est à la fois aussi simple que possible :</span><span class="sxs-lookup"><span data-stu-id="5f62e-111">The project file for the Blazor Server app is about as simple as it can get:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>netcoreapp3.0</TargetFramework>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="5f62e-112">Le fichier projet pour une Blazor WebAssembly application semble un peu plus complexe (les numéros de version exacts peuvent varier) :</span><span class="sxs-lookup"><span data-stu-id="5f62e-112">The project file for a Blazor WebAssembly app looks slightly more involved (exact version numbers may vary):</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>netstandard2.0</TargetFramework>
    <RazorLangVersion>3.0</RazorLangVersion>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="Microsoft.AspNetCore.Blazor" Version="3.1.0" />
    <PackageReference Include="Microsoft.AspNetCore.Blazor.Build" Version="3.1.0" PrivateAssets="all" />
    <PackageReference Include="Microsoft.AspNetCore.Blazor.HttpClient" Version="3.1.0" />
    <PackageReference Include="Microsoft.AspNetCore.Blazor.DevServer" Version="3.1.0" PrivateAssets="all" />
  </ItemGroup>

  <ItemGroup>
    <ProjectReference Include="..\Shared\BlazorWebAssemblyApp1.Shared.csproj" />
  </ItemGroup>

</Project>
```

Blazor<span data-ttu-id="5f62e-113">WebAssemblyles projets ciblent .NET standard au lieu de .net Core, car ils s’exécutent dans le navigateur sur un WebAssembly Runtime .net basé sur.</span><span class="sxs-lookup"><span data-stu-id="5f62e-113"> WebAssembly projects target .NET Standard instead of .NET Core because they run in the browser on a WebAssembly-based .NET runtime.</span></span> <span data-ttu-id="5f62e-114">Vous ne pouvez pas installer .NET dans un navigateur Web comme vous le pouvez sur un serveur ou un ordinateur de développement.</span><span class="sxs-lookup"><span data-stu-id="5f62e-114">You can't install .NET into a web browser like you can on a server or developer machine.</span></span> <span data-ttu-id="5f62e-115">Par conséquent, le projet fait référence Blazor à l’infrastructure à l’aide de références de package individuelles.</span><span class="sxs-lookup"><span data-stu-id="5f62e-115">Consequently, the project references the Blazor framework using individual package references.</span></span>

<span data-ttu-id="5f62e-116">Par comparaison, un projet ASP.NET Web Forms par défaut comprend près de 300 lignes de code XML dans son fichier *. csproj* , dont la plupart répertorient explicitement les différents fichiers de code et de contenu du projet.</span><span class="sxs-lookup"><span data-stu-id="5f62e-116">By comparison, a default ASP.NET Web Forms project includes almost 300 lines of XML in its *.csproj* file, most of which is explicitly listing the various code and content files in the project.</span></span> <span data-ttu-id="5f62e-117">Un grand nombre des simplifications dans les projets .NET Core et .NET Standard proviennent des cibles et des propriétés par défaut importées en référençant le `Microsoft.NET.Sdk.Web` Kit de développement logiciel (SDK), souvent appelé simplement Kit de développement logiciel (SDK) Web.</span><span class="sxs-lookup"><span data-stu-id="5f62e-117">Many of the simplifications in the .NET Core- and .NET Standard-based projects come from the default targets and properties imported by referencing the `Microsoft.NET.Sdk.Web` SDK, often referred to as simply the Web SDK.</span></span> <span data-ttu-id="5f62e-118">Le kit de développement logiciel (SDK) Web comprend des caractères génériques et d’autres pratiques qui simplifient l’inclusion de code et de fichiers de contenu dans le projet.</span><span class="sxs-lookup"><span data-stu-id="5f62e-118">The Web SDK includes wildcards and other conveniences that simplify inclusion of code and content files in the project.</span></span> <span data-ttu-id="5f62e-119">Vous n’avez pas besoin de répertorier les fichiers explicitement.</span><span class="sxs-lookup"><span data-stu-id="5f62e-119">You don't need to list the files explicitly.</span></span> <span data-ttu-id="5f62e-120">Quand vous ciblez .NET Core, le kit de développement logiciel (SDK) Web ajoute également des références d’infrastructure aux frameworks partagés .NET Core et ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="5f62e-120">When targeting .NET Core, the Web SDK also adds framework references to both the .NET Core and ASP.NET Core shared frameworks.</span></span> <span data-ttu-id="5f62e-121">Les frameworks sont visibles à partir du nœud infrastructures de **dépendances**  >  **Frameworks** dans la fenêtre **Explorateur de solutions** .</span><span class="sxs-lookup"><span data-stu-id="5f62e-121">The frameworks are visible from the **Dependencies** > **Frameworks** node in the **Solution Explorer** window.</span></span> <span data-ttu-id="5f62e-122">Les frameworks partagés sont des collections d’assemblys qui ont été installés sur l’ordinateur lors de l’installation de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5f62e-122">The shared frameworks are collections of assemblies that were installed on the machine when installing .NET Core.</span></span>

<span data-ttu-id="5f62e-123">Bien qu’elles soient prises en charge, les références d’assembly individuelles sont moins fréquentes dans les projets .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5f62e-123">Although they're supported, individual assembly references are less common in .NET Core projects.</span></span> <span data-ttu-id="5f62e-124">La plupart des dépendances de projet sont gérées en tant que références de package NuGet.</span><span class="sxs-lookup"><span data-stu-id="5f62e-124">Most project dependencies are handled as NuGet package references.</span></span> <span data-ttu-id="5f62e-125">Il vous suffit de référencer les dépendances de package de niveau supérieur dans les projets .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5f62e-125">You only need to reference top-level package dependencies in .NET Core projects.</span></span> <span data-ttu-id="5f62e-126">Les dépendances transitives sont incluses automatiquement.</span><span class="sxs-lookup"><span data-stu-id="5f62e-126">Transitive dependencies are included automatically.</span></span> <span data-ttu-id="5f62e-127">Au lieu d’utiliser le fichier *packages.config* couramment trouvé dans les projets ASP.NET Web Forms pour référencer des packages, des références de package sont ajoutées au fichier projet à l’aide de l' `<PackageReference>` élément.</span><span class="sxs-lookup"><span data-stu-id="5f62e-127">Instead of using the *packages.config* file commonly found in ASP.NET Web Forms projects to reference packages, package references are added to the project file using the `<PackageReference>` element.</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="12.0.2" />
</ItemGroup>
```

## <a name="entry-point"></a><span data-ttu-id="5f62e-128">Point d’entrée</span><span class="sxs-lookup"><span data-stu-id="5f62e-128">Entry point</span></span>

<span data-ttu-id="5f62e-129">Le Blazor point d’entrée de l’application serveur est défini dans le fichier *Program.cs* , comme vous pouvez le voir dans une application console.</span><span class="sxs-lookup"><span data-stu-id="5f62e-129">The Blazor Server app's entry point is defined in the *Program.cs* file, as you would see in a Console app.</span></span> <span data-ttu-id="5f62e-130">Lorsque l’application s’exécute, elle crée et exécute une instance d’hôte Web à l’aide des valeurs par défaut spécifiques aux applications Web.</span><span class="sxs-lookup"><span data-stu-id="5f62e-130">When the app executes, it creates and runs a web host instance using defaults specific to web apps.</span></span> <span data-ttu-id="5f62e-131">L’hôte Web gère le Blazor cycle de vie de l’application serveur et configure les services de niveau hôte.</span><span class="sxs-lookup"><span data-stu-id="5f62e-131">The web host manages the Blazor Server app's lifecycle and sets up host-level services.</span></span> <span data-ttu-id="5f62e-132">La configuration, la journalisation, l’injection de dépendances et le serveur HTTP sont des exemples de ces services.</span><span class="sxs-lookup"><span data-stu-id="5f62e-132">Examples of such services are configuration, logging, dependency injection, and the HTTP server.</span></span> <span data-ttu-id="5f62e-133">Ce code est principalement réutilisable et reste souvent inchangé.</span><span class="sxs-lookup"><span data-stu-id="5f62e-133">This code is mostly boilerplate and is often left unchanged.</span></span>

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

Blazor<span data-ttu-id="5f62e-134">les WebAssembly applications définissent également un point d’entrée dans *Program.cs*.</span><span class="sxs-lookup"><span data-stu-id="5f62e-134"> WebAssembly apps also define an entry point in *Program.cs*.</span></span> <span data-ttu-id="5f62e-135">Le code semble légèrement différent.</span><span class="sxs-lookup"><span data-stu-id="5f62e-135">The code looks slightly different.</span></span> <span data-ttu-id="5f62e-136">Le code est similaire en ce qu’il configure l’hôte d’application pour fournir les mêmes services de niveau hôte à l’application.</span><span class="sxs-lookup"><span data-stu-id="5f62e-136">The code is similar in that it's setting up the app host to provide the same host-level services to the app.</span></span> <span data-ttu-id="5f62e-137">WebAssemblyToutefois, l’hôte d’application ne configure pas un serveur http, car il s’exécute directement dans le navigateur.</span><span class="sxs-lookup"><span data-stu-id="5f62e-137">The WebAssembly app host doesn't, however, set up an HTTP server because it executes directly in the browser.</span></span>

Blazor<span data-ttu-id="5f62e-138">les applications ont une `Startup` classe au lieu d’un fichier *global. asax* pour définir la logique de démarrage de l’application.</span><span class="sxs-lookup"><span data-stu-id="5f62e-138"> apps have a `Startup` class instead of a *Global.asax* file to define the startup logic for the app.</span></span> <span data-ttu-id="5f62e-139">La `Startup` classe est utilisée pour configurer l’application et tous les services spécifiques à l’application.</span><span class="sxs-lookup"><span data-stu-id="5f62e-139">The `Startup` class is used to configure the app and any app-specific services.</span></span> <span data-ttu-id="5f62e-140">Dans l' Blazor application serveur, la `Startup` classe est utilisée pour configurer le point de terminaison de la connexion en temps réel utilisée par Blazor entre les navigateurs clients et le serveur.</span><span class="sxs-lookup"><span data-stu-id="5f62e-140">In the Blazor Server app, the `Startup` class is used to set up the endpoint for the real-time connection used by Blazor between the client browsers and the server.</span></span> <span data-ttu-id="5f62e-141">Dans l' Blazor WebAssembly application, la `Startup` classe définit les composants racine pour l’application et l’emplacement où elles doivent être rendues.</span><span class="sxs-lookup"><span data-stu-id="5f62e-141">In the Blazor WebAssembly app, the `Startup` class defines the root components for the app and where they should be rendered.</span></span> <span data-ttu-id="5f62e-142">Nous examinerons plus en détail la `Startup` classe dans la section démarrage de l' [application](./app-startup.md) .</span><span class="sxs-lookup"><span data-stu-id="5f62e-142">We'll take a deeper look at the `Startup` class in the [App startup](./app-startup.md) section.</span></span>

## <a name="static-files"></a><span data-ttu-id="5f62e-143">Fichiers statiques</span><span class="sxs-lookup"><span data-stu-id="5f62e-143">Static files</span></span>

<span data-ttu-id="5f62e-144">Contrairement aux projets ASP.NET Web Forms, tous les fichiers d’un Blazor projet ne peuvent pas être demandés en tant que fichiers statiques.</span><span class="sxs-lookup"><span data-stu-id="5f62e-144">Unlike ASP.NET Web Forms projects, not all files in a Blazor project can be requested as static files.</span></span> <span data-ttu-id="5f62e-145">Seuls les fichiers du dossier *wwwroot* sont adressables par le Web.</span><span class="sxs-lookup"><span data-stu-id="5f62e-145">Only the files in the *wwwroot* folder are web-addressable.</span></span> <span data-ttu-id="5f62e-146">Ce dossier est appelé « racine Web » de l’application.</span><span class="sxs-lookup"><span data-stu-id="5f62e-146">This folder is referred to the app's "web root".</span></span> <span data-ttu-id="5f62e-147">Tout ce qui se trouve en dehors de la racine Web de l’application *n’est pas* adressable par le Web.</span><span class="sxs-lookup"><span data-stu-id="5f62e-147">Anything outside of the app's web root *isn't* web-addressable.</span></span> <span data-ttu-id="5f62e-148">Ce programme d’installation fournit un niveau supplémentaire de sécurité qui empêche l’exposition accidentelle de fichiers projet sur le Web.</span><span class="sxs-lookup"><span data-stu-id="5f62e-148">This setup provides an additional level of security that prevents accidental exposing of project files over the web.</span></span>

## <a name="configuration"></a><span data-ttu-id="5f62e-149">Configuration</span><span class="sxs-lookup"><span data-stu-id="5f62e-149">Configuration</span></span>

<span data-ttu-id="5f62e-150">La configuration dans ASP.NET Web Forms Apps est généralement gérée à l’aide d’un ou plusieurs fichiers *web.config* .</span><span class="sxs-lookup"><span data-stu-id="5f62e-150">Configuration in ASP.NET Web Forms apps is typically handled using one or more *web.config* files.</span></span> Blazor<span data-ttu-id="5f62e-151">les applications n’ont généralement pas de fichiers *web.config* .</span><span class="sxs-lookup"><span data-stu-id="5f62e-151"> apps don't typically have *web.config* files.</span></span> <span data-ttu-id="5f62e-152">Dans ce cas, le fichier est utilisé uniquement pour configurer les paramètres spécifiques à IIS lorsqu’ils sont hébergés sur IIS.</span><span class="sxs-lookup"><span data-stu-id="5f62e-152">If they do, the file is only used to configure IIS-specific settings when hosted on IIS.</span></span> <span data-ttu-id="5f62e-153">Au lieu de cela, Blazor les applications serveur utilisent le ASP.net Core abstractions de la configuration (les Blazor WebAssembly applications ne prennent pas en charge les mêmes abstractions de configuration, mais il peut s’agir d’une fonctionnalité ajoutée à l’avenir).</span><span class="sxs-lookup"><span data-stu-id="5f62e-153">Instead, Blazor Server apps use the ASP.NET Core configuration abstractions (Blazor WebAssembly apps don't currently support the same configuration abstractions, but that may be a feature added in the future).</span></span> <span data-ttu-id="5f62e-154">Par exemple, l' Blazor application serveur par défaut stocke certains paramètres dans *appsettings.jssur*.</span><span class="sxs-lookup"><span data-stu-id="5f62e-154">For example, the default Blazor Server app stores some settings in *appsettings.json*.</span></span>

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

<span data-ttu-id="5f62e-155">Pour plus d’informations sur la configuration dans ASP.NET Core projets, consultez la section [configuration](./config.md) .</span><span class="sxs-lookup"><span data-stu-id="5f62e-155">We'll learn more about configuration in ASP.NET Core projects in the [Configuration](./config.md) section.</span></span>

## <a name="razor-components"></a><span data-ttu-id="5f62e-156">Composants Razor</span><span class="sxs-lookup"><span data-stu-id="5f62e-156">Razor components</span></span>

<span data-ttu-id="5f62e-157">La plupart des fichiers dans Blazor les projets sont des fichiers *. Razor* .</span><span class="sxs-lookup"><span data-stu-id="5f62e-157">Most files in Blazor projects are *.razor* files.</span></span> <span data-ttu-id="5f62e-158">Razor est un langage de création de modèles basé sur HTML et C# qui est utilisé pour générer dynamiquement l’interface utilisateur Web.</span><span class="sxs-lookup"><span data-stu-id="5f62e-158">Razor is a templating language based on HTML and C# that is used to dynamically generate web UI.</span></span> <span data-ttu-id="5f62e-159">Les fichiers *. Razor* définissent les composants qui composent l’interface utilisateur de l’application.</span><span class="sxs-lookup"><span data-stu-id="5f62e-159">The *.razor* files define components that make up the UI of the app.</span></span> <span data-ttu-id="5f62e-160">Pour l’essentiel, les composants sont identiques pour le Blazor serveur et les Blazor WebAssembly applications.</span><span class="sxs-lookup"><span data-stu-id="5f62e-160">For the most part, the components are identical for both the Blazor Server and Blazor WebAssembly apps.</span></span> <span data-ttu-id="5f62e-161">Les composants de Blazor sont analogues aux contrôles utilisateur dans ASP.NET Web Forms.</span><span class="sxs-lookup"><span data-stu-id="5f62e-161">Components in Blazor are analogous to user controls in ASP.NET Web Forms.</span></span>

<span data-ttu-id="5f62e-162">Chaque fichier de composant Razor est compilé dans une classe .NET lorsque le projet est généré.</span><span class="sxs-lookup"><span data-stu-id="5f62e-162">Each Razor component file is compiled into a .NET class when the project is built.</span></span> <span data-ttu-id="5f62e-163">La classe générée capture l’état du composant, la logique de rendu, les méthodes de cycle de vie, les gestionnaires d’événements et d’autres logiques.</span><span class="sxs-lookup"><span data-stu-id="5f62e-163">The generated class captures the component's state, rendering logic, lifecycle methods, event handlers, and other logic.</span></span> <span data-ttu-id="5f62e-164">Nous allons examiner les composants de création de composants de l' [interface utilisateur réutilisables avec Blazor ](./components.md) la section.</span><span class="sxs-lookup"><span data-stu-id="5f62e-164">We'll look at authoring components in the [Building reusable UI components with Blazor](./components.md) section.</span></span>

<span data-ttu-id="5f62e-165">Les fichiers *_Imports. Razor* ne sont pas des fichiers de composants Razor.</span><span class="sxs-lookup"><span data-stu-id="5f62e-165">The *_Imports.razor* files aren't Razor component files.</span></span> <span data-ttu-id="5f62e-166">Au lieu de cela, ils définissent un ensemble de directives Razor à importer dans d’autres fichiers *. Razor* dans le même dossier et dans ses sous-dossiers.</span><span class="sxs-lookup"><span data-stu-id="5f62e-166">Instead, they define a set of Razor directives to import into other *.razor* files within the same folder and in its subfolders.</span></span> <span data-ttu-id="5f62e-167">Par exemple, un fichier *_Imports. Razor* est un moyen conventionnel d’ajouter `using` des directives pour les espaces de noms couramment utilisés :</span><span class="sxs-lookup"><span data-stu-id="5f62e-167">For example, a *_Imports.razor* file is a conventional way to add `using` directives for commonly used namespaces:</span></span>

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

## <a name="pages"></a><span data-ttu-id="5f62e-168">Pages</span><span class="sxs-lookup"><span data-stu-id="5f62e-168">Pages</span></span>

<span data-ttu-id="5f62e-169">Où se trouvent les pages dans les Blazor applications ?</span><span class="sxs-lookup"><span data-stu-id="5f62e-169">Where are the pages in the Blazor apps?</span></span> Blazor<span data-ttu-id="5f62e-170">ne définit pas d’extension de fichier distincte pour les pages adressables, comme les fichiers *. aspx* dans ASP.NET Web Forms apps.</span><span class="sxs-lookup"><span data-stu-id="5f62e-170"> doesn't define a separate file extension for addressable pages, like the *.aspx* files in ASP.NET Web Forms apps.</span></span> <span data-ttu-id="5f62e-171">Au lieu de cela, les pages sont définies en affectant des itinéraires aux composants.</span><span class="sxs-lookup"><span data-stu-id="5f62e-171">Instead, pages are defined by assigning routes to components.</span></span> <span data-ttu-id="5f62e-172">Un itinéraire est généralement affecté à l’aide de la `@page` directive Razor.</span><span class="sxs-lookup"><span data-stu-id="5f62e-172">A route is typically assigned using the `@page` Razor directive.</span></span> <span data-ttu-id="5f62e-173">Par exemple, le `Counter` composant créé dans le fichier *pages/Counter. Razor* définit l’itinéraire suivant :</span><span class="sxs-lookup"><span data-stu-id="5f62e-173">For example, the `Counter` component authored in the *Pages/Counter.razor* file defines the following route:</span></span>

```razor
@page "/counter"
```

<span data-ttu-id="5f62e-174">Le routage dans Blazor est géré côté client et non sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="5f62e-174">Routing in Blazor is handled client-side, not on the server.</span></span> <span data-ttu-id="5f62e-175">Lorsque l’utilisateur navigue dans le navigateur, Blazor intercepte la navigation, puis restitue le composant avec l’itinéraire correspondant.</span><span class="sxs-lookup"><span data-stu-id="5f62e-175">As the user navigates in the browser, Blazor intercepts the navigation and then renders the component with the matching route.</span></span>

<span data-ttu-id="5f62e-176">Les itinéraires des composants ne sont pas actuellement déduits par l’emplacement des fichiers du composant, comme par exemple avec les pages *. aspx* .</span><span class="sxs-lookup"><span data-stu-id="5f62e-176">The component routes aren't currently inferred by the component's file location like they are with *.aspx* pages.</span></span> <span data-ttu-id="5f62e-177">Cette fonctionnalité peut être ajoutée à l’avenir.</span><span class="sxs-lookup"><span data-stu-id="5f62e-177">This feature may be added in the future.</span></span> <span data-ttu-id="5f62e-178">Chaque itinéraire doit être spécifié explicitement sur le composant.</span><span class="sxs-lookup"><span data-stu-id="5f62e-178">Each route must be specified explicitly on the component.</span></span> <span data-ttu-id="5f62e-179">Le stockage de composants routables dans un dossier *pages* n’a aucune signification particulière et constitue purement une convention.</span><span class="sxs-lookup"><span data-stu-id="5f62e-179">Storing routable components in a *Pages* folder has no special meaning and is purely a convention.</span></span>

<span data-ttu-id="5f62e-180">Nous examinerons plus en détail le routage dans Blazor dans la section [pages, routage et dispositions](./pages-routing-layouts.md) .</span><span class="sxs-lookup"><span data-stu-id="5f62e-180">We'll look in greater detail at routing in Blazor in the [Pages, routing, and layouts](./pages-routing-layouts.md) section.</span></span>

## <a name="layout"></a><span data-ttu-id="5f62e-181">Mise en page</span><span class="sxs-lookup"><span data-stu-id="5f62e-181">Layout</span></span>

<span data-ttu-id="5f62e-182">Dans ASP.NET Web Forms Apps, la disposition de page courante est gérée à l’aide de pages maîtres (*site. Master*).</span><span class="sxs-lookup"><span data-stu-id="5f62e-182">In ASP.NET Web Forms apps, common page layout is handled using master pages (*Site.Master*).</span></span> <span data-ttu-id="5f62e-183">Dans les Blazor applications, la mise en page est gérée à l’aide de composants de disposition (*Shared/MainLayout. Razor*).</span><span class="sxs-lookup"><span data-stu-id="5f62e-183">In Blazor apps, page layout is handled using layout components (*Shared/MainLayout.razor*).</span></span> <span data-ttu-id="5f62e-184">Les composants de disposition seront abordés plus en détail dans la section [page, routage et dispositions](./pages-routing-layouts.md) .</span><span class="sxs-lookup"><span data-stu-id="5f62e-184">Layout components will be discussed in more detail in [Page, routing, and layouts](./pages-routing-layouts.md) section.</span></span>

## <a name="bootstrap-blazor"></a><span data-ttu-id="5f62e-185">DémarrageBlazor</span><span class="sxs-lookup"><span data-stu-id="5f62e-185">Bootstrap Blazor</span></span>

<span data-ttu-id="5f62e-186">Pour Blazor le démarrage, l’application doit :</span><span class="sxs-lookup"><span data-stu-id="5f62e-186">To bootstrap Blazor, the app must:</span></span>

- <span data-ttu-id="5f62e-187">Spécifiez l’emplacement de la page où le composant racine (*app. Razor*) doit être rendu.</span><span class="sxs-lookup"><span data-stu-id="5f62e-187">Specify where on the page the root component (*App.Razor*) should be rendered.</span></span>
- <span data-ttu-id="5f62e-188">Ajoutez le Blazor script d’infrastructure correspondant.</span><span class="sxs-lookup"><span data-stu-id="5f62e-188">Add the corresponding Blazor framework script.</span></span>

<span data-ttu-id="5f62e-189">Dans l' Blazor application serveur, la page hôte du composant racine est définie dans le fichier *_Host. cshtml* .</span><span class="sxs-lookup"><span data-stu-id="5f62e-189">In the Blazor Server app, the root component's host page is defined in the *_Host.cshtml* file.</span></span> <span data-ttu-id="5f62e-190">Ce fichier définit une page Razor, et non un composant.</span><span class="sxs-lookup"><span data-stu-id="5f62e-190">This file defines a Razor Page, not a component.</span></span> <span data-ttu-id="5f62e-191">Razor Pages utiliser syntaxe Razor pour définir une page adressable par le serveur, à l’instar d’une page *. aspx* .</span><span class="sxs-lookup"><span data-stu-id="5f62e-191">Razor Pages use Razor syntax to define a server-addressable page, very much like an *.aspx* page.</span></span> <span data-ttu-id="5f62e-192">La `Html.RenderComponentAsync<TComponent>(RenderMode)` méthode est utilisée pour définir l’emplacement où un composant de niveau racine doit être restitué.</span><span class="sxs-lookup"><span data-stu-id="5f62e-192">The `Html.RenderComponentAsync<TComponent>(RenderMode)` method is used to define where a root-level component should be rendered.</span></span> <span data-ttu-id="5f62e-193">L' `RenderMode` option indique la manière dont le composant doit être rendu.</span><span class="sxs-lookup"><span data-stu-id="5f62e-193">The `RenderMode` option indicates the manner in which the component should be rendered.</span></span> <span data-ttu-id="5f62e-194">Le tableau suivant présente les options prises en charge `RenderMode` .</span><span class="sxs-lookup"><span data-stu-id="5f62e-194">The following table outlines the supported `RenderMode` options.</span></span>

|<span data-ttu-id="5f62e-195">Option</span><span class="sxs-lookup"><span data-stu-id="5f62e-195">Option</span></span>                        |<span data-ttu-id="5f62e-196">Description</span><span class="sxs-lookup"><span data-stu-id="5f62e-196">Description</span></span>       |
|------------------------------|------------------|
|`RenderMode.Server`           |<span data-ttu-id="5f62e-197">Rendu interactif une fois qu’une connexion avec le navigateur est établie</span><span class="sxs-lookup"><span data-stu-id="5f62e-197">Rendered interactively once a connection with the browser is established</span></span>|
|`RenderMode.ServerPrerendered`|<span data-ttu-id="5f62e-198">Premier prérendu puis rendu interactif</span><span class="sxs-lookup"><span data-stu-id="5f62e-198">First prerendered and then rendered interactively</span></span>|
|`RenderMode.Static`           |<span data-ttu-id="5f62e-199">Rendu en tant que contenu statique</span><span class="sxs-lookup"><span data-stu-id="5f62e-199">Rendered as static content</span></span>|

<span data-ttu-id="5f62e-200">La référence de script à *_framework/blazor.server.js* établit la connexion en temps réel avec le serveur, puis traite toutes les interactions utilisateur et les mises à jour de l’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="5f62e-200">The script reference to *_framework/blazor.server.js* establishes the real-time connection with the server and then deals with all user interactions and UI updates.</span></span>

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

<span data-ttu-id="5f62e-201">Dans l' Blazor WebAssembly application, la page hôte est un simple fichier HTML statique sous *wwwroot/index.html*.</span><span class="sxs-lookup"><span data-stu-id="5f62e-201">In the Blazor WebAssembly app, the host page is a simple static HTML file under *wwwroot/index.html*.</span></span> <span data-ttu-id="5f62e-202">L' `<app>` élément est utilisé pour indiquer l’emplacement où le composant racine doit être restitué.</span><span class="sxs-lookup"><span data-stu-id="5f62e-202">The `<app>` element is used to indicate where the root component should be rendered.</span></span>

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width" />
    <title>BlazorApp2</title>
    <base href="/" />
    <link href="css/bootstrap/bootstrap.min.css" rel="stylesheet" />
    <link href="css/site.css" rel="stylesheet" />
</head>
<body>
    <app>Loading...</app>

    <script src="_framework/blazor.webassembly.js"></script>
</body>
</html>
```

<span data-ttu-id="5f62e-203">Le composant spécifique à restituer est configuré dans la méthode de l’application `Startup.Configure` avec un sélecteur CSS correspondant indiquant où le composant doit être rendu.</span><span class="sxs-lookup"><span data-stu-id="5f62e-203">The specific component to render is configured in the app's `Startup.Configure` method with a corresponding CSS selector indicating where the component should be rendered.</span></span>

```csharp
public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
    }

    public void Configure(IComponentsApplicationBuilder app)
    {
        app.AddComponent<App>("app");
    }
}
```

## <a name="build-output"></a><span data-ttu-id="5f62e-204">Sortie de la génération</span><span class="sxs-lookup"><span data-stu-id="5f62e-204">Build output</span></span>

<span data-ttu-id="5f62e-205">Lorsqu’un Blazor projet est généré, tous les fichiers de code et de composant Razor sont compilés dans un assembly unique.</span><span class="sxs-lookup"><span data-stu-id="5f62e-205">When a Blazor project is built, all Razor component and code files are compiled into a single assembly.</span></span> <span data-ttu-id="5f62e-206">Contrairement aux projets ASP.NET Web Forms, Blazor ne prend pas en charge la compilation du runtime de la logique d’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="5f62e-206">Unlike ASP.NET Web Forms projects, Blazor doesn't support runtime compilation of the UI logic.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="5f62e-207">Exécuter l’application</span><span class="sxs-lookup"><span data-stu-id="5f62e-207">Run the app</span></span>

<span data-ttu-id="5f62e-208">Pour exécuter l' Blazor application serveur, appuyez sur `F5` dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5f62e-208">To run the Blazor Server app, press `F5` in Visual Studio.</span></span> Blazor<span data-ttu-id="5f62e-209">les applications ne prennent pas en charge la compilation du Runtime.</span><span class="sxs-lookup"><span data-stu-id="5f62e-209"> apps don't support runtime compilation.</span></span> <span data-ttu-id="5f62e-210">Pour afficher les résultats des modifications du balisage du code et des composants, régénérez et redémarrez l’application avec le débogueur attaché.</span><span class="sxs-lookup"><span data-stu-id="5f62e-210">To see the results of code and component markup changes, rebuild and restart the app with the debugger attached.</span></span> <span data-ttu-id="5f62e-211">Si vous exécutez sans le débogueur attaché ( `Ctrl+F5` ), Visual Studio surveille les modifications apportées aux fichiers et redémarre l’application à mesure que des modifications sont apportées.</span><span class="sxs-lookup"><span data-stu-id="5f62e-211">If you run without the debugger attached (`Ctrl+F5`), Visual Studio watches for file changes and restarts the app as changes are made.</span></span> <span data-ttu-id="5f62e-212">Vous actualisez manuellement le navigateur à mesure que des modifications sont apportées.</span><span class="sxs-lookup"><span data-stu-id="5f62e-212">You manually refresh the browser as changes are made.</span></span>

<span data-ttu-id="5f62e-213">Pour exécuter l' Blazor WebAssembly application, choisissez l’une des approches suivantes :</span><span class="sxs-lookup"><span data-stu-id="5f62e-213">To run the Blazor WebAssembly app, choose one of the following approaches:</span></span>

- <span data-ttu-id="5f62e-214">Exécutez le projet client directement à l’aide du serveur de développement.</span><span class="sxs-lookup"><span data-stu-id="5f62e-214">Run the client project directly using the development server.</span></span>
- <span data-ttu-id="5f62e-215">Exécutez le projet serveur lors de l’hébergement de l’application avec ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="5f62e-215">Run the server project when hosting the app with ASP.NET Core.</span></span>

Blazor<span data-ttu-id="5f62e-216">les WebAssembly applications ne prennent pas en charge le débogage à l’aide de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5f62e-216"> WebAssembly apps don't support debugging using Visual Studio.</span></span> <span data-ttu-id="5f62e-217">Pour exécuter l’application, utilisez `Ctrl+F5` au lieu de `F5` .</span><span class="sxs-lookup"><span data-stu-id="5f62e-217">To run the app, use `Ctrl+F5` instead of `F5`.</span></span> <span data-ttu-id="5f62e-218">Au lieu de cela, vous pouvez déboguer Blazor WebAssembly des applications directement dans le navigateur.</span><span class="sxs-lookup"><span data-stu-id="5f62e-218">You can instead debug Blazor WebAssembly apps directly in the browser.</span></span> <span data-ttu-id="5f62e-219">Pour plus d’informations, consultez [ Blazor ASP.net Core de débogage](/aspnet/core/blazor/debug) .</span><span class="sxs-lookup"><span data-stu-id="5f62e-219">See [Debug ASP.NET Core Blazor](/aspnet/core/blazor/debug) for details.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="5f62e-220">[Précédent](hosting-models.md) 
> [Suivant](app-startup.md)</span><span class="sxs-lookup"><span data-stu-id="5f62e-220">[Previous](hosting-models.md)
[Next](app-startup.md)</span></span>
