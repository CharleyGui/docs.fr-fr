---
title: L'événement '<eventname1>' ne peut pas implémenter l'événement '<eventname2>' pour l'interface '<interface>', car leurs types délégués '<delegate1>' et '<delegate2> ne correspondent pas
ms.date: 07/20/2015
f1_keywords:
- vbc31423
- bc31423
helpviewer_keywords:
- BC31423
ms.assetid: 2e754b66-5836-48ff-9697-b9c0d7085f18
ms.openlocfilehash: d6b85124b4408df532623f7c14a76e936ea28572
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64625538"
---
# <a name="event-eventname1-cannot-implement-event-eventname2-on-interface-interface-because-their-delegate-types-delegate1-and-delegate2-do-not-match"></a>Événement '\<nom_événement1 >' ne peut pas implémenter l’événement '\<nom_événement2 >' sur l’interface '\<interface >', car leurs types' délégués\<delegate1 >' et '\<delegate2 >' ne correspondent pas
Visual Basic ne peut pas implémenter un événement, car le type de délégué de l’événement ne correspond pas au type de délégué de l’événement dans l’interface. Cette erreur peut se produire quand vous définissez plusieurs événements dans une interface et essayez ensuite de les implémenter ensemble avec le même événement. Un événement peut implémenter deux événements ou plus seulement si tous les événements implémentés sont déclarés à l’aide de la syntaxe `As` et s’ils spécifient le même type délégué.  
  
 **ID d’erreur :** BC31423  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Implémentez les événements séparément.  
  
     - ou -  
  
- Définissez les événements dans l’interface à l’aide de la `As` syntaxe et spécifient le même type délégué.  
  
## <a name="see-also"></a>Voir aussi

- [Event (instruction)](../../../visual-basic/language-reference/statements/event-statement.md)
- [Delegate (instruction)](../../../visual-basic/language-reference/statements/delegate-statement.md)
- [Événements](../../../visual-basic/programming-guide/language-features/events/index.md)
