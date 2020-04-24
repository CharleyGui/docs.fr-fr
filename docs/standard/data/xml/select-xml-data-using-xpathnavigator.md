---
title: Sélection de données XML à l'aide de XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: c268c49e-32b9-4171-b782-dcb7b065fa73
ms.openlocfilehash: 99b6b3b6959abf4c8adc313364ad641249bd9bc3
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710165"
---
# <a name="select-xml-data-using-xpathnavigator"></a>Sélection de données XML à l'aide de XPathNavigator
La classe <xref:System.Xml.XPath.XPathNavigator> offre un ensemble de méthodes permettant de sélectionner une collection de nœuds dans un objet <xref:System.Xml.XPath.XPathDocument> ou <xref:System.Xml.XmlDocument> à l’aide d’une expression XPath. Une fois la collection de nœuds sélectionnée, vous pouvez y effectuer des itérations.  
  
## <a name="xpathnavigator-selection-methods"></a>Méthodes de sélection de XPathNavigator  
 La classe <xref:System.Xml.XPath.XPathNavigator> offre un ensemble de méthodes permettant de sélectionner une collection de nœuds dans un objet <xref:System.Xml.XPath.XPathDocument> ou <xref:System.Xml.XmlDocument> à l’aide d’une expression XPath. La classe <xref:System.Xml.XPath.XPathNavigator> fournit également un ensemble de méthodes optimisées permettant une sélection plus rapide des nœuds ancêtres, enfants et descendants qu'avec une expression XPath. La collection de nœuds sélectionnée est retournée dans un objet <xref:System.Xml.XPath.XPathNodeIterator> ou dans un objet <xref:System.Xml.XPath.XPathNavigator> si un seul nœud est sélectionné.  
  
### <a name="selecting-nodes-using-xpath-expressions"></a>Sélection de nœuds à l’aide d’expressions XPath  
 Pour sélectionner une collection de nœuds à l’aide d’une expression XPath, utilisez l’une des méthodes de sélection suivantes.  
  
- <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
 Lorsqu'elles sont appelées, ces méthodes retournent une collection de nœuds dans laquelle vous pouvez vous déplacer librement à l'aide d'un objet <xref:System.Xml.XPath.XPathNodeIterator> ou d'un objet <xref:System.Xml.XPath.XPathNavigator> si un seul nœud est sélectionné.  
  
 La navigation avec un objet <xref:System.Xml.XPath.XPathNodeIterator> n'affecte pas la position de l'objet <xref:System.Xml.XPath.XPathNavigator> utilisé pour le créer. L'objet <xref:System.Xml.XPath.XPathNavigator> retourné par les méthodes <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> est positionné sur le nœud unique retourné et n'affecte pas non plus la position de l'objet<xref:System.Xml.XPath.XPathNavigator> utilisé pour le créer.  
  
 L'exemple suivant illustre la création d'un objet <xref:System.Xml.XPath.XPathNavigator> à partir d'un objet <xref:System.Xml.XPath.XPathDocument>, l'utilisation de la méthode <xref:System.Xml.XPath.XPathNavigator.Select%2A> pour sélectionner des nœuds dans l'objet <xref:System.Xml.XPath.XPathDocument> et l'utilisation de l'objet <xref:System.Xml.XPath.XPathNodeIterator> pour itérer sur les nœuds sélectionnés.  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
Dim nodes As XPathNodeIterator = navigator.Select("/bookstore/book")  
  
While nodes.MoveNext()  
    Console.WriteLine(nodes.Current.Name)  
End While  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
XPathNodeIterator nodes = navigator.Select("/bookstore/book");  
  
while(nodes.MoveNext())  
{  
    Console.WriteLine(nodes.Current.Name);  
}  
```  
  
 L'exemple prend le fichier `books.xml` comme entrée.  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
### <a name="optimized-selection-methods"></a>Méthodes de sélection optimisées  
 Les méthodes <xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A> et <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> de la classe <xref:System.Xml.XPath.XPathNavigator> représentent des expressions XPath couramment utilisées pour extraire des nœuds enfants, descendants et ancêtres. Ces méthodes sont optimisées pour offrir de meilleures performances et sont plus rapides que les expressions XPath correspondantes. Les méthodes <xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A> et <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> sélectionnent des nœuds ancêtres, enfants et descendants d'après une valeur <xref:System.Xml.XPath.XPathNodeType> ou d'après le nom local et l'URI d'espace de noms des nœuds à sélectionner. Les nœuds ancêtres, enfants et descendants sélectionnés sont retournés dans un objet <xref:System.Xml.XPath.XPathNodeIterator>.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [Traitement des données XML à l'aide du modèle de données XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [Évaluation d’expressions XPath à l’aide de XPathNavigator](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)
- [Mise en correspondance de nœuds avec XPathNavigator](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)
- [Types de nœuds reconnus avec les requêtes XPath](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)
- [Requêtes et espaces de noms XPath](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)
- [Expressions XPath compilées](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
