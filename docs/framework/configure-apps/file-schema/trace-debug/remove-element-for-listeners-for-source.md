---
title: Élément <remove> pour <listeners> pour <source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/remove
helpviewer_keywords:
- remove element for <listeners> for <source>
- <remove> element for <listeners> for <source>
ms.assetid: 3ff6b578-273d-407f-b07f-8251f1f9f5d0
ms.openlocfilehash: 4a11308278f755ec8271477352d91d8797d105c5
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699497"
---
# <a name="remove-element-for-listeners-for-source"></a><span data-ttu-id="a4b1b-102">\<remove > élément de \<listeners > pour \<Source ></span><span class="sxs-lookup"><span data-stu-id="a4b1b-102">\<remove> Element for \<listeners> for \<source></span></span>
<span data-ttu-id="a4b1b-103">Supprime un écouteur de la collection `Listeners` pour une source de trace.</span><span class="sxs-lookup"><span data-stu-id="a4b1b-103">Removes a listener from the `Listeners` collection for a trace source.</span></span>  
  
[<span data-ttu-id="a4b1b-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="a4b1b-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="a4b1b-105">&nbsp; @ no__t-1[ **\<System. diagnostics >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="a4b1b-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>  
<span data-ttu-id="a4b1b-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<sources >** ](sources-element.md)</span><span class="sxs-lookup"><span data-stu-id="a4b1b-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)</span></span>  
<span data-ttu-id="a4b1b-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5[ **\<source >** ](source-element.md)</span><span class="sxs-lookup"><span data-stu-id="a4b1b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)</span></span>  
<span data-ttu-id="a4b1b-108">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7[ **&nbsp;0listeners >** ](listeners-element-for-source.md)</span><span class="sxs-lookup"><span data-stu-id="a4b1b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-source.md)</span></span>  
<span data-ttu-id="a4b1b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<remove>**</span><span class="sxs-lookup"><span data-stu-id="a4b1b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4b1b-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a4b1b-110">Syntax</span></span>  
  
```xml  
<remove name="listenerName" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a4b1b-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="a4b1b-111">Attributes and Elements</span></span>  
 <span data-ttu-id="a4b1b-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="a4b1b-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a4b1b-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="a4b1b-113">Attributes</span></span>  
  
|<span data-ttu-id="a4b1b-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="a4b1b-114">Attribute</span></span>|<span data-ttu-id="a4b1b-115">Description</span><span class="sxs-lookup"><span data-stu-id="a4b1b-115">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="a4b1b-116">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="a4b1b-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="a4b1b-117">Nom de l’écouteur à supprimer de la collection `Listeners`.</span><span class="sxs-lookup"><span data-stu-id="a4b1b-117">The name of the listener to remove from the `Listeners` collection.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a4b1b-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a4b1b-118">Child Elements</span></span>  
 <span data-ttu-id="a4b1b-119">Aucun.</span><span class="sxs-lookup"><span data-stu-id="a4b1b-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a4b1b-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="a4b1b-120">Parent Elements</span></span>  
  
|<span data-ttu-id="a4b1b-121">Élément</span><span class="sxs-lookup"><span data-stu-id="a4b1b-121">Element</span></span>|<span data-ttu-id="a4b1b-122">Description</span><span class="sxs-lookup"><span data-stu-id="a4b1b-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="a4b1b-123">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a4b1b-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="a4b1b-124">Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.</span><span class="sxs-lookup"><span data-stu-id="a4b1b-124">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="a4b1b-125">Contient les sources de trace qui lancent des messages de traçage.</span><span class="sxs-lookup"><span data-stu-id="a4b1b-125">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="a4b1b-126">Spécifie une source de trace qui lance des messages de traçage.</span><span class="sxs-lookup"><span data-stu-id="a4b1b-126">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="a4b1b-127">Spécifie les écouteurs qui collectent, stockent et acheminent les messages.</span><span class="sxs-lookup"><span data-stu-id="a4b1b-127">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a4b1b-128">Notes</span><span class="sxs-lookup"><span data-stu-id="a4b1b-128">Remarks</span></span>  
 <span data-ttu-id="a4b1b-129">L’élément `<remove>` supprime un écouteur spécifié de la collection `Listeners` pour une source de trace.</span><span class="sxs-lookup"><span data-stu-id="a4b1b-129">The `<remove>` element removes a specified listener from the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="a4b1b-130">Vous pouvez supprimer un élément de la collection `Listeners` pour une source de suivi par programmation en appelant la méthode <xref:System.Diagnostics.TraceListenerCollection.Remove%2A> sur la propriété <xref:System.Diagnostics.TraceSource.Listeners%2A> de l’instance <xref:System.Diagnostics.TraceSource>.</span><span class="sxs-lookup"><span data-stu-id="a4b1b-130">You can remove an element from the `Listeners` collection for a trace source programmatically by calling the <xref:System.Diagnostics.TraceListenerCollection.Remove%2A> method on the <xref:System.Diagnostics.TraceSource.Listeners%2A> property of the <xref:System.Diagnostics.TraceSource> instance.</span></span>  
  
 <span data-ttu-id="a4b1b-131">Cet élément peut être utilisé dans le fichier de configuration de l’ordinateur (machine. config) et dans le fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="a4b1b-131">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a4b1b-132">Exemple</span><span class="sxs-lookup"><span data-stu-id="a4b1b-132">Example</span></span>  
 <span data-ttu-id="a4b1b-133">L’exemple suivant montre comment utiliser l’élément `<remove>` avant d’utiliser l’élément `<add>` pour ajouter l’écouteur `console` à la collection `Listeners` pour la source de trace `TraceSourceApp`.</span><span class="sxs-lookup"><span data-stu-id="a4b1b-133">The following example shows how to use the `<remove>` element before using the `<add>` element to add the listener `console` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a4b1b-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a4b1b-134">See also</span></span>

- <xref:System.Diagnostics.TraceSource.Listeners%2A>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="a4b1b-135">Schéma des paramètres de trace et de débogage</span><span class="sxs-lookup"><span data-stu-id="a4b1b-135">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="a4b1b-136">\<clear></span><span class="sxs-lookup"><span data-stu-id="a4b1b-136">\<clear></span></span>](clear-element-for-listeners-for-source.md)
- [<span data-ttu-id="a4b1b-137">Écouteurs de suivi</span><span class="sxs-lookup"><span data-stu-id="a4b1b-137">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
