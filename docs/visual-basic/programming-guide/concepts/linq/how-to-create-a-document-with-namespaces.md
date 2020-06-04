---
title: 'Procédure : créer un document avec des espaces de noms (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: cc5b0d4d-360c-4ada-94fa-2d2916e989be
ms.openlocfilehash: a440c9d810798eb5ebd025a336cbb17fface23b4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414632"
---
# <a name="how-to-create-a-document-with-namespaces-linq-to-xml-visual-basic"></a>Comment : créer un document avec des espaces de noms (LINQ to XML) (Visual Basic)
Cette rubrique montre comment créer un document avec des espaces de noms dans Visual Basic.  
  
 Lorsque vous utilisez des littéraux XML en Visual Basic, les utilisateurs peuvent définir un espace de noms XML global par défaut. Cet espace de noms est l'espace de noms par défaut pour les littéraux XML et les propriétés XML. L'espace de noms XML par défaut peut être défini au niveau projet ou au niveau fichier. S'il est défini au niveau fichier, il remplace l'espace de noms par défaut défini au niveau projet.  
  
 Vous pouvez également définir d'autres espaces de noms et spécifier les préfixes d'espaces de noms de ces espaces de noms.  
  
 Vous définissez les espaces de noms par défaut et les espaces de noms avec préfixe à l'aide du mot clé `Imports`.  
  
 Pour plus d’informations, consultez [Introduction aux littéraux XML dans Visual Basic](introduction-to-xml-literals.md).  
  
 Notez que l'espace de noms XML par défaut s'applique uniquement aux éléments, et non aux attributs. Par défaut, les attributs ne sont jamais dans aucun espace de noms. Toutefois, vous pouvez utiliser un préfixe d'espace de noms pour placer un attribut dans un espace de noms.  
  
## <a name="example"></a>Exemple  
 Cet exemple crée un document qui contient un espace de noms.  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <aw:Root>  
                <aw:Child aw:Att="attvalue"/>  
            </aw:Root>  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
 Cet exemple produit la sortie suivante :  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Child aw:Att="attvalue" />  
</aw:Root>  
```  
  
## <a name="example"></a>Exemple  
 Cet exemple crée un document qui contient deux espaces de noms, dont l'un est l'espace de noms par défaut.  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
Imports <xmlns:fc="www.fourthcoffee.com">  
  
Module Module1  
  
    Sub Main()  
        Dim root As XElement = _  
            <Root>  
                <Child Att="attvalue"/>  
                <fc:Child2>child2 content</fc:Child2>  
            </Root>  
        Console.WriteLine(root)  
    End Sub  
  
End Module  
```  
  
 Cet exemple produit la sortie suivante :  
  
```xml  
<Root xmlns:fc="www.fourthcoffee.com" xmlns="http://www.adventure-works.com">  
  <Child Att="attvalue" />  
  <fc:Child2>child2 content</fc:Child2>  
</Root>  
```  
  
## <a name="example"></a>Exemple  
 L'exemple suivant crée un document qui contient plusieurs espaces de noms, tous deux avec des préfixes d'espaces de noms.  
  
 Lors de la sérialisation d'une arborescence XML, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] émet des déclarations d'espaces de noms selon les besoins, de sorte que chaque élément soit dans son espace de noms désigné.  
  
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
  
End Module  
```  
  
 Cet exemple produit la sortie suivante :  
  
```xml  
<aw:Root xmlns:fc="www.fourthcoffee.com" xmlns:aw="http://www.adventure-works.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des espaces de noms (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md)
