---
title: <system.diagnostics> Element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.diagnostics
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics
helpviewer_keywords:
- <system.diagnostics> element
- system.diagnostics element
ms.assetid: 3f348f42-fa72-4ff2-aa1c-bb9eecad4bb2
ms.openlocfilehash: 4f831592d7d178276b1625e1ef7d8512085342af
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153205"
---
# <a name="systemdiagnostics-element"></a>\<system.diagnostics> Element
Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<system.diagnostics>**  
  
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
|[\<affirmer>](assert-element.md)|Indique si une boîte de message doit s’afficher quand vous appelez la méthode <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> ; spécifie également le nom du fichier dans lequel écrire les messages.|  
|[\<performanceCompers>](performancecounters-element.md)|Spécifie la taille de la mémoire globale partagée par les compteurs de performances.|  
|[\<sharedListeners>](sharedlisteners-element.md)|Contient des écouteurs auxquels toute source ou tout élément de trace peuvent faire référence. Les auditeurs identifiés comme des auditeurs partagés peuvent être ajoutés à des sources ou des traces par leur nom.|  
|[\<sources>](sources-element.md)|Spécifie les sources de traces qui déclenchent des messages de traçage.|  
|[\<commutateurs>](switches-element.md)|Contient des interrupteurs de trace et les niveaux où les commutateurs de trace sont réglés.|  
|[\<trace>](trace-element.md)|Contient les écouteurs qui collectent, stockent et acheminent les messages de traçage.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
  
## <a name="example"></a> Exemple  
 L’exemple suivant montre comment intégrer un interrupteur de trace et un auditeur de trace à l’intérieur du ** \<système.diagnostics>** élément. Le `General` commutateur de trace <xref:System.Diagnostics.TraceLevel> est réglé au niveau. L’auditeur `myListener` de traces `MyListener.log` crée un fichier appelé et écrit la sortie au fichier.  
  
> [!NOTE]
> Dans .NET Framework 2.0, vous pouvez spécifier la valeur d'un commutateur avec du texte. Par exemple, vous `true` pouvez <xref:System.Diagnostics.BooleanSwitch> spécifier pour un ou `Error` utiliser <xref:System.Diagnostics.TraceSwitch>le texte représentant une valeur de recensement telle que pour un . La ligne `<add name="myTraceSwitch" value="Error" />` équivaut à `<add name="myTraceSwitch" value="1" />`.  
  
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
- [Trace et Debug Paramètres Schema](index.md)
