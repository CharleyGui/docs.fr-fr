---
title: "'<typename>' ne peut pas hériter de <type> '<basetypename>' car il étend l'accès du <type> de base en dehors de l'assembly"
ms.date: 07/20/2015
f1_keywords:
- vbc30910
- bc30910
helpviewer_keywords:
- BC30910
ms.assetid: 68fc05c5-5d55-4742-9a3b-ea04312594f4
ms.openlocfilehash: aa04c558abbcc4259c2821cdcbdc1669b91ffee0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402770"
---
# <a name="typename-cannot-inherit-from-type-basetypename-because-it-expands-the-access-of-the-base-type-outside-the-assembly"></a>'\<typename>' ne peut pas hériter de \<type> '\<basetypename>' car il étend l'accès du \<type> de base en dehors de l'assembly
Une classe ou une interface hérite d’une classe de base ou d’une interface, mais a un niveau d’accès moins restrictif.  
  
 Par exemple, une `Public` interface hérite d’une `Friend` interface ou une `Protected` classe hérite d’une `Private` classe. Cela expose l’interface ou la classe de base à l’accès au-delà du niveau prévu.  
  
 **ID d’erreur :** BC30910  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Modifiez le niveau d’accès de la classe ou de l’interface dérivée pour qu’il soit au moins aussi restrictif que celui de la classe ou de l’interface de base.  
  
     -ou-  
  
- Si vous avez besoin d’un niveau d’accès moins restrictif, supprimez l' `Inherits` instruction. Vous ne pouvez pas hériter d’une classe ou d’une interface de base plus restreinte.  
  
## <a name="see-also"></a>Voir aussi

- [Class (instruction)](../statements/class-statement.md)
- [Interface (instruction)](../statements/interface-statement.md)
- [Inherits Statement](../statements/inherits-statement.md)
- [Niveaux d’accès dans Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md)
