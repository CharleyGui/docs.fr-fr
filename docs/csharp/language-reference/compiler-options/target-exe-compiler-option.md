---
description: -target:exe (Options du compilateur C#)
title: -target:exe (Options du compilateur C#)
ms.date: 07/20/2015
f1_keywords:
- /exe
helpviewer_keywords:
- target compiler options [C#], /target:exe
- /target compiler options [C#], /target:exe
- -target compiler options [C#], /target:exe
ms.assetid: bda5717d-1b91-4848-956b-fcf85c30e432
ms.openlocfilehash: ae1706f1ecdd396e24711070d19420faa6d34761
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "91193760"
---
# <a name="-targetexe-c-compiler-options"></a><span data-ttu-id="47ad0-103">-target:exe (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="47ad0-103">-target:exe (C# Compiler Options)</span></span>

<span data-ttu-id="47ad0-104">L’option **-target:exe** indique au compilateur de créer une application console exécutable (EXE).</span><span class="sxs-lookup"><span data-stu-id="47ad0-104">The **-target:exe** option causes the compiler to create an executable (EXE), console application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47ad0-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="47ad0-105">Syntax</span></span>  
  
```console  
-target:exe  
```  
  
## <a name="remarks"></a><span data-ttu-id="47ad0-106">Notes</span><span class="sxs-lookup"><span data-stu-id="47ad0-106">Remarks</span></span>  

 <span data-ttu-id="47ad0-107">L’option **-target:exe** est activée par défaut.</span><span class="sxs-lookup"><span data-stu-id="47ad0-107">The **-target:exe** option is in effect by default.</span></span> <span data-ttu-id="47ad0-108">Le fichier exécutable est créé avec l’extension .exe.</span><span class="sxs-lookup"><span data-stu-id="47ad0-108">The executable file will be created with the .exe extension.</span></span>  
  
 <span data-ttu-id="47ad0-109">Utilisez [-target:winexe](./target-winexe-compiler-option.md) pour créer un programme exécutable Windows.</span><span class="sxs-lookup"><span data-stu-id="47ad0-109">Use [-target:winexe](./target-winexe-compiler-option.md) to create a Windows program executable.</span></span>  
  
 <span data-ttu-id="47ad0-110">À moins que l’option [-out](./out-compiler-option.md) spécifie autre chose, le fichier de sortie prend le nom du fichier d’entrée qui contient la méthode [Main](../../programming-guide/main-and-command-args/index.md).</span><span class="sxs-lookup"><span data-stu-id="47ad0-110">Unless otherwise specified with the [-out](./out-compiler-option.md) option, the output file name takes the name of the input file that contains the [Main](../../programming-guide/main-and-command-args/index.md) method.</span></span>  
  
 <span data-ttu-id="47ad0-111">Quand ils sont spécifiés dans la ligne de commande, tous les fichiers jusqu’à l’option **-out** ou **-target:module** suivante sont utilisés pour créer le fichier .exe.</span><span class="sxs-lookup"><span data-stu-id="47ad0-111">When specified at the command line, all files up to the next **-out** or **-target:module** option are used to create the .exe file</span></span>  
  
 <span data-ttu-id="47ad0-112">Une seule et unique méthode **Main** est requise dans les fichiers de code source qui sont compilés dans un fichier .exe.</span><span class="sxs-lookup"><span data-stu-id="47ad0-112">One and only one **Main** method is required in the source code files that are compiled into an .exe file.</span></span> <span data-ttu-id="47ad0-113">L’option de compilateur [-main](./main-compiler-option.md) vous permet de spécifier la classe contenant la méthode **Main**, au cas où votre code possède plusieurs classes avec une méthode **Main**.</span><span class="sxs-lookup"><span data-stu-id="47ad0-113">The [-main](./main-compiler-option.md) compiler option lets you specify which class contains the **Main** method, in cases where your code has more than one class with a **Main** method.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="47ad0-114">Pour définir cette option du compilateur dans l'environnement de développement Visual Studio</span><span class="sxs-lookup"><span data-stu-id="47ad0-114">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="47ad0-115">Ouvrez la page **Propriétés** du projet.</span><span class="sxs-lookup"><span data-stu-id="47ad0-115">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="47ad0-116">Cliquez sur la page de propriétés **Application**.</span><span class="sxs-lookup"><span data-stu-id="47ad0-116">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="47ad0-117">Modifiez la propriété **Type de sortie**.</span><span class="sxs-lookup"><span data-stu-id="47ad0-117">Modify the **Output type** property.</span></span>  
  
 <span data-ttu-id="47ad0-118">Pour plus d’informations sur la façon de définir cette option du compilateur par programmation, consultez <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="47ad0-118">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="47ad0-119">Exemple</span><span class="sxs-lookup"><span data-stu-id="47ad0-119">Example</span></span>  

 <span data-ttu-id="47ad0-120">Chacune des lignes de commande suivantes compile `in.cs` et crée `in.exe` :</span><span class="sxs-lookup"><span data-stu-id="47ad0-120">Each of the following command lines will compile `in.cs`, creating `in.exe`:</span></span>  
  
```console  
csc -target:exe in.cs  
csc in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="47ad0-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="47ad0-121">See also</span></span>

- [<span data-ttu-id="47ad0-122">-Target (options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="47ad0-122">-target (C# Compiler Options)</span></span>](./target-compiler-option.md)
- [<span data-ttu-id="47ad0-123">Options du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="47ad0-123">C# Compiler Options</span></span>](./index.md)
