---
title: <filter>Élément <add> pour <listeners> pour pour pour<trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- filter element for <add> for <listeners> for <trace>
- <filter> element for <add> for <listeners> for <trace>
ms.assetid: eb9c18f5-dfa8-47c5-b91b-e4b93e76e1cc
ms.openlocfilehash: b6c2c2bf7fe953a75f9d8129039ef33b4d8a3f56
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153464"
---
# <a name="filter-element-for-add-for-listeners-for-trace"></a><span data-ttu-id="ead51-102">\<filtrer> Element \<pour ajouter de \<la> pour \<les auditeurs> pour les traces></span><span class="sxs-lookup"><span data-stu-id="ead51-102">\<filter> Element for \<add> for \<listeners> for \<trace></span></span>
<span data-ttu-id="ead51-103">Ajoute un filtre à un `Listeners` auditeur de la collection pour une trace.</span><span class="sxs-lookup"><span data-stu-id="ead51-103">Adds a filter to a listener in the `Listeners` collection for a trace.</span></span>  

<span data-ttu-id="ead51-104">[**\<configuration>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ead51-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ead51-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="ead51-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="ead51-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)</span><span class="sxs-lookup"><span data-stu-id="ead51-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)</span></span>\
<span data-ttu-id="ead51-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<auditeurs>**](listeners-element-for-trace.md)</span><span class="sxs-lookup"><span data-stu-id="ead51-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-trace.md)</span></span>\
<span data-ttu-id="ead51-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ajouter>**](add-element-for-listeners-for-trace.md)</span><span class="sxs-lookup"><span data-stu-id="ead51-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-listeners-for-trace.md)</span></span>\
<span data-ttu-id="ead51-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filtrer>**</span><span class="sxs-lookup"><span data-stu-id="ead51-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filter>**</span></span>

## <a name="syntax"></a><span data-ttu-id="ead51-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ead51-110">Syntax</span></span>  
  
```xml  
<filter
  type="traceFilterClassName"
  initializeData="data" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ead51-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="ead51-111">Attributes and Elements</span></span>  
 <span data-ttu-id="ead51-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="ead51-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ead51-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="ead51-113">Attributes</span></span>  
  
|<span data-ttu-id="ead51-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="ead51-114">Attribute</span></span>|<span data-ttu-id="ead51-115">Description</span><span class="sxs-lookup"><span data-stu-id="ead51-115">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="ead51-116">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="ead51-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="ead51-117">Spécifie le type de filtre, <xref:System.Diagnostics.TraceFilter> qui devrait hériter de la classe.</span><span class="sxs-lookup"><span data-stu-id="ead51-117">Specifies the type of the filter, which should inherit from the <xref:System.Diagnostics.TraceFilter> class.</span></span> <span data-ttu-id="ead51-118">Vous pouvez utiliser le nom du type, qui correspond à <xref:System.Type.FullName%2A> la propriété du type, ou vous pouvez utiliser le nom <xref:System.Type.AssemblyQualifiedName%2A> de type entièrement qualifié, y compris les informations d’assemblage, qui correspond à la propriété.</span><span class="sxs-lookup"><span data-stu-id="ead51-118">You can use the namespace-qualified name of the type, which corresponds to the type's <xref:System.Type.FullName%2A> property, or you can use the fully qualified type name including the assembly information, which corresponds to the <xref:System.Type.AssemblyQualifiedName%2A> property.</span></span> <span data-ttu-id="ead51-119">Pour plus d’informations sur les noms de type entièrement qualifiés, voir [spécifier des noms de type entièrement qualifiés](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="ead51-119">For information about fully qualified type names, see [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="ead51-120">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="ead51-120">Optional attribute.</span></span><br /><br /> <span data-ttu-id="ead51-121">La chaîne est passée au constructeur pour la classe de filtre spécifiée.</span><span class="sxs-lookup"><span data-stu-id="ead51-121">The string passed to the constructor for the specified filter class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ead51-122">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="ead51-122">Child Elements</span></span>  
 <span data-ttu-id="ead51-123">Aucun.</span><span class="sxs-lookup"><span data-stu-id="ead51-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ead51-124">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="ead51-124">Parent Elements</span></span>  
  
|<span data-ttu-id="ead51-125">Élément</span><span class="sxs-lookup"><span data-stu-id="ead51-125">Element</span></span>|<span data-ttu-id="ead51-126">Description</span><span class="sxs-lookup"><span data-stu-id="ead51-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="ead51-127">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ead51-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="ead51-128">Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.</span><span class="sxs-lookup"><span data-stu-id="ead51-128">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="ead51-129">Contient les écouteurs qui collectent, stockent et acheminent les messages de traçage.</span><span class="sxs-lookup"><span data-stu-id="ead51-129">Contains listeners that collect, store, and route tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="ead51-130">Contient des auditeurs qui recueillent, stockent et acheminent des messages.</span><span class="sxs-lookup"><span data-stu-id="ead51-130">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="ead51-131">Les auditeurs dirigent la sortie de traçage vers une cible appropriée.</span><span class="sxs-lookup"><span data-stu-id="ead51-131">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`add`|<span data-ttu-id="ead51-132">Ajoute un écouteur à la collection `Listeners`.</span><span class="sxs-lookup"><span data-stu-id="ead51-132">Adds a listener to the `Listeners` collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ead51-133">Notes </span><span class="sxs-lookup"><span data-stu-id="ead51-133">Remarks</span></span>  
 <span data-ttu-id="ead51-134">L’élément `<filter>` doit être `<add>` contenu dans un élément pour un auditeur de trace qui spécifie le type de l’auditeur, et pas seulement le nom d’un auditeur défini dans un [ \<>d’écoutes partagées ](sharedlisteners-element.md).</span><span class="sxs-lookup"><span data-stu-id="ead51-134">The `<filter>` element must be contained in an `<add>` element for a trace listener that specifies the type of the listener, not just the name of a listener defined in a [\<sharedListeners>](sharedlisteners-element.md).</span></span> <span data-ttu-id="ead51-135">Si l’auditeur est défini dans un [ \<>d’écoute partagé, ](sharedlisteners-element.md)le filtre de cet auditeur doit être défini dans cet élément.</span><span class="sxs-lookup"><span data-stu-id="ead51-135">If the listener is defined in a [\<sharedListeners>](sharedlisteners-element.md), the filter for that listener must be defined in that element.</span></span>  
  
 <span data-ttu-id="ead51-136">Cet élément peut être utilisé dans le fichier de configuration de la machine (Machine.config) et le fichier de configuration d’application.</span><span class="sxs-lookup"><span data-stu-id="ead51-136">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ead51-137"> Exemple</span><span class="sxs-lookup"><span data-stu-id="ead51-137">Example</span></span>  
 <span data-ttu-id="ead51-138">L’exemple suivant montre `<filter>` comment utiliser l’élément pour `console` ajouter `Listeners` un filtre à l’auditeur `Error`de la collection pour la trace, en spécifiant le niveau d’événement de filtre comme .</span><span class="sxs-lookup"><span data-stu-id="ead51-138">The following example shows how to use the `<filter>` element to add a filter to the listener `console` in the `Listeners` collection for trace, specifying the filter event level as `Error`.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <trace autoflush="false" indentsize="4">  
      <listeners>  
        <add name="console"
          type="System.Diagnostics.ConsoleTraceListener" >  
          <filter type="System.Diagnostics.EventTypeFilter"
            initializeData="Error" />  
        </add>  
        <remove name="Default" />  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ead51-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ead51-139">See also</span></span>

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceFilter>
- [<span data-ttu-id="ead51-140">Trace et Debug Paramètres Schema</span><span class="sxs-lookup"><span data-stu-id="ead51-140">Trace and Debug Settings Schema</span></span>](index.md)
