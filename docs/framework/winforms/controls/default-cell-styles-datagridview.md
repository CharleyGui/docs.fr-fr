---
title: 'Procédure : définir des styles de cellules par défaut et des formats de données pour le contrôle DataGridView Windows Forms à l’aide du concepteur'
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], cell styles
- cells [Windows Forms], setting styles
- data formats
- data [Windows Forms], setting formats
ms.assetid: fc6da49f-8942-41da-b49f-b2afc38cc656
ms.openlocfilehash: 6d7d867b7c9e83b68589e046565bfb0199692f5f
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69658511"
---
# <a name="how-to-set-default-cell-styles-and-data-formats-for-the-windows-forms-datagridview-control-using-the-designer"></a>Procédure : définir des styles de cellules par défaut et des formats de données pour le contrôle DataGridView Windows Forms à l’aide du concepteur

Le <xref:System.Windows.Forms.DataGridView> contrôle vous permet de spécifier des styles de cellules et des formats de données de cellule par défaut pour l’ensemble du contrôle, pour des colonnes spécifiques, pour les en-têtes de ligne et de colonne, et pour les lignes en alternance afin de créer un effet comptable. Les styles par défaut définis pour l’ensemble du contrôle sont remplacés par les styles par défaut définis pour les colonnes et les lignes en alternance. En outre, les styles que vous définissez dans le code pour les lignes et les cellules individuelles remplacent les styles par défaut.

Pour plus d’informations sur les styles de cellules, consultez [styles de cellule dans le contrôle DataGridView Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md). Pour définir des styles pour les lignes en alternance, [consultez Procédure: Définissez des styles de ligne en alternance pour le contrôle DataGridView Windows Forms à l'](set-alternating-row-styles-for-the-datagrid-using-the-designer.md)aide du concepteur.

Vous pouvez également définir des styles à <xref:System.Windows.Forms.DataGridView.RowTemplate%2A> l’aide de la propriété pour affecter toutes les lignes qui seront ajoutées au contrôle. Pour plus d’informations sur le modèle de ligne [, consultez Procédure: Utilisez le modèle de ligne pour personnaliser les lignes du contrôle](use-the-row-template-to-customize-rows-in-the-datagrid.md)DataGridView Windows Forms.

Les procédures suivantes requièrent un projet d' **application Windows** avec un formulaire <xref:System.Windows.Forms.DataGridView> contenant un contrôle. Pour plus d’informations sur la configuration d’un tel [projet, consultez Procédure: Créez un projet](/visualstudio/ide/step-1-create-a-windows-forms-application-project) d’application Windows Forms [et procédez comme suit: Ajoutez des contrôles à](how-to-add-controls-to-windows-forms.md)Windows Forms.

### <a name="to-set-default-styles-for-all-cells-in-the-control"></a>Pour définir les styles par défaut de toutes les cellules du contrôle

1. Sélectionnez le <xref:System.Windows.Forms.DataGridView> contrôle dans le concepteur.

2. Dans la **fenêtre Propriétés** , cliquez sur le bouton de![sélection (le bouton de sélection (...) dans le fenêtre Propriétés de](./media/visual-studio-ellipsis-button.png)Visual Studio.) en <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A>regard de <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A> la <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A>propriété, ou. La boîte de dialogue **Générateur CellStyle** s’affiche.

3. Définissez le style en définissant les propriétés à l’aide du volet de **visualisation** pour confirmer vos choix.

> [!NOTE]
> Si les styles visuels sont activés, les en-têtes de lignes et de <xref:System.Windows.Forms.DataGridView.TopLeftHeaderCell%2A>colonnes (à l’exception de) sont automatiquement mis en forme par <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A> le <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A> thème actuel, remplaçant ainsi les valeurs de propriété et.
>
> Vous pouvez définir des styles de cellule pour <xref:System.Windows.Forms.DataGridView> plusieurs contrôles sélectionnés à l’aide du concepteur, mais uniquement s’ils ont des valeurs identiques pour la propriété de style de cellule que vous souhaitez modifier. Si des styles de cellule diffèrent pour cette propriété, les fenêtres de **Propriétés** de la boîte de dialogue **Générateur CellStyle** sont vides.

### <a name="to-set-default-styles-for-cells-in-individual-columns"></a>Pour définir les styles par défaut des cellules dans des colonnes individuelles

1. Cliquez avec le bouton <xref:System.Windows.Forms.DataGridView> droit sur le contrôle dans le concepteur, puis choisissez **modifier les colonnes**.

2. Sélectionnez une colonne dans la liste **colonnes sélectionnées** .

3. Dans la grille des **Propriétés** de la colonne, cliquez sur![le bouton de sélection (...) dans le fenêtre Propriétés de Visual Studio](./media/visual-studio-ellipsis-button.png).) en regard <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> de la propriété. La boîte de dialogue **Générateur CellStyle** s’affiche.

4. Définissez le style en définissant les propriétés à l’aide du volet de **visualisation** pour confirmer vos choix.

### <a name="to-format-data-in-cells"></a>Pour mettre en forme des données dans des cellules

1. Utilisez l’une des procédures précédentes pour afficher une boîte de dialogue **Générateur CellStyle** liée à une propriété de style de cellule par défaut.

2. Dans la boîte de dialogue **Générateur CellStyle** , cliquez sur le bouton![de sélection (...) dans le fenêtre Propriétés de Visual Studio.](./media/visual-studio-ellipsis-button.png)) en regard de la <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> propriété. La boîte de dialogue **chaîne de format** s’affiche.

3. Sélectionnez un type de format, puis modifiez les détails du type (par exemple, le nombre de décimales à afficher) à l’aide de la zone **exemple** pour confirmer vos choix.

4. Si vous liez le <xref:System.Windows.Forms.DataGridView> contrôle à une source de données qui est susceptible de contenir des valeurs NULL, renseignez la zone de texte **valeur null** . Cette valeur est affichée lorsque la valeur de cellule est égale à une référence null`Nothing` (dans Visual Basic) <xref:System.DBNull.Value?displayProperty=nameWithType>ou.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A?displayProperty=nameWithType>
- [Styles de cellules dans le contrôle DataGridView Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Guide pratique pour Définir des styles de ligne en alternance pour le contrôle DataGridView Windows Forms à l’aide du concepteur](set-alternating-row-styles-for-the-datagrid-using-the-designer.md)
- [Guide pratique : Créer un projet Application Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Guide pratique pour Ajouter des contrôles à Windows Forms](how-to-add-controls-to-windows-forms.md)
