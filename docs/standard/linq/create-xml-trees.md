---
title: Créer des arborescences XML en C#-LINQ to XML
description: Vous pouvez créer une arborescence XML en C# à l’aide des constructeurs LINQ to XML XElement et XAttribute, et vous pouvez faire en sorte que le code ressemble à la structure du code XML sous-jacent.
ms.date: 08/31/2018
ms.assetid: cc74234a-0bac-4327-9c8c-5a2ead15b595
ms.openlocfilehash: 97bf40d84f40eabf6fa84f10bf4febb7697b10f5
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553760"
---
# <a name="create-xml-trees-in-c-linq-to-xml"></a>Créer des arborescences XML en C# (LINQ to XML)

Cet article fournit des informations sur la création d’arborescences XML en C#.

Pour plus d’informations sur l’utilisation des résultats de requêtes LINQ comme contenu d’un <xref:System.Xml.Linq.XElement> , consultez [construction fonctionnelle](functional-construction.md).

## <a name="construct-elements"></a>Éléments de construction

Les signatures des constructeurs <xref:System.Xml.Linq.XElement> et <xref:System.Xml.Linq.XAttribute> vous permettent de passer le contenu de l'élément ou attribut en tant qu'arguments du constructeur. Étant donné que l’un des constructeurs prend une quantité variable d’arguments, vous pouvez passer une quantité quelconque d’éléments enfants. Bien entendu, chacun de ces éléments enfants peut contenir ses propres éléments enfants. Pour tout élément, vous pouvez ajouter une quantité quelconque d'attributs.

Lors de l'ajout d'objets <xref:System.Xml.Linq.XNode> (y compris <xref:System.Xml.Linq.XElement>) ou <xref:System.Xml.Linq.XAttribute>, si le contenu n'a pas de parent, les objets sont simplement attachés à l'arborescence XML. Si le nouveau contenu a déjà un parent et fait partie d’une autre arborescence XML, il est cloné et le nouveau contenu cloné est attaché à l’arborescence XML. Le dernier exemple de cet article illustre cela.

Pour créer un `contacts` <xref:System.Xml.Linq.XElement> , vous pouvez utiliser le code suivant :

```csharp
XElement contacts =
    new XElement("Contacts",
        new XElement("Contact",
            new XElement("Name", "Patrick Hines"),
            new XElement("Phone", "206-555-0144"),
            new XElement("Address",
                new XElement("Street1", "123 Main St"),
                new XElement("City", "Mercer Island"),
                new XElement("State", "WA"),
                new XElement("Postal", "68042")
            )
        )
    );
```

S'il est mis en retrait correctement, le code pour construire des objets <xref:System.Xml.Linq.XElement> ressemble étroitement à la structure du code XML sous-jacent.

## <a name="xelement-constructors"></a>Constructeurs XElement

La classe <xref:System.Xml.Linq.XElement> utilise les constructeurs suivants pour la construction fonctionnelle. Notez qu’il existe d’autres constructeurs pour <xref:System.Xml.Linq.XElement> , mais parce qu’ils ne sont pas utilisés pour la construction fonctionnelle, ils ne sont pas répertoriés ici.

|Constructeur|Description|
|-----------------|-----------------|
|`XElement(XName name, object content)`|Crée un objet <xref:System.Xml.Linq.XElement>. Le paramètre `name` spécifie le nom de l'élément ; `content` spécifie le contenu de l'élément.|
|`XElement(XName name)`|Crée un objet <xref:System.Xml.Linq.XElement> avec son objet <xref:System.Xml.Linq.XName> initialisé au nom spécifié.|
|`XElement(XName name, params object[] content)`|Crée un objet <xref:System.Xml.Linq.XElement> avec son objet <xref:System.Xml.Linq.XName> initialisé au nom spécifié. Les attributs et/ou éléments enfants sont créés à partir du contenu de la liste de paramètres.|

Le paramètre `content` est extrêmement souple. Il prend en charge tout type d’objet qui est un enfant valide d’un <xref:System.Xml.Linq.XElement> . Les règles suivantes s'appliquent à différents types d'objets passés dans ce paramètre :

- Une chaîne est ajoutée en tant que contenu de texte.
- Un objet <xref:System.Xml.Linq.XElement> est ajouté en tant qu'élément enfant.
- Un objet <xref:System.Xml.Linq.XAttribute> est ajouté en tant qu'attribut.
- Un objet <xref:System.Xml.Linq.XProcessingInstruction>, <xref:System.Xml.Linq.XComment> ou <xref:System.Xml.Linq.XText> est ajouté en tant que contenu enfant.
- Un objet <xref:System.Collections.IEnumerable> est énuméré et ces règles sont appliquées de manière récursive aux résultats.
- Pour tout autre type, sa méthode `ToString` est appelée et le résultat est ajouté en tant que contenu texte.

## <a name="example-create-an-xelement-with-content"></a>Exemple : création d’un XElement avec du contenu

Vous pouvez créer un objet <xref:System.Xml.Linq.XElement> qui contient du contenu simple avec un appel de méthode unique. Pour cela, spécifiez le contenu comme second paramètre, comme suit :

```csharp
XElement n = new XElement("Customer", "Adventure Works");
Console.WriteLine(n);
```

Cet exemple produit la sortie suivante :

```xml
<Customer>Adventure Works</Customer>
```

Vous pouvez passer tout type d'objet en tant que contenu. Par exemple, le code suivant crée un élément qui contient un nombre à virgule flottante en tant que contenu :

```csharp
XElement n = new XElement("Cost", 324.50);
Console.WriteLine(n);
```

Cet exemple produit la sortie suivante :

```xml
<Cost>324.5</Cost>
```

Le nombre à virgule flottante est boxed et passé au constructeur. Le nombre boxed est converti en une chaîne et utilisé comme contenu de l'élément.

## <a name="example-create-an-xelement-with-a-child-element"></a>Exemple : créer XElement avec un élément enfant

Si vous passez une instance de la classe <xref:System.Xml.Linq.XElement> comme argument de contenu, le constructeur crée un élément avec un élément enfant :

```csharp
XElement shippingUnit = new XElement("ShippingUnit",
    new XElement("Cost", 324.50)
);
Console.WriteLine(shippingUnit);
```

Cet exemple produit la sortie suivante :

```xml
<ShippingUnit>
  <Cost>324.5</Cost>
</ShippingUnit>
```

## <a name="example-create-an-xelement-with-multiple-child-elements"></a>Exemple : création d’un XElement avec plusieurs éléments enfants

Vous pouvez passer une quantité quelconque d'objets <xref:System.Xml.Linq.XElement> comme contenu. Chacun des objets <xref:System.Xml.Linq.XElement> est inclus en tant qu'élément enfant.

```csharp
XElement address = new XElement("Address",
    new XElement("Street1", "123 Main St"),
    new XElement("City", "Mercer Island"),
    new XElement("State", "WA"),
    new XElement("Postal", "68042")
);
Console.WriteLine(address);
```

Cet exemple produit la sortie suivante :

```xml
<Address>
  <Street1>123 Main St</Street1>
  <City>Mercer Island</City>
  <State>WA</State>
  <Postal>68042</Postal>
</Address>
```

En étendant l’exemple précédent, vous pouvez créer une arborescence XML entière, comme suit :

```csharp
XElement contacts =
    new XElement("Contacts",
        new XElement("Contact",
            new XElement("Name", "Patrick Hines"),
            new XElement("Phone", "206-555-0144"),
            new XElement("Address",
                new XElement("Street1", "123 Main St"),
                new XElement("City", "Mercer Island"),
                new XElement("State", "WA"),
                new XElement("Postal", "68042")
            )
        )
    );
Console.WriteLine(contacts);
```

Cet exemple produit la sortie suivante :

```xml
<Contacts>
  <Contact>
    <Name>Patrick Hines</Name>
    <Phone>206-555-0144</Phone>
    <Address>
      <Street1>123 Main St</Street1>
      <City>Mercer Island</City>
      <State>WA</State>
      <Postal>68042</Postal>
    </Address>
  </Contact>
</Contacts>
```

## <a name="example-create-an-xelement-with-an-xattribute"></a>Exemple : créer XElement avec un XAttribute

Si vous passez une instance de la classe <xref:System.Xml.Linq.XAttribute> comme argument de contenu, le constructeur crée un élément avec un attribut :

```csharp
XElement phone = new XElement("Phone",
    new XAttribute("Type", "Home"),
    "555-555-5555");
Console.WriteLine(phone);
```

Cet exemple produit la sortie suivante :

```xml
<Phone Type="Home">555-555-5555</Phone>
```

## <a name="example-create-an-empty-element"></a>Exemple : créer un élément vide

Pour créer un vide <xref:System.Xml.Linq.XElement> , ne transmettez pas de contenu au constructeur. L'exemple suivant crée un élément vide :

```csharp
XElement n = new XElement("Customer");
Console.WriteLine(n);
```

Cet exemple produit la sortie suivante :

```xml
<Customer />
```

## <a name="example-attach-vs-clone"></a>Exemple : attacher et cloner

Comme mentionné précédemment, lors de l’ajout d’objets <xref:System.Xml.Linq.XNode> (y compris <xref:System.Xml.Linq.XElement>) ou <xref:System.Xml.Linq.XAttribute>, si le contenu n’a pas de parent, les objets sont simplement attachés à l’arborescence XML. Si le nouveau contenu a déjà un parent et fait partie d’une autre arborescence XML, il est cloné et le nouveau contenu cloné est attaché à l’arborescence XML.

L’exemple suivant illustre le comportement lorsque vous ajoutez un élément apparenté à une arborescence et lorsque vous ajoutez un élément sans parent à une arborescence :

```csharp
// Create a tree with a child element.
XElement xmlTree1 = new XElement("Root",
    new XElement("Child1", 1)
);

// Create an element that's not parented.
XElement child2 = new XElement("Child2", 2);

// Create a tree and add Child1 and Child2 to it.
XElement xmlTree2 = new XElement("Root",
    xmlTree1.Element("Child1"),
    child2
);

// Compare Child1 identity.
Console.WriteLine("Child1 was {0}",
    xmlTree1.Element("Child1") == xmlTree2.Element("Child1") ?
    "attached" : "cloned");

// Compare Child2 identity.
Console.WriteLine("Child2 was {0}",
    child2 == xmlTree2.Element("Child2") ?
    "attached" : "cloned");

// This example produces the following output:
//    Child1 was cloned
//    Child2 was attached
```

## <a name="see-also"></a>Voir aussi

- [Construction fonctionnelle](functional-construction.md)
