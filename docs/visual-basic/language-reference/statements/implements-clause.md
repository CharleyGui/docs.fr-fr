---
title: Implements (clause)
ms.date: 07/20/2015
f1_keywords:
- vb.ImplementsClause
helpviewer_keywords:
- interface implementation [Visual Basic], reimplementation
- interface members [Visual Basic], reimplementation
- interface members [Visual Basic], Implements keyword
- interface members
- members [Visual Basic], reimplementation
- interface implementation [Visual Basic], Implements keyword
- interface members [Visual Basic], implementing
- Implements keyword [Visual Basic]
- Implements statement [Visual Basic], about Implements
- members [Visual Basic], implementing
- members [Visual Basic], Implements keyword
- reimplementation
ms.assetid: 5252cdf9-964d-4fc6-af0f-0449b7126b5a
ms.openlocfilehash: 7c95cf76b1bac24e2a0f20857b8984d54ebbea85
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866159"
---
# <a name="implements-clause-visual-basic"></a><span data-ttu-id="1f332-102">Implements, clause (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1f332-102">Implements Clause (Visual Basic)</span></span>

<span data-ttu-id="1f332-103">Indique qu’un membre de classe ou de structure fournit l’implémentation d’un membre défini dans une interface.</span><span class="sxs-lookup"><span data-stu-id="1f332-103">Indicates that a class or structure member is providing the implementation for a member defined in an interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1f332-104">Notes</span><span class="sxs-lookup"><span data-stu-id="1f332-104">Remarks</span></span>  

<span data-ttu-id="1f332-105">Le `Implements` mot clé n’est pas le même que l' [instruction Implements](implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="1f332-105">The `Implements` keyword is not the same as the [Implements Statement](implements-statement.md).</span></span> <span data-ttu-id="1f332-106">Utilisez l' `Implements` instruction pour spécifier qu’une classe ou une structure implémente une ou plusieurs interfaces, puis, pour chaque membre, vous utilisez le `Implements` mot clé pour spécifier l’interface et le membre qu’elle implémente.</span><span class="sxs-lookup"><span data-stu-id="1f332-106">You use the `Implements` statement to specify that a class or structure implements one or more interfaces, and then for each member you use the `Implements` keyword to specify which interface and which member it implements.</span></span>

<span data-ttu-id="1f332-107">Si une classe ou une structure implémente une interface, elle doit inclure l' `Implements` instruction immédiatement après l’instruction de la [classe](class-statement.md) ou de la [structure](structure-statement.md), et elle doit implémenter tous les membres définis par l’interface.</span><span class="sxs-lookup"><span data-stu-id="1f332-107">If a class or structure implements an interface, it must include the `Implements` statement immediately after the [Class Statement](class-statement.md) or [Structure Statement](structure-statement.md), and it must implement all the members defined by the interface.</span></span>

## <a name="reimplementation"></a><span data-ttu-id="1f332-108">Réimplémentation</span><span class="sxs-lookup"><span data-stu-id="1f332-108">Reimplementation</span></span>  

<span data-ttu-id="1f332-109">Dans une classe dérivée, vous pouvez réimplémenter un membre d’interface que la classe de base a déjà implémenté.</span><span class="sxs-lookup"><span data-stu-id="1f332-109">In a derived class, you can reimplement an interface member that the base class has already implemented.</span></span> <span data-ttu-id="1f332-110">Cela diffère de la substitution du membre de classe de base dans les aspects suivants :</span><span class="sxs-lookup"><span data-stu-id="1f332-110">This is different from overriding the base class member in the following respects:</span></span>

- <span data-ttu-id="1f332-111">Le membre de la classe de base n’a pas besoin d’être [substituable](../modifiers/overridable.md) pour être réimplémenté.</span><span class="sxs-lookup"><span data-stu-id="1f332-111">The base class member does not need to be [Overridable](../modifiers/overridable.md) to be reimplemented.</span></span>
- <span data-ttu-id="1f332-112">Vous pouvez réimplémenter le membre avec un nom différent.</span><span class="sxs-lookup"><span data-stu-id="1f332-112">You can reimplement the member with a different name.</span></span>

<span data-ttu-id="1f332-113">Le `Implements` mot clé peut être utilisé dans les contextes suivants :</span><span class="sxs-lookup"><span data-stu-id="1f332-113">The `Implements` keyword can be used in the following contexts:</span></span>

- [<span data-ttu-id="1f332-114">Event, instruction</span><span class="sxs-lookup"><span data-stu-id="1f332-114">Event Statement</span></span>](event-statement.md)
- [<span data-ttu-id="1f332-115">Function (instruction)</span><span class="sxs-lookup"><span data-stu-id="1f332-115">Function Statement</span></span>](function-statement.md)
- [<span data-ttu-id="1f332-116">Property Statement</span><span class="sxs-lookup"><span data-stu-id="1f332-116">Property Statement</span></span>](property-statement.md)
- [<span data-ttu-id="1f332-117">Sub (instruction)</span><span class="sxs-lookup"><span data-stu-id="1f332-117">Sub Statement</span></span>](sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="1f332-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1f332-118">See also</span></span>

- [<span data-ttu-id="1f332-119">Implements, instruction</span><span class="sxs-lookup"><span data-stu-id="1f332-119">Implements Statement</span></span>](implements-statement.md)
- [<span data-ttu-id="1f332-120">Interface (instruction)</span><span class="sxs-lookup"><span data-stu-id="1f332-120">Interface Statement</span></span>](interface-statement.md)
- [<span data-ttu-id="1f332-121">Class (instruction)</span><span class="sxs-lookup"><span data-stu-id="1f332-121">Class Statement</span></span>](class-statement.md)
- [<span data-ttu-id="1f332-122">Structure, instruction</span><span class="sxs-lookup"><span data-stu-id="1f332-122">Structure Statement</span></span>](structure-statement.md)
