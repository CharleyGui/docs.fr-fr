---
title: 'Procédure : Créer un document avec des espaces de noms (C#) (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 37e63c57-f86d-47ac-88a7-2c2d107def30
ms.openlocfilehash: 9b9e81a131d4e17ce2d87dd3f511ed66e370d884
ms.sourcegitcommit: eb9ff6f364cde6f11322e03800d8f5ce302f3c73
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68710003"
---
# <a name="how-to-create-a-document-with-namespaces-c-linq-to-xml"></a><span data-ttu-id="76a55-102">Procédure : Créer un document avec des espaces de noms (C#) (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="76a55-102">How to: Create a Document with Namespaces (C#) (LINQ to XML)</span></span>
<span data-ttu-id="76a55-103">Cette rubrique montre comment créer des documents avec des espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="76a55-103">This topic shows how to create documents with namespaces.</span></span>  
  
## <a name="example"></a><span data-ttu-id="76a55-104">Exemples</span><span class="sxs-lookup"><span data-stu-id="76a55-104">Example</span></span>  
 <span data-ttu-id="76a55-105">Pour créer un élément ou un attribut qui se trouve dans un espace de noms, vous devez d'abord déclarer et initialiser un objet <xref:System.Xml.Linq.XNamespace>.</span><span class="sxs-lookup"><span data-stu-id="76a55-105">To create an element or an attribute that is in a namespace, you first declare and initialize an <xref:System.Xml.Linq.XNamespace> object.</span></span> <span data-ttu-id="76a55-106">Vous devez ensuite utiliser la surcharge d'opérateur d'addition pour combiner l'espace de noms avec le nom local, exprimé sous la forme de chaîne.</span><span class="sxs-lookup"><span data-stu-id="76a55-106">You then use the addition operator overload to combine the namespace with the local name, expressed as a string.</span></span>  
  
 <span data-ttu-id="76a55-107">L'exemple suivant crée un document avec un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="76a55-107">The following example creates a document with one namespace.</span></span> <span data-ttu-id="76a55-108">Par défaut, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sérialise ce document avec un espace de noms par défaut.</span><span class="sxs-lookup"><span data-stu-id="76a55-108">By default, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] serializes this document with a default namespace.</span></span>  
  
```csharp  
// Create an XML tree in a namespace.  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
    new XElement(aw + "Child", "child content")  
);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="76a55-109">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="76a55-109">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child>child content</Child>  
</Root>  
```  
  
## <a name="example"></a><span data-ttu-id="76a55-110">Exemples</span><span class="sxs-lookup"><span data-stu-id="76a55-110">Example</span></span>  
 <span data-ttu-id="76a55-111">L'exemple suivant crée un document avec un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="76a55-111">The following example creates a document with one namespace.</span></span> <span data-ttu-id="76a55-112">Il crée également un attribut qui déclare l'espace de noms avec un préfixe d'espace de noms.</span><span class="sxs-lookup"><span data-stu-id="76a55-112">It also creates an attribute that declares the namespace with a namespace prefix.</span></span> <span data-ttu-id="76a55-113">Pour créer un attribut qui déclare un espace de noms avec un préfixe, vous devez créer un attribut où le nom de l'attribut est le préfixe d'espace de noms, et ce nom est dans l'espace de noms <xref:System.Xml.Linq.XNamespace.Xmlns%2A>.</span><span class="sxs-lookup"><span data-stu-id="76a55-113">To create an attribute that declares a namespace with a prefix, you create an attribute where the name of the attribute is the namespace prefix, and this name is in the <xref:System.Xml.Linq.XNamespace.Xmlns%2A> namespace.</span></span> <span data-ttu-id="76a55-114">La valeur de cet attribut est l'URI de l'espace de noms.</span><span class="sxs-lookup"><span data-stu-id="76a55-114">The value of this attribute is the URI of the namespace.</span></span>  
  
```csharp  
// Create an XML tree in a namespace, with a specified prefix  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com"),  
    new XElement(aw + "Child", "child content")  
);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="76a55-115">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="76a55-115">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Child>child content</aw:Child>  
</aw:Root>  
```  
  
## <a name="example"></a><span data-ttu-id="76a55-116">Exemples</span><span class="sxs-lookup"><span data-stu-id="76a55-116">Example</span></span>  
 <span data-ttu-id="76a55-117">L'exemple suivant illustre la création d'un document qui contient deux espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="76a55-117">The following example shows the creation of a document that contains two namespaces.</span></span> <span data-ttu-id="76a55-118">L'un est l'espace de noms par défaut.</span><span class="sxs-lookup"><span data-stu-id="76a55-118">One is the default namespace.</span></span> <span data-ttu-id="76a55-119">L'autre est un espace de noms avec un préfixe.</span><span class="sxs-lookup"><span data-stu-id="76a55-119">Another is a namespace with a prefix.</span></span>  
  
 <span data-ttu-id="76a55-120">Grâce à l’inclusion d’attributs d’espaces de noms dans l’élément racine, les espaces de noms sont sérialisés de sorte que `http://www.adventure-works.com` soit l’espace de noms par défaut et `www.fourthcoffee.com` soit sérialisé avec le préfixe « fc ».</span><span class="sxs-lookup"><span data-stu-id="76a55-120">By including namespace attributes in the root element, the namespaces are serialized so that `http://www.adventure-works.com` is the default namespace, and `www.fourthcoffee.com` is serialized with a prefix of "fc".</span></span> <span data-ttu-id="76a55-121">Pour créer un attribut qui déclare un espace de noms par défaut, vous devez créer un attribut avec le nom « xmlns », sans espace de noms.</span><span class="sxs-lookup"><span data-stu-id="76a55-121">To create an attribute that declares a default namespace, you create an attribute with the name "xmlns", without a namespace.</span></span> <span data-ttu-id="76a55-122">La valeur de l'attribut est l'URI de l'espace de noms par défaut.</span><span class="sxs-lookup"><span data-stu-id="76a55-122">The value of the attribute is the default namespace URI.</span></span>  
  
```csharp  
// The http://www.adventure-works.com namespace is forced to be the default namespace.  
XNamespace aw = "http://www.adventure-works.com";  
XNamespace fc = "www.fourthcoffee.com";  
XElement root = new XElement(aw + "Root",  
    new XAttribute("xmlns", "http://www.adventure-works.com"),  
    new XAttribute(XNamespace.Xmlns + "fc", "www.fourthcoffee.com"),  
    new XElement(fc + "Child",  
        new XElement(aw + "DifferentChild", "other content")  
    ),  
    new XElement(aw + "Child2", "c2 content"),  
    new XElement(fc + "Child3", "c3 content")  
);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="76a55-123">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="76a55-123">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com" xmlns:fc="www.fourthcoffee.com">  
  <fc:Child>  
    <DifferentChild>other content</DifferentChild>  
  </fc:Child>  
  <Child2>c2 content</Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</Root>  
```  
  
## <a name="example"></a><span data-ttu-id="76a55-124">Exemples</span><span class="sxs-lookup"><span data-stu-id="76a55-124">Example</span></span>  
 <span data-ttu-id="76a55-125">L'exemple suivant crée un document qui contient deux espaces de noms, tous deux avec des préfixes d'espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="76a55-125">The following example creates a document that contains two namespaces, both with namespace prefixes.</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XNamespace fc = "www.fourthcoffee.com";  
XElement root = new XElement(aw + "Root",  
    new XAttribute(XNamespace.Xmlns + "aw", aw.NamespaceName),  
    new XAttribute(XNamespace.Xmlns + "fc", fc.NamespaceName),  
    new XElement(fc + "Child",  
        new XElement(aw + "DifferentChild", "other content")  
    ),  
    new XElement(aw + "Child2", "c2 content"),  
    new XElement(fc + "Child3", "c3 content")  
);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="76a55-126">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="76a55-126">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com" xmlns:fc="www.fourthcoffee.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="example"></a><span data-ttu-id="76a55-127">Exemples</span><span class="sxs-lookup"><span data-stu-id="76a55-127">Example</span></span>  
 <span data-ttu-id="76a55-128">Une autre approche permettant d'obtenir les mêmes résultats consiste à utiliser des noms développés au lieu de déclarer et de créer un objet <xref:System.Xml.Linq.XNamespace>.</span><span class="sxs-lookup"><span data-stu-id="76a55-128">Another way to accomplish the same result is to use expanded names instead of declaring and creating an <xref:System.Xml.Linq.XNamespace> object.</span></span>  
  
 <span data-ttu-id="76a55-129">Cette approche a des implications en termes de performances.</span><span class="sxs-lookup"><span data-stu-id="76a55-129">This approach has performance implications.</span></span> <span data-ttu-id="76a55-130">Chaque fois que vous passez une chaîne qui contient un nom développé à [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] doit analyser le nom, rechercher l’espace de noms atomisé et rechercher le nom atomisé.</span><span class="sxs-lookup"><span data-stu-id="76a55-130">Each time you pass a string that contains an expanded name to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] must parse the name, find the atomized namespace, and find the atomized name.</span></span> <span data-ttu-id="76a55-131">Ce processus consomme du temps de processeur.</span><span class="sxs-lookup"><span data-stu-id="76a55-131">This process takes CPU time.</span></span> <span data-ttu-id="76a55-132">Si les performances sont importantes, vous souhaiterez peut-être déclarer et utiliser un objet <xref:System.Xml.Linq.XNamespace> de manière explicite.</span><span class="sxs-lookup"><span data-stu-id="76a55-132">If performance is important, you might want to declare and use an <xref:System.Xml.Linq.XNamespace> object explicitly.</span></span>  
  
 <span data-ttu-id="76a55-133">Si les performances sont importantes, consultez [Préatomisation des objets XName (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/pre-atomization-of-xname-objects-linq-to-xml.md) pour plus d’informations</span><span class="sxs-lookup"><span data-stu-id="76a55-133">If performance is an important issue, see [Pre-Atomization of XName Objects (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/pre-atomization-of-xname-objects-linq-to-xml.md) for more information</span></span>  
  
```csharp  
// Create an XML tree in a namespace, with a specified prefix  
XElement root = new XElement("{http://www.adventure-works.com}Root",  
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com"),  
    new XElement("{http://www.adventure-works.com}Child", "child content")  
);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="76a55-134">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="76a55-134">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Child>child content</aw:Child>  
</aw:Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="76a55-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="76a55-135">See also</span></span>

- [<span data-ttu-id="76a55-136">Vue d’ensemble des espaces de noms (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="76a55-136">Namespaces Overview (LINQ to XML) (C#)</span></span>](namespaces-overview-linq-to-xml.md)
