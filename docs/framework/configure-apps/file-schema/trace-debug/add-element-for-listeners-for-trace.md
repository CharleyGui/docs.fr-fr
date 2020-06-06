---
title: <add>, Élément de <listeners> pour<trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add
helpviewer_keywords:
- initializeData attribute
- <add> element for <listeners>
- add element for <listeners>
ms.assetid: 81e804a3-ef11-4d39-bbde-bfa012c179e2
ms.openlocfilehash: c64673908dc9afe67d97c08f93e5b9d9533bd34d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153670"
---
# <a name="add-element-for-listeners-for-trace"></a><span data-ttu-id="1d45a-102">\<add>, Élément de \<listeners> pour\<trace></span><span class="sxs-lookup"><span data-stu-id="1d45a-102">\<add> Element for \<listeners> for \<trace></span></span>
<span data-ttu-id="1d45a-103">Ajoute un écouteur à la collection d' **écouteurs** .</span><span class="sxs-lookup"><span data-stu-id="1d45a-103">Adds a listener to the **Listeners** collection.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-trace.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="1d45a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1d45a-104">Syntax</span></span>  
  
```xml  
<add name="name"
     type="trace listener class name, Version, Culture, PublicKeyToken"  
     initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1d45a-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="1d45a-105">Attributes and Elements</span></span>  
 <span data-ttu-id="1d45a-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="1d45a-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1d45a-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="1d45a-107">Attributes</span></span>  
  
|<span data-ttu-id="1d45a-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="1d45a-108">Attribute</span></span>|<span data-ttu-id="1d45a-109">Description</span><span class="sxs-lookup"><span data-stu-id="1d45a-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1d45a-110">**type**</span><span class="sxs-lookup"><span data-stu-id="1d45a-110">**type**</span></span>|<span data-ttu-id="1d45a-111">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="1d45a-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="1d45a-112">Spécifie le type de l’écouteur.</span><span class="sxs-lookup"><span data-stu-id="1d45a-112">Specifies the type of the listener.</span></span> <span data-ttu-id="1d45a-113">Vous devez utiliser une chaîne qui répond aux exigences spécifiées dans [spécification de noms de types qualifiés complets](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="1d45a-113">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|<span data-ttu-id="1d45a-114">**initializeData**</span><span class="sxs-lookup"><span data-stu-id="1d45a-114">**initializeData**</span></span>|<span data-ttu-id="1d45a-115">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="1d45a-115">Optional attribute.</span></span><br /><br /> <span data-ttu-id="1d45a-116">Chaîne passée au constructeur pour la classe spécifiée.</span><span class="sxs-lookup"><span data-stu-id="1d45a-116">The string passed to the constructor for the specified class.</span></span>|  
|<span data-ttu-id="1d45a-117">**name**</span><span class="sxs-lookup"><span data-stu-id="1d45a-117">**name**</span></span>|<span data-ttu-id="1d45a-118">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="1d45a-118">Optional attribute.</span></span><br /><br /> <span data-ttu-id="1d45a-119">Spécifie le nom de l’écouteur.</span><span class="sxs-lookup"><span data-stu-id="1d45a-119">Specifies the name of the listener.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1d45a-120">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="1d45a-120">Child Elements</span></span>  
  
|<span data-ttu-id="1d45a-121">Élément</span><span class="sxs-lookup"><span data-stu-id="1d45a-121">Element</span></span>|<span data-ttu-id="1d45a-122">Description</span><span class="sxs-lookup"><span data-stu-id="1d45a-122">Description</span></span>|  
|-------------|-----------------|  
|[\<filter>](filter-element-for-add-for-listeners-for-trace.md)|<span data-ttu-id="1d45a-123">Ajoute un filtre à un écouteur dans la `Listeners` collection pour une trace.</span><span class="sxs-lookup"><span data-stu-id="1d45a-123">Adds a filter to a listener in the `Listeners` collection for a trace.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1d45a-124">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="1d45a-124">Parent Elements</span></span>  
  
|<span data-ttu-id="1d45a-125">Élément</span><span class="sxs-lookup"><span data-stu-id="1d45a-125">Element</span></span>|<span data-ttu-id="1d45a-126">Description</span><span class="sxs-lookup"><span data-stu-id="1d45a-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="1d45a-127">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1d45a-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`listeners`|<span data-ttu-id="1d45a-128">Spécifie un écouteur qui collecte, stocke et achemine des messages.</span><span class="sxs-lookup"><span data-stu-id="1d45a-128">Specifies a listener that collects, stores, and routes messages.</span></span> <span data-ttu-id="1d45a-129">Les écouteurs dirigent la sortie de suivi vers une cible appropriée.</span><span class="sxs-lookup"><span data-stu-id="1d45a-129">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="1d45a-130">Spécifie l'élément racine de la section de configuration ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="1d45a-130">Specifies the root element for the ASP.NET configuration section.</span></span>|  
|`trace`|<span data-ttu-id="1d45a-131">Contient les écouteurs qui collectent, stockent et acheminent les messages de traçage.</span><span class="sxs-lookup"><span data-stu-id="1d45a-131">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1d45a-132">Remarques</span><span class="sxs-lookup"><span data-stu-id="1d45a-132">Remarks</span></span>  
 <span data-ttu-id="1d45a-133">Les <xref:System.Diagnostics.Debug> <xref:System.Diagnostics.Trace> classes et partagent la même collection d' **écouteurs** .</span><span class="sxs-lookup"><span data-stu-id="1d45a-133">The <xref:System.Diagnostics.Debug> and <xref:System.Diagnostics.Trace> classes share the same **Listeners** collection.</span></span> <span data-ttu-id="1d45a-134">Si vous ajoutez un objet écouteur à la collection dans l’une de ces classes, l’autre classe utilise le même écouteur.</span><span class="sxs-lookup"><span data-stu-id="1d45a-134">If you add a listener object to the collection in one of these classes, the other class uses the same listener.</span></span> <span data-ttu-id="1d45a-135">Les classes d’écouteur dérivent de <xref:System.Diagnostics.TraceListener> .</span><span class="sxs-lookup"><span data-stu-id="1d45a-135">The listener classes derive from the <xref:System.Diagnostics.TraceListener>.</span></span>  
  
 <span data-ttu-id="1d45a-136">Si vous ne spécifiez pas l' `name` attribut de l’écouteur de la trace, la <xref:System.Diagnostics.TraceListener.Name%2A> valeur par défaut de l’écouteur de la trace est une chaîne vide ("").</span><span class="sxs-lookup"><span data-stu-id="1d45a-136">If you do not specify the `name` attribute of the trace listener, the <xref:System.Diagnostics.TraceListener.Name%2A> of the trace listener defaults to an empty string ("").</span></span> <span data-ttu-id="1d45a-137">Si votre application n’a qu’un seul écouteur, vous pouvez l’ajouter sans spécifier de nom et la supprimer en spécifiant une chaîne vide pour le nom.</span><span class="sxs-lookup"><span data-stu-id="1d45a-137">If your application has only one listener, you can add it without specifying a name, and remove it by specifying an empty string for the name.</span></span> <span data-ttu-id="1d45a-138">Toutefois, si votre application a plusieurs écouteurs, vous devez spécifier des noms uniques pour chaque écouteur de suivi, ce qui vous permet d’identifier et de gérer des écouteurs de suivi individuels dans les <xref:System.Diagnostics.Debug.Listeners%2A> <xref:System.Diagnostics.Trace.Listeners%2A> collections et.</span><span class="sxs-lookup"><span data-stu-id="1d45a-138">However, if your application has more than one listener, you should specify unique names for each trace listener, which allows you to identify and manage individual trace listeners within the <xref:System.Diagnostics.Debug.Listeners%2A> and <xref:System.Diagnostics.Trace.Listeners%2A> collections.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1d45a-139">L’ajout de plusieurs écouteurs de suivi du même type et portant le même nom n’entraîne l’ajout d’un seul écouteur de suivi de ce type et d’un même nom à la `Listeners` collection.</span><span class="sxs-lookup"><span data-stu-id="1d45a-139">Adding more than one trace listener of the same type and with the same name results in only one trace listener of that type and name being added to the `Listeners` collection.</span></span> <span data-ttu-id="1d45a-140">Toutefois, vous pouvez ajouter par programmation plusieurs écouteurs identiques à la `Listeners` collection.</span><span class="sxs-lookup"><span data-stu-id="1d45a-140">However, you can programmatically add multiple identical listeners to the `Listeners` collection.</span></span>  
  
 <span data-ttu-id="1d45a-141">La valeur de l’attribut **initializeData** dépend du type d’écouteur que vous créez.</span><span class="sxs-lookup"><span data-stu-id="1d45a-141">The value for the **initializeData** attribute depends on the type of listener you create.</span></span> <span data-ttu-id="1d45a-142">Tous les écouteurs de suivi ne nécessitent pas que vous spécifiez **initializeData**.</span><span class="sxs-lookup"><span data-stu-id="1d45a-142">Not all trace listeners require that you specify **initializeData**.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1d45a-143">Lorsque vous utilisez l' `initializeData` attribut, vous pouvez recevoir l’avertissement du compilateur « l’attribut’initializeData’n’est pas déclaré. »</span><span class="sxs-lookup"><span data-stu-id="1d45a-143">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="1d45a-144">Cet avertissement se produit parce que les paramètres de configuration sont validés par rapport à la classe de base abstraite <xref:System.Diagnostics.TraceListener> , qui ne reconnaît pas l' `initializeData` attribut.</span><span class="sxs-lookup"><span data-stu-id="1d45a-144">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="1d45a-145">En règle générale, vous pouvez ignorer cet avertissement pour les implémentations d’écouteurs de trace qui ont un constructeur qui prend un paramètre.</span><span class="sxs-lookup"><span data-stu-id="1d45a-145">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="1d45a-146">Le tableau suivant répertorie les écouteurs de suivi inclus avec le .NET Framework et décrit la valeur de leurs attributs **initializeData** .</span><span class="sxs-lookup"><span data-stu-id="1d45a-146">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their **initializeData** attributes.</span></span>  
  
|<span data-ttu-id="1d45a-147">Classe d’écouteur de suivi</span><span class="sxs-lookup"><span data-stu-id="1d45a-147">Trace listener class</span></span>|<span data-ttu-id="1d45a-148">valeur de l’attribut initializeData</span><span class="sxs-lookup"><span data-stu-id="1d45a-148">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|<span data-ttu-id="1d45a-149">`useErrorStream`Valeur du <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructeur.</span><span class="sxs-lookup"><span data-stu-id="1d45a-149">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="1d45a-150">Affectez à l’attribut la valeur `initializeData` " `true` " pour écrire la sortie de trace et de débogage dans <xref:System.Console.Error%2A?displayProperty=nameWithType> ; « `false` » dans lequel écrire <xref:System.Console.Out%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="1d45a-150">Set the `initializeData` attribute to "`true`" to write trace and debug output to <xref:System.Console.Error%2A?displayProperty=nameWithType>; "`false`" to write to <xref:System.Console.Out%2A?displayProperty=nameWithType>.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|<span data-ttu-id="1d45a-151">Nom du fichier vers lequel <xref:System.Diagnostics.DelimitedListTraceListener> écrit.</span><span class="sxs-lookup"><span data-stu-id="1d45a-151">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="1d45a-152">Nom du nom d’une source de journal des événements existante.</span><span class="sxs-lookup"><span data-stu-id="1d45a-152">The name of the name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="1d45a-153">Nom du fichier <xref:System.Diagnostics.EventSchemaTraceListener> dans lequel écrit.</span><span class="sxs-lookup"><span data-stu-id="1d45a-153">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="1d45a-154">Nom du fichier <xref:System.Diagnostics.TextWriterTraceListener> dans lequel écrit.</span><span class="sxs-lookup"><span data-stu-id="1d45a-154">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="1d45a-155">Nom du fichier <xref:System.Diagnostics.XmlWriterTraceListener> dans lequel écrit.</span><span class="sxs-lookup"><span data-stu-id="1d45a-155">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="1d45a-156">Exemple</span><span class="sxs-lookup"><span data-stu-id="1d45a-156">Example</span></span>  
 <span data-ttu-id="1d45a-157">L’exemple suivant montre comment utiliser des **\<add>** éléments pour ajouter les écouteurs `MyListener` et `MyEventListener` la collection d' **écouteurs** .</span><span class="sxs-lookup"><span data-stu-id="1d45a-157">The following example shows how to use **\<add>** elements to add the listeners `MyListener` and `MyEventListener` to the **Listeners** collection.</span></span> <span data-ttu-id="1d45a-158">`MyListener`crée un fichier appelé `MyListener.log` et écrit la sortie dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="1d45a-158">`MyListener` creates a file called `MyListener.log` and writes the output to the file.</span></span> <span data-ttu-id="1d45a-159">`MyEventListener`crée une entrée dans le journal des événements.</span><span class="sxs-lookup"><span data-stu-id="1d45a-159">`MyEventListener` creates an entry in the event log.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1d45a-160">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1d45a-160">See also</span></span>

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- [<span data-ttu-id="1d45a-161">Schéma des paramètres de traçage et de débogage</span><span class="sxs-lookup"><span data-stu-id="1d45a-161">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="1d45a-162">Écouteurs de suivi</span><span class="sxs-lookup"><span data-stu-id="1d45a-162">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
