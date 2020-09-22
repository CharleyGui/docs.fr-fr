---
title: L'accesseur 'Set' de la propriété '<propertyname>' n'est pas accessible
ms.date: 07/20/2015
f1_keywords:
- vbc31102
- bc31102
helpviewer_keywords:
- BC31102
ms.assetid: 6f7b31b7-3656-4ae1-8851-90f5f4c6950a
ms.openlocfilehash: a18a851d4db0ab17cd9b8ffaed4317a9fcf5292b
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90870773"
---
# <a name="set-accessor-of-property-propertyname-is-not-accessible"></a><span data-ttu-id="bd954-102">L'accesseur 'Set' de la propriété '\<propertyname>' n'est pas accessible</span><span class="sxs-lookup"><span data-stu-id="bd954-102">'Set' accessor of property '\<propertyname>' is not accessible</span></span>

<span data-ttu-id="bd954-103">Une instruction tente de stocker la valeur d’une propriété lorsqu’elle n’a pas accès à la procédure de la propriété `Set` .</span><span class="sxs-lookup"><span data-stu-id="bd954-103">A statement attempts to store the value of a property when it does not have access to the property's `Set` procedure.</span></span>  
  
 <span data-ttu-id="bd954-104">Si l' [instruction Set](../statements/set-statement.md) est marquée avec un niveau d’accès plus restrictif que son [instruction Property](../statements/property-statement.md), une tentative de définition de la valeur de la propriété peut échouer dans les cas suivants :</span><span class="sxs-lookup"><span data-stu-id="bd954-104">If the [Set Statement](../statements/set-statement.md) is marked with a more restrictive access level than its [Property Statement](../statements/property-statement.md), an attempt to set the property value could fail in the following cases:</span></span>  
  
- <span data-ttu-id="bd954-105">L' `Set` instruction est marquée comme [privée](../modifiers/private.md) et le code appelant est en dehors de la classe ou de la structure dans laquelle la propriété est définie.</span><span class="sxs-lookup"><span data-stu-id="bd954-105">The `Set` statement is marked [Private](../modifiers/private.md) and the calling code is outside the class or structure in which the property is defined.</span></span>  
  
- <span data-ttu-id="bd954-106">L' `Set` instruction est marquée comme [protégée](../modifiers/protected.md) et le code appelant n’est pas dans la classe ou la structure dans laquelle la propriété est définie, ni dans une classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="bd954-106">The `Set` statement is marked [Protected](../modifiers/protected.md) and the calling code is not in the class or structure in which the property is defined, nor in a derived class.</span></span>  
  
- <span data-ttu-id="bd954-107">L' `Set` instruction est marquée [Friend](../modifiers/friend.md) et le code appelant n’est pas dans le même assembly que celui dans lequel la propriété est définie.</span><span class="sxs-lookup"><span data-stu-id="bd954-107">The `Set` statement is marked [Friend](../modifiers/friend.md) and the calling code is not in the same assembly in which the property is defined.</span></span>  
  
 <span data-ttu-id="bd954-108">**ID d’erreur :** BC31102</span><span class="sxs-lookup"><span data-stu-id="bd954-108">**Error ID:** BC31102</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="bd954-109">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="bd954-109">To correct this error</span></span>  
  
- <span data-ttu-id="bd954-110">Si vous avez le contrôle du code source définissant la propriété, pensez à déclarer la `Set` procédure avec le même niveau d’accès que la propriété elle-même.</span><span class="sxs-lookup"><span data-stu-id="bd954-110">If you have control of the source code defining the property, consider declaring the `Set` procedure with the same access level as the property itself.</span></span>  
  
- <span data-ttu-id="bd954-111">Si vous n’avez pas le contrôle du code source qui définit la propriété, ou si vous devez limiter le `Set` niveau d’accès à la procédure plus que la propriété elle-même, essayez de déplacer l’instruction qui définit la valeur de la propriété sur une région de code qui a un meilleur accès à la propriété.</span><span class="sxs-lookup"><span data-stu-id="bd954-111">If you do not have control of the source code defining the property, or you must restrict the `Set` procedure access level more than the property itself, try to move the statement that sets the property value to a region of code that has better access to the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd954-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bd954-112">See also</span></span>

- [<span data-ttu-id="bd954-113">Procédures Property</span><span class="sxs-lookup"><span data-stu-id="bd954-113">Property Procedures</span></span>](../../programming-guide/language-features/procedures/property-procedures.md)
- [<span data-ttu-id="bd954-114">Comment : déclarer une propriété avec des niveaux d'accès mixtes</span><span class="sxs-lookup"><span data-stu-id="bd954-114">How to: Declare a Property with Mixed Access Levels</span></span>](../../programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)
