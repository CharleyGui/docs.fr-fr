---
title: Channel, classe
ms.date: 03/30/2017
ms.assetid: d9fae2ca-209c-4341-a0f5-6b79d1a67776
ms.openlocfilehash: a920636e7df9609b12834366b1488c80122f9fca
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96274229"
---
# <a name="channel-class"></a>Channel, classe

Channel  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp
class Channel  
{  
  string LocalAddress;  
  Endpoint ref;  
  string RemoteAddress;  
  string SessionId;  
  string Type;  
};  
```  
  
## <a name="methods"></a>Méthodes  

 La classe Channel ne définit aucune méthode.  
  
## <a name="properties"></a>Propriétés  

 La classe Channel possède les propriétés suivantes.  
  
### <a name="localaddress"></a>LocalAddress  

 Type de données : chaîne  
  
 Type d'accès : Lecture seule  
  
 Point de terminaison local du canal.  
  
### <a name="ref"></a>ref  

 Type de données : point de terminaison  
  
 Type d'accès : Lecture seule  
  
 Référence au point de terminaison auquel le canal se connecte.  
  
### <a name="remoteaddress"></a>RemoteAddress  

 Type de données : chaîne  
  
 Type d'accès : Lecture seule  
  
 Adresse distante associée au canal.  
  
### <a name="sessionid"></a>SessionId  

 Type de données : chaîne  
  
 Type d'accès : Lecture seule  
  
 Id de session actuel, le cas échéant.  
  
### <a name="type"></a>Type  

 Type de données : chaîne  
  
 Type d'accès : Lecture seule  
  
 Type du canal.  
  
## <a name="requirements"></a>Spécifications  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|-----------------------------------|  
|Espace de noms|Défini dans root\ServiceModel|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Channels.ChannelBase>
