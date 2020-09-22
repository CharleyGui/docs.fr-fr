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
# <a name="event-eventname1-cannot-implement-event-eventname2-on-interface-interface-because-their-delegate-types-delegate1-and-delegate2-do-not-match"></a>L'événement '\<eventname1>' ne peut pas implémenter l'événement '\<eventname2>' pour l'interface '\<interface>', car leurs types délégués '\<delegate1>' et '\<delegate2> ne correspondent pas

Visual Basic ne peut pas implémenter un événement, car le type délégué de l’événement ne correspond pas au type délégué de l’événement dans l’interface. Cette erreur peut se produire quand vous définissez plusieurs événements dans une interface et essayez ensuite de les implémenter ensemble avec le même événement. Un événement peut implémenter deux événements ou plus seulement si tous les événements implémentés sont déclarés à l’aide de la syntaxe `As` et s’ils spécifient le même type délégué.  
  
 **ID d’erreur :** BC31423  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Implémentez les événements séparément.  
  
     Ou  
  
- Définissez les événements dans l’interface à l’aide de la `As` syntaxe et spécifiez le même type délégué.  
  
## <a name="see-also"></a>Voir aussi

- [Event, instruction](../statements/event-statement.md)
- [Delegate, instruction](../statements/delegate-statement.md)
- [Événements](../../programming-guide/language-features/events/index.md)
