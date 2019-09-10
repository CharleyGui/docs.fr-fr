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
# <a name="how-to-set-the-text-content-of-a-textbox-control"></a>Procédure : Définir le texte d’un contrôle TextBox

Cet exemple montre comment utiliser la <xref:System.Windows.Controls.TextBox.Text%2A> propriété pour définir le contenu de texte initial d’un <xref:System.Windows.Controls.TextBox> contrôle.

> [!NOTE]
> Bien que [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] la version de l’exemple puisse utiliser `<TextBox.Text>` les balises autour du <xref:System.Windows.Controls.TextBox> texte du contenu de chaque bouton, cela n’est pas <xref:System.Windows.Controls.TextBox> nécessaire car <xref:System.Windows.Markup.ContentPropertyAttribute> le applique l' <xref:System.Windows.Controls.TextBox.Text%2A> attribut à la propriété. . Pour plus d’informations, consultez [vue d’ensemble du langage XAML (WPF)](../advanced/xaml-overview-wpf.md).

## <a name="example"></a>Exemples

[!code-xaml[TextBox_MiscCode#_TextBoxSetTextXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxsettextxaml)]

## <a name="example"></a>Exemple

[!code-csharp[TextBox_MiscCode#_TextBoxSetText](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textboxsettext)]
[!code-vb[TextBox_MiscCode#_TextBoxSetText](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textboxsettext)]

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de TextBox](textbox-overview.md)
- [Vue d’ensemble de RichTextBox](richtextbox-overview.md)
