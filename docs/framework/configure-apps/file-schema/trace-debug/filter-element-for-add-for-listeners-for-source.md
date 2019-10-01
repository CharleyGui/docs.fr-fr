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
ms.openlocfilehash: ec288685f47c8a35e2371c31d359b604a4967196
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697163"
---
# <a name="filter-element-for-add-for-listeners-for-source"></a><span data-ttu-id="9b8dd-102">\<filter > élément de \<Add > pour \<listeners > pour \<Source ></span><span class="sxs-lookup"><span data-stu-id="9b8dd-102">\<filter> Element for \<add> for \<listeners> for \<source></span></span>
<span data-ttu-id="9b8dd-103">Ajoute un filtre à un écouteur dans la collection `Listeners` pour une source de trace.</span><span class="sxs-lookup"><span data-stu-id="9b8dd-103">Adds a filter to a listener in the `Listeners` collection for a trace source.</span></span>  
  
[<span data-ttu-id="9b8dd-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="9b8dd-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="9b8dd-105">&nbsp; @ no__t-1[ **\<System. diagnostics >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="9b8dd-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>  
<span data-ttu-id="9b8dd-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<sources >** ](sources-element.md)</span><span class="sxs-lookup"><span data-stu-id="9b8dd-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)</span></span>  
<span data-ttu-id="9b8dd-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5[ **\<source >** ](source-element.md)</span><span class="sxs-lookup"><span data-stu-id="9b8dd-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)</span></span>  
<span data-ttu-id="9b8dd-108">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7[ **&nbsp;0listeners >** ](listeners-element-for-source.md)</span><span class="sxs-lookup"><span data-stu-id="9b8dd-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-source.md)</span></span>  
<span data-ttu-id="9b8dd-109">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7 @ no__t-8 @ no__t-9[ **&nbsp;2Add >** ](add-element-for-listeners-for-source.md)</span><span class="sxs-lookup"><span data-stu-id="9b8dd-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-listeners-for-source.md)</span></span>  
<span data-ttu-id="9b8dd-110">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7 @ no__t-8 @ no__t-9 @ no__t-10 @ no__t-11 **&nbsp;3filter >**</span><span class="sxs-lookup"><span data-stu-id="9b8dd-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filter>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b8dd-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9b8dd-111">Syntax</span></span>  
  
```xml  
<filter   
  type="traceFilterClassName"   
  initializeData="data" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9b8dd-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="9b8dd-112">Attributes and Elements</span></span>  
 <span data-ttu-id="9b8dd-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="9b8dd-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9b8dd-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="9b8dd-114">Attributes</span></span>  
  
|<span data-ttu-id="9b8dd-115">Attribut</span><span class="sxs-lookup"><span data-stu-id="9b8dd-115">Attribute</span></span>|<span data-ttu-id="9b8dd-116">Description</span><span class="sxs-lookup"><span data-stu-id="9b8dd-116">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="9b8dd-117">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="9b8dd-117">Required attribute.</span></span><br /><br /> <span data-ttu-id="9b8dd-118">Spécifie le type du filtre, qui doit hériter de la classe <xref:System.Diagnostics.TraceFilter>.</span><span class="sxs-lookup"><span data-stu-id="9b8dd-118">Specifies the type of the filter, which should inherit from the <xref:System.Diagnostics.TraceFilter> class.</span></span> <span data-ttu-id="9b8dd-119">Vous pouvez utiliser le nom qualifié par un espace de noms du type, qui correspond à la propriété <xref:System.Type.FullName%2A> du type, ou vous pouvez utiliser le nom de type qualifié complet, y compris les informations de l’assembly, qui correspond à la propriété <xref:System.Type.AssemblyQualifiedName%2A>.</span><span class="sxs-lookup"><span data-stu-id="9b8dd-119">You can use the namespace-qualified name of the type, which corresponds to the type's <xref:System.Type.FullName%2A> property, or you can use the fully qualified type name including the assembly information, which corresponds to the <xref:System.Type.AssemblyQualifiedName%2A> property.</span></span> <span data-ttu-id="9b8dd-120">Pour plus d’informations sur les noms de types qualifiés complets, consultez [spécification de noms de types qualifiés complets](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="9b8dd-120">For information about fully qualified type names, see [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="9b8dd-121">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="9b8dd-121">Optional attribute.</span></span><br /><br /> <span data-ttu-id="9b8dd-122">Chaîne passée au constructeur pour la classe de filtre spécifiée.</span><span class="sxs-lookup"><span data-stu-id="9b8dd-122">The string passed to the constructor for the specified filter class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9b8dd-123">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="9b8dd-123">Child Elements</span></span>  
 <span data-ttu-id="9b8dd-124">Aucun.</span><span class="sxs-lookup"><span data-stu-id="9b8dd-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9b8dd-125">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="9b8dd-125">Parent Elements</span></span>  
  
|<span data-ttu-id="9b8dd-126">Élément</span><span class="sxs-lookup"><span data-stu-id="9b8dd-126">Element</span></span>|<span data-ttu-id="9b8dd-127">Description</span><span class="sxs-lookup"><span data-stu-id="9b8dd-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="9b8dd-128">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9b8dd-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="9b8dd-129">Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.</span><span class="sxs-lookup"><span data-stu-id="9b8dd-129">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="9b8dd-130">Contient les sources de trace qui lancent des messages de traçage.</span><span class="sxs-lookup"><span data-stu-id="9b8dd-130">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="9b8dd-131">Spécifie une source de trace qui lance des messages de traçage.</span><span class="sxs-lookup"><span data-stu-id="9b8dd-131">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="9b8dd-132">Contient des écouteurs qui collectent, stockent et acheminent des messages.</span><span class="sxs-lookup"><span data-stu-id="9b8dd-132">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="9b8dd-133">Les écouteurs dirigent la sortie de suivi vers une cible appropriée.</span><span class="sxs-lookup"><span data-stu-id="9b8dd-133">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`add`|<span data-ttu-id="9b8dd-134">Ajoute un écouteur à la collection `Listeners` pour une source de trace.</span><span class="sxs-lookup"><span data-stu-id="9b8dd-134">Adds a listener to the `Listeners` collection for a trace source.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9b8dd-135">Notes</span><span class="sxs-lookup"><span data-stu-id="9b8dd-135">Remarks</span></span>  
 <span data-ttu-id="9b8dd-136">L’élément `<filter>` doit être contenu dans un élément `<add>` pour un écouteur source de suivi qui spécifie le type de l’écouteur, pas seulement le nom d’un écouteur défini dans un [> \<sharedListeners](sharedlisteners-element.md).</span><span class="sxs-lookup"><span data-stu-id="9b8dd-136">The `<filter>` element must be contained in an `<add>` element for a trace source listener that specifies the type of the listener, not just the name of a listener defined in a [\<sharedListeners>](sharedlisteners-element.md).</span></span> <span data-ttu-id="9b8dd-137">Si l’écouteur est défini dans une [> \<sharedListeners](sharedlisteners-element.md), le filtre de cet écouteur doit être défini dans cet élément.</span><span class="sxs-lookup"><span data-stu-id="9b8dd-137">If the listener is defined in a [\<sharedListeners>](sharedlisteners-element.md), the filter for that listener must be defined in that element.</span></span>  
  
 <span data-ttu-id="9b8dd-138">Cet élément peut être utilisé dans le fichier de configuration de l’ordinateur (machine. config) et dans le fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="9b8dd-138">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9b8dd-139">Exemple</span><span class="sxs-lookup"><span data-stu-id="9b8dd-139">Example</span></span>  
 <span data-ttu-id="9b8dd-140">L’exemple suivant montre comment utiliser l’élément `<filter>` pour ajouter un filtre à l’écouteur `console` dans la collection `Listeners` pour la source de suivi `myTraceSource`, en spécifiant le niveau d’événement de filtre en tant que `Error`.</span><span class="sxs-lookup"><span data-stu-id="9b8dd-140">The following example shows how to use the `<filter>` element to add a filter to the listener `console` in the `Listeners` collection for the trace source `myTraceSource`, specifying the filter event level as `Error`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9b8dd-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9b8dd-141">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceFilter>
- [<span data-ttu-id="9b8dd-142">Schéma des paramètres de trace et de débogage</span><span class="sxs-lookup"><span data-stu-id="9b8dd-142">Trace and Debug Settings Schema</span></span>](index.md)
