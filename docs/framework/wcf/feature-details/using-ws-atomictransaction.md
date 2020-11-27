---
title: Utilisation de WS-AtomicTransaction
ms.date: 03/30/2017
helpviewer_keywords:
- WS-AT protocol [WCF]
ms.assetid: 04a4c200-0af0-4c5d-a3d9-87cb7339e054
ms.openlocfilehash: 22b84dc49ab723953ce36402ac14221f410dda11
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96281597"
---
# <a name="using-ws-atomictransaction"></a>Utilisation de WS-AtomicTransaction

WS-AtomicTransaction (WS-AT) est un protocole de transaction interopérable. Ce protocole vous permet de transférer des transactions distribuées à l'aide de messages de service Web et d'assurer la coordination d'infrastructures de transaction hétérogènes de manière interopérable. WS-AT utilise un protocole de validation en deux phases pour un résultat atomique entre les applications distribuées, les gestionnaires de transactions et les gestionnaires de ressources.  
  
 L’implémentation WS-AT Windows Communication Foundation (WCF) fournit inclut un service de protocole intégré au gestionnaire de transactions Microsoft Distributed Transaction Coordinator (MSDTC). À l’aide de WS-AT, les applications WCF peuvent transmettre des transactions à d’autres applications, y compris des services Web interopérables construits à l’aide de technologies tierces.  
  
 Lorsqu’une transaction est transférée entre une application cliente et une application serveur, le protocole utilisé dépend de la liaison exposée par le serveur sur le point de terminaison sélectionné par le client. Certaines liaisons fournies par le système WCF spécifient par défaut le `OleTransactions` protocole comme format de propagation de transaction, tandis que d’autres spécifient par défaut WS-AT. Vous pouvez également modifier le protocole de transaction utilisé par les liaisons en programmant le protocole de votre choix.  
  
 Le choix du protocole a des conséquences sur :  
  
- Le format des en-têtes de message utilisé pour transférer la transaction du client au serveur.  
  
- Le protocole réseau utilisé pour exécuter le protocole de validation en deux phases entre le gestionnaire de transactions du client et la transaction du serveur et ainsi déterminer le résultat final de la transaction.  
  
 Si le serveur et le client sont écrits à l’aide de WCF, vous n’avez pas besoin d’utiliser WS-AT. Il vous suffit en effet d'utiliser les paramètres par défaut de `NetTcpBinding` et d'activer l'attribut `TransactionFlow` pour que le protocole `OleTransactions` soit utilisé à la place. Pour plus d’informations, consultez [\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md). En revanche, si vous transférez des transactions vers des services Web construits à l’aide de technologies tierces, vous devez utiliser le protocole WS-AT.  
  
## <a name="see-also"></a>Voir aussi

- [Configuration de la prise en charge WS-Atomic Transaction](configuring-ws-atomic-transaction-support.md)
