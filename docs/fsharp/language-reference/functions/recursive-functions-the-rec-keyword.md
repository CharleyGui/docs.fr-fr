---
title: 'Fonctions récursives : Le mot clé rec'
description: Découvrez comment la F# mot clé « rec » est utilisé avec le mot clé 'let' pour définir une fonction récursive.
ms.date: 05/16/2016
ms.openlocfilehash: 86eaf1c8a5566d8b9cbc4dcb72f945e2497e5439
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65645291"
---
# <a name="recursive-functions-the-rec-keyword"></a><span data-ttu-id="153c2-103">Fonctions récursives : Le mot clé rec</span><span class="sxs-lookup"><span data-stu-id="153c2-103">Recursive Functions: The rec Keyword</span></span>

<span data-ttu-id="153c2-104">Le `rec` mot clé est utilisée conjointement avec la `let` mot clé pour définir une fonction récursive.</span><span class="sxs-lookup"><span data-stu-id="153c2-104">The `rec` keyword is used together with the `let` keyword to define a recursive function.</span></span>

## <a name="syntax"></a><span data-ttu-id="153c2-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="153c2-105">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="153c2-106">Notes</span><span class="sxs-lookup"><span data-stu-id="153c2-106">Remarks</span></span>

<span data-ttu-id="153c2-107">Fonctions récursives, les fonctions qui appellent elles-mêmes, sont identifiées explicitement dans le F# langage.</span><span class="sxs-lookup"><span data-stu-id="153c2-107">Recursive functions, functions that call themselves, are identified explicitly in the F# language.</span></span> <span data-ttu-id="153c2-108">L’identificateur qui est en cours de définition sont ainsi disponibles dans la portée de la fonction.</span><span class="sxs-lookup"><span data-stu-id="153c2-108">This makes the identifer that is being defined available in the scope of the function.</span></span>

<span data-ttu-id="153c2-109">Le code suivant illustre une fonction récursive qui calcule le *n*<sup>th</sup> nombre Fibonacci.</span><span class="sxs-lookup"><span data-stu-id="153c2-109">The following code illustrates a recursive function that computes the *n*<sup>th</sup> Fibonacci number.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet4001.fs)]

> [!NOTE]
> <span data-ttu-id="153c2-110">Dans la pratique, code comme celui ci-dessus est inutile de mémoire et le temps processeur, car il implique le recalcul des valeurs précédemment calculées.</span><span class="sxs-lookup"><span data-stu-id="153c2-110">In practice, code like that above is wasteful of memory and processor time because it involves the recomputation of previously computed values.</span></span>

<span data-ttu-id="153c2-111">Les méthodes sont implicitement récursives dans le type ; Il est inutile d’ajouter le `rec` mot clé.</span><span class="sxs-lookup"><span data-stu-id="153c2-111">Methods are implicitly recursive within the type; there is no need to add the `rec` keyword.</span></span> <span data-ttu-id="153c2-112">Liaisons let dans les classes ne sont pas implicitement récursifs.</span><span class="sxs-lookup"><span data-stu-id="153c2-112">Let bindings within classes are not implicitly recursive.</span></span>

## <a name="mutually-recursive-functions"></a><span data-ttu-id="153c2-113">Fonctions mutuellement récursives</span><span class="sxs-lookup"><span data-stu-id="153c2-113">Mutually Recursive Functions</span></span>

<span data-ttu-id="153c2-114">Parfois, les fonctions sont *mutuellement récursives*, ce qui signifie que les appels forment un cercle, où une fonction appelle une autre qui à son tour appelle la première, avec n’importe quel nombre d’appels entre les deux.</span><span class="sxs-lookup"><span data-stu-id="153c2-114">Sometimes functions are *mutually recursive*, meaning that calls form a circle, where one function calls another which in turn calls the first, with any number of calls in between.</span></span> <span data-ttu-id="153c2-115">Vous devez définir de telles fonctions dans celui `let` à l’aide de la liaison la `and` mot clé pour les relier.</span><span class="sxs-lookup"><span data-stu-id="153c2-115">You must define such functions together in the one `let` binding, using the `and` keyword to link them together.</span></span>

<span data-ttu-id="153c2-116">L’exemple suivant montre deux mutuellement fonctions récursives.</span><span class="sxs-lookup"><span data-stu-id="153c2-116">The following example shows two mutually recursive functions.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet4002.fs)]

## <a name="see-also"></a><span data-ttu-id="153c2-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="153c2-117">See also</span></span>

- [<span data-ttu-id="153c2-118">Fonctions</span><span class="sxs-lookup"><span data-stu-id="153c2-118">Functions</span></span>](index.md)
