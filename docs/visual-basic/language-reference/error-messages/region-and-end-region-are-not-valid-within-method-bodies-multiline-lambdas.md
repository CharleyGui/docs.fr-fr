---
title: Les instructions « #Region » et « #End Region » ne sont pas valides dans le corps des méthodes ou les expressions lambda multiligne
ms.date: 07/20/2015
f1_keywords:
- bc32025
- vbc32025
helpviewer_keywords:
- BC32025
ms.assetid: 43707bf1-1c6b-4d82-b081-e5a17dca51c1
ms.openlocfilehash: 5652139ab139ea93258eb116f97ba21b76986a24
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400381"
---
# <a name="region-and-end-region-statements-are-not-valid-within-method-bodiesmultiline-lambdas"></a>Les instructions '#Region' et '#End Region' ne sont pas valides dans le corps des méthodes ou les expressions lambda multiligne
Le `#Region` bloc doit être déclaré au niveau d’un classe, d’un module ou d’un espace de noms. Une région réductible peut inclure une ou plusieurs procédures, mais elle ne peut pas commencer ni se terminer à l’intérieur d’une procédure.  
  
 **ID d’erreur :** BC32025  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1. Vérifiez que la procédure précédente est correctement terminée par une `End Function` instruction ou `End Sub` .  
  
2. Vérifiez que les `#Region` `#End Region` directives et se trouvent dans le même bloc de code.  
  
## <a name="see-also"></a>Voir aussi

- [#Region directive](../directives/region-directive.md)
