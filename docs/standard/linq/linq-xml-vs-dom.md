---
title: LINQ to XML, différences par rapport à DOM
description: Il existe des différences clés entre LINQ to XML et DOM. LINQ to XML prend en charge la construction fonctionnelle et les littéraux XML, qui illustrent mieux la structure des arborescences XML qu’ils génèrent.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 51c0e3d2-c047-4e6a-a423-d61a882400b7
ms.openlocfilehash: 905fe1b47361e2b96c79bc56cb831b3cb298e4de
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553324"
---
# <a name="linq-to-xml-vs-dom"></a>LINQ to XML, différences par rapport à DOM

Cet article décrit quelques-unes des principales différences entre LINQ to XML et l’API de programmation XML prédominante actuelle, le W3C Document Object Model (DOM).

## <a name="new-ways-to-construct-xml-trees"></a>Nouvelles manières de construire des arborescences XML

Dans le modèle DOM W3C, vous construisez une arborescence XML de bas en haut ; autrement dit, vous créez un document, vous créez des éléments, puis vous ajoutez les éléments au document.

Par exemple, l’exemple suivant utilise un moyen classique de créer une arborescence XML à l’aide de l’implémentation Microsoft du modèle DOM, <xref:System.Xml.XmlDocument> .

```csharp
XmlDocument doc = new XmlDocument();
XmlElement name = doc.CreateElement("Name");
name.InnerText = "Patrick Hines";
XmlElement phone1 = doc.CreateElement("Phone");
phone1.SetAttribute("Type", "Home");
phone1.InnerText = "206-555-0144";
XmlElement phone2 = doc.CreateElement("Phone");
phone2.SetAttribute("Type", "Work");
phone2.InnerText = "425-555-0145";
XmlElement street1 = doc.CreateElement("Street1");
street1.InnerText = "123 Main St";
XmlElement city = doc.CreateElement("City");
city.InnerText = "Mercer Island";
XmlElement state = doc.CreateElement("State");
state.InnerText = "WA";
XmlElement postal = doc.CreateElement("Postal");
postal.InnerText = "68042";
XmlElement address = doc.CreateElement("Address");
address.AppendChild(street1);
address.AppendChild(city);
address.AppendChild(state);
address.AppendChild(postal);
XmlElement contact = doc.CreateElement("Contact");
contact.AppendChild(name);
contact.AppendChild(phone1);
contact.AppendChild(phone2);
contact.AppendChild(address);
XmlElement contacts = doc.CreateElement("Contacts");
contacts.AppendChild(contact);
doc.AppendChild(contacts);
```

```vb
Dim doc As XmlDocument = New XmlDocument()
Dim name As XmlElement = doc.CreateElement("Name")
name.InnerText = "Patrick Hines"
Dim phone1 As XmlElement = doc.CreateElement("Phone")
phone1.SetAttribute("Type", "Home")
phone1.InnerText = "206-555-0144"
Dim phone2 As XmlElement = doc.CreateElement("Phone")
phone2.SetAttribute("Type", "Work")
phone2.InnerText = "425-555-0145"
Dim street1 As XmlElement = doc.CreateElement("Street1")
street1.InnerText = "123 Main St"
Dim city As XmlElement = doc.CreateElement("City")
city.InnerText = "Mercer Island"
Dim state As XmlElement = doc.CreateElement("State")
state.InnerText = "WA"
Dim postal As XmlElement = doc.CreateElement("Postal")
postal.InnerText = "68042"
Dim address As XmlElement = doc.CreateElement("Address")
address.AppendChild(street1)
address.AppendChild(city)
address.AppendChild(state)
address.AppendChild(postal)
Dim contact As XmlElement = doc.CreateElement("Contact")
contact.AppendChild(name)
contact.AppendChild(phone1)
contact.AppendChild(phone2)
contact.AppendChild(address)
Dim contacts As XmlElement = doc.CreateElement("Contacts")
contacts.AppendChild(contact)
doc.AppendChild(contacts)
Console.WriteLine(doc.OuterXml)
```

Ce style de codage masque la structure de l’arborescence XML. LINQ to XML prend également en charge une autre approche, la *construction fonctionnelle*, qui illustre mieux la structure. Cette approche peut être effectuée avec les <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XAttribute> constructeurs et. Dans Visual Basic, elle peut également être effectuée à l’aide de littéraux XML. Cet exemple illustre la construction de la même arborescence XML à l’aide de la construction fonctionnelle :

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
Dim contacts = _
    <Contacts>
        <Contact>
            <Name>Patrick Hines</Name>
            <Phone Type="Home">206-555-0144</Phone>
            <Phone Type="Work">425-555-0145</Phone>
            <Address>
                <Street1>123 Main St</Street1>
                <City>Mercer Island</City>
                <State>WA</State>
                <Postal>68042</Postal>
            </Address>
        </Contact>
    </Contacts>
```

Notez que la mise en retrait du code pour construire l’arborescence XML affiche la structure des données XML sous-jacentes. La version Visual Basic utilise des littéraux XML.

Pour plus d’informations, consultez [arborescences XML](functional-construction.md).

## <a name="work-directly-with-xml-elements"></a>Travailler directement avec des éléments XML

Lorsque vous programmez avec des données XML, vous travaillez en général principalement avec les éléments XML et éventuellement les attributs. Dans LINQ to XML, vous pouvez travailler directement avec des éléments et des attributs XML. Vous pouvez par exemple effectuer les opérations suivantes :

- Créer des éléments XML sans utiliser d'objet de document. Cela simplifie la programmation lorsque vous devez travailler avec des fragments d'arborescences XML.
- Charger des objets `T:System.Xml.Linq.XElement` directement à partir d'un fichier XML.
- Sérialiser des objets `T:System.Xml.Linq.XElement` dans un fichier ou un flux.

Comparez cela au modèle DOM W3C, dans lequel le document XML est utilisé en tant que conteneur logique pour l'arborescence XML. Dans le modèle DOM, les nœuds XML, y compris les éléments et attributs, doivent être créés dans le contexte d'un document XML. Voici un fragment de code pour créer un élément de nom dans le modèle DOM :

```csharp
XmlDocument doc = new XmlDocument();
XmlElement name = doc.CreateElement("Name");
name.InnerText = "Patrick Hines";
doc.AppendChild(name);
```

```vb
Dim doc As XmlDocument = New XmlDocument()
Dim name As XmlElement = doc.CreateElement("Name")
name.InnerText = "Patrick Hines"
doc.AppendChild(name)
```

Si vous souhaitez utiliser un élément dans plusieurs documents, vous devez importer les nœuds d'un document à un autre. LINQ to XML évite cette couche de complexité.

Lors de l'utilisation de LINQ to XML, vous utilisez la classe <xref:System.Xml.Linq.XDocument> uniquement si vous souhaitez ajouter un commentaire ou une information de traitement au niveau racine du document.

## <a name="simplified-handling-of-names-and-namespaces"></a>Gestion simplifiée des noms et des espaces de noms

La gestion des noms, des espaces de noms et des préfixes d'espaces de noms est généralement un aspect complexe de la programmation XML. LINQ to XML simplifie les noms et les espaces de noms en éliminant la nécessité de gérer les préfixes d’espaces de noms. Vous pouvez si vous le souhaitez contrôler les préfixes d'espaces de noms. Toutefois, si vous décidez de ne pas contrôler explicitement les préfixes d’espaces de noms, LINQ to XML affectera des préfixes d’espaces de noms lors de la sérialisation s’ils sont requis, ou sérialisera à l’aide des espaces de noms par défaut si ce n’est pas le cas. Si des espaces de noms par défaut sont utilisés, il n'y aura pas de préfixes d'espaces de noms dans le document résultant. Pour plus d’informations, consultez [vue d’ensemble des espaces de noms](namespaces-overview.md).

Un autre problème lié au modèle DOM est qu’il ne vous permet pas de modifier le nom d’un nœud. Au lieu de cela, vous devez créer un nouveau nœud et y copier tous les nœuds enfants, perdant ainsi l'identité de nœud d'origine. LINQ to XML évite ce problème en vous permettant de définir la <xref:System.Xml.Linq.XName> propriété sur un nœud.

## <a name="static-method-support-for-loading-xml"></a>Prise en charge des méthodes statiques pour le chargement XML

LINQ to XML vous permet de charger du code XML à l’aide de méthodes statiques, au lieu de méthodes d’instance. Cela simplifie le chargement et l'analyse. Pour plus d’informations, consultez [Comment charger du code XML à partir d’un fichier](load-xml-file.md).

## <a name="removal-of-support-for-dtd-constructs"></a>Suppression de la prise en charge des constructions DTD

LINQ to XML simplifie davantage la programmation XML en supprimant la prise en charge des entités et des références d’entité. La gestion des entités est complexe et rarement utilisée. La suppression de leur prise en charge augmente les performances et simplifie l'interface de programmation. Quand une arborescence de LINQ to XML est remplie, toutes les entités DTD sont développées.

## <a name="support-for-fragments"></a>Prise en charge des fragments

LINQ to XML ne fournit pas d’équivalent pour la `XmlDocumentFragment` classe. Dans de nombreux cas, toutefois, le `XmlDocumentFragment` concept peut être géré par le résultat d’une requête typée à partir <xref:System.Collections.Generic.IEnumerable%601> de <xref:System.Xml.Linq.XNode> ou <xref:System.Collections.Generic.IEnumerable%601> de <xref:System.Xml.Linq.XElement> .

## <a name="support-for-xpathnavigator"></a>Prise en charge de XPathNavigator

LINQ to XML assure la prise en charge de <xref:System.Xml.XPath.XPathNavigator> via des méthodes d’extension dans l' <xref:System.Xml.XPath?displayProperty=nameWithType> espace de noms. Pour plus d'informations, consultez <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.

## <a name="support-for-white-space-and-indentation"></a>Prise en charge des espaces blancs et de la mise en retrait

LINQ to XML gère l’espace blanc plus simplement que le modèle DOM.

Un scénario courant consiste à lire le code XML mis en retrait, à créer une arborescence XML en mémoire sans nœuds d’espace blanc (autrement dit, ne pas conserver les espaces), à effectuer certaines opérations sur le code XML, puis à enregistrer le code XML avec mise en retrait. Lorsque vous sérialisez le code XML avec mise en forme, seuls les espaces significatifs dans l'arborescence XML sont conservés. Il s’agit du comportement par défaut pour LINQ to XML.

Un autre scénario courant consiste à lire et à modifier du code XML qui a déjà été intentionnellement mis en retrait. Vous ne souhaiterez peut-être modifier cette mise en retrait en aucune manière. Dans LINQ to XML, vous pouvez effectuer les opérations suivantes :

- Conserver les espaces lorsque vous chargez ou analysez le XML.
- Désactivation de la mise en forme lors de la sérialisation du code XML.

LINQ to XML stocke les espaces en tant que <xref:System.Xml.Linq.XText> nœud, au lieu d’avoir un <xref:System.Xml.XmlNodeType.Whitespace> type de nœud spécialisé, comme le fait le DOM.

## <a name="support-for-annotations"></a>Prise en charge des annotations

Les éléments LINQ to XML prennent en charge un ensemble extensible d’annotations. Cela est utile pour assurer le suivi de diverses informations relatives à un élément, telles que des informations de schéma, le fait que l'élément soit lié à une interface utilisateur ou tout autre type d'informations spécifiques aux applications. Pour plus d’informations, consultez [LINQ to XML annotations](linq-xml-annotations.md).

## <a name="support-for-schema-information"></a>Prise en charge des informations de schéma

LINQ to XML assure la prise en charge de la validation XSD via des méthodes d’extension dans l' <xref:System.Xml.Schema?displayProperty=nameWithType> espace de noms. Vous pouvez valider la conformité d’une arborescence XML à un schéma XSD. Vous pouvez remplir l’arborescence XML avec le PSVI (Post-Schema-Validation Infoset). Pour plus d’informations, consultez [Comment valider à l’aide de XSD](validate-xsd.md) et <xref:System.Xml.Schema.Extensions> .

## <a name="see-also"></a>Voir aussi

- [Présentation de LINQ to XML](linq-xml-overview.md)
