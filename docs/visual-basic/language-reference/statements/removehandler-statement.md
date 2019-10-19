---
title: RemoveHandler, instruction (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.RemoveHandlerMethod
- vb.RemoveHandler
- RemoveHandler
helpviewer_keywords:
- RemoveHandler keyword [Visual Basic]
- RemoveHandler statement [Visual Basic]
ms.assetid: 647cd825-e877-4910-b4f1-8d168beebe6a
ms.openlocfilehash: 47f35bd76d7734878e7b5b206b4aecd856276593
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582024"
---
# <a name="removehandler-statement"></a><span data-ttu-id="5f286-102">RemoveHandler, instruction</span><span class="sxs-lookup"><span data-stu-id="5f286-102">RemoveHandler Statement</span></span>
<span data-ttu-id="5f286-103">Supprime l’association entre un événement et un gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="5f286-103">Removes the association between an event and an event handler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f286-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5f286-104">Syntax</span></span>  
  
```vb  
RemoveHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a><span data-ttu-id="5f286-105">Composants</span><span class="sxs-lookup"><span data-stu-id="5f286-105">Parts</span></span>  
  
|<span data-ttu-id="5f286-106">Terme</span><span class="sxs-lookup"><span data-stu-id="5f286-106">Term</span></span>|<span data-ttu-id="5f286-107">Définition</span><span class="sxs-lookup"><span data-stu-id="5f286-107">Definition</span></span>|  
|---|---|  
|`event`|<span data-ttu-id="5f286-108">Nom de l’événement géré.</span><span class="sxs-lookup"><span data-stu-id="5f286-108">The name of the event being handled.</span></span>|  
|`eventhandler`|<span data-ttu-id="5f286-109">Nom de la procédure qui gère actuellement l’événement.</span><span class="sxs-lookup"><span data-stu-id="5f286-109">The name of the procedure currently handling the event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5f286-110">Notes</span><span class="sxs-lookup"><span data-stu-id="5f286-110">Remarks</span></span>  
 <span data-ttu-id="5f286-111">Les instructions `AddHandler` et `RemoveHandler` vous permettent de démarrer et d’arrêter la gestion des événements pour un événement spécifique à tout moment pendant l’exécution du programme.</span><span class="sxs-lookup"><span data-stu-id="5f286-111">The `AddHandler` and `RemoveHandler` statements allow you to start and stop event handling for a specific event at any time during program execution.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5f286-112">Pour les événements personnalisés, l’instruction `RemoveHandler` appelle l’accesseur `RemoveHandler` de l’événement.</span><span class="sxs-lookup"><span data-stu-id="5f286-112">For custom events, the `RemoveHandler` statement invokes the event's `RemoveHandler` accessor.</span></span> <span data-ttu-id="5f286-113">Pour plus d’informations sur les événements personnalisés, consultez [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="5f286-113">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5f286-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="5f286-114">Example</span></span>  
 [!code-vb[VbVbalrEvents#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#17)]  
  
## <a name="see-also"></a><span data-ttu-id="5f286-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5f286-115">See also</span></span>

- [<span data-ttu-id="5f286-116">AddHandler (instruction)</span><span class="sxs-lookup"><span data-stu-id="5f286-116">AddHandler Statement</span></span>](../../../visual-basic/language-reference/statements/addhandler-statement.md)
- [<span data-ttu-id="5f286-117">Handles</span><span class="sxs-lookup"><span data-stu-id="5f286-117">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)
- [<span data-ttu-id="5f286-118">Event (instruction)</span><span class="sxs-lookup"><span data-stu-id="5f286-118">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)
- [<span data-ttu-id="5f286-119">Événements</span><span class="sxs-lookup"><span data-stu-id="5f286-119">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
