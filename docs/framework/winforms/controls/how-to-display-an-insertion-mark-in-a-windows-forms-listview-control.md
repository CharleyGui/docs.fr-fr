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
# <a name="how-to-display-an-insertion-mark-in-a-windows-forms-listview-control"></a><span data-ttu-id="88bb2-102">Comment : afficher une marque d'insertion dans un contrôle ListView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="88bb2-102">How to: Display an Insertion Mark in a Windows Forms ListView Control</span></span>
<span data-ttu-id="88bb2-103">La marque d'insertion dans le contrôle <xref:System.Windows.Forms.ListView> indique aux utilisateurs l'emplacement où les éléments déplacés seront insérés.</span><span class="sxs-lookup"><span data-stu-id="88bb2-103">The insertion mark in the <xref:System.Windows.Forms.ListView> control shows users the point where dragged items will be inserted.</span></span> <span data-ttu-id="88bb2-104">Quand un utilisateur fait glisser un élément vers un point entre deux autres éléments, la marque d'insertion indique le nouvel emplacement prévu de l'élément.</span><span class="sxs-lookup"><span data-stu-id="88bb2-104">When a user drags an item to a point between two other items, the insertion mark shows the item's expected new location.</span></span>  
  
 <span data-ttu-id="88bb2-105">L'illustration suivante montre une marque d'insertion :</span><span class="sxs-lookup"><span data-stu-id="88bb2-105">The following image shows an insertion mark:</span></span>  
  
 <span data-ttu-id="88bb2-106">![Capture d’écran montrant une marque d’insertion ListView.](./media/how-to-display-an-insertion-mark-in-a-windows-forms-listview-control/listview-insertion-mark.gif "ListViewInsertion")</span><span class="sxs-lookup"><span data-stu-id="88bb2-106">![Screenshot that shows a ListView insertion mark.](./media/how-to-display-an-insertion-mark-in-a-windows-forms-listview-control/listview-insertion-mark.gif "ListViewInsertion")</span></span>  
  
 <span data-ttu-id="88bb2-107">L’exemple de code suivant montre comment utiliser cette fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="88bb2-107">The following code example demonstrates how to use this feature.</span></span>  
  
## <a name="example"></a><span data-ttu-id="88bb2-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="88bb2-108">Example</span></span>  
 [!code-cpp[System.Windows.Forms.ListView.InsertionMark#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/CPP/listviewinsertionmarkexample.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListView.InsertionMark#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/CS/listviewinsertionmarkexample.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.InsertionMark#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/VB/listviewinsertionmarkexample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="88bb2-109">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="88bb2-109">Compiling the Code</span></span>  
 <span data-ttu-id="88bb2-110">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="88bb2-110">This example requires:</span></span>  
  
- <span data-ttu-id="88bb2-111">des références aux assemblys System et System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="88bb2-111">References to the System and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88bb2-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="88bb2-112">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.InsertionMark%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ListViewInsertionMark>
- [<span data-ttu-id="88bb2-113">Contrôle ListView</span><span class="sxs-lookup"><span data-stu-id="88bb2-113">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="88bb2-114">Vue d’ensemble du contrôle ListView</span><span class="sxs-lookup"><span data-stu-id="88bb2-114">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
- [<span data-ttu-id="88bb2-115">Procédure pas à pas : exécution d’opérations de glisser-déposer dans Windows Forms</span><span class="sxs-lookup"><span data-stu-id="88bb2-115">Walkthrough: Performing a Drag-and-Drop Operation in Windows Forms</span></span>](../advanced/walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md)
