---
title: PeerTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 40bf6be2-8087-4cb3-a66c-408d53eb9269
ms.openlocfilehash: ae6a3448896cb206bce8867daf7104c3e484ecc8
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96269013"
---
# <a name="peertransportbindingelement"></a>PeerTransportBindingElement

PeerTransportBindingElement  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp
class PeerTransportBindingElement : TransportBindingElement  
{  
  string ListenIPAddress;  
  sint32 Port;  
  PeerSecuritySettings Security;  
};  
```  
  
## <a name="methods"></a>Méthodes  

 La classe PeerTransportBindingElement ne définit pas de méthode.  
  
## <a name="properties"></a>Propriétés  

 La classe PeerTransportBindingElement a les propriétés suivantes :  
  
### <a name="listenipaddress"></a>ListenIPAddress  

 Type de données : chaîne  
  
 Type d'accès : Lecture seule  
  
 Adresse IP sur laquelle le nœud homologue écoute les messages.  
  
### <a name="port"></a>Port  

 Type de données : sint32  
  
 Type d'accès : Lecture seule  
  
 Port d’interface de réseau sur lequel la liaison traite les messages de canaux homologues.  
  
### <a name="security"></a>Sécurité  

 Type de données : PeerSecuritySettings  
  
 Type d'accès : Lecture seule  
  
 Paramètres de sécurité de transport de l'homologue.  
  
## <a name="requirements"></a>Spécifications  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|-----------------------------------|  
|Espace de noms|Défini dans root\ServiceModel|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Channels.PeerTransportBindingElement>
