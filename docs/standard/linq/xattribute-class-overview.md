---
title: Vue d’ensemble de la classe XAttribute
description: La classe XAttribute représente des attributs XML. L’utilisation des attributs dans LINQ to XML est semblable à l’utilisation des éléments.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 5a630f24-f9ad-400e-831e-c14ebfc9e142
ms.openlocfilehash: deab6e8dd9695a442cd362401aec8b68cdbf218f
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552401"
---
# <a name="xattribute-class-overview"></a>Vue d’ensemble de la classe XAttribute

Les attributs sont des paires nom-valeur associées à un élément. La classe <xref:System.Xml.Linq.XAttribute> représente des attributs XML.

L’utilisation des attributs dans LINQ to XML est semblable à l’utilisation des éléments. Leurs constructeurs sont similaires. Les méthodes que vous utilisez pour en récupérer des collections sont similaires. Une expression de requête LINQ pour une collection d’attributs ressemble à une expression de requête LINQ pour une collection d’éléments.

L'ordre dans lequel les attributs ont été ajoutés à un élément est conservé. Autrement dit, lorsque vous itérez au sein des attributs, vous les voyez dans l'ordre dans lequel ils ont été ajoutés.

## <a name="the-xattribute-constructor"></a>Le constructeur XAttribute

Le constructeur suivant de la <xref:System.Xml.Linq.XAttribute> classe est celui que vous utiliserez le plus souvent :

|Constructeur|Description|
|-----------------|-----------------|
|`XAttribute(XName name, object content)`|Elle crée un objet <xref:System.Xml.Linq.XAttribute>. L'argument `name` spécifie le nom de l'attribut ; l'argument `content` spécifie le contenu de l'attribut.|

## <a name="example-create-an-element-with-an-attribute"></a>Exemple : créer un élément avec un attribut

L’exemple suivant illustre la tâche courante de création d’un élément qui contient un attribut.

```csharp
XElement phone = new XElement("Phone",
    new XAttribute("Type", "Home"),
    "555-555-5555");
Console.WriteLine(phone);
```

```vb
Dim phone As XElement = <Phone Type="Home">555-555-5555</Phone>
Console.WriteLine(phone)
```

Cet exemple produit la sortie suivante :

```xml
<Phone Type="Home">555-555-5555</Phone>
```

## <a name="example-functional-construction-of-attributes"></a>Exemple : construction fonctionnelle d’attributs

Vous pouvez construire des <xref:System.Xml.Linq.XAttribute> objets en ligne avec la construction d' <xref:System.Xml.Linq.XElement> objets, comme indiqué dans l’exemple suivant :

```csharp
XElement c = new XElement("Customers",
    new XElement("Customer",
        new XElement("Name", "John Doe"),
        new XElement("PhoneNumbers",
            new XElement("Phone",
                new XAttribute("type", "home"),
                "555-555-5555"),
            new XElement("Phone",
                new XAttribute("type", "work"),
                "666-666-6666")
        )
    )
);
Console.WriteLine(c);
```

```vb
Dim c As XElement = _
    <Customers>
        <Customer>
            <Name>John Doe</Name>
            <PhoneNumbers>
                <Phone type="home">555-555-5555</Phone>
                <Phone type="work">666-666-6666</Phone>
            </PhoneNumbers>
        </Customer>
    </Customers>
Console.WriteLine(c)
```

Cet exemple produit la sortie suivante :

```xml
<Customers>
  <Customer>
    <Name>John Doe</Name>
    <PhoneNumbers>
      <Phone type="home">555-555-5555</Phone>
      <Phone type="work">666-666-6666</Phone>
    </PhoneNumbers>
  </Customer>
</Customers>
```

## <a name="attributes-arent-nodes"></a>Les attributs ne sont pas des nœuds

Il existe certaines différences entre les attributs et les éléments. <xref:System.Xml.Linq.XAttribute> les objets ne sont pas des nœuds dans l’arborescence XML. Il s’agit de paires nom-valeur associées à un élément XML. Par opposition au modèle DOM (Document Objet Model), cela reflète plus étroitement la structure du langage XML. Bien que <xref:System.Xml.Linq.XAttribute> les objets ne soient pas réellement des nœuds dans l’arborescence XML, l’utilisation d' <xref:System.Xml.Linq.XAttribute> objets est semblable à l’utilisation d' <xref:System.Xml.Linq.XElement> objets.

Cette distinction ne revêt une importance que pour les développeurs qui écrivent du code qui interagit avec des arborescences XML au niveau nœud. De nombreux développeurs ne se soucient pas de cette distinction.

## <a name="see-also"></a>Voir aussi

- [Présentation de LINQ to XML](linq-xml-overview.md)
