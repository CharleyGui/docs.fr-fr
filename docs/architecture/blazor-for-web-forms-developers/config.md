---
title: Configuration de l’application
description: Découvrez comment configurer des Blazor applications sans utiliser ConfigurationManager.
author: csharpfritz
ms.author: jefritz
no-loc:
- Blazor
ms.date: 11/20/2020
ms.openlocfilehash: 360d9077bc981a2e9875bb1f86b49c0029424d6e
ms.sourcegitcommit: 2f485e721f7f34b87856a51181b5b56624b31fd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2020
ms.locfileid: "96509791"
---
# <a name="app-configuration"></a><span data-ttu-id="879a6-103">Configuration de l’application</span><span class="sxs-lookup"><span data-stu-id="879a6-103">App configuration</span></span>

<span data-ttu-id="879a6-104">Le principal moyen de charger la configuration de l’application dans Web Forms consiste à utiliser des entrées dans le fichier *web.config* &mdash; , soit sur le serveur, soit sur un fichier de configuration associé référencé par *web.config*. Vous pouvez utiliser l' `ConfigurationManager` objet statique pour interagir avec les paramètres d’application, les chaînes de connexion du référentiel de données et d’autres fournisseurs de configuration étendus ajoutés à l’application.</span><span class="sxs-lookup"><span data-stu-id="879a6-104">The primary way to load app configuration in Web Forms is with entries in the *web.config* file&mdash;either on the server or a related configuration file referenced by *web.config*. You can use the static `ConfigurationManager` object to interact with app settings, data repository connection strings, and other extended configuration providers that are added into the app.</span></span> <span data-ttu-id="879a6-105">Il est courant de voir les interactions avec la configuration d’application comme indiqué dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="879a6-105">It's typical to see interactions with app configuration as seen in the following code:</span></span>

```csharp
var configurationValue = ConfigurationManager.AppSettings["ConfigurationSettingName"];
var connectionString = ConfigurationManager.ConnectionStrings["MyDatabaseConnectionName"].ConnectionString;
```

<span data-ttu-id="879a6-106">Avec ASP.NET Core et côté serveur Blazor , le fichier *web.config* peut être présent si votre application est hébergée sur un serveur IIS Windows.</span><span class="sxs-lookup"><span data-stu-id="879a6-106">With ASP.NET Core and server-side Blazor, the *web.config* file MAY be present if your app is hosted on a Windows IIS server.</span></span> <span data-ttu-id="879a6-107">Toutefois, il n’y a aucune `ConfigurationManager` interaction avec cette configuration, et vous pouvez recevoir une configuration d’application plus structurée à partir d’autres sources.</span><span class="sxs-lookup"><span data-stu-id="879a6-107">However, there's no `ConfigurationManager` interaction with this configuration, and you can receive more structured app configuration from other sources.</span></span> <span data-ttu-id="879a6-108">Voyons comment la configuration est collectée et comment vous pouvez toujours accéder aux informations de configuration à partir d’un fichier de *web.config* .</span><span class="sxs-lookup"><span data-stu-id="879a6-108">Let's take a look at how configuration is gathered and how you can still access configuration information from a *web.config* file.</span></span>

## <a name="configuration-sources"></a><span data-ttu-id="879a6-109">Sources de configuration</span><span class="sxs-lookup"><span data-stu-id="879a6-109">Configuration sources</span></span>

<span data-ttu-id="879a6-110">ASP.NET Core reconnaît qu’il existe de nombreuses sources de configuration que vous pouvez utiliser pour votre application.</span><span class="sxs-lookup"><span data-stu-id="879a6-110">ASP.NET Core recognizes there are many configuration sources you may want to use for your app.</span></span> <span data-ttu-id="879a6-111">Le Framework tente de vous offrir le meilleur de ces fonctionnalités par défaut.</span><span class="sxs-lookup"><span data-stu-id="879a6-111">The framework attempts to offer you the best of these features by default.</span></span> <span data-ttu-id="879a6-112">La configuration est lue et agrégée à partir de ces diverses sources par ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="879a6-112">Configuration is read and aggregated from these various sources by ASP.NET Core.</span></span> <span data-ttu-id="879a6-113">Les valeurs chargées ultérieurement pour la même clé de configuration sont prioritaires par rapport aux valeurs antérieures.</span><span class="sxs-lookup"><span data-stu-id="879a6-113">Later loaded values for the same configuration key take precedence over earlier values.</span></span>

<span data-ttu-id="879a6-114">ASP.NET Core a été conçu pour être compatible avec le Cloud et pour faciliter la configuration des applications pour les opérateurs et les développeurs.</span><span class="sxs-lookup"><span data-stu-id="879a6-114">ASP.NET Core was designed to be cloud-aware and to make the configuration of apps easier for both operators and developers.</span></span> <span data-ttu-id="879a6-115">ASP.NET Core prend en charge l’environnement et sait s’il s’exécute dans `Production` votre `Development` environnement ou.</span><span class="sxs-lookup"><span data-stu-id="879a6-115">ASP.NET Core is environment-aware and knows if it's running in your `Production` or `Development` environment.</span></span> <span data-ttu-id="879a6-116">L’indicateur d’environnement est défini dans la `ASPNETCORE_ENVIRONMENT` variable d’environnement système.</span><span class="sxs-lookup"><span data-stu-id="879a6-116">The environment indicator is set in the `ASPNETCORE_ENVIRONMENT` system environment variable.</span></span> <span data-ttu-id="879a6-117">Si aucune valeur n’est configurée, l’application est exécutée par défaut dans l' `Production` environnement.</span><span class="sxs-lookup"><span data-stu-id="879a6-117">If no value is configured, the app defaults to running in the `Production` environment.</span></span>

<span data-ttu-id="879a6-118">Votre application peut déclencher et ajouter une configuration à partir de plusieurs sources en fonction du nom de l’environnement.</span><span class="sxs-lookup"><span data-stu-id="879a6-118">Your app can trigger and add configuration from several sources based on the environment's name.</span></span> <span data-ttu-id="879a6-119">Par défaut, la configuration est chargée à partir des ressources suivantes dans l’ordre indiqué :</span><span class="sxs-lookup"><span data-stu-id="879a6-119">By default, the configuration is loaded from the following resources in the order listed:</span></span>

1. <span data-ttu-id="879a6-120">*appsettings.js* fichier, s’il est présent</span><span class="sxs-lookup"><span data-stu-id="879a6-120">*appsettings.json* file, if present</span></span>
1. <span data-ttu-id="879a6-121">*appSettings. Fichier {ENVIRONMENT_NAME}. JSON* , s’il est présent</span><span class="sxs-lookup"><span data-stu-id="879a6-121">*appsettings.{ENVIRONMENT_NAME}.json* file, if present</span></span>
1. <span data-ttu-id="879a6-122">Fichier de secrets de l’utilisateur sur le disque, le cas échéant</span><span class="sxs-lookup"><span data-stu-id="879a6-122">User secrets file on disk, if present</span></span>
1. <span data-ttu-id="879a6-123">Variables d'environnement</span><span class="sxs-lookup"><span data-stu-id="879a6-123">Environment variables</span></span>
1. <span data-ttu-id="879a6-124">Arguments de ligne de commande</span><span class="sxs-lookup"><span data-stu-id="879a6-124">Command-line arguments</span></span>

## <a name="appsettingsjson-format-and-access"></a><span data-ttu-id="879a6-125">appsettings.jsau format et à l’accès</span><span class="sxs-lookup"><span data-stu-id="879a6-125">appsettings.json format and access</span></span>

<span data-ttu-id="879a6-126">La *appsettings.jssur* le fichier peut être hiérarchique avec des valeurs structurées comme le JSON suivant :</span><span class="sxs-lookup"><span data-stu-id="879a6-126">The *appsettings.json* file can be hierarchical with values structured like the following JSON:</span></span>

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

<span data-ttu-id="879a6-127">Lorsqu’il est présenté avec le code JSON précédent, le système de configuration aplatit les valeurs enfants et référence leurs chemins d’accès hiérarchiques complets.</span><span class="sxs-lookup"><span data-stu-id="879a6-127">When presented with the preceding JSON, the configuration system flattens child values and references their fully qualified hierarchical paths.</span></span> <span data-ttu-id="879a6-128">Un caractère deux-points ( `:` ) sépare chaque propriété de la hiérarchie.</span><span class="sxs-lookup"><span data-stu-id="879a6-128">A colon (`:`) character separates each property in the hierarchy.</span></span> <span data-ttu-id="879a6-129">Par exemple, la clé de configuration `section1:key0` accède à la `section1` valeur du littéral d’objet `key0` .</span><span class="sxs-lookup"><span data-stu-id="879a6-129">For example, the configuration key `section1:key0` accesses the `section1` object literal's `key0` value.</span></span>

## <a name="user-secrets"></a><span data-ttu-id="879a6-130">Secrets utilisateur</span><span class="sxs-lookup"><span data-stu-id="879a6-130">User secrets</span></span>

<span data-ttu-id="879a6-131">Secrets de l’utilisateur :</span><span class="sxs-lookup"><span data-stu-id="879a6-131">User secrets are:</span></span>

* <span data-ttu-id="879a6-132">Valeurs de configuration qui sont stockées dans un fichier JSON sur la station de travail du développeur, en dehors du dossier de développement de l’application.</span><span class="sxs-lookup"><span data-stu-id="879a6-132">Configuration values that are stored in a JSON file on the developer's workstation, outside of the app development folder.</span></span>
* <span data-ttu-id="879a6-133">Chargé uniquement lors de l’exécution dans l' `Development` environnement.</span><span class="sxs-lookup"><span data-stu-id="879a6-133">Only loaded when running in the `Development` environment.</span></span>
* <span data-ttu-id="879a6-134">Associé à une application spécifique.</span><span class="sxs-lookup"><span data-stu-id="879a6-134">Associated with a specific app.</span></span>
* <span data-ttu-id="879a6-135">Gérée à l’aide de la commande de l’interface CLI .NET `user-secrets` .</span><span class="sxs-lookup"><span data-stu-id="879a6-135">Managed with the .NET CLI's `user-secrets` command.</span></span>

<span data-ttu-id="879a6-136">Configurez votre application pour le stockage des secrets en exécutant la `user-secrets` commande suivante :</span><span class="sxs-lookup"><span data-stu-id="879a6-136">Configure your app for secrets storage by executing the `user-secrets` command:</span></span>

```dotnetcli
dotnet user-secrets init
```

<span data-ttu-id="879a6-137">La commande précédente ajoute un `UserSecretsId` élément au fichier projet.</span><span class="sxs-lookup"><span data-stu-id="879a6-137">The preceding command adds a `UserSecretsId` element to the project file.</span></span> <span data-ttu-id="879a6-138">L’élément contient un GUID, qui est utilisé pour associer des secrets à l’application.</span><span class="sxs-lookup"><span data-stu-id="879a6-138">The element contains a GUID, which is used to associate secrets with the app.</span></span> <span data-ttu-id="879a6-139">Vous pouvez ensuite définir une clé secrète à l’aide de la `set` commande.</span><span class="sxs-lookup"><span data-stu-id="879a6-139">You can then define a secret with the `set` command.</span></span> <span data-ttu-id="879a6-140">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="879a6-140">For example:</span></span>

```dotnetcli
dotnet user-secrets set "Parent:ApiKey" "12345"
```

<span data-ttu-id="879a6-141">La commande précédente rend la `Parent:ApiKey` clé de configuration disponible sur la station de travail d’un développeur avec la valeur `12345` .</span><span class="sxs-lookup"><span data-stu-id="879a6-141">The preceding command makes the `Parent:ApiKey` configuration key available on a developer's workstation with the value `12345`.</span></span>

<span data-ttu-id="879a6-142">Pour plus d’informations sur la création, le stockage et la gestion des secrets d’utilisateur, consultez la page [stockage sécurisé des secrets d’application en développement dans ASP.net Core](/aspnet/core/security/app-secrets) document.</span><span class="sxs-lookup"><span data-stu-id="879a6-142">For more information about creating, storing, and managing user secrets, see the [Safe storage of app secrets in development in ASP.NET Core](/aspnet/core/security/app-secrets) document.</span></span>

## <a name="environment-variables"></a><span data-ttu-id="879a6-143">Variables d'environnement</span><span class="sxs-lookup"><span data-stu-id="879a6-143">Environment variables</span></span>

<span data-ttu-id="879a6-144">L’ensemble suivant de valeurs chargées dans la configuration de votre application est les variables d’environnement du système.</span><span class="sxs-lookup"><span data-stu-id="879a6-144">The next set of values loaded into your app configuration is the system's environment variables.</span></span> <span data-ttu-id="879a6-145">Tous les paramètres de la variable d’environnement de votre système sont désormais accessibles via l’API de configuration.</span><span class="sxs-lookup"><span data-stu-id="879a6-145">All of your system's environment variable settings are now accessible to you through the configuration API.</span></span> <span data-ttu-id="879a6-146">Les valeurs hiérarchiques sont aplaties et séparées par deux-points quand elles sont lues à l’intérieur de votre application.</span><span class="sxs-lookup"><span data-stu-id="879a6-146">Hierarchical values are flattened and separated by colon characters when read inside your app.</span></span> <span data-ttu-id="879a6-147">Toutefois, certains systèmes d’exploitation n’autorisent pas les noms de variables d’environnement de deux-points.</span><span class="sxs-lookup"><span data-stu-id="879a6-147">However, some operating systems don't allow the colon character environment variable names.</span></span> <span data-ttu-id="879a6-148">ASP.NET Core résout cette limitation en convertissant les valeurs qui comportent des traits de soulignement doubles ( `__` ) en deux-points lorsque vous y accédez.</span><span class="sxs-lookup"><span data-stu-id="879a6-148">ASP.NET Core addresses this limitation by converting values that have double-underscores (`__`) into a colon when they're accessed.</span></span> <span data-ttu-id="879a6-149">La `Parent:ApiKey` valeur de la section secrets de l’utilisateur ci-dessus peut être remplacée par la variable d’environnement `Parent__ApiKey` .</span><span class="sxs-lookup"><span data-stu-id="879a6-149">The `Parent:ApiKey` value from the user secrets section above can be overridden with the environment variable `Parent__ApiKey`.</span></span>

## <a name="command-line-arguments"></a><span data-ttu-id="879a6-150">Arguments de ligne de commande</span><span class="sxs-lookup"><span data-stu-id="879a6-150">Command-line arguments</span></span>

<span data-ttu-id="879a6-151">La configuration peut également être fournie en tant qu’arguments de ligne de commande au démarrage de votre application.</span><span class="sxs-lookup"><span data-stu-id="879a6-151">Configuration can also be provided as command-line arguments when your app is started.</span></span> <span data-ttu-id="879a6-152">Utilisez la notation double tiret ( `--` ) ou la barre oblique ( `/` ) pour indiquer le nom de la valeur de configuration à définir et la valeur à configurer.</span><span class="sxs-lookup"><span data-stu-id="879a6-152">Use the double-dash (`--`) or forward-slash (`/`) notation to indicate the name of the configuration value to set and the value to be configured.</span></span> <span data-ttu-id="879a6-153">La syntaxe ressemble aux commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="879a6-153">The syntax resembles the following commands:</span></span>

```dotnetcli
dotnet run CommandLineKey1=value1 --CommandLineKey2=value2 /CommandLineKey3=value3
dotnet run --CommandLineKey1 value1 /CommandLineKey2 value2
dotnet run Parent:ApiKey=67890
```

## <a name="the-return-of-webconfig"></a><span data-ttu-id="879a6-154">Retour de web.config</span><span class="sxs-lookup"><span data-stu-id="879a6-154">The return of web.config</span></span>

<span data-ttu-id="879a6-155">Si vous avez déployé votre application sur Windows sur IIS, le fichier *web.config* configure toujours IIS pour gérer votre application.</span><span class="sxs-lookup"><span data-stu-id="879a6-155">If you've deployed your app to Windows on IIS, the *web.config* file still configures IIS to manage your app.</span></span> <span data-ttu-id="879a6-156">Par défaut, IIS ajoute une référence au module ASP.NET Core (ANCM).</span><span class="sxs-lookup"><span data-stu-id="879a6-156">By default, IIS adds a reference to the ASP.NET Core Module (ANCM).</span></span> <span data-ttu-id="879a6-157">ANCM est un module IIS natif qui héberge votre application à la place du serveur Web Kestrel.</span><span class="sxs-lookup"><span data-stu-id="879a6-157">ANCM is a native IIS module that hosts your app in place of the Kestrel web server.</span></span> <span data-ttu-id="879a6-158">Cette *web.config* section ressemble au balisage XML suivant :</span><span class="sxs-lookup"><span data-stu-id="879a6-158">This *web.config* section resembles the following XML markup:</span></span>

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

<span data-ttu-id="879a6-159">La configuration spécifique à l’application peut être définie en imbriquant un `environmentVariables` élément dans l' `aspNetCore` élément.</span><span class="sxs-lookup"><span data-stu-id="879a6-159">App-specific configuration can be defined by nesting an `environmentVariables` element in the `aspNetCore` element.</span></span> <span data-ttu-id="879a6-160">Les valeurs définies dans cette section sont présentées à l’application ASP.NET Core en tant que variables d’environnement.</span><span class="sxs-lookup"><span data-stu-id="879a6-160">The values defined in this section are presented to the ASP.NET Core app as environment variables.</span></span> <span data-ttu-id="879a6-161">Les variables d’environnement sont chargées correctement au cours de ce segment de démarrage de l’application.</span><span class="sxs-lookup"><span data-stu-id="879a6-161">The environment variables load appropriately during that segment of app startup.</span></span>

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

## <a name="read-configuration-in-the-app"></a><span data-ttu-id="879a6-162">Lire la configuration dans l’application</span><span class="sxs-lookup"><span data-stu-id="879a6-162">Read configuration in the app</span></span>

<span data-ttu-id="879a6-163">ASP.NET Core fournit la configuration de l’application par le biais de l' <xref:Microsoft.Extensions.Configuration.IConfiguration> interface.</span><span class="sxs-lookup"><span data-stu-id="879a6-163">ASP.NET Core provides app configuration through the <xref:Microsoft.Extensions.Configuration.IConfiguration> interface.</span></span> <span data-ttu-id="879a6-164">Cette interface de configuration doit être demandée par vos Blazor composants, Blazor pages et toute autre classe gérée par ASP.net core qui a besoin d’accéder à la configuration.</span><span class="sxs-lookup"><span data-stu-id="879a6-164">This configuration interface should be requested by your Blazor components, Blazor pages, and any other ASP.NET Core-managed class that needs access to configuration.</span></span> <span data-ttu-id="879a6-165">Le ASP.NET Core Framework remplira automatiquement cette interface avec la configuration résolue configurée précédemment.</span><span class="sxs-lookup"><span data-stu-id="879a6-165">The ASP.NET Core framework will automatically populate this interface with the resolved configuration configured earlier.</span></span> <span data-ttu-id="879a6-166">Sur une Blazor page ou un balisage Razor d’un composant, vous pouvez injecter l' `IConfiguration` objet avec une `@inject` directive en haut du fichier *. Razor* , comme suit :</span><span class="sxs-lookup"><span data-stu-id="879a6-166">On a Blazor page or a component's Razor markup, you can inject the `IConfiguration` object with an `@inject` directive at the top of the *.razor* file like this:</span></span>

```razor
@inject IConfiguration Configuration
```

<span data-ttu-id="879a6-167">Cette instruction précédente rend l' `IConfiguration` objet disponible en tant que `Configuration` variable dans le reste du modèle Razor.</span><span class="sxs-lookup"><span data-stu-id="879a6-167">This preceding statement makes the `IConfiguration` object available as the `Configuration` variable throughout the rest of the Razor template.</span></span>

<span data-ttu-id="879a6-168">Les paramètres de configuration individuels peuvent être lus en spécifiant la hiérarchie des paramètres de configuration recherchée comme paramètre d’indexeur :</span><span class="sxs-lookup"><span data-stu-id="879a6-168">Individual configuration settings can be read by specifying the configuration setting hierarchy sought as an indexer parameter:</span></span>

```csharp
var mySetting = Configuration["section1:key0"];
```

<span data-ttu-id="879a6-169">Vous pouvez extraire des sections de configuration entières à l’aide de la <xref:Microsoft.Extensions.Configuration.IConfiguration.GetSection%2A> méthode pour récupérer une collection de clés à un emplacement spécifique à l’aide d’une syntaxe similaire à pour `GetSection("section1")` récupérer la configuration de Section1 dans l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="879a6-169">You can fetch entire configuration sections by using the <xref:Microsoft.Extensions.Configuration.IConfiguration.GetSection%2A> method to retrieve a collection of keys at a specific location with a syntax similar to `GetSection("section1")` to retrieve the configuration for section1 from the earlier example.</span></span>

## <a name="strongly-typed-configuration"></a><span data-ttu-id="879a6-170">Configuration fortement typée</span><span class="sxs-lookup"><span data-stu-id="879a6-170">Strongly typed configuration</span></span>

<span data-ttu-id="879a6-171">Avec Web Forms, il était possible de créer un type de configuration fortement typé hérité du <xref:System.Configuration.ConfigurationSection> type et des types associés.</span><span class="sxs-lookup"><span data-stu-id="879a6-171">With Web Forms, it was possible to create a strongly typed configuration type that inherited from the <xref:System.Configuration.ConfigurationSection> type and associated types.</span></span> <span data-ttu-id="879a6-172">`ConfigurationSection`Vous permettait de configurer certaines règles d’entreprise et le traitement de ces valeurs de configuration.</span><span class="sxs-lookup"><span data-stu-id="879a6-172">A `ConfigurationSection` allowed you to configure some business rules and processing for those configuration values.</span></span>

<span data-ttu-id="879a6-173">Dans ASP.NET Core, vous pouvez spécifier une hiérarchie de classes qui recevra les valeurs de configuration.</span><span class="sxs-lookup"><span data-stu-id="879a6-173">In ASP.NET Core, you can specify a class hierarchy that will receive the configuration values.</span></span> <span data-ttu-id="879a6-174">Ces classes :</span><span class="sxs-lookup"><span data-stu-id="879a6-174">These classes:</span></span>

* <span data-ttu-id="879a6-175">Il n’est pas nécessaire d’hériter d’une classe parente.</span><span class="sxs-lookup"><span data-stu-id="879a6-175">Don't need to inherit from a parent class.</span></span>
* <span data-ttu-id="879a6-176">Doit inclure `public` des propriétés qui correspondent aux propriétés et aux références de type pour la structure de configuration que vous souhaitez capturer.</span><span class="sxs-lookup"><span data-stu-id="879a6-176">Should include `public` properties that match the properties and type references for the configuration structure you wish to capture.</span></span>

<span data-ttu-id="879a6-177">Pour le *appsettings.jsprécédent sur* l’exemple, vous pouvez définir les classes suivantes pour capturer les valeurs :</span><span class="sxs-lookup"><span data-stu-id="879a6-177">For the earlier *appsettings.json* sample, you could define the following classes to capture the values:</span></span>

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

<span data-ttu-id="879a6-178">Cette hiérarchie de classes peut être remplie en ajoutant la ligne suivante à la `Startup.ConfigureServices` méthode :</span><span class="sxs-lookup"><span data-stu-id="879a6-178">This class hierarchy can be populated by adding the following line to the `Startup.ConfigureServices` method:</span></span>

```csharp
services.Configure<MyConfig>(Configuration);
```

<span data-ttu-id="879a6-179">Dans le reste de l’application, vous pouvez ajouter un paramètre d’entrée aux classes ou à une `@inject` directive dans les modèles Razor de type `IOptions<MyConfig>` pour recevoir les paramètres de configuration fortement typés.</span><span class="sxs-lookup"><span data-stu-id="879a6-179">In the rest of the app, you can add an input parameter to classes or an `@inject` directive in Razor templates of type `IOptions<MyConfig>` to receive the strongly typed configuration settings.</span></span> <span data-ttu-id="879a6-180">La `IOptions<MyConfig>.Value` propriété produira la `MyConfig` valeur remplie à partir des paramètres de configuration.</span><span class="sxs-lookup"><span data-stu-id="879a6-180">The `IOptions<MyConfig>.Value` property will yield the `MyConfig` value populated from the configuration settings.</span></span>

```razor
@inject IOptions<MyConfig> options
@code {
    var MyConfiguration = options.Value;
    var theSetting = MyConfiguration.section1.key0;
}
```

<span data-ttu-id="879a6-181">Vous trouverez plus d’informations sur la fonctionnalité options dans le [modèle options de ASP.net Core](/aspnet/core/fundamentals/configuration/options#options-interfaces) document.</span><span class="sxs-lookup"><span data-stu-id="879a6-181">More information about the Options feature can be found in the [Options pattern in ASP.NET Core](/aspnet/core/fundamentals/configuration/options#options-interfaces) document.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="879a6-182">[Précédent](middleware.md) 
> [Suivant](security-authentication-authorization.md)</span><span class="sxs-lookup"><span data-stu-id="879a6-182">[Previous](middleware.md)
[Next](security-authentication-authorization.md)</span></span>
