---
title: 'Procédure : utiliser des dictionnaires à l’aide de LINQ to XML'
ms.date: 07/20/2015
ms.assetid: 6cb3f969-1986-414a-b850-87418712edea
ms.openlocfilehash: 14c9c35693f323292849f01af79ae81f92921611
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397672"
---
# <a name="how-to-work-with-dictionaries-using-linq-to-xml-visual-basic"></a>Comment : utiliser des dictionnaires à l’aide de LINQ to XML (Visual Basic)
Il est souvent plus pratique de convertir différentes structures de données au format XML et du format XML en d’autres structures de données. Cette rubrique présente une implémentation spécifique de cette approche générale en convertissant un objet <xref:System.Collections.Generic.Dictionary%602> au format XML et inversement.  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise des littéraux XML et une requête dans une expression incorporée. La requête projette de nouveaux <xref:System.Xml.Linq.XElement> objets, qui deviennent ensuite le nouveau contenu de l' `Root` <xref:System.Xml.Linq.XElement> objet.  
  
```vb  
Dim dict As Dictionary(Of String, String) = New Dictionary(Of String, String)()  
dict.Add("Child1", "Value1")  
dict.Add("Child2", "Value2")  
dict.Add("Child3", "Value3")  
dict.Add("Child4", "Value4")  
Dim root As XElement = _  
    <Root>  
        <%= From keyValue In dict _  
            Select New XElement(keyValue.Key, keyValue.Value) %>  
    </Root>  
Console.WriteLine(root)  
```  
  
 Ce code génère la sortie suivante :  
  
```xml  
          <Root>  
  <Child1>Value1</Child1>  
  <Child2>Value2</Child2>  
  <Child3>Value3</Child3>  
  <Child4>Value4</Child4>  
</Root>  
```  
  
## <a name="example"></a>Exemple  
 Le code suivant crée un dictionnaire à partir de données XML.  
  
```vb  
Dim root As XElement = _  
        <Root>  
            <Child1>Value1</Child1>  
            <Child2>Value2</Child2>  
            <Child3>Value3</Child3>  
            <Child4>Value4</Child4>  
        </Root>  
  
Dim dict As Dictionary(Of String, String) = New Dictionary(Of String, String)  
For Each el As XElement In root.Elements  
    dict.Add(el.Name.LocalName, el.Value)  
Next  
For Each str As String In dict.Keys  
    Console.WriteLine("{0}:{1}", str, dict(str))  
Next  
```  
  
 Ce code génère la sortie suivante :  
  
```console  
Child1:Value1  
Child2:Value2  
Child3:Value3  
Child4:Value4  
```  
  
## <a name="see-also"></a>Voir aussi

- [Projections et transformations (LINQ to XML) (Visual Basic)](projections-and-transformations-linq-to-xml.md)
