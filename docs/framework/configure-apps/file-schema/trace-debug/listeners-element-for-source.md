---
title: Élément <listeners> pour <source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners
helpviewer_keywords:
- listeners element for <source>
- <listeners> element for <source>
ms.assetid: a2991f43-b4d3-4614-a8e7-da392de9697f
ms.openlocfilehash: b7144b0a7004ba32b21cbc98513df574a5a9e1d9
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91195179"
---
# <a name="listeners-element-for-source"></a>\<listeners>, élément de \<source>

Ajoute ou supprime des écouteurs dans la <xref:System.Diagnostics.TraceSource.Listeners%2A> collection pour un <xref:System.Diagnostics.TraceSource> . Un écouteur dirige la sortie de suivi vers une cible appropriée, telle qu’un journal, une fenêtre ou un fichier texte.  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<listeners>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<listeners>
  <add>...</add>  
  <remove ... />  
  <clear/>  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  

 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  

 Aucun.  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<add>](add-element-for-listeners-for-source.md)|Ajoute un écouteur à la collection `Listeners`.|  
|[\<remove>](remove-element-for-listeners-for-source.md)|Supprime un écouteur de la `Listeners` collection.|  
|[\<clear>](clear-element-for-listeners-for-source.md)|Efface la collection `Listeners` pour une source de trace.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`system.diagnostics`|Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.|  
|`sources`|Contient les sources de trace qui lancent des messages de traçage.|  
|`source`|Spécifie une source de trace qui lance des messages de traçage.|  
  
## <a name="remarks"></a>Notes  
  
## <a name="configuration-file"></a>Fichier de configuration  

 Cet élément peut être utilisé dans le fichier de configuration de l’ordinateur (Machine.config) et dans le fichier de configuration de l’application.  
  
## <a name="example"></a>Exemple  

 L’exemple suivant montre comment utiliser l' `<listeners>` élément pour ajouter un écouteur de suivi de console à la `mySource` source et supprimer l’écouteur de suivi par défaut.  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="mySource" switchName="sourceSwitch"
        switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <add name="console"
            type="System.Diagnostics.ConsoleTraceListener">  
            <filter type="System.Diagnostics.EventTypeFilter"
              initializeData="Error"/>  
          </add>  
          <remove name="Default"/>  
        </listeners>  
      </source>  
    </sources>  
    <switches>  
      <add name="sourceSwitch" value="Warning"/>  
    </switches>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Diagnostics.TraceListener>
- [Schéma des paramètres de traçage et de débogage](index.md)
- [Écouteurs de la trace](../../../debug-trace-profile/trace-listeners.md)
