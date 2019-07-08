---
title: explicit, mot clé - Référence C#
ms.custom: seodec18
ms.date: 08/24/2018
f1_keywords:
- explicit_CSharpKeyword
- explicit
helpviewer_keywords:
- explicit keyword [C#]
ms.assetid: cfb8f42a-e411-4db2-af9b-796b05644846
ms.openlocfilehash: a260c6f1ccac6e09770f1cb8f43d5d872b4b2650
ms.sourcegitcommit: eaa6d5cd0f4e7189dbe0bd756e9f53508b01989e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2019
ms.locfileid: "67610103"
---
# <a name="explicit-c-reference"></a><span data-ttu-id="2bb3c-102">explicit (référence C#)</span><span class="sxs-lookup"><span data-stu-id="2bb3c-102">explicit (C# Reference)</span></span>

<span data-ttu-id="2bb3c-103">Le mot clé `explicit` déclare un opérateur de conversion de type défini par l’utilisateur qui doit être appelé avec un cast.</span><span class="sxs-lookup"><span data-stu-id="2bb3c-103">The `explicit` keyword declares a user-defined type conversion operator that must be invoked with a cast.</span></span>

<span data-ttu-id="2bb3c-104">L’exemple suivant définit l’opérateur qui effectue la conversion d’une classe `Fahrenheit` en classe `Celsius`.</span><span class="sxs-lookup"><span data-stu-id="2bb3c-104">The following example defines the operator that converts from a `Fahrenheit` class to a `Celsius` class.</span></span> <span data-ttu-id="2bb3c-105">L’opérateur doit être défini dans une classe `Fahrenheit` ou une classe `Celsius` :</span><span class="sxs-lookup"><span data-stu-id="2bb3c-105">The operator must be defined either inside a `Fahrenheit` class or a `Celsius` class:</span></span>

[!code-csharp[csrefKeywordsConversion#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#2)]

<span data-ttu-id="2bb3c-106">Vous appelez l’opérateur de conversion défini avec un cast, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="2bb3c-106">You invoke the defined conversion operator with a cast, as the following example shows:</span></span>

[!code-csharp[csrefKeywordsConversion#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#3)]

<span data-ttu-id="2bb3c-107">L’opérateur de conversion convertit un type source en type cible.</span><span class="sxs-lookup"><span data-stu-id="2bb3c-107">The conversion operator converts from a source type to a target type.</span></span> <span data-ttu-id="2bb3c-108">Le type source fournit l’opérateur de conversion.</span><span class="sxs-lookup"><span data-stu-id="2bb3c-108">The source type provides the conversion operator.</span></span> <span data-ttu-id="2bb3c-109">Contrairement à une conversion implicite, les opérateurs de conversion explicite doivent être appelés au moyen d’un cast.</span><span class="sxs-lookup"><span data-stu-id="2bb3c-109">Unlike implicit conversion, explicit conversion operators must be invoked by means of a cast.</span></span> <span data-ttu-id="2bb3c-110">Si une opération de conversion peut provoquer des exceptions ou la perte d’informations, vous devez la marquer comme `explicit`.</span><span class="sxs-lookup"><span data-stu-id="2bb3c-110">If a conversion operation can cause exceptions or lose information, you should mark it `explicit`.</span></span> <span data-ttu-id="2bb3c-111">Cela empêche que le compilateur appelle l’opération de conversion en mode silencieux, avec éventuellement des conséquences imprévisibles.</span><span class="sxs-lookup"><span data-stu-id="2bb3c-111">This prevents the compiler from silently invoking the conversion operation with possibly unforeseen consequences.</span></span>

<span data-ttu-id="2bb3c-112">L’omission du cast provoque l’erreur de compilation CS0266.</span><span class="sxs-lookup"><span data-stu-id="2bb3c-112">Omitting the cast results in compile-time error CS0266.</span></span>

<span data-ttu-id="2bb3c-113">Pour plus d’informations, consultez [Utilisation d’opérateurs de conversion](../../programming-guide/statements-expressions-operators/using-conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="2bb3c-113">For more information, see [Using Conversion Operators](../../programming-guide/statements-expressions-operators/using-conversion-operators.md).</span></span>

## <a name="example"></a><span data-ttu-id="2bb3c-114">Exemples</span><span class="sxs-lookup"><span data-stu-id="2bb3c-114">Example</span></span>

<span data-ttu-id="2bb3c-115">L’exemple suivant fournit des classes `Fahrenheit` et `Celsius`, chacune fournissant un opérateur de conversion explicite à l’autre classe.</span><span class="sxs-lookup"><span data-stu-id="2bb3c-115">The following example provides a `Fahrenheit` and a `Celsius` class, each of which provides an explicit conversion operator to the other class.</span></span>

[!code-csharp[csrefKeywordsConversion#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#1)]

## <a name="example"></a><span data-ttu-id="2bb3c-116">Exemples</span><span class="sxs-lookup"><span data-stu-id="2bb3c-116">Example</span></span>

<span data-ttu-id="2bb3c-117">L’exemple suivant définit un struct, `Digit`, qui représente un seul chiffre décimal.</span><span class="sxs-lookup"><span data-stu-id="2bb3c-117">The following example defines a struct, `Digit`, that represents a single decimal digit.</span></span> <span data-ttu-id="2bb3c-118">Un opérateur est défini pour les conversions de `byte` à `Digit`, mais étant donné que les octets ne peuvent pas tous être convertis en `Digit`, la conversion est explicite.</span><span class="sxs-lookup"><span data-stu-id="2bb3c-118">An operator is defined for conversions from `byte` to `Digit`, but because not all bytes can be converted to a `Digit`, the conversion is explicit.</span></span>

[!code-csharp[csrefKeywordsConversion#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#4)]

## <a name="c-language-specification"></a><span data-ttu-id="2bb3c-119">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="2bb3c-119">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="2bb3c-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2bb3c-120">See also</span></span>

- [<span data-ttu-id="2bb3c-121">Référence C#</span><span class="sxs-lookup"><span data-stu-id="2bb3c-121">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="2bb3c-122">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="2bb3c-122">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="2bb3c-123">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="2bb3c-123">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="2bb3c-124">implicit</span><span class="sxs-lookup"><span data-stu-id="2bb3c-124">implicit</span></span>](implicit.md)
- [<span data-ttu-id="2bb3c-125">Surcharge d’opérateur</span><span class="sxs-lookup"><span data-stu-id="2bb3c-125">Operator overloading</span></span>](../operators/operator-overloading.md)
- [<span data-ttu-id="2bb3c-126">Guide pratique pour implémenter des conversions définies par l’utilisateur entre des structs</span><span class="sxs-lookup"><span data-stu-id="2bb3c-126">How to: Implement User-Defined Conversions Between Structs</span></span>](../../programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)
- [<span data-ttu-id="2bb3c-127">Conversions explicites définies par l’utilisateur chaînées en C#</span><span class="sxs-lookup"><span data-stu-id="2bb3c-127">Chained user-defined explicit conversions in C#</span></span>](https://blogs.msdn.microsoft.com/ericlippert/2007/04/16/chained-user-defined-explicit-conversions-in-c/)
