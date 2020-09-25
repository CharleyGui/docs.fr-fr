---
title: <authentication> d' <clientCertificate> élément
ms.date: 03/30/2017
ms.assetid: 4a55eea2-1826-4026-b911-b7cc9e9c8bfe
ms.openlocfilehash: 13296dbc2b3bc8836770197a1549586c841b4635
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201601"
---
# <a name="authentication-of-clientcertificate-element"></a>\<authentication> d' \<clientCertificate> élément

Spécifie les comportements d'authentification des certificats clients utilisés par un service.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCertificate>**](clientcertificate-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<authentication>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<authentication customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                includeWindowsGroups="Boolean"
                mapClientCertificateToWindowsAccount="Boolean"
                revocationMode="NoCheck/Online/Offline"
                trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  

 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|customCertificateValidatorType|Chaîne facultative. Type et assembly utilisés pour valider un type personnalisé. Cet attribut doit être défini lorsque `certificateValidationMode` a la valeur `Custom`.|  
|certificateValidationMode|Énumération facultative. Spécifie l'un des modes utilisés pour valider les informations d'identification. Cet attribut est de type <xref:System.ServiceModel.Security.X509CertificateValidationMode>. S'il est défini à <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom?displayProperty=nameWithType>, un `customCertificateValidator` doit également être fourni. La valeur par défaut est <xref:System.ServiceModel.Security.X509CertificateValidationMode.ChainTrust?displayProperty=nameWithType>.|  
|includeWindowsGroups|Valeur booléenne facultative. Spécifie si des groupes Windows sont inclus dans le contexte de sécurité. L'affectation de la valeur `true` à cet attribut a un impact sur les performances du fait que cela provoque une expansion de groupe complète. Affectez la valeur `false` à cet attribut s'il n'est pas nécessaire d'établir la liste des groupes auxquels appartient un utilisateur.|  
|mapClientCertificateToWindowsAccount|Propriété booléenne. Spécifie si le client peut être mappé à une identité Windows à l'aide du certificat. Active Directory doit être activé pour cela.|  
|revocationMode|Énumération facultative. Un des modes utilisés pour vérifier des listes de certificats révoqués (RCL). Par défaut, il s’agit de `Online`. Cette valeur est ignorée lors de l'utilisation de la sécurité de transport HTTP.|  
|trustedStoreLocation|Énumération facultative. L'un des deux emplacements du magasin du système : `LocalMachine` ou `CurrentUser`. Cette valeur est utilisée lorsqu'un certificat de service est négocié au client. La validation est effectuée par rapport au magasin de **personnes autorisées** dans l’emplacement de magasin spécifié. Par défaut, il s’agit de `CurrentUser`.|  
  
## <a name="customcertificatevalidatortype-attribute"></a>customCertificateValidatorType, attribut  
  
|Valeur|Description|  
|-----------|-----------------|  
|String|Spécifie le nom de type, l'assembly et d'autres données utilisées pour rechercher le type.|  
  
## <a name="certificatevalidationmode-attribute"></a>certificateValidationMode, attribut  
  
|Valeur|Description|  
|-----------|-----------------|  
|Énumération|Une des valeurs suivantes : None, PeerTrust, ChainTrust, PeerOrChainTrust, Custom.<br /><br /> Pour plus d’informations, consultez [utilisation des certificats](../../../wcf/feature-details/working-with-certificates.md).|  
  
## <a name="revocationmode-attribute"></a>revocationMode, attribut  
  
|Valeur|Description|  
|-----------|-----------------|  
|Énumération|Une des valeurs suivantes : NoCheck, Online, Offline. Pour plus d’informations, consultez [utilisation des certificats](../../../wcf/feature-details/working-with-certificates.md).|  
  
## <a name="trustedstorelocation-attribute"></a>trustedStoreLocation, attribut  
  
|Valeur|Description|  
|-----------|-----------------|  
|Énumération|L’une des valeurs suivantes : `LocalMachine` ou `CurrentUser`. Par défaut, il s’agit de `CurrentUser`. Si l'application cliente s'exécute sous un compte système, le certificat se trouve généralement dans `LocalMachine`. Si l'application cliente s'exécute sous un compte d'utilisateur, le certificat se trouve généralement dans `CurrentUser`.|  
  
### <a name="child-elements"></a>Éléments enfants  

 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<clientCertificate>](clientcertificate-of-servicecredentials.md)|Définit un certificat X.509 utilisé pour authentifier un client à un service.|  
  
## <a name="remarks"></a>Notes  

 L'élément `<authentication>` correspond à la classe <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication>. Il vous permet de personnaliser la manière dont les clients sont authentifiés. Vous pouvez affecter `certificateValidationMode`, `None`, `ChainTrust`, `PeerOrChainTrust` ou `PeerTrust` à l'attribut `Custom`. Par défaut, le niveau a la valeur `ChainTrust` , qui spécifie que chaque certificat doit se trouver dans une hiérarchie de certificats se terminant par une *autorité racine* au sommet de la chaîne. C’est le mode le plus sécurisé. Vous pouvez également affecter la valeur `PeerOrChainTrust`, laquelle spécifie que les certificats auto-émis (approbation homologue) sont acceptés, de même que les certificats qui se trouvent dans une chaîne approuvée. Cette valeur est utilisée lors du développement et du débogage des clients et des services car il n'est pas nécessaire d'acheter les certificats auto-émis auprès d'une autorité approuvée. Lorsque vous déployez un client, utilisez à la place la valeur `ChainTrust`.  
  
 Vous pouvez également utiliser `Custom`. Lorsque vous utilisez `Custom`, vous devez également affecter l'assembly et le type utilisés pour valider le certificat à l'attribut `customCertificateValidatorType`. Pour créer votre propre validateur personnalisé, vous devez hériter de la classe <xref:System.IdentityModel.Selectors.X509CertificateValidator> abstraite. Pour plus d’informations, consultez [Comment : créer un service qui utilise un validateur de certificat personnalisé](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).  
  
## <a name="example"></a>Exemple  

 Le code suivant spécifie un certificat X.509 et un type de validation personnalisé dans l'élément `<authentication>`.  
  
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

- <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication>
- <xref:System.ServiceModel.Security.X509CertificateValidationMode>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.Authentication%2A>
- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement.Authentication%2A>
- <xref:System.ServiceModel.Configuration.X509ClientCertificateAuthenticationElement>
- [Comportements de sécurité](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [Procédure : créer un service qui utilise un validateur de certificat personnalisé](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)
- [Utilisation des certificats](../../../wcf/feature-details/working-with-certificates.md)
