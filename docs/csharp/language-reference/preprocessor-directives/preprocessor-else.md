---
title: '#else - Référence C#'
ms.date: 07/20/2015
f1_keywords:
- '#else'
helpviewer_keywords:
- '#else directive [C#]'
ms.assetid: 6a347322-cfa2-4a86-98f8-ddfa2cb7d4db
ms.openlocfilehash: 967ef38687b739ef3bea3f8923ab26bba0b6cea9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712557"
---
# <a name="else-c-reference"></a><span data-ttu-id="daa34-102">#else (référence C#)</span><span class="sxs-lookup"><span data-stu-id="daa34-102">#else (C# Reference)</span></span>
<span data-ttu-id="daa34-103">`#else` vous permet de créer une directive conditionnelle composée de sorte que si aucune des expressions contenues dans les précédentes directives [#if](./preprocessor-if.md) ou [#elif](./preprocessor-elif.md) (facultatif) n’a la valeur `true`, le compilateur évalue l’ensemble du code entre `#else` et la directive `#endif` suivante.</span><span class="sxs-lookup"><span data-stu-id="daa34-103">`#else` lets you create a compound conditional directive, so that, if none of the expressions in the preceding [#if](./preprocessor-if.md) or (optional) [#elif](./preprocessor-elif.md) directives evaluate to `true`, the compiler will evaluate all code between `#else` and the subsequent `#endif`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="daa34-104">Notes </span><span class="sxs-lookup"><span data-stu-id="daa34-104">Remarks</span></span>  
 <span data-ttu-id="daa34-105">[#endif](./preprocessor-endif.md) doit être la directive de préprocesseur suivante après `#else`.</span><span class="sxs-lookup"><span data-stu-id="daa34-105">[#endif](./preprocessor-endif.md) must be the next preprocessor directive after `#else`.</span></span> <span data-ttu-id="daa34-106">Consultez [#if](./preprocessor-if.md) pour obtenir un exemple d’utilisation de `#else`.</span><span class="sxs-lookup"><span data-stu-id="daa34-106">See [#if](./preprocessor-if.md) for an example of how to use `#else`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="daa34-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="daa34-107">See also</span></span>

- [<span data-ttu-id="daa34-108">Référence C</span><span class="sxs-lookup"><span data-stu-id="daa34-108">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="daa34-109">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="daa34-109">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="daa34-110">Directives de préprocesseur de CMD</span><span class="sxs-lookup"><span data-stu-id="daa34-110">C# Preprocessor Directives</span></span>](./index.md)
