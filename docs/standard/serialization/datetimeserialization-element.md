---
title: Élément <dateTimeSerialization>
description: Cet article décrit l' <dateTimeSerialization> élément, qui détermine le mode de sérialisation des objets DateTime.
ms.date: 03/30/2017
helpviewer_keywords:
- dateTimeSerialization element
- XML serialization, configuration
- <dateTimeSerialization> element
ms.assetid: 90fda55c-7730-41e9-bc4b-6423a4b920af
ms.openlocfilehash: 652a88e25f59cd905e47ef71351e47e67f375286
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83375824"
---
# <a name="datetimeserialization-element"></a><span data-ttu-id="69748-103">\<dateTimeSerialization>, élément</span><span class="sxs-lookup"><span data-stu-id="69748-103">\<dateTimeSerialization> Element</span></span>
<span data-ttu-id="69748-104">Détermine le mode de sérialisation des objets <xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="69748-104">Determines the serialization mode of <xref:System.DateTime> objects.</span></span>  
  
 <span data-ttu-id="69748-105">\<configuration></span><span class="sxs-lookup"><span data-stu-id="69748-105">\<configuration></span></span>  
<span data-ttu-id="69748-106">\<dateTimeSerialization></span><span class="sxs-lookup"><span data-stu-id="69748-106">\<dateTimeSerialization></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69748-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="69748-107">Syntax</span></span>  
  
```xml  
<dateTimeSerialization  
    mode = "Roundtrip|Local"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="69748-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="69748-108">Attributes and Elements</span></span>  
 <span data-ttu-id="69748-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="69748-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="69748-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="69748-110">Attributes</span></span>  
  
|<span data-ttu-id="69748-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="69748-111">Attributes</span></span>|<span data-ttu-id="69748-112">Description</span><span class="sxs-lookup"><span data-stu-id="69748-112">Description</span></span>|  
|----------------|-----------------|  
|`mode`|<span data-ttu-id="69748-113">facultatif.</span><span class="sxs-lookup"><span data-stu-id="69748-113">Optional.</span></span> <span data-ttu-id="69748-114">Spécifie le mode de sérialisation.</span><span class="sxs-lookup"><span data-stu-id="69748-114">Specifies the serialization mode.</span></span> <span data-ttu-id="69748-115">Affectez-le à l'une des valeurs <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>.</span><span class="sxs-lookup"><span data-stu-id="69748-115">Set to one of the <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode> values.</span></span> <span data-ttu-id="69748-116">La valeur par défaut est **RoundTrip**.</span><span class="sxs-lookup"><span data-stu-id="69748-116">The default is **RoundTrip**.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="69748-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="69748-117">Child Elements</span></span>  
 <span data-ttu-id="69748-118">Aucun.</span><span class="sxs-lookup"><span data-stu-id="69748-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="69748-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="69748-119">Parent Elements</span></span>  
  
|<span data-ttu-id="69748-120">Élément</span><span class="sxs-lookup"><span data-stu-id="69748-120">Element</span></span>|<span data-ttu-id="69748-121">Description</span><span class="sxs-lookup"><span data-stu-id="69748-121">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="69748-122">system.xml.serialization</span><span class="sxs-lookup"><span data-stu-id="69748-122">system.xml.serialization</span></span>|<span data-ttu-id="69748-123">Élément de niveau supérieur permettant de contrôler la sérialisation XML.</span><span class="sxs-lookup"><span data-stu-id="69748-123">The top-level element for controlling XML serialization.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="69748-124">Remarks</span><span class="sxs-lookup"><span data-stu-id="69748-124">Remarks</span></span>  
 <span data-ttu-id="69748-125">Dans les versions 1,0, 1,1, 2,0 et versions ultérieures de la .NET Framework, quand cette propriété est définie sur **local**, <xref:System.DateTime> les objets sont toujours mis en forme en tant qu’heure locale.</span><span class="sxs-lookup"><span data-stu-id="69748-125">In versions 1.0, 1.1, 2.0 and later versions of the .NET Framework, when this property is set to **Local**, <xref:System.DateTime> objects are always formatted as the local time.</span></span> <span data-ttu-id="69748-126">Autrement dit, les informations du fuseau horaire local sont toujours incluses avec les données sérialisées.</span><span class="sxs-lookup"><span data-stu-id="69748-126">That is, local time zone information is always included with the serialized data.</span></span> <span data-ttu-id="69748-127">Affectez la valeur **Local** à cette propriété pour garantir la compatibilité avec les versions antérieures du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="69748-127">Set this property to **Local** to ensure compatibility with older versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="69748-128">Dans la version 2,0 et les versions ultérieures du .NET Framework dont cette propriété a la valeur **roundtrip**, les <xref:System.DateTime> objets sont examinés pour déterminer s’ils se trouvent dans le fuseau horaire local, UTC ou non spécifié.</span><span class="sxs-lookup"><span data-stu-id="69748-128">In version 2.0 and later versions of the .NET Framework that have this property set to **Roundtrip**, <xref:System.DateTime> objects are examined to determine whether they are in the local, UTC, or an unspecified time zone.</span></span> <span data-ttu-id="69748-129">Les objets <xref:System.DateTime> sont ensuite sérialisés de manière à ce que ces informations soient conservées.</span><span class="sxs-lookup"><span data-stu-id="69748-129">The <xref:System.DateTime> objects are then serialized in such a way that this information is preserved.</span></span> <span data-ttu-id="69748-130">Il s'agit du comportement par défaut, recommandé pour toutes les nouvelles applications qui ne communiquent pas avec les versions antérieures du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="69748-130">This is the default behavior and is the recommended behavior for all new applications that do not communicate with older versions of the framework.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69748-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="69748-131">See also</span></span>

- <xref:System.DateTime>
- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [<span data-ttu-id="69748-132">Schéma du fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="69748-132">Configuration File Schema</span></span>](../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="69748-133">\<schemaImporterExtensions>, élément</span><span class="sxs-lookup"><span data-stu-id="69748-133">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)
- [<span data-ttu-id="69748-134">\<Ajouter> élément pour \< schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="69748-134">\<add> Element for \<schemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)
- [<span data-ttu-id="69748-135">\<Élément System. Xml. Serialization></span><span class="sxs-lookup"><span data-stu-id="69748-135">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)
