---
title: Configuration requise pour .NET Core sur Windows
description: Découvrez les dépendances nécessaires sur votre machine Windows pour développer et exécuter des applications .NET Core.
ms.custom: updateeachvsrelease
ms.date: 04/08/2019
ms.openlocfilehash: 9c4c15a08e0988955ecdf442307059868cb377d1
ms.sourcegitcommit: b5c59eaaf8bf48ef3ec259f228cb328d6d4c0ceb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2019
ms.locfileid: "67539357"
---
# <a name="prerequisites-for-net-core-on-windows"></a><span data-ttu-id="e1ef9-103">Configuration requise pour .NET Core sur Windows</span><span class="sxs-lookup"><span data-stu-id="e1ef9-103">Prerequisites for .NET Core on Windows</span></span>

<span data-ttu-id="e1ef9-104">Cet article présente les versions de système d’exploitation prises en charge pour exécuter des applications .NET Core sur Windows.</span><span class="sxs-lookup"><span data-stu-id="e1ef9-104">This article shows the supported OS versions in order to run .NET Core applications on Windows.</span></span> <span data-ttu-id="e1ef9-105">Les versions de système d’exploitation et les dépendances prises en charge ci-après s’appliquent aux trois façons de développer des applications .NET Core sur Windows :</span><span class="sxs-lookup"><span data-stu-id="e1ef9-105">The supported OS versions and dependencies that follow apply to the three ways of developing .NET Core apps on Windows:</span></span>

* [<span data-ttu-id="e1ef9-106">Ligne de commande</span><span class="sxs-lookup"><span data-stu-id="e1ef9-106">Command line</span></span>](tutorials/using-with-xplat-cli.md)
* [<span data-ttu-id="e1ef9-107">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e1ef9-107">Visual Studio</span></span>](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)
* [<span data-ttu-id="e1ef9-108">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="e1ef9-108">Visual Studio Code</span></span>](https://code.visualstudio.com/)

<span data-ttu-id="e1ef9-109">De même, si vous développez sous Windows à l’aide de Visual Studio 2017, la section [Prérequis pour Visual Studio 2017](#prerequisites-with-visual-studio-2017) explore en détail les versions minimales prises en charge pour le développement .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e1ef9-109">Also, if you're developing on Windows using Visual Studio 2017, the [Prerequisites with Visual Studio 2017](#prerequisites-with-visual-studio-2017) section goes in more detail about minimum versions supported for .NET Core development.</span></span>

## <a name="net-core-supported-windows-versions"></a><span data-ttu-id="e1ef9-110">Versions Windows prises en charge par .NET Core</span><span class="sxs-lookup"><span data-stu-id="e1ef9-110">.NET Core supported Windows versions</span></span>

<span data-ttu-id="e1ef9-111">.NET Core est pris en charge par les versions suivantes de :</span><span class="sxs-lookup"><span data-stu-id="e1ef9-111">.NET Core is supported on the following versions of:</span></span>

* <span data-ttu-id="e1ef9-112">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="e1ef9-112">Windows 7 SP1</span></span>
* <span data-ttu-id="e1ef9-113">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="e1ef9-113">Windows 8.1</span></span>
* <span data-ttu-id="e1ef9-114">Mise à jour anniversaire Windows 10 (version 1607) ou ultérieur</span><span class="sxs-lookup"><span data-stu-id="e1ef9-114">Windows 10 Anniversary Update (version 1607) or later versions</span></span>
* <span data-ttu-id="e1ef9-115">Windows Server 2008 R2 SP1 (version complète ou Server Core)</span><span class="sxs-lookup"><span data-stu-id="e1ef9-115">Windows Server 2008 R2 SP1 (Full Server or Server Core)</span></span>
* <span data-ttu-id="e1ef9-116">Windows Server 2012 SP1 (version complète ou Server Core)</span><span class="sxs-lookup"><span data-stu-id="e1ef9-116">Windows Server 2012 SP1 (Full Server or Server Core)</span></span>
* <span data-ttu-id="e1ef9-117">Windows Server 2012 R2 (version complète ou Server Core)</span><span class="sxs-lookup"><span data-stu-id="e1ef9-117">Windows Server 2012 R2 (Full Server or Server Core)</span></span>
* <span data-ttu-id="e1ef9-118">Windows Server 2016 ou versions ultérieures (version complète, Server Core ou Nano Server)</span><span class="sxs-lookup"><span data-stu-id="e1ef9-118">Windows Server 2016 or later versions (Full Server, Server Core, or Nano Server)</span></span>

## <a name="net-core-supported-operating-systems"></a><span data-ttu-id="e1ef9-119">Systèmes d’exploitation pris en charge par .NET Core</span><span class="sxs-lookup"><span data-stu-id="e1ef9-119">.NET Core supported operating systems</span></span>

<span data-ttu-id="e1ef9-120">Les articles suivants dressent la liste complète des systèmes d’exploitation .NET Core pris en charge par version :</span><span class="sxs-lookup"><span data-stu-id="e1ef9-120">The following articles have a complete list of .NET Core supported operating systems per version:</span></span>

* [<span data-ttu-id="e1ef9-121">.NET Core 3.0 (préversion)</span><span class="sxs-lookup"><span data-stu-id="e1ef9-121">.NET Core 3.0 (Preview)</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md)
* [<span data-ttu-id="e1ef9-122">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="e1ef9-122">.NET Core 2.2</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md)
* [<span data-ttu-id="e1ef9-123">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="e1ef9-123">.NET Core 2.1</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)
* [<span data-ttu-id="e1ef9-124">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="e1ef9-124">.NET Core 1.0</span></span>](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md)

<span data-ttu-id="e1ef9-125">Pour obtenir des liens de téléchargement et plus d’informations, consultez [Téléchargements .NET](https://dotnet.microsoft.com/download) afin de télécharger la version la plus récente ou [Archive des téléchargements .NET](https://dotnet.microsoft.com/download/archives#dotnet-core) pour les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="e1ef9-125">For download links and more information, see [.NET downloads](https://dotnet.microsoft.com/download) to download the latest version or [.NET downloads archive](https://dotnet.microsoft.com/download/archives#dotnet-core) for older versions.</span></span>

## <a name="net-core-dependencies"></a><span data-ttu-id="e1ef9-126">Dépendances .NET Core</span><span class="sxs-lookup"><span data-stu-id="e1ef9-126">.NET Core dependencies</span></span>

<span data-ttu-id="e1ef9-127">.NET Core 1.1 et ses versions antérieures nécessitent le package redistribuable Visual C++ lors de l’exécution sur des versions de Windows antérieures à Windows 10 et Windows Server 2016.</span><span class="sxs-lookup"><span data-stu-id="e1ef9-127">.NET Core 1.1 and earlier versions require the Visual C++ Redistributable when running on Windows versions earlier than Windows 10 and Windows Server 2016.</span></span> <span data-ttu-id="e1ef9-128">Cette dépendance est installée automatiquement par le programme d’installation de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e1ef9-128">This dependency is automatically installed by the .NET Core installer.</span></span>

<span data-ttu-id="e1ef9-129">Vous devez installer [Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685) manuellement quand :</span><span class="sxs-lookup"><span data-stu-id="e1ef9-129">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685) must be manually installed when:</span></span>

* <span data-ttu-id="e1ef9-130">vous installez .NET Core avec le [script du programme d’installation](./tools/dotnet-install-script.md) ;</span><span class="sxs-lookup"><span data-stu-id="e1ef9-130">Installing .NET Core with the [installer script](./tools/dotnet-install-script.md).</span></span>
* <span data-ttu-id="e1ef9-131">vous déployez une application .NET Core autonome.</span><span class="sxs-lookup"><span data-stu-id="e1ef9-131">Deploying a self-contained .NET Core application.</span></span>
* <span data-ttu-id="e1ef9-132">Génération du produit à partir de la source.</span><span class="sxs-lookup"><span data-stu-id="e1ef9-132">Building the product from source.</span></span>
* <span data-ttu-id="e1ef9-133">Installation de .NET Core via un fichier *.zip*.</span><span class="sxs-lookup"><span data-stu-id="e1ef9-133">Installing .NET Core via a *.zip* file.</span></span> <span data-ttu-id="e1ef9-134">Ceci peut inclure des serveurs de builds/CI/CD.</span><span class="sxs-lookup"><span data-stu-id="e1ef9-134">This can include build/CI/CD servers.</span></span>

> [!NOTE]
> <span data-ttu-id="e1ef9-135">**Pour Windows 8.1 et versions antérieures, ou Windows Server 2012 R2 et versions antérieures :**</span><span class="sxs-lookup"><span data-stu-id="e1ef9-135">**For Windows 8.1 and earlier versions, or Windows Server 2012 R2 and earlier versions:**</span></span>
>
> <span data-ttu-id="e1ef9-136">Vérifiez que votre installation Windows est à jour et comprend le correctif logiciel [KB2999226](https://support.microsoft.com/help/2999226/update-for-universal-c-runtime-in-windows), installable via Windows Update.</span><span class="sxs-lookup"><span data-stu-id="e1ef9-136">Make sure that your Windows installation is up-to-date and includes [KB2999226](https://support.microsoft.com/help/2999226/update-for-universal-c-runtime-in-windows), which can be installed through Windows Update.</span></span> <span data-ttu-id="e1ef9-137">Si cette mise à jour n’est pas installée, quand vous lancez une application .NET Core, vous recevez une erreur semblable à celle-ci : `The program can't start because api-ms-win-crt-runtime-l1-1-0.dll is missing from your computer. Try reinstalling the program to fix this problem.`</span><span class="sxs-lookup"><span data-stu-id="e1ef9-137">If you don't have this update installed, you'll see an error like the following when you launch a .NET Core application: `The program can't start because api-ms-win-crt-runtime-l1-1-0.dll is missing from your computer. Try reinstalling the program to fix this problem.`</span></span>
>
> <span data-ttu-id="e1ef9-138">**Pour Windows 7 ou Windows Server 2008 R2 :**</span><span class="sxs-lookup"><span data-stu-id="e1ef9-138">**For Windows 7 or Windows Server 2008 R2:**</span></span>
>
> <span data-ttu-id="e1ef9-139">Outre KB2999226, vérifiez également que la mise à jour [KB2533623](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot) est installée.</span><span class="sxs-lookup"><span data-stu-id="e1ef9-139">In addition to KB2999226, make sure you also have [KB2533623](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot) installed.</span></span> <span data-ttu-id="e1ef9-140">Si cette mise à jour n’est pas installée, quand vous lancez une application .NET Core, vous recevez une erreur comme celle-ci : `The library hostfxr.dll was found, but loading it from C:\<path_to_app>\hostfxr.dll failed`.</span><span class="sxs-lookup"><span data-stu-id="e1ef9-140">If you don't have this update installed, you'll see an error similar to the following when you launch a .NET Core application: `The library hostfxr.dll was found, but loading it from C:\<path_to_app>\hostfxr.dll failed`.</span></span>

## <a name="prerequisites-for-net-core-30-preview-3"></a><span data-ttu-id="e1ef9-141">Configuration requise pour .NET Core 3.0 Preview 3</span><span class="sxs-lookup"><span data-stu-id="e1ef9-141">Prerequisites for .NET Core 3.0 Preview 3</span></span>

<span data-ttu-id="e1ef9-142">.NET Core 3.0 Preview 3 nécessite la même configuration que d’autres versions de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e1ef9-142">.NET Core 3.0 Preview 3 has the same prerequisites as other versions of .NET Core.</span></span> <span data-ttu-id="e1ef9-143">Toutefois, si vous souhaitez utiliser Visual Studio pour créer des projets .NET Core 3.0, vous devez utiliser [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019).</span><span class="sxs-lookup"><span data-stu-id="e1ef9-143">However, if you want to use Visual Studio to create .NET Core 3.0 projects, you must use the [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019).</span></span> <span data-ttu-id="e1ef9-144">Visual Studio 2019 peut être installée côte à côte avec d’autres versions de Visual Studio, sans générer de conflits.</span><span class="sxs-lookup"><span data-stu-id="e1ef9-144">Visual Studio 2019 can be installed side-by-side with other versions of Visual Studio without conflict.</span></span>

## <a name="prerequisites-with-visual-studio-2017"></a><span data-ttu-id="e1ef9-145">Prérequis pour Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="e1ef9-145">Prerequisites with Visual Studio 2017</span></span>
    
<span data-ttu-id="e1ef9-146">Vous pouvez utiliser l’éditeur de votre choix pour développer des applications .NET Core à l’aide du Kit SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e1ef9-146">You can use any editor to develop .NET Core applications using the .NET Core SDK.</span></span> <span data-ttu-id="e1ef9-147">Visual Studio 2017 fournit un environnement de développement intégré pour les applications .NET Core sur Windows.</span><span class="sxs-lookup"><span data-stu-id="e1ef9-147">Visual Studio 2017 provides an integrated development environment for .NET Core apps on Windows.</span></span>

<span data-ttu-id="e1ef9-148">Vous trouverez plus d’informations sur les modifications apportées à Visual Studio 2017 dans les [notes de publication](/visualstudio/releasenotes/vs2017-relnotes).</span><span class="sxs-lookup"><span data-stu-id="e1ef9-148">You can read more about the changes in Visual Studio 2017 in the [release notes](/visualstudio/releasenotes/vs2017-relnotes).</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="e1ef9-149">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="e1ef9-149">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="e1ef9-150">Pour développer des applications .NET Core dans Visual Studio 2017 à l’aide du SDK .NET Core 2.2 :</span><span class="sxs-lookup"><span data-stu-id="e1ef9-150">To develop .NET Core apps in Visual Studio 2017 using the .NET Core 2.2 SDK:</span></span>

 1. <span data-ttu-id="e1ef9-151">[Téléchargez et installez Visual Studio 2017 version 15.9.0 ou version ultérieure](/visualstudio/install/install-visual-studio) en sélectionnant la charge de travail **Développement multiplateforme .NET Core** (dans la section **Autres ensembles d’outils**).</span><span class="sxs-lookup"><span data-stu-id="e1ef9-151">[Download and install Visual Studio 2017 version 15.9.0 or higher](/visualstudio/install/install-visual-studio) with the **.NET Core cross-platform development** workload (in the **Other Toolsets** section) selected.</span></span>

![Capture d’écran de l’installation de Visual Studio 2017 avec la charge de travail « Développement multiplateforme .NET Core » sélectionnée](./media/windows-prerequisites/vs-2017-workloads.jpg)

<span data-ttu-id="e1ef9-153">Une fois l’ensemble d’outils **Développement multiplateforme .NET Core** installé, Visual Studio installe généralement une version précédente du SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e1ef9-153">After the **.NET Core cross-platform development** toolset is installed, Visual Studio usually installs a previous version of the .NET Core SDK.</span></span>
<span data-ttu-id="e1ef9-154">Par exemple, Visual Studio 2017 15.9 utilise par défaut le SDK .NET Core 2.1 après l’installation de la charge de travail.</span><span class="sxs-lookup"><span data-stu-id="e1ef9-154">For example, Visual Studio 2017 15.9 uses .NET Core 2.1 SDK by default after the workload is installed.</span></span>

<span data-ttu-id="e1ef9-155">Pour mettre à jour Visual Studio afin d’utiliser le SDK .NET Core 2.2 :</span><span class="sxs-lookup"><span data-stu-id="e1ef9-155">To update Visual Studio to use .NET Core 2.2 SDK:</span></span>

 1. <span data-ttu-id="e1ef9-156">Installez le [SDK .NET Core 2.2](https://dotnet.microsoft.com/download).</span><span class="sxs-lookup"><span data-stu-id="e1ef9-156">Install the [.NET Core 2.2 SDK](https://dotnet.microsoft.com/download).</span></span>

 1. <span data-ttu-id="e1ef9-157">Si vous souhaitez que votre projet utilise le runtime .NET Core le plus récent, reciblez les projets .NET Core existants ou nouveaux vers .NET Core 2.2 en suivant ces instructions :</span><span class="sxs-lookup"><span data-stu-id="e1ef9-157">If you want your project to use the latest .NET Core runtime, retarget existing or new .NET Core projects to .NET Core 2.2 using the following instructions:</span></span>

    * <span data-ttu-id="e1ef9-158">Dans le menu **Projet** , choisissez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="e1ef9-158">On the **Project** menu, choose **Properties**.</span></span>
    * <span data-ttu-id="e1ef9-159">Dans le menu de sélection du **framework cible**, choisissez **.NET Core 2.2**.</span><span class="sxs-lookup"><span data-stu-id="e1ef9-159">In the **Target framework** selection menu, set the value to **.NET Core 2.2**.</span></span>

![Capture d’écran de la propriété de projet Application Visual Studio 2017 avec définition de l’élément de menu framework cible sur « .NET Core 2.2 »](./media/windows-prerequisites/targeting-dotnet-core.jpg)

<span data-ttu-id="e1ef9-161">Une fois que vous avez configuré Visual Studio avec le SDK .NET Core 2.2, vous pouvez effectuer les actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="e1ef9-161">Once you have Visual Studio configured with .NET Core 2.2 SDK, you can do the following actions:</span></span>

* <span data-ttu-id="e1ef9-162">Ouvrir, générer et exécuter les projets .NET Core 1.x et 2.x existants.</span><span class="sxs-lookup"><span data-stu-id="e1ef9-162">Open, build, and run existing .NET Core 1.x and 2.x projects.</span></span>
* <span data-ttu-id="e1ef9-163">Recibler les projets .NET Core 1.x et 2.x vers .NET Core 2.2, les générer et les exécuter.</span><span class="sxs-lookup"><span data-stu-id="e1ef9-163">Retarget .NET Core 1.x and 2.x projects to .NET Core 2.2, build, and run.</span></span>
* <span data-ttu-id="e1ef9-164">Créer des projets .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="e1ef9-164">Create new .NET Core 2.2 projects.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="e1ef9-165">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="e1ef9-165">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="e1ef9-166">Pur développer des applications .NET Core 1.x dans Visual Studio, [téléchargez et installez Visual Studio 2017](/visualstudio/install/install-visual-studio) en sélectionnant la charge de travail **Développement multiplateforme .NET Core** (dans la section **Autres ensembles d’outils**).</span><span class="sxs-lookup"><span data-stu-id="e1ef9-166">To develop .NET Core 1.x apps in Visual Studio, [download and install Visual Studio 2017](/visualstudio/install/install-visual-studio) with the **".NET Core cross-platform development"** workload (in the **Other Toolsets** section) selected.</span></span>

![Capture d’écran de l’installation de Visual Studio 2017 avec la charge de travail « Développement multiplateforme .NET Core » sélectionnée](./media/windows-prerequisites/vs-workloads.jpg)

> [!IMPORTANT]
> <span data-ttu-id="e1ef9-168">Bien que vous puissiez utiliser Visual Studio 2015 pour le développement .NET Core 1.x, nous vous le déconseillons pour les raisons suivantes :</span><span class="sxs-lookup"><span data-stu-id="e1ef9-168">It's possible to use Visual Studio 2015 for .NET Core 1.x development, but it's not recommended for the following reasons:</span></span>
  > * <span data-ttu-id="e1ef9-169">Les outils .NET Core sont une préversion, qui n’est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="e1ef9-169">The .NET Core tooling is a preview version, which is not supported.</span></span>
  > * <span data-ttu-id="e1ef9-170">Les projets sont basés sur project.json, configuration qui est dépréciée.</span><span class="sxs-lookup"><span data-stu-id="e1ef9-170">The projects are project.json-based, which is deprecated.</span></span>
>
> <span data-ttu-id="e1ef9-171">Pour plus d’informations sur les changements de format de projet, consultez la page [Vue d’ensemble des modifications](./tools/cli-msbuild-architecture.md).</span><span class="sxs-lookup"><span data-stu-id="e1ef9-171">For more information about the project format changes, see [High-level overview of changes](./tools/cli-msbuild-architecture.md).</span></span>

---

<a name="vs-mapping"></a>

> [!TIP]
> <span data-ttu-id="e1ef9-172">Pour vérifier votre version de Visual Studio :</span><span class="sxs-lookup"><span data-stu-id="e1ef9-172">To verify your Visual Studio version:</span></span>
>
> * <span data-ttu-id="e1ef9-173">Dans le menu **Aide**, choisissez **À propos de Microsoft Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="e1ef9-173">On the **Help** menu, choose **About Microsoft Visual Studio**.</span></span>
> * <span data-ttu-id="e1ef9-174">Dans la boîte de dialogue **À propos de Microsoft Visual Studio**, vérifiez le numéro de version.</span><span class="sxs-lookup"><span data-stu-id="e1ef9-174">In the **About Microsoft Visual Studio** dialog, verify the version number.</span></span>
>   * <span data-ttu-id="e1ef9-175">Pour les applications .NET Core 3.0 Preview 3, Visual Studio 2019 version 16.0 ou ultérieure.</span><span class="sxs-lookup"><span data-stu-id="e1ef9-175">For .NET Core 3.0 Preview 3 apps, Visual Studio 2019 version 16.0 or higher.</span></span>
>   * <span data-ttu-id="e1ef9-176">Pour les applications .NET Core 2.2, Visual Studio 2017 version 15.9 ou ultérieure.</span><span class="sxs-lookup"><span data-stu-id="e1ef9-176">For .NET Core 2.2 apps, Visual Studio 2017 version 15.9 or higher.</span></span>
>   * <span data-ttu-id="e1ef9-177">Pour les applications .NET Core 2.1, Visual Studio 2017 version 15.7 ou ultérieure.</span><span class="sxs-lookup"><span data-stu-id="e1ef9-177">For .NET Core 2.1 apps, Visual Studio 2017 version 15.7 or higher.</span></span>
>   * <span data-ttu-id="e1ef9-178">Pour les applications .NET Core 1.x, Visual Studio 2017 version 15.0 ou ultérieure.</span><span class="sxs-lookup"><span data-stu-id="e1ef9-178">For .NET Core 1.x apps, Visual Studio 2017 version 15.0 or higher.</span></span>
