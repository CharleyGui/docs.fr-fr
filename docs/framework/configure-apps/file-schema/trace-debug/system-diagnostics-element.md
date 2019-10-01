---
title: < l’élément System. Diagnostics >
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.diagnostics
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics
helpviewer_keywords:
- <system.diagnostics> element
- system.diagnostics element
ms.assetid: 3f348f42-fa72-4ff2-aa1c-bb9eecad4bb2
ms.openlocfilehash: dc05c46cb1ba74baceaaeadc2959a6889faf19c9
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699195"
---
# <a name="systemdiagnostics-element"></a><span data-ttu-id="cbe86-102">Élément \<System. Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="cbe86-102">\<system.diagnostics> Element</span></span>
<span data-ttu-id="cbe86-103">Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.</span><span class="sxs-lookup"><span data-stu-id="cbe86-103">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>  
  
[<span data-ttu-id="cbe86-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="cbe86-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="cbe86-105">&nbsp; @ no__t-1 **\<Système. diagnostics >**</span><span class="sxs-lookup"><span data-stu-id="cbe86-105">&nbsp;&nbsp;**\<system.diagnostics>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cbe86-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cbe86-106">Syntax</span></span>  
  
```xml  
<system.diagnostics>   
</system.diagnostics>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cbe86-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="cbe86-107">Attributes and Elements</span></span>  
 <span data-ttu-id="cbe86-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="cbe86-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cbe86-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="cbe86-109">Attributes</span></span>  
 <span data-ttu-id="cbe86-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="cbe86-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="cbe86-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="cbe86-111">Child Elements</span></span>  
  
|<span data-ttu-id="cbe86-112">Élément</span><span class="sxs-lookup"><span data-stu-id="cbe86-112">Element</span></span>|<span data-ttu-id="cbe86-113">Description</span><span class="sxs-lookup"><span data-stu-id="cbe86-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cbe86-114">\<assert></span><span class="sxs-lookup"><span data-stu-id="cbe86-114">\<assert></span></span>](assert-element.md)|<span data-ttu-id="cbe86-115">Indique si une boîte de message doit s’afficher quand vous appelez la méthode <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> ; spécifie également le nom du fichier dans lequel écrire les messages.</span><span class="sxs-lookup"><span data-stu-id="cbe86-115">Specifies whether to display a message box when you call the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> method; also specifies the name of the file to write messages to.</span></span>|  
|[<span data-ttu-id="cbe86-116">\<performanceCounters></span><span class="sxs-lookup"><span data-stu-id="cbe86-116">\<performanceCounters></span></span>](performancecounters-element.md)|<span data-ttu-id="cbe86-117">Spécifie la taille de la mémoire globale partagée par les compteurs de performances.</span><span class="sxs-lookup"><span data-stu-id="cbe86-117">Specifies the size of the global memory shared by performance counters.</span></span>|  
|[<span data-ttu-id="cbe86-118">\<sharedListeners></span><span class="sxs-lookup"><span data-stu-id="cbe86-118">\<sharedListeners></span></span>](sharedlisteners-element.md)|<span data-ttu-id="cbe86-119">Contient des écouteurs auxquels toute source ou tout élément de trace peuvent faire référence.</span><span class="sxs-lookup"><span data-stu-id="cbe86-119">Contains listeners that any source or trace element can reference.</span></span> <span data-ttu-id="cbe86-120">Les écouteurs identifiés comme écouteurs partagés peuvent être ajoutés à des sources ou des suivis par nom.</span><span class="sxs-lookup"><span data-stu-id="cbe86-120">Listeners identified as shared listeners can be added to sources or traces by name.</span></span>|  
|[<span data-ttu-id="cbe86-121">\<sources></span><span class="sxs-lookup"><span data-stu-id="cbe86-121">\<sources></span></span>](sources-element.md)|<span data-ttu-id="cbe86-122">Spécifie les sources de suivi qui initialisent les messages de suivi.</span><span class="sxs-lookup"><span data-stu-id="cbe86-122">Specifies trace sources that initiate tracing messages.</span></span>|  
|[<span data-ttu-id="cbe86-123">\<switches></span><span class="sxs-lookup"><span data-stu-id="cbe86-123">\<switches></span></span>](switches-element.md)|<span data-ttu-id="cbe86-124">Contient des commutateurs de trace et les niveaux où les commutateurs de trace sont définis.</span><span class="sxs-lookup"><span data-stu-id="cbe86-124">Contains trace switches and the levels where the trace switches are set.</span></span>|  
|[<span data-ttu-id="cbe86-125">\<trace></span><span class="sxs-lookup"><span data-stu-id="cbe86-125">\<trace></span></span>](trace-element.md)|<span data-ttu-id="cbe86-126">Contient les écouteurs qui collectent, stockent et acheminent les messages de traçage.</span><span class="sxs-lookup"><span data-stu-id="cbe86-126">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cbe86-127">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="cbe86-127">Parent Elements</span></span>  
  
|<span data-ttu-id="cbe86-128">Élément</span><span class="sxs-lookup"><span data-stu-id="cbe86-128">Element</span></span>|<span data-ttu-id="cbe86-129">Description</span><span class="sxs-lookup"><span data-stu-id="cbe86-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="cbe86-130">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cbe86-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="cbe86-131">Exemple</span><span class="sxs-lookup"><span data-stu-id="cbe86-131">Example</span></span>  
 <span data-ttu-id="cbe86-132">L’exemple suivant montre comment incorporer un commutateur de trace et un écouteur de trace à l’intérieur de l’élément **\<Système. diagnostics >** .</span><span class="sxs-lookup"><span data-stu-id="cbe86-132">The following example shows how to embed a trace switch and a trace listener inside the **\<system.diagnostics>** element.</span></span> <span data-ttu-id="cbe86-133">Le commutateur de trace `General` est défini sur le niveau <xref:System.Diagnostics.TraceLevel>.</span><span class="sxs-lookup"><span data-stu-id="cbe86-133">The `General` trace switch is set to the <xref:System.Diagnostics.TraceLevel> level.</span></span> <span data-ttu-id="cbe86-134">L’écouteur de suivi `myListener` crée un fichier nommé `MyListener.log` et écrit la sortie dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="cbe86-134">The trace listener `myListener` creates a file called `MyListener.log` and writes the output to the file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cbe86-135">Dans .NET Framework 2.0, vous pouvez spécifier la valeur d'un commutateur avec du texte.</span><span class="sxs-lookup"><span data-stu-id="cbe86-135">In the .NET Framework version 2.0, you can use text to specify the value for a switch.</span></span> <span data-ttu-id="cbe86-136">Par exemple, vous pouvez spécifier `true` pour une <xref:System.Diagnostics.BooleanSwitch> ou utiliser le texte représentant une valeur d’énumération telle que `Error` pour une <xref:System.Diagnostics.TraceSwitch>.</span><span class="sxs-lookup"><span data-stu-id="cbe86-136">For example, you can specify `true` for a <xref:System.Diagnostics.BooleanSwitch> or use the text representing an enumeration value such as `Error` for a <xref:System.Diagnostics.TraceSwitch>.</span></span> <span data-ttu-id="cbe86-137">La ligne `<add name="myTraceSwitch" value="Error" />` équivaut à `<add name="myTraceSwitch" value="1" />`.</span><span class="sxs-lookup"><span data-stu-id="cbe86-137">The line `<add name="myTraceSwitch" value="Error" />` is equivalent to `<add name="myTraceSwitch" value="1" />`.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <switches>  
         <add name="General" value="4" />  
      </switches>  
      <trace autoflush="true" indentsize="2">  
         <listeners>  
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener, System, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="MyListener.log" traceOutputOptions="ProcessId, LogicalOperationStack, Timestamp, ThreadId, Callstack, DateTime" />  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="cbe86-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cbe86-138">See also</span></span>

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- [<span data-ttu-id="cbe86-139">Schéma des paramètres de trace et de débogage</span><span class="sxs-lookup"><span data-stu-id="cbe86-139">Trace and Debug Settings Schema</span></span>](index.md)
