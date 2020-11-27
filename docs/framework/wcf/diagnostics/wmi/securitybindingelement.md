---
title: SecurityBindingElement
ms.date: 03/30/2017
ms.assetid: ef93b6e6-3524-48a8-94d3-c8837f1872f9
ms.openlocfilehash: 61eae75de04f75b6ad6e78d16569595732b3d28f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96273306"
---
# <a name="securitybindingelement"></a>SecurityBindingElement

SecurityBindingElement  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp
class SecurityBindingElement : BindingElement  
{  
  string DefaultAlgorithmSuite;  
  boolean IncludeTimestamp;  
  string KeyEntropyMode;  
  LocalServiceSecuritySettings LocalServiceSecuritySettings;  
  string MessageSecurityVersion;  
  string SecurityHeaderLayout;  
};  
```  
  
## <a name="methods"></a>Méthodes  

 La classe SecurityBindingElement ne définit pas de méthode.  
  
## <a name="properties"></a>Propriétés  

 La classe SecurityBindingElement a les propriétés suivantes :  
  
### <a name="defaultalgorithmsuite"></a>DefaultAlgorithmSuite  

 Type de données : chaîne  
  
 Type d'accès : Lecture seule  
  
 Spécifie les algorithmes à utiliser avec la liaison.  
  
### <a name="includetimestamp"></a>IncludeTimestamp  

 Type de données : booléen  
  
 Type d'accès : Lecture seule  
  
 Valeur booléenne qui spécifie si chaque message contient un horodatage.  
  
### <a name="keyentropymode"></a>KeyEntropyMode  

 Type de données : chaîne  
  
 Type d'accès : Lecture seule  
  
 Source d'entropie utilisée pour créer des clés.  
  
### <a name="localservicesecuritysettings"></a>LocalServiceSecuritySettings  

 Type de données : LocalServiceSecuritySettings  
  
 Type d'accès : Lecture seule  
  
 Propriétés de sécurité spécifiques d’une liaison pour le service local.  
  
### <a name="messagesecurityversion"></a>MessageSecurityVersion  

 Type de données : chaîne  
  
 Type d'accès : Lecture seule  
  
 Version utilisée pour la sécurité de message.  
  
### <a name="securityheaderlayout"></a>SecurityHeaderLayout  

 Type de données : chaîne  
  
 Type d'accès : Lecture seule  
  
 Ordre des éléments dans l'en-tête de sécurité pour cette liaison.  
  
## <a name="requirements"></a>Spécifications  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|-----------------------------------|  
|Espace de noms|Défini dans root\ServiceModel|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Channels.SecurityBindingElement>
