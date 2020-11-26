---
title: System.ServiceModel.ManualFlowThrottleLimitReached
ms.date: 03/30/2017
ms.assetid: 9aba851f-1830-493b-8e3e-60f454eb923e
ms.openlocfilehash: 180a06efc94acba40806e1f5d661553127549596
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96248485"
---
# <a name="systemservicemodelmanualflowthrottlelimitreached"></a>System.ServiceModel.ManualFlowThrottleLimitReached

System.ServiceModel.ManualFlowThrottleLimitReached  
  
## <a name="description"></a>Description  

 Le système a atteint la limite définie pour l'accélérateur ManualFlowControlLimit. La valeur d'accélérateur peut être modifiée via la propriété ManualFlowControlLimit sur ServiceHost ou InstanceContext, le cas échéant.  
  
 Cette trace est émise lorsque la limite de contrôle de flux manuelle est initialement réduite à 0. Les modifications ultérieures apportées à 0 ne sont pas suivies. La limite de contrôle de flux sur le contexte d'instance est suivie une fois pour chaque contexte.  
  
## <a name="see-also"></a>Voir aussi

- [Suivi](index.md)
- [Utilisation du suivi pour résoudre les problèmes posés par votre application](using-tracing-to-troubleshoot-your-application.md)
- [Administration et diagnostics](../index.md)
