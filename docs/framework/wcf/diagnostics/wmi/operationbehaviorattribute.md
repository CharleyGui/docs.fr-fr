---
title: OperationBehaviorAttribute
ms.date: 03/30/2017
ms.assetid: 8c9b0755-9e83-411f-bdcb-61a586022797
ms.openlocfilehash: 76cc619aed4ba2b944a8d11dc454a40368a4068c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96269078"
---
# <a name="operationbehaviorattribute"></a>OperationBehaviorAttribute

OperationBehaviorAttribute  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp
class OperationBehaviorAttribute : Behavior  
{  
  boolean AutoDisposeParameters;  
  string Impersonation;  
  string ReleaseInstanceMode;  
  boolean TransactionAutoComplete;  
  boolean TransactionScopeRequired;  
};  
```  
  
## <a name="methods"></a>Méthodes  

 La classe OperationBehaviorAttribute ne définit pas de méthodes.  
  
## <a name="properties"></a>Propriétés  

 La classe OperationBehaviorAttribute a les propriétés suivantes :  
  
### <a name="autodisposeparameters"></a>AutoDisposeParameters  

 Type de données : booléen  
  
 Type d'accès : Lecture seule  
  
 État de la fonctionnalité d’élimination automatique pour les paramètres.  
  
### <a name="impersonation"></a>Emprunt d'identité  

 Type de données : chaîne  
  
 Type d'accès : Lecture seule  
  
 Indique le niveau d'emprunt d'identité de l'appelant pris en charge par l'opération.  
  
### <a name="releaseinstancemode"></a>ReleaseInstanceMode  

 Type de données : chaîne  
  
 Type d'accès : Lecture seule  
  
 Indique à quel moment il convient de recycler l'objet lors de l'appel d'une opération.  
  
### <a name="transactionautocomplete"></a>TransactionAutoComplete  

 Type de données : booléen  
  
 Type d'accès : Lecture seule  
  
 Indique s’il convient de valider automatiquement la transaction actuelle si aucune exception non traitée ne se produit.  
  
### <a name="transactionscoperequired"></a>TransactionScopeRequired  

 Type de données : booléen  
  
 Type d'accès : Lecture seule  
  
 Indique si l’opération nécessite une transaction.  
  
## <a name="requirements"></a>Spécifications  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|-----------------------------------|  
|Espace de noms|Défini dans root\ServiceModel|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.OperationBehaviorAttribute>
