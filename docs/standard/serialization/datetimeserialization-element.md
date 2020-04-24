---
title: Élément <dateTimeSerialization>
ms.date: 03/30/2017
helpviewer_keywords:
- dateTimeSerialization element
- XML serialization, configuration
- <dateTimeSerialization> element
ms.assetid: 90fda55c-7730-41e9-bc4b-6423a4b920af
ms.openlocfilehash: 180a4942dd4b701b56fe4788d5f8cd8607faaedd
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459266"
---
# <a name="datetimeserialization-element"></a><span data-ttu-id="0c386-102">\<dateTimeSerialization>, élément</span><span class="sxs-lookup"><span data-stu-id="0c386-102">\<dateTimeSerialization> Element</span></span>
<span data-ttu-id="0c386-103">Détermine le mode de sérialisation des objets <xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="0c386-103">Determines the serialization mode of <xref:System.DateTime> objects.</span></span>  
  
 <span data-ttu-id="0c386-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="0c386-104">\<configuration></span></span>  
<span data-ttu-id="0c386-105">\<dateTimeSerialization></span><span class="sxs-lookup"><span data-stu-id="0c386-105">\<dateTimeSerialization></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c386-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0c386-106">Syntax</span></span>  
  
```xml  
<dateTimeSerialization  
    mode = "Roundtrip|Local"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0c386-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="0c386-107">Attributes and Elements</span></span>  
 <span data-ttu-id="0c386-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="0c386-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0c386-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="0c386-109">Attributes</span></span>  
  
|<span data-ttu-id="0c386-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="0c386-110">Attributes</span></span>|<span data-ttu-id="0c386-111">Description</span><span class="sxs-lookup"><span data-stu-id="0c386-111">Description</span></span>|  
|----------------|-----------------|  
|`mode`|<span data-ttu-id="0c386-112">facultatif.</span><span class="sxs-lookup"><span data-stu-id="0c386-112">Optional.</span></span> <span data-ttu-id="0c386-113">Spécifie le mode de sérialisation.</span><span class="sxs-lookup"><span data-stu-id="0c386-113">Specifies the serialization mode.</span></span> <span data-ttu-id="0c386-114">Affectez-le à l'une des valeurs <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>.</span><span class="sxs-lookup"><span data-stu-id="0c386-114">Set to one of the <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode> values.</span></span> <span data-ttu-id="0c386-115">La valeur par défaut est **RoundTrip**.</span><span class="sxs-lookup"><span data-stu-id="0c386-115">The default is **RoundTrip**.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0c386-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="0c386-116">Child Elements</span></span>  
 <span data-ttu-id="0c386-117">Aucune.</span><span class="sxs-lookup"><span data-stu-id="0c386-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0c386-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="0c386-118">Parent Elements</span></span>  
  
|<span data-ttu-id="0c386-119">Élément</span><span class="sxs-lookup"><span data-stu-id="0c386-119">Element</span></span>|<span data-ttu-id="0c386-120">Description</span><span class="sxs-lookup"><span data-stu-id="0c386-120">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0c386-121">system.xml.serialization</span><span class="sxs-lookup"><span data-stu-id="0c386-121">system.xml.serialization</span></span>|<span data-ttu-id="0c386-122">Élément de niveau supérieur permettant de contrôler la sérialisation XML.</span><span class="sxs-lookup"><span data-stu-id="0c386-122">The top-level element for controlling XML serialization.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0c386-123">Notes</span><span class="sxs-lookup"><span data-stu-id="0c386-123">Remarks</span></span>  
 <span data-ttu-id="0c386-124">Dans les versions 1,0, 1,1, 2,0 et versions ultérieures de la .NET Framework, quand cette propriété est **Local**définie sur <xref:System.DateTime> local, les objets sont toujours mis en forme en tant qu’heure locale.</span><span class="sxs-lookup"><span data-stu-id="0c386-124">In versions 1.0, 1.1, 2.0 and later versions of the .NET Framework, when this property is set to **Local**, <xref:System.DateTime> objects are always formatted as the local time.</span></span> <span data-ttu-id="0c386-125">Autrement dit, les informations du fuseau horaire local sont toujours incluses avec les données sérialisées.</span><span class="sxs-lookup"><span data-stu-id="0c386-125">That is, local time zone information is always included with the serialized data.</span></span> <span data-ttu-id="0c386-126">Affectez la valeur **Local** à cette propriété pour garantir la compatibilité avec les versions antérieures du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0c386-126">Set this property to **Local** to ensure compatibility with older versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="0c386-127">Dans la version 2,0 et les versions ultérieures du .NET Framework dont cette propriété a **Roundtrip**la valeur <xref:System.DateTime> Roundtrip, les objets sont examinés pour déterminer s’ils se trouvent dans le fuseau horaire local, UTC ou non spécifié.</span><span class="sxs-lookup"><span data-stu-id="0c386-127">In version 2.0 and later versions of the .NET Framework that have this property set to **Roundtrip**, <xref:System.DateTime> objects are examined to determine whether they are in the local, UTC, or an unspecified time zone.</span></span> <span data-ttu-id="0c386-128">Les objets <xref:System.DateTime> sont ensuite sérialisés de manière à ce que ces informations soient conservées.</span><span class="sxs-lookup"><span data-stu-id="0c386-128">The <xref:System.DateTime> objects are then serialized in such a way that this information is preserved.</span></span> <span data-ttu-id="0c386-129">Il s'agit du comportement par défaut, recommandé pour toutes les nouvelles applications qui ne communiquent pas avec les versions antérieures du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0c386-129">This is the default behavior and is the recommended behavior for all new applications that do not communicate with older versions of the framework.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c386-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0c386-130">See also</span></span>

- <xref:System.DateTime>
- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [<span data-ttu-id="0c386-131">Schéma du fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="0c386-131">Configuration File Schema</span></span>](../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="0c386-132">\<schemaImporterExtensions>, élément</span><span class="sxs-lookup"><span data-stu-id="0c386-132">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)
- [<span data-ttu-id="0c386-133">\<Ajouter> élément pour \<SchemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="0c386-133">\<add> Element for \<schemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)
- [<span data-ttu-id="0c386-134">\<Élément System. Xml. Serialization></span><span class="sxs-lookup"><span data-stu-id="0c386-134">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)
