---
title: <serviceCertificate>d' <clientCredentials> élément
ms.date: 03/30/2017
ms.assetid: e50c0ac5-f0df-4c90-b54b-fc602c1f84ea
ms.openlocfilehash: a3013d0f7efd3014892cf6400447d708809c5fcd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936338"
---
# <a name="servicecertificate-of-clientcredentials-element"></a>\<serviceCertificate > de \<l’élément ClientCredentials >
Spécifie un certificat à utiliser lors de l'authentification d'un service au client.  
  
 \<system.ServiceModel>  
\<behaviors>  
\<endpointBehaviors>  
\<> de comportement  
\<clientCredentials>  
\<serviceCertificate>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<serviceCertificate />
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
 Aucun.  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<defaultCertificate>](defaultcertificate-element.md)|Spécifie un certificat X.509 à utiliser lorsqu'un service ou un service d'émission de jeton de sécurité n'en fournit pas un via un protocole de négociation.|  
|[\<scopedCertificates>](scopedcertificates-element.md)|Représente une collection de certificats X.509 fournie par les services spécifiques (étendus) à des fins d’authentification. Cette collection est utilisée en général pour spécifier les certificats de service pour les services d’émission de jeton de sécurité dans un scénario fédéré.|  
|[\<authentication>](authentication-of-servicecertificate-element.md)|Spécifie les comportements d'authentification des certificats de service utilisés par un client.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|Spécifie les informations d'identification utilisées par le client pour l'authentifier auprès d'un service.|  
  
## <a name="remarks"></a>Notes  
 Cet élément de configuration spécifie les paramètres utilisés par le client pour valider le certificat présenté par le service à l'aide de l'authentification SSL. Il contient également tout certificat pour le service explicitement configuré sur le client à utiliser pour chiffrer des messages au service à l'aide de la sécurité de message.  
  
 Les attributs de l' `serviceCertificate` élément sont identiques aux attributs de l' [ \<> ClientCertificate](clientcertificate-of-clientcredentials-element.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.ServiceCertificate%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.ServiceCertificate%2A>
- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- [Comportements de sécurité](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [Sécurisation des clients](../../../wcf/securing-clients.md)
- [Utilisation des certificats](../../../wcf/feature-details/working-with-certificates.md)
- [Sécurisation des services et des clients](../../../wcf/feature-details/securing-services-and-clients.md)
