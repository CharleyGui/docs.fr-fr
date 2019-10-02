---
title: Élément <clear> pour <listeners> pour <trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/clear
helpviewer_keywords:
- clear element for <listeners> for <trace>
- <clear> element for <listeners> for <trace>
ms.assetid: b44732a8-271f-4a06-ba9e-fe3298d6f192
ms.openlocfilehash: 0361580724351f8f42d058d5e20354e3335bac2f
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699377"
---
# <a name="clear-element-for-listeners-for-trace"></a>\<clear > élément de \<listeners > pour \<trace >
Efface la collection `Listeners` de la trace.  
  
[ **\<configuration>** ](../configuration-element.md)  
&nbsp; @ no__t-1[ **\<System. diagnostics >** ](system-diagnostics-element.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<trace >** ](trace-element.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5[ **\<listeners >** ](listeners-element-for-trace.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7 **\<clear >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
 Aucun.  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`system.diagnostics`|Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.|  
|`trace`|Contient les écouteurs qui collectent, stockent et acheminent les messages de traçage.|  
|`listeners`|Contient des écouteurs qui collectent, stockent et acheminent des messages. Les écouteurs dirigent la sortie de suivi vers une cible appropriée.|  
  
## <a name="remarks"></a>Notes  
 L’élément `<clear>` supprime tous les écouteurs de la collection `Listeners` pour la trace. Vous pouvez utiliser l’élément `<clear>` avant d’utiliser l’élément `<add>` pour être certain qu’il n’existe aucun autre écouteur actif dans la collection.  
  
 Vous pouvez effacer la collection `Listeners` par programmation en appelant la méthode <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> sur la propriété <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> (`System.Diagnostics.Trace.Listeners.Clear()`).  
  
 Cet élément peut être utilisé dans le fichier de configuration de l’ordinateur (machine. config) et dans le fichier de configuration de l’application.  
  
> [!NOTE]
> L’élément `<clear>` supprime la <xref:System.Diagnostics.DefaultTraceListener> de la collection `Listeners`, en modifiant le comportement des méthodes <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType> et <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType>. L’appel d’une méthode `Assert` ou `Fail` entraîne normalement l’affichage d’une boîte de message. Toutefois, la boîte de message ne s’affiche pas si le <xref:System.Diagnostics.DefaultTraceListener> n’est pas dans la collection `Listeners`.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser l’élément `<clear>` avant d’utiliser l’élément `<add>` pour ajouter l’écouteur `console` à la collection `Listeners` pour la trace.  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <trace autoflush="false" indentsize="4">  
      <listeners>  
        <clear/>  
        <add name="console"   
          type="System.Diagnostics.ConsoleTraceListener" >  
          <filter type="System.Diagnostics.EventTypeFilter"   
            initializeData="Error" />  
        </add>  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>   
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Diagnostics.Trace.Listeners%2A>
- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- <xref:System.Diagnostics.TraceSource>
- [Schéma des paramètres de trace et de débogage](index.md)
- [\<remove>](remove-element-for-listeners-for-trace.md)
- [Écouteurs de suivi](../../../debug-trace-profile/trace-listeners.md)
