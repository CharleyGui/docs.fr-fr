---
title: <audienceUris>
ms.date: 03/30/2017
ms.assetid: 7a3d8515-d756-4afe-a22d-07cbe2217ee3
author: BrucePerlerMS
ms.openlocfilehash: bd04e4ebdf5c58adaeea0ff0ca5993d7d9ce38f1
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252168"
---
# <a name="audienceuris"></a>\<audienceUris>
Spécifie l’ensemble d’URI qui sont des identificateurs acceptables de la partie de confiance (RP). Les jetons ne sont pas acceptés, sauf s’ils sont étendus à l’un des URI d’audience autorisés.  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. identityModel >** ](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlers >** ](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlerConfiguration >** ](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<audienceUris >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <audienceUris mode=xs:string>  
          <add value=xs:string />  
          <clear />  
          <remove value=xs:string />  
        </audienceUris>  
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
|mode|<xref:System.IdentityModel.Selectors.AudienceUriMode> Valeur qui spécifie si la restriction de l’audience doit être appliquée à un jeton entrant. Les valeurs possibles sont « Always », « Never » et « BearerKeyOnly ». La valeur par défaut est « Always ». facultatif.|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|`<add value=xs:string>`|Ajoute l’URI spécifié par l' `value` attribut à la collection audienceUris. L'attribut `value` est obligatoire. L’URI respecte la casse.|  
|`<clear>`|Efface la collection audienceUris. Tous les identificateurs sont supprimés de la collection.|  
|`<remove value=xs:string>`|Supprime l’URI spécifié par l' `value` attribut de la collection audienceUris. L'attribut `value` est obligatoire. L’URI respecte la casse.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|Fournit la configuration pour une collection de gestionnaires de jetons de sécurité.|  
  
## <a name="remarks"></a>Notes  
 Par défaut, la collection est vide ; Utilisez `<add>`les `<clear>`éléments, `<remove>` et pour modifier la collection. <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>les <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> objets et utilisent les valeurs de la collection d’URI d’audience pour configurer toutes les restrictions <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> d’URI d’audience autorisées dans les objets.  
  
 L' `<audienceUris>` élément est représenté par la <xref:System.IdentityModel.Configuration.AudienceUriElementCollection> classe. Un URI individuel ajouté à la collection est représenté par la <xref:System.IdentityModel.Configuration.AudienceUriElement> classe.  
  
> [!NOTE]
> L’utilisation de l' `<audienceUris>` élément en tant qu’élément enfant de l' [ \<élément identityConfiguration >](identityconfiguration.md) a été dépréciée, mais est toujours prise en charge pour la compatibilité descendante. Les paramètres de `<securityTokenHandlerConfiguration>` l’élément remplacent ceux de `<identityConfiguration>` l’élément.  
  
## <a name="example"></a>Exemple  
 Le code XML suivant montre comment configurer les URI d’audience acceptables pour une application. Cet exemple configure un seul URI. Les jetons dont la portée est limitée à cet URI seront acceptés, tous les autres seront rejetés.  
  
```xml  
<audienceUris>  
  <add value="http://localhost:19851/"/>  
</audienceUris>  
```
