---
title: Élément <listeners> pour <trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners
helpviewer_keywords:
- <listeners> element
- listeners element
ms.assetid: 1394c2c3-6304-46db-87c1-8e8b16f5ad5b
ms.openlocfilehash: 10530cfadf2e182f912c699e50294af4b57f47b5
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088865"
---
# <a name="listeners-element-for-trace"></a>\<écouteurs > élément pour \<trace >
Spécifie un écouteur qui collecte, stocke et achemine des messages. Les écouteurs dirigent la sortie de suivi vers une cible appropriée.  

[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. diagnostics >** ](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;\<de [**trace**](trace-element.md) >
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**écouteurs**\<

## <a name="syntax"></a>Syntaxe  
  
```xml  
<listeners>   
  <add>...</add>  
  <clear/>  
  <remove ... />  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
 Aucun(e).  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<add>](add-element-for-listeners-for-trace.md)|Ajoute un écouteur à la collection `Listeners`.|  
|[\<clear>](clear-element-for-listeners-for-trace.md)|Efface la collection `Listeners` de la trace.|  
|[\<remove>](remove-element-for-listeners-for-trace.md)|Supprime un écouteur de la collection `Listeners`.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`system.diagnostics`|Spécifie l'élément racine de la section de configuration ASP.NET.|  
|`trace`|Contient les écouteurs qui collectent, stockent et acheminent les messages de traçage.|  
  
## <a name="remarks"></a>Notes  
 Les classes <xref:System.Diagnostics.Debug> et <xref:System.Diagnostics.Trace> partagent la même collection d' **écouteurs** . Si vous ajoutez un objet écouteur à la collection dans l’une de ces classes, l’autre classe utilise le même écouteur. Les classes d’écouteur fournies avec le .NET Framework dérivent de la classe <xref:System.Diagnostics.TraceListener>.  
  
## <a name="configuration-file"></a>Fichier de configuration  
 Cet élément peut être utilisé dans le fichier de configuration de l’ordinateur (machine. config) et dans le fichier de configuration de l’application.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser l’élément **\<écouteurs >** pour ajouter les écouteurs `MyListener` et `MyEventListener` à la collection d' **écouteurs** . `MyListener` crée un fichier nommé `MyListener.log` et écrit la sortie dans le fichier. `MyEventListener` crée une entrée dans le journal des événements.  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <trace autoflush="true" indentsize="0">  
      <listeners>  
        <add name="myListener"   
          type="System.Diagnostics.TextWriterTraceListener,   
            system, version=1.0.3300.0, Culture=neutral,   
            PublicKeyToken=b77a5c561934e089"   
          initializeData="c:\myListener.log" />  
        <add name="MyEventListener"  
          type="System.Diagnostics.EventLogTraceListener,   
            system, version=1.0.3300.0, Culture=neutral,   
            PublicKeyToken=b77a5c561934e089"  
          initializeData="MyConfigEventLog"/>  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Diagnostics.TraceListener>
- [Schéma des paramètres de trace et de débogage](index.md)
