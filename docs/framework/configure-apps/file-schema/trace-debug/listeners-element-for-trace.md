---
title: Élément <listeners> pour <trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners
helpviewer_keywords:
- <listeners> element
- listeners element
ms.assetid: 1394c2c3-6304-46db-87c1-8e8b16f5ad5b
ms.openlocfilehash: fd12be1b775d7611ef3f16d23147470313bf9866
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153371"
---
# <a name="listeners-element-for-trace"></a>\<auditeurs> Element \<pour trace>
Spécifie un auditeur qui recueille, stocke et achemine les messages. Les auditeurs dirigent la sortie de traçage vers une cible appropriée.  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<auditeurs>**

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
 Aucun.  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<ajouter>](add-element-for-listeners-for-trace.md)|Ajoute un écouteur à la collection `Listeners`.|  
|[\<clair>](clear-element-for-listeners-for-trace.md)|Efface la collection `Listeners` de la trace.|  
|[\<supprimer>](remove-element-for-listeners-for-trace.md)|Retire un auditeur de `Listeners` la collection.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`system.diagnostics`|Spécifie l'élément racine de la section de configuration ASP.NET.|  
|`trace`|Contient les écouteurs qui collectent, stockent et acheminent les messages de traçage.|  
  
## <a name="remarks"></a>Notes   
 Les <xref:System.Diagnostics.Debug> <xref:System.Diagnostics.Trace> classes et les classes partagent la même collection **d’auditeurs.** Si vous ajoutez un objet d’écoute à la collection dans l’une de ces classes, l’autre classe utilise le même auditeur. Les classes d’auditeur expédiées avec <xref:System.Diagnostics.TraceListener> le cadre .NET dérivent de la classe.  
  
## <a name="configuration-file"></a>Fichier de configuration  
 Cet élément peut être utilisé dans le fichier de configuration de la machine (Machine.config) et le fichier de configuration d’application.  
  
## <a name="example"></a> Exemple  
 L’exemple suivant montre comment utiliser les `MyListener` `MyEventListener` ** \<auditeurs>** élément pour ajouter les auditeurs et à la collection **Listeners.** `MyListener`crée un `MyListener.log` fichier appelé et écrit la sortie au fichier. `MyEventListener`crée une entrée dans le journal de l’événement.  
  
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
- [Trace et Debug Paramètres Schema](index.md)
