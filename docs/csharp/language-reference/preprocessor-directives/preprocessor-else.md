---
description: '#else - Référence C#'
title: '#else - Référence C#'
ms.date: 07/20/2015
f1_keywords:
- '#else'
helpviewer_keywords:
- '#else directive [C#]'
ms.assetid: 6a347322-cfa2-4a86-98f8-ddfa2cb7d4db
ms.openlocfilehash: f0dc8c34672c3e9e5a2207211794fbc8099640c5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91168671"
---
# <a name="else-c-reference"></a><span data-ttu-id="a9d3c-103">#else (référence C#)</span><span class="sxs-lookup"><span data-stu-id="a9d3c-103">#else (C# Reference)</span></span>

<span data-ttu-id="a9d3c-104">`#else` vous permet de créer une directive conditionnelle composée de sorte que si aucune des expressions contenues dans les précédentes directives [#if](./preprocessor-if.md) ou [#elif](./preprocessor-elif.md) (facultatif) n’a la valeur `true`, le compilateur évalue l’ensemble du code entre `#else` et la directive `#endif` suivante.</span><span class="sxs-lookup"><span data-stu-id="a9d3c-104">`#else` lets you create a compound conditional directive, so that, if none of the expressions in the preceding [#if](./preprocessor-if.md) or (optional) [#elif](./preprocessor-elif.md) directives evaluate to `true`, the compiler will evaluate all code between `#else` and the subsequent `#endif`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a9d3c-105">Notes</span><span class="sxs-lookup"><span data-stu-id="a9d3c-105">Remarks</span></span>  

 <span data-ttu-id="a9d3c-106">[#endif](./preprocessor-endif.md) doit être la directive de préprocesseur suivante après `#else`.</span><span class="sxs-lookup"><span data-stu-id="a9d3c-106">[#endif](./preprocessor-endif.md) must be the next preprocessor directive after `#else`.</span></span> <span data-ttu-id="a9d3c-107">Consultez [#if](./preprocessor-if.md) pour obtenir un exemple d’utilisation de `#else`.</span><span class="sxs-lookup"><span data-stu-id="a9d3c-107">See [#if](./preprocessor-if.md) for an example of how to use `#else`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9d3c-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a9d3c-108">See also</span></span>

- [<span data-ttu-id="a9d3c-109">Référence C#</span><span class="sxs-lookup"><span data-stu-id="a9d3c-109">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="a9d3c-110">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="a9d3c-110">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="a9d3c-111">Directives de préprocesseur C#</span><span class="sxs-lookup"><span data-stu-id="a9d3c-111">C# Preprocessor Directives</span></span>](./index.md)
