---
title: <peer>d' <clientCredentials> élément
ms.date: 03/30/2017
ms.assetid: 505bd987-0042-4622-b68e-94f439729d53
ms.openlocfilehash: dce7ef64de1e3eb248e3553c97cbce8e9b205b4c
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400097"
---
# <a name="peer-of-clientcredentials-element"></a>\<> homologue \<de l’élément > ClientCredentials
Spécifie les informations d'identification utilisées lors de l'authentification de clients de réseau pair à pair.  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportements >** ](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportement**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clientCredentials >** ](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> homologues**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<peer>
  <certificate />
  <peerAuthentication />
  <messageSenderAuthentication />
</peer>
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
 Aucun.  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<certificate>](certificate-element.md)|Spécifie un certificat X.509 à utiliser pour signer et chiffrer des messages pour les clients de réseau pair à pair. .|  
|[\<peerAuthentication>](peerauthentication-element.md)|Spécifie les options d'authentification pour les clients du réseau pair à pair.|  
|[\<messageSenderAuthentication>](messagesenderauthentication-element.md)|Spécifie les options d'authentification pour les expéditeurs de messages.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|Spécifie les informations d'identification utilisées pour authentifier un client auprès d'un service.|  
  
## <a name="remarks"></a>Notes  
 Cet élément de configuration spécifie les informations d'identification qu'un nœud homologue utilise pour s'authentifier sur les autres nœuds de la maille, ainsi que les paramètres d'authentification qu'un nœud homologue utilise pour authentifier les autres nœuds homologues. Pour plus d’informations, consultez [canal homologue l’authentification des messages](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90)) et la [sécurisation des applications canal homologue](../../../wcf/feature-details/securing-peer-channel-applications.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Peer%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.Peer%2A>
- <xref:System.ServiceModel.Security.PeerCredential>
- [Réseaux homologues](../../../wcf/feature-details/peer-to-peer-networking.md)
- [Sécurisation des clients](../../../wcf/securing-clients.md)
- [canal homologue l’authentification des messages](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))
- [canal homologue l’authentification personnalisée](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))
- [Sécurisation des applications de canal homologue](../../../wcf/feature-details/securing-peer-channel-applications.md)
- [Sécurisation des services et des clients](../../../wcf/feature-details/securing-services-and-clients.md)
