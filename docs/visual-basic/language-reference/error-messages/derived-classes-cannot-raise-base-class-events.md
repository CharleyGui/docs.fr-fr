---
title: Les classes dérivées ne peuvent pas déclencher les événements de la classe de base
ms.date: 07/20/2015
f1_keywords:
- vbc30029
- bc30029
helpviewer_keywords:
- BC30029
ms.assetid: 63afa1c6-2f93-4512-a2f0-372455979771
ms.openlocfilehash: c59212a28ba27123a7db9163ff7437c159a3d310
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409697"
---
# <a name="derived-classes-cannot-raise-base-class-events"></a><span data-ttu-id="d3a89-102">Les classes dérivées ne peuvent pas déclencher les événements de la classe de base</span><span class="sxs-lookup"><span data-stu-id="d3a89-102">Derived classes cannot raise base class events</span></span>
<span data-ttu-id="d3a89-103">Un événement peut être déclenché uniquement à partir de l’espace de déclaration dans lequel il est déclaré.</span><span class="sxs-lookup"><span data-stu-id="d3a89-103">An event can be raised only from the declaration space in which it is declared.</span></span> <span data-ttu-id="d3a89-104">Par conséquent, une classe ne peut pas déclencher d’événements à partir d’une autre classe, même une classe à partir de laquelle elle est dérivée.</span><span class="sxs-lookup"><span data-stu-id="d3a89-104">Therefore, a class cannot raise events from any other class, even one from which it is derived.</span></span>  
  
 <span data-ttu-id="d3a89-105">**ID d’erreur :** BC30029</span><span class="sxs-lookup"><span data-stu-id="d3a89-105">**Error ID:** BC30029</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d3a89-106">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="d3a89-106">To correct this error</span></span>  
  
- <span data-ttu-id="d3a89-107">Déplacez l' `Event` instruction ou l' `RaiseEvent` instruction de façon à ce qu’elles se trouvent dans la même classe.</span><span class="sxs-lookup"><span data-stu-id="d3a89-107">Move the `Event` statement or the `RaiseEvent` statement so they are in the same class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3a89-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d3a89-108">See also</span></span>

- [<span data-ttu-id="d3a89-109">Event, instruction</span><span class="sxs-lookup"><span data-stu-id="d3a89-109">Event Statement</span></span>](../statements/event-statement.md)
- [<span data-ttu-id="d3a89-110">RaiseEvent, instruction</span><span class="sxs-lookup"><span data-stu-id="d3a89-110">RaiseEvent Statement</span></span>](../statements/raiseevent-statement.md)
