---
title: <message> de <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 6ebf0240-d7be-4493-b0fe-f00fd5989d77
ms.openlocfilehash: 09d9d4a5d1967afaf9a6ed5756c309e78fee0923
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400257"
---
# <a name="message-of-netmsmqbinding"></a>\<> de message \<de NetMsmqBinding >

Définit les paramètres de sécurité des messages SOAP sur cette liaison `netMsmqBinding`.

[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<liaisons >** ](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netMsmqBinding >** ](netmsmqbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de liaison**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de sécurité**](security-of-netmsmqbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de messages**  

## <a name="syntax"></a>Syntaxe

```xml
<netMsmqBinding>
  <binding>
    <security>
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />
    </security>
  </binding>
</netMsmqBinding>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

|Attribut|Description|
|---------------|-----------------|
|algorithmSuite|Définit le chiffrement des messages et algorithmes de clé de type WRAP utilisés pour obtenir la sécurité basée sur des messages pour les messages envoyés via le transport MSMQ.<br /><br /> La valeur par défaut est `Aes256`. Cet attribut est de type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.|
|clientCredentialType|Spécifie le type d'information d'identification à utiliser lors de l'exécution de l'authentification du client pour les messages envoyés via le transport MSMQ. Les valeurs valides sont les suivantes :<br /><br /> None Permet au service d'interagir avec les clients anonymes. Ni le service ni le client n'exigent d'informations d'identification.<br />Windows Cela permet aux échanges SOAP d’être sous le contexte authentifié d’une information d’identification Windows. Exécute toujours une authentification basée sur Kerberos.<br />Nom d’utilisateur Cela permet au service d’exiger que le client soit authentifié à l’aide d’informations d’identification de nom d’utilisateur. Dans ce cas, les informations d’identification doivent être spécifiées à l’aide du `clientCredentials` comportement **attention :**  Windows Communication Foundation (WCF) ne prend pas en charge l’envoi d’un résumé de mot de passe ou la dérivation de clés à l’aide d’un mot de passe et de ces clés pour la sécurité de message. Par conséquent, WCF garantit que l’échange est sécurisé lors de l’utilisation d’informations d’identification de nom d’utilisateur. Ce mode requiert que le certificat de service soit spécifié côté client à l'aide du comportement `clientCredential` et de `serviceCertificate`. <br /><br /> Certificat Cela permet au service d’exiger que le client soit authentifié à l’aide d’un certificat. Les informations d'identification du client dans ce cas doivent être spécifiées à l'aide du comportement `clientCredentials`. Les informations d'identification du service dans ce cas doivent être spécifiées à l'aide du comportement `clientCredentials` en spécifiant le `serviceCertificate`.<br />CardSpace Cela permet au service d’exiger que le client soit authentifié à l’aide d’un CardSpace. Le `serviceCertificate` doit être configuré dans le comportement `clientCredential`.<br /><br /> La valeur par défaut est `Windows`. Cet attribut est de type <xref:System.ServiceModel.MessageCredentialType>.|

### <a name="child-elements"></a>Éléments enfants

Aucun

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[\<> de sécurité](security-of-netmsmqbinding.md)|Définit les paramètres de sécurité d’une liaison.|

## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>
- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Message%2A>
- <xref:System.ServiceModel.NetMsmqSecurity.Message%2A>
- <xref:System.ServiceModel.MessageSecurityOverMsmq>
- [Files d’attente dans WCF](../../../wcf/feature-details/queues-in-wcf.md)
- [Sécurisation des services et des clients](../../../wcf/feature-details/securing-services-and-clients.md)
- [Liaisons](../../../wcf/bindings.md)
- [Configuration des liaisons fournies par le système](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Utilisation de liaisons pour configurer des services et des clients](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](../../../misc/binding.md)
