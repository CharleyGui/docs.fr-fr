---
title: for, instruction C#
ms.date: 06/13/2018
f1_keywords:
- for
- for_CSharpKeyword
helpviewer_keywords:
- for keyword [C#]
ms.assetid: 34041a40-2c87-467a-9ffb-a0417d8f67a8
ms.openlocfilehash: 166f8a99a3556664f5f3701c94aa8593ac7ebe32
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66422081"
---
# <a name="for-c-reference"></a><span data-ttu-id="0156c-102">for (référence C#)</span><span class="sxs-lookup"><span data-stu-id="0156c-102">for (C# reference)</span></span>

<span data-ttu-id="0156c-103">L’instruction `for` exécute une instruction ou un bloc d’instructions tant qu’une expression booléenne donne la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="0156c-103">The `for` statement executes a statement or a block of statements while a specified Boolean expression evaluates to `true`.</span></span>

<span data-ttu-id="0156c-104">À tout moment dans le bloc d’instructions `for`, vous pouvez sortir de la boucle à l’aide de l’instruction [break](break.md), ou passer à l’itération suivante de la boucle à l’aide de l’instruction [continue](continue.md).</span><span class="sxs-lookup"><span data-stu-id="0156c-104">At any point within the `for` statement block, you can break out of the loop by using the [break](break.md) statement, or step to the next iteration in the loop by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="0156c-105">Vous pouvez également quitter une boucle `for` en utilisant les instructions [goto](goto.md), [return](return.md) ou [throw](throw.md).</span><span class="sxs-lookup"><span data-stu-id="0156c-105">You also can exit a `for` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="structure-of-the-for-statement"></a><span data-ttu-id="0156c-106">Structure de l’instruction `for`</span><span class="sxs-lookup"><span data-stu-id="0156c-106">Structure of the `for` statement</span></span>

<span data-ttu-id="0156c-107">Chaque instruction `for` définit des sections *initialiseur*, *condition* et *itérateur* :</span><span class="sxs-lookup"><span data-stu-id="0156c-107">The `for` statement defines *initializer*, *condition*, and *iterator* sections:</span></span>

```csharp
for (initializer; condition; iterator)
    body
```

<span data-ttu-id="0156c-108">Ces trois sections sont facultatives.</span><span class="sxs-lookup"><span data-stu-id="0156c-108">All three sections are optional.</span></span> <span data-ttu-id="0156c-109">Le corps de la boucle est une instruction ou un bloc d’instructions.</span><span class="sxs-lookup"><span data-stu-id="0156c-109">The body of the loop is either a statement or a block of statements.</span></span>

<span data-ttu-id="0156c-110">L’exemple suivant montre l’instruction `for` avec toutes les sections définies :</span><span class="sxs-lookup"><span data-stu-id="0156c-110">The following example shows the `for` statement with all of the sections defined:</span></span>

[!code-csharp-interactive[for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#5)]

### <a name="the-initializer-section"></a><span data-ttu-id="0156c-111">La section *initialiseur*</span><span class="sxs-lookup"><span data-stu-id="0156c-111">The *initializer* section</span></span>

<span data-ttu-id="0156c-112">Les instructions figurant dans la section *initialiseur* sont exécutées une seule fois, avant d’entrer dans la boucle.</span><span class="sxs-lookup"><span data-stu-id="0156c-112">The statements in the *initializer* section are executed only once, before entering the loop.</span></span> <span data-ttu-id="0156c-113">La section *initialiseur* contient au choix :</span><span class="sxs-lookup"><span data-stu-id="0156c-113">The *initializer* section is either of the following:</span></span>

- <span data-ttu-id="0156c-114">La déclaration et l’initialisation d’une variable de boucle locale, qui n’est pas accessible à partir de l’extérieur de la boucle, ou</span><span class="sxs-lookup"><span data-stu-id="0156c-114">The declaration and initialization of a local loop variable, which can't be accessed from outside the loop.</span></span>

- <span data-ttu-id="0156c-115">Zéro, une ou plusieurs expressions d’instruction parmi celles de la liste suivante, séparées par des virgules :</span><span class="sxs-lookup"><span data-stu-id="0156c-115">Zero or more statement expressions from the following list, separated by commas:</span></span>

  - <span data-ttu-id="0156c-116">Instruction d’[assignation](../operators/assignment-operator.md)</span><span class="sxs-lookup"><span data-stu-id="0156c-116">[assignment](../operators/assignment-operator.md) statement</span></span>

  - <span data-ttu-id="0156c-117">Appel d’une méthode</span><span class="sxs-lookup"><span data-stu-id="0156c-117">invocation of a method</span></span>

  - <span data-ttu-id="0156c-118">Expression d’[incrémentation](../operators/arithmetic-operators.md#increment-operator-) préfixée ou suffixée, telle que `++i` ou `i++`</span><span class="sxs-lookup"><span data-stu-id="0156c-118">prefix or postfix [increment](../operators/arithmetic-operators.md#increment-operator-) expression, such as `++i` or `i++`</span></span>

  - <span data-ttu-id="0156c-119">Expression de [décrémentation](../operators/arithmetic-operators.md#decrement-operator---) préfixée ou suffixée, telle que `--i` ou `i--`</span><span class="sxs-lookup"><span data-stu-id="0156c-119">prefix or postfix [decrement](../operators/arithmetic-operators.md#decrement-operator---) expression, such as `--i` or `i--`</span></span>

  - <span data-ttu-id="0156c-120">Création d’un objet à l’aide du mot clé [new](new-operator.md)</span><span class="sxs-lookup"><span data-stu-id="0156c-120">creation of an object by using [new](new-operator.md) keyword</span></span>

  - <span data-ttu-id="0156c-121">Expression [await](await.md)</span><span class="sxs-lookup"><span data-stu-id="0156c-121">[await](await.md) expression</span></span>

<span data-ttu-id="0156c-122">La section *initialiseur* dans l’exemple ci-dessus déclare et initialise la variable de boucle locale `i` :</span><span class="sxs-lookup"><span data-stu-id="0156c-122">The *initializer* section in the example above declares and initializes the local loop variable `i`:</span></span>

```csharp
int i = 0
```

### <a name="the-condition-section"></a><span data-ttu-id="0156c-123">La section *condition*</span><span class="sxs-lookup"><span data-stu-id="0156c-123">The *condition* section</span></span>

<span data-ttu-id="0156c-124">La section *condition*, si elle est présente, doit être une expression booléenne.</span><span class="sxs-lookup"><span data-stu-id="0156c-124">The *condition* section, if present, must be a boolean expression.</span></span> <span data-ttu-id="0156c-125">Cette expression est évaluée avant chaque itération de boucle.</span><span class="sxs-lookup"><span data-stu-id="0156c-125">That expression is evaluated before every loop iteration.</span></span> <span data-ttu-id="0156c-126">Si la section *condition* est absente ou que l’expression booléenne est `true`, l’itération suivante de la boucle est exécutée ; sinon, la boucle est fermée.</span><span class="sxs-lookup"><span data-stu-id="0156c-126">If the *condition* section is not present or the boolean expression evaluates to `true`, the next loop iteration is executed; otherwise, the loop is exited.</span></span>

<span data-ttu-id="0156c-127">La section *condition* dans l’exemple ci-dessus détermine si la boucle se termine en fonction de la valeur de la variable de boucle locale :</span><span class="sxs-lookup"><span data-stu-id="0156c-127">The *condition* section in the example above determines if the loop terminates based on the value of the local loop variable:</span></span>

```csharp
i < 5
```

### <a name="the-iterator-section"></a><span data-ttu-id="0156c-128">La section *itérateur*</span><span class="sxs-lookup"><span data-stu-id="0156c-128">The *iterator* section</span></span>

<span data-ttu-id="0156c-129">La section *itérateur* définit ce qui se produit après chaque itération du corps de la boucle.</span><span class="sxs-lookup"><span data-stu-id="0156c-129">The *iterator* section defines what happens after each iteration of the body of the loop.</span></span> <span data-ttu-id="0156c-130">La section *itérateur* contient zéro, une ou plusieurs des expressions d’instruction suivantes, séparées par des virgules :</span><span class="sxs-lookup"><span data-stu-id="0156c-130">The *iterator* section contains zero or more of the following statement expressions, separated by commas:</span></span>

- <span data-ttu-id="0156c-131">Instruction d’[assignation](../operators/assignment-operator.md)</span><span class="sxs-lookup"><span data-stu-id="0156c-131">[assignment](../operators/assignment-operator.md) statement</span></span>

- <span data-ttu-id="0156c-132">Appel d’une méthode</span><span class="sxs-lookup"><span data-stu-id="0156c-132">invocation of a method</span></span>

- <span data-ttu-id="0156c-133">Expression d’[incrémentation](../operators/arithmetic-operators.md#increment-operator-) préfixée ou suffixée, telle que `++i` ou `i++`</span><span class="sxs-lookup"><span data-stu-id="0156c-133">prefix or postfix [increment](../operators/arithmetic-operators.md#increment-operator-) expression, such as `++i` or `i++`</span></span>

- <span data-ttu-id="0156c-134">Expression de [décrémentation](../operators/arithmetic-operators.md#decrement-operator---) préfixée ou suffixée, telle que `--i` ou `i--`</span><span class="sxs-lookup"><span data-stu-id="0156c-134">prefix or postfix [decrement](../operators/arithmetic-operators.md#decrement-operator---) expression, such as `--i` or `i--`</span></span>

- <span data-ttu-id="0156c-135">Création d’un objet à l’aide du mot clé [new](new-operator.md)</span><span class="sxs-lookup"><span data-stu-id="0156c-135">creation of an object by using [new](new-operator.md) keyword</span></span>

- <span data-ttu-id="0156c-136">Expression [await](await.md)</span><span class="sxs-lookup"><span data-stu-id="0156c-136">[await](await.md) expression</span></span>

<span data-ttu-id="0156c-137">La section *itérateur* dans l’exemple ci-dessus incrémente la variable de boucle locale :</span><span class="sxs-lookup"><span data-stu-id="0156c-137">The *iterator* section in the example above increments the local loop variable:</span></span>

```csharp
i++
```

## <a name="examples"></a><span data-ttu-id="0156c-138">Exemples</span><span class="sxs-lookup"><span data-stu-id="0156c-138">Examples</span></span>

<span data-ttu-id="0156c-139">L’exemple suivant illustre plusieurs utilisations moins courantes des sections d’instruction `for` : l’attribution d’une valeur à une variable de boucle externe dans la section *initialiseur*, l’appel d’une méthode dans les sections *initialiseur* et *itérateur*, et la modification des valeurs de deux variables dans la section *itérateur*.</span><span class="sxs-lookup"><span data-stu-id="0156c-139">The following example illustrates several less common usages of the `for` statement sections: assigning a value to an external loop variable in the *initializer* section, invoking a method in both the *initializer* and the *iterator* sections, and changing the values of two variables in the *iterator* section.</span></span> <span data-ttu-id="0156c-140">Sélectionnez **Exécuter** pour exécuter l’exemple de code.</span><span class="sxs-lookup"><span data-stu-id="0156c-140">Select **Run** to run the example code.</span></span> <span data-ttu-id="0156c-141">Après cela, vous pouvez modifier le code et le réexécuter.</span><span class="sxs-lookup"><span data-stu-id="0156c-141">After that you can modify the code and run it again.</span></span>

[!code-csharp-interactive[not typical for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#6)]

<span data-ttu-id="0156c-142">L’exemple suivant définit la boucle `for` infinie :</span><span class="sxs-lookup"><span data-stu-id="0156c-142">The following example defines the infinite `for` loop:</span></span>

[!code-csharp[infinite for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#7)]

## <a name="c-language-specification"></a><span data-ttu-id="0156c-143">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="0156c-143">C# language specification</span></span>

<span data-ttu-id="0156c-144">Pour plus d’informations, voir la section [Instruction for](~/_csharplang/spec/statements.md#the-for-statement) de la [spécification du langage C#](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="0156c-144">For more information, see [The for statement](~/_csharplang/spec/statements.md#the-for-statement) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0156c-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0156c-145">See also</span></span>

- [<span data-ttu-id="0156c-146">Référence C#</span><span class="sxs-lookup"><span data-stu-id="0156c-146">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="0156c-147">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="0156c-147">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="0156c-148">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="0156c-148">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="0156c-149">foreach, in</span><span class="sxs-lookup"><span data-stu-id="0156c-149">foreach, in</span></span>](foreach-in.md)
