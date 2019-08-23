---
title: <clear>, Élément <listeners> de pour<trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/clear
helpviewer_keywords:
- clear element for <listeners> for <trace>
- <clear> element for <listeners> for <trace>
ms.assetid: b44732a8-271f-4a06-ba9e-fe3298d6f192
ms.openlocfilehash: 9816ba0f8e4ddd4c38537eb4e014a4240ff20407
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927173"
---
# <a name="clear-element-for-listeners-for-trace"></a>\<Effacer > élément pour \<les écouteurs > pour \<la trace >
Efface la collection `Listeners` de la trace.  
  
 \<configuration>  
\<system.diagnostics>  
\<> de trace  
\<listeners>  
\<clear>  
  
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
 L' `<clear>` élément supprime tous les écouteurs de la `Listeners` collection pour la trace. Vous pouvez utiliser l' `<clear>` élément avant d’utiliser `<add>` l’élément pour être certain qu’il n’existe aucun autre écouteur actif dans la collection.  
  
 Vous pouvez effacer la `Listeners` collection par programmation en appelant la <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> méthode sur la <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> propriété (`System.Diagnostics.Trace.Listeners.Clear()`).  
  
 Cet élément peut être utilisé dans le fichier de configuration de l’ordinateur (machine. config) et dans le fichier de configuration de l’application.  
  
> [!NOTE]
> L' `<clear>` élément supprime le <xref:System.Diagnostics.DefaultTraceListener> de la `Listeners` <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType> <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> collection, en<xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>modifiant le comportement des méthodes ,,et.<xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> L’appel `Assert` d' `Fail` une méthode ou entraîne normalement l’affichage d’une boîte de message. Toutefois, la boîte de message ne s’affiche pas <xref:System.Diagnostics.DefaultTraceListener> si le n’est `Listeners` pas dans la collection.  
  
## <a name="example"></a>Exemples  
 L’exemple suivant montre `<clear>` comment utiliser l’élément avant d’utiliser l' `<add>` élément `console` pour ajouter l’écouteur à la `Listeners` collection pour la trace.  
  
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
