---
title: <filter>Élément <add> pour <listeners> pour pour pour<source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#filter
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- <filter> element for <add> for <listeners> for <source>
- filter element for <add> for <listeners> for <source>
ms.assetid: 15808b80-4579-4c25-b385-178cfdf154ba
ms.openlocfilehash: 0cb668782de263d5f784691f46cb8b74541d942b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153514"
---
# <a name="filter-element-for-add-for-listeners-for-source"></a><span data-ttu-id="b2ec0-102">\<filtrer> Element \<pour ajouter de \<la> pour \<les auditeurs> pour les> de source</span><span class="sxs-lookup"><span data-stu-id="b2ec0-102">\<filter> Element for \<add> for \<listeners> for \<source></span></span>
<span data-ttu-id="b2ec0-103">Ajoute un filtre à un écouteur dans la collection `Listeners` pour une source de trace.</span><span class="sxs-lookup"><span data-stu-id="b2ec0-103">Adds a filter to a listener in the `Listeners` collection for a trace source.</span></span>  

<span data-ttu-id="b2ec0-104">[**\<configuration>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b2ec0-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b2ec0-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="b2ec0-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="b2ec0-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)</span><span class="sxs-lookup"><span data-stu-id="b2ec0-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)</span></span>\
<span data-ttu-id="b2ec0-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)</span><span class="sxs-lookup"><span data-stu-id="b2ec0-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)</span></span>\
<span data-ttu-id="b2ec0-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<auditeurs>**](listeners-element-for-source.md)</span><span class="sxs-lookup"><span data-stu-id="b2ec0-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-source.md)</span></span>\
<span data-ttu-id="b2ec0-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ajouter>**](add-element-for-listeners-for-source.md)</span><span class="sxs-lookup"><span data-stu-id="b2ec0-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-listeners-for-source.md)</span></span>\
<span data-ttu-id="b2ec0-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filtrer>**</span><span class="sxs-lookup"><span data-stu-id="b2ec0-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filter>**</span></span>

## <a name="syntax"></a><span data-ttu-id="b2ec0-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b2ec0-111">Syntax</span></span>  
  
```xml  
<filter
  type="traceFilterClassName"
  initializeData="data" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b2ec0-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="b2ec0-112">Attributes and Elements</span></span>  
 <span data-ttu-id="b2ec0-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="b2ec0-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b2ec0-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="b2ec0-114">Attributes</span></span>  
  
|<span data-ttu-id="b2ec0-115">Attribut</span><span class="sxs-lookup"><span data-stu-id="b2ec0-115">Attribute</span></span>|<span data-ttu-id="b2ec0-116">Description</span><span class="sxs-lookup"><span data-stu-id="b2ec0-116">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="b2ec0-117">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="b2ec0-117">Required attribute.</span></span><br /><br /> <span data-ttu-id="b2ec0-118">Spécifie le type de filtre, <xref:System.Diagnostics.TraceFilter> qui devrait hériter de la classe.</span><span class="sxs-lookup"><span data-stu-id="b2ec0-118">Specifies the type of the filter, which should inherit from the <xref:System.Diagnostics.TraceFilter> class.</span></span> <span data-ttu-id="b2ec0-119">Vous pouvez utiliser le nom du type, qui correspond à <xref:System.Type.FullName%2A> la propriété du type, ou vous pouvez utiliser le nom <xref:System.Type.AssemblyQualifiedName%2A> de type entièrement qualifié, y compris les informations d’assemblage, qui correspond à la propriété.</span><span class="sxs-lookup"><span data-stu-id="b2ec0-119">You can use the namespace-qualified name of the type, which corresponds to the type's <xref:System.Type.FullName%2A> property, or you can use the fully qualified type name including the assembly information, which corresponds to the <xref:System.Type.AssemblyQualifiedName%2A> property.</span></span> <span data-ttu-id="b2ec0-120">Pour plus d’informations sur les noms de type entièrement qualifiés, voir [spécifier des noms de type entièrement qualifiés](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="b2ec0-120">For information about fully qualified type names, see [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="b2ec0-121">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="b2ec0-121">Optional attribute.</span></span><br /><br /> <span data-ttu-id="b2ec0-122">La chaîne est passée au constructeur pour la classe de filtre spécifiée.</span><span class="sxs-lookup"><span data-stu-id="b2ec0-122">The string passed to the constructor for the specified filter class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b2ec0-123">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="b2ec0-123">Child Elements</span></span>  
 <span data-ttu-id="b2ec0-124">Aucun.</span><span class="sxs-lookup"><span data-stu-id="b2ec0-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b2ec0-125">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="b2ec0-125">Parent Elements</span></span>  
  
|<span data-ttu-id="b2ec0-126">Élément</span><span class="sxs-lookup"><span data-stu-id="b2ec0-126">Element</span></span>|<span data-ttu-id="b2ec0-127">Description</span><span class="sxs-lookup"><span data-stu-id="b2ec0-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="b2ec0-128">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b2ec0-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="b2ec0-129">Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.</span><span class="sxs-lookup"><span data-stu-id="b2ec0-129">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="b2ec0-130">Contient les sources de trace qui lancent des messages de traçage.</span><span class="sxs-lookup"><span data-stu-id="b2ec0-130">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="b2ec0-131">Spécifie une source de trace qui lance des messages de traçage.</span><span class="sxs-lookup"><span data-stu-id="b2ec0-131">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="b2ec0-132">Contient des auditeurs qui recueillent, stockent et acheminent des messages.</span><span class="sxs-lookup"><span data-stu-id="b2ec0-132">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="b2ec0-133">Les auditeurs dirigent la sortie de traçage vers une cible appropriée.</span><span class="sxs-lookup"><span data-stu-id="b2ec0-133">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`add`|<span data-ttu-id="b2ec0-134">Ajoute un écouteur à la collection `Listeners` pour une source de trace.</span><span class="sxs-lookup"><span data-stu-id="b2ec0-134">Adds a listener to the `Listeners` collection for a trace source.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b2ec0-135">Notes </span><span class="sxs-lookup"><span data-stu-id="b2ec0-135">Remarks</span></span>  
 <span data-ttu-id="b2ec0-136">L’élément `<filter>` doit être `<add>` contenu dans un élément pour un auditeur de source de trace qui spécifie le type de l’auditeur, et pas seulement le nom d’un auditeur défini dans un [ \<>d’écoutes partagées ](sharedlisteners-element.md).</span><span class="sxs-lookup"><span data-stu-id="b2ec0-136">The `<filter>` element must be contained in an `<add>` element for a trace source listener that specifies the type of the listener, not just the name of a listener defined in a [\<sharedListeners>](sharedlisteners-element.md).</span></span> <span data-ttu-id="b2ec0-137">Si l’auditeur est défini dans un [ \<>d’écoute partagé, ](sharedlisteners-element.md)le filtre de cet auditeur doit être défini dans cet élément.</span><span class="sxs-lookup"><span data-stu-id="b2ec0-137">If the listener is defined in a [\<sharedListeners>](sharedlisteners-element.md), the filter for that listener must be defined in that element.</span></span>  
  
 <span data-ttu-id="b2ec0-138">Cet élément peut être utilisé dans le fichier de configuration de la machine (Machine.config) et le fichier de configuration d’application.</span><span class="sxs-lookup"><span data-stu-id="b2ec0-138">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b2ec0-139"> Exemple</span><span class="sxs-lookup"><span data-stu-id="b2ec0-139">Example</span></span>  
 <span data-ttu-id="b2ec0-140">L’exemple suivant montre `<filter>` comment utiliser l’élément pour `console` ajouter `Listeners` un filtre `myTraceSource`à l’auditeur dans `Error`la collection pour la source de trace , spécifiant le niveau d’événement de filtre comme .</span><span class="sxs-lookup"><span data-stu-id="b2ec0-140">The following example shows how to use the `<filter>` element to add a filter to the listener `console` in the `Listeners` collection for the trace source `myTraceSource`, specifying the filter event level as `Error`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b2ec0-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b2ec0-141">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceFilter>
- [<span data-ttu-id="b2ec0-142">Trace et Debug Paramètres Schema</span><span class="sxs-lookup"><span data-stu-id="b2ec0-142">Trace and Debug Settings Schema</span></span>](index.md)
