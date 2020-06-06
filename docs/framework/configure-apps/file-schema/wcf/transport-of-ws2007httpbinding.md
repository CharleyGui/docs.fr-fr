---
title: <transport> de <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: 692befa3-8b0b-4ec5-b601-755874e98eb0
ms.openlocfilehash: 0cd20c607b0c4ddd3ecfd806d38ba63b4a5c5a25
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73732764"
---
# <a name="transport-of-ws2007httpbinding"></a>\<transport> de \<ws2007HttpBinding>
Définit les paramètres d'authentification correspondant au transport HTTP.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ws2007HttpBinding>**](ws2007httpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-ws2007httpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
           proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
           realm="string" />
```  
  
## <a name="type"></a>Type  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`clientCredentialType`|Spécifie les informations d'identification utilisées pour authentifier le client auprès du service. Cet attribut est de type <xref:System.ServiceModel.HttpClientCredentialType>.|  
|`proxyCredentialType`|Spécifie les informations d'identification utilisées pour authentifier le client auprès d'un proxy de domaine. Cet attribut est de type <xref:System.ServiceModel.HttpProxyCredentialType>.|  
|`realm`|Domaine d’authentification correspondant à l’authentification de base ou Digest. La valeur par défaut est une chaîne vide.<br /><br /> Un domaine d'authentification spécifie au moins le nom de l'hôte qui exécute l'authentification. Il peut également spécifier une collection d’utilisateurs disposant d’un accès. Un utilisateur peut interroger le domaine d'authentification afin de déterminer les noms d'utilisateur et les mots de passe pouvant être utilisés.|  
  
## <a name="clientcredentialtype-attribute"></a>Attribut clientCredentialType  
  
|Valeur|Description|  
|-----------|-----------------|  
|None|La sécurité est désactivée.|  
|De base|Utilise l'authentification de base.|  
|Digest|Utilise l’authentification Digest.|  
|Ntlm|Utilise l'authentification NTLM comme solution de secours dans un domaine Windows.|  
|Windows|Utilise l'authentification intégrée Windows.|  
|Certificat|Utilise des certificats X.509 pour authentifier le client.|  
  
## <a name="proxycredentialtype-attribute"></a>Attribut proxyCredentialType  
  
|Valeur|Description|  
|-----------|-----------------|  
|None|La sécurité est désactivée.|  
|De base|Utilise l'authentification de base.|  
|Digest|Utilise l’authentification Digest.|  
|Ntlm|Utilise l'authentification NTLM comme solution de secours dans un domaine Windows.|  
|Windows|Utilise l'authentification intégrée Windows.|  
|Certificat|Utilise des certificats X.509 pour authentifier le client.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucune  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<security>](security-of-ws2007httpbinding.md)|Représente les fonctionnalités de sécurité de l' [\<ws2007HttpBinding>](ws2007httpbinding.md) élément.|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.WSHttpTransportSecurityElement>
- [Securing Services and Clients](../../../wcf/feature-details/securing-services-and-clients.md)
- [Liaisons](../../../wcf/bindings.md)
- [Configuration des liaisons fournies par le système](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Utilisation de liaisons pour configurer des services et des clients](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
