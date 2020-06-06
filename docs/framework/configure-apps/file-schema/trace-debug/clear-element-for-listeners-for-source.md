---
title: <clear>, Élément de <listeners> pour<source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/clear
helpviewer_keywords:
- <clear> element for <listeners> for <source>
- clear element for <listeners> for <source>
ms.assetid: 76796bb2-9c0b-4526-8135-8bf18b16d8d9
ms.openlocfilehash: 7f9ddd93d27c3619119702c82c9e8752dab1af7b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153579"
---
# <a name="clear-element-for-listeners-for-source"></a><span data-ttu-id="f4294-102">\<clear>, Élément de \<listeners> pour\<source></span><span class="sxs-lookup"><span data-stu-id="f4294-102">\<clear> Element for \<listeners> for \<source></span></span>
<span data-ttu-id="f4294-103">Efface la collection `Listeners` pour une source de trace.</span><span class="sxs-lookup"><span data-stu-id="f4294-103">Clears the `Listeners` collection for a trace source.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-source.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="f4294-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f4294-104">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f4294-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="f4294-105">Attributes and Elements</span></span>  
 <span data-ttu-id="f4294-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="f4294-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f4294-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="f4294-107">Attributes</span></span>  
 <span data-ttu-id="f4294-108">Aucun.</span><span class="sxs-lookup"><span data-stu-id="f4294-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f4294-109">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="f4294-109">Child Elements</span></span>  
 <span data-ttu-id="f4294-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="f4294-110">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f4294-111">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="f4294-111">Parent Elements</span></span>  
  
|<span data-ttu-id="f4294-112">Élément</span><span class="sxs-lookup"><span data-stu-id="f4294-112">Element</span></span>|<span data-ttu-id="f4294-113">Description</span><span class="sxs-lookup"><span data-stu-id="f4294-113">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="f4294-114">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f4294-114">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="f4294-115">Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.</span><span class="sxs-lookup"><span data-stu-id="f4294-115">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="f4294-116">Contient les sources de trace qui lancent des messages de traçage.</span><span class="sxs-lookup"><span data-stu-id="f4294-116">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="f4294-117">Spécifie une source de trace qui lance des messages de traçage.</span><span class="sxs-lookup"><span data-stu-id="f4294-117">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="f4294-118">Spécifie les écouteurs qui collectent, stockent et acheminent les messages.</span><span class="sxs-lookup"><span data-stu-id="f4294-118">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f4294-119">Remarques</span><span class="sxs-lookup"><span data-stu-id="f4294-119">Remarks</span></span>  
 <span data-ttu-id="f4294-120">L' `<clear>` élément supprime tous les écouteurs de la `Listeners` collection pour une source de suivi, y compris <xref:System.Diagnostics.DefaultTraceListener> .</span><span class="sxs-lookup"><span data-stu-id="f4294-120">The `<clear>` element removes all listeners from the `Listeners` collection for a trace source, including the <xref:System.Diagnostics.DefaultTraceListener>.</span></span> <span data-ttu-id="f4294-121">Vous pouvez utiliser l' `<clear>` élément avant d’utiliser l' `<add>` élément pour être certain qu’il n’existe aucun autre écouteur actif dans la collection.</span><span class="sxs-lookup"><span data-stu-id="f4294-121">You can use the `<clear>` element before using the `<add>` element to be certain there are no other active listeners in the collection.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="f4294-122">Fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="f4294-122">Configuration File</span></span>  
 <span data-ttu-id="f4294-123">Cet élément peut être utilisé dans le fichier de configuration de l’ordinateur (machine. config) et dans le fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="f4294-123">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f4294-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="f4294-124">Example</span></span>  
 <span data-ttu-id="f4294-125">L’exemple suivant montre comment utiliser l' `<clear>` élément avant d’utiliser les `<add>` éléments pour ajouter les écouteurs `console` et `textListener` la `Listeners` collection pour la source de trace `TraceSourceApp` .</span><span class="sxs-lookup"><span data-stu-id="f4294-125">The following example shows how to use the `<clear>` element before using the `<add>` elements to add the listeners `console` and `textListener` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f4294-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f4294-126">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="f4294-127">Schéma des paramètres de traçage et de débogage</span><span class="sxs-lookup"><span data-stu-id="f4294-127">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="f4294-128">Écouteurs de suivi</span><span class="sxs-lookup"><span data-stu-id="f4294-128">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
