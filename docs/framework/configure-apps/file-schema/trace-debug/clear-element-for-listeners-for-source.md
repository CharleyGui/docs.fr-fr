---
title: <clear>, élément de <listeners> pour <source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/clear
helpviewer_keywords:
- <clear> element for <listeners> for <source>
- clear element for <listeners> for <source>
ms.assetid: 76796bb2-9c0b-4526-8135-8bf18b16d8d9
ms.openlocfilehash: 4567f236397435e89371ca4c80730ff964fddd21
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088934"
---
# <a name="clear-element-for-listeners-for-source"></a><span data-ttu-id="fe72f-102">\<> élément Clear pour \<écouteurs > pour \<source ></span><span class="sxs-lookup"><span data-stu-id="fe72f-102">\<clear> Element for \<listeners> for \<source></span></span>
<span data-ttu-id="fe72f-103">Efface la collection `Listeners` pour une source de trace.</span><span class="sxs-lookup"><span data-stu-id="fe72f-103">Clears the `Listeners` collection for a trace source.</span></span>  

<span data-ttu-id="fe72f-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="fe72f-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="fe72f-105">&nbsp;&nbsp;[ **\<System. diagnostics >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="fe72f-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="fe72f-106">&nbsp;&nbsp;&nbsp;&nbsp;\<[**sources**](sources-element.md) ></span><span class="sxs-lookup"><span data-stu-id="fe72f-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)\</span></span>
<span data-ttu-id="fe72f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**source**](source-element.md) ></span><span class="sxs-lookup"><span data-stu-id="fe72f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)</span></span>\
<span data-ttu-id="fe72f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ \**\<\** ](listeners-element-for-source.md)</span><span class="sxs-lookup"><span data-stu-id="fe72f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-source.md)\</span></span>
<span data-ttu-id="fe72f-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**Clear** ></span><span class="sxs-lookup"><span data-stu-id="fe72f-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="fe72f-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fe72f-110">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fe72f-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="fe72f-111">Attributes and Elements</span></span>  
 <span data-ttu-id="fe72f-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="fe72f-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fe72f-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="fe72f-113">Attributes</span></span>  
 <span data-ttu-id="fe72f-114">Aucun(e).</span><span class="sxs-lookup"><span data-stu-id="fe72f-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="fe72f-115">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="fe72f-115">Child Elements</span></span>  
 <span data-ttu-id="fe72f-116">Aucun(e).</span><span class="sxs-lookup"><span data-stu-id="fe72f-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fe72f-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="fe72f-117">Parent Elements</span></span>  
  
|<span data-ttu-id="fe72f-118">Élément</span><span class="sxs-lookup"><span data-stu-id="fe72f-118">Element</span></span>|<span data-ttu-id="fe72f-119">Description</span><span class="sxs-lookup"><span data-stu-id="fe72f-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="fe72f-120">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fe72f-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="fe72f-121">Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.</span><span class="sxs-lookup"><span data-stu-id="fe72f-121">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="fe72f-122">Contient les sources de trace qui lancent des messages de traçage.</span><span class="sxs-lookup"><span data-stu-id="fe72f-122">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="fe72f-123">Spécifie une source de trace qui lance des messages de traçage.</span><span class="sxs-lookup"><span data-stu-id="fe72f-123">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="fe72f-124">Spécifie les écouteurs qui collectent, stockent et acheminent les messages.</span><span class="sxs-lookup"><span data-stu-id="fe72f-124">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fe72f-125">Notes</span><span class="sxs-lookup"><span data-stu-id="fe72f-125">Remarks</span></span>  
 <span data-ttu-id="fe72f-126">L’élément `<clear>` supprime tous les écouteurs de la collection `Listeners` pour une source de suivi, y compris le <xref:System.Diagnostics.DefaultTraceListener>.</span><span class="sxs-lookup"><span data-stu-id="fe72f-126">The `<clear>` element removes all listeners from the `Listeners` collection for a trace source, including the <xref:System.Diagnostics.DefaultTraceListener>.</span></span> <span data-ttu-id="fe72f-127">Vous pouvez utiliser l’élément `<clear>` avant d’utiliser l’élément `<add>` pour être certain qu’il n’existe aucun autre écouteur actif dans la collection.</span><span class="sxs-lookup"><span data-stu-id="fe72f-127">You can use the `<clear>` element before using the `<add>` element to be certain there are no other active listeners in the collection.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="fe72f-128">Fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="fe72f-128">Configuration File</span></span>  
 <span data-ttu-id="fe72f-129">Cet élément peut être utilisé dans le fichier de configuration de l’ordinateur (machine. config) et dans le fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="fe72f-129">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fe72f-130">Exemple</span><span class="sxs-lookup"><span data-stu-id="fe72f-130">Example</span></span>  
 <span data-ttu-id="fe72f-131">L’exemple suivant montre comment utiliser l’élément `<clear>` avant d’utiliser les éléments `<add>` pour ajouter les écouteurs `console` et `textListener` à la collection `Listeners` pour le `TraceSourceApp`de la source de trace.</span><span class="sxs-lookup"><span data-stu-id="fe72f-131">The following example shows how to use the `<clear>` element before using the `<add>` elements to add the listeners `console` and `textListener` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fe72f-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fe72f-132">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="fe72f-133">Schéma des paramètres de trace et de débogage</span><span class="sxs-lookup"><span data-stu-id="fe72f-133">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="fe72f-134">Écouteurs de suivi</span><span class="sxs-lookup"><span data-stu-id="fe72f-134">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
