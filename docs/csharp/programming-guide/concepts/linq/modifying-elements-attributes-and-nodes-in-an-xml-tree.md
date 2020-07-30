---
title: Modification d’éléments, d’attributs et de nœuds dans une arborescence XML
description: En savoir plus sur les méthodes et les propriétés que vous pouvez utiliser pour modifier un élément, ses nœuds enfants ou ses attributs.
ms.date: 07/20/2015
ms.assetid: 0ed22e4e-4c6b-4eb1-b0eb-06685efd8c33
ms.openlocfilehash: bfff882dc57a4f6f4b228563ac923122097d88d0
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303164"
---
# <a name="modifying-elements-attributes-and-nodes-in-an-xml-tree"></a><span data-ttu-id="600a7-103">Modification d’éléments, d’attributs et de nœuds dans une arborescence XML</span><span class="sxs-lookup"><span data-stu-id="600a7-103">Modifying Elements, Attributes, and Nodes in an XML Tree</span></span>
<span data-ttu-id="600a7-104">Le tableau suivant résume les méthodes et propriétés que vous pouvez utiliser pour modifier un élément, ses éléments enfants ou ses attributs.</span><span class="sxs-lookup"><span data-stu-id="600a7-104">The following table summarizes the methods and properties that you can use to modify an element, its child elements, or its attributes.</span></span>  
  
 <span data-ttu-id="600a7-105">Les méthodes suivantes modifient un objet <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="600a7-105">The following methods modify an <xref:System.Xml.Linq.XElement>.</span></span>  
  
|<span data-ttu-id="600a7-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="600a7-106">Method</span></span>|<span data-ttu-id="600a7-107">Description</span><span class="sxs-lookup"><span data-stu-id="600a7-107">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>|<span data-ttu-id="600a7-108">Remplace un élément par du code XML analysé.</span><span class="sxs-lookup"><span data-stu-id="600a7-108">Replaces an element with parsed XML.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|<span data-ttu-id="600a7-109">Supprime tout le contenu (nœuds enfants et attributs) d'un élément.</span><span class="sxs-lookup"><span data-stu-id="600a7-109">Removes all content (child nodes and attributes) of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="600a7-110">Supprime les attributs d'un élément.</span><span class="sxs-lookup"><span data-stu-id="600a7-110">Removes the attributes of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A?displayProperty=nameWithType>|<span data-ttu-id="600a7-111">Remplace tout le contenu (nœuds enfants et attributs) d'un élément.</span><span class="sxs-lookup"><span data-stu-id="600a7-111">Replaces all content (child nodes and attributes) of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="600a7-112">Remplace les attributs d'un élément.</span><span class="sxs-lookup"><span data-stu-id="600a7-112">Replaces the attributes of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|<span data-ttu-id="600a7-113">Définit la valeur d'un attribut.</span><span class="sxs-lookup"><span data-stu-id="600a7-113">Sets the value of an attribute.</span></span> <span data-ttu-id="600a7-114">Crée l'attribut s'il n'existe pas.</span><span class="sxs-lookup"><span data-stu-id="600a7-114">Creates the attribute if it doesn't exist.</span></span> <span data-ttu-id="600a7-115">Si la valeur est définie à `null`, supprime l'attribut.</span><span class="sxs-lookup"><span data-stu-id="600a7-115">If the value is set to `null`, removes the attribute.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|<span data-ttu-id="600a7-116">Définit la valeur d'un élément enfant.</span><span class="sxs-lookup"><span data-stu-id="600a7-116">Sets the value of a child element.</span></span> <span data-ttu-id="600a7-117">Crée l'élément s'il n'existe pas.</span><span class="sxs-lookup"><span data-stu-id="600a7-117">Creates the element if it doesn't exist.</span></span> <span data-ttu-id="600a7-118">Si la valeur est définie à `null`, supprime l'élément.</span><span class="sxs-lookup"><span data-stu-id="600a7-118">If the value is set to `null`, removes the element.</span></span>|  
|<xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType>|<span data-ttu-id="600a7-119">Remplace le contenu (nœuds enfants) d'un élément par le texte spécifié.</span><span class="sxs-lookup"><span data-stu-id="600a7-119">Replaces the content (child nodes) of an element with the specified text.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetValue%2A?displayProperty=nameWithType>|<span data-ttu-id="600a7-120">Définit la valeur d'un élément.</span><span class="sxs-lookup"><span data-stu-id="600a7-120">Sets the value of an element.</span></span>|  
  
 <span data-ttu-id="600a7-121">Les méthodes suivantes modifient un objet <xref:System.Xml.Linq.XAttribute>.</span><span class="sxs-lookup"><span data-stu-id="600a7-121">The following methods modify an <xref:System.Xml.Linq.XAttribute>.</span></span>  
  
|<span data-ttu-id="600a7-122">Méthode</span><span class="sxs-lookup"><span data-stu-id="600a7-122">Method</span></span>|<span data-ttu-id="600a7-123">Description</span><span class="sxs-lookup"><span data-stu-id="600a7-123">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType>|<span data-ttu-id="600a7-124">Définit la valeur d'un attribut.</span><span class="sxs-lookup"><span data-stu-id="600a7-124">Sets the value of an attribute.</span></span>|  
|<xref:System.Xml.Linq.XAttribute.SetValue%2A?displayProperty=nameWithType>|<span data-ttu-id="600a7-125">Définit la valeur d'un attribut.</span><span class="sxs-lookup"><span data-stu-id="600a7-125">Sets the value of an attribute.</span></span>|  
  
 <span data-ttu-id="600a7-126">Les méthodes suivantes modifient un objet <xref:System.Xml.Linq.XNode> (y compris un objet <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XDocument>).</span><span class="sxs-lookup"><span data-stu-id="600a7-126">The following methods modify an <xref:System.Xml.Linq.XNode> (including an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>).</span></span>  
  
|<span data-ttu-id="600a7-127">Méthode</span><span class="sxs-lookup"><span data-stu-id="600a7-127">Method</span></span>|<span data-ttu-id="600a7-128">Description</span><span class="sxs-lookup"><span data-stu-id="600a7-128">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A?displayProperty=nameWithType>|<span data-ttu-id="600a7-129">Remplace un nœud par du nouveau contenu.</span><span class="sxs-lookup"><span data-stu-id="600a7-129">Replaces a node with new content.</span></span>|  
  
 <span data-ttu-id="600a7-130">Les méthodes suivantes modifient un objet <xref:System.Xml.Linq.XContainer> (un objet <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XDocument>).</span><span class="sxs-lookup"><span data-stu-id="600a7-130">The following methods modify an <xref:System.Xml.Linq.XContainer> (an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>).</span></span>  
  
|<span data-ttu-id="600a7-131">Méthode</span><span class="sxs-lookup"><span data-stu-id="600a7-131">Method</span></span>|<span data-ttu-id="600a7-132">Description</span><span class="sxs-lookup"><span data-stu-id="600a7-132">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A?displayProperty=nameWithType>|<span data-ttu-id="600a7-133">Remplace les nœuds enfants par du nouveau contenu.</span><span class="sxs-lookup"><span data-stu-id="600a7-133">Replaces the children nodes with new content.</span></span>|  
