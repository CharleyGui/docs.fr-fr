---
title: <issuedToken>
ms.date: 03/30/2017
ms.assetid: b6eae4b7-a6cd-4e1a-b0f6-f407022550b0
ms.openlocfilehash: 9f3feb11fbe45cbb4b952c70feaa99f9c481dd2b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91157367"
---
# \<issuedToken>

Spécifie un jeton personnalisé utilisé pour authentifier un client auprès d'un service.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuedToken>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<issuedToken cacheIssuedTokens="Boolean"
             defaultKeyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"
             issuedTokenRenewalThresholdPercentage = "0 to 100"
             issuerChannelBehaviors="String"
             localIssuerChannelBehaviors="String"
             maxIssuedTokenCachingTime="TimeSpan">
</issuedToken>
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  

 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`cacheIssuedTokens`|Attribut booléen facultatif indiquant si les jetons sont mis en cache. Par défaut, il s’agit de `true`.|  
|`defaultKeyEntropyMode`|Attribut de chaîne facultatif qui spécifie les valeurs aléatoires (entropies) utilisées pour les opérations de protocole de transfert. Les valeurs comprennent `ClientEntropy`, `ServerEntropy` et `CombinedEntropy`. La valeur par défaut est `CombinedEntropy`. Cet attribut est de type <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.|  
|`issuedTokenRenewalThresholdPercentage`|Attribut entier facultatif indiquant le pourcentage d'un délai valide (fourni par l'émetteur du jeton) pouvant s'écouler avant le renouvellement d'un jeton. Les valeurs sont comprises entre 0 et 100. La valeur par défaut est 60, c'est-à-dire que 60 % du délai s'écoule avant la tentative de renouvellement.|  
|`issuerChannelBehaviors`|Attribut facultatif indiquant les comportements de canal à utiliser lors d'une communication avec l'émetteur.|  
|`localIssuerChannelBehaviors`|Attribut facultatif indiquant les comportements de canal à utiliser lors d'une communication avec l'émetteur local.|  
|`maxIssuedTokenCachingTime`|Attribut Timespan facultatif indiquant la durée de mise en cache des jetons émis lorsque l'émetteur de jeton (un STS) ne spécifie aucune durée. La valeur par défaut est « 10675199.02:48:05.4775807 ».|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<localIssuer>](localissuer.md)|Spécifie l’adresse de l’émetteur local du jeton et la liaison utilisée pour communiquer avec le point de terminaison.|  
|[\<issuerChannelBehaviors>](issuerchannelbehaviors-element.md)|Spécifie les comportements de point de terminaison à utiliser lors d'une communication avec un émetteur local.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|Spécifie les informations d'identification utilisées pour authentifier un client auprès d'un service.|  
  
## <a name="remarks"></a>Notes  

 Un jeton émis est un type d'informations d'identification personnalisé utilisé, par exemple, lors d'une authentification à l'aide d'un service STS dans un scénario fédéré. Par défaut, le jeton est un jeton SAML. Pour plus d’informations, consultez [Fédération et jetons émis](../../../wcf/feature-details/federation-and-issued-tokens.md), ainsi que [Fédération et jetons émis](../../../wcf/feature-details/federation-and-issued-tokens.md).  
  
 Cette section contient les éléments permettant de configurer un émetteur local de jetons ou les comportements utilisés avec un service d'émission de jeton de sécurité. Pour obtenir des instructions sur la configuration d’un client pour qu’il utilise un émetteur local, consultez [procédure : configurer un émetteur local](../../../wcf/feature-details/how-to-configure-a-local-issuer.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.IssuedToken%2A>
- <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential>
- [Comportements de sécurité](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [Sécurisation des services et des clients](../../../wcf/feature-details/securing-services-and-clients.md)
- [Fédération et jetons émis](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [Sécurisation des clients](../../../wcf/securing-clients.md)
- [Procédure : créer un client fédéré](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [Procédure : configurer un émetteur local](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [Fédération et jetons émis](../../../wcf/feature-details/federation-and-issued-tokens.md)
