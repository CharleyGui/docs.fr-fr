---
title: <remove>, Élément <listeners> de pour<source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/remove
helpviewer_keywords:
- remove element for <listeners> for <source>
- <remove> element for <listeners> for <source>
ms.assetid: 3ff6b578-273d-407f-b07f-8251f1f9f5d0
ms.openlocfilehash: edd27dd262004aead7db4d81db8ecab0e831dac1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926992"
---
# <a name="remove-element-for-listeners-for-source"></a><span data-ttu-id="2884f-102">\<supprimer > élément pour \<les écouteurs > pour \<le > source</span><span class="sxs-lookup"><span data-stu-id="2884f-102">\<remove> Element for \<listeners> for \<source></span></span>
<span data-ttu-id="2884f-103">Supprime un écouteur de la collection `Listeners` pour une source de trace.</span><span class="sxs-lookup"><span data-stu-id="2884f-103">Removes a listener from the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="2884f-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="2884f-104">\<configuration></span></span>  
<span data-ttu-id="2884f-105">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="2884f-105">\<system.diagnostics></span></span>  
<span data-ttu-id="2884f-106">\<sources></span><span class="sxs-lookup"><span data-stu-id="2884f-106">\<sources></span></span>  
<span data-ttu-id="2884f-107">\<> source</span><span class="sxs-lookup"><span data-stu-id="2884f-107">\<source></span></span>  
<span data-ttu-id="2884f-108">\<listeners></span><span class="sxs-lookup"><span data-stu-id="2884f-108">\<listeners></span></span>  
<span data-ttu-id="2884f-109">\<remove></span><span class="sxs-lookup"><span data-stu-id="2884f-109">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2884f-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2884f-110">Syntax</span></span>  
  
```xml  
<remove name="listenerName" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2884f-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="2884f-111">Attributes and Elements</span></span>  
 <span data-ttu-id="2884f-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="2884f-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2884f-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="2884f-113">Attributes</span></span>  
  
|<span data-ttu-id="2884f-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="2884f-114">Attribute</span></span>|<span data-ttu-id="2884f-115">Description</span><span class="sxs-lookup"><span data-stu-id="2884f-115">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="2884f-116">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="2884f-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="2884f-117">Nom de l’écouteur à supprimer de la `Listeners` collection.</span><span class="sxs-lookup"><span data-stu-id="2884f-117">The name of the listener to remove from the `Listeners` collection.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2884f-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="2884f-118">Child Elements</span></span>  
 <span data-ttu-id="2884f-119">Aucun.</span><span class="sxs-lookup"><span data-stu-id="2884f-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2884f-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="2884f-120">Parent Elements</span></span>  
  
|<span data-ttu-id="2884f-121">Élément</span><span class="sxs-lookup"><span data-stu-id="2884f-121">Element</span></span>|<span data-ttu-id="2884f-122">Description</span><span class="sxs-lookup"><span data-stu-id="2884f-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="2884f-123">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2884f-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="2884f-124">Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.</span><span class="sxs-lookup"><span data-stu-id="2884f-124">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="2884f-125">Contient les sources de trace qui lancent des messages de traçage.</span><span class="sxs-lookup"><span data-stu-id="2884f-125">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="2884f-126">Spécifie une source de trace qui lance des messages de traçage.</span><span class="sxs-lookup"><span data-stu-id="2884f-126">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="2884f-127">Spécifie les écouteurs qui collectent, stockent et acheminent les messages.</span><span class="sxs-lookup"><span data-stu-id="2884f-127">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2884f-128">Notes</span><span class="sxs-lookup"><span data-stu-id="2884f-128">Remarks</span></span>  
 <span data-ttu-id="2884f-129">L' `<remove>` élément supprime un écouteur spécifié de la `Listeners` collection pour une source de trace.</span><span class="sxs-lookup"><span data-stu-id="2884f-129">The `<remove>` element removes a specified listener from the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="2884f-130">Vous pouvez supprimer un élément de la `Listeners` collection pour une source de suivi par programmation en appelant la <xref:System.Diagnostics.TraceListenerCollection.Remove%2A> méthode sur la <xref:System.Diagnostics.TraceSource.Listeners%2A> propriété de l' <xref:System.Diagnostics.TraceSource> instance.</span><span class="sxs-lookup"><span data-stu-id="2884f-130">You can remove an element from the `Listeners` collection for a trace source programmatically by calling the <xref:System.Diagnostics.TraceListenerCollection.Remove%2A> method on the <xref:System.Diagnostics.TraceSource.Listeners%2A> property of the <xref:System.Diagnostics.TraceSource> instance.</span></span>  
  
 <span data-ttu-id="2884f-131">Cet élément peut être utilisé dans le fichier de configuration de l’ordinateur (machine. config) et dans le fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="2884f-131">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2884f-132">Exemple</span><span class="sxs-lookup"><span data-stu-id="2884f-132">Example</span></span>  
 <span data-ttu-id="2884f-133">L’exemple suivant `<remove>` montre comment utiliser l’élément avant d’utiliser l' `<add>` élément `console` pour ajouter l’écouteur à la `Listeners` collection pour la source `TraceSourceApp`de trace.</span><span class="sxs-lookup"><span data-stu-id="2884f-133">The following example shows how to use the `<remove>` element before using the `<add>` element to add the listener `console` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="TraceSourceApp" switchName="sourceSwitch"   
         switchType="System.Diagnostics.SourceSwitch" >  
         <listeners>  
           <remove name="Default"/>  
           <add name="console"   
             type="System.Diagnostics.ConsoleTraceListener" />  
         </listeners>  
      </source>  
    </sources>  
  </system.diagnostics>  
</configuration>   
```  
  
## <a name="see-also"></a><span data-ttu-id="2884f-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2884f-134">See also</span></span>

- <xref:System.Diagnostics.TraceSource.Listeners%2A>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="2884f-135">Schéma des paramètres de trace et de débogage</span><span class="sxs-lookup"><span data-stu-id="2884f-135">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="2884f-136">\<clear></span><span class="sxs-lookup"><span data-stu-id="2884f-136">\<clear></span></span>](clear-element-for-listeners-for-source.md)
- [<span data-ttu-id="2884f-137">Écouteurs de suivi</span><span class="sxs-lookup"><span data-stu-id="2884f-137">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
