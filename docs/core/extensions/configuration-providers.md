---
title: Fournisseurs de configuration dans .NET
description: Découvrez comment l’API du fournisseur de configuration est utilisée pour configurer des applications .NET.
author: IEvangelist
ms.author: dapine
ms.date: 12/04/2020
ms.openlocfilehash: 036eb403318200bc0ae1d93e2c7cf9d074cb0bfb
ms.sourcegitcommit: 88fbb019b84c2d044d11fb4f6004aec07f2b25b1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97899446"
---
# <a name="configuration-providers-in-net"></a><span data-ttu-id="b4d88-103">Fournisseurs de configuration dans .NET</span><span class="sxs-lookup"><span data-stu-id="b4d88-103">Configuration providers in .NET</span></span>

<span data-ttu-id="b4d88-104">La configuration dans .NET est possible avec les fournisseurs de configuration.</span><span class="sxs-lookup"><span data-stu-id="b4d88-104">Configuration in .NET is possible with configuration providers.</span></span> <span data-ttu-id="b4d88-105">Il existe plusieurs types de fournisseurs qui reposent sur différentes sources de configuration.</span><span class="sxs-lookup"><span data-stu-id="b4d88-105">There are several types of providers that rely on various configuration sources.</span></span> <span data-ttu-id="b4d88-106">Cet article détaille tous les différents fournisseurs de configuration et leurs sources correspondantes.</span><span class="sxs-lookup"><span data-stu-id="b4d88-106">This article details all of the different configuration providers and their corresponding sources.</span></span>

- [<span data-ttu-id="b4d88-107">Fournisseur de configuration de fichier</span><span class="sxs-lookup"><span data-stu-id="b4d88-107">File configuration provider</span></span>](#file-configuration-provider)
- [<span data-ttu-id="b4d88-108">Fournisseur de configuration de variable d’environnement</span><span class="sxs-lookup"><span data-stu-id="b4d88-108">Environment variable configuration provider</span></span>](#environment-variable-configuration-provider)
- [<span data-ttu-id="b4d88-109">Fournisseur de configuration de ligne de commande</span><span class="sxs-lookup"><span data-stu-id="b4d88-109">Command-line configuration provider</span></span>](#command-line-configuration-provider)
- [<span data-ttu-id="b4d88-110">Fournisseur de configuration de clé par fichier</span><span class="sxs-lookup"><span data-stu-id="b4d88-110">Key-per-file configuration provider</span></span>](#key-per-file-configuration-provider)
- [<span data-ttu-id="b4d88-111">Fournisseur de configuration de la mémoire</span><span class="sxs-lookup"><span data-stu-id="b4d88-111">Memory configuration provider</span></span>](#memory-configuration-provider)

## <a name="file-configuration-provider"></a><span data-ttu-id="b4d88-112">Fournisseur de configuration de fichier</span><span class="sxs-lookup"><span data-stu-id="b4d88-112">File configuration provider</span></span>

<span data-ttu-id="b4d88-113"><xref:Microsoft.Extensions.Configuration.FileConfigurationProvider> est la classe de base pour charger la configuration à partir du système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="b4d88-113"><xref:Microsoft.Extensions.Configuration.FileConfigurationProvider> is the base class for loading configuration from the file system.</span></span> <span data-ttu-id="b4d88-114">Les fournisseurs de configuration suivants dérivent de `FileConfigurationProvider` :</span><span class="sxs-lookup"><span data-stu-id="b4d88-114">The following configuration providers derive from `FileConfigurationProvider`:</span></span>

- [<span data-ttu-id="b4d88-115">Fournisseur de configuration JSON</span><span class="sxs-lookup"><span data-stu-id="b4d88-115">JSON configuration provider</span></span>](#json-configuration-provider)
- [<span data-ttu-id="b4d88-116">Fournisseur de configuration XML</span><span class="sxs-lookup"><span data-stu-id="b4d88-116">XML configuration provider</span></span>](#xml-configuration-provider)
- [<span data-ttu-id="b4d88-117">Fournisseur de configuration INI</span><span class="sxs-lookup"><span data-stu-id="b4d88-117">INI configuration provider</span></span>](#ini-configuration-provider)

### <a name="json-configuration-provider"></a><span data-ttu-id="b4d88-118">Fournisseur de configuration JSON</span><span class="sxs-lookup"><span data-stu-id="b4d88-118">JSON configuration provider</span></span>

<span data-ttu-id="b4d88-119">La <xref:Microsoft.Extensions.Configuration.Json.JsonConfigurationProvider> classe charge la configuration à partir d’un fichier JSON.</span><span class="sxs-lookup"><span data-stu-id="b4d88-119">The <xref:Microsoft.Extensions.Configuration.Json.JsonConfigurationProvider> class loads configuration from a JSON file.</span></span> <span data-ttu-id="b4d88-120">Installez le [`Microsoft.Extensions.Configuration.Json`](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.Json) package NuGet.</span><span class="sxs-lookup"><span data-stu-id="b4d88-120">Install the [`Microsoft.Extensions.Configuration.Json`](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.Json) NuGet package.</span></span>

<span data-ttu-id="b4d88-121">Les surcharges peuvent spécifier :</span><span class="sxs-lookup"><span data-stu-id="b4d88-121">Overloads can specify:</span></span>

- <span data-ttu-id="b4d88-122">Indique si le fichier est facultatif</span><span class="sxs-lookup"><span data-stu-id="b4d88-122">Whether the file is optional</span></span>
- <span data-ttu-id="b4d88-123">Si la configuration est rechargée en cas de modification du fichier</span><span class="sxs-lookup"><span data-stu-id="b4d88-123">Whether the configuration is reloaded if the file changes</span></span>

<span data-ttu-id="b4d88-124">Considérez le code suivant :</span><span class="sxs-lookup"><span data-stu-id="b4d88-124">Consider the following code:</span></span>

:::code language="csharp" source="snippets/configuration/console-json/Program.cs" range="1-39,43-44" highlight="23-29":::

<span data-ttu-id="b4d88-125">Le code précédent :</span><span class="sxs-lookup"><span data-stu-id="b4d88-125">The preceding code:</span></span>

- <span data-ttu-id="b4d88-126">Efface tous les fournisseurs de configuration existants qui ont été ajoutés par défaut dans la <xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder(System.String[])> méthode.</span><span class="sxs-lookup"><span data-stu-id="b4d88-126">Clears all existing configuration providers that were added by default in the <xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder(System.String[])> method.</span></span>
- <span data-ttu-id="b4d88-127">Configure le fournisseur de configuration JSON pour charger le *appsettings.jssur* et  *appSettings*. `Environment` fichiers *JSON* avec les options suivantes :</span><span class="sxs-lookup"><span data-stu-id="b4d88-127">Configures the JSON configuration provider to load the *appsettings.json* and  *appsettings*.`Environment`.*json* files with the following options:</span></span>
  - <span data-ttu-id="b4d88-128">`optional: true`: Le fichier est facultatif.</span><span class="sxs-lookup"><span data-stu-id="b4d88-128">`optional: true`: The file is optional.</span></span>
  - <span data-ttu-id="b4d88-129">`reloadOnChange: true` : Le fichier est rechargé lorsque des modifications sont enregistrées.</span><span class="sxs-lookup"><span data-stu-id="b4d88-129">`reloadOnChange: true` : The file is reloaded when changes are saved.</span></span>

<span data-ttu-id="b4d88-130">Les paramètres JSON sont remplacés par les paramètres dans le [fournisseur de configuration des variables d’environnement](#environment-variable-configuration-provider) et le [fournisseur de configuration de ligne de commande](#command-line-configuration-provider).</span><span class="sxs-lookup"><span data-stu-id="b4d88-130">The JSON settings are overridden by settings in the [Environment variables configuration provider](#environment-variable-configuration-provider) and the [Command-line configuration provider](#command-line-configuration-provider).</span></span>

<span data-ttu-id="b4d88-131">Voici un exemple *appsettings.jssur* un fichier avec différents paramètres de configuration :</span><span class="sxs-lookup"><span data-stu-id="b4d88-131">An example *appsettings.json* file with various configuration settings follows:</span></span>

:::code language="json" source="snippets/configuration/console-json/appsettings.json":::

<span data-ttu-id="b4d88-132">À partir de l' <xref:Microsoft.Extensions.Configuration.IConfigurationBuilder> instance, après avoir ajouté des fournisseurs de configuration, vous pouvez appeler <xref:Microsoft.Extensions.Configuration.IConfigurationBuilder.Build?displayProperty=nameWithType> pour obtenir l' <xref:Microsoft.Extensions.Configuration.IConfigurationRoot> objet.</span><span class="sxs-lookup"><span data-stu-id="b4d88-132">From the <xref:Microsoft.Extensions.Configuration.IConfigurationBuilder> instance, after configuration providers have been added you can call <xref:Microsoft.Extensions.Configuration.IConfigurationBuilder.Build?displayProperty=nameWithType> to get the <xref:Microsoft.Extensions.Configuration.IConfigurationRoot> object.</span></span> <span data-ttu-id="b4d88-133">La racine de configuration représente la racine d’une hiérarchie de configuration.</span><span class="sxs-lookup"><span data-stu-id="b4d88-133">The configuration root represents the root of a configuration hierarchy.</span></span> <span data-ttu-id="b4d88-134">Les sections de la configuration peuvent être liées à des instances d’objets .NET, et fournies ultérieurement comme par le biais de l' <xref:Microsoft.Extensions.Options.IOptions%601> injection de dépendances.</span><span class="sxs-lookup"><span data-stu-id="b4d88-134">Sections from the configuration can be bound to instances of .NET objects, and later provided as <xref:Microsoft.Extensions.Options.IOptions%601> through dependency injection.</span></span>

<span data-ttu-id="b4d88-135">Prenons le `TransientFaultHandlingOptions` type d’enregistrement défini comme suit :</span><span class="sxs-lookup"><span data-stu-id="b4d88-135">Consider the `TransientFaultHandlingOptions` record type defined as follows:</span></span>

:::code language="csharp" source="snippets/configuration/console-json/TransientFaultHandlingOptions.cs":::

<span data-ttu-id="b4d88-136">Pour plus d’informations sur les types d’enregistrements, consultez [types d’enregistrements en C# 9](../../csharp/whats-new/csharp-9.md#record-types).</span><span class="sxs-lookup"><span data-stu-id="b4d88-136">For information on record types, see [Record types in C# 9](../../csharp/whats-new/csharp-9.md#record-types).</span></span>

<span data-ttu-id="b4d88-137">Le code suivant génère la racine de configuration, lie une section au `TransientFaultHandlingOptions` type d’enregistrement et imprime les valeurs liées dans la fenêtre de console :</span><span class="sxs-lookup"><span data-stu-id="b4d88-137">The following code builds the configuration root, binds a section to the `TransientFaultHandlingOptions` record type, and prints the bound values to the console window:</span></span>

:::code language="csharp" source="snippets/configuration/console-json/Program.cs" range="31-38":::

<span data-ttu-id="b4d88-138">L’application écrirait l’exemple de sortie suivant :</span><span class="sxs-lookup"><span data-stu-id="b4d88-138">The application would write the following sample output:</span></span>

:::code language="csharp" source="snippets/configuration/console-json/Program.cs" range="40-42":::

### <a name="xml-configuration-provider"></a><span data-ttu-id="b4d88-139">Fournisseur de configuration XML</span><span class="sxs-lookup"><span data-stu-id="b4d88-139">XML configuration provider</span></span>

<span data-ttu-id="b4d88-140">La <xref:Microsoft.Extensions.Configuration.Xml.XmlConfigurationProvider> classe charge la configuration à partir d’un fichier XML au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="b4d88-140">The <xref:Microsoft.Extensions.Configuration.Xml.XmlConfigurationProvider> class loads configuration from an XML file at runtime.</span></span> <span data-ttu-id="b4d88-141">Installez le [`Microsoft.Extensions.Configuration.Xml`](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.Xml) package NuGet.</span><span class="sxs-lookup"><span data-stu-id="b4d88-141">Install the [`Microsoft.Extensions.Configuration.Xml`](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.Xml) NuGet package.</span></span>

<span data-ttu-id="b4d88-142">Le code suivant illustre la configuration de fichiers XML à l’aide du fournisseur de configuration XML.</span><span class="sxs-lookup"><span data-stu-id="b4d88-142">The following code demonstrates configuration of XML files using the XML configuration provider.</span></span>

:::code language="csharp" source="snippets/configuration/console-xml/Program.cs" range="1-34,52,58-59" highlight="23-34":::

<span data-ttu-id="b4d88-143">Le code précédent :</span><span class="sxs-lookup"><span data-stu-id="b4d88-143">The preceding code:</span></span>

- <span data-ttu-id="b4d88-144">Efface tous les fournisseurs de configuration existants qui ont été ajoutés par défaut dans la <xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder(System.String[])> méthode.</span><span class="sxs-lookup"><span data-stu-id="b4d88-144">Clears all existing configuration providers that were added by default in the <xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder(System.String[])> method.</span></span>
- <span data-ttu-id="b4d88-145">Configure le fournisseur de configuration XML pour charger les fichiers *appsettings.xml* et *repeating-example.xml* avec les options suivantes :</span><span class="sxs-lookup"><span data-stu-id="b4d88-145">Configures the XML configuration provider to load the *appsettings.xml* and *repeating-example.xml* files with the following options:</span></span>
  - <span data-ttu-id="b4d88-146">`optional: true`: Le fichier est facultatif.</span><span class="sxs-lookup"><span data-stu-id="b4d88-146">`optional: true`: The file is optional.</span></span>
  - <span data-ttu-id="b4d88-147">`reloadOnChange: true` : Le fichier est rechargé lorsque des modifications sont enregistrées.</span><span class="sxs-lookup"><span data-stu-id="b4d88-147">`reloadOnChange: true` : The file is reloaded when changes are saved.</span></span>
- <span data-ttu-id="b4d88-148">Configure le fournisseur de configuration des variables d’environnement.</span><span class="sxs-lookup"><span data-stu-id="b4d88-148">Configures the environment variables configuration provider.</span></span>
- <span data-ttu-id="b4d88-149">Configure le fournisseur de configuration de ligne de commande si le donné `args` contient des arguments.</span><span class="sxs-lookup"><span data-stu-id="b4d88-149">Configures the command-line configuration provider if the given `args` contains arguments.</span></span>

<span data-ttu-id="b4d88-150">Les paramètres XML sont remplacés par les paramètres dans le [fournisseur de configuration des variables d’environnement](#environment-variable-configuration-provider) et le [fournisseur de configuration de ligne de commande](#command-line-configuration-provider).</span><span class="sxs-lookup"><span data-stu-id="b4d88-150">The XML settings are overridden by settings in the [Environment variables configuration provider](#environment-variable-configuration-provider) and the [Command-line configuration provider](#command-line-configuration-provider).</span></span>

<span data-ttu-id="b4d88-151">Voici un exemple *appsettings.xml* fichier avec différents paramètres de configuration :</span><span class="sxs-lookup"><span data-stu-id="b4d88-151">An example *appsettings.xml* file with various configuration settings follows:</span></span>

:::code language="xml" source="snippets/configuration/console-xml/appsettings.xml":::

<span data-ttu-id="b4d88-152">Les éléments répétitifs qui utilisent le même nom d’élément fonctionnent si l’attribut `name` est utilisé pour distinguer les éléments :</span><span class="sxs-lookup"><span data-stu-id="b4d88-152">Repeating elements that use the same element name work if the `name` attribute is used to distinguish the elements:</span></span>

:::code language="xml" source="snippets/configuration/console-xml/repeating-example.xml":::

<span data-ttu-id="b4d88-153">Le code suivant lit le fichier de configuration précédent et affiche les clés et les valeurs :</span><span class="sxs-lookup"><span data-stu-id="b4d88-153">The following code reads the previous configuration file and displays the keys and values:</span></span>

:::code language="csharp" source="snippets/configuration/console-xml/Program.cs" range="36-51":::

<span data-ttu-id="b4d88-154">L’application écrirait l’exemple de sortie suivant :</span><span class="sxs-lookup"><span data-stu-id="b4d88-154">The application would write the following sample output:</span></span>

:::code language="csharp" source="snippets/configuration/console-xml/Program.cs" range="53-57":::

<span data-ttu-id="b4d88-155">Les attributs peuvent être utilisés pour fournir des valeurs :</span><span class="sxs-lookup"><span data-stu-id="b4d88-155">Attributes can be used to supply values:</span></span>

```xml
<?xml version="1.0" encoding="UTF-8"?>
<configuration>
  <key attribute="value" />
  <section>
    <key attribute="value" />
  </section>
</configuration>
```

<span data-ttu-id="b4d88-156">Le fichier de configuration précédent charge les clés suivantes avec `value` :</span><span class="sxs-lookup"><span data-stu-id="b4d88-156">The previous configuration file loads the following keys with `value`:</span></span>

- `key:attribute`
- `section:key:attribute`

### <a name="ini-configuration-provider"></a><span data-ttu-id="b4d88-157">Fournisseur de configuration INI</span><span class="sxs-lookup"><span data-stu-id="b4d88-157">INI configuration provider</span></span>

<span data-ttu-id="b4d88-158">La <xref:Microsoft.Extensions.Configuration.Ini.IniConfigurationProvider> classe charge la configuration à partir d’un fichier ini au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="b4d88-158">The <xref:Microsoft.Extensions.Configuration.Ini.IniConfigurationProvider> class loads configuration from an INI file at runtime.</span></span> <span data-ttu-id="b4d88-159">Installez le [`Microsoft.Extensions.Configuration.Ini`](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.Ini)  package NuGet.</span><span class="sxs-lookup"><span data-stu-id="b4d88-159">Install the [`Microsoft.Extensions.Configuration.Ini`](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.Ini)  NuGet package.</span></span>

<span data-ttu-id="b4d88-160">Le code suivant efface tous les fournisseurs de configuration et ajoute le `IniConfigurationProvider` avec deux fichiers ini comme source :</span><span class="sxs-lookup"><span data-stu-id="b4d88-160">The following code clears all the configuration providers and adds the `IniConfigurationProvider` with two INI files as the source:</span></span>

:::code language="csharp" source="snippets/configuration/console-ini/Program.cs" range="1-37,44-45" highlight="24-30":::

<span data-ttu-id="b4d88-161">Voici un exemple *appsettings.ini* fichier avec différents paramètres de configuration :</span><span class="sxs-lookup"><span data-stu-id="b4d88-161">An example *appsettings.ini* file with various configuration settings follows:</span></span>

:::code language="ini" source="snippets/configuration/console-ini/appsettings.ini":::

<span data-ttu-id="b4d88-162">Le code suivant affiche les paramètres de configuration précédents en les écrivant dans la fenêtre de console :</span><span class="sxs-lookup"><span data-stu-id="b4d88-162">The following code displays the preceding configuration settings by writing them to the console window:</span></span>

:::code language="csharp" source="snippets/configuration/console-ini/Program.cs" range="32-36":::

<span data-ttu-id="b4d88-163">L’application écrirait l’exemple de sortie suivant :</span><span class="sxs-lookup"><span data-stu-id="b4d88-163">The application would write the following sample output:</span></span>

:::code language="csharp" source="snippets/configuration/console-ini/Program.cs" range="38-43":::

## <a name="environment-variable-configuration-provider"></a><span data-ttu-id="b4d88-164">Fournisseur de configuration de variable d’environnement</span><span class="sxs-lookup"><span data-stu-id="b4d88-164">Environment variable configuration provider</span></span>

<span data-ttu-id="b4d88-165">À l’aide de la configuration par défaut, le <xref:Microsoft.Extensions.Configuration.EnvironmentVariables.EnvironmentVariablesConfigurationProvider> charge la configuration à partir des paires clé-valeur de variable d’environnement après la lecture *appsettings.jssur*, *appSettings.* `Environment` *. JSON* et le gestionnaire de secret.</span><span class="sxs-lookup"><span data-stu-id="b4d88-165">Using the default configuration, the <xref:Microsoft.Extensions.Configuration.EnvironmentVariables.EnvironmentVariablesConfigurationProvider> loads configuration from environment variable key-value pairs after reading *appsettings.json*, *appsettings.*`Environment`*.json*, and Secret manager.</span></span> <span data-ttu-id="b4d88-166">Par conséquent, les valeurs de clés lues à partir de l’environnement remplacent les valeurs lues à partir de *appsettings.jssur*, *appSettings.* `Environment` *. JSON* et le gestionnaire de secret.</span><span class="sxs-lookup"><span data-stu-id="b4d88-166">Therefore, key values read from the environment override values read from *appsettings.json*, *appsettings.*`Environment`*.json*, and Secret manager.</span></span>

<span data-ttu-id="b4d88-167">Le `:` séparateur ne fonctionne pas avec les clés hiérarchiques de variable d’environnement sur toutes les plateformes.</span><span class="sxs-lookup"><span data-stu-id="b4d88-167">The `:` separator doesn't work with environment variable hierarchical keys on all platforms.</span></span> <span data-ttu-id="b4d88-168">Le trait de soulignement double ( `__` ) est automatiquement remplacé par un `:` et est pris en charge par toutes les plateformes.</span><span class="sxs-lookup"><span data-stu-id="b4d88-168">The double underscore (`__`) is automatically replaced by a `:` and is supported by all platforms.</span></span> <span data-ttu-id="b4d88-169">Par exemple, le `:` séparateur n’est pas pris en charge par [bash](https://linuxhint.com/bash-environment-variables), mais `__` est.</span><span class="sxs-lookup"><span data-stu-id="b4d88-169">For example, the `:` separator is not supported by [Bash](https://linuxhint.com/bash-environment-variables), but `__` is.</span></span>

<span data-ttu-id="b4d88-170">Les `set` commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="b4d88-170">The following `set` commands:</span></span>

- <span data-ttu-id="b4d88-171">Définissez les clés et les valeurs d’environnement de l’exemple précédent sur Windows.</span><span class="sxs-lookup"><span data-stu-id="b4d88-171">Set the environment keys and values of the preceding example on Windows.</span></span>
- <span data-ttu-id="b4d88-172">Testez les paramètres en les remplaçant par leurs valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="b4d88-172">Test the settings by changing them from their default values.</span></span> <span data-ttu-id="b4d88-173">La `dotnet run` commande doit être exécutée dans le répertoire du projet.</span><span class="sxs-lookup"><span data-stu-id="b4d88-173">The `dotnet run` command must be run in the project directory.</span></span>

```dotnetcli
set SecretKey="Secret key from environment"
set TransientFaultHandlingOptions__Enabled="true"
set TransientFaultHandlingOptions__AutoRetryDelay="00:00:13"

dotnet run
```

<span data-ttu-id="b4d88-174">Paramètres d’environnement précédents :</span><span class="sxs-lookup"><span data-stu-id="b4d88-174">The preceding environment settings:</span></span>

- <span data-ttu-id="b4d88-175">Sont uniquement définies dans les processus lancés à partir de la fenêtre de commande dans laquelle ils ont été définis.</span><span class="sxs-lookup"><span data-stu-id="b4d88-175">Are only set in processes launched from the command window they were set in.</span></span>
- <span data-ttu-id="b4d88-176">Ne seront pas lues par les applications Web lancées avec Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b4d88-176">Won't be read by web apps launched with Visual Studio.</span></span>

<span data-ttu-id="b4d88-177">Les commandes [setx](/windows-server/administration/windows-commands/setx) suivantes peuvent être utilisées pour définir les clés et les valeurs d’environnement sur Windows.</span><span class="sxs-lookup"><span data-stu-id="b4d88-177">The following [setx](/windows-server/administration/windows-commands/setx) commands can be used to set the environment keys and values on Windows.</span></span> <span data-ttu-id="b4d88-178">Contrairement à `set` , `setx` les paramètres sont conservés.</span><span class="sxs-lookup"><span data-stu-id="b4d88-178">Unlike `set`, `setx` settings are persisted.</span></span> <span data-ttu-id="b4d88-179">`/M` définit la variable dans l’environnement système.</span><span class="sxs-lookup"><span data-stu-id="b4d88-179">`/M` sets the variable in the system environment.</span></span> <span data-ttu-id="b4d88-180">Si le `/M` commutateur n’est pas utilisé, une variable d’environnement utilisateur est définie.</span><span class="sxs-lookup"><span data-stu-id="b4d88-180">If the `/M` switch isn't used, a user environment variable is set.</span></span>

```dotnetcli
setx SecretKey "Secret key from setx environment" /M
setx TransientFaultHandlingOptions__Enabled "true" /M
setx TransientFaultHandlingOptions__AutoRetryDelay "00:00:05" /M

dotnet run
```

<span data-ttu-id="b4d88-181">Pour vérifier que les commandes précédentes remplacent *appsettings.jssur* et *appSettings.* `Environment` *. JSON*:</span><span class="sxs-lookup"><span data-stu-id="b4d88-181">To test that the preceding commands override *appsettings.json* and *appsettings.*`Environment`*.json*:</span></span>

- <span data-ttu-id="b4d88-182">Avec Visual Studio : quittez et redémarrez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b4d88-182">With Visual Studio: Exit and restart Visual Studio.</span></span>
- <span data-ttu-id="b4d88-183">Avec l’interface CLI : démarrez une nouvelle fenêtre de commande et entrez `dotnet run` .</span><span class="sxs-lookup"><span data-stu-id="b4d88-183">With the CLI: Start a new command window and enter `dotnet run`.</span></span>

<span data-ttu-id="b4d88-184">Appelez <xref:Microsoft.Extensions.Configuration.EnvironmentVariablesExtensions.AddEnvironmentVariables%2A> avec une chaîne pour spécifier un préfixe pour les variables d’environnement :</span><span class="sxs-lookup"><span data-stu-id="b4d88-184">Call <xref:Microsoft.Extensions.Configuration.EnvironmentVariablesExtensions.AddEnvironmentVariables%2A> with a string to specify a prefix for environment variables:</span></span>

:::code language="csharp" source="snippets/configuration/console-env/Program.cs" highlight="21-22":::

<span data-ttu-id="b4d88-185">Dans le code précédent :</span><span class="sxs-lookup"><span data-stu-id="b4d88-185">In the preceding code:</span></span>

- <span data-ttu-id="b4d88-186">`config.AddEnvironmentVariables(prefix: "CustomPrefix_")` est ajouté après les fournisseurs de configuration par défaut.</span><span class="sxs-lookup"><span data-stu-id="b4d88-186">`config.AddEnvironmentVariables(prefix: "CustomPrefix_")` is added after the default configuration providers.</span></span> <span data-ttu-id="b4d88-187">Pour obtenir un exemple de classement des fournisseurs de configuration, consultez [fournisseur de configuration XML](#xml-configuration-provider).</span><span class="sxs-lookup"><span data-stu-id="b4d88-187">For an example of ordering the configuration providers, see [XML configuration provider](#xml-configuration-provider).</span></span>
- <span data-ttu-id="b4d88-188">Les variables d’environnement définies avec le `CustomPrefix_` préfixe remplacent les fournisseurs de configuration par défaut.</span><span class="sxs-lookup"><span data-stu-id="b4d88-188">Environment variables set with the `CustomPrefix_` prefix override the default configuration providers.</span></span> <span data-ttu-id="b4d88-189">Cela comprend les variables d’environnement sans le préfixe.</span><span class="sxs-lookup"><span data-stu-id="b4d88-189">This includes environment variables without the prefix.</span></span>

<span data-ttu-id="b4d88-190">Le préfixe est supprimé lorsque les paires clé-valeur de configuration sont lues.</span><span class="sxs-lookup"><span data-stu-id="b4d88-190">The prefix is stripped off when the configuration key-value pairs are read.</span></span>

<span data-ttu-id="b4d88-191">Les commandes suivantes testent le préfixe personnalisé :</span><span class="sxs-lookup"><span data-stu-id="b4d88-191">The following commands test the custom prefix:</span></span>

```dotnetcli
set CustomPrefix__SecretKey="Secret key with CustomPrefix_ environment"
set CustomPrefix__TransientFaultHandlingOptions__Enabled=true
set CustomPrefix__TransientFaultHandlingOptions__AutoRetryDelay=00:00:21

dotnet run
```

<span data-ttu-id="b4d88-192">La configuration par défaut charge les variables d’environnement et les arguments de ligne de commande précédés du préfixe `DOTNET_` .</span><span class="sxs-lookup"><span data-stu-id="b4d88-192">The default configuration loads environment variables and command-line arguments prefixed with `DOTNET_`.</span></span> <span data-ttu-id="b4d88-193">Le `DOTNET_` préfixe est utilisé par .net pour la [configuration](generic-host.md#app-configuration)de l' [hôte](generic-host.md#host-configuration) et de l’application, mais pas pour la configuration de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="b4d88-193">The `DOTNET_` prefix is used by .NET for [host](generic-host.md#host-configuration) and [app configuration](generic-host.md#app-configuration), but not for user configuration.</span></span>

<span data-ttu-id="b4d88-194">Pour plus d’informations sur la configuration de l’hôte et de l’application, consultez [hôte générique .net](generic-host.md).</span><span class="sxs-lookup"><span data-stu-id="b4d88-194">For more information on host and app configuration, see [.NET Generic Host](generic-host.md).</span></span>

<span data-ttu-id="b4d88-195">Dans [Azure App service](https://azure.microsoft.com/services/app-service), sélectionnez **nouveau paramètre d’application** dans la page **paramètres > configuration** .</span><span class="sxs-lookup"><span data-stu-id="b4d88-195">On [Azure App Service](https://azure.microsoft.com/services/app-service), select **New application setting** on the **Settings > Configuration** page.</span></span> <span data-ttu-id="b4d88-196">Azure App Service paramètres de l’application sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="b4d88-196">Azure App Service application settings are:</span></span>

- <span data-ttu-id="b4d88-197">Chiffré au repos et transmis sur un canal chiffré.</span><span class="sxs-lookup"><span data-stu-id="b4d88-197">Encrypted at rest and transmitted over an encrypted channel.</span></span>
- <span data-ttu-id="b4d88-198">Exposés en tant que variables d’environnement.</span><span class="sxs-lookup"><span data-stu-id="b4d88-198">Exposed as environment variables.</span></span>

### <a name="connection-string-prefixes"></a><span data-ttu-id="b4d88-199">Préfixes des chaînes de connexion</span><span class="sxs-lookup"><span data-stu-id="b4d88-199">Connection string prefixes</span></span>

<span data-ttu-id="b4d88-200">L’API de configuration a des règles de traitement spéciales pour quatre variables d’environnement de chaîne de connexion.</span><span class="sxs-lookup"><span data-stu-id="b4d88-200">The Configuration API has special processing rules for four connection string environment variables.</span></span> <span data-ttu-id="b4d88-201">Ces chaînes de connexion sont impliquées dans la configuration des chaînes de connexion Azure pour l’environnement de l’application.</span><span class="sxs-lookup"><span data-stu-id="b4d88-201">These connection strings are involved in configuring Azure connection strings for the app environment.</span></span> <span data-ttu-id="b4d88-202">Les variables d’environnement avec les préfixes indiqués dans le tableau sont chargées dans l’application avec la configuration par défaut ou lorsqu’aucun préfixe n’est fourni à `AddEnvironmentVariables` .</span><span class="sxs-lookup"><span data-stu-id="b4d88-202">Environment variables with the prefixes shown in the table are loaded into the app with the default configuration or when no prefix is supplied to `AddEnvironmentVariables`.</span></span>

| <span data-ttu-id="b4d88-203">Préfixe de la chaîne de connexion</span><span class="sxs-lookup"><span data-stu-id="b4d88-203">Connection string prefix</span></span> | <span data-ttu-id="b4d88-204">Fournisseur</span><span class="sxs-lookup"><span data-stu-id="b4d88-204">Provider</span></span>                                                                |
|--------------------------|-------------------------------------------------------------------------|
| `CUSTOMCONNSTR_`         | <span data-ttu-id="b4d88-205">Fournisseur personnalisé</span><span class="sxs-lookup"><span data-stu-id="b4d88-205">Custom provider</span></span>                                                         |
| `MYSQLCONNSTR_`          | [<span data-ttu-id="b4d88-206">MySQL</span><span class="sxs-lookup"><span data-stu-id="b4d88-206">MySQL</span></span>](https://www.mysql.com)                                          |
| `SQLAZURECONNSTR_`       | [<span data-ttu-id="b4d88-207">Azure SQL Database</span><span class="sxs-lookup"><span data-stu-id="b4d88-207">Azure SQL Database</span></span>](https://azure.microsoft.com/services/sql-database) |
| `SQLCONNSTR_`            | [<span data-ttu-id="b4d88-208">SQL Server</span><span class="sxs-lookup"><span data-stu-id="b4d88-208">SQL Server</span></span>](https://www.microsoft.com/sql-server)                      |

<span data-ttu-id="b4d88-209">Quand une variable d’environnement est découverte et chargée dans la configuration avec l’un des quatre préfixes indiqués dans le tableau :</span><span class="sxs-lookup"><span data-stu-id="b4d88-209">When an environment variable is discovered and loaded into configuration with any of the four prefixes shown in the table:</span></span>

- <span data-ttu-id="b4d88-210">La clé de configuration est créée en supprimant le préfixe de la variable d’environnement et en ajoutant une section de clé de configuration (`ConnectionStrings`).</span><span class="sxs-lookup"><span data-stu-id="b4d88-210">The configuration key is created by removing the environment variable prefix and adding a configuration key section (`ConnectionStrings`).</span></span>
- <span data-ttu-id="b4d88-211">Une nouvelle paire clé-valeur de configuration est créée qui représente le fournisseur de connexion de base de données (à l’exception de `CUSTOMCONNSTR_`, qui ne possède aucun fournisseur indiqué).</span><span class="sxs-lookup"><span data-stu-id="b4d88-211">A new configuration key-value pair is created that represents the database connection provider (except for `CUSTOMCONNSTR_`, which has no stated provider).</span></span>

| <span data-ttu-id="b4d88-212">Clé de variable d’environnement</span><span class="sxs-lookup"><span data-stu-id="b4d88-212">Environment variable key</span></span> | <span data-ttu-id="b4d88-213">Clé de configuration convertie</span><span class="sxs-lookup"><span data-stu-id="b4d88-213">Converted configuration key</span></span> | <span data-ttu-id="b4d88-214">Entrée de configuration de fournisseur</span><span class="sxs-lookup"><span data-stu-id="b4d88-214">Provider configuration entry</span></span>                                                    |
|--------------------------|-----------------------------|---------------------------------------------------------------------------------|
| `CUSTOMCONNSTR_{KEY}`    | `ConnectionStrings:{KEY}`   | <span data-ttu-id="b4d88-215">Entrée de configuration non créée.</span><span class="sxs-lookup"><span data-stu-id="b4d88-215">Configuration entry not created.</span></span>                                                |
| `MYSQLCONNSTR_{KEY}`     | `ConnectionStrings:{KEY}`   | <span data-ttu-id="b4d88-216">Clé : `ConnectionStrings:{KEY}_ProviderName` :</span><span class="sxs-lookup"><span data-stu-id="b4d88-216">Key: `ConnectionStrings:{KEY}_ProviderName`:</span></span><br><span data-ttu-id="b4d88-217">Valeur: `MySql.Data.MySqlClient`</span><span class="sxs-lookup"><span data-stu-id="b4d88-217">Value: `MySql.Data.MySqlClient`</span></span> |
| `SQLAZURECONNSTR_{KEY}`  | `ConnectionStrings:{KEY}`   | <span data-ttu-id="b4d88-218">Clé : `ConnectionStrings:{KEY}_ProviderName` :</span><span class="sxs-lookup"><span data-stu-id="b4d88-218">Key: `ConnectionStrings:{KEY}_ProviderName`:</span></span><br><span data-ttu-id="b4d88-219">Valeur: `System.Data.SqlClient`</span><span class="sxs-lookup"><span data-stu-id="b4d88-219">Value: `System.Data.SqlClient`</span></span>  |
| `SQLCONNSTR_{KEY}`       | `ConnectionStrings:{KEY}`   | <span data-ttu-id="b4d88-220">Clé : `ConnectionStrings:{KEY}_ProviderName` :</span><span class="sxs-lookup"><span data-stu-id="b4d88-220">Key: `ConnectionStrings:{KEY}_ProviderName`:</span></span><br><span data-ttu-id="b4d88-221">Valeur: `System.Data.SqlClient`</span><span class="sxs-lookup"><span data-stu-id="b4d88-221">Value: `System.Data.SqlClient`</span></span>  |

### <a name="environment-variables-set-in-launchsettingsjson"></a><span data-ttu-id="b4d88-222">Variables d’environnement définies dans launchSettings.jssur</span><span class="sxs-lookup"><span data-stu-id="b4d88-222">Environment variables set in launchSettings.json</span></span>

<span data-ttu-id="b4d88-223">Les variables d’environnement définies dans *launchSettings.jslors de* la substitution de celles définies dans l’environnement système.</span><span class="sxs-lookup"><span data-stu-id="b4d88-223">Environment variables set in *launchSettings.json* override those set in the system environment.</span></span>

## <a name="command-line-configuration-provider"></a><span data-ttu-id="b4d88-224">Fournisseur de configuration de ligne de commande</span><span class="sxs-lookup"><span data-stu-id="b4d88-224">Command-line configuration provider</span></span>

<span data-ttu-id="b4d88-225">À l’aide de la configuration par défaut, le <xref:Microsoft.Extensions.Configuration.CommandLine.CommandLineConfigurationProvider> charge la configuration à partir de paires clé-valeur d’argument de ligne de commande après les sources de configuration suivantes :</span><span class="sxs-lookup"><span data-stu-id="b4d88-225">Using the default configuration, the <xref:Microsoft.Extensions.Configuration.CommandLine.CommandLineConfigurationProvider> loads configuration from command-line argument key-value pairs after the following configuration sources:</span></span>

- <span data-ttu-id="b4d88-226">*appsettings.jssur* et *appSettings*. `Environment` fichiers *JSON* .</span><span class="sxs-lookup"><span data-stu-id="b4d88-226">*appsettings.json* and *appsettings*.`Environment`.*json* files.</span></span>
- <span data-ttu-id="b4d88-227">Secrets d’application (gestionnaire de secret) dans l' `Development` environnement.</span><span class="sxs-lookup"><span data-stu-id="b4d88-227">App secrets (Secret Manager) in the `Development` environment.</span></span>
- <span data-ttu-id="b4d88-228">Variables d'environnement.</span><span class="sxs-lookup"><span data-stu-id="b4d88-228">Environment variables.</span></span>

<span data-ttu-id="b4d88-229">Par défaut, les valeurs de configuration définies sur la ligne de commande remplacent les valeurs de configuration définies avec tous les autres fournisseurs de configuration.</span><span class="sxs-lookup"><span data-stu-id="b4d88-229">By default, configuration values set on the command line override configuration values set with all the other configuration providers.</span></span>

### <a name="command-line-arguments"></a><span data-ttu-id="b4d88-230">Arguments de ligne de commande</span><span class="sxs-lookup"><span data-stu-id="b4d88-230">Command-line arguments</span></span>

<span data-ttu-id="b4d88-231">La commande suivante définit des clés et des valeurs à l’aide de `=` :</span><span class="sxs-lookup"><span data-stu-id="b4d88-231">The following command sets keys and values using `=`:</span></span>

```dotnetcli
dotnet run SecretKey="Secret key from command line"
```

<span data-ttu-id="b4d88-232">La commande suivante définit des clés et des valeurs à l’aide de `/` :</span><span class="sxs-lookup"><span data-stu-id="b4d88-232">The following command sets keys and values using `/`:</span></span>

```dotnetcli
dotnet run /SecretKey "Secret key set from forward slash"
```

<span data-ttu-id="b4d88-233">La commande suivante définit des clés et des valeurs à l’aide de `--` :</span><span class="sxs-lookup"><span data-stu-id="b4d88-233">The following command sets keys and values using `--`:</span></span>

```dotnetcli
dotnet run --SecretKey "Secret key set from double hyphen"
```

<span data-ttu-id="b4d88-234">Valeur de la clé :</span><span class="sxs-lookup"><span data-stu-id="b4d88-234">The key value:</span></span>

- <span data-ttu-id="b4d88-235">Doit suivre `=` ou la clé doit avoir un préfixe `--` ou `/` lorsque la valeur suit un espace.</span><span class="sxs-lookup"><span data-stu-id="b4d88-235">Must follow `=`, or the key must have a prefix of `--` or `/` when the value follows a space.</span></span>
- <span data-ttu-id="b4d88-236">N’est pas obligatoire si `=` est utilisé.</span><span class="sxs-lookup"><span data-stu-id="b4d88-236">Isn't required if `=` is used.</span></span> <span data-ttu-id="b4d88-237">Par exemple : `SomeKey=`.</span><span class="sxs-lookup"><span data-stu-id="b4d88-237">For example, `SomeKey=`.</span></span>

<span data-ttu-id="b4d88-238">Dans la même commande, ne mélangez pas les paires clé-valeur d’argument de ligne de commande qui utilisent `=` des paires clé-valeur utilisant un espace.</span><span class="sxs-lookup"><span data-stu-id="b4d88-238">Within the same command, don't mix command-line argument key-value pairs that use `=` with key-value pairs that use a space.</span></span>

## <a name="key-per-file-configuration-provider"></a><span data-ttu-id="b4d88-239">Fournisseur de configuration de clé par fichier</span><span class="sxs-lookup"><span data-stu-id="b4d88-239">Key-per-file configuration provider</span></span>

<span data-ttu-id="b4d88-240">Le <xref:Microsoft.Extensions.Configuration.KeyPerFile.KeyPerFileConfigurationProvider> utilise les fichiers d’un répertoire en tant que paires clé-valeur de configuration.</span><span class="sxs-lookup"><span data-stu-id="b4d88-240">The <xref:Microsoft.Extensions.Configuration.KeyPerFile.KeyPerFileConfigurationProvider> uses a directory's files as configuration key-value pairs.</span></span> <span data-ttu-id="b4d88-241">La clé est le nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="b4d88-241">The key is the file name.</span></span> <span data-ttu-id="b4d88-242">La valeur est le contenu du fichier.</span><span class="sxs-lookup"><span data-stu-id="b4d88-242">The value is the file's contents.</span></span> <span data-ttu-id="b4d88-243">Le fournisseur de configuration par fichier clé est utilisé dans les scénarios d’hébergement de l’ancrage.</span><span class="sxs-lookup"><span data-stu-id="b4d88-243">The Key-per-file configuration provider is used in Docker hosting scenarios.</span></span>

<span data-ttu-id="b4d88-244">Pour activer la configuration clé par fichier, appelez la méthode d’extension <xref:Microsoft.Extensions.Configuration.KeyPerFileConfigurationBuilderExtensions.AddKeyPerFile%2A> sur une instance de <xref:Microsoft.Extensions.Configuration.ConfigurationBuilder>.</span><span class="sxs-lookup"><span data-stu-id="b4d88-244">To activate key-per-file configuration, call the <xref:Microsoft.Extensions.Configuration.KeyPerFileConfigurationBuilderExtensions.AddKeyPerFile%2A> extension method on an instance of <xref:Microsoft.Extensions.Configuration.ConfigurationBuilder>.</span></span> <span data-ttu-id="b4d88-245">Le `directoryPath` aux fichiers doit être un chemin d’accès absolu.</span><span class="sxs-lookup"><span data-stu-id="b4d88-245">The `directoryPath` to the files must be an absolute path.</span></span>

<span data-ttu-id="b4d88-246">Les surcharges permettent de spécifier :</span><span class="sxs-lookup"><span data-stu-id="b4d88-246">Overloads permit specifying:</span></span>

- <span data-ttu-id="b4d88-247">Un délégué `Action<KeyPerFileConfigurationSource>` qui configure la source.</span><span class="sxs-lookup"><span data-stu-id="b4d88-247">An `Action<KeyPerFileConfigurationSource>` delegate that configures the source.</span></span>
- <span data-ttu-id="b4d88-248">Si le répertoire est facultatif et le chemin d’accès au répertoire.</span><span class="sxs-lookup"><span data-stu-id="b4d88-248">Whether the directory is optional and the path to the directory.</span></span>

<span data-ttu-id="b4d88-249">Le double trait de soulignement (`__`) est utilisé comme un délimiteur de clé de configuration dans les noms de fichiers.</span><span class="sxs-lookup"><span data-stu-id="b4d88-249">The double-underscore (`__`) is used as a configuration key delimiter in file names.</span></span> <span data-ttu-id="b4d88-250">Par exemple, le nom de fichier `Logging__LogLevel__System` génère la clé de configuration `Logging:LogLevel:System`.</span><span class="sxs-lookup"><span data-stu-id="b4d88-250">For example, the file name `Logging__LogLevel__System` produces the configuration key `Logging:LogLevel:System`.</span></span>

<span data-ttu-id="b4d88-251">Appelez `ConfigureAppConfiguration` lors de la création de l’hôte pour spécifier la configuration de l’application :</span><span class="sxs-lookup"><span data-stu-id="b4d88-251">Call `ConfigureAppConfiguration` when building the host to specify the app's configuration:</span></span>

```csharp
.ConfigureAppConfiguration((_, configuration) =>
{
    var path = Path.Combine(
        Directory.GetCurrentDirectory(), "path/to/files");

    configuration.AddKeyPerFile(directoryPath: path, optional: true);
})
```

## <a name="memory-configuration-provider"></a><span data-ttu-id="b4d88-252">Fournisseur de configuration de la mémoire</span><span class="sxs-lookup"><span data-stu-id="b4d88-252">Memory configuration provider</span></span>

<span data-ttu-id="b4d88-253">Le <xref:Microsoft.Extensions.Configuration.Memory.MemoryConfigurationProvider> utilise une collection en mémoire en tant que paires clé-valeur de configuration.</span><span class="sxs-lookup"><span data-stu-id="b4d88-253">The <xref:Microsoft.Extensions.Configuration.Memory.MemoryConfigurationProvider> uses an in-memory collection as configuration key-value pairs.</span></span>

<span data-ttu-id="b4d88-254">Le code suivant ajoute une collection de mémoire au système de configuration :</span><span class="sxs-lookup"><span data-stu-id="b4d88-254">The following code adds a memory collection to the configuration system:</span></span>

:::code language="csharp" source="snippets/configuration/console-memory/Program.cs" highlight="22-29":::

<span data-ttu-id="b4d88-255">Dans le code précédent, <xref:Microsoft.Extensions.Configuration.MemoryConfigurationBuilderExtensions.AddInMemoryCollection(Microsoft.Extensions.Configuration.IConfigurationBuilder,System.Collections.Generic.IEnumerable{System.Collections.Generic.KeyValuePair{System.String,System.String}})?displayProperty=nameWithType> ajoute le fournisseur de mémoire après les fournisseurs de configuration par défaut.</span><span class="sxs-lookup"><span data-stu-id="b4d88-255">In the preceding code, <xref:Microsoft.Extensions.Configuration.MemoryConfigurationBuilderExtensions.AddInMemoryCollection(Microsoft.Extensions.Configuration.IConfigurationBuilder,System.Collections.Generic.IEnumerable{System.Collections.Generic.KeyValuePair{System.String,System.String}})?displayProperty=nameWithType> adds the memory provider after the default configuration providers.</span></span> <span data-ttu-id="b4d88-256">Pour obtenir un exemple de classement des fournisseurs de configuration, consultez [fournisseur de configuration XML](#xml-configuration-provider).</span><span class="sxs-lookup"><span data-stu-id="b4d88-256">For an example of ordering the configuration providers, see [XML configuration provider](#xml-configuration-provider).</span></span>

## <a name="see-also"></a><span data-ttu-id="b4d88-257">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b4d88-257">See also</span></span>

- [<span data-ttu-id="b4d88-258">Configuration dans .NET</span><span class="sxs-lookup"><span data-stu-id="b4d88-258">Configuration in .NET</span></span>](configuration.md)
- [<span data-ttu-id="b4d88-259">Hôte générique .NET</span><span class="sxs-lookup"><span data-stu-id="b4d88-259">.NET Generic Host</span></span>](generic-host.md)
- [<span data-ttu-id="b4d88-260">Implémenter un fournisseur de configuration personnalisé</span><span class="sxs-lookup"><span data-stu-id="b4d88-260">Implement a custom configuration provider</span></span>](custom-configuration-provider.md)
