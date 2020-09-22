---
title: L'événement '<eventname1>' ne peut pas implémenter l'événement '<eventname2>' pour l'interface '<interface>', car leurs types délégués '<delegate1>' et '<delegate2> ne correspondent pas
ms.date: 07/20/2015
f1_keywords:
- vbc31423
- bc31423
helpviewer_keywords:
- BC31423
ms.assetid: 2e754b66-5836-48ff-9697-b9c0d7085f18
ms.openlocfilehash: b1e0728a4f865b432b142df4ded1efddb376201e
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874324"
---
# <a name="event-eventname1-cannot-implement-event-eventname2-on-interface-interface-because-their-delegate-types-delegate1-and-delegate2-do-not-match"></a><span data-ttu-id="35277-102">L'événement '\<eventname1>' ne peut pas implémenter l'événement '\<eventname2>' pour l'interface '\<interface>', car leurs types délégués '\<delegate1>' et '\<delegate2> ne correspondent pas</span><span class="sxs-lookup"><span data-stu-id="35277-102">Event '\<eventname1>' cannot implement event '\<eventname2>' on interface '\<interface>' because their delegate types '\<delegate1>' and '\<delegate2>' do not match</span></span>

<span data-ttu-id="35277-103">Visual Basic ne peut pas implémenter un événement, car le type délégué de l’événement ne correspond pas au type délégué de l’événement dans l’interface.</span><span class="sxs-lookup"><span data-stu-id="35277-103">Visual Basic cannot implement an event because the delegate type of the event does not match the delegate type of the event in the interface.</span></span> <span data-ttu-id="35277-104">Cette erreur peut se produire quand vous définissez plusieurs événements dans une interface et essayez ensuite de les implémenter ensemble avec le même événement.</span><span class="sxs-lookup"><span data-stu-id="35277-104">This error can occur when you define multiple events in an interface and then attempt to implement them together with the same event.</span></span> <span data-ttu-id="35277-105">Un événement peut implémenter deux événements ou plus seulement si tous les événements implémentés sont déclarés à l’aide de la syntaxe `As` et s’ils spécifient le même type délégué.</span><span class="sxs-lookup"><span data-stu-id="35277-105">An event can implement two or more events only if all implemented events are declared using the `As` syntax and specify the same delegate type.</span></span>  
  
 <span data-ttu-id="35277-106">**ID d’erreur :** BC31423</span><span class="sxs-lookup"><span data-stu-id="35277-106">**Error ID:** BC31423</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="35277-107">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="35277-107">To correct this error</span></span>  
  
- <span data-ttu-id="35277-108">Implémentez les événements séparément.</span><span class="sxs-lookup"><span data-stu-id="35277-108">Implement the events separately.</span></span>  
  
     <span data-ttu-id="35277-109">Ou</span><span class="sxs-lookup"><span data-stu-id="35277-109">—or—</span></span>  
  
- <span data-ttu-id="35277-110">Définissez les événements dans l’interface à l’aide de la `As` syntaxe et spécifiez le même type délégué.</span><span class="sxs-lookup"><span data-stu-id="35277-110">Define the events in the interface using the `As` syntax and specify the same delegate type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35277-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="35277-111">See also</span></span>

- [<span data-ttu-id="35277-112">Event, instruction</span><span class="sxs-lookup"><span data-stu-id="35277-112">Event Statement</span></span>](../statements/event-statement.md)
- [<span data-ttu-id="35277-113">Delegate, instruction</span><span class="sxs-lookup"><span data-stu-id="35277-113">Delegate Statement</span></span>](../statements/delegate-statement.md)
- [<span data-ttu-id="35277-114">Événements</span><span class="sxs-lookup"><span data-stu-id="35277-114">Events</span></span>](../../programming-guide/language-features/events/index.md)
