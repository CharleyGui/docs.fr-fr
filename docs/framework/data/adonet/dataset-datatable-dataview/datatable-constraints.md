---
title: Contraintes de DataTable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 27c9f2fd-f64d-4b4e-bbf6-1d24f47067cb
ms.openlocfilehash: 1224518a9a16f48f770b6839317b9787da97377b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153272"
---
# <a name="datatable-constraints"></a><span data-ttu-id="533a4-102">Contraintes de DataTable</span><span class="sxs-lookup"><span data-stu-id="533a4-102">DataTable Constraints</span></span>

<span data-ttu-id="533a4-103">Vous pouvez utiliser des contraintes pour appliquer des restrictions sur les données dans un objet <xref:System.Data.DataTable> afin de conserver l'intégrité des données.</span><span class="sxs-lookup"><span data-stu-id="533a4-103">You can use constraints to enforce restrictions on the data in a <xref:System.Data.DataTable>, in order to maintain the integrity of the data.</span></span> <span data-ttu-id="533a4-104">Une contrainte est une règle automatique, appliquée à une ou plusieurs colonnes en relation, qui détermine l'action à réaliser lorsque la valeur d'une ligne est modifiée.</span><span class="sxs-lookup"><span data-stu-id="533a4-104">A constraint is an automatic rule, applied to a column or related columns, that determines the course of action when the value of a row is somehow altered.</span></span> <span data-ttu-id="533a4-105">Les contraintes sont appliquées lorsque la `System.Data.DataSet.EnforceConstraints` propriété de a la <xref:System.Data.DataSet> **valeur true**.</span><span class="sxs-lookup"><span data-stu-id="533a4-105">Constraints are enforced when the `System.Data.DataSet.EnforceConstraints` property of the <xref:System.Data.DataSet> is **true**.</span></span> <span data-ttu-id="533a4-106">Pour obtenir un exemple de code montrant comment définir la propriété `EnforceConstraints`, consultez la rubrique de référence <xref:System.Data.DataSet.EnforceConstraints%2A>.</span><span class="sxs-lookup"><span data-stu-id="533a4-106">For a code example that shows how to set the `EnforceConstraints` property, see the <xref:System.Data.DataSet.EnforceConstraints%2A> reference topic.</span></span>  
  
 <span data-ttu-id="533a4-107">Il y a deux types de contraintes dans ADO.NET : la <xref:System.Data.ForeignKeyConstraint> et la <xref:System.Data.UniqueConstraint>.</span><span class="sxs-lookup"><span data-stu-id="533a4-107">There are two kinds of constraints in ADO.NET: the <xref:System.Data.ForeignKeyConstraint> and the <xref:System.Data.UniqueConstraint>.</span></span> <span data-ttu-id="533a4-108">Par défaut, les deux contraintes sont créées automatiquement lorsque vous créez une relation entre deux tables ou plus en ajoutant un <xref:System.Data.DataRelation> au **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="533a4-108">By default, both constraints are created automatically when you create a relationship between two or more tables by adding a <xref:System.Data.DataRelation> to the **DataSet**.</span></span> <span data-ttu-id="533a4-109">Toutefois, vous pouvez désactiver ce comportement en spécifiant **createConstraints**  =  **false** lors de la création de la relation.</span><span class="sxs-lookup"><span data-stu-id="533a4-109">However, you can disable this behavior by specifying **createConstraints** = **false** when creating the relation.</span></span>  
  
## <a name="foreignkeyconstraint"></a><span data-ttu-id="533a4-110">ForeignKeyConstraint</span><span class="sxs-lookup"><span data-stu-id="533a4-110">ForeignKeyConstraint</span></span>  

 <span data-ttu-id="533a4-111">Un **ForeignKeyConstraint** applique des règles sur la façon dont les mises à jour et les suppressions des tables associées sont propagées.</span><span class="sxs-lookup"><span data-stu-id="533a4-111">A **ForeignKeyConstraint** enforces rules about how updates and deletes to related tables are propagated.</span></span> <span data-ttu-id="533a4-112">Par exemple, si une valeur dans une ligne d’une table est mise à jour ou supprimée et que cette même valeur est également utilisée dans une ou plusieurs tables associées, un **ForeignKeyConstraint** détermine ce qui se passe dans les tables associées.</span><span class="sxs-lookup"><span data-stu-id="533a4-112">For example, if a value in a row of one table is updated or deleted, and that same value is also used in one or more related tables, a **ForeignKeyConstraint** determines what happens in the related tables.</span></span>  
  
 <span data-ttu-id="533a4-113">Les <xref:System.Data.ForeignKeyConstraint.DeleteRule%2A> <xref:System.Data.ForeignKeyConstraint.UpdateRule%2A> Propriétés et du **ForeignKeyConstraint** définissent l’action à entreprendre lorsque l’utilisateur tente de supprimer ou de mettre à jour une ligne dans une table associée.</span><span class="sxs-lookup"><span data-stu-id="533a4-113">The <xref:System.Data.ForeignKeyConstraint.DeleteRule%2A> and <xref:System.Data.ForeignKeyConstraint.UpdateRule%2A> properties of the **ForeignKeyConstraint** define the action to be taken when the user attempts to delete or update a row in a related table.</span></span> <span data-ttu-id="533a4-114">Le tableau suivant décrit les différents paramètres disponibles pour les propriétés **DeleteRule** et **UpdateRule** de **ForeignKeyConstraint**.</span><span class="sxs-lookup"><span data-stu-id="533a4-114">The following table describes the different settings available for the **DeleteRule** and **UpdateRule** properties of the **ForeignKeyConstraint**.</span></span>  
  
|<span data-ttu-id="533a4-115">Paramètre de règle</span><span class="sxs-lookup"><span data-stu-id="533a4-115">Rule setting</span></span>|<span data-ttu-id="533a4-116">Description</span><span class="sxs-lookup"><span data-stu-id="533a4-116">Description</span></span>|  
|------------------|-----------------|  
|<span data-ttu-id="533a4-117">**Répercuté**</span><span class="sxs-lookup"><span data-stu-id="533a4-117">**Cascade**</span></span>|<span data-ttu-id="533a4-118">Supprime ou met à jour les lignes connexes.</span><span class="sxs-lookup"><span data-stu-id="533a4-118">Delete or update related rows.</span></span>|  
|<span data-ttu-id="533a4-119">**SetNull**</span><span class="sxs-lookup"><span data-stu-id="533a4-119">**SetNull**</span></span>|<span data-ttu-id="533a4-120">Définissez les valeurs des lignes connexes sur **DBNull**.</span><span class="sxs-lookup"><span data-stu-id="533a4-120">Set values in related rows to **DBNull**.</span></span>|  
|<span data-ttu-id="533a4-121">**SetDefault**</span><span class="sxs-lookup"><span data-stu-id="533a4-121">**SetDefault**</span></span>|<span data-ttu-id="533a4-122">Définit les valeurs des lignes connexes sur la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="533a4-122">Set values in related rows to the default value.</span></span>|  
|<span data-ttu-id="533a4-123">**Aucun**</span><span class="sxs-lookup"><span data-stu-id="533a4-123">**None**</span></span>|<span data-ttu-id="533a4-124">N'effectue aucune action sur les lignes connexes.</span><span class="sxs-lookup"><span data-stu-id="533a4-124">Take no action on related rows.</span></span> <span data-ttu-id="533a4-125">Il s’agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="533a4-125">This is the default.</span></span>|  
  
 <span data-ttu-id="533a4-126">Un **ForeignKeyConstraint** peut restreindre, ainsi que propager, les modifications apportées aux colonnes associées.</span><span class="sxs-lookup"><span data-stu-id="533a4-126">A **ForeignKeyConstraint** can restrict, as well as propagate, changes to related columns.</span></span> <span data-ttu-id="533a4-127">En fonction des propriétés définies pour le **ForeignKeyConstraint** d’une colonne, si la propriété **EnforceConstraints** du jeu de **données** a la **valeur true**, l’exécution de certaines opérations sur la ligne parente entraîne une exception.</span><span class="sxs-lookup"><span data-stu-id="533a4-127">Depending on the properties set for the **ForeignKeyConstraint** of a column, if the **EnforceConstraints** property of the **DataSet** is **true**, performing certain operations on the parent row will result in an exception.</span></span> <span data-ttu-id="533a4-128">Par exemple, si la propriété **DeleteRule** de **ForeignKeyConstraint** a la valeur **None**, une ligne parente ne peut pas être supprimée si elle contient des lignes enfants.</span><span class="sxs-lookup"><span data-stu-id="533a4-128">For example, if the **DeleteRule** property of the **ForeignKeyConstraint** is **None**, a parent row cannot be deleted if it has any child rows.</span></span>  
  
 <span data-ttu-id="533a4-129">Vous pouvez créer une contrainte de clé étrangère entre des colonnes uniques ou entre un tableau de colonnes à l’aide du constructeur **ForeignKeyConstraint** .</span><span class="sxs-lookup"><span data-stu-id="533a4-129">You can create a foreign key constraint between single columns or between an array of columns by using the **ForeignKeyConstraint** constructor.</span></span> <span data-ttu-id="533a4-130">Transmettez l’objet **ForeignKeyConstraint** résultant à la méthode **Add** de la propriété **Constraints** de la table, qui est un **ConstraintCollection**.</span><span class="sxs-lookup"><span data-stu-id="533a4-130">Pass the resulting **ForeignKeyConstraint** object to the **Add** method of the table's **Constraints** property, which is a **ConstraintCollection**.</span></span> <span data-ttu-id="533a4-131">Vous pouvez également passer des arguments de constructeur à plusieurs surcharges de la méthode **Add** d’un **ConstraintCollection** pour créer un **ForeignKeyConstraint**.</span><span class="sxs-lookup"><span data-stu-id="533a4-131">You can also pass constructor arguments to several overloads of the **Add** method of a **ConstraintCollection** to create a **ForeignKeyConstraint**.</span></span>  
  
 <span data-ttu-id="533a4-132">Lors de la création d’un **ForeignKeyConstraint**, vous pouvez passer les valeurs de **DeleteRule** et **UpdateRule** comme arguments au constructeur, ou vous pouvez les définir comme des propriétés comme dans l’exemple suivant (où **DeleteRule** a la valeur **None**).</span><span class="sxs-lookup"><span data-stu-id="533a4-132">When creating a **ForeignKeyConstraint**, you can pass the **DeleteRule** and **UpdateRule** values to the constructor as arguments, or you can set them as properties as in the following example (where the **DeleteRule** value is set to **None**).</span></span>  
  
```vb  
Dim custOrderFK As ForeignKeyConstraint = New ForeignKeyConstraint("CustOrderFK", _  
  custDS.Tables("CustTable").Columns("CustomerID"), _  
  custDS.Tables("OrdersTable").Columns("CustomerID"))  
custOrderFK.DeleteRule = Rule.None
' Cannot delete a customer value that has associated existing orders.  
custDS.Tables("OrdersTable").Constraints.Add(custOrderFK)  
```  
  
```csharp  
ForeignKeyConstraint custOrderFK = new ForeignKeyConstraint("CustOrderFK",  
  custDS.Tables["CustTable"].Columns["CustomerID"],
  custDS.Tables["OrdersTable"].Columns["CustomerID"]);  
custOrderFK.DeleteRule = Rule.None;
// Cannot delete a customer value that has associated existing orders.  
custDS.Tables["OrdersTable"].Constraints.Add(custOrderFK);  
```  
  
### <a name="acceptrejectrule"></a><span data-ttu-id="533a4-133">AcceptRejectRule</span><span class="sxs-lookup"><span data-stu-id="533a4-133">AcceptRejectRule</span></span>  

 <span data-ttu-id="533a4-134">Les modifications apportées aux lignes peuvent être acceptées à l’aide de la méthode **AcceptChanges** ou annulées à l’aide de la méthode **RejectChanges** du **DataSet**, du **DataTable**ou de **DataRow**.</span><span class="sxs-lookup"><span data-stu-id="533a4-134">Changes to rows can be accepted using the **AcceptChanges** method or canceled using the **RejectChanges** method of the **DataSet**, **DataTable**, or **DataRow**.</span></span> <span data-ttu-id="533a4-135">Lorsqu’un **jeu de données** contient des **ForeignKeyConstraints**, l’appel des méthodes **AcceptChanges** ou **RejectChanges** applique la méthode **AcceptRejectRule**.</span><span class="sxs-lookup"><span data-stu-id="533a4-135">When a **DataSet** contains **ForeignKeyConstraints**, invoking the **AcceptChanges** or **RejectChanges** methods enforces the **AcceptRejectRule**.</span></span> <span data-ttu-id="533a4-136">La propriété **AcceptRejectRule** de **ForeignKeyConstraint** détermine l’action qui sera entreprise sur les lignes enfants lorsque **AcceptChanges** ou **RejectChanges** est appelé sur la ligne parente.</span><span class="sxs-lookup"><span data-stu-id="533a4-136">The **AcceptRejectRule** property of the **ForeignKeyConstraint** determines which action will be taken on the child rows when **AcceptChanges** or **RejectChanges** is called on the parent row.</span></span>  
  
 <span data-ttu-id="533a4-137">Le tableau suivant répertorie les paramètres disponibles pour **AcceptRejectRule**.</span><span class="sxs-lookup"><span data-stu-id="533a4-137">The following table lists the available settings for the **AcceptRejectRule**.</span></span>  
  
|<span data-ttu-id="533a4-138">Paramètre de règle</span><span class="sxs-lookup"><span data-stu-id="533a4-138">Rule setting</span></span>|<span data-ttu-id="533a4-139">Description</span><span class="sxs-lookup"><span data-stu-id="533a4-139">Description</span></span>|  
|------------------|-----------------|  
|<span data-ttu-id="533a4-140">**Répercuté**</span><span class="sxs-lookup"><span data-stu-id="533a4-140">**Cascade**</span></span>|<span data-ttu-id="533a4-141">Accepte ou rejette les modifications des lignes enfants.</span><span class="sxs-lookup"><span data-stu-id="533a4-141">Accept or reject changes to child rows.</span></span>|  
|<span data-ttu-id="533a4-142">**Aucun**</span><span class="sxs-lookup"><span data-stu-id="533a4-142">**None**</span></span>|<span data-ttu-id="533a4-143">N'effectue aucune action sur les lignes enfants.</span><span class="sxs-lookup"><span data-stu-id="533a4-143">Take no action on child rows.</span></span> <span data-ttu-id="533a4-144">Il s’agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="533a4-144">This is the default.</span></span>|  
  
### <a name="example"></a><span data-ttu-id="533a4-145">Exemple</span><span class="sxs-lookup"><span data-stu-id="533a4-145">Example</span></span>  

 <span data-ttu-id="533a4-146">L'exemple suivant crée un objet <xref:System.Data.ForeignKeyConstraint>, définit plusieurs de ses propriétés, notamment la <xref:System.Data.ForeignKeyConstraint.AcceptRejectRule%2A>, et l'ajoute à la <xref:System.Data.ConstraintCollection> d'un objet <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="533a4-146">The following example creates a <xref:System.Data.ForeignKeyConstraint>, sets several of its properties, including the <xref:System.Data.ForeignKeyConstraint.AcceptRejectRule%2A>, and adds it to the <xref:System.Data.ConstraintCollection> of a <xref:System.Data.DataTable> object.</span></span>  
  
 [!code-csharp[DataWorks Data.AcceptRejectRule#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.AcceptRejectRule/CS/source.cs#1)]
 [!code-vb[DataWorks Data.AcceptRejectRule#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.AcceptRejectRule/VB/source.vb#1)]  
  
## <a name="uniqueconstraint"></a><span data-ttu-id="533a4-147">UniqueConstraint</span><span class="sxs-lookup"><span data-stu-id="533a4-147">UniqueConstraint</span></span>  

 <span data-ttu-id="533a4-148">L’objet **UniqueConstraint** , qui peut être assigné à une colonne unique ou à un tableau de colonnes dans un **DataTable**, garantit que toutes les données de la colonne ou des colonnes spécifiées sont uniques par ligne.</span><span class="sxs-lookup"><span data-stu-id="533a4-148">The **UniqueConstraint** object, which can be assigned either to a single column or to an array of columns in a **DataTable**, ensures that all data in the specified column or columns is unique per row.</span></span> <span data-ttu-id="533a4-149">Vous pouvez créer une contrainte unique pour une colonne ou un tableau de colonnes à l’aide du constructeur **UniqueConstraint** .</span><span class="sxs-lookup"><span data-stu-id="533a4-149">You can create a unique constraint for a column or array of columns by using the **UniqueConstraint** constructor.</span></span> <span data-ttu-id="533a4-150">Transmettez l’objet **UniqueConstraint** résultant à la méthode **Add** de la propriété **Constraints** de la table, qui est un **ConstraintCollection**.</span><span class="sxs-lookup"><span data-stu-id="533a4-150">Pass the resulting **UniqueConstraint** object to the **Add** method of the table's **Constraints** property, which is a **ConstraintCollection**.</span></span> <span data-ttu-id="533a4-151">Vous pouvez également passer des arguments de constructeur à plusieurs surcharges de la méthode **Add** d’un **ConstraintCollection** pour créer un **UniqueConstraint**.</span><span class="sxs-lookup"><span data-stu-id="533a4-151">You can also pass constructor arguments to several overloads of the **Add** method of a **ConstraintCollection** to create a **UniqueConstraint**.</span></span> <span data-ttu-id="533a4-152">Lorsque vous créez un **UniqueConstraint** pour une ou plusieurs colonnes, vous pouvez éventuellement spécifier si la ou les colonnes sont une clé primaire.</span><span class="sxs-lookup"><span data-stu-id="533a4-152">When creating a **UniqueConstraint** for a column or columns, you can optionally specify whether the column or columns are a primary key.</span></span>  
  
 <span data-ttu-id="533a4-153">Vous pouvez également créer une contrainte unique pour une colonne en attribuant la **valeur true**à la propriété **unique** de la colonne.</span><span class="sxs-lookup"><span data-stu-id="533a4-153">You can also create a unique constraint for a column by setting the **Unique** property of the column to **true**.</span></span> <span data-ttu-id="533a4-154">Sinon, l’affectation de la **valeur false** à la propriété **unique** d’une seule colonne supprime toute contrainte unique qui peut exister.</span><span class="sxs-lookup"><span data-stu-id="533a4-154">Alternatively, setting the **Unique** property of a single column to **false** removes any unique constraint that may exist.</span></span> <span data-ttu-id="533a4-155">Lorsque vous définissez une ou plusieurs colonnes comme clé primaire d'une table, une contrainte unique est automatiquement créée pour les colonnes spécifiées.</span><span class="sxs-lookup"><span data-stu-id="533a4-155">Defining a column or columns as the primary key for a table will automatically create a unique constraint for the specified column or columns.</span></span> <span data-ttu-id="533a4-156">Si vous supprimez une colonne de la propriété **PrimaryKey** d’un **DataTable**, **UniqueConstraint** est supprimé.</span><span class="sxs-lookup"><span data-stu-id="533a4-156">If you remove a column from the **PrimaryKey** property of a **DataTable**, the **UniqueConstraint** is removed.</span></span>  
  
 <span data-ttu-id="533a4-157">L’exemple suivant crée un **UniqueConstraint** pour deux colonnes d’un **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="533a4-157">The following example creates a **UniqueConstraint** for two columns of a **DataTable**.</span></span>  
  
```vb  
Dim custTable As DataTable = custDS.Tables("Customers")  
Dim custUnique As UniqueConstraint = _  
    New UniqueConstraint(New DataColumn()   {custTable.Columns("CustomerID"), _  
    custTable.Columns("CompanyName")})  
custDS.Tables("Customers").Constraints.Add(custUnique)  
```  
  
```csharp  
DataTable custTable = custDS.Tables["Customers"];  
UniqueConstraint custUnique = new UniqueConstraint(new DataColumn[]
    {custTable.Columns["CustomerID"],
    custTable.Columns["CompanyName"]});  
custDS.Tables["Customers"].Constraints.Add(custUnique);  
```  
  
## <a name="see-also"></a><span data-ttu-id="533a4-158">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="533a4-158">See also</span></span>

- <xref:System.Data.DataRelation>
- <xref:System.Data.DataTable>
- <xref:System.Data.ForeignKeyConstraint>
- <xref:System.Data.UniqueConstraint>
- [<span data-ttu-id="533a4-159">Définition de schéma de DataTable</span><span class="sxs-lookup"><span data-stu-id="533a4-159">DataTable Schema Definition</span></span>](datatable-schema-definition.md)
- [<span data-ttu-id="533a4-160">DataSets, DataTables et DataViews</span><span class="sxs-lookup"><span data-stu-id="533a4-160">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="533a4-161">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="533a4-161">ADO.NET Overview</span></span>](../ado-net-overview.md)
