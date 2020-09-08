---
title: Requêtes compilées statiquement-LINQ to XML
description: Découvrez comment les requêtes LINQ to XML tirent un avantage en termes de performances par rapport à XMLDocument en étant compilées statiquement.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 3bf558fe-0705-479d-86d4-00188f5fcf9c
ms.openlocfilehash: 53dd47247eae8802dcf8187d0e82eb1c8bead9f9
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553415"
---
# <a name="statically-compiled-queries-linq-to-xml"></a>Requêtes compilées statiquement (LINQ to XML)

L’un des avantages les plus importants en matière de performances de LINQ to XML, par rapport à <xref:System.Xml.XmlDocument> , est que les requêtes dans les LINQ to XML sont compilées statiquement, tandis que les requêtes XPath doivent être interprétées au moment de l’exécution. Cette fonctionnalité étant intégrée à LINQ to XML, il n’est pas nécessaire d’effectuer des étapes supplémentaires pour en tirer parti, mais il est utile de comprendre la distinction lors du choix entre les deux technologies. Cet article explique la différence.

## <a name="statically-compiled-queries-vs-xpath"></a>Requêtes compilées statiquement et XPath

L'exemple suivant montre comment obtenir les éléments descendants avec un nom spécifié et avec un attribut avec une valeur spécifiée. L’expression XPath équivalente est `//Address[@Type='Shipping']` .

```csharp
XDocument po = XDocument.Load("PurchaseOrders.xml");

IEnumerable<XElement> list1 =
    from el in po.Descendants("Address")
    where (string)el.Attribute("Type") == "Shipping"
    select el;

foreach (XElement el in list1)
    Console.WriteLine(el);
```

```vb
Dim po = XDocument.Load("PurchaseOrders.xml")

Dim list1 = From el In po.Descendants("Address")
            Where el.@Type = "Shipping"

For Each el In list1
    Console.WriteLine(el)
Next
```

L’expression de requête dans cet exemple est réécrite par le compilateur en syntaxe de requête fondée sur une méthode. L'exemple suivant, qui est écrit dans la syntaxe de requête fondée sur une méthode, produit les mêmes résultats que l'exemple précédent :

```csharp
XDocument po = XDocument.Load("PurchaseOrders.xml");

IEnumerable<XElement> list1 =
    po
    .Descendants("Address")
    .Where(el => (string)el.Attribute("Type") == "Shipping");

foreach (XElement el in list1)
    Console.WriteLine(el);
```

 ```vb
Dim po = XDocument.Load("PurchaseOrders.xml")

Dim list1 As IEnumerable(Of XElement) = po.Descendants("Address").Where(Function(el) el.@Type = "Shipping")

For Each el In list1
    Console.WriteLine(el)
Next
```

La méthode <xref:System.Linq.Enumerable.Where%2A> est une méthode d'extension. Pour plus d’informations, consultez [méthodes d’extension (Guide de programmation C#)](../../csharp/programming-guide/classes-and-structs/extension-methods.md). <xref:System.Linq.Enumerable.Where%2A> étant une méthode d'extension, la requête ci-dessus est compilée comme si elle était écrite comme suit :

```csharp
XDocument po = XDocument.Load("PurchaseOrders.xml");

IEnumerable<XElement> list1 =
    System.Linq.Enumerable.Where(
        po.Descendants("Address"),
        el => (string)el.Attribute("Type") == "Shipping");

foreach (XElement el in list1)
    Console.WriteLine(el);
```

```vb
Dim po = XDocument.Load("PurchaseOrders.xml")

Dim list1 = Enumerable.Where(po.Descendants("Address"), Function(el) el.@Type = "Shipping")

For Each el In list1
    Console.WriteLine(el)
Next
```

Cet exemple produit exactement les mêmes résultats que les deux exemples précédents. Ceci illustre le fait que les requêtes sont effectivement compilées en appels de méthodes liés statiquement. Ceci, combiné à la sémantique d'exécution différée des itérateurs, améliore la performance. Pour plus d’informations sur la sémantique d’exécution différée des itérateurs, consultez [exécution différée et évaluation](deferred-execution-lazy-evaluation.md)différée.

> [!NOTE]
> Ces exemples sont représentatifs du code susceptible d'être écrit par le compilateur. L’implémentation réelle peut différer légèrement de ces exemples, mais les performances sont les mêmes que, ou similaires à, ces exemples.

## <a name="executing-xpath-expressions-with-xmldocument"></a>Exécution d’expressions XPath avec XmlDocument

L'exemple suivant utilise <xref:System.Xml.XmlDocument> pour produire les mêmes résultats que les exemples précédents :

```csharp
XmlReader reader = XmlReader.Create("PurchaseOrders.xml");
XmlDocument doc = new XmlDocument();
doc.Load(reader);
XmlNodeList nl = doc.SelectNodes(".//Address[@Type='Shipping']");
foreach (XmlNode n in nl)
    Console.WriteLine(n.OuterXml);
reader.Close();
```

```vb
Dim reader = Xml.XmlReader.Create("PurchaseOrders.xml")
Dim doc As New Xml.XmlDocument()
doc.Load(reader)
Dim nl As Xml.XmlNodeList = doc.SelectNodes(".//Address[@Type='Shipping']")
For Each n As Xml.XmlNode In nl
    Console.WriteLine(n.OuterXml)
Next
reader.Close()
```

Cette requête retourne le même résultat que les exemples qui utilisent LINQ to XML ; la seule différence est que LINQ to XML met en retrait le code XML imprimé, contrairement à <xref:System.Xml.XmlDocument> .

Toutefois, l' <xref:System.Xml.XmlDocument> approche ne fonctionne généralement pas aussi bien que LINQ to XML, car la <xref:System.Xml.XmlNode.SelectNodes%2A> méthode doit effectuer les opérations suivantes chaque fois qu’elle est appelée :

- Analyser la chaîne qui contient l’expression XPath, en scindant la chaîne en jetons.
- Validez les jetons pour vous assurer que l’expression XPath est valide.
- Traduisez l’expression en une arborescence d’expression interne.
- Itérez au sein des nœuds, en sélectionnant de manière appropriée les nœuds du jeu de résultats en fonction de l’évaluation de l’expression.

Ces opérations représentent un travail considérablement plus important que celui effectué par la requête LINQ to XML correspondant. La différence de performance spécifique varie selon les différents types de requête, mais en général les requêtes LINQ to XML effectuent moins de tâches et fournissent donc une meilleure performance que l'évaluation des expressions XPath à l'aide de <xref:System.Xml.XmlDocument>.
