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
ms.openlocfilehash: 0248706ed78de160ef0131a0c7595374febf1aa9
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699589"
---
# <a name="add-element-for-webrequestmodules-network-settings"></a>\<add > élément de webRequestModules (paramètres réseau)
Ajoute un module de demande Web personnalisé à l’application.  
  
[ **\<configuration>** ](../configuration-element.md)  
&nbsp; @ no__t-1[ **@no__t -4System. net >** ](system-net-element-network-settings.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<webRequestModules >** ](webrequestmodules-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Ajouter >**  
  
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
|`prefix`|Préfixe URI pour les requêtes gérées par ce module de demande Web.|  
|`type`|Le nom de type qualifié complet (indiqué par la propriété <xref:System.Type.FullName%2A>) et le nom de l’assembly (indiqué par la propriété <xref:System.Reflection.Assembly.FullName%2A>), séparés par une virgule, qui implémente ce module de demande Web.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|**Élément**|**Description**|  
|-----------------|---------------------|  
|[webRequestModules](webrequestmodules-element-network-settings.md)|Spécifie les modules à utiliser pour demander des informations à des hôtes réseau.|  
  
## <a name="remarks"></a>Notes  
 L’attribut `prefix` définit le préfixe URI qui utilise le module de demande Web spécifié. Les modules de demande Web sont généralement enregistrés pour gérer un protocole spécifique, tel que HTTP ou FTP, mais peuvent être inscrits pour gérer une demande à un serveur ou à un chemin d’accès spécifique sur un serveur.  
  
 Le module de demande Web est créé lorsqu’un préfixe d’URI correspondant est passé à la méthode <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType>.  
  
 La valeur de l’attribut `prefix` doit être celle des caractères de début d’un URI valide. Par exemple, `http` ou `http://www.contoso.com`.
  
 La valeur de l’attribut `type` doit être un nom de type valide et le nom d’assembly correspondant, séparés par une virgule.
  
## <a name="configuration-files"></a>Fichiers de configuration  
 Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant inscrit un module de demande Web personnalisé pour HTTP. Vous devez remplacer les valeurs de version et PublicKeyToken par les valeurs correctes pour le module spécifié.  
  
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
- [Schéma des paramètres réseau](index.md)
