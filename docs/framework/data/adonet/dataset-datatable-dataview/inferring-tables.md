---
title: Déduction de tables
ms.date: 03/30/2017
ms.assetid: 74a288d4-b8e9-4f1a-b2cd-10df92c1ed1f
ms.openlocfilehash: 4a3d7b239dbc405cf2acae967b5be401dc772e38
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177551"
---
# <a name="inferring-tables"></a><span data-ttu-id="dd4df-102">Déduction de tables</span><span class="sxs-lookup"><span data-stu-id="dd4df-102">Inferring Tables</span></span>

<span data-ttu-id="dd4df-103">Lors de l'inférence du schéma d'un objet <xref:System.Data.DataSet> à partir d'un document XML, ADO.NET identifie d'abord les éléments XML qui représentent des tables.</span><span class="sxs-lookup"><span data-stu-id="dd4df-103">When inferring a schema for a <xref:System.Data.DataSet> from an XML document, ADO.NET first determines which XML elements represent tables.</span></span> <span data-ttu-id="dd4df-104">Les structures XML suivantes aboutissent à une table pour le schéma du **DataSet** :</span><span class="sxs-lookup"><span data-stu-id="dd4df-104">The following XML structures result in a table for the **DataSet** schema:</span></span>  
  
- <span data-ttu-id="dd4df-105">éléments avec attributs ;</span><span class="sxs-lookup"><span data-stu-id="dd4df-105">Elements with attributes</span></span>  
  
- <span data-ttu-id="dd4df-106">éléments avec éléments enfants ;</span><span class="sxs-lookup"><span data-stu-id="dd4df-106">Elements with child elements</span></span>  
  
- <span data-ttu-id="dd4df-107">éléments qui se répètent.</span><span class="sxs-lookup"><span data-stu-id="dd4df-107">Repeating elements</span></span>  
  
## <a name="elements-with-attributes"></a><span data-ttu-id="dd4df-108">Éléments avec attributs</span><span class="sxs-lookup"><span data-stu-id="dd4df-108">Elements with Attributes</span></span>  

 <span data-ttu-id="dd4df-109">Les éléments contenant des attributs spécifiés donnent des tables déduites.</span><span class="sxs-lookup"><span data-stu-id="dd4df-109">Elements that have attributes specified in them result in inferred tables.</span></span> <span data-ttu-id="dd4df-110">Examinons, par exemple, le code XML suivant :</span><span class="sxs-lookup"><span data-stu-id="dd4df-110">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1"/>  
  <Element1 attr1="value2">Text1</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="dd4df-111">Le processus d'inférence produit une table nommée « Element1 ».</span><span class="sxs-lookup"><span data-stu-id="dd4df-111">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="dd4df-112">**Jeu de données :** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="dd4df-112">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="dd4df-113">**Table :** Élément1</span><span class="sxs-lookup"><span data-stu-id="dd4df-113">**Table:** Element1</span></span>  
  
|<span data-ttu-id="dd4df-114">attr1</span><span class="sxs-lookup"><span data-stu-id="dd4df-114">attr1</span></span>|<span data-ttu-id="dd4df-115">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="dd4df-115">Element1_Text</span></span>|  
|-----------|--------------------|  
|<span data-ttu-id="dd4df-116">valeur1</span><span class="sxs-lookup"><span data-stu-id="dd4df-116">value1</span></span>||  
|<span data-ttu-id="dd4df-117">valeur2</span><span class="sxs-lookup"><span data-stu-id="dd4df-117">value2</span></span>|<span data-ttu-id="dd4df-118">Text1</span><span class="sxs-lookup"><span data-stu-id="dd4df-118">Text1</span></span>|  
  
## <a name="elements-with-child-elements"></a><span data-ttu-id="dd4df-119">Éléments avec éléments enfants</span><span class="sxs-lookup"><span data-stu-id="dd4df-119">Elements with Child Elements</span></span>  

 <span data-ttu-id="dd4df-120">Les éléments possédant des éléments enfants donnent des tables déduites.</span><span class="sxs-lookup"><span data-stu-id="dd4df-120">Elements that have child elements result in inferred tables.</span></span> <span data-ttu-id="dd4df-121">Examinons, par exemple, le code XML suivant :</span><span class="sxs-lookup"><span data-stu-id="dd4df-121">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
  </Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="dd4df-122">Le processus d'inférence produit une table nommée « Element1 ».</span><span class="sxs-lookup"><span data-stu-id="dd4df-122">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="dd4df-123">**Jeu de données :** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="dd4df-123">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="dd4df-124">**Table :** Élément1</span><span class="sxs-lookup"><span data-stu-id="dd4df-124">**Table:** Element1</span></span>  
  
|<span data-ttu-id="dd4df-125">ChildElement1</span><span class="sxs-lookup"><span data-stu-id="dd4df-125">ChildElement1</span></span>|  
|-------------------|  
|<span data-ttu-id="dd4df-126">Text1</span><span class="sxs-lookup"><span data-stu-id="dd4df-126">Text1</span></span>|  
  
 <span data-ttu-id="dd4df-127">L'élément document, ou racine, donne une table déduite s'il comporte des attributs ou des éléments enfants qui sont inférés en tant que colonnes.</span><span class="sxs-lookup"><span data-stu-id="dd4df-127">The document, or root, element result in an inferred table if it has attributes or child elements that are inferred as columns.</span></span> <span data-ttu-id="dd4df-128">Si l’élément de document n’a pas d’attributs ni d’éléments enfants qui seraient déduits en tant que colonnes, l’élément est déduit en tant que **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="dd4df-128">If the document element has no attributes and no child elements that would be inferred as columns, the element is inferred as a **DataSet**.</span></span> <span data-ttu-id="dd4df-129">Examinons, par exemple, le code XML suivant :</span><span class="sxs-lookup"><span data-stu-id="dd4df-129">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element2>Text2</Element2>  
</DocumentElement>  
```  
  
 <span data-ttu-id="dd4df-130">Le processus d'inférence produit une table nommée « DocumentElement ».</span><span class="sxs-lookup"><span data-stu-id="dd4df-130">The inference process produces a table named "DocumentElement."</span></span>  
  
 <span data-ttu-id="dd4df-131">**Jeu de données :** NewDataSet</span><span class="sxs-lookup"><span data-stu-id="dd4df-131">**DataSet:** NewDataSet</span></span>  
  
 <span data-ttu-id="dd4df-132">**Table :** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="dd4df-132">**Table:** DocumentElement</span></span>  
  
|<span data-ttu-id="dd4df-133">Element1</span><span class="sxs-lookup"><span data-stu-id="dd4df-133">Element1</span></span>|<span data-ttu-id="dd4df-134">Element2</span><span class="sxs-lookup"><span data-stu-id="dd4df-134">Element2</span></span>|  
|--------------|--------------|  
|<span data-ttu-id="dd4df-135">Text1</span><span class="sxs-lookup"><span data-stu-id="dd4df-135">Text1</span></span>|<span data-ttu-id="dd4df-136">Text2</span><span class="sxs-lookup"><span data-stu-id="dd4df-136">Text2</span></span>|  
  
 <span data-ttu-id="dd4df-137">Examinons également le code XML suivant :</span><span class="sxs-lookup"><span data-stu-id="dd4df-137">Alternatively, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 <span data-ttu-id="dd4df-138">Le processus d’inférence produit un **DataSet** nommé « DocumentElement » qui contient une table nommée « Element1 ».</span><span class="sxs-lookup"><span data-stu-id="dd4df-138">The inference process produces a **DataSet** named "DocumentElement" that contains a table named "Element1."</span></span>  
  
 <span data-ttu-id="dd4df-139">**Jeu de données :** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="dd4df-139">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="dd4df-140">**Table :** Élément1</span><span class="sxs-lookup"><span data-stu-id="dd4df-140">**Table:** Element1</span></span>  
  
|<span data-ttu-id="dd4df-141">attr1</span><span class="sxs-lookup"><span data-stu-id="dd4df-141">attr1</span></span>|<span data-ttu-id="dd4df-142">attr2</span><span class="sxs-lookup"><span data-stu-id="dd4df-142">attr2</span></span>|  
|-----------|-----------|  
|<span data-ttu-id="dd4df-143">valeur1</span><span class="sxs-lookup"><span data-stu-id="dd4df-143">value1</span></span>|<span data-ttu-id="dd4df-144">valeur2</span><span class="sxs-lookup"><span data-stu-id="dd4df-144">value2</span></span>|  
  
## <a name="repeating-elements"></a><span data-ttu-id="dd4df-145">Éléments qui se répètent</span><span class="sxs-lookup"><span data-stu-id="dd4df-145">Repeating Elements</span></span>  

 <span data-ttu-id="dd4df-146">Les éléments qui se répètent donnent une seule table déduite.</span><span class="sxs-lookup"><span data-stu-id="dd4df-146">Elements that repeat result in a single inferred table.</span></span> <span data-ttu-id="dd4df-147">Examinons, par exemple, le code XML suivant :</span><span class="sxs-lookup"><span data-stu-id="dd4df-147">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="dd4df-148">Le processus d'inférence produit une table nommée « Element1 ».</span><span class="sxs-lookup"><span data-stu-id="dd4df-148">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="dd4df-149">**Jeu de données :** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="dd4df-149">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="dd4df-150">**Table :** Élément1</span><span class="sxs-lookup"><span data-stu-id="dd4df-150">**Table:** Element1</span></span>  
  
|<span data-ttu-id="dd4df-151">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="dd4df-151">Element1_Text</span></span>|  
|--------------------|  
|<span data-ttu-id="dd4df-152">Text1</span><span class="sxs-lookup"><span data-stu-id="dd4df-152">Text1</span></span>|  
|<span data-ttu-id="dd4df-153">Text2</span><span class="sxs-lookup"><span data-stu-id="dd4df-153">Text2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dd4df-154">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dd4df-154">See also</span></span>

- [<span data-ttu-id="dd4df-155">Déduction de la structure relationnelle des DataSet à partir de XML</span><span class="sxs-lookup"><span data-stu-id="dd4df-155">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="dd4df-156">Chargement d'un DataSet à partir de XML</span><span class="sxs-lookup"><span data-stu-id="dd4df-156">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)
- [<span data-ttu-id="dd4df-157">Chargement des informations de schéma de DataSet à partir de XML</span><span class="sxs-lookup"><span data-stu-id="dd4df-157">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="dd4df-158">Utilisation de XML dans un DataSet</span><span class="sxs-lookup"><span data-stu-id="dd4df-158">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="dd4df-159">DataSets, DataTables et DataViews</span><span class="sxs-lookup"><span data-stu-id="dd4df-159">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="dd4df-160">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="dd4df-160">ADO.NET Overview</span></span>](../ado-net-overview.md)
