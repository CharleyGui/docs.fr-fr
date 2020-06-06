---
title: <add> de <claimTypeRequirements>
ms.date: 03/30/2017
ms.assetid: c68e83c9-39e8-4264-b1ce-b6a9eb5b98aa
ms.openlocfilehash: 6ba935f7f6dae0e4d9e6581f53a50c684efcbed3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153085"
---
# <a name="add-of-claimtyperequirements"></a>\<add> de \<claimTypeRequirements>
Spécifie les types de revendications requis et facultatifs censés apparaître dans les informations d'identification fédérées. Par exemple, les services déclarent les exigences relatives aux informations d’identification entrantes devant posséder un certain jeu de types de revendications.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenParameters>**](issuedtokenparameters.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequirements>**](claimtyperequirements-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<claimTypeRequirements>
  <add claimType="URI"
       isOptional="Boolean" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|claimType|URI définissant le type d'une revendication. Par exemple, pour acheter un produit d'un site Web, l'utilisateur doit présenter une carte de crédit valide avec limite de crédit suffisante. Le type de revendication est l'URI de la carte de crédit.|  
|isOptional|Valeur booléenne indiquant si l'opération concerne une revendication facultative. Affectez à cet attribut la valeur `false` si c'est une revendication requise.<br /><br /> Vous pouvez utiliser cet attribut lorsque le service demande certaines informations sans pour autant les exiger. Par exemple, si vous avez besoin que l’utilisateur entre son prénom, son nom et son adresse, il est préférable de choisir ce numéro de téléphone.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<claimTypeRequirements>](claimtyperequirements-element.md)|Spécifie une collection de types de revendications requis.<br /><br /> Dans un scénario fédéré, les services déclarent les spécifications relatives aux informations d'identification entrantes. Par exemple, ces informations d'identification doivent posséder un jeu de types de revendications défini. Chaque élément de la collection indique les types de revendications requis et facultatifs censés apparaître dans les informations d'identification fédérées.|  
  
## <a name="remarks"></a>Remarques  
 Dans un scénario fédéré, les services déclarent les spécifications relatives aux informations d'identification entrantes. Par exemple, ces informations d'identification doivent posséder un jeu de types de revendications défini. Cette exigence est explicitée dans une stratégie de sécurité. Lorsqu’un client requiert des informations d’identification à partir d’un service fédéré (CardSpace, par exemple), il indique ces exigences dans une demande de jeton (RequestSecurityToken) afin que le service fédéré puisse publier ces informations et répondre aux exigences.  
  
## <a name="example"></a>Exemple  
 La configuration suivante ajoute deux exigences de type de revendication à une liaison de sécurité.  
  
```xml  
<bindings>
  <wsFederationHttpBinding>
    <binding name="myFederatedBinding">
      <security mode="Message">
        <message issuedTokenType="urn:oasis:names:tc:SAML:1.0:assertion">
          <claimTypeRequirements>
            <add claimType="http://schemas.microsoft.com/ws/2005/05/identity/claims/EmailAddress" />
            <add claimType="http://schemas.microsoft.com/ws/2005/05/identity/claims/UserName"
                 optional="true" />
          </claimTypeRequirements>
        </message>
      </security>
    </binding>
  </wsFederationHttpBinding>
</bindings>
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [\<claimTypeRequirements>](claimtyperequirements-element.md)
- [Liaisons](../../../wcf/bindings.md)
- [Extension de liaisons](../../../wcf/extending/extending-bindings.md)
- [Liaisons personnalisées](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [Comment : créer une liaison personnalisée à l’aide de SecurityBindingElement](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [Custom Binding Security](../../../wcf/samples/custom-binding-security.md)
