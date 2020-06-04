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
ms.openlocfilehash: 282b7d91ec7cfe2f587c67bc9a982f0da22ad925
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410307"
---
# <a name="accessing-xml-in-visual-basic"></a>Accès au code XML dans Visual Basic
Visual Basic fournit des propriétés d’axe XML pour accéder aux structures et les parcourir [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] . Ces propriétés utilisent une syntaxe spéciale pour vous permettre d’accéder aux éléments et aux attributs en spécifiant les noms XML.  
  
 Le tableau suivant répertorie les fonctionnalités de langage qui vous permettent d’accéder aux éléments et attributs XML dans Visual Basic.  
  
### <a name="xml-axis-properties"></a>Propriétés d'axe XML  
  
|Description de la propriété|Exemple|Description|  
|--------------------------|-------------|-----------------|  
|*child, axe*|`contact.<phone>`|Obtient tous les `phone` éléments qui sont des éléments enfants de l' `contact` élément.|  
|*axe d'attribut*|`phone.@type`|Obtient tous les `type` attributs de l' `phone` élément.|  
|*descendant, axe*|`contacts...<name>`|Obtient tous les `name` éléments de l' `contacts` élément, quelle que soit la profondeur de la hiérarchie à laquelle ils se produisent.|  
|*indexeur d’extension*|`contacts...<name>(0)`|Obtient le premier `name` élément de la séquence.|  
|*value*|`contacts...<name>.Value`|Obtient la représentation sous forme de chaîne du premier objet dans la séquence, ou `Nothing` si la séquence est vide.|  
  
## <a name="in-this-section"></a>Dans cette section  
 [Guide pratique : accéder à des éléments descendants XML](how-to-access-xml-descendant-elements.md)  
 Montre comment utiliser une propriété d’axe descendant pour accéder à tous les éléments XML portant un nom spécifié et contenus sous un élément XML spécifié.  
  
 [Comment : accéder à des éléments enfants XML](how-to-access-xml-child-elements.md)  
 Montre comment utiliser une propriété d’axe enfant pour accéder à tous les éléments enfants XML portant un nom spécifié dans un élément XML.  
  
 [Guide pratique : accéder à des attributs XML](how-to-access-xml-attributes.md)  
 Montre comment utiliser une propriété d’axe d’attribut pour accéder à tous les attributs XML portant un nom spécifié dans un élément XML.  
  
 [Comment : déclarer et utiliser des préfixes d'espaces de noms XML](how-to-declare-and-use-xml-namespace-prefixes.md)  
 Montre comment déclarer un préfixe d’espace de noms XML et l’utiliser pour créer des éléments XML et y accéder.  
  
## <a name="related-sections"></a>Sections connexes  
 [Propriétés d'axe XML](../../../language-reference/xml-axis/index.md)  
 Fournit des liens vers des sections décrivant les différentes propriétés d’accès XML.  
  
 [Vue d’ensemble de LINQ to XML en Visual Basic](overview-of-linq-to-xml.md)  
 Fournit une introduction à l’utilisation [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] de dans Visual Basic.  
  
 [Création de code XML dans Visual Basic](creating-xml.md)  
 Fournit une introduction à l’utilisation de littéraux XML dans Visual Basic.  
  
 [Manipulation de code XML dans Visual Basic](manipulating-xml.md)  
 Fournit des liens vers des sections relatives au chargement et à la modification de code XML dans Visual Basic.  
  
 [XML](index.md)  
 Fournit des liens vers des sections décrivant comment utiliser [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dans Visual Basic.
