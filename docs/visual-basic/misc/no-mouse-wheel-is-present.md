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
# <a name="no-mouse-wheel-is-present"></a>Absence de roulette de souris

La propriété `My.Computer.Mouse.WheelScrollLines` a été appelée, mais la souris ne possède pas de roulette de défilement.  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Vérifiez la propriété `My.Computer.Mouse.WheelExists` pour déterminer si la souris a une roulette de défilement avant d’appeler la propriété `My.Computer.Mouse.WheelScrollLines` .  
  
     - ou -  
  
- Installez une souris dotée d’une roulette de défilement sur l’ordinateur.  
  
## <a name="see-also"></a>Voir aussi

- [My. Computer. Mouse. WheelScrollLines](xref:Microsoft.VisualBasic.Devices.Mouse.WheelScrollLines)
- [My. Computer. Mouse. WheelExists](xref:Microsoft.VisualBasic.Devices.Mouse.WheelExists)
- [Gestion et levée d’exceptions dans .NET](../../standard/exceptions/index.md)
