---
title: AsymmetricSecurityBindingElement
ms.date: 03/30/2017
ms.assetid: 7bd3b6be-8f77-4927-93ae-6fa371893cca
ms.openlocfilehash: 00485ff80a0064e700d99203de3aa581d3761f30
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96255726"
---
# <a name="asymmetricsecuritybindingelement"></a>AsymmetricSecurityBindingElement

AsymmetricSecurityBindingElement  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp
class AsymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a>Méthodes  

 La classe AsymmetricSecurityBindingElement ne définit pas de méthodes.  
  
## <a name="properties"></a>Propriétés  

 La classe AsymmetricSecurityBindingElement a les propriétés suivantes :  
  
### <a name="messageprotectionorder"></a>MessageProtectionOrder  

 Type de données : chaîne  
  
 Type d'accès : Lecture seule  
  
 Ordre de chiffrement et de signature des messages de cette liaison.  
  
### <a name="requiresignatureconfirmation"></a>RequireSignatureConfirmation  

 Type de données : booléen  
  
 Type d'accès : Lecture seule  
  
 Si la liaison requiert la confirmation de signature.  
  
## <a name="requirements"></a>Spécifications  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|-----------------------------------|  
|Espace de noms|Défini dans root\ServiceModel|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>
