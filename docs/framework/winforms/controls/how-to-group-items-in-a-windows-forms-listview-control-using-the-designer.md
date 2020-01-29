---
title: Regrouper des éléments dans un contrôle ListView à l’aide du concepteur
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], grouping items
- grouping
- groups [Windows Forms], in Windows Forms controls
ms.assetid: 8b615000-69d9-4c64-acaf-b54fa09b69e3
ms.openlocfilehash: 935d8d75517e1028e686ca229f6ada656f58b01e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736686"
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control-using-the-designer"></a>Comment : regrouper des éléments dans un contrôle ListView Windows Forms à l'aide du concepteur

La fonctionnalité de regroupement du contrôle <xref:System.Windows.Forms.ListView> vous permet d’afficher des jeux d’éléments associés dans des groupes. Ces groupes sont séparés sur l’écran par des en-têtes de groupe horizontaux qui contiennent les titres des groupes. Vous pouvez utiliser des groupes de <xref:System.Windows.Forms.ListView> pour faciliter la navigation dans des listes volumineuses en regroupant les éléments par ordre alphabétique, par date ou par tout autre regroupement logique. L’illustration suivante montre des éléments groupés :

![Nombres séparés en groupes pairs et impairs.](./media/how-to-group-items-in-a-windows-forms-listview-control-using-the-designer/odd-even-list-view-groups.gif)

La procédure suivante requiert un projet d' **application Windows** avec un formulaire contenant un contrôle de <xref:System.Windows.Forms.ListView>. Pour plus d’informations sur la configuration d’un tel projet, consultez [Comment : créer un projet d’application Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) et [Comment : ajouter des contrôles à des Windows Forms](how-to-add-controls-to-windows-forms.md).

Pour activer le regroupement, vous devez d’abord créer un ou plusieurs objets <xref:System.Windows.Forms.ListViewGroup> dans le concepteur ou par programme. Une fois qu’un groupe a été défini, vous pouvez lui affecter des éléments.

## <a name="to-add-or-remove-groups-in-the-designer"></a>Pour ajouter ou supprimer des groupes dans le concepteur

1. Dans la fenêtre **Propriétés** , cliquez sur les **points de suspension** (![le bouton de sélection (...) du bouton fenêtre Propriétés de Visual Studio.](./media/visual-studio-ellipsis-button.png)) en regard de la propriété <xref:System.Windows.Forms.ListView.Groups%2A>.

     L **'éditeur de collections ListViewGroup** s’affiche.

2. Pour ajouter un groupe, cliquez sur le bouton **Ajouter** . Vous pouvez ensuite définir les propriétés du nouveau groupe, telles que les propriétés <xref:System.Windows.Forms.ListViewGroup.Header%2A> et <xref:System.Windows.Forms.ListViewGroup.HeaderAlignment%2A>. Pour supprimer un groupe, sélectionnez-le et cliquez sur le bouton **supprimer** .

## <a name="to-assign-items-to-groups-in-the-designer"></a>Pour assigner des éléments à des groupes dans le concepteur

1. Dans la fenêtre **Propriétés** , cliquez sur les **points de suspension** (![le bouton de sélection (...) du bouton fenêtre Propriétés de Visual Studio.](./media/visual-studio-ellipsis-button.png)) en regard de la propriété <xref:System.Windows.Forms.ListView.Items%2A>.

     L' **éditeur de collections ListViewItem** s’affiche.

2. Pour ajouter un nouvel élément, cliquez sur le bouton **Ajouter** . Vous pouvez ensuite définir les propriétés du nouvel élément, telles que les propriétés <xref:System.Windows.Forms.ListViewItem.Text%2A> et <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A>.

3. Sélectionnez la propriété <xref:System.Windows.Forms.ListViewItem.Group%2A> et choisissez un groupe dans la liste déroulante.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.Groups%2A>
- <xref:System.Windows.Forms.ListViewGroup>
- [ListView, contrôle](listview-control-windows-forms.md)
- [Vue d’ensemble du contrôle ListView](listview-control-overview-windows-forms.md)
- [Guide pratique pour ajouter et supprimer des éléments avec le contrôle ListView Windows Forms](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
