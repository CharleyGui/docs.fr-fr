---
title: <issuedTokenAuthentication> de <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 5c2e288f-f603-4d13-839a-0fd6d1981bec
ms.openlocfilehash: 6d468a27ee05fb4dd8cf087d10e5d170783d3454
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400356"
---
# <a name="issuedtokenauthentication-of-servicecredentials"></a>\<issuedTokenAuthentication> de \<serviceCredentials>
Indique un jeton personnalisé émis en tant qu'informations d'identification du service.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuedTokenAuthentication>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<issuedTokenAuthentication allowUntrustedRsaIssuers="Boolean"
                           audienceUriMode="Always/BearerKeyOnly/Never"
                           customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                           certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                           revocationMode="NoCheck/Online/Offline"
                           samlSerializer="String"
                           trustedStoreLocation="CurrentUser/LocalMachine">
  <allowedAudienceUris>
    <add allowedAudienceUri="String" />
  </allowedAudienceUris>
  <knownCertificates>
    <add findValue="String"
         storeLocation="CurrentUser/LocalMachine"
         storeName=" CurrentUser/LocalMachine"
         x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
  </knownCertificates>
</issuedTokenAuthentication>
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`allowedAudienceUris`|Obtient le jeu d'URI cibles pour lesquels le jeton de sécurité <xref:System.IdentityModel.Tokens.SamlSecurityToken> peut être visé pour être considéré comme valide par une instance de <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>. Pour plus d'informations sur l'utilisation de cet attribut, consultez <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>.|  
|`allowUntrustedRsaIssuers`|Valeur booléenne indiquant si les émetteurs de certificats RSA non fiables sont autorisés.<br /><br /> Les certificats sont signés par des autorités de certification (CA) pour en assurer l'authenticité. Un émetteur non fiable est une autorité de certification qui n'est pas spécifiée comme étant approuvée pour signer des certificats.|  
|`audienceUriMode`|Obtient une valeur indiquant si le <xref:System.IdentityModel.Tokens.SamlSecurityToken> du jeton de sécurité <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> doit être validé. Cette valeur est de type <xref:System.IdentityModel.Selectors.AudienceUriMode>. Pour plus d'informations sur l'utilisation de cet attribut, consultez <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>.|  
|`certificateValidationMode`|Définit le mode de validation du certificat. L'une des valeurs valides du <xref:System.ServiceModel.Security.X509CertificateValidationMode>. S'il est défini à `Custom`, un `customCertificateValidator` doit également être fourni. Par défaut, il s’agit de `ChainTrust`.|  
|`customCertificateValidatorType`|Chaîne facultative. Type et assembly utilisés pour valider un type personnalisé. Cet attribut doit être défini lorsque `certificateValidationMode` a la valeur `Custom`.|  
|`revocationMode`|Définit le mode de révocation qui spécifie si un contrôle de révocation a lieu et s'il est effectué en ligne ou hors connexion. Cet attribut est de type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.|  
|`samlSerializer`|Attribut de chaîne facultatif indiquant le type de SamlSerializer utilisé pour les informations d'identification du service. La valeur par défaut est une chaîne vide.|  
|`trustedStoreLocation`|Énumération facultative. L'un des deux emplacements du magasin du système : `LocalMachine` ou `CurrentUser`.|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|`knownCertificates`|Indique une collection d’éléments <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement> qui spécifient des émetteurs approuvés au niveau des informations d’identification du service.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|Spécifie les informations d’identification à utiliser pour authentifier le service, ainsi que les paramètres liés à la validation des informations d’identification du client.|  
  
## <a name="remarks"></a>Remarques  
 Le scénario de jeton émis comporte trois étapes. Lors de la première phase, un client qui tente d’accéder à un service est appelé *service de jeton sécurisé*. Le service d'émission de jeton sécurisé authentifie ensuite le client et émet par la suite un jeton au client, généralement un jeton SAML (Security Assertions Markup Language). Le client retourne ensuite au service avec le jeton. Le service recherche dans le jeton les données lui permettant de l'authentifier, et par conséquent d'authentifier le client. Pour authentifier le jeton, le service doit connaître le certificat utilisé par le service d'émission de jeton sécurisé.  
  
 Cet élément est le référentiel pour les certificats de service d'émission de jeton sécurisé de ce type. Pour ajouter des certificats, utilisez le [\<knownCertificates>](knowncertificates.md) . Insérez un [\<add>](add-of-knowncertificates.md) pour chaque certificat, comme indiqué dans l’exemple suivant.  
  
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
  
 Pour plus d’informations sur l’utilisation de cet élément de configuration, consultez [Comment : configurer des informations d’identification sur un service FS (Federation Service)](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.IssuedTokenAuthentication%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>
- <xref:System.ServiceModel.Description.ServiceCredentials.IssuedTokenAuthentication%2A>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential>
- [Securing Services and Clients](../../../wcf/feature-details/securing-services-and-clients.md)
- [Comment : configurer des informations d'identification sur un service FS (Federation Service)](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
