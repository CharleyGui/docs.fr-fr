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
# <a name="systemxmlserialization-element"></a>Élément \<system.xml.serialization>

Élément de niveau supérieur permettant de contrôler la sérialisation XML. Pour plus d’informations sur les fichiers de configuration, consultez [Schéma des fichiers de configuration](../../framework/configure-apps/file-schema/index.md).

\<configuration>\
\<system.xml.serialization>

## <a name="syntax"></a>Syntaxe

```xml
<system.xml.serialization>
</system.xml.serialization>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[\<dateTimeSerialization>Appartient](datetimeserialization-element.md)|Détermine le mode de sérialisation des objets <xref:System.DateTime>.|
|[\<schemaImporterExtensions>Appartient](schemaimporterextensions-element.md)|Contient des types utilisés par le <xref:System.Xml.Serialization.XmlSchemaImporter> pour mapper des types XSD en types .NET Framework.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[\<configuration>Appartient](../../framework/configure-apps/file-schema/configuration-element.md)|Élément racine dans chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|

## <a name="example"></a>Exemple

L'exemple de code suivant illustre comment spécifier le mode de sérialisation d'un objet <xref:System.DateTime> et l'ajout de types utilisés par le <xref:System.Xml.Serialization.XmlSchemaImporter> lors du mappage de types XSD en types .NET Framework.

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

## <a name="see-also"></a>Voir aussi

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [Schéma des fichiers de configuration](../../framework/configure-apps/file-schema/index.md)
- [\<dateTimeSerialization>Appartient](datetimeserialization-element.md)
- [\<schemaImporterExtensions>Appartient](schemaimporterextensions-element.md)
- [\<add>, Élément de\<schemaImporterExtensions>](add-element-for-schemaimporterextensions.md)
