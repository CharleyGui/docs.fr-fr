---
description: -target:module (Options du compilateur C#)
title: -target:module (Options du compilateur C#)
ms.date: 07/20/2015
f1_keywords:
- /target:module
helpviewer_keywords:
- -target compiler options [C#], /target:module
- target compiler options [C#], /target:module
- /target compiler options [C#], /target:module
ms.assetid: 9af1e4fa-c749-44e7-ae58-90a3d05d4e72
ms.openlocfilehash: 2074e170ab177c39fdf3954fa93ae4b666bf853d
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2020
ms.locfileid: "89466051"
---
# <a name="-targetmodule-c-compiler-options"></a><span data-ttu-id="8a6db-103">-target:module (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="8a6db-103">-target:module (C# Compiler Options)</span></span>
<span data-ttu-id="8a6db-104">Cette option empêche le compilateur de générer un manifeste d’assembly.</span><span class="sxs-lookup"><span data-stu-id="8a6db-104">This option causes the compiler to not generate an assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a6db-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8a6db-105">Syntax</span></span>  
  
```console  
-target:module  
```  
  
## <a name="remarks"></a><span data-ttu-id="8a6db-106">Notes</span><span class="sxs-lookup"><span data-stu-id="8a6db-106">Remarks</span></span>  
 <span data-ttu-id="8a6db-107">Par défaut, le fichier de sortie créé en effectuant une compilation avec cette option porte l’extension .netmodule.</span><span class="sxs-lookup"><span data-stu-id="8a6db-107">By default, the output file created by compiling with this option will have an extension of .netmodule.</span></span>  
  
 <span data-ttu-id="8a6db-108">Un fichier qui n’a pas de manifeste d’assembly ne peut pas être chargé par le Runtime .NET.</span><span class="sxs-lookup"><span data-stu-id="8a6db-108">A file that does not have an assembly manifest cannot be loaded by the .NET runtime.</span></span> <span data-ttu-id="8a6db-109">Cependant, un tel fichier peut être incorporé dans le manifeste d’un assembly au moyen de [-addmodule](./addmodule-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="8a6db-109">However, such a file can be incorporated into the assembly manifest of an assembly by means of [-addmodule](./addmodule-compiler-option.md).</span></span>  
  
 <span data-ttu-id="8a6db-110">Si plusieurs modules sont créés dans une seule compilation, les types [internal](../keywords/internal.md) d’un module sont accessibles à d’autres modules dans la compilation.</span><span class="sxs-lookup"><span data-stu-id="8a6db-110">If more than one module is created in a single compilation, [internal](../keywords/internal.md) types in one module will be available to other modules in the compilation.</span></span> <span data-ttu-id="8a6db-111">Quand le code d’un module référence des types `internal` dans un autre module, les deux modules doivent être incorporés dans un manifeste d’assembly au moyen de **-addmodule**.</span><span class="sxs-lookup"><span data-stu-id="8a6db-111">When code in one module references `internal` types in another module, then both modules must be incorporated into an assembly manifest, by means of **-addmodule**.</span></span>  
  
 <span data-ttu-id="8a6db-112">La création d’un module n’est pas prise en charge dans l’environnement de développement Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8a6db-112">Creating a module is not supported in the Visual Studio development environment.</span></span>  
  
 <span data-ttu-id="8a6db-113">Pour plus d’informations sur la façon de définir cette option du compilateur par programmation, consultez <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="8a6db-113">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8a6db-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="8a6db-114">Example</span></span>  
 <span data-ttu-id="8a6db-115">Compilez `in.cs`, en créant `in.netmodule` :</span><span class="sxs-lookup"><span data-stu-id="8a6db-115">Compile `in.cs`, creating `in.netmodule`:</span></span>  
  
```console  
csc -target:module in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="8a6db-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8a6db-116">See also</span></span>

- [<span data-ttu-id="8a6db-117">-Target (options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="8a6db-117">-target (C# Compiler Options)</span></span>](./target-compiler-option.md)
- [<span data-ttu-id="8a6db-118">Options du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="8a6db-118">C# Compiler Options</span></span>](./index.md)
