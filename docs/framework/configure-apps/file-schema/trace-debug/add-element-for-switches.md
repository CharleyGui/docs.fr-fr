---
title: Élément <add> pour <switches>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/switches/add
helpviewer_keywords:
- <add> element for <switches>
- add element for <switches>
ms.assetid: 712ac3a7-7abf-4a9e-8db4-acd241c2f369
ms.openlocfilehash: 2edc890049d62913d693ad61d8d814d012c0f482
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697177"
---
# <a name="add-element-for-switches"></a><span data-ttu-id="9d2bb-102">\<add > élément de \<switches ></span><span class="sxs-lookup"><span data-stu-id="9d2bb-102">\<add> Element for \<switches></span></span>
<span data-ttu-id="9d2bb-103">Spécifie le niveau auquel un commutateur de trace est défini.</span><span class="sxs-lookup"><span data-stu-id="9d2bb-103">Specifies the level where a trace switch is set.</span></span>  
  
[<span data-ttu-id="9d2bb-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="9d2bb-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="9d2bb-105">&nbsp; @ no__t-1[ **\<System. diagnostics >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="9d2bb-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>  
<span data-ttu-id="9d2bb-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<switches >** ](switches-element.md)</span><span class="sxs-lookup"><span data-stu-id="9d2bb-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<switches>**](switches-element.md)</span></span>  
<span data-ttu-id="9d2bb-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Ajouter >**</span><span class="sxs-lookup"><span data-stu-id="9d2bb-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d2bb-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9d2bb-108">Syntax</span></span>  
  
```xml  
<add name="switch name"  
     value="value"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9d2bb-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="9d2bb-109">Attributes and Elements</span></span>  
 <span data-ttu-id="9d2bb-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="9d2bb-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9d2bb-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="9d2bb-111">Attributes</span></span>  
  
|<span data-ttu-id="9d2bb-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="9d2bb-112">Attribute</span></span>|<span data-ttu-id="9d2bb-113">Description</span><span class="sxs-lookup"><span data-stu-id="9d2bb-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9d2bb-114">**name**</span><span class="sxs-lookup"><span data-stu-id="9d2bb-114">**name**</span></span>|<span data-ttu-id="9d2bb-115">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="9d2bb-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="9d2bb-116">Spécifie le nom du commutateur.</span><span class="sxs-lookup"><span data-stu-id="9d2bb-116">Specifies the name of the switch.</span></span> <span data-ttu-id="9d2bb-117">La valeur de cet attribut correspond au paramètre *DisplayName* passé au constructeur de commutateur.</span><span class="sxs-lookup"><span data-stu-id="9d2bb-117">The value of this attribute corresponds to the *displayName* parameter that is passed to switch constructor.</span></span>|  
|<span data-ttu-id="9d2bb-118">**value**</span><span class="sxs-lookup"><span data-stu-id="9d2bb-118">**value**</span></span>|<span data-ttu-id="9d2bb-119">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="9d2bb-119">Required attribute.</span></span><br /><br /> <span data-ttu-id="9d2bb-120">Spécifie le niveau du commutateur.</span><span class="sxs-lookup"><span data-stu-id="9d2bb-120">Specifies the level of the switch.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9d2bb-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="9d2bb-121">Child Elements</span></span>  
 <span data-ttu-id="9d2bb-122">Aucun.</span><span class="sxs-lookup"><span data-stu-id="9d2bb-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9d2bb-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="9d2bb-123">Parent Elements</span></span>  
  
|<span data-ttu-id="9d2bb-124">Élément</span><span class="sxs-lookup"><span data-stu-id="9d2bb-124">Element</span></span>|<span data-ttu-id="9d2bb-125">Description</span><span class="sxs-lookup"><span data-stu-id="9d2bb-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="9d2bb-126">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9d2bb-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`switches`|<span data-ttu-id="9d2bb-127">Contient des commutateurs de traçage et le niveau auquel ils sont définis.</span><span class="sxs-lookup"><span data-stu-id="9d2bb-127">Contains trace switches and the level where the trace switches are set.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="9d2bb-128">Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.</span><span class="sxs-lookup"><span data-stu-id="9d2bb-128">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9d2bb-129">Notes</span><span class="sxs-lookup"><span data-stu-id="9d2bb-129">Remarks</span></span>  
 <span data-ttu-id="9d2bb-130">Vous pouvez modifier le niveau d’un commutateur de trace en le plaçant dans un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="9d2bb-130">You can change the level of a trace switch by putting it in a configuration file.</span></span> <span data-ttu-id="9d2bb-131">Si le commutateur est un <xref:System.Diagnostics.BooleanSwitch>, vous pouvez l’activer ou la désactiver.</span><span class="sxs-lookup"><span data-stu-id="9d2bb-131">If the switch is a <xref:System.Diagnostics.BooleanSwitch>, you can turn it on and off.</span></span> <span data-ttu-id="9d2bb-132">Si le commutateur est un <xref:System.Diagnostics.TraceSwitch>, vous pouvez lui affecter différents niveaux pour spécifier les types de messages de trace ou de débogage que l’application génère.</span><span class="sxs-lookup"><span data-stu-id="9d2bb-132">If the switch is a <xref:System.Diagnostics.TraceSwitch>, you can assign different levels to it to specify the types of trace or debug messages the application outputs.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9d2bb-133">Exemple</span><span class="sxs-lookup"><span data-stu-id="9d2bb-133">Example</span></span>  
 <span data-ttu-id="9d2bb-134">L’exemple suivant montre comment utiliser l’élément **\<add >** pour définir le commutateur de trace `General` sur le niveau <xref:System.Diagnostics.TraceLevel> et activer le commutateur de trace booléen `Data`.</span><span class="sxs-lookup"><span data-stu-id="9d2bb-134">The following example shows how to use the **\<add>** element to set the `General` trace switch to the <xref:System.Diagnostics.TraceLevel> level, and enable the `Data` Boolean trace switch.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9d2bb-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9d2bb-135">See also</span></span>

- <xref:System.Diagnostics.Switch>
- <xref:System.Diagnostics.TraceSwitch>
- <xref:System.Diagnostics.BooleanSwitch>
- [<span data-ttu-id="9d2bb-136">Schéma des paramètres de trace et de débogage</span><span class="sxs-lookup"><span data-stu-id="9d2bb-136">Trace and Debug Settings Schema</span></span>](index.md)
