---
title: 'Procédure : Écrire des requêtes avec un filtrage complexe (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: bf286ffc-7990-4b00-a4eb-ee3d70129950
ms.openlocfilehash: 0459c9549238257c0a76276a1d10f6d370144214
ms.sourcegitcommit: eb9ff6f364cde6f11322e03800d8f5ce302f3c73
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68709866"
---
# <a name="how-to-write-queries-with-complex-filtering-visual-basic"></a>Procédure : Écrire des requêtes avec un filtrage complexe (Visual Basic)
Il peut arriver que vous souhaitiez écrire des requêtes LINQ to XML à l'aide de filtres complexes. Par exemple, il se peut que vous deviez rechercher tous les éléments qui ont un élément enfant avec un nom et une valeur spécifiques. Cette rubrique fournit un exemple d'écriture de requête avec un filtrage complexe.  
  
## <a name="example"></a>Exemple  
 Cet exemple montre comment rechercher tous les éléments `PurchaseOrder` qui ont un élément `Address` enfant ayant un attribut `Type` égal à « Shipping » et un élément `State` enfant égal à « NY ». Il utilise une sous-requête dans la clause `Where` et l'opérateur `Any` retourne `True` si la collection possède des éléments.  
  
 Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Plusieurs commandes fournisseur (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).  
  
 Pour plus d’informations sur `Any` l’opérateur, consultez [opérations de quantificateur (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md).  
  
```vb  
Dim root As XElement = XElement.Load("PurchaseOrders.xml")  
Dim purchaseOrders As IEnumerable(Of XElement) = _  
    From el In root.<PurchaseOrder> _  
    Where _  
        (From add In el.<Address> _  
        Where _  
             add.@Type = "Shipping" And _  
             add.<State>.Value = "NY" _  
        Select add) _  
    .Any() _  
    Select el  
For Each el As XElement In purchaseOrders  
    Console.WriteLine(el.@PurchaseOrderNumber)  
Next  
```  
  
 Ce code génère la sortie suivante :  
  
```  
99505  
```  
  
## <a name="example"></a>Exemple  
 L'exemple suivant illustre la même requête pour du code XML qui est dans un espace de noms. Pour plus d’informations, consultez [vue d’ensemble des espaces de noms (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).  
  
 Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Plusieurs commandes fournisseur dans un espace de noms](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md).  
  
```vb  
Imports <xmlns:aw='http://www.adventure-works.com'>  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = XElement.Load("PurchaseOrdersInNamespace.xml")  
        Dim purchaseOrders As IEnumerable(Of XElement) = _  
            From el In root.<aw:PurchaseOrder> _  
            Where _  
                (From add In el.<aw:Address> _  
                Where _  
                     add.@aw:Type = "Shipping" And _  
                     add.<aw:State>.Value = "NY" _  
                Select add) _  
            .Any() _  
            Select el  
        For Each el As XElement In purchaseOrders  
            Console.WriteLine(el.@aw:PurchaseOrderNumber)  
        Next  
    End Sub  
End Module  
```  
  
 Ce code génère la sortie suivante :  
  
```  
99505  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [Requêtes de base (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
- [Propriété d’axe enfant XML](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)
- [Propriété d’axe d’attribut XML](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)
- [Propriété de valeur XML](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
- [Opérations de projection (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/projection-operations.md)
- [Opérations de quantificateur (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md)
