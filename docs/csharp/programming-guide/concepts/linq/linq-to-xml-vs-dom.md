---
title: LINQ à XML vs DOM (C)
ms.date: 07/20/2015
ms.assetid: 51c0e3d2-c047-4e6a-a423-d61a882400b7
ms.openlocfilehash: 92d0da494829d57517d52fe93a3cbcf1398fdbe4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79168387"
---
# <a name="linq-to-xml-vs-dom-c"></a><span data-ttu-id="81a5d-102">LINQ à XML vs DOM (C)</span><span class="sxs-lookup"><span data-stu-id="81a5d-102">LINQ to XML vs. DOM (C#)</span></span>
<span data-ttu-id="81a5d-103">Cette section décrit certaines des principales différences entre [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] et l’API de programmation XML actuellement prédominante, le modèle DOM (Document Object Model) W3C.</span><span class="sxs-lookup"><span data-stu-id="81a5d-103">This section describes some key differences between [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] and the current predominant XML programming API, the W3C Document Object Model (DOM).</span></span>  
  
## <a name="new-ways-to-construct-xml-trees"></a><span data-ttu-id="81a5d-104">Nouvelles manières de construire des arborescences XML</span><span class="sxs-lookup"><span data-stu-id="81a5d-104">New Ways to Construct XML Trees</span></span>  
 <span data-ttu-id="81a5d-105">Dans le modèle DOM W3C, vous construisez une arborescence XML de bas en haut ; autrement dit, vous créez un document, vous créez des éléments, puis vous ajoutez les éléments au document.</span><span class="sxs-lookup"><span data-stu-id="81a5d-105">In the W3C DOM, you build an XML tree from the bottom up; that is, you create a document, you create elements, and then you add the elements to the document.</span></span>  
  
 <span data-ttu-id="81a5d-106">Voici un exemple typique de création d’une arborescence XML à l’aide de l’implémentation Microsoft du modèle DOM, <xref:System.Xml.XmlDocument> :</span><span class="sxs-lookup"><span data-stu-id="81a5d-106">For example, the following would be a typical way to create an XML tree using the Microsoft implementation of DOM, <xref:System.Xml.XmlDocument>:</span></span>  
  
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
  
 <span data-ttu-id="81a5d-107">Ce style de codage ne fournit visuellement que peu d’informations concernant la structure de l’arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="81a5d-107">This style of coding does not visually provide much information about the structure of the XML tree.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="81a5d-108">prend en charge cette approche de la construction d’une arborescence XML, mais également une approche alternative, la *construction fonctionnelle*.</span><span class="sxs-lookup"><span data-stu-id="81a5d-108">supports this approach to constructing an XML tree, but also supports an alternative approach, *functional construction*.</span></span> <span data-ttu-id="81a5d-109">La construction fonctionnelle utilise les constructeurs <xref:System.Xml.Linq.XElement> et <xref:System.Xml.Linq.XAttribute> pour générer une arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="81a5d-109">Functional construction uses the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XAttribute> constructors to build an XML tree.</span></span>  
  
 <span data-ttu-id="81a5d-110">Voici comment vous pouvez construire la même arborescence XML à l’aide de la construction fonctionnelle [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="81a5d-110">Here is how you would construct the same XML tree by using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] functional construction:</span></span>  
  
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
  
 <span data-ttu-id="81a5d-111">Notez que la mise en retrait du code pour construire l’arborescence XML affiche la structure des données XML sous-jacentes.</span><span class="sxs-lookup"><span data-stu-id="81a5d-111">Notice that indenting the code to construct the XML tree shows the structure of the underlying XML.</span></span>  
  
 <span data-ttu-id="81a5d-112">Pour plus d’informations, consultez [Création d’arborescences XML (C#)](./linq-to-xml-overview.md).</span><span class="sxs-lookup"><span data-stu-id="81a5d-112">For more information, see [Creating XML Trees (C#)](./linq-to-xml-overview.md).</span></span>  
  
## <a name="working-directly-with-xml-elements"></a><span data-ttu-id="81a5d-113">Utilisation directe des éléments XML</span><span class="sxs-lookup"><span data-stu-id="81a5d-113">Working Directly with XML Elements</span></span>  
 <span data-ttu-id="81a5d-114">Lorsque vous programmez avec des données XML, vous travaillez en général principalement avec les éléments XML et éventuellement les attributs.</span><span class="sxs-lookup"><span data-stu-id="81a5d-114">When you program with XML, your primary focus is usually on XML elements and perhaps on attributes.</span></span> <span data-ttu-id="81a5d-115">Dans [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], vous pouvez utiliser directement les éléments et les attributs XML.</span><span class="sxs-lookup"><span data-stu-id="81a5d-115">In [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can work directly with XML elements and attributes.</span></span> <span data-ttu-id="81a5d-116">Vous pouvez par exemple effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="81a5d-116">For example, you can do the following:</span></span>  
  
- <span data-ttu-id="81a5d-117">Créer des éléments XML sans utiliser d'objet de document.</span><span class="sxs-lookup"><span data-stu-id="81a5d-117">Create XML elements without using a document object at all.</span></span> <span data-ttu-id="81a5d-118">Cela simplifie la programmation lorsque vous devez travailler avec des fragments d'arborescences XML.</span><span class="sxs-lookup"><span data-stu-id="81a5d-118">This simplifies programming when you have to work with fragments of XML trees.</span></span>  
  
- <span data-ttu-id="81a5d-119">Charger des objets `T:System.Xml.Linq.XElement` directement à partir d'un fichier XML.</span><span class="sxs-lookup"><span data-stu-id="81a5d-119">Load `T:System.Xml.Linq.XElement` objects directly from an XML file.</span></span>  
  
- <span data-ttu-id="81a5d-120">Sérialiser des objets `T:System.Xml.Linq.XElement` dans un fichier ou un flux.</span><span class="sxs-lookup"><span data-stu-id="81a5d-120">Serialize `T:System.Xml.Linq.XElement` objects to a file or a stream.</span></span>  
  
 <span data-ttu-id="81a5d-121">Comparez cela au modèle DOM W3C, dans lequel le document XML est utilisé en tant que conteneur logique pour l'arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="81a5d-121">Compare this to the W3C DOM, in which the XML document is used as a logical container for the XML tree.</span></span> <span data-ttu-id="81a5d-122">Dans le modèle DOM, les nœuds XML, y compris les éléments et attributs, doivent être créés dans le contexte d'un document XML.</span><span class="sxs-lookup"><span data-stu-id="81a5d-122">In DOM, XML nodes, including elements and attributes, must be created in the context of an XML document.</span></span> <span data-ttu-id="81a5d-123">Voici un fragment de code permettant de créer un élément de nom dans le modèle DOM :</span><span class="sxs-lookup"><span data-stu-id="81a5d-123">Here is a fragment of the code to create a name element in DOM:</span></span>  
  
```csharp  
XmlDocument doc = new XmlDocument();  
XmlElement name = doc.CreateElement("Name");  
name.InnerText = "Patrick Hines";  
doc.AppendChild(name);  
```  
  
 <span data-ttu-id="81a5d-124">Si vous souhaitez utiliser un élément dans plusieurs documents, vous devez importer les nœuds d'un document à un autre.</span><span class="sxs-lookup"><span data-stu-id="81a5d-124">If you want to use an element across multiple documents, you must import the nodes across documents.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="81a5d-125">évite cette couche de complexité.</span><span class="sxs-lookup"><span data-stu-id="81a5d-125">avoids this layer of complexity.</span></span>  
  
 <span data-ttu-id="81a5d-126">Lors de l'utilisation de LINQ to XML, vous utilisez la classe <xref:System.Xml.Linq.XDocument> uniquement si vous souhaitez ajouter un commentaire ou une information de traitement au niveau racine du document.</span><span class="sxs-lookup"><span data-stu-id="81a5d-126">When using LINQ to XML, you use the <xref:System.Xml.Linq.XDocument> class only if you want to add a comment or processing instruction at the root level of the document.</span></span>  
  
## <a name="simplified-handling-of-names-and-namespaces"></a><span data-ttu-id="81a5d-127">Gestion simplifiée des noms et des espaces de noms</span><span class="sxs-lookup"><span data-stu-id="81a5d-127">Simplified Handling of Names and Namespaces</span></span>  
 <span data-ttu-id="81a5d-128">La gestion des noms, des espaces de noms et des préfixes d'espaces de noms est généralement un aspect complexe de la programmation XML.</span><span class="sxs-lookup"><span data-stu-id="81a5d-128">Handling names, namespaces, and namespace prefixes is generally a complex part of XML programming.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="81a5d-129">simplifie les noms et les espaces de noms en éliminant la nécessité de gérer les préfixes d’espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="81a5d-129">simplifies names and namespaces by eliminating the requirement to deal with namespace prefixes.</span></span> <span data-ttu-id="81a5d-130">Vous pouvez si vous le souhaitez contrôler les préfixes d'espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="81a5d-130">If you want to control namespace prefixes, you can.</span></span> <span data-ttu-id="81a5d-131">Si vous décidez cependant de ne pas contrôler explicitement les préfixes d’espaces de noms, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] affecte des préfixes d’espaces de noms lors de la sérialisation s’ils sont nécessaires ou, s’ils ne le sont pas, sérialise en utilisant les espaces de noms par défaut.</span><span class="sxs-lookup"><span data-stu-id="81a5d-131">But if you decide to not explicitly control namespace prefixes, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] will assign namespace prefixes during serialization if they are required, or will serialize using default namespaces if they are not.</span></span> <span data-ttu-id="81a5d-132">Si des espaces de noms par défaut sont utilisés, il n'y aura pas de préfixes d'espaces de noms dans le document résultant.</span><span class="sxs-lookup"><span data-stu-id="81a5d-132">If default namespaces are used, there will be no namespace prefixes in the resulting document.</span></span> <span data-ttu-id="81a5d-133">Pour plus d’informations, consultez [Vue d’ensemble des espaces de noms (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="81a5d-133">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="81a5d-134">L'un des autres problèmes associés au modèle DOM est qu'il ne vous permet pas de modifier le nom d'un nœud.</span><span class="sxs-lookup"><span data-stu-id="81a5d-134">Another problem with the DOM is that it does not let you change the name of a node.</span></span> <span data-ttu-id="81a5d-135">Au lieu de cela, vous devez créer un nouveau nœud et y copier tous les nœuds enfants, perdant ainsi l'identité de nœud d'origine.</span><span class="sxs-lookup"><span data-stu-id="81a5d-135">Instead, you have to create a new node and copy all the child nodes to it, losing the original node identity.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="81a5d-136">évite ce problème en vous permettant de définir la propriété <xref:System.Xml.Linq.XName> sur un nœud.</span><span class="sxs-lookup"><span data-stu-id="81a5d-136">avoids this problem by enabling you to set the <xref:System.Xml.Linq.XName> property on a node.</span></span>  
  
## <a name="static-method-support-for-loading-xml"></a><span data-ttu-id="81a5d-137">Prise en charge des méthodes statiques pour le chargement de données XML</span><span class="sxs-lookup"><span data-stu-id="81a5d-137">Static Method Support for Loading XML</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="81a5d-138">vous permet de charger du code XML en utilisant des méthodes statiques au lieu de méthodes d’instance.</span><span class="sxs-lookup"><span data-stu-id="81a5d-138">lets you load XML by using static methods, instead of instance methods.</span></span> <span data-ttu-id="81a5d-139">Cela simplifie le chargement et l'analyse.</span><span class="sxs-lookup"><span data-stu-id="81a5d-139">This simplifies loading and parsing.</span></span> <span data-ttu-id="81a5d-140">Pour plus d’informations, voir [Comment charger XML à partir d’un fichier (C)](./how-to-load-xml-from-a-file.md).</span><span class="sxs-lookup"><span data-stu-id="81a5d-140">For more information, see [How to load XML from a file (C#)](./how-to-load-xml-from-a-file.md).</span></span>  
  
## <a name="removal-of-support-for-dtd-constructs"></a><span data-ttu-id="81a5d-141">Suppression de la prise en charge des constructions de DTD</span><span class="sxs-lookup"><span data-stu-id="81a5d-141">Removal of Support for DTD Constructs</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="81a5d-142">simplifie la programmation XML en supprimant la prise en charge des entités et des références d'entités.</span><span class="sxs-lookup"><span data-stu-id="81a5d-142">further simplifies XML programming by removing support for entities and entity references.</span></span> <span data-ttu-id="81a5d-143">La gestion des entités est complexe et rarement utilisée.</span><span class="sxs-lookup"><span data-stu-id="81a5d-143">The management of entities is complex, and is rarely used.</span></span> <span data-ttu-id="81a5d-144">La suppression de leur prise en charge augmente les performances et simplifie l'interface de programmation.</span><span class="sxs-lookup"><span data-stu-id="81a5d-144">Removing their support increases performance and simplifies the programming interface.</span></span> <span data-ttu-id="81a5d-145">Quand une arborescence [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] est remplie, toutes les entités DTD sont développées.</span><span class="sxs-lookup"><span data-stu-id="81a5d-145">When a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] tree is populated, all DTD entities are expanded.</span></span>  
  
## <a name="support-for-fragments"></a><span data-ttu-id="81a5d-146">Prise en charge des fragments</span><span class="sxs-lookup"><span data-stu-id="81a5d-146">Support for Fragments</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="81a5d-147">ne fournit pas d’équivalent pour la classe `XmlDocumentFragment`.</span><span class="sxs-lookup"><span data-stu-id="81a5d-147">does not provide an equivalent for the `XmlDocumentFragment` class.</span></span> <span data-ttu-id="81a5d-148">Dans de nombreux cas, cependant, le concept de `XmlDocumentFragment` peut être géré par le résultat d’une requête typée <xref:System.Collections.Generic.IEnumerable%601> de <xref:System.Xml.Linq.XNode> ou <xref:System.Collections.Generic.IEnumerable%601> de <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="81a5d-148">In many cases, however, the `XmlDocumentFragment` concept can be handled by the result of a query that is typed as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XNode>, or <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>.</span></span>  
  
## <a name="support-for-xpathnavigator"></a><span data-ttu-id="81a5d-149">Prise en charge de XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="81a5d-149">Support for XPathNavigator</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="81a5d-150">fournit une prise en charge pour <xref:System.Xml.XPath.XPathNavigator> via les méthodes d’extension de l’espace de noms <xref:System.Xml.XPath?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="81a5d-150">provides support for <xref:System.Xml.XPath.XPathNavigator> through extension methods in the <xref:System.Xml.XPath?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="81a5d-151">Pour plus d’informations, consultez <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="81a5d-151">For more information, see <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span></span>  
  
## <a name="support-for-white-space-and-indentation"></a><span data-ttu-id="81a5d-152">Prise en charge des espaces blancs et de la mise en retrait</span><span class="sxs-lookup"><span data-stu-id="81a5d-152">Support for White Space and Indentation</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="81a5d-153">gère les espaces plus simplement que le modèle DOM.</span><span class="sxs-lookup"><span data-stu-id="81a5d-153">handles white space more simply than the DOM.</span></span>  
  
 <span data-ttu-id="81a5d-154">Un scénario courant consiste à lire le code XML mis en retrait, à créer une arborescence XML en mémoire sans nœuds d'espaces (autrement dit, ne pas conserver les espaces), à effectuer certaines opérations sur le code XML, puis à enregistrer le code XML avec mise en retrait.</span><span class="sxs-lookup"><span data-stu-id="81a5d-154">A common scenario is to read indented XML, create an in-memory XML tree without any white space text nodes (that is, not preserving white space), perform some operations on the XML, and then save the XML with indentation.</span></span> <span data-ttu-id="81a5d-155">Lorsque vous sérialisez le code XML avec mise en forme, seuls les espaces significatifs dans l'arborescence XML sont conservés.</span><span class="sxs-lookup"><span data-stu-id="81a5d-155">When you serialize the XML with formatting, only significant white space in the XML tree is preserved.</span></span> <span data-ttu-id="81a5d-156">Il s'agit du comportement par défaut pour [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="81a5d-156">This is the default behavior for [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="81a5d-157">Un autre scénario courant consiste à lire et à modifier du code XML qui a déjà été intentionnellement mis en retrait.</span><span class="sxs-lookup"><span data-stu-id="81a5d-157">Another common scenario is to read and modify XML that has already been intentionally indented.</span></span> <span data-ttu-id="81a5d-158">Vous ne souhaiterez peut-être modifier cette mise en retrait en aucune manière.</span><span class="sxs-lookup"><span data-stu-id="81a5d-158">You might not want to change this indentation in any way.</span></span> <span data-ttu-id="81a5d-159">Dans [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], vous devez pour cela conserver les espaces lorsque vous chargez ou analysez le code XML et que vous désactivez la mise en forme lors de la sérialisation du code XML.</span><span class="sxs-lookup"><span data-stu-id="81a5d-159">In [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can do this by preserving white space when you load or parse the XML and disabling formatting when you serialize the XML.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="81a5d-160">stocke les espaces en tant que nœud <xref:System.Xml.Linq.XText> au lieu de faire appel à un type de nœud <xref:System.Xml.XmlNodeType.Whitespace> spécialisé, comme le fait DOM.</span><span class="sxs-lookup"><span data-stu-id="81a5d-160">stores white space as an <xref:System.Xml.Linq.XText> node, instead of having a specialized <xref:System.Xml.XmlNodeType.Whitespace> node type, as the DOM does.</span></span>  
  
## <a name="support-for-annotations"></a><span data-ttu-id="81a5d-161">Prise en charge des annotations</span><span class="sxs-lookup"><span data-stu-id="81a5d-161">Support for Annotations</span></span>  
 <span data-ttu-id="81a5d-162">Les éléments [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] prennent en charge un ensemble extensible d'annotations.</span><span class="sxs-lookup"><span data-stu-id="81a5d-162">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] elements support an extensible set of annotations.</span></span> <span data-ttu-id="81a5d-163">Cela est utile pour assurer le suivi de diverses informations relatives à un élément, telles que des informations de schéma, le fait que l'élément soit lié à une interface utilisateur ou tout autre type d'informations spécifiques aux applications.</span><span class="sxs-lookup"><span data-stu-id="81a5d-163">This is useful for tracking miscellaneous information about an element, such as schema information, information about whether the element is bound to a UI, or any other kind of application-specific information.</span></span> <span data-ttu-id="81a5d-164">Pour plus d’informations, consultez [Annotations LINQ to XML](./linq-to-xml-annotations.md).</span><span class="sxs-lookup"><span data-stu-id="81a5d-164">For more information, see [LINQ to XML Annotations](./linq-to-xml-annotations.md).</span></span>  
  
## <a name="support-for-schema-information"></a><span data-ttu-id="81a5d-165">Prise en charge des informations de schéma</span><span class="sxs-lookup"><span data-stu-id="81a5d-165">Support for Schema Information</span></span>  
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="81a5d-166">fournit une prise en charge de la validation XSD via les méthodes d’extension de l’espace de noms <xref:System.Xml.Schema?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="81a5d-166">provides support for XSD validation through extension methods in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="81a5d-167">Vous pouvez valider la conformité d’une arborescence XML à un schéma XSD.</span><span class="sxs-lookup"><span data-stu-id="81a5d-167">You can validate that an XML tree complies with an XSD.</span></span> <span data-ttu-id="81a5d-168">Vous pouvez remplir l’arborescence XML avec le PSVI (Post-Schema-Validation Infoset).</span><span class="sxs-lookup"><span data-stu-id="81a5d-168">You can populate the XML tree with the post-schema-validation infoset (PSVI).</span></span> <span data-ttu-id="81a5d-169">Pour plus d’informations, voir Comment <xref:System.Xml.Schema.Extensions> [valider à l’aide de XSD](./how-to-validate-using-xsd-linq-to-xml.md) et .</span><span class="sxs-lookup"><span data-stu-id="81a5d-169">For more information, see [How to validate using XSD](./how-to-validate-using-xsd-linq-to-xml.md) and <xref:System.Xml.Schema.Extensions>.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="81a5d-170">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="81a5d-170">See also</span></span>

- [<span data-ttu-id="81a5d-171">Bien démarrer (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="81a5d-171">Getting Started (LINQ to XML)</span></span>](./linq-to-xml-overview.md)
