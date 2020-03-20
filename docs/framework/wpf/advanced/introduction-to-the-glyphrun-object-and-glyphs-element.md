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
ms.openlocfilehash: 32e8ab7104b8ea2f985395065868ed154ca1e378
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181964"
---
# <a name="introduction-to-the-glyphrun-object-and-glyphs-element"></a>Introduction à l'objet GlyphRun et à l'élément Glyphs
Ce sujet décrit <xref:System.Windows.Media.GlyphRun> l’objet et l’élément. <xref:System.Windows.Documents.Glyphs>  

<a name="text_glyphrunovw_intro"></a>
## <a name="introduction-to-glyphrun"></a>Introduction à GlyphRun  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]fournit un support texte avancé, y compris la <xref:System.Windows.Documents.Glyphs> balisage au niveau du glyph, avec un accès direct aux clients qui veulent intercepter et persister le texte après le formatage. Ces fonctionnalités assurent une prise en charge critique pour les différentes spécifications de rendu de texte propres à chacun des scénarios suivants.  
  
1. Affichage à l’écran de documents de format fixe.  
  
2. Scénarios d’impression.  
  
    - [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] comme langage d’imprimante.  
  
    - Microsoft XPS Document Writer.  
  
    - Pilotes d’imprimante précédents, sortie des applications Win32 au format fixe.  
  
    - Format de spouleur d’impression.  
  
3. Représentation de documents à format fixe, y compris les clients pour les versions précédentes de Windows et d’autres appareils informatiques.  
  
> [!NOTE]
> <xref:System.Windows.Documents.Glyphs>et <xref:System.Windows.Media.GlyphRun> sont conçus pour la présentation de documents à format fixe et les scénarios d’impression. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]fournit plusieurs éléments pour [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] la mise <xref:System.Windows.Controls.Label> <xref:System.Windows.Controls.TextBlock>en page générale et des scénarios tels que et . Pour plus d’informations sur la mise en page et [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] les scénarios, voir la [Typographie dans WPF](typography-in-wpf.md).  
  
<a name="text_glyphrunovw_glyphrunobject"></a>
## <a name="the-glyphrun-object"></a>Objet GlyphRun  
 L’objet <xref:System.Windows.Media.GlyphRun> représente une séquence de glyphes à partir d’un seul visage d’une seule police à une seule taille, et avec un seul style de rendu.  
  
 <xref:System.Windows.Media.GlyphRun>comprend les deux détails de <xref:System.Windows.Documents.Glyphs.Indices%2A> police tels que les positions de glyphe et de glyphe individuel. Il comprend également les points de code Unicode d’origine que l’exécution a été généré à partir, caractère-à-glyph tampon offset informations, et par caractère et par-glyphe drapeaux.  
  
 <xref:System.Windows.Media.GlyphRun>a un niveau <xref:System.Windows.FrameworkElement>élevé <xref:System.Windows.Documents.Glyphs>correspondant , . <xref:System.Windows.Documents.Glyphs>peut être utilisé dans l’arbre élément et dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] la majoration pour représenter <xref:System.Windows.Media.GlyphRun> la sortie.  
  
<a name="text_glyphrunovw_glyphselement"></a>
## <a name="the-glyphs-element"></a>Élément Glyphs  
 L’élément <xref:System.Windows.Documents.Glyphs> représente la <xref:System.Windows.Media.GlyphRun> [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]sortie d’un in . La syntaxe de balisage <xref:System.Windows.Documents.Glyphs> suivante est utilisée pour décrire l’élément.  
  
 [!code-xaml[GlyphsOvwSample1#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSample1/CS/default.xaml#1)]  
  
 Les définitions de propriétés suivantes correspondent aux quatre premiers attributs de l’exemple de balisage.  
  
|Propriété|Description|  
|--------------|-----------------|  
|<xref:System.Windows.Documents.Glyphs.FontUri%2A>|Précise un identifiant de ressource : nom de fichier, identifiant de ressource d’uniforme Web (URI), ou référence de ressource dans l’application .exe ou conteneur.|  
|<xref:System.Windows.Documents.Glyphs.FontRenderingEmSize%2A>|Spécifie la taille de police en unités de surface de dessin (la valeur par défaut est 0,96 pouce).|  
|<xref:System.Windows.Documents.Glyphs.StyleSimulations%2A>|Spécifie les indicateurs des styles gras et italique.|  
|<xref:System.Windows.Documents.Glyphs.BidiLevel%2A>|Spécifie le niveau de disposition bidirectionnelle. Les valeurs paires et nulles impliquent une disposition de gauche à droite ; les valeurs impaires impliquent une disposition de droite à gauche.|  
  
<a name="text_glyphrunovw_indicesproperty"></a>
### <a name="indices-property"></a>Propriété Indices  
 La <xref:System.Windows.Documents.Glyphs.Indices%2A> propriété est une chaîne de spécifications glyphe. Quand une séquence de glyphes forme un groupement unique, la spécification du premier glyphe du groupement est précédée d’une spécification qui indique le nombre de glyphes et de points de code qui se combinent pour former le regroupement. La <xref:System.Windows.Documents.Glyphs.Indices%2A> propriété recueille en une seule chaîne les propriétés suivantes.  
  
- Index de glyphe  
  
- Largeurs d’avance de glyphe  
  
- Combinaison de vecteurs d’attachement de glyphe  
  
- Mappage de groupement des points de code aux glyphes  
  
- Indicateurs de glyphe  
  
 Chaque spécification de glyphe présente la forme suivante.  
  
 `[GlyphIndex][,[Advance][,[uOffset][,[vOffset][,[Flags]]]]]`  
  
<a name="text_glyphrunovw_glyphmetrics"></a>
## <a name="glyph-metrics"></a>Métriques de glyphe  
 Chaque glyphe définit les mesures qui spécifient comment il s’aligne avec d’autres <xref:System.Windows.Documents.Glyphs>. Le graphique suivant définit les diverses qualités typographiques de deux glyphes de caractères différents.  
  
 ![Diagramme des mesures de glyphe](./media/glyph-example.png "glyph_example")  
  
<a name="text_glyphrunovw_glyphsmarkup"></a>
## <a name="glyphs-markup"></a>Balisage Glyphs  
 L’exemple de code suivant montre <xref:System.Windows.Documents.Glyphs> comment [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]utiliser diverses propriétés de l’élément dans .  
  
 [!code-xaml[GlyphsOvwSamp2#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSamp2/CS/default.xaml#1)]  
  
## <a name="see-also"></a>Voir aussi

- [Typographie dans WPF](typography-in-wpf.md)
- [Documents dans WPF](documents-in-wpf.md)
- [Texte](optimizing-performance-text.md)
