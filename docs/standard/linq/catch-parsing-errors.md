---
title: Comment intercepter les erreurs d’analyse-LINQ to XML
description: Une exception peut se produire dans votre programme C# ou Visual Basic si elle tente d’analyser du code XML non valide avec une méthode telle que XElement. Parse. Vous pouvez écrire le programme pour intercepter ces exceptions et y répondre.
ms.date: 7/20/2015
dev_langs:
- csharp
- vb
ms.assetid: bfb612d4-5605-48ef-8c93-915cf9d5dcfb
ms.openlocfilehash: f7679bd5a0726c669eb47ad6ad66e0f64259264b
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552453"
---
# <a name="how-to-catch-parsing-errors-linq-to-xml"></a><span data-ttu-id="4c000-104">Comment intercepter les erreurs d’analyse (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="4c000-104">How to catch parsing errors (LINQ to XML)</span></span>

<span data-ttu-id="4c000-105">Cet article montre comment détecter du code XML incorrect ou non valide en C# ou Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="4c000-105">This article shows how to detect badly formed or invalid XML in C# or Visual Basic.</span></span>

<span data-ttu-id="4c000-106">LINQ to XML est implémentée à l’aide de <xref:System.Xml.XmlReader> .</span><span class="sxs-lookup"><span data-stu-id="4c000-106">LINQ to XML is implemented using <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="4c000-107">Si un code XML incorrect ou non valide est passé à LINQ to XML, la classe sous-jacente <xref:System.Xml.XmlReader> lèvera une exception.</span><span class="sxs-lookup"><span data-stu-id="4c000-107">If badly formed or invalid XML is passed to LINQ to XML, the underlying <xref:System.Xml.XmlReader> class will throw an exception.</span></span> <span data-ttu-id="4c000-108">Les différentes méthodes qui analysent du code XML, telles que <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType> , n’interceptent pas l’exception, mais l’exception peut être interceptée par votre application.</span><span class="sxs-lookup"><span data-stu-id="4c000-108">The various methods that parse XML, such as <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, don't catch the exception; the exception can then be caught by your application.</span></span>

## <a name="example-parse-invalid-xml"></a><span data-ttu-id="4c000-109">Exemple : analyser du code XML non valide</span><span class="sxs-lookup"><span data-stu-id="4c000-109">Example: Parse invalid XML</span></span>

<span data-ttu-id="4c000-110">Le code suivant tente d’analyser du code XML non valide.</span><span class="sxs-lookup"><span data-stu-id="4c000-110">The following code tries to parse invalid XML.</span></span>

```csharp
try {
    XElement contacts = XElement.Parse(
        @"<Contacts>
            <Contact>
                <Name>Jim Wilson</Name>
            </Contact>
          </Contcts>");

    Console.WriteLine(contacts);
}
catch (System.Xml.XmlException e)
{
    Console.WriteLine(e.Message);
}
```

```vb
Try
    Dim contacts As XElement = XElement.Parse("<Contacts>" & vbCrLf & _
        "    <Contact>" & vbCrLf & _
        "        <Name>Jim Wilson</Name>" & vbCrLf & _
        "    </Contact>" & vbCrLf & _
        "</Contcts>")

    Console.WriteLine(contacts)
Catch e As System.Xml.XmlException
    Console.WriteLine(e.Message)
End Try
```

<span data-ttu-id="4c000-111">En raison de la balise de fin non valide `</Contcts>` , l’exemple lève l’exception suivante :</span><span class="sxs-lookup"><span data-stu-id="4c000-111">Because of the invalid end tag `</Contcts>`, the example throws the following exception:</span></span>

```output
The 'Contacts' start tag on line 1 doesn't match the end tag of 'Contcts'. Line 5, position 13.
```

<span data-ttu-id="4c000-112">Pour plus d’informations sur les exceptions <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType> <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType> levées par les méthodes,, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> et <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> , consultez la <xref:System.Xml.XmlReader> documentation.</span><span class="sxs-lookup"><span data-stu-id="4c000-112">For information about the exceptions that the <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, and <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> methods throw, see the <xref:System.Xml.XmlReader> documentation.</span></span>

## <a name="see-also"></a><span data-ttu-id="4c000-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4c000-113">See also</span></span>

- [<span data-ttu-id="4c000-114">Comment analyser une chaîne</span><span class="sxs-lookup"><span data-stu-id="4c000-114">How to parse a string</span></span>](parse-string.md)
