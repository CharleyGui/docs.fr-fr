---
title: 'Procédure : mettre en forme le contrôle DataGrid Windows Forms à l’aide du concepteur'
ms.date: 03/30/2017
helpviewer_keywords:
- columns [Windows Forms], DataGrid controls
- colors [Windows Forms], applying to DataGrid controls
- DataGrid control [Windows Forms], formatting
- DataGrid control [Windows Forms], default styles
- tables [Windows Forms], formatting in DataGrid control
- formatting [Windows Forms]
ms.assetid: 533b9814-6124-49dc-9fda-085f1502609f
ms.openlocfilehash: b3a85f5f9e51dae50a40058b8f07f92976da66f2
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2019
ms.locfileid: "69666160"
---
# <a name="how-to-format-the-windows-forms-datagrid-control-using-the-designer"></a>Procédure : mettre en forme le contrôle DataGrid Windows Forms à l’aide du concepteur

> [!NOTE]
> Le contrôle <xref:System.Windows.Forms.DataGridView> remplace le contrôle <xref:System.Windows.Forms.DataGrid> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.DataGrid> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix. Pour plus d’informations, consultez [Différences entre les contrôles DataGridView et DataGrid Windows Forms](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).

L’application de différentes couleurs à différentes parties <xref:System.Windows.Forms.DataGrid> d’un contrôle peut aider à rendre les informations plus faciles à lire et à interpréter. La couleur peut être appliquée aux lignes et aux colonnes. Les lignes et les colonnes peuvent également être masquées ou affichées à votre convenance.

Il existe trois aspects de base de la mise <xref:System.Windows.Forms.DataGrid> en forme du contrôle :

- Vous pouvez définir des propriétés pour établir un style par défaut dans lequel les données sont affichées.

- À partir de cette base, vous pouvez personnaliser la façon dont certaines tables s’affichent au moment de l’exécution.

- Enfin, vous pouvez modifier les colonnes qui sont affichées dans la grille de données ainsi que les couleurs et autres mises en forme affichées.

En guise d’étape initiale dans la mise en forme d’une grille de données, vous <xref:System.Windows.Forms.DataGrid> pouvez définir les propriétés du lui-même. Ces options de couleur et de format forment une base à partir de laquelle vous pouvez apporter des modifications en fonction des tables de données et des colonnes affichées.

La procédure suivante requiert un projet d' **application Windows** avec un formulaire contenant <xref:System.Windows.Forms.DataGrid> un contrôle. Pour plus d’informations sur la configuration d’un tel [projet, consultez Procédure : Créez un projet](/visualstudio/ide/step-1-create-a-windows-forms-application-project) d’application Windows Forms [et procédez comme suit : Ajoutez des contrôles à](how-to-add-controls-to-windows-forms.md)Windows Forms. Dans Visual Studio 2005, le <xref:System.Windows.Forms.DataGrid> contrôle ne se trouve pas dans la **boîte à outils** par défaut. Pour plus d'informations, voir [Procédure : Ajoutez des éléments à la](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165355(v=vs.100))boîte à outils.

### <a name="to-establish-a-default-style-for-the-datagrid-control"></a>Pour établir un style par défaut pour le contrôle DataGrid

1. Sélectionnez le contrôle <xref:System.Windows.Forms.DataGrid>.

2. Dans la fenêtre **Propriétés** , définissez les propriétés suivantes, selon le cas.

    |Property|Description|
    |--------------|-----------------|
    |<xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A>|La `BackColor` propriété définit la couleur des lignes paires de la grille. Lorsque vous définissez la <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> propriété sur une couleur différente, chaque autre ligne est définie sur cette nouvelle couleur (lignes 1, 3, 5, etc.).|
    |<xref:System.Windows.Forms.DataGrid.BackColor%2A>|Couleur d’arrière-plan des lignes numérotées de la grille (lignes 0, 2, 4, 6, etc.).|
    |<xref:System.Windows.Forms.DataGrid.BackgroundColor%2A>|Tandis <xref:System.Windows.Forms.DataGrid.BackColor%2A> que <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> les propriétés et déterminent la couleur des lignes dans la <xref:System.Windows.Forms.DataGrid.BackgroundColor%2A> grille, la propriété détermine la couleur de la zone en dehors de la zone de ligne, qui est visible uniquement lorsque la grille défile vers le bas, ou si seules quelques lignes sont contenu dans la grille.|
    |<xref:System.Windows.Forms.DataGrid.BorderStyle%2A>|Style de bordure de la grille, l’une <xref:System.Windows.Forms.BorderStyle> des valeurs d’énumération.|
    |<xref:System.Windows.Forms.DataGrid.CaptionBackColor%2A>|Couleur d’arrière-plan du titre de fenêtre de la grille qui s’affiche immédiatement au-dessus de la grille.|
    |<xref:System.Windows.Forms.DataGrid.CaptionFont%2A>|Police de la légende en haut de la grille.|
    |<xref:System.Windows.Forms.DataGrid.CaptionForeColor%2A>|Couleur d’arrière-plan du titre de fenêtre de la grille.|
    |<xref:System.Windows.Forms.Control.Font%2A>|Police utilisée pour afficher le texte dans la grille.|
    |<xref:System.Windows.Forms.DataGrid.ForeColor%2A>|Couleur de la police affichée par les données dans les lignes de la grille de données.|
    |<xref:System.Windows.Forms.DataGrid.GridLineColor%2A>|Couleur des lignes de la grille de données.|
    |<xref:System.Windows.Forms.DataGrid.GridLineStyle%2A>|Style des lignes qui séparent les cellules de la grille, l’une des valeurs <xref:System.Windows.Forms.DataGridLineStyle> d’énumération.|
    |<xref:System.Windows.Forms.DataGrid.HeaderBackColor%2A>|Couleur d’arrière-plan des en-têtes de ligne et de colonne.|
    |<xref:System.Windows.Forms.DataGrid.HeaderFont%2A>|Police utilisée pour les en-têtes de colonnes.|
    |<xref:System.Windows.Forms.DataGrid.HeaderForeColor%2A>|Couleur de premier plan des en-têtes de colonnes de la grille, y compris le texte d’en-tête de colonne et le signe plus (+) et les glyphes de signe moins (-) qui développent et réduisent les lignes quand plusieurs tables associées sont affichées.|
    |<xref:System.Windows.Forms.DataGrid.LinkColor%2A>|Couleur du texte de tous les liens de la grille de données, y compris les liens vers les tables enfants, le nom de la relation, etc.|
    |<xref:System.Windows.Forms.DataGrid.ParentRowsBackColor%2A>|Dans une table enfant, il s’agit de la couleur d’arrière-plan des lignes parentes.|
    |<xref:System.Windows.Forms.DataGrid.ParentRowsForeColor%2A>|Dans une table enfant, il s’agit de la couleur de premier plan des lignes parentes.|
    |<xref:System.Windows.Forms.DataGrid.ParentRowsLabelStyle%2A>|Détermine si les noms de table et de colonne sont affichés dans la ligne parente, au <xref:System.Windows.Forms.DataGridParentRowsLabelStyle> moyen de l’énumération.|
    |<xref:System.Windows.Forms.DataGrid.PreferredColumnWidth%2A>|Largeur par défaut (en pixels) des colonnes de la grille. Définissez cette propriété avant de réinitialiser les <xref:System.Windows.Forms.DataGrid.DataSource%2A> propriétés <xref:System.Windows.Forms.DataGrid.DataMember%2A> et (séparément ou à l’aide de <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> la méthode), sinon la propriété n’aura aucun effet.<br /><br /> La propriété ne peut pas être définie sur une valeur inférieure à 0.|
    |<xref:System.Windows.Forms.DataGrid.PreferredRowHeight%2A>|Hauteur de ligne (en pixels) des lignes de la grille. Définissez cette propriété avant de réinitialiser les <xref:System.Windows.Forms.DataGrid.DataSource%2A> propriétés <xref:System.Windows.Forms.DataGrid.DataMember%2A> et (séparément ou à l’aide de <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> la méthode), sinon la propriété n’aura aucun effet.<br /><br /> La propriété ne peut pas être définie sur une valeur inférieure à 0.|
    |<xref:System.Windows.Forms.DataGrid.RowHeaderWidth%2A>|Largeur des en-têtes de lignes de la grille.|
    |<xref:System.Windows.Forms.DataGrid.SelectionBackColor%2A>|Quand une ligne ou une cellule est sélectionnée, il s’agit de la couleur d’arrière-plan.|
    |<xref:System.Windows.Forms.DataGrid.SelectionForeColor%2A>|Quand une ligne ou une cellule est sélectionnée, il s’agit de la couleur de premier plan.|

    > [!NOTE]
    > Lorsque vous personnalisez les couleurs des contrôles, il est possible de rendre le contrôle inaccessible en raison d’un choix de couleurs médiocres (par exemple, rouge et vert). Utilisez les couleurs disponibles dans la palette **couleurs système** pour éviter ce problème.

    La procédure suivante requiert un <xref:System.Windows.Forms.DataGrid> contrôle lié à une table de données. Pour plus d'informations, voir [Procédure : Liez le contrôle Windows Forms DataGrid à une source](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)de données.

### <a name="to-set-the-table-and-column-style-of-a-data-table-at-design-time"></a>Pour définir le style de table et de colonne d’une table de données au moment de la conception

1. Sélectionnez le <xref:System.Windows.Forms.DataGrid> contrôle sur votre formulaire.

2. Dans la fenêtre **Propriétés** , sélectionnez la <xref:System.Windows.Forms.DataGrid.TableStyles%2A> propriété et![cliquez sur **le bouton de sélection (.** ..) dans le bouton fenêtre Propriétés de Visual Studio.](./media/visual-studio-ellipsis-button.png)).

3. Dans la boîte de dialogue **éditeur de collections DataGridTableStyle** , cliquez sur **Ajouter** pour ajouter un style de table à la collection.

     Avec l' **éditeur de collections DataGridTableStyle**, vous pouvez ajouter et supprimer des styles de table, définir des propriétés d’affichage et de mise en page, et définir le nom de mappage pour les styles de table.

4. Affectez <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> à la propriété le nom de mappage pour chaque style de table.

     Le nom de mappage est utilisé pour spécifier le style de table à utiliser avec la table.

5. Dans l **'éditeur de collections DataGridTableStyle**, <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> sélectionnez la propriété et cliquez sur le![bouton de sélection (...) dans le fenêtre Propriétés de Visual Studio.](./media/visual-studio-ellipsis-button.png)).

6. Dans la boîte de dialogue **éditeur de collections DataGridColumnStyle** , ajoutez des styles de colonne au style de table que vous avez créé.

     Avec l' **éditeur de collections DataGridColumnStyle**, vous pouvez ajouter et supprimer des styles de colonne, définir des propriétés d’affichage et de mise en page, et définir le nom de mappage et les chaînes de mise en forme pour les colonnes de données.

    > [!NOTE]
    > Pour plus d’informations sur la mise en forme des chaînes, consultez [mise en forme des types](../../../standard/base-types/formatting-types.md).

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.GridTableStylesCollection>
- <xref:System.Windows.Forms.GridColumnStylesCollection>
- <xref:System.Windows.Forms.DataGrid>
- [Guide pratique pour Supprimer ou masquer des colonnes dans le contrôle DataGrid Windows Forms](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
- [DataGrid, contrôle](datagrid-control-windows-forms.md)
