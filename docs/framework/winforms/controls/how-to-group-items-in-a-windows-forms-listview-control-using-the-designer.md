---
title: 'Procédure : regrouper des éléments dans un contrôle ListView Windows Forms à l’aide du concepteur'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], grouping items
- grouping
- groups [Windows Forms], in Windows Forms controls
ms.assetid: 8b615000-69d9-4c64-acaf-b54fa09b69e3
ms.openlocfilehash: b63bcd9e5e357db350cc2987e09af84eb58bdcff
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039401"
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control-using-the-designer"></a>Procédure : regrouper des éléments dans un contrôle ListView Windows Forms à l’aide du concepteur

La fonctionnalité de regroupement du <xref:System.Windows.Forms.ListView> contrôle vous permet d’afficher des jeux d’éléments associés dans des groupes. Ces groupes sont séparés sur l’écran par des en-têtes de groupe horizontaux qui contiennent les titres des groupes. Vous pouvez utiliser <xref:System.Windows.Forms.ListView> des groupes pour faciliter la navigation dans des listes volumineuses en regroupant les éléments par ordre alphabétique, par date ou par tout autre regroupement logique. L’illustration suivante montre des éléments groupés:

![Nombres séparés en groupes pairs et impairs.](./media/how-to-group-items-in-a-windows-forms-listview-control-using-the-designer/odd-even-list-view-groups.gif)

La procédure suivante requiert un projet d' **application Windows** avec un formulaire contenant <xref:System.Windows.Forms.ListView> un contrôle. Pour plus d’informations sur la configuration d’un tel [projet, consultez Procédure: Créez un projet](/visualstudio/ide/step-1-create-a-windows-forms-application-project) d’application Windows Forms [et procédez comme suit: Ajoutez des contrôles à](how-to-add-controls-to-windows-forms.md)Windows Forms.

Pour activer le regroupement, vous devez d’abord créer un ou <xref:System.Windows.Forms.ListViewGroup> plusieurs objets dans le concepteur ou par programme. Une fois qu’un groupe a été défini, vous pouvez lui affecter des éléments.

> [!NOTE]
> <xref:System.Windows.Forms.ListView>les groupes sont disponibles uniquement [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] sur lorsque votre application appelle <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> la méthode. Sur les systèmes d’exploitation antérieurs, tout code relatif aux groupes n’a aucun effet et les groupes n’apparaissent pas. Pour plus d'informations, consultez <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>.

## <a name="to-add-or-remove-groups-in-the-designer"></a>Pour ajouter ou supprimer des groupes dans le concepteur

1. Dans la fenêtre **Propriétés** , cliquez sur le bouton![de sélection (...) dans le bouton fenêtre Propriétés de Visual Studio.](./media/visual-studio-ellipsis-button.png)) en regard de la <xref:System.Windows.Forms.ListView.Groups%2A> propriété.

     L **'éditeur de collections ListViewGroup** s’affiche.

2. Pour ajouter un groupe, cliquez sur le bouton **Ajouter** . Vous pouvez ensuite définir les propriétés du nouveau groupe, telles que les <xref:System.Windows.Forms.ListViewGroup.Header%2A> propriétés <xref:System.Windows.Forms.ListViewGroup.HeaderAlignment%2A> et. Pour supprimer un groupe, sélectionnez-le et cliquez sur le bouton **supprimer** .

## <a name="to-assign-items-to-groups-in-the-designer"></a>Pour assigner des éléments à des groupes dans le concepteur

1. Dans la fenêtre **Propriétés** , cliquez sur le bouton![de sélection (...) dans le bouton fenêtre Propriétés de Visual Studio.](./media/visual-studio-ellipsis-button.png)) en regard de la <xref:System.Windows.Forms.ListView.Items%2A> propriété.

     L' **éditeur de collections ListViewItem** s’affiche.

2. Pour ajouter un nouvel élément, cliquez sur le bouton **Ajouter** . Vous pouvez ensuite définir les propriétés du nouvel élément, telles que les <xref:System.Windows.Forms.ListViewItem.Text%2A> propriétés <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> et.

3. Sélectionnez la <xref:System.Windows.Forms.ListViewItem.Group%2A> propriété et choisissez un groupe dans la liste déroulante.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.Groups%2A>
- <xref:System.Windows.Forms.ListViewGroup>
- [Contrôle ListView](listview-control-windows-forms.md)
- [Vue d’ensemble du contrôle ListView](listview-control-overview-windows-forms.md)
- [Guide pratique pour Ajouter et supprimer des éléments avec le contrôle ListView Windows Forms](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
