---
description: -linkresource (Options du compilateur C#)
title: -linkresource (Options du compilateur C#)
ms.date: 07/20/2015
f1_keywords:
- /linkresource
helpviewer_keywords:
- /linkresource compiler option [C#]
- linkres compiler option [C#]
- /linkres compiler option [C#]
- -linkres compiler option [C#]
- -linkresource compiler option [C#]
- linkresource compiler option [C#]
ms.assetid: 440c26c2-77c1-4811-a0a3-57cce3f5fc96
ms.openlocfilehash: 4efa0cbf286b40ad971bad66a7acce15e553eb39
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91194100"
---
# <a name="-linkresource-c-compiler-options"></a><span data-ttu-id="cff15-103">-linkresource (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="cff15-103">-linkresource (C# Compiler Options)</span></span>

<span data-ttu-id="cff15-104">Crée un lien vers une ressource .NET dans le fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="cff15-104">Creates a link to a .NET resource in the output file.</span></span> <span data-ttu-id="cff15-105">Le fichier de ressources n’est pas ajouté au fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="cff15-105">The resource file is not added to the output file.</span></span> <span data-ttu-id="cff15-106">Cette option diffère de l’option [-resource](./resource-compiler-option.md) qui incorpore un fichier de ressources dans le fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="cff15-106">This differs from the [-resource](./resource-compiler-option.md) option which does embed a resource file in the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cff15-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cff15-107">Syntax</span></span>  
  
```console  
-linkresource:filename[,identifier[,accessibility-modifier]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="cff15-108">Arguments</span><span class="sxs-lookup"><span data-stu-id="cff15-108">Arguments</span></span>  

 `filename`  
 <span data-ttu-id="cff15-109">Fichier de ressources .NET auquel vous souhaitez lier l’assembly.</span><span class="sxs-lookup"><span data-stu-id="cff15-109">The .NET resource file to which you want to link from the assembly.</span></span>  
  
 <span data-ttu-id="cff15-110">`identifier` (facultatif)</span><span class="sxs-lookup"><span data-stu-id="cff15-110">`identifier` (optional)</span></span>  
 <span data-ttu-id="cff15-111">Nom logique de la ressource. Il s’agit du nom utilisé pour charger la ressource.</span><span class="sxs-lookup"><span data-stu-id="cff15-111">The logical name for the resource; the name that is used to load the resource.</span></span> <span data-ttu-id="cff15-112">La valeur par défaut est le nom du fichier.</span><span class="sxs-lookup"><span data-stu-id="cff15-112">The default is the name of the file.</span></span>  
  
 <span data-ttu-id="cff15-113">`accessibility-modifier` (facultatif)</span><span class="sxs-lookup"><span data-stu-id="cff15-113">`accessibility-modifier` (optional)</span></span>  
 <span data-ttu-id="cff15-114">Accessibilité de la ressource : publique ou privée.</span><span class="sxs-lookup"><span data-stu-id="cff15-114">The accessibility of the resource: public or private.</span></span> <span data-ttu-id="cff15-115">La valeur par défaut est public.</span><span class="sxs-lookup"><span data-stu-id="cff15-115">The default is public.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cff15-116">Notes</span><span class="sxs-lookup"><span data-stu-id="cff15-116">Remarks</span></span>  

 <span data-ttu-id="cff15-117">Par défaut, les ressources liées sont publiques dans l’assembly quand elles sont créées avec le compilateur C#.</span><span class="sxs-lookup"><span data-stu-id="cff15-117">By default, linked resources are public in the assembly when they are created with the C# compiler.</span></span> <span data-ttu-id="cff15-118">Pour rendre les ressources privées, spécifiez le modificateur d’accessibilité `private`.</span><span class="sxs-lookup"><span data-stu-id="cff15-118">To make the resources private, specify `private` as the accessibility modifier.</span></span> <span data-ttu-id="cff15-119">Aucun autre modificateur que `public` ou `private` n’est autorisé.</span><span class="sxs-lookup"><span data-stu-id="cff15-119">No other modifier other than `public` or `private` is allowed.</span></span>  
  
 <span data-ttu-id="cff15-120">**-linkresource** nécessite une option [-target](./target-compiler-option.md) autre que **-target:module**.</span><span class="sxs-lookup"><span data-stu-id="cff15-120">**-linkresource** requires one of the [-target](./target-compiler-option.md) options other than **-target:module**.</span></span>  
  
 <span data-ttu-id="cff15-121">Si `filename` est un fichier de ressources .net créé, par exemple par [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) ou dans l’environnement de développement, il est accessible à l’aide des membres de l' <xref:System.Resources> espace de noms.</span><span class="sxs-lookup"><span data-stu-id="cff15-121">If `filename` is a .NET resource file created, for example, by [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace.</span></span> <span data-ttu-id="cff15-122">Pour plus d'informations, consultez <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="cff15-122">For more information, see <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span></span> <span data-ttu-id="cff15-123">Pour toutes les autres ressources, utilisez les méthodes `GetManifestResource` dans la classe <xref:System.Reflection.Assembly> pour accéder à la ressource au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="cff15-123">For all other resources, use the `GetManifestResource` methods in the <xref:System.Reflection.Assembly> class to access the resource at run time.</span></span>  
  
 <span data-ttu-id="cff15-124">Le fichier spécifié dans `filename` peut avoir n’importe quel format.</span><span class="sxs-lookup"><span data-stu-id="cff15-124">The file specified in `filename` can be any format.</span></span> <span data-ttu-id="cff15-125">C’est le cas, par exemple, si vous voulez qu’une DLL native fasse partie de l'assembly pour qu’elle puisse être installée dans le Global Assembly Cache et accessible à partir du code managé dans l'assembly.</span><span class="sxs-lookup"><span data-stu-id="cff15-125">For example, you may want to make a native DLL part of the assembly, so that it can be installed into the global assembly cache and accessed from managed code in the assembly.</span></span> <span data-ttu-id="cff15-126">Le deuxième des exemples suivants montre comment effectuer cette opération.</span><span class="sxs-lookup"><span data-stu-id="cff15-126">The second of the following examples shows how to do this.</span></span> <span data-ttu-id="cff15-127">Vous pouvez effectuer la même opération dans Assembly Linker.</span><span class="sxs-lookup"><span data-stu-id="cff15-127">You can do the same thing in the Assembly Linker.</span></span> <span data-ttu-id="cff15-128">Le troisième des exemples suivants montre comment effectuer cette opération.</span><span class="sxs-lookup"><span data-stu-id="cff15-128">The third of the following examples shows how to do this.</span></span> <span data-ttu-id="cff15-129">Pour plus d’informations, consultez [Al.exe (Assembly Linker)](../../../framework/tools/al-exe-assembly-linker.md) et [Utilisation d’assemblys et du Global Assembly Cache](../../../framework/app-domains/working-with-assemblies-and-the-gac.md).</span><span class="sxs-lookup"><span data-stu-id="cff15-129">For more information, see [Al.exe (Assembly Linker)](../../../framework/tools/al-exe-assembly-linker.md) and [Working with Assemblies and the Global Assembly Cache](../../../framework/app-domains/working-with-assemblies-and-the-gac.md).</span></span>  
  
 <span data-ttu-id="cff15-130">**-linkres** est la forme abrégée de **-linkresource**.</span><span class="sxs-lookup"><span data-stu-id="cff15-130">**-linkres** is the short form of **-linkresource**.</span></span>  
  
 <span data-ttu-id="cff15-131">Cette option de compilateur n’est pas disponible dans Visual Studio et ne peut pas être changée par programmation.</span><span class="sxs-lookup"><span data-stu-id="cff15-131">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cff15-132">Exemple</span><span class="sxs-lookup"><span data-stu-id="cff15-132">Example</span></span>  

 <span data-ttu-id="cff15-133">Compiler `in.cs` et créer un lien vers le fichier de ressources `rf.resource` :</span><span class="sxs-lookup"><span data-stu-id="cff15-133">Compile `in.cs` and link to resource file `rf.resource`:</span></span>  
  
```console  
csc -linkresource:rf.resource in.cs  
```  
  
## <a name="example"></a><span data-ttu-id="cff15-134">Exemple</span><span class="sxs-lookup"><span data-stu-id="cff15-134">Example</span></span>  

 <span data-ttu-id="cff15-135">Compiler `A.cs` dans une DLL, créer un lien vers une DLL native N.dll et placer la sortie dans le Global Assembly Cache (GAC).</span><span class="sxs-lookup"><span data-stu-id="cff15-135">Compile `A.cs` into a DLL, link to a native DLL N.dll, and put the output in the Global Assembly Cache (GAC).</span></span> <span data-ttu-id="cff15-136">Dans cet exemple, A.dll et N.dll résident dans le GAC.</span><span class="sxs-lookup"><span data-stu-id="cff15-136">In this example, both A.dll and N.dll will reside in the GAC.</span></span>  
  
```console  
csc -linkresource:N.dll -t:library A.cs  
gacutil -i A.dll  
```  
  
## <a name="example"></a><span data-ttu-id="cff15-137">Exemple</span><span class="sxs-lookup"><span data-stu-id="cff15-137">Example</span></span>  

 <span data-ttu-id="cff15-138">Cet exemple obtient le même résultat, mais en utilisant des options Assembly Linker.</span><span class="sxs-lookup"><span data-stu-id="cff15-138">This example does the same thing as the previous one, but by using Assembly Linker options.</span></span>  
  
```console  
csc -t:module A.cs  
al -out:A.dll A.netmodule -link:N.dll
gacutil -i A.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="cff15-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cff15-139">See also</span></span>

- [<span data-ttu-id="cff15-140">Options du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="cff15-140">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="cff15-141">Al.exe (Assembly Linker)</span><span class="sxs-lookup"><span data-stu-id="cff15-141">Al.exe (Assembly Linker)</span></span>](../../../framework/tools/al-exe-assembly-linker.md)
- [<span data-ttu-id="cff15-142">Utilisation d'assemblys et du Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="cff15-142">Working with Assemblies and the Global Assembly Cache</span></span>](../../../framework/app-domains/working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="cff15-143">Gestion des propriétés des projets et des solutions</span><span class="sxs-lookup"><span data-stu-id="cff15-143">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
