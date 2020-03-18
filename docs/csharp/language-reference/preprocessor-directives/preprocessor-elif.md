---
title: '#elif - Référence C#'
ms.date: 07/20/2015
f1_keywords:
- '#elif'
helpviewer_keywords:
- '#elif directive [C#]'
ms.assetid: 731d78df-08e0-4d51-b8c8-f193c27de13f
ms.openlocfilehash: c78818f40b76414d289af6c704ff019b63befe37
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712570"
---
# <a name="elif-c-reference"></a><span data-ttu-id="fa67a-102">#elif (référence C#)</span><span class="sxs-lookup"><span data-stu-id="fa67a-102">#elif (C# Reference)</span></span>
<span data-ttu-id="fa67a-103">`#elif` vous permet de créer une directive conditionnelle composée.</span><span class="sxs-lookup"><span data-stu-id="fa67a-103">`#elif` lets you create a compound conditional directive.</span></span> <span data-ttu-id="fa67a-104">L’expression `#elif` est évaluée si ni l’expression [#if](./preprocessor-if.md) précédente ni une expression de directive `#elif` facultative précédente n’est évaluée à `true`.</span><span class="sxs-lookup"><span data-stu-id="fa67a-104">The `#elif` expression will be evaluated if neither the preceding [#if](./preprocessor-if.md) nor any preceding, optional, `#elif` directive expressions evaluate to `true`.</span></span> <span data-ttu-id="fa67a-105">Si une expression `#elif` est évaluée à `true`, le compilateur évalue l’ensemble du code situé entre `#elif` et la directive conditionnelle suivante.</span><span class="sxs-lookup"><span data-stu-id="fa67a-105">If a `#elif` expression evaluates to `true`, the compiler evaluates all the code between the `#elif` and the next conditional directive.</span></span> <span data-ttu-id="fa67a-106">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="fa67a-106">For example:</span></span>  
  
```csharp
#define VC7  
//...  
#if debug  
    Console.WriteLine("Debug build");  
#elif VC7  
    Console.WriteLine("Visual Studio 7");  
#endif  
```  
  
 <span data-ttu-id="fa67a-107">Vous pouvez utiliser les opérateurs `==` (égalité), `!=` (inégalité) `&&` (et) et `||` (ou) pour évaluer plusieurs symboles.</span><span class="sxs-lookup"><span data-stu-id="fa67a-107">You can use the operators `==` (equality), `!=` (inequality), `&&` (and), and `||` (or), to evaluate multiple symbols.</span></span> <span data-ttu-id="fa67a-108">Vous pouvez également regrouper des symboles et des opérateurs à l’aide de parenthèses.</span><span class="sxs-lookup"><span data-stu-id="fa67a-108">You can also group symbols and operators with parentheses.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fa67a-109">Notes </span><span class="sxs-lookup"><span data-stu-id="fa67a-109">Remarks</span></span>  
 <span data-ttu-id="fa67a-110">`#elif` revient à utiliser :</span><span class="sxs-lookup"><span data-stu-id="fa67a-110">`#elif` is equivalent to using:</span></span>  
  
```csharp
#else  
#if  
```  
  
 <span data-ttu-id="fa67a-111">`#elif` est plus simple à utiliser, car chaque expression `#if` a besoin d’une expression [#endif](./preprocessor-endif.md), alors qu’une expression `#elif` peut être utilisée sans expression `#endif` correspondante.</span><span class="sxs-lookup"><span data-stu-id="fa67a-111">Using `#elif` is simpler, because each `#if` requires a [#endif](./preprocessor-endif.md), whereas a `#elif` can be used without a matching `#endif`.</span></span>  
  
 <span data-ttu-id="fa67a-112">Consultez [#if](./preprocessor-if.md) pour obtenir un exemple d’utilisation de `#elif`.</span><span class="sxs-lookup"><span data-stu-id="fa67a-112">See [#if](./preprocessor-if.md) for an example of how to use `#elif`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa67a-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fa67a-113">See also</span></span>

- [<span data-ttu-id="fa67a-114">Référence C</span><span class="sxs-lookup"><span data-stu-id="fa67a-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="fa67a-115">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="fa67a-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="fa67a-116">Directives de préprocesseur de CMD</span><span class="sxs-lookup"><span data-stu-id="fa67a-116">C# Preprocessor Directives</span></span>](./index.md)
