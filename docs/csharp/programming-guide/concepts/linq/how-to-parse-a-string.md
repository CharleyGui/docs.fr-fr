---
title: Comment analyser une chaîne (C)
ms.date: 07/20/2015
ms.assetid: 81e5686c-9658-42d8-a7e3-b11be0a2c98b
ms.openlocfilehash: 79821eb9e5cd7187ac3c2a93f85eaae45c5c48ac
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75345809"
---
# <a name="how-to-parse-a-string-c"></a>Comment analyser une chaîne (C)

Cette rubrique montre comment analyser une chaîne pour créer une arborescence XML en C#.

## <a name="example"></a> Exemple

Le code Cmd suivant montre comment analyser une chaîne XML :

```csharp
XElement contacts = XElement.Parse(
    @"<Contacts>
        <Contact>
            <Name>Patrick Hines</Name>
            <Phone Type=""home"">206-555-0144</Phone>
            <Phone Type=""work"">425-555-0145</Phone>
            <Address>
            <Street1>123 Main St</Street1>
            <City>Mercer Island</City>
            <State>WA</State>
            <Postal>68042</Postal>
            </Address>
            <NetWorth>10</NetWorth>
        </Contact>
        <Contact>
            <Name>Gretchen Rivas</Name>
            <Phone Type=""mobile"">206-555-0163</Phone>
            <Address>
            <Street1>123 Main St</Street1>
            <City>Mercer Island</City>
            <State>WA</State>
            <Postal>68042</Postal>
            </Address>
            <NetWorth>11</NetWorth>
        </Contact>
    </Contacts>");
Console.WriteLine(contacts);
```

Le `Contacts` nœud `Contact` de racine a deux nœuds. Pour accéder à certaines données spécifiques dans votre XML analysé, utilisez la méthode [XElement.Elements()](xref:System.Xml.Linq.XContainer.Elements) qui, dans ce cas, renvoie les éléments de l’enfant du nœud de racine. `Contacts` L’exemple suivant imprime le premier `Contact` nœud à la console :

```csharp
List<XElement> contactNodes = contacts.Elements("Contact").ToList();
Console.WriteLine(contactNodes[0]);
```

## <a name="see-also"></a>Voir aussi

- [Comment trouver un élément avec un attribut spécifique (C)](how-to-find-an-element-with-a-specific-attribute.md)
