---
title: Déduction des relations
ms.date: 03/30/2017
ms.assetid: 8fa86a9d-6545-4a9d-b1f5-58d9742179c7
ms.openlocfilehash: 92a4953dc7f5119ffbf171ff2a7bf5b58e896638
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204774"
---
# <a name="inferring-relationships"></a><span data-ttu-id="82bec-102">Déduction des relations</span><span class="sxs-lookup"><span data-stu-id="82bec-102">Inferring Relationships</span></span>
<span data-ttu-id="82bec-103">Si un élément déduit en tant que table comporte un élément enfant également déduit en tant que table, un objet <xref:System.Data.DataRelation> sera créé entre les deux tables.</span><span class="sxs-lookup"><span data-stu-id="82bec-103">If an element that is inferred as a table has a child element that is also inferred as a table, a <xref:System.Data.DataRelation> will be created between the two tables.</span></span> <span data-ttu-id="82bec-104">Une nouvelle colonne portant le nom **ParentTableName_Id** sera ajoutée à la fois à la table créée pour l’élément parent et à la table créée pour l’élément enfant.</span><span class="sxs-lookup"><span data-stu-id="82bec-104">A new column with a name of **ParentTableName_Id** will be added to both the table created for the parent element, and the table created for the child element.</span></span> <span data-ttu-id="82bec-105">La propriété **ColumnMapping** de cette colonne d’identité aura pour valeur **MappingType. Hidden**.</span><span class="sxs-lookup"><span data-stu-id="82bec-105">The **ColumnMapping** property of this identity column will be set to **MappingType.Hidden**.</span></span> <span data-ttu-id="82bec-106">La colonne sera une clé primaire auto-incrémentée pour la table parente et sera utilisée pour le **DataRelation** entre les deux tables.</span><span class="sxs-lookup"><span data-stu-id="82bec-106">The column will be an auto-incrementing primary key for the parent table, and will be used for the **DataRelation** between the two tables.</span></span> <span data-ttu-id="82bec-107">Le type de données de la colonne d’identité ajoutée sera **System. Int32**, contrairement au type de données de toutes les autres colonnes déduites, qui est **System. String**.</span><span class="sxs-lookup"><span data-stu-id="82bec-107">The data type of the added identity column will be **System.Int32**, unlike the data type of all other inferred columns, which is **System.String**.</span></span> <span data-ttu-id="82bec-108">Une <xref:System.Data.ForeignKeyConstraint> opération en**cascade** **DeleteRule** = est également créée à l’aide de la nouvelle colonne dans les tables parent et enfant.</span><span class="sxs-lookup"><span data-stu-id="82bec-108">A <xref:System.Data.ForeignKeyConstraint> with **DeleteRule** = **Cascade** will also be created using the new column in both the parent and child tables.</span></span>  
  
 <span data-ttu-id="82bec-109">Examinons, par exemple, le code XML suivant :</span><span class="sxs-lookup"><span data-stu-id="82bec-109">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1 attr1="value1" attr2="value2"/>  
    <ChildElement2>Text2</ChildElement2>  
  </Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="82bec-110">Le processus d'inférence produira deux tables :  **Element1** et **ChildElement1**.</span><span class="sxs-lookup"><span data-stu-id="82bec-110">The inference process will produce two tables: **Element1** and **ChildElement1**.</span></span>  
  
 <span data-ttu-id="82bec-111">La table **element1** aura deux colonnes: **Element1_Id** et **ChildElement2**.</span><span class="sxs-lookup"><span data-stu-id="82bec-111">The **Element1** table will have two columns: **Element1_Id** and **ChildElement2**.</span></span> <span data-ttu-id="82bec-112">La propriété **ColumnMapping** de la colonne **Element1_Id** aura pour valeur **MappingType. Hidden**.</span><span class="sxs-lookup"><span data-stu-id="82bec-112">The **ColumnMapping** property of the **Element1_Id** column will be set to **MappingType.Hidden**.</span></span> <span data-ttu-id="82bec-113">La propriété **ColumnMapping** de la colonne **ChildElement2** est définie sur **MappingType. Element**.</span><span class="sxs-lookup"><span data-stu-id="82bec-113">The **ColumnMapping** property of the **ChildElement2** column will be set to **MappingType.Element**.</span></span> <span data-ttu-id="82bec-114">La colonne **Element1_Id** est définie en tant que clé primaire de la table **element1** .</span><span class="sxs-lookup"><span data-stu-id="82bec-114">The **Element1_Id** column will be set as the primary key of the **Element1** table.</span></span>  
  
 <span data-ttu-id="82bec-115">La table **ChildElement1** aura trois colonnes: **attr1**, **attr2** et **Element1_Id**.</span><span class="sxs-lookup"><span data-stu-id="82bec-115">The **ChildElement1** table will have three columns: **attr1**, **attr2** and **Element1_Id**.</span></span> <span data-ttu-id="82bec-116">La propriété **ColumnMapping** des colonnes **attr1** et **attr2** aura pour valeur **MappingType. Attribute**.</span><span class="sxs-lookup"><span data-stu-id="82bec-116">The **ColumnMapping** property for the **attr1** and **attr2** columns will be set to **MappingType.Attribute**.</span></span> <span data-ttu-id="82bec-117">La propriété **ColumnMapping** de la colonne **Element1_Id** aura pour valeur **MappingType. Hidden**.</span><span class="sxs-lookup"><span data-stu-id="82bec-117">The **ColumnMapping** property of the **Element1_Id** column will be set to **MappingType.Hidden**.</span></span>  
  
 <span data-ttu-id="82bec-118">Un **DataRelation** et un **ForeignKeyConstraint** seront créés à l’aide des colonnes **Element1_Id** des deux tables.</span><span class="sxs-lookup"><span data-stu-id="82bec-118">A **DataRelation** and **ForeignKeyConstraint** will be created using the **Element1_Id** columns from both tables.</span></span>  
  
 <span data-ttu-id="82bec-119">**Ensemble** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="82bec-119">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="82bec-120">**Table :** Element1</span><span class="sxs-lookup"><span data-stu-id="82bec-120">**Table:** Element1</span></span>  
  
|<span data-ttu-id="82bec-121">Element1_Id</span><span class="sxs-lookup"><span data-stu-id="82bec-121">Element1_Id</span></span>|<span data-ttu-id="82bec-122">ChildElement2</span><span class="sxs-lookup"><span data-stu-id="82bec-122">ChildElement2</span></span>|  
|------------------|-------------------|  
|<span data-ttu-id="82bec-123">0</span><span class="sxs-lookup"><span data-stu-id="82bec-123">0</span></span>|<span data-ttu-id="82bec-124">Text2</span><span class="sxs-lookup"><span data-stu-id="82bec-124">Text2</span></span>|  
  
 <span data-ttu-id="82bec-125">**Table :** ChildElement1</span><span class="sxs-lookup"><span data-stu-id="82bec-125">**Table:** ChildElement1</span></span>  
  
|<span data-ttu-id="82bec-126">attr1</span><span class="sxs-lookup"><span data-stu-id="82bec-126">attr1</span></span>|<span data-ttu-id="82bec-127">attr2</span><span class="sxs-lookup"><span data-stu-id="82bec-127">attr2</span></span>|<span data-ttu-id="82bec-128">Element1_Id</span><span class="sxs-lookup"><span data-stu-id="82bec-128">Element1_Id</span></span>|  
|-----------|-----------|------------------|  
|<span data-ttu-id="82bec-129">valeur1</span><span class="sxs-lookup"><span data-stu-id="82bec-129">value1</span></span>|<span data-ttu-id="82bec-130">valeur2</span><span class="sxs-lookup"><span data-stu-id="82bec-130">value2</span></span>|<span data-ttu-id="82bec-131">0</span><span class="sxs-lookup"><span data-stu-id="82bec-131">0</span></span>|  
  
 <span data-ttu-id="82bec-132">**DataRelation** Element1_ChildElement1</span><span class="sxs-lookup"><span data-stu-id="82bec-132">**DataRelation:** Element1_ChildElement1</span></span>  
  
 <span data-ttu-id="82bec-133">**ParentTable:** Element1</span><span class="sxs-lookup"><span data-stu-id="82bec-133">**ParentTable:** Element1</span></span>  
  
 <span data-ttu-id="82bec-134">**ParentColumn:** Element1_Id</span><span class="sxs-lookup"><span data-stu-id="82bec-134">**ParentColumn:** Element1_Id</span></span>  
  
 <span data-ttu-id="82bec-135">**ChildTable** ChildElement1</span><span class="sxs-lookup"><span data-stu-id="82bec-135">**ChildTable:** ChildElement1</span></span>  
  
 <span data-ttu-id="82bec-136">**ChildColumn:** Element1_Id</span><span class="sxs-lookup"><span data-stu-id="82bec-136">**ChildColumn:** Element1_Id</span></span>  
  
 <span data-ttu-id="82bec-137">**Imbriquée** True</span><span class="sxs-lookup"><span data-stu-id="82bec-137">**Nested:** True</span></span>  
  
 <span data-ttu-id="82bec-138">**ForeignKeyConstraint** Element1_ChildElement1</span><span class="sxs-lookup"><span data-stu-id="82bec-138">**ForeignKeyConstraint:** Element1_ChildElement1</span></span>  
  
 <span data-ttu-id="82bec-139">**Chronique** Element1_Id</span><span class="sxs-lookup"><span data-stu-id="82bec-139">**Column:** Element1_Id</span></span>  
  
 <span data-ttu-id="82bec-140">**ParentTable:** Element1</span><span class="sxs-lookup"><span data-stu-id="82bec-140">**ParentTable:** Element1</span></span>  
  
 <span data-ttu-id="82bec-141">**ChildTable** ChildElement1</span><span class="sxs-lookup"><span data-stu-id="82bec-141">**ChildTable:** ChildElement1</span></span>  
  
 <span data-ttu-id="82bec-142">**DeleteRule** Cascade</span><span class="sxs-lookup"><span data-stu-id="82bec-142">**DeleteRule:** Cascade</span></span>  
  
 <span data-ttu-id="82bec-143">**AcceptRejectRule** Aucun</span><span class="sxs-lookup"><span data-stu-id="82bec-143">**AcceptRejectRule:** None</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82bec-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="82bec-144">See also</span></span>

- [<span data-ttu-id="82bec-145">Inférence de la structure relationnelle d’un DataSet à partir de XML</span><span class="sxs-lookup"><span data-stu-id="82bec-145">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="82bec-146">Chargement d’un DataSet à partir de XML</span><span class="sxs-lookup"><span data-stu-id="82bec-146">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)
- [<span data-ttu-id="82bec-147">Chargement des informations de schéma de DataSet à partir de XML</span><span class="sxs-lookup"><span data-stu-id="82bec-147">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="82bec-148">Imbrication de DataRelations</span><span class="sxs-lookup"><span data-stu-id="82bec-148">Nesting DataRelations</span></span>](nesting-datarelations.md)
- [<span data-ttu-id="82bec-149">Utilisation de XML dans un DataSet</span><span class="sxs-lookup"><span data-stu-id="82bec-149">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="82bec-150">DataSets, DataTables et DataViews</span><span class="sxs-lookup"><span data-stu-id="82bec-150">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="82bec-151">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="82bec-151">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
