---
title: Vue d'ensemble du contrôle ListView
ms.date: 03/30/2017
f1_keywords:
- ListView
helpviewer_keywords:
- lists
- ListView control [Windows Forms], about ListView control
- list views
ms.assetid: c9ef56c1-3bb1-4101-9f4e-e95e720f2756
ms.openlocfilehash: 9308ff6646704d16b32669827a1f26bebf6958d8
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745157"
---
# <a name="listview-control-overview-windows-forms"></a>Vue d'ensemble du contrôle ListView (Windows Forms)
Le contrôle <xref:System.Windows.Forms.ListView> Windows Forms affiche une liste d'éléments avec des icônes. Vous pouvez utiliser un affichage de liste pour créer une interface utilisateur comme le volet droit de l'Explorateur Windows. Le contrôle a quatre modes d’affichage : LargeIcon, SmallIcon, List et details.  
  
## <a name="what-you-can-do-with-the-listview-control"></a>Ce que vous pouvez faire avec le contrôle ListView  
  
> [!NOTE]
> Un mode d’affichage supplémentaire, vignette, est disponible uniquement sur Windows XP et le système d’exploitation Windows Server 2003. Pour plus d’informations, consultez [Comment : activer l’affichage en mosaïque dans un contrôle ListView Windows Forms](how-to-enable-tile-view-in-a-windows-forms-listview-control.md).  
  
 Le mode LargeIcon affiche de grandes icônes en regard du texte de l’élément. les éléments apparaissent dans plusieurs colonnes si le contrôle est suffisamment grand. Le mode SmallIcon est le même, sauf qu’il affiche de petites icônes. Le mode liste affiche de petites icônes, mais se trouve toujours dans une seule colonne. Le mode Détails affiche les éléments dans plusieurs colonnes. Pour plus d’informations, consultez [Comment : ajouter des colonnes au contrôle ListView Windows Forms](how-to-add-columns-to-the-windows-forms-listview-control.md). Le mode d’affichage est déterminé par la propriété <xref:System.Windows.Forms.ListView.View%2A>. Tous les modes d’affichage peuvent afficher des images à partir de listes d’images. Pour plus d’informations, consultez [Comment : afficher des icônes pour le contrôle ListView Windows Forms](how-to-display-icons-for-the-windows-forms-listview-control.md).  
  
 Le tableau suivant répertorie quelques-uns des membres <xref:System.Windows.Forms.ListView> et les vues dans lesquelles ils sont valides.  
  
|Membre ListView|Consultez la rubrique .|  
|---------------------|----------|  
|Propriété<xref:System.Windows.Forms.ListView.Alignment%2A>|<xref:System.Windows.Forms.View.SmallIcon> ou <xref:System.Windows.Forms.View.LargeIcon>|  
|Propriété<xref:System.Windows.Forms.ListView.AutoArrange%2A>|<xref:System.Windows.Forms.View.SmallIcon> ou <xref:System.Windows.Forms.View.LargeIcon>|  
|Méthode <xref:System.Windows.Forms.ListView.AutoResizeColumn%2A>|<xref:System.Windows.Forms.View.Details>|  
|Propriété<xref:System.Windows.Forms.ListView.Columns%2A>|<xref:System.Windows.Forms.View.Details> ou <xref:System.Windows.Forms.View.Tile>|  
|Événement<xref:System.Windows.Forms.ListView.DrawSubItem>|<xref:System.Windows.Forms.View.Details>|  
|Méthode <xref:System.Windows.Forms.ListView.FindItemWithText%2A>|<xref:System.Windows.Forms.View.Details>, <xref:System.Windows.Forms.View.List> ou <xref:System.Windows.Forms.View.Tile>|  
|Méthode <xref:System.Windows.Forms.ListView.FindNearestItem%2A>|<xref:System.Windows.Forms.View.SmallIcon> ou <xref:System.Windows.Forms.View.LargeIcon>|  
|Méthode <xref:System.Windows.Forms.ListView.GetItemAt%2A>|<xref:System.Windows.Forms.View.Details> ou <xref:System.Windows.Forms.View.Tile>|  
|Propriété<xref:System.Windows.Forms.ListView.Groups%2A>|Toutes les vues sauf <xref:System.Windows.Forms.View.List>|  
|Propriété<xref:System.Windows.Forms.ListView.HeaderStyle%2A>|<xref:System.Windows.Forms.View.Details>.|  
|Propriété<xref:System.Windows.Forms.ListView.InsertionMark%2A>|<xref:System.Windows.Forms.View.LargeIcon>, <xref:System.Windows.Forms.View.SmallIcon> ou <xref:System.Windows.Forms.View.Tile>|  
  
 La propriété de clé du contrôle <xref:System.Windows.Forms.ListView> est <xref:System.Windows.Forms.ListView.Items%2A>, qui contient les éléments affichés par le contrôle. La propriété <xref:System.Windows.Forms.ListView.SelectedItems%2A> contient une collection des éléments actuellement sélectionnés dans le contrôle. L’utilisateur peut sélectionner plusieurs éléments, par exemple pour glisser-déplacer plusieurs éléments à la fois vers un autre contrôle, si la propriété <xref:System.Windows.Forms.ListView.MultiSelect%2A> est définie sur `true`. Le contrôle <xref:System.Windows.Forms.ListView> peut afficher des cases à cocher en regard des éléments, si la propriété <xref:System.Windows.Forms.ListView.CheckBoxes%2A> est définie sur `true`.  
  
 La propriété <xref:System.Windows.Forms.ListView.Activation%2A> détermine le type d’action que l’utilisateur doit effectuer pour activer un élément dans la liste : les options sont <xref:System.Windows.Forms.ItemActivation.Standard>, <xref:System.Windows.Forms.ItemActivation.OneClick>et <xref:System.Windows.Forms.ItemActivation.TwoClick>. <xref:System.Windows.Forms.ItemActivation.OneClick> activation nécessite un simple clic pour activer l’élément. <xref:System.Windows.Forms.ItemActivation.TwoClick> activation nécessite que l’utilisateur double-clique pour activer l’élément. un clic simple modifie la couleur du texte de l’élément. <xref:System.Windows.Forms.ItemActivation.Standard> activation nécessite que l’utilisateur double-clique pour activer un élément, mais l’élément ne change pas d’apparence.  
  
 Le contrôle <xref:System.Windows.Forms.ListView> prend également en charge les styles visuels et les autres fonctionnalités disponibles sur la plateforme Windows XP, y compris le regroupement, l’affichage en mosaïque et les marques d’insertion.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.ListView>
- [ListView, contrôle](listview-control-windows-forms.md)
- [Guide pratique pour ajouter et supprimer des éléments avec le contrôle ListView Windows Forms](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [Guide pratique pour ajouter des colonnes au contrôle ListView Windows Forms](how-to-add-columns-to-the-windows-forms-listview-control.md)
- [Guide pratique pour afficher des icônes pour le contrôle ListView Windows Forms](how-to-display-icons-for-the-windows-forms-listview-control.md)
- [Guide pratique pour afficher des sous-éléments en colonnes avec le contrôle ListView Windows Forms](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)
- [Guide pratique pour sélectionner un élément dans le contrôle ListView Windows Forms](how-to-select-an-item-in-the-windows-forms-listview-control.md)
- [Guide pratique pour grouper des éléments dans un contrôle ListView Windows Forms](how-to-group-items-in-a-windows-forms-listview-control.md)
- [Guide pratique pour afficher une marque d'insertion dans un contrôle ListView Windows Forms](how-to-display-an-insertion-mark-in-a-windows-forms-listview-control.md)
- [Guide pratique pour ajouter des fonctions de recherche à un contrôle ListView](how-to-add-search-capabilities-to-a-listview-control.md)
- [Guide pratique pour ajouter des informations personnalisées à un contrôle TreeView ou ListView (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
- [Guide pratique pour créer une interface utilisateur à plusieurs volets à l'aide des Windows Forms](how-to-create-a-multipane-user-interface-with-windows-forms.md)
