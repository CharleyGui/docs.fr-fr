---
title: Guide pratique pour rechercher un attribut du parent (XPath-LINQ to XML) (C#)
description: Découvrez comment rechercher un attribut de l’élément parent. Consultez un exemple de code qui utilise un exemple de document XML.
ms.date: 07/20/2015
ms.assetid: dbef9d89-a5c4-431f-80cc-7a2ebf323f86
ms.openlocfilehash: 03344bb66f617970d9598c91366eb7d69514397a
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303294"
---
# <a name="how-to-find-an-attribute-of-the-parent-xpath-linq-to-xml-c"></a>Guide pratique pour rechercher un attribut du parent (XPath-LINQ to XML) (C#)

Cette rubrique montre comment naviguer jusqu'à l'élément parent et rechercher un attribut de celui-ci.

L’expression XPath est la suivante :

`../@id`

## <a name="example"></a>Exemple

Cet exemple recherche d'abord un élément `Author`. Il recherche ensuite l'attribut `id` de l'élément parent.

Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Livres (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).

```csharp
XDocument books = XDocument.Load("Books.xml");

XElement author =
    books
    .Root
    .Element("Book")
    .Element("Author");

// LINQ to XML query
XAttribute att1 =
    author
    .Parent
    .Attribute("id");

// XPath expression
XAttribute att2 = ((IEnumerable)author.XPathEvaluate("../@id")).Cast<XAttribute>().First();

if (att1 == att2)
    Console.WriteLine("Results are identical");
else
    Console.WriteLine("Results differ");
Console.WriteLine(att1);
```

Cet exemple produit la sortie suivante :

```output
Results are identical
id="bk101"
```
