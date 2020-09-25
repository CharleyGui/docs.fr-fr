---
title: <filter>, Élément <add> de pour pour <listeners><trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- filter element for <add> for <listeners> for <trace>
- <filter> element for <add> for <listeners> for <trace>
ms.assetid: eb9c18f5-dfa8-47c5-b91b-e4b93e76e1cc
ms.openlocfilehash: d856fc742bc2dca51095ce0866dcbfdaadadf64d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91176108"
---
# <a name="filter-element-for-add-for-listeners-for-trace"></a><span data-ttu-id="2ea63-102">\<filter>, Élément \<add> de pour pour \<listeners>\<trace></span><span class="sxs-lookup"><span data-stu-id="2ea63-102">\<filter> Element for \<add> for \<listeners> for \<trace></span></span>

<span data-ttu-id="2ea63-103">Ajoute un filtre à un écouteur dans la `Listeners` collection pour une trace.</span><span class="sxs-lookup"><span data-stu-id="2ea63-103">Adds a filter to a listener in the `Listeners` collection for a trace.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-trace.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-listeners-for-trace.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filter>**

## <a name="syntax"></a><span data-ttu-id="2ea63-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2ea63-104">Syntax</span></span>  
  
```xml  
<filter
  type="traceFilterClassName"
  initializeData="data" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2ea63-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="2ea63-105">Attributes and Elements</span></span>  

 <span data-ttu-id="2ea63-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="2ea63-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2ea63-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="2ea63-107">Attributes</span></span>  
  
|<span data-ttu-id="2ea63-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="2ea63-108">Attribute</span></span>|<span data-ttu-id="2ea63-109">Description</span><span class="sxs-lookup"><span data-stu-id="2ea63-109">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="2ea63-110">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="2ea63-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="2ea63-111">Spécifie le type du filtre, qui doit hériter de la <xref:System.Diagnostics.TraceFilter> classe.</span><span class="sxs-lookup"><span data-stu-id="2ea63-111">Specifies the type of the filter, which should inherit from the <xref:System.Diagnostics.TraceFilter> class.</span></span> <span data-ttu-id="2ea63-112">Vous pouvez utiliser le nom qualifié par un espace de noms du type, qui correspond à la <xref:System.Type.FullName%2A> propriété du type, ou vous pouvez utiliser le nom de type qualifié complet, y compris les informations de l’assembly, qui correspond à la <xref:System.Type.AssemblyQualifiedName%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="2ea63-112">You can use the namespace-qualified name of the type, which corresponds to the type's <xref:System.Type.FullName%2A> property, or you can use the fully qualified type name including the assembly information, which corresponds to the <xref:System.Type.AssemblyQualifiedName%2A> property.</span></span> <span data-ttu-id="2ea63-113">Pour plus d’informations sur les noms de types qualifiés complets, consultez [spécification de noms de types qualifiés complets](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="2ea63-113">For information about fully qualified type names, see [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="2ea63-114">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="2ea63-114">Optional attribute.</span></span><br /><br /> <span data-ttu-id="2ea63-115">Chaîne passée au constructeur pour la classe de filtre spécifiée.</span><span class="sxs-lookup"><span data-stu-id="2ea63-115">The string passed to the constructor for the specified filter class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2ea63-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="2ea63-116">Child Elements</span></span>  

 <span data-ttu-id="2ea63-117">Aucun.</span><span class="sxs-lookup"><span data-stu-id="2ea63-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2ea63-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="2ea63-118">Parent Elements</span></span>  
  
|<span data-ttu-id="2ea63-119">Élément</span><span class="sxs-lookup"><span data-stu-id="2ea63-119">Element</span></span>|<span data-ttu-id="2ea63-120">Description</span><span class="sxs-lookup"><span data-stu-id="2ea63-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="2ea63-121">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2ea63-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="2ea63-122">Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.</span><span class="sxs-lookup"><span data-stu-id="2ea63-122">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="2ea63-123">Contient les écouteurs qui collectent, stockent et acheminent les messages de traçage.</span><span class="sxs-lookup"><span data-stu-id="2ea63-123">Contains listeners that collect, store, and route tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="2ea63-124">Contient des écouteurs qui collectent, stockent et acheminent des messages.</span><span class="sxs-lookup"><span data-stu-id="2ea63-124">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="2ea63-125">Les écouteurs dirigent la sortie de suivi vers une cible appropriée.</span><span class="sxs-lookup"><span data-stu-id="2ea63-125">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`add`|<span data-ttu-id="2ea63-126">Ajoute un écouteur à la collection `Listeners`.</span><span class="sxs-lookup"><span data-stu-id="2ea63-126">Adds a listener to the `Listeners` collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2ea63-127">Notes</span><span class="sxs-lookup"><span data-stu-id="2ea63-127">Remarks</span></span>  

 <span data-ttu-id="2ea63-128">L' `<filter>` élément doit être contenu dans un `<add>` élément pour un écouteur de trace qui spécifie le type de l’écouteur, pas seulement le nom d’un écouteur défini dans un [\<sharedListeners>](sharedlisteners-element.md) .</span><span class="sxs-lookup"><span data-stu-id="2ea63-128">The `<filter>` element must be contained in an `<add>` element for a trace listener that specifies the type of the listener, not just the name of a listener defined in a [\<sharedListeners>](sharedlisteners-element.md).</span></span> <span data-ttu-id="2ea63-129">Si l’écouteur est défini dans un [\<sharedListeners>](sharedlisteners-element.md) , le filtre de cet écouteur doit être défini dans cet élément.</span><span class="sxs-lookup"><span data-stu-id="2ea63-129">If the listener is defined in a [\<sharedListeners>](sharedlisteners-element.md), the filter for that listener must be defined in that element.</span></span>  
  
 <span data-ttu-id="2ea63-130">Cet élément peut être utilisé dans le fichier de configuration de l’ordinateur (Machine.config) et dans le fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="2ea63-130">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2ea63-131">Exemple</span><span class="sxs-lookup"><span data-stu-id="2ea63-131">Example</span></span>  

 <span data-ttu-id="2ea63-132">L’exemple suivant montre comment utiliser l' `<filter>` élément pour ajouter un filtre à l’écouteur `console` dans la `Listeners` collection pour la trace, en spécifiant le niveau d’événement de filtre en tant que `Error` .</span><span class="sxs-lookup"><span data-stu-id="2ea63-132">The following example shows how to use the `<filter>` element to add a filter to the listener `console` in the `Listeners` collection for trace, specifying the filter event level as `Error`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2ea63-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2ea63-133">See also</span></span>

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceFilter>
- [<span data-ttu-id="2ea63-134">Schéma des paramètres de traçage et de débogage</span><span class="sxs-lookup"><span data-stu-id="2ea63-134">Trace and Debug Settings Schema</span></span>](index.md)
