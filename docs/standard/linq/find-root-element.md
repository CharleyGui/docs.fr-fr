---
title: Comment Rechercher l’élément racine-LINQ to XML
description: Découvrez comment utiliser XPath et LINQ to XML, en C# et Visual Basic, pour Rechercher l’élément racine d’un document XML.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 4fd824e0-4d39-429b-b092-f6a5c046ee6c
ms.openlocfilehash: 89247c19fc31add4e95f11742772cef1bdd2ce63
ms.sourcegitcommit: aa6d8a90a4f5d8fe0f6e967980b8c98433f05a44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90679465"
---
# <a name="how-to-find-the-root-element-linq-to-xml"></a><span data-ttu-id="16da0-103">Comment Rechercher l’élément racine (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="16da0-103">How to find the root element (LINQ to XML)</span></span>

<span data-ttu-id="16da0-104">Cet article fournit un exemple qui montre comment utiliser XPath et LINQ to XML, en C# et Visual Basic, pour Rechercher l’élément racine d’un document XML.</span><span class="sxs-lookup"><span data-stu-id="16da0-104">This article provides an example that shows how to use XPath and LINQ to XML, in C# and Visual Basic, to find the root element of an XML document.</span></span>

## <a name="example-find-the-root-element"></a><span data-ttu-id="16da0-105">Exemple : Rechercher l’élément racine</span><span class="sxs-lookup"><span data-stu-id="16da0-105">Example: Find the root element</span></span>

<span data-ttu-id="16da0-106">Cet exemple utilise LINQ to XML requête et XPath pour Rechercher l’élément racine dans le document XML [exemple de fichier XML : plusieurs commandes fournisseur](sample-xml-file-multiple-purchase-orders.md).</span><span class="sxs-lookup"><span data-stu-id="16da0-106">This example uses LINQ to XML query and XPath to find the root element in XML document [Sample XML file: Multiple purchase orders](sample-xml-file-multiple-purchase-orders.md).</span></span> <span data-ttu-id="16da0-107">L'expression XPath est `/PurchaseOrders`.</span><span class="sxs-lookup"><span data-stu-id="16da0-107">The XPath expression is `/PurchaseOrders`.</span></span>

```csharp
XDocument po = XDocument.Load("PurchaseOrders.xml");

// LINQ to XML query
XElement el1 = po.Root;

// XPath expression
XElement el2 = po.XPathSelectElement("/PurchaseOrders");

if (el1 == el2)
    Console.WriteLine("Results are identical");
else
    Console.WriteLine("Results differ");
Console.WriteLine(el1.Name);
```

```vb
Dim po As XDocument = XDocument.Load("PurchaseOrders.xml")

' LINQ to XML query
Dim el1 As XElement = po.Root

' XPath expression
Dim el2 As XElement = po.XPathSelectElement("/PurchaseOrders")

If el1 Is el2 Then
    Console.WriteLine("Results are identical")
Else
    Console.WriteLine("Results differ")
End If
Console.WriteLine(el1.Name)
```

<span data-ttu-id="16da0-108">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="16da0-108">This example produces the following output:</span></span>

```output
Results are identical
PurchaseOrders
```

## <a name="see-also"></a><span data-ttu-id="16da0-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="16da0-109">See also</span></span>

- [<span data-ttu-id="16da0-110">Comparaison de XPath et LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="16da0-110">Comparison of XPath and LINQ to XML</span></span>](comparison-xpath-linq-xml.md)
