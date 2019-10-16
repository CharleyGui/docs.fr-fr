---
title: 'Comment : Rechercher le frère précédent (XPath-LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: ec046283-9fe2-4440-b295-860bf700099d
ms.openlocfilehash: bc54239d2ddaafcc46413ed13c274449daaba0c7
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320601"
---
# <a name="how-to-find-the-immediate-preceding-sibling-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="ac49d-102">Comment : Rechercher le frère précédent (XPath-LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ac49d-102">How to: Find the Immediate Preceding Sibling (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="ac49d-103">Il peut arriver que vous souhaitiez rechercher le frère précédent d'un nœud.</span><span class="sxs-lookup"><span data-stu-id="ac49d-103">Sometimes you want to find the immediate preceding sibling to a node.</span></span> <span data-ttu-id="ac49d-104">Étant donné la différence de sémantique des prédicats de position pour les axes enfants précédents dans XPath par opposition à [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], il s'agit de l'une des comparaisons les plus intéressantes.</span><span class="sxs-lookup"><span data-stu-id="ac49d-104">Due to the difference in the semantics of positional predicates for the preceding sibling axes in XPath as opposed to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], this is one of the more interesting comparisons.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ac49d-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="ac49d-105">Example</span></span>  
 <span data-ttu-id="ac49d-106">Dans cet exemple, la requête [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] utilise l'opérateur <xref:System.Linq.Enumerable.Last%2A> pour rechercher le dernier nœud dans la collection retournée par <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>.</span><span class="sxs-lookup"><span data-stu-id="ac49d-106">In this example, the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query uses the <xref:System.Linq.Enumerable.Last%2A> operator to find the last node in the collection returned by <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>.</span></span> <span data-ttu-id="ac49d-107">Par contraste, l'expression XPath utilise un prédicat avec une valeur de 1 pour rechercher l'élément précédent.</span><span class="sxs-lookup"><span data-stu-id="ac49d-107">By contrast, the XPath expression uses a predicate with a value of 1 to find the immediately preceding element.</span></span>  
  
```vb  
Dim root As XElement = _   
    <Root>  
        <Child1/>  
        <Child2/>  
        <Child3/>  
        <Child4/>  
    </Root>  
Dim child4 As XElement = root.Element("Child4")  
  
' LINQ to XML query  
Dim el1 As XElement = child4.ElementsBeforeSelf().Last()  
  
' XPath expression  
Dim el2 As XElement = _  
    DirectCast(child4.XPathEvaluate("preceding-sibling::*[1]"),  _  
    IEnumerable).Cast(Of XElement)().First()  
  
If el1 Is el2 Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
Console.WriteLine(el1)  
```  
  
 <span data-ttu-id="ac49d-108">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="ac49d-108">This example produces the following output:</span></span>  
  
```console
Results are identical  
<Child3 />  
```  
  
## <a name="see-also"></a><span data-ttu-id="ac49d-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ac49d-109">See also</span></span>

- [<span data-ttu-id="ac49d-110">LINQ to XML pour les utilisateurs XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ac49d-110">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
