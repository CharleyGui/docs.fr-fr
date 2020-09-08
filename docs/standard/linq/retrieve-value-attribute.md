---
title: Comment récupérer la valeur d’un LINQ to XML d’attributs
description: Récupérez la valeur d’un attribut. Vous pouvez convertir un XAttribute en type souhaité ou utiliser la propriété XAttribute. Value.
ms.date: 07/20/2015
ms.assetid: 817bbe89-5979-4234-bf0c-46f63692ac8c
ms.openlocfilehash: 7af3616c9808cad5dfb52f53c74b21a59da5c954
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553652"
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml"></a>Comment récupérer la valeur d’un attribut (LINQ to XML)

Cet article explique comment obtenir la valeur des attributs. Vous pouvez procéder de deux manières : tout d'abord, vous pouvez convertir un objet <xref:System.Xml.Linq.XAttribute> vers le type souhaité ; l'opérateur de conversion. explicite convertit alors le contenu de l'élément ou attribut vers le type spécifié. En guise d'alternative, vous pouvez utiliser la propriété <xref:System.Xml.Linq.XAttribute.Value%2A>. Toutefois, la conversion est généralement la meilleure approche. Si vous effectuez un cast de l’attribut en un type valeur Nullable, le code est plus simple à écrire lors de la récupération de la valeur d’un attribut qui peut ou non exister. Pour obtenir des exemples de cette technique, consultez [Comment récupérer la valeur d’un élément](retrieve-value-element.md).

## <a name="example-use-a-cast-to-retrieve-the-value-of-an-attribute"></a>Exemple : utiliser un cast pour récupérer la valeur d’un attribut

Pour récupérer la valeur d’un attribut en C#, vous effectuez un cast de l' <xref:System.Xml.Linq.XAttribute> objet vers le type souhaité. Dans Visual Basic, vous pouvez utiliser la propriété d’attribut intégrée pour récupérer la valeur.

```csharp
XElement root = new XElement("Root",
                    new XAttribute("Attr", "abcde")
                );
Console.WriteLine(root);
string str = (string)root.Attribute("Attr");
Console.WriteLine(str);
```

```vb
Dim root As XElement = <Root Attr="abcde"/>
Console.WriteLine(root)
Dim str As String = root.@Attr
Console.WriteLine(str)
```

Cet exemple produit la sortie suivante :

```output
<Root Attr="abcde" />
abcde
```

## <a name="example-use-a-cast-to-retrieve-from-xml-thats-in-a-namespace"></a>Exemple : utiliser un cast pour extraire du code XML qui se trouve dans un espace de noms

L’exemple suivant montre comment récupérer la valeur d’un attribut si l’attribut se trouve dans un espace de noms. Pour plus d’informations, consultez [vue d’ensemble des espaces de noms](namespaces-overview.md).

```csharp
XNamespace aw = "http://www.adventure-works.com";
XElement root = new XElement(aw + "Root",
                    new XAttribute(aw + "Attr", "abcde")
                );
string str = (string)root.Attribute(aw + "Attr");
Console.WriteLine(str);
```

```vb
Imports <xmlns:aw="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim root As XElement = <aw:Root aw:Attr="abcde"/>
        Dim str As String = root.@aw:Attr
        Console.WriteLine(str)
    End Sub
End Module
```

Cet exemple produit la sortie suivante :

```output
abcde
```

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des axes LINQ to XML](linq-xml-axes-overview.md)
