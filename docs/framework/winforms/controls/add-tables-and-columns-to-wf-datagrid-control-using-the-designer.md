---
title: 'Procédure : ajouter des tables et des colonnes au contrôle DataGrid Windows Forms à l’aide du concepteur'
ms.date: 03/30/2017
helpviewer_keywords:
- columns [Windows Forms], adding to DataGrid control
- tables [Windows Forms], adding to DataGrid control
- DataGrid control [Windows Forms], adding tables and columns
ms.assetid: 4a6d1b34-b696-476b-bf8a-57c6230aa9e1
ms.openlocfilehash: a5955840988cb747b21f32efbd5c6091a86f483a
ms.sourcegitcommit: ffd7dd79468a81bbb0d6449f6d65513e050c04c4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2019
ms.locfileid: "65959518"
---
# <a name="how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control-using-the-designer"></a>Procédure : ajouter des tables et des colonnes au contrôle DataGrid Windows Forms à l’aide du concepteur

> [!NOTE]
> Le contrôle <xref:System.Windows.Forms.DataGridView> remplace le contrôle <xref:System.Windows.Forms.DataGrid> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.DataGrid> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix. Pour plus d’informations, consultez [Différences entre les contrôles DataGridView et DataGrid Windows Forms](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).

Vous pouvez afficher des données dans les formulaires Windows <xref:System.Windows.Forms.DataGrid> contrôle dans les tables et colonnes en créant <xref:System.Windows.Forms.DataGridTableStyle> objets et en les ajoutant à la <xref:System.Windows.Forms.GridTableStylesCollection> objet, qui est accessible via la <xref:System.Windows.Forms.DataGrid> du contrôle <xref:System.Windows.Forms.DataGrid.TableStyles%2A> propriété. Chaque style de table affiche le contenu de toute table de données spécifiée dans le <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> propriété de la <xref:System.Windows.Forms.DataGridTableStyle>. Par défaut, un style de table sans style de colonne spécifié affiche toutes les colonnes des table de données. Vous pouvez limiter les colonnes de la table s’affichent en ajoutant <xref:System.Windows.Forms.DataGridColumnStyle> des objets sur le <xref:System.Windows.Forms.GridColumnStylesCollection>, qui est accessible via la <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> propriété de chaque <xref:System.Windows.Forms.DataGridTableStyle>.

Les procédures suivantes nécessitent un **Windows Application** projet avec un formulaire qui contient un <xref:System.Windows.Forms.DataGrid> contrôle. Pour plus d’informations sur la façon de configurer un tel projet, consultez [Comment : Créer un projet d’application Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) et [Comment : Ajouter des contrôles aux Windows Forms](how-to-add-controls-to-windows-forms.md). Par défaut dans Visual Studio 2005, le <xref:System.Windows.Forms.DataGrid> contrôle n’est pas dans le **boîte à outils**. Pour plus d’informations sur son ajout, consultez [Comment : Ajouter des éléments à la boîte à outils](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165355(v=vs.100)).

> [!NOTE]
> Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).

### <a name="to-add-a-table-to-the-datagrid-control-in-the-designer"></a>Pour ajouter une table au contrôle DataGrid dans le Concepteur

1. Pour afficher des données dans la table, vous devez d’abord lier le <xref:System.Windows.Forms.DataGrid> contrôle à un jeu de données. Pour plus d'informations, voir [Procédure : Lier le contrôle DataGrid Windows Forms à une Source de données à l’aide du concepteur](bind-wf-datagrid-control-to-a-data-source-using-the-designer.md).

2. Sélectionnez le <xref:System.Windows.Forms.DataGrid> du contrôle <xref:System.Windows.Forms.DataGrid.TableStyles%2A> propriété dans la fenêtre Propriétés, puis cliquez sur le bouton de sélection (![bouton les points de suspension (...) dans la fenêtre Propriétés de Visual Studio.](./media/visual-studio-ellipsis-button.png)) en regard de la propriété pour afficher le **Éditeur de collections DataGridTableStyle**.

3. Dans l’éditeur de collections, cliquez sur **ajouter** pour insérer un style de table.

4. Cliquez sur **OK** pour fermer l’éditeur de collections, puis rouvrez-le en cliquant sur le bouton de sélection en regard du <xref:System.Windows.Forms.DataGrid.TableStyles%2A> propriété.

     Lorsque vous rouvrez l’éditeur de collections, des tables de données liées au contrôle seront affiche dans la liste déroulante pour le <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> propriété du style du tableau.

5. Dans le **membres** zone de l’éditeur de collection, cliquez sur le style de table.

6. Dans le **propriétés** zone de l’éditeur de collection, sélectionnez le <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> valeur pour la table que vous souhaitez afficher.

### <a name="to-add-a-column-to-the-datagrid-control-in-the-designer"></a>Pour ajouter une colonne au contrôle DataGrid dans le Concepteur

1. Dans le **membres** zone de la **éditeur de collections DataGridTableStyle**, sélectionnez le style de table approprié. Dans le **propriétés** zone de l’éditeur de collection, sélectionnez le <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> collection, puis cliquez sur le bouton de sélection (![bouton les points de suspension (...) dans la fenêtre Propriétés de Visual Studio.](./media/visual-studio-ellipsis-button.png)) à côté la propriété à afficher le **éditeur de collections DataGridColumnStyle**.

2. Dans l’éditeur de collections, cliquez sur **ajouter** pour insérer un style de colonne ou cliquez sur la flèche vers le bas en regard **ajouter** pour spécifier un type de colonne.

     Dans la zone de liste déroulante, vous pouvez sélectionner le <xref:System.Windows.Forms.DataGridTextBoxColumn> ou <xref:System.Windows.Forms.DataGridBoolColumn> type.

3. Cliquez sur OK pour fermer la **éditeur de collections DataGridColumnStyle**, puis rouvrez-le en cliquant sur le bouton de sélection en regard du <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> propriété.

     Lorsque vous rouvrez l’éditeur de collections, les colonnes de données dans la table de données liées s’affichent dans la liste déroulante pour le <xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A> propriété du style de colonne.

4. Dans le **membres** zone de l’éditeur de collection, cliquez sur le style de colonne.

5. Dans le **propriétés** zone de l’éditeur de collection, sélectionnez le <xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A> valeur pour la colonne que vous souhaitez afficher.

## <a name="see-also"></a>Voir aussi

- [DataGrid, contrôle](datagrid-control-windows-forms.md)
- [Guide pratique pour Supprimer ou masquer des colonnes dans le contrôle DataGrid Windows Forms](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
