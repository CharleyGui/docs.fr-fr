---
title: <add>Élément <listeners> pour pour<source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add
helpviewer_keywords:
- initializeData attribute
- add element for <listeners> for <source>
- <add> element for <listeners> for <source>
ms.assetid: 4ce36ac1-81ef-48e8-b8b2-b5a5b0e2adcb
ms.openlocfilehash: 883eef32172c5a7f900197995b4c57c3d5a84e19
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153683"
---
# <a name="add-element-for-listeners-for-source"></a>\<ajouter> Element pour \<les auditeurs \<> pour les> de source
Ajoute un écouteur à la collection `Listeners` pour une source de trace.  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<auditeurs>**](listeners-element-for-source.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<ajouter>**

## <a name="syntax"></a>Syntaxe  
  
```xml  
<add name="name"
  type="TraceListenerClassName, Version, Culture, PublicKeyToken"  
  initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`type`|Attribut requis, sauf si vous faites référence `sharedListeners` à un auditeur dans la collection, auquel cas vous n’avez qu’à vous y référer par son nom (voir l’exemple ). [Example](#example)<br /><br /> Spécifie le type de l’auditeur. Vous devez utiliser une chaîne qui répond aux exigences spécifiées dans [le spécifier des noms de type entièrement qualifiés](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).|  
|`initializeData`|Attribut facultatif.<br /><br /> La chaîne passa au constructeur pour la classe spécifiée. A <xref:System.Configuration.ConfigurationException> est jeté si la classe n’a pas un constructeur qui prend une ficelle.|  
|`name`|Attribut facultatif.<br /><br /> Spécifie le nom de l’auditeur.|  
|`traceOutputOptions`|Attribut facultatif.<br /><br /> Spécifie la valeur de la <xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A> propriété pour l’auditeur de traces.|  
|[attributs personnalisés]|Attributs facultatifs.<br /><br /> Spécifie la valeur des attributs <xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A> spécifiques à l’auditeur identifiés par la méthode de cet auditeur. <xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A>est un exemple d’attribut <xref:System.Diagnostics.DelimitedListTraceListener> supplémentaire unique à la classe.|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<filtrer>](filter-element-for-add-for-listeners-for-source.md)|Ajoute un filtre à un écouteur dans la collection `Listeners` pour une source de trace.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`system.diagnostics`|Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.|  
|`sources`|Contient les sources de trace qui lancent des messages de traçage.|  
|`source`|Spécifie une source de trace qui lance des messages de traçage.|  
|`listeners`|Spécifie les auditeurs qui recueillent, stockent et acheminent les messages.|  
  
## <a name="remarks"></a>Notes   
 Les classes d’auditeur expédiées avec <xref:System.Diagnostics.TraceListener> le cadre .NET dérivent de la classe.  
  
 Si vous ne `name` spécifiez pas <xref:System.Diagnostics.TraceListener.Name%2A> l’attribut de l’auditeur de trace, la propriété de l’auditeur de traces manque à une chaîne vide («).). Si votre application n’a qu’un seul auditeur, vous pouvez l’ajouter sans spécifier un nom, et vous pouvez la supprimer en spécifiant une chaîne vide pour le nom. Toutefois, si votre application a plus d’un auditeur, vous devez spécifier un nom unique pour <xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType> chaque auditeur de traces, ce qui vous permet d’identifier et de gérer les auditeurs de traces individuelles dans la collection.  
  
> [!NOTE]
> L’ajout de plus d’un auditeur de traces du même type et avec le même `Listeners` nom n’entraîne qu’un seul auditeur de trace de ce type et le nom ajouté à la collection. Cependant, vous pouvez programmer de `Listeners` façon programmatique plusieurs auditeurs identiques à la collection.  
  
 La valeur `initializeData` de l’attribut dépend du type d’auditeur que vous créez. Pas tous les auditeurs `initializeData`trace exigent que vous spécifiez .  
  
> [!NOTE]
> Lorsque vous `initializeData` utilisez l’attribut, vous pouvez obtenir l’avertissement compilateur "L’attribut 'initializeData' n’est pas déclaré." Cet avertissement se produit parce que les paramètres <xref:System.Diagnostics.TraceListener>de configuration sont `initializeData` validés par rapport à la classe de base abstraite , qui ne reconnaît pas l’attribut. Typiquement, vous pouvez ignorer cet avertissement pour les implémentations d’auditeur de trace qui ont un constructeur qui prend un paramètre.  
  
 Le tableau suivant montre les auditeurs trace qui sont inclus dans `initializeData` le cadre .NET et décrit la valeur de leurs attributs.  
  
|Cours d’auditeur de trace|initialiser la valeur d’attribut deData|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|La `useErrorStream` valeur <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> pour le constructeur.  Définissez `initializeData` l’attribut à «`true`écrire la sortie de trace et de débaillement au flux d’erreurs standard ; l’a`false`fixé à " d’écrire au flux de sortie standard.|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|Nom du fichier vers lequel <xref:System.Diagnostics.DelimitedListTraceListener> écrit.|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|Nom d'une source existante de journal des événements.|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|Le nom du fichier <xref:System.Diagnostics.EventSchemaTraceListener> à qui le nom écrit.|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|Le nom du fichier <xref:System.Diagnostics.TextWriterTraceListener> à qui le nom écrit.|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|Le nom du fichier <xref:System.Diagnostics.XmlWriterTraceListener> à qui le nom écrit.|  
  
## <a name="configuration-file"></a>Fichier de configuration  
 Cet élément peut être utilisé dans le fichier de configuration de la machine (Machine.config) et le fichier de configuration d’application.  
  
## <a name="example"></a> Exemple  
 L’exemple suivant montre `<add>` comment utiliser `console` des `textListener` éléments `Listeners` pour ajouter `TraceSourceApp`les auditeurs et à la collection pour la source de traces . L’auditeur `textListener` écrit trace sortie au fichier myListener.log.  
  
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
