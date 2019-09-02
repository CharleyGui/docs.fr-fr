---
title: Création de colonnes AutoIncrement
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cf09732a-ab54-4d98-89e2-4d0a1f28fbce
ms.openlocfilehash: 2548ad9382b406978dac0a3d366207626278f501
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205129"
---
# <a name="creating-autoincrement-columns"></a><span data-ttu-id="60253-102">Création de colonnes AutoIncrement</span><span class="sxs-lookup"><span data-stu-id="60253-102">Creating AutoIncrement Columns</span></span>
<span data-ttu-id="60253-103">Pour garantir que les valeurs de colonne sont uniques, vous pouvez les définir de sorte qu'elles s'incrémentent automatiquement lors de l'ajout de lignes à la table.</span><span class="sxs-lookup"><span data-stu-id="60253-103">To ensure unique column values, you can set the column values to increment automatically when new rows are added to the table.</span></span> <span data-ttu-id="60253-104">Pour créer une auto-incrémentation <xref:System.Data.DataColumn>, affectez <xref:System.Data.DataColumn.AutoIncrement%2A> la valeur **true**à la propriété de la colonne.</span><span class="sxs-lookup"><span data-stu-id="60253-104">To create an auto-incrementing <xref:System.Data.DataColumn>, set the <xref:System.Data.DataColumn.AutoIncrement%2A> property of the column to **true**.</span></span> <span data-ttu-id="60253-105">Le <xref:System.Data.DataColumn> commence par la valeur définie dans la <xref:System.Data.DataColumn.AutoIncrementSeed%2A> propriété, et chaque ligne ajoutée à la valeur de la colonne **AutoIncrement** augmente de la valeur définie dans la <xref:System.Data.DataColumn.AutoIncrementStep%2A> propriété de la colonne.</span><span class="sxs-lookup"><span data-stu-id="60253-105">The <xref:System.Data.DataColumn> then starts with the value defined in the <xref:System.Data.DataColumn.AutoIncrementSeed%2A> property, and with each row added the value of the **AutoIncrement** column increases by the value defined in the <xref:System.Data.DataColumn.AutoIncrementStep%2A> property of the column.</span></span>  
  
 <span data-ttu-id="60253-106">Pour les colonnes **AutoIncrement** , nous vous recommandons <xref:System.Data.DataColumn.ReadOnly%2A> d’affecter la valeur **true**à la propriété du **DataColumn** .</span><span class="sxs-lookup"><span data-stu-id="60253-106">For **AutoIncrement** columns, we recommend that the <xref:System.Data.DataColumn.ReadOnly%2A> property of the **DataColumn** be set to **true**.</span></span>  
  
 <span data-ttu-id="60253-107">L'exemple suivant montre comment créer une colonne commençant par la valeur 200, avec une incrémentation par pas de 3.</span><span class="sxs-lookup"><span data-stu-id="60253-107">The following example demonstrates how to create a column that starts with a value of 200 and adds incrementally in steps of 3.</span></span>  
  
```vb  
Dim workColumn As DataColumn = workTable.Columns.Add( _  
    "CustomerID", typeof(Int32))  
workColumn.AutoIncrement = true  
workColumn.AutoIncrementSeed = 200  
workColumn.AutoIncrementStep = 3  
```  
  
```csharp  
DataColumn workColumn = workTable.Columns.Add(  
    "CustomerID", typeof(Int32));  
workColumn.AutoIncrement = true;  
workColumn.AutoIncrementSeed = 200;  
workColumn.AutoIncrementStep = 3;  
```  
  
## <a name="see-also"></a><span data-ttu-id="60253-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="60253-108">See also</span></span>

- <xref:System.Data.DataColumn>
- [<span data-ttu-id="60253-109">Définition de schéma de DataTable</span><span class="sxs-lookup"><span data-stu-id="60253-109">DataTable Schema Definition</span></span>](datatable-schema-definition.md)
- [<span data-ttu-id="60253-110">DataTables</span><span class="sxs-lookup"><span data-stu-id="60253-110">DataTables</span></span>](datatables.md)
- [<span data-ttu-id="60253-111">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="60253-111">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
