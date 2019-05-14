---
title: opérateur, mot clé - Référence C#
ms.custom: seodec18
description: Découvrez comment surcharger un opérateur C# intégré
ms.date: 08/27/2018
f1_keywords:
- operator_CSharpKeyword
- operator
helpviewer_keywords:
- operator keyword [C#]
ms.assetid: 59218cce-e90e-42f6-a6bb-30300981b86a
ms.openlocfilehash: 47ce91c343092ac2f7555c1edf3418527776e131
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64754760"
---
# <a name="operator-c-reference"></a><span data-ttu-id="56edc-103">operator (référence C#)</span><span class="sxs-lookup"><span data-stu-id="56edc-103">operator (C# Reference)</span></span>

<span data-ttu-id="56edc-104">Utilisez le mot clé `operator` pour surcharger un opérateur intégré ou pour fournir une conversion définie par l’utilisateur dans une déclaration class ou struct.</span><span class="sxs-lookup"><span data-stu-id="56edc-104">Use the `operator` keyword to overload a built-in operator or to provide a user-defined conversion in a class or struct declaration.</span></span>

<span data-ttu-id="56edc-105">Pour surcharger un opérateur sur une classe ou un struct personnalisé, créez une déclaration d’opérateur dans le type correspondant.</span><span class="sxs-lookup"><span data-stu-id="56edc-105">To overload an operator on a custom class or struct, you create an operator declaration in the corresponding type.</span></span> <span data-ttu-id="56edc-106">La déclaration d’opérateur qui surcharge un opérateur C# intégré doit respecter les règles suivantes :</span><span class="sxs-lookup"><span data-stu-id="56edc-106">The operator declaration that overloads a built-in C# operator must satisfy the following rules:</span></span>

- <span data-ttu-id="56edc-107">Elle contient un modificateur `public` et un modificateur `static`.</span><span class="sxs-lookup"><span data-stu-id="56edc-107">It includes both a `public` and a `static` modifier.</span></span>
- <span data-ttu-id="56edc-108">Elle contient `operator X`, où `X` est le nom ou le symbole de l’opérateur surchargé.</span><span class="sxs-lookup"><span data-stu-id="56edc-108">It includes `operator X` where `X` is the name or symbol of the operator being overloaded.</span></span>
- <span data-ttu-id="56edc-109">Les opérateurs unaires ont un seul paramètre et les opérateurs binaires en ont deux.</span><span class="sxs-lookup"><span data-stu-id="56edc-109">Unary operators have one parameter, and binary operators have two parameters.</span></span> <span data-ttu-id="56edc-110">Dans chaque cas, au moins un paramètre doit être du même type que la classe ou le struct qui déclare l’opérateur.</span><span class="sxs-lookup"><span data-stu-id="56edc-110">In each case, at least one parameter must be the same type as the class or struct that declares the operator.</span></span>

<span data-ttu-id="56edc-111">Pour plus d’informations sur la définition d’opérateurs de conversion, consultez les articles sur les mots clés [explicit](explicit.md) et [implicit](implicit.md).</span><span class="sxs-lookup"><span data-stu-id="56edc-111">For information about how to define conversion operators, see the [explicit](explicit.md) and [implicit](implicit.md) keyword articles.</span></span>

<span data-ttu-id="56edc-112">Pour avoir une vue d’ensemble des opérateurs C# qui peuvent être surchargés, consultez l’article [Opérateurs surchargeables](../../programming-guide/statements-expressions-operators/overloadable-operators.md).</span><span class="sxs-lookup"><span data-stu-id="56edc-112">For an overview of the C# operators that can be overloaded, see the [Overloadable operators](../../programming-guide/statements-expressions-operators/overloadable-operators.md) article.</span></span>

## <a name="example"></a><span data-ttu-id="56edc-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="56edc-113">Example</span></span>

<span data-ttu-id="56edc-114">L’exemple suivant définit un type `Fraction` qui représente des nombres fractionnaires.</span><span class="sxs-lookup"><span data-stu-id="56edc-114">The following example defines a `Fraction` type that represents fractional numbers.</span></span> <span data-ttu-id="56edc-115">Cette classe surcharge les opérateurs `+` et `*` pour effectuer des opérations d’addition et de multiplication fractionnaires. Elle fournit également un opérateur de conversion qui convertit un type `Fraction` en type `double`.</span><span class="sxs-lookup"><span data-stu-id="56edc-115">It overloads the `+` and `*` operators to perform fractional addition and multiplication, and also provides a conversion operator that converts a `Fraction` type to a `double` type.</span></span>

[!code-csharp[csrefKeywordsConversion#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#6)]

## <a name="c-language-specification"></a><span data-ttu-id="56edc-116">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="56edc-116">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="56edc-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="56edc-117">See also</span></span>

- [<span data-ttu-id="56edc-118">Référence C#</span><span class="sxs-lookup"><span data-stu-id="56edc-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="56edc-119">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="56edc-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="56edc-120">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="56edc-120">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="56edc-121">implicit</span><span class="sxs-lookup"><span data-stu-id="56edc-121">implicit</span></span>](implicit.md)
- [<span data-ttu-id="56edc-122">explicit</span><span class="sxs-lookup"><span data-stu-id="56edc-122">explicit</span></span>](explicit.md)
- [<span data-ttu-id="56edc-123">Opérateurs surchargeables</span><span class="sxs-lookup"><span data-stu-id="56edc-123">Overloadable operators</span></span>](../../programming-guide/statements-expressions-operators/overloadable-operators.md)
- [<span data-ttu-id="56edc-124">Guide pratique pour implémenter des conversions définies par l’utilisateur entre des structs</span><span class="sxs-lookup"><span data-stu-id="56edc-124">How to: Implement User-Defined Conversions Between Structs</span></span>](../../programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)
