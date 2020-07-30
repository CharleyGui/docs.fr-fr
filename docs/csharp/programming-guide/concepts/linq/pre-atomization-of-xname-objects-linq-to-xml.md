---
title: Préatomisation des objets XName (LINQ to XML) (C#)
description: En savoir plus sur la préatomisation des objets XName. La pré-atomisation des objets améliore les performances lors de la création d’une grande arborescence XML dans laquelle des noms spécifiques sont répétés.
ms.date: 07/20/2015
ms.assetid: e84fbbe7-f072-4771-bfbb-059d18e1ad15
ms.openlocfilehash: 4d217f6c78dc5d83ce424fb3ba95785f2dac0b73
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302826"
---
# <a name="pre-atomization-of-xname-objects-linq-to-xml-c"></a><span data-ttu-id="b46a1-104">Préatomisation des objets XName (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="b46a1-104">Pre-Atomization of XName Objects (LINQ to XML) (C#)</span></span>
<span data-ttu-id="b46a1-105">L'un des moyens d'améliorer les performances dans LINQ to XML est de préatomiser les objets <xref:System.Xml.Linq.XName>.</span><span class="sxs-lookup"><span data-stu-id="b46a1-105">One way to improve performance in LINQ to XML is to pre-atomize <xref:System.Xml.Linq.XName> objects.</span></span> <span data-ttu-id="b46a1-106">La préatomisation signifie que vous attribuez une chaîne à un objet <xref:System.Xml.Linq.XName> avant de créer l'arborescence XML à l'aide des constructeurs des classes <xref:System.Xml.Linq.XElement> et <xref:System.Xml.Linq.XAttribute>.</span><span class="sxs-lookup"><span data-stu-id="b46a1-106">Pre-atomization means that you assign a string to an <xref:System.Xml.Linq.XName> object before you create the XML tree by using the constructors of the <xref:System.Xml.Linq.XElement> and  <xref:System.Xml.Linq.XAttribute> classes.</span></span> <span data-ttu-id="b46a1-107">Ensuite, au lieu de passer une chaîne au constructeur, ce qui utiliserait la conversion implicite de la chaîne en <xref:System.Xml.Linq.XName>, vous passez l'objet <xref:System.Xml.Linq.XName> initialisé.</span><span class="sxs-lookup"><span data-stu-id="b46a1-107">Then, instead of passing a string to the constructor, which would use the implicit conversion from string to <xref:System.Xml.Linq.XName>, you pass the initialized <xref:System.Xml.Linq.XName> object.</span></span>  
  
 <span data-ttu-id="b46a1-108">Ceci améliore la performance lorsque vous créez une grande arborescence XML dans laquelle des noms spécifiques sont répétés.</span><span class="sxs-lookup"><span data-stu-id="b46a1-108">This improves performance when you create a large XML tree in which specific names are repeated.</span></span> <span data-ttu-id="b46a1-109">Pour ce faire, vous devez déclarer et initialiser les objets <xref:System.Xml.Linq.XName> avant de construire l'arborescence XML, puis vous devez utiliser les objets <xref:System.Xml.Linq.XName> au lieu de spécifier des chaînes pour les noms d'élément et d'attribut.</span><span class="sxs-lookup"><span data-stu-id="b46a1-109">To do this, you declare and initialize <xref:System.Xml.Linq.XName> objects before you construct the XML tree, and then use the <xref:System.Xml.Linq.XName> objects instead of specifying strings for the element and attribute names.</span></span> <span data-ttu-id="b46a1-110">Cette technique peut apporter une amélioration significative de la performance si vous créez un grand nombre d'éléments (ou d'attributs) avec le même nom.</span><span class="sxs-lookup"><span data-stu-id="b46a1-110">This technique can yield significant performance gains if you are creating a large number of elements (or attributes) with the same name.</span></span>  
  
 <span data-ttu-id="b46a1-111">Vous devez tester la préatomisation avec votre scénario pour décider si vous devez l'utiliser.</span><span class="sxs-lookup"><span data-stu-id="b46a1-111">You should test pre-atomization with your scenario to decide if you should use it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b46a1-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="b46a1-112">Example</span></span>  
 <span data-ttu-id="b46a1-113">l’exemple ci-dessous illustre ce cas de figure.</span><span class="sxs-lookup"><span data-stu-id="b46a1-113">The following example demonstrates this.</span></span>  
  
```csharp  
XName Root = "Root";  
XName Data = "Data";  
XName ID = "ID";  
  
XElement root = new XElement(Root,  
    new XElement(Data,  
        new XAttribute(ID, "1"),  
        "4,100,000"),  
    new XElement(Data,  
        new XAttribute(ID, "2"),  
        "3,700,000"),  
    new XElement(Data,  
        new XAttribute(ID, "3"),  
        "1,150,000")  
);  
  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="b46a1-114">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="b46a1-114">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Data ID="1">4,100,000</Data>  
  <Data ID="2">3,700,000</Data>  
  <Data ID="3">1,150,000</Data>  
</Root>  
```  
  
 <span data-ttu-id="b46a1-115">L'exemple suivant illustre la même technique dans laquelle le document XML est dans un espace de noms :</span><span class="sxs-lookup"><span data-stu-id="b46a1-115">The following example shows the same technique where the XML document is in a namespace:</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XName Root = aw + "Root";  
XName Data = aw + "Data";  
XName ID = "ID";  
  
XElement root = new XElement(Root,  
    new XAttribute(XNamespace.Xmlns + "aw", aw),  
    new XElement(Data,  
        new XAttribute(ID, "1"),  
        "4,100,000"),  
    new XElement(Data,  
        new XAttribute(ID, "2"),  
        "3,700,000"),  
    new XElement(Data,  
        new XAttribute(ID, "3"),  
        "1,150,000")  
);  
  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="b46a1-116">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="b46a1-116">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Data ID="1">4,100,000</aw:Data>  
  <aw:Data ID="2">3,700,000</aw:Data>  
  <aw:Data ID="3">1,150,000</aw:Data>  
</aw:Root>  
```  
  
 <span data-ttu-id="b46a1-117">L'exemple suivant reflète mieux la situation que vous êtes susceptible de rencontrer dans le monde réel.</span><span class="sxs-lookup"><span data-stu-id="b46a1-117">The following example is more similar to what you will likely encounter in the real world.</span></span> <span data-ttu-id="b46a1-118">Dans cet exemple, le contenu de l'élément est fourni par une requête :</span><span class="sxs-lookup"><span data-stu-id="b46a1-118">In this example, the content of the element is supplied by a query:</span></span>  
  
```csharp  
XName Root = "Root";  
XName Data = "Data";  
XName ID = "ID";  
  
DateTime t1 = DateTime.Now;  
XElement root = new XElement(Root,  
    from i in System.Linq.Enumerable.Range(1, 100000)  
    select new XElement(Data,  
        new XAttribute(ID, i),  
        i * 5)  
);  
DateTime t2 = DateTime.Now;  
  
Console.WriteLine("Time to construct:{0}", t2 - t1);  
```  
  
 <span data-ttu-id="b46a1-119">L'exemple suivant produit une meilleure performance que l'exemple précédent, dans lequel les noms ne sont pas préatomisés :</span><span class="sxs-lookup"><span data-stu-id="b46a1-119">The previous example performs better than the following example, in which names are not pre-atomized:</span></span>  
  
```csharp  
DateTime t1 = DateTime.Now;  
XElement root = new XElement("Root",  
    from i in System.Linq.Enumerable.Range(1, 100000)  
    select new XElement("Data",  
        new XAttribute("ID", i),  
        i * 5)  
);  
DateTime t2 = DateTime.Now;  
  
Console.WriteLine("Time to construct:{0}", t2 - t1);  
```  
  
## <a name="see-also"></a><span data-ttu-id="b46a1-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b46a1-120">See also</span></span>

- [<span data-ttu-id="b46a1-121">Objets XName et XNamespace atomisés (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="b46a1-121">Atomized XName and XNamespace Objects (LINQ to XML) (C#)</span></span>](./atomized-xname-and-xnamespace-objects-linq-to-xml.md)
