---
title: <filter>, élément de <add> pour <sharedListeners>
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
ms.openlocfilehash: e04ecd773bd6aa7791858711edbd72128dc391ea
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088879"
---
# <a name="filter-element-for-add-for-sharedlisteners"></a><span data-ttu-id="f1891-102">\<> un élément de filtre pour \<> d’ajout pour \<sharedListeners ></span><span class="sxs-lookup"><span data-stu-id="f1891-102">\<filter> Element for \<add> for \<sharedListeners></span></span>
<span data-ttu-id="f1891-103">Ajoute un filtre à un écouteur dans la collection `sharedListeners`.</span><span class="sxs-lookup"><span data-stu-id="f1891-103">Adds a filter to a listener in the `sharedListeners` collection.</span></span>  

<span data-ttu-id="f1891-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f1891-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f1891-105">&nbsp;&nbsp;[ **\<System. diagnostics >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="f1891-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="f1891-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<sharedListeners**](sharedlisteners-element.md) ></span><span class="sxs-lookup"><span data-stu-id="f1891-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sharedListeners>**](sharedlisteners-element.md)</span></span>\
<span data-ttu-id="f1891-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**Ajouter**](add-element-for-sharedlisteners.md) ></span><span class="sxs-lookup"><span data-stu-id="f1891-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-sharedlisteners.md)</span></span>\
<span data-ttu-id="f1891-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **&nbsp;&nbsp;\<** ></span><span class="sxs-lookup"><span data-stu-id="f1891-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filter>**</span></span>

## <a name="syntax"></a><span data-ttu-id="f1891-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f1891-109">Syntax</span></span>  
  
```xml  
<filter type="System.Diagnostics.EventTypeFilter"   
  initializeData="Warning" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f1891-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="f1891-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f1891-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="f1891-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f1891-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="f1891-112">Attributes</span></span>  
  
|<span data-ttu-id="f1891-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="f1891-113">Attribute</span></span>|<span data-ttu-id="f1891-114">Description</span><span class="sxs-lookup"><span data-stu-id="f1891-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f1891-115">**type**</span><span class="sxs-lookup"><span data-stu-id="f1891-115">**type**</span></span>|<span data-ttu-id="f1891-116">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="f1891-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="f1891-117">Spécifie le type du filtre.</span><span class="sxs-lookup"><span data-stu-id="f1891-117">Specifies the type of the filter.</span></span> <span data-ttu-id="f1891-118">Vous pouvez utiliser uniquement le nom complet du type (au format de la propriété <xref:System.Type.FullName%2A?displayProperty=nameWithType>), ou vous pouvez utiliser le nom de type qualifié complet, y compris les informations de l’assembly (au format de la propriété <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="f1891-118">You can use only the full name of the type (in the format of the <xref:System.Type.FullName%2A?displayProperty=nameWithType> property), or you can use the fully qualified type name including the assembly information (in the format of the <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType> property).</span></span> <span data-ttu-id="f1891-119">Pour plus d’informations sur la création d’un nom de type qualifié complet, consultez [spécification de noms de types qualifiés complets](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="f1891-119">For information on creating a fully qualified type name, see [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|<span data-ttu-id="f1891-120">**initializeData**</span><span class="sxs-lookup"><span data-stu-id="f1891-120">**initializeData**</span></span>|<span data-ttu-id="f1891-121">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="f1891-121">Optional attribute.</span></span><br /><br /> <span data-ttu-id="f1891-122">Chaîne passée au constructeur pour la classe spécifiée.</span><span class="sxs-lookup"><span data-stu-id="f1891-122">The string passed to the constructor for the specified class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f1891-123">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="f1891-123">Child Elements</span></span>  
 <span data-ttu-id="f1891-124">Aucun(e).</span><span class="sxs-lookup"><span data-stu-id="f1891-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f1891-125">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="f1891-125">Parent Elements</span></span>  
  
|<span data-ttu-id="f1891-126">Élément</span><span class="sxs-lookup"><span data-stu-id="f1891-126">Element</span></span>|<span data-ttu-id="f1891-127">Description</span><span class="sxs-lookup"><span data-stu-id="f1891-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="f1891-128">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f1891-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="f1891-129">Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.</span><span class="sxs-lookup"><span data-stu-id="f1891-129">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sharedListeners`|<span data-ttu-id="f1891-130">Collection d’écouteurs qui peut faire référence à n’importe quel élément source ou trace.</span><span class="sxs-lookup"><span data-stu-id="f1891-130">A collection of listeners that any source or trace element can reference.</span></span>|  
|`add`|<span data-ttu-id="f1891-131">Ajoute un écouteur à la collection **sharedListeners** .</span><span class="sxs-lookup"><span data-stu-id="f1891-131">Adds a listener to the **sharedListeners** collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f1891-132">Notes</span><span class="sxs-lookup"><span data-stu-id="f1891-132">Remarks</span></span>  
 <span data-ttu-id="f1891-133">Si un écouteur est défini dans un élément `<add>` de l’élément `<sharedListeners>`, le filtre de cet écouteur doit être défini dans un élément `<filter>` qui est un enfant de l’élément `<add>`.</span><span class="sxs-lookup"><span data-stu-id="f1891-133">If a listener is defined in an `<add>` element of the `<sharedListeners>` element, the filter for that listener should be defined in a `<filter>` element that is a child of the `<add>` element.</span></span>  
  
 <span data-ttu-id="f1891-134">Cet élément peut être utilisé dans le fichier de configuration de l’ordinateur (machine. config) et dans le fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="f1891-134">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f1891-135">Exemple</span><span class="sxs-lookup"><span data-stu-id="f1891-135">Example</span></span>  
 <span data-ttu-id="f1891-136">L’exemple suivant montre comment utiliser l’élément `<filter>` pour ajouter un filtre à l’écouteur de la trace `console` dans la collection de `sharedListeners`.</span><span class="sxs-lookup"><span data-stu-id="f1891-136">The following example shows how to use the `<filter>` element to add a filter to the trace listener `console` in the `sharedListeners` collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f1891-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f1891-137">See also</span></span>

- <xref:System.Diagnostics.TraceFilter>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="f1891-138">Schéma des paramètres de trace et de débogage</span><span class="sxs-lookup"><span data-stu-id="f1891-138">Trace and Debug Settings Schema</span></span>](index.md)
