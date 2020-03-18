---
title: Comment écrire des requêtes sur XML dans les espaces de nom (C)
ms.date: 07/20/2015
ms.assetid: 7c54df81-15e4-4091-8c81-a87637029130
ms.openlocfilehash: a8b8d55daaad1ae00e43fed897080ed7a62fafab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75337375"
---
# <a name="how-to-write-queries-on-xml-in-namespaces-c"></a><span data-ttu-id="016c6-102">Comment écrire des requêtes sur XML dans les espaces de nom (C)</span><span class="sxs-lookup"><span data-stu-id="016c6-102">How to write queries on XML in namespaces (C#)</span></span>
<span data-ttu-id="016c6-103">Pour écrire des requêtes sur du code XML qui est dans un espace de noms, vous devez utiliser des objets <xref:System.Xml.Linq.XName> qui ont l'espace de noms correct.</span><span class="sxs-lookup"><span data-stu-id="016c6-103">To write a query on XML that is in a namespace, you must use <xref:System.Xml.Linq.XName> objects that have the correct namespace.</span></span>  
  
 <span data-ttu-id="016c6-104">Pour C#, l'approche la plus courante consiste à initialiser un objet <xref:System.Xml.Linq.XNamespace> à l'aide d'une chaîne contenant l'URI, puis à utiliser la surcharge d'opérateur d'addition pour combiner l'espace de noms avec le nom local.</span><span class="sxs-lookup"><span data-stu-id="016c6-104">For C#, the most common approach is to initialize an <xref:System.Xml.Linq.XNamespace> using a string that contains the URI, then use the addition operator overload to combine the namespace with the local name.</span></span>  
  
 <span data-ttu-id="016c6-105">Le premier ensemble d’exemples de cette rubrique montre comment créer une arborescence XML dans un espace de noms par défaut.</span><span class="sxs-lookup"><span data-stu-id="016c6-105">The first set of examples in this topic shows how to create an XML tree in a default namespace.</span></span> <span data-ttu-id="016c6-106">Le second ensemble illustre la création d’une arborescence XML dans un espace de noms avec un préfixe.</span><span class="sxs-lookup"><span data-stu-id="016c6-106">The second set shows how to create an XML tree in a namespace with a prefix.</span></span>  
  
## <a name="example"></a><span data-ttu-id="016c6-107"> Exemple</span><span class="sxs-lookup"><span data-stu-id="016c6-107">Example</span></span>  
 <span data-ttu-id="016c6-108">L’exemple suivant crée une arborescence XML qui est dans un espace de noms par défaut.</span><span class="sxs-lookup"><span data-stu-id="016c6-108">The following example creates an XML tree that is in a default namespace.</span></span> <span data-ttu-id="016c6-109">Il récupère ensuite une collection d'éléments.</span><span class="sxs-lookup"><span data-stu-id="016c6-109">It then retrieves a collection of elements.</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = XElement.Parse(  
@"<Root xmlns='http://www.adventure-works.com'>  
    <Child>1</Child>  
    <Child>2</Child>  
    <Child>3</Child>  
    <AnotherChild>4</AnotherChild>  
    <AnotherChild>5</AnotherChild>  
    <AnotherChild>6</AnotherChild>  
</Root>");  
IEnumerable<XElement> c1 =  
    from el in root.Elements(aw + "Child")  
    select el;  
foreach (XElement el in c1)  
    Console.WriteLine((int)el);  
```  
  
 <span data-ttu-id="016c6-110">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="016c6-110">This example produces the following output:</span></span>  
  
```output  
1  
2  
3  
```  
  
## <a name="example"></a><span data-ttu-id="016c6-111"> Exemple</span><span class="sxs-lookup"><span data-stu-id="016c6-111">Example</span></span>  
 <span data-ttu-id="016c6-112">En C#, vous écrivez des requêtes de la même manière, que ce soit sur une arborescence XML qui utilise un espace de noms avec un préfixe ou sur une arborescence XML avec un espace de noms par défaut.</span><span class="sxs-lookup"><span data-stu-id="016c6-112">In C#, you write queries in the same way regardless of whether you are writing queries on an XML tree that uses a namespace with a prefix or on an XML tree with a default namespace.</span></span>  
  
 <span data-ttu-id="016c6-113">L’exemple suivant crée une arborescence XML qui est dans un espace de noms avec un préfixe.</span><span class="sxs-lookup"><span data-stu-id="016c6-113">The following example creates an XML tree that is in a namespace with a prefix.</span></span> <span data-ttu-id="016c6-114">Il récupère ensuite une collection d'éléments.</span><span class="sxs-lookup"><span data-stu-id="016c6-114">It then retrieves a collection of elements.</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = XElement.Parse(  
@"<aw:Root xmlns:aw='http://www.adventure-works.com'>  
    <aw:Child>1</aw:Child>  
    <aw:Child>2</aw:Child>  
    <aw:Child>3</aw:Child>  
    <aw:AnotherChild>4</aw:AnotherChild>  
    <aw:AnotherChild>5</aw:AnotherChild>  
    <aw:AnotherChild>6</aw:AnotherChild>  
</aw:Root>");  
IEnumerable<XElement> c1 =  
    from el in root.Elements(aw + "Child")  
    select el;  
foreach (XElement el in c1)  
    Console.WriteLine((int)el);  
```  
  
 <span data-ttu-id="016c6-115">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="016c6-115">This example produces the following output:</span></span>  
  
```output  
1  
2  
3  
```  
  
## <a name="see-also"></a><span data-ttu-id="016c6-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="016c6-116">See also</span></span>

- [<span data-ttu-id="016c6-117">Vue d’ensemble des espaces de noms (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="016c6-117">Namespaces Overview (LINQ to XML) (C#)</span></span>](namespaces-overview-linq-to-xml.md)
