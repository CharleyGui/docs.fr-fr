---
title: Élément <system.xml.serialization>
description: Cet article décrit l’élément <System. Xml. Serialization>, qui est l’élément de niveau supérieur pour le contrôle de la sérialisation XML.
ms.date: 03/30/2017
helpviewer_keywords:
- system.xml.serialization element
- XML serialization, configuration
- <system.xml.serialization> element
ms.assetid: 3ce45919-388a-418c-8968-6df0372c73ec
ms.openlocfilehash: 1e66220004d561f937d03c506e6f30db4ccc635b
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83380114"
---
# <a name="systemxmlserialization-element"></a><span data-ttu-id="c485f-103">\<Élément System. Xml. Serialization></span><span class="sxs-lookup"><span data-stu-id="c485f-103">\<system.xml.serialization> Element</span></span>

<span data-ttu-id="c485f-104">Élément de niveau supérieur permettant de contrôler la sérialisation XML.</span><span class="sxs-lookup"><span data-stu-id="c485f-104">The top-level element for controlling XML serialization.</span></span> <span data-ttu-id="c485f-105">Pour plus d’informations sur les fichiers de configuration, consultez [Schéma des fichiers de configuration](../../../docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="c485f-105">For more information about configuration files, see [Configuration File Schema](../../../docs/framework/configure-apps/file-schema/index.md).</span></span>

<span data-ttu-id="c485f-106">\<> de configuration </span><span class="sxs-lookup"><span data-stu-id="c485f-106">\<configuration></span></span>\
<span data-ttu-id="c485f-107">\<system.xml.serialization></span><span class="sxs-lookup"><span data-stu-id="c485f-107">\<system.xml.serialization></span></span>

## <a name="syntax"></a><span data-ttu-id="c485f-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c485f-108">Syntax</span></span>

```xml
<system.xml.serialization>
</system.xml.serialization>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c485f-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="c485f-109">Attributes and Elements</span></span>

<span data-ttu-id="c485f-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="c485f-110">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="c485f-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="c485f-111">Attributes</span></span>

<span data-ttu-id="c485f-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="c485f-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c485f-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="c485f-113">Child Elements</span></span>

|<span data-ttu-id="c485f-114">Élément</span><span class="sxs-lookup"><span data-stu-id="c485f-114">Element</span></span>|<span data-ttu-id="c485f-115">Description</span><span class="sxs-lookup"><span data-stu-id="c485f-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c485f-116">\<dateTimeSerialization>, élément</span><span class="sxs-lookup"><span data-stu-id="c485f-116">\<dateTimeSerialization> Element</span></span>](../../../docs/standard/serialization/datetimeserialization-element.md)|<span data-ttu-id="c485f-117">Détermine le mode de sérialisation des objets <xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="c485f-117">Determines the serialization mode of <xref:System.DateTime> objects.</span></span>|
|[<span data-ttu-id="c485f-118">\<schemaImporterExtensions>, élément</span><span class="sxs-lookup"><span data-stu-id="c485f-118">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)|<span data-ttu-id="c485f-119">Contient des types utilisés par le <xref:System.Xml.Serialization.XmlSchemaImporter> pour mapper des types XSD en types .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c485f-119">Contains types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping of XSD types to .NET Framework types.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c485f-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="c485f-120">Parent Elements</span></span>

|<span data-ttu-id="c485f-121">Élément</span><span class="sxs-lookup"><span data-stu-id="c485f-121">Element</span></span>|<span data-ttu-id="c485f-122">Description</span><span class="sxs-lookup"><span data-stu-id="c485f-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c485f-123">\<Élément de> de configuration</span><span class="sxs-lookup"><span data-stu-id="c485f-123">\<configuration> Element</span></span>](../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="c485f-124">Élément racine dans chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c485f-124">The root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|

## <a name="example"></a><span data-ttu-id="c485f-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="c485f-125">Example</span></span>

<span data-ttu-id="c485f-126">L'exemple de code suivant illustre comment spécifier le mode de sérialisation d'un objet <xref:System.DateTime> et l'ajout de types utilisés par le <xref:System.Xml.Serialization.XmlSchemaImporter> lors du mappage de types XSD en types .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c485f-126">The following code example illustrates how to specify the serialization mode of a <xref:System.DateTime> object, and the addition of types used by the <xref:System.Xml.Serialization.XmlSchemaImporter> when mapping XSD types to .NET Framework types.</span></span>

```xml
<system.xml.serialization>
    <xmlSerializer checkDeserializeAdvances="false" />
    <dateTimeSerialization mode = "Local" />
    <schemaImporterExtensions>
        <add
        name = "MobileCapabilities"
        type = "System.Web.Mobile.MobileCapabilities,
        System.Web.Mobile, Version=2.0.0.0, Culture=neutral,
        PublicKeyToken=b03f5f6f11d40a3a" />
    </schemaImporterExtensions>
</system.xml.serialization>
```

## <a name="see-also"></a><span data-ttu-id="c485f-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c485f-127">See also</span></span>

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [<span data-ttu-id="c485f-128">Schéma du fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="c485f-128">Configuration File Schema</span></span>](../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="c485f-129">\<dateTimeSerialization>, élément</span><span class="sxs-lookup"><span data-stu-id="c485f-129">\<dateTimeSerialization> Element</span></span>](../../../docs/standard/serialization/datetimeserialization-element.md)
- [<span data-ttu-id="c485f-130">\<schemaImporterExtensions>, élément</span><span class="sxs-lookup"><span data-stu-id="c485f-130">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)
- [<span data-ttu-id="c485f-131">\<Ajouter> élément pour \< schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="c485f-131">\<add> Element for \<schemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)
