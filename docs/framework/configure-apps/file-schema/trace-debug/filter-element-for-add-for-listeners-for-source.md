---
title: <filter>, Élément <add> de pour pour <listeners><source>
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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153514"
---
# <a name="filter-element-for-add-for-listeners-for-source"></a><span data-ttu-id="cf737-102">\<filter>, Élément \<add> de pour pour \<listeners>\<source></span><span class="sxs-lookup"><span data-stu-id="cf737-102">\<filter> Element for \<add> for \<listeners> for \<source></span></span>
<span data-ttu-id="cf737-103">Ajoute un filtre à un écouteur dans la collection `Listeners` pour une source de trace.</span><span class="sxs-lookup"><span data-stu-id="cf737-103">Adds a filter to a listener in the `Listeners` collection for a trace source.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-source.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-listeners-for-source.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filter>**

## <a name="syntax"></a><span data-ttu-id="cf737-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cf737-104">Syntax</span></span>  
  
```xml  
<filter
  type="traceFilterClassName"
  initializeData="data" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cf737-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="cf737-105">Attributes and Elements</span></span>  
 <span data-ttu-id="cf737-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="cf737-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cf737-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="cf737-107">Attributes</span></span>  
  
|<span data-ttu-id="cf737-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="cf737-108">Attribute</span></span>|<span data-ttu-id="cf737-109">Description</span><span class="sxs-lookup"><span data-stu-id="cf737-109">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="cf737-110">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="cf737-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="cf737-111">Spécifie le type du filtre, qui doit hériter de la <xref:System.Diagnostics.TraceFilter> classe.</span><span class="sxs-lookup"><span data-stu-id="cf737-111">Specifies the type of the filter, which should inherit from the <xref:System.Diagnostics.TraceFilter> class.</span></span> <span data-ttu-id="cf737-112">Vous pouvez utiliser le nom qualifié par un espace de noms du type, qui correspond à la <xref:System.Type.FullName%2A> propriété du type, ou vous pouvez utiliser le nom de type qualifié complet, y compris les informations de l’assembly, qui correspond à la <xref:System.Type.AssemblyQualifiedName%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="cf737-112">You can use the namespace-qualified name of the type, which corresponds to the type's <xref:System.Type.FullName%2A> property, or you can use the fully qualified type name including the assembly information, which corresponds to the <xref:System.Type.AssemblyQualifiedName%2A> property.</span></span> <span data-ttu-id="cf737-113">Pour plus d’informations sur les noms de types qualifiés complets, consultez [spécification de noms de types qualifiés complets](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="cf737-113">For information about fully qualified type names, see [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="cf737-114">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="cf737-114">Optional attribute.</span></span><br /><br /> <span data-ttu-id="cf737-115">Chaîne passée au constructeur pour la classe de filtre spécifiée.</span><span class="sxs-lookup"><span data-stu-id="cf737-115">The string passed to the constructor for the specified filter class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cf737-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="cf737-116">Child Elements</span></span>  
 <span data-ttu-id="cf737-117">Aucun.</span><span class="sxs-lookup"><span data-stu-id="cf737-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cf737-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="cf737-118">Parent Elements</span></span>  
  
|<span data-ttu-id="cf737-119">Élément</span><span class="sxs-lookup"><span data-stu-id="cf737-119">Element</span></span>|<span data-ttu-id="cf737-120">Description</span><span class="sxs-lookup"><span data-stu-id="cf737-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="cf737-121">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cf737-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="cf737-122">Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.</span><span class="sxs-lookup"><span data-stu-id="cf737-122">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="cf737-123">Contient les sources de trace qui lancent des messages de traçage.</span><span class="sxs-lookup"><span data-stu-id="cf737-123">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="cf737-124">Spécifie une source de trace qui lance des messages de traçage.</span><span class="sxs-lookup"><span data-stu-id="cf737-124">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="cf737-125">Contient des écouteurs qui collectent, stockent et acheminent des messages.</span><span class="sxs-lookup"><span data-stu-id="cf737-125">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="cf737-126">Les écouteurs dirigent la sortie de suivi vers une cible appropriée.</span><span class="sxs-lookup"><span data-stu-id="cf737-126">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`add`|<span data-ttu-id="cf737-127">Ajoute un écouteur à la collection `Listeners` pour une source de trace.</span><span class="sxs-lookup"><span data-stu-id="cf737-127">Adds a listener to the `Listeners` collection for a trace source.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cf737-128">Remarques</span><span class="sxs-lookup"><span data-stu-id="cf737-128">Remarks</span></span>  
 <span data-ttu-id="cf737-129">L' `<filter>` élément doit être contenu dans un `<add>` élément pour un écouteur de source de suivi qui spécifie le type de l’écouteur, pas seulement le nom d’un écouteur défini dans un [\<sharedListeners>](sharedlisteners-element.md) .</span><span class="sxs-lookup"><span data-stu-id="cf737-129">The `<filter>` element must be contained in an `<add>` element for a trace source listener that specifies the type of the listener, not just the name of a listener defined in a [\<sharedListeners>](sharedlisteners-element.md).</span></span> <span data-ttu-id="cf737-130">Si l’écouteur est défini dans un [\<sharedListeners>](sharedlisteners-element.md) , le filtre de cet écouteur doit être défini dans cet élément.</span><span class="sxs-lookup"><span data-stu-id="cf737-130">If the listener is defined in a [\<sharedListeners>](sharedlisteners-element.md), the filter for that listener must be defined in that element.</span></span>  
  
 <span data-ttu-id="cf737-131">Cet élément peut être utilisé dans le fichier de configuration de l’ordinateur (machine. config) et dans le fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="cf737-131">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cf737-132">Exemple</span><span class="sxs-lookup"><span data-stu-id="cf737-132">Example</span></span>  
 <span data-ttu-id="cf737-133">L’exemple suivant montre comment utiliser l' `<filter>` élément pour ajouter un filtre à l’écouteur `console` dans la `Listeners` collection pour la source de suivi `myTraceSource` , en spécifiant le niveau d’événement de filtre en tant que `Error` .</span><span class="sxs-lookup"><span data-stu-id="cf737-133">The following example shows how to use the `<filter>` element to add a filter to the listener `console` in the `Listeners` collection for the trace source `myTraceSource`, specifying the filter event level as `Error`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cf737-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cf737-134">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceFilter>
- [<span data-ttu-id="cf737-135">Schéma des paramètres de traçage et de débogage</span><span class="sxs-lookup"><span data-stu-id="cf737-135">Trace and Debug Settings Schema</span></span>](index.md)
