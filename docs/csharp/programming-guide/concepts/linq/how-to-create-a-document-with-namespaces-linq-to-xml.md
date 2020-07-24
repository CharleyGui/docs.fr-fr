---
title: Comment créer un document avec des espaces de noms (C#) (LINQ to XML)
description: Apprenez à créer un document avec un espace de noms dans LINQ to XML en C# en utilisant un objet XNamespace pour combiner l’espace de noms avec le nom local.
ms.date: 07/20/2015
ms.assetid: 37e63c57-f86d-47ac-88a7-2c2d107def30
ms.openlocfilehash: 6472baefc73285af1c6dca0bfe7d874003940fc4
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103390"
---
# <a name="how-to-create-a-document-with-namespaces-c-linq-to-xml"></a>Comment créer un document avec des espaces de noms (C#) (LINQ to XML)
Cette rubrique montre comment créer des documents avec des espaces de noms.  
  
## <a name="example"></a>Exemple  
 Pour créer un élément ou un attribut qui se trouve dans un espace de noms, vous devez d'abord déclarer et initialiser un objet <xref:System.Xml.Linq.XNamespace>. Vous devez ensuite utiliser la surcharge d'opérateur d'addition pour combiner l'espace de noms avec le nom local, exprimé sous la forme de chaîne.  
  
 L'exemple suivant crée un document avec un espace de noms. Par défaut, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sérialise ce document avec un espace de noms par défaut.  
  
```csharp  
// Create an XML tree in a namespace.  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
    new XElement(aw + "Child", "child content")  
);  
Console.WriteLine(root);  
```  
  
 Cet exemple produit la sortie suivante :  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child>child content</Child>  
</Root>  
```  
  
## <a name="example"></a>Exemple  
 L'exemple suivant crée un document avec un espace de noms. Il crée également un attribut qui déclare l'espace de noms avec un préfixe d'espace de noms. Pour créer un attribut qui déclare un espace de noms avec un préfixe, vous devez créer un attribut où le nom de l'attribut est le préfixe d'espace de noms, et ce nom est dans l'espace de noms <xref:System.Xml.Linq.XNamespace.Xmlns%2A>. La valeur de cet attribut est l'URI de l'espace de noms.  
  
```csharp  
// Create an XML tree in a namespace, with a specified prefix  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com"),  
    new XElement(aw + "Child", "child content")  
);  
Console.WriteLine(root);  
```  
  
 Cet exemple produit la sortie suivante :  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Child>child content</aw:Child>  
</aw:Root>  
```  
  
## <a name="example"></a>Exemple  
 L'exemple suivant illustre la création d'un document qui contient deux espaces de noms. L'un est l'espace de noms par défaut. L'autre est un espace de noms avec un préfixe.  
  
 Grâce à l’inclusion d’attributs d’espaces de noms dans l’élément racine, les espaces de noms sont sérialisés de sorte que `http://www.adventure-works.com` soit l’espace de noms par défaut et `www.fourthcoffee.com` soit sérialisé avec le préfixe « fc ». Pour créer un attribut qui déclare un espace de noms par défaut, vous devez créer un attribut avec le nom « xmlns », sans espace de noms. La valeur de l'attribut est l'URI de l'espace de noms par défaut.  
  
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
  
 Cet exemple produit la sortie suivante :  
  
```xml  
<Root xmlns="http://www.adventure-works.com" xmlns:fc="www.fourthcoffee.com">  
  <fc:Child>  
    <DifferentChild>other content</DifferentChild>  
  </fc:Child>  
  <Child2>c2 content</Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</Root>  
```  
  
## <a name="example"></a>Exemple  
 L'exemple suivant crée un document qui contient deux espaces de noms, tous deux avec des préfixes d'espaces de noms.  
  
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
  
 Cet exemple produit la sortie suivante :  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com" xmlns:fc="www.fourthcoffee.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="example"></a>Exemple  
 Une autre approche permettant d'obtenir les mêmes résultats consiste à utiliser des noms développés au lieu de déclarer et de créer un objet <xref:System.Xml.Linq.XNamespace>.  
  
 Cette approche a des implications en termes de performances. Chaque fois que vous passez une chaîne qui contient un nom développé à [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] doit analyser le nom, rechercher l’espace de noms atomisé et rechercher le nom atomisé. Ce processus consomme du temps de processeur. Si les performances sont importantes, vous souhaiterez peut-être déclarer et utiliser un objet <xref:System.Xml.Linq.XNamespace> de manière explicite.  
  
 Si les performances sont importantes, consultez [Préatomisation des objets XName (LINQ to XML) (C#)](./pre-atomization-of-xname-objects-linq-to-xml.md) pour plus d’informations  
  
```csharp  
// Create an XML tree in a namespace, with a specified prefix  
XElement root = new XElement("{http://www.adventure-works.com}Root",  
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com"),  
    new XElement("{http://www.adventure-works.com}Child", "child content")  
);  
Console.WriteLine(root);  
```  
  
 Cet exemple produit la sortie suivante :  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Child>child content</aw:Child>  
</aw:Root>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des espaces de noms (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md)
