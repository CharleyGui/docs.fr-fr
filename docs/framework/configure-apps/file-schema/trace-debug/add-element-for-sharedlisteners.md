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
ms.openlocfilehash: 0c7665898f8c625c2d07b67ea6c7fe25113fddd8
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699478"
---
# <a name="add-element-for-sharedlisteners"></a><span data-ttu-id="4467b-102">\<add > élément de \<sharedListeners ></span><span class="sxs-lookup"><span data-stu-id="4467b-102">\<add> Element for \<sharedListeners></span></span>
<span data-ttu-id="4467b-103">Ajoute un écouteur à la collection `sharedListeners`.</span><span class="sxs-lookup"><span data-stu-id="4467b-103">Adds a listener to the `sharedListeners` collection.</span></span> <span data-ttu-id="4467b-104">`sharedListeners` est une collection d’écouteurs qui peut faire référence à tout [\<source >](source-element.md) ou [\<trace >](trace-element.md) .</span><span class="sxs-lookup"><span data-stu-id="4467b-104">`sharedListeners` is a collection of listeners that any [\<source>](source-element.md) or [\<trace>](trace-element.md) can reference.</span></span>  <span data-ttu-id="4467b-105">Par défaut, les écouteurs de la collection `sharedListeners` ne sont pas placés dans une collection `Listeners`.</span><span class="sxs-lookup"><span data-stu-id="4467b-105">By default, listeners in the `sharedListeners` collection are not placed in a `Listeners` collection.</span></span> <span data-ttu-id="4467b-106">Ils doivent être ajoutés par nom à la > [\<source >](source-element.md) ou [\<trace](trace-element.md).</span><span class="sxs-lookup"><span data-stu-id="4467b-106">They must be added by name to the [\<source>](source-element.md) or [\<trace>](trace-element.md).</span></span> <span data-ttu-id="4467b-107">Il n’est pas possible d’accéder aux écouteurs de la collection `sharedListeners` dans le code au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="4467b-107">It is not possible to get the listeners in the `sharedListeners` collection in code at run time.</span></span>  
  
[<span data-ttu-id="4467b-108"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="4467b-108">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="4467b-109">&nbsp; @ no__t-1[ **\<System. diagnostics >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="4467b-109">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>  
<span data-ttu-id="4467b-110">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<sharedListeners >** ](sharedlisteners-element.md)</span><span class="sxs-lookup"><span data-stu-id="4467b-110">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sharedListeners>**](sharedlisteners-element.md)</span></span>  
<span data-ttu-id="4467b-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Ajouter >**</span><span class="sxs-lookup"><span data-stu-id="4467b-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4467b-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4467b-112">Syntax</span></span>  
  
```xml  
<add name="name"   
  type="TraceListenerClassName, Version, Culture, PublicKeyToken"  
  initializeData="data"
  traceOutputOptions = "None"
/>  
```
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4467b-113">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="4467b-113">Attributes and Elements</span></span>  
 <span data-ttu-id="4467b-114">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="4467b-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4467b-115">Attributs</span><span class="sxs-lookup"><span data-stu-id="4467b-115">Attributes</span></span>  
  
|<span data-ttu-id="4467b-116">Attribut</span><span class="sxs-lookup"><span data-stu-id="4467b-116">Attribute</span></span>|<span data-ttu-id="4467b-117">Description</span><span class="sxs-lookup"><span data-stu-id="4467b-117">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="4467b-118">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="4467b-118">Required attribute.</span></span><br /><br /> <span data-ttu-id="4467b-119">Spécifie le nom de l’écouteur utilisé pour ajouter l’écouteur partagé à une collection `Listeners`.</span><span class="sxs-lookup"><span data-stu-id="4467b-119">Specifies the name of the listener that is used to add the shared listener to a `Listeners` collection.</span></span>|  
|`type`|<span data-ttu-id="4467b-120">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="4467b-120">Required attribute.</span></span><br /><br /> <span data-ttu-id="4467b-121">Spécifie le type de l’écouteur.</span><span class="sxs-lookup"><span data-stu-id="4467b-121">Specifies the type of the listener.</span></span> <span data-ttu-id="4467b-122">Vous devez utiliser une chaîne qui répond aux exigences spécifiées dans [spécification de noms de types qualifiés complets](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="4467b-122">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="4467b-123">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="4467b-123">Optional attribute.</span></span><br /><br /> <span data-ttu-id="4467b-124">Chaîne passée au constructeur pour la classe spécifiée.</span><span class="sxs-lookup"><span data-stu-id="4467b-124">The string passed to the constructor for the specified class.</span></span>|  
|`traceOutputOptions`|<span data-ttu-id="4467b-125">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="4467b-125">Optional attribute.</span></span><br/><br/><span data-ttu-id="4467b-126">Représentation sous forme de chaîne d’un ou plusieurs membres de l’énumération <xref:System.Diagnostics.TraceOptions> qui indique les données à écrire dans la sortie de trace.</span><span class="sxs-lookup"><span data-stu-id="4467b-126">The string representation of one or more <xref:System.Diagnostics.TraceOptions> enumeration members that indicates the data to be written to the trace output.</span></span> <span data-ttu-id="4467b-127">Plusieurs éléments sont séparés par des virgules.</span><span class="sxs-lookup"><span data-stu-id="4467b-127">Multiple items are separated by commas.</span></span> <span data-ttu-id="4467b-128">La valeur par défaut est « None ».</span><span class="sxs-lookup"><span data-stu-id="4467b-128">The default value is "None".</span></span>|

### <a name="child-elements"></a><span data-ttu-id="4467b-129">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="4467b-129">Child Elements</span></span>  
  
|<span data-ttu-id="4467b-130">Élément</span><span class="sxs-lookup"><span data-stu-id="4467b-130">Element</span></span>|<span data-ttu-id="4467b-131">Description</span><span class="sxs-lookup"><span data-stu-id="4467b-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4467b-132">\<filter></span><span class="sxs-lookup"><span data-stu-id="4467b-132">\<filter></span></span>](filter-element-for-add-for-sharedlisteners.md)|<span data-ttu-id="4467b-133">Ajoute un filtre à un écouteur dans la collection `sharedListeners`.</span><span class="sxs-lookup"><span data-stu-id="4467b-133">Adds a filter to a listener in the `sharedListeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4467b-134">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="4467b-134">Parent Elements</span></span>  
  
|<span data-ttu-id="4467b-135">Élément</span><span class="sxs-lookup"><span data-stu-id="4467b-135">Element</span></span>|<span data-ttu-id="4467b-136">Description</span><span class="sxs-lookup"><span data-stu-id="4467b-136">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="4467b-137">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4467b-137">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="4467b-138">Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.</span><span class="sxs-lookup"><span data-stu-id="4467b-138">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sharedListeners`|<span data-ttu-id="4467b-139">Collection d’écouteurs qui peut faire référence à n’importe quel élément source ou trace.</span><span class="sxs-lookup"><span data-stu-id="4467b-139">A collection of listeners that any source or trace element can reference.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4467b-140">Notes</span><span class="sxs-lookup"><span data-stu-id="4467b-140">Remarks</span></span>  
 <span data-ttu-id="4467b-141">Les classes d’écouteur fournies avec le .NET Framework dérivent de la classe <xref:System.Diagnostics.TraceListener>.</span><span class="sxs-lookup"><span data-stu-id="4467b-141">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span> <span data-ttu-id="4467b-142">La valeur de l’attribut `name` est utilisée pour ajouter l’écouteur partagé à une collection `Listeners` pour une trace ou une source de trace.</span><span class="sxs-lookup"><span data-stu-id="4467b-142">The value for the `name` attribute is used to add the shared listener to a `Listeners` collection for either a trace or a trace source.</span></span> <span data-ttu-id="4467b-143">La valeur de l’attribut `initializeData` dépend du type d’écouteur que vous créez.</span><span class="sxs-lookup"><span data-stu-id="4467b-143">The value for the `initializeData` attribute depends on the type of listener you create.</span></span> <span data-ttu-id="4467b-144">Tous les écouteurs de suivi ne nécessitent pas que vous spécifiiez `initializeData`.</span><span class="sxs-lookup"><span data-stu-id="4467b-144">Not all trace listeners require that you specify `initializeData`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4467b-145">Lorsque vous utilisez l’attribut `initializeData`, vous pouvez recevoir l’avertissement du compilateur « l’attribut’initializeData’n’est pas déclaré. »</span><span class="sxs-lookup"><span data-stu-id="4467b-145">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="4467b-146">Cet avertissement se produit parce que les paramètres de configuration sont validés par rapport à la classe de base abstraite <xref:System.Diagnostics.TraceListener>, qui ne reconnaît pas l’attribut `initializeData`.</span><span class="sxs-lookup"><span data-stu-id="4467b-146">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="4467b-147">En règle générale, vous pouvez ignorer cet avertissement pour les implémentations d’écouteurs de trace qui ont un constructeur qui prend un paramètre.</span><span class="sxs-lookup"><span data-stu-id="4467b-147">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="4467b-148">Le tableau suivant répertorie les écouteurs de suivi inclus avec le .NET Framework et décrit la valeur de leurs attributs `initializeData`.</span><span class="sxs-lookup"><span data-stu-id="4467b-148">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their `initializeData` attributes.</span></span>  
  
|<span data-ttu-id="4467b-149">Classe d’écouteur de suivi</span><span class="sxs-lookup"><span data-stu-id="4467b-149">Trace listener class</span></span>|<span data-ttu-id="4467b-150">valeur de l’attribut initializeData</span><span class="sxs-lookup"><span data-stu-id="4467b-150">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener>|<span data-ttu-id="4467b-151">La valeur `useErrorStream` pour le constructeur <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A>.</span><span class="sxs-lookup"><span data-stu-id="4467b-151">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="4467b-152">Affectez à l’attribut `initializeData` la valeur « `true` » pour écrire la sortie de trace et de débogage dans le flux d’erreurs standard. Affectez-lui la valeur « `false` » pour écrire dans le flux de sortie standard.</span><span class="sxs-lookup"><span data-stu-id="4467b-152">Set the `initializeData` attribute to "`true`" to write trace and debug output to the standard error stream; set it to "`false`" to write to the standard output stream.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener>|<span data-ttu-id="4467b-153">Nom du fichier dans lequel le <xref:System.Diagnostics.DelimitedListTraceListener> écrit.</span><span class="sxs-lookup"><span data-stu-id="4467b-153">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="4467b-154">Nom d’une source de journal des événements existante.</span><span class="sxs-lookup"><span data-stu-id="4467b-154">The name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="4467b-155">Nom du fichier dans lequel le <xref:System.Diagnostics.EventSchemaTraceListener> écrit.</span><span class="sxs-lookup"><span data-stu-id="4467b-155">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="4467b-156">Nom du fichier dans lequel le <xref:System.Diagnostics.TextWriterTraceListener> écrit.</span><span class="sxs-lookup"><span data-stu-id="4467b-156">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener>|<span data-ttu-id="4467b-157">Nom du fichier dans lequel le <xref:System.Diagnostics.XmlWriterTraceListener> écrit.</span><span class="sxs-lookup"><span data-stu-id="4467b-157">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="configuration-file"></a><span data-ttu-id="4467b-158">Fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="4467b-158">Configuration File</span></span>  
 <span data-ttu-id="4467b-159">Cet élément peut être utilisé dans le fichier de configuration de l’ordinateur (machine. config) et dans le fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="4467b-159">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4467b-160">Exemple</span><span class="sxs-lookup"><span data-stu-id="4467b-160">Example</span></span>  
 <span data-ttu-id="4467b-161">L’exemple suivant montre comment utiliser les éléments `<add>` pour ajouter la <xref:System.Diagnostics.TextWriterTraceListener> @ no__t-2 à la collection `sharedListeners`.</span><span class="sxs-lookup"><span data-stu-id="4467b-161">The following example shows how to use `<add>` elements to add the <xref:System.Diagnostics.TextWriterTraceListener>`textListener` to the `sharedListeners` collection.</span></span>   <span data-ttu-id="4467b-162">`textListener` est ajouté par nom à la collection `Listeners` pour la source de suivi `TraceSourceApp`.</span><span class="sxs-lookup"><span data-stu-id="4467b-162">`textListener` is added by name to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span> <span data-ttu-id="4467b-163">L’écouteur `textListener` écrit la sortie de trace dans le fichier myListener. log.</span><span class="sxs-lookup"><span data-stu-id="4467b-163">The `textListener` listener writes trace output to the file myListener.log.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4467b-164">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4467b-164">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="4467b-165">Schéma des paramètres de trace et de débogage</span><span class="sxs-lookup"><span data-stu-id="4467b-165">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="4467b-166">Écouteurs de suivi</span><span class="sxs-lookup"><span data-stu-id="4467b-166">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
