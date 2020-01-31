---
title: accéder à des objets liés à des lignes DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- object binding [Windows Forms], accessing bound objects
- data grids [Windows Forms], accessing bound objects
- DataGridView control [Windows Forms], accessing objects bound to rows
ms.assetid: 0e05748f-4403-4eb8-8b2f-b098108181b5
ms.openlocfilehash: 0b9a4becb78ae817141728467c1e9ea5b693476d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743166"
---
# <a name="how-to-access-objects-bound-to-windows-forms-datagridview-rows"></a>Comment : accéder à des objets liés à des lignes DataGridView Windows Forms
Il est parfois utile d’afficher une table d’informations stockée dans une collection d’objets métier. Quand vous liez un contrôle <xref:System.Windows.Forms.DataGridView> à une telle collection, chaque propriété publique est affichée dans sa propre colonne, à moins que la propriété n'ait été marquée comme non consultable avec un <xref:System.ComponentModel.BrowsableAttribute>. Par exemple, une collection d’objets `Customer` aurait des colonnes telles que **Nom** et **Adresse**.  
  
 Si ces objets contiennent des informations supplémentaires et du code auquel vous souhaitez accéder, vous pouvez l'atteindre via des objets de ligne. Dans l'exemple de code suivant, les utilisateurs peuvent sélectionner plusieurs lignes et cliquer sur un bouton pour envoyer une facture à chacun des clients correspondants.  
  
### <a name="to-access-row-bound-objects"></a>Pour accéder à des objets liés à une ligne  
  
- Utilisez la propriété <xref:System.Windows.Forms.DataGridViewRow.DataBoundItem%2A?displayProperty=nameWithType>.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewObjectBinding#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/CS/datagridviewobjectbinding.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewObjectBinding#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/VB/datagridviewobjectbinding.vb#10)]  
  
## <a name="example"></a>Exemple  
 L'exemple de code complet comprend une implémentation `Customer` simple et lie le <xref:System.Windows.Forms.DataGridView> à un <xref:System.Collections.ArrayList> contenant quelques objets `Customer`. Le gestionnaire d’événements <xref:System.Windows.Forms.Control.Click> du <xref:System.Windows.Forms.Button?displayProperty=nameWithType> doit accéder aux objets `Customer` par l’intermédiaire des lignes, car la collection de clients n’est pas accessible en dehors du gestionnaire d’événements <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType>.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewObjectBinding#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/CS/datagridviewobjectbinding.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewObjectBinding#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/VB/datagridviewobjectbinding.vb#00)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
- des références aux assemblys System et System.Windows.Forms ;  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewRow>
- <xref:System.Windows.Forms.DataGridViewRow.DataBoundItem%2A?displayProperty=nameWithType>
- [Affichage des données dans le contrôle DataGridView Windows Forms](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Comment : lier des objets aux contrôles DataGridView Windows Forms](how-to-bind-objects-to-windows-forms-datagridview-controls.md)
