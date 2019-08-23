---
title: <add>, Élément <listeners> de pour<source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add
helpviewer_keywords:
- initializeData attribute
- add element for <listeners> for <source>
- <add> element for <listeners> for <source>
ms.assetid: 4ce36ac1-81ef-48e8-b8b2-b5a5b0e2adcb
ms.openlocfilehash: 96bfde3ec425f6f77d1d655808d155eb0e6fcd0f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927196"
---
# <a name="add-element-for-listeners-for-source"></a>\<Ajouter > élément pour \<les écouteurs > pour \<le > source
Ajoute un écouteur à la collection `Listeners` pour une source de trace.  
  
 \<configuration>  
\<system.diagnostics>  
\<sources>  
\<> source  
\<listeners>  
\<add>  
  
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
|`type`|Attribut obligatoire, sauf si vous référencez un écouteur dans `sharedListeners` la collection, auquel cas vous devez uniquement faire référence à celui-ci par son nom (Voir l' [exemple](#example)).<br /><br /> Spécifie le type de l’écouteur. Vous devez utiliser une chaîne qui répond aux exigences spécifiées dans [spécification de noms de types qualifiés complets](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).|  
|`initializeData`|Attribut facultatif.<br /><br /> Chaîne passée au constructeur pour la classe spécifiée. Une <xref:System.Configuration.ConfigurationException> exception est levée si la classe n’a pas de constructeur qui prend une chaîne.|  
|`name`|Attribut facultatif.<br /><br /> Spécifie le nom de l’écouteur.|  
|`traceOutputOptions`|Attribut facultatif.<br /><br /> Spécifie <xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A> la valeur de la propriété pour l’écouteur de la trace.|  
|[attributs personnalisés]|Attributs facultatifs.<br /><br /> Spécifie la valeur des attributs spécifiques de l’écouteur identifiés <xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A> par la méthode pour cet écouteur. <xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A>est un exemple d’attribut supplémentaire unique à la <xref:System.Diagnostics.DelimitedListTraceListener> classe.|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<filter>](filter-element-for-add-for-listeners-for-source.md)|Ajoute un filtre à un écouteur dans la collection `Listeners` pour une source de trace.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`system.diagnostics`|Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.|  
|`sources`|Contient les sources de trace qui lancent des messages de traçage.|  
|`source`|Spécifie une source de trace qui lance des messages de traçage.|  
|`listeners`|Spécifie les écouteurs qui collectent, stockent et acheminent les messages.|  
  
## <a name="remarks"></a>Notes  
 Les classes d’écouteur fournies avec le .NET Framework dérivent de la <xref:System.Diagnostics.TraceListener> classe.  
  
 Si vous ne spécifiez pas `name` l’attribut de l’écouteur de la <xref:System.Diagnostics.TraceListener.Name%2A> trace, la propriété de l’écouteur de la trace est définie par défaut sur une chaîne vide (""). Si votre application n’a qu’un seul écouteur, vous pouvez l’ajouter sans spécifier de nom et vous pouvez la supprimer en spécifiant une chaîne vide pour le nom. Toutefois, si votre application a plusieurs écouteurs, vous devez spécifier un nom unique pour chaque écouteur de suivi, ce qui vous permet d’identifier et de gérer des écouteurs de suivi individuels dans <xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType> la collection.  
  
> [!NOTE]
> L’ajout de plusieurs écouteurs de suivi du même type et portant le même nom n’entraîne l’ajout d’un seul écouteur de suivi de ce type et d’un `Listeners` même nom à la collection. Toutefois, vous pouvez ajouter par programmation plusieurs écouteurs identiques à la `Listeners` collection.  
  
 La valeur de l' `initializeData` attribut dépend du type d’écouteur que vous créez. Tous les écouteurs de suivi ne nécessitent pas que `initializeData`vous spécifiiez.  
  
> [!NOTE]
> Lorsque vous utilisez l' `initializeData` attribut, vous pouvez recevoir l’avertissement du compilateur «l’attribut’initializeData’n’est pas déclaré.» Cet avertissement se produit parce que les paramètres de configuration sont validés par <xref:System.Diagnostics.TraceListener>rapport à la classe de base `initializeData` abstraite, qui ne reconnaît pas l’attribut. En règle générale, vous pouvez ignorer cet avertissement pour les implémentations d’écouteurs de trace qui ont un constructeur qui prend un paramètre.  
  
 Le tableau suivant répertorie les écouteurs de suivi inclus avec le .NET Framework et décrit la valeur de leurs `initializeData` attributs.  
  
|Classe d’écouteur de suivi|valeur de l’attribut initializeData|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|`useErrorStream` Valeur<xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> du constructeur.  Affectez `initializeData` à l’attribut`true`la valeur «» pour écrire la sortie de trace et de débogage dans le flux`false`d’erreur standard; affectez-lui la valeur «» pour écrire dans le flux de sortie standard.|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|Nom du fichier <xref:System.Diagnostics.DelimitedListTraceListener> dans lequel écrit.|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|Nom d’une source de journal des événements existante.|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|Nom du fichier dans lequel <xref:System.Diagnostics.EventSchemaTraceListener> écrit.|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|Nom du fichier dans lequel <xref:System.Diagnostics.TextWriterTraceListener> écrit.|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|Nom du fichier dans lequel <xref:System.Diagnostics.XmlWriterTraceListener> écrit.|  
  
## <a name="configuration-file"></a>Fichier de configuration  
 Cet élément peut être utilisé dans le fichier de configuration de l’ordinateur (machine. config) et dans le fichier de configuration de l’application.  
  
## <a name="example"></a>Exemple  
 L’exemple `<add>` suivant montre comment utiliser des éléments pour ajouter les `console` écouteurs et `textListener` la `Listeners` collection pour la source `TraceSourceApp`de trace. L' `textListener` écouteur écrit la sortie de trace dans le fichier myListener. log.  
  
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
- [Schéma des paramètres de trace et de débogage](index.md)
- [Écouteurs de suivi](../../../debug-trace-profile/trace-listeners.md)
