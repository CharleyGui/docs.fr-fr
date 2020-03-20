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
# <a name="add-element-for-sharedlisteners"></a><span data-ttu-id="acc4e-102">\<ajouter> Element pour \<les> sharedListeners</span><span class="sxs-lookup"><span data-stu-id="acc4e-102">\<add> Element for \<sharedListeners></span></span>
<span data-ttu-id="acc4e-103">Ajoute un écouteur à la collection `sharedListeners`.</span><span class="sxs-lookup"><span data-stu-id="acc4e-103">Adds a listener to the `sharedListeners` collection.</span></span> <span data-ttu-id="acc4e-104">`sharedListeners`est une collection d’auditeurs que toute [ \<source>](source-element.md) ou [ \<trace>](trace-element.md) peut référencer.</span><span class="sxs-lookup"><span data-stu-id="acc4e-104">`sharedListeners` is a collection of listeners that any [\<source>](source-element.md) or [\<trace>](trace-element.md) can reference.</span></span>  <span data-ttu-id="acc4e-105">Par défaut, les `sharedListeners` auditeurs de `Listeners` la collection ne sont pas placés dans une collection.</span><span class="sxs-lookup"><span data-stu-id="acc4e-105">By default, listeners in the `sharedListeners` collection are not placed in a `Listeners` collection.</span></span> <span data-ttu-id="acc4e-106">Ils doivent être ajoutés [ \<](source-element.md) par leur nom à la source>ou [ \<tracer>](trace-element.md).</span><span class="sxs-lookup"><span data-stu-id="acc4e-106">They must be added by name to the [\<source>](source-element.md) or [\<trace>](trace-element.md).</span></span> <span data-ttu-id="acc4e-107">Il n’est pas possible `sharedListeners` d’obtenir les auditeurs dans la collection dans le code à l’heure d’exécution.</span><span class="sxs-lookup"><span data-stu-id="acc4e-107">It is not possible to get the listeners in the `sharedListeners` collection in code at run time.</span></span>  

<span data-ttu-id="acc4e-108">[**\<configuration>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="acc4e-108">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="acc4e-109">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="acc4e-109">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="acc4e-110">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sharedListeners>**](sharedlisteners-element.md)</span><span class="sxs-lookup"><span data-stu-id="acc4e-110">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sharedListeners>**](sharedlisteners-element.md)</span></span>\
<span data-ttu-id="acc4e-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<ajouter>**</span><span class="sxs-lookup"><span data-stu-id="acc4e-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="acc4e-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="acc4e-112">Syntax</span></span>  
  
```xml  
<add name="name"
  type="TraceListenerClassName, Version, Culture, PublicKeyToken"  
  initializeData="data"
  traceOutputOptions = "None"
/>  
```
  
## <a name="attributes-and-elements"></a><span data-ttu-id="acc4e-113">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="acc4e-113">Attributes and Elements</span></span>  
 <span data-ttu-id="acc4e-114">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="acc4e-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="acc4e-115">Attributs</span><span class="sxs-lookup"><span data-stu-id="acc4e-115">Attributes</span></span>  
  
|<span data-ttu-id="acc4e-116">Attribut</span><span class="sxs-lookup"><span data-stu-id="acc4e-116">Attribute</span></span>|<span data-ttu-id="acc4e-117">Description</span><span class="sxs-lookup"><span data-stu-id="acc4e-117">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="acc4e-118">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="acc4e-118">Required attribute.</span></span><br /><br /> <span data-ttu-id="acc4e-119">Spécifie le nom de l’auditeur qui est `Listeners` utilisé pour ajouter l’auditeur partagé à une collection.</span><span class="sxs-lookup"><span data-stu-id="acc4e-119">Specifies the name of the listener that is used to add the shared listener to a `Listeners` collection.</span></span>|  
|`type`|<span data-ttu-id="acc4e-120">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="acc4e-120">Required attribute.</span></span><br /><br /> <span data-ttu-id="acc4e-121">Spécifie le type de l’auditeur.</span><span class="sxs-lookup"><span data-stu-id="acc4e-121">Specifies the type of the listener.</span></span> <span data-ttu-id="acc4e-122">Vous devez utiliser une chaîne qui répond aux exigences spécifiées dans [le spécifier des noms de type entièrement qualifiés](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="acc4e-122">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="acc4e-123">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="acc4e-123">Optional attribute.</span></span><br /><br /> <span data-ttu-id="acc4e-124">La chaîne passa au constructeur pour la classe spécifiée.</span><span class="sxs-lookup"><span data-stu-id="acc4e-124">The string passed to the constructor for the specified class.</span></span>|  
|`traceOutputOptions`|<span data-ttu-id="acc4e-125">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="acc4e-125">Optional attribute.</span></span><br/><br/><span data-ttu-id="acc4e-126">La représentation des chaînes <xref:System.Diagnostics.TraceOptions> d’un ou de plusieurs membres qui indique les données à écrire à la sortie de traces.</span><span class="sxs-lookup"><span data-stu-id="acc4e-126">The string representation of one or more <xref:System.Diagnostics.TraceOptions> enumeration members that indicates the data to be written to the trace output.</span></span> <span data-ttu-id="acc4e-127">Plusieurs articles sont séparés par des virgules.</span><span class="sxs-lookup"><span data-stu-id="acc4e-127">Multiple items are separated by commas.</span></span> <span data-ttu-id="acc4e-128">La valeur par défaut est "Aucun".</span><span class="sxs-lookup"><span data-stu-id="acc4e-128">The default value is "None".</span></span>|

### <a name="child-elements"></a><span data-ttu-id="acc4e-129">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="acc4e-129">Child Elements</span></span>  
  
|<span data-ttu-id="acc4e-130">Élément</span><span class="sxs-lookup"><span data-stu-id="acc4e-130">Element</span></span>|<span data-ttu-id="acc4e-131">Description</span><span class="sxs-lookup"><span data-stu-id="acc4e-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="acc4e-132">\<filtrer></span><span class="sxs-lookup"><span data-stu-id="acc4e-132">\<filter></span></span>](filter-element-for-add-for-sharedlisteners.md)|<span data-ttu-id="acc4e-133">Ajoute un filtre à un écouteur dans la collection `sharedListeners`.</span><span class="sxs-lookup"><span data-stu-id="acc4e-133">Adds a filter to a listener in the `sharedListeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="acc4e-134">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="acc4e-134">Parent Elements</span></span>  
  
|<span data-ttu-id="acc4e-135">Élément</span><span class="sxs-lookup"><span data-stu-id="acc4e-135">Element</span></span>|<span data-ttu-id="acc4e-136">Description</span><span class="sxs-lookup"><span data-stu-id="acc4e-136">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="acc4e-137">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="acc4e-137">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="acc4e-138">Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.</span><span class="sxs-lookup"><span data-stu-id="acc4e-138">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sharedListeners`|<span data-ttu-id="acc4e-139">Une collection d’auditeurs que toute source ou élément de trace peut référencer.</span><span class="sxs-lookup"><span data-stu-id="acc4e-139">A collection of listeners that any source or trace element can reference.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="acc4e-140">Notes </span><span class="sxs-lookup"><span data-stu-id="acc4e-140">Remarks</span></span>  
 <span data-ttu-id="acc4e-141">Les classes d’auditeur expédiées avec <xref:System.Diagnostics.TraceListener> le cadre .NET dérivent de la classe.</span><span class="sxs-lookup"><span data-stu-id="acc4e-141">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span> <span data-ttu-id="acc4e-142">La valeur `name` de l’attribut est utilisée pour `Listeners` ajouter l’auditeur partagé à une collection pour une trace ou une source de trace.</span><span class="sxs-lookup"><span data-stu-id="acc4e-142">The value for the `name` attribute is used to add the shared listener to a `Listeners` collection for either a trace or a trace source.</span></span> <span data-ttu-id="acc4e-143">La valeur `initializeData` de l’attribut dépend du type d’auditeur que vous créez.</span><span class="sxs-lookup"><span data-stu-id="acc4e-143">The value for the `initializeData` attribute depends on the type of listener you create.</span></span> <span data-ttu-id="acc4e-144">Pas tous les auditeurs `initializeData`trace exigent que vous spécifiez .</span><span class="sxs-lookup"><span data-stu-id="acc4e-144">Not all trace listeners require that you specify `initializeData`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="acc4e-145">Lorsque vous `initializeData` utilisez l’attribut, vous pouvez obtenir l’avertissement compilateur "L’attribut 'initializeData' n’est pas déclaré."</span><span class="sxs-lookup"><span data-stu-id="acc4e-145">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="acc4e-146">Cet avertissement se produit parce que les paramètres <xref:System.Diagnostics.TraceListener>de configuration sont `initializeData` validés par rapport à la classe de base abstraite , qui ne reconnaît pas l’attribut.</span><span class="sxs-lookup"><span data-stu-id="acc4e-146">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="acc4e-147">Typiquement, vous pouvez ignorer cet avertissement pour les implémentations d’auditeur de trace qui ont un constructeur qui prend un paramètre.</span><span class="sxs-lookup"><span data-stu-id="acc4e-147">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="acc4e-148">Le tableau suivant montre les auditeurs trace qui sont inclus dans `initializeData` le cadre .NET et décrit la valeur de leurs attributs.</span><span class="sxs-lookup"><span data-stu-id="acc4e-148">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their `initializeData` attributes.</span></span>  
  
|<span data-ttu-id="acc4e-149">Cours d’auditeur de trace</span><span class="sxs-lookup"><span data-stu-id="acc4e-149">Trace listener class</span></span>|<span data-ttu-id="acc4e-150">initialiser la valeur d’attribut deData</span><span class="sxs-lookup"><span data-stu-id="acc4e-150">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener>|<span data-ttu-id="acc4e-151">La `useErrorStream` valeur <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> pour le constructeur.</span><span class="sxs-lookup"><span data-stu-id="acc4e-151">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="acc4e-152">Définissez `initializeData` l’attribut à «`true`écrire la sortie de trace et de débaillement au flux d’erreurs standard ; l’a`false`fixé à " d’écrire au flux de sortie standard.</span><span class="sxs-lookup"><span data-stu-id="acc4e-152">Set the `initializeData` attribute to "`true`" to write trace and debug output to the standard error stream; set it to "`false`" to write to the standard output stream.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener>|<span data-ttu-id="acc4e-153">Nom du fichier vers lequel <xref:System.Diagnostics.DelimitedListTraceListener> écrit.</span><span class="sxs-lookup"><span data-stu-id="acc4e-153">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="acc4e-154">Nom d'une source existante de journal des événements.</span><span class="sxs-lookup"><span data-stu-id="acc4e-154">The name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="acc4e-155">Le nom du fichier <xref:System.Diagnostics.EventSchemaTraceListener> à qui le nom écrit.</span><span class="sxs-lookup"><span data-stu-id="acc4e-155">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="acc4e-156">Le nom du fichier <xref:System.Diagnostics.TextWriterTraceListener> à qui le nom écrit.</span><span class="sxs-lookup"><span data-stu-id="acc4e-156">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener>|<span data-ttu-id="acc4e-157">Le nom du fichier <xref:System.Diagnostics.XmlWriterTraceListener> à qui le nom écrit.</span><span class="sxs-lookup"><span data-stu-id="acc4e-157">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="configuration-file"></a><span data-ttu-id="acc4e-158">Fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="acc4e-158">Configuration File</span></span>  
 <span data-ttu-id="acc4e-159">Cet élément peut être utilisé dans le fichier de configuration de la machine (Machine.config) et le fichier de configuration d’application.</span><span class="sxs-lookup"><span data-stu-id="acc4e-159">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="acc4e-160"> Exemple</span><span class="sxs-lookup"><span data-stu-id="acc4e-160">Example</span></span>  
 <span data-ttu-id="acc4e-161">L’exemple suivant montre `<add>` comment utiliser <xref:System.Diagnostics.TextWriterTraceListener> `textListener` des `sharedListeners` éléments pour ajouter la collection.</span><span class="sxs-lookup"><span data-stu-id="acc4e-161">The following example shows how to use `<add>` elements to add the <xref:System.Diagnostics.TextWriterTraceListener>`textListener` to the `sharedListeners` collection.</span></span>   <span data-ttu-id="acc4e-162">`textListener`est ajouté par `Listeners` son nom à `TraceSourceApp`la collection pour la source de traces .</span><span class="sxs-lookup"><span data-stu-id="acc4e-162">`textListener` is added by name to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span> <span data-ttu-id="acc4e-163">L’auditeur `textListener` écrit trace sortie au fichier myListener.log.</span><span class="sxs-lookup"><span data-stu-id="acc4e-163">The `textListener` listener writes trace output to the file myListener.log.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="acc4e-164">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="acc4e-164">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="acc4e-165">Trace et Debug Paramètres Schema</span><span class="sxs-lookup"><span data-stu-id="acc4e-165">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="acc4e-166">Écouteurs de suivi</span><span class="sxs-lookup"><span data-stu-id="acc4e-166">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
