---
title: Élément <system.xml.serialization>
description: Cet article décrit l’élément <system.xml. Serialization>, qui est l’élément de niveau supérieur pour le contrôle de la sérialisation XML.
ms.date: 03/30/2017
helpviewer_keywords:
- system.xml.serialization element
- XML serialization, configuration
- <system.xml.serialization> element
ms.assetid: 3ce45919-388a-418c-8968-6df0372c73ec
ms.openlocfilehash: 6291799aadc429e943996f2256d773ac36dd370f
ms.sourcegitcommit: 74d05613d6c57106f83f82ce8ee71176874ea3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2020
ms.locfileid: "93282391"
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
|[\<dateTimeSerialization> Appartient](datetimeserialization-element.md)|Détermine le mode de sérialisation des objets <xref:System.DateTime>.|
|[\<schemaImporterExtensions> Appartient](schemaimporterextensions-element.md)|Contient les types utilisés par le <xref:System.Xml.Serialization.XmlSchemaImporter> pour le mappage de types XSD à des types .net.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[\<configuration> Appartient](../../framework/configure-apps/file-schema/configuration-element.md)|Élément racine dans chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|

## <a name="example"></a>Exemple

L’exemple de code suivant montre comment spécifier le mode de sérialisation d’un <xref:System.DateTime> objet, ainsi que l’ajout de types utilisés par <xref:System.Xml.Serialization.XmlSchemaImporter> lors du mappage de types XSD à des types .net.

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
- [Schéma du fichier de configuration](../../framework/configure-apps/file-schema/index.md)
- [\<dateTimeSerialization> Appartient](datetimeserialization-element.md)
- [\<schemaImporterExtensions> Appartient](schemaimporterextensions-element.md)
- [\<add> , Élément de \<schemaImporterExtensions>](add-element-for-schemaimporterextensions.md)
