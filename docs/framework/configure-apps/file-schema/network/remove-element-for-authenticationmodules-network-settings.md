---
title: <remove>, élément d’authenticationModules (paramètres réseau)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/authenticationModules/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- remove element, authenticationModules
- <authenticationModules>, remove element
- <remove> element, authenticationModules
- authenticationModules, remove element
ms.assetid: abf79949-b05c-465a-b51c-bbeda9a74173
ms.openlocfilehash: d171fea193bbae068e69b8976abb8e56a5623f02
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154775"
---
# <a name="remove-element-for-authenticationmodules-network-settings"></a>\<remove>, élément d’authenticationModules (paramètres réseau)
Supprime un module d’authentification de l’application.  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<authenticationModules>**](authenticationmodules-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a>Syntaxe  
  
```xml  
<remove
   type="authentication module name"
/>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|**Attribut**|**Description**|  
|-------------------|---------------------|  
|**type**|Nom du module d’authentification à supprimer.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|**Appartient**|**Description**|  
|-----------------|---------------------|  
|[authenticationModules](authenticationmodules-element-network-settings.md)|Spécifie les modules utilisés pour authentifier les demandes réseau.|  
  
## <a name="remarks"></a>Remarques  
 L' `remove` élément supprime les modules d’authentification qui ont été définis précédemment dans le fichier de configuration ou à un niveau supérieur dans la hiérarchie de configuration.  
  
 La valeur de l' `type` attribut doit être un nom de classe valide.  
  
## <a name="configuration-files"></a>Fichiers de configuration  
 Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant supprime un module d’authentification.  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <remove type="System.Net.NtlmClient" />  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [Schéma des paramètres réseau](index.md)
