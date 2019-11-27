---
title: 'Boucles : expression for...to'
description: Voir comment le F# ... to expression est utilisé pour effectuer une itération dans une boucle sur une plage de valeurs d’une variable de boucle.
ms.date: 05/16/2016
ms.openlocfilehash: 882b6e48dd09efcb57f7ef2f419e68a6c43393a5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283901"
---
# <a name="loops-forto-expression"></a><span data-ttu-id="9670a-103">Boucles : expression for...to</span><span class="sxs-lookup"><span data-stu-id="9670a-103">Loops: for...to Expression</span></span>

<span data-ttu-id="9670a-104">L’expression `for...to` est utilisée pour effectuer une itération dans une boucle sur une plage de valeurs d’une variable de boucle.</span><span class="sxs-lookup"><span data-stu-id="9670a-104">The `for...to` expression is used to iterate in a loop over a range of values of a loop variable.</span></span>

## <a name="syntax"></a><span data-ttu-id="9670a-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9670a-105">Syntax</span></span>

```fsharp
for identifier = start [ to | downto ] finish do
    body-expression
```

## <a name="remarks"></a><span data-ttu-id="9670a-106">Notes</span><span class="sxs-lookup"><span data-stu-id="9670a-106">Remarks</span></span>

<span data-ttu-id="9670a-107">Le type de l’identificateur est déduit à partir du type des expressions de *début* et de *fin* .</span><span class="sxs-lookup"><span data-stu-id="9670a-107">The type of the identifier is inferred from the type of the *start* and *finish* expressions.</span></span> <span data-ttu-id="9670a-108">Les types pour ces expressions doivent être des entiers 32 bits.</span><span class="sxs-lookup"><span data-stu-id="9670a-108">Types for these expressions must be 32-bit integers.</span></span>

<span data-ttu-id="9670a-109">Bien qu’il s’agisse techniquement d’une expression, `for...to` ressemble davantage à une instruction traditionnelle dans un langage de programmation impératif.</span><span class="sxs-lookup"><span data-stu-id="9670a-109">Although technically an expression, `for...to` is more like a traditional statement in an imperative programming language.</span></span> <span data-ttu-id="9670a-110">Le type de retour de l' *expression de corps* doit être `unit`.</span><span class="sxs-lookup"><span data-stu-id="9670a-110">The return type for the *body-expression* must be `unit`.</span></span> <span data-ttu-id="9670a-111">Les exemples suivants illustrent différentes utilisations de l’expression `for...to`.</span><span class="sxs-lookup"><span data-stu-id="9670a-111">The following examples show various uses of the `for...to` expression.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5101.fs)]

<span data-ttu-id="9670a-112">La sortie du code précédent est la suivante.</span><span class="sxs-lookup"><span data-stu-id="9670a-112">The output of the previous code is as follows.</span></span>

```console
1 2 3 4 5 6 7 8 9 10
10 9 8 7 6 5 4 3 2 1
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18
```

## <a name="see-also"></a><span data-ttu-id="9670a-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9670a-113">See also</span></span>

- [<span data-ttu-id="9670a-114">Informations de référence du langage F#</span><span class="sxs-lookup"><span data-stu-id="9670a-114">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="9670a-115">Boucles : expression `for...in`</span><span class="sxs-lookup"><span data-stu-id="9670a-115">Loops: `for...in` Expression</span></span>](loops-for-in-expression.md)
- [<span data-ttu-id="9670a-116">Boucles : expression `while...do`</span><span class="sxs-lookup"><span data-stu-id="9670a-116">Loops: `while...do` Expression</span></span>](loops-while-do-expression.md)
