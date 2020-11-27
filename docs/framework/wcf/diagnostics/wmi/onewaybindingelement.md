---
title: OneWayBindingElement
ms.date: 03/30/2017
ms.assetid: 5c7e17c3-39b9-4214-ae08-9e6141734305
ms.openlocfilehash: 806066a8845068413d2a52c78878f76b5f5fa34f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96250370"
---
# <a name="onewaybindingelement"></a>OneWayBindingElement

OneWayBindingElement  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp
class OneWayBindingElement : BindingElement  
{  
  ChannelPoolSettings ChannelPoolSettings;  
  sint32 MaxAcceptedChannels;  
  boolean PacketRoutable;  
};  
```  
  
## <a name="methods"></a>Méthodes  

 La classe OneWayBindingElement ne définit pas de méthode.  
  
## <a name="properties"></a>Propriétés  

 La classe OneWayBindingElement a les propriétés suivantes :  
  
### <a name="channelpoolsettings"></a>ChannelPoolSettings  

 Type de données : ChannelPoolSettings  
  
 Type d'accès : Lecture seule  
  
 Paramètres du pool de canaux.  
  
### <a name="maxacceptedchannels"></a>MaxAcceptedChannels  

 Type de données : sint32  
  
 Type d'accès : Lecture seule  
  
 Nombre maximal de canaux acceptés.  
  
### <a name="packetroutable"></a>PacketRoutable  

 Type de données : booléen  
  
 Type d'accès : Lecture seule  
  
 Valeur qui indique si le paquet peut être routé.  
  
## <a name="requirements"></a>Spécifications  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|-----------------------------------|  
|Espace de noms|Défini dans root\ServiceModel|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Channels.OneWayBindingElement>
