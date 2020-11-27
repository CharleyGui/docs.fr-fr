---
title: TcpTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 33bbc1e5-44e4-4ee3-b7b5-801dc78956e4
ms.openlocfilehash: 6af85d62fffada95537494692b8694f42d7a2932
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96290086"
---
# <a name="tcptransportbindingelement"></a>TcpTransportBindingElement

TcpTransportBindingElement  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp
class TcpTransportBindingElement : ConnectionOrientedTransportBindingElement  
{  
  TcpConnectionPoolSettings ConnectionPoolSettings;  
  sint32 ListenBacklog;  
  boolean PortSharingEnabled;  
  boolean TeredoEnabled;  
};  
```  
  
## <a name="methods"></a>Méthodes  

 La classe TcpTransportBindingElement ne définit pas de méthode.  
  
## <a name="properties"></a>Propriétés  

 La classe TcpTransportBindingElement a les propriétés suivantes :  
  
### <a name="connectionpoolsettings"></a>ConnectionPoolSettings  

 Type de données : TcpConnectionPoolSettings  
  
 Type d'accès : Lecture seule  
  
 Paramètres de pool de connexions.  
  
### <a name="listenbacklog"></a>ListenBacklog  

 Type de données : sint32  
  
 Type d'accès : Lecture seule  
  
 Nombre maximal de demandes de connexion en file d'attente pouvant être en attente.  
  
### <a name="portsharingenabled"></a>PortSharingEnabled  

 Type de données : booléen  
  
 Type d'accès : Lecture seule  
  
 Valeur booléenne qui spécifie si le partage de port TCP est activé pour cette connexion.  
  
### <a name="teredoenabled"></a>TeredoEnabled  

 Type de données : booléen  
  
 Type d'accès : Lecture seule  
  
 Valeur booléenne qui spécifie si Teredo (technologie d'adressage de clients placés derrière des pare-feu) est activé.  
  
## <a name="requirements"></a>Spécifications  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|-----------------------------------|  
|Espace de noms|Défini dans root\ServiceModel|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Channels.TcpTransportBindingElement>
