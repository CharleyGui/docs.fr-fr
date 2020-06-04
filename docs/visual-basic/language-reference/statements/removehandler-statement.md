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
ms.openlocfilehash: 3514a79f2430b148e6a3727b83029b4e207a677b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404250"
---
# <a name="removehandler-statement"></a><span data-ttu-id="976b1-102">RemoveHandler, instruction</span><span class="sxs-lookup"><span data-stu-id="976b1-102">RemoveHandler Statement</span></span>
<span data-ttu-id="976b1-103">Supprime l’association entre un événement et un gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="976b1-103">Removes the association between an event and an event handler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="976b1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="976b1-104">Syntax</span></span>  
  
```vb  
RemoveHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a><span data-ttu-id="976b1-105">Éléments</span><span class="sxs-lookup"><span data-stu-id="976b1-105">Parts</span></span>  
  
|<span data-ttu-id="976b1-106">Terme</span><span class="sxs-lookup"><span data-stu-id="976b1-106">Term</span></span>|<span data-ttu-id="976b1-107">Définition</span><span class="sxs-lookup"><span data-stu-id="976b1-107">Definition</span></span>|  
|---|---|  
|`event`|<span data-ttu-id="976b1-108">Nom de l’événement géré.</span><span class="sxs-lookup"><span data-stu-id="976b1-108">The name of the event being handled.</span></span>|  
|`eventhandler`|<span data-ttu-id="976b1-109">Nom de la procédure qui gère actuellement l’événement.</span><span class="sxs-lookup"><span data-stu-id="976b1-109">The name of the procedure currently handling the event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="976b1-110">Notes</span><span class="sxs-lookup"><span data-stu-id="976b1-110">Remarks</span></span>  
 <span data-ttu-id="976b1-111">Les `AddHandler` `RemoveHandler` instructions et vous permettent de démarrer et d’arrêter la gestion des événements pour un événement spécifique à tout moment pendant l’exécution du programme.</span><span class="sxs-lookup"><span data-stu-id="976b1-111">The `AddHandler` and `RemoveHandler` statements allow you to start and stop event handling for a specific event at any time during program execution.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="976b1-112">Pour les événements personnalisés, l' `RemoveHandler` instruction appelle l’accesseur de l’événement `RemoveHandler` .</span><span class="sxs-lookup"><span data-stu-id="976b1-112">For custom events, the `RemoveHandler` statement invokes the event's `RemoveHandler` accessor.</span></span> <span data-ttu-id="976b1-113">Pour plus d’informations sur les événements personnalisés, consultez [Event Statement](event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="976b1-113">For more information on custom events, see [Event Statement](event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="976b1-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="976b1-114">Example</span></span>  
 [!code-vb[VbVbalrEvents#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#17)]  
  
## <a name="see-also"></a><span data-ttu-id="976b1-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="976b1-115">See also</span></span>

- [<span data-ttu-id="976b1-116">AddHandler, instruction</span><span class="sxs-lookup"><span data-stu-id="976b1-116">AddHandler Statement</span></span>](addhandler-statement.md)
- [<span data-ttu-id="976b1-117">Poignées</span><span class="sxs-lookup"><span data-stu-id="976b1-117">Handles</span></span>](handles-clause.md)
- [<span data-ttu-id="976b1-118">Event, instruction</span><span class="sxs-lookup"><span data-stu-id="976b1-118">Event Statement</span></span>](event-statement.md)
- [<span data-ttu-id="976b1-119">Événements</span><span class="sxs-lookup"><span data-stu-id="976b1-119">Events</span></span>](../../programming-guide/language-features/events/index.md)
