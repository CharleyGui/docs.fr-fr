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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153605"
---
# <a name="add-element-for-sharedlisteners"></a>\<add>, élément de \<sharedListeners>
Ajoute un écouteur à la collection `sharedListeners`. `sharedListeners`est une collection d’écouteurs que tout [\<source>](source-element.md) ou [\<trace>](trace-element.md) peut référencer.  Par défaut, les écouteurs de la `sharedListeners` collection ne sont pas placés dans une `Listeners` collection. Ils doivent être ajoutés par nom au [\<source>](source-element.md) ou [\<trace>](trace-element.md) . Il n’est pas possible d’accéder aux écouteurs de la `sharedListeners` collection dans le code au moment de l’exécution.  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sharedListeners>**](sharedlisteners-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

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
|`name`|Attribut requis.<br /><br /> Spécifie le nom de l’écouteur utilisé pour ajouter l’écouteur partagé à une `Listeners` collection.|  
|`type`|Attribut requis.<br /><br /> Spécifie le type de l’écouteur. Vous devez utiliser une chaîne qui répond aux exigences spécifiées dans [spécification de noms de types qualifiés complets](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).|  
|`initializeData`|Attribut facultatif.<br /><br /> Chaîne passée au constructeur pour la classe spécifiée.|  
|`traceOutputOptions`|Attribut facultatif.<br/><br/>Représentation sous forme de chaîne d’un ou plusieurs membres de l' <xref:System.Diagnostics.TraceOptions> énumération qui indique les données à écrire dans la sortie de trace. Plusieurs éléments sont séparés par des virgules. La valeur par défaut est « None ».|

### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<filter>](filter-element-for-add-for-sharedlisteners.md)|Ajoute un filtre à un écouteur dans la collection `sharedListeners`.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`system.diagnostics`|Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.|  
|`sharedListeners`|Collection d’écouteurs qui peut faire référence à n’importe quel élément source ou trace.|  
  
## <a name="remarks"></a>Remarques  
 Les classes d’écouteur fournies avec le .NET Framework dérivent de la <xref:System.Diagnostics.TraceListener> classe. La valeur de l' `name` attribut est utilisée pour ajouter l’écouteur partagé à une `Listeners` collection pour une trace ou une source de trace. La valeur de l' `initializeData` attribut dépend du type d’écouteur que vous créez. Tous les écouteurs de suivi ne nécessitent pas que vous spécifiiez `initializeData` .  
  
> [!NOTE]
> Lorsque vous utilisez l' `initializeData` attribut, vous pouvez recevoir l’avertissement du compilateur « l’attribut’initializeData’n’est pas déclaré. » Cet avertissement se produit parce que les paramètres de configuration sont validés par rapport à la classe de base abstraite <xref:System.Diagnostics.TraceListener> , qui ne reconnaît pas l' `initializeData` attribut. En règle générale, vous pouvez ignorer cet avertissement pour les implémentations d’écouteurs de trace qui ont un constructeur qui prend un paramètre.  
  
 Le tableau suivant répertorie les écouteurs de suivi inclus avec le .NET Framework et décrit la valeur de leurs `initializeData` attributs.  
  
|Classe d’écouteur de suivi|valeur de l’attribut initializeData|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener>|`useErrorStream`Valeur du <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructeur.  Affectez à l’attribut la valeur « `initializeData` `true` » pour écrire la sortie de trace et de débogage dans le flux d’erreur standard ; affectez-lui la valeur « `false` » pour écrire dans le flux de sortie standard.|  
|<xref:System.Diagnostics.DelimitedListTraceListener>|Nom du fichier vers lequel <xref:System.Diagnostics.DelimitedListTraceListener> écrit.|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|Nom d'une source existante de journal des événements.|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|Nom du fichier <xref:System.Diagnostics.EventSchemaTraceListener> dans lequel écrit.|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|Nom du fichier <xref:System.Diagnostics.TextWriterTraceListener> dans lequel écrit.|  
|<xref:System.Diagnostics.XmlWriterTraceListener>|Nom du fichier <xref:System.Diagnostics.XmlWriterTraceListener> dans lequel écrit.|  
  
## <a name="configuration-file"></a>Fichier de configuration  
 Cet élément peut être utilisé dans le fichier de configuration de l’ordinateur (machine. config) et dans le fichier de configuration de l’application.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser des `<add>` éléments pour ajouter <xref:System.Diagnostics.TextWriterTraceListener> `textListener` à la `sharedListeners` collection.   `textListener`est ajouté par nom à la `Listeners` collection pour la source de suivi `TraceSourceApp` . L' `textListener` écouteur écrit la sortie de trace dans le fichier myListener. log.  
  
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
- [Schéma des paramètres de traçage et de débogage](index.md)
- [Écouteurs de suivi](../../../debug-trace-profile/trace-listeners.md)
