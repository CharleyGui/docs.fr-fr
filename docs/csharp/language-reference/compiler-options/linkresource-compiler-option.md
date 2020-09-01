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
ms.openlocfilehash: 162baad57397b6d992dcf8f03f0b3661e0105cb8
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125343"
---
# <a name="-linkresource-c-compiler-options"></a><span data-ttu-id="9e44d-103">-linkresource (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="9e44d-103">-linkresource (C# Compiler Options)</span></span>
<span data-ttu-id="9e44d-104">Crée un lien vers une ressource .NET Framework dans le fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="9e44d-104">Creates a link to a .NET Framework resource in the output file.</span></span> <span data-ttu-id="9e44d-105">Le fichier de ressources n’est pas ajouté au fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="9e44d-105">The resource file is not added to the output file.</span></span> <span data-ttu-id="9e44d-106">Cette option diffère de l’option [-resource](./resource-compiler-option.md) qui incorpore un fichier de ressources dans le fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="9e44d-106">This differs from the [-resource](./resource-compiler-option.md) option which does embed a resource file in the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e44d-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9e44d-107">Syntax</span></span>  
  
```console  
-linkresource:filename[,identifier[,accessibility-modifier]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="9e44d-108">Arguments</span><span class="sxs-lookup"><span data-stu-id="9e44d-108">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="9e44d-109">Fichier de ressources .NET Framework que vous voulez lier à l’assembly.</span><span class="sxs-lookup"><span data-stu-id="9e44d-109">The .NET Framework resource file to which you want to link from the assembly.</span></span>  
  
 <span data-ttu-id="9e44d-110">`identifier` (facultatif)</span><span class="sxs-lookup"><span data-stu-id="9e44d-110">`identifier` (optional)</span></span>  
 <span data-ttu-id="9e44d-111">Nom logique de la ressource. Il s’agit du nom utilisé pour charger la ressource.</span><span class="sxs-lookup"><span data-stu-id="9e44d-111">The logical name for the resource; the name that is used to load the resource.</span></span> <span data-ttu-id="9e44d-112">La valeur par défaut est le nom du fichier.</span><span class="sxs-lookup"><span data-stu-id="9e44d-112">The default is the name of the file.</span></span>  
  
 <span data-ttu-id="9e44d-113">`accessibility-modifier` (facultatif)</span><span class="sxs-lookup"><span data-stu-id="9e44d-113">`accessibility-modifier` (optional)</span></span>  
 <span data-ttu-id="9e44d-114">Accessibilité de la ressource : publique ou privée.</span><span class="sxs-lookup"><span data-stu-id="9e44d-114">The accessibility of the resource: public or private.</span></span> <span data-ttu-id="9e44d-115">La valeur par défaut est public.</span><span class="sxs-lookup"><span data-stu-id="9e44d-115">The default is public.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9e44d-116">Remarques</span><span class="sxs-lookup"><span data-stu-id="9e44d-116">Remarks</span></span>  
 <span data-ttu-id="9e44d-117">Par défaut, les ressources liées sont publiques dans l’assembly quand elles sont créées avec le compilateur C#.</span><span class="sxs-lookup"><span data-stu-id="9e44d-117">By default, linked resources are public in the assembly when they are created with the C# compiler.</span></span> <span data-ttu-id="9e44d-118">Pour rendre les ressources privées, spécifiez le modificateur d’accessibilité `private`.</span><span class="sxs-lookup"><span data-stu-id="9e44d-118">To make the resources private, specify `private` as the accessibility modifier.</span></span> <span data-ttu-id="9e44d-119">Aucun autre modificateur que `public` ou `private` n’est autorisé.</span><span class="sxs-lookup"><span data-stu-id="9e44d-119">No other modifier other than `public` or `private` is allowed.</span></span>  
  
 <span data-ttu-id="9e44d-120">**-linkresource** nécessite une option [-target](./target-compiler-option.md) autre que **-target:module**.</span><span class="sxs-lookup"><span data-stu-id="9e44d-120">**-linkresource** requires one of the [-target](./target-compiler-option.md) options other than **-target:module**.</span></span>  
  
 <span data-ttu-id="9e44d-121">Si `filename` est un fichier de ressources .NET Framework créé, par exemple, par [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) ou dans l'environnement de développement, il est accessible à l'aide des membres de l'espace de noms <xref:System.Resources>.</span><span class="sxs-lookup"><span data-stu-id="9e44d-121">If `filename` is a .NET Framework resource file created, for example, by [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace.</span></span> <span data-ttu-id="9e44d-122">Pour plus d'informations, consultez <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9e44d-122">For more information, see <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span></span> <span data-ttu-id="9e44d-123">Pour toutes les autres ressources, utilisez les méthodes `GetManifestResource` dans la classe <xref:System.Reflection.Assembly> pour accéder à la ressource au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="9e44d-123">For all other resources, use the `GetManifestResource` methods in the <xref:System.Reflection.Assembly> class to access the resource at run time.</span></span>  
  
 <span data-ttu-id="9e44d-124">Le fichier spécifié dans `filename` peut avoir n’importe quel format.</span><span class="sxs-lookup"><span data-stu-id="9e44d-124">The file specified in `filename` can be any format.</span></span> <span data-ttu-id="9e44d-125">C’est le cas, par exemple, si vous voulez qu’une DLL native fasse partie de l'assembly pour qu’elle puisse être installée dans le Global Assembly Cache et accessible à partir du code managé dans l'assembly.</span><span class="sxs-lookup"><span data-stu-id="9e44d-125">For example, you may want to make a native DLL part of the assembly, so that it can be installed into the global assembly cache and accessed from managed code in the assembly.</span></span> <span data-ttu-id="9e44d-126">Le deuxième des exemples suivants montre comment effectuer cette opération.</span><span class="sxs-lookup"><span data-stu-id="9e44d-126">The second of the following examples shows how to do this.</span></span> <span data-ttu-id="9e44d-127">Vous pouvez effectuer la même opération dans Assembly Linker.</span><span class="sxs-lookup"><span data-stu-id="9e44d-127">You can do the same thing in the Assembly Linker.</span></span> <span data-ttu-id="9e44d-128">Le troisième des exemples suivants montre comment effectuer cette opération.</span><span class="sxs-lookup"><span data-stu-id="9e44d-128">The third of the following examples shows how to do this.</span></span> <span data-ttu-id="9e44d-129">Pour plus d’informations, consultez [Al.exe (Assembly Linker)](../../../framework/tools/al-exe-assembly-linker.md) et [Utilisation d’assemblys et du Global Assembly Cache](../../../framework/app-domains/working-with-assemblies-and-the-gac.md).</span><span class="sxs-lookup"><span data-stu-id="9e44d-129">For more information, see [Al.exe (Assembly Linker)](../../../framework/tools/al-exe-assembly-linker.md) and [Working with Assemblies and the Global Assembly Cache](../../../framework/app-domains/working-with-assemblies-and-the-gac.md).</span></span>  
  
 <span data-ttu-id="9e44d-130">**-linkres** est la forme abrégée de **-linkresource**.</span><span class="sxs-lookup"><span data-stu-id="9e44d-130">**-linkres** is the short form of **-linkresource**.</span></span>  
  
 <span data-ttu-id="9e44d-131">Cette option de compilateur n’est pas disponible dans Visual Studio et ne peut pas être changée par programmation.</span><span class="sxs-lookup"><span data-stu-id="9e44d-131">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9e44d-132">Exemple</span><span class="sxs-lookup"><span data-stu-id="9e44d-132">Example</span></span>  
 <span data-ttu-id="9e44d-133">Compiler `in.cs` et créer un lien vers le fichier de ressources `rf.resource` :</span><span class="sxs-lookup"><span data-stu-id="9e44d-133">Compile `in.cs` and link to resource file `rf.resource`:</span></span>  
  
```console  
csc -linkresource:rf.resource in.cs  
```  
  
## <a name="example"></a><span data-ttu-id="9e44d-134">Exemple</span><span class="sxs-lookup"><span data-stu-id="9e44d-134">Example</span></span>  
 <span data-ttu-id="9e44d-135">Compiler `A.cs` dans une DLL, créer un lien vers une DLL native N.dll et placer la sortie dans le Global Assembly Cache (GAC).</span><span class="sxs-lookup"><span data-stu-id="9e44d-135">Compile `A.cs` into a DLL, link to a native DLL N.dll, and put the output in the Global Assembly Cache (GAC).</span></span> <span data-ttu-id="9e44d-136">Dans cet exemple, A.dll et N.dll résident dans le GAC.</span><span class="sxs-lookup"><span data-stu-id="9e44d-136">In this example, both A.dll and N.dll will reside in the GAC.</span></span>  
  
```console  
csc -linkresource:N.dll -t:library A.cs  
gacutil -i A.dll  
```  
  
## <a name="example"></a><span data-ttu-id="9e44d-137">Exemple</span><span class="sxs-lookup"><span data-stu-id="9e44d-137">Example</span></span>  
 <span data-ttu-id="9e44d-138">Cet exemple obtient le même résultat, mais en utilisant des options Assembly Linker.</span><span class="sxs-lookup"><span data-stu-id="9e44d-138">This example does the same thing as the previous one, but by using Assembly Linker options.</span></span>  
  
```console  
csc -t:module A.cs  
al -out:A.dll A.netmodule -link:N.dll
gacutil -i A.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="9e44d-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9e44d-139">See also</span></span>

- [<span data-ttu-id="9e44d-140">Options du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="9e44d-140">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="9e44d-141">Al.exe (Assembly Linker)</span><span class="sxs-lookup"><span data-stu-id="9e44d-141">Al.exe (Assembly Linker)</span></span>](../../../framework/tools/al-exe-assembly-linker.md)
- [<span data-ttu-id="9e44d-142">Utilisation d'assemblys et du Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="9e44d-142">Working with Assemblies and the Global Assembly Cache</span></span>](../../../framework/app-domains/working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="9e44d-143">Gestion des propriétés des projets et des solutions</span><span class="sxs-lookup"><span data-stu-id="9e44d-143">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
