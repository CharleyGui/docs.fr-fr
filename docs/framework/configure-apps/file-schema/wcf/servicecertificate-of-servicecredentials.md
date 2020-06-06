---
title: <serviceCertificate> de <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 597ae6d5-4938-4950-9f5e-b2280e816182
ms.openlocfilehash: 513dcad7f4325d653df87fe9cc27572c25e153c5
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399668"
---
# <a name="servicecertificate-of-servicecredentials"></a>\<serviceCertificate> de \<serviceCredentials>
Spécifiez un certificat X.509 qui sera utilisé pour authentifier le service auprès des clients à l'aide du mode de sécurité Message.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceCertificate>**  
  
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
|`storeLocation`|Spécifie l'emplacement du magasin de certificats X.509 que le client utilise pour valider le certificat du serveur. Les valeurs valides sont les suivantes :<br /><br /> -LocalMachine : magasin de certificats attribué à l’ordinateur local.<br />-CurrentUser : magasin de certificats attribué à l’utilisateur actuel.<br /><br /> La valeur par défaut est LocalMachine.|  
|`storeName`|Spécifie le nom du magasin de certificats X.509 à ouvrir. Les valeurs valides sont les suivantes :<br /><br /> -AddressBook : magasin de certificats pour d’autres utilisateurs.<br />-AuthRoot : magasin de certificats pour les autorités de certification tierces.<br />-CertificatAuthority : magasin de certificats pour les autorités de certification intermédiaires (ca).<br />-Non autorisé : magasin de certificats pour les certificats révoqués.<br />-My : magasin de certificats pour les certificats personnels.<br />-Root : magasin de certificats pour les autorités de certification racines de confiance.<br />-TrustedPeople : magasin de certificats pour les personnes et les ressources directement approuvées.<br />-TrustedPublisher : magasin de certificats pour les éditeurs directement approuvés.<br /><br /> La valeur par défaut est My.|  
|`x509FindType`|Définit le type de recherche X.509 à exécuter. Les valeurs valides sont les suivantes :<br /><br /> -FindByThumbprint<br />-FindBySubjectName<br />-FindBySubjectDistinguishedName<br />- FindByIssuerName<br />- FindByIssuerDistinguishedName<br />-FindBySerialNumber<br />- FindByTimeValid<br />- FindByTimeNotYetValid<br />- FindByTemplateName<br />- FindByApplicationPolicy<br />- FindByCertificatePolicy<br />- FindByExtension<br />- FindByKeyUsage<br />- FindBySubjectKeyIdentifier<br /><br /> Le type contenu dans l'attribut `findValue` doit satisfaire les spécifications du X509FindType spécifié.<br /><br /> La valeur par défaut est FindBySubjectDistinguishedName.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucune  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|Spécifie l’information d’identification à utiliser pour authentifier le service, ainsi que les paramètres liés à la validation de l’information d’identification du client.|  
  
## <a name="remarks"></a>Remarques  
 Cet élément vous permet de spécifier un certificat X.509 qui sera utilisé pour authentifier le service auprès des clients à l'aide du mode de sécurité Message. Si vous utilisez un certificat qui sera périodiquement renouvelé, son empreinte numérique changera. Dans ce cas, utilisez le nom du sujet comme `x509FindType` car le certificat peut être réémis avec le même nom du sujet.  
  
 Pour plus d’informations sur l’utilisation de l’élément, consultez Guide pratique [pour spécifier les valeurs d’informations d’identification du client](../../../wcf/how-to-specify-client-credential-values.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.ServiceCertificate%2A>
- <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential>
- <xref:System.ServiceModel.Description.ServiceCredentials.ServiceCertificate%2A>
- [Guide pratique pour spécifier les valeurs d’informations d’identification du client](../../../wcf/how-to-specify-client-credential-values.md)
- [Comportements de sécurité](../../../wcf/feature-details/security-behaviors-in-wcf.md)
