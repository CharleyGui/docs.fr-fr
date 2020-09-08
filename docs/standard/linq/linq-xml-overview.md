---
title: Vue d’ensemble-LINQ to XML
description: LINQ to XML fournit une interface de programmation XML en mémoire qui est basée sur les fonctionnalités de .NET et comparable à une API DOM mise à jour.
ms.date: 10/30/2018
dev_langs:
- csharp
- vb
ms.assetid: 716b94d3-0091-4de1-8e05-41bc069fa9dd
ms.openlocfilehash: f805d757c9059a07988c6cb16e41ffed017fe853
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553356"
---
# <a name="linq-to-xml-overview"></a>Présentation de LINQ to XML

LINQ to XML fournit une interface de programmation XML en mémoire qui exploite le framework LINQ (Language-Integrated Query) de .NET. LINQ to XML utilise les capacités .NET et s’apparente à une interface de programmation XML DOM (Document Object Model) améliorée et mise à jour.

Le langage XML a été largement adopté comme méthode pour mettre en forme des données dans de nombreux contextes. Par exemple, on trouve du code XML sur le Web, dans les fichiers de configuration, dans les fichiers Microsoft Office Word et dans les bases de données.

LINQ to XML est une approche à jour et repensée de la programmation avec XML. Il fournit les fonctionnalités de modification de document en mémoire du Document Object Model (DOM) et prend en charge les expressions de requête LINQ. Bien que ces expressions de requête soient syntaxiquement différentes de XPath, elles procurent la même fonctionnalité.

## <a name="linq-to-xml-developers"></a>LINQ to XML les développeurs

LINQ to XML cible un large éventail de développeurs. Pour un développeur en moyenne qui souhaite simplement faire un travail, LINQ to XML facilite le XML en fournissant une expérience de requête similaire à SQL. Un rapide apprentissage permettra aux programmeurs d'écrire des requêtes succinctes et puissantes dans le langage de programmation de leur choix.

Les développeurs professionnels peuvent utiliser LINQ to XML pour augmenter leur productivité de façon considérable. Avec LINQ to XML, ils peuvent écrire moins de code qui est plus expressif, plus compact et plus puissant. Ils peuvent utiliser simultanément des expressions de requête de plusieurs domaines de données.

## <a name="linq-to-xml-is-an-xml-programming-interface"></a>LINQ to XML est une interface de programmation XML

LINQ to XML est une interface de programmation XML en mémoire compatible avec LINQ qui vous permet d’utiliser XML à partir des langages de programmation .NET.

LINQ to XML est semblable au Document Object Model (DOM) dans le fait qu’il remet le document XML en mémoire. Vous pouvez interroger et modifier le document, et après l'avoir modifié, vous pouvez l'enregistrer dans un fichier ou le sérialiser et l'envoyer via Internet. Toutefois, LINQ to XML diffère de DOM :

- Il fournit un nouveau modèle objet qui est plus léger et plus facile à utiliser.
- Elle tire parti des fonctionnalités de langage en C# et Visual Basic.

L’avantage le plus important de LINQ to XML est son intégration à LINQ (Language-Integrated Query). Cette intégration vous permet d'écrire des requêtes sur le document XML en mémoire afin de récupérer des collections d'éléments et d'attributs. La fonctionnalité de requête de LINQ to XML est comparable dans les fonctionnalités (mais pas dans la syntaxe) à XPath et XQuery. L’intégration de LINQ en C# et Visual Basic fournit un typage plus fort, une vérification au moment de la compilation et une prise en charge améliorée du débogueur.

Un autre avantage de LINQ to XML est la possibilité d’utiliser les résultats de requête en tant que paramètres pour <xref:System.Xml.Linq.XElement> et les <xref:System.Xml.Linq.XAttribute> constructeurs d’objets permet une approche puissante de la création d’arborescences XML. Cette approche, appelée *construction fonctionnelle*, permet aux développeurs de transformer facilement des arborescences XML d’une forme en une autre.

Par exemple, vous pouvez avoir un bon de commande XML standard, comme décrit dans [exemple de fichier XML : bon de commande standard](sample-xml-file-typical-purchase-order.md). À l’aide de LINQ to XML, vous pouvez exécuter la requête suivante pour obtenir la valeur de l’attribut de numéro de référence pour chaque élément item dans le bon de commande :

```csharp
// Load the XML file from our project directory containing the purchase orders
var filename = "PurchaseOrder.xml";
var currentDirectory = Directory.GetCurrentDirectory();
var purchaseOrderFilepath = Path.Combine(currentDirectory, filename);

XElement purchaseOrder = XElement.Load(purchaseOrderFilepath);

IEnumerable<string> partNos =  from item in purchaseOrder.Descendants("Item")
                               select (string) item.Attribute("PartNumber");
```

```vb
' Load the XML file from our project directory containing the purchase orders
Dim filename = "PurchaseOrder.xml"
Dim currentDirectory = Directory.GetCurrentDirectory()
Dim purchaseOrderFilepath = Path.Combine(currentDirectory, filename)

Dim purchaseOrder As XElement = XElement.Load(purchaseOrderFilepath)

Dim partNos = _
    From item In purchaseOrder...<Item> _
    Select item.@PartNumber
```

En C#, cela peut être réécrit dans la syntaxe de la méthode :

```csharp
IEnumerable<string> partNos = purchaseOrder.Descendants("Item").Select(x => (string) x.Attribute("PartNumber"));
```

Vous pourriez également, si vous le souhaitez, générer une liste des éléments avec une valeur supérieure à $ 100, triés par numéro de référence. Pour obtenir ces informations, vous pourriez exécuter la requête suivante :

```csharp
// Load the XML file from our project directory containing the purchase orders
var filename = "PurchaseOrder.xml";
var currentDirectory = Directory.GetCurrentDirectory();
var purchaseOrderFilepath = Path.Combine(currentDirectory, filename);

XElement purchaseOrder = XElement.Load(purchaseOrderFilepath);

IEnumerable<XElement> pricesByPartNos =  from item in purchaseOrder.Descendants("Item")
                                 where (int) item.Element("Quantity") * (decimal) item.Element("USPrice") > 100
                                 orderby (string)item.Element("PartNumber")
                                 select item;
```

```vb
' Load the XML file from our project directory containing the purchase orders
Dim filename = "PurchaseOrder.xml"
Dim currentDirectory = Directory.GetCurrentDirectory()
Dim purchaseOrderFilepath = Path.Combine(currentDirectory, filename)

Dim purchaseOrder As XElement = XElement.Load(purchaseOrderFilepath)

Dim partNos = _
From item In purchaseOrder...<Item> _
Where (item.<Quantity>.Value * _
       item.<USPrice>.Value) > 100 _
Order By item.<PartNumber>.Value _
Select item
```

Là encore, en C#, cela peut être réécrit dans la syntaxe de la méthode :

```csharp
IEnumerable<XElement> pricesByPartNos = purchaseOrder.Descendants("Item")
                                        .Where(item => (int)item.Element("Quantity") * (decimal)item.Element("USPrice") > 100)
                                        .OrderBy(order => order.Element("PartNumber"));
```

Outre ces fonctionnalités LINQ, LINQ to XML fournit une interface de programmation XML améliorée. À l’aide de LINQ to XML, vous pouvez :

- Charger du code XML à partir de [fichiers](load-xml-file.md) ou de [flux](stream-xml-fragments-xmlreader.md).
- sérialiser du code XML vers des fichiers ou des flux ;
- créer du code XML à partir de zéro à l'aide de la construction fonctionnelle ;
- interroger du code XML à l’aide d’axes de type XPath ;
- manipuler l'arborescence XML en mémoire à l'aide de méthodes telles que <xref:System.Xml.Linq.XContainer.Add%2A>, <xref:System.Xml.Linq.XNode.Remove%2A>, <xref:System.Xml.Linq.XNode.ReplaceWith%2A> et <xref:System.Xml.Linq.XElement.SetValue%2A> ;
- valider des arborescences XML à l'aide de XSD ;
- utiliser une combinaison de ces fonctionnalités pour transformer des arborescences XML d'une forme à une autre.

## <a name="create-xml-trees"></a>Créer des arborescences XML

L’un des avantages les plus significatifs de la programmation avec LINQ to XML est qu’il est facile de créer des arborescences XML. Par exemple, pour créer une petite arborescence XML, vous pouvez écrire du code comme suit :

```csharp
XElement contacts =
new XElement("Contacts",
    new XElement("Contact",
        new XElement("Name", "Patrick Hines"),
        new XElement("Phone", "206-555-0144",
            new XAttribute("Type", "Home")),
        new XElement("phone", "425-555-0145",
            new XAttribute("Type", "Work")),
        new XElement("Address",
            new XElement("Street1", "123 Main St"),
            new XElement("City", "Mercer Island"),
            new XElement("State", "WA"),
            new XElement("Postal", "68042")
        )
    )
);
```

```vb
Dim contacts As XElement = _
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

> [!NOTE]
> La version Visual Basic de l’exemple utilise des littéraux XML. Vous pouvez également utiliser <xref:System.Xml.Linq.XElement> dans Visual Basic, comme dans la version C#.

Pour plus d’informations, consultez [arborescences XML](functional-construction.md).

## <a name="see-also"></a>Voir aussi

- [Référence](reference.md)
- [LINQ to XML, différences par rapport à DOM](linq-xml-vs-dom.md)
- [LINQ to XML différences par rapport à d’autres technologies XML](linq-xml-vs-xml-technologies.md)
- <xref:System.Xml.Linq>
