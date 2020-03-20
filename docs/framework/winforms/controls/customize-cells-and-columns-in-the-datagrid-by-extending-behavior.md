---
title: Personnaliser les cellules et les colonnes dans le contrôle DataGridView en élargissant leur comportement et leur apparence
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], cell customization
- columns [Windows Forms], customizing in DataGridView control
- cells [Windows Forms], customizing in DataGridView control
ms.assetid: 9b7dc7b6-5ce6-4566-9949-902f74f17a81
ms.openlocfilehash: e111f0bce812fc0851fabd1fde0fc2a6d44dd25f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182389"
---
# <a name="how-to-customize-cells-and-columns-in-the-windows-forms-datagridview-control-by-extending-their-behavior-and-appearance"></a>Comment : personnaliser les cellules et les colonnes du contrôle DataGridView Windows Forms en étendant leur comportement et leur apparence
Le contrôle <xref:System.Windows.Forms.DataGridView> offre plusieurs manières de personnaliser son apparence et son comportement à l'aide de propriétés, d'événements et de classes auxiliaires. Parfois, vous pouvez avoir des exigences pour vos cellules qui vont au-delà de ce que peuvent fournir ces fonctionnalités. Vous pouvez créer vos propres classes <xref:System.Windows.Forms.DataGridViewCell> pour fournir des fonctionnalités étendues.  
  
 Vous pouvez créer une classe <xref:System.Windows.Forms.DataGridViewCell> personnalisée en dérivant de la classe de base <xref:System.Windows.Forms.DataGridViewCell> ou de l'une de ses classes dérivées. Bien que vous puissiez afficher tout type de cellule dans tout type de colonne, vous créerez en général aussi une classe <xref:System.Windows.Forms.DataGridViewColumn> personnalisée spécialisée pour l'affichage de votre type de cellule. Les classes de colonne dérivent de <xref:System.Windows.Forms.DataGridViewColumn> ou de l'un de ses types dérivés.  
  
 Dans l'exemple de code suivant, vous allez créer une classe de cellule personnalisée nommée `DataGridViewRolloverCell` qui détecte quand la souris entre et sort des limites de la cellule. Pendant que la souris se trouve dans les limites de la cellule, un rectangle d'incrustation est dessiné. Ce nouveau type dérive de <xref:System.Windows.Forms.DataGridViewTextBoxCell> et se comporte à tous autres égards comme sa classe de base. La classe de colonne auxiliaire se nomme `DataGridViewRolloverColumn`.  
  
 Pour utiliser ces classes, créez un formulaire contenant un contrôle <xref:System.Windows.Forms.DataGridView>, ajoutez un ou plusieurs objets `DataGridViewRolloverColumn` à la collection <xref:System.Windows.Forms.DataGridView.Columns%2A> et remplissez le contrôle avec des lignes contenant des valeurs.  
  
> [!NOTE]
> Cet exemple ne fonctionnera pas correctement si vous ajoutez des lignes vides. Des lignes vides sont créées par exemple quand vous ajoutez des lignes au contrôle en définissant la propriété <xref:System.Windows.Forms.DataGridView.RowCount%2A>. Cela est dû au fait que les lignes ajoutées dans ce cas sont partagées automatiquement, ce qui signifie que les objets `DataGridViewRolloverCell` ne sont instanciés qu'une fois que vous cliquez sur les cellules individuelles, provoquant ainsi l'annulation du partage des lignes associées.  
  
 Ce type de personnalisation de cellule exigeant des lignes non partagées, il ne convient pas aux grands jeux de données. Pour plus d’informations sur le partage des rangées, voir [les meilleures pratiques pour l’échelle de windows Forms DataGridView Control](best-practices-for-scaling-the-windows-forms-datagridview-control.md).  
  
> [!NOTE]
> Quand vous dérivez de <xref:System.Windows.Forms.DataGridViewCell> ou <xref:System.Windows.Forms.DataGridViewColumn> et que vous ajoutez de nouvelles propriétés à la classe dérivée, veillez à substituer la méthode `Clone` pour copier les nouvelles propriétés lors des opérations de clonage. Vous devez aussi appeler la méthode `Clone` de la classe de base pour que les propriétés de la classe de base soient copiées dans la nouvelle cellule ou colonne.  
  
### <a name="to-customize-cells-and-columns-in-the-datagridview-control"></a>Pour personnaliser des cellules et des colonnes dans le contrôle DataGridView  
  
1. Dérivez une nouvelle classe de cellule, nommée `DataGridViewRolloverCell`, à partir du type <xref:System.Windows.Forms.DataGridViewTextBoxCell>.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#201](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#201)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#201](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#201)]  
    [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#202](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#202)]
    [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#202](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#202)]  
  
2. Substituez la méthode <xref:System.Windows.Forms.DataGridViewTextBoxCell.Paint%2A> dans la classe `DataGridViewRolloverCell` . Dans la substitution, appelez d'abord l'implémentation de la classe de base, qui gère la fonctionnalité de zone de texte hébergée. Ensuite, utilisez la méthode <xref:System.Windows.Forms.Control.PointToClient%2A> du contrôle pour convertir la position du curseur (en coordonnées d'écran) en coordonnées de la zone cliente <xref:System.Windows.Forms.DataGridView>. Si les coordonnées de la souris se situent dans les limites de la cellule, dessinez le rectangle d'incrustation.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#210](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#210)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#210](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#210)]  
  
3. Substituez les méthodes <xref:System.Windows.Forms.DataGridViewCell.OnMouseEnter%2A> et <xref:System.Windows.Forms.DataGridViewCell.OnMouseLeave%2A> dans la classe `DataGridViewRolloverCell` pour forcer les cellules à se repeindre quand le pointeur de la souris entre ou quitte les cellules.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#220](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#220)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#220](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#220)]  
  
4. Dérivez une nouvelle classe, nommée `DataGridViewRolloverCellColumn`, à partir du type <xref:System.Windows.Forms.DataGridViewColumn>. Dans le constructeur, assignez un nouvel objet `DataGridViewRolloverCell` à sa propriété <xref:System.Windows.Forms.DataGridViewColumn.CellTemplate%2A>.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#300](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#300)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#300](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#300)]  
  
## <a name="example"></a> Exemple  
 L'exemple de code complet comprend un petit formulaire de test qui illustre le comportement du type de cellule personnalisé.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#000](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#000)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
- Références aux assemblys System, System.Windows.Form et System.Drawing.  

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCell>
- <xref:System.Windows.Forms.DataGridViewColumn>
- [Personnalisation du contrôle DataGridView Windows Forms](customizing-the-windows-forms-datagridview-control.md)
- [Architecture du contrôle DataGridView](datagridview-control-architecture-windows-forms.md)
- [Types de colonnes dans le contrôle DataGridView Windows Forms](column-types-in-the-windows-forms-datagridview-control.md)
- [Meilleures pratiques pour la mise à l'échelle du contrôle DataGridView Windows Forms](best-practices-for-scaling-the-windows-forms-datagridview-control.md)
