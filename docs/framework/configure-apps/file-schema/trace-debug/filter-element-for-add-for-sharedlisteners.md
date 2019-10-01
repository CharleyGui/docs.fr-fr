---
title: Élément <filter> pour <add> pour <sharedListeners>
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
ms.openlocfilehash: 4e92f80e9f6069b5fa70501e13a55d5a6fe95e7a
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697325"
---
# <a name="filter-element-for-add-for-sharedlisteners"></a>\<filter > élément de \<Add > pour \<sharedListeners >
Ajoute un filtre à un écouteur dans la collection `sharedListeners`.  
  
[ **\<configuration>** ](../configuration-element.md)  
&nbsp; @ no__t-1[ **\<System. diagnostics >** ](system-diagnostics-element.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<sharedListeners >** ](sharedlisteners-element.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5[ **\<Add >** ](add-element-for-sharedlisteners.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7 **\<filter >**  
  
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
|**type**|Attribut requis.<br /><br /> Spécifie le type du filtre. Vous pouvez utiliser uniquement le nom complet du type (au format de la propriété <xref:System.Type.FullName%2A?displayProperty=nameWithType>), ou vous pouvez utiliser le nom de type qualifié complet, y compris les informations de l’assembly (au format de la propriété <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType>). Pour plus d’informations sur la création d’un nom de type qualifié complet, consultez [spécification de noms de types qualifiés complets](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).|  
|**initializeData**|Attribut facultatif.<br /><br /> Chaîne passée au constructeur pour la classe spécifiée.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`system.diagnostics`|Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.|  
|`sharedListeners`|Collection d’écouteurs qui peut faire référence à n’importe quel élément source ou trace.|  
|`add`|Ajoute un écouteur à la collection **sharedListeners** .|  
  
## <a name="remarks"></a>Notes  
 Si un écouteur est défini dans un élément `<add>` de l’élément `<sharedListeners>`, le filtre de cet écouteur doit être défini dans un élément `<filter>` qui est un enfant de l’élément `<add>`.  
  
 Cet élément peut être utilisé dans le fichier de configuration de l’ordinateur (machine. config) et dans le fichier de configuration de l’application.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser l’élément `<filter>` pour ajouter un filtre à l’écouteur de la trace `console` dans la collection `sharedListeners`.  
  
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
- [Schéma des paramètres de trace et de débogage](index.md)
