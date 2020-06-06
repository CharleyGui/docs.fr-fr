---
title: <issuerTokenResolver>
ms.date: 03/30/2017
ms.assetid: f74392f6-3f5b-4880-bd8a-3a9130d31e65
author: BrucePerlerMS
ms.openlocfilehash: 67d7e0aa5b6b05bfe8b17a1b1efebb1fbddbb0eb
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152669"
---
# \<issuerTokenResolver>
Inscrit le programme de résolution de jetons d’émetteur utilisé par les gestionnaires dans la collection de gestionnaires de jetons. Le programme de résolution de jetons d’émetteur est utilisé pour résoudre le jeton de signature sur les jetons et les messages entrants.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuerTokenResolver>**  
  
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
|type|Spécifie le type de programme de résolution de jetons d’émetteur. Il doit s’agir de la <xref:System.IdentityModel.Tokens.IssuerTokenResolver> classe ou d’un type qui dérive de la <xref:System.IdentityModel.Tokens.IssuerTokenResolver> classe. Obligatoire.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucune  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|Fournit la configuration pour une collection de gestionnaires de jetons de sécurité.|  
  
## <a name="remarks"></a>Remarques  
 Le programme de résolution de jetons d’émetteur est utilisé pour résoudre le jeton de signature sur les jetons et les messages entrants. Il est utilisé pour récupérer le matériel de chiffrement utilisé pour vérifier la signature. Vous devez spécifier l' `type` attribut. Le type spécifié peut être <xref:System.IdentityModel.Tokens.IssuerTokenResolver> ou un type personnalisé qui dérive de la <xref:System.IdentityModel.Tokens.IssuerTokenResolver> classe.  
  
 Certains gestionnaires de jetons vous permettent de spécifier les paramètres du programme de résolution de jetons d’émetteur dans la configuration. Les paramètres sur des gestionnaires de jetons individuels remplacent ceux spécifiés dans la collection de gestionnaires de jetons de sécurité.  
  
> [!NOTE]
> La spécification de l' `<issuerTokenResolver>` élément en tant qu’élément enfant de l' [\<identityConfiguration>](identityconfiguration.md) élément a été dépréciée, mais est toujours prise en charge pour la compatibilité descendante. Les paramètres de l' `<securityTokenHandlerConfiguration>` élément remplacent ceux de l' `<identityConfiguration>` élément.  
  
## <a name="example"></a>Exemple  
 Le code XML suivant montre la configuration d’un programme de résolution de jetons d’émetteur basé sur une classe personnalisée qui dérive de <xref:System.IdentityModel.Tokens.IssuerTokenResolver> . Le programme de résolution de jetons gère un dictionnaire de paires de clés d’audience qui est initialisé à partir d’un élément de configuration personnalisé ( `<AddAudienceKeyPair>` ) défini pour la classe. La classe substitue la <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> méthode pour traiter cet élément. Le remplacement est illustré dans l’exemple suivant : Toutefois, les méthodes qu’il appelle ne sont pas affichées par souci de concision. Pour obtenir un exemple complet, consultez l’exemple `CustomToken` .  
  
```xml  
<issuerTokenResolver type="SimpleWebToken.CustomIssuerTokenResolver, SimpleWebToken">  
  <AddAudienceKeyPair  symmetricKey="wAVkldQiFypTQ+kdNdGWCYCHRcee8XmXxOvgmak8vSY=" audience="http://localhost:19851/" />  
</issuerTokenResolver>  
```  
  
## <a name="example"></a>Exemple
  
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
