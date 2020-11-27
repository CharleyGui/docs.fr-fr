---
title: Service
ms.date: 03/30/2017
ms.assetid: 999806e1-6376-409e-b998-b0af391adfe7
ms.openlocfilehash: aa4eecbcc8a2ef818cd99d777b0e3c2f1f222e46
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96273280"
---
# <a name="service"></a>Service

Service  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp
class Service  
{  
  string BaseAddresses[];  
  Behavior Behaviors[];  
  string ConfigurationName;  
  string CounterInstanceName;  
  string DistinguishedName;  
  string Extensions[];  
  string Metadata[];  
  string Name;  
  string Namespace;  
  datetime Opened;  
  Channel OutgoingChannels[];  
  sint32 ProcessId;  
};  
```  
  
## <a name="methods"></a>Méthodes  

 La classe Service ne définit aucune méthode.  
  
## <a name="properties"></a>Propriétés  

 La classe Service a les propriétés suivantes :  
  
### <a name="baseaddresses"></a>BaseAddresses  

 Type de données : tableau de chaînes  
  
 Type d'accès : Lecture seule  
  
 Les adresses de base utilisées par le service.  
  
### <a name="behaviors"></a>Comportements  

 Type de données : tableau de comportements  
  
 Type d'accès : Lecture seule  
  
 Les comportements associés à ce service.  
  
### <a name="configurationname"></a>ConfigurationName  

 Type de données : chaîne  
  
 Type d'accès : Lecture seule  
  
 ServiceElement_BehaviorConfiguration  
  
### <a name="counterinstancename"></a>CounterInstanceName  

 Type de données : chaîne  
  
 Type d'accès : Lecture seule  
  
 Le nom d'instance de l'instance des compteurs de performances du service.  
  
### <a name="distinguishedname"></a>DistinguishedName  

 Type de données : chaîne  
  
 Type d'accès : Lecture seule  
  
 Nom du service à cette adresse.  
  
### <a name="extensions"></a>Extensions  

 Type de données : tableau de chaînes  
  
 Type d'accès : Lecture seule  
  
 Les contextes d’instance pour les extensions de l’instance de service.  
  
### <a name="metadata"></a>Métadonnées  

 Type de données : tableau de chaînes  
  
 Type d'accès : Lecture seule  
  
 Les paramètres de métadonnées du service.  
  
### <a name="name"></a>Nom  

 Type de données : chaîne  
  
 Type d'accès : Lecture seule  
  
 Le nom unique de ce service.  
  
### <a name="namespace"></a>Espace de noms  

 Type de données : chaîne  
  
 Type d'accès : Lecture seule  
  
 L'espace de noms du service.  
  
### <a name="opened"></a>Ouvert  

 Type de données : datetime  
  
 Type d'accès : Lecture seule  
  
 L'heure à laquelle le service a été ouvert.  
  
### <a name="outgoingchannels"></a>OutgoingChannels  

 Type de données : tableau de canaux  
  
 Type d'accès : Lecture seule  
  
 Les canaux qui sortent de l'instance de service.  
  
### <a name="processid"></a>ProcessId  

 Type de données : sint32  
  
 Type d'accès : Lecture seule  
  
 L'ID de processus du processus qui héberge le service.  
  
## <a name="requirements"></a>Spécifications  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|-----------------------------------|  
|Espace de noms|Défini dans root\ServiceModel|
