---
title: Opérateur AddressOf (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- AddressOf
- vb.AddressOf
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- addresses, passing to API procedures
ms.assetid: 8105a59d-60d8-4ab5-b221-5899cdfacbf4
ms.openlocfilehash: 098ca95687d8b0e9f4ac90d5c7e0df9a9a0ad950
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760375"
---
# <a name="addressof-operator-visual-basic"></a><span data-ttu-id="b35f3-102">Opérateur AddressOf (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b35f3-102">AddressOf Operator (Visual Basic)</span></span>
<span data-ttu-id="b35f3-103">Crée une instance de délégué qui fait référence à la procédure spécifique.</span><span class="sxs-lookup"><span data-stu-id="b35f3-103">Creates a delegate instance that references the specific procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b35f3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b35f3-104">Syntax</span></span>  
  
```  
AddressOf procedurename  
```  
  
## <a name="parts"></a><span data-ttu-id="b35f3-105">Composants</span><span class="sxs-lookup"><span data-stu-id="b35f3-105">Parts</span></span>  
 `procedurename`  
 <span data-ttu-id="b35f3-106">Requis.</span><span class="sxs-lookup"><span data-stu-id="b35f3-106">Required.</span></span> <span data-ttu-id="b35f3-107">Indique la procédure à référencer par le délégué nouvellement créé.</span><span class="sxs-lookup"><span data-stu-id="b35f3-107">Specifies the procedure to be referenced by the newly created delegate.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b35f3-108">Notes</span><span class="sxs-lookup"><span data-stu-id="b35f3-108">Remarks</span></span>  
 <span data-ttu-id="b35f3-109">Le `AddressOf` opérateur crée un délégué qui pointe vers le sub ou de la fonction spécifiée par `procedurename`.</span><span class="sxs-lookup"><span data-stu-id="b35f3-109">The `AddressOf` operator creates a delegate that points to the sub or function specified by `procedurename`.</span></span> <span data-ttu-id="b35f3-110">Lorsque la procédure spécifiée est qu'une méthode d’instance puis le délégué fait référence à l’instance et la méthode.</span><span class="sxs-lookup"><span data-stu-id="b35f3-110">When the specified procedure is an instance method then the delegate refers to both the instance and the method.</span></span> <span data-ttu-id="b35f3-111">Ensuite, lorsque le délégué est appelé la méthode spécifiée de l’instance spécifiée est appelée.</span><span class="sxs-lookup"><span data-stu-id="b35f3-111">Then, when the  delegate is invoked the specified method of the specified instance is called.</span></span>  
  
 <span data-ttu-id="b35f3-112">Le `AddressOf` opérateur peut être utilisé comme opérande d’un constructeur délégué ou il peut être utilisé dans un contexte dans lequel le type du délégué peut être déterminé par le compilateur.</span><span class="sxs-lookup"><span data-stu-id="b35f3-112">The `AddressOf` operator can be used as the operand of a delegate constructor or it can be used in a context in which the type of the delegate can be determined by the compiler.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b35f3-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="b35f3-113">Example</span></span>  
 <span data-ttu-id="b35f3-114">Cet exemple utilise le `AddressOf` opérateur pour désigner un délégué pour gérer le `Click` événements d’un bouton.</span><span class="sxs-lookup"><span data-stu-id="b35f3-114">This example uses the `AddressOf` operator to designate a delegate to handle the `Click` event of a button.</span></span>  
  
 [!code-vb[VbVbalrDelegates#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="b35f3-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="b35f3-115">Example</span></span>  
 <span data-ttu-id="b35f3-116">L’exemple suivant utilise le `AddressOf` opérateur pour désigner la fonction de démarrage d’un thread.</span><span class="sxs-lookup"><span data-stu-id="b35f3-116">The following example uses the `AddressOf` operator to designate the startup function for a thread.</span></span>  
  
 [!code-vb[VbVbalrDelegates#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="b35f3-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b35f3-117">See also</span></span>

- [<span data-ttu-id="b35f3-118">Declare (instruction)</span><span class="sxs-lookup"><span data-stu-id="b35f3-118">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
- [<span data-ttu-id="b35f3-119">Function (instruction)</span><span class="sxs-lookup"><span data-stu-id="b35f3-119">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="b35f3-120">Sub (instruction)</span><span class="sxs-lookup"><span data-stu-id="b35f3-120">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="b35f3-121">Délégués</span><span class="sxs-lookup"><span data-stu-id="b35f3-121">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)
