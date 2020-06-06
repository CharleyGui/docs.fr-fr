---
title: Élément <add> pour <switches>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/switches/add
helpviewer_keywords:
- <add> element for <switches>
- add element for <switches>
ms.assetid: 712ac3a7-7abf-4a9e-8db4-acd241c2f369
ms.openlocfilehash: db2de681227dfdb7420808963219b9f52381f8fe
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74088958"
---
# <a name="add-element-for-switches"></a><span data-ttu-id="f57c0-102">\<add>, élément de \<switches></span><span class="sxs-lookup"><span data-stu-id="f57c0-102">\<add> Element for \<switches></span></span>
<span data-ttu-id="f57c0-103">Spécifie le niveau auquel un commutateur de trace est défini.</span><span class="sxs-lookup"><span data-stu-id="f57c0-103">Specifies the level where a trace switch is set.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<switches>**](switches-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="f57c0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f57c0-104">Syntax</span></span>  
  
```xml  
<add name="switch name"  
     value="value"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f57c0-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="f57c0-105">Attributes and Elements</span></span>  
 <span data-ttu-id="f57c0-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="f57c0-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f57c0-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="f57c0-107">Attributes</span></span>  
  
|<span data-ttu-id="f57c0-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="f57c0-108">Attribute</span></span>|<span data-ttu-id="f57c0-109">Description</span><span class="sxs-lookup"><span data-stu-id="f57c0-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f57c0-110">**name**</span><span class="sxs-lookup"><span data-stu-id="f57c0-110">**name**</span></span>|<span data-ttu-id="f57c0-111">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="f57c0-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="f57c0-112">Spécifie le nom du commutateur.</span><span class="sxs-lookup"><span data-stu-id="f57c0-112">Specifies the name of the switch.</span></span> <span data-ttu-id="f57c0-113">La valeur de cet attribut correspond au paramètre *DisplayName* passé au constructeur de commutateur.</span><span class="sxs-lookup"><span data-stu-id="f57c0-113">The value of this attribute corresponds to the *displayName* parameter that is passed to switch constructor.</span></span>|  
|<span data-ttu-id="f57c0-114">**value**</span><span class="sxs-lookup"><span data-stu-id="f57c0-114">**value**</span></span>|<span data-ttu-id="f57c0-115">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="f57c0-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="f57c0-116">Spécifie le niveau du commutateur.</span><span class="sxs-lookup"><span data-stu-id="f57c0-116">Specifies the level of the switch.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f57c0-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="f57c0-117">Child Elements</span></span>  
 <span data-ttu-id="f57c0-118">Aucun.</span><span class="sxs-lookup"><span data-stu-id="f57c0-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f57c0-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="f57c0-119">Parent Elements</span></span>  
  
|<span data-ttu-id="f57c0-120">Élément</span><span class="sxs-lookup"><span data-stu-id="f57c0-120">Element</span></span>|<span data-ttu-id="f57c0-121">Description</span><span class="sxs-lookup"><span data-stu-id="f57c0-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="f57c0-122">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f57c0-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`switches`|<span data-ttu-id="f57c0-123">Contient des commutateurs de traçage et le niveau auquel ils sont définis.</span><span class="sxs-lookup"><span data-stu-id="f57c0-123">Contains trace switches and the level where the trace switches are set.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="f57c0-124">Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.</span><span class="sxs-lookup"><span data-stu-id="f57c0-124">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f57c0-125">Remarques</span><span class="sxs-lookup"><span data-stu-id="f57c0-125">Remarks</span></span>  
 <span data-ttu-id="f57c0-126">Vous pouvez modifier le niveau d’un commutateur de trace en le plaçant dans un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="f57c0-126">You can change the level of a trace switch by putting it in a configuration file.</span></span> <span data-ttu-id="f57c0-127">Si le commutateur est un <xref:System.Diagnostics.BooleanSwitch> , vous pouvez l’activer ou le désactiver.</span><span class="sxs-lookup"><span data-stu-id="f57c0-127">If the switch is a <xref:System.Diagnostics.BooleanSwitch>, you can turn it on and off.</span></span> <span data-ttu-id="f57c0-128">Si le commutateur est un <xref:System.Diagnostics.TraceSwitch> , vous pouvez lui affecter différents niveaux pour spécifier les types de messages de trace ou de débogage que l’application génère.</span><span class="sxs-lookup"><span data-stu-id="f57c0-128">If the switch is a <xref:System.Diagnostics.TraceSwitch>, you can assign different levels to it to specify the types of trace or debug messages the application outputs.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f57c0-129">Exemple</span><span class="sxs-lookup"><span data-stu-id="f57c0-129">Example</span></span>  
 <span data-ttu-id="f57c0-130">L’exemple suivant montre comment utiliser l' **\<add>** élément pour définir le `General` commutateur de trace sur le <xref:System.Diagnostics.TraceLevel> niveau et activer le `Data` commutateur de trace booléen.</span><span class="sxs-lookup"><span data-stu-id="f57c0-130">The following example shows how to use the **\<add>** element to set the `General` trace switch to the <xref:System.Diagnostics.TraceLevel> level, and enable the `Data` Boolean trace switch.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f57c0-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f57c0-131">See also</span></span>

- <xref:System.Diagnostics.Switch>
- <xref:System.Diagnostics.TraceSwitch>
- <xref:System.Diagnostics.BooleanSwitch>
- [<span data-ttu-id="f57c0-132">Schéma des paramètres de traçage et de débogage</span><span class="sxs-lookup"><span data-stu-id="f57c0-132">Trace and Debug Settings Schema</span></span>](index.md)
