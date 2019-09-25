---
title: Configuration requise pour .NET Core sur Windows
description: Découvrez les dépendances nécessaires sur votre machine Windows pour développer et exécuter des applications .NET Core.
f1_keywords:
- NETSDK1045
ms.custom: updateeachvsrelease
ms.date: 09/20/2019
ms.openlocfilehash: c46a1f12ca20c0e21ee205e409a2a5a89e3389b3
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71214548"
---
# <a name="prerequisites-for-net-core-on-windows"></a><span data-ttu-id="995ec-103">Configuration requise pour .NET Core sur Windows</span><span class="sxs-lookup"><span data-stu-id="995ec-103">Prerequisites for .NET Core on Windows</span></span>

<span data-ttu-id="995ec-104">Cet article présente les versions de système d’exploitation prises en charge pour exécuter des applications .NET Core sur Windows.</span><span class="sxs-lookup"><span data-stu-id="995ec-104">This article shows the supported OS versions in order to run .NET Core applications on Windows.</span></span> <span data-ttu-id="995ec-105">Les versions de système d’exploitation et les dépendances prises en charge ci-après s’appliquent aux trois façons de développer des applications .NET Core sur Windows :</span><span class="sxs-lookup"><span data-stu-id="995ec-105">The supported OS versions and dependencies that follow apply to the three ways of developing .NET Core apps on Windows:</span></span>

* [<span data-ttu-id="995ec-106">Ligne de commande</span><span class="sxs-lookup"><span data-stu-id="995ec-106">Command line</span></span>](./tutorials/using-with-xplat-cli.md)
* [<span data-ttu-id="995ec-107">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="995ec-107">Visual Studio</span></span>](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019)
* [<span data-ttu-id="995ec-108">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="995ec-108">Visual Studio Code</span></span>](https://code.visualstudio.com/)

<span data-ttu-id="995ec-109">En outre, si vous développez sur Windows à l’aide de Visual Studio, la section [conditions préalables au développement d’applications .net core avec Visual Studio](#prerequisites-to-develop-net-core-apps-with-visual-studio) est plus détaillée sur les versions minimales prises en charge pour le développement .net core.</span><span class="sxs-lookup"><span data-stu-id="995ec-109">Also, if you're developing on Windows using Visual Studio, the [Prerequisites to develop .NET Core apps with Visual Studio](#prerequisites-to-develop-net-core-apps-with-visual-studio) section goes in more detail about minimum versions supported for .NET Core development.</span></span>

## <a name="net-core-supported-operating-systems"></a><span data-ttu-id="995ec-110">Systèmes d’exploitation pris en charge par .NET Core</span><span class="sxs-lookup"><span data-stu-id="995ec-110">.NET Core supported operating systems</span></span>

<span data-ttu-id="995ec-111">Les articles suivants dressent la liste complète des systèmes d’exploitation .NET Core pris en charge par version :</span><span class="sxs-lookup"><span data-stu-id="995ec-111">The following articles have a complete list of .NET Core supported operating systems per version:</span></span>

* [<span data-ttu-id="995ec-112">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="995ec-112">.NET Core 3.0</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md)
* [<span data-ttu-id="995ec-113">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="995ec-113">.NET Core 2.2</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md)
* [<span data-ttu-id="995ec-114">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="995ec-114">.NET Core 2.1</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)
* [<span data-ttu-id="995ec-115">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="995ec-115">.NET Core 1.0</span></span>](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md)

<span data-ttu-id="995ec-116">Pour obtenir des liens de téléchargement et plus d’informations, consultez [Téléchargements .NET](https://dotnet.microsoft.com/download) afin de télécharger la version la plus récente ou [Archive des téléchargements .NET](https://dotnet.microsoft.com/download/archives#dotnet-core) pour les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="995ec-116">For download links and more information, see [.NET downloads](https://dotnet.microsoft.com/download) to download the latest version or [.NET downloads archive](https://dotnet.microsoft.com/download/archives#dotnet-core) for older versions.</span></span>

## <a name="net-core-dependencies"></a><span data-ttu-id="995ec-117">Dépendances .NET Core</span><span class="sxs-lookup"><span data-stu-id="995ec-117">.NET Core dependencies</span></span>

<span data-ttu-id="995ec-118">.NET Core 1.1 et ses versions antérieures nécessitent le package redistribuable Visual C++ lors de l’exécution sur des versions de Windows antérieures à Windows 10 et Windows Server 2016.</span><span class="sxs-lookup"><span data-stu-id="995ec-118">.NET Core 1.1 and earlier versions require the Visual C++ Redistributable when running on Windows versions earlier than Windows 10 and Windows Server 2016.</span></span> <span data-ttu-id="995ec-119">Cette dépendance est installée automatiquement par le programme d’installation de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="995ec-119">This dependency is automatically installed by the .NET Core installer.</span></span>

<span data-ttu-id="995ec-120">Vous devez installer [Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685) manuellement quand :</span><span class="sxs-lookup"><span data-stu-id="995ec-120">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685) must be manually installed when:</span></span>

* <span data-ttu-id="995ec-121">vous installez .NET Core avec le [script du programme d’installation](./tools/dotnet-install-script.md) ;</span><span class="sxs-lookup"><span data-stu-id="995ec-121">Installing .NET Core with the [installer script](./tools/dotnet-install-script.md).</span></span>
* <span data-ttu-id="995ec-122">vous déployez une application .NET Core autonome.</span><span class="sxs-lookup"><span data-stu-id="995ec-122">Deploying a self-contained .NET Core application.</span></span>
* <span data-ttu-id="995ec-123">Génération du produit à partir de la source.</span><span class="sxs-lookup"><span data-stu-id="995ec-123">Building the product from source.</span></span>
* <span data-ttu-id="995ec-124">Installation de .NET Core via un fichier *.zip*.</span><span class="sxs-lookup"><span data-stu-id="995ec-124">Installing .NET Core via a *.zip* file.</span></span> <span data-ttu-id="995ec-125">Ceci peut inclure des serveurs de builds/CI/CD.</span><span class="sxs-lookup"><span data-stu-id="995ec-125">This can include build/CI/CD servers.</span></span>

> [!NOTE]
> <span data-ttu-id="995ec-126">**Pour Windows 8.1 et versions antérieures, ou Windows Server 2012 R2 et versions antérieures :**</span><span class="sxs-lookup"><span data-stu-id="995ec-126">**For Windows 8.1 and earlier versions, or Windows Server 2012 R2 and earlier versions:**</span></span>
>
> <span data-ttu-id="995ec-127">Vérifiez que votre installation Windows est à jour et comprend le correctif logiciel [KB2999226](https://support.microsoft.com/help/2999226/update-for-universal-c-runtime-in-windows), installable via Windows Update.</span><span class="sxs-lookup"><span data-stu-id="995ec-127">Make sure that your Windows installation is up-to-date and includes [KB2999226](https://support.microsoft.com/help/2999226/update-for-universal-c-runtime-in-windows), which can be installed through Windows Update.</span></span> <span data-ttu-id="995ec-128">Si cette mise à jour n’est pas installée, quand vous lancez une application .NET Core, vous recevez une erreur semblable à celle-ci : `The program can't start because api-ms-win-crt-runtime-l1-1-0.dll is missing from your computer. Try reinstalling the program to fix this problem.`</span><span class="sxs-lookup"><span data-stu-id="995ec-128">If you don't have this update installed, you'll see an error like the following when you launch a .NET Core application: `The program can't start because api-ms-win-crt-runtime-l1-1-0.dll is missing from your computer. Try reinstalling the program to fix this problem.`</span></span>
>
> <span data-ttu-id="995ec-129">**Pour Windows 7 ou Windows Server 2008 R2 :**</span><span class="sxs-lookup"><span data-stu-id="995ec-129">**For Windows 7 or Windows Server 2008 R2:**</span></span>
>
> <span data-ttu-id="995ec-130">Outre KB2999226, vérifiez également que la mise à jour [KB2533623](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot) est installée.</span><span class="sxs-lookup"><span data-stu-id="995ec-130">In addition to KB2999226, make sure you also have [KB2533623](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot) installed.</span></span> <span data-ttu-id="995ec-131">Si cette mise à jour n’est pas installée, quand vous lancez une application .NET Core, vous recevez une erreur comme celle-ci : `The library hostfxr.dll was found, but loading it from C:\<path_to_app>\hostfxr.dll failed`.</span><span class="sxs-lookup"><span data-stu-id="995ec-131">If you don't have this update installed, you'll see an error similar to the following when you launch a .NET Core application: `The library hostfxr.dll was found, but loading it from C:\<path_to_app>\hostfxr.dll failed`.</span></span>

## <a name="prerequisites-to-develop-net-core-apps-with-visual-studio"></a><span data-ttu-id="995ec-132">Conditions préalables au développement d’applications .NET Core avec Visual Studio</span><span class="sxs-lookup"><span data-stu-id="995ec-132">Prerequisites to develop .NET Core apps with Visual Studio</span></span>
    
<span data-ttu-id="995ec-133">Même si vous pouvez utiliser n’importe quel éditeur pour développer des applications .NET Core à l’aide de l’kit SDK .NET Core, Visual Studio 2017 et versions ultérieures fournissent un environnement de développement intégré pour les applications .NET Core sur Windows.</span><span class="sxs-lookup"><span data-stu-id="995ec-133">Even though you can use any editor to develop .NET Core applications using the .NET Core SDK, Visual Studio 2017 and later versions provide an integrated development environment for .NET Core apps on Windows.</span></span>

<a name="vs-mapping"></a>

<span data-ttu-id="995ec-134">Une version minimale de Visual Studio est requise pour chaque version de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="995ec-134">Each .NET Core version has a minimum version of Visual Studio required.</span></span> <span data-ttu-id="995ec-135">Pour vérifier votre version de Visual Studio :</span><span class="sxs-lookup"><span data-stu-id="995ec-135">To verify your Visual Studio version:</span></span>

* <span data-ttu-id="995ec-136">Dans le menu **Aide**, choisissez **À propos de Microsoft Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="995ec-136">On the **Help** menu, choose **About Microsoft Visual Studio**.</span></span>
* <span data-ttu-id="995ec-137">Dans la boîte de dialogue **À propos de Microsoft Visual Studio**, vérifiez le numéro de version.</span><span class="sxs-lookup"><span data-stu-id="995ec-137">In the **About Microsoft Visual Studio** dialog, verify the version number.</span></span>

<span data-ttu-id="995ec-138">Le tableau suivant répertorie la version minimale pour chaque kit de développement logiciel (SDK) :</span><span class="sxs-lookup"><span data-stu-id="995ec-138">The following table lists the minimum version for each SDK:</span></span>

| <span data-ttu-id="995ec-139">Version de kit SDK .NET Core</span><span class="sxs-lookup"><span data-stu-id="995ec-139">.NET Core SDK version</span></span> | <span data-ttu-id="995ec-140">Version de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="995ec-140">Visual Studio version</span></span>                      |
| --------------------- | ------------------------------------------ |
| <span data-ttu-id="995ec-141">3.0</span><span class="sxs-lookup"><span data-stu-id="995ec-141">3.0</span></span>                   | <span data-ttu-id="995ec-142">Visual Studio 2019 version 16,3 ou ultérieure.</span><span class="sxs-lookup"><span data-stu-id="995ec-142">Visual Studio 2019 version 16.3 or higher.</span></span> |
| <span data-ttu-id="995ec-143">2.2</span><span class="sxs-lookup"><span data-stu-id="995ec-143">2.2</span></span>                   | <span data-ttu-id="995ec-144">Visual Studio 2017 version 15,9 ou ultérieure.</span><span class="sxs-lookup"><span data-stu-id="995ec-144">Visual Studio 2017 version 15.9 or higher.</span></span> |
| <span data-ttu-id="995ec-145">2.1</span><span class="sxs-lookup"><span data-stu-id="995ec-145">2.1</span></span>                   | <span data-ttu-id="995ec-146">Visual Studio 2017 version 15,7 ou ultérieure.</span><span class="sxs-lookup"><span data-stu-id="995ec-146">Visual Studio 2017 version 15.7 or higher.</span></span> |
| <span data-ttu-id="995ec-147">1.x</span><span class="sxs-lookup"><span data-stu-id="995ec-147">1.x</span></span>                   | <span data-ttu-id="995ec-148">Visual Studio 2017 version 15,0 ou ultérieure.</span><span class="sxs-lookup"><span data-stu-id="995ec-148">Visual Studio 2017 version 15.0 or higher.</span></span> |

<!-- markdownlint-disable MD025 -->

# <a name="net-core-30tabnetcore30"></a>[<span data-ttu-id="995ec-149">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="995ec-149">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="995ec-150">Pour développer des applications .NET Core dans Visual Studio 2019 à l’aide du kit de développement logiciel (SDK) .NET Core 3,0 :</span><span class="sxs-lookup"><span data-stu-id="995ec-150">To develop .NET Core apps in Visual Studio 2019 using the .NET Core 3.0 SDK:</span></span>

* <span data-ttu-id="995ec-151">[Téléchargez et installez Visual Studio 2019 version 16,3 ou ultérieure](/visualstudio/install/install-visual-studio) et sélectionnez l’une des charges de travail suivantes, qui comprend le kit SDK .net Core, selon le type d’application que vous créez :</span><span class="sxs-lookup"><span data-stu-id="995ec-151">[Download and install Visual Studio 2019 version 16.3 or higher](/visualstudio/install/install-visual-studio) and select one of the following workloads that includes the .NET Core SDK, depending on the kind of application you're building:</span></span>

  * <span data-ttu-id="995ec-152">La charge de travail **développement multiplateforme .net Core** dans la section **autres ensembles d’outils** .</span><span class="sxs-lookup"><span data-stu-id="995ec-152">The **.NET Core cross-platform development** workload in the **Other Toolsets** section.</span></span>
  * <span data-ttu-id="995ec-153">La charge de travail **ASP.net et développement Web** dans la section **Web & Cloud** .</span><span class="sxs-lookup"><span data-stu-id="995ec-153">The **ASP.NET and web development** workload in the **Web & Cloud** section.</span></span>
  * <span data-ttu-id="995ec-154">La charge de travail **développement net Desktop** dans la section **Windows** .</span><span class="sxs-lookup"><span data-stu-id="995ec-154">The **NET desktop development** workload in the **Windows** section.</span></span>

<span data-ttu-id="995ec-155">L’illustration suivante montre la charge de travail de **développement multiplateforme .net Core** sélectionnée dans l’interface utilisateur de Visual Studio :</span><span class="sxs-lookup"><span data-stu-id="995ec-155">The following image shows the **.NET Core cross-platform development** workload selected in the Visual Studio UI:</span></span>

![Capture d’écran de l’installation de Visual Studio 2019 avec la charge de travail « développement multiplateforme .NET Core » sélectionnée](./media/windows-prerequisites/vs-2019-workloads.jpg)

<span data-ttu-id="995ec-157">Visual Studio 2019 16,3 utilise le kit de développement logiciel (SDK) .NET Core 3,0 par défaut après l’installation de l’une de ces charges de travail.</span><span class="sxs-lookup"><span data-stu-id="995ec-157">Visual Studio 2019 16.3 uses .NET Core 3.0 SDK by default after any of these workloads are installed.</span></span>

<span data-ttu-id="995ec-158">Si vous souhaitez que vos projets existants utilisent la dernière version du Runtime .NET Core, reciblez chaque projet .NET Core existant vers .NET Core 3,0 à l’aide des instructions suivantes :</span><span class="sxs-lookup"><span data-stu-id="995ec-158">If you want your existing projects to use the latest .NET Core runtime, retarget each existing .NET Core project to .NET Core 3.0 using the following instructions:</span></span>

* <span data-ttu-id="995ec-159">Dans le menu **Projet** , choisissez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="995ec-159">On the **Project** menu, choose **Properties**.</span></span>
* <span data-ttu-id="995ec-160">Dans le menu de sélection du **Framework cible** , définissez la valeur sur **.net Core 3,0**.</span><span class="sxs-lookup"><span data-stu-id="995ec-160">In the **Target framework** selection menu, set the value to **.NET Core 3.0**.</span></span>

![Capture d’écran de la propriété de projet d’application Visual Studio 2019 avec l’élément de menu Framework cible « .NET Core 3,0 » sélectionné](./media/windows-prerequisites/target-dotnet-core-3-0.jpg)

<span data-ttu-id="995ec-162">Une fois que Visual Studio est configuré avec le kit de développement logiciel (SDK) .NET Core 3,0, vous pouvez effectuer les actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="995ec-162">Once you have Visual Studio configured with .NET Core 3.0 SDK, you can do the following actions:</span></span>

* <span data-ttu-id="995ec-163">Ouvrir, générer et exécuter les projets .NET Core 1.x et 2.x existants.</span><span class="sxs-lookup"><span data-stu-id="995ec-163">Open, build, and run existing .NET Core 1.x and 2.x projects.</span></span>
* <span data-ttu-id="995ec-164">Reciblez les projets .NET Core 1. x et 2. x vers .NET Core 3,0, générez et exécutez.</span><span class="sxs-lookup"><span data-stu-id="995ec-164">Retarget .NET Core 1.x and 2.x projects to .NET Core 3.0, build, and run.</span></span>
* <span data-ttu-id="995ec-165">Créez de nouveaux projets .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="995ec-165">Create new .NET Core 3.0 projects.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="995ec-166">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="995ec-166">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="995ec-167">Pour développer des applications .NET Core dans Visual Studio 2017 à l’aide du SDK .NET Core 2.2 :</span><span class="sxs-lookup"><span data-stu-id="995ec-167">To develop .NET Core apps in Visual Studio 2017 using the .NET Core 2.2 SDK:</span></span>

* <span data-ttu-id="995ec-168">[Téléchargez et installez Visual Studio 2017 version 15.9.0 ou version ultérieure](/visualstudio/install/install-visual-studio) en sélectionnant la charge de travail **Développement multiplateforme .NET Core** (dans la section **Autres ensembles d’outils**).</span><span class="sxs-lookup"><span data-stu-id="995ec-168">[Download and install Visual Studio 2017 version 15.9.0 or higher](/visualstudio/install/install-visual-studio) with the **.NET Core cross-platform development** workload (in the **Other Toolsets** section) selected.</span></span>

![Capture d’écran de l’installation de Visual Studio 2017 avec la charge de travail « Développement multiplateforme .NET Core » sélectionnée](./media/windows-prerequisites/vs-2017-workloads.jpg)

<span data-ttu-id="995ec-170">Une fois l’ensemble d’outils **Développement multiplateforme .NET Core** installé, Visual Studio installe généralement une version précédente du SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="995ec-170">After the **.NET Core cross-platform development** toolset is installed, Visual Studio usually installs a previous version of the .NET Core SDK.</span></span>
<span data-ttu-id="995ec-171">Par exemple, Visual Studio 2017 15.9 utilise par défaut le SDK .NET Core 2.1 après l’installation de la charge de travail.</span><span class="sxs-lookup"><span data-stu-id="995ec-171">For example, Visual Studio 2017 15.9 uses .NET Core 2.1 SDK by default after the workload is installed.</span></span>

<span data-ttu-id="995ec-172">Pour mettre à jour Visual Studio afin d’utiliser le SDK .NET Core 2.2 :</span><span class="sxs-lookup"><span data-stu-id="995ec-172">To update Visual Studio to use .NET Core 2.2 SDK:</span></span>

 1. <span data-ttu-id="995ec-173">Installez le [SDK .NET Core 2.2](https://dotnet.microsoft.com/download).</span><span class="sxs-lookup"><span data-stu-id="995ec-173">Install the [.NET Core 2.2 SDK](https://dotnet.microsoft.com/download).</span></span>

 1. <span data-ttu-id="995ec-174">Si vous souhaitez que votre projet utilise la dernière version du Runtime .NET Core, reciblez chaque projet .NET Core existant ou nouveau dans .NET Core 2,2 à l’aide des instructions suivantes :</span><span class="sxs-lookup"><span data-stu-id="995ec-174">If you want your project to use the latest .NET Core runtime, retarget each existing or new .NET Core project to .NET Core 2.2 using the following instructions:</span></span>

    * <span data-ttu-id="995ec-175">Dans le menu **Projet** , choisissez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="995ec-175">On the **Project** menu, choose **Properties**.</span></span>
    * <span data-ttu-id="995ec-176">Dans le menu de sélection du **framework cible**, choisissez **.NET Core 2.2**.</span><span class="sxs-lookup"><span data-stu-id="995ec-176">In the **Target framework** selection menu, set the value to **.NET Core 2.2**.</span></span>

![Capture d’écran de la propriété de projet Application Visual Studio 2017 avec définition de l’élément de menu framework cible sur « .NET Core 2.2 »](./media/windows-prerequisites/targeting-dotnet-core.jpg)

<span data-ttu-id="995ec-178">Une fois que vous avez configuré Visual Studio avec le SDK .NET Core 2.2, vous pouvez effectuer les actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="995ec-178">Once you have Visual Studio configured with .NET Core 2.2 SDK, you can do the following actions:</span></span>

* <span data-ttu-id="995ec-179">Ouvrir, générer et exécuter les projets .NET Core 1.x et 2.x existants.</span><span class="sxs-lookup"><span data-stu-id="995ec-179">Open, build, and run existing .NET Core 1.x and 2.x projects.</span></span>
* <span data-ttu-id="995ec-180">Recibler les projets .NET Core 1.x et 2.x vers .NET Core 2.2, les générer et les exécuter.</span><span class="sxs-lookup"><span data-stu-id="995ec-180">Retarget .NET Core 1.x and 2.x projects to .NET Core 2.2, build, and run.</span></span>
* <span data-ttu-id="995ec-181">Créer des projets .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="995ec-181">Create new .NET Core 2.2 projects.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="995ec-182">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="995ec-182">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="995ec-183">Pur développer des applications .NET Core 1.x dans Visual Studio, [téléchargez et installez Visual Studio 2017](/visualstudio/install/install-visual-studio) en sélectionnant la charge de travail **Développement multiplateforme .NET Core** (dans la section **Autres ensembles d’outils**).</span><span class="sxs-lookup"><span data-stu-id="995ec-183">To develop .NET Core 1.x apps in Visual Studio, [download and install Visual Studio 2017](/visualstudio/install/install-visual-studio) with the **".NET Core cross-platform development"** workload (in the **Other Toolsets** section) selected.</span></span>

![Capture d’écran de l’installation de Visual Studio 2017 avec la charge de travail « Développement multiplateforme .NET Core » sélectionnée](./media/windows-prerequisites/vs-workloads.jpg)

> [!IMPORTANT]
> <span data-ttu-id="995ec-185">Bien que vous puissiez utiliser Visual Studio 2015 pour le développement .NET Core 1.x, nous vous le déconseillons pour les raisons suivantes :</span><span class="sxs-lookup"><span data-stu-id="995ec-185">It's possible to use Visual Studio 2015 for .NET Core 1.x development, but it's not recommended for the following reasons:</span></span>
>
> * <span data-ttu-id="995ec-186">Les outils .NET Core sont une préversion, qui n’est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="995ec-186">The .NET Core tooling is a preview version, which is not supported.</span></span>
> * <span data-ttu-id="995ec-187">Les projets sont basés sur project.json, configuration qui est dépréciée.</span><span class="sxs-lookup"><span data-stu-id="995ec-187">The projects are project.json-based, which is deprecated.</span></span>
>
> <span data-ttu-id="995ec-188">Pour plus d’informations sur les changements de format de projet, consultez la page [Vue d’ensemble des modifications](./tools/cli-msbuild-architecture.md).</span><span class="sxs-lookup"><span data-stu-id="995ec-188">For more information about the project format changes, see [High-level overview of changes](./tools/cli-msbuild-architecture.md).</span></span>

---
