---
title: <add>
ms.date: 03/30/2017
ms.assetid: 4712a888-f154-4395-8887-ef14a88a6497
author: BrucePerlerMS
ms.openlocfilehash: 9505970c1fd7fcdfe62d3c6ef58f5d653fab4106
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941991"
---
# <a name="add"></a>\<add>
Ajoute le gestionnaire de jetons de sécurité spécifié à la collection de gestionnaires de jetons.  
  
 \<system.identityModel>  
\<identityConfiguration>  
\<securityTokenHandlers>  
\<add>  
  
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
|type|Nom de type CLR du gestionnaire de jetons à ajouter. Pour plus d’informations sur la spécification de `type` l’attribut, consultez [références de types personnalisés](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<samlSecurityTokenRequirement>](samlsecuritytokenrequirement.md)|Fournit la configuration pour <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> la classe, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> la classe ou une classe dérivée de l’une de ces classes.|  
|[\<sessionTokenRequirement>](sessiontokenrequirement.md)|Fournit la configuration pour <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> la classe ou les classes dérivées.|  
|[\<userNameSecurityTokenHandlerRequirement>](usernamesecuritytokenhandlerrequirement.md)|Fournit la configuration pour <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> la classe ou les classes dérivées.|  
|[\<x509SecurityTokenHandlerRequirement>](x509securitytokenhandlerrequirement.md)|Fournit une configuration facultative pour <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> la classe ou les classes dérivées.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<securityTokenHandlers>](securitytokenhandlers.md)|Spécifie une collection de gestionnaires de jetons de sécurité inscrits auprès du point de terminaison.|  
  
## <a name="remarks"></a>Notes  
 L' `<add>` élément peut accepter un seul élément enfant qui spécifie la configuration du gestionnaire de jetons. Cela dépend du fait que la classe de gestionnaire référencée par `type` l’attribut de `<add>` l’élément assure la prise en charge de cette fonctionnalité. Les classes de gestionnaire de jetons qui fournissent cette fonctionnalité doivent exposer un constructeur <xref:System.Xml.XmlElement> qui prend un objet.  
  
```  
public class CustomTokenHandler : Microsoft.IdentityModel.Tokens.SecurityTokenHandler  
{  
    public CustomTokenHandler( XmlElement customConfig )  
    {  
    }  
}  
```  
  
 Plusieurs des classes de gestionnaires de jetons de sécurité intégrées offrent cette fonctionnalité. Ces classes sont <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> ,<xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>et .<xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>  
  
> [!IMPORTANT]
> La collection de gestionnaires de jetons ne peut contenir qu’un seul gestionnaire d’un type donné. Cela signifie, par exemple, que si vous souhaitez ajouter un gestionnaire dérivé de la <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> classe à la collection, vous devez d’abord supprimer le <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, qui est présent par défaut, à partir de la collection. Vous pouvez utiliser l' [ \<élément remove >](remove.md) pour supprimer un gestionnaire unique de la collection ou utiliser l' [ \<élément clear >](clear.md) pour supprimer tous les gestionnaires de la collection.  
  
 Les paramètres spécifiés sur un gestionnaire substituent les paramètres équivalents spécifiés sur la collection de gestionnaires de jetons sous l' [ \<élément securityTokenHandlerConfiguration >](securitytokenhandlerconfiguration.md) et ceux spécifiés au niveau du service sous le [ \< élément identityConfiguration >](identityconfiguration.md) .  
  
## <a name="example"></a>Exemple  
 Le code XML suivant montre l’utilisation des `<add>` éléments `<remove>` et pour remplacer le gestionnaire de jetons de session par défaut par un gestionnaire de jetons de session personnalisé. Le code XML est extrait de `ClaimsAwareWebFarm` l’exemple.  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
