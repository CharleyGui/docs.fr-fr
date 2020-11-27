---
title: LocalServiceSecuritySettings
ms.date: 03/30/2017
ms.assetid: 490aa0e5-5242-4f8d-b505-5ec6287633b4
ms.openlocfilehash: eecf2b0bf459fd14236c550e393149553183b3ac
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96267921"
---
# <a name="localservicesecuritysettings"></a>LocalServiceSecuritySettings

LocalServiceSecuritySettings  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp
class LocalServiceSecuritySettings  
{  
  boolean DetectReplays;  
  datetime InactivityTimeout;  
  datetime IssuedCookieLifetime;  
  sint32 MaxCachedCookies;  
  datetime MaxClockSkew;  
  sint32 MaxPendingSessions;  
  sint32 MaxStatefulNegotiations;  
  datetime NegotiationTimeout;  
  boolean ReconnectTransportOnFailure;  
  sint32 ReplayCacheSize;  
  datetime ReplayWindow;  
  datetime SessionKeyRenewalInterval;  
  datetime SessionKeyRolloverInterval;  
  datetime TimestampValidityDuration;  
};  
```  
  
## <a name="methods"></a>Méthodes  

 La classe LocalServiceSecuritySettings ne définit pas de méthode.  
  
## <a name="properties"></a>Propriétés  

 La classe LocalServiceSecuritySettings a les propriétés suivantes :  
  
### <a name="detectreplays"></a>DetectReplays  

 Type de données : booléen  
  
 Type d'accès : Lecture seule  
  
 Valeur booléenne qui spécifie si les attaques par relecture contre le canal sont détectées et traitées automatiquement.  
  
### <a name="inactivitytimeout"></a>InactivityTimeout  

 Type de données : datetime  
  
 Type d'accès : Lecture seule  
  
 Nombre maximal de sessions de sécurité en attente que le service prend en charge.  
  
### <a name="issuedcookielifetime"></a>IssuedCookieLifetime  

 Type de données : datetime  
  
 Type d'accès : Lecture seule  
  
 TimeSpan qui spécifie la durée de vie de tous les nouveaux cookies de sécurité.  
  
### <a name="maxcachedcookies"></a>MaxCachedCookies  

 Type de données : sint32  
  
 Type d'accès : Lecture seule  
  
 Nombre maximal de cookies qui peuvent être mis en cache.  
  
### <a name="maxclockskew"></a>MaxClockSkew  

 Type de données : datetime  
  
 Type d'accès : Lecture seule  
  
 TimeSpan qui spécifie la différence de temps maximale entre les horloges système des deux parties communicantes.  
  
### <a name="maxpendingsessions"></a>MaxPendingSessions  

 Type de données : sint32  
  
 Type d'accès : Lecture seule  
  
 Nombre maximal de connexions en attente sur le service.  
  
### <a name="maxstatefulnegotiations"></a>MaxStatefulNegotiations  

 Type de données : sint32  
  
 Type d'accès : Lecture seule  
  
 Nombre de négociations de sécurité qui peuvent être actives simultanément.  
  
### <a name="negotiationtimeout"></a>NegotiationTimeout  

 Type de données : datetime  
  
 Type d'accès : Lecture seule  
  
 TimeSpan qui spécifie la durée maximale de la phase de négociation de sécurité entre le serveur et le client.  
  
### <a name="reconnecttransportonfailure"></a>ReconnectTransportOnFailure  

 Type de données : booléen  
  
 Type d'accès : Lecture seule  
  
 Valeur booléenne qui spécifie si des connexions utilisant la messagerie WS-Reliable tentent une reconnexion après des incidents de transport.  
  
### <a name="replaycachesize"></a>ReplayCacheSize  

 Type de données : sint32  
  
 Type d'accès : Lecture seule  
  
 Nombre de pointeurs en cache utilisés pour la détection de relecture.  
  
### <a name="replaywindow"></a>ReplayWindow  

 Type de données : datetime  
  
 Type d'accès : Lecture seule  
  
 TimeSpan qui spécifie la durée de validité des pointeurs de messages individuels.  
  
### <a name="sessionkeyrenewalinterval"></a>SessionKeyRenewalInterval  

 Type de données : datetime  
  
 Type d'accès : Lecture seule  
  
 TimeSpan qui spécifie le délai d'attente au terme duquel l'initiateur renouvelle la clé de la session de sécurité.  
  
### <a name="sessionkeyrolloverinterval"></a>SessionKeyRolloverInterval  

 Type de données : datetime  
  
 Type d'accès : Lecture seule  
  
 TimeSpan qui spécifie la période de validité d'une clé de session précédente sur les messages entrants pendant un renouvellement de clé.  
  
### <a name="timestampvalidityduration"></a>TimestampValidityDuration  

 Type de données : datetime  
  
 Type d'accès : Lecture seule  
  
 TimeSpan qui spécifie la durée de validité d'un horodatage.  
  
## <a name="requirements"></a>Spécifications  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|-----------------------------------|  
|Espace de noms|Défini dans root\ServiceModel|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
