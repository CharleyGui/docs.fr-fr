---
title: Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout
ms.date: 03/30/2017
ms.assetid: 2dbe34c5-57c7-4b64-9257-63021911d03c
ms.openlocfilehash: dd2a0b67ec140aa2e6fe1abad8e85c0206abd8ea
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84579019"
---
# <a name="microsofttransactionstransactionbridgevolatileoutcometimeout"></a>Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout
Le service du protocole WS-AT a dépassé le délai spécifié lors de l'attente d'une réponse à un message de résultat provenant d'un participant volatil. Le résultat de la transaction peut s'avérer incertain si le participant retourne.  
  
## <a name="description"></a>Description  
 Suivi lorsqu’un participant volatil a décidé de valider ou d’abandonner mais n’a pas répondu à une demande de validation ou de restauration dans un délai donné.  
  
## <a name="troubleshooting"></a>Dépannage  
 Assurez-vous que tous les participants volatils sont en mesure de répondre dans le délai imparti. Le délai par défaut est de 180 secondes.  S'il est insuffisant, augmentez le délai du minuteur `VolatileOutcomeDelay` de WS-AT.  
  
## <a name="see-also"></a>Voir aussi

- [Suivi](index.md)
- [Utilisation du suivi pour résoudre les problèmes posés par votre application](using-tracing-to-troubleshoot-your-application.md)
- [Administration et diagnostics](../index.md)
