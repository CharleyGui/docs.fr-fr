---
title: '* Opérateur'
ms.date: 07/20/2015
f1_keywords:
- vb.*
helpviewer_keywords:
- arithmetic operators [Visual Basic], multiplication
- operators [Visual Basic], multiplication
- '* operator [Visual Basic]'
- multiplication operator [Visual Basic], syntax
- math operators [Visual Basic]
ms.assetid: 2b210382-99da-4195-89ba-b1d06f5e89ad
ms.openlocfilehash: 7038fef4258d190b726a851b26f2a2840ff3c0ea
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873365"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="ac7bc-102">\*, opérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ac7bc-102">\* Operator (Visual Basic)</span></span>

<span data-ttu-id="ac7bc-103">Multiplie deux nombres.</span><span class="sxs-lookup"><span data-stu-id="ac7bc-103">Multiplies two numbers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac7bc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ac7bc-104">Syntax</span></span>  
  
```vb  
number1 * number2  
```  
  
## <a name="parts"></a><span data-ttu-id="ac7bc-105">Éléments</span><span class="sxs-lookup"><span data-stu-id="ac7bc-105">Parts</span></span>  
  
|<span data-ttu-id="ac7bc-106">Terme</span><span class="sxs-lookup"><span data-stu-id="ac7bc-106">Term</span></span>|<span data-ttu-id="ac7bc-107">Définition</span><span class="sxs-lookup"><span data-stu-id="ac7bc-107">Definition</span></span>|  
|---|---|  
|`number1`|<span data-ttu-id="ac7bc-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="ac7bc-108">Required.</span></span> <span data-ttu-id="ac7bc-109">Toute expression numérique.</span><span class="sxs-lookup"><span data-stu-id="ac7bc-109">Any numeric expression.</span></span>|  
|`number2`|<span data-ttu-id="ac7bc-110">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="ac7bc-110">Required.</span></span> <span data-ttu-id="ac7bc-111">Toute expression numérique.</span><span class="sxs-lookup"><span data-stu-id="ac7bc-111">Any numeric expression.</span></span>|  
  
## <a name="result"></a><span data-ttu-id="ac7bc-112">Résultats</span><span class="sxs-lookup"><span data-stu-id="ac7bc-112">Result</span></span>  

 <span data-ttu-id="ac7bc-113">Le résultat est le produit de `number1` et `number2` .</span><span class="sxs-lookup"><span data-stu-id="ac7bc-113">The result is the product of `number1` and `number2`.</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="ac7bc-114">Types pris en charge</span><span class="sxs-lookup"><span data-stu-id="ac7bc-114">Supported Types</span></span>  

 <span data-ttu-id="ac7bc-115">Tous les types numériques, y compris les types à virgule flottante non signée et `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="ac7bc-115">All numeric types, including the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ac7bc-116">Notes</span><span class="sxs-lookup"><span data-stu-id="ac7bc-116">Remarks</span></span>  

 <span data-ttu-id="ac7bc-117">Le type de données du résultat dépend des types des opérandes.</span><span class="sxs-lookup"><span data-stu-id="ac7bc-117">The data type of the result depends on the types of the operands.</span></span> <span data-ttu-id="ac7bc-118">Le tableau suivant montre comment le type de données du résultat est déterminé.</span><span class="sxs-lookup"><span data-stu-id="ac7bc-118">The following table shows how the data type of the result is determined.</span></span>  
  
|<span data-ttu-id="ac7bc-119">Types de données des opérandes</span><span class="sxs-lookup"><span data-stu-id="ac7bc-119">Operand data types</span></span>|<span data-ttu-id="ac7bc-120">Type de données de résultat</span><span class="sxs-lookup"><span data-stu-id="ac7bc-120">Result data type</span></span>|  
|---|---|  
|<span data-ttu-id="ac7bc-121">Les deux expressions sont des types de données intégraux ([SByte](../data-types/sbyte-data-type.md), [Byte](../data-types/byte-data-type.md), [short](../data-types/short-data-type.md), [UShort](../data-types/ushort-data-type.md), [Integer](../data-types/integer-data-type.md), [UInteger](../data-types/uinteger-data-type.md), [long](../data-types/long-data-type.md), [ULong](../data-types/ulong-data-type.md))</span><span class="sxs-lookup"><span data-stu-id="ac7bc-121">Both expressions are integral data types ([SByte](../data-types/sbyte-data-type.md), [Byte](../data-types/byte-data-type.md), [Short](../data-types/short-data-type.md), [UShort](../data-types/ushort-data-type.md), [Integer](../data-types/integer-data-type.md), [UInteger](../data-types/uinteger-data-type.md), [Long](../data-types/long-data-type.md), [ULong](../data-types/ulong-data-type.md))</span></span>|<span data-ttu-id="ac7bc-122">Type de données numérique approprié pour les types de données de `number1` et `number2` .</span><span class="sxs-lookup"><span data-stu-id="ac7bc-122">A numeric data type appropriate for the data types of `number1` and `number2`.</span></span> <span data-ttu-id="ac7bc-123">Consultez les tables « arithmétiques sur les entiers » dans [types de données des résultats d’opérateur](data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="ac7bc-123">See the "Integer Arithmetic" tables in [Data Types of Operator Results](data-types-of-operator-results.md).</span></span>|  
|<span data-ttu-id="ac7bc-124">Les deux expressions sont [décimales](../data-types/decimal-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="ac7bc-124">Both expressions are [Decimal](../data-types/decimal-data-type.md)</span></span>|`Decimal`|  
|<span data-ttu-id="ac7bc-125">Les deux expressions sont [uniques](../data-types/single-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="ac7bc-125">Both expressions are [Single](../data-types/single-data-type.md)</span></span>|`Single`|  
|<span data-ttu-id="ac7bc-126">L’une des expressions est un type de données à virgule flottante ( `Single` ou [double](../data-types/double-data-type.md)), mais pas les deux `Single` (Notez qu' `Decimal` il ne s’agit pas d’un type de données à virgule flottante)</span><span class="sxs-lookup"><span data-stu-id="ac7bc-126">Either expression is a floating-point data type (`Single` or [Double](../data-types/double-data-type.md)) but not both `Single` (note `Decimal` is not a floating-point data type)</span></span>|`Double`|  
  
 <span data-ttu-id="ac7bc-127">Si une expression prend la valeur [Nothing](../nothing.md), elle est considérée comme égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="ac7bc-127">If an expression evaluates to [Nothing](../nothing.md), it is treated as zero.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="ac7bc-128">Surcharge</span><span class="sxs-lookup"><span data-stu-id="ac7bc-128">Overloading</span></span>  

 <span data-ttu-id="ac7bc-129">L' `*` opérateur peut être *surchargé*, ce qui signifie qu’une classe ou une structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou de cette structure.</span><span class="sxs-lookup"><span data-stu-id="ac7bc-129">The `*` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="ac7bc-130">Si votre code utilise cet opérateur sur une classe ou une structure de ce type, veillez à bien comprendre son comportement redéfini.</span><span class="sxs-lookup"><span data-stu-id="ac7bc-130">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="ac7bc-131">Pour plus d'informations, consultez [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="ac7bc-131">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ac7bc-132">Exemple</span><span class="sxs-lookup"><span data-stu-id="ac7bc-132">Example</span></span>  

 <span data-ttu-id="ac7bc-133">Cet exemple utilise l' `*` opérateur pour multiplier deux nombres.</span><span class="sxs-lookup"><span data-stu-id="ac7bc-133">This example uses the `*` operator to multiply two numbers.</span></span> <span data-ttu-id="ac7bc-134">Le résultat est le produit des deux opérandes.</span><span class="sxs-lookup"><span data-stu-id="ac7bc-134">The result is the product of the two operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="ac7bc-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ac7bc-135">See also</span></span>

- [<span data-ttu-id="ac7bc-136">\* = (Opérateur)</span><span class="sxs-lookup"><span data-stu-id="ac7bc-136">\*= Operator</span></span>](multiplication-assignment-operator.md)
- [<span data-ttu-id="ac7bc-137">Opérateurs arithmétiques</span><span class="sxs-lookup"><span data-stu-id="ac7bc-137">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="ac7bc-138">Priorité des opérateurs en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ac7bc-138">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="ac7bc-139">Opérateurs listés par fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="ac7bc-139">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="ac7bc-140">Opérateurs arithmétiques en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ac7bc-140">Arithmetic Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
