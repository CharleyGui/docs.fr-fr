---
title: Élément <listeners> pour <source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners
helpviewer_keywords:
- listeners element for <source>
- <listeners> element for <source>
ms.assetid: a2991f43-b4d3-4614-a8e7-da392de9697f
ms.openlocfilehash: 853bc94978218fd4d426e6070b3a36e20435cd6d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920494"
---
# <a name="listeners-element-for-source"></a><span data-ttu-id="cdc28-102">\<écouteur > élément du \<> source</span><span class="sxs-lookup"><span data-stu-id="cdc28-102">\<listeners> Element for \<source></span></span>
<span data-ttu-id="cdc28-103">Ajoute ou supprime des écouteurs dans la <xref:System.Diagnostics.TraceSource.Listeners%2A> collection pour un <xref:System.Diagnostics.TraceSource>.</span><span class="sxs-lookup"><span data-stu-id="cdc28-103">Adds or removes listeners in the <xref:System.Diagnostics.TraceSource.Listeners%2A> collection for a <xref:System.Diagnostics.TraceSource>.</span></span> <span data-ttu-id="cdc28-104">Un écouteur dirige la sortie de suivi vers une cible appropriée, telle qu’un journal, une fenêtre ou un fichier texte.</span><span class="sxs-lookup"><span data-stu-id="cdc28-104">A listener directs the tracing output to an appropriate target, such as a log, window, or text file.</span></span>  
  
 <span data-ttu-id="cdc28-105">\<configuration></span><span class="sxs-lookup"><span data-stu-id="cdc28-105">\<configuration></span></span>  
<span data-ttu-id="cdc28-106">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="cdc28-106">\<system.diagnostics></span></span>  
<span data-ttu-id="cdc28-107">\<sources></span><span class="sxs-lookup"><span data-stu-id="cdc28-107">\<sources></span></span>  
<span data-ttu-id="cdc28-108">\<> source</span><span class="sxs-lookup"><span data-stu-id="cdc28-108">\<source></span></span>  
<span data-ttu-id="cdc28-109">\<Élément > d’écouteurs</span><span class="sxs-lookup"><span data-stu-id="cdc28-109">\<listeners> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cdc28-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cdc28-110">Syntax</span></span>  
  
```xml  
<listeners>   
  <add>...</add>  
  <remove ... />  
  <clear/>  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cdc28-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="cdc28-111">Attributes and Elements</span></span>  
 <span data-ttu-id="cdc28-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="cdc28-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cdc28-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="cdc28-113">Attributes</span></span>  
 <span data-ttu-id="cdc28-114">Aucun.</span><span class="sxs-lookup"><span data-stu-id="cdc28-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="cdc28-115">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="cdc28-115">Child Elements</span></span>  
  
|<span data-ttu-id="cdc28-116">Élément</span><span class="sxs-lookup"><span data-stu-id="cdc28-116">Element</span></span>|<span data-ttu-id="cdc28-117">Description</span><span class="sxs-lookup"><span data-stu-id="cdc28-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cdc28-118">\<add></span><span class="sxs-lookup"><span data-stu-id="cdc28-118">\<add></span></span>](add-element-for-listeners-for-source.md)|<span data-ttu-id="cdc28-119">Ajoute un écouteur à la collection `Listeners`.</span><span class="sxs-lookup"><span data-stu-id="cdc28-119">Adds a listener to the `Listeners` collection.</span></span>|  
|[<span data-ttu-id="cdc28-120">\<remove></span><span class="sxs-lookup"><span data-stu-id="cdc28-120">\<remove></span></span>](remove-element-for-listeners-for-source.md)|<span data-ttu-id="cdc28-121">Supprime un écouteur de la `Listeners` collection.</span><span class="sxs-lookup"><span data-stu-id="cdc28-121">Removes a listener from the `Listeners` collection.</span></span>|  
|[<span data-ttu-id="cdc28-122">\<clear></span><span class="sxs-lookup"><span data-stu-id="cdc28-122">\<clear></span></span>](clear-element-for-listeners-for-source.md)|<span data-ttu-id="cdc28-123">Efface la collection `Listeners` pour une source de trace.</span><span class="sxs-lookup"><span data-stu-id="cdc28-123">Clears the `Listeners` collection for a trace source.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cdc28-124">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="cdc28-124">Parent Elements</span></span>  
  
|<span data-ttu-id="cdc28-125">Élément</span><span class="sxs-lookup"><span data-stu-id="cdc28-125">Element</span></span>|<span data-ttu-id="cdc28-126">Description</span><span class="sxs-lookup"><span data-stu-id="cdc28-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="cdc28-127">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cdc28-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="cdc28-128">Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.</span><span class="sxs-lookup"><span data-stu-id="cdc28-128">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="cdc28-129">Contient les sources de trace qui lancent des messages de traçage.</span><span class="sxs-lookup"><span data-stu-id="cdc28-129">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="cdc28-130">Spécifie une source de trace qui lance des messages de traçage.</span><span class="sxs-lookup"><span data-stu-id="cdc28-130">Specifies a trace source that initiates tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cdc28-131">Notes</span><span class="sxs-lookup"><span data-stu-id="cdc28-131">Remarks</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="cdc28-132">Fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="cdc28-132">Configuration File</span></span>  
 <span data-ttu-id="cdc28-133">Cet élément peut être utilisé dans le fichier de configuration de l’ordinateur (machine. config) et dans le fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="cdc28-133">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cdc28-134">Exemples</span><span class="sxs-lookup"><span data-stu-id="cdc28-134">Example</span></span>  
 <span data-ttu-id="cdc28-135">L’exemple suivant montre comment utiliser l' `<listeners>` élément pour ajouter un écouteur de suivi de console à la `mySource` source et supprimer l’écouteur de suivi par défaut.</span><span class="sxs-lookup"><span data-stu-id="cdc28-135">The following example shows how to use the `<listeners>` element to add a console trace listener to the `mySource` source and to remove the default trace listener.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cdc28-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cdc28-136">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="cdc28-137">Schéma des paramètres de trace et de débogage</span><span class="sxs-lookup"><span data-stu-id="cdc28-137">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="cdc28-138">Écouteurs de suivi</span><span class="sxs-lookup"><span data-stu-id="cdc28-138">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
