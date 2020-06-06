---
title: <remove>, Élément de <listeners> pour<trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/remove
helpviewer_keywords:
- remove element
- <remove> element
ms.assetid: 9a5cd1b5-be1a-485f-8f0c-2890ad3ef3e0
ms.openlocfilehash: f06973ec30d5061e4a200d6bf7e68adcf6302018
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74088843"
---
# <a name="remove-element-for-listeners-for-trace"></a><span data-ttu-id="ecca7-102">\<remove>, Élément de \<listeners> pour\<trace></span><span class="sxs-lookup"><span data-stu-id="ecca7-102">\<remove> Element for \<listeners> for \<trace></span></span>
<span data-ttu-id="ecca7-103">Supprime un écouteur de la collection d' **écouteurs** .</span><span class="sxs-lookup"><span data-stu-id="ecca7-103">Removes a listener from the **Listeners** collection.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-trace.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a><span data-ttu-id="ecca7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ecca7-104">Syntax</span></span>  
  
```xml  
<remove name="listener name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ecca7-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="ecca7-105">Attributes and Elements</span></span>  
 <span data-ttu-id="ecca7-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="ecca7-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ecca7-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="ecca7-107">Attributes</span></span>  
  
|<span data-ttu-id="ecca7-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="ecca7-108">Attribute</span></span>|<span data-ttu-id="ecca7-109">Description</span><span class="sxs-lookup"><span data-stu-id="ecca7-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ecca7-110">**name**</span><span class="sxs-lookup"><span data-stu-id="ecca7-110">**name**</span></span>|<span data-ttu-id="ecca7-111">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="ecca7-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="ecca7-112">Nom de l’écouteur à supprimer de la collection d' **écouteurs** .</span><span class="sxs-lookup"><span data-stu-id="ecca7-112">The name of the listener to remove from the **Listeners** collection.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ecca7-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="ecca7-113">Child Elements</span></span>  
 <span data-ttu-id="ecca7-114">Aucun.</span><span class="sxs-lookup"><span data-stu-id="ecca7-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ecca7-115">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="ecca7-115">Parent Elements</span></span>  
  
|<span data-ttu-id="ecca7-116">Élément</span><span class="sxs-lookup"><span data-stu-id="ecca7-116">Element</span></span>|<span data-ttu-id="ecca7-117">Description</span><span class="sxs-lookup"><span data-stu-id="ecca7-117">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="ecca7-118">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ecca7-118">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`listeners`|<span data-ttu-id="ecca7-119">Spécifie un écouteur qui collecte, stocke et achemine des messages.</span><span class="sxs-lookup"><span data-stu-id="ecca7-119">Specifies a listener that collects, stores, and routes messages.</span></span> <span data-ttu-id="ecca7-120">Les écouteurs dirigent la sortie de suivi vers une cible appropriée.</span><span class="sxs-lookup"><span data-stu-id="ecca7-120">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="ecca7-121">Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.</span><span class="sxs-lookup"><span data-stu-id="ecca7-121">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="ecca7-122">Configuration du service de trace ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="ecca7-122">Configures the ASP.NET trace service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ecca7-123">Remarques</span><span class="sxs-lookup"><span data-stu-id="ecca7-123">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ecca7-124">La suppression du <xref:System.Diagnostics.DefaultTraceListener> de la `Listeners` collection altère le comportement des <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> méthodes,, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType> <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType> et <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="ecca7-124">Removing the <xref:System.Diagnostics.DefaultTraceListener> from the `Listeners` collection alters the behavior of the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, and <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="ecca7-125">L’appel d’une `Assert` `Fail` méthode ou entraîne normalement l’affichage d’une boîte de message, mais la boîte de message ne s’affiche pas si le <xref:System.Diagnostics.DefaultTraceListener> n’est pas dans la `Listeners` collection.</span><span class="sxs-lookup"><span data-stu-id="ecca7-125">Calling an `Assert` or `Fail` method normally results in the display of a message box, however the message box is not displayed if the <xref:System.Diagnostics.DefaultTraceListener> is not in the `Listeners` collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ecca7-126">Exemple</span><span class="sxs-lookup"><span data-stu-id="ecca7-126">Example</span></span>  
 <span data-ttu-id="ecca7-127">L’exemple suivant montre comment supprimer l’écouteur de suivi par défaut de la collection d' **écouteurs** de trace.</span><span class="sxs-lookup"><span data-stu-id="ecca7-127">The following example shows how to remove the default trace listener from the trace **Listeners** collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ecca7-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ecca7-128">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- [<span data-ttu-id="ecca7-129">Schéma des paramètres de traçage et de débogage</span><span class="sxs-lookup"><span data-stu-id="ecca7-129">Trace and Debug Settings Schema</span></span>](index.md)
