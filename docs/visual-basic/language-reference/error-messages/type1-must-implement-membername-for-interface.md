---
title: <type1><typename> doit implémenter <membername> pour l’interface <interfacename>
ms.date: 07/20/2015
f1_keywords:
- vbc30154
- bc30154
helpviewer_keywords:
- BC30154
ms.assetid: 259afdfa-3608-4760-adcb-88ec0da5020d
ms.openlocfilehash: 4ffe18e11c388a8c69ef0592bde1b78f5b219680
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84386852"
---
# <a name="type1typename-must-implement-membername-for-interface-interfacename"></a><span data-ttu-id="3ab81-102">\<type1>\<typename> doit implémenter \<membername> pour l’interface \<interfacename></span><span class="sxs-lookup"><span data-stu-id="3ab81-102">\<type1>'\<typename>' must implement '\<membername>' for interface '\<interfacename>'</span></span>
<span data-ttu-id="3ab81-103">' \<typename> 'doit implémenter' \<membername> 'pour l’interface' \<interfacename> '.</span><span class="sxs-lookup"><span data-stu-id="3ab81-103">'\<typename>' must implement '\<membername>' for interface '\<interfacename>'.</span></span> <span data-ttu-id="3ab81-104">La propriété d’implémentation doit avoir des spécificateurs’ReadOnly'/'WriteOnly’correspondants.</span><span class="sxs-lookup"><span data-stu-id="3ab81-104">Implementing property must have matching 'ReadOnly'/'WriteOnly' specifiers.</span></span>  
  
 <span data-ttu-id="3ab81-105">Une classe ou une structure prétend implémenter une interface, mais n’implémente pas une procédure, une propriété ou un événement défini par l’interface.</span><span class="sxs-lookup"><span data-stu-id="3ab81-105">A class or structure claims to implement an interface but does not implement a procedure, property, or event defined by the interface.</span></span> <span data-ttu-id="3ab81-106">Chaque membre de l’interface doit être implémenté.</span><span class="sxs-lookup"><span data-stu-id="3ab81-106">Every member of the interface must be implemented.</span></span>  
  
 <span data-ttu-id="3ab81-107">**ID d’erreur :** BC30154</span><span class="sxs-lookup"><span data-stu-id="3ab81-107">**Error ID:** BC30154</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="3ab81-108">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="3ab81-108">To correct this error</span></span>  
  
1. <span data-ttu-id="3ab81-109">Déclarez un membre avec le même nom et la même signature que ceux définis dans l’interface.</span><span class="sxs-lookup"><span data-stu-id="3ab81-109">Declare a member with the same name and signature as defined in the interface.</span></span> <span data-ttu-id="3ab81-110">Veillez à inclure au moins l' `End Function` `End Sub` instruction, ou `End Property` .</span><span class="sxs-lookup"><span data-stu-id="3ab81-110">Be sure to include at least the `End Function`, `End Sub`, or `End Property` statement.</span></span>  
  
2. <span data-ttu-id="3ab81-111">Ajoutez une `Implements` clause à la fin de l' `Function` instruction,, `Sub` `Property` ou `Event` .</span><span class="sxs-lookup"><span data-stu-id="3ab81-111">Add an `Implements` clause to the end of the `Function`, `Sub`, `Property`, or `Event` statement.</span></span> <span data-ttu-id="3ab81-112">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="3ab81-112">For example:</span></span>  
  
    ```vb  
    Public Event ItHappened() Implements IBaseInterface.ItHappened  
    ```  
  
3. <span data-ttu-id="3ab81-113">Lors de l’implémentation d’une propriété, assurez-vous que `ReadOnly` ou `WriteOnly` est utilisé de la même façon que dans la définition de l’interface.</span><span class="sxs-lookup"><span data-stu-id="3ab81-113">When implementing a property, make sure that `ReadOnly` or `WriteOnly` is used in the same way as in the interface definition.</span></span>  
  
4. <span data-ttu-id="3ab81-114">Lors de l’implémentation d’une propriété, déclarez `Get` et des `Set` procédures, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="3ab81-114">When implementing a property, declare `Get` and `Set` procedures, as appropriate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ab81-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3ab81-115">See also</span></span>

- [<span data-ttu-id="3ab81-116">Implements, instruction</span><span class="sxs-lookup"><span data-stu-id="3ab81-116">Implements Statement</span></span>](../statements/implements-statement.md)
- [<span data-ttu-id="3ab81-117">Interfaces</span><span class="sxs-lookup"><span data-stu-id="3ab81-117">Interfaces</span></span>](../../programming-guide/language-features/interfaces/index.md)
