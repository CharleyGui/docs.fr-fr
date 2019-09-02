---
title: Déduction de tables
ms.date: 03/30/2017
ms.assetid: 74a288d4-b8e9-4f1a-b2cd-10df92c1ed1f
ms.openlocfilehash: 84cee828f2d3c918a12e449da5b01a3d72d86333
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203518"
---
# <a name="inferring-tables"></a><span data-ttu-id="0d3b4-102">Déduction de tables</span><span class="sxs-lookup"><span data-stu-id="0d3b4-102">Inferring Tables</span></span>
<span data-ttu-id="0d3b4-103">Lors de l'inférence du schéma d'un objet <xref:System.Data.DataSet> à partir d'un document XML, ADO.NET identifie d'abord les éléments XML qui représentent des tables.</span><span class="sxs-lookup"><span data-stu-id="0d3b4-103">When inferring a schema for a <xref:System.Data.DataSet> from an XML document, ADO.NET first determines which XML elements represent tables.</span></span> <span data-ttu-id="0d3b4-104">Les structures XML suivantes aboutissent à une table pour le schéma du **DataSet** :</span><span class="sxs-lookup"><span data-stu-id="0d3b4-104">The following XML structures result in a table for the **DataSet** schema:</span></span>  
  
- <span data-ttu-id="0d3b4-105">éléments avec attributs ;</span><span class="sxs-lookup"><span data-stu-id="0d3b4-105">Elements with attributes</span></span>  
  
- <span data-ttu-id="0d3b4-106">éléments avec éléments enfants ;</span><span class="sxs-lookup"><span data-stu-id="0d3b4-106">Elements with child elements</span></span>  
  
- <span data-ttu-id="0d3b4-107">éléments qui se répètent.</span><span class="sxs-lookup"><span data-stu-id="0d3b4-107">Repeating elements</span></span>  
  
## <a name="elements-with-attributes"></a><span data-ttu-id="0d3b4-108">Éléments avec attributs</span><span class="sxs-lookup"><span data-stu-id="0d3b4-108">Elements with Attributes</span></span>  
 <span data-ttu-id="0d3b4-109">Les éléments contenant des attributs spécifiés donnent des tables déduites.</span><span class="sxs-lookup"><span data-stu-id="0d3b4-109">Elements that have attributes specified in them result in inferred tables.</span></span> <span data-ttu-id="0d3b4-110">Examinons, par exemple, le code XML suivant :</span><span class="sxs-lookup"><span data-stu-id="0d3b4-110">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1"/>  
  <Element1 attr1="value2">Text1</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="0d3b4-111">Le processus d'inférence produit une table nommée « Element1 ».</span><span class="sxs-lookup"><span data-stu-id="0d3b4-111">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="0d3b4-112">**Ensemble** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="0d3b4-112">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="0d3b4-113">**Table :** Element1</span><span class="sxs-lookup"><span data-stu-id="0d3b4-113">**Table:** Element1</span></span>  
  
|<span data-ttu-id="0d3b4-114">attr1</span><span class="sxs-lookup"><span data-stu-id="0d3b4-114">attr1</span></span>|<span data-ttu-id="0d3b4-115">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="0d3b4-115">Element1_Text</span></span>|  
|-----------|--------------------|  
|<span data-ttu-id="0d3b4-116">valeur1</span><span class="sxs-lookup"><span data-stu-id="0d3b4-116">value1</span></span>||  
|<span data-ttu-id="0d3b4-117">valeur2</span><span class="sxs-lookup"><span data-stu-id="0d3b4-117">value2</span></span>|<span data-ttu-id="0d3b4-118">Text1</span><span class="sxs-lookup"><span data-stu-id="0d3b4-118">Text1</span></span>|  
  
## <a name="elements-with-child-elements"></a><span data-ttu-id="0d3b4-119">Éléments avec éléments enfants</span><span class="sxs-lookup"><span data-stu-id="0d3b4-119">Elements with Child Elements</span></span>  
 <span data-ttu-id="0d3b4-120">Les éléments possédant des éléments enfants donnent des tables déduites.</span><span class="sxs-lookup"><span data-stu-id="0d3b4-120">Elements that have child elements result in inferred tables.</span></span> <span data-ttu-id="0d3b4-121">Examinons, par exemple, le code XML suivant :</span><span class="sxs-lookup"><span data-stu-id="0d3b4-121">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
  </Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="0d3b4-122">Le processus d'inférence produit une table nommée « Element1 ».</span><span class="sxs-lookup"><span data-stu-id="0d3b4-122">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="0d3b4-123">**Ensemble** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="0d3b4-123">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="0d3b4-124">**Table :** Element1</span><span class="sxs-lookup"><span data-stu-id="0d3b4-124">**Table:** Element1</span></span>  
  
|<span data-ttu-id="0d3b4-125">ChildElement1</span><span class="sxs-lookup"><span data-stu-id="0d3b4-125">ChildElement1</span></span>|  
|-------------------|  
|<span data-ttu-id="0d3b4-126">Text1</span><span class="sxs-lookup"><span data-stu-id="0d3b4-126">Text1</span></span>|  
  
 <span data-ttu-id="0d3b4-127">L'élément document, ou racine, donne une table déduite s'il comporte des attributs ou des éléments enfants qui sont inférés en tant que colonnes.</span><span class="sxs-lookup"><span data-stu-id="0d3b4-127">The document, or root, element result in an inferred table if it has attributes or child elements that are inferred as columns.</span></span> <span data-ttu-id="0d3b4-128">Si l’élément de document n’a pas d’attributs ni d’éléments enfants qui seraient déduits en tant que colonnes, l’élément est déduit en tant que **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="0d3b4-128">If the document element has no attributes and no child elements that would be inferred as columns, the element is inferred as a **DataSet**.</span></span> <span data-ttu-id="0d3b4-129">Examinons, par exemple, le code XML suivant :</span><span class="sxs-lookup"><span data-stu-id="0d3b4-129">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element2>Text2</Element2>  
</DocumentElement>  
```  
  
 <span data-ttu-id="0d3b4-130">Le processus d'inférence produit une table nommée « DocumentElement ».</span><span class="sxs-lookup"><span data-stu-id="0d3b4-130">The inference process produces a table named "DocumentElement."</span></span>  
  
 <span data-ttu-id="0d3b4-131">**Ensemble** NewDataSet</span><span class="sxs-lookup"><span data-stu-id="0d3b4-131">**DataSet:** NewDataSet</span></span>  
  
 <span data-ttu-id="0d3b4-132">**Table :** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="0d3b4-132">**Table:** DocumentElement</span></span>  
  
|<span data-ttu-id="0d3b4-133">Element1</span><span class="sxs-lookup"><span data-stu-id="0d3b4-133">Element1</span></span>|<span data-ttu-id="0d3b4-134">Element2</span><span class="sxs-lookup"><span data-stu-id="0d3b4-134">Element2</span></span>|  
|--------------|--------------|  
|<span data-ttu-id="0d3b4-135">Text1</span><span class="sxs-lookup"><span data-stu-id="0d3b4-135">Text1</span></span>|<span data-ttu-id="0d3b4-136">Text2</span><span class="sxs-lookup"><span data-stu-id="0d3b4-136">Text2</span></span>|  
  
 <span data-ttu-id="0d3b4-137">Examinons également le code XML suivant :</span><span class="sxs-lookup"><span data-stu-id="0d3b4-137">Alternatively, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 <span data-ttu-id="0d3b4-138">Le processus d’inférence produit un **DataSet** nommé «DocumentElement» qui contient une table nommée «Element1».</span><span class="sxs-lookup"><span data-stu-id="0d3b4-138">The inference process produces a **DataSet** named "DocumentElement" that contains a table named "Element1."</span></span>  
  
 <span data-ttu-id="0d3b4-139">**Ensemble** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="0d3b4-139">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="0d3b4-140">**Table :** Element1</span><span class="sxs-lookup"><span data-stu-id="0d3b4-140">**Table:** Element1</span></span>  
  
|<span data-ttu-id="0d3b4-141">attr1</span><span class="sxs-lookup"><span data-stu-id="0d3b4-141">attr1</span></span>|<span data-ttu-id="0d3b4-142">attr2</span><span class="sxs-lookup"><span data-stu-id="0d3b4-142">attr2</span></span>|  
|-----------|-----------|  
|<span data-ttu-id="0d3b4-143">valeur1</span><span class="sxs-lookup"><span data-stu-id="0d3b4-143">value1</span></span>|<span data-ttu-id="0d3b4-144">valeur2</span><span class="sxs-lookup"><span data-stu-id="0d3b4-144">value2</span></span>|  
  
## <a name="repeating-elements"></a><span data-ttu-id="0d3b4-145">Éléments qui se répètent</span><span class="sxs-lookup"><span data-stu-id="0d3b4-145">Repeating Elements</span></span>  
 <span data-ttu-id="0d3b4-146">Les éléments qui se répètent donnent une seule table déduite.</span><span class="sxs-lookup"><span data-stu-id="0d3b4-146">Elements that repeat result in a single inferred table.</span></span> <span data-ttu-id="0d3b4-147">Examinons, par exemple, le code XML suivant :</span><span class="sxs-lookup"><span data-stu-id="0d3b4-147">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="0d3b4-148">Le processus d'inférence produit une table nommée « Element1 ».</span><span class="sxs-lookup"><span data-stu-id="0d3b4-148">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="0d3b4-149">**Ensemble** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="0d3b4-149">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="0d3b4-150">**Table :** Element1</span><span class="sxs-lookup"><span data-stu-id="0d3b4-150">**Table:** Element1</span></span>  
  
|<span data-ttu-id="0d3b4-151">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="0d3b4-151">Element1_Text</span></span>|  
|--------------------|  
|<span data-ttu-id="0d3b4-152">Text1</span><span class="sxs-lookup"><span data-stu-id="0d3b4-152">Text1</span></span>|  
|<span data-ttu-id="0d3b4-153">Text2</span><span class="sxs-lookup"><span data-stu-id="0d3b4-153">Text2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0d3b4-154">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0d3b4-154">See also</span></span>

- [<span data-ttu-id="0d3b4-155">Inférence de la structure relationnelle d’un DataSet à partir de XML</span><span class="sxs-lookup"><span data-stu-id="0d3b4-155">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="0d3b4-156">Chargement d’un DataSet à partir de XML</span><span class="sxs-lookup"><span data-stu-id="0d3b4-156">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)
- [<span data-ttu-id="0d3b4-157">Chargement des informations de schéma de DataSet à partir de XML</span><span class="sxs-lookup"><span data-stu-id="0d3b4-157">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="0d3b4-158">Utilisation de XML dans un DataSet</span><span class="sxs-lookup"><span data-stu-id="0d3b4-158">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="0d3b4-159">DataSets, DataTables et DataViews</span><span class="sxs-lookup"><span data-stu-id="0d3b4-159">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="0d3b4-160">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="0d3b4-160">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
