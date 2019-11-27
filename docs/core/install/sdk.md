---
title: Installer kit SDK .NET Core sur Windows, Linux et macOS-.NET Core
description: Découvrez comment installer .NET Core sur Windows, Linux et macOS. Découvrez les dépendances requises pour développer des applications .NET Core.
author: thraka
ms.author: adegeo
ms.date: 11/06/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 2f65e9dc39a4cd1076af1a70dfedfa671f20b42d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450876"
---
# <a name="install-the-net-core-sdk"></a><span data-ttu-id="8dc6e-104">Installer le kit SDK .NET Core</span><span class="sxs-lookup"><span data-stu-id="8dc6e-104">Install the .NET Core SDK</span></span>

<span data-ttu-id="8dc6e-105">Dans cet article, vous allez apprendre à installer le kit SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8dc6e-105">In this article, you'll learn how to install the .NET Core SDK.</span></span> <span data-ttu-id="8dc6e-106">Le kit SDK .NET Core est utilisé pour créer des applications et des bibliothèques .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8dc6e-106">The .NET Core SDK is used to create .NET Core apps and libraries.</span></span> <span data-ttu-id="8dc6e-107">Le Runtime .NET Core est toujours installé avec le kit de développement logiciel (SDK).</span><span class="sxs-lookup"><span data-stu-id="8dc6e-107">The .NET Core runtime is always installed with the SDK.</span></span>

<span data-ttu-id="8dc6e-108">Vous pouvez télécharger et installer .NET Core directement avec l’un des liens suivants :</span><span class="sxs-lookup"><span data-stu-id="8dc6e-108">You can download and install .NET Core directly with one of the following links:</span></span>

- [<span data-ttu-id="8dc6e-109">Téléchargements .NET Core 3,1 Preview 3</span><span class="sxs-lookup"><span data-stu-id="8dc6e-109">.NET Core 3.1 Preview 3 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="8dc6e-110">Téléchargements .NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="8dc6e-110">.NET Core 3.0 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- [<span data-ttu-id="8dc6e-111">Téléchargements .NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="8dc6e-111">.NET Core 2.2 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- [<span data-ttu-id="8dc6e-112">Téléchargements .NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="8dc6e-112">.NET Core 2.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.1)

<span data-ttu-id="8dc6e-113">Vous pouvez également installer .NET Core dans le cadre d’un environnement de développement intégré (IDE), détaillé dans les sections ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="8dc6e-113">You can also install .NET Core as part of an integrated development environment (IDE), detailed in the sections below.</span></span>

## <a name="install-with-an-installer"></a><span data-ttu-id="8dc6e-114">Installer avec un programme d’installation</span><span class="sxs-lookup"><span data-stu-id="8dc6e-114">Install with an installer</span></span>

<span data-ttu-id="8dc6e-115">Windows et macOS ont tous deux des programmes d’installation autonomes qui peuvent être utilisés pour installer le kit de développement logiciel (SDK) .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="8dc6e-115">Both Windows and macOS have standalone installers that can be used to install the .NET Core 3.0 SDK.</span></span>

- <span data-ttu-id="8dc6e-116">UC Windows [x64](https://dotnet.microsoft.com/download/thank-you/dotnet-sdk-3.0.100-windows-x64-installer) | [UC x32](https://dotnet.microsoft.com/download/thank-you/dotnet-sdk-3.0.100-windows-x86-installer)</span><span class="sxs-lookup"><span data-stu-id="8dc6e-116">Windows [x64 CPUs](https://dotnet.microsoft.com/download/thank-you/dotnet-sdk-3.0.100-windows-x64-installer) | [x32 CPUs](https://dotnet.microsoft.com/download/thank-you/dotnet-sdk-3.0.100-windows-x86-installer)</span></span>
- <span data-ttu-id="8dc6e-117">[processeurs MacOS x64](https://dotnet.microsoft.com/download/thank-you/dotnet-sdk-3.0.100-macos-x64-installer)</span><span class="sxs-lookup"><span data-stu-id="8dc6e-117">macOS [x64 CPUs](https://dotnet.microsoft.com/download/thank-you/dotnet-sdk-3.0.100-macos-x64-installer)</span></span>

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a><span data-ttu-id="8dc6e-118">Installer avec un gestionnaire de package</span><span class="sxs-lookup"><span data-stu-id="8dc6e-118">Install with a package manager</span></span>

<span data-ttu-id="8dc6e-119">Vous pouvez installer les kit SDK .NET Core avec un grand nombre de gestionnaires de packages Linux courants.</span><span class="sxs-lookup"><span data-stu-id="8dc6e-119">You can install the .NET Core SDK with many of the common Linux package managers.</span></span> <span data-ttu-id="8dc6e-120">Pour plus d’informations, consultez [Linux Package Manager-install .net Core](linux-package-manager-rhel7.md).</span><span class="sxs-lookup"><span data-stu-id="8dc6e-120">For more information, see [Linux Package Manager - Install .NET Core](linux-package-manager-rhel7.md).</span></span>

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-visual-studio"></a><span data-ttu-id="8dc6e-121">Installer avec Visual Studio</span><span class="sxs-lookup"><span data-stu-id="8dc6e-121">Install with Visual Studio</span></span>

<span data-ttu-id="8dc6e-122">Si vous utilisez Visual Studio pour développer des applications .NET Core, le tableau suivant décrit la version minimale requise de Visual Studio en fonction de la version de kit SDK .NET Core cible.</span><span class="sxs-lookup"><span data-stu-id="8dc6e-122">If you're using Visual Studio to develop .NET Core apps, the following table describes the minimum required version of Visual Studio based on the target .NET Core SDK version.</span></span>

| <span data-ttu-id="8dc6e-123">Version de kit SDK .NET Core</span><span class="sxs-lookup"><span data-stu-id="8dc6e-123">.NET Core SDK version</span></span> | <span data-ttu-id="8dc6e-124">Version de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="8dc6e-124">Visual Studio version</span></span>                      |
| --------------------- | ------------------------------------------ |
| <span data-ttu-id="8dc6e-125">3,0</span><span class="sxs-lookup"><span data-stu-id="8dc6e-125">3.0</span></span>                   | <span data-ttu-id="8dc6e-126">Visual Studio 2019 version 16,3 ou ultérieure.</span><span class="sxs-lookup"><span data-stu-id="8dc6e-126">Visual Studio 2019 version 16.3 or higher.</span></span> |
| <span data-ttu-id="8dc6e-127">2.2</span><span class="sxs-lookup"><span data-stu-id="8dc6e-127">2.2</span></span>                   | <span data-ttu-id="8dc6e-128">Visual Studio 2017 version 15,9 ou ultérieure.</span><span class="sxs-lookup"><span data-stu-id="8dc6e-128">Visual Studio 2017 version 15.9 or higher.</span></span> |
| <span data-ttu-id="8dc6e-129">2.1</span><span class="sxs-lookup"><span data-stu-id="8dc6e-129">2.1</span></span>                   | <span data-ttu-id="8dc6e-130">Visual Studio 2017 version 15,7 ou ultérieure.</span><span class="sxs-lookup"><span data-stu-id="8dc6e-130">Visual Studio 2017 version 15.7 or higher.</span></span> |

<span data-ttu-id="8dc6e-131">Si vous avez déjà installé Visual Studio, vous pouvez vérifier votre version en procédant comme suit.</span><span class="sxs-lookup"><span data-stu-id="8dc6e-131">If you already have Visual Studio installed, you can check your version with the following steps.</span></span>

01. <span data-ttu-id="8dc6e-132">Ouvrez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8dc6e-132">Open Visual Studio.</span></span>
01. <span data-ttu-id="8dc6e-133">Sélectionnez **aide** > **à propos de Microsoft Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="8dc6e-133">Select **Help** > **About Microsoft Visual Studio**.</span></span>
01. <span data-ttu-id="8dc6e-134">Lisez le numéro de version dans la boîte de dialogue **à propos** de.</span><span class="sxs-lookup"><span data-stu-id="8dc6e-134">Read the version number from the **About** dialog.</span></span>

<span data-ttu-id="8dc6e-135">Visual Studio peut installer les kit SDK .NET Core et Runtime les plus récents.</span><span class="sxs-lookup"><span data-stu-id="8dc6e-135">Visual Studio can install the latest .NET Core SDK and runtime.</span></span>

- <span data-ttu-id="8dc6e-136">[Téléchargez Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span><span class="sxs-lookup"><span data-stu-id="8dc6e-136">[Download Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span></span>

### <a name="select-a-workload"></a><span data-ttu-id="8dc6e-137">Sélectionner une charge de travail</span><span class="sxs-lookup"><span data-stu-id="8dc6e-137">Select a workload</span></span>

<span data-ttu-id="8dc6e-138">Lors de l’installation ou de la modification de Visual Studio, sélectionnez l’une des charges de travail suivantes, selon le type d’application que vous créez :</span><span class="sxs-lookup"><span data-stu-id="8dc6e-138">When installing or modifying Visual Studio, select one of the following workloads, depending on the kind of application you're building:</span></span>

- <span data-ttu-id="8dc6e-139">La charge de travail **développement multiplateforme .net Core** dans la section **autres ensembles d’outils** .</span><span class="sxs-lookup"><span data-stu-id="8dc6e-139">The **.NET Core cross-platform development** workload in the **Other Toolsets** section.</span></span>
- <span data-ttu-id="8dc6e-140">La charge de travail **ASP.net et développement Web** dans la section **Web & Cloud** .</span><span class="sxs-lookup"><span data-stu-id="8dc6e-140">The **ASP.NET and web development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="8dc6e-141">La charge de travail **développement Azure** dans la section **Web & Cloud** .</span><span class="sxs-lookup"><span data-stu-id="8dc6e-141">The **Azure development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="8dc6e-142">La charge de travail **développement .net Desktop** dans la section **Desktop & mobile** .</span><span class="sxs-lookup"><span data-stu-id="8dc6e-142">The **.NET desktop development** workload in the **Desktop & Mobile** section.</span></span>

<span data-ttu-id="8dc6e-143">[![Windows Visual Studio 2019 avec charge de travail .NET Core](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="8dc6e-143">[![Windows Visual Studio 2019 with .NET Core workload](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span></span>

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-visual-studio-for-mac"></a><span data-ttu-id="8dc6e-144">Installer avec Visual Studio pour Mac</span><span class="sxs-lookup"><span data-stu-id="8dc6e-144">Install with Visual Studio for Mac</span></span>

<span data-ttu-id="8dc6e-145">Visual Studio pour Mac installe le kit SDK .NET Core lorsque la charge de travail **.net Core** est sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="8dc6e-145">Visual Studio for Mac installs the .NET Core SDK when the **.NET Core** workload is selected.</span></span> <span data-ttu-id="8dc6e-146">Pour commencer à utiliser le développement .NET Core sur macOS, consultez [installer Visual Studio 2019 pour Mac](/visualstudio/mac/installation).</span><span class="sxs-lookup"><span data-stu-id="8dc6e-146">To get started with .NET Core development on macOS, see [Install Visual Studio 2019 for Mac](/visualstudio/mac/installation).</span></span>

<span data-ttu-id="8dc6e-147">[![la fonctionnalité de charge de travail de Visual Studio 2019 pour Mac macOS avec .NET Core](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="8dc6e-147">[![macOS Visual Studio 2019 for Mac with .NET Core workload feature](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span></span>

::: zone-end

## <a name="install-from-visual-studio-code"></a><span data-ttu-id="8dc6e-148">Installer à partir de Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="8dc6e-148">Install from Visual Studio Code</span></span>

<span data-ttu-id="8dc6e-149">Visual Studio Code est un éditeur de code source puissant et léger qui s’exécute sur votre bureau.</span><span class="sxs-lookup"><span data-stu-id="8dc6e-149">Visual Studio Code is a powerful and lightweight source code editor that runs on your desktop.</span></span> <span data-ttu-id="8dc6e-150">Visual Studio Code est disponible pour Windows, macOS et Linux.</span><span class="sxs-lookup"><span data-stu-id="8dc6e-150">Visual Studio Code is available for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="8dc6e-151">Même si Visual Studio Code n’est pas fourni avec la prise en charge de .NET Core, l’ajout de la prise en charge de .NET Core est simple.</span><span class="sxs-lookup"><span data-stu-id="8dc6e-151">While Visual Studio Code doesn't come with .NET Core support, adding .NET Core support is simple.</span></span>

01. <span data-ttu-id="8dc6e-152">[Téléchargez et installez Visual Studio code](https://code.visualstudio.com/Download).</span><span class="sxs-lookup"><span data-stu-id="8dc6e-152">[Download and install Visual Studio Code](https://code.visualstudio.com/Download).</span></span>
01. <span data-ttu-id="8dc6e-153">[Téléchargez et installez le kit SDK .net Core](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span><span class="sxs-lookup"><span data-stu-id="8dc6e-153">[Download and install the .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span></span>
01. <span data-ttu-id="8dc6e-154">[Installez l' C# extension à partir de la place de marché Visual Studio code](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp).</span><span class="sxs-lookup"><span data-stu-id="8dc6e-154">[Install the C# extension from the Visual Studio Code marketplace](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp).</span></span>

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a><span data-ttu-id="8dc6e-155">Installer avec l’automatisation PowerShell</span><span class="sxs-lookup"><span data-stu-id="8dc6e-155">Install with PowerShell automation</span></span>

<span data-ttu-id="8dc6e-156">Les [scripts dotnet-install](../tools/dotnet-install-script.md) sont utilisés pour l’automatisation et les installations non administratives du kit de développement logiciel (SDK).</span><span class="sxs-lookup"><span data-stu-id="8dc6e-156">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the SDK.</span></span> <span data-ttu-id="8dc6e-157">Vous pouvez télécharger le script à partir de la [page de référence du script dotnet-install](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="8dc6e-157">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="8dc6e-158">Par défaut, le script installe la dernière version de [support à long terme (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , qui est .net Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="8dc6e-158">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 2.1.</span></span> <span data-ttu-id="8dc6e-159">Pour installer la version actuelle de .NET Core, exécutez le script avec le commutateur suivant.</span><span class="sxs-lookup"><span data-stu-id="8dc6e-159">To install the current release of .NET Core, run the script with the following switch.</span></span>

```powershell
dotnet-install.ps1 -Channel Current
```

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a><span data-ttu-id="8dc6e-160">Installer avec l’automatisation bash</span><span class="sxs-lookup"><span data-stu-id="8dc6e-160">Install with bash automation</span></span>

<span data-ttu-id="8dc6e-161">Les [scripts dotnet-install](../tools/dotnet-install-script.md) sont utilisés pour l’automatisation et les installations non administratives du kit de développement logiciel (SDK).</span><span class="sxs-lookup"><span data-stu-id="8dc6e-161">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the SDK.</span></span> <span data-ttu-id="8dc6e-162">Vous pouvez télécharger le script à partir de la [page de référence du script dotnet-install](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="8dc6e-162">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="8dc6e-163">Par défaut, le script installe la dernière version de [support à long terme (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , qui est .net Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="8dc6e-163">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 2.1.</span></span> <span data-ttu-id="8dc6e-164">Pour installer la version actuelle de .NET Core, exécutez le script avec le commutateur suivant.</span><span class="sxs-lookup"><span data-stu-id="8dc6e-164">To install the current release of .NET Core, run the script with the following switch.</span></span>

```bash
./dotnet-install.sh -c Current
```

::: zone-end

## <a name="docker"></a><span data-ttu-id="8dc6e-165">Docker</span><span class="sxs-lookup"><span data-stu-id="8dc6e-165">Docker</span></span>

<span data-ttu-id="8dc6e-166">Les conteneurs offrent un moyen léger d’isoler votre application du reste du système hôte.</span><span class="sxs-lookup"><span data-stu-id="8dc6e-166">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="8dc6e-167">Les conteneurs sur le même ordinateur partagent simplement le noyau et utilisent les ressources fournies à votre application.</span><span class="sxs-lookup"><span data-stu-id="8dc6e-167">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="8dc6e-168">.NET Core peut s’exécuter dans un conteneur d’ancrage.</span><span class="sxs-lookup"><span data-stu-id="8dc6e-168">.NET Core can run in a Docker container.</span></span> <span data-ttu-id="8dc6e-169">Les images Docker .NET Core officielles sont publiées dans Microsoft Container Registry (MCR) et détectables dans le [référentiel Docker Hub Microsoft .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/).</span><span class="sxs-lookup"><span data-stu-id="8dc6e-169">Official .NET Core Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span> <span data-ttu-id="8dc6e-170">Chaque référentiel contient des images pour différentes combinaisons possibles de .NET (kit de développement logiciel ou runtime) et du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="8dc6e-170">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="8dc6e-171">Microsoft fournit des images adaptées à des scénarios particuliers.</span><span class="sxs-lookup"><span data-stu-id="8dc6e-171">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="8dc6e-172">Par exemple, celles du [référentiel ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) sont conçues pour exécuter des applications ASP.NET Core en production.</span><span class="sxs-lookup"><span data-stu-id="8dc6e-172">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="8dc6e-173">Pour plus d’informations sur l’utilisation de .NET Core dans un conteneur d’ancrage, consultez [Introduction à .net et à l’ancreur](../docker/introduction.md) et aux [exemples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span><span class="sxs-lookup"><span data-stu-id="8dc6e-173">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="8dc6e-174">Étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="8dc6e-174">Next steps</span></span>

::: zone pivot="os-windows"

- <span data-ttu-id="8dc6e-175">[Didacticiel : C# Hello World didacticiel](../tutorials/with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="8dc6e-175">[Tutorial: C# Hello World tutorial](../tutorials/with-visual-studio.md).</span></span>
- <span data-ttu-id="8dc6e-176">[Didacticiel : Visual Basic Hello World didacticiel](../tutorials/vb-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="8dc6e-176">[Tutorial: Visual Basic Hello World tutorial](../tutorials/vb-with-visual-studio.md).</span></span>
- <span data-ttu-id="8dc6e-177">[Didacticiel : créer une application avec Visual Studio code](https://code.visualstudio.com/docs/languages/dotnet).</span><span class="sxs-lookup"><span data-stu-id="8dc6e-177">[Tutorial: Create a new app with Visual Studio Code](https://code.visualstudio.com/docs/languages/dotnet).</span></span>
- <span data-ttu-id="8dc6e-178">[Didacticiel : conteneur d’une application .net Core](../docker/build-container.md).</span><span class="sxs-lookup"><span data-stu-id="8dc6e-178">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end

::: zone pivot="os-macos"

- <span data-ttu-id="8dc6e-179">[Didacticiel : prise en main de MacOS](../tutorials/using-on-mac-vs.md).</span><span class="sxs-lookup"><span data-stu-id="8dc6e-179">[Tutorial: Get started on macOS](../tutorials/using-on-mac-vs.md).</span></span>
- <span data-ttu-id="8dc6e-180">[Didacticiel : créer une application avec Visual Studio code](https://code.visualstudio.com/docs/languages/dotnet).</span><span class="sxs-lookup"><span data-stu-id="8dc6e-180">[Tutorial: Create a new app with Visual Studio Code](https://code.visualstudio.com/docs/languages/dotnet).</span></span>
- <span data-ttu-id="8dc6e-181">[Didacticiel : conteneur d’une application .net Core](../docker/build-container.md).</span><span class="sxs-lookup"><span data-stu-id="8dc6e-181">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end
