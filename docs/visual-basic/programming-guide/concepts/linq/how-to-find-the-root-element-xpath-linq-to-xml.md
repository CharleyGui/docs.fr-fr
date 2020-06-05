---
title: 'Procédure : rechercher l’élément racine (XPath-LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 72c3aed5-9522-4454-a876-2070aad13f2e
ms.openlocfilehash: d1a507f97954c62672689bae719f251fed9a298b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84364511"
---
# <a name="how-to-find-the-root-element-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="a80b5-102">Comment : Rechercher l’élément racine (XPath-LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a80b5-102">How to: Find the Root Element (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="a80b5-103">Cette rubrique montre comment obtenir l'élément racine avec XPath et [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a80b5-103">This topic shows how to get the root element with XPath and [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="a80b5-104">L’expression XPath est la suivante :</span><span class="sxs-lookup"><span data-stu-id="a80b5-104">The XPath expression is:</span></span>  
  
 `/PurchaseOrders`  
  
## <a name="example"></a><span data-ttu-id="a80b5-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="a80b5-105">Example</span></span>  
 <span data-ttu-id="a80b5-106">Cet exemple recherche l'élément racine.</span><span class="sxs-lookup"><span data-stu-id="a80b5-106">This example finds the root element.</span></span>  
  
 <span data-ttu-id="a80b5-107">Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Plusieurs commandes fournisseur (LINQ to XML)](sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="a80b5-107">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="a80b5-108">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="a80b5-108">This example produces the following output:</span></span>  
  
```console  
Results are identical  
PurchaseOrders  
```  
  
## <a name="see-also"></a><span data-ttu-id="a80b5-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a80b5-109">See also</span></span>

- [<span data-ttu-id="a80b5-110">LINQ to XML pour les utilisateurs XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a80b5-110">LINQ to XML for XPath Users (Visual Basic)</span></span>](linq-to-xml-for-xpath-users.md)
