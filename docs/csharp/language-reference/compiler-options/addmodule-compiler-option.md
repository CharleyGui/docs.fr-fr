---
description: -addmodule (Options du compilateur C#)
title: -addmodule (Options du compilateur C#)
ms.date: 07/20/2015
f1_keywords:
- /addmodule
helpviewer_keywords:
- /addmodule compiler option [C#]
- -addmodule compiler option [C#]
- addmodule compiler option [C#]
ms.assetid: ed604546-0dc2-4bd4-9a3e-610a8d973e58
ms.openlocfilehash: bcc615d52aec0a09ebf3913b3ece71f2cbfcbda9
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89126123"
---
# <a name="-addmodule-c-compiler-options"></a><span data-ttu-id="e4a0f-103">-addmodule (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="e4a0f-103">-addmodule (C# Compiler Options)</span></span>
<span data-ttu-id="e4a0f-104">Cette option ajoute un module créé avec le commutateur target:module à la compilation actuelle.</span><span class="sxs-lookup"><span data-stu-id="e4a0f-104">This option adds a module that was created with the target:module switch to the current compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4a0f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e4a0f-105">Syntax</span></span>  
  
```console  
-addmodule:file[;file2]  
```  
  
## <a name="arguments"></a><span data-ttu-id="e4a0f-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="e4a0f-106">Arguments</span></span>  
 <span data-ttu-id="e4a0f-107">`file`, `file2`</span><span class="sxs-lookup"><span data-stu-id="e4a0f-107">`file`, `file2`</span></span>  
 <span data-ttu-id="e4a0f-108">Fichier de sortie qui contient des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="e4a0f-108">An output file that contains metadata.</span></span> <span data-ttu-id="e4a0f-109">Le fichier ne peut pas contenir un manifeste d’assembly.</span><span class="sxs-lookup"><span data-stu-id="e4a0f-109">The file cannot contain an assembly manifest.</span></span> <span data-ttu-id="e4a0f-110">Pour importer plusieurs fichiers, séparez les noms des fichiers par une virgule ou un point-virgule.</span><span class="sxs-lookup"><span data-stu-id="e4a0f-110">To import more than one file, separate file names with either a comma or a semicolon.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e4a0f-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="e4a0f-111">Remarks</span></span>  
 <span data-ttu-id="e4a0f-112">Tous les modules ajoutés par **-addmodule** doivent se trouver dans le même répertoire que le fichier de sortie au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="e4a0f-112">All modules added with **-addmodule** must be in the same directory as the output file at run time.</span></span> <span data-ttu-id="e4a0f-113">Vous pouvez donc spécifier un module dans n’importe quel répertoire au moment de la compilation, mais le module doit se trouver dans le répertoire de l’application au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="e4a0f-113">That is, you can specify a module in any directory at compile time but the module must be in the application directory at run time.</span></span> <span data-ttu-id="e4a0f-114">Si le module n’est pas dans le répertoire de l’application au moment de l’exécution, vous obtiendrez <xref:System.TypeLoadException>.</span><span class="sxs-lookup"><span data-stu-id="e4a0f-114">If the module is not in the application directory at run time, you will get a <xref:System.TypeLoadException>.</span></span>  
  
 <span data-ttu-id="e4a0f-115">`file` ne peut pas contenir un assembly.</span><span class="sxs-lookup"><span data-stu-id="e4a0f-115">`file` cannot contain an assembly.</span></span> <span data-ttu-id="e4a0f-116">Si, par exemple, le fichier de sortie a été créé avec [-target:module](./target-module-compiler-option.md), ses métadonnées peuvent être importées avec **-addmodule**.</span><span class="sxs-lookup"><span data-stu-id="e4a0f-116">For example, if the output file was created with [-target:module](./target-module-compiler-option.md), its metadata can be imported with **-addmodule**.</span></span>  
  
 <span data-ttu-id="e4a0f-117">Si le fichier de sortie a été créé avec une option **-target** autre que **-target:module**, ses métadonnées ne peuvent pas être importées avec **-addmodule**, mais peuvent l’être avec [-reference](./reference-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="e4a0f-117">If the output file was created with a **-target** option other than **-target:module**, its metadata cannot be imported with **-addmodule** but can be imported with [-reference](./reference-compiler-option.md).</span></span>  
  
 <span data-ttu-id="e4a0f-118">Cette option du compilateur n’est pas disponible dans Visual Studio ; un projet ne peut pas référencer un module.</span><span class="sxs-lookup"><span data-stu-id="e4a0f-118">This compiler option is unavailable in Visual Studio; a project cannot reference a module.</span></span> <span data-ttu-id="e4a0f-119">Par ailleurs, cette option du compilateur ne peut pas être changée par programmation.</span><span class="sxs-lookup"><span data-stu-id="e4a0f-119">In addition, this compiler option cannot be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e4a0f-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="e4a0f-120">Example</span></span>  
 <span data-ttu-id="e4a0f-121">Compilez le fichier source `input.cs` et ajoutez les métadonnées de `metad1.netmodule` et `metad2.netmodule` pour produire `out.exe` :</span><span class="sxs-lookup"><span data-stu-id="e4a0f-121">Compile source file `input.cs` and add metadata from `metad1.netmodule` and `metad2.netmodule` to produce `out.exe`:</span></span>  
  
```console  
csc -addmodule:metad1.netmodule;metad2.netmodule -out:out.exe input.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="e4a0f-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e4a0f-122">See also</span></span>

- [<span data-ttu-id="e4a0f-123">Options du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="e4a0f-123">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="e4a0f-124">Gestion des propriétés des projets et des solutions</span><span class="sxs-lookup"><span data-stu-id="e4a0f-124">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="e4a0f-125">Assemblys multifichiers</span><span class="sxs-lookup"><span data-stu-id="e4a0f-125">Multifile Assemblies</span></span>](../../../framework/app-domains/multifile-assemblies.md)
- [<span data-ttu-id="e4a0f-126">Comment : générer un assembly multifichier</span><span class="sxs-lookup"><span data-stu-id="e4a0f-126">How to: Build a Multifile Assembly</span></span>](../../../framework/app-domains/build-multifile-assembly.md)
