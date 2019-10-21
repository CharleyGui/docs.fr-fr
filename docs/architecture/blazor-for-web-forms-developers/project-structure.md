---
title: Structure de projet pour les applications éblouissantes
description: Découvrez comment les structures de projet des ASP.NET Web Forms et des projets éblouissants sont comparées.
author: danroth27
ms.author: daroth
ms.date: 09/11/2019
ms.openlocfilehash: aa9157bd8627e7a03e33872c3023f91ba3d66951
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72520224"
---
# <a name="project-structure-for-blazor-apps"></a>Structure de projet pour les applications éblouissantes

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Malgré leurs différences de structure de projet, ASP.NET Web Forms et éblouissant partagent un grand nombre de concepts similaires. Ici, nous allons examiner la structure d’un projet éblouissant et le comparer à un projet de Web Forms ASP.NET.

Pour créer votre première application éblouissante, suivez les instructions fournies dans les [étapes de prise](/aspnet/core/blazor/get-started)en main de éblouissant. Vous pouvez suivre les instructions pour créer une application de serveur éblouissant ou une application de webassembly éblouissante hébergée dans ASP.NET Core. À l’exception de la logique spécifique au modèle d’hébergement, la majeure partie du code dans les deux projets est identique.

## <a name="project-file"></a>Fichier projet

Les applications serveur éblouissantes sont des projets .NET Core. Le fichier projet pour l’application de serveur éblouissante est à la fois aussi simple que possible :

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>netcoreapp3.0</TargetFramework>
  </PropertyGroup>

</Project>
```

Le fichier projet pour une application de webassembly éblouissant est légèrement plus impliqué (les numéros de version exacts peuvent varier) :

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

Les projets de webassembly éblouissant ciblent .NET Standard au lieu de .NET Core, car ils s’exécutent dans le navigateur sur un Runtime .NET basé sur webassembly. Vous ne pouvez pas installer .NET dans un navigateur Web comme vous le pouvez sur un serveur ou un ordinateur de développement. Par conséquent, le projet fait référence au Framework éblouissant à l’aide de références de package individuelles.

Par comparaison, un projet ASP.NET Web Forms par défaut comprend près de 300 lignes de code XML dans son fichier *. csproj* , dont la plupart répertorient explicitement les différents fichiers de code et de contenu du projet. La plupart des simplifications dans les projets .NET Core et .NET Standard proviennent des cibles et des propriétés par défaut importées en référençant le kit de développement logiciel (SDK) `Microsoft.NET.Sdk.Web`, souvent appelé simplement le kit de développement logiciel (SDK) Web. Le kit de développement logiciel (SDK) Web comprend des caractères génériques et d’autres pratiques qui simplifient l’inclusion de code et de fichiers de contenu dans le projet. Vous n’avez pas besoin de répertorier les fichiers explicitement. Quand vous ciblez .NET Core, le kit de développement logiciel (SDK) Web ajoute également des références d’infrastructure aux frameworks partagés .NET Core et ASP.NET Core. Les frameworks sont visibles à partir du nœud **dépendances**  > **infrastructures** dans la fenêtre **Explorateur de solutions** . Les frameworks partagés sont des collections d’assemblys qui ont été installés sur l’ordinateur lors de l’installation de .NET Core.

Bien qu’elles soient prises en charge, les références d’assembly individuelles sont moins fréquentes dans les projets .NET Core. La plupart des dépendances de projet sont gérées en tant que références de package NuGet. Il vous suffit de référencer les dépendances de package de niveau supérieur dans les projets .NET Core. Les dépendances transitives sont incluses automatiquement. Au lieu d’utiliser le fichier *packages. config* couramment trouvé dans les projets ASP.NET Web Forms pour référencer des packages, des références de package sont ajoutées au fichier projet à l’aide de l’élément `<PackageReference>`.

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="12.0.2" />
</ItemGroup>
```

## <a name="entry-point"></a>Point d’entrée

Le point d’entrée de l’application serveur éblouissant est défini dans le fichier *Program.cs* , comme vous pouvez le voir dans une application console. Lorsque l’application s’exécute, elle crée et exécute une instance d’hôte Web à l’aide des valeurs par défaut spécifiques aux applications Web. L’hôte Web gère le cycle de vie de l’application serveur éblouissante et configure les services de niveau hôte. La configuration, la journalisation, l’injection de dépendances et le serveur HTTP sont des exemples de ces services. Ce code est principalement réutilisable et reste souvent inchangé.

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

Les applications de webassembly éblouissantes définissent également un point d’entrée dans *Program.cs*. Le code semble légèrement différent. Le code est similaire en ce qu’il configure l’hôte d’application pour fournir les mêmes services de niveau hôte à l’application. Toutefois, l’hôte d’application webassembly ne configure pas un serveur HTTP, car il s’exécute directement dans le navigateur.

Les applications éblouissantes ont une classe `Startup` au lieu d’un fichier *global. asax* pour définir la logique de démarrage de l’application. La classe `Startup` est utilisée pour configurer l’application et tous les services spécifiques à l’application. Dans l’application de serveur éblouissant, la classe `Startup` est utilisée pour configurer le point de terminaison de la connexion en temps réel utilisée par éblouissant entre les navigateurs clients et le serveur. Dans l’application de webassembly éblouissant, la classe `Startup` définit les composants racine de l’application et l’emplacement où elles doivent être rendues. Nous examinerons plus en détail la classe `Startup` dans la section démarrage de l' [application](./app-startup.md) .

## <a name="static-files"></a>Fichiers statiques

Contrairement aux projets ASP.NET Web Forms, tous les fichiers d’un projet éblouissant ne peuvent pas être demandés en tant que fichiers statiques. Seuls les fichiers du dossier *wwwroot* sont adressables par le Web. Ce dossier est appelé « racine Web » de l’application. Tout ce qui se trouve en dehors de la racine Web de l’application *n’est pas* adressable par le Web. Ce programme d’installation fournit un niveau supplémentaire de sécurité qui empêche l’exposition accidentelle de fichiers projet sur le Web.

## <a name="configuration"></a>Configuration

La configuration dans ASP.NET Web Forms Apps est généralement gérée à l’aide d’un ou de plusieurs fichiers *Web. config* . Les applications éblouissantes n’ont généralement pas de fichiers *Web. config* . Dans ce cas, le fichier est utilisé uniquement pour configurer les paramètres spécifiques à IIS lorsqu’ils sont hébergés sur IIS. Au lieu de cela, les applications de serveur éblouissant utilisent le ASP.NET Core abstractions de la configuration (les applications webassembly éblouissantes ne prennent pas en charge les mêmes abstractions de configuration, mais il peut s’agir d’une fonctionnalité ajoutée à l’avenir). Par exemple, l’application de serveur éblouissante par défaut stocke certains paramètres dans *appSettings. JSON*.

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

La plupart des fichiers dans les projets éblouissants sont des fichiers *. Razor* . Razor est un langage de création de modèles basé C# sur HTML et utilisé pour générer dynamiquement l’interface utilisateur Web. Les fichiers *. Razor* définissent les composants qui composent l’interface utilisateur de l’application. Pour l’essentiel, les composants sont identiques pour le serveur éblouissant et les applications webassembly éblouissantes. Les composants de éblouissant sont analogues aux contrôles utilisateur dans ASP.NET Web Forms.

Chaque fichier de composant Razor est compilé dans une classe .NET lorsque le projet est généré. La classe générée capture l’état du composant, la logique de rendu, les méthodes de cycle de vie, les gestionnaires d’événements et d’autres logiques. Nous examinerons la création de composants dans la section [création de composants d’interface utilisateur réutilisables avec éblouissant](./components.md) .

Les fichiers *_Imports. Razor* ne sont pas des fichiers de composants Razor. Au lieu de cela, ils définissent un ensemble de directives Razor à importer dans d’autres fichiers *. Razor* dans le même dossier et dans ses sous-dossiers. Par exemple, un fichier *_Imports. Razor* est un moyen conventionnel d’ajouter des instructions `using` pour les espaces de noms couramment utilisés :

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

Où se trouvent les pages des applications éblouissantes ? Éblouissant ne définit pas d’extension de fichier distincte pour les pages adressables, comme les fichiers *. aspx* dans ASP.NET Web Forms apps. Au lieu de cela, les pages sont définies en affectant des itinéraires aux composants. Un itinéraire est généralement affecté à l’aide de la directive `@page` Razor. Par exemple, le composant `Counter` créé dans le fichier *pages/Counter. Razor* définit l’itinéraire suivant :

```razor
@page "/counter"
```

Le routage dans éblouissant est géré côté client et non sur le serveur. Lorsque l’utilisateur navigue dans le navigateur, éblouissant intercepte la navigation, puis restitue le composant avec l’itinéraire correspondant. 

Les itinéraires des composants ne sont pas actuellement déduits par l’emplacement des fichiers du composant, comme par exemple avec les pages *. aspx* . Cette fonctionnalité peut être ajoutée à l’avenir. Chaque itinéraire doit être spécifié explicitement sur le composant. Le stockage de composants routables dans un dossier *pages* n’a aucune signification particulière et constitue purement une convention.

Nous examinerons plus en détail le routage dans éblouissant dans la section [pages, routage et dispositions](./pages-routing-layouts.md) .

## <a name="layout"></a>Mise en page

Dans ASP.NET Web Forms Apps, la disposition de page courante est gérée à l’aide de pages maîtres (*site. Master*). Dans les applications éblouissantes, la mise en page est gérée à l’aide de composants de disposition (*Shared/MainLayout. Razor*). Les composants de disposition seront abordés plus en détail dans la section [page, routage et dispositions](./pages-routing-layouts.md) .

## <a name="bootstrap-blazor"></a>Démarrage éblouissant

Pour démarrer éblouissant, l’application doit :

- Spécifiez l’emplacement de la page où le composant racine (*app. Razor*) doit être rendu.
- Ajoutez le script de Framework éblouissant correspondant.

Dans l’application de serveur éblouissant, la page hôte du composant racine est définie dans le fichier *_Host. cshtml* . Ce fichier définit une page Razor, et non un composant. Razor Pages utiliser syntaxe Razor pour définir une page adressable par le serveur, à l’instar d’une page *. aspx* . La méthode `Html.RenderComponentAsync<TComponent>(RenderMode)` est utilisée pour définir l’emplacement de rendu d’un composant de niveau racine. L’option `RenderMode` indique la manière dont le composant doit être rendu. Le tableau suivant présente les options de `RenderMode` prises en charge.

|Option                        |Description       |
|------------------------------|------------------|
|`RenderMode.Server`           |Rendu interactif une fois qu’une connexion avec le navigateur est établie|
|`RenderMode.ServerPrerendered`|Premier prérendu puis rendu interactif|
|`RenderMode.Static`           |Rendu en tant que contenu statique|

La référence de script à *_framework/éblouissant. Server. js* établit la connexion en temps réel avec le serveur, puis traite toutes les interactions utilisateur et les mises à jour de l’interface utilisateur.

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

Dans l’application de webassembly éblouissant, la page hôte est un simple fichier HTML statique sous *wwwroot/index.html*. L’élément `<app>` est utilisé pour indiquer l’emplacement où le composant racine doit être restitué.

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

Le composant spécifique à restituer est configuré dans la méthode `Startup.Configure` de l’application avec un sélecteur CSS correspondant indiquant où le composant doit être rendu.

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

Lorsqu’un projet éblouissant est généré, tous les fichiers de code et de composant Razor sont compilés dans un assembly unique. Contrairement aux projets ASP.NET Web Forms, éblouissant ne prend pas en charge la compilation du runtime de la logique d’interface utilisateur.

## <a name="run-the-app"></a>Exécuter l'application

Pour exécuter l’application de serveur éblouissante, appuyez sur `F5` dans Visual Studio. Les applications éblouissantes ne prennent pas en charge la compilation au moment de l’exécution. Pour afficher les résultats des modifications du balisage du code et des composants, régénérez et redémarrez l’application avec le débogueur attaché. Si vous exécutez sans le débogueur attaché (`Ctrl+F5`), Visual Studio surveille les modifications apportées aux fichiers et redémarre l’application à mesure que des modifications sont apportées. Vous actualisez manuellement le navigateur à mesure que des modifications sont apportées.

Pour exécuter l’application éblouissant webassembly, choisissez l’une des approches suivantes :

- Exécutez le projet client directement à l’aide du serveur de développement.
- Exécutez le projet serveur lors de l’hébergement de l’application avec ASP.NET Core.

Les applications webassembly éblouissantes ne prennent pas en charge le débogage à l’aide de Visual Studio. Pour exécuter l’application, utilisez `Ctrl+F5` au lieu de `F5`. Au lieu de cela, vous pouvez déboguer des applications webassembly éblouissantes directement dans le navigateur. Pour plus d’informations, consultez [Déboguer ASP.net Core éblouissant](/aspnet/core/blazor/debug) .

>[!div class="step-by-step"]
>[Précédent](hosting-models.md)
>[Suivant](app-startup.md)
