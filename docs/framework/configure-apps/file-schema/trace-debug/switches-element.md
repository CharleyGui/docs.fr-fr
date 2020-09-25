---
title: Élément <switches>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/switches
- http://schemas.microsoft.com/.NetConfiguration/v2.0#switches
helpviewer_keywords:
- <switches> element
- switches element
- trace switches, <switches> element
ms.assetid: 4cf36786-b89a-40e2-a0f1-86bb9b783343
ms.openlocfilehash: bdd6efdec1e118075495002509c7367c1162baba
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91176095"
---
# <a name="switches-element"></a>Élément \<switches>

Contient des commutateurs de traçage et le niveau auquel ils sont définis.  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<switches>**

## <a name="syntax"></a>Syntaxe  
  
```xml  
      <switches>
</switches>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  

 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  

 Aucun.  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<add>](add-element-for-switches.md)|Spécifie le niveau auquel un commutateur de trace est défini.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`System.diagnostics`|Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.|  
  
## <a name="remarks"></a>Notes  

 Vous pouvez modifier le niveau d’un commutateur de trace en le plaçant dans un fichier de configuration. Si le commutateur est un <xref:System.Diagnostics.BooleanSwitch> , vous pouvez l’activer ou le désactiver. Si le commutateur est un <xref:System.Diagnostics.TraceSwitch> , vous pouvez lui affecter différents niveaux pour spécifier les types de messages de trace ou de débogage que l’application génère.  
  
## <a name="example"></a>Exemple  

 L’exemple suivant montre comment utiliser l' **\<switch>** élément pour définir le `General` commutateur de trace sur le <xref:System.Diagnostics.TraceLevel> niveau et activer le `Data` commutateur de trace booléen.  
  
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
