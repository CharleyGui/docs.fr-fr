---
title: Ajout de contraintes existantes à un DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 307d2809-208b-4cf8-b6a9-5d16f15fc16c
ms.openlocfilehash: 267d6489d39f86fc06b35de8cf30dad74f501b0b
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72523236"
---
# <a name="adding-existing-constraints-to-a-dataset"></a>Ajout de contraintes existantes à un DataSet

La méthode **Fill** du **DataAdapter** remplit un <xref:System.Data.DataSet> uniquement avec les colonnes et les lignes de la table d’une source de données ; Bien que les contraintes soient généralement définies par la source de données, la méthode **Fill** n’ajoute pas ces informations de schéma au **DataSet** par défaut. Pour remplir un **DataSet** avec des informations de contrainte de clé primaire existantes à partir d’une source de données, vous pouvez appeler la méthode **FillSchema** du **DataAdapter**ou définir la propriété **MissingSchemaAction** du **DataAdapter** . à **AddWithKey** avant d’appeler **Fill**. Cela permet de s’assurer que les contraintes de clé primaire dans le **DataSet** reflètent celles de la source de données. Les informations de contrainte de clé étrangère ne sont pas incluses et doivent être créées explicitement, comme indiqué dans les [contraintes de DataTable](./dataset-datatable-dataview/datatable-constraints.md).  
  
L’ajout d’informations de schéma à un **DataSet** avant de le remplir avec des données garantit que les contraintes de clé primaire sont incluses avec les objets <xref:System.Data.DataTable> dans le **jeu**de données. Par conséquent, lorsque des appels supplémentaires pour remplir le **DataSet** sont effectués, les informations de colonne de clé primaire sont utilisées pour faire correspondre les nouvelles lignes de la source de données avec les lignes actuelles dans chaque **DataTable**, et les données actuelles des tables sont remplacées par les données de la source de données. Sans les informations de schéma, les nouvelles lignes de la source de données sont ajoutées au **DataSet**, ce qui génère des lignes en double.  
  
> [!NOTE]
> Si une colonne d’une source de données est identifiée comme auto-incrémentée, la méthode **FillSchema** ou la méthode **Fill** avec un **MissingSchemaAction** de **AddWithKey**crée un **DataColumn** avec une propriété **AutoIncrement** définissez sur `true`. Toutefois, vous devrez définir vous-même les valeurs **AutoIncrementStep** et **AutoIncrementSeed** . Pour plus d’informations sur les colonnes à incrémentation automatique, consultez [Creating AutoIncrement Columns](./dataset-datatable-dataview/creating-autoincrement-columns.md).  
  
L’utilisation de **FillSchema** ou la définition de **MissingSchemaAction** sur **AddWithKey** nécessite un traitement supplémentaire au niveau de la source de données pour déterminer les informations de colonne de clé primaire. Ce traitement supplémentaire peut gêner la performance. Si vous connaissez les informations de clé primaire au moment du design, il est recommandé de spécifier explicitement la ou les colonnes de clé primaire afin d'atteindre une performance optimale. Pour plus d’informations sur la définition explicite des informations de clé primaire pour une table, consultez [définition des clés primaires](./dataset-datatable-dataview/defining-primary-keys.md).
  
L’exemple de code suivant montre comment ajouter des informations de schéma à un **DataSet** à l’aide de **FillSchema**:
  
```vb  
Dim custDataSet As New DataSet()  
  
custAdapter.FillSchema(custDataSet, SchemaType.Source, "Customers")  
custAdapter.Fill(custDataSet, "Customers")  
```  
  
```csharp  
var custDataSet = new DataSet();  
  
custAdapter.FillSchema(custDataSet, SchemaType.Source, "Customers");  
custAdapter.Fill(custDataSet, "Customers");  
```  
  
L’exemple de code suivant montre comment ajouter des informations de schéma à un **DataSet** à l’aide de la propriété **MissingSchemaAction. AddWithKey** de la méthode **Fill** :
  
```vb  
Dim custDataSet As New DataSet()  
  
custAdapter.MissingSchemaAction = MissingSchemaAction.AddWithKey  
custAdapter.Fill(custDataSet, "Customers")  
```  
  
```csharp  
var custDataSet = new DataSet();  
  
custAdapter.MissingSchemaAction = MissingSchemaAction.AddWithKey;  
custAdapter.Fill(custDataSet, "Customers");  
```  
  
## <a name="handling-multiple-result-sets"></a>Gestion de jeux de résultats multiples  

Si le **DataAdapter** rencontre plusieurs jeux de résultats retournés par **SelectCommand**, il crée plusieurs tables dans le **jeu de données**. Les tables reçoivent un nom incrémentiel par défaut de base zéro de **table** *N*, en commençant par **table** au lieu de « Table0 ». Si un nom de table est passé comme argument à la méthode **FillSchema** , les tables reçoivent un nom incrémentiel de base zéro de **TableName** *N*, en commençant par **TableName** au lieu de « TableName0 ».  
  
> [!NOTE]
> Si la méthode **FillSchema** de l’objet **OleDbDataAdapter** est appelée pour une commande qui retourne plusieurs jeux de résultats, seules les informations de schéma du premier jeu de résultats sont retournées. Lors du retour d’informations de schéma pour plusieurs jeux de résultats à l’aide de l' **OleDbDataAdapter**, il est recommandé de spécifier un **MissingSchemaAction** de **AddWithKey** et d’obtenir les informations de schéma lors de l’appel du **remplissage** méthode.  
  
## <a name="see-also"></a>Voir aussi

- [DataAdapters et DataReaders](dataadapters-and-datareaders.md)
- [DataSets, DataTables et DataViews](./dataset-datatable-dataview/index.md)
- [Extraction et modification de données dans ADO.NET](retrieving-and-modifying-data.md)
- [Vue d’ensemble d’ADO.NET](ado-net-overview.md)
