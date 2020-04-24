---
title: Suppression de données XML à l'aide de XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 9f436bca-1b96-494b-a6d2-e102c7551752
ms.openlocfilehash: 062a98a9cc10e6be00f165cf617de2d92d65acbf
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710360"
---
# <a name="remove-xml-data-using-xpathnavigator"></a><span data-ttu-id="12a18-102">Suppression de données XML à l'aide de XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="12a18-102">Remove XML Data using XPathNavigator</span></span>
<span data-ttu-id="12a18-103">La classe <xref:System.Xml.XPath.XPathNavigator> fournit un ensemble de méthodes permettant de supprimer des nœuds et des valeurs d'un document XML.</span><span class="sxs-lookup"><span data-stu-id="12a18-103">The <xref:System.Xml.XPath.XPathNavigator> class provides a set of methods used to remove nodes and values from an XML document.</span></span> <span data-ttu-id="12a18-104">Pour pouvoir utiliser ces méthodes, vous devez pouvoir modifier l'objet <xref:System.Xml.XPath.XPathNavigator>, ce qui signifie que sa propriété <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> doit être `true`.</span><span class="sxs-lookup"><span data-stu-id="12a18-104">In order to use these methods, the <xref:System.Xml.XPath.XPathNavigator> object must be editable, that is, its <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> property must be `true`.</span></span>  
  
 <span data-ttu-id="12a18-105">Les objets <xref:System.Xml.XPath.XPathNavigator> qui permettent d'éditer un document XML sont créés par la méthode <xref:System.Xml.XmlDocument.CreateNavigator%2A> de la classe <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="12a18-105"><xref:System.Xml.XPath.XPathNavigator> objects that can edit an XML document are created by the <xref:System.Xml.XmlDocument.CreateNavigator%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="12a18-106">Les objets <xref:System.Xml.XPath.XPathNavigator> créés par la classe <xref:System.Xml.XPath.XPathDocument> sont en lecture seule et toute tentative d'utilisation des méthodes de modification d'un objet <xref:System.Xml.XPath.XPathNavigator> créé par un objet <xref:System.Xml.XPath.XPathDocument> se traduit par un objet <xref:System.NotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="12a18-106"><xref:System.Xml.XPath.XPathNavigator> objects created by the <xref:System.Xml.XPath.XPathDocument> class are read-only and any attempt to use the editing methods of an <xref:System.Xml.XPath.XPathNavigator> object created by an <xref:System.Xml.XPath.XPathDocument> object results in a <xref:System.NotSupportedException>.</span></span>  
  
 <span data-ttu-id="12a18-107">Pour plus d’informations sur la création d’objets <xref:System.Xml.XPath.XPathNavigator> modifiables, consultez [Lecture de données XML à l’aide de XPathDocument et XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).</span><span class="sxs-lookup"><span data-stu-id="12a18-107">For more information about creating editable <xref:System.Xml.XPath.XPathNavigator> objects, see [Reading XML Data using XPathDocument and XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).</span></span>  
  
## <a name="removing-nodes"></a><span data-ttu-id="12a18-108">Suppression de nœuds</span><span class="sxs-lookup"><span data-stu-id="12a18-108">Removing Nodes</span></span>  
 <span data-ttu-id="12a18-109">La classe <xref:System.Xml.XPath.XPathNavigator> fournit la méthode <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> permettant de supprimer des nœuds d'un document XML.</span><span class="sxs-lookup"><span data-stu-id="12a18-109">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> method to remove nodes from an XML document.</span></span>  
  
### <a name="removing-a-node"></a><span data-ttu-id="12a18-110">Suppression d'un nœud</span><span class="sxs-lookup"><span data-stu-id="12a18-110">Removing a Node</span></span>  
 <span data-ttu-id="12a18-111">La classe <xref:System.Xml.XPath.XPathNavigator> fournit la méthode <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> permettant de supprimer d'un document XML le nœud actuel sur lequel l'objet <xref:System.Xml.XPath.XPathNavigator> est positionné.</span><span class="sxs-lookup"><span data-stu-id="12a18-111">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> method to delete the current node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on from an XML document.</span></span>  
  
 <span data-ttu-id="12a18-112">Une fois qu'un nœud a été supprimé à l'aide de la méthode <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A>, il n'est plus accessible depuis la racine de l'objet <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="12a18-112">After a node has been deleted using the <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> method, it is no longer reachable from the root of the <xref:System.Xml.XmlDocument> object.</span></span> <span data-ttu-id="12a18-113">Après la suppression d'un nœud, l'objet <xref:System.Xml.XPath.XPathNavigator> est positionné sur le nœud parent du nœud supprimé.</span><span class="sxs-lookup"><span data-stu-id="12a18-113">After a node has been deleted, the <xref:System.Xml.XPath.XPathNavigator> is positioned on the parent node of the deleted node.</span></span>  
  
 <span data-ttu-id="12a18-114">Une suppression n'affecte en rien la position des objets <xref:System.Xml.XPath.XPathNavigator> positionnés sur le nœud supprimé.</span><span class="sxs-lookup"><span data-stu-id="12a18-114">A delete operation doesn't affect the position of any <xref:System.Xml.XPath.XPathNavigator> object positioned on the deleted node.</span></span> <span data-ttu-id="12a18-115">Ces objets <xref:System.Xml.XPath.XPathNavigator> sont valides dans le sens où ils peuvent se déplacer dans la sous-arborescence supprimée, mais ils ne peuvent pas être déplacés vers le nœud principal avec les méthodes ordinaires de navigation dans les collections de nœuds de la classe <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="12a18-115">These <xref:System.Xml.XPath.XPathNavigator> objects are valid in the sense that they can move within the deleted subtree, but cannot be moved to the main node tree using the regular node set navigation methods of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="12a18-116">La méthode <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A> de la classe <xref:System.Xml.XPath.XPathNavigator> peut être utilisée pour redéplacer ces objets <xref:System.Xml.XPath.XPathNavigator> vers l’arborescence de nœuds principale ou depuis l’arborescence de nœuds principale vers la sous-arborescence supprimée.</span><span class="sxs-lookup"><span data-stu-id="12a18-116">The <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class can be used to move these <xref:System.Xml.XPath.XPathNavigator> objects back into the main node tree, or from the main node tree to the deleted subtree.</span></span>  
  
 <span data-ttu-id="12a18-117">Dans l'exemple suivant, l'élément `price` du premier élément `book` du fichier `contosoBooks.xml` est supprimé à l'aide de la méthode <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A>.</span><span class="sxs-lookup"><span data-stu-id="12a18-117">In the following example, the `price` element of the first `book` element of the `contosoBooks.xml` file is deleted using the <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> method.</span></span> <span data-ttu-id="12a18-118">Après la suppression de l'élément <xref:System.Xml.XPath.XPathNavigator>, l'objet `price` est positionné sur l'élément `book` parent.</span><span class="sxs-lookup"><span data-stu-id="12a18-118">The position of the <xref:System.Xml.XPath.XPathNavigator> object after the `price` element is deleted is on the parent `book` element.</span></span>  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("contosoBooks.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("price", "http://www.contoso.com/books")  
  
navigator.DeleteSelf()  
  
Console.WriteLine("Position after delete: {0}", navigator.Name)  
Console.WriteLine(navigator.OuterXml)  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("contosoBooks.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books");  
navigator.MoveToChild("book", "http://www.contoso.com/books");  
navigator.MoveToChild("price", "http://www.contoso.com/books");  
  
navigator.DeleteSelf();  
  
Console.WriteLine("Position after delete: {0}", navigator.Name);  
Console.WriteLine(navigator.OuterXml);  
```  
  
 <span data-ttu-id="12a18-119">L'exemple prend le fichier `contosoBooks.xml` comme entrée.</span><span class="sxs-lookup"><span data-stu-id="12a18-119">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="removing-an-attribute-node"></a><span data-ttu-id="12a18-120">Suppression d'un nœud d'attribut</span><span class="sxs-lookup"><span data-stu-id="12a18-120">Removing an Attribute Node</span></span>  
 <span data-ttu-id="12a18-121">Les nœuds d'attribut d'un document XML se suppriment à l'aide de la méthode <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A>.</span><span class="sxs-lookup"><span data-stu-id="12a18-121">Attribute nodes are removed from an XML document using the <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> method.</span></span>  
  
 <span data-ttu-id="12a18-122">Une fois qu'un nœud d'attribut a été supprimé, il n'est plus accessible depuis le nœud racine d'un objet <xref:System.Xml.XmlDocument> et l'objet <xref:System.Xml.XPath.XPathNavigator> est positionné sur l'élément parent.</span><span class="sxs-lookup"><span data-stu-id="12a18-122">After an attribute node has been deleted, it is no longer reachable from the root node of an <xref:System.Xml.XmlDocument> object and the <xref:System.Xml.XPath.XPathNavigator> object is positioned on the parent element.</span></span>  
  
#### <a name="default-attributes"></a><span data-ttu-id="12a18-123">Attributs par défaut</span><span class="sxs-lookup"><span data-stu-id="12a18-123">Default Attributes</span></span>  
 <span data-ttu-id="12a18-124">Quelle que soit la méthode utilisée pour la suppression des attributs, la suppression d'attributs définis comme des attributs par défaut dans la DTD ou dans le schéma XML du document XML est sujette à des restrictions spéciales.</span><span class="sxs-lookup"><span data-stu-id="12a18-124">Regardless of the method used to remove attributes, there are special limitations on removing attributes that are defined as default attributes in the DTD or XML Schema for the XML document.</span></span> <span data-ttu-id="12a18-125">Les attributs par défaut ne peuvent pas être supprimés, à moins que l'élément auquel ils appartiennent ne le soit également.</span><span class="sxs-lookup"><span data-stu-id="12a18-125">Default attributes cannot be removed unless the element they belong to is also removed.</span></span> <span data-ttu-id="12a18-126">Il y a toujours des attributs par défaut pour les éléments pour lesquels des attributs par défaut ont été déclarés ; par conséquent, la suppression d'un attribut par défaut entraîne l'insertion, dans l'élément, d'un attribut de remplacement qui est initialisé à la valeur par défaut déclarée.</span><span class="sxs-lookup"><span data-stu-id="12a18-126">Default attributes are always present for elements that have default attributes declared, and as a result, deleting a default attribute results in a replacement attribute being inserted into the element and initialized to the default value that was declared.</span></span>  
  
## <a name="removing-values"></a><span data-ttu-id="12a18-127">Suppression de valeurs</span><span class="sxs-lookup"><span data-stu-id="12a18-127">Removing Values</span></span>  
 <span data-ttu-id="12a18-128">La classe <xref:System.Xml.XPath.XPathNavigator> fournit les méthodes <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> et <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> permettant de supprimer des valeurs typées et non typées d'un document XML.</span><span class="sxs-lookup"><span data-stu-id="12a18-128">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> and <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> methods to remove untyped and typed values from an XML document.</span></span>  
  
### <a name="removing-untyped-values"></a><span data-ttu-id="12a18-129">Suppression de valeurs non typées</span><span class="sxs-lookup"><span data-stu-id="12a18-129">Removing Untyped Values</span></span>  
 <span data-ttu-id="12a18-130">La méthode <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> insère simplement la valeur `string` non typée transmise sous la forme d'un paramètre comme la valeur du nœud sur lequel l'objet <xref:System.Xml.XPath.XPathNavigator> est actuellement positionné.</span><span class="sxs-lookup"><span data-stu-id="12a18-130">The <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method simply inserts the untyped `string` value passed as a parameter as the value of the node the <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span> <span data-ttu-id="12a18-131">La transmission d'une chaîne vide à la méthode <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> supprime la valeur du nœud actuel.</span><span class="sxs-lookup"><span data-stu-id="12a18-131">Passing an empty string to the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method removes the value of the current node.</span></span>  
  
 <span data-ttu-id="12a18-132">L'exemple suivant supprime la valeur de l'élément `price` du premier élément `book` du fichier `contosoBooks.xml` à l'aide de la méthode <xref:System.Xml.XPath.XPathNavigator.SetValue%2A>.</span><span class="sxs-lookup"><span data-stu-id="12a18-132">The following example removes the value of the `price` element of the first `book` element in the `contosoBooks.xml` file using the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method.</span></span>  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("contosoBooks.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("price", "http://www.contoso.com/books")  
  
navigator.SetValue("")  
  
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
  
navigator.SetValue("");  
  
navigator.MoveToRoot();  
Console.WriteLine(navigator.OuterXml);  
```  
  
 <span data-ttu-id="12a18-133">L'exemple prend le fichier `contosoBooks.xml` comme entrée.</span><span class="sxs-lookup"><span data-stu-id="12a18-133">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="removing-typed-values"></a><span data-ttu-id="12a18-134">Suppression de valeurs typées</span><span class="sxs-lookup"><span data-stu-id="12a18-134">Removing Typed Values</span></span>  
 <span data-ttu-id="12a18-135">Si le type d'un nœud est un type simple des schémas XML du W3C, la nouvelle valeur insérée par la méthode <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> est vérifiée par rapport aux facettes du type simple avant d'être définie.</span><span class="sxs-lookup"><span data-stu-id="12a18-135">When the type of a node is a W3C XML Schema simple type, the new value inserted by the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method is checked against the facets of the simple type before the value is set.</span></span> <span data-ttu-id="12a18-136">Si la nouvelle valeur n'est pas valide par rapport au type du nœud (par exemple, une valeur est définie sur `-1` pour un élément dont le type est `xs:positiveInteger`), une exception se produit.</span><span class="sxs-lookup"><span data-stu-id="12a18-136">If the new value is not valid according to the type of the node (for example, setting a value of `-1` on an element whose type is `xs:positiveInteger`), it results in an exception.</span></span> <span data-ttu-id="12a18-137">De même, la méthode <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> ne peut pas recevoir la valeur `null` comme paramètre.</span><span class="sxs-lookup"><span data-stu-id="12a18-137">The <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method also cannot be passed `null` as a parameter.</span></span> <span data-ttu-id="12a18-138">Par conséquent, la suppression de la valeur d'un nœud typé doit être conforme au type de schéma du nœud.</span><span class="sxs-lookup"><span data-stu-id="12a18-138">As a result removing the value of a typed node must comply with the schema type of the node.</span></span>  
  
 <span data-ttu-id="12a18-139">L'exemple suivant supprime la valeur de l'élément `price` du premier élément `book` du fichier `contosoBooks.xml` à l'aide de la méthode <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> en définissant la valeur sur `0`.</span><span class="sxs-lookup"><span data-stu-id="12a18-139">The following example removes the value of the `price` element of the first `book` element in the `contosoBooks.xml` file using the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method by setting the value to `0`.</span></span> <span data-ttu-id="12a18-140">La valeur du nœud n'est pas supprimée, mais le prix du livre a été supprimé d'après son type de données (`xs:decimal`).</span><span class="sxs-lookup"><span data-stu-id="12a18-140">The value of the node is not removed, but the price of the book has been removed according to its data type of `xs:decimal`.</span></span>  
  
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
  
navigator.SetTypedValue(0)  
  
navigator.MoveToRoot()  
Console.WriteLine(navigator.OuterXml)  
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
  
navigator.SetTypedValue(0);  
  
navigator.MoveToRoot();  
Console.WriteLine(navigator.OuterXml);  
```  
  
## <a name="namespace-nodes"></a><span data-ttu-id="12a18-141">Nœuds d'espace de noms</span><span class="sxs-lookup"><span data-stu-id="12a18-141">Namespace Nodes</span></span>  
 <span data-ttu-id="12a18-142">Il est impossible de supprimer des nœuds d'espace de noms d'un objet <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="12a18-142">Namespace nodes cannot be deleted from an <xref:System.Xml.XmlDocument> object.</span></span> <span data-ttu-id="12a18-143">Toute tentative de suppression des nœuds d'espace de noms avec la méthode <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> produit une exception.</span><span class="sxs-lookup"><span data-stu-id="12a18-143">Attempts to delete namespace nodes using the <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> method results in an exception.</span></span>  
  
## <a name="the-innerxml-and-outerxml-properties"></a><span data-ttu-id="12a18-144">Propriétés InnerXml et OuterXml</span><span class="sxs-lookup"><span data-stu-id="12a18-144">The InnerXml and OuterXml Properties</span></span>  
 <span data-ttu-id="12a18-145">Les propriétés <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> et <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> de la classe <xref:System.Xml.XPath.XPathNavigator> modifient le balisage XML des nœuds sur lesquels un objet <xref:System.Xml.XPath.XPathNavigator> est actuellement positionné.</span><span class="sxs-lookup"><span data-stu-id="12a18-145">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties of the <xref:System.Xml.XPath.XPathNavigator> class change the XML markup of the nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span>  
  
 <span data-ttu-id="12a18-146">La propriété <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> modifie le balisage XML des nœuds enfants sur lesquels un objet <xref:System.Xml.XPath.XPathNavigator> est actuellement positionné avec le contenu analysé de la `string` XML donnée.</span><span class="sxs-lookup"><span data-stu-id="12a18-146">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on with the parsed contents of the given XML `string`.</span></span> <span data-ttu-id="12a18-147">De même, la propriété <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> modifie le balisage XML des nœuds enfants sur lesquels un objet <xref:System.Xml.XPath.XPathNavigator> est actuellement positionné, ainsi que le nœud actuel proprement dit.</span><span class="sxs-lookup"><span data-stu-id="12a18-147">Similarly, the <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on as well as the current node itself.</span></span>  
  
 <span data-ttu-id="12a18-148">Outre les méthodes décrites dans cette rubrique, les propriétés <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> et <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> permettent de supprimer des nœuds et des valeurs d'un document XML.</span><span class="sxs-lookup"><span data-stu-id="12a18-148">In addition to the methods described in this topic, the <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties can be used to remove nodes and values from an XML document.</span></span> <span data-ttu-id="12a18-149">Pour plus d'informations sur l'utilisation des propriétés <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> et <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> pour modifier des nœuds, consultez la rubrique [Modification de données XML à l’aide de XPathNavigator](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md).</span><span class="sxs-lookup"><span data-stu-id="12a18-149">For more information about using the <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties to modify nodes, see the [Modify XML Data using XPathNavigator](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) topic.</span></span>  
  
## <a name="saving-an-xml-document"></a><span data-ttu-id="12a18-150">Enregistrement d'un document XML</span><span class="sxs-lookup"><span data-stu-id="12a18-150">Saving an XML Document</span></span>  
 <span data-ttu-id="12a18-151">L'enregistrement des modifications apportées à un objet <xref:System.Xml.XmlDocument> suite aux méthodes décrites dans cette rubrique s'effectue à l'aide des méthodes de la classe <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="12a18-151">Saving changes made to an <xref:System.Xml.XmlDocument> object as the result of the methods described in this topic is performed using the methods of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="12a18-152">Pour plus d'informations sur l'enregistrement des modifications apportées à un objet <xref:System.Xml.XmlDocument>, consultez [Enregistrement et écriture d'un document](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).</span><span class="sxs-lookup"><span data-stu-id="12a18-152">For more information about saving changes made to an <xref:System.Xml.XmlDocument> object, see [Saving and Writing a Document](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12a18-153">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="12a18-153">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="12a18-154">Traitement des données XML à l'aide du modèle de données XPath</span><span class="sxs-lookup"><span data-stu-id="12a18-154">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="12a18-155">Insertion de données XML à l’aide de XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="12a18-155">Insert XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/insert-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="12a18-156">Modification de données XML à l’aide de XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="12a18-156">Modify XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md)
