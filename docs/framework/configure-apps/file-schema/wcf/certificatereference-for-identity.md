---
title: <certificateReference> pour <identity>
ms.date: 03/30/2017
ms.assetid: ac359c65-c22d-42d2-97de-db53b77cebdb
ms.openlocfilehash: 49c731b2637c15e0b968d8c2523c51c8e138e7bf
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926170"
---
# <a name="certificatereference-for-identity"></a>\<CertificateReference > pour \<l’identité >
Spécifie les paramètres de validation du certificat X.509. Un client Windows Communication Foundation sécurisé (WCF) qui se connecte à un point de terminaison avec cette identité vérifie que les revendications présentées par le serveur contiennent la revendication d’identité utilisée pour construire cette identité.  
  
 \<identity>  
\<certificateReference>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<certificateReference findValue="String"
                      isChainIncluded="Boolean"
                      storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                      storeLocation="LocalMachine/CurrentUser"
                      X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier">
</certificateReference>
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|findValue|Indique la valeur à rechercher dans le magasin de certificats X.509. Le type contenu dans cet attribut doit répondre aux exigences de la valeur `X509FindType` spécifiée. La valeur par défaut est une chaîne vide.|  
|isChainIncluded|Valeur booléenne indiquant si la validation est effectuée à l’aide d’une chaîne de certificats.|  
|storeLocation|Indique l'emplacement du magasin de certificats pouvant être utilisé par le client pour valider le certificat du serveur.<br /><br /> Les valeurs valides sont les suivantes :<br /><br /> -   LocalMachine: Magasin de certificats affecté à l’ordinateur local.<br />CurrentUser Magasin de certificats attribué à l’utilisateur actuel.<br /><br /> La valeur par défaut est LocalMachine.<br /><br /> Cet attribut est de type <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.|  
|storeName|Spécifie le nom du magasin de certificats X.509 à ouvrir.<br /><br /> Les valeurs valides sont les suivantes :<br /><br /> Carnet Magasin de certificats pour d’autres utilisateurs.<br />-   AuthRoot: Magasin de certificats pour les autorités de certification tierces.<br />CertificateAuthority Magasin de certificats pour les autorités de certification intermédiaires.<br />Interdits Magasin de certificats pour les certificats révoqués.<br />M' Magasin de certificats pour les certificats personnels.<br />Causes Magasin de certificats pour les autorités de certification racines de confiance.<br />TrustedPeople Magasin de certificats pour les personnes et les ressources directement approuvées.<br />TrustedPublisher Magasin de certificats pour les éditeurs directement approuvés.<br /><br /> La valeur par défaut est My.<br /><br /> Cet attribut est de type <xref:System.Security.Cryptography.X509Certificates.StoreName>.|  
|X509FindType|Indique le type de recherche X.509 à exécuter. Le type contenu dans l'attribut `findValue` doit satisfaire les spécifications du X509FindType spécifié.<br /><br /> Les valeurs valides sont les suivantes :<br /><br /> -   FindByThumbPrint<br />-   FindBySubjectName<br />-   FindBySubjectDistinguishedName<br />-   FindByIssuerName<br />-   FindByIssuerDistinguishedName<br />-   FindBySerialNumber<br />-   FindByTimeValid<br />-   FindByTimeNotYetValid<br />-   FindByTemplateName<br />-   FindByApplicationPolicy<br />-   FindByCertificatePolicy<br />-   FindByExtension<br />-   FindByKeyUsage<br />-   FindBySubjectKeyIdentifier<br /><br /> La valeur par défaut est FindBySubjectDistinguishedName.<br /><br /> Cet attribut est de type <xref:System.Security.Cryptography.X509Certificates.X509FindType>.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<identity>](identity.md)|Indique les paramètres permettant l'authentification d'un point de terminaison par les autres points de terminaison qui échangent des messages avec lui.|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Configuration.CertificateReferenceElement>
- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
