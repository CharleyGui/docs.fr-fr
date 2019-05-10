---
title: 'Procédure : sélectionner un élément dans le contrôle ListView Windows Forms'
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
ms.openlocfilehash: 41a30ba6c242d0587e98b458e41ca213e8885bca
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64638201"
---
# <a name="how-to-select-an-item-in-the-windows-forms-listview-control"></a>Procédure : sélectionner un élément dans le contrôle ListView Windows Forms
Cet exemple montre comment sélectionner par programme un élément dans un formulaire Windows <xref:System.Windows.Forms.ListView> contrôle. Sélection d’un élément par programme ne change pas automatiquement le focus à la <xref:System.Windows.Forms.ListView> contrôle. Pour cette raison, vous également souhaitez généralement définir l’élément comme ayant le focus lors de la sélection d’un élément.  
  
## <a name="example"></a>Exemple  
 [!code-csharp[System.Windows.Forms.ListView.Misc#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Misc/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.Misc#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.Misc/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
- Un <xref:System.Windows.Forms.ListView> contrôle nommé `listView1` qui contient au moins un élément.  
  
- Références aux espaces de noms <xref:System?displayProperty=nameWithType> et <xref:System.Windows.Forms?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListViewItem.Selected%2A?displayProperty=nameWithType>
