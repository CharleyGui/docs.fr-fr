---
title: Élément <add> pour <switches>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/switches/add
helpviewer_keywords:
- <add> element for <switches>
- add element for <switches>
ms.assetid: 712ac3a7-7abf-4a9e-8db4-acd241c2f369
ms.openlocfilehash: 8fcd5cbe63a323a7509f5ff8c615364295c244d5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920539"
---
# <a name="add-element-for-switches"></a><span data-ttu-id="ddb53-102">\<Ajoutez > élément pour \<les commutateurs ></span><span class="sxs-lookup"><span data-stu-id="ddb53-102">\<add> Element for \<switches></span></span>
<span data-ttu-id="ddb53-103">Spécifie le niveau auquel un commutateur de trace est défini.</span><span class="sxs-lookup"><span data-stu-id="ddb53-103">Specifies the level where a trace switch is set.</span></span>  
  
 <span data-ttu-id="ddb53-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="ddb53-104">\<configuration></span></span>  
<span data-ttu-id="ddb53-105">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="ddb53-105">\<system.diagnostics></span></span>  
<span data-ttu-id="ddb53-106">\<switches></span><span class="sxs-lookup"><span data-stu-id="ddb53-106">\<switches></span></span>  
<span data-ttu-id="ddb53-107">\<add></span><span class="sxs-lookup"><span data-stu-id="ddb53-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ddb53-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ddb53-108">Syntax</span></span>  
  
```xml  
<add name="switch name"  
     value="value"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ddb53-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="ddb53-109">Attributes and Elements</span></span>  
 <span data-ttu-id="ddb53-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="ddb53-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ddb53-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="ddb53-111">Attributes</span></span>  
  
|<span data-ttu-id="ddb53-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="ddb53-112">Attribute</span></span>|<span data-ttu-id="ddb53-113">Description</span><span class="sxs-lookup"><span data-stu-id="ddb53-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ddb53-114">**name**</span><span class="sxs-lookup"><span data-stu-id="ddb53-114">**name**</span></span>|<span data-ttu-id="ddb53-115">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="ddb53-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="ddb53-116">Spécifie le nom du commutateur.</span><span class="sxs-lookup"><span data-stu-id="ddb53-116">Specifies the name of the switch.</span></span> <span data-ttu-id="ddb53-117">La valeur de cet attribut correspond au paramètre *DisplayName* passé au constructeur de commutateur.</span><span class="sxs-lookup"><span data-stu-id="ddb53-117">The value of this attribute corresponds to the *displayName* parameter that is passed to switch constructor.</span></span>|  
|<span data-ttu-id="ddb53-118">**value**</span><span class="sxs-lookup"><span data-stu-id="ddb53-118">**value**</span></span>|<span data-ttu-id="ddb53-119">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="ddb53-119">Required attribute.</span></span><br /><br /> <span data-ttu-id="ddb53-120">Spécifie le niveau du commutateur.</span><span class="sxs-lookup"><span data-stu-id="ddb53-120">Specifies the level of the switch.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ddb53-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="ddb53-121">Child Elements</span></span>  
 <span data-ttu-id="ddb53-122">Aucun.</span><span class="sxs-lookup"><span data-stu-id="ddb53-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ddb53-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="ddb53-123">Parent Elements</span></span>  
  
|<span data-ttu-id="ddb53-124">Élément</span><span class="sxs-lookup"><span data-stu-id="ddb53-124">Element</span></span>|<span data-ttu-id="ddb53-125">Description</span><span class="sxs-lookup"><span data-stu-id="ddb53-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="ddb53-126">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ddb53-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`switches`|<span data-ttu-id="ddb53-127">Contient des commutateurs de traçage et le niveau auquel ils sont définis.</span><span class="sxs-lookup"><span data-stu-id="ddb53-127">Contains trace switches and the level where the trace switches are set.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="ddb53-128">Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.</span><span class="sxs-lookup"><span data-stu-id="ddb53-128">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ddb53-129">Notes</span><span class="sxs-lookup"><span data-stu-id="ddb53-129">Remarks</span></span>  
 <span data-ttu-id="ddb53-130">Vous pouvez modifier le niveau d’un commutateur de trace en le plaçant dans un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="ddb53-130">You can change the level of a trace switch by putting it in a configuration file.</span></span> <span data-ttu-id="ddb53-131">Si le commutateur est un <xref:System.Diagnostics.BooleanSwitch>, vous pouvez l’activer ou le désactiver.</span><span class="sxs-lookup"><span data-stu-id="ddb53-131">If the switch is a <xref:System.Diagnostics.BooleanSwitch>, you can turn it on and off.</span></span> <span data-ttu-id="ddb53-132">Si le commutateur est un <xref:System.Diagnostics.TraceSwitch>, vous pouvez lui affecter différents niveaux pour spécifier les types de messages de trace ou de débogage que l’application génère.</span><span class="sxs-lookup"><span data-stu-id="ddb53-132">If the switch is a <xref:System.Diagnostics.TraceSwitch>, you can assign different levels to it to specify the types of trace or debug messages the application outputs.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ddb53-133">Exemple</span><span class="sxs-lookup"><span data-stu-id="ddb53-133">Example</span></span>  
 <span data-ttu-id="ddb53-134">L’exemple suivant montre comment utiliser <xref:System.Diagnostics.TraceLevel> l' `Data` `General`  **\<élément Add >** pour définir le commutateur de trace sur le niveau et activer le commutateur de trace booléen.</span><span class="sxs-lookup"><span data-stu-id="ddb53-134">The following example shows how to use the **\<add>** element to set the `General` trace switch to the <xref:System.Diagnostics.TraceLevel> level, and enable the `Data` Boolean trace switch.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ddb53-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ddb53-135">See also</span></span>

- <xref:System.Diagnostics.Switch>
- <xref:System.Diagnostics.TraceSwitch>
- <xref:System.Diagnostics.BooleanSwitch>
- [<span data-ttu-id="ddb53-136">Schéma des paramètres de trace et de débogage</span><span class="sxs-lookup"><span data-stu-id="ddb53-136">Trace and Debug Settings Schema</span></span>](index.md)
