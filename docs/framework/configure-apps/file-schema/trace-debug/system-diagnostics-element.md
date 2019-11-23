---
title: < l’élément System. Diagnostics >
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.diagnostics
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics
helpviewer_keywords:
- <system.diagnostics> element
- system.diagnostics element
ms.assetid: 3f348f42-fa72-4ff2-aa1c-bb9eecad4bb2
ms.openlocfilehash: dc05c46cb1ba74baceaaeadc2959a6889faf19c9
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699195"
---
# <a name="systemdiagnostics-element"></a>\<l’élément System. Diagnostics >
Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.  
  
[ **\<configuration>** ](../configuration-element.md)  
&nbsp;&nbsp; **\<System. diagnostics >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.diagnostics>   
</system.diagnostics>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributes  
 Aucune.  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<assert>](assert-element.md)|Indique si une boîte de message doit s’afficher quand vous appelez la méthode <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> ; spécifie également le nom du fichier dans lequel écrire les messages.|  
|[\<performanceCounters>](performancecounters-element.md)|Spécifie la taille de la mémoire globale partagée par les compteurs de performances.|  
|[\<sharedListeners>](sharedlisteners-element.md)|Contient des écouteurs auxquels toute source ou tout élément de trace peuvent faire référence. Les écouteurs identifiés comme écouteurs partagés peuvent être ajoutés à des sources ou des suivis par nom.|  
|[\<sources>](sources-element.md)|Spécifie les sources de suivi qui initialisent les messages de suivi.|  
|[\<switches>](switches-element.md)|Contient des commutateurs de trace et les niveaux où les commutateurs de trace sont définis.|  
|[\<trace>](trace-element.md)|Contient les écouteurs qui collectent, stockent et acheminent les messages de traçage.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment incorporer un commutateur de trace et un écouteur de suivi à l’intérieur de l’élément **\<System. diagnostics >** . Le commutateur de trace `General` est défini sur le niveau de <xref:System.Diagnostics.TraceLevel>. L’écouteur de suivi `myListener` crée un fichier nommé `MyListener.log` et écrit la sortie dans le fichier.  
  
> [!NOTE]
> Dans .NET Framework 2.0, vous pouvez spécifier la valeur d'un commutateur avec du texte. Par exemple, vous pouvez spécifier `true` pour une <xref:System.Diagnostics.BooleanSwitch> ou utiliser le texte représentant une valeur d’énumération telle que `Error` pour un <xref:System.Diagnostics.TraceSwitch>. La ligne `<add name="myTraceSwitch" value="Error" />` équivaut à `<add name="myTraceSwitch" value="1" />`.  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <switches>  
         <add name="General" value="4" />  
      </switches>  
      <trace autoflush="true" indentsize="2">  
         <listeners>  
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener, System, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="MyListener.log" traceOutputOptions="ProcessId, LogicalOperationStack, Timestamp, ThreadId, Callstack, DateTime" />  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- [Schéma des paramètres de trace et de débogage](index.md)
