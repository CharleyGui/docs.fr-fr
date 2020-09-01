---
description: -target:library (Options du compilateur C#)
title: -target:library (Options du compilateur C#)
ms.date: 07/20/2015
f1_keywords:
- /dll
helpviewer_keywords:
- -target compiler options [C#], /target:library
- target compiler options [C#], /target:library
- /target compiler options [C#], /target:library
ms.assetid: c5670e88-2126-47c1-8d1c-217923837d17
ms.openlocfilehash: 953249c4d0168ed3d279d03a0b2fb63d8ff6d5f5
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89128476"
---
# <a name="-targetlibrary-c-compiler-options"></a><span data-ttu-id="29f4a-103">-target:library (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="29f4a-103">-target:library (C# Compiler Options)</span></span>
<span data-ttu-id="29f4a-104">L’option **-target:library** indique au compilateur de créer une bibliothèque de liens dynamiques (DLL) à la place d’un fichier exécutable (EXE).</span><span class="sxs-lookup"><span data-stu-id="29f4a-104">The **-target:library** option causes the compiler to create a dynamic-link library (DLL) rather than an executable file (EXE).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29f4a-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="29f4a-105">Syntax</span></span>  
  
```console  
-target:library  
```  
  
## <a name="remarks"></a><span data-ttu-id="29f4a-106">Notes</span><span class="sxs-lookup"><span data-stu-id="29f4a-106">Remarks</span></span>  
 <span data-ttu-id="29f4a-107">La DLL est créée avec l’extension .dll.</span><span class="sxs-lookup"><span data-stu-id="29f4a-107">The DLL will be created with the .dll extension.</span></span>  
  
 <span data-ttu-id="29f4a-108">Sauf spécification contraire avec l’option [-out](./out-compiler-option.md), le fichier de sortie prend le nom du premier fichier d’entrée.</span><span class="sxs-lookup"><span data-stu-id="29f4a-108">Unless otherwise specified with the [-out](./out-compiler-option.md) option, the output file name takes the name of the first input file.</span></span>  
  
 <span data-ttu-id="29f4a-109">Quand ils sont spécifiés dans la ligne de commande, tous les fichiers jusqu’à l’option **-out** ou **-target:module** suivante sont utilisés pour créer le fichier .dll.</span><span class="sxs-lookup"><span data-stu-id="29f4a-109">When specified at the command line, all files up to the next **-out** or **-target:module** option are used to create the .dll file.</span></span>  
  
 <span data-ttu-id="29f4a-110">Lors de la création d’un fichier .dll, une méthode [Main](../../programming-guide/main-and-command-args/index.md) n’est pas obligatoire.</span><span class="sxs-lookup"><span data-stu-id="29f4a-110">When building a .dll file, a [Main](../../programming-guide/main-and-command-args/index.md) method is not required.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="29f4a-111">Pour définir cette option du compilateur dans l'environnement de développement Visual Studio</span><span class="sxs-lookup"><span data-stu-id="29f4a-111">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="29f4a-112">Ouvrez la page **Propriétés** du projet.</span><span class="sxs-lookup"><span data-stu-id="29f4a-112">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="29f4a-113">Cliquez sur la page de propriétés **Application**.</span><span class="sxs-lookup"><span data-stu-id="29f4a-113">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="29f4a-114">Modifiez la propriété **Type de sortie**.</span><span class="sxs-lookup"><span data-stu-id="29f4a-114">Modify the **Output type** property.</span></span>  
  
 <span data-ttu-id="29f4a-115">Pour plus d’informations sur la façon de définir cette option du compilateur par programmation, consultez <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="29f4a-115">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="29f4a-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="29f4a-116">Example</span></span>  
 <span data-ttu-id="29f4a-117">Compilez `in.cs`, en créant `in.dll` :</span><span class="sxs-lookup"><span data-stu-id="29f4a-117">Compile `in.cs`, creating `in.dll`:</span></span>  
  
```console  
csc -target:library in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="29f4a-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="29f4a-118">See also</span></span>

- [<span data-ttu-id="29f4a-119">-Target (options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="29f4a-119">-target (C# Compiler Options)</span></span>](./target-compiler-option.md)
- [<span data-ttu-id="29f4a-120">Options du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="29f4a-120">C# Compiler Options</span></span>](./index.md)
