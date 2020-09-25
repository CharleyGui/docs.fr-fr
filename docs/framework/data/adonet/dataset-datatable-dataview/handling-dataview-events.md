---
title: Gestion des événements de DataView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e5675663-fc91-4e0d-87a9-481b25b64c0f
ms.openlocfilehash: 2a67cb040c5d438d17ad91d41e97f24f3166262b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204539"
---
# <a name="handling-dataview-events"></a><span data-ttu-id="c4f12-102">Gestion des événements de DataView</span><span class="sxs-lookup"><span data-stu-id="c4f12-102">Handling DataView Events</span></span>

<span data-ttu-id="c4f12-103">Vous pouvez utiliser l'événement <xref:System.Data.DataView.ListChanged> du <xref:System.Data.DataView> pour déterminer si une vue a été mise à jour.</span><span class="sxs-lookup"><span data-stu-id="c4f12-103">You can use the <xref:System.Data.DataView.ListChanged> event of the <xref:System.Data.DataView> to determine if a view has been updated.</span></span> <span data-ttu-id="c4f12-104">Les mises à jour qui déclenchent l'événement incluent l'ajout, la suppression ou la modification d'une ligne dans la table sous-jacente, l'ajout ou la suppression d'une colonne dans le schéma de la table sous-jacente et une modification d'une relation parente ou enfant.</span><span class="sxs-lookup"><span data-stu-id="c4f12-104">Updates that raise the event include adding, deleting, or modifying a row in the underlying table; adding or deleting a column to the schema of the underlying table; and a change in a parent or child relationship.</span></span> <span data-ttu-id="c4f12-105">L’événement **ListChanged** vous avertit également si la liste des lignes que vous affichez a changé de manière significative en raison de l’application d’un nouvel ordre de tri ou d’un filtre.</span><span class="sxs-lookup"><span data-stu-id="c4f12-105">The **ListChanged** event also notifies you if the list of rows you are viewing has changed significantly due to the application of a new sort order or a filter.</span></span>  
  
 <span data-ttu-id="c4f12-106">L’événement **ListChanged** implémente le délégué **ListChangedEventHandler** de l' <xref:System.ComponentModel> espace de noms et prend comme entrée un <xref:System.ComponentModel.ListChangedEventArgs> objet.</span><span class="sxs-lookup"><span data-stu-id="c4f12-106">The **ListChanged** event implements the **ListChangedEventHandler** delegate of the <xref:System.ComponentModel> namespace and takes as input a <xref:System.ComponentModel.ListChangedEventArgs> object.</span></span> <span data-ttu-id="c4f12-107">Vous pouvez déterminer le type de modification qui s’est produit à l’aide de la <xref:System.ComponentModel.ListChangedType> valeur d’énumération dans la propriété **ListChangedType** de l’objet **ListChangedEventArgs** .</span><span class="sxs-lookup"><span data-stu-id="c4f12-107">You can determine what type of change has occurred using the <xref:System.ComponentModel.ListChangedType> enumeration value in the **ListChangedType** property of the **ListChangedEventArgs** object.</span></span> <span data-ttu-id="c4f12-108">Pour les modifications qui impliquent l’ajout, la suppression ou le déplacement de lignes, il est possible d’accéder au nouvel index de la ligne ajoutée ou déplacée et à l’index précédent de la ligne supprimée à l’aide de la propriété **NewIndex** de l’objet **ListChangedEventArgs** .</span><span class="sxs-lookup"><span data-stu-id="c4f12-108">For changes that involve adding, deleting, or moving rows, the new index of the added or moved row and the previous index of the deleted row can be accessed using the **NewIndex** property of the **ListChangedEventArgs** object.</span></span> <span data-ttu-id="c4f12-109">Dans le cas d’une ligne déplacée, l’index précédent de la ligne déplacée est accessible à l’aide de la propriété **OldIndex** de l’objet **ListChangedEventArgs** .</span><span class="sxs-lookup"><span data-stu-id="c4f12-109">In the case of a moved row, the previous index of the moved row can be accessed using the **OldIndex** property of the **ListChangedEventArgs** object.</span></span>  
  
 <span data-ttu-id="c4f12-110">Le **DataViewManager** expose également un événement **ListChanged** pour vous avertir si une table a été ajoutée ou supprimée, ou si une modification a été apportée à la collection **relations** du **DataSet**sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="c4f12-110">The **DataViewManager** also exposes a **ListChanged** event to notify you if a table has been added or removed, or if a change has been made to the **Relations** collection of the underlying **DataSet**.</span></span>  
  
 <span data-ttu-id="c4f12-111">L’exemple de code suivant montre comment ajouter un gestionnaire d’événements **ListChanged** .</span><span class="sxs-lookup"><span data-stu-id="c4f12-111">The following code example shows how to add a **ListChanged** event handler.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c4f12-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c4f12-112">See also</span></span>

- <xref:System.Data.DataView>
- <xref:System.ComponentModel.ListChangedEventHandler>
- [<span data-ttu-id="c4f12-113">DataViews</span><span class="sxs-lookup"><span data-stu-id="c4f12-113">DataViews</span></span>](dataviews.md)
- [<span data-ttu-id="c4f12-114">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="c4f12-114">ADO.NET Overview</span></span>](../ado-net-overview.md)
