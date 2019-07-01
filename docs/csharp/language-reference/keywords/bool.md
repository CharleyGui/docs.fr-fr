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
ms.openlocfilehash: a6aae34433ee6f5d141d95f0c434af1825e9bf4b
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67424435"
---
# <a name="bool-c-reference"></a><span data-ttu-id="ab0d0-102">bool (référence C#)</span><span class="sxs-lookup"><span data-stu-id="ab0d0-102">bool (C# Reference)</span></span>

<span data-ttu-id="ab0d0-103">Le mot clé `bool` est un alias de <xref:System.Boolean?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ab0d0-103">The `bool` keyword is an alias of <xref:System.Boolean?displayProperty=nameWithType>.</span></span> <span data-ttu-id="ab0d0-104">Il sert à déclarer des variables qui stockent les valeurs booléennes : [true](true-literal.md) et [false](false-literal.md).</span><span class="sxs-lookup"><span data-stu-id="ab0d0-104">It is used to declare variables to store the Boolean values: [true](true-literal.md) and [false](false-literal.md).</span></span>

> [!NOTE]
> <span data-ttu-id="ab0d0-105">Utilisez le type `bool?` si vous voulez suivre une logique à trois valeurs, par exemple pour travailler avec des bases de données qui acceptent un type booléen à trois valeurs.</span><span class="sxs-lookup"><span data-stu-id="ab0d0-105">Use the `bool?` type, if you need to support the three-valued logic, for example, when you work with databases that support a three-valued Boolean type.</span></span> <span data-ttu-id="ab0d0-106">Dans le cas des opérandes `bool?`, les opérateurs prédéfinis `&` et `|` prennent en charge la logique à trois valeurs.</span><span class="sxs-lookup"><span data-stu-id="ab0d0-106">For the `bool?` operands, the predefined `&` and `|` operators support the three-valued logic.</span></span> <span data-ttu-id="ab0d0-107">Pour plus d’informations, voir la section [Opérateurs logiques booléens Nullable](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) de l’article [Opérateurs logiques booléens](../operators/boolean-logical-operators.md).</span><span class="sxs-lookup"><span data-stu-id="ab0d0-107">For more information, see the [Nullable Boolean logical operators](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) section of the [Boolean logical operators](../operators/boolean-logical-operators.md) article.</span></span>

## <a name="literals"></a><span data-ttu-id="ab0d0-108">Littéraux</span><span class="sxs-lookup"><span data-stu-id="ab0d0-108">Literals</span></span>

<span data-ttu-id="ab0d0-109">Vous pouvez assigner une valeur booléenne à une variable `bool`.</span><span class="sxs-lookup"><span data-stu-id="ab0d0-109">You can assign a Boolean value to a `bool` variable.</span></span> <span data-ttu-id="ab0d0-110">Vous pouvez également assigner à une variable `bool` une expression dont le résultat est une valeur `bool`.</span><span class="sxs-lookup"><span data-stu-id="ab0d0-110">You can also assign an expression that evaluates to `bool` to a `bool` variable.</span></span>

[!code-csharp[csrefKeywordsTypes#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#1)]

<span data-ttu-id="ab0d0-111">La valeur par défaut d’une variable `bool` est `false`.</span><span class="sxs-lookup"><span data-stu-id="ab0d0-111">The default value of a `bool` variable is `false`.</span></span> <span data-ttu-id="ab0d0-112">La valeur par défaut d’une variable `bool?` est `null`.</span><span class="sxs-lookup"><span data-stu-id="ab0d0-112">The default value of a `bool?` variable is `null`.</span></span>

## <a name="conversions"></a><span data-ttu-id="ab0d0-113">Conversions</span><span class="sxs-lookup"><span data-stu-id="ab0d0-113">Conversions</span></span>

<span data-ttu-id="ab0d0-114">Dans C++, une valeur de type `bool` peut être convertie en une valeur de type `int`. En d’autres termes, `false` équivaut à zéro et `true` équivaut à une valeur différente de zéro.</span><span class="sxs-lookup"><span data-stu-id="ab0d0-114">In C++, a value of type `bool` can be converted to a value of type `int`; in other words, `false` is equivalent to zero and `true` is equivalent to nonzero values.</span></span> <span data-ttu-id="ab0d0-115">Dans C#, il n’y a pas de conversion possible entre le type `bool` et les autres types.</span><span class="sxs-lookup"><span data-stu-id="ab0d0-115">In C#, there is no conversion between the `bool` type and other types.</span></span> <span data-ttu-id="ab0d0-116">Par exemple, l’instruction `if` suivante n’est pas valide dans C# :</span><span class="sxs-lookup"><span data-stu-id="ab0d0-116">For example, the following `if` statement is invalid in C#:</span></span>

[!code-csharp[csrefKeywordsTypes#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#2)]

<span data-ttu-id="ab0d0-117">Pour tester une variable du type `int`, vous devez la comparer explicitement à une valeur, telle que zéro, comme suit :</span><span class="sxs-lookup"><span data-stu-id="ab0d0-117">To test a variable of the type `int`, you have to explicitly compare it to a value, such as zero, as follows:</span></span>

[!code-csharp[csrefKeywordsTypes#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#3)]

## <a name="example"></a><span data-ttu-id="ab0d0-118">Exemples</span><span class="sxs-lookup"><span data-stu-id="ab0d0-118">Example</span></span>

<span data-ttu-id="ab0d0-119">Dans cet exemple, vous tapez un caractère, et le programme vérifie si le caractère entré est une lettre.</span><span class="sxs-lookup"><span data-stu-id="ab0d0-119">In this example, you enter a character from the keyboard and the program checks if the input character is a letter.</span></span> <span data-ttu-id="ab0d0-120">Si c’est une lettre, le programme vérifie s’il s’agit d’une minuscule ou d’une majuscule.</span><span class="sxs-lookup"><span data-stu-id="ab0d0-120">If it is a letter, it checks if it is lowercase or uppercase.</span></span> <span data-ttu-id="ab0d0-121">Ces vérifications sont effectuées avec les méthodes <xref:System.Char.IsLetter%2A>, et <xref:System.Char.IsLower%2A>, qui retournent toutes les deux le type `bool` :</span><span class="sxs-lookup"><span data-stu-id="ab0d0-121">These checks are performed with the <xref:System.Char.IsLetter%2A>, and <xref:System.Char.IsLower%2A>, both of which return the `bool` type:</span></span>

[!code-csharp[csrefKeywordsTypes#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#4)]

## <a name="c-language-specification"></a><span data-ttu-id="ab0d0-122">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="ab0d0-122">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="ab0d0-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ab0d0-123">See also</span></span>

- [<span data-ttu-id="ab0d0-124">Référence C#</span><span class="sxs-lookup"><span data-stu-id="ab0d0-124">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="ab0d0-125">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="ab0d0-125">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="ab0d0-126">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="ab0d0-126">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
- [<span data-ttu-id="ab0d0-127">Types intégraux</span><span class="sxs-lookup"><span data-stu-id="ab0d0-127">Integral types</span></span>](../../../csharp/language-reference/builtin-types/integral-numeric-types.md)
- [<span data-ttu-id="ab0d0-128">Tableau des types intégrés</span><span class="sxs-lookup"><span data-stu-id="ab0d0-128">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)
- [<span data-ttu-id="ab0d0-129">Tableau des conversions numériques implicites</span><span class="sxs-lookup"><span data-stu-id="ab0d0-129">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)
- [<span data-ttu-id="ab0d0-130">Tableau des conversions numériques explicites</span><span class="sxs-lookup"><span data-stu-id="ab0d0-130">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
