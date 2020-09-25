---
title: Élément <switches>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/switches
- http://schemas.microsoft.com/.NetConfiguration/v2.0#switches
helpviewer_keywords:
- <switches> element
- switches element
- trace switches, <switches> element
ms.assetid: 4cf36786-b89a-40e2-a0f1-86bb9b783343
ms.openlocfilehash: bdd6efdec1e118075495002509c7367c1162baba
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91176095"
---
# <a name="switches-element"></a><span data-ttu-id="b8ffb-102">Élément \<switches></span><span class="sxs-lookup"><span data-stu-id="b8ffb-102">\<switches> Element</span></span>

<span data-ttu-id="b8ffb-103">Contient des commutateurs de traçage et le niveau auquel ils sont définis.</span><span class="sxs-lookup"><span data-stu-id="b8ffb-103">Contains trace switches and the level where the trace switches are set.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<switches>**

## <a name="syntax"></a><span data-ttu-id="b8ffb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b8ffb-104">Syntax</span></span>  
  
```xml  
      <switches>
</switches>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b8ffb-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="b8ffb-105">Attributes and Elements</span></span>  

 <span data-ttu-id="b8ffb-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="b8ffb-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b8ffb-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="b8ffb-107">Attributes</span></span>  

 <span data-ttu-id="b8ffb-108">Aucun.</span><span class="sxs-lookup"><span data-stu-id="b8ffb-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b8ffb-109">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="b8ffb-109">Child Elements</span></span>  
  
|<span data-ttu-id="b8ffb-110">Élément</span><span class="sxs-lookup"><span data-stu-id="b8ffb-110">Element</span></span>|<span data-ttu-id="b8ffb-111">Description</span><span class="sxs-lookup"><span data-stu-id="b8ffb-111">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-element-for-switches.md)|<span data-ttu-id="b8ffb-112">Spécifie le niveau auquel un commutateur de trace est défini.</span><span class="sxs-lookup"><span data-stu-id="b8ffb-112">Specifies the level where a trace switch is set.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b8ffb-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="b8ffb-113">Parent Elements</span></span>  
  
|<span data-ttu-id="b8ffb-114">Élément</span><span class="sxs-lookup"><span data-stu-id="b8ffb-114">Element</span></span>|<span data-ttu-id="b8ffb-115">Description</span><span class="sxs-lookup"><span data-stu-id="b8ffb-115">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="b8ffb-116">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b8ffb-116">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`System.diagnostics`|<span data-ttu-id="b8ffb-117">Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.</span><span class="sxs-lookup"><span data-stu-id="b8ffb-117">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b8ffb-118">Notes</span><span class="sxs-lookup"><span data-stu-id="b8ffb-118">Remarks</span></span>  

 <span data-ttu-id="b8ffb-119">Vous pouvez modifier le niveau d’un commutateur de trace en le plaçant dans un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="b8ffb-119">You can change the level of a trace switch by putting it in a configuration file.</span></span> <span data-ttu-id="b8ffb-120">Si le commutateur est un <xref:System.Diagnostics.BooleanSwitch> , vous pouvez l’activer ou le désactiver.</span><span class="sxs-lookup"><span data-stu-id="b8ffb-120">If the switch is a <xref:System.Diagnostics.BooleanSwitch>, you can turn it on and off.</span></span> <span data-ttu-id="b8ffb-121">Si le commutateur est un <xref:System.Diagnostics.TraceSwitch> , vous pouvez lui affecter différents niveaux pour spécifier les types de messages de trace ou de débogage que l’application génère.</span><span class="sxs-lookup"><span data-stu-id="b8ffb-121">If the switch is a <xref:System.Diagnostics.TraceSwitch>, you can assign different levels to it to specify the types of trace or debug messages the application outputs.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b8ffb-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="b8ffb-122">Example</span></span>  

 <span data-ttu-id="b8ffb-123">L’exemple suivant montre comment utiliser l' **\<switch>** élément pour définir le `General` commutateur de trace sur le <xref:System.Diagnostics.TraceLevel> niveau et activer le `Data` commutateur de trace booléen.</span><span class="sxs-lookup"><span data-stu-id="b8ffb-123">The following example shows how to use the **\<switch>** element to set the `General` trace switch to the <xref:System.Diagnostics.TraceLevel> level, and enable the `Data` Boolean trace switch.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <switches>  
         <add name="General" value="4" />  
         <add name="Data" value="1" />  
      </switches>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b8ffb-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b8ffb-124">See also</span></span>

- <xref:System.Diagnostics.Switch>
- <xref:System.Diagnostics.TraceSwitch>
- <xref:System.Diagnostics.BooleanSwitch>
- [<span data-ttu-id="b8ffb-125">Schéma des paramètres de traçage et de débogage</span><span class="sxs-lookup"><span data-stu-id="b8ffb-125">Trace and Debug Settings Schema</span></span>](index.md)
