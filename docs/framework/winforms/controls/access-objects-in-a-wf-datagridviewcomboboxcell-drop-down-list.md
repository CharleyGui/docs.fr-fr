---
title: Accéder aux objets dans la liste déroulante DataGridViewComboBoxCell
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], accessing objects in combo box cells
- combo boxes [Windows Forms], in DataGridView control
- combo boxes [Windows Forms], accessing objects in DataGridViewComboBoxCell drop-down lists
ms.assetid: bcbe794a-d1fa-47f8-b5a3-5f085b32097d
ms.openlocfilehash: 7e76ab1ac9089778e4371f4ee65b06d5ebc570bf
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746311"
---
# <a name="how-to-access-objects-in-a-windows-forms-datagridviewcomboboxcell-drop-down-list"></a>Comment : accéder à des objets dans une liste déroulante DataGridViewComboBoxCell Windows Forms
À l’instar du contrôle <xref:System.Windows.Forms.ComboBox>, les types <xref:System.Windows.Forms.DataGridViewComboBoxColumn> et <xref:System.Windows.Forms.DataGridViewComboBoxCell> vous permettent d’ajouter des objets arbitraires à leurs listes déroulantes. Avec cette fonctionnalité, vous pouvez représenter des États complexes dans une liste déroulante sans avoir à stocker les objets correspondants dans une collection distincte.  
  
 Contrairement au contrôle <xref:System.Windows.Forms.ComboBox>, les types de <xref:System.Windows.Forms.DataGridView> n’ont pas de propriété <xref:System.Windows.Forms.ComboBox.SelectedItem%2A> pour récupérer l’objet actuellement sélectionné. Au lieu de cela, vous devez définir la propriété <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A?displayProperty=nameWithType> ou <xref:System.Windows.Forms.DataGridViewComboBoxCell.ValueMember%2A?displayProperty=nameWithType> sur le nom d’une propriété de votre objet métier. Lorsque l’utilisateur effectue une sélection, la propriété indiquée de l’objet métier définit la propriété de <xref:System.Windows.Forms.DataGridViewCell.Value%2A> de la cellule.  
  
 Pour récupérer l’objet métier à l’aide de la valeur de cellule, la propriété `ValueMember` doit indiquer une propriété qui retourne une référence à l’objet métier lui-même. Par conséquent, si le type de l’objet métier n’est pas sous votre contrôle, vous devez ajouter une telle propriété en étendant le type par héritage.  
  
 Les procédures suivantes montrent comment remplir une liste déroulante avec des objets métier et récupérer les objets par le biais de la propriété <xref:System.Windows.Forms.DataGridViewCell.Value%2A> de la cellule.  
  
### <a name="to-add-business-objects-to-the-drop-down-list"></a>Pour ajouter des objets métier à la liste déroulante  
  
1. Créer un <xref:System.Windows.Forms.DataGridViewComboBoxColumn> et remplir son <xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A> collection. Vous pouvez également définir la propriété <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A> de la colonne sur la collection d’objets métier. Dans ce cas, toutefois, vous ne pouvez pas ajouter « non assigné » à la liste déroulante sans créer un objet métier correspondant dans votre collection.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#110](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#110)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#110)]  
  
2. Définissez les propriétés <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> et <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A>. <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> indique la propriété de l’objet métier à afficher dans la liste déroulante. <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> indique la propriété qui retourne une référence à l’objet métier.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#115](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#115)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#115](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#115)]  
  
3. Assurez-vous que votre type d’objet métier contient une propriété qui retourne une référence à l’instance actuelle. Cette propriété doit être nommée avec la valeur assignée à <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> à l’étape précédente.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#310](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#310)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#310](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#310)]  
  
### <a name="to-retrieve-the-currently-selected-business-object"></a>Pour récupérer l’objet métier actuellement sélectionné  
  
- Récupérez la propriété <xref:System.Windows.Forms.DataGridViewCell.Value%2A> de la cellule et effectuez un cast de celle-ci vers le type d’objet métier.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#120)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#120)]  
  
## <a name="example"></a>Exemple  
 L’exemple complet illustre l’utilisation des objets métier dans une liste déroulante. Dans l’exemple, un contrôle de <xref:System.Windows.Forms.DataGridView> est lié à une collection d’objets `Task`. Chaque objet `Task` a une propriété `AssignedTo` qui indique l’objet `Employee` actuellement assigné à cette tâche. La colonne `Assigned To` affiche la valeur de la propriété `Name` pour chaque employé affecté, ou « non assigné » si la valeur de la propriété `Task.AssignedTo` est `null`.  
  
 Pour afficher le comportement de cet exemple, procédez comme suit :  
  
1. Modifiez les affectations dans la colonne `Assigned To` en sélectionnant des valeurs différentes dans les listes déroulantes ou en appuyant sur CTRL + 0 dans une cellule de zone de liste déroulante.  
  
2. Cliquez sur `Generate Report` pour afficher les affectations actuelles. Cela démontre qu’une modification de la colonne `Assigned To` met automatiquement à jour la collection de `tasks`.  
  
3. Cliquez sur un bouton de `Request Status` pour appeler la méthode `RequestStatus` de l’objet `Employee` actif pour cette ligne. Cela montre que l’objet sélectionné a été récupéré avec succès.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#000](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#000)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
- des références aux assemblys System et System.Windows.Forms ;  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewComboBoxColumn>
- <xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewComboBoxCell>
- <xref:System.Windows.Forms.DataGridViewComboBoxCell.Items%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewComboBoxCell.DataSource%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewComboBoxCell.ValueMember%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCell.Value%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ComboBox>
- [Affichage des données dans le contrôle DataGridView Windows Forms](displaying-data-in-the-windows-forms-datagridview-control.md)
