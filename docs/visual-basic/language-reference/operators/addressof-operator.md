---
title: AddressOf, opérateur
ms.date: 07/20/2015
f1_keywords:
- AddressOf
- vb.AddressOf
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- addresses, passing to API procedures
ms.assetid: 8105a59d-60d8-4ab5-b221-5899cdfacbf4
ms.openlocfilehash: e88520bd7e731a35b98c1d40c5210dc5d1314911
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350282"
---
# <a name="addressof-operator-visual-basic"></a><span data-ttu-id="72b1f-102">Opérateur AddressOf (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="72b1f-102">AddressOf Operator (Visual Basic)</span></span>
<span data-ttu-id="72b1f-103">Crée une instance de délégué qui fait référence à la procédure spécifique.</span><span class="sxs-lookup"><span data-stu-id="72b1f-103">Creates a delegate instance that references the specific procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72b1f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="72b1f-104">Syntax</span></span>  
  
```vb  
AddressOf procedurename  
```  
  
## <a name="parts"></a><span data-ttu-id="72b1f-105">Composants</span><span class="sxs-lookup"><span data-stu-id="72b1f-105">Parts</span></span>  
 `procedurename`  
 <span data-ttu-id="72b1f-106">Requis.</span><span class="sxs-lookup"><span data-stu-id="72b1f-106">Required.</span></span> <span data-ttu-id="72b1f-107">Spécifie la procédure à référencer par le délégué nouvellement créé.</span><span class="sxs-lookup"><span data-stu-id="72b1f-107">Specifies the procedure to be referenced by the newly created delegate.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="72b1f-108">Notes</span><span class="sxs-lookup"><span data-stu-id="72b1f-108">Remarks</span></span>  
 <span data-ttu-id="72b1f-109">L’opérateur `AddressOf` crée un délégué qui pointe vers la sous ou la fonction spécifiée par `procedurename`.</span><span class="sxs-lookup"><span data-stu-id="72b1f-109">The `AddressOf` operator creates a delegate that points to the sub or function specified by `procedurename`.</span></span> <span data-ttu-id="72b1f-110">Lorsque la procédure spécifiée est une méthode d’instance, le délégué fait référence à la fois à l’instance et à la méthode.</span><span class="sxs-lookup"><span data-stu-id="72b1f-110">When the specified procedure is an instance method then the delegate refers to both the instance and the method.</span></span> <span data-ttu-id="72b1f-111">Ensuite, lorsque le délégué est appelé, la méthode spécifiée de l’instance spécifiée est appelée.</span><span class="sxs-lookup"><span data-stu-id="72b1f-111">Then, when the  delegate is invoked the specified method of the specified instance is called.</span></span>  
  
 <span data-ttu-id="72b1f-112">L’opérateur `AddressOf` peut être utilisé comme opérande d’un constructeur délégué ou il peut être utilisé dans un contexte dans lequel le type du délégué peut être déterminé par le compilateur.</span><span class="sxs-lookup"><span data-stu-id="72b1f-112">The `AddressOf` operator can be used as the operand of a delegate constructor or it can be used in a context in which the type of the delegate can be determined by the compiler.</span></span>  
  
## <a name="example"></a><span data-ttu-id="72b1f-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="72b1f-113">Example</span></span>  
 <span data-ttu-id="72b1f-114">Cet exemple utilise l’opérateur `AddressOf` pour désigner un délégué qui gère l’événement `Click` d’un bouton.</span><span class="sxs-lookup"><span data-stu-id="72b1f-114">This example uses the `AddressOf` operator to designate a delegate to handle the `Click` event of a button.</span></span>  
  
 [!code-vb[VbVbalrDelegates#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="72b1f-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="72b1f-115">Example</span></span>  
 <span data-ttu-id="72b1f-116">L’exemple suivant utilise l’opérateur `AddressOf` pour désigner la fonction de démarrage d’un thread.</span><span class="sxs-lookup"><span data-stu-id="72b1f-116">The following example uses the `AddressOf` operator to designate the startup function for a thread.</span></span>  
  
 [!code-vb[VbVbalrDelegates#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="72b1f-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="72b1f-117">See also</span></span>

- [<span data-ttu-id="72b1f-118">Declare Statement</span><span class="sxs-lookup"><span data-stu-id="72b1f-118">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
- [<span data-ttu-id="72b1f-119">Function (instruction)</span><span class="sxs-lookup"><span data-stu-id="72b1f-119">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="72b1f-120">Sub (instruction)</span><span class="sxs-lookup"><span data-stu-id="72b1f-120">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="72b1f-121">Délégués</span><span class="sxs-lookup"><span data-stu-id="72b1f-121">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)
