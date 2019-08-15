---
title: 'Procédure : ajouter des tables et des colonnes au contrôle DataGrid Windows Forms à l’aide du concepteur'
ms.date: 03/30/2017
helpviewer_keywords:
- columns [Windows Forms], adding to DataGrid control
- tables [Windows Forms], adding to DataGrid control
- DataGrid control [Windows Forms], adding tables and columns
ms.assetid: 4a6d1b34-b696-476b-bf8a-57c6230aa9e1
ms.openlocfilehash: d11c4f7e4cdfb597477bb99f38612ed648849f20
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040050"
---
# <a name="how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control-using-the-designer"></a>Procédure : ajouter des tables et des colonnes au contrôle DataGrid Windows Forms à l’aide du concepteur

> [!NOTE]
> Le contrôle <xref:System.Windows.Forms.DataGridView> remplace le contrôle <xref:System.Windows.Forms.DataGrid> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.DataGrid> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix. Pour plus d’informations, consultez [Différences entre les contrôles DataGridView et DataGrid Windows Forms](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).

Vous pouvez afficher des données dans le <xref:System.Windows.Forms.DataGrid> contrôle Windows Forms dans les tables et les <xref:System.Windows.Forms.DataGridTableStyle> colonnes en créant des objets et <xref:System.Windows.Forms.GridTableStylesCollection> en les ajoutant à l’objet, <xref:System.Windows.Forms.DataGrid> accessible via <xref:System.Windows.Forms.DataGrid.TableStyles%2A> la propriété du contrôle. Chaque style de table affiche le contenu de la table de données spécifiée dans <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> la propriété <xref:System.Windows.Forms.DataGridTableStyle>de. Par défaut, un style de table sans les styles de colonne spécifiés affiche toutes les colonnes de cette table de données. Vous pouvez limiter les colonnes de la <xref:System.Windows.Forms.DataGridColumnStyle> table en ajoutant des objets <xref:System.Windows.Forms.GridColumnStylesCollection>au, qui est accessible par le biais <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> de la propriété <xref:System.Windows.Forms.DataGridTableStyle>de chacune d’elles.

Les procédures suivantes requièrent un projet d' **application Windows** avec un formulaire qui <xref:System.Windows.Forms.DataGrid> contient un contrôle. Pour plus d’informations sur la configuration d’un projet de ce [type, consultez Procédure: Créez un projet](/visualstudio/ide/step-1-create-a-windows-forms-application-project) d’application Windows Forms [et procédez comme suit: Ajoutez des contrôles à](how-to-add-controls-to-windows-forms.md)Windows Forms. Par défaut, dans Visual Studio 2005, <xref:System.Windows.Forms.DataGrid> le contrôle ne se trouve pas dans la **boîte à outils**. Pour plus d’informations sur l’ajout [de ce dernier, consultez Procédure: Ajoutez des éléments à la](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165355(v=vs.100))boîte à outils.

### <a name="to-add-a-table-to-the-datagrid-control-in-the-designer"></a>Pour ajouter une table au contrôle DataGrid dans le concepteur

1. Pour afficher des données dans la table, vous devez d’abord lier le <xref:System.Windows.Forms.DataGrid> contrôle à un DataSet. Pour plus d’informations, consultez [Guide pratique pour Liez le contrôle Windows Forms DataGrid à une source de données à l'](bind-wf-datagrid-control-to-a-data-source-using-the-designer.md)aide du concepteur.

2. Sélectionnez la <xref:System.Windows.Forms.DataGrid> propriété du <xref:System.Windows.Forms.DataGrid.TableStyles%2A> contrôle dans la fenêtre Propriétés, puis cliquez sur le bouton de sélection![(...) dans le fenêtre Propriétés de Visual Studio.](./media/visual-studio-ellipsis-button.png)) en regard de la propriété pour afficher le **Éditeur de collections DataGridTableStyle**.

3. Dans l’éditeur de collections, cliquez sur **Ajouter** pour insérer un style de tableau.

4. Cliquez sur **OK** pour fermer l’éditeur de collections, puis rouvrez-le en cliquant sur le bouton de sélection <xref:System.Windows.Forms.DataGrid.TableStyles%2A> en regard de la propriété.

     Lorsque vous rouvrez l’éditeur de collections, toutes les tables de données liées au contrôle s’affichent dans la liste déroulante <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> de la propriété du style de table.

5. Dans la zone **membres** de l’éditeur de collections, cliquez sur le style de table.

6. Dans la zone **Propriétés** de l’éditeur de collections, sélectionnez <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> la valeur de la table que vous souhaitez afficher.

### <a name="to-add-a-column-to-the-datagrid-control-in-the-designer"></a>Pour ajouter une colonne au contrôle DataGrid dans le concepteur

1. Dans la zone **membres** de l **'éditeur de collections DataGridTableStyle**, sélectionnez le style de table approprié. Dans la zone **Propriétés** de l’éditeur de collections, sélectionnez <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> le regroupement, puis cliquez sur le bouton de![sélection (le bouton de sélection (...) dans le fenêtre Propriétés de](./media/visual-studio-ellipsis-button.png)Visual Studio.) en regard de la propriété pour Affichez l **'éditeur de collections DataGridColumnStyle**.

2. Dans l’éditeur de collections, cliquez sur **Ajouter** pour insérer un style de colonne ou cliquez sur la flèche vers le bas en regard de **Ajouter** pour spécifier un type de colonne.

     Dans la zone de liste déroulante, vous pouvez sélectionner <xref:System.Windows.Forms.DataGridTextBoxColumn> le <xref:System.Windows.Forms.DataGridBoolColumn> type ou.

3. Cliquez sur OK pour fermer l **'éditeur de collections DataGridColumnStyle**, puis rouvrez-le en cliquant sur le bouton de <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> sélection en regard de la propriété.

     Lorsque vous rouvrez l’éditeur de collections, toutes les colonnes de données de la table de données liée s’affichent dans la liste déroulante de la <xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A> propriété du style de colonne.

4. Dans la zone **membres** de l’éditeur de collections, cliquez sur le style de colonne.

5. Dans la zone **Propriétés** de l’éditeur de collections, sélectionnez <xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A> la valeur de la colonne que vous souhaitez afficher.

## <a name="see-also"></a>Voir aussi

- [DataGrid, contrôle](datagrid-control-windows-forms.md)
- [Guide pratique pour Supprimer ou masquer des colonnes dans le contrôle DataGrid Windows Forms](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
