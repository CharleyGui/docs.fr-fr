---
title: Comment créer une hiérarchie à l’aide d’un regroupement (C#)
description: Apprenez à regrouper des données, puis générez un nouveau fichier XML dans lequel la hiérarchie XML reflète le regroupement.
ms.date: 07/20/2015
ms.assetid: 0213d59e-5f76-438c-9cab-4bf11f7b971d
ms.openlocfilehash: d9470ce9b9b7702cf9b835cb2143b6a36f3a254f
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302917"
---
# <a name="how-to-create-hierarchy-using-grouping-c"></a><span data-ttu-id="1f986-103">Comment créer une hiérarchie à l’aide d’un regroupement (C#)</span><span class="sxs-lookup"><span data-stu-id="1f986-103">How to create hierarchy using grouping (C#)</span></span>
<span data-ttu-id="1f986-104">Cet exemple montre comment grouper des données, puis générer du code XML basé sur le regroupement.</span><span class="sxs-lookup"><span data-stu-id="1f986-104">This example shows how to group data, and then generate XML based on the grouping.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1f986-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="1f986-105">Example</span></span>  
 <span data-ttu-id="1f986-106">Cet exemple groupe tout d'abord les données par catégorie, puis il génère un nouveau fichier XML dans lequel la hiérarchie XML reflète le regroupement.</span><span class="sxs-lookup"><span data-stu-id="1f986-106">This example first groups data by a category, then generates a new XML file in which the XML hierarchy reflects the grouping.</span></span>  
  
 <span data-ttu-id="1f986-107">Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Données numériques (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="1f986-107">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="1f986-108">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="1f986-108">This example produces the following output:</span></span>  
  
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
