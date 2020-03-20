---
title: <add>Élément <listeners> pour pour<trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add
helpviewer_keywords:
- initializeData attribute
- <add> element for <listeners>
- add element for <listeners>
ms.assetid: 81e804a3-ef11-4d39-bbde-bfa012c179e2
ms.openlocfilehash: c64673908dc9afe67d97c08f93e5b9d9533bd34d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153670"
---
# <a name="add-element-for-listeners-for-trace"></a>\<ajouter> Element pour \<les auditeurs \<> pour les traces>
Ajoute un auditeur à la collection **Listeners.**  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<auditeurs>**](listeners-element-for-trace.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<ajouter>**

## <a name="syntax"></a>Syntaxe  
  
```xml  
<add name="name"
     type="trace listener class name, Version, Culture, PublicKeyToken"  
     initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|**type**|Attribut requis.<br /><br /> Spécifie le type de l’auditeur. Vous devez utiliser une chaîne qui répond aux exigences spécifiées dans [le spécifier des noms de type entièrement qualifiés](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).|  
|**initialiserData**|Attribut facultatif.<br /><br /> La chaîne passa au constructeur pour la classe spécifiée.|  
|**name**|Attribut facultatif.<br /><br /> Spécifie le nom de l’auditeur.|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<filtrer>](filter-element-for-add-for-listeners-for-trace.md)|Ajoute un filtre à un `Listeners` auditeur de la collection pour une trace.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`listeners`|Spécifie un auditeur qui recueille, stocke et achemine les messages. Les auditeurs dirigent la sortie de traçage vers une cible appropriée.|  
|`system.diagnostics`|Spécifie l'élément racine de la section de configuration ASP.NET.|  
|`trace`|Contient les écouteurs qui collectent, stockent et acheminent les messages de traçage.|  
  
## <a name="remarks"></a>Notes   
 Les <xref:System.Diagnostics.Debug> <xref:System.Diagnostics.Trace> classes et les classes partagent la même collection **d’auditeurs.** Si vous ajoutez un objet d’écoute à la collection dans l’une de ces classes, l’autre classe utilise le même auditeur. Les classes d’auditeurs dérivent de la <xref:System.Diagnostics.TraceListener>.  
  
 Si vous ne `name` spécifiez pas <xref:System.Diagnostics.TraceListener.Name%2A> l’attribut de l’auditeur de trace, l’auditeur de traces par défaut à une chaîne vide («).). Si votre application n’a qu’un seul auditeur, vous pouvez l’ajouter sans spécifier un nom, et la supprimer en spécifiant une chaîne vide pour le nom. Toutefois, si votre application a plus d’un auditeur, vous devez spécifier des noms uniques <xref:System.Diagnostics.Debug.Listeners%2A> pour <xref:System.Diagnostics.Trace.Listeners%2A> chaque auditeur de traces, ce qui vous permet d’identifier et de gérer les auditeurs de traces individuels au sein de la et des collections.  
  
> [!NOTE]
> L’ajout de plus d’un auditeur de traces du même type et avec le même `Listeners` nom n’entraîne qu’un seul auditeur de trace de ce type et le nom ajouté à la collection. Cependant, vous pouvez programmer de `Listeners` façon programmatique plusieurs auditeurs identiques à la collection.  
  
 La valeur de l’attribut **initializeData** dépend du type d’auditeur que vous créez. Pas tous les auditeurs trace exigent que vous spécifiez **initializeData**.  
  
> [!NOTE]
> Lorsque vous `initializeData` utilisez l’attribut, vous pouvez obtenir l’avertissement compilateur "L’attribut 'initializeData' n’est pas déclaré." Cet avertissement se produit parce que les paramètres <xref:System.Diagnostics.TraceListener>de configuration sont `initializeData` validés par rapport à la classe de base abstraite , qui ne reconnaît pas l’attribut. Typiquement, vous pouvez ignorer cet avertissement pour les implémentations d’auditeur de trace qui ont un constructeur qui prend un paramètre.  
  
 Le tableau suivant montre les auditeurs trace qui sont inclus dans le cadre .NET et décrit la valeur de leurs attributs **initializeData.**  
  
|Cours d’auditeur de trace|initialiser la valeur d’attribut deData|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|La `useErrorStream` valeur <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> pour le constructeur.  Définissez `initializeData` l’attribut à "`true`écrire la <xref:System.Console.Error%2A?displayProperty=nameWithType>trace et la sortie de déboçon à ; "`false`écrire à <xref:System.Console.Out%2A?displayProperty=nameWithType>.|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|Nom du fichier vers lequel <xref:System.Diagnostics.DelimitedListTraceListener> écrit.|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|Le nom du nom d’une source existante de journal d’événements.|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|Le nom du fichier <xref:System.Diagnostics.EventSchemaTraceListener> à qui le nom écrit.|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|Le nom du fichier <xref:System.Diagnostics.TextWriterTraceListener> à qui le nom écrit.|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|Le nom du fichier <xref:System.Diagnostics.XmlWriterTraceListener> à qui le nom écrit.|  
  
## <a name="example"></a> Exemple  
 L’exemple suivant montre ** \<** comment utiliser ajouter des `MyListener` éléments `MyEventListener`>pour ajouter les auditeurs et à la collection **Listeners.** `MyListener`crée un `MyListener.log` fichier appelé et écrit la sortie au fichier. `MyEventListener`crée une entrée dans le journal de l’événement.  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <trace autoflush="true" indentsize="0">  
         <listeners>  
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener, system, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="c:\myListener.log" />  
            <add name="MyEventListener"  
                 type="System.Diagnostics.EventLogTraceListener, system, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"                 initializeData="MyConfigEventLog"/>  
            <add name="configConsoleListener"  
                 type="System.Diagnostics.ConsoleTraceListener, system, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"/>  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- [Trace et Debug Paramètres Schema](index.md)
- [Écouteurs de suivi](../../../debug-trace-profile/trace-listeners.md)
