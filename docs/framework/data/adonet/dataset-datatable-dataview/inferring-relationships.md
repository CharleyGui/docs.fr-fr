---
title: Déduction des relations
ms.date: 03/30/2017
ms.assetid: 8fa86a9d-6545-4a9d-b1f5-58d9742179c7
ms.openlocfilehash: ee691eee95c34afdb6374cdd7448d4b44ece3055
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177564"
---
# <a name="inferring-relationships"></a><span data-ttu-id="92836-102">Déduction des relations</span><span class="sxs-lookup"><span data-stu-id="92836-102">Inferring Relationships</span></span>

<span data-ttu-id="92836-103">Si un élément déduit en tant que table comporte un élément enfant également déduit en tant que table, un objet <xref:System.Data.DataRelation> sera créé entre les deux tables.</span><span class="sxs-lookup"><span data-stu-id="92836-103">If an element that is inferred as a table has a child element that is also inferred as a table, a <xref:System.Data.DataRelation> will be created between the two tables.</span></span> <span data-ttu-id="92836-104">Une nouvelle colonne portant le nom **ParentTableName_Id** sera ajoutée à la fois à la table créée pour l’élément parent et à la table créée pour l’élément enfant.</span><span class="sxs-lookup"><span data-stu-id="92836-104">A new column with a name of **ParentTableName_Id** will be added to both the table created for the parent element, and the table created for the child element.</span></span> <span data-ttu-id="92836-105">La propriété **ColumnMapping** de cette colonne d’identité aura pour valeur **MappingType. Hidden**.</span><span class="sxs-lookup"><span data-stu-id="92836-105">The **ColumnMapping** property of this identity column will be set to **MappingType.Hidden**.</span></span> <span data-ttu-id="92836-106">La colonne sera une clé primaire auto-incrémentée pour la table parente et sera utilisée pour le **DataRelation** entre les deux tables.</span><span class="sxs-lookup"><span data-stu-id="92836-106">The column will be an auto-incrementing primary key for the parent table, and will be used for the **DataRelation** between the two tables.</span></span> <span data-ttu-id="92836-107">Le type de données de la colonne d’identité ajoutée sera **System. Int32**, contrairement au type de données de toutes les autres colonnes déduites, qui est **System. String**.</span><span class="sxs-lookup"><span data-stu-id="92836-107">The data type of the added identity column will be **System.Int32**, unlike the data type of all other inferred columns, which is **System.String**.</span></span> <span data-ttu-id="92836-108">Une <xref:System.Data.ForeignKeyConstraint> opération **DeleteRule**en  =  **cascade** DeleteRule est également créée à l’aide de la nouvelle colonne dans les tables parent et enfant.</span><span class="sxs-lookup"><span data-stu-id="92836-108">A <xref:System.Data.ForeignKeyConstraint> with **DeleteRule** = **Cascade** will also be created using the new column in both the parent and child tables.</span></span>  
  
 <span data-ttu-id="92836-109">Examinons, par exemple, le code XML suivant :</span><span class="sxs-lookup"><span data-stu-id="92836-109">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1 attr1="value1" attr2="value2"/>  
    <ChildElement2>Text2</ChildElement2>  
  </Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="92836-110">Le processus d’inférence produira deux tables : **element1** et **ChildElement1**.</span><span class="sxs-lookup"><span data-stu-id="92836-110">The inference process will produce two tables: **Element1** and **ChildElement1**.</span></span>  
  
 <span data-ttu-id="92836-111">La table **element1** aura deux colonnes : **Element1_Id** et **ChildElement2**.</span><span class="sxs-lookup"><span data-stu-id="92836-111">The **Element1** table will have two columns: **Element1_Id** and **ChildElement2**.</span></span> <span data-ttu-id="92836-112">La propriété **ColumnMapping** de la colonne **Element1_Id** aura pour valeur **MappingType. Hidden**.</span><span class="sxs-lookup"><span data-stu-id="92836-112">The **ColumnMapping** property of the **Element1_Id** column will be set to **MappingType.Hidden**.</span></span> <span data-ttu-id="92836-113">La propriété **ColumnMapping** de la colonne **ChildElement2** est définie sur **MappingType. Element**.</span><span class="sxs-lookup"><span data-stu-id="92836-113">The **ColumnMapping** property of the **ChildElement2** column will be set to **MappingType.Element**.</span></span> <span data-ttu-id="92836-114">La **Element1_Id** colonne sera définie en tant que clé primaire de la table **element1** .</span><span class="sxs-lookup"><span data-stu-id="92836-114">The **Element1_Id** column will be set as the primary key of the **Element1** table.</span></span>  
  
 <span data-ttu-id="92836-115">La table **ChildElement1** comporte trois colonnes : **attr1**, **attr2** et **Element1_Id**.</span><span class="sxs-lookup"><span data-stu-id="92836-115">The **ChildElement1** table will have three columns: **attr1**, **attr2** and **Element1_Id**.</span></span> <span data-ttu-id="92836-116">La propriété **ColumnMapping** des colonnes **attr1** et **attr2** aura pour valeur **MappingType. Attribute**.</span><span class="sxs-lookup"><span data-stu-id="92836-116">The **ColumnMapping** property for the **attr1** and **attr2** columns will be set to **MappingType.Attribute**.</span></span> <span data-ttu-id="92836-117">La propriété **ColumnMapping** de la colonne **Element1_Id** aura pour valeur **MappingType. Hidden**.</span><span class="sxs-lookup"><span data-stu-id="92836-117">The **ColumnMapping** property of the **Element1_Id** column will be set to **MappingType.Hidden**.</span></span>  
  
 <span data-ttu-id="92836-118">Un **DataRelation** et un **ForeignKeyConstraint** seront créés à l’aide des colonnes **Element1_Id** des deux tables.</span><span class="sxs-lookup"><span data-stu-id="92836-118">A **DataRelation** and **ForeignKeyConstraint** will be created using the **Element1_Id** columns from both tables.</span></span>  
  
 <span data-ttu-id="92836-119">**Jeu de données :** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="92836-119">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="92836-120">**Table :** Élément1</span><span class="sxs-lookup"><span data-stu-id="92836-120">**Table:** Element1</span></span>  
  
|<span data-ttu-id="92836-121">Element1_Id</span><span class="sxs-lookup"><span data-stu-id="92836-121">Element1_Id</span></span>|<span data-ttu-id="92836-122">ChildElement2</span><span class="sxs-lookup"><span data-stu-id="92836-122">ChildElement2</span></span>|  
|------------------|-------------------|  
|<span data-ttu-id="92836-123">0</span><span class="sxs-lookup"><span data-stu-id="92836-123">0</span></span>|<span data-ttu-id="92836-124">Text2</span><span class="sxs-lookup"><span data-stu-id="92836-124">Text2</span></span>|  
  
 <span data-ttu-id="92836-125">**Table :** ChildElement1</span><span class="sxs-lookup"><span data-stu-id="92836-125">**Table:** ChildElement1</span></span>  
  
|<span data-ttu-id="92836-126">attr1</span><span class="sxs-lookup"><span data-stu-id="92836-126">attr1</span></span>|<span data-ttu-id="92836-127">attr2</span><span class="sxs-lookup"><span data-stu-id="92836-127">attr2</span></span>|<span data-ttu-id="92836-128">Element1_Id</span><span class="sxs-lookup"><span data-stu-id="92836-128">Element1_Id</span></span>|  
|-----------|-----------|------------------|  
|<span data-ttu-id="92836-129">valeur1</span><span class="sxs-lookup"><span data-stu-id="92836-129">value1</span></span>|<span data-ttu-id="92836-130">valeur2</span><span class="sxs-lookup"><span data-stu-id="92836-130">value2</span></span>|<span data-ttu-id="92836-131">0</span><span class="sxs-lookup"><span data-stu-id="92836-131">0</span></span>|  
  
 <span data-ttu-id="92836-132">**DataRelation :** Element1_ChildElement1</span><span class="sxs-lookup"><span data-stu-id="92836-132">**DataRelation:** Element1_ChildElement1</span></span>  
  
 <span data-ttu-id="92836-133">**ParentTable :** Élément1</span><span class="sxs-lookup"><span data-stu-id="92836-133">**ParentTable:** Element1</span></span>  
  
 <span data-ttu-id="92836-134">**ParentColumn :** Element1_Id</span><span class="sxs-lookup"><span data-stu-id="92836-134">**ParentColumn:** Element1_Id</span></span>  
  
 <span data-ttu-id="92836-135">**ChildTable :** ChildElement1</span><span class="sxs-lookup"><span data-stu-id="92836-135">**ChildTable:** ChildElement1</span></span>  
  
 <span data-ttu-id="92836-136">**ChildColumn :** Element1_Id</span><span class="sxs-lookup"><span data-stu-id="92836-136">**ChildColumn:** Element1_Id</span></span>  
  
 <span data-ttu-id="92836-137">**Imbriqué :** :</span><span class="sxs-lookup"><span data-stu-id="92836-137">**Nested:** True</span></span>  
  
 <span data-ttu-id="92836-138">**ForeignKeyConstraint :** Element1_ChildElement1</span><span class="sxs-lookup"><span data-stu-id="92836-138">**ForeignKeyConstraint:** Element1_ChildElement1</span></span>  
  
 <span data-ttu-id="92836-139">**Colonne :** Element1_Id</span><span class="sxs-lookup"><span data-stu-id="92836-139">**Column:** Element1_Id</span></span>  
  
 <span data-ttu-id="92836-140">**ParentTable :** Élément1</span><span class="sxs-lookup"><span data-stu-id="92836-140">**ParentTable:** Element1</span></span>  
  
 <span data-ttu-id="92836-141">**ChildTable :** ChildElement1</span><span class="sxs-lookup"><span data-stu-id="92836-141">**ChildTable:** ChildElement1</span></span>  
  
 <span data-ttu-id="92836-142">**DeleteRule :** Répercuté</span><span class="sxs-lookup"><span data-stu-id="92836-142">**DeleteRule:** Cascade</span></span>  
  
 <span data-ttu-id="92836-143">**AcceptRejectRule :** None</span><span class="sxs-lookup"><span data-stu-id="92836-143">**AcceptRejectRule:** None</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92836-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="92836-144">See also</span></span>

- [<span data-ttu-id="92836-145">Déduction de la structure relationnelle des DataSet à partir de XML</span><span class="sxs-lookup"><span data-stu-id="92836-145">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="92836-146">Chargement d'un DataSet à partir de XML</span><span class="sxs-lookup"><span data-stu-id="92836-146">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)
- [<span data-ttu-id="92836-147">Chargement des informations de schéma de DataSet à partir de XML</span><span class="sxs-lookup"><span data-stu-id="92836-147">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="92836-148">Imbrication de DataRelations</span><span class="sxs-lookup"><span data-stu-id="92836-148">Nesting DataRelations</span></span>](nesting-datarelations.md)
- [<span data-ttu-id="92836-149">Utilisation de XML dans un DataSet</span><span class="sxs-lookup"><span data-stu-id="92836-149">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="92836-150">DataSets, DataTables et DataViews</span><span class="sxs-lookup"><span data-stu-id="92836-150">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="92836-151">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="92836-151">ADO.NET Overview</span></span>](../ado-net-overview.md)
