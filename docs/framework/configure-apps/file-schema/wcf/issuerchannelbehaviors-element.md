---
title: Élément <issuerChannelBehaviors>
ms.date: 03/30/2017
ms.assetid: f7378673-8e9b-45b2-98d1-cf5dccdd8c40
no-loc:
- <system.serviceModel>
- <behaviors>
- <endpointBehaviors>
- <behavior>
- <clientCredentials>
- <issuedToken>
- <issuerChannelBehaviors>
- <dataContractSerializer>
ms.openlocfilehash: cbbfb9d3b5af47a360aa82cf837cd6749f61b641
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70893158"
---
# <a name="issuerchannelbehaviors-element"></a>Élément \<issuerChannelBehaviors>

Contient une collection de comportements de point de terminaison client Windows Communication Foundation (WCF) (définis dans la configuration) à utiliser lors de la communication avec les services de jeton de service spécifiés. Les comportements définis ne peuvent pas inclure d' [\<clientCredentials>](clientcredentials.md) éléments.

[\<configuration>](../configuration-element.md)\
&nbsp;&nbsp;[\<system.serviceModel>](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<behaviors>](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<endpointBehaviors>](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<behavior>](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<clientCredentials>](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<issuedToken>](issuedtoken.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<issuerChannelBehaviors>

## <a name="syntax"></a>Syntaxe

```xml
<issuerChannelBehaviors>
  <add behaviorConfiguration="string"
       issuerAddress="string" />
</issuerChannelBehaviors>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[\<add>](add-of-issuerchannelbehaviors.md)|Ajoute un comportement à la collection.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[\<issuedToken>](issuedtoken.md)|Spécifie un jeton personnalisé utilisé pour authentifier un client auprès d'un service.|

## <a name="remarks"></a>Remarques

Utilisez cet élément lorsque des comportements (autres que ceux qui contiennent des éléments `<clientCredentials>`) doivent être utilisés pour communiquer avec un service. Par exemple, si un [\<dataContractSerializer>](datacontractserializer-element.md) élément de comportement doit être inclus.

## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>
- [Identité du service et authentification](../../../wcf/feature-details/service-identity-and-authentication.md)
- [Comportements de sécurité](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [Fédération et jetons émis](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [Securing Services and Clients](../../../wcf/feature-details/securing-services-and-clients.md)
- [Sécurisation des clients](../../../wcf/securing-clients.md)
- [Comment : créer un client fédéré](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [Comment : configurer un émetteur local](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [Fédération et jetons émis](../../../wcf/feature-details/federation-and-issued-tokens.md)
