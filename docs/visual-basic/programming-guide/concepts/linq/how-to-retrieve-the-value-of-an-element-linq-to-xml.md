---
title: 'Procédure : récupérer la valeur d’un élément (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 76b9b2a5-b3ba-49da-ba74-82100e1bd21c
ms.openlocfilehash: b8ff44416f0fbb590119af7e11714e449185d977
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397789"
---
# <a name="how-to-retrieve-the-value-of-an-element-linq-to-xml-visual-basic"></a>Comment : récupérer la valeur d’un élément (LINQ to XML) (Visual Basic)
Cette rubrique montre comment obtenir la valeur d'éléments. Il existe deux façons de procéder. L'un des moyens consiste à convertir un objet <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XAttribute> vers le type souhaité. L'opérateur de conversion explicite convertit alors le contenu de l'élément ou attribut vers le type spécifié et l'affecte à votre variable. En guise d'alternative, vous pouvez utiliser la propriété <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> ou <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType>.  
  
 Avec Visual Basic, la meilleure approche consiste à utiliser la propriété <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType>.  
  
## <a name="example"></a>Exemple  
 Pour récupérer la valeur d'un élément, il vous suffit de convertir l'objet <xref:System.Xml.Linq.XElement> vers le type souhaité. Vous pouvez toujours convertir un élément en chaîne, comme suit :  
  
```vb  
Dim e As XElement = <StringElement>abcde</StringElement>  
Console.WriteLine(e)  
Console.WriteLine("Value of e:" & e.Value)  
```  
  
 Cet exemple produit la sortie suivante :  
  
```xml  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="example"></a>Exemple  
 Vous pouvez également convertir des éléments vers des types autres que des chaînes. Par exemple, si vous avez un élément qui contient un entier, vous pouvez le convertir en `int`, comme illustré dans le code suivant :  
  
```vb  
Dim e As XElement = <Age>44</Age>  
Console.WriteLine(e)  
Console.WriteLine("Value of e:" & CInt(e))  
```  
  
 Cet exemple produit la sortie suivante :  
  
```xml  
<Age>44</Age>  
Value of e:44  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] fournit des opérateurs de cast explicites pour les types de données suivants : `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID` et `GUID?`.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] fournit les mêmes opérateurs de conversion pour les objets <xref:System.Xml.Linq.XAttribute>.  
  
## <a name="example"></a>Exemple  
 Vous pouvez utiliser la propriété <xref:System.Xml.Linq.XElement.Value%2A> pour récupérer le contenu d'un élément :  
  
```vb  
Dim e As XElement = <StringElement>abcde</StringElement>  
Console.WriteLine(e)  
Console.WriteLine("Value of e:" & e.Value)  
```  
  
 Cet exemple produit la sortie suivante :  
  
```xml  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="example"></a>Exemple  
 Parfois, vous souhaitez récupérer la valeur d'un élément sans être certain qu'il existe. Dans ce cas, lorsque vous assignez l’élément casté à un type Nullable ( `string` ou l’un des types valeur Nullable dans le .NET Framework), si l’élément n’existe pas, la variable assignée a simplement la valeur `Nothing` . Le code suivant montre que lorsqu'il n'est pas certain que l'élément existe, il est plus simple d'utiliser la conversion que la propriété <xref:System.Xml.Linq.XElement.Value%2A>.  
  
```vb  
Dim root As XElement = <Root>  
                           <Child1>child 1 content</Child1>  
                           <Child2>2</Child2>  
                       </Root>  
  
' The following assignments show why it is easier to use  
' casting when the element might or might not exist.  
  
Dim c1 As String = CStr(root.Element("Child1"))  
Console.WriteLine("c1:{0}", IIf(c1 Is Nothing, "element does not exist", c1))  
  
Dim c2 As Nullable(Of Integer) = CType(root.Element("Child2"), Nullable(Of Integer))  
Console.WriteLine("c2:{0}", IIf(Not (c2.HasValue), "element does not exist", c2.ToString()))  
  
Dim c3 As String = CStr(root.Element("Child3"))  
Console.WriteLine("c3:{0}", IIf(c3 Is Nothing, "element does not exist", c3))  
  
Dim c4 As Nullable(Of Integer) = CType(root.Element("Child4"), Nullable(Of Integer))  
Console.WriteLine("c4:{0}", IIf(Not (c4.HasValue), "element does not exist", c4.ToString()))  
  
Console.WriteLine()  
  
' The following assignments show the required code when using  
' the Value property when the attribute might or might not exist.  
' Notice that this is more difficult than the casting approach.  
  
Dim e1 As XElement = root.Element("Child1")  
Dim v1 As String  
If (e1 Is Nothing) Then  
    v1 = Nothing  
Else  
    v1 = e1.Value  
End If  
Console.WriteLine("v1:{0}", IIf(v1 Is Nothing, "element does not exist", v1))  
  
Dim e2 As XElement = root.Element("Child2")  
Dim v2 As Nullable(Of Integer)  
If (e2 Is Nothing) Then  
    v2 = Nothing  
Else  
    v2 = e2.Value  
End If  
Console.WriteLine("v2:{0}", IIf(Not (v2.HasValue), "element does not exist", v2))  
  
Dim e3 As XElement = root.Element("Child3")  
Dim v3 As String  
If (e3 Is Nothing) Then  
    v3 = Nothing  
Else  
    v3 = e3.Value  
End If  
Console.WriteLine("v3:{0}", IIf(v3 Is Nothing, "element does not exist", v3))  
  
Dim e4 As XElement = root.Element("Child4")  
Dim v4 As Nullable(Of Integer)  
If (e4 Is Nothing) Then  
    v4 = Nothing  
Else  
    v4 = e4.Value  
End If  
Console.WriteLine("v4:{0}", IIf(Not (v4.HasValue), "element does not exist", v4))  
```  
  
 Ce code génère la sortie suivante :  
  
```console  
c1:child 1 content  
c2:2  
c3:element does not exist  
c4:element does not exist  
  
v1:child 1 content  
v2:2  
v3:element does not exist  
v4:element does not exist  
```  
  
 En général, le code à écrire est plus simple lors de l'utilisation de la conversion pour récupérer le contenu d'éléments ou d'attributs.  
  
## <a name="see-also"></a>Voir aussi

- [Axes LINQ to XML (Visual Basic)](linq-to-xml-axes.md)
