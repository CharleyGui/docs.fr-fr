---
title: Utilisation d'assemblys et du Global Assembly Cache
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- global assembly cache, benefits
- ACLs [.NET Framework]
- GAC (global assembly cache), benefits
- access control lists [.NET Framework]
ms.assetid: 8a18e5c2-d41d-49ef-abcb-7c27e2469433
ms.openlocfilehash: 7834fbc4d74b44c4bc5204ac451e92cac22e1ef5
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645419"
---
# <a name="working-with-assemblies-and-the-global-assembly-cache"></a><span data-ttu-id="c7c33-102">Utilisation d'assemblys et du Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="c7c33-102">Working with Assemblies and the Global Assembly Cache</span></span>

<span data-ttu-id="c7c33-103">Si vous prévoyez de partager un assembly entre plusieurs applications, vous pouvez l’installer dans le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="c7c33-103">If you intend to share an assembly among several applications, you can install it into the global assembly cache.</span></span> <span data-ttu-id="c7c33-104">Chaque ordinateur où le common language runtime est installé a ce cache de code à l’échelle de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="c7c33-104">Each computer where the common language runtime is installed has this machine-wide code cache.</span></span> <span data-ttu-id="c7c33-105">Le Global Assembly Cache stocke des assemblys spécialement destinés à être partagés entre plusieurs applications sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="c7c33-105">The global assembly cache stores assemblies specifically designated to be shared by several applications on the computer.</span></span> <span data-ttu-id="c7c33-106">Un assembly doit avoir un nom fort pour être installé dans le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="c7c33-106">An assembly must have a strong name to be installed in the global assembly cache.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c7c33-107">Les assemblys placés dans le Global Assembly Cache doivent avoir le même nom d’assembly et le même nom de fichier (sans l’extension du nom de fichier).</span><span class="sxs-lookup"><span data-stu-id="c7c33-107">Assemblies placed in the global assembly cache must have the same assembly name and file name (not including the file name extension).</span></span> <span data-ttu-id="c7c33-108">Par exemple, un assembly avec le nom d’assembly monAssembly doit avoir le nom de fichier monAssembly.exe ou monAssembly.dll.</span><span class="sxs-lookup"><span data-stu-id="c7c33-108">For example, an assembly with the assembly name of myAssembly must have a file name of either myAssembly.exe or myAssembly.dll.</span></span>  
  
<span data-ttu-id="c7c33-109">Il est recommandé de partager des assemblys en les installant dans le Global Assembly Cache seulement quand c’est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="c7c33-109">You should share assemblies by installing them into the global assembly cache only when necessary.</span></span> <span data-ttu-id="c7c33-110">Une règle générale est de conserver les dépendances d’assembly privées et de placer les assemblys dans le répertoire de l’application, sauf si le partage d’un assembly est explicitement nécessaire.</span><span class="sxs-lookup"><span data-stu-id="c7c33-110">As a general guideline, keep assembly dependencies private and locate assemblies in the application directory unless sharing an assembly is explicitly required.</span></span> <span data-ttu-id="c7c33-111">En outre, il n’est pas nécessaire d’installer des assemblys dans le Global Assembly Cache pour les rendre accessibles à COM Interop ou à du code non managé.</span><span class="sxs-lookup"><span data-stu-id="c7c33-111">In addition, you do not have to install assemblies into the global assembly cache to make them accessible to COM interop or unmanaged code.</span></span>  
  
<span data-ttu-id="c7c33-112">Vous pouvez souhaiter installer un assembly dans le Global Assembly Cache pour plusieurs raisons :</span><span class="sxs-lookup"><span data-stu-id="c7c33-112">There are several reasons why you might want to install an assembly into the global assembly cache:</span></span>  
  
- <span data-ttu-id="c7c33-113">Emplacement partagé.</span><span class="sxs-lookup"><span data-stu-id="c7c33-113">Shared location.</span></span>  
  
     <span data-ttu-id="c7c33-114">Les assemblys qui doivent être utilisés par des applications peuvent être placés dans le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="c7c33-114">Assemblies that should be used by applications can be put in the global assembly cache.</span></span> <span data-ttu-id="c7c33-115">Par exemple, si toutes les applications doivent utiliser un assembly qui se trouve dans le Global Assembly Cache, vous pouvez ajouter une instruction de stratégie de version au fichier Machine.config pour rediriger les références à l’assembly.</span><span class="sxs-lookup"><span data-stu-id="c7c33-115">For example, if all applications should use an assembly located in the global assembly cache, a version policy statement can be added to the Machine.config file that redirects references to the assembly.</span></span>  
  
- <span data-ttu-id="c7c33-116">Sécurité des fichiers.</span><span class="sxs-lookup"><span data-stu-id="c7c33-116">File security.</span></span>  
  
     <span data-ttu-id="c7c33-117">Les administrateurs protègent souvent le répertoire systemroot en utilisant une liste de contrôle d’accès pour contrôler l’accès en écriture et en exécution.</span><span class="sxs-lookup"><span data-stu-id="c7c33-117">Administrators often protect the systemroot directory using an Access Control List (ACL) to control write and execute access.</span></span> <span data-ttu-id="c7c33-118">Le Global Assembly Cache étant installé dans le répertoire systemroot, il hérite de la liste de contrôle d’accès de ce répertoire.</span><span class="sxs-lookup"><span data-stu-id="c7c33-118">Because the global assembly cache is installed in the systemroot directory, it inherits that directory's ACL.</span></span> <span data-ttu-id="c7c33-119">Il est recommandé que seuls les utilisateurs disposant de privilèges d’administrateur soient autorisés à supprimer des fichiers du Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="c7c33-119">It is recommended that only users with Administrator privileges be allowed to delete files from the global assembly cache.</span></span>  
  
- <span data-ttu-id="c7c33-120">Contrôle de version côte à côte.</span><span class="sxs-lookup"><span data-stu-id="c7c33-120">Side-by-side versioning.</span></span>  
  
     <span data-ttu-id="c7c33-121">Plusieurs copies des assemblys avec le même nom mais avec des informations de version différentes peuvent être conservées dans le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="c7c33-121">Multiple copies of assemblies with the same name but different version information can be maintained in the global assembly cache.</span></span>  
  
- <span data-ttu-id="c7c33-122">Emplacements de recherche supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="c7c33-122">Additional search location.</span></span>  
  
     <span data-ttu-id="c7c33-123">Le common language runtime recherche dans le Global Assembly Cache un assembly qui correspond à l’assembly demandé avant de chercher ailleurs ou d’utiliser les informations du code base dans un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="c7c33-123">The common language runtime checks the global assembly cache for an assembly that matches the assembly request before probing or using the codebase information in a configuration file.</span></span>  
  
 <span data-ttu-id="c7c33-124">Notez que dans certains scénarios, vous ne voulez explicitement pas installer un assembly dans le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="c7c33-124">Note that there are scenarios where you explicitly do not want to install an assembly into the global assembly cache.</span></span> <span data-ttu-id="c7c33-125">Si vous placez un des assemblys composant une application dans le Global Assembly Cache, vous ne pouvez plus répliquer ni installer l’application en utilisant XCOPY pour copier le répertoire de l’application.</span><span class="sxs-lookup"><span data-stu-id="c7c33-125">If you place one of the assemblies that make up an application into the global assembly cache, you can no longer replicate or install the application by using XCOPY to copy the application directory.</span></span> <span data-ttu-id="c7c33-126">Dans ce cas, vous devez également déplacer l’assembly dans le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="c7c33-126">In this case, you must also move the assembly into the global assembly cache.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c7c33-127">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="c7c33-127">In This Section</span></span>  
[<span data-ttu-id="c7c33-128">Comment : installer un assembly dans le global assembly cache</span><span class="sxs-lookup"><span data-stu-id="c7c33-128">How to: Install an Assembly into the Global Assembly Cache</span></span>](install-assembly-into-gac.md)  
<span data-ttu-id="c7c33-129">Décrit les façons d’installer un assembly dans le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="c7c33-129">Describes the ways to install an assembly into the global assembly cache.</span></span>  
  
[<span data-ttu-id="c7c33-130">Guide pratique pour visualiser le contenu du Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="c7c33-130">How to: View the Contents of the Global Assembly Cache</span></span>](how-to-view-the-contents-of-the-gac.md)  
<span data-ttu-id="c7c33-131">Explique comment utiliser [Gacutil.exe (outil Global Assembly Cache](../tools/gacutil-exe-gac-tool.md) pour visualiser le contenu du Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="c7c33-131">Explains how to use the [Gacutil.exe (Global Assembly Cache Tool)](../tools/gacutil-exe-gac-tool.md) to view the contents of the global assembly cache.</span></span>  
  
[<span data-ttu-id="c7c33-132">Guide pratique pour supprimer un assembly du Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="c7c33-132">How to: Remove an Assembly from the Global Assembly Cache</span></span>](how-to-remove-an-assembly-from-the-gac.md)  
<span data-ttu-id="c7c33-133">Explique comment utiliser [Gacutil.exe (outil Global Assembly Cache](../tools/gacutil-exe-gac-tool.md) pour supprimer un assembly du Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="c7c33-133">Explains how to use the [Gacutil.exe (Global Assembly Cache Tool)](../tools/gacutil-exe-gac-tool.md) to remove an assembly from the global assembly cache.</span></span>  
  
[<span data-ttu-id="c7c33-134">Utilisation de composants de service avec le Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="c7c33-134">Using Serviced Components with the Global Assembly Cache</span></span>](use-serviced-components-with-the-gac.md)  
<span data-ttu-id="c7c33-135">Explique pourquoi les composants traités (composants COM+ managés) doivent être placés dans le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="c7c33-135">Explains why serviced components (managed COM+ components) should be placed in the global assembly cache.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c7c33-136">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="c7c33-136">Related Sections</span></span>  

[<span data-ttu-id="c7c33-137">Création d’assemblys</span><span class="sxs-lookup"><span data-stu-id="c7c33-137">Creating Assemblies</span></span>](../../standard/assembly/create.md)  
<span data-ttu-id="c7c33-138">Fournit une vue d’ensemble de la création d’assemblys.</span><span class="sxs-lookup"><span data-stu-id="c7c33-138">Provides an overview of creating assemblies.</span></span>  
  
[<span data-ttu-id="c7c33-139">Global assembly cache</span><span class="sxs-lookup"><span data-stu-id="c7c33-139">Global Assembly Cache</span></span>](gac.md)  
<span data-ttu-id="c7c33-140">Décrit le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="c7c33-140">Describes the global assembly cache.</span></span>  
  
[<span data-ttu-id="c7c33-141">Guide pratique pour afficher le contenu d’un assembly</span><span class="sxs-lookup"><span data-stu-id="c7c33-141">How to: View Assembly Contents</span></span>](../../standard/assembly/view-contents.md)  
<span data-ttu-id="c7c33-142">Explique comment utiliser [Ildasm.exe (Désassembleur IL)](../tools/ildasm-exe-il-disassembler.md) pour visualiser les informations du langage MSIL (Microsoft Intermediate Language) dans un assembly.</span><span class="sxs-lookup"><span data-stu-id="c7c33-142">Explains how to use the [Ildasm.exe (IL Disassembler)](../tools/ildasm-exe-il-disassembler.md) to view Microsoft intermediate language (MSIL) information in an assembly.</span></span>  
  
[<span data-ttu-id="c7c33-143">Méthode de localisation des assemblys par le runtime</span><span class="sxs-lookup"><span data-stu-id="c7c33-143">How the Runtime Locates Assemblies</span></span>](../deployment/how-the-runtime-locates-assemblies.md)  
<span data-ttu-id="c7c33-144">Décrit comment le common language runtime localise et charge les assemblys qui composent votre application.</span><span class="sxs-lookup"><span data-stu-id="c7c33-144">Describes how the common language runtime locates and loads the assemblies that make up your application.</span></span>  
  
[<span data-ttu-id="c7c33-145">Programmation à l’aide d’assemblys</span><span class="sxs-lookup"><span data-stu-id="c7c33-145">Programming with Assemblies</span></span>](../../standard/assembly/index.md)  
<span data-ttu-id="c7c33-146">Décrit les assemblys, les blocs de construction des applications managées.</span><span class="sxs-lookup"><span data-stu-id="c7c33-146">Describes assemblies, the building blocks of managed applications.</span></span>
