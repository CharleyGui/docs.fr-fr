---
title: Installer kit SDK .NET Core sur Windows, Linux et macOS-.NET Core
description: Découvrez comment installer .NET Core sur Windows, Linux et macOS. Découvrez les dépendances requises pour développer des applications .NET Core.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 004ef2a768f4a5415942d405e4a8292928c89f94
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75340655"
---
# <a name="install-the-net-core-sdk"></a><span data-ttu-id="1516e-104">Installer le kit SDK .NET Core</span><span class="sxs-lookup"><span data-stu-id="1516e-104">Install the .NET Core SDK</span></span>

<span data-ttu-id="1516e-105">Dans cet article, vous allez apprendre à installer le kit SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1516e-105">In this article, you'll learn how to install the .NET Core SDK.</span></span> <span data-ttu-id="1516e-106">Le kit SDK .NET Core est utilisé pour créer des applications et des bibliothèques .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1516e-106">The .NET Core SDK is used to create .NET Core apps and libraries.</span></span> <span data-ttu-id="1516e-107">Le Runtime .NET Core est toujours installé avec le kit de développement logiciel (SDK).</span><span class="sxs-lookup"><span data-stu-id="1516e-107">The .NET Core runtime is always installed with the SDK.</span></span>

::: zone pivot="os-windows"

## <a name="install-with-an-installer"></a><span data-ttu-id="1516e-108">Installer avec un programme d’installation</span><span class="sxs-lookup"><span data-stu-id="1516e-108">Install with an installer</span></span>

<span data-ttu-id="1516e-109">Windows possède des programmes d’installation autonomes qui peuvent être utilisés pour installer le kit de développement logiciel (SDK) .NET Core 3,1 :</span><span class="sxs-lookup"><span data-stu-id="1516e-109">Windows has standalone installers that can be used to install the .NET Core 3.1 SDK:</span></span>

- [<span data-ttu-id="1516e-110">Processeurs x64 (64 bits)</span><span class="sxs-lookup"><span data-stu-id="1516e-110">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="1516e-111">Processeurs x86 (32 bits)</span><span class="sxs-lookup"><span data-stu-id="1516e-111">x86 (32-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-an-installer"></a><span data-ttu-id="1516e-112">Installer avec un programme d’installation</span><span class="sxs-lookup"><span data-stu-id="1516e-112">Install with an installer</span></span>

<span data-ttu-id="1516e-113">macOS possède des programmes d’installation autonomes qui peuvent être utilisés pour installer le kit de développement logiciel (SDK) .NET Core 3,1 :</span><span class="sxs-lookup"><span data-stu-id="1516e-113">macOS has standalone installers that can be used to install the .NET Core 3.1 SDK:</span></span>

- [<span data-ttu-id="1516e-114">Processeurs x64 (64 bits)</span><span class="sxs-lookup"><span data-stu-id="1516e-114">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a><span data-ttu-id="1516e-115">Installer avec un gestionnaire de package</span><span class="sxs-lookup"><span data-stu-id="1516e-115">Install with a package manager</span></span>

<span data-ttu-id="1516e-116">Vous pouvez installer les kit SDK .NET Core avec un grand nombre de gestionnaires de packages Linux courants.</span><span class="sxs-lookup"><span data-stu-id="1516e-116">You can install the .NET Core SDK with many of the common Linux package managers.</span></span> <span data-ttu-id="1516e-117">Pour plus d’informations, consultez [Linux Package Manager-install .net Core](linux-package-managers.md).</span><span class="sxs-lookup"><span data-stu-id="1516e-117">For more information, see [Linux Package Manager - Install .NET Core](linux-package-managers.md).</span></span>

<span data-ttu-id="1516e-118">L’installation de avec un gestionnaire de package est uniquement prise en charge sur l’architecture x64.</span><span class="sxs-lookup"><span data-stu-id="1516e-118">Installing with a package manager is only supported on the x64 architecture.</span></span> <span data-ttu-id="1516e-119">Si vous installez le kit SDK .NET Core avec une architecture différente, par exemple ARM, suivez les instructions de [téléchargement et d’installation manuelle](#download-and-manually-install) ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="1516e-119">If you're installing the .NET Core SDK with a different architecture, such as ARM, follow the [Download and manually install](#download-and-manually-install) instructions below.</span></span> <span data-ttu-id="1516e-120">Pour plus d’informations sur les architectures prises en charge, consultez [.net Core Dependencies and Requirements](dependencies.md).</span><span class="sxs-lookup"><span data-stu-id="1516e-120">For more information about what architectures are supported, see [.NET Core dependencies and requirements](dependencies.md).</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="1516e-121">Télécharger et installer manuellement</span><span class="sxs-lookup"><span data-stu-id="1516e-121">Download and manually install</span></span>

<span data-ttu-id="1516e-122">Pour extraire le kit de développement logiciel (SDK) et rendre les commandes de CLI .NET Core disponibles sur le terminal, commencez par [Télécharger](#all-net-core-downloads) une version binaire de .net core.</span><span class="sxs-lookup"><span data-stu-id="1516e-122">To extract the SDK and make the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="1516e-123">Ensuite, ouvrez un terminal et exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="1516e-123">Then, open a terminal and run the following commands.</span></span>

```bash
mkdir -p $HOME/dotnet && tar zxf dotnet-sdk-3.1.100-linux-x64.tar.gz -C $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> <span data-ttu-id="1516e-124">Les commandes `export` précédentes rendent uniquement les commandes CLI .NET Core disponibles pour la session Terminal dans laquelle elles ont été exécutées.</span><span class="sxs-lookup"><span data-stu-id="1516e-124">The preceding `export` commands only make the .NET Core CLI commands available for the terminal session in which it was run.</span></span>
>
> <span data-ttu-id="1516e-125">Vous pouvez modifier votre profil de Shell pour ajouter définitivement les commandes.</span><span class="sxs-lookup"><span data-stu-id="1516e-125">You can edit your shell profile to permanently add the commands.</span></span> <span data-ttu-id="1516e-126">Un certain nombre de shells différents sont disponibles pour Linux et chacun d’eux a un profil différent.</span><span class="sxs-lookup"><span data-stu-id="1516e-126">There are a number of different shells available for Linux and each has a different profile.</span></span> <span data-ttu-id="1516e-127">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="1516e-127">For example:</span></span>
>
> - <span data-ttu-id="1516e-128">**Interpréteur**de commandes bash : *~/. bash_profile*, *~ fichier/.bashrc*</span><span class="sxs-lookup"><span data-stu-id="1516e-128">**Bash Shell**: *~/.bash_profile*, *~/.bashrc*</span></span>
> - <span data-ttu-id="1516e-129">**Shell Korn**: *~/.kshrc* ou *. Profile*</span><span class="sxs-lookup"><span data-stu-id="1516e-129">**Korn Shell**: *~/.kshrc* or *.profile*</span></span>
> - <span data-ttu-id="1516e-130">**Z Shell**: *~/.zshrc* ou *. zprofile*</span><span class="sxs-lookup"><span data-stu-id="1516e-130">**Z Shell**: *~/.zshrc* or *.zprofile*</span></span>
>
> <span data-ttu-id="1516e-131">Modifiez le fichier source approprié pour votre shell et ajoutez `:$HOME/dotnet` à la fin de l’instruction `PATH` existante.</span><span class="sxs-lookup"><span data-stu-id="1516e-131">Edit the appropriate source file for your shell and add `:$HOME/dotnet` to the end of the existing `PATH` statement.</span></span> <span data-ttu-id="1516e-132">Si aucune instruction `PATH` n’est incluse, ajoutez une nouvelle ligne avec `export PATH=$PATH:$HOME/dotnet`.</span><span class="sxs-lookup"><span data-stu-id="1516e-132">If no `PATH` statement is included, add a new line with `export PATH=$PATH:$HOME/dotnet`.</span></span>
>
> <span data-ttu-id="1516e-133">En outre, ajoutez `export DOTNET_ROOT=$HOME/dotnet` à la fin du fichier.</span><span class="sxs-lookup"><span data-stu-id="1516e-133">Also, add `export DOTNET_ROOT=$HOME/dotnet` to the end of the file.</span></span>

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-visual-studio"></a><span data-ttu-id="1516e-134">Installer avec Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1516e-134">Install with Visual Studio</span></span>

<span data-ttu-id="1516e-135">Si vous utilisez Visual Studio pour développer des applications .NET Core, le tableau suivant décrit la version minimale requise de Visual Studio en fonction de la version de kit SDK .NET Core cible.</span><span class="sxs-lookup"><span data-stu-id="1516e-135">If you're using Visual Studio to develop .NET Core apps, the following table describes the minimum required version of Visual Studio based on the target .NET Core SDK version.</span></span>

| <span data-ttu-id="1516e-136">Version de kit SDK .NET Core</span><span class="sxs-lookup"><span data-stu-id="1516e-136">.NET Core SDK version</span></span> | <span data-ttu-id="1516e-137">Version de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1516e-137">Visual Studio version</span></span>                      |
| --------------------- | ------------------------------------------ |
| <span data-ttu-id="1516e-138">3.1</span><span class="sxs-lookup"><span data-stu-id="1516e-138">3.1</span></span>                   | <span data-ttu-id="1516e-139">Visual Studio 2019 version 16,4 ou ultérieure.</span><span class="sxs-lookup"><span data-stu-id="1516e-139">Visual Studio 2019 version 16.4 or higher.</span></span> |
| <span data-ttu-id="1516e-140">3.0</span><span class="sxs-lookup"><span data-stu-id="1516e-140">3.0</span></span>                   | <span data-ttu-id="1516e-141">Visual Studio 2019 version 16,3 ou ultérieure.</span><span class="sxs-lookup"><span data-stu-id="1516e-141">Visual Studio 2019 version 16.3 or higher.</span></span> |
| <span data-ttu-id="1516e-142">2.2</span><span class="sxs-lookup"><span data-stu-id="1516e-142">2.2</span></span>                   | <span data-ttu-id="1516e-143">Visual Studio 2017 version 15,9 ou ultérieure.</span><span class="sxs-lookup"><span data-stu-id="1516e-143">Visual Studio 2017 version 15.9 or higher.</span></span> |
| <span data-ttu-id="1516e-144">2.1</span><span class="sxs-lookup"><span data-stu-id="1516e-144">2.1</span></span>                   | <span data-ttu-id="1516e-145">Visual Studio 2017 version 15,7 ou ultérieure.</span><span class="sxs-lookup"><span data-stu-id="1516e-145">Visual Studio 2017 version 15.7 or higher.</span></span> |

<span data-ttu-id="1516e-146">Si vous avez déjà installé Visual Studio, vous pouvez vérifier votre version en procédant comme suit.</span><span class="sxs-lookup"><span data-stu-id="1516e-146">If you already have Visual Studio installed, you can check your version with the following steps.</span></span>

01. <span data-ttu-id="1516e-147">Ouvrez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1516e-147">Open Visual Studio.</span></span>
01. <span data-ttu-id="1516e-148">Sélectionnez **aide** > **à propos de Microsoft Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="1516e-148">Select **Help** > **About Microsoft Visual Studio**.</span></span>
01. <span data-ttu-id="1516e-149">Lisez le numéro de version dans la boîte de dialogue **à propos** de.</span><span class="sxs-lookup"><span data-stu-id="1516e-149">Read the version number from the **About** dialog.</span></span>

<span data-ttu-id="1516e-150">Visual Studio peut installer les kit SDK .NET Core et Runtime les plus récents.</span><span class="sxs-lookup"><span data-stu-id="1516e-150">Visual Studio can install the latest .NET Core SDK and runtime.</span></span>

- <span data-ttu-id="1516e-151">[Téléchargez Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span><span class="sxs-lookup"><span data-stu-id="1516e-151">[Download Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span></span>

### <a name="select-a-workload"></a><span data-ttu-id="1516e-152">Sélectionner une charge de travail</span><span class="sxs-lookup"><span data-stu-id="1516e-152">Select a workload</span></span>

<span data-ttu-id="1516e-153">Lors de l’installation ou de la modification de Visual Studio, sélectionnez l’une des charges de travail suivantes, selon le type d’application que vous créez :</span><span class="sxs-lookup"><span data-stu-id="1516e-153">When installing or modifying Visual Studio, select one of the following workloads, depending on the kind of application you're building:</span></span>

- <span data-ttu-id="1516e-154">La charge de travail **développement multiplateforme .net Core** dans la section **autres ensembles d’outils** .</span><span class="sxs-lookup"><span data-stu-id="1516e-154">The **.NET Core cross-platform development** workload in the **Other Toolsets** section.</span></span>
- <span data-ttu-id="1516e-155">La charge de travail **ASP.net et développement Web** dans la section **Web & Cloud** .</span><span class="sxs-lookup"><span data-stu-id="1516e-155">The **ASP.NET and web development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="1516e-156">La charge de travail **développement Azure** dans la section **Web & Cloud** .</span><span class="sxs-lookup"><span data-stu-id="1516e-156">The **Azure development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="1516e-157">La charge de travail **développement .net Desktop** dans la section **Desktop & mobile** .</span><span class="sxs-lookup"><span data-stu-id="1516e-157">The **.NET desktop development** workload in the **Desktop & Mobile** section.</span></span>

<span data-ttu-id="1516e-158">[![Windows Visual Studio 2019 avec charge de travail .NET Core](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="1516e-158">[![Windows Visual Studio 2019 with .NET Core workload](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span></span>

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-visual-studio-for-mac"></a><span data-ttu-id="1516e-159">Installer avec Visual Studio pour Mac</span><span class="sxs-lookup"><span data-stu-id="1516e-159">Install with Visual Studio for Mac</span></span>

<span data-ttu-id="1516e-160">Visual Studio pour Mac installe le kit SDK .NET Core lorsque la charge de travail **.net Core** est sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="1516e-160">Visual Studio for Mac installs the .NET Core SDK when the **.NET Core** workload is selected.</span></span> <span data-ttu-id="1516e-161">Pour commencer à utiliser le développement .NET Core sur macOS, consultez [installer Visual Studio 2019 pour Mac](/visualstudio/mac/installation).</span><span class="sxs-lookup"><span data-stu-id="1516e-161">To get started with .NET Core development on macOS, see [Install Visual Studio 2019 for Mac](/visualstudio/mac/installation).</span></span> <span data-ttu-id="1516e-162">Pour la version la plus récente, .NET Core 3,1, vous devez utiliser le Visual Studio pour Mac 8,4 preview.</span><span class="sxs-lookup"><span data-stu-id="1516e-162">For the latest release, .NET Core 3.1, you must use the Visual Studio for Mac 8.4 Preview.</span></span>

<span data-ttu-id="1516e-163">[![la fonctionnalité de charge de travail de Visual Studio 2019 pour Mac macOS avec .NET Core](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="1516e-163">[![macOS Visual Studio 2019 for Mac with .NET Core workload feature](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span></span>

::: zone-end

## <a name="install-alongside-visual-studio-code"></a><span data-ttu-id="1516e-164">Installer en même temps que Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="1516e-164">Install alongside Visual Studio Code</span></span>

<span data-ttu-id="1516e-165">Visual Studio Code est un éditeur de code source puissant et léger qui s’exécute sur votre bureau.</span><span class="sxs-lookup"><span data-stu-id="1516e-165">Visual Studio Code is a powerful and lightweight source code editor that runs on your desktop.</span></span> <span data-ttu-id="1516e-166">Visual Studio Code est disponible pour Windows, macOS et Linux.</span><span class="sxs-lookup"><span data-stu-id="1516e-166">Visual Studio Code is available for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="1516e-167">Même si Visual Studio Code n’est pas fourni avec un programme d’installation automatisé de .NET Core, comme Visual Studio, l’ajout de la prise en charge de .NET Core est simple.</span><span class="sxs-lookup"><span data-stu-id="1516e-167">While Visual Studio Code doesn't come with an automated .NET Core installer like Visual Studio does, adding .NET Core support is simple.</span></span>

01. <span data-ttu-id="1516e-168">[Téléchargez et installez Visual Studio code](https://code.visualstudio.com/Download).</span><span class="sxs-lookup"><span data-stu-id="1516e-168">[Download and install Visual Studio Code](https://code.visualstudio.com/Download).</span></span>
01. <span data-ttu-id="1516e-169">[Téléchargez et installez le kit SDK .net Core](https://dotnet.microsoft.com/download/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="1516e-169">[Download and install the .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core).</span></span>
01. <span data-ttu-id="1516e-170">[Installez l' C# extension à partir de la place de marché Visual Studio code](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp).</span><span class="sxs-lookup"><span data-stu-id="1516e-170">[Install the C# extension from the Visual Studio Code marketplace](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp).</span></span>

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a><span data-ttu-id="1516e-171">Installer avec l’automatisation PowerShell</span><span class="sxs-lookup"><span data-stu-id="1516e-171">Install with PowerShell automation</span></span>

<span data-ttu-id="1516e-172">Les [scripts dotnet-install](../tools/dotnet-install-script.md) sont utilisés pour l’automatisation et les installations non administratives du kit de développement logiciel (SDK).</span><span class="sxs-lookup"><span data-stu-id="1516e-172">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the SDK.</span></span> <span data-ttu-id="1516e-173">Vous pouvez télécharger le script à partir de la [page de référence du script dotnet-install](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="1516e-173">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="1516e-174">Par défaut, le script installe la dernière version de [support à long terme (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , qui est .net Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="1516e-174">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 2.1.</span></span> <span data-ttu-id="1516e-175">Pour installer la version actuelle de .NET Core, exécutez le script avec le commutateur suivant.</span><span class="sxs-lookup"><span data-stu-id="1516e-175">To install the current release of .NET Core, run the script with the following switch.</span></span>

```powershell
dotnet-install.ps1 -Channel Current
```

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a><span data-ttu-id="1516e-176">Installer avec l’automatisation bash</span><span class="sxs-lookup"><span data-stu-id="1516e-176">Install with bash automation</span></span>

<span data-ttu-id="1516e-177">Les [scripts dotnet-install](../tools/dotnet-install-script.md) sont utilisés pour l’automatisation et les installations non administratives du kit de développement logiciel (SDK).</span><span class="sxs-lookup"><span data-stu-id="1516e-177">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the SDK.</span></span> <span data-ttu-id="1516e-178">Vous pouvez télécharger le script à partir de la [page de référence du script dotnet-install](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="1516e-178">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="1516e-179">Par défaut, le script installe la dernière version de [support à long terme (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , qui est .net Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="1516e-179">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 2.1.</span></span> <span data-ttu-id="1516e-180">Pour installer la version actuelle de .NET Core, exécutez le script avec le commutateur suivant.</span><span class="sxs-lookup"><span data-stu-id="1516e-180">To install the current release of .NET Core, run the script with the following switch.</span></span>

```bash
./dotnet-install.sh -c Current
```

::: zone-end

## <a name="all-net-core-downloads"></a><span data-ttu-id="1516e-181">Tous les téléchargements .NET Core</span><span class="sxs-lookup"><span data-stu-id="1516e-181">All .NET Core downloads</span></span>

<span data-ttu-id="1516e-182">Vous pouvez télécharger et installer .NET Core directement avec l’un des liens suivants :</span><span class="sxs-lookup"><span data-stu-id="1516e-182">You can download and install .NET Core directly with one of the following links:</span></span>

- [<span data-ttu-id="1516e-183">Téléchargements .NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="1516e-183">.NET Core 3.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="1516e-184">Téléchargements .NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="1516e-184">.NET Core 3.0 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- [<span data-ttu-id="1516e-185">Téléchargements .NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="1516e-185">.NET Core 2.2 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- [<span data-ttu-id="1516e-186">Téléchargements .NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="1516e-186">.NET Core 2.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a><span data-ttu-id="1516e-187">Docker</span><span class="sxs-lookup"><span data-stu-id="1516e-187">Docker</span></span>

<span data-ttu-id="1516e-188">Les conteneurs offrent un moyen léger d’isoler votre application du reste du système hôte.</span><span class="sxs-lookup"><span data-stu-id="1516e-188">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="1516e-189">Les conteneurs sur le même ordinateur partagent simplement le noyau et utilisent les ressources fournies à votre application.</span><span class="sxs-lookup"><span data-stu-id="1516e-189">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="1516e-190">.NET Core peut s’exécuter dans un conteneur d’ancrage.</span><span class="sxs-lookup"><span data-stu-id="1516e-190">.NET Core can run in a Docker container.</span></span> <span data-ttu-id="1516e-191">Les images Docker .NET Core officielles sont publiées dans Microsoft Container Registry (MCR) et détectables dans le [référentiel Docker Hub Microsoft .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/).</span><span class="sxs-lookup"><span data-stu-id="1516e-191">Official .NET Core Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span> <span data-ttu-id="1516e-192">Chaque référentiel contient des images pour différentes combinaisons possibles de .NET (kit de développement logiciel ou runtime) et du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="1516e-192">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="1516e-193">Microsoft fournit des images adaptées à des scénarios particuliers.</span><span class="sxs-lookup"><span data-stu-id="1516e-193">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="1516e-194">Par exemple, celles du [référentiel ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) sont conçues pour exécuter des applications ASP.NET Core en production.</span><span class="sxs-lookup"><span data-stu-id="1516e-194">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="1516e-195">Pour plus d’informations sur l’utilisation de .NET Core dans un conteneur d’ancrage, consultez [Introduction à .net et à l’ancreur](../docker/introduction.md) et aux [exemples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span><span class="sxs-lookup"><span data-stu-id="1516e-195">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="1516e-196">Étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="1516e-196">Next steps</span></span>

::: zone pivot="os-windows"

- <span data-ttu-id="1516e-197">[Didacticiel : Hello World didacticiel](../tutorials/with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="1516e-197">[Tutorial: Hello World tutorial](../tutorials/with-visual-studio.md).</span></span>
- <span data-ttu-id="1516e-198">[Didacticiel : créer une application avec Visual Studio code](../tutorials/with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="1516e-198">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="1516e-199">[Didacticiel : conteneur d’une application .net Core](../docker/build-container.md).</span><span class="sxs-lookup"><span data-stu-id="1516e-199">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end

::: zone pivot="os-macos"

- <span data-ttu-id="1516e-200">[Didacticiel : prise en main de MacOS](../tutorials/using-on-mac-vs.md).</span><span class="sxs-lookup"><span data-stu-id="1516e-200">[Tutorial: Get started on macOS](../tutorials/using-on-mac-vs.md).</span></span>
- <span data-ttu-id="1516e-201">[Didacticiel : créer une application avec Visual Studio code](../tutorials/with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="1516e-201">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="1516e-202">[Didacticiel : conteneur d’une application .net Core](../docker/build-container.md).</span><span class="sxs-lookup"><span data-stu-id="1516e-202">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end

::: zone pivot="os-linux"

- <span data-ttu-id="1516e-203">[Didacticiel : créer une application avec Visual Studio code](../tutorials/with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="1516e-203">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="1516e-204">[Didacticiel : conteneur d’une application .net Core](../docker/build-container.md).</span><span class="sxs-lookup"><span data-stu-id="1516e-204">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end
