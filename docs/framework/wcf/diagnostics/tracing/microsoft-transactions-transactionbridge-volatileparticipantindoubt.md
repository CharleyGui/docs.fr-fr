---
title: Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt
ms.date: 03/30/2017
ms.assetid: 3e8fc825-9f22-47e7-9c16-d64ef291c932
ms.openlocfilehash: ab1c2c8afe3a66536810a614cc6deac12519cb9b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599631"
---
# <a name="microsofttransactionstransactionbridgevolatileparticipantindoubt"></a>Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt
Le service du protocole WS-AT a reçu un message Prepared ou Replay d'un participant volatil non reconnu. Une faute a été renvoyée au participant, qui déclarera que le résultat de la transaction est douteux.  
  
## <a name="description"></a>Description  
 Suivi généré lorsque le gestionnaire de transactions local reçoit un message Prepared ou Replay d’une inscription volatile qu’il a déjà oubliée.  
  
## <a name="troubleshooting"></a>Dépannage  
 Recherchez les causes potentielles de retard des messages qui viennent du participant volatil.  
  
## <a name="see-also"></a>Voir aussi

- [Suivi](index.md)
- [Utilisation du suivi pour résoudre les problèmes posés par votre application](using-tracing-to-troubleshoot-your-application.md)
- [Administration et diagnostics](../index.md)
