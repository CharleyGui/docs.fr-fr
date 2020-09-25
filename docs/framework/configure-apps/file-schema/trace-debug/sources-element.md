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
ms.openlocfilehash: 670fb359f892d83feac56c849361c4b980d9a922
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173807"
---
# <a name="sources-element"></a><span data-ttu-id="d49d1-102">Élément \<sources></span><span class="sxs-lookup"><span data-stu-id="d49d1-102">\<sources> Element</span></span>

<span data-ttu-id="d49d1-103">Spécifie les sources de suivi qui initialisent les messages de suivi.</span><span class="sxs-lookup"><span data-stu-id="d49d1-103">Specifies trace sources that initiate tracing messages.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<sources>**

## <a name="syntax"></a><span data-ttu-id="d49d1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d49d1-104">Syntax</span></span>  
  
```xml  
<sources>  
   <source>...</source>  
</sources>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d49d1-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="d49d1-105">Attributes and Elements</span></span>  

 <span data-ttu-id="d49d1-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="d49d1-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d49d1-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="d49d1-107">Attributes</span></span>  

 <span data-ttu-id="d49d1-108">Aucun.</span><span class="sxs-lookup"><span data-stu-id="d49d1-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d49d1-109">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="d49d1-109">Child Elements</span></span>  
  
|<span data-ttu-id="d49d1-110">Élément</span><span class="sxs-lookup"><span data-stu-id="d49d1-110">Element</span></span>|<span data-ttu-id="d49d1-111">Description</span><span class="sxs-lookup"><span data-stu-id="d49d1-111">Description</span></span>|  
|-------------|-----------------|  
|[\<source>](source-element.md)|<span data-ttu-id="d49d1-112">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="d49d1-112">Required element.</span></span><br /><br /> <span data-ttu-id="d49d1-113">Spécifie une source de trace qui lance des messages de traçage.</span><span class="sxs-lookup"><span data-stu-id="d49d1-113">Specifies a trace source that initiates tracing messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d49d1-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="d49d1-114">Parent Elements</span></span>  
  
|<span data-ttu-id="d49d1-115">Élément</span><span class="sxs-lookup"><span data-stu-id="d49d1-115">Element</span></span>|<span data-ttu-id="d49d1-116">Description</span><span class="sxs-lookup"><span data-stu-id="d49d1-116">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="d49d1-117">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d49d1-117">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="d49d1-118">Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.</span><span class="sxs-lookup"><span data-stu-id="d49d1-118">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d49d1-119">Notes</span><span class="sxs-lookup"><span data-stu-id="d49d1-119">Remarks</span></span>  

 <span data-ttu-id="d49d1-120">Cet élément peut être utilisé dans le fichier de configuration de l’ordinateur (Machine.config) et dans le fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="d49d1-120">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d49d1-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="d49d1-121">Example</span></span>  

 <span data-ttu-id="d49d1-122">L’exemple suivant montre comment utiliser l' `<sources>` élément pour ajouter la source de suivi `mySource` et définir le niveau du commutateur source nommé `sourceSwitch` .</span><span class="sxs-lookup"><span data-stu-id="d49d1-122">The following example shows how to use the `<sources>` element to add the trace source `mySource` and to set the level for the source switch named `sourceSwitch`.</span></span> <span data-ttu-id="d49d1-123">Un écouteur de suivi de console est ajouté pour écrire des informations de traçage dans la console.</span><span class="sxs-lookup"><span data-stu-id="d49d1-123">A console trace listener is added that writes trace information to the console.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d49d1-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d49d1-124">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.XmlWriterTraceListener>
- [<span data-ttu-id="d49d1-125">Schéma des paramètres de traçage et de débogage</span><span class="sxs-lookup"><span data-stu-id="d49d1-125">Trace and Debug Settings Schema</span></span>](index.md)
- [\<source>](source-element.md)
