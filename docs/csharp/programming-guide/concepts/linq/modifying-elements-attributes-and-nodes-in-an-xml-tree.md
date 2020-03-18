---
title: Modification d’éléments, d’attributs et de nœuds dans une arborescence XML3
ms.date: 07/20/2015
ms.assetid: 0ed22e4e-4c6b-4eb1-b0eb-06685efd8c33
ms.openlocfilehash: 93a4d67129e22d0bbeef464c1d4d8758439edb7b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "66484232"
---
# <a name="modifying-elements-attributes-and-nodes-in-an-xml-tree"></a><span data-ttu-id="a6fde-102">Modification d’éléments, d’attributs et de nœuds dans une arborescence XML</span><span class="sxs-lookup"><span data-stu-id="a6fde-102">Modifying Elements, Attributes, and Nodes in an XML Tree</span></span>
<span data-ttu-id="a6fde-103">Le tableau suivant résume les méthodes et propriétés que vous pouvez utiliser pour modifier un élément, ses éléments enfants ou ses attributs.</span><span class="sxs-lookup"><span data-stu-id="a6fde-103">The following table summarizes the methods and properties that you can use to modify an element, its child elements, or its attributes.</span></span>  
  
 <span data-ttu-id="a6fde-104">Les méthodes suivantes modifient un objet <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="a6fde-104">The following methods modify an <xref:System.Xml.Linq.XElement>.</span></span>  
  
|<span data-ttu-id="a6fde-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="a6fde-105">Method</span></span>|<span data-ttu-id="a6fde-106">Description</span><span class="sxs-lookup"><span data-stu-id="a6fde-106">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>|<span data-ttu-id="a6fde-107">Remplace un élément par du code XML analysé.</span><span class="sxs-lookup"><span data-stu-id="a6fde-107">Replaces an element with parsed XML.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|<span data-ttu-id="a6fde-108">Supprime tout le contenu (nœuds enfants et attributs) d'un élément.</span><span class="sxs-lookup"><span data-stu-id="a6fde-108">Removes all content (child nodes and attributes) of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="a6fde-109">Supprime les attributs d'un élément.</span><span class="sxs-lookup"><span data-stu-id="a6fde-109">Removes the attributes of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A?displayProperty=nameWithType>|<span data-ttu-id="a6fde-110">Remplace tout le contenu (nœuds enfants et attributs) d'un élément.</span><span class="sxs-lookup"><span data-stu-id="a6fde-110">Replaces all content (child nodes and attributes) of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="a6fde-111">Remplace les attributs d'un élément.</span><span class="sxs-lookup"><span data-stu-id="a6fde-111">Replaces the attributes of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|<span data-ttu-id="a6fde-112">Définit la valeur d'un attribut.</span><span class="sxs-lookup"><span data-stu-id="a6fde-112">Sets the value of an attribute.</span></span> <span data-ttu-id="a6fde-113">Crée l'attribut s'il n'existe pas.</span><span class="sxs-lookup"><span data-stu-id="a6fde-113">Creates the attribute if it doesn't exist.</span></span> <span data-ttu-id="a6fde-114">Si la valeur est définie à `null`, supprime l'attribut.</span><span class="sxs-lookup"><span data-stu-id="a6fde-114">If the value is set to `null`, removes the attribute.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|<span data-ttu-id="a6fde-115">Définit la valeur d'un élément enfant.</span><span class="sxs-lookup"><span data-stu-id="a6fde-115">Sets the value of a child element.</span></span> <span data-ttu-id="a6fde-116">Crée l'élément s'il n'existe pas.</span><span class="sxs-lookup"><span data-stu-id="a6fde-116">Creates the element if it doesn't exist.</span></span> <span data-ttu-id="a6fde-117">Si la valeur est définie à `null`, supprime l'élément.</span><span class="sxs-lookup"><span data-stu-id="a6fde-117">If the value is set to `null`, removes the element.</span></span>|  
|<xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType>|<span data-ttu-id="a6fde-118">Remplace le contenu (nœuds enfants) d'un élément par le texte spécifié.</span><span class="sxs-lookup"><span data-stu-id="a6fde-118">Replaces the content (child nodes) of an element with the specified text.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetValue%2A?displayProperty=nameWithType>|<span data-ttu-id="a6fde-119">Définit la valeur d'un élément.</span><span class="sxs-lookup"><span data-stu-id="a6fde-119">Sets the value of an element.</span></span>|  
  
 <span data-ttu-id="a6fde-120">Les méthodes suivantes modifient un objet <xref:System.Xml.Linq.XAttribute>.</span><span class="sxs-lookup"><span data-stu-id="a6fde-120">The following methods modify an <xref:System.Xml.Linq.XAttribute>.</span></span>  
  
|<span data-ttu-id="a6fde-121">Méthode</span><span class="sxs-lookup"><span data-stu-id="a6fde-121">Method</span></span>|<span data-ttu-id="a6fde-122">Description</span><span class="sxs-lookup"><span data-stu-id="a6fde-122">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType>|<span data-ttu-id="a6fde-123">Définit la valeur d'un attribut.</span><span class="sxs-lookup"><span data-stu-id="a6fde-123">Sets the value of an attribute.</span></span>|  
|<xref:System.Xml.Linq.XAttribute.SetValue%2A?displayProperty=nameWithType>|<span data-ttu-id="a6fde-124">Définit la valeur d'un attribut.</span><span class="sxs-lookup"><span data-stu-id="a6fde-124">Sets the value of an attribute.</span></span>|  
  
 <span data-ttu-id="a6fde-125">Les méthodes suivantes modifient un objet <xref:System.Xml.Linq.XNode> (y compris un objet <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XDocument>).</span><span class="sxs-lookup"><span data-stu-id="a6fde-125">The following methods modify an <xref:System.Xml.Linq.XNode> (including an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>).</span></span>  
  
|<span data-ttu-id="a6fde-126">Méthode</span><span class="sxs-lookup"><span data-stu-id="a6fde-126">Method</span></span>|<span data-ttu-id="a6fde-127">Description</span><span class="sxs-lookup"><span data-stu-id="a6fde-127">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A?displayProperty=nameWithType>|<span data-ttu-id="a6fde-128">Remplace un nœud par du nouveau contenu.</span><span class="sxs-lookup"><span data-stu-id="a6fde-128">Replaces a node with new content.</span></span>|  
  
 <span data-ttu-id="a6fde-129">Les méthodes suivantes modifient un objet <xref:System.Xml.Linq.XContainer> (un objet <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XDocument>).</span><span class="sxs-lookup"><span data-stu-id="a6fde-129">The following methods modify an <xref:System.Xml.Linq.XContainer> (an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>).</span></span>  
  
|<span data-ttu-id="a6fde-130">Méthode</span><span class="sxs-lookup"><span data-stu-id="a6fde-130">Method</span></span>|<span data-ttu-id="a6fde-131">Description</span><span class="sxs-lookup"><span data-stu-id="a6fde-131">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A?displayProperty=nameWithType>|<span data-ttu-id="a6fde-132">Remplace les nœuds enfants par du nouveau contenu.</span><span class="sxs-lookup"><span data-stu-id="a6fde-132">Replaces the children nodes with new content.</span></span>|  
