---
title: Structure de projet pour les Blazor applications
description: Découvrez comment les structures de projet de ASP.NET Web Forms et des Blazor projets sont comparées.
author: danroth27
ms.author: daroth
no-loc:
- Blazor
- WebAssembly
ms.date: 11/20/2020
ms.openlocfilehash: d91430eb654ee16934408bf064803b34ca700640
ms.sourcegitcommit: 2f485e721f7f34b87856a51181b5b56624b31fd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2020
ms.locfileid: "96509804"
---
# <a name="project-structure-for-no-locblazor-apps"></a>Structure de projet pour les Blazor applications

Malgré leurs différences de structure de projet, ASP.NET Web Forms et Blazor partagent un grand nombre de concepts similaires. Ici, nous allons examiner la structure d’un Blazor projet et le comparer à un projet de Web Forms ASP.net.

Pour créer votre première Blazor application, suivez les instructions fournies dans les [ Blazor étapes de mise](/aspnet/core/blazor/get-started)en route. Vous pouvez suivre les instructions pour créer une Blazor application serveur ou une Blazor WebAssembly application hébergée dans ASP.net core. À l’exception de la logique spécifique au modèle d’hébergement, la majeure partie du code dans les deux projets est identique.

## <a name="project-file"></a>Fichier projet

Blazor Les applications serveur sont des projets .NET. Le fichier projet pour l' Blazor application serveur est à la fois aussi simple que possible :

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>net5.0</TargetFramework>
  </PropertyGroup>

</Project>
```

Le fichier projet pour une Blazor WebAssembly application semble un peu plus complexe (les numéros de version exacts peuvent varier) :

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

BlazorWebAssemblyProject targets `Microsoft.NET.Sdk.BlazorWebAssembly` au lieu du `Microsoft.NET.Sdk.Web` Kit de développement logiciel (SDK), car ils s’exécutent dans le navigateur sur un WebAssembly Runtime .net basé sur. Vous ne pouvez pas installer .NET dans un navigateur Web comme vous le pouvez sur un serveur ou un ordinateur de développement. Par conséquent, le projet fait référence Blazor à l’infrastructure à l’aide de références de package individuelles.

Par comparaison, un projet ASP.NET Web Forms par défaut comprend près de 300 lignes de code XML dans son fichier *. csproj* , dont la plupart répertorient explicitement les différents fichiers de code et de contenu du projet. Avec la version de `.NET 5` `Blazor Server` et l' `Blazor WebAssembly` application, vous pouvez facilement partager un seul Runtime unifié.

Bien qu’elles soient prises en charge, les références d’assembly individuelles sont moins fréquentes dans les projets .NET. La plupart des dépendances de projet sont gérées en tant que références de package NuGet. Il vous suffit de référencer les dépendances de package de niveau supérieur dans les projets .NET. Les dépendances transitives sont incluses automatiquement. Au lieu d’utiliser le fichier *packages.config* couramment trouvé dans les projets ASP.NET Web Forms pour référencer des packages, des références de package sont ajoutées au fichier projet à l’aide de l' `<PackageReference>` élément.

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="12.0.2" />
</ItemGroup>
```

## <a name="entry-point"></a>Point d’entrée

Le Blazor point d’entrée de l’application serveur est défini dans le fichier *Program.cs* , comme vous pouvez le voir dans une application console. Lorsque l’application s’exécute, elle crée et exécute une instance d’hôte Web à l’aide des valeurs par défaut spécifiques aux applications Web. L’hôte Web gère le Blazor cycle de vie de l’application serveur et configure les services de niveau hôte. La configuration, la journalisation, l’injection de dépendances et le serveur HTTP sont des exemples de ces services. Ce code est principalement réutilisable et reste souvent inchangé.

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

Blazorles WebAssembly applications définissent également un point d’entrée dans *Program.cs*. Le code semble légèrement différent. Le code est similaire en ce qu’il configure l’hôte d’application pour fournir les mêmes services de niveau hôte à l’application. WebAssemblyToutefois, l’hôte d’application ne configure pas un serveur http, car il s’exécute directement dans le navigateur.

Blazor les applications ont une `Startup` classe au lieu d’un fichier *global. asax* pour définir la logique de démarrage de l’application. La `Startup` classe est utilisée pour configurer l’application et tous les services spécifiques à l’application. Dans l' Blazor application serveur, la `Startup` classe est utilisée pour configurer le point de terminaison de la connexion en temps réel utilisée par Blazor entre les navigateurs clients et le serveur. Dans l' Blazor WebAssembly application, la `Startup` classe définit les composants racine pour l’application et l’emplacement où elles doivent être rendues. Nous examinerons plus en détail la `Startup` classe dans la section démarrage de l' [application](./app-startup.md) .

## <a name="static-files"></a>Fichiers statiques

Contrairement aux projets ASP.NET Web Forms, tous les fichiers d’un Blazor projet ne peuvent pas être demandés en tant que fichiers statiques. Seuls les fichiers du dossier *wwwroot* sont adressables par le Web. Ce dossier est appelé « racine Web » de l’application. Tout ce qui se trouve en dehors de la racine Web de l’application *n’est pas* adressable par le Web. Ce programme d’installation fournit un niveau supplémentaire de sécurité qui empêche l’exposition accidentelle de fichiers projet sur le Web.

## <a name="configuration"></a>Configuration

La configuration dans ASP.NET Web Forms Apps est généralement gérée à l’aide d’un ou plusieurs fichiers *web.config* . Blazor les applications n’ont généralement pas de fichiers *web.config* . Dans ce cas, le fichier est utilisé uniquement pour configurer les paramètres spécifiques à IIS lorsqu’ils sont hébergés sur IIS. Au lieu de cela, Blazor les applications serveur utilisent le ASP.net Core abstractions de la configuration (les Blazor WebAssembly applications ne prennent pas en charge les mêmes abstractions de configuration, mais il peut s’agir d’une fonctionnalité ajoutée à l’avenir). Par exemple, l' Blazor application serveur par défaut stocke certains paramètres dans *appsettings.jssur*.

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

Pour plus d’informations sur la configuration dans ASP.NET Core projets, consultez la section [configuration](./config.md) .

## <a name="razor-components"></a>Composants Razor

La plupart des fichiers dans Blazor les projets sont des fichiers *. Razor* . Razor est un langage de création de modèles basé sur HTML et C# qui est utilisé pour générer dynamiquement l’interface utilisateur Web. Les fichiers *. Razor* définissent les composants qui composent l’interface utilisateur de l’application. Pour l’essentiel, les composants sont identiques pour le Blazor serveur et les Blazor WebAssembly applications. Les composants de Blazor sont analogues aux contrôles utilisateur dans ASP.NET Web Forms.

Chaque fichier de composant Razor est compilé dans une classe .NET lorsque le projet est généré. La classe générée capture l’état du composant, la logique de rendu, les méthodes de cycle de vie, les gestionnaires d’événements et d’autres logiques. Nous allons examiner les composants de création de composants de l' [interface utilisateur réutilisables avec Blazor ](./components.md) la section.

Les fichiers *_Imports. Razor* ne sont pas des fichiers de composants Razor. Au lieu de cela, ils définissent un ensemble de directives Razor à importer dans d’autres fichiers *. Razor* dans le même dossier et dans ses sous-dossiers. Par exemple, un fichier *_Imports. Razor* est un moyen conventionnel d’ajouter `using` des directives pour les espaces de noms couramment utilisés :

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

Où se trouvent les pages dans les Blazor applications ? Blazor ne définit pas d’extension de fichier distincte pour les pages adressables, comme les fichiers *. aspx* dans ASP.NET Web Forms apps. Au lieu de cela, les pages sont définies en affectant des itinéraires aux composants. Un itinéraire est généralement affecté à l’aide de la `@page` directive Razor. Par exemple, le `Counter` composant créé dans le fichier *pages/Counter. Razor* définit l’itinéraire suivant :

```razor
@page "/counter"
```

Le routage dans Blazor est géré côté client et non sur le serveur. Lorsque l’utilisateur navigue dans le navigateur, Blazor intercepte la navigation, puis restitue le composant avec l’itinéraire correspondant.

Les itinéraires des composants ne sont pas actuellement déduits par l’emplacement des fichiers du composant, comme par exemple avec les pages *. aspx* . Cette fonctionnalité peut être ajoutée à l’avenir. Chaque itinéraire doit être spécifié explicitement sur le composant. Le stockage de composants routables dans un dossier *pages* n’a aucune signification particulière et constitue purement une convention.

Nous examinerons plus en détail le routage dans Blazor dans la section [pages, routage et dispositions](./pages-routing-layouts.md) .

## <a name="layout"></a>Layout

Dans ASP.NET Web Forms Apps, une mise en page courante est gérée à l’aide de pages maîtres (*site. Master*). Dans Blazor les applications, la mise en page est gérée à l’aide de composants de disposition (*Shared/MainLayout. Razor*). Les composants de disposition seront abordés plus en détail dans la section [page, routage et dispositions](./pages-routing-layouts.md) .

## <a name="bootstrap-no-locblazor"></a>Démarrage Blazor

Pour Blazor le démarrage, l’application doit :

- Spécifiez l’emplacement de la page où le composant racine (*app. Razor*) doit être rendu.
- Ajoutez le Blazor script d’infrastructure correspondant.

Dans l' Blazor application serveur, la page hôte du composant racine est définie dans le fichier *_Host. cshtml* . Ce fichier définit une page Razor, et non un composant. Razor Pages utiliser syntaxe Razor pour définir une page adressable par le serveur, à l’instar d’une page *. aspx* . La `Html.RenderComponentAsync<TComponent>(RenderMode)` méthode est utilisée pour définir l’emplacement où un composant de niveau racine doit être restitué. L' `RenderMode` option indique la manière dont le composant doit être rendu. Le tableau suivant présente les options prises en charge `RenderMode` .

|Option                        |Description       |
|------------------------------|------------------|
|`RenderMode.Server`           |Rendu interactif une fois qu’une connexion avec le navigateur est établie|
|`RenderMode.ServerPrerendered`|Premier prérendu puis rendu interactif|
|`RenderMode.Static`           |Rendu en tant que contenu statique|

La référence de script à *_framework/blazor.server.js* établit la connexion en temps réel avec le serveur, puis traite toutes les interactions utilisateur et les mises à jour de l’interface utilisateur.

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

Dans l' Blazor WebAssembly application, la page hôte est un simple fichier HTML statique sous *wwwroot/index.html*. L' `<div>` élément avec l’ID nommé `app` est utilisé pour indiquer l’emplacement où le composant racine doit être restitué.

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

Le composant racine à restituer est configuré dans la méthode de l’application `Program.Main` avec la flexibilité nécessaire pour inscrire différents services via l’injection de dépendances. Vous pouvez faire référence à ajouter des services à [ Blazor WebAssembly ](https://docs.microsoft.com/aspnet/core/blazor/fundamentals/dependency-injection?view=aspnetcore-5.0#blazor-webassembly) une application dans

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

## <a name="build-output"></a>Sortie de la génération

Lorsqu’un Blazor projet est généré, tous les fichiers de code et de composant Razor sont compilés dans un assembly unique. Contrairement aux projets ASP.NET Web Forms, Blazor ne prend pas en charge la compilation du runtime de la logique d’interface utilisateur.

## <a name="run-the-app"></a>Exécuter l’application

Pour exécuter l' Blazor application serveur, appuyez sur `F5` dans Visual Studio. Blazor les applications ne prennent pas en charge la compilation du Runtime. Pour afficher les résultats des modifications du balisage du code et des composants, régénérez et redémarrez l’application avec le débogueur attaché. Si vous exécutez sans le débogueur attaché ( `Ctrl+F5` ), Visual Studio surveille les modifications apportées aux fichiers et redémarre l’application à mesure que des modifications sont apportées. Vous actualisez manuellement le navigateur à mesure que des modifications sont apportées.

Pour exécuter l' Blazor WebAssembly application, choisissez l’une des approches suivantes :

- Exécutez le projet client directement à l’aide du serveur de développement.
- Exécutez le projet serveur lors de l’hébergement de l’application avec ASP.NET Core.

BlazorWebAssemblyles applications peuvent être déboguées dans le navigateur et dans Visual Studio. pour plus d’informations, consultez [ASP.net Core Blazor WebAssembly de débogage](/aspnet/core/blazor/debug) .

>[!div class="step-by-step"]
>[Précédent](hosting-models.md) 
> [Suivant](app-startup.md)
