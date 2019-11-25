---
title: <add>
ms.date: 03/30/2017
ms.assetid: 4712a888-f154-4395-8887-ef14a88a6497
author: BrucePerlerMS
ms.openlocfilehash: 83ba51cbbd5100bf7412f9914a270cac88f7faa1
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73973800"
---
# <a name="add"></a>\<add>
Ajoute le gestionnaire de jetons de sécurité spécifié à la collection de gestionnaires de jetons.  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. identityModel >** ](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration**](identityconfiguration.md) >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**securityTokenHandlers**](securitytokenhandlers.md) >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**Ajouter des >**  
  
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
|type|Nom de type CLR du gestionnaire de jetons à ajouter. Pour plus d’informations sur la spécification de l’attribut `type`, consultez [références de types personnalisés](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<samlSecurityTokenRequirement >](samlsecuritytokenrequirement.md)|Fournit la configuration pour la classe <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, la classe <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> ou une classe dérivée de l’une de ces classes.|  
|[\<sessionTokenRequirement >](sessiontokenrequirement.md)|Fournit la configuration pour la classe <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> ou les classes dérivées.|  
|[\<userNameSecurityTokenHandlerRequirement >](usernamesecuritytokenhandlerrequirement.md)|Fournit la configuration pour la classe <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> ou les classes dérivées.|  
|[\<x509SecurityTokenHandlerRequirement >](x509securitytokenhandlerrequirement.md)|Fournit la configuration facultative pour la classe <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> ou les classes dérivées.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<securityTokenHandlers >](securitytokenhandlers.md)|Spécifie une collection de gestionnaires de jetons de sécurité inscrits auprès du point de terminaison.|  
  
## <a name="remarks"></a>Notes  
 L’élément `<add>` peut accepter un élément enfant unique qui spécifie la configuration du gestionnaire de jetons. Cela dépend du fait que la classe de gestionnaire référencée via l’attribut `type` de l’élément `<add>` fournit la prise en charge de cette fonctionnalité. Les classes de gestionnaire de jetons qui fournissent cette fonctionnalité doivent exposer un constructeur qui prend un objet <xref:System.Xml.XmlElement>.  

```csharp  
public class CustomTokenHandler : Microsoft.IdentityModel.Tokens.SecurityTokenHandler  
{  
    public CustomTokenHandler( XmlElement customConfig )  
    {  
    }  
}  
```  
  
 Plusieurs des classes de gestionnaires de jetons de sécurité intégrées offrent cette fonctionnalité. Ces classes sont <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>et <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>.  
  
> [!IMPORTANT]
> La collection de gestionnaires de jetons ne peut contenir qu’un seul gestionnaire d’un type donné. Cela signifie, par exemple, que si vous souhaitez ajouter un gestionnaire dérivé de la classe <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> à la collection, vous devez d’abord supprimer l' <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, qui est présent par défaut, de la collection. Vous pouvez utiliser l’élément [\<remove >](remove.md) pour supprimer un gestionnaire unique de la collection ou utiliser l’élément [\<Clear >](clear.md) pour supprimer tous les gestionnaires de la collection.  
  
 Les paramètres spécifiés sur un gestionnaire substituent les paramètres équivalents spécifiés dans la collection de gestionnaires de jetons sous l’élément [\<securityTokenHandlerConfiguration >](securitytokenhandlerconfiguration.md) et ceux spécifiés au niveau du service sous l’élément [\<identityConfiguration](identityconfiguration.md) .  
  
## <a name="example"></a>Exemple  
 Le code XML suivant montre l’utilisation des éléments `<add>` et `<remove>` pour remplacer le gestionnaire de jetons de session par défaut par un gestionnaire de jetons de session personnalisé. Le code XML provient de l’exemple `ClaimsAwareWebFarm`.  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
