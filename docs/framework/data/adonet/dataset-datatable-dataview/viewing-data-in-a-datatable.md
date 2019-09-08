---
title: Affichage des données dans un DataTable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1d26e0fb-f6e0-4afa-9a9c-b8d55b8f20dc
ms.openlocfilehash: c13f0b802b2714a17ea4014625a65ebd1b0011f4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785854"
---
# <a name="viewing-data-in-a-datatable"></a>Affichage des données dans un DataTable

Vous pouvez accéder au contenu d’un <xref:System.Data.DataTable> objet à l’aide des collections **Rows** et **Columns** du **DataTable**. Vous pouvez également utiliser la <xref:System.Data.DataTable.Select%2A> méthode pour retourner des sous-ensembles de données dans un **DataTable** en fonction de critères, notamment des critères de recherche, un ordre de tri et un état de ligne. En outre, vous pouvez utiliser la <xref:System.Data.DataRowCollection.Find%2A> méthode du **DataRowCollection** lors de la recherche d’une ligne particulière à l’aide d’une valeur de clé primaire.

La méthode **Select** de l’objet **DataTable** retourne un ensemble d' <xref:System.Data.DataRow> objets qui correspondent aux critères spécifiés. **Select** accepte des arguments facultatifs d’une expression de filtre, d’une expression de tri et d’un **DataViewRowState**. L’expression de filtre identifie les lignes à retourner en fonction des valeurs **DataColumn** , `LastName = 'Smith'`telles que. L'expression de tri respecte les conventions SQL standard de tri des colonnes, comme `LastName ASC, FirstName ASC`. Pour plus d’informations sur les règles d' <xref:System.Data.DataColumn.Expression%2A> écriture d’expressions, consultez la propriété de la classe **DataColumn** .

> [!TIP]
> Si vous effectuez un certain nombre d’appels à la méthode **Select** d’un **DataTable**, vous pouvez augmenter les performances en créant d' <xref:System.Data.DataView> abord un pour le **DataTable**. La création du **DataView** indexe les lignes de la table. La méthode **Select** utilise ensuite cet index, ce qui réduit considérablement le temps nécessaire pour générer le résultat de la requête. Pour plus d’informations sur la création d’un **DataView** pour un **DataTable**, consultez [DataView](dataviews.md).

La méthode **Select** détermine la version des lignes à afficher ou à manipuler en fonction d' <xref:System.Data.DataViewRowState>un. Le tableau suivant décrit les valeurs possibles de l’énumération **DataViewRowState** .

|Valeur DataViewRowState|Description|
|----------------------------|-----------------|
|**CurrentRows**|Les lignes en cours comprennent les lignes non modifiées, les lignes ajoutées et les lignes modifiées.|
|**Supprimé**|Ligne supprimée.|
|**ModifiedCurrent**|Une version actuelle, qui est une version modifiée des données d'origine. (Voir **ModifiedOriginal**.)|
|**ModifiedOriginal**|La version d'origine de toutes les lignes modifiées. La version actuelle est disponible à l’aide de **ModifiedCurrent**.|
|**Ajoute**|Nouvelle ligne.|
|**Aucun**|Aucune.|
|**OriginalRows**|Les lignes d'origine, notamment les lignes non modifiées et les lignes supprimées.|
|**Inchangé**|Ligne non modifiée.|

Dans l’exemple suivant, l’objet **DataSet** est filtré afin que vous n’utilisiez que des lignes dont **DataViewRowState** a la valeur **CurrentRows**.

```vb
Dim column As DataColumn
Dim row As DataRow

Dim currentRows() As DataRow = _
    workTable.Select(Nothing, Nothing, DataViewRowState.CurrentRows)

If (currentRows.Length < 1 ) Then
  Console.WriteLine("No Current Rows Found")
Else
  For Each column in workTable.Columns
    Console.Write(vbTab & column.ColumnName)
  Next

  Console.WriteLine(vbTab & "RowState")

  For Each row In currentRows
    For Each column In workTable.Columns
      Console.Write(vbTab & row(column).ToString())
    Next

    Dim rowState As String = _
        System.Enum.GetName(row.RowState.GetType(), row.RowState)
    Console.WriteLine(vbTab & rowState)
  Next
End If
```

```csharp
DataRow[] currentRows = workTable.Select(
    null, null, DataViewRowState.CurrentRows);

if (currentRows.Length < 1 )
  Console.WriteLine("No Current Rows Found");
else
{
  foreach (DataColumn column in workTable.Columns)
    Console.Write("\t{0}", column.ColumnName);

  Console.WriteLine("\tRowState");

  foreach (DataRow row in currentRows)
  {
    foreach (DataColumn column in workTable.Columns)
      Console.Write("\t{0}", row[column]);

    Console.WriteLine("\t" + row.RowState);
  }
}
```

La méthode **Select** peut être utilisée pour retourner des lignes avec des valeurs **RowState** ou Field différentes. L’exemple suivant retourne un tableau **DataRow** qui référence toutes les lignes qui ont été supprimées, et retourne un autre tableau **DataRow** qui référence toutes les lignes, classées par **CustLName**, où la colonne **CustID** est supérieure à 5. Pour plus d’informations sur l’affichage des informations dans la ligne **supprimée** , consultez [États des lignes et versions de ligne](row-states-and-row-versions.md).

```vb
' Retrieve all deleted rows.
Dim deletedRows() As DataRow = workTable.Select(Nothing, Nothing, DataViewRowState.Deleted)

' Retrieve rows where CustID > 5, and order by CustLName.
Dim custRows() As DataRow = workTable.Select( _
    "CustID > 5", "CustLName ASC")
```

```csharp
// Retrieve all deleted rows.
DataRow[] deletedRows = workTable.Select(
    null, null, DataViewRowState.Deleted);

// Retrieve rows where CustID > 5, and order by CustLName.
DataRow[] custRows = workTable.Select("CustID > 5", "CustLName ASC");
```

## <a name="see-also"></a>Voir aussi

- <xref:System.Data.DataRow>
- <xref:System.Data.DataSet>
- <xref:System.Data.DataTable>
- <xref:System.Data.DataViewRowState>
- [Manipulation des données dans un DataTable](manipulating-data-in-a-datatable.md)
- [États des lignes et versions des lignes](row-states-and-row-versions.md)
- [Vue d’ensemble d’ADO.NET](../ado-net-overview.md)
