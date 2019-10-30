---
title: Structure de projet pour les applications éblouissantes
description: Découvrez comment les structures de projet des ASP.NET Web Forms et des projets éblouissants sont comparées.
author: danroth27
ms.author: daroth
ms.date: 09/11/2019
ms.openlocfilehash: 2c383e86ff22f5a3460476998992b66e9417cc11
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73087862"
---
# <a name="project-structure-for-blazor-apps"></a><span data-ttu-id="fe9b6-103">Structure de projet pour les applications éblouissantes</span><span class="sxs-lookup"><span data-stu-id="fe9b6-103">Project structure for Blazor apps</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="fe9b6-104">Malgré leurs différences de structure de projet, ASP.NET Web Forms et éblouissant partagent un grand nombre de concepts similaires.</span><span class="sxs-lookup"><span data-stu-id="fe9b6-104">Despite their significant project structure differences, ASP.NET Web Forms and Blazor share many similar concepts.</span></span> <span data-ttu-id="fe9b6-105">Ici, nous allons examiner la structure d’un projet éblouissant et le comparer à un projet de Web Forms ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="fe9b6-105">Here, we'll look at the structure of a Blazor project and compare it to an ASP.NET Web Forms project.</span></span>

<span data-ttu-id="fe9b6-106">Pour créer votre première application éblouissante, suivez les instructions fournies dans les [étapes de prise](/aspnet/core/blazor/get-started)en main de éblouissant.</span><span class="sxs-lookup"><span data-stu-id="fe9b6-106">To create your first Blazor app, follow the instructions in the [Blazor getting started steps](/aspnet/core/blazor/get-started).</span></span> <span data-ttu-id="fe9b6-107">Vous pouvez suivre les instructions pour créer une application de serveur éblouissant ou une application de webassembly éblouissante hébergée dans ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="fe9b6-107">You can follow the instructions to create either a Blazor Server app or a Blazor WebAssembly app hosted in ASP.NET Core.</span></span> <span data-ttu-id="fe9b6-108">À l’exception de la logique spécifique au modèle d’hébergement, la majeure partie du code dans les deux projets est identique.</span><span class="sxs-lookup"><span data-stu-id="fe9b6-108">Except for the hosting model-specific logic, most of the code in both projects is the same.</span></span>

## <a name="project-file"></a><span data-ttu-id="fe9b6-109">Fichier projet</span><span class="sxs-lookup"><span data-stu-id="fe9b6-109">Project file</span></span>

<span data-ttu-id="fe9b6-110">Les applications serveur éblouissantes sont des projets .NET Core.</span><span class="sxs-lookup"><span data-stu-id="fe9b6-110">Blazor Server apps are .NET Core projects.</span></span> <span data-ttu-id="fe9b6-111">Le fichier projet pour l’application de serveur éblouissante est à la fois aussi simple que possible :</span><span class="sxs-lookup"><span data-stu-id="fe9b6-111">The project file for the Blazor Server app is about as simple as it can get:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>netcoreapp3.0</TargetFramework>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="fe9b6-112">Le fichier projet pour une application de webassembly éblouissant est légèrement plus impliqué (les numéros de version exacts peuvent varier) :</span><span class="sxs-lookup"><span data-stu-id="fe9b6-112">The project file for a Blazor WebAssembly app looks slightly more involved (exact version numbers may vary):</span></span>

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

<span data-ttu-id="fe9b6-113">Les projets de webassembly éblouissant ciblent .NET Standard au lieu de .NET Core, car ils s’exécutent dans le navigateur sur un Runtime .NET basé sur webassembly.</span><span class="sxs-lookup"><span data-stu-id="fe9b6-113">Blazor WebAssembly projects target .NET Standard instead of .NET Core because they run in the browser on a WebAssembly-based .NET runtime.</span></span> <span data-ttu-id="fe9b6-114">Vous ne pouvez pas installer .NET dans un navigateur Web comme vous le pouvez sur un serveur ou un ordinateur de développement.</span><span class="sxs-lookup"><span data-stu-id="fe9b6-114">You can't install .NET into a web browser like you can on a server or developer machine.</span></span> <span data-ttu-id="fe9b6-115">Par conséquent, le projet fait référence au Framework éblouissant à l’aide de références de package individuelles.</span><span class="sxs-lookup"><span data-stu-id="fe9b6-115">Consequently, the project references the Blazor framework using individual package references.</span></span>

<span data-ttu-id="fe9b6-116">Par comparaison, un projet ASP.NET Web Forms par défaut comprend près de 300 lignes de code XML dans son fichier *. csproj* , dont la plupart répertorient explicitement les différents fichiers de code et de contenu du projet.</span><span class="sxs-lookup"><span data-stu-id="fe9b6-116">By comparison, a default ASP.NET Web Forms project includes almost 300 lines of XML in its *.csproj* file, most of which is explicitly listing the various code and content files in the project.</span></span> <span data-ttu-id="fe9b6-117">La plupart des simplifications dans les projets .NET Core et .NET Standard proviennent des cibles et des propriétés par défaut importées en référençant le kit de développement logiciel (SDK) `Microsoft.NET.Sdk.Web`, souvent appelé simplement le kit de développement logiciel (SDK) Web.</span><span class="sxs-lookup"><span data-stu-id="fe9b6-117">Many of the simplifications in the .NET Core- and .NET Standard-based projects come from the default targets and properties imported by referencing the `Microsoft.NET.Sdk.Web` SDK, often referred to as simply the Web SDK.</span></span> <span data-ttu-id="fe9b6-118">Le kit de développement logiciel (SDK) Web comprend des caractères génériques et d’autres pratiques qui simplifient l’inclusion de code et de fichiers de contenu dans le projet.</span><span class="sxs-lookup"><span data-stu-id="fe9b6-118">The Web SDK includes wildcards and other conveniences that simplify inclusion of code and content files in the project.</span></span> <span data-ttu-id="fe9b6-119">Vous n’avez pas besoin de répertorier les fichiers explicitement.</span><span class="sxs-lookup"><span data-stu-id="fe9b6-119">You don't need to list the files explicitly.</span></span> <span data-ttu-id="fe9b6-120">Quand vous ciblez .NET Core, le kit de développement logiciel (SDK) Web ajoute également des références d’infrastructure aux frameworks partagés .NET Core et ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="fe9b6-120">When targeting .NET Core, the Web SDK also adds framework references to both the .NET Core and ASP.NET Core shared frameworks.</span></span> <span data-ttu-id="fe9b6-121">Les frameworks sont visibles à partir du nœud **dépendances**  > **infrastructures** dans la fenêtre **Explorateur de solutions** .</span><span class="sxs-lookup"><span data-stu-id="fe9b6-121">The frameworks are visible from the **Dependencies** > **Frameworks** node in the **Solution Explorer** window.</span></span> <span data-ttu-id="fe9b6-122">Les frameworks partagés sont des collections d’assemblys qui ont été installés sur l’ordinateur lors de l’installation de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="fe9b6-122">The shared frameworks are collections of assemblies that were installed on the machine when installing .NET Core.</span></span>

<span data-ttu-id="fe9b6-123">Bien qu’elles soient prises en charge, les références d’assembly individuelles sont moins fréquentes dans les projets .NET Core.</span><span class="sxs-lookup"><span data-stu-id="fe9b6-123">Although they're supported, individual assembly references are less common in .NET Core projects.</span></span> <span data-ttu-id="fe9b6-124">La plupart des dépendances de projet sont gérées en tant que références de package NuGet.</span><span class="sxs-lookup"><span data-stu-id="fe9b6-124">Most project dependencies are handled as NuGet package references.</span></span> <span data-ttu-id="fe9b6-125">Il vous suffit de référencer les dépendances de package de niveau supérieur dans les projets .NET Core.</span><span class="sxs-lookup"><span data-stu-id="fe9b6-125">You only need to reference top-level package dependencies in .NET Core projects.</span></span> <span data-ttu-id="fe9b6-126">Les dépendances transitives sont incluses automatiquement.</span><span class="sxs-lookup"><span data-stu-id="fe9b6-126">Transitive dependencies are included automatically.</span></span> <span data-ttu-id="fe9b6-127">Au lieu d’utiliser le fichier *packages. config* couramment trouvé dans les projets ASP.NET Web Forms pour référencer des packages, des références de package sont ajoutées au fichier projet à l’aide de l’élément `<PackageReference>`.</span><span class="sxs-lookup"><span data-stu-id="fe9b6-127">Instead of using the *packages.config* file commonly found in ASP.NET Web Forms projects to reference packages, package references are added to the project file using the `<PackageReference>` element.</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="12.0.2" />
</ItemGroup>
```

## <a name="entry-point"></a><span data-ttu-id="fe9b6-128">Point d’entrée</span><span class="sxs-lookup"><span data-stu-id="fe9b6-128">Entry point</span></span>

<span data-ttu-id="fe9b6-129">Le point d’entrée de l’application serveur éblouissant est défini dans le fichier *Program.cs* , comme vous pouvez le voir dans une application console.</span><span class="sxs-lookup"><span data-stu-id="fe9b6-129">The Blazor Server app's entry point is defined in the *Program.cs* file, as you would see in a Console app.</span></span> <span data-ttu-id="fe9b6-130">Lorsque l’application s’exécute, elle crée et exécute une instance d’hôte Web à l’aide des valeurs par défaut spécifiques aux applications Web.</span><span class="sxs-lookup"><span data-stu-id="fe9b6-130">When the app executes, it creates and runs a web host instance using defaults specific to web apps.</span></span> <span data-ttu-id="fe9b6-131">L’hôte Web gère le cycle de vie de l’application serveur éblouissante et configure les services de niveau hôte.</span><span class="sxs-lookup"><span data-stu-id="fe9b6-131">The web host manages the Blazor Server app's lifecycle and sets up host-level services.</span></span> <span data-ttu-id="fe9b6-132">La configuration, la journalisation, l’injection de dépendances et le serveur HTTP sont des exemples de ces services.</span><span class="sxs-lookup"><span data-stu-id="fe9b6-132">Examples of such services are configuration, logging, dependency injection, and the HTTP server.</span></span> <span data-ttu-id="fe9b6-133">Ce code est principalement réutilisable et reste souvent inchangé.</span><span class="sxs-lookup"><span data-stu-id="fe9b6-133">This code is mostly boilerplate and is often left unchanged.</span></span>

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

<span data-ttu-id="fe9b6-134">Les applications de webassembly éblouissantes définissent également un point d’entrée dans *Program.cs*.</span><span class="sxs-lookup"><span data-stu-id="fe9b6-134">Blazor WebAssembly apps also define an entry point in *Program.cs*.</span></span> <span data-ttu-id="fe9b6-135">Le code semble légèrement différent.</span><span class="sxs-lookup"><span data-stu-id="fe9b6-135">The code looks slightly different.</span></span> <span data-ttu-id="fe9b6-136">Le code est similaire en ce qu’il configure l’hôte d’application pour fournir les mêmes services de niveau hôte à l’application.</span><span class="sxs-lookup"><span data-stu-id="fe9b6-136">The code is similar in that it's setting up the app host to provide the same host-level services to the app.</span></span> <span data-ttu-id="fe9b6-137">Toutefois, l’hôte d’application webassembly ne configure pas un serveur HTTP, car il s’exécute directement dans le navigateur.</span><span class="sxs-lookup"><span data-stu-id="fe9b6-137">The WebAssembly app host doesn't, however, set up an HTTP server because it executes directly in the browser.</span></span>

<span data-ttu-id="fe9b6-138">Les applications éblouissantes ont une classe `Startup` au lieu d’un fichier *global. asax* pour définir la logique de démarrage de l’application.</span><span class="sxs-lookup"><span data-stu-id="fe9b6-138">Blazor apps have a `Startup` class instead of a *Global.asax* file to define the startup logic for the app.</span></span> <span data-ttu-id="fe9b6-139">La classe `Startup` est utilisée pour configurer l’application et tous les services spécifiques à l’application.</span><span class="sxs-lookup"><span data-stu-id="fe9b6-139">The `Startup` class is used to configure the app and any app-specific services.</span></span> <span data-ttu-id="fe9b6-140">Dans l’application de serveur éblouissant, la classe `Startup` est utilisée pour configurer le point de terminaison de la connexion en temps réel utilisée par éblouissant entre les navigateurs clients et le serveur.</span><span class="sxs-lookup"><span data-stu-id="fe9b6-140">In the Blazor Server app, the `Startup` class is used to set up the endpoint for the real-time connection used by Blazor between the client browsers and the server.</span></span> <span data-ttu-id="fe9b6-141">Dans l’application de webassembly éblouissant, la classe `Startup` définit les composants racine de l’application et l’emplacement où elles doivent être rendues.</span><span class="sxs-lookup"><span data-stu-id="fe9b6-141">In the Blazor WebAssembly app, the `Startup` class defines the root components for the app and where they should be rendered.</span></span> <span data-ttu-id="fe9b6-142">Nous examinerons plus en détail la classe `Startup` dans la section démarrage de l' [application](./app-startup.md) .</span><span class="sxs-lookup"><span data-stu-id="fe9b6-142">We'll take a deeper look at the `Startup` class in the [App startup](./app-startup.md) section.</span></span>

## <a name="static-files"></a><span data-ttu-id="fe9b6-143">Fichiers statiques</span><span class="sxs-lookup"><span data-stu-id="fe9b6-143">Static files</span></span>

<span data-ttu-id="fe9b6-144">Contrairement aux projets ASP.NET Web Forms, tous les fichiers d’un projet éblouissant ne peuvent pas être demandés en tant que fichiers statiques.</span><span class="sxs-lookup"><span data-stu-id="fe9b6-144">Unlike ASP.NET Web Forms projects, not all files in a Blazor project can be requested as static files.</span></span> <span data-ttu-id="fe9b6-145">Seuls les fichiers du dossier *wwwroot* sont adressables par le Web.</span><span class="sxs-lookup"><span data-stu-id="fe9b6-145">Only the files in the *wwwroot* folder are web-addressable.</span></span> <span data-ttu-id="fe9b6-146">Ce dossier est appelé « racine Web » de l’application.</span><span class="sxs-lookup"><span data-stu-id="fe9b6-146">This folder is referred to the app's "web root".</span></span> <span data-ttu-id="fe9b6-147">Tout ce qui se trouve en dehors de la racine Web de l’application *n’est pas* adressable par le Web.</span><span class="sxs-lookup"><span data-stu-id="fe9b6-147">Anything outside of the app's web root *isn't* web-addressable.</span></span> <span data-ttu-id="fe9b6-148">Ce programme d’installation fournit un niveau supplémentaire de sécurité qui empêche l’exposition accidentelle de fichiers projet sur le Web.</span><span class="sxs-lookup"><span data-stu-id="fe9b6-148">This setup provides an additional level of security that prevents accidental exposing of project files over the web.</span></span>

## <a name="configuration"></a><span data-ttu-id="fe9b6-149">Configuration</span><span class="sxs-lookup"><span data-stu-id="fe9b6-149">Configuration</span></span>

<span data-ttu-id="fe9b6-150">La configuration dans ASP.NET Web Forms Apps est généralement gérée à l’aide d’un ou de plusieurs fichiers *Web. config* .</span><span class="sxs-lookup"><span data-stu-id="fe9b6-150">Configuration in ASP.NET Web Forms apps is typically handled using one or more *web.config* files.</span></span> <span data-ttu-id="fe9b6-151">Les applications éblouissantes n’ont généralement pas de fichiers *Web. config* .</span><span class="sxs-lookup"><span data-stu-id="fe9b6-151">Blazor apps don't typically have *web.config* files.</span></span> <span data-ttu-id="fe9b6-152">Dans ce cas, le fichier est utilisé uniquement pour configurer les paramètres spécifiques à IIS lorsqu’ils sont hébergés sur IIS.</span><span class="sxs-lookup"><span data-stu-id="fe9b6-152">If they do, the file is only used to configure IIS-specific settings when hosted on IIS.</span></span> <span data-ttu-id="fe9b6-153">Au lieu de cela, les applications de serveur éblouissant utilisent le ASP.NET Core abstractions de la configuration (les applications webassembly éblouissantes ne prennent pas en charge les mêmes abstractions de configuration, mais il peut s’agir d’une fonctionnalité ajoutée à l’avenir).</span><span class="sxs-lookup"><span data-stu-id="fe9b6-153">Instead, Blazor Server apps use the ASP.NET Core configuration abstractions (Blazor WebAssembly apps don't currently support the same configuration abstractions, but that may be a feature added in the future).</span></span> <span data-ttu-id="fe9b6-154">Par exemple, l’application de serveur éblouissante par défaut stocke certains paramètres dans *appSettings. JSON*.</span><span class="sxs-lookup"><span data-stu-id="fe9b6-154">For example, the default Blazor Server app stores some settings in *appsettings.json*.</span></span>

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

<span data-ttu-id="fe9b6-155">Pour plus d’informations sur la configuration dans ASP.NET Core projets, consultez la section [configuration](./config.md) .</span><span class="sxs-lookup"><span data-stu-id="fe9b6-155">We'll learn more about configuration in ASP.NET Core projects in the [Configuration](./config.md) section.</span></span>

## <a name="razor-components"></a><span data-ttu-id="fe9b6-156">Composants Razor</span><span class="sxs-lookup"><span data-stu-id="fe9b6-156">Razor components</span></span>

<span data-ttu-id="fe9b6-157">La plupart des fichiers dans les projets éblouissants sont des fichiers *. Razor* .</span><span class="sxs-lookup"><span data-stu-id="fe9b6-157">Most files in Blazor projects are *.razor* files.</span></span> <span data-ttu-id="fe9b6-158">Razor est un langage de création de modèles basé C# sur HTML et utilisé pour générer dynamiquement l’interface utilisateur Web.</span><span class="sxs-lookup"><span data-stu-id="fe9b6-158">Razor is a templating language based on HTML and C# that is used to dynamically generate web UI.</span></span> <span data-ttu-id="fe9b6-159">Les fichiers *. Razor* définissent les composants qui composent l’interface utilisateur de l’application.</span><span class="sxs-lookup"><span data-stu-id="fe9b6-159">The *.razor* files define components that make up the UI of the app.</span></span> <span data-ttu-id="fe9b6-160">Pour l’essentiel, les composants sont identiques pour le serveur éblouissant et les applications webassembly éblouissantes.</span><span class="sxs-lookup"><span data-stu-id="fe9b6-160">For the most part, the components are identical for both the Blazor Server and Blazor WebAssembly apps.</span></span> <span data-ttu-id="fe9b6-161">Les composants de éblouissant sont analogues aux contrôles utilisateur dans ASP.NET Web Forms.</span><span class="sxs-lookup"><span data-stu-id="fe9b6-161">Components in Blazor are analogous to user controls in ASP.NET Web Forms.</span></span>

<span data-ttu-id="fe9b6-162">Chaque fichier de composant Razor est compilé dans une classe .NET lorsque le projet est généré.</span><span class="sxs-lookup"><span data-stu-id="fe9b6-162">Each Razor component file is compiled into a .NET class when the project is built.</span></span> <span data-ttu-id="fe9b6-163">La classe générée capture l’état du composant, la logique de rendu, les méthodes de cycle de vie, les gestionnaires d’événements et d’autres logiques.</span><span class="sxs-lookup"><span data-stu-id="fe9b6-163">The generated class captures the component's state, rendering logic, lifecycle methods, event handlers, and other logic.</span></span> <span data-ttu-id="fe9b6-164">Nous examinerons la création de composants dans la section [création de composants d’interface utilisateur réutilisables avec éblouissant](./components.md) .</span><span class="sxs-lookup"><span data-stu-id="fe9b6-164">We'll look at authoring components in the [Building reusable UI components with Blazor](./components.md) section.</span></span>

<span data-ttu-id="fe9b6-165">Les fichiers *_Imports. Razor* ne sont pas des fichiers de composants Razor.</span><span class="sxs-lookup"><span data-stu-id="fe9b6-165">The *_Imports.razor* files aren't Razor component files.</span></span> <span data-ttu-id="fe9b6-166">Au lieu de cela, ils définissent un ensemble de directives Razor à importer dans d’autres fichiers *. Razor* dans le même dossier et dans ses sous-dossiers.</span><span class="sxs-lookup"><span data-stu-id="fe9b6-166">Instead, they define a set of Razor directives to import into other *.razor* files within the same folder and in its subfolders.</span></span> <span data-ttu-id="fe9b6-167">Par exemple, un fichier *_Imports. Razor* est un moyen conventionnel d’ajouter des instructions `using` pour les espaces de noms couramment utilisés :</span><span class="sxs-lookup"><span data-stu-id="fe9b6-167">For example, a *_Imports.razor* file is a conventional way to add `using` statements for commonly used namespaces:</span></span>

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

## <a name="pages"></a><span data-ttu-id="fe9b6-168">Pages</span><span class="sxs-lookup"><span data-stu-id="fe9b6-168">Pages</span></span>

<span data-ttu-id="fe9b6-169">Où se trouvent les pages des applications éblouissantes ?</span><span class="sxs-lookup"><span data-stu-id="fe9b6-169">Where are the pages in the Blazor apps?</span></span> <span data-ttu-id="fe9b6-170">Éblouissant ne définit pas d’extension de fichier distincte pour les pages adressables, comme les fichiers *. aspx* dans ASP.NET Web Forms apps.</span><span class="sxs-lookup"><span data-stu-id="fe9b6-170">Blazor doesn't define a separate file extension for addressable pages, like the *.aspx* files in ASP.NET Web Forms apps.</span></span> <span data-ttu-id="fe9b6-171">Au lieu de cela, les pages sont définies en affectant des itinéraires aux composants.</span><span class="sxs-lookup"><span data-stu-id="fe9b6-171">Instead, pages are defined by assigning routes to components.</span></span> <span data-ttu-id="fe9b6-172">Un itinéraire est généralement affecté à l’aide de la directive `@page` Razor.</span><span class="sxs-lookup"><span data-stu-id="fe9b6-172">A route is typically assigned using the `@page` Razor directive.</span></span> <span data-ttu-id="fe9b6-173">Par exemple, le composant `Counter` créé dans le fichier *pages/Counter. Razor* définit l’itinéraire suivant :</span><span class="sxs-lookup"><span data-stu-id="fe9b6-173">For example, the `Counter` component authored in the *Pages/Counter.razor* file defines the following route:</span></span>

```razor
@page "/counter"
```

<span data-ttu-id="fe9b6-174">Le routage dans éblouissant est géré côté client et non sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="fe9b6-174">Routing in Blazor is handled client-side, not on the server.</span></span> <span data-ttu-id="fe9b6-175">Lorsque l’utilisateur navigue dans le navigateur, éblouissant intercepte la navigation, puis restitue le composant avec l’itinéraire correspondant.</span><span class="sxs-lookup"><span data-stu-id="fe9b6-175">As the user navigates in the browser, Blazor intercepts the navigation and then renders the component with the matching route.</span></span>

<span data-ttu-id="fe9b6-176">Les itinéraires des composants ne sont pas actuellement déduits par l’emplacement des fichiers du composant, comme par exemple avec les pages *. aspx* .</span><span class="sxs-lookup"><span data-stu-id="fe9b6-176">The component routes aren't currently inferred by the component's file location like they are with *.aspx* pages.</span></span> <span data-ttu-id="fe9b6-177">Cette fonctionnalité peut être ajoutée à l’avenir.</span><span class="sxs-lookup"><span data-stu-id="fe9b6-177">This feature may be added in the future.</span></span> <span data-ttu-id="fe9b6-178">Chaque itinéraire doit être spécifié explicitement sur le composant.</span><span class="sxs-lookup"><span data-stu-id="fe9b6-178">Each route must be specified explicitly on the component.</span></span> <span data-ttu-id="fe9b6-179">Le stockage de composants routables dans un dossier *pages* n’a aucune signification particulière et constitue purement une convention.</span><span class="sxs-lookup"><span data-stu-id="fe9b6-179">Storing routable components in a *Pages* folder has no special meaning and is purely a convention.</span></span>

<span data-ttu-id="fe9b6-180">Nous examinerons plus en détail le routage dans éblouissant dans la section [pages, routage et dispositions](./pages-routing-layouts.md) .</span><span class="sxs-lookup"><span data-stu-id="fe9b6-180">We'll look in greater detail at routing in Blazor in the [Pages, routing, and layouts](./pages-routing-layouts.md) section.</span></span>

## <a name="layout"></a><span data-ttu-id="fe9b6-181">Mise en page</span><span class="sxs-lookup"><span data-stu-id="fe9b6-181">Layout</span></span>

<span data-ttu-id="fe9b6-182">Dans ASP.NET Web Forms Apps, la disposition de page courante est gérée à l’aide de pages maîtres (*site. Master*).</span><span class="sxs-lookup"><span data-stu-id="fe9b6-182">In ASP.NET Web Forms apps, common page layout is handled using master pages (*Site.Master*).</span></span> <span data-ttu-id="fe9b6-183">Dans les applications éblouissantes, la mise en page est gérée à l’aide de composants de disposition (*Shared/MainLayout. Razor*).</span><span class="sxs-lookup"><span data-stu-id="fe9b6-183">In Blazor apps, page layout is handled using layout components (*Shared/MainLayout.razor*).</span></span> <span data-ttu-id="fe9b6-184">Les composants de disposition seront abordés plus en détail dans la section [page, routage et dispositions](./pages-routing-layouts.md) .</span><span class="sxs-lookup"><span data-stu-id="fe9b6-184">Layout components will be discussed in more detail in [Page, routing, and layouts](./pages-routing-layouts.md) section.</span></span>

## <a name="bootstrap-blazor"></a><span data-ttu-id="fe9b6-185">Démarrage éblouissant</span><span class="sxs-lookup"><span data-stu-id="fe9b6-185">Bootstrap Blazor</span></span>

<span data-ttu-id="fe9b6-186">Pour démarrer éblouissant, l’application doit :</span><span class="sxs-lookup"><span data-stu-id="fe9b6-186">To bootstrap Blazor, the app must:</span></span>

- <span data-ttu-id="fe9b6-187">Spécifiez l’emplacement de la page où le composant racine (*app. Razor*) doit être rendu.</span><span class="sxs-lookup"><span data-stu-id="fe9b6-187">Specify where on the page the root component (*App.Razor*) should be rendered.</span></span>
- <span data-ttu-id="fe9b6-188">Ajoutez le script de Framework éblouissant correspondant.</span><span class="sxs-lookup"><span data-stu-id="fe9b6-188">Add the corresponding Blazor framework script.</span></span>

<span data-ttu-id="fe9b6-189">Dans l’application de serveur éblouissant, la page hôte du composant racine est définie dans le fichier *_Host. cshtml* .</span><span class="sxs-lookup"><span data-stu-id="fe9b6-189">In the Blazor Server app, the root component's host page is defined in the *_Host.cshtml* file.</span></span> <span data-ttu-id="fe9b6-190">Ce fichier définit une page Razor, et non un composant.</span><span class="sxs-lookup"><span data-stu-id="fe9b6-190">This file defines a Razor Page, not a component.</span></span> <span data-ttu-id="fe9b6-191">Razor Pages utiliser syntaxe Razor pour définir une page adressable par le serveur, à l’instar d’une page *. aspx* .</span><span class="sxs-lookup"><span data-stu-id="fe9b6-191">Razor Pages use Razor syntax to define a server-addressable page, very much like an *.aspx* page.</span></span> <span data-ttu-id="fe9b6-192">La méthode `Html.RenderComponentAsync<TComponent>(RenderMode)` est utilisée pour définir l’emplacement de rendu d’un composant de niveau racine.</span><span class="sxs-lookup"><span data-stu-id="fe9b6-192">The `Html.RenderComponentAsync<TComponent>(RenderMode)` method is used to define where a root-level component should be rendered.</span></span> <span data-ttu-id="fe9b6-193">L’option `RenderMode` indique la manière dont le composant doit être rendu.</span><span class="sxs-lookup"><span data-stu-id="fe9b6-193">The `RenderMode` option indicates the manner in which the component should be rendered.</span></span> <span data-ttu-id="fe9b6-194">Le tableau suivant présente les options de `RenderMode` prises en charge.</span><span class="sxs-lookup"><span data-stu-id="fe9b6-194">The following table outlines the supported `RenderMode` options.</span></span>

|<span data-ttu-id="fe9b6-195">Option</span><span class="sxs-lookup"><span data-stu-id="fe9b6-195">Option</span></span>                        |<span data-ttu-id="fe9b6-196">Description</span><span class="sxs-lookup"><span data-stu-id="fe9b6-196">Description</span></span>       |
|------------------------------|------------------|
|`RenderMode.Server`           |<span data-ttu-id="fe9b6-197">Rendu interactif une fois qu’une connexion avec le navigateur est établie</span><span class="sxs-lookup"><span data-stu-id="fe9b6-197">Rendered interactively once a connection with the browser is established</span></span>|
|`RenderMode.ServerPrerendered`|<span data-ttu-id="fe9b6-198">Premier prérendu puis rendu interactif</span><span class="sxs-lookup"><span data-stu-id="fe9b6-198">First prerendered and then rendered interactively</span></span>|
|`RenderMode.Static`           |<span data-ttu-id="fe9b6-199">Rendu en tant que contenu statique</span><span class="sxs-lookup"><span data-stu-id="fe9b6-199">Rendered as static content</span></span>|

<span data-ttu-id="fe9b6-200">La référence de script à *_framework/éblouissant. Server. js* établit la connexion en temps réel avec le serveur, puis traite toutes les interactions utilisateur et les mises à jour de l’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="fe9b6-200">The script reference to *_framework/blazor.server.js* establishes the real-time connection with the server and then deals with all user interactions and UI updates.</span></span>

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

<span data-ttu-id="fe9b6-201">Dans l’application de webassembly éblouissant, la page hôte est un simple fichier HTML statique sous *wwwroot/index.html*.</span><span class="sxs-lookup"><span data-stu-id="fe9b6-201">In the Blazor WebAssembly app, the host page is a simple static HTML file under *wwwroot/index.html*.</span></span> <span data-ttu-id="fe9b6-202">L’élément `<app>` est utilisé pour indiquer l’emplacement où le composant racine doit être restitué.</span><span class="sxs-lookup"><span data-stu-id="fe9b6-202">The `<app>` element is used to indicate where the root component should be rendered.</span></span>

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

<span data-ttu-id="fe9b6-203">Le composant spécifique à restituer est configuré dans la méthode `Startup.Configure` de l’application avec un sélecteur CSS correspondant indiquant où le composant doit être rendu.</span><span class="sxs-lookup"><span data-stu-id="fe9b6-203">The specific component to render is configured in the app's `Startup.Configure` method with a corresponding CSS selector indicating where the component should be rendered.</span></span>

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

## <a name="build-output"></a><span data-ttu-id="fe9b6-204">Sortie de la génération</span><span class="sxs-lookup"><span data-stu-id="fe9b6-204">Build output</span></span>

<span data-ttu-id="fe9b6-205">Lorsqu’un projet éblouissant est généré, tous les fichiers de code et de composant Razor sont compilés dans un assembly unique.</span><span class="sxs-lookup"><span data-stu-id="fe9b6-205">When a Blazor project is built, all Razor component and code files are compiled into a single assembly.</span></span> <span data-ttu-id="fe9b6-206">Contrairement aux projets ASP.NET Web Forms, éblouissant ne prend pas en charge la compilation du runtime de la logique d’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="fe9b6-206">Unlike ASP.NET Web Forms projects, Blazor doesn't support runtime compilation of the UI logic.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="fe9b6-207">Exécuter l'application</span><span class="sxs-lookup"><span data-stu-id="fe9b6-207">Run the app</span></span>

<span data-ttu-id="fe9b6-208">Pour exécuter l’application de serveur éblouissante, appuyez sur `F5` dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="fe9b6-208">To run the Blazor Server app, press `F5` in Visual Studio.</span></span> <span data-ttu-id="fe9b6-209">Les applications éblouissantes ne prennent pas en charge la compilation au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="fe9b6-209">Blazor apps don't support runtime compilation.</span></span> <span data-ttu-id="fe9b6-210">Pour afficher les résultats des modifications du balisage du code et des composants, régénérez et redémarrez l’application avec le débogueur attaché.</span><span class="sxs-lookup"><span data-stu-id="fe9b6-210">To see the results of code and component markup changes, rebuild and restart the app with the debugger attached.</span></span> <span data-ttu-id="fe9b6-211">Si vous exécutez sans le débogueur attaché (`Ctrl+F5`), Visual Studio surveille les modifications apportées aux fichiers et redémarre l’application à mesure que des modifications sont apportées.</span><span class="sxs-lookup"><span data-stu-id="fe9b6-211">If you run without the debugger attached (`Ctrl+F5`), Visual Studio watches for file changes and restarts the app as changes are made.</span></span> <span data-ttu-id="fe9b6-212">Vous actualisez manuellement le navigateur à mesure que des modifications sont apportées.</span><span class="sxs-lookup"><span data-stu-id="fe9b6-212">You manually refresh the browser as changes are made.</span></span>

<span data-ttu-id="fe9b6-213">Pour exécuter l’application éblouissant webassembly, choisissez l’une des approches suivantes :</span><span class="sxs-lookup"><span data-stu-id="fe9b6-213">To run the Blazor WebAssembly app, choose one of the following approaches:</span></span>

- <span data-ttu-id="fe9b6-214">Exécutez le projet client directement à l’aide du serveur de développement.</span><span class="sxs-lookup"><span data-stu-id="fe9b6-214">Run the client project directly using the development server.</span></span>
- <span data-ttu-id="fe9b6-215">Exécutez le projet serveur lors de l’hébergement de l’application avec ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="fe9b6-215">Run the server project when hosting the app with ASP.NET Core.</span></span>

<span data-ttu-id="fe9b6-216">Les applications webassembly éblouissantes ne prennent pas en charge le débogage à l’aide de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="fe9b6-216">Blazor WebAssembly apps don't support debugging using Visual Studio.</span></span> <span data-ttu-id="fe9b6-217">Pour exécuter l’application, utilisez `Ctrl+F5` au lieu de `F5`.</span><span class="sxs-lookup"><span data-stu-id="fe9b6-217">To run the app, use `Ctrl+F5` instead of `F5`.</span></span> <span data-ttu-id="fe9b6-218">Au lieu de cela, vous pouvez déboguer des applications webassembly éblouissantes directement dans le navigateur.</span><span class="sxs-lookup"><span data-stu-id="fe9b6-218">You can instead debug Blazor WebAssembly apps directly in the browser.</span></span> <span data-ttu-id="fe9b6-219">Pour plus d’informations, consultez [Déboguer ASP.net Core éblouissant](/aspnet/core/blazor/debug) .</span><span class="sxs-lookup"><span data-stu-id="fe9b6-219">See [Debug ASP.NET Core Blazor](/aspnet/core/blazor/debug) for details.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="fe9b6-220">[Précédent](hosting-models.md)
>[Suivant](app-startup.md)</span><span class="sxs-lookup"><span data-stu-id="fe9b6-220">[Previous](hosting-models.md)
[Next](app-startup.md)</span></span>
