---
title: "Comment : filtrer sur des noms d'éléments (LINQ to XML)"
ms.date: 07/20/2015
ms.assetid: b1437b4a-48aa-4546-834a-d6d3ab015fe1
ms.openlocfilehash: 0c443ffa17f7bd4f7537068b97165cda97a37ced
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353019"
---
# <a name="how-to-filter-on-element-names-linq-to-xml-visual-basic"></a>Comment : filtrer sur des noms d’éléments (LINQ to XML) (Visual Basic)
Lorsque vous appelez l'une des méthodes qui retournent <xref:System.Collections.Generic.IEnumerable%601> de collections <xref:System.Xml.Linq.XElement>, vous pouvez filtrer sur le nom de l'élément.  
  
## <a name="example"></a>Exemple  
 Cet exemple récupère une collection des descendants filtrée de sorte à contenir uniquement les descendants avec le nom spécifié.  
  
 Cet exemple utilise le document XML suivant : [Exemple de fichier XML : commande fournisseur typique (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).  
  
```vb  
Dim po As XElement = XElement.Load("PurchaseOrder.xml")  
Dim items As IEnumerable(Of XElement) = _  
    From el In po...<ProductName> _  
    Select el  
For Each prdName As XElement In items  
    Console.WriteLine(prdName.Name.ToString & ":" & prdName.Value)  
Next  
```  
  
 Ce code génère la sortie suivante :  
  
```console  
ProductName:Lawnmower  
ProductName:Baby Monitor  
```  
  
 Les autres méthodes qui retournent <xref:System.Collections.Generic.IEnumerable%601> de collections <xref:System.Xml.Linq.XElement> suivent le même modèle. Leurs signatures sont semblables à <xref:System.Xml.Linq.XContainer.Elements%2A> et <xref:System.Xml.Linq.XContainer.Descendants%2A>. Voici la liste complète des méthodes qui ont des signatures de méthodes semblables :  
  
- <xref:System.Xml.Linq.XNode.Ancestors%2A>  
  
- <xref:System.Xml.Linq.XContainer.Descendants%2A>  
  
- <xref:System.Xml.Linq.XContainer.Elements%2A>  
  
- <xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A>  
  
- <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>  
  
- <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A>  
  
- <xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A>  
  
## <a name="example"></a>Exemple  
 L'exemple suivant illustre la même requête pour du code XML qui est dans un espace de noms. Pour plus d’informations, consultez [vue d’ensemble des espaces de noms (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).  
  
 Cet exemple utilise le document XML suivant : [Exemple de fichier XML : commande fournisseur typique dans un espace de noms](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md).  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim po As XElement = XElement.Load("PurchaseOrderInNamespace.xml")  
        Dim items As IEnumerable(Of XElement) = _  
            From el In po...<aw:ProductName> _  
            Select el  
        For Each prdName As XElement In items  
            Console.WriteLine(prdName.Name.ToString & ":" & prdName.Value)  
        Next  
    End Sub  
End Module  
```  
  
 Ce code génère la sortie suivante :  
  
```console  
{http://www.adventure-works.com}ProductName:Lawnmower  
{http://www.adventure-works.com}ProductName:Baby Monitor  
```  
  
## <a name="see-also"></a>Voir aussi

- [Axes LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
