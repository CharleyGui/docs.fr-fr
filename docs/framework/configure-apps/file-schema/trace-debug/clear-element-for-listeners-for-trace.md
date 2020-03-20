---
title: <clear>Élément <listeners> pour pour<trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/clear
helpviewer_keywords:
- clear element for <listeners> for <trace>
- <clear> element for <listeners> for <trace>
ms.assetid: b44732a8-271f-4a06-ba9e-fe3298d6f192
ms.openlocfilehash: 905dad8274fede80f4809ff3c7a014049f9df450
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153540"
---
# <a name="clear-element-for-listeners-for-trace"></a>\<élément> clair pour \<les auditeurs \<> pour les traces>
Efface la collection `Listeners` de la trace.  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<auditeurs>**](listeners-element-for-trace.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clair>**

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
|`listeners`|Contient des auditeurs qui recueillent, stockent et acheminent des messages. Les auditeurs dirigent la sortie de traçage vers une cible appropriée.|  
  
## <a name="remarks"></a>Notes   
 L’élément `<clear>` supprime tous `Listeners` les auditeurs de la collection pour la trace. Vous pouvez `<clear>` utiliser l’élément avant d’utiliser l’élément `<add>` pour être certain qu’il n’y a pas d’autres auditeurs actifs dans la collection.  
  
 Vous pouvez `Listeners` effacer la collecte programmatiquement en appelant la <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> méthode sur la <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> propriété (`System.Diagnostics.Trace.Listeners.Clear()`).  
  
 Cet élément peut être utilisé dans le fichier de configuration de la machine (Machine.config) et le fichier de configuration d’application.  
  
> [!NOTE]
> `<clear>` L’élément supprime <xref:System.Diagnostics.DefaultTraceListener> le `Listeners` de la collection, <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>modifiant <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType> <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>le <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> comportement de la , , , et les méthodes. L’appel d’une `Assert` méthode ou `Fail` une méthode permet normalement l’affichage d’une boîte de message. Toutefois, la boîte de message <xref:System.Diagnostics.DefaultTraceListener> n’est `Listeners` pas affichée si elle n’est pas dans la collection.  
  
## <a name="example"></a> Exemple  
 L’exemple suivant montre `<clear>` comment utiliser `<add>` l’élément avant `console` d’utiliser l’élément pour ajouter l’auditeur à la `Listeners` collection pour la trace.  
  
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
- [Trace et Debug Paramètres Schema](index.md)
- [\<supprimer>](remove-element-for-listeners-for-trace.md)
- [Écouteurs de suivi](../../../debug-trace-profile/trace-listeners.md)
