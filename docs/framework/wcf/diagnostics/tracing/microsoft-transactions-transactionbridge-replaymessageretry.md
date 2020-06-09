---
title: Microsoft.Transactions.TransactionBridge.ReplayMessageRetry
ms.date: 03/30/2017
ms.assetid: e5b820ae-504d-405a-926a-9effa41d2369
ms.openlocfilehash: 162452d5d12859571d78ef19cf1d838953ee7acd
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596205"
---
# <a name="microsofttransactionstransactionbridgereplaymessageretry"></a>Microsoft.Transactions.TransactionBridge.ReplayMessageRetry
Une nouvelle tentative de message Replay a été envoyée à un coordinateur qui ne répond pas.  
  
## <a name="description"></a>Description  
 Suivi si le gestionnaire de transactions local a dû renvoyer un message Replay à un coordinateur supérieur parce qu’il n’a pas reçu de réponse dans un délai donné.  
  
## <a name="troubleshooting"></a>Dépannage  
 Recherchez d'éventuels problèmes liés au réseau ou au produit pouvant empêcher la réponse d'être remise à temps.  Si un nombre élevé de ces messages apparaissent, cela peut indiquer des problèmes d'infrastructure ou des délais de réponse anormalement longs. Ces deux problèmes réduiront considérablement le débit des transactions au sein du système.  
  
## <a name="see-also"></a>Voir aussi

- [Suivi](index.md)
- [Utilisation du suivi pour résoudre les problèmes posés par votre application](using-tracing-to-troubleshoot-your-application.md)
- [Administration et diagnostics](../index.md)
