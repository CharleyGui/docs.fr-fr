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
# <a name="add-element-for-listeners-for-source"></a><span data-ttu-id="c7dd8-102">\<Ajouter > élément pour \<les écouteurs > pour \<le > source</span><span class="sxs-lookup"><span data-stu-id="c7dd8-102">\<add> Element for \<listeners> for \<source></span></span>
<span data-ttu-id="c7dd8-103">Ajoute un écouteur à la collection `Listeners` pour une source de trace.</span><span class="sxs-lookup"><span data-stu-id="c7dd8-103">Adds a listener to the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="c7dd8-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="c7dd8-104">\<configuration></span></span>  
<span data-ttu-id="c7dd8-105">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="c7dd8-105">\<system.diagnostics></span></span>  
<span data-ttu-id="c7dd8-106">\<sources></span><span class="sxs-lookup"><span data-stu-id="c7dd8-106">\<sources></span></span>  
<span data-ttu-id="c7dd8-107">\<> source</span><span class="sxs-lookup"><span data-stu-id="c7dd8-107">\<source></span></span>  
<span data-ttu-id="c7dd8-108">\<listeners></span><span class="sxs-lookup"><span data-stu-id="c7dd8-108">\<listeners></span></span>  
<span data-ttu-id="c7dd8-109">\<add></span><span class="sxs-lookup"><span data-stu-id="c7dd8-109">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7dd8-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c7dd8-110">Syntax</span></span>  
  
```xml  
<add name="name"   
  type="TraceListenerClassName, Version, Culture, PublicKeyToken"  
  initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c7dd8-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="c7dd8-111">Attributes and Elements</span></span>  
 <span data-ttu-id="c7dd8-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="c7dd8-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c7dd8-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="c7dd8-113">Attributes</span></span>  
  
|<span data-ttu-id="c7dd8-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="c7dd8-114">Attribute</span></span>|<span data-ttu-id="c7dd8-115">Description</span><span class="sxs-lookup"><span data-stu-id="c7dd8-115">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="c7dd8-116">Attribut obligatoire, sauf si vous référencez un écouteur dans `sharedListeners` la collection, auquel cas vous devez uniquement faire référence à celui-ci par son nom (Voir l' [exemple](#example)).</span><span class="sxs-lookup"><span data-stu-id="c7dd8-116">Required attribute, unless you're referencing a listener in the `sharedListeners` collection, in which case you only need to refer to it by name (see the [Example](#example)).</span></span><br /><br /> <span data-ttu-id="c7dd8-117">Spécifie le type de l’écouteur.</span><span class="sxs-lookup"><span data-stu-id="c7dd8-117">Specifies the type of the listener.</span></span> <span data-ttu-id="c7dd8-118">Vous devez utiliser une chaîne qui répond aux exigences spécifiées dans [spécification de noms de types qualifiés complets](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="c7dd8-118">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="c7dd8-119">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="c7dd8-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="c7dd8-120">Chaîne passée au constructeur pour la classe spécifiée.</span><span class="sxs-lookup"><span data-stu-id="c7dd8-120">The string passed to the constructor for the specified class.</span></span> <span data-ttu-id="c7dd8-121">Une <xref:System.Configuration.ConfigurationException> exception est levée si la classe n’a pas de constructeur qui prend une chaîne.</span><span class="sxs-lookup"><span data-stu-id="c7dd8-121">A <xref:System.Configuration.ConfigurationException> is thrown if the class does not have a constructor that takes a string.</span></span>|  
|`name`|<span data-ttu-id="c7dd8-122">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="c7dd8-122">Optional attribute.</span></span><br /><br /> <span data-ttu-id="c7dd8-123">Spécifie le nom de l’écouteur.</span><span class="sxs-lookup"><span data-stu-id="c7dd8-123">Specifies the name of the listener.</span></span>|  
|`traceOutputOptions`|<span data-ttu-id="c7dd8-124">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="c7dd8-124">Optional attribute.</span></span><br /><br /> <span data-ttu-id="c7dd8-125">Spécifie <xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A> la valeur de la propriété pour l’écouteur de la trace.</span><span class="sxs-lookup"><span data-stu-id="c7dd8-125">Specifies the <xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A> property value for the trace listener.</span></span>|  
|<span data-ttu-id="c7dd8-126">[attributs personnalisés]</span><span class="sxs-lookup"><span data-stu-id="c7dd8-126">[custom attributes]</span></span>|<span data-ttu-id="c7dd8-127">Attributs facultatifs.</span><span class="sxs-lookup"><span data-stu-id="c7dd8-127">Optional attributes.</span></span><br /><br /> <span data-ttu-id="c7dd8-128">Spécifie la valeur des attributs spécifiques de l’écouteur identifiés <xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A> par la méthode pour cet écouteur.</span><span class="sxs-lookup"><span data-stu-id="c7dd8-128">Specifies the value for listener-specific attributes identified by the <xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A> method for that listener.</span></span> <span data-ttu-id="c7dd8-129"><xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A>est un exemple d’attribut supplémentaire unique à la <xref:System.Diagnostics.DelimitedListTraceListener> classe.</span><span class="sxs-lookup"><span data-stu-id="c7dd8-129"><xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> is an example of an extra attribute unique to the <xref:System.Diagnostics.DelimitedListTraceListener> class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c7dd8-130">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="c7dd8-130">Child Elements</span></span>  
  
|<span data-ttu-id="c7dd8-131">Élément</span><span class="sxs-lookup"><span data-stu-id="c7dd8-131">Element</span></span>|<span data-ttu-id="c7dd8-132">Description</span><span class="sxs-lookup"><span data-stu-id="c7dd8-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c7dd8-133">\<filter></span><span class="sxs-lookup"><span data-stu-id="c7dd8-133">\<filter></span></span>](filter-element-for-add-for-listeners-for-source.md)|<span data-ttu-id="c7dd8-134">Ajoute un filtre à un écouteur dans la collection `Listeners` pour une source de trace.</span><span class="sxs-lookup"><span data-stu-id="c7dd8-134">Adds a filter to a listener in the `Listeners` collection for a trace source.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c7dd8-135">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="c7dd8-135">Parent Elements</span></span>  
  
|<span data-ttu-id="c7dd8-136">Élément</span><span class="sxs-lookup"><span data-stu-id="c7dd8-136">Element</span></span>|<span data-ttu-id="c7dd8-137">Description</span><span class="sxs-lookup"><span data-stu-id="c7dd8-137">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="c7dd8-138">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c7dd8-138">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="c7dd8-139">Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.</span><span class="sxs-lookup"><span data-stu-id="c7dd8-139">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="c7dd8-140">Contient les sources de trace qui lancent des messages de traçage.</span><span class="sxs-lookup"><span data-stu-id="c7dd8-140">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="c7dd8-141">Spécifie une source de trace qui lance des messages de traçage.</span><span class="sxs-lookup"><span data-stu-id="c7dd8-141">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="c7dd8-142">Spécifie les écouteurs qui collectent, stockent et acheminent les messages.</span><span class="sxs-lookup"><span data-stu-id="c7dd8-142">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c7dd8-143">Notes</span><span class="sxs-lookup"><span data-stu-id="c7dd8-143">Remarks</span></span>  
 <span data-ttu-id="c7dd8-144">Les classes d’écouteur fournies avec le .NET Framework dérivent de la <xref:System.Diagnostics.TraceListener> classe.</span><span class="sxs-lookup"><span data-stu-id="c7dd8-144">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
 <span data-ttu-id="c7dd8-145">Si vous ne spécifiez pas `name` l’attribut de l’écouteur de la <xref:System.Diagnostics.TraceListener.Name%2A> trace, la propriété de l’écouteur de la trace est définie par défaut sur une chaîne vide ("").</span><span class="sxs-lookup"><span data-stu-id="c7dd8-145">If you do not specify the `name` attribute of the trace listener, the <xref:System.Diagnostics.TraceListener.Name%2A> property of the trace listener defaults to an empty string ("").</span></span> <span data-ttu-id="c7dd8-146">Si votre application n’a qu’un seul écouteur, vous pouvez l’ajouter sans spécifier de nom et vous pouvez la supprimer en spécifiant une chaîne vide pour le nom.</span><span class="sxs-lookup"><span data-stu-id="c7dd8-146">If your application has only one listener, you can add it without specifying a name, and you can remove it by specifying an empty string for the name.</span></span> <span data-ttu-id="c7dd8-147">Toutefois, si votre application a plusieurs écouteurs, vous devez spécifier un nom unique pour chaque écouteur de suivi, ce qui vous permet d’identifier et de gérer des écouteurs de suivi individuels dans <xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType> la collection.</span><span class="sxs-lookup"><span data-stu-id="c7dd8-147">However, if your application has more than one listener, you should specify a unique name for each trace listener, which allows you to identify and manage individual trace listeners in the <xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType> collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c7dd8-148">L’ajout de plusieurs écouteurs de suivi du même type et portant le même nom n’entraîne l’ajout d’un seul écouteur de suivi de ce type et d’un `Listeners` même nom à la collection.</span><span class="sxs-lookup"><span data-stu-id="c7dd8-148">Adding more than one trace listener of the same type and with the same name results in only one trace listener of that type and name being added to the `Listeners` collection.</span></span> <span data-ttu-id="c7dd8-149">Toutefois, vous pouvez ajouter par programmation plusieurs écouteurs identiques à la `Listeners` collection.</span><span class="sxs-lookup"><span data-stu-id="c7dd8-149">However, you can programmatically add multiple identical listeners to the `Listeners` collection.</span></span>  
  
 <span data-ttu-id="c7dd8-150">La valeur de l' `initializeData` attribut dépend du type d’écouteur que vous créez.</span><span class="sxs-lookup"><span data-stu-id="c7dd8-150">The value for the `initializeData` attribute depends on the type of listener you create.</span></span> <span data-ttu-id="c7dd8-151">Tous les écouteurs de suivi ne nécessitent pas que `initializeData`vous spécifiiez.</span><span class="sxs-lookup"><span data-stu-id="c7dd8-151">Not all trace listeners require that you specify `initializeData`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c7dd8-152">Lorsque vous utilisez l' `initializeData` attribut, vous pouvez recevoir l’avertissement du compilateur «l’attribut’initializeData’n’est pas déclaré.»</span><span class="sxs-lookup"><span data-stu-id="c7dd8-152">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="c7dd8-153">Cet avertissement se produit parce que les paramètres de configuration sont validés par <xref:System.Diagnostics.TraceListener>rapport à la classe de base `initializeData` abstraite, qui ne reconnaît pas l’attribut.</span><span class="sxs-lookup"><span data-stu-id="c7dd8-153">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="c7dd8-154">En règle générale, vous pouvez ignorer cet avertissement pour les implémentations d’écouteurs de trace qui ont un constructeur qui prend un paramètre.</span><span class="sxs-lookup"><span data-stu-id="c7dd8-154">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="c7dd8-155">Le tableau suivant répertorie les écouteurs de suivi inclus avec le .NET Framework et décrit la valeur de leurs `initializeData` attributs.</span><span class="sxs-lookup"><span data-stu-id="c7dd8-155">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their `initializeData` attributes.</span></span>  
  
|<span data-ttu-id="c7dd8-156">Classe d’écouteur de suivi</span><span class="sxs-lookup"><span data-stu-id="c7dd8-156">Trace listener class</span></span>|<span data-ttu-id="c7dd8-157">valeur de l’attribut initializeData</span><span class="sxs-lookup"><span data-stu-id="c7dd8-157">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|<span data-ttu-id="c7dd8-158">`useErrorStream` Valeur<xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> du constructeur.</span><span class="sxs-lookup"><span data-stu-id="c7dd8-158">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="c7dd8-159">Affectez `initializeData` à l’attribut`true`la valeur «» pour écrire la sortie de trace et de débogage dans le flux`false`d’erreur standard; affectez-lui la valeur «» pour écrire dans le flux de sortie standard.</span><span class="sxs-lookup"><span data-stu-id="c7dd8-159">Set the `initializeData` attribute to "`true`" to write trace and debug output to the standard error stream; set it to "`false`" to write to the standard output stream.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|<span data-ttu-id="c7dd8-160">Nom du fichier <xref:System.Diagnostics.DelimitedListTraceListener> dans lequel écrit.</span><span class="sxs-lookup"><span data-stu-id="c7dd8-160">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="c7dd8-161">Nom d’une source de journal des événements existante.</span><span class="sxs-lookup"><span data-stu-id="c7dd8-161">The name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="c7dd8-162">Nom du fichier dans lequel <xref:System.Diagnostics.EventSchemaTraceListener> écrit.</span><span class="sxs-lookup"><span data-stu-id="c7dd8-162">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="c7dd8-163">Nom du fichier dans lequel <xref:System.Diagnostics.TextWriterTraceListener> écrit.</span><span class="sxs-lookup"><span data-stu-id="c7dd8-163">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="c7dd8-164">Nom du fichier dans lequel <xref:System.Diagnostics.XmlWriterTraceListener> écrit.</span><span class="sxs-lookup"><span data-stu-id="c7dd8-164">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="configuration-file"></a><span data-ttu-id="c7dd8-165">Fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="c7dd8-165">Configuration File</span></span>  
 <span data-ttu-id="c7dd8-166">Cet élément peut être utilisé dans le fichier de configuration de l’ordinateur (machine. config) et dans le fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="c7dd8-166">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c7dd8-167">Exemple</span><span class="sxs-lookup"><span data-stu-id="c7dd8-167">Example</span></span>  
 <span data-ttu-id="c7dd8-168">L’exemple `<add>` suivant montre comment utiliser des éléments pour ajouter les `console` écouteurs et `textListener` la `Listeners` collection pour la source `TraceSourceApp`de trace.</span><span class="sxs-lookup"><span data-stu-id="c7dd8-168">The following example shows how to use `<add>` elements to add the listeners `console` and `textListener` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span> <span data-ttu-id="c7dd8-169">L' `textListener` écouteur écrit la sortie de trace dans le fichier myListener. log.</span><span class="sxs-lookup"><span data-stu-id="c7dd8-169">The `textListener` listener writes trace output to the file myListener.log.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c7dd8-170">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c7dd8-170">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="c7dd8-171">Schéma des paramètres de trace et de débogage</span><span class="sxs-lookup"><span data-stu-id="c7dd8-171">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="c7dd8-172">Écouteurs de suivi</span><span class="sxs-lookup"><span data-stu-id="c7dd8-172">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
