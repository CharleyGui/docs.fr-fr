---
title: Comment rechercher un élément avec un attribut spécifique-LINQ to XML
description: Découvrez comment rechercher un élément dont l’attribut a une valeur spécifique.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: b92591aa-3cfb-490e-99f6-da8de335e362
ms.openlocfilehash: 4c74de90a348d81ac87c98bf6ee27f3c78f34e83
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552352"
---
# <a name="how-to-find-an-element-with-a-specific-attribute-linq-to-xml"></a><span data-ttu-id="0a7aa-103">Comment rechercher un élément avec un attribut spécifique (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="0a7aa-103">How to find an element with a specific attribute (LINQ to XML)</span></span>

<span data-ttu-id="0a7aa-104">Cet article fournit des exemples de recherche d’un élément dont l’attribut a une valeur spécifique.</span><span class="sxs-lookup"><span data-stu-id="0a7aa-104">This article provides examples of how to find an element whose attribute has a specific value.</span></span>

## <a name="example-find-an-element-whose-attribute-has-a-specific-value"></a><span data-ttu-id="0a7aa-105">Exemple : Rechercher un élément dont l’attribut a une valeur spécifique</span><span class="sxs-lookup"><span data-stu-id="0a7aa-105">Example: Find an element whose attribute has a specific value</span></span>

<span data-ttu-id="0a7aa-106">L’exemple suivant montre comment Rechercher l' `Address` élément qui a un `Type` attribut avec la valeur « Billing ».</span><span class="sxs-lookup"><span data-stu-id="0a7aa-106">The following example shows how to find the `Address` element that has a `Type` attribute with a value of "Billing".</span></span> <span data-ttu-id="0a7aa-107">L’exemple utilise un document XML [exemple de fichier XML : commande fournisseur typique](sample-xml-file-typical-purchase-order.md).</span><span class="sxs-lookup"><span data-stu-id="0a7aa-107">The example uses XML document [Sample XML file: Typical purchase order](sample-xml-file-typical-purchase-order.md).</span></span>

```csharp
XElement root = XElement.Load("PurchaseOrder.xml");
IEnumerable<XElement> address =
    from el in root.Elements("Address")
    where (string)el.Attribute("Type") == "Billing"
    select el;
foreach (XElement el in address)
    Console.WriteLine(el);
```

```vb
Dim root As XElement = XElement.Load("PurchaseOrder.xml")
Dim address As IEnumerable(Of XElement) = _
    From el In root.<Address> _
    Where el.@Type = "Billing" _
    Select el
For Each el As XElement In address
    Console.WriteLine(el)
Next
```

<span data-ttu-id="0a7aa-108">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="0a7aa-108">This example produces the following output:</span></span>

```xml
<Address Type="Billing">
  <Name>Tai Yee</Name>
  <Street>8 Oak Avenue</Street>
  <City>Old Town</City>
  <State>PA</State>
  <Zip>95819</Zip>
  <Country>USA</Country>
</Address>
```

## <a name="example-find-an-element-in-xml-thats-in-a-namespace"></a><span data-ttu-id="0a7aa-109">Exemple : Rechercher un élément dans du code XML qui se trouve dans un espace de noms</span><span class="sxs-lookup"><span data-stu-id="0a7aa-109">Example: Find an element in XML that's in a namespace</span></span>

<span data-ttu-id="0a7aa-110">L’exemple suivant illustre la même requête, mais pour le code XML qui se trouve dans un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="0a7aa-110">The following example shows the same query, but for XML that's in a namespace.</span></span> <span data-ttu-id="0a7aa-111">Elle utilise un document XML [exemple de fichier XML : commande fournisseur typique dans un espace de noms](sample-xml-file-typical-purchase-order-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="0a7aa-111">It uses XML document [Sample XML file: typical purchase order in a namespace](sample-xml-file-typical-purchase-order-namespace.md).</span></span>

<span data-ttu-id="0a7aa-112">Pour plus d’informations sur les espaces de noms, consultez [vue d’ensemble des espaces](namespaces-overview.md)de noms.</span><span class="sxs-lookup"><span data-stu-id="0a7aa-112">For more information about namespaces, see [Namespaces overview](namespaces-overview.md).</span></span>

```csharp
XElement root = XElement.Load("PurchaseOrderInNamespace.xml");
XNamespace aw = "http://www.adventure-works.com";
IEnumerable<XElement> address =
    from el in root.Elements(aw + "Address")
    where (string)el.Attribute(aw + "Type") == "Billing"
    select el;
foreach (XElement el in address)
    Console.WriteLine(el);
```

```vb
Imports <xmlns:aw='http://www.adventure-works.com'>

Module Module1
    Sub Main()
        Dim root As XElement = XElement.Load("PurchaseOrderInNamespace.xml")
        Dim address As IEnumerable(Of XElement) = _
            From el In root.<aw:Address> _
            Where el.@aw:Type = "Billing" _
            Select el
        For Each el As XElement In address
            Console.WriteLine(el)
        Next
    End Sub
End Module
```

<span data-ttu-id="0a7aa-113">Cet exemple produit la sortie suivante ::</span><span class="sxs-lookup"><span data-stu-id="0a7aa-113">This example produces the following output::</span></span>

```xml
<aw:Address aw:Type="Billing" xmlns:aw="http://www.adventure-works.com">
  <aw:Name>Tai Yee</aw:Name>
  <aw:Street>8 Oak Avenue</aw:Street>
  <aw:City>Old Town</aw:City>
  <aw:State>PA</aw:State>
  <aw:Zip>95819</aw:Zip>
  <aw:Country>USA</aw:Country>
</aw:Address>
```

## <a name="see-also"></a><span data-ttu-id="0a7aa-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0a7aa-114">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [<span data-ttu-id="0a7aa-115">Vue d’ensemble des opérateurs de requête standard (C#)</span><span class="sxs-lookup"><span data-stu-id="0a7aa-115">Standard Query Operators Overview (C#)</span></span>](../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="0a7aa-116">Opérations de projection (C#)</span><span class="sxs-lookup"><span data-stu-id="0a7aa-116">Projection Operations (C#)</span></span>](../../csharp/programming-guide/concepts/linq/projection-operations.md)
- [<span data-ttu-id="0a7aa-117">Requêtes de base (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0a7aa-117">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
- [<span data-ttu-id="0a7aa-118">Vue d’ensemble des opérateurs de requête standard (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0a7aa-118">Standard Query Operators Overview (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="0a7aa-119">Opérations de projection (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0a7aa-119">Projection Operations (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/projection-operations.md)
