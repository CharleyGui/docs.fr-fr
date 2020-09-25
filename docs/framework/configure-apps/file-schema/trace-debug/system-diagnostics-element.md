---
title: <l’élément System. Diagnostics>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.diagnostics
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics
helpviewer_keywords:
- <system.diagnostics> element
- system.diagnostics element
ms.assetid: 3f348f42-fa72-4ff2-aa1c-bb9eecad4bb2
ms.openlocfilehash: aff324ac9952c95c78d7ca15572651dba23b79b7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91195166"
---
# <a name="systemdiagnostics-element"></a><span data-ttu-id="a383f-102">Élément \<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="a383f-102">\<system.diagnostics> Element</span></span>

<span data-ttu-id="a383f-103">Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.</span><span class="sxs-lookup"><span data-stu-id="a383f-103">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<system.diagnostics>**  
  
## <a name="syntax"></a><span data-ttu-id="a383f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a383f-104">Syntax</span></span>  
  
```xml  
<system.diagnostics>
</system.diagnostics>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a383f-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="a383f-105">Attributes and Elements</span></span>  

 <span data-ttu-id="a383f-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="a383f-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a383f-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="a383f-107">Attributes</span></span>  

 <span data-ttu-id="a383f-108">Aucun.</span><span class="sxs-lookup"><span data-stu-id="a383f-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a383f-109">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a383f-109">Child Elements</span></span>  
  
|<span data-ttu-id="a383f-110">Élément</span><span class="sxs-lookup"><span data-stu-id="a383f-110">Element</span></span>|<span data-ttu-id="a383f-111">Description</span><span class="sxs-lookup"><span data-stu-id="a383f-111">Description</span></span>|  
|-------------|-----------------|  
|[\<assert>](assert-element.md)|<span data-ttu-id="a383f-112">Indique si une boîte de message doit s’afficher quand vous appelez la méthode <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> ; spécifie également le nom du fichier dans lequel écrire les messages.</span><span class="sxs-lookup"><span data-stu-id="a383f-112">Specifies whether to display a message box when you call the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> method; also specifies the name of the file to write messages to.</span></span>|  
|[\<performanceCounters>](performancecounters-element.md)|<span data-ttu-id="a383f-113">Spécifie la taille de la mémoire globale partagée par les compteurs de performances.</span><span class="sxs-lookup"><span data-stu-id="a383f-113">Specifies the size of the global memory shared by performance counters.</span></span>|  
|[\<sharedListeners>](sharedlisteners-element.md)|<span data-ttu-id="a383f-114">Contient des écouteurs auxquels toute source ou tout élément de trace peuvent faire référence.</span><span class="sxs-lookup"><span data-stu-id="a383f-114">Contains listeners that any source or trace element can reference.</span></span> <span data-ttu-id="a383f-115">Les écouteurs identifiés comme écouteurs partagés peuvent être ajoutés à des sources ou des suivis par nom.</span><span class="sxs-lookup"><span data-stu-id="a383f-115">Listeners identified as shared listeners can be added to sources or traces by name.</span></span>|  
|[\<sources>](sources-element.md)|<span data-ttu-id="a383f-116">Spécifie les sources de suivi qui initialisent les messages de suivi.</span><span class="sxs-lookup"><span data-stu-id="a383f-116">Specifies trace sources that initiate tracing messages.</span></span>|  
|[\<switches>](switches-element.md)|<span data-ttu-id="a383f-117">Contient des commutateurs de trace et les niveaux où les commutateurs de trace sont définis.</span><span class="sxs-lookup"><span data-stu-id="a383f-117">Contains trace switches and the levels where the trace switches are set.</span></span>|  
|[\<trace>](trace-element.md)|<span data-ttu-id="a383f-118">Contient les écouteurs qui collectent, stockent et acheminent les messages de traçage.</span><span class="sxs-lookup"><span data-stu-id="a383f-118">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a383f-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="a383f-119">Parent Elements</span></span>  
  
|<span data-ttu-id="a383f-120">Élément</span><span class="sxs-lookup"><span data-stu-id="a383f-120">Element</span></span>|<span data-ttu-id="a383f-121">Description</span><span class="sxs-lookup"><span data-stu-id="a383f-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="a383f-122">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a383f-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a383f-123">Exemple</span><span class="sxs-lookup"><span data-stu-id="a383f-123">Example</span></span>  

 <span data-ttu-id="a383f-124">L’exemple suivant montre comment incorporer un commutateur de trace et un écouteur de suivi à l’intérieur de l' **\<system.diagnostics>** élément.</span><span class="sxs-lookup"><span data-stu-id="a383f-124">The following example shows how to embed a trace switch and a trace listener inside the **\<system.diagnostics>** element.</span></span> <span data-ttu-id="a383f-125">Le `General` commutateur de trace est défini sur le <xref:System.Diagnostics.TraceLevel> niveau.</span><span class="sxs-lookup"><span data-stu-id="a383f-125">The `General` trace switch is set to the <xref:System.Diagnostics.TraceLevel> level.</span></span> <span data-ttu-id="a383f-126">L’écouteur de suivi `myListener` crée un fichier nommé `MyListener.log` et écrit la sortie dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="a383f-126">The trace listener `myListener` creates a file called `MyListener.log` and writes the output to the file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a383f-127">Dans .NET Framework 2.0, vous pouvez spécifier la valeur d'un commutateur avec du texte.</span><span class="sxs-lookup"><span data-stu-id="a383f-127">In the .NET Framework version 2.0, you can use text to specify the value for a switch.</span></span> <span data-ttu-id="a383f-128">Par exemple, vous pouvez spécifier `true` pour un <xref:System.Diagnostics.BooleanSwitch> ou utiliser le texte représentant une valeur d’énumération comme `Error` pour un <xref:System.Diagnostics.TraceSwitch> .</span><span class="sxs-lookup"><span data-stu-id="a383f-128">For example, you can specify `true` for a <xref:System.Diagnostics.BooleanSwitch> or use the text representing an enumeration value such as `Error` for a <xref:System.Diagnostics.TraceSwitch>.</span></span> <span data-ttu-id="a383f-129">La ligne `<add name="myTraceSwitch" value="Error" />` équivaut à `<add name="myTraceSwitch" value="1" />`.</span><span class="sxs-lookup"><span data-stu-id="a383f-129">The line `<add name="myTraceSwitch" value="Error" />` is equivalent to `<add name="myTraceSwitch" value="1" />`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a383f-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a383f-130">See also</span></span>

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- [<span data-ttu-id="a383f-131">Schéma des paramètres de traçage et de débogage</span><span class="sxs-lookup"><span data-stu-id="a383f-131">Trace and Debug Settings Schema</span></span>](index.md)
