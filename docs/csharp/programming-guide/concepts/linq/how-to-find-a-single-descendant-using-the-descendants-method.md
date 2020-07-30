---
title: Guide pratique pour rechercher un seul descendant à l’aide de la méthode descendants (C#)
description: Découvrez comment rechercher un seul descendant à l’aide de la méthode d’axe descendants. Cette méthode est utile pour trouver un descendant particulier avec un nom spécifique.
ms.date: 07/20/2015
ms.assetid: 6f735be9-0293-4680-8007-ca9d96bfebed
ms.openlocfilehash: 993e2b45f93509cf526d0c8c5de488b50de3efef
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303333"
---
# <a name="how-to-find-a-single-descendant-using-the-descendants-method-c"></a><span data-ttu-id="1f299-104">Guide pratique pour rechercher un seul descendant à l’aide de la méthode descendants (C#)</span><span class="sxs-lookup"><span data-stu-id="1f299-104">How to find a single descendant using the descendants method (C#)</span></span>
<span data-ttu-id="1f299-105">Vous pouvez utiliser la méthode d'axe <xref:System.Xml.Linq.XContainer.Descendants%2A> pour écrire rapidement du code afin de rechercher un seul élément nommé de manière unique.</span><span class="sxs-lookup"><span data-stu-id="1f299-105">You can use the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis method to quickly write code to find a single uniquely named element.</span></span> <span data-ttu-id="1f299-106">Cette technique est particulièrement utile lorsque vous souhaitez rechercher un descendant particulier avec un nom spécifique.</span><span class="sxs-lookup"><span data-stu-id="1f299-106">This technique is especially useful when you want to find a particular descendant with a specific name.</span></span> <span data-ttu-id="1f299-107">Vous pourriez écrire du code pour naviguer jusqu'à l'élément souhaité, mais il est souvent plus rapide et plus facile d'écrire le code à l'aide de l'axe <xref:System.Xml.Linq.XContainer.Descendants%2A>.</span><span class="sxs-lookup"><span data-stu-id="1f299-107">You could write the code to navigate to the desired element, but it is often faster and easier to write the code using the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1f299-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="1f299-108">Example</span></span>  
 <span data-ttu-id="1f299-109">Cet exemple utilise l'opérateur de requête standard <xref:System.Linq.Enumerable.First%2A>.</span><span class="sxs-lookup"><span data-stu-id="1f299-109">This example uses the <xref:System.Linq.Enumerable.First%2A> standard query operator.</span></span>  
  
```csharp  
XElement root = XElement.Parse(@"<Root>  
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
</Root>");  
string grandChild3 = (string)  
    (from el in root.Descendants("GrandChild3")  
    select el).First();  
Console.WriteLine(grandChild3);  
```  
  
 <span data-ttu-id="1f299-110">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="1f299-110">This code produces the following output:</span></span>  
  
```output  
GC3 Value  
```  
  
## <a name="example"></a><span data-ttu-id="1f299-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="1f299-111">Example</span></span>  
 <span data-ttu-id="1f299-112">L'exemple suivant illustre la même requête pour du code XML qui est dans un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="1f299-112">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="1f299-113">Pour plus d’informations, consultez [Vue d’ensemble des espaces de noms (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="1f299-113">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
```csharp  
XElement root = XElement.Parse(@"<aw:Root xmlns:aw='http://www.adventure-works.com'>  
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
</aw:Root>");  
XNamespace aw = "http://www.adventure-works.com";  
string grandChild3 = (string)  
    (from el in root.Descendants(aw + "GrandChild3")  
     select el).First();  
Console.WriteLine(grandChild3);  
```  
  
 <span data-ttu-id="1f299-114">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="1f299-114">This code produces the following output:</span></span>  
  
```output  
GC3 Value  
```  
