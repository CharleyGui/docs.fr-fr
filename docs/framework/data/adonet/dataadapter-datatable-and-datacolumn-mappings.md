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
# <a name="dataadapter-datatable-and-datacolumn-mappings"></a>Mappages de DataAdapter DataTable et DataColumn

Un **DataAdapter** contient une collection de zéro ou plusieurs <xref:System.Data.Common.DataTableMapping> objets dans sa propriété **TableMappings** . Un **DataTableMapping** fournit un mappage principal entre les données retournées par une requête sur une source de données et un <xref:System.Data.DataTable> . Le nom **DataTableMapping** peut être passé à la place du nom du **DataTable** à la méthode **Fill** du **DataAdapter**. L’exemple suivant crée un **DataTableMapping** nommé **AuthorsMapping** pour la table **Authors** .  
  
```vb  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors")  
```  
  
```csharp  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors");  
```  
  
 Un **DataTableMapping** vous permet d’utiliser des noms de colonnes dans un **DataTable** qui sont différents de ceux de la base de données. Le **DataAdapter** utilise le mappage pour faire correspondre les colonnes lorsque la table est mise à jour.  
  
 Si vous ne spécifiez pas de nom **TableName** ou **DataTableMapping** lors de l’appel de la méthode **Fill** ou **Update** du **DataAdapter**, le **DataAdapter** recherche un **DataTableMapping** nommé « table ». Si ce **DataTableMapping** n’existe pas, le **TableName** du **DataTable** est « table ». Vous pouvez spécifier un **DataTableMapping** par défaut en créant un **DataTableMapping** portant le nom « table ».  
  
 L’exemple de code suivant crée un **DataTableMapping** (à partir de l' <xref:System.Data.Common> espace de noms) et en fait le mappage par défaut pour le **DataAdapter** spécifié en le nommant « table ». L’exemple mappe ensuite les colonnes de la première table du résultat de la requête (la table **Customers** de la base de données **Northwind** ) à un ensemble de noms plus conviviaux dans la table **Customers de Northwind** dans le <xref:System.Data.DataSet> . Pour les colonnes qui ne sont pas mappées, le nom de la colonne de la source de données est utilisé.  
  
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
  
 Dans les situations plus avancées, vous pouvez décider que vous souhaitez que le même **DataAdapter** prenne en charge le chargement de différentes tables avec des mappages différents. Pour ce faire, ajoutez simplement des objets **DataTableMapping** supplémentaires.  
  
 Quand la méthode **Fill** reçoit une instance d’un **DataSet** et un nom **DataTableMapping** , si un mappage portant ce nom existe, il est utilisé ; dans le cas contraire, un **DataTable** portant ce nom est utilisé.  
  
 Les exemples suivants créent un **DataTableMapping** avec un nom **Customers** et un nom **DataTable** **BizTalkSchema**. L’exemple mappe ensuite les lignes retournées par l’instruction SELECT au **DataTable** **BizTalkSchema** .  
  
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
> Si aucun nom de colonne source n'est fourni pour un mappage de colonne ou aucun nom de table source n'est fourni pour un mappage de table, les noms par défaut sont automatiquement générés. Si aucune colonne source n’est fournie pour un mappage de colonnes, le mappage de colonnes reçoit un nom incrémentiel par défaut de **SourceColumn** *N,* en commençant par **SourceColumn1**. Si aucun nom de table source n’est fourni pour un mappage de table, le mappage de table reçoit un nom incrémentiel par défaut de **SourceTable** *N*, en commençant par **SourceTable1**.  
  
> [!NOTE]
> Nous vous recommandons d’éviter la Convention d’affectation de noms de **SourceColumn** *n* pour un mappage de colonnes, ou **SourceTable** *n* pour un mappage de table, car le nom que vous fournissez peut être en conflit avec un nom de mappage de colonne par défaut existant dans le **ColumnMappingCollection** ou le nom de mappage de table dans le **DataTableMappingCollection**. Si le nom fourni existe déjà, une exception sera levée.  
  
## <a name="handling-multiple-result-sets"></a>Gestion de jeux de résultats multiples  

 Si votre **SelectCommand** retourne plusieurs tables, **Fill** génère automatiquement des noms de table avec des valeurs incrémentielles pour les tables du **DataSet**, en commençant par le nom de table spécifié et en continuant sous la forme **TableName** *N*, en commençant par **TableName1**. Vous pouvez utiliser des mappages de table pour mapper le nom de table généré automatiquement à un nom que vous souhaitez spécifier pour la table dans le **jeu de données**. Par exemple, pour un **SelectCommand** qui retourne deux tables, **Customers** et **Orders**, émettez l’appel suivant à **Fill**.  
  
```vb  
adapter.Fill(customersDataSet, "Customers")  
```  

```csharp  
adapter.Fill(customersDataSet, "Customers");  
```  

 Deux tables sont créées dans le **jeu de données**: **Customers** et **Customers1**. Vous pouvez utiliser des mappages de table pour vous assurer que la deuxième table est nommée **Orders** au lieu de **Customers1**. Pour ce faire, mappez la table source de **Customers1** à la table **Orders**du **DataSet** , comme indiqué dans l’exemple suivant.  
  
```vb  
adapter.TableMappings.Add("Customers1", "Orders")  
adapter.Fill(customersDataSet, "Customers")  
```  

```csharp  
adapter.TableMappings.Add("Customers1", "Orders");  
adapter.Fill(customersDataSet, "Customers");  
```
  
## <a name="see-also"></a>Voir aussi

- [DataAdapters et DataReaders](dataadapters-and-datareaders.md)
- [Extraction et modification de données dans ADO.NET](retrieving-and-modifying-data.md)
- [Vue d'ensemble d’ADO.NET](ado-net-overview.md)
