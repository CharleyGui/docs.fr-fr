---
title: '&amp;(Visual Basic), opérateur'
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
ms.openlocfilehash: aaa7c1b9ab7f6c920180d97b55c3bdeb23f00e02
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592241"
---
# <a name="amp-operator-visual-basic"></a><span data-ttu-id="eaf2b-102">&amp;(Visual Basic), opérateur</span><span class="sxs-lookup"><span data-stu-id="eaf2b-102">&amp; Operator (Visual Basic)</span></span>
<span data-ttu-id="eaf2b-103">Génère une concaténation de chaîne de deux expressions.</span><span class="sxs-lookup"><span data-stu-id="eaf2b-103">Generates a string concatenation of two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eaf2b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eaf2b-104">Syntax</span></span>  
  
```vb  
result = expression1 & expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="eaf2b-105">Composants</span><span class="sxs-lookup"><span data-stu-id="eaf2b-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="eaf2b-106">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="eaf2b-106">Required.</span></span> <span data-ttu-id="eaf2b-107">Toute variable `String` ou `Object`.</span><span class="sxs-lookup"><span data-stu-id="eaf2b-107">Any `String` or `Object` variable.</span></span>  
  
 `expression1`  
 <span data-ttu-id="eaf2b-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="eaf2b-108">Required.</span></span> <span data-ttu-id="eaf2b-109">Toute expression avec un type de données qui s’étend à `String`.</span><span class="sxs-lookup"><span data-stu-id="eaf2b-109">Any expression with a data type that widens to `String`.</span></span>  
  
 `expression2`  
 <span data-ttu-id="eaf2b-110">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="eaf2b-110">Required.</span></span> <span data-ttu-id="eaf2b-111">Toute expression avec un type de données qui s’étend à `String`.</span><span class="sxs-lookup"><span data-stu-id="eaf2b-111">Any expression with a data type that widens to `String`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eaf2b-112">Notes</span><span class="sxs-lookup"><span data-stu-id="eaf2b-112">Remarks</span></span>  
 <span data-ttu-id="eaf2b-113">Si le type de données de `expression1` ou `expression2` n’est pas `String`, mais s’étend à `String`, il est converti en `String`.</span><span class="sxs-lookup"><span data-stu-id="eaf2b-113">If the data type of `expression1` or `expression2` is not `String` but widens to `String`, it is converted to `String`.</span></span> <span data-ttu-id="eaf2b-114">Si l’un des types de données ne s’étend pas à `String`, le compilateur génère une erreur.</span><span class="sxs-lookup"><span data-stu-id="eaf2b-114">If either of the data types does not widen to `String`, the compiler generates an error.</span></span>  
  
 <span data-ttu-id="eaf2b-115">Le type de données de `result` est `String`.</span><span class="sxs-lookup"><span data-stu-id="eaf2b-115">The data type of `result` is `String`.</span></span> <span data-ttu-id="eaf2b-116">Si l’une ou les deux expressions ont la valeur [Nothing](../../../visual-basic/language-reference/nothing.md) ou si elles ont la valeur <xref:System.DBNull.Value?displayProperty=nameWithType>, elles sont traitées comme une chaîne avec la valeur «».</span><span class="sxs-lookup"><span data-stu-id="eaf2b-116">If one or both expressions evaluate to [Nothing](../../../visual-basic/language-reference/nothing.md) or have a value of <xref:System.DBNull.Value?displayProperty=nameWithType>, they are treated as a string with a value of "".</span></span>  
  
> [!NOTE]
> <span data-ttu-id="eaf2b-117">L’opérateur `&` peut être *surchargé*, ce qui signifie qu’une classe ou une structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou de cette structure.</span><span class="sxs-lookup"><span data-stu-id="eaf2b-117">The `&` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="eaf2b-118">Si votre code utilise cet opérateur sur une classe ou une structure de ce type, veillez à bien comprendre son comportement redéfini.</span><span class="sxs-lookup"><span data-stu-id="eaf2b-118">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="eaf2b-119">Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="eaf2b-119">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="eaf2b-120">Le caractère perluète (&) peut également être utilisé pour identifier des variables en tant que type `Long`.</span><span class="sxs-lookup"><span data-stu-id="eaf2b-120">The ampersand (&) character can also be used to identify variables as type `Long`.</span></span> <span data-ttu-id="eaf2b-121">Pour plus d’informations, consultez [caractères de type](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md).</span><span class="sxs-lookup"><span data-stu-id="eaf2b-121">For more information, see [Type Characters](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="eaf2b-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="eaf2b-122">Example</span></span>  
 <span data-ttu-id="eaf2b-123">Cet exemple utilise l’opérateur `&` pour forcer la concaténation de chaînes.</span><span class="sxs-lookup"><span data-stu-id="eaf2b-123">This example uses the `&` operator to force string concatenation.</span></span> <span data-ttu-id="eaf2b-124">Le résultat est une valeur de chaîne représentant la concaténation des deux opérandes de chaîne.</span><span class="sxs-lookup"><span data-stu-id="eaf2b-124">The result is a string value representing the concatenation of the two string operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="eaf2b-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eaf2b-125">See also</span></span>

- [<span data-ttu-id="eaf2b-126">&= (opérateur)</span><span class="sxs-lookup"><span data-stu-id="eaf2b-126">&= Operator</span></span>](../../../visual-basic/language-reference/operators/and-assignment-operator.md)
- [<span data-ttu-id="eaf2b-127">opérateur de concaténation</span><span class="sxs-lookup"><span data-stu-id="eaf2b-127">Concatenation Operators</span></span>](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [<span data-ttu-id="eaf2b-128">Priorité des opérateurs en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="eaf2b-128">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="eaf2b-129">Opérateurs répertoriés par fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="eaf2b-129">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="eaf2b-130">Opérateurs de concaténation dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="eaf2b-130">Concatenation Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
