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
Visual Basic fournit des propriétés d’axe XML pour accéder aux structures [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] et les parcourir. Ces propriétés utilisent une syntaxe spéciale pour vous permettre d’accéder aux éléments et aux attributs en spécifiant les noms XML.  
  
 Le tableau suivant répertorie les fonctionnalités de langage qui vous permettent d’accéder aux éléments et attributs XML dans Visual Basic.  
  
### <a name="xml-axis-properties"></a>Propriétés d'axe XML  
  
|Description de la propriété|Exemple|Description|  
|--------------------------|-------------|-----------------|  
|*axe enfant*|`contact.<phone>`|Obtient tous les éléments `phone` qui sont des éléments enfants de l’élément `contact`.|  
|*axe d’attribut*|`phone.@type`|Obtient tous les attributs `type` de l’élément `phone`.|  
|*axe descendant*|`contacts...<name>`|Obtient tous les éléments `name` de l’élément `contacts`, quelle que soit la profondeur de la hiérarchie à laquelle ils se produisent.|  
|*indexeur d’extension*|`contacts...<name>(0)`|Obtient le premier élément `name` de la séquence.|  
|*valeur*|`contacts...<name>.Value`|Obtient la représentation sous forme de chaîne du premier objet dans la séquence, ou `Nothing` si la séquence est vide.|  
  
## <a name="in-this-section"></a>Dans cette section  
 [Guide pratique : accéder à des éléments descendants XML](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-descendant-elements.md)  
 Montre comment utiliser une propriété d’axe descendant pour accéder à tous les éléments XML portant un nom spécifié et contenus sous un élément XML spécifié.  
  
 [Guide pratique : accéder à des éléments enfants XML](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-child-elements.md)  
 Montre comment utiliser une propriété d’axe enfant pour accéder à tous les éléments enfants XML portant un nom spécifié dans un élément XML.  
  
 [Guide pratique : accéder à des attributs XML](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-attributes.md)  
 Montre comment utiliser une propriété d’axe d’attribut pour accéder à tous les attributs XML portant un nom spécifié dans un élément XML.  
  
 [Guide pratique : déclarer et utiliser des préfixes d’espaces de noms XML](../../../../visual-basic/programming-guide/language-features/xml/how-to-declare-and-use-xml-namespace-prefixes.md)  
 Montre comment déclarer un préfixe d’espace de noms XML et l’utiliser pour créer des éléments XML et y accéder.  
  
## <a name="related-sections"></a>Sections connexes  
 [Propriétés d’axe XML](../../../../visual-basic/language-reference/xml-axis/index.md)  
 Fournit des liens vers des sections décrivant les différentes propriétés d’accès XML.  
  
 [Vue d’ensemble de LINQ to XML en Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md)  
 Fournit une introduction à l’utilisation de [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dans Visual Basic.  
  
 [Création de code XML dans Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 Fournit une introduction à l’utilisation de littéraux XML dans Visual Basic.  
  
 [Manipulation de code XML dans Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)  
 Fournit des liens vers des sections relatives au chargement et à la modification de code XML dans Visual Basic.  
  
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 Fournit des liens vers des sections décrivant l’utilisation de [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dans Visual Basic.
