---
title: '##region - Référence C#'
ms.date: 07/20/2015
f1_keywords:
- '#region'
helpviewer_keywords:
- '#region directive [C#]'
ms.assetid: 672c87d1-9771-4f64-ab3f-0ad3d4ffb2b4
ms.openlocfilehash: 66583d6e067b006b03130d8ff842b56bf57bcebc
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83802774"
---
# <a name="region-c-reference"></a><span data-ttu-id="c1ccb-102">#region (référence C#)</span><span class="sxs-lookup"><span data-stu-id="c1ccb-102">#region (C# Reference)</span></span>
<span data-ttu-id="c1ccb-103">`#region`vous permet de spécifier un bloc de code que vous pouvez développer ou réduire lors de l’utilisation de la fonctionnalité [mode plan](/visualstudio/ide/outlining) de l’éditeur de code.</span><span class="sxs-lookup"><span data-stu-id="c1ccb-103">`#region` lets you specify a block of code that you can expand or collapse when using the [outlining](/visualstudio/ide/outlining) feature of the code editor.</span></span> <span data-ttu-id="c1ccb-104">Dans les fichiers de code volumineux, il peut être pratique de réduire ou masquer une ou plusieurs régions pour vous concentrer sur la partie du fichier sur laquelle vous êtes en train de travailler.</span><span class="sxs-lookup"><span data-stu-id="c1ccb-104">In longer code files, it is convenient to be able to collapse or hide one or more regions so that you can focus on the part of the file that you are currently working on.</span></span> <span data-ttu-id="c1ccb-105">L’exemple suivant montre comment définir une région :</span><span class="sxs-lookup"><span data-stu-id="c1ccb-105">The following example shows how to define a region:</span></span>  
  
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
  
## <a name="remarks"></a><span data-ttu-id="c1ccb-106">Notes</span><span class="sxs-lookup"><span data-stu-id="c1ccb-106">Remarks</span></span>  
 <span data-ttu-id="c1ccb-107">Un bloc `#region` doit se terminer par une directive [#endregion](./preprocessor-endregion.md).</span><span class="sxs-lookup"><span data-stu-id="c1ccb-107">A `#region` block must be terminated with a [#endregion](./preprocessor-endregion.md) directive.</span></span>  
  
 <span data-ttu-id="c1ccb-108">Un bloc `#region` ne peut pas chevaucher un bloc [#if](./preprocessor-if.md).</span><span class="sxs-lookup"><span data-stu-id="c1ccb-108">A `#region` block cannot overlap with a [#if](./preprocessor-if.md) block.</span></span> <span data-ttu-id="c1ccb-109">Toutefois, un bloc `#region` peut être imbriqué dans un bloc `#if` et, inversement, un bloc `#if` peut être imbriqué dans un bloc `#region`.</span><span class="sxs-lookup"><span data-stu-id="c1ccb-109">However, a `#region` block can be nested in a `#if` block, and a `#if` block can be nested in a `#region` block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1ccb-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c1ccb-110">See also</span></span>

- [<span data-ttu-id="c1ccb-111">Référence C#</span><span class="sxs-lookup"><span data-stu-id="c1ccb-111">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="c1ccb-112">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="c1ccb-112">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="c1ccb-113">Directives de préprocesseur C#</span><span class="sxs-lookup"><span data-stu-id="c1ccb-113">C# Preprocessor Directives</span></span>](./index.md)
