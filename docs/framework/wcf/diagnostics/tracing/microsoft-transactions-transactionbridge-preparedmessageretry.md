---
title: Microsoft.Transactions.TransactionBridge.PreparedMessageRetry
ms.date: 03/30/2017
ms.assetid: 2194292d-bf5f-4aef-9336-cd3c4795cb71
ms.openlocfilehash: edab153123ae48702811532df3b5b5bf0849c26a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275916"
---
# <a name="microsofttransactionstransactionbridgepreparedmessageretry"></a>Microsoft.Transactions.TransactionBridge.PreparedMessageRetry

Une nouvelle tentative de message Prepared a été envoyée à un coordinateur qui ne répond pas.  
  
## <a name="description"></a>Description  

 Suivi lorsque le gestionnaire de transactions local a dû renvoyer un message Prepared à un coordinateur supérieur parce qu'il n'a pas reçu de réponse dans un délai donné.  
  
## <a name="troubleshooting"></a>Dépannage  

 Recherchez d'éventuels problèmes liés au réseau ou au produit pouvant empêcher la réponse d'être remise à temps.  Si un nombre élevé de ces messages apparaissent, cela peut indiquer des problèmes d'infrastructure ou des délais de réponse anormalement longs. Ces deux problèmes réduiront considérablement le débit des transactions au sein du système.  
  
## <a name="see-also"></a>Voir aussi

- [Suivi](index.md)
- [Utilisation du suivi pour résoudre les problèmes posés par votre application](using-tracing-to-troubleshoot-your-application.md)
- [Administration et diagnostics](../index.md)
