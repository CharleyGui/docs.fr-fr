---
title: 'Exceptions : try...finally (expression)'
description: Découvrez comment les F# ... Enfin, l’expression vous permet d’exécuter le code de nettoyage même si un bloc de code lève une exception.
ms.date: 05/16/2016
ms.openlocfilehash: 0ddb64ac13b307404864ec5b54f26fd8a7a3d7d8
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2019
ms.locfileid: "71083005"
---
# <a name="exceptions-the-tryfinally-expression"></a><span data-ttu-id="eb95b-103">Exceptions : try...finally (expression)</span><span class="sxs-lookup"><span data-stu-id="eb95b-103">Exceptions: The try...finally Expression</span></span>

<span data-ttu-id="eb95b-104">L' `try...finally` expression vous permet d’exécuter le code de nettoyage même si un bloc de code lève une exception.</span><span class="sxs-lookup"><span data-stu-id="eb95b-104">The `try...finally` expression enables you to execute clean-up code even if a block of code throws an exception.</span></span>

## <a name="syntax"></a><span data-ttu-id="eb95b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eb95b-105">Syntax</span></span>

```fsharp
try
    expression1
finally
    expression2
```

## <a name="remarks"></a><span data-ttu-id="eb95b-106">Notes</span><span class="sxs-lookup"><span data-stu-id="eb95b-106">Remarks</span></span>

<span data-ttu-id="eb95b-107">L' `try...finally` expression peut être utilisée pour exécuter le code dans *Expression2* dans la syntaxe précédente, qu’une exception soit générée ou non lors de l’exécution de *expression1*.</span><span class="sxs-lookup"><span data-stu-id="eb95b-107">The `try...finally` expression can be used to execute the code in *expression2* in the preceding syntax regardless of whether an exception is generated during the execution of *expression1*.</span></span>

<span data-ttu-id="eb95b-108">Le type de *Expression2* ne contribue pas à la valeur de l’expression entière ; le type retourné lorsqu’une exception ne se produit pas est la dernière valeur dans *expression1*.</span><span class="sxs-lookup"><span data-stu-id="eb95b-108">The type of *expression2* does not contribute to the value of the whole expression; the type returned when an exception does not occur is the last value in *expression1*.</span></span> <span data-ttu-id="eb95b-109">Lorsqu’une exception se produit, aucune valeur n’est retournée et le déroulement du contrôle est transféré vers le gestionnaire d’exceptions correspondant suivant, en haut de la pile des appels.</span><span class="sxs-lookup"><span data-stu-id="eb95b-109">When an exception does occur, no value is returned and the flow of control transfers to the next matching exception handler up the call stack.</span></span> <span data-ttu-id="eb95b-110">Si aucun gestionnaire d’exceptions n’est trouvé, le programme se termine.</span><span class="sxs-lookup"><span data-stu-id="eb95b-110">If no exception handler is found, the program terminates.</span></span> <span data-ttu-id="eb95b-111">Avant que le code d’un gestionnaire correspondant soit exécuté ou que le programme se termine, le `finally` code de la branche est exécuté.</span><span class="sxs-lookup"><span data-stu-id="eb95b-111">Before the code in a matching handler is executed or the program terminates, the code in the `finally` branch is executed.</span></span>

<span data-ttu-id="eb95b-112">Le code suivant illustre l’utilisation de l' `try...finally` expression.</span><span class="sxs-lookup"><span data-stu-id="eb95b-112">The following code demonstrates the use of the `try...finally` expression.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5701.fs)]

<span data-ttu-id="eb95b-113">La sortie de la console est la suivante.</span><span class="sxs-lookup"><span data-stu-id="eb95b-113">The output to the console is as follows.</span></span>

```console
Closing stream
Exception handled.
```

<span data-ttu-id="eb95b-114">Comme vous pouvez le voir dans la sortie, le flux a été fermé avant le traitement de l’exception externe, `test.txt` et le fichier `test1`contient le texte, ce qui indique que les mémoires tampons ont été vidées et écrites sur le disque, même si l’exception a été transférée contrôle au gestionnaire d’exceptions externe.</span><span class="sxs-lookup"><span data-stu-id="eb95b-114">As you can see from the output, the stream was closed before the outer exception was handled, and the file `test.txt` contains the text `test1`, which indicates that the buffers were flushed and written to disk even though the exception transferred control to the outer exception handler.</span></span>

<span data-ttu-id="eb95b-115">Notez que la `try...with` construction est une construction distincte de la `try...finally` construction.</span><span class="sxs-lookup"><span data-stu-id="eb95b-115">Note that the `try...with` construct is a separate construct from the `try...finally` construct.</span></span> <span data-ttu-id="eb95b-116">Par conséquent, si votre code nécessite à `with` la fois un `finally` bloc et un bloc, vous devez imbriquer les deux constructions, comme dans l’exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="eb95b-116">Therefore, if your code requires both a `with` block and a `finally` block, you have to nest the two constructs, as in the following code example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5702.fs)]

<span data-ttu-id="eb95b-117">Dans le contexte des expressions de calcul, y compris les expressions de séquence et les flux de travail asynchrones, **essayez... Enfin** , les expressions peuvent avoir une implémentation personnalisée.</span><span class="sxs-lookup"><span data-stu-id="eb95b-117">In the context of computation expressions, including sequence expressions and asynchronous workflows, **try...finally** expressions can have a custom implementation.</span></span> <span data-ttu-id="eb95b-118">Pour plus d’informations, consultez [expressions de calcul](../computation-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="eb95b-118">For more information, see [Computation Expressions](../computation-expressions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="eb95b-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eb95b-119">See also</span></span>

- [<span data-ttu-id="eb95b-120">Gestion des exceptions</span><span class="sxs-lookup"><span data-stu-id="eb95b-120">Exception Handling</span></span>](index.md)
- [<span data-ttu-id="eb95b-121">Exceptions : L' `try...with` expression</span><span class="sxs-lookup"><span data-stu-id="eb95b-121">Exceptions: The `try...with` Expression</span></span>](the-try-with-expression.md)
