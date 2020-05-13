---
title: Élément <dateTimeSerialization>
description: Cet article décrit l' <dateTimeSerialization> élément, qui détermine le mode de sérialisation des objets DateTime.
ms.date: 03/30/2017
helpviewer_keywords:
- dateTimeSerialization element
- XML serialization, configuration
- <dateTimeSerialization> element
ms.assetid: 90fda55c-7730-41e9-bc4b-6423a4b920af
ms.openlocfilehash: 652a88e25f59cd905e47ef71351e47e67f375286
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83375824"
---
# <a name="datetimeserialization-element"></a>\<dateTimeSerialization>, élément
Détermine le mode de sérialisation des objets <xref:System.DateTime>.  
  
 \<configuration>  
\<dateTimeSerialization>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<dateTimeSerialization  
    mode = "Roundtrip|Local"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attributs|Description|  
|----------------|-----------------|  
|`mode`|facultatif. Spécifie le mode de sérialisation. Affectez-le à l'une des valeurs <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>. La valeur par défaut est **RoundTrip**.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|system.xml.serialization|Élément de niveau supérieur permettant de contrôler la sérialisation XML.|  
  
## <a name="remarks"></a>Remarks  
 Dans les versions 1,0, 1,1, 2,0 et versions ultérieures de la .NET Framework, quand cette propriété est définie sur **local**, <xref:System.DateTime> les objets sont toujours mis en forme en tant qu’heure locale. Autrement dit, les informations du fuseau horaire local sont toujours incluses avec les données sérialisées. Affectez la valeur **Local** à cette propriété pour garantir la compatibilité avec les versions antérieures du .NET Framework.  
  
 Dans la version 2,0 et les versions ultérieures du .NET Framework dont cette propriété a la valeur **roundtrip**, les <xref:System.DateTime> objets sont examinés pour déterminer s’ils se trouvent dans le fuseau horaire local, UTC ou non spécifié. Les objets <xref:System.DateTime> sont ensuite sérialisés de manière à ce que ces informations soient conservées. Il s'agit du comportement par défaut, recommandé pour toutes les nouvelles applications qui ne communiquent pas avec les versions antérieures du .NET Framework.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.DateTime>
- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [Schéma du fichier de configuration](../../../docs/framework/configure-apps/file-schema/index.md)
- [\<schemaImporterExtensions>, élément](../../../docs/standard/serialization/schemaimporterextensions-element.md)
- [\<Ajouter> élément pour \< schemaImporterExtensions>](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)
- [\<Élément System. Xml. Serialization>](../../../docs/standard/serialization/system-xml-serialization-element.md)
