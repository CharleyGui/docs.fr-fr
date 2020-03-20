---
title: Définition des clés primaires
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2ea85959-e763-4669-8bd9-46a9dab894bd
ms.openlocfilehash: 159b23eb4ef5ca38ebce6e488080d315ec3be081
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151180"
---
# <a name="defining-primary-keys"></a>Définition des clés primaires
Une table de base de données a généralement une colonne ou un groupe de colonnes identifiant de façon unique chaque ligne de la table. Cette colonne ou ce groupe de colonnes d'identification s'appelle la clé primaire.  
  
 Lorsque vous identifiez <xref:System.Data.DataTable.PrimaryKey%2A> un <xref:System.Data.DataTable>single <xref:System.Data.DataColumn> comme le pour un , la <xref:System.Data.DataColumn.Unique%2A> table définit automatiquement la <xref:System.Data.DataColumn.AllowDBNull%2A> propriété de la colonne à **faux** et la propriété à **vrai**. Pour les touches primaires à colonnes multiples, seule la propriété **AllowDBNull** est automatiquement **fausse.**  
  
 La propriété **PrimaryKey** d’un <xref:System.Data.DataTable> reçoit comme valeur un tableau d’un ou plusieurs objets **DataColumn,** comme le montrent les exemples suivants. Le premier exemple définit une colonne unique comme clé primaire.  
  
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
- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)
