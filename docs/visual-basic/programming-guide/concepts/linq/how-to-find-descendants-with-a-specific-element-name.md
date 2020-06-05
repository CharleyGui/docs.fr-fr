---
title: 'Procédure : rechercher les descendants avec un nom d’élément spécifique'
ms.date: 07/20/2015
ms.assetid: 78915518-0d25-4051-ab55-929779989510
ms.openlocfilehash: 19e0807f3bb7e83061b2076a177107eec126e717
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84405207"
---
# <a name="how-to-find-descendants-with-a-specific-element-name-visual-basic"></a><span data-ttu-id="4245f-102">Comment : Rechercher des descendants avec un nom d’élément spécifique (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4245f-102">How to: Find Descendants with a Specific Element Name (Visual Basic)</span></span>
<span data-ttu-id="4245f-103">Parfois, vous souhaitez rechercher tous les descendants avec un nom particulier.</span><span class="sxs-lookup"><span data-stu-id="4245f-103">Sometimes you want to find all descendants with a particular name.</span></span> <span data-ttu-id="4245f-104">Vous pourriez écrire du code pour itérer au sein de tous les descendants, mais il est plus facile d'utiliser l'axe <xref:System.Xml.Linq.XContainer.Descendants%2A>.</span><span class="sxs-lookup"><span data-stu-id="4245f-104">You could write code to iterate through all of the descendants, but it is easier to use the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4245f-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="4245f-105">Example</span></span>  
 <span data-ttu-id="4245f-106">L'exemple suivant montre comment rechercher des descendants en fonction du nom d'élément.</span><span class="sxs-lookup"><span data-stu-id="4245f-106">The following example shows how to find descendants based on the element name.</span></span>  
  
```vb  
Dim root As XElement = _  
    <root>  
        <para>  
            <r>  
                <t>Some text </t>  
            </r>  
            <n>  
                <r>  
                    <t>that is broken up into </t>  
                </r>  
            </n>  
            <n>  
                <r>  
                    <t>multiple segments.</t>  
                </r>  
            </n>  
        </para>  
    </root>  
  
Dim textSegs As IEnumerable(Of String) = _  
    From seg In root...<t> _  
    Select seg.Value  
  
Dim str As String = textSegs.Aggregate( _  
    New StringBuilder, _  
    Function(sb, i) sb.Append(i), _  
    Function(sb) sb.ToString)  
  
Console.WriteLine(str)  
```  
  
 <span data-ttu-id="4245f-107">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="4245f-107">This code produces the following output:</span></span>  
  
```console  
Some text that is broken up into multiple segments.  
```  
  
## <a name="example"></a><span data-ttu-id="4245f-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="4245f-108">Example</span></span>  
 <span data-ttu-id="4245f-109">L'exemple suivant illustre la même requête pour du code XML qui est dans un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="4245f-109">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="4245f-110">Pour plus d’informations, consultez [vue d’ensemble des espaces de noms (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="4245f-110">For more information, see [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span></span>  
  
```vb  
Imports <xmlns='http://www.adatum.com'>  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <root>  
                <para>  
                    <r>  
                        <t>Some text </t>  
                    </r>  
                    <n>  
                        <r>  
                            <t>that is broken up into </t>  
                        </r>  
                    </n>  
                    <n>  
                        <r>  
                            <t>multiple segments.</t>  
                        </r>  
                    </n>  
                </para>  
            </root>  
  
        Dim textSegs As IEnumerable(Of String) = _  
            From seg In root...<t> _  
            Select seg.Value  
  
        Dim str As String = textSegs.Aggregate( _  
            New StringBuilder, _  
            Function(sb, i) sb.Append(i), _  
            Function(sb) sb.ToString)  
  
        Console.WriteLine(str)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="4245f-111">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="4245f-111">This code produces the following output:</span></span>  
  
```console  
Some text that is broken up into multiple segments.  
```  
  
## <a name="see-also"></a><span data-ttu-id="4245f-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4245f-112">See also</span></span>

- <xref:System.Xml.Linq.XContainer.Descendants%2A>
- [<span data-ttu-id="4245f-113">Requêtes de base (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4245f-113">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](basic-queries-linq-to-xml.md)
