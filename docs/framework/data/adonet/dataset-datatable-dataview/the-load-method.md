---
title: Méthode Load
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: e22e5812-89c6-41f0-9302-bb899a46dbff
ms.openlocfilehash: f1c819333225c22efb85946001a1fc8340d57989
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150725"
---
# <a name="the-load-method"></a>Méthode Load
Vous pouvez utiliser la méthode <xref:System.Data.DataTable.Load%2A> pour charger un objet <xref:System.Data.DataTable> de lignes d'une source de données. Il s’agit d’une méthode surchargée qui, dans sa forme la plus simple, accepte un seul paramètre, un **DataReader**. Sous cette forme, il charge simplement le **DataTable** avec des lignes. En option, vous pouvez spécifier le **paramètre LoadOption** pour contrôler la façon dont les données sont ajoutées à la **DataTable**.  
  
 Le **paramètre LoadOption** est particulièrement utile dans les cas où le **DataTable** contient déjà des lignes de données, car il décrit comment les données entrantes de la source de données seront combinées avec les données déjà dans le tableau. Par exemple, **PreserveCurrentValues** (par défaut) précise que dans les cas où une ligne est marquée comme **ajoutée** dans le **DataTable**, la valeur **d’origine** ou chaque colonne est réglée sur le contenu de la ligne correspondante à partir de la source de données. La valeur **actuelle** conservera les valeurs attribuées lors de l’ajout de la ligne, et le **RowState** de la ligne sera réglé sur **Changed**.  
  
 Le tableau suivant donne une brève description des valeurs d'énumération <xref:System.Data.LoadOption>.  
  
|Valeur LoadOption|Description|  
|----------------------|-----------------|  
|**OverwriteRow**|Si les lignes entrantes ont la même valeur **PrimaryKey** que d’affilée déjà dans le **DataTable**, les valeurs **originales** et **actuelles** de chaque colonne sont remplacées par les valeurs de la rangée entrante, et la propriété **RowState** est définie à **inchangé .**<br /><br /> Des lignes provenant de la source de données qui n’existent pas déjà dans le **DataTable** sont ajoutées avec une valeur **RowState** de **Unchanged**.<br /><br /> Cette option actualise en effet le contenu de la **DataTable** afin qu’elle corresponde au contenu de la source de données.|  
|**PreserveCurrentValues (par défaut)**|Si les lignes entrantes ont la même valeur **PrimaryKey** qu’une ligne déjà dans le **DataTable**, la valeur **d’origine** est réglée sur le contenu de la ligne entrante, et la valeur **actuelle** n’est pas modifiée.<br /><br /> Si le **RowState** est **ajouté** ou **modifié,** il est réglé sur **Modified**.<br /><br /> Si le **RowState** a été **supprimé,** il reste **supprimé**.<br /><br /> Des lignes provenant de la source de données qui n’existent pas déjà dans le **DataTable** sont ajoutées, et le **RowState** est réglé à **unchanged**.|  
|**UpdateCurrentValues**|Si les lignes entrantes ont la même valeur **PrimaryKey** que la ligne déjà dans le **DataTable**, la valeur **actuelle** est copiée à la valeur **originale,** et la valeur **actuelle** est ensuite réglée sur le contenu de la ligne entrante.<br /><br /> Si le **RowState** dans le **DataTable** a été **ajouté**, le **RowState** reste **ajouté**. Pour les lignes marquées comme **modifiées** ou **supprimées,** le **RowState** est **modifié**.<br /><br /> Des lignes de la source de données qui n’existent pas déjà dans le **DataTable** sont ajoutées, et le **RowState** est configuré à **Ajouté**.|  
  
 L’échantillon suivant utilise la méthode **load** pour afficher une liste d’anniversaires pour les employés de la base de données **Northwind.**  
  
```vb  
Private Sub LoadBirthdays(ByVal connectionString As String)  
    ' Assumes that connectionString is a valid connection string  
    ' to the Northwind database on SQL Server.  
    Dim queryString As String = _  
    "SELECT LastName, FirstName, BirthDate " & _  
      " FROM dbo.Employees " & _  
      "ORDER BY BirthDate, LastName, FirstName"  
  
    ' Open and fill a DataSet.
    Dim adapter As SqlDataAdapter = New SqlDataAdapter( _  
        queryString, connectionString)  
    Dim employees As New DataSet  
    adapter.Fill(employees, "Employees")  
  
    ' Create a SqlDataReader for use with the Load Method.  
    Dim reader As DataTableReader = employees.GetDataReader()  
  
    ' Create an instance of DataTable and assign the first  
    ' DataTable in the DataSet.Tables collection to it.  
    Dim dataTableEmp As DataTable = employees.Tables(0)  
  
    ' Fill the DataTable with data by calling Load and  
    ' passing the SqlDataReader.  
    dataTableEmp.Load(reader, LoadOption.OverwriteRow)  
  
    ' Loop through the rows collection and display the values  
    ' in the console window.  
    Dim employeeRow As DataRow  
    For Each employeeRow In dataTableEmp.Rows  
        Console.WriteLine("{0:MM\\dd\\yyyy}" & ControlChars.Tab & _  
          "{1}, {2}", _  
          employeeRow("BirthDate"), _  
          employeeRow("LastName"), _  
          employeeRow("FirstName"))  
    Next employeeRow  
  
    ' Keep the window opened to view the contents.  
    Console.ReadLine()  
End Sub  
```  
  
## <a name="see-also"></a>Voir aussi

- [Manipulation des données dans un DataTable](manipulating-data-in-a-datatable.md)
- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)
