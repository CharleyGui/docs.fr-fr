---
title: Élément <listeners> pour <trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners
helpviewer_keywords:
- <listeners> element
- listeners element
ms.assetid: 1394c2c3-6304-46db-87c1-8e8b16f5ad5b
ms.openlocfilehash: fd12be1b775d7611ef3f16d23147470313bf9866
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153371"
---
# <a name="listeners-element-for-trace"></a><span data-ttu-id="75042-102">\<auditeurs> Element \<pour trace></span><span class="sxs-lookup"><span data-stu-id="75042-102">\<listeners> Element for \<trace></span></span>
<span data-ttu-id="75042-103">Spécifie un auditeur qui recueille, stocke et achemine les messages.</span><span class="sxs-lookup"><span data-stu-id="75042-103">Specifies a listener that collects, stores, and routes messages.</span></span> <span data-ttu-id="75042-104">Les auditeurs dirigent la sortie de traçage vers une cible appropriée.</span><span class="sxs-lookup"><span data-stu-id="75042-104">Listeners direct the tracing output to an appropriate target.</span></span>  

<span data-ttu-id="75042-105">[**\<configuration>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="75042-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="75042-106">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="75042-106">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="75042-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)</span><span class="sxs-lookup"><span data-stu-id="75042-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)</span></span>\
<span data-ttu-id="75042-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<auditeurs>**</span><span class="sxs-lookup"><span data-stu-id="75042-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<listeners>**</span></span>

## <a name="syntax"></a><span data-ttu-id="75042-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="75042-109">Syntax</span></span>  
  
```xml  
<listeners>
  <add>...</add>  
  <clear/>  
  <remove ... />  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="75042-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="75042-110">Attributes and Elements</span></span>  
 <span data-ttu-id="75042-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="75042-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="75042-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="75042-112">Attributes</span></span>  
 <span data-ttu-id="75042-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="75042-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="75042-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="75042-114">Child Elements</span></span>  
  
|<span data-ttu-id="75042-115">Élément</span><span class="sxs-lookup"><span data-stu-id="75042-115">Element</span></span>|<span data-ttu-id="75042-116">Description</span><span class="sxs-lookup"><span data-stu-id="75042-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="75042-117">\<ajouter></span><span class="sxs-lookup"><span data-stu-id="75042-117">\<add></span></span>](add-element-for-listeners-for-trace.md)|<span data-ttu-id="75042-118">Ajoute un écouteur à la collection `Listeners`.</span><span class="sxs-lookup"><span data-stu-id="75042-118">Adds a listener to the `Listeners` collection.</span></span>|  
|[<span data-ttu-id="75042-119">\<clair></span><span class="sxs-lookup"><span data-stu-id="75042-119">\<clear></span></span>](clear-element-for-listeners-for-trace.md)|<span data-ttu-id="75042-120">Efface la collection `Listeners` de la trace.</span><span class="sxs-lookup"><span data-stu-id="75042-120">Clears the `Listeners` collection for trace.</span></span>|  
|[<span data-ttu-id="75042-121">\<supprimer></span><span class="sxs-lookup"><span data-stu-id="75042-121">\<remove></span></span>](remove-element-for-listeners-for-trace.md)|<span data-ttu-id="75042-122">Retire un auditeur de `Listeners` la collection.</span><span class="sxs-lookup"><span data-stu-id="75042-122">Removes a listener from the `Listeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="75042-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="75042-123">Parent Elements</span></span>  
  
|<span data-ttu-id="75042-124">Élément</span><span class="sxs-lookup"><span data-stu-id="75042-124">Element</span></span>|<span data-ttu-id="75042-125">Description</span><span class="sxs-lookup"><span data-stu-id="75042-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="75042-126">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="75042-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="75042-127">Spécifie l'élément racine de la section de configuration ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="75042-127">Specifies the root element for the ASP.NET configuration section.</span></span>|  
|`trace`|<span data-ttu-id="75042-128">Contient les écouteurs qui collectent, stockent et acheminent les messages de traçage.</span><span class="sxs-lookup"><span data-stu-id="75042-128">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="75042-129">Notes </span><span class="sxs-lookup"><span data-stu-id="75042-129">Remarks</span></span>  
 <span data-ttu-id="75042-130">Les <xref:System.Diagnostics.Debug> <xref:System.Diagnostics.Trace> classes et les classes partagent la même collection **d’auditeurs.**</span><span class="sxs-lookup"><span data-stu-id="75042-130">The <xref:System.Diagnostics.Debug> and <xref:System.Diagnostics.Trace> classes share the same **Listeners** collection.</span></span> <span data-ttu-id="75042-131">Si vous ajoutez un objet d’écoute à la collection dans l’une de ces classes, l’autre classe utilise le même auditeur.</span><span class="sxs-lookup"><span data-stu-id="75042-131">If you add a listener object to the collection in one of these classes, the other class uses the same listener.</span></span> <span data-ttu-id="75042-132">Les classes d’auditeur expédiées avec <xref:System.Diagnostics.TraceListener> le cadre .NET dérivent de la classe.</span><span class="sxs-lookup"><span data-stu-id="75042-132">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="75042-133">Fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="75042-133">Configuration File</span></span>  
 <span data-ttu-id="75042-134">Cet élément peut être utilisé dans le fichier de configuration de la machine (Machine.config) et le fichier de configuration d’application.</span><span class="sxs-lookup"><span data-stu-id="75042-134">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="75042-135"> Exemple</span><span class="sxs-lookup"><span data-stu-id="75042-135">Example</span></span>  
 <span data-ttu-id="75042-136">L’exemple suivant montre comment utiliser les `MyListener` `MyEventListener` \*\* \<auditeurs>\*\* élément pour ajouter les auditeurs et à la collection **Listeners.**</span><span class="sxs-lookup"><span data-stu-id="75042-136">The following example shows how to use the **\<listeners>** element to add the listeners `MyListener` and `MyEventListener` to the **Listeners** collection.</span></span> <span data-ttu-id="75042-137">`MyListener`crée un `MyListener.log` fichier appelé et écrit la sortie au fichier.</span><span class="sxs-lookup"><span data-stu-id="75042-137">`MyListener` creates a file called `MyListener.log` and writes the output to the file.</span></span> <span data-ttu-id="75042-138">`MyEventListener`crée une entrée dans le journal de l’événement.</span><span class="sxs-lookup"><span data-stu-id="75042-138">`MyEventListener` creates an entry in the event log.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="75042-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="75042-139">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="75042-140">Trace et Debug Paramètres Schema</span><span class="sxs-lookup"><span data-stu-id="75042-140">Trace and Debug Settings Schema</span></span>](index.md)
