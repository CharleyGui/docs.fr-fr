---
title: Typographie
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], about typography
ms.assetid: 06cbf17b-6eff-4fe5-949d-2dd533e4e1f4
ms.openlocfilehash: 501a4221c99d405484a2fb908641d27d1f38f266
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187348"
---
# <a name="typography-in-wpf"></a>Typographie dans WPF
Cette rubrique présente les principales fonctionnalités typographiques de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Ces caractéristiques comprennent l’amélioration de la qualité et des performances du rendu du texte, le support typographie OpenType, l’amélioration du texte international, l’amélioration du support de police et de nouvelles interfaces de programmation d’applications textuelles (API).  
  
<a name="Improved_Quality_and_Performance_of_Text"></a>
## <a name="improved-quality-and-performance-of-text"></a>Amélioration de la qualité et des performances du texte  
 Le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] texte est rendu à l’aide de Microsoft ClearType, ce qui améliore la clarté et la lisibilité du texte. ClearType est une technologie logicielle développée par Microsoft qui améliore la lisibilité du texte sur les écrans de radio(liquid) existants (écrans de cristal liquide), tels que les écrans d’ordinateur portable, les écrans de PC de poche et les moniteurs de panneaux plats. ClearType utilise un rendu sous-pixel qui permet d’afficher le texte avec une plus grande fidélité à sa forme réelle en alignant les caractères sur une partie fractionnaire d’un pixel. Cette résolution accrue augmente la netteté des détails dans l’affichage textuel, ce qui facilite grandement la lecture pendant des périodes prolongées. Une autre amélioration de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ClearType est y-direction anti-aliasing, qui lisse les sommets et les fonds des courbes peu profondes dans les caractères de texte. Pour plus de détails sur les fonctionnalités ClearType, voir [ClearType Overview](cleartype-overview.md).  
  
 ![Texte avec anticrénelage ClearType dans la direction y](./media/typography-in-wpf/text-y-direction-antialiasing.gif)  
Texte avec anticrénelage ClearType dans la direction y  
  
 L’ensemble du pipeline de rendu de texte peut être accéléré par matériel dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], sous réserve que votre ordinateur respecte le niveau matériel minimum exigé. Un rendu ne pouvant pas être exécuté à l’aide de matériel repasse à un rendu logiciel. L’accélération du matériel affecte toutes les phases du pipeline de rendu de texte, du stockage des glyphes individuels, en composant les glyphes en glyphes, en appliquant des effets, à l’application de l’algorithme de mélange ClearType à la sortie affichée finale. Pour plus d’informations sur l’accélération matérielle, consultez [Couches de rendu graphiques](graphics-rendering-tiers.md).  
  
 ![Diagramme du pipeline de rendu de texte](./media/typography-in-wpf/text-rendering-pipeline.png)  
  
 En outre, un texte animé, par caractères ou par glyphes, tire pleinement parti de la fonction de matériel graphique activée par [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Il en résulte une animation de texte lisse.  
  
<a name="Rich_Typography"></a>
## <a name="rich-typography"></a>Typographie riche  
 Le format de police OpenType est une extension du format de police TrueType®. Le format de police OpenType a été développé conjointement par Microsoft et Adobe, et fournit un assortiment riche de fonctionnalités typographiques avancées. L’objet <xref:System.Windows.Documents.Typography> expose de nombreuses caractéristiques avancées des polices OpenType, telles que les alternatives stylistiques et les lave-linge. Le Windows SDK fournit un ensemble de polices OpenType échantillon qui sont conçus avec des fonctionnalités riches, telles que les polices Périclès et Pescadero. Pour plus d’informations, voir [Sample OpenType Font Pack](sample-opentype-font-pack.md).  
  
 La police Pericles OpenType contient des glyphes supplémentaires qui fournissent des alternatives stylistiques à l’ensemble standard de glyphes. Le texte suivant présente des glyphes de style alternatif.  
  
 ![Texte utilisant des glyphes de style alternatifs OpenType](./media/typography-in-wpf/opentype-stylistic-alternate-glyphs.gif "Texte utilisant des glyphes de style alternatifs OpenType")  
  
 Les lettres ornées sont des glyphes décoratifs qui utilisent une ornementation élaborée souvent associée à la calligraphie. Le texte suivant présente des glyphes standard et des glyphes à lettres ornées avec la police Pescadero.  
  
 ![Texte utilisant des glyphes standard et ornés OpenType](./media/typography-in-wpf/opentype-standard-swash-glyphs.gif "Texte utilisant des glyphes standard et ornés OpenType")  
  
 Pour plus de détails sur les fonctionnalités OpenType, voir [OpenType Font Features](opentype-font-features.md).  
  
<a name="Enhanced_International_Text_Support"></a>
## <a name="enhanced-international-text-support"></a>Prise en charge améliorée du texte international  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] offre une prise en charge améliorée du texte international par le biais des fonctionnalités suivantes :  
  
- Interligne automatique dans tous les systèmes d’écriture, par le biais de mesures adaptables.  
  
- Prise en charge générale du texte international. Pour plus d’informations, consultez [Globalisation pour WPF](globalization-for-wpf.md).  
  
- Saut de ligne, césure et justification par langue.  
  
<a name="Enhanced_Font_Support"></a>
## <a name="enhanced-font-support"></a>Prise en charge améliorée des polices  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] offre une prise en charge améliorée des polices par le biais des fonctionnalités suivantes :  
  
- Unicode pour tout le texte. La sélection et le comportement de la police ne requièrent plus de jeu de caractères ou de page de codes.  
  
- Comportement de police indépendant des paramètres globaux, tels que les paramètres régionaux du système.  
  
- Séparé <xref:System.Windows.FontWeight> <xref:System.Windows.FontStretch>, <xref:System.Windows.FontStyle> , et <xref:System.Windows.Media.FontFamily>les types pour définir un . Cela offre une plus grande flexibilité que dans la programmation Win32, dans laquelle boolean combinaisons d’italique et audacieux sont utilisés pour définir une famille de polices.  
  
- Sens d’écriture (horizontal ou vertical) géré indépendamment du nom de police.  
  
- Police de liaison et repli de police dans un fichier XML portable, en utilisant la technologie de police composite. Les polices composites permettent de générer une gamme complète de polices multilingues. Les polices composites fournissent également un mécanisme qui évite d’afficher les glyphes manquants. Pour plus d’informations, <xref:System.Windows.Media.FontFamily> voir les remarques dans la classe.  
  
- Polices internationales générées à partir de polices composites, à l’aide d’un groupe de polices d’une seule langue. Cela permet de limiter les coûts de ressources lors du développement de polices pour plusieurs langues.  
  
- Polices composites incorporées dans un document, autorisant ainsi la portabilité du document. Pour plus d’informations, <xref:System.Windows.Media.FontFamily> voir les remarques dans la classe.  
  
<a name="New_Text_APIs"></a>
## <a name="new-text-application-programming-interfaces-apis"></a>Nouvelles interfaces de programmation d’applications (API) texte  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]fournit plusieurs API texte pour les développeurs à utiliser lors de l’inclusion du texte dans leurs applications. Ces API sont regroupées en trois catégories :  
  
- **Mise en page et interface utilisateur**. Le texte commun contrôle l’interface utilisateur graphique (GUI).  
  
- **Dessin de texte léger**. Permet de dessiner du texte directement sur des objets.  
  
- **Formatage de texte avancé**. Permet d’implémenter un moteur de texte personnalisé.  
  
### <a name="layout-and-user-interface"></a>Disposition et interface utilisateur  
 Au plus haut niveau de fonctionnalité, les [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] API <xref:System.Windows.Controls.Label> <xref:System.Windows.Controls.TextBlock>de <xref:System.Windows.Controls.TextBox>texte fournissent des contrôles communs tels que , , et . Ces contrôles fournissent les éléments [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] de base dans une application et proposent une méthode simple pour présenter le texte et interagir avec celui-ci. Contrôles tels <xref:System.Windows.Controls.RichTextBox> <xref:System.Windows.Controls.PasswordBox> que et permettent une manipulation de texte plus avancée ou spécialisée. Et des <xref:System.Windows.Documents.TextRange>classes <xref:System.Windows.Documents.TextSelection>telles <xref:System.Windows.Documents.TextPointer> que , , et permettre la manipulation utile du texte. Ces [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] contrôles fournissent <xref:System.Windows.Controls.Control.FontFamily%2A>des <xref:System.Windows.Controls.Control.FontSize%2A>propriétés telles que , et <xref:System.Windows.Controls.Control.FontStyle%2A>, qui vous permettent de contrôler la police qui est utilisé pour rendre le texte.  
  
#### <a name="using-bitmap-effects-transforms-and-text-effects"></a>Utilisation d’effets bitmap, de transformations et d’effets de texte  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vous permet de créer des utilisations visuellement intéressantes de texte par le biais des fonctionnalités d’utilisation telles que les effets bitmap, les transformations et les effets de texte. L’exemple suivant présente un type classique d’effet d’ombre portée appliqué au texte.  
  
 ![Ombre de texte avec douceur &#61; 0,25](./media/typography-in-wpf/drop-shadow-text-effect.jpg)
  
 L’exemple suivant présente un effet d’ombre portée et un bruit appliqués au texte.  
  
 ![Ombre du texte avec bruit](./media/typography-in-wpf/drop-shadow-noise-text.jpg)
  
 L’exemple suivant présente un effet d’éclat extérieur appliqué au texte.  
  
 ![Ombre du texte utilisant OuterGlowBitmapEffect](./media/typography-in-wpf/text-shadow-glow-effect.jpg)
  
 L’exemple suivant présente un effet de flou appliqué au texte.  
  
 ![Ombre du texte utilisant BlurBitmapEffect](./media/typography-in-wpf/text-shadow-blur-effect.jpg)  

 Dans l’exemple suivant, la deuxième ligne du texte est mise à l’échelle par 150 % le long de l’axe x et la troisième ligne du texte est mise à l’échelle par 150 % le long de l’axe y.  
  
 ![Texte mis à l'échelle à l'aide de ScaleTransform](./media/typography-in-wpf/scaled-text-scaletransform.jpg)
  
 L’exemple suivant présente le texte incliné le long de l’axe x.  
  
 ![Texte incliné à l'aide de SkewTransform](./media/typography-in-wpf/skewed-transformed-text.jpg)
  
 Un <xref:System.Windows.Media.TextEffect> objet est un objet d’aide qui vous permet de traiter le texte comme un ou plusieurs groupes de caractères dans une chaîne de texte. L’exemple suivant montre un caractère individuel qui fait l’objet d’une rotation. Chaque caractère fait indépendamment l’objet d’une rotation à intervalles d’une seconde.  
  
 ![Capture d'écran : effet de rotation du texte](./media/typography-in-wpf/rotating-text-effect.jpg)
  
#### <a name="using-flow-documents"></a>Utilisation de documents dynamiques  
 En plus des [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] contrôles [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] communs, offre un contrôle <xref:System.Windows.Documents.FlowDocument> de mise en page pour la présentation du texte, l’élément. L’élément, <xref:System.Windows.Documents.FlowDocument> en <xref:System.Windows.Controls.DocumentViewer> conjonction avec l’élément, fournit un contrôle pour de grandes quantités de texte avec des exigences de mise en page variables. Les commandes de mise en <xref:System.Windows.Documents.Typography> page donnent accès à [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] une typographie avancée à travers les propriétés liées à l’objet et à la police d’autres contrôles.  
  
 L’exemple suivant montre le <xref:System.Windows.Controls.FlowDocumentReader>contenu texte hébergé dans un , qui fournit la recherche, la navigation, la pagination et le support de mise à l’échelle du contenu.  
  
 ![Capture d’écran qui montre des polices OpenType.](./media/typography-in-wpf/typography-text-flowdocumentreader.png)
  
 Pour plus d’informations, consultez [Documents dans WPF](documents-in-wpf.md).  
  
### <a name="lightweight-text-drawing"></a>Dessin de texte léger  
 Vous pouvez dessiner [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] du texte <xref:System.Windows.Media.DrawingContext.DrawText%2A> directement sur <xref:System.Windows.Media.DrawingContext> les objets en utilisant la méthode de l’objet. Pour utiliser cette méthode, <xref:System.Windows.Media.FormattedText> vous créez un objet. Cet objet vous permet de dessiner du texte multiligne dans lequel chaque caractère du texte peut être mis en forme individuellement. La fonctionnalité de <xref:System.Windows.Media.FormattedText> l’objet contient une grande partie de la fonctionnalité des drapeaux DrawText dans l’API Windows. En outre, <xref:System.Windows.Media.FormattedText> l’objet contient des fonctionnalités telles que le support d’élipsis, dans lequel une ellipsis est affichée lorsque le texte dépasse ses limites. L’exemple suivant présente un texte auquel plusieurs formats sont appliqués, notamment un dégradé linéaire sur les deuxième et troisième mots.  
  
 ![Texte affiché à l'aide de l'objet FormattedText](./media/typography-in-wpf/text-formatted-linear-gradient.jpg)
  
 Vous pouvez convertir le <xref:System.Windows.Media.Geometry> texte formaté en objets, vous permettant de créer d’autres types de texte visuellement intéressant. Par exemple, vous <xref:System.Windows.Media.Geometry> pouvez créer un objet en fonction du contour d’une chaîne de texte.  
  
 ![Contour du texte utilisant un pinceau de dégradé linéaire](./media/typography-in-wpf/text-outline-linear-gradient.jpg)  
  
 Les exemples suivants illustrent plusieurs façons de créer des effets visuels intéressants en modifiant le trait, le remplissage et la surbrillance du texte converti.  
  
 ![Texte avec différentes couleurs de trait et de remplissage](./media/typography-in-wpf/fill-stroke-text-effect.jpg)  
  
 ![Texte avec pinceau image appliqué au trait](./media/typography-in-wpf/image-brush-application.jpg)
  
 ![Texte avec pinceau d’image appliqué à la course et mettre en évidence](./media/typography-in-wpf/image-brush-text-application.jpg)
  
 Pour plus d’informations sur l’objet, <xref:System.Windows.Media.FormattedText> voir Dessin Texte [formaté](drawing-formatted-text.md).  
  
### <a name="advanced-text-formatting"></a>Mise en forme de texte avancée  
 Au niveau le plus avancé des [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] API de texte, vous offre <xref:System.Windows.Media.TextFormatting.TextFormatter> la possibilité de <xref:System.Windows.Media.TextFormatting> créer la mise en page personnalisée de texte en utilisant l’objet et d’autres types dans l’espace de nom. Les <xref:System.Windows.Media.TextFormatting.TextFormatter> classes et les classes associées vous permettent d’implémenter la mise en page de texte personnalisé qui prend en charge votre propre définition des formats de caractères, des styles de paragraphes, des règles de rupture de ligne et d’autres fonctionnalités de mise en page pour le texte international. Dans certains cas, vous pouvez être amené à remplacer l’implémentation par défaut de la prise en charge de la disposition du texte [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Toutefois, si vous créez une application ou un contrôle d’édition de texte, vous aurez peut-être besoin d’une implémentation différente de l’implémentation [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] par défaut.  
  
 Contrairement à une API <xref:System.Windows.Media.TextFormatting.TextFormatter> texte traditionnelle, l’interaction avec un client de mise en page de texte à travers un ensemble de méthodes de rappel. Il exige du client qu’il fournisse ces méthodes dans le cas d’une mise en œuvre de la <xref:System.Windows.Media.TextFormatting.TextSource> classe. Le diagramme suivant illustre l’interaction de <xref:System.Windows.Media.TextFormatting.TextFormatter>mise en page de texte entre l’application client et .  
  
 ![Diagramme du client de disposition du texte et TextFormatter](./media/typography-in-wpf/text-layout-text-formatter-interaction.png)  
  
 Pour plus d’informations sur la création de la disposition de texte personnalisée, consultez [Mise en forme de texte avancée](advanced-text-formatting.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Media.FormattedText>
- <xref:System.Windows.Media.TextFormatting.TextFormatter>
- [Vue d’ensemble ClearType](cleartype-overview.md)
- [Fonctionnalités des polices OpenType](opentype-font-features.md)
- [Dessin du texte mis en forme](drawing-formatted-text.md)
- [Mise en forme de texte avancée](advanced-text-formatting.md)
- [Texte](optimizing-performance-text.md)
- [Typographie Microsoft](https://docs.microsoft.com/typography/)
