---
title: 'Procédure : Écrire des requêtes sur du code XML dans des espaces de noms (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 7d4131b5-3288-414f-b77c-b2edc2a1f465
ms.openlocfilehash: 3b910e8b46632fbff2228baef44a45e8c22d731e
ms.sourcegitcommit: eb9ff6f364cde6f11322e03800d8f5ce302f3c73
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68709874"
---
# <a name="how-to-write-queries-on-xml-in-namespaces-visual-basic"></a><span data-ttu-id="7035f-102">Procédure : Écrire des requêtes sur du code XML dans des espaces de noms (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7035f-102">How to: Write Queries on XML in Namespaces (Visual Basic)</span></span>
<span data-ttu-id="7035f-103">Pour écrire des requêtes sur du code XML qui est dans un espace de noms, vous devez utiliser des objets <xref:System.Xml.Linq.XName> qui ont l'espace de noms correct.</span><span class="sxs-lookup"><span data-stu-id="7035f-103">To write a query on XML that is in a namespace, you must use <xref:System.Xml.Linq.XName> objects that have the correct namespace.</span></span>  
  
 <span data-ttu-id="7035f-104">Dans Visual Basic, l'approche la plus courante consiste à définir un espace de noms global, puis à utiliser des littéraux XML et des propriétés XML qui emploient l'espace de noms global.</span><span class="sxs-lookup"><span data-stu-id="7035f-104">In Visual Basic, the most common approach is to define a global namespace, and then use XML literals and XML properties that use the global namespace.</span></span> <span data-ttu-id="7035f-105">Vous pouvez définir un espace de noms par défaut global, auquel cas les éléments dans les littéraux XML seront par défaut dans l'espace de noms.</span><span class="sxs-lookup"><span data-stu-id="7035f-105">You can define a global default namespace, in which case elements in the XML literals will be in the namespace by default.</span></span> <span data-ttu-id="7035f-106">En guise d'alternative, vous pouvez définir un espace de noms global avec un préfixe, puis utiliser le préfixe selon les besoins dans les littéraux XML et les propriétés XML.</span><span class="sxs-lookup"><span data-stu-id="7035f-106">Alternatively, you can define a global namespace with a prefix, and then use the prefix as required in the XML literals, and in XML properties.</span></span> <span data-ttu-id="7035f-107">Comme avec d'autres formes de code XML, les attributs ne sont jamais dans aucun espace de noms par défaut.</span><span class="sxs-lookup"><span data-stu-id="7035f-107">As with other forms of XML, attributes are always in no namespace by default.</span></span>  
  
 <span data-ttu-id="7035f-108">Le premier ensemble d’exemples de cette rubrique montre comment créer une arborescence XML dans un espace de noms par défaut.</span><span class="sxs-lookup"><span data-stu-id="7035f-108">The first set of examples in this topic shows how to create an XML tree in a default namespace.</span></span> <span data-ttu-id="7035f-109">Le second ensemble illustre la création d’une arborescence XML dans un espace de noms avec un préfixe.</span><span class="sxs-lookup"><span data-stu-id="7035f-109">The second set shows how to create an XML tree in a namespace with a prefix.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7035f-110">Exemples</span><span class="sxs-lookup"><span data-stu-id="7035f-110">Example</span></span>  
 <span data-ttu-id="7035f-111">L’exemple suivant crée une arborescence XML qui est dans un espace de noms par défaut.</span><span class="sxs-lookup"><span data-stu-id="7035f-111">The following example creates an XML tree that is in a default namespace.</span></span> <span data-ttu-id="7035f-112">Il récupère ensuite une collection d'éléments.</span><span class="sxs-lookup"><span data-stu-id="7035f-112">It then retrieves a collection of elements.</span></span>  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <Root>  
                <Child>1</Child>  
                <Child>2</Child>  
                <Child>3</Child>  
                <AnotherChild>4</AnotherChild>  
                <AnotherChild>5</AnotherChild>  
                <AnotherChild>6</AnotherChild>  
            </Root>  
        Dim c1 As IEnumerable(Of XElement) = _  
            From el In root.<Child> _  
            Select el  
        For Each el As XElement In c1  
            Console.WriteLine(el.Value)  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="7035f-113">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="7035f-113">This example produces the following output:</span></span>  
  
```  
1  
2  
3  
```  
  
## <a name="example"></a><span data-ttu-id="7035f-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="7035f-114">Example</span></span>  
 <span data-ttu-id="7035f-115">En Visual Basic, toutefois, l'écriture de requêtes sur sur arborescence XML qui utilise un espace de noms avec un préfixe diffère de l'écriture sur une arborescence XML dans un espace de noms par défaut.</span><span class="sxs-lookup"><span data-stu-id="7035f-115">In Visual Basic, however, writing queries on an XML tree that uses a namespace with a prefix is quite different from querying an XML tree in a default namespace.</span></span> <span data-ttu-id="7035f-116">En général, vous devez utiliser l'instruction `Imports` pour importer l'espace de noms avec un préfixe.</span><span class="sxs-lookup"><span data-stu-id="7035f-116">Typically you use the `Imports` statement to import the namespace with a prefix.</span></span> <span data-ttu-id="7035f-117">Vous utilisez ensuite le préfixe dans les noms d’éléments et d’attributs, lors de la construction de l’arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="7035f-117">You then use the prefix in the element and attribute names when you construct the XML tree.</span></span> <span data-ttu-id="7035f-118">Vous utilisez également le préfixe lors de l’interrogation d’une arborescence XML avec des propriétés XML.</span><span class="sxs-lookup"><span data-stu-id="7035f-118">You also use the prefix when querying an XML tree using XML properties.</span></span>  
  
 <span data-ttu-id="7035f-119">L’exemple suivant crée une arborescence XML qui est dans un espace de noms avec un préfixe.</span><span class="sxs-lookup"><span data-stu-id="7035f-119">The following example creates an XML tree that is in a namespace with a prefix.</span></span> <span data-ttu-id="7035f-120">Il récupère ensuite une collection d'éléments.</span><span class="sxs-lookup"><span data-stu-id="7035f-120">It then retrieves a collection of elements.</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <aw:Root>  
                <aw:Child>1</aw:Child>  
                <aw:Child>2</aw:Child>  
                <aw:Child>3</aw:Child>  
                <aw:AnotherChild>4</aw:AnotherChild>  
                <aw:AnotherChild>5</aw:AnotherChild>  
                <aw:AnotherChild>6</aw:AnotherChild>  
            </aw:Root>  
        Dim c1 As IEnumerable(Of XElement) = _  
            From el In root.<aw:Child> _  
            Select el  
        For Each el As XElement In c1  
            Console.WriteLine(CInt(el))  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="7035f-121">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="7035f-121">This example produces the following output:</span></span>  
  
```  
1  
2  
3  
```  
  
## <a name="see-also"></a><span data-ttu-id="7035f-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7035f-122">See also</span></span>

- [<span data-ttu-id="7035f-123">Vue d’ensemble des espaces de noms (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7035f-123">Namespaces Overview (LINQ to XML) (Visual Basic)</span></span>](namespaces-overview-linq-to-xml.md)
