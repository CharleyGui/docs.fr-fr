---
title: Vue d’ensemble de LINQ to XML (C#)
ms.date: 10/30/2018
ms.assetid: 716b94d3-0091-4de1-8e05-41bc069fa9dd
ms.openlocfilehash: a9435027a7487af96227fdc7a0eae6f511d82b23
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66484350"
---
# <a name="linq-to-xml-overview-c"></a>Vue d’ensemble de LINQ to XML (C#)

LINQ to XML fournit une interface de programmation XML en mémoire qui exploite le framework LINQ (Language-Integrated Query) de .NET. LINQ to XML utilise les capacités .NET et s’apparente à une interface de programmation XML DOM (Document Object Model) améliorée et mise à jour. 
 
Le langage XML a été largement adopté comme méthode pour mettre en forme des données dans de nombreux contextes. Par exemple, on trouve du code XML sur le Web, dans les fichiers de configuration, dans les fichiers Microsoft Office Word et dans les bases de données.

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] est une approche à jour et repensée de la programmation avec XML. Elle propose les fonctionnalités de modification des documents en mémoire du modèle DOM (Document Objet Model) et prend en charge les expressions de requête [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]. Bien que ces expressions de requête soient syntaxiquement différentes de XPath, elles procurent la même fonctionnalité.

## <a name="linq-to-xml-developers"></a>Développeurs LINQ to XML

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] cible un large éventail de développeurs. Pour un développeur qui souhaite simplement se faciliter la tâche, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] rend le XML plus abordable en fournissant une expérience de requête semblable à SQL. Un rapide apprentissage permettra aux programmeurs d'écrire des requêtes succinctes et puissantes dans le langage de programmation de leur choix.

Les développeurs professionnels peuvent utiliser [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] pour accroître considérablement leur productivité. Avec [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], ils peuvent écrire moins de code qui est plus expressif, plus compact et plus puissant. Ils peuvent utiliser simultanément des expressions de requête de plusieurs domaines de données.

## <a name="what-is-linq-to-xml"></a>Qu'est-ce que LINQ to XML ?

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] est une interface de programmation XML prenant en charge LINQ qui vous permet de travailler avec du code XML dans les langages de programmation .NET Framework.

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] s’apparente au modèle DOM en ce sens qu’il place le document XML en mémoire. Vous pouvez interroger et modifier le document, et après l'avoir modifié, vous pouvez l'enregistrer dans un fichier ou le sérialiser et l'envoyer via Internet. Cependant, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] diffère du modèle DOM : il fournit un nouveau modèle objet qui est plus léger et plus facile à manipuler, et qui tire parti des fonctionnalités du langage C#.

Le principal avantage de [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] est son intégration avec [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]. Cette intégration vous permet d'écrire des requêtes sur le document XML en mémoire afin de récupérer des collections d'éléments et d'attributs. La capacité de requête de [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] est comparable en terme de fonctionnalités (mais pas en termes de syntaxe) à XQuery et XPath. L’intégration de [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dans C# fournit un typage plus fort, la vérification au moment de la compilation et une prise en charge améliorée du débogueur.

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] présente également l'avantage de pouvoir utiliser des résultats de requête en tant que paramètres de constructeurs d'objets <xref:System.Xml.Linq.XElement> et <xref:System.Xml.Linq.XAttribute>, ce qui constitue une approche puissante pour la création d'arborescences XML. Cette approche, appelée *construction fonctionnelle*, permet aux développeurs de transformer facilement des arborescences XML d’une forme en une autre.

Par exemple, vous pouvez avoir un bon de commande XML standard comme décrit dans [Exemple de fichier XML : Commande fournisseur standard (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml-1.md). En utilisant [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], vous pourriez exécuter la requête suivante afin d'obtenir la valeur d'attribut de numéro de référence pour chaque élément de la commande fournisseur :

```csharp
// Load the XML file from our project directory containing the purchase orders
var filename = "PurchaseOrder.xml";
var currentDirectory = Directory.GetCurrentDirectory();
var purchaseOrderFilepath = Path.Combine(currentDirectory, filename);

XElement purchaseOrder = XElement.Load($"{purchaseOrderFilepath}");

IEnumerable<string> partNos =  from item in purchaseOrder.Descendants("Item")
                               select (string) item.Attribute("PartNumber");
```

Vous pouvez réécrire ceci sous forme d’une syntaxe de méthode :

```csharp
IEnumerable<string> partNos = purchaseOrder.Descendants("Item").Select(x => (string) x.Attribute("PartNumber"));
```

Vous pourriez également, si vous le souhaitez, générer une liste des éléments avec une valeur supérieure à $ 100, triés par numéro de référence. Pour obtenir ces informations, vous pourriez exécuter la requête suivante :

```csharp
// Load the XML file from our project directory containing the purchase orders
var filename = "PurchaseOrder.xml";
var currentDirectory = Directory.GetCurrentDirectory();
var purchaseOrderFilepath = Path.Combine(currentDirectory, filename);

XElement purchaseOrder = XElement.Load($"{purchaseOrderFilepath}");

IEnumerable<XElement> pricesByPartNos =  from item in purchaseOrder.Descendants("Item")
                                 where (int) item.Element("Quantity") * (decimal) item.Element("USPrice") > 100
                                 orderby (string)item.Element("PartNumber")
                                 select item;
```

Vous pouvez aussi réécrire ceci sous forme d’une syntaxe de méthode :

```csharp
IEnumerable<XElement> pricesByPartNos = purchaseOrder.Descendants("Item")
                                        .Where(item => (int)item.Element("Quantity") * (decimal)item.Element("USPrice") > 100)
                                        .OrderBy(order => order.Element("PartNumber"));
```

Outre ces fonctionnalités [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] fournit une interface de programmation XML améliorée. Grâce à [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], vous pouvez :

- charger du code XML à partir de [fichiers](how-to-load-xml-from-a-file.md) ou de [flux](how-to-stream-xml-fragments-from-an-xmlreader.md) ;

- sérialiser du code XML vers des fichiers ou des flux ;

- créer du code XML à partir de zéro à l'aide de la construction fonctionnelle ;

- interroger du code XML à l'aide d'axes de type XPath ;

- manipuler l'arborescence XML en mémoire à l'aide de méthodes telles que <xref:System.Xml.Linq.XContainer.Add%2A>, <xref:System.Xml.Linq.XNode.Remove%2A>, <xref:System.Xml.Linq.XNode.ReplaceWith%2A> et <xref:System.Xml.Linq.XElement.SetValue%2A> ;

- valider des arborescences XML à l'aide de XSD ;

- utiliser une combinaison de ces fonctionnalités pour transformer des arborescences XML d'une forme à une autre.

## <a name="creating-xml-trees"></a>Création d'arborescences XML

Un des principaux avantages liés à la programmation avec [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] tient à la facilité de création d’arborescences XML. Par exemple, pour créer une petite arborescence XML, vous pouvez écrire du code comme suit :

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

Pour plus d’informations, consultez [Création d’arborescences XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md).

## <a name="see-also"></a>Voir aussi

- [Référence (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/reference-linq-to-xml.md)
- [LINQ to XML, différences par rapport à DOM (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-vs-dom.md)
- [LINQ to XML, différences par rapport à d’autres technologies XML](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-vs-other-xml-technologies.md)
- <xref:System.Xml.Linq>
