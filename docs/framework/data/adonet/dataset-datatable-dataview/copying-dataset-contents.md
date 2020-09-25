---
title: Copie de contenu de DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cb846617-2b1a-44ff-bd7f-5835f5ea37fa
ms.openlocfilehash: 1cadcacab6084bbf3caaf61d98b78fe3067d92f7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202368"
---
# <a name="copying-dataset-contents"></a>Copie de contenu de DataSet

Vous pouvez créer une copie de afin de pouvoir <xref:System.Data.DataSet> utiliser des données sans affecter les données d’origine, ou utiliser un sous-ensemble des données d’un **DataSet**. Lors de la copie d’un **jeu de données**, vous pouvez :  
  
- Créez une copie exacte du **DataSet**, y compris le schéma, les données, les informations d’état de ligne et les versions de ligne.  
  
- Créez un **DataSet** qui contient le schéma d’un **DataSet**existant, mais uniquement les lignes qui ont été modifiées. Vous pouvez retourner toutes les lignes qui ont été modifiées ou spécifier un **DataRowState**spécifique. Pour plus d’informations sur les États de ligne, consultez [États de ligne et versions de ligne](row-states-and-row-versions.md).  
  
- Copiez le schéma, ou structure relationnelle, du **DataSet** uniquement, sans copier les lignes. Les lignes peuvent être importées dans un objet <xref:System.Data.DataTable> existant à l'aide de la méthode <xref:System.Data.DataTable.ImportRow%2A>.  
  
 Pour créer une copie exacte du **DataSet** qui comprend à la fois le schéma et les données, utilisez la <xref:System.Data.DataSet.Copy%2A> méthode du **DataSet**. L’exemple de code suivant montre comment créer une copie exacte du **DataSet**.  
  
```vb  
Dim copyDataSet As DataSet = customerDataSet.Copy()  
```  
  
```csharp  
DataSet copyDataSet = customerDataSet.Copy();  
```  
  
 Pour créer une copie d’un **DataSet** qui comprend le schéma et uniquement les données qui représentent des lignes **ajoutées**, **modifiées**ou **supprimées** , utilisez la <xref:System.Data.DataSet.GetChanges%2A> méthode du **DataSet**. Vous pouvez également utiliser **GetChanges** pour retourner uniquement les lignes avec un état de ligne spécifié en passant une valeur **DataRowState** lors de l’appel de **GetChanges**. L’exemple de code suivant montre comment passer un **DataRowState** lors de l’appel de **GetChanges**.  
  
```vb  
' Copy all changes.  
Dim changeDataSet As DataSet = customerDataSet.GetChanges()  
' Copy only new rows.  
Dim addedDataSetAs DataSet = _  
    customerDataSet.GetChanges(DataRowState.Added)  
```  
  
```csharp  
// Copy all changes.  
DataSet changeDataSet = customerDataSet.GetChanges();  
// Copy only new rows.  
DataSet addedDataSet= customerDataSet.GetChanges(DataRowState.Added);  
```  
  
 Pour créer une copie d’un **DataSet** qui n’inclue que le schéma, utilisez la <xref:System.Data.DataSet.Clone%2A> méthode du **DataSet**. Vous pouvez également ajouter des lignes existantes au DataSet cloné à l’aide de la méthode **ImportRow** de l' **objet** **DataTable**. **ImportRow** ajoute des données, un état de ligne et des informations de version de ligne à la table spécifiée. Les valeurs de colonne ne seront ajoutées que si le nom de colonne est identique et le type de données compatible.  
  
 L’exemple de code suivant crée un clone d’un **DataSet** , puis ajoute les lignes du **DataSet** d’origine à la table **Customers** dans le clone du **jeu de données** pour les clients où la colonne **PaysRégion** a la valeur « Germany ».  
  
```vb  
Dim customerDataSet As New DataSet  
        customerDataSet.Tables.Add(New DataTable("Customers"))  
        customerDataSet.Tables("Customers").Columns.Add("Name", GetType(String))  
        customerDataSet.Tables("Customers").Columns.Add("CountryRegion", GetType(String))  
        customerDataSet.Tables("Customers").Rows.Add("Juan", "Spain")  
        customerDataSet.Tables("Customers").Rows.Add("Johann", "Germany")  
        customerDataSet.Tables("Customers").Rows.Add("John", "UK")  
  
Dim germanyCustomers As DataSet = customerDataSet.Clone()  
  
Dim copyRows() As DataRow = _  
  customerDataSet.Tables("Customers").Select("CountryRegion = 'Germany'")  
  
Dim customerTable As DataTable = germanyCustomers.Tables("Customers")  
Dim copyRow As DataRow  
  
For Each copyRow In copyRows  
  customerTable.ImportRow(copyRow)  
Next  
```  
  
```csharp  
DataSet customerDataSet = new DataSet();  
customerDataSet.Tables.Add(new DataTable("Customers"));  
customerDataSet.Tables["Customers"].Columns.Add("Name", typeof(string));  
customerDataSet.Tables["Customers"].Columns.Add("CountryRegion", typeof(string));  
customerDataSet.Tables["Customers"].Rows.Add("Juan", "Spain");  
customerDataSet.Tables["Customers"].Rows.Add("Johann", "Germany");  
customerDataSet.Tables["Customers"].Rows.Add("John", "UK");  
  
DataSet germanyCustomers = customerDataSet.Clone();  
  
DataRow[] copyRows =
  customerDataSet.Tables["Customers"].Select("CountryRegion = 'Germany'");  
  
DataTable customerTable = germanyCustomers.Tables["Customers"];  
  
foreach (DataRow copyRow in copyRows)  
  customerTable.ImportRow(copyRow);  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Data.DataSet>
- <xref:System.Data.DataTable>
- [DataSets, DataTables et DataViews](index.md)
- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)
