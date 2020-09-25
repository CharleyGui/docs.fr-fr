---
title: <add> , Élément de <listeners> pour <source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add
helpviewer_keywords:
- initializeData attribute
- add element for <listeners> for <source>
- <add> element for <listeners> for <source>
ms.assetid: 4ce36ac1-81ef-48e8-b8b2-b5a5b0e2adcb
ms.openlocfilehash: a5abaffbad986785b8879297883da9614f0a8103
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201692"
---
# <a name="add-element-for-listeners-for-source"></a><span data-ttu-id="cb1be-102">\<add> , Élément de \<listeners> pour \<source></span><span class="sxs-lookup"><span data-stu-id="cb1be-102">\<add> Element for \<listeners> for \<source></span></span>

<span data-ttu-id="cb1be-103">Ajoute un écouteur à la collection `Listeners` pour une source de trace.</span><span class="sxs-lookup"><span data-stu-id="cb1be-103">Adds a listener to the `Listeners` collection for a trace source.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-source.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="cb1be-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cb1be-104">Syntax</span></span>  
  
```xml  
<add name="name"
  type="TraceListenerClassName, Version, Culture, PublicKeyToken"  
  initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cb1be-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="cb1be-105">Attributes and Elements</span></span>  

 <span data-ttu-id="cb1be-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="cb1be-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cb1be-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="cb1be-107">Attributes</span></span>  
  
|<span data-ttu-id="cb1be-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="cb1be-108">Attribute</span></span>|<span data-ttu-id="cb1be-109">Description</span><span class="sxs-lookup"><span data-stu-id="cb1be-109">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="cb1be-110">Attribut obligatoire, sauf si vous référencez un écouteur dans la `sharedListeners` collection, auquel cas vous devez uniquement faire référence à celui-ci par son nom (Voir l' [exemple](#example)).</span><span class="sxs-lookup"><span data-stu-id="cb1be-110">Required attribute, unless you're referencing a listener in the `sharedListeners` collection, in which case you only need to refer to it by name (see the [Example](#example)).</span></span><br /><br /> <span data-ttu-id="cb1be-111">Spécifie le type de l’écouteur.</span><span class="sxs-lookup"><span data-stu-id="cb1be-111">Specifies the type of the listener.</span></span> <span data-ttu-id="cb1be-112">Vous devez utiliser une chaîne qui répond aux exigences spécifiées dans [spécification de noms de types qualifiés complets](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="cb1be-112">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="cb1be-113">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="cb1be-113">Optional attribute.</span></span><br /><br /> <span data-ttu-id="cb1be-114">Chaîne passée au constructeur pour la classe spécifiée.</span><span class="sxs-lookup"><span data-stu-id="cb1be-114">The string passed to the constructor for the specified class.</span></span> <span data-ttu-id="cb1be-115">Une <xref:System.Configuration.ConfigurationException> exception est levée si la classe n’a pas de constructeur qui prend une chaîne.</span><span class="sxs-lookup"><span data-stu-id="cb1be-115">A <xref:System.Configuration.ConfigurationException> is thrown if the class does not have a constructor that takes a string.</span></span>|  
|`name`|<span data-ttu-id="cb1be-116">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="cb1be-116">Optional attribute.</span></span><br /><br /> <span data-ttu-id="cb1be-117">Spécifie le nom de l’écouteur.</span><span class="sxs-lookup"><span data-stu-id="cb1be-117">Specifies the name of the listener.</span></span>|  
|`traceOutputOptions`|<span data-ttu-id="cb1be-118">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="cb1be-118">Optional attribute.</span></span><br /><br /> <span data-ttu-id="cb1be-119">Spécifie la <xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A> valeur de la propriété pour l’écouteur de la trace.</span><span class="sxs-lookup"><span data-stu-id="cb1be-119">Specifies the <xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A> property value for the trace listener.</span></span>|  
|<span data-ttu-id="cb1be-120">[attributs personnalisés]</span><span class="sxs-lookup"><span data-stu-id="cb1be-120">[custom attributes]</span></span>|<span data-ttu-id="cb1be-121">Attributs facultatifs.</span><span class="sxs-lookup"><span data-stu-id="cb1be-121">Optional attributes.</span></span><br /><br /> <span data-ttu-id="cb1be-122">Spécifie la valeur des attributs spécifiques de l’écouteur identifiés par la <xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A> méthode pour cet écouteur.</span><span class="sxs-lookup"><span data-stu-id="cb1be-122">Specifies the value for listener-specific attributes identified by the <xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A> method for that listener.</span></span> <span data-ttu-id="cb1be-123"><xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> est un exemple d’attribut supplémentaire unique à la <xref:System.Diagnostics.DelimitedListTraceListener> classe.</span><span class="sxs-lookup"><span data-stu-id="cb1be-123"><xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> is an example of an extra attribute unique to the <xref:System.Diagnostics.DelimitedListTraceListener> class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cb1be-124">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="cb1be-124">Child Elements</span></span>  
  
|<span data-ttu-id="cb1be-125">Élément</span><span class="sxs-lookup"><span data-stu-id="cb1be-125">Element</span></span>|<span data-ttu-id="cb1be-126">Description</span><span class="sxs-lookup"><span data-stu-id="cb1be-126">Description</span></span>|  
|-------------|-----------------|  
|[\<filter>](filter-element-for-add-for-listeners-for-source.md)|<span data-ttu-id="cb1be-127">Ajoute un filtre à un écouteur dans la collection `Listeners` pour une source de trace.</span><span class="sxs-lookup"><span data-stu-id="cb1be-127">Adds a filter to a listener in the `Listeners` collection for a trace source.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cb1be-128">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="cb1be-128">Parent Elements</span></span>  
  
|<span data-ttu-id="cb1be-129">Élément</span><span class="sxs-lookup"><span data-stu-id="cb1be-129">Element</span></span>|<span data-ttu-id="cb1be-130">Description</span><span class="sxs-lookup"><span data-stu-id="cb1be-130">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="cb1be-131">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cb1be-131">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="cb1be-132">Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.</span><span class="sxs-lookup"><span data-stu-id="cb1be-132">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="cb1be-133">Contient les sources de trace qui lancent des messages de traçage.</span><span class="sxs-lookup"><span data-stu-id="cb1be-133">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="cb1be-134">Spécifie une source de trace qui lance des messages de traçage.</span><span class="sxs-lookup"><span data-stu-id="cb1be-134">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="cb1be-135">Spécifie les écouteurs qui collectent, stockent et acheminent les messages.</span><span class="sxs-lookup"><span data-stu-id="cb1be-135">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cb1be-136">Notes</span><span class="sxs-lookup"><span data-stu-id="cb1be-136">Remarks</span></span>  

 <span data-ttu-id="cb1be-137">Les classes d’écouteur fournies avec le .NET Framework dérivent de la <xref:System.Diagnostics.TraceListener> classe.</span><span class="sxs-lookup"><span data-stu-id="cb1be-137">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
 <span data-ttu-id="cb1be-138">Si vous ne spécifiez pas l' `name` attribut de l’écouteur de la trace, la <xref:System.Diagnostics.TraceListener.Name%2A> propriété de l’écouteur de la trace est définie par défaut sur une chaîne vide ("").</span><span class="sxs-lookup"><span data-stu-id="cb1be-138">If you do not specify the `name` attribute of the trace listener, the <xref:System.Diagnostics.TraceListener.Name%2A> property of the trace listener defaults to an empty string ("").</span></span> <span data-ttu-id="cb1be-139">Si votre application n’a qu’un seul écouteur, vous pouvez l’ajouter sans spécifier de nom et vous pouvez la supprimer en spécifiant une chaîne vide pour le nom.</span><span class="sxs-lookup"><span data-stu-id="cb1be-139">If your application has only one listener, you can add it without specifying a name, and you can remove it by specifying an empty string for the name.</span></span> <span data-ttu-id="cb1be-140">Toutefois, si votre application a plusieurs écouteurs, vous devez spécifier un nom unique pour chaque écouteur de suivi, ce qui vous permet d’identifier et de gérer des écouteurs de suivi individuels dans la <xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType> collection.</span><span class="sxs-lookup"><span data-stu-id="cb1be-140">However, if your application has more than one listener, you should specify a unique name for each trace listener, which allows you to identify and manage individual trace listeners in the <xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType> collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cb1be-141">L’ajout de plusieurs écouteurs de suivi du même type et portant le même nom n’entraîne l’ajout d’un seul écouteur de suivi de ce type et d’un même nom à la `Listeners` collection.</span><span class="sxs-lookup"><span data-stu-id="cb1be-141">Adding more than one trace listener of the same type and with the same name results in only one trace listener of that type and name being added to the `Listeners` collection.</span></span> <span data-ttu-id="cb1be-142">Toutefois, vous pouvez ajouter par programmation plusieurs écouteurs identiques à la `Listeners` collection.</span><span class="sxs-lookup"><span data-stu-id="cb1be-142">However, you can programmatically add multiple identical listeners to the `Listeners` collection.</span></span>  
  
 <span data-ttu-id="cb1be-143">La valeur de l' `initializeData` attribut dépend du type d’écouteur que vous créez.</span><span class="sxs-lookup"><span data-stu-id="cb1be-143">The value for the `initializeData` attribute depends on the type of listener you create.</span></span> <span data-ttu-id="cb1be-144">Tous les écouteurs de suivi ne nécessitent pas que vous spécifiiez `initializeData` .</span><span class="sxs-lookup"><span data-stu-id="cb1be-144">Not all trace listeners require that you specify `initializeData`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cb1be-145">Lorsque vous utilisez l' `initializeData` attribut, vous pouvez recevoir l’avertissement du compilateur « l’attribut’initializeData’n’est pas déclaré. »</span><span class="sxs-lookup"><span data-stu-id="cb1be-145">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="cb1be-146">Cet avertissement se produit parce que les paramètres de configuration sont validés par rapport à la classe de base abstraite <xref:System.Diagnostics.TraceListener> , qui ne reconnaît pas l' `initializeData` attribut.</span><span class="sxs-lookup"><span data-stu-id="cb1be-146">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="cb1be-147">En règle générale, vous pouvez ignorer cet avertissement pour les implémentations d’écouteurs de trace qui ont un constructeur qui prend un paramètre.</span><span class="sxs-lookup"><span data-stu-id="cb1be-147">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="cb1be-148">Le tableau suivant répertorie les écouteurs de suivi inclus avec le .NET Framework et décrit la valeur de leurs `initializeData` attributs.</span><span class="sxs-lookup"><span data-stu-id="cb1be-148">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their `initializeData` attributes.</span></span>  
  
|<span data-ttu-id="cb1be-149">Classe d’écouteur de suivi</span><span class="sxs-lookup"><span data-stu-id="cb1be-149">Trace listener class</span></span>|<span data-ttu-id="cb1be-150">valeur de l’attribut initializeData</span><span class="sxs-lookup"><span data-stu-id="cb1be-150">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|<span data-ttu-id="cb1be-151">`useErrorStream`Valeur du <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructeur.</span><span class="sxs-lookup"><span data-stu-id="cb1be-151">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="cb1be-152">Affectez à l’attribut la valeur « `initializeData` `true` » pour écrire la sortie de trace et de débogage dans le flux d’erreur standard ; affectez-lui la valeur « `false` » pour écrire dans le flux de sortie standard.</span><span class="sxs-lookup"><span data-stu-id="cb1be-152">Set the `initializeData` attribute to "`true`" to write trace and debug output to the standard error stream; set it to "`false`" to write to the standard output stream.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|<span data-ttu-id="cb1be-153">Nom du fichier vers lequel <xref:System.Diagnostics.DelimitedListTraceListener> écrit.</span><span class="sxs-lookup"><span data-stu-id="cb1be-153">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="cb1be-154">Nom d'une source existante de journal des événements.</span><span class="sxs-lookup"><span data-stu-id="cb1be-154">The name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="cb1be-155">Nom du fichier <xref:System.Diagnostics.EventSchemaTraceListener> dans lequel écrit.</span><span class="sxs-lookup"><span data-stu-id="cb1be-155">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="cb1be-156">Nom du fichier <xref:System.Diagnostics.TextWriterTraceListener> dans lequel écrit.</span><span class="sxs-lookup"><span data-stu-id="cb1be-156">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="cb1be-157">Nom du fichier <xref:System.Diagnostics.XmlWriterTraceListener> dans lequel écrit.</span><span class="sxs-lookup"><span data-stu-id="cb1be-157">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="configuration-file"></a><span data-ttu-id="cb1be-158">Fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="cb1be-158">Configuration File</span></span>  

 <span data-ttu-id="cb1be-159">Cet élément peut être utilisé dans le fichier de configuration de l’ordinateur (Machine.config) et dans le fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="cb1be-159">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cb1be-160">Exemple</span><span class="sxs-lookup"><span data-stu-id="cb1be-160">Example</span></span>  

 <span data-ttu-id="cb1be-161">L’exemple suivant montre comment utiliser des `<add>` éléments pour ajouter les écouteurs `console` et `textListener` la `Listeners` collection pour la source de trace `TraceSourceApp` .</span><span class="sxs-lookup"><span data-stu-id="cb1be-161">The following example shows how to use `<add>` elements to add the listeners `console` and `textListener` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span> <span data-ttu-id="cb1be-162">L' `textListener` écouteur écrit la sortie de trace dans le fichier myListener. log.</span><span class="sxs-lookup"><span data-stu-id="cb1be-162">The `textListener` listener writes trace output to the file myListener.log.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cb1be-163">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cb1be-163">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="cb1be-164">Schéma des paramètres de traçage et de débogage</span><span class="sxs-lookup"><span data-stu-id="cb1be-164">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="cb1be-165">Écouteurs de la trace</span><span class="sxs-lookup"><span data-stu-id="cb1be-165">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
