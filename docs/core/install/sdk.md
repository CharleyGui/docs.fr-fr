---
title: Installer .NET Core SDK sur Windows, Linux et macOS - .NET Core
description: Apprenez à installer .NET Core sur Windows, Linux et macOS. Découvrez les dépendances nécessaires au développement d’applications .NET Core.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 13600ea01e18ad47e6295653ba3b79ce53ff3257
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399006"
---
# <a name="install-the-net-core-sdk"></a><span data-ttu-id="cde23-104">Installer le kit de développement logiciel (SDK) .NET Core</span><span class="sxs-lookup"><span data-stu-id="cde23-104">Install the .NET Core SDK</span></span>

<span data-ttu-id="cde23-105">Dans cet article, vous apprendrez à installer le .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="cde23-105">In this article, you'll learn how to install the .NET Core SDK.</span></span> <span data-ttu-id="cde23-106">Le .NET Core SDK est utilisé pour créer des applications et des bibliothèques .NET Core.</span><span class="sxs-lookup"><span data-stu-id="cde23-106">The .NET Core SDK is used to create .NET Core apps and libraries.</span></span> <span data-ttu-id="cde23-107">Le temps d’exécution .NET Core est toujours installé avec le SDK.</span><span class="sxs-lookup"><span data-stu-id="cde23-107">The .NET Core runtime is always installed with the SDK.</span></span>

::: zone pivot="os-windows"

## <a name="install-with-an-installer"></a><span data-ttu-id="cde23-108">Installer avec un installateur</span><span class="sxs-lookup"><span data-stu-id="cde23-108">Install with an installer</span></span>

<span data-ttu-id="cde23-109">Windows a des installateurs autonomes qui peuvent être utilisés pour installer le .NET Core 3.1 SDK:</span><span class="sxs-lookup"><span data-stu-id="cde23-109">Windows has standalone installers that can be used to install the .NET Core 3.1 SDK:</span></span>

- [<span data-ttu-id="cde23-110">x64 (64 bits) DPC</span><span class="sxs-lookup"><span data-stu-id="cde23-110">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="cde23-111">x86 (32 bits) CPU</span><span class="sxs-lookup"><span data-stu-id="cde23-111">x86 (32-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-an-installer"></a><span data-ttu-id="cde23-112">Installer avec un installateur</span><span class="sxs-lookup"><span data-stu-id="cde23-112">Install with an installer</span></span>

<span data-ttu-id="cde23-113">macOS a des installateurs autonomes qui peuvent être utilisés pour installer le .NET Core 3.1 SDK:</span><span class="sxs-lookup"><span data-stu-id="cde23-113">macOS has standalone installers that can be used to install the .NET Core 3.1 SDK:</span></span>

- [<span data-ttu-id="cde23-114">x64 (64 bits) DPC</span><span class="sxs-lookup"><span data-stu-id="cde23-114">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

## <a name="download-and-manually-install"></a><span data-ttu-id="cde23-115">Télécharger et installer manuellement</span><span class="sxs-lookup"><span data-stu-id="cde23-115">Download and manually install</span></span>

<span data-ttu-id="cde23-116">Comme alternative aux installateurs macOS pour .NET Core, vous pouvez télécharger et installer manuellement le SDK.</span><span class="sxs-lookup"><span data-stu-id="cde23-116">As an alternative to the macOS installers for .NET Core, you can download and manually install the SDK.</span></span>

<span data-ttu-id="cde23-117">Pour extraire le SDK et rendre disponibles les commandes CLI .NET Core au terminal, [téléchargez](#all-net-core-downloads) d’abord une version binaire .NET Core.</span><span class="sxs-lookup"><span data-stu-id="cde23-117">To extract the SDK and make the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="cde23-118">Ensuite, ouvrez un terminal et exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="cde23-118">Then, open a terminal and run the following commands.</span></span> <span data-ttu-id="cde23-119">On suppose que le temps d’exécution est téléchargé sur le `~/Downloads/dotnet-sdk.pkg` fichier.</span><span class="sxs-lookup"><span data-stu-id="cde23-119">It's assumed the runtime is downloaded to the `~/Downloads/dotnet-sdk.pkg` file.</span></span>

```bash
mkdir -p $HOME/dotnet
sudo installer -pkg ~/Downloads/dotnet-sdk.pkg -target $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

::: zone-end

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a><span data-ttu-id="cde23-120">Installer avec un gestionnaire de paquets</span><span class="sxs-lookup"><span data-stu-id="cde23-120">Install with a package manager</span></span>

<span data-ttu-id="cde23-121">Vous pouvez installer le .NET Core SDK avec de nombreux gestionnaires de paquets Linux communs.</span><span class="sxs-lookup"><span data-stu-id="cde23-121">You can install the .NET Core SDK with many of the common Linux package managers.</span></span> <span data-ttu-id="cde23-122">Pour plus d’informations, voir [Linux Package Manager - Install .NET Core](linux-package-managers.md).</span><span class="sxs-lookup"><span data-stu-id="cde23-122">For more information, see [Linux Package Manager - Install .NET Core](linux-package-managers.md).</span></span>

<span data-ttu-id="cde23-123">L’installation avec un gestionnaire de paquets n’est pris en charge que sur l’architecture x64.</span><span class="sxs-lookup"><span data-stu-id="cde23-123">Installing with a package manager is only supported on the x64 architecture.</span></span> <span data-ttu-id="cde23-124">Si vous installez le .NET Core SDK avec une architecture différente, comme ARM, suivez le [Télécharger et installer manuellement](#download-and-manually-install) des instructions ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="cde23-124">If you're installing the .NET Core SDK with a different architecture, such as ARM, follow the [Download and manually install](#download-and-manually-install) instructions below.</span></span> <span data-ttu-id="cde23-125">Pour plus d’informations sur les architectures qui sont prises en charge, voir [.NET Core dépendances et les exigences](dependencies.md).</span><span class="sxs-lookup"><span data-stu-id="cde23-125">For more information about what architectures are supported, see [.NET Core dependencies and requirements](dependencies.md).</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="cde23-126">Télécharger et installer manuellement</span><span class="sxs-lookup"><span data-stu-id="cde23-126">Download and manually install</span></span>

<span data-ttu-id="cde23-127">Pour extraire le SDK et rendre disponibles les commandes CLI .NET Core au terminal, [téléchargez](#all-net-core-downloads) d’abord une version binaire .NET Core.</span><span class="sxs-lookup"><span data-stu-id="cde23-127">To extract the SDK and make the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="cde23-128">Ensuite, ouvrez un terminal et exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="cde23-128">Then, open a terminal and run the following commands.</span></span>

```bash
mkdir -p $HOME/dotnet && tar zxf dotnet-sdk-3.1.100-linux-x64.tar.gz -C $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> <span data-ttu-id="cde23-129">Les `export` commandes précédentes ne rendent disponibles que les commandes CLI de base .NET pour la session terminale au cours de laquelle il a été exécuté.</span><span class="sxs-lookup"><span data-stu-id="cde23-129">The preceding `export` commands only make the .NET Core CLI commands available for the terminal session in which it was run.</span></span>
>
> <span data-ttu-id="cde23-130">Vous pouvez modifier votre profil shell pour ajouter définitivement les commandes.</span><span class="sxs-lookup"><span data-stu-id="cde23-130">You can edit your shell profile to permanently add the commands.</span></span> <span data-ttu-id="cde23-131">Il ya un certain nombre de coquilles différentes disponibles pour Linux et chacun a un profil différent.</span><span class="sxs-lookup"><span data-stu-id="cde23-131">There are a number of different shells available for Linux and each has a different profile.</span></span> <span data-ttu-id="cde23-132">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="cde23-132">For example:</span></span>
>
> - <span data-ttu-id="cde23-133">**Bash Shell**: *'/.bash_profile*, *'/.bashrc'*</span><span class="sxs-lookup"><span data-stu-id="cde23-133">**Bash Shell**: *~/.bash_profile*, *~/.bashrc*</span></span>
> - <span data-ttu-id="cde23-134">**Korn Shell**: *'/.kshrc* ou *.profil*</span><span class="sxs-lookup"><span data-stu-id="cde23-134">**Korn Shell**: *~/.kshrc* or *.profile*</span></span>
> - <span data-ttu-id="cde23-135">**Z Shell**: *'/.zshrc* ou *.zprofile*</span><span class="sxs-lookup"><span data-stu-id="cde23-135">**Z Shell**: *~/.zshrc* or *.zprofile*</span></span>
>
> <span data-ttu-id="cde23-136">Modifiez le fichier source approprié `:$HOME/dotnet` pour votre coque `PATH` et ajoutez à la fin de l’instruction existante.</span><span class="sxs-lookup"><span data-stu-id="cde23-136">Edit the appropriate source file for your shell and add `:$HOME/dotnet` to the end of the existing `PATH` statement.</span></span> <span data-ttu-id="cde23-137">Si `PATH` aucune déclaration n’est incluse, ajoutez une nouvelle ligne avec `export PATH=$PATH:$HOME/dotnet`.</span><span class="sxs-lookup"><span data-stu-id="cde23-137">If no `PATH` statement is included, add a new line with `export PATH=$PATH:$HOME/dotnet`.</span></span>
>
> <span data-ttu-id="cde23-138">En outre, ajouter `export DOTNET_ROOT=$HOME/dotnet` à la fin du fichier.</span><span class="sxs-lookup"><span data-stu-id="cde23-138">Also, add `export DOTNET_ROOT=$HOME/dotnet` to the end of the file.</span></span>

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-visual-studio"></a><span data-ttu-id="cde23-139">Installer avec Visual Studio</span><span class="sxs-lookup"><span data-stu-id="cde23-139">Install with Visual Studio</span></span>

<span data-ttu-id="cde23-140">Si vous utilisez Visual Studio pour développer des applications .NET Core, le tableau suivant décrit la version minimale requise de Visual Studio en fonction de la version SDK target .NET Core.</span><span class="sxs-lookup"><span data-stu-id="cde23-140">If you're using Visual Studio to develop .NET Core apps, the following table describes the minimum required version of Visual Studio based on the target .NET Core SDK version.</span></span>

| <span data-ttu-id="cde23-141">version SDK Core .NET</span><span class="sxs-lookup"><span data-stu-id="cde23-141">.NET Core SDK version</span></span> | <span data-ttu-id="cde23-142">Version de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="cde23-142">Visual Studio version</span></span>                      |
| --------------------- | ------------------------------------------ |
| <span data-ttu-id="cde23-143">3.1</span><span class="sxs-lookup"><span data-stu-id="cde23-143">3.1</span></span>                   | <span data-ttu-id="cde23-144">Visual Studio 2019 version 16.4 ou plus.</span><span class="sxs-lookup"><span data-stu-id="cde23-144">Visual Studio 2019 version 16.4 or higher.</span></span> |
| <span data-ttu-id="cde23-145">3.0</span><span class="sxs-lookup"><span data-stu-id="cde23-145">3.0</span></span>                   | <span data-ttu-id="cde23-146">Visual Studio 2019 version 16.3 ou plus.</span><span class="sxs-lookup"><span data-stu-id="cde23-146">Visual Studio 2019 version 16.3 or higher.</span></span> |
| <span data-ttu-id="cde23-147">2.2</span><span class="sxs-lookup"><span data-stu-id="cde23-147">2.2</span></span>                   | <span data-ttu-id="cde23-148">Visual Studio 2017 version 15.9 ou plus.</span><span class="sxs-lookup"><span data-stu-id="cde23-148">Visual Studio 2017 version 15.9 or higher.</span></span> |
| <span data-ttu-id="cde23-149">2.1</span><span class="sxs-lookup"><span data-stu-id="cde23-149">2.1</span></span>                   | <span data-ttu-id="cde23-150">Visual Studio 2017 version 15.7 ou plus.</span><span class="sxs-lookup"><span data-stu-id="cde23-150">Visual Studio 2017 version 15.7 or higher.</span></span> |

<span data-ttu-id="cde23-151">Si vous avez déjà Visual Studio installé, vous pouvez vérifier votre version avec les étapes suivantes.</span><span class="sxs-lookup"><span data-stu-id="cde23-151">If you already have Visual Studio installed, you can check your version with the following steps.</span></span>

01. <span data-ttu-id="cde23-152">Ouvrez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="cde23-152">Open Visual Studio.</span></span>
01. <span data-ttu-id="cde23-153">Sélectionnez > **l’aide sur Microsoft Visual Studio**. **Help**</span><span class="sxs-lookup"><span data-stu-id="cde23-153">Select **Help** > **About Microsoft Visual Studio**.</span></span>
01. <span data-ttu-id="cde23-154">Lisez le numéro de version du **Dialogue About.**</span><span class="sxs-lookup"><span data-stu-id="cde23-154">Read the version number from the **About** dialog.</span></span>

<span data-ttu-id="cde23-155">Visual Studio peut installer le dernier .NET Core SDK et l’heure d’exécution.</span><span class="sxs-lookup"><span data-stu-id="cde23-155">Visual Studio can install the latest .NET Core SDK and runtime.</span></span>

- <span data-ttu-id="cde23-156">[Télécharger Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span><span class="sxs-lookup"><span data-stu-id="cde23-156">[Download Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span></span>

### <a name="select-a-workload"></a><span data-ttu-id="cde23-157">Sélectionnez une charge de travail</span><span class="sxs-lookup"><span data-stu-id="cde23-157">Select a workload</span></span>

<span data-ttu-id="cde23-158">Lors de l’installation ou de la modification de Visual Studio, sélectionnez une ou plusieurs des charges de travail suivantes, selon le type d’application que vous construisez :</span><span class="sxs-lookup"><span data-stu-id="cde23-158">When installing or modifying Visual Studio, select one or more of the following workloads, depending on the kind of application you're building:</span></span>

- <span data-ttu-id="cde23-159">La charge de travail **de développement multiplateforme .NET Core** dans la section Autres **outils.**</span><span class="sxs-lookup"><span data-stu-id="cde23-159">The **.NET Core cross-platform development** workload in the **Other Toolsets** section.</span></span>
- <span data-ttu-id="cde23-160">La charge de travail **de développement ASP.NET et Web** dans la section Web & **Cloud.**</span><span class="sxs-lookup"><span data-stu-id="cde23-160">The **ASP.NET and web development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="cde23-161">La charge de travail **de développement Azure** dans la section **Web & Cloud.**</span><span class="sxs-lookup"><span data-stu-id="cde23-161">The **Azure development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="cde23-162">La charge de travail **de développement de bureau .NET** dans la section Desktop & **Mobile.**</span><span class="sxs-lookup"><span data-stu-id="cde23-162">The **.NET desktop development** workload in the **Desktop & Mobile** section.</span></span>

<span data-ttu-id="cde23-163">[![Windows Visual Studio 2019 avec .NET Core charge de travail](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="cde23-163">[![Windows Visual Studio 2019 with .NET Core workload](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="cde23-164">Télécharger et installer manuellement</span><span class="sxs-lookup"><span data-stu-id="cde23-164">Download and manually install</span></span>

<span data-ttu-id="cde23-165">Pour extraire l’heure d’exécution et rendre disponibles les commandes CLI de base .NET au terminal, [téléchargez](#all-net-core-downloads) d’abord une version binaire .NET Core.</span><span class="sxs-lookup"><span data-stu-id="cde23-165">To extract the runtime and make the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="cde23-166">Ensuite, créez un répertoire à installer, par exemple. `%USERPROFILE%\dotnet`</span><span class="sxs-lookup"><span data-stu-id="cde23-166">Then, create a directory to install to, for example `%USERPROFILE%\dotnet`.</span></span> <span data-ttu-id="cde23-167">Enfin, extraire le fichier zip téléchargé dans ce répertoire.</span><span class="sxs-lookup"><span data-stu-id="cde23-167">Finally, extract the downloaded zip file into that directory.</span></span>

<span data-ttu-id="cde23-168">Par défaut, les commandes et les applications CLI de base .NET n’utiliseront pas le noyau .NET installé de cette façon.</span><span class="sxs-lookup"><span data-stu-id="cde23-168">By default, .NET Core CLI commands and apps will not use .NET Core installed in this way.</span></span> <span data-ttu-id="cde23-169">Vous devez choisir explicitement de l’utiliser.</span><span class="sxs-lookup"><span data-stu-id="cde23-169">You have to explicitly choose to use it.</span></span> <span data-ttu-id="cde23-170">Pour ce faire, modifiez les variables de l’environnement avec lesquelles une application est lancée :</span><span class="sxs-lookup"><span data-stu-id="cde23-170">To do so, change the environment variables with which an application is started:</span></span>

```console
set DOTNET_ROOT=%USERPROFILE%\dotnet
set PATH=%USERPROFILE%\dotnet;%PATH%
```

<span data-ttu-id="cde23-171">Cette approche vous permet d’installer plusieurs versions dans des endroits distincts, puis de choisir explicitement l’emplacement d’installation qu’une application doit utiliser en exécutant l’application avec des variables d’environnement pointant vers cet endroit.</span><span class="sxs-lookup"><span data-stu-id="cde23-171">This approach lets you install multiple versions into separate locations, then explicitly choose which install location an application should use by running the application with environment variables pointing at that location.</span></span>

<span data-ttu-id="cde23-172">Même lorsque ces variables d’environnement sont définies, .NET Core tient toujours compte de l’emplacement d’installation global par défaut lors de la sélection du meilleur cadre pour l’exécution de l’application.</span><span class="sxs-lookup"><span data-stu-id="cde23-172">Even when these environment variables are set, .NET Core still considers the default global install location when selecting the best framework for running the application.</span></span> <span data-ttu-id="cde23-173">La valeur `C:\Program Files\dotnet`par défaut est généralement, que les installateurs utilisent.</span><span class="sxs-lookup"><span data-stu-id="cde23-173">The default is typically `C:\Program Files\dotnet`, which the installers use.</span></span> <span data-ttu-id="cde23-174">Vous pouvez demander à l’heure d’exécution d’utiliser uniquement l’emplacement d’installation personnalisé en définissant cette variable d’environnement ainsi:</span><span class="sxs-lookup"><span data-stu-id="cde23-174">You can instruct the runtime to only use the custom install location by setting this environment variable as well:</span></span>

```console
set DOTNET_MULTILEVEL_LOOKUP=0
```

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-visual-studio-for-mac"></a><span data-ttu-id="cde23-175">Installer avec Visual Studio pour Mac</span><span class="sxs-lookup"><span data-stu-id="cde23-175">Install with Visual Studio for Mac</span></span>

<span data-ttu-id="cde23-176">Visual Studio pour Mac installe le .NET Core SDK lorsque la charge de travail **.NET Core** est sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="cde23-176">Visual Studio for Mac installs the .NET Core SDK when the **.NET Core** workload is selected.</span></span> <span data-ttu-id="cde23-177">Pour commencer avec .NET Core développement sur macOS, voir [Installer Visual Studio 2019 pour Mac](/visualstudio/mac/installation).</span><span class="sxs-lookup"><span data-stu-id="cde23-177">To get started with .NET Core development on macOS, see [Install Visual Studio 2019 for Mac](/visualstudio/mac/installation).</span></span> <span data-ttu-id="cde23-178">Pour la dernière version, .NET Core 3.1, vous devez utiliser le Visual Studio pour Mac 8.4 Aperçu.</span><span class="sxs-lookup"><span data-stu-id="cde23-178">For the latest release, .NET Core 3.1, you must use the Visual Studio for Mac 8.4 Preview.</span></span>

<span data-ttu-id="cde23-179">[![macOS Visual Studio 2019 pour Mac avec une fonction de charge de travail .NET Core](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="cde23-179">[![macOS Visual Studio 2019 for Mac with .NET Core workload feature](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span></span>

::: zone-end

## <a name="install-alongside-visual-studio-code"></a><span data-ttu-id="cde23-180">Installer aux côtés de Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="cde23-180">Install alongside Visual Studio Code</span></span>

<span data-ttu-id="cde23-181">Visual Studio Code est un éditeur de code source puissant et léger qui s’exécute sur votre bureau.</span><span class="sxs-lookup"><span data-stu-id="cde23-181">Visual Studio Code is a powerful and lightweight source code editor that runs on your desktop.</span></span> <span data-ttu-id="cde23-182">Visual Studio Code est disponible pour Windows, macOS et Linux.</span><span class="sxs-lookup"><span data-stu-id="cde23-182">Visual Studio Code is available for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="cde23-183">Bien que Visual Studio Code ne soit pas livré avec un installateur .NET Core automatisé comme Visual Studio, l’ajout de support .NET Core est simple.</span><span class="sxs-lookup"><span data-stu-id="cde23-183">While Visual Studio Code doesn't come with an automated .NET Core installer like Visual Studio does, adding .NET Core support is simple.</span></span>

01. <span data-ttu-id="cde23-184">[Téléchargez et installez Visual Studio Code](https://code.visualstudio.com/Download).</span><span class="sxs-lookup"><span data-stu-id="cde23-184">[Download and install Visual Studio Code](https://code.visualstudio.com/Download).</span></span>
01. <span data-ttu-id="cde23-185">[Téléchargez et installez le .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="cde23-185">[Download and install the .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core).</span></span>
01. <span data-ttu-id="cde23-186">[Installez l’extension Cmd à partir du marché du code de studio visuel.](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp)</span><span class="sxs-lookup"><span data-stu-id="cde23-186">[Install the C# extension from the Visual Studio Code marketplace](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp).</span></span>

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a><span data-ttu-id="cde23-187">Installer avec l’automatisation PowerShell</span><span class="sxs-lookup"><span data-stu-id="cde23-187">Install with PowerShell automation</span></span>

<span data-ttu-id="cde23-188">Les [scripts d’installation de dotnet](../tools/dotnet-install-script.md) sont utilisés pour l’automatisation et les installations non admin du SDK.</span><span class="sxs-lookup"><span data-stu-id="cde23-188">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the SDK.</span></span> <span data-ttu-id="cde23-189">Vous pouvez télécharger le script à partir de la page de [référence de script dotnet-install](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="cde23-189">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="cde23-190">Le script par défaut à l’installation de la dernière [version de support à long terme (LTS),](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) qui est .NET Core 3.1.</span><span class="sxs-lookup"><span data-stu-id="cde23-190">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="cde23-191">Pour installer la version actuelle de .NET Core, exécutez le script avec le commutateur suivant.</span><span class="sxs-lookup"><span data-stu-id="cde23-191">To install the current release of .NET Core, run the script with the following switch.</span></span>

```powershell
dotnet-install.ps1 -Channel Current
```

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a><span data-ttu-id="cde23-192">Installer avec l’automatisation bash</span><span class="sxs-lookup"><span data-stu-id="cde23-192">Install with bash automation</span></span>

<span data-ttu-id="cde23-193">Les [scripts d’installation de dotnet](../tools/dotnet-install-script.md) sont utilisés pour l’automatisation et les installations non admin du SDK.</span><span class="sxs-lookup"><span data-stu-id="cde23-193">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the SDK.</span></span> <span data-ttu-id="cde23-194">Vous pouvez télécharger le script à partir de la page de [référence de script dotnet-install](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="cde23-194">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="cde23-195">Le script par défaut à l’installation de la dernière [version de support à long terme (LTS),](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) qui est .NET Core 3.1.</span><span class="sxs-lookup"><span data-stu-id="cde23-195">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="cde23-196">Pour installer la version actuelle de .NET Core, exécutez le script avec le commutateur suivant.</span><span class="sxs-lookup"><span data-stu-id="cde23-196">To install the current release of .NET Core, run the script with the following switch.</span></span>

```bash
./dotnet-install.sh -c Current
```

::: zone-end

## <a name="all-net-core-downloads"></a><span data-ttu-id="cde23-197">Tous les téléchargements .NET Core</span><span class="sxs-lookup"><span data-stu-id="cde23-197">All .NET Core downloads</span></span>

<span data-ttu-id="cde23-198">Vous pouvez télécharger et installer .NET Core directement avec l’un des liens suivants:</span><span class="sxs-lookup"><span data-stu-id="cde23-198">You can download and install .NET Core directly with one of the following links:</span></span>

- [<span data-ttu-id="cde23-199">.NET Core 3.1 téléchargements</span><span class="sxs-lookup"><span data-stu-id="cde23-199">.NET Core 3.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="cde23-200">.NET Core 3.0 téléchargements</span><span class="sxs-lookup"><span data-stu-id="cde23-200">.NET Core 3.0 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- [<span data-ttu-id="cde23-201">.NET Core 2.2 téléchargements</span><span class="sxs-lookup"><span data-stu-id="cde23-201">.NET Core 2.2 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- [<span data-ttu-id="cde23-202">.NET Core 2.1 téléchargements</span><span class="sxs-lookup"><span data-stu-id="cde23-202">.NET Core 2.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a><span data-ttu-id="cde23-203">Docker</span><span class="sxs-lookup"><span data-stu-id="cde23-203">Docker</span></span>

<span data-ttu-id="cde23-204">Les conteneurs fournissent un moyen léger d’isoler votre application du reste du système hôte.</span><span class="sxs-lookup"><span data-stu-id="cde23-204">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="cde23-205">Les conteneurs de la même machine ne partagent que le noyau et utilisent les ressources données à votre application.</span><span class="sxs-lookup"><span data-stu-id="cde23-205">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="cde23-206">.NET Core peut fonctionner dans un conteneur Docker.</span><span class="sxs-lookup"><span data-stu-id="cde23-206">.NET Core can run in a Docker container.</span></span> <span data-ttu-id="cde23-207">Les images Docker .NET Core officielles sont publiées dans Microsoft Container Registry (MCR) et détectables dans le [référentiel Docker Hub Microsoft .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/).</span><span class="sxs-lookup"><span data-stu-id="cde23-207">Official .NET Core Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span> <span data-ttu-id="cde23-208">Chaque référentiel contient des images pour différentes combinaisons possibles de .NET (kit de développement logiciel ou runtime) et du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="cde23-208">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="cde23-209">Microsoft fournit des images adaptées à des scénarios particuliers.</span><span class="sxs-lookup"><span data-stu-id="cde23-209">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="cde23-210">Par exemple, celles du [référentiel ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) sont conçues pour exécuter des applications ASP.NET Core en production.</span><span class="sxs-lookup"><span data-stu-id="cde23-210">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="cde23-211">Pour plus d’informations sur l’utilisation de .NET Core dans un conteneur Docker, voir [Introduction à .NET et Docker](../docker/introduction.md) et [Échantillons](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span><span class="sxs-lookup"><span data-stu-id="cde23-211">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="cde23-212">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="cde23-212">Next steps</span></span>

::: zone pivot="os-windows"

- <span data-ttu-id="cde23-213">[Tutorial: Bonjour World tutoriel](../tutorials/with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="cde23-213">[Tutorial: Hello World tutorial](../tutorials/with-visual-studio.md).</span></span>
- <span data-ttu-id="cde23-214">[Tutorial: Créer une nouvelle application avec Visual Studio Code](../tutorials/with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="cde23-214">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="cde23-215">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span><span class="sxs-lookup"><span data-stu-id="cde23-215">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end

::: zone pivot="os-macos"

- <span data-ttu-id="cde23-216">[Travailler avec macOS Catalina notarisation](macos-notarization-issues.md).</span><span class="sxs-lookup"><span data-stu-id="cde23-216">[Working with macOS Catalina notarization](macos-notarization-issues.md).</span></span>
- <span data-ttu-id="cde23-217">[Tutorial: Démarrer sur macOS](../tutorials/using-on-mac-vs.md).</span><span class="sxs-lookup"><span data-stu-id="cde23-217">[Tutorial: Get started on macOS](../tutorials/using-on-mac-vs.md).</span></span>
- <span data-ttu-id="cde23-218">[Tutorial: Créer une nouvelle application avec Visual Studio Code](../tutorials/with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="cde23-218">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="cde23-219">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span><span class="sxs-lookup"><span data-stu-id="cde23-219">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end

::: zone pivot="os-linux"

- <span data-ttu-id="cde23-220">[Tutorial: Créer une nouvelle application avec Visual Studio Code](../tutorials/with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="cde23-220">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="cde23-221">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span><span class="sxs-lookup"><span data-stu-id="cde23-221">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end
