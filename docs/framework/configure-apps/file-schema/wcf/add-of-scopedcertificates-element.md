---
title: <add>d' <scopedCertificates> élément
ms.date: 03/30/2017
ms.assetid: e21c1ef8-d6d6-4bca-ac5a-6fbf4bd77412
ms.openlocfilehash: 9756d37527fcf888cad930b24677ae8e6a2c8fba
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920057"
---
# <a name="add-of-scopedcertificates-element"></a>\<Ajouter > de \<l’élément de > scopedCertificates
Ajoute un certificat X.509 à la collection de certificats étendus.  
  
 \<system.ServiceModel>  
\<behaviors>  
section endpointBehaviors  
\<> de comportement  
\<clientCredentials>  
\<serviceCertificate>  
\<scopedCertificates>  
\<Ajouter > élément pour \<scopedCertificates >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<add findValue="String"
     storeLocation="CurrentUser/LocalMachine"
     storeName=" CurrentUser/LocalMachine"
     targetUri="string"
     x509Type="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|targetUri|Chaîne. Spécifie l'URI du service a associé au certificat.|  
|findValue|Chaîne. La valeur à rechercher.|  
|x509FindType|Énumération. L'un des champs de certificat à rechercher.|  
|storeLocation|Énumération. L'un des deux emplacements du magasin dans lequel effectuer la recherche.|  
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
|[\<scopedCertificates>](scopedcertificates-element.md)|Représente une collection de certificats X.509 fournie par les services spécifiques (étendus) à des fins d’authentification.|  
  
## <a name="remarks"></a>Notes  
 Cet élément permet au client de configurer un certificat de service à utiliser en fonction de l'URL du service avec lequel il communique. Ceci s'avère particulièrement utile dans les scénarios de jeton émis dans lesquels un client peut communiquer avec plusieurs services (autant le service final que les services de jeton de sécurité intermédiaire). Pour les liaisons qui utilisent la sécurité de message basée sur des certificats, ce certificat est utilisé pour chiffrer les messages au service et doit être utilisé par le service pour signer les réponses au client.  
  
 Le certificat par défaut est utilisé si une liaison requiert un certificat pour le service et qu’aucun certificat spécifique de l’URL du service n’est trouvé dans ScopedCertificates.  
  
 Pour plus d’informations, consultez la section «certificats délimités [» de la rubrique How to: Créez un client](../../../wcf/feature-details/how-to-create-a-federated-client.md)fédéré.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant illustre l'ajout d'un certificat X.509 à la collection.  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="MyEndpointBehavior">
      <clientCredentials>
        <serviceCertificate>
          <scopedCertificates>
            <add targetUri="http://www.contoso.com"
                 findValue="www.Contoso.com"
                 storeLocation="LocalMachine"
                 storeName="Root"
                 x509FindType="FindByIssuerName" />
          </scopedCertificates>
        </serviceCertificate>
      </clientCredentials>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement.ScopedCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElementCollection>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A>
- [Guide pratique : Créer un client fédéré](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [Utilisation des certificats](../../../wcf/feature-details/working-with-certificates.md)
- [Sécurisation des clients](../../../wcf/securing-clients.md)
- [Sécurisation des services et des clients](../../../wcf/feature-details/securing-services-and-clients.md)
