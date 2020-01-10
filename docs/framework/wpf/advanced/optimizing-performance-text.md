---
title: 'Optimisation des performances : texte'
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
ms.openlocfilehash: 3e729458538353499f27f95ea2ca37fea1335238
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740341"
---
# <a name="optimizing-performance-text"></a>Optimisation des performances : texte

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] prend en charge la présentation de contenu de texte par le biais de l’utilisation de contrôles [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] avec de nombreuses fonctionnalités. En général, vous pouvez diviser le rendu du texte en trois couches :

1. Utilisation directe des objets <xref:System.Windows.Documents.Glyphs> et <xref:System.Windows.Media.GlyphRun>.

2. À l’aide de l’objet <xref:System.Windows.Media.FormattedText>.

3. À l’aide de contrôles de haut niveau, tels que les objets <xref:System.Windows.Controls.TextBlock> et <xref:System.Windows.Documents.FlowDocument>.

Cette rubrique fournit des recommandations relatives aux performances de rendu de texte.

<a name="Glyph_Level"></a>

## <a name="rendering-text-at-the-glyph-level"></a>Rendu de texte au niveau du glyphe

[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fournit une prise en charge de texte avancée, notamment le balisage au niveau du glyphe avec un accès direct aux <xref:System.Windows.Documents.Glyphs> pour les clients qui souhaitent intercepter et conserver du texte après la mise en forme. Ces fonctionnalités assurent une prise en charge critique pour les différentes spécifications de rendu de texte propres à chacun des scénarios suivants.

- Affichage à l’écran de documents de format fixe.

- Scénarios d’impression.

  - [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] comme langage d’imprimante.

  - Microsoft XPS document Writer.

  - Pilotes d’imprimante précédents, sortie des applications Win32 au format fixe.

  - Format de spouleur d’impression.

- Représentation de document de format fixe, y compris les clients des versions antérieures de Windows et d’autres appareils informatiques.

> [!NOTE]
> <xref:System.Windows.Documents.Glyphs> et <xref:System.Windows.Media.GlyphRun> sont conçus pour les scénarios de présentation et d’impression de documents de format fixe. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fournit plusieurs éléments pour la mise en page générale et les scénarios de [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)], tels que <xref:System.Windows.Controls.Label> et <xref:System.Windows.Controls.TextBlock>. Pour plus d’informations sur les scénarios de disposition et d’[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], consultez [Typographie dans WPF](typography-in-wpf.md).

Les exemples suivants montrent comment définir les propriétés d’un objet <xref:System.Windows.Documents.Glyphs> dans [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. L’objet <xref:System.Windows.Documents.Glyphs> représente la sortie d’une <xref:System.Windows.Media.GlyphRun> dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Ces exemples supposent que les polices Arial, Courrier New et Times New Roman sont installées dans le dossier **C:\WINDOWS\Fonts** sur l’ordinateur local.

[!code-xaml[GlyphsOvwSample1#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSample1/CS/default.xaml#1)]

### <a name="using-drawglyphrun"></a>Utilisation de DrawGlyphRun

Si vous avez un contrôle personnalisé et que vous souhaitez restituer des glyphes, utilisez la méthode <xref:System.Windows.Media.DrawingContext.DrawGlyphRun%2A>.

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit également des services de niveau inférieur pour la mise en forme de texte personnalisée par le biais de l’utilisation de l’objet <xref:System.Windows.Media.FormattedText>. La méthode la plus efficace pour afficher du texte dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] consiste à générer du contenu de texte au niveau du glyphe à l’aide de <xref:System.Windows.Documents.Glyphs> et de <xref:System.Windows.Media.GlyphRun>. Toutefois, le coût de cette efficacité est la perte d’une mise en forme de texte enrichi facile à utiliser, qui sont des fonctionnalités intégrées de [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] contrôles, tels que les <xref:System.Windows.Controls.TextBlock> et les <xref:System.Windows.Documents.FlowDocument>.

<a name="FormattedText_Object"></a>

## <a name="formattedtext-object"></a>Objet FormattedText

L’objet <xref:System.Windows.Media.FormattedText> vous permet de dessiner du texte multiligne, dans lequel chaque caractère du texte peut être mis en forme individuellement. Pour plus d'informations, consultez [Dessin du texte mis en forme](drawing-formatted-text.md).

Pour créer du texte mis en forme, appelez le constructeur <xref:System.Windows.Media.FormattedText.%23ctor%2A> pour créer un objet <xref:System.Windows.Media.FormattedText>. Une fois que vous avez créé la chaîne initiale de texte mis en forme, vous pouvez appliquer différents styles de mise en forme. Si votre application souhaite implémenter sa propre disposition, l’objet <xref:System.Windows.Media.FormattedText> est mieux adapté à l’utilisation d’un contrôle, comme <xref:System.Windows.Controls.TextBlock>. Pour plus d’informations sur l’objet <xref:System.Windows.Media.FormattedText>, consultez [dessin du texte mis en forme](drawing-formatted-text.md) .

L’objet <xref:System.Windows.Media.FormattedText> fournit une fonctionnalité de mise en forme du texte de bas niveau. Vous pouvez appliquer plusieurs styles de mise en forme à un ou plusieurs caractères. Par exemple, vous pouvez appeler les méthodes <xref:System.Windows.Media.FormattedText.SetFontSize%2A> et <xref:System.Windows.Media.FormattedText.SetForegroundBrush%2A> pour modifier la mise en forme des cinq premiers caractères du texte.

L’exemple de code suivant crée un objet <xref:System.Windows.Media.FormattedText> et le rend.

[!code-csharp[formattedtextsnippets#FormattedTextSnippets1](~/samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets1)]
[!code-vb[formattedtextsnippets#FormattedTextSnippets1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets1)]

<a name="FlowDocument_TextBlock_Label"></a>

## <a name="flowdocument-textblock-and-label-controls"></a>Contrôles FlowDocument, TextBlock et Label

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] inclut plusieurs contrôles pour dessiner le texte à l’écran. Chaque contrôle est ciblé sur un scénario différent et dispose de sa propre liste de fonctionnalités et limitations.

### <a name="flowdocument-impacts-performance-more-than-textblock-or-label"></a>FlowDocument influe davantage sur les performances que TextBlock ou Label

En général, l’élément <xref:System.Windows.Controls.TextBlock> doit être utilisé quand une prise en charge de texte limitée est nécessaire, par exemple une courte phrase dans une [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. <xref:System.Windows.Controls.Label> peut être utilisé quand une prise en charge minimale du texte est requise. L’élément <xref:System.Windows.Documents.FlowDocument> est un conteneur pour les documents refluides qui prennent en charge la présentation enrichie de contenu et, par conséquent, a un impact accru sur les performances par rapport à l’utilisation des contrôles <xref:System.Windows.Controls.TextBlock> ou <xref:System.Windows.Controls.Label>.

Pour plus d’informations sur <xref:System.Windows.Documents.FlowDocument>, consultez [vue d’ensemble des documents dynamiques](flow-document-overview.md).

### <a name="avoid-using-textblock-in-flowdocument"></a>Éviter l’utilisation de TextBlock dans FlowDocument

L’élément <xref:System.Windows.Controls.TextBlock> est dérivé de <xref:System.Windows.UIElement>. L’élément <xref:System.Windows.Documents.Run> est dérivé de <xref:System.Windows.Documents.TextElement>, ce qui est moins coûteux à utiliser qu’un objet dérivé de <xref:System.Windows.UIElement>. Lorsque cela est possible, utilisez <xref:System.Windows.Documents.Run> plutôt que <xref:System.Windows.Controls.TextBlock> pour afficher le contenu de texte dans un <xref:System.Windows.Documents.FlowDocument>.

L’exemple de balisage suivant illustre deux façons de définir le contenu de texte dans un <xref:System.Windows.Documents.FlowDocument>:

[!code-xaml[Performance#PerformanceSnippet13](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/FlowDocument.xaml#performancesnippet13)]

### <a name="avoid-using-run-to-set-text-properties"></a>Éviter l’utilisation de Run pour définir des propriétés de texte

En général, l’utilisation d’un <xref:System.Windows.Documents.Run> dans un <xref:System.Windows.Controls.TextBlock> est plus gourmande en performances que l’utilisation d’un objet <xref:System.Windows.Documents.Run> explicite. Si vous utilisez un <xref:System.Windows.Documents.Run> pour définir des propriétés de texte, définissez ces propriétés directement sur le <xref:System.Windows.Controls.TextBlock> à la place.

L’exemple de balisage suivant illustre ces deux méthodes de définition d’une propriété de texte, dans ce cas, la propriété <xref:System.Windows.Controls.TextBlock.FontWeight%2A> :

[!code-xaml[Performance#PerformanceSnippet12](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml#performancesnippet12)]

Le tableau suivant montre le coût de l’affichage des objets 1000 <xref:System.Windows.Controls.TextBlock> avec et sans <xref:System.Windows.Documents.Run>explicite.

|**Type de TextBlock**|**Durée de création (ms)**|**Temps d’affichage (ms)**|
|------------------------|------------------------------|----------------------------|
|Utilisation de Run pour définir des propriétés de texte|146|540|
|Utilisation de TextBlock pour définir des propriétés de texte|43|453|

### <a name="avoid-databinding-to-the-labelcontent-property"></a>Éviter la liaison de données à la propriété Label.Content

Imaginez un scénario dans lequel vous disposez d’un objet <xref:System.Windows.Controls.Label> qui est fréquemment mis à jour à partir d’une source <xref:System.String>. Lorsque vous liez des données à la propriété <xref:System.Windows.Controls.ContentControl.Content%2A> de l’élément de <xref:System.Windows.Controls.Label> à l’objet source <xref:System.String>, vous pouvez constater des performances médiocres. Chaque fois que le <xref:System.String> source est mis à jour, l’ancien objet <xref:System.String> est ignoré et une nouvelle <xref:System.String> est recréée, car un objet <xref:System.String> est immuable, il ne peut pas être modifié. Cela amène ensuite la <xref:System.Windows.Controls.ContentPresenter> de l’objet <xref:System.Windows.Controls.Label> à abandonner son ancien contenu et à régénérer le nouveau contenu pour afficher le nouveau <xref:System.String>.

La solution à ce problème est simple. Si la <xref:System.Windows.Controls.Label> n’est pas définie sur une valeur de <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> personnalisée, remplacez la <xref:System.Windows.Controls.Label> par une <xref:System.Windows.Controls.TextBlock> et liez <xref:System.Windows.Controls.TextBlock.Text%2A> ses données à la chaîne source.

|**Propriété liée aux données**|**Durée de la mise à jour (ms)**|
|-----------------------------|----------------------------|
|Label.Content|835|
|TextBlock.Text|242|

<a name="Hyperlink"></a>

## <a name="hyperlink"></a>Lien hypertexte

L’objet <xref:System.Windows.Documents.Hyperlink> est un élément de contenu de workflow au niveau de la ligne qui vous permet d’héberger des liens hypertexte dans le contenu dynamique.

### <a name="combine-hyperlinks-in-one-textblock-object"></a>Combiner des liens hypertexte en un objet TextBlock

Vous pouvez optimiser l’utilisation de plusieurs éléments <xref:System.Windows.Documents.Hyperlink> en les regroupant dans le même <xref:System.Windows.Controls.TextBlock>. De cette façon, vous réduisez le nombre d’objets à créer dans votre application. Par exemple, vous pouvez afficher plusieurs liens hypertexte, comme suit :

Page d’accueil MSN &#124; Mon MSN

L’exemple de balisage suivant montre plusieurs <xref:System.Windows.Controls.TextBlock> éléments utilisés pour afficher les liens hypertexte :

[!code-xaml[Performance#PerformanceSnippet9](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet9)]

L’exemple de balisage suivant montre un moyen plus efficace d’afficher les liens hypertexte, cette fois, à l’aide d’un <xref:System.Windows.Controls.TextBlock>unique :

[!code-xaml[Performance#PerformanceSnippet10](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet10)]

### <a name="showing-underlines-on-hyperlinks-only-on-mouseenter-events"></a>Affichage du soulignement des liens hypertexte uniquement pour les événements MouseEnter

Un objet <xref:System.Windows.TextDecoration> est un ornement visuel que vous pouvez ajouter à du texte. Toutefois, il peut s’agir d’une utilisation intensive des performances pour instancier. Si vous utilisez beaucoup d’éléments <xref:System.Windows.Documents.Hyperlink>, envisagez d’afficher un soulignement uniquement lors du déclenchement d’un événement, tel que l’événement <xref:System.Windows.ContentElement.MouseEnter>. Pour plus d’informations, consultez [Spécifier si un lien hypertexte est souligné ou non](how-to-specify-whether-a-hyperlink-is-underlined.md).

L’illustration suivante montre comment l’événement MouseEnter déclenche le lien hypertexte souligné :

![Liens hypertexte affichant TextDecorations](./media/how-to-specify-whether-a-hyperlink-is-underlined/text-decorations-hyperlinks.png)

L’exemple de balisage suivant illustre une <xref:System.Windows.Documents.Hyperlink> définie avec et sans soulignement :

[!code-xaml[Performance#PerformanceSnippet11](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet11)]

Le tableau suivant montre les performances de l’affichage de 1000 <xref:System.Windows.Documents.Hyperlink> éléments avec et sans soulignement.

|**Lien hypertexte**|**Durée de création (ms)**|**Temps d’affichage (ms)**|
|-------------------|------------------------------|----------------------------|
|Avec soulignement|289|1130|
|Sans soulignement|299|776|

<a name="Text_Formatting_Features"></a>

## <a name="text-formatting-features"></a>Fonctionnalités de mise en forme du texte

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit des services de mise en forme de texte enrichi, comme la coupure de mots automatique. Ces services peuvent affecter les performances de l’application et doivent être utilisés uniquement si nécessaire.

### <a name="avoid-unnecessary-use-of-hyphenation"></a>Éviter l’utilisation inutile de la coupure de mots

La césure automatique détecte les points d’arrêt de trait d’Union pour les lignes de texte et autorise des positions de rupture supplémentaires pour les lignes dans les objets <xref:System.Windows.Controls.TextBlock> et <xref:System.Windows.Documents.FlowDocument>. Par défaut, la fonctionnalité de coupure de mots automatique est désactivée dans ces objets. Vous pouvez activer cette fonctionnalité en définissant la propriété IsHyphenationEnabled de l’objet sur `true`. Toutefois, l’activation de cette fonctionnalité amène [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] à lancer l’interopérabilité COM (Component Object Model), ce qui peut avoir un impact sur les performances de l’application. Nous vous recommandons de ne pas utiliser la coupure de mots automatique, sauf si vous en avez besoin.

### <a name="use-figures-carefully"></a>Utiliser les figures avec précaution

Un élément <xref:System.Windows.Documents.Figure> représente une partie du contenu dynamique qui peut être positionnée de manière absolue dans une page de contenu. Dans certains cas, un <xref:System.Windows.Documents.Figure> peut entraîner la remise en forme automatique d’une page entière si sa position est en conflit avec du contenu qui a déjà été disposé. Vous pouvez réduire le risque de reformatage inutile en regroupant les éléments <xref:System.Windows.Documents.Figure> les uns à côté des autres ou en les déclarant vers le haut du contenu dans un scénario de taille de page fixe.

### <a name="optimal-paragraph"></a>Paragraphe optimal

La fonctionnalité de paragraphe optimal de l’objet <xref:System.Windows.Documents.FlowDocument> présente des paragraphes afin que l’espace blanc soit distribué aussi uniformément que possible. Par défaut, la fonctionnalité de paragraphe optimal est désactivée. Vous pouvez activer cette fonctionnalité en affectant à la propriété <xref:System.Windows.Documents.FlowDocument.IsOptimalParagraphEnabled%2A> de l’objet la valeur `true`. Toutefois, l’activation de cette fonctionnalité affecte les performances de l’application. Nous vous recommandons de ne pas utiliser la fonctionnalité de paragraphe optimal, sauf si vous en avez besoin.

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
