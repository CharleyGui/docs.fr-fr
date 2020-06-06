---
title: <certificate>d' <clientCertificate> élément
ms.date: 03/30/2017
ms.assetid: 00297efb-a7f2-4e03-bc2b-943d545610fc
ms.openlocfilehash: d0c4ef9d3657d2dfa787feb3576beda09d1997a3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400542"
---
# <a name="certificate-of-clientcertificate-element"></a>\<certificate>d' \<clientCertificate> élément
Spécifie un certificat X.509 utilisé pour signer et chiffrer des messages.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCertificate>**](clientcertificate-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificate>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<certificate findValue="String"
             storeLocation = "CurrentUser/LocalMachine"
             storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
             X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`findValue`|Chaîne qui contient la valeur à rechercher dans le magasin de certificats X.509. Le type contenu dans l'attribut doit satisfaire les spécifications du X509FindType spécifié. La valeur par défaut est une chaîne vide.|  
|`storeLocation`|Spécifie l'emplacement du magasin de certificats X.509 que le client utilise pour valider le certificat du serveur. Les valeurs valides sont les suivantes :<br /><br /> -LocalMachine : magasin de certificats attribué à l’ordinateur local.<br />-CurrentUser : magasin de certificats attribué à l’utilisateur actuel.<br /><br /> La valeur par défaut est LocalMachine.|  
|`storeName`|Spécifie le nom du magasin de certificats X.509 à ouvrir. Les valeurs valides sont les suivantes :<br /><br /> -AddressBook : magasin de certificats pour d’autres utilisateurs.<br />-AuthRoot : magasin de certificats pour les autorités de certification tierces.<br />-CertificationAuthority : magasin de certificats pour les autorités de certification intermédiaires (ca).<br />-Non autorisé : magasin de certificats pour les certificats révoqués.<br />-My : magasin de certificats pour les certificats personnels.<br />-Root : magasin de certificats pour les autorités de certification racines de confiance.<br />-TrustedPeople : magasin de certificats pour les personnes et les ressources directement approuvées.<br />-TrustedPublisher : magasin de certificats pour les éditeurs directement approuvés.<br /><br /> La valeur par défaut est My.|  
|`X509FindType`|Définit le type de recherche X.509 à exécuter. Les valeurs valides sont les suivantes :<br /><br /> -FindByThumbPrint<br />-FindBySubjectName<br />-FindBySubjectDistinguishedName<br />- FindByIssuerName<br />- FindByIssuerDistinguishedName<br />-FindBySerialNumber<br />- FindByTimeValid<br />- FindByTimeNotYetValid<br />- FindByTemplateName<br />- FindByApplicationPolicy<br />- FindByCertificatePolicy<br />- FindByExtension<br />- FindByKeyUsage<br />- FindBySubjectKeyIdentifier<br /><br /> Le type contenu dans l'attribut `findValue` doit satisfaire les spécifications du X509FindType spécifié.<br /><br /> La valeur par défaut est FindBySubjectDistinguishedName.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<clientCertificate>](clientcertificate-of-servicecredentials.md)||  
  
## <a name="remarks"></a>Notes  
 L'élément `<certificate>` est utilisé lorsque le service doit disposer du certificat du client à l'avance afin de communiquer de manière sécurisée avec le client. Cela se produit lors de l'utilisation du modèle de communication duplex. Dans le modèle demande-réponse classique, le client inclut son certificat dans la demande que le service utilise pour sécuriser à nouveau sa réponse au client. Dans le modèle de communication duplex, toutefois, le service ne dispose pas de demande du client et, par conséquent, requiert le certificat du client à l'avance pour sécuriser l'envoi du message au client. C'est pourquoi vous devez obtenir le certificat du client dans une négociation hors bande et l'indiquer à l'aide de cet élément. Pour plus d’informations sur les services duplex, consultez [Comment : créer un contrat duplex](../../../wcf/feature-details/how-to-create-a-duplex-contract.md).  
  
## <a name="example"></a>Exemple  
 Le code suivant indique comment rechercher un certificat X.509 approprié ainsi qu’un type de validation personnalisé dans l’élément `<authentication>`.  
  
```xml  
<serviceBehaviors>
  <behavior name="myServiceBehavior">
    <clientCertificate>
      <certificate findValue="www.cohowinery.com"
                   storeLocation="CurrentUser"
                   storeName="TrustedPeople"
                   x509FindType="FindByIssuerName" />
      <authentication customCertificateValidatorType="MyTypes.Coho"
                      certificateValidationMode="Custom"
                      revocationMode="Offline"
                      includeWindowsGroups="false"
                      mapClientCertificateToWindowsAccount="true" />
    </clientCertificate>
  </behavior>
</serviceBehaviors>
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.Certificate%2A>
- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement.Certificate%2A>
- <xref:System.ServiceModel.Configuration.X509ClientCertificateCredentialsElement>
- [Comportements de sécurité](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [Guide pratique pour créer un service qui utilise un validateur de certificat personnalisé](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)
- [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md)
