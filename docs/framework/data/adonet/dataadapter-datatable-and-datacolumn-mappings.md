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
# <a name="dataadapter-datatable-and-datacolumn-mappings"></a>Mappages de DataAdapter DataTable et DataColumn
Un **DataAdapter** contient une collection <xref:System.Data.Common.DataTableMapping> d’objets nuls ou plus dans sa propriété **TableMappings.** Un **DataTableMapping** fournit une cartographie principale entre les données retournées <xref:System.Data.DataTable>à partir d’une requête contre une source de données, et un . Le nom **DataTableMapping** peut être transmis à la place du nom **DataTable** à la méthode **De remplissage** du **DataAdapter**. L’exemple suivant crée un **DataTableMapping** nommé **AuthorsMapping** pour la table **des auteurs.**  
  
```vb  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors")  
```  
  
```csharp  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors");  
```  
  
 Un **DataTableMapping** vous permet d’utiliser des noms de colonnes dans un **DataTable** qui sont différents de ceux de la base de données. Le **DataAdapter** utilise la cartographie pour correspondre aux colonnes lorsque la table est mise à jour.  
  
 Si vous ne spécifiez pas un **nom TableName** ou un nom **DataTableMapping** lors de l’appel de la méthode **De remplissage** ou de mise **à jour** du **DataAdapter**, le **DataAdapter** recherche un **DataTableMapping** nommé "Table". Si celui **DataTableMapping n’existe** pas, le Nom de **table** de la **Table est** "Table". Vous pouvez spécifier un défaut **DataTableMapping** en créant un **DataTableMapping** avec le nom de "Table".  
  
 L’exemple de code suivant crée un <xref:System.Data.Common> **DataTableMapping** (à partir de l’espace de nom) et en fait la cartographie par défaut pour le **DataAdapter** spécifié en le nommant "Table". L’exemple cartographie ensuite les colonnes du premier tableau du résultat de la requête (la table **des clients** de la base de données **Northwind)** à un ensemble de noms plus conviviaux dans le tableau **des clients Northwind** dans le <xref:System.Data.DataSet>. Pour les colonnes qui ne sont pas mappées, le nom de la colonne de la source de données est utilisé.  
  
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
  
 Dans des situations plus avancées, vous pouvez décider que vous voulez que le même **DataAdapter** supporte le chargement de différentes tables avec différentes cartes. Pour ce faire, il suffit d’ajouter des objets **De dataTableMapping** supplémentaires.  
  
 Lorsque la méthode **De remplissage** est adoptée, une instance d’un **DataSet** et d’un nom **DataTableMapping,** si une cartographie avec ce nom existe, elle est utilisée; autrement, un **DataTable** avec ce nom est utilisé.  
  
 Les exemples suivants créent un **DataTableMapping** avec un nom de **clients** et un nom **DataTable** de **BizTalkSchema**. L’exemple cartographie ensuite les lignes retournées par la déclaration SELECT à la **BizTalkSchema** **DataTable**.  
  
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
> Si aucun nom de colonne source n'est fourni pour un mappage de colonne ou aucun nom de table source n'est fourni pour un mappage de table, les noms par défaut sont automatiquement générés. Si aucune colonne source n’est fournie pour une cartographie de colonne, la cartographie de colonne est donnée un nom par défaut progressif de **SourceColumn** *N,* à commencer par **SourceColumn1**. Si aucun nom de table source n’est fourni pour une cartographie de table, la cartographie de table est donnée un nom par défaut progressif de **SourceTable** *N*, à commencer par **SourceTable1**.  
  
> [!NOTE]
> Nous vous recommandons d’éviter la convention de nommage de **SourceColumn** *N* pour une cartographie de colonne, ou **SourceTable** *N* pour une cartographie de table, parce que le nom que vous fournissez peut entrer en conflit avec un nom de cartographie de colonne par défaut existant dans le **ColumnMappingCollection** ou nom de cartographie de table dans le **DataTableMappingCollection**. Si le nom fourni existe déjà, une exception sera levée.  
  
## <a name="handling-multiple-result-sets"></a>Gestion de jeux de résultats multiples  
 Si votre **SelectCommand** retourne plusieurs tables, **Fill** génère automatiquement des noms de table avec des valeurs incrémentielles pour les tables dans le **DataSet**, en commençant par le nom de table spécifié et en continuant sous la forme **TableName** *N*, à commencer par **TableName1**. Vous pouvez utiliser des cartes de table pour cartographier le nom de table généré automatiquement à un nom que vous souhaitez spécifié pour la table dans le **DataSet**. Par exemple, pour un **SelectCommand** qui renvoie deux tables, **clients** et **commandes,** émettent l’appel suivant à **Remplir**.  
  
```vb  
adapter.Fill(customersDataSet, "Customers")  
```  

```csharp  
adapter.Fill(customersDataSet, "Customers");  
```  

 Deux tables sont créées dans le **DataSet**: **Clients** et **Clients1**. Vous pouvez utiliser des cartes de table pour vous assurer que la deuxième table est nommée **Commandes** au lieu de **Customers1**. Pour ce faire, cartographiez le tableau source des **clients1** sur les **commandes**de table **DataSet,** comme le montre l’exemple suivant.  
  
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
