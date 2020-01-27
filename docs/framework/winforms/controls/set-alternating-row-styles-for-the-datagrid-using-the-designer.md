---
title: Définir des styles de ligne en alternance pour le contrôle DataGridView à l’aide du concepteur
ms.date: 03/30/2017
helpviewer_keywords:
- ledger-like formats
- DataGridView control [Windows Forms], row style alternation
- Windows Forms, rows
- rows [Windows Forms], alternating
- data [Windows Forms], displaying
ms.assetid: 02373442-bf94-4470-9f8a-e44c4a9d5b88
ms.openlocfilehash: 74f65d03a359136de943f8a2937ed5e5f1e62519
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743049"
---
# <a name="how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control-using-the-designer"></a>Comment : définir des styles de ligne en alternance pour le contrôle DataGridView Windows Forms à l'aide du concepteur

Les données tabulaires sont souvent présentées dans un format de type comptabilité où les lignes alternées ont des couleurs d’arrière-plan différentes. Avec ce format, il est facile pour les utilisateurs de déterminer quelle cellule appartient à quelle ligne, en particulier dans les tableaux larges qui ont beaucoup de colonnes.

Avec le contrôle <xref:System.Windows.Forms.DataGridView>, vous pouvez spécifier des informations de style complètes pour les lignes en alternance. Vous pouvez utiliser des caractéristiques de style telles que la couleur de premier plan et la police, en plus de la couleur d’arrière-plan, pour différencier les lignes alternées. Pour plus d’informations, consultez [styles de cellule dans le contrôle DataGridView Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md).

La procédure suivante requiert un projet d' **application Windows** avec un formulaire contenant un contrôle de <xref:System.Windows.Forms.DataGridView>. Pour plus d’informations sur la configuration d’un tel projet, consultez [Comment : créer un projet d’application Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) et [Comment : ajouter des contrôles à des Windows Forms](how-to-add-controls-to-windows-forms.md).

### <a name="define-styles-for-alternating-rows"></a>Définir des styles pour les lignes en alternance

1. Sélectionnez le contrôle <xref:System.Windows.Forms.DataGridView> dans le concepteur.

2. Dans la fenêtre **Propriétés** , cliquez sur le bouton de sélection (![le bouton de sélection (...) dans la fenêtre Propriétés de Visual Studio.](./media/visual-studio-ellipsis-button.png)) en regard de la propriété <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A>.

3. Dans la boîte de dialogue **Générateur CellStyle** , définissez le style en définissant les propriétés et utilisez le volet de **visualisation** pour confirmer vos choix. Les styles que vous spécifiez sont utilisés pour toutes les autres lignes affichées dans le contrôle, en commençant par le deuxième.

4. Pour définir des styles pour les lignes restantes, répétez les étapes 2 et 3 à l’aide de la propriété <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A>.

    > [!NOTE]
    > Les cellules sont affichées à l’aide de styles hérités de plusieurs propriétés. Pour plus d’informations sur l’héritage de style, consultez [styles de cellule dans le contrôle DataGridView Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md).

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.DataGridView>
- [Styles de cellules dans le contrôle DataGridView Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Mises en forme et styles de base dans le contrôle DataGridView Windows Forms](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [Utilisation du concepteur avec le contrôle DataGridView Windows Forms](using-the-designer-with-the-windows-forms-datagridview-control.md)
- [Comment : créer un projet d’application Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Comment : ajouter des contrôles à des Windows Forms](how-to-add-controls-to-windows-forms.md)
