---
title: Architecture du contrôle DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], architecture
ms.assetid: 1c6cabf0-02ee-4bbc-9574-b54bb7f5b19e
ms.openlocfilehash: 2e1884383cca87f8d4ff84f486e2b29761a0c55d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742528"
---
# <a name="datagridview-control-architecture-windows-forms"></a>Architecture du contrôle DataGridView (Windows Forms)
Le contrôle <xref:System.Windows.Forms.DataGridView> et ses classes associées sont conçus pour être un système flexible et extensible permettant d’afficher et de modifier des données tabulaires. Ces classes sont toutes contenues dans l’espace de noms <xref:System.Windows.Forms?displayProperty=nameWithType>, et elles sont toutes nommées avec le préfixe « DataGridView ».  
  
## <a name="architecture-elements"></a>Éléments d'architecture  
 Les principales classes auxiliaires <xref:System.Windows.Forms.DataGridView> dérivent de <xref:System.Windows.Forms.DataGridViewElement>. Le modèle objet suivant illustre la hiérarchie d’héritage <xref:System.Windows.Forms.DataGridViewElement>.  
  
 ![Diagramme qui affiche la hiérarchie du modèle objet DataGridViewElement.](./media/datagridview-control-architecture-windows-forms/datagridviewelement-object-model.gif)  
  
 La classe <xref:System.Windows.Forms.DataGridViewElement> fournit une référence au contrôle parent <xref:System.Windows.Forms.DataGridView> et a une propriété <xref:System.Windows.Forms.DataGridViewElement.State%2A>, qui contient une valeur qui représente une combinaison de valeurs de l’énumération <xref:System.Windows.Forms.DataGridViewElementStates>.  
  
 Les sections suivantes décrivent plus en détail les classes <xref:System.Windows.Forms.DataGridView> Companion.  
  
### <a name="datagridviewelementstates"></a>DataGridViewElementStates  
 L’énumération <xref:System.Windows.Forms.DataGridViewElementStates> contient les valeurs suivantes :  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.None>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.Frozen>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.ReadOnly>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.Resizable>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.ResizableSet>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.Selected>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.Visible>  
  
 Les valeurs de cette énumération peuvent être combinées avec les opérateurs logiques au niveau du bit, de sorte que la propriété <xref:System.Windows.Forms.DataGridViewElement.State%2A> peut exprimer plusieurs États à la fois. Par exemple, un <xref:System.Windows.Forms.DataGridViewElement> peut être <xref:System.Windows.Forms.DataGridViewElementStates.Frozen>simultanément, <xref:System.Windows.Forms.DataGridViewElementStates.Selected>et <xref:System.Windows.Forms.DataGridViewElementStates.Visible>.  
  
### <a name="cells-and-bands"></a>Cellules et bandes  
 Le contrôle <xref:System.Windows.Forms.DataGridView> comprend deux types d’objets fondamentaux : les cellules et les bandes. Toutes les cellules dérivent de la classe de base <xref:System.Windows.Forms.DataGridViewCell>. Les deux types de bandes, <xref:System.Windows.Forms.DataGridViewColumn> et <xref:System.Windows.Forms.DataGridViewRow>, dérivent les deux de la classe de base <xref:System.Windows.Forms.DataGridViewBand>.  
  
 Le contrôle <xref:System.Windows.Forms.DataGridView> interagit avec plusieurs classes, mais les plus fréquemment rencontrées sont <xref:System.Windows.Forms.DataGridViewCell>, <xref:System.Windows.Forms.DataGridViewColumn>et <xref:System.Windows.Forms.DataGridViewRow>.  
  
### <a name="datagridviewcell"></a>DataGridViewCell  
 La cellule est l’unité fondamentale de l’interaction pour le <xref:System.Windows.Forms.DataGridView>. L’affichage est centré sur les cellules et l’entrée de données est souvent effectuée par le biais de cellules. Vous pouvez accéder aux cellules à l’aide de la collection <xref:System.Windows.Forms.DataGridViewRow.Cells%2A> de la classe <xref:System.Windows.Forms.DataGridViewRow>, et vous pouvez accéder aux cellules sélectionnées à l’aide de la collection <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> du contrôle <xref:System.Windows.Forms.DataGridView>. Le modèle objet suivant illustre cette utilisation et affiche la hiérarchie d’héritage <xref:System.Windows.Forms.DataGridViewCell>.  
  
 ![Diagramme qui affiche la hiérarchie du modèle objet DataGridViewCell.](./media/datagridview-control-architecture-windows-forms/datagridviewcell-object-model.gif)  
  
 Le type de <xref:System.Windows.Forms.DataGridViewCell> est une classe de base abstraite, dont tous les types de cellule dérivent. <xref:System.Windows.Forms.DataGridViewCell> et ses types dérivés ne sont pas des contrôles Windows Forms, mais certains contrôleurs de Windows Forms hôtes. Toute fonctionnalité d’édition prise en charge par une cellule est généralement gérée par un contrôle hébergé.  
  
 les objets <xref:System.Windows.Forms.DataGridViewCell> ne contrôlent pas leurs propres fonctionnalités d’apparence et de peinture de la même façon que les contrôles Windows Forms. Au lieu de cela, le <xref:System.Windows.Forms.DataGridView> est responsable de l’apparence de ses objets <xref:System.Windows.Forms.DataGridViewCell>. Vous pouvez affecter de manière significative l’apparence et le comportement des cellules en interagissant avec les propriétés et événements du contrôle <xref:System.Windows.Forms.DataGridView>. Quand vous avez des exigences spéciales pour les personnalisations qui dépassent les capacités du contrôle <xref:System.Windows.Forms.DataGridView>, vous pouvez implémenter votre propre classe qui dérive de <xref:System.Windows.Forms.DataGridViewCell> ou de l’une de ses classes enfants.  
  
 La liste suivante répertorie les classes dérivées de <xref:System.Windows.Forms.DataGridViewCell>:  
  
- <xref:System.Windows.Forms.DataGridViewTextBoxCell>  
  
- <xref:System.Windows.Forms.DataGridViewButtonCell>  
  
- <xref:System.Windows.Forms.DataGridViewLinkCell>  
  
- <xref:System.Windows.Forms.DataGridViewCheckBoxCell>  
  
- <xref:System.Windows.Forms.DataGridViewComboBoxCell>  
  
- <xref:System.Windows.Forms.DataGridViewImageCell>  
  
- <xref:System.Windows.Forms.DataGridViewHeaderCell>  
  
- <xref:System.Windows.Forms.DataGridViewRowHeaderCell>  
  
- <xref:System.Windows.Forms.DataGridViewColumnHeaderCell>  
  
- <xref:System.Windows.Forms.DataGridViewTopLeftHeaderCell>  
  
- Vos types de cellules personnalisés  
  
### <a name="datagridviewcolumn"></a>DataGridViewColumn  
 Le schéma du magasin de données attaché du contrôle <xref:System.Windows.Forms.DataGridView> est exprimé dans les colonnes du contrôle <xref:System.Windows.Forms.DataGridView>. Vous pouvez accéder aux colonnes du contrôle <xref:System.Windows.Forms.DataGridView> à l’aide de la collection <xref:System.Windows.Forms.DataGridView.Columns%2A>. Vous pouvez accéder aux colonnes sélectionnées à l’aide de la collection <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>. Le modèle objet suivant illustre cette utilisation et affiche la hiérarchie d’héritage <xref:System.Windows.Forms.DataGridViewColumn>.  
  
 ![Diagramme qui affiche la hiérarchie du modèle objet DataGridViewColumn.](./media/datagridview-control-architecture-windows-forms/datagridviewcolumn-object-model.gif)  
  
 Certains des types de cellule clés ont des types de colonnes correspondants. Celles-ci sont dérivées de la classe de base <xref:System.Windows.Forms.DataGridViewColumn>.  
  
 La liste suivante répertorie les classes dérivées de <xref:System.Windows.Forms.DataGridViewColumn>:  
  
- <xref:System.Windows.Forms.DataGridViewButtonColumn>  
  
- <xref:System.Windows.Forms.DataGridViewCheckBoxColumn>  
  
- <xref:System.Windows.Forms.DataGridViewComboBoxColumn>  
  
- <xref:System.Windows.Forms.DataGridViewImageColumn>  
  
- <xref:System.Windows.Forms.DataGridViewTextBoxColumn>  
  
- <xref:System.Windows.Forms.DataGridViewLinkColumn>  
  
- Vos types de colonnes personnalisés  
  
### <a name="datagridview-editing-controls"></a>Contrôles d’édition DataGridView  
 Les cellules qui prennent en charge la fonctionnalité d’édition avancée utilisent généralement un contrôle hébergé qui est dérivé d’un contrôle de Windows Forms. Ces contrôles implémentent également l’interface <xref:System.Windows.Forms.IDataGridViewEditingControl>. Le modèle objet suivant illustre l’utilisation de ces contrôles.  
  
 ![Diagramme montrant la hiérarchie du modèle objet du contrôle d’édition DataGridView.](./media/datagridview-control-architecture-windows-forms/datagridviewediting-object-model.gif)  
  
 Les contrôles d’édition suivants sont fournis avec le contrôle <xref:System.Windows.Forms.DataGridView> :  
  
- <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl>  
  
- <xref:System.Windows.Forms.DataGridViewTextBoxEditingControl>  
  
 Pour plus d’informations sur la création de vos propres contrôles d’édition, consultez [Comment : héberger des contrôles dans Windows Forms des cellules DataGridView](how-to-host-controls-in-windows-forms-datagridview-cells.md).  
  
 Le tableau suivant illustre la relation entre les types de cellules, les types de colonnes et les contrôles d’édition.  
  
|Type de cellule|Contrôle hébergé|Type de colonne|  
|---------------|--------------------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewButtonCell>|N/A|<xref:System.Windows.Forms.DataGridViewButtonColumn>|  
|<xref:System.Windows.Forms.DataGridViewCheckBoxCell>|N/A|<xref:System.Windows.Forms.DataGridViewCheckBoxColumn>|  
|<xref:System.Windows.Forms.DataGridViewComboBoxCell>|<xref:System.Windows.Forms.DataGridViewComboBoxEditingControl>|<xref:System.Windows.Forms.DataGridViewComboBoxColumn>|  
|<xref:System.Windows.Forms.DataGridViewImageCell>|N/A|<xref:System.Windows.Forms.DataGridViewImageColumn>|  
|<xref:System.Windows.Forms.DataGridViewLinkCell>|N/A|<xref:System.Windows.Forms.DataGridViewLinkColumn>|  
|<xref:System.Windows.Forms.DataGridViewTextBoxCell>|<xref:System.Windows.Forms.DataGridViewTextBoxEditingControl>|<xref:System.Windows.Forms.DataGridViewTextBoxColumn>|  
  
### <a name="datagridviewrow"></a>DataGridViewRow  
 La classe <xref:System.Windows.Forms.DataGridViewRow> affiche les champs de données d’un enregistrement à partir du magasin de données auquel le contrôle <xref:System.Windows.Forms.DataGridView> est attaché. Vous pouvez accéder aux lignes du contrôle <xref:System.Windows.Forms.DataGridView> à l’aide de la collection <xref:System.Windows.Forms.DataGridView.Rows%2A>. Vous pouvez accéder aux lignes sélectionnées à l’aide de la collection <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>. Le modèle objet suivant illustre cette utilisation et affiche la hiérarchie d’héritage <xref:System.Windows.Forms.DataGridViewRow>.  
  
 ![Diagramme qui affiche la hiérarchie du modèle objet DataGridViewRow.](./media/datagridview-control-architecture-windows-forms/datagridviewrow-object-model.gif)
  
 Vous pouvez dériver vos propres types à partir de la classe <xref:System.Windows.Forms.DataGridViewRow>, bien que cela ne soit généralement pas nécessaire. Le contrôle <xref:System.Windows.Forms.DataGridView> possède plusieurs événements et propriétés liés aux lignes pour personnaliser le comportement de ses objets <xref:System.Windows.Forms.DataGridViewRow>.  
  
 Si vous activez la propriété <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> du contrôle <xref:System.Windows.Forms.DataGridView>, une ligne spéciale pour l’ajout de nouvelles lignes apparaît comme dernière ligne. Cette ligne fait partie de la collection <xref:System.Windows.Forms.DataGridView.Rows%2A>, mais elle possède des fonctionnalités spéciales qui peuvent nécessiter votre attention. Pour plus d’informations, consultez [utilisation de la ligne pour les nouveaux enregistrements dans le contrôle DataGridView Windows Forms](using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble du contrôle DataGridView](datagridview-control-overview-windows-forms.md)
- [Personnalisation du contrôle DataGridView Windows Forms](customizing-the-windows-forms-datagridview-control.md)
- [Utilisation de la ligne pour les nouveaux enregistrements dans le contrôle DataGridView Windows Forms](using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)
