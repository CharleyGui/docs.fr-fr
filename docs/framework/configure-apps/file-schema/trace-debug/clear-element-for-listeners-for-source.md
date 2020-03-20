---
title: <clear>Élément <listeners> pour pour<source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/clear
helpviewer_keywords:
- <clear> element for <listeners> for <source>
- clear element for <listeners> for <source>
ms.assetid: 76796bb2-9c0b-4526-8135-8bf18b16d8d9
ms.openlocfilehash: 7f9ddd93d27c3619119702c82c9e8752dab1af7b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153579"
---
# <a name="clear-element-for-listeners-for-source"></a><span data-ttu-id="5dcad-102">\<élément> clair pour \<les auditeurs \<> pour les> de source</span><span class="sxs-lookup"><span data-stu-id="5dcad-102">\<clear> Element for \<listeners> for \<source></span></span>
<span data-ttu-id="5dcad-103">Efface la collection `Listeners` pour une source de trace.</span><span class="sxs-lookup"><span data-stu-id="5dcad-103">Clears the `Listeners` collection for a trace source.</span></span>  

<span data-ttu-id="5dcad-104">[**\<configuration>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="5dcad-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5dcad-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="5dcad-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="5dcad-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)</span><span class="sxs-lookup"><span data-stu-id="5dcad-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)</span></span>\
<span data-ttu-id="5dcad-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)</span><span class="sxs-lookup"><span data-stu-id="5dcad-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)</span></span>\
<span data-ttu-id="5dcad-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<auditeurs>**](listeners-element-for-source.md)</span><span class="sxs-lookup"><span data-stu-id="5dcad-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-source.md)</span></span>\
<span data-ttu-id="5dcad-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clair>**</span><span class="sxs-lookup"><span data-stu-id="5dcad-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="5dcad-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5dcad-110">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5dcad-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="5dcad-111">Attributes and Elements</span></span>  
 <span data-ttu-id="5dcad-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="5dcad-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5dcad-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="5dcad-113">Attributes</span></span>  
 <span data-ttu-id="5dcad-114">Aucun.</span><span class="sxs-lookup"><span data-stu-id="5dcad-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5dcad-115">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="5dcad-115">Child Elements</span></span>  
 <span data-ttu-id="5dcad-116">Aucun.</span><span class="sxs-lookup"><span data-stu-id="5dcad-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5dcad-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="5dcad-117">Parent Elements</span></span>  
  
|<span data-ttu-id="5dcad-118">Élément</span><span class="sxs-lookup"><span data-stu-id="5dcad-118">Element</span></span>|<span data-ttu-id="5dcad-119">Description</span><span class="sxs-lookup"><span data-stu-id="5dcad-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="5dcad-120">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5dcad-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="5dcad-121">Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.</span><span class="sxs-lookup"><span data-stu-id="5dcad-121">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="5dcad-122">Contient les sources de trace qui lancent des messages de traçage.</span><span class="sxs-lookup"><span data-stu-id="5dcad-122">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="5dcad-123">Spécifie une source de trace qui lance des messages de traçage.</span><span class="sxs-lookup"><span data-stu-id="5dcad-123">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="5dcad-124">Spécifie les auditeurs qui recueillent, stockent et acheminent les messages.</span><span class="sxs-lookup"><span data-stu-id="5dcad-124">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5dcad-125">Notes </span><span class="sxs-lookup"><span data-stu-id="5dcad-125">Remarks</span></span>  
 <span data-ttu-id="5dcad-126">L’élément `<clear>` supprime tous `Listeners` les auditeurs de la <xref:System.Diagnostics.DefaultTraceListener>collection pour une source de trace, y compris le .</span><span class="sxs-lookup"><span data-stu-id="5dcad-126">The `<clear>` element removes all listeners from the `Listeners` collection for a trace source, including the <xref:System.Diagnostics.DefaultTraceListener>.</span></span> <span data-ttu-id="5dcad-127">Vous pouvez `<clear>` utiliser l’élément avant d’utiliser l’élément `<add>` pour être certain qu’il n’y a pas d’autres auditeurs actifs dans la collection.</span><span class="sxs-lookup"><span data-stu-id="5dcad-127">You can use the `<clear>` element before using the `<add>` element to be certain there are no other active listeners in the collection.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="5dcad-128">Fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="5dcad-128">Configuration File</span></span>  
 <span data-ttu-id="5dcad-129">Cet élément peut être utilisé dans le fichier de configuration de la machine (Machine.config) et le fichier de configuration d’application.</span><span class="sxs-lookup"><span data-stu-id="5dcad-129">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5dcad-130"> Exemple</span><span class="sxs-lookup"><span data-stu-id="5dcad-130">Example</span></span>  
 <span data-ttu-id="5dcad-131">L’exemple suivant montre `<clear>` comment utiliser `<add>` l’élément avant `console` `textListener` d’utiliser les éléments pour ajouter les auditeurs et à la `Listeners` collection pour la source `TraceSourceApp`de traces .</span><span class="sxs-lookup"><span data-stu-id="5dcad-131">The following example shows how to use the `<clear>` element before using the `<add>` elements to add the listeners `console` and `textListener` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5dcad-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5dcad-132">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="5dcad-133">Trace et Debug Paramètres Schema</span><span class="sxs-lookup"><span data-stu-id="5dcad-133">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="5dcad-134">Écouteurs de suivi</span><span class="sxs-lookup"><span data-stu-id="5dcad-134">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
