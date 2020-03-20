---
title: <filter>Élément <add> pour <listeners> pour pour pour<source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#filter
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- <filter> element for <add> for <listeners> for <source>
- filter element for <add> for <listeners> for <source>
ms.assetid: 15808b80-4579-4c25-b385-178cfdf154ba
ms.openlocfilehash: 0cb668782de263d5f784691f46cb8b74541d942b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153514"
---
# <a name="filter-element-for-add-for-listeners-for-source"></a>\<filtrer> Element \<pour ajouter de \<la> pour \<les auditeurs> pour les> de source
Ajoute un filtre à un écouteur dans la collection `Listeners` pour une source de trace.  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<auditeurs>**](listeners-element-for-source.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ajouter>**](add-element-for-listeners-for-source.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filtrer>**

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
|`type`|Attribut requis.<br /><br /> Spécifie le type de filtre, <xref:System.Diagnostics.TraceFilter> qui devrait hériter de la classe. Vous pouvez utiliser le nom du type, qui correspond à <xref:System.Type.FullName%2A> la propriété du type, ou vous pouvez utiliser le nom <xref:System.Type.AssemblyQualifiedName%2A> de type entièrement qualifié, y compris les informations d’assemblage, qui correspond à la propriété. Pour plus d’informations sur les noms de type entièrement qualifiés, voir [spécifier des noms de type entièrement qualifiés](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).|  
|`initializeData`|Attribut facultatif.<br /><br /> La chaîne est passée au constructeur pour la classe de filtre spécifiée.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`system.diagnostics`|Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.|  
|`sources`|Contient les sources de trace qui lancent des messages de traçage.|  
|`source`|Spécifie une source de trace qui lance des messages de traçage.|  
|`listeners`|Contient des auditeurs qui recueillent, stockent et acheminent des messages. Les auditeurs dirigent la sortie de traçage vers une cible appropriée.|  
|`add`|Ajoute un écouteur à la collection `Listeners` pour une source de trace.|  
  
## <a name="remarks"></a>Notes   
 L’élément `<filter>` doit être `<add>` contenu dans un élément pour un auditeur de source de trace qui spécifie le type de l’auditeur, et pas seulement le nom d’un auditeur défini dans un [ \<>d’écoutes partagées ](sharedlisteners-element.md). Si l’auditeur est défini dans un [ \<>d’écoute partagé, ](sharedlisteners-element.md)le filtre de cet auditeur doit être défini dans cet élément.  
  
 Cet élément peut être utilisé dans le fichier de configuration de la machine (Machine.config) et le fichier de configuration d’application.  
  
## <a name="example"></a> Exemple  
 L’exemple suivant montre `<filter>` comment utiliser l’élément pour `console` ajouter `Listeners` un filtre `myTraceSource`à l’auditeur dans `Error`la collection pour la source de trace , spécifiant le niveau d’événement de filtre comme .  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="myTraceSource" switchName="SourceSwitch"
        switchType="System.Diagnostics.SourceSwitch"  >  
        <listeners>  
          <add name="console"
            type="System.Diagnostics.ConsoleTraceListener" >  
            <filter type="System.Diagnostics.EventTypeFilter"
              initializeData="Error" />  
          </add>  
          <remove name="Default" />  
        </listeners>  
      </source>  
    </sources>  
    <switches>  
      <add name="SourceSwitch" value="Warning" />  
    </switches>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceFilter>
- [Trace et Debug Paramètres Schema](index.md)
