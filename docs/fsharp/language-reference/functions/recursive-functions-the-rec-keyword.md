---
title: 'Fonctions récursives: Mot clé Rec'
description: Découvrez comment le F# mot clé’Rec’est utilisé avec le mot clé’Let’pour définir une fonction récursive.
ms.date: 05/16/2016
ms.openlocfilehash: 7edaa7206b2109c7b1a405624b9b2330968f9c52
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630653"
---
# <a name="recursive-functions-the-rec-keyword"></a><span data-ttu-id="d5679-103">Fonctions récursives: Mot clé Rec</span><span class="sxs-lookup"><span data-stu-id="d5679-103">Recursive Functions: The rec Keyword</span></span>

<span data-ttu-id="d5679-104">Le `rec` mot clé est utilisé conjointement avec `let` le mot clé pour définir une fonction récursive.</span><span class="sxs-lookup"><span data-stu-id="d5679-104">The `rec` keyword is used together with the `let` keyword to define a recursive function.</span></span>

## <a name="syntax"></a><span data-ttu-id="d5679-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d5679-105">Syntax</span></span>

```fsharp
// Recursive function:
let rec function-nameparameter-list =
function-body

// Mutually recursive functions:
let rec function1-nameparameter-list =
function1-body
and function2-nameparameter-list =
function2-body
...
```

## <a name="remarks"></a><span data-ttu-id="d5679-106">Notes</span><span class="sxs-lookup"><span data-stu-id="d5679-106">Remarks</span></span>

<span data-ttu-id="d5679-107">Les fonctions récursives, les fonctions qui s’appellent, sont identifiées F# explicitement dans le langage.</span><span class="sxs-lookup"><span data-stu-id="d5679-107">Recursive functions, functions that call themselves, are identified explicitly in the F# language.</span></span> <span data-ttu-id="d5679-108">Cela rend l’identificateur qui est défini comme étant disponible dans l’étendue de la fonction.</span><span class="sxs-lookup"><span data-stu-id="d5679-108">This makes the identifer that is being defined available in the scope of the function.</span></span>

<span data-ttu-id="d5679-109">Le code suivant illustre une fonction récursive qui calcule le *n*<sup>ième</sup> nombre de Fibonacci.</span><span class="sxs-lookup"><span data-stu-id="d5679-109">The following code illustrates a recursive function that computes the *n*<sup>th</sup> Fibonacci number.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet4001.fs)]

> [!NOTE]
> <span data-ttu-id="d5679-110">Dans la pratique, le code comme celui ci-dessus est gaspillant la mémoire et le temps processeur, car il implique le recalcul des valeurs calculées précédemment.</span><span class="sxs-lookup"><span data-stu-id="d5679-110">In practice, code like that above is wasteful of memory and processor time because it involves the recomputation of previously computed values.</span></span>

<span data-ttu-id="d5679-111">Les méthodes sont implicitement récursives dans le type; Il n’est pas nécessaire d’ajouter `rec` le mot clé.</span><span class="sxs-lookup"><span data-stu-id="d5679-111">Methods are implicitly recursive within the type; there is no need to add the `rec` keyword.</span></span> <span data-ttu-id="d5679-112">Les liaisons Let dans les classes ne sont pas implicitement récursives.</span><span class="sxs-lookup"><span data-stu-id="d5679-112">Let bindings within classes are not implicitly recursive.</span></span>

## <a name="mutually-recursive-functions"></a><span data-ttu-id="d5679-113">Fonctions mutuellement récursives</span><span class="sxs-lookup"><span data-stu-id="d5679-113">Mutually Recursive Functions</span></span>

<span data-ttu-id="d5679-114">Parfois, lesfonctions sont mutuellement récursives, ce qui signifie que les appels forment un cercle, où une fonction appelle une autre qui, à son tour, appelle la première, avec un nombre quelconque d’appels entre les deux.</span><span class="sxs-lookup"><span data-stu-id="d5679-114">Sometimes functions are *mutually recursive*, meaning that calls form a circle, where one function calls another which in turn calls the first, with any number of calls in between.</span></span> <span data-ttu-id="d5679-115">Vous devez définir de telles fonctions dans une `let` liaison, en utilisant le `and` mot clé pour les lier ensemble.</span><span class="sxs-lookup"><span data-stu-id="d5679-115">You must define such functions together in the one `let` binding, using the `and` keyword to link them together.</span></span>

<span data-ttu-id="d5679-116">L’exemple suivant montre deux fonctions mutuellement récursives.</span><span class="sxs-lookup"><span data-stu-id="d5679-116">The following example shows two mutually recursive functions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet4002.fs)]

## <a name="see-also"></a><span data-ttu-id="d5679-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d5679-117">See also</span></span>

- [<span data-ttu-id="d5679-118">Fonctions</span><span class="sxs-lookup"><span data-stu-id="d5679-118">Functions</span></span>](index.md)
