---
title: Scripts dotnet-install
description: En savoir plus sur les scripts dotnet-install pour installer les kit SDK .NET Core et le runtime partagé.
ms.date: 04/30/2020
ms.openlocfilehash: 8f27b8a7794e84e6e2b288d6cc2ec33ffcb7600f
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90538040"
---
# <a name="dotnet-install-scripts-reference"></a><span data-ttu-id="482a8-103">Documentation sur les scripts dotnet-install</span><span class="sxs-lookup"><span data-stu-id="482a8-103">dotnet-install scripts reference</span></span>

## <a name="name"></a><span data-ttu-id="482a8-104">Name</span><span class="sxs-lookup"><span data-stu-id="482a8-104">Name</span></span>

<span data-ttu-id="482a8-105">`dotnet-install.ps1` | `dotnet-install.sh` -Script utilisé pour installer le kit SDK .NET Core et le runtime partagé.</span><span class="sxs-lookup"><span data-stu-id="482a8-105">`dotnet-install.ps1` | `dotnet-install.sh` - Script used to install the .NET Core SDK and the shared runtime.</span></span>

## <a name="synopsis"></a><span data-ttu-id="482a8-106">Synopsis</span><span class="sxs-lookup"><span data-stu-id="482a8-106">Synopsis</span></span>

<span data-ttu-id="482a8-107">Windows :</span><span class="sxs-lookup"><span data-stu-id="482a8-107">Windows:</span></span>

```powershell
dotnet-install.ps1 [-Architecture <ARCHITECTURE>] [-AzureFeed]
    [-Channel <CHANNEL>] [-DryRun] [-FeedCredential]
    [-InstallDir <DIRECTORY>] [-JSonFile <JSONFILE>]
    [-NoCdn] [-NoPath] [-ProxyAddress] [-ProxyBypassList <LIST_OF_URLS>]
    [-ProxyUseDefaultCredentials] [-Runtime <RUNTIME>]
    [-SkipNonVersionedFiles] [-UncachedFeed] [-Verbose]
    [-Version <VERSION>]

Get-Help ./dotnet-install.ps1
```

<span data-ttu-id="482a8-108">Linux/macOS :</span><span class="sxs-lookup"><span data-stu-id="482a8-108">Linux/macOS:</span></span>

```bash
dotnet-install.sh  [--architecture <ARCHITECTURE>] [--azure-feed]
    [--channel <CHANNEL>] [--dry-run] [--feed-credential]
    [--install-dir <DIRECTORY>] [--jsonfile <JSONFILE>]
    [--no-cdn] [--no-path] [--runtime <RUNTIME>] [--runtime-id <RID>]
    [--skip-non-versioned-files] [--uncached-feed] [--verbose]
    [--version <VERSION>]

dotnet-install.sh --help
```

<span data-ttu-id="482a8-109">Comme le script bash lit également les commutateurs PowerShell, vous pouvez utiliser ces derniers avec le script sur les systèmes Linux/macOS.</span><span class="sxs-lookup"><span data-stu-id="482a8-109">The bash script also reads PowerShell switches, so you can use PowerShell switches with the script on Linux/macOS systems.</span></span>

## <a name="description"></a><span data-ttu-id="482a8-110">Description</span><span class="sxs-lookup"><span data-stu-id="482a8-110">Description</span></span>

<span data-ttu-id="482a8-111">Les `dotnet-install` scripts effectuent une installation non-administrateur du kit SDK .net Core, qui comprend le CLI .net Core et le runtime partagé.</span><span class="sxs-lookup"><span data-stu-id="482a8-111">The `dotnet-install` scripts perform a non-admin installation of the .NET Core SDK, which includes the .NET Core CLI and the shared runtime.</span></span> <span data-ttu-id="482a8-112">Il existe deux scripts :</span><span class="sxs-lookup"><span data-stu-id="482a8-112">There are two scripts:</span></span>

* <span data-ttu-id="482a8-113">Script PowerShell qui fonctionne sous Windows.</span><span class="sxs-lookup"><span data-stu-id="482a8-113">A PowerShell script that works on Windows.</span></span>
* <span data-ttu-id="482a8-114">Script bash qui fonctionne sur Linux/macOS.</span><span class="sxs-lookup"><span data-stu-id="482a8-114">A bash script that works on Linux/macOS.</span></span>

### <a name="purpose"></a><span data-ttu-id="482a8-115">Objectif</span><span class="sxs-lookup"><span data-stu-id="482a8-115">Purpose</span></span>

 <span data-ttu-id="482a8-116">L’utilisation prévue des scripts concerne les scénarios d’intégration continue (CI), où :</span><span class="sxs-lookup"><span data-stu-id="482a8-116">The intended use of the scripts is for Continuous Integration (CI) scenarios, where:</span></span>

* <span data-ttu-id="482a8-117">Le kit de développement logiciel (SDK) doit être installé sans intervention de l’utilisateur et sans droits d’administrateur.</span><span class="sxs-lookup"><span data-stu-id="482a8-117">The SDK needs to be installed without user interaction and without admin rights.</span></span>
* <span data-ttu-id="482a8-118">L’installation du SDK n’a pas besoin d’être conservée sur plusieurs exécutions d’intégration continue.</span><span class="sxs-lookup"><span data-stu-id="482a8-118">The SDK installation doesn't need to persist across multiple CI runs.</span></span>

  <span data-ttu-id="482a8-119">Séquence d’événements typique :</span><span class="sxs-lookup"><span data-stu-id="482a8-119">The typical sequence of events:</span></span>
  * <span data-ttu-id="482a8-120">L’élément CI est déclenché.</span><span class="sxs-lookup"><span data-stu-id="482a8-120">CI is triggered.</span></span>
  * <span data-ttu-id="482a8-121">CI installe le kit de développement logiciel (SDK) à l’aide de l’un de ces scripts.</span><span class="sxs-lookup"><span data-stu-id="482a8-121">CI installs the SDK using one of these scripts.</span></span>
  * <span data-ttu-id="482a8-122">CI termine son travail et efface les données temporaires, y compris l’installation du kit de développement logiciel (SDK).</span><span class="sxs-lookup"><span data-stu-id="482a8-122">CI finishes its work and clears temporary data including the SDK installation.</span></span>

<span data-ttu-id="482a8-123">Pour configurer un environnement de développement ou pour exécuter des applications, utilisez les programmes d’installation plutôt que ces scripts.</span><span class="sxs-lookup"><span data-stu-id="482a8-123">To set up a development environment or to run apps, use the installers rather than these scripts.</span></span>

### <a name="recommended-version"></a><span data-ttu-id="482a8-124">Version recommandée</span><span class="sxs-lookup"><span data-stu-id="482a8-124">Recommended version</span></span>

<span data-ttu-id="482a8-125">Nous vous recommandons d’utiliser la version stable des scripts :</span><span class="sxs-lookup"><span data-stu-id="482a8-125">We recommend that you use the stable version of the scripts:</span></span>

- <span data-ttu-id="482a8-126">Bash (Linux/macOS) : <https://dot.net/v1/dotnet-install.sh></span><span class="sxs-lookup"><span data-stu-id="482a8-126">Bash (Linux/macOS): <https://dot.net/v1/dotnet-install.sh></span></span>
- <span data-ttu-id="482a8-127">PowerShell (Windows) : <https://dot.net/v1/dotnet-install.ps1></span><span class="sxs-lookup"><span data-stu-id="482a8-127">PowerShell (Windows): <https://dot.net/v1/dotnet-install.ps1></span></span>

### <a name="script-behavior"></a><span data-ttu-id="482a8-128">Comportement du script</span><span class="sxs-lookup"><span data-stu-id="482a8-128">Script behavior</span></span>

<span data-ttu-id="482a8-129">Les deux scripts ont le même comportement.</span><span class="sxs-lookup"><span data-stu-id="482a8-129">Both scripts have the same behavior.</span></span> <span data-ttu-id="482a8-130">Ils téléchargent le fichier ZIP/tarball à partir de la build CLI, puis poursuivent l’installation dans l’emplacement par défaut ou dans un emplacement spécifié par `-InstallDir|--install-dir` .</span><span class="sxs-lookup"><span data-stu-id="482a8-130">They download the ZIP/tarball file from the CLI build drops and proceed to install it in either the default location or in a location specified by `-InstallDir|--install-dir`.</span></span>

<span data-ttu-id="482a8-131">Par défaut, les scripts d’installation téléchargent et installent le Kit de développement logiciel (SDK).</span><span class="sxs-lookup"><span data-stu-id="482a8-131">By default, the installation scripts download the SDK and install it.</span></span> <span data-ttu-id="482a8-132">Si vous souhaitez obtenir uniquement le runtime partagé, spécifiez l’argument `-Runtime|--runtime`.</span><span class="sxs-lookup"><span data-stu-id="482a8-132">If you wish to only obtain the shared runtime, specify the `-Runtime|--runtime` argument.</span></span>

<span data-ttu-id="482a8-133">Par défaut, le script ajoute l’emplacement d’installation $PATH pour la session active.</span><span class="sxs-lookup"><span data-stu-id="482a8-133">By default, the script adds the install location to the $PATH for the current session.</span></span> <span data-ttu-id="482a8-134">Remplacez ce comportement par défaut en spécifiant l’argument `-NoPath|--no-path`.</span><span class="sxs-lookup"><span data-stu-id="482a8-134">Override this default behavior by specifying the `-NoPath|--no-path` argument.</span></span> <span data-ttu-id="482a8-135">Le script ne définit pas la `DOTNET_ROOT` variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="482a8-135">The script doesn't set the `DOTNET_ROOT` environment variable.</span></span>

<span data-ttu-id="482a8-136">Avant d’exécuter le script, installez les [dépendances](../install/windows.md#dependencies) nécessaires.</span><span class="sxs-lookup"><span data-stu-id="482a8-136">Before running the script, install the required [dependencies](../install/windows.md#dependencies).</span></span>

<span data-ttu-id="482a8-137">Vous pouvez installer une version spécifique à l’aide de l’argument `-Version|--version`.</span><span class="sxs-lookup"><span data-stu-id="482a8-137">You can install a specific version using the `-Version|--version` argument.</span></span> <span data-ttu-id="482a8-138">La version doit être spécifiée sous la forme d’un numéro de version en trois parties, tel que `2.1.0` .</span><span class="sxs-lookup"><span data-stu-id="482a8-138">The version must be specified as a three-part version number, such as `2.1.0`.</span></span> <span data-ttu-id="482a8-139">Si la version n’est pas spécifiée, le script installe la `latest` version.</span><span class="sxs-lookup"><span data-stu-id="482a8-139">If the version isn't specified, the script installs the `latest` version.</span></span>

<span data-ttu-id="482a8-140">Les scripts d’installation ne mettent pas à jour le registre sur Windows.</span><span class="sxs-lookup"><span data-stu-id="482a8-140">The install scripts do not update the registry on Windows.</span></span> <span data-ttu-id="482a8-141">Ils téléchargent simplement les fichiers binaires Zippés et les copient dans un dossier.</span><span class="sxs-lookup"><span data-stu-id="482a8-141">They just download the zipped binaries and copy them to a folder.</span></span> <span data-ttu-id="482a8-142">Si vous souhaitez que les valeurs de clé de registre soient mises à jour, utilisez les programmes d’installation de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="482a8-142">If you want registry key values to be updated, use the .NET Core installers.</span></span>

## <a name="options"></a><span data-ttu-id="482a8-143">Options</span><span class="sxs-lookup"><span data-stu-id="482a8-143">Options</span></span>

- **`-Architecture|--architecture <ARCHITECTURE>`**

  <span data-ttu-id="482a8-144">Architecture des fichiers binaires .NET Core à installer.</span><span class="sxs-lookup"><span data-stu-id="482a8-144">Architecture of the .NET Core binaries to install.</span></span> <span data-ttu-id="482a8-145">Les valeurs possibles sont `<auto>`, `amd64`, `x64`, `x86`, `arm64` et `arm`.</span><span class="sxs-lookup"><span data-stu-id="482a8-145">Possible values are `<auto>`, `amd64`, `x64`, `x86`, `arm64`, and `arm`.</span></span> <span data-ttu-id="482a8-146">La valeur par défaut est `<auto>`, qui représente l’architecture de système d’exploitation en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="482a8-146">The default value is `<auto>`, which represents the currently running OS architecture.</span></span>

- **`-AzureFeed|--azure-feed`**

  <span data-ttu-id="482a8-147">Spécifie l’URL du flux Azure à utiliser par ce programme d’installation.</span><span class="sxs-lookup"><span data-stu-id="482a8-147">Specifies the URL for the Azure feed to the installer.</span></span> <span data-ttu-id="482a8-148">Nous recommandons de ne pas modifier cette valeur.</span><span class="sxs-lookup"><span data-stu-id="482a8-148">We recommended that you don't change this value.</span></span> <span data-ttu-id="482a8-149">La valeur par défaut est `https://dotnetcli.azureedge.net/dotnet`.</span><span class="sxs-lookup"><span data-stu-id="482a8-149">The default value is `https://dotnetcli.azureedge.net/dotnet`.</span></span>

- **`-Channel|--channel <CHANNEL>`**

  <span data-ttu-id="482a8-150">Spécifie le canal source pour l’installation.</span><span class="sxs-lookup"><span data-stu-id="482a8-150">Specifies the source channel for the installation.</span></span> <span data-ttu-id="482a8-151">Les valeurs possibles sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="482a8-151">The possible values are:</span></span>

  - <span data-ttu-id="482a8-152">`Current` - Version la plus récente.</span><span class="sxs-lookup"><span data-stu-id="482a8-152">`Current` - Most current release.</span></span>
  - <span data-ttu-id="482a8-153">`LTS` - Canal de prise en charge à long terme (dernière version prise en charge).</span><span class="sxs-lookup"><span data-stu-id="482a8-153">`LTS` - Long-Term Support channel (most current supported release).</span></span>
  - <span data-ttu-id="482a8-154">Version en deux parties au format X.Y représentant une version spécifique (par exemple, `2.1` ou `3.0`).</span><span class="sxs-lookup"><span data-stu-id="482a8-154">Two-part version in X.Y format representing a specific release (for example, `2.1` or `3.0`).</span></span>
  - <span data-ttu-id="482a8-155">Nom de la branche : par exemple, `release/3.1.1xx` ou `master` (pour les versions nocturnes).</span><span class="sxs-lookup"><span data-stu-id="482a8-155">Branch name: for example, `release/3.1.1xx` or `master` (for nightly releases).</span></span> <span data-ttu-id="482a8-156">Utilisez cette option pour installer une version à partir d’un canal de préversion.</span><span class="sxs-lookup"><span data-stu-id="482a8-156">Use this option to install a version from a preview channel.</span></span> <span data-ttu-id="482a8-157">Utilisez le nom du canal tel qu’il figure dans [programmes d’installation et binaires](https://github.com/dotnet/core-sdk#installers-and-binaries).</span><span class="sxs-lookup"><span data-stu-id="482a8-157">Use the name of the channel as listed in [Installers and Binaries](https://github.com/dotnet/core-sdk#installers-and-binaries).</span></span>

  <span data-ttu-id="482a8-158">La valeur par défaut est `LTS`.</span><span class="sxs-lookup"><span data-stu-id="482a8-158">The default value is `LTS`.</span></span> <span data-ttu-id="482a8-159">Pour plus d’informations sur les canaux de prise en charge de .NET, consultez la page [Stratégie de prise en charge .NET](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="482a8-159">For more information on .NET support channels, see the [.NET Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) page.</span></span>

- **`-DryRun|--dry-run`**

  <span data-ttu-id="482a8-160">Si cette option est définie, le script n’effectue pas l’installation.</span><span class="sxs-lookup"><span data-stu-id="482a8-160">If set, the script won't perform the installation.</span></span> <span data-ttu-id="482a8-161">Affiche à la place la ligne de commande à utiliser pour installer la version de l’interface CLI .NET Core actuellement demandée.</span><span class="sxs-lookup"><span data-stu-id="482a8-161">Instead, it displays what command line to use to consistently install the currently requested version of the .NET Core CLI.</span></span> <span data-ttu-id="482a8-162">Par exemple, si vous spécifiez la version `latest`, elle affiche un lien avec la version spécifique, pour que cette commande puisse être utilisée de façon déterministe dans un script de génération.</span><span class="sxs-lookup"><span data-stu-id="482a8-162">For example, if you specify version `latest`, it displays a link with the specific version so that this command can be used deterministically in a build script.</span></span> <span data-ttu-id="482a8-163">Elle affiche également l’emplacement du fichier binaire si vous préférez l’installer ou le télécharger vous-même.</span><span class="sxs-lookup"><span data-stu-id="482a8-163">It also displays the binary's location if you prefer to install or download it yourself.</span></span>

- **`-FeedCredential|--feed-credential`**

  <span data-ttu-id="482a8-164">Valeur utilisée comme chaîne de requête à ajouter au flux Azure.</span><span class="sxs-lookup"><span data-stu-id="482a8-164">Used as a query string to append to the Azure feed.</span></span> <span data-ttu-id="482a8-165">Elle permet de changer l’URL afin d’utiliser des comptes de stockage d’objets blob non publics.</span><span class="sxs-lookup"><span data-stu-id="482a8-165">It allows changing the URL to use non-public blob storage accounts.</span></span>

- **`--help`**

  <span data-ttu-id="482a8-166">Affiche l’aide pour le script.</span><span class="sxs-lookup"><span data-stu-id="482a8-166">Prints out help for the script.</span></span> <span data-ttu-id="482a8-167">S’applique uniquement au script bash.</span><span class="sxs-lookup"><span data-stu-id="482a8-167">Applies only to bash script.</span></span> <span data-ttu-id="482a8-168">Pour PowerShell, utilisez `Get-Help ./dotnet-install.ps1` .</span><span class="sxs-lookup"><span data-stu-id="482a8-168">For PowerShell, use `Get-Help ./dotnet-install.ps1`.</span></span>

- **`-InstallDir|--install-dir <DIRECTORY>`**

  <span data-ttu-id="482a8-169">Spécifie le chemin d’accès de l’installation.</span><span class="sxs-lookup"><span data-stu-id="482a8-169">Specifies the installation path.</span></span> <span data-ttu-id="482a8-170">S’il n’existe pas déjà, le répertoire est créé.</span><span class="sxs-lookup"><span data-stu-id="482a8-170">The directory is created if it doesn't exist.</span></span> <span data-ttu-id="482a8-171">La valeur par défaut est *%LocalAppData%\Microsoft\dotnet* sur Windows et */usr/share/dotnet* sur Linux/MacOS.</span><span class="sxs-lookup"><span data-stu-id="482a8-171">The default value is *%LocalAppData%\Microsoft\dotnet* on Windows and */usr/share/dotnet* on Linux/macOS.</span></span> <span data-ttu-id="482a8-172">Les fichiers binaires sont placés directement dans ce répertoire.</span><span class="sxs-lookup"><span data-stu-id="482a8-172">Binaries are placed directly in this directory.</span></span>

- **`-JSonFile|--jsonfile <JSONFILE>`**

  <span data-ttu-id="482a8-173">Spécifie le chemin d’accès à un [global.js](global-json.md) fichier qui sera utilisé pour déterminer la version du kit de développement logiciel (SDK).</span><span class="sxs-lookup"><span data-stu-id="482a8-173">Specifies a path to a [global.json](global-json.md) file that will be used to determine the SDK version.</span></span> <span data-ttu-id="482a8-174">La *global.jssur* le fichier doit avoir une valeur pour `sdk:version` .</span><span class="sxs-lookup"><span data-stu-id="482a8-174">The *global.json* file must have a value for `sdk:version`.</span></span>

- **`-NoCdn|--no-cdn`**

  <span data-ttu-id="482a8-175">Désactive le téléchargement à partir d’[Azure Content Delivery Network (CDN)](/azure/cdn/cdn-overview) et utilise directement le flux non mis en cache.</span><span class="sxs-lookup"><span data-stu-id="482a8-175">Disables downloading from the [Azure Content Delivery Network (CDN)](/azure/cdn/cdn-overview) and uses the uncached feed directly.</span></span>

- **`-NoPath|--no-path`**

  <span data-ttu-id="482a8-176">Si cette option est définie, le dossier d’installation n’est pas exporté dans le chemin de la session actuelle.</span><span class="sxs-lookup"><span data-stu-id="482a8-176">If set, the installation folder isn't exported to the path for the current session.</span></span> <span data-ttu-id="482a8-177">Par défaut, le script modifie le chemin d’accès, ce qui rend le CLI .NET Core disponible immédiatement après l’installation.</span><span class="sxs-lookup"><span data-stu-id="482a8-177">By default, the script modifies the PATH, which makes the .NET Core CLI available immediately after install.</span></span>

- **`-ProxyAddress`**

  <span data-ttu-id="482a8-178">Si cette option est définie, le programme d’installation utilise le proxy pendant la création de demandes web.</span><span class="sxs-lookup"><span data-stu-id="482a8-178">If set, the installer uses the proxy when making web requests.</span></span> <span data-ttu-id="482a8-179">(Valide uniquement pour Windows.)</span><span class="sxs-lookup"><span data-stu-id="482a8-179">(Only valid for Windows.)</span></span>

- **`-ProxyBypassList <LIST_OF_URLS>`**

  <span data-ttu-id="482a8-180">S' `ProxyAddress` il est défini avec, fournit une liste d’URL séparées par des virgules qui contournent le proxy.</span><span class="sxs-lookup"><span data-stu-id="482a8-180">If set with `ProxyAddress`, provides a list of comma-separated urls that will bypass the proxy.</span></span> <span data-ttu-id="482a8-181">(Valide uniquement pour Windows.)</span><span class="sxs-lookup"><span data-stu-id="482a8-181">(Only valid for Windows.)</span></span>

- **`ProxyUseDefaultCredentials`**

  <span data-ttu-id="482a8-182">Si cette option est définie, le programme d’installation utilise les informations d’identification de l’utilisateur actuel lors de l’utilisation de l’adresse proxy.</span><span class="sxs-lookup"><span data-stu-id="482a8-182">If set, the installer uses the credentials of the current user when using proxy address.</span></span> <span data-ttu-id="482a8-183">(Valide uniquement pour Windows.)</span><span class="sxs-lookup"><span data-stu-id="482a8-183">(Only valid for Windows.)</span></span>

- **`-Runtime|--runtime <RUNTIME>`**

  <span data-ttu-id="482a8-184">Installe uniquement le runtime partagé et non l’intégralité du SDK.</span><span class="sxs-lookup"><span data-stu-id="482a8-184">Installs just the shared runtime, not the entire SDK.</span></span> <span data-ttu-id="482a8-185">Les valeurs possibles sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="482a8-185">The possible values are:</span></span>

  - <span data-ttu-id="482a8-186">`dotnet` - le runtime partagé `Microsoft.NETCore.App`.</span><span class="sxs-lookup"><span data-stu-id="482a8-186">`dotnet` - the `Microsoft.NETCore.App` shared runtime.</span></span>
  - <span data-ttu-id="482a8-187">`aspnetcore` - le runtime partagé `Microsoft.AspNetCore.App`.</span><span class="sxs-lookup"><span data-stu-id="482a8-187">`aspnetcore` - the `Microsoft.AspNetCore.App` shared runtime.</span></span>
  - <span data-ttu-id="482a8-188">`windowsdesktop` - le runtime partagé `Microsoft.WindowsDesktop.App`.</span><span class="sxs-lookup"><span data-stu-id="482a8-188">`windowsdesktop` - the `Microsoft.WindowsDesktop.App` shared runtime.</span></span>

- **`--runtime-id <RID>`**

  <span data-ttu-id="482a8-189">Spécifie l' [identificateur du runtime](../rid-catalog.md) pour lequel les outils sont installés.</span><span class="sxs-lookup"><span data-stu-id="482a8-189">Specifies the [runtime identifier](../rid-catalog.md) for which the tools are being installed.</span></span> <span data-ttu-id="482a8-190">Utilisez `linux-x64` pour portable Linux.</span><span class="sxs-lookup"><span data-stu-id="482a8-190">Use `linux-x64` for portable Linux.</span></span> <span data-ttu-id="482a8-191">(Valide uniquement pour Linux/macOS.)</span><span class="sxs-lookup"><span data-stu-id="482a8-191">(Only valid for Linux/macOS.)</span></span>

- **`-SharedRuntime|--shared-runtime`**

  > [!NOTE]
  > <span data-ttu-id="482a8-192">Ce paramètre est obsolète et sera peut-être supprimé dans une future version du script.</span><span class="sxs-lookup"><span data-stu-id="482a8-192">This parameter is obsolete and may be removed in a future version of the script.</span></span> <span data-ttu-id="482a8-193">L'alternative recommandée est l’option `-Runtime|--runtime`.</span><span class="sxs-lookup"><span data-stu-id="482a8-193">The recommended alternative is the `-Runtime|--runtime` option.</span></span>

  <span data-ttu-id="482a8-194">Installe uniquement les bits du runtime partagé et non l’intégralité du SDK.</span><span class="sxs-lookup"><span data-stu-id="482a8-194">Installs just the shared runtime bits, not the entire SDK.</span></span> <span data-ttu-id="482a8-195">Cette option équivaut à spécifier `-Runtime|--runtime dotnet` .</span><span class="sxs-lookup"><span data-stu-id="482a8-195">This option is equivalent to specifying `-Runtime|--runtime dotnet`.</span></span>

- **`-SkipNonVersionedFiles|--skip-non-versioned-files`**

  <span data-ttu-id="482a8-196">Ignore l’installation des fichiers sans version, notamment *dotnet.exe*, s’ils existent déjà.</span><span class="sxs-lookup"><span data-stu-id="482a8-196">Skips installing non-versioned files, such as *dotnet.exe*, if they already exist.</span></span>

- **`-UncachedFeed|--uncached-feed`**

  <span data-ttu-id="482a8-197">Permet de changer l’URL pour le flux non mis en cache utilisé par ce programme d’installation.</span><span class="sxs-lookup"><span data-stu-id="482a8-197">Allows changing the URL for the uncached feed used by this installer.</span></span> <span data-ttu-id="482a8-198">Nous recommandons de ne pas modifier cette valeur.</span><span class="sxs-lookup"><span data-stu-id="482a8-198">We recommended that you don't change this value.</span></span>

- **`-Verbose|--verbose`**

  <span data-ttu-id="482a8-199">Affiche les informations de diagnostic.</span><span class="sxs-lookup"><span data-stu-id="482a8-199">Displays diagnostics information.</span></span>

- **`-Version|--version <VERSION>`**

  <span data-ttu-id="482a8-200">Représente une version spécifique.</span><span class="sxs-lookup"><span data-stu-id="482a8-200">Represents a specific build version.</span></span> <span data-ttu-id="482a8-201">Les valeurs possibles sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="482a8-201">The possible values are:</span></span>

  - <span data-ttu-id="482a8-202">`latest` : dernière version sur le canal (utilisée avec l’option `-Channel`).</span><span class="sxs-lookup"><span data-stu-id="482a8-202">`latest` - Latest build on the channel (used with the `-Channel` option).</span></span>
  - <span data-ttu-id="482a8-203">`coherent` : dernière version cohérente sur le canal ; utilise la dernière combinaison de packages stable (utilisée avec les options `-Channel` de nom de branche).</span><span class="sxs-lookup"><span data-stu-id="482a8-203">`coherent` - Latest coherent build on the channel; uses the latest stable package combination (used with Branch name `-Channel` options).</span></span>
  - <span data-ttu-id="482a8-204">Version en trois parties au format X.Y.Z représentant une version spécifique ; remplace l’option `-Channel`.</span><span class="sxs-lookup"><span data-stu-id="482a8-204">Three-part version in X.Y.Z format representing a specific build version; supersedes the `-Channel` option.</span></span> <span data-ttu-id="482a8-205">Par exemple : `2.0.0-preview2-006120`.</span><span class="sxs-lookup"><span data-stu-id="482a8-205">For example: `2.0.0-preview2-006120`.</span></span>

  <span data-ttu-id="482a8-206">Si aucune valeur n’est spécifiée, `-Version` est définie par défaut sur `latest`.</span><span class="sxs-lookup"><span data-stu-id="482a8-206">If not specified, `-Version` defaults to `latest`.</span></span>

## <a name="examples"></a><span data-ttu-id="482a8-207">Exemples</span><span class="sxs-lookup"><span data-stu-id="482a8-207">Examples</span></span>

- <span data-ttu-id="482a8-208">Installez la dernière version LTS (Long Term Support) à l’emplacement par défaut :</span><span class="sxs-lookup"><span data-stu-id="482a8-208">Install the latest long-term supported (LTS) version to the default location:</span></span>

  <span data-ttu-id="482a8-209">Windows :</span><span class="sxs-lookup"><span data-stu-id="482a8-209">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Channel LTS
  ```

  <span data-ttu-id="482a8-210">Mac OS/Linux :</span><span class="sxs-lookup"><span data-stu-id="482a8-210">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --channel LTS
  ```

- <span data-ttu-id="482a8-211">Installez la version la plus récente à partir du canal 3,1 à l’emplacement spécifié :</span><span class="sxs-lookup"><span data-stu-id="482a8-211">Install the latest version from 3.1 channel to the specified location:</span></span>

  <span data-ttu-id="482a8-212">Windows :</span><span class="sxs-lookup"><span data-stu-id="482a8-212">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Channel 3.1 -InstallDir C:\cli
  ```

  <span data-ttu-id="482a8-213">Mac OS/Linux :</span><span class="sxs-lookup"><span data-stu-id="482a8-213">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --channel 3.1 --install-dir ~/cli
  ```

- <span data-ttu-id="482a8-214">Installez la version 3.0.0 du runtime partagé :</span><span class="sxs-lookup"><span data-stu-id="482a8-214">Install the 3.0.0 version of the shared runtime:</span></span>

  <span data-ttu-id="482a8-215">Windows :</span><span class="sxs-lookup"><span data-stu-id="482a8-215">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Runtime dotnet -Version 3.0.0
  ```

  <span data-ttu-id="482a8-216">Mac OS/Linux :</span><span class="sxs-lookup"><span data-stu-id="482a8-216">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --runtime dotnet --version 3.0.0
  ```

- <span data-ttu-id="482a8-217">Obtenir le script et installer la version 2.1.2 derrière un proxy d’entreprise (Windows uniquement) :</span><span class="sxs-lookup"><span data-stu-id="482a8-217">Obtain script and install the 2.1.2 version behind a corporate proxy (Windows only):</span></span>

  ```powershell
  Invoke-WebRequest 'https://dot.net/v1/dotnet-install.ps1' -Proxy $env:HTTP_PROXY -ProxyUseDefaultCredentials -OutFile 'dotnet-install.ps1';
  ./dotnet-install.ps1 -InstallDir '~/.dotnet' -Version '2.1.2' -ProxyAddress $env:HTTP_PROXY -ProxyUseDefaultCredentials;
  ```

- <span data-ttu-id="482a8-218">Obtenir le script et installer les exemples unilignes de l’interface CLI .NET Core :</span><span class="sxs-lookup"><span data-stu-id="482a8-218">Obtain script and install .NET Core CLI one-liner examples:</span></span>

  <span data-ttu-id="482a8-219">Windows :</span><span class="sxs-lookup"><span data-stu-id="482a8-219">Windows:</span></span>

  ```powershell
  # Run a separate PowerShell process because the script calls exit, so it will end the current PowerShell session.
  &powershell -NoProfile -ExecutionPolicy unrestricted -Command "[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12; &([scriptblock]::Create((Invoke-WebRequest -UseBasicParsing 'https://dot.net/v1/dotnet-install.ps1'))) <additional install-script args>"
  ```

  <span data-ttu-id="482a8-220">Mac OS/Linux :</span><span class="sxs-lookup"><span data-stu-id="482a8-220">macOS/Linux:</span></span>

  ```bash
  curl -sSL https://dot.net/v1/dotnet-install.sh | bash /dev/stdin <additional install-script args>
  ```

## <a name="see-also"></a><span data-ttu-id="482a8-221">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="482a8-221">See also</span></span>

- [<span data-ttu-id="482a8-222">Versions de .NET Core</span><span class="sxs-lookup"><span data-stu-id="482a8-222">.NET Core releases</span></span>](https://github.com/dotnet/core/releases)
- [<span data-ttu-id="482a8-223">Archive de téléchargement de .NET Core Runtime et du Kit SDK</span><span class="sxs-lookup"><span data-stu-id="482a8-223">.NET Core Runtime and SDK download archive</span></span>](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md)
