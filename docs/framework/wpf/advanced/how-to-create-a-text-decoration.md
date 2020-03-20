---
title: 'Comment : créer une décoration de texte'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- fonts [WPF], baseline
- text [WPF], decorations
- fonts [WPF], underline
- fonts [WPF], overline
- strikethrough type [WPF]
- fonts [WPF], strikethrough
- overline type [WPF]
- underline type [WPF]
- typography [WPF], text decorations
- baseline type [WPF]
ms.assetid: cf3cb4e7-782a-4be7-b2d4-e0935e21e4e0
ms.openlocfilehash: cf3b3c3bcb75153a0be4f7ced03b38134b79a930
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185921"
---
# <a name="how-to-create-a-text-decoration"></a>Comment : créer une décoration de texte
Un <xref:System.Windows.TextDecoration> objet est une ornementation visuelle que vous pouvez ajouter au texte. Il existe quatre types de décorations de texte : souligner, baseline, strikethrough, et overline. L’exemple suivant montre l’emplacement des décorations de texte par rapport au texte.  
  
 ![Diagramme des types de décoration de texte](./media/how-to-create-a-text-decoration/text-decoration-types.gif)  
  
 Pour ajouter une décoration de <xref:System.Windows.TextDecoration> texte au texte, créez un objet et modifiez ses propriétés. Utilisez <xref:System.Windows.TextDecoration.Location%2A> la propriété pour spécifier où la décoration de texte apparaît, comme souligner. Utilisez <xref:System.Windows.TextDecoration.Pen%2A> la propriété pour spécifier l’apparence de la décoration de texte, telle qu’un remplissage solide ou une couleur de gradient. Si vous ne spécifiez pas une valeur pour la <xref:System.Windows.TextDecoration.Pen%2A> propriété, les décorations par défaut à la même couleur que le texte. Une fois que <xref:System.Windows.TextDecoration> vous avez défini <xref:System.Windows.TextDecorations> un objet, ajoutez-le à la collection de l’objet texte désiré.  
  
 L’exemple suivant montre une décoration de texte qui a été stylée avec un pinceau de gradient linéaire et un stylo pointillé.  
  
 ![Ornement de texte avec souligné dégradé linéaire](./media/how-to-create-a-text-decoration/text-decoration-gradient.png)  
  
 L’objet <xref:System.Windows.Documents.Hyperlink> est un élément de contenu de flux au niveau de l’intérieur qui vous permet d’héberger des hyperliens dans le contenu du flux. Par défaut, <xref:System.Windows.Documents.Hyperlink> <xref:System.Windows.TextDecoration> utilise un objet pour afficher un soulignement. <xref:System.Windows.TextDecoration>les objets peuvent être intensifs en matière <xref:System.Windows.Documents.Hyperlink> de performances pour instantané, en particulier si vous avez de nombreux objets. Si vous faites <xref:System.Windows.Documents.Hyperlink> un usage intensif des éléments, vous pouvez envisager de montrer <xref:System.Windows.ContentElement.MouseEnter> un point de évidence seulement lors du déclenchement d’un événement, comme l’événement.  
  
 Dans l’exemple suivant, le soulignement du lien « My MSN » est dynamique , il n’apparaît que lorsque l’événement <xref:System.Windows.ContentElement.MouseEnter> est déclenché.  
  
 ![Liens hypertexte affichant TextDecorations](./media/how-to-create-a-text-decoration/text-decorations-hyperlinks.png)  

 Pour plus d’informations, consultez [Spécifier si un lien hypertexte est souligné ou non](how-to-specify-whether-a-hyperlink-is-underlined.md).  
  
## <a name="example"></a> Exemple  
 Dans l’exemple de code suivant, une décoration de texte de souligner utilise la valeur de police par défaut.  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets1)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets1)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets1)]  
  
 Dans l’exemple de code suivant, une décoration de texte de souligner est créée avec une brosse de couleur solide pour le stylo.  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets2)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets2)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets2)]  
  
 Dans l’exemple de code suivant, une décoration de texte de souligner est créée avec un pinceau de gradient linéaire pour le stylo pointillé.  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets3](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets3)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets3)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets3](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets3)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.TextDecoration>
- <xref:System.Windows.Documents.Hyperlink>
- [Spécifier si un lien hypertexte est souligné ou non](how-to-specify-whether-a-hyperlink-is-underlined.md)
