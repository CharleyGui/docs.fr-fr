---
title: Définition des clés primaires
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2ea85959-e763-4669-8bd9-46a9dab894bd
ms.openlocfilehash: dbfd8a8b207c0da9403ac1f8ab36557c4abe383b
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204910"
---
# <a name="defining-primary-keys"></a>Définition des clés primaires
Une table de base de données a généralement une colonne ou un groupe de colonnes identifiant de façon unique chaque ligne de la table. Cette colonne ou ce groupe de colonnes d'identification s'appelle la clé primaire.  
  
 Lorsque vous identifiez un <xref:System.Data.DataColumn> unique <xref:System.Data.DataTable.PrimaryKey%2A> comme pour un <xref:System.Data.DataTable>, la table affecte <xref:System.Data.DataColumn.AllowDBNull%2A> automatiquement à la propriété de la colonne la **valeur false** et à la propriété la <xref:System.Data.DataColumn.Unique%2A> **valeur true**. Pour les clés primaires à plusieurs colonnes, seule la propriété **AllowDBNull** a automatiquement lavaleur false.  
  
 La propriété **PrimaryKey** d’un <xref:System.Data.DataTable> objet reçoit comme valeur un tableau d’un ou plusieurs objets **DataColumn** , comme indiqué dans les exemples suivants. Le premier exemple définit une colonne unique comme clé primaire.  
  
```vb  
workTable.PrimaryKey = New DataColumn() {workTable.Columns("CustID")}  
  
' Or  
  
Dim columns(1) As DataColumn  
columns(0) = workTable.Columns("CustID")  
workTable.PrimaryKey = columns  
```  
  
```csharp  
workTable.PrimaryKey = new DataColumn[] {workTable.Columns["CustID"]};  
  
// Or  
  
DataColumn[] columns = new DataColumn[1];  
columns[0] = workTable.Columns["CustID"];  
workTable.PrimaryKey = columns;  
```  
  
 L'exemple suivant définit deux colonnes comme clé primaire.  
  
```vb  
workTable.PrimaryKey = New DataColumn() {workTable.Columns("CustLName"), _  
                                         workTable.Columns("CustFName")}  
  
' Or  
  
Dim keyColumn(2) As DataColumn  
keyColumn(0) = workTable.Columns("CustLName")  
keyColumn(1) = workTable.Columns("CustFName")  
workTable.PrimaryKey = keyColumn  
```  
  
```csharp  
workTable.PrimaryKey = new DataColumn[] {workTable.Columns["CustLName"],   
                                         workTable.Columns["CustFName"]};  
  
// Or  
  
DataColumn[] keyColumn = new DataColumn[2];  
keyColumn[0] = workTable.Columns["CustLName"];  
keyColumn[1] = workTable.Columns["CustFName"];  
workTable.PrimaryKey = keyColumn;  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Data.DataTable>
- [Définition de schéma de DataTable](datatable-schema-definition.md)
- [DataTables](datatables.md)
- [Fournisseurs managés ADO.NET et centre de développement DataSet](https://go.microsoft.com/fwlink/?LinkId=217917)
