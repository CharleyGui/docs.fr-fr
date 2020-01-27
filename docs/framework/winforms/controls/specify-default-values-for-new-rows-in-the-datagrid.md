---
title: Spécifier des valeurs par défaut pour les nouvelles lignes dans le contrôle DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], default values for new rows
- DataGridView control [Windows Forms], data entry
- rows [Windows Forms], specifying default values
- DataGridView control [Windows Forms], default values for new rows
ms.assetid: 8d127963-d9f8-4e4e-9f7f-beb66688f1f2
ms.openlocfilehash: 364f922aefc10e57f2ed7f3a0c2a5b25c922d87a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742934"
---
# <a name="how-to-specify-default-values-for-new-rows-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="f39b3-102">Comment : spécifier des valeurs par défaut pour les nouvelles lignes dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f39b3-102">How to: Specify Default Values for New Rows in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="f39b3-103">Vous pouvez rendre l’entrée de données plus pratique lorsque l’application remplit les valeurs par défaut pour les nouvelles lignes ajoutées.</span><span class="sxs-lookup"><span data-stu-id="f39b3-103">You can make data entry more convenient when the application fills in default values for newly added rows.</span></span> <span data-ttu-id="f39b3-104">Avec la classe <xref:System.Windows.Forms.DataGridView>, vous pouvez remplir les valeurs par défaut avec l’événement <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded>.</span><span class="sxs-lookup"><span data-stu-id="f39b3-104">With the <xref:System.Windows.Forms.DataGridView> class, you can fill in default values with the <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> event.</span></span> <span data-ttu-id="f39b3-105">Cet événement est déclenché lorsque l’utilisateur entre la ligne pour les nouveaux enregistrements.</span><span class="sxs-lookup"><span data-stu-id="f39b3-105">This event is raised when the user enters the row for new records.</span></span> <span data-ttu-id="f39b3-106">Lorsque votre code gère cet événement, vous pouvez remplir les cellules souhaitées avec les valeurs de votre choix.</span><span class="sxs-lookup"><span data-stu-id="f39b3-106">When your code handles this event, you can populate desired cells with values of your choosing.</span></span>  
  
 <span data-ttu-id="f39b3-107">L’exemple de code suivant montre comment spécifier des valeurs par défaut pour les nouvelles lignes à l’aide de l’événement <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded>.</span><span class="sxs-lookup"><span data-stu-id="f39b3-107">The following code example demonstrates how to specify default values for new rows using the <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f39b3-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="f39b3-108">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#120)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#120)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f39b3-109">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="f39b3-109">Compiling the Code</span></span>  
 <span data-ttu-id="f39b3-110">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="f39b3-110">This example requires:</span></span>  
  
- <span data-ttu-id="f39b3-111">un contrôle <xref:System.Windows.Forms.DataGridView> nommé `dataGridView1` ;</span><span class="sxs-lookup"><span data-stu-id="f39b3-111">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="f39b3-112">Fonction `NewCustomerId` pour générer des valeurs de `CustomerID` uniques.</span><span class="sxs-lookup"><span data-stu-id="f39b3-112">A `NewCustomerId` function for generating unique `CustomerID` values.</span></span>  
  
- <span data-ttu-id="f39b3-113">des références aux assemblys <xref:System?displayProperty=nameWithType> et <xref:System.Windows.Forms?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f39b3-113">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f39b3-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f39b3-114">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded?displayProperty=nameWithType>
- [<span data-ttu-id="f39b3-115">Saisie de données dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f39b3-115">Data Entry in the Windows Forms DataGridView Control</span></span>](data-entry-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="f39b3-116">Utilisation de la ligne pour les nouveaux enregistrements dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f39b3-116">Using the Row for New Records in the Windows Forms DataGridView Control</span></span>](using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)
