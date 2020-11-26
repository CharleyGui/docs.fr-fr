---
description: -target:winexe (Options du compilateur C#)
title: -target:winexe (Options du compilateur C#)
ms.date: 07/20/2015
f1_keywords:
- /target:winexe
helpviewer_keywords:
- /target compiler options [C#], /target:winexe
- -target compiler options [C#], /target:winexe
- target compiler options [C#], /target:winexe
ms.assetid: b5a0619c-8caa-46a5-a743-1cf68408ad7a
ms.openlocfilehash: 6e14a2aac427c7adfd69f66eaf624816b75f6ea2
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "91168931"
---
# <a name="-targetwinexe-c-compiler-options"></a><span data-ttu-id="59942-103">-target:winexe (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="59942-103">-target:winexe (C# Compiler Options)</span></span>

<span data-ttu-id="59942-104">L’option **-target : winexe** force le compilateur à créer un programme Windows exécutable (exe).</span><span class="sxs-lookup"><span data-stu-id="59942-104">The **-target:winexe** option causes the compiler to create an executable (EXE), Windows program.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59942-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="59942-105">Syntax</span></span>  
  
```console  
-target:winexe  
```  
  
## <a name="remarks"></a><span data-ttu-id="59942-106">Notes</span><span class="sxs-lookup"><span data-stu-id="59942-106">Remarks</span></span>  

 <span data-ttu-id="59942-107">Le fichier exécutable est créé avec l’extension .exe.</span><span class="sxs-lookup"><span data-stu-id="59942-107">The executable file will be created with the .exe extension.</span></span> <span data-ttu-id="59942-108">Un programme Windows est un programme qui fournit une interface utilisateur à partir de la bibliothèque .NET ou avec les API Windows.</span><span class="sxs-lookup"><span data-stu-id="59942-108">A Windows program is one that provides a user interface from either the .NET library or with the Windows APIs.</span></span>  
  
 <span data-ttu-id="59942-109">Utilisez [-target:exe](./target-exe-compiler-option.md) pour créer une application console.</span><span class="sxs-lookup"><span data-stu-id="59942-109">Use [-target:exe](./target-exe-compiler-option.md) to create a console application.</span></span>  
  
 <span data-ttu-id="59942-110">À moins que l’option [-out](./out-compiler-option.md) spécifie autre chose, le fichier de sortie prend le nom du fichier d’entrée qui contient la méthode [Main](../../programming-guide/main-and-command-args/index.md).</span><span class="sxs-lookup"><span data-stu-id="59942-110">Unless otherwise specified with the [-out](./out-compiler-option.md) option, the output file name takes the name of the input file that contains the [Main](../../programming-guide/main-and-command-args/index.md) method.</span></span>  
  
 <span data-ttu-id="59942-111">Quand ils sont spécifiés dans la ligne de commande, tous les fichiers jusqu’à l’option **-out** ou [-target](./target-compiler-option.md) suivante sont utilisés pour créer le programme Windows.</span><span class="sxs-lookup"><span data-stu-id="59942-111">When specified at the command line, all files until the next **-out** or [-target](./target-compiler-option.md) option are used to create the Windows program.</span></span>  
  
 <span data-ttu-id="59942-112">Une seule et unique méthode **Main** est requise dans les fichiers de code source qui sont compilés dans un fichier .exe.</span><span class="sxs-lookup"><span data-stu-id="59942-112">One and only one **Main** method is required in the source code files that are compiled into an .exe file.</span></span> <span data-ttu-id="59942-113">L’option [-main](./main-compiler-option.md) vous permet de spécifier la classe contenant la méthode **Main**, au cas où votre code possède plusieurs classes avec une méthode **Main**.</span><span class="sxs-lookup"><span data-stu-id="59942-113">The [-main](./main-compiler-option.md) option lets you specify which class contains the **Main** method, in cases where your code has more than one class with a **Main** method.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="59942-114">Pour définir cette option du compilateur dans l'environnement de développement Visual Studio</span><span class="sxs-lookup"><span data-stu-id="59942-114">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="59942-115">Ouvrez la page **Propriétés** du projet.</span><span class="sxs-lookup"><span data-stu-id="59942-115">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="59942-116">Cliquez sur la page de propriétés **Application**.</span><span class="sxs-lookup"><span data-stu-id="59942-116">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="59942-117">Modifiez la propriété **Type de sortie**.</span><span class="sxs-lookup"><span data-stu-id="59942-117">Modify the **Output type** property.</span></span>  
  
 <span data-ttu-id="59942-118">Pour plus d’informations sur la façon de définir cette option du compilateur par programmation, consultez <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="59942-118">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="59942-119">Exemple</span><span class="sxs-lookup"><span data-stu-id="59942-119">Example</span></span>  

 <span data-ttu-id="59942-120">Compilez `in.cs` en un programme Windows :</span><span class="sxs-lookup"><span data-stu-id="59942-120">Compile `in.cs` into a Windows program:</span></span>  
  
```console  
csc -target:winexe in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="59942-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="59942-121">See also</span></span>

- [<span data-ttu-id="59942-122">-Target (options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="59942-122">-target (C# Compiler Options)</span></span>](./target-compiler-option.md)
- [<span data-ttu-id="59942-123">Options du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="59942-123">C# Compiler Options</span></span>](./index.md)
