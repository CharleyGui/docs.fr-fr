---
title: <clear> , Élément de <listeners> pour <source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/clear
helpviewer_keywords:
- <clear> element for <listeners> for <source>
- clear element for <listeners> for <source>
ms.assetid: 76796bb2-9c0b-4526-8135-8bf18b16d8d9
ms.openlocfilehash: d3e76496c82b508feabf8a46cf7bce7e3d54e8cf
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91149281"
---
# <a name="clear-element-for-listeners-for-source"></a><span data-ttu-id="e4eb5-102">\<clear> , Élément de \<listeners> pour \<source></span><span class="sxs-lookup"><span data-stu-id="e4eb5-102">\<clear> Element for \<listeners> for \<source></span></span>

<span data-ttu-id="e4eb5-103">Efface la collection `Listeners` pour une source de trace.</span><span class="sxs-lookup"><span data-stu-id="e4eb5-103">Clears the `Listeners` collection for a trace source.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-source.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="e4eb5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e4eb5-104">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e4eb5-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e4eb5-105">Attributes and Elements</span></span>  

 <span data-ttu-id="e4eb5-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="e4eb5-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e4eb5-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="e4eb5-107">Attributes</span></span>  

 <span data-ttu-id="e4eb5-108">Aucun.</span><span class="sxs-lookup"><span data-stu-id="e4eb5-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e4eb5-109">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e4eb5-109">Child Elements</span></span>  

 <span data-ttu-id="e4eb5-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="e4eb5-110">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e4eb5-111">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e4eb5-111">Parent Elements</span></span>  
  
|<span data-ttu-id="e4eb5-112">Élément</span><span class="sxs-lookup"><span data-stu-id="e4eb5-112">Element</span></span>|<span data-ttu-id="e4eb5-113">Description</span><span class="sxs-lookup"><span data-stu-id="e4eb5-113">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="e4eb5-114">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e4eb5-114">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="e4eb5-115">Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.</span><span class="sxs-lookup"><span data-stu-id="e4eb5-115">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="e4eb5-116">Contient les sources de trace qui lancent des messages de traçage.</span><span class="sxs-lookup"><span data-stu-id="e4eb5-116">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="e4eb5-117">Spécifie une source de trace qui lance des messages de traçage.</span><span class="sxs-lookup"><span data-stu-id="e4eb5-117">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="e4eb5-118">Spécifie les écouteurs qui collectent, stockent et acheminent les messages.</span><span class="sxs-lookup"><span data-stu-id="e4eb5-118">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e4eb5-119">Notes</span><span class="sxs-lookup"><span data-stu-id="e4eb5-119">Remarks</span></span>  

 <span data-ttu-id="e4eb5-120">L' `<clear>` élément supprime tous les écouteurs de la `Listeners` collection pour une source de suivi, y compris <xref:System.Diagnostics.DefaultTraceListener> .</span><span class="sxs-lookup"><span data-stu-id="e4eb5-120">The `<clear>` element removes all listeners from the `Listeners` collection for a trace source, including the <xref:System.Diagnostics.DefaultTraceListener>.</span></span> <span data-ttu-id="e4eb5-121">Vous pouvez utiliser l' `<clear>` élément avant d’utiliser l' `<add>` élément pour être certain qu’il n’existe aucun autre écouteur actif dans la collection.</span><span class="sxs-lookup"><span data-stu-id="e4eb5-121">You can use the `<clear>` element before using the `<add>` element to be certain there are no other active listeners in the collection.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="e4eb5-122">Fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="e4eb5-122">Configuration File</span></span>  

 <span data-ttu-id="e4eb5-123">Cet élément peut être utilisé dans le fichier de configuration de l’ordinateur (Machine.config) et dans le fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="e4eb5-123">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e4eb5-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="e4eb5-124">Example</span></span>  

 <span data-ttu-id="e4eb5-125">L’exemple suivant montre comment utiliser l' `<clear>` élément avant d’utiliser les `<add>` éléments pour ajouter les écouteurs `console` et `textListener` la `Listeners` collection pour la source de trace `TraceSourceApp` .</span><span class="sxs-lookup"><span data-stu-id="e4eb5-125">The following example shows how to use the `<clear>` element before using the `<add>` elements to add the listeners `console` and `textListener` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
       <source name="TraceSourceApp" switchName="sourceSwitch"
         switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <clear/>  
          <add name="console"
            type="System.Diagnostics.ConsoleTraceListener"/>  
          <add name="textListener"/>  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add name="textListener"
        type="System.Diagnostics.TextWriterTraceListener"
        initializeData="myListener.log"/>  
    </sharedListeners>  
    <switches>  
      <add name="sourceSwitch" value="Warning"/>  
    </switches>  
  </system.diagnostics>  
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="e4eb5-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e4eb5-126">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="e4eb5-127">Schéma des paramètres de traçage et de débogage</span><span class="sxs-lookup"><span data-stu-id="e4eb5-127">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="e4eb5-128">Écouteurs de la trace</span><span class="sxs-lookup"><span data-stu-id="e4eb5-128">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
