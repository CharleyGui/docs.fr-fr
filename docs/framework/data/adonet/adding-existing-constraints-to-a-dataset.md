---
title: Ajout de contraintes existantes à un DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 307d2809-208b-4cf8-b6a9-5d16f15fc16c
ms.openlocfilehash: db072692eba4044e854f25ff2c7f8c9960714018
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785111"
---
# <a name="adding-existing-constraints-to-a-dataset"></a><span data-ttu-id="2aa08-102">Ajout de contraintes existantes à un DataSet</span><span class="sxs-lookup"><span data-stu-id="2aa08-102">Adding Existing Constraints to a DataSet</span></span>
<span data-ttu-id="2aa08-103">La méthode **Fill** du **DataAdapter** remplit uniquement un <xref:System.Data.DataSet> avec les colonnes et les lignes de la table d’une source de données ; bien que les contraintes soient généralement définies par la source de données, la méthode **Fill** n’ajoute pas ces informations de schéma au  **Jeu de données** par défaut.</span><span class="sxs-lookup"><span data-stu-id="2aa08-103">The **Fill** method of the **DataAdapter** fills a <xref:System.Data.DataSet> only with table columns and rows from a data source; though constraints are commonly set by the data source, the **Fill** method does not add this schema information to the **DataSet** by default.</span></span> <span data-ttu-id="2aa08-104">Pour remplir un **DataSet** avec des informations de contrainte de clé primaire existantes à partir d’une source de données, vous pouvez appeler la méthode **FillSchema** du **DataAdapter**ou définir la propriété **MissingSchemaAction** du **DataAdapter** . à **AddWithKey** avant d’appeler **Fill**.</span><span class="sxs-lookup"><span data-stu-id="2aa08-104">To populate a **DataSet** with existing primary key constraint information from a data source, you can either call the **FillSchema** method of the **DataAdapter**, or set the **MissingSchemaAction** property of the **DataAdapter** to **AddWithKey** before calling **Fill**.</span></span> <span data-ttu-id="2aa08-105">Cela permet de s’assurer que les contraintes de clé primaire dans le **DataSet** reflètent celles de la source de données.</span><span class="sxs-lookup"><span data-stu-id="2aa08-105">This will ensure that primary key constraints in the **DataSet** reflect those at the data source.</span></span> <span data-ttu-id="2aa08-106">Les informations de contrainte de clé étrangère ne sont pas incluses et doivent être créées explicitement, comme indiqué dans les [contraintes de DataTable](./dataset-datatable-dataview/datatable-constraints.md).</span><span class="sxs-lookup"><span data-stu-id="2aa08-106">Foreign key constraint information is not included and must be created explicitly, as shown in [DataTable Constraints](./dataset-datatable-dataview/datatable-constraints.md).</span></span>  
  
 <span data-ttu-id="2aa08-107">L’ajout d’informations de schéma à un **DataSet** avant de le remplir avec des données garantit que les contraintes <xref:System.Data.DataTable> de clé primaire sont incluses avec les objets dans le **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="2aa08-107">Adding schema information to a **DataSet** before filling it with data ensures that primary key constraints are included with the <xref:System.Data.DataTable> objects in the **DataSet**.</span></span> <span data-ttu-id="2aa08-108">Par conséquent, lorsque des appels supplémentaires pour remplir le **DataSet** sont effectués, les informations de colonne de clé primaire sont utilisées pour faire correspondre les nouvelles lignes de la source de données avec les lignes actuelles dans chaque **DataTable**, et les données actuelles des tables sont remplacées par les données de la source de données.</span><span class="sxs-lookup"><span data-stu-id="2aa08-108">As a result, when additional calls to fill the **DataSet** are made, the primary key column information is used to match new rows from the data source with current rows in each **DataTable**, and current data in the tables is overwritten with data from the data source.</span></span> <span data-ttu-id="2aa08-109">Sans les informations de schéma, les nouvelles lignes de la source de données sont ajoutées au **DataSet**, ce qui génère des lignes en double.</span><span class="sxs-lookup"><span data-stu-id="2aa08-109">Without the schema information, the new rows from the data source are appended to the **DataSet**, resulting in duplicate rows.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2aa08-110">Si une colonne d’une source de données est identifiée comme auto-incrémentée, la méthode **FillSchema** ou la méthode **Fill** avec un **MissingSchemaAction** de **AddWithKey**crée un **DataColumn** avec une propriété **AutoIncrement** Affectez `true`à la valeur.</span><span class="sxs-lookup"><span data-stu-id="2aa08-110">If a column in a data source is identified as auto-incrementing, the **FillSchema** method, or the **Fill** method with a **MissingSchemaAction** of **AddWithKey**, creates a **DataColumn** with an **AutoIncrement** property set to `true`.</span></span> <span data-ttu-id="2aa08-111">Toutefois, vous devrez définir vous-même les valeurs **AutoIncrementStep** et **AutoIncrementSeed** .</span><span class="sxs-lookup"><span data-stu-id="2aa08-111">However, you will need to set the **AutoIncrementStep** and **AutoIncrementSeed** values yourself.</span></span> <span data-ttu-id="2aa08-112">Pour plus d’informations sur les colonnes à incrémentation automatique, consultez [Creating AutoIncrement Columns](./dataset-datatable-dataview/creating-autoincrement-columns.md).</span><span class="sxs-lookup"><span data-stu-id="2aa08-112">For more information about auto-incrementing columns, see [Creating AutoIncrement Columns](./dataset-datatable-dataview/creating-autoincrement-columns.md).</span></span>  
  
 <span data-ttu-id="2aa08-113">L’utilisation de **FillSchema** ou la définition de **MissingSchemaAction** sur **AddWithKey** nécessite un traitement supplémentaire au niveau de la source de données pour déterminer les informations de colonne de clé primaire.</span><span class="sxs-lookup"><span data-stu-id="2aa08-113">Using **FillSchema** or setting the **MissingSchemaAction** to **AddWithKey** requires extra processing at the data source to determine primary key column information.</span></span> <span data-ttu-id="2aa08-114">Ce traitement supplémentaire peut gêner la performance.</span><span class="sxs-lookup"><span data-stu-id="2aa08-114">This additional processing can hinder performance.</span></span> <span data-ttu-id="2aa08-115">Si vous connaissez les informations de clé primaire au moment du design, il est recommandé de spécifier explicitement la ou les colonnes de clé primaire afin d'atteindre une performance optimale.</span><span class="sxs-lookup"><span data-stu-id="2aa08-115">If you know the primary key information at design time, we recommend that you explicitly specify the primary key column or columns in order to achieve optimal performance.</span></span> <span data-ttu-id="2aa08-116">Pour plus d’informations sur la définition explicite des informations de clé primaire pour une table, consultez [définition des clés primaires](./dataset-datatable-dataview/defining-primary-keys.md).</span><span class="sxs-lookup"><span data-stu-id="2aa08-116">For information about explicitly setting primary key information for a table, see [Defining Primary Keys](./dataset-datatable-dataview/defining-primary-keys.md).</span></span>  
  
 <span data-ttu-id="2aa08-117">L’exemple de code suivant montre comment ajouter des informations de schéma à un **DataSet** à l’aide de **FillSchema**.</span><span class="sxs-lookup"><span data-stu-id="2aa08-117">The following code example shows how to add schema information to a **DataSet** using **FillSchema**.</span></span>  
  
```vb  
Dim custDataSet As DataSet = New DataSet()  
  
custAdapter.FillSchema(custDataSet, SchemaType.Source, "Customers")  
custAdapter.Fill(custDataSet, "Customers")  
```  
  
```csharp  
DataSet custDataSet = new DataSet();  
  
custAdapter.FillSchema(custDataSet, SchemaType.Source, "Customers");  
custAdapter.Fill(custDataSet, "Customers");  
```  
  
 <span data-ttu-id="2aa08-118">L’exemple de code suivant montre comment ajouter des informations de schéma à un **DataSet** à l’aide de la propriété **MissingSchemaAction. AddWithKey** de la méthode **Fill** .</span><span class="sxs-lookup"><span data-stu-id="2aa08-118">The following code example shows how to add schema information to a **DataSet** using the **MissingSchemaAction.AddWithKey** property of the **Fill** method.</span></span>  
  
```vb  
Dim custDataSet As DataSet = New DataSet()  
  
custAdapter.MissingSchemaAction = MissingSchemaAction.AddWithKey  
custAdapter.Fill(custDataSet, "Customers")  
```  
  
```csharp  
DataSet custDataSet = new DataSet();  
  
custAdapter.MissingSchemaAction = MissingSchemaAction.AddWithKey;  
custAdapter.Fill(custDataSet, "Customers");  
```  
  
## <a name="handling-multiple-result-sets"></a><span data-ttu-id="2aa08-119">Gestion de jeux de résultats multiples</span><span class="sxs-lookup"><span data-stu-id="2aa08-119">Handling Multiple Result Sets</span></span>  
 <span data-ttu-id="2aa08-120">Si le **DataAdapter** rencontre plusieurs jeux de résultats retournés par **SelectCommand**, il crée plusieurs tables dans le **jeu de données**.</span><span class="sxs-lookup"><span data-stu-id="2aa08-120">If the **DataAdapter** encounters multiple result sets returned from the **SelectCommand**, it will create multiple tables in the **DataSet**.</span></span> <span data-ttu-id="2aa08-121">Les tables reçoivent un nom incrémentiel par défaut de base zéro de **table** *N*, en commençant par **table** au lieu de « Table0 ».</span><span class="sxs-lookup"><span data-stu-id="2aa08-121">The tables will be given a zero-based incremental default name of **Table** *N*, starting with **Table** instead of "Table0".</span></span> <span data-ttu-id="2aa08-122">Si un nom de table est passé comme argument à la méthode **FillSchema** , les tables reçoivent un nom incrémentiel de base zéro de **TableName** *N*, en commençant par **TableName** au lieu de « TableName0 ».</span><span class="sxs-lookup"><span data-stu-id="2aa08-122">If a table name is passed as an argument to the **FillSchema** method, the tables will be given a zero-based incremental name of **TableName** *N*, starting with **TableName** instead of "TableName0".</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2aa08-123">Si la méthode **FillSchema** de l’objet **OleDbDataAdapter** est appelée pour une commande qui retourne plusieurs jeux de résultats, seules les informations de schéma du premier jeu de résultats sont retournées.</span><span class="sxs-lookup"><span data-stu-id="2aa08-123">If the **FillSchema** method of the **OleDbDataAdapter** object is called for a command that returns multiple result sets, only the schema information from the first result set is returned.</span></span> <span data-ttu-id="2aa08-124">Lors du retour d’informations de schéma pour plusieurs jeux de résultats à l’aide de l' **OleDbDataAdapter**, il est recommandé de spécifier un **MissingSchemaAction** de **AddWithKey** et d’obtenir les informations de schéma lors de l’appel du **remplissage** méthode.</span><span class="sxs-lookup"><span data-stu-id="2aa08-124">When returning schema information for multiple result sets using the **OleDbDataAdapter**, it is recommended that you specify a **MissingSchemaAction** of **AddWithKey** and obtain the schema information when calling the **Fill** method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2aa08-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2aa08-125">See also</span></span>

- [<span data-ttu-id="2aa08-126">DataAdapters et DataReaders</span><span class="sxs-lookup"><span data-stu-id="2aa08-126">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="2aa08-127">DataSets, DataTables et DataViews</span><span class="sxs-lookup"><span data-stu-id="2aa08-127">DataSets, DataTables, and DataViews</span></span>](./dataset-datatable-dataview/index.md)
- [<span data-ttu-id="2aa08-128">Extraction et modification de données dans ADO.NET</span><span class="sxs-lookup"><span data-stu-id="2aa08-128">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)
- [<span data-ttu-id="2aa08-129">Vue d’ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="2aa08-129">ADO.NET Overview</span></span>](ado-net-overview.md)
