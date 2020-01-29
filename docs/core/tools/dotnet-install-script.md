---
title: Scripts dotnet-install
description: En savoir plus sur les scripts dotnet-install pour installer les kit SDK .NET Core et le runtime partagé.
ms.date: 01/23/2020
ms.openlocfilehash: 169991ac4cd24ccab90634ff265c3ae5b603f8e9
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734205"
---
# <a name="dotnet-install-scripts-reference"></a><span data-ttu-id="8ab04-103">Documentation sur les scripts dotnet-install</span><span class="sxs-lookup"><span data-stu-id="8ab04-103">dotnet-install scripts reference</span></span>

## <a name="name"></a><span data-ttu-id="8ab04-104">Name</span><span class="sxs-lookup"><span data-stu-id="8ab04-104">Name</span></span>

<span data-ttu-id="8ab04-105">`dotnet-install.ps1` | `dotnet-install.sh`-script utilisé pour installer le kit SDK .NET Core et le runtime partagé.</span><span class="sxs-lookup"><span data-stu-id="8ab04-105">`dotnet-install.ps1` | `dotnet-install.sh` - Script used to install the .NET Core SDK and the shared runtime.</span></span>

## <a name="synopsis"></a><span data-ttu-id="8ab04-106">Résumé</span><span class="sxs-lookup"><span data-stu-id="8ab04-106">Synopsis</span></span>

<span data-ttu-id="8ab04-107">Windows :</span><span class="sxs-lookup"><span data-stu-id="8ab04-107">Windows:</span></span>

```powershell
dotnet-install.ps1 [-Channel] [-Version] [-JSonFile] [-InstallDir] [-Architecture]
    [-Runtime] [-DryRun] [-NoPath] [-Verbose] [-AzureFeed] [-UncachedFeed] [-NoCdn] [-FeedCredential]
    [-ProxyAddress] [-ProxyUseDefaultCredentials] [-SkipNonVersionedFiles] [-Help]
```

<span data-ttu-id="8ab04-108">Linux/macOs :</span><span class="sxs-lookup"><span data-stu-id="8ab04-108">Linux/macOs:</span></span>

```bash
dotnet-install.sh [--channel] [--version] [--jsonfile] [--install-dir] [--architecture]
    [--runtime] [--dry-run] [--no-path] [--verbose] [--azure-feed] [--uncached-feed] [--no-cdn] [--feed-credential]
    [--runtime-id] [--skip-non-versioned-files] [--help]
```

## <a name="description"></a><span data-ttu-id="8ab04-109">Description</span><span class="sxs-lookup"><span data-stu-id="8ab04-109">Description</span></span>

<span data-ttu-id="8ab04-110">Les scripts `dotnet-install` sont utilisés pour effectuer une installation non administrateur du SDK .NET Core, qui inclut les outils .NET Core CLI et le runtime partagé.</span><span class="sxs-lookup"><span data-stu-id="8ab04-110">The `dotnet-install` scripts are used to perform a non-admin installation of the .NET Core SDK, which includes the .NET Core CLI tools and the shared runtime.</span></span>

<span data-ttu-id="8ab04-111">Nous vous recommandons d’utiliser la version stable des scripts :</span><span class="sxs-lookup"><span data-stu-id="8ab04-111">We recommend that you use the stable version of the scripts:</span></span>

- <span data-ttu-id="8ab04-112">Bash (Linux/macOS) : <https://dot.net/v1/dotnet-install.sh></span><span class="sxs-lookup"><span data-stu-id="8ab04-112">Bash (Linux/macOS): <https://dot.net/v1/dotnet-install.sh></span></span>
- <span data-ttu-id="8ab04-113">PowerShell (Windows) : <https://dot.net/v1/dotnet-install.ps1></span><span class="sxs-lookup"><span data-stu-id="8ab04-113">PowerShell (Windows): <https://dot.net/v1/dotnet-install.ps1></span></span>

<span data-ttu-id="8ab04-114">La principale utilité de ces scripts réside dans les scénarios d’automatisation et les installations non administrateur.</span><span class="sxs-lookup"><span data-stu-id="8ab04-114">The main usefulness of these scripts is in automation scenarios and non-admin installations.</span></span> <span data-ttu-id="8ab04-115">Il existe deux scripts : un script PowerShell qui fonctionne sous Windows, et un autre script d’interpréteur de commandes qui fonctionne sous Linux/macOS.</span><span class="sxs-lookup"><span data-stu-id="8ab04-115">There are two scripts: one is a PowerShell script that works on Windows, and the other is a bash script that works on Linux/macOS.</span></span> <span data-ttu-id="8ab04-116">Les deux scripts ont le même comportement.</span><span class="sxs-lookup"><span data-stu-id="8ab04-116">Both scripts have the same behavior.</span></span> <span data-ttu-id="8ab04-117">Comme le script bash lit également les commutateurs PowerShell, vous pouvez utiliser ces derniers avec le script sur les systèmes Linux/macOS.</span><span class="sxs-lookup"><span data-stu-id="8ab04-117">The bash script also reads PowerShell switches, so you can use PowerShell switches with the script on Linux/macOS systems.</span></span>

<span data-ttu-id="8ab04-118">Les scripts d’installation téléchargent le fichier ZIP/tarball à partir des cibles de builds CLI, puis poursuivent l’installation dans l’emplacement par défaut ou dans un emplacement spécifié par `-InstallDir|--install-dir`.</span><span class="sxs-lookup"><span data-stu-id="8ab04-118">The installation scripts download the ZIP/tarball file from the CLI build drops and proceed to install it in either the default location or in a location specified by `-InstallDir|--install-dir`.</span></span> <span data-ttu-id="8ab04-119">Par défaut, les scripts d’installation téléchargent et installent le Kit de développement logiciel (SDK).</span><span class="sxs-lookup"><span data-stu-id="8ab04-119">By default, the installation scripts download the SDK and install it.</span></span> <span data-ttu-id="8ab04-120">Si vous souhaitez obtenir uniquement le runtime partagé, spécifiez l’argument `-Runtime|--runtime`.</span><span class="sxs-lookup"><span data-stu-id="8ab04-120">If you wish to only obtain the shared runtime, specify the `-Runtime|--runtime` argument.</span></span>

<span data-ttu-id="8ab04-121">Par défaut, le script ajoute l’emplacement d’installation $PATH pour la session active.</span><span class="sxs-lookup"><span data-stu-id="8ab04-121">By default, the script adds the install location to the $PATH for the current session.</span></span> <span data-ttu-id="8ab04-122">Remplacez ce comportement par défaut en spécifiant l’argument `-NoPath|--no-path`.</span><span class="sxs-lookup"><span data-stu-id="8ab04-122">Override this default behavior by specifying the `-NoPath|--no-path` argument.</span></span>

<span data-ttu-id="8ab04-123">Avant d’exécuter le script, installez les [dépendances](../install/dependencies.md) nécessaires.</span><span class="sxs-lookup"><span data-stu-id="8ab04-123">Before running the script, install the required [dependencies](../install/dependencies.md).</span></span>

<span data-ttu-id="8ab04-124">Vous pouvez installer une version spécifique à l’aide de l’argument `-Version|--version`.</span><span class="sxs-lookup"><span data-stu-id="8ab04-124">You can install a specific version using the `-Version|--version` argument.</span></span> <span data-ttu-id="8ab04-125">La version doit être spécifiée en trois parties (par exemple, `2.1.0`).</span><span class="sxs-lookup"><span data-stu-id="8ab04-125">The version must be specified as a three-part version (for example, `2.1.0`).</span></span> <span data-ttu-id="8ab04-126">Si aucune valeur n’est spécifiée, la version `latest` est utilisée.</span><span class="sxs-lookup"><span data-stu-id="8ab04-126">If not provided, it uses the `latest` version.</span></span>

## <a name="options"></a><span data-ttu-id="8ab04-127">Options</span><span class="sxs-lookup"><span data-stu-id="8ab04-127">Options</span></span>

- **`-Channel|--channel <CHANNEL>`**

  <span data-ttu-id="8ab04-128">Spécifie le canal source pour l’installation.</span><span class="sxs-lookup"><span data-stu-id="8ab04-128">Specifies the source channel for the installation.</span></span> <span data-ttu-id="8ab04-129">Les valeurs possibles sont :</span><span class="sxs-lookup"><span data-stu-id="8ab04-129">The possible values are:</span></span>

  - <span data-ttu-id="8ab04-130">`Current` - Version la plus récente.</span><span class="sxs-lookup"><span data-stu-id="8ab04-130">`Current` - Most current release.</span></span>
  - <span data-ttu-id="8ab04-131">`LTS` - Canal de prise en charge à long terme (dernière version prise en charge).</span><span class="sxs-lookup"><span data-stu-id="8ab04-131">`LTS` - Long-Term Support channel (most current supported release).</span></span>
  - <span data-ttu-id="8ab04-132">Version en deux parties au format X.Y représentant une version spécifique (par exemple, `2.1` ou `3.0`).</span><span class="sxs-lookup"><span data-stu-id="8ab04-132">Two-part version in X.Y format representing a specific release (for example, `2.1` or `3.0`).</span></span>
  - <span data-ttu-id="8ab04-133">Nom de la branche : par exemple, `release/3.1.1xx` ou `master` (pour les versions nocturnes).</span><span class="sxs-lookup"><span data-stu-id="8ab04-133">Branch name: for example, `release/3.1.1xx` or `master` (for nightly releases).</span></span> <span data-ttu-id="8ab04-134">Utilisez cette option pour installer une version à partir d’un canal de préversion.</span><span class="sxs-lookup"><span data-stu-id="8ab04-134">Use this option to install a version from a preview channel.</span></span> <span data-ttu-id="8ab04-135">Utilisez le nom du canal tel qu’il figure dans [programmes d’installation et binaires](https://github.com/dotnet/core-sdk#installers-and-binaries).</span><span class="sxs-lookup"><span data-stu-id="8ab04-135">Use the name of the channel as listed in [Installers and Binaries](https://github.com/dotnet/core-sdk#installers-and-binaries).</span></span>

  <span data-ttu-id="8ab04-136">La valeur par défaut est `LTS`.</span><span class="sxs-lookup"><span data-stu-id="8ab04-136">The default value is `LTS`.</span></span> <span data-ttu-id="8ab04-137">Pour plus d’informations sur les canaux de prise en charge de .NET, consultez la page [Stratégie de prise en charge .NET](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="8ab04-137">For more information on .NET support channels, see the [.NET Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) page.</span></span>

- **`-Version|--version <VERSION>`**

  <span data-ttu-id="8ab04-138">Représente une version spécifique.</span><span class="sxs-lookup"><span data-stu-id="8ab04-138">Represents a specific build version.</span></span> <span data-ttu-id="8ab04-139">Les valeurs possibles sont :</span><span class="sxs-lookup"><span data-stu-id="8ab04-139">The possible values are:</span></span>

  - <span data-ttu-id="8ab04-140">`latest` : dernière version sur le canal (utilisée avec l’option `-Channel`).</span><span class="sxs-lookup"><span data-stu-id="8ab04-140">`latest` - Latest build on the channel (used with the `-Channel` option).</span></span>
  - <span data-ttu-id="8ab04-141">`coherent` : dernière version cohérente sur le canal ; utilise la dernière combinaison de packages stable (utilisée avec les options `-Channel` de nom de branche).</span><span class="sxs-lookup"><span data-stu-id="8ab04-141">`coherent` - Latest coherent build on the channel; uses the latest stable package combination (used with Branch name `-Channel` options).</span></span>
  - <span data-ttu-id="8ab04-142">Version en trois parties au format X.Y.Z représentant une version spécifique ; remplace l’option `-Channel`.</span><span class="sxs-lookup"><span data-stu-id="8ab04-142">Three-part version in X.Y.Z format representing a specific build version; supersedes the `-Channel` option.</span></span> <span data-ttu-id="8ab04-143">Par exemple : `2.0.0-preview2-006120`.</span><span class="sxs-lookup"><span data-stu-id="8ab04-143">For example: `2.0.0-preview2-006120`.</span></span>

  <span data-ttu-id="8ab04-144">Si aucune valeur n’est spécifiée, `-Version` est définie par défaut sur `latest`.</span><span class="sxs-lookup"><span data-stu-id="8ab04-144">If not specified, `-Version` defaults to `latest`.</span></span>

- **`-JSonFile|--jsonfile <JSONFILE>`**

  <span data-ttu-id="8ab04-145">Spécifie le chemin d’accès à un fichier [global. JSON](global-json.md) qui sera utilisé pour déterminer la version du kit de développement logiciel (SDK).</span><span class="sxs-lookup"><span data-stu-id="8ab04-145">Specifies a path to a [global.json](global-json.md) file that will be used to determine the SDK version.</span></span> <span data-ttu-id="8ab04-146">Le fichier *global. JSON* doit avoir une valeur pour `sdk:version`.</span><span class="sxs-lookup"><span data-stu-id="8ab04-146">The *global.json* file must have a value for `sdk:version`.</span></span>

- **`-InstallDir|--install-dir <DIRECTORY>`**

  <span data-ttu-id="8ab04-147">Spécifie le chemin d’accès de l’installation.</span><span class="sxs-lookup"><span data-stu-id="8ab04-147">Specifies the installation path.</span></span> <span data-ttu-id="8ab04-148">S’il n’existe pas déjà, le répertoire est créé.</span><span class="sxs-lookup"><span data-stu-id="8ab04-148">The directory is created if it doesn't exist.</span></span> <span data-ttu-id="8ab04-149">La valeur par défaut est *%LocalAppData%\Microsoft\dotnet*.</span><span class="sxs-lookup"><span data-stu-id="8ab04-149">The default value is *%LocalAppData%\Microsoft\dotnet*.</span></span> <span data-ttu-id="8ab04-150">Les fichiers binaires sont placés directement dans ce répertoire.</span><span class="sxs-lookup"><span data-stu-id="8ab04-150">Binaries are placed directly in this directory.</span></span>

- **`-Architecture|--architecture <ARCHITECTURE>`**

  <span data-ttu-id="8ab04-151">Architecture des fichiers binaires .NET Core à installer.</span><span class="sxs-lookup"><span data-stu-id="8ab04-151">Architecture of the .NET Core binaries to install.</span></span> <span data-ttu-id="8ab04-152">Les valeurs possibles sont `<auto>`, `amd64`, `x64`, `x86`, `arm64` et `arm`.</span><span class="sxs-lookup"><span data-stu-id="8ab04-152">Possible values are `<auto>`, `amd64`, `x64`, `x86`, `arm64`, and `arm`.</span></span> <span data-ttu-id="8ab04-153">La valeur par défaut est `<auto>`, qui représente l’architecture de système d’exploitation en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="8ab04-153">The default value is `<auto>`, which represents the currently running OS architecture.</span></span>

- **`-SharedRuntime|--shared-runtime`**

  > [!NOTE]
  > <span data-ttu-id="8ab04-154">Ce paramètre est obsolète et sera peut-être supprimé dans une future version du script.</span><span class="sxs-lookup"><span data-stu-id="8ab04-154">This parameter is obsolete and may be removed in a future version of the script.</span></span> <span data-ttu-id="8ab04-155">L'alternative recommandée est l’option `-Runtime|--runtime`.</span><span class="sxs-lookup"><span data-stu-id="8ab04-155">The recommended alternative is the `-Runtime|--runtime` option.</span></span>

  <span data-ttu-id="8ab04-156">Installe uniquement les bits du runtime partagé et non l’intégralité du SDK.</span><span class="sxs-lookup"><span data-stu-id="8ab04-156">Installs just the shared runtime bits, not the entire SDK.</span></span> <span data-ttu-id="8ab04-157">Cette option équivaut à spécifier `-Runtime|--runtime dotnet`.</span><span class="sxs-lookup"><span data-stu-id="8ab04-157">This option is equivalent to specifying `-Runtime|--runtime dotnet`.</span></span>

- **`-Runtime|--runtime <RUNTIME>`**

  <span data-ttu-id="8ab04-158">Installe uniquement le runtime partagé et non l’intégralité du SDK.</span><span class="sxs-lookup"><span data-stu-id="8ab04-158">Installs just the shared runtime, not the entire SDK.</span></span> <span data-ttu-id="8ab04-159">Les valeurs possibles sont :</span><span class="sxs-lookup"><span data-stu-id="8ab04-159">The possible values are:</span></span>

  - <span data-ttu-id="8ab04-160">`dotnet` - le runtime partagé `Microsoft.NETCore.App`.</span><span class="sxs-lookup"><span data-stu-id="8ab04-160">`dotnet` - the `Microsoft.NETCore.App` shared runtime.</span></span>
  - <span data-ttu-id="8ab04-161">`aspnetcore` - le runtime partagé `Microsoft.AspNetCore.App`.</span><span class="sxs-lookup"><span data-stu-id="8ab04-161">`aspnetcore` - the `Microsoft.AspNetCore.App` shared runtime.</span></span>
  - <span data-ttu-id="8ab04-162">`windowsdesktop` - le runtime partagé `Microsoft.WindowsDesktop.App`.</span><span class="sxs-lookup"><span data-stu-id="8ab04-162">`windowsdesktop` - the `Microsoft.WindowsDesktop.App` shared runtime.</span></span>

- **`-DryRun|--dry-run`**

  <span data-ttu-id="8ab04-163">Si cette option est définie, le script n’effectue pas l’installation.</span><span class="sxs-lookup"><span data-stu-id="8ab04-163">If set, the script won't perform the installation.</span></span> <span data-ttu-id="8ab04-164">Affiche à la place la ligne de commande à utiliser pour installer la version de l’interface CLI .NET Core actuellement demandée.</span><span class="sxs-lookup"><span data-stu-id="8ab04-164">Instead, it displays what command line to use to consistently install the currently requested version of the .NET Core CLI.</span></span> <span data-ttu-id="8ab04-165">Par exemple, si vous spécifiez la version `latest`, elle affiche un lien avec la version spécifique, pour que cette commande puisse être utilisée de façon déterministe dans un script de génération.</span><span class="sxs-lookup"><span data-stu-id="8ab04-165">For example, if you specify version `latest`, it displays a link with the specific version so that this command can be used deterministically in a build script.</span></span> <span data-ttu-id="8ab04-166">Elle affiche également l’emplacement du fichier binaire si vous préférez l’installer ou le télécharger vous-même.</span><span class="sxs-lookup"><span data-stu-id="8ab04-166">It also displays the binary's location if you prefer to install or download it yourself.</span></span>

- **`-NoPath|--no-path`**

  <span data-ttu-id="8ab04-167">Si cette option est définie, le dossier d’installation n’est pas exporté dans le chemin de la session actuelle.</span><span class="sxs-lookup"><span data-stu-id="8ab04-167">If set, the installation folder isn't exported to the path for the current session.</span></span> <span data-ttu-id="8ab04-168">Par défaut, le script modifie le chemin, ce qui rend les outils CLI disponibles immédiatement après l’installation.</span><span class="sxs-lookup"><span data-stu-id="8ab04-168">By default, the script modifies the PATH, which makes the CLI tools available immediately after install.</span></span>

- **`-Verbose|--verbose`**

  <span data-ttu-id="8ab04-169">Affiche les informations de diagnostic.</span><span class="sxs-lookup"><span data-stu-id="8ab04-169">Displays diagnostics information.</span></span>

- **`-AzureFeed|--azure-feed`**

  <span data-ttu-id="8ab04-170">Spécifie l’URL du flux Azure à utiliser par ce programme d’installation.</span><span class="sxs-lookup"><span data-stu-id="8ab04-170">Specifies the URL for the Azure feed to the installer.</span></span> <span data-ttu-id="8ab04-171">Nous recommandons de ne pas modifier cette valeur.</span><span class="sxs-lookup"><span data-stu-id="8ab04-171">We recommended that you don't change this value.</span></span> <span data-ttu-id="8ab04-172">La valeur par défaut est `https://dotnetcli.azureedge.net/dotnet`.</span><span class="sxs-lookup"><span data-stu-id="8ab04-172">The default value is `https://dotnetcli.azureedge.net/dotnet`.</span></span>

- **`-UncachedFeed|--uncached-feed`**

  <span data-ttu-id="8ab04-173">Permet de changer l’URL pour le flux non mis en cache utilisé par ce programme d’installation.</span><span class="sxs-lookup"><span data-stu-id="8ab04-173">Allows changing the URL for the uncached feed used by this installer.</span></span> <span data-ttu-id="8ab04-174">Nous recommandons de ne pas modifier cette valeur.</span><span class="sxs-lookup"><span data-stu-id="8ab04-174">We recommended that you don't change this value.</span></span>

- **`-NoCdn|--no-cdn`**

  <span data-ttu-id="8ab04-175">Désactive le téléchargement à partir d’[Azure Content Delivery Network (CDN)](https://docs.microsoft.com/azure/cdn/cdn-overview) et utilise directement le flux non mis en cache.</span><span class="sxs-lookup"><span data-stu-id="8ab04-175">Disables downloading from the [Azure Content Delivery Network (CDN)](https://docs.microsoft.com/azure/cdn/cdn-overview) and uses the uncached feed directly.</span></span>

- **`-FeedCredential|--feed-credential`**

  <span data-ttu-id="8ab04-176">Valeur utilisée comme chaîne de requête à ajouter au flux Azure.</span><span class="sxs-lookup"><span data-stu-id="8ab04-176">Used as a query string to append to the Azure feed.</span></span> <span data-ttu-id="8ab04-177">Elle permet de changer l’URL afin d’utiliser des comptes de stockage d’objets blob non publics.</span><span class="sxs-lookup"><span data-stu-id="8ab04-177">It allows changing the URL to use non-public blob storage accounts.</span></span>

- **`--runtime-id`**

  <span data-ttu-id="8ab04-178">Spécifie l' [identificateur du runtime](../rid-catalog.md) pour lequel les outils sont installés.</span><span class="sxs-lookup"><span data-stu-id="8ab04-178">Specifies the [runtime identifier](../rid-catalog.md) for which the tools are being installed.</span></span> <span data-ttu-id="8ab04-179">Utilisez `linux-x64` pour portable Linux.</span><span class="sxs-lookup"><span data-stu-id="8ab04-179">Use `linux-x64` for portable Linux.</span></span> <span data-ttu-id="8ab04-180">(Valide uniquement pour Linux/macOS)</span><span class="sxs-lookup"><span data-stu-id="8ab04-180">(Only valid for Linux/macOS)</span></span>

- **`-ProxyAddress`**

  <span data-ttu-id="8ab04-181">Si cette option est définie, le programme d’installation utilise le proxy pendant la création de demandes web.</span><span class="sxs-lookup"><span data-stu-id="8ab04-181">If set, the installer uses the proxy when making web requests.</span></span> <span data-ttu-id="8ab04-182">(valide uniquement pour Windows)</span><span class="sxs-lookup"><span data-stu-id="8ab04-182">(Only valid for Windows)</span></span>

- **`ProxyUseDefaultCredentials`**

  <span data-ttu-id="8ab04-183">Si cette option est définie, le programme d’installation utilise les informations d’identification de l’utilisateur actuel lors de l’utilisation de l’adresse proxy.</span><span class="sxs-lookup"><span data-stu-id="8ab04-183">If set, the installer uses the credentials of the current user when using proxy address.</span></span> <span data-ttu-id="8ab04-184">(valide uniquement pour Windows)</span><span class="sxs-lookup"><span data-stu-id="8ab04-184">(Only valid for Windows)</span></span>

- **`-SkipNonVersionedFiles|--skip-non-versioned-files`**

  <span data-ttu-id="8ab04-185">Ignore l’installation des fichiers sans version, notamment *dotnet.exe*, s’ils existent déjà.</span><span class="sxs-lookup"><span data-stu-id="8ab04-185">Skips installing non-versioned files, such as *dotnet.exe*, if they already exist.</span></span>

- **`-Help|--help`**

  <span data-ttu-id="8ab04-186">Affiche l’aide pour le script.</span><span class="sxs-lookup"><span data-stu-id="8ab04-186">Prints out help for the script.</span></span>

## <a name="examples"></a><span data-ttu-id="8ab04-187">Exemples</span><span class="sxs-lookup"><span data-stu-id="8ab04-187">Examples</span></span>

- <span data-ttu-id="8ab04-188">Installez la dernière version LTS (Long Term Support) à l’emplacement par défaut :</span><span class="sxs-lookup"><span data-stu-id="8ab04-188">Install the latest long-term supported (LTS) version to the default location:</span></span>

  <span data-ttu-id="8ab04-189">Windows :</span><span class="sxs-lookup"><span data-stu-id="8ab04-189">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Channel LTS
  ```

  <span data-ttu-id="8ab04-190">Mac OS/Linux :</span><span class="sxs-lookup"><span data-stu-id="8ab04-190">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --channel LTS
  ```

- <span data-ttu-id="8ab04-191">Installez la version la plus récente à partir du canal 3,1 à l’emplacement spécifié :</span><span class="sxs-lookup"><span data-stu-id="8ab04-191">Install the latest version from 3.1 channel to the specified location:</span></span>

  <span data-ttu-id="8ab04-192">Windows :</span><span class="sxs-lookup"><span data-stu-id="8ab04-192">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Channel 3.1 -InstallDir C:\cli
  ```

  <span data-ttu-id="8ab04-193">Mac OS/Linux :</span><span class="sxs-lookup"><span data-stu-id="8ab04-193">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --channel 3.1 --install-dir ~/cli
  ```

- <span data-ttu-id="8ab04-194">Installez la version 3.0.0 du runtime partagé :</span><span class="sxs-lookup"><span data-stu-id="8ab04-194">Install the 3.0.0 version of the shared runtime:</span></span>

  <span data-ttu-id="8ab04-195">Windows :</span><span class="sxs-lookup"><span data-stu-id="8ab04-195">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Runtime dotnet -Version 3.0.0
  ```

  <span data-ttu-id="8ab04-196">Mac OS/Linux :</span><span class="sxs-lookup"><span data-stu-id="8ab04-196">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --runtime dotnet --version 3.0.0
  ```

- <span data-ttu-id="8ab04-197">Obtenir le script et installer la version 2.1.2 derrière un proxy d’entreprise (Windows uniquement) :</span><span class="sxs-lookup"><span data-stu-id="8ab04-197">Obtain script and install the 2.1.2 version behind a corporate proxy (Windows only):</span></span>

  ```powershell
  Invoke-WebRequest 'https://dot.net/v1/dotnet-install.ps1' -Proxy $env:HTTP_PROXY -ProxyUseDefaultCredentials -OutFile 'dotnet-install.ps1';
  ./dotnet-install.ps1 -InstallDir '~/.dotnet' -Version '2.1.2' -ProxyAddress $env:HTTP_PROXY -ProxyUseDefaultCredentials;
  ```

- <span data-ttu-id="8ab04-198">Obtenir le script et installer les exemples unilignes de l’interface CLI .NET Core :</span><span class="sxs-lookup"><span data-stu-id="8ab04-198">Obtain script and install .NET Core CLI one-liner examples:</span></span>

  <span data-ttu-id="8ab04-199">Windows :</span><span class="sxs-lookup"><span data-stu-id="8ab04-199">Windows:</span></span>

  ```powershell
  # Run a separate PowerShell process because the script calls exit, so it will end the current PowerShell session.
  &powershell -NoProfile -ExecutionPolicy unrestricted -Command "[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12; &([scriptblock]::Create((Invoke-WebRequest -UseBasicParsing 'https://dot.net/v1/dotnet-install.ps1'))) <additional install-script args>"
  ```

  <span data-ttu-id="8ab04-200">Mac OS/Linux :</span><span class="sxs-lookup"><span data-stu-id="8ab04-200">macOS/Linux:</span></span>

  ```bash
  curl -ssl https://dot.net/v1/dotnet-install.sh | bash /dev/stdin <additional install-script args>
  ```

## <a name="see-also"></a><span data-ttu-id="8ab04-201">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8ab04-201">See also</span></span>

- [<span data-ttu-id="8ab04-202">Versions de .NET Core</span><span class="sxs-lookup"><span data-stu-id="8ab04-202">.NET Core releases</span></span>](https://github.com/dotnet/core/releases)
- [<span data-ttu-id="8ab04-203">Archive de téléchargement de .NET Core Runtime et du Kit SDK</span><span class="sxs-lookup"><span data-stu-id="8ab04-203">.NET Core Runtime and SDK download archive</span></span>](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md)
