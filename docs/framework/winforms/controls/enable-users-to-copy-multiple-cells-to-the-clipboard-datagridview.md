---
title: 'Procédure : permettre aux utilisateurs de copier plusieurs cellules dans le Presse-papiers à partir du contrôle DataGridView Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cells [Windows Forms], copying to Clipboard
- DataGridView control [Windows Forms], copying multiple cells
- data grids [Windows Forms], copying multiple cells
- Clipboard [Windows Forms], copying multiple cells
ms.assetid: fd0403b2-d0e3-4ae0-839c-0f737e1eb4a9
ms.openlocfilehash: f6ff6abe5587c89d2102e2d40cc982f3a7fea5a3
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64651787"
---
# <a name="how-to-enable-users-to-copy-multiple-cells-to-the-clipboard-from-the-windows-forms-datagridview-control"></a><span data-ttu-id="5d5c6-102">Procédure : permettre aux utilisateurs de copier plusieurs cellules dans le Presse-papiers à partir du contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5d5c6-102">How to: Enable Users to Copy Multiple Cells to the Clipboard from the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="5d5c6-103">Quand vous activez la copie des cellules, vous rendez les données de votre contrôle <xref:System.Windows.Forms.DataGridView> facilement accessibles à d'autres applications via le <xref:System.Windows.Forms.Clipboard>.</span><span class="sxs-lookup"><span data-stu-id="5d5c6-103">When you enable cell copying, you make the data in your <xref:System.Windows.Forms.DataGridView> control easily accessible to other applications through the <xref:System.Windows.Forms.Clipboard>.</span></span> <span data-ttu-id="5d5c6-104">Les valeurs des cellules sélectionnées sont converties en chaînes et ajoutées au Presse-papiers sous forme de texte délimité par des tabulations en vue d'être collées dans des applications, telles que le Bloc-notes et Excel, et sous forme d'un tableau au format HTML en vue d'être collées dans des applications telles que Word.</span><span class="sxs-lookup"><span data-stu-id="5d5c6-104">The values of the selected cells are converted to strings and added to the Clipboard as tab-delimited text values for pasting into applications like Notepad and Excel, and as an HTML-formatted table for pasting into applications like Word.</span></span>  
  
 <span data-ttu-id="5d5c6-105">Vous pouvez configurer la copie de cellules pour copier uniquement les valeurs des cellules, pour inclure le texte des en-têtes de ligne et de colonne dans les données du Presse-papiers ou pour inclure le texte des en-têtes uniquement quand les utilisateurs sélectionnent des lignes et des colonnes entières.</span><span class="sxs-lookup"><span data-stu-id="5d5c6-105">You can configure cell copying to copy cell values only, to include row and column header text in the Clipboard data, or to include header text only when users select entire rows or columns.</span></span>  
  
 <span data-ttu-id="5d5c6-106">Selon le mode de sélection, les utilisateurs peuvent sélectionner plusieurs groupes de cellules non connectés.</span><span class="sxs-lookup"><span data-stu-id="5d5c6-106">Depending on the selection mode, users can select multiple disconnected groups of cells.</span></span> <span data-ttu-id="5d5c6-107">Quand un utilisateur copie des cellules dans le Presse-papiers, les lignes et les colonnes qui ne contiennent pas de cellules sélectionnées ne sont pas copiées.</span><span class="sxs-lookup"><span data-stu-id="5d5c6-107">When a user copies cells to the Clipboard, rows and columns with no selected cells are not copied.</span></span> <span data-ttu-id="5d5c6-108">Toutes les autres lignes ou colonnes deviennent des lignes et des colonnes de la table de données copiée dans le Presse-papiers.</span><span class="sxs-lookup"><span data-stu-id="5d5c6-108">All other rows or columns become rows and columns in the table of data copied to the Clipboard.</span></span> <span data-ttu-id="5d5c6-109">Les cellules non sélectionnées de ces lignes ou colonnes sont copiées comme des espaces réservés dans le Presse-papiers.</span><span class="sxs-lookup"><span data-stu-id="5d5c6-109">Unselected cells in these rows or columns are copied as blank placeholders to the Clipboard.</span></span>  
  
### <a name="to-enable-cell-copying"></a><span data-ttu-id="5d5c6-110">Pour activer la copie de cellule</span><span class="sxs-lookup"><span data-stu-id="5d5c6-110">To enable cell copying</span></span>  
  
- <span data-ttu-id="5d5c6-111">définir la propriété <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A?displayProperty=nameWithType> ;</span><span class="sxs-lookup"><span data-stu-id="5d5c6-111">Set the <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A?displayProperty=nameWithType> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewClipboardDemo#15](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewClipboardDemo/CS/datagridviewclipboarddemo.cs#15)]
     [!code-vb[System.Windows.Forms.DataGridViewClipboardDemo#15](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewClipboardDemo/VB/datagridviewclipboarddemo.vb#15)]  
  
## <a name="example"></a><span data-ttu-id="5d5c6-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="5d5c6-112">Example</span></span>  
 <span data-ttu-id="5d5c6-113">L'exemple de code complet suivant montre comment les cellules sont copiées vers le Presse-papiers.</span><span class="sxs-lookup"><span data-stu-id="5d5c6-113">The following complete code example demonstrates how cells are copied to the Clipboard.</span></span> <span data-ttu-id="5d5c6-114">Cet exemple inclut un bouton qui copie les cellules sélectionnées dans le Presse-papiers à l'aide de la méthode <xref:System.Windows.Forms.DataGridView.GetClipboardContent%2A?displayProperty=nameWithType> et affiche le contenu du Presse-papiers dans une zone de texte.</span><span class="sxs-lookup"><span data-stu-id="5d5c6-114">This example includes a button that copies the selected cells to the Clipboard using the <xref:System.Windows.Forms.DataGridView.GetClipboardContent%2A?displayProperty=nameWithType> method and displays the Clipboard contents in a text box.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridViewClipboardDemo#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewClipboardDemo/CS/datagridviewclipboarddemo.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewClipboardDemo#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewClipboardDemo/VB/datagridviewclipboarddemo.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5d5c6-115">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="5d5c6-115">Compiling the Code</span></span>  
 <span data-ttu-id="5d5c6-116">Ce code nécessite :</span><span class="sxs-lookup"><span data-stu-id="5d5c6-116">This code requires:</span></span>  
  
- <span data-ttu-id="5d5c6-117">Des références aux assemblys N:System et N:System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="5d5c6-117">References to the N:System and N:System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="5d5c6-118">Pour plus d’informations sur la création de cet exemple à partir de la ligne de commande pour Visual Basic ou Visual c#, consultez [génération à partir de la ligne de commande](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [de ligne de commande avec csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="5d5c6-118">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="5d5c6-119">Vous pouvez également créer cet exemple dans Visual Studio en collant le code dans un nouveau projet.</span><span class="sxs-lookup"><span data-stu-id="5d5c6-119">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d5c6-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5d5c6-120">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A>
- <xref:System.Windows.Forms.DataGridView.GetClipboardContent%2A>
- [<span data-ttu-id="5d5c6-121">Sélection et utilisation du Presse-papiers avec le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5d5c6-121">Selection and Clipboard Use with the Windows Forms DataGridView Control</span></span>](selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)
