---
title: <add>, Élément <listeners> de pour<trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add
helpviewer_keywords:
- initializeData attribute
- <add> element for <listeners>
- add element for <listeners>
ms.assetid: 81e804a3-ef11-4d39-bbde-bfa012c179e2
ms.openlocfilehash: d4ff919991ab1505b2845a225706d32cc1e57d0a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920568"
---
# <a name="add-element-for-listeners-for-trace"></a>\<Ajouter > élément pour \<les écouteurs > pour \<la trace >
Ajoute un écouteur à la collection d' **écouteurs** .  
  
 \<configuration>  
\<system.diagnostics>  
\<> de trace  
\<listeners>  
\<add>  
  
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
|**type**|Attribut requis.<br /><br /> Spécifie le type de l’écouteur. Vous devez utiliser une chaîne qui répond aux exigences spécifiées dans [spécification de noms de types qualifiés complets](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).|  
|**initializeData**|Attribut facultatif.<br /><br /> Chaîne passée au constructeur pour la classe spécifiée.|  
|**name**|Attribut facultatif.<br /><br /> Spécifie le nom de l’écouteur.|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<filter>](filter-element-for-add-for-listeners-for-trace.md)|Ajoute un filtre à un écouteur dans la `Listeners` collection pour une trace.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`listeners`|Spécifie un écouteur qui collecte, stocke et achemine des messages. Les écouteurs dirigent la sortie de suivi vers une cible appropriée.|  
|`system.diagnostics`|Spécifie l'élément racine de la section de configuration ASP.NET.|  
|`trace`|Contient les écouteurs qui collectent, stockent et acheminent les messages de traçage.|  
  
## <a name="remarks"></a>Notes  
 Les <xref:System.Diagnostics.Debug> classes <xref:System.Diagnostics.Trace> et partagent la même collection d' **écouteurs** . Si vous ajoutez un objet écouteur à la collection dans l’une de ces classes, l’autre classe utilise le même écouteur. Les classes d’écouteur dérivent de <xref:System.Diagnostics.TraceListener>.  
  
 Si vous ne spécifiez pas `name` l’attribut de l’écouteur de la <xref:System.Diagnostics.TraceListener.Name%2A> trace, la valeur par défaut de l’écouteur de la trace est une chaîne vide (""). Si votre application n’a qu’un seul écouteur, vous pouvez l’ajouter sans spécifier de nom et la supprimer en spécifiant une chaîne vide pour le nom. Toutefois, si votre application a plusieurs écouteurs, vous devez spécifier des noms uniques pour chaque écouteur de suivi, ce qui vous permet d’identifier et de gérer des écouteurs de suivi individuels <xref:System.Diagnostics.Debug.Listeners%2A> dans <xref:System.Diagnostics.Trace.Listeners%2A> les collections et.  
  
> [!NOTE]
> L’ajout de plusieurs écouteurs de suivi du même type et portant le même nom n’entraîne l’ajout d’un seul écouteur de suivi de ce type et d’un `Listeners` même nom à la collection. Toutefois, vous pouvez ajouter par programmation plusieurs écouteurs identiques à la `Listeners` collection.  
  
 La valeur de l’attribut **initializeData** dépend du type d’écouteur que vous créez. Tous les écouteurs de suivi ne nécessitent pas que vous spécifiez **initializeData**.  
  
> [!NOTE]
> Lorsque vous utilisez l' `initializeData` attribut, vous pouvez recevoir l’avertissement du compilateur «l’attribut’initializeData’n’est pas déclaré.» Cet avertissement se produit parce que les paramètres de configuration sont validés par <xref:System.Diagnostics.TraceListener>rapport à la classe de base `initializeData` abstraite, qui ne reconnaît pas l’attribut. En règle générale, vous pouvez ignorer cet avertissement pour les implémentations d’écouteurs de trace qui ont un constructeur qui prend un paramètre.  
  
 Le tableau suivant répertorie les écouteurs de suivi inclus avec le .NET Framework et décrit la valeur de leurs attributs **initializeData** .  
  
|Classe d’écouteur de suivi|valeur de l’attribut initializeData|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|`useErrorStream` Valeur<xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> du constructeur.  Affectez `initializeData` à l’attribut`true`la valeur "" pour écrire la sortie <xref:System.Console.Error%2A?displayProperty=nameWithType>de trace et de débogage dans; «`false`» dans lequel <xref:System.Console.Out%2A?displayProperty=nameWithType>écrire.|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|Nom du fichier <xref:System.Diagnostics.DelimitedListTraceListener> dans lequel écrit.|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|Nom du nom d’une source de journal des événements existante.|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|Nom du fichier dans lequel <xref:System.Diagnostics.EventSchemaTraceListener> écrit.|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|Nom du fichier dans lequel <xref:System.Diagnostics.TextWriterTraceListener> écrit.|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|Nom du fichier dans lequel <xref:System.Diagnostics.XmlWriterTraceListener> écrit.|  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser  **\<ajouter des >** `MyListener` des éléments pour ajouter les écouteurs et `MyEventListener` la collection d' **écouteurs** . `MyListener`crée un fichier appelé `MyListener.log` et écrit la sortie dans le fichier. `MyEventListener`crée une entrée dans le journal des événements.  
  
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
- [Schéma des paramètres de trace et de débogage](index.md)
- [Écouteurs de suivi](../../../debug-trace-profile/trace-listeners.md)
