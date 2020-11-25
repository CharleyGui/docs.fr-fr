---
title: Élément <schemaImporterExtensions>
description: L' <schemaImporterExtensions> élément contient les types utilisés par le XmlSchemaImporter pour le mappage de types XSD à des types .net.
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, configuration
- schemaImporterExtensions element
- <schemaImporterExtensions> element
ms.assetid: 465ef2a0-f909-4ac1-9a56-0ead5c849698
ms.openlocfilehash: 6b644ed1112b748be4dd301d6fa6f2a6416dc67e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722139"
---
# <a name="schemaimporterextensions-element"></a>\<schemaImporterExtensions>, élément

Contient les types utilisés par le <xref:System.Xml.Serialization.XmlSchemaImporter> pour le mappage de types XSD à des types .net. Pour plus d’informations sur les fichiers de configuration, consultez [Schéma des fichiers de configuration](../../framework/configure-apps/file-schema/index.md).  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<schemaImporterExtensions>  
    <!-- Add types -->  
</schemaImporterExtensions>  
```  
  
## <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<add> , Élément de \<schemaImporterExtensions>](add-element-for-schemaimporterextensions.md)|Ajoute des types utilisés par <xref:System.Xml.Serialization.XmlSchemaImporter> pour créer des mappages.|  
  
## <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<system.xml.serialization> Appartient](system-xml-serialization-element.md)|Élément de niveau supérieur permettant de contrôler la sérialisation XML.|  
  
## <a name="example"></a>Exemple  

 L’exemple de code suivant montre comment ajouter des types utilisés par le lors du <xref:System.Xml.Serialization.XmlSchemaImporter> mappage de types XSD à des types .net.  
  
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
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [Schéma du fichier de configuration](../../framework/configure-apps/file-schema/index.md)
- [\<dateTimeSerialization> Appartient](datetimeserialization-element.md)
- [\<add> , Élément de \<schemaImporterExtensions>](add-element-for-schemaimporterextensions.md)
- [\<system.xml.serialization> Appartient](system-xml-serialization-element.md)
