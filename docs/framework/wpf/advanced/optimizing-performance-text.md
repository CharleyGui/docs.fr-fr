---
title: 'Optimisation des performances: Text'
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
ms.openlocfilehash: 318972c20f6461489226e19b3e517ba0ac069b28
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933364"
---
# <a name="optimizing-performance-text"></a>Optimisation des performances: Text

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] prend en charge la présentation de contenu de texte par le biais de l’utilisation de contrôles [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] avec de nombreuses fonctionnalités. En général, vous pouvez diviser le rendu du texte en trois couches :

1. Utilisation directe <xref:System.Windows.Documents.Glyphs> des <xref:System.Windows.Media.GlyphRun> objets et.

2. À l' <xref:System.Windows.Media.FormattedText> aide de l’objet.

3. À l’aide de contrôles de haut niveau, <xref:System.Windows.Controls.TextBlock> tels <xref:System.Windows.Documents.FlowDocument> que les objets et.

Cette rubrique fournit des recommandations relatives aux performances de rendu de texte.

<a name="Glyph_Level"></a>

## <a name="rendering-text-at-the-glyph-level"></a>Rendu de texte au niveau du glyphe

[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]fournit une prise en charge de texte avancée, notamment le balisage <xref:System.Windows.Documents.Glyphs> au niveau du glyphe avec un accès direct à pour les clients qui souhaitent intercepter et conserver du texte après la mise en forme. Ces fonctionnalités assurent une prise en charge critique pour les différentes spécifications de rendu de texte propres à chacun des scénarios suivants.

- Affichage à l’écran de documents de format fixe.

- Scénarios d’impression.

  - [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] comme langage d’imprimante.

  - Microsoft XPS document Writer.

  - Pilotes d’imprimante précédents, sortie d’applications [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] au format fixe.

  - Format de spouleur d’impression.

- Représentation de document de format fixe, y compris les clients des versions antérieures de Windows et d’autres appareils informatiques.

> [!NOTE]
> <xref:System.Windows.Documents.Glyphs>et <xref:System.Windows.Media.GlyphRun> sont conçus pour des scénarios de présentation et d’impression de documents de format fixe. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]fournit plusieurs éléments pour la mise en [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] page générale et <xref:System.Windows.Controls.Label> les <xref:System.Windows.Controls.TextBlock>scénarios tels que et. Pour plus d’informations sur les scénarios de disposition et d’[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], consultez [Typographie dans WPF](typography-in-wpf.md).

Les exemples suivants montrent comment définir les propriétés d’un <xref:System.Windows.Documents.Glyphs> objet dans [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. L' <xref:System.Windows.Documents.Glyphs> objet représente la sortie d’un <xref:System.Windows.Media.GlyphRun> dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Ces exemples supposent que les polices Arial, Courrier New et Times New Roman sont installées dans le dossier **C:\WINDOWS\Fonts** sur l’ordinateur local.

[!code-xaml[GlyphsOvwSample1#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSample1/CS/default.xaml#1)]

### <a name="using-drawglyphrun"></a>Utilisation de DrawGlyphRun

Si vous avez un contrôle personnalisé et que vous souhaitez restituer des glyphes <xref:System.Windows.Media.DrawingContext.DrawGlyphRun%2A> , utilisez la méthode.

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]fournit également des services de niveau inférieur pour la mise en forme de texte personnalisée par <xref:System.Windows.Media.FormattedText> le biais de l’utilisation de l’objet. La méthode la plus efficace pour afficher du [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] texte dans est de générer du contenu de texte au <xref:System.Windows.Documents.Glyphs> niveau <xref:System.Windows.Media.GlyphRun>du glyphe à l’aide de et de. Toutefois, le coût de cette efficacité est la perte d’une mise en forme de texte enrichi facile à utiliser, qui sont des fonctionnalités [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] intégrées de contrôles, <xref:System.Windows.Controls.TextBlock> telles <xref:System.Windows.Documents.FlowDocument>que et.

<a name="FormattedText_Object"></a>

## <a name="formattedtext-object"></a>Objet FormattedText

L' <xref:System.Windows.Media.FormattedText> objet vous permet de dessiner du texte multiligne, dans lequel chaque caractère du texte peut être mis en forme individuellement. Pour plus d'informations, consultez [Dessin du texte mis en forme](drawing-formatted-text.md).

Pour créer du texte mis en forme <xref:System.Windows.Media.FormattedText.%23ctor%2A> , appelez le constructeur <xref:System.Windows.Media.FormattedText> pour créer un objet. Une fois que vous avez créé la chaîne initiale de texte mis en forme, vous pouvez appliquer différents styles de mise en forme. Si votre application souhaite implémenter sa propre disposition, l' <xref:System.Windows.Media.FormattedText> objet est mieux adapté à l’utilisation d’un contrôle, tel que. <xref:System.Windows.Controls.TextBlock> Pour plus d’informations sur <xref:System.Windows.Media.FormattedText> l’objet, consultez [dessin du texte mis en forme](drawing-formatted-text.md) .

L' <xref:System.Windows.Media.FormattedText> objet fournit une fonctionnalité de mise en forme du texte de bas niveau. Vous pouvez appliquer plusieurs styles de mise en forme à un ou plusieurs caractères. Par exemple, vous pouvez appeler <xref:System.Windows.Media.FormattedText.SetFontSize%2A> les méthodes et <xref:System.Windows.Media.FormattedText.SetForegroundBrush%2A> pour modifier la mise en forme des cinq premiers caractères du texte.

L’exemple de code suivant crée <xref:System.Windows.Media.FormattedText> un objet et le rend.

[!code-csharp[formattedtextsnippets#FormattedTextSnippets1](~/samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets1)]
[!code-vb[formattedtextsnippets#FormattedTextSnippets1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets1)]

<a name="FlowDocument_TextBlock_Label"></a>

## <a name="flowdocument-textblock-and-label-controls"></a>Contrôles FlowDocument, TextBlock et Label

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] inclut plusieurs contrôles pour dessiner le texte à l’écran. Chaque contrôle cible un scénario différent et dispose de sa propre liste de fonctionnalités et limitations.

### <a name="flowdocument-impacts-performance-more-than-textblock-or-label"></a>FlowDocument influe davantage sur les performances que TextBlock ou Label

En général, l' <xref:System.Windows.Controls.TextBlock> élément doit être utilisé quand une prise en charge de texte limitée est nécessaire, par exemple une [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]courte phrase dans un. <xref:System.Windows.Controls.Label>peut être utilisé quand une prise en charge minimale du texte est requise. L' <xref:System.Windows.Documents.FlowDocument> élément est un conteneur pour les documents refluides qui prennent en charge la présentation enrichie de contenu et, par conséquent, a un impact <xref:System.Windows.Controls.TextBlock> accru <xref:System.Windows.Controls.Label> sur les performances par rapport à l’utilisation des contrôles ou.

Pour plus d’informations <xref:System.Windows.Documents.FlowDocument>sur, consultez [vue d’ensemble des documents dynamiques](flow-document-overview.md).

### <a name="avoid-using-textblock-in-flowdocument"></a>Éviter l’utilisation de TextBlock dans FlowDocument

L' <xref:System.Windows.Controls.TextBlock> élément est dérivé de <xref:System.Windows.UIElement>. L' <xref:System.Windows.Documents.Run> élément est dérivé de <xref:System.Windows.Documents.TextElement>, ce qui est moins coûteux à utiliser qu' <xref:System.Windows.UIElement>un objet dérivé de. Lorsque cela est possible <xref:System.Windows.Documents.Run> , utilisez <xref:System.Windows.Controls.TextBlock> plutôt que pour afficher le contenu <xref:System.Windows.Documents.FlowDocument>de texte dans un.

L’exemple de balisage suivant illustre deux façons de définir le contenu de <xref:System.Windows.Documents.FlowDocument>texte dans un:

[!code-xaml[Performance#PerformanceSnippet13](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/FlowDocument.xaml#performancesnippet13)]

### <a name="avoid-using-run-to-set-text-properties"></a>Éviter l’utilisation de Run pour définir des propriétés de texte

En général, l’utilisation <xref:System.Windows.Documents.Run> d’un <xref:System.Windows.Controls.TextBlock> dans un est plus gourmande en performances que <xref:System.Windows.Documents.Run> l’utilisation d’un objet explicite. Si vous utilisez un <xref:System.Windows.Documents.Run> pour définir des propriétés de texte, définissez ces propriétés directement sur le à la <xref:System.Windows.Controls.TextBlock> place.

L’exemple de balisage suivant illustre ces deux méthodes de définition d’une propriété de texte, dans ce <xref:System.Windows.Controls.TextBlock.FontWeight%2A> cas, la propriété:

[!code-xaml[Performance#PerformanceSnippet12](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml#performancesnippet12)]

Le tableau suivant montre le coût de l’affichage <xref:System.Windows.Controls.TextBlock> des objets 1000 avec et sans <xref:System.Windows.Documents.Run>Explicit.

|**Type de TextBlock**|**Durée de création (ms)**|**Durée d’affichage (ms)**|
|------------------------|------------------------------|----------------------------|
|Utilisation de Run pour définir des propriétés de texte|146|540|
|Utilisation de TextBlock pour définir des propriétés de texte|43|453|

### <a name="avoid-databinding-to-the-labelcontent-property"></a>Éviter la liaison de données à la propriété Label.Content

Imaginez un scénario dans lequel vous disposez <xref:System.Windows.Controls.Label> d’un objet qui est fréquemment mis <xref:System.String> à jour à partir d’une source. Lorsque des données lient <xref:System.Windows.Controls.Label> la propriété <xref:System.Windows.Controls.ContentControl.Content%2A> de l’élément <xref:System.String> à l’objet source, vous pouvez constater des performances médiocres. Chaque fois que la <xref:System.String> source est mise à jour <xref:System.String> , l’ancien objet est supprimé et un <xref:System.String> nouveau est recréé, car un <xref:System.String> objet est immuable et ne peut pas être modifié. Cela entraîne, à son tour, <xref:System.Windows.Controls.ContentPresenter> la suppression <xref:System.Windows.Controls.Label> de son ancien contenu par le de l’objet et la régénération du nouveau contenu <xref:System.String>pour afficher le nouveau.

La solution à ce problème est simple. <xref:System.Windows.Controls.TextBlock.Text%2A> <xref:System.Windows.Controls.TextBlock> <xref:System.Windows.Controls.Label> <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> Si n’est pas défini sur une valeur personnalisée, remplacez le par un et liez sa propriété à la chaîne source. <xref:System.Windows.Controls.Label>

|**Propriété liée aux données**|**Durée de la mise à jour (ms)**|
|-----------------------------|----------------------------|
|Label.Content|835|
|TextBlock.Text|242|

<a name="Hyperlink"></a>

## <a name="hyperlink"></a>Lien hypertexte

L' <xref:System.Windows.Documents.Hyperlink> objet est un élément de contenu de workflow au niveau de la ligne qui vous permet d’héberger des liens hypertexte dans le contenu dynamique.

### <a name="combine-hyperlinks-in-one-textblock-object"></a>Combiner des liens hypertexte en un objet TextBlock

Vous pouvez optimiser l’utilisation de plusieurs <xref:System.Windows.Documents.Hyperlink> éléments en les regroupant dans le même <xref:System.Windows.Controls.TextBlock>. De cette façon, vous réduisez le nombre d’objets à créer dans votre application. Par exemple, vous pouvez afficher plusieurs liens hypertexte, comme suit :

Page d’accueil MSN &#124; Mon MSN

L’exemple de balisage suivant <xref:System.Windows.Controls.TextBlock> montre plusieurs éléments utilisés pour afficher les liens hypertexte:

[!code-xaml[Performance#PerformanceSnippet9](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet9)]

L’exemple de balisage suivant montre un moyen plus efficace d’afficher les liens hypertexte, cette fois, à l' <xref:System.Windows.Controls.TextBlock>aide d’un seul:

[!code-xaml[Performance#PerformanceSnippet10](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet10)]

### <a name="showing-underlines-on-hyperlinks-only-on-mouseenter-events"></a>Affichage du soulignement des liens hypertexte uniquement pour les événements MouseEnter

Un <xref:System.Windows.TextDecoration> objet est un ornement visuel que vous pouvez ajouter à du texte. Toutefois, il peut s’agir d’une utilisation intensive des performances pour instancier. Si vous utilisez beaucoup d' <xref:System.Windows.Documents.Hyperlink> éléments, envisagez d’afficher un soulignement uniquement lors du déclenchement d’un événement, tel que l' <xref:System.Windows.ContentElement.MouseEnter> événement. Pour plus d’informations, consultez [Spécifier si un lien hypertexte est souligné ou non](how-to-specify-whether-a-hyperlink-is-underlined.md).

L’illustration suivante montre comment l’événement MouseEnter déclenche le lien hypertexte souligné:

![Liens hypertexte affichant TextDecorations](./media/how-to-specify-whether-a-hyperlink-is-underlined/text-decorations-hyperlinks.png)

L’exemple de balisage suivant <xref:System.Windows.Documents.Hyperlink> montre un défini avec et sans soulignement:

[!code-xaml[Performance#PerformanceSnippet11](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet11)]

Le tableau suivant indique le coût des performances de l' <xref:System.Windows.Documents.Hyperlink> affichage de 1000 éléments avec et sans soulignement.

|**Lien hypertexte**|**Durée de création (ms)**|**Durée d’affichage (ms)**|
|-------------------|------------------------------|----------------------------|
|Avec soulignement|289|1130|
|Sans soulignement|299|776|

<a name="Text_Formatting_Features"></a>

## <a name="text-formatting-features"></a>Fonctionnalités de mise en forme du texte

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit des services de mise en forme de texte enrichi, comme la coupure de mots automatique. Ces services peuvent affecter les performances de l’application et doivent être utilisés uniquement si nécessaire.

### <a name="avoid-unnecessary-use-of-hyphenation"></a>Éviter l’utilisation inutile de la coupure de mots

La césure automatique détecte les points d’arrêt de trait d’Union pour les lignes de texte et autorise <xref:System.Windows.Controls.TextBlock> des <xref:System.Windows.Documents.FlowDocument> positions de rupture supplémentaires pour les lignes dans les objets et. Par défaut, la fonctionnalité de coupure de mots automatique est désactivée dans ces objets. Vous pouvez activer cette fonctionnalité en définissant la propriété IsHyphenationEnabled de l’objet sur `true`. Toutefois, l’activation de cette [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fonctionnalité entraîne l’initiation de l’interopérabilité COM (Component Object Model), ce qui peut avoir un impact sur les performances de l’application. Nous vous recommandons de ne pas utiliser la coupure de mots automatique, sauf si vous en avez besoin.

### <a name="use-figures-carefully"></a>Utiliser les figures avec précaution

Un <xref:System.Windows.Documents.Figure> élément représente une partie du contenu dynamique qui peut être positionnée de manière absolue dans une page de contenu. Dans certains cas, un <xref:System.Windows.Documents.Figure> peut entraîner la remise en forme automatique d’une page entière si sa position est en conflit avec du contenu qui a déjà été disposé. Vous pouvez réduire la possibilité d’un reformatage inutile en regroupant <xref:System.Windows.Documents.Figure> les éléments les uns à côté des autres ou en les déclarant vers le haut du contenu dans un scénario de taille de page fixe.

### <a name="optimal-paragraph"></a>Paragraphe optimal

La fonctionnalité de paragraphe optimal de <xref:System.Windows.Documents.FlowDocument> l’objet dispose des paragraphes afin que l’espace blanc soit distribué aussi uniformément que possible. Par défaut, la fonctionnalité de paragraphe optimal est désactivée. Vous pouvez activer cette fonctionnalité en affectant à <xref:System.Windows.Documents.FlowDocument.IsOptimalParagraphEnabled%2A> `true`la propriété de l’objet la valeur. Toutefois, l’activation de cette fonctionnalité affecte les performances de l’application. Nous vous recommandons de ne pas utiliser la fonctionnalité de paragraphe optimal, sauf si vous en avez besoin.

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
