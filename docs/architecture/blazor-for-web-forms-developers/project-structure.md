---
title: Structure de projet pour les applications Blazor
description: Découvrez comment se comparent les structures de projets des ASP.NET des formulaires Web et des projets Blazor.
author: danroth27
ms.author: daroth
ms.date: 09/11/2019
ms.openlocfilehash: 2c383e86ff22f5a3460476998992b66e9417cc11
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79401577"
---
# <a name="project-structure-for-blazor-apps"></a><span data-ttu-id="0de56-103">Structure de projet pour les applications Blazor</span><span class="sxs-lookup"><span data-stu-id="0de56-103">Project structure for Blazor apps</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="0de56-104">Malgré leurs différences importantes de structure de projet, ASP.NET Web Forms et Blazor partagent de nombreux concepts similaires.</span><span class="sxs-lookup"><span data-stu-id="0de56-104">Despite their significant project structure differences, ASP.NET Web Forms and Blazor share many similar concepts.</span></span> <span data-ttu-id="0de56-105">Ici, nous allons examiner la structure d’un projet Blazor et le comparer à un projet ASP.NET Web Forms.</span><span class="sxs-lookup"><span data-stu-id="0de56-105">Here, we'll look at the structure of a Blazor project and compare it to an ASP.NET Web Forms project.</span></span>

<span data-ttu-id="0de56-106">Pour créer votre première application Blazor, suivez les instructions dans le [Blazor se lancer étapes](/aspnet/core/blazor/get-started).</span><span class="sxs-lookup"><span data-stu-id="0de56-106">To create your first Blazor app, follow the instructions in the [Blazor getting started steps](/aspnet/core/blazor/get-started).</span></span> <span data-ttu-id="0de56-107">Vous pouvez suivre les instructions pour créer une application Blazor Server ou une application Blazor WebAssembly hébergée dans ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="0de56-107">You can follow the instructions to create either a Blazor Server app or a Blazor WebAssembly app hosted in ASP.NET Core.</span></span> <span data-ttu-id="0de56-108">À l’exception de la logique spécifique au modèle d’hébergement, la plupart du code des deux projets est le même.</span><span class="sxs-lookup"><span data-stu-id="0de56-108">Except for the hosting model-specific logic, most of the code in both projects is the same.</span></span>

## <a name="project-file"></a><span data-ttu-id="0de56-109">Fichier projet</span><span class="sxs-lookup"><span data-stu-id="0de56-109">Project file</span></span>

<span data-ttu-id="0de56-110">Les applications Blazor Server sont des projets .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0de56-110">Blazor Server apps are .NET Core projects.</span></span> <span data-ttu-id="0de56-111">Le fichier de projet pour l’application Blazor Server est à peu près aussi simple qu’il peut l’obtenir :</span><span class="sxs-lookup"><span data-stu-id="0de56-111">The project file for the Blazor Server app is about as simple as it can get:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>netcoreapp3.0</TargetFramework>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="0de56-112">Le fichier de projet d’une application Blazor WebAssembly semble légèrement plus impliqué (les numéros de version exact peuvent varier) :</span><span class="sxs-lookup"><span data-stu-id="0de56-112">The project file for a Blazor WebAssembly app looks slightly more involved (exact version numbers may vary):</span></span>

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

<span data-ttu-id="0de56-113">Blazor WebAssembly projette cible .NET Standard au lieu de .NET Core parce qu’ils s’exécutent dans le navigateur sur un WebAssembly-based .NET runtime.</span><span class="sxs-lookup"><span data-stu-id="0de56-113">Blazor WebAssembly projects target .NET Standard instead of .NET Core because they run in the browser on a WebAssembly-based .NET runtime.</span></span> <span data-ttu-id="0de56-114">Vous ne pouvez pas installer .NET dans un navigateur web comme vous pouvez sur un serveur ou une machine de développeur.</span><span class="sxs-lookup"><span data-stu-id="0de56-114">You can't install .NET into a web browser like you can on a server or developer machine.</span></span> <span data-ttu-id="0de56-115">Par conséquent, le projet fait référence au cadre Blazor à l’aide de références individuelles.</span><span class="sxs-lookup"><span data-stu-id="0de56-115">Consequently, the project references the Blazor framework using individual package references.</span></span>

<span data-ttu-id="0de56-116">En comparaison, un projet par défaut ASP.NET Web Forms comprend près de 300 lignes de XML dans son fichier *.csproj,* dont la plupart sont explicitement la liste des différents fichiers de code et de contenu dans le projet.</span><span class="sxs-lookup"><span data-stu-id="0de56-116">By comparison, a default ASP.NET Web Forms project includes almost 300 lines of XML in its *.csproj* file, most of which is explicitly listing the various code and content files in the project.</span></span> <span data-ttu-id="0de56-117">Bon nombre des simplifications dans les projets .NET Core- et .NET Standard-based `Microsoft.NET.Sdk.Web` proviennent des cibles par défaut et les propriétés importées par référence à la SDK, souvent appelé simplement le Web SDK.</span><span class="sxs-lookup"><span data-stu-id="0de56-117">Many of the simplifications in the .NET Core- and .NET Standard-based projects come from the default targets and properties imported by referencing the `Microsoft.NET.Sdk.Web` SDK, often referred to as simply the Web SDK.</span></span> <span data-ttu-id="0de56-118">Le Web SDK comprend des wildcards et d’autres commodités qui simplifient l’inclusion des fichiers de code et de contenu dans le projet.</span><span class="sxs-lookup"><span data-stu-id="0de56-118">The Web SDK includes wildcards and other conveniences that simplify inclusion of code and content files in the project.</span></span> <span data-ttu-id="0de56-119">Vous n’avez pas besoin d’énumérer explicitement les fichiers.</span><span class="sxs-lookup"><span data-stu-id="0de56-119">You don't need to list the files explicitly.</span></span> <span data-ttu-id="0de56-120">Lors du ciblage .NET Core, le Web SDK ajoute également des références-cadres à la fois le base .NET et ASP.NET cadres communs core.</span><span class="sxs-lookup"><span data-stu-id="0de56-120">When targeting .NET Core, the Web SDK also adds framework references to both the .NET Core and ASP.NET Core shared frameworks.</span></span> <span data-ttu-id="0de56-121">Les cadres sont visibles à partir du nœud**Des cadres** **de dépendance** > dans la fenêtre **Solution Explorer.**</span><span class="sxs-lookup"><span data-stu-id="0de56-121">The frameworks are visible from the **Dependencies** > **Frameworks** node in the **Solution Explorer** window.</span></span> <span data-ttu-id="0de56-122">Les cadres partagés sont des collections d’assemblages qui ont été installés sur la machine lors de l’installation .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0de56-122">The shared frameworks are collections of assemblies that were installed on the machine when installing .NET Core.</span></span>

<span data-ttu-id="0de56-123">Bien qu’elles soient prises en charge, les références d’assemblage individuels sont moins courantes dans les projets .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0de56-123">Although they're supported, individual assembly references are less common in .NET Core projects.</span></span> <span data-ttu-id="0de56-124">La plupart des dépendances de projet sont traitées comme des références de paquet NuGet.</span><span class="sxs-lookup"><span data-stu-id="0de56-124">Most project dependencies are handled as NuGet package references.</span></span> <span data-ttu-id="0de56-125">Vous n’avez qu’à faire référence aux dépendances de paquets de haut niveau dans les projets .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0de56-125">You only need to reference top-level package dependencies in .NET Core projects.</span></span> <span data-ttu-id="0de56-126">Les dépendances transitoires sont incluses automatiquement.</span><span class="sxs-lookup"><span data-stu-id="0de56-126">Transitive dependencies are included automatically.</span></span> <span data-ttu-id="0de56-127">Au lieu d’utiliser le fichier *packages.config* que l’on trouve couramment dans ASP.NET les `<PackageReference>` projets Web Forms pour les paquets de référence, des références de paquets sont ajoutées au fichier de projet à l’aide de l’élément.</span><span class="sxs-lookup"><span data-stu-id="0de56-127">Instead of using the *packages.config* file commonly found in ASP.NET Web Forms projects to reference packages, package references are added to the project file using the `<PackageReference>` element.</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="12.0.2" />
</ItemGroup>
```

## <a name="entry-point"></a><span data-ttu-id="0de56-128">Point d’entrée</span><span class="sxs-lookup"><span data-stu-id="0de56-128">Entry point</span></span>

<span data-ttu-id="0de56-129">Le point d’entrée de l’application Blazor Server est défini dans le fichier *Program.cs,* comme vous le verriez dans une application Console.</span><span class="sxs-lookup"><span data-stu-id="0de56-129">The Blazor Server app's entry point is defined in the *Program.cs* file, as you would see in a Console app.</span></span> <span data-ttu-id="0de56-130">Lorsque l’application s’exécute, elle crée et exécute une instance d’hôte Web en utilisant des défauts spécifiques aux applications Web.</span><span class="sxs-lookup"><span data-stu-id="0de56-130">When the app executes, it creates and runs a web host instance using defaults specific to web apps.</span></span> <span data-ttu-id="0de56-131">L’hébergeur gère le cycle de vie de l’application Blazor Server et met en place des services au niveau de l’hôte.</span><span class="sxs-lookup"><span data-stu-id="0de56-131">The web host manages the Blazor Server app's lifecycle and sets up host-level services.</span></span> <span data-ttu-id="0de56-132">Des exemples de ces services sont la configuration, l’enregistrement, l’injection de dépendance et le serveur HTTP.</span><span class="sxs-lookup"><span data-stu-id="0de56-132">Examples of such services are configuration, logging, dependency injection, and the HTTP server.</span></span> <span data-ttu-id="0de56-133">Ce code est principalement boilerplate et est souvent laissé inchangé.</span><span class="sxs-lookup"><span data-stu-id="0de56-133">This code is mostly boilerplate and is often left unchanged.</span></span>

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

<span data-ttu-id="0de56-134">Les applications Blazor WebAssembly définissent également un point d’entrée dans *Program.cs*.</span><span class="sxs-lookup"><span data-stu-id="0de56-134">Blazor WebAssembly apps also define an entry point in *Program.cs*.</span></span> <span data-ttu-id="0de56-135">Le code semble légèrement différent.</span><span class="sxs-lookup"><span data-stu-id="0de56-135">The code looks slightly different.</span></span> <span data-ttu-id="0de56-136">Le code est similaire en ce qu’il configure l’hôte de l’application pour fournir les mêmes services au niveau de l’hôte à l’application.</span><span class="sxs-lookup"><span data-stu-id="0de56-136">The code is similar in that it's setting up the app host to provide the same host-level services to the app.</span></span> <span data-ttu-id="0de56-137">L’hébergeur d’applications WebAssembly n’a cependant pas configuré un serveur HTTP parce qu’il s’exécute directement dans le navigateur.</span><span class="sxs-lookup"><span data-stu-id="0de56-137">The WebAssembly app host doesn't, however, set up an HTTP server because it executes directly in the browser.</span></span>

<span data-ttu-id="0de56-138">Les applications Blazor ont une `Startup` classe au lieu d’un fichier *Global.asax* pour définir la logique de démarrage de l’application.</span><span class="sxs-lookup"><span data-stu-id="0de56-138">Blazor apps have a `Startup` class instead of a *Global.asax* file to define the startup logic for the app.</span></span> <span data-ttu-id="0de56-139">La `Startup` classe est utilisée pour configurer l’application et tous les services spécifiques à l’application.</span><span class="sxs-lookup"><span data-stu-id="0de56-139">The `Startup` class is used to configure the app and any app-specific services.</span></span> <span data-ttu-id="0de56-140">Dans l’application Blazor `Startup` Server, la classe est utilisée pour configurer le point de terminaison de la connexion en temps réel utilisée par Blazor entre les navigateurs clients et le serveur.</span><span class="sxs-lookup"><span data-stu-id="0de56-140">In the Blazor Server app, the `Startup` class is used to set up the endpoint for the real-time connection used by Blazor between the client browsers and the server.</span></span> <span data-ttu-id="0de56-141">Dans l’application WebAssembly De `Startup` Blazor, la classe définit les composants racinaires de l’application et où ils doivent être rendus.</span><span class="sxs-lookup"><span data-stu-id="0de56-141">In the Blazor WebAssembly app, the `Startup` class defines the root components for the app and where they should be rendered.</span></span> <span data-ttu-id="0de56-142">Nous allons jeter un regard `Startup` plus approfondi sur la classe dans la section [de démarrage App.](./app-startup.md)</span><span class="sxs-lookup"><span data-stu-id="0de56-142">We'll take a deeper look at the `Startup` class in the [App startup](./app-startup.md) section.</span></span>

## <a name="static-files"></a><span data-ttu-id="0de56-143">Fichiers statiques</span><span class="sxs-lookup"><span data-stu-id="0de56-143">Static files</span></span>

<span data-ttu-id="0de56-144">Contrairement aux projets ASP.NET Web Forms, tous les fichiers d’un projet Blazor ne peuvent pas être demandés sous forme de fichiers statiques.</span><span class="sxs-lookup"><span data-stu-id="0de56-144">Unlike ASP.NET Web Forms projects, not all files in a Blazor project can be requested as static files.</span></span> <span data-ttu-id="0de56-145">Seuls les fichiers du dossier *wwwroot* sont adressables au Web.</span><span class="sxs-lookup"><span data-stu-id="0de56-145">Only the files in the *wwwroot* folder are web-addressable.</span></span> <span data-ttu-id="0de56-146">Ce dossier est référé à la « racine web » de l’application.</span><span class="sxs-lookup"><span data-stu-id="0de56-146">This folder is referred to the app's "web root".</span></span> <span data-ttu-id="0de56-147">Tout ce qui est en dehors de la racine web de l’application *n’est pas* accessible au Web.</span><span class="sxs-lookup"><span data-stu-id="0de56-147">Anything outside of the app's web root *isn't* web-addressable.</span></span> <span data-ttu-id="0de56-148">Cette configuration fournit un niveau de sécurité supplémentaire qui empêche l’exposition accidentelle de fichiers de projet sur le web.</span><span class="sxs-lookup"><span data-stu-id="0de56-148">This setup provides an additional level of security that prevents accidental exposing of project files over the web.</span></span>

## <a name="configuration"></a><span data-ttu-id="0de56-149">Configuration</span><span class="sxs-lookup"><span data-stu-id="0de56-149">Configuration</span></span>

<span data-ttu-id="0de56-150">La configuration dans ASP.NET applications Web Forms est généralement gérée à l’aide d’un ou de plusieurs fichiers *web.config.*</span><span class="sxs-lookup"><span data-stu-id="0de56-150">Configuration in ASP.NET Web Forms apps is typically handled using one or more *web.config* files.</span></span> <span data-ttu-id="0de56-151">Les applications Blazor n’ont généralement pas de fichiers *web.config.*</span><span class="sxs-lookup"><span data-stu-id="0de56-151">Blazor apps don't typically have *web.config* files.</span></span> <span data-ttu-id="0de56-152">S’ils le font, le fichier n’est utilisé que pour configurer des paramètres spécifiques à l’IIS lorsqu’il est hébergé sur IIS.</span><span class="sxs-lookup"><span data-stu-id="0de56-152">If they do, the file is only used to configure IIS-specific settings when hosted on IIS.</span></span> <span data-ttu-id="0de56-153">Au lieu de cela, les applications Blazor Server utilisent les abstractions de configuration ASP.NET Core (les applications Blazor WebAssembly ne prennent pas actuellement en charge les mêmes abstractions de configuration, mais cela peut être une fonctionnalité ajoutée à l’avenir).</span><span class="sxs-lookup"><span data-stu-id="0de56-153">Instead, Blazor Server apps use the ASP.NET Core configuration abstractions (Blazor WebAssembly apps don't currently support the same configuration abstractions, but that may be a feature added in the future).</span></span> <span data-ttu-id="0de56-154">Par exemple, l’application par défaut Blazor Server stocke certains paramètres dans *appsettings.json*.</span><span class="sxs-lookup"><span data-stu-id="0de56-154">For example, the default Blazor Server app stores some settings in *appsettings.json*.</span></span>

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

<span data-ttu-id="0de56-155">Nous en apprendrons davantage sur la configuration dans ASP.NET projets de base dans la section [Configuration.](./config.md)</span><span class="sxs-lookup"><span data-stu-id="0de56-155">We'll learn more about configuration in ASP.NET Core projects in the [Configuration](./config.md) section.</span></span>

## <a name="razor-components"></a><span data-ttu-id="0de56-156">Composants de rasoir</span><span class="sxs-lookup"><span data-stu-id="0de56-156">Razor components</span></span>

<span data-ttu-id="0de56-157">La plupart des fichiers dans les projets Blazor sont des fichiers *.razor.*</span><span class="sxs-lookup"><span data-stu-id="0de56-157">Most files in Blazor projects are *.razor* files.</span></span> <span data-ttu-id="0de56-158">Razor est un langage de templating basé sur HTML et C qui est utilisé pour générer dynamiquement l’interface utilisateur web.</span><span class="sxs-lookup"><span data-stu-id="0de56-158">Razor is a templating language based on HTML and C# that is used to dynamically generate web UI.</span></span> <span data-ttu-id="0de56-159">Les fichiers *.razor* définissent les composants qui composent l’interface utilisateur de l’application.</span><span class="sxs-lookup"><span data-stu-id="0de56-159">The *.razor* files define components that make up the UI of the app.</span></span> <span data-ttu-id="0de56-160">Pour la plupart, les composants sont identiques pour les applications Blazor Server et Blazor WebAssembly.</span><span class="sxs-lookup"><span data-stu-id="0de56-160">For the most part, the components are identical for both the Blazor Server and Blazor WebAssembly apps.</span></span> <span data-ttu-id="0de56-161">Les composants de Blazor sont analogues aux contrôles des utilisateurs dans ASP.NET formulaires Web.</span><span class="sxs-lookup"><span data-stu-id="0de56-161">Components in Blazor are analogous to user controls in ASP.NET Web Forms.</span></span>

<span data-ttu-id="0de56-162">Chaque fichier de composants Razor est compilé dans une classe .NET lorsque le projet est construit.</span><span class="sxs-lookup"><span data-stu-id="0de56-162">Each Razor component file is compiled into a .NET class when the project is built.</span></span> <span data-ttu-id="0de56-163">La classe générée capture l’état du composant, rendant la logique, les méthodes de cycle de vie, les gestionnaires d’événements, et d’autres logiques.</span><span class="sxs-lookup"><span data-stu-id="0de56-163">The generated class captures the component's state, rendering logic, lifecycle methods, event handlers, and other logic.</span></span> <span data-ttu-id="0de56-164">Nous examinerons la création de composants dans les [composants réutilisables de l’interface utilisateur du bâtiment avec](./components.md) la section Blazor.</span><span class="sxs-lookup"><span data-stu-id="0de56-164">We'll look at authoring components in the [Building reusable UI components with Blazor](./components.md) section.</span></span>

<span data-ttu-id="0de56-165">Les *fichiers _Imports.razor* ne sont pas des fichiers de composants Razor.</span><span class="sxs-lookup"><span data-stu-id="0de56-165">The *_Imports.razor* files aren't Razor component files.</span></span> <span data-ttu-id="0de56-166">Au lieu de cela, ils définissent un ensemble de directives Razor à importer dans d’autres fichiers *.razor* dans le même dossier et dans ses sous-plis.</span><span class="sxs-lookup"><span data-stu-id="0de56-166">Instead, they define a set of Razor directives to import into other *.razor* files within the same folder and in its subfolders.</span></span> <span data-ttu-id="0de56-167">Par exemple, un fichier *_Imports.razor* est un `using` moyen conventionnel d’ajouter des instructions pour les espaces de nom couramment utilisés :</span><span class="sxs-lookup"><span data-stu-id="0de56-167">For example, a *_Imports.razor* file is a conventional way to add `using` statements for commonly used namespaces:</span></span>

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

## <a name="pages"></a><span data-ttu-id="0de56-168">Pages</span><span class="sxs-lookup"><span data-stu-id="0de56-168">Pages</span></span>

<span data-ttu-id="0de56-169">Où sont les pages des applications Blazor ?</span><span class="sxs-lookup"><span data-stu-id="0de56-169">Where are the pages in the Blazor apps?</span></span> <span data-ttu-id="0de56-170">Blazor ne définit pas une extension de fichier séparée pour les pages adressables, comme les fichiers *.aspx* dans ASP.NET applications Web Forms.</span><span class="sxs-lookup"><span data-stu-id="0de56-170">Blazor doesn't define a separate file extension for addressable pages, like the *.aspx* files in ASP.NET Web Forms apps.</span></span> <span data-ttu-id="0de56-171">Au lieu de cela, les pages sont définies en assignant des itinéraires aux composants.</span><span class="sxs-lookup"><span data-stu-id="0de56-171">Instead, pages are defined by assigning routes to components.</span></span> <span data-ttu-id="0de56-172">Un itinéraire est généralement `@page` attribué à l’aide de la directive Razor.</span><span class="sxs-lookup"><span data-stu-id="0de56-172">A route is typically assigned using the `@page` Razor directive.</span></span> <span data-ttu-id="0de56-173">Par exemple, `Counter` le composant rédigé dans le fichier *Pages/Counter.razor* définit l’itinéraire suivant :</span><span class="sxs-lookup"><span data-stu-id="0de56-173">For example, the `Counter` component authored in the *Pages/Counter.razor* file defines the following route:</span></span>

```razor
@page "/counter"
```

<span data-ttu-id="0de56-174">Routing à Blazor est géré côté client, pas sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="0de56-174">Routing in Blazor is handled client-side, not on the server.</span></span> <span data-ttu-id="0de56-175">Pendant que l’utilisateur navigue dans le navigateur, Blazor intercepte la navigation, puis rend le composant avec l’itinéraire correspondant.</span><span class="sxs-lookup"><span data-stu-id="0de56-175">As the user navigates in the browser, Blazor intercepts the navigation and then renders the component with the matching route.</span></span>

<span data-ttu-id="0de56-176">Les itinéraires des composants ne sont pas actuellement déduits par l’emplacement du fichier du composant comme ils le sont avec des pages *.aspx.*</span><span class="sxs-lookup"><span data-stu-id="0de56-176">The component routes aren't currently inferred by the component's file location like they are with *.aspx* pages.</span></span> <span data-ttu-id="0de56-177">Cette fonctionnalité peut être ajoutée à l’avenir.</span><span class="sxs-lookup"><span data-stu-id="0de56-177">This feature may be added in the future.</span></span> <span data-ttu-id="0de56-178">Chaque itinéraire doit être spécifié explicitement sur le composant.</span><span class="sxs-lookup"><span data-stu-id="0de56-178">Each route must be specified explicitly on the component.</span></span> <span data-ttu-id="0de56-179">Le stockage des composants routables dans un dossier *Pages* n’a pas de signification particulière et est purement une convention.</span><span class="sxs-lookup"><span data-stu-id="0de56-179">Storing routable components in a *Pages* folder has no special meaning and is purely a convention.</span></span>

<span data-ttu-id="0de56-180">Nous examinerons plus en détail l’itinéraire dans Blazor dans les Pages, le routage et la section [mises en page.](./pages-routing-layouts.md)</span><span class="sxs-lookup"><span data-stu-id="0de56-180">We'll look in greater detail at routing in Blazor in the [Pages, routing, and layouts](./pages-routing-layouts.md) section.</span></span>

## <a name="layout"></a><span data-ttu-id="0de56-181">Disposition</span><span class="sxs-lookup"><span data-stu-id="0de56-181">Layout</span></span>

<span data-ttu-id="0de56-182">Dans ASP.NET applications Web Forms, la mise en page commune est gérée à l’aide de pages maîtresses (*Site.Master*).</span><span class="sxs-lookup"><span data-stu-id="0de56-182">In ASP.NET Web Forms apps, common page layout is handled using master pages (*Site.Master*).</span></span> <span data-ttu-id="0de56-183">Dans les applications Blazor, la mise en page est gérée à l’aide de composants de mise en page *(Shared/MainLayout.razor*).</span><span class="sxs-lookup"><span data-stu-id="0de56-183">In Blazor apps, page layout is handled using layout components (*Shared/MainLayout.razor*).</span></span> <span data-ttu-id="0de56-184">Les composants de mise en page seront discutés plus en détail dans [la section Page, routage et mise en page.](./pages-routing-layouts.md)</span><span class="sxs-lookup"><span data-stu-id="0de56-184">Layout components will be discussed in more detail in [Page, routing, and layouts](./pages-routing-layouts.md) section.</span></span>

## <a name="bootstrap-blazor"></a><span data-ttu-id="0de56-185">Bootstrap Blazor</span><span class="sxs-lookup"><span data-stu-id="0de56-185">Bootstrap Blazor</span></span>

<span data-ttu-id="0de56-186">Pour bootstrap Blazor, l’application doit:</span><span class="sxs-lookup"><span data-stu-id="0de56-186">To bootstrap Blazor, the app must:</span></span>

- <span data-ttu-id="0de56-187">Spécifier où sur la page le composant racine (*App.Razor*) doit être rendu.</span><span class="sxs-lookup"><span data-stu-id="0de56-187">Specify where on the page the root component (*App.Razor*) should be rendered.</span></span>
- <span data-ttu-id="0de56-188">Ajoutez le script-cadre Blazor correspondant.</span><span class="sxs-lookup"><span data-stu-id="0de56-188">Add the corresponding Blazor framework script.</span></span>

<span data-ttu-id="0de56-189">Dans l’application Blazor Server, la page d’accueil du composant racine est définie dans le fichier *_Host.cshtml.*</span><span class="sxs-lookup"><span data-stu-id="0de56-189">In the Blazor Server app, the root component's host page is defined in the *_Host.cshtml* file.</span></span> <span data-ttu-id="0de56-190">Ce fichier définit une page Razor, pas un composant.</span><span class="sxs-lookup"><span data-stu-id="0de56-190">This file defines a Razor Page, not a component.</span></span> <span data-ttu-id="0de56-191">Razor Pages utilise la syntaxe Razor pour définir une page adressable au serveur, tout comme une page *.aspx.*</span><span class="sxs-lookup"><span data-stu-id="0de56-191">Razor Pages use Razor syntax to define a server-addressable page, very much like an *.aspx* page.</span></span> <span data-ttu-id="0de56-192">La `Html.RenderComponentAsync<TComponent>(RenderMode)` méthode est utilisée pour définir où un composant au niveau des racines doit être rendu.</span><span class="sxs-lookup"><span data-stu-id="0de56-192">The `Html.RenderComponentAsync<TComponent>(RenderMode)` method is used to define where a root-level component should be rendered.</span></span> <span data-ttu-id="0de56-193">L’option `RenderMode` indique la façon dont le composant doit être rendu.</span><span class="sxs-lookup"><span data-stu-id="0de56-193">The `RenderMode` option indicates the manner in which the component should be rendered.</span></span> <span data-ttu-id="0de56-194">Le tableau suivant décrit `RenderMode` les options prises en charge.</span><span class="sxs-lookup"><span data-stu-id="0de56-194">The following table outlines the supported `RenderMode` options.</span></span>

|<span data-ttu-id="0de56-195">Option</span><span class="sxs-lookup"><span data-stu-id="0de56-195">Option</span></span>                        |<span data-ttu-id="0de56-196">Description</span><span class="sxs-lookup"><span data-stu-id="0de56-196">Description</span></span>       |
|------------------------------|------------------|
|`RenderMode.Server`           |<span data-ttu-id="0de56-197">Rendu interactif une fois qu’une connexion avec le navigateur est établie</span><span class="sxs-lookup"><span data-stu-id="0de56-197">Rendered interactively once a connection with the browser is established</span></span>|
|`RenderMode.ServerPrerendered`|<span data-ttu-id="0de56-198">D’abord préditulé puis rendu de manière interactive</span><span class="sxs-lookup"><span data-stu-id="0de56-198">First prerendered and then rendered interactively</span></span>|
|`RenderMode.Static`           |<span data-ttu-id="0de56-199">Rendu comme contenu statique</span><span class="sxs-lookup"><span data-stu-id="0de56-199">Rendered as static content</span></span>|

<span data-ttu-id="0de56-200">La référence de script à *_framework/blazor.server.js* établit la connexion en temps réel avec le serveur, puis traite de toutes les interactions utilisateur et mises à jour de l’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="0de56-200">The script reference to *_framework/blazor.server.js* establishes the real-time connection with the server and then deals with all user interactions and UI updates.</span></span>

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

<span data-ttu-id="0de56-201">Dans l’application Blazor WebAssembly, la page d’accueil est un fichier HTML statique simple sous *wwwroot/index.html*.</span><span class="sxs-lookup"><span data-stu-id="0de56-201">In the Blazor WebAssembly app, the host page is a simple static HTML file under *wwwroot/index.html*.</span></span> <span data-ttu-id="0de56-202">L’élément `<app>` est utilisé pour indiquer où le composant racine doit être rendu.</span><span class="sxs-lookup"><span data-stu-id="0de56-202">The `<app>` element is used to indicate where the root component should be rendered.</span></span>

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

<span data-ttu-id="0de56-203">Le composant spécifique à rendre est configuré dans la méthode de `Startup.Configure` l’application avec un sélecteur CSS correspondant indiquant où le composant doit être rendu.</span><span class="sxs-lookup"><span data-stu-id="0de56-203">The specific component to render is configured in the app's `Startup.Configure` method with a corresponding CSS selector indicating where the component should be rendered.</span></span>

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

## <a name="build-output"></a><span data-ttu-id="0de56-204">Sortie de la génération</span><span class="sxs-lookup"><span data-stu-id="0de56-204">Build output</span></span>

<span data-ttu-id="0de56-205">Lorsqu’un projet Blazor est construit, tous les fichiers de composants et de codes Razor sont compilés en un seul assemblage.</span><span class="sxs-lookup"><span data-stu-id="0de56-205">When a Blazor project is built, all Razor component and code files are compiled into a single assembly.</span></span> <span data-ttu-id="0de56-206">Contrairement aux projets ASP.NET Web Forms, Blazor ne prend pas en charge la compilation en temps d’exécution de la logique de l’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="0de56-206">Unlike ASP.NET Web Forms projects, Blazor doesn't support runtime compilation of the UI logic.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="0de56-207">Exécuter l’application</span><span class="sxs-lookup"><span data-stu-id="0de56-207">Run the app</span></span>

<span data-ttu-id="0de56-208">Pour exécuter l’application Blazor Server, appuyez `F5` sur Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0de56-208">To run the Blazor Server app, press `F5` in Visual Studio.</span></span> <span data-ttu-id="0de56-209">Les applications Blazor ne prennent pas en charge la compilation en temps d’exécution.</span><span class="sxs-lookup"><span data-stu-id="0de56-209">Blazor apps don't support runtime compilation.</span></span> <span data-ttu-id="0de56-210">Pour voir les résultats des modifications de balisage de code et de composant, reconstruisez et redémarrez l’application avec le débbugger ci-joint.</span><span class="sxs-lookup"><span data-stu-id="0de56-210">To see the results of code and component markup changes, rebuild and restart the app with the debugger attached.</span></span> <span data-ttu-id="0de56-211">Si vous exécutez sans le`Ctrl+F5`débbugger ci-joint (), Visual Studio veille pour les modifications de fichiers et redémarre l’application au fur et à mesure que des modifications sont apportées.</span><span class="sxs-lookup"><span data-stu-id="0de56-211">If you run without the debugger attached (`Ctrl+F5`), Visual Studio watches for file changes and restarts the app as changes are made.</span></span> <span data-ttu-id="0de56-212">Vous actualisez manuellement le navigateur au fur et à mesure que des modifications sont apportées.</span><span class="sxs-lookup"><span data-stu-id="0de56-212">You manually refresh the browser as changes are made.</span></span>

<span data-ttu-id="0de56-213">Pour exécuter l’application Blazor WebAssembly, choisissez l’une des approches suivantes :</span><span class="sxs-lookup"><span data-stu-id="0de56-213">To run the Blazor WebAssembly app, choose one of the following approaches:</span></span>

- <span data-ttu-id="0de56-214">Exécutez le projet client directement à l’aide du serveur de développement.</span><span class="sxs-lookup"><span data-stu-id="0de56-214">Run the client project directly using the development server.</span></span>
- <span data-ttu-id="0de56-215">Exécutez le projet serveur lors de l’hébergement de l’application avec ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="0de56-215">Run the server project when hosting the app with ASP.NET Core.</span></span>

<span data-ttu-id="0de56-216">Les applications Blazor WebAssembly ne prennent pas en charge le débogage à l’aide de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0de56-216">Blazor WebAssembly apps don't support debugging using Visual Studio.</span></span> <span data-ttu-id="0de56-217">Pour exécuter l’application, utilisez `Ctrl+F5` au lieu de `F5`.</span><span class="sxs-lookup"><span data-stu-id="0de56-217">To run the app, use `Ctrl+F5` instead of `F5`.</span></span> <span data-ttu-id="0de56-218">Vous pouvez plutôt débomber Blazor WebAssembly applications directement dans le navigateur.</span><span class="sxs-lookup"><span data-stu-id="0de56-218">You can instead debug Blazor WebAssembly apps directly in the browser.</span></span> <span data-ttu-id="0de56-219">Voir [Debug ASP.NET Core Blazor](/aspnet/core/blazor/debug) pour plus de détails.</span><span class="sxs-lookup"><span data-stu-id="0de56-219">See [Debug ASP.NET Core Blazor](/aspnet/core/blazor/debug) for details.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="0de56-220">[Suivant précédent](hosting-models.md)
>[Next](app-startup.md)</span><span class="sxs-lookup"><span data-stu-id="0de56-220">[Previous](hosting-models.md)
[Next](app-startup.md)</span></span>
