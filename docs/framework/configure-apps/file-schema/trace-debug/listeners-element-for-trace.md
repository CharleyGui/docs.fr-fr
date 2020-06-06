---
title: Élément <listeners> pour <trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners
helpviewer_keywords:
- <listeners> element
- listeners element
ms.assetid: 1394c2c3-6304-46db-87c1-8e8b16f5ad5b
ms.openlocfilehash: fd12be1b775d7611ef3f16d23147470313bf9866
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153371"
---
# <a name="listeners-element-for-trace"></a><span data-ttu-id="2f3b9-102">\<listeners>, élément de \<trace></span><span class="sxs-lookup"><span data-stu-id="2f3b9-102">\<listeners> Element for \<trace></span></span>
<span data-ttu-id="2f3b9-103">Spécifie un écouteur qui collecte, stocke et achemine des messages.</span><span class="sxs-lookup"><span data-stu-id="2f3b9-103">Specifies a listener that collects, stores, and routes messages.</span></span> <span data-ttu-id="2f3b9-104">Les écouteurs dirigent la sortie de suivi vers une cible appropriée.</span><span class="sxs-lookup"><span data-stu-id="2f3b9-104">Listeners direct the tracing output to an appropriate target.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<listeners>**

## <a name="syntax"></a><span data-ttu-id="2f3b9-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2f3b9-105">Syntax</span></span>  
  
```xml  
<listeners>
  <add>...</add>  
  <clear/>  
  <remove ... />  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2f3b9-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="2f3b9-106">Attributes and Elements</span></span>  
 <span data-ttu-id="2f3b9-107">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="2f3b9-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2f3b9-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="2f3b9-108">Attributes</span></span>  
 <span data-ttu-id="2f3b9-109">Aucun.</span><span class="sxs-lookup"><span data-stu-id="2f3b9-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="2f3b9-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="2f3b9-110">Child Elements</span></span>  
  
|<span data-ttu-id="2f3b9-111">Élément</span><span class="sxs-lookup"><span data-stu-id="2f3b9-111">Element</span></span>|<span data-ttu-id="2f3b9-112">Description</span><span class="sxs-lookup"><span data-stu-id="2f3b9-112">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-element-for-listeners-for-trace.md)|<span data-ttu-id="2f3b9-113">Ajoute un écouteur à la collection `Listeners`.</span><span class="sxs-lookup"><span data-stu-id="2f3b9-113">Adds a listener to the `Listeners` collection.</span></span>|  
|[\<clear>](clear-element-for-listeners-for-trace.md)|<span data-ttu-id="2f3b9-114">Efface la collection `Listeners` de la trace.</span><span class="sxs-lookup"><span data-stu-id="2f3b9-114">Clears the `Listeners` collection for trace.</span></span>|  
|[\<remove>](remove-element-for-listeners-for-trace.md)|<span data-ttu-id="2f3b9-115">Supprime un écouteur de la `Listeners` collection.</span><span class="sxs-lookup"><span data-stu-id="2f3b9-115">Removes a listener from the `Listeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2f3b9-116">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="2f3b9-116">Parent Elements</span></span>  
  
|<span data-ttu-id="2f3b9-117">Élément</span><span class="sxs-lookup"><span data-stu-id="2f3b9-117">Element</span></span>|<span data-ttu-id="2f3b9-118">Description</span><span class="sxs-lookup"><span data-stu-id="2f3b9-118">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="2f3b9-119">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2f3b9-119">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="2f3b9-120">Spécifie l'élément racine de la section de configuration ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="2f3b9-120">Specifies the root element for the ASP.NET configuration section.</span></span>|  
|`trace`|<span data-ttu-id="2f3b9-121">Contient les écouteurs qui collectent, stockent et acheminent les messages de traçage.</span><span class="sxs-lookup"><span data-stu-id="2f3b9-121">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2f3b9-122">Remarques</span><span class="sxs-lookup"><span data-stu-id="2f3b9-122">Remarks</span></span>  
 <span data-ttu-id="2f3b9-123">Les <xref:System.Diagnostics.Debug> <xref:System.Diagnostics.Trace> classes et partagent la même collection d' **écouteurs** .</span><span class="sxs-lookup"><span data-stu-id="2f3b9-123">The <xref:System.Diagnostics.Debug> and <xref:System.Diagnostics.Trace> classes share the same **Listeners** collection.</span></span> <span data-ttu-id="2f3b9-124">Si vous ajoutez un objet écouteur à la collection dans l’une de ces classes, l’autre classe utilise le même écouteur.</span><span class="sxs-lookup"><span data-stu-id="2f3b9-124">If you add a listener object to the collection in one of these classes, the other class uses the same listener.</span></span> <span data-ttu-id="2f3b9-125">Les classes d’écouteur fournies avec le .NET Framework dérivent de la <xref:System.Diagnostics.TraceListener> classe.</span><span class="sxs-lookup"><span data-stu-id="2f3b9-125">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="2f3b9-126">Fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="2f3b9-126">Configuration File</span></span>  
 <span data-ttu-id="2f3b9-127">Cet élément peut être utilisé dans le fichier de configuration de l’ordinateur (machine. config) et dans le fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="2f3b9-127">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2f3b9-128">Exemple</span><span class="sxs-lookup"><span data-stu-id="2f3b9-128">Example</span></span>  
 <span data-ttu-id="2f3b9-129">L’exemple suivant montre comment utiliser l' **\<listeners>** élément pour ajouter les écouteurs `MyListener` et `MyEventListener` la collection d' **écouteurs** .</span><span class="sxs-lookup"><span data-stu-id="2f3b9-129">The following example shows how to use the **\<listeners>** element to add the listeners `MyListener` and `MyEventListener` to the **Listeners** collection.</span></span> <span data-ttu-id="2f3b9-130">`MyListener`crée un fichier appelé `MyListener.log` et écrit la sortie dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="2f3b9-130">`MyListener` creates a file called `MyListener.log` and writes the output to the file.</span></span> <span data-ttu-id="2f3b9-131">`MyEventListener`crée une entrée dans le journal des événements.</span><span class="sxs-lookup"><span data-stu-id="2f3b9-131">`MyEventListener` creates an entry in the event log.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <trace autoflush="true" indentsize="0">  
      <listeners>  
        <add name="myListener"
          type="System.Diagnostics.TextWriterTraceListener,
            system, version=1.0.3300.0, Culture=neutral,
            PublicKeyToken=b77a5c561934e089"
          initializeData="c:\myListener.log" />  
        <add name="MyEventListener"  
          type="System.Diagnostics.EventLogTraceListener,
            system, version=1.0.3300.0, Culture=neutral,
            PublicKeyToken=b77a5c561934e089"  
          initializeData="MyConfigEventLog"/>  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2f3b9-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2f3b9-132">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="2f3b9-133">Schéma des paramètres de traçage et de débogage</span><span class="sxs-lookup"><span data-stu-id="2f3b9-133">Trace and Debug Settings Schema</span></span>](index.md)
