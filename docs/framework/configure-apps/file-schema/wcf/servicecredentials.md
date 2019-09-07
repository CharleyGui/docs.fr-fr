---
title: <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 96db336c-4f7a-4193-81a5-910b8ffd804f
ms.openlocfilehash: 90a34a4a52b4c7a2e67d733fecba132818cac4fc
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399652"
---
# <a name="servicecredentials"></a>\<serviceCredentials>
Spécifie l'information d'identification à utiliser pour authentifier le service, ainsi que les paramètres liés à la validation des informations d'identification du client.  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportements >** ](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportement**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<serviceCredentials >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<serviceCredentials type="String">
  <clientCertificate>
  </clientCertificate>
  <issuedTokenAuthentication>
  </issuedTokenAuthentication>
  <peer>
  </peer>
  <secureConversationAuthentication>
  </secureConversationAuthentication>
  <serviceCertificate>
  </serviceCertificate>
  <userNameAuthentication>
  </userNameAuthentication>
  <windowsAuthentication>
  </windowsAuthentication>
</serviceCredentials>
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`type`|Chaîne qui spécifie le type de cet élément de configuration.|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<clientCertificate>](clientcertificate-of-servicecredentials.md)|Spécifie le certificat à utiliser lorsque le certificat client est disponible hors bande. Cet élément spécifie également les paramètres de validation du certificat client. Cet élément est de type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>.|  
|[\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md)|Spécifie le jeton émis actuellement pour ce service. Cet élément est de type <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>.|  
|[\<peer>](peer-of-servicecredentials.md)|Spécifie les informations d'identification actuelles d'un nœud homologue. Cet élément est de type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.|  
|[\<secureConversationAuthentication>](secureconversationauthentication-of-servicecredential.md)|Spécifie les informations d'identification actuelles pour une conversation sécurisée. Cet élément est de type <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>.|  
|[\<serviceCertificate>](servicecertificate-of-servicecredentials.md)|Spécifie un certificat utilisé par un service pour s'identifier. Cet élément est de type <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>.|  
|[\<userNameAuthentication>](usernameauthentication.md)|Spécifie les paramètres pour la validation du mot de passe du nom d’utilisateur. Cet élément est de type <xref:System.ServiceModel.Configuration.UserNameServiceElement>.|  
|[\<windowsAuthentication>](windowsauthentication-of-servicecredentials.md)|Spécifie les paramètres de validation des informations d’identification Windows. Cet élément est de type <xref:System.ServiceModel.Configuration.WindowsServiceElement>.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|Spécifie un élément de comportement.|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement>
- <xref:System.ServiceModel.Description.ServiceCredentials>
- [Comportements de sécurité](../../../wcf/feature-details/security-behaviors-in-wcf.md)
