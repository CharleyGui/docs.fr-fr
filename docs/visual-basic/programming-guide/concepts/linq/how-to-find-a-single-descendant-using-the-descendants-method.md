---
title: 'Procédure : rechercher un seul descendant à l’aide de la méthode Descendants'
ms.date: 07/20/2015
ms.assetid: 0c03468c-efc8-4140-98f3-fb67acd9e8e1
ms.openlocfilehash: d3e193efb7cc050acc0e8113a892d24ad7262b16
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406896"
---
# <a name="how-to-find-a-single-descendant-using-the-descendants-method-visual-basic"></a><span data-ttu-id="0d0a2-102">Comment : Rechercher un seul descendant à l’aide de la méthode descendants (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0d0a2-102">How to: Find a Single Descendant Using the Descendants Method (Visual Basic)</span></span>
<span data-ttu-id="0d0a2-103">Vous pouvez utiliser la méthode d'axe <xref:System.Xml.Linq.XContainer.Descendants%2A> pour écrire rapidement du code afin de rechercher un seul élément nommé de manière unique.</span><span class="sxs-lookup"><span data-stu-id="0d0a2-103">You can use the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis method to quickly write code to find a single uniquely named element.</span></span> <span data-ttu-id="0d0a2-104">Cette technique est particulièrement utile lorsque vous souhaitez rechercher un descendant particulier avec un nom spécifique.</span><span class="sxs-lookup"><span data-stu-id="0d0a2-104">This technique is especially useful when you want to find a particular descendant with a specific name.</span></span> <span data-ttu-id="0d0a2-105">Vous pourriez écrire du code pour naviguer jusqu'à l'élément souhaité, mais il est souvent plus rapide et plus facile d'écrire le code à l'aide de l'axe <xref:System.Xml.Linq.XContainer.Descendants%2A>.</span><span class="sxs-lookup"><span data-stu-id="0d0a2-105">You could write the code to navigate to the desired element, but it is often faster and easier to write the code using the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0d0a2-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="0d0a2-106">Example</span></span>  
 <span data-ttu-id="0d0a2-107">Cet exemple utilise l'opérateur de requête standard <xref:System.Linq.Enumerable.First%2A>.</span><span class="sxs-lookup"><span data-stu-id="0d0a2-107">This example uses the <xref:System.Linq.Enumerable.First%2A> standard query operator.</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root>  
        <Child1>  
            <GrandChild1>GC1 Value</GrandChild1>  
        </Child1>  
        <Child2>  
            <GrandChild2>GC2 Value</GrandChild2>  
        </Child2>  
        <Child3>  
            <GrandChild3>GC3 Value</GrandChild3>  
        </Child3>  
        <Child4>  
            <GrandChild4>GC4 Value</GrandChild4>  
        </Child4>  
    </Root>  
Dim grandChild3 As String = _  
    (From el In root...<GrandChild3> _  
    Select el).First()  
Console.WriteLine(grandChild3)  
```  
  
 <span data-ttu-id="0d0a2-108">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="0d0a2-108">This code produces the following output:</span></span>  
  
```console  
GC3 Value  
```  
  
## <a name="example"></a><span data-ttu-id="0d0a2-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="0d0a2-109">Example</span></span>  
 <span data-ttu-id="0d0a2-110">L'exemple suivant illustre la même requête pour du code XML qui est dans un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="0d0a2-110">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="0d0a2-111">Pour plus d’informations, consultez [vue d’ensemble des espaces de noms (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="0d0a2-111">For more information, see [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span></span>  
  
```vb  
Imports <xmlns:aw='http://www.adventure-works.com'>  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <aw:Root>  
                <aw:Child1>  
                    <aw:GrandChild1>GC1 Value</aw:GrandChild1>  
                </aw:Child1>  
                <aw:Child2>  
                    <aw:GrandChild2>GC2 Value</aw:GrandChild2>  
                </aw:Child2>  
                <aw:Child3>  
                    <aw:GrandChild3>GC3 Value</aw:GrandChild3>  
                </aw:Child3>  
                <aw:Child4>  
                    <aw:GrandChild4>GC4 Value</aw:GrandChild4>  
                </aw:Child4>  
            </aw:Root>  
        Dim grandChild3 As String = _  
            (From el In root...<aw:GrandChild3> _  
            Select el).First()  
        Console.WriteLine(grandChild3)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="0d0a2-112">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="0d0a2-112">This code produces the following output:</span></span>  
  
```console  
GC3 Value  
```  
  
## <a name="see-also"></a><span data-ttu-id="0d0a2-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0d0a2-113">See also</span></span>

- [<span data-ttu-id="0d0a2-114">Requêtes de base (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0d0a2-114">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](basic-queries-linq-to-xml.md)
