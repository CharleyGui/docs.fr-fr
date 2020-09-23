---
title: Absence de roulette de souris
ms.date: 07/20/2015
f1_keywords:
- vbrMouse_NoWheelIsPresent
ms.assetid: e924ffba-4af1-4247-9a6f-d19a03738f62
ms.openlocfilehash: a9b468d876945a177f3e326a7dc37e6c8a80285d
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91078838"
---
# <a name="no-mouse-wheel-is-present"></a><span data-ttu-id="47c79-102">Absence de roulette de souris</span><span class="sxs-lookup"><span data-stu-id="47c79-102">No mouse wheel is present</span></span>

<span data-ttu-id="47c79-103">La propriété `My.Computer.Mouse.WheelScrollLines` a été appelée, mais la souris ne possède pas de roulette de défilement.</span><span class="sxs-lookup"><span data-stu-id="47c79-103">The `My.Computer.Mouse.WheelScrollLines` property was called, but the mouse has no scroll wheel.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="47c79-104">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="47c79-104">To correct this error</span></span>  
  
- <span data-ttu-id="47c79-105">Vérifiez la propriété `My.Computer.Mouse.WheelExists` pour déterminer si la souris a une roulette de défilement avant d’appeler la propriété `My.Computer.Mouse.WheelScrollLines` .</span><span class="sxs-lookup"><span data-stu-id="47c79-105">Check the `My.Computer.Mouse.WheelExists` property to see if the mouse has a scroll wheel before calling the `My.Computer.Mouse.WheelScrollLines` property.</span></span>  
  
     <span data-ttu-id="47c79-106">- ou -</span><span class="sxs-lookup"><span data-stu-id="47c79-106">-or-</span></span>  
  
- <span data-ttu-id="47c79-107">Installez une souris dotée d’une roulette de défilement sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="47c79-107">Install a mouse with a scroll wheel on the computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47c79-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="47c79-108">See also</span></span>

- [<span data-ttu-id="47c79-109">My. Computer. Mouse. WheelScrollLines</span><span class="sxs-lookup"><span data-stu-id="47c79-109">My.Computer.Mouse.WheelScrollLines</span></span>](xref:Microsoft.VisualBasic.Devices.Mouse.WheelScrollLines)
- [<span data-ttu-id="47c79-110">My. Computer. Mouse. WheelExists</span><span class="sxs-lookup"><span data-stu-id="47c79-110">My.Computer.Mouse.WheelExists</span></span>](xref:Microsoft.VisualBasic.Devices.Mouse.WheelExists)
- [<span data-ttu-id="47c79-111">Gestion et levée d’exceptions dans .NET</span><span class="sxs-lookup"><span data-stu-id="47c79-111">Handling and throwing exceptions in .NET</span></span>](../../standard/exceptions/index.md)
