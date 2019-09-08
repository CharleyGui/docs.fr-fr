---
title: Point de terminaison
ms.date: 03/30/2017
ms.assetid: fe63370d-81a1-40f3-97c2-59cb357c78d2
ms.openlocfilehash: 03c401358839671d750985b95b1aada599931aad
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795897"
---
# <a name="endpoint"></a>Point de terminaison
Point de terminaison  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp
class Endpoint  
{  
  string Address;  
  string AddressHeaders[];  
  string AddressIdentity;  
  sint32 AppDomainId;  
  Behavior Behaviors[];  
  Binding Binding;  
  string ContractName;  
  string CounterInstanceName;  
  string ListenUri;  
  string Name;  
  sint32 ProcessId;  
  Contract ref;  
};  
```  
  
## <a name="methods"></a>Méthodes  
 La classe Endpoint définit la méthode suivante.  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetOperationCounterInstanceName](getoperationcounterinstancename.md)|Récupère le nom d'instance du compteur de performance d'opération|  
  
## <a name="properties"></a>Properties  
 La classe Endpoint a les propriétés suivantes :  
  
### <a name="address"></a>Adresse  
 Type de données : chaîne  
  
 Type d’accès : Lecture seule  
  
 URI qui contient l'adresse du point de terminaison.  
  
### <a name="addressheaders"></a>AddressHeaders  
 Type de données : tableau de chaînes  
  
 Type d’accès : Lecture seule  
  
 Collection d’en-têtes d’adresse jointe à ce point de terminaison.  
  
### <a name="addressidentity"></a>AddressIdentity  
 Type de données : chaîne  
  
 Type d’accès : Lecture seule  
  
 Identité du point de terminaison.  
  
### <a name="appdomainid"></a>AppDomainId  
 Type de données : sint32  
  
 Type d’accès : Lecture seule  
  
 ID du domaine d'application qui héberge le point de terminaison.  
  
### <a name="behaviors"></a>comportements  
 Type de données : Tableau de comportements  
  
 Type d’accès : Lecture seule  
  
 Collection de comportements implémentée par ce point de terminaison.  
  
### <a name="binding"></a>Liaison  
 Type de données : Liaison  
  
 Type d’accès : Lecture seule  
  
 Liaison utilisée par ce point de terminaison.  
  
### <a name="contractname"></a>ContractName  
 Type de données : chaîne  
  
 Type d’accès : Lecture seule  
  
 Chaîne qui spécifie quel contrat est exposé par ce point de terminaison.  
  
### <a name="counterinstancename"></a>CounterInstanceName  
 Type de données : chaîne  
  
 Type d’accès : Lecture seule  
  
 Nom de l'instance des compteurs de performance du point de terminaison.  
  
### <a name="listenuri"></a>ListenUri  
 Type de données : chaîne  
  
 Type d’accès : Lecture seule  
  
 URI sur lequel le point de terminaison écoute.  
  
### <a name="name"></a>Nom  
 Type de données : chaîne  
  
 Type d’accès : Lecture seule  
  
 Nom unique de ce point de terminaison.  
  
### <a name="processid"></a>ProcessId  
 Type de données : sint32  
  
 Type d’accès : Lecture seule  
  
 ID du processus qui héberge le point de terminaison.  
  
### <a name="ref"></a>ref  
 Type de données : Contrat  
  
 Type d’accès : Lecture seule  
  
 Le contrat exposé par ce point de terminaison.  
  
## <a name="requirements"></a>Configuration requise  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|-----------------------------------|  
|Espace de noms|Défini dans root\ServiceModel|
