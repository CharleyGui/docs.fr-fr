---
title: L'accesseur 'Set' de la propriété '<propertyname>' n'est pas accessible
ms.date: 07/20/2015
f1_keywords:
- vbc31102
- bc31102
helpviewer_keywords:
- BC31102
ms.assetid: 6f7b31b7-3656-4ae1-8851-90f5f4c6950a
ms.openlocfilehash: 3cf828eb5f11090a74a65388e2b89a191046a456
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162243"
---
# <a name="bc31102-set-accessor-of-property-propertyname-is-not-accessible"></a>BC31102 : l’accesseur’Set’de la propriété' \<propertyname> 'n’est pas accessible

Une instruction tente de stocker la valeur d’une propriété lorsqu’elle n’a pas accès à la procédure de la propriété `Set` .

 Si l' [instruction Set](../statements/set-statement.md) est marquée avec un niveau d’accès plus restrictif que son [instruction Property](../statements/property-statement.md), une tentative de définition de la valeur de la propriété peut échouer dans les cas suivants :

- L' `Set` instruction est marquée comme [privée](../modifiers/private.md) et le code appelant est en dehors de la classe ou de la structure dans laquelle la propriété est définie.

- L' `Set` instruction est marquée comme [protégée](../modifiers/protected.md) et le code appelant n’est pas dans la classe ou la structure dans laquelle la propriété est définie, ni dans une classe dérivée.

- L' `Set` instruction est marquée [Friend](../modifiers/friend.md) et le code appelant n’est pas dans le même assembly que celui dans lequel la propriété est définie.

 **ID d’erreur :** BC31102

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Si vous avez le contrôle du code source définissant la propriété, pensez à déclarer la `Set` procédure avec le même niveau d’accès que la propriété elle-même.

- Si vous n’avez pas le contrôle du code source qui définit la propriété, ou si vous devez limiter le `Set` niveau d’accès à la procédure plus que la propriété elle-même, essayez de déplacer l’instruction qui définit la valeur de la propriété sur une région de code qui a un meilleur accès à la propriété.

## <a name="see-also"></a>Voir aussi

- [Procédures Property](../../programming-guide/language-features/procedures/property-procedures.md)
- [Comment : déclarer une propriété avec des niveaux d'accès mixtes](../../programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)
