---
title: Redimensionner des colonnes et des lignes dans le contrôle DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], sizing rows and columns
- columns [Windows Forms], resizing in grids
- data grids [Windows Forms], resizing columns and rows
ms.assetid: 7532764d-e5c1-4943-a08b-6377a722d3b6
ms.openlocfilehash: 8f8394a837ccc11c469f9ad4feeb60464d0014fe
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742412"
---
# <a name="resizing-columns-and-rows-in-the-windows-forms-datagridview-control"></a>Redimensionnement des colonnes et des lignes dans le contrôle DataGridView Windows Forms
Le contrôle `DataGridView` fournit de nombreuses options permettant de personnaliser le comportement de dimensionnement de ses colonnes et de ses lignes. En règle générale, les cellules `DataGridView` ne sont pas redimensionnées en fonction de leur contenu. Au lieu de cela, ils détourent toute valeur d’affichage supérieure à la cellule. Si le contenu peut être affiché sous forme de chaîne, la cellule l’affiche dans une info-bulle.  
  
 Par défaut, les utilisateurs peuvent faire glisser les séparateurs de ligne, de colonne et d’en-tête avec la souris pour afficher plus d’informations. Les utilisateurs peuvent également double-cliquer sur un séparateur pour redimensionner automatiquement la ligne, la colonne ou la bande d’en-tête associée en fonction de son contenu.  
  
 Le contrôle `DataGridView` fournit des propriétés, des méthodes et des événements qui vous permettent de personnaliser ou de désactiver tous ces comportements dirigés par l’utilisateur. En outre, vous pouvez redimensionner des lignes, des colonnes et des en-têtes par programmation en fonction de leur contenu, ou vous pouvez les configurer pour qu’ils se redimensionnent automatiquement chaque fois que leur contenu change. Vous pouvez également configurer des colonnes pour diviser automatiquement la largeur disponible du contrôle dans les proportions que vous spécifiez.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Options de dimensionnement dans le contrôle DataGridView Windows Forms](sizing-options-in-the-windows-forms-datagridview-control.md)  
 Décrit les options de dimensionnement des lignes, des colonnes et des en-têtes. Fournit également des détails sur les propriétés et les méthodes liées au dimensionnement, et décrit les scénarios d’utilisation courants.  
  
 [Mode Remplissage des colonnes dans le contrôle DataGridView Windows Forms](column-fill-mode-in-the-windows-forms-datagridview-control.md)  
 Décrit le mode de remplissage de colonne en détail et fournit un code de démonstration que vous pouvez utiliser pour expérimenter le mode de remplissage de colonne et d’autres modes.  
  
 [Guide pratique pour définir les modes de redimensionnement du contrôle DataGridView Windows Forms](how-to-set-the-sizing-modes-of-the-windows-forms-datagridview-control.md)  
 Décrit comment configurer les modes de dimensionnement à des fins courantes.  
  
 [Guide pratique pour redimensionner des cellules par programme pour les adapter au contenu du contrôle DataGridView Windows Forms](programmatically-resize-cells-to-fit-content-in-the-datagrid.md)  
 Fournit un code de démonstration que vous pouvez utiliser pour expérimenter le redimensionnement par programmation.  
  
 [Guide pratique pour redimensionner automatiquement des cellules lorsque leur contenu change dans le contrôle DataGridView Windows Forms](automatically-resize-cells-when-content-changes-in-the-datagrid.md)  
 Fournit un code de démonstration que vous pouvez utiliser pour expérimenter les modes de dimensionnement automatique.  
  
## <a name="reference"></a>Référence  
 <xref:System.Windows.Forms.DataGridView>  
 Fournit une documentation de référence pour le contrôle <xref:System.Windows.Forms.DataGridView>.  
  
## <a name="see-also"></a>Voir aussi

- [DataGridView, contrôle](datagridview-control-windows-forms.md)
