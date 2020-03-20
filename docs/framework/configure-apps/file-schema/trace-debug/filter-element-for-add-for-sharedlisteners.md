---
title: <filter>Élément <add> pour pour<sharedListeners>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners/add/filter
helpviewer_keywords:
- filter element for <add> for <sharedListeners>
- initializeData attribute
- <filter> element for <add> for <sharedListeners>
- filters, trace listeners
- trace listeners, filters
ms.assetid: 7d4e7faa-2e4e-4379-ac76-f6cd7f2f8fac
ms.openlocfilehash: 6fb52cdfa5792ab6059b60d8dbb91c107cd666ca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153451"
---
# <a name="filter-element-for-add-for-sharedlisteners"></a>\<filtrer> Element \<pour ajouter \<de la> pour les> d'>
Ajoute un filtre à un écouteur dans la collection `sharedListeners`.  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sharedListeners>**](sharedlisteners-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ajouter>**](add-element-for-sharedlisteners.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filtrer>**

## <a name="syntax"></a>Syntaxe  
  
```xml  
<filter type="System.Diagnostics.EventTypeFilter"
  initializeData="Warning" />  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|**type**|Attribut requis.<br /><br /> Spécifie le type de filtre. Vous ne pouvez utiliser que le nom complet <xref:System.Type.FullName%2A?displayProperty=nameWithType> du type (dans le format de la propriété), ou vous <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType> pouvez utiliser le nom de type entièrement qualifié, y compris les informations d’assemblage (dans le format de la propriété). Pour plus d’informations sur la création d’un nom de type entièrement qualifié, voir [Spécifier des noms de type entièrement qualifiés](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).|  
|**initialiserData**|Attribut facultatif.<br /><br /> La chaîne passa au constructeur pour la classe spécifiée.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`system.diagnostics`|Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.|  
|`sharedListeners`|Une collection d’auditeurs que toute source ou élément de trace peut référencer.|  
|`add`|Ajoute un auditeur à la collection **sharedListeners.**|  
  
## <a name="remarks"></a>Notes   
 Si un auditeur est `<add>` défini dans `<sharedListeners>` un élément de l’élément, le `<filter>` filtre de cet `<add>` auditeur doit être défini dans un élément qui est un enfant de l’élément.  
  
 Cet élément peut être utilisé dans le fichier de configuration de la machine (Machine.config) et le fichier de configuration d’application.  
  
## <a name="example"></a> Exemple  
 L’exemple suivant montre `<filter>` comment utiliser l’élément pour `console` ajouter `sharedListeners` un filtre à l’auditeur de traces de la collection.  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="myTraceSource" >  
        <listeners>  
          <add name="console" />  
          <remove name="Default" />  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add name="console"
        type="System.Diagnostics.ConsoleTraceListener" >  
        <filter type="System.Diagnostics.EventTypeFilter"
          initializeData="Error" />  
      </add>  
    </sharedListeners>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Diagnostics.TraceFilter>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceSource>
- [Trace et Debug Paramètres Schema](index.md)
