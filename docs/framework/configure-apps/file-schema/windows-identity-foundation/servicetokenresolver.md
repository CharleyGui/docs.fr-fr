---
title: <serviceTokenResolver>
ms.date: 03/30/2017
ms.assetid: 6e9001e1-e064-4f47-84b2-46225c177746
author: BrucePerlerMS
ms.openlocfilehash: 0983380e553acfe246d6b987784d818b8ae85b17
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152578"
---
# \<serviceTokenResolver>
Inscrit le programme de résolution de jetons de service qui est utilisé par les gestionnaires dans la collection de gestionnaires de jetons. Le programme de résolution de jetons de service est utilisé pour résoudre le jeton de chiffrement sur les jetons et les messages entrants.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)\
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
|type|Spécifie le type du programme de résolution de jetons de service. Le <xref:System.IdentityModel.Selectors.SecurityTokenResolver> type ou un type qui dérive de la <xref:System.IdentityModel.Selectors.SecurityTokenResolver> classe. Pour plus d’informations sur la spécification de l' `type` attribut, consultez [références de types personnalisés]. Obligatoire.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucune  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|Fournit la configuration pour une collection de gestionnaires de jetons de sécurité.|  
  
## <a name="remarks"></a>Remarques  
 Le programme de résolution de jetons de service peut être utilisé pour résoudre le jeton de chiffrement sur les jetons et les messages entrants. Il est utilisé pour récupérer la clé qui doit être utilisée pour déchiffrer les jetons entrants. Vous devez spécifier l' `type` attribut. Le type spécifié peut être <xref:System.IdentityModel.Selectors.SecurityTokenResolver> ou un type personnalisé qui dérive de la <xref:System.IdentityModel.Selectors.SecurityTokenResolver> classe.  
  
 Certains gestionnaires de jetons vous permettent de spécifier des paramètres de résolution de jetons de service dans la configuration. Les paramètres sur des gestionnaires de jetons individuels remplacent ceux spécifiés dans la collection de gestionnaires de jetons de sécurité.  
  
> [!NOTE]
> La spécification de l' `<serviceTokenResolver>` élément en tant qu’élément enfant de l' [\<identityConfiguration>](identityconfiguration.md) élément a été dépréciée, mais est toujours prise en charge pour la compatibilité descendante. Les paramètres de l' `<securityTokenHandlerConfiguration>` élément remplacent ceux de l' `<identityConfiguration>` élément.  
  
## <a name="example"></a>Exemple  
  
```xml  
<serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
```
