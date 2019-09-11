---
title: 'Procédure : Définir le texte d’un contrôle TextBox'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text content [WPF], setting
- TextBox control [WPF], setting text content
ms.assetid: bcd25fc7-a52f-4453-b802-2c8d2b335ab8
ms.openlocfilehash: 2e2bc70b108991fd4e3c138bfac5bff942173e33
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70856111"
---
# <a name="how-to-set-the-text-content-of-a-textbox-control"></a><span data-ttu-id="2b5f4-102">Procédure : Définir le texte d’un contrôle TextBox</span><span class="sxs-lookup"><span data-stu-id="2b5f4-102">How to: Set the Text Content of a TextBox Control</span></span>

<span data-ttu-id="2b5f4-103">Cet exemple montre comment utiliser la <xref:System.Windows.Controls.TextBox.Text%2A> propriété pour définir le contenu de texte initial d’un <xref:System.Windows.Controls.TextBox> contrôle.</span><span class="sxs-lookup"><span data-stu-id="2b5f4-103">This example shows how to use the <xref:System.Windows.Controls.TextBox.Text%2A> property to set the initial text contents of a <xref:System.Windows.Controls.TextBox> control.</span></span>

> [!NOTE]
> <span data-ttu-id="2b5f4-104">Bien que [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] la version de l’exemple puisse utiliser `<TextBox.Text>` les balises autour du <xref:System.Windows.Controls.TextBox> texte du contenu de chaque bouton, cela n’est pas <xref:System.Windows.Controls.TextBox> nécessaire car <xref:System.Windows.Markup.ContentPropertyAttribute> le applique l' <xref:System.Windows.Controls.TextBox.Text%2A> attribut à la propriété. .</span><span class="sxs-lookup"><span data-stu-id="2b5f4-104">Although the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] version of the example could use the `<TextBox.Text>` tags around the text of each button's <xref:System.Windows.Controls.TextBox> content, it is not necessary because the <xref:System.Windows.Controls.TextBox> applies the <xref:System.Windows.Markup.ContentPropertyAttribute> attribute to the <xref:System.Windows.Controls.TextBox.Text%2A> property.</span></span> <span data-ttu-id="2b5f4-105">Pour plus d’informations, consultez [vue d’ensemble du langage XAML (WPF)](../advanced/xaml-overview-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="2b5f4-105">For more information, see [XAML Overview (WPF)](../advanced/xaml-overview-wpf.md).</span></span>

## <a name="example"></a><span data-ttu-id="2b5f4-106">Exemples</span><span class="sxs-lookup"><span data-stu-id="2b5f4-106">Example</span></span>

[!code-xaml[TextBox_MiscCode#_TextBoxSetTextXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxsettextxaml)]

## <a name="example"></a><span data-ttu-id="2b5f4-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="2b5f4-107">Example</span></span>

[!code-csharp[TextBox_MiscCode#_TextBoxSetText](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textboxsettext)]
[!code-vb[TextBox_MiscCode#_TextBoxSetText](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textboxsettext)]

## <a name="see-also"></a><span data-ttu-id="2b5f4-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2b5f4-108">See also</span></span>

- [<span data-ttu-id="2b5f4-109">Vue d’ensemble de TextBox</span><span class="sxs-lookup"><span data-stu-id="2b5f4-109">TextBox Overview</span></span>](textbox-overview.md)
- [<span data-ttu-id="2b5f4-110">Vue d’ensemble de RichTextBox</span><span class="sxs-lookup"><span data-stu-id="2b5f4-110">RichTextBox Overview</span></span>](richtextbox-overview.md)
