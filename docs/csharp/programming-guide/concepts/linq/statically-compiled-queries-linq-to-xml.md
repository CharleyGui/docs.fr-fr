---
title: Requêtes compilées statiquement (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: 3bf558fe-0705-479d-86d4-00188f5fcf9c
ms.openlocfilehash: ee5d5fbc9bf2aa90635e75c5c8cbf52b16e3f349
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66483464"
---
# <a name="statically-compiled-queries-linq-to-xml-c"></a>Requêtes compilées statiquement (LINQ to XML) (C#)
L'un des principaux avantages de LINQ to XML en terme de performance, par rapport à <xref:System.Xml.XmlDocument>, est que les requêtes dans LINQ to XML sont compilées statiquement, tandis que les requêtes XPath doivent être interprétées lors de l'exécution. Cette fonctionnalité étant intégrée dans LINQ to XML, vous n'avez pas à effectuer d'étapes supplémentaires pour en bénéficier, mais il est utile de comprendre cette distinction pour pouvoir choisir entre ces deux technologies. Cette rubrique explique en quoi consiste la différence.  
  
## <a name="statically-compiled-queries-vs-xpath"></a>Requêtes compilées statiquement et XPath  
 L'exemple suivant montre comment obtenir les éléments descendants avec un nom spécifié et avec un attribut avec une valeur spécifiée.  
  
 L'expression XPath équivalente est indiquée ci-dessous :  
  
```  
//Address[@Type='Shipping']  
```  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
IEnumerable<XElement> list1 =  
    from el in po.Descendants("Address")  
    where (string)el.Attribute("Type") == "Shipping"  
    select el;  
  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 L'expression de requête contenue dans cet exemple est réécrite par le compilateur en syntaxe de requête fondée sur une méthode. L'exemple suivant, qui est écrit dans la syntaxe de requête fondée sur une méthode, produit les mêmes résultats que l'exemple précédent :  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
IEnumerable<XElement> list1 =  
    po  
    .Descendants("Address")  
    .Where(el => (string)el.Attribute("Type") == "Shipping");  
  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 La méthode <xref:System.Linq.Enumerable.Where%2A> est une méthode d'extension. Pour plus d’informations, consultez la page [Méthodes d’extension](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md). <xref:System.Linq.Enumerable.Where%2A> étant une méthode d'extension, la requête ci-dessus est compilée comme si elle était écrite comme suit :  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
IEnumerable<XElement> list1 =  
    System.Linq.Enumerable.Where(  
        po.Descendants("Address"),  
        el => (string)el.Attribute("Type") == "Shipping");  
  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 Cet exemple produit exactement les mêmes résultats que les deux exemples précédents. Ceci illustre le fait que les requêtes sont effectivement compilées en appels de méthodes liés statiquement. Ceci, combiné à la sémantique d'exécution différée des itérateurs, améliore la performance. Pour plus d’informations sur la sémantique d’exécution différée des itérateurs, consultez [Exécution et évaluation différées dans LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).  
  
> [!NOTE]
>  Ces exemples sont représentatifs du code susceptible d'être écrit par le compilateur. L'implémentation réelle peut différer légèrement de ces exemples, mais la performance sera identique ou similaire à celle de ces exemples.  
  
## <a name="executing-xpath-expressions-with-xmldocument"></a>Exécution d'expressions XPath avec XmlDocument  
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
  
 Cette requête retourne le même résultat que les exemples qui utilisent LINQ to XML ; la seule différence est que LINQ to XML met en retrait le XML imprimé, tandis que ce n'est pas le cas pour <xref:System.Xml.XmlDocument>.  
  
 Toutefois, l'approche <xref:System.Xml.XmlDocument> fournit généralement une performance inférieure à LINQ to XML, car la méthode <xref:System.Xml.XmlNode.SelectNodes%2A> doit effectuer les opérations suivantes au niveau interne chaque fois qu'elle est appelée :  
  
- Elle analyse la chaîne qui contient l'expression XPath, en scindant la chaîne en jetons.  
  
- Elle valide les jetons pour s'assurer que l'expression XPath est valide.  
  
- Elle traduit l'expression en arborescence d'expression interne.  
  
- Elle effectue l'itération sur les nœuds, en sélectionnant de façon appropriée les nœuds pour le jeu de résultats basé sur l'évaluation de l'expression.  
  
 Ces opérations représentent un travail considérablement plus important que celui effectué par la requête LINQ to XML correspondant. La différence de performance spécifique varie selon les différents types de requête, mais en général les requêtes LINQ to XML effectuent moins de tâches et fournissent donc une meilleure performance que l'évaluation des expressions XPath à l'aide de <xref:System.Xml.XmlDocument>.  
  