---
title: Les classes dérivées ne peuvent pas déclencher les événements de la classe de base
ms.date: 07/20/2015
f1_keywords:
- vbc30029
- bc30029
helpviewer_keywords:
- BC30029
ms.assetid: 63afa1c6-2f93-4512-a2f0-372455979771
ms.openlocfilehash: 7b86420466d77a6aa45b1201a9375b4433e4b5ec
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163439"
---
# <a name="bc30029-derived-classes-cannot-raise-base-class-events"></a><span data-ttu-id="3d5c8-102">BC30029 : les classes dérivées ne peuvent pas déclencher d’événements de classe de base</span><span class="sxs-lookup"><span data-stu-id="3d5c8-102">BC30029: Derived classes cannot raise base class events</span></span>

<span data-ttu-id="3d5c8-103">Un événement peut être déclenché uniquement à partir de l’espace de déclaration dans lequel il est déclaré.</span><span class="sxs-lookup"><span data-stu-id="3d5c8-103">An event can be raised only from the declaration space in which it is declared.</span></span> <span data-ttu-id="3d5c8-104">Par conséquent, une classe ne peut pas déclencher d’événements à partir d’une autre classe, même une classe à partir de laquelle elle est dérivée.</span><span class="sxs-lookup"><span data-stu-id="3d5c8-104">Therefore, a class cannot raise events from any other class, even one from which it is derived.</span></span>

 <span data-ttu-id="3d5c8-105">**ID d’erreur :** BC30029</span><span class="sxs-lookup"><span data-stu-id="3d5c8-105">**Error ID:** BC30029</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="3d5c8-106">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="3d5c8-106">To correct this error</span></span>

- <span data-ttu-id="3d5c8-107">Déplacez l' `Event` instruction ou l' `RaiseEvent` instruction de façon à ce qu’elles se trouvent dans la même classe.</span><span class="sxs-lookup"><span data-stu-id="3d5c8-107">Move the `Event` statement or the `RaiseEvent` statement so they are in the same class.</span></span>

## <a name="see-also"></a><span data-ttu-id="3d5c8-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3d5c8-108">See also</span></span>

- [<span data-ttu-id="3d5c8-109">Event, instruction</span><span class="sxs-lookup"><span data-stu-id="3d5c8-109">Event Statement</span></span>](../statements/event-statement.md)
- [<span data-ttu-id="3d5c8-110">RaiseEvent, instruction</span><span class="sxs-lookup"><span data-stu-id="3d5c8-110">RaiseEvent Statement</span></span>](../statements/raiseevent-statement.md)
