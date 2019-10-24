---
title: bool, mot clé - Référence C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- bool_CSharpKeyword
- bool
helpviewer_keywords:
- bool keyword [C#]
ms.assetid: 551cfe35-2632-4343-af49-33ad12da08e2
ms.openlocfilehash: 880e8c0b733afbf5c09f543e06a5a4a858d2b456
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72771846"
---
# <a name="bool-c-reference"></a><span data-ttu-id="913cb-102">bool (référence C#)</span><span class="sxs-lookup"><span data-stu-id="913cb-102">bool (C# Reference)</span></span>

<span data-ttu-id="913cb-103">Le mot clé `bool` est un alias de <xref:System.Boolean?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="913cb-103">The `bool` keyword is an alias of <xref:System.Boolean?displayProperty=nameWithType>.</span></span> <span data-ttu-id="913cb-104">Il sert à déclarer des variables qui stockent les valeurs booléennes : [true](true-literal.md) et [false](false-literal.md).</span><span class="sxs-lookup"><span data-stu-id="913cb-104">It is used to declare variables to store the Boolean values: [true](true-literal.md) and [false](false-literal.md).</span></span>

> [!NOTE]
> <span data-ttu-id="913cb-105">Utilisez le type `bool?` si vous voulez suivre une logique à trois valeurs, par exemple pour travailler avec des bases de données qui acceptent un type booléen à trois valeurs.</span><span class="sxs-lookup"><span data-stu-id="913cb-105">Use the `bool?` type, if you need to support the three-valued logic, for example, when you work with databases that support a three-valued Boolean type.</span></span> <span data-ttu-id="913cb-106">Dans le cas des opérandes `bool?`, les opérateurs prédéfinis `&` et `|` prennent en charge la logique à trois valeurs.</span><span class="sxs-lookup"><span data-stu-id="913cb-106">For the `bool?` operands, the predefined `&` and `|` operators support the three-valued logic.</span></span> <span data-ttu-id="913cb-107">Pour plus d’informations, voir la section [Opérateurs logiques booléens Nullable](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) de l’article [Opérateurs logiques booléens](../operators/boolean-logical-operators.md).</span><span class="sxs-lookup"><span data-stu-id="913cb-107">For more information, see the [Nullable Boolean logical operators](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) section of the [Boolean logical operators](../operators/boolean-logical-operators.md) article.</span></span>

## <a name="literals"></a><span data-ttu-id="913cb-108">Littéraux</span><span class="sxs-lookup"><span data-stu-id="913cb-108">Literals</span></span>

<span data-ttu-id="913cb-109">Vous pouvez assigner une valeur booléenne à une variable `bool`.</span><span class="sxs-lookup"><span data-stu-id="913cb-109">You can assign a Boolean value to a `bool` variable.</span></span> <span data-ttu-id="913cb-110">Vous pouvez également assigner à une variable `bool` une expression dont le résultat est une valeur `bool`.</span><span class="sxs-lookup"><span data-stu-id="913cb-110">You can also assign an expression that evaluates to `bool` to a `bool` variable.</span></span>

[!code-csharp[csrefKeywordsTypes#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#1)]

<span data-ttu-id="913cb-111">La valeur par défaut d’une variable `bool` est `false`.</span><span class="sxs-lookup"><span data-stu-id="913cb-111">The default value of a `bool` variable is `false`.</span></span> <span data-ttu-id="913cb-112">La valeur par défaut d’une variable `bool?` est `null`.</span><span class="sxs-lookup"><span data-stu-id="913cb-112">The default value of a `bool?` variable is `null`.</span></span>

## <a name="conversions"></a><span data-ttu-id="913cb-113">Conversions</span><span class="sxs-lookup"><span data-stu-id="913cb-113">Conversions</span></span>

<span data-ttu-id="913cb-114">Dans C++, une valeur de type `bool` peut être convertie en une valeur de type `int`. En d’autres termes, `false` équivaut à zéro et `true` équivaut à une valeur différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="913cb-114">In C++, a value of type `bool` can be converted to a value of type `int`; in other words, `false` is equivalent to zero and `true` is equivalent to nonzero values.</span></span> <span data-ttu-id="913cb-115">Dans C#, il n’y a pas de conversion possible entre le type `bool` et les autres types.</span><span class="sxs-lookup"><span data-stu-id="913cb-115">In C#, there is no conversion between the `bool` type and other types.</span></span> <span data-ttu-id="913cb-116">Par exemple, l’instruction `if` suivante n’est pas valide dans C# :</span><span class="sxs-lookup"><span data-stu-id="913cb-116">For example, the following `if` statement is invalid in C#:</span></span>

[!code-csharp[csrefKeywordsTypes#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#2)]

<span data-ttu-id="913cb-117">Pour tester une variable du type `int`, vous devez la comparer explicitement à une valeur, telle que zéro, comme suit :</span><span class="sxs-lookup"><span data-stu-id="913cb-117">To test a variable of the type `int`, you have to explicitly compare it to a value, such as zero, as follows:</span></span>

[!code-csharp[csrefKeywordsTypes#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#3)]

## <a name="example"></a><span data-ttu-id="913cb-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="913cb-118">Example</span></span>

<span data-ttu-id="913cb-119">Dans cet exemple, vous tapez un caractère, et le programme vérifie si le caractère entré est une lettre.</span><span class="sxs-lookup"><span data-stu-id="913cb-119">In this example, you enter a character from the keyboard and the program checks if the input character is a letter.</span></span> <span data-ttu-id="913cb-120">Si c’est une lettre, le programme vérifie s’il s’agit d’une minuscule ou d’une majuscule.</span><span class="sxs-lookup"><span data-stu-id="913cb-120">If it is a letter, it checks if it is lowercase or uppercase.</span></span> <span data-ttu-id="913cb-121">Ces vérifications sont effectuées avec les méthodes <xref:System.Char.IsLetter%2A>, et <xref:System.Char.IsLower%2A>, qui retournent toutes les deux le type `bool` :</span><span class="sxs-lookup"><span data-stu-id="913cb-121">These checks are performed with the <xref:System.Char.IsLetter%2A>, and <xref:System.Char.IsLower%2A>, both of which return the `bool` type:</span></span>

[!code-csharp[csrefKeywordsTypes#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#4)]

## <a name="c-language-specification"></a><span data-ttu-id="913cb-122">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="913cb-122">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="913cb-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="913cb-123">See also</span></span>

- [<span data-ttu-id="913cb-124">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="913cb-124">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="913cb-125">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="913cb-125">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="913cb-126">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="913cb-126">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="913cb-127">Types intégraux</span><span class="sxs-lookup"><span data-stu-id="913cb-127">Integral types</span></span>](../builtin-types/integral-numeric-types.md)
- [<span data-ttu-id="913cb-128">Tableau des types intégrés</span><span class="sxs-lookup"><span data-stu-id="913cb-128">Built-In Types Table</span></span>](./built-in-types-table.md)
