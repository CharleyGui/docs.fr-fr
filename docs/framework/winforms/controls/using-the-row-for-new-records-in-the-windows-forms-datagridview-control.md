---
title: Utilisation de la ligne pour les nouveaux enregistrements dans le contrôle DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], adding rows for new records
- rows [Windows Forms], new records
- DataGridView control [Windows Forms], data entry
ms.assetid: 6110f1ea-9794-442c-a98a-f104a1feeaf4
ms.openlocfilehash: 2fcd35f8c4d04909cdbc26f6a4293fdd570385b8
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728334"
---
# <a name="using-the-row-for-new-records-in-the-windows-forms-datagridview-control"></a>Utilisation de la ligne pour les nouveaux enregistrements dans le contrôle DataGridView Windows Forms
Lorsque vous utilisez une <xref:System.Windows.Forms.DataGridView> pour modifier des données dans votre application, vous souhaiterez souvent offrir à vos utilisateurs la possibilité d’ajouter de nouvelles lignes de données au magasin de données. Le contrôle <xref:System.Windows.Forms.DataGridView> prend en charge cette fonctionnalité en fournissant une ligne pour les nouveaux enregistrements, qui est toujours indiqué comme dernière ligne. Elle est marquée avec un symbole astérisque (*) dans son en-tête de ligne. Les sections suivantes décrivent certaines des choses que vous devez prendre en compte lorsque vous programmez avec la ligne pour les nouveaux enregistrements activés.  
  
## <a name="displaying-the-row-for-new-records"></a>Affichage de la ligne pour les nouveaux enregistrements  
 Utilisez la propriété <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> pour indiquer si la ligne des nouveaux enregistrements est affichée. La valeur par défaut de cette propriété est `true`.  
  
 Pour le cas lié aux données, la ligne des nouveaux enregistrements sera affichée si la propriété <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> du contrôle et la propriété <xref:System.ComponentModel.IBindingList.AllowNew%2A?displayProperty=nameWithType> de la source de données sont toutes les deux `true`. Si l’un ou l’autre est `false`, la ligne n’est pas affichée.  
  
## <a name="populating-the-row-for-new-records-with-default-data"></a>Remplissage de la ligne pour les nouveaux enregistrements avec les données par défaut  
 Lorsque l’utilisateur sélectionne la ligne pour les nouveaux enregistrements comme ligne actuelle, le contrôle de <xref:System.Windows.Forms.DataGridView> déclenche l’événement <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded>.  
  
 Cet événement donne accès au nouvel <xref:System.Windows.Forms.DataGridViewRow> et vous permet de remplir la nouvelle ligne avec les données par défaut. Pour plus d’informations, consultez [Comment : spécifier des valeurs par défaut pour les nouvelles lignes dans le contrôle DataGridView Windows Forms](specify-default-values-for-new-rows-in-the-datagrid.md)  
  
## <a name="the-rows-collection"></a>Collection Rows  
 La ligne des nouveaux enregistrements est contenue dans la collection de <xref:System.Windows.Forms.DataGridView.Rows%2A> du contrôle <xref:System.Windows.Forms.DataGridView>, mais se comporte différemment à deux égards :  
  
- La ligne des nouveaux enregistrements ne peut pas être supprimée de la collection <xref:System.Windows.Forms.DataGridView.Rows%2A> par programmation. Une <xref:System.InvalidOperationException> est levée si cette tentative est effectuée. L’utilisateur ne peut pas non plus supprimer la ligne pour les nouveaux enregistrements. La méthode <xref:System.Windows.Forms.DataGridViewRowCollection.Clear%2A?displayProperty=nameWithType> ne supprime pas cette ligne de la collection <xref:System.Windows.Forms.DataGridView.Rows%2A>.  
  
- Aucune ligne ne peut être ajoutée après la ligne pour les nouveaux enregistrements. Une <xref:System.InvalidOperationException> est déclenchée si cette tentative est effectuée. Par conséquent, la ligne des nouveaux enregistrements est toujours la dernière ligne dans le contrôle <xref:System.Windows.Forms.DataGridView>. Les méthodes sur <xref:System.Windows.Forms.DataGridViewRowCollection> qui ajoutent des lignes (<xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A>, <xref:System.Windows.Forms.DataGridViewRowCollection.AddCopy%2A>et <xref:System.Windows.Forms.DataGridViewRowCollection.AddCopies%2A>) appellent toutes les méthodes d’insertion en interne lorsque la ligne pour les nouveaux enregistrements est présente.  
  
## <a name="visual-customization-of-the-row-for-new-records"></a>Personnalisation visuelle de la ligne pour les nouveaux enregistrements  
 Lorsque la ligne des nouveaux enregistrements est créée, elle est basée sur la ligne spécifiée par la propriété <xref:System.Windows.Forms.DataGridView.RowTemplate%2A>. Les styles de cellule qui ne sont pas spécifiés pour cette ligne sont hérités d’autres propriétés. Pour plus d’informations sur l’héritage de style de cellule, consultez [styles de cellule dans le contrôle DataGridView Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md).  
  
 Les valeurs initiales affichées par les cellules de la ligne pour les nouveaux enregistrements sont extraites de la propriété <xref:System.Windows.Forms.DataGridViewCell.DefaultNewRowValue%2A> de chaque cellule. Pour les cellules de type <xref:System.Windows.Forms.DataGridViewImageCell>, cette propriété retourne une image d’espace réservé. Sinon, cette propriété retourne `null`. Vous pouvez substituer cette propriété pour retourner une valeur personnalisée. Toutefois, ces valeurs initiales peuvent être remplacées par un gestionnaire d’événements <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> lorsque le focus entre dans la ligne pour les nouveaux enregistrements.  
  
 Les icônes standard pour l’en-tête de cette ligne, qui sont une flèche ou un astérisque, ne sont pas exposées publiquement. Si vous souhaitez personnaliser les icônes, vous devrez créer une classe de <xref:System.Windows.Forms.DataGridViewRowHeaderCell> personnalisée.  
  
 Les icônes standard utilisent la propriété <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> du <xref:System.Windows.Forms.DataGridViewCellStyle> en cours d’utilisation par la cellule d’en-tête de ligne. Les icônes standard ne sont pas rendues si l’espace est insuffisant pour les afficher complètement.  
  
 Si la cellule d’en-tête de ligne a une valeur de chaîne définie et que l’espace est insuffisant pour le texte et l’icône, l’icône est supprimée en premier.  
  
## <a name="sorting"></a>Tri  
 En mode indépendant, les nouveaux enregistrements sont toujours ajoutés à la fin de l' <xref:System.Windows.Forms.DataGridView> même si l’utilisateur a trié le contenu du <xref:System.Windows.Forms.DataGridView>. L’utilisateur devra réappliquer le tri pour trier la ligne à la position correcte ; ce comportement est similaire à celui du contrôle <xref:System.Windows.Forms.ListView>.  
  
 Dans les modes de liaison de données et virtuelles, le comportement d’insertion lorsqu’un tri est appliqué dépend de l’implémentation du modèle de données. Pour ADO.NET, la ligne est immédiatement triée dans la position correcte.  
  
## <a name="other-notes-on-the-row-for-new-records"></a>Autres remarques sur la ligne pour les nouveaux enregistrements  
 Vous ne pouvez pas définir la propriété <xref:System.Windows.Forms.DataGridViewRow.Visible%2A> de cette ligne sur `false`. Une <xref:System.InvalidOperationException> est déclenchée si cette tentative est effectuée.  
  
 La ligne des nouveaux enregistrements est toujours créée dans l’état désélectionné.  
  
## <a name="virtual-mode"></a>Mode virtuel  
 Si vous implémentez le mode virtuel, vous devez effectuer le suivi de la nécessité d’une ligne pour les nouveaux enregistrements dans le modèle de données et de la restauration de l’ajout de la ligne. L’implémentation exacte de cette fonctionnalité dépend de l’implémentation du modèle de données et de sa sémantique de transaction, par exemple, si la portée de validation se situe au niveau de la cellule ou de la ligne. Pour plus d’informations, consultez [mode virtuel dans le contrôle DataGridView Windows Forms](virtual-mode-in-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded?displayProperty=nameWithType>
- [Saisie de données dans le contrôle DataGridView Windows Forms](data-entry-in-the-windows-forms-datagridview-control.md)
- [Guide pratique pour spécifier des valeurs par défaut pour les nouvelles lignes dans le contrôle DataGridView Windows Forms](specify-default-values-for-new-rows-in-the-datagrid.md)
