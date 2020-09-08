---
title: Procédure de création d’une hiérarchie à l’aide de GROUPING-LINQ to XML
description: Consultez un exemple sur la façon dont les données peuvent être regroupées en fonction des valeurs associées dans différents éléments, puis réorganisées pour placer les éléments connexes sous un élément qui reflète la relation.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 0213d59e-5f76-438c-9cab-4bf11f7b971d
ms.openlocfilehash: cd913a2546227154fc48ee4e4ae7d007b7e926a2
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553503"
---
# <a name="how-to-create-hierarchy-using-grouping-linq-to-xml"></a><span data-ttu-id="7ff36-103">Procédure de création d’une hiérarchie à l’aide d’un regroupement (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="7ff36-103">How to create hierarchy using grouping (LINQ to XML)</span></span>

<span data-ttu-id="7ff36-104">Les données peuvent être regroupées en fonction de valeurs associées dans différents éléments, puis réorganisées pour placer les éléments connexes sous un élément qui reflète la relation.</span><span class="sxs-lookup"><span data-stu-id="7ff36-104">Data can be grouped based on related values in different elements, then reordered to place related elements together under an element that reflects the relationship.</span></span> <span data-ttu-id="7ff36-105">Cet article fournit un exemple pour C# et Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="7ff36-105">This article provides an example for C# and Visual Basic.</span></span>

## <a name="example-create-a-new-xml-document-in-which-data-is-grouped-by-category"></a><span data-ttu-id="7ff36-106">Exemple : créer un document XML dans lequel les données sont regroupées par catégorie</span><span class="sxs-lookup"><span data-stu-id="7ff36-106">Example: Create a new XML document in which data is grouped by category</span></span>

<span data-ttu-id="7ff36-107">L’exemple suivant montre comment regrouper des données et générer du code XML basé sur le regroupement.</span><span class="sxs-lookup"><span data-stu-id="7ff36-107">The following example shows how to group data, and generate XML based on the grouping.</span></span> <span data-ttu-id="7ff36-108">Il regroupe tout d’abord les données par égalité de valeur des `<Category>` éléments, puis génère un nouveau fichier XML dans lequel la hiérarchie XML reflète le regroupement.</span><span class="sxs-lookup"><span data-stu-id="7ff36-108">It first groups data by equality of value of the `<Category>` elements, then generates a new XML file in which the XML hierarchy reflects the grouping.</span></span>

<span data-ttu-id="7ff36-109">Cet exemple utilise le document XML [exemple de fichier XML : données numériques](sample-xml-file-numerical-data.md).</span><span class="sxs-lookup"><span data-stu-id="7ff36-109">This example uses XML document [Sample XML file: Numerical data](sample-xml-file-numerical-data.md).</span></span>

```csharp
XElement doc = XElement.Load("Data.xml");
var newData =
    new XElement("Root",
        from data in doc.Elements("Data")
        group data by (string)data.Element("Category") into groupedData
        select new XElement("Group",
            new XAttribute("ID", groupedData.Key),
            from g in groupedData
            select new XElement("Data",
                g.Element("Quantity"),
                g.Element("Price")
            )
        )
    );
Console.WriteLine(newData);
```

```vb
Dim doc As XElement = XElement.Load("Data.xml")
Dim newData As XElement = _
    <Root>
        <%= _
            From data In doc.<Data> _
            Group By category = data.<Category>(0).Value _
            Into groupedData = Group _
            Select <Group ID=<%= category %>>
                       <%= _
                           From g In groupedData _
                           Select _
                           <Data>
                               <%= g.<Quantity>(0) %>
                               <%= g.<Price>(0) %>
                           </Data> _
                       %>
                   </Group> _
        %>
    </Root>
Console.WriteLine(newData)
```

<span data-ttu-id="7ff36-110">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="7ff36-110">This example produces the following output:</span></span>

```xml
<Root>
  <Group ID="A">
    <Data>
      <Quantity>3</Quantity>
      <Price>24.50</Price>
    </Data>
    <Data>
      <Quantity>5</Quantity>
      <Price>4.95</Price>
    </Data>
    <Data>
      <Quantity>3</Quantity>
      <Price>66.00</Price>
    </Data>
    <Data>
      <Quantity>15</Quantity>
      <Price>29.00</Price>
    </Data>
  </Group>
  <Group ID="B">
    <Data>
      <Quantity>1</Quantity>
      <Price>89.99</Price>
    </Data>
    <Data>
      <Quantity>10</Quantity>
      <Price>.99</Price>
    </Data>
    <Data>
      <Quantity>8</Quantity>
      <Price>6.99</Price>
    </Data>
  </Group>
</Root>
```
