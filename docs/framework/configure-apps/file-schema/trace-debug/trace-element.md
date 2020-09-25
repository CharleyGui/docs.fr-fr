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
ms.openlocfilehash: 617b42a0be2be272a78b33be997cce632d1c6dcb
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198923"
---
# <a name="trace-element"></a>Élément \<trace>

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
|`autoflush`|Attribut facultatif.<br /><br /> Spécifie si les écouteurs de la trace vident automatiquement la mémoire tampon de sortie après chaque opération d’écriture.|  
|`indentsize`|Attribut facultatif.<br /><br /> Spécifie le nombre d’espaces à mettre en retrait.|  
|`useGlobalLock`|Attribut facultatif.<br /><br /> Indique si le verrouillage global doit être utilisé.|  
  
## <a name="autoflush-attribute"></a>Attribut de vidage automatique  
  
|Valeur|Description|  
|-----------|-----------------|  
|`false`|N’efface pas automatiquement la mémoire tampon de sortie. Il s’agit de la valeur par défaut.|  
|`true`|Vide automatiquement la mémoire tampon de sortie.|  
  
## <a name="usegloballock-attribute"></a>Attribut useGlobalLock  
  
|Valeur|Description|  
|-----------|-----------------|  
|`false`|N’utilise pas le verrou global si l’écouteur est thread-safe ; dans le cas contraire, utilise le verrou global.|  
|`true`|Utilise le verrou global indépendamment du fait que l’écouteur soit thread-safe. Il s’agit de la valeur par défaut.|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<listeners>](listeners-element-for-trace.md)|Spécifie un écouteur qui collecte, stocke et achemine des messages.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`system.diagnostics`|Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.|  
  
## <a name="example"></a>Exemple  

 L’exemple suivant montre comment utiliser l' `<trace>` élément pour ajouter l’écouteur `MyListener` à la `Listeners` collection. `MyListener` crée un fichier nommé `MyListener.log` et écrit la sortie dans le fichier. L' `useGlobalLock` attribut a la valeur `false` , ce qui empêche l’utilisation du verrou global si l’écouteur de la trace est thread-safe. L' `autoflush` attribut a la valeur `true` , ce qui amène l’écouteur de la trace à écrire dans le fichier, que la <xref:System.Diagnostics.Trace.Flush%2A?displayProperty=nameWithType> méthode soit appelée ou non. L' `indentsize` attribut a la valeur 0 (zéro), ce qui amène l’écouteur à mettre en retrait les espaces nuls lorsque la <xref:System.Diagnostics.Trace.Indent%2A?displayProperty=nameWithType> méthode est appelée.  
  
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
- [Schéma des paramètres de traçage et de débogage](index.md)
