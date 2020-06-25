---
title: Installer kit SDK .NET Core sur Windows, Linux et macOS-.NET Core
description: Découvrez comment installer .NET Core sur Windows, Linux et macOS. Découvrez les dépendances requises pour développer des applications .NET Core.
author: adegeo
ms.author: adegeo
ms.date: 05/04/2020
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: a11d1eb3bae6affaa548407cbd68c166a30e99da
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85324666"
---
# <a name="install-the-net-core-sdk"></a><span data-ttu-id="3e303-104">Installer le kit SDK .NET Core</span><span class="sxs-lookup"><span data-stu-id="3e303-104">Install the .NET Core SDK</span></span>

<span data-ttu-id="3e303-105">Dans cet article, vous allez apprendre à installer le kit SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3e303-105">In this article, you'll learn how to install the .NET Core SDK.</span></span> <span data-ttu-id="3e303-106">Le kit SDK .NET Core est utilisé pour créer des applications et des bibliothèques .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3e303-106">The .NET Core SDK is used to create .NET Core apps and libraries.</span></span> <span data-ttu-id="3e303-107">Le Runtime .NET Core est toujours installé avec le kit de développement logiciel (SDK).</span><span class="sxs-lookup"><span data-stu-id="3e303-107">The .NET Core runtime is always installed with the SDK.</span></span>

::: zone pivot="os-windows"

## <a name="install-with-an-installer"></a><span data-ttu-id="3e303-108">Installer avec un programme d’installation</span><span class="sxs-lookup"><span data-stu-id="3e303-108">Install with an installer</span></span>

<span data-ttu-id="3e303-109">Windows possède des programmes d’installation autonomes qui peuvent être utilisés pour installer le kit de développement logiciel (SDK) .NET Core 3,1 :</span><span class="sxs-lookup"><span data-stu-id="3e303-109">Windows has standalone installers that can be used to install the .NET Core 3.1 SDK:</span></span>

- [<span data-ttu-id="3e303-110">Processeurs x64 (64 bits)</span><span class="sxs-lookup"><span data-stu-id="3e303-110">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="3e303-111">Processeurs x86 (32 bits)</span><span class="sxs-lookup"><span data-stu-id="3e303-111">x86 (32-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-an-installer"></a><span data-ttu-id="3e303-112">Installer avec un programme d’installation</span><span class="sxs-lookup"><span data-stu-id="3e303-112">Install with an installer</span></span>

<span data-ttu-id="3e303-113">macOS possède des programmes d’installation autonomes qui peuvent être utilisés pour installer le kit de développement logiciel (SDK) .NET Core 3,1 :</span><span class="sxs-lookup"><span data-stu-id="3e303-113">macOS has standalone installers that can be used to install the .NET Core 3.1 SDK:</span></span>

- [<span data-ttu-id="3e303-114">Processeurs x64 (64 bits)</span><span class="sxs-lookup"><span data-stu-id="3e303-114">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

## <a name="download-and-manually-install"></a><span data-ttu-id="3e303-115">Télécharger et installer manuellement</span><span class="sxs-lookup"><span data-stu-id="3e303-115">Download and manually install</span></span>

<span data-ttu-id="3e303-116">Comme alternative aux programmes d’installation macOS pour .NET Core, vous pouvez télécharger et installer manuellement le kit de développement logiciel (SDK).</span><span class="sxs-lookup"><span data-stu-id="3e303-116">As an alternative to the macOS installers for .NET Core, you can download and manually install the SDK.</span></span>

<span data-ttu-id="3e303-117">Pour extraire le kit de développement logiciel (SDK) et rendre les commandes de CLI .NET Core disponibles sur le terminal, commencez par [Télécharger](#all-net-core-downloads) une version binaire de .net core.</span><span class="sxs-lookup"><span data-stu-id="3e303-117">To extract the SDK and make the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="3e303-118">Ensuite, ouvrez un terminal et exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="3e303-118">Then, open a terminal and run the following commands.</span></span> <span data-ttu-id="3e303-119">Il est supposé que le runtime est téléchargé dans le `~/Downloads/dotnet-sdk.pkg` fichier.</span><span class="sxs-lookup"><span data-stu-id="3e303-119">It's assumed the runtime is downloaded to the `~/Downloads/dotnet-sdk.pkg` file.</span></span>

```bash
mkdir -p $HOME/dotnet
sudo installer -pkg ~/Downloads/dotnet-sdk.pkg -target $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

::: zone-end

::: zone pivot="os-linux"

## <a name="install-on-linux"></a><span data-ttu-id="3e303-120">Installer sur Linux</span><span class="sxs-lookup"><span data-stu-id="3e303-120">Install on Linux</span></span>

<span data-ttu-id="3e303-121">Cet article sera bientôt supprimé.</span><span class="sxs-lookup"><span data-stu-id="3e303-121">This article will be removed soon.</span></span> <span data-ttu-id="3e303-122">Il est actuellement remplacé par [install .net Core sur Linux](linux.md).</span><span class="sxs-lookup"><span data-stu-id="3e303-122">It is currently replaced by [Install .NET Core on Linux](linux.md).</span></span>

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-visual-studio"></a><span data-ttu-id="3e303-123">Installer avec Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3e303-123">Install with Visual Studio</span></span>

<span data-ttu-id="3e303-124">Si vous utilisez Visual Studio pour développer des applications .NET Core, le tableau suivant décrit la version minimale requise de Visual Studio en fonction de la version de kit SDK .NET Core cible.</span><span class="sxs-lookup"><span data-stu-id="3e303-124">If you're using Visual Studio to develop .NET Core apps, the following table describes the minimum required version of Visual Studio based on the target .NET Core SDK version.</span></span>

| <span data-ttu-id="3e303-125">Version de kit SDK .NET Core</span><span class="sxs-lookup"><span data-stu-id="3e303-125">.NET Core SDK version</span></span> | <span data-ttu-id="3e303-126">Version de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3e303-126">Visual Studio version</span></span>                      |
| --------------------- | ------------------------------------------ |
| <span data-ttu-id="3e303-127">3.1</span><span class="sxs-lookup"><span data-stu-id="3e303-127">3.1</span></span>                   | <span data-ttu-id="3e303-128">Visual Studio 2019 version 16,4 ou ultérieure.</span><span class="sxs-lookup"><span data-stu-id="3e303-128">Visual Studio 2019 version 16.4 or higher.</span></span> |
| <span data-ttu-id="3e303-129">3.0</span><span class="sxs-lookup"><span data-stu-id="3e303-129">3.0</span></span>                   | <span data-ttu-id="3e303-130">Visual Studio 2019 version 16,3 ou ultérieure.</span><span class="sxs-lookup"><span data-stu-id="3e303-130">Visual Studio 2019 version 16.3 or higher.</span></span> |
| <span data-ttu-id="3e303-131">2.2</span><span class="sxs-lookup"><span data-stu-id="3e303-131">2.2</span></span>                   | <span data-ttu-id="3e303-132">Visual Studio 2017 version 15,9 ou ultérieure.</span><span class="sxs-lookup"><span data-stu-id="3e303-132">Visual Studio 2017 version 15.9 or higher.</span></span> |
| <span data-ttu-id="3e303-133">2.1</span><span class="sxs-lookup"><span data-stu-id="3e303-133">2.1</span></span>                   | <span data-ttu-id="3e303-134">Visual Studio 2017 version 15,7 ou ultérieure.</span><span class="sxs-lookup"><span data-stu-id="3e303-134">Visual Studio 2017 version 15.7 or higher.</span></span> |

<span data-ttu-id="3e303-135">Si vous avez déjà installé Visual Studio, vous pouvez vérifier votre version en procédant comme suit.</span><span class="sxs-lookup"><span data-stu-id="3e303-135">If you already have Visual Studio installed, you can check your version with the following steps.</span></span>

01. <span data-ttu-id="3e303-136">Ouvrez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3e303-136">Open Visual Studio.</span></span>
01. <span data-ttu-id="3e303-137">Sélectionnez **aide**  >  **sur Microsoft Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="3e303-137">Select **Help** > **About Microsoft Visual Studio**.</span></span>
01. <span data-ttu-id="3e303-138">Lisez le numéro de version dans la boîte de dialogue **à propos** de.</span><span class="sxs-lookup"><span data-stu-id="3e303-138">Read the version number from the **About** dialog.</span></span>

<span data-ttu-id="3e303-139">Visual Studio peut installer les kit SDK .NET Core et Runtime les plus récents.</span><span class="sxs-lookup"><span data-stu-id="3e303-139">Visual Studio can install the latest .NET Core SDK and runtime.</span></span>

- <span data-ttu-id="3e303-140">[Téléchargez Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span><span class="sxs-lookup"><span data-stu-id="3e303-140">[Download Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span></span>

### <a name="select-a-workload"></a><span data-ttu-id="3e303-141">Sélectionner une charge de travail</span><span class="sxs-lookup"><span data-stu-id="3e303-141">Select a workload</span></span>

<span data-ttu-id="3e303-142">Lors de l’installation ou de la modification de Visual Studio, sélectionnez une ou plusieurs des charges de travail suivantes, en fonction du type d’application que vous créez :</span><span class="sxs-lookup"><span data-stu-id="3e303-142">When installing or modifying Visual Studio, select one or more of the following workloads, depending on the kind of application you're building:</span></span>

- <span data-ttu-id="3e303-143">La charge de travail **développement multiplateforme .net Core** dans la section **autres ensembles d’outils** .</span><span class="sxs-lookup"><span data-stu-id="3e303-143">The **.NET Core cross-platform development** workload in the **Other Toolsets** section.</span></span>
- <span data-ttu-id="3e303-144">La charge de travail **ASP.net et développement Web** dans la section **Web & Cloud** .</span><span class="sxs-lookup"><span data-stu-id="3e303-144">The **ASP.NET and web development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="3e303-145">La charge de travail **développement Azure** dans la section **Web & Cloud** .</span><span class="sxs-lookup"><span data-stu-id="3e303-145">The **Azure development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="3e303-146">La charge de travail **développement .net Desktop** dans la section **Desktop & mobile** .</span><span class="sxs-lookup"><span data-stu-id="3e303-146">The **.NET desktop development** workload in the **Desktop & Mobile** section.</span></span>

<span data-ttu-id="3e303-147">[![Windows Visual Studio 2019 avec charge de travail .NET Core](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="3e303-147">[![Windows Visual Studio 2019 with .NET Core workload](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="3e303-148">Télécharger et installer manuellement</span><span class="sxs-lookup"><span data-stu-id="3e303-148">Download and manually install</span></span>

<span data-ttu-id="3e303-149">Pour extraire le runtime et rendre les commandes CLI .NET Core disponibles sur le terminal, commencez par [Télécharger](#all-net-core-downloads) une version binaire .net core.</span><span class="sxs-lookup"><span data-stu-id="3e303-149">To extract the runtime and make the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="3e303-150">Ensuite, créez un répertoire dans lequel installer, par exemple `%USERPROFILE%\dotnet` .</span><span class="sxs-lookup"><span data-stu-id="3e303-150">Then, create a directory to install to, for example `%USERPROFILE%\dotnet`.</span></span> <span data-ttu-id="3e303-151">Enfin, extrayez le fichier zip téléchargé dans ce répertoire.</span><span class="sxs-lookup"><span data-stu-id="3e303-151">Finally, extract the downloaded zip file into that directory.</span></span>

<span data-ttu-id="3e303-152">Par défaut, les commandes et les applications CLI .NET Core n’utilisent pas .NET Core de cette manière et vous devez choisir explicitement de l’utiliser.</span><span class="sxs-lookup"><span data-stu-id="3e303-152">By default, .NET Core CLI commands and apps won't use .NET Core installed in this way and you must explicitly choose to use it.</span></span> <span data-ttu-id="3e303-153">Pour ce faire, modifiez les variables d’environnement à l’aide desquelles une application est démarrée :</span><span class="sxs-lookup"><span data-stu-id="3e303-153">To do so, change the environment variables with which an application is started:</span></span>

```console
set DOTNET_ROOT=%USERPROFILE%\dotnet
set PATH=%USERPROFILE%\dotnet;%PATH%
```

<span data-ttu-id="3e303-154">Cette approche vous permet d’installer plusieurs versions dans des emplacements distincts, puis de choisir explicitement l’emplacement d’installation qu’une application doit utiliser en exécutant l’application avec des variables d’environnement qui pointent à cet emplacement.</span><span class="sxs-lookup"><span data-stu-id="3e303-154">This approach lets you install multiple versions into separate locations, then explicitly choose which install location an application should use by running the application with environment variables pointing at that location.</span></span>

<span data-ttu-id="3e303-155">Même lorsque ces variables d’environnement sont définies, .NET Core prend toujours en compte l’emplacement d’installation globale par défaut lors de la sélection du meilleur Framework pour l’exécution de l’application.</span><span class="sxs-lookup"><span data-stu-id="3e303-155">Even when these environment variables are set, .NET Core still considers the default global install location when selecting the best framework for running the application.</span></span> <span data-ttu-id="3e303-156">La valeur par défaut est généralement `C:\Program Files\dotnet` , que les programmes d’installation utilisent.</span><span class="sxs-lookup"><span data-stu-id="3e303-156">The default is typically `C:\Program Files\dotnet`, which the installers use.</span></span> <span data-ttu-id="3e303-157">Vous pouvez indiquer à l’exécution d’utiliser uniquement l’emplacement d’installation personnalisé en définissant également cette variable d’environnement :</span><span class="sxs-lookup"><span data-stu-id="3e303-157">You can instruct the runtime to only use the custom install location by setting this environment variable as well:</span></span>

```console
set DOTNET_MULTILEVEL_LOOKUP=0
```

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-visual-studio-for-mac"></a><span data-ttu-id="3e303-158">Installer avec Visual Studio pour Mac</span><span class="sxs-lookup"><span data-stu-id="3e303-158">Install with Visual Studio for Mac</span></span>

<span data-ttu-id="3e303-159">Visual Studio pour Mac installe le kit SDK .NET Core lorsque la charge de travail **.net Core** est sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="3e303-159">Visual Studio for Mac installs the .NET Core SDK when the **.NET Core** workload is selected.</span></span> <span data-ttu-id="3e303-160">Pour commencer à utiliser le développement .NET Core sur macOS, consultez [installer Visual Studio 2019 pour Mac](/visualstudio/mac/installation).</span><span class="sxs-lookup"><span data-stu-id="3e303-160">To get started with .NET Core development on macOS, see [Install Visual Studio 2019 for Mac](/visualstudio/mac/installation).</span></span> <span data-ttu-id="3e303-161">Pour la version la plus récente, .NET Core 3,1, vous devez utiliser le Visual Studio pour Mac 8,4 preview.</span><span class="sxs-lookup"><span data-stu-id="3e303-161">For the latest release, .NET Core 3.1, you must use the Visual Studio for Mac 8.4 Preview.</span></span>

<span data-ttu-id="3e303-162">[![macOS Visual Studio 2019 pour Mac avec la charge de travail .NET Core](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="3e303-162">[![macOS Visual Studio 2019 for Mac with .NET Core workload feature](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span></span>

::: zone-end

::: zone pivot="os-windows,os-macos"

## <a name="install-alongside-visual-studio-code"></a><span data-ttu-id="3e303-163">Installer en même temps que Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="3e303-163">Install alongside Visual Studio Code</span></span>

<span data-ttu-id="3e303-164">Visual Studio Code est un éditeur de code source puissant et léger qui s’exécute sur votre bureau.</span><span class="sxs-lookup"><span data-stu-id="3e303-164">Visual Studio Code is a powerful and lightweight source code editor that runs on your desktop.</span></span> <span data-ttu-id="3e303-165">Visual Studio Code est disponible pour Windows, macOS et Linux.</span><span class="sxs-lookup"><span data-stu-id="3e303-165">Visual Studio Code is available for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="3e303-166">Même si Visual Studio Code n’est pas fourni avec un programme d’installation automatisé de .NET Core, comme Visual Studio, l’ajout de la prise en charge de .NET Core est simple.</span><span class="sxs-lookup"><span data-stu-id="3e303-166">While Visual Studio Code doesn't come with an automated .NET Core installer like Visual Studio does, adding .NET Core support is simple.</span></span>

01. <span data-ttu-id="3e303-167">[Téléchargez et installez Visual Studio code](https://code.visualstudio.com/Download).</span><span class="sxs-lookup"><span data-stu-id="3e303-167">[Download and install Visual Studio Code](https://code.visualstudio.com/Download).</span></span>
01. <span data-ttu-id="3e303-168">[Téléchargez et installez le kit SDK .net Core](https://dotnet.microsoft.com/download/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="3e303-168">[Download and install the .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core).</span></span>
01. <span data-ttu-id="3e303-169">[Installez l’extension C# à partir de la place de marché Visual Studio code](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp).</span><span class="sxs-lookup"><span data-stu-id="3e303-169">[Install the C# extension from the Visual Studio Code marketplace](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp).</span></span>

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a><span data-ttu-id="3e303-170">Installer avec l’automatisation PowerShell</span><span class="sxs-lookup"><span data-stu-id="3e303-170">Install with PowerShell automation</span></span>

<span data-ttu-id="3e303-171">Les [scripts dotnet-install](../tools/dotnet-install-script.md) sont utilisés pour l’automatisation et les installations non administratives du kit de développement logiciel (SDK).</span><span class="sxs-lookup"><span data-stu-id="3e303-171">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the SDK.</span></span> <span data-ttu-id="3e303-172">Vous pouvez télécharger le script à partir de la [page de référence du script dotnet-install](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="3e303-172">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="3e303-173">Par défaut, le script installe la dernière version de [support à long terme (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , qui est .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="3e303-173">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="3e303-174">Pour installer la version actuelle de .NET Core, exécutez le script avec le commutateur suivant.</span><span class="sxs-lookup"><span data-stu-id="3e303-174">To install the current release of .NET Core, run the script with the following switch.</span></span>

```powershell
dotnet-install.ps1 -Channel Current
```

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-bash-automation"></a><span data-ttu-id="3e303-175">Installer avec l’automatisation bash</span><span class="sxs-lookup"><span data-stu-id="3e303-175">Install with bash automation</span></span>

<span data-ttu-id="3e303-176">Les [scripts dotnet-install](../tools/dotnet-install-script.md) sont utilisés pour l’automatisation et les installations non administratives du kit de développement logiciel (SDK).</span><span class="sxs-lookup"><span data-stu-id="3e303-176">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the SDK.</span></span> <span data-ttu-id="3e303-177">Vous pouvez télécharger le script à partir de la [page de référence du script dotnet-install](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="3e303-177">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="3e303-178">Par défaut, le script installe la dernière version de [support à long terme (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , qui est .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="3e303-178">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="3e303-179">Pour installer la version actuelle de .NET Core, exécutez le script avec le commutateur suivant.</span><span class="sxs-lookup"><span data-stu-id="3e303-179">To install the current release of .NET Core, run the script with the following switch.</span></span>

```bash
./dotnet-install.sh -c Current
```

::: zone-end

## <a name="all-net-core-downloads"></a><span data-ttu-id="3e303-180">Tous les téléchargements .NET Core</span><span class="sxs-lookup"><span data-stu-id="3e303-180">All .NET Core downloads</span></span>

<span data-ttu-id="3e303-181">Vous pouvez télécharger et installer .NET Core directement avec l’un des liens suivants :</span><span class="sxs-lookup"><span data-stu-id="3e303-181">You can download and install .NET Core directly with one of the following links:</span></span>

- [<span data-ttu-id="3e303-182">Téléchargements .NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="3e303-182">.NET Core 3.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="3e303-183">Téléchargements .NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="3e303-183">.NET Core 3.0 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- [<span data-ttu-id="3e303-184">Téléchargements .NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="3e303-184">.NET Core 2.2 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- [<span data-ttu-id="3e303-185">Téléchargements .NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="3e303-185">.NET Core 2.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a><span data-ttu-id="3e303-186">Docker</span><span class="sxs-lookup"><span data-stu-id="3e303-186">Docker</span></span>

<span data-ttu-id="3e303-187">Les conteneurs offrent un moyen léger d’isoler votre application du reste du système hôte.</span><span class="sxs-lookup"><span data-stu-id="3e303-187">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="3e303-188">Les conteneurs sur le même ordinateur partagent simplement le noyau et utilisent les ressources fournies à votre application.</span><span class="sxs-lookup"><span data-stu-id="3e303-188">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="3e303-189">.NET Core peut s’exécuter dans un conteneur d’ancrage.</span><span class="sxs-lookup"><span data-stu-id="3e303-189">.NET Core can run in a Docker container.</span></span> <span data-ttu-id="3e303-190">Les images Docker .NET Core officielles sont publiées dans Microsoft Container Registry (MCR) et détectables dans le [référentiel Docker Hub Microsoft .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/).</span><span class="sxs-lookup"><span data-stu-id="3e303-190">Official .NET Core Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span> <span data-ttu-id="3e303-191">Chaque référentiel contient des images pour différentes combinaisons possibles de .NET (kit de développement logiciel ou runtime) et du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="3e303-191">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="3e303-192">Microsoft fournit des images adaptées à des scénarios particuliers.</span><span class="sxs-lookup"><span data-stu-id="3e303-192">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="3e303-193">Par exemple, celles du [référentiel ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) sont conçues pour exécuter des applications ASP.NET Core en production.</span><span class="sxs-lookup"><span data-stu-id="3e303-193">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="3e303-194">Pour plus d’informations sur l’utilisation de .NET Core dans un conteneur d’ancrage, consultez [Introduction à .net et à l’ancreur](../docker/introduction.md) et aux [exemples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span><span class="sxs-lookup"><span data-stu-id="3e303-194">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="3e303-195">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="3e303-195">Next steps</span></span>

::: zone pivot="os-windows"

- <span data-ttu-id="3e303-196">[Didacticiel : Hello World didacticiel](../tutorials/with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="3e303-196">[Tutorial: Hello World tutorial](../tutorials/with-visual-studio.md).</span></span>
- <span data-ttu-id="3e303-197">[Didacticiel : créer une application avec Visual Studio code](../tutorials/with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="3e303-197">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="3e303-198">[Didacticiel : conteneur d’une application .net Core](../docker/build-container.md).</span><span class="sxs-lookup"><span data-stu-id="3e303-198">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end

::: zone pivot="os-macos"

- <span data-ttu-id="3e303-199">[Utilisation de la notaire Catalina MacOS](macos-notarization-issues.md).</span><span class="sxs-lookup"><span data-stu-id="3e303-199">[Working with macOS Catalina notarization](macos-notarization-issues.md).</span></span>
- <span data-ttu-id="3e303-200">[Didacticiel : prise en main de MacOS](../tutorials/using-on-mac-vs.md).</span><span class="sxs-lookup"><span data-stu-id="3e303-200">[Tutorial: Get started on macOS](../tutorials/using-on-mac-vs.md).</span></span>
- <span data-ttu-id="3e303-201">[Didacticiel : créer une application avec Visual Studio code](../tutorials/with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="3e303-201">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="3e303-202">[Didacticiel : conteneur d’une application .net Core](../docker/build-container.md).</span><span class="sxs-lookup"><span data-stu-id="3e303-202">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end

::: zone pivot="os-linux"

- <span data-ttu-id="3e303-203">[Didacticiel : créer une application avec Visual Studio code](../tutorials/with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="3e303-203">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="3e303-204">[Didacticiel : conteneur d’une application .net Core](../docker/build-container.md).</span><span class="sxs-lookup"><span data-stu-id="3e303-204">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end
