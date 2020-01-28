---
title: Ajouter des tables et des colonnes au contrôle DataGrid à l’aide du concepteur
ms.date: 03/30/2017
helpviewer_keywords:
- columns [Windows Forms], adding to DataGrid control
- tables [Windows Forms], adding to DataGrid control
- DataGrid control [Windows Forms], adding tables and columns
ms.assetid: 4a6d1b34-b696-476b-bf8a-57c6230aa9e1
ms.openlocfilehash: fed7465fbe665b1945161653616e3a21640e0b2a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746263"
---
# <a name="how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control-using-the-designer"></a>Comment : ajouter des tables et des colonnes au contrôle DataGrid Windows Forms à l'aide du concepteur

> [!NOTE]
> Le contrôle <xref:System.Windows.Forms.DataGridView> remplace le contrôle <xref:System.Windows.Forms.DataGrid> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.DataGrid> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix. Pour plus d’informations, consultez [Différences entre les contrôles DataGridView et DataGrid Windows Forms](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).

Vous pouvez afficher des données dans le contrôle Windows Forms <xref:System.Windows.Forms.DataGrid> dans les tables et les colonnes en créant <xref:System.Windows.Forms.DataGridTableStyle> objets et en les ajoutant à l’objet <xref:System.Windows.Forms.GridTableStylesCollection>, accessible via la propriété <xref:System.Windows.Forms.DataGrid> du contrôle <xref:System.Windows.Forms.DataGrid.TableStyles%2A>. Chaque style de table affiche le contenu de la table de données spécifiée dans la propriété <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> du <xref:System.Windows.Forms.DataGridTableStyle>. Par défaut, un style de table sans les styles de colonne spécifiés affiche toutes les colonnes de cette table de données. Vous pouvez limiter les colonnes de la table en ajoutant des objets <xref:System.Windows.Forms.DataGridColumnStyle> à l' <xref:System.Windows.Forms.GridColumnStylesCollection>, accessible via la propriété <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> de chaque <xref:System.Windows.Forms.DataGridTableStyle>.

Les procédures suivantes requièrent un projet d' **application Windows** avec un formulaire qui contient un contrôle de <xref:System.Windows.Forms.DataGrid>. Pour plus d’informations sur la façon de configurer ce type de projet, consultez [Comment : créer un projet d’application Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) et [Comment : ajouter des contrôles à des Windows Forms](how-to-add-controls-to-windows-forms.md). Par défaut, dans Visual Studio 2005, le contrôle <xref:System.Windows.Forms.DataGrid> ne se trouve pas dans la **boîte à outils**. Pour plus d’informations sur l’ajout de ce dernier, consultez [Comment : ajouter des éléments à la boîte à outils](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165355(v=vs.100)).

### <a name="to-add-a-table-to-the-datagrid-control-in-the-designer"></a>Pour ajouter une table au contrôle DataGrid dans le concepteur

1. Pour afficher des données dans la table, vous devez d’abord lier le contrôle <xref:System.Windows.Forms.DataGrid> à un DataSet. Pour plus d’informations, consultez [Comment : lier le contrôle Windows Forms DataGrid à une source de données à l’aide du concepteur](bind-wf-datagrid-control-to-a-data-source-using-the-designer.md).

2. Sélectionnez la propriété <xref:System.Windows.Forms.DataGrid.TableStyles%2A> du contrôle <xref:System.Windows.Forms.DataGrid> dans le Fenêtre Propriétés, puis cliquez sur le bouton de sélection (![le bouton de sélection (...) dans la Fenêtre Propriétés de Visual Studio.](./media/visual-studio-ellipsis-button.png)) en regard de la propriété pour afficher l **'éditeur de collections DataGridTableStyle**.

3. Dans l’éditeur de collections, cliquez sur **Ajouter** pour insérer un style de tableau.

4. Cliquez sur **OK** pour fermer l’éditeur de collections, puis rouvrez-le en cliquant sur le bouton de sélection en regard de la propriété <xref:System.Windows.Forms.DataGrid.TableStyles%2A>.

     Lorsque vous rouvrez l’éditeur de collections, toutes les tables de données liées au contrôle s’affichent dans la liste déroulante de la propriété <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> du style de table.

5. Dans la zone **membres** de l’éditeur de collections, cliquez sur le style de table.

6. Dans la zone **Propriétés** de l’éditeur de collections, sélectionnez la valeur <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> de la table que vous souhaitez afficher.

### <a name="to-add-a-column-to-the-datagrid-control-in-the-designer"></a>Pour ajouter une colonne au contrôle DataGrid dans le concepteur

1. Dans la zone **membres** de l **'éditeur de collections DataGridTableStyle**, sélectionnez le style de table approprié. Dans la zone **Propriétés** de l’éditeur de collections, sélectionnez la collection <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A>, puis cliquez sur le bouton de sélection (![le bouton de sélection (...) dans le fenêtre Propriétés de Visual Studio.](./media/visual-studio-ellipsis-button.png)) en regard de la propriété pour afficher l' **éditeur de collections DataGridColumnStyle**.

2. Dans l’éditeur de collections, cliquez sur **Ajouter** pour insérer un style de colonne ou cliquez sur la flèche vers le bas en regard de **Ajouter** pour spécifier un type de colonne.

     Dans la zone de liste déroulante, vous pouvez sélectionner le <xref:System.Windows.Forms.DataGridTextBoxColumn> ou le type de <xref:System.Windows.Forms.DataGridBoolColumn>.

3. Cliquez sur OK pour fermer l **'éditeur de collections DataGridColumnStyle**, puis rouvrez-le en cliquant sur le bouton de sélection en regard de la propriété <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A>.

     Lorsque vous rouvrez l’éditeur de collections, toutes les colonnes de données de la table de données liée s’affichent dans la liste déroulante de la propriété <xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A> du style de colonne.

4. Dans la zone **membres** de l’éditeur de collections, cliquez sur le style de colonne.

5. Dans la zone **Propriétés** de l’éditeur de collections, sélectionnez la valeur <xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A> pour la colonne que vous souhaitez afficher.

## <a name="see-also"></a>Voir aussi

- [DataGrid, contrôle](datagrid-control-windows-forms.md)
- [Guide pratique pour supprimer ou masquer des colonnes dans le contrôle DataGrid Windows Forms](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
