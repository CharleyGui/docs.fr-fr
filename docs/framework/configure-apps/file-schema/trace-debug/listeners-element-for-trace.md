---
title: Élément <listeners> pour <trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners
helpviewer_keywords:
- <listeners> element
- listeners element
ms.assetid: 1394c2c3-6304-46db-87c1-8e8b16f5ad5b
ms.openlocfilehash: 84b67532825372e7f69d86e1ef6060f4263587eb
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699354"
---
# <a name="listeners-element-for-trace"></a><span data-ttu-id="7adc2-102">\<listeners > élément de \<trace ></span><span class="sxs-lookup"><span data-stu-id="7adc2-102">\<listeners> Element for \<trace></span></span>
<span data-ttu-id="7adc2-103">Spécifie un écouteur qui collecte, stocke et achemine des messages.</span><span class="sxs-lookup"><span data-stu-id="7adc2-103">Specifies a listener that collects, stores, and routes messages.</span></span> <span data-ttu-id="7adc2-104">Les écouteurs dirigent la sortie de suivi vers une cible appropriée.</span><span class="sxs-lookup"><span data-stu-id="7adc2-104">Listeners direct the tracing output to an appropriate target.</span></span>  
  
[<span data-ttu-id="7adc2-105"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="7adc2-105">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="7adc2-106">&nbsp; @ no__t-1[ **\<System. diagnostics >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="7adc2-106">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>  
<span data-ttu-id="7adc2-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<trace >** ](trace-element.md)</span><span class="sxs-lookup"><span data-stu-id="7adc2-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)</span></span>  
<span data-ttu-id="7adc2-108">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<listeners >**</span><span class="sxs-lookup"><span data-stu-id="7adc2-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<listeners>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7adc2-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7adc2-109">Syntax</span></span>  
  
```xml  
<listeners>   
  <add>...</add>  
  <clear/>  
  <remove ... />  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7adc2-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="7adc2-110">Attributes and Elements</span></span>  
 <span data-ttu-id="7adc2-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="7adc2-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7adc2-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="7adc2-112">Attributes</span></span>  
 <span data-ttu-id="7adc2-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="7adc2-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7adc2-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="7adc2-114">Child Elements</span></span>  
  
|<span data-ttu-id="7adc2-115">Élément</span><span class="sxs-lookup"><span data-stu-id="7adc2-115">Element</span></span>|<span data-ttu-id="7adc2-116">Description</span><span class="sxs-lookup"><span data-stu-id="7adc2-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7adc2-117">\<add></span><span class="sxs-lookup"><span data-stu-id="7adc2-117">\<add></span></span>](add-element-for-listeners-for-trace.md)|<span data-ttu-id="7adc2-118">Ajoute un écouteur à la collection `Listeners`.</span><span class="sxs-lookup"><span data-stu-id="7adc2-118">Adds a listener to the `Listeners` collection.</span></span>|  
|[<span data-ttu-id="7adc2-119">\<clear></span><span class="sxs-lookup"><span data-stu-id="7adc2-119">\<clear></span></span>](clear-element-for-listeners-for-trace.md)|<span data-ttu-id="7adc2-120">Efface la collection `Listeners` de la trace.</span><span class="sxs-lookup"><span data-stu-id="7adc2-120">Clears the `Listeners` collection for trace.</span></span>|  
|[<span data-ttu-id="7adc2-121">\<remove></span><span class="sxs-lookup"><span data-stu-id="7adc2-121">\<remove></span></span>](remove-element-for-listeners-for-trace.md)|<span data-ttu-id="7adc2-122">Supprime un écouteur de la collection `Listeners`.</span><span class="sxs-lookup"><span data-stu-id="7adc2-122">Removes a listener from the `Listeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7adc2-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="7adc2-123">Parent Elements</span></span>  
  
|<span data-ttu-id="7adc2-124">Élément</span><span class="sxs-lookup"><span data-stu-id="7adc2-124">Element</span></span>|<span data-ttu-id="7adc2-125">Description</span><span class="sxs-lookup"><span data-stu-id="7adc2-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="7adc2-126">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7adc2-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="7adc2-127">Spécifie l'élément racine de la section de configuration ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="7adc2-127">Specifies the root element for the ASP.NET configuration section.</span></span>|  
|`trace`|<span data-ttu-id="7adc2-128">Contient les écouteurs qui collectent, stockent et acheminent les messages de traçage.</span><span class="sxs-lookup"><span data-stu-id="7adc2-128">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7adc2-129">Notes</span><span class="sxs-lookup"><span data-stu-id="7adc2-129">Remarks</span></span>  
 <span data-ttu-id="7adc2-130">Les classes <xref:System.Diagnostics.Debug> et <xref:System.Diagnostics.Trace> partagent la même collection d' **écouteurs** .</span><span class="sxs-lookup"><span data-stu-id="7adc2-130">The <xref:System.Diagnostics.Debug> and <xref:System.Diagnostics.Trace> classes share the same **Listeners** collection.</span></span> <span data-ttu-id="7adc2-131">Si vous ajoutez un objet écouteur à la collection dans l’une de ces classes, l’autre classe utilise le même écouteur.</span><span class="sxs-lookup"><span data-stu-id="7adc2-131">If you add a listener object to the collection in one of these classes, the other class uses the same listener.</span></span> <span data-ttu-id="7adc2-132">Les classes d’écouteur fournies avec le .NET Framework dérivent de la classe <xref:System.Diagnostics.TraceListener>.</span><span class="sxs-lookup"><span data-stu-id="7adc2-132">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="7adc2-133">Fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="7adc2-133">Configuration File</span></span>  
 <span data-ttu-id="7adc2-134">Cet élément peut être utilisé dans le fichier de configuration de l’ordinateur (machine. config) et dans le fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="7adc2-134">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7adc2-135">Exemple</span><span class="sxs-lookup"><span data-stu-id="7adc2-135">Example</span></span>  
 <span data-ttu-id="7adc2-136">L’exemple suivant montre comment utiliser l’élément **\<listeners >** pour ajouter les écouteurs `MyListener` et `MyEventListener` à la collection d' **écouteurs** .</span><span class="sxs-lookup"><span data-stu-id="7adc2-136">The following example shows how to use the **\<listeners>** element to add the listeners `MyListener` and `MyEventListener` to the **Listeners** collection.</span></span> <span data-ttu-id="7adc2-137">`MyListener` crée un fichier nommé `MyListener.log` et écrit la sortie dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="7adc2-137">`MyListener` creates a file called `MyListener.log` and writes the output to the file.</span></span> <span data-ttu-id="7adc2-138">`MyEventListener` crée une entrée dans le journal des événements.</span><span class="sxs-lookup"><span data-stu-id="7adc2-138">`MyEventListener` creates an entry in the event log.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <trace autoflush="true" indentsize="0">  
      <listeners>  
        <add name="myListener"   
          type="System.Diagnostics.TextWriterTraceListener,   
            system, version=1.0.3300.0, Culture=neutral,   
            PublicKeyToken=b77a5c561934e089"   
          initializeData="c:\myListener.log" />  
        <add name="MyEventListener"  
          type="System.Diagnostics.EventLogTraceListener,   
            system, version=1.0.3300.0, Culture=neutral,   
            PublicKeyToken=b77a5c561934e089"  
          initializeData="MyConfigEventLog"/>  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7adc2-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7adc2-139">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="7adc2-140">Schéma des paramètres de trace et de débogage</span><span class="sxs-lookup"><span data-stu-id="7adc2-140">Trace and Debug Settings Schema</span></span>](index.md)
