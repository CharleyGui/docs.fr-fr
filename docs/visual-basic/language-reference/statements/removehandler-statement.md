---
title: RemoveHandler, instruction
ms.date: 07/20/2015
f1_keywords:
- vb.RemoveHandlerMethod
- vb.RemoveHandler
- RemoveHandler
helpviewer_keywords:
- RemoveHandler keyword [Visual Basic]
- RemoveHandler statement [Visual Basic]
ms.assetid: 647cd825-e877-4910-b4f1-8d168beebe6a
ms.openlocfilehash: 177952acf362ccb36a36b5f09b11a1a93dbefa29
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74333036"
---
# <a name="removehandler-statement"></a><span data-ttu-id="59c98-102">RemoveHandler, instruction</span><span class="sxs-lookup"><span data-stu-id="59c98-102">RemoveHandler Statement</span></span>
<span data-ttu-id="59c98-103">Supprime l’association entre un événement et un gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="59c98-103">Removes the association between an event and an event handler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59c98-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="59c98-104">Syntax</span></span>  
  
```vb  
RemoveHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a><span data-ttu-id="59c98-105">Composants</span><span class="sxs-lookup"><span data-stu-id="59c98-105">Parts</span></span>  
  
|<span data-ttu-id="59c98-106">Terme</span><span class="sxs-lookup"><span data-stu-id="59c98-106">Term</span></span>|<span data-ttu-id="59c98-107">Définition</span><span class="sxs-lookup"><span data-stu-id="59c98-107">Definition</span></span>|  
|---|---|  
|`event`|<span data-ttu-id="59c98-108">Nom de l’événement géré.</span><span class="sxs-lookup"><span data-stu-id="59c98-108">The name of the event being handled.</span></span>|  
|`eventhandler`|<span data-ttu-id="59c98-109">Nom de la procédure qui gère actuellement l’événement.</span><span class="sxs-lookup"><span data-stu-id="59c98-109">The name of the procedure currently handling the event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="59c98-110">Notes</span><span class="sxs-lookup"><span data-stu-id="59c98-110">Remarks</span></span>  
 <span data-ttu-id="59c98-111">Les instructions `AddHandler` et `RemoveHandler` vous permettent de démarrer et d’arrêter la gestion des événements pour un événement spécifique à tout moment pendant l’exécution du programme.</span><span class="sxs-lookup"><span data-stu-id="59c98-111">The `AddHandler` and `RemoveHandler` statements allow you to start and stop event handling for a specific event at any time during program execution.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="59c98-112">Pour les événements personnalisés, l’instruction `RemoveHandler` appelle l’accesseur `RemoveHandler` de l’événement.</span><span class="sxs-lookup"><span data-stu-id="59c98-112">For custom events, the `RemoveHandler` statement invokes the event's `RemoveHandler` accessor.</span></span> <span data-ttu-id="59c98-113">Pour plus d’informations sur les événements personnalisés, consultez [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="59c98-113">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="59c98-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="59c98-114">Example</span></span>  
 [!code-vb[VbVbalrEvents#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#17)]  
  
## <a name="see-also"></a><span data-ttu-id="59c98-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="59c98-115">See also</span></span>

- [<span data-ttu-id="59c98-116">AddHandler (instruction)</span><span class="sxs-lookup"><span data-stu-id="59c98-116">AddHandler Statement</span></span>](../../../visual-basic/language-reference/statements/addhandler-statement.md)
- [<span data-ttu-id="59c98-117">Handles</span><span class="sxs-lookup"><span data-stu-id="59c98-117">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)
- [<span data-ttu-id="59c98-118">Event (instruction)</span><span class="sxs-lookup"><span data-stu-id="59c98-118">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)
- [<span data-ttu-id="59c98-119">Événements</span><span class="sxs-lookup"><span data-stu-id="59c98-119">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
