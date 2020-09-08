---
title: Comment analyser un LINQ to XML de chaîne
description: Vous pouvez analyser une chaîne avec XElement. Parse pour créer une arborescence XML en C# et en Visual Basic, et vous pouvez créer une arborescence XML avec des littéraux XML dans Visual Basic.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 81e5686c-9658-42d8-a7e3-b11be0a2c98b
ms.openlocfilehash: f4bd22acbf3b11d801c791cc591d882810450fd4
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552489"
---
# <a name="how-to-parse-a-string-linq-to-xml"></a>Comment analyser une chaîne (LINQ to XML)

Cet article montre comment analyser une chaîne pour créer une arborescence XML en C# et dans Visual Basic.

## <a name="example"></a>Exemple

Le code C# suivant montre comment analyser une chaîne XML :

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

Vous pouvez analyser une chaîne dans Visual Basic de la même manière. Toutefois, il est plus efficace d’utiliser des littéraux XML, comme indiqué dans le code suivant, parce que les littéraux XML ne sont pas affectés par les mêmes pénalités de performances que l’analyse de code XML à partir d’une chaîne.

En utilisant des littéraux XML, vous pouvez simplement copier et coller votre code XML dans votre programme Visual Basic.

> [!NOTE]
> L'analyse de texte ou le chargement d'un document XML à partir d'un fichier texte est moins efficace que la construction fonctionnelle. Si vous initialisez une arborescence XML à partir du code, il faut moins de temps processeur pour utiliser la construction fonctionnelle que pour analyser le texte.

```vb
Dim contacts as XElement = _
    <Contacts>
        <Contact>
            <Name>Patrick Hines</Name>
            <Phone Type="home">206-555-0144</Phone>
            <Phone Type="work">425-555-0145</Phone>
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
            <Phone Type="mobile">206-555-0163</Phone>
            <Address>
            <Street1>123 Main St</Street1>
            <City>Mercer Island</City>
            <State>WA</State>
            <Postal>68042</Postal>
            </Address>
            <NetWorth>11</NetWorth>
        </Contact>
    </Contacts>
```

Le `Contacts` nœud racine a deux `Contact` nœuds. Pour accéder à des données spécifiques dans votre code XML analysé, utilisez la méthode [XElement. Elements ()](xref:System.Xml.Linq.XContainer.Elements) , qui, dans ce cas, retourne les éléments enfants du `Contacts` nœud racine. L’exemple suivant imprime le premier `Contact` nœud sur la console :

```csharp
List<XElement> contactNodes = contacts.Elements("Contact").ToList();
Console.WriteLine(contactNodes[0]);
```

```vb
Dim contactNodes As List(Of XElement) = contacts.Elements("Contact").ToList()
Console.WriteLine(contactNodes(0))
```

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour rechercher un élément avec un attribut spécifique](find-element-specific-attribute.md)
