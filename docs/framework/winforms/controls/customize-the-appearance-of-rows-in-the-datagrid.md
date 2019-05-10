---
title: 'Procédure : personnaliser l’aspect des lignes dans le contrôle DataGridView Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], customizing rows
- rows [Windows Forms], customizing in DataGridView control
- DataGridView control [Windows Forms], customizing rows
ms.assetid: d40b53d2-7e7c-48c5-8570-6e79d15c3bbb
ms.openlocfilehash: 32a21705b553ec915b4510dbe2fa32a0ae097d96
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64648158"
---
# <a name="how-to-customize-the-appearance-of-rows-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="418cd-102">Procédure : personnaliser l’aspect des lignes dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="418cd-102">How to: Customize the Appearance of Rows in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="418cd-103">Vous pouvez contrôler l'apparence des lignes <xref:System.Windows.Forms.DataGridView> en gérant l'un ou l'autre des événements <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> et <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType> (ou les deux).</span><span class="sxs-lookup"><span data-stu-id="418cd-103">You can control the appearance of <xref:System.Windows.Forms.DataGridView> rows by handling one or both of the <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> and <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType> events.</span></span> <span data-ttu-id="418cd-104">Ces événements sont conçus pour que vous puissiez peindre uniquement ce que vous souhaitez, tout en laissant le contrôle <xref:System.Windows.Forms.DataGridView> peindre le reste.</span><span class="sxs-lookup"><span data-stu-id="418cd-104">These events are designed so that you can paint only what you want to while letting the <xref:System.Windows.Forms.DataGridView> control paint the rest.</span></span> <span data-ttu-id="418cd-105">Par exemple, si vous souhaitez peindre un arrière-plan personnalisé, vous pouvez gérer l'événement <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> et laisser chaque cellule peindre son propre contenu de premier plan.</span><span class="sxs-lookup"><span data-stu-id="418cd-105">For example, if you want to paint a custom background, you can handle the <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> event and let the individual cells paint their own foreground content.</span></span> <span data-ttu-id="418cd-106">Vous pouvez également laisser les cellules se peindre elles-mêmes et ajouter du contenu de premier plan personnalisé dans un gestionnaire pour l'événement <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="418cd-106">Alternately, you can let the cells paint themselves and add custom foreground content in a handler for the <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType> event.</span></span> <span data-ttu-id="418cd-107">Vous pouvez aussi désactiver la peinture des cellules et peindre tout vous-même dans un gestionnaire d'événements <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="418cd-107">You can also disable cell painting and paint everything yourself in a <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> event handler.</span></span>  
  
 <span data-ttu-id="418cd-108">L'exemple de code suivant implémente des gestionnaires pour les deux événements pour fournir un arrière-plan de sélection dégradé et du contenu de premier plan personnalisé qui s'étend sur plusieurs colonnes.</span><span class="sxs-lookup"><span data-stu-id="418cd-108">The following code example implements handlers for both events in order to provide a gradient selection background and some custom foreground content that spans multiple columns.</span></span>  
  
## <a name="example"></a><span data-ttu-id="418cd-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="418cd-109">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewRowPainting#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRowPainting/CS/datagridviewrowpainting.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewRowPainting#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRowPainting/VB/datagridviewrowpainting.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="418cd-110">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="418cd-110">Compiling the Code</span></span>  
 <span data-ttu-id="418cd-111">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="418cd-111">This example requires:</span></span>  
  
- <span data-ttu-id="418cd-112">Références aux assemblys System, System.Drawing et System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="418cd-112">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="418cd-113">Pour plus d’informations sur la création de cet exemple à partir de la ligne de commande pour Visual Basic ou Visual c#, consultez [génération à partir de la ligne de commande](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [de ligne de commande avec csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="418cd-113">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="418cd-114">Vous pouvez également créer cet exemple dans Visual Studio en collant le code dans un nouveau projet.</span><span class="sxs-lookup"><span data-stu-id="418cd-114">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  

## <a name="see-also"></a><span data-ttu-id="418cd-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="418cd-115">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType>
- [<span data-ttu-id="418cd-116">Personnalisation du contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="418cd-116">Customizing the Windows Forms DataGridView Control</span></span>](customizing-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="418cd-117">Architecture du contrôle DataGridView</span><span class="sxs-lookup"><span data-stu-id="418cd-117">DataGridView Control Architecture</span></span>](datagridview-control-architecture-windows-forms.md)
