---
title: Comment récupérer la valeur superficielle d’un élément-LINQ to XML
description: Utilisez la `ShallowValue` méthode d’extension pour récupérer la valeur superficielle d’un élément. La valeur superficielle est la valeur de cet élément uniquement ; autrement dit, il n’inclut pas les valeurs des éléments descendants.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 924a2699-72f6-4be1-aaa6-de62f8ec73b9
ms.openlocfilehash: 761ffc07b13ebdc652b75bf96ba5b121c7912fd7
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553664"
---
# <a name="how-to-retrieve-the-shallow-value-of-an-element-linq-to-xml"></a>Comment récupérer la valeur superficielle d’un élément (LINQ to XML)

Cet article montre comment récupérer la valeur superficielle d’un élément, qui est la valeur de cet élément uniquement, à l’exclusion des valeurs des éléments descendants. L'extraction de la valeur superficielle est utile lorsque vous voulez sélectionner des éléments en fonction de leur contenu.

Lorsque vous utilisez le cast ou la <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> propriété pour récupérer une valeur d’élément, la valeur comprend les descendants. Pour récupérer la valeur superficielle, vous pouvez utiliser la `ShallowValue` méthode d’extension, comme illustré dans l’exemple suivant. L’exemple déclare une méthode d’extension qui récupère la valeur superficielle d’un élément. Il utilise ensuite la méthode d’extension dans une requête pour répertorier tous les éléments qui contiennent une valeur calculée.

## <a name="example-use-the-shallowvalue-extension-method-to-retrieve-the-shallow-value-of-an-element"></a>Exemple : utilisation de la `ShallowValue` méthode d’extension pour récupérer la valeur superficielle d’un élément

Les exemples utilisent le fichier texte Report.xml qui contient les éléments suivants :

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

Voici le code de l’exemple :

```csharp
public static class MyExtensions
{
    public static string ShallowValue(this XElement xe)
    {
        return xe
               .Nodes()
               .OfType<XText>()
               .Aggregate(new StringBuilder(),
                          (s, c) => s.Append(c),
                          s => s.ToString());
    }
}

class Program
{
    static void Main(string[] args)
    {
        XElement root = XElement.Load("Report.xml");

        IEnumerable<XElement> query = from el in root.Descendants()
                                      where el.ShallowValue().StartsWith("=")
                                      select el;

        foreach (var q in query)
        {
            Console.WriteLine("{0}{1}{2}",
                q.Name.ToString().PadRight(8),
                q.Attribute("Name").ToString().PadRight(20),
                q.ShallowValue());
        }
    }
}
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

Cet exemple produit la sortie suivante :

```output
Column  Name="CustomerId"   =Customer.CustomerId.Heading
Column  Name="Name"         =Customer.Name.Heading
Column  Name="CustomerId"   =Customer.CustomerId
Column  Name="Name"         =Customer.Name
```

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des axes LINQ to XML](linq-xml-axes-overview.md)
