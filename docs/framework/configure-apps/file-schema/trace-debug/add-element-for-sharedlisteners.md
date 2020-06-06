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
# <a name="add-element-for-sharedlisteners"></a><span data-ttu-id="2d829-102">\<add>, élément de \<sharedListeners></span><span class="sxs-lookup"><span data-stu-id="2d829-102">\<add> Element for \<sharedListeners></span></span>
<span data-ttu-id="2d829-103">Ajoute un écouteur à la collection `sharedListeners`.</span><span class="sxs-lookup"><span data-stu-id="2d829-103">Adds a listener to the `sharedListeners` collection.</span></span> <span data-ttu-id="2d829-104">`sharedListeners`est une collection d’écouteurs que tout [\<source>](source-element.md) ou [\<trace>](trace-element.md) peut référencer.</span><span class="sxs-lookup"><span data-stu-id="2d829-104">`sharedListeners` is a collection of listeners that any [\<source>](source-element.md) or [\<trace>](trace-element.md) can reference.</span></span>  <span data-ttu-id="2d829-105">Par défaut, les écouteurs de la `sharedListeners` collection ne sont pas placés dans une `Listeners` collection.</span><span class="sxs-lookup"><span data-stu-id="2d829-105">By default, listeners in the `sharedListeners` collection are not placed in a `Listeners` collection.</span></span> <span data-ttu-id="2d829-106">Ils doivent être ajoutés par nom au [\<source>](source-element.md) ou [\<trace>](trace-element.md) .</span><span class="sxs-lookup"><span data-stu-id="2d829-106">They must be added by name to the [\<source>](source-element.md) or [\<trace>](trace-element.md).</span></span> <span data-ttu-id="2d829-107">Il n’est pas possible d’accéder aux écouteurs de la `sharedListeners` collection dans le code au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="2d829-107">It is not possible to get the listeners in the `sharedListeners` collection in code at run time.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sharedListeners>**](sharedlisteners-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="2d829-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2d829-108">Syntax</span></span>  
  
```xml  
<add name="name"
  type="TraceListenerClassName, Version, Culture, PublicKeyToken"  
  initializeData="data"
  traceOutputOptions = "None"
/>  
```
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2d829-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="2d829-109">Attributes and Elements</span></span>  
 <span data-ttu-id="2d829-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="2d829-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2d829-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="2d829-111">Attributes</span></span>  
  
|<span data-ttu-id="2d829-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="2d829-112">Attribute</span></span>|<span data-ttu-id="2d829-113">Description</span><span class="sxs-lookup"><span data-stu-id="2d829-113">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="2d829-114">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="2d829-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="2d829-115">Spécifie le nom de l’écouteur utilisé pour ajouter l’écouteur partagé à une `Listeners` collection.</span><span class="sxs-lookup"><span data-stu-id="2d829-115">Specifies the name of the listener that is used to add the shared listener to a `Listeners` collection.</span></span>|  
|`type`|<span data-ttu-id="2d829-116">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="2d829-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="2d829-117">Spécifie le type de l’écouteur.</span><span class="sxs-lookup"><span data-stu-id="2d829-117">Specifies the type of the listener.</span></span> <span data-ttu-id="2d829-118">Vous devez utiliser une chaîne qui répond aux exigences spécifiées dans [spécification de noms de types qualifiés complets](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="2d829-118">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="2d829-119">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="2d829-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="2d829-120">Chaîne passée au constructeur pour la classe spécifiée.</span><span class="sxs-lookup"><span data-stu-id="2d829-120">The string passed to the constructor for the specified class.</span></span>|  
|`traceOutputOptions`|<span data-ttu-id="2d829-121">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="2d829-121">Optional attribute.</span></span><br/><br/><span data-ttu-id="2d829-122">Représentation sous forme de chaîne d’un ou plusieurs membres de l' <xref:System.Diagnostics.TraceOptions> énumération qui indique les données à écrire dans la sortie de trace.</span><span class="sxs-lookup"><span data-stu-id="2d829-122">The string representation of one or more <xref:System.Diagnostics.TraceOptions> enumeration members that indicates the data to be written to the trace output.</span></span> <span data-ttu-id="2d829-123">Plusieurs éléments sont séparés par des virgules.</span><span class="sxs-lookup"><span data-stu-id="2d829-123">Multiple items are separated by commas.</span></span> <span data-ttu-id="2d829-124">La valeur par défaut est « None ».</span><span class="sxs-lookup"><span data-stu-id="2d829-124">The default value is "None".</span></span>|

### <a name="child-elements"></a><span data-ttu-id="2d829-125">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="2d829-125">Child Elements</span></span>  
  
|<span data-ttu-id="2d829-126">Élément</span><span class="sxs-lookup"><span data-stu-id="2d829-126">Element</span></span>|<span data-ttu-id="2d829-127">Description</span><span class="sxs-lookup"><span data-stu-id="2d829-127">Description</span></span>|  
|-------------|-----------------|  
|[\<filter>](filter-element-for-add-for-sharedlisteners.md)|<span data-ttu-id="2d829-128">Ajoute un filtre à un écouteur dans la collection `sharedListeners`.</span><span class="sxs-lookup"><span data-stu-id="2d829-128">Adds a filter to a listener in the `sharedListeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2d829-129">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="2d829-129">Parent Elements</span></span>  
  
|<span data-ttu-id="2d829-130">Élément</span><span class="sxs-lookup"><span data-stu-id="2d829-130">Element</span></span>|<span data-ttu-id="2d829-131">Description</span><span class="sxs-lookup"><span data-stu-id="2d829-131">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="2d829-132">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2d829-132">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="2d829-133">Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.</span><span class="sxs-lookup"><span data-stu-id="2d829-133">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sharedListeners`|<span data-ttu-id="2d829-134">Collection d’écouteurs qui peut faire référence à n’importe quel élément source ou trace.</span><span class="sxs-lookup"><span data-stu-id="2d829-134">A collection of listeners that any source or trace element can reference.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2d829-135">Remarques</span><span class="sxs-lookup"><span data-stu-id="2d829-135">Remarks</span></span>  
 <span data-ttu-id="2d829-136">Les classes d’écouteur fournies avec le .NET Framework dérivent de la <xref:System.Diagnostics.TraceListener> classe.</span><span class="sxs-lookup"><span data-stu-id="2d829-136">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span> <span data-ttu-id="2d829-137">La valeur de l' `name` attribut est utilisée pour ajouter l’écouteur partagé à une `Listeners` collection pour une trace ou une source de trace.</span><span class="sxs-lookup"><span data-stu-id="2d829-137">The value for the `name` attribute is used to add the shared listener to a `Listeners` collection for either a trace or a trace source.</span></span> <span data-ttu-id="2d829-138">La valeur de l' `initializeData` attribut dépend du type d’écouteur que vous créez.</span><span class="sxs-lookup"><span data-stu-id="2d829-138">The value for the `initializeData` attribute depends on the type of listener you create.</span></span> <span data-ttu-id="2d829-139">Tous les écouteurs de suivi ne nécessitent pas que vous spécifiiez `initializeData` .</span><span class="sxs-lookup"><span data-stu-id="2d829-139">Not all trace listeners require that you specify `initializeData`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2d829-140">Lorsque vous utilisez l' `initializeData` attribut, vous pouvez recevoir l’avertissement du compilateur « l’attribut’initializeData’n’est pas déclaré. »</span><span class="sxs-lookup"><span data-stu-id="2d829-140">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="2d829-141">Cet avertissement se produit parce que les paramètres de configuration sont validés par rapport à la classe de base abstraite <xref:System.Diagnostics.TraceListener> , qui ne reconnaît pas l' `initializeData` attribut.</span><span class="sxs-lookup"><span data-stu-id="2d829-141">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="2d829-142">En règle générale, vous pouvez ignorer cet avertissement pour les implémentations d’écouteurs de trace qui ont un constructeur qui prend un paramètre.</span><span class="sxs-lookup"><span data-stu-id="2d829-142">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="2d829-143">Le tableau suivant répertorie les écouteurs de suivi inclus avec le .NET Framework et décrit la valeur de leurs `initializeData` attributs.</span><span class="sxs-lookup"><span data-stu-id="2d829-143">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their `initializeData` attributes.</span></span>  
  
|<span data-ttu-id="2d829-144">Classe d’écouteur de suivi</span><span class="sxs-lookup"><span data-stu-id="2d829-144">Trace listener class</span></span>|<span data-ttu-id="2d829-145">valeur de l’attribut initializeData</span><span class="sxs-lookup"><span data-stu-id="2d829-145">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener>|<span data-ttu-id="2d829-146">`useErrorStream`Valeur du <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructeur.</span><span class="sxs-lookup"><span data-stu-id="2d829-146">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="2d829-147">Affectez à l’attribut la valeur « `initializeData` `true` » pour écrire la sortie de trace et de débogage dans le flux d’erreur standard ; affectez-lui la valeur « `false` » pour écrire dans le flux de sortie standard.</span><span class="sxs-lookup"><span data-stu-id="2d829-147">Set the `initializeData` attribute to "`true`" to write trace and debug output to the standard error stream; set it to "`false`" to write to the standard output stream.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener>|<span data-ttu-id="2d829-148">Nom du fichier vers lequel <xref:System.Diagnostics.DelimitedListTraceListener> écrit.</span><span class="sxs-lookup"><span data-stu-id="2d829-148">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="2d829-149">Nom d'une source existante de journal des événements.</span><span class="sxs-lookup"><span data-stu-id="2d829-149">The name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="2d829-150">Nom du fichier <xref:System.Diagnostics.EventSchemaTraceListener> dans lequel écrit.</span><span class="sxs-lookup"><span data-stu-id="2d829-150">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="2d829-151">Nom du fichier <xref:System.Diagnostics.TextWriterTraceListener> dans lequel écrit.</span><span class="sxs-lookup"><span data-stu-id="2d829-151">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener>|<span data-ttu-id="2d829-152">Nom du fichier <xref:System.Diagnostics.XmlWriterTraceListener> dans lequel écrit.</span><span class="sxs-lookup"><span data-stu-id="2d829-152">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="configuration-file"></a><span data-ttu-id="2d829-153">Fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="2d829-153">Configuration File</span></span>  
 <span data-ttu-id="2d829-154">Cet élément peut être utilisé dans le fichier de configuration de l’ordinateur (machine. config) et dans le fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="2d829-154">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2d829-155">Exemple</span><span class="sxs-lookup"><span data-stu-id="2d829-155">Example</span></span>  
 <span data-ttu-id="2d829-156">L’exemple suivant montre comment utiliser des `<add>` éléments pour ajouter <xref:System.Diagnostics.TextWriterTraceListener> `textListener` à la `sharedListeners` collection.</span><span class="sxs-lookup"><span data-stu-id="2d829-156">The following example shows how to use `<add>` elements to add the <xref:System.Diagnostics.TextWriterTraceListener>`textListener` to the `sharedListeners` collection.</span></span>   <span data-ttu-id="2d829-157">`textListener`est ajouté par nom à la `Listeners` collection pour la source de suivi `TraceSourceApp` .</span><span class="sxs-lookup"><span data-stu-id="2d829-157">`textListener` is added by name to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span> <span data-ttu-id="2d829-158">L' `textListener` écouteur écrit la sortie de trace dans le fichier myListener. log.</span><span class="sxs-lookup"><span data-stu-id="2d829-158">The `textListener` listener writes trace output to the file myListener.log.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2d829-159">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2d829-159">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="2d829-160">Schéma des paramètres de traçage et de débogage</span><span class="sxs-lookup"><span data-stu-id="2d829-160">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="2d829-161">Écouteurs de suivi</span><span class="sxs-lookup"><span data-stu-id="2d829-161">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
