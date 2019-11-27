---
title: '&amp;, opérateur'
ms.date: 07/20/2015
f1_keywords:
- vb.&
helpviewer_keywords:
- And (&) operator
- ampersand operator (&)
- '& operator'
- concatenation operators [Visual Basic], syntax
- strings [Visual Basic], concatenating
ms.assetid: fefc3d00-cbf1-475c-8c5e-6fb213b3f85a
ms.openlocfilehash: 4cae7e59083890e82d754bdaa58942c2224357b0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74336057"
---
# <a name="amp-operator-visual-basic"></a><span data-ttu-id="af81d-102">Opérateur de &amp; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="af81d-102">&amp; Operator (Visual Basic)</span></span>
<span data-ttu-id="af81d-103">Génère une concaténation de chaîne de deux expressions.</span><span class="sxs-lookup"><span data-stu-id="af81d-103">Generates a string concatenation of two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af81d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="af81d-104">Syntax</span></span>  
  
```vb  
result = expression1 & expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="af81d-105">Composants</span><span class="sxs-lookup"><span data-stu-id="af81d-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="af81d-106">Requis.</span><span class="sxs-lookup"><span data-stu-id="af81d-106">Required.</span></span> <span data-ttu-id="af81d-107">Toute variable `String` ou `Object`.</span><span class="sxs-lookup"><span data-stu-id="af81d-107">Any `String` or `Object` variable.</span></span>  
  
 `expression1`  
 <span data-ttu-id="af81d-108">Requis.</span><span class="sxs-lookup"><span data-stu-id="af81d-108">Required.</span></span> <span data-ttu-id="af81d-109">Toute expression avec un type de données qui s’étend à `String`.</span><span class="sxs-lookup"><span data-stu-id="af81d-109">Any expression with a data type that widens to `String`.</span></span>  
  
 `expression2`  
 <span data-ttu-id="af81d-110">Requis.</span><span class="sxs-lookup"><span data-stu-id="af81d-110">Required.</span></span> <span data-ttu-id="af81d-111">Toute expression avec un type de données qui s’étend à `String`.</span><span class="sxs-lookup"><span data-stu-id="af81d-111">Any expression with a data type that widens to `String`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="af81d-112">Notes</span><span class="sxs-lookup"><span data-stu-id="af81d-112">Remarks</span></span>  
 <span data-ttu-id="af81d-113">Si le type de données de `expression1` ou `expression2` n’est pas `String` mais s’élargit à `String`, il est converti en `String`.</span><span class="sxs-lookup"><span data-stu-id="af81d-113">If the data type of `expression1` or `expression2` is not `String` but widens to `String`, it is converted to `String`.</span></span> <span data-ttu-id="af81d-114">Si l’un des types de données ne s’étend pas à `String`, le compilateur génère une erreur.</span><span class="sxs-lookup"><span data-stu-id="af81d-114">If either of the data types does not widen to `String`, the compiler generates an error.</span></span>  
  
 <span data-ttu-id="af81d-115">Le type de données de `result` est `String`.</span><span class="sxs-lookup"><span data-stu-id="af81d-115">The data type of `result` is `String`.</span></span> <span data-ttu-id="af81d-116">Si l’une ou les deux expressions ont la valeur [Nothing](../../../visual-basic/language-reference/nothing.md) ou si elles ont la valeur <xref:System.DBNull.Value?displayProperty=nameWithType>, elles sont traitées comme une chaîne avec la valeur «».</span><span class="sxs-lookup"><span data-stu-id="af81d-116">If one or both expressions evaluate to [Nothing](../../../visual-basic/language-reference/nothing.md) or have a value of <xref:System.DBNull.Value?displayProperty=nameWithType>, they are treated as a string with a value of "".</span></span>  
  
> [!NOTE]
> <span data-ttu-id="af81d-117">L’opérateur `&` peut être *surchargé*, ce qui signifie qu’une classe ou une structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou de cette structure.</span><span class="sxs-lookup"><span data-stu-id="af81d-117">The `&` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="af81d-118">Si votre code utilise cet opérateur sur une classe ou une structure de ce type, veillez à bien comprendre son comportement redéfini.</span><span class="sxs-lookup"><span data-stu-id="af81d-118">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="af81d-119">Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="af81d-119">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="af81d-120">Le caractère perluète (&) peut également être utilisé pour identifier des variables en tant que type `Long`.</span><span class="sxs-lookup"><span data-stu-id="af81d-120">The ampersand (&) character can also be used to identify variables as type `Long`.</span></span> <span data-ttu-id="af81d-121">Pour plus d’informations, consultez [caractères de type](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md).</span><span class="sxs-lookup"><span data-stu-id="af81d-121">For more information, see [Type Characters](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="af81d-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="af81d-122">Example</span></span>  
 <span data-ttu-id="af81d-123">Cet exemple utilise l’opérateur `&` pour forcer la concaténation de chaînes.</span><span class="sxs-lookup"><span data-stu-id="af81d-123">This example uses the `&` operator to force string concatenation.</span></span> <span data-ttu-id="af81d-124">Le résultat est une valeur de chaîne représentant la concaténation des deux opérandes de chaîne.</span><span class="sxs-lookup"><span data-stu-id="af81d-124">The result is a string value representing the concatenation of the two string operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="af81d-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="af81d-125">See also</span></span>

- [<span data-ttu-id="af81d-126">&=, opérateur</span><span class="sxs-lookup"><span data-stu-id="af81d-126">&= Operator</span></span>](../../../visual-basic/language-reference/operators/and-assignment-operator.md)
- [<span data-ttu-id="af81d-127">Opérateurs de concaténation</span><span class="sxs-lookup"><span data-stu-id="af81d-127">Concatenation Operators</span></span>](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [<span data-ttu-id="af81d-128">Priorité des opérateurs en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="af81d-128">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="af81d-129">Opérateurs répertoriés par fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="af81d-129">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="af81d-130">Opérateurs de concaténation dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="af81d-130">Concatenation Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
