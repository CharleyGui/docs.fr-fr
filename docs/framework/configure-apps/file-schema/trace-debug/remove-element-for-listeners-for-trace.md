---
title: <remove>, Élément <listeners> de pour<trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/remove
helpviewer_keywords:
- remove element
- <remove> element
ms.assetid: 9a5cd1b5-be1a-485f-8f0c-2890ad3ef3e0
ms.openlocfilehash: 0c5c9efb8a22d26ea5d4467f9628af5935d6dbad
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920476"
---
# <a name="remove-element-for-listeners-for-trace"></a><span data-ttu-id="8aa44-102">\<supprimer > élément pour \<les écouteurs > pour \<la trace ></span><span class="sxs-lookup"><span data-stu-id="8aa44-102">\<remove> Element for \<listeners> for \<trace></span></span>
<span data-ttu-id="8aa44-103">Supprime un écouteur de la collection d' **écouteurs** .</span><span class="sxs-lookup"><span data-stu-id="8aa44-103">Removes a listener from the **Listeners** collection.</span></span>  
  
 <span data-ttu-id="8aa44-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="8aa44-104">\<configuration></span></span>  
<span data-ttu-id="8aa44-105">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="8aa44-105">\<system.diagnostics></span></span>  
<span data-ttu-id="8aa44-106">\<> de trace</span><span class="sxs-lookup"><span data-stu-id="8aa44-106">\<trace></span></span>  
<span data-ttu-id="8aa44-107">\<listeners></span><span class="sxs-lookup"><span data-stu-id="8aa44-107">\<listeners></span></span>  
<span data-ttu-id="8aa44-108">\<remove></span><span class="sxs-lookup"><span data-stu-id="8aa44-108">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8aa44-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8aa44-109">Syntax</span></span>  
  
```xml  
<remove name="listener name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8aa44-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="8aa44-110">Attributes and Elements</span></span>  
 <span data-ttu-id="8aa44-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="8aa44-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8aa44-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="8aa44-112">Attributes</span></span>  
  
|<span data-ttu-id="8aa44-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="8aa44-113">Attribute</span></span>|<span data-ttu-id="8aa44-114">Description</span><span class="sxs-lookup"><span data-stu-id="8aa44-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8aa44-115">**name**</span><span class="sxs-lookup"><span data-stu-id="8aa44-115">**name**</span></span>|<span data-ttu-id="8aa44-116">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="8aa44-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="8aa44-117">Nom de l’écouteur à supprimer de la collection d' **écouteurs** .</span><span class="sxs-lookup"><span data-stu-id="8aa44-117">The name of the listener to remove from the **Listeners** collection.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8aa44-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="8aa44-118">Child Elements</span></span>  
 <span data-ttu-id="8aa44-119">Aucun.</span><span class="sxs-lookup"><span data-stu-id="8aa44-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8aa44-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="8aa44-120">Parent Elements</span></span>  
  
|<span data-ttu-id="8aa44-121">Élément</span><span class="sxs-lookup"><span data-stu-id="8aa44-121">Element</span></span>|<span data-ttu-id="8aa44-122">Description</span><span class="sxs-lookup"><span data-stu-id="8aa44-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="8aa44-123">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8aa44-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`listeners`|<span data-ttu-id="8aa44-124">Spécifie un écouteur qui collecte, stocke et achemine des messages.</span><span class="sxs-lookup"><span data-stu-id="8aa44-124">Specifies a listener that collects, stores, and routes messages.</span></span> <span data-ttu-id="8aa44-125">Les écouteurs dirigent la sortie de suivi vers une cible appropriée.</span><span class="sxs-lookup"><span data-stu-id="8aa44-125">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="8aa44-126">Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.</span><span class="sxs-lookup"><span data-stu-id="8aa44-126">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="8aa44-127">Configure le service de trace ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="8aa44-127">Configures the ASP.NET trace service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8aa44-128">Notes</span><span class="sxs-lookup"><span data-stu-id="8aa44-128">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8aa44-129">La suppression <xref:System.Diagnostics.DefaultTraceListener> du de `Listeners` la <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>collection altère <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>le <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> comportement des méthodes, ,et.<xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="8aa44-129">Removing the <xref:System.Diagnostics.DefaultTraceListener> from the `Listeners` collection alters the behavior of the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, and <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="8aa44-130">L’appel `Assert` d' `Fail` une méthode ou entraîne normalement l’affichage d’une boîte de message, mais la boîte de message ne s' <xref:System.Diagnostics.DefaultTraceListener> affiche pas si le `Listeners` n’est pas dans la collection.</span><span class="sxs-lookup"><span data-stu-id="8aa44-130">Calling an `Assert` or `Fail` method normally results in the display of a message box, however the message box is not displayed if the <xref:System.Diagnostics.DefaultTraceListener> is not in the `Listeners` collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8aa44-131">Exemple</span><span class="sxs-lookup"><span data-stu-id="8aa44-131">Example</span></span>  
 <span data-ttu-id="8aa44-132">L’exemple suivant montre comment supprimer l’écouteur de suivi par défaut de la collection d' **écouteurs** de trace.</span><span class="sxs-lookup"><span data-stu-id="8aa44-132">The following example shows how to remove the default trace listener from the trace **Listeners** collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8aa44-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8aa44-133">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- [<span data-ttu-id="8aa44-134">Schéma des paramètres de trace et de débogage</span><span class="sxs-lookup"><span data-stu-id="8aa44-134">Trace and Debug Settings Schema</span></span>](index.md)
