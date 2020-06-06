---
title: <allowedAudienceUris>
ms.date: 03/30/2017
ms.assetid: 0f4dc73d-d95d-4193-9755-7df4cf2b8e1c
ms.openlocfilehash: ea2d4bb285047939992e9b191abc2dc896bdaa6a
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398275"
---
# \<allowedAudienceUris>
Représente une collection d’URI cibles pour lesquels le jeton de sécurité <xref:System.IdentityModel.Tokens.SamlSecurityToken> peut être visé pour être considéré comme valide par une instance de <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenAuthentication>**](issuedtokenauthentication-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<allowedAudienceUris>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<allowedAudienceUris>
  <add allowedAudienceUri="String" />
</allowedAudienceUris>
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
 Aucun.  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<add>](add-of-allowedaudienceuris.md)|Ajoute un URI cible pour lequel le jeton de sécurité <xref:System.IdentityModel.Tokens.SamlSecurityToken> peut être visé pour être considéré comme valide par une instance de <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md)|Spécifie un jeton émis en guise d'information d'identification du service.|  
  
## <a name="remarks"></a>Remarques  
 Vous devez utiliser cette collection dans une application fédérée qui utilise un service de jeton de sécurité (STS) qui émet des jetons de sécurité <xref:System.IdentityModel.Tokens.SamlSecurityToken>. Lorsque le STS émet le jeton de sécurité, il peut spécifier l'URI des services Web pour lesquels le jeton de sécurité est prévu en ajoutant un <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> au jeton de sécurité. Cela permet au <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> du service Web destinataire de vérifier que le jeton de sécurité émis est prévu pour ce service Web en spécifiant que ce contrôle doit arriver en effectuant les opérations suivantes :  
  
- Affectez à l'attribut `audienceUriMode` de `<issuedTokenAuthentication>` la valeur <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> ou <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>.  
  
- Spécifiez le jeu d'URI valides en ajoutant les URI à cette collection.  
  
 Pour plus d’informations, consultez <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.  
  
 Pour plus d’informations sur l’utilisation de cet élément de configuration, consultez [Comment : configurer des informations d’identification sur un service FS (Federation Service)](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.AllowedAudienceUris%2A>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElementCollection>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowedAudienceUris%2A>
- [\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md)
- [\<add>](add-of-allowedaudienceuris.md)
- [Comportements de sécurité](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [Securing Services and Clients](../../../wcf/feature-details/securing-services-and-clients.md)
- [Comment : configurer des informations d'identification sur un service FS (Federation Service)](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
