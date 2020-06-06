---
title: Élément <trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace
- http://schemas.microsoft.com/.NetConfiguration/v2.0#trace
helpviewer_keywords:
- <trace> element
- listeners
- trace element
- trace listener, <trace> element
ms.assetid: 7931c942-63c1-47c3-a045-9d9de3cacdbf
ms.openlocfilehash: 7d8a989219d84e8604e767456c84c0092bc73b22
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153164"
---
# <a name="trace-element"></a><span data-ttu-id="a1b4a-102">Élément \<trace></span><span class="sxs-lookup"><span data-stu-id="a1b4a-102">\<trace> Element</span></span>
<span data-ttu-id="a1b4a-103">Contient les écouteurs qui collectent, stockent et acheminent les messages de traçage.</span><span class="sxs-lookup"><span data-stu-id="a1b4a-103">Contains listeners that collect, store, and route tracing messages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<trace>**  
  
## <a name="syntax"></a><span data-ttu-id="a1b4a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a1b4a-104">Syntax</span></span>  
  
```xml  
<trace autoflush="true|false"
       indentsize="indent value"  
       useGlobalLock="true| false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a1b4a-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="a1b4a-105">Attributes and Elements</span></span>  
 <span data-ttu-id="a1b4a-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="a1b4a-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a1b4a-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="a1b4a-107">Attributes</span></span>  
  
|<span data-ttu-id="a1b4a-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="a1b4a-108">Attribute</span></span>|<span data-ttu-id="a1b4a-109">Description</span><span class="sxs-lookup"><span data-stu-id="a1b4a-109">Description</span></span>|  
|---------------|-----------------|  
|`autoflush`|<span data-ttu-id="a1b4a-110">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="a1b4a-110">Optional attribute.</span></span><br /><br /> <span data-ttu-id="a1b4a-111">Spécifie si les écouteurs de la trace vident automatiquement la mémoire tampon de sortie après chaque opération d’écriture.</span><span class="sxs-lookup"><span data-stu-id="a1b4a-111">Specifies whether the trace listeners automatically flush the output buffer after every write operation.</span></span>|  
|`indentsize`|<span data-ttu-id="a1b4a-112">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="a1b4a-112">Optional attribute.</span></span><br /><br /> <span data-ttu-id="a1b4a-113">Spécifie le nombre d’espaces à mettre en retrait.</span><span class="sxs-lookup"><span data-stu-id="a1b4a-113">Specifies the number of spaces to indent.</span></span>|  
|`useGlobalLock`|<span data-ttu-id="a1b4a-114">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="a1b4a-114">Optional attribute.</span></span><br /><br /> <span data-ttu-id="a1b4a-115">Indique si le verrouillage global doit être utilisé.</span><span class="sxs-lookup"><span data-stu-id="a1b4a-115">Indicates whether the global lock should be used.</span></span>|  
  
## <a name="autoflush-attribute"></a><span data-ttu-id="a1b4a-116">Attribut de vidage automatique</span><span class="sxs-lookup"><span data-stu-id="a1b4a-116">autoflush Attribute</span></span>  
  
|<span data-ttu-id="a1b4a-117">Valeur</span><span class="sxs-lookup"><span data-stu-id="a1b4a-117">Value</span></span>|<span data-ttu-id="a1b4a-118">Description</span><span class="sxs-lookup"><span data-stu-id="a1b4a-118">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="a1b4a-119">N’efface pas automatiquement la mémoire tampon de sortie.</span><span class="sxs-lookup"><span data-stu-id="a1b4a-119">Does not automatically flush the output buffer.</span></span> <span data-ttu-id="a1b4a-120">Il s'agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="a1b4a-120">This is the default.</span></span>|  
|`true`|<span data-ttu-id="a1b4a-121">Vide automatiquement la mémoire tampon de sortie.</span><span class="sxs-lookup"><span data-stu-id="a1b4a-121">Automatically flushes the output buffer.</span></span>|  
  
## <a name="usegloballock-attribute"></a><span data-ttu-id="a1b4a-122">Attribut useGlobalLock</span><span class="sxs-lookup"><span data-stu-id="a1b4a-122">useGlobalLock Attribute</span></span>  
  
|<span data-ttu-id="a1b4a-123">Valeur</span><span class="sxs-lookup"><span data-stu-id="a1b4a-123">Value</span></span>|<span data-ttu-id="a1b4a-124">Description</span><span class="sxs-lookup"><span data-stu-id="a1b4a-124">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="a1b4a-125">N’utilise pas le verrou global si l’écouteur est thread-safe ; dans le cas contraire, utilise le verrou global.</span><span class="sxs-lookup"><span data-stu-id="a1b4a-125">Does not use the global lock if the listener is thread safe; otherwise, uses the global lock.</span></span>|  
|`true`|<span data-ttu-id="a1b4a-126">Utilise le verrou global indépendamment du fait que l’écouteur soit thread-safe.</span><span class="sxs-lookup"><span data-stu-id="a1b4a-126">Uses the global lock regardless of whether the listener is thread safe.</span></span> <span data-ttu-id="a1b4a-127">Il s'agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="a1b4a-127">This is the default.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a1b4a-128">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a1b4a-128">Child Elements</span></span>  
  
|<span data-ttu-id="a1b4a-129">Élément</span><span class="sxs-lookup"><span data-stu-id="a1b4a-129">Element</span></span>|<span data-ttu-id="a1b4a-130">Description</span><span class="sxs-lookup"><span data-stu-id="a1b4a-130">Description</span></span>|  
|-------------|-----------------|  
|[\<listeners>](listeners-element-for-trace.md)|<span data-ttu-id="a1b4a-131">Spécifie un écouteur qui collecte, stocke et achemine des messages.</span><span class="sxs-lookup"><span data-stu-id="a1b4a-131">Specifies a listener that collects, stores, and routes messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a1b4a-132">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="a1b4a-132">Parent Elements</span></span>  
  
|<span data-ttu-id="a1b4a-133">Élément</span><span class="sxs-lookup"><span data-stu-id="a1b4a-133">Element</span></span>|<span data-ttu-id="a1b4a-134">Description</span><span class="sxs-lookup"><span data-stu-id="a1b4a-134">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="a1b4a-135">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a1b4a-135">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="a1b4a-136">Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.</span><span class="sxs-lookup"><span data-stu-id="a1b4a-136">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a1b4a-137">Exemple</span><span class="sxs-lookup"><span data-stu-id="a1b4a-137">Example</span></span>  
 <span data-ttu-id="a1b4a-138">L’exemple suivant montre comment utiliser l' `<trace>` élément pour ajouter l’écouteur `MyListener` à la `Listeners` collection.</span><span class="sxs-lookup"><span data-stu-id="a1b4a-138">The following example shows how to use the `<trace>` element to add the listener `MyListener` to the `Listeners` collection.</span></span> <span data-ttu-id="a1b4a-139">`MyListener`crée un fichier nommé `MyListener.log` et écrit la sortie dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="a1b4a-139">`MyListener` creates a file that is named `MyListener.log` and writes the output to the file.</span></span> <span data-ttu-id="a1b4a-140">L' `useGlobalLock` attribut a la valeur `false` , ce qui empêche l’utilisation du verrou global si l’écouteur de la trace est thread-safe.</span><span class="sxs-lookup"><span data-stu-id="a1b4a-140">The `useGlobalLock` attribute is set to `false`, which causes the global lock not to be used if the trace listener is thread safe.</span></span> <span data-ttu-id="a1b4a-141">L' `autoflush` attribut a la valeur `true` , ce qui amène l’écouteur de la trace à écrire dans le fichier, que la <xref:System.Diagnostics.Trace.Flush%2A?displayProperty=nameWithType> méthode soit appelée ou non.</span><span class="sxs-lookup"><span data-stu-id="a1b4a-141">The `autoflush` attribute is set to `true`, which causes the trace listener to write to the file regardless of whether the <xref:System.Diagnostics.Trace.Flush%2A?displayProperty=nameWithType> method is called.</span></span> <span data-ttu-id="a1b4a-142">L' `indentsize` attribut a la valeur 0 (zéro), ce qui amène l’écouteur à mettre en retrait les espaces nuls lorsque la <xref:System.Diagnostics.Trace.Indent%2A?displayProperty=nameWithType> méthode est appelée.</span><span class="sxs-lookup"><span data-stu-id="a1b4a-142">The `indentsize` attribute is set to 0 (zero), which causes the listener to indent zero spaces when the <xref:System.Diagnostics.Trace.Indent%2A?displayProperty=nameWithType> method is called.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <trace useGlobalLock="false" autoflush="true" indentsize="0">  
         <listeners>  
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener, system version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="c:\myListener.log" />  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a1b4a-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a1b4a-143">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- [<span data-ttu-id="a1b4a-144">Schéma des paramètres de traçage et de débogage</span><span class="sxs-lookup"><span data-stu-id="a1b4a-144">Trace and Debug Settings Schema</span></span>](index.md)
