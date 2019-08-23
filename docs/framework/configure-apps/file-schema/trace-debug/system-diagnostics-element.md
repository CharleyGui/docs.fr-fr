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
ms.openlocfilehash: f3b4238a8d7028d47122a420526b38ee4f327332
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926946"
---
# <a name="systemdiagnostics-element"></a>\<System. Diagnostics, élément >
Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.  
  
 \<configuration>  
\<system.diagnostics>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.diagnostics>   
</system.diagnostics>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
 Aucun.  
  
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
 L’exemple suivant montre comment incorporer un commutateur de trace et un écouteur de suivi à l’intérieur de l'  **\<élément System. Diagnostics >** . Le commutateur de <xref:System.Diagnostics.TraceLevel> traceestdéfini`General` sur le niveau. L’écouteur `myListener` de suivi crée un fichier `MyListener.log` nommé et écrit la sortie dans le fichier.  
  
> [!NOTE]
> Dans .NET Framework 2.0, vous pouvez spécifier la valeur d'un commutateur avec du texte. Par exemple, vous pouvez spécifier `true` pour un <xref:System.Diagnostics.BooleanSwitch> ou utiliser le texte représentant `Error` une valeur d’énumération comme pour <xref:System.Diagnostics.TraceSwitch>un. La ligne `<add name="myTraceSwitch" value="Error" />` équivaut à `<add name="myTraceSwitch" value="1" />`.  
  
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
