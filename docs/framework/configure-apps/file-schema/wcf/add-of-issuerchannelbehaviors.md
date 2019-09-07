---
title: <add> de <issuerChannelBehaviors>
ms.date: 03/30/2017
ms.assetid: 50710506-e28f-45dd-ab7e-bff6f44173db
ms.openlocfilehash: cf7ac2691ad1c641352a8047373ced538b19e983
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398329"
---
# <a name="add-of-issuerchannelbehaviors"></a>\<Ajouter > de \<la > issuerChannelBehaviors

Ajoute un comportement de point de terminaison à utiliser lors de la communication avec un service STS.

> [!NOTE]
> Si un comportement de point de terminaison contient un [ \<élément ClientCredentials >](clientcredentials.md) , une exception est levée.

[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportements >** ](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportement**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clientCredentials >** ](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<issuedToken >** ](issuedtoken.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<issuerChannelBehaviors >** ](issuerchannelbehaviors-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Ajouter >**  

## <a name="syntax"></a>Syntaxe

```xml
<add issuerAddress="string"
     behaviorConfiguration="string" />
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

|Attribut|Description|
|---------------|-----------------|
|issuerAddress|URI de l'émetteur de jeton de sécurité avec lequel communiquer.|
|behaviorConfiguration|Nom d'un comportement de point de terminaison défini dans le même fichier de configuration.|

### <a name="child-elements"></a>Éléments enfants

Aucun.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[\<issuerChannelBehaviors>](issuerchannelbehaviors-element.md)|Contient une collection de comportements de point de terminaison client Windows Communication Foundation (WCF) à utiliser lors de la communication avec les services de jeton de service spécifiés.|

## <a name="remarks"></a>Notes

`issuerAddress` contient l'URI du service d'émission de jeton de sécurité avec lequel le client souhaite communiquer. `behaviorConfiguration`pointe vers un comportement de point de terminaison que l’application utilise dans les canaux créés par Windows Communication Foundation (WCF) pour récupérer les jetons émis à partir des services d’émission de jeton de sécurité.

## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>
- [Identité du service et authentification](../../../wcf/feature-details/service-identity-and-authentication.md)
- [Comportements de sécurité](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [Fédération et jetons émis](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [Sécurisation des services et des clients](../../../wcf/feature-details/securing-services-and-clients.md)
- [Sécurisation des clients](../../../wcf/securing-clients.md)
- [Guide pratique pour Créer un client fédéré](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [Guide pratique pour Configurer un émetteur local](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [Fédération et jetons émis](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [\<issuerChannelBehaviors>](issuerchannelbehaviors-element.md)
