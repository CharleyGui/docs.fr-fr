---
title: -reference
ms.date: 03/13/2018
helpviewer_keywords:
- /reference compiler option [Visual Basic]
- r compiler option [Visual Basic]
- -reference compiler option [Visual Basic]
- /r compiler option [Visual Basic]
- reference compiler option [Visual Basic]
- -r compiler option [Visual Basic]
ms.assetid: 66bdfced-bbf6-43d1-a554-bc0990315737
ms.openlocfilehash: 8b57affa05c77d8ed20bfead7de767a8dd994241
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348584"
---
# <a name="-reference-visual-basic"></a><span data-ttu-id="6c4a7-102">-reference (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6c4a7-102">-reference (Visual Basic)</span></span>
<span data-ttu-id="6c4a7-103">Causes the compiler to make type information in the specified assemblies available to the project you are currently compiling.</span><span class="sxs-lookup"><span data-stu-id="6c4a7-103">Causes the compiler to make type information in the specified assemblies available to the project you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c4a7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6c4a7-104">Syntax</span></span>  
  
```console  
-reference:fileList  
```

<span data-ttu-id="6c4a7-105">or</span><span class="sxs-lookup"><span data-stu-id="6c4a7-105">or</span></span>

```console
-r:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="6c4a7-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="6c4a7-106">Arguments</span></span>  
  
|<span data-ttu-id="6c4a7-107">Terme</span><span class="sxs-lookup"><span data-stu-id="6c4a7-107">Term</span></span>|<span data-ttu-id="6c4a7-108">Définition</span><span class="sxs-lookup"><span data-stu-id="6c4a7-108">Definition</span></span>|  
|---|---|  
|`fileList`|<span data-ttu-id="6c4a7-109">Requis.</span><span class="sxs-lookup"><span data-stu-id="6c4a7-109">Required.</span></span> <span data-ttu-id="6c4a7-110">Liste délimitée par des virgules des noms de fichiers d’assembly.</span><span class="sxs-lookup"><span data-stu-id="6c4a7-110">Comma-delimited list of assembly file names.</span></span> <span data-ttu-id="6c4a7-111">Si le nom de fichier contient un espace, placez-le entre des guillemets.</span><span class="sxs-lookup"><span data-stu-id="6c4a7-111">If the file name contains a space, enclose the name in quotation marks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6c4a7-112">Notes</span><span class="sxs-lookup"><span data-stu-id="6c4a7-112">Remarks</span></span>  
 <span data-ttu-id="6c4a7-113">The file(s) you import must contain assembly metadata.</span><span class="sxs-lookup"><span data-stu-id="6c4a7-113">The file(s) you import must contain assembly metadata.</span></span> <span data-ttu-id="6c4a7-114">Only public types are visible outside the assembly.</span><span class="sxs-lookup"><span data-stu-id="6c4a7-114">Only public types are visible outside the assembly.</span></span> <span data-ttu-id="6c4a7-115">The [-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md) option imports metadata from a module.</span><span class="sxs-lookup"><span data-stu-id="6c4a7-115">The [-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md) option imports metadata from a module.</span></span>  
  
 <span data-ttu-id="6c4a7-116">If you reference an assembly (Assembly A) which itself references another assembly (Assembly B), you need to reference Assembly B if:</span><span class="sxs-lookup"><span data-stu-id="6c4a7-116">If you reference an assembly (Assembly A) which itself references another assembly (Assembly B), you need to reference Assembly B if:</span></span>  
  
- <span data-ttu-id="6c4a7-117">Un type de l’Assembly A hérite d’un type ou implémente une interface de l’Assembly B.</span><span class="sxs-lookup"><span data-stu-id="6c4a7-117">A type from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
- <span data-ttu-id="6c4a7-118">Un champ, une propriété, un événement ou une méthode qui a un type de retour ou un type de paramètre de l’Assembly B est appelé.</span><span class="sxs-lookup"><span data-stu-id="6c4a7-118">A field, property, event, or method that has a return type or parameter type from Assembly B is invoked.</span></span>  
  
 <span data-ttu-id="6c4a7-119">Use [-libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) to specify the directory in which one or more of your assembly references is located.</span><span class="sxs-lookup"><span data-stu-id="6c4a7-119">Use [-libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) to specify the directory in which one or more of your assembly references is located.</span></span>  
  
 <span data-ttu-id="6c4a7-120">For the compiler to recognize a type in an assembly (not a module), it must be forced to resolve the type.</span><span class="sxs-lookup"><span data-stu-id="6c4a7-120">For the compiler to recognize a type in an assembly (not a module), it must be forced to resolve the type.</span></span> <span data-ttu-id="6c4a7-121">One example of how you can do this is to define an instance of the type.</span><span class="sxs-lookup"><span data-stu-id="6c4a7-121">One example of how you can do this is to define an instance of the type.</span></span> <span data-ttu-id="6c4a7-122">Other ways are available to resolve type names in an assembly for the compiler.</span><span class="sxs-lookup"><span data-stu-id="6c4a7-122">Other ways are available to resolve type names in an assembly for the compiler.</span></span> <span data-ttu-id="6c4a7-123">For example, if you inherit from a type in an assembly, the type name then becomes known to the compiler.</span><span class="sxs-lookup"><span data-stu-id="6c4a7-123">For example, if you inherit from a type in an assembly, the type name then becomes known to the compiler.</span></span>  
  
 <span data-ttu-id="6c4a7-124">The Vbc.rsp response file, which references commonly used .NET Framework assemblies, is used by default.</span><span class="sxs-lookup"><span data-stu-id="6c4a7-124">The Vbc.rsp response file, which references commonly used .NET Framework assemblies, is used by default.</span></span> <span data-ttu-id="6c4a7-125">Use `-noconfig` if you do not want the compiler to use Vbc.rsp.</span><span class="sxs-lookup"><span data-stu-id="6c4a7-125">Use `-noconfig` if you do not want the compiler to use Vbc.rsp.</span></span>  
  
 <span data-ttu-id="6c4a7-126">La forme abrégée de `-reference` est `/r`.</span><span class="sxs-lookup"><span data-stu-id="6c4a7-126">The short form of `-reference` is `/r`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6c4a7-127">Exemple</span><span class="sxs-lookup"><span data-stu-id="6c4a7-127">Example</span></span>  
 <span data-ttu-id="6c4a7-128">The following command compiles source file `Input.vb` and reference assemblies from `Metad1.dll` and `Metad2.dll` to produce `Out.exe`.</span><span class="sxs-lookup"><span data-stu-id="6c4a7-128">The following command compiles source file `Input.vb` and reference assemblies from `Metad1.dll` and `Metad2.dll` to produce `Out.exe`.</span></span>  
  
```console
vbc -reference:metad1.dll,metad2.dll -out:out.exe input.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="6c4a7-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6c4a7-129">See also</span></span>

- [<span data-ttu-id="6c4a7-130">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6c4a7-130">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="6c4a7-131">-noconfig</span><span class="sxs-lookup"><span data-stu-id="6c4a7-131">-noconfig</span></span>](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [<span data-ttu-id="6c4a7-132">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6c4a7-132">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="6c4a7-133">Public</span><span class="sxs-lookup"><span data-stu-id="6c4a7-133">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)
- [<span data-ttu-id="6c4a7-134">Exemples de lignes de commande de compilation</span><span class="sxs-lookup"><span data-stu-id="6c4a7-134">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
