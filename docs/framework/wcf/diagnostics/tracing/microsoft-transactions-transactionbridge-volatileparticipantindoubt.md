---
title: Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt
ms.date: 03/30/2017
ms.assetid: 3e8fc825-9f22-47e7-9c16-d64ef291c932
ms.openlocfilehash: 9ad9dc9fd078f7ad4c0934c8bf9bb73feb935014
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96236648"
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
