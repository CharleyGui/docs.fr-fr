---
title: LINQ to XML et DOM (C#)
description: Découvrez les principales différences entre LINQ to XML et l’API de programmation XML W3C Document Object Model (DOM).
ms.date: 07/20/2015
ms.assetid: 51c0e3d2-c047-4e6a-a423-d61a882400b7
ms.openlocfilehash: f5fc3fd7869079d47d7c9031e3668afeed7a117b
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165338"
---
# <a name="linq-to-xml-vs-dom-c"></a><span data-ttu-id="c6d86-103">LINQ to XML et DOM (C#)</span><span class="sxs-lookup"><span data-stu-id="c6d86-103">LINQ to XML vs. DOM (C#)</span></span>
<span data-ttu-id="c6d86-104">Cette section décrit certaines des principales différences entre [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] et l’API de programmation XML actuellement prédominante, le modèle DOM (Document Object Model) W3C.</span><span class="sxs-lookup"><span data-stu-id="c6d86-104">This section describes some key differences between [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] and the current predominant XML programming API, the W3C Document Object Model (DOM).</span></span>  
  
## <a name="new-ways-to-construct-xml-trees"></a><span data-ttu-id="c6d86-105">Nouvelles manières de construire des arborescences XML</span><span class="sxs-lookup"><span data-stu-id="c6d86-105">New Ways to Construct XML Trees</span></span>  
 <span data-ttu-id="c6d86-106">Dans le modèle DOM W3C, vous construisez une arborescence XML de bas en haut ; autrement dit, vous créez un document, vous créez des éléments, puis vous ajoutez les éléments au document.</span><span class="sxs-lookup"><span data-stu-id="c6d86-106">In the W3C DOM, you build an XML tree from the bottom up; that is, you create a document, you create elements, and then you add the elements to the document.</span></span>  
  
 <span data-ttu-id="c6d86-107">Voici un exemple typique de création d’une arborescence XML à l’aide de l’implémentation Microsoft du modèle DOM, <xref:System.Xml.XmlDocument> :</span><span class="sxs-lookup"><span data-stu-id="c6d86-107">For example, the following would be a typical way to create an XML tree using the Microsoft implementation of DOM, <xref:System.Xml.XmlDocument>:</span></span>  
  
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
  
 <span data-ttu-id="c6d86-108">Ce style de codage ne fournit visuellement que peu d’informations concernant la structure de l’arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="c6d86-108">This style of coding does not visually provide much information about the structure of the XML tree.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="c6d86-109">prend en charge cette approche de la construction d’une arborescence XML, mais également une approche alternative, la *construction fonctionnelle*.</span><span class="sxs-lookup"><span data-stu-id="c6d86-109">supports this approach to constructing an XML tree, but also supports an alternative approach, *functional construction*.</span></span> <span data-ttu-id="c6d86-110">La construction fonctionnelle utilise les constructeurs <xref:System.Xml.Linq.XElement> et <xref:System.Xml.Linq.XAttribute> pour générer une arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="c6d86-110">Functional construction uses the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XAttribute> constructors to build an XML tree.</span></span>  
  
 <span data-ttu-id="c6d86-111">Voici comment vous pouvez construire la même arborescence XML à l’aide de la construction fonctionnelle [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="c6d86-111">Here is how you would construct the same XML tree by using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] functional construction:</span></span>  
  
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
  
 <span data-ttu-id="c6d86-112">Notez que la mise en retrait du code pour construire l’arborescence XML affiche la structure des données XML sous-jacentes.</span><span class="sxs-lookup"><span data-stu-id="c6d86-112">Notice that indenting the code to construct the XML tree shows the structure of the underlying XML.</span></span>  
  
 <span data-ttu-id="c6d86-113">Pour plus d’informations, consultez [Création d’arborescences XML (C#)](./linq-to-xml-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c6d86-113">For more information, see [Creating XML Trees (C#)](./linq-to-xml-overview.md).</span></span>  
  
## <a name="working-directly-with-xml-elements"></a><span data-ttu-id="c6d86-114">Utilisation directe des éléments XML</span><span class="sxs-lookup"><span data-stu-id="c6d86-114">Working Directly with XML Elements</span></span>  
 <span data-ttu-id="c6d86-115">Lorsque vous programmez avec des données XML, vous travaillez en général principalement avec les éléments XML et éventuellement les attributs.</span><span class="sxs-lookup"><span data-stu-id="c6d86-115">When you program with XML, your primary focus is usually on XML elements and perhaps on attributes.</span></span> <span data-ttu-id="c6d86-116">Dans [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], vous pouvez utiliser directement les éléments et les attributs XML.</span><span class="sxs-lookup"><span data-stu-id="c6d86-116">In [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can work directly with XML elements and attributes.</span></span> <span data-ttu-id="c6d86-117">Vous pouvez par exemple effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="c6d86-117">For example, you can do the following:</span></span>  
  
- <span data-ttu-id="c6d86-118">Créer des éléments XML sans utiliser d'objet de document.</span><span class="sxs-lookup"><span data-stu-id="c6d86-118">Create XML elements without using a document object at all.</span></span> <span data-ttu-id="c6d86-119">Cela simplifie la programmation lorsque vous devez travailler avec des fragments d'arborescences XML.</span><span class="sxs-lookup"><span data-stu-id="c6d86-119">This simplifies programming when you have to work with fragments of XML trees.</span></span>  
  
- <span data-ttu-id="c6d86-120">Charger des objets `T:System.Xml.Linq.XElement` directement à partir d'un fichier XML.</span><span class="sxs-lookup"><span data-stu-id="c6d86-120">Load `T:System.Xml.Linq.XElement` objects directly from an XML file.</span></span>  
  
- <span data-ttu-id="c6d86-121">Sérialiser des objets `T:System.Xml.Linq.XElement` dans un fichier ou un flux.</span><span class="sxs-lookup"><span data-stu-id="c6d86-121">Serialize `T:System.Xml.Linq.XElement` objects to a file or a stream.</span></span>  
  
 <span data-ttu-id="c6d86-122">Comparez cela au modèle DOM W3C, dans lequel le document XML est utilisé en tant que conteneur logique pour l'arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="c6d86-122">Compare this to the W3C DOM, in which the XML document is used as a logical container for the XML tree.</span></span> <span data-ttu-id="c6d86-123">Dans le modèle DOM, les nœuds XML, y compris les éléments et attributs, doivent être créés dans le contexte d'un document XML.</span><span class="sxs-lookup"><span data-stu-id="c6d86-123">In DOM, XML nodes, including elements and attributes, must be created in the context of an XML document.</span></span> <span data-ttu-id="c6d86-124">Voici un fragment de code permettant de créer un élément de nom dans le modèle DOM :</span><span class="sxs-lookup"><span data-stu-id="c6d86-124">Here is a fragment of the code to create a name element in DOM:</span></span>  
  
```csharp  
XmlDocument doc = new XmlDocument();  
XmlElement name = doc.CreateElement("Name");  
name.InnerText = "Patrick Hines";  
doc.AppendChild(name);  
```  
  
 <span data-ttu-id="c6d86-125">Si vous souhaitez utiliser un élément dans plusieurs documents, vous devez importer les nœuds d'un document à un autre.</span><span class="sxs-lookup"><span data-stu-id="c6d86-125">If you want to use an element across multiple documents, you must import the nodes across documents.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="c6d86-126">évite cette couche de complexité.</span><span class="sxs-lookup"><span data-stu-id="c6d86-126">avoids this layer of complexity.</span></span>  
  
 <span data-ttu-id="c6d86-127">Lors de l'utilisation de LINQ to XML, vous utilisez la classe <xref:System.Xml.Linq.XDocument> uniquement si vous souhaitez ajouter un commentaire ou une information de traitement au niveau racine du document.</span><span class="sxs-lookup"><span data-stu-id="c6d86-127">When using LINQ to XML, you use the <xref:System.Xml.Linq.XDocument> class only if you want to add a comment or processing instruction at the root level of the document.</span></span>  
  
## <a name="simplified-handling-of-names-and-namespaces"></a><span data-ttu-id="c6d86-128">Gestion simplifiée des noms et des espaces de noms</span><span class="sxs-lookup"><span data-stu-id="c6d86-128">Simplified Handling of Names and Namespaces</span></span>  
 <span data-ttu-id="c6d86-129">La gestion des noms, des espaces de noms et des préfixes d'espaces de noms est généralement un aspect complexe de la programmation XML.</span><span class="sxs-lookup"><span data-stu-id="c6d86-129">Handling names, namespaces, and namespace prefixes is generally a complex part of XML programming.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="c6d86-130">simplifie les noms et les espaces de noms en éliminant la nécessité de gérer les préfixes d’espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="c6d86-130">simplifies names and namespaces by eliminating the requirement to deal with namespace prefixes.</span></span> <span data-ttu-id="c6d86-131">Vous pouvez si vous le souhaitez contrôler les préfixes d'espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="c6d86-131">If you want to control namespace prefixes, you can.</span></span> <span data-ttu-id="c6d86-132">Si vous décidez cependant de ne pas contrôler explicitement les préfixes d’espaces de noms, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] affecte des préfixes d’espaces de noms lors de la sérialisation s’ils sont nécessaires ou, s’ils ne le sont pas, sérialise en utilisant les espaces de noms par défaut.</span><span class="sxs-lookup"><span data-stu-id="c6d86-132">But if you decide to not explicitly control namespace prefixes, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] will assign namespace prefixes during serialization if they are required, or will serialize using default namespaces if they are not.</span></span> <span data-ttu-id="c6d86-133">Si des espaces de noms par défaut sont utilisés, il n'y aura pas de préfixes d'espaces de noms dans le document résultant.</span><span class="sxs-lookup"><span data-stu-id="c6d86-133">If default namespaces are used, there will be no namespace prefixes in the resulting document.</span></span> <span data-ttu-id="c6d86-134">Pour plus d’informations, consultez [Vue d’ensemble des espaces de noms (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="c6d86-134">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="c6d86-135">L'un des autres problèmes associés au modèle DOM est qu'il ne vous permet pas de modifier le nom d'un nœud.</span><span class="sxs-lookup"><span data-stu-id="c6d86-135">Another problem with the DOM is that it does not let you change the name of a node.</span></span> <span data-ttu-id="c6d86-136">Au lieu de cela, vous devez créer un nouveau nœud et y copier tous les nœuds enfants, perdant ainsi l'identité de nœud d'origine.</span><span class="sxs-lookup"><span data-stu-id="c6d86-136">Instead, you have to create a new node and copy all the child nodes to it, losing the original node identity.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="c6d86-137">évite ce problème en vous permettant de définir la propriété <xref:System.Xml.Linq.XName> sur un nœud.</span><span class="sxs-lookup"><span data-stu-id="c6d86-137">avoids this problem by enabling you to set the <xref:System.Xml.Linq.XName> property on a node.</span></span>  
  
## <a name="static-method-support-for-loading-xml"></a><span data-ttu-id="c6d86-138">Prise en charge des méthodes statiques pour le chargement de données XML</span><span class="sxs-lookup"><span data-stu-id="c6d86-138">Static Method Support for Loading XML</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="c6d86-139">vous permet de charger du code XML en utilisant des méthodes statiques au lieu de méthodes d’instance.</span><span class="sxs-lookup"><span data-stu-id="c6d86-139">lets you load XML by using static methods, instead of instance methods.</span></span> <span data-ttu-id="c6d86-140">Cela simplifie le chargement et l'analyse.</span><span class="sxs-lookup"><span data-stu-id="c6d86-140">This simplifies loading and parsing.</span></span> <span data-ttu-id="c6d86-141">Pour plus d’informations, consultez Guide pratique [pour charger du code XML à partir d’un fichier (C#)](./how-to-load-xml-from-a-file.md).</span><span class="sxs-lookup"><span data-stu-id="c6d86-141">For more information, see [How to load XML from a file (C#)](./how-to-load-xml-from-a-file.md).</span></span>  
  
## <a name="removal-of-support-for-dtd-constructs"></a><span data-ttu-id="c6d86-142">Suppression de la prise en charge des constructions de DTD</span><span class="sxs-lookup"><span data-stu-id="c6d86-142">Removal of Support for DTD Constructs</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="c6d86-143">simplifie la programmation XML en supprimant la prise en charge des entités et des références d'entités.</span><span class="sxs-lookup"><span data-stu-id="c6d86-143">further simplifies XML programming by removing support for entities and entity references.</span></span> <span data-ttu-id="c6d86-144">La gestion des entités est complexe et rarement utilisée.</span><span class="sxs-lookup"><span data-stu-id="c6d86-144">The management of entities is complex, and is rarely used.</span></span> <span data-ttu-id="c6d86-145">La suppression de leur prise en charge augmente les performances et simplifie l'interface de programmation.</span><span class="sxs-lookup"><span data-stu-id="c6d86-145">Removing their support increases performance and simplifies the programming interface.</span></span> <span data-ttu-id="c6d86-146">Quand une arborescence [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] est remplie, toutes les entités DTD sont développées.</span><span class="sxs-lookup"><span data-stu-id="c6d86-146">When a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] tree is populated, all DTD entities are expanded.</span></span>  
  
## <a name="support-for-fragments"></a><span data-ttu-id="c6d86-147">Prise en charge des fragments</span><span class="sxs-lookup"><span data-stu-id="c6d86-147">Support for Fragments</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="c6d86-148">ne fournit pas d’équivalent pour la classe `XmlDocumentFragment`.</span><span class="sxs-lookup"><span data-stu-id="c6d86-148">does not provide an equivalent for the `XmlDocumentFragment` class.</span></span> <span data-ttu-id="c6d86-149">Dans de nombreux cas, cependant, le concept de `XmlDocumentFragment` peut être géré par le résultat d’une requête typée <xref:System.Collections.Generic.IEnumerable%601> de <xref:System.Xml.Linq.XNode> ou <xref:System.Collections.Generic.IEnumerable%601> de <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="c6d86-149">In many cases, however, the `XmlDocumentFragment` concept can be handled by the result of a query that is typed as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XNode>, or <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>.</span></span>  
  
## <a name="support-for-xpathnavigator"></a><span data-ttu-id="c6d86-150">Prise en charge de XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="c6d86-150">Support for XPathNavigator</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="c6d86-151">fournit une prise en charge pour <xref:System.Xml.XPath.XPathNavigator> via les méthodes d’extension de l’espace de noms <xref:System.Xml.XPath?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c6d86-151">provides support for <xref:System.Xml.XPath.XPathNavigator> through extension methods in the <xref:System.Xml.XPath?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="c6d86-152">Pour plus d’informations, consultez <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c6d86-152">For more information, see <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span></span>  
  
## <a name="support-for-white-space-and-indentation"></a><span data-ttu-id="c6d86-153">Prise en charge des espaces blancs et de la mise en retrait</span><span class="sxs-lookup"><span data-stu-id="c6d86-153">Support for White Space and Indentation</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="c6d86-154">gère les espaces plus simplement que le modèle DOM.</span><span class="sxs-lookup"><span data-stu-id="c6d86-154">handles white space more simply than the DOM.</span></span>  
  
 <span data-ttu-id="c6d86-155">Un scénario courant consiste à lire le code XML mis en retrait, à créer une arborescence XML en mémoire sans nœuds d'espaces (autrement dit, ne pas conserver les espaces), à effectuer certaines opérations sur le code XML, puis à enregistrer le code XML avec mise en retrait.</span><span class="sxs-lookup"><span data-stu-id="c6d86-155">A common scenario is to read indented XML, create an in-memory XML tree without any white space text nodes (that is, not preserving white space), perform some operations on the XML, and then save the XML with indentation.</span></span> <span data-ttu-id="c6d86-156">Lorsque vous sérialisez le code XML avec mise en forme, seuls les espaces significatifs dans l'arborescence XML sont conservés.</span><span class="sxs-lookup"><span data-stu-id="c6d86-156">When you serialize the XML with formatting, only significant white space in the XML tree is preserved.</span></span> <span data-ttu-id="c6d86-157">Il s'agit du comportement par défaut pour [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c6d86-157">This is the default behavior for [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="c6d86-158">Un autre scénario courant consiste à lire et à modifier du code XML qui a déjà été intentionnellement mis en retrait.</span><span class="sxs-lookup"><span data-stu-id="c6d86-158">Another common scenario is to read and modify XML that has already been intentionally indented.</span></span> <span data-ttu-id="c6d86-159">Vous ne souhaiterez peut-être modifier cette mise en retrait en aucune manière.</span><span class="sxs-lookup"><span data-stu-id="c6d86-159">You might not want to change this indentation in any way.</span></span> <span data-ttu-id="c6d86-160">Dans [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], vous devez pour cela conserver les espaces lorsque vous chargez ou analysez le code XML et que vous désactivez la mise en forme lors de la sérialisation du code XML.</span><span class="sxs-lookup"><span data-stu-id="c6d86-160">In [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can do this by preserving white space when you load or parse the XML and disabling formatting when you serialize the XML.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="c6d86-161">stocke les espaces en tant que nœud <xref:System.Xml.Linq.XText> au lieu de faire appel à un type de nœud <xref:System.Xml.XmlNodeType.Whitespace> spécialisé, comme le fait DOM.</span><span class="sxs-lookup"><span data-stu-id="c6d86-161">stores white space as an <xref:System.Xml.Linq.XText> node, instead of having a specialized <xref:System.Xml.XmlNodeType.Whitespace> node type, as the DOM does.</span></span>  
  
## <a name="support-for-annotations"></a><span data-ttu-id="c6d86-162">Prise en charge des annotations</span><span class="sxs-lookup"><span data-stu-id="c6d86-162">Support for Annotations</span></span>  
 <span data-ttu-id="c6d86-163">Les éléments [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] prennent en charge un ensemble extensible d'annotations.</span><span class="sxs-lookup"><span data-stu-id="c6d86-163">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] elements support an extensible set of annotations.</span></span> <span data-ttu-id="c6d86-164">Cela est utile pour assurer le suivi de diverses informations relatives à un élément, telles que des informations de schéma, le fait que l'élément soit lié à une interface utilisateur ou tout autre type d'informations spécifiques aux applications.</span><span class="sxs-lookup"><span data-stu-id="c6d86-164">This is useful for tracking miscellaneous information about an element, such as schema information, information about whether the element is bound to a UI, or any other kind of application-specific information.</span></span> <span data-ttu-id="c6d86-165">Pour plus d’informations, consultez [Annotations LINQ to XML](./linq-to-xml-annotations.md).</span><span class="sxs-lookup"><span data-stu-id="c6d86-165">For more information, see [LINQ to XML Annotations](./linq-to-xml-annotations.md).</span></span>  
  
## <a name="support-for-schema-information"></a><span data-ttu-id="c6d86-166">Prise en charge des informations de schéma</span><span class="sxs-lookup"><span data-stu-id="c6d86-166">Support for Schema Information</span></span>  
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="c6d86-167">fournit une prise en charge de la validation XSD via les méthodes d’extension de l’espace de noms <xref:System.Xml.Schema?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c6d86-167">provides support for XSD validation through extension methods in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="c6d86-168">Vous pouvez valider la conformité d’une arborescence XML à un schéma XSD.</span><span class="sxs-lookup"><span data-stu-id="c6d86-168">You can validate that an XML tree complies with an XSD.</span></span> <span data-ttu-id="c6d86-169">Vous pouvez remplir l’arborescence XML avec le PSVI (Post-Schema-Validation Infoset).</span><span class="sxs-lookup"><span data-stu-id="c6d86-169">You can populate the XML tree with the post-schema-validation infoset (PSVI).</span></span> <span data-ttu-id="c6d86-170">Pour plus d’informations, consultez [Comment valider à l’aide de XSD](./how-to-validate-using-xsd-linq-to-xml.md) et <xref:System.Xml.Schema.Extensions> .</span><span class="sxs-lookup"><span data-stu-id="c6d86-170">For more information, see [How to validate using XSD](./how-to-validate-using-xsd-linq-to-xml.md) and <xref:System.Xml.Schema.Extensions>.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="c6d86-171">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c6d86-171">See also</span></span>

- [<span data-ttu-id="c6d86-172">Mise en route (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="c6d86-172">Getting Started (LINQ to XML)</span></span>](./linq-to-xml-overview.md)
