---
title: 'Exceptions : fonction raise'
description: Découvrez comment la F# fonction «Raise» est utilisée pour indiquer qu’une erreur ou une condition exceptionnelle s’est produite.
ms.date: 05/16/2016
ms.openlocfilehash: e0cc8da8310203c537b8081af8a225671bd8c6a3
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630288"
---
# <a name="exceptions-the-raise-function"></a><span data-ttu-id="acba2-103">Exceptions : fonction raise</span><span class="sxs-lookup"><span data-stu-id="acba2-103">Exceptions: the raise Function</span></span>

<span data-ttu-id="acba2-104">La `raise` fonction est utilisée pour indiquer qu’une erreur ou une condition exceptionnelle s’est produite.</span><span class="sxs-lookup"><span data-stu-id="acba2-104">The `raise` function is used to indicate that an error or exceptional condition has occurred.</span></span> <span data-ttu-id="acba2-105">Les informations sur l’erreur sont capturées dans un objet exception.</span><span class="sxs-lookup"><span data-stu-id="acba2-105">Information about the error is captured in an exception object.</span></span>

## <a name="syntax"></a><span data-ttu-id="acba2-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="acba2-106">Syntax</span></span>

```fsharp
raise (expression)
```

## <a name="remarks"></a><span data-ttu-id="acba2-107">Notes</span><span class="sxs-lookup"><span data-stu-id="acba2-107">Remarks</span></span>

<span data-ttu-id="acba2-108">La `raise` fonction génère un objet exception et lance un processus de déroulement de pile.</span><span class="sxs-lookup"><span data-stu-id="acba2-108">The `raise` function generates an exception object and initiates a stack unwinding process.</span></span> <span data-ttu-id="acba2-109">Le processus de déroulement de la pile étant géré par le common language runtime (CLR), le comportement de ce processus est le même que dans tout autre langage .NET.</span><span class="sxs-lookup"><span data-stu-id="acba2-109">The stack unwinding process is managed by the common language runtime (CLR), so the behavior of this process is the same as it is in any other .NET language.</span></span> <span data-ttu-id="acba2-110">Le processus de déroulement de la pile est une recherche d’un gestionnaire d’exceptions qui correspond à l’exception générée.</span><span class="sxs-lookup"><span data-stu-id="acba2-110">The stack unwinding process is a search for an exception handler that matches the generated exception.</span></span> <span data-ttu-id="acba2-111">La recherche démarre dans l’expression `try...with` actuelle, s’il en existe une.</span><span class="sxs-lookup"><span data-stu-id="acba2-111">The search starts in the current `try...with` expression, if there is one.</span></span> <span data-ttu-id="acba2-112">Chaque modèle du bloc `with` est vérifié, dans l’ordre.</span><span class="sxs-lookup"><span data-stu-id="acba2-112">Each pattern in the `with` block is checked, in order.</span></span> <span data-ttu-id="acba2-113">Lorsqu’un gestionnaire d’exceptions correspondant est trouvé, l’exception est considérée comme gérée; dans le cas contraire, la pile est `with` déroulée et les blocs de la chaîne d’appel sont vérifiés jusqu’à ce qu’un gestionnaire correspondant soit trouvé.</span><span class="sxs-lookup"><span data-stu-id="acba2-113">When a matching exception handler is found, the exception is considered handled; otherwise, the stack is unwound and `with` blocks up the call chain are checked until a matching handler is found.</span></span> <span data-ttu-id="acba2-114">Tous `finally` les blocs qui sont rencontrés dans la chaîne d’appel sont également exécutés dans l’ordre où la pile se déroule.</span><span class="sxs-lookup"><span data-stu-id="acba2-114">Any `finally` blocks that are encountered in the call chain are also executed in sequence as the stack unwinds.</span></span>

<span data-ttu-id="acba2-115">La `raise` fonction est l’équivalent de `throw` dans C# ou C++.</span><span class="sxs-lookup"><span data-stu-id="acba2-115">The `raise` function is the equivalent of `throw` in C# or C++.</span></span> <span data-ttu-id="acba2-116">Utilisez `reraise` dans un gestionnaire catch pour propager la même exception en haut de la chaîne d’appel.</span><span class="sxs-lookup"><span data-stu-id="acba2-116">Use `reraise` in a catch handler to propagate the same exception up the call chain.</span></span>

<span data-ttu-id="acba2-117">Les exemples de code suivants illustrent l’utilisation `raise` de la fonction pour générer une exception.</span><span class="sxs-lookup"><span data-stu-id="acba2-117">The following code examples illustrate the use of the `raise` function to generate an exception.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5801.fs)]

<span data-ttu-id="acba2-118">La `raise` fonction peut également être utilisée pour déclencher des exceptions .net, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="acba2-118">The `raise` function can also be used to raise .NET exceptions, as shown in the following example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5802.fs)]

## <a name="see-also"></a><span data-ttu-id="acba2-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="acba2-119">See also</span></span>

- [<span data-ttu-id="acba2-120">Gestion des exceptions</span><span class="sxs-lookup"><span data-stu-id="acba2-120">Exception Handling</span></span>](index.md)
- [<span data-ttu-id="acba2-121">Types d'exceptions</span><span class="sxs-lookup"><span data-stu-id="acba2-121">Exception Types</span></span>](exception-types.md)
- [<span data-ttu-id="acba2-122">Exceptions : L' `try...with` expression</span><span class="sxs-lookup"><span data-stu-id="acba2-122">Exceptions: The `try...with` Expression</span></span>](the-try-with-expression.md)
- [<span data-ttu-id="acba2-123">Exceptions : L' `try...finally` expression</span><span class="sxs-lookup"><span data-stu-id="acba2-123">Exceptions: The `try...finally` Expression</span></span>](the-try-finally-expression.md)
- [<span data-ttu-id="acba2-124">Exceptions : La `failwith` fonction</span><span class="sxs-lookup"><span data-stu-id="acba2-124">Exceptions: The `failwith` Function</span></span>](the-failwith-function.md)
- [<span data-ttu-id="acba2-125">Exceptions : La `invalidArg` fonction</span><span class="sxs-lookup"><span data-stu-id="acba2-125">Exceptions: The `invalidArg` Function</span></span>](the-invalidArg-function.md)
