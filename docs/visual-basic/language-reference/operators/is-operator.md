---
title: Is, opérateur
ms.date: 07/20/2015
f1_keywords:
- vb.is
helpviewer_keywords:
- comparison operators [Visual Basic]
- equivalent objects
- TypeOf...Is expression
- Is operator [Visual Basic]
ms.assetid: 8045a6c8-2a83-45b6-ad47-d09a704c656d
ms.openlocfilehash: 3cc0ae5f04358fbe6b2aabc50498f39ca7225164
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84370802"
---
# <a name="is-operator-visual-basic"></a><span data-ttu-id="bac67-102">Is, opérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bac67-102">Is Operator (Visual Basic)</span></span>
<span data-ttu-id="bac67-103">Compare deux variables de référence d’objet.</span><span class="sxs-lookup"><span data-stu-id="bac67-103">Compares two object reference variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bac67-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bac67-104">Syntax</span></span>  
  
```vb  
result = object1 Is object2  
```  
  
## <a name="parts"></a><span data-ttu-id="bac67-105">Éléments</span><span class="sxs-lookup"><span data-stu-id="bac67-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="bac67-106">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="bac67-106">Required.</span></span> <span data-ttu-id="bac67-107">Toute `Boolean` valeur.</span><span class="sxs-lookup"><span data-stu-id="bac67-107">Any `Boolean` value.</span></span>  
  
 `object1`  
 <span data-ttu-id="bac67-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="bac67-108">Required.</span></span> <span data-ttu-id="bac67-109">N’importe quel `Object` nom.</span><span class="sxs-lookup"><span data-stu-id="bac67-109">Any `Object` name.</span></span>  
  
 `object2`  
 <span data-ttu-id="bac67-110">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="bac67-110">Required.</span></span> <span data-ttu-id="bac67-111">N’importe quel `Object` nom.</span><span class="sxs-lookup"><span data-stu-id="bac67-111">Any `Object` name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bac67-112">Notes</span><span class="sxs-lookup"><span data-stu-id="bac67-112">Remarks</span></span>  
 <span data-ttu-id="bac67-113">L' `Is` opérateur détermine si deux références d’objet font référence au même objet.</span><span class="sxs-lookup"><span data-stu-id="bac67-113">The `Is` operator determines if two object references refer to the same object.</span></span> <span data-ttu-id="bac67-114">Toutefois, il n’effectue pas de comparaisons de valeurs.</span><span class="sxs-lookup"><span data-stu-id="bac67-114">However, it does not perform value comparisons.</span></span> <span data-ttu-id="bac67-115">Si `object1` et `object2` font tous deux référence à la même instance d’objet, `result` est ; dans le `True` cas contraire, `result` est `False` .</span><span class="sxs-lookup"><span data-stu-id="bac67-115">If `object1` and `object2` both refer to the exact same object instance, `result` is `True`; if they do not, `result` is `False`.</span></span>  
  
 <span data-ttu-id="bac67-116">`Is`peut également être utilisé avec le `TypeOf` mot clé pour créer une `TypeOf` expression... `Is` , qui teste si une variable objet est compatible avec un type de données.</span><span class="sxs-lookup"><span data-stu-id="bac67-116">`Is` can also be used with the `TypeOf` keyword to make a `TypeOf`...`Is` expression, which tests whether an object variable is compatible with a data type.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bac67-117">Le `Is` mot clé est également utilisé dans la [sélection... Instruction case](../statements/select-case-statement.md).</span><span class="sxs-lookup"><span data-stu-id="bac67-117">The `Is` keyword is also used in the [Select...Case Statement](../statements/select-case-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bac67-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="bac67-118">Example</span></span>  
 <span data-ttu-id="bac67-119">L’exemple suivant utilise l' `Is` opérateur pour comparer des paires de références d’objets.</span><span class="sxs-lookup"><span data-stu-id="bac67-119">The following example uses the `Is` operator to compare pairs of object references.</span></span> <span data-ttu-id="bac67-120">Les résultats sont assignés à une `Boolean` valeur indiquant si les deux objets sont identiques.</span><span class="sxs-lookup"><span data-stu-id="bac67-120">The results are assigned to a `Boolean` value representing whether the two objects are identical.</span></span>  
  
 [!code-vb[VbVbalrOperators#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#27)]  
  
 <span data-ttu-id="bac67-121">Comme le montre l’exemple précédent, vous pouvez utiliser l' `Is` opérateur pour tester à la fois les objets à liaison anticipée et les objets à liaison tardive.</span><span class="sxs-lookup"><span data-stu-id="bac67-121">As the preceding example demonstrates, you can use the `Is` operator to test both early bound and late bound objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bac67-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bac67-122">See also</span></span>

- [<span data-ttu-id="bac67-123">TypeOf, opérateur</span><span class="sxs-lookup"><span data-stu-id="bac67-123">TypeOf Operator</span></span>](typeof-operator.md)
- [<span data-ttu-id="bac67-124">IsNot, opérateur</span><span class="sxs-lookup"><span data-stu-id="bac67-124">IsNot Operator</span></span>](isnot-operator.md)
- [<span data-ttu-id="bac67-125">Comparison Operators in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bac67-125">Comparison Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [<span data-ttu-id="bac67-126">Priorité des opérateurs en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bac67-126">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="bac67-127">Opérateurs listés par fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="bac67-127">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="bac67-128">Opérateurs et expressions</span><span class="sxs-lookup"><span data-stu-id="bac67-128">Operators and Expressions</span></span>](../../programming-guide/language-features/operators-and-expressions/index.md)
