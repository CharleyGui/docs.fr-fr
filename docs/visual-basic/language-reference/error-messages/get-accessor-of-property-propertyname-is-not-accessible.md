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
# <a name="get-accessor-of-property-propertyname-is-not-accessible"></a><span data-ttu-id="c5277-102">L'accesseur 'Get' de la propriété '\<propertyname>' n'est pas accessible</span><span class="sxs-lookup"><span data-stu-id="c5277-102">'Get' accessor of property '\<propertyname>' is not accessible</span></span>
<span data-ttu-id="c5277-103">Une instruction tente de récupérer la valeur d’une propriété lorsqu’elle n’a pas accès à la procédure de la propriété `Get` .</span><span class="sxs-lookup"><span data-stu-id="c5277-103">A statement attempts to retrieve the value of a property when it does not have access to the property's `Get` procedure.</span></span>  
  
 <span data-ttu-id="c5277-104">Si l' [instruction d’extraction](../statements/get-statement.md) est marquée avec un niveau d’accès plus restrictif que son [instruction Property](../statements/property-statement.md), une tentative de lecture de la valeur de la propriété peut échouer dans les cas suivants :</span><span class="sxs-lookup"><span data-stu-id="c5277-104">If the [Get Statement](../statements/get-statement.md) is marked with a more restrictive access level than its [Property Statement](../statements/property-statement.md), an attempt to read the property value could fail in the following cases:</span></span>  
  
- <span data-ttu-id="c5277-105">L' `Get` instruction est marquée comme [privée](../modifiers/private.md) et le code appelant est en dehors de la classe ou de la structure dans laquelle la propriété est définie.</span><span class="sxs-lookup"><span data-stu-id="c5277-105">The `Get` statement is marked [Private](../modifiers/private.md) and the calling code is outside the class or structure in which the property is defined.</span></span>  
  
- <span data-ttu-id="c5277-106">L' `Get` instruction est marquée comme [protégée](../modifiers/protected.md) et le code appelant n’est pas dans la classe ou la structure dans laquelle la propriété est définie, ni dans une classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="c5277-106">The `Get` statement is marked [Protected](../modifiers/protected.md) and the calling code is not in the class or structure in which the property is defined, nor in a derived class.</span></span>  
  
- <span data-ttu-id="c5277-107">L' `Get` instruction est marquée [Friend](../modifiers/friend.md) et le code appelant n’est pas dans le même assembly que celui dans lequel la propriété est définie.</span><span class="sxs-lookup"><span data-stu-id="c5277-107">The `Get` statement is marked [Friend](../modifiers/friend.md) and the calling code is not in the same assembly in which the property is defined.</span></span>  
  
 <span data-ttu-id="c5277-108">**ID d’erreur :** BC31103</span><span class="sxs-lookup"><span data-stu-id="c5277-108">**Error ID:** BC31103</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c5277-109">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="c5277-109">To correct this error</span></span>  
  
- <span data-ttu-id="c5277-110">Si vous avez le contrôle du code source définissant la propriété, pensez à déclarer la `Get` procédure avec le même niveau d’accès que la propriété elle-même.</span><span class="sxs-lookup"><span data-stu-id="c5277-110">If you have control of the source code defining the property, consider declaring the `Get` procedure with the same access level as the property itself.</span></span>  
  
- <span data-ttu-id="c5277-111">Si vous n’avez pas le contrôle du code source qui définit la propriété, ou si vous devez limiter le niveau d’accès de la procédure à la `Get` propriété elle-même, essayez de déplacer l’instruction qui lit la valeur de la propriété dans une région de code qui a un meilleur accès à la propriété.</span><span class="sxs-lookup"><span data-stu-id="c5277-111">If you do not have control of the source code defining the property, or you must restrict the `Get` procedure access level more than the property itself, try to move the statement that reads the property value to a region of code that has better access to the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5277-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c5277-112">See also</span></span>

- [<span data-ttu-id="c5277-113">Procédures Property</span><span class="sxs-lookup"><span data-stu-id="c5277-113">Property Procedures</span></span>](../../programming-guide/language-features/procedures/property-procedures.md)
- [<span data-ttu-id="c5277-114">Comment : déclarer une propriété avec des niveaux d'accès mixtes</span><span class="sxs-lookup"><span data-stu-id="c5277-114">How to: Declare a Property with Mixed Access Levels</span></span>](../../programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)
