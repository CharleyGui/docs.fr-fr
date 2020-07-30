---
title: Contenu valide des objets XElement et XDocument3
description: Découvrez les arguments valides qui peuvent être passés aux constructeurs et aux méthodes que vous utilisez pour ajouter du contenu aux éléments et aux documents.
ms.date: 07/20/2015
ms.assetid: 0d253586-2b97-459f-b1a7-f30f38f3ed9f
ms.openlocfilehash: dfafbe76b078db6c22b475770ebadaff38c75ba8
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302254"
---
# <a name="valid-content-of-xelement-and-xdocument-objects"></a><span data-ttu-id="526a0-103">Contenu valide des objets XElement et XDocument</span><span class="sxs-lookup"><span data-stu-id="526a0-103">Valid Content of XElement and XDocument Objects</span></span>
<span data-ttu-id="526a0-104">Cette rubrique décrit les arguments valides qui peuvent être passés aux constructeurs et méthodes utilisés pour ajouter du contenu aux éléments et aux documents.</span><span class="sxs-lookup"><span data-stu-id="526a0-104">This topic describes the valid arguments that can be passed to constructors and methods that you use to add content to elements and documents.</span></span>  
  
## <a name="valid-content"></a><span data-ttu-id="526a0-105">Contenu valide</span><span class="sxs-lookup"><span data-stu-id="526a0-105">Valid Content</span></span>  
 <span data-ttu-id="526a0-106">Les requêtes sont souvent évaluées à un objet <xref:System.Collections.Generic.IEnumerable%601> de <xref:System.Xml.Linq.XElement> ou un objet <xref:System.Collections.Generic.IEnumerable%601> de <xref:System.Xml.Linq.XAttribute>.</span><span class="sxs-lookup"><span data-stu-id="526a0-106">Queries often evaluate to <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement> or <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XAttribute>.</span></span> <span data-ttu-id="526a0-107">Vous pouvez passer des collections d'objets <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XAttribute> au constructeur <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="526a0-107">You can pass collections of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects to the <xref:System.Xml.Linq.XElement> constructor.</span></span> <span data-ttu-id="526a0-108">Par conséquent, il est commode de passer les résultats d'une requête en tant que contenu dans des méthodes et des constructeurs que vous utilisez pour remplir des arborescences XML.</span><span class="sxs-lookup"><span data-stu-id="526a0-108">Therefore, it is convenient to pass the results of a query as content into methods and constructors that you use to populate XML trees.</span></span>  
  
 <span data-ttu-id="526a0-109">Lors de l'ajout de contenu simple, divers types peuvent être passés à cette méthode.</span><span class="sxs-lookup"><span data-stu-id="526a0-109">When adding simple content, various types can be passed to this method.</span></span> <span data-ttu-id="526a0-110">Les types valides sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="526a0-110">Valid types include the following:</span></span>  
  
- <xref:System.String>  
  
- <xref:System.Double>  
  
- <xref:System.Single>  
  
- <xref:System.Decimal>  
  
- <xref:System.Boolean>  
  
- <xref:System.DateTime>  
  
- <xref:System.TimeSpan>  
  
- <xref:System.DateTimeOffset>  
  
- <span data-ttu-id="526a0-111">Tout type qui implémente `Object.ToString`.</span><span class="sxs-lookup"><span data-stu-id="526a0-111">Any type that implements `Object.ToString`.</span></span>  
  
- <span data-ttu-id="526a0-112">Tout type qui implémente <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="526a0-112">Any type that implements <xref:System.Collections.Generic.IEnumerable%601>.</span></span>  
  
 <span data-ttu-id="526a0-113">Lors de l'ajout de contenu complexe, divers types peuvent être passés à cette méthode :</span><span class="sxs-lookup"><span data-stu-id="526a0-113">When adding complex content, various types can be passed to this method:</span></span>  
  
- <xref:System.Xml.Linq.XObject>  
  
- <xref:System.Xml.Linq.XNode>  
  
- <xref:System.Xml.Linq.XAttribute>  
  
- <span data-ttu-id="526a0-114">Tout type qui implémente <xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="526a0-114">Any type that implements <xref:System.Collections.Generic.IEnumerable%601></span></span>  
  
 <span data-ttu-id="526a0-115">Si un objet implémente <xref:System.Collections.Generic.IEnumerable%601>, la collection dans l'objet est énumérée et tous les éléments de la collection sont ajoutés.</span><span class="sxs-lookup"><span data-stu-id="526a0-115">If an object implements <xref:System.Collections.Generic.IEnumerable%601>, the collection in the object is enumerated, and all items in the collection are added.</span></span> <span data-ttu-id="526a0-116">Si la collection contient des objets <xref:System.Xml.Linq.XNode> ou <xref:System.Xml.Linq.XAttribute>, chaque élément de la collection est ajouté séparément.</span><span class="sxs-lookup"><span data-stu-id="526a0-116">If the collection contains <xref:System.Xml.Linq.XNode> or <xref:System.Xml.Linq.XAttribute> objects, each item in the collection is added separately.</span></span> <span data-ttu-id="526a0-117">Si la collection contient du texte (ou des objets convertis en texte), le texte dans la collection est concaténé et ajouté en tant que nœud de texte simple.</span><span class="sxs-lookup"><span data-stu-id="526a0-117">If the collection contains text (or objects that are converted to text), the text in the collection is concatenated and added as a single text node.</span></span>  
  
 <span data-ttu-id="526a0-118">Si le contenu est `null`, rien n'est ajouté.</span><span class="sxs-lookup"><span data-stu-id="526a0-118">If content is `null`, nothing is added.</span></span> <span data-ttu-id="526a0-119">Lors du passage d'une collection, des éléments de cette collection peuvent avoir la valeur `null`.</span><span class="sxs-lookup"><span data-stu-id="526a0-119">When passing a collection items in the collection can be `null`.</span></span> <span data-ttu-id="526a0-120">Un élément `null` dans la collection n'a aucun effet sur l'arborescence.</span><span class="sxs-lookup"><span data-stu-id="526a0-120">A `null` item in the collection has no effect on the tree.</span></span>  
  
 <span data-ttu-id="526a0-121">Un attribut ajouté doit avoir un nom unique dans son élément conteneur.</span><span class="sxs-lookup"><span data-stu-id="526a0-121">An added attribute must have a unique name within its containing element.</span></span>  
  
 <span data-ttu-id="526a0-122">Lors de l’ajout d’objets <xref:System.Xml.Linq.XNode> ou <xref:System.Xml.Linq.XAttribute>, si le contenu n’a pas de parent, les objets sont simplement attachés à l’arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="526a0-122">When adding <xref:System.Xml.Linq.XNode> or <xref:System.Xml.Linq.XAttribute> objects, if the new content has no parent, then the objects are simply attached to the XML tree.</span></span> <span data-ttu-id="526a0-123">Si le nouveau contenu a déjà un parent et fait partie d'une autre arborescence XML, il est cloné et le nouveau contenu cloné est attaché à l'arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="526a0-123">If the new content already is parented and is part of another XML tree, then the new content is cloned, and the newly cloned content is attached to the XML tree.</span></span>  
  
## <a name="valid-content-for-documents"></a><span data-ttu-id="526a0-124">Contenu valide pour les documents</span><span class="sxs-lookup"><span data-stu-id="526a0-124">Valid Content for Documents</span></span>  
 <span data-ttu-id="526a0-125">Les attributs et le contenu simple ne peuvent pas être ajoutés à un document.</span><span class="sxs-lookup"><span data-stu-id="526a0-125">Attributes and simple content cannot be added to a document.</span></span>  
  
 <span data-ttu-id="526a0-126">Il n'existe pas beaucoup de scénarios qui requièrent la création d'un objet <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="526a0-126">There are not many scenarios that require you to create an <xref:System.Xml.Linq.XDocument>.</span></span> <span data-ttu-id="526a0-127">Au lieu de cela, vous pouvez généralement créer vos arborescences XML avec un nœud racine <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="526a0-127">Instead, you can usually create your XML trees with an <xref:System.Xml.Linq.XElement> root node.</span></span> <span data-ttu-id="526a0-128">À moins que la création d'un document ne soit spécifiquement requise (par exemple si vous devez créer des instructions de traitement et des commentaires au niveau supérieur ou si vous devez prendre en charge des types de documents), il est souvent plus commode d'utiliser <xref:System.Xml.Linq.XElement> comme nœud racine.</span><span class="sxs-lookup"><span data-stu-id="526a0-128">Unless you have a specific requirement to create a document (for example, because you have to create processing instructions and comments at the top level, or you have to support document types), it is often more convenient to use <xref:System.Xml.Linq.XElement> as your root node.</span></span>  
  
 <span data-ttu-id="526a0-129">Le contenu valide pour un document inclut les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="526a0-129">Valid content for a document includes the following:</span></span>  
  
- <span data-ttu-id="526a0-130">Zéro ou un objet <xref:System.Xml.Linq.XDocumentType>.</span><span class="sxs-lookup"><span data-stu-id="526a0-130">Zero or one <xref:System.Xml.Linq.XDocumentType> objects.</span></span> <span data-ttu-id="526a0-131">Les types de documents doivent figurer avant l'élément.</span><span class="sxs-lookup"><span data-stu-id="526a0-131">The document types must come before the element.</span></span>  
  
- <span data-ttu-id="526a0-132">Zéro ou un élément.</span><span class="sxs-lookup"><span data-stu-id="526a0-132">Zero or one element.</span></span>  
  
- <span data-ttu-id="526a0-133">Zéro ou plusieurs commentaires.</span><span class="sxs-lookup"><span data-stu-id="526a0-133">Zero or more comments.</span></span>  
  
- <span data-ttu-id="526a0-134">Zéro ou plusieurs instructions de traitement.</span><span class="sxs-lookup"><span data-stu-id="526a0-134">Zero or more processing instructions.</span></span>  
  
- <span data-ttu-id="526a0-135">Zéro ou plusieurs nœuds de texte qui contiennent uniquement des espaces blancs.</span><span class="sxs-lookup"><span data-stu-id="526a0-135">Zero or more text nodes that contain only white space.</span></span>  
  
## <a name="constructors-and-functions-that-allow-adding-content"></a><span data-ttu-id="526a0-136">Constructeurs et fonctions qui autorisent l'ajout de contenu</span><span class="sxs-lookup"><span data-stu-id="526a0-136">Constructors and Functions that Allow Adding Content</span></span>  
 <span data-ttu-id="526a0-137">Les méthodes suivantes vous permettent d'ajouter du contenu enfant à un objet <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XDocument> :</span><span class="sxs-lookup"><span data-stu-id="526a0-137">The following methods allow you to add child content to an <xref:System.Xml.Linq.XElement> or an <xref:System.Xml.Linq.XDocument>:</span></span>  
  
|<span data-ttu-id="526a0-138">Méthode</span><span class="sxs-lookup"><span data-stu-id="526a0-138">Method</span></span>|<span data-ttu-id="526a0-139">Description</span><span class="sxs-lookup"><span data-stu-id="526a0-139">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.%23ctor%2A>|<span data-ttu-id="526a0-140">Construit un objet <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="526a0-140">Constructs an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XDocument.%23ctor%2A>|<span data-ttu-id="526a0-141">Construit un objet <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="526a0-141">Constructs a <xref:System.Xml.Linq.XDocument>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.Add%2A>|<span data-ttu-id="526a0-142">Ajoute à la fin du contenu enfant de l'objet <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="526a0-142">Adds to the end of the child content of the <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>.</span></span>|  
|<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>|<span data-ttu-id="526a0-143">Ajoute du contenu après l'objet <xref:System.Xml.Linq.XNode>.</span><span class="sxs-lookup"><span data-stu-id="526a0-143">Adds content after the <xref:System.Xml.Linq.XNode>.</span></span>|  
|<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>|<span data-ttu-id="526a0-144">Ajoute du contenu avant l'objet <xref:System.Xml.Linq.XNode>.</span><span class="sxs-lookup"><span data-stu-id="526a0-144">Adds content before the <xref:System.Xml.Linq.XNode>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.AddFirst%2A>|<span data-ttu-id="526a0-145">Ajoute du contenu au début du contenu enfant de l'objet <xref:System.Xml.Linq.XContainer>.</span><span class="sxs-lookup"><span data-stu-id="526a0-145">Adds content at the beginning of the child content of the <xref:System.Xml.Linq.XContainer>.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A>|<span data-ttu-id="526a0-146">Remplace tout le contenu (nœuds enfants et attributs) d'un objet <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="526a0-146">Replaces all content (child nodes and attributes) of an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A>|<span data-ttu-id="526a0-147">Remplace les attributs d'un objet <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="526a0-147">Replaces the attributes of an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A>|<span data-ttu-id="526a0-148">Remplace les nœuds enfants par du nouveau contenu.</span><span class="sxs-lookup"><span data-stu-id="526a0-148">Replaces the children nodes with new content.</span></span>|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A>|<span data-ttu-id="526a0-149">Remplace un nœud par du nouveau contenu.</span><span class="sxs-lookup"><span data-stu-id="526a0-149">Replaces a node with new content.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="526a0-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="526a0-150">See also</span></span>

- [<span data-ttu-id="526a0-151">Création d’arborescences XML (C#)</span><span class="sxs-lookup"><span data-stu-id="526a0-151">Creating XML Trees (C#)</span></span>](./linq-to-xml-overview.md)
