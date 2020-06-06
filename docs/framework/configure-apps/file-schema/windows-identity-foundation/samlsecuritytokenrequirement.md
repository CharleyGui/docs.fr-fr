---
title: <samlSecurityTokenRequirement>
ms.date: 03/30/2017
ms.assetid: 09202d12-88d3-49cc-953b-703bcc1690eb
author: BrucePerlerMS
ms.openlocfilehash: b27f337189a7d0b66ffd38e032b5eb864e5094a1
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152630"
---
# \<samlSecurityTokenRequirement>
Fournit la configuration pour la <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> classe, la <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> classe ou une classe dérivée de l’une de ces classes. Représenté par la <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> classe.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<samlSecurityTokenRequirement>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add>  
        <samlSecurityTokenRequirement
            issuerCertificateValidationMode="None||ChainTrust||PeerTrust||PeerOrChainTrust||Custom"  
            issuerCertificateRevocationMode="NoCheck||Offline||Online"  
            issuerCertificateTrustedStoreLocation="CurrentLocation||LocalMachine"  
            issuerCertificateValidator="Namespace.Class Assembly"  
            mapToWindows=xs:boolean  
          <nameClaimType value=xs:string />  
          <roleClaimType value=xs:string />  
        </samlSecurityTokenRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|mapToWindows|Spécifie si le gestionnaire de jetons doit mapper le jeton de validation à un compte Windows à l’aide de la revendication UPN entrante. La valeur par défaut est « false ».|  
|issuerCertificateRevocationMode|<xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>Valeur qui spécifie le mode de révocation à utiliser pour le certificat X. 509. La valeur par défaut est « online ».|  
|issuerCertificateValidationMode|<xref:System.ServiceModel.Security.X509CertificateValidationMode>Valeur qui spécifie le mode de validation à utiliser pour le certificat X. 509. La valeur par défaut est « PeerOrChainTrust ».|  
|issuerCertificateTrustedStoreLocation|<xref:System.Security.Cryptography.X509Certificates.StoreLocation>Valeur qui spécifie le magasin de certificats X. 509. La valeur par défaut est « LocalMachine ».|  
|issuerCertificateValidator|Type personnalisé qui dérive de <xref:System.IdentityModel.Selectors.X509CertificateValidator> . Si l' `issuerCertificateValidationMode` attribut est « Custom », une instance de ce type est utilisée pour la validation du certificat de l’émetteur.|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<nameClaimType>](nameclaimtype.md)|Définit le type de revendication qui spécifie la <xref:System.Security.Principal.IIdentity.Name%2A> propriété.|  
|[\<roleClaimType>](roleclaimtype.md)|Spécifie le type de revendication qui définit les revendications de type de rôle dans la collection d' <xref:System.Security.Claims.ClaimsIdentity> objets retournée par la <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> méthode du gestionnaire de jetons.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<add>](add.md)|Ajoute le gestionnaire de jetons de sécurité spécifié à la collection de gestionnaires de jetons.|  
  
## <a name="remarks"></a>Remarques  
 L' `<samlSecurityTokenRequirement>` élément est représenté par la <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> classe dans le modèle objet et est utilisé pour configurer la `SamlSecurityTokenRequirement` propriété sur un <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> ou un <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> .  
  
## <a name="example"></a>Exemple  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement issuerCertificateValidationMode="PeerOrChainTrust"  
                                  issuerCertificateRevocationMode="Online"  
                                  issuerCertificateTrustedStoreLocation="LocalMachine"  
                                  mapToWindows="false">  
  
        <nameClaimType value="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name" />  
        <roleClaimType value="schemas.microsoft.com/ws/2006/04/identity/claims/role" />  
    </samlSecurityTokenRequirement>  
</add>  
```
