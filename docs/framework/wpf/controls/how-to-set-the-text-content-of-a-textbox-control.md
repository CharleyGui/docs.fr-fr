---
title: "Comment : définir le texte d'un contrôle TextBox"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text content [WPF], setting
- TextBox control [WPF], setting text content
ms.assetid: bcd25fc7-a52f-4453-b802-2c8d2b335ab8
ms.openlocfilehash: 9b16f2d99295a28725255361b0be3ef7f4245fd2
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459303"
---
# <a name="how-to-set-the-text-content-of-a-textbox-control"></a><span data-ttu-id="fd3c7-102">Comment : définir le texte d'un contrôle TextBox</span><span class="sxs-lookup"><span data-stu-id="fd3c7-102">How to: Set the Text Content of a TextBox Control</span></span>

<span data-ttu-id="fd3c7-103">Cet exemple montre comment utiliser la propriété <xref:System.Windows.Controls.TextBox.Text%2A> pour définir le texte initial d’un contrôle <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="fd3c7-103">This example shows how to use the <xref:System.Windows.Controls.TextBox.Text%2A> property to set the initial text contents of a <xref:System.Windows.Controls.TextBox> control.</span></span>

> [!NOTE]
> <span data-ttu-id="fd3c7-104">Bien que la version [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] de l’exemple puisse utiliser les balises `<TextBox.Text>` autour du texte du contenu <xref:System.Windows.Controls.TextBox> de chaque bouton, cela n’est pas nécessaire, car le <xref:System.Windows.Controls.TextBox> applique l’attribut <xref:System.Windows.Markup.ContentPropertyAttribute> à la propriété <xref:System.Windows.Controls.TextBox.Text%2A>.</span><span class="sxs-lookup"><span data-stu-id="fd3c7-104">Although the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] version of the example could use the `<TextBox.Text>` tags around the text of each button's <xref:System.Windows.Controls.TextBox> content, it is not necessary because the <xref:System.Windows.Controls.TextBox> applies the <xref:System.Windows.Markup.ContentPropertyAttribute> attribute to the <xref:System.Windows.Controls.TextBox.Text%2A> property.</span></span> <span data-ttu-id="fd3c7-105">Pour plus d’informations, consultez [vue d’ensemble du langage XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md).</span><span class="sxs-lookup"><span data-stu-id="fd3c7-105">For more information, see [XAML Overview (WPF)](../../../desktop-wpf/fundamentals/xaml.md).</span></span>

## <a name="example"></a><span data-ttu-id="fd3c7-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="fd3c7-106">Example</span></span>

[!code-xaml[TextBox_MiscCode#_TextBoxSetTextXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxsettextxaml)]

## <a name="example"></a><span data-ttu-id="fd3c7-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="fd3c7-107">Example</span></span>

[!code-csharp[TextBox_MiscCode#_TextBoxSetText](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textboxsettext)]
[!code-vb[TextBox_MiscCode#_TextBoxSetText](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textboxsettext)]

## <a name="see-also"></a><span data-ttu-id="fd3c7-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fd3c7-108">See also</span></span>

- [<span data-ttu-id="fd3c7-109">Vue d’ensemble de TextBox</span><span class="sxs-lookup"><span data-stu-id="fd3c7-109">TextBox Overview</span></span>](textbox-overview.md)
- [<span data-ttu-id="fd3c7-110">Vue d’ensemble de RichTextBox</span><span class="sxs-lookup"><span data-stu-id="fd3c7-110">RichTextBox Overview</span></span>](richtextbox-overview.md)
