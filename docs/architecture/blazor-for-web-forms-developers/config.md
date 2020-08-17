---
title: la configuration d’une application ;
description: Découvrez comment configurer des Blazor applications sans utiliser ConfigurationManager.
author: csharpfritz
ms.author: jefritz
no-loc:
- Blazor
ms.date: 04/01/2020
ms.openlocfilehash: 6154b4f8c7a5bff42e603b12d5ef85468b80224e
ms.sourcegitcommit: 0100be20fcf23f61dab672deced70059ed71bb2e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88267501"
---
# <a name="app-configuration"></a>la configuration d’une application ;

Le principal moyen de charger la configuration de l’application dans Web Forms consiste à utiliser des entrées dans le fichier *web.config* &mdash; , soit sur le serveur, soit sur un fichier de configuration associé référencé par *web.config*. Vous pouvez utiliser l' `ConfigurationManager` objet statique pour interagir avec les paramètres d’application, les chaînes de connexion du référentiel de données et d’autres fournisseurs de configuration étendus ajoutés à l’application. Il est courant de voir les interactions avec la configuration d’application comme indiqué dans le code suivant :

```csharp
var configurationValue = ConfigurationManager.AppSettings["ConfigurationSettingName"];
var connectionString = ConfigurationManager.ConnectionStrings["MyDatabaseConnectionName"].ConnectionString;
```

Avec ASP.NET Core et côté serveur Blazor , le fichier *web.config* peut être présent si votre application est hébergée sur un serveur IIS Windows. Toutefois, il n’y a aucune `ConfigurationManager` interaction avec cette configuration, et vous pouvez recevoir une configuration d’application plus structurée à partir d’autres sources. Voyons comment la configuration est collectée et comment vous pouvez toujours accéder aux informations de configuration à partir d’un fichier de *web.config* .

## <a name="configuration-sources"></a>Sources de configuration

ASP.NET Core reconnaît qu’il existe de nombreuses sources de configuration que vous pouvez utiliser pour votre application. Le Framework tente de vous offrir le meilleur de ces fonctionnalités par défaut. La configuration est lue et agrégée à partir de ces diverses sources par ASP.NET Core. Les valeurs chargées ultérieurement pour la même clé de configuration sont prioritaires par rapport aux valeurs antérieures.

ASP.NET Core a été conçu pour être compatible avec le Cloud et pour faciliter la configuration des applications pour les opérateurs et les développeurs. ASP.NET Core prend en charge l’environnement et sait s’il s’exécute dans `Production` votre `Development` environnement ou. L’indicateur d’environnement est défini dans la `ASPNETCORE_ENVIRONMENT` variable d’environnement système. Si aucune valeur n’est configurée, l’application est exécutée par défaut dans l' `Production` environnement.

Votre application peut déclencher et ajouter une configuration à partir de plusieurs sources en fonction du nom de l’environnement. Par défaut, la configuration est chargée à partir des ressources suivantes dans l’ordre indiqué :

1. *appsettings.js* fichier, s’il est présent
1. *appSettings. Fichier {ENVIRONMENT_NAME}. JSON* , s’il est présent
1. Fichier de secrets de l’utilisateur sur le disque, le cas échéant
1. Variables d'environnement
1. Arguments de ligne de commande

## <a name="appsettingsjson-format-and-access"></a>appsettings.jsau format et à l’accès

La *appsettings.jssur* le fichier peut être hiérarchique avec des valeurs structurées comme le JSON suivant :

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

Lorsqu’il est présenté avec le code JSON précédent, le système de configuration aplatit les valeurs enfants et référence leurs chemins d’accès hiérarchiques complets. Un caractère deux-points ( `:` ) sépare chaque propriété de la hiérarchie. Par exemple, la clé de configuration `section1:key0` accède à la `section1` valeur du littéral d’objet `key0` .

## <a name="user-secrets"></a>Secrets de l’utilisateur

Secrets de l’utilisateur :

* Valeurs de configuration qui sont stockées dans un fichier JSON sur la station de travail du développeur, en dehors du dossier de développement de l’application.
* Chargé uniquement lors de l’exécution dans l' `Development` environnement.
* Associé à une application spécifique.
* Géré avec la commande de l’CLI .NET Core `user-secrets` .

Configurez votre application pour le stockage des secrets en exécutant la `user-secrets` commande suivante :

```dotnetcli
dotnet user-secrets init
```

La commande précédente ajoute un `UserSecretsId` élément au fichier projet. L’élément contient un GUID, qui est utilisé pour associer des secrets à l’application. Vous pouvez ensuite définir une clé secrète à l’aide de la `set` commande. Par exemple :

```dotnetcli
dotnet user-secrets set "Parent:ApiKey" "12345"
```

La commande précédente rend la `Parent:ApiKey` clé de configuration disponible sur la station de travail d’un développeur avec la valeur `12345` .

Pour plus d’informations sur la création, le stockage et la gestion des secrets d’utilisateur, consultez la page [stockage sécurisé des secrets d’application en développement dans ASP.net Core](/aspnet/core/security/app-secrets) document.

## <a name="environment-variables"></a>Variables d'environnement

L’ensemble suivant de valeurs chargées dans la configuration de votre application est les variables d’environnement du système. Tous les paramètres de la variable d’environnement de votre système sont désormais accessibles via l’API de configuration. Les valeurs hiérarchiques sont aplaties et séparées par deux-points quand elles sont lues à l’intérieur de votre application. Toutefois, certains systèmes d’exploitation n’autorisent pas les noms de variables d’environnement de deux-points. ASP.NET Core résout cette limitation en convertissant les valeurs qui comportent des traits de soulignement doubles ( `__` ) en deux-points lorsque vous y accédez. La `Parent:ApiKey` valeur de la section secrets de l’utilisateur ci-dessus peut être remplacée par la variable d’environnement `Parent__ApiKey` .

## <a name="command-line-arguments"></a>Arguments de ligne de commande

La configuration peut également être fournie en tant qu’arguments de ligne de commande au démarrage de votre application. Utilisez la notation double tiret ( `--` ) ou la barre oblique ( `/` ) pour indiquer le nom de la valeur de configuration à définir et la valeur à configurer. La syntaxe ressemble aux commandes suivantes :

```dotnetcli
dotnet run CommandLineKey1=value1 --CommandLineKey2=value2 /CommandLineKey3=value3
dotnet run --CommandLineKey1 value1 /CommandLineKey2 value2
dotnet run Parent:ApiKey=67890
```

## <a name="the-return-of-webconfig"></a>Retour de web.config

Si vous avez déployé votre application sur Windows sur IIS, le fichier *web.config* configure toujours IIS pour gérer votre application. Par défaut, IIS ajoute une référence au module ASP.NET Core (ANCM). ANCM est un module IIS natif qui héberge votre application à la place du serveur Web Kestrel. Cette *web.config* section ressemble au balisage XML suivant :

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

La configuration spécifique à l’application peut être définie en imbriquant un `environmentVariables` élément dans l' `aspNetCore` élément. Les valeurs définies dans cette section sont présentées à l’application ASP.NET Core en tant que variables d’environnement. Les variables d’environnement sont chargées correctement au cours de ce segment de démarrage de l’application.

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

ASP.NET Core fournit la configuration de l’application par le biais de l' <xref:Microsoft.Extensions.Configuration.IConfiguration> interface. Cette interface de configuration doit être demandée par vos Blazor composants, Blazor pages et toute autre classe gérée par ASP.net core qui a besoin d’accéder à la configuration. Le ASP.NET Core Framework remplira automatiquement cette interface avec la configuration résolue configurée précédemment. Sur une Blazor page ou un balisage Razor d’un composant, vous pouvez injecter l' `IConfiguration` objet avec une `@inject` directive en haut du fichier *. Razor* , comme suit :

```razor
@inject IConfiguration Configuration
```

Cette instruction précédente rend l' `IConfiguration` objet disponible en tant que `Configuration` variable dans le reste du modèle Razor.

Les paramètres de configuration individuels peuvent être lus en spécifiant la hiérarchie des paramètres de configuration recherchée comme paramètre d’indexeur :

```csharp
var mySetting = Configuration["section1:key0"];
```

Vous pouvez extraire des sections de configuration entières à l’aide de la <xref:Microsoft.Extensions.Configuration.IConfiguration.GetSection%2A> méthode pour récupérer une collection de clés à un emplacement spécifique à l’aide d’une syntaxe similaire à pour `GetSection("section1")` récupérer la configuration de Section1 dans l’exemple précédent.

## <a name="strongly-typed-configuration"></a>Configuration fortement typée

Avec Web Forms, il était possible de créer un type de configuration fortement typé hérité du <xref:System.Configuration.ConfigurationSection> type et des types associés. `ConfigurationSection`Vous permettait de configurer certaines règles d’entreprise et le traitement de ces valeurs de configuration.

Dans ASP.NET Core, vous pouvez spécifier une hiérarchie de classes qui recevra les valeurs de configuration. Ces classes :

* Il n’est pas nécessaire d’hériter d’une classe parente.
* Doit inclure `public` des propriétés qui correspondent aux propriétés et aux références de type pour la structure de configuration que vous souhaitez capturer.

Pour le *appsettings.jsprécédent sur* l’exemple, vous pouvez définir les classes suivantes pour capturer les valeurs :

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

Cette hiérarchie de classes peut être remplie en ajoutant la ligne suivante à la `Startup.ConfigureServices` méthode :

```csharp
services.Configure<MyConfig>(Configuration);
```

Dans le reste de l’application, vous pouvez ajouter un paramètre d’entrée aux classes ou à une `@inject` directive dans les modèles Razor de type `IOptions<MyConfig>` pour recevoir les paramètres de configuration fortement typés. La `IOptions<MyConfig>.Value` propriété produira la `MyConfig` valeur remplie à partir des paramètres de configuration.

```razor
@inject IOptions<MyConfig> options
@code {
    var MyConfiguration = options.Value;
    var theSetting = MyConfiguration.section1.key0;
}
```

Vous trouverez plus d’informations sur la fonctionnalité options dans le [modèle options de ASP.net Core](/aspnet/core/fundamentals/configuration/options#options-interfaces) document.

>[!div class="step-by-step"]
>[Précédent](middleware.md) 
> [Suivant](security-authentication-authorization.md)
