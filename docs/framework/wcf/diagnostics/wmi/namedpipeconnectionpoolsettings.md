---
title: NamedPipeConnectionPoolSettings
ms.date: 03/30/2017
ms.assetid: 079bccb8-54b5-4436-a43d-5567763f72ce
ms.openlocfilehash: 8422e1adf9a8914b631431eba5c9c0ed058cd0f3
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96258021"
---
# <a name="namedpipeconnectionpoolsettings"></a>NamedPipeConnectionPoolSettings

NamedPipeConnectionPoolSettings  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp
class NamedPipeConnectionPoolSettings  
{  
  string GroupName;  
  datetime IdleTimeout;  
  sint32 MaxOutboundConnectionsPerEndpoint;  
};  
```  
  
## <a name="methods"></a>Méthodes  

 La classe NamedPipeConnectionPoolSettings ne définit pas de méthodes.  
  
## <a name="properties"></a>Propriétés  

 La classe NamedPipeConnectionPoolSettings a les propriétés suivantes :  
  
### <a name="groupname"></a>GroupName  

 Type de données : chaîne  
  
 Type d'accès : Lecture seule  
  
 Nom de groupe du pool de connexions utilisé par l'élément de liaison.  
  
### <a name="idletimeout"></a>IdleTimeout  

 Type de données : datetime  
  
 Type d'accès : Lecture seule  
  
 Période maximale d'inactivité de la connexion au terme de laquelle la connexion est coupée.  
  
### <a name="maxoutboundconnectionsperendpoint"></a>MaxOutboundConnectionsPerEndpoint  

 Type de données : sint32  
  
 Type d'accès : Lecture seule  
  
 Nombre maximal de connexions sortantes pour chaque point de terminaison sur le client.  
  
## <a name="requirements"></a>Spécifications  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|-----------------------------------|  
|Espace de noms|Défini dans root\ServiceModel|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>
