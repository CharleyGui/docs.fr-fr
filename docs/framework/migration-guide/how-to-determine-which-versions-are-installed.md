---
title: déterminer les versions du .NET Framework installées
ms.date: 04/18/2019
dev_langs:
- csharp
- vb
ms.custom: updateeachrelease
helpviewer_keywords:
- versions, determining for .NET Framework
- .NET Framework, determining version
ms.assetid: 40a67826-e4df-4f59-a651-d9eb0fdc755d
ms.openlocfilehash: b860aac01780acb67c53e822eff478b78198996b
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738192"
---
# <a name="how-to-determine-which-net-framework-versions-are-installed"></a><span data-ttu-id="52ee1-102">Guide pratique pour déterminer les versions du .NET Framework installées</span><span class="sxs-lookup"><span data-stu-id="52ee1-102">How to: Determine which .NET Framework versions are installed</span></span>

<span data-ttu-id="52ee1-103">Les utilisateurs peuvent [installer](../install/index.md) et exécuter plusieurs versions du .NET Framework sur leurs ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="52ee1-103">Users can [install](../install/index.md) and run multiple versions of the .NET Framework on their computers.</span></span> <span data-ttu-id="52ee1-104">Quand vous développez ou déployez votre application, vous pouvez avoir besoin de savoir quelles versions de .NET Framework sont installées sur l'ordinateur de l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="52ee1-104">When you develop or deploy your app, you might need to know which .NET Framework versions are installed on the user’s computer.</span></span>

<span data-ttu-id="52ee1-105">Le .NET Framework comporte deux principaux composants, dont les versions sont définies séparément :</span><span class="sxs-lookup"><span data-stu-id="52ee1-105">The .NET Framework consists of two main components, which are versioned separately:</span></span>

- <span data-ttu-id="52ee1-106">Un jeu d'assemblys, qui correspondent aux collections de types et de ressources qui fournissent les fonctionnalités de vos applications.</span><span class="sxs-lookup"><span data-stu-id="52ee1-106">A set of assemblies, which are collections of types and resources that provide the functionality for your apps.</span></span> <span data-ttu-id="52ee1-107">.NET Framework et les assemblys partagent le même numéro de version.</span><span class="sxs-lookup"><span data-stu-id="52ee1-107">The .NET Framework and assemblies share the same version number.</span></span>

- <span data-ttu-id="52ee1-108">Le Common Language Runtime (CLR), qui gère et exécute le code de votre application.</span><span class="sxs-lookup"><span data-stu-id="52ee1-108">The common language runtime (CLR), which manages and executes your app's code.</span></span> <span data-ttu-id="52ee1-109">Le CLR est identifié par son propre numéro de version (consultez [versions et dépendances](versions-and-dependencies.md)).</span><span class="sxs-lookup"><span data-stu-id="52ee1-109">The CLR is identified by its own version number (see [Versions and dependencies](versions-and-dependencies.md)).</span></span>

> [!NOTE]
> <span data-ttu-id="52ee1-110">Chaque nouvelle version du .NET Framework conserve les fonctionnalités des versions antérieures et en ajoute de nouvelles.</span><span class="sxs-lookup"><span data-stu-id="52ee1-110">Each new version of the .NET Framework retains features from the previous versions and adds new features.</span></span> <span data-ttu-id="52ee1-111">Vous pouvez charger plusieurs versions du .NET Framework sur un seul ordinateur en même temps, ce qui signifie que vous pouvez installer le .NET Framework sans avoir à désinstaller les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="52ee1-111">You can load multiple versions of the .NET Framework on a single computer at the same time, which means that you can install the .NET Framework without having to uninstall previous versions.</span></span> <span data-ttu-id="52ee1-112">En règle générale, il est préférable de ne pas désinstaller les versions antérieures du .NET Framework, car une application que vous utilisez peut dépendre d’une version spécifique et risquer de dysfonctionner si cette version est supprimée.</span><span class="sxs-lookup"><span data-stu-id="52ee1-112">In general, you shouldn't uninstall previous versions of the .NET Framework, because an application you use may depend on a specific version and may break if that version is removed.</span></span>
>
> <span data-ttu-id="52ee1-113">Il existe une différence entre la version du .NET Framework et la version du CLR :</span><span class="sxs-lookup"><span data-stu-id="52ee1-113">There is a difference between the .NET Framework version and the CLR version:</span></span>
>
> - <span data-ttu-id="52ee1-114">La version du .NET Framework dépend du jeu d’assemblys qui constituent la bibliothèque de classes du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="52ee1-114">The .NET Framework version is based on the set of assemblies that form the .NET Framework class library.</span></span> <span data-ttu-id="52ee1-115">Par exemple, 4.5, 4.6.1 et 4.7.2 sont des versions de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="52ee1-115">For example, .NET Framework versions include 4.5, 4.6.1, and 4.7.2.</span></span>
> - <span data-ttu-id="52ee1-116">La version du CLR dépend du runtime sur lequel les applications .NET Framework s’exécutent.</span><span class="sxs-lookup"><span data-stu-id="52ee1-116">The CLR version is based on the runtime on which .NET Framework applications execute.</span></span> <span data-ttu-id="52ee1-117">En règle générale, une version particulière du CLR prend en charge plusieurs versions du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="52ee1-117">A single CLR version typically supports multiple .NET Framework versions.</span></span> <span data-ttu-id="52ee1-118">Par exemple, le CLR version 4.0.30319.*xxxxx* prend en charge les versions 4 à 4.5.2 du .NET Framework, où *xxxxx* est inférieur à 42000, tandis que le CLR version 4.0.30319.42000 prend en charge toutes les versions du .NET Framework à partir de .NET Framework 4.6.</span><span class="sxs-lookup"><span data-stu-id="52ee1-118">For example, CLR version 4.0.30319.*xxxxx* supports .NET Framework versions 4 through 4.5.2, where *xxxxx* is less than 42000, and CLR version 4.0.30319.42000 supports .NET Framework versions starting with .NET Framework 4.6.</span></span>
>
> <span data-ttu-id="52ee1-119">Pour plus d’informations sur les versions, consultez [Versions et dépendances du .NET Framework](versions-and-dependencies.md).</span><span class="sxs-lookup"><span data-stu-id="52ee1-119">For more information about versions, see [.NET Framework versions and dependencies](versions-and-dependencies.md).</span></span>

<span data-ttu-id="52ee1-120">Le registre contient une liste des versions de .NET Framework installées sur un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="52ee1-120">The registry contains a list of the .NET Framework versions installed on a computer.</span></span> <span data-ttu-id="52ee1-121">Vous pouvez utiliser l’éditeur du Registre pour consulter le registre ou l’interroger avec du code :</span><span class="sxs-lookup"><span data-stu-id="52ee1-121">You can either use the Registry Editor to view the registry or query it with code:</span></span>

- <span data-ttu-id="52ee1-122">Identifiez les versions les plus récentes du .NET Framework (4.5 et versions ultérieures) :</span><span class="sxs-lookup"><span data-stu-id="52ee1-122">Find newer .NET Framework versions (4.5 and later):</span></span>

  - [<span data-ttu-id="52ee1-123">Utiliser l’Éditeur du Registre pour déterminer les versions du .NET Framework</span><span class="sxs-lookup"><span data-stu-id="52ee1-123">Use the Registry Editor to find .NET Framework versions</span></span>](#net_b)
  - [<span data-ttu-id="52ee1-124">Utiliser du code pour interroger le Registre sur les versions du .NET Framework</span><span class="sxs-lookup"><span data-stu-id="52ee1-124">Use code to query the registry for .NET Framework versions</span></span>](#net_d)
  - [<span data-ttu-id="52ee1-125">Utiliser PowerShell pour interroger le Registre sur les versions du .NET Framework</span><span class="sxs-lookup"><span data-stu-id="52ee1-125">Use PowerShell to query the registry for .NET Framework versions</span></span>](#ps_a)

- <span data-ttu-id="52ee1-126">Rechercher les anciennes versions de .NET Framework (1 à 4) :</span><span class="sxs-lookup"><span data-stu-id="52ee1-126">Find older .NET Framework versions (1 through 4):</span></span>

  - [<span data-ttu-id="52ee1-127">Utiliser l’Éditeur du Registre pour déterminer les versions du .NET Framework</span><span class="sxs-lookup"><span data-stu-id="52ee1-127">Use the Registry Editor to find .NET Framework versions</span></span>](#net_a)
  - [<span data-ttu-id="52ee1-128">Utiliser du code pour interroger le Registre sur les versions du .NET Framework</span><span class="sxs-lookup"><span data-stu-id="52ee1-128">Use code to query the registry for .NET Framework versions</span></span>](#net_c)

<span data-ttu-id="52ee1-129">Pour obtenir la liste des versions du CLR installées sur un ordinateur, utilisez un outil ou du code :</span><span class="sxs-lookup"><span data-stu-id="52ee1-129">To get a list of the CLR versions installed on a computer, use a tool or code:</span></span>

- [<span data-ttu-id="52ee1-130">Utiliser l’outil Clrver</span><span class="sxs-lookup"><span data-stu-id="52ee1-130">Use the Clrver tool</span></span>](#clr_a)
- [<span data-ttu-id="52ee1-131">Utiliser du code pour interroger la classe Environment</span><span class="sxs-lookup"><span data-stu-id="52ee1-131">Use code to query the Environment class</span></span>](#clr_b)

<span data-ttu-id="52ee1-132">Pour plus d’informations sur la détection des mises à jour installées pour chaque version du .NET Framework, consultez [procédure : déterminer les mises à jour de .NET Framework installées](how-to-determine-which-net-framework-updates-are-installed.md).</span><span class="sxs-lookup"><span data-stu-id="52ee1-132">For information about detecting the installed updates for each version of the .NET Framework, see [How to: Determine which .NET Framework updates are installed](how-to-determine-which-net-framework-updates-are-installed.md).</span></span>

## <a name="find-newer-net-framework-versions-45-and-later"></a><span data-ttu-id="52ee1-133">Identifier les versions les plus récentes du .NET Framework (4.5 et versions ultérieures)</span><span class="sxs-lookup"><span data-stu-id="52ee1-133">Find newer .NET Framework versions (4.5 and later)</span></span>

<span data-ttu-id="52ee1-134">Vous pouvez utiliser l’éditeur du Registre pour rechercher des informations de version dans le registre, ou vous pouvez interroger le registre par programme.</span><span class="sxs-lookup"><span data-stu-id="52ee1-134">You can use Registry Editor to find version information in the registry, or you can query the registry programmatically.</span></span>

<a name="net_b"></a>

### <a name="use-registry-editor"></a><span data-ttu-id="52ee1-135">Utiliser l’éditeur du Registre</span><span class="sxs-lookup"><span data-stu-id="52ee1-135">Use Registry Editor</span></span>

1. <span data-ttu-id="52ee1-136">À partir du menu **Démarrer**, choisissez **Exécuter**, entrez *regedit*, puis sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="52ee1-136">From the **Start** menu, choose **Run**, enter *regedit*, and then select **OK**.</span></span>

     <span data-ttu-id="52ee1-137">Vous devez disposer d’informations d’identification d’administrateur pour exécuter regedit.</span><span class="sxs-lookup"><span data-stu-id="52ee1-137">You must have administrative credentials to run regedit.</span></span>

2. <span data-ttu-id="52ee1-138">Dans l’éditeur du Registre, ouvrez la sous-clé suivante : **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full**.</span><span class="sxs-lookup"><span data-stu-id="52ee1-138">In the Registry Editor, open the following subkey: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full**.</span></span> <span data-ttu-id="52ee1-139">Si la sous-clé **Full** est absente, alors .NET Framework 4.5 n’est pas installé ni une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="52ee1-139">If the **Full** subkey isn't present, then you don't have the .NET Framework 4.5 or later installed.</span></span>

    > [!NOTE]
    > <span data-ttu-id="52ee1-140">Le dossier **NET Framework Setup** du Registre ne commence *pas* par un point.</span><span class="sxs-lookup"><span data-stu-id="52ee1-140">The **NET Framework Setup** folder in the registry does *not* begin with a period.</span></span>

3. <span data-ttu-id="52ee1-141">Recherchez une entrée DWORD nommée **Release**.</span><span class="sxs-lookup"><span data-stu-id="52ee1-141">Check for a DWORD entry named **Release**.</span></span> <span data-ttu-id="52ee1-142">S’il existe, .NET Framework 4,5 ou version ultérieure est installé.</span><span class="sxs-lookup"><span data-stu-id="52ee1-142">If it exists, then you have .NET Framework 4.5 or later installed.</span></span> <span data-ttu-id="52ee1-143">Sa valeur est une clé de version correspondant à une version particulière du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="52ee1-143">Its value is a release key that corresponds to a particular version of the .NET Framework.</span></span> <span data-ttu-id="52ee1-144">Dans l’illustration suivante, par exemple, la valeur de l’entrée de **version** est 378389, qui est la clé de mise en version de .NET Framework 4,5.</span><span class="sxs-lookup"><span data-stu-id="52ee1-144">In the following figure, for example, the value of the **Release** entry is 378389, which is the release key for .NET Framework 4.5.</span></span>

   <span data-ttu-id="52ee1-145">![Entrée de Registre pour le .NET Framework 4,5](./media/clr-installdir.png "Entrée de Registre pour le .NET Framework 4,5")</span><span class="sxs-lookup"><span data-stu-id="52ee1-145">![Registry entry for the .NET Framework 4.5](./media/clr-installdir.png "Registry entry for the .NET Framework 4.5")</span></span>

<span data-ttu-id="52ee1-146">Le tableau suivant présente la valeur DWORD **Version** sur les différents systèmes d’exploitation pour .NET Framework 4.5 et les versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="52ee1-146">The following table lists the value of the **Release** DWORD on individual operating systems for .NET Framework 4.5 and later versions.</span></span>

[!INCLUDE[Release key values note](~/includes/version-keys-note.md)]

<a name="version_table"></a>

|<span data-ttu-id="52ee1-147">Version du .NET Framework</span><span class="sxs-lookup"><span data-stu-id="52ee1-147">.NET Framework version</span></span>|<span data-ttu-id="52ee1-148">Valeur du paramètre DWORD Release</span><span class="sxs-lookup"><span data-stu-id="52ee1-148">Value of the Release DWORD</span></span>|
|--------------------------------|-------------|
|<span data-ttu-id="52ee1-149">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="52ee1-149">.NET Framework 4.5</span></span>|<span data-ttu-id="52ee1-150">Tous les systèmes d’exploitation Windows : 378389</span><span class="sxs-lookup"><span data-stu-id="52ee1-150">All Windows operating systems: 378389</span></span>|
|<span data-ttu-id="52ee1-151">.NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="52ee1-151">.NET Framework 4.5.1</span></span>|<span data-ttu-id="52ee1-152">Sur Windows 8.1 et Windows Server 2012 R2:378675</span><span class="sxs-lookup"><span data-stu-id="52ee1-152">On Windows 8.1 and Windows Server 2012 R2: 378675</span></span><br /><span data-ttu-id="52ee1-153">Sur tous les autres systèmes d’exploitation Windows : 378758</span><span class="sxs-lookup"><span data-stu-id="52ee1-153">On all other Windows operating systems: 378758</span></span>|
|<span data-ttu-id="52ee1-154">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="52ee1-154">.NET Framework 4.5.2</span></span>|<span data-ttu-id="52ee1-155">Tous les systèmes d’exploitation Windows : 379893</span><span class="sxs-lookup"><span data-stu-id="52ee1-155">All Windows operating systems: 379893</span></span>|
|<span data-ttu-id="52ee1-156">.NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="52ee1-156">.NET Framework 4.6</span></span>|<span data-ttu-id="52ee1-157">Sur Windows 10:393295</span><span class="sxs-lookup"><span data-stu-id="52ee1-157">On Windows 10: 393295</span></span><br /><span data-ttu-id="52ee1-158">Sur tous les autres systèmes d’exploitation Windows : 393297</span><span class="sxs-lookup"><span data-stu-id="52ee1-158">On all other Windows operating systems: 393297</span></span>|
|<span data-ttu-id="52ee1-159">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="52ee1-159">.NET Framework 4.6.1</span></span>|<span data-ttu-id="52ee1-160">Sur les systèmes Windows intégrant la mise à jour du 10 novembre : 394254</span><span class="sxs-lookup"><span data-stu-id="52ee1-160">On Windows 10 November Update systems: 394254</span></span><br /><span data-ttu-id="52ee1-161">Sur tous les autres systèmes d’exploitation Windows (y compris Windows 10) : 394271</span><span class="sxs-lookup"><span data-stu-id="52ee1-161">On all other Windows operating systems (including Windows 10): 394271</span></span>|
|<span data-ttu-id="52ee1-162">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="52ee1-162">.NET Framework 4.6.2</span></span>|<span data-ttu-id="52ee1-163">Sur les systèmes Mise à jour anniversaire Windows 10 et Windows Server 2016 : 394802</span><span class="sxs-lookup"><span data-stu-id="52ee1-163">On Windows 10 Anniversary Update and Windows Server 2016: 394802</span></span><br /><span data-ttu-id="52ee1-164">Sur tous les autres systèmes d’exploitation Windows (y compris les autres systèmes d’exploitation Windows 10) : 394806</span><span class="sxs-lookup"><span data-stu-id="52ee1-164">On all other Windows operating systems (including other Windows 10 operating systems): 394806</span></span>|
|<span data-ttu-id="52ee1-165">.NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="52ee1-165">.NET Framework 4.7</span></span>|<span data-ttu-id="52ee1-166">Sur Windows 10 Creators Update : 460798</span><span class="sxs-lookup"><span data-stu-id="52ee1-166">On Windows 10 Creators Update: 460798</span></span><br /><span data-ttu-id="52ee1-167">Sur tous les autres systèmes d’exploitation Windows (y compris les autres systèmes d’exploitation Windows 10) : 460805</span><span class="sxs-lookup"><span data-stu-id="52ee1-167">On all other Windows operating systems (including other Windows 10 operating systems): 460805</span></span>|
|<span data-ttu-id="52ee1-168">.NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="52ee1-168">.NET Framework 4.7.1</span></span>|<span data-ttu-id="52ee1-169">Sur Windows 10 automne Creators Update et Windows Server, version 1709:461308</span><span class="sxs-lookup"><span data-stu-id="52ee1-169">On Windows 10 Fall Creators Update and Windows Server, version 1709: 461308</span></span><br/><span data-ttu-id="52ee1-170">Sur tous les autres systèmes d’exploitation Windows (y compris les autres systèmes d’exploitation Windows 10) : 461310</span><span class="sxs-lookup"><span data-stu-id="52ee1-170">On all other Windows operating systems (including other Windows 10 operating systems): 461310</span></span>|
|<span data-ttu-id="52ee1-171">.NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="52ee1-171">.NET Framework 4.7.2</span></span>|<span data-ttu-id="52ee1-172">Sur Windows 10 avril 2018 mise à jour et Windows Server, version 1803:461808</span><span class="sxs-lookup"><span data-stu-id="52ee1-172">On Windows 10 April 2018 Update and Windows Server, version 1803: 461808</span></span><br/><span data-ttu-id="52ee1-173">Sur tous les systèmes d’exploitation Windows autres que Windows 10 avril 2018 Update et Windows Server, version 1803:461814</span><span class="sxs-lookup"><span data-stu-id="52ee1-173">On all Windows operating systems other than Windows 10 April 2018 Update and Windows Server, version 1803: 461814</span></span>|
|<span data-ttu-id="52ee1-174">.NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="52ee1-174">.NET Framework 4.8</span></span>|<span data-ttu-id="52ee1-175">Sur Windows 10 mai 2019 mise à jour et Windows 10 novembre 2019 mise à jour : 528040</span><span class="sxs-lookup"><span data-stu-id="52ee1-175">On Windows 10 May 2019 Update and Windows 10 November 2019 Update: 528040</span></span><br/><span data-ttu-id="52ee1-176">Sur tous les autres systèmes d’exploitation Windows (y compris les autres systèmes d’exploitation Windows 10) : 528049</span><span class="sxs-lookup"><span data-stu-id="52ee1-176">On all other Windows operating systems (including other Windows 10 operating systems): 528049</span></span>|

#### <a name="specific-version"></a><span data-ttu-id="52ee1-177">Version spécifique</span><span class="sxs-lookup"><span data-stu-id="52ee1-177">Specific version</span></span>

<span data-ttu-id="52ee1-178">Pour déterminer si une version *spécifique* du .NET Framework est installée sur une version particulière du système d’exploitation Windows, testez si la valeur DWORD de la **version** est *égale à* la valeur indiquée dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="52ee1-178">To determine whether a *specific* version of the .NET Framework is installed on a particular version of the Windows operating system, test whether the **Release** DWORD value is *equal to* the value listed in the table.</span></span> <span data-ttu-id="52ee1-179">Par exemple, pour déterminer si .NET Framework 4.6 est présent sur un système Windows 10, regardez si la valeur **Version** est *égale à* 393295.</span><span class="sxs-lookup"><span data-stu-id="52ee1-179">For example, to determine whether .NET Framework 4.6 is present on a Windows 10 system, test for the a **Release** value that is *equal to* 393295.</span></span>

#### <a name="minimum-version"></a><span data-ttu-id="52ee1-180">Version minimale</span><span class="sxs-lookup"><span data-stu-id="52ee1-180">Minimum version</span></span>

<span data-ttu-id="52ee1-181">Pour déterminer si une version *minimale* du .NET Framework est présente, utilisez la valeur DWORD de la plus **petite version de** cette version du tableau précédent.</span><span class="sxs-lookup"><span data-stu-id="52ee1-181">To determine whether a *minimum* version of the .NET Framework is present, use the smallest **RELEASE** DWORD value for that version from the previous table.</span></span> <span data-ttu-id="52ee1-182">(Pour des raisons pratiques, les valeurs minimales sont également répertoriées dans le tableau qui suit.)</span><span class="sxs-lookup"><span data-stu-id="52ee1-182">(For convenience, the minimum values are also listed in the table that follows.)</span></span>

<span data-ttu-id="52ee1-183">Par exemple, si votre application s’exécute sous .NET Framework 4,8 ou une version ultérieure, testez une valeur DWORD **Release** *supérieure ou égale à* 528040.</span><span class="sxs-lookup"><span data-stu-id="52ee1-183">For example, if your application runs under .NET Framework 4.8 or a later version, test for a **RELEASE** DWORD value that is *greater than or equal to* 528040.</span></span>

|<span data-ttu-id="52ee1-184">Version du .NET Framework</span><span class="sxs-lookup"><span data-stu-id="52ee1-184">.NET Framework version</span></span>|<span data-ttu-id="52ee1-185">Valeur minimale du paramètre DWORD Release</span><span class="sxs-lookup"><span data-stu-id="52ee1-185">Minimum value of the Release DWORD</span></span>|
|--------------------------------|-------------|
|<span data-ttu-id="52ee1-186">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="52ee1-186">.NET Framework 4.5</span></span>|<span data-ttu-id="52ee1-187">378389</span><span class="sxs-lookup"><span data-stu-id="52ee1-187">378389</span></span>|
|<span data-ttu-id="52ee1-188">.NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="52ee1-188">.NET Framework 4.5.1</span></span>|<span data-ttu-id="52ee1-189">378675</span><span class="sxs-lookup"><span data-stu-id="52ee1-189">378675</span></span>|
|<span data-ttu-id="52ee1-190">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="52ee1-190">.NET Framework 4.5.2</span></span>|<span data-ttu-id="52ee1-191">379893</span><span class="sxs-lookup"><span data-stu-id="52ee1-191">379893</span></span>|
|<span data-ttu-id="52ee1-192">.NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="52ee1-192">.NET Framework 4.6</span></span>|<span data-ttu-id="52ee1-193">393295</span><span class="sxs-lookup"><span data-stu-id="52ee1-193">393295</span></span>|
|<span data-ttu-id="52ee1-194">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="52ee1-194">.NET Framework 4.6.1</span></span>|<span data-ttu-id="52ee1-195">394254</span><span class="sxs-lookup"><span data-stu-id="52ee1-195">394254</span></span>|
|<span data-ttu-id="52ee1-196">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="52ee1-196">.NET Framework 4.6.2</span></span>|<span data-ttu-id="52ee1-197">394802</span><span class="sxs-lookup"><span data-stu-id="52ee1-197">394802</span></span>|
|<span data-ttu-id="52ee1-198">.NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="52ee1-198">.NET Framework 4.7</span></span>|<span data-ttu-id="52ee1-199">460798</span><span class="sxs-lookup"><span data-stu-id="52ee1-199">460798</span></span>|
|<span data-ttu-id="52ee1-200">.NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="52ee1-200">.NET Framework 4.7.1</span></span>|<span data-ttu-id="52ee1-201">461308</span><span class="sxs-lookup"><span data-stu-id="52ee1-201">461308</span></span>|
|<span data-ttu-id="52ee1-202">.NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="52ee1-202">.NET Framework 4.7.2</span></span>|<span data-ttu-id="52ee1-203">461808</span><span class="sxs-lookup"><span data-stu-id="52ee1-203">461808</span></span>|
|<span data-ttu-id="52ee1-204">.NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="52ee1-204">.NET Framework 4.8</span></span>|<span data-ttu-id="52ee1-205">528040</span><span class="sxs-lookup"><span data-stu-id="52ee1-205">528040</span></span>|

#### <a name="multiple-versions"></a><span data-ttu-id="52ee1-206">Plusieurs versions</span><span class="sxs-lookup"><span data-stu-id="52ee1-206">Multiple versions</span></span>

<span data-ttu-id="52ee1-207">Pour tester plusieurs versions, commencez par rechercher une valeur *supérieure ou égale à* la plus petite valeur DWORD de la dernière version de .NET Framework, puis comparez-la avec la plus petite valeur DWORD de chacune des versions antérieures, en allant de la plus récente à la plus ancienne.</span><span class="sxs-lookup"><span data-stu-id="52ee1-207">To test for multiple versions, begin by testing for a value that is *greater than or equal to* the smaller DWORD value for the latest .NET Framework version, and then compare the value with the smaller DWORD value for each successive earlier version.</span></span> <span data-ttu-id="52ee1-208">Par exemple, si votre application exige .NET Framework 4.7 ou une version ultérieure et que vous souhaitez identifier la version installée de .NET Framework, commencez par rechercher une valeur DWORD **Version** *supérieure ou égale à* 461808 (la plus petite valeur DWORD pour .NET Framework 4.7.2).</span><span class="sxs-lookup"><span data-stu-id="52ee1-208">For example, if your application requires .NET Framework 4.7 or later and you want to determine the specific version of .NET Framework present, start by testing for a **RELEASE** DWORD value that is *great than or equal to* to 461808 (the smaller DWORD value for .NET Framework 4.7.2).</span></span> <span data-ttu-id="52ee1-209">Ensuite, comparez la valeur DWORD **Version** avec la plus petite valeur de chaque version ultérieure de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="52ee1-209">Then compare the **RELEASE** DWORD value with the smaller value for each later .NET Framework version.</span></span>

<a name="net_d"></a>

### <a name="query-the-registry-using-code"></a><span data-ttu-id="52ee1-210">Interroger le registre à l’aide de code</span><span class="sxs-lookup"><span data-stu-id="52ee1-210">Query the registry using code</span></span>

1. <span data-ttu-id="52ee1-211">Utilisez les méthodes <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> et <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType> pour accéder à la sous-clé **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** dans le Registre Windows.</span><span class="sxs-lookup"><span data-stu-id="52ee1-211">Use the <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> and <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType> methods to access the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** subkey in the Windows registry.</span></span>

   <span data-ttu-id="52ee1-212">L’existence de l’entrée DWORD **Release** dans la sous-clé **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** indique que .NET Framework 4.5 ou une version ultérieure sont installés sur un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="52ee1-212">The existence of the **Release** DWORD entry in the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** subkey indicates that the .NET Framework 4.5 or a later version is installed on a computer.</span></span>

2. <span data-ttu-id="52ee1-213">Vérifiez la valeur de l’entrée **Release** pour déterminer la version installée.</span><span class="sxs-lookup"><span data-stu-id="52ee1-213">Check the value of the **Release** entry to determine the installed version.</span></span> <span data-ttu-id="52ee1-214">Pour être compatible, recherchez une valeur supérieure ou égale à la valeur listée dans le [tableau des versions du .NET Framework](#version_table).</span><span class="sxs-lookup"><span data-stu-id="52ee1-214">To be forward-compatible, check for a value greater than or equal to the value listed in the [.NET Framework version table](#version_table).</span></span>

<span data-ttu-id="52ee1-215">L’exemple suivant vérifie la valeur de l’entrée **Release** dans le Registre pour identifier les versions 4.5 et ultérieures du .NET Framework installées :</span><span class="sxs-lookup"><span data-stu-id="52ee1-215">The following example checks the value of the **Release** entry in the registry to find the .NET Framework 4.5 and later versions that are installed:</span></span>

[!code-csharp[ListVersions#5](../../../samples/snippets/csharp/framework/migration-guide/versions-installed3.cs)]
[!code-vb[ListVersions#5](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed3.vb)]

<span data-ttu-id="52ee1-216">Cet exemple suit la pratique recommandée concernant la vérification de version :</span><span class="sxs-lookup"><span data-stu-id="52ee1-216">This example follows the recommended practice for version checking:</span></span>

- <span data-ttu-id="52ee1-217">Il vérifie si la valeur de l’entrée **Release** est *supérieure ou égale à* la valeur des clés de version connues.</span><span class="sxs-lookup"><span data-stu-id="52ee1-217">It checks whether the value of the **Release** entry is *greater than or equal to* the value of the known release keys.</span></span>

- <span data-ttu-id="52ee1-218">Il effectue sa vérification en partant de la version la plus récente vers la version la plus ancienne.</span><span class="sxs-lookup"><span data-stu-id="52ee1-218">It checks in order from most recent version to earliest version.</span></span>

<a name="ps_a"></a>

### <a name="use-powershell-to-check-for-a-minimum-required-version"></a><span data-ttu-id="52ee1-219">Utiliser PowerShell pour vérifier la version minimale requise</span><span class="sxs-lookup"><span data-stu-id="52ee1-219">Use PowerShell to check for a minimum-required version</span></span>

<span data-ttu-id="52ee1-220">Utilisez des commandes PowerShell pour vérifier la valeur de l’entrée **Release** de la sous-clé **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full**.</span><span class="sxs-lookup"><span data-stu-id="52ee1-220">Use PowerShell commands to check the value of the **Release** entry of the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** subkey.</span></span>

<span data-ttu-id="52ee1-221">Les exemples suivants vérifient la valeur de l’entrée **Release** pour déterminer si .NET Framework 4.6.2 ou une version ultérieure sont installés.</span><span class="sxs-lookup"><span data-stu-id="52ee1-221">The following examples check the value of the **Release** entry to determine whether the .NET Framework 4.6.2 or later is installed.</span></span> <span data-ttu-id="52ee1-222">Ce code retourne `True` s’il est installé et `False` dans le cas contraire.</span><span class="sxs-lookup"><span data-stu-id="52ee1-222">This code returns `True` if it's installed and `False` otherwise.</span></span>

```PowerShell
(Get-ItemProperty "HKLM:SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full").Release -ge 394802
```

<span data-ttu-id="52ee1-223">Pour rechercher une version de .NET Framework minimale requise, remplacez `394802` dans l’exemple par une valeur de la [table .NET Framework version](#version_table).</span><span class="sxs-lookup"><span data-stu-id="52ee1-223">To check for a different minimum-required .NET Framework version, replace `394802` in the example with a value from the [.NET Framework version table](#version_table).</span></span> <span data-ttu-id="52ee1-224">Utilisez la valeur la plus petite indiquée pour cette version.</span><span class="sxs-lookup"><span data-stu-id="52ee1-224">Use the smallest value shown for that version.</span></span>

## <a name="find-older-net-framework-versions-1-through-4"></a><span data-ttu-id="52ee1-225">Rechercher les anciennes versions de .NET Framework (1 à 4)</span><span class="sxs-lookup"><span data-stu-id="52ee1-225">Find older .NET Framework versions (1 through 4)</span></span>

<a name="net_a"></a>

### <a name="use-registry-editor-older-framework-versions"></a><span data-ttu-id="52ee1-226">Utiliser l’éditeur du Registre (versions antérieures de l’infrastructure)</span><span class="sxs-lookup"><span data-stu-id="52ee1-226">Use Registry Editor (older framework versions)</span></span>

1. <span data-ttu-id="52ee1-227">À partir du menu **Démarrer**, choisissez **Exécuter**, entrez *regedit*, puis sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="52ee1-227">From the **Start** menu, choose **Run**, enter *regedit*, and then select **OK**.</span></span>

    <span data-ttu-id="52ee1-228">Vous devez disposer d’informations d’identification d’administrateur pour exécuter regedit.</span><span class="sxs-lookup"><span data-stu-id="52ee1-228">You must have administrative credentials to run regedit.</span></span>

2. <span data-ttu-id="52ee1-229">Dans l’éditeur du Registre, ouvrez la sous-clé suivante : **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP**:</span><span class="sxs-lookup"><span data-stu-id="52ee1-229">In the Registry Editor, open the following subkey: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP**:</span></span>

    - <span data-ttu-id="52ee1-230">Pour les versions 1.1 à 3.5 du .NET Framework, chaque version installée est listée en tant que sous-clé sous la sous-clé **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP**.</span><span class="sxs-lookup"><span data-stu-id="52ee1-230">For .NET Framework versions 1.1 through 3.5, each installed version is listed as a subkey under the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP** subkey.</span></span> <span data-ttu-id="52ee1-231">Par exemple, **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v3.5**.</span><span class="sxs-lookup"><span data-stu-id="52ee1-231">For example, **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v3.5**.</span></span> <span data-ttu-id="52ee1-232">Le numéro de version est stocké sous forme de valeur dans l’entrée **Version** de la sous-clé de version.</span><span class="sxs-lookup"><span data-stu-id="52ee1-232">The version number is stored as a value in the version subkey's **Version** entry.</span></span>

    - <span data-ttu-id="52ee1-233">Pour .NET Framework 4, l’entrée **Version** se trouve sous la sous-clé **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Client**, sous la sous-clé **HKEY_LOCAL_MACHINE\SOFTWARE\ Microsoft\NET Framework Setup\NDP\v4.0\Full** ou sous les deux sous-clés.</span><span class="sxs-lookup"><span data-stu-id="52ee1-233">For .NET Framework 4, the **Version** entry is under the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Client** subkey, the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Full** subkey, or under both subkeys.</span></span>

    > [!NOTE]
    > <span data-ttu-id="52ee1-234">Le dossier d’installation **NET Framework Setup** dans le Registre ne commence pas par un point.</span><span class="sxs-lookup"><span data-stu-id="52ee1-234">The **NET Framework Setup** folder in the registry does not begin with a period.</span></span>

    <span data-ttu-id="52ee1-235">La figure suivante illustre la sous-clé et son entrée **Version** pour .NET Framework 3.5.</span><span class="sxs-lookup"><span data-stu-id="52ee1-235">The following figure shows the subkey and its **Version** entry for the .NET Framework 3.5.</span></span>

    <span data-ttu-id="52ee1-236">![Entrée de Registre pour le .NET Framework 3,5.](./media/net-4-and-earlier.png ".NET Framework 3,5 et versions antérieures")</span><span class="sxs-lookup"><span data-stu-id="52ee1-236">![The registry entry for the .NET Framework 3.5.](./media/net-4-and-earlier.png ".NET Framework 3.5 and earlier versions")</span></span>

<a name="net_c"></a>

### <a name="query-the-registry-using-code-older-framework-versions"></a><span data-ttu-id="52ee1-237">Interroger le registre à l’aide de code (versions antérieures du Framework)</span><span class="sxs-lookup"><span data-stu-id="52ee1-237">Query the registry using code (older framework versions)</span></span>

<span data-ttu-id="52ee1-238">Utilisez la classe <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> pour accéder à la sous-clé **HKEY_LOCAL_MACHINE\Software\Microsoft\NET Framework Setup\NDP** dans le Registre Windows.</span><span class="sxs-lookup"><span data-stu-id="52ee1-238">Use the <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> class to access the **HKEY_LOCAL_MACHINE\Software\Microsoft\NET Framework Setup\NDP** subkey in the Windows registry.</span></span>

<span data-ttu-id="52ee1-239">L’exemple suivant recherche les versions .NET Framework 1 à 4 qui sont installées :</span><span class="sxs-lookup"><span data-stu-id="52ee1-239">The following example finds the .NET Framework 1 through 4 versions that are installed:</span></span>

[!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed1.cs)]
[!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed1.vb)]

## <a name="find-clr-versions"></a><span data-ttu-id="52ee1-240">Identifier les versions du CLR</span><span class="sxs-lookup"><span data-stu-id="52ee1-240">Find CLR versions</span></span>

<a name="clr_a"></a>

### <a name="use-clrverexe"></a><span data-ttu-id="52ee1-241">Utiliser CLRVer. exe</span><span class="sxs-lookup"><span data-stu-id="52ee1-241">Use Clrver.exe</span></span>

<span data-ttu-id="52ee1-242">Utilisez l’[outil de version CLR (Clrver.exe)](../tools/clrver-exe-clr-version-tool.md) pour déterminer quelles versions du CLR sont installées sur un ordinateur :</span><span class="sxs-lookup"><span data-stu-id="52ee1-242">Use the [CLR Version tool (Clrver.exe)](../tools/clrver-exe-clr-version-tool.md) to determine which versions of the CLR are installed on a computer:</span></span>

- <span data-ttu-id="52ee1-243">À partir d’une [invite de commandes développeur pour Visual Studio](../tools/developer-command-prompt-for-vs.md), entrez `clrver`.</span><span class="sxs-lookup"><span data-stu-id="52ee1-243">From a [Developer Command Prompt for Visual Studio](../tools/developer-command-prompt-for-vs.md), enter `clrver`.</span></span>

    <span data-ttu-id="52ee1-244">Résultat de l'exemple :</span><span class="sxs-lookup"><span data-stu-id="52ee1-244">Sample output:</span></span>

    ```console
    Versions installed on the machine:
    v2.0.50727
    v4.0.30319
    ```

<a name="clr_b"></a>

### <a name="use-the-environment-class"></a><span data-ttu-id="52ee1-245">Utiliser la classe Environment</span><span class="sxs-lookup"><span data-stu-id="52ee1-245">Use the Environment class</span></span>

> [!IMPORTANT]
> <span data-ttu-id="52ee1-246">Pour .NET Framework 4.5 et ultérieur, n’utilisez pas la propriété <xref:System.Environment.Version%2A?displayProperty=nameWithType> pour détecter la version du CLR.</span><span class="sxs-lookup"><span data-stu-id="52ee1-246">For the .NET Framework 4.5 and later versions, don't use the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property to detect the version of the CLR.</span></span> <span data-ttu-id="52ee1-247">Interrogez plutôt le Registre comme décrit dans [Identifier les versions 4.5 et ultérieures du .NET Framework avec du code](#net_d).</span><span class="sxs-lookup"><span data-stu-id="52ee1-247">Instead, query the registry as described in [Find .NET Framework versions 4.5 and later with code](#net_d).</span></span>

1. <span data-ttu-id="52ee1-248">Interrogez la propriété <xref:System.Environment.Version?displayProperty=nameWithType> pour récupérer un objet <xref:System.Version>.</span><span class="sxs-lookup"><span data-stu-id="52ee1-248">Query the <xref:System.Environment.Version?displayProperty=nameWithType> property to retrieve a <xref:System.Version> object.</span></span>

    <span data-ttu-id="52ee1-249">L’objet `System.Version` retourné identifie la version du runtime qui est en train d’exécuter le code.</span><span class="sxs-lookup"><span data-stu-id="52ee1-249">The returned `System.Version` object identifies the version of the runtime that's currently executing the code.</span></span> <span data-ttu-id="52ee1-250">Il ne retourne pas les versions d’assembly ni d’autres versions du runtime susceptibles d’avoir été installées sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="52ee1-250">It doesn't return assembly versions or other versions of the runtime that may have been installed on the computer.</span></span>

    <span data-ttu-id="52ee1-251">Pour les versions 4, 4.5, 4.5.1 et 4.5.2 du .NET Framework, la représentation sous forme de chaîne de l’objet <xref:System.Version> retourné a la forme 4.0.30319.*xxxxx*, où *xxxxx* est inférieur à 42000.</span><span class="sxs-lookup"><span data-stu-id="52ee1-251">For the .NET Framework versions 4, 4.5, 4.5.1, and 4.5.2, the string representation of the returned <xref:System.Version> object has the form 4.0.30319.*xxxxx*, where *xxxxx* is less than 42000.</span></span> <span data-ttu-id="52ee1-252">Pour les versions 4.6 et ultérieures du .NET Framework, la forme est 4.0.30319.42000.</span><span class="sxs-lookup"><span data-stu-id="52ee1-252">For the .NET Framework 4.6 and later versions, it has the form 4.0.30319.42000.</span></span>

2. <span data-ttu-id="52ee1-253">Une fois que vous avez l’objet `Version`, interrogez-le comme suit :</span><span class="sxs-lookup"><span data-stu-id="52ee1-253">After you have the `Version` object, query it as follows:</span></span>

   - <span data-ttu-id="52ee1-254">Pour l’identificateur de la version majeure (par exemple, *4* pour la version 4.0), utilisez la propriété <xref:System.Version.Major%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="52ee1-254">For the major release identifier (for example, *4* for version 4.0), use the <xref:System.Version.Major%2A?displayProperty=nameWithType> property.</span></span>

   - <span data-ttu-id="52ee1-255">Pour l’identificateur de la version mineure (par exemple, *0* pour la version 4.0), utilisez la propriété <xref:System.Version.Minor%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="52ee1-255">For the minor release identifier (for example, *0* for version 4.0), use the <xref:System.Version.Minor%2A?displayProperty=nameWithType> property.</span></span>

   - <span data-ttu-id="52ee1-256">Pour la chaîne de la version entière (par exemple, *4.0.30319.18010*), utilisez la méthode <xref:System.Version.ToString%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="52ee1-256">For the entire version string (for example, *4.0.30319.18010*), use the <xref:System.Version.ToString%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="52ee1-257">Cette méthode retourne une valeur unique qui reflète la version du runtime qui est en train d’exécuter le code.</span><span class="sxs-lookup"><span data-stu-id="52ee1-257">This method returns a single value that reflects the version of the runtime that's executing the code.</span></span> <span data-ttu-id="52ee1-258">Elle ne retourne pas les versions d’assembly ni d’autres versions du runtime susceptibles d’être installées sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="52ee1-258">It doesn't return assembly versions or other runtime versions that may be installed on the computer.</span></span>

<span data-ttu-id="52ee1-259">L’exemple suivant utilise la propriété <xref:System.Environment.Version%2A?displayProperty=nameWithType> pour récupérer les informations de version du CLR :</span><span class="sxs-lookup"><span data-stu-id="52ee1-259">The following example uses the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property to retrieve CLR version information:</span></span>

[!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed2.cs)]
[!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed2.vb)]

## <a name="see-also"></a><span data-ttu-id="52ee1-260">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="52ee1-260">See also</span></span>

- [<span data-ttu-id="52ee1-261">Comment : déterminer les mises à jour de .NET Framework installées</span><span class="sxs-lookup"><span data-stu-id="52ee1-261">How to: Determine which .NET Framework updates are installed</span></span>](how-to-determine-which-net-framework-updates-are-installed.md)
- [<span data-ttu-id="52ee1-262">Installer le .NET Framework pour les développeurs</span><span class="sxs-lookup"><span data-stu-id="52ee1-262">Install the .NET Framework for developers</span></span>](../install/guide-for-developers.md)
- [<span data-ttu-id="52ee1-263">Versions et dépendances du .NET Framework</span><span class="sxs-lookup"><span data-stu-id="52ee1-263">.NET Framework versions and dependencies</span></span>](versions-and-dependencies.md)
