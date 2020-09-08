---
title: Comment calculer des valeurs intermédiaires-LINQ to XML
description: Calculez les valeurs intermédiaires à utiliser pour le tri, le filtrage et la sélection.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 7fd3001f-f8f9-4bce-879f-d4c7af8a04fe
ms.openlocfilehash: aa5b83e9bf359481773db673fd3de9c4dcff6af2
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552456"
---
# <a name="how-to-calculate-intermediate-values-linq-to-xml"></a><span data-ttu-id="019f0-103">Comment calculer des valeurs intermédiaires (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="019f0-103">How to calculate intermediate values (LINQ to XML)</span></span>

<span data-ttu-id="019f0-104">Cet article montre comment calculer des valeurs intermédiaires à utiliser pour le tri, le filtrage et la sélection en C# et Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="019f0-104">This article shows how to calculate intermediate values for use in sorting, filtering, and selecting in C# and Visual Basic.</span></span>

## <a name="example-use-the-let-clause-to-calculate-based-on-element-data"></a><span data-ttu-id="019f0-105">Exemple : utiliser la `let` clause pour calculer en fonction des données d’élément</span><span class="sxs-lookup"><span data-stu-id="019f0-105">Example: Use the `let` clause to calculate based on element data</span></span>

<span data-ttu-id="019f0-106">L’exemple suivant utilise la `let` clause pour calculer des produits de valeurs numériques à partir d’éléments.</span><span class="sxs-lookup"><span data-stu-id="019f0-106">The following example uses the `let` clause to calculate products of numerical values from elements.</span></span> <span data-ttu-id="019f0-107">Il utilise le document XML [exemple de fichier XML : données numériques](sample-xml-file-numerical-data.md).</span><span class="sxs-lookup"><span data-stu-id="019f0-107">It uses XML document [Sample XML file: Numerical data](sample-xml-file-numerical-data.md).</span></span>

```csharp
XElement root = XElement.Load("Data.xml");
IEnumerable<decimal> extensions =
    from el in root.Elements("Data")
    let extension = (decimal)el.Element("Quantity") * (decimal)el.Element("Price")
    where extension >= 25
    orderby extension
    select extension;
foreach (decimal ex in extensions)
    Console.WriteLine(ex);
```

```vb
Dim root As XElement = XElement.Load("Data.xml")
Dim extensions As IEnumerable(Of Decimal) = _
    From el In root.<Data> _
    Let extension = CDec(el.<Quantity>.Value) * CDec(el.<Price>.Value) _
    Where extension > 25 _
    Order By extension _
    Select extension
For Each ex As Decimal In extensions
    Console.WriteLine(ex)
Next
```

<span data-ttu-id="019f0-108">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="019f0-108">This example produces the following output:</span></span>

```output
55.92
73.50
89.99
198.00
435.00
```

## <a name="example-calculate-from-xml-thats-in-a-namespace"></a><span data-ttu-id="019f0-109">Exemple : calculer à partir du code XML qui se trouve dans un espace de noms</span><span class="sxs-lookup"><span data-stu-id="019f0-109">Example: Calculate from XML that's in a namespace</span></span>

<span data-ttu-id="019f0-110">L’exemple suivant illustre la même requête que précédemment, mais pour le code XML qui se trouve dans un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="019f0-110">The following example shows the same query as before, but for XML that's in a namespace.</span></span> <span data-ttu-id="019f0-111">Elle utilise le document XML [exemple de fichier XML : données numériques dans un espace de noms](sample-xml-file-numerical-data-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="019f0-111">It uses the XML document [Sample XML file: Numerical data in a namespace](sample-xml-file-numerical-data-namespace.md).</span></span>

<span data-ttu-id="019f0-112">Pour plus d’informations, consultez [vue d’ensemble des espaces de noms](namespaces-overview.md).</span><span class="sxs-lookup"><span data-stu-id="019f0-112">For more information, see [Namespaces overview](namespaces-overview.md).</span></span>

```csharp
XElement root = XElement.Load("DataInNamespace.xml");
XNamespace ad = "http://www.adatum.com";
IEnumerable<decimal> extensions =
    from el in root.Elements(ad + "Data")
    let extension = (decimal)el.Element(ad + "Quantity") * (decimal)el.Element(ad + "Price")
    where extension >= 25
    orderby extension
    select extension;
foreach (decimal ex in extensions)
    Console.WriteLine(ex);
```

```vb
Imports <xmlns="http://www.adatum.com">

Module Module1
    Sub Main()
        Dim root As XElement = XElement.Load("DataInNamespace.xml")
        Dim extensions As IEnumerable(Of Decimal) = _
            From el In root.<Data> _
            Let extension = CDec(el.<Quantity>.Value) * CDec(el.<Price>.Value) _
            Where extension > 25 _
            Order By extension _
            Select extension
        For Each ex As Decimal In extensions
            Console.WriteLine(ex)
        Next
    End Sub
End Module
```

<span data-ttu-id="019f0-113">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="019f0-113">This example produces the following output:</span></span>

```output
55.92
73.50
89.99
198.00
435.00
```

## <a name="see-also"></a><span data-ttu-id="019f0-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="019f0-114">See also</span></span>

- [<span data-ttu-id="019f0-115">Requêtes de base (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="019f0-115">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
