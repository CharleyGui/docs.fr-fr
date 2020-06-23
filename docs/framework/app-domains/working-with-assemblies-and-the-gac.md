---
title: Utilisation d'assemblys et du Global Assembly Cache
description: Travaillez avec les assemblys et le Global Assembly Cache (GAC) dans .NET. Examinez les raisons pour lesquelles vous pouvez souhaiter installer un assembly dans le GAC.
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- global assembly cache, benefits
- ACLs [.NET Framework]
- GAC (global assembly cache), benefits
- access control lists [.NET Framework]
ms.assetid: 8a18e5c2-d41d-49ef-abcb-7c27e2469433
ms.openlocfilehash: 16cfd9faf02d5b58acad1cc0cf19be61c9814d35
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2020
ms.locfileid: "85105160"
---
# <a name="working-with-assemblies-and-the-global-assembly-cache"></a><span data-ttu-id="64cd0-104">Utilisation d'assemblys et du Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="64cd0-104">Working with Assemblies and the Global Assembly Cache</span></span>

<span data-ttu-id="64cd0-105">Si vous prévoyez de partager un assembly entre plusieurs applications, vous pouvez l’installer dans le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="64cd0-105">If you intend to share an assembly among several applications, you can install it into the global assembly cache.</span></span> <span data-ttu-id="64cd0-106">Chaque ordinateur où le common language runtime est installé a ce cache de code à l’échelle de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="64cd0-106">Each computer where the common language runtime is installed has this machine-wide code cache.</span></span> <span data-ttu-id="64cd0-107">Le Global Assembly Cache stocke des assemblys spécialement destinés à être partagés entre plusieurs applications sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="64cd0-107">The global assembly cache stores assemblies specifically designated to be shared by several applications on the computer.</span></span> <span data-ttu-id="64cd0-108">Un assembly doit avoir un nom fort pour être installé dans le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="64cd0-108">An assembly must have a strong name to be installed in the global assembly cache.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="64cd0-109">Les assemblys placés dans le Global Assembly Cache doivent avoir le même nom d’assembly et le même nom de fichier (sans l’extension du nom de fichier).</span><span class="sxs-lookup"><span data-stu-id="64cd0-109">Assemblies placed in the global assembly cache must have the same assembly name and file name (not including the file name extension).</span></span> <span data-ttu-id="64cd0-110">Par exemple, un assembly avec le nom d’assembly monAssembly doit avoir le nom de fichier monAssembly.exe ou monAssembly.dll.</span><span class="sxs-lookup"><span data-stu-id="64cd0-110">For example, an assembly with the assembly name of myAssembly must have a file name of either myAssembly.exe or myAssembly.dll.</span></span>  
  
<span data-ttu-id="64cd0-111">Il est recommandé de partager des assemblys en les installant dans le Global Assembly Cache seulement quand c’est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="64cd0-111">You should share assemblies by installing them into the global assembly cache only when necessary.</span></span> <span data-ttu-id="64cd0-112">Une règle générale est de conserver les dépendances d’assembly privées et de placer les assemblys dans le répertoire de l’application, sauf si le partage d’un assembly est explicitement nécessaire.</span><span class="sxs-lookup"><span data-stu-id="64cd0-112">As a general guideline, keep assembly dependencies private and locate assemblies in the application directory unless sharing an assembly is explicitly required.</span></span> <span data-ttu-id="64cd0-113">En outre, il n’est pas nécessaire d’installer des assemblys dans le Global Assembly Cache pour les rendre accessibles à COM Interop ou à du code non managé.</span><span class="sxs-lookup"><span data-stu-id="64cd0-113">In addition, you do not have to install assemblies into the global assembly cache to make them accessible to COM interop or unmanaged code.</span></span>  
  
<span data-ttu-id="64cd0-114">Vous pouvez souhaiter installer un assembly dans le Global Assembly Cache pour plusieurs raisons :</span><span class="sxs-lookup"><span data-stu-id="64cd0-114">There are several reasons why you might want to install an assembly into the global assembly cache:</span></span>  
  
- <span data-ttu-id="64cd0-115">Emplacement partagé.</span><span class="sxs-lookup"><span data-stu-id="64cd0-115">Shared location.</span></span>  
  
     <span data-ttu-id="64cd0-116">Les assemblys qui doivent être utilisés par des applications peuvent être placés dans le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="64cd0-116">Assemblies that should be used by applications can be put in the global assembly cache.</span></span> <span data-ttu-id="64cd0-117">Par exemple, si toutes les applications doivent utiliser un assembly qui se trouve dans le Global Assembly Cache, vous pouvez ajouter une instruction de stratégie de version au fichier Machine.config pour rediriger les références à l’assembly.</span><span class="sxs-lookup"><span data-stu-id="64cd0-117">For example, if all applications should use an assembly located in the global assembly cache, a version policy statement can be added to the Machine.config file that redirects references to the assembly.</span></span>  
  
- <span data-ttu-id="64cd0-118">Sécurité des fichiers.</span><span class="sxs-lookup"><span data-stu-id="64cd0-118">File security.</span></span>  
  
     <span data-ttu-id="64cd0-119">Les administrateurs protègent souvent le répertoire systemroot en utilisant une liste de contrôle d’accès pour contrôler l’accès en écriture et en exécution.</span><span class="sxs-lookup"><span data-stu-id="64cd0-119">Administrators often protect the systemroot directory using an Access Control List (ACL) to control write and execute access.</span></span> <span data-ttu-id="64cd0-120">Le Global Assembly Cache étant installé dans le répertoire systemroot, il hérite de la liste de contrôle d’accès de ce répertoire.</span><span class="sxs-lookup"><span data-stu-id="64cd0-120">Because the global assembly cache is installed in the systemroot directory, it inherits that directory's ACL.</span></span> <span data-ttu-id="64cd0-121">Il est recommandé que seuls les utilisateurs disposant de privilèges d’administrateur soient autorisés à supprimer des fichiers du Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="64cd0-121">It is recommended that only users with Administrator privileges be allowed to delete files from the global assembly cache.</span></span>  
  
- <span data-ttu-id="64cd0-122">Contrôle de version côte à côte.</span><span class="sxs-lookup"><span data-stu-id="64cd0-122">Side-by-side versioning.</span></span>  
  
     <span data-ttu-id="64cd0-123">Plusieurs copies des assemblys avec le même nom mais avec des informations de version différentes peuvent être conservées dans le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="64cd0-123">Multiple copies of assemblies with the same name but different version information can be maintained in the global assembly cache.</span></span>  
  
- <span data-ttu-id="64cd0-124">Emplacements de recherche supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="64cd0-124">Additional search location.</span></span>  
  
     <span data-ttu-id="64cd0-125">Le common language runtime recherche dans le Global Assembly Cache un assembly qui correspond à l’assembly demandé avant de chercher ailleurs ou d’utiliser les informations du code base dans un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="64cd0-125">The common language runtime checks the global assembly cache for an assembly that matches the assembly request before probing or using the codebase information in a configuration file.</span></span>  
  
 <span data-ttu-id="64cd0-126">Notez que dans certains scénarios, vous ne voulez explicitement pas installer un assembly dans le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="64cd0-126">Note that there are scenarios where you explicitly do not want to install an assembly into the global assembly cache.</span></span> <span data-ttu-id="64cd0-127">Si vous placez un des assemblys composant une application dans le Global Assembly Cache, vous ne pouvez plus répliquer ni installer l’application en utilisant XCOPY pour copier le répertoire de l’application.</span><span class="sxs-lookup"><span data-stu-id="64cd0-127">If you place one of the assemblies that make up an application into the global assembly cache, you can no longer replicate or install the application by using XCOPY to copy the application directory.</span></span> <span data-ttu-id="64cd0-128">Dans ce cas, vous devez également déplacer l’assembly dans le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="64cd0-128">In this case, you must also move the assembly into the global assembly cache.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="64cd0-129">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="64cd0-129">In This Section</span></span>  
[<span data-ttu-id="64cd0-130">Comment : installer un assembly dans le global assembly cache</span><span class="sxs-lookup"><span data-stu-id="64cd0-130">How to: Install an Assembly into the Global Assembly Cache</span></span>](install-assembly-into-gac.md)  
<span data-ttu-id="64cd0-131">Décrit les façons d’installer un assembly dans le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="64cd0-131">Describes the ways to install an assembly into the global assembly cache.</span></span>  
  
[<span data-ttu-id="64cd0-132">Procédure : Visualiser le contenu du Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="64cd0-132">How to: View the Contents of the Global Assembly Cache</span></span>](how-to-view-the-contents-of-the-gac.md)  
<span data-ttu-id="64cd0-133">Explique comment utiliser [Gacutil.exe (outil Global Assembly Cache](../tools/gacutil-exe-gac-tool.md) pour visualiser le contenu du Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="64cd0-133">Explains how to use the [Gacutil.exe (Global Assembly Cache Tool)](../tools/gacutil-exe-gac-tool.md) to view the contents of the global assembly cache.</span></span>  
  
[<span data-ttu-id="64cd0-134">Procédure : supprimer un assembly du Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="64cd0-134">How to: Remove an Assembly from the Global Assembly Cache</span></span>](how-to-remove-an-assembly-from-the-gac.md)  
<span data-ttu-id="64cd0-135">Explique comment utiliser [Gacutil.exe (outil Global Assembly Cache](../tools/gacutil-exe-gac-tool.md) pour supprimer un assembly du Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="64cd0-135">Explains how to use the [Gacutil.exe (Global Assembly Cache Tool)](../tools/gacutil-exe-gac-tool.md) to remove an assembly from the global assembly cache.</span></span>  
  
[<span data-ttu-id="64cd0-136">Utilisation de composants de service avec le Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="64cd0-136">Using Serviced Components with the Global Assembly Cache</span></span>](use-serviced-components-with-the-gac.md)  
<span data-ttu-id="64cd0-137">Explique pourquoi les composants traités (composants COM+ managés) doivent être placés dans le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="64cd0-137">Explains why serviced components (managed COM+ components) should be placed in the global assembly cache.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="64cd0-138">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="64cd0-138">Related Sections</span></span>  

[<span data-ttu-id="64cd0-139">Création d’assemblys</span><span class="sxs-lookup"><span data-stu-id="64cd0-139">Creating Assemblies</span></span>](../../standard/assembly/create.md)  
<span data-ttu-id="64cd0-140">Fournit une vue d’ensemble de la création d’assemblys.</span><span class="sxs-lookup"><span data-stu-id="64cd0-140">Provides an overview of creating assemblies.</span></span>  
  
[<span data-ttu-id="64cd0-141">Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="64cd0-141">Global Assembly Cache</span></span>](gac.md)  
<span data-ttu-id="64cd0-142">Décrit le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="64cd0-142">Describes the global assembly cache.</span></span>  
  
[<span data-ttu-id="64cd0-143">Guide pratique pour afficher le contenu d’un assembly</span><span class="sxs-lookup"><span data-stu-id="64cd0-143">How to: View Assembly Contents</span></span>](../../standard/assembly/view-contents.md)  
<span data-ttu-id="64cd0-144">Explique comment utiliser [Ildasm.exe (Désassembleur IL)](../tools/ildasm-exe-il-disassembler.md) pour visualiser les informations du langage MSIL (Microsoft Intermediate Language) dans un assembly.</span><span class="sxs-lookup"><span data-stu-id="64cd0-144">Explains how to use the [Ildasm.exe (IL Disassembler)](../tools/ildasm-exe-il-disassembler.md) to view Microsoft intermediate language (MSIL) information in an assembly.</span></span>  
  
[<span data-ttu-id="64cd0-145">Méthode de localisation des assemblys par le runtime</span><span class="sxs-lookup"><span data-stu-id="64cd0-145">How the Runtime Locates Assemblies</span></span>](../deployment/how-the-runtime-locates-assemblies.md)  
<span data-ttu-id="64cd0-146">Décrit comment le common language runtime localise et charge les assemblys qui composent votre application.</span><span class="sxs-lookup"><span data-stu-id="64cd0-146">Describes how the common language runtime locates and loads the assemblies that make up your application.</span></span>  
  
[<span data-ttu-id="64cd0-147">Programmation à l’aide d’assemblys</span><span class="sxs-lookup"><span data-stu-id="64cd0-147">Programming with Assemblies</span></span>](../../standard/assembly/index.md)  
<span data-ttu-id="64cd0-148">Décrit les assemblys, les blocs de construction des applications managées.</span><span class="sxs-lookup"><span data-stu-id="64cd0-148">Describes assemblies, the building blocks of managed applications.</span></span>
