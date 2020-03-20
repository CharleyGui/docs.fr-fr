---
title: 'Comment : créer du texte avec contour'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- typography [WPF], linear gradient brush
- outlined text [WPF]
- gradient brush [WPF]
- linear gradient brush [WPF]
- typography [WPF], outline effects
ms.assetid: 4aa3cf6e-1953-4f26-8230-7c1409e5f28d
ms.openlocfilehash: d0ce46b9895589fd4635b567136204368a6431ad
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186855"
---
# <a name="how-to-create-outlined-text"></a>Comment : créer du texte avec contour
Dans la plupart des cas, lorsque vous ajoutez [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] l’ornementation aux chaînes de texte dans votre application, vous utilisez du texte en termes de collection de caractères discrets, ou glyphes. Par exemple, vous pouvez créer un pinceau de <xref:System.Windows.Controls.Control.Foreground%2A> gradient <xref:System.Windows.Controls.TextBox> linéaire et l’appliquer à la propriété d’un objet. Lorsque vous affichez ou modifiez la boîte de texte, le pinceau de gradient linéaire est automatiquement appliqué à l’ensemble actuel des caractères de la chaîne de texte.  
  
 ![Texte affiché avec un pinceau de dégradé linéaire](./media/how-to-create-outlined-text/text-linear-gradient.jpg)
  
 Cependant, vous pouvez également <xref:System.Windows.Media.Geometry> convertir le texte en objets, vous permettant de créer d’autres types de texte visuellement riche. Par exemple, vous <xref:System.Windows.Media.Geometry> pouvez créer un objet en fonction du contour d’une chaîne de texte.  
  
 ![Contour du texte utilisant un pinceau de dégradé linéaire](./media/how-to-create-outlined-text/text-outline-linear-gradient.jpg)  
  
 Lorsque le texte est <xref:System.Windows.Media.Geometry> converti en objet, il ne s’agit plus d’une collection de caractères, vous ne pouvez pas modifier les caractères de la chaîne de texte. Vous pouvez néanmoins modifier l’apparence du texte converti en changeant ses propriétés de trait et de remplissage. Le trait fait référence au contour du texte converti et le remplissage à la zone située à l’intérieur du contour du texte converti.  
  
 Les exemples suivants illustrent plusieurs façons de créer des effets visuels en modifiant le trait et le remplissage du texte converti.  
  
 ![Texte avec différentes couleurs de trait et de remplissage](./media/how-to-create-outlined-text/fill-stroke-text-effect.jpg)  
  
 ![Texte avec pinceau image appliqué au trait](./media/how-to-create-outlined-text/image-brush-application.jpg)
  
 Il est également possible de modifier le rectangle de la boîte de délimitation, ou de mettre en évidence, du texte converti. L’exemple suivant illustre un moyen de créer des effets visuels en modifiant le trait et le point culminant du texte converti.  
  
 ![Texte avec pinceau d’image appliqué à la course et mettre en évidence](./media/how-to-create-outlined-text/image-brush-text-application.jpg)

## <a name="example"></a> Exemple  
 La clé pour convertir <xref:System.Windows.Media.Geometry> le texte en <xref:System.Windows.Media.FormattedText> un objet est d’utiliser l’objet. Une fois que vous avez créé <xref:System.Windows.Media.FormattedText.BuildGeometry%2A> <xref:System.Windows.Media.FormattedText.BuildHighlightGeometry%2A> cet objet, vous <xref:System.Windows.Media.Geometry> pouvez utiliser le et les méthodes pour convertir le texte en objets. La première méthode renvoie la géométrie du texte formaté; la deuxième méthode renvoie la géométrie de la boîte de délimitation du texte formaté. L’exemple de code suivant <xref:System.Windows.Media.FormattedText> montre comment créer un objet et récupérer les géométries du texte formaté et de sa boîte de délimitation.  
  
 [!code-csharp[OutlineTextControlViewer#CreateText](~/samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs#createtext)]
 [!code-vb[OutlineTextControlViewer#CreateText](~/samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb#createtext)]  
  
 Afin d’afficher les <xref:System.Windows.Media.Geometry> objets récupérés, vous <xref:System.Windows.Media.DrawingContext> devez accéder à l’objet qui affiche le texte converti. Dans ces exemples de code, cela se fait en créant un objet de contrôle personnalisé qui est dérivé d’une classe qui prend en charge le rendu défini par l’utilisateur.  
  
 Pour <xref:System.Windows.Media.Geometry> afficher des objets dans le contrôle <xref:System.Windows.UIElement.OnRender%2A> personnalisé, fournir un remplacement pour la méthode. Votre méthode précédée <xref:System.Windows.Media.DrawingContext.DrawGeometry%2A> devrait utiliser <xref:System.Windows.Media.Geometry> la méthode pour dessiner les objets.  
  
 [!code-csharp[OutlineTextControlViewer#OnRender](~/samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs#onrender)]
 [!code-vb[OutlineTextControlViewer#OnRender](~/samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb#onrender)]  
  
  Pour la source de l’objet de contrôle utilisateur personnalisé par exemple, voir [OutlineTextControl.cs pour C et](https://github.com/dotnet/samples/blob/master/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs) [OutlineTextControl.vb pour Visual Basic](https://github.com/dotnet/samples/blob/master/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb).
  
## <a name="see-also"></a>Voir aussi

- [Dessin du texte mis en forme](drawing-formatted-text.md)
