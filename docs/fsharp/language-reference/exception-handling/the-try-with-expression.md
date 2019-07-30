---
title: 'Exceptions : try...with (expression)'
description: Découvrez comment utiliser la F# procédure «try... avec’expression pour la gestion des exceptions.
ms.date: 05/16/2016
ms.openlocfilehash: e4d615086a93e26b76cca460e797659ca13792b5
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630250"
---
# <a name="exceptions-the-trywith-expression"></a><span data-ttu-id="da8dd-103">Exceptions : try...with (expression)</span><span class="sxs-lookup"><span data-stu-id="da8dd-103">Exceptions: The try...with Expression</span></span>

<span data-ttu-id="da8dd-104">Cette rubrique décrit l' `try...with` expression, qui est utilisée pour la gestion des exceptions dans le F# langage.</span><span class="sxs-lookup"><span data-stu-id="da8dd-104">This topic describes the `try...with` expression, the expression that is used for exception handling in the F# language.</span></span>

## <a name="syntax"></a><span data-ttu-id="da8dd-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="da8dd-105">Syntax</span></span>

```fsharp
try
    expression1
with
| pattern1 -> expression2
| pattern2 -> expression3
...
```

## <a name="remarks"></a><span data-ttu-id="da8dd-106">Notes</span><span class="sxs-lookup"><span data-stu-id="da8dd-106">Remarks</span></span>

<span data-ttu-id="da8dd-107">L' `try...with` expression est utilisée pour gérer les exceptions F#dans.</span><span class="sxs-lookup"><span data-stu-id="da8dd-107">The `try...with` expression is used to handle exceptions in F#.</span></span> <span data-ttu-id="da8dd-108">Elle est similaire à l' `try...catch` instruction dans C#.</span><span class="sxs-lookup"><span data-stu-id="da8dd-108">It is similar to the `try...catch` statement in C#.</span></span> <span data-ttu-id="da8dd-109">Dans la syntaxe précédente, le code de *expression1* peut générer une exception.</span><span class="sxs-lookup"><span data-stu-id="da8dd-109">In the preceding syntax, the code in *expression1* might generate an exception.</span></span> <span data-ttu-id="da8dd-110">L' `try...with` expression retourne une valeur.</span><span class="sxs-lookup"><span data-stu-id="da8dd-110">The `try...with` expression returns a value.</span></span> <span data-ttu-id="da8dd-111">Si aucune exception n’est levée, l’expression entière retourne la valeur de *expression1*.</span><span class="sxs-lookup"><span data-stu-id="da8dd-111">If no exception is thrown, the whole expression returns the value of *expression1*.</span></span> <span data-ttu-id="da8dd-112">Si une exception est levée, chaque *modèle* est comparé à son tour à l’exception, et pour le premier modèle correspondant, l' *expression*correspondante, appelée *Gestionnaire d’exceptions*, pour cette branche est exécutée et l’expression globale retourne la valeur de l’expression dans ce gestionnaire d’exceptions.</span><span class="sxs-lookup"><span data-stu-id="da8dd-112">If an exception is thrown, each *pattern* is compared in turn with the exception, and for the first matching pattern, the corresponding *expression*, known as the *exception handler*, for that branch is executed, and the overall expression returns the value of the expression in that exception handler.</span></span> <span data-ttu-id="da8dd-113">Si aucun modèle ne correspond, l’exception se propage vers le haut de la pile des appels jusqu’à ce qu’un gestionnaire correspondant soit trouvé.</span><span class="sxs-lookup"><span data-stu-id="da8dd-113">If no pattern matches, the exception propagates up the call stack until a matching handler is found.</span></span> <span data-ttu-id="da8dd-114">Les types des valeurs retournées à partir de chaque expression dans les gestionnaires d’exceptions doivent correspondre au type retourné par l' `try` expression dans le bloc.</span><span class="sxs-lookup"><span data-stu-id="da8dd-114">The types of the values returned from each expression in the exception handlers must match the type returned from the expression in the `try` block.</span></span>

<span data-ttu-id="da8dd-115">Souvent, le fait qu’une erreur s’est produite signifie également qu’il n’y a pas de valeur valide pouvant être retournée par les expressions de chaque gestionnaire d’exceptions.</span><span class="sxs-lookup"><span data-stu-id="da8dd-115">Frequently, the fact that an error occurred also means that there is no valid value that can be returned from the expressions in each exception handler.</span></span> <span data-ttu-id="da8dd-116">Un modèle fréquent consiste à avoir le type de l’expression comme type d’option.</span><span class="sxs-lookup"><span data-stu-id="da8dd-116">A frequent pattern is to have the type of the expression be an option type.</span></span> <span data-ttu-id="da8dd-117">L’exemple de code suivant illustre ce modèle.</span><span class="sxs-lookup"><span data-stu-id="da8dd-117">The following code example illustrates this pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5601.fs)]

<span data-ttu-id="da8dd-118">Il F# peut s’agir d’exceptions .net ou d’exceptions.</span><span class="sxs-lookup"><span data-stu-id="da8dd-118">Exceptions can be .NET exceptions, or they can be F# exceptions.</span></span> <span data-ttu-id="da8dd-119">Vous pouvez définir F# des exceptions à l' `exception` aide du mot clé.</span><span class="sxs-lookup"><span data-stu-id="da8dd-119">You can define F# exceptions by using the `exception` keyword.</span></span>

<span data-ttu-id="da8dd-120">Vous pouvez utiliser divers modèles pour filtrer sur le type d’exception et d’autres conditions; les options sont résumées dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="da8dd-120">You can use a variety of patterns to filter on the exception type and other conditions; the options are summarized in the following table.</span></span>

|<span data-ttu-id="da8dd-121">Motif</span><span class="sxs-lookup"><span data-stu-id="da8dd-121">Pattern</span></span>|<span data-ttu-id="da8dd-122">Description</span><span class="sxs-lookup"><span data-stu-id="da8dd-122">Description</span></span>|
|-------|-----------|
|<span data-ttu-id="da8dd-123">:?</span><span class="sxs-lookup"><span data-stu-id="da8dd-123">:?</span></span> <span data-ttu-id="da8dd-124">*exception-type*</span><span class="sxs-lookup"><span data-stu-id="da8dd-124">*exception-type*</span></span>|<span data-ttu-id="da8dd-125">Correspond au type d’exception .NET spécifié.</span><span class="sxs-lookup"><span data-stu-id="da8dd-125">Matches the specified .NET exception type.</span></span>|
|<span data-ttu-id="da8dd-126">:?</span><span class="sxs-lookup"><span data-stu-id="da8dd-126">:?</span></span> <span data-ttu-id="da8dd-127">*exception-type* en tant qu' *identificateur*</span><span class="sxs-lookup"><span data-stu-id="da8dd-127">*exception-type* as *identifier*</span></span>|<span data-ttu-id="da8dd-128">Correspond au type d’exception .NET spécifié, mais donne à l’exception une valeur nommée.</span><span class="sxs-lookup"><span data-stu-id="da8dd-128">Matches the specified .NET exception type, but gives the exception a named value.</span></span>|
|<span data-ttu-id="da8dd-129">*nom de l’exception* (*arguments*)</span><span class="sxs-lookup"><span data-stu-id="da8dd-129">*exception-name*(*arguments*)</span></span>|<span data-ttu-id="da8dd-130">Correspond à F# un type d’exception et lie les arguments.</span><span class="sxs-lookup"><span data-stu-id="da8dd-130">Matches an F# exception type and binds the arguments.</span></span>|
|<span data-ttu-id="da8dd-131">*identifier*</span><span class="sxs-lookup"><span data-stu-id="da8dd-131">*identifier*</span></span>|<span data-ttu-id="da8dd-132">Représente n’importe quelle exception et lie le nom à l’objet exception.</span><span class="sxs-lookup"><span data-stu-id="da8dd-132">Matches any exception and binds the name to the exception object.</span></span> <span data-ttu-id="da8dd-133">Équivalent à **:? System. exception en**tant qu'_identificateur_</span><span class="sxs-lookup"><span data-stu-id="da8dd-133">Equivalent to **:? System.Exception as**_identifier_</span></span>|
|<span data-ttu-id="da8dd-134">*identificateur* lorsque la *condition*</span><span class="sxs-lookup"><span data-stu-id="da8dd-134">*identifier* when *condition*</span></span>|<span data-ttu-id="da8dd-135">Correspond à toute exception si la condition est true.</span><span class="sxs-lookup"><span data-stu-id="da8dd-135">Matches any exception if the condition is true.</span></span>|

## <a name="examples"></a><span data-ttu-id="da8dd-136">Exemples</span><span class="sxs-lookup"><span data-stu-id="da8dd-136">Examples</span></span>

<span data-ttu-id="da8dd-137">Les exemples de code suivants illustrent l’utilisation des différents modèles de gestionnaire d’exceptions.</span><span class="sxs-lookup"><span data-stu-id="da8dd-137">The following code examples illustrate the use of the various exception handler patterns.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5602.fs)]

> [!NOTE]
> <span data-ttu-id="da8dd-138">La `try...with` construction est une expression distincte de l' `try...finally` expression.</span><span class="sxs-lookup"><span data-stu-id="da8dd-138">The `try...with` construct is a separate expression from the `try...finally` expression.</span></span> <span data-ttu-id="da8dd-139">Par conséquent, si votre code nécessite à `with` la fois un `finally` bloc et un bloc, vous devrez imbriquer les deux expressions.</span><span class="sxs-lookup"><span data-stu-id="da8dd-139">Therefore, if your code requires both a `with` block and a `finally` block, you will have to nest the two expressions.</span></span>

> [!NOTE]
> <span data-ttu-id="da8dd-140">Vous pouvez utiliser `try...with` dans les flux de travail asynchrones et d’autres expressions de calcul, auquel cas une version `try...with` personnalisée de l’expression est utilisée.</span><span class="sxs-lookup"><span data-stu-id="da8dd-140">You can use `try...with` in asynchronous workflows and other computation expressions, in which case a customized version of the `try...with` expression is used.</span></span> <span data-ttu-id="da8dd-141">Pour plus d’informations, consultez [flux de travail asynchrones](../asynchronous-workflows.md)et expressions de [calcul](../computation-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="da8dd-141">For more information, see [Asynchronous Workflows](../asynchronous-workflows.md), and [Computation Expressions](../computation-expressions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="da8dd-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="da8dd-142">See also</span></span>

- [<span data-ttu-id="da8dd-143">Gestion des exceptions</span><span class="sxs-lookup"><span data-stu-id="da8dd-143">Exception Handling</span></span>](index.md)
- [<span data-ttu-id="da8dd-144">Types d'exceptions</span><span class="sxs-lookup"><span data-stu-id="da8dd-144">Exception Types</span></span>](exception-types.md)
- [<span data-ttu-id="da8dd-145">Exceptions : L' `try...finally` expression</span><span class="sxs-lookup"><span data-stu-id="da8dd-145">Exceptions: The `try...finally` Expression</span></span>](the-try-finally-expression.md)
