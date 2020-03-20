---
title: <certificateReference>
ms.date: 03/30/2017
ms.assetid: 2ac8bc14-e9f1-48fb-b662-f5991558fbe4
author: BrucePerlerMS
ms.openlocfilehash: 47d432a84d070476ddffd9b98a4ba46d8163bdc3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152812"
---
# <a name="certificatereference"></a>\<certificatReference>
Spécifie les paramètres qui sont utilisés pour trouver et valider un certificat X.509 dans un magasin de certificats.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<fédérationConfiguration>**](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificatReference>**  
  
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
|storeName|Nom du magasin de certificats X.509. La valeur par défaut est "My". facultatif.|  
|storeLocation|Une <xref:System.Security.Cryptography.X509Certificates.StoreLocation> valeur qui précise l’emplacement du magasin de certificats X.509. La valeur par défaut est "LocalMachine". facultatif.|  
|x509FindType|Une <xref:System.Security.Cryptography.X509Certificates.X509FindType> valeur qui spécifie le type de recherche qui doit être exécutée. La valeur par défaut est "FindBySubjectDistinguishedName". facultatif.|  
|findValue|Valeur à rechercher dans le magasin de certificats X.509. facultatif.|  
|isChainIncluded|Précise si la validation doit être effectuée à l’aide de la chaîne de certificats. La valeur par défaut est "vraie"; validation est effectuée à l’aide de la chaîne de certificats. facultatif.|  
  
### <a name="child-elements"></a>Éléments enfants  
 None  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<serviceCertificate>](servicecertificate.md)|Configure le certificat utilisé pour chiffrer et déchiffrer les jetons.|  
  
## <a name="remarks"></a>Notes   
 L’élément `<certificateReference>` spécifie les paramètres qui sont utilisés pour trouver et valider un certificat X.509 dans un magasin de certificats. Lorsqu’il est spécifié comme `<serviceCertificate>` l’élément enfant de l’élément, il spécifie les paramètres de localisation et de vérification du certificat X.509 qui est utilisé pour chiffrer et déchiffrer les jetons. L’élément `<certificateReference>` est représenté <xref:System.ServiceModel.Configuration.CertificateReferenceElement> par la classe.
