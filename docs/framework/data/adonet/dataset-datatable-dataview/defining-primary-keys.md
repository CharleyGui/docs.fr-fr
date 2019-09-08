---
title: Définition des clés primaires
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2ea85959-e763-4669-8bd9-46a9dab894bd
ms.openlocfilehash: 0f87b1b730eecf0edad75bd87ca8b491b96e1d2b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784709"
---
# <a name="defining-primary-keys"></a><span data-ttu-id="1e8a3-102">Définition des clés primaires</span><span class="sxs-lookup"><span data-stu-id="1e8a3-102">Defining Primary Keys</span></span>
<span data-ttu-id="1e8a3-103">Une table de base de données a généralement une colonne ou un groupe de colonnes identifiant de façon unique chaque ligne de la table.</span><span class="sxs-lookup"><span data-stu-id="1e8a3-103">A database table commonly has a column or group of columns that uniquely identifies each row in the table.</span></span> <span data-ttu-id="1e8a3-104">Cette colonne ou ce groupe de colonnes d'identification s'appelle la clé primaire.</span><span class="sxs-lookup"><span data-stu-id="1e8a3-104">This identifying column or group of columns is called the primary key.</span></span>  
  
 <span data-ttu-id="1e8a3-105">Lorsque vous identifiez un <xref:System.Data.DataColumn> unique <xref:System.Data.DataTable.PrimaryKey%2A> comme pour un <xref:System.Data.DataTable>, la table affecte <xref:System.Data.DataColumn.AllowDBNull%2A> automatiquement à la propriété de la colonne la **valeur false** et à la propriété la <xref:System.Data.DataColumn.Unique%2A> **valeur true**.</span><span class="sxs-lookup"><span data-stu-id="1e8a3-105">When you identify a single <xref:System.Data.DataColumn> as the <xref:System.Data.DataTable.PrimaryKey%2A> for a <xref:System.Data.DataTable>, the table automatically sets the <xref:System.Data.DataColumn.AllowDBNull%2A> property of the column to **false** and the <xref:System.Data.DataColumn.Unique%2A> property to **true**.</span></span> <span data-ttu-id="1e8a3-106">Pour les clés primaires à plusieurs colonnes, seule la propriété **AllowDBNull** a automatiquement la valeur **false**.</span><span class="sxs-lookup"><span data-stu-id="1e8a3-106">For multiple-column primary keys, only the **AllowDBNull** property is automatically set to **false**.</span></span>  
  
 <span data-ttu-id="1e8a3-107">La propriété **PrimaryKey** d’un <xref:System.Data.DataTable> objet reçoit comme valeur un tableau d’un ou plusieurs objets **DataColumn** , comme indiqué dans les exemples suivants.</span><span class="sxs-lookup"><span data-stu-id="1e8a3-107">The **PrimaryKey** property of a <xref:System.Data.DataTable> receives as its value an array of one or more **DataColumn** objects, as shown in the following examples.</span></span> <span data-ttu-id="1e8a3-108">Le premier exemple définit une colonne unique comme clé primaire.</span><span class="sxs-lookup"><span data-stu-id="1e8a3-108">The first example defines a single column as the primary key.</span></span>  
  
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
  
 <span data-ttu-id="1e8a3-109">L'exemple suivant définit deux colonnes comme clé primaire.</span><span class="sxs-lookup"><span data-stu-id="1e8a3-109">The following example defines two columns as a primary key.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1e8a3-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1e8a3-110">See also</span></span>

- <xref:System.Data.DataTable>
- [<span data-ttu-id="1e8a3-111">Définition de schéma de DataTable</span><span class="sxs-lookup"><span data-stu-id="1e8a3-111">DataTable Schema Definition</span></span>](datatable-schema-definition.md)
- [<span data-ttu-id="1e8a3-112">DataTables</span><span class="sxs-lookup"><span data-stu-id="1e8a3-112">DataTables</span></span>](datatables.md)
- [<span data-ttu-id="1e8a3-113">Vue d’ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="1e8a3-113">ADO.NET Overview</span></span>](../ado-net-overview.md)
