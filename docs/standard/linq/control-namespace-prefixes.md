---
title: Comment contrôler les préfixes d’espaces de noms-LINQ to XML
description: Vous pouvez contrôler les préfixes d’espaces de noms lors de la sérialisation d’une arborescence XML en C# et Visual Basic. Pour ce faire, insérez des attributs qui déclarent des espaces de noms.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 64de5186-b81a-4ddd-8327-8693df59a01b
ms.openlocfilehash: 07efc23c11cd0dc0d281968911cf24d6ecbc76a2
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552452"
---
# <a name="how-to-control-namespace-prefixes-linq-to-xml"></a>Guide pratique pour contrôler les préfixes d’espace de noms (LINQ to XML)

Cet article explique comment contrôler les préfixes d’espaces de noms lors de la sérialisation d’une arborescence XML en C# et Visual Basic.

Dans de nombreux cas, il n’est pas nécessaire de contrôler les préfixes d’espaces de noms. Toutefois, certains outils de programmation XML en ont besoin. Par exemple, vous pouvez manipuler une feuille de style XSLT ou un document XAML qui contient des expressions XPath incorporées qui font référence à des préfixes d’espaces de noms spécifiques. Dans ce cas, il est important que le document soit sérialisé avec ces préfixes. Il s’agit d’une raison courante de contrôler les préfixes d’espaces de noms.

Une autre raison est que vous souhaitez que les utilisateurs modifient le document XML manuellement et que vous souhaitiez créer des préfixes d’espaces de noms qui sont pratiques pour l’utilisateur à taper. Par exemple, vous pourriez générer un document XSD. Les conventions applicables aux schémas suggèrent que vous utilisiez `xs` ou `xsd` comme préfixe de l'espace de noms de schéma.

Pour contrôler les préfixes d'espaces de noms, vous devez insérer des attributs qui déclarent des espaces de noms. Si vous déclarez les espaces de noms avec des préfixes spécifiques, LINQ to XML tentera d’honorer les préfixes d’espace de noms lors de la sérialisation.

Pour créer un attribut qui déclare un espace de noms avec un préfixe, vous devez créer un attribut où l'espace de noms du nom de l'attribut est <xref:System.Xml.Linq.XNamespace.Xmlns%2A> et le nom de l'attribut est le préfixe d'espace de noms. La valeur de l'attribut est l'URI de l'espace de noms.

## <a name="example-create-two-namespaces-that-have-prefixes"></a>Exemple : créer deux espaces de noms qui ont des préfixes

Cet exemple déclare deux espaces de noms. Elle spécifie le préfixe `aw` de l' `http://www.adventure-works.com` espace de noms et le préfixe `fc` de l' `www.fourthcoffee.com` espace de noms.

```csharp
XNamespace aw = "http://www.adventure-works.com";
XNamespace fc = "www.fourthcoffee.com";
XElement root = new XElement(aw + "Root",
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com"),
    new XAttribute(XNamespace.Xmlns + "fc", "www.fourthcoffee.com"),
    new XElement(fc + "Child",
        new XElement(aw + "DifferentChild", "other content")
    ),
    new XElement(aw + "Child2", "c2 content"),
    new XElement(fc + "Child3", "c3 content")
);
Console.WriteLine(root);
```

```vb
Imports <xmlns:aw="http://www.adventure-works.com">
Imports <xmlns:fc="www.fourthcoffee.com">

Module Module1

    Sub Main()
        Dim root As XElement = _
            <aw:Root>
                <fc:Child>
                    <aw:DifferentChild>other content</aw:DifferentChild>
                </fc:Child>
                <aw:Child2>c2 content</aw:Child2>
                <fc:Child3>c3 content</fc:Child3>
            </aw:Root>
        Console.WriteLine(root)
    End Sub

This example produces the following output:

```xml
<aw:Root xmlns:aw="http://www.adventure-works.com" xmlns:fc="www.fourthcoffee.com">
  <fc:Child>
    <aw:DifferentChild>other content</aw:DifferentChild>
  </fc:Child>
  <aw:Child2>c2 content</aw:Child2>
  <fc:Child3>c3 content</fc:Child3>
</aw:Root>
```

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des espaces de noms](namespaces-overview.md)
