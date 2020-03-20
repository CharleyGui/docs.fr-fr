---
title: <remove>Élément <listeners> pour pour<source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/remove
helpviewer_keywords:
- remove element for <listeners> for <source>
- <remove> element for <listeners> for <source>
ms.assetid: 3ff6b578-273d-407f-b07f-8251f1f9f5d0
ms.openlocfilehash: 657e6db2af9b99b3bbf03afc6aab02c58a830f2d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153333"
---
# <a name="remove-element-for-listeners-for-source"></a><span data-ttu-id="e2cdc-102">\<supprimer> Élément pour \<les auditeurs \<> pour les> de source</span><span class="sxs-lookup"><span data-stu-id="e2cdc-102">\<remove> Element for \<listeners> for \<source></span></span>
<span data-ttu-id="e2cdc-103">Supprime un écouteur de la collection `Listeners` pour une source de trace.</span><span class="sxs-lookup"><span data-stu-id="e2cdc-103">Removes a listener from the `Listeners` collection for a trace source.</span></span>  

<span data-ttu-id="e2cdc-104">[**\<configuration>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e2cdc-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e2cdc-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="e2cdc-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="e2cdc-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)</span><span class="sxs-lookup"><span data-stu-id="e2cdc-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)</span></span>\
<span data-ttu-id="e2cdc-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)</span><span class="sxs-lookup"><span data-stu-id="e2cdc-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)</span></span>\
<span data-ttu-id="e2cdc-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<auditeurs>**](listeners-element-for-source.md)</span><span class="sxs-lookup"><span data-stu-id="e2cdc-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-source.md)</span></span>\
<span data-ttu-id="e2cdc-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<supprimer>**</span><span class="sxs-lookup"><span data-stu-id="e2cdc-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="e2cdc-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e2cdc-110">Syntax</span></span>  
  
```xml  
<remove name="listenerName" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e2cdc-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e2cdc-111">Attributes and Elements</span></span>  
 <span data-ttu-id="e2cdc-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="e2cdc-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e2cdc-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="e2cdc-113">Attributes</span></span>  
  
|<span data-ttu-id="e2cdc-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="e2cdc-114">Attribute</span></span>|<span data-ttu-id="e2cdc-115">Description</span><span class="sxs-lookup"><span data-stu-id="e2cdc-115">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="e2cdc-116">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="e2cdc-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="e2cdc-117">Le nom de l’auditeur `Listeners` à retirer de la collection.</span><span class="sxs-lookup"><span data-stu-id="e2cdc-117">The name of the listener to remove from the `Listeners` collection.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e2cdc-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e2cdc-118">Child Elements</span></span>  
 <span data-ttu-id="e2cdc-119">Aucun.</span><span class="sxs-lookup"><span data-stu-id="e2cdc-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e2cdc-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e2cdc-120">Parent Elements</span></span>  
  
|<span data-ttu-id="e2cdc-121">Élément</span><span class="sxs-lookup"><span data-stu-id="e2cdc-121">Element</span></span>|<span data-ttu-id="e2cdc-122">Description</span><span class="sxs-lookup"><span data-stu-id="e2cdc-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="e2cdc-123">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e2cdc-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="e2cdc-124">Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.</span><span class="sxs-lookup"><span data-stu-id="e2cdc-124">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="e2cdc-125">Contient les sources de trace qui lancent des messages de traçage.</span><span class="sxs-lookup"><span data-stu-id="e2cdc-125">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="e2cdc-126">Spécifie une source de trace qui lance des messages de traçage.</span><span class="sxs-lookup"><span data-stu-id="e2cdc-126">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="e2cdc-127">Spécifie les auditeurs qui recueillent, stockent et acheminent les messages.</span><span class="sxs-lookup"><span data-stu-id="e2cdc-127">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e2cdc-128">Notes </span><span class="sxs-lookup"><span data-stu-id="e2cdc-128">Remarks</span></span>  
 <span data-ttu-id="e2cdc-129">L’élément `<remove>` supprime un auditeur `Listeners` spécifié de la collection pour une source de traces.</span><span class="sxs-lookup"><span data-stu-id="e2cdc-129">The `<remove>` element removes a specified listener from the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="e2cdc-130">Vous pouvez supprimer un `Listeners` élément de la collection pour <xref:System.Diagnostics.TraceListenerCollection.Remove%2A> une source <xref:System.Diagnostics.TraceSource.Listeners%2A> de <xref:System.Diagnostics.TraceSource> traces programmatiquement en appelant la méthode sur la propriété de l’instance.</span><span class="sxs-lookup"><span data-stu-id="e2cdc-130">You can remove an element from the `Listeners` collection for a trace source programmatically by calling the <xref:System.Diagnostics.TraceListenerCollection.Remove%2A> method on the <xref:System.Diagnostics.TraceSource.Listeners%2A> property of the <xref:System.Diagnostics.TraceSource> instance.</span></span>  
  
 <span data-ttu-id="e2cdc-131">Cet élément peut être utilisé dans le fichier de configuration de la machine (Machine.config) et le fichier de configuration d’application.</span><span class="sxs-lookup"><span data-stu-id="e2cdc-131">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e2cdc-132"> Exemple</span><span class="sxs-lookup"><span data-stu-id="e2cdc-132">Example</span></span>  
 <span data-ttu-id="e2cdc-133">L’exemple suivant montre `<remove>` comment utiliser `<add>` l’élément avant `console` d’utiliser l’élément pour ajouter l’auditeur à la `Listeners` collection pour la source `TraceSourceApp`de traces .</span><span class="sxs-lookup"><span data-stu-id="e2cdc-133">The following example shows how to use the `<remove>` element before using the `<add>` element to add the listener `console` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e2cdc-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e2cdc-134">See also</span></span>

- <xref:System.Diagnostics.TraceSource.Listeners%2A>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="e2cdc-135">Trace et Debug Paramètres Schema</span><span class="sxs-lookup"><span data-stu-id="e2cdc-135">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="e2cdc-136">\<clair></span><span class="sxs-lookup"><span data-stu-id="e2cdc-136">\<clear></span></span>](clear-element-for-listeners-for-source.md)
- [<span data-ttu-id="e2cdc-137">Écouteurs de suivi</span><span class="sxs-lookup"><span data-stu-id="e2cdc-137">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
