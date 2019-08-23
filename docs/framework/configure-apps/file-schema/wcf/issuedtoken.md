---
title: <issuedToken>
ms.date: 03/30/2017
ms.assetid: b6eae4b7-a6cd-4e1a-b0f6-f407022550b0
ms.openlocfilehash: 68e3a0802a10b14148188a81ee24ed901caa147f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925380"
---
# <a name="issuedtoken"></a>\<issuedToken>
Spécifie un jeton personnalisé utilisé pour authentifier un client auprès d'un service.  
  
 \<system.ServiceModel>  
\<behaviors>  
section endpointBehaviors  
\<> de comportement  
\<clientCredentials>  
\<issuedToken>  
  
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
|`maxIssuedTokenCachingTime`|Attribut Timespan facultatif indiquant la durée de mise en cache des jetons émis lorsque l'émetteur de jeton (un STS) ne spécifie aucune durée. La valeur par défaut est «10675199.02:48:05.4775807».|  
  
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
 Un jeton émis est un type d'informations d'identification personnalisé utilisé, par exemple, lors d'une authentification à l'aide d'un service STS dans un scénario fédéré. Par défaut, le jeton est un jeton SAML. Pour plus d’informations, consultez [Fédération et jetons émis](../../../wcf/feature-details/federation-and-issued-tokens.md). et la [Fédération et les jetons émis](../../../wcf/feature-details/federation-and-issued-tokens.md).  
  
 Cette section contient les éléments permettant de configurer un émetteur local de jetons ou les comportements utilisés avec un service d'émission de jeton de sécurité. Pour obtenir des instructions sur la configuration d’un client pour qu’il utilise un [émetteur local, consultez Procédure: Configurez un émetteur](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)local.  
  
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
- [Guide pratique pour Créer un client fédéré](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [Guide pratique pour Configurer un émetteur local](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [Fédération et jetons émis](../../../wcf/feature-details/federation-and-issued-tokens.md)
