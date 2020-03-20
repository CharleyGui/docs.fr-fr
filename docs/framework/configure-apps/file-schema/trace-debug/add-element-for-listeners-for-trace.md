---
title: <add>Élément <listeners> pour pour<trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add
helpviewer_keywords:
- initializeData attribute
- <add> element for <listeners>
- add element for <listeners>
ms.assetid: 81e804a3-ef11-4d39-bbde-bfa012c179e2
ms.openlocfilehash: c64673908dc9afe67d97c08f93e5b9d9533bd34d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153670"
---
# <a name="add-element-for-listeners-for-trace"></a><span data-ttu-id="034f3-102">\<ajouter> Element pour \<les auditeurs \<> pour les traces></span><span class="sxs-lookup"><span data-stu-id="034f3-102">\<add> Element for \<listeners> for \<trace></span></span>
<span data-ttu-id="034f3-103">Ajoute un auditeur à la collection **Listeners.**</span><span class="sxs-lookup"><span data-stu-id="034f3-103">Adds a listener to the **Listeners** collection.</span></span>  

<span data-ttu-id="034f3-104">[**\<configuration>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="034f3-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="034f3-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="034f3-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="034f3-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)</span><span class="sxs-lookup"><span data-stu-id="034f3-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)</span></span>\
<span data-ttu-id="034f3-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<auditeurs>**](listeners-element-for-trace.md)</span><span class="sxs-lookup"><span data-stu-id="034f3-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-trace.md)</span></span>\
<span data-ttu-id="034f3-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<ajouter>**</span><span class="sxs-lookup"><span data-stu-id="034f3-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="034f3-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="034f3-109">Syntax</span></span>  
  
```xml  
<add name="name"
     type="trace listener class name, Version, Culture, PublicKeyToken"  
     initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="034f3-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="034f3-110">Attributes and Elements</span></span>  
 <span data-ttu-id="034f3-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="034f3-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="034f3-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="034f3-112">Attributes</span></span>  
  
|<span data-ttu-id="034f3-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="034f3-113">Attribute</span></span>|<span data-ttu-id="034f3-114">Description</span><span class="sxs-lookup"><span data-stu-id="034f3-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="034f3-115">**type**</span><span class="sxs-lookup"><span data-stu-id="034f3-115">**type**</span></span>|<span data-ttu-id="034f3-116">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="034f3-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="034f3-117">Spécifie le type de l’auditeur.</span><span class="sxs-lookup"><span data-stu-id="034f3-117">Specifies the type of the listener.</span></span> <span data-ttu-id="034f3-118">Vous devez utiliser une chaîne qui répond aux exigences spécifiées dans [le spécifier des noms de type entièrement qualifiés](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="034f3-118">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|<span data-ttu-id="034f3-119">**initialiserData**</span><span class="sxs-lookup"><span data-stu-id="034f3-119">**initializeData**</span></span>|<span data-ttu-id="034f3-120">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="034f3-120">Optional attribute.</span></span><br /><br /> <span data-ttu-id="034f3-121">La chaîne passa au constructeur pour la classe spécifiée.</span><span class="sxs-lookup"><span data-stu-id="034f3-121">The string passed to the constructor for the specified class.</span></span>|  
|<span data-ttu-id="034f3-122">**name**</span><span class="sxs-lookup"><span data-stu-id="034f3-122">**name**</span></span>|<span data-ttu-id="034f3-123">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="034f3-123">Optional attribute.</span></span><br /><br /> <span data-ttu-id="034f3-124">Spécifie le nom de l’auditeur.</span><span class="sxs-lookup"><span data-stu-id="034f3-124">Specifies the name of the listener.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="034f3-125">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="034f3-125">Child Elements</span></span>  
  
|<span data-ttu-id="034f3-126">Élément</span><span class="sxs-lookup"><span data-stu-id="034f3-126">Element</span></span>|<span data-ttu-id="034f3-127">Description</span><span class="sxs-lookup"><span data-stu-id="034f3-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="034f3-128">\<filtrer></span><span class="sxs-lookup"><span data-stu-id="034f3-128">\<filter></span></span>](filter-element-for-add-for-listeners-for-trace.md)|<span data-ttu-id="034f3-129">Ajoute un filtre à un `Listeners` auditeur de la collection pour une trace.</span><span class="sxs-lookup"><span data-stu-id="034f3-129">Adds a filter to a listener in the `Listeners` collection for a trace.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="034f3-130">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="034f3-130">Parent Elements</span></span>  
  
|<span data-ttu-id="034f3-131">Élément</span><span class="sxs-lookup"><span data-stu-id="034f3-131">Element</span></span>|<span data-ttu-id="034f3-132">Description</span><span class="sxs-lookup"><span data-stu-id="034f3-132">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="034f3-133">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="034f3-133">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`listeners`|<span data-ttu-id="034f3-134">Spécifie un auditeur qui recueille, stocke et achemine les messages.</span><span class="sxs-lookup"><span data-stu-id="034f3-134">Specifies a listener that collects, stores, and routes messages.</span></span> <span data-ttu-id="034f3-135">Les auditeurs dirigent la sortie de traçage vers une cible appropriée.</span><span class="sxs-lookup"><span data-stu-id="034f3-135">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="034f3-136">Spécifie l'élément racine de la section de configuration ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="034f3-136">Specifies the root element for the ASP.NET configuration section.</span></span>|  
|`trace`|<span data-ttu-id="034f3-137">Contient les écouteurs qui collectent, stockent et acheminent les messages de traçage.</span><span class="sxs-lookup"><span data-stu-id="034f3-137">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="034f3-138">Notes </span><span class="sxs-lookup"><span data-stu-id="034f3-138">Remarks</span></span>  
 <span data-ttu-id="034f3-139">Les <xref:System.Diagnostics.Debug> <xref:System.Diagnostics.Trace> classes et les classes partagent la même collection **d’auditeurs.**</span><span class="sxs-lookup"><span data-stu-id="034f3-139">The <xref:System.Diagnostics.Debug> and <xref:System.Diagnostics.Trace> classes share the same **Listeners** collection.</span></span> <span data-ttu-id="034f3-140">Si vous ajoutez un objet d’écoute à la collection dans l’une de ces classes, l’autre classe utilise le même auditeur.</span><span class="sxs-lookup"><span data-stu-id="034f3-140">If you add a listener object to the collection in one of these classes, the other class uses the same listener.</span></span> <span data-ttu-id="034f3-141">Les classes d’auditeurs dérivent de la <xref:System.Diagnostics.TraceListener>.</span><span class="sxs-lookup"><span data-stu-id="034f3-141">The listener classes derive from the <xref:System.Diagnostics.TraceListener>.</span></span>  
  
 <span data-ttu-id="034f3-142">Si vous ne `name` spécifiez pas <xref:System.Diagnostics.TraceListener.Name%2A> l’attribut de l’auditeur de trace, l’auditeur de traces par défaut à une chaîne vide («).).</span><span class="sxs-lookup"><span data-stu-id="034f3-142">If you do not specify the `name` attribute of the trace listener, the <xref:System.Diagnostics.TraceListener.Name%2A> of the trace listener defaults to an empty string ("").</span></span> <span data-ttu-id="034f3-143">Si votre application n’a qu’un seul auditeur, vous pouvez l’ajouter sans spécifier un nom, et la supprimer en spécifiant une chaîne vide pour le nom.</span><span class="sxs-lookup"><span data-stu-id="034f3-143">If your application has only one listener, you can add it without specifying a name, and remove it by specifying an empty string for the name.</span></span> <span data-ttu-id="034f3-144">Toutefois, si votre application a plus d’un auditeur, vous devez spécifier des noms uniques <xref:System.Diagnostics.Debug.Listeners%2A> pour <xref:System.Diagnostics.Trace.Listeners%2A> chaque auditeur de traces, ce qui vous permet d’identifier et de gérer les auditeurs de traces individuels au sein de la et des collections.</span><span class="sxs-lookup"><span data-stu-id="034f3-144">However, if your application has more than one listener, you should specify unique names for each trace listener, which allows you to identify and manage individual trace listeners within the <xref:System.Diagnostics.Debug.Listeners%2A> and <xref:System.Diagnostics.Trace.Listeners%2A> collections.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="034f3-145">L’ajout de plus d’un auditeur de traces du même type et avec le même `Listeners` nom n’entraîne qu’un seul auditeur de trace de ce type et le nom ajouté à la collection.</span><span class="sxs-lookup"><span data-stu-id="034f3-145">Adding more than one trace listener of the same type and with the same name results in only one trace listener of that type and name being added to the `Listeners` collection.</span></span> <span data-ttu-id="034f3-146">Cependant, vous pouvez programmer de `Listeners` façon programmatique plusieurs auditeurs identiques à la collection.</span><span class="sxs-lookup"><span data-stu-id="034f3-146">However, you can programmatically add multiple identical listeners to the `Listeners` collection.</span></span>  
  
 <span data-ttu-id="034f3-147">La valeur de l’attribut **initializeData** dépend du type d’auditeur que vous créez.</span><span class="sxs-lookup"><span data-stu-id="034f3-147">The value for the **initializeData** attribute depends on the type of listener you create.</span></span> <span data-ttu-id="034f3-148">Pas tous les auditeurs trace exigent que vous spécifiez **initializeData**.</span><span class="sxs-lookup"><span data-stu-id="034f3-148">Not all trace listeners require that you specify **initializeData**.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="034f3-149">Lorsque vous `initializeData` utilisez l’attribut, vous pouvez obtenir l’avertissement compilateur "L’attribut 'initializeData' n’est pas déclaré."</span><span class="sxs-lookup"><span data-stu-id="034f3-149">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="034f3-150">Cet avertissement se produit parce que les paramètres <xref:System.Diagnostics.TraceListener>de configuration sont `initializeData` validés par rapport à la classe de base abstraite , qui ne reconnaît pas l’attribut.</span><span class="sxs-lookup"><span data-stu-id="034f3-150">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="034f3-151">Typiquement, vous pouvez ignorer cet avertissement pour les implémentations d’auditeur de trace qui ont un constructeur qui prend un paramètre.</span><span class="sxs-lookup"><span data-stu-id="034f3-151">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="034f3-152">Le tableau suivant montre les auditeurs trace qui sont inclus dans le cadre .NET et décrit la valeur de leurs attributs **initializeData.**</span><span class="sxs-lookup"><span data-stu-id="034f3-152">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their **initializeData** attributes.</span></span>  
  
|<span data-ttu-id="034f3-153">Cours d’auditeur de trace</span><span class="sxs-lookup"><span data-stu-id="034f3-153">Trace listener class</span></span>|<span data-ttu-id="034f3-154">initialiser la valeur d’attribut deData</span><span class="sxs-lookup"><span data-stu-id="034f3-154">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|<span data-ttu-id="034f3-155">La `useErrorStream` valeur <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> pour le constructeur.</span><span class="sxs-lookup"><span data-stu-id="034f3-155">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="034f3-156">Définissez `initializeData` l’attribut à "`true`écrire la <xref:System.Console.Error%2A?displayProperty=nameWithType>trace et la sortie de déboçon à ; "`false`écrire à <xref:System.Console.Out%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="034f3-156">Set the `initializeData` attribute to "`true`" to write trace and debug output to <xref:System.Console.Error%2A?displayProperty=nameWithType>; "`false`" to write to <xref:System.Console.Out%2A?displayProperty=nameWithType>.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|<span data-ttu-id="034f3-157">Nom du fichier vers lequel <xref:System.Diagnostics.DelimitedListTraceListener> écrit.</span><span class="sxs-lookup"><span data-stu-id="034f3-157">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="034f3-158">Le nom du nom d’une source existante de journal d’événements.</span><span class="sxs-lookup"><span data-stu-id="034f3-158">The name of the name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="034f3-159">Le nom du fichier <xref:System.Diagnostics.EventSchemaTraceListener> à qui le nom écrit.</span><span class="sxs-lookup"><span data-stu-id="034f3-159">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="034f3-160">Le nom du fichier <xref:System.Diagnostics.TextWriterTraceListener> à qui le nom écrit.</span><span class="sxs-lookup"><span data-stu-id="034f3-160">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="034f3-161">Le nom du fichier <xref:System.Diagnostics.XmlWriterTraceListener> à qui le nom écrit.</span><span class="sxs-lookup"><span data-stu-id="034f3-161">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="034f3-162"> Exemple</span><span class="sxs-lookup"><span data-stu-id="034f3-162">Example</span></span>  
 <span data-ttu-id="034f3-163">L’exemple suivant montre \*\* \<\*\* comment utiliser ajouter des `MyListener` éléments `MyEventListener`>pour ajouter les auditeurs et à la collection **Listeners.**</span><span class="sxs-lookup"><span data-stu-id="034f3-163">The following example shows how to use **\<add>** elements to add the listeners `MyListener` and `MyEventListener` to the **Listeners** collection.</span></span> <span data-ttu-id="034f3-164">`MyListener`crée un `MyListener.log` fichier appelé et écrit la sortie au fichier.</span><span class="sxs-lookup"><span data-stu-id="034f3-164">`MyListener` creates a file called `MyListener.log` and writes the output to the file.</span></span> <span data-ttu-id="034f3-165">`MyEventListener`crée une entrée dans le journal de l’événement.</span><span class="sxs-lookup"><span data-stu-id="034f3-165">`MyEventListener` creates an entry in the event log.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="034f3-166">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="034f3-166">See also</span></span>

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- [<span data-ttu-id="034f3-167">Trace et Debug Paramètres Schema</span><span class="sxs-lookup"><span data-stu-id="034f3-167">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="034f3-168">Écouteurs de suivi</span><span class="sxs-lookup"><span data-stu-id="034f3-168">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
