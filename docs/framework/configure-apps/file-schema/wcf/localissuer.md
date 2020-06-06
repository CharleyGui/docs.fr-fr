---
title: <localIssuer>
ms.date: 03/30/2017
ms.assetid: 26bdd0df-0e7d-4b9e-bbeb-f28c53769385
ms.openlocfilehash: 055b7b49d1f775d49ac20de18c18ca0433716a23
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70397860"
---
# \<localIssuer>
Spécifie l'adresse et la liaison de l'émetteur local à utiliser pour obtenir un jeton de sécurité.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedToken>**](issuedtoken.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<localIssuer>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<localIssuer address="String"
             binding="String"
             bindingConfiguration="String" />
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|address|Chaîne obligatoire. Spécifie l'URI de l'émetteur local.|  
|binding|Chaîne facultative. Une des liaisons fournies par le système. Pour obtenir une liste, consultez [liaisons fournies par le système](../../../wcf/system-provided-bindings.md).|  
|bindingConfiguration|Chaîne facultative. Spécifie une configuration de liaison recherchée dans le fichier de configuration.|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<identity>](identity.md)|Spécifie les informations d'identité de l'émetteur local.|  
|[\<headers>](headers-element.md)|Collection d'en-têtes d'adresse requis pour adresser correctement l'émetteur local. Vous pouvez utiliser le mot clé `add` pour ajouter un en-tête à cette collection.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<issuedToken>](issuedtoken.md)|Spécifie un jeton personnalisé utilisé pour authentifier un client auprès d'un service.|  
  
## <a name="remarks"></a>Remarques  
 Lors de l'obtention d'un jeton émis depuis un service d'émission de jeton de sécurité (STS), l'application cliente doit être configurée avec l'adresse et la liaison à utiliser pour pouvoir communiquer avec le STS. Lorsque <xref:System.ServiceModel.WSFederationHttpBinding> ne fournit pas d’URL pour le service d’émission de jeton de sécurité, ou lorsque l’adresse de l’émetteur d’une liaison fédérée est `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` ou `null` , le canal du Windows Communication Foundation du client (WCF) utilise les valeurs spécifiées par `address` et `binding` pour communiquer avec le STS pour obtenir le jeton émis. Pour plus d’informations sur la configuration d’un émetteur local, consultez [procédure : configurer un émetteur local](../../../wcf/feature-details/how-to-configure-a-local-issuer.md).  
  
## <a name="example"></a>Exemple  
 L'exemple suivant définit les attributs `address`, `binding` et `bindingConfiguration` d'un élément `localIssuer`.  
  
```xml  
<system.serviceModel>
  <behaviors>
    <endpointBehaviors>
      <behavior name="MyEndpointBehavior">
        <clientCredentials>
          <issuedToken cacheIssuedTokens="false"
                       defaultKeyEntropyMode="ClientEntropy">
            <localIssuer address="net.tcp://cohowinery/tokens"
                         binding="netTcpBinding"
                         bindingConfiguration="myTcpBindingConfig" />
          </issuedToken>
        </clientCredentials>
      </behavior>
    </endpointBehaviors>
  </behaviors>
</system.serviceModel>
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.LocalIssuer%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential>
- [Comportements de sécurité](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [Comment : configurer un émetteur local](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [Identité du service et authentification](../../../wcf/feature-details/service-identity-and-authentication.md)
- [Comportements de sécurité](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [Fédération et jetons émis](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [Securing Services and Clients](../../../wcf/feature-details/securing-services-and-clients.md)
- [Sécurisation des clients](../../../wcf/securing-clients.md)
- [Comment : créer un client fédéré](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [Fédération et jetons émis](../../../wcf/feature-details/federation-and-issued-tokens.md)
