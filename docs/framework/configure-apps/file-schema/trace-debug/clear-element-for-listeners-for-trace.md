---
title: <clear>, Élément de <listeners> pour<trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/clear
helpviewer_keywords:
- clear element for <listeners> for <trace>
- <clear> element for <listeners> for <trace>
ms.assetid: b44732a8-271f-4a06-ba9e-fe3298d6f192
ms.openlocfilehash: 905dad8274fede80f4809ff3c7a014049f9df450
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153540"
---
# <a name="clear-element-for-listeners-for-trace"></a><span data-ttu-id="5ff8c-102">\<clear>, Élément de \<listeners> pour\<trace></span><span class="sxs-lookup"><span data-stu-id="5ff8c-102">\<clear> Element for \<listeners> for \<trace></span></span>
<span data-ttu-id="5ff8c-103">Efface la collection `Listeners` de la trace.</span><span class="sxs-lookup"><span data-stu-id="5ff8c-103">Clears the `Listeners` collection for trace.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-trace.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="5ff8c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5ff8c-104">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5ff8c-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="5ff8c-105">Attributes and Elements</span></span>  
 <span data-ttu-id="5ff8c-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="5ff8c-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5ff8c-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="5ff8c-107">Attributes</span></span>  
 <span data-ttu-id="5ff8c-108">Aucun.</span><span class="sxs-lookup"><span data-stu-id="5ff8c-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5ff8c-109">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="5ff8c-109">Child Elements</span></span>  
 <span data-ttu-id="5ff8c-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="5ff8c-110">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5ff8c-111">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="5ff8c-111">Parent Elements</span></span>  
  
|<span data-ttu-id="5ff8c-112">Élément</span><span class="sxs-lookup"><span data-stu-id="5ff8c-112">Element</span></span>|<span data-ttu-id="5ff8c-113">Description</span><span class="sxs-lookup"><span data-stu-id="5ff8c-113">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="5ff8c-114">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5ff8c-114">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="5ff8c-115">Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.</span><span class="sxs-lookup"><span data-stu-id="5ff8c-115">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="5ff8c-116">Contient les écouteurs qui collectent, stockent et acheminent les messages de traçage.</span><span class="sxs-lookup"><span data-stu-id="5ff8c-116">Contains listeners that collect, store, and route tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="5ff8c-117">Contient des écouteurs qui collectent, stockent et acheminent des messages.</span><span class="sxs-lookup"><span data-stu-id="5ff8c-117">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="5ff8c-118">Les écouteurs dirigent la sortie de suivi vers une cible appropriée.</span><span class="sxs-lookup"><span data-stu-id="5ff8c-118">Listeners direct the tracing output to an appropriate target.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5ff8c-119">Remarques</span><span class="sxs-lookup"><span data-stu-id="5ff8c-119">Remarks</span></span>  
 <span data-ttu-id="5ff8c-120">L' `<clear>` élément supprime tous les écouteurs de la `Listeners` collection pour la trace.</span><span class="sxs-lookup"><span data-stu-id="5ff8c-120">The `<clear>` element removes all listeners from the `Listeners` collection for trace.</span></span> <span data-ttu-id="5ff8c-121">Vous pouvez utiliser l' `<clear>` élément avant d’utiliser l' `<add>` élément pour être certain qu’il n’existe aucun autre écouteur actif dans la collection.</span><span class="sxs-lookup"><span data-stu-id="5ff8c-121">You can use the `<clear>` element before using the `<add>` element to be certain there are no other active listeners in the collection.</span></span>  
  
 <span data-ttu-id="5ff8c-122">Vous pouvez effacer la `Listeners` collection par programmation en appelant la <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> méthode sur la <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> propriété ( `System.Diagnostics.Trace.Listeners.Clear()` ).</span><span class="sxs-lookup"><span data-stu-id="5ff8c-122">You can clear the `Listeners` collection programmatically by calling the <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> method on the <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> property (`System.Diagnostics.Trace.Listeners.Clear()`).</span></span>  
  
 <span data-ttu-id="5ff8c-123">Cet élément peut être utilisé dans le fichier de configuration de l’ordinateur (machine. config) et dans le fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="5ff8c-123">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5ff8c-124">L' `<clear>` élément supprime le <xref:System.Diagnostics.DefaultTraceListener> de la `Listeners` collection, en modifiant le comportement des <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> méthodes, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType> , <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType> et <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="5ff8c-124">The `<clear>` element removes the <xref:System.Diagnostics.DefaultTraceListener> from the `Listeners` collection, altering the behavior of the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, and <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="5ff8c-125">L’appel d’une `Assert` `Fail` méthode ou entraîne normalement l’affichage d’une boîte de message.</span><span class="sxs-lookup"><span data-stu-id="5ff8c-125">Calling an `Assert` or `Fail` method normally results in the display of a message box.</span></span> <span data-ttu-id="5ff8c-126">Toutefois, la boîte de message ne s’affiche pas si le <xref:System.Diagnostics.DefaultTraceListener> n’est pas dans la `Listeners` collection.</span><span class="sxs-lookup"><span data-stu-id="5ff8c-126">However, the message box is not displayed if the <xref:System.Diagnostics.DefaultTraceListener> is not in the `Listeners` collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5ff8c-127">Exemple</span><span class="sxs-lookup"><span data-stu-id="5ff8c-127">Example</span></span>  
 <span data-ttu-id="5ff8c-128">L’exemple suivant montre comment utiliser l' `<clear>` élément avant d’utiliser l' `<add>` élément pour ajouter l’écouteur `console` à la `Listeners` collection pour la trace.</span><span class="sxs-lookup"><span data-stu-id="5ff8c-128">The following example shows how to use the `<clear>` element before using the `<add>` element to add the listener `console` to the `Listeners` collection for trace.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <trace autoflush="false" indentsize="4">  
      <listeners>  
        <clear/>  
        <add name="console"
          type="System.Diagnostics.ConsoleTraceListener" >  
          <filter type="System.Diagnostics.EventTypeFilter"
            initializeData="Error" />  
        </add>  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="5ff8c-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5ff8c-129">See also</span></span>

- <xref:System.Diagnostics.Trace.Listeners%2A>
- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="5ff8c-130">Schéma des paramètres de traçage et de débogage</span><span class="sxs-lookup"><span data-stu-id="5ff8c-130">Trace and Debug Settings Schema</span></span>](index.md)
- [\<remove>](remove-element-for-listeners-for-trace.md)
- [<span data-ttu-id="5ff8c-131">Écouteurs de suivi</span><span class="sxs-lookup"><span data-stu-id="5ff8c-131">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
