---
title: 'Comment : interroger LINQ to XML à l’aide de XPath'
ms.date: 07/20/2015
ms.assetid: e1f69a20-1efa-452d-9089-c472fa84b3d5
ms.openlocfilehash: 563756c019ddd458d46f47c843e32ddc7bbaacd1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347655"
---
# <a name="how-to-query-linq-to-xml-using-xpath-visual-basic"></a>How to: Query LINQ to XML Using XPath (Visual Basic)
Cette rubrique présente les méthodes d’extension qui vous permettent d’interroger une arborescence XML à l’aide de XPath. Pour plus d'informations sur l'utilisation de ces méthodes d'extension, consultez <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.  
  
 À moins que vous n’ayez une raison spécifique pour interroger à l’aide de XPath, par exemple en cas d’utilisation intensive de code hérité, l’utilisation de XPath avec LINQ to XML n’est pas recommandée. Les requêtes XPath présentent des performances inférieures à celles des requêtes [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].  
  
## <a name="example"></a>Exemple  
 L'exemple suivant crée une petite arborescence XML et utilise <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> pour sélectionner un ensemble d'éléments.  
  
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
  
 Cet exemple génère la sortie suivante :  
  
```xml  
<Child2>4</Child2>  
<Child2>5</Child2>  
<Child2>6</Child2>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Advanced Query Techniques (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
