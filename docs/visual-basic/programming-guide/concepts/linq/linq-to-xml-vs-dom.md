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
# <a name="linq-to-xml-vs-dom-visual-basic"></a><span data-ttu-id="d7343-102">LINQ to XML et DOM (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d7343-102">LINQ to XML vs. DOM (Visual Basic)</span></span>
<span data-ttu-id="d7343-103">Cette section décrit certaines des principales différences entre [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] et l’API de programmation XML actuellement prédominante, le modèle DOM (Document Object Model) W3C.</span><span class="sxs-lookup"><span data-stu-id="d7343-103">This section describes some key differences between [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] and the current predominant XML programming API, the W3C Document Object Model (DOM).</span></span>  
  
## <a name="new-ways-to-construct-xml-trees"></a><span data-ttu-id="d7343-104">Nouvelles manières de construire des arborescences XML</span><span class="sxs-lookup"><span data-stu-id="d7343-104">New Ways to Construct XML Trees</span></span>  
 <span data-ttu-id="d7343-105">Dans le modèle DOM W3C, vous construisez une arborescence XML de bas en haut ; autrement dit, vous créez un document, vous créez des éléments, puis vous ajoutez les éléments au document.</span><span class="sxs-lookup"><span data-stu-id="d7343-105">In the W3C DOM, you build an XML tree from the bottom up; that is, you create a document, you create elements, and then you add the elements to the document.</span></span>  
  
 <span data-ttu-id="d7343-106">Voici un exemple typique de création d’une arborescence XML à l’aide de l’implémentation Microsoft du modèle DOM, <xref:System.Xml.XmlDocument> :</span><span class="sxs-lookup"><span data-stu-id="d7343-106">For example, the following would be a typical way to create an XML tree using the Microsoft implementation of DOM, <xref:System.Xml.XmlDocument>:</span></span>  
  
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
  
 <span data-ttu-id="d7343-107">Ce style de codage ne fournit visuellement que peu d’informations concernant la structure de l’arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="d7343-107">This style of coding does not visually provide much information about the structure of the XML tree.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="d7343-108">prend en charge cette approche de la construction d’une arborescence XML, mais également une approche alternative, la *construction fonctionnelle*.</span><span class="sxs-lookup"><span data-stu-id="d7343-108">supports this approach to constructing an XML tree, but also supports an alternative approach, *functional construction*.</span></span> <span data-ttu-id="d7343-109">Dans Visual Basic, la construction fonctionnelle utilise des littéraux XML pour générer une arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="d7343-109">In Visual Basic, functional construction uses XML literals to build an XML tree.</span></span>  
  
 <span data-ttu-id="d7343-110">Voici comment vous pouvez construire la même arborescence XML à l’aide de la construction fonctionnelle [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="d7343-110">Here is how you would construct the same XML tree by using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] functional construction:</span></span>  
  
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
  
 <span data-ttu-id="d7343-111">Notez que la mise en retrait du code pour construire l’arborescence XML affiche la structure des données XML sous-jacentes.</span><span class="sxs-lookup"><span data-stu-id="d7343-111">Notice that indenting the code to construct the XML tree shows the structure of the underlying XML.</span></span>  
  
 <span data-ttu-id="d7343-112">Pour plus d’informations, consultez [création d’arborescences XML (Visual Basic)](creating-xml-trees.md).</span><span class="sxs-lookup"><span data-stu-id="d7343-112">For more information, see [Creating XML Trees (Visual Basic)](creating-xml-trees.md).</span></span>  
  
## <a name="working-directly-with-xml-elements"></a><span data-ttu-id="d7343-113">Utilisation directe des éléments XML</span><span class="sxs-lookup"><span data-stu-id="d7343-113">Working Directly with XML Elements</span></span>  
 <span data-ttu-id="d7343-114">Lorsque vous programmez avec des données XML, vous travaillez en général principalement avec les éléments XML et éventuellement les attributs.</span><span class="sxs-lookup"><span data-stu-id="d7343-114">When you program with XML, your primary focus is usually on XML elements and perhaps on attributes.</span></span> <span data-ttu-id="d7343-115">Dans [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], vous pouvez utiliser directement les éléments et les attributs XML.</span><span class="sxs-lookup"><span data-stu-id="d7343-115">In [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can work directly with XML elements and attributes.</span></span> <span data-ttu-id="d7343-116">Vous pouvez par exemple effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="d7343-116">For example, you can do the following:</span></span>  
  
- <span data-ttu-id="d7343-117">Créer des éléments XML sans utiliser d'objet de document.</span><span class="sxs-lookup"><span data-stu-id="d7343-117">Create XML elements without using a document object at all.</span></span> <span data-ttu-id="d7343-118">Cela simplifie la programmation lorsque vous devez travailler avec des fragments d'arborescences XML.</span><span class="sxs-lookup"><span data-stu-id="d7343-118">This simplifies programming when you have to work with fragments of XML trees.</span></span>  
  
- <span data-ttu-id="d7343-119">Charger des objets `T:System.Xml.Linq.XElement` directement à partir d'un fichier XML.</span><span class="sxs-lookup"><span data-stu-id="d7343-119">Load `T:System.Xml.Linq.XElement` objects directly from an XML file.</span></span>  
  
- <span data-ttu-id="d7343-120">Sérialiser des objets `T:System.Xml.Linq.XElement` dans un fichier ou un flux.</span><span class="sxs-lookup"><span data-stu-id="d7343-120">Serialize `T:System.Xml.Linq.XElement` objects to a file or a stream.</span></span>  
  
 <span data-ttu-id="d7343-121">Comparez cela au modèle DOM W3C, dans lequel le document XML est utilisé en tant que conteneur logique pour l'arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="d7343-121">Compare this to the W3C DOM, in which the XML document is used as a logical container for the XML tree.</span></span> <span data-ttu-id="d7343-122">Dans le modèle DOM, les nœuds XML, y compris les éléments et attributs, doivent être créés dans le contexte d'un document XML.</span><span class="sxs-lookup"><span data-stu-id="d7343-122">In DOM, XML nodes, including elements and attributes, must be created in the context of an XML document.</span></span> <span data-ttu-id="d7343-123">Voici un fragment de code permettant de créer un élément de nom dans le modèle DOM :</span><span class="sxs-lookup"><span data-stu-id="d7343-123">Here is a fragment of the code to create a name element in DOM:</span></span>  
  
```vb  
Dim doc As XmlDocument = New XmlDocument()  
Dim name As XmlElement = doc.CreateElement("Name")  
name.InnerText = "Patrick Hines"  
doc.AppendChild(name)  
```  
  
 <span data-ttu-id="d7343-124">Si vous souhaitez utiliser un élément dans plusieurs documents, vous devez importer les nœuds d'un document à un autre.</span><span class="sxs-lookup"><span data-stu-id="d7343-124">If you want to use an element across multiple documents, you must import the nodes across documents.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="d7343-125">évite cette couche de complexité.</span><span class="sxs-lookup"><span data-stu-id="d7343-125">avoids this layer of complexity.</span></span>  
  
 <span data-ttu-id="d7343-126">Lors de l'utilisation de LINQ to XML, vous utilisez la classe <xref:System.Xml.Linq.XDocument> uniquement si vous souhaitez ajouter un commentaire ou une information de traitement au niveau racine du document.</span><span class="sxs-lookup"><span data-stu-id="d7343-126">When using LINQ to XML, you use the <xref:System.Xml.Linq.XDocument> class only if you want to add a comment or processing instruction at the root level of the document.</span></span>  
  
## <a name="simplified-handling-of-names-and-namespaces"></a><span data-ttu-id="d7343-127">Gestion simplifiée des noms et des espaces de noms</span><span class="sxs-lookup"><span data-stu-id="d7343-127">Simplified Handling of Names and Namespaces</span></span>  
 <span data-ttu-id="d7343-128">La gestion des noms, des espaces de noms et des préfixes d'espaces de noms est généralement un aspect complexe de la programmation XML.</span><span class="sxs-lookup"><span data-stu-id="d7343-128">Handling names, namespaces, and namespace prefixes is generally a complex part of XML programming.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="d7343-129">simplifie les noms et les espaces de noms en éliminant la nécessité de gérer les préfixes d’espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="d7343-129">simplifies names and namespaces by eliminating the requirement to deal with namespace prefixes.</span></span> <span data-ttu-id="d7343-130">Vous pouvez si vous le souhaitez contrôler les préfixes d'espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="d7343-130">If you want to control namespace prefixes, you can.</span></span> <span data-ttu-id="d7343-131">Si vous décidez cependant de ne pas contrôler explicitement les préfixes d’espaces de noms, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] affecte des préfixes d’espaces de noms lors de la sérialisation s’ils sont nécessaires ou, s’ils ne le sont pas, sérialise en utilisant les espaces de noms par défaut.</span><span class="sxs-lookup"><span data-stu-id="d7343-131">But if you decide to not explicitly control namespace prefixes, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] will assign namespace prefixes during serialization if they are required, or will serialize using default namespaces if they are not.</span></span> <span data-ttu-id="d7343-132">Si des espaces de noms par défaut sont utilisés, il n'y aura pas de préfixes d'espaces de noms dans le document résultant.</span><span class="sxs-lookup"><span data-stu-id="d7343-132">If default namespaces are used, there will be no namespace prefixes in the resulting document.</span></span> <span data-ttu-id="d7343-133">Pour plus d’informations, consultez [vue d’ensemble des espaces de noms (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="d7343-133">For more information, see [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="d7343-134">L'un des autres problèmes associés au modèle DOM est qu'il ne vous permet pas de modifier le nom d'un nœud.</span><span class="sxs-lookup"><span data-stu-id="d7343-134">Another problem with the DOM is that it does not let you change the name of a node.</span></span> <span data-ttu-id="d7343-135">Au lieu de cela, vous devez créer un nouveau nœud et y copier tous les nœuds enfants, perdant ainsi l'identité de nœud d'origine.</span><span class="sxs-lookup"><span data-stu-id="d7343-135">Instead, you have to create a new node and copy all the child nodes to it, losing the original node identity.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="d7343-136">évite ce problème en vous permettant de définir la propriété <xref:System.Xml.Linq.XName> sur un nœud.</span><span class="sxs-lookup"><span data-stu-id="d7343-136">avoids this problem by enabling you to set the <xref:System.Xml.Linq.XName> property on a node.</span></span>  
  
## <a name="static-method-support-for-loading-xml"></a><span data-ttu-id="d7343-137">Prise en charge des méthodes statiques pour le chargement de données XML</span><span class="sxs-lookup"><span data-stu-id="d7343-137">Static Method Support for Loading XML</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="d7343-138">vous permet de charger du code XML en utilisant des méthodes statiques au lieu de méthodes d’instance.</span><span class="sxs-lookup"><span data-stu-id="d7343-138">lets you load XML by using static methods, instead of instance methods.</span></span> <span data-ttu-id="d7343-139">Cela simplifie le chargement et l'analyse.</span><span class="sxs-lookup"><span data-stu-id="d7343-139">This simplifies loading and parsing.</span></span> <span data-ttu-id="d7343-140">Pour plus d’informations, consultez [Comment : charger du code XML à partir d’un fichier (Visual Basic)](how-to-load-xml-from-a-file.md).</span><span class="sxs-lookup"><span data-stu-id="d7343-140">For more information, see [How to: Load XML from a File (Visual Basic)](how-to-load-xml-from-a-file.md).</span></span>  
  
## <a name="removal-of-support-for-dtd-constructs"></a><span data-ttu-id="d7343-141">Suppression de la prise en charge des constructions de DTD</span><span class="sxs-lookup"><span data-stu-id="d7343-141">Removal of Support for DTD Constructs</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="d7343-142">simplifie la programmation XML en supprimant la prise en charge des entités et des références d'entités.</span><span class="sxs-lookup"><span data-stu-id="d7343-142">further simplifies XML programming by removing support for entities and entity references.</span></span> <span data-ttu-id="d7343-143">La gestion des entités est complexe et rarement utilisée.</span><span class="sxs-lookup"><span data-stu-id="d7343-143">The management of entities is complex, and is rarely used.</span></span> <span data-ttu-id="d7343-144">La suppression de leur prise en charge augmente les performances et simplifie l'interface de programmation.</span><span class="sxs-lookup"><span data-stu-id="d7343-144">Removing their support increases performance and simplifies the programming interface.</span></span> <span data-ttu-id="d7343-145">Quand une arborescence [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] est remplie, toutes les entités DTD sont développées.</span><span class="sxs-lookup"><span data-stu-id="d7343-145">When a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] tree is populated, all DTD entities are expanded.</span></span>  
  
## <a name="support-for-fragments"></a><span data-ttu-id="d7343-146">Prise en charge des fragments</span><span class="sxs-lookup"><span data-stu-id="d7343-146">Support for Fragments</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="d7343-147">ne fournit pas d’équivalent pour la classe `XmlDocumentFragment`.</span><span class="sxs-lookup"><span data-stu-id="d7343-147">does not provide an equivalent for the `XmlDocumentFragment` class.</span></span> <span data-ttu-id="d7343-148">Dans de nombreux cas, cependant, le concept de `XmlDocumentFragment` peut être géré par le résultat d’une requête typée <xref:System.Collections.Generic.IEnumerable%601> de <xref:System.Xml.Linq.XNode> ou <xref:System.Collections.Generic.IEnumerable%601> de <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="d7343-148">In many cases, however, the `XmlDocumentFragment` concept can be handled by the result of a query that is typed as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XNode>, or <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>.</span></span>  
  
## <a name="support-for-xpathnavigator"></a><span data-ttu-id="d7343-149">Prise en charge de XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="d7343-149">Support for XPathNavigator</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="d7343-150">fournit une prise en charge pour <xref:System.Xml.XPath.XPathNavigator> via les méthodes d’extension de l’espace de noms <xref:System.Xml.XPath?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d7343-150">provides support for <xref:System.Xml.XPath.XPathNavigator> through extension methods in the <xref:System.Xml.XPath?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="d7343-151">Pour plus d’informations, consultez <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d7343-151">For more information, see <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span></span>  
  
## <a name="support-for-white-space-and-indentation"></a><span data-ttu-id="d7343-152">Prise en charge des espaces blancs et de la mise en retrait</span><span class="sxs-lookup"><span data-stu-id="d7343-152">Support for White Space and Indentation</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="d7343-153">gère les espaces plus simplement que le modèle DOM.</span><span class="sxs-lookup"><span data-stu-id="d7343-153">handles white space more simply than the DOM.</span></span>  
  
 <span data-ttu-id="d7343-154">Un scénario courant consiste à lire le code XML mis en retrait, à créer une arborescence XML en mémoire sans nœuds d'espaces (autrement dit, ne pas conserver les espaces), à effectuer certaines opérations sur le code XML, puis à enregistrer le code XML avec mise en retrait.</span><span class="sxs-lookup"><span data-stu-id="d7343-154">A common scenario is to read indented XML, create an in-memory XML tree without any white space text nodes (that is, not preserving white space), perform some operations on the XML, and then save the XML with indentation.</span></span> <span data-ttu-id="d7343-155">Lorsque vous sérialisez le code XML avec mise en forme, seuls les espaces significatifs dans l'arborescence XML sont conservés.</span><span class="sxs-lookup"><span data-stu-id="d7343-155">When you serialize the XML with formatting, only significant white space in the XML tree is preserved.</span></span> <span data-ttu-id="d7343-156">Il s'agit du comportement par défaut pour [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d7343-156">This is the default behavior for [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="d7343-157">Un autre scénario courant consiste à lire et à modifier du code XML qui a déjà été intentionnellement mis en retrait.</span><span class="sxs-lookup"><span data-stu-id="d7343-157">Another common scenario is to read and modify XML that has already been intentionally indented.</span></span> <span data-ttu-id="d7343-158">Vous ne souhaiterez peut-être modifier cette mise en retrait en aucune manière.</span><span class="sxs-lookup"><span data-stu-id="d7343-158">You might not want to change this indentation in any way.</span></span> <span data-ttu-id="d7343-159">Dans [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], vous devez pour cela conserver les espaces lorsque vous chargez ou analysez le code XML et que vous désactivez la mise en forme lors de la sérialisation du code XML.</span><span class="sxs-lookup"><span data-stu-id="d7343-159">In [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can do this by preserving white space when you load or parse the XML and disabling formatting when you serialize the XML.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="d7343-160">stocke les espaces en tant que nœud <xref:System.Xml.Linq.XText> au lieu de faire appel à un type de nœud <xref:System.Xml.XmlNodeType.Whitespace> spécialisé, comme le fait DOM.</span><span class="sxs-lookup"><span data-stu-id="d7343-160">stores white space as an <xref:System.Xml.Linq.XText> node, instead of having a specialized <xref:System.Xml.XmlNodeType.Whitespace> node type, as the DOM does.</span></span>  
  
## <a name="support-for-annotations"></a><span data-ttu-id="d7343-161">Prise en charge des annotations</span><span class="sxs-lookup"><span data-stu-id="d7343-161">Support for Annotations</span></span>  
 <span data-ttu-id="d7343-162">Les éléments [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] prennent en charge un ensemble extensible d'annotations.</span><span class="sxs-lookup"><span data-stu-id="d7343-162">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] elements support an extensible set of annotations.</span></span> <span data-ttu-id="d7343-163">Cela est utile pour assurer le suivi de diverses informations relatives à un élément, telles que des informations de schéma, le fait que l'élément soit lié à une interface utilisateur ou tout autre type d'informations spécifiques aux applications.</span><span class="sxs-lookup"><span data-stu-id="d7343-163">This is useful for tracking miscellaneous information about an element, such as schema information, information about whether the element is bound to a UI, or any other kind of application-specific information.</span></span> <span data-ttu-id="d7343-164">Pour plus d’informations, consultez [Annotations LINQ to XML](linq-to-xml-annotations.md).</span><span class="sxs-lookup"><span data-stu-id="d7343-164">For more information, see [LINQ to XML Annotations](linq-to-xml-annotations.md).</span></span>  
  
## <a name="support-for-schema-information"></a><span data-ttu-id="d7343-165">Prise en charge des informations de schéma</span><span class="sxs-lookup"><span data-stu-id="d7343-165">Support for Schema Information</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="d7343-166">fournit une prise en charge de la validation XSD via les méthodes d’extension de l’espace de noms <xref:System.Xml.Schema?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d7343-166">provides support for XSD validation through extension methods in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="d7343-167">Vous pouvez valider la conformité d’une arborescence XML à un schéma XSD.</span><span class="sxs-lookup"><span data-stu-id="d7343-167">You can validate that an XML tree complies with an XSD.</span></span> <span data-ttu-id="d7343-168">Vous pouvez remplir l’arborescence XML avec le PSVI (Post-Schema-Validation Infoset).</span><span class="sxs-lookup"><span data-stu-id="d7343-168">You can populate the XML tree with the post-schema-validation infoset (PSVI).</span></span> <span data-ttu-id="d7343-169">Pour plus d’informations, consultez [Guide pratique pour valider à l’aide de XSD](how-to-validate-using-xsd-linq-to-xml.md) et <xref:System.Xml.Schema.Extensions>.</span><span class="sxs-lookup"><span data-stu-id="d7343-169">For more information, see [How to: Validate Using XSD](how-to-validate-using-xsd-linq-to-xml.md) and <xref:System.Xml.Schema.Extensions>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7343-170">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d7343-170">See also</span></span>

- [<span data-ttu-id="d7343-171">Mise en route (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="d7343-171">Getting Started (LINQ to XML)</span></span>](getting-started-linq-to-xml.md)
