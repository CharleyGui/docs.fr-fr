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
# <a name="how-to-set-the-text-content-of-a-textbox-control"></a>Comment : définir le texte d'un contrôle TextBox

Cet exemple montre comment utiliser la propriété <xref:System.Windows.Controls.TextBox.Text%2A> pour définir le texte initial d’un contrôle <xref:System.Windows.Controls.TextBox>.

> [!NOTE]
> Bien que la version [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] de l’exemple puisse utiliser les balises `<TextBox.Text>` autour du texte du contenu <xref:System.Windows.Controls.TextBox> de chaque bouton, cela n’est pas nécessaire, car le <xref:System.Windows.Controls.TextBox> applique l’attribut <xref:System.Windows.Markup.ContentPropertyAttribute> à la propriété <xref:System.Windows.Controls.TextBox.Text%2A>. Pour plus d’informations, consultez [vue d’ensemble du langage XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md).

## <a name="example"></a>Exemple

[!code-xaml[TextBox_MiscCode#_TextBoxSetTextXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxsettextxaml)]

## <a name="example"></a>Exemple

[!code-csharp[TextBox_MiscCode#_TextBoxSetText](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textboxsettext)]
[!code-vb[TextBox_MiscCode#_TextBoxSetText](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textboxsettext)]

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de TextBox](textbox-overview.md)
- [Vue d’ensemble de RichTextBox](richtextbox-overview.md)
