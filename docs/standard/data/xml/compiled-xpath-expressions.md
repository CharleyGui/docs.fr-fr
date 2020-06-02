---
title: Expressions XPath compilées
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: e25dd95f-b64c-4d8b-a3a4-379e1aa0ad55
ms.openlocfilehash: e74b52e471699fc663504fa42d6c7e502859adda
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291524"
---
# <a name="compiled-xpath-expressions"></a>Expressions XPath compilées
Un objet <xref:System.Xml.XPath.XPathExpression> représente une requête XPath compilée retournée depuis la méthode statique <xref:System.Xml.XPath.XPathExpression.Compile%2A> de la classe <xref:System.Xml.XPath.XPathExpression> ou depuis la méthode <xref:System.Xml.XPath.XPathNavigator.Compile%2A> de la classe <xref:System.Xml.XPath.XPathNavigator>.  
  
## <a name="the-xpathexpression-class"></a>La classe XPathExpression  
 Une requête XPath compilée représentée par un objet <xref:System.Xml.XPath.XPathExpression> est utile si la même requête XPath doit être utilisée plusieurs fois.  
  
 Par exemple, lorsque la méthode <xref:System.Xml.XPath.XPathNavigator.Select%2A> doit être appelée plusieurs fois, au lieu d'utiliser chaque fois une chaîne représentant la requête XPath, utilisez la méthode <xref:System.Xml.XPath.XPathExpression.Compile%2A> de la classe <xref:System.Xml.XPath.XPathExpression> ou la méthode <xref:System.Xml.XPath.XPathNavigator.Compile%2A> de la classe <xref:System.Xml.XPath.XPathNavigator> pour compiler et mettre en cache la requête XPath dans un objet <xref:System.Xml.XPath.XPathExpression> afin de pouvoir la réutiliser et d'améliorer ainsi les performances.  
  
 Une fois compilé, l’objet <xref:System.Xml.XPath.XPathExpression> peut être utilisé comme entrée des méthodes suivantes de la classe <xref:System.Xml.XPath.XPathNavigator> selon le type retourné par la requête XPath.  
  
- <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.XPath.XPathNavigator.Matches%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
 Le tableau suivant décrit chacun des types de retours XPath W3C, leurs équivalents Microsoft .NET Framework et les méthodes avec lesquelles l'objet <xref:System.Xml.XPath.XPathExpression> peut être utilisé selon le type de retour.  
  
|Type de retour XPath W3C|Type .NET Framework équivalent|Description|Méthodes|  
|---------------------------|------------------------------------|-----------------|-------------|  
|`Node set`|<xref:System.Xml.XPath.XPathNodeIterator>|Une collection non triée des nœuds sans doublons créés dans l’ordre du document.|<xref:System.Xml.XPath.XPathNavigator.Select%2A> ou <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>|  
|`Boolean`|<xref:System.Boolean>|Une valeur `true` ou `false`.|<xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> ou<br /><br /> <xref:System.Xml.XPath.XPathNavigator.Matches%2A>|  
|`Number`|<xref:System.Double>|Nombre à virgule flottante.|<xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>|  
|`String`|<xref:System.String>|Séquence de caractères UCS.|<xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>|  
  
> [!NOTE]
> La méthode <xref:System.Xml.XPath.XPathNavigator.Matches%2A> accepte une expression XPath comme paramètre. La méthode <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> retourne un objet <xref:System.Xml.XPath.XPathNavigator>, pas un des types de retours XPath W3C.  
  
### <a name="the-returntype-property"></a>La propriété ReturnType  
 Une fois qu'une requête XPath a été compilée dans un objet <xref:System.Xml.XPath.XPathExpression>, vous pouvez utiliser la propriété <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> de l'objet <xref:System.Xml.XPath.XPathExpression> pour déterminer ce que retourne la requête XPath.  
  
 La propriété <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> retourne une des valeurs d'énumération <xref:System.Xml.XPath.XPathResultType> suivantes, représentant les types de retours XPath W3C.  
  
- <xref:System.Xml.XPath.XPathResultType.Any>  
  
- <xref:System.Xml.XPath.XPathResultType.Boolean>  
  
- <xref:System.Xml.XPath.XPathResultType.Error>  
  
- <xref:System.Xml.XPath.XPathResultType.Navigator>  
  
- <xref:System.Xml.XPath.XPathResultType.NodeSet>  
  
- <xref:System.Xml.XPath.XPathResultType.Number>  
  
- <xref:System.Xml.XPath.XPathResultType.String>  
  
 L'exemple suivant utilise l'objet <xref:System.Xml.XPath.XPathExpression> pour retourner un nombre et une collection de nœuds à partir du fichier `books.xml`. La propriété <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> de chaque objet <xref:System.Xml.XPath.XPathExpression> ainsi que les résultats des méthodes <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> et <xref:System.Xml.XPath.XPathNavigator.Select%2A> sont écrits à la console.  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
' Returns a number.  
Dim query1 As XPathExpression = navigator.Compile("bookstore/book/price/text()*10")  
Console.WriteLine(query1.ReturnType)  
  
Dim number As Double = CType(navigator.Evaluate(query1), Double)  
Console.WriteLine(number)  
  
' Returns a node set.  
Dim query2 As XPathExpression = navigator.Compile("bookstore/book/price")  
Console.WriteLine(query2.ReturnType)  
  
Dim nodes As XPathNodeIterator = navigator.Select(query2)  
nodes.MoveNext()  
Console.WriteLine(nodes.Current.Value)  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
// Returns a number.  
XPathExpression query1 = navigator.Compile("bookstore/book/price/text()*10");  
Console.WriteLine(query1.ReturnType);  
  
Double number = (Double)navigator.Evaluate(query1);  
Console.WriteLine(number);  
  
// Returns a node set.  
XPathExpression query2 = navigator.Compile("bookstore/book/price");  
Console.WriteLine(query2.ReturnType);  
  
XPathNodeIterator nodes = navigator.Select(query2);  
nodes.MoveNext();  
Console.WriteLine(nodes.Current.Value);  
```  
  
 L'exemple prend le fichier `books.xml` comme entrée.  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
### <a name="higher-performance-xpath-expressions"></a>Expressions XPath plus performantes  
 Pour obtenir des performances optimales, utilisez l'expression XPath la plus spécifique possible dans vos requêtes. Par exemple, si le nœud `book` est un enfant du noeud `bookstore` et si le nœud `bookstore` est l'élément de niveau supérieur dans un document XML, il est plus rapide d'utiliser l'expression XPath `/bookstore/book` que `//book`. L’expression XPath `//book` analysera en effet chaque nœud de l’arborescence XML en vue d’identifier les nœuds qui correspondent.  
  
 De plus, l'utilisation des méthodes de navigation dans les nœuds fournies par la classe <xref:System.Xml.XPath.XPathNavigator> peut améliorer les performances par rapport aux méthodes de sélection fournies par la classe <xref:System.Xml.XPath.XPathNavigator> lorsque les critères de sélection sont simples. Par exemple, si vous devez sélectionner le premier enfant du nœud actuel, il est plus rapide d’utiliser la méthode <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A> que d’utiliser l’expression XPath `child::*[1]` et la méthode <xref:System.Xml.XPath.XPathNavigator.Select%2A>.  
  
 Pour plus d'informations sur les méthodes de navigation dans les nœuds fournies par la classe <xref:System.Xml.XPath.XPathNavigator>, consultez [Navigation dans la collection de nœuds à l’aide de XPathNavigator](node-set-navigation-using-xpathnavigator.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [Traitement des données XML à l'aide du modèle de données XPath](process-xml-data-using-the-xpath-data-model.md)
- [Sélection de données XML à l'aide de XPathNavigator](select-xml-data-using-xpathnavigator.md)
- [Évaluation d’expressions XPath à l’aide de XPathNavigator](evaluate-xpath-expressions-using-xpathnavigator.md)
- [Mise en correspondance de nœuds avec XPathNavigator](matching-nodes-using-xpathnavigator.md)
- [Types de nœuds reconnus avec les requêtes XPath](node-types-recognized-with-xpath-queries.md)
- [Requêtes et espaces de noms XPath](xpath-queries-and-namespaces.md)
