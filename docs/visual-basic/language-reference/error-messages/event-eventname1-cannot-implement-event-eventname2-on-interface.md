---
title: L'événement '<eventname1>' ne peut pas implémenter l'événement '<eventname2>' pour l'interface '<interface>', car leurs types délégués '<delegate1>' et '<delegate2> ne correspondent pas
ms.date: 07/20/2015
f1_keywords:
- vbc31423
- bc31423
helpviewer_keywords:
- BC31423
ms.assetid: 2e754b66-5836-48ff-9697-b9c0d7085f18
ms.openlocfilehash: d0b2b095ed355b420b28e87ed0b9d6a31f049ebf
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162022"
---
# <a name="bc31423-event-eventname1-cannot-implement-event-eventname2-on-interface-interface-because-their-delegate-types-delegate1-and-delegate2-do-not-match"></a>BC31423 : l’événement' \<eventname1> 'ne peut pas implémenter l’événement' \<eventname2> 'sur l’interface' \<interface> ', car leurs types délégués' \<delegate1> 'et' \<delegate2> 'ne correspondent pas

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
