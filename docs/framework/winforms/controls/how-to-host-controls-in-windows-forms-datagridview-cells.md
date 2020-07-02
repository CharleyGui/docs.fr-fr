---
title: Contrôles hôtes dans les cellules DataGridView
description: Découvrez comment héberger des contrôles dans Windows Forms des cellules DataGridView pour permettre à vos utilisateurs d’entrer et de modifier des valeurs de différentes façons.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], hosting in cells
- DataGridView control [Windows Forms], hosting controls in cells
- cells [Windows Forms], hosting controls
ms.assetid: e79a9d4e-64ec-41f5-93ec-f5492633cbb2
ms.openlocfilehash: 87901cbf86689bec49f5692feeabdae79f6b93ba
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619544"
---
# <a name="how-to-host-controls-in-windows-forms-datagridview-cells"></a><span data-ttu-id="1f1ef-103">Comment : héberger des contrôles dans des cellules DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1f1ef-103">How to: Host Controls in Windows Forms DataGridView Cells</span></span>
<span data-ttu-id="1f1ef-104">Le contrôle <xref:System.Windows.Forms.DataGridView> fournit plusieurs types de colonnes, ce qui permet à vos utilisateurs d'entrer et de modifier des valeurs de plusieurs façons.</span><span class="sxs-lookup"><span data-stu-id="1f1ef-104">The <xref:System.Windows.Forms.DataGridView> control provides several column types, enabling your users to enter and edit values in a variety of ways.</span></span> <span data-ttu-id="1f1ef-105">Toutefois, si ces types de colonnes ne répondent pas à vos besoins de saisie de données, vous pouvez créer vos propres types de colonnes avec des cellules qui hébergent les contrôles de votre choix.</span><span class="sxs-lookup"><span data-stu-id="1f1ef-105">If these column types do not meet your data-entry needs, however, you can create your own column types with cells that host controls of your choosing.</span></span> <span data-ttu-id="1f1ef-106">Pour cela, vous devez définir des classes qui dérivent de <xref:System.Windows.Forms.DataGridViewColumn> et <xref:System.Windows.Forms.DataGridViewCell>.</span><span class="sxs-lookup"><span data-stu-id="1f1ef-106">To do this, you must define classes that derive from <xref:System.Windows.Forms.DataGridViewColumn> and <xref:System.Windows.Forms.DataGridViewCell>.</span></span> <span data-ttu-id="1f1ef-107">Vous devez aussi définir une classe qui dérive de <xref:System.Windows.Forms.Control> et implémente l'interface <xref:System.Windows.Forms.IDataGridViewEditingControl>.</span><span class="sxs-lookup"><span data-stu-id="1f1ef-107">You must also define a class that derives from <xref:System.Windows.Forms.Control> and implements the <xref:System.Windows.Forms.IDataGridViewEditingControl> interface.</span></span>  
  
 <span data-ttu-id="1f1ef-108">L'exemple de code suivant montre comment créer une colonne de calendrier.</span><span class="sxs-lookup"><span data-stu-id="1f1ef-108">The following code example shows how to create a calendar column.</span></span> <span data-ttu-id="1f1ef-109">Les cellules de cette colonne affichent des dates dans des cellules de zone de texte ordinaires, mais quand l'utilisateur modifie une cellule, un contrôle <xref:System.Windows.Forms.DateTimePicker> apparaît.</span><span class="sxs-lookup"><span data-stu-id="1f1ef-109">The cells of this column display dates in ordinary text box cells, but when the user edits a cell, a <xref:System.Windows.Forms.DateTimePicker> control appears.</span></span> <span data-ttu-id="1f1ef-110">Pour éviter de devoir réimplémenter une fonctionnalité d'affichage de zone de texte, la classe `CalendarCell` dérive de la classe <xref:System.Windows.Forms.DataGridViewTextBoxCell> au lieu d'hériter directement de la classe <xref:System.Windows.Forms.DataGridViewCell>.</span><span class="sxs-lookup"><span data-stu-id="1f1ef-110">In order to avoid having to implement text box display functionality again, the `CalendarCell` class derives from the <xref:System.Windows.Forms.DataGridViewTextBoxCell> class rather than inheriting the <xref:System.Windows.Forms.DataGridViewCell> class directly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1f1ef-111">Quand vous dérivez de <xref:System.Windows.Forms.DataGridViewCell> ou <xref:System.Windows.Forms.DataGridViewColumn> et que vous ajoutez de nouvelles propriétés à la classe dérivée, veillez à substituer la méthode `Clone` pour copier les nouvelles propriétés lors des opérations de clonage.</span><span class="sxs-lookup"><span data-stu-id="1f1ef-111">When you derive from <xref:System.Windows.Forms.DataGridViewCell> or <xref:System.Windows.Forms.DataGridViewColumn> and add new properties to the derived class, be sure to override the `Clone` method to copy the new properties during cloning operations.</span></span> <span data-ttu-id="1f1ef-112">Vous devez aussi appeler la méthode `Clone` de la classe de base pour que les propriétés de la classe de base soient copiées dans la nouvelle cellule ou colonne.</span><span class="sxs-lookup"><span data-stu-id="1f1ef-112">You should also call the base class's `Clone` method so that the properties of the base class are copied to the new cell or column.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1f1ef-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="1f1ef-113">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewCalendarColumn#000](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCalendarColumn/CS/datagridviewcalendarcolumn.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewCalendarColumn#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCalendarColumn/VB/datagridviewcalendarcolumn.vb#000)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1f1ef-114">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="1f1ef-114">Compiling the Code</span></span>  
 <span data-ttu-id="1f1ef-115">L'exemple suivant nécessite :</span><span class="sxs-lookup"><span data-stu-id="1f1ef-115">The following example requires:</span></span>  
  
- <span data-ttu-id="1f1ef-116">des références aux assemblys System et System.Windows.Forms ;</span><span class="sxs-lookup"><span data-stu-id="1f1ef-116">References to the System and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f1ef-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1f1ef-117">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn>
- <xref:System.Windows.Forms.DataGridViewCell>
- <xref:System.Windows.Forms.DataGridViewTextBoxCell>
- <xref:System.Windows.Forms.IDataGridViewEditingControl>
- <xref:System.Windows.Forms.DateTimePicker>
- [<span data-ttu-id="1f1ef-118">Personnalisation du contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1f1ef-118">Customizing the Windows Forms DataGridView Control</span></span>](customizing-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="1f1ef-119">Architecture du contrôle DataGridView</span><span class="sxs-lookup"><span data-stu-id="1f1ef-119">DataGridView Control Architecture</span></span>](datagridview-control-architecture-windows-forms.md)
- [<span data-ttu-id="1f1ef-120">Types de colonnes dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1f1ef-120">Column Types in the Windows Forms DataGridView Control</span></span>](column-types-in-the-windows-forms-datagridview-control.md)
