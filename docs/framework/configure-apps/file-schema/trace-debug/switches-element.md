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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153228"
---
# <a name="switches-element"></a><span data-ttu-id="d08e1-102">Élément \<switches></span><span class="sxs-lookup"><span data-stu-id="d08e1-102">\<switches> Element</span></span>
<span data-ttu-id="d08e1-103">Contient des commutateurs de traçage et le niveau auquel ils sont définis.</span><span class="sxs-lookup"><span data-stu-id="d08e1-103">Contains trace switches and the level where the trace switches are set.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<switches>**

## <a name="syntax"></a><span data-ttu-id="d08e1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d08e1-104">Syntax</span></span>  
  
```xml  
      <switches>
</switches>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d08e1-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="d08e1-105">Attributes and Elements</span></span>  
 <span data-ttu-id="d08e1-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="d08e1-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d08e1-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="d08e1-107">Attributes</span></span>  
 <span data-ttu-id="d08e1-108">Aucun.</span><span class="sxs-lookup"><span data-stu-id="d08e1-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d08e1-109">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="d08e1-109">Child Elements</span></span>  
  
|<span data-ttu-id="d08e1-110">Élément</span><span class="sxs-lookup"><span data-stu-id="d08e1-110">Element</span></span>|<span data-ttu-id="d08e1-111">Description</span><span class="sxs-lookup"><span data-stu-id="d08e1-111">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-element-for-switches.md)|<span data-ttu-id="d08e1-112">Spécifie le niveau auquel un commutateur de trace est défini.</span><span class="sxs-lookup"><span data-stu-id="d08e1-112">Specifies the level where a trace switch is set.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d08e1-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="d08e1-113">Parent Elements</span></span>  
  
|<span data-ttu-id="d08e1-114">Élément</span><span class="sxs-lookup"><span data-stu-id="d08e1-114">Element</span></span>|<span data-ttu-id="d08e1-115">Description</span><span class="sxs-lookup"><span data-stu-id="d08e1-115">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="d08e1-116">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d08e1-116">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`System.diagnostics`|<span data-ttu-id="d08e1-117">Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.</span><span class="sxs-lookup"><span data-stu-id="d08e1-117">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d08e1-118">Remarques</span><span class="sxs-lookup"><span data-stu-id="d08e1-118">Remarks</span></span>  
 <span data-ttu-id="d08e1-119">Vous pouvez modifier le niveau d’un commutateur de trace en le plaçant dans un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="d08e1-119">You can change the level of a trace switch by putting it in a configuration file.</span></span> <span data-ttu-id="d08e1-120">Si le commutateur est un <xref:System.Diagnostics.BooleanSwitch> , vous pouvez l’activer ou le désactiver.</span><span class="sxs-lookup"><span data-stu-id="d08e1-120">If the switch is a <xref:System.Diagnostics.BooleanSwitch>, you can turn it on and off.</span></span> <span data-ttu-id="d08e1-121">Si le commutateur est un <xref:System.Diagnostics.TraceSwitch> , vous pouvez lui affecter différents niveaux pour spécifier les types de messages de trace ou de débogage que l’application génère.</span><span class="sxs-lookup"><span data-stu-id="d08e1-121">If the switch is a <xref:System.Diagnostics.TraceSwitch>, you can assign different levels to it to specify the types of trace or debug messages the application outputs.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d08e1-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="d08e1-122">Example</span></span>  
 <span data-ttu-id="d08e1-123">L’exemple suivant montre comment utiliser l' **\<switch>** élément pour définir le `General` commutateur de trace sur le <xref:System.Diagnostics.TraceLevel> niveau et activer le `Data` commutateur de trace booléen.</span><span class="sxs-lookup"><span data-stu-id="d08e1-123">The following example shows how to use the **\<switch>** element to set the `General` trace switch to the <xref:System.Diagnostics.TraceLevel> level, and enable the `Data` Boolean trace switch.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d08e1-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d08e1-124">See also</span></span>

- <xref:System.Diagnostics.Switch>
- <xref:System.Diagnostics.TraceSwitch>
- <xref:System.Diagnostics.BooleanSwitch>
- [<span data-ttu-id="d08e1-125">Schéma des paramètres de traçage et de débogage</span><span class="sxs-lookup"><span data-stu-id="d08e1-125">Trace and Debug Settings Schema</span></span>](index.md)
