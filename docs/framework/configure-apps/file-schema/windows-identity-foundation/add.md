---
title: <add>
ms.date: 03/30/2017
ms.assetid: 4712a888-f154-4395-8887-ef14a88a6497
author: BrucePerlerMS
ms.openlocfilehash: 7c2b6bdc62da63905d7ff33a9984808e7b7d114f
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90544538"
---
# \<add>
Ajoute le gestionnaire de jetons de sécurité spécifié à la collection de gestionnaires de jetons.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add type=xs:string>  
        <optionalConfigurationElement>  
        </optionalConfigurationElement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|type|Nom de type CLR du gestionnaire de jetons à ajouter. Pour plus d’informations sur la spécification de l' `type` attribut, consultez [références de types personnalisés](/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<samlSecurityTokenRequirement>](samlsecuritytokenrequirement.md)|Fournit la configuration pour la <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> classe, la <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> classe ou une classe dérivée de l’une de ces classes.|  
|[\<sessionTokenRequirement>](sessiontokenrequirement.md)|Fournit la configuration pour la <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> classe ou les classes dérivées.|  
|[\<userNameSecurityTokenHandlerRequirement>](usernamesecuritytokenhandlerrequirement.md)|Fournit la configuration pour la <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> classe ou les classes dérivées.|  
|[\<x509SecurityTokenHandlerRequirement>](x509securitytokenhandlerrequirement.md)|Fournit une configuration facultative pour la <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> classe ou les classes dérivées.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<securityTokenHandlers>](securitytokenhandlers.md)|Spécifie une collection de gestionnaires de jetons de sécurité inscrits auprès du point de terminaison.|  
  
## <a name="remarks"></a>Notes  
 L' `<add>` élément peut accepter un seul élément enfant qui spécifie la configuration du gestionnaire de jetons. Cela dépend du fait que la classe de gestionnaire référencée par l' `type` attribut de l' `<add>` élément assure la prise en charge de cette fonctionnalité. Les classes de gestionnaire de jetons qui fournissent cette fonctionnalité doivent exposer un constructeur qui prend un <xref:System.Xml.XmlElement> objet.  

```csharp  
public class CustomTokenHandler : Microsoft.IdentityModel.Tokens.SecurityTokenHandler  
{  
    public CustomTokenHandler( XmlElement customConfig )  
    {  
    }  
}  
```  
  
 Plusieurs des classes de gestionnaires de jetons de sécurité intégrées offrent cette fonctionnalité. Ces classes sont <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> , <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> , <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> , <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> et <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> .  
  
> [!IMPORTANT]
> La collection de gestionnaires de jetons ne peut contenir qu’un seul gestionnaire d’un type donné. Cela signifie, par exemple, que si vous souhaitez ajouter un gestionnaire dérivé de la <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> classe à la collection, vous devez d’abord supprimer le <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> , qui est présent par défaut, à partir de la collection. Vous pouvez utiliser l' [\<remove>](remove.md) élément pour supprimer un gestionnaire unique de la collection ou utiliser l' [\<clear>](clear.md) élément pour supprimer tous les gestionnaires de la collection.  
  
 Les paramètres spécifiés sur un gestionnaire substituent les paramètres équivalents spécifiés dans la collection de gestionnaires de jetons sous l' [\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md) élément et ceux spécifiés au niveau du service sous l' [\<identityConfiguration>](identityconfiguration.md) élément.  
  
## <a name="example"></a> Exemple  
 Le code XML suivant montre l’utilisation des `<add>` `<remove>` éléments et pour remplacer le gestionnaire de jetons de session par défaut par un gestionnaire de jetons de session personnalisé. Le code XML est extrait de l' `ClaimsAwareWebFarm` exemple.  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
