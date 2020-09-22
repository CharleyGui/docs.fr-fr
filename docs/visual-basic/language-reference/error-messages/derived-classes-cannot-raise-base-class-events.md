---
title: Les classes dérivées ne peuvent pas déclencher les événements de la classe de base
ms.date: 07/20/2015
f1_keywords:
- vbc30029
- bc30029
helpviewer_keywords:
- BC30029
ms.assetid: 63afa1c6-2f93-4512-a2f0-372455979771
ms.openlocfilehash: 0233a1584c5e871506b5c4762e98874c343f19b8
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874490"
---
# <a name="derived-classes-cannot-raise-base-class-events"></a><span data-ttu-id="3a0f2-102">Les classes dérivées ne peuvent pas déclencher les événements de la classe de base</span><span class="sxs-lookup"><span data-stu-id="3a0f2-102">Derived classes cannot raise base class events</span></span>

<span data-ttu-id="3a0f2-103">Un événement peut être déclenché uniquement à partir de l’espace de déclaration dans lequel il est déclaré.</span><span class="sxs-lookup"><span data-stu-id="3a0f2-103">An event can be raised only from the declaration space in which it is declared.</span></span> <span data-ttu-id="3a0f2-104">Par conséquent, une classe ne peut pas déclencher d’événements à partir d’une autre classe, même une classe à partir de laquelle elle est dérivée.</span><span class="sxs-lookup"><span data-stu-id="3a0f2-104">Therefore, a class cannot raise events from any other class, even one from which it is derived.</span></span>  
  
 <span data-ttu-id="3a0f2-105">**ID d’erreur :** BC30029</span><span class="sxs-lookup"><span data-stu-id="3a0f2-105">**Error ID:** BC30029</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="3a0f2-106">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="3a0f2-106">To correct this error</span></span>  
  
- <span data-ttu-id="3a0f2-107">Déplacez l' `Event` instruction ou l' `RaiseEvent` instruction de façon à ce qu’elles se trouvent dans la même classe.</span><span class="sxs-lookup"><span data-stu-id="3a0f2-107">Move the `Event` statement or the `RaiseEvent` statement so they are in the same class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a0f2-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3a0f2-108">See also</span></span>

- [<span data-ttu-id="3a0f2-109">Event, instruction</span><span class="sxs-lookup"><span data-stu-id="3a0f2-109">Event Statement</span></span>](../statements/event-statement.md)
- [<span data-ttu-id="3a0f2-110">RaiseEvent, instruction</span><span class="sxs-lookup"><span data-stu-id="3a0f2-110">RaiseEvent Statement</span></span>](../statements/raiseevent-statement.md)
