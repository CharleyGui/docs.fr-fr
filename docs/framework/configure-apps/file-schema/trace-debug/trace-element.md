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
ms.openlocfilehash: 02fd794eb7b7b7f46f7f7bc4e43036cb4a4758ed
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699182"
---
# <a name="trace-element"></a>Élément de > de trace \<
Contient les écouteurs qui collectent, stockent et acheminent les messages de traçage.  
  
[ **\<configuration>** ](../configuration-element.md)  
&nbsp;&nbsp;[ **\<System. diagnostics >** ](system-diagnostics-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp; **\<de trace** >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<trace autoflush="true|false"   
       indentsize="indent value"  
       useGlobalLock="true| false"/>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributes  
  
|Attribut|Description|  
|---------------|-----------------|  
|`autoflush`|Attribut facultatif.<br /><br /> Spécifie si les écouteurs de la trace vident automatiquement la mémoire tampon de sortie après chaque opération d’écriture.|  
|`indentsize`|Attribut facultatif.<br /><br /> Spécifie le nombre d’espaces à mettre en retrait.|  
|`useGlobalLock`|Attribut facultatif.<br /><br /> Indique si le verrouillage global doit être utilisé.|  
  
## <a name="autoflush-attribute"></a>Attribut de vidage automatique  
  
|Value|Description|  
|-----------|-----------------|  
|`false`|N’efface pas automatiquement la mémoire tampon de sortie. Il s'agit de la valeur par défaut.|  
|`true`|Vide automatiquement la mémoire tampon de sortie.|  
  
## <a name="usegloballock-attribute"></a>Attribut useGlobalLock  
  
|Value|Description|  
|-----------|-----------------|  
|`false`|N’utilise pas le verrou global si l’écouteur est thread-safe ; dans le cas contraire, utilise le verrou global.|  
|`true`|Utilise le verrou global indépendamment du fait que l’écouteur soit thread-safe. Il s'agit de la valeur par défaut.|  
  
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
 L’exemple suivant montre comment utiliser l’élément `<trace>` pour ajouter l’écouteur `MyListener` à la collection de `Listeners`. `MyListener` crée un fichier nommé `MyListener.log` et écrit la sortie dans le fichier. L’attribut `useGlobalLock` est défini sur `false`, ce qui empêche l’utilisation du verrou global si l’écouteur de la trace est thread-safe. L’attribut `autoflush` est défini sur `true`, ce qui entraîne l’écriture de l’écouteur de la trace dans le fichier, que la méthode <xref:System.Diagnostics.Trace.Flush%2A?displayProperty=nameWithType> soit appelée ou non. L’attribut `indentsize` a la valeur 0 (zéro), ce qui amène l’écouteur à mettre en retrait les espaces nuls lorsque la méthode <xref:System.Diagnostics.Trace.Indent%2A?displayProperty=nameWithType> est appelée.  
  
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
- [Schéma des paramètres de trace et de débogage](index.md)
