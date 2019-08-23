---
title: 'Procédure : Générer une boîte de dialogue d’interface utilisateur standard à l’aide d’une grille'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dialog boxes [WPF], creating
- Grid control [WPF], creating [WPF], dialog box
ms.assetid: d6ac3d51-844b-4d29-96d8-81a696a7b960
ms.openlocfilehash: 68c9653e616388374aad2ad33ac7dab68446241d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923422"
---
# <a name="how-to-build-a-standard-ui-dialog-box-by-using-grid"></a>Procédure : Générer une boîte de dialogue d’interface utilisateur standard à l’aide d’une grille
Cet exemple montre comment créer une boîte de [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] dialogue standard à l’aide <xref:System.Windows.Controls.Grid> de l’élément.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant crée une boîte de dialogue telle que la boîte de dialogue **exécuter** dans le système d’exploitation Windows.  
  
 L’exemple crée un <xref:System.Windows.Controls.Grid> et utilise les <xref:System.Windows.Controls.ColumnDefinition> classes <xref:System.Windows.Controls.RowDefinition> et pour définir cinq colonnes et quatre lignes.  
  
 L’exemple ajoute et positionne ensuite un <xref:System.Windows.Controls.Image>, `RunIcon.png`, pour représenter l’image trouvée dans la boîte de dialogue. L’image est placée sur la première colonne et ligne de <xref:System.Windows.Controls.Grid> (l’angle supérieur gauche).  
  
 Ensuite, l’exemple ajoute un <xref:System.Windows.Controls.TextBlock> élément à la première colonne, qui s’étend sur les colonnes restantes de la première ligne. Elle ajoute un <xref:System.Windows.Controls.TextBlock> autre élément à la deuxième ligne de la première colonne, pour représenter la zone de texte **ouverte** . Le <xref:System.Windows.Controls.TextBlock> suivant, qui représente la zone d’entrée de données.  
  
 Enfin, l’exemple ajoute trois <xref:System.Windows.Controls.Button> éléments à la dernière ligne, qui représentent les événements **OK**, **Annuler**et **Parcourir** .  
  
 [!code-csharp[GridRunDialog#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GridRunDialog/CSharp/window1.xaml.cs#1)]
 [!code-vb[GridRunDialog#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GridRunDialog/VisualBasic/grid_vb.vb#1)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Controls.Grid>
- <xref:System.Windows.GridUnitType>
- [Vue d’ensemble de Panel](panels-overview.md)
- [Rubriques de guide pratique](grid-how-to-topics.md)
