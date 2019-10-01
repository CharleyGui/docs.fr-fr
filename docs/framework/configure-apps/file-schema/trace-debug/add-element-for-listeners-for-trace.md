---
title: Élément <add> pour <listeners> pour <trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add
helpviewer_keywords:
- initializeData attribute
- <add> element for <listeners>
- add element for <listeners>
ms.assetid: 81e804a3-ef11-4d39-bbde-bfa012c179e2
ms.openlocfilehash: d89a77107e7aff65b007a69c23af34771146570c
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697336"
---
# <a name="add-element-for-listeners-for-trace"></a><span data-ttu-id="489a6-102">\<add > élément de \<listeners > pour \<trace ></span><span class="sxs-lookup"><span data-stu-id="489a6-102">\<add> Element for \<listeners> for \<trace></span></span>
<span data-ttu-id="489a6-103">Ajoute un écouteur à la collection d' **écouteurs** .</span><span class="sxs-lookup"><span data-stu-id="489a6-103">Adds a listener to the **Listeners** collection.</span></span>  
  
[<span data-ttu-id="489a6-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="489a6-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="489a6-105">&nbsp; @ no__t-1[ **\<System. diagnostics >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="489a6-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>  
<span data-ttu-id="489a6-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<trace >** ](trace-element.md)</span><span class="sxs-lookup"><span data-stu-id="489a6-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)</span></span>  
<span data-ttu-id="489a6-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5[ **\<listeners >** ](listeners-element-for-trace.md)</span><span class="sxs-lookup"><span data-stu-id="489a6-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-trace.md)</span></span>  
<span data-ttu-id="489a6-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Ajouter >**</span><span class="sxs-lookup"><span data-stu-id="489a6-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="489a6-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="489a6-109">Syntax</span></span>  
  
```xml  
<add name="name"   
     type="trace listener class name, Version, Culture, PublicKeyToken"  
     initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="489a6-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="489a6-110">Attributes and Elements</span></span>  
 <span data-ttu-id="489a6-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="489a6-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="489a6-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="489a6-112">Attributes</span></span>  
  
|<span data-ttu-id="489a6-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="489a6-113">Attribute</span></span>|<span data-ttu-id="489a6-114">Description</span><span class="sxs-lookup"><span data-stu-id="489a6-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="489a6-115">**type**</span><span class="sxs-lookup"><span data-stu-id="489a6-115">**type**</span></span>|<span data-ttu-id="489a6-116">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="489a6-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="489a6-117">Spécifie le type de l’écouteur.</span><span class="sxs-lookup"><span data-stu-id="489a6-117">Specifies the type of the listener.</span></span> <span data-ttu-id="489a6-118">Vous devez utiliser une chaîne qui répond aux exigences spécifiées dans [spécification de noms de types qualifiés complets](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="489a6-118">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|<span data-ttu-id="489a6-119">**initializeData**</span><span class="sxs-lookup"><span data-stu-id="489a6-119">**initializeData**</span></span>|<span data-ttu-id="489a6-120">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="489a6-120">Optional attribute.</span></span><br /><br /> <span data-ttu-id="489a6-121">Chaîne passée au constructeur pour la classe spécifiée.</span><span class="sxs-lookup"><span data-stu-id="489a6-121">The string passed to the constructor for the specified class.</span></span>|  
|<span data-ttu-id="489a6-122">**name**</span><span class="sxs-lookup"><span data-stu-id="489a6-122">**name**</span></span>|<span data-ttu-id="489a6-123">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="489a6-123">Optional attribute.</span></span><br /><br /> <span data-ttu-id="489a6-124">Spécifie le nom de l’écouteur.</span><span class="sxs-lookup"><span data-stu-id="489a6-124">Specifies the name of the listener.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="489a6-125">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="489a6-125">Child Elements</span></span>  
  
|<span data-ttu-id="489a6-126">Élément</span><span class="sxs-lookup"><span data-stu-id="489a6-126">Element</span></span>|<span data-ttu-id="489a6-127">Description</span><span class="sxs-lookup"><span data-stu-id="489a6-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="489a6-128">\<filter></span><span class="sxs-lookup"><span data-stu-id="489a6-128">\<filter></span></span>](filter-element-for-add-for-listeners-for-trace.md)|<span data-ttu-id="489a6-129">Ajoute un filtre à un écouteur dans la collection `Listeners` pour une trace.</span><span class="sxs-lookup"><span data-stu-id="489a6-129">Adds a filter to a listener in the `Listeners` collection for a trace.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="489a6-130">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="489a6-130">Parent Elements</span></span>  
  
|<span data-ttu-id="489a6-131">Élément</span><span class="sxs-lookup"><span data-stu-id="489a6-131">Element</span></span>|<span data-ttu-id="489a6-132">Description</span><span class="sxs-lookup"><span data-stu-id="489a6-132">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="489a6-133">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="489a6-133">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`listeners`|<span data-ttu-id="489a6-134">Spécifie un écouteur qui collecte, stocke et achemine des messages.</span><span class="sxs-lookup"><span data-stu-id="489a6-134">Specifies a listener that collects, stores, and routes messages.</span></span> <span data-ttu-id="489a6-135">Les écouteurs dirigent la sortie de suivi vers une cible appropriée.</span><span class="sxs-lookup"><span data-stu-id="489a6-135">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="489a6-136">Spécifie l'élément racine de la section de configuration ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="489a6-136">Specifies the root element for the ASP.NET configuration section.</span></span>|  
|`trace`|<span data-ttu-id="489a6-137">Contient les écouteurs qui collectent, stockent et acheminent les messages de traçage.</span><span class="sxs-lookup"><span data-stu-id="489a6-137">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="489a6-138">Notes</span><span class="sxs-lookup"><span data-stu-id="489a6-138">Remarks</span></span>  
 <span data-ttu-id="489a6-139">Les classes <xref:System.Diagnostics.Debug> et <xref:System.Diagnostics.Trace> partagent la même collection d' **écouteurs** .</span><span class="sxs-lookup"><span data-stu-id="489a6-139">The <xref:System.Diagnostics.Debug> and <xref:System.Diagnostics.Trace> classes share the same **Listeners** collection.</span></span> <span data-ttu-id="489a6-140">Si vous ajoutez un objet écouteur à la collection dans l’une de ces classes, l’autre classe utilise le même écouteur.</span><span class="sxs-lookup"><span data-stu-id="489a6-140">If you add a listener object to the collection in one of these classes, the other class uses the same listener.</span></span> <span data-ttu-id="489a6-141">Les classes d’écouteur dérivent de la <xref:System.Diagnostics.TraceListener>.</span><span class="sxs-lookup"><span data-stu-id="489a6-141">The listener classes derive from the <xref:System.Diagnostics.TraceListener>.</span></span>  
  
 <span data-ttu-id="489a6-142">Si vous ne spécifiez pas l’attribut `name` de l’écouteur de la trace, la <xref:System.Diagnostics.TraceListener.Name%2A> de l’écouteur de la trace est une chaîne vide ("") par défaut.</span><span class="sxs-lookup"><span data-stu-id="489a6-142">If you do not specify the `name` attribute of the trace listener, the <xref:System.Diagnostics.TraceListener.Name%2A> of the trace listener defaults to an empty string ("").</span></span> <span data-ttu-id="489a6-143">Si votre application n’a qu’un seul écouteur, vous pouvez l’ajouter sans spécifier de nom et la supprimer en spécifiant une chaîne vide pour le nom.</span><span class="sxs-lookup"><span data-stu-id="489a6-143">If your application has only one listener, you can add it without specifying a name, and remove it by specifying an empty string for the name.</span></span> <span data-ttu-id="489a6-144">Toutefois, si votre application a plusieurs écouteurs, vous devez spécifier des noms uniques pour chaque écouteur de suivi, ce qui vous permet d’identifier et de gérer des écouteurs de suivi individuels dans les collections <xref:System.Diagnostics.Debug.Listeners%2A> et <xref:System.Diagnostics.Trace.Listeners%2A>.</span><span class="sxs-lookup"><span data-stu-id="489a6-144">However, if your application has more than one listener, you should specify unique names for each trace listener, which allows you to identify and manage individual trace listeners within the <xref:System.Diagnostics.Debug.Listeners%2A> and <xref:System.Diagnostics.Trace.Listeners%2A> collections.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="489a6-145">L’ajout de plusieurs écouteurs de suivi du même type et portant le même nom entraîne l’ajout d’un seul écouteur de suivi de ce type et d’un nom à la collection `Listeners`.</span><span class="sxs-lookup"><span data-stu-id="489a6-145">Adding more than one trace listener of the same type and with the same name results in only one trace listener of that type and name being added to the `Listeners` collection.</span></span> <span data-ttu-id="489a6-146">Toutefois, vous pouvez ajouter par programmation plusieurs écouteurs identiques à la collection `Listeners`.</span><span class="sxs-lookup"><span data-stu-id="489a6-146">However, you can programmatically add multiple identical listeners to the `Listeners` collection.</span></span>  
  
 <span data-ttu-id="489a6-147">La valeur de l’attribut **initializeData** dépend du type d’écouteur que vous créez.</span><span class="sxs-lookup"><span data-stu-id="489a6-147">The value for the **initializeData** attribute depends on the type of listener you create.</span></span> <span data-ttu-id="489a6-148">Tous les écouteurs de suivi ne nécessitent pas que vous spécifiez **initializeData**.</span><span class="sxs-lookup"><span data-stu-id="489a6-148">Not all trace listeners require that you specify **initializeData**.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="489a6-149">Lorsque vous utilisez l’attribut `initializeData`, vous pouvez recevoir l’avertissement du compilateur « l’attribut’initializeData’n’est pas déclaré. »</span><span class="sxs-lookup"><span data-stu-id="489a6-149">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="489a6-150">Cet avertissement se produit parce que les paramètres de configuration sont validés par rapport à la classe de base abstraite <xref:System.Diagnostics.TraceListener>, qui ne reconnaît pas l’attribut `initializeData`.</span><span class="sxs-lookup"><span data-stu-id="489a6-150">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="489a6-151">En règle générale, vous pouvez ignorer cet avertissement pour les implémentations d’écouteurs de trace qui ont un constructeur qui prend un paramètre.</span><span class="sxs-lookup"><span data-stu-id="489a6-151">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="489a6-152">Le tableau suivant répertorie les écouteurs de suivi inclus avec le .NET Framework et décrit la valeur de leurs attributs **initializeData** .</span><span class="sxs-lookup"><span data-stu-id="489a6-152">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their **initializeData** attributes.</span></span>  
  
|<span data-ttu-id="489a6-153">Classe d’écouteur de suivi</span><span class="sxs-lookup"><span data-stu-id="489a6-153">Trace listener class</span></span>|<span data-ttu-id="489a6-154">valeur de l’attribut initializeData</span><span class="sxs-lookup"><span data-stu-id="489a6-154">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|<span data-ttu-id="489a6-155">La valeur `useErrorStream` pour le constructeur <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A>.</span><span class="sxs-lookup"><span data-stu-id="489a6-155">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="489a6-156">Affectez à l’attribut `initializeData` la valeur « `true` » pour écrire la sortie de trace et de débogage sur <xref:System.Console.Error%2A?displayProperty=nameWithType>. « `false` » pour écrire dans <xref:System.Console.Out%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="489a6-156">Set the `initializeData` attribute to "`true`" to write trace and debug output to <xref:System.Console.Error%2A?displayProperty=nameWithType>; "`false`" to write to <xref:System.Console.Out%2A?displayProperty=nameWithType>.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|<span data-ttu-id="489a6-157">Nom du fichier dans lequel le <xref:System.Diagnostics.DelimitedListTraceListener> écrit.</span><span class="sxs-lookup"><span data-stu-id="489a6-157">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="489a6-158">Nom du nom d’une source de journal des événements existante.</span><span class="sxs-lookup"><span data-stu-id="489a6-158">The name of the name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="489a6-159">Nom du fichier dans lequel le <xref:System.Diagnostics.EventSchemaTraceListener> écrit.</span><span class="sxs-lookup"><span data-stu-id="489a6-159">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="489a6-160">Nom du fichier dans lequel le <xref:System.Diagnostics.TextWriterTraceListener> écrit.</span><span class="sxs-lookup"><span data-stu-id="489a6-160">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="489a6-161">Nom du fichier dans lequel le <xref:System.Diagnostics.XmlWriterTraceListener> écrit.</span><span class="sxs-lookup"><span data-stu-id="489a6-161">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="489a6-162">Exemple</span><span class="sxs-lookup"><span data-stu-id="489a6-162">Example</span></span>  
 <span data-ttu-id="489a6-163">L’exemple suivant montre comment utiliser les éléments de **> \<Add** pour ajouter les écouteurs `MyListener` et `MyEventListener` à la collection d' **écouteurs** .</span><span class="sxs-lookup"><span data-stu-id="489a6-163">The following example shows how to use **\<add>** elements to add the listeners `MyListener` and `MyEventListener` to the **Listeners** collection.</span></span> <span data-ttu-id="489a6-164">`MyListener` crée un fichier nommé `MyListener.log` et écrit la sortie dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="489a6-164">`MyListener` creates a file called `MyListener.log` and writes the output to the file.</span></span> <span data-ttu-id="489a6-165">`MyEventListener` crée une entrée dans le journal des événements.</span><span class="sxs-lookup"><span data-stu-id="489a6-165">`MyEventListener` creates an entry in the event log.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="489a6-166">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="489a6-166">See also</span></span>

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- [<span data-ttu-id="489a6-167">Schéma des paramètres de trace et de débogage</span><span class="sxs-lookup"><span data-stu-id="489a6-167">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="489a6-168">Écouteurs de suivi</span><span class="sxs-lookup"><span data-stu-id="489a6-168">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
