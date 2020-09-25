---
title: Mappages de DataAdapter DataTable et DataColumn
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d023260a-a66a-4c39-b8f4-090cd130e730
ms.openlocfilehash: b979431836b55b23ac9ba6ec4535f33765dce555
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177733"
---
# <a name="dataadapter-datatable-and-datacolumn-mappings"></a><span data-ttu-id="bbba1-102">Mappages de DataAdapter DataTable et DataColumn</span><span class="sxs-lookup"><span data-stu-id="bbba1-102">DataAdapter DataTable and DataColumn Mappings</span></span>

<span data-ttu-id="bbba1-103">Un **DataAdapter** contient une collection de zéro ou plusieurs <xref:System.Data.Common.DataTableMapping> objets dans sa propriété **TableMappings** .</span><span class="sxs-lookup"><span data-stu-id="bbba1-103">A **DataAdapter** contains a collection of zero or more <xref:System.Data.Common.DataTableMapping> objects in its **TableMappings** property.</span></span> <span data-ttu-id="bbba1-104">Un **DataTableMapping** fournit un mappage principal entre les données retournées par une requête sur une source de données et un <xref:System.Data.DataTable> .</span><span class="sxs-lookup"><span data-stu-id="bbba1-104">A **DataTableMapping** provides a master mapping between the data returned from a query against a data source, and a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="bbba1-105">Le nom **DataTableMapping** peut être passé à la place du nom du **DataTable** à la méthode **Fill** du **DataAdapter**.</span><span class="sxs-lookup"><span data-stu-id="bbba1-105">The **DataTableMapping** name can be passed in place of the **DataTable** name to the **Fill** method of the **DataAdapter**.</span></span> <span data-ttu-id="bbba1-106">L’exemple suivant crée un **DataTableMapping** nommé **AuthorsMapping** pour la table **Authors** .</span><span class="sxs-lookup"><span data-stu-id="bbba1-106">The following example creates a **DataTableMapping** named **AuthorsMapping** for the **Authors** table.</span></span>  
  
```vb  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors")  
```  
  
```csharp  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors");  
```  
  
 <span data-ttu-id="bbba1-107">Un **DataTableMapping** vous permet d’utiliser des noms de colonnes dans un **DataTable** qui sont différents de ceux de la base de données.</span><span class="sxs-lookup"><span data-stu-id="bbba1-107">A **DataTableMapping** enables you to use column names in a **DataTable** that are different from those in the database.</span></span> <span data-ttu-id="bbba1-108">Le **DataAdapter** utilise le mappage pour faire correspondre les colonnes lorsque la table est mise à jour.</span><span class="sxs-lookup"><span data-stu-id="bbba1-108">The **DataAdapter** uses the mapping to match the columns when the table is updated.</span></span>  
  
 <span data-ttu-id="bbba1-109">Si vous ne spécifiez pas de nom **TableName** ou **DataTableMapping** lors de l’appel de la méthode **Fill** ou **Update** du **DataAdapter**, le **DataAdapter** recherche un **DataTableMapping** nommé « table ».</span><span class="sxs-lookup"><span data-stu-id="bbba1-109">If you do not specify a **TableName** or a **DataTableMapping** name when calling the **Fill** or **Update** method of the **DataAdapter**, the **DataAdapter** looks for a **DataTableMapping** named "Table".</span></span> <span data-ttu-id="bbba1-110">Si ce **DataTableMapping** n’existe pas, le **TableName** du **DataTable** est « table ».</span><span class="sxs-lookup"><span data-stu-id="bbba1-110">If that **DataTableMapping** does not exist, the **TableName** of the **DataTable** is "Table".</span></span> <span data-ttu-id="bbba1-111">Vous pouvez spécifier un **DataTableMapping** par défaut en créant un **DataTableMapping** portant le nom « table ».</span><span class="sxs-lookup"><span data-stu-id="bbba1-111">You can specify a default **DataTableMapping** by creating a **DataTableMapping** with the name of "Table".</span></span>  
  
 <span data-ttu-id="bbba1-112">L’exemple de code suivant crée un **DataTableMapping** (à partir de l' <xref:System.Data.Common> espace de noms) et en fait le mappage par défaut pour le **DataAdapter** spécifié en le nommant « table ».</span><span class="sxs-lookup"><span data-stu-id="bbba1-112">The following code example creates a **DataTableMapping** (from the <xref:System.Data.Common> namespace) and makes it the default mapping for the specified **DataAdapter** by naming it "Table".</span></span> <span data-ttu-id="bbba1-113">L’exemple mappe ensuite les colonnes de la première table du résultat de la requête (la table **Customers** de la base de données **Northwind** ) à un ensemble de noms plus conviviaux dans la table **Customers de Northwind** dans le <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="bbba1-113">The example then maps the columns from the first table in the query result (the **Customers** table of the **Northwind** database) to a set of more user-friendly names in the **Northwind Customers** table in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="bbba1-114">Pour les colonnes qui ne sont pas mappées, le nom de la colonne de la source de données est utilisé.</span><span class="sxs-lookup"><span data-stu-id="bbba1-114">For columns that are not mapped, the name of the column from the data source is used.</span></span>  
  
```vb  
Dim mapping As DataTableMapping = _  
  adapter.TableMappings.Add("Table", "NorthwindCustomers")  
mapping.ColumnMappings.Add("CompanyName", "Company")  
mapping.ColumnMappings.Add("ContactName", "Contact")  
mapping.ColumnMappings.Add("PostalCode", "ZIPCode")  
  
adapter.Fill(custDS)  
```  
  
```csharp  
DataTableMapping mapping =
  adapter.TableMappings.Add("Table", "NorthwindCustomers");  
mapping.ColumnMappings.Add("CompanyName", "Company");  
mapping.ColumnMappings.Add("ContactName", "Contact");  
mapping.ColumnMappings.Add("PostalCode", "ZIPCode");  
  
adapter.Fill(custDS);  
```  
  
 <span data-ttu-id="bbba1-115">Dans les situations plus avancées, vous pouvez décider que vous souhaitez que le même **DataAdapter** prenne en charge le chargement de différentes tables avec des mappages différents.</span><span class="sxs-lookup"><span data-stu-id="bbba1-115">In more advanced situations, you may decide that you want the same **DataAdapter** to support loading different tables with different mappings.</span></span> <span data-ttu-id="bbba1-116">Pour ce faire, ajoutez simplement des objets **DataTableMapping** supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="bbba1-116">To do this, simply add additional **DataTableMapping** objects.</span></span>  
  
 <span data-ttu-id="bbba1-117">Quand la méthode **Fill** reçoit une instance d’un **DataSet** et un nom **DataTableMapping** , si un mappage portant ce nom existe, il est utilisé ; dans le cas contraire, un **DataTable** portant ce nom est utilisé.</span><span class="sxs-lookup"><span data-stu-id="bbba1-117">When the **Fill** method is passed an instance of a **DataSet** and a **DataTableMapping** name, if a mapping with that name exists it is used; otherwise, a **DataTable** with that name is used.</span></span>  
  
 <span data-ttu-id="bbba1-118">Les exemples suivants créent un **DataTableMapping** avec un nom **Customers** et un nom **DataTable** **BizTalkSchema**.</span><span class="sxs-lookup"><span data-stu-id="bbba1-118">The following examples create a **DataTableMapping** with a name of **Customers** and a **DataTable** name of **BizTalkSchema**.</span></span> <span data-ttu-id="bbba1-119">L’exemple mappe ensuite les lignes retournées par l’instruction SELECT au **DataTable** **BizTalkSchema** .</span><span class="sxs-lookup"><span data-stu-id="bbba1-119">The example then maps the rows returned by the SELECT statement to the **BizTalkSchema** **DataTable**.</span></span>  
  
```vb  
Dim mapping As ITableMapping = _  
  adapter.TableMappings.Add("Customers", "BizTalkSchema")  
mapping.ColumnMappings.Add("CustomerID", "ClientID")  
mapping.ColumnMappings.Add("CompanyName", "ClientName")  
mapping.ColumnMappings.Add("ContactName", "Contact")  
mapping.ColumnMappings.Add("PostalCode", "ZIP")  
  
adapter.Fill(custDS, "Customers")  
```  
  
```csharp  
ITableMapping mapping =
  adapter.TableMappings.Add("Customers", "BizTalkSchema");  
mapping.ColumnMappings.Add("CustomerID", "ClientID");  
mapping.ColumnMappings.Add("CompanyName", "ClientName");  
mapping.ColumnMappings.Add("ContactName", "Contact");  
mapping.ColumnMappings.Add("PostalCode", "ZIP");  
  
adapter.Fill(custDS, "Customers");  
```  
  
> [!NOTE]
> <span data-ttu-id="bbba1-120">Si aucun nom de colonne source n'est fourni pour un mappage de colonne ou aucun nom de table source n'est fourni pour un mappage de table, les noms par défaut sont automatiquement générés.</span><span class="sxs-lookup"><span data-stu-id="bbba1-120">If a source column name is not supplied for a column mapping or a source table name is not supplied for a table mapping, default names will be automatically generated.</span></span> <span data-ttu-id="bbba1-121">Si aucune colonne source n’est fournie pour un mappage de colonnes, le mappage de colonnes reçoit un nom incrémentiel par défaut de **SourceColumn** *N,* en commençant par **SourceColumn1**.</span><span class="sxs-lookup"><span data-stu-id="bbba1-121">If no source column is supplied for a column mapping, the column mapping is given an incremental default name of **SourceColumn** *N,* starting with **SourceColumn1**.</span></span> <span data-ttu-id="bbba1-122">Si aucun nom de table source n’est fourni pour un mappage de table, le mappage de table reçoit un nom incrémentiel par défaut de **SourceTable** *N*, en commençant par **SourceTable1**.</span><span class="sxs-lookup"><span data-stu-id="bbba1-122">If no source table name is supplied for a table mapping, the table mapping is given an incremental default name of **SourceTable** *N*, starting with **SourceTable1**.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bbba1-123">Nous vous recommandons d’éviter la Convention d’affectation de noms de **SourceColumn** *n* pour un mappage de colonnes, ou **SourceTable** *n* pour un mappage de table, car le nom que vous fournissez peut être en conflit avec un nom de mappage de colonne par défaut existant dans le **ColumnMappingCollection** ou le nom de mappage de table dans le **DataTableMappingCollection**.</span><span class="sxs-lookup"><span data-stu-id="bbba1-123">We recommend that you avoid the naming convention of **SourceColumn** *N* for a column mapping, or **SourceTable** *N* for a table mapping, because the name you supply may conflict with an existing default column mapping name in the **ColumnMappingCollection** or table mapping name in the **DataTableMappingCollection**.</span></span> <span data-ttu-id="bbba1-124">Si le nom fourni existe déjà, une exception sera levée.</span><span class="sxs-lookup"><span data-stu-id="bbba1-124">If the supplied name already exists, an exception will be thrown.</span></span>  
  
## <a name="handling-multiple-result-sets"></a><span data-ttu-id="bbba1-125">Gestion de jeux de résultats multiples</span><span class="sxs-lookup"><span data-stu-id="bbba1-125">Handling Multiple Result Sets</span></span>  

 <span data-ttu-id="bbba1-126">Si votre **SelectCommand** retourne plusieurs tables, **Fill** génère automatiquement des noms de table avec des valeurs incrémentielles pour les tables du **DataSet**, en commençant par le nom de table spécifié et en continuant sous la forme **TableName** *N*, en commençant par **TableName1**.</span><span class="sxs-lookup"><span data-stu-id="bbba1-126">If your **SelectCommand** returns multiple tables, **Fill** automatically generates table names with incremental values for the tables in the **DataSet**, starting with the specified table name and continuing on in the form **TableName** *N*, starting with **TableName1**.</span></span> <span data-ttu-id="bbba1-127">Vous pouvez utiliser des mappages de table pour mapper le nom de table généré automatiquement à un nom que vous souhaitez spécifier pour la table dans le **jeu de données**.</span><span class="sxs-lookup"><span data-stu-id="bbba1-127">You can use table mappings to map the automatically generated table name to a name you want specified for the table in the **DataSet**.</span></span> <span data-ttu-id="bbba1-128">Par exemple, pour un **SelectCommand** qui retourne deux tables, **Customers** et **Orders**, émettez l’appel suivant à **Fill**.</span><span class="sxs-lookup"><span data-stu-id="bbba1-128">For example, for a **SelectCommand** that returns two tables, **Customers** and **Orders**, issue the following call to **Fill**.</span></span>  
  
```vb  
adapter.Fill(customersDataSet, "Customers")  
```  

```csharp  
adapter.Fill(customersDataSet, "Customers");  
```  

 <span data-ttu-id="bbba1-129">Deux tables sont créées dans le **jeu de données**: **Customers** et **Customers1**.</span><span class="sxs-lookup"><span data-stu-id="bbba1-129">Two tables are created in the **DataSet**: **Customers** and **Customers1**.</span></span> <span data-ttu-id="bbba1-130">Vous pouvez utiliser des mappages de table pour vous assurer que la deuxième table est nommée **Orders** au lieu de **Customers1**.</span><span class="sxs-lookup"><span data-stu-id="bbba1-130">You can use table mappings to ensure that the second table is named **Orders** instead of **Customers1**.</span></span> <span data-ttu-id="bbba1-131">Pour ce faire, mappez la table source de **Customers1** à la table **Orders**du **DataSet** , comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="bbba1-131">To do this, map the source table of **Customers1** to the **DataSet** table **Orders**, as shown in the following example.</span></span>  
  
```vb  
adapter.TableMappings.Add("Customers1", "Orders")  
adapter.Fill(customersDataSet, "Customers")  
```  

```csharp  
adapter.TableMappings.Add("Customers1", "Orders");  
adapter.Fill(customersDataSet, "Customers");  
```
  
## <a name="see-also"></a><span data-ttu-id="bbba1-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bbba1-132">See also</span></span>

- [<span data-ttu-id="bbba1-133">DataAdapters et DataReaders</span><span class="sxs-lookup"><span data-stu-id="bbba1-133">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="bbba1-134">Extraction et modification de données dans ADO.NET</span><span class="sxs-lookup"><span data-stu-id="bbba1-134">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)
- [<span data-ttu-id="bbba1-135">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="bbba1-135">ADO.NET Overview</span></span>](ado-net-overview.md)
