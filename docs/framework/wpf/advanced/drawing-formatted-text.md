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
ms.openlocfilehash: f23f54283849ddaa827a98f0f28a39a72305dc1d
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77095227"
---
# <a name="drawing-formatted-text"></a>Dessin du texte mis en forme
Cette rubrique fournit une vue d’ensemble des fonctionnalités de l’objet <xref:System.Windows.Media.FormattedText>. Cet objet offre un contrôle de bas niveau pour le dessin de texte dans des applications [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  

## <a name="technology-overview"></a>Vue d’ensemble de la technologie  
 L’objet <xref:System.Windows.Media.FormattedText> vous permet de dessiner du texte multiligne, dans lequel chaque caractère du texte peut être mis en forme individuellement. L’exemple suivant montre un texte auquel plusieurs formats sont appliqués.  
  
 ![Texte affiché à l'aide de l'objet FormattedText](./media/typography-in-wpf/text-formatted-linear-gradient.jpg)  
  
> [!NOTE]
> Pour les développeurs qui migrent à partir de l’API Win32, le tableau de la section [migration de Win32](#win32_migration) répertorie les indicateurs Win32 DrawText et l’équivalent approximatif dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
### <a name="reasons-for-using-formatted-text"></a>Raisons d’utiliser du texte mis en forme  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] inclut plusieurs contrôles pour dessiner le texte à l’écran. Chaque contrôle cible un scénario différent et dispose de sa propre liste de fonctionnalités et limitations. En général, l’élément <xref:System.Windows.Controls.TextBlock> doit être utilisé quand une prise en charge de texte limitée est nécessaire, par exemple une courte phrase dans une [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. <xref:System.Windows.Controls.Label> peut être utilisé quand une prise en charge minimale du texte est requise. Pour plus d’informations, consultez [Documents dans WPF](documents-in-wpf.md).  
  
 L’objet <xref:System.Windows.Media.FormattedText> fournit des fonctionnalités de mise en forme du texte plus importantes que [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] contrôles de texte, et peut être utile dans les cas où vous souhaitez utiliser du texte comme élément décoratif. Pour plus d’informations, consultez la section suivante, [Conversion du texte mis en forme en géométrie](#converting_formatted_text).  
  
 En outre, l’objet <xref:System.Windows.Media.FormattedText> est utile pour créer des objets dérivés de <xref:System.Windows.Media.DrawingVisual>textuels. <xref:System.Windows.Media.DrawingVisual> est une classe de dessin légère qui est utilisée pour afficher des formes, des images ou du texte. Pour plus d’informations, consultez [Test de positionnement à l’aide de DrawingVisuals, exemple](https://github.com/Microsoft/WPF-Samples/tree/master/Visual%20Layer/DrawingVisual).  
  
## <a name="using-the-formattedtext-object"></a>Utilisation de l’objet FormattedText  
 Pour créer du texte mis en forme, appelez le constructeur <xref:System.Windows.Media.FormattedText.%23ctor%2A> pour créer un objet <xref:System.Windows.Media.FormattedText>. Une fois que vous avez créé la chaîne initiale de texte mis en forme, vous pouvez appliquer différents styles de mise en forme.  
  
 Utilisez la propriété <xref:System.Windows.Media.FormattedText.MaxTextWidth%2A> pour contraindre le texte à une largeur spécifique. Le texte est alors automatiquement renvoyé à la ligne pour éviter de dépasser la largeur spécifiée. Utilisez la propriété <xref:System.Windows.Media.FormattedText.MaxTextHeight%2A> pour contraindre le texte à une hauteur spécifique. Le texte affiche des points de suspension (...) en lieu et place du texte qui dépasse la hauteur spécifiée.  
  
 ![Texte affiché avec des retours à la main et des points de suspension.](./media/drawing-formatted-text/formatted-text-wordwrap-ellipsis.png)    
  
 Vous pouvez appliquer plusieurs styles de mise en forme à un ou plusieurs caractères. Par exemple, vous pouvez appeler les méthodes <xref:System.Windows.Media.FormattedText.SetFontSize%2A> et <xref:System.Windows.Media.FormattedText.SetForegroundBrush%2A> pour modifier la mise en forme des cinq premiers caractères du texte.  
  
 L’exemple de code suivant crée un objet <xref:System.Windows.Media.FormattedText>, puis applique plusieurs styles de mise en forme au texte.  
  
 [!code-csharp[FormattedTextSnippets#FormattedTextSnippets1](~/samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets1)]
 [!code-vb[FormattedTextSnippets#FormattedTextSnippets1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets1)]  
  
### <a name="font-size-unit-of-measure"></a>Unité de mesure de la taille de police  
 Comme avec d’autres objets texte dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] applications, l’objet <xref:System.Windows.Media.FormattedText> utilise des pixels indépendants du périphérique comme unité de mesure. Toutefois, la plupart des applications Win32 utilisent des points comme unité de mesure. Si vous souhaitez utiliser le texte affiché en unités de points dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] applications, vous devez convertir les unités indépendantes du périphérique (1/96ème de pouce par unité) en points. L’exemple de code suivant montre comment effectuer cette conversion.  
  
 [!code-csharp[FormattedTextSnippets#FormattedTextSnippets2](~/samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets2)]
 [!code-vb[FormattedTextSnippets#FormattedTextSnippets2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets2)]  
  
<a name="converting_formatted_text"></a>   
### <a name="converting-formatted-text-to-a-geometry"></a>Conversion du texte mis en forme en géométrie  
 Vous pouvez convertir du texte mis en forme en objets <xref:System.Windows.Media.Geometry>, ce qui vous permet de créer d’autres types de texte visuellement intéressant. Par exemple, vous pouvez créer un objet <xref:System.Windows.Media.Geometry> basé sur le contour d’une chaîne de texte.  
  
 ![Contour du texte utilisant un pinceau de dégradé linéaire](./media/typography-in-wpf/text-outline-linear-gradient.jpg)    
  
 Les exemples suivants illustrent plusieurs façons de créer des effets visuels intéressants en modifiant le trait, le remplissage et la surbrillance du texte converti.  
  
 ![Texte avec différentes couleurs de trait et de remplissage](./media/typography-in-wpf/fill-stroke-text-effect.jpg)  
  
 ![Texte avec pinceau image appliqué au trait](./media/typography-in-wpf/image-brush-application.jpg)
  
 ![Texte avec pinceau d’image appliqué au trait et à la mise en surbrillance](./media/typography-in-wpf/image-brush-text-application.jpg)
  
 Lorsque le texte est converti en objet <xref:System.Windows.Media.Geometry>, il n’est plus une collection de caractères ; vous ne pouvez pas modifier les caractères dans la chaîne de texte. Vous pouvez néanmoins modifier l’apparence du texte converti en changeant ses propriétés de trait et de remplissage. Le trait fait référence au contour du texte converti et le remplissage à la zone située à l’intérieur du contour du texte converti. Pour plus d’informations, consultez [Créer du texte avec contour](how-to-create-outlined-text.md).  
  
 Vous pouvez également convertir du texte mis en forme en objet <xref:System.Windows.Media.PathGeometry> et utiliser l’objet pour mettre le texte en surbrillance. Par exemple, vous pouvez appliquer une animation à l’objet <xref:System.Windows.Media.PathGeometry> pour que l’animation suive le contour du texte mis en forme.  
  
 L’exemple suivant montre le texte mis en forme qui a été converti en objet <xref:System.Windows.Media.PathGeometry>. Une ellipse animée suit le tracé des traits du texte rendu.  
  
 ![Sphère suivant la géométrie de tracé du texte](./media/drawing-formatted-text/sphere-following-geometry-path.gif)  
Sphère suivant la géométrie de tracé du texte  
  
 Pour plus d’informations, consultez [Guide pratique pour créer une animation PathGeometry pour du texte](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms743610(v=vs.100)).  
  
 Vous pouvez créer d’autres utilisations intéressantes pour le texte mis en forme une fois qu’il a été converti en objet <xref:System.Windows.Media.PathGeometry>. Par exemple, vous pouvez y insérer une vidéo.  
  
 ![Vidéo s’affichant dans la géométrie de tracé du texte](./media/drawing-formatted-text/video-displaying-text-path-geometry.png)
  
<a name="win32_migration"></a>   
## <a name="win32-migration"></a>Migration depuis Win32  
 Les fonctionnalités de <xref:System.Windows.Media.FormattedText> pour dessiner du texte sont similaires à celles de la fonction Win32 DrawText. Pour les développeurs qui migrent à partir de l’API Win32, le tableau suivant répertorie les indicateurs Win32 DrawText et l’équivalent approximatif dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
|Indicateur DrawText|Équivalent WPF|Notes|  
|-------------------|--------------------|-----------|  
|DT_BOTTOM|<xref:System.Windows.Media.FormattedText.Height%2A>|Utilisez la propriété <xref:System.Windows.Media.FormattedText.Height%2A> pour calculer une position « y » de DrawText Win32 appropriée.|  
|DT_CALCRECT|<xref:System.Windows.Media.FormattedText.Height%2A>, <xref:System.Windows.Media.FormattedText.Width%2A>|Utilisez les propriétés <xref:System.Windows.Media.FormattedText.Height%2A> et <xref:System.Windows.Media.FormattedText.Width%2A> pour calculer le rectangle de sortie.|  
|DT_CENTER|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|Utilisez la propriété <xref:System.Windows.Media.FormattedText.TextAlignment%2A> avec la valeur définie sur <xref:System.Windows.TextAlignment.Center>.|  
|DT_EDITCONTROL|None|Non requis. La largeur de l’espace et le rendu de la dernière ligne sont les mêmes que dans le contrôle d’édition du framework.|  
|DT_END_ELLIPSIS|<xref:System.Windows.Media.FormattedText.Trimming%2A>|Utilisez la propriété <xref:System.Windows.Media.FormattedText.Trimming%2A> avec la valeur <xref:System.Windows.TextTrimming.CharacterEllipsis>.<br /><br /> Utilisez <xref:System.Windows.TextTrimming.WordEllipsis> pour obtenir des DT_END_ELLIPSIS Win32 avec des points de suspension de fin DT_WORD_ELIPSIS. dans ce cas, les points de suspension des caractères se produisent uniquement sur les mots qui ne tiennent pas sur une seule ligne.|  
|DT_EXPAND_TABS|None|Non requis. Des tabulations sont créées automatiquement avec des taquets tous les 4 cadratins, ce qui correspond plus ou moins à la largeur de 8 caractères indépendants du langage.|  
|DT_EXTERNALLEADING|None|Non requis. L’espacement externe est toujours inclus dans l’interligne. Utilisez la propriété <xref:System.Windows.Media.FormattedText.LineHeight%2A> pour créer un espacement de lignes défini par l’utilisateur.|  
|DT_HIDEPREFIX|None|Non pris en charge. Supprimez le' & 'de la chaîne avant de construire l’objet <xref:System.Windows.Media.FormattedText>.|  
|DT_LEFT|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|Il s’agit de l’alignement de texte par défaut. Utilisez la propriété <xref:System.Windows.Media.FormattedText.TextAlignment%2A> avec la valeur définie sur <xref:System.Windows.TextAlignment.Left>. (WPF uniquement)|  
|DT_MODIFYSTRING|None|Non pris en charge.|  
|DT_NOCLIP|<xref:System.Windows.Media.Visual.VisualClip%2A>|Le découpage n’est pas effectué automatiquement. Si vous souhaitez découper du texte, utilisez la propriété <xref:System.Windows.Media.Visual.VisualClip%2A>.|  
|DT_NOFULLWIDTHCHARBREAK|None|Non pris en charge.|  
|DT_NOPREFIX|None|Non requis. Le caractère '&' présent dans les chaînes est toujours traité comme un caractère normal.|  
|DT_PATHELLIPSIS|None|Utilisez la propriété <xref:System.Windows.Media.FormattedText.Trimming%2A> avec la valeur <xref:System.Windows.TextTrimming.WordEllipsis>.|  
|DT_PREFIX|None|Non pris en charge. Si vous souhaitez utiliser des traits de soulignement pour du texte, par exemple une touche accélérateur ou un lien, utilisez la méthode <xref:System.Windows.Media.FormattedText.SetTextDecorations%2A>.|  
|DT_PREFIXONLY|None|Non pris en charge.|  
|DT_RIGHT|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|Utilisez la propriété <xref:System.Windows.Media.FormattedText.TextAlignment%2A> avec la valeur définie sur <xref:System.Windows.TextAlignment.Right>. (WPF uniquement)|  
|DT_RTLREADING|<xref:System.Windows.Media.FormattedText.FlowDirection%2A>|Attribuez à la propriété <xref:System.Windows.Media.FormattedText.FlowDirection%2A> la valeur <xref:System.Windows.FlowDirection.RightToLeft>.|  
|DT_SINGLELINE|None|Non requis. les objets <xref:System.Windows.Media.FormattedText> se comportent comme un contrôle à ligne unique, sauf si la propriété <xref:System.Windows.Media.FormattedText.MaxTextWidth%2A> est définie ou si le texte contient un retour chariot/saut de ligne (CR/LF).|  
|DT_TABSTOP|None|Les positions des taquets de tabulation définies par l’utilisateur ne sont pas prises en charge.|  
|DT_TOP|<xref:System.Windows.Media.FormattedText.Height%2A>|Non requis. La justification en haut est la valeur par défaut. D’autres valeurs de positionnement vertical peuvent être définies à l’aide de la propriété <xref:System.Windows.Media.FormattedText.Height%2A> pour calculer une position « y » appropriée de la valeur Win32 DrawText.|  
|DT_VCENTER|<xref:System.Windows.Media.FormattedText.Height%2A>|Utilisez la propriété <xref:System.Windows.Media.FormattedText.Height%2A> pour calculer une position « y » de DrawText Win32 appropriée.|  
|DT_WORDBREAK|None|Non requis. Les césures de mots se produisent automatiquement avec les objets <xref:System.Windows.Media.FormattedText>. Vous ne pouvez pas la désactiver.|  
|DT_WORD_ELLIPSIS|<xref:System.Windows.Media.FormattedText.Trimming%2A>|Utilisez la propriété <xref:System.Windows.Media.FormattedText.Trimming%2A> avec la valeur <xref:System.Windows.TextTrimming.WordEllipsis>.|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Media.FormattedText>
- [Documents dans WPF](documents-in-wpf.md)
- [Typographie dans WPF](typography-in-wpf.md)
- [Créer du texte avec contour](how-to-create-outlined-text.md)
- [Guide pratique pour créer une animation PathGeometry pour du texte](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms743610(v=vs.100))
