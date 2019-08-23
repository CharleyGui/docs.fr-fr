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
ms.openlocfilehash: 9e40a9656bd1d89203b167860ef6951d5e30377c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918395"
---
# <a name="introduction-to-the-glyphrun-object-and-glyphs-element"></a>Introduction à l'objet GlyphRun et à l'élément Glyphs
Cette rubrique décrit l' <xref:System.Windows.Media.GlyphRun> objet et l' <xref:System.Windows.Documents.Glyphs> élément.  

<a name="text_glyphrunovw_intro"></a>   
## <a name="introduction-to-glyphrun"></a>Introduction à GlyphRun  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]fournit une prise en charge de texte avancée, notamment le balisage <xref:System.Windows.Documents.Glyphs> au niveau du glyphe avec un accès direct à pour les clients qui souhaitent intercepter et conserver du texte après la mise en forme. Ces fonctionnalités assurent une prise en charge critique pour les différentes spécifications de rendu de texte propres à chacun des scénarios suivants.  
  
1. Affichage à l’écran de documents de format fixe.  
  
2. Scénarios d’impression.  
  
    - [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] comme langage d’imprimante.  
  
    - Microsoft XPS document Writer.  
  
    - Pilotes d’imprimante précédents, sortie d’applications [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] au format fixe.  
  
    - Format de spouleur d’impression.  
  
3. Représentation de document de format fixe, y compris les clients des versions antérieures de Windows et d’autres appareils informatiques.  
  
> [!NOTE]
> <xref:System.Windows.Documents.Glyphs>et <xref:System.Windows.Media.GlyphRun> sont conçus pour des scénarios de présentation et d’impression de documents de format fixe. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]fournit plusieurs éléments pour la mise en [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] page générale et <xref:System.Windows.Controls.Label> les <xref:System.Windows.Controls.TextBlock>scénarios tels que et. Pour plus d’informations sur les scénarios de disposition et d’[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], consultez [Typographie dans WPF](typography-in-wpf.md).  
  
<a name="text_glyphrunovw_glyphrunobject"></a>   
## <a name="the-glyphrun-object"></a>Objet GlyphRun  
 L' <xref:System.Windows.Media.GlyphRun> objet représente une séquence de glyphes d’une seule face d’une police unique à une seule taille, avec un style de rendu unique.  
  
 <xref:System.Windows.Media.GlyphRun>comprend les détails de la police, <xref:System.Windows.Documents.Glyphs.Indices%2A> tels que les positions de glyphe et de glyphes individuels. Il comprend également les points [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] de code d’origine à partir desquels la série a été générée, les informations de mappage de décalage de la mémoire tampon de caractère à glyphe et les indicateurs par caractère et par glyphe.  
  
 <xref:System.Windows.Media.GlyphRun>a un de haut niveau <xref:System.Windows.FrameworkElement> <xref:System.Windows.Documents.Glyphs>correspondant. <xref:System.Windows.Documents.Glyphs>peut être utilisé dans l’arborescence d’éléments et [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dans le balisage pour représenter <xref:System.Windows.Media.GlyphRun> la sortie.  
  
<a name="text_glyphrunovw_glyphselement"></a>   
## <a name="the-glyphs-element"></a>Élément Glyphs  
 L' <xref:System.Windows.Documents.Glyphs> élément représente la sortie d’un <xref:System.Windows.Media.GlyphRun> dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. La syntaxe de balisage suivante est utilisée pour <xref:System.Windows.Documents.Glyphs> décrire l’élément.  
  
 [!code-xaml[GlyphsOvwSample1#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSample1/CS/default.xaml#1)]  
  
 Les définitions de propriétés suivantes correspondent aux quatre premiers attributs de l’exemple de balisage.  
  
|Propriété|Description|  
|--------------|-----------------|  
|<xref:System.Windows.Documents.Glyphs.FontUri%2A>|Spécifie un identificateur de ressource: nom de fichier [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)], Web ou référence de ressource dans le fichier application. exe ou le conteneur.|  
|<xref:System.Windows.Documents.Glyphs.FontRenderingEmSize%2A>|Spécifie la taille de police en unités de surface de dessin (la valeur par défaut est 0,96 pouce).|  
|<xref:System.Windows.Documents.Glyphs.StyleSimulations%2A>|Spécifie les indicateurs des styles gras et italique.|  
|<xref:System.Windows.Documents.Glyphs.BidiLevel%2A>|Spécifie le niveau de disposition bidirectionnelle. Les valeurs paires et nulles impliquent une disposition de gauche à droite ; les valeurs impaires impliquent une disposition de droite à gauche.|  
  
<a name="text_glyphrunovw_indicesproperty"></a>   
### <a name="indices-property"></a>Propriété Indices  
 La <xref:System.Windows.Documents.Glyphs.Indices%2A> propriété est une chaîne de spécifications de glyphe. Quand une séquence de glyphes forme un groupement unique, la spécification du premier glyphe du groupement est précédée d’une spécification qui indique le nombre de glyphes et de points de code qui se combinent pour former le regroupement. La <xref:System.Windows.Documents.Glyphs.Indices%2A> propriété collecte dans une chaîne les propriétés suivantes.  
  
- Index de glyphe  
  
- Largeurs d’avance de glyphe  
  
- Combinaison de vecteurs d’attachement de glyphe  
  
- Mappage de groupement des points de code aux glyphes  
  
- Indicateurs de glyphe  
  
 Chaque spécification de glyphe présente la forme suivante.  
  
 `[GlyphIndex][,[Advance][,[uOffset][,[vOffset][,[Flags]]]]]`  
  
<a name="text_glyphrunovw_glyphmetrics"></a>   
## <a name="glyph-metrics"></a>Métriques de glyphe  
 Chaque glyphe définit des mesures qui spécifient la façon dont il s' <xref:System.Windows.Documents.Glyphs>aligne avec l’autre. Le graphique suivant définit les diverses qualités typographiques de deux glyphes de caractères différents.  
  
 ![Diagramme des mesures de glyphe](./media/glyph-example.png "glyph_example")  
  
<a name="text_glyphrunovw_glyphsmarkup"></a>   
## <a name="glyphs-markup"></a>Balisage Glyphs  
 L’exemple de code suivant montre comment utiliser les différentes propriétés de <xref:System.Windows.Documents.Glyphs> l’élément [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]dans.  
  
 [!code-xaml[GlyphsOvwSamp2#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSamp2/CS/default.xaml#1)]  
  
## <a name="see-also"></a>Voir aussi

- [Typographie dans WPF](typography-in-wpf.md)
- [Documents dans WPF](documents-in-wpf.md)
- [Text](optimizing-performance-text.md)
