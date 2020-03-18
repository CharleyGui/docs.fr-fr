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
# <a name="project-structure-for-blazor-apps"></a>Structure de projet pour les applications Blazor

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Malgré leurs différences importantes de structure de projet, ASP.NET Web Forms et Blazor partagent de nombreux concepts similaires. Ici, nous allons examiner la structure d’un projet Blazor et le comparer à un projet ASP.NET Web Forms.

Pour créer votre première application Blazor, suivez les instructions dans le [Blazor se lancer étapes](/aspnet/core/blazor/get-started). Vous pouvez suivre les instructions pour créer une application Blazor Server ou une application Blazor WebAssembly hébergée dans ASP.NET Core. À l’exception de la logique spécifique au modèle d’hébergement, la plupart du code des deux projets est le même.

## <a name="project-file"></a>Fichier projet

Les applications Blazor Server sont des projets .NET Core. Le fichier de projet pour l’application Blazor Server est à peu près aussi simple qu’il peut l’obtenir :

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>netcoreapp3.0</TargetFramework>
  </PropertyGroup>

</Project>
```

Le fichier de projet d’une application Blazor WebAssembly semble légèrement plus impliqué (les numéros de version exact peuvent varier) :

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

Blazor WebAssembly projette cible .NET Standard au lieu de .NET Core parce qu’ils s’exécutent dans le navigateur sur un WebAssembly-based .NET runtime. Vous ne pouvez pas installer .NET dans un navigateur web comme vous pouvez sur un serveur ou une machine de développeur. Par conséquent, le projet fait référence au cadre Blazor à l’aide de références individuelles.

En comparaison, un projet par défaut ASP.NET Web Forms comprend près de 300 lignes de XML dans son fichier *.csproj,* dont la plupart sont explicitement la liste des différents fichiers de code et de contenu dans le projet. Bon nombre des simplifications dans les projets .NET Core- et .NET Standard-based `Microsoft.NET.Sdk.Web` proviennent des cibles par défaut et les propriétés importées par référence à la SDK, souvent appelé simplement le Web SDK. Le Web SDK comprend des wildcards et d’autres commodités qui simplifient l’inclusion des fichiers de code et de contenu dans le projet. Vous n’avez pas besoin d’énumérer explicitement les fichiers. Lors du ciblage .NET Core, le Web SDK ajoute également des références-cadres à la fois le base .NET et ASP.NET cadres communs core. Les cadres sont visibles à partir du nœud**Des cadres** **de dépendance** > dans la fenêtre **Solution Explorer.** Les cadres partagés sont des collections d’assemblages qui ont été installés sur la machine lors de l’installation .NET Core.

Bien qu’elles soient prises en charge, les références d’assemblage individuels sont moins courantes dans les projets .NET Core. La plupart des dépendances de projet sont traitées comme des références de paquet NuGet. Vous n’avez qu’à faire référence aux dépendances de paquets de haut niveau dans les projets .NET Core. Les dépendances transitoires sont incluses automatiquement. Au lieu d’utiliser le fichier *packages.config* que l’on trouve couramment dans ASP.NET les `<PackageReference>` projets Web Forms pour les paquets de référence, des références de paquets sont ajoutées au fichier de projet à l’aide de l’élément.

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="12.0.2" />
</ItemGroup>
```

## <a name="entry-point"></a>Point d’entrée

Le point d’entrée de l’application Blazor Server est défini dans le fichier *Program.cs,* comme vous le verriez dans une application Console. Lorsque l’application s’exécute, elle crée et exécute une instance d’hôte Web en utilisant des défauts spécifiques aux applications Web. L’hébergeur gère le cycle de vie de l’application Blazor Server et met en place des services au niveau de l’hôte. Des exemples de ces services sont la configuration, l’enregistrement, l’injection de dépendance et le serveur HTTP. Ce code est principalement boilerplate et est souvent laissé inchangé.

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

Les applications Blazor WebAssembly définissent également un point d’entrée dans *Program.cs*. Le code semble légèrement différent. Le code est similaire en ce qu’il configure l’hôte de l’application pour fournir les mêmes services au niveau de l’hôte à l’application. L’hébergeur d’applications WebAssembly n’a cependant pas configuré un serveur HTTP parce qu’il s’exécute directement dans le navigateur.

Les applications Blazor ont une `Startup` classe au lieu d’un fichier *Global.asax* pour définir la logique de démarrage de l’application. La `Startup` classe est utilisée pour configurer l’application et tous les services spécifiques à l’application. Dans l’application Blazor `Startup` Server, la classe est utilisée pour configurer le point de terminaison de la connexion en temps réel utilisée par Blazor entre les navigateurs clients et le serveur. Dans l’application WebAssembly De `Startup` Blazor, la classe définit les composants racinaires de l’application et où ils doivent être rendus. Nous allons jeter un regard `Startup` plus approfondi sur la classe dans la section [de démarrage App.](./app-startup.md)

## <a name="static-files"></a>Fichiers statiques

Contrairement aux projets ASP.NET Web Forms, tous les fichiers d’un projet Blazor ne peuvent pas être demandés sous forme de fichiers statiques. Seuls les fichiers du dossier *wwwroot* sont adressables au Web. Ce dossier est référé à la « racine web » de l’application. Tout ce qui est en dehors de la racine web de l’application *n’est pas* accessible au Web. Cette configuration fournit un niveau de sécurité supplémentaire qui empêche l’exposition accidentelle de fichiers de projet sur le web.

## <a name="configuration"></a>Configuration

La configuration dans ASP.NET applications Web Forms est généralement gérée à l’aide d’un ou de plusieurs fichiers *web.config.* Les applications Blazor n’ont généralement pas de fichiers *web.config.* S’ils le font, le fichier n’est utilisé que pour configurer des paramètres spécifiques à l’IIS lorsqu’il est hébergé sur IIS. Au lieu de cela, les applications Blazor Server utilisent les abstractions de configuration ASP.NET Core (les applications Blazor WebAssembly ne prennent pas actuellement en charge les mêmes abstractions de configuration, mais cela peut être une fonctionnalité ajoutée à l’avenir). Par exemple, l’application par défaut Blazor Server stocke certains paramètres dans *appsettings.json*.

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

Nous en apprendrons davantage sur la configuration dans ASP.NET projets de base dans la section [Configuration.](./config.md)

## <a name="razor-components"></a>Composants de rasoir

La plupart des fichiers dans les projets Blazor sont des fichiers *.razor.* Razor est un langage de templating basé sur HTML et C qui est utilisé pour générer dynamiquement l’interface utilisateur web. Les fichiers *.razor* définissent les composants qui composent l’interface utilisateur de l’application. Pour la plupart, les composants sont identiques pour les applications Blazor Server et Blazor WebAssembly. Les composants de Blazor sont analogues aux contrôles des utilisateurs dans ASP.NET formulaires Web.

Chaque fichier de composants Razor est compilé dans une classe .NET lorsque le projet est construit. La classe générée capture l’état du composant, rendant la logique, les méthodes de cycle de vie, les gestionnaires d’événements, et d’autres logiques. Nous examinerons la création de composants dans les [composants réutilisables de l’interface utilisateur du bâtiment avec](./components.md) la section Blazor.

Les *fichiers _Imports.razor* ne sont pas des fichiers de composants Razor. Au lieu de cela, ils définissent un ensemble de directives Razor à importer dans d’autres fichiers *.razor* dans le même dossier et dans ses sous-plis. Par exemple, un fichier *_Imports.razor* est un `using` moyen conventionnel d’ajouter des instructions pour les espaces de nom couramment utilisés :

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

## <a name="pages"></a>Pages

Où sont les pages des applications Blazor ? Blazor ne définit pas une extension de fichier séparée pour les pages adressables, comme les fichiers *.aspx* dans ASP.NET applications Web Forms. Au lieu de cela, les pages sont définies en assignant des itinéraires aux composants. Un itinéraire est généralement `@page` attribué à l’aide de la directive Razor. Par exemple, `Counter` le composant rédigé dans le fichier *Pages/Counter.razor* définit l’itinéraire suivant :

```razor
@page "/counter"
```

Routing à Blazor est géré côté client, pas sur le serveur. Pendant que l’utilisateur navigue dans le navigateur, Blazor intercepte la navigation, puis rend le composant avec l’itinéraire correspondant.

Les itinéraires des composants ne sont pas actuellement déduits par l’emplacement du fichier du composant comme ils le sont avec des pages *.aspx.* Cette fonctionnalité peut être ajoutée à l’avenir. Chaque itinéraire doit être spécifié explicitement sur le composant. Le stockage des composants routables dans un dossier *Pages* n’a pas de signification particulière et est purement une convention.

Nous examinerons plus en détail l’itinéraire dans Blazor dans les Pages, le routage et la section [mises en page.](./pages-routing-layouts.md)

## <a name="layout"></a>Disposition

Dans ASP.NET applications Web Forms, la mise en page commune est gérée à l’aide de pages maîtresses (*Site.Master*). Dans les applications Blazor, la mise en page est gérée à l’aide de composants de mise en page *(Shared/MainLayout.razor*). Les composants de mise en page seront discutés plus en détail dans [la section Page, routage et mise en page.](./pages-routing-layouts.md)

## <a name="bootstrap-blazor"></a>Bootstrap Blazor

Pour bootstrap Blazor, l’application doit:

- Spécifier où sur la page le composant racine (*App.Razor*) doit être rendu.
- Ajoutez le script-cadre Blazor correspondant.

Dans l’application Blazor Server, la page d’accueil du composant racine est définie dans le fichier *_Host.cshtml.* Ce fichier définit une page Razor, pas un composant. Razor Pages utilise la syntaxe Razor pour définir une page adressable au serveur, tout comme une page *.aspx.* La `Html.RenderComponentAsync<TComponent>(RenderMode)` méthode est utilisée pour définir où un composant au niveau des racines doit être rendu. L’option `RenderMode` indique la façon dont le composant doit être rendu. Le tableau suivant décrit `RenderMode` les options prises en charge.

|Option                        |Description       |
|------------------------------|------------------|
|`RenderMode.Server`           |Rendu interactif une fois qu’une connexion avec le navigateur est établie|
|`RenderMode.ServerPrerendered`|D’abord préditulé puis rendu de manière interactive|
|`RenderMode.Static`           |Rendu comme contenu statique|

La référence de script à *_framework/blazor.server.js* établit la connexion en temps réel avec le serveur, puis traite de toutes les interactions utilisateur et mises à jour de l’interface utilisateur.

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

Dans l’application Blazor WebAssembly, la page d’accueil est un fichier HTML statique simple sous *wwwroot/index.html*. L’élément `<app>` est utilisé pour indiquer où le composant racine doit être rendu.

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

Le composant spécifique à rendre est configuré dans la méthode de `Startup.Configure` l’application avec un sélecteur CSS correspondant indiquant où le composant doit être rendu.

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

## <a name="build-output"></a>Sortie de la génération

Lorsqu’un projet Blazor est construit, tous les fichiers de composants et de codes Razor sont compilés en un seul assemblage. Contrairement aux projets ASP.NET Web Forms, Blazor ne prend pas en charge la compilation en temps d’exécution de la logique de l’interface utilisateur.

## <a name="run-the-app"></a>Exécuter l’application

Pour exécuter l’application Blazor Server, appuyez `F5` sur Visual Studio. Les applications Blazor ne prennent pas en charge la compilation en temps d’exécution. Pour voir les résultats des modifications de balisage de code et de composant, reconstruisez et redémarrez l’application avec le débbugger ci-joint. Si vous exécutez sans le`Ctrl+F5`débbugger ci-joint (), Visual Studio veille pour les modifications de fichiers et redémarre l’application au fur et à mesure que des modifications sont apportées. Vous actualisez manuellement le navigateur au fur et à mesure que des modifications sont apportées.

Pour exécuter l’application Blazor WebAssembly, choisissez l’une des approches suivantes :

- Exécutez le projet client directement à l’aide du serveur de développement.
- Exécutez le projet serveur lors de l’hébergement de l’application avec ASP.NET Core.

Les applications Blazor WebAssembly ne prennent pas en charge le débogage à l’aide de Visual Studio. Pour exécuter l’application, utilisez `Ctrl+F5` au lieu de `F5`. Vous pouvez plutôt débomber Blazor WebAssembly applications directement dans le navigateur. Voir [Debug ASP.NET Core Blazor](/aspnet/core/blazor/debug) pour plus de détails.

>[!div class="step-by-step"]
>[Suivant précédent](hosting-models.md)
>[Next](app-startup.md)
