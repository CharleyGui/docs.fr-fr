---
title: "'<typename>' ne peut pas hériter de <type> '<basetypename>' car il étend l'accès du <type> de base en dehors de l'assembly"
ms.date: 07/20/2015
f1_keywords:
- vbc30910
- bc30910
helpviewer_keywords:
- BC30910
ms.assetid: 68fc05c5-5d55-4742-9a3b-ea04312594f4
ms.openlocfilehash: 5c019f9d74b11e48aa05a1480b9449fa28488b43
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161840"
---
# <a name="bc30910-typename-cannot-inherit-from-type-basetypename-because-it-expands-the-access-of-the-base-type-outside-the-assembly"></a>BC30910 : ' \<typename> 'ne peut pas hériter de \<type> ' \<basetypename> ', car il étend l’accès de la base \<type> en dehors de l’assembly

Une classe ou une interface hérite d’une classe de base ou d’une interface, mais a un niveau d’accès moins restrictif.

 Par exemple, une `Public` interface hérite d’une `Friend` interface ou une `Protected` classe hérite d’une `Private` classe. Cela expose l’interface ou la classe de base à l’accès au-delà du niveau prévu.

 **ID d’erreur :** BC30910

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Modifiez le niveau d’accès de la classe ou de l’interface dérivée pour qu’il soit au moins aussi restrictif que celui de la classe ou de l’interface de base.

     - ou -

- Si vous avez besoin d’un niveau d’accès moins restrictif, supprimez l' `Inherits` instruction. Vous ne pouvez pas hériter d’une classe ou d’une interface de base plus restreinte.

## <a name="see-also"></a>Voir aussi

- [Class (instruction)](../statements/class-statement.md)
- [Interface (instruction)](../statements/interface-statement.md)
- [Inherits Statement](../statements/inherits-statement.md)
- [Niveaux d’accès dans Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md)
