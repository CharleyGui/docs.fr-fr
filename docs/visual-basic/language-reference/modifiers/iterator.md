---
title: Itérateur
ms.date: 07/20/2015
f1_keywords:
- vb.Iterator
helpviewer_keywords:
- Iterator keyword [Visual Basic]
ms.assetid: 69cb0b04-ac87-49d0-bcfe-810c0d60daff
ms.openlocfilehash: 0b459a16317b8ba55886e52ecadb227ddf2fee83
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875432"
---
# <a name="iterator-visual-basic"></a><span data-ttu-id="c6ba5-102">Itérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c6ba5-102">Iterator (Visual Basic)</span></span>

<span data-ttu-id="c6ba5-103">Spécifie qu’une fonction ou un `Get` accesseur est un itérateur.</span><span class="sxs-lookup"><span data-stu-id="c6ba5-103">Specifies that a function or `Get` accessor is an iterator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c6ba5-104">Notes</span><span class="sxs-lookup"><span data-stu-id="c6ba5-104">Remarks</span></span>  

 <span data-ttu-id="c6ba5-105">Un *itérateur* exécute une itération personnalisée sur une collection.</span><span class="sxs-lookup"><span data-stu-id="c6ba5-105">An *iterator* performs a custom iteration over a collection.</span></span> <span data-ttu-id="c6ba5-106">Un itérateur utilise l’instruction [yield](../statements/yield-statement.md) pour retourner chaque élément de la collection un par un.</span><span class="sxs-lookup"><span data-stu-id="c6ba5-106">An iterator uses the [Yield](../statements/yield-statement.md) statement to return each element in the collection one at a time.</span></span> <span data-ttu-id="c6ba5-107">Quand une `Yield` instruction est atteinte, l’emplacement actuel dans le code est conservé.</span><span class="sxs-lookup"><span data-stu-id="c6ba5-107">When a `Yield` statement is reached, the current location in code is retained.</span></span> <span data-ttu-id="c6ba5-108">L'exécution redémarrera à partir de cet emplacement la prochaine fois que la fonction d'itérateur sera appelée.</span><span class="sxs-lookup"><span data-stu-id="c6ba5-108">Execution is restarted from that location the next time that the iterator function is called.</span></span>  
  
 <span data-ttu-id="c6ba5-109">Un itérateur peut être implémenté en tant que fonction ou en tant qu' `Get` accesseur d’une définition de propriété.</span><span class="sxs-lookup"><span data-stu-id="c6ba5-109">An iterator can be implemented as a function or as a `Get` accessor of a property definition.</span></span> <span data-ttu-id="c6ba5-110">Le `Iterator` modificateur apparaît dans la déclaration de la fonction d’itérateur ou de l' `Get` accesseur.</span><span class="sxs-lookup"><span data-stu-id="c6ba5-110">The `Iterator` modifier appears in the declaration of the iterator function or `Get` accessor.</span></span>  
  
 <span data-ttu-id="c6ba5-111">Vous appelez un itérateur à partir du code client à l’aide [d’un for each... Instruction suivante](../statements/for-each-next-statement.md).</span><span class="sxs-lookup"><span data-stu-id="c6ba5-111">You call an iterator from client code by using a [For Each...Next Statement](../statements/for-each-next-statement.md).</span></span>  
  
 <span data-ttu-id="c6ba5-112">Le type de retour d’une fonction ou d’un `Get` accesseur d’itérateur peut être <xref:System.Collections.IEnumerable> , <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Collections.IEnumerator> ou <xref:System.Collections.Generic.IEnumerator%601> .</span><span class="sxs-lookup"><span data-stu-id="c6ba5-112">The return type of an iterator function or `Get` accessor can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>  
  
 <span data-ttu-id="c6ba5-113">Un itérateur ne peut pas avoir de `ByRef` paramètres.</span><span class="sxs-lookup"><span data-stu-id="c6ba5-113">An iterator cannot have any `ByRef` parameters.</span></span>  
  
 <span data-ttu-id="c6ba5-114">Un itérateur ne peut pas être présent dans un événement, un constructeur d’instance, un constructeur statique ou un destructeur statique.</span><span class="sxs-lookup"><span data-stu-id="c6ba5-114">An iterator cannot occur in an event, instance constructor, static constructor, or static destructor.</span></span>  
  
 <span data-ttu-id="c6ba5-115">Un itérateur peut être une fonction anonyme.</span><span class="sxs-lookup"><span data-stu-id="c6ba5-115">An iterator can be an anonymous function.</span></span> <span data-ttu-id="c6ba5-116">Pour plus d’informations, consultez [itérateurs](../../programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="c6ba5-116">For more information, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="usage"></a><span data-ttu-id="c6ba5-117">Usage</span><span class="sxs-lookup"><span data-stu-id="c6ba5-117">Usage</span></span>  

 <span data-ttu-id="c6ba5-118">Le modificateur `Iterator` peut être utilisé dans les contextes suivants :</span><span class="sxs-lookup"><span data-stu-id="c6ba5-118">The `Iterator` modifier can be used in these contexts:</span></span>  
  
- [<span data-ttu-id="c6ba5-119">Function (instruction)</span><span class="sxs-lookup"><span data-stu-id="c6ba5-119">Function Statement</span></span>](../statements/function-statement.md)  
  
- [<span data-ttu-id="c6ba5-120">Property Statement</span><span class="sxs-lookup"><span data-stu-id="c6ba5-120">Property Statement</span></span>](../statements/property-statement.md)  
  
## <a name="example"></a><span data-ttu-id="c6ba5-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="c6ba5-121">Example</span></span>  

 <span data-ttu-id="c6ba5-122">L’exemple suivant illustre une fonction d’itérateur.</span><span class="sxs-lookup"><span data-stu-id="c6ba5-122">The following example demonstrates an iterator function.</span></span> <span data-ttu-id="c6ba5-123">La fonction Iterator a une `Yield` instruction qui se trouve à l’intérieur d’une instruction [for... Next](../statements/for-next-statement.md) .</span><span class="sxs-lookup"><span data-stu-id="c6ba5-123">The iterator function has a `Yield` statement that is inside a [For…Next](../statements/for-next-statement.md) loop.</span></span> <span data-ttu-id="c6ba5-124">Chaque itération de [pour chaque](../statements/for-each-next-statement.md) corps d’instruction dans `Main` crée un appel à la `Power` fonction d’itérateur.</span><span class="sxs-lookup"><span data-stu-id="c6ba5-124">Each iteration of the [For Each](../statements/for-each-next-statement.md) statement body in `Main` creates a call to the `Power` iterator function.</span></span> <span data-ttu-id="c6ba5-125">Chaque appel à la fonction d'itérateur continue vers l'exécution suivante de l'instruction `Yield`, qui se produit pendant l'itération suivante de la boucle `For…Next`.</span><span class="sxs-lookup"><span data-stu-id="c6ba5-125">Each call to the iterator function proceeds to the next execution of the `Yield` statement, which occurs during the next iteration of the `For…Next` loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#98)]  
  
## <a name="example"></a><span data-ttu-id="c6ba5-126">Exemple</span><span class="sxs-lookup"><span data-stu-id="c6ba5-126">Example</span></span>  

 <span data-ttu-id="c6ba5-127">L'exemple suivant illustre un accesseur `Get` qui est un itérateur.</span><span class="sxs-lookup"><span data-stu-id="c6ba5-127">The following example demonstrates a `Get` accessor that is an iterator.</span></span> <span data-ttu-id="c6ba5-128">Le `Iterator` modificateur est dans la déclaration de propriété.</span><span class="sxs-lookup"><span data-stu-id="c6ba5-128">The `Iterator` modifier is in the property declaration.</span></span>  
  
 [!code-vb[VbVbalrStatements#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#99)]  
  
 <span data-ttu-id="c6ba5-129">Pour obtenir des exemples supplémentaires, consultez [itérateurs](../../programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="c6ba5-129">For additional examples, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6ba5-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c6ba5-130">See also</span></span>

- <xref:System.Runtime.CompilerServices.IteratorStateMachineAttribute>
- [<span data-ttu-id="c6ba5-131">Iterators</span><span class="sxs-lookup"><span data-stu-id="c6ba5-131">Iterators</span></span>](../../programming-guide/concepts/iterators.md)
- [<span data-ttu-id="c6ba5-132">Yield (instruction)</span><span class="sxs-lookup"><span data-stu-id="c6ba5-132">Yield Statement</span></span>](../statements/yield-statement.md)
