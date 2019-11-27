---
title: Expressions incorporées en XML
ms.date: 07/20/2015
f1_keywords:
- vb.XmlEmbeddedExpression
helpviewer_keywords:
- embedded expressions [Visual Basic]
- LINQ to XML [Visual Basic], embedded expressions
- XML literals [Visual Basic], embedded expressions
ms.assetid: bf2eb779-b751-4b7c-854f-9f2161482352
ms.openlocfilehash: 0cdb960160457108ddf18c554dae5f5993269833
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74332353"
---
# <a name="embedded-expressions-in-xml-visual-basic"></a>Expressions incorporées en XML (Visual Basic)
Les expressions incorporées vous permettent de créer des littéraux XML qui contiennent des expressions évaluées au moment de l’exécution. La syntaxe d’une expression incorporée est `<%=` `expression` `%>`, qui est identique à la syntaxe utilisée dans ASP.NET.  
  
 Par exemple, vous pouvez créer un littéral d’élément XML, en combinant des expressions incorporées avec un contenu de texte littéral.  
  
 [!code-vb[VbXMLSamples#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#27)]  
  
 Si `isbnNumber` contient l’entier 12345 et `modifiedDate` contient la date 3/5/2006, lorsque ce code s’exécute, la valeur de `book` est :  
  
```xml  
<book category="fiction" isbn="12345">  
  <modifiedDate>3/5/2006</modifiedDate>  
</book>  
```  
  
## <a name="embedded-expression-location-and-validation"></a>Emplacement et validation de l’expression incorporée  
 Les expressions incorporées peuvent apparaître uniquement à certains emplacements dans des expressions de littéral XML. L’emplacement de l’expression détermine les types que l’expression peut retourner et la façon dont `Nothing` est géré. Le tableau suivant décrit les emplacements et types d’expressions incorporés autorisés.  
  
|Emplacement dans le littéral|Type d’expression|Gestion des `Nothing`|  
|---|---|---|  
|Nom d’élément XML|<xref:System.Xml.Linq.XName>|Error|  
|Contenu de l’élément XML|`Object` ou tableau de `Object`|Ignoré|  
|Nom de l’attribut d’élément XML|<xref:System.Xml.Linq.XName>|Erreur, sauf si la valeur de l’attribut est également `Nothing`|  
|Valeur de l’attribut d’élément XML|`Object`|Déclaration d’attribut ignorée|  
|Attribut d’élément XML|<xref:System.Xml.Linq.XAttribute> ou une collection de <xref:System.Xml.Linq.XAttribute>|Ignoré|  
|Élément racine du document XML|<xref:System.Xml.Linq.XElement> ou une collection d’un objet <xref:System.Xml.Linq.XElement> et d’un nombre arbitraire d’objets <xref:System.Xml.Linq.XProcessingInstruction> et <xref:System.Xml.Linq.XComment>|Ignoré|  
  
- Exemple d’expression incorporée dans un nom d’élément XML :  
  
     [!code-vb[VbXMLSamples#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#32)]  
  
- Exemple d’expression incorporée dans le contenu d’un élément XML :  
  
     [!code-vb[VbXMLSamples#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#33)]  
  
- Exemple d’une expression incorporée dans un nom d’attribut d’élément XML :  
  
     [!code-vb[VbXMLSamples#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#34)]  
  
- Exemple d’une expression incorporée dans une valeur d’attribut d’élément XML :  
  
     [!code-vb[VbXMLSamples#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#35)]  
  
- Exemple d’expression incorporée dans un attribut d’élément XML :  
  
     [!code-vb[VbXMLSamples#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#36)]  
  
- Exemple d’expression incorporée dans un élément racine de document XML :  
  
     [!code-vb[VbXMLSamples#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#37)]  
  
 Si vous activez `Option Strict`, le compilateur vérifie que le type de chaque expression incorporée s’étend au type requis. La seule exception concerne l’élément racine d’un document XML, qui est vérifié au moment de l’exécution du code. Si vous compilez sans `Option Strict`, vous pouvez incorporer des expressions de type `Object` et leur type est vérifié au moment de l’exécution.  
  
 Dans les emplacements où le contenu est facultatif, les expressions incorporées qui contiennent des `Nothing` sont ignorées. Cela signifie que vous n’avez pas besoin de vérifier que le contenu de l’élément, les valeurs d’attribut et les éléments de tableau ne sont pas `Nothing` avant d’utiliser un littéral XML. Les valeurs requises, telles que les noms d’élément et d’attribut, ne peuvent pas être `Nothing`.  
  
 Pour plus d’informations sur l’utilisation d’une expression incorporée dans un type particulier de littéral, consultez [littéral de document XML](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md), [littéral d’élément XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).  
  
## <a name="scoping-rules"></a>Règles de portée  
 Le compilateur convertit chaque littéral XML en un appel de constructeur pour le type de littéral approprié. Le contenu littéral et les expressions incorporées dans un littéral XML sont passés comme arguments au constructeur. Cela signifie que tous les éléments de programmation Visual Basic disponibles pour un littéral XML sont également disponibles pour ses expressions incorporées.  
  
 Dans un littéral XML, vous pouvez accéder aux préfixes d’espaces de noms XML déclarés avec l’instruction `Imports`. Vous pouvez déclarer un nouveau préfixe d’espace de noms XML ou occulter un préfixe d’espace de noms XML existant dans un élément à l’aide de l’attribut `xmlns`. Le nouvel espace de noms est disponible pour les nœuds enfants de cet élément, mais pas pour les littéraux XML dans les expressions incorporées.  
  
> [!NOTE]
> Lorsque vous déclarez un préfixe d’espace de noms XML à l’aide de l’attribut d’espace de noms `xmlns`, la valeur de l’attribut doit être une chaîne constante. À cet égard, l’utilisation de l’attribut `xmlns` est semblable à l’utilisation de l’instruction `Imports` pour déclarer un espace de noms XML. Vous ne pouvez pas utiliser une expression incorporée pour spécifier la valeur de l’espace de noms XML.  
  
## <a name="see-also"></a>Voir aussi

- [Création de code XML dans Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [Littéral de document XML](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
- [Littéral d’élément XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [Option Strict (instruction)](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Imports (instruction) (espace de noms et type .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [Vue d’ensemble des littéraux XML](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md)
