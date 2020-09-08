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
# <a name="how-to-catch-parsing-errors-linq-to-xml"></a>Comment intercepter les erreurs d’analyse (LINQ to XML)

Cet article montre comment détecter du code XML incorrect ou non valide en C# ou Visual Basic.

LINQ to XML est implémentée à l’aide de <xref:System.Xml.XmlReader> . Si un code XML incorrect ou non valide est passé à LINQ to XML, la classe sous-jacente <xref:System.Xml.XmlReader> lèvera une exception. Les différentes méthodes qui analysent du code XML, telles que <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType> , n’interceptent pas l’exception, mais l’exception peut être interceptée par votre application.

## <a name="example-parse-invalid-xml"></a>Exemple : analyser du code XML non valide

Le code suivant tente d’analyser du code XML non valide.

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

En raison de la balise de fin non valide `</Contcts>` , l’exemple lève l’exception suivante :

```output
The 'Contacts' start tag on line 1 doesn't match the end tag of 'Contcts'. Line 5, position 13.
```

Pour plus d’informations sur les exceptions <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType> <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType> levées par les méthodes,, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> et <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> , consultez la <xref:System.Xml.XmlReader> documentation.

## <a name="see-also"></a>Voir aussi

- [Comment analyser une chaîne](parse-string.md)
