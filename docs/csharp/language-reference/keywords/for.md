---
description: for, instruction-référence C#
title: for, instruction-référence C#
ms.date: 06/13/2018
f1_keywords:
- for
- for_CSharpKeyword
helpviewer_keywords:
- for keyword [C#]
ms.assetid: 34041a40-2c87-467a-9ffb-a0417d8f67a8
ms.openlocfilehash: be9ecdc08d54c9cde1c49656a16e0d85a6d7084d
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89126929"
---
# <a name="for-c-reference"></a><span data-ttu-id="42207-103">for (référence C#)</span><span class="sxs-lookup"><span data-stu-id="42207-103">for (C# reference)</span></span>

<span data-ttu-id="42207-104">L’instruction `for` exécute une instruction ou un bloc d’instructions tant qu’une expression booléenne donne la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="42207-104">The `for` statement executes a statement or a block of statements while a specified Boolean expression evaluates to `true`.</span></span>

<span data-ttu-id="42207-105">À tout moment dans le bloc d’instructions `for`, vous pouvez sortir de la boucle à l’aide de l’instruction [break](break.md), ou passer à l’itération suivante de la boucle à l’aide de l’instruction [continue](continue.md).</span><span class="sxs-lookup"><span data-stu-id="42207-105">At any point within the `for` statement block, you can break out of the loop by using the [break](break.md) statement, or step to the next iteration in the loop by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="42207-106">Vous pouvez également quitter une `for` boucle à l’aide des instructions [goto](goto.md), [Return](return.md)ou [throw](throw.md) .</span><span class="sxs-lookup"><span data-stu-id="42207-106">You can also exit a `for` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="structure-of-the-for-statement"></a><span data-ttu-id="42207-107">Structure de l’instruction `for`</span><span class="sxs-lookup"><span data-stu-id="42207-107">Structure of the `for` statement</span></span>

<span data-ttu-id="42207-108">Chaque instruction `for` définit des sections *initialiseur*, *condition* et *itérateur* :</span><span class="sxs-lookup"><span data-stu-id="42207-108">The `for` statement defines *initializer*, *condition*, and *iterator* sections:</span></span>

```csharp
for (initializer; condition; iterator)
    body
```

<span data-ttu-id="42207-109">Ces trois sections sont facultatives.</span><span class="sxs-lookup"><span data-stu-id="42207-109">All three sections are optional.</span></span> <span data-ttu-id="42207-110">Le corps de la boucle est une instruction ou un bloc d’instructions.</span><span class="sxs-lookup"><span data-stu-id="42207-110">The body of the loop is either a statement or a block of statements.</span></span>

<span data-ttu-id="42207-111">L’exemple suivant montre l’instruction `for` avec toutes les sections définies :</span><span class="sxs-lookup"><span data-stu-id="42207-111">The following example shows the `for` statement with all of the sections defined:</span></span>

[!code-csharp-interactive[for loop example](snippets/IterationKeywordsExamples.cs#5)]

### <a name="the-initializer-section"></a><span data-ttu-id="42207-112">La section *initialiseur*</span><span class="sxs-lookup"><span data-stu-id="42207-112">The *initializer* section</span></span>

<span data-ttu-id="42207-113">Les instructions figurant dans la section *initialiseur* sont exécutées une seule fois, avant d’entrer dans la boucle.</span><span class="sxs-lookup"><span data-stu-id="42207-113">The statements in the *initializer* section are executed only once, before entering the loop.</span></span> <span data-ttu-id="42207-114">La section *initialiseur* contient au choix :</span><span class="sxs-lookup"><span data-stu-id="42207-114">The *initializer* section is either of the following:</span></span>

- <span data-ttu-id="42207-115">La déclaration et l’initialisation d’une variable de boucle locale, qui n’est pas accessible à partir de l’extérieur de la boucle, ou</span><span class="sxs-lookup"><span data-stu-id="42207-115">The declaration and initialization of a local loop variable, which can't be accessed from outside the loop.</span></span>

- <span data-ttu-id="42207-116">Zéro, une ou plusieurs expressions d’instruction parmi celles de la liste suivante, séparées par des virgules :</span><span class="sxs-lookup"><span data-stu-id="42207-116">Zero or more statement expressions from the following list, separated by commas:</span></span>

  - <span data-ttu-id="42207-117">Instruction d’[assignation](../operators/assignment-operator.md)</span><span class="sxs-lookup"><span data-stu-id="42207-117">[assignment](../operators/assignment-operator.md) statement</span></span>

  - <span data-ttu-id="42207-118">Appel d’une méthode</span><span class="sxs-lookup"><span data-stu-id="42207-118">invocation of a method</span></span>

  - <span data-ttu-id="42207-119">Expression d’[incrémentation](../operators/arithmetic-operators.md#increment-operator-) préfixée ou suffixée, telle que `++i` ou `i++`</span><span class="sxs-lookup"><span data-stu-id="42207-119">prefix or postfix [increment](../operators/arithmetic-operators.md#increment-operator-) expression, such as `++i` or `i++`</span></span>

  - <span data-ttu-id="42207-120">Expression de [décrémentation](../operators/arithmetic-operators.md#decrement-operator---) préfixée ou suffixée, telle que `--i` ou `i--`</span><span class="sxs-lookup"><span data-stu-id="42207-120">prefix or postfix [decrement](../operators/arithmetic-operators.md#decrement-operator---) expression, such as `--i` or `i--`</span></span>

  - <span data-ttu-id="42207-121">Création d’un objet à l’aide de l’opérateur [new](../operators/new-operator.md)</span><span class="sxs-lookup"><span data-stu-id="42207-121">creation of an object by using the [new](../operators/new-operator.md) operator</span></span>

  - <span data-ttu-id="42207-122">Expression [await](../operators/await.md)</span><span class="sxs-lookup"><span data-stu-id="42207-122">[await](../operators/await.md) expression</span></span>

<span data-ttu-id="42207-123">La section *initialiseur* dans l’exemple ci-dessus déclare et initialise la variable de boucle locale `i` :</span><span class="sxs-lookup"><span data-stu-id="42207-123">The *initializer* section in the example above declares and initializes the local loop variable `i`:</span></span>

```csharp
int i = 0
```

### <a name="the-condition-section"></a><span data-ttu-id="42207-124">La section *condition*</span><span class="sxs-lookup"><span data-stu-id="42207-124">The *condition* section</span></span>

<span data-ttu-id="42207-125">La section *condition*, si elle est présente, doit être une expression booléenne.</span><span class="sxs-lookup"><span data-stu-id="42207-125">The *condition* section, if present, must be a boolean expression.</span></span> <span data-ttu-id="42207-126">Cette expression est évaluée avant chaque itération de boucle.</span><span class="sxs-lookup"><span data-stu-id="42207-126">That expression is evaluated before every loop iteration.</span></span> <span data-ttu-id="42207-127">Si la section *condition* est absente ou que l’expression booléenne est `true`, l’itération suivante de la boucle est exécutée ; sinon, la boucle est fermée.</span><span class="sxs-lookup"><span data-stu-id="42207-127">If the *condition* section is not present or the boolean expression evaluates to `true`, the next loop iteration is executed; otherwise, the loop is exited.</span></span>

<span data-ttu-id="42207-128">La section *condition* dans l’exemple ci-dessus détermine si la boucle se termine en fonction de la valeur de la variable de boucle locale :</span><span class="sxs-lookup"><span data-stu-id="42207-128">The *condition* section in the example above determines if the loop terminates based on the value of the local loop variable:</span></span>

```csharp
i < 5
```

### <a name="the-iterator-section"></a><span data-ttu-id="42207-129">La section *itérateur*</span><span class="sxs-lookup"><span data-stu-id="42207-129">The *iterator* section</span></span>

<span data-ttu-id="42207-130">La section *itérateur* définit ce qui se produit après chaque itération du corps de la boucle.</span><span class="sxs-lookup"><span data-stu-id="42207-130">The *iterator* section defines what happens after each iteration of the body of the loop.</span></span> <span data-ttu-id="42207-131">La section *itérateur* contient zéro, une ou plusieurs des expressions d’instruction suivantes, séparées par des virgules :</span><span class="sxs-lookup"><span data-stu-id="42207-131">The *iterator* section contains zero or more of the following statement expressions, separated by commas:</span></span>

- <span data-ttu-id="42207-132">Instruction d’[assignation](../operators/assignment-operator.md)</span><span class="sxs-lookup"><span data-stu-id="42207-132">[assignment](../operators/assignment-operator.md) statement</span></span>

- <span data-ttu-id="42207-133">Appel d’une méthode</span><span class="sxs-lookup"><span data-stu-id="42207-133">invocation of a method</span></span>

- <span data-ttu-id="42207-134">Expression d’[incrémentation](../operators/arithmetic-operators.md#increment-operator-) préfixée ou suffixée, telle que `++i` ou `i++`</span><span class="sxs-lookup"><span data-stu-id="42207-134">prefix or postfix [increment](../operators/arithmetic-operators.md#increment-operator-) expression, such as `++i` or `i++`</span></span>

- <span data-ttu-id="42207-135">Expression de [décrémentation](../operators/arithmetic-operators.md#decrement-operator---) préfixée ou suffixée, telle que `--i` ou `i--`</span><span class="sxs-lookup"><span data-stu-id="42207-135">prefix or postfix [decrement](../operators/arithmetic-operators.md#decrement-operator---) expression, such as `--i` or `i--`</span></span>

- <span data-ttu-id="42207-136">Création d’un objet à l’aide de l’opérateur [new](../operators/new-operator.md)</span><span class="sxs-lookup"><span data-stu-id="42207-136">creation of an object by using the [new](../operators/new-operator.md) operator</span></span>

- <span data-ttu-id="42207-137">Expression [await](../operators/await.md)</span><span class="sxs-lookup"><span data-stu-id="42207-137">[await](../operators/await.md) expression</span></span>

<span data-ttu-id="42207-138">La section *itérateur* dans l’exemple ci-dessus incrémente la variable de boucle locale :</span><span class="sxs-lookup"><span data-stu-id="42207-138">The *iterator* section in the example above increments the local loop variable:</span></span>

```csharp
i++
```

## <a name="examples"></a><span data-ttu-id="42207-139">Exemples</span><span class="sxs-lookup"><span data-stu-id="42207-139">Examples</span></span>

<span data-ttu-id="42207-140">L’exemple suivant illustre plusieurs utilisations moins courantes des sections d’instruction `for` : l’attribution d’une valeur à une variable de boucle externe dans la section *initialiseur*, l’appel d’une méthode dans les sections *initialiseur* et *itérateur*, et la modification des valeurs de deux variables dans la section *itérateur*.</span><span class="sxs-lookup"><span data-stu-id="42207-140">The following example illustrates several less common usages of the `for` statement sections: assigning a value to an external loop variable in the *initializer* section, invoking a method in both the *initializer* and the *iterator* sections, and changing the values of two variables in the *iterator* section.</span></span> <span data-ttu-id="42207-141">Sélectionnez **Exécuter** pour exécuter l’exemple de code.</span><span class="sxs-lookup"><span data-stu-id="42207-141">Select **Run** to run the example code.</span></span> <span data-ttu-id="42207-142">Après cela, vous pouvez modifier le code et le réexécuter.</span><span class="sxs-lookup"><span data-stu-id="42207-142">After that you can modify the code and run it again.</span></span>

[!code-csharp-interactive[not typical for loop example](snippets/IterationKeywordsExamples.cs#6)]

<span data-ttu-id="42207-143">L’exemple suivant définit la boucle `for` infinie :</span><span class="sxs-lookup"><span data-stu-id="42207-143">The following example defines the infinite `for` loop:</span></span>

[!code-csharp[infinite for loop example](snippets/IterationKeywordsExamples.cs#7)]

## <a name="c-language-specification"></a><span data-ttu-id="42207-144">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="42207-144">C# language specification</span></span>

<span data-ttu-id="42207-145">Pour plus d’informations, voir la section [Instruction for](~/_csharplang/spec/statements.md#the-for-statement) de la [spécification du langage C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="42207-145">For more information, see [The for statement](~/_csharplang/spec/statements.md#the-for-statement) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span>

## <a name="see-also"></a><span data-ttu-id="42207-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="42207-146">See also</span></span>

- [<span data-ttu-id="42207-147">Référence C#</span><span class="sxs-lookup"><span data-stu-id="42207-147">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="42207-148">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="42207-148">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="42207-149">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="42207-149">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="42207-150">foreach, in</span><span class="sxs-lookup"><span data-stu-id="42207-150">foreach, in</span></span>](foreach-in.md)
