---
title: Comment déboguer des ensembles de résultats de requête vides-LINQ to XML
description: Lorsque vous interrogez une arborescence XML dans un espace de noms par défaut, évitez l’erreur courante d’interrogation comme si le XML ne se trouvait pas dans un espace de noms.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: b569f0dc-425e-45a6-acbf-770fb761c981
ms.openlocfilehash: 3320763fffe77ddd6ca4c78e77629ec0805e4290
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553487"
---
# <a name="how-to-debug-empty-query-results-sets-linq-to-xml"></a><span data-ttu-id="679af-103">Comment déboguer des ensembles de résultats de requête vides (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="679af-103">How to debug empty query results sets (LINQ to XML)</span></span>

<span data-ttu-id="679af-104">L'un des problèmes les plus courants lors de l'interrogation d'une arborescence XML est que si celle-ci possède un espace de noms par défaut, le développeur écrit parfois la requête comme si le code XML n'était dans aucun espace de noms.</span><span class="sxs-lookup"><span data-stu-id="679af-104">One of the most common problems when querying XML trees is that if the XML tree has a default namespace, the developer sometimes writes the query as though the XML were not in a namespace.</span></span>

<span data-ttu-id="679af-105">Le premier ensemble d’exemples de cet article illustre le chargement d’un fichier XML dans un espace de noms par défaut et son interrogation incorrecte.</span><span class="sxs-lookup"><span data-stu-id="679af-105">The first set of examples in this article shows a typical way that XML in a default namespace is loaded, and then queried improperly.</span></span>

<span data-ttu-id="679af-106">Le deuxième ensemble d'exemples illustre les corrections que vous devez apporter pour pouvoir interroger du code XML dans un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="679af-106">The second set of examples show the necessary corrections so that you can query XML in a namespace.</span></span>

<span data-ttu-id="679af-107">Pour plus d’informations, consultez [vue d’ensemble des espaces de noms](namespaces-overview.md).</span><span class="sxs-lookup"><span data-stu-id="679af-107">For more information, see [Namespaces overview](namespaces-overview.md).</span></span>

## <a name="example-an-improper-query-on-xml-in-a-namespace"></a><span data-ttu-id="679af-108">Exemple : une requête incorrecte sur XML dans un espace de noms</span><span class="sxs-lookup"><span data-stu-id="679af-108">Example: An improper query on XML in a namespace</span></span>

<span data-ttu-id="679af-109">Cet exemple illustre la création de code XML dans un espace de noms et une requête qui retourne un jeu de résultats vide.</span><span class="sxs-lookup"><span data-stu-id="679af-109">This example shows creation of XML in a namespace, and a query that returns an empty result set.</span></span>

```csharp
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
    from el in root.Elements("Child")
    select el;
Console.WriteLine("Result set follows:");
foreach (XElement el in c1)
    Console.WriteLine((int)el);
Console.WriteLine("End of result set");
```

```vb
Dim root As XElement = _
    <Root xmlns='http://www.adventure-works.com'>
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
Console.WriteLine("Result set follows:")
For Each el As XElement In c1
    Console.WriteLine(el.Value)
Next
Console.WriteLine("End of result set")
```

<span data-ttu-id="679af-110">L’exemple produit le résultat suivant :</span><span class="sxs-lookup"><span data-stu-id="679af-110">The example produces this result:</span></span>

```output
Result set follows:
End of result set
```

## <a name="example-a-proper-query-on-xml-in-a-namespace"></a><span data-ttu-id="679af-111">Exemple : une requête correcte sur XML dans un espace de noms</span><span class="sxs-lookup"><span data-stu-id="679af-111">Example: A proper query on XML in a namespace</span></span>

<span data-ttu-id="679af-112">Cet exemple illustre la création de code XML dans un espace de noms et une requête qui est codée correctement.</span><span class="sxs-lookup"><span data-stu-id="679af-112">This example shows creation of XML in a namespace, and a query that's  coded properly.</span></span>

<span data-ttu-id="679af-113">La solution consiste à déclarer et à initialiser un objet <xref:System.Xml.Linq.XNamespace> et à l’utiliser lors de la spécification d’objets <xref:System.Xml.Linq.XName>.</span><span class="sxs-lookup"><span data-stu-id="679af-113">The solution is to declare and initialize an <xref:System.Xml.Linq.XNamespace> object, and to use it when specifying <xref:System.Xml.Linq.XName> objects.</span></span> <span data-ttu-id="679af-114">Dans ce cas, l'argument de la méthode <xref:System.Xml.Linq.XContainer.Elements%2A> est un objet <xref:System.Xml.Linq.XName>.</span><span class="sxs-lookup"><span data-stu-id="679af-114">In this case, the argument to the <xref:System.Xml.Linq.XContainer.Elements%2A> method is an <xref:System.Xml.Linq.XName> object.</span></span>

```csharp
XElement root = XElement.Parse(
@"<Root xmlns='http://www.adventure-works.com'>
    <Child>1</Child>
    <Child>2</Child>
    <Child>3</Child>
    <AnotherChild>4</AnotherChild>
    <AnotherChild>5</AnotherChild>
    <AnotherChild>6</AnotherChild>
</Root>");
XNamespace aw = "http://www.adventure-works.com";
IEnumerable<XElement> c1 =
    from el in root.Elements(aw + "Child")
    select el;
Console.WriteLine("Result set follows:");
foreach (XElement el in c1)
    Console.WriteLine((int)el);
Console.WriteLine("End of result set");
```

```vb
Imports <xmlns="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim root As XElement = _
            <Root xmlns='http://www.adventure-works.com'>
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
        Console.WriteLine("Result set follows:")
        For Each el As XElement In c1
            Console.WriteLine(CInt(el))
        Next
        Console.WriteLine("End of result set")
    End Sub
End Module
```

<span data-ttu-id="679af-115">L’exemple produit le résultat suivant :</span><span class="sxs-lookup"><span data-stu-id="679af-115">The example produces this result:</span></span>

```output
Result set follows:
1
2
3
End of result set
```

## <a name="see-also"></a><span data-ttu-id="679af-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="679af-116">See also</span></span>

- [<span data-ttu-id="679af-117">Requêtes de base (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="679af-117">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
