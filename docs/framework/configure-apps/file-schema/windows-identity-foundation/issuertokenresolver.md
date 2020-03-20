---
title: <issuerTokenResolver>
ms.date: 03/30/2017
ms.assetid: f74392f6-3f5b-4880-bd8a-3a9130d31e65
author: BrucePerlerMS
ms.openlocfilehash: 67d7e0aa5b6b05bfe8b17a1b1efebb1fbddbb0eb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152669"
---
# <a name="issuertokenresolver"></a>\<émetteurTokenResolver>
Enregistre le résa résolveur de jetons de l’émetteur qui est utilisé par les gestionnaires dans la collection de gestionnaires de jetons. Le résolveur de jetons de l’émetteur est utilisé pour résoudre le jeton de signature sur les jetons entrants et les messages.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identitéConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<sécuritéTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<sécuritéTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<émetteurTokenResolver>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <issuerTokenResolver type=xs:string>  
        </issuerTokenResolver>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|type|Spécifie le type de résouteur de jetons de l’émetteur. Doit être <xref:System.IdentityModel.Tokens.IssuerTokenResolver> soit la classe ou un <xref:System.IdentityModel.Tokens.IssuerTokenResolver> type qui dérive de la classe. Obligatoire.|  
  
### <a name="child-elements"></a>Éléments enfants  
 None  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<sécuritéTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|Fournit la configuration pour une collection de gestionnaires de jetons de sécurité.|  
  
## <a name="remarks"></a>Notes   
 Le résolveur de jetons de l’émetteur est utilisé pour résoudre le jeton de signature sur les jetons entrants et les messages. Il est utilisé pour récupérer le matériel cryptographique qui est utilisé pour vérifier la signature. Vous devez `type` spécifier l’attribut. Le type spécifié <xref:System.IdentityModel.Tokens.IssuerTokenResolver> peut être soit ou un <xref:System.IdentityModel.Tokens.IssuerTokenResolver> type personnalisé qui dérive de la classe.  
  
 Certains gestionnaires de jetons vous permettent de spécifier les paramètres de résolution de jetons de l’émetteur dans la configuration. Les paramètres des manutentionnaires individuels remplacent ceux spécifiés sur la collection de gestionnaires de jetons de sécurité.  
  
> [!NOTE]
> Spécifier l’élément `<issuerTokenResolver>` comme élément enfant de [ \<l’identitéConfiguration>](identityconfiguration.md) élément a été déprécié, mais est toujours pris en charge pour la compatibilité vers l’arrière. Les paramètres `<securityTokenHandlerConfiguration>` de l’élément `<identityConfiguration>` l’emportent sur ceux de l’élément.  
  
## <a name="example"></a> Exemple  
 Le XML suivant affiche la configuration d’un résolveur de jetons <xref:System.IdentityModel.Tokens.IssuerTokenResolver>d’émetteur qui est basé sur une classe personnalisée qui dérive de . Le résolveur de jetons maintient un dictionnaire de paires d’audience-clé qui est parascé à partir d’un élément de configuration personnalisé (`<AddAudienceKeyPair>`) défini pour la classe. La classe l’emporte sur la <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> méthode pour traiter cet élément. La dérogation est illustrée dans l’exemple suivant; cependant, les méthodes qu’il appelle ne sont pas indiquées pour la brièveté. Pour l’exemple complet, voir l’échantillon. `CustomToken`  
  
```xml  
<issuerTokenResolver type="SimpleWebToken.CustomIssuerTokenResolver, SimpleWebToken">  
  <AddAudienceKeyPair  symmetricKey="wAVkldQiFypTQ+kdNdGWCYCHRcee8XmXxOvgmak8vSY=" audience="http://localhost:19851/" />  
</issuerTokenResolver>  
```  
  
## <a name="example"></a> Exemple
  
```csharp
public override void LoadCustomConfiguration(System.Xml.XmlNodeList nodelist)  
{  
    foreach (XmlNode node in nodelist)  
    {  
        XmlDictionaryReader rdr = XmlDictionaryReader.CreateDictionaryReader(new XmlTextReader(new StringReader(node.OuterXml)));  
        rdr.MoveToContent();  
  
        string symmetricKey = rdr.GetAttribute("symmetricKey");  
        string audience = rdr.GetAttribute("audience");  
  
        this.AddAudienceKeyPair(audience, symmetricKey);  
    }  
}  
```
  
## <a name="see-also"></a>Voir aussi

- <xref:System.IdentityModel.Tokens.IssuerTokenResolver>
