---
title: Comparaison de l'interrogation d'un XDocument et d'un Interrogation d’un XElement
ms.date: 07/20/2015
ms.assetid: 2d111f84-0ded-4cde-8d93-5440557a726d
ms.openlocfilehash: 3cd79c8f2cde101de43a9b9e983709e2e0d11814
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396296"
---
# <a name="querying-an-xdocument-vs-querying-an-xelement-visual-basic"></a>Interrogation d’un XDocument et interrogation d’un XElement (Visual Basic)
Lorsque vous chargez un document par le biais de <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>, vous remarquerez que vous devez écrire des requêtes de manière légèrement différente comparé au chargement par le biais de <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>.  
  
## <a name="comparison-of-xdocumentload-and-xelementload"></a>Comparaison de XDocument.Load et XElement.Load  
 Lorsque vous chargez un document XML dans <xref:System.Xml.Linq.XElement> par le biais de <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, l'objet <xref:System.Xml.Linq.XElement> à la racine de l'arborescence XML contient l'élément racine du document chargé. Toutefois, lorsque vous chargez le même document XML dans un objet <xref:System.Xml.Linq.XDocument> par le biais de <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>, la racine de l'arborescence est un nœud <xref:System.Xml.Linq.XDocument> et l'élément racine du document chargé est le nœud <xref:System.Xml.Linq.XElement> enfant autorisé de l'objet <xref:System.Xml.Linq.XDocument>. Les axes [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] opèrent relativement au nœud racine.  
  
 Ce premier exemple charge une arborescence XML à l'aide de <xref:System.Xml.Linq.XElement.Load%2A>. Il interroge ensuite les éléments enfants de la racine de l'arborescence.  
  
```vb  
' Create a simple document and  write it to a file  
File.WriteAllText("Test.xml", "<Root>" + Environment.NewLine + _  
    "    <Child1>1</Child1>" + Environment.NewLine + _  
    "    <Child2>2</Child2>" + Environment.NewLine + _  
    "    <Child3>3</Child3>" + Environment.NewLine + _  
    "</Root>")  
  
Console.WriteLine("Querying tree loaded with XElement.Load")  
Console.WriteLine("----")  
Dim doc As XElement = XElement.Load("Test.xml")  
Dim childList As IEnumerable(Of XElement) = _  
        From el In doc.Elements() _  
        Select el  
For Each e As XElement In childList  
    Console.WriteLine(e)  
Next  
```  
  
 Comme prévu, cet exemple produit la sortie suivante :  
  
```console
Querying tree loaded with XElement.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  
 L'exemple suivant est identique au précédent, hormis le fait que l'arborescence XML est chargée dans un objet <xref:System.Xml.Linq.XDocument> au lieu d'un objet <xref:System.Xml.Linq.XElement>.  
  
```vb  
' Create a simple document and  write it to a file  
File.WriteAllText("Test.xml", "<Root>" + Environment.NewLine + _  
    "    <Child1>1</Child1>" + Environment.NewLine + _  
    "    <Child2>2</Child2>" + Environment.NewLine + _  
    "    <Child3>3</Child3>" + Environment.NewLine + _  
    "</Root>")  
  
Console.WriteLine("Querying tree loaded with XDocument.Load")  
Console.WriteLine("----")  
Dim doc As XDocument = XDocument.Load("Test.xml")  
Dim childList As IEnumerable(Of XElement) = _  
        From el In doc.Elements() _  
        Select el  
For Each e As XElement In childList  
    Console.WriteLine(e)  
Next  
```  
  
 Cet exemple produit la sortie suivante :  
  
```console
Querying tree loaded with XDocument.Load  
----  
<Root>  
  <Child1>1</Child1>  
  <Child2>2</Child2>  
  <Child3>3</Child3>  
</Root>  
```  
  
 Notez que la même requête a retourné le nœud `Root` au lieu des trois nœuds enfants.  
  
 L'une des solutions à ce problème consiste à utiliser la propriété <xref:System.Xml.Linq.XDocument.Root%2A> avant d'accéder aux méthodes d'axe, comme suit :  
  
```vb  
' Create a simple document and  write it to a file  
File.WriteAllText("Test.xml", "<Root>" + Environment.NewLine + _  
    "    <Child1>1</Child1>" + Environment.NewLine + _  
    "    <Child2>2</Child2>" + Environment.NewLine + _  
    "    <Child3>3</Child3>" + Environment.NewLine + _  
    "</Root>")  
  
Console.WriteLine("Querying tree loaded with XDocument.Load")  
Console.WriteLine("----")  
Dim doc As XDocument = XDocument.Load("Test.xml")  
Dim childList As IEnumerable(Of XElement) = _  
        From el In doc.Root.Elements() _  
        Select el  
For Each e As XElement In childList  
    Console.WriteLine(e)  
Next  
```  
  
 Cette requête s'exécute maintenant de la même manière que la requête sur l'arborescence enracinée dans <xref:System.Xml.Linq.XElement>. L'exemple produit la sortie suivante :  
  
```console
Querying tree loaded with XDocument.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Requêtes de base (LINQ to XML) (Visual Basic)](basic-queries-linq-to-xml.md)
