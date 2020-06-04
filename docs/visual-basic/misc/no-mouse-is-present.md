---
title: Absence de souris
ms.date: 07/20/2015
f1_keywords:
- vbrMouse_NoMouseIsPresent
ms.assetid: 4472fd57-4217-4463-9d3c-dc4a8fe88f1b
ms.openlocfilehash: 748661cae35292968aae989789a96d1df855b6ce
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84376119"
---
# <a name="no-mouse-is-present"></a>Absence de souris
L’une des propriétés de l’objet `My.Computer.Mouse` a été appelée, mais aucune souris ou aucun port de souris n’est installé sur l’ordinateur.  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Ajoutez un bloc `Try...Catch` autour de l’appel à la propriété de l’objet `My.Computer.Mouse` .  
  
     — ou —  
  
- Installez une souris sur l’ordinateur.  
  
## <a name="see-also"></a>Voir aussi

- [My.Computer.Mouse](xref:Microsoft.VisualBasic.Devices.Mouse)
- [Gestion et levée d’exceptions dans .NET](../../standard/exceptions/index.md)
- [Try...Catch...Finally (instruction)](../language-reference/statements/try-catch-finally-statement.md)
