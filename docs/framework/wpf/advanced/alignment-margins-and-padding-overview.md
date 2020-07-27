---
title: Vue d'ensemble de l'alignement, des marges et du remplissage
description: En savoir plus sur HorizontalAlignment, Margin, Padding et VerticalAlignment, qui contrôlent la position des éléments enfants dans les applications Windows Presentation Foundation.
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
ms.openlocfilehash: 832325086c85a7b044876e825d93e0b680a0b99c
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165889"
---
# <a name="alignment-margins-and-padding-overview"></a>Vue d'ensemble de l'alignement, des marges et du remplissage
La <xref:System.Windows.FrameworkElement> classe expose plusieurs propriétés utilisées pour positionner des éléments enfants avec précision. Cette rubrique présente quatre des propriétés les plus importantes : <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> , <xref:System.Windows.FrameworkElement.Margin%2A> , <xref:System.Windows.Controls.Border.Padding%2A> et <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> . Il est important de comprendre les effets de ces propriétés, car elles servent de base au contrôle de la position des éléments dans les applications [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  

<a name="wcpsdk_layout_amp_introduction"></a>
## <a name="introduction-to-element-positioning"></a>Introduction au positionnement d’un élément  
 Il existe de nombreuses manières de positionner des éléments à l’aide de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Toutefois, l’obtention d’une disposition idéale va au-delà du simple choix de l' <xref:System.Windows.Controls.Panel> élément approprié. Le contrôle précis du positionnement requiert une compréhension des <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> Propriétés,, <xref:System.Windows.FrameworkElement.Margin%2A> <xref:System.Windows.Controls.Border.Padding%2A> et <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> .  
  
 L’illustration suivante montre un scénario de disposition qui utilise plusieurs propriétés de positionnement.  
  
 ![Exemple de propriétés de positionnement WPF](./media/layout-margins-padding-alignment-graphic1.PNG "layout_margins_padding_alignment_graphic1")  
  
 À première vue, les <xref:System.Windows.Controls.Button> éléments de cette illustration peuvent sembler être placés de façon aléatoire. Toutefois, leurs positions sont contrôlées de manière précise à l’aide d’une combinaison d’informations relatives aux marges, aux alignements et au remplissage.  
  
 L’exemple suivant décrit comment créer la disposition de l’illustration précédente. Un <xref:System.Windows.Controls.Border> élément encapsule un parent <xref:System.Windows.Controls.StackPanel> , avec une <xref:System.Windows.Controls.Border.Padding%2A> valeur de 15 DIP (Device Independent Pixel). Il s’agit de la <xref:System.Windows.Media.Brushes.LightBlue%2A> bande étroite qui entoure l’enfant <xref:System.Windows.Controls.StackPanel> . Les éléments enfants du <xref:System.Windows.Controls.StackPanel> sont utilisés pour illustrer chacune des diverses propriétés de positionnement détaillées dans cette rubrique. Trois <xref:System.Windows.Controls.Button> éléments sont utilisés pour illustrer les <xref:System.Windows.FrameworkElement.Margin%2A> <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> Propriétés et.  
  
 [!code-csharp[MPALayoutSampleIntro#1](~/samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutSampleIntro/CSharp/MPA_Layout_Sample_Intro.cs#1)]
 [!code-vb[MPALayoutSampleIntro#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutSampleIntro/VisualBasic/MPALayoutIntro.vb#1)]  
  
 Le diagramme suivant fournit un gros plan de l’affichage des différentes propriétés de positionnement utilisées dans l’exemple précédent. Les sections suivantes de cette rubrique décrivent plus en détail la manière d’utiliser chaque propriété de positionnement.  
  
 ![Propriétés de positionnement avec&#45;d’appels d’écran](./media/layout-margins-padding-alignment-graphic2.PNG "layout_margins_padding_alignment_graphic2")  
  
<a name="wcpsdk_layout_amp_alignment_properties"></a>
## <a name="understanding-alignment-properties"></a>Présentation des propriétés d’alignement  
 Les <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> Propriétés et décrivent comment un élément enfant doit être positionné dans l’espace de disposition alloué d’un élément parent. En utilisant ces propriétés ensemble, vous pouvez positionner des éléments enfants avec précision. Par exemple, les éléments enfants d’un <xref:System.Windows.Controls.DockPanel> peuvent spécifier quatre alignements horizontaux différents : <xref:System.Windows.HorizontalAlignment.Left> , <xref:System.Windows.HorizontalAlignment.Right> , ou <xref:System.Windows.HorizontalAlignment.Center> , ou pour remplir l' <xref:System.Windows.HorizontalAlignment.Stretch> espace disponible. Des valeurs similaires sont disponibles pour le positionnement vertical.  
  
> [!NOTE]
> <xref:System.Windows.FrameworkElement.Height%2A>Les propriétés et définies explicitement <xref:System.Windows.FrameworkElement.Width%2A> sur un élément sont prioritaires sur la <xref:System.Windows.HorizontalAlignment.Stretch> valeur de la propriété. Toute tentative de définition de <xref:System.Windows.FrameworkElement.Height%2A> , de <xref:System.Windows.FrameworkElement.Width%2A> et <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> d’une valeur de `Stretch` entraîne l’ignorance de la `Stretch` demande.  
  
<a name="wcpsdk_layout_amp_horizontalalignment_properties"></a>
### <a name="horizontalalignment-property"></a>Propriété HorizontalAlignment  
 La <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> propriété déclare les caractéristiques d’alignement horizontal à appliquer aux éléments enfants. Le tableau suivant montre chacune des valeurs possibles de la <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> propriété.  
  
|Membre|Description|  
|------------|-----------------|  
|<xref:System.Windows.HorizontalAlignment.Left>|Les éléments enfants sont alignés à gauche de l’espace de disposition alloué par l’élément parent.|  
|<xref:System.Windows.HorizontalAlignment.Center>|Les éléments enfants sont alignés au centre de l’espace de disposition alloué par l’élément parent.|  
|<xref:System.Windows.HorizontalAlignment.Right>|Les éléments enfants sont alignés à droite de l’espace de disposition alloué par l’élément parent.|  
|<xref:System.Windows.HorizontalAlignment.Stretch> (par défaut)|Les éléments enfants sont étirés pour remplir l’espace de disposition alloué par l’élément parent. <xref:System.Windows.FrameworkElement.Width%2A>Les valeurs explicites et <xref:System.Windows.FrameworkElement.Height%2A> sont prioritaires.|  
  
 L’exemple suivant montre comment appliquer la <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> propriété à des <xref:System.Windows.Controls.Button> éléments. Chaque valeur d’attribut est présentée pour mieux illustrer les différents comportements de rendu.  
  
 [!code-csharp[MPALayoutHorizontalAlignment#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutHorizontalAlignment/CSharp/MPA_Layout_HorizontalAlignment.cs#2)]
 [!code-vb[MPALayoutHorizontalAlignment#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutHorizontalAlignment/VisualBasic/MPA_Layout_HorizontalAlignment.vb#2)]  
  
 Le code précédent permet d’obtenir une disposition semblable à l’image suivante. Les effets de positionnement de chaque <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> valeur sont visibles dans l’illustration.  
  
 ![Exemple d'alignement horizontal](./media/layout-horizontal-alignment-graphic.PNG "layout_horizontal_alignment_graphic")  
  
<a name="wcpsdk_layout_amp_verticalalignment_properties"></a>
### <a name="verticalalignment-property"></a>Propriété VerticalAlignment  
 La <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> propriété décrit les caractéristiques d’alignement vertical à appliquer aux éléments enfants. Le tableau suivant montre chacune des valeurs possibles pour la <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> propriété.  
  
|Membre|Description|  
|------------|-----------------|  
|<xref:System.Windows.VerticalAlignment.Top>|Les éléments enfants sont alignés en haut de l’espace de disposition alloué par l’élément parent.|  
|<xref:System.Windows.VerticalAlignment.Center>|Les éléments enfants sont alignés au centre de l’espace de disposition alloué par l’élément parent.|  
|<xref:System.Windows.VerticalAlignment.Bottom>|Les éléments enfants sont alignés en bas de l’espace de disposition alloué par l’élément parent.|  
|<xref:System.Windows.VerticalAlignment.Stretch> (par défaut)|Les éléments enfants sont étirés pour remplir l’espace de disposition alloué par l’élément parent. <xref:System.Windows.FrameworkElement.Width%2A>Les valeurs explicites et <xref:System.Windows.FrameworkElement.Height%2A> sont prioritaires.|  
  
 L’exemple suivant montre comment appliquer la <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> propriété à des <xref:System.Windows.Controls.Button> éléments. Chaque valeur d’attribut est présentée pour mieux illustrer les différents comportements de rendu. Dans le cadre de cet exemple, un <xref:System.Windows.Controls.Grid> élément avec un quadrillage visible est utilisé comme parent, pour mieux illustrer le comportement de disposition de chaque valeur de propriété.  
  
 [!code-csharp[MPALayoutVerticalAlignment#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutVerticalAlignment/CSharp/MPA_Layout_VerticalAlignment.cs#2)]
 [!code-vb[MPALayoutVerticalAlignment#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutVerticalAlignment/VisualBasic/MPA_Layout_VerticalAlignment.vb#2)]
 [!code-xaml[MPALayoutVerticalAlignment#2](~/samples/snippets/xaml/VS_Snippets_Wpf/MPALayoutVerticalAlignment/XAML/default.xaml#2)]  
  
 Le code précédent permet d’obtenir une disposition semblable à l’image suivante. Les effets de positionnement de chaque <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> valeur sont visibles dans l’illustration.  
  
 ![Exemple de propriété VerticalAlignment](./media/layout-vertical-alignment-graphic.PNG "layout_vertical_alignment_graphic")  
  
<a name="wcpsdk_layout_amp_margin_properties"></a>
## <a name="understanding-margin-properties"></a>Présentation des propriétés de marge  
 La <xref:System.Windows.FrameworkElement.Margin%2A> propriété décrit la distance entre un élément et son enfant ou ses pairs. <xref:System.Windows.FrameworkElement.Margin%2A>les valeurs peuvent être uniformes, en utilisant une syntaxe telle que `Margin="20"` . Avec cette syntaxe, une uniforme <xref:System.Windows.FrameworkElement.Margin%2A> de 20 pixels indépendants du périphérique est appliquée à l’élément. <xref:System.Windows.FrameworkElement.Margin%2A>les valeurs peuvent également prendre la forme de quatre valeurs distinctes, chaque valeur décrivant une marge distincte à appliquer à gauche, en haut, à droite et en bas (dans cet ordre), comme `Margin="0,10,5,25"` . L’utilisation correcte de la <xref:System.Windows.FrameworkElement.Margin%2A> propriété permet un contrôle très précis de la position de rendu d’un élément et de la position de rendu de ses éléments voisins et enfants.  
  
> [!NOTE]
> Une marge différente de zéro applique un espace en dehors de <xref:System.Windows.FrameworkElement.ActualWidth%2A> et de <xref:System.Windows.FrameworkElement.ActualHeight%2A> .  
  
 L’exemple suivant montre comment appliquer des marges uniformes autour d’un groupe d' <xref:System.Windows.Controls.Button> éléments. Les <xref:System.Windows.Controls.Button> éléments sont espacés uniformément avec une mémoire tampon de marge de dix pixels dans chaque direction.  
  
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
 Le remplissage est semblable à <xref:System.Windows.FrameworkElement.Margin%2A> dans la plupart des aspects. La propriété de remplissage est exposée uniquement sur quelques classes, principalement à des fins pratiques : <xref:System.Windows.Documents.Block> , <xref:System.Windows.Controls.Border> , <xref:System.Windows.Controls.Control> et <xref:System.Windows.Controls.TextBlock> sont des exemples de classes qui exposent une propriété de remplissage. La <xref:System.Windows.Controls.Border.Padding%2A> propriété agrandit la taille effective d’un élément enfant par la valeur spécifiée <xref:System.Windows.Thickness> .  
  
 L’exemple suivant montre comment appliquer <xref:System.Windows.Controls.Border.Padding%2A> à un élément parent <xref:System.Windows.Controls.Border> .  
  
 [!code-cpp[MarginPaddingAlignmentSample#3](~/samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#3)]
 [!code-csharp[MarginPaddingAlignmentSample#3](~/samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#3)]
 [!code-vb[MarginPaddingAlignmentSample#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#3)]
 [!code-xaml[MarginPaddingAlignmentSample#3](~/samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#3)]  
  
<a name="wcpsdk_layout_amp_summary"></a>
## <a name="using-alignment-margins-and-padding-in-an-application"></a>Utilisation de l’alignement, des marges et du remplissage dans une application  
 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, <xref:System.Windows.FrameworkElement.Margin%2A> , <xref:System.Windows.Controls.Border.Padding%2A> et <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> fournissent le contrôle de positionnement nécessaire pour créer un complexe [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] . Vous pouvez utiliser les effets de chaque propriété pour changer le positionnement d’un élément enfant. Cela vous apporte une plus grande souplesse pour créer des applications dynamiques et une expérience utilisateur saisissante.  
  
 L’exemple suivant illustre chacun des concepts détaillés dans cette rubrique. En s’appuyant sur l’infrastructure figurant dans le premier exemple de cette rubrique, cet exemple ajoute un <xref:System.Windows.Controls.Grid> élément en tant qu’enfant de <xref:System.Windows.Controls.Border> dans le premier exemple. <xref:System.Windows.Controls.Border.Padding%2A>est appliqué à l' <xref:System.Windows.Controls.Border> élément parent. Le <xref:System.Windows.Controls.Grid> est utilisé pour partitionner l’espace entre trois <xref:System.Windows.Controls.StackPanel> éléments enfants. <xref:System.Windows.Controls.Button>les éléments sont à nouveau utilisés pour afficher les divers effets de <xref:System.Windows.FrameworkElement.Margin%2A> et <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> . <xref:System.Windows.Controls.TextBlock>des éléments sont ajoutés à chacun <xref:System.Windows.Controls.ColumnDefinition> pour mieux définir les différentes propriétés appliquées aux <xref:System.Windows.Controls.Button> éléments dans chaque colonne.  
  
 [!code-cpp[MarginPaddingAlignmentSample#4](~/samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#4)]
 [!code-csharp[MarginPaddingAlignmentSample#4](~/samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#4)]
 [!code-vb[MarginPaddingAlignmentSample#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#4)]
 [!code-xaml[MarginPaddingAlignmentSample#4](~/samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#4)]  
  
 Une fois compilée, l’application précédente présente une [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] semblable à l’illustration suivante. Les effets des différentes valeurs de propriété sont évidents dans l’espacement entre les éléments, et les valeurs de propriété significatives pour les éléments de chaque colonne sont affichées dans les <xref:System.Windows.Controls.TextBlock> éléments.  
  
 ![Plusieurs propriétés de positionnement dans une application](./media/layout-margins-padding-aligment-graphic3.PNG "layout_margins_padding_aligment_graphic3")  
  
<a name="wcpsdk_layout_amp_alignment_whatsnext"></a>
## <a name="whats-next"></a>Prochaine étape  
 Les propriétés de positionnement définies par la <xref:System.Windows.FrameworkElement> classe permettent un contrôle précis de l’emplacement des éléments dans les [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications. Vous disposez désormais de plusieurs techniques pour mieux positionner les éléments à l’aide de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Des ressources supplémentaires expliquent plus en détail la disposition [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. La rubrique [vue d’ensemble des panneaux](../controls/panels-overview.md) contient plus de détails sur les différents <xref:System.Windows.Controls.Panel> éléments. La rubrique [procédure pas à pas : ma première application de bureau WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md) présente des techniques avancées qui utilisent des éléments de disposition pour positionner des composants et lier leurs actions à des sources de données.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.FrameworkElement>
- <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>
- <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>
- <xref:System.Windows.FrameworkElement.Margin%2A>
- [Vue d'ensemble de Panel](../controls/panels-overview.md)
- [Disposition](layout.md)
- [Galerie de dispositions WPF, exemple](https://go.microsoft.com/fwlink/?LinkID=160054)
