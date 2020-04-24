---
title: Élément <system.xml.serialization>
ms.date: 03/30/2017
helpviewer_keywords:
- system.xml.serialization element
- XML serialization, configuration
- <system.xml.serialization> element
ms.assetid: 3ce45919-388a-418c-8968-6df0372c73ec
ms.openlocfilehash: 02027a238bc9a2f82963ea841584d2bb3c6446c6
ms.sourcegitcommit: 52e588dc2ee74d484cd07ac60076be25cbf777ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67410543"
---
# <a name="systemxmlserialization-element"></a><span data-ttu-id="ef442-102">\<Élément System. Xml. Serialization></span><span class="sxs-lookup"><span data-stu-id="ef442-102">\<system.xml.serialization> Element</span></span>

<span data-ttu-id="ef442-103">Élément de niveau supérieur permettant de contrôler la sérialisation XML.</span><span class="sxs-lookup"><span data-stu-id="ef442-103">The top-level element for controlling XML serialization.</span></span> <span data-ttu-id="ef442-104">Pour plus d’informations sur les fichiers de configuration, consultez [Schéma des fichiers de configuration](../../../docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="ef442-104">For more information about configuration files, see [Configuration File Schema](../../../docs/framework/configure-apps/file-schema/index.md).</span></span>

<span data-ttu-id="ef442-105">\<> de configuration </span><span class="sxs-lookup"><span data-stu-id="ef442-105">\<configuration></span></span>\
<span data-ttu-id="ef442-106">\<system.xml.serialization></span><span class="sxs-lookup"><span data-stu-id="ef442-106">\<system.xml.serialization></span></span>

## <a name="syntax"></a><span data-ttu-id="ef442-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ef442-107">Syntax</span></span>

```xml
<system.xml.serialization>
</system.xml.serialization>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ef442-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="ef442-108">Attributes and Elements</span></span>

<span data-ttu-id="ef442-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="ef442-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="ef442-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="ef442-110">Attributes</span></span>

<span data-ttu-id="ef442-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="ef442-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ef442-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="ef442-112">Child Elements</span></span>

|<span data-ttu-id="ef442-113">Élément</span><span class="sxs-lookup"><span data-stu-id="ef442-113">Element</span></span>|<span data-ttu-id="ef442-114">Description</span><span class="sxs-lookup"><span data-stu-id="ef442-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ef442-115">\<dateTimeSerialization>, élément</span><span class="sxs-lookup"><span data-stu-id="ef442-115">\<dateTimeSerialization> Element</span></span>](../../../docs/standard/serialization/datetimeserialization-element.md)|<span data-ttu-id="ef442-116">Détermine le mode de sérialisation des objets <xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="ef442-116">Determines the serialization mode of <xref:System.DateTime> objects.</span></span>|
|[<span data-ttu-id="ef442-117">\<schemaImporterExtensions>, élément</span><span class="sxs-lookup"><span data-stu-id="ef442-117">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)|<span data-ttu-id="ef442-118">Contient des types utilisés par le <xref:System.Xml.Serialization.XmlSchemaImporter> pour mapper des types XSD en types .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ef442-118">Contains types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping of XSD types to .NET Framework types.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="ef442-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="ef442-119">Parent Elements</span></span>

|<span data-ttu-id="ef442-120">Élément</span><span class="sxs-lookup"><span data-stu-id="ef442-120">Element</span></span>|<span data-ttu-id="ef442-121">Description</span><span class="sxs-lookup"><span data-stu-id="ef442-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ef442-122">\<Élément de> de configuration</span><span class="sxs-lookup"><span data-stu-id="ef442-122">\<configuration> Element</span></span>](../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="ef442-123">Élément racine dans chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ef442-123">The root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|

## <a name="example"></a><span data-ttu-id="ef442-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="ef442-124">Example</span></span>

<span data-ttu-id="ef442-125">L'exemple de code suivant illustre comment spécifier le mode de sérialisation d'un objet <xref:System.DateTime> et l'ajout de types utilisés par le <xref:System.Xml.Serialization.XmlSchemaImporter> lors du mappage de types XSD en types .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ef442-125">The following code example illustrates how to specify the serialization mode of a <xref:System.DateTime> object, and the addition of types used by the <xref:System.Xml.Serialization.XmlSchemaImporter> when mapping XSD types to .NET Framework types.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="ef442-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ef442-126">See also</span></span>

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [<span data-ttu-id="ef442-127">Schéma du fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="ef442-127">Configuration File Schema</span></span>](../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="ef442-128">\<dateTimeSerialization>, élément</span><span class="sxs-lookup"><span data-stu-id="ef442-128">\<dateTimeSerialization> Element</span></span>](../../../docs/standard/serialization/datetimeserialization-element.md)
- [<span data-ttu-id="ef442-129">\<schemaImporterExtensions>, élément</span><span class="sxs-lookup"><span data-stu-id="ef442-129">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)
- [<span data-ttu-id="ef442-130">\<Ajouter> élément pour \<SchemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="ef442-130">\<add> Element for \<schemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)
