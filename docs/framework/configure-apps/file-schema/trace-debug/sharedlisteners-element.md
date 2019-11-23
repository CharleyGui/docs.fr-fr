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
ms.openlocfilehash: b419ecf451b79808e545525c7b8761175f390200
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699301"
---
# <a name="sharedlisteners-element"></a>Élément \<sharedListeners >
Contient des écouteurs auxquels toute source ou tout élément de trace peuvent faire référence.  Ces écouteurs ne reçoivent pas de suivi par défaut, et il n’est pas possible de récupérer ces écouteurs au moment de l’exécution. Les écouteurs identifiés comme écouteurs partagés peuvent être ajoutés à des sources ou des suivis par nom.  
  
[ **\<configuration>** ](../configuration-element.md)  
&nbsp;&nbsp;[ **\<System. diagnostics >** ](system-diagnostics-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp; **\<sharedListeners >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<sharedListeners>   
  <add>...</add>  
</sharedListeners>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributes  
 Aucune.  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<add>](add-element-for-listeners-for-trace.md)|Ajoute un écouteur à la collection `sharedListeners`.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`Configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`system.diagnostics`|Spécifie l'élément racine de la section de configuration ASP.NET.|  
  
## <a name="remarks"></a>Remarques  
 L’ajout d’un écouteur à la collection d’écouteurs partagés ne fait pas de l’écouteur actif. Il doit toujours être ajouté à une source de suivi ou à une trace en l’ajoutant à la collection `Listeners` pour cet élément trace. Les classes d’écouteur dans le .NET Framework dérivent de la classe <xref:System.Diagnostics.TraceListener>.  
  
 Cet élément peut être utilisé dans le fichier de configuration de l’ordinateur (machine. config) et dans le fichier de configuration de l’application.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser l’élément `<sharedListeners>` pour ajouter l’écouteur `console` à la collection `Listeners` pour les classes <xref:System.Diagnostics.TraceSource> et <xref:System.Diagnostics.Trace>. L’écouteur de suivi de console écrit les informations de trace dans la console par le biais d’appels à <xref:System.Diagnostics.TraceSource> ou <xref:System.Diagnostics.Trace>.  
  
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
- [Schéma des paramètres de trace et de débogage](index.md)
- [Écouteurs de suivi](../../../debug-trace-profile/trace-listeners.md)
