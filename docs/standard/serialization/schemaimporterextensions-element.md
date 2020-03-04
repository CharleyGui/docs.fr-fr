---
title: Élément <schemaImporterExtensions>
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, configuration
- schemaImporterExtensions element
- <schemaImporterExtensions> element
ms.assetid: 465ef2a0-f909-4ac1-9a56-0ead5c849698
ms.openlocfilehash: 5ed80ac370e34d6b62bb2b601cb7bd978228a302
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159817"
---
# <a name="schemaimporterextensions-element"></a><span data-ttu-id="e8c45-102">\<élément schemaImporterExtensions ></span><span class="sxs-lookup"><span data-stu-id="e8c45-102">\<schemaImporterExtensions> Element</span></span>
<span data-ttu-id="e8c45-103">Contient des types utilisés par le <xref:System.Xml.Serialization.XmlSchemaImporter> pour mapper des types XSD en types .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e8c45-103">Contains types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping of XSD types to .NET Framework types.</span></span> <span data-ttu-id="e8c45-104">Pour plus d’informations sur les fichiers de configuration, consultez [Schéma des fichiers de configuration](../../../docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="e8c45-104">For more information about configuration files, see [Configuration File Schema](../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8c45-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e8c45-105">Syntax</span></span>  
  
```xml  
<schemaImporterExtensions>  
    <!-- Add types -->  
</schemaImporterExtensions>  
```  
  
## <a name="child-elements"></a><span data-ttu-id="e8c45-106">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e8c45-106">Child Elements</span></span>  
  
|<span data-ttu-id="e8c45-107">Élément</span><span class="sxs-lookup"><span data-stu-id="e8c45-107">Element</span></span>|<span data-ttu-id="e8c45-108">Description</span><span class="sxs-lookup"><span data-stu-id="e8c45-108">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e8c45-109">\<ajoutez > élément pour \<schemaImporterExtensions ></span><span class="sxs-lookup"><span data-stu-id="e8c45-109">\<add> Element for \<schemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)|<span data-ttu-id="e8c45-110">Ajoute des types utilisés par <xref:System.Xml.Serialization.XmlSchemaImporter> pour créer des mappages.</span><span class="sxs-lookup"><span data-stu-id="e8c45-110">Adds types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> to create mappings.</span></span>|  
  
## <a name="parent-elements"></a><span data-ttu-id="e8c45-111">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e8c45-111">Parent Elements</span></span>  
  
|<span data-ttu-id="e8c45-112">Élément</span><span class="sxs-lookup"><span data-stu-id="e8c45-112">Element</span></span>|<span data-ttu-id="e8c45-113">Description</span><span class="sxs-lookup"><span data-stu-id="e8c45-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e8c45-114">\<system.xml.serialization>, élément</span><span class="sxs-lookup"><span data-stu-id="e8c45-114">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)|<span data-ttu-id="e8c45-115">Élément de niveau supérieur permettant de contrôler la sérialisation XML.</span><span class="sxs-lookup"><span data-stu-id="e8c45-115">The top-level element for controlling XML serialization.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e8c45-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="e8c45-116">Example</span></span>  
 <span data-ttu-id="e8c45-117">L'exemple de code suivant illustre comment ajouter des types utilisés par <xref:System.Xml.Serialization.XmlSchemaImporter> lors du mappage de types XSD en types .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e8c45-117">The following code example illustrates how to add types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> when mapping XSD types to .NET Framework types.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e8c45-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e8c45-118">See also</span></span>

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [<span data-ttu-id="e8c45-119">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="e8c45-119">Configuration File Schema</span></span>](../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="e8c45-120">\<dateTimeSerialization>, élément</span><span class="sxs-lookup"><span data-stu-id="e8c45-120">\<dateTimeSerialization> Element</span></span>](../../../docs/standard/serialization/datetimeserialization-element.md)
- [<span data-ttu-id="e8c45-121">\<ajoutez > élément pour \<schemaImporterExtensions ></span><span class="sxs-lookup"><span data-stu-id="e8c45-121">\<add> Element for \<schemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)
- [<span data-ttu-id="e8c45-122">\<system.xml.serialization>, élément</span><span class="sxs-lookup"><span data-stu-id="e8c45-122">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)
