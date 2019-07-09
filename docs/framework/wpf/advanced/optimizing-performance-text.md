---
title: 'Optimisation des performances : Texte'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- rendering text [WPF]
- hyperlinks [WPF]
- formatted text [WPF]
- text [WPF], performance
- glyphs [WPF]
ms.assetid: 66b1b9a7-8618-48db-b616-c57ea4327b98
ms.openlocfilehash: 67549e75244790973554d08de8f4dac99d28bd80
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67660772"
---
# <a name="optimizing-performance-text"></a>Optimisation des performances : Texte

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] prend en charge la présentation de contenu de texte par le biais de l’utilisation de contrôles [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] avec de nombreuses fonctionnalités. En général, vous pouvez diviser le rendu du texte en trois couches :

1. À l’aide de la <xref:System.Windows.Documents.Glyphs> et <xref:System.Windows.Media.GlyphRun> objets directement.

2. À l’aide de la <xref:System.Windows.Media.FormattedText> objet.

3. À l’aide de contrôles de niveau supérieur, tels que le <xref:System.Windows.Controls.TextBlock> et <xref:System.Windows.Documents.FlowDocument> objets.

Cette rubrique fournit des recommandations relatives aux performances de rendu de texte.

<a name="Glyph_Level"></a>

## <a name="rendering-text-at-the-glyph-level"></a>Rendu de texte au niveau du glyphe

[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Fournit la prise en charge de texte avancée, y compris le balisage au niveau du glyphe avec accès direct à <xref:System.Windows.Documents.Glyphs> pour les clients qui souhaitent intercepter et rendre le texte persistant après la mise en forme. Ces fonctionnalités assurent une prise en charge critique pour les différentes spécifications de rendu de texte propres à chacun des scénarios suivants.

- Affichage à l’écran de documents de format fixe.

- Scénarios d’impression.

  - [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] comme langage d’imprimante.

  - [!INCLUDE[TLA#tla_mxdw](../../../../includes/tlasharptla-mxdw-md.md)].

  - Pilotes d’imprimante précédents, sortie d’applications [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] au format fixe.

  - Format de spouleur d’impression.

- Représentation sous forme de document de format fixe, notamment des clients pour des versions précédentes de [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] et autres appareils informatiques.

> [!NOTE]
> <xref:System.Windows.Documents.Glyphs> et <xref:System.Windows.Media.GlyphRun> sont conçus pour la présentation de documents à format fixe et les scénarios d’impression. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fournit plusieurs éléments pour la présentation générale et [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] scénarios comme <xref:System.Windows.Controls.Label> et <xref:System.Windows.Controls.TextBlock>. Pour plus d’informations sur les scénarios de disposition et d’[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], consultez [Typographie dans WPF](typography-in-wpf.md).

Les exemples suivants montrent comment définir des propriétés pour un <xref:System.Windows.Documents.Glyphs> dans l’objet [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. Le <xref:System.Windows.Documents.Glyphs> objet représente la sortie d’un <xref:System.Windows.Media.GlyphRun> dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Ces exemples supposent que les polices Arial, Courrier New et Times New Roman sont installées dans le dossier **C:\WINDOWS\Fonts** sur l’ordinateur local.

[!code-xaml[GlyphsOvwSample1#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSample1/CS/default.xaml#1)]

### <a name="using-drawglyphrun"></a>Utilisation de DrawGlyphRun

Si vous avez un contrôle personnalisé et que vous souhaitez afficher des glyphes, utilisez le <xref:System.Windows.Media.DrawingContext.DrawGlyphRun%2A> (méthode).

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit également des services de niveau inférieur pour le texte personnalisé à l’aide de la mise en forme le <xref:System.Windows.Media.FormattedText> objet. Le moyen le plus efficace de rendu du texte dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] est de générer le contenu de texte au niveau de glyphe à l’aide <xref:System.Windows.Documents.Glyphs> et <xref:System.Windows.Media.GlyphRun>. Toutefois, le coût de cette efficacité est la perte de facile à utiliser texte enrichi, qui sont des fonctionnalités intégrées de [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] contrôles, tels que <xref:System.Windows.Controls.TextBlock> et <xref:System.Windows.Documents.FlowDocument>.

<a name="FormattedText_Object"></a>

## <a name="formattedtext-object"></a>Objet FormattedText

Le <xref:System.Windows.Media.FormattedText> objet permet de dessiner du texte multiligne, dans lequel chaque caractère du texte peut être mis en forme individuellement. Pour plus d'informations, consultez [Dessin du texte mis en forme](drawing-formatted-text.md).

Pour créer le texte mis en forme, appelez le <xref:System.Windows.Media.FormattedText.%23ctor%2A> constructeur pour créer un <xref:System.Windows.Media.FormattedText> objet. Une fois que vous avez créé la chaîne initiale de texte mis en forme, vous pouvez appliquer différents styles de mise en forme. Si votre application souhaite implémenter sa propre disposition, puis le <xref:System.Windows.Media.FormattedText> objet est à l’aide d’un contrôle, comme le meilleur choix <xref:System.Windows.Controls.TextBlock>. Pour plus d’informations sur la <xref:System.Windows.Media.FormattedText> d’objets, consultez [dessin du texte mis en forme](drawing-formatted-text.md) .

Le <xref:System.Windows.Media.FormattedText> objet fournit la fonctionnalité de mise en forme de texte de bas niveau. Vous pouvez appliquer plusieurs styles de mise en forme à un ou plusieurs caractères. Par exemple, vous pouvez appeler à la fois le <xref:System.Windows.Media.FormattedText.SetFontSize%2A> et <xref:System.Windows.Media.FormattedText.SetForegroundBrush%2A> méthodes pour modifier la mise en forme des cinq premiers caractères dans le texte.

L’exemple de code suivant crée un <xref:System.Windows.Media.FormattedText> de l’objet et effectue le rendu.

[!code-csharp[formattedtextsnippets#FormattedTextSnippets1](~/samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets1)]
[!code-vb[formattedtextsnippets#FormattedTextSnippets1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets1)]

<a name="FlowDocument_TextBlock_Label"></a>

## <a name="flowdocument-textblock-and-label-controls"></a>Contrôles FlowDocument, TextBlock et Label

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] inclut plusieurs contrôles pour dessiner le texte à l’écran. Chaque contrôle cible un scénario différent et dispose de sa propre liste de fonctionnalités et limitations.

### <a name="flowdocument-impacts-performance-more-than-textblock-or-label"></a>FlowDocument influe davantage sur les performances que TextBlock ou Label

En règle générale, le <xref:System.Windows.Controls.TextBlock> élément doit être utilisé lors de la prise en charge de texte limitée est requis, par exemple, une courte phrase dans un [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. <xref:System.Windows.Controls.Label> peut être utilisé lors de la prise en charge de texte minimale est requise. Le <xref:System.Windows.Documents.FlowDocument> élément est un conteneur pour les documents qui prennent en charge la présentation enrichie du contenu et par conséquent, a un impact sur les performances supérieur que l’utilisation de la <xref:System.Windows.Controls.TextBlock> ou <xref:System.Windows.Controls.Label> contrôles.

Pour plus d’informations sur <xref:System.Windows.Documents.FlowDocument>, consultez [vue d’ensemble du Document de flux](flow-document-overview.md).

### <a name="avoid-using-textblock-in-flowdocument"></a>Éviter l’utilisation de TextBlock dans FlowDocument

Le <xref:System.Windows.Controls.TextBlock> élément est dérivé de <xref:System.Windows.UIElement>. Le <xref:System.Windows.Documents.Run> élément est dérivé de <xref:System.Windows.Documents.TextElement>, qui est moins cher à utiliser qu’un <xref:System.Windows.UIElement>-objet dérivé. Si possible, utilisez <xref:System.Windows.Documents.Run> plutôt que <xref:System.Windows.Controls.TextBlock> pour afficher du texte contenu dans un <xref:System.Windows.Documents.FlowDocument>.

L’exemple de balisage suivant illustre deux façons de définir le contenu de texte dans un <xref:System.Windows.Documents.FlowDocument>:

[!code-xaml[Performance#PerformanceSnippet13](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/FlowDocument.xaml#performancesnippet13)]

### <a name="avoid-using-run-to-set-text-properties"></a>Éviter l’utilisation de Run pour définir des propriétés de texte

En règle générale, à l’aide un <xref:System.Windows.Documents.Run> au sein d’un <xref:System.Windows.Controls.TextBlock> est performances plus performante que celle de ne pas utiliser de <xref:System.Windows.Documents.Run> tout de l’objet. Si vous utilisez un <xref:System.Windows.Documents.Run> afin de définir les propriétés de texte, définissez ces propriétés directement sur le <xref:System.Windows.Controls.TextBlock> à la place.

L’exemple de balisage suivant illustre ces deux façons de définir une propriété de texte, dans ce cas, le <xref:System.Windows.Controls.TextBlock.FontWeight%2A> propriété :

[!code-xaml[Performance#PerformanceSnippet12](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml#performancesnippet12)]

Le tableau suivant montre le coût de l’affichage de 1000 <xref:System.Windows.Controls.TextBlock> objets avec et sans explicite <xref:System.Windows.Documents.Run>.

|**Type de TextBlock**|**Durée de création (ms)**|**Durée d’affichage (ms)**|
|------------------------|------------------------------|----------------------------|
|Utilisation de Run pour définir des propriétés de texte|146|540|
|Utilisation de TextBlock pour définir des propriétés de texte|43|453|

### <a name="avoid-databinding-to-the-labelcontent-property"></a>Éviter la liaison de données à la propriété Label.Content

Imaginez un scénario où vous avez un <xref:System.Windows.Controls.Label> objet qui est fréquemment mis à jour à partir d’un <xref:System.String> source. Lors de la liaison de données la <xref:System.Windows.Controls.Label> l’élément <xref:System.Windows.Controls.ContentControl.Content%2A> propriété le <xref:System.String> source de l’objet, vous pouvez rencontrer des performances médiocres. Chaque fois que la source de <xref:System.String> est mis à jour, l’ancien <xref:System.String> objet est ignoré et un nouveau <xref:System.String> est recréé, car un <xref:System.String> objet est immuable, il ne peut pas être modifié. Ceci, à son tour, provoque la <xref:System.Windows.Controls.ContentPresenter> de la <xref:System.Windows.Controls.Label> objet à ignorer son ancien contenu et à régénérer le nouveau contenu pour afficher le nouveau <xref:System.String>.

La solution à ce problème est simple. Si le <xref:System.Windows.Controls.Label> n’est pas défini sur un personnalisé <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> , remplacez le <xref:System.Windows.Controls.Label> avec un <xref:System.Windows.Controls.TextBlock> et lier les données son <xref:System.Windows.Controls.TextBlock.Text%2A> propriété à la chaîne source.

|**Propriété liée aux données**|**Durée de la mise à jour (ms)**|
|-----------------------------|----------------------------|
|Label.Content|835|
|TextBlock.Text|242|

<a name="Hyperlink"></a>

## <a name="hyperlink"></a>Lien hypertexte

Le <xref:System.Windows.Documents.Hyperlink> objet est un élément de contenu de flux inline qui permet d’héberger des liens hypertexte dans le contenu de flux.

### <a name="combine-hyperlinks-in-one-textblock-object"></a>Combiner des liens hypertexte en un objet TextBlock

Vous pouvez optimiser l’utilisation de plusieurs <xref:System.Windows.Documents.Hyperlink> éléments en les regroupant dans le même <xref:System.Windows.Controls.TextBlock>. De cette façon, vous réduisez le nombre d’objets à créer dans votre application. Par exemple, vous pouvez afficher plusieurs liens hypertexte, comme suit :

Page d’accueil MSN &#124; Mon MSN

L’exemple de balisage suivant montre plusieurs <xref:System.Windows.Controls.TextBlock> éléments utilisés pour afficher les liens hypertexte :

[!code-xaml[Performance#PerformanceSnippet9](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet9)]

L’exemple de balisage suivant montre un moyen plus efficace d’afficher les liens hypertexte, cette fois, à l’aide d’un seul <xref:System.Windows.Controls.TextBlock>:

[!code-xaml[Performance#PerformanceSnippet10](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet10)]

### <a name="showing-underlines-on-hyperlinks-only-on-mouseenter-events"></a>Affichage du soulignement des liens hypertexte uniquement pour les événements MouseEnter

Un <xref:System.Windows.TextDecoration> objet est une ornementation visuelle que vous pouvez ajouter au texte ; Toutefois, il peut être performances intensif à instancier. Si vous utilisez beaucoup de <xref:System.Windows.Documents.Hyperlink> éléments, envisagez d’afficher un soulignement uniquement lors du déclenchement d’un événement, tel que le <xref:System.Windows.ContentElement.MouseEnter> événement. Pour plus d’informations, consultez [Spécifier si un lien hypertexte est souligné ou non](how-to-specify-whether-a-hyperlink-is-underlined.md).

L’illustration suivante montre comment l’événement MouseEnter déclenche le lien hypertexte souligné :

![Liens hypertexte affichant TextDecorations](./media/how-to-specify-whether-a-hyperlink-is-underlined/text-decorations-hyperlinks.png)

L’exemple de balisage suivant montre un <xref:System.Windows.Documents.Hyperlink> défini avec et sans soulignement :

[!code-xaml[Performance#PerformanceSnippet11](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet11)]

Le tableau suivant montre le coût de performances de l’affichage de 1000 <xref:System.Windows.Documents.Hyperlink> éléments avec et sans soulignement.

|**Lien hypertexte**|**Durée de création (ms)**|**Durée d’affichage (ms)**|
|-------------------|------------------------------|----------------------------|
|Avec soulignement|289|1130|
|Sans soulignement|299|776|

<a name="Text_Formatting_Features"></a>

## <a name="text-formatting-features"></a>Fonctionnalités de mise en forme du texte

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit des services de mise en forme de texte enrichi, comme la coupure de mots automatique. Ces services peuvent affecter les performances de l’application et doivent être utilisés uniquement si nécessaire.

### <a name="avoid-unnecessary-use-of-hyphenation"></a>Éviter l’utilisation inutile de la coupure de mots

Coupure de mots automatique recherche des points d’arrêt de trait d’union pour des lignes de texte et autorise des positions d’arrêt supplémentaires pour les lignes de <xref:System.Windows.Controls.TextBlock> et <xref:System.Windows.Documents.FlowDocument> objets. Par défaut, la fonctionnalité de coupure de mots automatique est désactivée dans ces objets. Vous pouvez activer cette fonctionnalité en définissant la propriété IsHyphenationEnabled de l’objet sur `true`. Toutefois, si vous activez cette fonctionnalité, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] lance l’interopérabilité [!INCLUDE[TLA#tla_com](../../../../includes/tlasharptla-com-md.md)], ce qui peut affecter les performances de l’application. Nous vous recommandons de ne pas utiliser la coupure de mots automatique, sauf si vous en avez besoin.

### <a name="use-figures-carefully"></a>Utiliser les figures avec précaution

Un <xref:System.Windows.Documents.Figure> élément représente une partie de contenu de flux qui peut être positionnés de manière absolue dans une page de contenu. Dans certains cas, un <xref:System.Windows.Documents.Figure> peut entraîner une page entière de reformater automatiquement si sa position est en conflit avec le contenu qui a déjà été disposé. Vous pouvez réduire la probabilité de la remise en forme inutile en regroupant <xref:System.Windows.Documents.Figure> éléments en regard les uns des autres, ou en les déclarant près du début du contenu dans un scénario de taille de page fixe.

### <a name="optimal-paragraph"></a>Paragraphe optimal

La fonctionnalité de paragraphe optimal de la <xref:System.Windows.Documents.FlowDocument> objet dispose les paragraphes afin que les blancs soient distribués de manière aussi égale que possible. Par défaut, la fonctionnalité de paragraphe optimal est désactivée. Vous pouvez activer cette fonctionnalité en définissant l’objet <xref:System.Windows.Documents.FlowDocument.IsOptimalParagraphEnabled%2A> propriété `true`. Toutefois, l’activation de cette fonctionnalité affecte les performances de l’application. Nous vous recommandons de ne pas utiliser la fonctionnalité de paragraphe optimal, sauf si vous en avez besoin.

## <a name="see-also"></a>Voir aussi

- [Optimisation des performances des applications WPF](optimizing-wpf-application-performance.md)
- [Planification des performances des applications](planning-for-application-performance.md)
- [Tirer parti du matériel](optimizing-performance-taking-advantage-of-hardware.md)
- [Disposition et conception](optimizing-performance-layout-and-design.md)
- [Graphiques 2D et acquisition d'images](optimizing-performance-2d-graphics-and-imaging.md)
- [Comportement de l’objet](optimizing-performance-object-behavior.md)
- [Ressources d'application](optimizing-performance-application-resources.md)
- [Liaison de données](optimizing-performance-data-binding.md)
- [Autres recommandations relatives aux performances](optimizing-performance-other-recommendations.md)
