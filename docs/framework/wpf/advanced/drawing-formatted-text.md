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
ms.openlocfilehash: eeba54ebd63b26a50c8c01a2478e847b3e660a3f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937689"
---
# <a name="drawing-formatted-text"></a>Dessin du texte mis en forme
Cette rubrique fournit une vue d’ensemble des fonctionnalités de <xref:System.Windows.Media.FormattedText> l’objet. Cet objet offre un contrôle de bas niveau pour le dessin de texte dans des applications [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  

## <a name="technology-overview"></a>Vue d’ensemble de la technologie  
 L' <xref:System.Windows.Media.FormattedText> objet vous permet de dessiner du texte multiligne, dans lequel chaque caractère du texte peut être mis en forme individuellement. L’exemple suivant montre un texte auquel plusieurs formats sont appliqués.  
  
 ![Texte affiché à l'aide de l'objet FormattedText](./media/typography-in-wpf/text-formatted-linear-gradient.jpg)  
  
> [!NOTE]
> Pour les développeurs qui migrent depuis l’API [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)], le tableau présenté dans la section [Migration depuis Win32](#win32_migration) répertorie les indicateurs DrawText de [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] et leur équivalent approximatif dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
### <a name="reasons-for-using-formatted-text"></a>Raisons d’utiliser du texte mis en forme  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] inclut plusieurs contrôles pour dessiner le texte à l’écran. Chaque contrôle cible un scénario différent et dispose de sa propre liste de fonctionnalités et limitations. En général, l' <xref:System.Windows.Controls.TextBlock> élément doit être utilisé quand une prise en charge de texte limitée est nécessaire, par exemple une [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]courte phrase dans un. <xref:System.Windows.Controls.Label>peut être utilisé quand une prise en charge minimale du texte est requise. Pour plus d’informations, consultez [Documents dans WPF](documents-in-wpf.md).  
  
 L' <xref:System.Windows.Media.FormattedText> objet fournit des [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fonctionnalités de mise en forme du texte supérieures aux contrôles de texte et peut être utile dans les cas où vous souhaitez utiliser du texte comme élément décoratif. Pour plus d’informations, consultez la section suivante, [Conversion du texte mis en forme en géométrie](#converting_formatted_text).  
  
 En outre, l' <xref:System.Windows.Media.FormattedText> objet est utile pour créer des objets dérivés de texte. <xref:System.Windows.Media.DrawingVisual> <xref:System.Windows.Media.DrawingVisual>est une classe de dessin légère qui est utilisée pour restituer des formes, des images ou du texte. Pour plus d’informations, consultez [Test de positionnement à l’aide de DrawingVisuals, exemple](https://go.microsoft.com/fwlink/?LinkID=159994).  
  
## <a name="using-the-formattedtext-object"></a>Utilisation de l’objet FormattedText  
 Pour créer du texte mis en forme <xref:System.Windows.Media.FormattedText.%23ctor%2A> , appelez le constructeur <xref:System.Windows.Media.FormattedText> pour créer un objet. Une fois que vous avez créé la chaîne initiale de texte mis en forme, vous pouvez appliquer différents styles de mise en forme.  
  
 Utilisez la <xref:System.Windows.Media.FormattedText.MaxTextWidth%2A> propriété pour contraindre le texte à une largeur spécifique. Le texte est alors automatiquement renvoyé à la ligne pour éviter de dépasser la largeur spécifiée. Utilisez la <xref:System.Windows.Media.FormattedText.MaxTextHeight%2A> propriété pour contraindre le texte à une hauteur spécifique. Le texte affiche des points de suspension (...) en lieu et place du texte qui dépasse la hauteur spécifiée.  
  
 ![Texte affiché avec des retours à la main et des points de suspension.](./media/drawing-formatted-text/formatted-text-wordwrap-ellipsis.png)    
  
 Vous pouvez appliquer plusieurs styles de mise en forme à un ou plusieurs caractères. Par exemple, vous pouvez appeler <xref:System.Windows.Media.FormattedText.SetFontSize%2A> les méthodes et <xref:System.Windows.Media.FormattedText.SetForegroundBrush%2A> pour modifier la mise en forme des cinq premiers caractères du texte.  
  
 L’exemple de code suivant crée <xref:System.Windows.Media.FormattedText> un objet, puis applique plusieurs styles de mise en forme au texte.  
  
 [!code-csharp[FormattedTextSnippets#FormattedTextSnippets1](~/samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets1)]
 [!code-vb[FormattedTextSnippets#FormattedTextSnippets1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets1)]  
  
### <a name="font-size-unit-of-measure"></a>Unité de mesure de la taille de police  
 Comme pour les autres objets texte [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] dans les applications <xref:System.Windows.Media.FormattedText> , l’objet utilise des pixels indépendants du périphérique comme unité de mesure. Toutefois, la plupart des applications [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] utilisent des points comme unité de mesure. Si vous souhaitez utiliser le texte affiché en unités de points dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] les applications, vous devez convertir les unités indépendantes du périphérique (1/96ème de pouce par unité) en points. L’exemple de code suivant montre comment effectuer cette conversion.  
  
 [!code-csharp[FormattedTextSnippets#FormattedTextSnippets2](~/samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets2)]
 [!code-vb[FormattedTextSnippets#FormattedTextSnippets2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets2)]  
  
<a name="converting_formatted_text"></a>   
### <a name="converting-formatted-text-to-a-geometry"></a>Conversion du texte mis en forme en géométrie  
 Vous pouvez convertir du texte mis <xref:System.Windows.Media.Geometry> en forme en objets, ce qui vous permet de créer d’autres types de texte visuellement intéressant. Par exemple, vous pouvez créer un <xref:System.Windows.Media.Geometry> objet basé sur le contour d’une chaîne de texte.  
  
 ![Contour du texte utilisant un pinceau de dégradé linéaire](./media/typography-in-wpf/text-outline-linear-gradient.jpg)    
  
 Les exemples suivants illustrent plusieurs façons de créer des effets visuels intéressants en modifiant le trait, le remplissage et la surbrillance du texte converti.  
  
 ![Texte avec différentes couleurs de trait et de remplissage](./media/typography-in-wpf/fill-stroke-text-effect.jpg)  
  
 ![Texte avec pinceau image appliqué au trait](./media/typography-in-wpf/image-brush-application.jpg)
  
 ![Texte avec pinceau d’image appliqué au trait et à la mise en surbrillance](./media/typography-in-wpf/image-brush-text-application.jpg)
  
 Quand le texte est converti en <xref:System.Windows.Media.Geometry> un objet, il n’est plus une collection de caractères, vous ne pouvez pas modifier les caractères dans la chaîne de texte. Vous pouvez néanmoins modifier l’apparence du texte converti en changeant ses propriétés de trait et de remplissage. Le trait fait référence au contour du texte converti et le remplissage à la zone située à l’intérieur du contour du texte converti. Pour plus d’informations, consultez [Créer du texte avec contour](how-to-create-outlined-text.md).  
  
 Vous pouvez également convertir du texte mis en <xref:System.Windows.Media.PathGeometry> forme en objet et utiliser l’objet pour mettre le texte en surbrillance. Par exemple, vous pouvez appliquer une animation à l' <xref:System.Windows.Media.PathGeometry> objet afin que l’animation suive le contour du texte mis en forme.  
  
 L’exemple suivant montre le texte mis en forme qui a été <xref:System.Windows.Media.PathGeometry> converti en objet. Une ellipse animée suit le tracé des traits du texte rendu.  
  
 ![Sphère suivant la géométrie de tracé du texte](./media/drawing-formatted-text/sphere-following-geometry-path.gif)  
Sphère suivant la géométrie de tracé du texte  
  
 Pour plus d’informations, consultez [Guide pratique pour Créer une animation PathGeometry pour le](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms743610(v=vs.100))texte.  
  
 Vous pouvez créer d’autres utilisations intéressantes pour le texte mis en forme une fois qu' <xref:System.Windows.Media.PathGeometry> il a été converti en objet. Par exemple, vous pouvez y insérer une vidéo.  
  
 ![Vidéo s’affichant dans la géométrie de tracé du texte](./media/drawing-formatted-text/video-displaying-text-path-geometry.png)
  
<a name="win32_migration"></a>   
## <a name="win32-migration"></a>Migration depuis Win32  
 Les fonctionnalités de <xref:System.Windows.Media.FormattedText> pour dessiner du texte sont similaires aux fonctionnalités de la [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] fonction DrawText. Pour les développeurs qui migrent depuis l’API [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)], le tableau suivant répertorie les indicateurs DrawText de [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] et leur équivalent approximatif dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
|Indicateur DrawText|Équivalent WPF|Notes|  
|-------------------|--------------------|-----------|  
|DT_BOTTOM|<xref:System.Windows.Media.FormattedText.Height%2A>|Utilisez la <xref:System.Windows.Media.FormattedText.Height%2A> propriété pour calculer une position' [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] y’DrawText appropriée.|  
|DT_CALCRECT|<xref:System.Windows.Media.FormattedText.Height%2A>, <xref:System.Windows.Media.FormattedText.Width%2A>|Utilisez les <xref:System.Windows.Media.FormattedText.Height%2A> propriétés <xref:System.Windows.Media.FormattedText.Width%2A> et pour calculer le rectangle de sortie.|  
|DT_CENTER|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|Utilisez la <xref:System.Windows.Media.FormattedText.TextAlignment%2A> propriété avec la valeur définie sur <xref:System.Windows.TextAlignment.Center>.|  
|DT_EDITCONTROL|Aucun|Non requis La largeur de l’espace et le rendu de la dernière ligne sont les mêmes que dans le contrôle d’édition du framework.|  
|DT_END_ELLIPSIS|<xref:System.Windows.Media.FormattedText.Trimming%2A>|Utilisez la <xref:System.Windows.Media.FormattedText.Trimming%2A> propriété avec la valeur <xref:System.Windows.TextTrimming.CharacterEllipsis>.<br /><br /> Utilisez <xref:System.Windows.TextTrimming.WordEllipsis> pour obtenir [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] DT_END_ELLIPSIS avec des points de suspension de fin DT_WORD_ELIPSIS. dans ce cas, les points de suspension des caractères se produisent uniquement sur les mots qui ne tiennent pas sur une seule ligne.|  
|DT_EXPAND_TABS|Aucun|Non requis Des tabulations sont créées automatiquement avec des taquets tous les 4 cadratins, ce qui correspond plus ou moins à la largeur de 8 caractères indépendants du langage.|  
|DT_EXTERNALLEADING|Aucun|Non requis L’espacement externe est toujours inclus dans l’interligne. Utilisez la <xref:System.Windows.Media.FormattedText.LineHeight%2A> propriété pour créer un espacement de lignes défini par l’utilisateur.|  
|DT_HIDEPREFIX|Aucun|Non pris en charge. Supprimez le' & 'de la chaîne avant de construire <xref:System.Windows.Media.FormattedText> l’objet.|  
|DT_LEFT|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|Il s’agit de l’alignement de texte par défaut. Utilisez la <xref:System.Windows.Media.FormattedText.TextAlignment%2A> propriété avec la valeur définie sur <xref:System.Windows.TextAlignment.Left>. (WPF uniquement)|  
|DT_MODIFYSTRING|Aucun|Non pris en charge.|  
|DT_NOCLIP|<xref:System.Windows.Media.Visual.VisualClip%2A>|Le découpage n’est pas effectué automatiquement. Si vous souhaitez découper du texte, <xref:System.Windows.Media.Visual.VisualClip%2A> utilisez la propriété.|  
|DT_NOFULLWIDTHCHARBREAK|Aucun|Non pris en charge.|  
|DT_NOPREFIX|Aucun|Non requis Le caractère '&' présent dans les chaînes est toujours traité comme un caractère normal.|  
|DT_PATHELLIPSIS|Aucun|Utilisez la <xref:System.Windows.Media.FormattedText.Trimming%2A> propriété avec la valeur <xref:System.Windows.TextTrimming.WordEllipsis>.|  
|DT_PREFIX|Aucun|Non pris en charge. Si vous souhaitez utiliser des traits de soulignement pour du texte, par exemple une touche accélérateur ou un <xref:System.Windows.Media.FormattedText.SetTextDecorations%2A> lien, utilisez la méthode.|  
|DT_PREFIXONLY|Aucun|Non pris en charge.|  
|DT_RIGHT|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|Utilisez la <xref:System.Windows.Media.FormattedText.TextAlignment%2A> propriété avec la valeur définie sur <xref:System.Windows.TextAlignment.Right>. (WPF uniquement)|  
|DT_RTLREADING|<xref:System.Windows.Media.FormattedText.FlowDirection%2A>|Affectez à la propriété <xref:System.Windows.Media.FormattedText.FlowDirection%2A> la valeur <xref:System.Windows.FlowDirection.RightToLeft>.|  
|DT_SINGLELINE|Aucun|Non requis <xref:System.Windows.Media.FormattedText>les objets se comportent comme un contrôle à ligne <xref:System.Windows.Media.FormattedText.MaxTextWidth%2A> unique, à moins que la propriété soit définie ou que le texte contienne un retour chariot/saut de ligne (CR/LF).|  
|DT_TABSTOP|Aucun|Les positions des taquets de tabulation définies par l’utilisateur ne sont pas prises en charge.|  
|DT_TOP|<xref:System.Windows.Media.FormattedText.Height%2A>|Non requis La justification en haut est la valeur par défaut. D’autres valeurs de positionnement vertical peuvent être définies à <xref:System.Windows.Media.FormattedText.Height%2A> l’aide de la propriété pour [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] calculer une position’y’DrawText appropriée.|  
|DT_VCENTER|<xref:System.Windows.Media.FormattedText.Height%2A>|Utilisez la <xref:System.Windows.Media.FormattedText.Height%2A> propriété pour calculer une position' [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] y’DrawText appropriée.|  
|DT_WORDBREAK|Aucun|Non requis Les césures de mots <xref:System.Windows.Media.FormattedText> se produisent automatiquement avec les objets. Vous ne pouvez pas la désactiver.|  
|DT_WORD_ELLIPSIS|<xref:System.Windows.Media.FormattedText.Trimming%2A>|Utilisez la <xref:System.Windows.Media.FormattedText.Trimming%2A> propriété avec la valeur <xref:System.Windows.TextTrimming.WordEllipsis>.|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Media.FormattedText>
- [Documents dans WPF](documents-in-wpf.md)
- [Typographie dans WPF](typography-in-wpf.md)
- [Créer du texte avec contour](how-to-create-outlined-text.md)
- [Guide pratique : Créer une animation PathGeometry pour du texte](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms743610(v=vs.100))
