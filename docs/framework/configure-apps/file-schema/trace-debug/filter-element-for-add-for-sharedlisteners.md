---
title: <filter>Élément <add> pour pour<sharedListeners>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners/add/filter
helpviewer_keywords:
- filter element for <add> for <sharedListeners>
- initializeData attribute
- <filter> element for <add> for <sharedListeners>
- filters, trace listeners
- trace listeners, filters
ms.assetid: 7d4e7faa-2e4e-4379-ac76-f6cd7f2f8fac
ms.openlocfilehash: 6fb52cdfa5792ab6059b60d8dbb91c107cd666ca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153451"
---
# <a name="filter-element-for-add-for-sharedlisteners"></a><span data-ttu-id="91d85-102">\<filtrer> Element \<pour ajouter \<de la> pour les> d'></span><span class="sxs-lookup"><span data-stu-id="91d85-102">\<filter> Element for \<add> for \<sharedListeners></span></span>
<span data-ttu-id="91d85-103">Ajoute un filtre à un écouteur dans la collection `sharedListeners`.</span><span class="sxs-lookup"><span data-stu-id="91d85-103">Adds a filter to a listener in the `sharedListeners` collection.</span></span>  

<span data-ttu-id="91d85-104">[**\<configuration>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="91d85-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="91d85-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="91d85-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="91d85-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sharedListeners>**](sharedlisteners-element.md)</span><span class="sxs-lookup"><span data-stu-id="91d85-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sharedListeners>**](sharedlisteners-element.md)</span></span>\
<span data-ttu-id="91d85-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ajouter>**](add-element-for-sharedlisteners.md)</span><span class="sxs-lookup"><span data-stu-id="91d85-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-sharedlisteners.md)</span></span>\
<span data-ttu-id="91d85-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filtrer>**</span><span class="sxs-lookup"><span data-stu-id="91d85-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filter>**</span></span>

## <a name="syntax"></a><span data-ttu-id="91d85-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="91d85-109">Syntax</span></span>  
  
```xml  
<filter type="System.Diagnostics.EventTypeFilter"
  initializeData="Warning" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="91d85-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="91d85-110">Attributes and Elements</span></span>  
 <span data-ttu-id="91d85-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="91d85-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="91d85-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="91d85-112">Attributes</span></span>  
  
|<span data-ttu-id="91d85-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="91d85-113">Attribute</span></span>|<span data-ttu-id="91d85-114">Description</span><span class="sxs-lookup"><span data-stu-id="91d85-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="91d85-115">**type**</span><span class="sxs-lookup"><span data-stu-id="91d85-115">**type**</span></span>|<span data-ttu-id="91d85-116">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="91d85-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="91d85-117">Spécifie le type de filtre.</span><span class="sxs-lookup"><span data-stu-id="91d85-117">Specifies the type of the filter.</span></span> <span data-ttu-id="91d85-118">Vous ne pouvez utiliser que le nom complet <xref:System.Type.FullName%2A?displayProperty=nameWithType> du type (dans le format de la propriété), ou vous <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType> pouvez utiliser le nom de type entièrement qualifié, y compris les informations d’assemblage (dans le format de la propriété).</span><span class="sxs-lookup"><span data-stu-id="91d85-118">You can use only the full name of the type (in the format of the <xref:System.Type.FullName%2A?displayProperty=nameWithType> property), or you can use the fully qualified type name including the assembly information (in the format of the <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType> property).</span></span> <span data-ttu-id="91d85-119">Pour plus d’informations sur la création d’un nom de type entièrement qualifié, voir [Spécifier des noms de type entièrement qualifiés](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="91d85-119">For information on creating a fully qualified type name, see [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|<span data-ttu-id="91d85-120">**initialiserData**</span><span class="sxs-lookup"><span data-stu-id="91d85-120">**initializeData**</span></span>|<span data-ttu-id="91d85-121">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="91d85-121">Optional attribute.</span></span><br /><br /> <span data-ttu-id="91d85-122">La chaîne passa au constructeur pour la classe spécifiée.</span><span class="sxs-lookup"><span data-stu-id="91d85-122">The string passed to the constructor for the specified class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="91d85-123">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="91d85-123">Child Elements</span></span>  
 <span data-ttu-id="91d85-124">Aucun.</span><span class="sxs-lookup"><span data-stu-id="91d85-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="91d85-125">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="91d85-125">Parent Elements</span></span>  
  
|<span data-ttu-id="91d85-126">Élément</span><span class="sxs-lookup"><span data-stu-id="91d85-126">Element</span></span>|<span data-ttu-id="91d85-127">Description</span><span class="sxs-lookup"><span data-stu-id="91d85-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="91d85-128">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="91d85-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="91d85-129">Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.</span><span class="sxs-lookup"><span data-stu-id="91d85-129">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sharedListeners`|<span data-ttu-id="91d85-130">Une collection d’auditeurs que toute source ou élément de trace peut référencer.</span><span class="sxs-lookup"><span data-stu-id="91d85-130">A collection of listeners that any source or trace element can reference.</span></span>|  
|`add`|<span data-ttu-id="91d85-131">Ajoute un auditeur à la collection **sharedListeners.**</span><span class="sxs-lookup"><span data-stu-id="91d85-131">Adds a listener to the **sharedListeners** collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="91d85-132">Notes </span><span class="sxs-lookup"><span data-stu-id="91d85-132">Remarks</span></span>  
 <span data-ttu-id="91d85-133">Si un auditeur est `<add>` défini dans `<sharedListeners>` un élément de l’élément, le `<filter>` filtre de cet `<add>` auditeur doit être défini dans un élément qui est un enfant de l’élément.</span><span class="sxs-lookup"><span data-stu-id="91d85-133">If a listener is defined in an `<add>` element of the `<sharedListeners>` element, the filter for that listener should be defined in a `<filter>` element that is a child of the `<add>` element.</span></span>  
  
 <span data-ttu-id="91d85-134">Cet élément peut être utilisé dans le fichier de configuration de la machine (Machine.config) et le fichier de configuration d’application.</span><span class="sxs-lookup"><span data-stu-id="91d85-134">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="91d85-135"> Exemple</span><span class="sxs-lookup"><span data-stu-id="91d85-135">Example</span></span>  
 <span data-ttu-id="91d85-136">L’exemple suivant montre `<filter>` comment utiliser l’élément pour `console` ajouter `sharedListeners` un filtre à l’auditeur de traces de la collection.</span><span class="sxs-lookup"><span data-stu-id="91d85-136">The following example shows how to use the `<filter>` element to add a filter to the trace listener `console` in the `sharedListeners` collection.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="myTraceSource" >  
        <listeners>  
          <add name="console" />  
          <remove name="Default" />  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add name="console"
        type="System.Diagnostics.ConsoleTraceListener" >  
        <filter type="System.Diagnostics.EventTypeFilter"
          initializeData="Error" />  
      </add>  
    </sharedListeners>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="91d85-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="91d85-137">See also</span></span>

- <xref:System.Diagnostics.TraceFilter>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="91d85-138">Trace et Debug Paramètres Schema</span><span class="sxs-lookup"><span data-stu-id="91d85-138">Trace and Debug Settings Schema</span></span>](index.md)
