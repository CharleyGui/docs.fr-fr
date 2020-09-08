---
title: Comment créer un document avec des espaces de noms en C#-LINQ to XML
description: Utilisez l’objet XNamespace en C# pour créer des documents qui ont des espaces de noms ou des espaces de noms par défaut avec un préfixe.
ms.date: 07/20/2015
ms.assetid: 37e63c57-f86d-47ac-88a7-2c2d107def30
ms.openlocfilehash: 3ec9624bcc599a73a6872e5c4c79504a1a4b4380
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553519"
---
# <a name="how-to-create-a-document-with-namespaces-in-c-linq-to-xml"></a><span data-ttu-id="9777d-103">Comment créer un document avec des espaces de noms en C# (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="9777d-103">How to create a document with namespaces in C# (LINQ to XML)</span></span>

<span data-ttu-id="9777d-104">Cet article montre comment créer des documents en C# qui ont des espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="9777d-104">This article shows how to create documents in C# that have namespaces.</span></span>

## <a name="example-declare-and-initialize-a-default-namespace"></a><span data-ttu-id="9777d-105">Exemple : déclarer et initialiser un espace de noms par défaut</span><span class="sxs-lookup"><span data-stu-id="9777d-105">Example: Declare and initialize a default namespace</span></span>

<span data-ttu-id="9777d-106">Pour créer un élément ou un attribut qui se trouve dans un espace de noms, vous devez d’abord déclarer et initialiser un <xref:System.Xml.Linq.XNamespace> objet.</span><span class="sxs-lookup"><span data-stu-id="9777d-106">To create an element or an attribute that's in a namespace, you first declare and initialize an <xref:System.Xml.Linq.XNamespace> object.</span></span> <span data-ttu-id="9777d-107">Vous devez ensuite utiliser la surcharge d'opérateur d'addition pour combiner l'espace de noms avec le nom local, exprimé sous la forme de chaîne.</span><span class="sxs-lookup"><span data-stu-id="9777d-107">You then use the addition operator overload to combine the namespace with the local name, expressed as a string.</span></span>

<span data-ttu-id="9777d-108">L'exemple suivant crée un document avec un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="9777d-108">The following example creates a document with one namespace.</span></span> <span data-ttu-id="9777d-109">Par défaut, LINQ to XML sérialise ce document avec un espace de noms par défaut.</span><span class="sxs-lookup"><span data-stu-id="9777d-109">By default, LINQ to XML serializes this document with a default namespace.</span></span>

```csharp
// Create an XML tree in a namespace.
XNamespace aw = "http://www.adventure-works.com";
XElement root = new XElement(aw + "Root",
    new XElement(aw + "Child", "child content")
);
Console.WriteLine(root);
```

<span data-ttu-id="9777d-110">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="9777d-110">This example produces the following output:</span></span>

```xml
<Root xmlns="http://www.adventure-works.com">
  <Child>child content</Child>
</Root>
```

## <a name="example-create-a-document-that-has-a-namespace-and-an-attribute"></a><span data-ttu-id="9777d-111">Exemple : créer un document avec un espace de noms et un attribut</span><span class="sxs-lookup"><span data-stu-id="9777d-111">Example: Create a document that has a namespace and an attribute</span></span>

<span data-ttu-id="9777d-112">L'exemple suivant crée un document avec un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="9777d-112">The following example creates a document with one namespace.</span></span> <span data-ttu-id="9777d-113">Il crée également un attribut qui déclare l'espace de noms avec un préfixe d'espace de noms.</span><span class="sxs-lookup"><span data-stu-id="9777d-113">It also creates an attribute that declares the namespace with a namespace prefix.</span></span> <span data-ttu-id="9777d-114">Pour créer un attribut qui déclare un espace de noms avec un préfixe, vous devez créer un attribut où le nom de l'attribut est le préfixe d'espace de noms, et ce nom est dans l'espace de noms <xref:System.Xml.Linq.XNamespace.Xmlns%2A>.</span><span class="sxs-lookup"><span data-stu-id="9777d-114">To create an attribute that declares a namespace with a prefix, you create an attribute where the name of the attribute is the namespace prefix, and this name is in the <xref:System.Xml.Linq.XNamespace.Xmlns%2A> namespace.</span></span> <span data-ttu-id="9777d-115">La valeur de cet attribut est l'URI de l'espace de noms.</span><span class="sxs-lookup"><span data-stu-id="9777d-115">The value of this attribute is the URI of the namespace.</span></span>

```csharp
// Create an XML tree in a namespace, with a specified prefix
XNamespace aw = "http://www.adventure-works.com";
XElement root = new XElement(aw + "Root",
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com"),
    new XElement(aw + "Child", "child content")
);
Console.WriteLine(root);
```

<span data-ttu-id="9777d-116">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="9777d-116">This example produces the following output:</span></span>

```xml
<aw:Root xmlns:aw="http://www.adventure-works.com">
  <aw:Child>child content</aw:Child>
</aw:Root>
```

## <a name="example-create-a-document-that-has-two-namespaces-one-with-a-prefix"></a><span data-ttu-id="9777d-117">Exemple : créer un document qui a deux espaces de noms, un avec un préfixe</span><span class="sxs-lookup"><span data-stu-id="9777d-117">Example: Create a document that has two namespaces, one with a prefix</span></span>

<span data-ttu-id="9777d-118">L'exemple suivant illustre la création d'un document qui contient deux espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="9777d-118">The following example shows the creation of a document that contains two namespaces.</span></span> <span data-ttu-id="9777d-119">L’un est l’espace de noms par défaut, l’autre est un espace de noms avec un préfixe.</span><span class="sxs-lookup"><span data-stu-id="9777d-119">One is the default namespace, the other is a namespace with a prefix.</span></span>

<span data-ttu-id="9777d-120">En incluant des attributs d’espace de noms dans l’élément racine, les espaces de noms sont sérialisés de sorte qu' `http://www.adventure-works.com` il s’agit de l’espace de noms par défaut, et `www.fourthcoffee.com` est sérialisé avec un préfixe `fc` .</span><span class="sxs-lookup"><span data-stu-id="9777d-120">By including namespace attributes in the root element, the namespaces are serialized so that `http://www.adventure-works.com` is the default namespace, and `www.fourthcoffee.com` is serialized with a prefix of `fc`.</span></span> <span data-ttu-id="9777d-121">Pour créer un attribut qui déclare un espace de noms par défaut, vous devez créer un attribut avec le nom `xmlns` , sans espace de noms.</span><span class="sxs-lookup"><span data-stu-id="9777d-121">To create an attribute that declares a default namespace, you create an attribute with the name `xmlns`, without a namespace.</span></span> <span data-ttu-id="9777d-122">La valeur de l'attribut est l'URI de l'espace de noms par défaut.</span><span class="sxs-lookup"><span data-stu-id="9777d-122">The value of the attribute is the default namespace URI.</span></span>

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

<span data-ttu-id="9777d-123">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="9777d-123">This example produces the following output:</span></span>

```xml
<Root xmlns="http://www.adventure-works.com" xmlns:fc="www.fourthcoffee.com">
  <fc:Child>
    <DifferentChild>other content</DifferentChild>
  </fc:Child>
  <Child2>c2 content</Child2>
  <fc:Child3>c3 content</fc:Child3>
</Root>
```

## <a name="example-create-a-document-that-has-two-namespaces-both-with-prefixes"></a><span data-ttu-id="9777d-124">Exemple : créer un document qui a deux espaces de noms, tous deux avec des préfixes</span><span class="sxs-lookup"><span data-stu-id="9777d-124">Example: Create a document that has two namespaces, both with prefixes</span></span>

<span data-ttu-id="9777d-125">L'exemple suivant crée un document qui contient deux espaces de noms, tous deux avec des préfixes d'espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="9777d-125">The following example creates a document that contains two namespaces, both with namespace prefixes.</span></span>

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

<span data-ttu-id="9777d-126">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="9777d-126">This example produces the following output:</span></span>

```xml
<aw:Root xmlns:aw="http://www.adventure-works.com" xmlns:fc="www.fourthcoffee.com">
  <fc:Child>
    <aw:DifferentChild>other content</aw:DifferentChild>
  </fc:Child>
  <aw:Child2>c2 content</aw:Child2>
  <fc:Child3>c3 content</fc:Child3>
</aw:Root>
```

## <a name="example-create-a-namespace-using-expanded-names"></a><span data-ttu-id="9777d-127">Exemple : créer un espace de noms à l’aide de noms développés</span><span class="sxs-lookup"><span data-stu-id="9777d-127">Example: Create a namespace using expanded names</span></span>

<span data-ttu-id="9777d-128">Une autre approche permettant d'obtenir les mêmes résultats consiste à utiliser des noms développés au lieu de déclarer et de créer un objet <xref:System.Xml.Linq.XNamespace>.</span><span class="sxs-lookup"><span data-stu-id="9777d-128">Another way to accomplish the same result is to use expanded names instead of declaring and creating an <xref:System.Xml.Linq.XNamespace> object.</span></span>

<span data-ttu-id="9777d-129">Cette approche a des implications en termes de performances.</span><span class="sxs-lookup"><span data-stu-id="9777d-129">This approach has performance implications.</span></span> <span data-ttu-id="9777d-130">Chaque fois que vous transmettez une chaîne qui contient un nom développé à LINQ to XML, LINQ to XML devez analyser le nom, Rechercher l’espace de noms atomisé et rechercher le nom atomisé.</span><span class="sxs-lookup"><span data-stu-id="9777d-130">Each time you pass a string that contains an expanded name to LINQ to XML, LINQ to XML must parse the name, find the atomized namespace, and find the atomized name.</span></span> <span data-ttu-id="9777d-131">Ce processus consomme du temps de processeur.</span><span class="sxs-lookup"><span data-stu-id="9777d-131">This process takes CPU time.</span></span> <span data-ttu-id="9777d-132">Si les performances sont importantes, vous souhaiterez peut-être déclarer et utiliser un objet <xref:System.Xml.Linq.XNamespace> de manière explicite.</span><span class="sxs-lookup"><span data-stu-id="9777d-132">If performance is important, you might want to declare and use an <xref:System.Xml.Linq.XNamespace> object explicitly.</span></span>

<span data-ttu-id="9777d-133">Si les performances constituent un problème important, consultez [préatomisation des objets XName](pre-atomization-xname-objects.md) pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="9777d-133">If performance is an important issue, see [Pre-Atomization of XName Objects](pre-atomization-xname-objects.md) for more information.</span></span>

```csharp
// Create an XML tree in a namespace, with a specified prefix
XElement root = new XElement("{http://www.adventure-works.com}Root",
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com"),
    new XElement("{http://www.adventure-works.com}Child", "child content")
);
Console.WriteLine(root);
```

<span data-ttu-id="9777d-134">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="9777d-134">This example produces the following output:</span></span>

```xml
<aw:Root xmlns:aw="http://www.adventure-works.com">
  <aw:Child>child content</aw:Child>
</aw:Root>
```

## <a name="see-also"></a><span data-ttu-id="9777d-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9777d-135">See also</span></span>

- [<span data-ttu-id="9777d-136">Vue d’ensemble des espaces de noms</span><span class="sxs-lookup"><span data-stu-id="9777d-136">Namespaces overview</span></span>](namespaces-overview.md)
