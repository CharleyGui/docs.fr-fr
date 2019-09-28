---
title: Configuration requise pour .NET Core sur Windows
description: Découvrez les dépendances nécessaires sur votre machine Windows pour développer et exécuter des applications .NET Core.
f1_keywords:
- NETSDK1045
ms.custom: updateeachvsrelease
ms.date: 09/20/2019
ms.openlocfilehash: b1557e6910cb6d0b6d7e2b3ce2aec97d3715fec7
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2019
ms.locfileid: "71591670"
---
# <a name="prerequisites-for-net-core-on-windows"></a><span data-ttu-id="87d80-103">Configuration requise pour .NET Core sur Windows</span><span class="sxs-lookup"><span data-stu-id="87d80-103">Prerequisites for .NET Core on Windows</span></span>

<span data-ttu-id="87d80-104">Cet article présente les versions de système d’exploitation prises en charge pour exécuter des applications .NET Core sur Windows.</span><span class="sxs-lookup"><span data-stu-id="87d80-104">This article shows the supported OS versions in order to run .NET Core applications on Windows.</span></span> <span data-ttu-id="87d80-105">Les versions de système d’exploitation et les dépendances prises en charge ci-après s’appliquent aux trois façons de développer des applications .NET Core sur Windows :</span><span class="sxs-lookup"><span data-stu-id="87d80-105">The supported OS versions and dependencies that follow apply to the three ways of developing .NET Core apps on Windows:</span></span>

* [<span data-ttu-id="87d80-106">Ligne de commande</span><span class="sxs-lookup"><span data-stu-id="87d80-106">Command line</span></span>](./tutorials/using-with-xplat-cli.md)
* [<span data-ttu-id="87d80-107">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="87d80-107">Visual Studio</span></span>](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019)
* [<span data-ttu-id="87d80-108">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="87d80-108">Visual Studio Code</span></span>](https://code.visualstudio.com/)

<span data-ttu-id="87d80-109">En outre, si vous développez sur Windows à l’aide de Visual Studio, la section [conditions préalables au développement d’applications .net core avec Visual Studio](#prerequisites-to-develop-net-core-apps-with-visual-studio) est plus détaillée sur les versions minimales prises en charge pour le développement .net core.</span><span class="sxs-lookup"><span data-stu-id="87d80-109">Also, if you're developing on Windows using Visual Studio, the [Prerequisites to develop .NET Core apps with Visual Studio](#prerequisites-to-develop-net-core-apps-with-visual-studio) section goes in more detail about minimum versions supported for .NET Core development.</span></span>

## <a name="net-core-supported-operating-systems"></a><span data-ttu-id="87d80-110">Systèmes d’exploitation pris en charge par .NET Core</span><span class="sxs-lookup"><span data-stu-id="87d80-110">.NET Core supported operating systems</span></span>

<span data-ttu-id="87d80-111">Les articles suivants dressent la liste complète des systèmes d’exploitation .NET Core pris en charge par version :</span><span class="sxs-lookup"><span data-stu-id="87d80-111">The following articles have a complete list of .NET Core supported operating systems per version:</span></span>

* [<span data-ttu-id="87d80-112">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="87d80-112">.NET Core 3.0</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md)
* [<span data-ttu-id="87d80-113">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="87d80-113">.NET Core 2.2</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md)
* [<span data-ttu-id="87d80-114">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="87d80-114">.NET Core 2.1</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)

<span data-ttu-id="87d80-115">Pour obtenir des liens de téléchargement et plus d’informations, consultez [Téléchargements .NET](https://dotnet.microsoft.com/download) afin de télécharger la version la plus récente ou [Archive des téléchargements .NET](https://dotnet.microsoft.com/download/archives#dotnet-core) pour les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="87d80-115">For download links and more information, see [.NET downloads](https://dotnet.microsoft.com/download) to download the latest version or [.NET downloads archive](https://dotnet.microsoft.com/download/archives#dotnet-core) for older versions.</span></span>

## <a name="net-core-dependencies"></a><span data-ttu-id="87d80-116">Dépendances .NET Core</span><span class="sxs-lookup"><span data-stu-id="87d80-116">.NET Core dependencies</span></span>

<span data-ttu-id="87d80-117">Vous devez installer [Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685) manuellement quand :</span><span class="sxs-lookup"><span data-stu-id="87d80-117">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685) must be manually installed when:</span></span>

* <span data-ttu-id="87d80-118">vous installez .NET Core avec le [script du programme d’installation](./tools/dotnet-install-script.md) ;</span><span class="sxs-lookup"><span data-stu-id="87d80-118">Installing .NET Core with the [installer script](./tools/dotnet-install-script.md).</span></span>
* <span data-ttu-id="87d80-119">vous déployez une application .NET Core autonome.</span><span class="sxs-lookup"><span data-stu-id="87d80-119">Deploying a self-contained .NET Core application.</span></span>
* <span data-ttu-id="87d80-120">Génération du produit à partir de la source.</span><span class="sxs-lookup"><span data-stu-id="87d80-120">Building the product from source.</span></span>
* <span data-ttu-id="87d80-121">Installation de .NET Core via un fichier *.zip*.</span><span class="sxs-lookup"><span data-stu-id="87d80-121">Installing .NET Core via a *.zip* file.</span></span> <span data-ttu-id="87d80-122">Ceci peut inclure des serveurs de builds/CI/CD.</span><span class="sxs-lookup"><span data-stu-id="87d80-122">This can include build/CI/CD servers.</span></span>

> [!NOTE]
> <span data-ttu-id="87d80-123">**Pour Windows 8.1 et versions antérieures, ou Windows Server 2012 R2 et versions antérieures :**</span><span class="sxs-lookup"><span data-stu-id="87d80-123">**For Windows 8.1 and earlier versions, or Windows Server 2012 R2 and earlier versions:**</span></span>
>
> <span data-ttu-id="87d80-124">Vérifiez que votre installation Windows est à jour et comprend le correctif logiciel [KB2999226](https://support.microsoft.com/help/2999226/update-for-universal-c-runtime-in-windows), installable via Windows Update.</span><span class="sxs-lookup"><span data-stu-id="87d80-124">Make sure that your Windows installation is up-to-date and includes [KB2999226](https://support.microsoft.com/help/2999226/update-for-universal-c-runtime-in-windows), which can be installed through Windows Update.</span></span> <span data-ttu-id="87d80-125">Si cette mise à jour n’est pas installée, quand vous lancez une application .NET Core, vous recevez une erreur semblable à celle-ci : `The program can't start because api-ms-win-crt-runtime-l1-1-0.dll is missing from your computer. Try reinstalling the program to fix this problem.`</span><span class="sxs-lookup"><span data-stu-id="87d80-125">If you don't have this update installed, you'll see an error like the following when you launch a .NET Core application: `The program can't start because api-ms-win-crt-runtime-l1-1-0.dll is missing from your computer. Try reinstalling the program to fix this problem.`</span></span>
>
> <span data-ttu-id="87d80-126">**Pour Windows 7 ou Windows Server 2008 R2 :**</span><span class="sxs-lookup"><span data-stu-id="87d80-126">**For Windows 7 or Windows Server 2008 R2:**</span></span>
>
> <span data-ttu-id="87d80-127">Outre KB2999226, vérifiez également que la mise à jour [KB2533623](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot) est installée.</span><span class="sxs-lookup"><span data-stu-id="87d80-127">In addition to KB2999226, make sure you also have [KB2533623](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot) installed.</span></span> <span data-ttu-id="87d80-128">Si cette mise à jour n’est pas installée, quand vous lancez une application .NET Core, vous recevez une erreur comme celle-ci : `The library hostfxr.dll was found, but loading it from C:\<path_to_app>\hostfxr.dll failed`.</span><span class="sxs-lookup"><span data-stu-id="87d80-128">If you don't have this update installed, you'll see an error similar to the following when you launch a .NET Core application: `The library hostfxr.dll was found, but loading it from C:\<path_to_app>\hostfxr.dll failed`.</span></span>

## <a name="prerequisites-to-develop-net-core-apps-with-visual-studio"></a><span data-ttu-id="87d80-129">Conditions préalables au développement d’applications .NET Core avec Visual Studio</span><span class="sxs-lookup"><span data-stu-id="87d80-129">Prerequisites to develop .NET Core apps with Visual Studio</span></span>
    
<span data-ttu-id="87d80-130">Même si vous pouvez utiliser n’importe quel éditeur pour développer des applications .NET Core à l’aide de l’kit SDK .NET Core, Visual Studio 2017 et versions ultérieures fournissent un environnement de développement intégré pour les applications .NET Core sur Windows.</span><span class="sxs-lookup"><span data-stu-id="87d80-130">Even though you can use any editor to develop .NET Core applications using the .NET Core SDK, Visual Studio 2017 and later versions provide an integrated development environment for .NET Core apps on Windows.</span></span>

<a name="vs-mapping"></a>

<span data-ttu-id="87d80-131">Une version minimale de Visual Studio est requise pour chaque version de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="87d80-131">Each .NET Core version has a minimum version of Visual Studio required.</span></span> <span data-ttu-id="87d80-132">Pour vérifier votre version de Visual Studio :</span><span class="sxs-lookup"><span data-stu-id="87d80-132">To verify your Visual Studio version:</span></span>

* <span data-ttu-id="87d80-133">Dans le menu **Aide**, choisissez **À propos de Microsoft Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="87d80-133">On the **Help** menu, choose **About Microsoft Visual Studio**.</span></span>
* <span data-ttu-id="87d80-134">Dans la boîte de dialogue **À propos de Microsoft Visual Studio**, vérifiez le numéro de version.</span><span class="sxs-lookup"><span data-stu-id="87d80-134">In the **About Microsoft Visual Studio** dialog, verify the version number.</span></span>

<span data-ttu-id="87d80-135">Le tableau suivant répertorie la version minimale pour chaque kit de développement logiciel (SDK) :</span><span class="sxs-lookup"><span data-stu-id="87d80-135">The following table lists the minimum version for each SDK:</span></span>

| <span data-ttu-id="87d80-136">Version de kit SDK .NET Core</span><span class="sxs-lookup"><span data-stu-id="87d80-136">.NET Core SDK version</span></span> | <span data-ttu-id="87d80-137">Version de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="87d80-137">Visual Studio version</span></span>                      |
| --------------------- | ------------------------------------------ |
| <span data-ttu-id="87d80-138">3.0</span><span class="sxs-lookup"><span data-stu-id="87d80-138">3.0</span></span>                   | <span data-ttu-id="87d80-139">Visual Studio 2019 version 16,3 ou ultérieure.</span><span class="sxs-lookup"><span data-stu-id="87d80-139">Visual Studio 2019 version 16.3 or higher.</span></span> |
| <span data-ttu-id="87d80-140">2.2</span><span class="sxs-lookup"><span data-stu-id="87d80-140">2.2</span></span>                   | <span data-ttu-id="87d80-141">Visual Studio 2017 version 15,9 ou ultérieure.</span><span class="sxs-lookup"><span data-stu-id="87d80-141">Visual Studio 2017 version 15.9 or higher.</span></span> |
| <span data-ttu-id="87d80-142">2.1</span><span class="sxs-lookup"><span data-stu-id="87d80-142">2.1</span></span>                   | <span data-ttu-id="87d80-143">Visual Studio 2017 version 15,7 ou ultérieure.</span><span class="sxs-lookup"><span data-stu-id="87d80-143">Visual Studio 2017 version 15.7 or higher.</span></span> |
| <span data-ttu-id="87d80-144">1.x</span><span class="sxs-lookup"><span data-stu-id="87d80-144">1.x</span></span>                   | <span data-ttu-id="87d80-145">Visual Studio 2017 version 15,0 ou ultérieure.</span><span class="sxs-lookup"><span data-stu-id="87d80-145">Visual Studio 2017 version 15.0 or higher.</span></span> |

<!-- markdownlint-disable MD025 -->

# <a name="net-core-30tabnetcore30"></a>[<span data-ttu-id="87d80-146">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="87d80-146">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="87d80-147">Pour développer des applications .NET Core dans Visual Studio 2019 à l’aide du kit de développement logiciel (SDK) .NET Core 3,0 :</span><span class="sxs-lookup"><span data-stu-id="87d80-147">To develop .NET Core apps in Visual Studio 2019 using the .NET Core 3.0 SDK:</span></span>

* <span data-ttu-id="87d80-148">[Téléchargez et installez Visual Studio 2019 version 16,3 ou ultérieure](/visualstudio/install/install-visual-studio) et sélectionnez l’une des charges de travail suivantes, qui comprend le kit SDK .net Core, selon le type d’application que vous créez :</span><span class="sxs-lookup"><span data-stu-id="87d80-148">[Download and install Visual Studio 2019 version 16.3 or higher](/visualstudio/install/install-visual-studio) and select one of the following workloads that includes the .NET Core SDK, depending on the kind of application you're building:</span></span>

  * <span data-ttu-id="87d80-149">La charge de travail **développement multiplateforme .net Core** dans la section **autres ensembles d’outils** .</span><span class="sxs-lookup"><span data-stu-id="87d80-149">The **.NET Core cross-platform development** workload in the **Other Toolsets** section.</span></span>
  * <span data-ttu-id="87d80-150">La charge de travail **ASP.net et développement Web** dans la section **Web & Cloud** .</span><span class="sxs-lookup"><span data-stu-id="87d80-150">The **ASP.NET and web development** workload in the **Web & Cloud** section.</span></span>
  * <span data-ttu-id="87d80-151">La charge de travail **développement net Desktop** dans la section **Windows** .</span><span class="sxs-lookup"><span data-stu-id="87d80-151">The **NET desktop development** workload in the **Windows** section.</span></span>

<span data-ttu-id="87d80-152">L’illustration suivante montre la charge de travail de **développement multiplateforme .net Core** sélectionnée dans l’interface utilisateur de Visual Studio :</span><span class="sxs-lookup"><span data-stu-id="87d80-152">The following image shows the **.NET Core cross-platform development** workload selected in the Visual Studio UI:</span></span>

![Capture d’écran de l’installation de Visual Studio 2019 avec la charge de travail « développement multiplateforme .NET Core » sélectionnée](./media/windows-prerequisites/vs-2019-workloads.jpg)

<span data-ttu-id="87d80-154">Visual Studio 2019 16,3 utilise le kit de développement logiciel (SDK) .NET Core 3,0 par défaut après l’installation de l’une de ces charges de travail.</span><span class="sxs-lookup"><span data-stu-id="87d80-154">Visual Studio 2019 16.3 uses .NET Core 3.0 SDK by default after any of these workloads are installed.</span></span>

<span data-ttu-id="87d80-155">Si vous souhaitez que vos projets existants utilisent la dernière version du Runtime .NET Core, reciblez chaque projet .NET Core existant vers .NET Core 3,0 à l’aide des instructions suivantes :</span><span class="sxs-lookup"><span data-stu-id="87d80-155">If you want your existing projects to use the latest .NET Core runtime, retarget each existing .NET Core project to .NET Core 3.0 using the following instructions:</span></span>

* <span data-ttu-id="87d80-156">Dans le menu **Projet** , choisissez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="87d80-156">On the **Project** menu, choose **Properties**.</span></span>
* <span data-ttu-id="87d80-157">Dans le menu de sélection du **Framework cible** , définissez la valeur sur **.net Core 3,0**.</span><span class="sxs-lookup"><span data-stu-id="87d80-157">In the **Target framework** selection menu, set the value to **.NET Core 3.0**.</span></span>

![Capture d’écran de la propriété de projet d’application Visual Studio 2019 avec l’élément de menu Framework cible « .NET Core 3,0 » sélectionné](./media/windows-prerequisites/target-dotnet-core-3-0.jpg)

<span data-ttu-id="87d80-159">Une fois que Visual Studio est configuré avec le kit de développement logiciel (SDK) .NET Core 3,0, vous pouvez effectuer les actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="87d80-159">Once you have Visual Studio configured with .NET Core 3.0 SDK, you can do the following actions:</span></span>

* <span data-ttu-id="87d80-160">Ouvrir, générer et exécuter les projets .NET Core 1.x et 2.x existants.</span><span class="sxs-lookup"><span data-stu-id="87d80-160">Open, build, and run existing .NET Core 1.x and 2.x projects.</span></span>
* <span data-ttu-id="87d80-161">Reciblez les projets .NET Core 1. x et 2. x vers .NET Core 3,0, générez et exécutez.</span><span class="sxs-lookup"><span data-stu-id="87d80-161">Retarget .NET Core 1.x and 2.x projects to .NET Core 3.0, build, and run.</span></span>
* <span data-ttu-id="87d80-162">Créez de nouveaux projets .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="87d80-162">Create new .NET Core 3.0 projects.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="87d80-163">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="87d80-163">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="87d80-164">Pour développer des applications .NET Core dans Visual Studio 2017 à l’aide du SDK .NET Core 2.2 :</span><span class="sxs-lookup"><span data-stu-id="87d80-164">To develop .NET Core apps in Visual Studio 2017 using the .NET Core 2.2 SDK:</span></span>

* <span data-ttu-id="87d80-165">[Téléchargez et installez Visual Studio 2019 version 16,3 ou ultérieure](/visualstudio/install/install-visual-studio) avec la charge de travail **développement multiplateforme .net Core** (dans la section **autres ensembles d’outils** ) sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="87d80-165">[Download and install Visual Studio 2019 version 16.3 or higher](/visualstudio/install/install-visual-studio) with the **.NET Core cross-platform development** workload (in the **Other Toolsets** section) selected.</span></span>
* <span data-ttu-id="87d80-166">[Téléchargez et installez Visual Studio 2017 version 15.9.0 ou version ultérieure](/visualstudio/install/install-visual-studio) en sélectionnant la charge de travail **Développement multiplateforme .NET Core** (dans la section **Autres ensembles d’outils**).</span><span class="sxs-lookup"><span data-stu-id="87d80-166">[Download and install Visual Studio 2017 version 15.9.0 or higher](/visualstudio/install/install-visual-studio) with the **.NET Core cross-platform development** workload (in the **Other Toolsets** section) selected.</span></span>

![Capture d’écran de l’installation de Visual Studio 2017 avec la charge de travail « Développement multiplateforme .NET Core » sélectionnée](./media/windows-prerequisites/vs-2017-workloads.jpg)

<span data-ttu-id="87d80-168">Une fois l’ensemble d’outils **Développement multiplateforme .NET Core** installé, Visual Studio installe généralement une version précédente du SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="87d80-168">After the **.NET Core cross-platform development** toolset is installed, Visual Studio usually installs a previous version of the .NET Core SDK.</span></span>
<span data-ttu-id="87d80-169">Par exemple, Visual Studio 2017 15.9 utilise par défaut le SDK .NET Core 2.1 après l’installation de la charge de travail.</span><span class="sxs-lookup"><span data-stu-id="87d80-169">For example, Visual Studio 2017 15.9 uses .NET Core 2.1 SDK by default after the workload is installed.</span></span>

<span data-ttu-id="87d80-170">Pour mettre à jour Visual Studio afin d’utiliser le SDK .NET Core 2.2 :</span><span class="sxs-lookup"><span data-stu-id="87d80-170">To update Visual Studio to use .NET Core 2.2 SDK:</span></span>

 1. <span data-ttu-id="87d80-171">Installez le [SDK .NET Core 2.2](https://dotnet.microsoft.com/download).</span><span class="sxs-lookup"><span data-stu-id="87d80-171">Install the [.NET Core 2.2 SDK](https://dotnet.microsoft.com/download).</span></span>

 1. <span data-ttu-id="87d80-172">Si vous souhaitez que votre projet utilise la dernière version du Runtime .NET Core, reciblez chaque projet .NET Core existant ou nouveau dans .NET Core 2,2 à l’aide des instructions suivantes :</span><span class="sxs-lookup"><span data-stu-id="87d80-172">If you want your project to use the latest .NET Core runtime, retarget each existing or new .NET Core project to .NET Core 2.2 using the following instructions:</span></span>

    * <span data-ttu-id="87d80-173">Dans le menu **Projet** , choisissez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="87d80-173">On the **Project** menu, choose **Properties**.</span></span>
    * <span data-ttu-id="87d80-174">Dans le menu de sélection du **framework cible**, choisissez **.NET Core 2.2**.</span><span class="sxs-lookup"><span data-stu-id="87d80-174">In the **Target framework** selection menu, set the value to **.NET Core 2.2**.</span></span>

![Capture d’écran de la propriété de projet Application Visual Studio 2017 avec définition de l’élément de menu framework cible sur « .NET Core 2.2 »](./media/windows-prerequisites/targeting-dotnet-core.jpg)

<span data-ttu-id="87d80-176">Une fois que vous avez configuré Visual Studio avec le SDK .NET Core 2.2, vous pouvez effectuer les actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="87d80-176">Once you have Visual Studio configured with .NET Core 2.2 SDK, you can do the following actions:</span></span>

* <span data-ttu-id="87d80-177">Ouvrir, générer et exécuter les projets .NET Core 1.x et 2.x existants.</span><span class="sxs-lookup"><span data-stu-id="87d80-177">Open, build, and run existing .NET Core 1.x and 2.x projects.</span></span>
* <span data-ttu-id="87d80-178">Recibler les projets .NET Core 1.x et 2.x vers .NET Core 2.2, les générer et les exécuter.</span><span class="sxs-lookup"><span data-stu-id="87d80-178">Retarget .NET Core 1.x and 2.x projects to .NET Core 2.2, build, and run.</span></span>
* <span data-ttu-id="87d80-179">Créer des projets .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="87d80-179">Create new .NET Core 2.2 projects.</span></span>

---
