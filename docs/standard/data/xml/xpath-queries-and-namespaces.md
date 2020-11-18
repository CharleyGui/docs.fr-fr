---
title: Requêtes et espaces de noms XPath
description: En savoir plus sur les requêtes XPath & les espaces de noms. Les requêtes XPath connaissent les espaces de noms dans un document XML & peuvent utiliser des préfixes d’espaces de noms pour qualifier des noms d’attributs d’élément &.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ef6402be-2f8e-4be2-8d3e-a80891cdef8b
ms.openlocfilehash: a97ff5afef23c361b1f675d2f07f43b3bc5df299
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94818386"
---
# <a name="xpath-queries-and-namespaces"></a>Requêtes et espaces de noms XPath
Les requêtes XPath reconnaissent les espaces de noms d’un document XML et peuvent utiliser les préfixes d’espace de noms pour qualifier des noms d’éléments et d’attributs. Le fait de qualifier des noms d’éléments et d’attributs avec un préfixe d’espace de noms permet de limiter les nœuds retournés par une requête XPath aux nœuds qui appartiennent à un espace de noms spécifique.  
  
 Par exemple, si le préfixe `books` correspond à l’espace de noms `http://www.contoso.com/books`, la requête XPath suivante `/books:books/books:book` sélectionne uniquement les éléments `book` se trouvant dans l’espace de noms `http://www.contoso.com/books`.  
  
## <a name="the-xmlnamespacemanager"></a>La classe XmlNamespaceManager  
 Pour qu'il soit possible d'utiliser des espaces de noms dans une requête XPath, un objet dérivé de l'interface <xref:System.Xml.IXmlNamespaceResolver> comme la classe <xref:System.Xml.XmlNamespaceManager> est construit avec l'URI d'espace de noms et le préfixe à utiliser dans la requête XPath.  
  
 L'objet <xref:System.Xml.XmlNamespaceManager> peut être utilisé dans la requête de chacune des manières suivantes.  
  
- L'objet <xref:System.Xml.XmlNamespaceManager> est associé à un objet <xref:System.Xml.XPath.XPathExpression> existant en utilisant la méthode <xref:System.Xml.XPath.XPathExpression.SetContext%2A> de l'objet <xref:System.Xml.XPath.XPathExpression>. Vous pouvez aussi compiler un nouvel objet <xref:System.Xml.XPath.XPathExpression> à l'aide de la méthode <xref:System.Xml.XPath.XPathExpression.Compile%2A> statique, qui prend comme paramètres une chaîne représentant l'expression XPath ainsi qu'un objet <xref:System.Xml.XmlNamespaceManager> et retourne un nouvel objet <xref:System.Xml.XPath.XPathExpression>.  
  
- L’objet <xref:System.Xml.XmlNamespaceManager> lui-même est passé en paramètre à une méthode réceptrice de la classe <xref:System.Xml.XPath.XPathNavigator> en même temps qu’une chaîne représentant l’expression XPath.  
  
 Voici les méthodes de la classe <xref:System.Xml.XPath.XPathNavigator> qui acceptent comme paramètre un objet dérivé de l'interface <xref:System.Xml.IXmlNamespaceResolver>.  
  
- <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
### <a name="the-default-namespace"></a>L'espace de noms par défaut  
 Dans le document XML suivant, l'espace de noms par défaut, avec un préfixe vide, est utilisé pour déclarer l'espace de noms `http://www.contoso.com/books`.  
  
```xml  
<books xmlns="http://www.contoso.com/books">  
    <book>  
        <title>Title</title>  
        <author>Author Name</author>  
        <price>5.50</price>  
    </book>  
</books>  
```  
  
 XPath traite le préfixe vide comme l’espace de noms `null`. Autrement dit, seuls les préfixes mappés à des espaces de noms peuvent être utilisés dans des requêtes XPath. Cela signifie que si vous voulez appliquer une requête à un espace de noms d'un document XML, vous devez définir un préfixe pour cet espace de noms, même si c'est l'espace de noms par défaut.  
  
 Par exemple, si aucun préfixe n’est défini pour le document XML ci-dessus, la requête XPath `/books/book` ne retournera aucun résultat.  
  
 Un préfixe doit être lié afin d'éviter toute ambiguïté lors de l'interrogation de documents où certains nœuds ne sont pas dans un espace de noms et certains se trouvent dans un espace de noms par défaut.  
  
 Le code suivant définit un préfixe pour l'espace de noms par défaut et sélectionne tous les éléments `book` de l'espace de noms `http://www.contoso.com/books`.  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
Dim query As XPathExpression = navigator.Compile("/books:books/books:book")  
Dim manager As XmlNamespaceManager = New XmlNamespaceManager(navigator.NameTable)  
manager.AddNamespace("books", "http://www.contoso.com/books")  
query.SetContext(manager)  
Dim nodes As XPathNodeIterator = navigator.Select(query)  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
XPathExpression query = navigator.Compile("/books:books/books:book");  
XmlNamespaceManager manager = new XmlNamespaceManager(navigator.NameTable);  
manager.AddNamespace("books", "http://www.contoso.com/books");  
query.SetContext(manager);  
XPathNodeIterator nodes = navigator.Select(query);  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [Traitement des données XML à l'aide du modèle de données XPath](process-xml-data-using-the-xpath-data-model.md)
- [Sélection de données XML à l'aide de XPathNavigator](select-xml-data-using-xpathnavigator.md)
- [Évaluation d’expressions XPath à l’aide de XPathNavigator](evaluate-xpath-expressions-using-xpathnavigator.md)
- [Mise en correspondance de nœuds avec XPathNavigator](matching-nodes-using-xpathnavigator.md)
- [Types de nœuds reconnus avec les requêtes XPath](node-types-recognized-with-xpath-queries.md)
- [Expressions XPath compilées](compiled-xpath-expressions.md)
