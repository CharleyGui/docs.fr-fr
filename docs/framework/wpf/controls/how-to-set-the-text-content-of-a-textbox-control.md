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
# <a name="how-to-set-the-text-content-of-a-textbox-control"></a>Comment : définir le texte d'un contrôle TextBox

Cet exemple montre comment utiliser la <xref:System.Windows.Controls.TextBox.Text%2A> propriété pour définir le contenu de texte initial d’un <xref:System.Windows.Controls.TextBox> contrôle.

> [!NOTE]
> Bien que la [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] version de l’exemple puisse utiliser les `<TextBox.Text>` balises autour du texte du contenu de chaque bouton <xref:System.Windows.Controls.TextBox> , cela n’est pas nécessaire car le <xref:System.Windows.Controls.TextBox> applique l' <xref:System.Windows.Markup.ContentPropertyAttribute> attribut à la <xref:System.Windows.Controls.TextBox.Text%2A> propriété. Pour plus d’informations, consultez [vue d’ensemble du langage XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md).

## <a name="example"></a> Exemple

[!code-xaml[TextBox_MiscCode#_TextBoxSetTextXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxsettextxaml)]

## <a name="example"></a>Exemple

[!code-csharp[TextBox_MiscCode#_TextBoxSetText](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textboxsettext)]
[!code-vb[TextBox_MiscCode#_TextBoxSetText](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textboxsettext)]

## <a name="see-also"></a>Voir aussi

- [Vue d'ensemble de TextBox](textbox-overview.md)
- [Vue d'ensemble de RichTextBox](richtextbox-overview.md)
