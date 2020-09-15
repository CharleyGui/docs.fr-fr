---
title: Génération de code XML à partir de fichiers CSV-LINQ to XML
description: Découvrez comment créer du code XML à partir d’un fichier de valeurs séparées par des virgules (CSV) en C# ou Visual Basic.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 57b9ccde-f983-4a21-ae61-70ecede30307
ms.openlocfilehash: 1d1fd5b9348be8aae40e11b7b15173d5c169847b
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552424"
---
# <a name="how-to-generate-xml-from-csv-files-linq-to-xml"></a><span data-ttu-id="d073a-103">Génération de code XML à partir de fichiers CSV (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="d073a-103">How to generate XML from CSV files (LINQ to XML)</span></span>

<span data-ttu-id="d073a-104">Vous pouvez utiliser LINQ to XML en C# ou Visual Basic pour créer du code XML à partir d’un fichier de valeurs séparées par des virgules (CSV).</span><span class="sxs-lookup"><span data-stu-id="d073a-104">You can use LINQ to XML in C# or Visual Basic to create XML from a comma-separated values (CSV) file.</span></span>

## <a name="example-generate-xml-from-a-csv-file"></a><span data-ttu-id="d073a-105">Exemple : générer du code XML à partir d’un fichier CSV</span><span class="sxs-lookup"><span data-stu-id="d073a-105">Example: Generate XML from a CSV file</span></span>

<span data-ttu-id="d073a-106">Cet exemple exécute une requête LINQ sur un tableau de chaînes, puis utilise la `let` clause pour fractionner chaque chaîne en un tableau de champs.</span><span class="sxs-lookup"><span data-stu-id="d073a-106">This example does a LINQ query on an array of strings, then uses the `let` clause to split each string into an array of fields.</span></span>

```csharp
// Create the text file.
string csvString = @"GREAL,Great Lakes Food Market,Howard Snyder,Marketing Manager,(503) 555-7555,2732 Baker Blvd.,Eugene,OR,97403,USA
HUNGC,Hungry Coyote Import Store,Yoshi Latimer,Sales Representative,(503) 555-6874,City Center Plaza 516 Main St.,Elgin,OR,97827,USA
LAZYK,Lazy K Kountry Store,John Steel,Marketing Manager,(509) 555-7969,12 Orchestra Terrace,Walla Walla,WA,99362,USA
LETSS,Let's Stop N Shop,Jaime Yorres,Owner,(415) 555-5938,87 Polk St. Suite 5,San Francisco,CA,94117,USA";
File.WriteAllText("cust.csv", csvString);

// Read into an array of strings.
string[] source = File.ReadAllLines("cust.csv");
XElement cust = new XElement("Root",
    from str in source
    let fields = str.Split(',')
    select new XElement("Customer",
        new XAttribute("CustomerID", fields[0]),
        new XElement("CompanyName", fields[1]),
        new XElement("ContactName", fields[2]),
        new XElement("ContactTitle", fields[3]),
        new XElement("Phone", fields[4]),
        new XElement("FullAddress",
            new XElement("Address", fields[5]),
            new XElement("City", fields[6]),
            new XElement("Region", fields[7]),
            new XElement("PostalCode", fields[8]),
            new XElement("Country", fields[9])
        )
    )
);
Console.WriteLine(cust);
```

```vb
' Create the text file.
Dim csvString As String = "GREAL,Great Lakes Food Market,Howard Snyder,Marketing Manager,(503) 555-7555,2732 Baker Blvd.,Eugene,OR,97403,USA" & vbCrLf & _
    "HUNGC,Hungry Coyote Import Store,Yoshi Latimer,Sales Representative,(503) 555-6874,City Center Plaza 516 Main St.,Elgin,OR,97827,USA" & vbCrLf & _
    "LAZYK,Lazy K Kountry Store,John Steel,Marketing Manager,(509) 555-7969,12 Orchestra Terrace,Walla Walla,WA,99362,USA" & vbCrLf & _
    "LETSS,Let's Stop N Shop,Jaime Yorres,Owner,(415) 555-5938,87 Polk St. Suite 5,San Francisco,CA,94117,USA"
File.WriteAllText("cust.csv", csvString)

' Read into an array of strings.
Dim source As String() = File.ReadAllLines("cust.csv")
Dim cust As XElement = _
    <Root>
        <%= From strs In source _
            Let fields = Split(strs, ",") _
            Select _
            <Customer CustomerID=<%= fields(0) %>>
                <CompanyName><%= fields(1) %></CompanyName>
                <ContactName><%= fields(2) %></ContactName>
                <ContactTitle><%= fields(3) %></ContactTitle>
                <Phone><%= fields(4) %></Phone>
                <FullAddress>
                    <Address><%= fields(5) %></Address>
                    <City><%= fields(6) %></City>
                    <Region><%= fields(7) %></Region>
                    <PostalCode><%= fields(8) %></PostalCode>
                    <Country><%= fields(9) %></Country>
                </FullAddress>
            </Customer> _
        %>
    </Root>
Console.WriteLine(cust)
```

<span data-ttu-id="d073a-107">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="d073a-107">This example produces the following output:</span></span>

```xml
<Root>
  <Customer CustomerID="GREAL">
    <CompanyName>Great Lakes Food Market</CompanyName>
    <ContactName>Howard Snyder</ContactName>
    <ContactTitle>Marketing Manager</ContactTitle>
    <Phone>(503) 555-7555</Phone>
    <FullAddress>
      <Address>2732 Baker Blvd.</Address>
      <City>Eugene</City>
      <Region>OR</Region>
      <PostalCode>97403</PostalCode>
      <Country>USA</Country>
    </FullAddress>
  </Customer>
  <Customer CustomerID="HUNGC">
    <CompanyName>Hungry Coyote Import Store</CompanyName>
    <ContactName>Yoshi Latimer</ContactName>
    <ContactTitle>Sales Representative</ContactTitle>
    <Phone>(503) 555-6874</Phone>
    <FullAddress>
      <Address>City Center Plaza 516 Main St.</Address>
      <City>Elgin</City>
      <Region>OR</Region>
      <PostalCode>97827</PostalCode>
      <Country>USA</Country>
    </FullAddress>
  </Customer>
  <Customer CustomerID="LAZYK">
    <CompanyName>Lazy K Kountry Store</CompanyName>
    <ContactName>John Steel</ContactName>
    <ContactTitle>Marketing Manager</ContactTitle>
    <Phone>(509) 555-7969</Phone>
    <FullAddress>
      <Address>12 Orchestra Terrace</Address>
      <City>Walla Walla</City>
      <Region>WA</Region>
      <PostalCode>99362</PostalCode>
      <Country>USA</Country>
    </FullAddress>
  </Customer>
  <Customer CustomerID="LETSS">
    <CompanyName>Let's Stop N Shop</CompanyName>
    <ContactName>Jaime Yorres</ContactName>
    <ContactTitle>Owner</ContactTitle>
    <Phone>(415) 555-5938</Phone>
    <FullAddress>
      <Address>87 Polk St. Suite 5</Address>
      <City>San Francisco</City>
      <Region>CA</Region>
      <PostalCode>94117</PostalCode>
      <Country>USA</Country>
    </FullAddress>
  </Customer>
</Root>
```