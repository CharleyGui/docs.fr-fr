---
title: <filter>, Élément <add> de pour<sharedListeners>
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
ms.openlocfilehash: 571a3add232f3e4f9747040dc104b85e8cc3085e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920507"
---
# <a name="filter-element-for-add-for-sharedlisteners"></a><span data-ttu-id="18685-102">\<élément de > de \<filtre pour l' \<ajout de > pour sharedListeners ></span><span class="sxs-lookup"><span data-stu-id="18685-102">\<filter> Element for \<add> for \<sharedListeners></span></span>
<span data-ttu-id="18685-103">Ajoute un filtre à un écouteur dans la collection `sharedListeners`.</span><span class="sxs-lookup"><span data-stu-id="18685-103">Adds a filter to a listener in the `sharedListeners` collection.</span></span>  
  
 <span data-ttu-id="18685-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="18685-104">\<configuration></span></span>  
<span data-ttu-id="18685-105">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="18685-105">\<system.diagnostics></span></span>  
<span data-ttu-id="18685-106">\<sharedListeners >, élément</span><span class="sxs-lookup"><span data-stu-id="18685-106">\<sharedListeners> Element</span></span>  
<span data-ttu-id="18685-107">\<add></span><span class="sxs-lookup"><span data-stu-id="18685-107">\<add></span></span>  
<span data-ttu-id="18685-108">\<filter></span><span class="sxs-lookup"><span data-stu-id="18685-108">\<filter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18685-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="18685-109">Syntax</span></span>  
  
```xml  
<filter type="System.Diagnostics.EventTypeFilter"   
  initializeData="Warning" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="18685-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="18685-110">Attributes and Elements</span></span>  
 <span data-ttu-id="18685-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="18685-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="18685-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="18685-112">Attributes</span></span>  
  
|<span data-ttu-id="18685-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="18685-113">Attribute</span></span>|<span data-ttu-id="18685-114">Description</span><span class="sxs-lookup"><span data-stu-id="18685-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="18685-115">**type**</span><span class="sxs-lookup"><span data-stu-id="18685-115">**type**</span></span>|<span data-ttu-id="18685-116">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="18685-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="18685-117">Spécifie le type du filtre.</span><span class="sxs-lookup"><span data-stu-id="18685-117">Specifies the type of the filter.</span></span> <span data-ttu-id="18685-118">Vous pouvez utiliser uniquement le nom complet du type (au format de la <xref:System.Type.FullName%2A?displayProperty=nameWithType> propriété), ou vous pouvez utiliser le nom de type qualifié complet, y compris les informations de l’assembly (au format de la <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType> propriété).</span><span class="sxs-lookup"><span data-stu-id="18685-118">You can use only the full name of the type (in the format of the <xref:System.Type.FullName%2A?displayProperty=nameWithType> property), or you can use the fully qualified type name including the assembly information (in the format of the <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType> property).</span></span> <span data-ttu-id="18685-119">Pour plus d’informations sur la création d’un nom de type qualifié complet, consultez [spécification de noms de types qualifiés complets](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="18685-119">For information on creating a fully qualified type name, see [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|<span data-ttu-id="18685-120">**initializeData**</span><span class="sxs-lookup"><span data-stu-id="18685-120">**initializeData**</span></span>|<span data-ttu-id="18685-121">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="18685-121">Optional attribute.</span></span><br /><br /> <span data-ttu-id="18685-122">Chaîne passée au constructeur pour la classe spécifiée.</span><span class="sxs-lookup"><span data-stu-id="18685-122">The string passed to the constructor for the specified class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="18685-123">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="18685-123">Child Elements</span></span>  
 <span data-ttu-id="18685-124">Aucun.</span><span class="sxs-lookup"><span data-stu-id="18685-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="18685-125">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="18685-125">Parent Elements</span></span>  
  
|<span data-ttu-id="18685-126">Élément</span><span class="sxs-lookup"><span data-stu-id="18685-126">Element</span></span>|<span data-ttu-id="18685-127">Description</span><span class="sxs-lookup"><span data-stu-id="18685-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="18685-128">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="18685-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="18685-129">Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.</span><span class="sxs-lookup"><span data-stu-id="18685-129">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sharedListeners`|<span data-ttu-id="18685-130">Collection d’écouteurs qui peut faire référence à n’importe quel élément source ou trace.</span><span class="sxs-lookup"><span data-stu-id="18685-130">A collection of listeners that any source or trace element can reference.</span></span>|  
|`add`|<span data-ttu-id="18685-131">Ajoute un écouteur à la collection **sharedListeners** .</span><span class="sxs-lookup"><span data-stu-id="18685-131">Adds a listener to the **sharedListeners** collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="18685-132">Notes</span><span class="sxs-lookup"><span data-stu-id="18685-132">Remarks</span></span>  
 <span data-ttu-id="18685-133">Si un écouteur est défini dans un `<add>` élément de l' `<sharedListeners>` élément, le filtre de cet écouteur doit être défini dans un `<filter>` élément qui est un enfant de l' `<add>` élément.</span><span class="sxs-lookup"><span data-stu-id="18685-133">If a listener is defined in an `<add>` element of the `<sharedListeners>` element, the filter for that listener should be defined in a `<filter>` element that is a child of the `<add>` element.</span></span>  
  
 <span data-ttu-id="18685-134">Cet élément peut être utilisé dans le fichier de configuration de l’ordinateur (machine. config) et dans le fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="18685-134">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="18685-135">Exemple</span><span class="sxs-lookup"><span data-stu-id="18685-135">Example</span></span>  
 <span data-ttu-id="18685-136">L’exemple suivant montre comment utiliser l' `<filter>` élément pour ajouter un filtre à l' `console` écouteur de la trace dans `sharedListeners` la collection.</span><span class="sxs-lookup"><span data-stu-id="18685-136">The following example shows how to use the `<filter>` element to add a filter to the trace listener `console` in the `sharedListeners` collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="18685-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="18685-137">See also</span></span>

- <xref:System.Diagnostics.TraceFilter>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="18685-138">Schéma des paramètres de trace et de débogage</span><span class="sxs-lookup"><span data-stu-id="18685-138">Trace and Debug Settings Schema</span></span>](index.md)
