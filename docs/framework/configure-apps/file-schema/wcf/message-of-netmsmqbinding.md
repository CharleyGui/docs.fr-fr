---
title: <message> de <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 6ebf0240-d7be-4493-b0fe-f00fd5989d77
ms.openlocfilehash: 5a4a4e8b645ee2c607988ac3031af537c93ca8c0
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73736759"
---
# <a name="message-of-netmsmqbinding"></a>\<message> de \<netMsmqBinding>

Définit les paramètres de sécurité des messages SOAP sur cette liaison `netMsmqBinding`.

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netMsmqBinding>**](netmsmqbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-netmsmqbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**  

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
|clientCredentialType|Spécifie le type d'information d'identification à utiliser lors de l'exécution de l'authentification du client pour les messages envoyés via le transport MSMQ. Les valeurs valides sont les suivantes :<br /><br /> -None : cela permet au service d’interagir avec des clients anonymes. Ni le service ni le client n'exigent d'informations d'identification.<br />-Windows : permet aux échanges SOAP d’être sous le contexte authentifié d’une information d’identification Windows. Exécute toujours une authentification basée sur Kerberos.<br />-UserName : permet au service d’exiger que le client soit authentifié à l’aide d’informations d’identification de nom d’utilisateur. Les informations d’identification dans ce cas doivent être spécifiées à l’aide de la prudence relative au `clientCredentials` comportement **:** Windows Communication Foundation (WCF) ne prend pas en charge l’envoi d’un résumé de mot de passe ou la dérivation de clés à l’aide du mot de passe et de ces clés pour la sécurité de message. WCF applique donc la sécurisation des échanges lors de l'utilisation des informations d'identification Nom d'utilisateur. Ce mode requiert que le certificat de service soit spécifié côté client à l'aide du comportement `clientCredential` et de `serviceCertificate`. <br /><br /> -Certificat : permet au service d’exiger que le client soit authentifié à l’aide d’un certificat. Les informations d'identification du client dans ce cas doivent être spécifiées à l'aide du comportement `clientCredentials`. Les informations d'identification du service dans ce cas doivent être spécifiées à l'aide du comportement `clientCredentials` en spécifiant le `serviceCertificate`.<br />-CardSpace : permet au service d’exiger que le client soit authentifié à l’aide d’un CardSpace. Le `serviceCertificate` doit être configuré dans le comportement `clientCredential`.<br /><br /> La valeur par défaut est `Windows`. Cet attribut est de type <xref:System.ServiceModel.MessageCredentialType>.|

### <a name="child-elements"></a>Éléments enfants

Aucune

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[\<security>](security-of-netmsmqbinding.md)|Définit les paramètres de sécurité d’une liaison.|

## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>
- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Message%2A>
- <xref:System.ServiceModel.NetMsmqSecurity.Message%2A>
- <xref:System.ServiceModel.MessageSecurityOverMsmq>
- [Files d'attente dans WCF](../../../wcf/feature-details/queues-in-wcf.md)
- [Securing Services and Clients](../../../wcf/feature-details/securing-services-and-clients.md)
- [Liaisons](../../../wcf/bindings.md)
- [Configuration des liaisons fournies par le système](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Utilisation de liaisons pour configurer des services et des clients](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
