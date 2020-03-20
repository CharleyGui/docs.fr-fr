---
title: Élément <sharedListeners>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#sharedListeners
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners
helpviewer_keywords:
- <sharedListeners> element
- listeners
- shared listeners
- trace listeners, <sharedListeners> element
- sharedListeners element
ms.assetid: de200534-19dd-4156-86cf-c50521802c4c
ms.openlocfilehash: 69f15cc9583b397017ac30a0c567914495867c18
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153319"
---
# <a name="sharedlisteners-element"></a>\<sharedListeners> Element
Contient des écouteurs auxquels toute source ou tout élément de trace peuvent faire référence.  Ces auditeurs ne reçoivent aucune trace par défaut, et il n’est pas possible de récupérer ces auditeurs au moment de l’exécution. Les auditeurs identifiés comme des auditeurs partagés peuvent être ajoutés à des sources ou des traces par leur nom.  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<sharedListeners>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<sharedListeners>
  <add>...</add>  
</sharedListeners>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
 Aucun.  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<ajouter>](add-element-for-listeners-for-trace.md)|Ajoute un écouteur à la collection `sharedListeners`.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`Configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`system.diagnostics`|Spécifie l'élément racine de la section de configuration ASP.NET.|  
  
## <a name="remarks"></a>Notes   
 L’ajout d’un auditeur à la collection d’auditeurs partagés n’en fait pas un auditeur actif. Il doit encore être ajouté à une source de `Listeners` traces ou une trace en l’ajoutant à la collection pour cet élément de trace. Les cours d’auditeur dans le <xref:System.Diagnostics.TraceListener> cadre .NET dérivent de la classe.  
  
 Cet élément peut être utilisé dans le fichier de configuration de la machine (Machine.config) et le fichier de configuration d’application.  
  
## <a name="example"></a> Exemple  
 L’exemple suivant montre `<sharedListeners>` comment utiliser l’élément pour ajouter `console` l’auditeur à la `Listeners` collection pour les <xref:System.Diagnostics.TraceSource> classes et <xref:System.Diagnostics.Trace> les classes. L’auditeur de trace de console écrit des <xref:System.Diagnostics.TraceSource> <xref:System.Diagnostics.Trace>informations trace à la console par des appels à l’un ou l’autre ou .  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sharedListeners>  
      <add name="console" type="System.Diagnostics.ConsoleTraceListener" >  
        <filter type="System.Diagnostics.EventTypeFilter"  
          initializeData="Warning" />  
      </add>  
    </sharedListeners>  
    <sources>  
      <source name="mySource" switchName="sourceSwitch"  >  
        <listeners>  
          <add name="console" />  
        </listeners>  
      </source>  
    </sources>  
    <switches>  
      <add name="sourceSwitch" value="Verbose"/>  
    </switches>  
    <trace>  
      <listeners>  
        <add name="console" />  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Diagnostics.TraceListener>
- [Trace et Debug Paramètres Schema](index.md)
- [Écouteurs de suivi](../../../debug-trace-profile/trace-listeners.md)
