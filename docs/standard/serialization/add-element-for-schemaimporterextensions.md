---
title: Élément <add> pour <schemaImporterExtensions>
description: L' <add> élément ajoute les types utilisés par la classe XmlSchemaImporter pour le mappage des types XSD aux types .NET Framework.
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, configuration
- <add> element for <schemaImporterExtensions> element
ms.assetid: c828a558-094b-441e-9065-790b87315fa0
ms.openlocfilehash: 401d1ba9cc2f97e93d7851f96f73b552e6ed6356
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378478"
---
# <a name="add-element-for-schemaimporterextensions"></a>\<Ajouter> élément pour \< schemaImporterExtensions>
Ajoute des types utilisés par <xref:System.Xml.Serialization.XmlSchemaImporter> pour mapper des types XSD en types .NET Framework. Pour plus d’informations sur les fichiers de configuration, consultez [Schéma des fichiers de configuration](../../../docs/framework/configure-apps/file-schema/index.md).  
  
 \<configuration>  
\<system.xml.serialization>  
\<schemaImporterExtensions>  
\<add>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<add name = "typeName" type="fully qualified type [,Version=version number] [,Culture=culture] [,PublicKeyToken= token]"/>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|**name**|Nom simple utilisé pour rechercher l'instance.|  
|**type**|Obligatoire. Spécifie la classe d'extension de schéma à ajouter. La valeur d’attribut **type** doit figurer sur une ligne et inclure le nom complet du type. Lorsque l'assembly est placé dans le Global Assembly Cache (GAC), il doit également inclure la version, la culture et le jeton de clé publique de l'assembly signé.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|\<schemaImporterExtensions>|Contient les types utilisés par <xref:System.Xml.Serialization.XmlSchemaImporter>.|  
  
## <a name="example"></a>Exemple  
 L'exemple de code suivant ajoute un type d'extension que XmlSchemaImporter peut utiliser lors du mappage de types.  
  
```xml  
<configuration>  
  <system.xml.serialization>  
    <schemaImporterExtensions>  
       <add name="contoso" type="System.Web.Mobile.MobileCapabilities,
       System.Web.Mobile, Version=2.0.0.0, Culture=neutral,
       PublicKeyToken=b03f5f7f11d50a3a" />
    </schemaImporterExtensions>  
  </system.xml.serialization>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- [\<Élément System. Xml. Serialization>](../../../docs/standard/serialization/system-xml-serialization-element.md)
- [\<schemaImporterExtensions>, élément](../../../docs/standard/serialization/schemaimporterextensions-element.md)
