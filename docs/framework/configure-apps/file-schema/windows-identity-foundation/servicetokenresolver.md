---
title: <serviceTokenResolver>
ms.date: 03/30/2017
ms.assetid: 6e9001e1-e064-4f47-84b2-46225c177746
author: BrucePerlerMS
ms.openlocfilehash: 0983380e553acfe246d6b987784d818b8ae85b17
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152578"
---
# <a name="servicetokenresolver"></a>\<serviceTokenResolver>
Enregistre le résammateur de jetons de service qui est utilisé par les gestionnaires dans la collection de manutention de jetons. Le résolveur de jetons de service est utilisé pour résoudre le jeton de chiffrement sur les jetons et les messages entrants.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identitéConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<sécuritéTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<sécuritéTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceTokenResolver>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <serviceTokenResolver type=xs:string>  
        </serviceTokenResolver>  
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
|type|Spécifie le type de résoutur du jet de service. Soit <xref:System.IdentityModel.Selectors.SecurityTokenResolver> le type ou un type <xref:System.IdentityModel.Selectors.SecurityTokenResolver> qui dérive de la classe. Pour plus d’informations `type` sur la façon de spécifier l’attribut, voir [Références de type personnalisé]. Obligatoire.|  
  
### <a name="child-elements"></a>Éléments enfants  
 None  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<sécuritéTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|Fournit la configuration pour une collection de gestionnaires de jetons de sécurité.|  
  
## <a name="remarks"></a>Notes   
 Le résolveur de jetons de service peut être utilisé pour résoudre le jeton de chiffrement sur les jetons et les messages entrants. Il est utilisé pour récupérer la clé qui doit être utilisée pour déchiffrer les jetons entrants. Vous devez `type` spécifier l’attribut. Le type spécifié <xref:System.IdentityModel.Selectors.SecurityTokenResolver> peut être soit ou un <xref:System.IdentityModel.Selectors.SecurityTokenResolver> type personnalisé qui dérive de la classe.  
  
 Certains gestionnaires de jetons vous permettent de spécifier les paramètres de résolution de jetons de service dans la configuration. Les paramètres des manutentionnaires individuels remplacent ceux spécifiés sur la collection de gestionnaires de jetons de sécurité.  
  
> [!NOTE]
> Spécifier l’élément `<serviceTokenResolver>` comme élément enfant de [ \<l’identitéConfiguration>](identityconfiguration.md) élément a été déprécié, mais est toujours pris en charge pour la compatibilité vers l’arrière. Les paramètres `<securityTokenHandlerConfiguration>` de l’élément `<identityConfiguration>` l’emportent sur ceux de l’élément.  
  
## <a name="example"></a> Exemple  
  
```xml  
<serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
```
