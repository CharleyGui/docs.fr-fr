---
title: Personnaliser l’apparence des lignes dans le contrôle DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], customizing rows
- rows [Windows Forms], customizing in DataGridView control
- DataGridView control [Windows Forms], customizing rows
ms.assetid: d40b53d2-7e7c-48c5-8570-6e79d15c3bbb
ms.openlocfilehash: 099b2104e7a4887aa846c4d65273db2dd4f60559
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744038"
---
# <a name="how-to-customize-the-appearance-of-rows-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="4c275-102">Comment : personnaliser l'apparence des lignes du contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4c275-102">How to: Customize the Appearance of Rows in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="4c275-103">Vous pouvez contrôler l'apparence des lignes <xref:System.Windows.Forms.DataGridView> en gérant l'un ou l'autre des événements <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> et <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType> (ou les deux).</span><span class="sxs-lookup"><span data-stu-id="4c275-103">You can control the appearance of <xref:System.Windows.Forms.DataGridView> rows by handling one or both of the <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> and <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType> events.</span></span> <span data-ttu-id="4c275-104">Ces événements sont conçus pour que vous puissiez peindre uniquement ce que vous souhaitez, tout en laissant le contrôle <xref:System.Windows.Forms.DataGridView> peindre le reste.</span><span class="sxs-lookup"><span data-stu-id="4c275-104">These events are designed so that you can paint only what you want to while letting the <xref:System.Windows.Forms.DataGridView> control paint the rest.</span></span> <span data-ttu-id="4c275-105">Par exemple, si vous souhaitez peindre un arrière-plan personnalisé, vous pouvez gérer l'événement <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> et laisser chaque cellule peindre son propre contenu de premier plan.</span><span class="sxs-lookup"><span data-stu-id="4c275-105">For example, if you want to paint a custom background, you can handle the <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> event and let the individual cells paint their own foreground content.</span></span> <span data-ttu-id="4c275-106">Vous pouvez également laisser les cellules se peindre elles-mêmes et ajouter du contenu de premier plan personnalisé dans un gestionnaire pour l'événement <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4c275-106">Alternately, you can let the cells paint themselves and add custom foreground content in a handler for the <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType> event.</span></span> <span data-ttu-id="4c275-107">Vous pouvez aussi désactiver la peinture des cellules et peindre tout vous-même dans un gestionnaire d'événements <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4c275-107">You can also disable cell painting and paint everything yourself in a <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> event handler.</span></span>  
  
 <span data-ttu-id="4c275-108">L'exemple de code suivant implémente des gestionnaires pour les deux événements pour fournir un arrière-plan de sélection dégradé et du contenu de premier plan personnalisé qui s'étend sur plusieurs colonnes.</span><span class="sxs-lookup"><span data-stu-id="4c275-108">The following code example implements handlers for both events in order to provide a gradient selection background and some custom foreground content that spans multiple columns.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4c275-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="4c275-109">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewRowPainting#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRowPainting/CS/datagridviewrowpainting.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewRowPainting#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRowPainting/VB/datagridviewrowpainting.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4c275-110">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="4c275-110">Compiling the Code</span></span>  
 <span data-ttu-id="4c275-111">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="4c275-111">This example requires:</span></span>  
  
- <span data-ttu-id="4c275-112">Références aux assemblys System, System.Drawing et System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="4c275-112">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c275-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4c275-113">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType>
- [<span data-ttu-id="4c275-114">Personnalisation du contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4c275-114">Customizing the Windows Forms DataGridView Control</span></span>](customizing-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="4c275-115">Architecture du contrôle DataGridView</span><span class="sxs-lookup"><span data-stu-id="4c275-115">DataGridView Control Architecture</span></span>](datagridview-control-architecture-windows-forms.md)
