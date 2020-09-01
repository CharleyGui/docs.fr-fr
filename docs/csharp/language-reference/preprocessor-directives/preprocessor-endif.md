---
description: '#endif - Référence C#'
title: '#endif - Référence C#'
ms.date: 07/20/2015
f1_keywords:
- '#endif'
helpviewer_keywords:
- '#endif directive [C#]'
ms.assetid: 6a5fca55-5aee-441f-86f6-1c99fbe9ec05
ms.openlocfilehash: 8068a6e437145178fd5c88763c86692a8700c349
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89138161"
---
# <a name="endif-c-reference"></a><span data-ttu-id="00991-103">#endif (référence C#)</span><span class="sxs-lookup"><span data-stu-id="00991-103">#endif (C# Reference)</span></span>
<span data-ttu-id="00991-104">`#endif` spécifie la fin d’une directive conditionnelle, qui a commencé avec la directive [#if](./preprocessor-if.md).</span><span class="sxs-lookup"><span data-stu-id="00991-104">`#endif` specifies the end of a conditional directive, which began with the [#if](./preprocessor-if.md) directive.</span></span> <span data-ttu-id="00991-105">Par exemple,</span><span class="sxs-lookup"><span data-stu-id="00991-105">For example,</span></span>  
  
```csharp
#define DEBUG  
// ...  
#if DEBUG  
    Console.WriteLine("Debug version");  
#endif  
```  
  
## <a name="remarks"></a><span data-ttu-id="00991-106">Remarques</span><span class="sxs-lookup"><span data-stu-id="00991-106">Remarks</span></span>  
 <span data-ttu-id="00991-107">Une directive conditionnelle commençant par une directive `#if` doit se terminer explicitement par une directive `#endif`.</span><span class="sxs-lookup"><span data-stu-id="00991-107">A conditional directive, beginning with a `#if` directive, must explicitly be terminated with a `#endif` directive.</span></span> <span data-ttu-id="00991-108">Consultez [#if](./preprocessor-if.md) pour obtenir un exemple d’utilisation de `#endif`.</span><span class="sxs-lookup"><span data-stu-id="00991-108">See [#if](./preprocessor-if.md) for an example of how to use `#endif`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00991-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="00991-109">See also</span></span>

- [<span data-ttu-id="00991-110">Référence C#</span><span class="sxs-lookup"><span data-stu-id="00991-110">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="00991-111">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="00991-111">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="00991-112">Directives de préprocesseur C#</span><span class="sxs-lookup"><span data-stu-id="00991-112">C# Preprocessor Directives</span></span>](./index.md)
