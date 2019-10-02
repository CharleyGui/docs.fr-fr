---
title: Élément <clear> pour <listeners> pour <trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/clear
helpviewer_keywords:
- clear element for <listeners> for <trace>
- <clear> element for <listeners> for <trace>
ms.assetid: b44732a8-271f-4a06-ba9e-fe3298d6f192
ms.openlocfilehash: 0361580724351f8f42d058d5e20354e3335bac2f
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699377"
---
# <a name="clear-element-for-listeners-for-trace"></a><span data-ttu-id="bf66e-102">\<clear > élément de \<listeners > pour \<trace ></span><span class="sxs-lookup"><span data-stu-id="bf66e-102">\<clear> Element for \<listeners> for \<trace></span></span>
<span data-ttu-id="bf66e-103">Efface la collection `Listeners` de la trace.</span><span class="sxs-lookup"><span data-stu-id="bf66e-103">Clears the `Listeners` collection for trace.</span></span>  
  
[<span data-ttu-id="bf66e-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="bf66e-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="bf66e-105">&nbsp; @ no__t-1[ **\<System. diagnostics >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="bf66e-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>  
<span data-ttu-id="bf66e-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<trace >** ](trace-element.md)</span><span class="sxs-lookup"><span data-stu-id="bf66e-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)</span></span>  
<span data-ttu-id="bf66e-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5[ **\<listeners >** ](listeners-element-for-trace.md)</span><span class="sxs-lookup"><span data-stu-id="bf66e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-trace.md)</span></span>  
<span data-ttu-id="bf66e-108">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7 **\<clear >**</span><span class="sxs-lookup"><span data-stu-id="bf66e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf66e-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bf66e-109">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bf66e-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="bf66e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="bf66e-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="bf66e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bf66e-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="bf66e-112">Attributes</span></span>  
 <span data-ttu-id="bf66e-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="bf66e-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="bf66e-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="bf66e-114">Child Elements</span></span>  
 <span data-ttu-id="bf66e-115">Aucun.</span><span class="sxs-lookup"><span data-stu-id="bf66e-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bf66e-116">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="bf66e-116">Parent Elements</span></span>  
  
|<span data-ttu-id="bf66e-117">Élément</span><span class="sxs-lookup"><span data-stu-id="bf66e-117">Element</span></span>|<span data-ttu-id="bf66e-118">Description</span><span class="sxs-lookup"><span data-stu-id="bf66e-118">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="bf66e-119">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bf66e-119">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="bf66e-120">Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.</span><span class="sxs-lookup"><span data-stu-id="bf66e-120">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="bf66e-121">Contient les écouteurs qui collectent, stockent et acheminent les messages de traçage.</span><span class="sxs-lookup"><span data-stu-id="bf66e-121">Contains listeners that collect, store, and route tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="bf66e-122">Contient des écouteurs qui collectent, stockent et acheminent des messages.</span><span class="sxs-lookup"><span data-stu-id="bf66e-122">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="bf66e-123">Les écouteurs dirigent la sortie de suivi vers une cible appropriée.</span><span class="sxs-lookup"><span data-stu-id="bf66e-123">Listeners direct the tracing output to an appropriate target.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bf66e-124">Notes</span><span class="sxs-lookup"><span data-stu-id="bf66e-124">Remarks</span></span>  
 <span data-ttu-id="bf66e-125">L’élément `<clear>` supprime tous les écouteurs de la collection `Listeners` pour la trace.</span><span class="sxs-lookup"><span data-stu-id="bf66e-125">The `<clear>` element removes all listeners from the `Listeners` collection for trace.</span></span> <span data-ttu-id="bf66e-126">Vous pouvez utiliser l’élément `<clear>` avant d’utiliser l’élément `<add>` pour être certain qu’il n’existe aucun autre écouteur actif dans la collection.</span><span class="sxs-lookup"><span data-stu-id="bf66e-126">You can use the `<clear>` element before using the `<add>` element to be certain there are no other active listeners in the collection.</span></span>  
  
 <span data-ttu-id="bf66e-127">Vous pouvez effacer la collection `Listeners` par programmation en appelant la méthode <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> sur la propriété <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> (`System.Diagnostics.Trace.Listeners.Clear()`).</span><span class="sxs-lookup"><span data-stu-id="bf66e-127">You can clear the `Listeners` collection programmatically by calling the <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> method on the <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> property (`System.Diagnostics.Trace.Listeners.Clear()`).</span></span>  
  
 <span data-ttu-id="bf66e-128">Cet élément peut être utilisé dans le fichier de configuration de l’ordinateur (machine. config) et dans le fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="bf66e-128">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bf66e-129">L’élément `<clear>` supprime la <xref:System.Diagnostics.DefaultTraceListener> de la collection `Listeners`, en modifiant le comportement des méthodes <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType> et <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bf66e-129">The `<clear>` element removes the <xref:System.Diagnostics.DefaultTraceListener> from the `Listeners` collection, altering the behavior of the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, and <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="bf66e-130">L’appel d’une méthode `Assert` ou `Fail` entraîne normalement l’affichage d’une boîte de message.</span><span class="sxs-lookup"><span data-stu-id="bf66e-130">Calling an `Assert` or `Fail` method normally results in the display of a message box.</span></span> <span data-ttu-id="bf66e-131">Toutefois, la boîte de message ne s’affiche pas si le <xref:System.Diagnostics.DefaultTraceListener> n’est pas dans la collection `Listeners`.</span><span class="sxs-lookup"><span data-stu-id="bf66e-131">However, the message box is not displayed if the <xref:System.Diagnostics.DefaultTraceListener> is not in the `Listeners` collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bf66e-132">Exemple</span><span class="sxs-lookup"><span data-stu-id="bf66e-132">Example</span></span>  
 <span data-ttu-id="bf66e-133">L’exemple suivant montre comment utiliser l’élément `<clear>` avant d’utiliser l’élément `<add>` pour ajouter l’écouteur `console` à la collection `Listeners` pour la trace.</span><span class="sxs-lookup"><span data-stu-id="bf66e-133">The following example shows how to use the `<clear>` element before using the `<add>` element to add the listener `console` to the `Listeners` collection for trace.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bf66e-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bf66e-134">See also</span></span>

- <xref:System.Diagnostics.Trace.Listeners%2A>
- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="bf66e-135">Schéma des paramètres de trace et de débogage</span><span class="sxs-lookup"><span data-stu-id="bf66e-135">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="bf66e-136">\<remove></span><span class="sxs-lookup"><span data-stu-id="bf66e-136">\<remove></span></span>](remove-element-for-listeners-for-trace.md)
- [<span data-ttu-id="bf66e-137">Écouteurs de suivi</span><span class="sxs-lookup"><span data-stu-id="bf66e-137">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
