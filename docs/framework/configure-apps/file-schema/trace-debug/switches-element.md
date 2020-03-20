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
ms.openlocfilehash: 15cc9680d7a20341eb5d1d1df302c1e034e70e02
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153228"
---
# <a name="switches-element"></a><span data-ttu-id="0cbd9-102">\<commutateurs> Element</span><span class="sxs-lookup"><span data-stu-id="0cbd9-102">\<switches> Element</span></span>
<span data-ttu-id="0cbd9-103">Contient des commutateurs de traçage et le niveau auquel ils sont définis.</span><span class="sxs-lookup"><span data-stu-id="0cbd9-103">Contains trace switches and the level where the trace switches are set.</span></span>  

<span data-ttu-id="0cbd9-104">[**\<configuration>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="0cbd9-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="0cbd9-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="0cbd9-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="0cbd9-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<commutateurs>**</span><span class="sxs-lookup"><span data-stu-id="0cbd9-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<switches>**</span></span>

## <a name="syntax"></a><span data-ttu-id="0cbd9-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0cbd9-107">Syntax</span></span>  
  
```xml  
      <switches>
</switches>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0cbd9-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="0cbd9-108">Attributes and Elements</span></span>  
 <span data-ttu-id="0cbd9-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="0cbd9-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0cbd9-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="0cbd9-110">Attributes</span></span>  
 <span data-ttu-id="0cbd9-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="0cbd9-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0cbd9-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="0cbd9-112">Child Elements</span></span>  
  
|<span data-ttu-id="0cbd9-113">Élément</span><span class="sxs-lookup"><span data-stu-id="0cbd9-113">Element</span></span>|<span data-ttu-id="0cbd9-114">Description</span><span class="sxs-lookup"><span data-stu-id="0cbd9-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0cbd9-115">\<ajouter></span><span class="sxs-lookup"><span data-stu-id="0cbd9-115">\<add></span></span>](add-element-for-switches.md)|<span data-ttu-id="0cbd9-116">Spécifie le niveau auquel un commutateur de trace est défini.</span><span class="sxs-lookup"><span data-stu-id="0cbd9-116">Specifies the level where a trace switch is set.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0cbd9-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="0cbd9-117">Parent Elements</span></span>  
  
|<span data-ttu-id="0cbd9-118">Élément</span><span class="sxs-lookup"><span data-stu-id="0cbd9-118">Element</span></span>|<span data-ttu-id="0cbd9-119">Description</span><span class="sxs-lookup"><span data-stu-id="0cbd9-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="0cbd9-120">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0cbd9-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`System.diagnostics`|<span data-ttu-id="0cbd9-121">Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.</span><span class="sxs-lookup"><span data-stu-id="0cbd9-121">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0cbd9-122">Notes </span><span class="sxs-lookup"><span data-stu-id="0cbd9-122">Remarks</span></span>  
 <span data-ttu-id="0cbd9-123">Vous pouvez modifier le niveau d’un commutateur de trace en le mettant dans un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="0cbd9-123">You can change the level of a trace switch by putting it in a configuration file.</span></span> <span data-ttu-id="0cbd9-124">Si l’interrupteur est un, <xref:System.Diagnostics.BooleanSwitch>vous pouvez l’allumer et éteindre.</span><span class="sxs-lookup"><span data-stu-id="0cbd9-124">If the switch is a <xref:System.Diagnostics.BooleanSwitch>, you can turn it on and off.</span></span> <span data-ttu-id="0cbd9-125">Si le commutateur <xref:System.Diagnostics.TraceSwitch>est un , vous pouvez lui attribuer différents niveaux pour spécifier les types de traces ou de déboçons messages les sorties d’application.</span><span class="sxs-lookup"><span data-stu-id="0cbd9-125">If the switch is a <xref:System.Diagnostics.TraceSwitch>, you can assign different levels to it to specify the types of trace or debug messages the application outputs.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0cbd9-126"> Exemple</span><span class="sxs-lookup"><span data-stu-id="0cbd9-126">Example</span></span>  
 <span data-ttu-id="0cbd9-127">L’exemple suivant montre comment utiliser \*\* \<l’interrupteur>\*\* élément <xref:System.Diagnostics.TraceLevel> pour définir `Data` le `General` commutateur de trace au niveau, et activer le commutateur de trace Boolean.</span><span class="sxs-lookup"><span data-stu-id="0cbd9-127">The following example shows how to use the **\<switch>** element to set the `General` trace switch to the <xref:System.Diagnostics.TraceLevel> level, and enable the `Data` Boolean trace switch.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0cbd9-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0cbd9-128">See also</span></span>

- <xref:System.Diagnostics.Switch>
- <xref:System.Diagnostics.TraceSwitch>
- <xref:System.Diagnostics.BooleanSwitch>
- [<span data-ttu-id="0cbd9-129">Trace et Debug Paramètres Schema</span><span class="sxs-lookup"><span data-stu-id="0cbd9-129">Trace and Debug Settings Schema</span></span>](index.md)
