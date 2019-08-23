---
title: 'Procédure : Ajouter un filigrane à un TextBox'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- displaying a background image inside a text box to aid user input [WPF]
- aid usability of a TextBox using a background image [WPF]
ms.assetid: df89bdd8-a0fb-45e0-b312-dd53332d01a8
ms.openlocfilehash: abe276c686d394ded13ec03f08deae65e4098d03
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923575"
---
# <a name="how-to-add-a-watermark-to-a-textbox"></a><span data-ttu-id="d394c-102">Procédure : Ajouter un filigrane à un TextBox</span><span class="sxs-lookup"><span data-stu-id="d394c-102">How to: Add a Watermark to a TextBox</span></span>
<span data-ttu-id="d394c-103">L’exemple suivant montre comment faciliter l’utilisation d’un <xref:System.Windows.Controls.TextBox> en affichant une image d’arrière-plan explicative dans le <xref:System.Windows.Controls.TextBox> jusqu’à ce que l’utilisateur entre du texte, à l’endroit où l’image est supprimée.</span><span class="sxs-lookup"><span data-stu-id="d394c-103">The following example shows how to aid usability of a <xref:System.Windows.Controls.TextBox> by displaying an explanatory background image inside of the <xref:System.Windows.Controls.TextBox> until the user inputs text, at which point the image is removed.</span></span> <span data-ttu-id="d394c-104">En outre, l’image d’arrière-plan est restaurée à nouveau si l’utilisateur supprime son entrée.</span><span class="sxs-lookup"><span data-stu-id="d394c-104">In addition, the background image is restored again if the user removes their input.</span></span> <span data-ttu-id="d394c-105">Voir l’illustration ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="d394c-105">See illustration below.</span></span>  
  
 <span data-ttu-id="d394c-106">![Une zone de texte avec une image d’arrière-plan](./media/editing-textbox-using-background-image.png "Editing_TextBox_using_background_image")</span><span class="sxs-lookup"><span data-stu-id="d394c-106">![A TextBox with a background image](./media/editing-textbox-using-background-image.png "Editing_TextBox_using_background_image")</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d394c-107">La raison pour laquelle une image d’arrière-plan est utilisée dans cet exemple plutôt <xref:System.Windows.Controls.TextBox.Text%2A> que de <xref:System.Windows.Controls.TextBox>manipuler simplement la propriété de, c’est qu’une image d’arrière-plan n’interfère pas avec la liaison de données.</span><span class="sxs-lookup"><span data-stu-id="d394c-107">The reason a background image is used in this example rather then simply manipulating the <xref:System.Windows.Controls.TextBox.Text%2A> property of <xref:System.Windows.Controls.TextBox>, is that a background image will not interfere with data binding.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d394c-108">Exemples</span><span class="sxs-lookup"><span data-stu-id="d394c-108">Example</span></span>  
 [!code-xaml[TextBoxMiscSnippets_snip#TextBoxBackgroundExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/textbox_with_background_image.xaml#textboxbackgroundexamplewholepage)]  
  
 [!code-csharp[TextBoxMiscSnippets_snip#TextBoxBackgroundCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/textbox_with_background_image.xaml.cs#textboxbackgroundcodeexamplewholepage)]
 [!code-vb[TextBoxMiscSnippets_snip#TextBoxBackgroundCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/visualbasic/textbox_with_background_image.xaml.vb#textboxbackgroundcodeexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="d394c-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d394c-109">See also</span></span>

- [<span data-ttu-id="d394c-110">Vue d’ensemble de TextBox</span><span class="sxs-lookup"><span data-stu-id="d394c-110">TextBox Overview</span></span>](textbox-overview.md)
- [<span data-ttu-id="d394c-111">Vue d’ensemble de RichTextBox</span><span class="sxs-lookup"><span data-stu-id="d394c-111">RichTextBox Overview</span></span>](richtextbox-overview.md)
