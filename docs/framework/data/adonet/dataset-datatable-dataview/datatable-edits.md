---
title: Modifications de DataTable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f08008a9-042e-4de9-94f3-4f0e502b1eb5
ms.openlocfilehash: 4fdb19e7fa014bf4a7c924b1fbae53fa44de6e3c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153259"
---
# <a name="datatable-edits"></a><span data-ttu-id="0b611-102">Modifications de DataTable</span><span class="sxs-lookup"><span data-stu-id="0b611-102">DataTable Edits</span></span>

<span data-ttu-id="0b611-103">Lorsque vous modifiez les valeurs de colonne d'un objet <xref:System.Data.DataRow>, les modifications sont immédiatement placées dans l'état actuel de la ligne.</span><span class="sxs-lookup"><span data-stu-id="0b611-103">When you make changes to column values in a <xref:System.Data.DataRow>, the changes are immediately placed in the current state of the row.</span></span> <span data-ttu-id="0b611-104"><xref:System.Data.DataRowState>Est ensuite défini sur **modifié**, et les modifications sont acceptées ou rejetées à l' <xref:System.Data.DataRow.AcceptChanges%2A> aide <xref:System.Data.DataRow.RejectChanges%2A> des méthodes ou du **DataRow**.</span><span class="sxs-lookup"><span data-stu-id="0b611-104">The <xref:System.Data.DataRowState> is then set to **Modified**, and the changes are accepted or rejected using the <xref:System.Data.DataRow.AcceptChanges%2A> or <xref:System.Data.DataRow.RejectChanges%2A> methods of the **DataRow**.</span></span> <span data-ttu-id="0b611-105">Le **DataRow** fournit également trois méthodes que vous pouvez utiliser pour suspendre l’état de la ligne pendant que vous la modifiez.</span><span class="sxs-lookup"><span data-stu-id="0b611-105">The **DataRow** also provides three methods that you can use to suspend the state of the row while you are editing it.</span></span> <span data-ttu-id="0b611-106">Ces méthodes sont <xref:System.Data.DataRow.BeginEdit%2A>, <xref:System.Data.DataRow.EndEdit%2A> et <xref:System.Data.DataRow.CancelEdit%2A>.</span><span class="sxs-lookup"><span data-stu-id="0b611-106">These methods are <xref:System.Data.DataRow.BeginEdit%2A>, <xref:System.Data.DataRow.EndEdit%2A>, and <xref:System.Data.DataRow.CancelEdit%2A>.</span></span>  
  
 <span data-ttu-id="0b611-107">Lorsque vous modifiez directement les valeurs de colonne dans un **DataRow** , **DataRow** gère les valeurs de colonne à l’aide des versions de ligne **actuelles**, **par défaut**et **d’origine** .</span><span class="sxs-lookup"><span data-stu-id="0b611-107">When you modify column values in a **DataRow** directly, the **DataRow** manages the column values using the **Current**, **Default**, and **Original** row versions.</span></span> <span data-ttu-id="0b611-108">En plus de ces versions de ligne, les méthodes **BeginEdit**, **EndEdit**et **CancelEdit** utilisent une quatrième version de ligne : **Proposed**.</span><span class="sxs-lookup"><span data-stu-id="0b611-108">In addition to these row versions, the **BeginEdit**, **EndEdit**, and **CancelEdit** methods use a fourth row version: **Proposed**.</span></span> <span data-ttu-id="0b611-109">Pour plus d’informations sur les versions de ligne, consultez [États de ligne et versions de ligne](row-states-and-row-versions.md).</span><span class="sxs-lookup"><span data-stu-id="0b611-109">For more information about row versions, see [Row States and Row Versions](row-states-and-row-versions.md).</span></span>  
  
 <span data-ttu-id="0b611-110">La version de ligne **proposée** existe pendant une opération de modification qui commence par appeler **BeginEdit** et qui se termine à l’aide de **EndEdit** ou **CancelEdit,** ou en appelant **AcceptChanges** ou **RejectChanges**.</span><span class="sxs-lookup"><span data-stu-id="0b611-110">The **Proposed** row version exists during an edit operation that begins by calling **BeginEdit** and that ends either by using **EndEdit** or **CancelEdit,** or by calling **AcceptChanges** or **RejectChanges**.</span></span>  
  
 <span data-ttu-id="0b611-111">Pendant l’opération de modification, vous pouvez appliquer la logique de validation à des colonnes individuelles en évaluant le **ProposedValue** dans l’événement **ColumnChanged** du **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="0b611-111">During the edit operation, you can apply validation logic to individual columns by evaluating the **ProposedValue** in the **ColumnChanged** event of the **DataTable**.</span></span> <span data-ttu-id="0b611-112">L’événement **ColumnChanged** contient des **DataColumnChangeEventArgs** qui maintiennent une référence à la colonne qui change et à **ProposedValue**.</span><span class="sxs-lookup"><span data-stu-id="0b611-112">The **ColumnChanged** event holds **DataColumnChangeEventArgs** that keep a reference to the column that is changing and to the **ProposedValue**.</span></span> <span data-ttu-id="0b611-113">Après avoir évalué la valeur proposée, vous pouvez la modifier ou annuler la modification.</span><span class="sxs-lookup"><span data-stu-id="0b611-113">After you evaluate the proposed value, you can either modify it or cancel the edit.</span></span> <span data-ttu-id="0b611-114">Lorsque la modification est terminée, la ligne passe de l’état **proposé** .</span><span class="sxs-lookup"><span data-stu-id="0b611-114">When the edit is ended, the row moves out of the **Proposed** state.</span></span>  
  
 <span data-ttu-id="0b611-115">Vous pouvez confirmer les modifications en appelant **EndEdit**, ou vous pouvez les annuler en appelant **CancelEdit**.</span><span class="sxs-lookup"><span data-stu-id="0b611-115">You can confirm edits by calling **EndEdit**, or you can cancel them by calling **CancelEdit**.</span></span> <span data-ttu-id="0b611-116">Notez que si **EndEdit** confirme vos modifications, le **DataSet** n’accepte pas réellement les modifications tant que **AcceptChanges** n’est pas appelé.</span><span class="sxs-lookup"><span data-stu-id="0b611-116">Note that while **EndEdit** does confirm your edits, the **DataSet** does not actually accept the changes until **AcceptChanges** is called.</span></span> <span data-ttu-id="0b611-117">Notez également que si vous appelez **AcceptChanges** avant de mettre fin à la modification avec **EndEdit** ou **CancelEdit**, la modification est terminée et les valeurs de ligne **proposées** sont acceptées pour les versions de ligne **actuelles** et **d’origine** .</span><span class="sxs-lookup"><span data-stu-id="0b611-117">Note also that if you call **AcceptChanges** before you have ended the edit with **EndEdit** or **CancelEdit**, the edit is ended and the **Proposed** row values are accepted for both the **Current** and **Original** row versions.</span></span> <span data-ttu-id="0b611-118">De la même manière, l’appel de **RejectChanges** met fin à la modification et ignore les versions de ligne **actuelles** et **proposées** .</span><span class="sxs-lookup"><span data-stu-id="0b611-118">In the same manner, calling **RejectChanges** ends the edit and discards the **Current** and **Proposed** row versions.</span></span> <span data-ttu-id="0b611-119">L’appel de **EndEdit** ou **CancelEdit** après l’appel à **AcceptChanges** ou **RejectChanges** n’a aucun effet, car la modification est déjà terminée.</span><span class="sxs-lookup"><span data-stu-id="0b611-119">Calling **EndEdit** or **CancelEdit** after calling **AcceptChanges** or **RejectChanges** has no effect because the edit has already ended.</span></span>  
  
 <span data-ttu-id="0b611-120">L’exemple suivant montre comment utiliser **BeginEdit** avec **EndEdit** et **CancelEdit**.</span><span class="sxs-lookup"><span data-stu-id="0b611-120">The following example demonstrates how to use **BeginEdit** with **EndEdit** and **CancelEdit**.</span></span> <span data-ttu-id="0b611-121">L’exemple vérifie également le **ProposedValue** dans l’événement **ColumnChanged** et décide s’il faut annuler la modification.</span><span class="sxs-lookup"><span data-stu-id="0b611-121">The example also checks the **ProposedValue** in the **ColumnChanged** event and decides whether to cancel the edit.</span></span>  
  
```vb  
Dim workTable As DataTable = New DataTable  
workTable.Columns.Add("LastName", Type.GetType("System.String"))  
  
AddHandler workTable.ColumnChanged, _  
  New DataColumnChangeEventHandler(AddressOf OnColumnChanged)  
  
Dim workRow As DataRow = workTable.NewRow()  
workRow(0) = "Smith"  
workTable.Rows.Add(workRow)  
  
workRow.BeginEdit()  
' Causes the ColumnChanged event to write a message and cancel the edit.  
workRow(0) = ""
workRow.EndEdit()  
  
' Displays "Smith, New".  
Console.WriteLine("{0}, {1}", workRow(0), workRow.RowState)  
  
Private Shared Sub OnColumnChanged( _  
  sender As Object, args As DataColumnChangeEventArgs)  
  If args.Column.ColumnName = "LastName" Then  
    If args.ProposedValue.ToString() = "" Then  
      Console.WriteLine("Last Name cannot be blank.  Edit canceled.")  
      args.Row.CancelEdit()  
    End If  
  End If  
End Sub  
```  
  
```csharp  
DataTable workTable  = new DataTable();  
workTable.Columns.Add("LastName", typeof(String));  
  
workTable.ColumnChanged +=
  new DataColumnChangeEventHandler(OnColumnChanged);  
  
DataRow workRow = workTable.NewRow();  
workRow[0] = "Smith";  
workTable.Rows.Add(workRow);  
  
workRow.BeginEdit();  
// Causes the ColumnChanged event to write a message and cancel the edit.  
workRow[0] = "";
workRow.EndEdit();  
  
// Displays "Smith, New".  
Console.WriteLine("{0}, {1}", workRow[0], workRow.RowState);
  
protected static void OnColumnChanged(  
  Object sender, DataColumnChangeEventArgs args)  
{  
  if (args.Column.ColumnName == "LastName")  
    if (args.ProposedValue.ToString() == "")  
    {  
      Console.WriteLine("Last Name cannot be blank. Edit canceled.");  
      args.Row.CancelEdit();  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="0b611-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0b611-122">See also</span></span>

- <xref:System.Data.DataRow>
- <xref:System.Data.DataTable>
- <xref:System.Data.DataRowVersion>
- [<span data-ttu-id="0b611-123">Manipulation des données dans un DataTable</span><span class="sxs-lookup"><span data-stu-id="0b611-123">Manipulating Data in a DataTable</span></span>](manipulating-data-in-a-datatable.md)
- [<span data-ttu-id="0b611-124">Gestion des événements de DataTable</span><span class="sxs-lookup"><span data-stu-id="0b611-124">Handling DataTable Events</span></span>](handling-datatable-events.md)
- [<span data-ttu-id="0b611-125">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="0b611-125">ADO.NET Overview</span></span>](../ado-net-overview.md)
