---
title: Élément <add> pour <sharedListeners>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners/add
helpviewer_keywords:
- initializeData attribute
- <add> element for <sharedListeners>
- add element for <sharedListeners>
ms.assetid: 1595e1bc-2492-421f-8384-7f382eb8eb57
ms.openlocfilehash: 5588892ec75a791eda1eb043936c0af95e79354e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153605"
---
# <a name="add-element-for-sharedlisteners"></a>\<ajouter> Element pour \<les> sharedListeners
Ajoute un écouteur à la collection `sharedListeners`. `sharedListeners`est une collection d’auditeurs que toute [ \<source>](source-element.md) ou [ \<trace>](trace-element.md) peut référencer.  Par défaut, les `sharedListeners` auditeurs de `Listeners` la collection ne sont pas placés dans une collection. Ils doivent être ajoutés [ \<](source-element.md) par leur nom à la source>ou [ \<tracer>](trace-element.md). Il n’est pas possible `sharedListeners` d’obtenir les auditeurs dans la collection dans le code à l’heure d’exécution.  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sharedListeners>**](sharedlisteners-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<ajouter>**

## <a name="syntax"></a>Syntaxe  
  
```xml  
<add name="name"
  type="TraceListenerClassName, Version, Culture, PublicKeyToken"  
  initializeData="data"
  traceOutputOptions = "None"
/>  
```
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`name`|Attribut requis.<br /><br /> Spécifie le nom de l’auditeur qui est `Listeners` utilisé pour ajouter l’auditeur partagé à une collection.|  
|`type`|Attribut requis.<br /><br /> Spécifie le type de l’auditeur. Vous devez utiliser une chaîne qui répond aux exigences spécifiées dans [le spécifier des noms de type entièrement qualifiés](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).|  
|`initializeData`|Attribut facultatif.<br /><br /> La chaîne passa au constructeur pour la classe spécifiée.|  
|`traceOutputOptions`|Attribut facultatif.<br/><br/>La représentation des chaînes <xref:System.Diagnostics.TraceOptions> d’un ou de plusieurs membres qui indique les données à écrire à la sortie de traces. Plusieurs articles sont séparés par des virgules. La valeur par défaut est "Aucun".|

### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<filtrer>](filter-element-for-add-for-sharedlisteners.md)|Ajoute un filtre à un écouteur dans la collection `sharedListeners`.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`system.diagnostics`|Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.|  
|`sharedListeners`|Une collection d’auditeurs que toute source ou élément de trace peut référencer.|  
  
## <a name="remarks"></a>Notes   
 Les classes d’auditeur expédiées avec <xref:System.Diagnostics.TraceListener> le cadre .NET dérivent de la classe. La valeur `name` de l’attribut est utilisée pour `Listeners` ajouter l’auditeur partagé à une collection pour une trace ou une source de trace. La valeur `initializeData` de l’attribut dépend du type d’auditeur que vous créez. Pas tous les auditeurs `initializeData`trace exigent que vous spécifiez .  
  
> [!NOTE]
> Lorsque vous `initializeData` utilisez l’attribut, vous pouvez obtenir l’avertissement compilateur "L’attribut 'initializeData' n’est pas déclaré." Cet avertissement se produit parce que les paramètres <xref:System.Diagnostics.TraceListener>de configuration sont `initializeData` validés par rapport à la classe de base abstraite , qui ne reconnaît pas l’attribut. Typiquement, vous pouvez ignorer cet avertissement pour les implémentations d’auditeur de trace qui ont un constructeur qui prend un paramètre.  
  
 Le tableau suivant montre les auditeurs trace qui sont inclus dans `initializeData` le cadre .NET et décrit la valeur de leurs attributs.  
  
|Cours d’auditeur de trace|initialiser la valeur d’attribut deData|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener>|La `useErrorStream` valeur <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> pour le constructeur.  Définissez `initializeData` l’attribut à «`true`écrire la sortie de trace et de débaillement au flux d’erreurs standard ; l’a`false`fixé à " d’écrire au flux de sortie standard.|  
|<xref:System.Diagnostics.DelimitedListTraceListener>|Nom du fichier vers lequel <xref:System.Diagnostics.DelimitedListTraceListener> écrit.|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|Nom d'une source existante de journal des événements.|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|Le nom du fichier <xref:System.Diagnostics.EventSchemaTraceListener> à qui le nom écrit.|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|Le nom du fichier <xref:System.Diagnostics.TextWriterTraceListener> à qui le nom écrit.|  
|<xref:System.Diagnostics.XmlWriterTraceListener>|Le nom du fichier <xref:System.Diagnostics.XmlWriterTraceListener> à qui le nom écrit.|  
  
## <a name="configuration-file"></a>Fichier de configuration  
 Cet élément peut être utilisé dans le fichier de configuration de la machine (Machine.config) et le fichier de configuration d’application.  
  
## <a name="example"></a> Exemple  
 L’exemple suivant montre `<add>` comment utiliser <xref:System.Diagnostics.TextWriterTraceListener> `textListener` des `sharedListeners` éléments pour ajouter la collection.   `textListener`est ajouté par `Listeners` son nom à `TraceSourceApp`la collection pour la source de traces . L’auditeur `textListener` écrit trace sortie au fichier myListener.log.  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="TraceSourceApp" switchName="sourceSwitch"
        switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <add name="console"
            type="System.Diagnostics.ConsoleTraceListener"/>  
          <add name="textListener"/>  
          <remove name="Default"/>  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add name="textListener"
        type="System.Diagnostics.TextWriterTraceListener"
        initializeData="myListener.log"/>  
    </sharedListeners>  
    <switches>  
      <add name="sourceSwitch" value="Warning"/>  
    </switches>  
  </system.diagnostics>  
</configuration>
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [Trace et Debug Paramètres Schema](index.md)
- [Écouteurs de suivi](../../../debug-trace-profile/trace-listeners.md)
