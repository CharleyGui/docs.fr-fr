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
# <a name="bc30029-derived-classes-cannot-raise-base-class-events"></a>BC30029 : les classes dérivées ne peuvent pas déclencher d’événements de classe de base

Un événement peut être déclenché uniquement à partir de l’espace de déclaration dans lequel il est déclaré. Par conséquent, une classe ne peut pas déclencher d’événements à partir d’une autre classe, même une classe à partir de laquelle elle est dérivée.

 **ID d’erreur :** BC30029

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Déplacez l' `Event` instruction ou l' `RaiseEvent` instruction de façon à ce qu’elles se trouvent dans la même classe.

## <a name="see-also"></a>Voir aussi

- [Event, instruction](../statements/event-statement.md)
- [RaiseEvent, instruction](../statements/raiseevent-statement.md)
