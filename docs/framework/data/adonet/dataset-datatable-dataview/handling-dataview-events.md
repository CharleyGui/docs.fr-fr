---
title: Gestion des événements de DataView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e5675663-fc91-4e0d-87a9-481b25b64c0f
ms.openlocfilehash: b625fad846c4c6cf008843bff1f6b0eabe0e1de4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151102"
---
# <a name="handling-dataview-events"></a><span data-ttu-id="5b038-102">Gestion des événements de DataView</span><span class="sxs-lookup"><span data-stu-id="5b038-102">Handling DataView Events</span></span>
<span data-ttu-id="5b038-103">Vous pouvez utiliser l'événement <xref:System.Data.DataView.ListChanged> du <xref:System.Data.DataView> pour déterminer si une vue a été mise à jour.</span><span class="sxs-lookup"><span data-stu-id="5b038-103">You can use the <xref:System.Data.DataView.ListChanged> event of the <xref:System.Data.DataView> to determine if a view has been updated.</span></span> <span data-ttu-id="5b038-104">Les mises à jour qui déclenchent l'événement incluent l'ajout, la suppression ou la modification d'une ligne dans la table sous-jacente, l'ajout ou la suppression d'une colonne dans le schéma de la table sous-jacente et une modification d'une relation parente ou enfant.</span><span class="sxs-lookup"><span data-stu-id="5b038-104">Updates that raise the event include adding, deleting, or modifying a row in the underlying table; adding or deleting a column to the schema of the underlying table; and a change in a parent or child relationship.</span></span> <span data-ttu-id="5b038-105">**L’événement ListChanged** vous informe également si la liste des lignes que vous visionez a considérablement changé en raison de l’application d’un nouvel ordre de tri ou d’un filtre.</span><span class="sxs-lookup"><span data-stu-id="5b038-105">The **ListChanged** event also notifies you if the list of rows you are viewing has changed significantly due to the application of a new sort order or a filter.</span></span>  
  
 <span data-ttu-id="5b038-106">**L’événement ListChanged** implémente le délégué <xref:System.ComponentModel> **ListChangedEventHandler** de l’espace de nom et prend comme entrée un <xref:System.ComponentModel.ListChangedEventArgs> objet.</span><span class="sxs-lookup"><span data-stu-id="5b038-106">The **ListChanged** event implements the **ListChangedEventHandler** delegate of the <xref:System.ComponentModel> namespace and takes as input a <xref:System.ComponentModel.ListChangedEventArgs> object.</span></span> <span data-ttu-id="5b038-107">Vous pouvez déterminer quel type de <xref:System.ComponentModel.ListChangedType> changement s’est produit en utilisant la valeur de recensement dans la propriété **ListChangedType** de l’objet **ListChangedEventArgs.**</span><span class="sxs-lookup"><span data-stu-id="5b038-107">You can determine what type of change has occurred using the <xref:System.ComponentModel.ListChangedType> enumeration value in the **ListChangedType** property of the **ListChangedEventArgs** object.</span></span> <span data-ttu-id="5b038-108">Pour les modifications qui impliquent l’ajout, la suppression ou le déplacement des lignes, le nouvel index de la ligne ajoutée ou déplacée et l’index précédent de la rangée supprimée peuvent être consultés à l’aide de la propriété **NewIndex** de **l’objet ListChangedEventArgs.**</span><span class="sxs-lookup"><span data-stu-id="5b038-108">For changes that involve adding, deleting, or moving rows, the new index of the added or moved row and the previous index of the deleted row can be accessed using the **NewIndex** property of the **ListChangedEventArgs** object.</span></span> <span data-ttu-id="5b038-109">Dans le cas d’une ligne déplacée, l’indice précédent de la ligne déplacée peut être consulté à l’aide de la propriété **OldIndex** de **l’objet ListChangedEventArgs.**</span><span class="sxs-lookup"><span data-stu-id="5b038-109">In the case of a moved row, the previous index of the moved row can be accessed using the **OldIndex** property of the **ListChangedEventArgs** object.</span></span>  
  
 <span data-ttu-id="5b038-110">Le **DataViewManager** expose également un événement **ListChanged** pour vous informer si un tableau a été ajouté ou supprimé, ou si un changement a été apporté à la collecte **des relations** du **DataSet**sous-jacent .</span><span class="sxs-lookup"><span data-stu-id="5b038-110">The **DataViewManager** also exposes a **ListChanged** event to notify you if a table has been added or removed, or if a change has been made to the **Relations** collection of the underlying **DataSet**.</span></span>  
  
 <span data-ttu-id="5b038-111">L’exemple de code suivant montre comment ajouter un gestionnaire d’événement **ListChanged.**</span><span class="sxs-lookup"><span data-stu-id="5b038-111">The following code example shows how to add a **ListChanged** event handler.</span></span>  
  
```vb  
AddHandler custView.ListChanged, _  
  New System.ComponentModel.ListChangedEventHandler( _  
  AddressOf OnListChanged)  
  
Private Shared Sub OnListChanged( _  
  sender As Object, args As System.ComponentModel.ListChangedEventArgs)  
  Console.WriteLine("ListChanged:")  
  Console.WriteLine(vbTab & "    Type = " & _  
    System.Enum.GetName(args.ListChangedType.GetType(), _  
    args.ListChangedType))  
  Console.WriteLine(vbTab & "OldIndex = " & args.OldIndex)  
  Console.WriteLine(vbTab & "NewIndex = " & args.NewIndex)  
End Sub  
```  
  
```csharp  
custView.ListChanged  += new
  System.ComponentModel.ListChangedEventHandler(OnListChanged);  
  
protected static void OnListChanged(object sender,
  System.ComponentModel.ListChangedEventArgs args)  
{  
  Console.WriteLine("ListChanged:");  
  Console.WriteLine("\t    Type = " + args.ListChangedType);  
  Console.WriteLine("\tOldIndex = " + args.OldIndex);  
  Console.WriteLine("\tNewIndex = " + args.NewIndex);  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="5b038-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5b038-112">See also</span></span>

- <xref:System.Data.DataView>
- <xref:System.ComponentModel.ListChangedEventHandler>
- [<span data-ttu-id="5b038-113">DataViews</span><span class="sxs-lookup"><span data-stu-id="5b038-113">DataViews</span></span>](dataviews.md)
- [<span data-ttu-id="5b038-114">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="5b038-114">ADO.NET Overview</span></span>](../ado-net-overview.md)
