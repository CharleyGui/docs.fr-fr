---
title: Types de colonnes dans le contrôle DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- columns [Windows Forms], types
- DataGridView control [Windows Forms], column types
- data grids [Windows Forms], columns
ms.assetid: f0a0a9f1-8757-4bfd-891f-d7d12870dbed
ms.openlocfilehash: e918394cca6350854074d4c1567890138b2a1462
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743856"
---
# <a name="column-types-in-the-windows-forms-datagridview-control"></a>Types de colonnes dans le contrôle DataGridView Windows Forms
Le contrôle <xref:System.Windows.Forms.DataGridView> utilise plusieurs types de colonne pour afficher ses informations et permettre aux utilisateurs de modifier ou d’ajouter des informations.  
  
 Lorsque vous liez un contrôle <xref:System.Windows.Forms.DataGridView> et affectez à la propriété <xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A> la valeur `true`, les colonnes sont générées automatiquement à l’aide des types de colonnes par défaut appropriés pour les types de données contenus dans la source de données liée.  
  
 Vous pouvez également créer vous-même des instances d’une des classes de colonne et les ajouter à la collection retournée par la propriété <xref:System.Windows.Forms.DataGridView.Columns%2A>. Vous pouvez créer ces instances pour une utilisation en tant que colonnes indépendantes, ou vous pouvez les lier manuellement. Les colonnes liées manuellement sont utiles, par exemple, lorsque vous souhaitez remplacer une colonne générée automatiquement d’un type par une colonne d’un autre type.  
  
 Le tableau suivant décrit les différentes classes de colonne disponibles pour une utilisation dans le contrôle <xref:System.Windows.Forms.DataGridView>.  
  
|Classe|Description|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewTextBoxColumn>|Utilisé avec les valeurs textuelles. Généré automatiquement lors de la liaison à des nombres et à des chaînes.|  
|<xref:System.Windows.Forms.DataGridViewCheckBoxColumn>|Utilisé avec les valeurs <xref:System.Boolean> et <xref:System.Windows.Forms.CheckState>. Généré automatiquement lors de la liaison à des valeurs de ces types.|  
|<xref:System.Windows.Forms.DataGridViewImageColumn>|Utilisé pour afficher des images. Généré automatiquement lors de la liaison à des tableaux d’octets, des objets <xref:System.Drawing.Image> ou des objets <xref:System.Drawing.Icon>.|  
|<xref:System.Windows.Forms.DataGridViewButtonColumn>|Utilisé pour afficher les boutons dans les cellules. Non généré automatiquement lors de la liaison. Généralement utilisé comme colonnes indépendantes.|  
|<xref:System.Windows.Forms.DataGridViewComboBoxColumn>|Permet d’afficher les listes déroulantes dans les cellules. Non généré automatiquement lors de la liaison. Généralement lié aux données manuellement.|  
|<xref:System.Windows.Forms.DataGridViewLinkColumn>|Utilisé pour afficher des liens dans les cellules. Non généré automatiquement lors de la liaison. Généralement lié aux données manuellement.|  
|Votre type de colonne personnalisé|Vous pouvez créer votre propre classe Column en héritant de la classe <xref:System.Windows.Forms.DataGridViewColumn> ou de l’une de ses classes dérivées pour fournir une apparence personnalisée, un comportement ou des contrôles hébergés. Pour plus d’informations, consultez [Comment : personnaliser des cellules et des colonnes dans le contrôle DataGridView Windows Forms en étendant leur comportement et leur apparence](customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md)|  
  
 Ces types de colonnes sont décrits plus en détail dans les sections suivantes.  
  
## <a name="datagridviewtextboxcolumn"></a>DataGridViewTextBoxColumn  
 Le <xref:System.Windows.Forms.DataGridViewTextBoxColumn> est un type de colonne à usage général pour une utilisation avec des valeurs textuelles telles que des nombres et des chaînes. En mode édition, un contrôle de <xref:System.Windows.Forms.TextBox> est affiché dans la cellule active, ce qui permet aux utilisateurs de modifier la valeur de la cellule.  
  
 Les valeurs des cellules sont automatiquement converties en chaînes pour l’affichage. Les valeurs entrées ou modifiées par l’utilisateur sont automatiquement analysées pour créer une valeur de cellule du type de données approprié. Vous pouvez personnaliser ces conversions en gérant les événements <xref:System.Windows.Forms.DataGridView.CellFormatting> et <xref:System.Windows.Forms.DataGridView.CellParsing> du contrôle <xref:System.Windows.Forms.DataGridView>.  
  
 Le type de données de la valeur de cellule d’une colonne est spécifié dans la propriété <xref:System.Windows.Forms.DataGridViewColumn.ValueType%2A> de la colonne.  
  
## <a name="datagridviewcheckboxcolumn"></a>DataGridViewCheckBoxColumn  
 Le <xref:System.Windows.Forms.DataGridViewCheckBoxColumn> est utilisé avec les valeurs de <xref:System.Boolean> et de <xref:System.Windows.Forms.CheckState>. <xref:System.Boolean> valeurs sont affichées sous forme de cases à cocher à deux ou trois États, en fonction de la valeur de la propriété <xref:System.Windows.Forms.DataGridViewCheckBoxColumn.ThreeState%2A>. Lorsque la colonne est liée à <xref:System.Windows.Forms.CheckState> valeurs, la valeur de la propriété <xref:System.Windows.Forms.DataGridViewCheckBoxColumn.ThreeState%2A> est `true` par défaut.  
  
 En règle générale, les valeurs des cellules de case à cocher sont destinées au stockage, comme toutes les autres données, ou à l’exécution d’opérations en bloc. Si vous souhaitez répondre immédiatement lorsque les utilisateurs cliquent sur une cellule de case à cocher, vous pouvez gérer l’événement <xref:System.Windows.Forms.DataGridView.CellClick>, mais cet événement se produit avant la mise à jour de la valeur de la cellule. Si vous avez besoin de la nouvelle valeur au moment du clic, une option consiste à calculer la valeur attendue en fonction de la valeur actuelle. Une autre approche consiste à valider immédiatement la modification et à gérer l’événement <xref:System.Windows.Forms.DataGridView.CellValueChanged> pour y répondre. Pour valider la modification en cas de clic sur la cellule, vous devez gérer l’événement <xref:System.Windows.Forms.DataGridView.CurrentCellDirtyStateChanged>. Dans le gestionnaire, si la cellule active est une cellule de case à cocher, appelez la méthode <xref:System.Windows.Forms.DataGridView.CommitEdit%2A> et transmettez la valeur <xref:System.Windows.Forms.DataGridViewDataErrorContexts.Commit>.  
  
## <a name="datagridviewimagecolumn"></a>DataGridViewImageColumn  
 Le <xref:System.Windows.Forms.DataGridViewImageColumn> est utilisé pour afficher des images. Les colonnes d’image peuvent être renseignées automatiquement à partir d’une source de données, remplies manuellement pour les colonnes indépendantes ou remplies dynamiquement dans un gestionnaire pour l’événement <xref:System.Windows.Forms.DataGridView.CellFormatting>.  
  
 Le remplissage automatique d’une colonne d’image d’une source de données fonctionne avec des tableaux d’octets dans divers formats d’image, y compris tous les formats pris en charge par la classe <xref:System.Drawing.Image> et le format d’image OLE utilisé par Microsoft® Access et l’exemple de base de données Northwind.  
  
 Le remplissage manuel d’une colonne d’image est utile lorsque vous souhaitez fournir les fonctionnalités d’un <xref:System.Windows.Forms.DataGridViewButtonColumn>, mais avec une apparence personnalisée. Vous pouvez gérer l’événement <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType> pour répondre aux clics dans une cellule d’image.  
  
 Le remplissage des cellules d’une colonne image dans un gestionnaire pour l’événement <xref:System.Windows.Forms.DataGridView.CellFormatting> est utile lorsque vous souhaitez fournir des images pour des valeurs calculées ou des valeurs dans des formats non-image. Par exemple, vous pouvez avoir une colonne « risque » avec des valeurs de chaîne telles que `"high"`, `"middle"`et `"low"` que vous souhaitez afficher sous forme d’icônes. Vous pouvez également avoir une colonne « image » qui contient les emplacements des images qui doivent être chargées plutôt que le contenu binaire des images.  
  
## <a name="datagridviewbuttoncolumn"></a>DataGridViewButtonColumn  
 Avec la <xref:System.Windows.Forms.DataGridViewButtonColumn>, vous pouvez afficher une colonne de cellules qui contiennent des boutons. Cela est utile lorsque vous souhaitez offrir à vos utilisateurs un moyen simple d’effectuer des actions sur des enregistrements particuliers, par exemple en plaçant une commande ou en affichant des enregistrements enfants dans une fenêtre distincte.  
  
 Les colonnes de bouton ne sont pas générées automatiquement lorsque vous liez des données à un contrôle de <xref:System.Windows.Forms.DataGridView>. Pour utiliser des colonnes de bouton, vous devez les créer manuellement et les ajouter à la collection retournée par la propriété <xref:System.Windows.Forms.DataGridView.Columns%2A?displayProperty=nameWithType>.  
  
 Vous pouvez répondre aux clics de l’utilisateur dans les cellules du bouton en gérant l’événement <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType>.  
  
## <a name="datagridviewcomboboxcolumn"></a>DataGridViewComboBoxColumn  
 Avec la <xref:System.Windows.Forms.DataGridViewComboBoxColumn>, vous pouvez afficher une colonne de cellules qui contiennent des zones de liste déroulante. Cela est utile pour l’entrée de données dans des champs qui ne peuvent contenir que des valeurs particulières, telles que la colonne Category de la table Products de l’exemple de base de données Northwind.  
  
 Vous pouvez remplir la liste déroulante utilisée pour toutes les cellules de la même façon que vous remplissez une liste déroulante <xref:System.Windows.Forms.ComboBox>, soit manuellement via la collection retournée par la propriété <xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A>, soit en le liant à une source de données par le biais des propriétés <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A>, <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A>et <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A>. Pour plus d’informations, consultez [contrôle ComboBox](combobox-control-windows-forms.md).  
  
 Vous pouvez lier les valeurs de cellule réelles à la source de données utilisée par le contrôle <xref:System.Windows.Forms.DataGridView> en définissant la propriété <xref:System.Windows.Forms.DataGridViewColumn.DataPropertyName%2A> de l' <xref:System.Windows.Forms.DataGridViewComboBoxColumn?displayProperty=nameWithType>.  
  
 Les colonnes de zone de liste déroulante ne sont pas générées automatiquement lorsque vous liez des données à un contrôle <xref:System.Windows.Forms.DataGridView>. Pour utiliser des colonnes de zone de liste déroulante, vous devez les créer manuellement et les ajouter à la collection retournée par la propriété <xref:System.Windows.Forms.DataGridView.Columns%2A>.  
  
## <a name="datagridviewlinkcolumn"></a>DataGridViewLinkColumn  
 Avec la <xref:System.Windows.Forms.DataGridViewLinkColumn>, vous pouvez afficher une colonne de cellules qui contiennent des liens hypertexte. Cela est utile pour les valeurs d’URL dans la source de données ou comme alternative à la colonne de bouton pour les comportements spéciaux, tels que l’ouverture d’une fenêtre avec des enregistrements enfants.  
  
 Les colonnes de lien ne sont pas générées automatiquement lors de la liaison de données d’un contrôle <xref:System.Windows.Forms.DataGridView>. Pour utiliser des colonnes de lien, vous devez les créer manuellement et les ajouter à la collection retournée par la propriété <xref:System.Windows.Forms.DataGridView.Columns%2A>.  
  
 Vous pouvez répondre aux clics de l’utilisateur sur les liens en gérant l’événement <xref:System.Windows.Forms.DataGridView.CellContentClick>. Cet événement est différent des événements <xref:System.Windows.Forms.DataGridView.CellClick> et <xref:System.Windows.Forms.DataGridView.CellMouseClick>, qui se produisent lorsqu’un utilisateur clique n’importe où dans une cellule.  
  
 La classe <xref:System.Windows.Forms.DataGridViewLinkColumn> fournit plusieurs propriétés permettant de modifier l’apparence des liens avant, pendant et après leur clic.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn>
- <xref:System.Windows.Forms.DataGridViewButtonColumn>
- <xref:System.Windows.Forms.DataGridViewCheckBoxColumn>
- <xref:System.Windows.Forms.DataGridViewComboBoxColumn>
- <xref:System.Windows.Forms.DataGridViewImageColumn>
- <xref:System.Windows.Forms.DataGridViewTextBoxColumn>
- <xref:System.Windows.Forms.DataGridViewLinkColumn>
- [DataGridView, contrôle](datagridview-control-windows-forms.md)
- [Comment : afficher des images dans les cellules du contrôle DataGridView Windows Forms](how-to-display-images-in-cells-of-the-windows-forms-datagridview-control.md)
- [Guide pratique pour utiliser des colonnes de type image dans le contrôle DataGridView Windows Forms](how-to-work-with-image-columns-in-the-windows-forms-datagridview-control.md)
- [Personnalisation du contrôle DataGridView Windows Forms](customizing-the-windows-forms-datagridview-control.md)
