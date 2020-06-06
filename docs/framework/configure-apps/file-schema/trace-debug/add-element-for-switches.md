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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74088958"
---
# <a name="add-element-for-switches"></a>\<add>, élément de \<switches>
Spécifie le niveau auquel un commutateur de trace est défini.  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<switches>**](switches-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

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
|**value**|Attribut requis.<br /><br /> Spécifie le niveau du commutateur.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`switches`|Contient des commutateurs de traçage et le niveau auquel ils sont définis.|  
|`system.diagnostics`|Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.|  
  
## <a name="remarks"></a>Remarques  
 Vous pouvez modifier le niveau d’un commutateur de trace en le plaçant dans un fichier de configuration. Si le commutateur est un <xref:System.Diagnostics.BooleanSwitch> , vous pouvez l’activer ou le désactiver. Si le commutateur est un <xref:System.Diagnostics.TraceSwitch> , vous pouvez lui affecter différents niveaux pour spécifier les types de messages de trace ou de débogage que l’application génère.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser l' **\<add>** élément pour définir le `General` commutateur de trace sur le <xref:System.Diagnostics.TraceLevel> niveau et activer le `Data` commutateur de trace booléen.  
  
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
- [Schéma des paramètres de traçage et de débogage](index.md)
