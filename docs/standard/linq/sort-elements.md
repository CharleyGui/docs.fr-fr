---
title: Comment trier des éléments-LINQ to XML
description: Découvrez comment écrire une requête qui trie ses résultats.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: aee6fbbc-81fd-4b3e-b40f-6ed7b3bd3fee
ms.openlocfilehash: c2d7915aacf0c41e99581fa8b5cc397bcaf5c612
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553420"
---
# <a name="how-to-sort-elements-linq-to-xml"></a><span data-ttu-id="cab32-103">Comment trier des éléments (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="cab32-103">How to sort elements (LINQ to XML)</span></span>

<span data-ttu-id="cab32-104">Vous pouvez trier vos résultats lorsque vous interrogez XML.</span><span class="sxs-lookup"><span data-stu-id="cab32-104">You can sort your results when you query XML.</span></span> <span data-ttu-id="cab32-105">Cet article fournit deux exemples : le premier trie les résultats pour le code XML qui *n’est pas* dans un espace de noms et le second effectue le même tri, mais pour le code XML qui *se trouve* dans un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="cab32-105">This article provides two examples: the first sorts results for XML that *isn't* in a namespace, and the second does the same sort, but for XML that *is* in a namespace.</span></span>

## <a name="example-write-a-query-that-sorts-its-results"></a><span data-ttu-id="cab32-106">Exemple : écrire une requête qui trie ses résultats</span><span class="sxs-lookup"><span data-stu-id="cab32-106">Example: Write a query that sorts its results</span></span>

<span data-ttu-id="cab32-107">Cet exemple montre comment écrire une requête qui trie ses résultats.</span><span class="sxs-lookup"><span data-stu-id="cab32-107">This example shows how to write a query that sorts its results.</span></span> <span data-ttu-id="cab32-108">Il utilise le document XML [exemple de fichier XML : données numériques](sample-xml-file-numerical-data.md).</span><span class="sxs-lookup"><span data-stu-id="cab32-108">It uses XML document [Sample XML file: Numerical data](sample-xml-file-numerical-data.md).</span></span>

```csharp
XElement root = XElement.Load("Data.xml");
IEnumerable<decimal> prices =
    from el in root.Elements("Data")
    let price = (decimal)el.Element("Price")
    orderby price
    select price;
foreach (decimal el in prices)
    Console.WriteLine(el);
```

```vb
Dim root As XElement = XElement.Load("Data.xml")
Dim prices As IEnumerable(Of Decimal) = _
    From el In root.<Data> _
    Let price = Convert.ToDecimal(el.<Price>.Value) _
    Order By (price) _
    Select price
For Each el As Decimal In prices
    Console.WriteLine(el)
Next
```

<span data-ttu-id="cab32-109">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="cab32-109">This example produces the following output:</span></span>

```output
0.99
4.95
6.99
24.50
29.00
66.00
89.99
```

## <a name="example-write-a-query-in-a-namespace-that-sorts-its-results"></a><span data-ttu-id="cab32-110">Exemple : écrire une requête dans un espace de noms qui trie ses résultats</span><span class="sxs-lookup"><span data-stu-id="cab32-110">Example: Write a query in a namespace that sorts its results</span></span>

<span data-ttu-id="cab32-111">L’exemple suivant illustre la même requête pour du code XML qui se trouve dans un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="cab32-111">The following example shows the same query for XML that's in a namespace.</span></span> <span data-ttu-id="cab32-112">Il utilise le document XML [exemple de fichier XML : données numériques dans un espace de noms](sample-xml-file-numerical-data-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="cab32-112">It uses XML document [Sample XML file: Numerical data in a namespace](sample-xml-file-numerical-data-namespace.md).</span></span>

<span data-ttu-id="cab32-113">Pour plus d’informations, consultez [vue d’ensemble des espaces de noms](namespaces-overview.md).</span><span class="sxs-lookup"><span data-stu-id="cab32-113">For more information, see [Namespaces overview](namespaces-overview.md).</span></span>

```csharp
XElement root = XElement.Load("DataInNamespace.xml");
XNamespace aw = "http://www.adatum.com";
IEnumerable<decimal> prices =
    from el in root.Elements(aw + "Data")
    let price = (decimal)el.Element(aw + "Price")
    orderby price
    select price;
foreach (decimal el in prices)
    Console.WriteLine(el);
```

```vb
Imports <xmlns='http://www.adatum.com'>

Module Module1
    Sub Main()
        Dim root As XElement = XElement.Load("DataInNamespace.xml")
        Dim prices As IEnumerable(Of Decimal) = _
            From el In root.<Data> _
            Let price = Convert.ToDecimal(el.<Price>.Value) _
            Order By (price) _
            Select price
        For Each el As Decimal In prices
            Console.WriteLine(el)
        Next
    End Sub
End Module
```

<span data-ttu-id="cab32-114">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="cab32-114">This example produces the following output:</span></span>

```output
0.99
4.95
6.99
24.50
29.00
66.00
89.99
```

## <a name="see-also"></a><span data-ttu-id="cab32-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cab32-115">See also</span></span>

- [<span data-ttu-id="cab32-116">Tri des données (C#)</span><span class="sxs-lookup"><span data-stu-id="cab32-116">Sorting Data (C#)</span></span>](../../csharp/programming-guide/concepts/linq/sorting-data.md)
- [<span data-ttu-id="cab32-117">Tri des données (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cab32-117">Sorting Data (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/sorting-data.md)
- [<span data-ttu-id="cab32-118">Requêtes de base (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cab32-118">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
