---
title: <messageSenderAuthentication>
ms.date: 03/30/2017
ms.assetid: ea62fc06-55fb-42e0-aa2b-8867bdf4b415
ms.openlocfilehash: e7888d01838312aa51397ca39133edb9318fac80
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204773"
---
# \<messageSenderAuthentication>

Spécifie les paramètres d'authentification pour le certificat homologue utilisé par l'expéditeur d'un message.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peer>**](peer-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<messageSenderAuthentication>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<messageSenderAuthentication customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                             certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                             revocationMode="NoCheck/Online/Offline"
                             trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  

 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`certificateValidationMode`|Énumération facultative. Spécifie l'un des cinq modes utilisés pour valider les informations d'identification. Cet attribut est de type <xref:System.ServiceModel.Security.X509CertificateValidationMode>. S'il est défini à `Custom`, un `customCertificateValidator` doit également être fourni.|  
|`customCertificateValidatorType`|Chaîne facultative. Spécifie un type et un assembly utilisés pour valider un type personnalisé. Cet attribut doit être défini lorsque `certificateValidationMode` a la valeur `Custom`. Cet attribut est de type <xref:System.IdentityModel.Selectors.X509CertificateValidator>. Windows Communication Foundation (WCF) fournit un validateur de certificat homologue par défaut qui vérifie le certificat homologue par rapport au magasin de personnes autorisées. Il vérifie également que le certificat remonte jusqu'à une racine valide. Vous pouvez implémenter un validateur personnalisé pour spécifier un comportement différent et utiliser cet attribut pour pointer vers ce validateur.|  
|`revocationMode`|Énumération facultative. Spécifie le mode de révocation de certificat. Cet attribut est de type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>. Le système vérifie que le certificat homologue n'a pas été révoqué en le recherchant dans la liste des certificats révoqués. Cette vérification peut être effectuée en ligne ou par rapport à une liste de révocations mise en cache. La vérification de la révocation peut être désactivée en affectant la valeur NoCheck à cet attribut.|  
|`trustedStoreLocation`|Énumération facultative. Spécifie l’emplacement du magasin de confiance dans lequel le certificat homologue est validé par le système de sécurité WCF. Cet attribut est de type <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.|  
  
### <a name="child-elements"></a>Éléments enfants  

 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<peer>](peer-of-servicecredentials.md)|Spécifie les informations d'identification actuelles d'un nœud homologue.|  
  
## <a name="remarks"></a>Notes  

 Cet élément doit être configuré si l'authentification des messages est sélectionnée. Pour les canaux de sortie, chaque message est signé à l’aide du certificat fourni par [\<certificate>](certificate-element.md) . Avant d'être remis à l'application, tous les messages sont vérifiés par rapport aux informations d'identification de message à l'aide du validateur spécifié par l'attribut `customCertificateValidatorType` de cet élément. Le validateur peut accepter ou rejeter les informations d'identification.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>
- [Utilisation des certificats](../../../wcf/feature-details/working-with-certificates.md)
- [Réseaux homologues](../../../wcf/feature-details/peer-to-peer-networking.md)
- [Peer Channel Message Authentication](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))
- [Peer Channel Custom Authentication](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))
- [Sécurisation des applications de canal homologue](../../../wcf/feature-details/securing-peer-channel-applications.md)
