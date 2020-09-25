---
title: <certificateReference>
ms.date: 03/30/2017
ms.assetid: 2ac8bc14-e9f1-48fb-b662-f5991558fbe4
author: BrucePerlerMS
ms.openlocfilehash: c21e5186b8afdf8c72cbfc605af94c95bc2bc0d5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201373"
---
# \<certificateReference>

Spécifie les paramètres utilisés pour rechercher et valider un certificat X. 509 dans un magasin de certificats.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificateReference>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <serviceCertificate>  
      <certificateReference
        storeName="AddressBook||AuthRoot||CertificateAuthority||Disallowed||My||Root||TrustedPeople||TrustedPublisher"  
        storeLocation="CurrentUser||LocalMachine"  
        x509FindType="FindByThumbprint||FindBySubjectName||FindBySubjectDistinguishedName||FindByIssuerName||FindByIssuerDistinguishedName||FindBySerialNumber||FindByTimeValid||FindByTimeNotYetValid||FindByTimeExpired||FindByTemplateName||FindByApplicationPolicy||FindByCertificatePolicy||FindByExtension||FindByKeyUsage||FindBySubjectKeyIdentifier"  
        findValue=xs:String  
        isChainIncluded=xs:Boolean >  
      </certificateReference>  
    </serviceCertificate>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  

 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|storeName|Nom du magasin de certificats X.509. La valeur par défaut est « My ». Optionnel.|  
|storeLocation|<xref:System.Security.Cryptography.X509Certificates.StoreLocation>Valeur qui spécifie l’emplacement du magasin de certificats X. 509. La valeur par défaut est « LocalMachine ». Optionnel.|  
|x509FindType|<xref:System.Security.Cryptography.X509Certificates.X509FindType>Valeur qui spécifie le type de recherche à exécuter. La valeur par défaut est « FindBySubjectDistinguishedName ». Optionnel.|  
|findValue|Valeur à rechercher dans le magasin de certificats X.509. Optionnel.|  
|isChainIncluded|Spécifie si la validation doit être effectuée à l’aide de la chaîne de certificats. La valeur par défaut est « true ». la validation est effectuée à l’aide de la chaîne de certificats. Optionnel.|  
  
### <a name="child-elements"></a>Éléments enfants  

 None  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<serviceCertificate>](servicecertificate.md)|Configure le certificat utilisé pour chiffrer et déchiffrer les jetons.|  
  
## <a name="remarks"></a>Notes  

 L' `<certificateReference>` élément spécifie les paramètres utilisés pour rechercher et valider un certificat X. 509 dans un magasin de certificats. Lorsqu’il est spécifié en tant qu’élément enfant de l' `<serviceCertificate>` élément, il spécifie l’emplacement et les paramètres de vérification du certificat X. 509 utilisé pour chiffrer et déchiffrer les jetons. L' `<certificateReference>` élément est représenté par la <xref:System.ServiceModel.Configuration.CertificateReferenceElement> classe.
