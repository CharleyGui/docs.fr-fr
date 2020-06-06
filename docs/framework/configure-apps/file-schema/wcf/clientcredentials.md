---
title: <clientCredentials>
ms.date: 03/30/2017
ms.assetid: 1e6eef0d-a34e-4d74-b0f7-f65d2181858d
ms.openlocfilehash: f295fe48e194611c80b78c0c23ab3e66ea1c0b64
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400495"
---
# \<clientCredentials>
Indique les informations d'identification utilisées pour authentifier le client auprès d'un service.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clientCredentials>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<clientCredentials type="String"
                   supportInteractive="Boolean" >
  <clientCertificate>
  </clientCertificate>
  <digest>
  </digest>
  <isuedToken>
  </isuedToken>
  <peer>
  </peer>
  <serviceCertificate>
  </serviceCertificate>
  <windowsAuthentication>
  </windowsAuthentication>
</clientCredentials>
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`supportInteractive`|Valeur booléenne indiquant si un utilisateur interactif peut sélectionner les informations d'identification d'un client pendant l'exécution. La valeur par défaut est `true`.|  
|`type`|Chaîne qui spécifie le type de cet élément de configuration.|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<clientCertificate>](clientcertificate-of-clientcredentials-element.md)|Indique le certificat utilisé pour authentifier le client auprès du service. Cet élément est de type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateClientElement>.|  
|[\<httpDigest>](httpdigest-element.md)|Indique un condensat utilisé pour authentifier le client auprès du service. Cet élément est de type <xref:System.ServiceModel.Configuration.HttpDigestClientElement>.|  
|[\<issuedToken>](issuedtoken.md)|Spécifie un type de jeton personnalisé utilisé pour authentifier le client à un service STS. Cet élément est de type <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>.|  
|[\<peer>](peer-of-clientcredentials-element.md)|Spécifie des informations d'identification d'homologue actuelles. Cet élément est de type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.|  
|[\<serviceCertificate>](servicecertificate-of-clientcredentials-element.md)|Spécifie le certificat utilisé pour authentifier le service auprès du client et fournit une structure permettant de définir des options de certificat. Ce certificat doit être fourni au client hors bande, à partir du service. Cet élément est de type <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>.|  
|[\<windows>](windows-of-clientcredentials-element.md)|Indique des informations d'identification Windows. La valeur par défaut correspond aux informations d'identification du thread actuel. Cet élément est de type <xref:System.ServiceModel.Configuration.WindowsClientElement>.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|Spécifie un comportement de point de terminaison.|  
  
## <a name="remarks"></a>Remarques  
 Les informations d'identification du client permettent d'authentifier le client auprès des services dans les cas où l'authentification mutuelle est requise. Cette section de configuration peut également servir à spécifier des certificats de service pour les scénarios dans lesquels le client doit sécuriser des messages auprès d'un service à l'aide du certificat de ce dernier.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- [Comportements de sécurité](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [Sécurisation des clients](../../../wcf/securing-clients.md)
