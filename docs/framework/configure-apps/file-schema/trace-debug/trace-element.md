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
ms.openlocfilehash: fd90d271591a47849b3f70aea50cbe909b6fd613
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920409"
---
# <a name="trace-element"></a><span data-ttu-id="a2f8e-102">\<Élément trace ></span><span class="sxs-lookup"><span data-stu-id="a2f8e-102">\<trace> Element</span></span>
<span data-ttu-id="a2f8e-103">Contient les écouteurs qui collectent, stockent et acheminent les messages de traçage.</span><span class="sxs-lookup"><span data-stu-id="a2f8e-103">Contains listeners that collect, store, and route tracing messages.</span></span>  
  
 <span data-ttu-id="a2f8e-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="a2f8e-104">\<configuration></span></span>  
<span data-ttu-id="a2f8e-105">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="a2f8e-105">\<system.diagnostics></span></span>  
<span data-ttu-id="a2f8e-106">\<> de trace</span><span class="sxs-lookup"><span data-stu-id="a2f8e-106">\<trace></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2f8e-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a2f8e-107">Syntax</span></span>  
  
```xml  
<trace autoflush="true|false"   
       indentsize="indent value"  
       useGlobalLock="true| false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a2f8e-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="a2f8e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="a2f8e-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="a2f8e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a2f8e-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="a2f8e-110">Attributes</span></span>  
  
|<span data-ttu-id="a2f8e-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="a2f8e-111">Attribute</span></span>|<span data-ttu-id="a2f8e-112">Description</span><span class="sxs-lookup"><span data-stu-id="a2f8e-112">Description</span></span>|  
|---------------|-----------------|  
|`autoflush`|<span data-ttu-id="a2f8e-113">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="a2f8e-113">Optional attribute.</span></span><br /><br /> <span data-ttu-id="a2f8e-114">Spécifie si les écouteurs de la trace vident automatiquement la mémoire tampon de sortie après chaque opération d’écriture.</span><span class="sxs-lookup"><span data-stu-id="a2f8e-114">Specifies whether the trace listeners automatically flush the output buffer after every write operation.</span></span>|  
|`indentsize`|<span data-ttu-id="a2f8e-115">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="a2f8e-115">Optional attribute.</span></span><br /><br /> <span data-ttu-id="a2f8e-116">Spécifie le nombre d’espaces à mettre en retrait.</span><span class="sxs-lookup"><span data-stu-id="a2f8e-116">Specifies the number of spaces to indent.</span></span>|  
|`useGlobalLock`|<span data-ttu-id="a2f8e-117">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="a2f8e-117">Optional attribute.</span></span><br /><br /> <span data-ttu-id="a2f8e-118">Indique si le verrouillage global doit être utilisé.</span><span class="sxs-lookup"><span data-stu-id="a2f8e-118">Indicates whether the global lock should be used.</span></span>|  
  
## <a name="autoflush-attribute"></a><span data-ttu-id="a2f8e-119">Attribut de vidage automatique</span><span class="sxs-lookup"><span data-stu-id="a2f8e-119">autoflush Attribute</span></span>  
  
|<span data-ttu-id="a2f8e-120">Valeur</span><span class="sxs-lookup"><span data-stu-id="a2f8e-120">Value</span></span>|<span data-ttu-id="a2f8e-121">Description</span><span class="sxs-lookup"><span data-stu-id="a2f8e-121">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="a2f8e-122">N’efface pas automatiquement la mémoire tampon de sortie.</span><span class="sxs-lookup"><span data-stu-id="a2f8e-122">Does not automatically flush the output buffer.</span></span> <span data-ttu-id="a2f8e-123">Il s'agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="a2f8e-123">This is the default.</span></span>|  
|`true`|<span data-ttu-id="a2f8e-124">Vide automatiquement la mémoire tampon de sortie.</span><span class="sxs-lookup"><span data-stu-id="a2f8e-124">Automatically flushes the output buffer.</span></span>|  
  
## <a name="usegloballock-attribute"></a><span data-ttu-id="a2f8e-125">Attribut useGlobalLock</span><span class="sxs-lookup"><span data-stu-id="a2f8e-125">useGlobalLock Attribute</span></span>  
  
|<span data-ttu-id="a2f8e-126">Valeur</span><span class="sxs-lookup"><span data-stu-id="a2f8e-126">Value</span></span>|<span data-ttu-id="a2f8e-127">Description</span><span class="sxs-lookup"><span data-stu-id="a2f8e-127">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="a2f8e-128">N’utilise pas le verrou global si l’écouteur est thread-safe; dans le cas contraire, utilise le verrou global.</span><span class="sxs-lookup"><span data-stu-id="a2f8e-128">Does not use the global lock if the listener is thread safe; otherwise, uses the global lock.</span></span>|  
|`true`|<span data-ttu-id="a2f8e-129">Utilise le verrou global indépendamment du fait que l’écouteur soit thread-safe.</span><span class="sxs-lookup"><span data-stu-id="a2f8e-129">Uses the global lock regardless of whether the listener is thread safe.</span></span> <span data-ttu-id="a2f8e-130">Il s'agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="a2f8e-130">This is the default.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a2f8e-131">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a2f8e-131">Child Elements</span></span>  
  
|<span data-ttu-id="a2f8e-132">Élément</span><span class="sxs-lookup"><span data-stu-id="a2f8e-132">Element</span></span>|<span data-ttu-id="a2f8e-133">Description</span><span class="sxs-lookup"><span data-stu-id="a2f8e-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a2f8e-134">\<listeners></span><span class="sxs-lookup"><span data-stu-id="a2f8e-134">\<listeners></span></span>](listeners-element-for-trace.md)|<span data-ttu-id="a2f8e-135">Spécifie un écouteur qui collecte, stocke et achemine des messages.</span><span class="sxs-lookup"><span data-stu-id="a2f8e-135">Specifies a listener that collects, stores, and routes messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a2f8e-136">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="a2f8e-136">Parent Elements</span></span>  
  
|<span data-ttu-id="a2f8e-137">Élément</span><span class="sxs-lookup"><span data-stu-id="a2f8e-137">Element</span></span>|<span data-ttu-id="a2f8e-138">Description</span><span class="sxs-lookup"><span data-stu-id="a2f8e-138">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="a2f8e-139">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a2f8e-139">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="a2f8e-140">Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.</span><span class="sxs-lookup"><span data-stu-id="a2f8e-140">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a2f8e-141">Exemples</span><span class="sxs-lookup"><span data-stu-id="a2f8e-141">Example</span></span>  
 <span data-ttu-id="a2f8e-142">L’exemple suivant montre comment utiliser l' `<trace>` élément pour ajouter l' `MyListener` écouteur à la `Listeners` collection.</span><span class="sxs-lookup"><span data-stu-id="a2f8e-142">The following example shows how to use the `<trace>` element to add the listener `MyListener` to the `Listeners` collection.</span></span> <span data-ttu-id="a2f8e-143">`MyListener`crée un fichier nommé `MyListener.log` et écrit la sortie dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="a2f8e-143">`MyListener` creates a file that is named `MyListener.log` and writes the output to the file.</span></span> <span data-ttu-id="a2f8e-144">L' `useGlobalLock` attribut a la `false`valeur, ce qui empêche l’utilisation du verrou global si l’écouteur de la trace est thread-safe.</span><span class="sxs-lookup"><span data-stu-id="a2f8e-144">The `useGlobalLock` attribute is set to `false`, which causes the global lock not to be used if the trace listener is thread safe.</span></span> <span data-ttu-id="a2f8e-145">L' `autoflush` attribut a la `true`valeur, ce qui amène l’écouteur de la trace à écrire dans le fichier, <xref:System.Diagnostics.Trace.Flush%2A?displayProperty=nameWithType> que la méthode soit appelée ou non.</span><span class="sxs-lookup"><span data-stu-id="a2f8e-145">The `autoflush` attribute is set to `true`, which causes the trace listener to write to the file regardless of whether the <xref:System.Diagnostics.Trace.Flush%2A?displayProperty=nameWithType> method is called.</span></span> <span data-ttu-id="a2f8e-146">L' `indentsize` attribut a la valeur 0 (zéro), ce qui amène l’écouteur à mettre en retrait les <xref:System.Diagnostics.Trace.Indent%2A?displayProperty=nameWithType> espaces nuls lorsque la méthode est appelée.</span><span class="sxs-lookup"><span data-stu-id="a2f8e-146">The `indentsize` attribute is set to 0 (zero), which causes the listener to indent zero spaces when the <xref:System.Diagnostics.Trace.Indent%2A?displayProperty=nameWithType> method is called.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a2f8e-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a2f8e-147">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- [<span data-ttu-id="a2f8e-148">Schéma des paramètres de trace et de débogage</span><span class="sxs-lookup"><span data-stu-id="a2f8e-148">Trace and Debug Settings Schema</span></span>](index.md)
