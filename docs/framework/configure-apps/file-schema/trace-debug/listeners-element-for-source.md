---
title: Élément <listeners> pour <source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners
helpviewer_keywords:
- listeners element for <source>
- <listeners> element for <source>
ms.assetid: a2991f43-b4d3-4614-a8e7-da392de9697f
ms.openlocfilehash: 0eee325e01b41a15a19e4f40f479596f9d70f73b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153410"
---
# <a name="listeners-element-for-source"></a><span data-ttu-id="c22c8-102">\<auditeurs> Element \<pour les> source</span><span class="sxs-lookup"><span data-stu-id="c22c8-102">\<listeners> Element for \<source></span></span>
<span data-ttu-id="c22c8-103">Ajoute ou supprime les <xref:System.Diagnostics.TraceSource.Listeners%2A> auditeurs <xref:System.Diagnostics.TraceSource>de la collection pour un .</span><span class="sxs-lookup"><span data-stu-id="c22c8-103">Adds or removes listeners in the <xref:System.Diagnostics.TraceSource.Listeners%2A> collection for a <xref:System.Diagnostics.TraceSource>.</span></span> <span data-ttu-id="c22c8-104">Un auditeur dirige la sortie de traçage vers une cible appropriée, comme un journal, une fenêtre ou un fichier texte.</span><span class="sxs-lookup"><span data-stu-id="c22c8-104">A listener directs the tracing output to an appropriate target, such as a log, window, or text file.</span></span>  
  
[<span data-ttu-id="c22c8-105">**\<configuration>**</span><span class="sxs-lookup"><span data-stu-id="c22c8-105">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="c22c8-106">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="c22c8-106">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>  
<span data-ttu-id="c22c8-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)</span><span class="sxs-lookup"><span data-stu-id="c22c8-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)</span></span>  
<span data-ttu-id="c22c8-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)</span><span class="sxs-lookup"><span data-stu-id="c22c8-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)</span></span>  
<span data-ttu-id="c22c8-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<auditeurs>**</span><span class="sxs-lookup"><span data-stu-id="c22c8-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<listeners>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c22c8-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c22c8-110">Syntax</span></span>  
  
```xml  
<listeners>
  <add>...</add>  
  <remove ... />  
  <clear/>  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c22c8-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="c22c8-111">Attributes and Elements</span></span>  
 <span data-ttu-id="c22c8-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="c22c8-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c22c8-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="c22c8-113">Attributes</span></span>  
 <span data-ttu-id="c22c8-114">Aucun.</span><span class="sxs-lookup"><span data-stu-id="c22c8-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c22c8-115">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="c22c8-115">Child Elements</span></span>  
  
|<span data-ttu-id="c22c8-116">Élément</span><span class="sxs-lookup"><span data-stu-id="c22c8-116">Element</span></span>|<span data-ttu-id="c22c8-117">Description</span><span class="sxs-lookup"><span data-stu-id="c22c8-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c22c8-118">\<ajouter></span><span class="sxs-lookup"><span data-stu-id="c22c8-118">\<add></span></span>](add-element-for-listeners-for-source.md)|<span data-ttu-id="c22c8-119">Ajoute un écouteur à la collection `Listeners`.</span><span class="sxs-lookup"><span data-stu-id="c22c8-119">Adds a listener to the `Listeners` collection.</span></span>|  
|[<span data-ttu-id="c22c8-120">\<supprimer></span><span class="sxs-lookup"><span data-stu-id="c22c8-120">\<remove></span></span>](remove-element-for-listeners-for-source.md)|<span data-ttu-id="c22c8-121">Retire un auditeur de `Listeners` la collection.</span><span class="sxs-lookup"><span data-stu-id="c22c8-121">Removes a listener from the `Listeners` collection.</span></span>|  
|[<span data-ttu-id="c22c8-122">\<clair></span><span class="sxs-lookup"><span data-stu-id="c22c8-122">\<clear></span></span>](clear-element-for-listeners-for-source.md)|<span data-ttu-id="c22c8-123">Efface la collection `Listeners` pour une source de trace.</span><span class="sxs-lookup"><span data-stu-id="c22c8-123">Clears the `Listeners` collection for a trace source.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c22c8-124">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="c22c8-124">Parent Elements</span></span>  
  
|<span data-ttu-id="c22c8-125">Élément</span><span class="sxs-lookup"><span data-stu-id="c22c8-125">Element</span></span>|<span data-ttu-id="c22c8-126">Description</span><span class="sxs-lookup"><span data-stu-id="c22c8-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="c22c8-127">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c22c8-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="c22c8-128">Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.</span><span class="sxs-lookup"><span data-stu-id="c22c8-128">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="c22c8-129">Contient les sources de trace qui lancent des messages de traçage.</span><span class="sxs-lookup"><span data-stu-id="c22c8-129">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="c22c8-130">Spécifie une source de trace qui lance des messages de traçage.</span><span class="sxs-lookup"><span data-stu-id="c22c8-130">Specifies a trace source that initiates tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c22c8-131">Notes </span><span class="sxs-lookup"><span data-stu-id="c22c8-131">Remarks</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="c22c8-132">Fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="c22c8-132">Configuration File</span></span>  
 <span data-ttu-id="c22c8-133">Cet élément peut être utilisé dans le fichier de configuration de la machine (Machine.config) et le fichier de configuration d’application.</span><span class="sxs-lookup"><span data-stu-id="c22c8-133">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c22c8-134"> Exemple</span><span class="sxs-lookup"><span data-stu-id="c22c8-134">Example</span></span>  
 <span data-ttu-id="c22c8-135">L’exemple suivant montre `<listeners>` comment utiliser l’élément pour `mySource` ajouter un auditeur de trace de console à la source et pour supprimer l’auditeur de trace par défaut.</span><span class="sxs-lookup"><span data-stu-id="c22c8-135">The following example shows how to use the `<listeners>` element to add a console trace listener to the `mySource` source and to remove the default trace listener.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="mySource" switchName="sourceSwitch"
        switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <add name="console"
            type="System.Diagnostics.ConsoleTraceListener">  
            <filter type="System.Diagnostics.EventTypeFilter"
              initializeData="Error"/>  
          </add>  
          <remove name="Default"/>  
        </listeners>  
      </source>  
    </sources>  
    <switches>  
      <add name="sourceSwitch" value="Warning"/>  
    </switches>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c22c8-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c22c8-136">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="c22c8-137">Trace et Debug Paramètres Schema</span><span class="sxs-lookup"><span data-stu-id="c22c8-137">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="c22c8-138">Écouteurs de suivi</span><span class="sxs-lookup"><span data-stu-id="c22c8-138">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
