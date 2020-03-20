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
# <a name="add-element-for-listeners-for-source"></a><span data-ttu-id="ca769-102">\<ajouter> Element pour \<les auditeurs \<> pour les> de source</span><span class="sxs-lookup"><span data-stu-id="ca769-102">\<add> Element for \<listeners> for \<source></span></span>
<span data-ttu-id="ca769-103">Ajoute un écouteur à la collection `Listeners` pour une source de trace.</span><span class="sxs-lookup"><span data-stu-id="ca769-103">Adds a listener to the `Listeners` collection for a trace source.</span></span>  

<span data-ttu-id="ca769-104">[**\<configuration>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ca769-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ca769-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="ca769-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="ca769-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)</span><span class="sxs-lookup"><span data-stu-id="ca769-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)</span></span>\
<span data-ttu-id="ca769-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)</span><span class="sxs-lookup"><span data-stu-id="ca769-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)</span></span>\
<span data-ttu-id="ca769-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<auditeurs>**](listeners-element-for-source.md)</span><span class="sxs-lookup"><span data-stu-id="ca769-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-source.md)</span></span>\
<span data-ttu-id="ca769-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<ajouter>**</span><span class="sxs-lookup"><span data-stu-id="ca769-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="ca769-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ca769-110">Syntax</span></span>  
  
```xml  
<add name="name"
  type="TraceListenerClassName, Version, Culture, PublicKeyToken"  
  initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ca769-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="ca769-111">Attributes and Elements</span></span>  
 <span data-ttu-id="ca769-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="ca769-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ca769-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="ca769-113">Attributes</span></span>  
  
|<span data-ttu-id="ca769-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="ca769-114">Attribute</span></span>|<span data-ttu-id="ca769-115">Description</span><span class="sxs-lookup"><span data-stu-id="ca769-115">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="ca769-116">Attribut requis, sauf si vous faites référence `sharedListeners` à un auditeur dans la collection, auquel cas vous n’avez qu’à vous y référer par son nom (voir l’exemple ). [Example](#example)</span><span class="sxs-lookup"><span data-stu-id="ca769-116">Required attribute, unless you're referencing a listener in the `sharedListeners` collection, in which case you only need to refer to it by name (see the [Example](#example)).</span></span><br /><br /> <span data-ttu-id="ca769-117">Spécifie le type de l’auditeur.</span><span class="sxs-lookup"><span data-stu-id="ca769-117">Specifies the type of the listener.</span></span> <span data-ttu-id="ca769-118">Vous devez utiliser une chaîne qui répond aux exigences spécifiées dans [le spécifier des noms de type entièrement qualifiés](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="ca769-118">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="ca769-119">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="ca769-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="ca769-120">La chaîne passa au constructeur pour la classe spécifiée.</span><span class="sxs-lookup"><span data-stu-id="ca769-120">The string passed to the constructor for the specified class.</span></span> <span data-ttu-id="ca769-121">A <xref:System.Configuration.ConfigurationException> est jeté si la classe n’a pas un constructeur qui prend une ficelle.</span><span class="sxs-lookup"><span data-stu-id="ca769-121">A <xref:System.Configuration.ConfigurationException> is thrown if the class does not have a constructor that takes a string.</span></span>|  
|`name`|<span data-ttu-id="ca769-122">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="ca769-122">Optional attribute.</span></span><br /><br /> <span data-ttu-id="ca769-123">Spécifie le nom de l’auditeur.</span><span class="sxs-lookup"><span data-stu-id="ca769-123">Specifies the name of the listener.</span></span>|  
|`traceOutputOptions`|<span data-ttu-id="ca769-124">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="ca769-124">Optional attribute.</span></span><br /><br /> <span data-ttu-id="ca769-125">Spécifie la valeur de la <xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A> propriété pour l’auditeur de traces.</span><span class="sxs-lookup"><span data-stu-id="ca769-125">Specifies the <xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A> property value for the trace listener.</span></span>|  
|<span data-ttu-id="ca769-126">[attributs personnalisés]</span><span class="sxs-lookup"><span data-stu-id="ca769-126">[custom attributes]</span></span>|<span data-ttu-id="ca769-127">Attributs facultatifs.</span><span class="sxs-lookup"><span data-stu-id="ca769-127">Optional attributes.</span></span><br /><br /> <span data-ttu-id="ca769-128">Spécifie la valeur des attributs <xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A> spécifiques à l’auditeur identifiés par la méthode de cet auditeur.</span><span class="sxs-lookup"><span data-stu-id="ca769-128">Specifies the value for listener-specific attributes identified by the <xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A> method for that listener.</span></span> <span data-ttu-id="ca769-129"><xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A>est un exemple d’attribut <xref:System.Diagnostics.DelimitedListTraceListener> supplémentaire unique à la classe.</span><span class="sxs-lookup"><span data-stu-id="ca769-129"><xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> is an example of an extra attribute unique to the <xref:System.Diagnostics.DelimitedListTraceListener> class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ca769-130">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="ca769-130">Child Elements</span></span>  
  
|<span data-ttu-id="ca769-131">Élément</span><span class="sxs-lookup"><span data-stu-id="ca769-131">Element</span></span>|<span data-ttu-id="ca769-132">Description</span><span class="sxs-lookup"><span data-stu-id="ca769-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ca769-133">\<filtrer></span><span class="sxs-lookup"><span data-stu-id="ca769-133">\<filter></span></span>](filter-element-for-add-for-listeners-for-source.md)|<span data-ttu-id="ca769-134">Ajoute un filtre à un écouteur dans la collection `Listeners` pour une source de trace.</span><span class="sxs-lookup"><span data-stu-id="ca769-134">Adds a filter to a listener in the `Listeners` collection for a trace source.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ca769-135">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="ca769-135">Parent Elements</span></span>  
  
|<span data-ttu-id="ca769-136">Élément</span><span class="sxs-lookup"><span data-stu-id="ca769-136">Element</span></span>|<span data-ttu-id="ca769-137">Description</span><span class="sxs-lookup"><span data-stu-id="ca769-137">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="ca769-138">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ca769-138">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="ca769-139">Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.</span><span class="sxs-lookup"><span data-stu-id="ca769-139">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="ca769-140">Contient les sources de trace qui lancent des messages de traçage.</span><span class="sxs-lookup"><span data-stu-id="ca769-140">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="ca769-141">Spécifie une source de trace qui lance des messages de traçage.</span><span class="sxs-lookup"><span data-stu-id="ca769-141">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="ca769-142">Spécifie les auditeurs qui recueillent, stockent et acheminent les messages.</span><span class="sxs-lookup"><span data-stu-id="ca769-142">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ca769-143">Notes </span><span class="sxs-lookup"><span data-stu-id="ca769-143">Remarks</span></span>  
 <span data-ttu-id="ca769-144">Les classes d’auditeur expédiées avec <xref:System.Diagnostics.TraceListener> le cadre .NET dérivent de la classe.</span><span class="sxs-lookup"><span data-stu-id="ca769-144">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
 <span data-ttu-id="ca769-145">Si vous ne `name` spécifiez pas <xref:System.Diagnostics.TraceListener.Name%2A> l’attribut de l’auditeur de trace, la propriété de l’auditeur de traces manque à une chaîne vide («).).</span><span class="sxs-lookup"><span data-stu-id="ca769-145">If you do not specify the `name` attribute of the trace listener, the <xref:System.Diagnostics.TraceListener.Name%2A> property of the trace listener defaults to an empty string ("").</span></span> <span data-ttu-id="ca769-146">Si votre application n’a qu’un seul auditeur, vous pouvez l’ajouter sans spécifier un nom, et vous pouvez la supprimer en spécifiant une chaîne vide pour le nom.</span><span class="sxs-lookup"><span data-stu-id="ca769-146">If your application has only one listener, you can add it without specifying a name, and you can remove it by specifying an empty string for the name.</span></span> <span data-ttu-id="ca769-147">Toutefois, si votre application a plus d’un auditeur, vous devez spécifier un nom unique pour <xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType> chaque auditeur de traces, ce qui vous permet d’identifier et de gérer les auditeurs de traces individuelles dans la collection.</span><span class="sxs-lookup"><span data-stu-id="ca769-147">However, if your application has more than one listener, you should specify a unique name for each trace listener, which allows you to identify and manage individual trace listeners in the <xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType> collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ca769-148">L’ajout de plus d’un auditeur de traces du même type et avec le même `Listeners` nom n’entraîne qu’un seul auditeur de trace de ce type et le nom ajouté à la collection.</span><span class="sxs-lookup"><span data-stu-id="ca769-148">Adding more than one trace listener of the same type and with the same name results in only one trace listener of that type and name being added to the `Listeners` collection.</span></span> <span data-ttu-id="ca769-149">Cependant, vous pouvez programmer de `Listeners` façon programmatique plusieurs auditeurs identiques à la collection.</span><span class="sxs-lookup"><span data-stu-id="ca769-149">However, you can programmatically add multiple identical listeners to the `Listeners` collection.</span></span>  
  
 <span data-ttu-id="ca769-150">La valeur `initializeData` de l’attribut dépend du type d’auditeur que vous créez.</span><span class="sxs-lookup"><span data-stu-id="ca769-150">The value for the `initializeData` attribute depends on the type of listener you create.</span></span> <span data-ttu-id="ca769-151">Pas tous les auditeurs `initializeData`trace exigent que vous spécifiez .</span><span class="sxs-lookup"><span data-stu-id="ca769-151">Not all trace listeners require that you specify `initializeData`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ca769-152">Lorsque vous `initializeData` utilisez l’attribut, vous pouvez obtenir l’avertissement compilateur "L’attribut 'initializeData' n’est pas déclaré."</span><span class="sxs-lookup"><span data-stu-id="ca769-152">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="ca769-153">Cet avertissement se produit parce que les paramètres <xref:System.Diagnostics.TraceListener>de configuration sont `initializeData` validés par rapport à la classe de base abstraite , qui ne reconnaît pas l’attribut.</span><span class="sxs-lookup"><span data-stu-id="ca769-153">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="ca769-154">Typiquement, vous pouvez ignorer cet avertissement pour les implémentations d’auditeur de trace qui ont un constructeur qui prend un paramètre.</span><span class="sxs-lookup"><span data-stu-id="ca769-154">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="ca769-155">Le tableau suivant montre les auditeurs trace qui sont inclus dans `initializeData` le cadre .NET et décrit la valeur de leurs attributs.</span><span class="sxs-lookup"><span data-stu-id="ca769-155">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their `initializeData` attributes.</span></span>  
  
|<span data-ttu-id="ca769-156">Cours d’auditeur de trace</span><span class="sxs-lookup"><span data-stu-id="ca769-156">Trace listener class</span></span>|<span data-ttu-id="ca769-157">initialiser la valeur d’attribut deData</span><span class="sxs-lookup"><span data-stu-id="ca769-157">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|<span data-ttu-id="ca769-158">La `useErrorStream` valeur <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> pour le constructeur.</span><span class="sxs-lookup"><span data-stu-id="ca769-158">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="ca769-159">Définissez `initializeData` l’attribut à «`true`écrire la sortie de trace et de débaillement au flux d’erreurs standard ; l’a`false`fixé à " d’écrire au flux de sortie standard.</span><span class="sxs-lookup"><span data-stu-id="ca769-159">Set the `initializeData` attribute to "`true`" to write trace and debug output to the standard error stream; set it to "`false`" to write to the standard output stream.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|<span data-ttu-id="ca769-160">Nom du fichier vers lequel <xref:System.Diagnostics.DelimitedListTraceListener> écrit.</span><span class="sxs-lookup"><span data-stu-id="ca769-160">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="ca769-161">Nom d'une source existante de journal des événements.</span><span class="sxs-lookup"><span data-stu-id="ca769-161">The name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="ca769-162">Le nom du fichier <xref:System.Diagnostics.EventSchemaTraceListener> à qui le nom écrit.</span><span class="sxs-lookup"><span data-stu-id="ca769-162">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="ca769-163">Le nom du fichier <xref:System.Diagnostics.TextWriterTraceListener> à qui le nom écrit.</span><span class="sxs-lookup"><span data-stu-id="ca769-163">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="ca769-164">Le nom du fichier <xref:System.Diagnostics.XmlWriterTraceListener> à qui le nom écrit.</span><span class="sxs-lookup"><span data-stu-id="ca769-164">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="configuration-file"></a><span data-ttu-id="ca769-165">Fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="ca769-165">Configuration File</span></span>  
 <span data-ttu-id="ca769-166">Cet élément peut être utilisé dans le fichier de configuration de la machine (Machine.config) et le fichier de configuration d’application.</span><span class="sxs-lookup"><span data-stu-id="ca769-166">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ca769-167"> Exemple</span><span class="sxs-lookup"><span data-stu-id="ca769-167">Example</span></span>  
 <span data-ttu-id="ca769-168">L’exemple suivant montre `<add>` comment utiliser `console` des `textListener` éléments `Listeners` pour ajouter `TraceSourceApp`les auditeurs et à la collection pour la source de traces .</span><span class="sxs-lookup"><span data-stu-id="ca769-168">The following example shows how to use `<add>` elements to add the listeners `console` and `textListener` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span> <span data-ttu-id="ca769-169">L’auditeur `textListener` écrit trace sortie au fichier myListener.log.</span><span class="sxs-lookup"><span data-stu-id="ca769-169">The `textListener` listener writes trace output to the file myListener.log.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ca769-170">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ca769-170">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="ca769-171">Trace et Debug Paramètres Schema</span><span class="sxs-lookup"><span data-stu-id="ca769-171">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="ca769-172">Écouteurs de suivi</span><span class="sxs-lookup"><span data-stu-id="ca769-172">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
