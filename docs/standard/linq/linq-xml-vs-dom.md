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
# <a name="linq-to-xml-vs-dom"></a><span data-ttu-id="3781c-104">LINQ to XML, différences par rapport à DOM</span><span class="sxs-lookup"><span data-stu-id="3781c-104">LINQ to XML vs. DOM</span></span>

<span data-ttu-id="3781c-105">Cet article décrit quelques-unes des principales différences entre LINQ to XML et l’API de programmation XML prédominante actuelle, le W3C Document Object Model (DOM).</span><span class="sxs-lookup"><span data-stu-id="3781c-105">This article describes some key differences between LINQ to XML and the current predominant XML programming API, the W3C Document Object Model (DOM).</span></span>

## <a name="new-ways-to-construct-xml-trees"></a><span data-ttu-id="3781c-106">Nouvelles manières de construire des arborescences XML</span><span class="sxs-lookup"><span data-stu-id="3781c-106">New ways to construct XML trees</span></span>

<span data-ttu-id="3781c-107">Dans le modèle DOM W3C, vous construisez une arborescence XML de bas en haut ; autrement dit, vous créez un document, vous créez des éléments, puis vous ajoutez les éléments au document.</span><span class="sxs-lookup"><span data-stu-id="3781c-107">In the W3C DOM, you build an XML tree from the bottom up; that is, you create a document, you create elements, and then you add the elements to the document.</span></span>

<span data-ttu-id="3781c-108">Par exemple, l’exemple suivant utilise un moyen classique de créer une arborescence XML à l’aide de l’implémentation Microsoft du modèle DOM, <xref:System.Xml.XmlDocument> .</span><span class="sxs-lookup"><span data-stu-id="3781c-108">For example, the following example uses a typical way to create an XML tree using the Microsoft implementation of DOM, <xref:System.Xml.XmlDocument>.</span></span>

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

<span data-ttu-id="3781c-109">Ce style de codage masque la structure de l’arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="3781c-109">This style of coding hides the structure of the XML tree.</span></span> <span data-ttu-id="3781c-110">LINQ to XML prend également en charge une autre approche, la *construction fonctionnelle*, qui illustre mieux la structure.</span><span class="sxs-lookup"><span data-stu-id="3781c-110">LINQ to XML also supports an alternative approach, *functional construction*, that better shows the structure.</span></span> <span data-ttu-id="3781c-111">Cette approche peut être effectuée avec les <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XAttribute> constructeurs et.</span><span class="sxs-lookup"><span data-stu-id="3781c-111">This approach can be done with the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XAttribute> constructors.</span></span> <span data-ttu-id="3781c-112">Dans Visual Basic, elle peut également être effectuée à l’aide de littéraux XML.</span><span class="sxs-lookup"><span data-stu-id="3781c-112">In Visual Basic, it can also be done with XML literals.</span></span> <span data-ttu-id="3781c-113">Cet exemple illustre la construction de la même arborescence XML à l’aide de la construction fonctionnelle :</span><span class="sxs-lookup"><span data-stu-id="3781c-113">This example demonstrates construction of the same XML tree using functional construction:</span></span>

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

<span data-ttu-id="3781c-114">Notez que la mise en retrait du code pour construire l’arborescence XML affiche la structure des données XML sous-jacentes.</span><span class="sxs-lookup"><span data-stu-id="3781c-114">Notice that indenting the code to construct the XML tree shows the structure of the underlying XML.</span></span> <span data-ttu-id="3781c-115">La version Visual Basic utilise des littéraux XML.</span><span class="sxs-lookup"><span data-stu-id="3781c-115">The Visual Basic version uses XML literals.</span></span>

<span data-ttu-id="3781c-116">Pour plus d’informations, consultez [arborescences XML](functional-construction.md).</span><span class="sxs-lookup"><span data-stu-id="3781c-116">For more information, see [XML trees](functional-construction.md).</span></span>

## <a name="work-directly-with-xml-elements"></a><span data-ttu-id="3781c-117">Travailler directement avec des éléments XML</span><span class="sxs-lookup"><span data-stu-id="3781c-117">Work directly with XML elements</span></span>

<span data-ttu-id="3781c-118">Lorsque vous programmez avec des données XML, vous travaillez en général principalement avec les éléments XML et éventuellement les attributs.</span><span class="sxs-lookup"><span data-stu-id="3781c-118">When you program with XML, your primary focus is usually on XML elements and perhaps on attributes.</span></span> <span data-ttu-id="3781c-119">Dans LINQ to XML, vous pouvez travailler directement avec des éléments et des attributs XML.</span><span class="sxs-lookup"><span data-stu-id="3781c-119">In LINQ to XML, you can work directly with XML elements and attributes.</span></span> <span data-ttu-id="3781c-120">Vous pouvez par exemple effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="3781c-120">For example, you can do the following:</span></span>

- <span data-ttu-id="3781c-121">Créer des éléments XML sans utiliser d'objet de document.</span><span class="sxs-lookup"><span data-stu-id="3781c-121">Create XML elements without using a document object at all.</span></span> <span data-ttu-id="3781c-122">Cela simplifie la programmation lorsque vous devez travailler avec des fragments d'arborescences XML.</span><span class="sxs-lookup"><span data-stu-id="3781c-122">This simplifies programming when you have to work with fragments of XML trees.</span></span>
- <span data-ttu-id="3781c-123">Charger des objets `T:System.Xml.Linq.XElement` directement à partir d'un fichier XML.</span><span class="sxs-lookup"><span data-stu-id="3781c-123">Load `T:System.Xml.Linq.XElement` objects directly from an XML file.</span></span>
- <span data-ttu-id="3781c-124">Sérialiser des objets `T:System.Xml.Linq.XElement` dans un fichier ou un flux.</span><span class="sxs-lookup"><span data-stu-id="3781c-124">Serialize `T:System.Xml.Linq.XElement` objects to a file or a stream.</span></span>

<span data-ttu-id="3781c-125">Comparez cela au modèle DOM W3C, dans lequel le document XML est utilisé en tant que conteneur logique pour l'arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="3781c-125">Compare this to the W3C DOM, in which the XML document is used as a logical container for the XML tree.</span></span> <span data-ttu-id="3781c-126">Dans le modèle DOM, les nœuds XML, y compris les éléments et attributs, doivent être créés dans le contexte d'un document XML.</span><span class="sxs-lookup"><span data-stu-id="3781c-126">In DOM, XML nodes, including elements and attributes, must be created in the context of an XML document.</span></span> <span data-ttu-id="3781c-127">Voici un fragment de code pour créer un élément de nom dans le modèle DOM :</span><span class="sxs-lookup"><span data-stu-id="3781c-127">Here is a fragment of code to create a name element in DOM:</span></span>

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

<span data-ttu-id="3781c-128">Si vous souhaitez utiliser un élément dans plusieurs documents, vous devez importer les nœuds d'un document à un autre.</span><span class="sxs-lookup"><span data-stu-id="3781c-128">If you want to use an element across multiple documents, you must import the nodes across documents.</span></span> <span data-ttu-id="3781c-129">LINQ to XML évite cette couche de complexité.</span><span class="sxs-lookup"><span data-stu-id="3781c-129">LINQ to XML avoids this layer of complexity.</span></span>

<span data-ttu-id="3781c-130">Lors de l'utilisation de LINQ to XML, vous utilisez la classe <xref:System.Xml.Linq.XDocument> uniquement si vous souhaitez ajouter un commentaire ou une information de traitement au niveau racine du document.</span><span class="sxs-lookup"><span data-stu-id="3781c-130">When using LINQ to XML, you use the <xref:System.Xml.Linq.XDocument> class only if you want to add a comment or processing instruction at the root level of the document.</span></span>

## <a name="simplified-handling-of-names-and-namespaces"></a><span data-ttu-id="3781c-131">Gestion simplifiée des noms et des espaces de noms</span><span class="sxs-lookup"><span data-stu-id="3781c-131">Simplified handling of names and namespaces</span></span>

<span data-ttu-id="3781c-132">La gestion des noms, des espaces de noms et des préfixes d'espaces de noms est généralement un aspect complexe de la programmation XML.</span><span class="sxs-lookup"><span data-stu-id="3781c-132">Handling names, namespaces, and namespace prefixes is generally a complex part of XML programming.</span></span> <span data-ttu-id="3781c-133">LINQ to XML simplifie les noms et les espaces de noms en éliminant la nécessité de gérer les préfixes d’espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="3781c-133">LINQ to XML simplifies names and namespaces by eliminating the requirement to deal with namespace prefixes.</span></span> <span data-ttu-id="3781c-134">Vous pouvez si vous le souhaitez contrôler les préfixes d'espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="3781c-134">If you want to control namespace prefixes, you can.</span></span> <span data-ttu-id="3781c-135">Toutefois, si vous décidez de ne pas contrôler explicitement les préfixes d’espaces de noms, LINQ to XML affectera des préfixes d’espaces de noms lors de la sérialisation s’ils sont requis, ou sérialisera à l’aide des espaces de noms par défaut si ce n’est pas le cas.</span><span class="sxs-lookup"><span data-stu-id="3781c-135">But if you decide to not explicitly control namespace prefixes, LINQ to XML will assign namespace prefixes during serialization if they're required, or will serialize using default namespaces if they're not.</span></span> <span data-ttu-id="3781c-136">Si des espaces de noms par défaut sont utilisés, il n'y aura pas de préfixes d'espaces de noms dans le document résultant.</span><span class="sxs-lookup"><span data-stu-id="3781c-136">If default namespaces are used, there will be no namespace prefixes in the resulting document.</span></span> <span data-ttu-id="3781c-137">Pour plus d’informations, consultez [vue d’ensemble des espaces de noms](namespaces-overview.md).</span><span class="sxs-lookup"><span data-stu-id="3781c-137">For more information, see [Namespaces overview](namespaces-overview.md).</span></span>

<span data-ttu-id="3781c-138">Un autre problème lié au modèle DOM est qu’il ne vous permet pas de modifier le nom d’un nœud.</span><span class="sxs-lookup"><span data-stu-id="3781c-138">Another problem with the DOM is that it doesn't let you change the name of a node.</span></span> <span data-ttu-id="3781c-139">Au lieu de cela, vous devez créer un nouveau nœud et y copier tous les nœuds enfants, perdant ainsi l'identité de nœud d'origine.</span><span class="sxs-lookup"><span data-stu-id="3781c-139">Instead, you have to create a new node and copy all the child nodes to it, losing the original node identity.</span></span> <span data-ttu-id="3781c-140">LINQ to XML évite ce problème en vous permettant de définir la <xref:System.Xml.Linq.XName> propriété sur un nœud.</span><span class="sxs-lookup"><span data-stu-id="3781c-140">LINQ to XML avoids this problem by enabling you to set the <xref:System.Xml.Linq.XName> property on a node.</span></span>

## <a name="static-method-support-for-loading-xml"></a><span data-ttu-id="3781c-141">Prise en charge des méthodes statiques pour le chargement XML</span><span class="sxs-lookup"><span data-stu-id="3781c-141">Static method support for loading XML</span></span>

<span data-ttu-id="3781c-142">LINQ to XML vous permet de charger du code XML à l’aide de méthodes statiques, au lieu de méthodes d’instance.</span><span class="sxs-lookup"><span data-stu-id="3781c-142">LINQ to XML lets you load XML by using static methods, instead of instance methods.</span></span> <span data-ttu-id="3781c-143">Cela simplifie le chargement et l'analyse.</span><span class="sxs-lookup"><span data-stu-id="3781c-143">This simplifies loading and parsing.</span></span> <span data-ttu-id="3781c-144">Pour plus d’informations, consultez [Comment charger du code XML à partir d’un fichier](load-xml-file.md).</span><span class="sxs-lookup"><span data-stu-id="3781c-144">For more information, see [How to load XML from a file](load-xml-file.md).</span></span>

## <a name="removal-of-support-for-dtd-constructs"></a><span data-ttu-id="3781c-145">Suppression de la prise en charge des constructions DTD</span><span class="sxs-lookup"><span data-stu-id="3781c-145">Removal of support for DTD constructs</span></span>

<span data-ttu-id="3781c-146">LINQ to XML simplifie davantage la programmation XML en supprimant la prise en charge des entités et des références d’entité.</span><span class="sxs-lookup"><span data-stu-id="3781c-146">LINQ to XML further simplifies XML programming by removing support for entities and entity references.</span></span> <span data-ttu-id="3781c-147">La gestion des entités est complexe et rarement utilisée.</span><span class="sxs-lookup"><span data-stu-id="3781c-147">The management of entities is complex, and is rarely used.</span></span> <span data-ttu-id="3781c-148">La suppression de leur prise en charge augmente les performances et simplifie l'interface de programmation.</span><span class="sxs-lookup"><span data-stu-id="3781c-148">Removing their support increases performance and simplifies the programming interface.</span></span> <span data-ttu-id="3781c-149">Quand une arborescence de LINQ to XML est remplie, toutes les entités DTD sont développées.</span><span class="sxs-lookup"><span data-stu-id="3781c-149">When a LINQ to XML tree is populated, all DTD entities are expanded.</span></span>

## <a name="support-for-fragments"></a><span data-ttu-id="3781c-150">Prise en charge des fragments</span><span class="sxs-lookup"><span data-stu-id="3781c-150">Support for fragments</span></span>

<span data-ttu-id="3781c-151">LINQ to XML ne fournit pas d’équivalent pour la `XmlDocumentFragment` classe.</span><span class="sxs-lookup"><span data-stu-id="3781c-151">LINQ to XML doesn't provide an equivalent for the `XmlDocumentFragment` class.</span></span> <span data-ttu-id="3781c-152">Dans de nombreux cas, toutefois, le `XmlDocumentFragment` concept peut être géré par le résultat d’une requête typée à partir <xref:System.Collections.Generic.IEnumerable%601> de <xref:System.Xml.Linq.XNode> ou <xref:System.Collections.Generic.IEnumerable%601> de <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="3781c-152">In many cases, however, the `XmlDocumentFragment` concept can be handled by the result of a query that's typed as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XNode>, or <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>.</span></span>

## <a name="support-for-xpathnavigator"></a><span data-ttu-id="3781c-153">Prise en charge de XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="3781c-153">Support for XPathNavigator</span></span>

<span data-ttu-id="3781c-154">LINQ to XML assure la prise en charge de <xref:System.Xml.XPath.XPathNavigator> via des méthodes d’extension dans l' <xref:System.Xml.XPath?displayProperty=nameWithType> espace de noms.</span><span class="sxs-lookup"><span data-stu-id="3781c-154">LINQ to XML provides support for <xref:System.Xml.XPath.XPathNavigator> through extension methods in the <xref:System.Xml.XPath?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="3781c-155">Pour plus d'informations, consultez <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3781c-155">For more information, see <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span></span>

## <a name="support-for-white-space-and-indentation"></a><span data-ttu-id="3781c-156">Prise en charge des espaces blancs et de la mise en retrait</span><span class="sxs-lookup"><span data-stu-id="3781c-156">Support for white space and indentation</span></span>

<span data-ttu-id="3781c-157">LINQ to XML gère l’espace blanc plus simplement que le modèle DOM.</span><span class="sxs-lookup"><span data-stu-id="3781c-157">LINQ to XML handles white space more simply than the DOM.</span></span>

<span data-ttu-id="3781c-158">Un scénario courant consiste à lire le code XML mis en retrait, à créer une arborescence XML en mémoire sans nœuds d’espace blanc (autrement dit, ne pas conserver les espaces), à effectuer certaines opérations sur le code XML, puis à enregistrer le code XML avec mise en retrait.</span><span class="sxs-lookup"><span data-stu-id="3781c-158">A common scenario is to read indented XML, create an in-memory XML tree without any white space text nodes (that is, not preserving white space), do some operations on the XML, and then save the XML with indentation.</span></span> <span data-ttu-id="3781c-159">Lorsque vous sérialisez le code XML avec mise en forme, seuls les espaces significatifs dans l'arborescence XML sont conservés.</span><span class="sxs-lookup"><span data-stu-id="3781c-159">When you serialize the XML with formatting, only significant white space in the XML tree is preserved.</span></span> <span data-ttu-id="3781c-160">Il s’agit du comportement par défaut pour LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="3781c-160">This is the default behavior for LINQ to XML.</span></span>

<span data-ttu-id="3781c-161">Un autre scénario courant consiste à lire et à modifier du code XML qui a déjà été intentionnellement mis en retrait.</span><span class="sxs-lookup"><span data-stu-id="3781c-161">Another common scenario is to read and modify XML that has already been intentionally indented.</span></span> <span data-ttu-id="3781c-162">Vous ne souhaiterez peut-être modifier cette mise en retrait en aucune manière.</span><span class="sxs-lookup"><span data-stu-id="3781c-162">You might not want to change this indentation in any way.</span></span> <span data-ttu-id="3781c-163">Dans LINQ to XML, vous pouvez effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="3781c-163">In LINQ to XML, you can do this by:</span></span>

- <span data-ttu-id="3781c-164">Conserver les espaces lorsque vous chargez ou analysez le XML.</span><span class="sxs-lookup"><span data-stu-id="3781c-164">Preserving white space when you load or parse the XML.</span></span>
- <span data-ttu-id="3781c-165">Désactivation de la mise en forme lors de la sérialisation du code XML.</span><span class="sxs-lookup"><span data-stu-id="3781c-165">Disabling formatting when you serialize the XML.</span></span>

<span data-ttu-id="3781c-166">LINQ to XML stocke les espaces en tant que <xref:System.Xml.Linq.XText> nœud, au lieu d’avoir un <xref:System.Xml.XmlNodeType.Whitespace> type de nœud spécialisé, comme le fait le DOM.</span><span class="sxs-lookup"><span data-stu-id="3781c-166">LINQ to XML stores white space as an <xref:System.Xml.Linq.XText> node, instead of having a specialized <xref:System.Xml.XmlNodeType.Whitespace> node type, as the DOM does.</span></span>

## <a name="support-for-annotations"></a><span data-ttu-id="3781c-167">Prise en charge des annotations</span><span class="sxs-lookup"><span data-stu-id="3781c-167">Support for annotations</span></span>

<span data-ttu-id="3781c-168">Les éléments LINQ to XML prennent en charge un ensemble extensible d’annotations.</span><span class="sxs-lookup"><span data-stu-id="3781c-168">LINQ to XML elements support an extensible set of annotations.</span></span> <span data-ttu-id="3781c-169">Cela est utile pour assurer le suivi de diverses informations relatives à un élément, telles que des informations de schéma, le fait que l'élément soit lié à une interface utilisateur ou tout autre type d'informations spécifiques aux applications.</span><span class="sxs-lookup"><span data-stu-id="3781c-169">This is useful for tracking miscellaneous information about an element, such as schema information, information about whether the element is bound to a UI, or any other kind of application-specific information.</span></span> <span data-ttu-id="3781c-170">Pour plus d’informations, consultez [LINQ to XML annotations](linq-xml-annotations.md).</span><span class="sxs-lookup"><span data-stu-id="3781c-170">For more information, see [LINQ to XML annotations](linq-xml-annotations.md).</span></span>

## <a name="support-for-schema-information"></a><span data-ttu-id="3781c-171">Prise en charge des informations de schéma</span><span class="sxs-lookup"><span data-stu-id="3781c-171">Support for schema information</span></span>

<span data-ttu-id="3781c-172">LINQ to XML assure la prise en charge de la validation XSD via des méthodes d’extension dans l' <xref:System.Xml.Schema?displayProperty=nameWithType> espace de noms.</span><span class="sxs-lookup"><span data-stu-id="3781c-172">LINQ to XML provides support for XSD validation through extension methods in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="3781c-173">Vous pouvez valider la conformité d’une arborescence XML à un schéma XSD.</span><span class="sxs-lookup"><span data-stu-id="3781c-173">You can validate that an XML tree complies with an XSD.</span></span> <span data-ttu-id="3781c-174">Vous pouvez remplir l’arborescence XML avec le PSVI (Post-Schema-Validation Infoset).</span><span class="sxs-lookup"><span data-stu-id="3781c-174">You can populate the XML tree with the post-schema-validation infoset (PSVI).</span></span> <span data-ttu-id="3781c-175">Pour plus d’informations, consultez [Comment valider à l’aide de XSD](validate-xsd.md) et <xref:System.Xml.Schema.Extensions> .</span><span class="sxs-lookup"><span data-stu-id="3781c-175">For more information, see [How to validate using XSD](validate-xsd.md) and <xref:System.Xml.Schema.Extensions>.</span></span>

## <a name="see-also"></a><span data-ttu-id="3781c-176">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3781c-176">See also</span></span>

- [<span data-ttu-id="3781c-177">Présentation de LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="3781c-177">LINQ to XML overview</span></span>](linq-xml-overview.md)
