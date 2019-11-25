---
title: 'Comment : écrire des requêtes sur du code XML dans des espaces de noms'
ms.date: 07/20/2015
ms.assetid: 7d4131b5-3288-414f-b77c-b2edc2a1f465
ms.openlocfilehash: 496cf8daf5136e8aafff000312bbd730a5152e9f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344473"
---
# <a name="how-to-write-queries-on-xml-in-namespaces-visual-basic"></a>How to: Write Queries on XML in Namespaces (Visual Basic)
Pour écrire des requêtes sur du code XML qui est dans un espace de noms, vous devez utiliser des objets <xref:System.Xml.Linq.XName> qui ont l'espace de noms correct.  
  
 Dans Visual Basic, l'approche la plus courante consiste à définir un espace de noms global, puis à utiliser des littéraux XML et des propriétés XML qui emploient l'espace de noms global. Vous pouvez définir un espace de noms par défaut global, auquel cas les éléments dans les littéraux XML seront par défaut dans l'espace de noms. En guise d'alternative, vous pouvez définir un espace de noms global avec un préfixe, puis utiliser le préfixe selon les besoins dans les littéraux XML et les propriétés XML. Comme avec d'autres formes de code XML, les attributs ne sont jamais dans aucun espace de noms par défaut.  
  
 Le premier ensemble d’exemples de cette rubrique montre comment créer une arborescence XML dans un espace de noms par défaut. Le second ensemble illustre la création d’une arborescence XML dans un espace de noms avec un préfixe.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant crée une arborescence XML qui est dans un espace de noms par défaut. Il récupère ensuite une collection d'éléments.  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <Root>  
                <Child>1</Child>  
                <Child>2</Child>  
                <Child>3</Child>  
                <AnotherChild>4</AnotherChild>  
                <AnotherChild>5</AnotherChild>  
                <AnotherChild>6</AnotherChild>  
            </Root>  
        Dim c1 As IEnumerable(Of XElement) = _  
            From el In root.<Child> _  
            Select el  
        For Each el As XElement In c1  
            Console.WriteLine(el.Value)  
        Next  
    End Sub  
End Module  
```  
  
 Cet exemple génère la sortie suivante :  
  
```console  
1  
2  
3  
```  
  
## <a name="example"></a>Exemple  
 En Visual Basic, toutefois, l'écriture de requêtes sur sur arborescence XML qui utilise un espace de noms avec un préfixe diffère de l'écriture sur une arborescence XML dans un espace de noms par défaut. En général, vous devez utiliser l'instruction `Imports` pour importer l'espace de noms avec un préfixe. Vous utilisez ensuite le préfixe dans les noms d’éléments et d’attributs, lors de la construction de l’arborescence XML. Vous utilisez également le préfixe lors de l’interrogation d’une arborescence XML avec des propriétés XML.  
  
 L’exemple suivant crée une arborescence XML qui est dans un espace de noms avec un préfixe. Il récupère ensuite une collection d'éléments.  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <aw:Root>  
                <aw:Child>1</aw:Child>  
                <aw:Child>2</aw:Child>  
                <aw:Child>3</aw:Child>  
                <aw:AnotherChild>4</aw:AnotherChild>  
                <aw:AnotherChild>5</aw:AnotherChild>  
                <aw:AnotherChild>6</aw:AnotherChild>  
            </aw:Root>  
        Dim c1 As IEnumerable(Of XElement) = _  
            From el In root.<aw:Child> _  
            Select el  
        For Each el As XElement In c1  
            Console.WriteLine(CInt(el))  
        Next  
    End Sub  
End Module  
```  
  
 Cet exemple génère la sortie suivante :  
  
```console  
1  
2  
3  
```  
  
## <a name="see-also"></a>Voir aussi

- [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md)
