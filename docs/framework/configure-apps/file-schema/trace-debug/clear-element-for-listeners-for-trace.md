---
title: <clear>, Élément <listeners> de pour<trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/clear
helpviewer_keywords:
- clear element for <listeners> for <trace>
- <clear> element for <listeners> for <trace>
ms.assetid: b44732a8-271f-4a06-ba9e-fe3298d6f192
ms.openlocfilehash: 9816ba0f8e4ddd4c38537eb4e014a4240ff20407
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927173"
---
# <a name="clear-element-for-listeners-for-trace"></a><span data-ttu-id="f8723-102">\<Effacer > élément pour \<les écouteurs > pour \<la trace ></span><span class="sxs-lookup"><span data-stu-id="f8723-102">\<clear> Element for \<listeners> for \<trace></span></span>
<span data-ttu-id="f8723-103">Efface la collection `Listeners` de la trace.</span><span class="sxs-lookup"><span data-stu-id="f8723-103">Clears the `Listeners` collection for trace.</span></span>  
  
 <span data-ttu-id="f8723-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="f8723-104">\<configuration></span></span>  
<span data-ttu-id="f8723-105">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="f8723-105">\<system.diagnostics></span></span>  
<span data-ttu-id="f8723-106">\<> de trace</span><span class="sxs-lookup"><span data-stu-id="f8723-106">\<trace></span></span>  
<span data-ttu-id="f8723-107">\<listeners></span><span class="sxs-lookup"><span data-stu-id="f8723-107">\<listeners></span></span>  
<span data-ttu-id="f8723-108">\<clear></span><span class="sxs-lookup"><span data-stu-id="f8723-108">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8723-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f8723-109">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f8723-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="f8723-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f8723-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="f8723-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f8723-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="f8723-112">Attributes</span></span>  
 <span data-ttu-id="f8723-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="f8723-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f8723-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="f8723-114">Child Elements</span></span>  
 <span data-ttu-id="f8723-115">Aucun.</span><span class="sxs-lookup"><span data-stu-id="f8723-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f8723-116">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="f8723-116">Parent Elements</span></span>  
  
|<span data-ttu-id="f8723-117">Élément</span><span class="sxs-lookup"><span data-stu-id="f8723-117">Element</span></span>|<span data-ttu-id="f8723-118">Description</span><span class="sxs-lookup"><span data-stu-id="f8723-118">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="f8723-119">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f8723-119">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="f8723-120">Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.</span><span class="sxs-lookup"><span data-stu-id="f8723-120">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="f8723-121">Contient les écouteurs qui collectent, stockent et acheminent les messages de traçage.</span><span class="sxs-lookup"><span data-stu-id="f8723-121">Contains listeners that collect, store, and route tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="f8723-122">Contient des écouteurs qui collectent, stockent et acheminent des messages.</span><span class="sxs-lookup"><span data-stu-id="f8723-122">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="f8723-123">Les écouteurs dirigent la sortie de suivi vers une cible appropriée.</span><span class="sxs-lookup"><span data-stu-id="f8723-123">Listeners direct the tracing output to an appropriate target.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f8723-124">Notes</span><span class="sxs-lookup"><span data-stu-id="f8723-124">Remarks</span></span>  
 <span data-ttu-id="f8723-125">L' `<clear>` élément supprime tous les écouteurs de la `Listeners` collection pour la trace.</span><span class="sxs-lookup"><span data-stu-id="f8723-125">The `<clear>` element removes all listeners from the `Listeners` collection for trace.</span></span> <span data-ttu-id="f8723-126">Vous pouvez utiliser l' `<clear>` élément avant d’utiliser `<add>` l’élément pour être certain qu’il n’existe aucun autre écouteur actif dans la collection.</span><span class="sxs-lookup"><span data-stu-id="f8723-126">You can use the `<clear>` element before using the `<add>` element to be certain there are no other active listeners in the collection.</span></span>  
  
 <span data-ttu-id="f8723-127">Vous pouvez effacer la `Listeners` collection par programmation en appelant la <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> méthode sur la <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> propriété (`System.Diagnostics.Trace.Listeners.Clear()`).</span><span class="sxs-lookup"><span data-stu-id="f8723-127">You can clear the `Listeners` collection programmatically by calling the <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> method on the <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> property (`System.Diagnostics.Trace.Listeners.Clear()`).</span></span>  
  
 <span data-ttu-id="f8723-128">Cet élément peut être utilisé dans le fichier de configuration de l’ordinateur (machine. config) et dans le fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="f8723-128">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f8723-129">L' `<clear>` élément supprime le <xref:System.Diagnostics.DefaultTraceListener> de la `Listeners` <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType> <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> collection, en<xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>modifiant le comportement des méthodes ,,et.<xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="f8723-129">The `<clear>` element removes the <xref:System.Diagnostics.DefaultTraceListener> from the `Listeners` collection, altering the behavior of the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, and <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="f8723-130">L’appel `Assert` d' `Fail` une méthode ou entraîne normalement l’affichage d’une boîte de message.</span><span class="sxs-lookup"><span data-stu-id="f8723-130">Calling an `Assert` or `Fail` method normally results in the display of a message box.</span></span> <span data-ttu-id="f8723-131">Toutefois, la boîte de message ne s’affiche pas <xref:System.Diagnostics.DefaultTraceListener> si le n’est `Listeners` pas dans la collection.</span><span class="sxs-lookup"><span data-stu-id="f8723-131">However, the message box is not displayed if the <xref:System.Diagnostics.DefaultTraceListener> is not in the `Listeners` collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f8723-132">Exemples</span><span class="sxs-lookup"><span data-stu-id="f8723-132">Example</span></span>  
 <span data-ttu-id="f8723-133">L’exemple suivant montre `<clear>` comment utiliser l’élément avant d’utiliser l' `<add>` élément `console` pour ajouter l’écouteur à la `Listeners` collection pour la trace.</span><span class="sxs-lookup"><span data-stu-id="f8723-133">The following example shows how to use the `<clear>` element before using the `<add>` element to add the listener `console` to the `Listeners` collection for trace.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f8723-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f8723-134">See also</span></span>

- <xref:System.Diagnostics.Trace.Listeners%2A>
- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="f8723-135">Schéma des paramètres de trace et de débogage</span><span class="sxs-lookup"><span data-stu-id="f8723-135">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="f8723-136">\<remove></span><span class="sxs-lookup"><span data-stu-id="f8723-136">\<remove></span></span>](remove-element-for-listeners-for-trace.md)
- [<span data-ttu-id="f8723-137">Écouteurs de suivi</span><span class="sxs-lookup"><span data-stu-id="f8723-137">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
