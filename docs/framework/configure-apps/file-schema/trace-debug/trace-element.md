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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153164"
---
# <a name="trace-element"></a><span data-ttu-id="63936-102">\<trace> Élément</span><span class="sxs-lookup"><span data-stu-id="63936-102">\<trace> Element</span></span>
<span data-ttu-id="63936-103">Contient les écouteurs qui collectent, stockent et acheminent les messages de traçage.</span><span class="sxs-lookup"><span data-stu-id="63936-103">Contains listeners that collect, store, and route tracing messages.</span></span>  
  
[<span data-ttu-id="63936-104">**\<configuration>**</span><span class="sxs-lookup"><span data-stu-id="63936-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="63936-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="63936-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>  
<span data-ttu-id="63936-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<trace>**</span><span class="sxs-lookup"><span data-stu-id="63936-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<trace>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63936-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="63936-107">Syntax</span></span>  
  
```xml  
<trace autoflush="true|false"
       indentsize="indent value"  
       useGlobalLock="true| false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="63936-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="63936-108">Attributes and Elements</span></span>  
 <span data-ttu-id="63936-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="63936-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="63936-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="63936-110">Attributes</span></span>  
  
|<span data-ttu-id="63936-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="63936-111">Attribute</span></span>|<span data-ttu-id="63936-112">Description</span><span class="sxs-lookup"><span data-stu-id="63936-112">Description</span></span>|  
|---------------|-----------------|  
|`autoflush`|<span data-ttu-id="63936-113">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="63936-113">Optional attribute.</span></span><br /><br /> <span data-ttu-id="63936-114">Précise si les auditeurs trace automatiquement rincer le tampon de sortie après chaque opération d’écriture.</span><span class="sxs-lookup"><span data-stu-id="63936-114">Specifies whether the trace listeners automatically flush the output buffer after every write operation.</span></span>|  
|`indentsize`|<span data-ttu-id="63936-115">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="63936-115">Optional attribute.</span></span><br /><br /> <span data-ttu-id="63936-116">Spécifie le nombre d’espaces à en retrait.</span><span class="sxs-lookup"><span data-stu-id="63936-116">Specifies the number of spaces to indent.</span></span>|  
|`useGlobalLock`|<span data-ttu-id="63936-117">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="63936-117">Optional attribute.</span></span><br /><br /> <span data-ttu-id="63936-118">Indique si le verrou global doit être utilisé.</span><span class="sxs-lookup"><span data-stu-id="63936-118">Indicates whether the global lock should be used.</span></span>|  
  
## <a name="autoflush-attribute"></a><span data-ttu-id="63936-119">Attribut autoflush</span><span class="sxs-lookup"><span data-stu-id="63936-119">autoflush Attribute</span></span>  
  
|<span data-ttu-id="63936-120">Valeur</span><span class="sxs-lookup"><span data-stu-id="63936-120">Value</span></span>|<span data-ttu-id="63936-121">Description</span><span class="sxs-lookup"><span data-stu-id="63936-121">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="63936-122">Ne chasse pas automatiquement le tampon de sortie.</span><span class="sxs-lookup"><span data-stu-id="63936-122">Does not automatically flush the output buffer.</span></span> <span data-ttu-id="63936-123">Il s’agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="63936-123">This is the default.</span></span>|  
|`true`|<span data-ttu-id="63936-124">Rincer automatiquement le tampon de sortie.</span><span class="sxs-lookup"><span data-stu-id="63936-124">Automatically flushes the output buffer.</span></span>|  
  
## <a name="usegloballock-attribute"></a><span data-ttu-id="63936-125">utilisationGlobalLock Attribut</span><span class="sxs-lookup"><span data-stu-id="63936-125">useGlobalLock Attribute</span></span>  
  
|<span data-ttu-id="63936-126">Valeur</span><span class="sxs-lookup"><span data-stu-id="63936-126">Value</span></span>|<span data-ttu-id="63936-127">Description</span><span class="sxs-lookup"><span data-stu-id="63936-127">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="63936-128">N’utilise pas le verrou global si l’auditeur est sans danger de thread; autrement, utilise le verrou global.</span><span class="sxs-lookup"><span data-stu-id="63936-128">Does not use the global lock if the listener is thread safe; otherwise, uses the global lock.</span></span>|  
|`true`|<span data-ttu-id="63936-129">Utilise le verrou global indépendamment du fait que l’auditeur soit sans danger pour le thread.</span><span class="sxs-lookup"><span data-stu-id="63936-129">Uses the global lock regardless of whether the listener is thread safe.</span></span> <span data-ttu-id="63936-130">Il s’agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="63936-130">This is the default.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="63936-131">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="63936-131">Child Elements</span></span>  
  
|<span data-ttu-id="63936-132">Élément</span><span class="sxs-lookup"><span data-stu-id="63936-132">Element</span></span>|<span data-ttu-id="63936-133">Description</span><span class="sxs-lookup"><span data-stu-id="63936-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="63936-134">\<auditeurs></span><span class="sxs-lookup"><span data-stu-id="63936-134">\<listeners></span></span>](listeners-element-for-trace.md)|<span data-ttu-id="63936-135">Spécifie un auditeur qui recueille, stocke et achemine les messages.</span><span class="sxs-lookup"><span data-stu-id="63936-135">Specifies a listener that collects, stores, and routes messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="63936-136">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="63936-136">Parent Elements</span></span>  
  
|<span data-ttu-id="63936-137">Élément</span><span class="sxs-lookup"><span data-stu-id="63936-137">Element</span></span>|<span data-ttu-id="63936-138">Description</span><span class="sxs-lookup"><span data-stu-id="63936-138">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="63936-139">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="63936-139">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="63936-140">Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.</span><span class="sxs-lookup"><span data-stu-id="63936-140">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="63936-141"> Exemple</span><span class="sxs-lookup"><span data-stu-id="63936-141">Example</span></span>  
 <span data-ttu-id="63936-142">L’exemple suivant montre `<trace>` comment utiliser l’élément pour ajouter l’auditeur `MyListener` à la `Listeners` collection.</span><span class="sxs-lookup"><span data-stu-id="63936-142">The following example shows how to use the `<trace>` element to add the listener `MyListener` to the `Listeners` collection.</span></span> <span data-ttu-id="63936-143">`MyListener`crée un fichier `MyListener.log` qui est nommé et écrit la sortie au fichier.</span><span class="sxs-lookup"><span data-stu-id="63936-143">`MyListener` creates a file that is named `MyListener.log` and writes the output to the file.</span></span> <span data-ttu-id="63936-144">L’attribut `useGlobalLock` est `false`défini à , ce qui provoque la serrure globale de ne pas être utilisé si l’auditeur trace est thread safe.</span><span class="sxs-lookup"><span data-stu-id="63936-144">The `useGlobalLock` attribute is set to `false`, which causes the global lock not to be used if the trace listener is thread safe.</span></span> <span data-ttu-id="63936-145">L’attribut `autoflush` est `true`défini à , ce qui provoque l’auditeur <xref:System.Diagnostics.Trace.Flush%2A?displayProperty=nameWithType> trace d’écrire au fichier indépendamment du fait que la méthode est appelée.</span><span class="sxs-lookup"><span data-stu-id="63936-145">The `autoflush` attribute is set to `true`, which causes the trace listener to write to the file regardless of whether the <xref:System.Diagnostics.Trace.Flush%2A?displayProperty=nameWithType> method is called.</span></span> <span data-ttu-id="63936-146">L’attribut `indentsize` est réglé à 0 (zéro), ce qui provoque <xref:System.Diagnostics.Trace.Indent%2A?displayProperty=nameWithType> l’auditeur à l’auditeur à l’indent zéro espace lorsque la méthode est appelée.</span><span class="sxs-lookup"><span data-stu-id="63936-146">The `indentsize` attribute is set to 0 (zero), which causes the listener to indent zero spaces when the <xref:System.Diagnostics.Trace.Indent%2A?displayProperty=nameWithType> method is called.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="63936-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="63936-147">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- [<span data-ttu-id="63936-148">Trace et Debug Paramètres Schema</span><span class="sxs-lookup"><span data-stu-id="63936-148">Trace and Debug Settings Schema</span></span>](index.md)
