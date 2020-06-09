---
title: Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing
ms.date: 03/30/2017
ms.assetid: 10ef3876-6f8e-4d4e-8444-f47847b64795
ms.openlocfilehash: 31fb8d466c76c7490aa80dfcab089332af4036a2
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84589130"
---
# <a name="microsofttransactionstransactionbridgedurableparticipantreplaywhilepreparing"></a>Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing
Le service de protocole WS-AT a reçu un message Replay d'un participant durable n'ayant pas répondu au message Prepared. Par conséquent, la transaction a été abandonnée.  
  
## <a name="description"></a>Description  
 Un suivi est généré si un message Replay est reçu lorsqu'un participant durable est encore en cours de préparation. Il s’agit d’un message illégal pour cet état et la transaction va être abandonnée.  
  
## <a name="troubleshooting"></a>Dépannage

La réception de cette erreur peut indiquer qu’un participant durable (y compris subalterne subordonné) a récupéré d’une défaillance ; Toutefois, il ne garantit pas le résultat de la transaction et demande son état.  
  
## <a name="see-also"></a>Voir aussi

- [Suivi](index.md)
- [Utilisation du suivi pour résoudre les problèmes posés par votre application](using-tracing-to-troubleshoot-your-application.md)
- [Administration et diagnostics](../index.md)
