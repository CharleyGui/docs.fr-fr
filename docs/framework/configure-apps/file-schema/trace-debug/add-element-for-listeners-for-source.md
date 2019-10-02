---
title: Élément <add> pour <listeners> pour <source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add
helpviewer_keywords:
- initializeData attribute
- add element for <listeners> for <source>
- <add> element for <listeners> for <source>
ms.assetid: 4ce36ac1-81ef-48e8-b8b2-b5a5b0e2adcb
ms.openlocfilehash: 0818d7ec248b210f215759069b9f69a3e29637f5
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699400"
---
# <a name="add-element-for-listeners-for-source"></a><span data-ttu-id="31c66-102">\<add > élément de \<listeners > pour \<Source ></span><span class="sxs-lookup"><span data-stu-id="31c66-102">\<add> Element for \<listeners> for \<source></span></span>
<span data-ttu-id="31c66-103">Ajoute un écouteur à la collection `Listeners` pour une source de trace.</span><span class="sxs-lookup"><span data-stu-id="31c66-103">Adds a listener to the `Listeners` collection for a trace source.</span></span>  
  
[<span data-ttu-id="31c66-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="31c66-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="31c66-105">&nbsp; @ no__t-1[ **\<System. diagnostics >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="31c66-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>  
<span data-ttu-id="31c66-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<sources >** ](sources-element.md)</span><span class="sxs-lookup"><span data-stu-id="31c66-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)</span></span>  
<span data-ttu-id="31c66-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5[ **\<source >** ](source-element.md)</span><span class="sxs-lookup"><span data-stu-id="31c66-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)</span></span>  
<span data-ttu-id="31c66-108">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7[ **&nbsp;0listeners >** ](listeners-element-for-source.md)</span><span class="sxs-lookup"><span data-stu-id="31c66-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-source.md)</span></span>  
<span data-ttu-id="31c66-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<add>**</span><span class="sxs-lookup"><span data-stu-id="31c66-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31c66-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="31c66-110">Syntax</span></span>  
  
```xml  
<add name="name"   
  type="TraceListenerClassName, Version, Culture, PublicKeyToken"  
  initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="31c66-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="31c66-111">Attributes and Elements</span></span>  
 <span data-ttu-id="31c66-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="31c66-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="31c66-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="31c66-113">Attributes</span></span>  
  
|<span data-ttu-id="31c66-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="31c66-114">Attribute</span></span>|<span data-ttu-id="31c66-115">Description</span><span class="sxs-lookup"><span data-stu-id="31c66-115">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="31c66-116">Attribut obligatoire, sauf si vous faites référence à un écouteur dans la collection `sharedListeners`, auquel cas vous devez uniquement faire référence à celui-ci par son nom (Voir l' [exemple](#example)).</span><span class="sxs-lookup"><span data-stu-id="31c66-116">Required attribute, unless you're referencing a listener in the `sharedListeners` collection, in which case you only need to refer to it by name (see the [Example](#example)).</span></span><br /><br /> <span data-ttu-id="31c66-117">Spécifie le type de l’écouteur.</span><span class="sxs-lookup"><span data-stu-id="31c66-117">Specifies the type of the listener.</span></span> <span data-ttu-id="31c66-118">Vous devez utiliser une chaîne qui répond aux exigences spécifiées dans [spécification de noms de types qualifiés complets](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="31c66-118">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="31c66-119">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="31c66-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="31c66-120">Chaîne passée au constructeur pour la classe spécifiée.</span><span class="sxs-lookup"><span data-stu-id="31c66-120">The string passed to the constructor for the specified class.</span></span> <span data-ttu-id="31c66-121">Une <xref:System.Configuration.ConfigurationException> est levée si la classe n’a pas de constructeur qui prend une chaîne.</span><span class="sxs-lookup"><span data-stu-id="31c66-121">A <xref:System.Configuration.ConfigurationException> is thrown if the class does not have a constructor that takes a string.</span></span>|  
|`name`|<span data-ttu-id="31c66-122">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="31c66-122">Optional attribute.</span></span><br /><br /> <span data-ttu-id="31c66-123">Spécifie le nom de l’écouteur.</span><span class="sxs-lookup"><span data-stu-id="31c66-123">Specifies the name of the listener.</span></span>|  
|`traceOutputOptions`|<span data-ttu-id="31c66-124">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="31c66-124">Optional attribute.</span></span><br /><br /> <span data-ttu-id="31c66-125">Spécifie la valeur de la propriété <xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A> pour l’écouteur de la trace.</span><span class="sxs-lookup"><span data-stu-id="31c66-125">Specifies the <xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A> property value for the trace listener.</span></span>|  
|<span data-ttu-id="31c66-126">[attributs personnalisés]</span><span class="sxs-lookup"><span data-stu-id="31c66-126">[custom attributes]</span></span>|<span data-ttu-id="31c66-127">Attributs facultatifs.</span><span class="sxs-lookup"><span data-stu-id="31c66-127">Optional attributes.</span></span><br /><br /> <span data-ttu-id="31c66-128">Spécifie la valeur des attributs spécifiques à l’écouteur identifiés par la méthode <xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A> pour cet écouteur.</span><span class="sxs-lookup"><span data-stu-id="31c66-128">Specifies the value for listener-specific attributes identified by the <xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A> method for that listener.</span></span> <span data-ttu-id="31c66-129"><xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> est un exemple d’attribut supplémentaire unique à la classe <xref:System.Diagnostics.DelimitedListTraceListener>.</span><span class="sxs-lookup"><span data-stu-id="31c66-129"><xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> is an example of an extra attribute unique to the <xref:System.Diagnostics.DelimitedListTraceListener> class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="31c66-130">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="31c66-130">Child Elements</span></span>  
  
|<span data-ttu-id="31c66-131">Élément</span><span class="sxs-lookup"><span data-stu-id="31c66-131">Element</span></span>|<span data-ttu-id="31c66-132">Description</span><span class="sxs-lookup"><span data-stu-id="31c66-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="31c66-133">\<filter></span><span class="sxs-lookup"><span data-stu-id="31c66-133">\<filter></span></span>](filter-element-for-add-for-listeners-for-source.md)|<span data-ttu-id="31c66-134">Ajoute un filtre à un écouteur dans la collection `Listeners` pour une source de trace.</span><span class="sxs-lookup"><span data-stu-id="31c66-134">Adds a filter to a listener in the `Listeners` collection for a trace source.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="31c66-135">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="31c66-135">Parent Elements</span></span>  
  
|<span data-ttu-id="31c66-136">Élément</span><span class="sxs-lookup"><span data-stu-id="31c66-136">Element</span></span>|<span data-ttu-id="31c66-137">Description</span><span class="sxs-lookup"><span data-stu-id="31c66-137">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="31c66-138">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="31c66-138">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="31c66-139">Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.</span><span class="sxs-lookup"><span data-stu-id="31c66-139">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="31c66-140">Contient les sources de trace qui lancent des messages de traçage.</span><span class="sxs-lookup"><span data-stu-id="31c66-140">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="31c66-141">Spécifie une source de trace qui lance des messages de traçage.</span><span class="sxs-lookup"><span data-stu-id="31c66-141">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="31c66-142">Spécifie les écouteurs qui collectent, stockent et acheminent les messages.</span><span class="sxs-lookup"><span data-stu-id="31c66-142">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="31c66-143">Notes</span><span class="sxs-lookup"><span data-stu-id="31c66-143">Remarks</span></span>  
 <span data-ttu-id="31c66-144">Les classes d’écouteur fournies avec le .NET Framework dérivent de la classe <xref:System.Diagnostics.TraceListener>.</span><span class="sxs-lookup"><span data-stu-id="31c66-144">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
 <span data-ttu-id="31c66-145">Si vous ne spécifiez pas l’attribut `name` de l’écouteur de la trace, la propriété <xref:System.Diagnostics.TraceListener.Name%2A> de l’écouteur de la trace est définie par défaut sur une chaîne vide ("").</span><span class="sxs-lookup"><span data-stu-id="31c66-145">If you do not specify the `name` attribute of the trace listener, the <xref:System.Diagnostics.TraceListener.Name%2A> property of the trace listener defaults to an empty string ("").</span></span> <span data-ttu-id="31c66-146">Si votre application n’a qu’un seul écouteur, vous pouvez l’ajouter sans spécifier de nom et vous pouvez la supprimer en spécifiant une chaîne vide pour le nom.</span><span class="sxs-lookup"><span data-stu-id="31c66-146">If your application has only one listener, you can add it without specifying a name, and you can remove it by specifying an empty string for the name.</span></span> <span data-ttu-id="31c66-147">Toutefois, si votre application a plusieurs écouteurs, vous devez spécifier un nom unique pour chaque écouteur de suivi, ce qui vous permet d’identifier et de gérer des écouteurs de suivi individuels dans la collection <xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="31c66-147">However, if your application has more than one listener, you should specify a unique name for each trace listener, which allows you to identify and manage individual trace listeners in the <xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType> collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="31c66-148">L’ajout de plusieurs écouteurs de suivi du même type et portant le même nom entraîne l’ajout d’un seul écouteur de suivi de ce type et d’un nom à la collection `Listeners`.</span><span class="sxs-lookup"><span data-stu-id="31c66-148">Adding more than one trace listener of the same type and with the same name results in only one trace listener of that type and name being added to the `Listeners` collection.</span></span> <span data-ttu-id="31c66-149">Toutefois, vous pouvez ajouter par programmation plusieurs écouteurs identiques à la collection `Listeners`.</span><span class="sxs-lookup"><span data-stu-id="31c66-149">However, you can programmatically add multiple identical listeners to the `Listeners` collection.</span></span>  
  
 <span data-ttu-id="31c66-150">La valeur de l’attribut `initializeData` dépend du type d’écouteur que vous créez.</span><span class="sxs-lookup"><span data-stu-id="31c66-150">The value for the `initializeData` attribute depends on the type of listener you create.</span></span> <span data-ttu-id="31c66-151">Tous les écouteurs de suivi ne nécessitent pas que vous spécifiiez `initializeData`.</span><span class="sxs-lookup"><span data-stu-id="31c66-151">Not all trace listeners require that you specify `initializeData`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="31c66-152">Lorsque vous utilisez l’attribut `initializeData`, vous pouvez recevoir l’avertissement du compilateur « l’attribut’initializeData’n’est pas déclaré. »</span><span class="sxs-lookup"><span data-stu-id="31c66-152">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="31c66-153">Cet avertissement se produit parce que les paramètres de configuration sont validés par rapport à la classe de base abstraite <xref:System.Diagnostics.TraceListener>, qui ne reconnaît pas l’attribut `initializeData`.</span><span class="sxs-lookup"><span data-stu-id="31c66-153">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="31c66-154">En règle générale, vous pouvez ignorer cet avertissement pour les implémentations d’écouteurs de trace qui ont un constructeur qui prend un paramètre.</span><span class="sxs-lookup"><span data-stu-id="31c66-154">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="31c66-155">Le tableau suivant répertorie les écouteurs de suivi inclus avec le .NET Framework et décrit la valeur de leurs attributs `initializeData`.</span><span class="sxs-lookup"><span data-stu-id="31c66-155">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their `initializeData` attributes.</span></span>  
  
|<span data-ttu-id="31c66-156">Classe d’écouteur de suivi</span><span class="sxs-lookup"><span data-stu-id="31c66-156">Trace listener class</span></span>|<span data-ttu-id="31c66-157">valeur de l’attribut initializeData</span><span class="sxs-lookup"><span data-stu-id="31c66-157">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|<span data-ttu-id="31c66-158">La valeur `useErrorStream` pour le constructeur <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A>.</span><span class="sxs-lookup"><span data-stu-id="31c66-158">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="31c66-159">Affectez à l’attribut `initializeData` la valeur « `true` » pour écrire la sortie de trace et de débogage dans le flux d’erreurs standard. Affectez-lui la valeur « `false` » pour écrire dans le flux de sortie standard.</span><span class="sxs-lookup"><span data-stu-id="31c66-159">Set the `initializeData` attribute to "`true`" to write trace and debug output to the standard error stream; set it to "`false`" to write to the standard output stream.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|<span data-ttu-id="31c66-160">Nom du fichier dans lequel le <xref:System.Diagnostics.DelimitedListTraceListener> écrit.</span><span class="sxs-lookup"><span data-stu-id="31c66-160">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="31c66-161">Nom d’une source de journal des événements existante.</span><span class="sxs-lookup"><span data-stu-id="31c66-161">The name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="31c66-162">Nom du fichier dans lequel le <xref:System.Diagnostics.EventSchemaTraceListener> écrit.</span><span class="sxs-lookup"><span data-stu-id="31c66-162">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="31c66-163">Nom du fichier dans lequel le <xref:System.Diagnostics.TextWriterTraceListener> écrit.</span><span class="sxs-lookup"><span data-stu-id="31c66-163">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="31c66-164">Nom du fichier dans lequel le <xref:System.Diagnostics.XmlWriterTraceListener> écrit.</span><span class="sxs-lookup"><span data-stu-id="31c66-164">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="configuration-file"></a><span data-ttu-id="31c66-165">Fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="31c66-165">Configuration File</span></span>  
 <span data-ttu-id="31c66-166">Cet élément peut être utilisé dans le fichier de configuration de l’ordinateur (machine. config) et dans le fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="31c66-166">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="31c66-167">Exemple</span><span class="sxs-lookup"><span data-stu-id="31c66-167">Example</span></span>  
 <span data-ttu-id="31c66-168">L’exemple suivant montre comment utiliser les éléments `<add>` pour ajouter les écouteurs `console` et `textListener` à la collection `Listeners` pour la source de trace `TraceSourceApp`.</span><span class="sxs-lookup"><span data-stu-id="31c66-168">The following example shows how to use `<add>` elements to add the listeners `console` and `textListener` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span> <span data-ttu-id="31c66-169">L’écouteur `textListener` écrit la sortie de trace dans le fichier myListener. log.</span><span class="sxs-lookup"><span data-stu-id="31c66-169">The `textListener` listener writes trace output to the file myListener.log.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="31c66-170">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="31c66-170">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="31c66-171">Schéma des paramètres de trace et de débogage</span><span class="sxs-lookup"><span data-stu-id="31c66-171">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="31c66-172">Écouteurs de suivi</span><span class="sxs-lookup"><span data-stu-id="31c66-172">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
