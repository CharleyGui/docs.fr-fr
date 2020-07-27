---
title: "Comment : définir le texte d'un contrôle TextBox"
description: Découvrez comment utiliser la propriété Text pour définir le texte initial d’un contrôle Windows Presentation Foundation TextBox.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text content [WPF], setting
- TextBox control [WPF], setting text content
ms.assetid: bcd25fc7-a52f-4453-b802-2c8d2b335ab8
ms.openlocfilehash: 41efb69e297b3c6fdb1203c358dcc72d7a9f806f
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168040"
---
# <a name="how-to-set-the-text-content-of-a-textbox-control"></a><span data-ttu-id="bcdeb-103">Comment : définir le texte d'un contrôle TextBox</span><span class="sxs-lookup"><span data-stu-id="bcdeb-103">How to: Set the Text Content of a TextBox Control</span></span>

<span data-ttu-id="bcdeb-104">Cet exemple montre comment utiliser la <xref:System.Windows.Controls.TextBox.Text%2A> propriété pour définir le contenu de texte initial d’un <xref:System.Windows.Controls.TextBox> contrôle.</span><span class="sxs-lookup"><span data-stu-id="bcdeb-104">This example shows how to use the <xref:System.Windows.Controls.TextBox.Text%2A> property to set the initial text contents of a <xref:System.Windows.Controls.TextBox> control.</span></span>

> [!NOTE]
> <span data-ttu-id="bcdeb-105">Bien que la [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] version de l’exemple puisse utiliser les `<TextBox.Text>` balises autour du texte du contenu de chaque bouton <xref:System.Windows.Controls.TextBox> , cela n’est pas nécessaire car le <xref:System.Windows.Controls.TextBox> applique l' <xref:System.Windows.Markup.ContentPropertyAttribute> attribut à la <xref:System.Windows.Controls.TextBox.Text%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="bcdeb-105">Although the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] version of the example could use the `<TextBox.Text>` tags around the text of each button's <xref:System.Windows.Controls.TextBox> content, it is not necessary because the <xref:System.Windows.Controls.TextBox> applies the <xref:System.Windows.Markup.ContentPropertyAttribute> attribute to the <xref:System.Windows.Controls.TextBox.Text%2A> property.</span></span> <span data-ttu-id="bcdeb-106">Pour plus d’informations, consultez [vue d’ensemble du langage XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md).</span><span class="sxs-lookup"><span data-stu-id="bcdeb-106">For more information, see [XAML Overview (WPF)](../../../desktop-wpf/fundamentals/xaml.md).</span></span>

## <a name="example"></a><span data-ttu-id="bcdeb-107"> Exemple</span><span class="sxs-lookup"><span data-stu-id="bcdeb-107">Example</span></span>

[!code-xaml[TextBox_MiscCode#_TextBoxSetTextXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxsettextxaml)]

## <a name="example"></a><span data-ttu-id="bcdeb-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="bcdeb-108">Example</span></span>

[!code-csharp[TextBox_MiscCode#_TextBoxSetText](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textboxsettext)]
[!code-vb[TextBox_MiscCode#_TextBoxSetText](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textboxsettext)]

## <a name="see-also"></a><span data-ttu-id="bcdeb-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bcdeb-109">See also</span></span>

- [<span data-ttu-id="bcdeb-110">Vue d'ensemble de TextBox</span><span class="sxs-lookup"><span data-stu-id="bcdeb-110">TextBox Overview</span></span>](textbox-overview.md)
- [<span data-ttu-id="bcdeb-111">Vue d'ensemble de RichTextBox</span><span class="sxs-lookup"><span data-stu-id="bcdeb-111">RichTextBox Overview</span></span>](richtextbox-overview.md)
