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
# <a name="schemaimporterextensions-element"></a>\<schemaImporterExtensions>, élément
Contient des types utilisés par le <xref:System.Xml.Serialization.XmlSchemaImporter> pour mapper des types XSD en types .NET Framework. Pour plus d’informations sur les fichiers de configuration, consultez [Schéma des fichiers de configuration](../../../docs/framework/configure-apps/file-schema/index.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<schemaImporterExtensions>  
    <!-- Add types -->  
</schemaImporterExtensions>  
```  
  
## <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<Ajouter> élément pour \< schemaImporterExtensions>](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)|Ajoute des types utilisés par <xref:System.Xml.Serialization.XmlSchemaImporter> pour créer des mappages.|  
  
## <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<Élément System. Xml. Serialization>](../../../docs/standard/serialization/system-xml-serialization-element.md)|Élément de niveau supérieur permettant de contrôler la sérialisation XML.|  
  
## <a name="example"></a>Exemple  
 L'exemple de code suivant illustre comment ajouter des types utilisés par <xref:System.Xml.Serialization.XmlSchemaImporter> lors du mappage de types XSD en types .NET Framework.  
  
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
- [Schéma du fichier de configuration](../../../docs/framework/configure-apps/file-schema/index.md)
- [\<dateTimeSerialization>, élément](../../../docs/standard/serialization/datetimeserialization-element.md)
- [\<Ajouter> élément pour \< schemaImporterExtensions>](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)
- [\<Élément System. Xml. Serialization>](../../../docs/standard/serialization/system-xml-serialization-element.md)
