---
title: Comment récupérer la valeur d’un élément (LINQ à XML) (C)
ms.date: 07/20/2015
ms.assetid: 4228c007-07c9-4cf2-a45b-e7074c109581
ms.openlocfilehash: c4bb78e937fe0de08242923cdd7cd638abf571c7
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805836"
---
# <a name="how-to-retrieve-the-value-of-an-element-linq-to-xml-c"></a><span data-ttu-id="58c5c-102">Comment récupérer la valeur d’un élément (LINQ à XML) (C)</span><span class="sxs-lookup"><span data-stu-id="58c5c-102">How to retrieve the value of an element (LINQ to XML) (C#)</span></span>

<span data-ttu-id="58c5c-103">Cet article montre comment obtenir la valeur des éléments.</span><span class="sxs-lookup"><span data-stu-id="58c5c-103">This article shows how to get the value of elements.</span></span> <span data-ttu-id="58c5c-104">Il y a deux façons principales d’obtenir la valeur :</span><span class="sxs-lookup"><span data-stu-id="58c5c-104">There are two main ways to get the value:</span></span>

- <span data-ttu-id="58c5c-105">Lancer <xref:System.Xml.Linq.XElement> un <xref:System.Xml.Linq.XAttribute> ou un au type désiré.</span><span class="sxs-lookup"><span data-stu-id="58c5c-105">Cast an <xref:System.Xml.Linq.XElement> or an <xref:System.Xml.Linq.XAttribute> to the desired type.</span></span> <span data-ttu-id="58c5c-106">L'opérateur de conversion explicite convertit alors le contenu de l'élément ou attribut vers le type spécifié et l'affecte à votre variable.</span><span class="sxs-lookup"><span data-stu-id="58c5c-106">The explicit conversion operator then converts the contents of the element or attribute to the specified type and assigns it to your variable.</span></span>

- <span data-ttu-id="58c5c-107">Utilisez <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> les <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType> propriétés ou les propriétés.</span><span class="sxs-lookup"><span data-stu-id="58c5c-107">Use the <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> or <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType> properties.</span></span> <span data-ttu-id="58c5c-108">Vous pouvez également définir la valeur en utilisant ces propriétés.</span><span class="sxs-lookup"><span data-stu-id="58c5c-108">You can also set the value using these properties.</span></span>

<span data-ttu-id="58c5c-109">Avec C, le casting est généralement la meilleure approche.</span><span class="sxs-lookup"><span data-stu-id="58c5c-109">With C#, casting is generally the better approach.</span></span> <span data-ttu-id="58c5c-110">Si vous lancez l’élément ou l’attribut à un type de valeur nul, le code est plus simple à écrire lors de la récupération de la valeur d’un élément (ou attribut) qui pourrait ou ne pourrait pas exister.</span><span class="sxs-lookup"><span data-stu-id="58c5c-110">If you cast the element or attribute to a nullable value type, the code is simpler to write when retrieving the value of an element (or attribute) that might or might not exist.</span></span> <span data-ttu-id="58c5c-111">Le [dernier exemple](#element-might-not-exist-example) de cet article démontre que le casting est plus simple dans le cas où l’élément pourrait ne pas exister.</span><span class="sxs-lookup"><span data-stu-id="58c5c-111">The [last example](#element-might-not-exist-example) in this article demonstrates that casting is simpler in the case where the element might not exist.</span></span> <span data-ttu-id="58c5c-112">Toutefois, vous ne pouvez pas définir le contenu d'un élément par le biais de la conversion, comme vous le pouvez par le biais de la propriété <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="58c5c-112">However, you cannot set the contents of an element through casting, as you can through <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="string-cast-example"></a><span data-ttu-id="58c5c-113">Exemple de lance-cordes</span><span class="sxs-lookup"><span data-stu-id="58c5c-113">String cast example</span></span>  
 <span data-ttu-id="58c5c-114">Pour récupérer la valeur d’un élément, jetez l’objet <xref:System.Xml.Linq.XElement> sur le type désiré.</span><span class="sxs-lookup"><span data-stu-id="58c5c-114">To retrieve the value of an element, cast the <xref:System.Xml.Linq.XElement> object to your desired type.</span></span> <span data-ttu-id="58c5c-115">Vous pouvez jeter un élément à une chaîne, comme suit:</span><span class="sxs-lookup"><span data-stu-id="58c5c-115">You can cast an element to a string, as follows:</span></span>  
  
```csharp  
XElement e = new XElement("StringElement", "abcde");  
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + (string)e);  
```  
  
 <span data-ttu-id="58c5c-116">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="58c5c-116">This example produces the following output:</span></span>  
  
```output  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="integer-cast-example"></a><span data-ttu-id="58c5c-117">Integer fait l’exemple</span><span class="sxs-lookup"><span data-stu-id="58c5c-117">Integer cast example</span></span>  
 <span data-ttu-id="58c5c-118">Vous pouvez également convertir des éléments vers des types autres que des chaînes.</span><span class="sxs-lookup"><span data-stu-id="58c5c-118">You can also cast elements to types other than string.</span></span> <span data-ttu-id="58c5c-119">Par exemple, si vous avez un élément qui contient un entier, vous pouvez le convertir en `int`, comme illustré dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="58c5c-119">For example, if you have an element that contains an integer, you can cast it to `int`, as shown in the following code:</span></span>  
  
```csharp  
XElement e = new XElement("Age", "44");  
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + (int)e);  
```  
  
 <span data-ttu-id="58c5c-120">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="58c5c-120">This example produces the following output:</span></span>  
  
```output  
<Age>44</Age>  
Value of e:44  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="58c5c-121">fournit des opérateurs de cast explicites pour les types de données suivants : `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID` et `GUID?`.</span><span class="sxs-lookup"><span data-stu-id="58c5c-121">provides explicit cast operators for the following data types: `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`, and `GUID?`.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="58c5c-122">fournit les mêmes opérateurs de conversion pour les objets <xref:System.Xml.Linq.XAttribute>.</span><span class="sxs-lookup"><span data-stu-id="58c5c-122">provides the same cast operators for <xref:System.Xml.Linq.XAttribute> objects.</span></span>  
  
## <a name="value-property-example"></a><span data-ttu-id="58c5c-123">Exemple de propriété de valeur</span><span class="sxs-lookup"><span data-stu-id="58c5c-123">Value property example</span></span>  
 <span data-ttu-id="58c5c-124">Vous pouvez utiliser la propriété <xref:System.Xml.Linq.XElement.Value%2A> pour récupérer le contenu d'un élément :</span><span class="sxs-lookup"><span data-stu-id="58c5c-124">You can use the <xref:System.Xml.Linq.XElement.Value%2A> property to retrieve the contents of an element:</span></span>  
  
```csharp  
XElement e = new XElement("StringElement", "abcde");
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + e.Value);  
```  
  
 <span data-ttu-id="58c5c-125">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="58c5c-125">This example produces the following output:</span></span>  
  
```output  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="element-might-not-exist-example"></a><span data-ttu-id="58c5c-126">L’élément n’existe peut-être pas d’exemple</span><span class="sxs-lookup"><span data-stu-id="58c5c-126">Element might not exist example</span></span>
 <span data-ttu-id="58c5c-127">Parfois, vous essayez de récupérer la valeur d’un élément, même si vous n’êtes pas sûr si elle existe.</span><span class="sxs-lookup"><span data-stu-id="58c5c-127">Sometimes you try to retrieve the value of an element even though you're not sure if it exists.</span></span> <span data-ttu-id="58c5c-128">Dans ce cas, lorsque vous attribuez l’élément castré à un type de référence nul ou à `null`un type de valeur nul, si l’élément n’existe pas, la variable assignée est définie à .</span><span class="sxs-lookup"><span data-stu-id="58c5c-128">In this case, when you assign the casted element to a nullable reference type or nullable value type, if the element does not exist, the assigned variable is set to `null`.</span></span> <span data-ttu-id="58c5c-129">Le code suivant montre que lorsqu'il n'est pas certain que l'élément existe, il est plus simple d'utiliser la conversion que la propriété <xref:System.Xml.Linq.XElement.Value%2A>.</span><span class="sxs-lookup"><span data-stu-id="58c5c-129">The following code shows that when the element might or might not exist, it is easier to use casting than to use the <xref:System.Xml.Linq.XElement.Value%2A> property.</span></span>  
  
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
  
 <span data-ttu-id="58c5c-130">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="58c5c-130">This code produces the following output:</span></span>  
  
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
  
 <span data-ttu-id="58c5c-131">En général, le code à écrire est plus simple lors de l'utilisation de la conversion pour récupérer le contenu d'éléments ou d'attributs.</span><span class="sxs-lookup"><span data-stu-id="58c5c-131">In general, you can write simpler code when using casting to retrieve the contents of elements and attributes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58c5c-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="58c5c-132">See also</span></span>

- [<span data-ttu-id="58c5c-133">Axes LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="58c5c-133">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
