---
title: 'Comment : projeter un nouveau type (LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 8cfb24f5-89b2-4cfb-b85d-e7963f8f1845
ms.openlocfilehash: 64b563c57406caae7869905c417db9e6439e6157
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72318371"
---
# <a name="how-to-project-a-new-type-linq-to-xml-visual-basic"></a><span data-ttu-id="2b1c6-102">Comment : projeter un nouveau type (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2b1c6-102">How to: Project a New Type (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="2b1c6-103">Les autres exemples de cette section ont illustré des requêtes qui retournent des résultats comme <xref:System.Collections.Generic.IEnumerable%601> de <xref:System.Xml.Linq.XElement>, <xref:System.Collections.Generic.IEnumerable%601> de `string` et <xref:System.Collections.Generic.IEnumerable%601> de `int`.</span><span class="sxs-lookup"><span data-stu-id="2b1c6-103">Other examples in this section have shown queries that return results as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, <xref:System.Collections.Generic.IEnumerable%601> of `string`, and <xref:System.Collections.Generic.IEnumerable%601> of `int`.</span></span> <span data-ttu-id="2b1c6-104">Il s'agit de types de résultats courants, mais ils ne conviennent pas à chaque scénario.</span><span class="sxs-lookup"><span data-stu-id="2b1c6-104">These are common result types, but they are not appropriate for every scenario.</span></span> <span data-ttu-id="2b1c6-105">Dans de nombreux cas, vous souhaiterez que vos requêtes retournent un objet <xref:System.Collections.Generic.IEnumerable%601> d'un autre type.</span><span class="sxs-lookup"><span data-stu-id="2b1c6-105">In many cases you will want your queries to return an <xref:System.Collections.Generic.IEnumerable%601> of some other type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2b1c6-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="2b1c6-106">Example</span></span>  
 <span data-ttu-id="2b1c6-107">Cet exemple montre comment instancier des objets dans la clause `Select`.</span><span class="sxs-lookup"><span data-stu-id="2b1c6-107">This example shows how to instantiate objects in the `Select` clause.</span></span> <span data-ttu-id="2b1c6-108">Le code définit tout d'abord une nouvelle classe avec un constructeur, puis modifie l'instruction `Select` de sorte que l'expression soit une nouvelle instance de la nouvelle classe.</span><span class="sxs-lookup"><span data-stu-id="2b1c6-108">The code first defines a new class with a constructor, and then modifies the `Select` statement so that the expression is a new instance of the new class.</span></span>  
  
 <span data-ttu-id="2b1c6-109">Cet exemple utilise le document XML suivant : [Exemple de fichier XML : commande fournisseur typique (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="2b1c6-109">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="2b1c6-110">Cet exemple utilise la méthode `M:System.Xml.Linq.XElement.Element` qui a été introduite dans la rubrique [Comment : récupérer un seul élément enfant (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-a-single-child-element-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="2b1c6-110">This example uses the `M:System.Xml.Linq.XElement.Element` method that was introduced in the topic [How to: Retrieve a Single Child Element (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-a-single-child-element-linq-to-xml.md).</span></span> <span data-ttu-id="2b1c6-111">Il utilise également des casts pour récupérer les valeurs des éléments retournés par la méthode `M:System.Xml.Linq.XElement.Element`.</span><span class="sxs-lookup"><span data-stu-id="2b1c6-111">It also uses casts to retrieve the values of the elements that are returned by the `M:System.Xml.Linq.XElement.Element` method.</span></span>  
  
 <span data-ttu-id="2b1c6-112">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="2b1c6-112">This example produces the following output:</span></span>  
  
```console  
Lawnmower:1  
Baby Monitor:2  
```  
  
## <a name="see-also"></a><span data-ttu-id="2b1c6-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2b1c6-113">See also</span></span>

- [<span data-ttu-id="2b1c6-114">Projections et transformations (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2b1c6-114">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
