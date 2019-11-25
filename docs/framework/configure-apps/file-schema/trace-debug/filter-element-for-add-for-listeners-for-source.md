---
title: Élément <filter> pour <add> pour <listeners> pour <source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#filter
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- <filter> element for <add> for <listeners> for <source>
- filter element for <add> for <listeners> for <source>
ms.assetid: 15808b80-4579-4c25-b385-178cfdf154ba
ms.openlocfilehash: 766088b8a26ce3218031df74b193658ba8024280
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088909"
---
# <a name="filter-element-for-add-for-listeners-for-source"></a><span data-ttu-id="0c5ad-102">\<> un élément de filtre pour \<> d’écouteurs pour \<> Source \<</span><span class="sxs-lookup"><span data-stu-id="0c5ad-102">\<filter> Element for \<add> for \<listeners> for \<source></span></span>
<span data-ttu-id="0c5ad-103">Ajoute un filtre à un écouteur dans la collection `Listeners` pour une source de trace.</span><span class="sxs-lookup"><span data-stu-id="0c5ad-103">Adds a filter to a listener in the `Listeners` collection for a trace source.</span></span>  

<span data-ttu-id="0c5ad-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="0c5ad-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="0c5ad-105">&nbsp;&nbsp;[ **\<System. diagnostics >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="0c5ad-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="0c5ad-106">&nbsp;&nbsp;&nbsp;&nbsp;\<[**sources**](sources-element.md) ></span><span class="sxs-lookup"><span data-stu-id="0c5ad-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)\</span></span>
<span data-ttu-id="0c5ad-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**source**](source-element.md) ></span><span class="sxs-lookup"><span data-stu-id="0c5ad-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)</span></span>\
<span data-ttu-id="0c5ad-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ \**\<\** ](listeners-element-for-source.md)</span><span class="sxs-lookup"><span data-stu-id="0c5ad-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-source.md)\</span></span>
<span data-ttu-id="0c5ad-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**Ajouter**](add-element-for-listeners-for-source.md) ></span><span class="sxs-lookup"><span data-stu-id="0c5ad-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-listeners-for-source.md)</span></span>\
<span data-ttu-id="0c5ad-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<**</span><span class="sxs-lookup"><span data-stu-id="0c5ad-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filter>**</span></span>

## <a name="syntax"></a><span data-ttu-id="0c5ad-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0c5ad-111">Syntax</span></span>  
  
```xml  
<filter   
  type="traceFilterClassName"   
  initializeData="data" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0c5ad-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="0c5ad-112">Attributes and Elements</span></span>  
 <span data-ttu-id="0c5ad-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="0c5ad-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0c5ad-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="0c5ad-114">Attributes</span></span>  
  
|<span data-ttu-id="0c5ad-115">Attribut</span><span class="sxs-lookup"><span data-stu-id="0c5ad-115">Attribute</span></span>|<span data-ttu-id="0c5ad-116">Description</span><span class="sxs-lookup"><span data-stu-id="0c5ad-116">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="0c5ad-117">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="0c5ad-117">Required attribute.</span></span><br /><br /> <span data-ttu-id="0c5ad-118">Spécifie le type du filtre, qui doit hériter de la classe <xref:System.Diagnostics.TraceFilter>.</span><span class="sxs-lookup"><span data-stu-id="0c5ad-118">Specifies the type of the filter, which should inherit from the <xref:System.Diagnostics.TraceFilter> class.</span></span> <span data-ttu-id="0c5ad-119">Vous pouvez utiliser le nom qualifié par un espace de noms du type, qui correspond à la propriété <xref:System.Type.FullName%2A> du type, ou vous pouvez utiliser le nom de type qualifié complet, y compris les informations de l’assembly, qui correspond à la propriété <xref:System.Type.AssemblyQualifiedName%2A>.</span><span class="sxs-lookup"><span data-stu-id="0c5ad-119">You can use the namespace-qualified name of the type, which corresponds to the type's <xref:System.Type.FullName%2A> property, or you can use the fully qualified type name including the assembly information, which corresponds to the <xref:System.Type.AssemblyQualifiedName%2A> property.</span></span> <span data-ttu-id="0c5ad-120">Pour plus d’informations sur les noms de types qualifiés complets, consultez [spécification de noms de types qualifiés complets](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="0c5ad-120">For information about fully qualified type names, see [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="0c5ad-121">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="0c5ad-121">Optional attribute.</span></span><br /><br /> <span data-ttu-id="0c5ad-122">Chaîne passée au constructeur pour la classe de filtre spécifiée.</span><span class="sxs-lookup"><span data-stu-id="0c5ad-122">The string passed to the constructor for the specified filter class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0c5ad-123">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="0c5ad-123">Child Elements</span></span>  
 <span data-ttu-id="0c5ad-124">Aucun(e).</span><span class="sxs-lookup"><span data-stu-id="0c5ad-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0c5ad-125">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="0c5ad-125">Parent Elements</span></span>  
  
|<span data-ttu-id="0c5ad-126">Élément</span><span class="sxs-lookup"><span data-stu-id="0c5ad-126">Element</span></span>|<span data-ttu-id="0c5ad-127">Description</span><span class="sxs-lookup"><span data-stu-id="0c5ad-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="0c5ad-128">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0c5ad-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="0c5ad-129">Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.</span><span class="sxs-lookup"><span data-stu-id="0c5ad-129">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="0c5ad-130">Contient les sources de trace qui lancent des messages de traçage.</span><span class="sxs-lookup"><span data-stu-id="0c5ad-130">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="0c5ad-131">Spécifie une source de trace qui lance des messages de traçage.</span><span class="sxs-lookup"><span data-stu-id="0c5ad-131">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="0c5ad-132">Contient des écouteurs qui collectent, stockent et acheminent des messages.</span><span class="sxs-lookup"><span data-stu-id="0c5ad-132">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="0c5ad-133">Les écouteurs dirigent la sortie de suivi vers une cible appropriée.</span><span class="sxs-lookup"><span data-stu-id="0c5ad-133">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`add`|<span data-ttu-id="0c5ad-134">Ajoute un écouteur à la collection `Listeners` pour une source de trace.</span><span class="sxs-lookup"><span data-stu-id="0c5ad-134">Adds a listener to the `Listeners` collection for a trace source.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0c5ad-135">Notes</span><span class="sxs-lookup"><span data-stu-id="0c5ad-135">Remarks</span></span>  
 <span data-ttu-id="0c5ad-136">L’élément `<filter>` doit être contenu dans un élément `<add>` pour un écouteur source de suivi qui spécifie le type de l’écouteur, pas seulement le nom d’un écouteur défini dans un [\<sharedListeners](sharedlisteners-element.md).</span><span class="sxs-lookup"><span data-stu-id="0c5ad-136">The `<filter>` element must be contained in an `<add>` element for a trace source listener that specifies the type of the listener, not just the name of a listener defined in a [\<sharedListeners>](sharedlisteners-element.md).</span></span> <span data-ttu-id="0c5ad-137">Si l’écouteur est défini dans une [\<sharedListeners](sharedlisteners-element.md), le filtre de cet écouteur doit être défini dans cet élément.</span><span class="sxs-lookup"><span data-stu-id="0c5ad-137">If the listener is defined in a [\<sharedListeners>](sharedlisteners-element.md), the filter for that listener must be defined in that element.</span></span>  
  
 <span data-ttu-id="0c5ad-138">Cet élément peut être utilisé dans le fichier de configuration de l’ordinateur (machine. config) et dans le fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="0c5ad-138">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0c5ad-139">Exemple</span><span class="sxs-lookup"><span data-stu-id="0c5ad-139">Example</span></span>  
 <span data-ttu-id="0c5ad-140">L’exemple suivant montre comment utiliser l’élément `<filter>` pour ajouter un filtre à l’écouteur `console` dans la collection `Listeners` pour le `myTraceSource`de la source de trace, en spécifiant le niveau d’événement de filtre en tant que `Error`.</span><span class="sxs-lookup"><span data-stu-id="0c5ad-140">The following example shows how to use the `<filter>` element to add a filter to the listener `console` in the `Listeners` collection for the trace source `myTraceSource`, specifying the filter event level as `Error`.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="myTraceSource" switchName="SourceSwitch"   
        switchType="System.Diagnostics.SourceSwitch"  >  
        <listeners>  
          <add name="console"   
            type="System.Diagnostics.ConsoleTraceListener" >  
            <filter type="System.Diagnostics.EventTypeFilter"   
              initializeData="Error" />  
          </add>  
          <remove name="Default" />  
        </listeners>  
      </source>  
    </sources>  
    <switches>  
      <add name="SourceSwitch" value="Warning" />  
    </switches>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0c5ad-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0c5ad-141">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceFilter>
- [<span data-ttu-id="0c5ad-142">Schéma des paramètres de trace et de débogage</span><span class="sxs-lookup"><span data-stu-id="0c5ad-142">Trace and Debug Settings Schema</span></span>](index.md)
