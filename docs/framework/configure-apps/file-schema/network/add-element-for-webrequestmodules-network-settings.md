---
title: <add>, élément de webRequestModules (paramètres réseau)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules/add
- http://schemas.microsoft.com/.NetConfiguration/v2.0#add
helpviewer_keywords:
- <webRequestModules>, add element
- webRequestModules, add element
- add element, webRequestModules
- <add> element, webRequestModules
ms.assetid: 47ec4adc-f39f-4bcd-8680-1ec21fd26890
ms.openlocfilehash: f4edce948033478aab59a2aff61abadc55a327ce
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155022"
---
# <a name="add-element-for-webrequestmodules-network-settings"></a>\<ajouter> Element pour webRequestModules (Paramètres réseau)
Ajoute un module de demande Web personnalisé à l’application.  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<webRequestModules>**](webrequestmodules-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<ajouter>**

## <a name="syntax"></a>Syntaxe  
  
```xml  
<add
  prefix="URI prefix"
  type="type_fullname, assembly_fullname"
/>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|**Attribut**|**Description**|  
|-------------------|---------------------|  
|`prefix`|Le préfixe URI pour les demandes traitées par ce module de demande Web.|  
|`type`|Le nom de type entièrement <xref:System.Type.FullName%2A> qualifié (indiqué par la <xref:System.Reflection.Assembly.FullName%2A> propriété) et le nom d’assemblage (indiqué par la propriété), séparés par une virgule, qui implémente ce module de demande Web.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|**Élément**|**Description**|  
|-----------------|---------------------|  
|[webRequestModules](webrequestmodules-element-network-settings.md)|Spécifie les modules à utiliser pour demander des informations aux hôtes du réseau.|  
  
## <a name="remarks"></a>Notes   
 L’attribut `prefix` définit le préfixe URI qui utilise le module de demande Web spécifié. Les modules de demande Web sont généralement enregistrés pour gérer un protocole spécifique, tel que HTTP ou FTP, mais peuvent être enregistrés pour traiter une demande à un serveur ou un chemin spécifique sur un serveur.  
  
 Le module de demande Web est créé lorsqu’un <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> préfixe URI correspondant est transmis à la méthode.  
  
 La valeur `prefix` de l’attribut doit être les personnages principaux d’une URI valide. Par exemple, `http` ou `http://www.contoso.com`.
  
 La valeur `type` de l’attribut doit être un nom de type valide et un nom d’assemblage correspondant, séparé par une virgule.
  
## <a name="configuration-files"></a>Fichiers de configuration  
 Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).  
  
## <a name="example"></a> Exemple  
 L’exemple suivant enregistre un module de demande Web personnalisé pour HTTP. Vous devez remplacer les valeurs de Version et PublicKeyToken par les valeurs correctes pour le module spécifié.  
  
```xml  
<configuration>  
  <system.net>  
    <webRequestModules>  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator, System, Version=2.0.3600.0,  
           Culture=neutral, PublicKeyToken=b77a5c561934e089"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Net.WebRequest>
- [Paramètres réseau Schema](index.md)
