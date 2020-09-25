---
description: '##region - Référence C#'
title: '##region - Référence C#'
ms.date: 07/20/2015
f1_keywords:
- '#region'
helpviewer_keywords:
- '#region directive [C#]'
ms.assetid: 672c87d1-9771-4f64-ab3f-0ad3d4ffb2b4
ms.openlocfilehash: dcb806a213bea9d7c782eeddc712f1eb76257e80
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91186404"
---
# <a name="region-c-reference"></a><span data-ttu-id="dee11-103">#region (référence C#)</span><span class="sxs-lookup"><span data-stu-id="dee11-103">#region (C# Reference)</span></span>

<span data-ttu-id="dee11-104">`#region` vous permet de spécifier un bloc de code que vous pouvez développer ou réduire lors de l’utilisation de la fonctionnalité [mode plan](/visualstudio/ide/outlining) de l’éditeur de code.</span><span class="sxs-lookup"><span data-stu-id="dee11-104">`#region` lets you specify a block of code that you can expand or collapse when using the [outlining](/visualstudio/ide/outlining) feature of the code editor.</span></span> <span data-ttu-id="dee11-105">Dans les fichiers de code volumineux, il peut être pratique de réduire ou masquer une ou plusieurs régions pour vous concentrer sur la partie du fichier sur laquelle vous êtes en train de travailler.</span><span class="sxs-lookup"><span data-stu-id="dee11-105">In longer code files, it is convenient to be able to collapse or hide one or more regions so that you can focus on the part of the file that you are currently working on.</span></span> <span data-ttu-id="dee11-106">L’exemple suivant montre comment définir une région :</span><span class="sxs-lookup"><span data-stu-id="dee11-106">The following example shows how to define a region:</span></span>  
  
```csharp
#region MyClass definition  
public class MyClass
{  
    static void Main()
    {  
    }  
}  
#endregion  
```  
  
## <a name="remarks"></a><span data-ttu-id="dee11-107">Notes</span><span class="sxs-lookup"><span data-stu-id="dee11-107">Remarks</span></span>  

 <span data-ttu-id="dee11-108">Un bloc `#region` doit se terminer par une directive [#endregion](./preprocessor-endregion.md).</span><span class="sxs-lookup"><span data-stu-id="dee11-108">A `#region` block must be terminated with a [#endregion](./preprocessor-endregion.md) directive.</span></span>  
  
 <span data-ttu-id="dee11-109">Un bloc `#region` ne peut pas chevaucher un bloc [#if](./preprocessor-if.md).</span><span class="sxs-lookup"><span data-stu-id="dee11-109">A `#region` block cannot overlap with a [#if](./preprocessor-if.md) block.</span></span> <span data-ttu-id="dee11-110">Toutefois, un bloc `#region` peut être imbriqué dans un bloc `#if` et, inversement, un bloc `#if` peut être imbriqué dans un bloc `#region`.</span><span class="sxs-lookup"><span data-stu-id="dee11-110">However, a `#region` block can be nested in a `#if` block, and a `#if` block can be nested in a `#region` block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dee11-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dee11-111">See also</span></span>

- [<span data-ttu-id="dee11-112">Référence C#</span><span class="sxs-lookup"><span data-stu-id="dee11-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="dee11-113">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="dee11-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="dee11-114">Directives de préprocesseur C#</span><span class="sxs-lookup"><span data-stu-id="dee11-114">C# Preprocessor Directives</span></span>](./index.md)
