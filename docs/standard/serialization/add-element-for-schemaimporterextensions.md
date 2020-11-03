---
title: <add>, élément de <schemaImporterExtensions>
description: L' <add> élément ajoute les types utilisés par la classe XmlSchemaImporter pour le mappage des types XSD aux types .net.
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, configuration
- <add> element for <schemaImporterExtensions> element
ms.assetid: c828a558-094b-441e-9065-790b87315fa0
ms.openlocfilehash: 38d8ebd6e973632b23865ad60e007d9aa21e7da6
ms.sourcegitcommit: 74d05613d6c57106f83f82ce8ee71176874ea3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2020
ms.locfileid: "93281995"
---
# <a name="add-element-for-schemaimporterextensions"></a>\<add>, élément de \<schemaImporterExtensions>

Ajoute des types utilisés par <xref:System.Xml.Serialization.XmlSchemaImporter> pour mapper des types XSD à des types .net. Pour plus d’informations sur les fichiers de configuration, consultez [Schéma des fichiers de configuration](../../framework/configure-apps/file-schema/index.md).  
  
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
- [\<system.xml.serialization> Appartient](system-xml-serialization-element.md)
- [\<schemaImporterExtensions> Appartient](schemaimporterextensions-element.md)
