---
title: Utilisation d'espaces de noms globaux (Visual Basic) (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 0a8064d5-e02f-4315-ad48-6deaa443a2f0
ms.openlocfilehash: 9aab6f7175c905fcb3e82829f131f52b3d9368ac
ms.sourcegitcommit: eb9ff6f364cde6f11322e03800d8f5ce302f3c73
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68710382"
---
# <a name="working-with-global-namespaces-visual-basic-linq-to-xml"></a>Utilisation d'espaces de noms globaux (Visual Basic) (LINQ to XML)
L’une des principales fonctionnalités des littéraux XML dans Visual Basic est la possibilité de déclarer des espaces de noms XML à `Imports` l’aide de l’instruction. Grâce à cette fonctionnalité, vous pouvez déclarer un espace de noms XML qui utilise un préfixe ou déclarer un espace de noms XML par défaut.  
  
 Cette fonctionnalité est utile dans deux situations. Tout d'abord, les espaces de noms déclarés dans des littéraux XML ne sont pas reportés dans les expressions incorporées. La déclaration d'espaces de noms globaux réduit la quantité de travail nécessaire pour utiliser des expressions incorporées avec des espaces de noms. En second lieu, vous devez déclarer des espaces de noms globaux afin d'utiliser des espaces de noms avec des propriétés XML.  
  
 Vous pouvez déclarer des espaces de noms globaux au niveau du projet. Vous pouvez également déclarer des espaces de noms globaux au niveau du module, ce qui substitue les espaces de noms globaux au niveau du projet. Pour finir, vous pouvez substituer des espaces de noms globaux dans un littéral XML.  
  
 Lors de l'utilisation de littéraux XML ou de propriétés XML qui se trouvent dans des espaces de noms déclarés globalement, vous pouvez afficher le nom développé des littéraux ou des propriétés XML en plaçant le curseur de souris au-dessus d'eux dans Visual Studio. Le nom développé s’affiche alors dans une info-bulle.  
  
 Vous pouvez obtenir un objet <xref:System.Xml.Linq.XNamespace> qui correspond à un espace de noms global à l'aide de la méthode `GetXmlNamespace`.  
  
## <a name="examples-of-global-namespaces"></a>Exemples d'espaces de noms globaux  
 L'exemple suivant déclare un espace de noms global par défaut à l'aide de l'instruction `Imports`, puis il utilise un littéral XML pour initialiser un objet <xref:System.Xml.Linq.XElement> dans cet espace de noms :  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <Root/>  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
 Cet exemple génère la sortie suivante :  
  
```xml  
<Root xmlns="http://www.adventure-works.com" />  
```  
  
 L'exemple suivant déclare un espace de noms global avec un préfixe, puis il utilise un littéral XML pour initialiser un élément :  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <aw:Root/>  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
 Cet exemple génère la sortie suivante :  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com" />  
```  
  
## <a name="global-namespaces-and-embedded-expressions"></a>Espaces de noms globaux et expressions incorporées  
 Les espaces de noms déclarés dans des littéraux XML ne sont pas reportés dans les expressions incorporées. L'exemple suivant déclare un espace de noms par défaut. Il utilise ensuite une expression incorporée pour l'élément `Child`.  
  
```vb  
Dim root As XElement = _  
    <Root xmlns="http://www.adventure-works.com">  
        <%= <Child/> %>  
    </Root>  
Console.WriteLine(root)  
```  
  
 Cet exemple génère la sortie suivante :  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child xmlns="" />  
</Root>  
```  
  
 Comme vous pouvez le voir, le code XML résultant inclut une déclaration d'un espace de noms par défaut de sorte que l'élément `Child` ne se trouve dans aucun espace de noms.  
  
 Vous pourriez redéclarer l'espace de noms dans l'expression incorporée, comme suit :  
  
```vb  
Dim root As XElement = _  
    <Root xmlns="http://www.adventure-works.com">  
        <%= <Child xmlns="http://www.adventure-works.com"/> %>  
    </Root>  
Console.WriteLine(root)  
```  
  
 Cet exemple génère la sortie suivante :  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child xmlns="http://www.adventure-works.com" />  
</Root>  
```  
  
 Toutefois, ceci peut s'avérer plus laborieux que l'approche de l'espace de noms global par défaut, qui est préférable. Avec l'espace de noms global par défaut, vous pouvez utiliser des littéraux XML sans déclarer d'espaces de noms. Le code XML résultant sera dans l'espace de noms par défaut déclaré globalement.  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <Root>  
                                   <%= <Child/> %>  
                               </Root>  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
 Cet exemple génère la sortie suivante :  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child />  
</Root>  
```  
  
## <a name="using-namespaces-with-xml-properties"></a>Utilisation d'espaces de noms avec des propriétés XML  
 Si vous travaillez avec une arborescence XML qui se trouve dans un espace de noms et que vous utilisez des propriétés XML, vous devez utiliser un espace de noms global de sorte que les propriétés XML se trouvent également dans l’espace de noms correct. L’exemple suivant déclare une arborescence XML dans un espace de noms. Il imprime ensuite le nombre d'éléments `Child`.  
  
```vb  
Dim root As XElement = _  
    <Root xmlns="http://www.adventure-works.com">  
        <Child>content</Child>  
    </Root>  
Console.WriteLine(root.<Child>.Count())  
```  
  
 Cet exemple indique qu'il n'existe aucun élément `Child`. Il génère la sortie suivante :  
  
```  
0  
```  
  
 Si toutefois vous déclarez un espace de noms global par défaut, le littéral XML et la propriété XML sont tous deux dans l'espace de noms global par défaut :  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <Root>  
                <Child>content</Child>  
            </Root>  
        Console.WriteLine(root.<Child>.Count())  
    End Sub  
End Module  
```  
  
 Cet exemple indique qu'il existe un élément `Child`. Il génère la sortie suivante :  
  
```  
1  
```  
  
 Si vous déclarez un espace de noms global qui a un préfixe, vous pouvez utiliser le préfixe à la fois pour les littéraux XML et les propriétés XML :  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <aw:Root>  
                <aw:Child>content</aw:Child>  
            </aw:Root>  
        Console.WriteLine(root.<aw:Child>.Count())  
    End Sub  
End Module  
```  
  
## <a name="xnamespace-and-global-namespaces"></a>XNamespace et espaces de noms globaux  
 Vous pouvez obtenir un objet <xref:System.Xml.Linq.XNamespace> à l'aide de la méthode `GetXmlNamespace` :  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <aw:Root/>  
        Dim xn As XNamespace = GetXmlNamespace(aw)  
        Console.WriteLine(xn)  
    End Sub  
End Module  
```  
  
 Cet exemple génère la sortie suivante :  
  
```  
http://www.adventure-works.com  
```  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des espaces de noms (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md)
