---
title: 'Procédure : rechercher un élément avec un élément enfant spécifique'
ms.date: 07/20/2015
ms.assetid: b0d0a463-6a85-46c3-8453-ad25b0ecf93c
ms.openlocfilehash: a05504070fe3d2ea5eb6135fd3bf697b131686c6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84405285"
---
# <a name="how-to-find-an-element-with-a-specific-child-element-visual-basic"></a>Comment : Rechercher un élément avec un élément enfant spécifique (Visual Basic)
Cette rubrique montre comment rechercher un élément particulier qui a un élément enfant avec une valeur spécifique.  
  
## <a name="example"></a>Exemple  
 L'exemple recherche l'élément `Test` qui a un élément enfant `CommandLine` avec la valeur « Examp2.EXE ».  
  
 Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Configuration test (LINQ to XML)](sample-xml-file-test-configuration-linq-to-xml.md).  
  
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
  
 Ce code génère la sortie suivante :  
  
```console  
0002  
0006  
```  
  
 Notez que cet exemple utilise la propriété d' [axe enfant XML](../../../language-reference/xml-axis/xml-child-axis-property.md), la [propriété d’axe d’attribut XML](../../../language-reference/xml-axis/xml-attribute-axis-property.md)et la [propriété de valeur XML](../../../language-reference/xml-axis/xml-value-property.md).  
  
## <a name="example"></a>Exemple  
 L'exemple suivant illustre la même requête pour du code XML qui est dans un espace de noms. Pour plus d’informations, consultez [vue d’ensemble des espaces de noms (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).  
  
 Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Configuration test dans un espace de noms](sample-xml-file-test-configuration-in-a-namespace.md).  
  
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
  
 Ce code génère la sortie suivante :  
  
```console  
0002  
0006  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [Requêtes de base (LINQ to XML) (Visual Basic)](basic-queries-linq-to-xml.md)
- [Vue d’ensemble des opérateurs de requête standard (Visual Basic)](standard-query-operators-overview.md)
- [Opérations de projection (Visual Basic)](projection-operations.md)
