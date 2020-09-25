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
ms.openlocfilehash: 7e249e59423740b36e42f59fae8854412d01a0cc
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173846"
---
# <a name="sharedlisteners-element"></a><span data-ttu-id="eac4b-102">Élément \<sharedListeners></span><span class="sxs-lookup"><span data-stu-id="eac4b-102">\<sharedListeners> Element</span></span>

<span data-ttu-id="eac4b-103">Contient des écouteurs auxquels toute source ou tout élément de trace peuvent faire référence.</span><span class="sxs-lookup"><span data-stu-id="eac4b-103">Contains listeners that any source or trace element can reference.</span></span>  <span data-ttu-id="eac4b-104">Ces écouteurs ne reçoivent pas de suivi par défaut, et il n’est pas possible de récupérer ces écouteurs au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="eac4b-104">These listeners do not receive any traces by default, and it is not possible to retrieve these listeners at run time.</span></span> <span data-ttu-id="eac4b-105">Les écouteurs identifiés comme écouteurs partagés peuvent être ajoutés à des sources ou des suivis par nom.</span><span class="sxs-lookup"><span data-stu-id="eac4b-105">Listeners identified as shared listeners can be added to sources or traces by name.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<sharedListeners>**  
  
## <a name="syntax"></a><span data-ttu-id="eac4b-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eac4b-106">Syntax</span></span>  
  
```xml  
<sharedListeners>
  <add>...</add>  
</sharedListeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eac4b-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="eac4b-107">Attributes and Elements</span></span>  

 <span data-ttu-id="eac4b-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="eac4b-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eac4b-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="eac4b-109">Attributes</span></span>  

 <span data-ttu-id="eac4b-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="eac4b-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="eac4b-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="eac4b-111">Child Elements</span></span>  
  
|<span data-ttu-id="eac4b-112">Élément</span><span class="sxs-lookup"><span data-stu-id="eac4b-112">Element</span></span>|<span data-ttu-id="eac4b-113">Description</span><span class="sxs-lookup"><span data-stu-id="eac4b-113">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-element-for-listeners-for-trace.md)|<span data-ttu-id="eac4b-114">Ajoute un écouteur à la collection `sharedListeners`.</span><span class="sxs-lookup"><span data-stu-id="eac4b-114">Adds a listener to the `sharedListeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="eac4b-115">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="eac4b-115">Parent Elements</span></span>  
  
|<span data-ttu-id="eac4b-116">Élément</span><span class="sxs-lookup"><span data-stu-id="eac4b-116">Element</span></span>|<span data-ttu-id="eac4b-117">Description</span><span class="sxs-lookup"><span data-stu-id="eac4b-117">Description</span></span>|  
|-------------|-----------------|  
|`Configuration`|<span data-ttu-id="eac4b-118">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="eac4b-118">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="eac4b-119">Spécifie l'élément racine de la section de configuration ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="eac4b-119">Specifies the root element for the ASP.NET configuration section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eac4b-120">Notes</span><span class="sxs-lookup"><span data-stu-id="eac4b-120">Remarks</span></span>  

 <span data-ttu-id="eac4b-121">L’ajout d’un écouteur à la collection d’écouteurs partagés ne fait pas de l’écouteur actif.</span><span class="sxs-lookup"><span data-stu-id="eac4b-121">Adding a listener to the shared listeners collection does not make it an active listener.</span></span> <span data-ttu-id="eac4b-122">Il doit toujours être ajouté à une source de suivi ou à une trace en l’ajoutant à la `Listeners` collection de cet élément trace.</span><span class="sxs-lookup"><span data-stu-id="eac4b-122">It must still be added to a trace source or a trace by adding it to the `Listeners` collection for that trace element.</span></span> <span data-ttu-id="eac4b-123">Les classes d’écouteur dans le .NET Framework dérivent de la <xref:System.Diagnostics.TraceListener> classe.</span><span class="sxs-lookup"><span data-stu-id="eac4b-123">The listener classes in the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
 <span data-ttu-id="eac4b-124">Cet élément peut être utilisé dans le fichier de configuration de l’ordinateur (Machine.config) et dans le fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="eac4b-124">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eac4b-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="eac4b-125">Example</span></span>  

 <span data-ttu-id="eac4b-126">L’exemple suivant montre comment utiliser l' `<sharedListeners>` élément pour ajouter l’écouteur `console` à la `Listeners` collection pour les <xref:System.Diagnostics.TraceSource> <xref:System.Diagnostics.Trace> classes et.</span><span class="sxs-lookup"><span data-stu-id="eac4b-126">The following example shows how to use the `<sharedListeners>` element to add the listener `console` to the `Listeners` collection for both the <xref:System.Diagnostics.TraceSource> and <xref:System.Diagnostics.Trace> classes.</span></span> <span data-ttu-id="eac4b-127">L’écouteur de suivi de console écrit les informations de trace dans la console par le biais d’appels à <xref:System.Diagnostics.TraceSource> ou <xref:System.Diagnostics.Trace> .</span><span class="sxs-lookup"><span data-stu-id="eac4b-127">The console trace listener writes trace information to the console through calls to either <xref:System.Diagnostics.TraceSource> or <xref:System.Diagnostics.Trace>.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="eac4b-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eac4b-128">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="eac4b-129">Schéma des paramètres de traçage et de débogage</span><span class="sxs-lookup"><span data-stu-id="eac4b-129">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="eac4b-130">Écouteurs de la trace</span><span class="sxs-lookup"><span data-stu-id="eac4b-130">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
