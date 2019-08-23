---
title: <clientCertificate> de <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 90ad03aa-2317-43dd-8a72-6d24cdcad15c
ms.openlocfilehash: 277e5e33bcc7f9d417da7ce24caa4c6200c23e23
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919542"
---
# <a name="clientcertificate-of-servicecredentials"></a>\<> ClientCertificate of \<ServiceCredentials >
Définit un certificat X.509 permettant de signer et de chiffrer des messages destinés à un client et envoyés à partir d'un service selon un modèle de communication duplex.  
  
 \<system.ServiceModel>  
\<behaviors>  
\<serviceBehaviors>  
\<serviceBehaviors>  
\<> de comportement  
\<serviceCredentials>  
\<clientCertificate>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<clientCertificate>
  <certificate />
  <authentication />
</clientCertificate>
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
 Aucun.  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<authentication>](authentication-of-clientcertificate-element.md)|Spécifie des options d'authentification pour le certificat client.|  
|[\<certificate>](certificate-of-clientcertificate-element.md)|Spécifie le certificat à utiliser.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|Spécifie les informations d’identification à utiliser pour authentifier le service, ainsi que les paramètres liés à la validation des informations d’identification du client.|  
  
## <a name="remarks"></a>Notes  
 Cet élément est utilisé lorsque le service doit disposer du certificat du client à l'avance afin de communiquer de manière sécurisée avec le client. Cela se produit lors de l'utilisation du modèle de communication duplex. Dans le modèle demande-réponse classique, le client inclut son certificat dans la demande que le service utilise pour sécuriser à nouveau sa réponse au client. Dans le modèle de communication duplex, toutefois, le service ne dispose pas de demande du client et, par conséquent, requiert le certificat du client à l'avance pour sécuriser l'envoi du message au client. C'est pourquoi vous devez obtenir le certificat du client dans une négociation hors bande et l'indiquer à l'aide de cet élément. Pour plus d’informations sur les services duplex [, consultez Procédure: Créez un contrat](../../../wcf/feature-details/how-to-create-a-duplex-contract.md)duplex.  
  
 Le certificat défini dans cet élément est utilisé pour chiffrer les messages au client uniquement pour les liaisons configurées avec le mode d’authentification de sécurité des messages `MutualCertificateDuplex`.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.ClientCertificate%2A>
- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>
- <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential>
- [Guide pratique : Créer un contrat duplex](../../../wcf/feature-details/how-to-create-a-duplex-contract.md)
- [Comportements de sécurité](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [Utilisation des certificats](../../../wcf/feature-details/working-with-certificates.md)
