---
title: Afficher une marque d’insertion dans le contrôle ListView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ListView control [Windows Forms], drag operations
- graphics [Windows Forms], insertion marks
- drop and drag [Windows Forms], insertion marks
- insertion marks
ms.assetid: 88d0a15b-25fd-4dc3-a685-297351311940
ms.openlocfilehash: eeae51223a21baaf4d2412de2ce11d0c6cbcae27
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742221"
---
# <a name="how-to-display-an-insertion-mark-in-a-windows-forms-listview-control"></a>Comment : afficher une marque d'insertion dans un contrôle ListView Windows Forms
La marque d'insertion dans le contrôle <xref:System.Windows.Forms.ListView> indique aux utilisateurs l'emplacement où les éléments déplacés seront insérés. Quand un utilisateur fait glisser un élément vers un point entre deux autres éléments, la marque d'insertion indique le nouvel emplacement prévu de l'élément.  
  
 L'illustration suivante montre une marque d'insertion :  
  
 ![Capture d’écran montrant une marque d’insertion ListView.](./media/how-to-display-an-insertion-mark-in-a-windows-forms-listview-control/listview-insertion-mark.gif "ListViewInsertion")  
  
 L’exemple de code suivant montre comment utiliser cette fonctionnalité.  
  
## <a name="example"></a>Exemple  
 [!code-cpp[System.Windows.Forms.ListView.InsertionMark#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/CPP/listviewinsertionmarkexample.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListView.InsertionMark#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/CS/listviewinsertionmarkexample.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.InsertionMark#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/VB/listviewinsertionmarkexample.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
- des références aux assemblys System et System.Windows.Forms.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.InsertionMark%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ListViewInsertionMark>
- [Contrôle ListView](listview-control-windows-forms.md)
- [Vue d’ensemble du contrôle ListView](listview-control-overview-windows-forms.md)
- [Procédure pas à pas : exécution d’opérations de glisser-déposer dans Windows Forms](../advanced/walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md)
