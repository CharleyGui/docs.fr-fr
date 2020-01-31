---
title: Créer un contrôle DataGridView indépendant
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data [Windows Forms], displaying without binding to data source
- DataGridView control [Windows Forms], unbound data
- DataGridView control [Windows Forms], displaying data without binding to a data source
- data [Windows Forms], unbound
- walkthroughs [Windows Forms], DataGridView control
ms.assetid: 5a8d6afa-1b4b-4b24-8db8-501086ffdebe
ms.openlocfilehash: ceb75d4ee845d1f643d4d88d5a9f1bde73edcc70
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740171"
---
# <a name="walkthrough-creating-an-unbound-windows-forms-datagridview-control"></a>Procédure pas à pas : création d'un contrôle DataGridView Windows Forms non lié
Vous pouvez souvent souhaiter afficher des données tabulaires qui ne proviennent pas d’une base de données. Par exemple, vous souhaiterez peut-être afficher le contenu d’un tableau de chaînes à deux dimensions. La classe <xref:System.Windows.Forms.DataGridView> fournit un moyen facile et facilement personnalisable d’afficher des données sans liaison à une source de données. Cette procédure pas à pas montre comment remplir un contrôle <xref:System.Windows.Forms.DataGridView> et gérer l’ajout et la suppression de lignes en mode « indépendant ». Par défaut, l’utilisateur peut ajouter de nouvelles lignes. Pour empêcher l’ajout de lignes, affectez à la propriété <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> la valeur `false`.  
  
 Pour copier le code dans cette rubrique sous la forme d’une liste unique, consultez [Comment : créer un contrôle DataGridView Windows Forms indépendant](how-to-create-an-unbound-windows-forms-datagridview-control.md).  
  
## <a name="creating-the-form"></a>Création du formulaire  
  
#### <a name="to-use-an-unbound-datagridview-control"></a>Pour utiliser un contrôle DataGridView indépendant  
  
1. Créez une classe qui dérive de <xref:System.Windows.Forms.Form> et contient les déclarations de variables et la méthode `Main` suivantes.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#01](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#01)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#01](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#01)]  
    [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#02](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#02](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#02)]  
  
2. Implémentez une méthode `SetupLayout` dans la définition de classe de votre formulaire pour configurer la disposition du formulaire.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#20)]  
  
3. Créez une méthode de `SetupDataGridView` pour configurer les propriétés et les colonnes de <xref:System.Windows.Forms.DataGridView>.  
  
     Cette méthode ajoute d’abord le contrôle <xref:System.Windows.Forms.DataGridView> à la collection de <xref:System.Windows.Forms.Control.Controls%2A> du formulaire. Ensuite, le nombre de colonnes à afficher est défini à l’aide de la propriété <xref:System.Windows.Forms.DataGridView.ColumnCount%2A>. Le style par défaut des en-têtes de colonnes est défini en définissant les propriétés <xref:System.Windows.Forms.DataGridViewCellStyle.BackColor%2A>, <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A>et <xref:System.Windows.Forms.DataGridViewCellStyle.Font%2A> de la <xref:System.Windows.Forms.DataGridViewCellStyle> retournée par la propriété <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A>.  
  
     Les propriétés de disposition et d’apparence sont définies, puis les noms de colonnes sont assignés. Quand cette méthode se termine, le contrôle <xref:System.Windows.Forms.DataGridView> est prêt à être rempli.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#30)]  
  
4. Créez une `PopulateDataGridView` méthode pour ajouter des lignes au contrôle <xref:System.Windows.Forms.DataGridView>.  
  
     Chaque ligne représente une chanson et les informations qui lui sont associées.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#40](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#40)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#40](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#40)]  
  
5. Une fois les méthodes utilitaires en place, vous pouvez attacher des gestionnaires d’événements.  
  
     Vous allez gérer les événements <xref:System.Windows.Forms.Control.Click> des boutons **Ajouter** et **supprimer** , l’événement <xref:System.Windows.Forms.Form.Load> du formulaire et l’événement <xref:System.Windows.Forms.DataGridView.CellFormatting> du contrôle <xref:System.Windows.Forms.DataGridView>.  
  
     Lorsque l’événement <xref:System.Windows.Forms.Control.Click> du bouton **Ajouter** est déclenché, une nouvelle ligne vide est ajoutée au <xref:System.Windows.Forms.DataGridView>.  
  
     Lorsque l’événement <xref:System.Windows.Forms.Control.Click> du bouton **supprimer** est déclenché, la ligne sélectionnée est supprimée, sauf s’il s’agit de la ligne pour les nouveaux enregistrements, ce qui permet à l’utilisateur d’ajouter de nouvelles lignes. Cette ligne est toujours la dernière ligne dans le contrôle <xref:System.Windows.Forms.DataGridView>.  
  
     Lorsque l’événement <xref:System.Windows.Forms.Form.Load> du formulaire est déclenché, les méthodes utilitaires `SetupLayout`, `SetupDataGridView`et `PopulateDataGridView` sont appelées.  
  
     Lorsque l’événement <xref:System.Windows.Forms.DataGridView.CellFormatting> est déclenché, chaque cellule de la `Date` colonne est mise en forme comme une date longue, sauf si la valeur de la cellule ne peut pas être analysée.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#10)]  
  
## <a name="testing-the-application"></a>Test de l'application  
 Vous pouvez maintenant tester le formulaire pour vous assurer qu’il se comporte comme prévu.  
  
#### <a name="to-test-the-form"></a>Pour tester le formulaire  
  
- Appuyez sur F5 pour exécuter l'application.  
  
     Vous verrez un contrôle de <xref:System.Windows.Forms.DataGridView> qui affiche les chansons figurant dans `PopulateDataGridView`. Vous pouvez ajouter de nouvelles lignes avec le bouton **Ajouter une ligne** , et vous pouvez supprimer les lignes sélectionnées à l’aide du bouton **Supprimer la ligne** . Le contrôle de <xref:System.Windows.Forms.DataGridView> indépendant est le magasin de données, et ses données sont indépendantes de toute source externe, telle qu’une <xref:System.Data.DataSet> ou un tableau.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Cette application vous offre une compréhension de base des fonctionnalités du contrôle <xref:System.Windows.Forms.DataGridView>. Vous pouvez personnaliser l’apparence et le comportement du contrôle <xref:System.Windows.Forms.DataGridView> de plusieurs façons :  
  
- Modifiez les styles de bordure et d’en-tête. Pour plus d’informations, consultez [Comment : modifier les styles de bordure et de quadrillage dans le contrôle DataGridView Windows Forms](change-the-border-and-gridline-styles-in-the-datagrid.md).  
  
- Activez ou restreignez l’entrée utilisateur dans le contrôle <xref:System.Windows.Forms.DataGridView>. Pour plus d’informations, consultez [Comment : empêcher l’ajout et la suppression de lignes dans le contrôle datagridview Windows Forms](prevent-row-addition-and-deletion-datagridview.md), et [Comment : créer des colonnes en lecture seule dans le contrôle DataGridView Windows Forms](how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md).  
  
- Vérifiez les entrées d’utilisateur pour les erreurs liées aux bases de données. Pour plus d’informations, consultez [procédure pas à pas : gestion des erreurs qui se produisent lors de l’entrée de données dans le contrôle DataGridView Windows Forms](handling-errors-that-occur-during-data-entry-in-the-datagrid.md).  
  
- Gérer des jeux de données très volumineux en mode virtuel. Pour plus d’informations, consultez [procédure pas à pas : implémentation du mode virtuel dans le Windows Forms contrôle DataGridView](implementing-virtual-mode-wf-datagridview-control.md).  
  
- Personnaliser l’apparence des cellules. Pour plus d’informations, consultez [Comment : personnaliser l’apparence des cellules dans le Windows Forms contrôle DataGridView](customize-the-appearance-of-cells-in-the-datagrid.md) et [Comment : définir des styles de cellules par défaut pour le contrôle DataGridView Windows Forms](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.DataGridView>
- [Affichage des données dans le contrôle DataGridView Windows Forms](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Guide pratique pour créer un contrôle DataGridView Windows Forms indépendant](how-to-create-an-unbound-windows-forms-datagridview-control.md)
- [Modes d’affichage des données dans le contrôle DataGridView Windows Forms](data-display-modes-in-the-windows-forms-datagridview-control.md)
