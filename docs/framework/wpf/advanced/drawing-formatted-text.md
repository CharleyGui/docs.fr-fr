---
title: Dessin du texte mis en forme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [WPF]
- typography [WPF], drawing formatted text
- formatted text [WPF]
- drawing [WPF], formatted text
ms.assetid: b1d851c1-331c-4814-9964-6fe769db6f1f
ms.openlocfilehash: 1e82795afbdd5b1b0a05f95600ebdb92fc134b7d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186560"
---
# <a name="drawing-formatted-text"></a>Dessin du texte mis en forme
Ce sujet donne un aperçu <xref:System.Windows.Media.FormattedText> des caractéristiques de l’objet. Cet objet offre un contrôle de bas niveau pour le dessin de texte dans des applications [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  

## <a name="technology-overview"></a>Vue d’ensemble de la technologie  
 L’objet <xref:System.Windows.Media.FormattedText> vous permet de dessiner du texte multi-lignes, dans lequel chaque personnage du texte peut être formaté individuellement. L’exemple suivant montre un texte auquel plusieurs formats sont appliqués.  
  
 ![Texte affiché à l'aide de l'objet FormattedText](./media/typography-in-wpf/text-formatted-linear-gradient.jpg)  
  
> [!NOTE]
> Pour les développeurs qui migrent à partir de l’API Win32, le tableau de la section Migration [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] [Win32](#win32_migration) répertorie les drapeaux Win32 DrawText et l’équivalent approximatif dans .  
  
### <a name="reasons-for-using-formatted-text"></a>Raisons d’utiliser du texte mis en forme  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] inclut plusieurs contrôles pour dessiner le texte à l’écran. Chaque contrôle est ciblé sur un scénario différent et dispose de sa propre liste de fonctionnalités et limitations. En général, <xref:System.Windows.Controls.TextBlock> l’élément doit être utilisé lorsque le support texte [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]limité est nécessaire, comme une brève phrase dans un . <xref:System.Windows.Controls.Label>peut être utilisé lorsque le support texte minimal est nécessaire. Pour plus d’informations, consultez [Documents dans WPF](documents-in-wpf.md).  
  
 L’objet <xref:System.Windows.Media.FormattedText> fournit de plus [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] grandes fonctionnalités de formatage de texte que les contrôles de texte, et peut être utile dans les cas où vous souhaitez utiliser le texte comme un élément décoratif. Pour plus d’informations, consultez la section suivante, [Conversion du texte mis en forme en géométrie](#converting_formatted_text).  
  
 En outre, <xref:System.Windows.Media.FormattedText> l’objet est utile <xref:System.Windows.Media.DrawingVisual>pour créer des objets dérivés orientés vers le texte. <xref:System.Windows.Media.DrawingVisual>est une classe de dessin léger qui est utilisé pour rendre les formes, les images ou le texte. Pour plus d’informations, consultez [Test de positionnement à l’aide de DrawingVisuals, exemple](https://github.com/Microsoft/WPF-Samples/tree/master/Visual%20Layer/DrawingVisual).  
  
## <a name="using-the-formattedtext-object"></a>Utilisation de l’objet FormattedText  
 Pour créer du texte <xref:System.Windows.Media.FormattedText.%23ctor%2A> formaté, appelez <xref:System.Windows.Media.FormattedText> le constructeur pour créer un objet. Une fois que vous avez créé la chaîne initiale de texte mis en forme, vous pouvez appliquer différents styles de mise en forme.  
  
 Utilisez <xref:System.Windows.Media.FormattedText.MaxTextWidth%2A> la propriété pour limiter le texte à une largeur spécifique. Le texte est alors automatiquement renvoyé à la ligne pour éviter de dépasser la largeur spécifiée. Utilisez <xref:System.Windows.Media.FormattedText.MaxTextHeight%2A> la propriété pour limiter le texte à une hauteur spécifique. Le texte affiche des points de suspension (...) en lieu et place du texte qui dépasse la hauteur spécifiée.  
  
 ![Texte affiché avec wordwrap et ellipsis.](./media/drawing-formatted-text/formatted-text-wordwrap-ellipsis.png)
  
 Vous pouvez appliquer plusieurs styles de mise en forme à un ou plusieurs caractères. Par exemple, vous pouvez <xref:System.Windows.Media.FormattedText.SetFontSize%2A> <xref:System.Windows.Media.FormattedText.SetForegroundBrush%2A> appeler à la fois le et les méthodes pour modifier le formatage des cinq premiers caractères dans le texte.  
  
 L’exemple de <xref:System.Windows.Media.FormattedText> code suivant crée un objet et applique ensuite plusieurs styles de formatage au texte.  
  
 [!code-csharp[FormattedTextSnippets#FormattedTextSnippets1](~/samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets1)]
 [!code-vb[FormattedTextSnippets#FormattedTextSnippets1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets1)]  
  
### <a name="font-size-unit-of-measure"></a>Unité de mesure de la taille de police  
 Comme pour les [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] autres objets <xref:System.Windows.Media.FormattedText> textuels dans les applications, l’objet utilise des pixels indépendants de l’appareil comme unité de mesure. Cependant, la plupart des applications Win32 utilisent les points comme unité de mesure. Si vous souhaitez utiliser le texte [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] d’affichage dans des unités de points dans les applications, vous devez convertir des unités indépendantes de l’appareil (1/96e pouce par unité) en points. L’exemple de code suivant montre comment effectuer cette conversion.  
  
 [!code-csharp[FormattedTextSnippets#FormattedTextSnippets2](~/samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets2)]
 [!code-vb[FormattedTextSnippets#FormattedTextSnippets2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets2)]  
  
<a name="converting_formatted_text"></a>
### <a name="converting-formatted-text-to-a-geometry"></a>Conversion du texte mis en forme en géométrie  
 Vous pouvez convertir le <xref:System.Windows.Media.Geometry> texte formaté en objets, vous permettant de créer d’autres types de texte visuellement intéressant. Par exemple, vous <xref:System.Windows.Media.Geometry> pouvez créer un objet en fonction du contour d’une chaîne de texte.  
  
 ![Contour du texte utilisant un pinceau de dégradé linéaire](./media/typography-in-wpf/text-outline-linear-gradient.jpg)
  
 Les exemples suivants illustrent plusieurs façons de créer des effets visuels intéressants en modifiant le trait, le remplissage et la surbrillance du texte converti.  
  
 ![Texte avec différentes couleurs de trait et de remplissage](./media/typography-in-wpf/fill-stroke-text-effect.jpg)  
  
 ![Texte avec pinceau image appliqué au trait](./media/typography-in-wpf/image-brush-application.jpg)
  
 ![Texte avec pinceau d’image appliqué à la course et mettre en évidence](./media/typography-in-wpf/image-brush-text-application.jpg)
  
 Lorsque le texte est <xref:System.Windows.Media.Geometry> converti en objet, il ne s’agit plus d’une collection de caractères, vous ne pouvez pas modifier les caractères de la chaîne de texte. Vous pouvez néanmoins modifier l’apparence du texte converti en changeant ses propriétés de trait et de remplissage. Le trait fait référence au contour du texte converti et le remplissage à la zone située à l’intérieur du contour du texte converti. Pour plus d’informations, consultez [Créer du texte avec contour](how-to-create-outlined-text.md).  
  
 Vous pouvez également convertir le <xref:System.Windows.Media.PathGeometry> texte formaté en objet, et utiliser l’objet pour mettre en surbrillance le texte. Par exemple, vous pouvez appliquer <xref:System.Windows.Media.PathGeometry> une animation à l’objet afin que l’animation suive le contour du texte formaté.  
  
 L’exemple suivant montre le texte formaté <xref:System.Windows.Media.PathGeometry> qui a été converti en objet. Une ellipse animée suit le tracé des traits du texte rendu.  
  
 ![Sphère suivant la géométrie de tracé du texte](./media/drawing-formatted-text/sphere-following-geometry-path.gif)  
Sphère suivant la géométrie de tracé du texte  
  
 Pour plus d’informations, consultez [Guide pratique pour créer une animation PathGeometry pour du texte](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms743610(v=vs.100)).  
  
 Vous pouvez créer d’autres utilisations intéressantes pour <xref:System.Windows.Media.PathGeometry> le texte formaté une fois qu’il a été converti en objet. Par exemple, vous pouvez y insérer une vidéo.  
  
 ![Vidéo s’affichant dans la géométrie de tracé du texte](./media/drawing-formatted-text/video-displaying-text-path-geometry.png)
  
<a name="win32_migration"></a>
## <a name="win32-migration"></a>Migration depuis Win32  
 Les caractéristiques du texte de <xref:System.Windows.Media.FormattedText> dessin sont similaires aux caractéristiques de la fonction Win32 DrawText. Pour les développeurs qui migrent à partir de l’API Win32, le tableau suivant [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]répertorie les drapeaux Win32 DrawText et l’équivalent approximatif dans .  
  
|Indicateur DrawText|Équivalent WPF|Notes|  
|-------------------|--------------------|-----------|  
|DT_BOTTOM|<xref:System.Windows.Media.FormattedText.Height%2A>|Utilisez <xref:System.Windows.Media.FormattedText.Height%2A> la propriété pour calculer une position appropriée Win32 DrawText 'y'.|  
|DT_CALCRECT|<xref:System.Windows.Media.FormattedText.Height%2A>, <xref:System.Windows.Media.FormattedText.Width%2A>|Utilisez <xref:System.Windows.Media.FormattedText.Height%2A> le <xref:System.Windows.Media.FormattedText.Width%2A> rectangle de sortie et les propriétés.|  
|DT_CENTER|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|Utilisez <xref:System.Windows.Media.FormattedText.TextAlignment%2A> la propriété avec <xref:System.Windows.TextAlignment.Center>la valeur définie à .|  
|DT_EDITCONTROL|None|Non requis. La largeur de l’espace et le rendu de la dernière ligne sont les mêmes que dans le contrôle d’édition du framework.|  
|DT_END_ELLIPSIS|<xref:System.Windows.Media.FormattedText.Trimming%2A>|Utilisez <xref:System.Windows.Media.FormattedText.Trimming%2A> la propriété <xref:System.Windows.TextTrimming.CharacterEllipsis>avec la valeur .<br /><br /> Utilisez <xref:System.Windows.TextTrimming.WordEllipsis> pour obtenir Win32 DT_END_ELLIPSIS avec DT_WORD_ELIPSIS ellipsis fin-dans ce cas, ellipsis caractère se produit uniquement sur des mots qui ne rentrent pas sur une seule ligne.|  
|DT_EXPAND_TABS|None|Non requis. Des tabulations sont créées automatiquement avec des taquets tous les 4 cadratins, ce qui correspond plus ou moins à la largeur de 8 caractères indépendants du langage.|  
|DT_EXTERNALLEADING|None|Non requis. L’espacement externe est toujours inclus dans l’interligne. Utilisez <xref:System.Windows.Media.FormattedText.LineHeight%2A> la propriété pour créer un espacement de ligne défini par l’utilisateur.|  
|DT_HIDEPREFIX|None|Non pris en charge. Retirez le «&» de la chaîne <xref:System.Windows.Media.FormattedText> avant de construire l’objet.|  
|DT_LEFT|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|Il s’agit de l’alignement de texte par défaut. Utilisez <xref:System.Windows.Media.FormattedText.TextAlignment%2A> la propriété avec <xref:System.Windows.TextAlignment.Left>la valeur définie à . (WPF uniquement)|  
|DT_MODIFYSTRING|None|Non pris en charge.|  
|DT_NOCLIP|<xref:System.Windows.Media.Visual.VisualClip%2A>|Le découpage n’est pas effectué automatiquement. Si vous souhaitez couper du <xref:System.Windows.Media.Visual.VisualClip%2A> texte, utilisez la propriété.|  
|DT_NOFULLWIDTHCHARBREAK|None|Non pris en charge.|  
|DT_NOPREFIX|None|Non requis. Le caractère '&' présent dans les chaînes est toujours traité comme un caractère normal.|  
|DT_PATHELLIPSIS|None|Utilisez <xref:System.Windows.Media.FormattedText.Trimming%2A> la propriété <xref:System.Windows.TextTrimming.WordEllipsis>avec la valeur .|  
|DT_PREFIX|None|Non pris en charge. Si vous souhaitez utiliser des soulignements pour le texte, <xref:System.Windows.Media.FormattedText.SetTextDecorations%2A> comme une clé d’accélérateur ou un lien, utilisez la méthode.|  
|DT_PREFIXONLY|None|Non pris en charge.|  
|DT_RIGHT|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|Utilisez <xref:System.Windows.Media.FormattedText.TextAlignment%2A> la propriété avec <xref:System.Windows.TextAlignment.Right>la valeur définie à . (WPF uniquement)|  
|DT_RTLREADING|<xref:System.Windows.Media.FormattedText.FlowDirection%2A>|Attribuez à la propriété <xref:System.Windows.Media.FormattedText.FlowDirection%2A> la valeur <xref:System.Windows.FlowDirection.RightToLeft>.|  
|DT_SINGLELINE|None|Non requis. <xref:System.Windows.Media.FormattedText>les objets se comportent comme un <xref:System.Windows.Media.FormattedText.MaxTextWidth%2A> contrôle de ligne unique, à moins que la propriété soit définie ou que le texte ne contienne un flux de retour/ligne de transport (CR/LF).|  
|DT_TABSTOP|None|Les positions des taquets de tabulation définies par l’utilisateur ne sont pas prises en charge.|  
|DT_TOP|<xref:System.Windows.Media.FormattedText.Height%2A>|Non requis. La justification en haut est la valeur par défaut. D’autres valeurs de positionnement vertical <xref:System.Windows.Media.FormattedText.Height%2A> peuvent être définies en utilisant la propriété pour calculer une position appropriée Win32 DrawText 'y'.|  
|DT_VCENTER|<xref:System.Windows.Media.FormattedText.Height%2A>|Utilisez <xref:System.Windows.Media.FormattedText.Height%2A> la propriété pour calculer une position appropriée Win32 DrawText 'y'.|  
|DT_WORDBREAK|None|Non requis. La rupture des <xref:System.Windows.Media.FormattedText> mots se produit automatiquement avec les objets. Vous ne pouvez pas la désactiver.|  
|DT_WORD_ELLIPSIS|<xref:System.Windows.Media.FormattedText.Trimming%2A>|Utilisez <xref:System.Windows.Media.FormattedText.Trimming%2A> la propriété <xref:System.Windows.TextTrimming.WordEllipsis>avec la valeur .|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Media.FormattedText>
- [Documents dans WPF](documents-in-wpf.md)
- [Typographie dans WPF](typography-in-wpf.md)
- [Créer du texte avec contour](how-to-create-outlined-text.md)
- [Guide pratique pour créer une animation PathGeometry pour du texte](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms743610(v=vs.100))
