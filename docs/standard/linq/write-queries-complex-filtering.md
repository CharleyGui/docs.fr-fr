---
title: Comment écrire des requêtes avec un filtrage complexe-LINQ to XML
description: Il peut arriver que vous souhaitiez écrire des requêtes LINQ to XML à l'aide de filtres complexes. Par exemple, il se peut que vous deviez rechercher tous les éléments qui ont un élément enfant avec un nom et une valeur spécifiques.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 4065d901-cf89-4e47-8bf9-abb65acfb003
ms.openlocfilehash: c5e7f812364e7e96e3a4b8f5515d07a3524ec979
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553809"
---
# <a name="how-to-write-queries-with-complex-filtering-linq-to-xml"></a><span data-ttu-id="4d4b6-104">Comment écrire des requêtes avec un filtrage complexe (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="4d4b6-104">How to write queries with complex filtering (LINQ to XML)</span></span>

<span data-ttu-id="4d4b6-105">Il peut arriver que vous souhaitiez écrire des requêtes LINQ to XML à l'aide de filtres complexes.</span><span class="sxs-lookup"><span data-stu-id="4d4b6-105">Sometimes you want to write LINQ to XML queries with complex filters.</span></span> <span data-ttu-id="4d4b6-106">Par exemple, il se peut que vous deviez rechercher tous les éléments qui ont un élément enfant avec un nom et une valeur spécifiques.</span><span class="sxs-lookup"><span data-stu-id="4d4b6-106">For example, you might have to find all elements that have a child element with a particular name and value.</span></span> <span data-ttu-id="4d4b6-107">Cet article donne un exemple d’écriture d’une requête avec un filtrage complexe.</span><span class="sxs-lookup"><span data-stu-id="4d4b6-107">This article gives an example of writing a query with complex filtering.</span></span>

## <a name="example-find-with-a-nested-query-in-the-where-clause"></a><span data-ttu-id="4d4b6-108">Exemple : Rechercher avec une requête imbriquée dans la `Where` clause</span><span class="sxs-lookup"><span data-stu-id="4d4b6-108">Example: Find with a nested query in the `Where` clause</span></span>

<span data-ttu-id="4d4b6-109">Cet exemple montre comment rechercher tous les `PurchaseOrder` éléments qui ont :</span><span class="sxs-lookup"><span data-stu-id="4d4b6-109">This example shows how to find all `PurchaseOrder` elements that have:</span></span>

- <span data-ttu-id="4d4b6-110">Élément enfant `Address` dont l' `Type` attribut est égal à « Shipping ».</span><span class="sxs-lookup"><span data-stu-id="4d4b6-110">A child `Address` element whose `Type` attribute equals "Shipping".</span></span>
- <span data-ttu-id="4d4b6-111">Élément enfant `State` qui est égal à « NY ».</span><span class="sxs-lookup"><span data-stu-id="4d4b6-111">A child `State` element that equals "NY".</span></span>

<span data-ttu-id="4d4b6-112">Il utilise une sous-requête dans la clause `Where` et l'opérateur `Any` retourne `true` si la collection possède des éléments.</span><span class="sxs-lookup"><span data-stu-id="4d4b6-112">It uses a nested query in the `Where` clause, and the `Any` operator returns `true` if the collection has any elements in it.</span></span> <span data-ttu-id="4d4b6-113">L’exemple utilise un document XML [exemple de fichier XML : plusieurs commandes fournisseur](sample-xml-file-multiple-purchase-orders.md).</span><span class="sxs-lookup"><span data-stu-id="4d4b6-113">The example uses XML document [Sample XML file: Multiple purchase orders](sample-xml-file-multiple-purchase-orders.md).</span></span>

<span data-ttu-id="4d4b6-114">Pour plus d’informations sur l' `Any` opérateur, consultez [opérations de quantificateur (C#)](../../../docs/csharp/programming-guide/concepts/linq/quantifier-operations.md) et [opérations de quantificateur (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md).</span><span class="sxs-lookup"><span data-stu-id="4d4b6-114">For more information about the `Any` operator, see [Quantifier Operations (C#)](../../../docs/csharp/programming-guide/concepts/linq/quantifier-operations.md) and [Quantifier Operations (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md).</span></span>

```csharp
XElement root = XElement.Load("PurchaseOrders.xml");
IEnumerable<XElement> purchaseOrders =
    from el in root.Elements("PurchaseOrder")
    where
        (from add in el.Elements("Address")
        where
            (string)add.Attribute("Type") == "Shipping" &&
            (string)add.Element("State") == "NY"
        select add)
        .Any()
    select el;
foreach (XElement el in purchaseOrders)
    Console.WriteLine((string)el.Attribute("PurchaseOrderNumber"));
```

```vb
Dim root As XElement = XElement.Load("PurchaseOrders.xml")
Dim purchaseOrders As IEnumerable(Of XElement) = _
    From el In root.<PurchaseOrder> _
    Where _
        (From add In el.<Address> _
        Where _
             add.@Type = "Shipping" And _
             add.<State>.Value = "NY" _
        Select add) _
    .Any() _
    Select el
For Each el As XElement In purchaseOrders
    Console.WriteLine(el.@PurchaseOrderNumber)
Next
```

<span data-ttu-id="4d4b6-115">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="4d4b6-115">This example produces the following output:</span></span>

```output
99505
```

## <a name="example-find-in-xml-thats-in-a-namespace"></a><span data-ttu-id="4d4b6-116">Exemple : Rechercher dans du code XML qui se trouve dans un espace de noms</span><span class="sxs-lookup"><span data-stu-id="4d4b6-116">Example: Find in XML that's in a namespace</span></span>

<span data-ttu-id="4d4b6-117">L’exemple suivant illustre la même requête que ci-dessus, mais pour le code XML qui se trouve dans un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="4d4b6-117">The following example shows the same query as above, but for XML that's in a namespace.</span></span> <span data-ttu-id="4d4b6-118">Pour plus d’informations, consultez [vue d’ensemble des espaces de noms](namespaces-overview.md).</span><span class="sxs-lookup"><span data-stu-id="4d4b6-118">For more information, see [Namespaces overview](namespaces-overview.md).</span></span>

<span data-ttu-id="4d4b6-119">Cet exemple utilise le document XML [exemple de fichier XML : plusieurs commandes fournisseur dans un espace de noms](sample-xml-file-multiple-purchase-orders-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="4d4b6-119">This example uses XML document [Sample XML file: Multiple purchase orders in a namespace](sample-xml-file-multiple-purchase-orders-namespace.md).</span></span>

```csharp
XElement root = XElement.Load("PurchaseOrdersInNamespace.xml");
XNamespace aw = "http://www.adventure-works.com";
IEnumerable<XElement> purchaseOrders =
    from el in root.Elements(aw + "PurchaseOrder")
    where
        (from add in el.Elements(aw + "Address")
         where
             (string)add.Attribute(aw + "Type") == "Shipping" &&
             (string)add.Element(aw + "State") == "NY"
         select add)
        .Any()
    select el;
foreach (XElement el in purchaseOrders)
    Console.WriteLine((string)el.Attribute(aw + "PurchaseOrderNumber"));
```

```vb
Imports <xmlns:aw='http://www.adventure-works.com'>

Module Module1
    Sub Main()
        Dim root As XElement = XElement.Load("PurchaseOrdersInNamespace.xml")
        Dim purchaseOrders As IEnumerable(Of XElement) = _
            From el In root.<aw:PurchaseOrder> _
            Where _
                (From add In el.<aw:Address> _
                Where _
                     add.@aw:Type = "Shipping" And _
                     add.<aw:State>.Value = "NY" _
                Select add) _
            .Any() _
            Select el
        For Each el As XElement In purchaseOrders
            Console.WriteLine(el.@aw:PurchaseOrderNumber)
        Next
    End Sub
End Module
```

<span data-ttu-id="4d4b6-120">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="4d4b6-120">This example produces the following output:</span></span>

```output
99505
```

## <a name="see-also"></a><span data-ttu-id="4d4b6-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4d4b6-121">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [<span data-ttu-id="4d4b6-122">Opérations de projection (C#)</span><span class="sxs-lookup"><span data-stu-id="4d4b6-122">Projection Operations (C#)</span></span>](../../csharp/programming-guide/concepts/linq/projection-operations.md)
- [<span data-ttu-id="4d4b6-123">Opérations de quantificateur (C#)</span><span class="sxs-lookup"><span data-stu-id="4d4b6-123">Quantifier Operations (C#)</span></span>](../../csharp/programming-guide/concepts/linq/quantifier-operations.md)
- [<span data-ttu-id="4d4b6-124">Propriété d'axe enfant XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4d4b6-124">XML Child Axis Property (Visual Basic)</span></span>](../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)
- [<span data-ttu-id="4d4b6-125">Propriété d'axe d'attribut XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4d4b6-125">XML Attribute Axis Property (Visual Basic)</span></span>](../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)
- [<span data-ttu-id="4d4b6-126">Propriété de valeur XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4d4b6-126">XML Value Property (Visual Basic)</span></span>](../../visual-basic/language-reference/xml-axis/xml-value-property.md)
- [<span data-ttu-id="4d4b6-127">Opérations de projection (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4d4b6-127">Projection Operations (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/projection-operations.md)
- [<span data-ttu-id="4d4b6-128">Opérations de quantificateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4d4b6-128">Quantifier Operations (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md)
