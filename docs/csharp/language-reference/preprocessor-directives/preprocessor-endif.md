---
title: '#endif - Référence C#'
ms.date: 07/20/2015
f1_keywords:
- '#endif'
helpviewer_keywords:
- '#endif directive [C#]'
ms.assetid: 6a5fca55-5aee-441f-86f6-1c99fbe9ec05
ms.openlocfilehash: cc344a224e2308e843328b228dd5e2466d02069f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712544"
---
# <a name="endif-c-reference"></a><span data-ttu-id="9ba04-102">#endif (référence C#)</span><span class="sxs-lookup"><span data-stu-id="9ba04-102">#endif (C# Reference)</span></span>
<span data-ttu-id="9ba04-103">`#endif` spécifie la fin d’une directive conditionnelle, qui a commencé avec la directive [#if](./preprocessor-if.md).</span><span class="sxs-lookup"><span data-stu-id="9ba04-103">`#endif` specifies the end of a conditional directive, which began with the [#if](./preprocessor-if.md) directive.</span></span> <span data-ttu-id="9ba04-104">Par exemple,</span><span class="sxs-lookup"><span data-stu-id="9ba04-104">For example,</span></span>  
  
```csharp
#define DEBUG  
// ...  
#if DEBUG  
    Console.WriteLine("Debug version");  
#endif  
```  
  
## <a name="remarks"></a><span data-ttu-id="9ba04-105">Notes </span><span class="sxs-lookup"><span data-stu-id="9ba04-105">Remarks</span></span>  
 <span data-ttu-id="9ba04-106">Une directive conditionnelle commençant par une directive `#if` doit se terminer explicitement par une directive `#endif`.</span><span class="sxs-lookup"><span data-stu-id="9ba04-106">A conditional directive, beginning with a `#if` directive, must explicitly be terminated with a `#endif` directive.</span></span> <span data-ttu-id="9ba04-107">Consultez [#if](./preprocessor-if.md) pour obtenir un exemple d’utilisation de `#endif`.</span><span class="sxs-lookup"><span data-stu-id="9ba04-107">See [#if](./preprocessor-if.md) for an example of how to use `#endif`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ba04-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9ba04-108">See also</span></span>

- [<span data-ttu-id="9ba04-109">Référence C</span><span class="sxs-lookup"><span data-stu-id="9ba04-109">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="9ba04-110">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="9ba04-110">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="9ba04-111">Directives de préprocesseur de CMD</span><span class="sxs-lookup"><span data-stu-id="9ba04-111">C# Preprocessor Directives</span></span>](./index.md)
