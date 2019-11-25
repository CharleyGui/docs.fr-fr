---
title: Accès à du code XML
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ to XML [Visual Basic], accessing XML
- Visual Basic code, XML
- accessing XML [Visual Basic], axis properties
- XML [Visual Basic], axis properties
- XML [Visual Basic], accessing
ms.assetid: c47f88b2-3cbc-4bb1-b4b9-be60f71ffc6a
ms.openlocfilehash: 1fa1d94fc710272ac0ba9ea7167989da42a51fcd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351746"
---
# <a name="accessing-xml-in-visual-basic"></a>Accès au code XML dans Visual Basic
Visual Basic provides XML axis properties for accessing and navigating [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] structures. These properties use a special syntax to enable you to access elements and attributes by specifying the XML names.  
  
 The following table lists the language features that enable you to access XML elements and attributes in Visual Basic.  
  
### <a name="xml-axis-properties"></a>Propriétés d'axe XML  
  
|Property description|Exemple|Description|  
|--------------------------|-------------|-----------------|  
|*child axis*|`contact.<phone>`|Gets all `phone` elements that are child elements of the `contact` element.|  
|*attribute axis*|`phone.@type`|Gets all `type` attributes of the `phone` element.|  
|*descendant axis*|`contacts...<name>`|Gets all `name` elements of the `contacts` element, regardless of how deep in the hierarchy they occur.|  
|*extension indexer*|`contacts...<name>(0)`|Gets the first `name` element from the sequence.|  
|*valeur*|`contacts...<name>.Value`|Gets the string representation of the first object in the sequence, or `Nothing` if the sequence is empty.|  
  
## <a name="in-this-section"></a>Dans cette section  
 [Guide pratique : accéder à des éléments descendants XML](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-descendant-elements.md)  
 Shows how to use a descendant axis property to access all XML elements that have a specified name and that are contained under a specified XML element.  
  
 [Guide pratique : accéder à des éléments enfants XML](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-child-elements.md)  
 Shows how to use a child axis property to access all XML child elements that have a specified name in an XML element.  
  
 [Guide pratique : accéder à des attributs XML](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-attributes.md)  
 Shows how to use an attribute axis property to access all XML attributes that have a specified name in an XML element.  
  
 [Guide pratique : déclarer et utiliser des préfixes d’espaces de noms XML](../../../../visual-basic/programming-guide/language-features/xml/how-to-declare-and-use-xml-namespace-prefixes.md)  
 Shows how to declare an XML namespace prefix and use it to create and access XML elements.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Propriétés d’axe XML](../../../../visual-basic/language-reference/xml-axis/index.md)  
 Provides links to sections describing the various XML access properties.  
  
 [Vue d’ensemble de LINQ to XML en Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md)  
 Provides an introduction to using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] in Visual Basic.  
  
 [Création de code XML dans Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 Provides an introduction to using XML literals in Visual Basic.  
  
 [Manipulation de code XML dans Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)  
 Provides links to sections about loading and modifying XML in Visual Basic.  
  
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 Provides links to sections describing how to use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] in Visual Basic.
