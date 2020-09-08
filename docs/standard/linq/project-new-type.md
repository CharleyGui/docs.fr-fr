---
title: Comment projeter un nouveau type-LINQ to XML
description: Votre requête peut retourner un IEnumerable d’un type autre que le type commun. Cet article montre comment procéder dans un exemple.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 48145cf9-1e0b-4e73-bbfd-28fc04800dc4
ms.openlocfilehash: 15eabf37e23363894ec1ab72e6df6dbe1fd974db
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553263"
---
# <a name="how-to-project-a-new-type-linq-to-xml"></a>Comment projeter un nouveau type (LINQ to XML)

Les autres exemples de cette section ont illustré des requêtes qui retournent des résultats comme <xref:System.Collections.Generic.IEnumerable%601> de <xref:System.Xml.Linq.XElement>, <xref:System.Collections.Generic.IEnumerable%601> de `string` et <xref:System.Collections.Generic.IEnumerable%601> de `int`. Il s’agit de types de résultats courants, mais ils ne conviennent pas à chaque scénario. Dans de nombreux cas, vous souhaiterez que vos requêtes retournent un <xref:System.Collections.Generic.IEnumerable%601> d’un autre type.

## <a name="example-define-a-new-type-and-have-the-select-statement-create-an-instance-of-the-type"></a>Exemple : définir un nouveau type et faire en sorte que l' `select` instruction crée une instance du type

Cet exemple montre comment instancier des objets dans la clause `select`. Le code commence par appeler un constructeur pour définir une nouvelle classe, puis modifie l' `select` instruction de sorte que l’expression soit une nouvelle instance de la nouvelle classe. L’exemple utilise un document XML [exemple de fichier XML : commande fournisseur typique](sample-xml-file-typical-purchase-order.md).

```csharp
class NameQty
{
    public string name;
    public int qty;
    public NameQty(string n, int q)
    {
        name = n;
        qty = q;
    }
};

class Program {
    public static void Main()
    {
        XElement po = XElement.Load("PurchaseOrder.xml");

        IEnumerable<NameQty> nqList =
            from n in po.Descendants("Item")
            select new NameQty(
                    (string)n.Element("ProductName"),
                    (int)n.Element("Quantity")
                );

        foreach (NameQty n in nqList)
            Console.WriteLine(n.name + ":" + n.qty);
    }
}
```

```vb
Public Class NameQty
    Public name As String
    Public qty As Integer
    Public Sub New(ByVal n As String, ByVal q As Integer)
        name = n
        qty = q
    End Sub
End Class

Public Class Program
    Shared Sub Main()
        Dim po As XElement = XElement.Load("PurchaseOrder.xml")

        Dim nqList As IEnumerable(Of NameQty) = _
            From n In po...<Item> _
            Select New NameQty( _
                n.<ProductName>.Value, CInt(n.<Quantity>.Value))

        For Each n As NameQty In nqList
            Console.WriteLine(n.name & ":" & n.qty)
        Next
    End Sub
End Class
```

Cet exemple utilise la <xref:System.Xml.Linq.XContainer.Element%2A> méthode introduite dans l’article [Comment récupérer un seul élément enfant](retrieve-single-child-element.md) . Il utilise également des casts pour récupérer les valeurs des éléments retournés par la méthode <xref:System.Xml.Linq.XContainer.Element%2A>.

Cet exemple produit la sortie suivante :

```output
Lawnmower:1
Baby Monitor:2
```

## <a name="see-also"></a>Voir aussi

- [Projections et transformations (LINQ to XML) (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
