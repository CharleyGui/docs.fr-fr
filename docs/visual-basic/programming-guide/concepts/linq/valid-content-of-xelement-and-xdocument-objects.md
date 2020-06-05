---
title: Contenu valide des Objects2 XElement et XDocument
ms.date: 07/20/2015
ms.assetid: 400bb692-478a-40b6-ac1b-4ccbb4cbbd02
ms.openlocfilehash: d222f19f6f588968a3ef1515dca522a4a80e1ffb
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84364342"
---
# <a name="valid-content-of-xelement-and-xdocument-objects"></a><span data-ttu-id="5a774-102">Contenu valide des objets XElement et XDocument</span><span class="sxs-lookup"><span data-stu-id="5a774-102">Valid Content of XElement and XDocument Objects</span></span>
<span data-ttu-id="5a774-103">Cette rubrique décrit les arguments valides qui peuvent être passés aux constructeurs et méthodes utilisés pour ajouter du contenu aux éléments et aux documents.</span><span class="sxs-lookup"><span data-stu-id="5a774-103">This topic describes the valid arguments that can be passed to constructors and methods that you use to add content to elements and documents.</span></span>  
  
## <a name="valid-content"></a><span data-ttu-id="5a774-104">Contenu valide</span><span class="sxs-lookup"><span data-stu-id="5a774-104">Valid Content</span></span>  
 <span data-ttu-id="5a774-105">Les requêtes sont souvent évaluées à un objet <xref:System.Collections.Generic.IEnumerable%601> de <xref:System.Xml.Linq.XElement> ou un objet <xref:System.Collections.Generic.IEnumerable%601> de <xref:System.Xml.Linq.XAttribute>.</span><span class="sxs-lookup"><span data-stu-id="5a774-105">Queries often evaluate to <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement> or <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XAttribute>.</span></span> <span data-ttu-id="5a774-106">Vous pouvez passer des collections d'objets <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XAttribute> au constructeur <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="5a774-106">You can pass collections of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects to the <xref:System.Xml.Linq.XElement> constructor.</span></span> <span data-ttu-id="5a774-107">Par conséquent, il est commode de passer les résultats d'une requête en tant que contenu dans des méthodes et des constructeurs que vous utilisez pour remplir des arborescences XML.</span><span class="sxs-lookup"><span data-stu-id="5a774-107">Therefore, it is convenient to pass the results of a query as content into methods and constructors that you use to populate XML trees.</span></span>  
  
 <span data-ttu-id="5a774-108">Lors de l'ajout de contenu simple, divers types peuvent être passés à cette méthode.</span><span class="sxs-lookup"><span data-stu-id="5a774-108">When adding simple content, various types can be passed to this method.</span></span> <span data-ttu-id="5a774-109">Les types valides sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="5a774-109">Valid types include the following:</span></span>  
  
- <xref:System.String>  
  
- <xref:System.Double>  
  
- <xref:System.Single>  
  
- <xref:System.Decimal>  
  
- <xref:System.Boolean>  
  
- <xref:System.DateTime>  
  
- <xref:System.TimeSpan>  
  
- <xref:System.DateTimeOffset>  
  
- <span data-ttu-id="5a774-110">Tout type qui implémente `Object.ToString`.</span><span class="sxs-lookup"><span data-stu-id="5a774-110">Any type that implements `Object.ToString`.</span></span>  
  
- <span data-ttu-id="5a774-111">Tout type qui implémente <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="5a774-111">Any type that implements <xref:System.Collections.Generic.IEnumerable%601>.</span></span>  
  
 <span data-ttu-id="5a774-112">Lors de l'ajout de contenu complexe, divers types peuvent être passés à cette méthode :</span><span class="sxs-lookup"><span data-stu-id="5a774-112">When adding complex content, various types can be passed to this method:</span></span>  
  
- <xref:System.Xml.Linq.XObject>  
  
- <xref:System.Xml.Linq.XNode>  
  
- <xref:System.Xml.Linq.XAttribute>  
  
- <span data-ttu-id="5a774-113">Tout type qui implémente <xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="5a774-113">Any type that implements <xref:System.Collections.Generic.IEnumerable%601></span></span>  
  
 <span data-ttu-id="5a774-114">Si un objet implémente <xref:System.Collections.Generic.IEnumerable%601>, la collection dans l'objet est énumérée et tous les éléments de la collection sont ajoutés.</span><span class="sxs-lookup"><span data-stu-id="5a774-114">If an object implements <xref:System.Collections.Generic.IEnumerable%601>, the collection in the object is enumerated, and all items in the collection are added.</span></span> <span data-ttu-id="5a774-115">Si la collection contient des objets <xref:System.Xml.Linq.XNode> ou <xref:System.Xml.Linq.XAttribute>, chaque élément de la collection est ajouté séparément.</span><span class="sxs-lookup"><span data-stu-id="5a774-115">If the collection contains <xref:System.Xml.Linq.XNode> or <xref:System.Xml.Linq.XAttribute> objects, each item in the collection is added separately.</span></span> <span data-ttu-id="5a774-116">Si la collection contient du texte (ou des objets convertis en texte), le texte dans la collection est concaténé et ajouté en tant que nœud de texte simple.</span><span class="sxs-lookup"><span data-stu-id="5a774-116">If the collection contains text (or objects that are converted to text), the text in the collection is concatenated and added as a single text node.</span></span>  
  
 <span data-ttu-id="5a774-117">Si le contenu est `null`, rien n'est ajouté.</span><span class="sxs-lookup"><span data-stu-id="5a774-117">If content is `null`, nothing is added.</span></span> <span data-ttu-id="5a774-118">Lors du passage d'une collection, des éléments de cette collection peuvent avoir la valeur `null`.</span><span class="sxs-lookup"><span data-stu-id="5a774-118">When passing a collection items in the collection can be `null`.</span></span> <span data-ttu-id="5a774-119">Un élément `null` dans la collection n'a aucun effet sur l'arborescence.</span><span class="sxs-lookup"><span data-stu-id="5a774-119">A `null` item in the collection has no effect on the tree.</span></span>  
  
 <span data-ttu-id="5a774-120">Un attribut ajouté doit avoir un nom unique dans son élément conteneur.</span><span class="sxs-lookup"><span data-stu-id="5a774-120">An added attribute must have a unique name within its containing element.</span></span>  
  
 <span data-ttu-id="5a774-121">Lors de l’ajout d’objets <xref:System.Xml.Linq.XNode> ou <xref:System.Xml.Linq.XAttribute>, si le contenu n’a pas de parent, les objets sont simplement attachés à l’arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="5a774-121">When adding <xref:System.Xml.Linq.XNode> or <xref:System.Xml.Linq.XAttribute> objects, if the new content has no parent, then the objects are simply attached to the XML tree.</span></span> <span data-ttu-id="5a774-122">Si le nouveau contenu a déjà un parent et fait partie d'une autre arborescence XML, il est cloné et le nouveau contenu cloné est attaché à l'arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="5a774-122">If the new content already is parented and is part of another XML tree, then the new content is cloned, and the newly cloned content is attached to the XML tree.</span></span>  
  
## <a name="valid-content-for-documents"></a><span data-ttu-id="5a774-123">Contenu valide pour les documents</span><span class="sxs-lookup"><span data-stu-id="5a774-123">Valid Content for Documents</span></span>  
 <span data-ttu-id="5a774-124">Les attributs et le contenu simple ne peuvent pas être ajoutés à un document.</span><span class="sxs-lookup"><span data-stu-id="5a774-124">Attributes and simple content cannot be added to a document.</span></span>  
  
 <span data-ttu-id="5a774-125">Il n'existe pas beaucoup de scénarios qui requièrent la création d'un objet <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="5a774-125">There are not many scenarios that require you to create an <xref:System.Xml.Linq.XDocument>.</span></span> <span data-ttu-id="5a774-126">Au lieu de cela, vous pouvez généralement créer vos arborescences XML avec un nœud racine <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="5a774-126">Instead, you can usually create your XML trees with an <xref:System.Xml.Linq.XElement> root node.</span></span> <span data-ttu-id="5a774-127">À moins que la création d'un document ne soit spécifiquement requise (par exemple si vous devez créer des instructions de traitement et des commentaires au niveau supérieur ou si vous devez prendre en charge des types de documents), il est souvent plus commode d'utiliser <xref:System.Xml.Linq.XElement> comme nœud racine.</span><span class="sxs-lookup"><span data-stu-id="5a774-127">Unless you have a specific requirement to create a document (for example, because you have to create processing instructions and comments at the top level, or you have to support document types), it is often more convenient to use <xref:System.Xml.Linq.XElement> as your root node.</span></span>  
  
 <span data-ttu-id="5a774-128">Le contenu valide pour un document inclut les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="5a774-128">Valid content for a document includes the following:</span></span>  
  
- <span data-ttu-id="5a774-129">Zéro ou un objet <xref:System.Xml.Linq.XDocumentType>.</span><span class="sxs-lookup"><span data-stu-id="5a774-129">Zero or one <xref:System.Xml.Linq.XDocumentType> objects.</span></span> <span data-ttu-id="5a774-130">Les types de documents doivent figurer avant l'élément.</span><span class="sxs-lookup"><span data-stu-id="5a774-130">The document types must come before the element.</span></span>  
  
- <span data-ttu-id="5a774-131">Zéro ou un élément.</span><span class="sxs-lookup"><span data-stu-id="5a774-131">Zero or one element.</span></span>  
  
- <span data-ttu-id="5a774-132">Zéro ou plusieurs commentaires.</span><span class="sxs-lookup"><span data-stu-id="5a774-132">Zero or more comments.</span></span>  
  
- <span data-ttu-id="5a774-133">Zéro ou plusieurs instructions de traitement.</span><span class="sxs-lookup"><span data-stu-id="5a774-133">Zero or more processing instructions.</span></span>  
  
- <span data-ttu-id="5a774-134">Zéro ou plusieurs nœuds de texte qui contiennent uniquement des espaces blancs.</span><span class="sxs-lookup"><span data-stu-id="5a774-134">Zero or more text nodes that contain only white space.</span></span>  
  
## <a name="constructors-and-functions-that-allow-adding-content"></a><span data-ttu-id="5a774-135">Constructeurs et fonctions qui autorisent l'ajout de contenu</span><span class="sxs-lookup"><span data-stu-id="5a774-135">Constructors and Functions that Allow Adding Content</span></span>  
 <span data-ttu-id="5a774-136">Les méthodes suivantes vous permettent d'ajouter du contenu enfant à un objet <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XDocument> :</span><span class="sxs-lookup"><span data-stu-id="5a774-136">The following methods allow you to add child content to an <xref:System.Xml.Linq.XElement> or an <xref:System.Xml.Linq.XDocument>:</span></span>  
  
|<span data-ttu-id="5a774-137">Méthode</span><span class="sxs-lookup"><span data-stu-id="5a774-137">Method</span></span>|<span data-ttu-id="5a774-138">Description</span><span class="sxs-lookup"><span data-stu-id="5a774-138">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.%23ctor%2A>|<span data-ttu-id="5a774-139">Construit un objet <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="5a774-139">Constructs an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XDocument.%23ctor%2A>|<span data-ttu-id="5a774-140">Construit un objet <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="5a774-140">Constructs a <xref:System.Xml.Linq.XDocument>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.Add%2A>|<span data-ttu-id="5a774-141">Ajoute à la fin du contenu enfant de l'objet <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="5a774-141">Adds to the end of the child content of the <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>.</span></span>|  
|<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>|<span data-ttu-id="5a774-142">Ajoute du contenu après l'objet <xref:System.Xml.Linq.XNode>.</span><span class="sxs-lookup"><span data-stu-id="5a774-142">Adds content after the <xref:System.Xml.Linq.XNode>.</span></span>|  
|<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>|<span data-ttu-id="5a774-143">Ajoute du contenu avant l'objet <xref:System.Xml.Linq.XNode>.</span><span class="sxs-lookup"><span data-stu-id="5a774-143">Adds content before the <xref:System.Xml.Linq.XNode>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.AddFirst%2A>|<span data-ttu-id="5a774-144">Ajoute du contenu au début du contenu enfant de l'objet <xref:System.Xml.Linq.XContainer>.</span><span class="sxs-lookup"><span data-stu-id="5a774-144">Adds content at the beginning of the child content of the <xref:System.Xml.Linq.XContainer>.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A>|<span data-ttu-id="5a774-145">Remplace tout le contenu (nœuds enfants et attributs) d'un objet <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="5a774-145">Replaces all content (child nodes and attributes) of an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A>|<span data-ttu-id="5a774-146">Remplace les attributs d'un objet <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="5a774-146">Replaces the attributes of an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A>|<span data-ttu-id="5a774-147">Remplace les nœuds enfants par du nouveau contenu.</span><span class="sxs-lookup"><span data-stu-id="5a774-147">Replaces the children nodes with new content.</span></span>|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A>|<span data-ttu-id="5a774-148">Remplace un nœud par du nouveau contenu.</span><span class="sxs-lookup"><span data-stu-id="5a774-148">Replaces a node with new content.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5a774-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5a774-149">See also</span></span>

- [<span data-ttu-id="5a774-150">Création d’arborescences XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5a774-150">Creating XML Trees (Visual Basic)</span></span>](creating-xml-trees.md)
