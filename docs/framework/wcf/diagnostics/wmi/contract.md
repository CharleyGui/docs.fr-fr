---
title: Contrat
ms.date: 03/30/2017
ms.assetid: aa00f6b3-7e1f-4213-841a-206463fca20b
ms.openlocfilehash: e4a21e95a6f1f1860ed36c968d17bb8ac8465dce
ms.sourcegitcommit: 9ee6cd851b6e176a5811ea28ed0d5935c71950f9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68868430"
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
  
## <a name="properties"></a>Properties  
 La classe Contract a les propriétés suivantes :  
  
### <a name="appdomainid"></a>AppDomainId  
 Type de données : sint32  
  
 Type d’accès: Lecture seule  
  
 ID du domaine d'application qui héberge le contrat.  
  
### <a name="behaviors"></a>comportements  
 Type de données: Tableau de comportements  
  
 Type d’accès: Lecture seule  
  
 Comportements associés à ce contrat.  
  
### <a name="name"></a>Name  
 Type de données : chaîne  
  
 Type d’accès: Lecture seule  
  
 Nom du contrat dans WSDL.  
  
### <a name="namespace"></a>Espace de noms  
 Type de données : chaîne  
  
 Type d’accès: Lecture seule  
  
 Espace de noms de l'élément `portType` dans WSDL.  
  
### <a name="operations"></a>Opérations  
 Type de données: Tableau d’opérations  
  
 Type d’accès: Lecture seule  
  
 Opérations de ce contrat.  
  
### <a name="processid"></a>ProcessId  
 Type de données : sint32  
  
 Type d’accès: Lecture seule  
  
 ID du processus qui héberge le contrat.  
  
### <a name="ref"></a>ref  
 Type de données: Contrat  
  
 Type d’accès: Lecture seule  
  
 Type de rappel lorsque le contrat est un contrat duplex.  
  
### <a name="sessionmode"></a>SessionMode  
 Type de données : chaîne  
  
 Type d’accès: Lecture seule  
  
 Indique si le contrat nécessite que la liaison associée à ce contrat utilise les sessions de canal.  
  
### <a name="type"></a>Type  
 Type de données : chaîne  
  
 Type d’accès: Lecture seule  
  
 Type du contrat.  
  
## <a name="requirements"></a>Configuration requise  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|-----------------------------------|  
|Espace de noms|Défini dans root\ServiceModel|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Description.ContractDescription>
