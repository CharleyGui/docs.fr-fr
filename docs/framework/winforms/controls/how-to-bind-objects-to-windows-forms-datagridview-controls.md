---
title: lier des objets à des contrôles DataGridView
description: Apprenez à lier une collection d’objets à un Windows Forms contrôle DataGridView afin que chaque objet s’affiche sous la forme d’une ligne distincte.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], object binding
- data grids [Windows Forms], object binding
- object binding [Windows Forms], DataGridView control
ms.assetid: cb8f29fa-577e-4e2b-883f-3a01c6189b9c
ms.openlocfilehash: add0047937b404dcec1ea12bac8053bb9bdfcf1c
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325855"
---
# <a name="how-to-bind-objects-to-windows-forms-datagridview-controls"></a><span data-ttu-id="2a265-103">Comment : lier des objets aux contrôles DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2a265-103">How to: Bind Objects to Windows Forms DataGridView Controls</span></span>
<span data-ttu-id="2a265-104">L'exemple de code suivant montre comment lier une collection d'objets à un contrôle <xref:System.Windows.Forms.DataGridView> pour que chaque objet soit affichée sur une ligne distincte.</span><span class="sxs-lookup"><span data-stu-id="2a265-104">The following code example demonstrates how to bind a collection of objects to a <xref:System.Windows.Forms.DataGridView> control so that each object displays as a separate row.</span></span> <span data-ttu-id="2a265-105">Cet exemple illustre également comment afficher une propriété avec un type énumération dans un <xref:System.Windows.Forms.DataGridViewComboBoxColumn> pour que la zone de liste déroulante modifiable contienne les valeurs d'énumération.</span><span class="sxs-lookup"><span data-stu-id="2a265-105">This example also illustrates how to display a property with an enumeration type in a <xref:System.Windows.Forms.DataGridViewComboBoxColumn> so that the combo box drop-down list contains the enumeration values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2a265-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="2a265-106">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridView._CollectionBound#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView._CollectionBound/CS/collectionbound.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridView._CollectionBound#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView._CollectionBound/VB/collectionbound.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2a265-107">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="2a265-107">Compiling the Code</span></span>  
 <span data-ttu-id="2a265-108">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="2a265-108">This example requires:</span></span>  
  
- <span data-ttu-id="2a265-109">des références aux assemblys System et System.Windows.Forms ;</span><span class="sxs-lookup"><span data-stu-id="2a265-109">References to the System and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a265-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2a265-110">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="2a265-111">Affichage des données dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2a265-111">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="2a265-112">Comment : accéder à des objets liés à des lignes DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2a265-112">How to: Access Objects Bound to Windows Forms DataGridView Rows</span></span>](how-to-access-objects-bound-to-windows-forms-datagridview-rows.md)
