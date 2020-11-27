---
title: Exceptions de transactions
ms.date: 03/30/2017
ms.assetid: 1d27ed51-7eda-477f-9eca-94fa129f3e07
ms.openlocfilehash: dcdf825699368617335f2d59a05f8826884a8e9e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96285679"
---
# <a name="transaction-exceptions"></a>Exceptions de transactions

Cette rubrique répertorie toutes les exceptions générées par la transaction Windows Communication Foundation (WCF).  
  
## <a name="exception-list"></a>Liste des exceptions  
  
|Code de la ressource|Chaîne de la ressource|  
|-------------------|---------------------|  
|SFxCannotHaveDifferentTransactionProtocolsInOneBinding|Les informations de stratégie qui sont importées à partir des métadonnées spécifient des valeurs différentes pour TransactionProtocol au sein des opérations. Un seul TransactionProtocol est pris en charge pour chaque point de terminaison.|  
|SFxTransactionAutoCompleteFalseAndInstanceContextMode|TransactionAutoComplete ne peut pas avoir la valeur false à moins que la valeur InstanceContextMode du service soit PerSession. Une erreur a été détectée sur l'implémentation de l'opération et du contrat spécifiés.|  
|SFxTransactionInvalidSetTransactionComplete|OperationContext.SetTransactionComplete peut être appelé dans une opération uniquement lorsque TransactionAutoComplete à la valeur false et TransactionScopeRequired la valeur true. Ce scénario n’est pas valide et la transaction en cours est terminée.|  
|TransactionFlowRequiredIssuedTokens|Pour transmettre une transaction, la transmission des jetons émis doit également être prise en charge.|  
|TrustDriverVersionDoesNotSupportIssuedTokens|La version de Trust configurée ne prend pas en charge les jetons émis. Utilisez WSTrustFeb2005 ou une version ultérieure.|
