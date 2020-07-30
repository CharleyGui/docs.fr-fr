---
title: Comment récupérer la valeur d’un élément (LINQ to XML) (C#)
description: Découvrez comment obtenir la valeur des éléments. Consultez les exemples utilisant la conversion de chaînes, la conversion d’entiers et la propriété Value.
ms.date: 07/20/2015
ms.assetid: 4228c007-07c9-4cf2-a45b-e7074c109581
ms.openlocfilehash: eb750927d74c3068d7ab06caba9835110bd77a09
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301539"
---
# <a name="how-to-retrieve-the-value-of-an-element-linq-to-xml-c"></a><span data-ttu-id="56cfe-104">Comment récupérer la valeur d’un élément (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="56cfe-104">How to retrieve the value of an element (LINQ to XML) (C#)</span></span>

<span data-ttu-id="56cfe-105">Cet article montre comment récupérer la valeur des éléments.</span><span class="sxs-lookup"><span data-stu-id="56cfe-105">This article shows how to get the value of elements.</span></span> <span data-ttu-id="56cfe-106">Il existe deux façons principales d’acquérir la valeur :</span><span class="sxs-lookup"><span data-stu-id="56cfe-106">There are two main ways to get the value:</span></span>

- <span data-ttu-id="56cfe-107">Effectuez un cast d’un <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XAttribute> d’un vers le type souhaité.</span><span class="sxs-lookup"><span data-stu-id="56cfe-107">Cast an <xref:System.Xml.Linq.XElement> or an <xref:System.Xml.Linq.XAttribute> to the desired type.</span></span> <span data-ttu-id="56cfe-108">L'opérateur de conversion explicite convertit alors le contenu de l'élément ou attribut vers le type spécifié et l'affecte à votre variable.</span><span class="sxs-lookup"><span data-stu-id="56cfe-108">The explicit conversion operator then converts the contents of the element or attribute to the specified type and assigns it to your variable.</span></span>

- <span data-ttu-id="56cfe-109">Utilisez les <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType> Propriétés ou.</span><span class="sxs-lookup"><span data-stu-id="56cfe-109">Use the <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> or <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType> properties.</span></span> <span data-ttu-id="56cfe-110">Vous pouvez également définir la valeur à l’aide de ces propriétés.</span><span class="sxs-lookup"><span data-stu-id="56cfe-110">You can also set the value using these properties.</span></span>

<span data-ttu-id="56cfe-111">Avec C#, la conversion est généralement la meilleure approche.</span><span class="sxs-lookup"><span data-stu-id="56cfe-111">With C#, casting is generally the better approach.</span></span> <span data-ttu-id="56cfe-112">Si vous effectuez un cast de l’élément ou de l’attribut en un type valeur Nullable, le code est plus simple à écrire lors de la récupération de la valeur d’un élément (ou attribut) qui peut ou non exister.</span><span class="sxs-lookup"><span data-stu-id="56cfe-112">If you cast the element or attribute to a nullable value type, the code is simpler to write when retrieving the value of an element (or attribute) that might or might not exist.</span></span> <span data-ttu-id="56cfe-113">Le [dernier exemple](#element-might-not-exist-example) de cet article montre que la conversion est plus simple dans le cas où l’élément n’existe peut-être pas.</span><span class="sxs-lookup"><span data-stu-id="56cfe-113">The [last example](#element-might-not-exist-example) in this article demonstrates that casting is simpler in the case where the element might not exist.</span></span> <span data-ttu-id="56cfe-114">Toutefois, vous ne pouvez pas définir le contenu d'un élément par le biais de la conversion, comme vous le pouvez par le biais de la propriété <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="56cfe-114">However, you cannot set the contents of an element through casting, as you can through <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="string-cast-example"></a><span data-ttu-id="56cfe-115">Exemple de conversion de chaîne</span><span class="sxs-lookup"><span data-stu-id="56cfe-115">String cast example</span></span>  
 <span data-ttu-id="56cfe-116">Pour récupérer la valeur d’un élément, effectuez un cast de l' <xref:System.Xml.Linq.XElement> objet vers le type souhaité.</span><span class="sxs-lookup"><span data-stu-id="56cfe-116">To retrieve the value of an element, cast the <xref:System.Xml.Linq.XElement> object to your desired type.</span></span> <span data-ttu-id="56cfe-117">Vous pouvez convertir un élément en chaîne, comme suit :</span><span class="sxs-lookup"><span data-stu-id="56cfe-117">You can cast an element to a string, as follows:</span></span>  
  
```csharp  
XElement e = new XElement("StringElement", "abcde");  
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + (string)e);  
```  
  
 <span data-ttu-id="56cfe-118">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="56cfe-118">This example produces the following output:</span></span>  
  
```output  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="integer-cast-example"></a><span data-ttu-id="56cfe-119">Exemple de cast d’entier</span><span class="sxs-lookup"><span data-stu-id="56cfe-119">Integer cast example</span></span>  
 <span data-ttu-id="56cfe-120">Vous pouvez également convertir des éléments vers des types autres que des chaînes.</span><span class="sxs-lookup"><span data-stu-id="56cfe-120">You can also cast elements to types other than string.</span></span> <span data-ttu-id="56cfe-121">Par exemple, si vous avez un élément qui contient un entier, vous pouvez le convertir en `int`, comme illustré dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="56cfe-121">For example, if you have an element that contains an integer, you can cast it to `int`, as shown in the following code:</span></span>  
  
```csharp  
XElement e = new XElement("Age", "44");  
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + (int)e);  
```  
  
 <span data-ttu-id="56cfe-122">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="56cfe-122">This example produces the following output:</span></span>  
  
```output  
<Age>44</Age>  
Value of e:44  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="56cfe-123">fournit des opérateurs de cast explicites pour les types de données suivants : `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID` et `GUID?`.</span><span class="sxs-lookup"><span data-stu-id="56cfe-123">provides explicit cast operators for the following data types: `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`, and `GUID?`.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="56cfe-124">fournit les mêmes opérateurs de conversion pour les objets <xref:System.Xml.Linq.XAttribute>.</span><span class="sxs-lookup"><span data-stu-id="56cfe-124">provides the same cast operators for <xref:System.Xml.Linq.XAttribute> objects.</span></span>  
  
## <a name="value-property-example"></a><span data-ttu-id="56cfe-125">Exemple de propriété Value</span><span class="sxs-lookup"><span data-stu-id="56cfe-125">Value property example</span></span>  
 <span data-ttu-id="56cfe-126">Vous pouvez utiliser la propriété <xref:System.Xml.Linq.XElement.Value%2A> pour récupérer le contenu d'un élément :</span><span class="sxs-lookup"><span data-stu-id="56cfe-126">You can use the <xref:System.Xml.Linq.XElement.Value%2A> property to retrieve the contents of an element:</span></span>  
  
```csharp  
XElement e = new XElement("StringElement", "abcde");
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + e.Value);  
```  
  
 <span data-ttu-id="56cfe-127">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="56cfe-127">This example produces the following output:</span></span>  
  
```output  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="element-might-not-exist-example"></a><span data-ttu-id="56cfe-128">L’élément n’existe peut-être pas</span><span class="sxs-lookup"><span data-stu-id="56cfe-128">Element might not exist example</span></span>
 <span data-ttu-id="56cfe-129">Parfois, vous tentez de récupérer la valeur d’un élément même si vous n’êtes pas certain qu’il existe.</span><span class="sxs-lookup"><span data-stu-id="56cfe-129">Sometimes you try to retrieve the value of an element even though you're not sure if it exists.</span></span> <span data-ttu-id="56cfe-130">Dans ce cas, lorsque vous assignez l’élément casté à un type de référence Nullable ou à un type de valeur Nullable, si l’élément n’existe pas, la variable assignée a la valeur `null` .</span><span class="sxs-lookup"><span data-stu-id="56cfe-130">In this case, when you assign the casted element to a nullable reference type or nullable value type, if the element does not exist, the assigned variable is set to `null`.</span></span> <span data-ttu-id="56cfe-131">Le code suivant montre que lorsqu'il n'est pas certain que l'élément existe, il est plus simple d'utiliser la conversion que la propriété <xref:System.Xml.Linq.XElement.Value%2A>.</span><span class="sxs-lookup"><span data-stu-id="56cfe-131">The following code shows that when the element might or might not exist, it is easier to use casting than to use the <xref:System.Xml.Linq.XElement.Value%2A> property.</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("Child1", "child 1 content"),  
    new XElement("Child2", "2")  
);  
  
// The following assignments show why it is easier to use  
// casting when the element might or might not exist.  
  
string c1 = (string)root.Element("Child1");  
Console.WriteLine("c1:{0}", c1 == null ? "element does not exist" : c1);  
  
int? c2 = (int?)root.Element("Child2");  
Console.WriteLine("c2:{0}", c2 == null ? "element does not exist" : c2.ToString());  
  
string c3 = (string)root.Element("Child3");  
Console.WriteLine("c3:{0}", c3 == null ? "element does not exist" : c3);  
  
int? c4 = (int?)root.Element("Child4");  
Console.WriteLine("c4:{0}", c4 == null ? "element does not exist" : c4.ToString());  
  
Console.WriteLine();  
  
// The following assignments show the required code when using  
// the Value property when the element might or might not exist.  
// Notice that this is more difficult than the casting approach.  
  
XElement e1 = root.Element("Child1");  
string v1;  
if (e1 == null)  
    v1 = null;  
else  
    v1 = e1.Value;  
Console.WriteLine("v1:{0}", v1 == null ? "element does not exist" : v1);  
  
XElement e2 = root.Element("Child2");  
int? v2;  
if (e2 == null)  
    v2 = null;  
else  
    v2 = Int32.Parse(e2.Value);  
Console.WriteLine("v2:{0}", v2 == null ? "element does not exist" : v2.ToString());  
  
XElement e3 = root.Element("Child3");  
string v3;  
if (e3 == null)  
    v3 = null;  
else  
    v3 = e3.Value;  
Console.WriteLine("v3:{0}", v3 == null ? "element does not exist" : v3);  
  
XElement e4 = root.Element("Child4");  
int? v4;  
if (e4 == null)  
    v4 = null;  
else  
    v4 = Int32.Parse(e4.Value);  
Console.WriteLine("v4:{0}", v4 == null ? "element does not exist" : v4.ToString());  
```  
  
 <span data-ttu-id="56cfe-132">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="56cfe-132">This code produces the following output:</span></span>  
  
```output  
c1:child 1 content  
c2:2  
c3:element does not exist  
c4:element does not exist  
  
v1:child 1 content  
v2:2  
v3:element does not exist  
v4:element does not exist  
```  
  
 <span data-ttu-id="56cfe-133">En général, le code à écrire est plus simple lors de l'utilisation de la conversion pour récupérer le contenu d'éléments ou d'attributs.</span><span class="sxs-lookup"><span data-stu-id="56cfe-133">In general, you can write simpler code when using casting to retrieve the contents of elements and attributes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56cfe-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="56cfe-134">See also</span></span>

- [<span data-ttu-id="56cfe-135">Axes LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="56cfe-135">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
