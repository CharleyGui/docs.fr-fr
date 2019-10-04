---
title: 'Procédure : Écrire une requête qui recherche des éléments en fonction du contexte (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 0b085290-ddc1-4126-aaa0-e4c95a3d9a09
ms.openlocfilehash: a7661ea35ff829875ee4c625c45da533865fea9f
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71835029"
---
# <a name="how-to-write-a-query-that-finds-elements-based-on-context-visual-basic"></a>Procédure : Écrire une requête qui recherche des éléments en fonction du contexte (Visual Basic)
Parfois, vous devez écrire une requête qui sélectionne des éléments en fonction de leur contexte. Vous souhaiterez peut-être filtrer en fonction des éléments frères qui précèdent ou qui suivent. Vous souhaiterez peut-être filtrer en fonction des éléments enfants ou ancêtres.  
  
 Vous pouvez pour cela écrire une requête et utiliser ses résultats dans la clause `where`. Si vous devez tout d'abord tester par rapport à la valeur Null, puis tester la valeur, il est plus pratique de créer la requête dans une clause `let`, puis d'utiliser les résultats dans la clause `where`.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant sélectionne tous les éléments `p` qui sont suivis immédiatement d'un élément `ul`.  
  
```vb  
Dim doc As XElement = _  
    <Root>  
        <p id='1'/>  
        <ul>abc</ul>  
        <Child>  
            <p id='2'/>  
            <notul/>  
            <p id='3'/>  
            <ul>def</ul>  
            <p id='4'/>  
        </Child>  
        <Child>  
            <p id='5'/>  
            <notul/>  
            <p id='6'/>  
            <ul>abc</ul>  
            <p id='7'/>  
        </Child>  
    </Root>  
  
Dim items As IEnumerable(Of XElement) = _  
    From e In doc...<p> _  
    Let z = e.ElementsAfterSelf().FirstOrDefault() _  
    Where z IsNot Nothing AndAlso z.Name.LocalName = "ul" _  
    Select e  
  
For Each e As XElement In items  
    Console.WriteLine("id = {0}", e.@<id>)  
Next  
```  
  
 Ce code génère la sortie suivante :  
  
```console  
id = 1  
id = 3  
id = 6  
```  
  
## <a name="example"></a>Exemple  
 L'exemple suivant illustre la même requête pour du code XML qui est dans un espace de noms. Pour plus d’informations, consultez [vue d’ensemble des espaces de noms (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).  
  
```vb  
Imports <xmlns='http://www.adatum.com'>  
  
Module Module1  
    Sub Main()  
        Dim doc As XElement = _  
            <Root>  
                <p id='1'/>  
                <ul>abc</ul>  
                <Child>  
                    <p id='2'/>  
                    <notul/>  
                    <p id='3'/>  
                    <ul>def</ul>  
                    <p id='4'/>  
                </Child>  
                <Child>  
                    <p id='5'/>  
                    <notul/>  
                    <p id='6'/>  
                    <ul>abc</ul>  
                    <p id='7'/>  
                </Child>  
            </Root>  
  
        Dim items As IEnumerable(Of XElement) = _  
            From e In doc...<p> _  
            Let z = e.ElementsAfterSelf().FirstOrDefault() _  
            Where z IsNot Nothing AndAlso z.Name = GetXmlNamespace().GetName("ul") _  
            Select e  
  
        For Each e As XElement In items  
            Console.WriteLine("id = {0}", e.@<id>)  
        Next  
    End Sub  
End Module  
```  
  
 Ce code génère la sortie suivante :  
  
```console  
id = 1  
id = 3  
id = 6  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Xml.Linq.XElement.Parse%2A>
- <xref:System.Xml.Linq.XContainer.Descendants%2A>
- <xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A>
- <xref:System.Linq.Enumerable.FirstOrDefault%2A>
- [Requêtes de base (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
