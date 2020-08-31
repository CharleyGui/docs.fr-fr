---
description: if-else - Référence C#
title: if-else - Référence C#
ms.date: 07/20/2015
f1_keywords:
- if_CSharpKeyword
- else
- else_CSharpKeyword
- if
helpviewer_keywords:
- else keyword [C#]
- if keyword [C#]
ms.assetid: d9a1d562-8cf5-4bd4-9ba7-8ad970cd25b2
ms.openlocfilehash: e2de84807a049bd47ea277db9fb010d0c2e4857d
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89118505"
---
# <a name="if-else-c-reference"></a><span data-ttu-id="07637-103">if-else (référence C#)</span><span class="sxs-lookup"><span data-stu-id="07637-103">if-else (C# Reference)</span></span>

<span data-ttu-id="07637-104">Une instruction `if` identifie l’instruction à exécuter en fonction de la valeur d’une expression booléenne.</span><span class="sxs-lookup"><span data-stu-id="07637-104">An `if` statement identifies which statement to run based on the value of a Boolean expression.</span></span> <span data-ttu-id="07637-105">Dans l’exemple suivant, la variable `bool``condition` est définie sur `true` puis archivé dans l’instruction `if` .</span><span class="sxs-lookup"><span data-stu-id="07637-105">In the following example, the `bool` variable `condition` is set to `true` and then checked in the `if` statement.</span></span> <span data-ttu-id="07637-106">La sortie est `The variable is set to true.`.</span><span class="sxs-lookup"><span data-stu-id="07637-106">The output is `The variable is set to true.`.</span></span>

[!code-csharp[csrefKeywordsSelection#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#1)]

<span data-ttu-id="07637-107">Vous pouvez exécuter les exemples de cette rubrique en les plaçant dans la méthode `Main` d’une application console.</span><span class="sxs-lookup"><span data-stu-id="07637-107">You can run the examples in this topic by placing them in the `Main` method of a console app.</span></span>

<span data-ttu-id="07637-108">En C#, une instruction `if` peut prendre deux formes, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="07637-108">An `if` statement in C# can take two forms, as the following example shows.</span></span>

```csharp
// if-else statement
if (condition)
{
    then-statement;
}
else
{
    else-statement;
}
// Next statement in the program.

// if statement without an else
if (condition)
{
    then-statement;
}
// Next statement in the program.
```

<span data-ttu-id="07637-109">Dans une instruction `if-else` , si `condition` a la valeur true, `then-statement` s’exécute.</span><span class="sxs-lookup"><span data-stu-id="07637-109">In an `if-else` statement, if `condition` evaluates to true, the `then-statement` runs.</span></span> <span data-ttu-id="07637-110">Si `condition` a la valeur false, `else-statement` s’exécute.</span><span class="sxs-lookup"><span data-stu-id="07637-110">If `condition` is false, the `else-statement` runs.</span></span> <span data-ttu-id="07637-111">Sachant que `condition` ne peut pas avoir simultanément les valeurs true et false, `then-statement` et `else-statement` d’une instruction `if-else` ne peuvent jamais s’exécuter.</span><span class="sxs-lookup"><span data-stu-id="07637-111">Because `condition` can’t be simultaneously true and false, the `then-statement` and the `else-statement` of an `if-else` statement can never both run.</span></span> <span data-ttu-id="07637-112">Une fois que `then-statement` ou `else-statement` s’est exécuté, le contrôle est transféré à l’instruction suivante après l’instruction `if` .</span><span class="sxs-lookup"><span data-stu-id="07637-112">After the `then-statement` or the `else-statement` runs, control is transferred to the next statement after the `if` statement.</span></span>

<span data-ttu-id="07637-113">Dans une instruction `if` qui n’inclut pas d’instruction `else` , si `condition` a la valeur true, `then-statement` s’exécute.</span><span class="sxs-lookup"><span data-stu-id="07637-113">In an `if` statement that doesn’t include an `else` statement, if `condition` is true, the `then-statement` runs.</span></span> <span data-ttu-id="07637-114">Si `condition` a la valeur false, le contrôle est transféré à l’instruction suivante après l’instruction `if` .</span><span class="sxs-lookup"><span data-stu-id="07637-114">If `condition` is false, control is transferred to the next statement after the `if` statement.</span></span>

<span data-ttu-id="07637-115">`then-statement` et `else-statement` peuvent tous deux être constitués d’une ou plusieurs instructions placées entre accolades (`{}`).</span><span class="sxs-lookup"><span data-stu-id="07637-115">Both the `then-statement` and the `else-statement` can consist of a single statement or multiple statements that are enclosed in braces (`{}`).</span></span> <span data-ttu-id="07637-116">Pour une seule instruction, les accolades sont facultatives, mais recommandées.</span><span class="sxs-lookup"><span data-stu-id="07637-116">For a single statement, the braces are optional but recommended.</span></span>

<span data-ttu-id="07637-117">La ou les instructions contenues dans `then-statement` et `else-statement` peuvent être de n’importe quel type, y compris une autre instruction `if` imbriquée à l’intérieur de l’instruction `if` d’origine.</span><span class="sxs-lookup"><span data-stu-id="07637-117">The statement or statements in the `then-statement` and the `else-statement` can be of any kind, including another `if` statement nested inside the original `if` statement.</span></span> <span data-ttu-id="07637-118">Dans les instructions `if` imbriquées, chaque clause `else` appartient à la dernière instruction `if` qui n’a pas d’instruction `else`correspondante.</span><span class="sxs-lookup"><span data-stu-id="07637-118">In nested `if` statements, each `else` clause belongs to the last `if` that doesn’t have a corresponding `else`.</span></span> <span data-ttu-id="07637-119">Dans l’exemple suivant, `Result1` s’affiche si `m > 10` et `n > 20` ont tous deux la valeur true.</span><span class="sxs-lookup"><span data-stu-id="07637-119">In the following example, `Result1` appears if both `m > 10` and `n > 20` evaluate to true.</span></span> <span data-ttu-id="07637-120">Si `m > 10` a la valeur true, mais que `n > 20` a la valeur false, `Result2` s’affiche.</span><span class="sxs-lookup"><span data-stu-id="07637-120">If `m > 10` is true but `n > 20` is false, `Result2` appears.</span></span>

[!code-csharp[csrefKeywordsSelection#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#2)]

<span data-ttu-id="07637-121">Si vous préférez que `Result2` s’affiche quand `(m > 10)` a la valeur false, vous pouvez spécifier cette association au moyen d’accolades pour établir le début et la fin de l’instruction `if` imbriquée, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="07637-121">If, instead, you want `Result2` to appear when `(m > 10)` is false, you can specify that association by using braces to establish the start and end of the nested `if` statement, as the following example shows.</span></span>

[!code-csharp[csrefKeywordsSelection#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#3)]

<span data-ttu-id="07637-122">`Result2` s’affiche si la condition `(m > 10)` a la valeur false.</span><span class="sxs-lookup"><span data-stu-id="07637-122">`Result2` appears if the condition `(m > 10)` evaluates to false.</span></span>

## <a name="example"></a><span data-ttu-id="07637-123">Exemple</span><span class="sxs-lookup"><span data-stu-id="07637-123">Example</span></span>

<span data-ttu-id="07637-124">Dans l’exemple suivant, vous entrez un caractère au clavier et le programme utilise une instruction `if` imbriquée pour déterminer si le caractère d’entrée est un caractère alphabétique.</span><span class="sxs-lookup"><span data-stu-id="07637-124">In the following example, you enter a character from the keyboard, and the program uses a nested `if` statement to determine whether the input character is an alphabetic character.</span></span> <span data-ttu-id="07637-125">Si le caractère d’entrée est un caractère alphabétique, le programme vérifie si c’est une minuscule ou une majuscule.</span><span class="sxs-lookup"><span data-stu-id="07637-125">If the input character is an alphabetic character, the program checks whether the input character is lowercase or uppercase.</span></span> <span data-ttu-id="07637-126">Un message s’affiche dans chaque cas.</span><span class="sxs-lookup"><span data-stu-id="07637-126">A message appears for each case.</span></span>

[!code-csharp[csrefKeywordsSelection#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#4)]

## <a name="example"></a><span data-ttu-id="07637-127">Exemple</span><span class="sxs-lookup"><span data-stu-id="07637-127">Example</span></span>

<span data-ttu-id="07637-128">Vous pouvez également imbriquer une `if` instruction à l’intérieur d’un bloc Else, comme le montre le code partiel suivant.</span><span class="sxs-lookup"><span data-stu-id="07637-128">You can also nest an `if` statement inside an else block, as the following partial code shows.</span></span> <span data-ttu-id="07637-129">L’exemple imbrique des instructions `if` à l’intérieur de deux blocs « else » et d’un bloc « then ».</span><span class="sxs-lookup"><span data-stu-id="07637-129">The example nests `if` statements inside two else blocks and one then block.</span></span> <span data-ttu-id="07637-130">Les commentaires précisent les conditions qui sont vraies (true) et celles qui sont fausses (false) dans chaque bloc.</span><span class="sxs-lookup"><span data-stu-id="07637-130">The comments specify which conditions are true or false in each block.</span></span>

[!code-csharp[csrefKeywordsSelection#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#5)]

## <a name="example"></a><span data-ttu-id="07637-131">Exemple</span><span class="sxs-lookup"><span data-stu-id="07637-131">Example</span></span>

<span data-ttu-id="07637-132">L’exemple suivant détermine si un caractère d’entrée est une lettre minuscule, une lettre majuscule ou un nombre.</span><span class="sxs-lookup"><span data-stu-id="07637-132">The following example determines whether an input character is a lowercase letter, an uppercase letter, or a number.</span></span> <span data-ttu-id="07637-133">Si ces trois conditions ont la valeur false, le caractère n’est pas un caractère alphanumérique.</span><span class="sxs-lookup"><span data-stu-id="07637-133">If all three conditions are false, the character isn’t an alphanumeric character.</span></span> <span data-ttu-id="07637-134">L’exemple affiche un message dans chaque cas.</span><span class="sxs-lookup"><span data-stu-id="07637-134">The example displays a message for each case.</span></span>

[!code-csharp[csrefKeywordsSelection#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#6)]

<span data-ttu-id="07637-135">De la même manière que le bloc « else » ou le bloc « then » peuvent contenir n’importe quelle instruction valide, vous pouvez utiliser n’importe quelle expression booléenne valide pour la condition.</span><span class="sxs-lookup"><span data-stu-id="07637-135">Just as a statement in the else block or the then block can be any valid statement, you can use any valid Boolean expression for the condition.</span></span> <span data-ttu-id="07637-136">Vous pouvez utiliser des [opérateurs logiques](../operators/boolean-logical-operators.md) tels que `!` ,,,, `&&` `||` `&` `|` et `^` pour créer des conditions composées.</span><span class="sxs-lookup"><span data-stu-id="07637-136">You can use [logical operators](../operators/boolean-logical-operators.md) such as `!`, `&&`, `||`, `&`, `|`, and `^` to make compound conditions.</span></span> <span data-ttu-id="07637-137">Le code suivant présente des exemples.</span><span class="sxs-lookup"><span data-stu-id="07637-137">The following code shows examples.</span></span>

```csharp
// NOT
bool result = true;
if (!result)
{
    Console.WriteLine("The condition is true (result is false).");
}
else
{
    Console.WriteLine("The condition is false (result is true).");
}

// Short-circuit AND
int m = 9;
int n = 7;
int p = 5;
if (m >= n && m >= p)
{
    Console.WriteLine("Nothing is larger than m.");
}

// AND and NOT
if (m >= n && !(p > m))
{
    Console.WriteLine("Nothing is larger than m.");
}

// Short-circuit OR
if (m > n || m > p)
{
    Console.WriteLine("m isn't the smallest.");
}

// NOT and OR
m = 4;
if (!(m >= n || m >= p))
{
    Console.WriteLine("Now m is the smallest.");
}
// Output:
// The condition is false (result is true).
// Nothing is larger than m.
// Nothing is larger than m.
// m isn't the smallest.
// Now m is the smallest.
```

## <a name="c-language-specification"></a><span data-ttu-id="07637-138">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="07637-138">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="07637-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="07637-139">See also</span></span>

- [<span data-ttu-id="07637-140">Référence C#</span><span class="sxs-lookup"><span data-stu-id="07637-140">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="07637-141">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="07637-141">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="07637-142">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="07637-142">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="07637-143">?:, Opérateur</span><span class="sxs-lookup"><span data-stu-id="07637-143">?: Operator</span></span>](../operators/conditional-operator.md)
- [<span data-ttu-id="07637-144">if-else, instruction (C++)</span><span class="sxs-lookup"><span data-stu-id="07637-144">if-else Statement (C++)</span></span>](/cpp/cpp/if-else-statement-cpp)
- [<span data-ttu-id="07637-145">switch</span><span class="sxs-lookup"><span data-stu-id="07637-145">switch</span></span>](switch.md)
