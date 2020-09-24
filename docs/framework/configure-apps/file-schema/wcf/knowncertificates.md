---
title: <knownCertificates>
ms.date: 03/30/2017
ms.assetid: 678e21b4-6493-47c3-8359-fcf0d37e2138
ms.openlocfilehash: 7ddb292b8f0ffe38133c7f142be751a87d2be11c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91150906"
---
# \<knownCertificates>

Représente une collection des certificats X.509 fournis pour authentifier des informations d’identification de sécurité publiées à partir d’un service d’émission de jetons de sécurité (STS).  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenAuthentication>**](issuedtokenauthentication-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<knownCertificates>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<knownCertificates>
  <add findValue="String"
       storeLocation="CurrentUser/LocalMachine"
       storeName=" CurrentUser/LocalMachine"
       x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
</knownCertificates>
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  

 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  

 Aucun.  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<add>](add-of-knowncertificates.md)|Ajoute un certificat X.509 à la collection.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md)|Spécifie un jeton émis en guise d'information d'identification du service.|  
  
## <a name="remarks"></a>Notes  

 Le scénario de jeton émis comporte trois étapes. Lors de la première phase, un client qui tente d’accéder à un service est appelé *service de jeton sécurisé*. Le service d'émission de jeton sécurisé authentifie ensuite le client et émet par la suite un jeton au client, généralement un jeton SAML (Security Assertions Markup Language). Le client retourne ensuite au service avec le jeton. Le service recherche dans le jeton les données lui permettant de l'authentifier, et par conséquent d'authentifier le client. Pour authentifier le jeton, le service doit connaître le certificat utilisé par le service d'émission de jeton sécurisé.  
  
 L' [\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md) élément est le référentiel de tels certificats de service de jeton sécurisé. Pour ajouter des certificats, utilisez l' [ \<knownCertificates> élément](knowncertificates.md). Insérez un [\<add>](add-of-knowncertificates.md) pour chaque certificat, comme indiqué dans l’exemple suivant.  
  
```xml  
<issuedTokenAuthentication>
  <knownCertificates>
    <add findValue="www.contoso.com"
         storeLocation="LocalMachine"
         storeName="My"
         X509FindType="FindBySubjectName" />
  </knownCertificates>
</issuedTokenAuthentication>
```  
  
 Par défaut, les certificats doivent être obtenus auprès d'un service d'émission de jeton sécurisé. Ces certificats « connus » garantissent que seuls les clients légitimes peuvent accéder à un service.  
  
 Pour passer en revue les conditions requises pour qu’un client soit authentifié par un service fédéré, et pour plus d’informations sur l’utilisation de cet élément de configuration, consultez [Comment : configurer des informations d’identification sur un service FS (Federation Service)](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md). Pour plus d’informations sur les scénarios fédérés, consultez [Fédération et jetons émis](../../../wcf/feature-details/federation-and-issued-tokens.md).  
  
 Pour obtenir un exemple qui montre comment remplir la collection dans la configuration, consultez [\<add>](add-of-knowncertificates.md) .  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.KnownCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElementCollection>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A>
- [\<add>](add-of-knowncertificates.md)
- [\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md)
- [Comportements de sécurité](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [Procédure : configurer des informations d’identification sur un service de fédération](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [Utilisation des certificats](../../../wcf/feature-details/working-with-certificates.md)
- [Fédération et jetons émis](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [\<add>](add-of-knowncertificates.md)
- [Sécurisation des services et des clients](../../../wcf/feature-details/securing-services-and-clients.md)
