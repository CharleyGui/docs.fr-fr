---
title: 'Procédure : rechercher un seul descendant à l’aide de la méthode Descendants (C#)'
ms.date: 07/20/2015
ms.assetid: 6f735be9-0293-4680-8007-ca9d96bfebed
ms.openlocfilehash: 726c89b8fdd3df774de2d7ac9a824f2b3769d404
ms.sourcegitcommit: eb9ff6f364cde6f11322e03800d8f5ce302f3c73
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68709967"
---
# <a name="how-to-find-a-single-descendant-using-the-descendants-method-c"></a>Procédure : rechercher un seul descendant à l’aide de la méthode Descendants (C#)
Vous pouvez utiliser la méthode d'axe <xref:System.Xml.Linq.XContainer.Descendants%2A> pour écrire rapidement du code afin de rechercher un seul élément nommé de manière unique. Cette technique est particulièrement utile lorsque vous souhaitez rechercher un descendant particulier avec un nom spécifique. Vous pourriez écrire du code pour naviguer jusqu'à l'élément souhaité, mais il est souvent plus rapide et plus facile d'écrire le code à l'aide de l'axe <xref:System.Xml.Linq.XContainer.Descendants%2A>.  
  
## <a name="example"></a>Exemples  
 Cet exemple utilise l'opérateur de requête standard <xref:System.Linq.Enumerable.First%2A>.  
  
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
  
 Ce code génère la sortie suivante :  
  
```  
GC3 Value  
```  
  
## <a name="example"></a>Exemples  
 L'exemple suivant illustre la même requête pour du code XML qui est dans un espace de noms. Pour plus d’informations, consultez [Vue d’ensemble des espaces de noms (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).  
  
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
  
 Ce code génère la sortie suivante :  
  
```  
GC3 Value  
```  
