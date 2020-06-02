---
title: Élément <schemaImporterExtensions>
description: L' <schemaImporterExtensions> élément contient les types utilisés par le XmlSchemaImporter pour le mappage de types XSD à des types de .NET Framework.
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, configuration
- schemaImporterExtensions element
- <schemaImporterExtensions> element
ms.assetid: 465ef2a0-f909-4ac1-9a56-0ead5c849698
ms.openlocfilehash: c46c5cb6e01463723f0f2ce3873fb4a6ec0b4e60
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84278400"
---
# <a name="schemaimporterextensions-element"></a><span data-ttu-id="82920-103">Élément \<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="82920-103">\<schemaImporterExtensions> Element</span></span>
<span data-ttu-id="82920-104">Contient des types utilisés par le <xref:System.Xml.Serialization.XmlSchemaImporter> pour mapper des types XSD en types .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="82920-104">Contains types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping of XSD types to .NET Framework types.</span></span> <span data-ttu-id="82920-105">Pour plus d’informations sur les fichiers de configuration, consultez [Schéma des fichiers de configuration](../../framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="82920-105">For more information about configuration files, see [Configuration File Schema](../../framework/configure-apps/file-schema/index.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82920-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="82920-106">Syntax</span></span>  
  
```xml  
<schemaImporterExtensions>  
    <!-- Add types -->  
</schemaImporterExtensions>  
```  
  
## <a name="child-elements"></a><span data-ttu-id="82920-107">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="82920-107">Child Elements</span></span>  
  
|<span data-ttu-id="82920-108">Élément</span><span class="sxs-lookup"><span data-stu-id="82920-108">Element</span></span>|<span data-ttu-id="82920-109">Description</span><span class="sxs-lookup"><span data-stu-id="82920-109">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="82920-110">\<add>, Élément de\<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="82920-110">\<add> Element for \<schemaImporterExtensions></span></span>](add-element-for-schemaimporterextensions.md)|<span data-ttu-id="82920-111">Ajoute des types utilisés par <xref:System.Xml.Serialization.XmlSchemaImporter> pour créer des mappages.</span><span class="sxs-lookup"><span data-stu-id="82920-111">Adds types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> to create mappings.</span></span>|  
  
## <a name="parent-elements"></a><span data-ttu-id="82920-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="82920-112">Parent Elements</span></span>  
  
|<span data-ttu-id="82920-113">Élément</span><span class="sxs-lookup"><span data-stu-id="82920-113">Element</span></span>|<span data-ttu-id="82920-114">Description</span><span class="sxs-lookup"><span data-stu-id="82920-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="82920-115">\<system.xml.serialization>Appartient</span><span class="sxs-lookup"><span data-stu-id="82920-115">\<system.xml.serialization> Element</span></span>](system-xml-serialization-element.md)|<span data-ttu-id="82920-116">Élément de niveau supérieur permettant de contrôler la sérialisation XML.</span><span class="sxs-lookup"><span data-stu-id="82920-116">The top-level element for controlling XML serialization.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="82920-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="82920-117">Example</span></span>  
 <span data-ttu-id="82920-118">L'exemple de code suivant illustre comment ajouter des types utilisés par <xref:System.Xml.Serialization.XmlSchemaImporter> lors du mappage de types XSD en types .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="82920-118">The following code example illustrates how to add types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> when mapping XSD types to .NET Framework types.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="82920-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="82920-119">See also</span></span>

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [<span data-ttu-id="82920-120">Schéma du fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="82920-120">Configuration File Schema</span></span>](../../framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="82920-121">\<dateTimeSerialization>Appartient</span><span class="sxs-lookup"><span data-stu-id="82920-121">\<dateTimeSerialization> Element</span></span>](datetimeserialization-element.md)
- [<span data-ttu-id="82920-122">\<add>, Élément de\<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="82920-122">\<add> Element for \<schemaImporterExtensions></span></span>](add-element-for-schemaimporterextensions.md)
- [<span data-ttu-id="82920-123">\<system.xml.serialization>Appartient</span><span class="sxs-lookup"><span data-stu-id="82920-123">\<system.xml.serialization> Element</span></span>](system-xml-serialization-element.md)
