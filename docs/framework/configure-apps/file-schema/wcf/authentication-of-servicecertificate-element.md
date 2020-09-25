---
title: <authentication> d' <serviceCertificate> élément
ms.date: 03/30/2017
ms.assetid: 733b67b4-08a1-4d25-9741-10046f9357ef
ms.openlocfilehash: c6f2578d85971740e5bd3d75151305a475187492
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201588"
---
# <a name="authentication-of-servicecertificate-element"></a>\<authentication> d' \<serviceCertificate> élément

Spécifie les paramètres utilisés par le proxy client pour authentifier les certificats de service obtenus à l'aide de la négociation SSL/TLS.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate-of-clientcredentials-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<authentication>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<authentication customCertificateValidatorType="String"
                certificateValidationMode="None/PeerTrust/ChainTrust/PeerOrChainTrust/Custom"
                revocationMode="NoCheck/Online/Offline"
                trustedStoreLocation="LocalMachine/CurrentUser" />
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  

 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|customCertificateValidatorType|Chaîne. Type et assembly utilisés pour valider un type personnalisé.|  
|certificateValidationMode|Spécifie l'un de trois modes utilisés pour valider des informations d'identification. S'il est défini à `Custom`, un customCertificateValidator doit également être fourni. Par défaut, il s’agit de `ChainTrust`.|  
|revocationMode|Un des modes utilisés pour vérifier des listes de certificat révoqués (CRL). Par défaut, il s’agit de `Online`.|  
|trustedStoreLocation|L'un des deux emplacements du magasin du système : `LocalMachine` ou `CurrentUser`. Cette valeur est utilisée lorsqu'un certificat de service est négocié au client. La validation est effectuée par rapport au magasin de **personnes autorisées** dans l’emplacement de magasin spécifié. Par défaut, il s’agit de `CurrentUser`.|  
  
## <a name="customcertificatevalidator-attribute"></a>customCertificateValidator, attribut  
  
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
|Énumération|Une des valeurs suivantes : NoCheck, Online, Offline.<br /><br /> Pour plus d’informations, consultez [utilisation des certificats](../../../wcf/feature-details/working-with-certificates.md).|  
  
## <a name="trustedstorelocation-attribute"></a>trustedStoreLocation, attribut  
  
|Valeur|Description|  
|-----------|-----------------|  
|Énumération|Une des valeurs suivantes : LocalMachine ou CurrentUser. La valeur par défaut est CurrentUser. Si l'application cliente s'exécute sous un compte système, le certificat se trouve généralement dans LocalMachine. Si l'application cliente s'exécute sous un compte d'utilisateur, le certificat se trouve généralement dans CurrentUser.|  
  
### <a name="child-elements"></a>Éléments enfants  

 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<serviceCertificate>](servicecertificate-of-clientcredentials-element.md)|Spécifie un certificat à utiliser lors de l'authentification d'un service au client.|  
  
## <a name="remarks"></a>Notes  

 L'attribut `certificateValidationMode` de cet élément de configuration spécifie le niveau de confiance utilisé pour authentifier les certificats. Par défaut, le niveau a la valeur `ChainTrust`, qui spécifie que chaque certificat doit se trouver dans une hiérarchie de certificats se terminant dans une autorité de certification approuvée au sommet de la chaîne. C’est le mode le plus sécurisé. Vous pouvez également affecter la valeur `PeerOrChainTrust`, laquelle spécifie que les certificats auto-émis (approbation homologue) sont acceptés, de même que les certificats qui se trouvent dans une chaîne approuvée. Cette valeur est utilisée lors du développement et du débogage des clients et des services car il n'est pas nécessaire d'acheter les certificats auto-émis auprès d'une autorité approuvée. Lorsque vous déployez un client, utilisez à la place la valeur `ChainTrust`. Vous pouvez également affecter la valeur `Custom` ou `None`. Pour utiliser la valeur `Custom`, vous devez également affecter à l'attribut `customCertificateValidator` l'assembly et le type utilisés pour valider le certificat. Pour créer un validateur personnalisé, vous devez hériter de la classe X509CertificateValidator abstraite. Pour plus d’informations, consultez [Comment : créer un service qui utilise un validateur de certificat personnalisé](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).  
  
 L'attribut `revocationMode` spécifie le mode de vérification des certificats à révoquer. La valeur par défaut est `online`, qui indique que les certificats sont automatiquement vérifiés pour révocation. Pour plus d’informations, consultez [utilisation des certificats](../../../wcf/feature-details/working-with-certificates.md).  
  
## <a name="example"></a>Exemple  

 Dans l’exemple suivant, deux tâches sont effectuées : Il spécifie d’abord un certificat de service que le client doit utiliser lors de la communication avec les points de terminaison dont le nom de domaine se trouve `www.contoso.com` sur le protocole http. Deuxièmement, le mode de révocation et l'emplacement de magasin utilisés pendant l'authentification sont définis.  
  
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

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.Authentication%2A>
- <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication>
- [Comportements de sécurité](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [Utilisation des certificats](../../../wcf/feature-details/working-with-certificates.md)
- [Procédure : créer un service qui utilise un validateur de certificat personnalisé](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)
- [\<authentication>](authentication-of-clientcertificate-element.md)
- [Sécurisation des clients](../../../wcf/securing-clients.md)
- [Sécurisation des services et des clients](../../../wcf/feature-details/securing-services-and-clients.md)
