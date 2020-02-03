---
title: Sélectionner un élément dans le contrôle ListView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lists [Windows Forms], selecting items
- ListView control [Windows Forms], selecting items
- selection [Windows Forms], in list views
- list views [Windows Forms], selecting items
ms.assetid: ddea918e-1ddf-47f4-bd09-1e9b4c9d0c39
ms.openlocfilehash: 57e985af9d0347510d7d7782f68d5b414d36e077
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743233"
---
# <a name="how-to-select-an-item-in-the-windows-forms-listview-control"></a>Comment : sélectionner un élément dans le contrôle ListView Windows Forms
Cet exemple montre comment sélectionner par programmation un élément dans un contrôle Windows Forms <xref:System.Windows.Forms.ListView>. La sélection d’un élément par programme ne change pas automatiquement le focus en contrôle de <xref:System.Windows.Forms.ListView>. Pour cette raison, vous souhaiterez généralement également définir l’élément comme ayant le focus lors de la sélection d’un élément.  
  
## <a name="example"></a>Exemple  
 [!code-csharp[System.Windows.Forms.ListView.Misc#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Misc/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.Misc#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.Misc/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
- Un contrôle <xref:System.Windows.Forms.ListView> nommé `listView1` qui contient au moins un élément.  
  
- Références aux espaces de noms <xref:System?displayProperty=nameWithType> et <xref:System.Windows.Forms?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListViewItem.Selected%2A?displayProperty=nameWithType>
