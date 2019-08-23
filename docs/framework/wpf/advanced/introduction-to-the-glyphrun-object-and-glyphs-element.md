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
# <a name="introduction-to-the-glyphrun-object-and-glyphs-element"></a><span data-ttu-id="137a9-102">Introduction à l'objet GlyphRun et à l'élément Glyphs</span><span class="sxs-lookup"><span data-stu-id="137a9-102">Introduction to the GlyphRun Object and Glyphs Element</span></span>
<span data-ttu-id="137a9-103">Cette rubrique décrit l' <xref:System.Windows.Media.GlyphRun> objet et l' <xref:System.Windows.Documents.Glyphs> élément.</span><span class="sxs-lookup"><span data-stu-id="137a9-103">This topic describes the <xref:System.Windows.Media.GlyphRun> object and the <xref:System.Windows.Documents.Glyphs> element.</span></span>  

<a name="text_glyphrunovw_intro"></a>   
## <a name="introduction-to-glyphrun"></a><span data-ttu-id="137a9-104">Introduction à GlyphRun</span><span class="sxs-lookup"><span data-stu-id="137a9-104">Introduction to GlyphRun</span></span>  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="137a9-105">fournit une prise en charge de texte avancée, notamment le balisage <xref:System.Windows.Documents.Glyphs> au niveau du glyphe avec un accès direct à pour les clients qui souhaitent intercepter et conserver du texte après la mise en forme.</span><span class="sxs-lookup"><span data-stu-id="137a9-105">provides advanced text support including glyph-level markup with direct access to <xref:System.Windows.Documents.Glyphs> for customers who want to intercept and persist text after formatting.</span></span> <span data-ttu-id="137a9-106">Ces fonctionnalités assurent une prise en charge critique pour les différentes spécifications de rendu de texte propres à chacun des scénarios suivants.</span><span class="sxs-lookup"><span data-stu-id="137a9-106">These features provide critical support for the different text rendering requirements in each of the following scenarios.</span></span>  
  
1. <span data-ttu-id="137a9-107">Affichage à l’écran de documents de format fixe.</span><span class="sxs-lookup"><span data-stu-id="137a9-107">Screen display of fixed-format documents.</span></span>  
  
2. <span data-ttu-id="137a9-108">Scénarios d’impression.</span><span class="sxs-lookup"><span data-stu-id="137a9-108">Print scenarios.</span></span>  
  
    - [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] <span data-ttu-id="137a9-109">comme langage d’imprimante.</span><span class="sxs-lookup"><span data-stu-id="137a9-109">as a device printer language.</span></span>  
  
    - <span data-ttu-id="137a9-110">Microsoft XPS document Writer.</span><span class="sxs-lookup"><span data-stu-id="137a9-110">Microsoft XPS Document Writer.</span></span>  
  
    - <span data-ttu-id="137a9-111">Pilotes d’imprimante précédents, sortie d’applications [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] au format fixe.</span><span class="sxs-lookup"><span data-stu-id="137a9-111">Previous printer drivers, output from [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] applications to the fixed format.</span></span>  
  
    - <span data-ttu-id="137a9-112">Format de spouleur d’impression.</span><span class="sxs-lookup"><span data-stu-id="137a9-112">Print spool format.</span></span>  
  
3. <span data-ttu-id="137a9-113">Représentation de document de format fixe, y compris les clients des versions antérieures de Windows et d’autres appareils informatiques.</span><span class="sxs-lookup"><span data-stu-id="137a9-113">Fixed-format document representation, including clients for previous versions of Windows and other computing devices.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="137a9-114"><xref:System.Windows.Documents.Glyphs>et <xref:System.Windows.Media.GlyphRun> sont conçus pour des scénarios de présentation et d’impression de documents de format fixe.</span><span class="sxs-lookup"><span data-stu-id="137a9-114"><xref:System.Windows.Documents.Glyphs> and <xref:System.Windows.Media.GlyphRun> are designed for fixed-format document presentation and print scenarios.</span></span> [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="137a9-115">fournit plusieurs éléments pour la mise en [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] page générale et <xref:System.Windows.Controls.Label> les <xref:System.Windows.Controls.TextBlock>scénarios tels que et.</span><span class="sxs-lookup"><span data-stu-id="137a9-115">provides several elements for general layout and [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] scenarios such as <xref:System.Windows.Controls.Label> and <xref:System.Windows.Controls.TextBlock>.</span></span> <span data-ttu-id="137a9-116">Pour plus d’informations sur les scénarios de disposition et d’[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], consultez [Typographie dans WPF](typography-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="137a9-116">For more information on layout and [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] scenarios, see the [Typography in WPF](typography-in-wpf.md).</span></span>  
  
<a name="text_glyphrunovw_glyphrunobject"></a>   
## <a name="the-glyphrun-object"></a><span data-ttu-id="137a9-117">Objet GlyphRun</span><span class="sxs-lookup"><span data-stu-id="137a9-117">The GlyphRun Object</span></span>  
 <span data-ttu-id="137a9-118">L' <xref:System.Windows.Media.GlyphRun> objet représente une séquence de glyphes d’une seule face d’une police unique à une seule taille, avec un style de rendu unique.</span><span class="sxs-lookup"><span data-stu-id="137a9-118">The <xref:System.Windows.Media.GlyphRun> object represents a sequence of glyphs from a single face of a single font at a single size, and with a single rendering style.</span></span>  
  
 <span data-ttu-id="137a9-119"><xref:System.Windows.Media.GlyphRun>comprend les détails de la police, <xref:System.Windows.Documents.Glyphs.Indices%2A> tels que les positions de glyphe et de glyphes individuels.</span><span class="sxs-lookup"><span data-stu-id="137a9-119"><xref:System.Windows.Media.GlyphRun> includes both font details such as glyph <xref:System.Windows.Documents.Glyphs.Indices%2A> and individual glyph positions.</span></span> <span data-ttu-id="137a9-120">Il comprend également les points [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] de code d’origine à partir desquels la série a été générée, les informations de mappage de décalage de la mémoire tampon de caractère à glyphe et les indicateurs par caractère et par glyphe.</span><span class="sxs-lookup"><span data-stu-id="137a9-120">It also includes the original [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] code points the run was generated from, character-to-glyph buffer offset mapping information, and per-character and per-glyph flags.</span></span>  
  
 <span data-ttu-id="137a9-121"><xref:System.Windows.Media.GlyphRun>a un de haut niveau <xref:System.Windows.FrameworkElement> <xref:System.Windows.Documents.Glyphs>correspondant.</span><span class="sxs-lookup"><span data-stu-id="137a9-121"><xref:System.Windows.Media.GlyphRun> has a corresponding high-level <xref:System.Windows.FrameworkElement>, <xref:System.Windows.Documents.Glyphs>.</span></span> <span data-ttu-id="137a9-122"><xref:System.Windows.Documents.Glyphs>peut être utilisé dans l’arborescence d’éléments et [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dans le balisage pour représenter <xref:System.Windows.Media.GlyphRun> la sortie.</span><span class="sxs-lookup"><span data-stu-id="137a9-122"><xref:System.Windows.Documents.Glyphs> can be used in the element tree and in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup to represent <xref:System.Windows.Media.GlyphRun> output.</span></span>  
  
<a name="text_glyphrunovw_glyphselement"></a>   
## <a name="the-glyphs-element"></a><span data-ttu-id="137a9-123">Élément Glyphs</span><span class="sxs-lookup"><span data-stu-id="137a9-123">The Glyphs Element</span></span>  
 <span data-ttu-id="137a9-124">L' <xref:System.Windows.Documents.Glyphs> élément représente la sortie d’un <xref:System.Windows.Media.GlyphRun> dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="137a9-124">The <xref:System.Windows.Documents.Glyphs> element represents the output of a <xref:System.Windows.Media.GlyphRun> in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span> <span data-ttu-id="137a9-125">La syntaxe de balisage suivante est utilisée pour <xref:System.Windows.Documents.Glyphs> décrire l’élément.</span><span class="sxs-lookup"><span data-stu-id="137a9-125">The following markup syntax is used to describe the <xref:System.Windows.Documents.Glyphs> element.</span></span>  
  
 [!code-xaml[GlyphsOvwSample1#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSample1/CS/default.xaml#1)]  
  
 <span data-ttu-id="137a9-126">Les définitions de propriétés suivantes correspondent aux quatre premiers attributs de l’exemple de balisage.</span><span class="sxs-lookup"><span data-stu-id="137a9-126">The following property definitions correspond to the first four attributes in the sample markup.</span></span>  
  
|<span data-ttu-id="137a9-127">Propriété</span><span class="sxs-lookup"><span data-stu-id="137a9-127">Property</span></span>|<span data-ttu-id="137a9-128">Description</span><span class="sxs-lookup"><span data-stu-id="137a9-128">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Windows.Documents.Glyphs.FontUri%2A>|<span data-ttu-id="137a9-129">Spécifie un identificateur de ressource: nom de fichier [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)], Web ou référence de ressource dans le fichier application. exe ou le conteneur.</span><span class="sxs-lookup"><span data-stu-id="137a9-129">Specifies a resource identifier: file name, Web [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)], or resource reference in the application .exe or container.</span></span>|  
|<xref:System.Windows.Documents.Glyphs.FontRenderingEmSize%2A>|<span data-ttu-id="137a9-130">Spécifie la taille de police en unités de surface de dessin (la valeur par défaut est 0,96 pouce).</span><span class="sxs-lookup"><span data-stu-id="137a9-130">Specifies the font size in drawing surface units (default is .96 inches).</span></span>|  
|<xref:System.Windows.Documents.Glyphs.StyleSimulations%2A>|<span data-ttu-id="137a9-131">Spécifie les indicateurs des styles gras et italique.</span><span class="sxs-lookup"><span data-stu-id="137a9-131">Specifies flags for bold and Italic styles.</span></span>|  
|<xref:System.Windows.Documents.Glyphs.BidiLevel%2A>|<span data-ttu-id="137a9-132">Spécifie le niveau de disposition bidirectionnelle.</span><span class="sxs-lookup"><span data-stu-id="137a9-132">Specifies the bidirectional layout level.</span></span> <span data-ttu-id="137a9-133">Les valeurs paires et nulles impliquent une disposition de gauche à droite ; les valeurs impaires impliquent une disposition de droite à gauche.</span><span class="sxs-lookup"><span data-stu-id="137a9-133">Even-numbered and zero values imply left-to-right layout; odd-numbered values imply right-to-left layout.</span></span>|  
  
<a name="text_glyphrunovw_indicesproperty"></a>   
### <a name="indices-property"></a><span data-ttu-id="137a9-134">Propriété Indices</span><span class="sxs-lookup"><span data-stu-id="137a9-134">Indices property</span></span>  
 <span data-ttu-id="137a9-135">La <xref:System.Windows.Documents.Glyphs.Indices%2A> propriété est une chaîne de spécifications de glyphe.</span><span class="sxs-lookup"><span data-stu-id="137a9-135">The <xref:System.Windows.Documents.Glyphs.Indices%2A> property is a string of glyph specifications.</span></span> <span data-ttu-id="137a9-136">Quand une séquence de glyphes forme un groupement unique, la spécification du premier glyphe du groupement est précédée d’une spécification qui indique le nombre de glyphes et de points de code qui se combinent pour former le regroupement.</span><span class="sxs-lookup"><span data-stu-id="137a9-136">Where a sequence of glyphs forms a single cluster, the specification of the first glyph in the cluster is preceded by a specification of how many glyphs and how many code points combine to form the cluster.</span></span> <span data-ttu-id="137a9-137">La <xref:System.Windows.Documents.Glyphs.Indices%2A> propriété collecte dans une chaîne les propriétés suivantes.</span><span class="sxs-lookup"><span data-stu-id="137a9-137">The <xref:System.Windows.Documents.Glyphs.Indices%2A> property collects in one string the following properties.</span></span>  
  
- <span data-ttu-id="137a9-138">Index de glyphe</span><span class="sxs-lookup"><span data-stu-id="137a9-138">Glyph indices</span></span>  
  
- <span data-ttu-id="137a9-139">Largeurs d’avance de glyphe</span><span class="sxs-lookup"><span data-stu-id="137a9-139">Glyph advance widths</span></span>  
  
- <span data-ttu-id="137a9-140">Combinaison de vecteurs d’attachement de glyphe</span><span class="sxs-lookup"><span data-stu-id="137a9-140">Combining glyph attachment vectors</span></span>  
  
- <span data-ttu-id="137a9-141">Mappage de groupement des points de code aux glyphes</span><span class="sxs-lookup"><span data-stu-id="137a9-141">Cluster mapping from code points to glyphs</span></span>  
  
- <span data-ttu-id="137a9-142">Indicateurs de glyphe</span><span class="sxs-lookup"><span data-stu-id="137a9-142">Glyph flags</span></span>  
  
 <span data-ttu-id="137a9-143">Chaque spécification de glyphe présente la forme suivante.</span><span class="sxs-lookup"><span data-stu-id="137a9-143">Each glyph specification has the following form.</span></span>  
  
 `[GlyphIndex][,[Advance][,[uOffset][,[vOffset][,[Flags]]]]]`  
  
<a name="text_glyphrunovw_glyphmetrics"></a>   
## <a name="glyph-metrics"></a><span data-ttu-id="137a9-144">Métriques de glyphe</span><span class="sxs-lookup"><span data-stu-id="137a9-144">Glyph Metrics</span></span>  
 <span data-ttu-id="137a9-145">Chaque glyphe définit des mesures qui spécifient la façon dont il s' <xref:System.Windows.Documents.Glyphs>aligne avec l’autre.</span><span class="sxs-lookup"><span data-stu-id="137a9-145">Each glyph defines metrics that specify how it aligns with other <xref:System.Windows.Documents.Glyphs>.</span></span> <span data-ttu-id="137a9-146">Le graphique suivant définit les diverses qualités typographiques de deux glyphes de caractères différents.</span><span class="sxs-lookup"><span data-stu-id="137a9-146">The following graphic defines the various typographic qualities of two different glyph characters.</span></span>  
  
 <span data-ttu-id="137a9-147">![Diagramme des mesures de glyphe](./media/glyph-example.png "glyph_example")</span><span class="sxs-lookup"><span data-stu-id="137a9-147">![Diagraph of glyph measurements](./media/glyph-example.png "glyph_example")</span></span>  
  
<a name="text_glyphrunovw_glyphsmarkup"></a>   
## <a name="glyphs-markup"></a><span data-ttu-id="137a9-148">Balisage Glyphs</span><span class="sxs-lookup"><span data-stu-id="137a9-148">Glyphs Markup</span></span>  
 <span data-ttu-id="137a9-149">L’exemple de code suivant montre comment utiliser les différentes propriétés de <xref:System.Windows.Documents.Glyphs> l’élément [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]dans.</span><span class="sxs-lookup"><span data-stu-id="137a9-149">The following code example shows how to use various properties of the <xref:System.Windows.Documents.Glyphs> element in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
 [!code-xaml[GlyphsOvwSamp2#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSamp2/CS/default.xaml#1)]  
  
## <a name="see-also"></a><span data-ttu-id="137a9-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="137a9-150">See also</span></span>

- [<span data-ttu-id="137a9-151">Typographie dans WPF</span><span class="sxs-lookup"><span data-stu-id="137a9-151">Typography in WPF</span></span>](typography-in-wpf.md)
- [<span data-ttu-id="137a9-152">Documents dans WPF</span><span class="sxs-lookup"><span data-stu-id="137a9-152">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="137a9-153">Text</span><span class="sxs-lookup"><span data-stu-id="137a9-153">Text</span></span>](optimizing-performance-text.md)
