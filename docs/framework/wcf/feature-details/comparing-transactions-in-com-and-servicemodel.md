---
title: Comparaison des transactions dans COM+ et dans ServiceModel
ms.date: 03/30/2017
ms.assetid: e493bcdd-b91a-4486-853f-83dbcd1931b7
ms.openlocfilehash: 30ecbd374e909141dbc944740f90c1b41ac44ed2
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96264906"
---
# <a name="comparing-transactions-in-com-and-servicemodel"></a>Comparaison des transactions dans COM+ et dans ServiceModel

Cette rubrique explique comment simuler le comportement d’un service COM+ transactionnel à l’aide des attributs Windows Communication Foundation (WCF) fournis par l' <xref:System.ServiceModel> espace de noms.  
  
## <a name="emulating-com-using-servicemodel-attributes"></a>Émulation de COM+ à l'aide d'attributs ServiceModel  

 Le tableau suivant compare l' <xref:System.EnterpriseServices.TransactionOption> énumération utilisée pour créer une `EnterpriseServices` transaction et la manière dont elles sont corrélées aux attributs WCF fournis par l' <xref:System.ServiceModel> espace de noms.  
  
|Attribut COM+|Attributs WCF|  
|---------------------|------------------------------------------------------------------------|  
|RequiresNew|<xref:System.ServiceModel.TransactionFlowAttribute> a la valeur <xref:System.ServiceModel.TransactionFlowOption.NotAllowed>.<br /><br /> <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> a la valeur `true`.<br /><br /> L’attribut `TransactionFlow` dans l’élément de liaison a la valeur `false`.|  
|Obligatoire|<xref:System.ServiceModel.TransactionFlowAttribute> a la valeur <xref:System.ServiceModel.TransactionFlowOption.Allowed>.<br /><br /> <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> a la valeur `true`.<br /><br /> L’attribut `TransactionFlow` dans l’élément de liaison a la valeur `true`.|  
|Prise en charge|Il n'existe pas d'équivalent direct. En général, vous devez à la place adopter le comportement spécifié pour `Required`.|  
|NotSupported|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> a la valeur `false`.<br /><br /> L’attribut `TransactionFlow` dans l’élément de liaison a la valeur `false`.|  
|Désactivé|Il n'existe pas d'équivalent direct. En général, vous devez à la place adopter le comportement spécifié pour `NotSupported`.|
