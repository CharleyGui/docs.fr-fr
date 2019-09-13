---
title: '- (Visual Basic), opérateur'
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
ms.openlocfilehash: eb34b34986613f36b624c43c04f98390ffba4fe0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965862"
---
# <a name="--operator-visual-basic"></a><span data-ttu-id="f0531-102">-, opérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f0531-102">- Operator (Visual Basic)</span></span>
<span data-ttu-id="f0531-103">Retourne la différence entre deux expressions numériques ou la valeur négative d’une expression numérique.</span><span class="sxs-lookup"><span data-stu-id="f0531-103">Returns the difference between two numeric expressions or the negative value of a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0531-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f0531-104">Syntax</span></span>  
  
```  
      expression1 – expression2  
- or -  
– expression1  
```  
  
## <a name="parts"></a><span data-ttu-id="f0531-105">Composants</span><span class="sxs-lookup"><span data-stu-id="f0531-105">Parts</span></span>  
 `expression1`  
 <span data-ttu-id="f0531-106">Requis.</span><span class="sxs-lookup"><span data-stu-id="f0531-106">Required.</span></span> <span data-ttu-id="f0531-107">Toute expression numérique.</span><span class="sxs-lookup"><span data-stu-id="f0531-107">Any numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="f0531-108">Obligatoire, sauf `–` si l’opérateur calcule une valeur négative.</span><span class="sxs-lookup"><span data-stu-id="f0531-108">Required unless the `–` operator is calculating a negative value.</span></span> <span data-ttu-id="f0531-109">Toute expression numérique.</span><span class="sxs-lookup"><span data-stu-id="f0531-109">Any numeric expression.</span></span>  
  
## <a name="result"></a><span data-ttu-id="f0531-110">Résultat</span><span class="sxs-lookup"><span data-stu-id="f0531-110">Result</span></span>  
 <span data-ttu-id="f0531-111">Le résultat est la différence entre `expression1` et `expression2`, ou la valeur négative de `expression1`.</span><span class="sxs-lookup"><span data-stu-id="f0531-111">The result is the difference between `expression1` and `expression2`, or the negated value of `expression1`.</span></span>  
  
 <span data-ttu-id="f0531-112">Le type de données de résultat est un type numérique approprié pour les types `expression1` de `expression2`données de et.</span><span class="sxs-lookup"><span data-stu-id="f0531-112">The result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="f0531-113">Consultez les tables « arithmétiques sur les entiers » dans [types de données des résultats d’opérateur](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="f0531-113">See the "Integer Arithmetic" tables in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="f0531-114">Types pris en charge</span><span class="sxs-lookup"><span data-stu-id="f0531-114">Supported Types</span></span>  
 <span data-ttu-id="f0531-115">tous les types numériques</span><span class="sxs-lookup"><span data-stu-id="f0531-115">All numeric types.</span></span> <span data-ttu-id="f0531-116">Cela comprend les types `Decimal`à virgule flottante non signée et.</span><span class="sxs-lookup"><span data-stu-id="f0531-116">This includes the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f0531-117">Notes</span><span class="sxs-lookup"><span data-stu-id="f0531-117">Remarks</span></span>  
 <span data-ttu-id="f0531-118">Dans la première utilisation indiquée dans la syntaxe indiquée précédemment, l' `–` opérateur est l’opérateur de soustraction arithmétique *binaire* pour la différence entre deux expressions numériques.</span><span class="sxs-lookup"><span data-stu-id="f0531-118">In the first usage shown in the syntax shown previously, the `–` operator is the *binary* arithmetic subtraction operator for the difference between two numeric expressions.</span></span>  
  
 <span data-ttu-id="f0531-119">Dans la deuxième utilisation indiquée dans la syntaxe indiquée précédemment, l' `–` opérateur est l’opérateur de négation *unaire* pour la valeur négative d’une expression.</span><span class="sxs-lookup"><span data-stu-id="f0531-119">In the second usage shown in the syntax shown previously, the `–` operator is the *unary* negation operator for the negative value of an expression.</span></span> <span data-ttu-id="f0531-120">Dans ce sens, la négation consiste à inverser le signe de `expression1` afin que le résultat soit positif si `expression1` est négatif.</span><span class="sxs-lookup"><span data-stu-id="f0531-120">In this sense, the negation consists of reversing the sign of `expression1` so that the result is positive if `expression1` is negative.</span></span>  
  
 <span data-ttu-id="f0531-121">Si l’une des expressions a la valeur [Nothing](../../../visual-basic/language-reference/nothing.md), l’opérateur `–` la traite comme zéro.</span><span class="sxs-lookup"><span data-stu-id="f0531-121">If either expression evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), the `–` operator treats it as zero.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f0531-122">L' `–` opérateur peut être *surchargé*, ce qui signifie qu’une classe ou une structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou de cette structure.</span><span class="sxs-lookup"><span data-stu-id="f0531-122">The `–` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="f0531-123">Si votre code utilise cet opérateur sur ce type de classe ou de structure, assurez-vous que vous comprenez son comportement redéfini.</span><span class="sxs-lookup"><span data-stu-id="f0531-123">If your code uses this operator on such a class or structure, make sure that you understand its redefined behavior.</span></span> <span data-ttu-id="f0531-124">Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="f0531-124">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f0531-125">Exemples</span><span class="sxs-lookup"><span data-stu-id="f0531-125">Example</span></span>  
 <span data-ttu-id="f0531-126">L’exemple suivant utilise l' `–` opérateur pour calculer et retourner la différence entre deux nombres, puis pour nier un nombre.</span><span class="sxs-lookup"><span data-stu-id="f0531-126">The following example uses the `–` operator to calculate and return the difference between two numbers, and then to negate a number.</span></span>  
  
 [!code-vb[VbVbalrOperators#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#10)]  
  
 <span data-ttu-id="f0531-127">Après l’exécution de ces instructions, `binaryResult` contient 124,45 et `unaryResult` contient – 334,90.</span><span class="sxs-lookup"><span data-stu-id="f0531-127">Following the execution of these statements, `binaryResult` contains 124.45 and `unaryResult` contains –334.90.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0531-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f0531-128">See also</span></span>

- [<span data-ttu-id="f0531-129">-=, Opérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f0531-129">-= Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)
- [<span data-ttu-id="f0531-130">Opérateurs arithmétiques</span><span class="sxs-lookup"><span data-stu-id="f0531-130">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="f0531-131">Priorité des opérateurs en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f0531-131">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="f0531-132">Opérateurs répertoriés par fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="f0531-132">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="f0531-133">Opérateurs arithmétiques dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f0531-133">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
