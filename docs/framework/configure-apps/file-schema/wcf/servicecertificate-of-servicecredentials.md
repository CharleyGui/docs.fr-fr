---
title: <serviceCertificate> de <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 597ae6d5-4938-4950-9f5e-b2280e816182
ms.openlocfilehash: 36a228da262095bfe05d66c6d44ac73ba0ca401b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936312"
---
# <a name="servicecertificate-of-servicecredentials"></a>\<serviceCertificate > de \<ServiceCredentials >
Spécifiez un certificat X.509 qui sera utilisé pour authentifier le service auprès des clients à l'aide du mode de sécurité Message.  
  
 \<system.ServiceModel>  
\<behaviors>  
\<serviceBehaviors>  
\<> de comportement  
\<serviceCredentials>  
\<serviceCertificate>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<serviceCertificate findValue="String"
                    storeLocation="LocalMachine/CurrentUser"
                    storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                    x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`findValue`|Chaîne qui contient la valeur à rechercher dans le magasin de certificats X.509. Le type contenu dans l'attribut doit satisfaire les spécifications du X509FindType spécifié. La valeur par défaut est une chaîne vide.|  
|`storeLocation`|Spécifie l'emplacement du magasin de certificats X.509 que le client utilise pour valider le certificat du serveur. Les valeurs valides sont les suivantes :<br /><br /> -LocalMachine: magasin de certificats attribué à l’ordinateur local.<br />-CurrentUser: magasin de certificats attribué à l’utilisateur actuel.<br /><br /> La valeur par défaut est LocalMachine.|  
|`storeName`|Spécifie le nom du magasin de certificats X.509 à ouvrir. Les valeurs valides sont les suivantes :<br /><br /> Carnet Magasin de certificats pour d’autres utilisateurs.<br />-   AuthRoot: Magasin de certificats pour les autorités de certification tierces.<br />- CertificatAuthority: Magasin de certificats pour les autorités de certification (ca) intermédiaires.<br />Interdits Magasin de certificats pour les certificats révoqués.<br />M' Magasin de certificats pour les certificats personnels.<br />Causes Magasin de certificats pour les autorités de certification racines de confiance (ca).<br />TrustedPeople Magasin de certificats pour les personnes et les ressources directement approuvées.<br />TrustedPublisher Magasin de certificats pour les éditeurs directement approuvés.<br /><br /> La valeur par défaut est My.|  
|`x509FindType`|Définit le type de recherche X.509 à exécuter. Les valeurs valides sont les suivantes :<br /><br /> -   FindByThumbprint<br />-   FindBySubjectName<br />-   FindBySubjectDistinguishedName<br />-   FindByIssuerName<br />-   FindByIssuerDistinguishedName<br />-   FindBySerialNumber<br />-   FindByTimeValid<br />-   FindByTimeNotYetValid<br />-   FindByTemplateName<br />-   FindByApplicationPolicy<br />-   FindByCertificatePolicy<br />-   FindByExtension<br />-   FindByKeyUsage<br />-   FindBySubjectKeyIdentifier<br /><br /> Le type contenu dans l'attribut `findValue` doit satisfaire les spécifications du X509FindType spécifié.<br /><br /> La valeur par défaut est FindBySubjectDistinguishedName.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|Spécifie l’information d’identification à utiliser pour authentifier le service, ainsi que les paramètres liés à la validation de l’information d’identification du client.|  
  
## <a name="remarks"></a>Notes  
 Cet élément vous permet de spécifier un certificat X.509 qui sera utilisé pour authentifier le service auprès des clients à l'aide du mode de sécurité Message. Si vous utilisez un certificat qui sera périodiquement renouvelé, son empreinte numérique changera. Dans ce cas, utilisez le nom du sujet comme `x509FindType` car le certificat peut être réémis avec le même nom du sujet.  
  
 Pour plus d’informations sur l’utilisation de l' [élément, consultez Procédure: Spécifiez les valeurs](../../../wcf/how-to-specify-client-credential-values.md)d’informations d’identification du client.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.ServiceCertificate%2A>
- <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential>
- <xref:System.ServiceModel.Description.ServiceCredentials.ServiceCertificate%2A>
- [Guide pratique pour Spécifier les valeurs d’informations d’identification du client](../../../wcf/how-to-specify-client-credential-values.md)
- [Comportements de sécurité](../../../wcf/feature-details/security-behaviors-in-wcf.md)
