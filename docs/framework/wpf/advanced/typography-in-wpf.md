---
title: Typographie
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], about typography
ms.assetid: 06cbf17b-6eff-4fe5-949d-2dd533e4e1f4
ms.openlocfilehash: 3d94873931e3ee6df780df214f508258aa07a791
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735535"
---
# <a name="typography-in-wpf"></a>Typographie dans WPF
Cette rubrique présente les principales fonctionnalités typographiques de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Ces fonctionnalités incluent une amélioration de la qualité et des performances du rendu du texte, de la prise en charge de typographie OpenType, du texte international amélioré, de la prise en charge améliorée des polices et des nouvelles interfaces de programmation d’applications (API) de texte.  
  
<a name="Improved_Quality_and_Performance_of_Text"></a>   
## <a name="improved-quality-and-performance-of-text"></a>Amélioration de la qualité et des performances du texte  
 Le texte de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] est affiché à l’aide de Microsoft ClearType, ce qui améliore la clarté et la lisibilité du texte. ClearType est une technologie logicielle développée par Microsoft qui améliore la lisibilité du texte sur les écrans LCD existants (affichages à cristaux liquides), tels que les écrans d’ordinateurs portables, les écrans de Pocket PC et les écrans plats. ClearType utilise le rendu de sous-pixel qui autorise l’affichage du texte avec une plus grande fidélité à sa forme réelle en alignant les caractères sur une partie fractionnaire d’un pixel. Cette résolution accrue augmente la netteté des détails dans l’affichage textuel, ce qui facilite grandement la lecture sur de longues périodes. Une autre amélioration de ClearType dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] est l’anticrénelage de direction y, qui lisse le haut et le bas des courbes superficielles dans les caractères de texte. Pour plus d’informations sur les fonctionnalités ClearType, consultez [vue d’ensemble de ClearType](cleartype-overview.md).  
  
 ![Texte avec anticrénelage ClearType dans la direction y](./media/typography-in-wpf/text-y-direction-antialiasing.gif)  
Texte avec anticrénelage ClearType dans la direction y  
  
 L’ensemble du pipeline de rendu de texte peut être accéléré par matériel dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], sous réserve que votre ordinateur respecte le niveau matériel minimum exigé. Un rendu ne pouvant pas être exécuté à l’aide de matériel repasse à un rendu logiciel. L’accélération matérielle affecte toutes les phases du pipeline de rendu de texte, du stockage des glyphes individuels, la composition des glyphes en séries de glyphes, l’application des effets, à l’application de l’algorithme de fusion ClearType à la sortie finale affichée. Pour plus d’informations sur l’accélération matérielle, consultez [Couches de rendu graphiques](graphics-rendering-tiers.md).  
  
 ![Diagramme du pipeline de rendu de texte](./media/typography-in-wpf/text-rendering-pipeline.png)  
  
 En outre, un texte animé, par caractères ou par glyphes, tire pleinement parti de la fonction de matériel graphique activée par [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Il en résulte une animation de texte lisse.  
  
<a name="Rich_Typography"></a>   
## <a name="rich-typography"></a>Typographie riche  
 Le format de police OpenType est une extension du format de police TrueType®. Le format de police OpenType a été développé conjointement par Microsoft et Adobe. il offre un large éventail de fonctionnalités typographiques avancées. L’objet <xref:System.Windows.Documents.Typography> expose un grand nombre des fonctionnalités avancées des polices OpenType, telles que les variantes stylistiques et les paraphes. Le SDK Windows fournit un ensemble d’exemples de polices OpenType conçues avec des fonctionnalités riches, telles que les polices Pericles et Pescadero. Pour plus d’informations, consultez [Exemple de pack de polices OpenType](sample-opentype-font-pack.md).  
  
 La police OpenType Pericles contient des glyphes supplémentaires qui fournissent des variantes stylistiques à l’ensemble de glyphes standard. Le texte suivant présente des glyphes de style alternatif.  
  
 ![Texte utilisant des glyphes de style alternatif OpenType](./media/typography-in-wpf/opentype-stylistic-alternate-glyphs.gif "Texte utilisant des glyphes de style alternatifs OpenType")  
  
 Les lettres ornées sont des glyphes décoratifs qui utilisent une ornementation élaborée souvent associée à la calligraphie. Le texte suivant présente des glyphes standard et des glyphes à lettres ornées avec la police Pescadero.  
  
 ![Texte utilisant des glyphes standard et ornés OpenType](./media/typography-in-wpf/opentype-standard-swash-glyphs.gif "Texte utilisant des glyphes standard et ornés OpenType")  
  
 Pour plus d’informations sur les fonctionnalités OpenType, consultez [caractéristiques des polices OpenType](opentype-font-features.md).  
  
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
  
- Séparer les types <xref:System.Windows.FontWeight>, <xref:System.Windows.FontStretch>et <xref:System.Windows.FontStyle> pour la définition d’un <xref:System.Windows.Media.FontFamily>. Cela offre une plus grande souplesse que dans la programmation Win32, dans laquelle les combinaisons booléennes d’italique et de gras sont utilisées pour définir une famille de polices.  
  
- Sens d’écriture (horizontal ou vertical) géré indépendamment du nom de police.  
  
- Liaison de polices et police de secours dans un fichier XML portable à l’aide de la technologie de police composite. Les polices composites permettent de générer une gamme complète de polices multilingues. Les polices composites fournissent également un mécanisme qui évite d’afficher les glyphes manquants. Pour plus d’informations, consultez les notes de la classe <xref:System.Windows.Media.FontFamily>.  
  
- Polices internationales générées à partir de polices composites, à l’aide d’un groupe de polices d’une seule langue. Cela permet de limiter les coûts de ressources lors du développement de polices pour plusieurs langues.  
  
- Polices composites incorporées dans un document, autorisant ainsi la portabilité du document. Pour plus d’informations, consultez les notes de la classe <xref:System.Windows.Media.FontFamily>.  
  
<a name="New_Text_APIs"></a>   
## <a name="new-text-application-programming-interfaces-apis"></a>Nouvelles interfaces de programmation d’applications (API) texte  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit plusieurs API de texte que les développeurs peuvent utiliser pour inclure du texte dans leurs applications. Ces API sont regroupées en trois catégories :  
  
- **Disposition et interface utilisateur**. Contrôles de texte courants pour l’interface utilisateur graphique (GUI).  
  
- **Dessin de texte léger**. Permet de dessiner du texte directement sur des objets.  
  
- **Mise en forme du texte avancée**. Permet d’implémenter un moteur de texte personnalisé.  
  
### <a name="layout-and-user-interface"></a>Disposition et interface utilisateur  
 Au plus haut niveau de fonctionnalité, les API de texte fournissent des contrôles de [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] communs tels que <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.TextBlock>et <xref:System.Windows.Controls.TextBox>. Ces contrôles fournissent les éléments [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] de base dans une application et proposent une méthode simple pour présenter le texte et interagir avec celui-ci. Les contrôles tels que <xref:System.Windows.Controls.RichTextBox> et <xref:System.Windows.Controls.PasswordBox> permettent une gestion de texte plus avancée ou spécialisée. Les classes et, telles que <xref:System.Windows.Documents.TextRange>, <xref:System.Windows.Documents.TextSelection>et <xref:System.Windows.Documents.TextPointer> permettent une manipulation de texte utile. Ces contrôles [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] fournissent des propriétés telles que <xref:System.Windows.Controls.Control.FontFamily%2A>, <xref:System.Windows.Controls.Control.FontSize%2A>et <xref:System.Windows.Controls.Control.FontStyle%2A>, qui vous permettent de contrôler la police utilisée pour restituer le texte.  
  
#### <a name="using-bitmap-effects-transforms-and-text-effects"></a>Utilisation d’effets bitmap, de transformations et d’effets de texte  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vous permet de créer des utilisations visuellement intéressantes de texte par le biais des fonctionnalités d’utilisation telles que les effets bitmap, les transformations et les effets de texte. L’exemple suivant présente un type classique d’effet d’ombre portée appliqué au texte.  
  
 ![Ombre du texte avec adoucissement &#61; 0,25](./media/typography-in-wpf/drop-shadow-text-effect.jpg) 
  
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
  
 Un objet <xref:System.Windows.Media.TextEffect> est un objet d’assistance qui vous permet de traiter le texte comme un ou plusieurs groupes de caractères dans une chaîne de texte. L’exemple suivant montre un caractère individuel qui fait l’objet d’une rotation. Chaque caractère fait indépendamment l’objet d’une rotation à intervalles d’une seconde.  
  
 ![Capture d'écran : effet de rotation du texte](./media/typography-in-wpf/rotating-text-effect.jpg) 
  
#### <a name="using-flow-documents"></a>Utilisation de documents dynamiques  
 Outre les contrôles de [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] courants, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] offre un contrôle de disposition pour la présentation de texte, l’élément <xref:System.Windows.Documents.FlowDocument>. L’élément <xref:System.Windows.Documents.FlowDocument>, conjointement avec l’élément <xref:System.Windows.Controls.DocumentViewer>, fournit un contrôle pour de grandes quantités de texte avec des exigences de disposition variables. Les contrôles de disposition fournissent un accès à la typographie avancée via l’objet <xref:System.Windows.Documents.Typography> et les propriétés liées à la police d’autres contrôles [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
 L’exemple suivant montre le contenu de texte hébergé dans une <xref:System.Windows.Controls.FlowDocumentReader>, qui fournit la prise en charge de la recherche, de la navigation, de la pagination et de la mise à l’échelle du contenu.  
  
 ![Capture d’écran montrant les polices OpenType.](./media/typography-in-wpf/typography-text-flowdocumentreader.png)
  
 Pour plus d’informations, consultez [Documents dans WPF](documents-in-wpf.md).  
  
### <a name="lightweight-text-drawing"></a>Dessin de texte léger  
 Vous pouvez dessiner du texte directement sur des objets [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] à l’aide de la méthode <xref:System.Windows.Media.DrawingContext.DrawText%2A> de l’objet <xref:System.Windows.Media.DrawingContext>. Pour utiliser cette méthode, vous créez un objet <xref:System.Windows.Media.FormattedText>. Cet objet vous permet de dessiner du texte multiligne dans lequel chaque caractère du texte peut être mis en forme individuellement. La fonctionnalité de l’objet <xref:System.Windows.Media.FormattedText> contient la plupart des fonctionnalités des indicateurs DrawText dans l’API Windows. En outre, l’objet <xref:System.Windows.Media.FormattedText> contient des fonctionnalités telles que la prise en charge des points de suspension, dans lesquelles des points de suspension s’affichent lorsque le texte dépasse ses limites. L’exemple suivant présente un texte auquel plusieurs formats sont appliqués, notamment un dégradé linéaire sur les deuxième et troisième mots.  
  
 ![Texte affiché à l'aide de l'objet FormattedText](./media/typography-in-wpf/text-formatted-linear-gradient.jpg) 
  
 Vous pouvez convertir du texte mis en forme en objets <xref:System.Windows.Media.Geometry>, ce qui vous permet de créer d’autres types de texte visuellement intéressant. Par exemple, vous pouvez créer un objet <xref:System.Windows.Media.Geometry> basé sur le contour d’une chaîne de texte.  
  
 ![Contour du texte utilisant un pinceau de dégradé linéaire](./media/typography-in-wpf/text-outline-linear-gradient.jpg)  
  
 Les exemples suivants illustrent plusieurs façons de créer des effets visuels intéressants en modifiant le trait, le remplissage et la surbrillance du texte converti.  
  
 ![Texte avec différentes couleurs de trait et de remplissage](./media/typography-in-wpf/fill-stroke-text-effect.jpg)  
  
 ![Texte avec pinceau image appliqué au trait](./media/typography-in-wpf/image-brush-application.jpg)
  
 ![Texte avec pinceau d’image appliqué au trait et à la mise en surbrillance](./media/typography-in-wpf/image-brush-text-application.jpg)
  
 Pour plus d’informations sur l’objet <xref:System.Windows.Media.FormattedText>, consultez [dessin du texte mis en forme](drawing-formatted-text.md).  
  
### <a name="advanced-text-formatting"></a>Mise en forme de texte avancée  
 Au niveau le plus avancé des API Text, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vous permet de créer une disposition de texte personnalisée à l’aide de l’objet <xref:System.Windows.Media.TextFormatting.TextFormatter> et d’autres types dans l’espace de noms <xref:System.Windows.Media.TextFormatting>. Les classes <xref:System.Windows.Media.TextFormatting.TextFormatter> et associées vous permettent d’implémenter une disposition de texte personnalisée qui prend en charge votre propre définition de formats de caractères, de styles de paragraphes, de règles de saut de ligne et d’autres fonctionnalités de disposition pour le texte international. Dans certains cas, vous pouvez être amené à remplacer l’implémentation par défaut de la prise en charge de la disposition du texte [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Toutefois, si vous créez une application ou un contrôle d’édition de texte, vous aurez peut-être besoin d’une implémentation différente de l’implémentation [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] par défaut.  
  
 Contrairement à une API texte traditionnelle, le <xref:System.Windows.Media.TextFormatting.TextFormatter> interagit avec un client de disposition de texte par le biais d’un ensemble de méthodes de rappel. Elle requiert que le client fournisse ces méthodes dans une implémentation de la classe <xref:System.Windows.Media.TextFormatting.TextSource>. Le diagramme suivant illustre l’interaction de la disposition du texte entre l’application cliente et <xref:System.Windows.Media.TextFormatting.TextFormatter>.  
  
 ![Diagramme du client de disposition du texte et TextFormatter](./media/typography-in-wpf/text-layout-text-formatter-interaction.png)  
  
 Pour plus d’informations sur la création de la disposition de texte personnalisée, consultez [Mise en forme de texte avancée](advanced-text-formatting.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Media.FormattedText>
- <xref:System.Windows.Media.TextFormatting.TextFormatter>
- [Vue d’ensemble ClearType](cleartype-overview.md)
- [Fonctionnalités des polices OpenType](opentype-font-features.md)
- [Dessin du texte mis en forme](drawing-formatted-text.md)
- [Mise en forme de texte avancée](advanced-text-formatting.md)
- [Text](optimizing-performance-text.md)
- [Typographie Microsoft](https://docs.microsoft.com/typography/)
