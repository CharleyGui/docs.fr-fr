---
title: Erreur Automation
ms.date: 07/20/2015
f1_keywords:
- vbrID440
ms.assetid: 2c4be5c5-2f0d-4a2b-96fe-d1b24f08fc4c
ms.openlocfilehash: d62ba57db8bffefb2cfebed705251d87fe285602
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409892"
---
# <a name="automation-error"></a>Erreur Automation

Une erreur s'est produite pendant l'exécution d'une méthode ou l'obtention / la définition d'une propriété de variable objet. L'application qui a créé l'objet a signalé l'erreur.  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1. Vérifiez les propriétés de l'objet `Err` pour déterminer la source et la nature de l'erreur.  
  
2. Utilisez l' `On Error Resume Next` instruction juste avant l’instruction d’accès, puis recherchez les erreurs immédiatement après l’accès à l’instruction.  
  
## <a name="see-also"></a>Voir aussi

- [Types d’erreurs](../../programming-guide/language-features/error-types.md)
- [Nous contacter](/visualstudio/ide/feedback-options)
