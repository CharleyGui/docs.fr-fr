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
# <a name="how-to-work-with-dictionaries-using-linq-to-xml-visual-basic"></a><span data-ttu-id="45436-102">Comment : utiliser des dictionnaires à l’aide de LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="45436-102">How to: Work with Dictionaries Using LINQ to XML (Visual Basic)</span></span>
<span data-ttu-id="45436-103">Il est souvent plus pratique de convertir différentes structures de données au format XML et du format XML en d’autres structures de données.</span><span class="sxs-lookup"><span data-stu-id="45436-103">It is often convenient to convert varieties of data structures to XML, and XML back to other data structures.</span></span> <span data-ttu-id="45436-104">Cette rubrique présente une implémentation spécifique de cette approche générale en convertissant un objet <xref:System.Collections.Generic.Dictionary%602> au format XML et inversement.</span><span class="sxs-lookup"><span data-stu-id="45436-104">This topic shows a specific implementation of this general approach by converting a <xref:System.Collections.Generic.Dictionary%602> to XML and back.</span></span>  
  
## <a name="example"></a><span data-ttu-id="45436-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="45436-105">Example</span></span>  
 <span data-ttu-id="45436-106">Cet exemple utilise des littéraux XML et une requête dans une expression incorporée.</span><span class="sxs-lookup"><span data-stu-id="45436-106">This example uses XML literals and a query in an embedded expression.</span></span> <span data-ttu-id="45436-107">La requête projette de nouveaux <xref:System.Xml.Linq.XElement> objets, qui deviennent ensuite le nouveau contenu de l' `Root` <xref:System.Xml.Linq.XElement> objet.</span><span class="sxs-lookup"><span data-stu-id="45436-107">The query projects new <xref:System.Xml.Linq.XElement> objects, which then become the new content for the `Root` <xref:System.Xml.Linq.XElement> object.</span></span>  
  
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
  
 <span data-ttu-id="45436-108">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="45436-108">This code produces the following output:</span></span>  
  
```xml  
          <Root>  
  <Child1>Value1</Child1>  
  <Child2>Value2</Child2>  
  <Child3>Value3</Child3>  
  <Child4>Value4</Child4>  
</Root>  
```  
  
## <a name="example"></a><span data-ttu-id="45436-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="45436-109">Example</span></span>  
 <span data-ttu-id="45436-110">Le code suivant crée un dictionnaire à partir de données XML.</span><span class="sxs-lookup"><span data-stu-id="45436-110">The following code creates a dictionary from XML.</span></span>  
  
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
  
 <span data-ttu-id="45436-111">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="45436-111">This code produces the following output:</span></span>  
  
```console  
Child1:Value1  
Child2:Value2  
Child3:Value3  
Child4:Value4  
```  
  
## <a name="see-also"></a><span data-ttu-id="45436-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="45436-112">See also</span></span>

- [<span data-ttu-id="45436-113">Projections et transformations (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="45436-113">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](projections-and-transformations-linq-to-xml.md)
