---
title: Installer kit SDK .NET Core sur Windows, Linux et macOS-.NET Core
description: Découvrez comment installer .NET Core sur Windows, Linux et macOS. Découvrez les dépendances requises pour développer des applications .NET Core.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 0aa323533dd9136372c2bbc330c9c3056fdf428c
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78157569"
---
# <a name="install-the-net-core-sdk"></a><span data-ttu-id="45ac4-104">Installer le kit SDK .NET Core</span><span class="sxs-lookup"><span data-stu-id="45ac4-104">Install the .NET Core SDK</span></span>

<span data-ttu-id="45ac4-105">Dans cet article, vous allez apprendre à installer le kit SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="45ac4-105">In this article, you'll learn how to install the .NET Core SDK.</span></span> <span data-ttu-id="45ac4-106">Le kit SDK .NET Core est utilisé pour créer des applications et des bibliothèques .NET Core.</span><span class="sxs-lookup"><span data-stu-id="45ac4-106">The .NET Core SDK is used to create .NET Core apps and libraries.</span></span> <span data-ttu-id="45ac4-107">Le Runtime .NET Core est toujours installé avec le kit de développement logiciel (SDK).</span><span class="sxs-lookup"><span data-stu-id="45ac4-107">The .NET Core runtime is always installed with the SDK.</span></span>

::: zone pivot="os-windows"

## <a name="install-with-an-installer"></a><span data-ttu-id="45ac4-108">Installer avec un programme d’installation</span><span class="sxs-lookup"><span data-stu-id="45ac4-108">Install with an installer</span></span>

<span data-ttu-id="45ac4-109">Windows possède des programmes d’installation autonomes qui peuvent être utilisés pour installer le kit de développement logiciel (SDK) .NET Core 3,1 :</span><span class="sxs-lookup"><span data-stu-id="45ac4-109">Windows has standalone installers that can be used to install the .NET Core 3.1 SDK:</span></span>

- [<span data-ttu-id="45ac4-110">Processeurs x64 (64 bits)</span><span class="sxs-lookup"><span data-stu-id="45ac4-110">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="45ac4-111">Processeurs x86 (32 bits)</span><span class="sxs-lookup"><span data-stu-id="45ac4-111">x86 (32-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-an-installer"></a><span data-ttu-id="45ac4-112">Installer avec un programme d’installation</span><span class="sxs-lookup"><span data-stu-id="45ac4-112">Install with an installer</span></span>

<span data-ttu-id="45ac4-113">macOS possède des programmes d’installation autonomes qui peuvent être utilisés pour installer le kit de développement logiciel (SDK) .NET Core 3,1 :</span><span class="sxs-lookup"><span data-stu-id="45ac4-113">macOS has standalone installers that can be used to install the .NET Core 3.1 SDK:</span></span>

- [<span data-ttu-id="45ac4-114">Processeurs x64 (64 bits)</span><span class="sxs-lookup"><span data-stu-id="45ac4-114">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

## <a name="download-and-manually-install"></a><span data-ttu-id="45ac4-115">Télécharger et installer manuellement</span><span class="sxs-lookup"><span data-stu-id="45ac4-115">Download and manually install</span></span>

<span data-ttu-id="45ac4-116">Comme alternative aux programmes d’installation macOS pour .NET Core, vous pouvez télécharger et installer manuellement le kit de développement logiciel (SDK).</span><span class="sxs-lookup"><span data-stu-id="45ac4-116">As an alternative to the macOS installers for .NET Core, you can download and manually install the SDK.</span></span>

<span data-ttu-id="45ac4-117">Pour extraire le kit de développement logiciel (SDK) et rendre les commandes de CLI .NET Core disponibles sur le terminal, commencez par [Télécharger](#all-net-core-downloads) une version binaire de .net core.</span><span class="sxs-lookup"><span data-stu-id="45ac4-117">To extract the SDK and make the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="45ac4-118">Ensuite, ouvrez un terminal et exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="45ac4-118">Then, open a terminal and run the following commands.</span></span> <span data-ttu-id="45ac4-119">Il est supposé que le runtime est téléchargé dans le fichier `~/Downloads/dotnet-sdk.pkg`.</span><span class="sxs-lookup"><span data-stu-id="45ac4-119">It's assumed the runtime is downloaded to the `~/Downloads/dotnet-sdk.pkg` file.</span></span>

```bash
mkdir -p $HOME/dotnet
sudo installer -pkg ~/Downloads/dotnet-sdk.pkg -target $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

::: zone-end

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a><span data-ttu-id="45ac4-120">Installer avec un gestionnaire de package</span><span class="sxs-lookup"><span data-stu-id="45ac4-120">Install with a package manager</span></span>

<span data-ttu-id="45ac4-121">Vous pouvez installer les kit SDK .NET Core avec un grand nombre de gestionnaires de packages Linux courants.</span><span class="sxs-lookup"><span data-stu-id="45ac4-121">You can install the .NET Core SDK with many of the common Linux package managers.</span></span> <span data-ttu-id="45ac4-122">Pour plus d’informations, consultez [Linux Package Manager-install .net Core](linux-package-managers.md).</span><span class="sxs-lookup"><span data-stu-id="45ac4-122">For more information, see [Linux Package Manager - Install .NET Core](linux-package-managers.md).</span></span>

<span data-ttu-id="45ac4-123">L’installation de avec un gestionnaire de package est uniquement prise en charge sur l’architecture x64.</span><span class="sxs-lookup"><span data-stu-id="45ac4-123">Installing with a package manager is only supported on the x64 architecture.</span></span> <span data-ttu-id="45ac4-124">Si vous installez le kit SDK .NET Core avec une architecture différente, par exemple ARM, suivez les instructions de [téléchargement et d’installation manuelle](#download-and-manually-install) ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="45ac4-124">If you're installing the .NET Core SDK with a different architecture, such as ARM, follow the [Download and manually install](#download-and-manually-install) instructions below.</span></span> <span data-ttu-id="45ac4-125">Pour plus d’informations sur les architectures prises en charge, consultez [.net Core Dependencies and Requirements](dependencies.md).</span><span class="sxs-lookup"><span data-stu-id="45ac4-125">For more information about what architectures are supported, see [.NET Core dependencies and requirements](dependencies.md).</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="45ac4-126">Télécharger et installer manuellement</span><span class="sxs-lookup"><span data-stu-id="45ac4-126">Download and manually install</span></span>

<span data-ttu-id="45ac4-127">Pour extraire le kit de développement logiciel (SDK) et rendre les commandes de CLI .NET Core disponibles sur le terminal, commencez par [Télécharger](#all-net-core-downloads) une version binaire de .net core.</span><span class="sxs-lookup"><span data-stu-id="45ac4-127">To extract the SDK and make the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="45ac4-128">Ensuite, ouvrez un terminal et exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="45ac4-128">Then, open a terminal and run the following commands.</span></span>

```bash
mkdir -p $HOME/dotnet && tar zxf dotnet-sdk-3.1.100-linux-x64.tar.gz -C $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> <span data-ttu-id="45ac4-129">Les commandes `export` précédentes rendent uniquement les commandes CLI .NET Core disponibles pour la session Terminal dans laquelle elles ont été exécutées.</span><span class="sxs-lookup"><span data-stu-id="45ac4-129">The preceding `export` commands only make the .NET Core CLI commands available for the terminal session in which it was run.</span></span>
>
> <span data-ttu-id="45ac4-130">Vous pouvez modifier votre profil de Shell pour ajouter définitivement les commandes.</span><span class="sxs-lookup"><span data-stu-id="45ac4-130">You can edit your shell profile to permanently add the commands.</span></span> <span data-ttu-id="45ac4-131">Un certain nombre de shells différents sont disponibles pour Linux et chacun d’eux a un profil différent.</span><span class="sxs-lookup"><span data-stu-id="45ac4-131">There are a number of different shells available for Linux and each has a different profile.</span></span> <span data-ttu-id="45ac4-132">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="45ac4-132">For example:</span></span>
>
> - <span data-ttu-id="45ac4-133">**Interpréteur**de commandes bash : *~/. bash_profile*, *~ fichier/.bashrc*</span><span class="sxs-lookup"><span data-stu-id="45ac4-133">**Bash Shell**: *~/.bash_profile*, *~/.bashrc*</span></span>
> - <span data-ttu-id="45ac4-134">**Shell Korn**: *~/.kshrc* ou *. Profile*</span><span class="sxs-lookup"><span data-stu-id="45ac4-134">**Korn Shell**: *~/.kshrc* or *.profile*</span></span>
> - <span data-ttu-id="45ac4-135">**Z Shell**: *~/.zshrc* ou *. zprofile*</span><span class="sxs-lookup"><span data-stu-id="45ac4-135">**Z Shell**: *~/.zshrc* or *.zprofile*</span></span>
>
> <span data-ttu-id="45ac4-136">Modifiez le fichier source approprié pour votre shell et ajoutez `:$HOME/dotnet` à la fin de l’instruction `PATH` existante.</span><span class="sxs-lookup"><span data-stu-id="45ac4-136">Edit the appropriate source file for your shell and add `:$HOME/dotnet` to the end of the existing `PATH` statement.</span></span> <span data-ttu-id="45ac4-137">Si aucune instruction `PATH` n’est incluse, ajoutez une nouvelle ligne avec `export PATH=$PATH:$HOME/dotnet`.</span><span class="sxs-lookup"><span data-stu-id="45ac4-137">If no `PATH` statement is included, add a new line with `export PATH=$PATH:$HOME/dotnet`.</span></span>
>
> <span data-ttu-id="45ac4-138">En outre, ajoutez `export DOTNET_ROOT=$HOME/dotnet` à la fin du fichier.</span><span class="sxs-lookup"><span data-stu-id="45ac4-138">Also, add `export DOTNET_ROOT=$HOME/dotnet` to the end of the file.</span></span>

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-visual-studio"></a><span data-ttu-id="45ac4-139">Installer avec Visual Studio</span><span class="sxs-lookup"><span data-stu-id="45ac4-139">Install with Visual Studio</span></span>

<span data-ttu-id="45ac4-140">Si vous utilisez Visual Studio pour développer des applications .NET Core, le tableau suivant décrit la version minimale requise de Visual Studio en fonction de la version de kit SDK .NET Core cible.</span><span class="sxs-lookup"><span data-stu-id="45ac4-140">If you're using Visual Studio to develop .NET Core apps, the following table describes the minimum required version of Visual Studio based on the target .NET Core SDK version.</span></span>

| <span data-ttu-id="45ac4-141">Version de kit SDK .NET Core</span><span class="sxs-lookup"><span data-stu-id="45ac4-141">.NET Core SDK version</span></span> | <span data-ttu-id="45ac4-142">Version de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="45ac4-142">Visual Studio version</span></span>                      |
| --------------------- | ------------------------------------------ |
| <span data-ttu-id="45ac4-143">3.1</span><span class="sxs-lookup"><span data-stu-id="45ac4-143">3.1</span></span>                   | <span data-ttu-id="45ac4-144">Visual Studio 2019 version 16,4 ou ultérieure.</span><span class="sxs-lookup"><span data-stu-id="45ac4-144">Visual Studio 2019 version 16.4 or higher.</span></span> |
| <span data-ttu-id="45ac4-145">3.0</span><span class="sxs-lookup"><span data-stu-id="45ac4-145">3.0</span></span>                   | <span data-ttu-id="45ac4-146">Visual Studio 2019 version 16,3 ou ultérieure.</span><span class="sxs-lookup"><span data-stu-id="45ac4-146">Visual Studio 2019 version 16.3 or higher.</span></span> |
| <span data-ttu-id="45ac4-147">2.2</span><span class="sxs-lookup"><span data-stu-id="45ac4-147">2.2</span></span>                   | <span data-ttu-id="45ac4-148">Visual Studio 2017 version 15,9 ou ultérieure.</span><span class="sxs-lookup"><span data-stu-id="45ac4-148">Visual Studio 2017 version 15.9 or higher.</span></span> |
| <span data-ttu-id="45ac4-149">2.1</span><span class="sxs-lookup"><span data-stu-id="45ac4-149">2.1</span></span>                   | <span data-ttu-id="45ac4-150">Visual Studio 2017 version 15,7 ou ultérieure.</span><span class="sxs-lookup"><span data-stu-id="45ac4-150">Visual Studio 2017 version 15.7 or higher.</span></span> |

<span data-ttu-id="45ac4-151">Si vous avez déjà installé Visual Studio, vous pouvez vérifier votre version en procédant comme suit.</span><span class="sxs-lookup"><span data-stu-id="45ac4-151">If you already have Visual Studio installed, you can check your version with the following steps.</span></span>

01. <span data-ttu-id="45ac4-152">Ouvrez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="45ac4-152">Open Visual Studio.</span></span>
01. <span data-ttu-id="45ac4-153">Sélectionnez **aide** > **à propos de Microsoft Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="45ac4-153">Select **Help** > **About Microsoft Visual Studio**.</span></span>
01. <span data-ttu-id="45ac4-154">Lisez le numéro de version dans la boîte de dialogue **à propos** de.</span><span class="sxs-lookup"><span data-stu-id="45ac4-154">Read the version number from the **About** dialog.</span></span>

<span data-ttu-id="45ac4-155">Visual Studio peut installer les kit SDK .NET Core et Runtime les plus récents.</span><span class="sxs-lookup"><span data-stu-id="45ac4-155">Visual Studio can install the latest .NET Core SDK and runtime.</span></span>

- <span data-ttu-id="45ac4-156">[Téléchargez Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span><span class="sxs-lookup"><span data-stu-id="45ac4-156">[Download Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span></span>

### <a name="select-a-workload"></a><span data-ttu-id="45ac4-157">Sélectionner une charge de travail</span><span class="sxs-lookup"><span data-stu-id="45ac4-157">Select a workload</span></span>

<span data-ttu-id="45ac4-158">Lors de l’installation ou de la modification de Visual Studio, sélectionnez une ou plusieurs des charges de travail suivantes, en fonction du type d’application que vous créez :</span><span class="sxs-lookup"><span data-stu-id="45ac4-158">When installing or modifying Visual Studio, select one or more of the following workloads, depending on the kind of application you're building:</span></span>

- <span data-ttu-id="45ac4-159">La charge de travail **développement multiplateforme .net Core** dans la section **autres ensembles d’outils** .</span><span class="sxs-lookup"><span data-stu-id="45ac4-159">The **.NET Core cross-platform development** workload in the **Other Toolsets** section.</span></span>
- <span data-ttu-id="45ac4-160">La charge de travail **ASP.net et développement Web** dans la section **Web & Cloud** .</span><span class="sxs-lookup"><span data-stu-id="45ac4-160">The **ASP.NET and web development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="45ac4-161">La charge de travail **développement Azure** dans la section **Web & Cloud** .</span><span class="sxs-lookup"><span data-stu-id="45ac4-161">The **Azure development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="45ac4-162">La charge de travail **développement .net Desktop** dans la section **Desktop & mobile** .</span><span class="sxs-lookup"><span data-stu-id="45ac4-162">The **.NET desktop development** workload in the **Desktop & Mobile** section.</span></span>

<span data-ttu-id="45ac4-163">[![Windows Visual Studio 2019 avec charge de travail .NET Core](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="45ac4-163">[![Windows Visual Studio 2019 with .NET Core workload](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="45ac4-164">Télécharger et installer manuellement</span><span class="sxs-lookup"><span data-stu-id="45ac4-164">Download and manually install</span></span>

<span data-ttu-id="45ac4-165">Pour extraire le runtime et rendre les commandes CLI .NET Core disponibles sur le terminal, commencez par [Télécharger](#all-net-core-downloads) une version binaire .net core.</span><span class="sxs-lookup"><span data-stu-id="45ac4-165">To extract the runtime and make the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="45ac4-166">Ensuite, créez un répertoire dans lequel effectuer l’installation, par exemple `%USERPROFILE%\dotnet`.</span><span class="sxs-lookup"><span data-stu-id="45ac4-166">Then, create a directory to install to, for example `%USERPROFILE%\dotnet`.</span></span> <span data-ttu-id="45ac4-167">Enfin, extrayez le fichier zip téléchargé dans ce répertoire.</span><span class="sxs-lookup"><span data-stu-id="45ac4-167">Finally, extract the downloaded zip file into that directory.</span></span>

<span data-ttu-id="45ac4-168">Par défaut, les commandes et applications CLI .NET Core n’utilisent pas .NET Core de cette manière.</span><span class="sxs-lookup"><span data-stu-id="45ac4-168">By default, .NET Core CLI commands and apps will not use .NET Core installed in this way.</span></span> <span data-ttu-id="45ac4-169">Vous devez choisir explicitement de l’utiliser.</span><span class="sxs-lookup"><span data-stu-id="45ac4-169">You have to explicitly choose to use it.</span></span> <span data-ttu-id="45ac4-170">Pour ce faire, modifiez les variables d’environnement à l’aide desquelles une application est démarrée :</span><span class="sxs-lookup"><span data-stu-id="45ac4-170">To do so, change the environment variables with which an application is started:</span></span>

```console
set DOTNET_ROOT=%USERPROFILE%\dotnet
set PATH=%USERPROFILE%\dotnet;%PATH%
```

<span data-ttu-id="45ac4-171">Cette approche vous permet d’installer plusieurs versions dans des emplacements distincts, puis de choisir explicitement l’emplacement d’installation qu’une application doit utiliser en exécutant l’application avec des variables d’environnement qui pointent à cet emplacement.</span><span class="sxs-lookup"><span data-stu-id="45ac4-171">This approach lets you install multiple versions into separate locations, then explicitly choose which install location an application should use by running the application with environment variables pointing at that location.</span></span>

<span data-ttu-id="45ac4-172">Même lorsque ces variables d’environnement sont définies, .NET Core prend toujours en compte l’emplacement d’installation globale par défaut lors de la sélection du meilleur Framework pour l’exécution de l’application.</span><span class="sxs-lookup"><span data-stu-id="45ac4-172">Even when these environment variables are set, .NET Core still considers the default global install location when selecting the best framework for running the application.</span></span> <span data-ttu-id="45ac4-173">La valeur par défaut est généralement `C:\Program Files\dotnet`, que les programmes d’installation utilisent.</span><span class="sxs-lookup"><span data-stu-id="45ac4-173">The default is typically `C:\Program Files\dotnet`, which the installers use.</span></span> <span data-ttu-id="45ac4-174">Vous pouvez indiquer à l’exécution d’utiliser uniquement l’emplacement d’installation personnalisé en définissant également cette variable d’environnement :</span><span class="sxs-lookup"><span data-stu-id="45ac4-174">You can instruct the runtime to only use the custom install location by setting this environment variable as well:</span></span>

```console
set DOTNET_MULTILEVEL_LOOKUP=0
```

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-visual-studio-for-mac"></a><span data-ttu-id="45ac4-175">Installer avec Visual Studio pour Mac</span><span class="sxs-lookup"><span data-stu-id="45ac4-175">Install with Visual Studio for Mac</span></span>

<span data-ttu-id="45ac4-176">Visual Studio pour Mac installe le kit SDK .NET Core lorsque la charge de travail **.net Core** est sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="45ac4-176">Visual Studio for Mac installs the .NET Core SDK when the **.NET Core** workload is selected.</span></span> <span data-ttu-id="45ac4-177">Pour commencer à utiliser le développement .NET Core sur macOS, consultez [installer Visual Studio 2019 pour Mac](/visualstudio/mac/installation).</span><span class="sxs-lookup"><span data-stu-id="45ac4-177">To get started with .NET Core development on macOS, see [Install Visual Studio 2019 for Mac](/visualstudio/mac/installation).</span></span> <span data-ttu-id="45ac4-178">Pour la version la plus récente, .NET Core 3,1, vous devez utiliser le Visual Studio pour Mac 8,4 preview.</span><span class="sxs-lookup"><span data-stu-id="45ac4-178">For the latest release, .NET Core 3.1, you must use the Visual Studio for Mac 8.4 Preview.</span></span>

<span data-ttu-id="45ac4-179">[![la fonctionnalité de charge de travail de Visual Studio 2019 pour Mac macOS avec .NET Core](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="45ac4-179">[![macOS Visual Studio 2019 for Mac with .NET Core workload feature](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span></span>

::: zone-end

## <a name="install-alongside-visual-studio-code"></a><span data-ttu-id="45ac4-180">Installer en même temps que Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="45ac4-180">Install alongside Visual Studio Code</span></span>

<span data-ttu-id="45ac4-181">Visual Studio Code est un éditeur de code source puissant et léger qui s’exécute sur votre bureau.</span><span class="sxs-lookup"><span data-stu-id="45ac4-181">Visual Studio Code is a powerful and lightweight source code editor that runs on your desktop.</span></span> <span data-ttu-id="45ac4-182">Visual Studio Code est disponible pour Windows, macOS et Linux.</span><span class="sxs-lookup"><span data-stu-id="45ac4-182">Visual Studio Code is available for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="45ac4-183">Même si Visual Studio Code n’est pas fourni avec un programme d’installation automatisé de .NET Core, comme Visual Studio, l’ajout de la prise en charge de .NET Core est simple.</span><span class="sxs-lookup"><span data-stu-id="45ac4-183">While Visual Studio Code doesn't come with an automated .NET Core installer like Visual Studio does, adding .NET Core support is simple.</span></span>

01. <span data-ttu-id="45ac4-184">[Téléchargez et installez Visual Studio code](https://code.visualstudio.com/Download).</span><span class="sxs-lookup"><span data-stu-id="45ac4-184">[Download and install Visual Studio Code](https://code.visualstudio.com/Download).</span></span>
01. <span data-ttu-id="45ac4-185">[Téléchargez et installez le kit SDK .net Core](https://dotnet.microsoft.com/download/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="45ac4-185">[Download and install the .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core).</span></span>
01. <span data-ttu-id="45ac4-186">[Installez l' C# extension à partir de la place de marché Visual Studio code](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp).</span><span class="sxs-lookup"><span data-stu-id="45ac4-186">[Install the C# extension from the Visual Studio Code marketplace](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp).</span></span>

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a><span data-ttu-id="45ac4-187">Installer avec l’automatisation PowerShell</span><span class="sxs-lookup"><span data-stu-id="45ac4-187">Install with PowerShell automation</span></span>

<span data-ttu-id="45ac4-188">Les [scripts dotnet-install](../tools/dotnet-install-script.md) sont utilisés pour l’automatisation et les installations non administratives du kit de développement logiciel (SDK).</span><span class="sxs-lookup"><span data-stu-id="45ac4-188">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the SDK.</span></span> <span data-ttu-id="45ac4-189">Vous pouvez télécharger le script à partir de la [page de référence du script dotnet-install](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="45ac4-189">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="45ac4-190">Par défaut, le script installe la dernière version de [support à long terme (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , qui est .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="45ac4-190">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="45ac4-191">Pour installer la version actuelle de .NET Core, exécutez le script avec le commutateur suivant.</span><span class="sxs-lookup"><span data-stu-id="45ac4-191">To install the current release of .NET Core, run the script with the following switch.</span></span>

```powershell
dotnet-install.ps1 -Channel Current
```

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a><span data-ttu-id="45ac4-192">Installer avec l’automatisation bash</span><span class="sxs-lookup"><span data-stu-id="45ac4-192">Install with bash automation</span></span>

<span data-ttu-id="45ac4-193">Les [scripts dotnet-install](../tools/dotnet-install-script.md) sont utilisés pour l’automatisation et les installations non administratives du kit de développement logiciel (SDK).</span><span class="sxs-lookup"><span data-stu-id="45ac4-193">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the SDK.</span></span> <span data-ttu-id="45ac4-194">Vous pouvez télécharger le script à partir de la [page de référence du script dotnet-install](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="45ac4-194">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="45ac4-195">Par défaut, le script installe la dernière version de [support à long terme (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , qui est .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="45ac4-195">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="45ac4-196">Pour installer la version actuelle de .NET Core, exécutez le script avec le commutateur suivant.</span><span class="sxs-lookup"><span data-stu-id="45ac4-196">To install the current release of .NET Core, run the script with the following switch.</span></span>

```bash
./dotnet-install.sh -c Current
```

::: zone-end

## <a name="all-net-core-downloads"></a><span data-ttu-id="45ac4-197">Tous les téléchargements .NET Core</span><span class="sxs-lookup"><span data-stu-id="45ac4-197">All .NET Core downloads</span></span>

<span data-ttu-id="45ac4-198">Vous pouvez télécharger et installer .NET Core directement avec l’un des liens suivants :</span><span class="sxs-lookup"><span data-stu-id="45ac4-198">You can download and install .NET Core directly with one of the following links:</span></span>

- [<span data-ttu-id="45ac4-199">Téléchargements .NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="45ac4-199">.NET Core 3.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="45ac4-200">Téléchargements .NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="45ac4-200">.NET Core 3.0 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- [<span data-ttu-id="45ac4-201">Téléchargements .NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="45ac4-201">.NET Core 2.2 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- [<span data-ttu-id="45ac4-202">Téléchargements .NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="45ac4-202">.NET Core 2.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a><span data-ttu-id="45ac4-203">Docker</span><span class="sxs-lookup"><span data-stu-id="45ac4-203">Docker</span></span>

<span data-ttu-id="45ac4-204">Les conteneurs offrent un moyen léger d’isoler votre application du reste du système hôte.</span><span class="sxs-lookup"><span data-stu-id="45ac4-204">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="45ac4-205">Les conteneurs sur le même ordinateur partagent simplement le noyau et utilisent les ressources fournies à votre application.</span><span class="sxs-lookup"><span data-stu-id="45ac4-205">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="45ac4-206">.NET Core peut s’exécuter dans un conteneur d’ancrage.</span><span class="sxs-lookup"><span data-stu-id="45ac4-206">.NET Core can run in a Docker container.</span></span> <span data-ttu-id="45ac4-207">Les images Docker .NET Core officielles sont publiées dans Microsoft Container Registry (MCR) et détectables dans le [référentiel Docker Hub Microsoft .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/).</span><span class="sxs-lookup"><span data-stu-id="45ac4-207">Official .NET Core Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span> <span data-ttu-id="45ac4-208">Chaque référentiel contient des images pour différentes combinaisons possibles de .NET (kit de développement logiciel ou runtime) et du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="45ac4-208">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="45ac4-209">Microsoft fournit des images adaptées à des scénarios particuliers.</span><span class="sxs-lookup"><span data-stu-id="45ac4-209">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="45ac4-210">Par exemple, celles du [référentiel ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) sont conçues pour exécuter des applications ASP.NET Core en production.</span><span class="sxs-lookup"><span data-stu-id="45ac4-210">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="45ac4-211">Pour plus d’informations sur l’utilisation de .NET Core dans un conteneur d’ancrage, consultez [Introduction à .net et à l’ancreur](../docker/introduction.md) et aux [exemples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span><span class="sxs-lookup"><span data-stu-id="45ac4-211">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="45ac4-212">Étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="45ac4-212">Next steps</span></span>

::: zone pivot="os-windows"

- <span data-ttu-id="45ac4-213">[Didacticiel : Hello World didacticiel](../tutorials/with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="45ac4-213">[Tutorial: Hello World tutorial](../tutorials/with-visual-studio.md).</span></span>
- <span data-ttu-id="45ac4-214">[Didacticiel : créer une application avec Visual Studio code](../tutorials/with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="45ac4-214">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="45ac4-215">[Didacticiel : conteneur d’une application .net Core](../docker/build-container.md).</span><span class="sxs-lookup"><span data-stu-id="45ac4-215">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end

::: zone pivot="os-macos"

- <span data-ttu-id="45ac4-216">[Utilisation de la notaire Catalina MacOS](macos-notarization-issues.md).</span><span class="sxs-lookup"><span data-stu-id="45ac4-216">[Working with macOS Catalina notarization](macos-notarization-issues.md).</span></span>
- <span data-ttu-id="45ac4-217">[Didacticiel : prise en main de MacOS](../tutorials/using-on-mac-vs.md).</span><span class="sxs-lookup"><span data-stu-id="45ac4-217">[Tutorial: Get started on macOS](../tutorials/using-on-mac-vs.md).</span></span>
- <span data-ttu-id="45ac4-218">[Didacticiel : créer une application avec Visual Studio code](../tutorials/with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="45ac4-218">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="45ac4-219">[Didacticiel : conteneur d’une application .net Core](../docker/build-container.md).</span><span class="sxs-lookup"><span data-stu-id="45ac4-219">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end

::: zone pivot="os-linux"

- <span data-ttu-id="45ac4-220">[Didacticiel : créer une application avec Visual Studio code](../tutorials/with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="45ac4-220">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="45ac4-221">[Didacticiel : conteneur d’une application .net Core](../docker/build-container.md).</span><span class="sxs-lookup"><span data-stu-id="45ac4-221">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end
