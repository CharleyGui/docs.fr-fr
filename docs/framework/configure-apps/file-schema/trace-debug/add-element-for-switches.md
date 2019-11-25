---
title: Élément <add> pour <switches>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/switches/add
helpviewer_keywords:
- <add> element for <switches>
- add element for <switches>
ms.assetid: 712ac3a7-7abf-4a9e-8db4-acd241c2f369
ms.openlocfilehash: db2de681227dfdb7420808963219b9f52381f8fe
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088958"
---
# <a name="add-element-for-switches"></a>\<ajoutez > élément pour les commutateurs \<
Spécifie le niveau auquel un commutateur de trace est défini.  

[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. diagnostics >** ](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**commutateurs**](switches-element.md)\<
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**ajouter >**

## <a name="syntax"></a>Syntaxe  
  
```xml  
<add name="switch name"  
     value="value"/>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|**name**|Attribut requis.<br /><br /> Spécifie le nom du commutateur. La valeur de cet attribut correspond au paramètre *DisplayName* passé au constructeur de commutateur.|  
|**valeur**|Attribut requis.<br /><br /> Spécifie le niveau du commutateur.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun(e).  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`switches`|Contient des commutateurs de traçage et le niveau auquel ils sont définis.|  
|`system.diagnostics`|Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.|  
  
## <a name="remarks"></a>Notes  
 Vous pouvez modifier le niveau d’un commutateur de trace en le plaçant dans un fichier de configuration. Si le commutateur est un <xref:System.Diagnostics.BooleanSwitch>, vous pouvez l’activer et le désactiver. Si le commutateur est un <xref:System.Diagnostics.TraceSwitch>, vous pouvez lui affecter différents niveaux pour spécifier les types de messages de trace ou de débogage que l’application génère.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser la **\<ajouter >** élément pour définir le commutateur de trace `General` au niveau de la <xref:System.Diagnostics.TraceLevel> et activer le commutateur de trace booléen `Data`.  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <switches>  
         <add name="General" value="4" />  
         <add name="Data" value="1" />  
      </switches>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Diagnostics.Switch>
- <xref:System.Diagnostics.TraceSwitch>
- <xref:System.Diagnostics.BooleanSwitch>
- [Schéma des paramètres de trace et de débogage](index.md)
