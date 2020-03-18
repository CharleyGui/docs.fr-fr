---
title: -target:library (Options du compilateur C#)
ms.date: 07/20/2015
f1_keywords:
- /dll
helpviewer_keywords:
- -target compiler options [C#], /target:library
- target compiler options [C#], /target:library
- /target compiler options [C#], /target:library
ms.assetid: c5670e88-2126-47c1-8d1c-217923837d17
ms.openlocfilehash: c947b2015c19d0809cab4535e989ee83ebf17fd9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69606392"
---
# <a name="-targetlibrary-c-compiler-options"></a><span data-ttu-id="3617d-102">-target:library (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="3617d-102">-target:library (C# Compiler Options)</span></span>
<span data-ttu-id="3617d-103">L’option **-target:library** indique au compilateur de créer une bibliothèque de liens dynamiques (DLL) à la place d’un fichier exécutable (EXE).</span><span class="sxs-lookup"><span data-stu-id="3617d-103">The **-target:library** option causes the compiler to create a dynamic-link library (DLL) rather than an executable file (EXE).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3617d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3617d-104">Syntax</span></span>  
  
```console  
-target:library  
```  
  
## <a name="remarks"></a><span data-ttu-id="3617d-105">Notes </span><span class="sxs-lookup"><span data-stu-id="3617d-105">Remarks</span></span>  
 <span data-ttu-id="3617d-106">La DLL est créée avec l’extension .dll.</span><span class="sxs-lookup"><span data-stu-id="3617d-106">The DLL will be created with the .dll extension.</span></span>  
  
 <span data-ttu-id="3617d-107">Sauf spécification contraire avec l’option [-out](./out-compiler-option.md), le fichier de sortie prend le nom du premier fichier d’entrée.</span><span class="sxs-lookup"><span data-stu-id="3617d-107">Unless otherwise specified with the [-out](./out-compiler-option.md) option, the output file name takes the name of the first input file.</span></span>  
  
 <span data-ttu-id="3617d-108">Quand ils sont spécifiés dans la ligne de commande, tous les fichiers jusqu’à l’option **-out** ou **-target:module** suivante sont utilisés pour créer le fichier .dll.</span><span class="sxs-lookup"><span data-stu-id="3617d-108">When specified at the command line, all files up to the next **-out** or **-target:module** option are used to create the .dll file.</span></span>  
  
 <span data-ttu-id="3617d-109">Lors de la création d’un fichier .dll, une méthode [Main](../../programming-guide/main-and-command-args/index.md) n’est pas obligatoire.</span><span class="sxs-lookup"><span data-stu-id="3617d-109">When building a .dll file, a [Main](../../programming-guide/main-and-command-args/index.md) method is not required.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="3617d-110">Pour définir cette option du compilateur dans l'environnement de développement Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3617d-110">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="3617d-111">Ouvrez la page **Propriétés** du projet.</span><span class="sxs-lookup"><span data-stu-id="3617d-111">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="3617d-112">Cliquez sur la page de propriétés **Application**.</span><span class="sxs-lookup"><span data-stu-id="3617d-112">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="3617d-113">Modifiez la propriété **Type de sortie**.</span><span class="sxs-lookup"><span data-stu-id="3617d-113">Modify the **Output type** property.</span></span>  
  
 <span data-ttu-id="3617d-114">Pour plus d’informations sur la façon de définir cette option du compilateur par programmation, consultez <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="3617d-114">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3617d-115"> Exemple</span><span class="sxs-lookup"><span data-stu-id="3617d-115">Example</span></span>  
 <span data-ttu-id="3617d-116">Compilez `in.cs`, en créant `in.dll` :</span><span class="sxs-lookup"><span data-stu-id="3617d-116">Compile `in.cs`, creating `in.dll`:</span></span>  
  
```console  
csc -target:library in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="3617d-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3617d-117">See also</span></span>

- [<span data-ttu-id="3617d-118">-cible (Options compilateur C)</span><span class="sxs-lookup"><span data-stu-id="3617d-118">-target (C# Compiler Options)</span></span>](./target-compiler-option.md)
- [<span data-ttu-id="3617d-119">Options de compilateur C</span><span class="sxs-lookup"><span data-stu-id="3617d-119">C# Compiler Options</span></span>](./index.md)
