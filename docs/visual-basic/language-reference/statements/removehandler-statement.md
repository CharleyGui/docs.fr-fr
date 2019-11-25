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
# <a name="removehandler-statement"></a><span data-ttu-id="d5a1a-102">RemoveHandler, instruction</span><span class="sxs-lookup"><span data-stu-id="d5a1a-102">RemoveHandler Statement</span></span>
<span data-ttu-id="d5a1a-103">Removes the association between an event and an event handler.</span><span class="sxs-lookup"><span data-stu-id="d5a1a-103">Removes the association between an event and an event handler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5a1a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d5a1a-104">Syntax</span></span>  
  
```vb  
RemoveHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a><span data-ttu-id="d5a1a-105">Composants</span><span class="sxs-lookup"><span data-stu-id="d5a1a-105">Parts</span></span>  
  
|<span data-ttu-id="d5a1a-106">Terme</span><span class="sxs-lookup"><span data-stu-id="d5a1a-106">Term</span></span>|<span data-ttu-id="d5a1a-107">Définition</span><span class="sxs-lookup"><span data-stu-id="d5a1a-107">Definition</span></span>|  
|---|---|  
|`event`|<span data-ttu-id="d5a1a-108">The name of the event being handled.</span><span class="sxs-lookup"><span data-stu-id="d5a1a-108">The name of the event being handled.</span></span>|  
|`eventhandler`|<span data-ttu-id="d5a1a-109">The name of the procedure currently handling the event.</span><span class="sxs-lookup"><span data-stu-id="d5a1a-109">The name of the procedure currently handling the event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d5a1a-110">Notes</span><span class="sxs-lookup"><span data-stu-id="d5a1a-110">Remarks</span></span>  
 <span data-ttu-id="d5a1a-111">The `AddHandler` and `RemoveHandler` statements allow you to start and stop event handling for a specific event at any time during program execution.</span><span class="sxs-lookup"><span data-stu-id="d5a1a-111">The `AddHandler` and `RemoveHandler` statements allow you to start and stop event handling for a specific event at any time during program execution.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d5a1a-112">For custom events, the `RemoveHandler` statement invokes the event's `RemoveHandler` accessor.</span><span class="sxs-lookup"><span data-stu-id="d5a1a-112">For custom events, the `RemoveHandler` statement invokes the event's `RemoveHandler` accessor.</span></span> <span data-ttu-id="d5a1a-113">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="d5a1a-113">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d5a1a-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="d5a1a-114">Example</span></span>  
 [!code-vb[VbVbalrEvents#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#17)]  
  
## <a name="see-also"></a><span data-ttu-id="d5a1a-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d5a1a-115">See also</span></span>

- [<span data-ttu-id="d5a1a-116">AddHandler (instruction)</span><span class="sxs-lookup"><span data-stu-id="d5a1a-116">AddHandler Statement</span></span>](../../../visual-basic/language-reference/statements/addhandler-statement.md)
- [<span data-ttu-id="d5a1a-117">Handles</span><span class="sxs-lookup"><span data-stu-id="d5a1a-117">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)
- [<span data-ttu-id="d5a1a-118">Event (instruction)</span><span class="sxs-lookup"><span data-stu-id="d5a1a-118">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)
- [<span data-ttu-id="d5a1a-119">Événements</span><span class="sxs-lookup"><span data-stu-id="d5a1a-119">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
