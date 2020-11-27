---
title: MsmqBindingElementBase
ms.date: 03/30/2017
ms.assetid: 210d41ab-a2a4-4d7a-afd2-0916c08a4015
ms.openlocfilehash: 48d26bfa9074fd605e3545579f0bdc2744dfc7d8
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96267857"
---
# <a name="msmqbindingelementbase"></a>MsmqBindingElementBase

MsmqBindingElementBase  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp  
class MsmqBindingElementBase : TransportBindingElement  
{  
  string CustomDeadLetterQueue;  
  string DeadLetterQueue;  
  boolean Durable;  
  boolean ExactlyOnce;  
  sint32 MaxRetryCycles;  
  string ReceiveErrorHandling;  
  sint32 ReceiveRetryCount;  
  datetime RetryCycleDelay;  
  datetime TimeToLive;  
  boolean UseMsmqTracing;  
  boolean UseSourceJournal;  
};  
```  
  
## <a name="methods"></a>Méthodes  

 La classe MsmqBindingElementBase ne définit pas de méthode.  
  
## <a name="properties"></a>Propriétés  

 La classe MsmqBindingElementBase a les propriétés suivantes :  
  
### <a name="customdeadletterqueue"></a>CustomDeadLetterQueue  

 Type de données : chaîne  
  
 Type d'accès : Lecture seule  
  
 URI qui contient l'emplacement de la file d'attente de lettres mortes pour chaque application, dans laquelle les messages expirés ou dont le transfert ou la remise a échoué sont placés.  
  
### <a name="deadletterqueue"></a>DeadLetterQueue  

 Type de données : chaîne  
  
 Type d'accès : Lecture seule  
  
 Valeur d'énumération qui indique le type de la file d'attente de lettres mortes à utiliser.  
  
### <a name="durable"></a>Durable  

 Type de données : booléen  
  
 Type d'accès : Lecture seule  
  
 Valeur qui indique si les messages traités par cette liaison sont durables ou volatils.  
  
### <a name="exactlyonce"></a>ExactlyOnce  

 Type de données : booléen  
  
 Type d'accès : Lecture seule  
  
 Valeur booléenne qui indique si les messages traités par cette liaison sont reçus exactement une fois.  
  
### <a name="maxretrycycles"></a>MaxRetryCycles  

 Type de données : sint32  
  
 Type d'accès : Lecture seule  
  
 Nombre maximal de cycles de nouvelle tentative de livraison de messages à l'application de réception.  
  
### <a name="receiveerrorhandling"></a>ReceiveErrorHandling  

 Type de données : chaîne  
  
 Type d'accès : Lecture seule  
  
 Paramètres de gestion de messages incohérents.  
  
### <a name="receiveretrycount"></a>ReceiveRetryCount  

 Type de données : sint32  
  
 Type d'accès : Lecture seule  
  
 Nombre maximal de nouvelles tentatives immédiates sur un message qui est lu à partir de la file d'attente d'application.  
  
### <a name="retrycycledelay"></a>RetryCycleDelay  

 Type de données : datetime  
  
 Type d'accès : Lecture seule  
  
 Valeur qui indique l'intervalle entre des cycles de nouvelle tentative de remise d'un message n'ayant pas pu être remis immédiatement.  
  
### <a name="timetolive"></a>timeToLive  

 Type de données : datetime  
  
 Type d'accès : Lecture seule  
  
 Intervalle qui indique combien de temps les messages traités par cette liaison peuvent séjourner dans la file d’attente avant expiration.  
  
### <a name="usemsmqtracing"></a>UseMsmqTracing  

 Type de données : booléen  
  
 Type d'accès : Lecture seule  
  
 Valeur booléenne qui indique si les messages traités par cette liaison doivent être suivis.  
  
### <a name="usesourcejournal"></a>UseSourceJournal  

 Type de données : booléen  
  
 Type d'accès : Lecture seule  
  
 Valeur booléenne qui indique si les copies des messages traités par cette liaison doivent être stockées dans la file d’attente du journal source.  
  
## <a name="requirements"></a>Spécifications  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|-----------------------------------|  
|Espace de noms|Défini dans root\ServiceModel|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.NetMsmqBinding>
- <xref:System.ServiceModel.MsmqBindingBase>
