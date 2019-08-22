---
title: 'Procédure : définir des styles de ligne alternée pour le contrôle DataGridView Windows Forms à l’aide du concepteur'
ms.date: 03/30/2017
helpviewer_keywords:
- ledger-like formats
- DataGridView control [Windows Forms], row style alternation
- Windows Forms, rows
- rows [Windows Forms], alternating
- data [Windows Forms], displaying
ms.assetid: 02373442-bf94-4470-9f8a-e44c4a9d5b88
ms.openlocfilehash: a24b4e6af98d2637ecae2352aaa881adcd1c1a45
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666844"
---
# <a name="how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control-using-the-designer"></a>Procédure : définir des styles de ligne alternée pour le contrôle DataGridView Windows Forms à l’aide du concepteur

Les données tabulaires sont souvent présentées dans un format de type comptabilité où les lignes alternées ont des couleurs d’arrière-plan différentes. Avec ce format, il est facile pour les utilisateurs de déterminer quelle cellule appartient à quelle ligne, en particulier dans les tableaux larges qui ont beaucoup de colonnes.

Avec le contrôle <xref:System.Windows.Forms.DataGridView>, vous pouvez spécifier des informations de style complètes pour les lignes en alternance. Vous pouvez utiliser des caractéristiques de style telles que la couleur de premier plan et la police, en plus de la couleur d’arrière-plan, pour différencier les lignes alternées. Pour plus d’informations, consultez [styles de cellule dans le contrôle DataGridView Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md).

La procédure suivante requiert un projet d' **application Windows** avec un formulaire contenant <xref:System.Windows.Forms.DataGridView> un contrôle. Pour plus d’informations sur la configuration d’un tel [projet, consultez Procédure: Créez un projet](/visualstudio/ide/step-1-create-a-windows-forms-application-project) d’application Windows Forms [et procédez comme suit: Ajoutez des contrôles à](how-to-add-controls-to-windows-forms.md)Windows Forms.

### <a name="define-styles-for-alternating-rows"></a>Définir des styles pour les lignes en alternance

1. Sélectionnez le <xref:System.Windows.Forms.DataGridView> contrôle dans le concepteur.

2. Dans la fenêtre **Propriétés** , cliquez sur le bouton de![sélection (le bouton de sélection (...) dans le fenêtre Propriétés de](./media/visual-studio-ellipsis-button.png)Visual Studio.) <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> en regard de la propriété.

3. Dans la boîte de dialogue **Générateur CellStyle** , définissez le style en définissant les propriétés et utilisez le volet de **visualisation** pour confirmer vos choix. Les styles que vous spécifiez sont utilisés pour toutes les autres lignes affichées dans le contrôle, en commençant par le deuxième.

4. Pour définir des styles pour les lignes restantes, répétez les étapes <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> 2 et 3 à l’aide de la propriété.

    > [!NOTE]
    > Les cellules sont affichées à l’aide de styles hérités de plusieurs propriétés. Pour plus d’informations sur l’héritage de style, consultez [styles de cellule dans le contrôle DataGridView Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md).

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.DataGridView>
- [Styles de cellules dans le contrôle DataGridView Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Mises en forme et styles de base dans le contrôle DataGridView Windows Forms](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [Utilisation du concepteur avec le contrôle DataGridView Windows Forms](using-the-designer-with-the-windows-forms-datagridview-control.md)
- [Guide pratique pour Créer un projet Application Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Guide pratique : Ajouter des contrôles à Windows Forms](how-to-add-controls-to-windows-forms.md)
