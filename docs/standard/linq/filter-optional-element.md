---
title: Comment filtrer sur un élément facultatif-LINQ to XML
description: Vous pouvez écrire une recherche pour un élément enfant de telle sorte que la recherche ne déclenche pas d’exception lorsque l’élément n’existe pas.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: f99e2f93-fca5-403f-8a0c-770761d4905a
ms.openlocfilehash: 0d6aa3319efb42b467782c8f09947bdae9657ab5
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552380"
---
# <a name="how-to-filter-on-an-optional-element-linq-to-xml"></a>Comment filtrer sur un élément facultatif (LINQ to XML)

Parfois, vous souhaitez filtrer un élément même si vous n’êtes pas certain qu’il existe dans votre document XML. Vous pouvez écrire votre recherche afin que, même si l’élément particulier ne possède pas l’élément enfant, vous ne déclenchez pas une exception de référence null en le filtrant.

## <a name="example-search-that-doesnt-trigger-an-exception-when-the-target-element-doesnt-exist"></a>Exemple : recherche qui ne déclenche pas d’exception lorsque l’élément cible n’existe pas

Dans l’exemple suivant, l' `Child5` élément n’a pas d' `Type` élément enfant, mais la requête s’exécute toujours correctement. L’exemple utilise la <xref:System.Xml.Linq.Extensions.Elements%2A> méthode d’extension.

```csharp
XElement root = XElement.Parse(@"<Root>
  <Child1>
    <Text>Child One Text</Text>
    <Type Value=""Yes""/>
  </Child1>
  <Child2>
    <Text>Child Two Text</Text>
    <Type Value=""Yes""/>
  </Child2>
  <Child3>
    <Text>Child Three Text</Text>
    <Type Value=""No""/>
  </Child3>
  <Child4>
    <Text>Child Four Text</Text>
    <Type Value=""Yes""/>
  </Child4>
  <Child5>
    <Text>Child Five Text</Text>
  </Child5>
</Root>");
var cList =
    from typeElement in root.Elements().Elements("Type")
    where (string)typeElement.Attribute("Value") == "Yes"
    select (string)typeElement.Parent.Element("Text");
foreach(string str in cList)
    Console.WriteLine(str);
```

```vb
Dim root As XElement = _
    <Root>
        <Child1>
            <Text>Child One Text</Text>
            <Type Value="Yes"/>
        </Child1>
        <Child2>
            <Text>Child Two Text</Text>
            <Type Value="Yes"/>
        </Child2>
        <Child3>
            <Text>Child Three Text</Text>
            <Type Value="No"/>
        </Child3>
        <Child4>
            <Text>Child Four Text</Text>
            <Type Value="Yes"/>
        </Child4>
        <Child5>
            <Text>Child Five Text</Text>
        </Child5>
    </Root>
Dim cList As IEnumerable(Of String) = _
    From typeElement In root.Elements().<Type> _
    Where typeElement.@Value = "Yes" _
    Select typeElement.Parent.<Text>.Value
Dim str As String
For Each str In cList
    Console.WriteLine(str)
Next
```

Cet exemple produit la sortie suivante :

```output
Child One Text
Child Two Text
Child Four Text
```

## <a name="example-same-search-but-for-xml-in-a-namespace"></a>Exemple : même recherche, mais pour XML dans un espace de noms

L’exemple suivant est la même requête, mais pour le code XML qui se trouve dans un espace de noms. Pour plus d’informations, consultez [vue d’ensemble des espaces de noms](namespaces-overview.md).

```csharp
XElement root = XElement.Parse(@"<Root xmlns='http://www.adatum.com'>
  <Child1>
    <Text>Child One Text</Text>
    <Type Value=""Yes""/>
  </Child1>
  <Child2>
    <Text>Child Two Text</Text>
    <Type Value=""Yes""/>
  </Child2>
  <Child3>
    <Text>Child Three Text</Text>
    <Type Value=""No""/>
  </Child3>
  <Child4>
    <Text>Child Four Text</Text>
    <Type Value=""Yes""/>
  </Child4>
  <Child5>
    <Text>Child Five Text</Text>
  </Child5>
</Root>");
XNamespace ad = "http://www.adatum.com";
var cList =
    from typeElement in root.Elements().Elements(ad + "Type")
    where (string)typeElement.Attribute("Value") == "Yes"
    select (string)typeElement.Parent.Element(ad + "Text");
foreach (string str in cList)
    Console.WriteLine(str);
```

```vb
Imports <xmlns='http://www.adatum.com'>

Module Module1
    Sub Main()
        Dim root As XElement = _
            <Root>
                <Child1>
                    <Text>Child One Text</Text>
                    <Type Value="Yes"/>
                </Child1>
                <Child2>
                    <Text>Child Two Text</Text>
                    <Type Value="Yes"/>
                </Child2>
                <Child3>
                    <Text>Child Three Text</Text>
                    <Type Value="No"/>
                </Child3>
                <Child4>
                    <Text>Child Four Text</Text>
                    <Type Value="Yes"/>
                </Child4>
                <Child5>
                    <Text>Child Five Text</Text>
                </Child5>
            </Root>
        Dim cList As IEnumerable(Of String) = _
            From typeElement In root.Elements().<Type> _
            Where typeElement.@Value = "Yes" _
            Select typeElement.Parent.<Text>.Value
        Dim str As String
        For Each str In cList
            Console.WriteLine(str)
        Next
    End Sub
End Module
```

Cet exemple produit la sortie suivante :

```output
Child One Text
Child Two Text
Child Four Text
```

## <a name="see-also"></a>Voir aussi

- <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType>
- [Vue d’ensemble des opérateurs de requête standard (C#)](../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Opérations de projection (C#)](../../csharp/programming-guide/concepts/linq/projection-operations.md)
- [Requêtes de base (LINQ to XML) (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
- [Propriété d'axe enfant XML (Visual Basic)](../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)
- [Propriété d'axe d'attribut XML (Visual Basic)](../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)
- [Propriété de valeur XML](../../visual-basic/language-reference/xml-axis/xml-value-property.md)
- [Vue d’ensemble des opérateurs de requête standard (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Opérations de projection (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/projection-operations.md)
