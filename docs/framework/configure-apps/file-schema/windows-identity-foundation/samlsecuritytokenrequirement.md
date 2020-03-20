---
title: <samlSecurityTokenRequirement>
ms.date: 03/30/2017
ms.assetid: 09202d12-88d3-49cc-953b-703bcc1690eb
author: BrucePerlerMS
ms.openlocfilehash: b27f337189a7d0b66ffd38e032b5eb864e5094a1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152630"
---
# <a name="samlsecuritytokenrequirement"></a>\<samlSecurityTokenRequirement>
Fournit la <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> configuration pour <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> la classe, la classe, ou une classe dérivée de l’une ou l’autre de ces classes. Représenté par <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> la classe.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identitéConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<sécuritéTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ajouter>**](add.md)\
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
|mapToWindows|Précise si le gestionnaire de jetons doit cartographier le jeton valide à un compte Windows en utilisant la réclamation UPN entrante. La valeur par défaut est « false ».|  
|issuerCertificateRevocationMode|Une <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> valeur qui spécifie le mode de révocation à utiliser pour le certificat X.509. La valeur par défaut est "En ligne".|  
|issuerCertificateValidationMode|Une <xref:System.ServiceModel.Security.X509CertificateValidationMode> valeur qui spécifie le mode de validation à utiliser pour le certificat X.509. La valeur par défaut est "PeerOrChainTrust".|  
|issuerCertificateTrustedStoreLocation|Une <xref:System.Security.Cryptography.X509Certificates.StoreLocation> valeur qui spécifie le magasin de certificats X.509. La valeur par défaut est "LocalMachine".|  
|émetteurCertificateValidator|Un type personnalisé qui <xref:System.IdentityModel.Selectors.X509CertificateValidator>dérive de . Si `issuerCertificateValidationMode` l’attribut est "Custom", une instance de ce type est utilisée pour la validation des certificats d’émetteur.|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<nomClaimType>](nameclaimtype.md)|Définit le type de réclamation <xref:System.Security.Principal.IIdentity.Name%2A> qui spécifie la propriété.|  
|[\<rôleClaimType>](roleclaimtype.md)|Spécifie le type de réclamation qui définit <xref:System.Security.Claims.ClaimsIdentity> les revendications de type de rôle dans la collection d’objets retournés par la <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> méthode du gestionnaire de jetons.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<ajouter>](add.md)|Ajoute le gestionnaire de jetons de sécurité spécifié à la collection de gestionnaires de jetons.|  
  
## <a name="remarks"></a>Notes   
 `<samlSecurityTokenRequirement>` L’élément est représenté <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> par la classe dans le `SamlSecurityTokenRequirement` modèle d’objet et est utilisé pour configurer la propriété sur un <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> ou un <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>.  
  
## <a name="example"></a> Exemple  
  
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
