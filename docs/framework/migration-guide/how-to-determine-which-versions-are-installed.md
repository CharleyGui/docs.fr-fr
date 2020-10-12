---
title: déterminer les versions du .NET Framework installées
description: Utilisez du code, regedit.exe ou PowerShell pour détecter les versions de .NET Framework qui sont installées sur un ordinateur en interrogeant le Registre Windows.
ms.date: 02/03/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- versions, determining for .NET Framework
- .NET Framework, determining version
ms.assetid: 40a67826-e4df-4f59-a651-d9eb0fdc755d
ms.openlocfilehash: faeb2c14b9c1d93b558c67a42c223702178407c0
ms.sourcegitcommit: b59237ca4ec763969a0dd775a3f8f39f8c59fe24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2020
ms.locfileid: "91955588"
---
# <a name="how-to-determine-which-net-framework-versions-are-installed"></a><span data-ttu-id="59e0b-103">Guide pratique pour déterminer les versions du .NET Framework installées</span><span class="sxs-lookup"><span data-stu-id="59e0b-103">How to: Determine which .NET Framework versions are installed</span></span>

<span data-ttu-id="59e0b-104">Les utilisateurs peuvent [installer](../install/index.md) et exécuter plusieurs versions de .NET Framework sur leurs ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="59e0b-104">Users can [install](../install/index.md) and run multiple versions of .NET Framework on their computers.</span></span> <span data-ttu-id="59e0b-105">Lorsque vous développez ou déployez votre application, vous devrez peut-être connaître les versions de .NET Framework qui sont installées sur l’ordinateur de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="59e0b-105">When you develop or deploy your app, you might need to know which .NET Framework versions are installed on the user's computer.</span></span> <span data-ttu-id="59e0b-106">Le registre contient une liste des versions de .NET Framework installées sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="59e0b-106">The registry contains a list of the versions of .NET Framework installed on the computer.</span></span>

<span data-ttu-id="59e0b-107">.NET Framework se compose de deux composants principaux, dont les versions sont gérées séparément :</span><span class="sxs-lookup"><span data-stu-id="59e0b-107">.NET Framework consists of two main components, which are versioned separately:</span></span>

- <span data-ttu-id="59e0b-108">Un jeu d'assemblys, qui correspondent aux collections de types et de ressources qui fournissent les fonctionnalités de vos applications.</span><span class="sxs-lookup"><span data-stu-id="59e0b-108">A set of assemblies, which are collections of types and resources that provide the functionality for your apps.</span></span> <span data-ttu-id="59e0b-109">.NET Framework et les assemblys partagent le même numéro de version.</span><span class="sxs-lookup"><span data-stu-id="59e0b-109">.NET Framework and the assemblies share the same version number.</span></span> <span data-ttu-id="59e0b-110">Par exemple, 4.5, 4.6.1 et 4.7.2 sont des versions de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="59e0b-110">For example, .NET Framework versions include 4.5, 4.6.1, and 4.7.2.</span></span>

- <span data-ttu-id="59e0b-111">Le Common Language Runtime (CLR), qui gère et exécute le code de votre application.</span><span class="sxs-lookup"><span data-stu-id="59e0b-111">The common language runtime (CLR), which manages and executes your app's code.</span></span> <span data-ttu-id="59e0b-112">En règle générale, une version particulière du CLR prend en charge plusieurs versions du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="59e0b-112">A single CLR version typically supports multiple .NET Framework versions.</span></span> <span data-ttu-id="59e0b-113">Par exemple, CLR version 4.0.30319. *xxxxx* où *xxxxx* est inférieur à 42000, prend en charge .NET Framework les versions 4 à 4.5.2.</span><span class="sxs-lookup"><span data-stu-id="59e0b-113">For example, CLR version 4.0.30319.*xxxxx* where *xxxxx* is less than 42000, supports .NET Framework versions 4 through 4.5.2.</span></span> <span data-ttu-id="59e0b-114">La version CLR supérieure ou égale à 4.0.30319.42000 prend en charge les versions .NET Framework à partir de .NET Framework 4,6.</span><span class="sxs-lookup"><span data-stu-id="59e0b-114">CLR version greater than or equal to 4.0.30319.42000 supports .NET Framework versions starting with .NET Framework 4.6.</span></span>

<span data-ttu-id="59e0b-115">Des outils gérés par la Communauté sont disponibles pour vous aider à détecter les versions de .NET Framework installées :</span><span class="sxs-lookup"><span data-stu-id="59e0b-115">Community-maintained tools are available to help detect which .NET Framework versions are installed:</span></span>

- [https://github.com/jmalarcon/DotNetVersions](https://github.com/jmalarcon/DotNetVersions)

  <span data-ttu-id="59e0b-116">Outil en ligne de commande .NET 2,0.</span><span class="sxs-lookup"><span data-stu-id="59e0b-116">A .NET 2.0 command-line tool.</span></span>

- [https://github.com/EliteLoser/DotNetVersionLister](https://github.com/EliteLoser/DotNetVersionLister)

  <span data-ttu-id="59e0b-117">Un module PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="59e0b-117">A PowerShell 2.0 module.</span></span>

<span data-ttu-id="59e0b-118">Pour plus d’informations sur la détection des mises à jour installées pour chaque version de .NET Framework, consultez [Comment : déterminer les mises à jour de .NET Framework installées](how-to-determine-which-net-framework-updates-are-installed.md).</span><span class="sxs-lookup"><span data-stu-id="59e0b-118">For information about detecting the installed updates for each version of .NET Framework, see [How to: Determine which .NET Framework updates are installed](how-to-determine-which-net-framework-updates-are-installed.md).</span></span>

## <a name="detect-net-framework-45-and-later-versions"></a><span data-ttu-id="59e0b-119">Détection des .NET Framework 4,5 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="59e0b-119">Detect .NET Framework 4.5 and later versions</span></span>

<span data-ttu-id="59e0b-120">La version de .NET Framework (4,5 et versions ultérieures) installée sur un ordinateur est listée dans le registre à l’adresse **HKEY_LOCAL_MACHINE \\ logiciel \\ Microsoft \\ NET Framework installation \\ NDP \\ v4 \\ Full**.</span><span class="sxs-lookup"><span data-stu-id="59e0b-120">The version of .NET Framework (4.5 and later) installed on a machine is listed in the registry at **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full**.</span></span> <span data-ttu-id="59e0b-121">Si la sous-clé **complète** est manquante, .NET Framework 4,5 ou version ultérieure n’est pas installé.</span><span class="sxs-lookup"><span data-stu-id="59e0b-121">If the **Full** subkey is missing, then .NET Framework 4.5 or above isn't installed.</span></span>

> [!NOTE]
> <span data-ttu-id="59e0b-122">La sous-clé **d’installation** du .NET Framework dans le chemin d’accès du registre ne commence *pas* par un point.</span><span class="sxs-lookup"><span data-stu-id="59e0b-122">The **NET Framework Setup** subkey in the registry path does *not* begin with a period.</span></span>

<span data-ttu-id="59e0b-123">La valeur de REG_DWORD de **version** dans le registre représente la version de .NET Framework installée.</span><span class="sxs-lookup"><span data-stu-id="59e0b-123">The **Release** REG_DWORD value in the registry represents the version of .NET Framework installed.</span></span>

<a name="version_table"></a>

| <span data-ttu-id="59e0b-124">Version du .NET Framework</span><span class="sxs-lookup"><span data-stu-id="59e0b-124">.NET Framework version</span></span> | <span data-ttu-id="59e0b-125">Valeur de la **mise en version**</span><span class="sxs-lookup"><span data-stu-id="59e0b-125">Value of **Release**</span></span> |
| ---------------------- | -------------------------- |
| <span data-ttu-id="59e0b-126">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="59e0b-126">.NET Framework 4.5</span></span>     | <span data-ttu-id="59e0b-127">Tous les systèmes d’exploitation Windows : 378389</span><span class="sxs-lookup"><span data-stu-id="59e0b-127">All Windows operating systems: 378389</span></span> |
| <span data-ttu-id="59e0b-128">.NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="59e0b-128">.NET Framework 4.5.1</span></span>   | <span data-ttu-id="59e0b-129">Sur Windows 8.1 et Windows Server 2012 R2:378675</span><span class="sxs-lookup"><span data-stu-id="59e0b-129">On Windows 8.1 and Windows Server 2012 R2: 378675</span></span><br /><span data-ttu-id="59e0b-130">Sur tous les autres systèmes d’exploitation Windows : 378758</span><span class="sxs-lookup"><span data-stu-id="59e0b-130">On all other Windows operating systems: 378758</span></span> |
| <span data-ttu-id="59e0b-131">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="59e0b-131">.NET Framework 4.5.2</span></span>   | <span data-ttu-id="59e0b-132">Tous les systèmes d’exploitation Windows : 379893</span><span class="sxs-lookup"><span data-stu-id="59e0b-132">All Windows operating systems: 379893</span></span> |
| <span data-ttu-id="59e0b-133">.NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="59e0b-133">.NET Framework 4.6</span></span>     | <span data-ttu-id="59e0b-134">Sur Windows 10:393295</span><span class="sxs-lookup"><span data-stu-id="59e0b-134">On Windows 10: 393295</span></span><br /><span data-ttu-id="59e0b-135">Sur tous les autres systèmes d’exploitation Windows : 393297</span><span class="sxs-lookup"><span data-stu-id="59e0b-135">On all other Windows operating systems: 393297</span></span> |
| <span data-ttu-id="59e0b-136">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="59e0b-136">.NET Framework 4.6.1</span></span>   | <span data-ttu-id="59e0b-137">Sur les systèmes Windows intégrant la mise à jour du 10 novembre : 394254</span><span class="sxs-lookup"><span data-stu-id="59e0b-137">On Windows 10 November Update systems: 394254</span></span><br /><span data-ttu-id="59e0b-138">Sur tous les autres systèmes d’exploitation Windows (y compris Windows 10) : 394271</span><span class="sxs-lookup"><span data-stu-id="59e0b-138">On all other Windows operating systems (including Windows 10): 394271</span></span> |
| <span data-ttu-id="59e0b-139">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="59e0b-139">.NET Framework 4.6.2</span></span>   | <span data-ttu-id="59e0b-140">Sur les systèmes Mise à jour anniversaire Windows 10 et Windows Server 2016 : 394802</span><span class="sxs-lookup"><span data-stu-id="59e0b-140">On Windows 10 Anniversary Update and Windows Server 2016: 394802</span></span><br /><span data-ttu-id="59e0b-141">Sur tous les autres systèmes d’exploitation Windows (y compris les autres systèmes d’exploitation Windows 10) : 394806</span><span class="sxs-lookup"><span data-stu-id="59e0b-141">On all other Windows operating systems (including other Windows 10 operating systems): 394806</span></span> |
| <span data-ttu-id="59e0b-142">.NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="59e0b-142">.NET Framework 4.7</span></span>     | <span data-ttu-id="59e0b-143">Sur Windows 10 Creators Update : 460798</span><span class="sxs-lookup"><span data-stu-id="59e0b-143">On Windows 10 Creators Update: 460798</span></span><br /><span data-ttu-id="59e0b-144">Sur tous les autres systèmes d’exploitation Windows (y compris les autres systèmes d’exploitation Windows 10) : 460805</span><span class="sxs-lookup"><span data-stu-id="59e0b-144">On all other Windows operating systems (including other Windows 10 operating systems): 460805</span></span> |
| <span data-ttu-id="59e0b-145">.NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="59e0b-145">.NET Framework 4.7.1</span></span>   | <span data-ttu-id="59e0b-146">Sur Windows 10 automne Creators Update et Windows Server, version 1709:461308</span><span class="sxs-lookup"><span data-stu-id="59e0b-146">On Windows 10 Fall Creators Update and Windows Server, version 1709: 461308</span></span><br/><span data-ttu-id="59e0b-147">Sur tous les autres systèmes d’exploitation Windows (y compris les autres systèmes d’exploitation Windows 10) : 461310</span><span class="sxs-lookup"><span data-stu-id="59e0b-147">On all other Windows operating systems (including other Windows 10 operating systems): 461310</span></span> |
| <span data-ttu-id="59e0b-148">.NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="59e0b-148">.NET Framework 4.7.2</span></span>   | <span data-ttu-id="59e0b-149">Sur Windows 10 avril 2018 mise à jour et Windows Server, version 1803:461808</span><span class="sxs-lookup"><span data-stu-id="59e0b-149">On Windows 10 April 2018 Update and Windows Server, version 1803: 461808</span></span><br/><span data-ttu-id="59e0b-150">Sur tous les systèmes d’exploitation Windows autres que Windows 10 avril 2018 Update et Windows Server, version 1803:461814</span><span class="sxs-lookup"><span data-stu-id="59e0b-150">On all Windows operating systems other than Windows 10 April 2018 Update and Windows Server, version 1803: 461814</span></span> |
| <span data-ttu-id="59e0b-151">.NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="59e0b-151">.NET Framework 4.8</span></span>     | <span data-ttu-id="59e0b-152">Sur Windows 10 mai 2019 mise à jour et Windows 10 novembre 2019 mise à jour : 528040</span><span class="sxs-lookup"><span data-stu-id="59e0b-152">On Windows 10 May 2019 Update and Windows 10 November 2019 Update: 528040</span></span><br/><span data-ttu-id="59e0b-153">Sur Windows 10 mai 2020 mise à jour : 528372</span><span class="sxs-lookup"><span data-stu-id="59e0b-153">On Windows 10 May 2020 Update: 528372</span></span><br/><span data-ttu-id="59e0b-154">Sur tous les autres systèmes d’exploitation Windows (y compris les autres systèmes d’exploitation Windows 10) : 528049</span><span class="sxs-lookup"><span data-stu-id="59e0b-154">On all other Windows operating systems (including other Windows 10 operating systems): 528049</span></span> |

### <a name="minimum-version"></a><span data-ttu-id="59e0b-155">Version minimale</span><span class="sxs-lookup"><span data-stu-id="59e0b-155">Minimum version</span></span>

<span data-ttu-id="59e0b-156">Pour déterminer si une version *minimale* de .NET Framework est présente, utilisez la plus petite valeur **de REG_DWORD de version pour** cette version à partir du tableau précédent.</span><span class="sxs-lookup"><span data-stu-id="59e0b-156">To determine whether a *minimum* version of .NET Framework is present, use the smallest **Release** REG_DWORD value for that version from the previous table.</span></span>

<span data-ttu-id="59e0b-157">Par exemple, si votre application s’exécute sous .NET Framework 4,8 ou une version ultérieure, testez une valeur de REG_DWORD de **mise en sortie** *supérieure ou égale à* 528040.</span><span class="sxs-lookup"><span data-stu-id="59e0b-157">For example, if your application runs under .NET Framework 4.8 or a later version, test for a **Release** REG_DWORD value that is *greater than or equal to* 528040.</span></span>

| <span data-ttu-id="59e0b-158">Version du .NET Framework</span><span class="sxs-lookup"><span data-stu-id="59e0b-158">.NET Framework version</span></span> | <span data-ttu-id="59e0b-159">Valeur minimale</span><span class="sxs-lookup"><span data-stu-id="59e0b-159">Minimum value</span></span> |
| ---------------------- | ------------- |
| <span data-ttu-id="59e0b-160">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="59e0b-160">.NET Framework 4.5</span></span>     | <span data-ttu-id="59e0b-161">378389</span><span class="sxs-lookup"><span data-stu-id="59e0b-161">378389</span></span> |
| <span data-ttu-id="59e0b-162">.NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="59e0b-162">.NET Framework 4.5.1</span></span>   | <span data-ttu-id="59e0b-163">378675</span><span class="sxs-lookup"><span data-stu-id="59e0b-163">378675</span></span> |
| <span data-ttu-id="59e0b-164">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="59e0b-164">.NET Framework 4.5.2</span></span>   | <span data-ttu-id="59e0b-165">379893</span><span class="sxs-lookup"><span data-stu-id="59e0b-165">379893</span></span> |
| <span data-ttu-id="59e0b-166">.NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="59e0b-166">.NET Framework 4.6</span></span>     | <span data-ttu-id="59e0b-167">393295</span><span class="sxs-lookup"><span data-stu-id="59e0b-167">393295</span></span> |
| <span data-ttu-id="59e0b-168">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="59e0b-168">.NET Framework 4.6.1</span></span>   | <span data-ttu-id="59e0b-169">394254</span><span class="sxs-lookup"><span data-stu-id="59e0b-169">394254</span></span> |
| <span data-ttu-id="59e0b-170">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="59e0b-170">.NET Framework 4.6.2</span></span>   | <span data-ttu-id="59e0b-171">394802</span><span class="sxs-lookup"><span data-stu-id="59e0b-171">394802</span></span> |
| <span data-ttu-id="59e0b-172">.NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="59e0b-172">.NET Framework 4.7</span></span>     | <span data-ttu-id="59e0b-173">460798</span><span class="sxs-lookup"><span data-stu-id="59e0b-173">460798</span></span> |
| <span data-ttu-id="59e0b-174">.NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="59e0b-174">.NET Framework 4.7.1</span></span>   | <span data-ttu-id="59e0b-175">461308</span><span class="sxs-lookup"><span data-stu-id="59e0b-175">461308</span></span> |
| <span data-ttu-id="59e0b-176">.NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="59e0b-176">.NET Framework 4.7.2</span></span>   | <span data-ttu-id="59e0b-177">461808</span><span class="sxs-lookup"><span data-stu-id="59e0b-177">461808</span></span> |
| <span data-ttu-id="59e0b-178">.NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="59e0b-178">.NET Framework 4.8</span></span>     | <span data-ttu-id="59e0b-179">528040</span><span class="sxs-lookup"><span data-stu-id="59e0b-179">528040</span></span> |

### <a name="use-registry-editor"></a><span data-ttu-id="59e0b-180">Utiliser l’éditeur du Registre</span><span class="sxs-lookup"><span data-stu-id="59e0b-180">Use Registry Editor</span></span>

01. <span data-ttu-id="59e0b-181">À partir du menu **Démarrer**, choisissez **Exécuter**, entrez *regedit*, puis sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="59e0b-181">From the **Start** menu, choose **Run**, enter *regedit*, and then select **OK**.</span></span>

   <span data-ttu-id="59e0b-182">(Vous devez disposer d’informations d’identification d’administration pour exécuter regedit.)</span><span class="sxs-lookup"><span data-stu-id="59e0b-182">(You must have administrative credentials to run regedit.)</span></span>

01. <span data-ttu-id="59e0b-183">Dans l’éditeur du Registre, ouvrez la sous-clé suivante : **HKEY_LOCAL_MACHINE \\ logiciel \\ Microsoft \\ NET Framework installation \\ NDP \\ v4 \\ Full**.</span><span class="sxs-lookup"><span data-stu-id="59e0b-183">In the Registry Editor, open the following subkey: **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full**.</span></span> <span data-ttu-id="59e0b-184">Si la sous-clé **complète** n’est pas présente, vous n’avez pas .NET Framework 4,5 ou une version ultérieure installée.</span><span class="sxs-lookup"><span data-stu-id="59e0b-184">If the **Full** subkey isn't present, then you don't have .NET Framework 4.5 or later installed.</span></span>

01. <span data-ttu-id="59e0b-185">Recherchez une entrée de REG_DWORD nommée **Release**.</span><span class="sxs-lookup"><span data-stu-id="59e0b-185">Check for a REG_DWORD entry named **Release**.</span></span> <span data-ttu-id="59e0b-186">S’il existe, .NET Framework 4,5 ou version ultérieure est installé.</span><span class="sxs-lookup"><span data-stu-id="59e0b-186">If it exists, then you have .NET Framework 4.5 or later installed.</span></span> <span data-ttu-id="59e0b-187">Sa valeur correspond à une version particulière de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="59e0b-187">Its value corresponds to a particular version of .NET Framework.</span></span> <span data-ttu-id="59e0b-188">Dans l’illustration suivante, par exemple, la valeur de l’entrée de **version** est 528040, qui est la clé de mise en version de .NET Framework 4,8.</span><span class="sxs-lookup"><span data-stu-id="59e0b-188">In the following figure, for example, the value of the **Release** entry is 528040, which is the release key for .NET Framework 4.8.</span></span>

   ![Entrée de Registre pour .NET Framework 4,5](./media/clr-installdir.png )

### <a name="use-powershell-to-check-for-a-minimum-version"></a><span data-ttu-id="59e0b-190">Utiliser PowerShell pour vérifier la version minimale</span><span class="sxs-lookup"><span data-stu-id="59e0b-190">Use PowerShell to check for a minimum version</span></span>

<span data-ttu-id="59e0b-191">Utilisez les commandes PowerShell pour vérifier la valeur de l’entrée de **publication** de l’HKEY_LOCAL_MACHINE sous-clé complète de l' \*\*installation du \\ logiciel \\ Microsoft \\ NET Framework, \\ NDP \\ v4 \\ \*\* .</span><span class="sxs-lookup"><span data-stu-id="59e0b-191">Use PowerShell commands to check the value of the **Release** entry of the **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full** subkey.</span></span>

<span data-ttu-id="59e0b-192">Les exemples suivants vérifient la valeur de l’entrée de **mise en sortie** pour déterminer si .NET Framework 4.6.2 ou version ultérieure est installé.</span><span class="sxs-lookup"><span data-stu-id="59e0b-192">The following examples check the value of the **Release** entry to determine whether .NET Framework 4.6.2 or later is installed.</span></span> <span data-ttu-id="59e0b-193">Ce code retourne `True` s’il est installé et `False` dans le cas contraire.</span><span class="sxs-lookup"><span data-stu-id="59e0b-193">This code returns `True` if it's installed and `False` otherwise.</span></span>

```powershell
(Get-ItemProperty "HKLM:SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full").Release -ge 394802
```

### <a name="query-the-registry-using-code"></a><span data-ttu-id="59e0b-194">Interroger le registre à l’aide de code</span><span class="sxs-lookup"><span data-stu-id="59e0b-194">Query the registry using code</span></span>

01. <span data-ttu-id="59e0b-195">Utilisez les <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType> méthodes et pour accéder à la sous-clé complète du \*\* \\ \\ programme d’installation de HKEY_LOCAL_MACHINE logiciel Microsoft \\ NET Framework, \\ NDP \\ \\ v4\*\* , dans le Registre Windows.</span><span class="sxs-lookup"><span data-stu-id="59e0b-195">Use the <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> and <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType> methods to access the **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full** subkey in the Windows registry.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="59e0b-196">Si l’application que vous exécutez est 32 bits et s’exécute sous Windows 64 bits, les chemins d’accès au Registre sont différents de ceux indiqués précédemment.</span><span class="sxs-lookup"><span data-stu-id="59e0b-196">If the app you're running is 32-bit and running in 64-bit Windows, the registry paths will be different than previously listed.</span></span> <span data-ttu-id="59e0b-197">Le registre 64 bits est disponible dans la sous-clé \*\*HKEY_LOCAL_MACHINE \\ Software \\ Wow6432Node \\ \*\* .</span><span class="sxs-lookup"><span data-stu-id="59e0b-197">The 64-bit registry is available in the **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\** subkey.</span></span> <span data-ttu-id="59e0b-198">Par exemple, la sous-clé de Registre pour .NET Framework 4,5 est **HKEY_LOCAL_MACHINE \\ logiciel \\ Wow6432Node \\ Microsoft \\ NET Framework Setup \\ NDP \\ v4 \\ complet**.</span><span class="sxs-lookup"><span data-stu-id="59e0b-198">For example, the registry subkey for .NET Framework 4.5 is **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full**.</span></span>

01. <span data-ttu-id="59e0b-199">Vérifiez la valeur REG_DWORD de **version** pour déterminer la version installée.</span><span class="sxs-lookup"><span data-stu-id="59e0b-199">Check the **Release** REG_DWORD value to determine the installed version.</span></span> <span data-ttu-id="59e0b-200">Pour être compatible, recherchez une valeur supérieure ou égale à la valeur listée dans le [tableau des versions du .NET Framework](#version_table).</span><span class="sxs-lookup"><span data-stu-id="59e0b-200">To be forward-compatible, check for a value greater than or equal to the value listed in the [.NET Framework version table](#version_table).</span></span>

<span data-ttu-id="59e0b-201">L’exemple suivant vérifie la valeur de l’entrée de **publication** dans le registre pour rechercher les versions de .NET Framework 4.5-4.8 qui sont installées :</span><span class="sxs-lookup"><span data-stu-id="59e0b-201">The following example checks the value of the **Release** entry in the registry to find the versions of .NET Framework 4.5-4.8 that are installed:</span></span>

:::code language="csharp" source="snippets/csharp/versions-installed.cs" id="2":::

:::code language="vb" source="snippets/visual-basic/versions-installed.vb" id="2":::

<span data-ttu-id="59e0b-202">L’exemple affiche une sortie similaire à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="59e0b-202">The example displays output like the following:</span></span>

```output
.NET Framework Version: 4.6.1
```

<span data-ttu-id="59e0b-203">Cet exemple suit la pratique recommandée concernant la vérification de version :</span><span class="sxs-lookup"><span data-stu-id="59e0b-203">This example follows the recommended practice for version checking:</span></span>

- <span data-ttu-id="59e0b-204">Il vérifie si la valeur de l’entrée **Release** est *supérieure ou égale à* la valeur des clés de version connues.</span><span class="sxs-lookup"><span data-stu-id="59e0b-204">It checks whether the value of the **Release** entry is *greater than or equal to* the value of the known release keys.</span></span>
- <span data-ttu-id="59e0b-205">Il effectue sa vérification en partant de la version la plus récente vers la version la plus ancienne.</span><span class="sxs-lookup"><span data-stu-id="59e0b-205">It checks in order from most recent version to earliest version.</span></span>

## <a name="detect-net-framework-10-through-40"></a><span data-ttu-id="59e0b-206">Détection des .NET Framework 1,0 à 4,0</span><span class="sxs-lookup"><span data-stu-id="59e0b-206">Detect .NET Framework 1.0 through 4.0</span></span>

<span data-ttu-id="59e0b-207">Chaque version de .NET Framework de 1,1 à 4,0 est indiquée sous la forme d’une sous-clé dans **HKEY_LOCAL_MACHINE \\ logiciel \\ Microsoft \\ NET Framework Setup \\ NDP**.</span><span class="sxs-lookup"><span data-stu-id="59e0b-207">Each version of .NET Framework from 1.1 to 4.0 is listed as a subkey at **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP**.</span></span> <span data-ttu-id="59e0b-208">Le tableau suivant répertorie le chemin d’accès à chaque version de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="59e0b-208">The following table lists the path to each .NET Framework version.</span></span> <span data-ttu-id="59e0b-209">Pour la plupart des versions, il existe une valeur d' **installation** REG_DWORD de `1` pour indiquer que cette version est installée.</span><span class="sxs-lookup"><span data-stu-id="59e0b-209">For most versions, there's an **Install** REG_DWORD value of `1` to indicate this version is installed.</span></span> <span data-ttu-id="59e0b-210">Dans ces sous-clés, il y a également une valeur de REG_SZ de **version** qui contient une chaîne de version.</span><span class="sxs-lookup"><span data-stu-id="59e0b-210">In these subkeys, there's also a **Version** REG_SZ value that contains a version string.</span></span>

> [!NOTE]
> <span data-ttu-id="59e0b-211">La sous-clé **d’installation** du .NET Framework dans le chemin d’accès du registre ne commence *pas* par un point.</span><span class="sxs-lookup"><span data-stu-id="59e0b-211">The **NET Framework Setup** subkey in the registry path does *not* begin with a period.</span></span>

| <span data-ttu-id="59e0b-212">Version du Framework</span><span class="sxs-lookup"><span data-stu-id="59e0b-212">Framework Version</span></span>  | <span data-ttu-id="59e0b-213">Sous-clé de Registre</span><span class="sxs-lookup"><span data-stu-id="59e0b-213">Registry Subkey</span></span> | <span data-ttu-id="59e0b-214">Valeur</span><span class="sxs-lookup"><span data-stu-id="59e0b-214">Value</span></span> |
| ------------------ | --------------- | ----- |
| <span data-ttu-id="59e0b-215">1.0</span><span class="sxs-lookup"><span data-stu-id="59e0b-215">1.0</span></span>                | <span data-ttu-id="59e0b-216">**HKLM \\ Software \\ Microsoft \\ . \\Stratégie NETFramework \\ v 1.0 \\ 3705**</span><span class="sxs-lookup"><span data-stu-id="59e0b-216">**HKLM\\Software\\Microsoft\\.NETFramework\\Policy\\v1.0\\3705**</span></span>     | <span data-ttu-id="59e0b-217">**Installer** REG_SZ est égal à `1`</span><span class="sxs-lookup"><span data-stu-id="59e0b-217">**Install** REG_SZ equals `1`</span></span> |
| <span data-ttu-id="59e0b-218">1.1</span><span class="sxs-lookup"><span data-stu-id="59e0b-218">1.1</span></span>                | <span data-ttu-id="59e0b-219">**HKLM \\ Software \\ Microsoft \\ NET Framework Setup \\ NDP \\ v 1.1.4322**</span><span class="sxs-lookup"><span data-stu-id="59e0b-219">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v1.1.4322**</span></span>   | <span data-ttu-id="59e0b-220">**Installer** REG_DWORD est égal à `1`</span><span class="sxs-lookup"><span data-stu-id="59e0b-220">**Install** REG_DWORD equals `1`</span></span> |
| <span data-ttu-id="59e0b-221">2.0</span><span class="sxs-lookup"><span data-stu-id="59e0b-221">2.0</span></span>                | <span data-ttu-id="59e0b-222">**HKLM \\ Software \\ Microsoft \\ .NET Framework Setup \\ NDP \\ v 2.0.50727**</span><span class="sxs-lookup"><span data-stu-id="59e0b-222">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v2.0.50727**</span></span>  | <span data-ttu-id="59e0b-223">**Installer** REG_DWORD est égal à `1`</span><span class="sxs-lookup"><span data-stu-id="59e0b-223">**Install** REG_DWORD equals `1`</span></span> |
| <span data-ttu-id="59e0b-224">3.0</span><span class="sxs-lookup"><span data-stu-id="59e0b-224">3.0</span></span>                | <span data-ttu-id="59e0b-225">**HKLM \\ Software \\ Microsoft \\ .NET Framework Setup \\ NDP \\ v 3.0 \\ installation**</span><span class="sxs-lookup"><span data-stu-id="59e0b-225">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v3.0\\Setup**</span></span> | <span data-ttu-id="59e0b-226">**InstallSuccess** REG_DWORD est égal à `1`</span><span class="sxs-lookup"><span data-stu-id="59e0b-226">**InstallSuccess** REG_DWORD equals `1`</span></span> |
| <span data-ttu-id="59e0b-227">3,5</span><span class="sxs-lookup"><span data-stu-id="59e0b-227">3.5</span></span>                | <span data-ttu-id="59e0b-228">**HKLM \\ Software \\ Microsoft \\ NET Framework Setup \\ NDP \\ v 3.5**</span><span class="sxs-lookup"><span data-stu-id="59e0b-228">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v3.5**</span></span>        | <span data-ttu-id="59e0b-229">**Installer** REG_DWORD est égal à `1`</span><span class="sxs-lookup"><span data-stu-id="59e0b-229">**Install** REG_DWORD equals `1`</span></span> |
| <span data-ttu-id="59e0b-230">Profil client 4,0</span><span class="sxs-lookup"><span data-stu-id="59e0b-230">4.0 Client Profile</span></span> | <span data-ttu-id="59e0b-231">**HKLM \\ Software \\ Microsoft \\ .NET Framework installation de \\ NDP \\ v4 \\ client**</span><span class="sxs-lookup"><span data-stu-id="59e0b-231">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v4\\Client**</span></span>  | <span data-ttu-id="59e0b-232">**Installer** REG_DWORD est égal à `1`</span><span class="sxs-lookup"><span data-stu-id="59e0b-232">**Install** REG_DWORD equals `1`</span></span> |
| <span data-ttu-id="59e0b-233">Profil complet 4,0</span><span class="sxs-lookup"><span data-stu-id="59e0b-233">4.0 Full Profile</span></span>   | <span data-ttu-id="59e0b-234">**HKLM version du \\ \\ \\ programme d’installation de Microsoft NET Framework, \\ NDP \\ v4 \\ complet**</span><span class="sxs-lookup"><span data-stu-id="59e0b-234">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full**</span></span>    | <span data-ttu-id="59e0b-235">**Installer** REG_DWORD est égal à `1`</span><span class="sxs-lookup"><span data-stu-id="59e0b-235">**Install** REG_DWORD equals `1`</span></span> |

> [!IMPORTANT]
> <span data-ttu-id="59e0b-236">Si l’application que vous exécutez est 32 bits et s’exécute sous Windows 64 bits, les chemins d’accès au Registre sont différents de ceux indiqués précédemment.</span><span class="sxs-lookup"><span data-stu-id="59e0b-236">If the app you're running is 32-bit and running in 64-bit Windows, the registry paths will be different than previously listed.</span></span> <span data-ttu-id="59e0b-237">Le registre 64 bits est disponible dans la sous-clé \*\*HKEY_LOCAL_MACHINE \\ Software \\ Wow6432Node \\ \*\* .</span><span class="sxs-lookup"><span data-stu-id="59e0b-237">The 64-bit registry is available in the **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\** subkey.</span></span> <span data-ttu-id="59e0b-238">Par exemple, la sous-clé de Registre pour .NET Framework 3,5 est **HKEY_LOCAL_MACHINE \\ logiciel \\ Wow6432Node \\ Microsoft \\ NET Framework Setup \\ NDP \\ v 3.5**.</span><span class="sxs-lookup"><span data-stu-id="59e0b-238">For example, the registry subkey for .NET Framework 3.5 is **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\NET Framework Setup\\NDP\\v3.5**.</span></span>

<span data-ttu-id="59e0b-239">Notez que le chemin d’accès au registre de la sous-clé .NET Framework 1,0 est différent des autres.</span><span class="sxs-lookup"><span data-stu-id="59e0b-239">Notice that the registry path to the .NET Framework 1.0 subkey is different from the others.</span></span>

### <a name="use-registry-editor-older-framework-versions"></a><span data-ttu-id="59e0b-240">Utiliser l’éditeur du Registre (versions antérieures de l’infrastructure)</span><span class="sxs-lookup"><span data-stu-id="59e0b-240">Use Registry Editor (older framework versions)</span></span>

01. <span data-ttu-id="59e0b-241">À partir du menu **Démarrer**, choisissez **Exécuter**, entrez *regedit*, puis sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="59e0b-241">From the **Start** menu, choose **Run**, enter *regedit*, and then select **OK**.</span></span>

    <span data-ttu-id="59e0b-242">Vous devez disposer d’informations d’identification d’administrateur pour exécuter regedit.</span><span class="sxs-lookup"><span data-stu-id="59e0b-242">You must have administrative credentials to run regedit.</span></span>

01. <span data-ttu-id="59e0b-243">Ouvrez la sous-clé qui correspond à la version que vous souhaitez vérifier.</span><span class="sxs-lookup"><span data-stu-id="59e0b-243">Open the subkey that matches the version you want to check.</span></span> <span data-ttu-id="59e0b-244">Utilisez le tableau de la section [détecter les .NET Framework 1,0 à 4,0](#detect-net-framework-10-through-40) .</span><span class="sxs-lookup"><span data-stu-id="59e0b-244">Use the table in the [Detect .NET Framework 1.0 through 4.0](#detect-net-framework-10-through-40) section.</span></span>

    <span data-ttu-id="59e0b-245">L’illustration suivante montre la sous-clé et sa valeur de **version** pour .NET Framework 3,5.</span><span class="sxs-lookup"><span data-stu-id="59e0b-245">The following figure shows the subkey and its **Version** value for .NET Framework 3.5.</span></span>

    <span data-ttu-id="59e0b-246">![Entrée de Registre pour .NET Framework 3,5.](./media/net-4-and-earlier.png ".NET Framework 3,5 et versions antérieures")</span><span class="sxs-lookup"><span data-stu-id="59e0b-246">![The registry entry for .NET Framework 3.5.](./media/net-4-and-earlier.png ".NET Framework 3.5 and earlier versions")</span></span>

### <a name="query-the-registry-using-code-older-framework-versions"></a><span data-ttu-id="59e0b-247">Interroger le registre à l’aide de code (versions antérieures du Framework)</span><span class="sxs-lookup"><span data-stu-id="59e0b-247">Query the registry using code (older framework versions)</span></span>

<span data-ttu-id="59e0b-248">Utilisez la <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> classe pour accéder à la sous-clé \*\* \\ \\ NDP du \\ programme d’installation \\ de HKEY_LOCAL_MACHINE logiciel Microsoft NET Framework\*\* dans le Registre Windows.</span><span class="sxs-lookup"><span data-stu-id="59e0b-248">Use the <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> class to access the **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP** subkey in the Windows registry.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="59e0b-249">Si l’application que vous exécutez est 32 bits et s’exécute sous Windows 64 bits, les chemins d’accès au Registre sont différents de ceux indiqués précédemment.</span><span class="sxs-lookup"><span data-stu-id="59e0b-249">If the app you're running is 32-bit and running in 64-bit Windows, the registry paths will be different than previously listed.</span></span> <span data-ttu-id="59e0b-250">Le registre 64 bits est disponible dans la sous-clé \*\*HKEY_LOCAL_MACHINE \\ Software \\ Wow6432Node \\ \*\* .</span><span class="sxs-lookup"><span data-stu-id="59e0b-250">The 64-bit registry is available in the **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\** subkey.</span></span> <span data-ttu-id="59e0b-251">Par exemple, la sous-clé de Registre pour .NET Framework 3,5 est **HKEY_LOCAL_MACHINE \\ logiciel \\ Wow6432Node \\ Microsoft \\ NET Framework Setup \\ NDP \\ v 3.5**.</span><span class="sxs-lookup"><span data-stu-id="59e0b-251">For example, the registry subkey for .NET Framework 3.5 is **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\NET Framework Setup\\NDP\\v3.5**.</span></span>

<span data-ttu-id="59e0b-252">L’exemple suivant recherche les versions de .NET Framework 1-4 qui sont installées :</span><span class="sxs-lookup"><span data-stu-id="59e0b-252">The following example finds the versions of .NET Framework 1-4 that are installed:</span></span>

:::code language="csharp" source="snippets/csharp/versions-installed.cs" id="1":::

:::code language="vb" source="snippets/visual-basic/versions-installed.vb" id="1":::

<span data-ttu-id="59e0b-253">L’exemple affiche une sortie similaire à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="59e0b-253">The example displays output similar to the following:</span></span>

```output
v2.0.50727  2.0.50727.4927  SP2
v3.0  3.0.30729.4926  SP2
v3.5  3.5.30729.4926  SP1
v4.0
  Client  4.0.0.0
```

## <a name="find-clr-versions"></a><span data-ttu-id="59e0b-254">Identifier les versions du CLR</span><span class="sxs-lookup"><span data-stu-id="59e0b-254">Find CLR versions</span></span>

<span data-ttu-id="59e0b-255">La .NET Framework CLR installée avec .NET Framework est gérée séparément.</span><span class="sxs-lookup"><span data-stu-id="59e0b-255">The .NET Framework CLR installed with .NET Framework is versioned separately.</span></span> <span data-ttu-id="59e0b-256">Il existe deux façons de détecter la version du .NET Framework CLR :</span><span class="sxs-lookup"><span data-stu-id="59e0b-256">There are two ways to detect the version of the .NET Framework CLR:</span></span>

- <span data-ttu-id="59e0b-257">**Outil Clrver.exe**</span><span class="sxs-lookup"><span data-stu-id="59e0b-257">**The Clrver.exe tool**</span></span>

  <span data-ttu-id="59e0b-258">Utilisez l' [outil CLR version (Clrver.exe)](../tools/clrver-exe-clr-version-tool.md) pour déterminer quelles versions du CLR sont installées sur un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="59e0b-258">Use the [CLR Version tool (Clrver.exe)](../tools/clrver-exe-clr-version-tool.md) to determine which versions of the CLR are installed on a computer.</span></span> <span data-ttu-id="59e0b-259">Ouvrez le [invite de commandes développeur pour Visual Studio](../tools/developer-command-prompt-for-vs.md) et entrez `clrver` .</span><span class="sxs-lookup"><span data-stu-id="59e0b-259">Open the [Developer Command Prompt for Visual Studio](../tools/developer-command-prompt-for-vs.md) and enter `clrver`.</span></span>

  <span data-ttu-id="59e0b-260">Exemple de sortie :</span><span class="sxs-lookup"><span data-stu-id="59e0b-260">Sample output:</span></span>

  ```console
  Versions installed on the machine:
  v2.0.50727
  v4.0.30319
  ```

- <span data-ttu-id="59e0b-261">**La `Environment` classe**</span><span class="sxs-lookup"><span data-stu-id="59e0b-261">**The `Environment` class**</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="59e0b-262">Pour .NET Framework 4,5 et versions ultérieures, n’utilisez pas la <xref:System.Environment.Version%2A?displayProperty=nameWithType> propriété pour détecter la version du CLR.</span><span class="sxs-lookup"><span data-stu-id="59e0b-262">For .NET Framework 4.5 and later versions, don't use the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property to detect the version of the CLR.</span></span> <span data-ttu-id="59e0b-263">Au lieu de cela, interrogez le registre comme décrit dans [détecter les .NET Framework 4,5 et versions ultérieures](#detect-net-framework-45-and-later-versions).</span><span class="sxs-lookup"><span data-stu-id="59e0b-263">Instead, query the registry as described in [Detect .NET Framework 4.5 and later versions](#detect-net-framework-45-and-later-versions).</span></span>

  1. <span data-ttu-id="59e0b-264">Interrogez la propriété <xref:System.Environment.Version?displayProperty=nameWithType> pour récupérer un objet <xref:System.Version>.</span><span class="sxs-lookup"><span data-stu-id="59e0b-264">Query the <xref:System.Environment.Version?displayProperty=nameWithType> property to retrieve a <xref:System.Version> object.</span></span>

     <span data-ttu-id="59e0b-265">L’objet `System.Version` retourné identifie la version du runtime qui est en train d’exécuter le code.</span><span class="sxs-lookup"><span data-stu-id="59e0b-265">The returned `System.Version` object identifies the version of the runtime that's currently executing the code.</span></span> <span data-ttu-id="59e0b-266">Il ne retourne pas les versions d’assembly ni d’autres versions du runtime susceptibles d’avoir été installées sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="59e0b-266">It doesn't return assembly versions or other versions of the runtime that may have been installed on the computer.</span></span>

     <span data-ttu-id="59e0b-267">Pour les versions .NET Framework 4, 4,5, 4.5.1 et 4.5.2, la représentation sous forme de chaîne de l' <xref:System.Version> objet retourné se présente sous la forme 4.0.30319.\* xxxxx\*, où *xxxxx* est inférieur à 42000.</span><span class="sxs-lookup"><span data-stu-id="59e0b-267">For .NET Framework versions 4, 4.5, 4.5.1, and 4.5.2, the string representation of the returned <xref:System.Version> object has the form 4.0.30319.*xxxxx*, where *xxxxx* is less than 42000.</span></span> <span data-ttu-id="59e0b-268">Pour .NET Framework 4,6 et versions ultérieures, il se présente sous la forme 4.0.30319.42000.</span><span class="sxs-lookup"><span data-stu-id="59e0b-268">For .NET Framework 4.6 and later versions, it has the form 4.0.30319.42000.</span></span>

  1. <span data-ttu-id="59e0b-269">Une fois que vous disposez de l’objet de **version** , interrogez-le comme suit :</span><span class="sxs-lookup"><span data-stu-id="59e0b-269">After you have the **Version** object, query it as follows:</span></span>

     - <span data-ttu-id="59e0b-270">Pour l’identificateur de la version majeure (par exemple, *4* pour la version 4.0), utilisez la propriété <xref:System.Version.Major%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="59e0b-270">For the major release identifier (for example, *4* for version 4.0), use the <xref:System.Version.Major%2A?displayProperty=nameWithType> property.</span></span>

     - <span data-ttu-id="59e0b-271">Pour l’identificateur de la version mineure (par exemple, *0* pour la version 4.0), utilisez la propriété <xref:System.Version.Minor%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="59e0b-271">For the minor release identifier (for example, *0* for version 4.0), use the <xref:System.Version.Minor%2A?displayProperty=nameWithType> property.</span></span>

     - <span data-ttu-id="59e0b-272">Pour la chaîne de la version entière (par exemple, *4.0.30319.18010*), utilisez la méthode <xref:System.Version.ToString%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="59e0b-272">For the entire version string (for example, *4.0.30319.18010*), use the <xref:System.Version.ToString%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="59e0b-273">Cette méthode retourne une valeur unique qui reflète la version du runtime qui est en train d’exécuter le code.</span><span class="sxs-lookup"><span data-stu-id="59e0b-273">This method returns a single value that reflects the version of the runtime that's executing the code.</span></span> <span data-ttu-id="59e0b-274">Elle ne retourne pas les versions d’assembly ni d’autres versions du runtime susceptibles d’être installées sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="59e0b-274">It doesn't return assembly versions or other runtime versions that may be installed on the computer.</span></span>

  <span data-ttu-id="59e0b-275">L’exemple suivant utilise la propriété <xref:System.Environment.Version%2A?displayProperty=nameWithType> pour récupérer les informations de version du CLR :</span><span class="sxs-lookup"><span data-stu-id="59e0b-275">The following example uses the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property to retrieve CLR version information:</span></span>

  ```csharp
  Console.WriteLine($"Version: {Environment.Version}");
  ```

  ```vb
  Console.WriteLine($"Version: {Environment.Version}")
  ```

  <span data-ttu-id="59e0b-276">L’exemple affiche une sortie similaire à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="59e0b-276">The example displays output similar to the following:</span></span>

  ```output
  Version: 4.0.30319.18010
  ```

## <a name="see-also"></a><span data-ttu-id="59e0b-277">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="59e0b-277">See also</span></span>

- [<span data-ttu-id="59e0b-278">Comment : déterminer les mises à jour de .NET Framework installées</span><span class="sxs-lookup"><span data-stu-id="59e0b-278">How to: Determine which .NET Framework updates are installed</span></span>](how-to-determine-which-net-framework-updates-are-installed.md)
- [<span data-ttu-id="59e0b-279">Installer .NET Framework pour les développeurs</span><span class="sxs-lookup"><span data-stu-id="59e0b-279">Install .NET Framework for developers</span></span>](../install/guide-for-developers.md)
- [<span data-ttu-id="59e0b-280">Versions et dépendances de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="59e0b-280">.NET Framework versions and dependencies</span></span>](versions-and-dependencies.md)
