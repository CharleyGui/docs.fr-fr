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
# <a name="how-to-project-a-new-type-linq-to-xml"></a><span data-ttu-id="41552-104">Comment projeter un nouveau type (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="41552-104">How to project a new type (LINQ to XML)</span></span>

<span data-ttu-id="41552-105">Les autres exemples de cette section ont illustré des requêtes qui retournent des résultats comme <xref:System.Collections.Generic.IEnumerable%601> de <xref:System.Xml.Linq.XElement>, <xref:System.Collections.Generic.IEnumerable%601> de `string` et <xref:System.Collections.Generic.IEnumerable%601> de `int`.</span><span class="sxs-lookup"><span data-stu-id="41552-105">Other examples in this section have shown queries that return results as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, <xref:System.Collections.Generic.IEnumerable%601> of `string`, and <xref:System.Collections.Generic.IEnumerable%601> of `int`.</span></span> <span data-ttu-id="41552-106">Il s’agit de types de résultats courants, mais ils ne conviennent pas à chaque scénario.</span><span class="sxs-lookup"><span data-stu-id="41552-106">These are common result types, but they're not appropriate for every scenario.</span></span> <span data-ttu-id="41552-107">Dans de nombreux cas, vous souhaiterez que vos requêtes retournent un <xref:System.Collections.Generic.IEnumerable%601> d’un autre type.</span><span class="sxs-lookup"><span data-stu-id="41552-107">In many cases, you'll want your queries to return an <xref:System.Collections.Generic.IEnumerable%601> of some other type.</span></span>

## <a name="example-define-a-new-type-and-have-the-select-statement-create-an-instance-of-the-type"></a><span data-ttu-id="41552-108">Exemple : définir un nouveau type et faire en sorte que l' `select` instruction crée une instance du type</span><span class="sxs-lookup"><span data-stu-id="41552-108">Example: Define a new type and have the `select` statement create an instance of the type</span></span>

<span data-ttu-id="41552-109">Cet exemple montre comment instancier des objets dans la clause `select`.</span><span class="sxs-lookup"><span data-stu-id="41552-109">This example shows how to instantiate objects in the `select` clause.</span></span> <span data-ttu-id="41552-110">Le code commence par appeler un constructeur pour définir une nouvelle classe, puis modifie l' `select` instruction de sorte que l’expression soit une nouvelle instance de la nouvelle classe.</span><span class="sxs-lookup"><span data-stu-id="41552-110">The code first invokes a constructor to define a new class, and then modifies the `select` statement so that the expression is a new instance of the new class.</span></span> <span data-ttu-id="41552-111">L’exemple utilise un document XML [exemple de fichier XML : commande fournisseur typique](sample-xml-file-typical-purchase-order.md).</span><span class="sxs-lookup"><span data-stu-id="41552-111">The example uses XML document [Sample XML file: Typical purchase order](sample-xml-file-typical-purchase-order.md).</span></span>

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

<span data-ttu-id="41552-112">Cet exemple utilise la <xref:System.Xml.Linq.XContainer.Element%2A> méthode introduite dans l’article [Comment récupérer un seul élément enfant](retrieve-single-child-element.md) .</span><span class="sxs-lookup"><span data-stu-id="41552-112">This example uses the <xref:System.Xml.Linq.XContainer.Element%2A> method that was introduced in the [How to retrieve a single child element](retrieve-single-child-element.md) article.</span></span> <span data-ttu-id="41552-113">Il utilise également des casts pour récupérer les valeurs des éléments retournés par la méthode <xref:System.Xml.Linq.XContainer.Element%2A>.</span><span class="sxs-lookup"><span data-stu-id="41552-113">It also uses casts to retrieve the values of the elements that are returned by the <xref:System.Xml.Linq.XContainer.Element%2A> method.</span></span>

<span data-ttu-id="41552-114">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="41552-114">This example produces the following output:</span></span>

```output
Lawnmower:1
Baby Monitor:2
```

## <a name="see-also"></a><span data-ttu-id="41552-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="41552-115">See also</span></span>

- [<span data-ttu-id="41552-116">Projections et transformations (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="41552-116">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
