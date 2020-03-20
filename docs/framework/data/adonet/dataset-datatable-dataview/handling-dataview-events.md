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
# <a name="handling-dataview-events"></a>Gestion des événements de DataView
Vous pouvez utiliser l'événement <xref:System.Data.DataView.ListChanged> du <xref:System.Data.DataView> pour déterminer si une vue a été mise à jour. Les mises à jour qui déclenchent l'événement incluent l'ajout, la suppression ou la modification d'une ligne dans la table sous-jacente, l'ajout ou la suppression d'une colonne dans le schéma de la table sous-jacente et une modification d'une relation parente ou enfant. **L’événement ListChanged** vous informe également si la liste des lignes que vous visionez a considérablement changé en raison de l’application d’un nouvel ordre de tri ou d’un filtre.  
  
 **L’événement ListChanged** implémente le délégué <xref:System.ComponentModel> **ListChangedEventHandler** de l’espace de nom et prend comme entrée un <xref:System.ComponentModel.ListChangedEventArgs> objet. Vous pouvez déterminer quel type de <xref:System.ComponentModel.ListChangedType> changement s’est produit en utilisant la valeur de recensement dans la propriété **ListChangedType** de l’objet **ListChangedEventArgs.** Pour les modifications qui impliquent l’ajout, la suppression ou le déplacement des lignes, le nouvel index de la ligne ajoutée ou déplacée et l’index précédent de la rangée supprimée peuvent être consultés à l’aide de la propriété **NewIndex** de **l’objet ListChangedEventArgs.** Dans le cas d’une ligne déplacée, l’indice précédent de la ligne déplacée peut être consulté à l’aide de la propriété **OldIndex** de **l’objet ListChangedEventArgs.**  
  
 Le **DataViewManager** expose également un événement **ListChanged** pour vous informer si un tableau a été ajouté ou supprimé, ou si un changement a été apporté à la collecte **des relations** du **DataSet**sous-jacent .  
  
 L’exemple de code suivant montre comment ajouter un gestionnaire d’événement **ListChanged.**  
  
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
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Data.DataView>
- <xref:System.ComponentModel.ListChangedEventHandler>
- [DataViews](dataviews.md)
- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)
