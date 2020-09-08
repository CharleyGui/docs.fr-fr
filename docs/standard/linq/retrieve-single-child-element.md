---
title: Récupération d’un seul élément enfant-LINQ to XML
description: Récupère le premier élément enfant ayant un nom spécifié. Vous pouvez utiliser XContainer. Element en C# et la notation d’indexeur de tableau dans Visual Basic.
ms.date: 07/20/2015
ms.assetid: ce37db9e-76fa-46eb-b4cc-e8f32d22ad90
ms.openlocfilehash: e557e82e4e5891d6890a0efb4973796050b75349
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553653"
---
# <a name="how-to-retrieve-a-single-child-element-linq-to-xml"></a><span data-ttu-id="f378e-104">Comment récupérer un seul élément enfant (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="f378e-104">How to retrieve a single child element (LINQ to XML)</span></span>

<span data-ttu-id="f378e-105">Cet article explique comment récupérer un seul élément enfant, le premier élément enfant portant un nom spécifié.</span><span class="sxs-lookup"><span data-stu-id="f378e-105">This article explains how to retrieve a single child element, the first child element that has a specified name.</span></span> <span data-ttu-id="f378e-106">En C#, vous effectuez cette opération avec la <xref:System.Xml.Linq.XContainer.Element%2A> méthode.</span><span class="sxs-lookup"><span data-stu-id="f378e-106">In C# you do this with the <xref:System.Xml.Linq.XContainer.Element%2A> method.</span></span> <span data-ttu-id="f378e-107">Dans Visual Basic vous le faites avec la notation d’indexeur de tableau.</span><span class="sxs-lookup"><span data-stu-id="f378e-107">In Visual Basic you do it with array indexer notation.</span></span>

## <a name="example-retrieve-the-first-element-that-has-a-specified-name"></a><span data-ttu-id="f378e-108">Exemple : récupérer le premier élément qui porte un nom spécifié</span><span class="sxs-lookup"><span data-stu-id="f378e-108">Example: Retrieve the first element that has a specified name</span></span>

<span data-ttu-id="f378e-109">L’exemple suivant récupère le premier `DeliveryNotes` élément du document XML dans exemple de [fichier XML : commande fournisseur typique](sample-xml-file-typical-purchase-order.md).</span><span class="sxs-lookup"><span data-stu-id="f378e-109">The following example retrieves the first `DeliveryNotes` element from the XML document in [Sample XML file: Typical purchase order](sample-xml-file-typical-purchase-order.md).</span></span>

```csharp
XElement po = XElement.Load("PurchaseOrder.xml");
XElement e = po.Element("DeliveryNotes");
Console.WriteLine(e);
```

```vb
Dim po As XElement = XElement.Load("PurchaseOrder.xml")
Dim e As XElement = po.<DeliveryNotes>(0)
Console.WriteLine(e)
```

<span data-ttu-id="f378e-110">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="f378e-110">This example produces the following output:</span></span>

```xml
<DeliveryNotes>Please leave packages in shed by driveway.</DeliveryNotes>
```

## <a name="example-retrieve-from-xml-thats-in-a-namespace"></a><span data-ttu-id="f378e-111">Exemple : récupérer à partir du code XML qui se trouve dans un espace de noms</span><span class="sxs-lookup"><span data-stu-id="f378e-111">Example: Retrieve from XML that's in a namespace</span></span>

<span data-ttu-id="f378e-112">L’exemple suivant fait la même chose que l’exemple ci-dessus, mais pour le code XML qui se trouve dans un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="f378e-112">The following example does the same thing as the one above, but for XML that's in a namespace.</span></span> <span data-ttu-id="f378e-113">Elle utilise le document XML [exemple de fichier XML : commande fournisseur typique dans un espace de noms](sample-xml-file-typical-purchase-order-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="f378e-113">It uses the XML document [Sample XML file: Typical purchase order in a namespace](sample-xml-file-typical-purchase-order-namespace.md).</span></span> <span data-ttu-id="f378e-114">Pour plus d’informations sur les espaces de noms, consultez [vue d’ensemble des espaces](namespaces-overview.md)de noms.</span><span class="sxs-lookup"><span data-stu-id="f378e-114">For more information about namespaces, see [Namespaces overview](namespaces-overview.md).</span></span>

```csharp
XElement po = XElement.Load("PurchaseOrderInNamespace.xml");
XNamespace aw = "http://www.adventure-works.com";
XElement e = po.Element(aw + "DeliveryNotes");
Console.WriteLine(e);
```

```vb
Imports <xmlns:aw="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim po As XElement = XElement.Load("PurchaseOrderInNamespace.xml")
        Dim e As XElement = po.<aw:DeliveryNotes>(0)
        Console.WriteLine(e)
    End Sub
End Module
```

<span data-ttu-id="f378e-115">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="f378e-115">This example produces the following output:</span></span>

```xml
<aw:DeliveryNotes xmlns:aw="http://www.adventure-works.com">Please leave packages in shed by driveway.</aw:DeliveryNotes>
```

## <a name="see-also"></a><span data-ttu-id="f378e-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f378e-116">See also</span></span>

- [<span data-ttu-id="f378e-117">Vue d’ensemble des axes LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="f378e-117">LINQ to XML axes overview</span></span>](linq-xml-axes-overview.md)
