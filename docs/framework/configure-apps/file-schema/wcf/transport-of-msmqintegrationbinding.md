---
title: <transport> de <msmqIntegrationBinding>
ms.date: 03/30/2017
ms.assetid: 054579e3-7fdd-47df-99ca-952706ba5c8e
ms.openlocfilehash: 03e6236d1e89f16a460860f5dffff19b7bed8a0a
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91169828"
---
# <a name="transport-of-msmqintegrationbinding"></a>\<transport> de \<msmqIntegrationBinding>

Définit les paramètres de sécurité pour le transport d'intégration Message Queuing.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<msmqIntegrationBinding>**](msmqintegrationbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-msmqintegrationbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<security>
  <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"
             msmqEncryptionAlgorithm="RC4Stream/AES"
             msmqProtectionLevel="None/Sign/EncryptAndSign"
             msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
</security>
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  

 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`msmqAuthenticationMode`|Spécifie comment le message doit être authentifié par le transport MSMQ. S'il a la valeur `None`, la valeur de l'attribut `msmqProtectionLevel` doit également être `None`.<br /><br /> Les valeurs valides sont les suivantes :<br /><br /> -None : aucune authentification.<br />-WindowsDomain : le mécanisme d’authentification utilise Active Directory pour obtenir le certificat X. 509 du SID associé au message. Il est ensuite utilisé pour vérifier l'ACL de la file d'attente afin de s'assurer que l'utilisateur a l'autorisation d'écrire dans la file d'attente.<br />-Certificat : le canal obtient le certificat à partir du magasin de certificats.<br /><br /> La valeur par défaut est WindowsDomain. Cet attribut est de type <xref:System.ServiceModel.MsmqAuthenticationMode>.|  
|`msmqEncryptionAlgorithm`|Spécifie l'algorithme à utiliser pour le chiffrement des messages sur le câble lors du transfert de messages entre des gestionnaires de file d'attente de messages. Les valeurs valides sont les suivantes :<br /><br /> -RC4Stream<br />-AES<br /><br /> La valeur par défaut est RC4Stream. Cet attribut est de type <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.|  
|`msmqProtectionLevel`|Spécifie le mode de sécurisation du message au niveau du transport MSMQ. Le chiffrement garantit l’intégrité des messages tandis que EncryptAndSign garantit l’intégrité et la non-répudiation des messages. autrement dit, le message provient de l’expéditeur et l’expéditeur est bien celui qu’il prétend être.<br /><br /> -Les valeurs valides sont les suivantes :<br />-None : aucune protection.<br />-Sign : les messages sont signés.<br />-EncryptAndSign : les messages sont chiffrés et signés.<br /><br /> La valeur par défaut est Sign. Cet attribut est de type ProtectionLevel.|  
|`msmqSecureHashAlgorithm`|: Spécifie l’algorithme à utiliser pour le calcul du condensé dans le cadre des signatures. Les valeurs valides sont les suivantes :<br />-MD5<br />-SHA1<br />-SHA256<br />-SHA512<br /><br /> La valeur par défaut est SHA1. Cet attribut est de type <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.<br>En raison de problèmes de collision avec MD5 et SHA1, Microsoft recommande SHA256 ou une meilleure solution.|  
  
### <a name="child-elements"></a>Éléments enfants  

 None  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<security>](security-of-basichttpbinding.md)|Définit les paramètres de sécurité pour une liaison MSMQ.|  
  
## <a name="remarks"></a>Notes  

 Cet élément encapsule les paramètres de sécurité pour le transport d'intégration MSMQ. Les paramètres sont les mêmes à la fois pour le transport d'intégration Message Queuing et le transport de mise en file d'attente. Cet élément vous permet de définir le mode d'authentification, l'algorithme de chiffrement, l'algorithme de hachage sécurisé et le niveau de protection.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement.Transport%2A>
- <xref:System.ServiceModel.MsmqTransportSecurity>
- [Sécurisation des services et des clients](../../../wcf/feature-details/securing-services-and-clients.md)
- [Liaisons](../../../wcf/bindings.md)
- [Configuration des liaisons fournies par le système](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Utilisation de liaisons pour configurer des services et des clients](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
