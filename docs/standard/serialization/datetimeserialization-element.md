---
title: Élément <dateTimeSerialization>
description: Cet article décrit l' <dateTimeSerialization> élément, qui détermine le mode de sérialisation des objets DateTime.
ms.date: 03/30/2017
helpviewer_keywords:
- dateTimeSerialization element
- XML serialization, configuration
- <dateTimeSerialization> element
ms.assetid: 90fda55c-7730-41e9-bc4b-6423a4b920af
ms.openlocfilehash: a2684ab72c1fb109d711e333e01836d3399caf86
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "84289640"
---
# <a name="datetimeserialization-element"></a><span data-ttu-id="7fa84-103">Élément \<dateTimeSerialization></span><span class="sxs-lookup"><span data-stu-id="7fa84-103">\<dateTimeSerialization> Element</span></span>
<span data-ttu-id="7fa84-104">Détermine le mode de sérialisation des objets <xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="7fa84-104">Determines the serialization mode of <xref:System.DateTime> objects.</span></span>  
  
 \<configuration>  
\<dateTimeSerialization>  
  
## <a name="syntax"></a><span data-ttu-id="7fa84-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7fa84-105">Syntax</span></span>  
  
```xml  
<dateTimeSerialization  
    mode = "Roundtrip|Local"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7fa84-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="7fa84-106">Attributes and Elements</span></span>  
 <span data-ttu-id="7fa84-107">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="7fa84-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7fa84-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="7fa84-108">Attributes</span></span>  
  
|<span data-ttu-id="7fa84-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="7fa84-109">Attributes</span></span>|<span data-ttu-id="7fa84-110">Description</span><span class="sxs-lookup"><span data-stu-id="7fa84-110">Description</span></span>|  
|----------------|-----------------|  
|`mode`|<span data-ttu-id="7fa84-111">facultatif.</span><span class="sxs-lookup"><span data-stu-id="7fa84-111">Optional.</span></span> <span data-ttu-id="7fa84-112">Spécifie le mode de sérialisation.</span><span class="sxs-lookup"><span data-stu-id="7fa84-112">Specifies the serialization mode.</span></span> <span data-ttu-id="7fa84-113">Affectez-le à l'une des valeurs <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>.</span><span class="sxs-lookup"><span data-stu-id="7fa84-113">Set to one of the <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode> values.</span></span> <span data-ttu-id="7fa84-114">La valeur par défaut est **RoundTrip**.</span><span class="sxs-lookup"><span data-stu-id="7fa84-114">The default is **RoundTrip**.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7fa84-115">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="7fa84-115">Child Elements</span></span>  
 <span data-ttu-id="7fa84-116">Aucun.</span><span class="sxs-lookup"><span data-stu-id="7fa84-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7fa84-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="7fa84-117">Parent Elements</span></span>  
  
|<span data-ttu-id="7fa84-118">Élément</span><span class="sxs-lookup"><span data-stu-id="7fa84-118">Element</span></span>|<span data-ttu-id="7fa84-119">Description</span><span class="sxs-lookup"><span data-stu-id="7fa84-119">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7fa84-120">system.xml.serialization</span><span class="sxs-lookup"><span data-stu-id="7fa84-120">system.xml.serialization</span></span>|<span data-ttu-id="7fa84-121">Élément de niveau supérieur permettant de contrôler la sérialisation XML.</span><span class="sxs-lookup"><span data-stu-id="7fa84-121">The top-level element for controlling XML serialization.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7fa84-122">Remarques</span><span class="sxs-lookup"><span data-stu-id="7fa84-122">Remarks</span></span>  
 <span data-ttu-id="7fa84-123">Dans les versions 1,0, 1,1, 2,0 et versions ultérieures de la .NET Framework, quand cette propriété est définie sur **local**, <xref:System.DateTime> les objets sont toujours mis en forme en tant qu’heure locale.</span><span class="sxs-lookup"><span data-stu-id="7fa84-123">In versions 1.0, 1.1, 2.0 and later versions of the .NET Framework, when this property is set to **Local**, <xref:System.DateTime> objects are always formatted as the local time.</span></span> <span data-ttu-id="7fa84-124">Autrement dit, les informations du fuseau horaire local sont toujours incluses avec les données sérialisées.</span><span class="sxs-lookup"><span data-stu-id="7fa84-124">That is, local time zone information is always included with the serialized data.</span></span> <span data-ttu-id="7fa84-125">Affectez la valeur **Local** à cette propriété pour garantir la compatibilité avec les versions antérieures du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7fa84-125">Set this property to **Local** to ensure compatibility with older versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="7fa84-126">Dans la version 2,0 et les versions ultérieures du .NET Framework dont cette propriété a la valeur **roundtrip**, les <xref:System.DateTime> objets sont examinés pour déterminer s’ils se trouvent dans le fuseau horaire local, UTC ou non spécifié.</span><span class="sxs-lookup"><span data-stu-id="7fa84-126">In version 2.0 and later versions of the .NET Framework that have this property set to **Roundtrip**, <xref:System.DateTime> objects are examined to determine whether they are in the local, UTC, or an unspecified time zone.</span></span> <span data-ttu-id="7fa84-127">Les objets <xref:System.DateTime> sont ensuite sérialisés de manière à ce que ces informations soient conservées.</span><span class="sxs-lookup"><span data-stu-id="7fa84-127">The <xref:System.DateTime> objects are then serialized in such a way that this information is preserved.</span></span> <span data-ttu-id="7fa84-128">Il s'agit du comportement par défaut, recommandé pour toutes les nouvelles applications qui ne communiquent pas avec les versions antérieures du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7fa84-128">This is the default behavior and is the recommended behavior for all new applications that do not communicate with older versions of the framework.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fa84-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7fa84-129">See also</span></span>

- <xref:System.DateTime>
- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [<span data-ttu-id="7fa84-130">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="7fa84-130">Configuration File Schema</span></span>](../../framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="7fa84-131">\<schemaImporterExtensions>Appartient</span><span class="sxs-lookup"><span data-stu-id="7fa84-131">\<schemaImporterExtensions> Element</span></span>](schemaimporterextensions-element.md)
- [<span data-ttu-id="7fa84-132">\<add>, Élément de\<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="7fa84-132">\<add> Element for \<schemaImporterExtensions></span></span>](add-element-for-schemaimporterextensions.md)
- [<span data-ttu-id="7fa84-133">\<system.xml.serialization>Appartient</span><span class="sxs-lookup"><span data-stu-id="7fa84-133">\<system.xml.serialization> Element</span></span>](system-xml-serialization-element.md)
