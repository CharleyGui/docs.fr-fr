---
title: Élément <assert>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/assert
- http://schemas.microsoft.com/.NetConfiguration/v2.0#assert
helpviewer_keywords:
- <assert> element
- assert element
ms.assetid: ef4c3229-b151-4d85-8091-e6456af9b935
ms.openlocfilehash: f3c1a1670139a8262dea449bfff99c7c1c19f088
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74088944"
---
# <a name="assert-element"></a>Élément \<assert>
Indique si une boîte de message doit s’afficher quand vous appelez la méthode <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> ; spécifie également le nom du fichier dans lequel écrire les messages.  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<assert>**

## <a name="syntax"></a>Syntaxe  
  
```xml  
<assert assertuienabled="true|false" logfilename="file name"/>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`assertuienabled`|Attribut facultatif.<br /><br /> Spécifie s’il faut afficher une boîte de message lorsque la méthode **Debug. Assert** prend la **valeur false**.|  
|`logfilename`|Attribut facultatif.<br /><br /> Spécifie le nom du fichier dans lequel le message doit être écrit si **Debug. Assert** prend la **valeur false**.|  
  
## <a name="assertuienabled-attribute"></a>Attribut AssertUiEnabled  
  
|Valeur|Description|  
|-----------|-----------------|  
|`true`|Affiche la boîte de message. Il s'agit de la valeur par défaut.|  
|`false`|N’affiche pas la boîte de message.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`system.diagnostics`|Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.|  
  
## <a name="remarks"></a>Remarques  
 Les deux attributs de l' **\<assert>** élément sont facultatifs. Vous pouvez désactiver les boîtes de message sans spécifier de fichier dans lequel écrire les messages, ou vous pouvez spécifier un fichier dans lequel écrire les messages tout en laissant les boîtes de message activées.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment désactiver l’affichage des boîtes de message lorsque vous appelez **Debug. Assert** et écrire les messages dans `c:\log.txt` .  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <assert assertuienabled="false" logfilename="c:\log.txt"/>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Diagnostics.Debug>
- [Schéma des paramètres de traçage et de débogage](index.md)
