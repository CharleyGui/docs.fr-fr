---
title: Ajouter des colonnes au contrôle ListView
description: Découvrez comment ajouter des colonnes au contrôle ListView Windows Forms pour afficher plusieurs types d’informations sur chaque élément de liste.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView control [Windows Forms], adding column headers
- columns [Windows Forms], adding to ListView controls
- list views [Windows Forms], adding columns
ms.assetid: 79174274-12ee-4a5d-80db-6ec02976d010
ms.openlocfilehash: 7ca4e86ca3a9679876f2525c49596534f175096a
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174560"
---
# <a name="how-to-add-columns-to-the-windows-forms-listview-control"></a>Comment : ajouter des colonnes au contrôle ListView Windows Forms
Dans le mode Détails, le <xref:System.Windows.Forms.ListView> contrôle peut afficher plusieurs colonnes pour chaque élément de liste. Vous pouvez utiliser les colonnes pour afficher à l’utilisateur plusieurs types d’informations sur chaque élément de liste. Par exemple, une liste de fichiers peut afficher le nom du fichier, le type de fichier, la taille et la date de la dernière modification du fichier. Pour plus d’informations sur le remplissage des colonnes après leur création, consultez [Comment : afficher des sous-éléments dans des colonnes avec le contrôle ListView Windows Forms](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md).  
  
### <a name="to-add-columns-programmatically"></a>Pour ajouter des colonnes par programmation  
  
1. Affectez à la propriété du contrôle la valeur <xref:System.Windows.Forms.ListView.View%2A> <xref:System.Windows.Forms.View.Details> .  
  
2. Utilisez la <xref:System.Windows.Forms.ListView.ColumnHeaderCollection.Add%2A> méthode de la propriété de la vue liste <xref:System.Windows.Forms.ListView.Columns%2A> .  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#31)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#31)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.ListView>
- [Contrôle ListView](listview-control-windows-forms.md)
- [Vue d'ensemble du contrôle ListView](listview-control-overview-windows-forms.md)
