---
title: <filter>, Élément <add> de <listeners> pour pour<trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- filter element for <add> for <listeners> for <trace>
- <filter> element for <add> for <listeners> for <trace>
ms.assetid: eb9c18f5-dfa8-47c5-b91b-e4b93e76e1cc
ms.openlocfilehash: afde5381a7dd7dfe6a1a9d238a2029511bd9bae2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927138"
---
# <a name="filter-element-for-add-for-listeners-for-trace"></a>\<élément de > de \<filtre pour l' \<ajout de > pour \<les écouteurs > pour la trace >
Ajoute un filtre à un écouteur dans la `Listeners` collection pour une trace.  
  
 \<configuration>  
\<system.diagnostics>  
\<> de trace  
\<listeners>  
\<add>  
\<filter>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<filter   
  type="traceFilterClassName"   
  initializeData="data" />  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`type`|Attribut requis.<br /><br /> Spécifie le type du filtre, qui doit hériter de <xref:System.Diagnostics.TraceFilter> la classe. Vous pouvez utiliser le nom qualifié par un espace de noms du type, qui correspond à la <xref:System.Type.FullName%2A> propriété du type, ou vous pouvez utiliser le nom de type qualifié complet, y compris les informations de <xref:System.Type.AssemblyQualifiedName%2A> l’assembly, qui correspond à la propriété. Pour plus d’informations sur les noms de types qualifiés complets, consultez [spécification de noms de types qualifiés complets](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).|  
|`initializeData`|Attribut facultatif.<br /><br /> Chaîne passée au constructeur pour la classe de filtre spécifiée.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`system.diagnostics`|Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.|  
|`trace`|Contient les écouteurs qui collectent, stockent et acheminent les messages de traçage.|  
|`listeners`|Contient des écouteurs qui collectent, stockent et acheminent des messages. Les écouteurs dirigent la sortie de suivi vers une cible appropriée.|  
|`add`|Ajoute un écouteur à la collection `Listeners`.|  
  
## <a name="remarks"></a>Notes  
 L' `<filter>` élément doit être contenu dans un `<add>` élément pour un écouteur de trace qui spécifie le type de l’écouteur, pas seulement le nom d’un écouteur défini dans un [ \<> sharedListeners](sharedlisteners-element.md). Si l’écouteur est défini dans un [ \<> sharedListeners](sharedlisteners-element.md), le filtre de cet écouteur doit être défini dans cet élément.  
  
 Cet élément peut être utilisé dans le fichier de configuration de l’ordinateur (machine. config) et dans le fichier de configuration de l’application.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser `<filter>` l’élément pour ajouter un filtre à l' `console` écouteur dans la `Listeners` collection pour la trace, en spécifiant le niveau d' `Error`événement de filtre en tant que.  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <trace autoflush="false" indentsize="4">  
      <listeners>  
        <add name="console"   
          type="System.Diagnostics.ConsoleTraceListener" >  
          <filter type="System.Diagnostics.EventTypeFilter"   
            initializeData="Error" />  
        </add>  
        <remove name="Default" />  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceFilter>
- [Schéma des paramètres de trace et de débogage](index.md)
