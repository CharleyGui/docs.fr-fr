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
# <a name="how-to-create-a-document-with-namespaces-in-c-linq-to-xml"></a>Comment créer un document avec des espaces de noms en C# (LINQ to XML)

Cet article montre comment créer des documents en C# qui ont des espaces de noms.

## <a name="example-declare-and-initialize-a-default-namespace"></a>Exemple : déclarer et initialiser un espace de noms par défaut

Pour créer un élément ou un attribut qui se trouve dans un espace de noms, vous devez d’abord déclarer et initialiser un <xref:System.Xml.Linq.XNamespace> objet. Vous devez ensuite utiliser la surcharge d'opérateur d'addition pour combiner l'espace de noms avec le nom local, exprimé sous la forme de chaîne.

L'exemple suivant crée un document avec un espace de noms. Par défaut, LINQ to XML sérialise ce document avec un espace de noms par défaut.

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

## <a name="example-create-a-document-that-has-a-namespace-and-an-attribute"></a>Exemple : créer un document avec un espace de noms et un attribut

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

## <a name="example-create-a-document-that-has-two-namespaces-one-with-a-prefix"></a>Exemple : créer un document qui a deux espaces de noms, un avec un préfixe

L'exemple suivant illustre la création d'un document qui contient deux espaces de noms. L’un est l’espace de noms par défaut, l’autre est un espace de noms avec un préfixe.

En incluant des attributs d’espace de noms dans l’élément racine, les espaces de noms sont sérialisés de sorte qu' `http://www.adventure-works.com` il s’agit de l’espace de noms par défaut, et `www.fourthcoffee.com` est sérialisé avec un préfixe `fc` . Pour créer un attribut qui déclare un espace de noms par défaut, vous devez créer un attribut avec le nom `xmlns` , sans espace de noms. La valeur de l'attribut est l'URI de l'espace de noms par défaut.

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

## <a name="example-create-a-document-that-has-two-namespaces-both-with-prefixes"></a>Exemple : créer un document qui a deux espaces de noms, tous deux avec des préfixes

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

## <a name="example-create-a-namespace-using-expanded-names"></a>Exemple : créer un espace de noms à l’aide de noms développés

Une autre approche permettant d'obtenir les mêmes résultats consiste à utiliser des noms développés au lieu de déclarer et de créer un objet <xref:System.Xml.Linq.XNamespace>.

Cette approche a des implications en termes de performances. Chaque fois que vous transmettez une chaîne qui contient un nom développé à LINQ to XML, LINQ to XML devez analyser le nom, Rechercher l’espace de noms atomisé et rechercher le nom atomisé. Ce processus consomme du temps de processeur. Si les performances sont importantes, vous souhaiterez peut-être déclarer et utiliser un objet <xref:System.Xml.Linq.XNamespace> de manière explicite.

Si les performances constituent un problème important, consultez [préatomisation des objets XName](pre-atomization-xname-objects.md) pour plus d’informations.

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

- [Vue d’ensemble des espaces de noms](namespaces-overview.md)
