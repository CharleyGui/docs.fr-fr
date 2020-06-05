---
title: 'Procédure : interroger LINQ to XML à l’aide de XPath'
ms.date: 07/20/2015
ms.assetid: e1f69a20-1efa-452d-9089-c472fa84b3d5
ms.openlocfilehash: d95e5a82d146c357f52d03375119474b042d49f6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397919"
---
# <a name="how-to-query-linq-to-xml-using-xpath-visual-basic"></a><span data-ttu-id="16f8f-102">Procédure : interrogation de LINQ to XML à l’aide de XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="16f8f-102">How to: Query LINQ to XML Using XPath (Visual Basic)</span></span>
<span data-ttu-id="16f8f-103">Cette rubrique présente les méthodes d’extension qui vous permettent d’interroger une arborescence XML à l’aide de XPath.</span><span class="sxs-lookup"><span data-stu-id="16f8f-103">This topic introduces the extension methods that enable you to query an XML tree by using XPath.</span></span> <span data-ttu-id="16f8f-104">Pour plus d'informations sur l'utilisation de ces méthodes d'extension, consultez <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="16f8f-104">For detailed information about using these extension methods, see <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="16f8f-105">À moins que vous n’ayez une raison spécifique pour interroger à l’aide de XPath, par exemple en cas d’utilisation intensive de code hérité, l’utilisation de XPath avec LINQ to XML n’est pas recommandée.</span><span class="sxs-lookup"><span data-stu-id="16f8f-105">Unless you have a very specific reason for querying using XPath, such as extensive use of legacy code, using XPath with LINQ to XML is not recommended.</span></span> <span data-ttu-id="16f8f-106">Les requêtes XPath présentent des performances inférieures à celles des requêtes [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="16f8f-106">XPath queries will not perform as well as [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="16f8f-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="16f8f-107">Example</span></span>  
 <span data-ttu-id="16f8f-108">L'exemple suivant crée une petite arborescence XML et utilise <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> pour sélectionner un ensemble d'éléments.</span><span class="sxs-lookup"><span data-stu-id="16f8f-108">The following example creates a small XML tree and uses <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> to select a set of elements.</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root>  
        <Child1>1</Child1>  
        <Child1>2</Child1>  
        <Child1>3</Child1>  
        <Child2>4</Child2>  
        <Child2>5</Child2>  
        <Child2>6</Child2>  
    </Root>  
  
Dim list As IEnumerable(Of XElement) = root.XPathSelectElements("./Child2")  
For Each el As XElement In list  
    Console.WriteLine(el)  
Next  
```  
  
 <span data-ttu-id="16f8f-109">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="16f8f-109">This example produces the following output:</span></span>  
  
```xml  
<Child2>4</Child2>  
<Child2>5</Child2>  
<Child2>6</Child2>  
```  
  
## <a name="see-also"></a><span data-ttu-id="16f8f-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="16f8f-110">See also</span></span>

- [<span data-ttu-id="16f8f-111">Techniques de requêtes avancées (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="16f8f-111">Advanced Query Techniques (LINQ to XML) (Visual Basic)</span></span>](advanced-query-techniques-linq-to-xml.md)
