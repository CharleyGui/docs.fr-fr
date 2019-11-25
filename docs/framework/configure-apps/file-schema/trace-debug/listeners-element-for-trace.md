---
title: Élément <listeners> pour <trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners
helpviewer_keywords:
- <listeners> element
- listeners element
ms.assetid: 1394c2c3-6304-46db-87c1-8e8b16f5ad5b
ms.openlocfilehash: 10530cfadf2e182f912c699e50294af4b57f47b5
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088865"
---
# <a name="listeners-element-for-trace"></a><span data-ttu-id="4860a-102">\<écouteurs > élément pour \<trace ></span><span class="sxs-lookup"><span data-stu-id="4860a-102">\<listeners> Element for \<trace></span></span>
<span data-ttu-id="4860a-103">Spécifie un écouteur qui collecte, stocke et achemine des messages.</span><span class="sxs-lookup"><span data-stu-id="4860a-103">Specifies a listener that collects, stores, and routes messages.</span></span> <span data-ttu-id="4860a-104">Les écouteurs dirigent la sortie de suivi vers une cible appropriée.</span><span class="sxs-lookup"><span data-stu-id="4860a-104">Listeners direct the tracing output to an appropriate target.</span></span>  

<span data-ttu-id="4860a-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="4860a-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="4860a-106">&nbsp;&nbsp;[ **\<System. diagnostics >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="4860a-106">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="4860a-107">&nbsp;&nbsp;&nbsp;&nbsp;\<de [**trace**](trace-element.md) ></span><span class="sxs-lookup"><span data-stu-id="4860a-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)\</span></span>
<span data-ttu-id="4860a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**écouteurs**\<</span><span class="sxs-lookup"><span data-stu-id="4860a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<listeners>**</span></span>

## <a name="syntax"></a><span data-ttu-id="4860a-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4860a-109">Syntax</span></span>  
  
```xml  
<listeners>   
  <add>...</add>  
  <clear/>  
  <remove ... />  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4860a-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="4860a-110">Attributes and Elements</span></span>  
 <span data-ttu-id="4860a-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="4860a-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4860a-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="4860a-112">Attributes</span></span>  
 <span data-ttu-id="4860a-113">Aucun(e).</span><span class="sxs-lookup"><span data-stu-id="4860a-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4860a-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="4860a-114">Child Elements</span></span>  
  
|<span data-ttu-id="4860a-115">Élément</span><span class="sxs-lookup"><span data-stu-id="4860a-115">Element</span></span>|<span data-ttu-id="4860a-116">Description</span><span class="sxs-lookup"><span data-stu-id="4860a-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4860a-117">\<add></span><span class="sxs-lookup"><span data-stu-id="4860a-117">\<add></span></span>](add-element-for-listeners-for-trace.md)|<span data-ttu-id="4860a-118">Ajoute un écouteur à la collection `Listeners`.</span><span class="sxs-lookup"><span data-stu-id="4860a-118">Adds a listener to the `Listeners` collection.</span></span>|  
|[<span data-ttu-id="4860a-119">\<clear></span><span class="sxs-lookup"><span data-stu-id="4860a-119">\<clear></span></span>](clear-element-for-listeners-for-trace.md)|<span data-ttu-id="4860a-120">Efface la collection `Listeners` de la trace.</span><span class="sxs-lookup"><span data-stu-id="4860a-120">Clears the `Listeners` collection for trace.</span></span>|  
|[<span data-ttu-id="4860a-121">\<remove></span><span class="sxs-lookup"><span data-stu-id="4860a-121">\<remove></span></span>](remove-element-for-listeners-for-trace.md)|<span data-ttu-id="4860a-122">Supprime un écouteur de la collection `Listeners`.</span><span class="sxs-lookup"><span data-stu-id="4860a-122">Removes a listener from the `Listeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4860a-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="4860a-123">Parent Elements</span></span>  
  
|<span data-ttu-id="4860a-124">Élément</span><span class="sxs-lookup"><span data-stu-id="4860a-124">Element</span></span>|<span data-ttu-id="4860a-125">Description</span><span class="sxs-lookup"><span data-stu-id="4860a-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="4860a-126">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4860a-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="4860a-127">Spécifie l'élément racine de la section de configuration ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="4860a-127">Specifies the root element for the ASP.NET configuration section.</span></span>|  
|`trace`|<span data-ttu-id="4860a-128">Contient les écouteurs qui collectent, stockent et acheminent les messages de traçage.</span><span class="sxs-lookup"><span data-stu-id="4860a-128">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4860a-129">Notes</span><span class="sxs-lookup"><span data-stu-id="4860a-129">Remarks</span></span>  
 <span data-ttu-id="4860a-130">Les classes <xref:System.Diagnostics.Debug> et <xref:System.Diagnostics.Trace> partagent la même collection d' **écouteurs** .</span><span class="sxs-lookup"><span data-stu-id="4860a-130">The <xref:System.Diagnostics.Debug> and <xref:System.Diagnostics.Trace> classes share the same **Listeners** collection.</span></span> <span data-ttu-id="4860a-131">Si vous ajoutez un objet écouteur à la collection dans l’une de ces classes, l’autre classe utilise le même écouteur.</span><span class="sxs-lookup"><span data-stu-id="4860a-131">If you add a listener object to the collection in one of these classes, the other class uses the same listener.</span></span> <span data-ttu-id="4860a-132">Les classes d’écouteur fournies avec le .NET Framework dérivent de la classe <xref:System.Diagnostics.TraceListener>.</span><span class="sxs-lookup"><span data-stu-id="4860a-132">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="4860a-133">Fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="4860a-133">Configuration File</span></span>  
 <span data-ttu-id="4860a-134">Cet élément peut être utilisé dans le fichier de configuration de l’ordinateur (machine. config) et dans le fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="4860a-134">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4860a-135">Exemple</span><span class="sxs-lookup"><span data-stu-id="4860a-135">Example</span></span>  
 <span data-ttu-id="4860a-136">L’exemple suivant montre comment utiliser l’élément **\<écouteurs >** pour ajouter les écouteurs `MyListener` et `MyEventListener` à la collection d' **écouteurs** .</span><span class="sxs-lookup"><span data-stu-id="4860a-136">The following example shows how to use the **\<listeners>** element to add the listeners `MyListener` and `MyEventListener` to the **Listeners** collection.</span></span> <span data-ttu-id="4860a-137">`MyListener` crée un fichier nommé `MyListener.log` et écrit la sortie dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="4860a-137">`MyListener` creates a file called `MyListener.log` and writes the output to the file.</span></span> <span data-ttu-id="4860a-138">`MyEventListener` crée une entrée dans le journal des événements.</span><span class="sxs-lookup"><span data-stu-id="4860a-138">`MyEventListener` creates an entry in the event log.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4860a-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4860a-139">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="4860a-140">Schéma des paramètres de trace et de débogage</span><span class="sxs-lookup"><span data-stu-id="4860a-140">Trace and Debug Settings Schema</span></span>](index.md)
