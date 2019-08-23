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
# <a name="how-to-add-a-watermark-to-a-textbox"></a>Procédure : Ajouter un filigrane à un TextBox
L’exemple suivant montre comment faciliter l’utilisation d’un <xref:System.Windows.Controls.TextBox> en affichant une image d’arrière-plan explicative dans le <xref:System.Windows.Controls.TextBox> jusqu’à ce que l’utilisateur entre du texte, à l’endroit où l’image est supprimée. En outre, l’image d’arrière-plan est restaurée à nouveau si l’utilisateur supprime son entrée. Voir l’illustration ci-dessous.  
  
 ![Une zone de texte avec une image d’arrière-plan](./media/editing-textbox-using-background-image.png "Editing_TextBox_using_background_image")  
  
> [!NOTE]
> La raison pour laquelle une image d’arrière-plan est utilisée dans cet exemple plutôt <xref:System.Windows.Controls.TextBox.Text%2A> que de <xref:System.Windows.Controls.TextBox>manipuler simplement la propriété de, c’est qu’une image d’arrière-plan n’interfère pas avec la liaison de données.  
  
## <a name="example"></a>Exemples  
 [!code-xaml[TextBoxMiscSnippets_snip#TextBoxBackgroundExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/textbox_with_background_image.xaml#textboxbackgroundexamplewholepage)]  
  
 [!code-csharp[TextBoxMiscSnippets_snip#TextBoxBackgroundCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/textbox_with_background_image.xaml.cs#textboxbackgroundcodeexamplewholepage)]
 [!code-vb[TextBoxMiscSnippets_snip#TextBoxBackgroundCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/visualbasic/textbox_with_background_image.xaml.vb#textboxbackgroundcodeexamplewholepage)]  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de TextBox](textbox-overview.md)
- [Vue d’ensemble de RichTextBox](richtextbox-overview.md)
