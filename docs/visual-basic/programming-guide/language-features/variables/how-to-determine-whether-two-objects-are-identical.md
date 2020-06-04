---
title: 'Comment : déterminer si deux objets sont identiques'
ms.date: 07/20/2015
helpviewer_keywords:
- testing [Visual Basic], objects
- objects [Visual Basic], comparing
- object variables [Visual Basic], determining identity
ms.assetid: 7829f817-0d1f-4749-a707-de0b95e0cf5c
ms.openlocfilehash: 67c3af8b7bdac3ad1c7e4908f1ac2684df7a87aa
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410475"
---
# <a name="how-to-determine-whether-two-objects-are-identical-visual-basic"></a><span data-ttu-id="c63e6-102">Comment : déterminer si deux objets sont identiques (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c63e6-102">How to: Determine Whether Two Objects Are Identical (Visual Basic)</span></span>
<span data-ttu-id="c63e6-103">Dans Visual Basic, deux références de variables sont considérées comme identiques si leurs pointeurs sont identiques, autrement dit, si les deux variables pointent vers la même instance de classe en mémoire.</span><span class="sxs-lookup"><span data-stu-id="c63e6-103">In Visual Basic, two variable references are considered identical if their pointers are the same, that is, if both variables point to the same class instance in memory.</span></span> <span data-ttu-id="c63e6-104">Par exemple, dans une application Windows Forms, vous souhaiterez peut-être effectuer une comparaison pour déterminer si l’instance actuelle ( `Me` ) est identique à une instance particulière, telle que `Form2` .</span><span class="sxs-lookup"><span data-stu-id="c63e6-104">For example, in a Windows Forms application, you might want to make a comparison to determine whether the current instance (`Me`) is the same as a particular instance, such as `Form2`.</span></span>  
  
 <span data-ttu-id="c63e6-105">Visual Basic fournit deux opérateurs pour comparer des pointeurs.</span><span class="sxs-lookup"><span data-stu-id="c63e6-105">Visual Basic provides two operators to compare pointers.</span></span> <span data-ttu-id="c63e6-106">L' [opérateur is](../../../language-reference/operators/is-operator.md) retourne `True` si les objets sont identiques, et l' [opérateur IsNot](../../../language-reference/operators/isnot-operator.md) retourne `True` s’ils ne le sont pas.</span><span class="sxs-lookup"><span data-stu-id="c63e6-106">The [Is Operator](../../../language-reference/operators/is-operator.md) returns `True` if the objects are identical, and the [IsNot Operator](../../../language-reference/operators/isnot-operator.md) returns `True` if they are not.</span></span>  
  
## <a name="determining-if-two-objects-are-identical"></a><span data-ttu-id="c63e6-107">Déterminer si deux objets sont identiques</span><span class="sxs-lookup"><span data-stu-id="c63e6-107">Determining if Two Objects Are Identical</span></span>  
  
#### <a name="to-determine-if-two-objects-are-identical"></a><span data-ttu-id="c63e6-108">Pour déterminer si deux objets sont identiques</span><span class="sxs-lookup"><span data-stu-id="c63e6-108">To determine if two objects are identical</span></span>  
  
1. <span data-ttu-id="c63e6-109">Configurez une `Boolean` expression pour tester les deux objets.</span><span class="sxs-lookup"><span data-stu-id="c63e6-109">Set up a `Boolean` expression to test the two objects.</span></span>  
  
2. <span data-ttu-id="c63e6-110">Dans votre expression de test, utilisez l' `Is` opérateur avec les deux objets en tant qu’opérandes.</span><span class="sxs-lookup"><span data-stu-id="c63e6-110">In your testing expression, use the `Is` operator with the two objects as operands.</span></span>  
  
     <span data-ttu-id="c63e6-111">`Is`retourne `True` si les objets pointent vers la même instance de classe.</span><span class="sxs-lookup"><span data-stu-id="c63e6-111">`Is` returns `True` if the objects point to the same class instance.</span></span>  
  
## <a name="determining-if-two-objects-are-not-identical"></a><span data-ttu-id="c63e6-112">Déterminer si deux objets ne sont pas identiques</span><span class="sxs-lookup"><span data-stu-id="c63e6-112">Determining if Two Objects Are Not Identical</span></span>  
 <span data-ttu-id="c63e6-113">Parfois, vous souhaitez effectuer une action si les deux objets ne sont pas identiques, et il peut être difficile de combiner `Not` et `Is` , par exemple `If Not obj1 Is obj2` .</span><span class="sxs-lookup"><span data-stu-id="c63e6-113">Sometimes you want to perform an action if the two objects are not identical, and it can be awkward to combine `Not` and `Is`, for example `If Not obj1 Is obj2`.</span></span> <span data-ttu-id="c63e6-114">Dans ce cas, vous pouvez utiliser l' `IsNot` opérateur.</span><span class="sxs-lookup"><span data-stu-id="c63e6-114">In such a case you can use the `IsNot` operator.</span></span>  
  
#### <a name="to-determine-if-two-objects-are-not-identical"></a><span data-ttu-id="c63e6-115">Pour déterminer si deux objets ne sont pas identiques</span><span class="sxs-lookup"><span data-stu-id="c63e6-115">To determine if two objects are not identical</span></span>  
  
1. <span data-ttu-id="c63e6-116">Configurez une `Boolean` expression pour tester les deux objets.</span><span class="sxs-lookup"><span data-stu-id="c63e6-116">Set up a `Boolean` expression to test the two objects.</span></span>  
  
2. <span data-ttu-id="c63e6-117">Dans votre expression de test, utilisez l' `IsNot` opérateur avec les deux objets en tant qu’opérandes.</span><span class="sxs-lookup"><span data-stu-id="c63e6-117">In your testing expression, use the `IsNot` operator with the two objects as operands.</span></span>  
  
     <span data-ttu-id="c63e6-118">`IsNot`retourne `True` si les objets ne pointent pas vers la même instance de classe.</span><span class="sxs-lookup"><span data-stu-id="c63e6-118">`IsNot` returns `True` if the objects do not point to the same class instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c63e6-119">Exemple</span><span class="sxs-lookup"><span data-stu-id="c63e6-119">Example</span></span>  
 <span data-ttu-id="c63e6-120">L’exemple suivant teste des paires de `Object` variables pour voir si elles pointent vers la même instance de classe.</span><span class="sxs-lookup"><span data-stu-id="c63e6-120">The following example tests pairs of `Object` variables to see if they point to the same class instance.</span></span>  
  
 [!code-vb[VbVbalrKeywords#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class7.vb#14)]  
  
 <span data-ttu-id="c63e6-121">L’exemple précédent affiche la sortie suivante.</span><span class="sxs-lookup"><span data-stu-id="c63e6-121">The preceding example displays the following output.</span></span>  
  
 `objA different from objB? True`  
  
 `objA identical to objC? True`  
  
## <a name="see-also"></a><span data-ttu-id="c63e6-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c63e6-122">See also</span></span>

- [<span data-ttu-id="c63e6-123">Object Data Type</span><span class="sxs-lookup"><span data-stu-id="c63e6-123">Object Data Type</span></span>](../../../language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="c63e6-124">Variables objets</span><span class="sxs-lookup"><span data-stu-id="c63e6-124">Object Variables</span></span>](object-variables.md)
- [<span data-ttu-id="c63e6-125">Valeurs des variables objets</span><span class="sxs-lookup"><span data-stu-id="c63e6-125">Object Variable Values</span></span>](object-variable-values.md)
- [<span data-ttu-id="c63e6-126">Is, opérateur</span><span class="sxs-lookup"><span data-stu-id="c63e6-126">Is Operator</span></span>](../../../language-reference/operators/is-operator.md)
- [<span data-ttu-id="c63e6-127">IsNot, opérateur</span><span class="sxs-lookup"><span data-stu-id="c63e6-127">IsNot Operator</span></span>](../../../language-reference/operators/isnot-operator.md)
- [<span data-ttu-id="c63e6-128">Comment : déterminer si deux objets sont liés</span><span class="sxs-lookup"><span data-stu-id="c63e6-128">How to: Determine Whether Two Objects Are Related</span></span>](how-to-determine-whether-two-objects-are-related.md)
- [<span data-ttu-id="c63e6-129">Me, My, MyBase et MyClass</span><span class="sxs-lookup"><span data-stu-id="c63e6-129">Me, My, MyBase, and MyClass</span></span>](../../program-structure/me-my-mybase-and-myclass.md)
