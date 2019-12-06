---
title: Installer kit SDK .NET Core sur Windows, Linux et macOS-.NET Core
description: Découvrez comment installer .NET Core sur Windows, Linux et macOS. Découvrez les dépendances requises pour développer des applications .NET Core.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 5ac2d7897ee4c6707669e4f9104317aeb2e1f473
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74835681"
---
# <a name="install-the-net-core-sdk"></a><span data-ttu-id="9b2d8-104">Installer le kit SDK .NET Core</span><span class="sxs-lookup"><span data-stu-id="9b2d8-104">Install the .NET Core SDK</span></span>

<span data-ttu-id="9b2d8-105">Dans cet article, vous allez apprendre à installer le kit SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9b2d8-105">In this article, you'll learn how to install the .NET Core SDK.</span></span> <span data-ttu-id="9b2d8-106">Le kit SDK .NET Core est utilisé pour créer des applications et des bibliothèques .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9b2d8-106">The .NET Core SDK is used to create .NET Core apps and libraries.</span></span> <span data-ttu-id="9b2d8-107">Le Runtime .NET Core est toujours installé avec le kit de développement logiciel (SDK).</span><span class="sxs-lookup"><span data-stu-id="9b2d8-107">The .NET Core runtime is always installed with the SDK.</span></span>

::: zone pivot="os-windows"

## <a name="install-with-an-installer"></a><span data-ttu-id="9b2d8-108">Installer avec un programme d’installation</span><span class="sxs-lookup"><span data-stu-id="9b2d8-108">Install with an installer</span></span>

<span data-ttu-id="9b2d8-109">Windows possède des programmes d’installation autonomes qui peuvent être utilisés pour installer le kit de développement logiciel (SDK) .NET Core 3,1 :</span><span class="sxs-lookup"><span data-stu-id="9b2d8-109">Windows has standalone installers that can be used to install the .NET Core 3.1 SDK:</span></span>

- [<span data-ttu-id="9b2d8-110">Processeurs x64 (64 bits)</span><span class="sxs-lookup"><span data-stu-id="9b2d8-110">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="9b2d8-111">Processeurs x86 (32 bits)</span><span class="sxs-lookup"><span data-stu-id="9b2d8-111">x86 (32-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-an-installer"></a><span data-ttu-id="9b2d8-112">Installer avec un programme d’installation</span><span class="sxs-lookup"><span data-stu-id="9b2d8-112">Install with an installer</span></span>

<span data-ttu-id="9b2d8-113">macOS possède des programmes d’installation autonomes qui peuvent être utilisés pour installer le kit de développement logiciel (SDK) .NET Core 3,1 :</span><span class="sxs-lookup"><span data-stu-id="9b2d8-113">macOS has standalone installers that can be used to install the .NET Core 3.1 SDK:</span></span>

- [<span data-ttu-id="9b2d8-114">Processeurs x64 (64 bits)</span><span class="sxs-lookup"><span data-stu-id="9b2d8-114">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a><span data-ttu-id="9b2d8-115">Installer avec un gestionnaire de package</span><span class="sxs-lookup"><span data-stu-id="9b2d8-115">Install with a package manager</span></span>

<span data-ttu-id="9b2d8-116">Vous pouvez installer les kit SDK .NET Core avec un grand nombre de gestionnaires de packages Linux courants.</span><span class="sxs-lookup"><span data-stu-id="9b2d8-116">You can install the .NET Core SDK with many of the common Linux package managers.</span></span> <span data-ttu-id="9b2d8-117">Pour plus d’informations, consultez [Linux Package Manager-install .net Core](linux-package-managers.md).</span><span class="sxs-lookup"><span data-stu-id="9b2d8-117">For more information, see [Linux Package Manager - Install .NET Core](linux-package-managers.md).</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="9b2d8-118">Télécharger et installer manuellement</span><span class="sxs-lookup"><span data-stu-id="9b2d8-118">Download and manually install</span></span>

<span data-ttu-id="9b2d8-119">Pour extraire le kit de développement logiciel (SDK) et rendre les commandes disponibles sur le terminal, commencez par [Télécharger](#all-net-core-downloads) une version binaire de .net core.</span><span class="sxs-lookup"><span data-stu-id="9b2d8-119">To extract the SDK and make the commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="9b2d8-120">Ensuite, ouvrez un terminal et exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="9b2d8-120">Then, open a terminal and run the following commands.</span></span>

```bash
mkdir -p $HOME/dotnet && tar zxf dotnet-sdk-3.1.101-linux-musl-x64.tar.gz -C $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> <span data-ttu-id="9b2d8-121">Les commandes ci-dessus rendent uniquement disponibles les commandes du kit de développement logiciel (SDK) .NET pour la session Terminal dans laquelle elles ont été exécutées.</span><span class="sxs-lookup"><span data-stu-id="9b2d8-121">The above commands will only make the .NET SDK commands available for the terminal session in which it was run.</span></span>
>
> <span data-ttu-id="9b2d8-122">Vous pouvez modifier votre profil de Shell pour ajouter définitivement les commandes.</span><span class="sxs-lookup"><span data-stu-id="9b2d8-122">You can edit your shell profile to permanently add the commands.</span></span> <span data-ttu-id="9b2d8-123">Un certain nombre de shells différents sont disponibles pour Linux et chacun d’eux a un profil différent.</span><span class="sxs-lookup"><span data-stu-id="9b2d8-123">There are a number of different shells available for Linux and each has a different profile.</span></span> <span data-ttu-id="9b2d8-124">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="9b2d8-124">For example:</span></span>
>
> - <span data-ttu-id="9b2d8-125">**Interpréteur**de commandes bash : *~/. bash_profile*, *~ fichier/.bashrc*</span><span class="sxs-lookup"><span data-stu-id="9b2d8-125">**Bash Shell**: *~/.bash_profile*, *~/.bashrc*</span></span>
> - <span data-ttu-id="9b2d8-126">**Shell Korn**: *~/.kshrc* ou *. Profile*</span><span class="sxs-lookup"><span data-stu-id="9b2d8-126">**Korn Shell**: *~/.kshrc* or *.profile*</span></span>
> - <span data-ttu-id="9b2d8-127">**Z Shell**: *~/.zshrc* ou *. zprofile*</span><span class="sxs-lookup"><span data-stu-id="9b2d8-127">**Z Shell**: *~/.zshrc* or *.zprofile*</span></span>
> 
> <span data-ttu-id="9b2d8-128">Modifiez le fichier source approprié pour votre shell et ajoutez `:$HOME/dotnet` à la fin de l’instruction `PATH` existante.</span><span class="sxs-lookup"><span data-stu-id="9b2d8-128">Edit the appropriate source file for your shell and add `:$HOME/dotnet` to the end of the existing `PATH` statement.</span></span> <span data-ttu-id="9b2d8-129">Si aucune instruction `PATH` n’est incluse, ajoutez une nouvelle ligne avec `export PATH=$PATH:$HOME/dotnet`.</span><span class="sxs-lookup"><span data-stu-id="9b2d8-129">If no `PATH` statement is included, add a new line with `export PATH=$PATH:$HOME/dotnet`.</span></span>
>
> <span data-ttu-id="9b2d8-130">En outre, ajoutez `export DOTNET_ROOT=$HOME/dotnet` à la fin du fichier.</span><span class="sxs-lookup"><span data-stu-id="9b2d8-130">Also, add `export DOTNET_ROOT=$HOME/dotnet` to the end of the file.</span></span>

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-visual-studio"></a><span data-ttu-id="9b2d8-131">Installer avec Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9b2d8-131">Install with Visual Studio</span></span>

<span data-ttu-id="9b2d8-132">Si vous utilisez Visual Studio pour développer des applications .NET Core, le tableau suivant décrit la version minimale requise de Visual Studio en fonction de la version de kit SDK .NET Core cible.</span><span class="sxs-lookup"><span data-stu-id="9b2d8-132">If you're using Visual Studio to develop .NET Core apps, the following table describes the minimum required version of Visual Studio based on the target .NET Core SDK version.</span></span>

| <span data-ttu-id="9b2d8-133">Version de kit SDK .NET Core</span><span class="sxs-lookup"><span data-stu-id="9b2d8-133">.NET Core SDK version</span></span> | <span data-ttu-id="9b2d8-134">Version de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9b2d8-134">Visual Studio version</span></span>                      |
| --------------------- | ------------------------------------------ |
| <span data-ttu-id="9b2d8-135">3.1</span><span class="sxs-lookup"><span data-stu-id="9b2d8-135">3.1</span></span>                   | <span data-ttu-id="9b2d8-136">Visual Studio 2019 version 16,4 ou ultérieure.</span><span class="sxs-lookup"><span data-stu-id="9b2d8-136">Visual Studio 2019 version 16.4 or higher.</span></span> |
| <span data-ttu-id="9b2d8-137">3.0</span><span class="sxs-lookup"><span data-stu-id="9b2d8-137">3.0</span></span>                   | <span data-ttu-id="9b2d8-138">Visual Studio 2019 version 16,3 ou ultérieure.</span><span class="sxs-lookup"><span data-stu-id="9b2d8-138">Visual Studio 2019 version 16.3 or higher.</span></span> |
| <span data-ttu-id="9b2d8-139">2.2</span><span class="sxs-lookup"><span data-stu-id="9b2d8-139">2.2</span></span>                   | <span data-ttu-id="9b2d8-140">Visual Studio 2017 version 15,9 ou ultérieure.</span><span class="sxs-lookup"><span data-stu-id="9b2d8-140">Visual Studio 2017 version 15.9 or higher.</span></span> |
| <span data-ttu-id="9b2d8-141">2.1</span><span class="sxs-lookup"><span data-stu-id="9b2d8-141">2.1</span></span>                   | <span data-ttu-id="9b2d8-142">Visual Studio 2017 version 15,7 ou ultérieure.</span><span class="sxs-lookup"><span data-stu-id="9b2d8-142">Visual Studio 2017 version 15.7 or higher.</span></span> |

<span data-ttu-id="9b2d8-143">Si vous avez déjà installé Visual Studio, vous pouvez vérifier votre version en procédant comme suit.</span><span class="sxs-lookup"><span data-stu-id="9b2d8-143">If you already have Visual Studio installed, you can check your version with the following steps.</span></span>

01. <span data-ttu-id="9b2d8-144">Ouvrez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9b2d8-144">Open Visual Studio.</span></span>
01. <span data-ttu-id="9b2d8-145">Sélectionnez **aide** > **à propos de Microsoft Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="9b2d8-145">Select **Help** > **About Microsoft Visual Studio**.</span></span>
01. <span data-ttu-id="9b2d8-146">Lisez le numéro de version dans la boîte de dialogue **à propos** de.</span><span class="sxs-lookup"><span data-stu-id="9b2d8-146">Read the version number from the **About** dialog.</span></span>

<span data-ttu-id="9b2d8-147">Visual Studio peut installer les kit SDK .NET Core et Runtime les plus récents.</span><span class="sxs-lookup"><span data-stu-id="9b2d8-147">Visual Studio can install the latest .NET Core SDK and runtime.</span></span>

- <span data-ttu-id="9b2d8-148">[Téléchargez Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span><span class="sxs-lookup"><span data-stu-id="9b2d8-148">[Download Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span></span>

### <a name="select-a-workload"></a><span data-ttu-id="9b2d8-149">Sélectionner une charge de travail</span><span class="sxs-lookup"><span data-stu-id="9b2d8-149">Select a workload</span></span>

<span data-ttu-id="9b2d8-150">Lors de l’installation ou de la modification de Visual Studio, sélectionnez l’une des charges de travail suivantes, selon le type d’application que vous créez :</span><span class="sxs-lookup"><span data-stu-id="9b2d8-150">When installing or modifying Visual Studio, select one of the following workloads, depending on the kind of application you're building:</span></span>

- <span data-ttu-id="9b2d8-151">La charge de travail **développement multiplateforme .net Core** dans la section **autres ensembles d’outils** .</span><span class="sxs-lookup"><span data-stu-id="9b2d8-151">The **.NET Core cross-platform development** workload in the **Other Toolsets** section.</span></span>
- <span data-ttu-id="9b2d8-152">La charge de travail **ASP.net et développement Web** dans la section **Web & Cloud** .</span><span class="sxs-lookup"><span data-stu-id="9b2d8-152">The **ASP.NET and web development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="9b2d8-153">La charge de travail **développement Azure** dans la section **Web & Cloud** .</span><span class="sxs-lookup"><span data-stu-id="9b2d8-153">The **Azure development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="9b2d8-154">La charge de travail **développement .net Desktop** dans la section **Desktop & mobile** .</span><span class="sxs-lookup"><span data-stu-id="9b2d8-154">The **.NET desktop development** workload in the **Desktop & Mobile** section.</span></span>

<span data-ttu-id="9b2d8-155">[![Windows Visual Studio 2019 avec charge de travail .NET Core](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="9b2d8-155">[![Windows Visual Studio 2019 with .NET Core workload](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span></span>

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-visual-studio-for-mac"></a><span data-ttu-id="9b2d8-156">Installer avec Visual Studio pour Mac</span><span class="sxs-lookup"><span data-stu-id="9b2d8-156">Install with Visual Studio for Mac</span></span>

<span data-ttu-id="9b2d8-157">Visual Studio pour Mac installe le kit SDK .NET Core lorsque la charge de travail **.net Core** est sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="9b2d8-157">Visual Studio for Mac installs the .NET Core SDK when the **.NET Core** workload is selected.</span></span> <span data-ttu-id="9b2d8-158">Pour commencer à utiliser le développement .NET Core sur macOS, consultez [installer Visual Studio 2019 pour Mac](/visualstudio/mac/installation).</span><span class="sxs-lookup"><span data-stu-id="9b2d8-158">To get started with .NET Core development on macOS, see [Install Visual Studio 2019 for Mac](/visualstudio/mac/installation).</span></span> <span data-ttu-id="9b2d8-159">Pour la version la plus récente, .NET Core 3,1, vous devez utiliser le Visual Studio pour Mac 8,4 preview.</span><span class="sxs-lookup"><span data-stu-id="9b2d8-159">For the latest release, .NET Core 3.1, you must use the Visual Studio for Mac 8.4 Preview.</span></span>

<span data-ttu-id="9b2d8-160">[![la fonctionnalité de charge de travail de Visual Studio 2019 pour Mac macOS avec .NET Core](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="9b2d8-160">[![macOS Visual Studio 2019 for Mac with .NET Core workload feature](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span></span>

::: zone-end

## <a name="install-alongside-visual-studio-code"></a><span data-ttu-id="9b2d8-161">Installer en même temps que Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="9b2d8-161">Install alongside Visual Studio Code</span></span>

<span data-ttu-id="9b2d8-162">Visual Studio Code est un éditeur de code source puissant et léger qui s’exécute sur votre bureau.</span><span class="sxs-lookup"><span data-stu-id="9b2d8-162">Visual Studio Code is a powerful and lightweight source code editor that runs on your desktop.</span></span> <span data-ttu-id="9b2d8-163">Visual Studio Code est disponible pour Windows, macOS et Linux.</span><span class="sxs-lookup"><span data-stu-id="9b2d8-163">Visual Studio Code is available for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="9b2d8-164">Même si Visual Studio Code n’est pas fourni avec un programme d’installation automatisé de .NET Core, comme Visual Studio, l’ajout de la prise en charge de .NET Core est simple.</span><span class="sxs-lookup"><span data-stu-id="9b2d8-164">While Visual Studio Code doesn't come with an automated .NET Core installer like Visual Studio does, adding .NET Core support is simple.</span></span>

01. <span data-ttu-id="9b2d8-165">[Téléchargez et installez Visual Studio code](https://code.visualstudio.com/Download).</span><span class="sxs-lookup"><span data-stu-id="9b2d8-165">[Download and install Visual Studio Code](https://code.visualstudio.com/Download).</span></span>
01. <span data-ttu-id="9b2d8-166">[Téléchargez et installez le kit SDK .net Core](https://dotnet.microsoft.com/download/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="9b2d8-166">[Download and install the .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core).</span></span>
01. <span data-ttu-id="9b2d8-167">[Installez l' C# extension à partir de la place de marché Visual Studio code](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp).</span><span class="sxs-lookup"><span data-stu-id="9b2d8-167">[Install the C# extension from the Visual Studio Code marketplace](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp).</span></span>

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a><span data-ttu-id="9b2d8-168">Installer avec l’automatisation PowerShell</span><span class="sxs-lookup"><span data-stu-id="9b2d8-168">Install with PowerShell automation</span></span>

<span data-ttu-id="9b2d8-169">Les [scripts dotnet-install](../tools/dotnet-install-script.md) sont utilisés pour l’automatisation et les installations non administratives du kit de développement logiciel (SDK).</span><span class="sxs-lookup"><span data-stu-id="9b2d8-169">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the SDK.</span></span> <span data-ttu-id="9b2d8-170">Vous pouvez télécharger le script à partir de la [page de référence du script dotnet-install](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="9b2d8-170">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="9b2d8-171">Par défaut, le script installe la dernière version de [support à long terme (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , qui est .net Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="9b2d8-171">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 2.1.</span></span> <span data-ttu-id="9b2d8-172">Pour installer la version actuelle de .NET Core, exécutez le script avec le commutateur suivant.</span><span class="sxs-lookup"><span data-stu-id="9b2d8-172">To install the current release of .NET Core, run the script with the following switch.</span></span>

```powershell
dotnet-install.ps1 -Channel Current
```

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a><span data-ttu-id="9b2d8-173">Installer avec l’automatisation bash</span><span class="sxs-lookup"><span data-stu-id="9b2d8-173">Install with bash automation</span></span>

<span data-ttu-id="9b2d8-174">Les [scripts dotnet-install](../tools/dotnet-install-script.md) sont utilisés pour l’automatisation et les installations non administratives du kit de développement logiciel (SDK).</span><span class="sxs-lookup"><span data-stu-id="9b2d8-174">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the SDK.</span></span> <span data-ttu-id="9b2d8-175">Vous pouvez télécharger le script à partir de la [page de référence du script dotnet-install](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="9b2d8-175">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="9b2d8-176">Par défaut, le script installe la dernière version de [support à long terme (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , qui est .net Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="9b2d8-176">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 2.1.</span></span> <span data-ttu-id="9b2d8-177">Pour installer la version actuelle de .NET Core, exécutez le script avec le commutateur suivant.</span><span class="sxs-lookup"><span data-stu-id="9b2d8-177">To install the current release of .NET Core, run the script with the following switch.</span></span>

```bash
./dotnet-install.sh -c Current
```

::: zone-end

## <a name="all-net-core-downloads"></a><span data-ttu-id="9b2d8-178">Tous les téléchargements .NET Core</span><span class="sxs-lookup"><span data-stu-id="9b2d8-178">All .NET Core downloads</span></span>

<span data-ttu-id="9b2d8-179">Vous pouvez télécharger et installer .NET Core directement avec l’un des liens suivants :</span><span class="sxs-lookup"><span data-stu-id="9b2d8-179">You can download and install .NET Core directly with one of the following links:</span></span>

- [<span data-ttu-id="9b2d8-180">Téléchargements .NET Core 3,1 preview</span><span class="sxs-lookup"><span data-stu-id="9b2d8-180">.NET Core 3.1 Preview downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="9b2d8-181">Téléchargements .NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="9b2d8-181">.NET Core 3.0 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- [<span data-ttu-id="9b2d8-182">Téléchargements .NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="9b2d8-182">.NET Core 2.2 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- [<span data-ttu-id="9b2d8-183">Téléchargements .NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="9b2d8-183">.NET Core 2.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a><span data-ttu-id="9b2d8-184">Docker</span><span class="sxs-lookup"><span data-stu-id="9b2d8-184">Docker</span></span>

<span data-ttu-id="9b2d8-185">Les conteneurs offrent un moyen léger d’isoler votre application du reste du système hôte.</span><span class="sxs-lookup"><span data-stu-id="9b2d8-185">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="9b2d8-186">Les conteneurs sur le même ordinateur partagent simplement le noyau et utilisent les ressources fournies à votre application.</span><span class="sxs-lookup"><span data-stu-id="9b2d8-186">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="9b2d8-187">.NET Core peut s’exécuter dans un conteneur d’ancrage.</span><span class="sxs-lookup"><span data-stu-id="9b2d8-187">.NET Core can run in a Docker container.</span></span> <span data-ttu-id="9b2d8-188">Les images Docker .NET Core officielles sont publiées dans Microsoft Container Registry (MCR) et détectables dans le [référentiel Docker Hub Microsoft .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/).</span><span class="sxs-lookup"><span data-stu-id="9b2d8-188">Official .NET Core Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span> <span data-ttu-id="9b2d8-189">Chaque référentiel contient des images pour différentes combinaisons possibles de .NET (kit de développement logiciel ou runtime) et du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="9b2d8-189">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="9b2d8-190">Microsoft fournit des images adaptées à des scénarios particuliers.</span><span class="sxs-lookup"><span data-stu-id="9b2d8-190">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="9b2d8-191">Par exemple, celles du [référentiel ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) sont conçues pour exécuter des applications ASP.NET Core en production.</span><span class="sxs-lookup"><span data-stu-id="9b2d8-191">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="9b2d8-192">Pour plus d’informations sur l’utilisation de .NET Core dans un conteneur d’ancrage, consultez [Introduction à .net et à l’ancreur](../docker/introduction.md) et aux [exemples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span><span class="sxs-lookup"><span data-stu-id="9b2d8-192">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="9b2d8-193">Étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="9b2d8-193">Next steps</span></span>

::: zone pivot="os-windows"

- <span data-ttu-id="9b2d8-194">[Didacticiel : C# Hello World didacticiel](../tutorials/with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="9b2d8-194">[Tutorial: C# Hello World tutorial](../tutorials/with-visual-studio.md).</span></span>
- <span data-ttu-id="9b2d8-195">[Didacticiel : Visual Basic Hello World didacticiel](../tutorials/vb-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="9b2d8-195">[Tutorial: Visual Basic Hello World tutorial](../tutorials/vb-with-visual-studio.md).</span></span>
- <span data-ttu-id="9b2d8-196">[Didacticiel : créer une application avec Visual Studio code](../tutorials/with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="9b2d8-196">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="9b2d8-197">[Didacticiel : conteneur d’une application .net Core](../docker/build-container.md).</span><span class="sxs-lookup"><span data-stu-id="9b2d8-197">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end

::: zone pivot="os-macos"

- <span data-ttu-id="9b2d8-198">[Didacticiel : prise en main de MacOS](../tutorials/using-on-mac-vs.md).</span><span class="sxs-lookup"><span data-stu-id="9b2d8-198">[Tutorial: Get started on macOS](../tutorials/using-on-mac-vs.md).</span></span>
- <span data-ttu-id="9b2d8-199">[Didacticiel : créer une application avec Visual Studio code](../tutorials/with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="9b2d8-199">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="9b2d8-200">[Didacticiel : conteneur d’une application .net Core](../docker/build-container.md).</span><span class="sxs-lookup"><span data-stu-id="9b2d8-200">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end

::: zone pivot="os-linux"

- <span data-ttu-id="9b2d8-201">[Didacticiel : créer une application avec Visual Studio code](../tutorials/with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="9b2d8-201">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="9b2d8-202">[Didacticiel : conteneur d’une application .net Core](../docker/build-container.md).</span><span class="sxs-lookup"><span data-stu-id="9b2d8-202">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end
