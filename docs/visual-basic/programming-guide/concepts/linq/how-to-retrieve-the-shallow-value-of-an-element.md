---
title: 'Procédure : récupérer la valeur superficielle d’un élément'
ms.date: 07/20/2015
ms.assetid: 730a6670-fb8c-41fc-8a1b-eb97a837e432
ms.openlocfilehash: 24e6b128481f56941f0a61da9766f02813a46e97
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397815"
---
# <a name="how-to-retrieve-the-shallow-value-of-an-element-visual-basic"></a><span data-ttu-id="ab17c-102">Comment : récupérer la valeur superficielle d’un élément (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ab17c-102">How to: Retrieve the Shallow Value of an Element (Visual Basic)</span></span>

<span data-ttu-id="ab17c-103">Cette rubrique montre comment obtenir la valeur superficielle d'un élément.</span><span class="sxs-lookup"><span data-stu-id="ab17c-103">This topic shows how to get the shallow value of an element.</span></span> <span data-ttu-id="ab17c-104">La valeur superficielle est la valeur de l’élément spécifique uniquement, par opposition à la valeur profonde, qui inclut les valeurs de tous les éléments descendants concaténés dans une chaîne unique.</span><span class="sxs-lookup"><span data-stu-id="ab17c-104">The shallow value is the value of the specific element only, as opposed to the deep value, which includes the values of all descendent elements concatenated into a single string.</span></span>

<span data-ttu-id="ab17c-105">Lorsque vous extrayez la valeur d'un élément par le biais d'une conversion ou en utilisant la propriété <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType>, vous extrayez une valeur profonde.</span><span class="sxs-lookup"><span data-stu-id="ab17c-105">When you retrieve an element value by using either casting or the <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> property, you retrieve the deep value.</span></span> <span data-ttu-id="ab17c-106">Pour extraire la valeur superficielle, vous pouvez utiliser la méthode d'extension `ShallowValue`, comme dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="ab17c-106">To retrieve the shallow value, you can use the `ShallowValue` extension method, as shown in the following example.</span></span> <span data-ttu-id="ab17c-107">L'extraction de la valeur superficielle est utile lorsque vous voulez sélectionner des éléments en fonction de leur contenu.</span><span class="sxs-lookup"><span data-stu-id="ab17c-107">Retrieving the shallow value is useful when you want to select elements based on their content.</span></span>

<span data-ttu-id="ab17c-108">L'exemple suivant déclare une méthode d'extension qui extrait la valeur superficielle d'un élément.</span><span class="sxs-lookup"><span data-stu-id="ab17c-108">The following example declares an extension method that retrieves the shallow value of an element.</span></span> <span data-ttu-id="ab17c-109">Il utilise ensuite la méthode d’extension dans une requête pour répertorier tous les éléments qui contiennent une valeur calculée.</span><span class="sxs-lookup"><span data-stu-id="ab17c-109">It then uses the extension method in a query to list all elements that contain a calculated value.</span></span>

## <a name="example"></a><span data-ttu-id="ab17c-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="ab17c-110">Example</span></span>

<span data-ttu-id="ab17c-111">Le fichier texte suivant, Report.xml, est la source pour cet exemple.</span><span class="sxs-lookup"><span data-stu-id="ab17c-111">The following text file, Report.xml, is the source for this example.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<Report>
  <Section>
    <Heading>
      <Column Name="CustomerId">=Customer.CustomerId.Heading</Column>
      <Column Name="Name">=Customer.Name.Heading</Column>
    </Heading>
    <Detail>
      <Column Name="CustomerId">=Customer.CustomerId</Column>
      <Column Name="Name">=Customer.Name</Column>
    </Detail>
  </Section>
</Report>
```

```vb
Module Module1
    <System.Runtime.CompilerServices.Extension()> _
    Public Function ShallowValue(ByVal xe As XElement)
        Return xe _
               .Nodes() _
               .OfType(Of XText)() _
               .Aggregate(New StringBuilder(), _
                              Function(s, c) s.Append(c), _
                              Function(s) s.ToString())
    End Function

    Sub Main()
        Dim root As XElement = XElement.Load("Report.xml")

        Dim query As IEnumerable(Of XElement) = _
            From el In root.Descendants() _
            Where (el.ShallowValue().StartsWith("=")) _
            Select el

        For Each q As XElement In query
            Console.WriteLine("{0}{1}{2}", _
                q.Name.ToString().PadRight(8), _
                q.Attribute("Name").ToString().PadRight(20), _
                q.ShallowValue())
        Next
    End Sub
End Module
```

<span data-ttu-id="ab17c-112">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="ab17c-112">This example produces the following output:</span></span>

```console
Column  Name="CustomerId"   =Customer.CustomerId.Heading
Column  Name="Name"         =Customer.Name.Heading
Column  Name="CustomerId"   =Customer.CustomerId
Column  Name="Name"         =Customer.Name
```

## <a name="see-also"></a><span data-ttu-id="ab17c-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ab17c-113">See also</span></span>

- [<span data-ttu-id="ab17c-114">Axes LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ab17c-114">LINQ to XML Axes (Visual Basic)</span></span>](linq-to-xml-axes.md)
