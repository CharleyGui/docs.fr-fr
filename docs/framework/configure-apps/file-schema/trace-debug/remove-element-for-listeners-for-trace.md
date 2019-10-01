---
title: Élément <remove> pour <listeners> pour <trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/remove
helpviewer_keywords:
- remove element
- <remove> element
ms.assetid: 9a5cd1b5-be1a-485f-8f0c-2890ad3ef3e0
ms.openlocfilehash: 56d1e56514aed98d5f3b9f7363e461af6ac68a8c
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697218"
---
# <a name="remove-element-for-listeners-for-trace"></a><span data-ttu-id="bca45-102">\<remove > élément de \<listeners > pour \<trace ></span><span class="sxs-lookup"><span data-stu-id="bca45-102">\<remove> Element for \<listeners> for \<trace></span></span>
<span data-ttu-id="bca45-103">Supprime un écouteur de la collection d' **écouteurs** .</span><span class="sxs-lookup"><span data-stu-id="bca45-103">Removes a listener from the **Listeners** collection.</span></span>  
  
[<span data-ttu-id="bca45-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="bca45-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="bca45-105">&nbsp; @ no__t-1[ **\<System. diagnostics >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="bca45-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>  
<span data-ttu-id="bca45-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<trace >** ](trace-element.md)</span><span class="sxs-lookup"><span data-stu-id="bca45-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)</span></span>  
<span data-ttu-id="bca45-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5[ **\<listeners >** ](listeners-element-for-trace.md)</span><span class="sxs-lookup"><span data-stu-id="bca45-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-trace.md)</span></span>  
<span data-ttu-id="bca45-108">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7 **\<remove >**</span><span class="sxs-lookup"><span data-stu-id="bca45-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bca45-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bca45-109">Syntax</span></span>  
  
```xml  
<remove name="listener name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bca45-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="bca45-110">Attributes and Elements</span></span>  
 <span data-ttu-id="bca45-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="bca45-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bca45-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="bca45-112">Attributes</span></span>  
  
|<span data-ttu-id="bca45-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="bca45-113">Attribute</span></span>|<span data-ttu-id="bca45-114">Description</span><span class="sxs-lookup"><span data-stu-id="bca45-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bca45-115">**name**</span><span class="sxs-lookup"><span data-stu-id="bca45-115">**name**</span></span>|<span data-ttu-id="bca45-116">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="bca45-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="bca45-117">Nom de l’écouteur à supprimer de la collection d' **écouteurs** .</span><span class="sxs-lookup"><span data-stu-id="bca45-117">The name of the listener to remove from the **Listeners** collection.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bca45-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="bca45-118">Child Elements</span></span>  
 <span data-ttu-id="bca45-119">Aucun.</span><span class="sxs-lookup"><span data-stu-id="bca45-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bca45-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="bca45-120">Parent Elements</span></span>  
  
|<span data-ttu-id="bca45-121">Élément</span><span class="sxs-lookup"><span data-stu-id="bca45-121">Element</span></span>|<span data-ttu-id="bca45-122">Description</span><span class="sxs-lookup"><span data-stu-id="bca45-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="bca45-123">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bca45-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`listeners`|<span data-ttu-id="bca45-124">Spécifie un écouteur qui collecte, stocke et achemine des messages.</span><span class="sxs-lookup"><span data-stu-id="bca45-124">Specifies a listener that collects, stores, and routes messages.</span></span> <span data-ttu-id="bca45-125">Les écouteurs dirigent la sortie de suivi vers une cible appropriée.</span><span class="sxs-lookup"><span data-stu-id="bca45-125">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="bca45-126">Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.</span><span class="sxs-lookup"><span data-stu-id="bca45-126">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="bca45-127">Configure le service de trace ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="bca45-127">Configures the ASP.NET trace service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bca45-128">Notes</span><span class="sxs-lookup"><span data-stu-id="bca45-128">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bca45-129">La suppression de la <xref:System.Diagnostics.DefaultTraceListener> de la collection `Listeners` altère le comportement des méthodes <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType> et <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bca45-129">Removing the <xref:System.Diagnostics.DefaultTraceListener> from the `Listeners` collection alters the behavior of the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, and <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="bca45-130">L’appel d’une méthode `Assert` ou `Fail` entraîne normalement l’affichage d’une boîte de message, mais la boîte de message ne s’affiche pas si le <xref:System.Diagnostics.DefaultTraceListener> n’est pas dans la collection `Listeners`.</span><span class="sxs-lookup"><span data-stu-id="bca45-130">Calling an `Assert` or `Fail` method normally results in the display of a message box, however the message box is not displayed if the <xref:System.Diagnostics.DefaultTraceListener> is not in the `Listeners` collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bca45-131">Exemple</span><span class="sxs-lookup"><span data-stu-id="bca45-131">Example</span></span>  
 <span data-ttu-id="bca45-132">L’exemple suivant montre comment supprimer l’écouteur de suivi par défaut de la collection d' **écouteurs** de trace.</span><span class="sxs-lookup"><span data-stu-id="bca45-132">The following example shows how to remove the default trace listener from the trace **Listeners** collection.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <trace autoflush="true" indentsize="0">  
         <listeners>  
            <remove name="Default" />  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bca45-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bca45-133">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- [<span data-ttu-id="bca45-134">Schéma des paramètres de trace et de débogage</span><span class="sxs-lookup"><span data-stu-id="bca45-134">Trace and Debug Settings Schema</span></span>](index.md)
