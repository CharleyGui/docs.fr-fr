---
title: Introduction à l'objet GlyphRun et à l'élément Glyphs
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], Glyphs element
- Glyphs elements [WPF]
- GlyphRun object [WPF]
- text [WPF], glyphs
- glyphs [WPF]
- typography [WPF], GlyphRun object
ms.assetid: 746ca769-a331-4435-9b95-f72a883b67c1
ms.openlocfilehash: 5b1fd9c6e12a3dbea6de939ee90c48df716bd265
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395813"
---
# <a name="introduction-to-the-glyphrun-object-and-glyphs-element"></a>Introduction à l'objet GlyphRun et à l'élément Glyphs
Cette rubrique décrit l’objet <xref:System.Windows.Media.GlyphRun> et l’élément <xref:System.Windows.Documents.Glyphs>.  

<a name="text_glyphrunovw_intro"></a>   
## <a name="introduction-to-glyphrun"></a>Introduction à GlyphRun  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] offre une prise en charge de texte avancée, notamment le balisage au niveau du glyphe avec un accès direct à <xref:System.Windows.Documents.Glyphs> pour les clients qui souhaitent intercepter et conserver du texte après la mise en forme. Ces fonctionnalités offrent une prise en charge critique pour les différentes spécifications de rendu de texte propres à chacun des scénarios suivants.  
  
1. Affichage à l’écran de documents de format fixe.  
  
2. Scénarios d’impression.  
  
    - [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] comme langage d’imprimante.  
  
    - Microsoft XPS document Writer.  
  
    - Pilotes d’imprimante précédents, sortie d’applications [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] au format fixe.  
  
    - Format de spouleur d’impression.  
  
3. Représentation de document de format fixe, y compris les clients des versions antérieures de Windows et d’autres appareils informatiques.  
  
> [!NOTE]
> <xref:System.Windows.Documents.Glyphs> et <xref:System.Windows.Media.GlyphRun> sont conçus pour les scénarios de présentation et d’impression de documents de format fixe. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fournit plusieurs éléments pour les scénarios de mise en page générale et de [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)], tels que <xref:System.Windows.Controls.Label> et <xref:System.Windows.Controls.TextBlock>. Pour plus d’informations sur les scénarios de disposition et d’[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], consultez [Typographie dans WPF](typography-in-wpf.md).  
  
<a name="text_glyphrunovw_glyphrunobject"></a>   
## <a name="the-glyphrun-object"></a>Objet GlyphRun  
 L’objet <xref:System.Windows.Media.GlyphRun> représente une séquence de glyphes d’une seule face d’une police unique à une seule taille, avec un style de rendu unique.  
  
 <xref:System.Windows.Media.GlyphRun> comprend les détails de la police, tels que le glyphe <xref:System.Windows.Documents.Glyphs.Indices%2A> et les positions des glyphes individuels. Il comprend également les points de code Unicode d’origine à partir desquels la série a été générée, les informations de mappage de décalage de la mémoire tampon de caractère à glyphe et les indicateurs par caractère et par glyphe.  
  
 <xref:System.Windows.Media.GlyphRun> a un <xref:System.Windows.FrameworkElement> de haut niveau correspondant <xref:System.Windows.Documents.Glyphs>. <xref:System.Windows.Documents.Glyphs> peut être utilisé dans l’arborescence d’éléments et dans le balisage [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pour représenter la sortie de <xref:System.Windows.Media.GlyphRun>.  
  
<a name="text_glyphrunovw_glyphselement"></a>   
## <a name="the-glyphs-element"></a>Élément Glyphs  
 L’élément <xref:System.Windows.Documents.Glyphs> représente la sortie d’une <xref:System.Windows.Media.GlyphRun> dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. La syntaxe de balisage suivante est utilisée pour décrire l’élément <xref:System.Windows.Documents.Glyphs>.  
  
 [!code-xaml[GlyphsOvwSample1#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSample1/CS/default.xaml#1)]  
  
 Les définitions de propriétés suivantes correspondent aux quatre premiers attributs de l’exemple de balisage.  
  
|Property|Description|  
|--------------|-----------------|  
|<xref:System.Windows.Documents.Glyphs.FontUri%2A>|Spécifie un identificateur de ressource : nom de fichier, @no__t Web-0 ou référence de ressource dans l’application. exe ou le conteneur.|  
|<xref:System.Windows.Documents.Glyphs.FontRenderingEmSize%2A>|Spécifie la taille de police en unités de surface de dessin (la valeur par défaut est 0,96 pouce).|  
|<xref:System.Windows.Documents.Glyphs.StyleSimulations%2A>|Spécifie les indicateurs des styles gras et italique.|  
|<xref:System.Windows.Documents.Glyphs.BidiLevel%2A>|Spécifie le niveau de disposition bidirectionnelle. Les valeurs paires et nulles impliquent une disposition de gauche à droite ; les valeurs impaires impliquent une disposition de droite à gauche.|  
  
<a name="text_glyphrunovw_indicesproperty"></a>   
### <a name="indices-property"></a>Propriété Indices  
 La propriété <xref:System.Windows.Documents.Glyphs.Indices%2A> est une chaîne de spécifications de glyphe. Quand une séquence de glyphes forme un groupement unique, la spécification du premier glyphe du groupement est précédée d’une spécification qui indique le nombre de glyphes et de points de code qui se combinent pour former le regroupement. La propriété <xref:System.Windows.Documents.Glyphs.Indices%2A> collecte dans une chaîne les propriétés suivantes.  
  
- Index de glyphe  
  
- Largeurs d’avance de glyphe  
  
- Combinaison de vecteurs d’attachement de glyphe  
  
- Mappage de groupement des points de code aux glyphes  
  
- Indicateurs de glyphe  
  
 Chaque spécification de glyphe présente la forme suivante.  
  
 `[GlyphIndex][,[Advance][,[uOffset][,[vOffset][,[Flags]]]]]`  
  
<a name="text_glyphrunovw_glyphmetrics"></a>   
## <a name="glyph-metrics"></a>Métriques de glyphe  
 Chaque glyphe définit des mesures qui spécifient la façon dont il s’aligne avec d’autres <xref:System.Windows.Documents.Glyphs>. Le graphique suivant définit les diverses qualités typographiques de deux glyphes de caractères différents.  
  
 ![Diagramme de mesures de glyphe](./media/glyph-example.png "glyph_example")  
  
<a name="text_glyphrunovw_glyphsmarkup"></a>   
## <a name="glyphs-markup"></a>Balisage Glyphs  
 L’exemple de code suivant montre comment utiliser les différentes propriétés de l’élément <xref:System.Windows.Documents.Glyphs> dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 [!code-xaml[GlyphsOvwSamp2#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSamp2/CS/default.xaml#1)]  
  
## <a name="see-also"></a>Voir aussi

- [Typographie dans WPF](typography-in-wpf.md)
- [Documents dans WPF](documents-in-wpf.md)
- [Texte](optimizing-performance-text.md)
