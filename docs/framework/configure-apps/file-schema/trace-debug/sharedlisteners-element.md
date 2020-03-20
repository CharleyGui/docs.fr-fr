---
title: Élément <sharedListeners>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#sharedListeners
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners
helpviewer_keywords:
- <sharedListeners> element
- listeners
- shared listeners
- trace listeners, <sharedListeners> element
- sharedListeners element
ms.assetid: de200534-19dd-4156-86cf-c50521802c4c
ms.openlocfilehash: 69f15cc9583b397017ac30a0c567914495867c18
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153319"
---
# <a name="sharedlisteners-element"></a><span data-ttu-id="b2e6c-102">\<sharedListeners> Element</span><span class="sxs-lookup"><span data-stu-id="b2e6c-102">\<sharedListeners> Element</span></span>
<span data-ttu-id="b2e6c-103">Contient des écouteurs auxquels toute source ou tout élément de trace peuvent faire référence.</span><span class="sxs-lookup"><span data-stu-id="b2e6c-103">Contains listeners that any source or trace element can reference.</span></span>  <span data-ttu-id="b2e6c-104">Ces auditeurs ne reçoivent aucune trace par défaut, et il n’est pas possible de récupérer ces auditeurs au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="b2e6c-104">These listeners do not receive any traces by default, and it is not possible to retrieve these listeners at run time.</span></span> <span data-ttu-id="b2e6c-105">Les auditeurs identifiés comme des auditeurs partagés peuvent être ajoutés à des sources ou des traces par leur nom.</span><span class="sxs-lookup"><span data-stu-id="b2e6c-105">Listeners identified as shared listeners can be added to sources or traces by name.</span></span>  
  
[<span data-ttu-id="b2e6c-106">**\<configuration>**</span><span class="sxs-lookup"><span data-stu-id="b2e6c-106">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="b2e6c-107">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="b2e6c-107">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>  
<span data-ttu-id="b2e6c-108">&nbsp;&nbsp;&nbsp;&nbsp;**\<sharedListeners>**</span><span class="sxs-lookup"><span data-stu-id="b2e6c-108">&nbsp;&nbsp;&nbsp;&nbsp;**\<sharedListeners>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2e6c-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b2e6c-109">Syntax</span></span>  
  
```xml  
<sharedListeners>
  <add>...</add>  
</sharedListeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b2e6c-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="b2e6c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="b2e6c-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="b2e6c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b2e6c-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="b2e6c-112">Attributes</span></span>  
 <span data-ttu-id="b2e6c-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="b2e6c-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b2e6c-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="b2e6c-114">Child Elements</span></span>  
  
|<span data-ttu-id="b2e6c-115">Élément</span><span class="sxs-lookup"><span data-stu-id="b2e6c-115">Element</span></span>|<span data-ttu-id="b2e6c-116">Description</span><span class="sxs-lookup"><span data-stu-id="b2e6c-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b2e6c-117">\<ajouter></span><span class="sxs-lookup"><span data-stu-id="b2e6c-117">\<add></span></span>](add-element-for-listeners-for-trace.md)|<span data-ttu-id="b2e6c-118">Ajoute un écouteur à la collection `sharedListeners`.</span><span class="sxs-lookup"><span data-stu-id="b2e6c-118">Adds a listener to the `sharedListeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b2e6c-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="b2e6c-119">Parent Elements</span></span>  
  
|<span data-ttu-id="b2e6c-120">Élément</span><span class="sxs-lookup"><span data-stu-id="b2e6c-120">Element</span></span>|<span data-ttu-id="b2e6c-121">Description</span><span class="sxs-lookup"><span data-stu-id="b2e6c-121">Description</span></span>|  
|-------------|-----------------|  
|`Configuration`|<span data-ttu-id="b2e6c-122">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b2e6c-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="b2e6c-123">Spécifie l'élément racine de la section de configuration ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="b2e6c-123">Specifies the root element for the ASP.NET configuration section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b2e6c-124">Notes </span><span class="sxs-lookup"><span data-stu-id="b2e6c-124">Remarks</span></span>  
 <span data-ttu-id="b2e6c-125">L’ajout d’un auditeur à la collection d’auditeurs partagés n’en fait pas un auditeur actif.</span><span class="sxs-lookup"><span data-stu-id="b2e6c-125">Adding a listener to the shared listeners collection does not make it an active listener.</span></span> <span data-ttu-id="b2e6c-126">Il doit encore être ajouté à une source de `Listeners` traces ou une trace en l’ajoutant à la collection pour cet élément de trace.</span><span class="sxs-lookup"><span data-stu-id="b2e6c-126">It must still be added to a trace source or a trace by adding it to the `Listeners` collection for that trace element.</span></span> <span data-ttu-id="b2e6c-127">Les cours d’auditeur dans le <xref:System.Diagnostics.TraceListener> cadre .NET dérivent de la classe.</span><span class="sxs-lookup"><span data-stu-id="b2e6c-127">The listener classes in the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
 <span data-ttu-id="b2e6c-128">Cet élément peut être utilisé dans le fichier de configuration de la machine (Machine.config) et le fichier de configuration d’application.</span><span class="sxs-lookup"><span data-stu-id="b2e6c-128">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b2e6c-129"> Exemple</span><span class="sxs-lookup"><span data-stu-id="b2e6c-129">Example</span></span>  
 <span data-ttu-id="b2e6c-130">L’exemple suivant montre `<sharedListeners>` comment utiliser l’élément pour ajouter `console` l’auditeur à la `Listeners` collection pour les <xref:System.Diagnostics.TraceSource> classes et <xref:System.Diagnostics.Trace> les classes.</span><span class="sxs-lookup"><span data-stu-id="b2e6c-130">The following example shows how to use the `<sharedListeners>` element to add the listener `console` to the `Listeners` collection for both the <xref:System.Diagnostics.TraceSource> and <xref:System.Diagnostics.Trace> classes.</span></span> <span data-ttu-id="b2e6c-131">L’auditeur de trace de console écrit des <xref:System.Diagnostics.TraceSource> <xref:System.Diagnostics.Trace>informations trace à la console par des appels à l’un ou l’autre ou .</span><span class="sxs-lookup"><span data-stu-id="b2e6c-131">The console trace listener writes trace information to the console through calls to either <xref:System.Diagnostics.TraceSource> or <xref:System.Diagnostics.Trace>.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sharedListeners>  
      <add name="console" type="System.Diagnostics.ConsoleTraceListener" >  
        <filter type="System.Diagnostics.EventTypeFilter"  
          initializeData="Warning" />  
      </add>  
    </sharedListeners>  
    <sources>  
      <source name="mySource" switchName="sourceSwitch"  >  
        <listeners>  
          <add name="console" />  
        </listeners>  
      </source>  
    </sources>  
    <switches>  
      <add name="sourceSwitch" value="Verbose"/>  
    </switches>  
    <trace>  
      <listeners>  
        <add name="console" />  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="b2e6c-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b2e6c-132">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="b2e6c-133">Trace et Debug Paramètres Schema</span><span class="sxs-lookup"><span data-stu-id="b2e6c-133">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="b2e6c-134">Écouteurs de suivi</span><span class="sxs-lookup"><span data-stu-id="b2e6c-134">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
