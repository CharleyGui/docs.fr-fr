---
title: <filter>, Élément de <add> pour<sharedListeners>
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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153451"
---
# <a name="filter-element-for-add-for-sharedlisteners"></a><span data-ttu-id="1022f-102">\<filter>, Élément de \<add> pour\<sharedListeners></span><span class="sxs-lookup"><span data-stu-id="1022f-102">\<filter> Element for \<add> for \<sharedListeners></span></span>
<span data-ttu-id="1022f-103">Ajoute un filtre à un écouteur dans la collection `sharedListeners`.</span><span class="sxs-lookup"><span data-stu-id="1022f-103">Adds a filter to a listener in the `sharedListeners` collection.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sharedListeners>**](sharedlisteners-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-sharedlisteners.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filter>**

## <a name="syntax"></a><span data-ttu-id="1022f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1022f-104">Syntax</span></span>  
  
```xml  
<filter type="System.Diagnostics.EventTypeFilter"
  initializeData="Warning" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1022f-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="1022f-105">Attributes and Elements</span></span>  
 <span data-ttu-id="1022f-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="1022f-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1022f-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="1022f-107">Attributes</span></span>  
  
|<span data-ttu-id="1022f-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="1022f-108">Attribute</span></span>|<span data-ttu-id="1022f-109">Description</span><span class="sxs-lookup"><span data-stu-id="1022f-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1022f-110">**type**</span><span class="sxs-lookup"><span data-stu-id="1022f-110">**type**</span></span>|<span data-ttu-id="1022f-111">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="1022f-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="1022f-112">Spécifie le type du filtre.</span><span class="sxs-lookup"><span data-stu-id="1022f-112">Specifies the type of the filter.</span></span> <span data-ttu-id="1022f-113">Vous pouvez utiliser uniquement le nom complet du type (au format de la <xref:System.Type.FullName%2A?displayProperty=nameWithType> propriété), ou vous pouvez utiliser le nom de type qualifié complet, y compris les informations de l’assembly (au format de la <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType> propriété).</span><span class="sxs-lookup"><span data-stu-id="1022f-113">You can use only the full name of the type (in the format of the <xref:System.Type.FullName%2A?displayProperty=nameWithType> property), or you can use the fully qualified type name including the assembly information (in the format of the <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType> property).</span></span> <span data-ttu-id="1022f-114">Pour plus d’informations sur la création d’un nom de type qualifié complet, consultez [spécification de noms de types qualifiés complets](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="1022f-114">For information on creating a fully qualified type name, see [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|<span data-ttu-id="1022f-115">**initializeData**</span><span class="sxs-lookup"><span data-stu-id="1022f-115">**initializeData**</span></span>|<span data-ttu-id="1022f-116">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="1022f-116">Optional attribute.</span></span><br /><br /> <span data-ttu-id="1022f-117">Chaîne passée au constructeur pour la classe spécifiée.</span><span class="sxs-lookup"><span data-stu-id="1022f-117">The string passed to the constructor for the specified class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1022f-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="1022f-118">Child Elements</span></span>  
 <span data-ttu-id="1022f-119">Aucun.</span><span class="sxs-lookup"><span data-stu-id="1022f-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1022f-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="1022f-120">Parent Elements</span></span>  
  
|<span data-ttu-id="1022f-121">Élément</span><span class="sxs-lookup"><span data-stu-id="1022f-121">Element</span></span>|<span data-ttu-id="1022f-122">Description</span><span class="sxs-lookup"><span data-stu-id="1022f-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="1022f-123">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1022f-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="1022f-124">Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.</span><span class="sxs-lookup"><span data-stu-id="1022f-124">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sharedListeners`|<span data-ttu-id="1022f-125">Collection d’écouteurs qui peut faire référence à n’importe quel élément source ou trace.</span><span class="sxs-lookup"><span data-stu-id="1022f-125">A collection of listeners that any source or trace element can reference.</span></span>|  
|`add`|<span data-ttu-id="1022f-126">Ajoute un écouteur à la collection **sharedListeners** .</span><span class="sxs-lookup"><span data-stu-id="1022f-126">Adds a listener to the **sharedListeners** collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1022f-127">Remarques</span><span class="sxs-lookup"><span data-stu-id="1022f-127">Remarks</span></span>  
 <span data-ttu-id="1022f-128">Si un écouteur est défini dans un `<add>` élément de l' `<sharedListeners>` élément, le filtre de cet écouteur doit être défini dans un `<filter>` élément qui est un enfant de l' `<add>` élément.</span><span class="sxs-lookup"><span data-stu-id="1022f-128">If a listener is defined in an `<add>` element of the `<sharedListeners>` element, the filter for that listener should be defined in a `<filter>` element that is a child of the `<add>` element.</span></span>  
  
 <span data-ttu-id="1022f-129">Cet élément peut être utilisé dans le fichier de configuration de l’ordinateur (machine. config) et dans le fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="1022f-129">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1022f-130">Exemple</span><span class="sxs-lookup"><span data-stu-id="1022f-130">Example</span></span>  
 <span data-ttu-id="1022f-131">L’exemple suivant montre comment utiliser l' `<filter>` élément pour ajouter un filtre à l’écouteur `console` de la trace dans la `sharedListeners` collection.</span><span class="sxs-lookup"><span data-stu-id="1022f-131">The following example shows how to use the `<filter>` element to add a filter to the trace listener `console` in the `sharedListeners` collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1022f-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1022f-132">See also</span></span>

- <xref:System.Diagnostics.TraceFilter>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="1022f-133">Schéma des paramètres de traçage et de débogage</span><span class="sxs-lookup"><span data-stu-id="1022f-133">Trace and Debug Settings Schema</span></span>](index.md)
