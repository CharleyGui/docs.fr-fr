---
title: 'Boucles : expression while...do'
description: Découvrez comment le... l’expression do est utilisée pour effectuer une exécution itérative (bouclage) alors qu’une condition de test spécifiée a la valeur true.
ms.date: 05/16/2016
ms.openlocfilehash: 73526279358db101f8d07721a200920f1e87f119
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216637"
---
# <a name="loops-whiledo-expression"></a><span data-ttu-id="d20e8-103">Boucles : expression while...do</span><span class="sxs-lookup"><span data-stu-id="d20e8-103">Loops: while...do Expression</span></span>

<span data-ttu-id="d20e8-104">L' `while...do` expression est utilisée pour effectuer une exécution itérative (bouclage) alors qu’une condition de test spécifiée a la valeur true.</span><span class="sxs-lookup"><span data-stu-id="d20e8-104">The `while...do` expression is used to perform iterative execution (looping) while a specified test condition is true.</span></span>

## <a name="syntax"></a><span data-ttu-id="d20e8-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d20e8-105">Syntax</span></span>

```fsharp
while test-expression do
    body-expression
```

## <a name="remarks"></a><span data-ttu-id="d20e8-106">Notes</span><span class="sxs-lookup"><span data-stu-id="d20e8-106">Remarks</span></span>

<span data-ttu-id="d20e8-107">L' *expression de test* est évaluée ; Si c’est `true`le cas, le *corps-expression* est exécuté et l’expression de test est de nouveau évaluée.</span><span class="sxs-lookup"><span data-stu-id="d20e8-107">The *test-expression* is evaluated; if it is `true`, the *body-expression* is executed and the test expression is evaluated again.</span></span> <span data-ttu-id="d20e8-108">Le *corps de l’expression* doit être `unit`de type.</span><span class="sxs-lookup"><span data-stu-id="d20e8-108">The *body-expression* must have type `unit`.</span></span> <span data-ttu-id="d20e8-109">Si l’expression de test `false`est, l’itération se termine.</span><span class="sxs-lookup"><span data-stu-id="d20e8-109">If the test expression is `false`, the iteration ends.</span></span>

<span data-ttu-id="d20e8-110">L’exemple suivant illustre l’utilisation de l' `while...do` expression.</span><span class="sxs-lookup"><span data-stu-id="d20e8-110">The following example illustrates the use of the `while...do` expression.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5301.fs)]

<span data-ttu-id="d20e8-111">La sortie du code précédent est un flux de nombres aléatoires compris entre 1 et 20, le dernier étant 10.</span><span class="sxs-lookup"><span data-stu-id="d20e8-111">The output of the previous code is a stream of random numbers between 1 and 20, the last of which is 10.</span></span>

```console
13 19 8 18 16 2 10
Found a 10!
```

> [!NOTE]
> <span data-ttu-id="d20e8-112">Vous pouvez utiliser `while...do` dans les expressions de séquence et d’autres expressions de calcul, auquel cas une version personnalisée `while...do` de l’expression est utilisée.</span><span class="sxs-lookup"><span data-stu-id="d20e8-112">You can use `while...do` in sequence expressions and other computation expressions, in which case a customized version of the `while...do` expression is used.</span></span> <span data-ttu-id="d20e8-113">Pour plus d’informations, consultez [séquences](sequences.md), [flux de travail asynchrones](asynchronous-workflows.md) et [expressions de calcul](computation-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="d20e8-113">For more information, see [Sequences](sequences.md), [Asynchronous Workflows](asynchronous-workflows.md), and [Computation Expressions](computation-expressions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d20e8-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d20e8-114">See also</span></span>

- [<span data-ttu-id="d20e8-115">Informations de référence du langage F#</span><span class="sxs-lookup"><span data-stu-id="d20e8-115">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="d20e8-116">Boucles `for...in`Formule</span><span class="sxs-lookup"><span data-stu-id="d20e8-116">Loops: `for...in` Expression</span></span>](loops-for-in-expression.md)
- [<span data-ttu-id="d20e8-117">Boucles `for...to`Formule</span><span class="sxs-lookup"><span data-stu-id="d20e8-117">Loops: `for...to` Expression</span></span>](loops-for-to-expression.md)
