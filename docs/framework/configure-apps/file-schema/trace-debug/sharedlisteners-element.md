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
ms.openlocfilehash: b419ecf451b79808e545525c7b8761175f390200
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699301"
---
# <a name="sharedlisteners-element"></a><span data-ttu-id="59292-102">Élément \<sharedListeners ></span><span class="sxs-lookup"><span data-stu-id="59292-102">\<sharedListeners> Element</span></span>
<span data-ttu-id="59292-103">Contient des écouteurs auxquels toute source ou tout élément de trace peuvent faire référence.</span><span class="sxs-lookup"><span data-stu-id="59292-103">Contains listeners that any source or trace element can reference.</span></span>  <span data-ttu-id="59292-104">Ces écouteurs ne reçoivent pas de suivi par défaut, et il n’est pas possible de récupérer ces écouteurs au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="59292-104">These listeners do not receive any traces by default, and it is not possible to retrieve these listeners at run time.</span></span> <span data-ttu-id="59292-105">Les écouteurs identifiés comme écouteurs partagés peuvent être ajoutés à des sources ou des suivis par nom.</span><span class="sxs-lookup"><span data-stu-id="59292-105">Listeners identified as shared listeners can be added to sources or traces by name.</span></span>  
  
[<span data-ttu-id="59292-106"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="59292-106">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="59292-107">&nbsp;&nbsp;[ **\<System. diagnostics >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="59292-107">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>  
<span data-ttu-id="59292-108">&nbsp;&nbsp;&nbsp;&nbsp; **\<sharedListeners >**</span><span class="sxs-lookup"><span data-stu-id="59292-108">&nbsp;&nbsp;&nbsp;&nbsp;**\<sharedListeners>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59292-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="59292-109">Syntax</span></span>  
  
```xml  
<sharedListeners>   
  <add>...</add>  
</sharedListeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="59292-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="59292-110">Attributes and Elements</span></span>  
 <span data-ttu-id="59292-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="59292-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="59292-112">Attributes</span><span class="sxs-lookup"><span data-stu-id="59292-112">Attributes</span></span>  
 <span data-ttu-id="59292-113">Aucune.</span><span class="sxs-lookup"><span data-stu-id="59292-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="59292-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="59292-114">Child Elements</span></span>  
  
|<span data-ttu-id="59292-115">Élément</span><span class="sxs-lookup"><span data-stu-id="59292-115">Element</span></span>|<span data-ttu-id="59292-116">Description</span><span class="sxs-lookup"><span data-stu-id="59292-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="59292-117">\<add></span><span class="sxs-lookup"><span data-stu-id="59292-117">\<add></span></span>](add-element-for-listeners-for-trace.md)|<span data-ttu-id="59292-118">Ajoute un écouteur à la collection `sharedListeners`.</span><span class="sxs-lookup"><span data-stu-id="59292-118">Adds a listener to the `sharedListeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="59292-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="59292-119">Parent Elements</span></span>  
  
|<span data-ttu-id="59292-120">Élément</span><span class="sxs-lookup"><span data-stu-id="59292-120">Element</span></span>|<span data-ttu-id="59292-121">Description</span><span class="sxs-lookup"><span data-stu-id="59292-121">Description</span></span>|  
|-------------|-----------------|  
|`Configuration`|<span data-ttu-id="59292-122">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="59292-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="59292-123">Spécifie l'élément racine de la section de configuration ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="59292-123">Specifies the root element for the ASP.NET configuration section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="59292-124">Remarques</span><span class="sxs-lookup"><span data-stu-id="59292-124">Remarks</span></span>  
 <span data-ttu-id="59292-125">L’ajout d’un écouteur à la collection d’écouteurs partagés ne fait pas de l’écouteur actif.</span><span class="sxs-lookup"><span data-stu-id="59292-125">Adding a listener to the shared listeners collection does not make it an active listener.</span></span> <span data-ttu-id="59292-126">Il doit toujours être ajouté à une source de suivi ou à une trace en l’ajoutant à la collection `Listeners` pour cet élément trace.</span><span class="sxs-lookup"><span data-stu-id="59292-126">It must still be added to a trace source or a trace by adding it to the `Listeners` collection for that trace element.</span></span> <span data-ttu-id="59292-127">Les classes d’écouteur dans le .NET Framework dérivent de la classe <xref:System.Diagnostics.TraceListener>.</span><span class="sxs-lookup"><span data-stu-id="59292-127">The listener classes in the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
 <span data-ttu-id="59292-128">Cet élément peut être utilisé dans le fichier de configuration de l’ordinateur (machine. config) et dans le fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="59292-128">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="59292-129">Exemple</span><span class="sxs-lookup"><span data-stu-id="59292-129">Example</span></span>  
 <span data-ttu-id="59292-130">L’exemple suivant montre comment utiliser l’élément `<sharedListeners>` pour ajouter l’écouteur `console` à la collection `Listeners` pour les classes <xref:System.Diagnostics.TraceSource> et <xref:System.Diagnostics.Trace>.</span><span class="sxs-lookup"><span data-stu-id="59292-130">The following example shows how to use the `<sharedListeners>` element to add the listener `console` to the `Listeners` collection for both the <xref:System.Diagnostics.TraceSource> and <xref:System.Diagnostics.Trace> classes.</span></span> <span data-ttu-id="59292-131">L’écouteur de suivi de console écrit les informations de trace dans la console par le biais d’appels à <xref:System.Diagnostics.TraceSource> ou <xref:System.Diagnostics.Trace>.</span><span class="sxs-lookup"><span data-stu-id="59292-131">The console trace listener writes trace information to the console through calls to either <xref:System.Diagnostics.TraceSource> or <xref:System.Diagnostics.Trace>.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="59292-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="59292-132">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="59292-133">Schéma des paramètres de trace et de débogage</span><span class="sxs-lookup"><span data-stu-id="59292-133">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="59292-134">Écouteurs de suivi</span><span class="sxs-lookup"><span data-stu-id="59292-134">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
