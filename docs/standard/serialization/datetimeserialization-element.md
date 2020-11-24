---
title: Élément <dateTimeSerialization>
description: Cet article décrit l' <dateTimeSerialization> élément, qui détermine le mode de sérialisation des objets DateTime.
ms.date: 03/30/2017
helpviewer_keywords:
- dateTimeSerialization element
- XML serialization, configuration
- <dateTimeSerialization> element
ms.assetid: 90fda55c-7730-41e9-bc4b-6423a4b920af
ms.openlocfilehash: 1623517e66955c14b7e738c860ec16086fe30429
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95678972"
---
# <a name="datetimeserialization-element"></a><span data-ttu-id="41311-103">Élément \<dateTimeSerialization></span><span class="sxs-lookup"><span data-stu-id="41311-103">\<dateTimeSerialization> Element</span></span>

<span data-ttu-id="41311-104">Détermine le mode de sérialisation des objets <xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="41311-104">Determines the serialization mode of <xref:System.DateTime> objects.</span></span>  
  
 \<configuration>  
\<dateTimeSerialization>  
  
## <a name="syntax"></a><span data-ttu-id="41311-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="41311-105">Syntax</span></span>  
  
```xml  
<dateTimeSerialization  
    mode = "Roundtrip|Local"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="41311-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="41311-106">Attributes and Elements</span></span>  

 <span data-ttu-id="41311-107">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="41311-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="41311-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="41311-108">Attributes</span></span>  
  
|<span data-ttu-id="41311-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="41311-109">Attributes</span></span>|<span data-ttu-id="41311-110">Description</span><span class="sxs-lookup"><span data-stu-id="41311-110">Description</span></span>|  
|----------------|-----------------|  
|`mode`|<span data-ttu-id="41311-111">facultatif.</span><span class="sxs-lookup"><span data-stu-id="41311-111">Optional.</span></span> <span data-ttu-id="41311-112">Spécifie le mode de sérialisation.</span><span class="sxs-lookup"><span data-stu-id="41311-112">Specifies the serialization mode.</span></span> <span data-ttu-id="41311-113">Affectez-le à l'une des valeurs <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>.</span><span class="sxs-lookup"><span data-stu-id="41311-113">Set to one of the <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode> values.</span></span> <span data-ttu-id="41311-114">La valeur par défaut est **RoundTrip**.</span><span class="sxs-lookup"><span data-stu-id="41311-114">The default is **RoundTrip**.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="41311-115">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="41311-115">Child Elements</span></span>  

 <span data-ttu-id="41311-116">Aucun.</span><span class="sxs-lookup"><span data-stu-id="41311-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="41311-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="41311-117">Parent Elements</span></span>  
  
|<span data-ttu-id="41311-118">Élément</span><span class="sxs-lookup"><span data-stu-id="41311-118">Element</span></span>|<span data-ttu-id="41311-119">Description</span><span class="sxs-lookup"><span data-stu-id="41311-119">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="41311-120">system.xml.serialization</span><span class="sxs-lookup"><span data-stu-id="41311-120">system.xml.serialization</span></span>|<span data-ttu-id="41311-121">Élément de niveau supérieur permettant de contrôler la sérialisation XML.</span><span class="sxs-lookup"><span data-stu-id="41311-121">The top-level element for controlling XML serialization.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="41311-122">Remarques</span><span class="sxs-lookup"><span data-stu-id="41311-122">Remarks</span></span>  

<span data-ttu-id="41311-123">Quand cette propriété est définie sur **local**, <xref:System.DateTime> les objets sont toujours mis en forme comme heure locale.</span><span class="sxs-lookup"><span data-stu-id="41311-123">When this property is set to **Local**, <xref:System.DateTime> objects are always formatted as the local time.</span></span> <span data-ttu-id="41311-124">Autrement dit, les informations du fuseau horaire local sont toujours incluses avec les données sérialisées.</span><span class="sxs-lookup"><span data-stu-id="41311-124">That is, local time zone information is always included with the serialized data.</span></span>
  
<span data-ttu-id="41311-125">Quand cette propriété est définie sur **roundtrip**, les <xref:System.DateTime> objets sont examinés pour déterminer s’ils se trouvent dans le fuseau horaire local, UTC ou non spécifié.</span><span class="sxs-lookup"><span data-stu-id="41311-125">When this property is set to **Roundtrip**, <xref:System.DateTime> objects are examined to determine whether they are in the local, UTC, or an unspecified time zone.</span></span> <span data-ttu-id="41311-126">Les objets <xref:System.DateTime> sont ensuite sérialisés de manière à ce que ces informations soient conservées.</span><span class="sxs-lookup"><span data-stu-id="41311-126">The <xref:System.DateTime> objects are then serialized in such a way that this information is preserved.</span></span> <span data-ttu-id="41311-127">Il s'agit du comportement par défaut, recommandé pour toutes les nouvelles applications qui ne communiquent pas avec les versions antérieures du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="41311-127">This is the default behavior and is the recommended behavior for all new applications that do not communicate with older versions of the framework.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41311-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="41311-128">See also</span></span>

- <xref:System.DateTime>
- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [<span data-ttu-id="41311-129">Schéma du fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="41311-129">Configuration File Schema</span></span>](../../framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="41311-130">\<schemaImporterExtensions> Appartient</span><span class="sxs-lookup"><span data-stu-id="41311-130">\<schemaImporterExtensions> Element</span></span>](schemaimporterextensions-element.md)
- [<span data-ttu-id="41311-131">\<add> , Élément de \<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="41311-131">\<add> Element for \<schemaImporterExtensions></span></span>](add-element-for-schemaimporterextensions.md)
- [<span data-ttu-id="41311-132">\<system.xml.serialization> Appartient</span><span class="sxs-lookup"><span data-stu-id="41311-132">\<system.xml.serialization> Element</span></span>](system-xml-serialization-element.md)
