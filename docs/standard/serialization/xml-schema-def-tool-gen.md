---
title: "Comment : utiliser l'outil XML Schema Definition pour générer des classes et des documents de schéma XML"
description: Découvrez comment utiliser l’outil XML Schema Definition pour générer un schéma XML décrivant une classe ou pour générer la classe définie par un schéma XML.
ms.date: 03/30/2017
helpviewer_keywords:
- generating XML classes using XML Schema Definition tool
- generating XML Schema Document using XML Schema Definition tool
- XML Schema Definition tool, using to generate classes that conform to specific schema
- XML Schema Definition tool, using to generate XML Schema Document
ms.assetid: 51f0edc3-993d-4051-b7f2-77753694d3d1
ms.openlocfilehash: 0e4e84ea7e11b2e7a00c852d4a2075747c71267e
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288964"
---
# <a name="how-to-use-the-xml-schema-definition-tool-to-generate-classes-and-xml-schema-documents"></a>Comment : utiliser l'outil XML Schema Definition pour générer des classes et des documents de schéma XML
L'outil XML Schema Definition (Xsd.exe) vous permet de générer un schéma XML qui décrit une classe ou de générer la classe définie par un schéma XML. Les procédures suivantes indiquent comment exécuter ces opérations.

L’outil XML Schema Definition (XSD. exe) se trouve généralement à l’emplacement suivant : \
_C : \\ Program Files (x86) \\ Microsoft SDK \\ Windows \\ {version} \\ bin \\ netfx {version} Tools\\_

### <a name="to-generate-classes-that-conform-to-a-specific-schema"></a>Pour générer des classes qui se conforment à un schéma spécifique  
  
1. Ouvrez une invite de commandes.  
  
2. Passez par exemple le schéma XML en tant qu'argument à l'outil XML Schema Definition, qui crée un ensemble de classes correspondant précisément au schéma XML :  
  
    ```console  
    xsd mySchema.xsd  
    ```  
  
     L'outil ne peut traiter que les schémas qui référencent la spécification XML du W3C (World Wide Web Consortium) du 16 mars 2001. En d’autres termes, l’espace de noms du schéma XML doit être « http://www.w3.org/2001/XMLSchema », comme indiqué dans l’exemple suivant.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <xs:schema attributeFormDefault="qualified" elementFormDefault="qualified" targetNamespace="" xmlns:xs="http://www.w3.org/2001/XMLSchema" />  
    ```  
  
3. Modifiez si nécessaire les classes avec les méthodes, les propriétés ou les champs. Pour plus d’informations sur la modification d’une classe avec des attributs, consultez [Contrôle de la sérialisation XML à l’aide d’attributs](controlling-xml-serialization-using-attributes.md) et [Attributs qui contrôlent la sérialisation encodée selon le protocole SOAP](attributes-that-control-encoded-soap-serialization.md).  
  
 Il est souvent utile d'examiner le schéma du flux de données XML généré lorsque les instances d'une ou de plusieurs classes sont sérialisées. Par exemple, vous pouvez publier votre schéma pour d'autres utilisateurs ou le comparer à un schéma auquel vous tentez de vous conformer.  
  
#### <a name="to-generate-an-xml-schema-document-from-a-set-of-classes"></a>Pour générer un document de schéma XML à partir d'un ensemble de classes  
  
1. Compilez la ou les classes dans une DLL.  
  
2. Ouvrez une invite de commandes.  
  
3. Passez la DLL en tant qu'argument dans Xsd.exe, par exemple :  
  
    ```console  
    xsd MyFile.dll  
    ```  
  
     Le ou les schémas sont écrits et commencent par le nom "schema0.xsd."  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Data.DataSet>
- [Outil XML Schema Definition et sérialisation XML](the-xml-schema-definition-tool-and-xml-serialization.md)
- [Introduction à la sérialisation XML](introducing-xml-serialization.md)
- [Outil XML Schema Definition (XSD. exe)](xml-schema-definition-tool-xsd-exe.md)
- <xref:System.Xml.Serialization.XmlSerializer>
- [Guide pratique pour sérialiser un objet](how-to-serialize-an-object.md)
- [Guide pratique pour désérialiser un objet](how-to-deserialize-an-object.md)
