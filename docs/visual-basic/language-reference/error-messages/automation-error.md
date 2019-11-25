---
title: Erreur Automation
ms.date: 07/20/2015
f1_keywords:
- vbrID440
ms.assetid: 2c4be5c5-2f0d-4a2b-96fe-d1b24f08fc4c
ms.openlocfilehash: df153167bc8c73a2d3760c8d7db30dccfa468e35
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976145"
---
# <a name="automation-error"></a>Erreur Automation

Une erreur s'est produite pendant l'exécution d'une méthode ou l'obtention / la définition d'une propriété de variable objet. L'application qui a créé l'objet a signalé l'erreur.  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1. Vérifiez les propriétés de l'objet `Err` pour déterminer la source et la nature de l'erreur.  
  
2. Utilisez l’instruction `On Error Resume Next` immédiatement avant l’instruction d’accès, puis recherchez les erreurs immédiatement après l’accès à l’instruction.  
  
## <a name="see-also"></a>Voir aussi

- [Types d’erreurs](../../../visual-basic/programming-guide/language-features/error-types.md)
- [Nous contacter](/visualstudio/ide/feedback-options)
