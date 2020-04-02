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
# <a name="app-configuration"></a><span data-ttu-id="34fb9-103">la configuration d’une application ;</span><span class="sxs-lookup"><span data-stu-id="34fb9-103">App configuration</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="34fb9-104">La principale façon de charger la configuration de l’application&mdash;dans les formulaires Web est avec les entrées dans le fichier *web.config* soit sur le serveur ou un fichier de configuration connexe référencé par *web.config*. Vous pouvez utiliser `ConfigurationManager` l’objet statique pour interagir avec les paramètres de l’application, les chaînes de connexion de référentiel de données et d’autres fournisseurs de configuration étendu qui sont ajoutés dans l’application.</span><span class="sxs-lookup"><span data-stu-id="34fb9-104">The primary way to load app configuration in Web Forms is with entries in the *web.config* file&mdash;either on the server or a related configuration file referenced by *web.config*. You can use the static `ConfigurationManager` object to interact with app settings, data repository connection strings, and other extended configuration providers that are added into the app.</span></span> <span data-ttu-id="34fb9-105">Il est typique de voir les interactions avec la configuration de l’application comme on le voit dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="34fb9-105">It's typical to see interactions with app configuration as seen in the following code:</span></span>

```csharp
var configurationValue = ConfigurationManager.AppSettings["ConfigurationSettingName"];
var connectionString = ConfigurationManager.ConnectionStrings["MyDatabaseConnectionName"].ConnectionString;
```

<span data-ttu-id="34fb9-106">Avec ASP.NET Core et le serveur Blazor, le fichier *web.config* peut être présent si votre application est hébergée sur un serveur Windows IIS.</span><span class="sxs-lookup"><span data-stu-id="34fb9-106">With ASP.NET Core and server-side Blazor, the *web.config* file MAY be present if your app is hosted on a Windows IIS server.</span></span> <span data-ttu-id="34fb9-107">Cependant, il n’y a pas `ConfigurationManager` d’interaction avec cette configuration, et vous pouvez recevoir une configuration d’application plus structurée à partir d’autres sources.</span><span class="sxs-lookup"><span data-stu-id="34fb9-107">However, there's no `ConfigurationManager` interaction with this configuration, and you can receive more structured app configuration from other sources.</span></span> <span data-ttu-id="34fb9-108">Jetons un coup d’oeil à la façon dont la configuration est recueillie et comment vous pouvez toujours accéder aux informations de configuration à partir d’un fichier *web.config.*</span><span class="sxs-lookup"><span data-stu-id="34fb9-108">Let's take a look at how configuration is gathered and how you can still access configuration information from a *web.config* file.</span></span>

## <a name="configuration-sources"></a><span data-ttu-id="34fb9-109">Sources de configuration</span><span class="sxs-lookup"><span data-stu-id="34fb9-109">Configuration sources</span></span>

<span data-ttu-id="34fb9-110">ASP.NET Core reconnaît qu’il existe de nombreuses sources de configuration que vous voudrez peut-être utiliser pour votre application.</span><span class="sxs-lookup"><span data-stu-id="34fb9-110">ASP.NET Core recognizes there are many configuration sources you may want to use for your app.</span></span> <span data-ttu-id="34fb9-111">Le cadre tente de vous offrir le meilleur de ces fonctionnalités par défaut.</span><span class="sxs-lookup"><span data-stu-id="34fb9-111">The framework attempts to offer you the best of these features by default.</span></span> <span data-ttu-id="34fb9-112">La configuration est lue et agrégée à partir de ces différentes sources par ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="34fb9-112">Configuration is read and aggregated from these various sources by ASP.NET Core.</span></span> <span data-ttu-id="34fb9-113">Des valeurs chargées ultérieures pour la même clé de configuration ont préséance sur les valeurs antérieures.</span><span class="sxs-lookup"><span data-stu-id="34fb9-113">Later loaded values for the same configuration key take precedence over earlier values.</span></span>

<span data-ttu-id="34fb9-114">ASP.NET Core a été conçu pour être conscient du cloud et faciliter la configuration des applications pour les opérateurs et les développeurs.</span><span class="sxs-lookup"><span data-stu-id="34fb9-114">ASP.NET Core was designed to be cloud-aware and to make configuration of apps easier for both operators and developers.</span></span> <span data-ttu-id="34fb9-115">ASP.NET Core est soucieux de l’environnement et sait `Production` s’il fonctionne dans votre environnement ou dans `Development` votre environnement.</span><span class="sxs-lookup"><span data-stu-id="34fb9-115">ASP.NET Core is environment-aware and knows if it's running in your `Production` or `Development` environment.</span></span> <span data-ttu-id="34fb9-116">L’indicateur de l’environnement est défini dans la variable de l’environnement du `ASPNETCORE_ENVIRONMENT` système.</span><span class="sxs-lookup"><span data-stu-id="34fb9-116">The environment indicator is set in the `ASPNETCORE_ENVIRONMENT` system environment variable.</span></span> <span data-ttu-id="34fb9-117">Si aucune valeur n’est configurée, `Production` l’application est par défaut pour s’exécuter dans l’environnement.</span><span class="sxs-lookup"><span data-stu-id="34fb9-117">If no value is configured, the app defaults to running in the `Production` environment.</span></span>

<span data-ttu-id="34fb9-118">Votre application peut déclencher et ajouter la configuration à partir de plusieurs sources basées sur le nom de l’environnement.</span><span class="sxs-lookup"><span data-stu-id="34fb9-118">Your app can trigger and add configuration from several sources based on the environment's name.</span></span> <span data-ttu-id="34fb9-119">Par défaut, la configuration est chargée à partir des ressources suivantes dans l’ordre énuméré :</span><span class="sxs-lookup"><span data-stu-id="34fb9-119">By default, configuration is loaded from the following resources in the order listed:</span></span>

1. <span data-ttu-id="34fb9-120">*fichier appsettings.json,* s’il est présent</span><span class="sxs-lookup"><span data-stu-id="34fb9-120">*appsettings.json* file, if present</span></span>
1. <span data-ttu-id="34fb9-121">*applications. Fichier ENVIRONMENT_NAME.json, s’il* est présent</span><span class="sxs-lookup"><span data-stu-id="34fb9-121">*appsettings.{ENVIRONMENT_NAME}.json* file, if present</span></span>
1. <span data-ttu-id="34fb9-122">Fichier de secrets d’utilisateur sur disque, si présent</span><span class="sxs-lookup"><span data-stu-id="34fb9-122">User secrets file on disk, if present</span></span>
1. <span data-ttu-id="34fb9-123">Variables d'environnement</span><span class="sxs-lookup"><span data-stu-id="34fb9-123">Environment variables</span></span>
1. <span data-ttu-id="34fb9-124">Arguments de ligne de commande</span><span class="sxs-lookup"><span data-stu-id="34fb9-124">Command-line arguments</span></span>

## <a name="appsettingsjson-format-and-access"></a><span data-ttu-id="34fb9-125">format et accès appsettings.json</span><span class="sxs-lookup"><span data-stu-id="34fb9-125">appsettings.json format and access</span></span>

<span data-ttu-id="34fb9-126">Le fichier *appsettings.json* peut être hiérarchique avec des valeurs structurées comme le JSON suivant :</span><span class="sxs-lookup"><span data-stu-id="34fb9-126">The *appsettings.json* file can be hierarchical with values structured like the following JSON:</span></span>

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

<span data-ttu-id="34fb9-127">Lorsqu’il est présenté avec le précédent JSON, le système de configuration aplatit les valeurs des enfants et fait référence à leurs chemins hiérarchiques entièrement qualifiés.</span><span class="sxs-lookup"><span data-stu-id="34fb9-127">When presented with the preceding JSON, the configuration system flattens child values and references their fully qualified hierarchical paths.</span></span> <span data-ttu-id="34fb9-128">Un personnage`:`de colon () sépare chaque propriété de la hiérarchie.</span><span class="sxs-lookup"><span data-stu-id="34fb9-128">A colon (`:`) character separates each property in the hierarchy.</span></span> <span data-ttu-id="34fb9-129">Par exemple, la `section1:key0` clé `section1` de configuration accède à la valeur littérale de `key0` l’objet.</span><span class="sxs-lookup"><span data-stu-id="34fb9-129">For example, the configuration key `section1:key0` accesses the `section1` object literal's `key0` value.</span></span>

## <a name="user-secrets"></a><span data-ttu-id="34fb9-130">Secrets d’utilisateur</span><span class="sxs-lookup"><span data-stu-id="34fb9-130">User secrets</span></span>

<span data-ttu-id="34fb9-131">Les secrets des utilisateurs sont les :</span><span class="sxs-lookup"><span data-stu-id="34fb9-131">User secrets are:</span></span>

* <span data-ttu-id="34fb9-132">Valeurs de configuration stockées dans un fichier JSON sur le poste de travail du développeur, en dehors du dossier de développement de l’application.</span><span class="sxs-lookup"><span data-stu-id="34fb9-132">Configuration values that are stored in a JSON file on the developer's workstation, outside of the app development folder.</span></span>
* <span data-ttu-id="34fb9-133">Seulement chargé lors `Development` de la course dans l’environnement.</span><span class="sxs-lookup"><span data-stu-id="34fb9-133">Only loaded when running in the `Development` environment.</span></span>
* <span data-ttu-id="34fb9-134">Associé à une application spécifique.</span><span class="sxs-lookup"><span data-stu-id="34fb9-134">Associated with a specific app.</span></span>
* <span data-ttu-id="34fb9-135">Géré avec la `user-secrets` commande de cLI de base .NET.</span><span class="sxs-lookup"><span data-stu-id="34fb9-135">Managed with the .NET Core CLI's `user-secrets` command.</span></span>

<span data-ttu-id="34fb9-136">Configurez votre application pour le `user-secrets` stockage des secrets en exécutant la commande :</span><span class="sxs-lookup"><span data-stu-id="34fb9-136">Configure your app for secrets storage by executing the `user-secrets` command:</span></span>

```dotnetcli
dotnet user-secrets init
```

<span data-ttu-id="34fb9-137">La commande précédente `UserSecretsId` ajoute un élément au dossier du projet.</span><span class="sxs-lookup"><span data-stu-id="34fb9-137">The preceding command adds a `UserSecretsId` element to the project file.</span></span> <span data-ttu-id="34fb9-138">L’élément contient un GUID, qui est utilisé pour associer des secrets à l’application.</span><span class="sxs-lookup"><span data-stu-id="34fb9-138">The element contains a GUID, which is used to associate secrets with the app.</span></span> <span data-ttu-id="34fb9-139">Vous pouvez alors définir `set` un secret avec la commande.</span><span class="sxs-lookup"><span data-stu-id="34fb9-139">You can then define a secret with the `set` command.</span></span> <span data-ttu-id="34fb9-140">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="34fb9-140">For example:</span></span>

```dotnetcli
dotnet user-secrets set "Parent:ApiKey" "12345"
```

<span data-ttu-id="34fb9-141">La commande précédente `Parent:ApiKey` rend la clé de configuration disponible `12345`sur le poste de travail d’un développeur avec la valeur .</span><span class="sxs-lookup"><span data-stu-id="34fb9-141">The preceding command makes the `Parent:ApiKey` configuration key available on a developer's workstation with the value `12345`.</span></span>

<span data-ttu-id="34fb9-142">Pour plus d’informations sur la création, le stockage et la gestion des secrets d’utilisateur, consultez le [stockage sécurisé des secrets d’applications en développement dans ASP.NET](/aspnet/core/security/app-secrets) document Core.</span><span class="sxs-lookup"><span data-stu-id="34fb9-142">For more information about creating, storing, and managing user secrets, see the [Safe storage of app secrets in development in ASP.NET Core](/aspnet/core/security/app-secrets) document.</span></span>

## <a name="environment-variables"></a><span data-ttu-id="34fb9-143">Variables d'environnement</span><span class="sxs-lookup"><span data-stu-id="34fb9-143">Environment variables</span></span>

<span data-ttu-id="34fb9-144">Le prochain ensemble de valeurs chargées dans la configuration de votre application est les variables de l’environnement du système.</span><span class="sxs-lookup"><span data-stu-id="34fb9-144">The next set of values loaded into your app configuration is the system's environment variables.</span></span> <span data-ttu-id="34fb9-145">Tous les paramètres variables de l’environnement de votre système vous sont désormais accessibles grâce à l’API de configuration.</span><span class="sxs-lookup"><span data-stu-id="34fb9-145">All of your system's environment variable settings are now accessible to you through the configuration API.</span></span> <span data-ttu-id="34fb9-146">Les valeurs hiérarchiques sont aplaties et séparées par des personnages du côlon lorsqu’elles sont lues à l’intérieur de votre application.</span><span class="sxs-lookup"><span data-stu-id="34fb9-146">Hierarchical values are flattened and separated by colon characters when read inside your app.</span></span> <span data-ttu-id="34fb9-147">Cependant, certains systèmes d’exploitation ne permettent pas les noms variables de l’environnement de caractère de colon.</span><span class="sxs-lookup"><span data-stu-id="34fb9-147">However, some operating systems don't allow the colon character environment variable names.</span></span> <span data-ttu-id="34fb9-148">ASP.NET Core s’attaque à cette limitation en convertissant`__`des valeurs qui ont des double-underscores ( ) en un côlon quand ils sont consultés.</span><span class="sxs-lookup"><span data-stu-id="34fb9-148">ASP.NET Core addresses this limitation by converting values that have double-underscores (`__`) into a colon when they're accessed.</span></span> <span data-ttu-id="34fb9-149">La `Parent:ApiKey` valeur de la section des secrets d’utilisateur `Parent__ApiKey`ci-dessus peut être annulée avec la variable de l’environnement .</span><span class="sxs-lookup"><span data-stu-id="34fb9-149">The `Parent:ApiKey` value from the user secrets section above can be overridden with the environment variable `Parent__ApiKey`.</span></span>

## <a name="command-line-arguments"></a><span data-ttu-id="34fb9-150">Arguments de ligne de commande</span><span class="sxs-lookup"><span data-stu-id="34fb9-150">Command-line arguments</span></span>

<span data-ttu-id="34fb9-151">La configuration peut également être fournie comme arguments de ligne de commande lorsque votre application est lancée.</span><span class="sxs-lookup"><span data-stu-id="34fb9-151">Configuration can also be provided as command-line arguments when your app is started.</span></span> <span data-ttu-id="34fb9-152">Utilisez la notation`--`double-dash (`/`) ou à l’avant pour indiquer le nom de la valeur de configuration à définir et la valeur à configurer.</span><span class="sxs-lookup"><span data-stu-id="34fb9-152">Use the double-dash (`--`) or forward-slash (`/`) notation to indicate the name of the configuration value to set and the value to be configured.</span></span> <span data-ttu-id="34fb9-153">La syntaxe ressemble aux commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="34fb9-153">The syntax resembles the following commands:</span></span>

```dotnetcli
dotnet run CommandLineKey1=value1 --CommandLineKey2=value2 /CommandLineKey3=value3
dotnet run --CommandLineKey1 value1 /CommandLineKey2 value2
dotnet run Parent:ApiKey=67890
```

## <a name="the-return-of-webconfig"></a><span data-ttu-id="34fb9-154">Le retour de web.config</span><span class="sxs-lookup"><span data-stu-id="34fb9-154">The return of web.config</span></span>

<span data-ttu-id="34fb9-155">Si vous avez déployé votre application sur Windows sur IIS, le fichier *web.config* configure toujours IIS pour gérer votre application.</span><span class="sxs-lookup"><span data-stu-id="34fb9-155">If you've deployed your app to Windows on IIS, the *web.config* file still configures IIS to manage your app.</span></span> <span data-ttu-id="34fb9-156">Par défaut, IIS ajoute une référence au module de base ASP.NET (ANCM).</span><span class="sxs-lookup"><span data-stu-id="34fb9-156">By default, IIS adds a reference to the ASP.NET Core Module (ANCM).</span></span> <span data-ttu-id="34fb9-157">ANCM est un module IIS natif qui héberge votre application à la place du serveur Web Kestrel.</span><span class="sxs-lookup"><span data-stu-id="34fb9-157">ANCM is a native IIS module that hosts your app in place of the Kestrel web server.</span></span> <span data-ttu-id="34fb9-158">Cette section *web.config* ressemble à la balisage XML suivante:</span><span class="sxs-lookup"><span data-stu-id="34fb9-158">This *web.config* section resembles the following XML markup:</span></span>

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

<span data-ttu-id="34fb9-159">La configuration spécifique à l’application `environmentVariables` peut `aspNetCore` être définie en niant un élément de l’élément.</span><span class="sxs-lookup"><span data-stu-id="34fb9-159">App-specific configuration can be defined by nesting an `environmentVariables` element in the `aspNetCore` element.</span></span> <span data-ttu-id="34fb9-160">Les valeurs définies dans cette section sont présentées à l’application ASP.NET Core comme variables de l’environnement.</span><span class="sxs-lookup"><span data-stu-id="34fb9-160">The values defined in this section are presented to the ASP.NET Core app as environment variables.</span></span> <span data-ttu-id="34fb9-161">Les variables de l’environnement se chargent de manière appropriée au cours de ce segment de démarrage d’applications.</span><span class="sxs-lookup"><span data-stu-id="34fb9-161">The environment variables load appropriately during that segment of app startup.</span></span>

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

## <a name="read-configuration-in-the-app"></a><span data-ttu-id="34fb9-162">Lire la configuration dans l’application</span><span class="sxs-lookup"><span data-stu-id="34fb9-162">Read configuration in the app</span></span>

<span data-ttu-id="34fb9-163">ASP.NET Core fournit la configuration <xref:Microsoft.Extensions.Configuration.IConfiguration> de l’application à travers l’interface.</span><span class="sxs-lookup"><span data-stu-id="34fb9-163">ASP.NET Core provides app configuration through the <xref:Microsoft.Extensions.Configuration.IConfiguration> interface.</span></span> <span data-ttu-id="34fb9-164">Cette interface de configuration doit être demandée par vos composants Blazor, pages Blazor et toute autre classe ASP.NET gérée par Core qui a besoin d’accéder à la configuration.</span><span class="sxs-lookup"><span data-stu-id="34fb9-164">This configuration interface should be requested by your Blazor components, Blazor pages, and any other ASP.NET Core-managed class that needs access to configuration.</span></span> <span data-ttu-id="34fb9-165">Le cadre ASP.NET Core remplira automatiquement cette interface avec la configuration résolue configurée plus tôt.</span><span class="sxs-lookup"><span data-stu-id="34fb9-165">The ASP.NET Core framework will automatically populate this interface with the resolved configuration configured earlier.</span></span> <span data-ttu-id="34fb9-166">Sur une page Blazor ou la balisage Razor `IConfiguration` d’un composant, vous pouvez injecter l’objet avec une `@inject` directive en haut du fichier *.razor* comme ceci:</span><span class="sxs-lookup"><span data-stu-id="34fb9-166">On a Blazor page or a component's Razor markup, you can inject the `IConfiguration` object with an `@inject` directive at the top of the *.razor* file like this:</span></span>

```razor
@inject IConfiguration Configuration
```

<span data-ttu-id="34fb9-167">Cette déclaration précédente `IConfiguration` rend l’objet disponible comme variable `Configuration` tout au long du reste du modèle Razor.</span><span class="sxs-lookup"><span data-stu-id="34fb9-167">This preceding statement makes the `IConfiguration` object available as the `Configuration` variable throughout the rest of the Razor template.</span></span>

<span data-ttu-id="34fb9-168">Les paramètres de configuration individuels peuvent être lus en spécifiant la hiérarchie de réglage de configuration recherchée comme paramètre d’indexeur :</span><span class="sxs-lookup"><span data-stu-id="34fb9-168">Individual configuration settings can be read by specifying the configuration setting hierarchy sought as an indexer parameter:</span></span>

```csharp
var mySetting = Configuration["section1:key0"];
```

<span data-ttu-id="34fb9-169">Vous pouvez aller chercher des <xref:Microsoft.Extensions.Configuration.IConfiguration.GetSection%2A> sections de configuration entières en utilisant la méthode `GetSection("section1")` pour récupérer une collection de clés à un endroit spécifique avec une syntaxe similaire à récupérer la configuration pour la section1 de l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="34fb9-169">You can fetch entire configuration sections by using the <xref:Microsoft.Extensions.Configuration.IConfiguration.GetSection%2A> method to retrieve a collection of keys at a specific location with a syntax similar to `GetSection("section1")` to retrieve the configuration for section1 from the earlier example.</span></span>

## <a name="strongly-typed-configuration"></a><span data-ttu-id="34fb9-170">Configuration fortement tapée</span><span class="sxs-lookup"><span data-stu-id="34fb9-170">Strongly typed configuration</span></span>

<span data-ttu-id="34fb9-171">Avec Web Forms, il a été possible de créer <xref:System.Configuration.ConfigurationSection> un type de configuration fortement tapé qui a hérité du type et des types associés.</span><span class="sxs-lookup"><span data-stu-id="34fb9-171">With Web Forms, it was possible to create a strongly typed configuration type that inherited from the <xref:System.Configuration.ConfigurationSection> type and associated types.</span></span> <span data-ttu-id="34fb9-172">A `ConfigurationSection` vous a permis de configurer certaines règles d’entreprise et le traitement de ces valeurs de configuration.</span><span class="sxs-lookup"><span data-stu-id="34fb9-172">A `ConfigurationSection` allowed you to configure some business rules and processing for those configuration values.</span></span>

<span data-ttu-id="34fb9-173">Dans ASP.NET Core, vous pouvez spécifier une hiérarchie de classe qui recevra les valeurs de configuration.</span><span class="sxs-lookup"><span data-stu-id="34fb9-173">In ASP.NET Core, you can specify a class hierarchy that will receive the configuration values.</span></span> <span data-ttu-id="34fb9-174">Ces classes:</span><span class="sxs-lookup"><span data-stu-id="34fb9-174">These classes:</span></span>

* <span data-ttu-id="34fb9-175">Vous n’avez pas besoin d’hériter d’une classe de parents.</span><span class="sxs-lookup"><span data-stu-id="34fb9-175">Don't need to inherit from a parent class.</span></span>
* <span data-ttu-id="34fb9-176">Devrait `public` inclure les propriétés qui correspondent aux propriétés et les références de type pour la structure de configuration que vous souhaitez capturer.</span><span class="sxs-lookup"><span data-stu-id="34fb9-176">Should include `public` properties that match the properties and type references for the configuration structure you wish to capture.</span></span>

<span data-ttu-id="34fb9-177">Pour l’échantillon *appsettings.json* antérieur, vous pouvez définir les classes suivantes pour capturer les valeurs :</span><span class="sxs-lookup"><span data-stu-id="34fb9-177">For the earlier *appsettings.json* sample, you could define the following classes to capture the values:</span></span>

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

<span data-ttu-id="34fb9-178">Cette hiérarchie de classe peut être peuplée `Startup.ConfigureServices` en ajoutant la ligne suivante à la méthode :</span><span class="sxs-lookup"><span data-stu-id="34fb9-178">This class hierarchy can be populated by adding the following line to the `Startup.ConfigureServices` method:</span></span>

```csharp
services.Configure<MyConfig>(Configuration);
```

<span data-ttu-id="34fb9-179">Dans le reste de l’application, vous pouvez `@inject` ajouter un paramètre `IOptions<MyConfig>` d’entrée aux classes ou une directive dans les modèles de type Razor pour recevoir les paramètres de configuration fortement tapés.</span><span class="sxs-lookup"><span data-stu-id="34fb9-179">In the rest of the app, you can add an input parameter to classes or an `@inject` directive in Razor templates of type `IOptions<MyConfig>` to receive the strongly typed configuration settings.</span></span> <span data-ttu-id="34fb9-180">La `IOptions<MyConfig>.Value` propriété produira `MyConfig` la valeur peuplée des paramètres de configuration.</span><span class="sxs-lookup"><span data-stu-id="34fb9-180">The `IOptions<MyConfig>.Value` property will yield the `MyConfig` value populated from the configuration settings.</span></span>

```razor
@inject IOptions<MyConfig> options
@code {
    var MyConfiguration = options.Value;
    var theSetting = MyConfiguration.section1.key0;
}
```

<span data-ttu-id="34fb9-181">Vous trouverez plus d’informations sur la fonction Options dans le modèle Options dans ASP.NET document [de base.](/aspnet/core/fundamentals/configuration/options#options-interfaces)</span><span class="sxs-lookup"><span data-stu-id="34fb9-181">More information about the Options feature can be found in the [Options pattern in ASP.NET Core](/aspnet/core/fundamentals/configuration/options#options-interfaces) document.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="34fb9-182">[Suivant précédent](middleware.md)
>[Next](security-authentication-authorization.md)</span><span class="sxs-lookup"><span data-stu-id="34fb9-182">[Previous](middleware.md)
[Next](security-authentication-authorization.md)</span></span>
