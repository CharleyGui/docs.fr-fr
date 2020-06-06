---
title: Élément <system.xml.serialization>
description: Cet article décrit l’élément < System. Xml. Serialization >, qui est l’élément de niveau supérieur pour le contrôle de la sérialisation XML.
ms.date: 03/30/2017
helpviewer_keywords:
- system.xml.serialization element
- XML serialization, configuration
- <system.xml.serialization> element
ms.assetid: 3ce45919-388a-418c-8968-6df0372c73ec
ms.openlocfilehash: f69e80592e9321de64421b977a63b83d8be2ad9e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "84289484"
---
# <a name="systemxmlserialization-element"></a><span data-ttu-id="c8d09-103">Élément \<system.xml.serialization></span><span class="sxs-lookup"><span data-stu-id="c8d09-103">\<system.xml.serialization> Element</span></span>

<span data-ttu-id="c8d09-104">Élément de niveau supérieur permettant de contrôler la sérialisation XML.</span><span class="sxs-lookup"><span data-stu-id="c8d09-104">The top-level element for controlling XML serialization.</span></span> <span data-ttu-id="c8d09-105">Pour plus d’informations sur les fichiers de configuration, consultez [Schéma des fichiers de configuration](../../framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="c8d09-105">For more information about configuration files, see [Configuration File Schema](../../framework/configure-apps/file-schema/index.md).</span></span>

\<configuration>\
\<system.xml.serialization>

## <a name="syntax"></a><span data-ttu-id="c8d09-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c8d09-106">Syntax</span></span>

```xml
<system.xml.serialization>
</system.xml.serialization>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c8d09-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="c8d09-107">Attributes and Elements</span></span>

<span data-ttu-id="c8d09-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="c8d09-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="c8d09-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="c8d09-109">Attributes</span></span>

<span data-ttu-id="c8d09-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="c8d09-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c8d09-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="c8d09-111">Child Elements</span></span>

|<span data-ttu-id="c8d09-112">Élément</span><span class="sxs-lookup"><span data-stu-id="c8d09-112">Element</span></span>|<span data-ttu-id="c8d09-113">Description</span><span class="sxs-lookup"><span data-stu-id="c8d09-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c8d09-114">\<dateTimeSerialization>Appartient</span><span class="sxs-lookup"><span data-stu-id="c8d09-114">\<dateTimeSerialization> Element</span></span>](datetimeserialization-element.md)|<span data-ttu-id="c8d09-115">Détermine le mode de sérialisation des objets <xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="c8d09-115">Determines the serialization mode of <xref:System.DateTime> objects.</span></span>|
|[<span data-ttu-id="c8d09-116">\<schemaImporterExtensions>Appartient</span><span class="sxs-lookup"><span data-stu-id="c8d09-116">\<schemaImporterExtensions> Element</span></span>](schemaimporterextensions-element.md)|<span data-ttu-id="c8d09-117">Contient des types utilisés par le <xref:System.Xml.Serialization.XmlSchemaImporter> pour mapper des types XSD en types .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c8d09-117">Contains types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping of XSD types to .NET Framework types.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c8d09-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="c8d09-118">Parent Elements</span></span>

|<span data-ttu-id="c8d09-119">Élément</span><span class="sxs-lookup"><span data-stu-id="c8d09-119">Element</span></span>|<span data-ttu-id="c8d09-120">Description</span><span class="sxs-lookup"><span data-stu-id="c8d09-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c8d09-121">\<configuration>Appartient</span><span class="sxs-lookup"><span data-stu-id="c8d09-121">\<configuration> Element</span></span>](../../framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="c8d09-122">Élément racine dans chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c8d09-122">The root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|

## <a name="example"></a><span data-ttu-id="c8d09-123">Exemple</span><span class="sxs-lookup"><span data-stu-id="c8d09-123">Example</span></span>

<span data-ttu-id="c8d09-124">L'exemple de code suivant illustre comment spécifier le mode de sérialisation d'un objet <xref:System.DateTime> et l'ajout de types utilisés par le <xref:System.Xml.Serialization.XmlSchemaImporter> lors du mappage de types XSD en types .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c8d09-124">The following code example illustrates how to specify the serialization mode of a <xref:System.DateTime> object, and the addition of types used by the <xref:System.Xml.Serialization.XmlSchemaImporter> when mapping XSD types to .NET Framework types.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="c8d09-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c8d09-125">See also</span></span>

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [<span data-ttu-id="c8d09-126">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="c8d09-126">Configuration File Schema</span></span>](../../framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="c8d09-127">\<dateTimeSerialization>Appartient</span><span class="sxs-lookup"><span data-stu-id="c8d09-127">\<dateTimeSerialization> Element</span></span>](datetimeserialization-element.md)
- [<span data-ttu-id="c8d09-128">\<schemaImporterExtensions>Appartient</span><span class="sxs-lookup"><span data-stu-id="c8d09-128">\<schemaImporterExtensions> Element</span></span>](schemaimporterextensions-element.md)
- [<span data-ttu-id="c8d09-129">\<add>, Élément de\<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="c8d09-129">\<add> Element for \<schemaImporterExtensions></span></span>](add-element-for-schemaimporterextensions.md)
