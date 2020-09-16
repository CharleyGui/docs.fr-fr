---
title: Comment rechercher un élément avec un élément enfant spécifique-LINQ to XML
description: Rechercher un élément dont l’élément enfant a une valeur spécifique
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 00cf5555-374e-4369-bf93-7bd2e7f21db3
ms.openlocfilehash: 2f97f920ce09222858a0a51eb52ffe0d58dba960
ms.sourcegitcommit: aa6d8a90a4f5d8fe0f6e967980b8c98433f05a44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90678637"
---
# <a name="how-to-find-an-element-with-a-specific-child-element-linq-to-xml"></a>Comment rechercher un élément avec un élément enfant spécifique (LINQ to XML)

Cet article montre comment rechercher un élément dont l’élément enfant a une valeur spécifique.

## <a name="example-find-an-element-whose-child-element-has-a-specific-value"></a>Exemple : Rechercher un élément dont l’élément enfant a une valeur spécifique

L’exemple recherche l' `Test` élément dont l' `CommandLine` élément enfant a la valeur « Examp2.EXE ». L’exemple utilise un document XML [exemple de fichier XML : configuration de test](sample-xml-file-test-configuration.md).

```csharp
XElement root = XElement.Load("TestConfig.xml");
IEnumerable<XElement> tests =
    from el in root.Elements("Test")
    where (string)el.Element("CommandLine") == "Examp2.EXE"
    select el;
foreach (XElement el in tests)
    Console.WriteLine((string)el.Attribute("TestId"));
```

```vb
Dim root As XElement = XElement.Load("TestConfig.xml")
Dim tests As IEnumerable(Of XElement) = _
    From el In root.<Test> _
    Where el.<CommandLine>.Value = "Examp2.EXE" _
    Select el
For Each el as XElement In tests
    Console.WriteLine(el.@TestId)
Next
```

Cet exemple produit la sortie suivante :

```output
0002
0006
```

Notez que la version Visual Basic du code utilise la [propriété d’axe enfant XML](../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md), la [propriété d’axe d’attribut XML](../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)et la [propriété de valeur XML](../../visual-basic/language-reference/xml-axis/xml-value-property.md).

## <a name="example-find-when-the-xml-is-in-a-namespace"></a>Exemple : Rechercher le moment où le XML se trouve dans un espace de noms

L’exemple suivant fait la même chose que le précédent, mais pour le code XML qui se trouve dans un espace de noms. L’exemple utilise un document XML [exemple de fichier XML : configuration de test dans un espace de noms](sample-xml-file-test-configuration-namespace.md).

Pour plus d’informations, consultez [vue d’ensemble des espaces de noms](namespaces-overview.md).

```csharp
XElement root = XElement.Load("TestConfigInNamespace.xml");
XNamespace ad = "http://www.adatum.com";
IEnumerable<XElement> tests =
    from el in root.Elements(ad + "Test")
    where (string)el.Element(ad + "CommandLine") == "Examp2.EXE"
    select el;
foreach (XElement el in tests)
    Console.WriteLine((string)el.Attribute("TestId"));
```

```vb
Imports <xmlns='http://www.adatum.com'>

Module Module1
    Sub Main()
        Dim root As XElement = XElement.Load("TestConfigInNamespace.xml")
        Dim tests As IEnumerable(Of XElement) = _
            From el In root.<Test> _
            Where el.<CommandLine>.Value = "Examp2.EXE" _
            Select el
        For Each el As XElement In tests
            Console.WriteLine(el.@TestId)
        Next
    End Sub
End Module
```

Cet exemple produit la sortie suivante :

```output
0002
0006
```

## <a name="see-also"></a>Voir aussi

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [Vue d'ensemble des opérateurs de requête standard](../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Opérations de projection](../../csharp/programming-guide/concepts/linq/projection-operations.md)
