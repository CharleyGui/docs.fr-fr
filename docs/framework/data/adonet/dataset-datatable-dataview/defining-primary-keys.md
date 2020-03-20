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
# <a name="defining-primary-keys"></a><span data-ttu-id="e62b4-102">Définition des clés primaires</span><span class="sxs-lookup"><span data-stu-id="e62b4-102">Defining Primary Keys</span></span>
<span data-ttu-id="e62b4-103">Une table de base de données a généralement une colonne ou un groupe de colonnes identifiant de façon unique chaque ligne de la table.</span><span class="sxs-lookup"><span data-stu-id="e62b4-103">A database table commonly has a column or group of columns that uniquely identifies each row in the table.</span></span> <span data-ttu-id="e62b4-104">Cette colonne ou ce groupe de colonnes d'identification s'appelle la clé primaire.</span><span class="sxs-lookup"><span data-stu-id="e62b4-104">This identifying column or group of columns is called the primary key.</span></span>  
  
 <span data-ttu-id="e62b4-105">Lorsque vous identifiez <xref:System.Data.DataTable.PrimaryKey%2A> un <xref:System.Data.DataTable>single <xref:System.Data.DataColumn> comme le pour un , la <xref:System.Data.DataColumn.Unique%2A> table définit automatiquement la <xref:System.Data.DataColumn.AllowDBNull%2A> propriété de la colonne à **faux** et la propriété à **vrai**.</span><span class="sxs-lookup"><span data-stu-id="e62b4-105">When you identify a single <xref:System.Data.DataColumn> as the <xref:System.Data.DataTable.PrimaryKey%2A> for a <xref:System.Data.DataTable>, the table automatically sets the <xref:System.Data.DataColumn.AllowDBNull%2A> property of the column to **false** and the <xref:System.Data.DataColumn.Unique%2A> property to **true**.</span></span> <span data-ttu-id="e62b4-106">Pour les touches primaires à colonnes multiples, seule la propriété **AllowDBNull** est automatiquement **fausse.**</span><span class="sxs-lookup"><span data-stu-id="e62b4-106">For multiple-column primary keys, only the **AllowDBNull** property is automatically set to **false**.</span></span>  
  
 <span data-ttu-id="e62b4-107">La propriété **PrimaryKey** d’un <xref:System.Data.DataTable> reçoit comme valeur un tableau d’un ou plusieurs objets **DataColumn,** comme le montrent les exemples suivants.</span><span class="sxs-lookup"><span data-stu-id="e62b4-107">The **PrimaryKey** property of a <xref:System.Data.DataTable> receives as its value an array of one or more **DataColumn** objects, as shown in the following examples.</span></span> <span data-ttu-id="e62b4-108">Le premier exemple définit une colonne unique comme clé primaire.</span><span class="sxs-lookup"><span data-stu-id="e62b4-108">The first example defines a single column as the primary key.</span></span>  
  
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
  
 <span data-ttu-id="e62b4-109">L'exemple suivant définit deux colonnes comme clé primaire.</span><span class="sxs-lookup"><span data-stu-id="e62b4-109">The following example defines two columns as a primary key.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e62b4-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e62b4-110">See also</span></span>

- <xref:System.Data.DataTable>
- [<span data-ttu-id="e62b4-111">Définition de schéma de DataTable</span><span class="sxs-lookup"><span data-stu-id="e62b4-111">DataTable Schema Definition</span></span>](datatable-schema-definition.md)
- [<span data-ttu-id="e62b4-112">DataTables</span><span class="sxs-lookup"><span data-stu-id="e62b4-112">DataTables</span></span>](datatables.md)
- [<span data-ttu-id="e62b4-113">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="e62b4-113">ADO.NET Overview</span></span>](../ado-net-overview.md)
