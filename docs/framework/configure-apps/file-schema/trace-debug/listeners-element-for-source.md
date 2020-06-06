---
title: Élément <listeners> pour <source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners
helpviewer_keywords:
- listeners element for <source>
- <listeners> element for <source>
ms.assetid: a2991f43-b4d3-4614-a8e7-da392de9697f
ms.openlocfilehash: 0eee325e01b41a15a19e4f40f479596f9d70f73b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153410"
---
# <a name="listeners-element-for-source"></a><span data-ttu-id="2fbe8-102">\<listeners>, élément de \<source></span><span class="sxs-lookup"><span data-stu-id="2fbe8-102">\<listeners> Element for \<source></span></span>
<span data-ttu-id="2fbe8-103">Ajoute ou supprime des écouteurs dans la <xref:System.Diagnostics.TraceSource.Listeners%2A> collection pour un <xref:System.Diagnostics.TraceSource> .</span><span class="sxs-lookup"><span data-stu-id="2fbe8-103">Adds or removes listeners in the <xref:System.Diagnostics.TraceSource.Listeners%2A> collection for a <xref:System.Diagnostics.TraceSource>.</span></span> <span data-ttu-id="2fbe8-104">Un écouteur dirige la sortie de suivi vers une cible appropriée, telle qu’un journal, une fenêtre ou un fichier texte.</span><span class="sxs-lookup"><span data-stu-id="2fbe8-104">A listener directs the tracing output to an appropriate target, such as a log, window, or text file.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<listeners>**  
  
## <a name="syntax"></a><span data-ttu-id="2fbe8-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2fbe8-105">Syntax</span></span>  
  
```xml  
<listeners>
  <add>...</add>  
  <remove ... />  
  <clear/>  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2fbe8-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="2fbe8-106">Attributes and Elements</span></span>  
 <span data-ttu-id="2fbe8-107">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="2fbe8-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2fbe8-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="2fbe8-108">Attributes</span></span>  
 <span data-ttu-id="2fbe8-109">Aucun.</span><span class="sxs-lookup"><span data-stu-id="2fbe8-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="2fbe8-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="2fbe8-110">Child Elements</span></span>  
  
|<span data-ttu-id="2fbe8-111">Élément</span><span class="sxs-lookup"><span data-stu-id="2fbe8-111">Element</span></span>|<span data-ttu-id="2fbe8-112">Description</span><span class="sxs-lookup"><span data-stu-id="2fbe8-112">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-element-for-listeners-for-source.md)|<span data-ttu-id="2fbe8-113">Ajoute un écouteur à la collection `Listeners`.</span><span class="sxs-lookup"><span data-stu-id="2fbe8-113">Adds a listener to the `Listeners` collection.</span></span>|  
|[\<remove>](remove-element-for-listeners-for-source.md)|<span data-ttu-id="2fbe8-114">Supprime un écouteur de la `Listeners` collection.</span><span class="sxs-lookup"><span data-stu-id="2fbe8-114">Removes a listener from the `Listeners` collection.</span></span>|  
|[\<clear>](clear-element-for-listeners-for-source.md)|<span data-ttu-id="2fbe8-115">Efface la collection `Listeners` pour une source de trace.</span><span class="sxs-lookup"><span data-stu-id="2fbe8-115">Clears the `Listeners` collection for a trace source.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2fbe8-116">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="2fbe8-116">Parent Elements</span></span>  
  
|<span data-ttu-id="2fbe8-117">Élément</span><span class="sxs-lookup"><span data-stu-id="2fbe8-117">Element</span></span>|<span data-ttu-id="2fbe8-118">Description</span><span class="sxs-lookup"><span data-stu-id="2fbe8-118">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="2fbe8-119">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2fbe8-119">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="2fbe8-120">Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.</span><span class="sxs-lookup"><span data-stu-id="2fbe8-120">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="2fbe8-121">Contient les sources de trace qui lancent des messages de traçage.</span><span class="sxs-lookup"><span data-stu-id="2fbe8-121">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="2fbe8-122">Spécifie une source de trace qui lance des messages de traçage.</span><span class="sxs-lookup"><span data-stu-id="2fbe8-122">Specifies a trace source that initiates tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2fbe8-123">Remarques</span><span class="sxs-lookup"><span data-stu-id="2fbe8-123">Remarks</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="2fbe8-124">Fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="2fbe8-124">Configuration File</span></span>  
 <span data-ttu-id="2fbe8-125">Cet élément peut être utilisé dans le fichier de configuration de l’ordinateur (machine. config) et dans le fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="2fbe8-125">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2fbe8-126">Exemple</span><span class="sxs-lookup"><span data-stu-id="2fbe8-126">Example</span></span>  
 <span data-ttu-id="2fbe8-127">L’exemple suivant montre comment utiliser l' `<listeners>` élément pour ajouter un écouteur de suivi de console à la `mySource` source et supprimer l’écouteur de suivi par défaut.</span><span class="sxs-lookup"><span data-stu-id="2fbe8-127">The following example shows how to use the `<listeners>` element to add a console trace listener to the `mySource` source and to remove the default trace listener.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="mySource" switchName="sourceSwitch"
        switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <add name="console"
            type="System.Diagnostics.ConsoleTraceListener">  
            <filter type="System.Diagnostics.EventTypeFilter"
              initializeData="Error"/>  
          </add>  
          <remove name="Default"/>  
        </listeners>  
      </source>  
    </sources>  
    <switches>  
      <add name="sourceSwitch" value="Warning"/>  
    </switches>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2fbe8-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2fbe8-128">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="2fbe8-129">Schéma des paramètres de traçage et de débogage</span><span class="sxs-lookup"><span data-stu-id="2fbe8-129">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="2fbe8-130">Écouteurs de suivi</span><span class="sxs-lookup"><span data-stu-id="2fbe8-130">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
