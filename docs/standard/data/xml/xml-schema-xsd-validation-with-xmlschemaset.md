---
title: Validation de schéma XML (XSD) avec XmlSchemaSet
description: Découvrez comment valider des documents XML par rapport à un schéma en langage XSD (XML Schema Definition), à l’aide d’une classe XmlSchemaSet dans .NET.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 359b10eb-ec05-4cc6-ac96-c2b060afc4de
ms.openlocfilehash: 82944fd3fb97c3086ffd47fbd2ba1f3192e6deb4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95672251"
---
# <a name="xml-schema-xsd-validation-with-xmlschemaset"></a>Validation de schéma XML (XSD) avec XmlSchemaSet

Les documents XML peuvent être validés par rapport à un schéma XSD (XML Schema Definition) dans un objet <xref:System.Xml.Schema.XmlSchemaSet>.  
  
## <a name="validate-xml-documents"></a>Valider des documents XML  

 Les documents XML sont validés par la méthode <xref:System.Xml.XmlReader.Create%2A> de la classe <xref:System.Xml.XmlReader>. Pour valider un document XML, vous construisez un objet <xref:System.Xml.XmlReaderSettings> qui contient un schéma de langage XSD (XML Schema Definition) permettant de valider le document XML.  
  
> [!NOTE]
> L’espace de noms <xref:System.Xml.Schema> contient des méthodes d’extension qui facilitent la validation d’une arborescence XML par rapport à un fichier XSD en cas d’utilisation de [LINQ to XML (C#)](../../linq/linq-xml-overview.md) et [LINQ to XML (Visual Basic)](../../linq/linq-xml-overview.md). Pour plus d’informations sur la validation de documents XML avec LINQ to XML, consultez [Comment valider à l’aide de XSD (LINQ to XML) (C#)](../../linq/validate-xsd.md) et [Comment : valider à l’aide de XSD (LINQ to XML) (Visual Basic)](../../linq/validate-xsd.md).
  
 Vous pouvez ajouter un schéma individuel ou un jeu de schémas (sous forme de <xref:System.Xml.Schema.XmlSchemaSet>) à un <xref:System.Xml.Schema.XmlSchemaSet> en le passant en tant que paramètre à la méthode <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> de <xref:System.Xml.Schema.XmlSchemaSet>. Lors de la validation d’un document, l’espace de noms cible du document doit correspondre à l’espace de noms cible du schéma dans le jeu de schémas.  
  
 Voici un exemple de document XML.  
  
 [!code-xml[XSDInference Examples #5](../../../../samples/snippets/xml/VS_Snippets_Data/XSDInference Examples/XML/contosoBooks.xml#5)]  
  
 Voici le schéma qui valide l'exemple de document XML.  
  
 [!code-xml[XSDInference Examples #6](../../../../samples/snippets/xml/VS_Snippets_Data/XSDInference Examples/XML/contosoBooks.xsd#6)]  
  
 Dans l'exemple de code suivant, le schéma ci-dessus est ajouté à la propriété <xref:System.Xml.XmlReaderSettings.Schemas%2A> de l'objet  de l'objet <xref:System.Xml.XmlReaderSettings>. L'objet <xref:System.Xml.XmlReaderSettings> est passé sous forme de paramètre à la méthode <xref:System.Xml.XmlReader.Create%2A> de l'objet <xref:System.Xml.XmlReader> qui valide le document XML ci-dessus.  
  
 La propriété <xref:System.Xml.XmlReaderSettings.ValidationType%2A> de l’objet <xref:System.Xml.XmlReaderSettings> est définie sur `Schema` pour effectuer la validation du document XML par la méthode <xref:System.Xml.XmlReader.Create%2A> de l’objet <xref:System.Xml.XmlReader>. Un objet <xref:System.Xml.Schema.ValidationEventHandler> est ajouté à l’objet <xref:System.Xml.XmlReaderSettings> pour gérer tous les événements <xref:System.Xml.Schema.XmlSeverityType.Warning> ou <xref:System.Xml.Schema.XmlSeverityType.Error> déclenchés par des erreurs trouvées lors du processus de validation du document et du schéma XML.  
  
 [!code-cpp[XmlSchemaSetOverall Example #1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaSetOverall Example/CPP/xmlschemasetexample.cpp#1)]
 [!code-csharp[XmlSchemaSetOverall Example #1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaSetOverall Example/CS/xmlschemasetexample.cs#1)]
 [!code-vb[XmlSchemaSetOverall Example #1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaSetOverall Example/VB/xmlschemasetexample.vb#1)]  
  
## <a name="see-also"></a>Voir aussi

- [XmlSchemaSet pour la compilation de schémas](xmlschemaset-for-schema-compilation.md)
- [Utilisation de schémas XML](working-with-xml-schemas.md)
