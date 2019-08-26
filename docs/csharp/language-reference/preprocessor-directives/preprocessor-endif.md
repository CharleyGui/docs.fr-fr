---
title: '#endif - Référence C#'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#endif'
helpviewer_keywords:
- '#endif directive [C#]'
ms.assetid: 6a5fca55-5aee-441f-86f6-1c99fbe9ec05
ms.openlocfilehash: 74205c836b4eeb2d8b17b907bb13708f3225df08
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69608568"
---
# <a name="endif-c-reference"></a><span data-ttu-id="c69cc-102">#endif (référence C#)</span><span class="sxs-lookup"><span data-stu-id="c69cc-102">#endif (C# Reference)</span></span>
<span data-ttu-id="c69cc-103">`#endif` spécifie la fin d’une directive conditionnelle, qui a commencé avec la directive [#if](./preprocessor-if.md).</span><span class="sxs-lookup"><span data-stu-id="c69cc-103">`#endif` specifies the end of a conditional directive, which began with the [#if](./preprocessor-if.md) directive.</span></span> <span data-ttu-id="c69cc-104">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="c69cc-104">For example,</span></span>  
  
```csharp
#define DEBUG  
// ...  
#if DEBUG  
    Console.WriteLine("Debug version");  
#endif  
```  
  
## <a name="remarks"></a><span data-ttu-id="c69cc-105">Remarques</span><span class="sxs-lookup"><span data-stu-id="c69cc-105">Remarks</span></span>  
 <span data-ttu-id="c69cc-106">Une directive conditionnelle commençant par une directive `#if` doit se terminer explicitement par une directive `#endif`.</span><span class="sxs-lookup"><span data-stu-id="c69cc-106">A conditional directive, beginning with a `#if` directive, must explicitly be terminated with a `#endif` directive.</span></span> <span data-ttu-id="c69cc-107">Consultez [#if](./preprocessor-if.md) pour obtenir un exemple d’utilisation de `#endif`.</span><span class="sxs-lookup"><span data-stu-id="c69cc-107">See [#if](./preprocessor-if.md) for an example of how to use `#endif`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c69cc-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c69cc-108">See also</span></span>

- [<span data-ttu-id="c69cc-109">Référence C#</span><span class="sxs-lookup"><span data-stu-id="c69cc-109">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="c69cc-110">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="c69cc-110">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="c69cc-111">Directives de préprocesseur C#</span><span class="sxs-lookup"><span data-stu-id="c69cc-111">C# Preprocessor Directives</span></span>](./index.md)
