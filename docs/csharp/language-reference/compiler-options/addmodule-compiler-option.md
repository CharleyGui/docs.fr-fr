---
title: -addmodule (Options du compilateur C#)
ms.date: 07/20/2015
f1_keywords:
- /addmodule
helpviewer_keywords:
- /addmodule compiler option [C#]
- -addmodule compiler option [C#]
- addmodule compiler option [C#]
ms.assetid: ed604546-0dc2-4bd4-9a3e-610a8d973e58
ms.openlocfilehash: 148a63c37cfbc4c60448adccde10947e91e22bb9
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70970184"
---
# <a name="-addmodule-c-compiler-options"></a><span data-ttu-id="b5a10-102">-addmodule (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="b5a10-102">-addmodule (C# Compiler Options)</span></span>
<span data-ttu-id="b5a10-103">Cette option ajoute un module créé avec le commutateur target:module à la compilation actuelle.</span><span class="sxs-lookup"><span data-stu-id="b5a10-103">This option adds a module that was created with the target:module switch to the current compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5a10-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b5a10-104">Syntax</span></span>  
  
```console  
-addmodule:file[;file2]  
```  
  
## <a name="arguments"></a><span data-ttu-id="b5a10-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="b5a10-105">Arguments</span></span>  
 <span data-ttu-id="b5a10-106">`file`, `file2`</span><span class="sxs-lookup"><span data-stu-id="b5a10-106">`file`, `file2`</span></span>  
 <span data-ttu-id="b5a10-107">Fichier de sortie qui contient des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="b5a10-107">An output file that contains metadata.</span></span> <span data-ttu-id="b5a10-108">Le fichier ne peut pas contenir un manifeste d’assembly.</span><span class="sxs-lookup"><span data-stu-id="b5a10-108">The file cannot contain an assembly manifest.</span></span> <span data-ttu-id="b5a10-109">Pour importer plusieurs fichiers, séparez les noms des fichiers par une virgule ou un point-virgule.</span><span class="sxs-lookup"><span data-stu-id="b5a10-109">To import more than one file, separate file names with either a comma or a semicolon.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b5a10-110">Notes</span><span class="sxs-lookup"><span data-stu-id="b5a10-110">Remarks</span></span>  
 <span data-ttu-id="b5a10-111">Tous les modules ajoutés par **-addmodule** doivent se trouver dans le même répertoire que le fichier de sortie au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="b5a10-111">All modules added with **-addmodule** must be in the same directory as the output file at run time.</span></span> <span data-ttu-id="b5a10-112">Vous pouvez donc spécifier un module dans n’importe quel répertoire au moment de la compilation, mais le module doit se trouver dans le répertoire de l’application au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="b5a10-112">That is, you can specify a module in any directory at compile time but the module must be in the application directory at run time.</span></span> <span data-ttu-id="b5a10-113">Si le module n’est pas dans le répertoire de l’application au moment de l’exécution, vous obtiendrez <xref:System.TypeLoadException>.</span><span class="sxs-lookup"><span data-stu-id="b5a10-113">If the module is not in the application directory at run time, you will get a <xref:System.TypeLoadException>.</span></span>  
  
 <span data-ttu-id="b5a10-114">`file` ne peut pas contenir un assembly.</span><span class="sxs-lookup"><span data-stu-id="b5a10-114">`file` cannot contain an assembly.</span></span> <span data-ttu-id="b5a10-115">Si, par exemple, le fichier de sortie a été créé avec [-target:module](./target-module-compiler-option.md), ses métadonnées peuvent être importées avec **-addmodule**.</span><span class="sxs-lookup"><span data-stu-id="b5a10-115">For example, if the output file was created with [-target:module](./target-module-compiler-option.md), its metadata can be imported with **-addmodule**.</span></span>  
  
 <span data-ttu-id="b5a10-116">Si le fichier de sortie a été créé avec une option **-target** autre que **-target:module**, ses métadonnées ne peuvent pas être importées avec **-addmodule**, mais peuvent l’être avec [-reference](./reference-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="b5a10-116">If the output file was created with a **-target** option other than **-target:module**, its metadata cannot be imported with **-addmodule** but can be imported with [-reference](./reference-compiler-option.md).</span></span>  
  
 <span data-ttu-id="b5a10-117">Cette option du compilateur n’est pas disponible dans Visual Studio ; un projet ne peut pas référencer un module.</span><span class="sxs-lookup"><span data-stu-id="b5a10-117">This compiler option is unavailable in Visual Studio; a project cannot reference a module.</span></span> <span data-ttu-id="b5a10-118">Par ailleurs, cette option du compilateur ne peut pas être changée par programmation.</span><span class="sxs-lookup"><span data-stu-id="b5a10-118">In addition, this compiler option cannot be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b5a10-119">Exemple</span><span class="sxs-lookup"><span data-stu-id="b5a10-119">Example</span></span>  
 <span data-ttu-id="b5a10-120">Compilez le fichier source `input.cs` et ajoutez les métadonnées de `metad1.netmodule` et `metad2.netmodule` pour produire `out.exe` :</span><span class="sxs-lookup"><span data-stu-id="b5a10-120">Compile source file `input.cs` and add metadata from `metad1.netmodule` and `metad2.netmodule` to produce `out.exe`:</span></span>  
  
```console  
csc -addmodule:metad1.netmodule;metad2.netmodule -out:out.exe input.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="b5a10-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b5a10-121">See also</span></span>

- [<span data-ttu-id="b5a10-122">Options du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="b5a10-122">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="b5a10-123">Gestion des propriétés des projets et des solutions</span><span class="sxs-lookup"><span data-stu-id="b5a10-123">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="b5a10-124">Assemblys multifichiers</span><span class="sxs-lookup"><span data-stu-id="b5a10-124">Multifile Assemblies</span></span>](../../../framework/app-domains/multifile-assemblies.md)
- [<span data-ttu-id="b5a10-125">Guide pratique pour générer un assembly multifichier</span><span class="sxs-lookup"><span data-stu-id="b5a10-125">How to: Build a Multifile Assembly</span></span>](../../../framework/app-domains/build-multifile-assembly.md)
