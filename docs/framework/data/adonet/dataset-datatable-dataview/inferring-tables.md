---
title: Déduction de tables
ms.date: 03/30/2017
ms.assetid: 74a288d4-b8e9-4f1a-b2cd-10df92c1ed1f
ms.openlocfilehash: 52ffd3fe90eb491dd01acf8538276cc828fdb309
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784494"
---
# <a name="inferring-tables"></a><span data-ttu-id="a7f30-102">Déduction de tables</span><span class="sxs-lookup"><span data-stu-id="a7f30-102">Inferring Tables</span></span>
<span data-ttu-id="a7f30-103">Lors de l'inférence du schéma d'un objet <xref:System.Data.DataSet> à partir d'un document XML, ADO.NET identifie d'abord les éléments XML qui représentent des tables.</span><span class="sxs-lookup"><span data-stu-id="a7f30-103">When inferring a schema for a <xref:System.Data.DataSet> from an XML document, ADO.NET first determines which XML elements represent tables.</span></span> <span data-ttu-id="a7f30-104">Les structures XML suivantes aboutissent à une table pour le schéma du **DataSet** :</span><span class="sxs-lookup"><span data-stu-id="a7f30-104">The following XML structures result in a table for the **DataSet** schema:</span></span>  
  
- <span data-ttu-id="a7f30-105">éléments avec attributs ;</span><span class="sxs-lookup"><span data-stu-id="a7f30-105">Elements with attributes</span></span>  
  
- <span data-ttu-id="a7f30-106">éléments avec éléments enfants ;</span><span class="sxs-lookup"><span data-stu-id="a7f30-106">Elements with child elements</span></span>  
  
- <span data-ttu-id="a7f30-107">éléments qui se répètent.</span><span class="sxs-lookup"><span data-stu-id="a7f30-107">Repeating elements</span></span>  
  
## <a name="elements-with-attributes"></a><span data-ttu-id="a7f30-108">Éléments avec attributs</span><span class="sxs-lookup"><span data-stu-id="a7f30-108">Elements with Attributes</span></span>  
 <span data-ttu-id="a7f30-109">Les éléments contenant des attributs spécifiés donnent des tables déduites.</span><span class="sxs-lookup"><span data-stu-id="a7f30-109">Elements that have attributes specified in them result in inferred tables.</span></span> <span data-ttu-id="a7f30-110">Examinons, par exemple, le code XML suivant :</span><span class="sxs-lookup"><span data-stu-id="a7f30-110">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1"/>  
  <Element1 attr1="value2">Text1</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="a7f30-111">Le processus d'inférence produit une table nommée « Element1 ».</span><span class="sxs-lookup"><span data-stu-id="a7f30-111">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="a7f30-112">**Ensemble** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="a7f30-112">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="a7f30-113">**Table :** Element1</span><span class="sxs-lookup"><span data-stu-id="a7f30-113">**Table:** Element1</span></span>  
  
|<span data-ttu-id="a7f30-114">attr1</span><span class="sxs-lookup"><span data-stu-id="a7f30-114">attr1</span></span>|<span data-ttu-id="a7f30-115">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="a7f30-115">Element1_Text</span></span>|  
|-----------|--------------------|  
|<span data-ttu-id="a7f30-116">valeur1</span><span class="sxs-lookup"><span data-stu-id="a7f30-116">value1</span></span>||  
|<span data-ttu-id="a7f30-117">valeur2</span><span class="sxs-lookup"><span data-stu-id="a7f30-117">value2</span></span>|<span data-ttu-id="a7f30-118">Text1</span><span class="sxs-lookup"><span data-stu-id="a7f30-118">Text1</span></span>|  
  
## <a name="elements-with-child-elements"></a><span data-ttu-id="a7f30-119">Éléments avec éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a7f30-119">Elements with Child Elements</span></span>  
 <span data-ttu-id="a7f30-120">Les éléments possédant des éléments enfants donnent des tables déduites.</span><span class="sxs-lookup"><span data-stu-id="a7f30-120">Elements that have child elements result in inferred tables.</span></span> <span data-ttu-id="a7f30-121">Examinons, par exemple, le code XML suivant :</span><span class="sxs-lookup"><span data-stu-id="a7f30-121">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
  </Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="a7f30-122">Le processus d'inférence produit une table nommée « Element1 ».</span><span class="sxs-lookup"><span data-stu-id="a7f30-122">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="a7f30-123">**Ensemble** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="a7f30-123">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="a7f30-124">**Table :** Element1</span><span class="sxs-lookup"><span data-stu-id="a7f30-124">**Table:** Element1</span></span>  
  
|<span data-ttu-id="a7f30-125">ChildElement1</span><span class="sxs-lookup"><span data-stu-id="a7f30-125">ChildElement1</span></span>|  
|-------------------|  
|<span data-ttu-id="a7f30-126">Text1</span><span class="sxs-lookup"><span data-stu-id="a7f30-126">Text1</span></span>|  
  
 <span data-ttu-id="a7f30-127">L'élément document, ou racine, donne une table déduite s'il comporte des attributs ou des éléments enfants qui sont inférés en tant que colonnes.</span><span class="sxs-lookup"><span data-stu-id="a7f30-127">The document, or root, element result in an inferred table if it has attributes or child elements that are inferred as columns.</span></span> <span data-ttu-id="a7f30-128">Si l’élément de document n’a pas d’attributs ni d’éléments enfants qui seraient déduits en tant que colonnes, l’élément est déduit en tant que **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="a7f30-128">If the document element has no attributes and no child elements that would be inferred as columns, the element is inferred as a **DataSet**.</span></span> <span data-ttu-id="a7f30-129">Examinons, par exemple, le code XML suivant :</span><span class="sxs-lookup"><span data-stu-id="a7f30-129">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element2>Text2</Element2>  
</DocumentElement>  
```  
  
 <span data-ttu-id="a7f30-130">Le processus d'inférence produit une table nommée « DocumentElement ».</span><span class="sxs-lookup"><span data-stu-id="a7f30-130">The inference process produces a table named "DocumentElement."</span></span>  
  
 <span data-ttu-id="a7f30-131">**Ensemble** NewDataSet</span><span class="sxs-lookup"><span data-stu-id="a7f30-131">**DataSet:** NewDataSet</span></span>  
  
 <span data-ttu-id="a7f30-132">**Table :** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="a7f30-132">**Table:** DocumentElement</span></span>  
  
|<span data-ttu-id="a7f30-133">Element1</span><span class="sxs-lookup"><span data-stu-id="a7f30-133">Element1</span></span>|<span data-ttu-id="a7f30-134">Element2</span><span class="sxs-lookup"><span data-stu-id="a7f30-134">Element2</span></span>|  
|--------------|--------------|  
|<span data-ttu-id="a7f30-135">Text1</span><span class="sxs-lookup"><span data-stu-id="a7f30-135">Text1</span></span>|<span data-ttu-id="a7f30-136">Text2</span><span class="sxs-lookup"><span data-stu-id="a7f30-136">Text2</span></span>|  
  
 <span data-ttu-id="a7f30-137">Examinons également le code XML suivant :</span><span class="sxs-lookup"><span data-stu-id="a7f30-137">Alternatively, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 <span data-ttu-id="a7f30-138">Le processus d’inférence produit un **DataSet** nommé « DocumentElement » qui contient une table nommée « Element1 ».</span><span class="sxs-lookup"><span data-stu-id="a7f30-138">The inference process produces a **DataSet** named "DocumentElement" that contains a table named "Element1."</span></span>  
  
 <span data-ttu-id="a7f30-139">**Ensemble** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="a7f30-139">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="a7f30-140">**Table :** Element1</span><span class="sxs-lookup"><span data-stu-id="a7f30-140">**Table:** Element1</span></span>  
  
|<span data-ttu-id="a7f30-141">attr1</span><span class="sxs-lookup"><span data-stu-id="a7f30-141">attr1</span></span>|<span data-ttu-id="a7f30-142">attr2</span><span class="sxs-lookup"><span data-stu-id="a7f30-142">attr2</span></span>|  
|-----------|-----------|  
|<span data-ttu-id="a7f30-143">valeur1</span><span class="sxs-lookup"><span data-stu-id="a7f30-143">value1</span></span>|<span data-ttu-id="a7f30-144">valeur2</span><span class="sxs-lookup"><span data-stu-id="a7f30-144">value2</span></span>|  
  
## <a name="repeating-elements"></a><span data-ttu-id="a7f30-145">Éléments qui se répètent</span><span class="sxs-lookup"><span data-stu-id="a7f30-145">Repeating Elements</span></span>  
 <span data-ttu-id="a7f30-146">Les éléments qui se répètent donnent une seule table déduite.</span><span class="sxs-lookup"><span data-stu-id="a7f30-146">Elements that repeat result in a single inferred table.</span></span> <span data-ttu-id="a7f30-147">Examinons, par exemple, le code XML suivant :</span><span class="sxs-lookup"><span data-stu-id="a7f30-147">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="a7f30-148">Le processus d'inférence produit une table nommée « Element1 ».</span><span class="sxs-lookup"><span data-stu-id="a7f30-148">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="a7f30-149">**Ensemble** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="a7f30-149">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="a7f30-150">**Table :** Element1</span><span class="sxs-lookup"><span data-stu-id="a7f30-150">**Table:** Element1</span></span>  
  
|<span data-ttu-id="a7f30-151">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="a7f30-151">Element1_Text</span></span>|  
|--------------------|  
|<span data-ttu-id="a7f30-152">Text1</span><span class="sxs-lookup"><span data-stu-id="a7f30-152">Text1</span></span>|  
|<span data-ttu-id="a7f30-153">Text2</span><span class="sxs-lookup"><span data-stu-id="a7f30-153">Text2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a7f30-154">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a7f30-154">See also</span></span>

- [<span data-ttu-id="a7f30-155">Inférence de la structure relationnelle d’un DataSet à partir de XML</span><span class="sxs-lookup"><span data-stu-id="a7f30-155">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="a7f30-156">Chargement d’un DataSet à partir de XML</span><span class="sxs-lookup"><span data-stu-id="a7f30-156">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)
- [<span data-ttu-id="a7f30-157">Chargement des informations de schéma de DataSet à partir de XML</span><span class="sxs-lookup"><span data-stu-id="a7f30-157">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="a7f30-158">Utilisation de XML dans un DataSet</span><span class="sxs-lookup"><span data-stu-id="a7f30-158">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="a7f30-159">DataSets, DataTables et DataViews</span><span class="sxs-lookup"><span data-stu-id="a7f30-159">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="a7f30-160">Vue d’ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a7f30-160">ADO.NET Overview</span></span>](../ado-net-overview.md)
