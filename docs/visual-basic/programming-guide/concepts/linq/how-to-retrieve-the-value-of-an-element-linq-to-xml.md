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
# <a name="how-to-retrieve-the-value-of-an-element-linq-to-xml-visual-basic"></a><span data-ttu-id="96e63-102">Comment : récupérer la valeur d’un élément (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="96e63-102">How to: Retrieve the Value of an Element (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="96e63-103">Cette rubrique montre comment obtenir la valeur d'éléments.</span><span class="sxs-lookup"><span data-stu-id="96e63-103">This topic shows how to get the value of elements.</span></span> <span data-ttu-id="96e63-104">Il existe deux façons de procéder.</span><span class="sxs-lookup"><span data-stu-id="96e63-104">There are two main ways to do this.</span></span> <span data-ttu-id="96e63-105">L'un des moyens consiste à convertir un objet <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XAttribute> vers le type souhaité.</span><span class="sxs-lookup"><span data-stu-id="96e63-105">One way is to cast an <xref:System.Xml.Linq.XElement> or an <xref:System.Xml.Linq.XAttribute> to the desired type.</span></span> <span data-ttu-id="96e63-106">L'opérateur de conversion explicite convertit alors le contenu de l'élément ou attribut vers le type spécifié et l'affecte à votre variable.</span><span class="sxs-lookup"><span data-stu-id="96e63-106">The explicit conversion operator then converts the contents of the element or attribute to the specified type and assigns it to your variable.</span></span> <span data-ttu-id="96e63-107">En guise d'alternative, vous pouvez utiliser la propriété <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> ou <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="96e63-107">Alternatively, you can use the <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> property or the <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="96e63-108">Avec Visual Basic, la meilleure approche consiste à utiliser la propriété <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="96e63-108">With Visual Basic, the best approach is to use the <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="96e63-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="96e63-109">Example</span></span>  
 <span data-ttu-id="96e63-110">Pour récupérer la valeur d'un élément, il vous suffit de convertir l'objet <xref:System.Xml.Linq.XElement> vers le type souhaité.</span><span class="sxs-lookup"><span data-stu-id="96e63-110">To retrieve the value of an element, you just cast the <xref:System.Xml.Linq.XElement> object to your desired type.</span></span> <span data-ttu-id="96e63-111">Vous pouvez toujours convertir un élément en chaîne, comme suit :</span><span class="sxs-lookup"><span data-stu-id="96e63-111">You can always cast an element to a string, as follows:</span></span>  
  
```vb  
Dim e As XElement = <StringElement>abcde</StringElement>  
Console.WriteLine(e)  
Console.WriteLine("Value of e:" & e.Value)  
```  
  
 <span data-ttu-id="96e63-112">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="96e63-112">This example produces the following output:</span></span>  
  
```xml  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="example"></a><span data-ttu-id="96e63-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="96e63-113">Example</span></span>  
 <span data-ttu-id="96e63-114">Vous pouvez également convertir des éléments vers des types autres que des chaînes.</span><span class="sxs-lookup"><span data-stu-id="96e63-114">You can also cast elements to types other than string.</span></span> <span data-ttu-id="96e63-115">Par exemple, si vous avez un élément qui contient un entier, vous pouvez le convertir en `int`, comme illustré dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="96e63-115">For example, if you have an element that contains an integer, you can cast it to `int`, as shown in the following code:</span></span>  
  
```vb  
Dim e As XElement = <Age>44</Age>  
Console.WriteLine(e)  
Console.WriteLine("Value of e:" & CInt(e))  
```  
  
 <span data-ttu-id="96e63-116">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="96e63-116">This example produces the following output:</span></span>  
  
```xml  
<Age>44</Age>  
Value of e:44  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="96e63-117">fournit des opérateurs de cast explicites pour les types de données suivants : `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID` et `GUID?`.</span><span class="sxs-lookup"><span data-stu-id="96e63-117">provides explicit cast operators for the following data types: `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`, and `GUID?`.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="96e63-118">fournit les mêmes opérateurs de conversion pour les objets <xref:System.Xml.Linq.XAttribute>.</span><span class="sxs-lookup"><span data-stu-id="96e63-118">provides the same cast operators for <xref:System.Xml.Linq.XAttribute> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="96e63-119">Exemple</span><span class="sxs-lookup"><span data-stu-id="96e63-119">Example</span></span>  
 <span data-ttu-id="96e63-120">Vous pouvez utiliser la propriété <xref:System.Xml.Linq.XElement.Value%2A> pour récupérer le contenu d'un élément :</span><span class="sxs-lookup"><span data-stu-id="96e63-120">You can use the <xref:System.Xml.Linq.XElement.Value%2A> property to retrieve the contents of an element:</span></span>  
  
```vb  
Dim e As XElement = <StringElement>abcde</StringElement>  
Console.WriteLine(e)  
Console.WriteLine("Value of e:" & e.Value)  
```  
  
 <span data-ttu-id="96e63-121">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="96e63-121">This example produces the following output:</span></span>  
  
```xml  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="example"></a><span data-ttu-id="96e63-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="96e63-122">Example</span></span>  
 <span data-ttu-id="96e63-123">Parfois, vous souhaitez récupérer la valeur d'un élément sans être certain qu'il existe.</span><span class="sxs-lookup"><span data-stu-id="96e63-123">Sometimes you try to retrieve the value of an element even though you are not sure it exists.</span></span> <span data-ttu-id="96e63-124">Dans ce cas, lorsque vous assignez l’élément casté à un type Nullable ( `string` ou l’un des types valeur Nullable dans le .NET Framework), si l’élément n’existe pas, la variable assignée a simplement la valeur `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="96e63-124">In this case, when you assign the casted element to a nullable type (either `string` or one of the nullable value types in the .NET Framework), if the element does not exist the assigned variable is just set to `Nothing`.</span></span> <span data-ttu-id="96e63-125">Le code suivant montre que lorsqu'il n'est pas certain que l'élément existe, il est plus simple d'utiliser la conversion que la propriété <xref:System.Xml.Linq.XElement.Value%2A>.</span><span class="sxs-lookup"><span data-stu-id="96e63-125">The following code shows that when the element might or might not exist, it is easier to use casting than to use the <xref:System.Xml.Linq.XElement.Value%2A> property.</span></span>  
  
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
  
 <span data-ttu-id="96e63-126">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="96e63-126">This code produces the following output:</span></span>  
  
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
  
 <span data-ttu-id="96e63-127">En général, le code à écrire est plus simple lors de l'utilisation de la conversion pour récupérer le contenu d'éléments ou d'attributs.</span><span class="sxs-lookup"><span data-stu-id="96e63-127">In general, you can write simpler code when using casting to retrieve the contents of elements and attributes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96e63-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="96e63-128">See also</span></span>

- [<span data-ttu-id="96e63-129">Axes LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="96e63-129">LINQ to XML Axes (Visual Basic)</span></span>](linq-to-xml-axes.md)
