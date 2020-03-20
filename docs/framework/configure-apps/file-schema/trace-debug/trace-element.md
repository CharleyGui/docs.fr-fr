---
title: Élément <trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace
- http://schemas.microsoft.com/.NetConfiguration/v2.0#trace
helpviewer_keywords:
- <trace> element
- listeners
- trace element
- trace listener, <trace> element
ms.assetid: 7931c942-63c1-47c3-a045-9d9de3cacdbf
ms.openlocfilehash: 7d8a989219d84e8604e767456c84c0092bc73b22
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153164"
---
# <a name="trace-element"></a>\<trace> Élément
Contient les écouteurs qui collectent, stockent et acheminent les messages de traçage.  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<trace>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<trace autoflush="true|false"
       indentsize="indent value"  
       useGlobalLock="true| false"/>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`autoflush`|Attribut facultatif.<br /><br /> Précise si les auditeurs trace automatiquement rincer le tampon de sortie après chaque opération d’écriture.|  
|`indentsize`|Attribut facultatif.<br /><br /> Spécifie le nombre d’espaces à en retrait.|  
|`useGlobalLock`|Attribut facultatif.<br /><br /> Indique si le verrou global doit être utilisé.|  
  
## <a name="autoflush-attribute"></a>Attribut autoflush  
  
|Valeur|Description|  
|-----------|-----------------|  
|`false`|Ne chasse pas automatiquement le tampon de sortie. Il s’agit de la valeur par défaut.|  
|`true`|Rincer automatiquement le tampon de sortie.|  
  
## <a name="usegloballock-attribute"></a>utilisationGlobalLock Attribut  
  
|Valeur|Description|  
|-----------|-----------------|  
|`false`|N’utilise pas le verrou global si l’auditeur est sans danger de thread; autrement, utilise le verrou global.|  
|`true`|Utilise le verrou global indépendamment du fait que l’auditeur soit sans danger pour le thread. Il s’agit de la valeur par défaut.|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<auditeurs>](listeners-element-for-trace.md)|Spécifie un auditeur qui recueille, stocke et achemine les messages.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`system.diagnostics`|Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.|  
  
## <a name="example"></a> Exemple  
 L’exemple suivant montre `<trace>` comment utiliser l’élément pour ajouter l’auditeur `MyListener` à la `Listeners` collection. `MyListener`crée un fichier `MyListener.log` qui est nommé et écrit la sortie au fichier. L’attribut `useGlobalLock` est `false`défini à , ce qui provoque la serrure globale de ne pas être utilisé si l’auditeur trace est thread safe. L’attribut `autoflush` est `true`défini à , ce qui provoque l’auditeur <xref:System.Diagnostics.Trace.Flush%2A?displayProperty=nameWithType> trace d’écrire au fichier indépendamment du fait que la méthode est appelée. L’attribut `indentsize` est réglé à 0 (zéro), ce qui provoque <xref:System.Diagnostics.Trace.Indent%2A?displayProperty=nameWithType> l’auditeur à l’auditeur à l’indent zéro espace lorsque la méthode est appelée.  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <trace useGlobalLock="false" autoflush="true" indentsize="0">  
         <listeners>  
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener, system version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="c:\myListener.log" />  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- [Trace et Debug Paramètres Schema](index.md)
