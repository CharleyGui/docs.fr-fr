---
title: Outil XML Schema Definition et sérialisation XML
ms.date: 03/30/2017
helpviewer_keywords:
- Xsd.exe
- XML serialization, XML Schema Definition tool
- XML Schema Definition tool
- serialization, XML Schema Definition tool
ms.assetid: 3c03f855-f931-47ff-bbc6-50c0367a16e4
ms.openlocfilehash: b51b9a0112893d9a7838155f4af051e7079c8cdd
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588386"
---
# <a name="the-xml-schema-definition-tool-and-xml-serialization"></a>Outil XML Schema Definition et sérialisation XML

L’outil XML Schema Definition[(XML Schema Definition Tool (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)) est installé&reg; avec les outils cadre .NET dans le cadre du kit de développement logiciel Windows (SDK). L’outil a deux principaux objectifs :  
  
- Générer des fichiers de classe C# ou Visual Basic conformes à un schéma de langage XSD (XML Schema Definition) spécifique. L'outil considère un schéma XML comme un argument et génère un fichier qui contient plusieurs classes qui, lorsqu'elles sont sérialisées avec <xref:System.Xml.Serialization.XmlSerializer>, se conforment au schéma. Pour plus d’informations sur la façon d’utiliser l’outil pour générer des classes qui se conforment à un schéma spécifique, consultez [How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents](../../../docs/standard/serialization/xml-schema-def-tool-gen.md).  
  
- Générer un document de schéma XML à partir d’un fichier .dll ou .exe. Pour consulter le schéma d’un ensemble de fichiers que vous avez créé ou d’un ensemble qui a été modifié avec des attributs, passez le fichier DLL ou EXE comme argument à l’outil pour générer le schéma XML. Pour plus d’informations sur la façon d’utiliser l’outil pour générer un document de schéma XML à partir d’un ensemble de classes, consultez [How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents](../../../docs/standard/serialization/xml-schema-def-tool-gen.md).  
  
Pour plus d’informations sur l’utilisation de l’outil, voir [XML Schema Definition Tool (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Data.DataSet>
- [Introduction à la sérialisation XML](../../../docs/standard/serialization/introducing-xml-serialization.md)
- [Outil XML Schema Definition (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)
- <xref:System.Xml.Serialization.XmlSerializer>
- [Guide pratique pour sérialiser un objet](../../../docs/standard/serialization/how-to-serialize-an-object.md)
- [Guide pratique pour désérialiser un objet](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
- [Guide pratique pour utiliser l’outil XML Schema Definition pour la génération de classes et de documents de schéma XML](../../../docs/standard/serialization/xml-schema-def-tool-gen.md)
- [Prise en charge de la liaison de schéma XML](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sh1e66zd(v=vs.100))
