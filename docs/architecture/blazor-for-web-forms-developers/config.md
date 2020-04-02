---
title: la configuration d’une application ;
description: Découvrez comment configurer les applications Blazor sans utiliser ConfigurationManager.
author: csharpfritz
ms.author: jefritz
ms.date: 04/01/2020
ms.openlocfilehash: c780a395f72e2520af86c20c7f6618953a528ff7
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588244"
---
# <a name="app-configuration"></a>la configuration d’une application ;

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

La principale façon de charger la configuration de l’application&mdash;dans les formulaires Web est avec les entrées dans le fichier *web.config* soit sur le serveur ou un fichier de configuration connexe référencé par *web.config*. Vous pouvez utiliser `ConfigurationManager` l’objet statique pour interagir avec les paramètres de l’application, les chaînes de connexion de référentiel de données et d’autres fournisseurs de configuration étendu qui sont ajoutés dans l’application. Il est typique de voir les interactions avec la configuration de l’application comme on le voit dans le code suivant :

```csharp
var configurationValue = ConfigurationManager.AppSettings["ConfigurationSettingName"];
var connectionString = ConfigurationManager.ConnectionStrings["MyDatabaseConnectionName"].ConnectionString;
```

Avec ASP.NET Core et le serveur Blazor, le fichier *web.config* peut être présent si votre application est hébergée sur un serveur Windows IIS. Cependant, il n’y a pas `ConfigurationManager` d’interaction avec cette configuration, et vous pouvez recevoir une configuration d’application plus structurée à partir d’autres sources. Jetons un coup d’oeil à la façon dont la configuration est recueillie et comment vous pouvez toujours accéder aux informations de configuration à partir d’un fichier *web.config.*

## <a name="configuration-sources"></a>Sources de configuration

ASP.NET Core reconnaît qu’il existe de nombreuses sources de configuration que vous voudrez peut-être utiliser pour votre application. Le cadre tente de vous offrir le meilleur de ces fonctionnalités par défaut. La configuration est lue et agrégée à partir de ces différentes sources par ASP.NET Core. Des valeurs chargées ultérieures pour la même clé de configuration ont préséance sur les valeurs antérieures.

ASP.NET Core a été conçu pour être conscient du cloud et faciliter la configuration des applications pour les opérateurs et les développeurs. ASP.NET Core est soucieux de l’environnement et sait `Production` s’il fonctionne dans votre environnement ou dans `Development` votre environnement. L’indicateur de l’environnement est défini dans la variable de l’environnement du `ASPNETCORE_ENVIRONMENT` système. Si aucune valeur n’est configurée, `Production` l’application est par défaut pour s’exécuter dans l’environnement.

Votre application peut déclencher et ajouter la configuration à partir de plusieurs sources basées sur le nom de l’environnement. Par défaut, la configuration est chargée à partir des ressources suivantes dans l’ordre énuméré :

1. *fichier appsettings.json,* s’il est présent
1. *applications. Fichier ENVIRONMENT_NAME.json, s’il* est présent
1. Fichier de secrets d’utilisateur sur disque, si présent
1. Variables d'environnement
1. Arguments de ligne de commande

## <a name="appsettingsjson-format-and-access"></a>format et accès appsettings.json

Le fichier *appsettings.json* peut être hiérarchique avec des valeurs structurées comme le JSON suivant :

```json
{
  "section0": {
    "key0": "value",
    "key1": "value"
  },
  "section1": {
    "key0": "value",
    "key1": "value"
  }
}
```

Lorsqu’il est présenté avec le précédent JSON, le système de configuration aplatit les valeurs des enfants et fait référence à leurs chemins hiérarchiques entièrement qualifiés. Un personnage`:`de colon () sépare chaque propriété de la hiérarchie. Par exemple, la `section1:key0` clé `section1` de configuration accède à la valeur littérale de `key0` l’objet.

## <a name="user-secrets"></a>Secrets d’utilisateur

Les secrets des utilisateurs sont les :

* Valeurs de configuration stockées dans un fichier JSON sur le poste de travail du développeur, en dehors du dossier de développement de l’application.
* Seulement chargé lors `Development` de la course dans l’environnement.
* Associé à une application spécifique.
* Géré avec la `user-secrets` commande de cLI de base .NET.

Configurez votre application pour le `user-secrets` stockage des secrets en exécutant la commande :

```dotnetcli
dotnet user-secrets init
```

La commande précédente `UserSecretsId` ajoute un élément au dossier du projet. L’élément contient un GUID, qui est utilisé pour associer des secrets à l’application. Vous pouvez alors définir `set` un secret avec la commande. Par exemple :

```dotnetcli
dotnet user-secrets set "Parent:ApiKey" "12345"
```

La commande précédente `Parent:ApiKey` rend la clé de configuration disponible `12345`sur le poste de travail d’un développeur avec la valeur .

Pour plus d’informations sur la création, le stockage et la gestion des secrets d’utilisateur, consultez le [stockage sécurisé des secrets d’applications en développement dans ASP.NET](/aspnet/core/security/app-secrets) document Core.

## <a name="environment-variables"></a>Variables d'environnement

Le prochain ensemble de valeurs chargées dans la configuration de votre application est les variables de l’environnement du système. Tous les paramètres variables de l’environnement de votre système vous sont désormais accessibles grâce à l’API de configuration. Les valeurs hiérarchiques sont aplaties et séparées par des personnages du côlon lorsqu’elles sont lues à l’intérieur de votre application. Cependant, certains systèmes d’exploitation ne permettent pas les noms variables de l’environnement de caractère de colon. ASP.NET Core s’attaque à cette limitation en convertissant`__`des valeurs qui ont des double-underscores ( ) en un côlon quand ils sont consultés. La `Parent:ApiKey` valeur de la section des secrets d’utilisateur `Parent__ApiKey`ci-dessus peut être annulée avec la variable de l’environnement .

## <a name="command-line-arguments"></a>Arguments de ligne de commande

La configuration peut également être fournie comme arguments de ligne de commande lorsque votre application est lancée. Utilisez la notation`--`double-dash (`/`) ou à l’avant pour indiquer le nom de la valeur de configuration à définir et la valeur à configurer. La syntaxe ressemble aux commandes suivantes :

```dotnetcli
dotnet run CommandLineKey1=value1 --CommandLineKey2=value2 /CommandLineKey3=value3
dotnet run --CommandLineKey1 value1 /CommandLineKey2 value2
dotnet run Parent:ApiKey=67890
```

## <a name="the-return-of-webconfig"></a>Le retour de web.config

Si vous avez déployé votre application sur Windows sur IIS, le fichier *web.config* configure toujours IIS pour gérer votre application. Par défaut, IIS ajoute une référence au module de base ASP.NET (ANCM). ANCM est un module IIS natif qui héberge votre application à la place du serveur Web Kestrel. Cette section *web.config* ressemble à la balisage XML suivante:

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <location path="." inheritInChildApplications="false">
    <system.webServer>
      <handlers>
        <add name="aspNetCore" path="*" verb="*" modules="AspNetCoreModuleV2" resourceType="Unspecified" />
      </handlers>
      <aspNetCore processPath=".\MyApp.exe"
                  stdoutLogEnabled="false"
                  stdoutLogFile=".\logs\stdout"
                  hostingModel="inprocess" />
    </system.webServer>
  </location>
</configuration>
```

La configuration spécifique à l’application `environmentVariables` peut `aspNetCore` être définie en niant un élément de l’élément. Les valeurs définies dans cette section sont présentées à l’application ASP.NET Core comme variables de l’environnement. Les variables de l’environnement se chargent de manière appropriée au cours de ce segment de démarrage d’applications.

```xml
<aspNetCore processPath="dotnet"
      arguments=".\MyApp.dll"
      stdoutLogEnabled="false"
      stdoutLogFile=".\logs\stdout"
      hostingModel="inprocess">
  <environmentVariables>
    <environmentVariable name="ASPNETCORE_ENVIRONMENT" value="Development" />
    <environmentVariable name="Parent:ApiKey" value="67890" />
  </environmentVariables>
</aspNetCore>
```

## <a name="read-configuration-in-the-app"></a>Lire la configuration dans l’application

ASP.NET Core fournit la configuration <xref:Microsoft.Extensions.Configuration.IConfiguration> de l’application à travers l’interface. Cette interface de configuration doit être demandée par vos composants Blazor, pages Blazor et toute autre classe ASP.NET gérée par Core qui a besoin d’accéder à la configuration. Le cadre ASP.NET Core remplira automatiquement cette interface avec la configuration résolue configurée plus tôt. Sur une page Blazor ou la balisage Razor `IConfiguration` d’un composant, vous pouvez injecter l’objet avec une `@inject` directive en haut du fichier *.razor* comme ceci:

```razor
@inject IConfiguration Configuration
```

Cette déclaration précédente `IConfiguration` rend l’objet disponible comme variable `Configuration` tout au long du reste du modèle Razor.

Les paramètres de configuration individuels peuvent être lus en spécifiant la hiérarchie de réglage de configuration recherchée comme paramètre d’indexeur :

```csharp
var mySetting = Configuration["section1:key0"];
```

Vous pouvez aller chercher des <xref:Microsoft.Extensions.Configuration.IConfiguration.GetSection%2A> sections de configuration entières en utilisant la méthode `GetSection("section1")` pour récupérer une collection de clés à un endroit spécifique avec une syntaxe similaire à récupérer la configuration pour la section1 de l’exemple précédent.

## <a name="strongly-typed-configuration"></a>Configuration fortement tapée

Avec Web Forms, il a été possible de créer <xref:System.Configuration.ConfigurationSection> un type de configuration fortement tapé qui a hérité du type et des types associés. A `ConfigurationSection` vous a permis de configurer certaines règles d’entreprise et le traitement de ces valeurs de configuration.

Dans ASP.NET Core, vous pouvez spécifier une hiérarchie de classe qui recevra les valeurs de configuration. Ces classes:

* Vous n’avez pas besoin d’hériter d’une classe de parents.
* Devrait `public` inclure les propriétés qui correspondent aux propriétés et les références de type pour la structure de configuration que vous souhaitez capturer.

Pour l’échantillon *appsettings.json* antérieur, vous pouvez définir les classes suivantes pour capturer les valeurs :

```csharp
public class MyConfig
{
    public MyConfigSection section0 { get; set;}

    public MyConfigSection section1 { get; set;}
}

public class MyConfigSection
{
    public string key0 { get; set; }

    public string key1 { get; set; }
}
```

Cette hiérarchie de classe peut être peuplée `Startup.ConfigureServices` en ajoutant la ligne suivante à la méthode :

```csharp
services.Configure<MyConfig>(Configuration);
```

Dans le reste de l’application, vous pouvez `@inject` ajouter un paramètre `IOptions<MyConfig>` d’entrée aux classes ou une directive dans les modèles de type Razor pour recevoir les paramètres de configuration fortement tapés. La `IOptions<MyConfig>.Value` propriété produira `MyConfig` la valeur peuplée des paramètres de configuration.

```razor
@inject IOptions<MyConfig> options
@code {
    var MyConfiguration = options.Value;
    var theSetting = MyConfiguration.section1.key0;
}
```

Vous trouverez plus d’informations sur la fonction Options dans le modèle Options dans ASP.NET document [de base.](/aspnet/core/fundamentals/configuration/options#options-interfaces)

>[!div class="step-by-step"]
>[Suivant précédent](middleware.md)
>[Next](security-authentication-authorization.md)
