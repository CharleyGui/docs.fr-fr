---
title: L'accesseur 'Get' de la propriété '<propertyname>' n'est pas accessible
ms.date: 07/20/2015
f1_keywords:
- vbc31103
- bc31103
helpviewer_keywords:
- BC31103
ms.assetid: 3c346c32-7669-4b04-841d-7a9df9cb703e
ms.openlocfilehash: cb953671e624d5b9170aa0b3a9dd80c7ba8337e3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402912"
---
# <a name="get-accessor-of-property-propertyname-is-not-accessible"></a>L'accesseur 'Get' de la propriété '\<propertyname>' n'est pas accessible
Une instruction tente de récupérer la valeur d’une propriété lorsqu’elle n’a pas accès à la procédure de la propriété `Get` .  
  
 Si l' [instruction d’extraction](../statements/get-statement.md) est marquée avec un niveau d’accès plus restrictif que son [instruction Property](../statements/property-statement.md), une tentative de lecture de la valeur de la propriété peut échouer dans les cas suivants :  
  
- L' `Get` instruction est marquée comme [privée](../modifiers/private.md) et le code appelant est en dehors de la classe ou de la structure dans laquelle la propriété est définie.  
  
- L' `Get` instruction est marquée comme [protégée](../modifiers/protected.md) et le code appelant n’est pas dans la classe ou la structure dans laquelle la propriété est définie, ni dans une classe dérivée.  
  
- L' `Get` instruction est marquée [Friend](../modifiers/friend.md) et le code appelant n’est pas dans le même assembly que celui dans lequel la propriété est définie.  
  
 **ID d’erreur :** BC31103  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Si vous avez le contrôle du code source définissant la propriété, pensez à déclarer la `Get` procédure avec le même niveau d’accès que la propriété elle-même.  
  
- Si vous n’avez pas le contrôle du code source qui définit la propriété, ou si vous devez limiter le niveau d’accès de la procédure à la `Get` propriété elle-même, essayez de déplacer l’instruction qui lit la valeur de la propriété dans une région de code qui a un meilleur accès à la propriété.  
  
## <a name="see-also"></a>Voir aussi

- [Procédures Property](../../programming-guide/language-features/procedures/property-procedures.md)
- [Comment : déclarer une propriété avec des niveaux d'accès mixtes](../../programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)
