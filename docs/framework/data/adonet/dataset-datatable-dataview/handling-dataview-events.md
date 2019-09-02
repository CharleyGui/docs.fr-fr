---
title: Gestion des événements de DataView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e5675663-fc91-4e0d-87a9-481b25b64c0f
ms.openlocfilehash: b3a1077bff9bf457b4aef0b05357d4a9260f8973
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204820"
---
# <a name="handling-dataview-events"></a>Gestion des événements de DataView
Vous pouvez utiliser l'événement <xref:System.Data.DataView.ListChanged> du <xref:System.Data.DataView> pour déterminer si une vue a été mise à jour. Les mises à jour qui déclenchent l'événement incluent l'ajout, la suppression ou la modification d'une ligne dans la table sous-jacente, l'ajout ou la suppression d'une colonne dans le schéma de la table sous-jacente et une modification d'une relation parente ou enfant. L’événement **ListChanged** vous avertit également si la liste des lignes que vous affichez a changé de manière significative en raison de l’application d’un nouvel ordre de tri ou d’un filtre.  
  
 L’événement **ListChanged** implémente le délégué **ListChangedEventHandler** de l' <xref:System.ComponentModel> espace de noms et prend comme <xref:System.ComponentModel.ListChangedEventArgs> entrée un objet. Vous pouvez déterminer le type de modification qui s’est produit <xref:System.ComponentModel.ListChangedType> à l’aide de la valeur d’énumération dans la propriété **ListChangedType** de l’objet **ListChangedEventArgs** . Pour les modifications qui impliquent l’ajout, la suppression ou le déplacement de lignes, il est possible d’accéder au nouvel index de la ligne ajoutée ou déplacée et à l’index précédent de la ligne supprimée à l’aide de la propriété **NewIndex** de l’objet **ListChangedEventArgs** . Dans le cas d’une ligne déplacée, l’index précédent de la ligne déplacée est accessible à l’aide de la propriété **OldIndex** de l’objet **ListChangedEventArgs** .  
  
 Le **DataViewManager** expose également un événement **ListChanged** pour vous avertir si une table a été ajoutée ou supprimée, ou si une modification a été apportée à la collection **relations** du **DataSet**sous-jacent.  
  
 L’exemple de code suivant montre comment ajouter un gestionnaire d’événements **ListChanged** .  
  
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
- [Fournisseurs managés ADO.NET et centre de développement DataSet](https://go.microsoft.com/fwlink/?LinkId=217917)
