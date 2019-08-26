---
title: '#else - Référence C#'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#else'
helpviewer_keywords:
- '#else directive [C#]'
ms.assetid: 6a347322-cfa2-4a86-98f8-ddfa2cb7d4db
ms.openlocfilehash: d6a514f71b3526b2ffe347cdd971b81907fb0aad
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69605716"
---
# <a name="else-c-reference"></a><span data-ttu-id="1b901-102">#else (référence C#)</span><span class="sxs-lookup"><span data-stu-id="1b901-102">#else (C# Reference)</span></span>
<span data-ttu-id="1b901-103">`#else` vous permet de créer une directive conditionnelle composée de sorte que si aucune des expressions contenues dans les précédentes directives [#if](./preprocessor-if.md) ou [#elif](./preprocessor-elif.md) (facultatif) n’a la valeur `true`, le compilateur évalue l’ensemble du code entre `#else` et la directive `#endif` suivante.</span><span class="sxs-lookup"><span data-stu-id="1b901-103">`#else` lets you create a compound conditional directive, so that, if none of the expressions in the preceding [#if](./preprocessor-if.md) or (optional) [#elif](./preprocessor-elif.md) directives evaluate to `true`, the compiler will evaluate all code between `#else` and the subsequent `#endif`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1b901-104">Remarques</span><span class="sxs-lookup"><span data-stu-id="1b901-104">Remarks</span></span>  
 <span data-ttu-id="1b901-105">[#endif](./preprocessor-endif.md) doit être la directive de préprocesseur suivante après `#else`.</span><span class="sxs-lookup"><span data-stu-id="1b901-105">[#endif](./preprocessor-endif.md) must be the next preprocessor directive after `#else`.</span></span> <span data-ttu-id="1b901-106">Consultez [#if](./preprocessor-if.md) pour obtenir un exemple d’utilisation de `#else`.</span><span class="sxs-lookup"><span data-stu-id="1b901-106">See [#if](./preprocessor-if.md) for an example of how to use `#else`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b901-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1b901-107">See also</span></span>

- [<span data-ttu-id="1b901-108">Référence C#</span><span class="sxs-lookup"><span data-stu-id="1b901-108">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="1b901-109">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="1b901-109">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="1b901-110">Directives de préprocesseur C#</span><span class="sxs-lookup"><span data-stu-id="1b901-110">C# Preprocessor Directives</span></span>](./index.md)
