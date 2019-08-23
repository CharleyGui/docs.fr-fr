---
title: Élément <defaultCertificate>
ms.date: 03/30/2017
ms.assetid: f1ddf364-9a00-45d3-b989-ff381c154ce6
ms.openlocfilehash: 93410e815a156f91db1962f05fb1aa6baca7f955
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919259"
---
# <a name="defaultcertificate-element"></a>\<defaultCertificate >, élément
Spécifie un certificat X.509 à utiliser lorsqu'un service ou un service d'émission de jeton de sécurité n'en fournit pas un via un protocole de négociation.  
  
 \<system.ServiceModel>  
\<behaviors>  
section endpointBehaviors  
\<> de comportement  
\<clientCredentials>  
\<serviceCertificate>  
\<defaultCertificate>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<defaultCertificate findValue="String"
                    storeLocation=" CurrentUser/LocalMachine"
                    storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                    x509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialiNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|findValue|Chaîne. La valeur à rechercher.|  
|x509FindType|Énumération. L'un des champs de certificat à rechercher.|  
|storeLocation|Énumération. L'un des deux emplacements du magasin du système à rechercher.|  
|storeName|Énumération. L'un des magasins de systèmes à rechercher.|  
  
## <a name="findvalue-attribute"></a>findValue, attribute  
  
|Valeur|Description|  
|-----------|-----------------|  
|String|La valeur dépend du champ (spécifié par l'attribut X509FindType) qui est recherché. Par exemple, lors de la recherche d'une empreinte numérique, la valeur doit être une chaîne de nombres hexadécimaux.|  
  
## <a name="x509findtype-attribute"></a>x509FindType, attribut  
  
|Valeur|Description|  
|-----------|-----------------|  
|Énumération|Les valeurs incluent : FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName , FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.|  
  
## <a name="storelocation-attribute"></a>storeLocation, attribut  
  
|Valeur|Description|  
|-----------|-----------------|  
|Énumération|CurrentUser ou LocalMachine.|  
  
## <a name="storename-attribute"></a>storeName, attribut  
  
|Valeur|Description|  
|-----------|-----------------|  
|Énumération|Les valeurs incluent : AddressBook, AuthRoot, CertificateAuthority, non autorisé, My, root, TrustedPeople et TrustedPublisher.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<serviceCertificate>](servicecertificate-of-clientcredentials-element.md)|Spécifie un certificat à utiliser lors de l'authentification d'un service au client.|  
  
## <a name="remarks"></a>Notes  
 Pour les liaisons qui utilisent la sécurité de message basée sur des certificats, le certificat spécifié par cet élément de configuration est utilisé pour chiffrer les messages au service et doit être utilisé par le service pour signer les réponses au client. Il stocke un certificat unique à utiliser lorsqu'aucun certificat n'est spécifié par un service.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant spécifie un certificat à utiliser pour les points de terminaison dont `http://www.contoso.com` l’URI commence par et un certificat à utiliser pour tous les autres points de terminaison qui n’effectuent pas de négociation de certificat.  
  
```xml  
<serviceCertificate>
  <defaultCertificate findValue="www.contoso.com"
                      storeLocation="LocalMachine"
                      storeName="TrustedPeople"
                      x509FindType="FindByIssuerDistinguishedName" />
  <scopedCertificates>
    <add targetUri="http://www.contoso.com"
         findValue="www.contoso.com"
         storeLocation="LocalMachine"
         storeName="Root"
         x509FindType="FindByIssuerName" />
  </scopedCertificates>
  <authentication revocationMode="Online"
                  trustedStoreLocation="LocalMachine" />
</serviceCertificate>
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Configuration.X509DefaultServiceCertificateElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.DefaultCertificate%2A>
- [Utilisation des certificats](../../../wcf/feature-details/working-with-certificates.md)
- [\<authentication>](authentication-of-clientcertificate-element.md)
- [Sécurisation des clients](../../../wcf/securing-clients.md)
- [Sécurisation des services et des clients](../../../wcf/feature-details/securing-services-and-clients.md)
