---
title: Contrat
ms.date: 03/30/2017
ms.assetid: aa00f6b3-7e1f-4213-841a-206463fca20b
ms.openlocfilehash: 0df39bbd0b273f1e898ccbe585be288cc245b7f5
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96274138"
---
# <a name="contract"></a>Contrat

Contrat  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp
class Contract  
{  
  sint32 AppDomainId;  
  Behavior Behaviors[];  
  string Name;  
  string Namespace;  
  Operation Operations[];  
  sint32 ProcessId;  
  Contract ref;  
  string SessionMode;  
  string Type;  
};  
```  
  
## <a name="methods"></a>Méthodes  

 La classe Contract ne définit pas de méthodes.  
  
## <a name="properties"></a>Propriétés  

 La classe Contract a les propriétés suivantes :  
  
### <a name="appdomainid"></a>AppDomainId  

 Type de données : sint32  
  
 Type d'accès : Lecture seule  
  
 ID du domaine d'application qui héberge le contrat.  
  
### <a name="behaviors"></a>Comportements  

 Type de données : tableau de comportements  
  
 Type d'accès : Lecture seule  
  
 Comportements associés à ce contrat.  
  
### <a name="name"></a>Nom  

 Type de données : chaîne  
  
 Type d'accès : Lecture seule  
  
 Nom du contrat dans WSDL.  
  
### <a name="namespace"></a>Espace de noms  

 Type de données : chaîne  
  
 Type d'accès : Lecture seule  
  
 Espace de noms de l'élément `portType` dans WSDL.  
  
### <a name="operations"></a>Opérations  

 Type de données : tableau d'opérations  
  
 Type d'accès : Lecture seule  
  
 Opérations de ce contrat.  
  
### <a name="processid"></a>ProcessId  

 Type de données : sint32  
  
 Type d'accès : Lecture seule  
  
 ID du processus qui héberge le contrat.  
  
### <a name="ref"></a>ref  

 Type de données: contrat  
  
 Type d'accès : Lecture seule  
  
 Type de rappel lorsque le contrat est un contrat duplex.  
  
### <a name="sessionmode"></a>SessionMode  

 Type de données : chaîne  
  
 Type d'accès : Lecture seule  
  
 Indique si le contrat nécessite que la liaison associée à ce contrat utilise les sessions de canal.  
  
### <a name="type"></a>Type  

 Type de données : chaîne  
  
 Type d'accès : Lecture seule  
  
 Type du contrat.  
  
## <a name="requirements"></a>Spécifications  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|-----------------------------------|  
|Espace de noms|Défini dans root\ServiceModel|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Description.ContractDescription>
