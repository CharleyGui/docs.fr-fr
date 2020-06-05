---
title: LINQ to XML, différences par rapport à DOM
ms.date: 07/20/2015
ms.assetid: 18c36130-d598-40b7-9007-828232252978
ms.openlocfilehash: 5813ca410e3e2b1ec284681451d0c0cec6f5e393
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84389330"
---
# <a name="linq-to-xml-vs-dom-visual-basic"></a>LINQ to XML et DOM (Visual Basic)
Cette section décrit certaines des principales différences entre [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] et l’API de programmation XML actuellement prédominante, le modèle DOM (Document Object Model) W3C.  
  
## <a name="new-ways-to-construct-xml-trees"></a>Nouvelles manières de construire des arborescences XML  
 Dans le modèle DOM W3C, vous construisez une arborescence XML de bas en haut ; autrement dit, vous créez un document, vous créez des éléments, puis vous ajoutez les éléments au document.  
  
 Voici un exemple typique de création d’une arborescence XML à l’aide de l’implémentation Microsoft du modèle DOM, <xref:System.Xml.XmlDocument> :  
  
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
  
 Ce style de codage ne fournit visuellement que peu d’informations concernant la structure de l’arborescence XML. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] prend en charge cette approche de la construction d’une arborescence XML, mais également une approche alternative, la *construction fonctionnelle*. Dans Visual Basic, la construction fonctionnelle utilise des littéraux XML pour générer une arborescence XML.  
  
 Voici comment vous pouvez construire la même arborescence XML à l’aide de la construction fonctionnelle [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] :  
  
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
  
 Notez que la mise en retrait du code pour construire l’arborescence XML affiche la structure des données XML sous-jacentes.  
  
 Pour plus d’informations, consultez [création d’arborescences XML (Visual Basic)](creating-xml-trees.md).  
  
## <a name="working-directly-with-xml-elements"></a>Utilisation directe des éléments XML  
 Lorsque vous programmez avec des données XML, vous travaillez en général principalement avec les éléments XML et éventuellement les attributs. Dans [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], vous pouvez utiliser directement les éléments et les attributs XML. Vous pouvez par exemple effectuer les opérations suivantes :  
  
- Créer des éléments XML sans utiliser d'objet de document. Cela simplifie la programmation lorsque vous devez travailler avec des fragments d'arborescences XML.  
  
- Charger des objets `T:System.Xml.Linq.XElement` directement à partir d'un fichier XML.  
  
- Sérialiser des objets `T:System.Xml.Linq.XElement` dans un fichier ou un flux.  
  
 Comparez cela au modèle DOM W3C, dans lequel le document XML est utilisé en tant que conteneur logique pour l'arborescence XML. Dans le modèle DOM, les nœuds XML, y compris les éléments et attributs, doivent être créés dans le contexte d'un document XML. Voici un fragment de code permettant de créer un élément de nom dans le modèle DOM :  
  
```vb  
Dim doc As XmlDocument = New XmlDocument()  
Dim name As XmlElement = doc.CreateElement("Name")  
name.InnerText = "Patrick Hines"  
doc.AppendChild(name)  
```  
  
 Si vous souhaitez utiliser un élément dans plusieurs documents, vous devez importer les nœuds d'un document à un autre. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] évite cette couche de complexité.  
  
 Lors de l'utilisation de LINQ to XML, vous utilisez la classe <xref:System.Xml.Linq.XDocument> uniquement si vous souhaitez ajouter un commentaire ou une information de traitement au niveau racine du document.  
  
## <a name="simplified-handling-of-names-and-namespaces"></a>Gestion simplifiée des noms et des espaces de noms  
 La gestion des noms, des espaces de noms et des préfixes d'espaces de noms est généralement un aspect complexe de la programmation XML. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] simplifie les noms et les espaces de noms en éliminant la nécessité de gérer les préfixes d’espaces de noms. Vous pouvez si vous le souhaitez contrôler les préfixes d'espaces de noms. Si vous décidez cependant de ne pas contrôler explicitement les préfixes d’espaces de noms, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] affecte des préfixes d’espaces de noms lors de la sérialisation s’ils sont nécessaires ou, s’ils ne le sont pas, sérialise en utilisant les espaces de noms par défaut. Si des espaces de noms par défaut sont utilisés, il n'y aura pas de préfixes d'espaces de noms dans le document résultant. Pour plus d’informations, consultez [vue d’ensemble des espaces de noms (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).  
  
 L'un des autres problèmes associés au modèle DOM est qu'il ne vous permet pas de modifier le nom d'un nœud. Au lieu de cela, vous devez créer un nouveau nœud et y copier tous les nœuds enfants, perdant ainsi l'identité de nœud d'origine. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] évite ce problème en vous permettant de définir la propriété <xref:System.Xml.Linq.XName> sur un nœud.  
  
## <a name="static-method-support-for-loading-xml"></a>Prise en charge des méthodes statiques pour le chargement de données XML  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] vous permet de charger du code XML en utilisant des méthodes statiques au lieu de méthodes d’instance. Cela simplifie le chargement et l'analyse. Pour plus d’informations, consultez [Comment : charger du code XML à partir d’un fichier (Visual Basic)](how-to-load-xml-from-a-file.md).  
  
## <a name="removal-of-support-for-dtd-constructs"></a>Suppression de la prise en charge des constructions de DTD  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] simplifie la programmation XML en supprimant la prise en charge des entités et des références d'entités. La gestion des entités est complexe et rarement utilisée. La suppression de leur prise en charge augmente les performances et simplifie l'interface de programmation. Quand une arborescence [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] est remplie, toutes les entités DTD sont développées.  
  
## <a name="support-for-fragments"></a>Prise en charge des fragments  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ne fournit pas d’équivalent pour la classe `XmlDocumentFragment`. Dans de nombreux cas, cependant, le concept de `XmlDocumentFragment` peut être géré par le résultat d’une requête typée <xref:System.Collections.Generic.IEnumerable%601> de <xref:System.Xml.Linq.XNode> ou <xref:System.Collections.Generic.IEnumerable%601> de <xref:System.Xml.Linq.XElement>.  
  
## <a name="support-for-xpathnavigator"></a>Prise en charge de XPathNavigator  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] fournit une prise en charge pour <xref:System.Xml.XPath.XPathNavigator> via les méthodes d’extension de l’espace de noms <xref:System.Xml.XPath?displayProperty=nameWithType>. Pour plus d’informations, consultez <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.  
  
## <a name="support-for-white-space-and-indentation"></a>Prise en charge des espaces blancs et de la mise en retrait  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] gère les espaces plus simplement que le modèle DOM.  
  
 Un scénario courant consiste à lire le code XML mis en retrait, à créer une arborescence XML en mémoire sans nœuds d'espaces (autrement dit, ne pas conserver les espaces), à effectuer certaines opérations sur le code XML, puis à enregistrer le code XML avec mise en retrait. Lorsque vous sérialisez le code XML avec mise en forme, seuls les espaces significatifs dans l'arborescence XML sont conservés. Il s'agit du comportement par défaut pour [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].  
  
 Un autre scénario courant consiste à lire et à modifier du code XML qui a déjà été intentionnellement mis en retrait. Vous ne souhaiterez peut-être modifier cette mise en retrait en aucune manière. Dans [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], vous devez pour cela conserver les espaces lorsque vous chargez ou analysez le code XML et que vous désactivez la mise en forme lors de la sérialisation du code XML.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] stocke les espaces en tant que nœud <xref:System.Xml.Linq.XText> au lieu de faire appel à un type de nœud <xref:System.Xml.XmlNodeType.Whitespace> spécialisé, comme le fait DOM.  
  
## <a name="support-for-annotations"></a>Prise en charge des annotations  
 Les éléments [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] prennent en charge un ensemble extensible d'annotations. Cela est utile pour assurer le suivi de diverses informations relatives à un élément, telles que des informations de schéma, le fait que l'élément soit lié à une interface utilisateur ou tout autre type d'informations spécifiques aux applications. Pour plus d’informations, consultez [Annotations LINQ to XML](linq-to-xml-annotations.md).  
  
## <a name="support-for-schema-information"></a>Prise en charge des informations de schéma  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] fournit une prise en charge de la validation XSD via les méthodes d’extension de l’espace de noms <xref:System.Xml.Schema?displayProperty=nameWithType>. Vous pouvez valider la conformité d’une arborescence XML à un schéma XSD. Vous pouvez remplir l’arborescence XML avec le PSVI (Post-Schema-Validation Infoset). Pour plus d’informations, consultez [Guide pratique pour valider à l’aide de XSD](how-to-validate-using-xsd-linq-to-xml.md) et <xref:System.Xml.Schema.Extensions>.  
  
## <a name="see-also"></a>Voir aussi

- [Mise en route (LINQ to XML)](getting-started-linq-to-xml.md)
