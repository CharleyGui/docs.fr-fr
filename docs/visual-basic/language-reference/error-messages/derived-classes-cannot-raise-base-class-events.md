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
# <a name="derived-classes-cannot-raise-base-class-events"></a>Les classes dérivées ne peuvent pas déclencher les événements de la classe de base

Un événement peut être déclenché uniquement à partir de l’espace de déclaration dans lequel il est déclaré. Par conséquent, une classe ne peut pas déclencher d’événements à partir d’une autre classe, même une classe à partir de laquelle elle est dérivée.  
  
 **ID d’erreur :** BC30029  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Déplacez l' `Event` instruction ou l' `RaiseEvent` instruction de façon à ce qu’elles se trouvent dans la même classe.  
  
## <a name="see-also"></a>Voir aussi

- [Event, instruction](../statements/event-statement.md)
- [RaiseEvent, instruction](../statements/raiseevent-statement.md)
