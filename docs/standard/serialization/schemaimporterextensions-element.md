---
title: Élément <schemaImporterExtensions>
description: L' <schemaImporterExtensions> élément contient les types utilisés par le XmlSchemaImporter pour le mappage de types XSD à des types de .NET Framework.
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, configuration
- schemaImporterExtensions element
- <schemaImporterExtensions> element
ms.assetid: 465ef2a0-f909-4ac1-9a56-0ead5c849698
ms.openlocfilehash: 5b9820ccdf2c75bed9beda72358c4c4d82ff9ff7
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379791"
---
# <a name="schemaimporterextensions-element"></a><span data-ttu-id="27f91-103">\<schemaImporterExtensions>, élément</span><span class="sxs-lookup"><span data-stu-id="27f91-103">\<schemaImporterExtensions> Element</span></span>
<span data-ttu-id="27f91-104">Contient des types utilisés par le <xref:System.Xml.Serialization.XmlSchemaImporter> pour mapper des types XSD en types .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="27f91-104">Contains types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping of XSD types to .NET Framework types.</span></span> <span data-ttu-id="27f91-105">Pour plus d’informations sur les fichiers de configuration, consultez [Schéma des fichiers de configuration](../../../docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="27f91-105">For more information about configuration files, see [Configuration File Schema](../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27f91-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="27f91-106">Syntax</span></span>  
  
```xml  
<schemaImporterExtensions>  
    <!-- Add types -->  
</schemaImporterExtensions>  
```  
  
## <a name="child-elements"></a><span data-ttu-id="27f91-107">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="27f91-107">Child Elements</span></span>  
  
|<span data-ttu-id="27f91-108">Élément</span><span class="sxs-lookup"><span data-stu-id="27f91-108">Element</span></span>|<span data-ttu-id="27f91-109">Description</span><span class="sxs-lookup"><span data-stu-id="27f91-109">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="27f91-110">\<Ajouter> élément pour \< schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="27f91-110">\<add> Element for \<schemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)|<span data-ttu-id="27f91-111">Ajoute des types utilisés par <xref:System.Xml.Serialization.XmlSchemaImporter> pour créer des mappages.</span><span class="sxs-lookup"><span data-stu-id="27f91-111">Adds types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> to create mappings.</span></span>|  
  
## <a name="parent-elements"></a><span data-ttu-id="27f91-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="27f91-112">Parent Elements</span></span>  
  
|<span data-ttu-id="27f91-113">Élément</span><span class="sxs-lookup"><span data-stu-id="27f91-113">Element</span></span>|<span data-ttu-id="27f91-114">Description</span><span class="sxs-lookup"><span data-stu-id="27f91-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="27f91-115">\<Élément System. Xml. Serialization></span><span class="sxs-lookup"><span data-stu-id="27f91-115">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)|<span data-ttu-id="27f91-116">Élément de niveau supérieur permettant de contrôler la sérialisation XML.</span><span class="sxs-lookup"><span data-stu-id="27f91-116">The top-level element for controlling XML serialization.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="27f91-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="27f91-117">Example</span></span>  
 <span data-ttu-id="27f91-118">L'exemple de code suivant illustre comment ajouter des types utilisés par <xref:System.Xml.Serialization.XmlSchemaImporter> lors du mappage de types XSD en types .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="27f91-118">The following code example illustrates how to add types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> when mapping XSD types to .NET Framework types.</span></span>  
  
```xml  
<system.xml.serialization>  
    <schemaImporterExtensions>  
        <add name = "MobileCapabilities" type =
        "System.Web.Mobile.MobileCapabilities,
        System.Web.Mobile, Version - 2.0.0.0, Culture = neutral,
        PublicKeyToken = b03f5f6f11d40a3a" />  
    </schemaImporterExtensions>  
</system.xml.serialization>  
```  
  
## <a name="see-also"></a><span data-ttu-id="27f91-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="27f91-119">See also</span></span>

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [<span data-ttu-id="27f91-120">Schéma du fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="27f91-120">Configuration File Schema</span></span>](../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="27f91-121">\<dateTimeSerialization>, élément</span><span class="sxs-lookup"><span data-stu-id="27f91-121">\<dateTimeSerialization> Element</span></span>](../../../docs/standard/serialization/datetimeserialization-element.md)
- [<span data-ttu-id="27f91-122">\<Ajouter> élément pour \< schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="27f91-122">\<add> Element for \<schemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)
- [<span data-ttu-id="27f91-123">\<Élément System. Xml. Serialization></span><span class="sxs-lookup"><span data-stu-id="27f91-123">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)
