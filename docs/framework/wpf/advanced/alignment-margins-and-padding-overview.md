---
title: Vue d'ensemble de l'alignement, des marges et du remplissage
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- margins [WPF]
- padding [WPF]
- aligning [WPF]
ms.assetid: 9c6a2009-9b86-4e40-8605-0a2664dc3973
ms.openlocfilehash: bec2d9cd224febb650e2de67bb7406365d075963
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145473"
---
# <a name="alignment-margins-and-padding-overview"></a>Vue d'ensemble de l'alignement, des marges et du remplissage
La <xref:System.Windows.FrameworkElement> classe expose plusieurs propriétés qui sont utilisées pour positionner précisément les éléments de l’enfant. Ce sujet traite de quatre <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>des <xref:System.Windows.FrameworkElement.Margin%2A> <xref:System.Windows.Controls.Border.Padding%2A>propriétés <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>les plus importantes: , , , et . Il est important de comprendre les effets de ces propriétés, car elles servent de base au contrôle de la position des éléments dans les applications [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  

<a name="wcpsdk_layout_amp_introduction"></a>
## <a name="introduction-to-element-positioning"></a>Introduction au positionnement d’un élément  
 Il existe de nombreuses manières de positionner des éléments à l’aide de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Cependant, la réalisation de la <xref:System.Windows.Controls.Panel> mise en page idéale va au-delà du simple choix du bon élément. Le contrôle fin du positionnement <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>exige <xref:System.Windows.FrameworkElement.Margin%2A> <xref:System.Windows.Controls.Border.Padding%2A>une <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> compréhension de la , , , et les propriétés.  
  
 L’illustration suivante montre un scénario de disposition qui utilise plusieurs propriétés de positionnement.  
  
 ![Exemple de propriétés de positionnement WPF](./media/layout-margins-padding-alignment-graphic1.PNG "layout_margins_padding_alignment_graphic1")  
  
 À première vue, les <xref:System.Windows.Controls.Button> éléments de cette illustration peuvent sembler être placés au hasard. Toutefois, leurs positions sont contrôlées de manière précise à l’aide d’une combinaison d’informations relatives aux marges, aux alignements et au remplissage.  
  
 L’exemple suivant décrit comment créer la disposition de l’illustration précédente. Un <xref:System.Windows.Controls.Border> élément encapsule <xref:System.Windows.Controls.StackPanel>un parent, d’une <xref:System.Windows.Controls.Border.Padding%2A> valeur de 15 pixels indépendants de l’appareil. Cela explique la <xref:System.Windows.Media.Brushes.LightBlue%2A> bande étroite qui <xref:System.Windows.Controls.StackPanel>entoure l’enfant . Les éléments <xref:System.Windows.Controls.StackPanel> de l’enfant sont utilisés pour illustrer chacune des différentes propriétés de positionnement qui sont détaillées dans ce sujet. Trois <xref:System.Windows.Controls.Button> éléments sont utilisés <xref:System.Windows.FrameworkElement.Margin%2A> pour <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> démontrer à la fois les propriétés et les propriétés.  
  
 [!code-csharp[MPALayoutSampleIntro#1](~/samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutSampleIntro/CSharp/MPA_Layout_Sample_Intro.cs#1)]
 [!code-vb[MPALayoutSampleIntro#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutSampleIntro/VisualBasic/MPALayoutIntro.vb#1)]  
  
 Le diagramme suivant fournit un gros plan de l’affichage des différentes propriétés de positionnement utilisées dans l’exemple précédent. Les sections suivantes de cette rubrique décrivent plus en détail la manière d’utiliser chaque propriété de positionnement.  
  
 ![Propriétés de positionnement avec Screen Call&#45;outs](./media/layout-margins-padding-alignment-graphic2.PNG "layout_margins_padding_alignment_graphic2")  
  
<a name="wcpsdk_layout_amp_alignment_properties"></a>
## <a name="understanding-alignment-properties"></a>Présentation des propriétés d’alignement  
 Les <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> propriétés et les propriétés décrivent comment un élément enfant doit être placé dans l’espace de mise en page alloué d’un élément parent. En utilisant ces propriétés ensemble, vous pouvez positionner des éléments enfants avec précision. Par exemple, les <xref:System.Windows.Controls.DockPanel> éléments pour enfants d’un <xref:System.Windows.HorizontalAlignment.Right>peut <xref:System.Windows.HorizontalAlignment.Center>spécifier quatre alignements horizontaux différents: <xref:System.Windows.HorizontalAlignment.Left>, , ou , ou pour <xref:System.Windows.HorizontalAlignment.Stretch> remplir l’espace disponible. Des valeurs similaires sont disponibles pour le positionnement vertical.  
  
> [!NOTE]
> L’ensemble <xref:System.Windows.FrameworkElement.Height%2A> <xref:System.Windows.FrameworkElement.Width%2A> explicite et les propriétés <xref:System.Windows.HorizontalAlignment.Stretch> sur un élément ont préséance sur la valeur de la propriété. Tentative de <xref:System.Windows.FrameworkElement.Height%2A> <xref:System.Windows.FrameworkElement.Width%2A>définir , <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> , `Stretch` et `Stretch` une valeur des résultats dans la demande étant ignorée.  
  
<a name="wcpsdk_layout_amp_horizontalalignment_properties"></a>
### <a name="horizontalalignment-property"></a>Propriété HorizontalAlignment  
 La <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> propriété déclare les caractéristiques d’alignement horizontal à appliquer aux éléments de l’enfant. Le tableau suivant montre chacune <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> des valeurs possibles de la propriété.  
  
|Membre|Description|  
|------------|-----------------|  
|<xref:System.Windows.HorizontalAlignment.Left>|Les éléments enfants sont alignés à gauche de l’espace de disposition alloué par l’élément parent.|  
|<xref:System.Windows.HorizontalAlignment.Center>|Les éléments enfants sont alignés au centre de l’espace de disposition alloué par l’élément parent.|  
|<xref:System.Windows.HorizontalAlignment.Right>|Les éléments enfants sont alignés à droite de l’espace de disposition alloué par l’élément parent.|  
|<xref:System.Windows.HorizontalAlignment.Stretch> (valeur par défaut)|Les éléments enfants sont étirés pour remplir l’espace de disposition alloué par l’élément parent. Explicite <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.Height%2A> et les valeurs priment.|  
  
 L’exemple suivant montre <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> comment <xref:System.Windows.Controls.Button> appliquer la propriété aux éléments. Chaque valeur d’attribut est présentée pour mieux illustrer les différents comportements de rendu.  
  
 [!code-csharp[MPALayoutHorizontalAlignment#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutHorizontalAlignment/CSharp/MPA_Layout_HorizontalAlignment.cs#2)]
 [!code-vb[MPALayoutHorizontalAlignment#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutHorizontalAlignment/VisualBasic/MPA_Layout_HorizontalAlignment.vb#2)]  
  
 Le code précédent permet d’obtenir une disposition semblable à l’image suivante. Les effets de <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> positionnement de chaque valeur sont visibles dans l’illustration.  
  
 ![Exemple d'alignement horizontal](./media/layout-horizontal-alignment-graphic.PNG "layout_horizontal_alignment_graphic")  
  
<a name="wcpsdk_layout_amp_verticalalignment_properties"></a>
### <a name="verticalalignment-property"></a>Propriété VerticalAlignment  
 La <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> propriété décrit les caractéristiques d’alignement vertical à appliquer aux éléments de l’enfant. Le tableau suivant montre chacune <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> des valeurs possibles pour la propriété.  
  
|Membre|Description|  
|------------|-----------------|  
|<xref:System.Windows.VerticalAlignment.Top>|Les éléments enfants sont alignés en haut de l’espace de disposition alloué par l’élément parent.|  
|<xref:System.Windows.VerticalAlignment.Center>|Les éléments enfants sont alignés au centre de l’espace de disposition alloué par l’élément parent.|  
|<xref:System.Windows.VerticalAlignment.Bottom>|Les éléments enfants sont alignés en bas de l’espace de disposition alloué par l’élément parent.|  
|<xref:System.Windows.VerticalAlignment.Stretch> (valeur par défaut)|Les éléments enfants sont étirés pour remplir l’espace de disposition alloué par l’élément parent. Explicite <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.Height%2A> et les valeurs priment.|  
  
 L’exemple suivant montre <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> comment <xref:System.Windows.Controls.Button> appliquer la propriété aux éléments. Chaque valeur d’attribut est présentée pour mieux illustrer les différents comportements de rendu. Aux fins de cet <xref:System.Windows.Controls.Grid> échantillon, un élément avec des grilles visibles est utilisé comme parent, pour mieux illustrer le comportement de mise en page de chaque valeur de propriété.  
  
 [!code-csharp[MPALayoutVerticalAlignment#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutVerticalAlignment/CSharp/MPA_Layout_VerticalAlignment.cs#2)]
 [!code-vb[MPALayoutVerticalAlignment#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutVerticalAlignment/VisualBasic/MPA_Layout_VerticalAlignment.vb#2)]
 [!code-xaml[MPALayoutVerticalAlignment#2](~/samples/snippets/xaml/VS_Snippets_Wpf/MPALayoutVerticalAlignment/XAML/default.xaml#2)]  
  
 Le code précédent permet d’obtenir une disposition semblable à l’image suivante. Les effets de <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> positionnement de chaque valeur sont visibles dans l’illustration.  
  
 ![Exemple de propriété VerticalAlignment](./media/layout-vertical-alignment-graphic.PNG "layout_vertical_alignment_graphic")  
  
<a name="wcpsdk_layout_amp_margin_properties"></a>
## <a name="understanding-margin-properties"></a>Présentation des propriétés de marge  
 La <xref:System.Windows.FrameworkElement.Margin%2A> propriété décrit la distance entre un élément et son enfant ou ses pairs. <xref:System.Windows.FrameworkElement.Margin%2A>valeurs peuvent être uniformes, `Margin="20"`en utilisant la syntaxe comme . Avec cette syntaxe, un uniforme <xref:System.Windows.FrameworkElement.Margin%2A> de 20 pixels indépendants de dispositif serait appliqué à l’élément. <xref:System.Windows.FrameworkElement.Margin%2A>les valeurs peuvent également prendre la forme de quatre valeurs distinctes, chaque valeur décrivant une marge distincte `Margin="0,10,5,25"`à appliquer à gauche, en haut, en haut et en bas (dans cet ordre), comme . Une utilisation <xref:System.Windows.FrameworkElement.Margin%2A> appropriée de la propriété permet un contrôle très fin de la position de rendu d’un élément et de la position de rendu de ses éléments voisins et des enfants.  
  
> [!NOTE]
> Une marge non zéro s’applique <xref:System.Windows.FrameworkElement.ActualWidth%2A> à <xref:System.Windows.FrameworkElement.ActualHeight%2A>l’espace en dehors de l’élément et .  
  
 L’exemple suivant montre comment appliquer des <xref:System.Windows.Controls.Button> marges uniformes autour d’un groupe d’éléments. Les <xref:System.Windows.Controls.Button> éléments sont espacés uniformément avec un tampon de marge de dix pixels dans chaque direction.  
  
 [!code-cpp[MarginPaddingAlignmentSample#1](~/samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#1)]
 [!code-csharp[MarginPaddingAlignmentSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#1)]
 [!code-vb[MarginPaddingAlignmentSample#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#1)]
 [!code-xaml[MarginPaddingAlignmentSample#1](~/samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#1)]  
  
 Dans de nombreux cas, une marge uniforme n’est pas appropriée. Ainsi, il est possible d’appliquer un espacement non uniforme. L’exemple suivant montre comment appliquer un espacement de marge non uniforme aux éléments enfants. Les marges sont décrites dans cet ordre : gauche, haut, droite, bas.  
  
 [!code-cpp[MarginPaddingAlignmentSample#2](~/samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#2)]
 [!code-csharp[MarginPaddingAlignmentSample#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#2)]
 [!code-vb[MarginPaddingAlignmentSample#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#2)]
 [!code-xaml[MarginPaddingAlignmentSample#2](~/samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#2)]  
  
<a name="wcpsdk_layout_amp_padding_properties"></a>
## <a name="understanding-the-padding-property"></a>Présentation de la propriété de remplissage  
 Le rembourrage <xref:System.Windows.FrameworkElement.Margin%2A> est similaire à la plupart des égards. La propriété Padding n’est exposée que sur quelques <xref:System.Windows.Documents.Block>classes, <xref:System.Windows.Controls.Control>principalement <xref:System.Windows.Controls.TextBlock> comme une commodité: , <xref:System.Windows.Controls.Border>, et sont des échantillons de classes qui exposent une propriété De padding. La <xref:System.Windows.Controls.Border.Padding%2A> propriété agrandit la taille effective d’un élément enfant par la valeur spécifiée. <xref:System.Windows.Thickness>  
  
 L’exemple suivant montre <xref:System.Windows.Controls.Border.Padding%2A> comment <xref:System.Windows.Controls.Border> s’appliquer à un élément parent.  
  
 [!code-cpp[MarginPaddingAlignmentSample#3](~/samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#3)]
 [!code-csharp[MarginPaddingAlignmentSample#3](~/samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#3)]
 [!code-vb[MarginPaddingAlignmentSample#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#3)]
 [!code-xaml[MarginPaddingAlignmentSample#3](~/samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#3)]  
  
<a name="wcpsdk_layout_amp_summary"></a>
## <a name="using-alignment-margins-and-padding-in-an-application"></a>Utilisation de l’alignement, des marges et du remplissage dans une application  
 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, <xref:System.Windows.FrameworkElement.Margin%2A> <xref:System.Windows.Controls.Border.Padding%2A>, <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> et de fournir le contrôle [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]de positionnement nécessaire pour créer un complexe . Vous pouvez utiliser les effets de chaque propriété pour changer le positionnement d’un élément enfant. Cela vous apporte une plus grande souplesse pour créer des applications dynamiques et une expérience utilisateur saisissante.  
  
 L’exemple suivant illustre chacun des concepts détaillés dans cette rubrique. S’appuyant sur l’infrastructure trouvée dans le premier <xref:System.Windows.Controls.Grid> échantillon de ce <xref:System.Windows.Controls.Border> sujet, cet exemple ajoute un élément comme un enfant du premier échantillon. <xref:System.Windows.Controls.Border.Padding%2A>s’applique à <xref:System.Windows.Controls.Border> l’élément parent. L’est <xref:System.Windows.Controls.Grid> utilisé pour répartir l’espace entre trois éléments enfant. <xref:System.Windows.Controls.StackPanel> <xref:System.Windows.Controls.Button>éléments sont à nouveau utilisés <xref:System.Windows.FrameworkElement.Margin%2A> pour <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>montrer les différents effets de et . <xref:System.Windows.Controls.TextBlock>éléments sont ajoutés à chacun <xref:System.Windows.Controls.ColumnDefinition> pour mieux <xref:System.Windows.Controls.Button> définir les différentes propriétés appliquées aux éléments de chaque colonne.  
  
 [!code-cpp[MarginPaddingAlignmentSample#4](~/samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#4)]
 [!code-csharp[MarginPaddingAlignmentSample#4](~/samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#4)]
 [!code-vb[MarginPaddingAlignmentSample#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#4)]
 [!code-xaml[MarginPaddingAlignmentSample#4](~/samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#4)]  
  
 Une fois compilée, l’application précédente présente une [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] semblable à l’illustration suivante. Les effets des diverses valeurs de propriété sont évidents dans l’espacement entre les <xref:System.Windows.Controls.TextBlock> éléments, et les valeurs de propriété significatives pour des éléments dans chaque colonne sont montrées dans les éléments.  
  
 ![Plusieurs propriétés de positionnement dans une application](./media/layout-margins-padding-aligment-graphic3.PNG "layout_margins_padding_aligment_graphic3")  
  
<a name="wcpsdk_layout_amp_alignment_whatsnext"></a>
## <a name="whats-next"></a>Étapes suivantes  
 Les propriétés de <xref:System.Windows.FrameworkElement> positionnement définies par [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] la classe permettent un contrôle fin du placement d’éléments dans les applications. Vous disposez désormais de plusieurs techniques pour mieux positionner les éléments à l’aide de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Des ressources supplémentaires expliquent plus en détail la disposition [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Le sujet [de l’aperçu des panneaux](../controls/panels-overview.md) contient plus de détails sur les différents <xref:System.Windows.Controls.Panel> éléments. Le sujet [Pas à pas: Ma première application de bureau WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md) introduit des techniques avancées qui utilisent des éléments de mise en page pour positionner les composants et lier leurs actions aux sources de données.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.FrameworkElement>
- <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>
- <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>
- <xref:System.Windows.FrameworkElement.Margin%2A>
- [Vue d’ensemble de Panel](../controls/panels-overview.md)
- [Disposition](layout.md)
- [Galerie de dispositions WPF, exemple](https://go.microsoft.com/fwlink/?LinkID=160054)
