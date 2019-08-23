---
title: <security> de <netPeerBinding>
ms.date: 03/30/2017
ms.assetid: 1ef40d8c-f903-4426-9b08-da81462766d8
ms.openlocfilehash: be5ebacec466caf8d8a77bf552f42da1861e77a1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936624"
---
# <a name="security-of-netpeerbinding"></a>\<> de sécurité \<de netPeerBinding >
Définit les paramètres de sécurité de l' [ \<> NetPeerTcpBinding](netpeertcpbinding.md), y compris le type d’authentification utilisé et la sécurité utilisée pour le transport des messages.  
  
 \<system.ServiceModel>  
\<bindings>  
\<netPeerBinding>  
\<binding>  
\<> de sécurité  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<netPeerBinding>
  <binding>
    <security mode="Message/None/Transport//TransportWithMessageCredential">
      <transport credentialType="Certificate/Password" />
    </security>
  </binding>
</netPeerBinding>
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|mode|facultatif. Spécifie le type de sécurité utilisé par les homologues configurés avec cette liaison. La valeur par défaut est `Message`. Cet attribut est de type <xref:System.ServiceModel.SecurityMode>.|  
  
## <a name="mode-attribute"></a>Attribut Mode  
  
|Valeur|Description|  
|-----------|-----------------|  
|Message|La sécurité SOAP assure l'authentification, l'intégrité et la confidentialité.|  
|Aucun|La sécurité est désactivée.|  
|Transport|La sécurité est fournie à l'aide de HTTPS.|  
|TransportWithMessageCredential|Le protocole HTTPS assure l'authentification et la confidentialité. Les messages SOAP fournissent des types d'informations d'identification enrichies.|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<transport>](transport-of-netpeertcpbinding.md)|Définit le type de transport pour les messages sécurisés envoyés par des homologues configurés avec cette liaison. Cet élément est de type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<binding>](../../../misc/binding.md)|Définit toutes les fonctions de liaison de l' [ \<> NetPeerTcpBinding](netpeertcpbinding.md).|  
  
## <a name="remarks"></a>Notes  
 La sécurité peut être spécifique au message ou au transport.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Configuration.PeerSecurityElement>
- <xref:System.ServiceModel.NetPeerTcpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Security%2A>
- <xref:System.ServiceModel.PeerSecuritySettings>
- [Sécurisation des services et des clients](../../../wcf/feature-details/securing-services-and-clients.md)
- [Sélection d’un type d’informations d’identification](../../../wcf/feature-details/selecting-a-credential-type.md)
- [Liaisons](../../../wcf/bindings.md)
- [Configuration des liaisons fournies par le système](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Utilisation de liaisons pour configurer des services et des clients](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](../../../misc/binding.md)
