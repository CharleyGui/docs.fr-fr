---
title: Guide pratique pour rechercher le frère précédent (XPath-LINQ to XML) (C#)
description: Cet exemple C# compare XPath à LINQ to XML pour savoir comment rechercher le frère qui précède immédiatement un nœud.
ms.date: 07/20/2015
ms.assetid: 74c06201-0b1b-4b5e-b3ac-0092980614e6
ms.openlocfilehash: eaee7f1205ce0d0b2a9c2c41d96ba532573a1384
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105202"
---
# <a name="how-to-find-the-immediate-preceding-sibling-xpath-linq-to-xml-c"></a><span data-ttu-id="96230-103">Guide pratique pour rechercher le frère précédent (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="96230-103">How to find the immediate preceding sibling (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="96230-104">Il peut arriver que vous souhaitiez rechercher le frère précédent d'un nœud.</span><span class="sxs-lookup"><span data-stu-id="96230-104">Sometimes you want to find the immediate preceding sibling to a node.</span></span> <span data-ttu-id="96230-105">Étant donné la différence de sémantique des prédicats de position pour les axes enfants précédents dans XPath par opposition à [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], il s'agit de l'une des comparaisons les plus intéressantes.</span><span class="sxs-lookup"><span data-stu-id="96230-105">Due to the difference in the semantics of positional predicates for the preceding sibling axes in XPath as opposed to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], this is one of the more interesting comparisons.</span></span>  
  
## <a name="example"></a><span data-ttu-id="96230-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="96230-106">Example</span></span>  
 <span data-ttu-id="96230-107">Dans cet exemple, la requête [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] utilise l'opérateur <xref:System.Linq.Enumerable.Last%2A> pour rechercher le dernier nœud dans la collection retournée par <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>.</span><span class="sxs-lookup"><span data-stu-id="96230-107">In this example, the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query uses the <xref:System.Linq.Enumerable.Last%2A> operator to find the last node in the collection returned by <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>.</span></span> <span data-ttu-id="96230-108">Par contraste, l’expression XPath utilise un prédicat avec une valeur de 1 pour rechercher l’élément précédent.</span><span class="sxs-lookup"><span data-stu-id="96230-108">By contrast, the XPath expression uses a predicate with a value of 1 to find the immediately preceding element.</span></span>  
  
```csharp  
XElement root = XElement.Parse(  
    @"<Root>  
    <Child1/>  
    <Child2/>  
    <Child3/>  
    <Child4/>  
</Root>");  
XElement child4 = root.Element("Child4");  
  
// LINQ to XML query  
XElement el1 =  
    child4  
    .ElementsBeforeSelf()  
    .Last();  
  
// XPath expression  
XElement el2 =  
    ((IEnumerable)child4  
                 .XPathEvaluate("preceding-sibling::*[1]"))  
                 .Cast<XElement>()  
                 .First();  
  
if (el1 == el2)  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
Console.WriteLine(el1);  
```  
  
 <span data-ttu-id="96230-109">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="96230-109">This example produces the following output:</span></span>  
  
```output  
Results are identical  
<Child3 />  
```  
