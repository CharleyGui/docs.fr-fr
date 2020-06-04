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
# <a name="derived-classes-cannot-raise-base-class-events"></a>Les classes dérivées ne peuvent pas déclencher les événements de la classe de base
Un événement peut être déclenché uniquement à partir de l’espace de déclaration dans lequel il est déclaré. Par conséquent, une classe ne peut pas déclencher d’événements à partir d’une autre classe, même une classe à partir de laquelle elle est dérivée.  
  
 **ID d’erreur :** BC30029  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Déplacez l' `Event` instruction ou l' `RaiseEvent` instruction de façon à ce qu’elles se trouvent dans la même classe.  
  
## <a name="see-also"></a>Voir aussi

- [Event, instruction](../statements/event-statement.md)
- [RaiseEvent, instruction](../statements/raiseevent-statement.md)
