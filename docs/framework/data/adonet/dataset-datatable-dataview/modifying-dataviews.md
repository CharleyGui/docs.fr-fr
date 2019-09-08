---
title: Modification des DataViews
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 697a3991-b660-4a5a-8a54-1a2304ff158e
ms.openlocfilehash: 3e811410ea9fdd4be0cbd84b895483f69f58b0d0
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786045"
---
# <a name="modifying-dataviews"></a><span data-ttu-id="a905a-102">Modification des DataViews</span><span class="sxs-lookup"><span data-stu-id="a905a-102">Modifying DataViews</span></span>
<span data-ttu-id="a905a-103">Vous pouvez utiliser l'objet <xref:System.Data.DataView> pour ajouter, supprimer ou modifier des lignes de données dans la table sous-jacente.</span><span class="sxs-lookup"><span data-stu-id="a905a-103">You can use the <xref:System.Data.DataView> to add, delete, or modify rows of data in the underlying table.</span></span> <span data-ttu-id="a905a-104">La possibilité d’utiliser le **DataView** pour modifier les données dans la table sous-jacente est contrôlée par la définition de l’une des trois propriétés booléennes du **DataView**.</span><span class="sxs-lookup"><span data-stu-id="a905a-104">The ability to use the **DataView** to modify data in the underlying table is controlled by setting one of three Boolean properties of the **DataView**.</span></span> <span data-ttu-id="a905a-105">Ces propriétés sont <xref:System.Data.DataView.AllowNew%2A>, <xref:System.Data.DataView.AllowEdit%2A> et <xref:System.Data.DataView.AllowDelete%2A>.</span><span class="sxs-lookup"><span data-stu-id="a905a-105">These properties are <xref:System.Data.DataView.AllowNew%2A>, <xref:System.Data.DataView.AllowEdit%2A>, and <xref:System.Data.DataView.AllowDelete%2A>.</span></span> <span data-ttu-id="a905a-106">Elles ont la valeur **true** par défaut.</span><span class="sxs-lookup"><span data-stu-id="a905a-106">They are set to **true** by default.</span></span>  
  
 <span data-ttu-id="a905a-107">Si **AllowNew** a la **valeur true**, vous pouvez <xref:System.Data.DataView.AddNew%2A> utiliser la méthode du **DataView** pour créer un <xref:System.Data.DataRowView>nouveau.</span><span class="sxs-lookup"><span data-stu-id="a905a-107">If **AllowNew** is **true**, you can use the <xref:System.Data.DataView.AddNew%2A> method of the **DataView** to create a new <xref:System.Data.DataRowView>.</span></span> <span data-ttu-id="a905a-108">Notez qu’une nouvelle ligne n’est pas réellement ajoutée au sous <xref:System.Data.DataTable> -jacent <xref:System.Data.DataRowView.EndEdit%2A> tant que la méthode du **DataRowView** n’a pas été appelée.</span><span class="sxs-lookup"><span data-stu-id="a905a-108">Note that a new row is not actually added to the underlying <xref:System.Data.DataTable> until the <xref:System.Data.DataRowView.EndEdit%2A> method of the **DataRowView** is called.</span></span> <span data-ttu-id="a905a-109">Si la <xref:System.Data.DataRowView.CancelEdit%2A> méthode du **DataRowView** est appelée, la nouvelle ligne est ignorée.</span><span class="sxs-lookup"><span data-stu-id="a905a-109">If the <xref:System.Data.DataRowView.CancelEdit%2A> method of the **DataRowView** is called, the new row is discarded.</span></span> <span data-ttu-id="a905a-110">Notez également que vous ne pouvez modifier qu’un seul **DataRowView** à la fois.</span><span class="sxs-lookup"><span data-stu-id="a905a-110">Note also that you can edit only one **DataRowView** at a time.</span></span> <span data-ttu-id="a905a-111">Si vous appelez la méthode **AddNew** ou **BeginEdit** du **DataRowView** alors qu’une ligne en attente existe, la méthode **EndEdit** est implicitement appelée sur la ligne en attente.</span><span class="sxs-lookup"><span data-stu-id="a905a-111">If you call the **AddNew** or **BeginEdit** method of the **DataRowView** while a pending row exists, **EndEdit** is implicitly called on the pending row.</span></span> <span data-ttu-id="a905a-112">Lorsque la méthode **EndEdit** est appelée, les modifications sont appliquées au **DataTable** sous-jacent et peuvent être validées ou rejetées ultérieurement à l’aide des méthodes **AcceptChanges** ou **RejectChanges** du **DataTable**, du **DataSet**ou **de Objet DataRow** .</span><span class="sxs-lookup"><span data-stu-id="a905a-112">When **EndEdit** is called, the changes are applied to the underlying **DataTable** and can later be committed or rejected using the **AcceptChanges** or **RejectChanges** methods of the **DataTable**, **DataSet**, or **DataRow** object.</span></span> <span data-ttu-id="a905a-113">Si **AllowNew** a la **valeur false**, une exception est levée si vous appelez la méthode **AddNew** du **DataRowView**.</span><span class="sxs-lookup"><span data-stu-id="a905a-113">If **AllowNew** is **false**, an exception is thrown if you call the **AddNew** method of the **DataRowView**.</span></span>  
  
 <span data-ttu-id="a905a-114">Si **AllowEdit** a la **valeur true**, vous pouvez modifier le contenu d’un **DataRow** via le **DataRowView**.</span><span class="sxs-lookup"><span data-stu-id="a905a-114">If **AllowEdit** is **true**, you can modify the contents of a **DataRow** via the **DataRowView**.</span></span> <span data-ttu-id="a905a-115">Vous pouvez confirmer les modifications apportées à la ligne sous-jacente à l’aide de **DataRowView. EndEdit** ou refuser les modifications à l’aide de **DataRowView. CancelEdit**.</span><span class="sxs-lookup"><span data-stu-id="a905a-115">You can confirm changes to the underlying row using **DataRowView.EndEdit** or reject the changes using **DataRowView.CancelEdit**.</span></span> <span data-ttu-id="a905a-116">Notez que vous ne pouvez modifier qu'une seule ligne à la fois.</span><span class="sxs-lookup"><span data-stu-id="a905a-116">Note that only one row can be edited at a time.</span></span> <span data-ttu-id="a905a-117">Si vous appelez les méthodes **AddNew** ou **BeginEdit** du **DataRowView** alors qu’une ligne en attente existe, la méthode **EndEdit** est implicitement appelée sur la ligne en attente.</span><span class="sxs-lookup"><span data-stu-id="a905a-117">If you call the **AddNew** or **BeginEdit** methods of the **DataRowView** while a pending row exists, **EndEdit** is implicitly called on the pending row.</span></span> <span data-ttu-id="a905a-118">Lorsque la méthode **EndEdit** est appelée, les modifications proposées sont placées dans la version de ligne **actuelle** du **DataRow** sous-jacent et peuvent être validées ou rejetées ultérieurement à l’aide des méthodes **AcceptChanges** ou **RejectChanges** de l' **objet Objet DataTable**, **DataSet**ou **DataRow** .</span><span class="sxs-lookup"><span data-stu-id="a905a-118">When **EndEdit** is called, proposed changes are placed in the **Current** row version of the underlying **DataRow** and can later be committed or rejected using the **AcceptChanges** or **RejectChanges** methods of the **DataTable**, **DataSet**, or **DataRow** object.</span></span> <span data-ttu-id="a905a-119">Si **AllowEdit** a la valeur **false**, une exception est levée si vous tentez de modifier une valeur dans le **DataView**.</span><span class="sxs-lookup"><span data-stu-id="a905a-119">If **AllowEdit** is **false**, an exception is thrown if you attempt to modify a value in the **DataView**.</span></span>  
  
 <span data-ttu-id="a905a-120">Lorsqu’un **DataRowView** existant est en cours de modification, les événements du **DataTable** sous-jacent sont toujours déclenchés avec les modifications proposées.</span><span class="sxs-lookup"><span data-stu-id="a905a-120">When an existing **DataRowView** is being edited, events of the underlying **DataTable** will still be raised with the proposed changes.</span></span> <span data-ttu-id="a905a-121">Notez que si vous appelez **EndEdit** ou **CancelEdit** sur le **DataRow**sous-jacent, les modifications en attente seront appliquées ou annulées, que la méthode **EndEdit** ou **CancelEdit** soit appelée sur le **DataRowView**ou non.</span><span class="sxs-lookup"><span data-stu-id="a905a-121">Note that if you call **EndEdit** or **CancelEdit** on the underlying **DataRow**, pending changes will be applied or canceled regardless of whether **EndEdit** or **CancelEdit** is called on the **DataRowView**.</span></span>  
  
 <span data-ttu-id="a905a-122">Si **AllowDelete** a la **valeur true**, vous pouvez supprimer des lignes du **DataView** à l’aide de la méthode **Delete** de l’objet **DataView** ou **DataRowView** , et les lignes sont supprimées du **DataTable**sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="a905a-122">If **AllowDelete** is **true**, you can delete rows from the **DataView** by using the **Delete** method of the **DataView** or **DataRowView** object, and the rows are deleted from the underlying **DataTable**.</span></span> <span data-ttu-id="a905a-123">Vous pouvez par la suite valider ou refuser les suppressions à l’aide de **AcceptChanges** ou de **RejectChanges** respectivement.</span><span class="sxs-lookup"><span data-stu-id="a905a-123">You can later commit or reject the deletes using **AcceptChanges** or **RejectChanges** respectively.</span></span> <span data-ttu-id="a905a-124">Si **AllowDelete** a la **valeur false**, une exception est levée si vous appelez la méthode **Delete** du **DataView** ou **DataRowView**.</span><span class="sxs-lookup"><span data-stu-id="a905a-124">If **AllowDelete** is **false**, an exception is thrown if you call the **Delete** method of the **DataView** or **DataRowView**.</span></span>  
  
 <span data-ttu-id="a905a-125">L’exemple de code suivant désactive l’utilisation du **DataView** pour supprimer des lignes et ajoute une nouvelle ligne à la table sous-jacente à l’aide du **DataView**.</span><span class="sxs-lookup"><span data-stu-id="a905a-125">The following code example disables using the **DataView** to delete rows  and adds a new row to the underlying table using the **DataView**.</span></span>  
  
```vb  
Dim custTable As DataTable = custDS.Tables("Customers")  
Dim custView As DataView = custTable.DefaultView  
custView.Sort = "CompanyName"  
  
custView.AllowDelete = False  
  
Dim newDRV As DataRowView = custView.AddNew()  
newDRV("CustomerID") = "ABCDE"  
newDRV("CompanyName") = "ABC Products"  
newDRV.EndEdit()  
```  
  
```csharp  
DataTable custTable = custDS.Tables["Customers"];  
DataView custView = custTable.DefaultView;  
custView.Sort = "CompanyName";  
  
custView.AllowDelete = false;  
  
DataRowView newDRV = custView.AddNew();  
newDRV["CustomerID"] = "ABCDE";  
newDRV["CompanyName"] = "ABC Products";  
newDRV.EndEdit();  
```  
  
## <a name="see-also"></a><span data-ttu-id="a905a-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a905a-126">See also</span></span>

- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- <xref:System.Data.DataRowView>
- [<span data-ttu-id="a905a-127">DataViews</span><span class="sxs-lookup"><span data-stu-id="a905a-127">DataViews</span></span>](dataviews.md)
- [<span data-ttu-id="a905a-128">Vue d’ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a905a-128">ADO.NET Overview</span></span>](../ado-net-overview.md)
