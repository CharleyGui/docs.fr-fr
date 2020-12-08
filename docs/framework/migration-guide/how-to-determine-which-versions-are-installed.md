---
title: déterminer les versions du .NET Framework installées
description: Utilisez du code, regedit.exe ou PowerShell pour détecter les versions de .NET Framework qui sont installées sur un ordinateur en interrogeant le Registre Windows.
ms.date: 12/04/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- versions, determining for .NET Framework
- .NET Framework, determining installed versions
ms.assetid: 40a67826-e4df-4f59-a651-d9eb0fdc755d
ms.openlocfilehash: a219514fafdcb17db259e089afa8318dbab24811
ms.sourcegitcommit: 45c7148f2483db2501c1aa696ab6ed2ed8cb71b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96851827"
---
# <a name="how-to-determine-which-net-framework-versions-are-installed"></a><span data-ttu-id="c09c9-103">Guide pratique pour déterminer les versions du .NET Framework installées</span><span class="sxs-lookup"><span data-stu-id="c09c9-103">How to: Determine which .NET Framework versions are installed</span></span>

<span data-ttu-id="c09c9-104">Les utilisateurs peuvent [installer](../install/index.md) et exécuter plusieurs versions de .NET Framework sur leurs ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="c09c9-104">Users can [install](../install/index.md) and run multiple versions of .NET Framework on their computers.</span></span> <span data-ttu-id="c09c9-105">Lorsque vous développez ou déployez votre application, vous devrez peut-être connaître les versions de .NET Framework qui sont installées sur l’ordinateur de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="c09c9-105">When you develop or deploy your app, you might need to know which .NET Framework versions are installed on the user's computer.</span></span> <span data-ttu-id="c09c9-106">Le registre contient une liste des versions de .NET Framework installées sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="c09c9-106">The registry contains a list of the versions of .NET Framework installed on the computer.</span></span>

> [!NOTE]
> <span data-ttu-id="c09c9-107">Cet article est spécifique à .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c09c9-107">This article is specific to .NET Framework.</span></span> <span data-ttu-id="c09c9-108">Pour déterminer les kits de développement logiciel (SDK) .NET Core et .NET 5 + et les runtimes installés, consultez [Comment vérifier que .net est déjà installé](../../core/install/how-to-detect-installed-versions.md).</span><span class="sxs-lookup"><span data-stu-id="c09c9-108">To determine which .NET Core and .NET 5+ SDKs and runtimes are installed, see [How to check that .NET is already installed](../../core/install/how-to-detect-installed-versions.md).</span></span>

<span data-ttu-id="c09c9-109">.NET Framework se compose de deux composants principaux, dont les versions sont gérées séparément :</span><span class="sxs-lookup"><span data-stu-id="c09c9-109">.NET Framework consists of two main components, which are versioned separately:</span></span>

- <span data-ttu-id="c09c9-110">Un jeu d'assemblys, qui correspondent aux collections de types et de ressources qui fournissent les fonctionnalités de vos applications.</span><span class="sxs-lookup"><span data-stu-id="c09c9-110">A set of assemblies, which are collections of types and resources that provide the functionality for your apps.</span></span> <span data-ttu-id="c09c9-111">.NET Framework et les assemblys partagent le même numéro de version.</span><span class="sxs-lookup"><span data-stu-id="c09c9-111">.NET Framework and the assemblies share the same version number.</span></span> <span data-ttu-id="c09c9-112">Par exemple, 4.5, 4.6.1 et 4.7.2 sont des versions de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c09c9-112">For example, .NET Framework versions include 4.5, 4.6.1, and 4.7.2.</span></span>

- <span data-ttu-id="c09c9-113">Le Common Language Runtime (CLR), qui gère et exécute le code de votre application.</span><span class="sxs-lookup"><span data-stu-id="c09c9-113">The common language runtime (CLR), which manages and executes your app's code.</span></span> <span data-ttu-id="c09c9-114">En règle générale, une version particulière du CLR prend en charge plusieurs versions du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c09c9-114">A single CLR version typically supports multiple .NET Framework versions.</span></span> <span data-ttu-id="c09c9-115">Par exemple, CLR version 4.0.30319. *xxxxx* où *xxxxx* est inférieur à 42000, prend en charge .NET Framework les versions 4 à 4.5.2.</span><span class="sxs-lookup"><span data-stu-id="c09c9-115">For example, CLR version 4.0.30319.*xxxxx* where *xxxxx* is less than 42000, supports .NET Framework versions 4 through 4.5.2.</span></span> <span data-ttu-id="c09c9-116">La version CLR supérieure ou égale à 4.0.30319.42000 prend en charge les versions .NET Framework à partir de .NET Framework 4,6.</span><span class="sxs-lookup"><span data-stu-id="c09c9-116">CLR version greater than or equal to 4.0.30319.42000 supports .NET Framework versions starting with .NET Framework 4.6.</span></span>

<span data-ttu-id="c09c9-117">Des outils gérés par la Communauté sont disponibles pour vous aider à détecter les versions de .NET Framework installées :</span><span class="sxs-lookup"><span data-stu-id="c09c9-117">Community-maintained tools are available to help detect which .NET Framework versions are installed:</span></span>

- [https://github.com/jmalarcon/DotNetVersions](https://github.com/jmalarcon/DotNetVersions)

  <span data-ttu-id="c09c9-118">Un outil de ligne de commande .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="c09c9-118">A .NET Framework 2.0 command-line tool.</span></span>

- [https://github.com/EliteLoser/DotNetVersionLister](https://github.com/EliteLoser/DotNetVersionLister)

  <span data-ttu-id="c09c9-119">Un module PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="c09c9-119">A PowerShell 2.0 module.</span></span>

<span data-ttu-id="c09c9-120">Pour plus d’informations sur la détection des mises à jour installées pour chaque version de .NET Framework, consultez [Comment : déterminer les mises à jour de .NET Framework installées](how-to-determine-which-net-framework-updates-are-installed.md).</span><span class="sxs-lookup"><span data-stu-id="c09c9-120">For information about detecting the installed updates for each version of .NET Framework, see [How to: Determine which .NET Framework updates are installed](how-to-determine-which-net-framework-updates-are-installed.md).</span></span>

## <a name="determine-which-net-implementation-and-version-an-app-is-running-on"></a><span data-ttu-id="c09c9-121">Déterminer l’implémentation .NET et la version sur laquelle une application s’exécute</span><span class="sxs-lookup"><span data-stu-id="c09c9-121">Determine which .NET implementation and version an app is running on</span></span>

<span data-ttu-id="c09c9-122">Vous pouvez utiliser la <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> propriété pour rechercher la version et l’implémentation .net sur laquelle votre application s’exécute.</span><span class="sxs-lookup"><span data-stu-id="c09c9-122">You can use the <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> property to query for which .NET implementation and version your app is running on.</span></span> <span data-ttu-id="c09c9-123">Si l’application s’exécute sur .NET Framework, la sortie ressemble à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="c09c9-123">If the app is running on .NET Framework, the output will be similar to:</span></span>

```output
.NET Framework 4.8.4250.0
```

<span data-ttu-id="c09c9-124">Par comparaison, si l’application s’exécute sur .NET Core ou sur .NET 5 +, la sortie est similaire à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="c09c9-124">By comparison, if the app is running on .NET Core or .NET 5+, the output will be similar to:</span></span>

```output
.NET Core 3.1.9
.NET 5.0.0
```

## <a name="detect-net-framework-45-and-later-versions"></a><span data-ttu-id="c09c9-125">Détection des .NET Framework 4,5 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="c09c9-125">Detect .NET Framework 4.5 and later versions</span></span>

<span data-ttu-id="c09c9-126">La version de .NET Framework (4,5 et versions ultérieures) installée sur un ordinateur est listée dans le registre à l’adresse **HKEY_LOCAL_MACHINE \\ logiciel \\ Microsoft \\ NET Framework installation \\ NDP \\ v4 \\ Full**.</span><span class="sxs-lookup"><span data-stu-id="c09c9-126">The version of .NET Framework (4.5 and later) installed on a machine is listed in the registry at **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full**.</span></span> <span data-ttu-id="c09c9-127">Si la sous-clé **complète** est manquante, .NET Framework 4,5 ou version ultérieure n’est pas installé.</span><span class="sxs-lookup"><span data-stu-id="c09c9-127">If the **Full** subkey is missing, then .NET Framework 4.5 or above isn't installed.</span></span>

> [!NOTE]
> <span data-ttu-id="c09c9-128">La sous-clé **d’installation** du .NET Framework dans le chemin d’accès du registre ne commence *pas* par un point.</span><span class="sxs-lookup"><span data-stu-id="c09c9-128">The **NET Framework Setup** subkey in the registry path does *not* begin with a period.</span></span>

<span data-ttu-id="c09c9-129">La valeur de REG_DWORD de **version** dans le registre représente la version de .NET Framework installée.</span><span class="sxs-lookup"><span data-stu-id="c09c9-129">The **Release** REG_DWORD value in the registry represents the version of .NET Framework installed.</span></span>

<a name="version_table"></a>

| <span data-ttu-id="c09c9-130">Version du .NET Framework</span><span class="sxs-lookup"><span data-stu-id="c09c9-130">.NET Framework version</span></span> | <span data-ttu-id="c09c9-131">Valeur de la **mise en version**</span><span class="sxs-lookup"><span data-stu-id="c09c9-131">Value of **Release**</span></span> |
| ---------------------- | -------------------------- |
| <span data-ttu-id="c09c9-132">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="c09c9-132">.NET Framework 4.5</span></span>     | <span data-ttu-id="c09c9-133">Tous les systèmes d’exploitation Windows : 378389</span><span class="sxs-lookup"><span data-stu-id="c09c9-133">All Windows operating systems: 378389</span></span> |
| <span data-ttu-id="c09c9-134">.NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="c09c9-134">.NET Framework 4.5.1</span></span>   | <span data-ttu-id="c09c9-135">Sur Windows 8.1 et Windows Server 2012 R2:378675</span><span class="sxs-lookup"><span data-stu-id="c09c9-135">On Windows 8.1 and Windows Server 2012 R2: 378675</span></span><br /><span data-ttu-id="c09c9-136">Sur tous les autres systèmes d’exploitation Windows : 378758</span><span class="sxs-lookup"><span data-stu-id="c09c9-136">On all other Windows operating systems: 378758</span></span> |
| <span data-ttu-id="c09c9-137">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="c09c9-137">.NET Framework 4.5.2</span></span>   | <span data-ttu-id="c09c9-138">Tous les systèmes d’exploitation Windows : 379893</span><span class="sxs-lookup"><span data-stu-id="c09c9-138">All Windows operating systems: 379893</span></span> |
| <span data-ttu-id="c09c9-139">.NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="c09c9-139">.NET Framework 4.6</span></span>     | <span data-ttu-id="c09c9-140">Sur Windows 10:393295</span><span class="sxs-lookup"><span data-stu-id="c09c9-140">On Windows 10: 393295</span></span><br /><span data-ttu-id="c09c9-141">Sur tous les autres systèmes d’exploitation Windows : 393297</span><span class="sxs-lookup"><span data-stu-id="c09c9-141">On all other Windows operating systems: 393297</span></span> |
| <span data-ttu-id="c09c9-142">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="c09c9-142">.NET Framework 4.6.1</span></span>   | <span data-ttu-id="c09c9-143">Sur les systèmes Windows intégrant la mise à jour du 10 novembre : 394254</span><span class="sxs-lookup"><span data-stu-id="c09c9-143">On Windows 10 November Update systems: 394254</span></span><br /><span data-ttu-id="c09c9-144">Sur tous les autres systèmes d’exploitation Windows (y compris Windows 10) : 394271</span><span class="sxs-lookup"><span data-stu-id="c09c9-144">On all other Windows operating systems (including Windows 10): 394271</span></span> |
| <span data-ttu-id="c09c9-145">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="c09c9-145">.NET Framework 4.6.2</span></span>   | <span data-ttu-id="c09c9-146">Sur les systèmes Mise à jour anniversaire Windows 10 et Windows Server 2016 : 394802</span><span class="sxs-lookup"><span data-stu-id="c09c9-146">On Windows 10 Anniversary Update and Windows Server 2016: 394802</span></span><br /><span data-ttu-id="c09c9-147">Sur tous les autres systèmes d’exploitation Windows (y compris les autres systèmes d’exploitation Windows 10) : 394806</span><span class="sxs-lookup"><span data-stu-id="c09c9-147">On all other Windows operating systems (including other Windows 10 operating systems): 394806</span></span> |
| <span data-ttu-id="c09c9-148">.NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="c09c9-148">.NET Framework 4.7</span></span>     | <span data-ttu-id="c09c9-149">Sur Windows 10 Creators Update : 460798</span><span class="sxs-lookup"><span data-stu-id="c09c9-149">On Windows 10 Creators Update: 460798</span></span><br /><span data-ttu-id="c09c9-150">Sur tous les autres systèmes d’exploitation Windows (y compris les autres systèmes d’exploitation Windows 10) : 460805</span><span class="sxs-lookup"><span data-stu-id="c09c9-150">On all other Windows operating systems (including other Windows 10 operating systems): 460805</span></span> |
| <span data-ttu-id="c09c9-151">.NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="c09c9-151">.NET Framework 4.7.1</span></span>   | <span data-ttu-id="c09c9-152">Sur Windows 10 automne Creators Update et Windows Server, version 1709:461308</span><span class="sxs-lookup"><span data-stu-id="c09c9-152">On Windows 10 Fall Creators Update and Windows Server, version 1709: 461308</span></span><br/><span data-ttu-id="c09c9-153">Sur tous les autres systèmes d’exploitation Windows (y compris les autres systèmes d’exploitation Windows 10) : 461310</span><span class="sxs-lookup"><span data-stu-id="c09c9-153">On all other Windows operating systems (including other Windows 10 operating systems): 461310</span></span> |
| <span data-ttu-id="c09c9-154">.NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="c09c9-154">.NET Framework 4.7.2</span></span>   | <span data-ttu-id="c09c9-155">Sur Windows 10 avril 2018 mise à jour et Windows Server, version 1803:461808</span><span class="sxs-lookup"><span data-stu-id="c09c9-155">On Windows 10 April 2018 Update and Windows Server, version 1803: 461808</span></span><br/><span data-ttu-id="c09c9-156">Sur tous les systèmes d’exploitation Windows autres que Windows 10 avril 2018 Update et Windows Server, version 1803:461814</span><span class="sxs-lookup"><span data-stu-id="c09c9-156">On all Windows operating systems other than Windows 10 April 2018 Update and Windows Server, version 1803: 461814</span></span> |
| <span data-ttu-id="c09c9-157">.NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="c09c9-157">.NET Framework 4.8</span></span>     | <span data-ttu-id="c09c9-158">Sur Windows 10 mai 2019 mise à jour et Windows 10 novembre 2019 mise à jour : 528040</span><span class="sxs-lookup"><span data-stu-id="c09c9-158">On Windows 10 May 2019 Update and Windows 10 November 2019 Update: 528040</span></span><br/><span data-ttu-id="c09c9-159">Sur Windows 10 mai 2020 mise à jour et Windows 10 octobre 2020 mise à jour : 528372</span><span class="sxs-lookup"><span data-stu-id="c09c9-159">On Windows 10 May 2020 Update and Windows 10 October 2020 Update: 528372</span></span><br/><span data-ttu-id="c09c9-160">Sur tous les autres systèmes d’exploitation Windows (y compris les autres systèmes d’exploitation Windows 10) : 528049</span><span class="sxs-lookup"><span data-stu-id="c09c9-160">On all other Windows operating systems (including other Windows 10 operating systems): 528049</span></span> |

### <a name="minimum-version"></a><span data-ttu-id="c09c9-161">Version minimale</span><span class="sxs-lookup"><span data-stu-id="c09c9-161">Minimum version</span></span>

<span data-ttu-id="c09c9-162">Pour déterminer si une version *minimale* de .NET Framework est présente, recherchez une valeur de REG_DWORD de **mise en sortie** qui est supérieure ou égale à la valeur correspondante indiquée dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="c09c9-162">To determine whether a *minimum* version of .NET Framework is present, check for a **Release** REG_DWORD value that's greater than or equal to the corresponding value listed in the following table.</span></span> <span data-ttu-id="c09c9-163">Par exemple, si votre application s’exécute sous .NET Framework 4,8 ou une version ultérieure, testez une valeur de REG_DWORD de **version** *supérieure ou égale à* 528040.</span><span class="sxs-lookup"><span data-stu-id="c09c9-163">For example, if your application runs under .NET Framework 4.8 or a later version, test for a **Release** REG_DWORD value that's *greater than or equal to* 528040.</span></span>

| <span data-ttu-id="c09c9-164">Version du .NET Framework</span><span class="sxs-lookup"><span data-stu-id="c09c9-164">.NET Framework version</span></span> | <span data-ttu-id="c09c9-165">Valeur minimale</span><span class="sxs-lookup"><span data-stu-id="c09c9-165">Minimum value</span></span> |
| ---------------------- | ------------- |
| <span data-ttu-id="c09c9-166">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="c09c9-166">.NET Framework 4.5</span></span>     | <span data-ttu-id="c09c9-167">378389</span><span class="sxs-lookup"><span data-stu-id="c09c9-167">378389</span></span> |
| <span data-ttu-id="c09c9-168">.NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="c09c9-168">.NET Framework 4.5.1</span></span>   | <span data-ttu-id="c09c9-169">378675</span><span class="sxs-lookup"><span data-stu-id="c09c9-169">378675</span></span> |
| <span data-ttu-id="c09c9-170">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="c09c9-170">.NET Framework 4.5.2</span></span>   | <span data-ttu-id="c09c9-171">379893</span><span class="sxs-lookup"><span data-stu-id="c09c9-171">379893</span></span> |
| <span data-ttu-id="c09c9-172">.NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="c09c9-172">.NET Framework 4.6</span></span>     | <span data-ttu-id="c09c9-173">393295</span><span class="sxs-lookup"><span data-stu-id="c09c9-173">393295</span></span> |
| <span data-ttu-id="c09c9-174">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="c09c9-174">.NET Framework 4.6.1</span></span>   | <span data-ttu-id="c09c9-175">394254</span><span class="sxs-lookup"><span data-stu-id="c09c9-175">394254</span></span> |
| <span data-ttu-id="c09c9-176">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="c09c9-176">.NET Framework 4.6.2</span></span>   | <span data-ttu-id="c09c9-177">394802</span><span class="sxs-lookup"><span data-stu-id="c09c9-177">394802</span></span> |
| <span data-ttu-id="c09c9-178">.NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="c09c9-178">.NET Framework 4.7</span></span>     | <span data-ttu-id="c09c9-179">460798</span><span class="sxs-lookup"><span data-stu-id="c09c9-179">460798</span></span> |
| <span data-ttu-id="c09c9-180">.NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="c09c9-180">.NET Framework 4.7.1</span></span>   | <span data-ttu-id="c09c9-181">461308</span><span class="sxs-lookup"><span data-stu-id="c09c9-181">461308</span></span> |
| <span data-ttu-id="c09c9-182">.NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="c09c9-182">.NET Framework 4.7.2</span></span>   | <span data-ttu-id="c09c9-183">461808</span><span class="sxs-lookup"><span data-stu-id="c09c9-183">461808</span></span> |
| <span data-ttu-id="c09c9-184">.NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="c09c9-184">.NET Framework 4.8</span></span>     | <span data-ttu-id="c09c9-185">528040</span><span class="sxs-lookup"><span data-stu-id="c09c9-185">528040</span></span> |

### <a name="use-registry-editor"></a><span data-ttu-id="c09c9-186">Utiliser l’éditeur du Registre</span><span class="sxs-lookup"><span data-stu-id="c09c9-186">Use Registry Editor</span></span>

1. <span data-ttu-id="c09c9-187">À partir du menu **Démarrer**, choisissez **Exécuter**, entrez *regedit*, puis sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="c09c9-187">From the **Start** menu, choose **Run**, enter *regedit*, and then select **OK**.</span></span>

   <span data-ttu-id="c09c9-188">(Vous devez disposer d’informations d’identification d’administration pour exécuter regedit.)</span><span class="sxs-lookup"><span data-stu-id="c09c9-188">(You must have administrative credentials to run regedit.)</span></span>

1. <span data-ttu-id="c09c9-189">Dans l’éditeur du Registre, ouvrez la sous-clé suivante : **HKEY_LOCAL_MACHINE \\ logiciel \\ Microsoft \\ NET Framework installation \\ NDP \\ v4 \\ Full**.</span><span class="sxs-lookup"><span data-stu-id="c09c9-189">In the Registry Editor, open the following subkey: **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full**.</span></span> <span data-ttu-id="c09c9-190">Si la sous-clé **complète** n’est pas présente, vous n’avez pas .NET Framework 4,5 ou une version ultérieure installée.</span><span class="sxs-lookup"><span data-stu-id="c09c9-190">If the **Full** subkey isn't present, then you don't have .NET Framework 4.5 or later installed.</span></span>

1. <span data-ttu-id="c09c9-191">Recherchez une entrée de REG_DWORD nommée **Release**.</span><span class="sxs-lookup"><span data-stu-id="c09c9-191">Check for a REG_DWORD entry named **Release**.</span></span> <span data-ttu-id="c09c9-192">S’il existe, .NET Framework 4,5 ou version ultérieure est installé.</span><span class="sxs-lookup"><span data-stu-id="c09c9-192">If it exists, then you have .NET Framework 4.5 or later installed.</span></span> <span data-ttu-id="c09c9-193">Sa valeur correspond à une version particulière de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c09c9-193">Its value corresponds to a particular version of .NET Framework.</span></span> <span data-ttu-id="c09c9-194">Dans l’illustration suivante, par exemple, la valeur de l’entrée de **version** est 528040, qui est la clé de mise en version de .NET Framework 4,8.</span><span class="sxs-lookup"><span data-stu-id="c09c9-194">In the following figure, for example, the value of the **Release** entry is 528040, which is the release key for .NET Framework 4.8.</span></span>

   ![Entrée de Registre pour .NET Framework 4,5](./media/clr-installdir.png )

### <a name="use-powershell-to-check-for-a-minimum-version"></a><span data-ttu-id="c09c9-196">Utiliser PowerShell pour vérifier la version minimale</span><span class="sxs-lookup"><span data-stu-id="c09c9-196">Use PowerShell to check for a minimum version</span></span>

<span data-ttu-id="c09c9-197">Utilisez les commandes PowerShell pour vérifier la valeur de l’entrée de **publication** de l’HKEY_LOCAL_MACHINE sous-clé complète de l' **installation du \\ logiciel \\ Microsoft \\ NET Framework, \\ NDP \\ v4 \\** .</span><span class="sxs-lookup"><span data-stu-id="c09c9-197">Use PowerShell commands to check the value of the **Release** entry of the **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full** subkey.</span></span>

<span data-ttu-id="c09c9-198">Les exemples suivants vérifient la valeur de l’entrée de **mise en sortie** pour déterminer si .NET Framework 4.6.2 ou version ultérieure est installé.</span><span class="sxs-lookup"><span data-stu-id="c09c9-198">The following examples check the value of the **Release** entry to determine whether .NET Framework 4.6.2 or later is installed.</span></span> <span data-ttu-id="c09c9-199">Ce code retourne `True` s’il est installé et `False` dans le cas contraire.</span><span class="sxs-lookup"><span data-stu-id="c09c9-199">This code returns `True` if it's installed and `False` otherwise.</span></span>

```powershell
(Get-ItemProperty "HKLM:\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full").Release -ge 394802
```

### <a name="query-the-registry-using-code"></a><span data-ttu-id="c09c9-200">Interroger le registre à l’aide de code</span><span class="sxs-lookup"><span data-stu-id="c09c9-200">Query the registry using code</span></span>

01. <span data-ttu-id="c09c9-201">Utilisez les <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType> méthodes et pour accéder à la sous-clé complète du **\\ \\ programme d’installation de HKEY_LOCAL_MACHINE logiciel Microsoft \\ NET Framework, \\ NDP \\ \\ v4** , dans le Registre Windows.</span><span class="sxs-lookup"><span data-stu-id="c09c9-201">Use the <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> and <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType> methods to access the **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full** subkey in the Windows registry.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="c09c9-202">Si l’application que vous exécutez est 32 bits et s’exécute sous Windows 64 bits, les chemins d’accès au Registre sont différents de ceux indiqués précédemment.</span><span class="sxs-lookup"><span data-stu-id="c09c9-202">If the app you're running is 32-bit and running in 64-bit Windows, the registry paths will be different than previously listed.</span></span> <span data-ttu-id="c09c9-203">Le registre 64 bits est disponible dans la sous-clé **HKEY_LOCAL_MACHINE \\ Software \\ Wow6432Node \\** .</span><span class="sxs-lookup"><span data-stu-id="c09c9-203">The 64-bit registry is available in the **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\** subkey.</span></span> <span data-ttu-id="c09c9-204">Par exemple, la sous-clé de Registre pour .NET Framework 4,5 est **HKEY_LOCAL_MACHINE \\ logiciel \\ Wow6432Node \\ Microsoft \\ NET Framework Setup \\ NDP \\ v4 \\ complet**.</span><span class="sxs-lookup"><span data-stu-id="c09c9-204">For example, the registry subkey for .NET Framework 4.5 is **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full**.</span></span>

01. <span data-ttu-id="c09c9-205">Vérifiez la valeur REG_DWORD de **version** pour déterminer la version installée.</span><span class="sxs-lookup"><span data-stu-id="c09c9-205">Check the **Release** REG_DWORD value to determine the installed version.</span></span> <span data-ttu-id="c09c9-206">Pour être compatible, recherchez une valeur supérieure ou égale à la valeur listée dans le [tableau des versions du .NET Framework](#version_table).</span><span class="sxs-lookup"><span data-stu-id="c09c9-206">To be forward-compatible, check for a value greater than or equal to the value listed in the [.NET Framework version table](#version_table).</span></span>

<span data-ttu-id="c09c9-207">L’exemple suivant vérifie la valeur de l’entrée de **publication** dans le registre pour rechercher les versions de .NET Framework 4.5-4.8 qui sont installées :</span><span class="sxs-lookup"><span data-stu-id="c09c9-207">The following example checks the value of the **Release** entry in the registry to find the versions of .NET Framework 4.5-4.8 that are installed:</span></span>

:::code language="csharp" source="snippets/csharp/versions-installed.cs" id="2":::

:::code language="vb" source="snippets/visual-basic/versions-installed.vb" id="2":::

<span data-ttu-id="c09c9-208">L’exemple affiche une sortie similaire à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="c09c9-208">The example displays output like the following:</span></span>

```output
.NET Framework Version: 4.6.1
```

<span data-ttu-id="c09c9-209">Cet exemple suit la pratique recommandée concernant la vérification de version :</span><span class="sxs-lookup"><span data-stu-id="c09c9-209">This example follows the recommended practice for version checking:</span></span>

- <span data-ttu-id="c09c9-210">Il vérifie si la valeur de l’entrée **Release** est *supérieure ou égale à* la valeur des clés de version connues.</span><span class="sxs-lookup"><span data-stu-id="c09c9-210">It checks whether the value of the **Release** entry is *greater than or equal to* the value of the known release keys.</span></span>
- <span data-ttu-id="c09c9-211">Il effectue sa vérification en partant de la version la plus récente vers la version la plus ancienne.</span><span class="sxs-lookup"><span data-stu-id="c09c9-211">It checks in order from most recent version to earliest version.</span></span>

## <a name="detect-net-framework-10-through-40"></a><span data-ttu-id="c09c9-212">Détection des .NET Framework 1,0 à 4,0</span><span class="sxs-lookup"><span data-stu-id="c09c9-212">Detect .NET Framework 1.0 through 4.0</span></span>

<span data-ttu-id="c09c9-213">Chaque version de .NET Framework de 1,1 à 4,0 est indiquée sous la forme d’une sous-clé dans **HKEY_LOCAL_MACHINE \\ logiciel \\ Microsoft \\ NET Framework Setup \\ NDP**.</span><span class="sxs-lookup"><span data-stu-id="c09c9-213">Each version of .NET Framework from 1.1 to 4.0 is listed as a subkey at **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP**.</span></span> <span data-ttu-id="c09c9-214">Le tableau suivant répertorie le chemin d’accès à chaque version de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c09c9-214">The following table lists the path to each .NET Framework version.</span></span> <span data-ttu-id="c09c9-215">Pour la plupart des versions, il existe une valeur d' **installation** REG_DWORD de `1` pour indiquer que cette version est installée.</span><span class="sxs-lookup"><span data-stu-id="c09c9-215">For most versions, there's an **Install** REG_DWORD value of `1` to indicate this version is installed.</span></span> <span data-ttu-id="c09c9-216">Dans ces sous-clés, il y a également une valeur de REG_SZ de **version** qui contient une chaîne de version.</span><span class="sxs-lookup"><span data-stu-id="c09c9-216">In these subkeys, there's also a **Version** REG_SZ value that contains a version string.</span></span>

> [!NOTE]
> <span data-ttu-id="c09c9-217">La sous-clé **d’installation** du .NET Framework dans le chemin d’accès du registre ne commence *pas* par un point.</span><span class="sxs-lookup"><span data-stu-id="c09c9-217">The **NET Framework Setup** subkey in the registry path does *not* begin with a period.</span></span>

| <span data-ttu-id="c09c9-218">Version du Framework</span><span class="sxs-lookup"><span data-stu-id="c09c9-218">Framework Version</span></span>  | <span data-ttu-id="c09c9-219">Sous-clé de Registre</span><span class="sxs-lookup"><span data-stu-id="c09c9-219">Registry Subkey</span></span> | <span data-ttu-id="c09c9-220">Valeur</span><span class="sxs-lookup"><span data-stu-id="c09c9-220">Value</span></span> |
| ------------------ | --------------- | ----- |
| <span data-ttu-id="c09c9-221">1.0</span><span class="sxs-lookup"><span data-stu-id="c09c9-221">1.0</span></span>                | <span data-ttu-id="c09c9-222">**HKLM \\ Software \\ Microsoft \\ . \\Stratégie NETFramework \\ v 1.0 \\ 3705**</span><span class="sxs-lookup"><span data-stu-id="c09c9-222">**HKLM\\Software\\Microsoft\\.NETFramework\\Policy\\v1.0\\3705**</span></span>     | <span data-ttu-id="c09c9-223">**Installer** REG_SZ est égal à `1`</span><span class="sxs-lookup"><span data-stu-id="c09c9-223">**Install** REG_SZ equals `1`</span></span> |
| <span data-ttu-id="c09c9-224">1.1</span><span class="sxs-lookup"><span data-stu-id="c09c9-224">1.1</span></span>                | <span data-ttu-id="c09c9-225">**HKLM \\ Software \\ Microsoft \\ NET Framework Setup \\ NDP \\ v 1.1.4322**</span><span class="sxs-lookup"><span data-stu-id="c09c9-225">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v1.1.4322**</span></span>   | <span data-ttu-id="c09c9-226">**Installer** REG_DWORD est égal à `1`</span><span class="sxs-lookup"><span data-stu-id="c09c9-226">**Install** REG_DWORD equals `1`</span></span> |
| <span data-ttu-id="c09c9-227">2.0</span><span class="sxs-lookup"><span data-stu-id="c09c9-227">2.0</span></span>                | <span data-ttu-id="c09c9-228">**HKLM \\ Software \\ Microsoft \\ .NET Framework Setup \\ NDP \\ v 2.0.50727**</span><span class="sxs-lookup"><span data-stu-id="c09c9-228">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v2.0.50727**</span></span>  | <span data-ttu-id="c09c9-229">**Installer** REG_DWORD est égal à `1`</span><span class="sxs-lookup"><span data-stu-id="c09c9-229">**Install** REG_DWORD equals `1`</span></span> |
| <span data-ttu-id="c09c9-230">3.0</span><span class="sxs-lookup"><span data-stu-id="c09c9-230">3.0</span></span>                | <span data-ttu-id="c09c9-231">**HKLM \\ Software \\ Microsoft \\ .NET Framework Setup \\ NDP \\ v 3.0 \\ installation**</span><span class="sxs-lookup"><span data-stu-id="c09c9-231">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v3.0\\Setup**</span></span> | <span data-ttu-id="c09c9-232">**InstallSuccess** REG_DWORD est égal à `1`</span><span class="sxs-lookup"><span data-stu-id="c09c9-232">**InstallSuccess** REG_DWORD equals `1`</span></span> |
| <span data-ttu-id="c09c9-233">3,5</span><span class="sxs-lookup"><span data-stu-id="c09c9-233">3.5</span></span>                | <span data-ttu-id="c09c9-234">**HKLM \\ Software \\ Microsoft \\ NET Framework Setup \\ NDP \\ v 3.5**</span><span class="sxs-lookup"><span data-stu-id="c09c9-234">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v3.5**</span></span>        | <span data-ttu-id="c09c9-235">**Installer** REG_DWORD est égal à `1`</span><span class="sxs-lookup"><span data-stu-id="c09c9-235">**Install** REG_DWORD equals `1`</span></span> |
| <span data-ttu-id="c09c9-236">Profil client 4,0</span><span class="sxs-lookup"><span data-stu-id="c09c9-236">4.0 Client Profile</span></span> | <span data-ttu-id="c09c9-237">**HKLM \\ Software \\ Microsoft \\ .NET Framework installation de \\ NDP \\ v4 \\ client**</span><span class="sxs-lookup"><span data-stu-id="c09c9-237">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v4\\Client**</span></span>  | <span data-ttu-id="c09c9-238">**Installer** REG_DWORD est égal à `1`</span><span class="sxs-lookup"><span data-stu-id="c09c9-238">**Install** REG_DWORD equals `1`</span></span> |
| <span data-ttu-id="c09c9-239">Profil complet 4,0</span><span class="sxs-lookup"><span data-stu-id="c09c9-239">4.0 Full Profile</span></span>   | <span data-ttu-id="c09c9-240">**HKLM version du \\ \\ \\ programme d’installation de Microsoft NET Framework, \\ NDP \\ v4 \\ complet**</span><span class="sxs-lookup"><span data-stu-id="c09c9-240">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full**</span></span>    | <span data-ttu-id="c09c9-241">**Installer** REG_DWORD est égal à `1`</span><span class="sxs-lookup"><span data-stu-id="c09c9-241">**Install** REG_DWORD equals `1`</span></span> |

> [!IMPORTANT]
> <span data-ttu-id="c09c9-242">Si l’application que vous exécutez est 32 bits et s’exécute sous Windows 64 bits, les chemins d’accès au Registre sont différents de ceux indiqués précédemment.</span><span class="sxs-lookup"><span data-stu-id="c09c9-242">If the app you're running is 32-bit and running in 64-bit Windows, the registry paths will be different than previously listed.</span></span> <span data-ttu-id="c09c9-243">Le registre 64 bits est disponible dans la sous-clé **HKEY_LOCAL_MACHINE \\ Software \\ Wow6432Node \\** .</span><span class="sxs-lookup"><span data-stu-id="c09c9-243">The 64-bit registry is available in the **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\** subkey.</span></span> <span data-ttu-id="c09c9-244">Par exemple, la sous-clé de Registre pour .NET Framework 3,5 est **HKEY_LOCAL_MACHINE \\ logiciel \\ Wow6432Node \\ Microsoft \\ NET Framework Setup \\ NDP \\ v 3.5**.</span><span class="sxs-lookup"><span data-stu-id="c09c9-244">For example, the registry subkey for .NET Framework 3.5 is **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\NET Framework Setup\\NDP\\v3.5**.</span></span>

<span data-ttu-id="c09c9-245">Notez que le chemin d’accès au registre de la sous-clé .NET Framework 1,0 est différent des autres.</span><span class="sxs-lookup"><span data-stu-id="c09c9-245">Notice that the registry path to the .NET Framework 1.0 subkey is different from the others.</span></span>

### <a name="use-registry-editor-older-framework-versions"></a><span data-ttu-id="c09c9-246">Utiliser l’éditeur du Registre (versions antérieures de l’infrastructure)</span><span class="sxs-lookup"><span data-stu-id="c09c9-246">Use Registry Editor (older framework versions)</span></span>

01. <span data-ttu-id="c09c9-247">À partir du menu **Démarrer**, choisissez **Exécuter**, entrez *regedit*, puis sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="c09c9-247">From the **Start** menu, choose **Run**, enter *regedit*, and then select **OK**.</span></span>

    <span data-ttu-id="c09c9-248">Vous devez disposer d’informations d’identification d’administrateur pour exécuter regedit.</span><span class="sxs-lookup"><span data-stu-id="c09c9-248">You must have administrative credentials to run regedit.</span></span>

01. <span data-ttu-id="c09c9-249">Ouvrez la sous-clé qui correspond à la version que vous souhaitez vérifier.</span><span class="sxs-lookup"><span data-stu-id="c09c9-249">Open the subkey that matches the version you want to check.</span></span> <span data-ttu-id="c09c9-250">Utilisez le tableau de la section [détecter les .NET Framework 1,0 à 4,0](#detect-net-framework-10-through-40) .</span><span class="sxs-lookup"><span data-stu-id="c09c9-250">Use the table in the [Detect .NET Framework 1.0 through 4.0](#detect-net-framework-10-through-40) section.</span></span>

    <span data-ttu-id="c09c9-251">L’illustration suivante montre la sous-clé et sa valeur de **version** pour .NET Framework 3,5.</span><span class="sxs-lookup"><span data-stu-id="c09c9-251">The following figure shows the subkey and its **Version** value for .NET Framework 3.5.</span></span>

    <span data-ttu-id="c09c9-252">![Entrée de Registre pour .NET Framework 3,5.](./media/net-4-and-earlier.png ".NET Framework 3,5 et versions antérieures")</span><span class="sxs-lookup"><span data-stu-id="c09c9-252">![The registry entry for .NET Framework 3.5.](./media/net-4-and-earlier.png ".NET Framework 3.5 and earlier versions")</span></span>

### <a name="query-the-registry-using-code-older-framework-versions"></a><span data-ttu-id="c09c9-253">Interroger le registre à l’aide de code (versions antérieures du Framework)</span><span class="sxs-lookup"><span data-stu-id="c09c9-253">Query the registry using code (older framework versions)</span></span>

<span data-ttu-id="c09c9-254">Utilisez la <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> classe pour accéder à la sous-clé **\\ \\ NDP du \\ programme d’installation \\ de HKEY_LOCAL_MACHINE logiciel Microsoft NET Framework** dans le Registre Windows.</span><span class="sxs-lookup"><span data-stu-id="c09c9-254">Use the <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> class to access the **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP** subkey in the Windows registry.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c09c9-255">Si l’application que vous exécutez est 32 bits et s’exécute sous Windows 64 bits, les chemins d’accès au Registre sont différents de ceux indiqués précédemment.</span><span class="sxs-lookup"><span data-stu-id="c09c9-255">If the app you're running is 32-bit and running in 64-bit Windows, the registry paths will be different than previously listed.</span></span> <span data-ttu-id="c09c9-256">Le registre 64 bits est disponible dans la sous-clé **HKEY_LOCAL_MACHINE \\ Software \\ Wow6432Node \\** .</span><span class="sxs-lookup"><span data-stu-id="c09c9-256">The 64-bit registry is available in the **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\** subkey.</span></span> <span data-ttu-id="c09c9-257">Par exemple, la sous-clé de Registre pour .NET Framework 3,5 est **HKEY_LOCAL_MACHINE \\ logiciel \\ Wow6432Node \\ Microsoft \\ NET Framework Setup \\ NDP \\ v 3.5**.</span><span class="sxs-lookup"><span data-stu-id="c09c9-257">For example, the registry subkey for .NET Framework 3.5 is **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\NET Framework Setup\\NDP\\v3.5**.</span></span>

<span data-ttu-id="c09c9-258">L’exemple suivant recherche les versions de .NET Framework 1-4 qui sont installées :</span><span class="sxs-lookup"><span data-stu-id="c09c9-258">The following example finds the versions of .NET Framework 1-4 that are installed:</span></span>

:::code language="csharp" source="snippets/csharp/versions-installed.cs" id="1":::

:::code language="vb" source="snippets/visual-basic/versions-installed.vb" id="1":::

<span data-ttu-id="c09c9-259">L’exemple affiche une sortie similaire à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="c09c9-259">The example displays output similar to the following:</span></span>

```output
v2.0.50727  2.0.50727.4927  SP2
v3.0  3.0.30729.4926  SP2
v3.5  3.5.30729.4926  SP1
v4.0
  Client  4.0.0.0
```

## <a name="find-clr-versions"></a><span data-ttu-id="c09c9-260">Identifier les versions du CLR</span><span class="sxs-lookup"><span data-stu-id="c09c9-260">Find CLR versions</span></span>

<span data-ttu-id="c09c9-261">La .NET Framework CLR installée avec .NET Framework est gérée séparément.</span><span class="sxs-lookup"><span data-stu-id="c09c9-261">The .NET Framework CLR installed with .NET Framework is versioned separately.</span></span> <span data-ttu-id="c09c9-262">Il existe deux façons de détecter la version du .NET Framework CLR :</span><span class="sxs-lookup"><span data-stu-id="c09c9-262">There are two ways to detect the version of the .NET Framework CLR:</span></span>

- <span data-ttu-id="c09c9-263">**Outil Clrver.exe**</span><span class="sxs-lookup"><span data-stu-id="c09c9-263">**The Clrver.exe tool**</span></span>

  <span data-ttu-id="c09c9-264">Utilisez l' [outil CLR version (Clrver.exe)](../tools/clrver-exe-clr-version-tool.md) pour déterminer quelles versions du CLR sont installées sur un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="c09c9-264">Use the [CLR Version tool (Clrver.exe)](../tools/clrver-exe-clr-version-tool.md) to determine which versions of the CLR are installed on a computer.</span></span> <span data-ttu-id="c09c9-265">Ouvrez le [invite de commandes développeur pour Visual Studio](../tools/developer-command-prompt-for-vs.md) et entrez `clrver` .</span><span class="sxs-lookup"><span data-stu-id="c09c9-265">Open the [Developer Command Prompt for Visual Studio](../tools/developer-command-prompt-for-vs.md) and enter `clrver`.</span></span>

  <span data-ttu-id="c09c9-266">Exemple de sortie :</span><span class="sxs-lookup"><span data-stu-id="c09c9-266">Sample output:</span></span>

  ```console
  Versions installed on the machine:
  v2.0.50727
  v4.0.30319
  ```

- <span data-ttu-id="c09c9-267">**La `Environment` classe**</span><span class="sxs-lookup"><span data-stu-id="c09c9-267">**The `Environment` class**</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="c09c9-268">Pour .NET Framework 4,5 et versions ultérieures, n’utilisez pas la <xref:System.Environment.Version%2A?displayProperty=nameWithType> propriété pour détecter la version du CLR.</span><span class="sxs-lookup"><span data-stu-id="c09c9-268">For .NET Framework 4.5 and later versions, don't use the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property to detect the version of the CLR.</span></span> <span data-ttu-id="c09c9-269">Au lieu de cela, interrogez le registre comme décrit dans [détecter les .NET Framework 4,5 et versions ultérieures](#detect-net-framework-45-and-later-versions).</span><span class="sxs-lookup"><span data-stu-id="c09c9-269">Instead, query the registry as described in [Detect .NET Framework 4.5 and later versions](#detect-net-framework-45-and-later-versions).</span></span>

  1. <span data-ttu-id="c09c9-270">Interrogez la propriété <xref:System.Environment.Version?displayProperty=nameWithType> pour récupérer un objet <xref:System.Version>.</span><span class="sxs-lookup"><span data-stu-id="c09c9-270">Query the <xref:System.Environment.Version?displayProperty=nameWithType> property to retrieve a <xref:System.Version> object.</span></span>

     <span data-ttu-id="c09c9-271">L’objet `System.Version` retourné identifie la version du runtime qui est en train d’exécuter le code.</span><span class="sxs-lookup"><span data-stu-id="c09c9-271">The returned `System.Version` object identifies the version of the runtime that's currently executing the code.</span></span> <span data-ttu-id="c09c9-272">Il ne retourne pas les versions d’assembly ni d’autres versions du runtime susceptibles d’avoir été installées sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="c09c9-272">It doesn't return assembly versions or other versions of the runtime that may have been installed on the computer.</span></span>

     <span data-ttu-id="c09c9-273">Pour les versions .NET Framework 4, 4,5, 4.5.1 et 4.5.2, la représentation sous forme de chaîne de l' <xref:System.Version> objet retourné se présente sous la forme 4.0.30319.*xxxxx*, où *xxxxx* est inférieur à 42000.</span><span class="sxs-lookup"><span data-stu-id="c09c9-273">For .NET Framework versions 4, 4.5, 4.5.1, and 4.5.2, the string representation of the returned <xref:System.Version> object has the form 4.0.30319.*xxxxx*, where *xxxxx* is less than 42000.</span></span> <span data-ttu-id="c09c9-274">Pour .NET Framework 4,6 et versions ultérieures, il se présente sous la forme 4.0.30319.42000.</span><span class="sxs-lookup"><span data-stu-id="c09c9-274">For .NET Framework 4.6 and later versions, it has the form 4.0.30319.42000.</span></span>

  1. <span data-ttu-id="c09c9-275">Une fois que vous disposez de l’objet de **version** , interrogez-le comme suit :</span><span class="sxs-lookup"><span data-stu-id="c09c9-275">After you have the **Version** object, query it as follows:</span></span>

     - <span data-ttu-id="c09c9-276">Pour l’identificateur de la version majeure (par exemple, *4* pour la version 4.0), utilisez la propriété <xref:System.Version.Major%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c09c9-276">For the major release identifier (for example, *4* for version 4.0), use the <xref:System.Version.Major%2A?displayProperty=nameWithType> property.</span></span>

     - <span data-ttu-id="c09c9-277">Pour l’identificateur de la version mineure (par exemple, *0* pour la version 4.0), utilisez la propriété <xref:System.Version.Minor%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c09c9-277">For the minor release identifier (for example, *0* for version 4.0), use the <xref:System.Version.Minor%2A?displayProperty=nameWithType> property.</span></span>

     - <span data-ttu-id="c09c9-278">Pour la chaîne de la version entière (par exemple, *4.0.30319.18010*), utilisez la méthode <xref:System.Version.ToString%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c09c9-278">For the entire version string (for example, *4.0.30319.18010*), use the <xref:System.Version.ToString%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="c09c9-279">Cette méthode retourne une valeur unique qui reflète la version du runtime qui est en train d’exécuter le code.</span><span class="sxs-lookup"><span data-stu-id="c09c9-279">This method returns a single value that reflects the version of the runtime that's executing the code.</span></span> <span data-ttu-id="c09c9-280">Elle ne retourne pas les versions d’assembly ni d’autres versions du runtime susceptibles d’être installées sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="c09c9-280">It doesn't return assembly versions or other runtime versions that may be installed on the computer.</span></span>

  <span data-ttu-id="c09c9-281">L’exemple suivant utilise la propriété <xref:System.Environment.Version%2A?displayProperty=nameWithType> pour récupérer les informations de version du CLR :</span><span class="sxs-lookup"><span data-stu-id="c09c9-281">The following example uses the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property to retrieve CLR version information:</span></span>

  ```csharp
  Console.WriteLine($"Version: {Environment.Version}");
  ```

  ```vb
  Console.WriteLine($"Version: {Environment.Version}")
  ```

  <span data-ttu-id="c09c9-282">L’exemple affiche une sortie similaire à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="c09c9-282">The example displays output similar to the following:</span></span>

  ```output
  Version: 4.0.30319.18010
  ```

## <a name="see-also"></a><span data-ttu-id="c09c9-283">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c09c9-283">See also</span></span>

- [<span data-ttu-id="c09c9-284">Comment : déterminer les mises à jour de .NET Framework installées</span><span class="sxs-lookup"><span data-stu-id="c09c9-284">How to: Determine which .NET Framework updates are installed</span></span>](how-to-determine-which-net-framework-updates-are-installed.md)
- [<span data-ttu-id="c09c9-285">Installer .NET Framework pour les développeurs</span><span class="sxs-lookup"><span data-stu-id="c09c9-285">Install .NET Framework for developers</span></span>](../install/guide-for-developers.md)
- [<span data-ttu-id="c09c9-286">Versions et dépendances de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="c09c9-286">.NET Framework versions and dependencies</span></span>](versions-and-dependencies.md)
