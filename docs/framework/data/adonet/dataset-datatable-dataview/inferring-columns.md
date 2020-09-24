---
title: Déduction des colonnes
ms.date: 03/30/2017
ms.assetid: 0e022699-c922-454c-93e2-957dd7e7247a
ms.openlocfilehash: 45d27b78b5d83d333c16192e172e7b7e3dd88c10
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164699"
---
# <a name="inferring-columns"></a><span data-ttu-id="bec20-102">Déduction des colonnes</span><span class="sxs-lookup"><span data-stu-id="bec20-102">Inferring Columns</span></span>

<span data-ttu-id="bec20-103">Après avoir déterminé les éléments à déduire en tant que tables pour un objet <xref:System.Data.DataSet> à partir d'un document XML, ADO.NET déduit les colonnes pour ces tables.</span><span class="sxs-lookup"><span data-stu-id="bec20-103">After ADO.NET has determined from an XML document which elements to infer as tables for a <xref:System.Data.DataSet>, it then infers the columns for those tables.</span></span> <span data-ttu-id="bec20-104">ADO.NET 2,0 a introduit un nouveau moteur d’inférence de schéma qui déduit un type de données fortement typé pour chaque élément **simpleType** .</span><span class="sxs-lookup"><span data-stu-id="bec20-104">ADO.NET 2.0 introduced a new schema inference engine that infers a strongly typed data type for each **simpleType** element.</span></span> <span data-ttu-id="bec20-105">Dans les versions précédentes, le type de données d’un élément **simpleType** inféré était toujours **xsd : String**.</span><span class="sxs-lookup"><span data-stu-id="bec20-105">In previous versions, the data type of an inferred **simpleType** element was always **xsd:string**.</span></span>  
  
## <a name="migration-and-backward-compatibility"></a><span data-ttu-id="bec20-106">Migration et compatibilité ascendante</span><span class="sxs-lookup"><span data-stu-id="bec20-106">Migration and Backward Compatibility</span></span>  

 <span data-ttu-id="bec20-107">La méthode **ReadXml** accepte un argument de type **InferSchema**.</span><span class="sxs-lookup"><span data-stu-id="bec20-107">The **ReadXml** method takes an argument of type **InferSchema**.</span></span> <span data-ttu-id="bec20-108">Cet argument vous permet de spécifier un comportement d’inférence compatible avec les versions précédentes.</span><span class="sxs-lookup"><span data-stu-id="bec20-108">This argument allows you to specify inference behavior compatible with previous versions.</span></span> <span data-ttu-id="bec20-109">Les valeurs disponibles pour l’énumération **InferSchema** sont indiquées dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="bec20-109">The available values for the **InferSchema** enumeration are shown in the following table.</span></span>  
  
 <xref:System.Data.XmlReadMode.InferSchema>  
 <span data-ttu-id="bec20-110">Assure la compatibilité ascendante en déduisant toujours un type simple comme l'objet <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="bec20-110">Provides backward compatibility by always inferring a simple type as <xref:System.String>.</span></span>  
  
 <xref:System.Data.XmlReadMode.InferTypedSchema>  
 <span data-ttu-id="bec20-111">Déduit un type de données fortement typées.</span><span class="sxs-lookup"><span data-stu-id="bec20-111">Infers a strongly typed data type.</span></span> <span data-ttu-id="bec20-112">Lève une exception s'il est utilisé avec un objet <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="bec20-112">Throws an exception if used with a <xref:System.Data.DataTable>.</span></span>  
  
 <xref:System.Data.XmlReadMode.IgnoreSchema>  
 <span data-ttu-id="bec20-113">Ignore tout schéma inline et lit les données dans le schéma <xref:System.Data.DataSet> existant.</span><span class="sxs-lookup"><span data-stu-id="bec20-113">Ignores any inline schema and reads data into the existing <xref:System.Data.DataSet> schema.</span></span>  
  
## <a name="attributes"></a><span data-ttu-id="bec20-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="bec20-114">Attributes</span></span>  

 <span data-ttu-id="bec20-115">Comme défini dans l' [inférence des tables](inferring-tables.md), un élément avec des attributs est déduit en tant que table.</span><span class="sxs-lookup"><span data-stu-id="bec20-115">As defined in [Inferring Tables](inferring-tables.md), an element with attributes will be inferred as a table.</span></span> <span data-ttu-id="bec20-116">Les attributs de cet élément seront ensuite déduits en tant que colonnes de cette table.</span><span class="sxs-lookup"><span data-stu-id="bec20-116">The attributes of that element will then be inferred as columns for the table.</span></span> <span data-ttu-id="bec20-117">La propriété **ColumnMapping** des colonnes aura pour valeur **MappingType. Attribute**afin de s’assurer que les noms de colonne seront écrits comme des attributs si le schéma est réécrit en XML.</span><span class="sxs-lookup"><span data-stu-id="bec20-117">The **ColumnMapping** property of the columns will be set to **MappingType.Attribute**, to ensure that the column names will be written as attributes if the schema is written back to XML.</span></span> <span data-ttu-id="bec20-118">Les valeurs des attributs sont stockées dans une ligne de la table.</span><span class="sxs-lookup"><span data-stu-id="bec20-118">The values of the attributes are stored in a row in the table.</span></span> <span data-ttu-id="bec20-119">Examinons, par exemple, le code XML suivant :</span><span class="sxs-lookup"><span data-stu-id="bec20-119">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 <span data-ttu-id="bec20-120">Le processus d’inférence produira une table nommée **element1** avec deux colonnes, **attr1** et **attr2**.</span><span class="sxs-lookup"><span data-stu-id="bec20-120">The inference process will produce a table named **Element1** with two columns, **attr1** and **attr2**.</span></span> <span data-ttu-id="bec20-121">La propriété **ColumnMapping** des deux colonnes aura pour valeur **MappingType. Attribute**.</span><span class="sxs-lookup"><span data-stu-id="bec20-121">The **ColumnMapping** property of both columns will be set to **MappingType.Attribute**.</span></span>  
  
 <span data-ttu-id="bec20-122">**Jeu de données :** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="bec20-122">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="bec20-123">**Table :** Élément1</span><span class="sxs-lookup"><span data-stu-id="bec20-123">**Table:** Element1</span></span>  
  
|<span data-ttu-id="bec20-124">attr1</span><span class="sxs-lookup"><span data-stu-id="bec20-124">attr1</span></span>|<span data-ttu-id="bec20-125">attr2</span><span class="sxs-lookup"><span data-stu-id="bec20-125">attr2</span></span>|  
|-----------|-----------|  
|<span data-ttu-id="bec20-126">valeur1</span><span class="sxs-lookup"><span data-stu-id="bec20-126">value1</span></span>|<span data-ttu-id="bec20-127">valeur2</span><span class="sxs-lookup"><span data-stu-id="bec20-127">value2</span></span>|  
  
## <a name="elements-without-attributes-or-child-elements"></a><span data-ttu-id="bec20-128">Éléments dépourvus d'attributs ou d'éléments enfants</span><span class="sxs-lookup"><span data-stu-id="bec20-128">Elements Without Attributes or Child Elements</span></span>  

 <span data-ttu-id="bec20-129">Si un élément ne comporte ni éléments enfants, ni attributs, il sera déduit en tant que colonne.</span><span class="sxs-lookup"><span data-stu-id="bec20-129">If an element has no child elements or attributes, it will be inferred as a column.</span></span> <span data-ttu-id="bec20-130">La propriété **ColumnMapping** de la colonne sera définie sur **MappingType. Element**.</span><span class="sxs-lookup"><span data-stu-id="bec20-130">The **ColumnMapping** property of the column will be set to **MappingType.Element**.</span></span> <span data-ttu-id="bec20-131">Le texte des éléments enfants est stocké dans une ligne de la table.</span><span class="sxs-lookup"><span data-stu-id="bec20-131">The text for child elements is stored in a row in the table.</span></span> <span data-ttu-id="bec20-132">Examinons, par exemple, le code XML suivant :</span><span class="sxs-lookup"><span data-stu-id="bec20-132">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
    <ChildElement2>Text2</ChildElement2>  
  </Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="bec20-133">Le processus d’inférence produira une table nommée **element1** avec deux colonnes **ChildElement1** et **ChildElement2**.</span><span class="sxs-lookup"><span data-stu-id="bec20-133">The inference process will produce a table named **Element1** with two columns, **ChildElement1** and **ChildElement2**.</span></span> <span data-ttu-id="bec20-134">La propriété **ColumnMapping** des deux colonnes aura pour valeur **MappingType. Element**.</span><span class="sxs-lookup"><span data-stu-id="bec20-134">The **ColumnMapping** property of both columns will be set to **MappingType.Element**.</span></span>  
  
 <span data-ttu-id="bec20-135">**Jeu de données :** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="bec20-135">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="bec20-136">**Table :** Élément1</span><span class="sxs-lookup"><span data-stu-id="bec20-136">**Table:** Element1</span></span>  
  
|<span data-ttu-id="bec20-137">ChildElement1</span><span class="sxs-lookup"><span data-stu-id="bec20-137">ChildElement1</span></span>|<span data-ttu-id="bec20-138">ChildElement2</span><span class="sxs-lookup"><span data-stu-id="bec20-138">ChildElement2</span></span>|  
|-------------------|-------------------|  
|<span data-ttu-id="bec20-139">Text1</span><span class="sxs-lookup"><span data-stu-id="bec20-139">Text1</span></span>|<span data-ttu-id="bec20-140">Text2</span><span class="sxs-lookup"><span data-stu-id="bec20-140">Text2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bec20-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bec20-141">See also</span></span>

- [<span data-ttu-id="bec20-142">Déduction de la structure relationnelle des DataSet à partir de XML</span><span class="sxs-lookup"><span data-stu-id="bec20-142">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="bec20-143">Chargement d'un DataSet à partir de XML</span><span class="sxs-lookup"><span data-stu-id="bec20-143">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)
- [<span data-ttu-id="bec20-144">Chargement des informations de schéma de DataSet à partir de XML</span><span class="sxs-lookup"><span data-stu-id="bec20-144">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="bec20-145">Utilisation de XML dans un DataSet</span><span class="sxs-lookup"><span data-stu-id="bec20-145">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="bec20-146">DataSets, DataTables et DataViews</span><span class="sxs-lookup"><span data-stu-id="bec20-146">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="bec20-147">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="bec20-147">ADO.NET Overview</span></span>](../ado-net-overview.md)
