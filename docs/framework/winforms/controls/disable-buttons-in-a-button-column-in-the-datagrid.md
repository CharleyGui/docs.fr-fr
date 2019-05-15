---
title: 'Procédure : désactiver des boutons dans une colonne de boutons dans le contrôle DataGridView Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], disabling buttons
- buttons [Windows Forms], disabling in button columns
- DataGridView control [Windows Forms], disabling button cells
ms.assetid: 5c344d01-013a-4a6b-8f8d-62ec9321d81e
ms.openlocfilehash: 7d6223e4d75524044e701ea4cf34dcc7487ccd25
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591784"
---
# <a name="how-to-disable-buttons-in-a-button-column-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="67fc8-102">Procédure : désactiver des boutons dans une colonne de boutons dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="67fc8-102">How to: Disable Buttons in a Button Column in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="67fc8-103">Le contrôle <xref:System.Windows.Forms.DataGridView> inclut la classe <xref:System.Windows.Forms.DataGridViewButtonCell> pour l'affichage des cellules avec une interface utilisateur telle qu'un bouton.</span><span class="sxs-lookup"><span data-stu-id="67fc8-103">The <xref:System.Windows.Forms.DataGridView> control includes the <xref:System.Windows.Forms.DataGridViewButtonCell> class for displaying cells with a user interface (UI) like a button.</span></span> <span data-ttu-id="67fc8-104">Toutefois, <xref:System.Windows.Forms.DataGridViewButtonCell> ne permet pas de désactiver l'apparence du bouton affiché par la cellule.</span><span class="sxs-lookup"><span data-stu-id="67fc8-104">However, <xref:System.Windows.Forms.DataGridViewButtonCell> does not provide a way to disable the appearance of the button displayed by the cell.</span></span>  
  
 <span data-ttu-id="67fc8-105">L'exemple de code suivant montre comment personnaliser la classe <xref:System.Windows.Forms.DataGridViewButtonCell> pour afficher des boutons qui peuvent apparaître désactivés.</span><span class="sxs-lookup"><span data-stu-id="67fc8-105">The following code example demonstrates how to customize the <xref:System.Windows.Forms.DataGridViewButtonCell> class to display buttons that can appear disabled.</span></span> <span data-ttu-id="67fc8-106">L'exemple définit un nouveau type de cellule, `DataGridViewDisableButtonCell`, qui dérive de <xref:System.Windows.Forms.DataGridViewButtonCell>.</span><span class="sxs-lookup"><span data-stu-id="67fc8-106">The example defines a new cell type, `DataGridViewDisableButtonCell`, that derives from <xref:System.Windows.Forms.DataGridViewButtonCell>.</span></span> <span data-ttu-id="67fc8-107">Ce type de cellule fournit une nouvelle propriété `Enabled` qui peut prendre la valeur `false` pour dessiner un bouton désactivé dans la cellule.</span><span class="sxs-lookup"><span data-stu-id="67fc8-107">This cell type provides a new `Enabled` property that can be set to `false` to draw a disabled button in the cell.</span></span> <span data-ttu-id="67fc8-108">L'exemple définit également un nouveau type de colonne, `DataGridViewDisableButtonColumn`, qui affiche des objets `DataGridViewDisableButtonCell`.</span><span class="sxs-lookup"><span data-stu-id="67fc8-108">The example also defines a new column type, `DataGridViewDisableButtonColumn`, that displays `DataGridViewDisableButtonCell` objects.</span></span> <span data-ttu-id="67fc8-109">Pour illustrer ce nouveau type de cellule et de colonne, la valeur actuelle de chaque <xref:System.Windows.Forms.DataGridViewCheckBoxCell> dans le <xref:System.Windows.Forms.DataGridView> parent détermine si la propriété  `Enabled` du `DataGridViewDisableButtonCell` sur la même ligne est `true` ou `false`.</span><span class="sxs-lookup"><span data-stu-id="67fc8-109">To demonstrate this new cell and column type, the current value of each <xref:System.Windows.Forms.DataGridViewCheckBoxCell> in the parent <xref:System.Windows.Forms.DataGridView> determines whether the `Enabled` property of the `DataGridViewDisableButtonCell` in the same row is `true` or `false`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="67fc8-110">Quand vous dérivez de <xref:System.Windows.Forms.DataGridViewCell> ou <xref:System.Windows.Forms.DataGridViewColumn> et que vous ajoutez de nouvelles propriétés à la classe dérivée, veillez à substituer la méthode `Clone` pour copier les nouvelles propriétés lors des opérations de clonage.</span><span class="sxs-lookup"><span data-stu-id="67fc8-110">When you derive from <xref:System.Windows.Forms.DataGridViewCell> or <xref:System.Windows.Forms.DataGridViewColumn> and add new properties to the derived class, be sure to override the `Clone` method to copy the new properties during cloning operations.</span></span> <span data-ttu-id="67fc8-111">Vous devez aussi appeler la méthode `Clone` de la classe de base pour que les propriétés de la classe de base soient copiées dans la nouvelle cellule ou colonne.</span><span class="sxs-lookup"><span data-stu-id="67fc8-111">You should also call the base class's `Clone` method so that the properties of the base class are copied to the new cell or column.</span></span>  
  
## <a name="example"></a><span data-ttu-id="67fc8-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="67fc8-112">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridView.DisabledButtons#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DisabledButtons/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.DataGridView.DisabledButtons#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DisabledButtons/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="67fc8-113">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="67fc8-113">Compiling the Code</span></span>  
 <span data-ttu-id="67fc8-114">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="67fc8-114">This example requires:</span></span>  
  
- <span data-ttu-id="67fc8-115">Références aux assemblys System, System.Drawing, System.Windows.Forms et System.Windows.Forms.VisualStyles.</span><span class="sxs-lookup"><span data-stu-id="67fc8-115">References to the System, System.Drawing, System.Windows.Forms and System.Windows.Forms.VisualStyles assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67fc8-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="67fc8-116">See also</span></span>

- [<span data-ttu-id="67fc8-117">Personnalisation du contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="67fc8-117">Customizing the Windows Forms DataGridView Control</span></span>](customizing-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="67fc8-118">Architecture du contrôle DataGridView</span><span class="sxs-lookup"><span data-stu-id="67fc8-118">DataGridView Control Architecture</span></span>](datagridview-control-architecture-windows-forms.md)
- [<span data-ttu-id="67fc8-119">Types de colonnes dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="67fc8-119">Column Types in the Windows Forms DataGridView Control</span></span>](column-types-in-the-windows-forms-datagridview-control.md)
