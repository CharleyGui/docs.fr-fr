---
title: 'Procédure : calculer des valeurs intermédiaires'
ms.date: 07/20/2015
ms.assetid: 933a97b2-dfe7-4f4d-94ad-e6e20df84abd
ms.openlocfilehash: bc38d4848a26a24aeb00581079c9dd31abb7ba1e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84375094"
---
# <a name="how-to-calculate-intermediate-values-visual-basic"></a><span data-ttu-id="c8176-102">Comment : calculer des valeurs intermédiaires (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c8176-102">How to: Calculate Intermediate Values (Visual Basic)</span></span>
<span data-ttu-id="c8176-103">Cet exemple montre comment calculer des valeurs intermédiaires qui peuvent être utilisées dans le tri, le filtrage et la sélection.</span><span class="sxs-lookup"><span data-stu-id="c8176-103">This example shows how to calculate intermediate values that can be used in sorting, filtering, and selecting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c8176-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="c8176-104">Example</span></span>  
 <span data-ttu-id="c8176-105">L'exemple suivant utilise la clause `Let`.</span><span class="sxs-lookup"><span data-stu-id="c8176-105">The following example uses the `Let` clause.</span></span>  
  
 <span data-ttu-id="c8176-106">Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Données numériques (LINQ to XML)](sample-xml-file-numerical-data-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="c8176-106">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="c8176-107">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="c8176-107">This code produces the following output:</span></span>  
  
```console  
55.92  
73.50  
89.99  
198.00  
435.00  
```  
  
## <a name="example"></a><span data-ttu-id="c8176-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="c8176-108">Example</span></span>  
 <span data-ttu-id="c8176-109">L'exemple suivant illustre la même requête pour du code XML qui est dans un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="c8176-109">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="c8176-110">Pour plus d’informations, consultez [vue d’ensemble des espaces de noms (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="c8176-110">For more information, see [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="c8176-111">Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Données numériques dans un espace de noms](sample-xml-file-numerical-data-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="c8176-111">This example uses the following XML document: [Sample XML File: Numerical Data in a Namespace](sample-xml-file-numerical-data-in-a-namespace.md).</span></span>  
  
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
  
 <span data-ttu-id="c8176-112">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="c8176-112">This code produces the following output:</span></span>  
  
```console  
55.92  
73.50  
89.99  
198.00  
435.00  
```  
  
## <a name="see-also"></a><span data-ttu-id="c8176-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c8176-113">See also</span></span>

- [<span data-ttu-id="c8176-114">Requêtes de base (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c8176-114">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](basic-queries-linq-to-xml.md)
