---
description: '#endif - Référence C#'
title: '#endif - Référence C#'
ms.date: 07/20/2015
f1_keywords:
- '#endif'
helpviewer_keywords:
- '#endif directive [C#]'
ms.assetid: 6a5fca55-5aee-441f-86f6-1c99fbe9ec05
ms.openlocfilehash: 0ccc00ceab2aa67c77140e3ef09907ba260d7e9b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91168632"
---
# <a name="endif-c-reference"></a><span data-ttu-id="f7927-103">#endif (référence C#)</span><span class="sxs-lookup"><span data-stu-id="f7927-103">#endif (C# Reference)</span></span>

<span data-ttu-id="f7927-104">`#endif` spécifie la fin d’une directive conditionnelle, qui a commencé avec la directive [#if](./preprocessor-if.md).</span><span class="sxs-lookup"><span data-stu-id="f7927-104">`#endif` specifies the end of a conditional directive, which began with the [#if](./preprocessor-if.md) directive.</span></span> <span data-ttu-id="f7927-105">Par exemple,</span><span class="sxs-lookup"><span data-stu-id="f7927-105">For example,</span></span>  
  
```csharp
#define DEBUG  
// ...  
#if DEBUG  
    Console.WriteLine("Debug version");  
#endif  
```  
  
## <a name="remarks"></a><span data-ttu-id="f7927-106">Notes</span><span class="sxs-lookup"><span data-stu-id="f7927-106">Remarks</span></span>  

 <span data-ttu-id="f7927-107">Une directive conditionnelle commençant par une directive `#if` doit se terminer explicitement par une directive `#endif`.</span><span class="sxs-lookup"><span data-stu-id="f7927-107">A conditional directive, beginning with a `#if` directive, must explicitly be terminated with a `#endif` directive.</span></span> <span data-ttu-id="f7927-108">Consultez [#if](./preprocessor-if.md) pour obtenir un exemple d’utilisation de `#endif`.</span><span class="sxs-lookup"><span data-stu-id="f7927-108">See [#if](./preprocessor-if.md) for an example of how to use `#endif`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7927-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f7927-109">See also</span></span>

- [<span data-ttu-id="f7927-110">Référence C#</span><span class="sxs-lookup"><span data-stu-id="f7927-110">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="f7927-111">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="f7927-111">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="f7927-112">Directives de préprocesseur C#</span><span class="sxs-lookup"><span data-stu-id="f7927-112">C# Preprocessor Directives</span></span>](./index.md)
