---
title: '- Opérateur'
ms.date: 07/20/2015
f1_keywords:
- vb.Negate
- vb.-
helpviewer_keywords:
- operator [Visual Basic]
- operators [Visual Basic], subtraction
- operators [Visual Basic], difference
- negation operator [Visual Basic]
- operators [Visual Basic], arithmetic
- subtraction operator [Visual Basic], syntax
- arithmetic operators [Visual Basic], subtraction
- difference operator [Visual Basic]
- math operators [Visual Basic]
- operators [Visual Basic], negation
- minus operator [Visual Basic]
ms.assetid: bff2c368-662d-4c92-ac87-1d9bdfd3426a
ms.openlocfilehash: b5129c2dbb361940fa6da2cb424ee23736ba72c5
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875330"
---
# <a name="--operator-visual-basic"></a><span data-ttu-id="ac6b0-102">-, opérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ac6b0-102">- Operator (Visual Basic)</span></span>

<span data-ttu-id="ac6b0-103">Retourne la différence entre deux expressions numériques ou la valeur négative d’une expression numérique.</span><span class="sxs-lookup"><span data-stu-id="ac6b0-103">Returns the difference between two numeric expressions or the negative value of a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac6b0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ac6b0-104">Syntax</span></span>  
  
```vb  
expression1 – expression2
```
  
<span data-ttu-id="ac6b0-105">or</span><span class="sxs-lookup"><span data-stu-id="ac6b0-105">or</span></span>

```vb  
–expression1  
```  
  
## <a name="parts"></a><span data-ttu-id="ac6b0-106">Éléments</span><span class="sxs-lookup"><span data-stu-id="ac6b0-106">Parts</span></span>  

 `expression1`  
 <span data-ttu-id="ac6b0-107">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="ac6b0-107">Required.</span></span> <span data-ttu-id="ac6b0-108">Toute expression numérique.</span><span class="sxs-lookup"><span data-stu-id="ac6b0-108">Any numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="ac6b0-109">Obligatoire, sauf si l' `–` opérateur calcule une valeur négative.</span><span class="sxs-lookup"><span data-stu-id="ac6b0-109">Required unless the `–` operator is calculating a negative value.</span></span> <span data-ttu-id="ac6b0-110">Toute expression numérique.</span><span class="sxs-lookup"><span data-stu-id="ac6b0-110">Any numeric expression.</span></span>  
  
## <a name="result"></a><span data-ttu-id="ac6b0-111">Résultats</span><span class="sxs-lookup"><span data-stu-id="ac6b0-111">Result</span></span>  

 <span data-ttu-id="ac6b0-112">Le résultat est la différence entre `expression1` et `expression2` , ou la valeur négative de `expression1` .</span><span class="sxs-lookup"><span data-stu-id="ac6b0-112">The result is the difference between `expression1` and `expression2`, or the negated value of `expression1`.</span></span>  
  
 <span data-ttu-id="ac6b0-113">Le type de données de résultat est un type numérique approprié pour les types de données de `expression1` et `expression2` .</span><span class="sxs-lookup"><span data-stu-id="ac6b0-113">The result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="ac6b0-114">Consultez les tables « arithmétiques sur les entiers » dans [types de données des résultats d’opérateur](data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="ac6b0-114">See the "Integer Arithmetic" tables in [Data Types of Operator Results](data-types-of-operator-results.md).</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="ac6b0-115">Types pris en charge</span><span class="sxs-lookup"><span data-stu-id="ac6b0-115">Supported Types</span></span>  

 <span data-ttu-id="ac6b0-116">tous les types numériques</span><span class="sxs-lookup"><span data-stu-id="ac6b0-116">All numeric types.</span></span> <span data-ttu-id="ac6b0-117">Cela comprend les types à virgule flottante non signée et `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="ac6b0-117">This includes the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ac6b0-118">Notes</span><span class="sxs-lookup"><span data-stu-id="ac6b0-118">Remarks</span></span>  

 <span data-ttu-id="ac6b0-119">Dans la première utilisation indiquée dans la syntaxe indiquée précédemment, l' `–` opérateur est l’opérateur de soustraction arithmétique *binaire* pour la différence entre deux expressions numériques.</span><span class="sxs-lookup"><span data-stu-id="ac6b0-119">In the first usage shown in the syntax shown previously, the `–` operator is the *binary* arithmetic subtraction operator for the difference between two numeric expressions.</span></span>  
  
 <span data-ttu-id="ac6b0-120">Dans la deuxième utilisation indiquée dans la syntaxe indiquée précédemment, l' `–` opérateur est l’opérateur de négation *unaire* pour la valeur négative d’une expression.</span><span class="sxs-lookup"><span data-stu-id="ac6b0-120">In the second usage shown in the syntax shown previously, the `–` operator is the *unary* negation operator for the negative value of an expression.</span></span> <span data-ttu-id="ac6b0-121">Dans ce sens, la négation consiste à inverser le signe de `expression1` afin que le résultat soit positif si `expression1` est négatif.</span><span class="sxs-lookup"><span data-stu-id="ac6b0-121">In this sense, the negation consists of reversing the sign of `expression1` so that the result is positive if `expression1` is negative.</span></span>  
  
 <span data-ttu-id="ac6b0-122">Si l’une des expressions a la valeur [Nothing](../nothing.md), l' `–` opérateur la traite comme zéro.</span><span class="sxs-lookup"><span data-stu-id="ac6b0-122">If either expression evaluates to [Nothing](../nothing.md), the `–` operator treats it as zero.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ac6b0-123">L' `–` opérateur peut être *surchargé*, ce qui signifie qu’une classe ou une structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou de cette structure.</span><span class="sxs-lookup"><span data-stu-id="ac6b0-123">The `–` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="ac6b0-124">Si votre code utilise cet opérateur sur ce type de classe ou de structure, assurez-vous que vous comprenez son comportement redéfini.</span><span class="sxs-lookup"><span data-stu-id="ac6b0-124">If your code uses this operator on such a class or structure, make sure that you understand its redefined behavior.</span></span> <span data-ttu-id="ac6b0-125">Pour plus d'informations, consultez [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="ac6b0-125">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ac6b0-126">Exemple</span><span class="sxs-lookup"><span data-stu-id="ac6b0-126">Example</span></span>  

 <span data-ttu-id="ac6b0-127">L’exemple suivant utilise l' `–` opérateur pour calculer et retourner la différence entre deux nombres, puis pour nier un nombre.</span><span class="sxs-lookup"><span data-stu-id="ac6b0-127">The following example uses the `–` operator to calculate and return the difference between two numbers, and then to negate a number.</span></span>  
  
 [!code-vb[VbVbalrOperators#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#10)]  
  
 <span data-ttu-id="ac6b0-128">Après l’exécution de ces instructions, `binaryResult` contient 124,45 et `unaryResult` contient – 334,90.</span><span class="sxs-lookup"><span data-stu-id="ac6b0-128">Following the execution of these statements, `binaryResult` contains 124.45 and `unaryResult` contains –334.90.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac6b0-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ac6b0-129">See also</span></span>

- [<span data-ttu-id="ac6b0-130">-=, Opérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ac6b0-130">-= Operator (Visual Basic)</span></span>](subtraction-assignment-operator.md)
- [<span data-ttu-id="ac6b0-131">Opérateurs arithmétiques</span><span class="sxs-lookup"><span data-stu-id="ac6b0-131">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="ac6b0-132">Priorité des opérateurs en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ac6b0-132">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="ac6b0-133">Opérateurs listés par fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="ac6b0-133">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="ac6b0-134">Opérateurs arithmétiques en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ac6b0-134">Arithmetic Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
