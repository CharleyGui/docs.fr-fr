---
title: <clear>Élément <listeners> pour pour<trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/clear
helpviewer_keywords:
- clear element for <listeners> for <trace>
- <clear> element for <listeners> for <trace>
ms.assetid: b44732a8-271f-4a06-ba9e-fe3298d6f192
ms.openlocfilehash: 905dad8274fede80f4809ff3c7a014049f9df450
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153540"
---
# <a name="clear-element-for-listeners-for-trace"></a><span data-ttu-id="cb795-102">\<élément> clair pour \<les auditeurs \<> pour les traces></span><span class="sxs-lookup"><span data-stu-id="cb795-102">\<clear> Element for \<listeners> for \<trace></span></span>
<span data-ttu-id="cb795-103">Efface la collection `Listeners` de la trace.</span><span class="sxs-lookup"><span data-stu-id="cb795-103">Clears the `Listeners` collection for trace.</span></span>  

<span data-ttu-id="cb795-104">[**\<configuration>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="cb795-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="cb795-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="cb795-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="cb795-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)</span><span class="sxs-lookup"><span data-stu-id="cb795-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)</span></span>\
<span data-ttu-id="cb795-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<auditeurs>**](listeners-element-for-trace.md)</span><span class="sxs-lookup"><span data-stu-id="cb795-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-trace.md)</span></span>\
<span data-ttu-id="cb795-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clair>**</span><span class="sxs-lookup"><span data-stu-id="cb795-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="cb795-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cb795-109">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cb795-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="cb795-110">Attributes and Elements</span></span>  
 <span data-ttu-id="cb795-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="cb795-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cb795-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="cb795-112">Attributes</span></span>  
 <span data-ttu-id="cb795-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="cb795-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="cb795-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="cb795-114">Child Elements</span></span>  
 <span data-ttu-id="cb795-115">Aucun.</span><span class="sxs-lookup"><span data-stu-id="cb795-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cb795-116">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="cb795-116">Parent Elements</span></span>  
  
|<span data-ttu-id="cb795-117">Élément</span><span class="sxs-lookup"><span data-stu-id="cb795-117">Element</span></span>|<span data-ttu-id="cb795-118">Description</span><span class="sxs-lookup"><span data-stu-id="cb795-118">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="cb795-119">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cb795-119">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="cb795-120">Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.</span><span class="sxs-lookup"><span data-stu-id="cb795-120">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="cb795-121">Contient les écouteurs qui collectent, stockent et acheminent les messages de traçage.</span><span class="sxs-lookup"><span data-stu-id="cb795-121">Contains listeners that collect, store, and route tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="cb795-122">Contient des auditeurs qui recueillent, stockent et acheminent des messages.</span><span class="sxs-lookup"><span data-stu-id="cb795-122">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="cb795-123">Les auditeurs dirigent la sortie de traçage vers une cible appropriée.</span><span class="sxs-lookup"><span data-stu-id="cb795-123">Listeners direct the tracing output to an appropriate target.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cb795-124">Notes </span><span class="sxs-lookup"><span data-stu-id="cb795-124">Remarks</span></span>  
 <span data-ttu-id="cb795-125">L’élément `<clear>` supprime tous `Listeners` les auditeurs de la collection pour la trace.</span><span class="sxs-lookup"><span data-stu-id="cb795-125">The `<clear>` element removes all listeners from the `Listeners` collection for trace.</span></span> <span data-ttu-id="cb795-126">Vous pouvez `<clear>` utiliser l’élément avant d’utiliser l’élément `<add>` pour être certain qu’il n’y a pas d’autres auditeurs actifs dans la collection.</span><span class="sxs-lookup"><span data-stu-id="cb795-126">You can use the `<clear>` element before using the `<add>` element to be certain there are no other active listeners in the collection.</span></span>  
  
 <span data-ttu-id="cb795-127">Vous pouvez `Listeners` effacer la collecte programmatiquement en appelant la <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> méthode sur la <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> propriété (`System.Diagnostics.Trace.Listeners.Clear()`).</span><span class="sxs-lookup"><span data-stu-id="cb795-127">You can clear the `Listeners` collection programmatically by calling the <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> method on the <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> property (`System.Diagnostics.Trace.Listeners.Clear()`).</span></span>  
  
 <span data-ttu-id="cb795-128">Cet élément peut être utilisé dans le fichier de configuration de la machine (Machine.config) et le fichier de configuration d’application.</span><span class="sxs-lookup"><span data-stu-id="cb795-128">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cb795-129">`<clear>` L’élément supprime <xref:System.Diagnostics.DefaultTraceListener> le `Listeners` de la collection, <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>modifiant <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType> <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>le <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> comportement de la , , , et les méthodes.</span><span class="sxs-lookup"><span data-stu-id="cb795-129">The `<clear>` element removes the <xref:System.Diagnostics.DefaultTraceListener> from the `Listeners` collection, altering the behavior of the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, and <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="cb795-130">L’appel d’une `Assert` méthode ou `Fail` une méthode permet normalement l’affichage d’une boîte de message.</span><span class="sxs-lookup"><span data-stu-id="cb795-130">Calling an `Assert` or `Fail` method normally results in the display of a message box.</span></span> <span data-ttu-id="cb795-131">Toutefois, la boîte de message <xref:System.Diagnostics.DefaultTraceListener> n’est `Listeners` pas affichée si elle n’est pas dans la collection.</span><span class="sxs-lookup"><span data-stu-id="cb795-131">However, the message box is not displayed if the <xref:System.Diagnostics.DefaultTraceListener> is not in the `Listeners` collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cb795-132"> Exemple</span><span class="sxs-lookup"><span data-stu-id="cb795-132">Example</span></span>  
 <span data-ttu-id="cb795-133">L’exemple suivant montre `<clear>` comment utiliser `<add>` l’élément avant `console` d’utiliser l’élément pour ajouter l’auditeur à la `Listeners` collection pour la trace.</span><span class="sxs-lookup"><span data-stu-id="cb795-133">The following example shows how to use the `<clear>` element before using the `<add>` element to add the listener `console` to the `Listeners` collection for trace.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cb795-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cb795-134">See also</span></span>

- <xref:System.Diagnostics.Trace.Listeners%2A>
- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="cb795-135">Trace et Debug Paramètres Schema</span><span class="sxs-lookup"><span data-stu-id="cb795-135">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="cb795-136">\<supprimer></span><span class="sxs-lookup"><span data-stu-id="cb795-136">\<remove></span></span>](remove-element-for-listeners-for-trace.md)
- [<span data-ttu-id="cb795-137">Écouteurs de suivi</span><span class="sxs-lookup"><span data-stu-id="cb795-137">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
