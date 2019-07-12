---
title: Typographie dans WPF
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], about typography
ms.assetid: 06cbf17b-6eff-4fe5-949d-2dd533e4e1f4
ms.openlocfilehash: 94937b2c3e6935474d337c62bfd6698441dfcc2e
ms.sourcegitcommit: 83ecdf731dc1920bca31f017b1556c917aafd7a0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/12/2019
ms.locfileid: "67860111"
---
# <a name="typography-in-wpf"></a>Typographie dans WPF
Cette rubrique présente les principales fonctionnalités typographiques de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Ces fonctionnalités incluent l’amélioration de la qualité et des performances de rendu de texte, une prise en charge de la typographie [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)], un texte international amélioré, une prise en charge de police améliorée et de nouvelles interfaces de programmation d’applications (API, Application Programming Interface) texte.  
  
<a name="Improved_Quality_and_Performance_of_Text"></a>   
## <a name="improved-quality-and-performance-of-text"></a>Amélioration de la qualité et des performances du texte  
 Le texte dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] est affiché à l’aide de [!INCLUDE[TLA#tla_ct](../../../../includes/tlasharptla-ct-md.md)], ce qui améliore sa clarté et sa lisibilité. [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] est une technologie logicielle développée par [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] qui améliore la lisibilité du texte sur les écrans LCD existants, tels que les écrans d’ordinateurs portables, les écrans de Pocket PC et les écrans plats. [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] utilise un rendu d’une précision inférieure au pixel qui permet l’affichage du texte avec une fidélité supérieure à sa forme réelle en alignant les caractères sur une fraction d’un pixel. Cette résolution accrue augmente la netteté des détails dans l’affichage textuel, ce qui facilite grandement la lecture pendant des périodes prolongées. Parmi les autres améliorations de [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], citons l’anticrénelage de direction y qui lisse le haut et le bas des courbes superficielles dans les caractères de texte. Pour plus d’informations sur les fonctionnalités [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)], consultez [Vue d’ensemble de ClearType](cleartype-overview.md).  
  
 ![Texte avec anticrénelage ClearType dans la direction y](./media/typography-in-wpf/text-y-direction-antialiasing.gif)  
Texte avec anticrénelage ClearType dans la direction y  
  
 L’ensemble du pipeline de rendu de texte peut être accéléré par matériel dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], sous réserve que votre ordinateur respecte le niveau matériel minimum exigé. Un rendu ne pouvant pas être exécuté à l’aide de matériel repasse à un rendu logiciel. L’accélération matérielle affecte toutes les phases du pipeline de rendu de texte, du stockage de glyphes individuels à l’application de l’algorithme de fusion [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] à la sortie finale affichée, en passant par la constitution de glyphes en exécutions de glyphes et l’application d’effets. Pour plus d’informations sur l’accélération matérielle, consultez [Couches de rendu graphiques](graphics-rendering-tiers.md).  
  
 ![Diagramme du pipeline de rendu de texte](./media/typography-in-wpf/text-rendering-pipeline.png)  
  
 En outre, un texte animé, par caractères ou par glyphes, tire pleinement parti de la fonction de matériel graphique activée par [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Il en résulte une animation de texte lisse.  
  
<a name="Rich_Typography"></a>   
## <a name="rich-typography"></a>Typographie riche  
 Le format de police [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] est une extension du format de police [!INCLUDE[TLA#tla_truetype](../../../../includes/tlasharptla-truetype-md.md)]. Le format de police [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)], développé conjointement par [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] et Adobe, offre un large éventail de fonctionnalités typographiques avancées. Le <xref:System.Windows.Documents.Typography> objet expose de nombreuses fonctionnalités avancées de [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] polices, telles que le format de remplaçants stylistiques et les lettres ornées. Le [!INCLUDE[TLA2#tla_lhsdk](../../../../includes/tla2sharptla-lhsdk-md.md)] fournit un jeu d’exemples de polices [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] conçues avec des fonctionnalités riches, telles que les polices Pericles et Pescadero. Pour plus d’informations, consultez [Exemple de pack de polices OpenType](sample-opentype-font-pack.md).  
  
 La police [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] Pericles contient des glyphes supplémentaires qui représentent des variantes stylistiques au jeu de glyphes standard. Le texte suivant présente des glyphes de style alternatif.  
  
 ![Texte utilisant des glyphes de substitution OpenType](./media/typography-in-wpf/opentype-stylistic-alternate-glyphs.gif "texte utilisant des glyphes de substitution OpenType")  
  
 Les lettres ornées sont des glyphes décoratifs qui utilisent une ornementation élaborée souvent associée à la calligraphie. Le texte suivant présente des glyphes standard et des glyphes à lettres ornées avec la police Pescadero.  
  
 ![Texte utilisant des glyphes standard et ornés OpenType](./media/typography-in-wpf/opentype-standard-swash-glyphs.gif "texte utilisant des glyphes standard et ornés OpenType")  
  
 Pour plus d’informations sur les fonctionnalités [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)], consultez [Fonctionnalités des polices OpenType](opentype-font-features.md).  
  
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
  
- Distinct <xref:System.Windows.FontWeight>, <xref:System.Windows.FontStretch>, et <xref:System.Windows.FontStyle> types permettant de définir un <xref:System.Windows.Media.FontFamily>. Cette fonctionnalité offre une souplesse plus importante que dans la programmation [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)], dans laquelle des combinaisons Boolean de caractères italiques et gras sont utilisées pour définir une famille de polices.  
  
- Sens d’écriture (horizontal ou vertical) géré indépendamment du nom de police.  
  
- Police de liaison et police de substitution dans un fichier [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] portable, à l’aide de la technologie de police composite. Les polices composites permettent de générer une gamme complète de polices multilingues. Les polices composites fournissent également un mécanisme qui évite d’afficher les glyphes manquants. Pour plus d’informations, consultez la section Notes dans la <xref:System.Windows.Media.FontFamily> classe.  
  
- Polices internationales générées à partir de polices composites, à l’aide d’un groupe de polices d’une seule langue. Cela permet de limiter les coûts de ressources lors du développement de polices pour plusieurs langues.  
  
- Polices composites incorporées dans un document, autorisant ainsi la portabilité du document. Pour plus d’informations, consultez la section Notes dans la <xref:System.Windows.Media.FontFamily> classe.  
  
<a name="New_Text_APIs"></a>   
## <a name="new-text-application-programming-interfaces-apis"></a>Nouvelles interfaces de programmation d’applications (API) texte  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit le texte de plusieurs API pour les développeurs à utiliser lors de l’inclure du texte dans leurs applications. Ces API est regroupées en trois catégories :  
  
- **Disposition et interface utilisateur**. Contrôles de texte courants pour l’interface graphique utilisateur ([!INCLUDE[TLA#tla_gui](../../../../includes/tlasharptla-gui-md.md)]).  
  
- **Dessin de texte léger**. Permet de dessiner du texte directement sur des objets.  
  
- **Mise en forme du texte avancée**. Permet d’implémenter un moteur de texte personnalisé.  
  
### <a name="layout-and-user-interface"></a>Disposition et interface utilisateur  
 Niveau le plus élevé de fonctionnalités, le texte API fournissent commun [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] contrôles tels que <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.TextBlock>, et <xref:System.Windows.Controls.TextBox>. Ces contrôles fournissent les éléments [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] de base dans une application et proposent une méthode simple pour présenter le texte et interagir avec celui-ci. Les contrôles tels que <xref:System.Windows.Controls.RichTextBox> et <xref:System.Windows.Controls.PasswordBox> activer plus avancée ou spécialisée de la gestion du texte. Les classes telles que <xref:System.Windows.Documents.TextRange>, <xref:System.Windows.Documents.TextSelection>, et <xref:System.Windows.Documents.TextPointer> activer manipulation utile du texte. Ces [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] contrôles fournissent des propriétés telles que <xref:System.Windows.Controls.Control.FontFamily%2A>, <xref:System.Windows.Controls.Control.FontSize%2A>, et <xref:System.Windows.Controls.Control.FontStyle%2A>, qui permettent de contrôler la police qui est utilisée pour restituer le texte.  
  
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
  
 Un <xref:System.Windows.Media.TextEffect> objet est un objet d’assistance qui vous permet de traiter le texte comme un ou plusieurs groupes de caractères dans une chaîne de texte. L’exemple suivant montre un caractère individuel qui fait l’objet d’une rotation. Chaque caractère fait indépendamment l’objet d’une rotation à intervalles d’une seconde.  
  
 ![Capture d'écran : effet de rotation du texte](./media/typography-in-wpf/rotating-text-effect.jpg) 
  
#### <a name="using-flow-documents"></a>Utilisation de documents dynamiques  
 En plus courantes [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] contrôles, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] offre un contrôle de disposition pour la présentation de texte : le <xref:System.Windows.Documents.FlowDocument> élément. Le <xref:System.Windows.Documents.FlowDocument> élément, conjointement avec le <xref:System.Windows.Controls.DocumentViewer> élément, fournit un contrôle pour les grandes quantités de texte avec diverses spécifications de disposition. Contrôles de disposition donnent accès à une typographie avancée via la <xref:System.Windows.Documents.Typography> objet et les propriétés de police des autres [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] contrôles.  
  
 L’exemple suivant montre le contenu de texte hébergé dans un <xref:System.Windows.Controls.FlowDocumentReader>, qui fournit la recherche, la navigation, la pagination et mise à l’échelle prise en charge de contenu.  
  
 ![Capture d’écran montrant des polices OpenType.](./media/typography-in-wpf/typography-text-flowdocumentreader.png)
  
 Pour plus d’informations, consultez [Documents dans WPF](documents-in-wpf.md).  
  
### <a name="lightweight-text-drawing"></a>Dessin de texte léger  
 Vous pouvez dessiner du texte directement à [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] objets à l’aide de la <xref:System.Windows.Media.DrawingContext.DrawText%2A> méthode de la <xref:System.Windows.Media.DrawingContext> objet. Pour utiliser cette méthode, vous créez un <xref:System.Windows.Media.FormattedText> objet. Cet objet vous permet de dessiner du texte multiligne dans lequel chaque caractère du texte peut être mis en forme individuellement. Les fonctionnalités de la <xref:System.Windows.Media.FormattedText> objet contient la plupart des fonctionnalités des indicateurs DrawText dans l’API Windows. En outre, le <xref:System.Windows.Media.FormattedText> objet contient des fonctionnalités telles que la prise en charge des points de suspension, dans lequel les points de suspension s’affiche lorsque le texte dépasse les limites. L’exemple suivant présente un texte auquel plusieurs formats sont appliqués, notamment un dégradé linéaire sur les deuxième et troisième mots.  
  
 ![Texte affiché à l'aide de l'objet FormattedText](./media/typography-in-wpf/text-formatted-linear-gradient.jpg) 
  
 Vous pouvez convertir le texte mis en forme dans <xref:System.Windows.Media.Geometry> objets, ce qui vous permet de créer d’autres types de texte présentant un intérêt visuel. Par exemple, vous pouvez créer un <xref:System.Windows.Media.Geometry> objet basé sur le contour d’une chaîne de texte.  
  
 ![Contour du texte utilisant un pinceau de dégradé linéaire](./media/typography-in-wpf/text-outline-linear-gradient.jpg)  
  
 Les exemples suivants illustrent plusieurs façons de créer des effets visuels intéressants en modifiant le trait, le remplissage et la surbrillance du texte converti.  
  
 ![Texte avec différentes couleurs de trait et de remplissage](./media/typography-in-wpf/fill-stroke-text-effect.jpg)  
  
 ![Texte avec pinceau image appliqué au trait](./media/typography-in-wpf/image-brush-application.jpg)
  
 ![Texte avec pinceau image appliqué pour tracer et mettre en surbrillance](./media/typography-in-wpf/image-brush-text-application.jpg)
  
 Pour plus d’informations sur la <xref:System.Windows.Media.FormattedText> d’objets, consultez [dessin du texte mis en forme](drawing-formatted-text.md).  
  
### <a name="advanced-text-formatting"></a>Mise en forme de texte avancée  
 Au niveau le plus avancé de l’API, texte [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vous offre la possibilité de créer la disposition de texte personnalisée à l’aide de la <xref:System.Windows.Media.TextFormatting.TextFormatter> objet et autres types dans le <xref:System.Windows.Media.TextFormatting> espace de noms. Le <xref:System.Windows.Media.TextFormatting.TextFormatter> et autoriser les classes associées vous permettent d’implémenter la disposition de texte personnalisée qui prend en charge votre propre définition des formats de caractère, styles de paragraphe, règles de saut de ligne et autres fonctionnalités de disposition pour le texte international. Dans certains cas, vous pouvez être amené à remplacer l’implémentation par défaut de la prise en charge de la disposition du texte [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Toutefois, si vous créez une application ou un contrôle d’édition de texte, vous aurez peut-être besoin d’une implémentation différente de l’implémentation [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] par défaut.  
  
 Contrairement à un texte traditionnelle [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)], le <xref:System.Windows.Media.TextFormatting.TextFormatter> interagit avec un client de disposition de texte via un ensemble de méthodes de rappel. Il nécessite le client fournisse ces méthodes dans une implémentation de la <xref:System.Windows.Media.TextFormatting.TextSource> classe. Le diagramme suivant illustre l’interaction de mise en page de texte entre l’application cliente et <xref:System.Windows.Media.TextFormatting.TextFormatter>.  
  
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
