---
title: Fournisseurs de configuration dans .NET
description: Découvrez comment l’API du fournisseur de configuration est utilisée pour configurer des applications .NET.
author: IEvangelist
ms.author: dapine
ms.date: 09/16/2020
ms.openlocfilehash: fe90ba9aee08ec9c1316335a5b3fd8dd6e90a811
ms.sourcegitcommit: fe8877e564deb68d77fa4b79f55584ac8d7e8997
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90720845"
---
# <a name="configuration-providers-in-net"></a><span data-ttu-id="a5dba-103">Fournisseurs de configuration dans .NET</span><span class="sxs-lookup"><span data-stu-id="a5dba-103">Configuration providers in .NET</span></span>

<span data-ttu-id="a5dba-104">La configuration dans .NET est possible avec les fournisseurs de configuration.</span><span class="sxs-lookup"><span data-stu-id="a5dba-104">Configuration in .NET is possible with configuration providers.</span></span> <span data-ttu-id="a5dba-105">Il existe plusieurs types de fournisseurs qui reposent sur différentes sources de configuration.</span><span class="sxs-lookup"><span data-stu-id="a5dba-105">There are several types of providers that rely on various configuration sources.</span></span> <span data-ttu-id="a5dba-106">Cet article détaille tous les différents fournisseurs de configuration et leurs sources correspondantes.</span><span class="sxs-lookup"><span data-stu-id="a5dba-106">This article details all of the different configuration providers and their corresponding sources.</span></span>

- [<span data-ttu-id="a5dba-107">Fournisseur de configuration de fichier</span><span class="sxs-lookup"><span data-stu-id="a5dba-107">File configuration provider</span></span>](#file-configuration-provider)
- [<span data-ttu-id="a5dba-108">Fournisseur de configuration de variable d’environnement</span><span class="sxs-lookup"><span data-stu-id="a5dba-108">Environment variable configuration provider</span></span>](#environment-variable-configuration-provider)
- [<span data-ttu-id="a5dba-109">Fournisseur de configuration de ligne de commande</span><span class="sxs-lookup"><span data-stu-id="a5dba-109">Command-line configuration provider</span></span>](#command-line-configuration-provider)
- [<span data-ttu-id="a5dba-110">Fournisseur de configuration de clé par fichier</span><span class="sxs-lookup"><span data-stu-id="a5dba-110">Key-per-file configuration provider</span></span>](#key-per-file-configuration-provider)
- [<span data-ttu-id="a5dba-111">Fournisseur de configuration de la mémoire</span><span class="sxs-lookup"><span data-stu-id="a5dba-111">Memory configuration provider</span></span>](#memory-configuration-provider)

## <a name="file-configuration-provider"></a><span data-ttu-id="a5dba-112">Fournisseur de configuration de fichier</span><span class="sxs-lookup"><span data-stu-id="a5dba-112">File configuration provider</span></span>

<span data-ttu-id="a5dba-113"><xref:Microsoft.Extensions.Configuration.FileConfigurationProvider> est la classe de base pour charger la configuration à partir du système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="a5dba-113"><xref:Microsoft.Extensions.Configuration.FileConfigurationProvider> is the base class for loading configuration from the file system.</span></span> <span data-ttu-id="a5dba-114">Les fournisseurs de configuration suivants dérivent de `FileConfigurationProvider` :</span><span class="sxs-lookup"><span data-stu-id="a5dba-114">The following configuration providers derive from `FileConfigurationProvider`:</span></span>

- [<span data-ttu-id="a5dba-115">Fournisseur de configuration JSON</span><span class="sxs-lookup"><span data-stu-id="a5dba-115">JSON configuration provider</span></span>](#json-configuration-provider)
- [<span data-ttu-id="a5dba-116">Fournisseur de configuration XML</span><span class="sxs-lookup"><span data-stu-id="a5dba-116">XML configuration provider</span></span>](#xml-configuration-provider)
- [<span data-ttu-id="a5dba-117">Fournisseur de configuration INI</span><span class="sxs-lookup"><span data-stu-id="a5dba-117">INI configuration provider</span></span>](#ini-configuration-provider)

### <a name="json-configuration-provider"></a><span data-ttu-id="a5dba-118">Fournisseur de configuration JSON</span><span class="sxs-lookup"><span data-stu-id="a5dba-118">JSON configuration provider</span></span>

<span data-ttu-id="a5dba-119">La <xref:Microsoft.Extensions.Configuration.Json.JsonConfigurationProvider> classe charge la configuration à partir d’un fichier JSON.</span><span class="sxs-lookup"><span data-stu-id="a5dba-119">The <xref:Microsoft.Extensions.Configuration.Json.JsonConfigurationProvider> class loads configuration from a JSON file.</span></span> <span data-ttu-id="a5dba-120">Installez le [`Microsoft.Extensions.Configuration.Json`](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.Json) package NuGet.</span><span class="sxs-lookup"><span data-stu-id="a5dba-120">Install the [`Microsoft.Extensions.Configuration.Json`](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.Json) NuGet package.</span></span>

<span data-ttu-id="a5dba-121">Les surcharges peuvent spécifier :</span><span class="sxs-lookup"><span data-stu-id="a5dba-121">Overloads can specify:</span></span>

- <span data-ttu-id="a5dba-122">Indique si le fichier est facultatif</span><span class="sxs-lookup"><span data-stu-id="a5dba-122">Whether the file is optional</span></span>
- <span data-ttu-id="a5dba-123">Si la configuration est rechargée en cas de modification du fichier</span><span class="sxs-lookup"><span data-stu-id="a5dba-123">Whether the configuration is reloaded if the file changes</span></span>

<span data-ttu-id="a5dba-124">Considérez le code suivant :</span><span class="sxs-lookup"><span data-stu-id="a5dba-124">Consider the following code:</span></span>

:::code language="csharp" source="snippets/configuration/console-json/Program.cs" range="1-33,37-38" highlight="17-23":::

<span data-ttu-id="a5dba-125">Le code précédent :</span><span class="sxs-lookup"><span data-stu-id="a5dba-125">The preceding code:</span></span>

- <span data-ttu-id="a5dba-126">Efface tous les fournisseurs de configuration existants qui ont été ajoutés par défaut dans la <xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder(System.String[])> méthode.</span><span class="sxs-lookup"><span data-stu-id="a5dba-126">Clears all existing configuration providers that were added by default in the <xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder(System.String[])> method.</span></span>
- <span data-ttu-id="a5dba-127">Configure le fournisseur de configuration JSON pour charger le *appsettings.jssur* et  *appSettings*. `Environment` fichiers *JSON* avec les options suivantes :</span><span class="sxs-lookup"><span data-stu-id="a5dba-127">Configures the JSON configuration provider to load the *appsettings.json* and  *appsettings*.`Environment`.*json* files with the following options:</span></span>
  - <span data-ttu-id="a5dba-128">`optional: true`: Le fichier est facultatif.</span><span class="sxs-lookup"><span data-stu-id="a5dba-128">`optional: true`: The file is optional.</span></span>
  - <span data-ttu-id="a5dba-129">`reloadOnChange: true` : Le fichier est rechargé lorsque des modifications sont enregistrées.</span><span class="sxs-lookup"><span data-stu-id="a5dba-129">`reloadOnChange: true` : The file is reloaded when changes are saved.</span></span>

<span data-ttu-id="a5dba-130">Les paramètres JSON sont remplacés par les paramètres dans le [fournisseur de configuration des variables d’environnement](#environment-variable-configuration-provider) et le [fournisseur de configuration de ligne de commande](#command-line-configuration-provider).</span><span class="sxs-lookup"><span data-stu-id="a5dba-130">The JSON settings are overridden by settings in the [Environment variables configuration provider](#environment-variable-configuration-provider) and the [Command-line configuration provider](#command-line-configuration-provider).</span></span>

<span data-ttu-id="a5dba-131">Voici un exemple *appsettings.jssur* un fichier avec différents paramètres de configuration :</span><span class="sxs-lookup"><span data-stu-id="a5dba-131">An example *appsettings.json* file with various configuration settings follows:</span></span>

:::code language="json" source="snippets/configuration/console-json/appsettings.json":::

<span data-ttu-id="a5dba-132">À partir de l' <xref:Microsoft.Extensions.Configuration.IConfigurationBuilder> instance, après avoir ajouté des fournisseurs de configuration, vous pouvez appeler <xref:Microsoft.Extensions.Configuration.IConfigurationBuilder.Build?displayProperty=nameWithType> pour obtenir l' <xref:Microsoft.Extensions.Configuration.IConfigurationRoot> objet.</span><span class="sxs-lookup"><span data-stu-id="a5dba-132">From the <xref:Microsoft.Extensions.Configuration.IConfigurationBuilder> instance, after configuration providers have been added you can call <xref:Microsoft.Extensions.Configuration.IConfigurationBuilder.Build?displayProperty=nameWithType> to get the <xref:Microsoft.Extensions.Configuration.IConfigurationRoot> object.</span></span> <span data-ttu-id="a5dba-133">La racine de configuration représente la racine d’une hiérarchie de configuration.</span><span class="sxs-lookup"><span data-stu-id="a5dba-133">The configuration root represents the root of a configuration hierarchy.</span></span> <span data-ttu-id="a5dba-134">Les sections de la configuration peuvent être liées à des instances d’objets .NET, et fournies ultérieurement comme par le biais de l' <xref:Microsoft.Extensions.Options.IOptions%601> injection de dépendances.</span><span class="sxs-lookup"><span data-stu-id="a5dba-134">Sections from the configuration can be bound to instances of .NET objects, and later provided as <xref:Microsoft.Extensions.Options.IOptions%601> through dependency injection.</span></span>

<span data-ttu-id="a5dba-135">Prenons le `TransientFaultHandlingOptions` type d’enregistrement défini comme suit :</span><span class="sxs-lookup"><span data-stu-id="a5dba-135">Consider the `TransientFaultHandlingOptions` record type defined as follows:</span></span>

:::code language="csharp" source="snippets/configuration/console-json/TransientFaultHandlingOptions.cs":::

<span data-ttu-id="a5dba-136">Pour plus d’informations sur les types d’enregistrements, consultez [types d’enregistrements en C# 9](../../csharp/whats-new/csharp-9.md#record-types).</span><span class="sxs-lookup"><span data-stu-id="a5dba-136">For information on record types, see [Record types in C# 9](../../csharp/whats-new/csharp-9.md#record-types).</span></span>

<span data-ttu-id="a5dba-137">Le code suivant génère la racine de configuration, lie une section au `TransientFaultHandlingOptions` type d’enregistrement et imprime les valeurs liées dans la fenêtre de console :</span><span class="sxs-lookup"><span data-stu-id="a5dba-137">The following code builds the configuration root, binds a section to the `TransientFaultHandlingOptions` record type, and prints the bound values to the console window:</span></span>

:::code language="csharp" source="snippets/configuration/console-json/Program.cs" range="25-32":::

<span data-ttu-id="a5dba-138">L’application écrirait l’exemple de sortie suivant :</span><span class="sxs-lookup"><span data-stu-id="a5dba-138">The application would write the following sample output:</span></span>

:::code language="csharp" source="snippets/configuration/console-json/Program.cs" range="34-36":::

### <a name="xml-configuration-provider"></a><span data-ttu-id="a5dba-139">Fournisseur de configuration XML</span><span class="sxs-lookup"><span data-stu-id="a5dba-139">XML configuration provider</span></span>

<span data-ttu-id="a5dba-140">La <xref:Microsoft.Extensions.Configuration.Xml.XmlConfigurationProvider> classe charge la configuration à partir d’un fichier XML au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="a5dba-140">The <xref:Microsoft.Extensions.Configuration.Xml.XmlConfigurationProvider> class loads configuration from an XML file at runtime.</span></span> <span data-ttu-id="a5dba-141">Installez le [`Microsoft.Extensions.Configuration.Xml`](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.Xml) package NuGet.</span><span class="sxs-lookup"><span data-stu-id="a5dba-141">Install the [`Microsoft.Extensions.Configuration.Xml`](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.Xml) NuGet package.</span></span>

<span data-ttu-id="a5dba-142">Le code suivant illustre la configuration de fichiers XML à l’aide du fournisseur de configuration XML.</span><span class="sxs-lookup"><span data-stu-id="a5dba-142">The following code demonstrates configuration of XML files using the XML configuration provider.</span></span>

:::code language="csharp" source="snippets/configuration/console-xml/Program.cs" range="1-28,46,52-53" highlight="17-28":::

<span data-ttu-id="a5dba-143">Le code précédent :</span><span class="sxs-lookup"><span data-stu-id="a5dba-143">The preceding code:</span></span>

- <span data-ttu-id="a5dba-144">Efface tous les fournisseurs de configuration existants qui ont été ajoutés par défaut dans la <xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder(System.String[])> méthode.</span><span class="sxs-lookup"><span data-stu-id="a5dba-144">Clears all existing configuration providers that were added by default in the <xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder(System.String[])> method.</span></span>
- <span data-ttu-id="a5dba-145">Configure le fournisseur de configuration XML pour charger les fichiers *appsettings.xml* et *repeating-example.xml* avec les options suivantes :</span><span class="sxs-lookup"><span data-stu-id="a5dba-145">Configures the XML configuration provider to load the *appsettings.xml* and *repeating-example.xml* files with the following options:</span></span>
  - <span data-ttu-id="a5dba-146">`optional: true`: Le fichier est facultatif.</span><span class="sxs-lookup"><span data-stu-id="a5dba-146">`optional: true`: The file is optional.</span></span>
  - <span data-ttu-id="a5dba-147">`reloadOnChange: true` : Le fichier est rechargé lorsque des modifications sont enregistrées.</span><span class="sxs-lookup"><span data-stu-id="a5dba-147">`reloadOnChange: true` : The file is reloaded when changes are saved.</span></span>
- <span data-ttu-id="a5dba-148">Configure le fournisseur de configuration des variables d’environnement.</span><span class="sxs-lookup"><span data-stu-id="a5dba-148">Configures the environment variables configuration provider.</span></span>
- <span data-ttu-id="a5dba-149">Configure le fournisseur de configuration de ligne de commande si le donné `args` contient des arguments.</span><span class="sxs-lookup"><span data-stu-id="a5dba-149">Configures the command-line configuration provider if the given `args` contains arguments.</span></span>

<span data-ttu-id="a5dba-150">Les paramètres XML sont remplacés par les paramètres dans le [fournisseur de configuration des variables d’environnement](#environment-variable-configuration-provider) et le [fournisseur de configuration de ligne de commande](#command-line-configuration-provider).</span><span class="sxs-lookup"><span data-stu-id="a5dba-150">The XML settings are overridden by settings in the [Environment variables configuration provider](#environment-variable-configuration-provider) and the [Command-line configuration provider](#command-line-configuration-provider).</span></span>

<span data-ttu-id="a5dba-151">Voici un exemple *appsettings.xml* fichier avec différents paramètres de configuration :</span><span class="sxs-lookup"><span data-stu-id="a5dba-151">An example *appsettings.xml* file with various configuration settings follows:</span></span>

:::code language="xml" source="snippets/configuration/console-xml/appsettings.xml":::

<span data-ttu-id="a5dba-152">Les éléments répétitifs qui utilisent le même nom d’élément fonctionnent si l’attribut `name` est utilisé pour distinguer les éléments :</span><span class="sxs-lookup"><span data-stu-id="a5dba-152">Repeating elements that use the same element name work if the `name` attribute is used to distinguish the elements:</span></span>

:::code language="xml" source="snippets/configuration/console-xml/repeating-example.xml":::

<span data-ttu-id="a5dba-153">Le code suivant lit le fichier de configuration précédent et affiche les clés et les valeurs :</span><span class="sxs-lookup"><span data-stu-id="a5dba-153">The following code reads the previous configuration file and displays the keys and values:</span></span>

:::code language="csharp" source="snippets/configuration/console-xml/Program.cs" range="30-45":::

<span data-ttu-id="a5dba-154">L’application écrirait l’exemple de sortie suivant :</span><span class="sxs-lookup"><span data-stu-id="a5dba-154">The application would write the following sample output:</span></span>

:::code language="csharp" source="snippets/configuration/console-xml/Program.cs" range="47-51":::

<span data-ttu-id="a5dba-155">Les attributs peuvent être utilisés pour fournir des valeurs :</span><span class="sxs-lookup"><span data-stu-id="a5dba-155">Attributes can be used to supply values:</span></span>

```xml
<?xml version="1.0" encoding="UTF-8"?>
<configuration>
  <key attribute="value" />
  <section>
    <key attribute="value" />
  </section>
</configuration>
```

<span data-ttu-id="a5dba-156">Le fichier de configuration précédent charge les clés suivantes avec `value` :</span><span class="sxs-lookup"><span data-stu-id="a5dba-156">The previous configuration file loads the following keys with `value`:</span></span>

- `key:attribute`
- `section:key:attribute`

### <a name="ini-configuration-provider"></a><span data-ttu-id="a5dba-157">Fournisseur de configuration INI</span><span class="sxs-lookup"><span data-stu-id="a5dba-157">INI configuration provider</span></span>

<span data-ttu-id="a5dba-158">La <xref:Microsoft.Extensions.Configuration.Ini.IniConfigurationProvider> classe charge la configuration à partir d’un fichier ini au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="a5dba-158">The <xref:Microsoft.Extensions.Configuration.Ini.IniConfigurationProvider> class loads configuration from an INI file at runtime.</span></span> <span data-ttu-id="a5dba-159">Installez le [`Microsoft.Extensions.Configuration.Ini`](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.Ini)  package NuGet.</span><span class="sxs-lookup"><span data-stu-id="a5dba-159">Install the [`Microsoft.Extensions.Configuration.Ini`](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.Ini)  NuGet package.</span></span>

<span data-ttu-id="a5dba-160">Le code suivant efface tous les fournisseurs de configuration et ajoute le `IniConfigurationProvider` avec deux fichiers ini comme source :</span><span class="sxs-lookup"><span data-stu-id="a5dba-160">The following code clears all the configuration providers and adds the `IniConfigurationProvider` with two INI files as the source:</span></span>

:::code language="csharp" source="snippets/configuration/console-ini/Program.cs" range="1-31,38-39" highlight="18-24":::

<span data-ttu-id="a5dba-161">Voici un exemple *appsettings.ini* fichier avec différents paramètres de configuration :</span><span class="sxs-lookup"><span data-stu-id="a5dba-161">An example *appsettings.ini* file with various configuration settings follows:</span></span>

:::code language="ini" source="snippets/configuration/console-ini/appsettings.ini":::

<span data-ttu-id="a5dba-162">Le code suivant affiche les paramètres de configuration précédents en les écrivant dans la fenêtre de console :</span><span class="sxs-lookup"><span data-stu-id="a5dba-162">The following code displays the preceding configuration settings by writing them to the console window:</span></span>

:::code language="csharp" source="snippets/configuration/console-ini/Program.cs" range="26-30":::

<span data-ttu-id="a5dba-163">L’application écrirait l’exemple de sortie suivant :</span><span class="sxs-lookup"><span data-stu-id="a5dba-163">The application would write the following sample output:</span></span>

:::code language="csharp" source="snippets/configuration/console-ini/Program.cs" range="32-37":::

## <a name="environment-variable-configuration-provider"></a><span data-ttu-id="a5dba-164">Fournisseur de configuration de variable d’environnement</span><span class="sxs-lookup"><span data-stu-id="a5dba-164">Environment variable configuration provider</span></span>

<span data-ttu-id="a5dba-165">À l’aide de la configuration par défaut, le <xref:Microsoft.Extensions.Configuration.EnvironmentVariables.EnvironmentVariablesConfigurationProvider> charge la configuration à partir des paires clé-valeur de variable d’environnement après la lecture *appsettings.jssur*, *appSettings.* `Environment` *. JSON*et le gestionnaire de secret.</span><span class="sxs-lookup"><span data-stu-id="a5dba-165">Using the default configuration, the <xref:Microsoft.Extensions.Configuration.EnvironmentVariables.EnvironmentVariablesConfigurationProvider> loads configuration from environment variable key-value pairs after reading *appsettings.json*, *appsettings.*`Environment`*.json*, and Secret manager.</span></span> <span data-ttu-id="a5dba-166">Par conséquent, les valeurs de clés lues à partir de l’environnement remplacent les valeurs lues à partir de *appsettings.jssur*, *appSettings.* `Environment` *. JSON*et le gestionnaire de secret.</span><span class="sxs-lookup"><span data-stu-id="a5dba-166">Therefore, key values read from the environment override values read from *appsettings.json*, *appsettings.*`Environment`*.json*, and Secret manager.</span></span>

<span data-ttu-id="a5dba-167">Le `:` séparateur ne fonctionne pas avec les clés hiérarchiques de variable d’environnement sur toutes les plateformes.</span><span class="sxs-lookup"><span data-stu-id="a5dba-167">The `:` separator doesn't work with environment variable hierarchical keys on all platforms.</span></span> <span data-ttu-id="a5dba-168">Le trait de soulignement double ( `__` ) est automatiquement remplacé par un `:` et est pris en charge par toutes les plateformes.</span><span class="sxs-lookup"><span data-stu-id="a5dba-168">The double underscore (`__`) is automatically replaced by a `:` and is supported by all platforms.</span></span> <span data-ttu-id="a5dba-169">Par exemple, le `:` séparateur n’est pas pris en charge par [bash](https://linuxhint.com/bash-environment-variables), mais `__` est.</span><span class="sxs-lookup"><span data-stu-id="a5dba-169">For example, the `:` separator is not supported by [Bash](https://linuxhint.com/bash-environment-variables), but `__` is.</span></span>

<span data-ttu-id="a5dba-170">Les `set` commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="a5dba-170">The following `set` commands:</span></span>

- <span data-ttu-id="a5dba-171">Définissez les clés et les valeurs d’environnement de l’exemple précédent sur Windows.</span><span class="sxs-lookup"><span data-stu-id="a5dba-171">Set the environment keys and values of the preceding example on Windows.</span></span>
- <span data-ttu-id="a5dba-172">Testez les paramètres en les remplaçant par leurs valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="a5dba-172">Test the settings by changing them from their default values.</span></span> <span data-ttu-id="a5dba-173">La `dotnet run` commande doit être exécutée dans le répertoire du projet.</span><span class="sxs-lookup"><span data-stu-id="a5dba-173">The `dotnet run` command must be run in the project directory.</span></span>

```dotnetcli
set SecretKey="Secret key from environment"
set TransientFaultHandlingOptions__Enabled="true"
set TransientFaultHandlingOptions__AutoRetryDelay="00:00:13"

dotnet run
```

<span data-ttu-id="a5dba-174">Paramètres d’environnement précédents :</span><span class="sxs-lookup"><span data-stu-id="a5dba-174">The preceding environment settings:</span></span>

- <span data-ttu-id="a5dba-175">Sont uniquement définies dans les processus lancés à partir de la fenêtre de commande dans laquelle ils ont été définis.</span><span class="sxs-lookup"><span data-stu-id="a5dba-175">Are only set in processes launched from the command window they were set in.</span></span>
- <span data-ttu-id="a5dba-176">Ne seront pas lues par les applications Web lancées avec Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a5dba-176">Won't be read by web apps launched with Visual Studio.</span></span>

<span data-ttu-id="a5dba-177">Les commandes [setx](/windows-server/administration/windows-commands/setx) suivantes peuvent être utilisées pour définir les clés et les valeurs d’environnement sur Windows.</span><span class="sxs-lookup"><span data-stu-id="a5dba-177">The following [setx](/windows-server/administration/windows-commands/setx) commands can be used to set the environment keys and values on Windows.</span></span> <span data-ttu-id="a5dba-178">Contrairement à `set` , `setx` les paramètres sont conservés.</span><span class="sxs-lookup"><span data-stu-id="a5dba-178">Unlike `set`, `setx` settings are persisted.</span></span> <span data-ttu-id="a5dba-179">`/M` définit la variable dans l’environnement système.</span><span class="sxs-lookup"><span data-stu-id="a5dba-179">`/M` sets the variable in the system environment.</span></span> <span data-ttu-id="a5dba-180">Si le `/M` commutateur n’est pas utilisé, une variable d’environnement utilisateur est définie.</span><span class="sxs-lookup"><span data-stu-id="a5dba-180">If the `/M` switch isn't used, a user environment variable is set.</span></span>

```dotnetcli
setx SecretKey "Secret key from setx environment" /M
setx TransientFaultHandlingOptions__Enabled "true" /M
setx TransientFaultHandlingOptions__AutoRetryDelay "00:00:05" /M

dotnet run
```

<span data-ttu-id="a5dba-181">Pour vérifier que les commandes précédentes remplacent *appsettings.jssur* et *appSettings.* `Environment` *. JSON*:</span><span class="sxs-lookup"><span data-stu-id="a5dba-181">To test that the preceding commands override *appsettings.json* and *appsettings.*`Environment`*.json*:</span></span>

- <span data-ttu-id="a5dba-182">Avec Visual Studio : quittez et redémarrez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a5dba-182">With Visual Studio: Exit and restart Visual Studio.</span></span>
- <span data-ttu-id="a5dba-183">Avec l’interface CLI : démarrez une nouvelle fenêtre de commande et entrez `dotnet run` .</span><span class="sxs-lookup"><span data-stu-id="a5dba-183">With the CLI: Start a new command window and enter `dotnet run`.</span></span>

<span data-ttu-id="a5dba-184">Appelez <xref:Microsoft.Extensions.Configuration.EnvironmentVariablesExtensions.AddEnvironmentVariables%2A> avec une chaîne pour spécifier un préfixe pour les variables d’environnement :</span><span class="sxs-lookup"><span data-stu-id="a5dba-184">Call <xref:Microsoft.Extensions.Configuration.EnvironmentVariablesExtensions.AddEnvironmentVariables%2A> with a string to specify a prefix for environment variables:</span></span>

:::code language="csharp" source="snippets/configuration/console-env/Program.cs" highlight="15-16":::

<span data-ttu-id="a5dba-185">Dans le code précédent :</span><span class="sxs-lookup"><span data-stu-id="a5dba-185">In the preceding code:</span></span>

- <span data-ttu-id="a5dba-186">`config.AddEnvironmentVariables(prefix: "CustomPrefix_")` est ajouté après les fournisseurs de configuration par défaut.</span><span class="sxs-lookup"><span data-stu-id="a5dba-186">`config.AddEnvironmentVariables(prefix: "CustomPrefix_")` is added after the default configuration providers.</span></span> <span data-ttu-id="a5dba-187">Pour obtenir un exemple de classement des fournisseurs de configuration, consultez [fournisseur de configuration XML](#xml-configuration-provider).</span><span class="sxs-lookup"><span data-stu-id="a5dba-187">For an example of ordering the configuration providers, see [XML configuration provider](#xml-configuration-provider).</span></span>
- <span data-ttu-id="a5dba-188">Les variables d’environnement définies avec le `CustomPrefix_` préfixe remplacent les fournisseurs de configuration par défaut.</span><span class="sxs-lookup"><span data-stu-id="a5dba-188">Environment variables set with the `CustomPrefix_` prefix override the default configuration providers.</span></span> <span data-ttu-id="a5dba-189">Cela comprend les variables d’environnement sans le préfixe.</span><span class="sxs-lookup"><span data-stu-id="a5dba-189">This includes environment variables without the prefix.</span></span>

<span data-ttu-id="a5dba-190">Le préfixe est supprimé lorsque les paires clé-valeur de configuration sont lues.</span><span class="sxs-lookup"><span data-stu-id="a5dba-190">The prefix is stripped off when the configuration key-value pairs are read.</span></span>

<span data-ttu-id="a5dba-191">Les commandes suivantes testent le préfixe personnalisé :</span><span class="sxs-lookup"><span data-stu-id="a5dba-191">The following commands test the custom prefix:</span></span>

```dotnetcli
set CustomPrefix__SecretKey="Secret key with CustomPrefix_ environment"
set CustomPrefix_TransientFaultHandlingOptions__Enabled=true
set CustomPrefix_TransientFaultHandlingOptions__AutoRetryDelay=00:00:21

dotnet run
```

<span data-ttu-id="a5dba-192">La configuration par défaut charge les variables d’environnement et les arguments de ligne de commande précédés du préfixe `DOTNET_` .</span><span class="sxs-lookup"><span data-stu-id="a5dba-192">The default configuration loads environment variables and command-line arguments prefixed with `DOTNET_`.</span></span> <span data-ttu-id="a5dba-193">Le `DOTNET_` préfixe est utilisé par .net pour la configuration de l’hôte et de l’application, mais pas pour la configuration de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="a5dba-193">The `DOTNET_` prefix is used by .NET for host and app configuration, but not for user configuration.</span></span>
<!-- For more information on host and app configuration, see .NET Generic Host. -->

<span data-ttu-id="a5dba-194">Dans [Azure App service](https://azure.microsoft.com/services/app-service), sélectionnez **nouveau paramètre d’application** dans la page **paramètres > configuration** .</span><span class="sxs-lookup"><span data-stu-id="a5dba-194">On [Azure App Service](https://azure.microsoft.com/services/app-service), select **New application setting** on the **Settings > Configuration** page.</span></span> <span data-ttu-id="a5dba-195">Azure App Service paramètres de l’application sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="a5dba-195">Azure App Service application settings are:</span></span>

- <span data-ttu-id="a5dba-196">Chiffré au repos et transmis sur un canal chiffré.</span><span class="sxs-lookup"><span data-stu-id="a5dba-196">Encrypted at rest and transmitted over an encrypted channel.</span></span>
- <span data-ttu-id="a5dba-197">Exposés en tant que variables d’environnement.</span><span class="sxs-lookup"><span data-stu-id="a5dba-197">Exposed as environment variables.</span></span>

### <a name="connection-string-prefixes"></a><span data-ttu-id="a5dba-198">Préfixes des chaînes de connexion</span><span class="sxs-lookup"><span data-stu-id="a5dba-198">Connection string prefixes</span></span>

<span data-ttu-id="a5dba-199">L’API de configuration a des règles de traitement spéciales pour quatre variables d’environnement de chaîne de connexion.</span><span class="sxs-lookup"><span data-stu-id="a5dba-199">The Configuration API has special processing rules for four connection string environment variables.</span></span> <span data-ttu-id="a5dba-200">Ces chaînes de connexion sont impliquées dans la configuration des chaînes de connexion Azure pour l’environnement de l’application.</span><span class="sxs-lookup"><span data-stu-id="a5dba-200">These connection strings are involved in configuring Azure connection strings for the app environment.</span></span> <span data-ttu-id="a5dba-201">Les variables d’environnement avec les préfixes indiqués dans le tableau sont chargées dans l’application avec la configuration par défaut ou lorsqu’aucun préfixe n’est fourni à `AddEnvironmentVariables` .</span><span class="sxs-lookup"><span data-stu-id="a5dba-201">Environment variables with the prefixes shown in the table are loaded into the app with the default configuration or when no prefix is supplied to `AddEnvironmentVariables`.</span></span>

| <span data-ttu-id="a5dba-202">Préfixe de la chaîne de connexion</span><span class="sxs-lookup"><span data-stu-id="a5dba-202">Connection string prefix</span></span> | <span data-ttu-id="a5dba-203">Fournisseur</span><span class="sxs-lookup"><span data-stu-id="a5dba-203">Provider</span></span>                                                                |
|--------------------------|-------------------------------------------------------------------------|
| `CUSTOMCONNSTR_`         | <span data-ttu-id="a5dba-204">Fournisseur personnalisé</span><span class="sxs-lookup"><span data-stu-id="a5dba-204">Custom provider</span></span>                                                         |
| `MYSQLCONNSTR_`          | [<span data-ttu-id="a5dba-205">MySQL</span><span class="sxs-lookup"><span data-stu-id="a5dba-205">MySQL</span></span>](https://www.mysql.com)                                          |
| `SQLAZURECONNSTR_`       | [<span data-ttu-id="a5dba-206">Azure SQL Database</span><span class="sxs-lookup"><span data-stu-id="a5dba-206">Azure SQL Database</span></span>](https://azure.microsoft.com/services/sql-database) |
| `SQLCONNSTR_`            | [<span data-ttu-id="a5dba-207">SQL Server</span><span class="sxs-lookup"><span data-stu-id="a5dba-207">SQL Server</span></span>](https://www.microsoft.com/sql-server)                      |

<span data-ttu-id="a5dba-208">Quand une variable d’environnement est découverte et chargée dans la configuration avec l’un des quatre préfixes indiqués dans le tableau :</span><span class="sxs-lookup"><span data-stu-id="a5dba-208">When an environment variable is discovered and loaded into configuration with any of the four prefixes shown in the table:</span></span>

- <span data-ttu-id="a5dba-209">La clé de configuration est créée en supprimant le préfixe de la variable d’environnement et en ajoutant une section de clé de configuration (`ConnectionStrings`).</span><span class="sxs-lookup"><span data-stu-id="a5dba-209">The configuration key is created by removing the environment variable prefix and adding a configuration key section (`ConnectionStrings`).</span></span>
- <span data-ttu-id="a5dba-210">Une nouvelle paire clé-valeur de configuration est créée qui représente le fournisseur de connexion de base de données (à l’exception de `CUSTOMCONNSTR_`, qui ne possède aucun fournisseur indiqué).</span><span class="sxs-lookup"><span data-stu-id="a5dba-210">A new configuration key-value pair is created that represents the database connection provider (except for `CUSTOMCONNSTR_`, which has no stated provider).</span></span>

| <span data-ttu-id="a5dba-211">Clé de variable d’environnement</span><span class="sxs-lookup"><span data-stu-id="a5dba-211">Environment variable key</span></span> | <span data-ttu-id="a5dba-212">Clé de configuration convertie</span><span class="sxs-lookup"><span data-stu-id="a5dba-212">Converted configuration key</span></span> | <span data-ttu-id="a5dba-213">Entrée de configuration de fournisseur</span><span class="sxs-lookup"><span data-stu-id="a5dba-213">Provider configuration entry</span></span>                                                    |
|--------------------------|-----------------------------|---------------------------------------------------------------------------------|
| `CUSTOMCONNSTR_{KEY}`    | `ConnectionStrings:{KEY}`   | <span data-ttu-id="a5dba-214">Entrée de configuration non créée.</span><span class="sxs-lookup"><span data-stu-id="a5dba-214">Configuration entry not created.</span></span>                                                |
| `MYSQLCONNSTR_{KEY}`     | `ConnectionStrings:{KEY}`   | <span data-ttu-id="a5dba-215">Clé : `ConnectionStrings:{KEY}_ProviderName` :</span><span class="sxs-lookup"><span data-stu-id="a5dba-215">Key: `ConnectionStrings:{KEY}_ProviderName`:</span></span><br><span data-ttu-id="a5dba-216">Valeur: `MySql.Data.MySqlClient`</span><span class="sxs-lookup"><span data-stu-id="a5dba-216">Value: `MySql.Data.MySqlClient`</span></span> |
| `SQLAZURECONNSTR_{KEY}`  | `ConnectionStrings:{KEY}`   | <span data-ttu-id="a5dba-217">Clé : `ConnectionStrings:{KEY}_ProviderName` :</span><span class="sxs-lookup"><span data-stu-id="a5dba-217">Key: `ConnectionStrings:{KEY}_ProviderName`:</span></span><br><span data-ttu-id="a5dba-218">Valeur: `System.Data.SqlClient`</span><span class="sxs-lookup"><span data-stu-id="a5dba-218">Value: `System.Data.SqlClient`</span></span>  |
| `SQLCONNSTR_{KEY}`       | `ConnectionStrings:{KEY}`   | <span data-ttu-id="a5dba-219">Clé : `ConnectionStrings:{KEY}_ProviderName` :</span><span class="sxs-lookup"><span data-stu-id="a5dba-219">Key: `ConnectionStrings:{KEY}_ProviderName`:</span></span><br><span data-ttu-id="a5dba-220">Valeur: `System.Data.SqlClient`</span><span class="sxs-lookup"><span data-stu-id="a5dba-220">Value: `System.Data.SqlClient`</span></span>  |

### <a name="environment-variables-set-in-launchsettingsjson"></a><span data-ttu-id="a5dba-221">Variables d’environnement définies dans launchSettings.jssur</span><span class="sxs-lookup"><span data-stu-id="a5dba-221">Environment variables set in launchSettings.json</span></span>

<span data-ttu-id="a5dba-222">Les variables d’environnement définies dans *launchSettings.jslors de* la substitution de celles définies dans l’environnement système.</span><span class="sxs-lookup"><span data-stu-id="a5dba-222">Environment variables set in *launchSettings.json* override those set in the system environment.</span></span>

## <a name="command-line-configuration-provider"></a><span data-ttu-id="a5dba-223">Fournisseur de configuration de ligne de commande</span><span class="sxs-lookup"><span data-stu-id="a5dba-223">Command-line configuration provider</span></span>

<span data-ttu-id="a5dba-224">À l’aide de la configuration par défaut, le <xref:Microsoft.Extensions.Configuration.CommandLine.CommandLineConfigurationProvider> charge la configuration à partir de paires clé-valeur d’argument de ligne de commande après les sources de configuration suivantes :</span><span class="sxs-lookup"><span data-stu-id="a5dba-224">Using the default configuration, the <xref:Microsoft.Extensions.Configuration.CommandLine.CommandLineConfigurationProvider> loads configuration from command-line argument key-value pairs after the following configuration sources:</span></span>

- <span data-ttu-id="a5dba-225">*appsettings.jssur* et *appSettings*. `Environment` fichiers *JSON* .</span><span class="sxs-lookup"><span data-stu-id="a5dba-225">*appsettings.json* and *appsettings*.`Environment`.*json* files.</span></span>
- <span data-ttu-id="a5dba-226">Secrets d’application (gestionnaire de secret) dans l' `Development` environnement.</span><span class="sxs-lookup"><span data-stu-id="a5dba-226">App secrets (Secret Manager) in the `Development` environment.</span></span>
- <span data-ttu-id="a5dba-227">Variables d'environnement.</span><span class="sxs-lookup"><span data-stu-id="a5dba-227">Environment variables.</span></span>

<span data-ttu-id="a5dba-228">Par défaut, les valeurs de configuration définies sur la ligne de commande remplacent les valeurs de configuration définies avec tous les autres fournisseurs de configuration.</span><span class="sxs-lookup"><span data-stu-id="a5dba-228">By default, configuration values set on the command line override configuration values set with all the other configuration providers.</span></span>

### <a name="command-line-arguments"></a><span data-ttu-id="a5dba-229">Arguments de ligne de commande</span><span class="sxs-lookup"><span data-stu-id="a5dba-229">Command-line arguments</span></span>

<span data-ttu-id="a5dba-230">La commande suivante définit des clés et des valeurs à l’aide de `=` :</span><span class="sxs-lookup"><span data-stu-id="a5dba-230">The following command sets keys and values using `=`:</span></span>

```dotnetcli
dotnet run SecretKey="Secret key from command line"
```

<span data-ttu-id="a5dba-231">La commande suivante définit des clés et des valeurs à l’aide de `/` :</span><span class="sxs-lookup"><span data-stu-id="a5dba-231">The following command sets keys and values using `/`:</span></span>

```dotnetcli
dotnet run /SecretKey "Secret key set from forward slash"
```

<span data-ttu-id="a5dba-232">La commande suivante définit des clés et des valeurs à l’aide de `--` :</span><span class="sxs-lookup"><span data-stu-id="a5dba-232">The following command sets keys and values using `--`:</span></span>

```dotnetcli
dotnet run --SecretKey "Secret key set from double hyphen"
```

<span data-ttu-id="a5dba-233">Valeur de la clé :</span><span class="sxs-lookup"><span data-stu-id="a5dba-233">The key value:</span></span>

- <span data-ttu-id="a5dba-234">Doit suivre `=` ou la clé doit avoir un préfixe `--` ou `/` lorsque la valeur suit un espace.</span><span class="sxs-lookup"><span data-stu-id="a5dba-234">Must follow `=`, or the key must have a prefix of `--` or `/` when the value follows a space.</span></span>
- <span data-ttu-id="a5dba-235">N’est pas obligatoire si `=` est utilisé.</span><span class="sxs-lookup"><span data-stu-id="a5dba-235">Isn't required if `=` is used.</span></span> <span data-ttu-id="a5dba-236">Par exemple : `SomeKey=`.</span><span class="sxs-lookup"><span data-stu-id="a5dba-236">For example, `SomeKey=`.</span></span>

<span data-ttu-id="a5dba-237">Dans la même commande, ne mélangez pas les paires clé-valeur d’argument de ligne de commande qui utilisent `=` des paires clé-valeur utilisant un espace.</span><span class="sxs-lookup"><span data-stu-id="a5dba-237">Within the same command, don't mix command-line argument key-value pairs that use `=` with key-value pairs that use a space.</span></span>

## <a name="key-per-file-configuration-provider"></a><span data-ttu-id="a5dba-238">Fournisseur de configuration de clé par fichier</span><span class="sxs-lookup"><span data-stu-id="a5dba-238">Key-per-file configuration provider</span></span>

<span data-ttu-id="a5dba-239">Le <xref:Microsoft.Extensions.Configuration.KeyPerFile.KeyPerFileConfigurationProvider> utilise les fichiers d’un répertoire en tant que paires clé-valeur de configuration.</span><span class="sxs-lookup"><span data-stu-id="a5dba-239">The <xref:Microsoft.Extensions.Configuration.KeyPerFile.KeyPerFileConfigurationProvider> uses a directory's files as configuration key-value pairs.</span></span> <span data-ttu-id="a5dba-240">La clé est le nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="a5dba-240">The key is the file name.</span></span> <span data-ttu-id="a5dba-241">La valeur est le contenu du fichier.</span><span class="sxs-lookup"><span data-stu-id="a5dba-241">The value is the file's contents.</span></span> <span data-ttu-id="a5dba-242">Le fournisseur de configuration par fichier clé est utilisé dans les scénarios d’hébergement de l’ancrage.</span><span class="sxs-lookup"><span data-stu-id="a5dba-242">The Key-per-file configuration provider is used in Docker hosting scenarios.</span></span>

<span data-ttu-id="a5dba-243">Pour activer la configuration clé par fichier, appelez la méthode d’extension <xref:Microsoft.Extensions.Configuration.KeyPerFileConfigurationBuilderExtensions.AddKeyPerFile%2A> sur une instance de <xref:Microsoft.Extensions.Configuration.ConfigurationBuilder>.</span><span class="sxs-lookup"><span data-stu-id="a5dba-243">To activate key-per-file configuration, call the <xref:Microsoft.Extensions.Configuration.KeyPerFileConfigurationBuilderExtensions.AddKeyPerFile%2A> extension method on an instance of <xref:Microsoft.Extensions.Configuration.ConfigurationBuilder>.</span></span> <span data-ttu-id="a5dba-244">Le `directoryPath` aux fichiers doit être un chemin d’accès absolu.</span><span class="sxs-lookup"><span data-stu-id="a5dba-244">The `directoryPath` to the files must be an absolute path.</span></span>

<span data-ttu-id="a5dba-245">Les surcharges permettent de spécifier :</span><span class="sxs-lookup"><span data-stu-id="a5dba-245">Overloads permit specifying:</span></span>

- <span data-ttu-id="a5dba-246">Un délégué `Action<KeyPerFileConfigurationSource>` qui configure la source.</span><span class="sxs-lookup"><span data-stu-id="a5dba-246">An `Action<KeyPerFileConfigurationSource>` delegate that configures the source.</span></span>
- <span data-ttu-id="a5dba-247">Si le répertoire est facultatif et le chemin d’accès au répertoire.</span><span class="sxs-lookup"><span data-stu-id="a5dba-247">Whether the directory is optional and the path to the directory.</span></span>

<span data-ttu-id="a5dba-248">Le double trait de soulignement (`__`) est utilisé comme un délimiteur de clé de configuration dans les noms de fichiers.</span><span class="sxs-lookup"><span data-stu-id="a5dba-248">The double-underscore (`__`) is used as a configuration key delimiter in file names.</span></span> <span data-ttu-id="a5dba-249">Par exemple, le nom de fichier `Logging__LogLevel__System` génère la clé de configuration `Logging:LogLevel:System`.</span><span class="sxs-lookup"><span data-stu-id="a5dba-249">For example, the file name `Logging__LogLevel__System` produces the configuration key `Logging:LogLevel:System`.</span></span>

<span data-ttu-id="a5dba-250">Appelez `ConfigureAppConfiguration` lors de la création de l’hôte pour spécifier la configuration de l’application :</span><span class="sxs-lookup"><span data-stu-id="a5dba-250">Call `ConfigureAppConfiguration` when building the host to specify the app's configuration:</span></span>

```csharp
.ConfigureAppConfiguration((_, configuration) =>
{
    var path = Path.Combine(
        Directory.GetCurrentDirectory(), "path/to/files");

    configuration.AddKeyPerFile(directoryPath: path, optional: true);
})
```

## <a name="memory-configuration-provider"></a><span data-ttu-id="a5dba-251">Fournisseur de configuration de la mémoire</span><span class="sxs-lookup"><span data-stu-id="a5dba-251">Memory configuration provider</span></span>

<span data-ttu-id="a5dba-252">Le <xref:Microsoft.Extensions.Configuration.Memory.MemoryConfigurationProvider> utilise une collection en mémoire en tant que paires clé-valeur de configuration.</span><span class="sxs-lookup"><span data-stu-id="a5dba-252">The <xref:Microsoft.Extensions.Configuration.Memory.MemoryConfigurationProvider> uses an in-memory collection as configuration key-value pairs.</span></span>

<span data-ttu-id="a5dba-253">Le code suivant ajoute une collection de mémoire au système de configuration :</span><span class="sxs-lookup"><span data-stu-id="a5dba-253">The following code adds a memory collection to the configuration system:</span></span>

:::code language="csharp" source="snippets/configuration/console-memory/Program.cs" highlight="16-23":::

<span data-ttu-id="a5dba-254">Dans le code précédent, <xref:Microsoft.Extensions.Configuration.MemoryConfigurationBuilderExtensions.AddInMemoryCollection(Microsoft.Extensions.Configuration.IConfigurationBuilder,System.Collections.Generic.IEnumerable{System.Collections.Generic.KeyValuePair{System.String,System.String}})?displayProperty=nameWithType> ajoute le fournisseur de mémoire après les fournisseurs de configuration par défaut.</span><span class="sxs-lookup"><span data-stu-id="a5dba-254">In the preceding code, <xref:Microsoft.Extensions.Configuration.MemoryConfigurationBuilderExtensions.AddInMemoryCollection(Microsoft.Extensions.Configuration.IConfigurationBuilder,System.Collections.Generic.IEnumerable{System.Collections.Generic.KeyValuePair{System.String,System.String}})?displayProperty=nameWithType> adds the memory provider after the default configuration providers.</span></span> <span data-ttu-id="a5dba-255">Pour obtenir un exemple de classement des fournisseurs de configuration, consultez [fournisseur de configuration XML](#xml-configuration-provider).</span><span class="sxs-lookup"><span data-stu-id="a5dba-255">For an example of ordering the configuration providers, see [XML configuration provider](#xml-configuration-provider).</span></span>

## <a name="see-also"></a><span data-ttu-id="a5dba-256">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a5dba-256">See also</span></span>

- [<span data-ttu-id="a5dba-257">Configuration dans .NET</span><span class="sxs-lookup"><span data-stu-id="a5dba-257">Configuration in .NET</span></span>](configuration.md)
- [<span data-ttu-id="a5dba-258">Implémenter un fournisseur de configuration personnalisé</span><span class="sxs-lookup"><span data-stu-id="a5dba-258">Implement a custom configuration provider</span></span>](custom-configuration-provider.md)
