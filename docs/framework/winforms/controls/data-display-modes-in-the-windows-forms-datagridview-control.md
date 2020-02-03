---
title: Modes d’affichage des données dans le contrôle DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms], display modes
- data grids [Windows Forms], display modes
- DataGridView control [Windows Forms], display modes
ms.assetid: 9755a030-3f3f-4705-a661-ba5a48a81875
ms.openlocfilehash: ad6be647e3a36904b055fd6771f539df28938fab
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744009"
---
# <a name="data-display-modes-in-the-windows-forms-datagridview-control"></a>Modes d'affichage des données dans le contrôle DataGridView Windows Forms
Le contrôle <xref:System.Windows.Forms.DataGridView> peut afficher des données dans trois modes distincts : liés, indépendants et virtuels. Choisissez le mode le plus approprié en fonction de vos besoins.  
  
## <a name="unbound"></a>Non liée  
 Le mode indépendant est adapté à l’affichage de petites quantités de données que vous gérez par programme. Vous n’attachez pas directement le contrôle <xref:System.Windows.Forms.DataGridView> à une source de données comme en mode dépendant. Au lieu de cela, vous devez remplir le contrôle vous-même, en général à l’aide de la méthode <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A?displayProperty=nameWithType>.  
  
 Le mode indépendant peut être particulièrement utile pour les données statiques, en lecture seule ou lorsque vous souhaitez fournir votre propre code qui interagit avec un magasin de données externe. Toutefois, lorsque vous souhaitez que les utilisateurs interagissent avec une source de données externe, vous utilisez généralement le mode dépendant.  
  
 Pour obtenir un exemple qui utilise un <xref:System.Windows.Forms.DataGridView>indépendant en lecture seule, consultez [Comment : créer un contrôle DataGridView Windows Forms indépendant](how-to-create-an-unbound-windows-forms-datagridview-control.md).  
  
## <a name="bound"></a>Lié  
 Le mode lié est adapté à la gestion des données à l’aide de l’interaction automatique avec le magasin de données. Vous pouvez attacher le contrôle <xref:System.Windows.Forms.DataGridView> directement à sa source de données en définissant la propriété <xref:System.Windows.Forms.DataGridView.DataSource%2A>. Lorsque le contrôle est lié aux données, les lignes de données sont envoyées et extraites sans nécessiter de gestion explicite de votre part. Lorsque la propriété <xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A> est `true`, chaque colonne de votre source de données entraîne la création d’une colonne correspondante dans le contrôle. Si vous préférez créer vos propres colonnes, vous pouvez définir cette propriété sur `false` et utiliser la propriété <xref:System.Windows.Forms.DataGridViewColumn.DataPropertyName%2A> pour lier chaque colonne lorsque vous la configurez. Cela est utile lorsque vous souhaitez utiliser un type de colonne autre que les types qui sont générés par défaut. Pour plus d’informations, consultez [types de colonnes dans le contrôle DataGridView Windows Forms](column-types-in-the-windows-forms-datagridview-control.md).  
  
 Pour obtenir un exemple qui utilise un contrôle de <xref:System.Windows.Forms.DataGridView> lié, consultez [procédure pas à pas : validation des données dans le contrôle DataGridView Windows Forms](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).  
  
 Vous pouvez également ajouter des colonnes indépendantes à un contrôle de <xref:System.Windows.Forms.DataGridView> en mode dépendant. Cela est utile lorsque vous souhaitez afficher une colonne de boutons ou des liens qui permettent aux utilisateurs d’effectuer des actions sur des lignes spécifiques. Il est également utile d’afficher des colonnes avec des valeurs calculées à partir de colonnes dépendantes. Vous pouvez remplir les valeurs de cellule pour les colonnes calculées dans un gestionnaire pour l’événement <xref:System.Windows.Forms.DataGridView.CellFormatting>. Toutefois, si vous utilisez un <xref:System.Data.DataSet> ou <xref:System.Data.DataTable> comme source de données, vous souhaiterez peut-être utiliser la propriété <xref:System.Data.DataColumn.Expression%2A?displayProperty=nameWithType> pour créer une colonne calculée à la place. Dans ce cas, le contrôle <xref:System.Windows.Forms.DataGridView> traitera la colonne calculée comme n’importe quelle autre colonne dans la source de données.  
  
 Le tri par colonnes indépendantes en mode dépendant n’est pas pris en charge. Si vous créez une colonne indépendante en mode dépendant qui contient des valeurs modifiables par l’utilisateur, vous devez implémenter le mode virtuel pour conserver ces valeurs lorsque le contrôle est trié par une colonne liée.  
  
## <a name="virtual"></a>Virtuelle  
 Avec le mode virtuel, vous pouvez implémenter vos propres opérations de gestion de données. Cela est nécessaire pour conserver les valeurs des colonnes indépendantes en mode dépendant lorsque le contrôle est trié par colonnes dépendantes. L’utilisation principale du mode virtuel, cependant, consiste à optimiser les performances lors de l’interaction avec de grandes quantités de données.  
  
 Vous attachez le contrôle <xref:System.Windows.Forms.DataGridView> à un cache que vous gérez, et votre code contrôle le moment où les lignes de données font l’objet d’un push et d’une extraction. Pour réduire l’encombrement mémoire, le cache doit être de la même taille que le nombre de lignes actuellement affichées. Lorsque l’utilisateur fait défiler les nouvelles lignes dans la vue, votre code demande de nouvelles données à partir du cache et vide éventuellement les anciennes données de la mémoire.  
  
 Lorsque vous implémentez le mode virtuel, vous devez effectuer le suivi de la nécessité d’une nouvelle ligne dans le modèle de données et de la restauration de l’ajout de la nouvelle ligne. L’implémentation exacte de cette fonctionnalité dépend de l’implémentation du modèle de données et de la sémantique de la transaction du modèle de données. indique si la portée de validation se situe au niveau de la cellule ou de la ligne.  
  
 Pour plus d’informations sur le mode virtuel, consultez [mode virtuel dans le Windows Forms contrôle DataGridView](virtual-mode-in-the-windows-forms-datagridview-control.md). Pour obtenir un exemple qui montre comment utiliser les événements en mode virtuel, consultez [procédure pas à pas : implémentation du mode virtuel dans le contrôle DataGridView Windows Forms](implementing-virtual-mode-wf-datagridview-control.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.VirtualMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.DataGridViewColumn.DataPropertyName%2A?displayProperty=nameWithType>
- [Affichage des données dans le contrôle DataGridView Windows Forms](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Types de colonnes dans le contrôle DataGridView Windows Forms](column-types-in-the-windows-forms-datagridview-control.md)
- [Procédure pas à pas : création d’un contrôle DataGridView Windows Forms non lié](walkthrough-creating-an-unbound-windows-forms-datagridview-control.md)
- [Guide pratique pour lier des données au contrôle DataGridView Windows Forms](how-to-bind-data-to-the-windows-forms-datagridview-control.md)
- [Mode virtuel dans le contrôle DataGridView Windows Forms](virtual-mode-in-the-windows-forms-datagridview-control.md)
- [Procédure pas à pas : implémentation du mode virtuel dans le contrôle DataGridView Windows Forms](implementing-virtual-mode-wf-datagridview-control.md)
