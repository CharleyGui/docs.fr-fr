---
title: '#elif - Référence C#'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#elif'
helpviewer_keywords:
- '#elif directive [C#]'
ms.assetid: 731d78df-08e0-4d51-b8c8-f193c27de13f
ms.openlocfilehash: b04db4bd23a459043efec59b8ebf9d322defbcf7
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69608585"
---
# <a name="elif-c-reference"></a><span data-ttu-id="b0df8-102">#elif (référence C#)</span><span class="sxs-lookup"><span data-stu-id="b0df8-102">#elif (C# Reference)</span></span>
<span data-ttu-id="b0df8-103">`#elif` vous permet de créer une directive conditionnelle composée.</span><span class="sxs-lookup"><span data-stu-id="b0df8-103">`#elif` lets you create a compound conditional directive.</span></span> <span data-ttu-id="b0df8-104">L’expression `#elif` est évaluée si ni l’expression [#if](./preprocessor-if.md) précédente ni une expression de directive `#elif` facultative précédente n’est évaluée à `true`.</span><span class="sxs-lookup"><span data-stu-id="b0df8-104">The `#elif` expression will be evaluated if neither the preceding [#if](./preprocessor-if.md) nor any preceding, optional, `#elif` directive expressions evaluate to `true`.</span></span> <span data-ttu-id="b0df8-105">Si une expression `#elif` est évaluée à `true`, le compilateur évalue l’ensemble du code situé entre `#elif` et la directive conditionnelle suivante.</span><span class="sxs-lookup"><span data-stu-id="b0df8-105">If a `#elif` expression evaluates to `true`, the compiler evaluates all the code between the `#elif` and the next conditional directive.</span></span> <span data-ttu-id="b0df8-106">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="b0df8-106">For example:</span></span>  
  
```csharp
#define VC7  
//...  
#if debug  
    Console.WriteLine("Debug build");  
#elif VC7  
    Console.WriteLine("Visual Studio 7");  
#endif  
```  
  
 <span data-ttu-id="b0df8-107">Vous pouvez utiliser les opérateurs `==` (égalité), `!=` (inégalité) `&&` (et) et `||` (ou) pour évaluer plusieurs symboles.</span><span class="sxs-lookup"><span data-stu-id="b0df8-107">You can use the operators `==` (equality), `!=` (inequality), `&&` (and), and `||` (or), to evaluate multiple symbols.</span></span> <span data-ttu-id="b0df8-108">Vous pouvez également regrouper des symboles et des opérateurs à l’aide de parenthèses.</span><span class="sxs-lookup"><span data-stu-id="b0df8-108">You can also group symbols and operators with parentheses.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b0df8-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="b0df8-109">Remarks</span></span>  
 <span data-ttu-id="b0df8-110">`#elif` revient à utiliser :</span><span class="sxs-lookup"><span data-stu-id="b0df8-110">`#elif` is equivalent to using:</span></span>  
  
```csharp
#else  
#if  
```  
  
 <span data-ttu-id="b0df8-111">`#elif` est plus simple à utiliser, car chaque expression `#if` a besoin d’une expression [#endif](./preprocessor-endif.md), alors qu’une expression `#elif` peut être utilisée sans expression `#endif` correspondante.</span><span class="sxs-lookup"><span data-stu-id="b0df8-111">Using `#elif` is simpler, because each `#if` requires a [#endif](./preprocessor-endif.md), whereas a `#elif` can be used without a matching `#endif`.</span></span>  
  
 <span data-ttu-id="b0df8-112">Consultez [#if](./preprocessor-if.md) pour obtenir un exemple d’utilisation de `#elif`.</span><span class="sxs-lookup"><span data-stu-id="b0df8-112">See [#if](./preprocessor-if.md) for an example of how to use `#elif`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0df8-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b0df8-113">See also</span></span>

- [<span data-ttu-id="b0df8-114">Référence C#</span><span class="sxs-lookup"><span data-stu-id="b0df8-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="b0df8-115">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="b0df8-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="b0df8-116">Directives de préprocesseur C#</span><span class="sxs-lookup"><span data-stu-id="b0df8-116">C# Preprocessor Directives</span></span>](./index.md)
