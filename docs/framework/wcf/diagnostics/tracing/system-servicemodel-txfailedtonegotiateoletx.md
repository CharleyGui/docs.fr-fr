---
title: System.ServiceModel.TxFailedToNegotiateOleTx
ms.date: 03/30/2017
ms.assetid: 3f0f0b4b-a1ad-4704-8329-455daf54892d
ms.openlocfilehash: 2c9ea77cdd76d4593c2ee5b09a4b917677b8925f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601411"
---
# <a name="systemservicemodeltxfailedtonegotiateoletx"></a>System.ServiceModel.TxFailedToNegotiateOleTx
La négociation du protocole OleTransactions n'a pas pu se terminer pour le contexte de coordination spécifié.  
  
## <a name="description"></a>Description  
 Tracé lorsqu'une transaction entrante avec des informations OleTx ne peut pas utiliser les informations OleTx jointes, et a recours à l'utilisation de WS-AT à la place.  
  
## <a name="troubleshooting"></a>Dépannage  
 Indique un problème potentiel avec la communication de MSDTC RPC entre les ordinateurs. Si beaucoup de ces suivis apparaissent dans le journal, il peut s'ensuivre une baisse radicale des performances.  Si OleTx n'est pas souhaité, affectez la valeur 0 à `OleTxUpgradeEnabled` dans la configuration du registre WS-AT.  
  
## <a name="see-also"></a>Voir aussi

- [Suivi](index.md)
- [Utilisation du suivi pour résoudre les problèmes posés par votre application](using-tracing-to-troubleshoot-your-application.md)
- [Administration et diagnostics](../index.md)
