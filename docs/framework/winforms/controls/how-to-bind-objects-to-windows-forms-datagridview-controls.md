---
title: 'Procédure : lier des objets à des contrôles DataGridView Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], object binding
- data grids [Windows Forms], object binding
- object binding [Windows Forms], DataGridView control
ms.assetid: cb8f29fa-577e-4e2b-883f-3a01c6189b9c
ms.openlocfilehash: 8cdfd5d8e5ec3dcd22abb9e4efcec3bb61fee1d9
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591321"
---
# <a name="how-to-bind-objects-to-windows-forms-datagridview-controls"></a>Procédure : lier des objets à des contrôles DataGridView Windows Forms
L'exemple de code suivant montre comment lier une collection d'objets à un contrôle <xref:System.Windows.Forms.DataGridView> pour que chaque objet soit affichée sur une ligne distincte. Cet exemple illustre également comment afficher une propriété avec un type énumération dans un <xref:System.Windows.Forms.DataGridViewComboBoxColumn> pour que la zone de liste déroulante modifiable contienne les valeurs d'énumération.  
  
## <a name="example"></a>Exemple  
 [!code-csharp[System.Windows.Forms.DataGridView._CollectionBound#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView._CollectionBound/CS/collectionbound.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridView._CollectionBound#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView._CollectionBound/VB/collectionbound.vb#00)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
- des références aux assemblys System et System.Windows.Forms ;  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.DataGridView>
- [Affichage des données dans le contrôle DataGridView Windows Forms](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Guide pratique pour Accéder aux objets liés à des Windows Forms DataGridView lignes](how-to-access-objects-bound-to-windows-forms-datagridview-rows.md)
