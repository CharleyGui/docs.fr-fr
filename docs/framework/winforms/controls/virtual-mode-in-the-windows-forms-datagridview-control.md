---
title: Mode virtuel dans le contrôle DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], virtual mode
ms.assetid: feae5d43-2848-4b1a-8ea7-77085dc415b5
ms.openlocfilehash: 0d82f0fc9946e5b61ea171f2f5d2ab5690db0c71
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745444"
---
# <a name="virtual-mode-in-the-windows-forms-datagridview-control"></a>Mode virtuel dans le contrôle DataGridView Windows Forms
Avec le mode virtuel, vous pouvez gérer l’interaction entre le contrôle <xref:System.Windows.Forms.DataGridView> et un cache de données personnalisé. Pour implémenter le mode virtuel, affectez à la propriété <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> la valeur `true` et gérez un ou plusieurs des événements décrits dans cette rubrique. En général, vous gérez au moins l’événement `CellValueNeeded`, ce qui permet au contrôle de rechercher des valeurs dans le cache de données.  
  
## <a name="bound-mode-and-virtual-mode"></a>Mode lié et mode virtuel  
 Le mode virtuel est nécessaire uniquement lorsque vous devez compléter ou remplacer le mode dépendant. En mode dépendant, vous définissez la propriété <xref:System.Windows.Forms.DataGridView.DataSource%2A> et le contrôle charge automatiquement les données à partir de la source spécifiée et lui soumet les modifications apportées par l’utilisateur. Vous pouvez contrôler quelles colonnes liées sont affichées, et la source de données elle-même gère généralement des opérations telles que le tri.  
  
## <a name="supplementing-bound-mode"></a>Mode lié complémentaire  
 Vous pouvez compléter le mode dépendant en affichant des colonnes indépendantes avec les colonnes dépendantes. Cela est parfois appelé « mode mixte » et est utile pour afficher des éléments tels que des valeurs calculées ou des contrôles d’interface utilisateur (IU).  
  
 Étant donné que les colonnes indépendantes sont en dehors de la source de données, elles sont ignorées par les opérations de tri de la source de données. Par conséquent, lorsque vous activez le tri en mode mixte, vous devez gérer les données indépendantes dans un cache local et implémenter le mode virtuel pour permettre au contrôle de <xref:System.Windows.Forms.DataGridView> d’interagir avec lui.  
  
 Pour plus d’informations sur l’utilisation du mode virtuel pour conserver les valeurs dans les colonnes indépendantes, consultez les exemples dans les rubriques de référence sur la propriété <xref:System.Windows.Forms.DataGridViewCheckBoxColumn.ThreeState%2A?displayProperty=nameWithType> et la classe <xref:System.Windows.Forms.DataGridViewComboBoxColumn?displayProperty=nameWithType>.  
  
## <a name="replacing-bound-mode"></a>Remplacement du mode Bound  
 Si le mode dépendant ne répond pas à vos besoins en matière de performances, vous pouvez gérer toutes vos données dans un cache personnalisé par le biais de gestionnaires d’événements en mode virtuel. Par exemple, vous pouvez utiliser le mode virtuel pour implémenter un mécanisme de chargement de données juste-à-temps, qui récupère uniquement le nombre de données d’une base de données en réseau nécessaire pour des performances optimales. Ce scénario est particulièrement utile lorsque vous travaillez avec de grandes quantités de données sur une connexion réseau lente ou avec des ordinateurs clients disposant d’une quantité limitée de mémoire RAM ou d’espace de stockage.  
  
 Pour plus d’informations sur l’utilisation du mode virtuel dans un scénario juste-à-temps, consultez [implémentation du mode virtuel avec le chargement de données juste-à-temps dans le contrôle DataGridView Windows Forms](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md).  
  
## <a name="virtual-mode-events"></a>Événements en mode virtuel  
 Si vos données sont en lecture seule, l’événement `CellValueNeeded` peut être le seul événement que vous devrez gérer. Des événements en mode virtuel supplémentaires vous permettent d’activer des fonctionnalités spécifiques telles que les modifications des utilisateurs, l’ajout et la suppression de lignes et les transactions au niveau des lignes.  
  
 Certains événements de <xref:System.Windows.Forms.DataGridView> standard (tels que les événements qui se produisent lorsque les utilisateurs ajoutent ou suppriment des lignes, ou lorsque les valeurs de cellule sont modifiées, analysées, validées ou mises en forme) sont également utiles en mode virtuel. Vous pouvez également gérer des événements qui vous permettent de gérer les valeurs qui ne sont généralement pas stockées dans une source de données liée, telles que le texte d’info-bulle de cellule, le texte d’erreur de ligne et de ligne, les données de menu contextuel de cellule et de ligne et les données de hauteur de ligne.  
  
 Pour plus d’informations sur l’implémentation du mode virtuel pour gérer les données en lecture/écriture avec une étendue de validation au niveau des lignes, consultez [procédure pas à pas : implémentation du mode virtuel dans le contrôle DataGridView Windows Forms](implementing-virtual-mode-wf-datagridview-control.md).  
  
 Pour obtenir un exemple qui implémente le mode virtuel avec une portée de validation au niveau de la cellule, consultez la rubrique de référence sur les propriétés de <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>.  
  
 Les événements suivants se produisent uniquement lorsque la propriété <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> est définie sur `true`.  
  
|Événement|Description|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.DataGridView.CellValueNeeded>|Utilisé par le contrôle pour récupérer une valeur de cellule à partir du cache de données pour l’affichage. Cet événement se produit uniquement pour les cellules des colonnes indépendantes.|  
|<xref:System.Windows.Forms.DataGridView.CellValuePushed>|Utilisé par le contrôle pour valider l’entrée d’utilisateur pour une cellule dans le cache de données. Cet événement se produit uniquement pour les cellules des colonnes indépendantes.<br /><br /> Appelez la méthode <xref:System.Windows.Forms.DataGridView.UpdateCellValue%2A> lors de la modification d’une valeur mise en cache en dehors d’un gestionnaire d’événements <xref:System.Windows.Forms.DataGridView.CellValuePushed> pour vous assurer que la valeur actuelle est affichée dans le contrôle et appliquer tous les modes de dimensionnement automatique actuellement en vigueur.|  
|<xref:System.Windows.Forms.DataGridView.NewRowNeeded>|Utilisé par le contrôle pour indiquer la nécessité d’une nouvelle ligne dans le cache de données.|  
|<xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>|Utilisé par le contrôle pour déterminer si une ligne comporte des modifications non validées.|  
|<xref:System.Windows.Forms.DataGridView.CancelRowEdit>|Utilisé par le contrôle pour indiquer qu’une ligne doit rétablir ses valeurs mises en cache.|  
  
 Les événements suivants sont utiles en mode virtuel, mais peuvent être utilisés indépendamment du paramètre de propriété <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>.  
  
|Événements|Description|  
|------------|-----------------|  
|<xref:System.Windows.Forms.DataGridView.UserDeletingRow><br /><br /> <xref:System.Windows.Forms.DataGridView.UserDeletedRow><br /><br /> <xref:System.Windows.Forms.DataGridView.RowsRemoved><br /><br /> <xref:System.Windows.Forms.DataGridView.RowsAdded>|Utilisé par le contrôle pour indiquer quand des lignes sont supprimées ou ajoutées, ce qui vous permet de mettre à jour le cache de données en conséquence.|  
|<xref:System.Windows.Forms.DataGridView.CellFormatting><br /><br /> <xref:System.Windows.Forms.DataGridView.CellParsing><br /><br /> <xref:System.Windows.Forms.DataGridView.CellValidating><br /><br /> <xref:System.Windows.Forms.DataGridView.CellValidated><br /><br /> <xref:System.Windows.Forms.DataGridView.RowValidating><br /><br /> <xref:System.Windows.Forms.DataGridView.RowValidated>|Utilisé par le contrôle pour mettre en forme les valeurs des cellules à afficher et pour analyser et valider les entrées utilisateur.|  
|<xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded>|Utilisé par le contrôle pour récupérer le texte de l’info-bulle de la cellule lorsque la propriété <xref:System.Windows.Forms.DataGridView.DataSource%2A> est définie ou que la propriété <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> est `true`.<br /><br /> Les info-bulles de cellule sont affichées uniquement lorsque la valeur de la propriété <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> est `true`.|  
|<xref:System.Windows.Forms.DataGridView.CellErrorTextNeeded><br /><br /> <xref:System.Windows.Forms.DataGridView.RowErrorTextNeeded>|Utilisé par le contrôle pour récupérer le texte d’erreur de la cellule ou de la ligne lorsque la propriété <xref:System.Windows.Forms.DataGridView.DataSource%2A> est définie ou que la propriété <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> est `true`.<br /><br /> Appelez la méthode <xref:System.Windows.Forms.DataGridView.UpdateCellErrorText%2A> ou la méthode <xref:System.Windows.Forms.DataGridView.UpdateRowErrorText%2A> lorsque vous modifiez le texte d’erreur de la cellule ou de la ligne pour vous assurer que la valeur actuelle est affichée dans le contrôle.<br /><br /> Les glyphes d’erreur de cellule et de ligne s’affichent lorsque les valeurs de propriété <xref:System.Windows.Forms.DataGridView.ShowCellErrors%2A> et <xref:System.Windows.Forms.DataGridView.ShowRowErrors%2A> sont `true`.|  
|<xref:System.Windows.Forms.DataGridView.CellContextMenuStripNeeded><br /><br /> <xref:System.Windows.Forms.DataGridView.RowContextMenuStripNeeded>|Utilisé par le contrôle pour récupérer une cellule ou une ligne <xref:System.Windows.Forms.ContextMenuStrip> lorsque la propriété de <xref:System.Windows.Forms.DataGridView.DataSource%2A> de contrôle est définie ou que la propriété <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> est `true`.|  
|<xref:System.Windows.Forms.DataGridView.RowHeightInfoNeeded><br /><br /> <xref:System.Windows.Forms.DataGridView.RowHeightInfoPushed>|Utilisé par le contrôle pour récupérer ou stocker les informations de hauteur de ligne dans le cache de données. Appelez la méthode <xref:System.Windows.Forms.DataGridView.UpdateRowHeightInfo%2A> lors de la modification des informations de hauteur de ligne mises en cache en dehors d’un gestionnaire d’événements <xref:System.Windows.Forms.DataGridView.RowHeightInfoPushed> pour vous assurer que la valeur actuelle est utilisée dans l’affichage du contrôle.|  
  
## <a name="best-practices-in-virtual-mode"></a>Meilleures pratiques en mode virtuel  
 Si vous implémentez le mode virtuel afin de travailler efficacement avec de grandes quantités de données, vous devez également vous assurer que vous travaillez efficacement avec le contrôle <xref:System.Windows.Forms.DataGridView> lui-même. Pour plus d’informations sur l’utilisation efficace des styles de cellule, le dimensionnement automatique, les sélections et le partage de lignes, consultez [meilleures pratiques pour la mise à l’échelle du contrôle DataGridView Windows Forms](best-practices-for-scaling-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>
- [Réglage des performances dans le contrôle DataGridView Windows Forms](performance-tuning-in-the-windows-forms-datagridview-control.md)
- [Meilleures pratiques pour la mise à l'échelle du contrôle DataGridView Windows Forms](best-practices-for-scaling-the-windows-forms-datagridview-control.md)
- [Procédure pas à pas : implémentation du mode virtuel dans le contrôle DataGridView Windows Forms](implementing-virtual-mode-wf-datagridview-control.md)
- [Implémentation du mode virtuel avec le chargement immédiat des données dans le contrôle DataGridView Windows Forms](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)
