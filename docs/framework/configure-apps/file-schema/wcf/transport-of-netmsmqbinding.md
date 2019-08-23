---
title: <transport> de <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 72e1b338-39f0-4af1-a5d9-7a2fb79f6a0b
ms.openlocfilehash: ede4103f9c8f2f73ac34036fe7a58242e32350e0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934694"
---
# <a name="transport-of-netmsmqbinding"></a>\<> de transport \<de NetMsmqBinding >
Définit les paramètres de sécurité de transport.  
  
 \<system.ServiceModel>  
\<bindings>  
\<netMsmqBinding>  
\<binding>  
\<> de sécurité  
\<transport>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<netMsmqBinding>
  <binding>
    <security>
      <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"
                 msmqEncryptionAlgorithm="RC4Stream/AES"
                 msmqProtectionLevel="None/Sign/EncryptAndSign"
                 msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
    </security>
  </binding>
</netMsmqBinding>
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|msmqAuthenticationMode|Spécifie comment le message doit être authentifié par le transport MSMQ. Les valeurs valides sont les suivantes :<br /><br /> None Aucune authentification.<br />WindowsDomain Le mécanisme d’authentification utilise Active Directory pour récupérer le certificat X. 509 pour l’identificateur de sécurité associé au message. Il est ensuite utilisé pour vérifier l'ACL de la file d'attente afin de s'assurer que l'utilisateur a l'autorisation en écriture dans la file d'attente.<br />Certificat Le canal récupère le certificat à partir du magasin de certificats.<br /><br /> Par défaut, il s’agit de `WindowsDomain`.<br /><br /> Si cet attribut a la valeur `None`, l'attribut `msmqProtectionLevel` doit également être défini à `None`. Cet attribut est de type <xref:System.ServiceModel.MsmqAuthenticationMode>|  
|msmqEncryptionAlgorithm|Spécifie l'algorithme à utiliser pour le chiffrement des messages sur le câble lors du transfert de messages entre des gestionnaires de file d'attente de messages. Les valeurs valides sont les suivantes :<br /><br /> -RC4Stream<br />-AES<br />-La valeur par défaut `RC4Stream`est. Cet attribut est de type <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.|  
|msmqProtectionLevel|Spécifie la façon dont les messages sont sécurisés au niveau du transport MSMQ. Le chiffrement garantit l'intégrité des messages, tandis que la signature et le chiffrement garantissent à la fois l'intégrité et le non-rejet des messages. Autrement dit, le message a été effectivement envoyé par l'expéditeur et l'expéditeur est celui qu'il prétend. Les valeurs valides sont les suivantes :<br /><br /> None Aucune protection.<br />Expéditeur Les messages sont signés.<br />EncryptAndSign Les messages sont chiffrés et signés.<br />-La valeur par `Sign`défaut est.|  
|msmqSecureHashAlgorithm|Spécifie l’algorithme de hachage à utiliser pour calculer le condensat de message. Les valeurs valides sont les suivantes :<br /><br /> -   MD5<br />-   SHA1<br />-   SHA256<br />-   SHA512<br /><br /> Par défaut, il s’agit de `SHA1`. Cet attribut est de type <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.<br>En raison de problèmes de collision avec MD5 et SHA1, Microsoft recommande SHA256 ou une meilleure solution.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<> de sécurité](security-of-netmsmqbinding.md)|Définit les paramètres de sécurité de transport pour les transports de mise en file d'attente.|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetMsmqSecurity.Transport%2A>
- <xref:System.ServiceModel.MsmqTransportSecurity>
- [Files d’attente dans WCF](../../../wcf/feature-details/queues-in-wcf.md)
- [Sécurisation des services et des clients](../../../wcf/feature-details/securing-services-and-clients.md)
- [Liaisons](../../../wcf/bindings.md)
- [Configuration des liaisons fournies par le système](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Utilisation de liaisons pour configurer des services et des clients](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](../../../misc/binding.md)
