---
title: <security> de <basicHttpBinding>
ms.date: 03/30/2017
ms.assetid: 6432708d-5465-4bd9-bfc2-466742db99cb
ms.openlocfilehash: c8e4f2d000a155eecd2a6c7faaaf4af525b24ca3
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738716"
---
# <a name="security-of-basichttpbinding"></a>\<> de sécurité de \<basicHttpBinding >
Définit les fonctionnalités de sécurité de la [\<basicHttpBinding >](basichttpbinding.md).  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) \
&nbsp;&nbsp;&nbsp;&nbsp;[**liaisons**](bindings.md)\<
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<basicHttpBinding >** ](basichttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\< **\**
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **&nbsp;&nbsp;\<** >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<security mode="Message/None/Transport/TransportWithCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
             realm="string" />
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />
</security>
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|mode|Optionnel. Spécifie le type de sécurité qui est utilisé. La valeur par défaut est `None`, Cet attribut est de type <xref:System.ServiceModel.BasicHttpSecurityMode>.|  
  
## <a name="mode-attribute"></a>Attribut Mode  
  
|valeur|Description|  
|-----------|-----------------|  
|aucune.|-Les messages ne sont pas sécurisés lors du transfert.|  
|Transport|La sécurité est fournie à l'aide du transport HTTPS. Les messages SOAP sont sécurisés par HTTPS. Le service est authentifié auprès du client à l'aide du certificat X.509 du service. Le client est authentifié à l'aide du ClientCredentialType fourni. Consultez la [> de transport\<](transport-of-basichttpbinding.md).|  
|Message|La sécurité est fournie à l'aide de la sécurité des messages SOAP. Par défaut, le corps est chiffré et signé. Pour cette liaison, le système impose que le certificat de serveur soit fourni au client hors bande. Le seul `ClientCredentialType` valide pour cette liaison est `Certificate`.|  
|TransportWithMessageCredential|L'intégrité, la confidentialité et l'authentification de serveur sont fournies par la sécurité du transport. L'authentification du client est fournie au moyen de la sécurité des messages SOAP. Ce mode est utile lorsque l'utilisateur effectue une authentification à l'aide du nom d'utilisateur/mot de passe et qu'il existe un déploiement HTTP pour sécuriser le transfert des messages.|  
|TransportCredentialOnly|Ce mode n'assure pas l'intégrité et la confidentialité des messages. Il fournit l'authentification du client basée sur http. Ce mode doit être utilisé avec précaution. Elle doit être utilisée dans les environnements où la sécurité de transport est fournie par d’autres moyens (par exemple, IPSec) et que seule l’authentification du client est fournie par l’infrastructure WCF.|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[> de transport \<](transport-of-basichttpbinding.md)|Définit les paramètres de sécurité de transport pour un service HTTP de base. Cet élément correspond à <xref:System.ServiceModel.HttpTransportSecurity>.|  
|[message de \<](message-of-basichttpbinding.md)|Définit les paramètres de sécurité de message pour un service HTTP de base. Cet élément correspond à <xref:System.ServiceModel.BasicHttpMessageSecurity>.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|liaison|Élément de liaison de la [\<basicHttpBinding >](basichttpbinding.md).|  
  
## <a name="remarks"></a>Notes  
 Par défaut, le message SOAP n'est pas sécurisé et le client n'est pas authentifié. Cet élément permet de configurer des paramètres de sécurité supplémentaires pour l'élément `basicHttpBinding`.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.BasicHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [Sécurisation des services et des clients](../../../wcf/feature-details/securing-services-and-clients.md)
- [Sélection d’un type d’informations d’identification](../../../wcf/feature-details/selecting-a-credential-type.md)
- [Liaisons](../../../wcf/bindings.md)
- [Configuration des liaisons fournies par le système](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Utilisation de liaisons pour configurer des services et des clients](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [liaison de \<](bindings.md)
