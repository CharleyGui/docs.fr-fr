---
title: Scripts dotnet-install
description: Découvrez les scripts dotnet-install pour installer les outils CLI .NET Core et le runtime partagé.
ms.date: 01/16/2019
ms.openlocfilehash: f72e12fc415824a9c69eba6f52e3c01717cf654c
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740532"
---
# <a name="dotnet-install-scripts-reference"></a><span data-ttu-id="01cff-103">Documentation sur les scripts dotnet-install</span><span class="sxs-lookup"><span data-stu-id="01cff-103">dotnet-install scripts reference</span></span>

## <a name="name"></a><span data-ttu-id="01cff-104">Name</span><span class="sxs-lookup"><span data-stu-id="01cff-104">Name</span></span>

<span data-ttu-id="01cff-105">`dotnet-install.ps1` | `dotnet-install.sh` : script utilisé pour installer les outils .NET Core CLI et le runtime partagé.</span><span class="sxs-lookup"><span data-stu-id="01cff-105">`dotnet-install.ps1` | `dotnet-install.sh` - Script used to install the .NET Core CLI tools and the shared runtime.</span></span>

## <a name="synopsis"></a><span data-ttu-id="01cff-106">Résumé</span><span class="sxs-lookup"><span data-stu-id="01cff-106">Synopsis</span></span>

<span data-ttu-id="01cff-107">Windows :</span><span class="sxs-lookup"><span data-stu-id="01cff-107">Windows:</span></span>

`dotnet-install.ps1 [-Channel] [-Version] [-InstallDir] [-Architecture] [-SharedRuntime] [-Runtime] [-DryRun] [-NoPath] [-Verbose] [-AzureFeed] [-UncachedFeed] [-NoCdn] [-FeedCredential] [-ProxyAddress] [-ProxyUseDefaultCredentials] [-SkipNonVersionedFiles] [-Help]`

<span data-ttu-id="01cff-108">Mac OS/Linux :</span><span class="sxs-lookup"><span data-stu-id="01cff-108">macOS/Linux:</span></span>

`dotnet-install.sh [--channel] [--version] [--install-dir] [--architecture] [--runtime] [--dry-run] [--no-path] [--verbose] [--azure-feed] [--uncached-feed] [--no-cdn] [--feed-credential] [--runtime-id] [--skip-non-versioned-files] [--help]`

## <a name="description"></a><span data-ttu-id="01cff-109">Description</span><span class="sxs-lookup"><span data-stu-id="01cff-109">Description</span></span>

<span data-ttu-id="01cff-110">Les scripts `dotnet-install` sont utilisés pour effectuer une installation non administrateur du SDK .NET Core, qui inclut les outils .NET Core CLI et le runtime partagé.</span><span class="sxs-lookup"><span data-stu-id="01cff-110">The `dotnet-install` scripts are used to perform a non-admin installation of the .NET Core SDK, which includes the .NET Core CLI tools and the shared runtime.</span></span>

<span data-ttu-id="01cff-111">Nous vous recommandons d’utiliser la version stable hébergée sur le [site web principal de .NET Core](https://dot.net).</span><span class="sxs-lookup"><span data-stu-id="01cff-111">We recommend that you use the stable version that is hosted on [.NET Core main website](https://dot.net).</span></span> <span data-ttu-id="01cff-112">Les chemins d’accès directs aux scripts sont :</span><span class="sxs-lookup"><span data-stu-id="01cff-112">The direct paths to the scripts are:</span></span>

- <span data-ttu-id="01cff-113"><https://dot.net/v1/dotnet-install.sh> (bash, UNIX)</span><span class="sxs-lookup"><span data-stu-id="01cff-113"><https://dot.net/v1/dotnet-install.sh> (bash, UNIX)</span></span>
- <span data-ttu-id="01cff-114"><https://dot.net/v1/dotnet-install.ps1> (Powershell, Windows)</span><span class="sxs-lookup"><span data-stu-id="01cff-114"><https://dot.net/v1/dotnet-install.ps1> (Powershell, Windows)</span></span>

<span data-ttu-id="01cff-115">La principale utilité de ces scripts réside dans les scénarios d’automatisation et les installations non administrateur.</span><span class="sxs-lookup"><span data-stu-id="01cff-115">The main usefulness of these scripts is in automation scenarios and non-admin installations.</span></span> <span data-ttu-id="01cff-116">Il existe deux scripts : un script PowerShell qui fonctionne sous Windows, et un autre script d’interpréteur de commandes qui fonctionne sous Linux/macOS.</span><span class="sxs-lookup"><span data-stu-id="01cff-116">There are two scripts: one is a PowerShell script that works on Windows, and the other is a bash script that works on Linux/macOS.</span></span> <span data-ttu-id="01cff-117">Les deux scripts ont le même comportement.</span><span class="sxs-lookup"><span data-stu-id="01cff-117">Both scripts have the same behavior.</span></span> <span data-ttu-id="01cff-118">Comme le script bash lit également les commutateurs PowerShell, vous pouvez utiliser ces derniers avec le script sur les systèmes Linux/macOS.</span><span class="sxs-lookup"><span data-stu-id="01cff-118">The bash script also reads PowerShell switches, so you can use PowerShell switches with the script on Linux/macOS systems.</span></span>

<span data-ttu-id="01cff-119">Les scripts d’installation téléchargent le fichier ZIP/tarball à partir des cibles de builds CLI, puis poursuivent l’installation dans l’emplacement par défaut ou dans un emplacement spécifié par `-InstallDir|--install-dir`.</span><span class="sxs-lookup"><span data-stu-id="01cff-119">The installation scripts download the ZIP/tarball file from the CLI build drops and proceed to install it in either the default location or in a location specified by `-InstallDir|--install-dir`.</span></span> <span data-ttu-id="01cff-120">Par défaut, les scripts d’installation téléchargent et installent le Kit de développement logiciel (SDK).</span><span class="sxs-lookup"><span data-stu-id="01cff-120">By default, the installation scripts download the SDK and install it.</span></span> <span data-ttu-id="01cff-121">Si vous souhaitez obtenir uniquement le runtime partagé, spécifiez l’argument `--runtime`.</span><span class="sxs-lookup"><span data-stu-id="01cff-121">If you wish to only obtain the shared runtime, specify the `--runtime` argument.</span></span>

<span data-ttu-id="01cff-122">Par défaut, le script ajoute l’emplacement d’installation $PATH pour la session active.</span><span class="sxs-lookup"><span data-stu-id="01cff-122">By default, the script adds the install location to the $PATH for the current session.</span></span> <span data-ttu-id="01cff-123">Remplacez ce comportement par défaut en spécifiant l’argument `--no-path`.</span><span class="sxs-lookup"><span data-stu-id="01cff-123">Override this default behavior by specifying the `--no-path` argument.</span></span>

<span data-ttu-id="01cff-124">Avant d’exécuter le script, installez les [dépendances](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md) nécessaires.</span><span class="sxs-lookup"><span data-stu-id="01cff-124">Before running the script, install the required [dependencies](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md).</span></span>

<span data-ttu-id="01cff-125">Vous pouvez installer une version spécifique à l’aide de l’argument `--version`.</span><span class="sxs-lookup"><span data-stu-id="01cff-125">You can install a specific version using the `--version` argument.</span></span> <span data-ttu-id="01cff-126">La version doit être spécifiée en trois parties (par exemple, 1.0.0-13232).</span><span class="sxs-lookup"><span data-stu-id="01cff-126">The version must be specified as a three-part version (for example, 1.0.0-13232).</span></span> <span data-ttu-id="01cff-127">Si aucune valeur n’est spécifiée, la version `latest` est utilisée.</span><span class="sxs-lookup"><span data-stu-id="01cff-127">If not provided, it uses the `latest` version.</span></span>

## <a name="options"></a><span data-ttu-id="01cff-128">Options</span><span class="sxs-lookup"><span data-stu-id="01cff-128">Options</span></span>

- **`-Channel <CHANNEL>`**

  <span data-ttu-id="01cff-129">Spécifie le canal source pour l’installation.</span><span class="sxs-lookup"><span data-stu-id="01cff-129">Specifies the source channel for the installation.</span></span> <span data-ttu-id="01cff-130">Les valeurs possibles sont :</span><span class="sxs-lookup"><span data-stu-id="01cff-130">The possible values are:</span></span>

  - <span data-ttu-id="01cff-131">`Current` - Version la plus récente.</span><span class="sxs-lookup"><span data-stu-id="01cff-131">`Current` - Most current release.</span></span>
  - <span data-ttu-id="01cff-132">`LTS` - Canal de prise en charge à long terme (dernière version prise en charge).</span><span class="sxs-lookup"><span data-stu-id="01cff-132">`LTS` - Long-Term Support channel (most current supported release).</span></span>
  - <span data-ttu-id="01cff-133">Version en deux parties au format X.Y représentant une version spécifique (par exemple, `2.0` ou `1.0`).</span><span class="sxs-lookup"><span data-stu-id="01cff-133">Two-part version in X.Y format representing a specific release (for example, `2.0` or `1.0`).</span></span>
  - <span data-ttu-id="01cff-134">Nom de la branche.</span><span class="sxs-lookup"><span data-stu-id="01cff-134">Branch name.</span></span> <span data-ttu-id="01cff-135">Par exemple, `release/2.0.0`, `release/2.0.0-preview2` ou `master` (pour les publications de nuit).</span><span class="sxs-lookup"><span data-stu-id="01cff-135">For example, `release/2.0.0`, `release/2.0.0-preview2`, or `master` (for nightly releases).</span></span>

  <span data-ttu-id="01cff-136">La valeur par défaut est `LTS`.</span><span class="sxs-lookup"><span data-stu-id="01cff-136">The default value is `LTS`.</span></span> <span data-ttu-id="01cff-137">Pour plus d’informations sur les canaux de prise en charge de .NET, consultez la page [Stratégie de prise en charge .NET](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="01cff-137">For more information on .NET support channels, see the [.NET Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) page.</span></span>

- **`-Version <VERSION>`**

  <span data-ttu-id="01cff-138">Représente une version spécifique.</span><span class="sxs-lookup"><span data-stu-id="01cff-138">Represents a specific build version.</span></span> <span data-ttu-id="01cff-139">Les valeurs possibles sont :</span><span class="sxs-lookup"><span data-stu-id="01cff-139">The possible values are:</span></span>

  - <span data-ttu-id="01cff-140">`latest` : dernière version sur le canal (utilisée avec l’option `-Channel`).</span><span class="sxs-lookup"><span data-stu-id="01cff-140">`latest` - Latest build on the channel (used with the `-Channel` option).</span></span>
  - <span data-ttu-id="01cff-141">`coherent` : dernière version cohérente sur le canal ; utilise la dernière combinaison de packages stable (utilisée avec les options `-Channel` de nom de branche).</span><span class="sxs-lookup"><span data-stu-id="01cff-141">`coherent` - Latest coherent build on the channel; uses the latest stable package combination (used with Branch name `-Channel` options).</span></span>
  - <span data-ttu-id="01cff-142">Version en trois parties au format X.Y.Z représentant une version spécifique ; remplace l’option `-Channel`.</span><span class="sxs-lookup"><span data-stu-id="01cff-142">Three-part version in X.Y.Z format representing a specific build version; supersedes the `-Channel` option.</span></span> <span data-ttu-id="01cff-143">Par exemple : `2.0.0-preview2-006120`.</span><span class="sxs-lookup"><span data-stu-id="01cff-143">For example: `2.0.0-preview2-006120`.</span></span>

  <span data-ttu-id="01cff-144">Si aucune valeur n’est spécifiée, `-Version` est définie par défaut sur `latest`.</span><span class="sxs-lookup"><span data-stu-id="01cff-144">If not specified, `-Version` defaults to `latest`.</span></span>

- **`-InstallDir <DIRECTORY>`**

  <span data-ttu-id="01cff-145">Spécifie le chemin d’accès de l’installation.</span><span class="sxs-lookup"><span data-stu-id="01cff-145">Specifies the installation path.</span></span> <span data-ttu-id="01cff-146">S’il n’existe pas déjà, le répertoire est créé.</span><span class="sxs-lookup"><span data-stu-id="01cff-146">The directory is created if it doesn't exist.</span></span> <span data-ttu-id="01cff-147">La valeur par défaut est *%LocalAppData%\Microsoft\dotnet*.</span><span class="sxs-lookup"><span data-stu-id="01cff-147">The default value is *%LocalAppData%\Microsoft\dotnet*.</span></span> <span data-ttu-id="01cff-148">Les fichiers binaires sont placés directement dans ce répertoire.</span><span class="sxs-lookup"><span data-stu-id="01cff-148">Binaries are placed directly in this directory.</span></span>

- **`-Architecture <ARCHITECTURE>`**

  <span data-ttu-id="01cff-149">Architecture des fichiers binaires .NET Core à installer.</span><span class="sxs-lookup"><span data-stu-id="01cff-149">Architecture of the .NET Core binaries to install.</span></span> <span data-ttu-id="01cff-150">Les valeurs possibles sont `<auto>`, `amd64`, `x64`, `x86`, `arm64` et `arm`.</span><span class="sxs-lookup"><span data-stu-id="01cff-150">Possible values are `<auto>`, `amd64`, `x64`, `x86`, `arm64`, and `arm`.</span></span> <span data-ttu-id="01cff-151">La valeur par défaut est `<auto>`, qui représente l’architecture de système d’exploitation en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="01cff-151">The default value is `<auto>`, which represents the currently running OS architecture.</span></span>

- **`-SharedRuntime`**

  > [!NOTE]
  > <span data-ttu-id="01cff-152">Ce paramètre est obsolète et sera peut-être supprimé dans une future version du script.</span><span class="sxs-lookup"><span data-stu-id="01cff-152">This parameter is obsolete and may be removed in a future version of the script.</span></span> <span data-ttu-id="01cff-153">L'alternative recommandée est l’option `Runtime`.</span><span class="sxs-lookup"><span data-stu-id="01cff-153">The recommended alternative is the `Runtime` option.</span></span>

  <span data-ttu-id="01cff-154">Installe uniquement les bits du runtime partagé et non l’intégralité du SDK.</span><span class="sxs-lookup"><span data-stu-id="01cff-154">Installs just the shared runtime bits, not the entire SDK.</span></span> <span data-ttu-id="01cff-155">Cela équivaut à spécifier `-Runtime dotnet`.</span><span class="sxs-lookup"><span data-stu-id="01cff-155">This is equivalent to specifying `-Runtime dotnet`.</span></span>

- **`-Runtime <RUNTIME>`**

  <span data-ttu-id="01cff-156">Installe uniquement le runtime partagé et non l’intégralité du SDK.</span><span class="sxs-lookup"><span data-stu-id="01cff-156">Installs just the shared runtime, not the entire SDK.</span></span> <span data-ttu-id="01cff-157">Les valeurs possibles sont :</span><span class="sxs-lookup"><span data-stu-id="01cff-157">The possible values are:</span></span>

  - <span data-ttu-id="01cff-158">`dotnet` - le runtime partagé `Microsoft.NETCore.App`.</span><span class="sxs-lookup"><span data-stu-id="01cff-158">`dotnet` - the `Microsoft.NETCore.App` shared runtime.</span></span>
  - <span data-ttu-id="01cff-159">`aspnetcore` - le runtime partagé `Microsoft.AspNetCore.App`.</span><span class="sxs-lookup"><span data-stu-id="01cff-159">`aspnetcore` - the `Microsoft.AspNetCore.App` shared runtime.</span></span>

- **`-DryRun`**

  <span data-ttu-id="01cff-160">Si cette option est définie, le script n’effectue pas l’installation.</span><span class="sxs-lookup"><span data-stu-id="01cff-160">If set, the script won't perform the installation.</span></span> <span data-ttu-id="01cff-161">Affiche à la place la ligne de commande à utiliser pour installer la version de l’interface CLI .NET Core actuellement demandée.</span><span class="sxs-lookup"><span data-stu-id="01cff-161">Instead, it displays what command line to use to consistently install the currently requested version of the .NET Core CLI.</span></span> <span data-ttu-id="01cff-162">Par exemple, si vous spécifiez la version `latest`, elle affiche un lien avec la version spécifique, pour que cette commande puisse être utilisée de façon déterministe dans un script de génération.</span><span class="sxs-lookup"><span data-stu-id="01cff-162">For example, if you specify version `latest`, it displays a link with the specific version so that this command can be used deterministically in a build script.</span></span> <span data-ttu-id="01cff-163">Elle affiche également l’emplacement du fichier binaire si vous préférez l’installer ou le télécharger vous-même.</span><span class="sxs-lookup"><span data-stu-id="01cff-163">It also displays the binary's location if you prefer to install or download it yourself.</span></span>

- **`-NoPath`**

  <span data-ttu-id="01cff-164">Si cette option est définie, le dossier d’installation n’est pas exporté dans le chemin de la session actuelle.</span><span class="sxs-lookup"><span data-stu-id="01cff-164">If set, the installation folder isn't exported to the path for the current session.</span></span> <span data-ttu-id="01cff-165">Par défaut, le script modifie le chemin, ce qui rend les outils CLI disponibles immédiatement après l’installation.</span><span class="sxs-lookup"><span data-stu-id="01cff-165">By default, the script modifies the PATH, which makes the CLI tools available immediately after install.</span></span>

- **`-Verbose`**

  <span data-ttu-id="01cff-166">Affiche les informations de diagnostic.</span><span class="sxs-lookup"><span data-stu-id="01cff-166">Displays diagnostics information.</span></span>

- **`-AzureFeed`**

  <span data-ttu-id="01cff-167">Spécifie l’URL du flux Azure à utiliser par ce programme d’installation.</span><span class="sxs-lookup"><span data-stu-id="01cff-167">Specifies the URL for the Azure feed to the installer.</span></span> <span data-ttu-id="01cff-168">Nous recommandons de ne pas modifier cette valeur.</span><span class="sxs-lookup"><span data-stu-id="01cff-168">We recommended that you don't change this value.</span></span> <span data-ttu-id="01cff-169">La valeur par défaut est `https://dotnetcli.azureedge.net/dotnet`.</span><span class="sxs-lookup"><span data-stu-id="01cff-169">The default value is `https://dotnetcli.azureedge.net/dotnet`.</span></span>

- **`-UncachedFeed`**

  <span data-ttu-id="01cff-170">Permet de changer l’URL pour le flux non mis en cache utilisé par ce programme d’installation.</span><span class="sxs-lookup"><span data-stu-id="01cff-170">Allows changing the URL for the uncached feed used by this installer.</span></span> <span data-ttu-id="01cff-171">Nous recommandons de ne pas modifier cette valeur.</span><span class="sxs-lookup"><span data-stu-id="01cff-171">We recommended that you don't change this value.</span></span>

- **`-NoCdn`**

  <span data-ttu-id="01cff-172">Désactive le téléchargement à partir d’[Azure Content Delivery Network (CDN)](https://docs.microsoft.com/azure/cdn/cdn-overview) et utilise directement le flux non mis en cache.</span><span class="sxs-lookup"><span data-stu-id="01cff-172">Disables downloading from the [Azure Content Delivery Network (CDN)](https://docs.microsoft.com/azure/cdn/cdn-overview) and uses the uncached feed directly.</span></span>

- **`-FeedCredential`**

  <span data-ttu-id="01cff-173">Valeur utilisée comme chaîne de requête à ajouter au flux Azure.</span><span class="sxs-lookup"><span data-stu-id="01cff-173">Used as a query string to append to the Azure feed.</span></span> <span data-ttu-id="01cff-174">Elle permet de changer l’URL afin d’utiliser des comptes de stockage d’objets blob non publics.</span><span class="sxs-lookup"><span data-stu-id="01cff-174">It allows changing the URL to use non-public blob storage accounts.</span></span>

- **`-ProxyAddress`**

  <span data-ttu-id="01cff-175">Si cette option est définie, le programme d’installation utilise le proxy pendant la création de demandes web.</span><span class="sxs-lookup"><span data-stu-id="01cff-175">If set, the installer uses the proxy when making web requests.</span></span> <span data-ttu-id="01cff-176">(valide uniquement pour Windows)</span><span class="sxs-lookup"><span data-stu-id="01cff-176">(Only valid for Windows)</span></span>

- **`ProxyUseDefaultCredentials`**

  <span data-ttu-id="01cff-177">Si cette option est définie, le programme d’installation utilise les informations d’identification de l’utilisateur actuel lors de l’utilisation de l’adresse proxy.</span><span class="sxs-lookup"><span data-stu-id="01cff-177">If set, the installer uses the credentials of the current user when using proxy address.</span></span> <span data-ttu-id="01cff-178">(valide uniquement pour Windows)</span><span class="sxs-lookup"><span data-stu-id="01cff-178">(Only valid for Windows)</span></span>

- **`-SkipNonVersionedFiles`**

  <span data-ttu-id="01cff-179">Ignore l’installation des fichiers sans version, notamment *dotnet.exe*, s’ils existent déjà.</span><span class="sxs-lookup"><span data-stu-id="01cff-179">Skips installing non-versioned files, such as *dotnet.exe*, if they already exist.</span></span>

- **`-Help`**

  <span data-ttu-id="01cff-180">Affiche l’aide pour le script.</span><span class="sxs-lookup"><span data-stu-id="01cff-180">Prints out help for the script.</span></span>

## <a name="examples"></a><span data-ttu-id="01cff-181">Exemples</span><span class="sxs-lookup"><span data-stu-id="01cff-181">Examples</span></span>

- <span data-ttu-id="01cff-182">Installez la dernière version LTS (Long Term Support) à l’emplacement par défaut :</span><span class="sxs-lookup"><span data-stu-id="01cff-182">Install the latest long-term supported (LTS) version to the default location:</span></span>

  <span data-ttu-id="01cff-183">Windows :</span><span class="sxs-lookup"><span data-stu-id="01cff-183">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Channel LTS
  ```

  <span data-ttu-id="01cff-184">Mac OS/Linux :</span><span class="sxs-lookup"><span data-stu-id="01cff-184">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --channel LTS
  ```

- <span data-ttu-id="01cff-185">Installez la dernière version depuis le canal 2.0 à l’emplacement spécifié :</span><span class="sxs-lookup"><span data-stu-id="01cff-185">Install the latest version from 2.0 channel to the specified location:</span></span>

  <span data-ttu-id="01cff-186">Windows :</span><span class="sxs-lookup"><span data-stu-id="01cff-186">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Channel 2.0 -InstallDir C:\cli
  ```

  <span data-ttu-id="01cff-187">Mac OS/Linux :</span><span class="sxs-lookup"><span data-stu-id="01cff-187">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --channel 2.0 --install-dir ~/cli
  ```

- <span data-ttu-id="01cff-188">Installez la version 1.1.0 du runtime partagé :</span><span class="sxs-lookup"><span data-stu-id="01cff-188">Install the 1.1.0 version of the shared runtime:</span></span>

  <span data-ttu-id="01cff-189">Windows :</span><span class="sxs-lookup"><span data-stu-id="01cff-189">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Runtime dotnet -Version 1.1.0
  ```

  <span data-ttu-id="01cff-190">Mac OS/Linux :</span><span class="sxs-lookup"><span data-stu-id="01cff-190">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --runtime dotnet --version 1.1.0
  ```

- <span data-ttu-id="01cff-191">Obtenir le script et installer la version 2.1.2 derrière un proxy d’entreprise (Windows uniquement) :</span><span class="sxs-lookup"><span data-stu-id="01cff-191">Obtain script and install the 2.1.2 version behind a corporate proxy (Windows only):</span></span>

  ```powershell
  Invoke-WebRequest 'https://dot.net/v1/dotnet-install.ps1' -Proxy $env:HTTP_PROXY -ProxyUseDefaultCredentials -OutFile 'dotnet-install.ps1';
  ./dotnet-install.ps1 -InstallDir '~/.dotnet' -Version '2.1.2' -ProxyAddress $env:HTTP_PROXY -ProxyUseDefaultCredentials;
  ```

- <span data-ttu-id="01cff-192">Obtenir le script et installer les exemples unilignes de l’interface CLI .NET Core :</span><span class="sxs-lookup"><span data-stu-id="01cff-192">Obtain script and install .NET Core CLI one-liner examples:</span></span>

  <span data-ttu-id="01cff-193">Windows :</span><span class="sxs-lookup"><span data-stu-id="01cff-193">Windows:</span></span>

  ```powershell
  @powershell -NoProfile -ExecutionPolicy unrestricted -Command "[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12; &([scriptblock]::Create((Invoke-WebRequest -UseBasicParsing 'https://dot.net/v1/dotnet-install.ps1'))) <additional install-script args>"
  ```

  <span data-ttu-id="01cff-194">Mac OS/Linux :</span><span class="sxs-lookup"><span data-stu-id="01cff-194">macOS/Linux:</span></span>

  ```bash
  curl -ssl https://dot.net/v1/dotnet-install.sh | bash /dev/stdin <additional install-script args>
  ```

## <a name="see-also"></a><span data-ttu-id="01cff-195">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="01cff-195">See also</span></span>

- [<span data-ttu-id="01cff-196">Versions de .NET Core</span><span class="sxs-lookup"><span data-stu-id="01cff-196">.NET Core releases</span></span>](https://github.com/dotnet/core/releases)
- [<span data-ttu-id="01cff-197">Archive de téléchargement de .NET Core Runtime et du Kit SDK</span><span class="sxs-lookup"><span data-stu-id="01cff-197">.NET Core Runtime and SDK download archive</span></span>](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md)
