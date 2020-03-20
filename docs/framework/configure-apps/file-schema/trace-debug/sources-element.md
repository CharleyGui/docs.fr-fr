---
title: Élément <sources>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources
- http://schemas.microsoft.com/.NetConfiguration/v2.0#sources
helpviewer_keywords:
- sources element
- trace sources
- <sources> element
ms.assetid: c727b2e2-423a-4463-a223-013f40ff16a3
ms.openlocfilehash: 2a76816ee73f516b3c7544877a77531acaa8e09c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153267"
---
# <a name="sources-element"></a><span data-ttu-id="16eb0-102">\<sources> Element</span><span class="sxs-lookup"><span data-stu-id="16eb0-102">\<sources> Element</span></span>
<span data-ttu-id="16eb0-103">Spécifie les sources de traces qui déclenchent des messages de traçage.</span><span class="sxs-lookup"><span data-stu-id="16eb0-103">Specifies trace sources that initiate tracing messages.</span></span>  

<span data-ttu-id="16eb0-104">[**\<configuration>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="16eb0-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="16eb0-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="16eb0-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="16eb0-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<sources>**</span><span class="sxs-lookup"><span data-stu-id="16eb0-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<sources>**</span></span>

## <a name="syntax"></a><span data-ttu-id="16eb0-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="16eb0-107">Syntax</span></span>  
  
```xml  
<sources>  
   <source>...</source>  
</sources>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="16eb0-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="16eb0-108">Attributes and Elements</span></span>  
 <span data-ttu-id="16eb0-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="16eb0-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="16eb0-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="16eb0-110">Attributes</span></span>  
 <span data-ttu-id="16eb0-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="16eb0-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="16eb0-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="16eb0-112">Child Elements</span></span>  
  
|<span data-ttu-id="16eb0-113">Élément</span><span class="sxs-lookup"><span data-stu-id="16eb0-113">Element</span></span>|<span data-ttu-id="16eb0-114">Description</span><span class="sxs-lookup"><span data-stu-id="16eb0-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="16eb0-115">\<source></span><span class="sxs-lookup"><span data-stu-id="16eb0-115">\<source></span></span>](source-element.md)|<span data-ttu-id="16eb0-116">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="16eb0-116">Required element.</span></span><br /><br /> <span data-ttu-id="16eb0-117">Spécifie une source de trace qui lance des messages de traçage.</span><span class="sxs-lookup"><span data-stu-id="16eb0-117">Specifies a trace source that initiates tracing messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="16eb0-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="16eb0-118">Parent Elements</span></span>  
  
|<span data-ttu-id="16eb0-119">Élément</span><span class="sxs-lookup"><span data-stu-id="16eb0-119">Element</span></span>|<span data-ttu-id="16eb0-120">Description</span><span class="sxs-lookup"><span data-stu-id="16eb0-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="16eb0-121">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="16eb0-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="16eb0-122">Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.</span><span class="sxs-lookup"><span data-stu-id="16eb0-122">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="16eb0-123">Notes </span><span class="sxs-lookup"><span data-stu-id="16eb0-123">Remarks</span></span>  
 <span data-ttu-id="16eb0-124">Cet élément peut être utilisé dans le fichier de configuration de la machine (Machine.config) et le fichier de configuration d’application.</span><span class="sxs-lookup"><span data-stu-id="16eb0-124">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="16eb0-125"> Exemple</span><span class="sxs-lookup"><span data-stu-id="16eb0-125">Example</span></span>  
 <span data-ttu-id="16eb0-126">L’exemple suivant montre `<sources>` comment utiliser l’élément pour ajouter la source `mySource` `sourceSwitch`de trace et pour définir le niveau pour le commutateur source nommé .</span><span class="sxs-lookup"><span data-stu-id="16eb0-126">The following example shows how to use the `<sources>` element to add the trace source `mySource` and to set the level for the source switch named `sourceSwitch`.</span></span> <span data-ttu-id="16eb0-127">Un auditeur de trace de console est ajouté qui écrit des informations de trace à la console.</span><span class="sxs-lookup"><span data-stu-id="16eb0-127">A console trace listener is added that writes trace information to the console.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <sources>  
         <source name="mySource" switchName="sourceSwitch"
            switchType="System.Diagnostics.SourceSwitch"  >  
            <listeners>  
               <add name="console"
                  type="System.Diagnostics.ConsoleTraceListener" >  
                  <filter type="System.Diagnostics.EventTypeFilter"
                     initializeData="Error" />  
               </add>  
               <remove name="Default" />  
            </listeners>  
         </source>  
      </sources>  
      <switches>  
         <add name="sourceSwitch" value="Warning" />  
      </switches>
   </system.diagnostics>
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="16eb0-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="16eb0-128">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.XmlWriterTraceListener>
- [<span data-ttu-id="16eb0-129">Trace et Debug Paramètres Schema</span><span class="sxs-lookup"><span data-stu-id="16eb0-129">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="16eb0-130">\<source></span><span class="sxs-lookup"><span data-stu-id="16eb0-130">\<source></span></span>](source-element.md)
