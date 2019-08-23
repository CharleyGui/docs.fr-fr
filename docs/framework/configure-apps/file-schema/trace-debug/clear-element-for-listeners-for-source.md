---
title: <clear>, Élément <listeners> de pour<source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/clear
helpviewer_keywords:
- <clear> element for <listeners> for <source>
- clear element for <listeners> for <source>
ms.assetid: 76796bb2-9c0b-4526-8135-8bf18b16d8d9
ms.openlocfilehash: 768d51a74b4c31d1250d2f5d6517f760f886e0a0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920550"
---
# <a name="clear-element-for-listeners-for-source"></a><span data-ttu-id="58354-102">\<Clear > élément pour \<les écouteurs > pour \<le > source</span><span class="sxs-lookup"><span data-stu-id="58354-102">\<clear> Element for \<listeners> for \<source></span></span>
<span data-ttu-id="58354-103">Efface la collection `Listeners` pour une source de trace.</span><span class="sxs-lookup"><span data-stu-id="58354-103">Clears the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="58354-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="58354-104">\<configuration></span></span>  
<span data-ttu-id="58354-105">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="58354-105">\<system.diagnostics></span></span>  
<span data-ttu-id="58354-106">\<sources></span><span class="sxs-lookup"><span data-stu-id="58354-106">\<sources></span></span>  
<span data-ttu-id="58354-107">\<> source</span><span class="sxs-lookup"><span data-stu-id="58354-107">\<source></span></span>  
<span data-ttu-id="58354-108">\<listeners></span><span class="sxs-lookup"><span data-stu-id="58354-108">\<listeners></span></span>  
<span data-ttu-id="58354-109">\<clear></span><span class="sxs-lookup"><span data-stu-id="58354-109">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58354-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="58354-110">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="58354-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="58354-111">Attributes and Elements</span></span>  
 <span data-ttu-id="58354-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="58354-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="58354-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="58354-113">Attributes</span></span>  
 <span data-ttu-id="58354-114">Aucun.</span><span class="sxs-lookup"><span data-stu-id="58354-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="58354-115">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="58354-115">Child Elements</span></span>  
 <span data-ttu-id="58354-116">Aucun.</span><span class="sxs-lookup"><span data-stu-id="58354-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="58354-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="58354-117">Parent Elements</span></span>  
  
|<span data-ttu-id="58354-118">Élément</span><span class="sxs-lookup"><span data-stu-id="58354-118">Element</span></span>|<span data-ttu-id="58354-119">Description</span><span class="sxs-lookup"><span data-stu-id="58354-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="58354-120">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="58354-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="58354-121">Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.</span><span class="sxs-lookup"><span data-stu-id="58354-121">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="58354-122">Contient les sources de trace qui lancent des messages de traçage.</span><span class="sxs-lookup"><span data-stu-id="58354-122">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="58354-123">Spécifie une source de trace qui lance des messages de traçage.</span><span class="sxs-lookup"><span data-stu-id="58354-123">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="58354-124">Spécifie les écouteurs qui collectent, stockent et acheminent les messages.</span><span class="sxs-lookup"><span data-stu-id="58354-124">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="58354-125">Notes</span><span class="sxs-lookup"><span data-stu-id="58354-125">Remarks</span></span>  
 <span data-ttu-id="58354-126">L' `<clear>` élément supprime tous les écouteurs de la `Listeners` collection pour une source de <xref:System.Diagnostics.DefaultTraceListener>suivi, y compris.</span><span class="sxs-lookup"><span data-stu-id="58354-126">The `<clear>` element removes all listeners from the `Listeners` collection for a trace source, including the <xref:System.Diagnostics.DefaultTraceListener>.</span></span> <span data-ttu-id="58354-127">Vous pouvez utiliser l' `<clear>` élément avant d’utiliser `<add>` l’élément pour être certain qu’il n’existe aucun autre écouteur actif dans la collection.</span><span class="sxs-lookup"><span data-stu-id="58354-127">You can use the `<clear>` element before using the `<add>` element to be certain there are no other active listeners in the collection.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="58354-128">Fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="58354-128">Configuration File</span></span>  
 <span data-ttu-id="58354-129">Cet élément peut être utilisé dans le fichier de configuration de l’ordinateur (machine. config) et dans le fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="58354-129">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="58354-130">Exemples</span><span class="sxs-lookup"><span data-stu-id="58354-130">Example</span></span>  
 <span data-ttu-id="58354-131">L’exemple suivant montre comment utiliser l' `<clear>` élément avant d’utiliser les `<add>` éléments `console` pour ajouter les écouteurs et `textListener` la `Listeners` collection pour la source `TraceSourceApp`de trace.</span><span class="sxs-lookup"><span data-stu-id="58354-131">The following example shows how to use the `<clear>` element before using the `<add>` elements to add the listeners `console` and `textListener` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
       <source name="TraceSourceApp" switchName="sourceSwitch"   
         switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <clear/>  
          <add name="console"   
            type="System.Diagnostics.ConsoleTraceListener"/>  
          <add name="textListener"/>  
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
  
## <a name="see-also"></a><span data-ttu-id="58354-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="58354-132">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="58354-133">Schéma des paramètres de trace et de débogage</span><span class="sxs-lookup"><span data-stu-id="58354-133">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="58354-134">Écouteurs de suivi</span><span class="sxs-lookup"><span data-stu-id="58354-134">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
