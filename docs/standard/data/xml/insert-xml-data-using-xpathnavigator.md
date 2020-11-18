---
title: Insertion de données XML à l’aide de XPathNavigator
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 2ed8c28b-b88d-4be7-9c87-92df01f0821f
ms.openlocfilehash: 1a0fa96c0fc4db1ab005961728e81b6940cd00e6
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94822710"
---
# <a name="insert-xml-data-using-xpathnavigator"></a><span data-ttu-id="16071-102">Insertion de données XML à l’aide de XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="16071-102">Insert XML Data using XPathNavigator</span></span>
<span data-ttu-id="16071-103">La classe <xref:System.Xml.XPath.XPathNavigator> fournit un ensemble de méthodes permettant d'insérer des nœuds frères, enfants et d'attribut dans un document XML.</span><span class="sxs-lookup"><span data-stu-id="16071-103">The <xref:System.Xml.XPath.XPathNavigator> class provides a set of methods used to insert sibling, child, and attribute nodes in an XML document.</span></span> <span data-ttu-id="16071-104">Pour pouvoir utiliser ces méthodes, vous devez pouvoir modifier l'objet <xref:System.Xml.XPath.XPathNavigator>, ce qui signifie que sa propriété <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> doit être `true`.</span><span class="sxs-lookup"><span data-stu-id="16071-104">In order to use these methods, the <xref:System.Xml.XPath.XPathNavigator> object must be editable, that is, its <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> property must be `true`.</span></span>  
  
 <span data-ttu-id="16071-105">Les objets <xref:System.Xml.XPath.XPathNavigator> qui permettent d'éditer un document XML sont créés par la méthode <xref:System.Xml.XmlDocument.CreateNavigator%2A> de la classe <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="16071-105"><xref:System.Xml.XPath.XPathNavigator> objects that can edit an XML document are created by the <xref:System.Xml.XmlDocument.CreateNavigator%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="16071-106">Les objets <xref:System.Xml.XPath.XPathNavigator> créés par la classe <xref:System.Xml.XPath.XPathDocument> sont en lecture seule et toute tentative d'utilisation des méthodes de modification d'un objet <xref:System.Xml.XPath.XPathNavigator> créé par un objet <xref:System.Xml.XPath.XPathDocument> se traduit par un objet <xref:System.NotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="16071-106"><xref:System.Xml.XPath.XPathNavigator> objects created by the <xref:System.Xml.XPath.XPathDocument> class are read-only and any attempt to use the editing methods of an <xref:System.Xml.XPath.XPathNavigator> object created by an <xref:System.Xml.XPath.XPathDocument> object results in a <xref:System.NotSupportedException>.</span></span>  
  
 <span data-ttu-id="16071-107">Pour plus d’informations sur la création d’objets <xref:System.Xml.XPath.XPathNavigator> modifiables, consultez [Lecture de données XML à l’aide de XPathDocument et XmlDocument](reading-xml-data-using-xpathdocument-and-xmldocument.md).</span><span class="sxs-lookup"><span data-stu-id="16071-107">For more information about creating editable <xref:System.Xml.XPath.XPathNavigator> objects, see [Reading XML Data using XPathDocument and XmlDocument](reading-xml-data-using-xpathdocument-and-xmldocument.md).</span></span>  
  
## <a name="inserting-nodes"></a><span data-ttu-id="16071-108">Insertion de nœuds</span><span class="sxs-lookup"><span data-stu-id="16071-108">Inserting Nodes</span></span>  
 <span data-ttu-id="16071-109">La classe <xref:System.Xml.XPath.XPathNavigator> fournit des méthodes permettant d'insérer des nœuds frères, enfants et d'attribut dans un document XML.</span><span class="sxs-lookup"><span data-stu-id="16071-109">The <xref:System.Xml.XPath.XPathNavigator> class provides methods to insert sibling, child, and attribute nodes in an XML document.</span></span> <span data-ttu-id="16071-110">Ces méthodes permettent d'insérer des nœuds et des attributs à différents emplacements par rapport à la position actuelle d'un objet <xref:System.Xml.XPath.XPathNavigator> et sont décrites dans les sections suivantes.</span><span class="sxs-lookup"><span data-stu-id="16071-110">These methods allow you to insert nodes and attributes in different locations in relation to the current position of an <xref:System.Xml.XPath.XPathNavigator> object and are described in the following sections.</span></span>  
  
### <a name="inserting-sibling-nodes"></a><span data-ttu-id="16071-111">Insertion de nœuds frères</span><span class="sxs-lookup"><span data-stu-id="16071-111">Inserting Sibling Nodes</span></span>  
 <span data-ttu-id="16071-112">La classe <xref:System.Xml.XPath.XPathNavigator> fournit les méthodes suivantes pour l'insertion de nœuds frères.</span><span class="sxs-lookup"><span data-stu-id="16071-112">The <xref:System.Xml.XPath.XPathNavigator> class provides the following methods to insert sibling nodes.</span></span>  
  
- <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A>  
  
 <span data-ttu-id="16071-113">Ces méthodes insèrent des nœuds frères avant et après le nœud sur lequel un objet <xref:System.Xml.XPath.XPathNavigator> est actuellement positionné.</span><span class="sxs-lookup"><span data-stu-id="16071-113">These methods insert sibling nodes before and after the node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span>  
  
 <span data-ttu-id="16071-114">Les méthodes <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> et <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> sont surchargées et acceptent un objet `string`, <xref:System.Xml.XmlReader> ou <xref:System.Xml.XPath.XPathNavigator> contenant le nœud frère à ajouter comme paramètre.</span><span class="sxs-lookup"><span data-stu-id="16071-114">The <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> and <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> methods are overloaded and accept a `string`, <xref:System.Xml.XmlReader> object, or <xref:System.Xml.XPath.XPathNavigator> object containing the sibling node to add as parameters.</span></span> <span data-ttu-id="16071-115">Ces deux méthodes retournent également un objet <xref:System.Xml.XmlWriter> permettant d'insérer des nœuds frères.</span><span class="sxs-lookup"><span data-stu-id="16071-115">Both methods also return an <xref:System.Xml.XmlWriter> object used to insert sibling nodes.</span></span>  
  
 <span data-ttu-id="16071-116">Les méthodes <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> et <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> insèrent un nœud frère unique avant et après le nœud sur lequel un objet <xref:System.Xml.XPath.XPathNavigator> est actuellement positionné à l'aide du préfixe d'espace de noms, du nom local, de l'URI d'espace de noms et de la valeur spécifiés comme paramètres.</span><span class="sxs-lookup"><span data-stu-id="16071-116">The <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> and <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> methods insert a single sibling node before and after the node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on using the namespace prefix, local name, namespace URI, and value specified as parameters.</span></span>  
  
 <span data-ttu-id="16071-117">Dans l'exemple suivant, un nouvel élément `pages` est inséré avant l'élément `price` enfant du premier élément `book` du fichier `contosoBooks.xml`.</span><span class="sxs-lookup"><span data-stu-id="16071-117">In the following example a new `pages` element is inserted before the `price` child element of the first `book` element in the `contosoBooks.xml` file.</span></span>  
  
 [!code-cpp[XPathNavigatorMethods#19](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#19)]
 [!code-csharp[XPathNavigatorMethods#19](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#19)]
 [!code-vb[XPathNavigatorMethods#19](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#19)]  
  
 <span data-ttu-id="16071-118">L'exemple prend le fichier `contosoBooks.xml` comme entrée.</span><span class="sxs-lookup"><span data-stu-id="16071-118">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="16071-119">Pour plus d'informations sur les méthodes <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> et <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A>, voir la documentation de référence sur la classe <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="16071-119">For more information about the <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> and <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> methods, see the <xref:System.Xml.XPath.XPathNavigator> class reference documentation.</span></span>  
  
### <a name="inserting-child-nodes"></a><span data-ttu-id="16071-120">Insertion de nœuds enfants</span><span class="sxs-lookup"><span data-stu-id="16071-120">Inserting Child Nodes</span></span>  
 <span data-ttu-id="16071-121">La classe <xref:System.Xml.XPath.XPathNavigator> fournit les méthodes suivantes pour l'insertion de nœuds enfants.</span><span class="sxs-lookup"><span data-stu-id="16071-121">The <xref:System.Xml.XPath.XPathNavigator> class provides the following methods to insert child nodes.</span></span>  
  
- <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A>  
  
 <span data-ttu-id="16071-122">Ces méthodes ajoutent des nœuds enfants à la fin et au début de la liste de nœuds enfants du nœud sur lequel un objet <xref:System.Xml.XPath.XPathNavigator> est actuellement positionné.</span><span class="sxs-lookup"><span data-stu-id="16071-122">These methods append and prepend child nodes to the end of and the beginning of the list of child nodes of the node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span>  
  
 <span data-ttu-id="16071-123">À l'instar des méthodes décrites dans la section sur l'insertion de nœuds frères, les méthodes <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> et <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> acceptent un objet `string`, <xref:System.Xml.XmlReader> ou <xref:System.Xml.XPath.XPathNavigator> contenant le nœud enfant à ajouter comme paramètre.</span><span class="sxs-lookup"><span data-stu-id="16071-123">Like the methods in the "Inserting Sibling Nodes" section, the <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> and <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> methods accept a `string`, <xref:System.Xml.XmlReader> object, or <xref:System.Xml.XPath.XPathNavigator> object containing the child node to add as parameters.</span></span> <span data-ttu-id="16071-124">Ces deux méthodes retournent également un objet <xref:System.Xml.XmlWriter> permettant d'insérer des nœuds enfants.</span><span class="sxs-lookup"><span data-stu-id="16071-124">Both methods also return an <xref:System.Xml.XmlWriter> object used to insert child nodes.</span></span>  
  
 <span data-ttu-id="16071-125">À l'instar également des méthodes décrites dans la section sur l'insertion de nœuds frères, les méthodes <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> et <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> insèrent un nœud enfant unique à la fin et au début de la liste de nœuds enfants du nœud sur lequel un objet <xref:System.Xml.XPath.XPathNavigator> est actuellement positionné à l'aide du préfixe d'espace de noms, du nom local, de l'URI d'espace de noms et de la valeur spécifiés comme paramètres.</span><span class="sxs-lookup"><span data-stu-id="16071-125">Also like the methods in the "Inserting Sibling Nodes" section, the <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> and <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> methods insert a single child node to the end of and the beginning of the list of child nodes of the node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on using the namespace prefix, local name, namespace URI, and value specified as parameters.</span></span>  
  
 <span data-ttu-id="16071-126">Dans l'exemple suivant, un nouvel élément `pages` enfant est ajouté à la liste d'éléments enfants du premier élément `book` du fichier `contosoBooks.xml`.</span><span class="sxs-lookup"><span data-stu-id="16071-126">In the following example, a new `pages` child element is appended to the list of child elements of the first `book` element in the `contosoBooks.xml` file.</span></span>  
  
 [!code-cpp[XPathNavigatorMethods#2](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#2)]
 [!code-csharp[XPathNavigatorMethods#2](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#2)]
 [!code-vb[XPathNavigatorMethods#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#2)]  
  
 <span data-ttu-id="16071-127">L'exemple prend le fichier `contosoBooks.xml` comme entrée.</span><span class="sxs-lookup"><span data-stu-id="16071-127">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="16071-128">Pour plus d'informations sur les méthodes <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> et <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A>, voir la documentation de référence sur la classe <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="16071-128">For more information about the <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> and <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> methods, see the <xref:System.Xml.XPath.XPathNavigator> class reference documentation.</span></span>  
  
### <a name="inserting-attribute-nodes"></a><span data-ttu-id="16071-129">Insertion de nœuds d'attribut</span><span class="sxs-lookup"><span data-stu-id="16071-129">Inserting Attribute Nodes</span></span>  
 <span data-ttu-id="16071-130">La classe <xref:System.Xml.XPath.XPathNavigator> fournit les méthodes suivantes pour l'insertion de nœuds d'attribut.</span><span class="sxs-lookup"><span data-stu-id="16071-130">The <xref:System.Xml.XPath.XPathNavigator> class provides the following methods to insert attribute nodes.</span></span>  
  
- <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A>  
  
 <span data-ttu-id="16071-131">Ces méthodes insèrent des nœuds d'attribut sur le nœud sur lequel un objet <xref:System.Xml.XPath.XPathNavigator> est actuellement positionné.</span><span class="sxs-lookup"><span data-stu-id="16071-131">These methods insert attribute nodes on the element node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span> <span data-ttu-id="16071-132">La méthode <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> crée un nœud d'attribut sur le nœud d'élément sur lequel un objet <xref:System.Xml.XPath.XPathNavigator> est actuellement positionné à l'aide du préfixe d'espace de noms, du nom local, de l'URI d'espace de noms et de la valeur spécifiés comme paramètres.</span><span class="sxs-lookup"><span data-stu-id="16071-132">The <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> method creates an attribute node on the element node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on using the namespace prefix, local name, namespace URI, and value specified as parameters.</span></span> <span data-ttu-id="16071-133">La méthode <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> retourne un objet <xref:System.Xml.XmlWriter> permettant d'insérer des nœuds d'attribut.</span><span class="sxs-lookup"><span data-stu-id="16071-133">The <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> method returns an <xref:System.Xml.XmlWriter> object used to insert attribute nodes.</span></span>  
  
 <span data-ttu-id="16071-134">Dans l'exemple suivant, de nouveaux attributs `discount` et `currency` sont créés sur l'élément `price` enfant du premier élément `book` du fichier `contosoBooks.xml` à l'aide de l'objet <xref:System.Xml.XmlWriter> retourné par la méthode <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A>.</span><span class="sxs-lookup"><span data-stu-id="16071-134">In the following example, new `discount` and `currency` attributes are created on the `price` child element of the first `book` element in the `contosoBooks.xml` file using the <xref:System.Xml.XmlWriter> object returned from the <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> method.</span></span>  
  
 [!code-cpp[XPathNavigatorMethods#8](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#8)]
 [!code-csharp[XPathNavigatorMethods#8](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#8)]
 [!code-vb[XPathNavigatorMethods#8](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#8)]  
  
 <span data-ttu-id="16071-135">L'exemple prend le fichier `contosoBooks.xml` comme entrée.</span><span class="sxs-lookup"><span data-stu-id="16071-135">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="16071-136">Pour plus d'informations sur les méthodes <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> et <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A>, voir la documentation de référence sur la classe <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="16071-136">For more information about the <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> and <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> methods, see the <xref:System.Xml.XPath.XPathNavigator> class reference documentation.</span></span>  
  
## <a name="copying-nodes"></a><span data-ttu-id="16071-137">Copie de nœuds</span><span class="sxs-lookup"><span data-stu-id="16071-137">Copying Nodes</span></span>  
 <span data-ttu-id="16071-138">Dans certains cas, il se peut que vous souhaitiez remplir un document XML avec le contenu d'un autre document XML.</span><span class="sxs-lookup"><span data-stu-id="16071-138">In certain cases you may want to populate an XML document with the contents from another XML document.</span></span> <span data-ttu-id="16071-139">Les classes <xref:System.Xml.XPath.XPathNavigator> et <xref:System.Xml.XmlWriter> peuvent copier des nœuds dans un objet <xref:System.Xml.XmlDocument> à partir d'un objet <xref:System.Xml.XmlReader> ou <xref:System.Xml.XPath.XPathNavigator> existant.</span><span class="sxs-lookup"><span data-stu-id="16071-139">Both the <xref:System.Xml.XPath.XPathNavigator> class and the <xref:System.Xml.XmlWriter> class can copy nodes to an <xref:System.Xml.XmlDocument> object from an existing <xref:System.Xml.XmlReader> object or <xref:System.Xml.XPath.XPathNavigator> object.</span></span>  
  
 <span data-ttu-id="16071-140">Les méthodes <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> et <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> de la classe <xref:System.Xml.XPath.XPathNavigator> présentent des surcharges qui peuvent accepter un objet <xref:System.Xml.XPath.XPathNavigator> ou <xref:System.Xml.XmlReader> comme paramètre.</span><span class="sxs-lookup"><span data-stu-id="16071-140">The <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> and <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> methods of the <xref:System.Xml.XPath.XPathNavigator> class all have overloads that can accept an <xref:System.Xml.XPath.XPathNavigator> object or an <xref:System.Xml.XmlReader> object as a parameter.</span></span>  
  
 <span data-ttu-id="16071-141">La méthode <xref:System.Xml.XmlWriter.WriteNode%2A> de la classe <xref:System.Xml.XmlWriter> présente des surcharges qui peuvent accepter un objet <xref:System.Xml.XmlNode>, <xref:System.Xml.XmlReader> ou <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="16071-141">The <xref:System.Xml.XmlWriter.WriteNode%2A> method of the <xref:System.Xml.XmlWriter> class has overloads that can accept an <xref:System.Xml.XmlNode>, <xref:System.Xml.XmlReader>, or <xref:System.Xml.XPath.XPathNavigator> object.</span></span>  
  
 <span data-ttu-id="16071-142">L'exemple suivant copie tous les éléments `book` d'un document dans un autre.</span><span class="sxs-lookup"><span data-stu-id="16071-142">The following example copies all the `book` elements from one document to another.</span></span>  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", String.Empty)  
  
Dim newBooks As XPathDocument = New XPathDocument("newBooks.xml")  
Dim newBooksNavigator As XPathNavigator = newBooks.CreateNavigator()  
  
Dim nav As XPathNavigator  
For Each nav in newBooksNavigator.SelectDescendants("book", "", false)  
    navigator.AppendChild(nav)  
Next  
  
document.Save("newBooks.xml");  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", String.Empty);  
  
XPathDocument newBooks = new XPathDocument("newBooks.xml");  
XPathNavigator newBooksNavigator = newBooks.CreateNavigator();  
  
foreach (XPathNavigator nav in newBooksNavigator.SelectDescendants("book", "", false))  
{  
    navigator.AppendChild(nav);  
}  
  
document.Save("newBooks.xml");  
```  
  
## <a name="inserting-values"></a><span data-ttu-id="16071-143">Insertion de valeurs</span><span class="sxs-lookup"><span data-stu-id="16071-143">Inserting Values</span></span>  
 <span data-ttu-id="16071-144">La classe <xref:System.Xml.XPath.XPathNavigator> fournit les méthodes <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> et <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> afin d'insérer des valeurs pour un nœud dans un objet <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="16071-144">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> and <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> methods to insert values for a node into an <xref:System.Xml.XmlDocument> object.</span></span>  
  
### <a name="inserting-untyped-values"></a><span data-ttu-id="16071-145">Insertion de valeurs non typées</span><span class="sxs-lookup"><span data-stu-id="16071-145">Inserting Untyped Values</span></span>  
 <span data-ttu-id="16071-146">La méthode <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> insère simplement la valeur `string` non typée transmise sous la forme d'un paramètre comme la valeur du nœud sur lequel l'objet <xref:System.Xml.XPath.XPathNavigator> est actuellement positionné.</span><span class="sxs-lookup"><span data-stu-id="16071-146">The <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method simply inserts the untyped `string` value passed as a parameter as the value of the node the <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span> <span data-ttu-id="16071-147">La valeur est insérée sans type ou sans vérifier que la nouvelle valeur est valide par rapport au type de nœud si les informations sur le schéma sont disponibles.</span><span class="sxs-lookup"><span data-stu-id="16071-147">The value is inserted without any type or without verifying that the new value is valid according to the type of the node if schema information is available.</span></span>  
  
 <span data-ttu-id="16071-148">Dans l'exemple suivant, la méthode <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> permet de mettre à jour tous les éléments `price` du fichier `contosoBooks.xml`.</span><span class="sxs-lookup"><span data-stu-id="16071-148">In the following example, the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method is used to update all `price` elements in the `contosoBooks.xml` file.</span></span>  
  
 [!code-cpp[XPathNavigatorMethods#47](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#47)]
 [!code-csharp[XPathNavigatorMethods#47](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#47)]
 [!code-vb[XPathNavigatorMethods#47](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#47)]  
  
 <span data-ttu-id="16071-149">L'exemple prend le fichier `contosoBooks.xml` comme entrée.</span><span class="sxs-lookup"><span data-stu-id="16071-149">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="inserting-typed-values"></a><span data-ttu-id="16071-150">Insertion de valeurs typées</span><span class="sxs-lookup"><span data-stu-id="16071-150">Inserting Typed Values</span></span>  
 <span data-ttu-id="16071-151">Si le type d'un nœud est un type simple des schémas XML du W3C, la nouvelle valeur insérée par la méthode <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> est vérifiée par rapport aux facettes du type simple avant d'être définie.</span><span class="sxs-lookup"><span data-stu-id="16071-151">When the type of a node is a W3C XML Schema simple type, the new value inserted by the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method is checked against the facets of the simple type before the value is set.</span></span> <span data-ttu-id="16071-152">Si la nouvelle valeur n'est pas valide par rapport au type du nœud (par exemple, une valeur est définie sur `-1` pour un élément dont le type est `xs:positiveInteger`), une exception se produit.</span><span class="sxs-lookup"><span data-stu-id="16071-152">If the new value is not valid according to the type of the node (for example, setting a value of `-1` on an element whose type is `xs:positiveInteger`), it results in an exception.</span></span>  
  
 <span data-ttu-id="16071-153">L'exemple suivant tente de modifier la valeur de l'élément `price` du premier élément `book` du fichier `contosoBooks.xml` en valeur <xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="16071-153">The following example attempts to change the value of the `price` element of the first `book` element in the `contosoBooks.xml` file to a <xref:System.DateTime> value.</span></span> <span data-ttu-id="16071-154">Étant donné que le type de schéma XML de l'élément `price` est défini comme `xs:decimal` dans les fichiers `contosoBooks.xsd`, une exception se produit.</span><span class="sxs-lookup"><span data-stu-id="16071-154">Because the XML Schema type of the `price` element is defined as `xs:decimal` in the `contosoBooks.xsd` files, this results in an exception.</span></span>  
  
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
  
 <span data-ttu-id="16071-155">L'exemple prend le fichier `contosoBooks.xml` comme entrée.</span><span class="sxs-lookup"><span data-stu-id="16071-155">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="16071-156">L'exemple prend également le fichier `contosoBooks.xsd` comme entrée.</span><span class="sxs-lookup"><span data-stu-id="16071-156">The example also takes the `contosoBooks.xsd` as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
## <a name="the-innerxml-and-outerxml-properties"></a><span data-ttu-id="16071-157">Propriétés InnerXml et OuterXml</span><span class="sxs-lookup"><span data-stu-id="16071-157">The InnerXml and OuterXml Properties</span></span>  
 <span data-ttu-id="16071-158">Les propriétés <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> et <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> de la classe <xref:System.Xml.XPath.XPathNavigator> modifient le balisage XML des nœuds sur lesquels un objet <xref:System.Xml.XPath.XPathNavigator> est actuellement positionné.</span><span class="sxs-lookup"><span data-stu-id="16071-158">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties of the <xref:System.Xml.XPath.XPathNavigator> class change the XML markup of the nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span>  
  
 <span data-ttu-id="16071-159">La propriété <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> modifie le balisage XML des nœuds enfants sur lesquels un objet <xref:System.Xml.XPath.XPathNavigator> est actuellement positionné avec le contenu analysé de la `string` XML donnée.</span><span class="sxs-lookup"><span data-stu-id="16071-159">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on with the parsed contents of the given XML `string`.</span></span> <span data-ttu-id="16071-160">De même, la propriété <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> modifie le balisage XML des nœuds enfants sur lesquels un objet <xref:System.Xml.XPath.XPathNavigator> est actuellement positionné, ainsi que le nœud actuel proprement dit.</span><span class="sxs-lookup"><span data-stu-id="16071-160">Similarly, the <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on as well as the current node itself.</span></span>  
  
 <span data-ttu-id="16071-161">Outre les méthodes décrites dans cette rubrique, les propriétés <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> et <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> peuvent permettre d'insérer des nœuds et des valeurs dans un document XML.</span><span class="sxs-lookup"><span data-stu-id="16071-161">In addition to the methods described in this topic, the <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties can be used to insert nodes and values in an XML document.</span></span> <span data-ttu-id="16071-162">Pour plus d'informations sur l'utilisation des propriétés <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> et <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> pour insérer des nœuds et des valeurs, consultez la rubrique [Modification de données XML à l’aide de XPathNavigator](modify-xml-data-using-xpathnavigator.md).</span><span class="sxs-lookup"><span data-stu-id="16071-162">For more information about using the <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties to insert nodes and values, see the [Modify XML Data using XPathNavigator](modify-xml-data-using-xpathnavigator.md) topic.</span></span>  
  
## <a name="namespace-and-xmllang-conflicts"></a><span data-ttu-id="16071-163">Conflits d'espace de noms et xml:lang</span><span class="sxs-lookup"><span data-stu-id="16071-163">Namespace and xml:lang Conflicts</span></span>  
 <span data-ttu-id="16071-164">Certains conflits relatifs à la portée de l'espace de noms et aux déclarations `xml:lang` peuvent survenir lors de l'insertion de données XML à l'aide des méthodes <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> et <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> de la classe <xref:System.Xml.XPath.XPathNavigator> qui prend les objets <xref:System.Xml.XmlReader> comme paramètres.</span><span class="sxs-lookup"><span data-stu-id="16071-164">Certain conflicts related to the scope of namespace and `xml:lang` declarations can occur when inserting XML data using the <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> and <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> methods of the <xref:System.Xml.XPath.XPathNavigator> class that take <xref:System.Xml.XmlReader> objects as parameters.</span></span>  
  
 <span data-ttu-id="16071-165">Les conflits d'espace de noms possibles sont les suivants.</span><span class="sxs-lookup"><span data-stu-id="16071-165">The following are the possible namespace conflicts.</span></span>  
  
- <span data-ttu-id="16071-166">Si un espace de noms se trouve dans la portée du contexte de l'objet <xref:System.Xml.XmlReader> où le préfixe du mappage de l'URI d'espace de noms ne se trouve pas dans le contexte de l'objet <xref:System.Xml.XPath.XPathNavigator>, une nouvelle déclaration d'espace de noms est ajoutée au nœud qui vient d'être inséré.</span><span class="sxs-lookup"><span data-stu-id="16071-166">If there is a namespace in-scope within the <xref:System.Xml.XmlReader> object's context, where the prefix to namespace URI mapping is not in the <xref:System.Xml.XPath.XPathNavigator> object's context, a new namespace declaration is added to the newly inserted node.</span></span>  
  
- <span data-ttu-id="16071-167">Si le même URI d'espace de noms se trouve dans la portée du contexte des objets <xref:System.Xml.XmlReader> et <xref:System.Xml.XPath.XPathNavigator>, mais dont le préfixe mappé est différent dans les deux contextes, une nouvelle déclaration d'espace de noms est ajoutée au nœud qui vient d'être inséré. Le préfixe et l'URI d'espace de noms de cette déclaration sont ceux de l'objet <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="16071-167">If the same namespace URI is in-scope within both the <xref:System.Xml.XmlReader> object's context and the <xref:System.Xml.XPath.XPathNavigator> object's context, but has a different prefix mapped to it in both contexts, a new namespace declaration is added to the newly inserted node, with the prefix and namespace URI taken from the <xref:System.Xml.XmlReader> object.</span></span>  
  
- <span data-ttu-id="16071-168">Si le même préfixe d'espace de noms se trouve dans la portée du contexte des objets <xref:System.Xml.XmlReader> et <xref:System.Xml.XPath.XPathNavigator>, mais dont l'URI d'espace de noms mappé est différent dans les deux contextes, une nouvelle déclaration d'espace de noms est ajoutée au nœud qui vient d'être inséré. Celle-ci redéclare ce préfixe avec l'URI d'espace de noms provenant de l'objet <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="16071-168">If the same namespace prefix is in-scope within both the <xref:System.Xml.XmlReader> object's context and the <xref:System.Xml.XPath.XPathNavigator> object's context, but has a different namespace URI mapped to it in both contexts, a new namespace declaration is added to the newly inserted node which re-declares that prefix with the namespace URI taken from <xref:System.Xml.XmlReader> object.</span></span>  
  
- <span data-ttu-id="16071-169">Si le préfixe et l'URI d'espace de noms sont identiques dans le contexte des objets <xref:System.Xml.XmlReader> et <xref:System.Xml.XPath.XPathNavigator>, aucune déclaration d'espace de noms n'est ajoutée au nœud qui vient d'être inséré.</span><span class="sxs-lookup"><span data-stu-id="16071-169">If the prefix as well as the namespace URI in both the <xref:System.Xml.XmlReader> object's context and the <xref:System.Xml.XPath.XPathNavigator> object's context is the same, no new namespace declaration is added to the newly inserted node.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="16071-170">La description ci-dessus s'applique également aux déclarations d'espaces de noms ayant pour préfixe la `string` vide (par exemple, la déclaration d'espace de noms par défaut).</span><span class="sxs-lookup"><span data-stu-id="16071-170">The description above also applies to namespace declarations with the empty `string` as a prefix (for example, the default namespace declaration).</span></span>  
  
 <span data-ttu-id="16071-171">Les conflits `xml:lang` possibles sont les suivants.</span><span class="sxs-lookup"><span data-stu-id="16071-171">The following are the possible `xml:lang` conflicts.</span></span>  
  
- <span data-ttu-id="16071-172">Si un attribut `xml:lang` se trouve dans la portée du contexte de l'objet <xref:System.Xml.XmlReader>, mais pas de l'objet <xref:System.Xml.XPath.XPathNavigator>, un attribut `xml:lang` dont la valeur est reprise dans l'objet <xref:System.Xml.XmlReader> est ajouté au nœud qui vient d'être inséré.</span><span class="sxs-lookup"><span data-stu-id="16071-172">If there is an `xml:lang` attribute in-scope within the <xref:System.Xml.XmlReader> object's context but not in the <xref:System.Xml.XPath.XPathNavigator> object's context, an `xml:lang` attribute whose value is taken from the <xref:System.Xml.XmlReader> object is added to the newly inserted node.</span></span>  
  
- <span data-ttu-id="16071-173">Si un attribut `xml:lang` se trouve dans la portée du contexte des objets <xref:System.Xml.XmlReader> et <xref:System.Xml.XPath.XPathNavigator>, mais si chacun présente une valeur différente, un attribut `xml:lang` dont la valeur est reprise dans l'objet <xref:System.Xml.XmlReader> est ajouté au nœud qui vient d'être inséré.</span><span class="sxs-lookup"><span data-stu-id="16071-173">If there is an `xml:lang` attribute in-scope within both the <xref:System.Xml.XmlReader> object's context and the <xref:System.Xml.XPath.XPathNavigator> object's context, but each has a different value, an `xml:lang` attribute whose value is taken from the <xref:System.Xml.XmlReader> object is added to the newly inserted node.</span></span>  
  
- <span data-ttu-id="16071-174">Si un attribut `xml:lang` se trouve dans la portée du contexte des objets <xref:System.Xml.XmlReader> et <xref:System.Xml.XPath.XPathNavigator> et si chacun présente la même valeur, aucun attribut `xml:lang` n'est ajouté au nœud qui vient d'être inséré.</span><span class="sxs-lookup"><span data-stu-id="16071-174">If there is an `xml:lang` attribute in-scope within both the <xref:System.Xml.XmlReader> object's context and the <xref:System.Xml.XPath.XPathNavigator> object's context, but each with the same value, no new `xml:lang` attribute is added on the newly inserted node.</span></span>  
  
- <span data-ttu-id="16071-175">Si un attribut `xml:lang` se trouve dans la portée du contexte de l'objet <xref:System.Xml.XPath.XPathNavigator> et si aucun n'existe dans le contexte de l'objet <xref:System.Xml.XmlReader>, aucun attribut `xml:lang` n'est ajouté au nœud qui vient d'être inséré.</span><span class="sxs-lookup"><span data-stu-id="16071-175">If there is an `xml:lang` attribute in-scope within the <xref:System.Xml.XPath.XPathNavigator> object's context, but none existing in the <xref:System.Xml.XmlReader> object's context, no `xml:lang` attribute is added to the newly inserted node.</span></span>  
  
## <a name="inserting-nodes-with-xmlwriter"></a><span data-ttu-id="16071-176">Insertion de nœuds avec XmlWriter</span><span class="sxs-lookup"><span data-stu-id="16071-176">Inserting Nodes with XmlWriter</span></span>  
 <span data-ttu-id="16071-177">Les méthodes permettant d'insérer des nœuds frères, enfants et d'attribut décrites dans la section sur l'insertion de nœuds et de valeurs sont surchargées.</span><span class="sxs-lookup"><span data-stu-id="16071-177">The methods used to insert sibling, child and attribute nodes described in the "Inserting Nodes and Values" section are overloaded.</span></span> <span data-ttu-id="16071-178">Les méthodes <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> et <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> de la classe <xref:System.Xml.XPath.XPathNavigator> retournent un objet <xref:System.Xml.XmlWriter> permettant d'insérer des nœuds.</span><span class="sxs-lookup"><span data-stu-id="16071-178">The <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> and <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> methods of the <xref:System.Xml.XPath.XPathNavigator> class return an <xref:System.Xml.XmlWriter> object used to insert nodes.</span></span>  
  
### <a name="unsupported-xmlwriter-methods"></a><span data-ttu-id="16071-179">Méthodes XmlWriter non prises en charge</span><span class="sxs-lookup"><span data-stu-id="16071-179">Unsupported XmlWriter Methods</span></span>  
 <span data-ttu-id="16071-180">Toutes les méthodes permettant d’écrire des informations dans un document XML à l’aide de la classe <xref:System.Xml.XmlWriter> ne sont pas prises en charge par la classe <xref:System.Xml.XPath.XPathNavigator> en raison de la différence entre le modèle de données XPath et le DOM (Document Object Model).</span><span class="sxs-lookup"><span data-stu-id="16071-180">Not all of the methods used for writing information to an XML document using the <xref:System.Xml.XmlWriter> class are supported by the <xref:System.Xml.XPath.XPathNavigator> class due to difference between the XPath data model and the Document Object Model (DOM).</span></span>  
  
 <span data-ttu-id="16071-181">Le tableau suivant décrit les méthodes de la classe <xref:System.Xml.XmlWriter> non prises en charge par la classe <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="16071-181">The following table describes the <xref:System.Xml.XmlWriter> class methods not supported by the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
|<span data-ttu-id="16071-182">Méthode</span><span class="sxs-lookup"><span data-stu-id="16071-182">Method</span></span>|<span data-ttu-id="16071-183">Description</span><span class="sxs-lookup"><span data-stu-id="16071-183">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.XmlWriter.WriteEntityRef%2A>|<span data-ttu-id="16071-184">Lève une exception <xref:System.NotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="16071-184">Throws a <xref:System.NotSupportedException> exception.</span></span>|  
|<xref:System.Xml.XmlWriter.WriteDocType%2A>|<span data-ttu-id="16071-185">Ignorée au niveau racine et lève une exception <xref:System.NotSupportedException> en cas d'appel à tout autre niveau du document XML.</span><span class="sxs-lookup"><span data-stu-id="16071-185">Ignored at the root level and throws a <xref:System.NotSupportedException> exception if called at any other level in the XML document.</span></span>|  
|<xref:System.Xml.XmlWriter.WriteCData%2A>|<span data-ttu-id="16071-186">Traitée comme un appel à la méthode <xref:System.Xml.XmlWriter.WriteString%2A> pour le ou les caractères équivalents.</span><span class="sxs-lookup"><span data-stu-id="16071-186">Treated as a call to the <xref:System.Xml.XmlWriter.WriteString%2A> method for the equivalent character or characters.</span></span>|  
|<xref:System.Xml.XmlWriter.WriteCharEntity%2A>|<span data-ttu-id="16071-187">Traitée comme un appel à la méthode <xref:System.Xml.XmlWriter.WriteString%2A> pour le ou les caractères équivalents.</span><span class="sxs-lookup"><span data-stu-id="16071-187">Treated as a call to the <xref:System.Xml.XmlWriter.WriteString%2A> method for the equivalent character or characters.</span></span>|  
|<xref:System.Xml.XmlWriter.WriteSurrogateCharEntity%2A>|<span data-ttu-id="16071-188">Traitée comme un appel à la méthode <xref:System.Xml.XmlWriter.WriteString%2A> pour le ou les caractères équivalents.</span><span class="sxs-lookup"><span data-stu-id="16071-188">Treated as a call to the <xref:System.Xml.XmlWriter.WriteString%2A> method for the equivalent character or characters.</span></span>|  
  
 <span data-ttu-id="16071-189">Pour plus d'informations sur la classe <xref:System.Xml.XmlWriter>, voir la documentation de référence sur la classe <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="16071-189">For more information about the <xref:System.Xml.XmlWriter> class, see the <xref:System.Xml.XmlWriter> class reference documentation.</span></span>  
  
### <a name="multiple-xmlwriter-objects"></a><span data-ttu-id="16071-190">Objets XmlWriter multiples</span><span class="sxs-lookup"><span data-stu-id="16071-190">Multiple XmlWriter Objects</span></span>  
 <span data-ttu-id="16071-191">Il est possible que plusieurs objets <xref:System.Xml.XPath.XPathNavigator> pointent sur différentes parties d'un document XML avec au moins un objet <xref:System.Xml.XmlWriter> ouvert.</span><span class="sxs-lookup"><span data-stu-id="16071-191">It is possible to have multiple <xref:System.Xml.XPath.XPathNavigator> objects pointing to different parts of an XML document with one or more open <xref:System.Xml.XmlWriter> objects.</span></span> <span data-ttu-id="16071-192">Plusieurs objets <xref:System.Xml.XmlWriter> sont autorisés et pris en charge dans des scénarios monothread.</span><span class="sxs-lookup"><span data-stu-id="16071-192">Multiple <xref:System.Xml.XmlWriter> objects are allowed and supported in single-threaded scenarios.</span></span>  
  
 <span data-ttu-id="16071-193">Les remarques suivantes sont importantes en cas d'utilisation de plusieurs objets <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="16071-193">The following are important notes to consider when using multiple <xref:System.Xml.XmlWriter> objects.</span></span>  
  
- <span data-ttu-id="16071-194">Les fragments XML écrits par les objets <xref:System.Xml.XmlWriter> sont ajoutés au document XML en cas d'appel de la méthode <xref:System.Xml.XmlWriter.Close%2A> de chaque objet <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="16071-194">XML fragments written by <xref:System.Xml.XmlWriter> objects are added to the XML document when the <xref:System.Xml.XmlWriter.Close%2A> method of each <xref:System.Xml.XmlWriter> object is called.</span></span> <span data-ttu-id="16071-195">Dans les autres cas, l'objet <xref:System.Xml.XmlWriter> écrit un fragment déconnecté.</span><span class="sxs-lookup"><span data-stu-id="16071-195">Until that point, the <xref:System.Xml.XmlWriter> object is writing a disconnected fragment.</span></span> <span data-ttu-id="16071-196">Si une opération est effectuée sur le document XML, avant l'appel de <xref:System.Xml.XmlWriter>, aucun fragment en cours d'écriture par un objet <xref:System.Xml.XmlWriter.Close%2A> n'est affecté.</span><span class="sxs-lookup"><span data-stu-id="16071-196">If an operation is performed on the XML document, any fragments being written by an <xref:System.Xml.XmlWriter> object, before the <xref:System.Xml.XmlWriter.Close%2A> has been called, are not affected.</span></span>  
  
- <span data-ttu-id="16071-197">Si un objet <xref:System.Xml.XmlWriter> ouvert existe dans une sous-arborescence XML particulière et si cette sous-arborescence est supprimée, l’objet <xref:System.Xml.XmlWriter> peut encore être ajouté à la sous-arborescence.</span><span class="sxs-lookup"><span data-stu-id="16071-197">If there is an open <xref:System.Xml.XmlWriter> object on a particular XML subtree and that subtree is deleted, the <xref:System.Xml.XmlWriter> object may still add to the sub-tree.</span></span> <span data-ttu-id="16071-198">La sous-arborescence devient simplement un fragment supprimé.</span><span class="sxs-lookup"><span data-stu-id="16071-198">The subtree simply becomes a deleted fragment.</span></span>  
  
- <span data-ttu-id="16071-199">Si plusieurs objets <xref:System.Xml.XmlWriter> sont ouverts au même point du document XML, ils sont ajoutés au document XML dans l'ordre dans lequel les objets <xref:System.Xml.XmlWriter> sont fermés, pas dans l'ordre dans lequel ils ont été ouverts.</span><span class="sxs-lookup"><span data-stu-id="16071-199">If multiple <xref:System.Xml.XmlWriter> objects are opened at the same point in the XML document, they are added to the XML document in the order in which the <xref:System.Xml.XmlWriter> objects are closed, not in the order in which they were opened.</span></span>  
  
 <span data-ttu-id="16071-200">L'exemple suivant crée un objet <xref:System.Xml.XmlDocument> et un objet <xref:System.Xml.XPath.XPathNavigator>, puis utilise l'objet <xref:System.Xml.XmlWriter> retourné par la méthode <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> pour créer la structure du premier livre du fichier `books.xml`.</span><span class="sxs-lookup"><span data-stu-id="16071-200">The following example creates an <xref:System.Xml.XmlDocument> object, creates an <xref:System.Xml.XPath.XPathNavigator> object, and then uses the <xref:System.Xml.XmlWriter> object returned by the <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> method to create the structure of the first book in the `books.xml` file.</span></span> <span data-ttu-id="16071-201">L'exemple l'enregistre ensuite comme fichier `book.xml`.</span><span class="sxs-lookup"><span data-stu-id="16071-201">The example then saves it as the `book.xml` file.</span></span>  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
Using writer As XmlWriter = navigator.PrependChild()  
  
    writer.WriteStartElement("bookstore")  
    writer.WriteStartElement("book")  
    writer.WriteAttributeString("genre", "autobiography")  
    writer.WriteAttributeString("publicationdate", "1981-03-22")  
    writer.WriteAttributeString("ISBN", "1-861003-11-0")  
    writer.WriteElementString("title", "The Autobiography of Benjamin Franklin")  
    writer.WriteStartElement("author")  
    writer.WriteElementString("first-name", "Benjamin")  
    writer.WriteElementString("last-name", "Franklin")  
    writer.WriteElementString("price", "8.99")  
    writer.WriteEndElement()  
    writer.WriteEndElement()  
    writer.WriteEndElement()  
  
End Using  
  
document.Save("book.xml")  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
XPathNavigator navigator = document.CreateNavigator();  
  
using (XmlWriter writer = navigator.PrependChild())  
{  
    writer.WriteStartElement("bookstore");  
    writer.WriteStartElement("book");  
    writer.WriteAttributeString("genre", "autobiography");  
    writer.WriteAttributeString("publicationdate", "1981-03-22");  
    writer.WriteAttributeString("ISBN", "1-861003-11-0");  
    writer.WriteElementString("title", "The Autobiography of Benjamin Franklin");  
    writer.WriteStartElement("author");  
    writer.WriteElementString("first-name", "Benjamin");  
    writer.WriteElementString("last-name", "Franklin");  
    writer.WriteElementString("price", "8.99");  
    writer.WriteEndElement();  
    writer.WriteEndElement();  
    writer.WriteEndElement();  
}  
document.Save("book.xml");  
```  
  
## <a name="saving-an-xml-document"></a><span data-ttu-id="16071-202">Enregistrement d'un document XML</span><span class="sxs-lookup"><span data-stu-id="16071-202">Saving an XML Document</span></span>  
 <span data-ttu-id="16071-203">L'enregistrement des modifications apportées à un objet <xref:System.Xml.XmlDocument> suite aux méthodes décrites dans cette rubrique s'effectue à l'aide des méthodes de la classe <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="16071-203">Saving changes made to an <xref:System.Xml.XmlDocument> object as the result of the methods described in this topic is performed using the methods of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="16071-204">Pour plus d'informations sur l'enregistrement des modifications apportées à un objet <xref:System.Xml.XmlDocument>, consultez [Enregistrement et écriture d'un document](saving-and-writing-a-document.md).</span><span class="sxs-lookup"><span data-stu-id="16071-204">For more information about saving changes made to an <xref:System.Xml.XmlDocument> object, see [Saving and Writing a Document](saving-and-writing-a-document.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16071-205">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="16071-205">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="16071-206">Traitement des données XML à l'aide du modèle de données XPath</span><span class="sxs-lookup"><span data-stu-id="16071-206">Process XML Data Using the XPath Data Model</span></span>](process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="16071-207">Modification de données XML à l’aide de XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="16071-207">Modify XML Data using XPathNavigator</span></span>](modify-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="16071-208">Suppression de données XML à l'aide de XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="16071-208">Remove XML Data using XPathNavigator</span></span>](remove-xml-data-using-xpathnavigator.md)
