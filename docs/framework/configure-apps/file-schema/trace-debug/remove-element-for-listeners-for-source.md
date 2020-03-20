---
title: <remove>Élément <listeners> pour pour<source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/remove
helpviewer_keywords:
- remove element for <listeners> for <source>
- <remove> element for <listeners> for <source>
ms.assetid: 3ff6b578-273d-407f-b07f-8251f1f9f5d0
ms.openlocfilehash: 657e6db2af9b99b3bbf03afc6aab02c58a830f2d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153333"
---
# <a name="remove-element-for-listeners-for-source"></a>\<supprimer> Élément pour \<les auditeurs \<> pour les> de source
Supprime un écouteur de la collection `Listeners` pour une source de trace.  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<auditeurs>**](listeners-element-for-source.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<supprimer>**

## <a name="syntax"></a>Syntaxe  
  
```xml  
<remove name="listenerName" />  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`name`|Attribut requis.<br /><br /> Le nom de l’auditeur `Listeners` à retirer de la collection.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`system.diagnostics`|Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.|  
|`sources`|Contient les sources de trace qui lancent des messages de traçage.|  
|`source`|Spécifie une source de trace qui lance des messages de traçage.|  
|`listeners`|Spécifie les auditeurs qui recueillent, stockent et acheminent les messages.|  
  
## <a name="remarks"></a>Notes   
 L’élément `<remove>` supprime un auditeur `Listeners` spécifié de la collection pour une source de traces.  
  
 Vous pouvez supprimer un `Listeners` élément de la collection pour <xref:System.Diagnostics.TraceListenerCollection.Remove%2A> une source <xref:System.Diagnostics.TraceSource.Listeners%2A> de <xref:System.Diagnostics.TraceSource> traces programmatiquement en appelant la méthode sur la propriété de l’instance.  
  
 Cet élément peut être utilisé dans le fichier de configuration de la machine (Machine.config) et le fichier de configuration d’application.  
  
## <a name="example"></a> Exemple  
 L’exemple suivant montre `<remove>` comment utiliser `<add>` l’élément avant `console` d’utiliser l’élément pour ajouter l’auditeur à la `Listeners` collection pour la source `TraceSourceApp`de traces .  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="TraceSourceApp" switchName="sourceSwitch"
         switchType="System.Diagnostics.SourceSwitch" >  
         <listeners>  
           <remove name="Default"/>  
           <add name="console"
             type="System.Diagnostics.ConsoleTraceListener" />  
         </listeners>  
      </source>  
    </sources>  
  </system.diagnostics>  
</configuration>
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Diagnostics.TraceSource.Listeners%2A>
- <xref:System.Diagnostics.TraceSource>
- [Trace et Debug Paramètres Schema](index.md)
- [\<clair>](clear-element-for-listeners-for-source.md)
- [Écouteurs de suivi](../../../debug-trace-profile/trace-listeners.md)
