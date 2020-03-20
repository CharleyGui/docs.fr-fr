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
# <a name="introduction-to-the-glyphrun-object-and-glyphs-element"></a><span data-ttu-id="71a13-102">Introduction à l'objet GlyphRun et à l'élément Glyphs</span><span class="sxs-lookup"><span data-stu-id="71a13-102">Introduction to the GlyphRun Object and Glyphs Element</span></span>
<span data-ttu-id="71a13-103">Ce sujet décrit <xref:System.Windows.Media.GlyphRun> l’objet et l’élément. <xref:System.Windows.Documents.Glyphs></span><span class="sxs-lookup"><span data-stu-id="71a13-103">This topic describes the <xref:System.Windows.Media.GlyphRun> object and the <xref:System.Windows.Documents.Glyphs> element.</span></span>  

<a name="text_glyphrunovw_intro"></a>
## <a name="introduction-to-glyphrun"></a><span data-ttu-id="71a13-104">Introduction à GlyphRun</span><span class="sxs-lookup"><span data-stu-id="71a13-104">Introduction to GlyphRun</span></span>  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="71a13-105">fournit un support texte avancé, y compris la <xref:System.Windows.Documents.Glyphs> balisage au niveau du glyph, avec un accès direct aux clients qui veulent intercepter et persister le texte après le formatage.</span><span class="sxs-lookup"><span data-stu-id="71a13-105">provides advanced text support including glyph-level markup with direct access to <xref:System.Windows.Documents.Glyphs> for customers who want to intercept and persist text after formatting.</span></span> <span data-ttu-id="71a13-106">Ces fonctionnalités assurent une prise en charge critique pour les différentes spécifications de rendu de texte propres à chacun des scénarios suivants.</span><span class="sxs-lookup"><span data-stu-id="71a13-106">These features provide critical support for the different text rendering requirements in each of the following scenarios.</span></span>  
  
1. <span data-ttu-id="71a13-107">Affichage à l’écran de documents de format fixe.</span><span class="sxs-lookup"><span data-stu-id="71a13-107">Screen display of fixed-format documents.</span></span>  
  
2. <span data-ttu-id="71a13-108">Scénarios d’impression.</span><span class="sxs-lookup"><span data-stu-id="71a13-108">Print scenarios.</span></span>  
  
    - [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] <span data-ttu-id="71a13-109">comme langage d’imprimante.</span><span class="sxs-lookup"><span data-stu-id="71a13-109">as a device printer language.</span></span>  
  
    - <span data-ttu-id="71a13-110">Microsoft XPS Document Writer.</span><span class="sxs-lookup"><span data-stu-id="71a13-110">Microsoft XPS Document Writer.</span></span>  
  
    - <span data-ttu-id="71a13-111">Pilotes d’imprimante précédents, sortie des applications Win32 au format fixe.</span><span class="sxs-lookup"><span data-stu-id="71a13-111">Previous printer drivers, output from Win32 applications to the fixed format.</span></span>  
  
    - <span data-ttu-id="71a13-112">Format de spouleur d’impression.</span><span class="sxs-lookup"><span data-stu-id="71a13-112">Print spool format.</span></span>  
  
3. <span data-ttu-id="71a13-113">Représentation de documents à format fixe, y compris les clients pour les versions précédentes de Windows et d’autres appareils informatiques.</span><span class="sxs-lookup"><span data-stu-id="71a13-113">Fixed-format document representation, including clients for previous versions of Windows and other computing devices.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="71a13-114"><xref:System.Windows.Documents.Glyphs>et <xref:System.Windows.Media.GlyphRun> sont conçus pour la présentation de documents à format fixe et les scénarios d’impression.</span><span class="sxs-lookup"><span data-stu-id="71a13-114"><xref:System.Windows.Documents.Glyphs> and <xref:System.Windows.Media.GlyphRun> are designed for fixed-format document presentation and print scenarios.</span></span> [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="71a13-115">fournit plusieurs éléments pour [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] la mise <xref:System.Windows.Controls.Label> <xref:System.Windows.Controls.TextBlock>en page générale et des scénarios tels que et .</span><span class="sxs-lookup"><span data-stu-id="71a13-115">provides several elements for general layout and [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] scenarios such as <xref:System.Windows.Controls.Label> and <xref:System.Windows.Controls.TextBlock>.</span></span> <span data-ttu-id="71a13-116">Pour plus d’informations sur la mise en page et [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] les scénarios, voir la [Typographie dans WPF](typography-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="71a13-116">For more information on layout and [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] scenarios, see the [Typography in WPF](typography-in-wpf.md).</span></span>  
  
<a name="text_glyphrunovw_glyphrunobject"></a>
## <a name="the-glyphrun-object"></a><span data-ttu-id="71a13-117">Objet GlyphRun</span><span class="sxs-lookup"><span data-stu-id="71a13-117">The GlyphRun Object</span></span>  
 <span data-ttu-id="71a13-118">L’objet <xref:System.Windows.Media.GlyphRun> représente une séquence de glyphes à partir d’un seul visage d’une seule police à une seule taille, et avec un seul style de rendu.</span><span class="sxs-lookup"><span data-stu-id="71a13-118">The <xref:System.Windows.Media.GlyphRun> object represents a sequence of glyphs from a single face of a single font at a single size, and with a single rendering style.</span></span>  
  
 <span data-ttu-id="71a13-119"><xref:System.Windows.Media.GlyphRun>comprend les deux détails de <xref:System.Windows.Documents.Glyphs.Indices%2A> police tels que les positions de glyphe et de glyphe individuel.</span><span class="sxs-lookup"><span data-stu-id="71a13-119"><xref:System.Windows.Media.GlyphRun> includes both font details such as glyph <xref:System.Windows.Documents.Glyphs.Indices%2A> and individual glyph positions.</span></span> <span data-ttu-id="71a13-120">Il comprend également les points de code Unicode d’origine que l’exécution a été généré à partir, caractère-à-glyph tampon offset informations, et par caractère et par-glyphe drapeaux.</span><span class="sxs-lookup"><span data-stu-id="71a13-120">It also includes the original Unicode code points the run was generated from, character-to-glyph buffer offset mapping information, and per-character and per-glyph flags.</span></span>  
  
 <span data-ttu-id="71a13-121"><xref:System.Windows.Media.GlyphRun>a un niveau <xref:System.Windows.FrameworkElement>élevé <xref:System.Windows.Documents.Glyphs>correspondant , .</span><span class="sxs-lookup"><span data-stu-id="71a13-121"><xref:System.Windows.Media.GlyphRun> has a corresponding high-level <xref:System.Windows.FrameworkElement>, <xref:System.Windows.Documents.Glyphs>.</span></span> <span data-ttu-id="71a13-122"><xref:System.Windows.Documents.Glyphs>peut être utilisé dans l’arbre élément et dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] la majoration pour représenter <xref:System.Windows.Media.GlyphRun> la sortie.</span><span class="sxs-lookup"><span data-stu-id="71a13-122"><xref:System.Windows.Documents.Glyphs> can be used in the element tree and in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup to represent <xref:System.Windows.Media.GlyphRun> output.</span></span>  
  
<a name="text_glyphrunovw_glyphselement"></a>
## <a name="the-glyphs-element"></a><span data-ttu-id="71a13-123">Élément Glyphs</span><span class="sxs-lookup"><span data-stu-id="71a13-123">The Glyphs Element</span></span>  
 <span data-ttu-id="71a13-124">L’élément <xref:System.Windows.Documents.Glyphs> représente la <xref:System.Windows.Media.GlyphRun> [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]sortie d’un in .</span><span class="sxs-lookup"><span data-stu-id="71a13-124">The <xref:System.Windows.Documents.Glyphs> element represents the output of a <xref:System.Windows.Media.GlyphRun> in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span> <span data-ttu-id="71a13-125">La syntaxe de balisage <xref:System.Windows.Documents.Glyphs> suivante est utilisée pour décrire l’élément.</span><span class="sxs-lookup"><span data-stu-id="71a13-125">The following markup syntax is used to describe the <xref:System.Windows.Documents.Glyphs> element.</span></span>  
  
 [!code-xaml[GlyphsOvwSample1#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSample1/CS/default.xaml#1)]  
  
 <span data-ttu-id="71a13-126">Les définitions de propriétés suivantes correspondent aux quatre premiers attributs de l’exemple de balisage.</span><span class="sxs-lookup"><span data-stu-id="71a13-126">The following property definitions correspond to the first four attributes in the sample markup.</span></span>  
  
|<span data-ttu-id="71a13-127">Propriété</span><span class="sxs-lookup"><span data-stu-id="71a13-127">Property</span></span>|<span data-ttu-id="71a13-128">Description</span><span class="sxs-lookup"><span data-stu-id="71a13-128">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Windows.Documents.Glyphs.FontUri%2A>|<span data-ttu-id="71a13-129">Précise un identifiant de ressource : nom de fichier, identifiant de ressource d’uniforme Web (URI), ou référence de ressource dans l’application .exe ou conteneur.</span><span class="sxs-lookup"><span data-stu-id="71a13-129">Specifies a resource identifier: file name, Web uniform resource identifier (URI), or resource reference in the application .exe or container.</span></span>|  
|<xref:System.Windows.Documents.Glyphs.FontRenderingEmSize%2A>|<span data-ttu-id="71a13-130">Spécifie la taille de police en unités de surface de dessin (la valeur par défaut est 0,96 pouce).</span><span class="sxs-lookup"><span data-stu-id="71a13-130">Specifies the font size in drawing surface units (default is .96 inches).</span></span>|  
|<xref:System.Windows.Documents.Glyphs.StyleSimulations%2A>|<span data-ttu-id="71a13-131">Spécifie les indicateurs des styles gras et italique.</span><span class="sxs-lookup"><span data-stu-id="71a13-131">Specifies flags for bold and Italic styles.</span></span>|  
|<xref:System.Windows.Documents.Glyphs.BidiLevel%2A>|<span data-ttu-id="71a13-132">Spécifie le niveau de disposition bidirectionnelle.</span><span class="sxs-lookup"><span data-stu-id="71a13-132">Specifies the bidirectional layout level.</span></span> <span data-ttu-id="71a13-133">Les valeurs paires et nulles impliquent une disposition de gauche à droite ; les valeurs impaires impliquent une disposition de droite à gauche.</span><span class="sxs-lookup"><span data-stu-id="71a13-133">Even-numbered and zero values imply left-to-right layout; odd-numbered values imply right-to-left layout.</span></span>|  
  
<a name="text_glyphrunovw_indicesproperty"></a>
### <a name="indices-property"></a><span data-ttu-id="71a13-134">Propriété Indices</span><span class="sxs-lookup"><span data-stu-id="71a13-134">Indices property</span></span>  
 <span data-ttu-id="71a13-135">La <xref:System.Windows.Documents.Glyphs.Indices%2A> propriété est une chaîne de spécifications glyphe.</span><span class="sxs-lookup"><span data-stu-id="71a13-135">The <xref:System.Windows.Documents.Glyphs.Indices%2A> property is a string of glyph specifications.</span></span> <span data-ttu-id="71a13-136">Quand une séquence de glyphes forme un groupement unique, la spécification du premier glyphe du groupement est précédée d’une spécification qui indique le nombre de glyphes et de points de code qui se combinent pour former le regroupement.</span><span class="sxs-lookup"><span data-stu-id="71a13-136">Where a sequence of glyphs forms a single cluster, the specification of the first glyph in the cluster is preceded by a specification of how many glyphs and how many code points combine to form the cluster.</span></span> <span data-ttu-id="71a13-137">La <xref:System.Windows.Documents.Glyphs.Indices%2A> propriété recueille en une seule chaîne les propriétés suivantes.</span><span class="sxs-lookup"><span data-stu-id="71a13-137">The <xref:System.Windows.Documents.Glyphs.Indices%2A> property collects in one string the following properties.</span></span>  
  
- <span data-ttu-id="71a13-138">Index de glyphe</span><span class="sxs-lookup"><span data-stu-id="71a13-138">Glyph indices</span></span>  
  
- <span data-ttu-id="71a13-139">Largeurs d’avance de glyphe</span><span class="sxs-lookup"><span data-stu-id="71a13-139">Glyph advance widths</span></span>  
  
- <span data-ttu-id="71a13-140">Combinaison de vecteurs d’attachement de glyphe</span><span class="sxs-lookup"><span data-stu-id="71a13-140">Combining glyph attachment vectors</span></span>  
  
- <span data-ttu-id="71a13-141">Mappage de groupement des points de code aux glyphes</span><span class="sxs-lookup"><span data-stu-id="71a13-141">Cluster mapping from code points to glyphs</span></span>  
  
- <span data-ttu-id="71a13-142">Indicateurs de glyphe</span><span class="sxs-lookup"><span data-stu-id="71a13-142">Glyph flags</span></span>  
  
 <span data-ttu-id="71a13-143">Chaque spécification de glyphe présente la forme suivante.</span><span class="sxs-lookup"><span data-stu-id="71a13-143">Each glyph specification has the following form.</span></span>  
  
 `[GlyphIndex][,[Advance][,[uOffset][,[vOffset][,[Flags]]]]]`  
  
<a name="text_glyphrunovw_glyphmetrics"></a>
## <a name="glyph-metrics"></a><span data-ttu-id="71a13-144">Métriques de glyphe</span><span class="sxs-lookup"><span data-stu-id="71a13-144">Glyph Metrics</span></span>  
 <span data-ttu-id="71a13-145">Chaque glyphe définit les mesures qui spécifient comment il s’aligne avec d’autres <xref:System.Windows.Documents.Glyphs>.</span><span class="sxs-lookup"><span data-stu-id="71a13-145">Each glyph defines metrics that specify how it aligns with other <xref:System.Windows.Documents.Glyphs>.</span></span> <span data-ttu-id="71a13-146">Le graphique suivant définit les diverses qualités typographiques de deux glyphes de caractères différents.</span><span class="sxs-lookup"><span data-stu-id="71a13-146">The following graphic defines the various typographic qualities of two different glyph characters.</span></span>  
  
 <span data-ttu-id="71a13-147">![Diagramme des mesures de glyphe](./media/glyph-example.png "glyph_example")</span><span class="sxs-lookup"><span data-stu-id="71a13-147">![Diagraph of glyph measurements](./media/glyph-example.png "glyph_example")</span></span>  
  
<a name="text_glyphrunovw_glyphsmarkup"></a>
## <a name="glyphs-markup"></a><span data-ttu-id="71a13-148">Balisage Glyphs</span><span class="sxs-lookup"><span data-stu-id="71a13-148">Glyphs Markup</span></span>  
 <span data-ttu-id="71a13-149">L’exemple de code suivant montre <xref:System.Windows.Documents.Glyphs> comment [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]utiliser diverses propriétés de l’élément dans .</span><span class="sxs-lookup"><span data-stu-id="71a13-149">The following code example shows how to use various properties of the <xref:System.Windows.Documents.Glyphs> element in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
 [!code-xaml[GlyphsOvwSamp2#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSamp2/CS/default.xaml#1)]  
  
## <a name="see-also"></a><span data-ttu-id="71a13-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="71a13-150">See also</span></span>

- [<span data-ttu-id="71a13-151">Typographie dans WPF</span><span class="sxs-lookup"><span data-stu-id="71a13-151">Typography in WPF</span></span>](typography-in-wpf.md)
- [<span data-ttu-id="71a13-152">Documents dans WPF</span><span class="sxs-lookup"><span data-stu-id="71a13-152">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="71a13-153">Texte</span><span class="sxs-lookup"><span data-stu-id="71a13-153">Text</span></span>](optimizing-performance-text.md)
