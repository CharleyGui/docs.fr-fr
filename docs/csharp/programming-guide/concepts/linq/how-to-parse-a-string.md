---
title: 'Procédure : Analyser une chaîne (C#)'
ms.date: 07/20/2015
ms.assetid: 81e5686c-9658-42d8-a7e3-b11be0a2c98b
ms.openlocfilehash: da1c9d2573ac09a9db7f87c619f67bf0b2fb23ba
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834191"
---
# <a name="how-to-parse-a-string-c"></a>Procédure : Analyser une chaîne (C#)

Cette rubrique montre comment analyser une chaîne pour créer une arborescence XML en C#.

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

Le nœud racine `Contacts` a deux nœuds `Contact`. Pour accéder à des données spécifiques dans votre code XML analysé, utilisez la méthode [XElement. Elements ()](xref:System.Xml.Linq.XContainer.Elements) , qui, dans ce cas, retourne les éléments enfants du nœud racine `Contacts`. L’exemple suivant imprime le premier nœud `Contact` sur la console :

```csharp
List<XElement> contactNodes = contacts.Elements("Contact").ToList();
Console.WriteLine(contactNodes[0]);
```
