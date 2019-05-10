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
ms.openlocfilehash: f8931e26d4c4f3cc52ecb838062d2e1beda74baf
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64598831"
---
# <a name="introduction-to-the-glyphrun-object-and-glyphs-element"></a>Introduction à l'objet GlyphRun et à l'élément Glyphs
Cette rubrique décrit la <xref:System.Windows.Media.GlyphRun> objet et le <xref:System.Windows.Documents.Glyphs> élément.  

<a name="text_glyphrunovw_intro"></a>   
## <a name="introduction-to-glyphrun"></a>Introduction à GlyphRun  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Fournit la prise en charge de texte avancée, y compris le balisage au niveau du glyphe avec accès direct à <xref:System.Windows.Documents.Glyphs> pour les clients qui souhaitent intercepter et rendre le texte persistant après la mise en forme. Ces fonctionnalités assurent une prise en charge critique pour les différentes spécifications de rendu de texte propres à chacun des scénarios suivants.  
  
1. Affichage à l’écran de documents de format fixe.  
  
2. Scénarios d’impression.  
  
    - [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] comme langage d’imprimante.  
  
    - [!INCLUDE[TLA#tla_mxdw](../../../../includes/tlasharptla-mxdw-md.md)].  
  
    - Pilotes d’imprimante précédents, sortie d’applications [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] au format fixe.  
  
    - Format de spouleur d’impression.  
  
3. Représentation sous forme de document de format fixe, notamment des clients pour des versions précédentes de [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] et autres appareils informatiques.  
  
> [!NOTE]
>  <xref:System.Windows.Documents.Glyphs> et <xref:System.Windows.Media.GlyphRun> sont conçus pour la présentation de documents à format fixe et les scénarios d’impression. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fournit plusieurs éléments pour la présentation générale et [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] scénarios comme <xref:System.Windows.Controls.Label> et <xref:System.Windows.Controls.TextBlock>. Pour plus d’informations sur les scénarios de disposition et d’[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], consultez [Typographie dans WPF](typography-in-wpf.md).  
  
<a name="text_glyphrunovw_glyphrunobject"></a>   
## <a name="the-glyphrun-object"></a>Objet GlyphRun  
 Le <xref:System.Windows.Media.GlyphRun> objet représente une séquence de glyphes à partir d’un type unique d’une police unique à une taille unique et avec un style de rendu unique.  
  
 <xref:System.Windows.Media.GlyphRun> inclut les détails de la police, tels que glyphe <xref:System.Windows.Documents.Glyphs.Indices%2A> et les positions de chaque glyphe. Il inclut également la version d’origine [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] l’exécution a été générée à partir des informations de mappage offset de mémoire tampon du caractère au glyphe et les indicateurs par caractère et par glyphe de points de code.  
  
 <xref:System.Windows.Media.GlyphRun> associé à un haut niveau <xref:System.Windows.FrameworkElement>, <xref:System.Windows.Documents.Glyphs>. <xref:System.Windows.Documents.Glyphs> peut être utilisé dans l’arborescence d’éléments et dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] balisage pour représenter <xref:System.Windows.Media.GlyphRun> sortie.  
  
<a name="text_glyphrunovw_glyphselement"></a>   
## <a name="the-glyphs-element"></a>Élément Glyphs  
 Le <xref:System.Windows.Documents.Glyphs> élément représente la sortie d’un <xref:System.Windows.Media.GlyphRun> dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. La syntaxe de balisage suivant est utilisée pour décrire le <xref:System.Windows.Documents.Glyphs> élément.  
  
 [!code-xaml[GlyphsOvwSample1#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSample1/CS/default.xaml#1)]  
  
 Les définitions de propriétés suivantes correspondent aux quatre premiers attributs de l’exemple de balisage.  
  
|Propriété|Description|  
|--------------|-----------------|  
|<xref:System.Windows.Documents.Glyphs.FontUri%2A>|Spécifie un identificateur de ressource : nom de fichier, Web [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)], ou référence de ressource dans l’application .exe ou le conteneur.|  
|<xref:System.Windows.Documents.Glyphs.FontRenderingEmSize%2A>|Spécifie la taille de police en unités de surface de dessin (la valeur par défaut est 0,96 pouce).|  
|<xref:System.Windows.Documents.Glyphs.StyleSimulations%2A>|Spécifie les indicateurs des styles gras et italique.|  
|<xref:System.Windows.Documents.Glyphs.BidiLevel%2A>|Spécifie le niveau de disposition bidirectionnelle. Les valeurs paires et nulles impliquent une disposition de gauche à droite ; les valeurs impaires impliquent une disposition de droite à gauche.|  
  
<a name="text_glyphrunovw_indicesproperty"></a>   
### <a name="indices-property"></a>Propriété Indices  
 Le <xref:System.Windows.Documents.Glyphs.Indices%2A> propriété est une chaîne de spécifications de glyphe. Quand une séquence de glyphes forme un groupement unique, la spécification du premier glyphe du groupement est précédée d’une spécification qui indique le nombre de glyphes et de points de code qui se combinent pour former le regroupement. Le <xref:System.Windows.Documents.Glyphs.Indices%2A> propriété collecte dans une chaîne les propriétés suivantes.  
  
- Index de glyphe  
  
- Largeurs d’avance de glyphe  
  
- Combinaison de vecteurs d’attachement de glyphe  
  
- Mappage de groupement des points de code aux glyphes  
  
- Indicateurs de glyphe  
  
 Chaque spécification de glyphe présente la forme suivante.  
  
 `[GlyphIndex][,[Advance][,[uOffset][,[vOffset][,[Flags]]]]]`  
  
<a name="text_glyphrunovw_glyphmetrics"></a>   
## <a name="glyph-metrics"></a>Métriques de glyphe  
 Chaque glyphe définit des métriques qui spécifient comment il s’aligne avec d’autres <xref:System.Windows.Documents.Glyphs>. Le graphique suivant définit les diverses qualités typographiques de deux glyphes de caractères différents.  
  
 ![Diagramme des mesures de glyphe](./media/glyph-example.png "glyph_example")  
  
<a name="text_glyphrunovw_glyphsmarkup"></a>   
## <a name="glyphs-markup"></a>Balisage Glyphs  
 L’exemple de code suivant montre comment utiliser diverses propriétés de la <xref:System.Windows.Documents.Glyphs> élément [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 [!code-xaml[GlyphsOvwSamp2#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSamp2/CS/default.xaml#1)]  
  
## <a name="see-also"></a>Voir aussi

- [Typographie dans WPF](typography-in-wpf.md)
- [Documents dans WPF](documents-in-wpf.md)
- [Text](optimizing-performance-text.md)
