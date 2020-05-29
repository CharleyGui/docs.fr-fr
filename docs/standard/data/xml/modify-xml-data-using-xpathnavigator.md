---
title: Modification de données XML à l’aide de XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 03a7c5a1-b296-4af4-b209-043c958dc0a5
ms.openlocfilehash: ea42cbfe7427e026f5e3339af5f5a2ceec17dad3
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84202199"
---
# <a name="modify-xml-data-using-xpathnavigator"></a><span data-ttu-id="96733-102">Modification de données XML à l’aide de XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="96733-102">Modify XML Data using XPathNavigator</span></span>
<span data-ttu-id="96733-103">La classe <xref:System.Xml.XPath.XPathNavigator> fournit un ensemble de méthodes permettant de modifier les nœuds et les valeurs d'un document XML.</span><span class="sxs-lookup"><span data-stu-id="96733-103">The <xref:System.Xml.XPath.XPathNavigator> class provides a set of methods used to modify nodes and values in an XML document.</span></span> <span data-ttu-id="96733-104">Pour pouvoir utiliser ces méthodes, vous devez pouvoir modifier l'objet <xref:System.Xml.XPath.XPathNavigator>, ce qui signifie que sa propriété <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> doit être `true`.</span><span class="sxs-lookup"><span data-stu-id="96733-104">In order to use these methods, the <xref:System.Xml.XPath.XPathNavigator> object must be editable, that is, its <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> property must be `true`.</span></span>  
  
 <span data-ttu-id="96733-105">Les objets <xref:System.Xml.XPath.XPathNavigator> qui permettent d'éditer un document XML sont créés par la méthode <xref:System.Xml.XmlDocument.CreateNavigator%2A> de la classe <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="96733-105"><xref:System.Xml.XPath.XPathNavigator> objects that can edit an XML document are created by the <xref:System.Xml.XmlDocument.CreateNavigator%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="96733-106">Les objets <xref:System.Xml.XPath.XPathNavigator> créés par la classe <xref:System.Xml.XPath.XPathDocument> sont en lecture seule et toute tentative d'utilisation des méthodes de modification d'un objet <xref:System.Xml.XPath.XPathNavigator> créé par un objet <xref:System.Xml.XPath.XPathDocument> se traduit par un objet <xref:System.NotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="96733-106"><xref:System.Xml.XPath.XPathNavigator> objects created by the <xref:System.Xml.XPath.XPathDocument> class are read-only and any attempt to use the editing methods of an <xref:System.Xml.XPath.XPathNavigator> object created by an <xref:System.Xml.XPath.XPathDocument> object result in a <xref:System.NotSupportedException>.</span></span>  
  
 <span data-ttu-id="96733-107">Pour plus d’informations sur la création d’objets <xref:System.Xml.XPath.XPathNavigator> modifiables, consultez [Lecture de données XML à l’aide de XPathDocument et XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).</span><span class="sxs-lookup"><span data-stu-id="96733-107">For more information about creating editable <xref:System.Xml.XPath.XPathNavigator> objects, see [Reading XML Data using XPathDocument and XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).</span></span>  
  
## <a name="modifying-nodes"></a><span data-ttu-id="96733-108">Modification de nœuds</span><span class="sxs-lookup"><span data-stu-id="96733-108">Modifying Nodes</span></span>  
 <span data-ttu-id="96733-109">Une technique simple de modification de la valeur d'un nœud consiste à utiliser les méthodes <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> et <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> de la classe <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="96733-109">A simple technique for changing the value of a node is to use the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> and <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> methods of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
 <span data-ttu-id="96733-110">Le tableau suivant répertorie les effets de ces méthodes sur différents types de nœuds.</span><span class="sxs-lookup"><span data-stu-id="96733-110">The following table lists the effects of these methods on different node types.</span></span>  
  
|<xref:System.Xml.XPath.XPathNodeType>|<span data-ttu-id="96733-111">Données modifiées</span><span class="sxs-lookup"><span data-stu-id="96733-111">Data Changed</span></span>|  
|---------------------------------------------------------------------------------------------------------------------------------------------|------------------|  
|<xref:System.Xml.XPath.XPathNodeType.Root>|<span data-ttu-id="96733-112">Non pris en charge.</span><span class="sxs-lookup"><span data-stu-id="96733-112">Not supported.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.Element>|<span data-ttu-id="96733-113">Contenu de l'élément.</span><span class="sxs-lookup"><span data-stu-id="96733-113">The content of the element.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.Attribute>|<span data-ttu-id="96733-114">Valeur de l'attribut.</span><span class="sxs-lookup"><span data-stu-id="96733-114">The value of the attribute.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.Text>|<span data-ttu-id="96733-115">Texte.</span><span class="sxs-lookup"><span data-stu-id="96733-115">The text content.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.ProcessingInstruction>|<span data-ttu-id="96733-116">Contenu, cible exclue.</span><span class="sxs-lookup"><span data-stu-id="96733-116">The content, excluding the target.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.Comment>|<span data-ttu-id="96733-117">Contenu du commentaire.</span><span class="sxs-lookup"><span data-stu-id="96733-117">The content of the comment.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.Namespace>|<span data-ttu-id="96733-118">Non pris en charge.</span><span class="sxs-lookup"><span data-stu-id="96733-118">Not Supported.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="96733-119">La modification des nœuds <xref:System.Xml.XPath.XPathNodeType.Namespace> ou <xref:System.Xml.XPath.XPathNodeType.Root> n'est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="96733-119">Editing <xref:System.Xml.XPath.XPathNodeType.Namespace> nodes or the <xref:System.Xml.XPath.XPathNodeType.Root> node is not supported.</span></span>  
  
 <span data-ttu-id="96733-120">La classe <xref:System.Xml.XPath.XPathNavigator> fournit également un ensemble de méthodes permettant d'insérer et de supprimer des nœuds.</span><span class="sxs-lookup"><span data-stu-id="96733-120">The <xref:System.Xml.XPath.XPathNavigator> class also provides a set of methods used to insert and remove nodes.</span></span> <span data-ttu-id="96733-121">Pour plus d’informations sur l’insertion et la suppression de nœuds d’un document XML, consultez les rubriques [Insertion de données XML à l’aide de XPathNavigator](../../../../docs/standard/data/xml/insert-xml-data-using-xpathnavigator.md) et [Suppression de données XML à l’aide de XPathNavigator](../../../../docs/standard/data/xml/remove-xml-data-using-xpathnavigator.md).</span><span class="sxs-lookup"><span data-stu-id="96733-121">For more information about inserting and removing nodes from an XML document, see the [Insert XML Data using XPathNavigator](../../../../docs/standard/data/xml/insert-xml-data-using-xpathnavigator.md) and [Remove XML Data using XPathNavigator](../../../../docs/standard/data/xml/remove-xml-data-using-xpathnavigator.md) topics.</span></span>  
  
### <a name="modifying-untyped-values"></a><span data-ttu-id="96733-122">Modification de valeurs non typées</span><span class="sxs-lookup"><span data-stu-id="96733-122">Modifying Untyped Values</span></span>  
 <span data-ttu-id="96733-123">La méthode <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> insère simplement la valeur `string` non typée transmise sous la forme d'un paramètre comme la valeur du nœud sur lequel l'objet <xref:System.Xml.XPath.XPathNavigator> est actuellement positionné.</span><span class="sxs-lookup"><span data-stu-id="96733-123">The <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method simply inserts the untyped `string` value passed as a parameter as the value of the node the <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span> <span data-ttu-id="96733-124">La valeur est insérée sans type ou sans vérifier que la nouvelle valeur est valide par rapport au type de nœud si les informations sur le schéma sont disponibles.</span><span class="sxs-lookup"><span data-stu-id="96733-124">The value is inserted without any type or without verifying that the new value is valid according to the type of the node if schema information is available.</span></span>  
  
 <span data-ttu-id="96733-125">Dans l'exemple suivant, la méthode <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> permet de mettre à jour tous les éléments `price` du fichier `contosoBooks.xml`.</span><span class="sxs-lookup"><span data-stu-id="96733-125">In the following example, the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method is used to update all `price` elements in the `contosoBooks.xml` file.</span></span>  
  
 [!code-cpp[XPathNavigatorMethods#47](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#47)]
 [!code-csharp[XPathNavigatorMethods#47](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#47)]
 [!code-vb[XPathNavigatorMethods#47](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#47)]  
  
 <span data-ttu-id="96733-126">L'exemple prend le fichier `contosoBooks.xml` comme entrée.</span><span class="sxs-lookup"><span data-stu-id="96733-126">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="modifying-typed-values"></a><span data-ttu-id="96733-127">Modification de valeurs typées</span><span class="sxs-lookup"><span data-stu-id="96733-127">Modifying Typed Values</span></span>  
 <span data-ttu-id="96733-128">Si le type d'un nœud est un type simple des schémas XML du W3C, la nouvelle valeur insérée par la méthode <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> est vérifiée par rapport aux facettes du type simple avant d'être définie.</span><span class="sxs-lookup"><span data-stu-id="96733-128">When the type of a node is a W3C XML Schema simple type, the new value inserted by the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method is checked against the facets of the simple type before the value is set.</span></span> <span data-ttu-id="96733-129">Si la nouvelle valeur n'est pas valide par rapport au type du nœud (par exemple, une valeur est définie sur `-1` pour un élément dont le type est `xs:positiveInteger`), une exception se produit.</span><span class="sxs-lookup"><span data-stu-id="96733-129">If the new value is not valid according to the type of the node (for example, setting a value of `-1` on an element whose type is `xs:positiveInteger`), it results in an exception.</span></span>  
  
 <span data-ttu-id="96733-130">L'exemple suivant tente de modifier la valeur de l'élément `price` du premier élément `book` du fichier `contosoBooks.xml` en valeur <xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="96733-130">The following example attempts to change the value of the `price` element of the first `book` element in the `contosoBooks.xml` file to a <xref:System.DateTime> value.</span></span> <span data-ttu-id="96733-131">Étant donné que le type de schéma XML de l'élément `price` est défini comme `xs:decimal` dans les fichiers `contosoBooks.xsd`, une exception se produit.</span><span class="sxs-lookup"><span data-stu-id="96733-131">Because the XML Schema type of the `price` element is defined as `xs:decimal` in the `contosoBooks.xsd` files, this results in an exception.</span></span>  
  
```vb  
Dim settings As XmlReaderSettings = New XmlReaderSettings()  
settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd")  
settings.ValidationType = ValidationType.Schema  
  
Dim reader As XmlReader = XmlReader.Create("contosoBooks.xml", settings)  
  
Dim document As XmlDocument = New XmlDocument()  
document.Load(reader)  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("price", "http://www.contoso.com/books")  
  
navigator.SetTypedValue(DateTime.Now)  
```  
  
```csharp  
XmlReaderSettings settings = new XmlReaderSettings();  
settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd");  
settings.ValidationType = ValidationType.Schema;  
  
XmlReader reader = XmlReader.Create("contosoBooks.xml", settings);  
  
XmlDocument document = new XmlDocument();  
document.Load(reader);  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books");  
navigator.MoveToChild("book", "http://www.contoso.com/books");  
navigator.MoveToChild("price", "http://www.contoso.com/books");  
  
navigator.SetTypedValue(DateTime.Now);  
```  
  
 <span data-ttu-id="96733-132">L'exemple prend le fichier `contosoBooks.xml` comme entrée.</span><span class="sxs-lookup"><span data-stu-id="96733-132">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="96733-133">L'exemple prend également le fichier `contosoBooks.xsd` comme entrée.</span><span class="sxs-lookup"><span data-stu-id="96733-133">The example also takes the `contosoBooks.xsd` as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
#### <a name="the-effects-of-editing-strongly-typed-xml-data"></a><span data-ttu-id="96733-134">Effets de la modification de données XML fortement typées</span><span class="sxs-lookup"><span data-stu-id="96733-134">The Effects of Editing Strongly Typed XML Data</span></span>  
 <span data-ttu-id="96733-135">La <xref:System.Xml.XPath.XPathNavigator> classe utilise le schéma XML W3C comme base pour décrire le XML fortement typé.</span><span class="sxs-lookup"><span data-stu-id="96733-135">The <xref:System.Xml.XPath.XPathNavigator> class uses the W3C XML Schema as a basis for describing strongly typed XML.</span></span> <span data-ttu-id="96733-136">Les éléments et les attributs ne peuvent pas être annotés avec les informations sur le type en fonction de la validation par rapport au document du W3C sur les schémas XML.</span><span class="sxs-lookup"><span data-stu-id="96733-136">Elements and attributes can be annotated with type information based on validation against a W3C XML Schema document.</span></span> <span data-ttu-id="96733-137">Les éléments pouvant contenir d'autres éléments ou attributs sont appelés types complexes, tandis que ceux qui ne peuvent avoir que du contenu textuel sont appelés types simples.</span><span class="sxs-lookup"><span data-stu-id="96733-137">Elements that can contain other elements or attributes are called complex types, while those that can only contain textual content are called simple types.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="96733-138">Les attributs ne peuvent avoir que des types simples.</span><span class="sxs-lookup"><span data-stu-id="96733-138">Attributes can only have simple types.</span></span>  
  
 <span data-ttu-id="96733-139">Un élément ou attribut peut être considéré comme valide pour le schéma s'il est conforme à toutes les règles spécifiques à sa définition de type.</span><span class="sxs-lookup"><span data-stu-id="96733-139">An element or attribute can be considered to be schema-valid if it conforms to all the rules specific to its type definition.</span></span> <span data-ttu-id="96733-140">Un élément ayant le type simple `xs:int` doit contenir une valeur numérique comprise entre -2147483648 et 2147483647 pour être valide pour le schéma.</span><span class="sxs-lookup"><span data-stu-id="96733-140">An element that has the simple type `xs:int` has to contain a numeric value between -2147483648 and 2147483647 to be schema-valid.</span></span> <span data-ttu-id="96733-141">Pour les types complexes, la validité de l'élément pour le schéma dépend de la validité pour le schéma de ses attributs et éléments enfants.</span><span class="sxs-lookup"><span data-stu-id="96733-141">For complex types, the schema-validity of the element is dependent on the schema-validity of its child elements and attributes.</span></span> <span data-ttu-id="96733-142">Donc, si un élément est valide par rapport à sa définition de type complexe, tous ses attributs et éléments enfants sont valides par rapport à leur définition de type.</span><span class="sxs-lookup"><span data-stu-id="96733-142">Thus if an element is valid against its complex type definition, all its child elements and attributes are valid against their type definitions.</span></span> <span data-ttu-id="96733-143">De même, si un seul attribut ou élément enfant d'un élément n'est pas valide par rapport à sa définition de type ou dispose d'une validité inconnue, l'élément est également non valide ou de validité inconnue.</span><span class="sxs-lookup"><span data-stu-id="96733-143">Similarly, if even one of the child elements or attributes of an element is invalid against its type definition, or has an unknown validity, the element is also either invalid or of unknown validity.</span></span>  
  
 <span data-ttu-id="96733-144">Étant donné que la validité d'un élément dépend de la validité de ses attributs et éléments enfants, les modifications apportées à l'un ou à l'autre se traduisent par une altération de la validité de l'élément s'il était précédemment valide.</span><span class="sxs-lookup"><span data-stu-id="96733-144">Given that the validity of an element is dependent on the validity of its child elements and attributes, modifications to either result in altering the validity of the element if it was previously valid.</span></span> <span data-ttu-id="96733-145">En particulier, si les attributs ou les éléments enfants d'un élément sont insérés, mis à jour ou supprimés, la validité de l'élément devient inconnue.</span><span class="sxs-lookup"><span data-stu-id="96733-145">Specifically, if the child elements or attributes of an element are inserted, updated, or deleted, then the validity of the element becomes unknown.</span></span> <span data-ttu-id="96733-146">Elle est représentée par la propriété <xref:System.Xml.Schema.IXmlSchemaInfo.Validity%2A> de la propriété <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> de l'élément définie sur <xref:System.Xml.Schema.XmlSchemaValidity.NotKnown>.</span><span class="sxs-lookup"><span data-stu-id="96733-146">This is represented by the <xref:System.Xml.Schema.IXmlSchemaInfo.Validity%2A> property of the element's <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> property being set to <xref:System.Xml.Schema.XmlSchemaValidity.NotKnown>.</span></span> <span data-ttu-id="96733-147">En outre, cet effet se répercute vers le haut de manière récursive dans le document XML car la validité de élément parent de l'élément (et de son élément parent, etc.) devient également inconnue.</span><span class="sxs-lookup"><span data-stu-id="96733-147">Furthermore, this effect cascades upwards recursively across the XML document, because the validity of the element's parent element (and its parent element, and so on) also becomes unknown.</span></span>  
  
 <span data-ttu-id="96733-148">Pour plus d'informations sur la validation de schémas et la classe <xref:System.Xml.XPath.XPathNavigator>, voir [Validation de schéma à l’aide de XPathNavigator](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md).</span><span class="sxs-lookup"><span data-stu-id="96733-148">For more information about schema validation and the <xref:System.Xml.XPath.XPathNavigator> class, see [Schema Validation using XPathNavigator](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md).</span></span>  
  
### <a name="modifying-attributes"></a><span data-ttu-id="96733-149">Modification d'attributs</span><span class="sxs-lookup"><span data-stu-id="96733-149">Modifying Attributes</span></span>  
 <span data-ttu-id="96733-150">Les méthodes <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> et <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> peuvent permettre de modifier des nœuds d'attribut typés et non typés, ainsi que les autres types de nœuds d'attribut répertoriés dans la section sur la modification de nœuds.</span><span class="sxs-lookup"><span data-stu-id="96733-150">The <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> and <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> methods can be used to modify untyped and typed attribute nodes as well as the other node types listed in the "Modifying Nodes" section.</span></span>  
  
 <span data-ttu-id="96733-151">L'exemple suivant modifie la valeur de l'attribut `genre` du premier élément `book` du fichier `books.xml`.</span><span class="sxs-lookup"><span data-stu-id="96733-151">The following example changes the value of the `genre` attribute of the first `book` element in the `books.xml` file.</span></span>  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", String.Empty)  
navigator.MoveToChild("book", String.Empty)  
navigator.MoveToAttribute("genre", String.Empty)  
  
navigator.SetValue("non-fiction")  
  
navigator.MoveToRoot()  
Console.WriteLine(navigator.OuterXml)  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", String.Empty);  
navigator.MoveToChild("book", String.Empty);  
navigator.MoveToAttribute("genre", String.Empty);  
  
navigator.SetValue("non-fiction");  
  
navigator.MoveToRoot();  
Console.WriteLine(navigator.OuterXml);  
```  
  
 <span data-ttu-id="96733-152">Pour plus d'informations sur les méthodes <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> et <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A>, voir les sections sur la modification de valeurs non typées et de valeurs typées.</span><span class="sxs-lookup"><span data-stu-id="96733-152">For more information about the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> and <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> methods, see the "Modifying Untyped Values" and "Modifying Typed Values" sections.</span></span>  
  
## <a name="innerxml-and-outerxml-properties"></a><span data-ttu-id="96733-153">Propriétés InnerXml et OuterXml</span><span class="sxs-lookup"><span data-stu-id="96733-153">InnerXml and OuterXml Properties</span></span>  
 <span data-ttu-id="96733-154">Les propriétés <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> et <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> de la classe <xref:System.Xml.XPath.XPathNavigator> modifient le balisage XML des nœuds sur lesquels un objet <xref:System.Xml.XPath.XPathNavigator> est actuellement positionné.</span><span class="sxs-lookup"><span data-stu-id="96733-154">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties of the <xref:System.Xml.XPath.XPathNavigator> class change the XML markup of the nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span>  
  
 <span data-ttu-id="96733-155">La propriété <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> modifie le balisage XML des nœuds enfants sur lesquels un objet <xref:System.Xml.XPath.XPathNavigator> est actuellement positionné avec le contenu analysé de la `string` XML donnée.</span><span class="sxs-lookup"><span data-stu-id="96733-155">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on with the parsed contents of the given XML `string`.</span></span> <span data-ttu-id="96733-156">De même, la propriété <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> modifie le balisage XML des nœuds enfants sur lesquels un objet <xref:System.Xml.XPath.XPathNavigator> est actuellement positionné, ainsi que le nœud actuel proprement dit.</span><span class="sxs-lookup"><span data-stu-id="96733-156">Similarly, the <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on as well as the current node itself.</span></span>  
  
 <span data-ttu-id="96733-157">L'exemple suivant utilise la propriété <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> pour modifier la valeur de l'élément `price` et insérer un nouvel attribut `discount` dans le premier élément `book` du fichier `contosoBooks.xml`.</span><span class="sxs-lookup"><span data-stu-id="96733-157">The following example uses the <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> property to modify the value of the `price` element and insert a new `discount` attribute on the first `book` element in the `contosoBooks.xml` file.</span></span>  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("contosoBooks.xml");  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("price", "http://www.contoso.com/books")  
  
navigator.OuterXml = "<price discount=\"0\">10.99</price>"  
  
navigator.MoveToRoot()  
Console.WriteLine(navigator.OuterXml)  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("contosoBooks.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books");  
navigator.MoveToChild("book", "http://www.contoso.com/books");  
navigator.MoveToChild("price", "http://www.contoso.com/books");  
  
navigator.OuterXml = "<price discount=\"0\">10.99</price>";  
  
navigator.MoveToRoot();  
Console.WriteLine(navigator.OuterXml);  
```  
  
 <span data-ttu-id="96733-158">L'exemple prend le fichier `contosoBooks.xml` comme entrée.</span><span class="sxs-lookup"><span data-stu-id="96733-158">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
## <a name="modifying-namespace-nodes"></a><span data-ttu-id="96733-159">Modification de nœuds d'espace de noms</span><span class="sxs-lookup"><span data-stu-id="96733-159">Modifying Namespace Nodes</span></span>  
 <span data-ttu-id="96733-160">Dans le DOM (Document Object Model), les déclarations d'espaces de noms sont traitées comme des attributs réguliers qui peuvent être insérés, mis à jour et supprimés.</span><span class="sxs-lookup"><span data-stu-id="96733-160">In the Document Object Model (DOM), namespace declarations are treated as if they are regular attributes that can be inserted, updated and deleted.</span></span> <span data-ttu-id="96733-161">La classe <xref:System.Xml.XPath.XPathNavigator> n'autorise pas ce type d'opération sur les nœuds d'espace de noms car toute modification de la valeur d'un nœud d'espace de noms peut modifier l'identité des éléments et attributs dans la portée du nœud d'espace de noms comme illustré dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="96733-161">The <xref:System.Xml.XPath.XPathNavigator> class does not allow such operations on namespace nodes because altering the value of a namespace node can change the identity of the elements and attributes within the scope of the namespace node as illustrated in the following example.</span></span>  
  
```xml  
<root xmlns="http://www.contoso.com">  
    <child />  
</root>  
```  
  
 <span data-ttu-id="96733-162">Si l'exemple XML ci-dessus est modifié de la manière suivante, chaque élément est effectivement renommé dans le document car la valeur de l'URI d'espace de noms de chaque élément est modifiée.</span><span class="sxs-lookup"><span data-stu-id="96733-162">If the XML example above is changed in the following way, this effectively renames every element in the document because the value of each element's namespace URI is changed.</span></span>  
  
```xml  
<root xmlns="urn:contoso.com">  
    <child />  
</root>  
```  
  
 <span data-ttu-id="96733-163">L'insertion d'espaces de noms n'entrant pas en conflit avec les déclarations d'espaces de noms dans la portée dans laquelle ils sont insérés est autorisée par la classe <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="96733-163">Inserting namespace nodes that do not conflict with namespace declarations at the scope that they are inserted in is allowed by the <xref:System.Xml.XPath.XPathNavigator> class.</span></span> <span data-ttu-id="96733-164">Dans ce cas, les déclarations d'espaces de noms ne sont pas déclarées dans des portées inférieures du document XML et ne se traduisent pas par l'attribution d'un nouveau nom comme illustré dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="96733-164">In this case, the namespace declarations are not declared at lower scopes in the XML document and does not result in renaming as illustrated in the following example.</span></span>  
  
```xml  
<root xmlns:a="http://www.contoso.com">  
    <parent>  
        <a:child />  
    </parent>  
</root>  
```  
  
 <span data-ttu-id="96733-165">Si l'exemple XML ci-dessus est modifié de la manière suivante, les déclarations d'espaces de noms sont correctement propagées dans le document XML sous la portée de l'autre déclaration d'espace de noms.</span><span class="sxs-lookup"><span data-stu-id="96733-165">If the XML example above is changed in the following way, the namespace declarations are correctly propagated across the XML document below the scope of the other namespace declaration.</span></span>  
  
```xml  
<root xmlns:a="http://www.contoso.com">  
    <parent a:parent-id="1234" xmlns:a="http://www.contoso.com/parent-id">  
        <a:child xmlns:a="http://www.contoso.com/" />  
    </parent>  
</root>  
```  
  
 <span data-ttu-id="96733-166">Dans l'exemple XML ci-dessus, l'attribut `a:parent-id` est inséré dans l'élément `parent` dans l'espace de noms `http://www.contoso.com/parent-id`.</span><span class="sxs-lookup"><span data-stu-id="96733-166">In the XML example above, the attribute `a:parent-id` is inserted on the `parent` element in the `http://www.contoso.com/parent-id` namespace.</span></span> <span data-ttu-id="96733-167">La méthode <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> permet d'insérer l'attribut tout en étant positionné sur l'élément `parent`.</span><span class="sxs-lookup"><span data-stu-id="96733-167">The <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> method is used to insert the attribute while positioned on the `parent` element.</span></span> <span data-ttu-id="96733-168">La déclaration d'espace de noms `http://www.contoso.com` est automatiquement insérée par la classe <xref:System.Xml.XPath.XPathNavigator> pour conserver la cohérence du reste du document XML.</span><span class="sxs-lookup"><span data-stu-id="96733-168">The `http://www.contoso.com` namespace declaration is automatically inserted by the <xref:System.Xml.XPath.XPathNavigator> class to preserve the consistency of the rest of the XML document.</span></span>  
  
## <a name="modifying-entity-reference-nodes"></a><span data-ttu-id="96733-169">Modification de nœuds de référence d'entité</span><span class="sxs-lookup"><span data-stu-id="96733-169">Modifying Entity Reference Nodes</span></span>  
 <span data-ttu-id="96733-170">Les nœuds de référence d'entité d'un objet <xref:System.Xml.XmlDocument> sont en lecture seule et ne peuvent pas être modifiés à l'aide des classes <xref:System.Xml.XPath.XPathNavigator> ou <xref:System.Xml.XmlNode>.</span><span class="sxs-lookup"><span data-stu-id="96733-170">Entity reference nodes in an <xref:System.Xml.XmlDocument> object are read-only and cannot be edited using either the <xref:System.Xml.XPath.XPathNavigator> or <xref:System.Xml.XmlNode> classes.</span></span> <span data-ttu-id="96733-171">Toute tentative de modification d'un nœud de référence d'entité se traduit par un objet <xref:System.InvalidOperationException>.</span><span class="sxs-lookup"><span data-stu-id="96733-171">Any attempt to modify an entity reference node results in an <xref:System.InvalidOperationException>.</span></span>  
  
## <a name="modifying-xsinil-nodes"></a><span data-ttu-id="96733-172">Modification de nœuds xsi:nil</span><span class="sxs-lookup"><span data-stu-id="96733-172">Modifying xsi:nil Nodes</span></span>  
 <span data-ttu-id="96733-173">La recommandation du W3C sur les schémas XML introduit le concept d'élément pouvant prendre la valeur null.</span><span class="sxs-lookup"><span data-stu-id="96733-173">The W3C XML Schema recommendation introduces the concept of an element being nillable.</span></span> <span data-ttu-id="96733-174">Si un élément peut prendre la valeur null, il peut n'avoir aucun contenu et rester valide.</span><span class="sxs-lookup"><span data-stu-id="96733-174">When an element is nillable, it is possible for the element to have no content and still be valid.</span></span> <span data-ttu-id="96733-175">Le concept d'élément pouvant prendre la valeur null est similaire à celui d'objet `null`.</span><span class="sxs-lookup"><span data-stu-id="96733-175">The concept of an element being nillable is similar to the concept of an object being `null`.</span></span> <span data-ttu-id="96733-176">La principale différence est qu'il est possible d'accéder à un objet `null` de n'importe quelle manière, tandis qu'un élément `xsi:nil` possède toujours des propriétés telles que des attributs accessibles, mais n'ayant aucun contenu (texte ou éléments enfants).</span><span class="sxs-lookup"><span data-stu-id="96733-176">The main difference is that a `null` object cannot be accessed in any way, while an `xsi:nil` element still has properties such as attributes that can be accessed, but has no content (child elements or text).</span></span> <span data-ttu-id="96733-177">L'existence de l'attribut `xsi:nil` présentant la valeur `true` dans un élément d'un document XML permet d'indiquer qu'un élément n'a aucun contenu.</span><span class="sxs-lookup"><span data-stu-id="96733-177">The existence of the `xsi:nil` attribute with a value of `true` on an element in an XML document is used to indicate that an element has no content.</span></span>  
  
 <span data-ttu-id="96733-178">Si un objet <xref:System.Xml.XPath.XPathNavigator> permet d'ajouter du contenu à un élément valide avec un attribut `xsi:nil` ayant la valeur `true`, la valeur de son attribut `xsi:nil` est définie sur `false`.</span><span class="sxs-lookup"><span data-stu-id="96733-178">If an <xref:System.Xml.XPath.XPathNavigator> object is used to add content to a valid element with an `xsi:nil` attribute with a value of `true`, the value of its `xsi:nil` attribute is set to `false`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="96733-179">Si le contenu d'un élément possédant un attribut `xsi:nil` défini sur `false` est supprimé, la valeur de l'attribut n'est pas modifiée en `true`.</span><span class="sxs-lookup"><span data-stu-id="96733-179">If the content of an element with an `xsi:nil` attribute set to `false` is deleted, the value of the attribute is not changed to `true`.</span></span>  
  
## <a name="saving-an-xml-document"></a><span data-ttu-id="96733-180">Enregistrement d'un document XML</span><span class="sxs-lookup"><span data-stu-id="96733-180">Saving an XML Document</span></span>  
 <span data-ttu-id="96733-181">L'enregistrement des modifications apportées à un objet <xref:System.Xml.XmlDocument> suite aux méthodes de modification décrites dans cette rubrique s'effectue à l'aide des méthodes de la classe <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="96733-181">Saving changes made to an <xref:System.Xml.XmlDocument> object as the result of the editing methods described in this topic is performed using the methods of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="96733-182">Pour plus d'informations sur l'enregistrement des modifications apportées à un objet <xref:System.Xml.XmlDocument>, consultez [Enregistrement et écriture d'un document](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).</span><span class="sxs-lookup"><span data-stu-id="96733-182">For more information about saving changes made to an <xref:System.Xml.XmlDocument> object, see [Saving and Writing a Document](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96733-183">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="96733-183">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="96733-184">Traitement des données XML à l'aide du modèle de données XPath</span><span class="sxs-lookup"><span data-stu-id="96733-184">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="96733-185">Insertion de données XML à l’aide de XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="96733-185">Insert XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/insert-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="96733-186">Suppression de données XML à l'aide de XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="96733-186">Remove XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/remove-xml-data-using-xpathnavigator.md)
