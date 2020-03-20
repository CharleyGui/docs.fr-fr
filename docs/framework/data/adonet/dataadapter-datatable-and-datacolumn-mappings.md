---
title: Mappages de DataAdapter DataTable et DataColumn
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d023260a-a66a-4c39-b8f4-090cd130e730
ms.openlocfilehash: 6380dd0512bd7834f50b87f90f445cb01b7a8b95
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151557"
---
# <a name="dataadapter-datatable-and-datacolumn-mappings"></a><span data-ttu-id="d2beb-102">Mappages de DataAdapter DataTable et DataColumn</span><span class="sxs-lookup"><span data-stu-id="d2beb-102">DataAdapter DataTable and DataColumn Mappings</span></span>
<span data-ttu-id="d2beb-103">Un **DataAdapter** contient une collection <xref:System.Data.Common.DataTableMapping> d’objets nuls ou plus dans sa propriété **TableMappings.**</span><span class="sxs-lookup"><span data-stu-id="d2beb-103">A **DataAdapter** contains a collection of zero or more <xref:System.Data.Common.DataTableMapping> objects in its **TableMappings** property.</span></span> <span data-ttu-id="d2beb-104">Un **DataTableMapping** fournit une cartographie principale entre les données retournées <xref:System.Data.DataTable>à partir d’une requête contre une source de données, et un .</span><span class="sxs-lookup"><span data-stu-id="d2beb-104">A **DataTableMapping** provides a master mapping between the data returned from a query against a data source, and a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="d2beb-105">Le nom **DataTableMapping** peut être transmis à la place du nom **DataTable** à la méthode **De remplissage** du **DataAdapter**.</span><span class="sxs-lookup"><span data-stu-id="d2beb-105">The **DataTableMapping** name can be passed in place of the **DataTable** name to the **Fill** method of the **DataAdapter**.</span></span> <span data-ttu-id="d2beb-106">L’exemple suivant crée un **DataTableMapping** nommé **AuthorsMapping** pour la table **des auteurs.**</span><span class="sxs-lookup"><span data-stu-id="d2beb-106">The following example creates a **DataTableMapping** named **AuthorsMapping** for the **Authors** table.</span></span>  
  
```vb  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors")  
```  
  
```csharp  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors");  
```  
  
 <span data-ttu-id="d2beb-107">Un **DataTableMapping** vous permet d’utiliser des noms de colonnes dans un **DataTable** qui sont différents de ceux de la base de données.</span><span class="sxs-lookup"><span data-stu-id="d2beb-107">A **DataTableMapping** enables you to use column names in a **DataTable** that are different from those in the database.</span></span> <span data-ttu-id="d2beb-108">Le **DataAdapter** utilise la cartographie pour correspondre aux colonnes lorsque la table est mise à jour.</span><span class="sxs-lookup"><span data-stu-id="d2beb-108">The **DataAdapter** uses the mapping to match the columns when the table is updated.</span></span>  
  
 <span data-ttu-id="d2beb-109">Si vous ne spécifiez pas un **nom TableName** ou un nom **DataTableMapping** lors de l’appel de la méthode **De remplissage** ou de mise **à jour** du **DataAdapter**, le **DataAdapter** recherche un **DataTableMapping** nommé "Table".</span><span class="sxs-lookup"><span data-stu-id="d2beb-109">If you do not specify a **TableName** or a **DataTableMapping** name when calling the **Fill** or **Update** method of the **DataAdapter**, the **DataAdapter** looks for a **DataTableMapping** named "Table".</span></span> <span data-ttu-id="d2beb-110">Si celui **DataTableMapping n’existe** pas, le Nom de **table** de la **Table est** "Table".</span><span class="sxs-lookup"><span data-stu-id="d2beb-110">If that **DataTableMapping** does not exist, the **TableName** of the **DataTable** is "Table".</span></span> <span data-ttu-id="d2beb-111">Vous pouvez spécifier un défaut **DataTableMapping** en créant un **DataTableMapping** avec le nom de "Table".</span><span class="sxs-lookup"><span data-stu-id="d2beb-111">You can specify a default **DataTableMapping** by creating a **DataTableMapping** with the name of "Table".</span></span>  
  
 <span data-ttu-id="d2beb-112">L’exemple de code suivant crée un <xref:System.Data.Common> **DataTableMapping** (à partir de l’espace de nom) et en fait la cartographie par défaut pour le **DataAdapter** spécifié en le nommant "Table".</span><span class="sxs-lookup"><span data-stu-id="d2beb-112">The following code example creates a **DataTableMapping** (from the <xref:System.Data.Common> namespace) and makes it the default mapping for the specified **DataAdapter** by naming it "Table".</span></span> <span data-ttu-id="d2beb-113">L’exemple cartographie ensuite les colonnes du premier tableau du résultat de la requête (la table **des clients** de la base de données **Northwind)** à un ensemble de noms plus conviviaux dans le tableau **des clients Northwind** dans le <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="d2beb-113">The example then maps the columns from the first table in the query result (the **Customers** table of the **Northwind** database) to a set of more user-friendly names in the **Northwind Customers** table in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="d2beb-114">Pour les colonnes qui ne sont pas mappées, le nom de la colonne de la source de données est utilisé.</span><span class="sxs-lookup"><span data-stu-id="d2beb-114">For columns that are not mapped, the name of the column from the data source is used.</span></span>  
  
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
  
 <span data-ttu-id="d2beb-115">Dans des situations plus avancées, vous pouvez décider que vous voulez que le même **DataAdapter** supporte le chargement de différentes tables avec différentes cartes.</span><span class="sxs-lookup"><span data-stu-id="d2beb-115">In more advanced situations, you may decide that you want the same **DataAdapter** to support loading different tables with different mappings.</span></span> <span data-ttu-id="d2beb-116">Pour ce faire, il suffit d’ajouter des objets **De dataTableMapping** supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="d2beb-116">To do this, simply add additional **DataTableMapping** objects.</span></span>  
  
 <span data-ttu-id="d2beb-117">Lorsque la méthode **De remplissage** est adoptée, une instance d’un **DataSet** et d’un nom **DataTableMapping,** si une cartographie avec ce nom existe, elle est utilisée; autrement, un **DataTable** avec ce nom est utilisé.</span><span class="sxs-lookup"><span data-stu-id="d2beb-117">When the **Fill** method is passed an instance of a **DataSet** and a **DataTableMapping** name, if a mapping with that name exists it is used; otherwise, a **DataTable** with that name is used.</span></span>  
  
 <span data-ttu-id="d2beb-118">Les exemples suivants créent un **DataTableMapping** avec un nom de **clients** et un nom **DataTable** de **BizTalkSchema**.</span><span class="sxs-lookup"><span data-stu-id="d2beb-118">The following examples create a **DataTableMapping** with a name of **Customers** and a **DataTable** name of **BizTalkSchema**.</span></span> <span data-ttu-id="d2beb-119">L’exemple cartographie ensuite les lignes retournées par la déclaration SELECT à la **BizTalkSchema** **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="d2beb-119">The example then maps the rows returned by the SELECT statement to the **BizTalkSchema** **DataTable**.</span></span>  
  
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
> <span data-ttu-id="d2beb-120">Si aucun nom de colonne source n'est fourni pour un mappage de colonne ou aucun nom de table source n'est fourni pour un mappage de table, les noms par défaut sont automatiquement générés.</span><span class="sxs-lookup"><span data-stu-id="d2beb-120">If a source column name is not supplied for a column mapping or a source table name is not supplied for a table mapping, default names will be automatically generated.</span></span> <span data-ttu-id="d2beb-121">Si aucune colonne source n’est fournie pour une cartographie de colonne, la cartographie de colonne est donnée un nom par défaut progressif de **SourceColumn** *N,* à commencer par **SourceColumn1**.</span><span class="sxs-lookup"><span data-stu-id="d2beb-121">If no source column is supplied for a column mapping, the column mapping is given an incremental default name of **SourceColumn** *N,* starting with **SourceColumn1**.</span></span> <span data-ttu-id="d2beb-122">Si aucun nom de table source n’est fourni pour une cartographie de table, la cartographie de table est donnée un nom par défaut progressif de **SourceTable** *N*, à commencer par **SourceTable1**.</span><span class="sxs-lookup"><span data-stu-id="d2beb-122">If no source table name is supplied for a table mapping, the table mapping is given an incremental default name of **SourceTable** *N*, starting with **SourceTable1**.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d2beb-123">Nous vous recommandons d’éviter la convention de nommage de **SourceColumn** *N* pour une cartographie de colonne, ou **SourceTable** *N* pour une cartographie de table, parce que le nom que vous fournissez peut entrer en conflit avec un nom de cartographie de colonne par défaut existant dans le **ColumnMappingCollection** ou nom de cartographie de table dans le **DataTableMappingCollection**.</span><span class="sxs-lookup"><span data-stu-id="d2beb-123">We recommend that you avoid the naming convention of **SourceColumn** *N* for a column mapping, or **SourceTable** *N* for a table mapping, because the name you supply may conflict with an existing default column mapping name in the **ColumnMappingCollection** or table mapping name in the **DataTableMappingCollection**.</span></span> <span data-ttu-id="d2beb-124">Si le nom fourni existe déjà, une exception sera levée.</span><span class="sxs-lookup"><span data-stu-id="d2beb-124">If the supplied name already exists, an exception will be thrown.</span></span>  
  
## <a name="handling-multiple-result-sets"></a><span data-ttu-id="d2beb-125">Gestion de jeux de résultats multiples</span><span class="sxs-lookup"><span data-stu-id="d2beb-125">Handling Multiple Result Sets</span></span>  
 <span data-ttu-id="d2beb-126">Si votre **SelectCommand** retourne plusieurs tables, **Fill** génère automatiquement des noms de table avec des valeurs incrémentielles pour les tables dans le **DataSet**, en commençant par le nom de table spécifié et en continuant sous la forme **TableName** *N*, à commencer par **TableName1**.</span><span class="sxs-lookup"><span data-stu-id="d2beb-126">If your **SelectCommand** returns multiple tables, **Fill** automatically generates table names with incremental values for the tables in the **DataSet**, starting with the specified table name and continuing on in the form **TableName** *N*, starting with **TableName1**.</span></span> <span data-ttu-id="d2beb-127">Vous pouvez utiliser des cartes de table pour cartographier le nom de table généré automatiquement à un nom que vous souhaitez spécifié pour la table dans le **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="d2beb-127">You can use table mappings to map the automatically generated table name to a name you want specified for the table in the **DataSet**.</span></span> <span data-ttu-id="d2beb-128">Par exemple, pour un **SelectCommand** qui renvoie deux tables, **clients** et **commandes,** émettent l’appel suivant à **Remplir**.</span><span class="sxs-lookup"><span data-stu-id="d2beb-128">For example, for a **SelectCommand** that returns two tables, **Customers** and **Orders**, issue the following call to **Fill**.</span></span>  
  
```vb  
adapter.Fill(customersDataSet, "Customers")  
```  

```csharp  
adapter.Fill(customersDataSet, "Customers");  
```  

 <span data-ttu-id="d2beb-129">Deux tables sont créées dans le **DataSet**: **Clients** et **Clients1**.</span><span class="sxs-lookup"><span data-stu-id="d2beb-129">Two tables are created in the **DataSet**: **Customers** and **Customers1**.</span></span> <span data-ttu-id="d2beb-130">Vous pouvez utiliser des cartes de table pour vous assurer que la deuxième table est nommée **Commandes** au lieu de **Customers1**.</span><span class="sxs-lookup"><span data-stu-id="d2beb-130">You can use table mappings to ensure that the second table is named **Orders** instead of **Customers1**.</span></span> <span data-ttu-id="d2beb-131">Pour ce faire, cartographiez le tableau source des **clients1** sur les **commandes**de table **DataSet,** comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="d2beb-131">To do this, map the source table of **Customers1** to the **DataSet** table **Orders**, as shown in the following example.</span></span>  
  
```vb  
adapter.TableMappings.Add("Customers1", "Orders")  
adapter.Fill(customersDataSet, "Customers")  
```  

```csharp  
adapter.TableMappings.Add("Customers1", "Orders");  
adapter.Fill(customersDataSet, "Customers");  
```
  
## <a name="see-also"></a><span data-ttu-id="d2beb-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d2beb-132">See also</span></span>

- [<span data-ttu-id="d2beb-133">DataAdapters et DataReaders</span><span class="sxs-lookup"><span data-stu-id="d2beb-133">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="d2beb-134">Extraction et modification de données dans ADO.NET</span><span class="sxs-lookup"><span data-stu-id="d2beb-134">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)
- [<span data-ttu-id="d2beb-135">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="d2beb-135">ADO.NET Overview</span></span>](ado-net-overview.md)
