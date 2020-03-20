---
title: Vue d'ensemble de Panel
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Panel control [WPF], about Panel control
- controls [WPF], Panel
ms.assetid: f73644af-9941-4611-8754-6d4cef03fc44
ms.openlocfilehash: 7810bfbf4f5bedf51e0797a4b9017f589e0b0a8a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187576"
---
# <a name="panels-overview"></a>Vue d'ensemble de Panel
<xref:System.Windows.Controls.Panel>sont des composants qui contrôlent le rendu des éléments , leur taille et leurs dimensions, leur position et l’arrangement de leur contenu pour enfants. Le [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fournit un certain nombre <xref:System.Windows.Controls.Panel> d’éléments prédéfinis <xref:System.Windows.Controls.Panel> ainsi que la possibilité de construire des éléments personnalisés.  
  
 Cette rubrique contient les sections suivantes.  
  
- [La classe Panel](#Panels_view_from_10000_feet)  
  
- [Membres communs aux éléments Panel](#Panels_declared_members)  
  
- [Éléments Panel dérivés](#Panels_derived_elements)  
  
- [Éléments Panel d’interface utilisateur](#Panels_main_UI_elements)  
  
- [Éléments Panel imbriqués](#Panels_nested_panel_elements)  
  
- [Éléments Panel personnalisés](#Panels_custom_panel_elements)  
  
- [Prise en charge de la localisation/globalisation](#Panels_global_localization)  
  
<a name="Panels_view_from_10000_feet"></a>
## <a name="the-panel-class"></a>La classe Panel  
 <xref:System.Windows.Controls.Panel>est la classe de base pour [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]tous les éléments qui fournissent un support de mise en page dans . Les <xref:System.Windows.Controls.Panel> éléments dérivés sont utilisés [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pour positionner et organiser des éléments et coder.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] comprend une suite complète d’implémentations Panel dérivées qui permettent la mise en œuvre de nombreuses dispositions complexes. Ces classes dérivées exposent des propriétés et des méthodes qui rendent possibles la plupart des scénarios [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] standard. Les développeurs qui sont incapables de trouver un comportement d’arrangement pour <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> <xref:System.Windows.FrameworkElement.MeasureOverride%2A> enfants qui répond à leurs besoins peuvent créer de nouvelles mises en page en l’emportent sur les méthodes et les méthodes. Pour plus d’informations sur les comportements de disposition personnalisés, consultez [Éléments Panel personnalisés](#Panels_custom_panel_elements).  
  
<a name="Panels_declared_members"></a>
## <a name="panel-common-members"></a>Membres communs aux éléments Panel  
 Tous <xref:System.Windows.Controls.Panel> les éléments prennent en charge les <xref:System.Windows.FrameworkElement>propriétés de dimensionnement et de positionnement de base définies par , <xref:System.Windows.FrameworkElement.Height%2A>y compris , <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> <xref:System.Windows.FrameworkElement.Margin%2A>, et <xref:System.Windows.FrameworkElement.LayoutTransform%2A>. Pour plus d’informations sur <xref:System.Windows.FrameworkElement>les propriétés de positionnement définies par , voir [Alignement, marges et aperçu de padding](../advanced/alignment-margins-and-padding-overview.md).  
  
 <xref:System.Windows.Controls.Panel>expose d’autres propriétés qui sont d’une importance cruciale dans la compréhension et l’utilisation de la mise en page. La <xref:System.Windows.Controls.Panel.Background%2A> propriété est utilisée pour remplir la zone entre les <xref:System.Windows.Media.Brush>limites d’un élément de panneau dérivé avec un . <xref:System.Windows.Controls.Panel.Children%2A>représente la collection d’éléments pour enfants dont il <xref:System.Windows.Controls.Panel> est composé. <xref:System.Windows.Controls.Panel.InternalChildren%2A>représente le contenu <xref:System.Windows.Controls.Panel.Children%2A> de la collection ainsi que les membres générés par la liaison de données. Les deux <xref:System.Windows.Controls.UIElementCollection> se composent d’un <xref:System.Windows.Controls.Panel>des éléments de l’enfant hébergé au sein du parent .  
  
 Panel expose également <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType> une propriété jointe qui peut être utilisée <xref:System.Windows.Controls.Panel>pour atteindre l’ordre en couches dans un dérivé . Les membres de <xref:System.Windows.Controls.Panel.Children%2A> la collection <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType> d’un groupe spécial ayant <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType> une valeur plus élevée apparaissent devant ceux qui ont une valeur inférieure. Ceci est particulièrement utile <xref:System.Windows.Controls.Canvas> pour <xref:System.Windows.Controls.Grid> les panneaux tels que et qui permettent aux enfants de partager le même espace de coordonnées.  
  
 <xref:System.Windows.Controls.Panel>définit également <xref:System.Windows.Controls.Panel.OnRender%2A> la méthode, qui peut être utilisée pour <xref:System.Windows.Controls.Panel>remplacer le comportement de présentation par défaut d’un .  
  
#### <a name="attached-properties"></a>Propriétés jointes  
 Les éléments Panel dérivés utilisent beaucoup les propriétés jointes. Une propriété attenante est une forme spécialisée de propriété de dépendance qui n’a pas la langue commune conventionnelle runtime (CLR) propriété "wrapper". Les propriétés jointes présentent une syntaxe spécialisée dans [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], visible dans plusieurs des exemples qui suivent.  
  
 Une des finalités d’une propriété jointe est de permettre aux éléments enfants de stocker les valeurs uniques d’une propriété définie en fait par un élément parent. Une application de cette fonctionnalité est de faire en sorte que les éléments enfants informent le parent sur la manière dont ils doivent être présentés dans l’interface utilisateur (IU) [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)], ce qui est extrêmement utile pour la disposition de l’application. Pour plus d’informations, consultez [Vue d’ensemble des propriétés jointes](../advanced/attached-properties-overview.md).  
  
<a name="Panels_derived_elements"></a>
## <a name="derived-panel-elements"></a>Éléments Panel dérivés  
 Beaucoup d’objets dérivent de <xref:System.Windows.Controls.Panel>, mais pas tous d’entre eux sont destinés à une utilisation comme fournisseurs de mise en page des racines. Il ya six classes<xref:System.Windows.Controls.Canvas> <xref:System.Windows.Controls.DockPanel>de <xref:System.Windows.Controls.Grid> <xref:System.Windows.Controls.StackPanel>panneau <xref:System.Windows.Controls.VirtualizingStackPanel>définis ( , , , , , et <xref:System.Windows.Controls.WrapPanel>) qui sont conçus spécifiquement pour la création d’application [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
 Chaque élément Panel encapsule sa propre fonctionnalité spéciale, comme indiqué dans le tableau suivant.  
  
|Nom de l’élément|Élément Panel d’IU ?|Description|  
|------------------|---------------|-----------------|  
|<xref:System.Windows.Controls.Canvas>|Oui|Définit une zone dans laquelle vous pouvez positionner explicitement <xref:System.Windows.Controls.Canvas> les éléments de l’enfant par coordonnées par rapport à la zone.|  
|<xref:System.Windows.Controls.DockPanel>|Oui|Définit une zone dans laquelle vous pouvez réorganiser des éléments enfants horizontalement ou verticalement, les uns par rapport aux autres.|  
|<xref:System.Windows.Controls.Grid>|Oui|Définit une zone de grille flexible composée de colonnes et de lignes. Les éléments <xref:System.Windows.Controls.Grid> de l’enfant d’un peut être positionné précisément en utilisant la <xref:System.Windows.FrameworkElement.Margin%2A> propriété.|  
|<xref:System.Windows.Controls.StackPanel>|Oui|Dispose des éléments enfants sur une seule ligne orientée horizontalement ou verticalement.|  
|<xref:System.Windows.Controls.Primitives.TabPanel>|Non |Gère la disposition des boutons <xref:System.Windows.Controls.TabControl>d’onglet dans un .|  
|<xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>|Non |Dispose le contenu <xref:System.Windows.Controls.ToolBar> dans un contrôle.|  
|<xref:System.Windows.Controls.Primitives.UniformGrid>|Non |<xref:System.Windows.Controls.Primitives.UniformGrid>est utilisé pour organiser les enfants dans une grille avec toutes les tailles de cellules égales.|  
|<xref:System.Windows.Controls.VirtualizingPanel>|Non |Fournit une classe de base pour les éléments Panel qui peuvent « virtualiser » leur collection d’enfants.|  
|<xref:System.Windows.Controls.VirtualizingStackPanel>|Oui|Organise et virtualise un contenu sur une seule ligne orientée horizontalement ou verticalement.|  
|<xref:System.Windows.Controls.WrapPanel>|Oui|<xref:System.Windows.Controls.WrapPanel>positionne les éléments de l’enfant en position séquentielle de gauche à droite, brisant le contenu à la ligne suivante au bord de la boîte contenante. La commande subséquente se produit séquentiellement de haut en bas <xref:System.Windows.Controls.WrapPanel.Orientation%2A> ou de droite à gauche, selon la valeur de la propriété.|  
  
<a name="Panels_main_UI_elements"></a>
## <a name="user-interface-panels"></a>Éléments Panel d’interface utilisateur  
 Il ya six classes [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de panneau disponibles qui <xref:System.Windows.Controls.DockPanel>sont <xref:System.Windows.Controls.Grid> <xref:System.Windows.Controls.StackPanel>optimisés <xref:System.Windows.Controls.WrapPanel>pour soutenir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] les scénarios: <xref:System.Windows.Controls.Canvas>, , , , <xref:System.Windows.Controls.VirtualizingStackPanel>et . Ces éléments Panel sont simples d’utilisation, polyvalents et suffisamment extensibles pour la plupart des applications.  
  
 Chaque <xref:System.Windows.Controls.Panel> élément dérivé traite différemment les contraintes de dimensionnement. Comprendre comment <xref:System.Windows.Controls.Panel> une poignée des contraintes dans la direction horizontale ou verticale peut rendre la disposition plus prévisible.  
  
|**Nom du panneau**|**Dimension x**|**Dimension y**|  
|--------------------|----------------------|----------------------|  
|<xref:System.Windows.Controls.Canvas>|Restreinte au contenu|Restreinte au contenu|  
|<xref:System.Windows.Controls.DockPanel>|Restreinte|Restreinte|  
|<xref:System.Windows.Controls.StackPanel>(Orientation verticale)|Restreinte|Restreinte au contenu|  
|<xref:System.Windows.Controls.StackPanel>(Orientation horizontale)|Restreinte au contenu|Restreinte|  
|<xref:System.Windows.Controls.Grid>|Restreinte|Contrainte, sauf dans <xref:System.Windows.GridUnitType.Auto> les cas où elles s’appliquent aux rangées et aux colonnes|  
|<xref:System.Windows.Controls.WrapPanel>|Restreinte au contenu|Restreinte au contenu|  
  
 Vous trouverez des descriptions plus détaillées et des exemples d’utilisation de chacun de ces éléments ci-dessous.  
  
<a name="Panels_overview_Canvas_subsection"></a>
### <a name="canvas"></a>Canevas  
 L’élément <xref:System.Windows.Controls.Canvas> permet le positionnement du contenu en fonction des coordonnées *X* et *y* absolues. Les éléments peuvent être dessinés dans un emplacement unique, ou s’ils occupent les mêmes coordonnées, l’ordre dans lequel ils apparaissent dans le balisage détermine l’ordre dans lequel ils sont dessinés.  
  
 <xref:System.Windows.Controls.Canvas>fournit le support de <xref:System.Windows.Controls.Panel>mise en page le plus flexible de tout . Les propriétés de hauteur et de largeur sont utilisées pour définir la zone de <xref:System.Windows.Controls.Canvas>la toile, et les éléments à l’intérieur sont attribués coordonnées absolues par rapport à la zone du parent. Quatre propriétés <xref:System.Windows.Controls.Canvas.Left%2A?displayProperty=nameWithType> <xref:System.Windows.Controls.Canvas.Top%2A?displayProperty=nameWithType>attachées, , , <xref:System.Windows.Controls.Canvas.Right%2A?displayProperty=nameWithType> et <xref:System.Windows.Controls.Canvas.Bottom%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.Canvas>permettent le contrôle fin du placement de l’objet dans un , permettant au développeur de positionner et d’organiser des éléments précisément sur l’écran.  
  
#### <a name="cliptobounds-within-a-canvas"></a>Propriété ClipToBounds à l’intérieur d’un élément Canvas  
 <xref:System.Windows.Controls.Canvas>peut positionner des éléments d’enfant à n’importe quelle position <xref:System.Windows.FrameworkElement.Height%2A> <xref:System.Windows.FrameworkElement.Width%2A>sur l’écran, même à des coordonnées qui sont en dehors de sa propre définition et . En <xref:System.Windows.Controls.Canvas> outre, n’est pas affectée par la taille de ses enfants. En conséquence, il est possible pour un élément enfant de surdraw <xref:System.Windows.Controls.Canvas>d’autres éléments en dehors du rectangle de délimitation du parent . Le comportement par <xref:System.Windows.Controls.Canvas> défaut d’un est de permettre aux <xref:System.Windows.Controls.Canvas>enfants d’être dessinés en dehors des limites du parent . Si ce comportement n’est <xref:System.Windows.UIElement.ClipToBounds%2A> pas souhaitable, `true`la propriété peut être définie à . Cela <xref:System.Windows.Controls.Canvas> provoque de clip à sa propre taille. <xref:System.Windows.Controls.Canvas>est le seul élément de mise en page qui permet aux enfants d’être dessinés en dehors de ses limites.  
  
 Ce comportement est illustré en images dans l’[exemple de comparaison des propriétés Width](https://github.com/Microsoft/WPF-Samples/tree/master/Elements/WidthProperties).  
  
#### <a name="defining-and-using-a-canvas"></a>Définition et utilisation d’un élément Canvas  
 A <xref:System.Windows.Controls.Canvas> peut être instantanée simplement [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] en utilisant ou en code. L’exemple suivant montre <xref:System.Windows.Controls.Canvas> comment utiliser pour positionner absolument le contenu. Ce code génère trois carrés de 100 pixels de côté. Le premier carré est rouge, et la position de son angle supérieur gauche (*x, y*) est définie sur (0, 0). Le deuxième carré est vert, et la position de son angle supérieur gauche est définie sur (100, 100), juste en dessous et à droite du premier carré. Le troisième carré est bleu, et la position de son angle supérieur gauche est définie sur (50, 50). Il englobe ainsi le quart inférieur droit du premier carré et le quart supérieur gauche du deuxième. Comme le troisième carré est disposé en dernier, il apparaît au-dessus des deux autres carrés, c’est-à-dire que les parties qui se chevauchent prennent la couleur de ce troisième carré.  
  
 [!code-csharp[CanvasOvwSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CanvasOvwSample/CSharp/Canvas_Ovw_Sample.cs#1)]
 [!code-vb[CanvasOvwSample#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasOvwSample/VisualBasic/canvas_vb.vb#1)]
 [!code-xaml[CanvasOvwSample#1](~/samples/snippets/xaml/VS_Snippets_Wpf/CanvasOvwSample/XAML/default.xaml#1)]  
  
 L’application compilée produit une nouvelle IU qui ressemble à ceci :  
  
 ![Élément Canevas classique.](./media/panel-intro-canvas.PNG "panel_intro_canvas")  
  
<a name="Panels_overview_DockPanel_subsection"></a>
### <a name="dockpanel"></a>DockPanel  
 L’élément <xref:System.Windows.Controls.DockPanel> <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> utilise la propriété ci-jointe comme ensemble dans les éléments de contenu pour enfants pour positionner le contenu le long des bords d’un conteneur. Lorsqu’il <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> <xref:System.Windows.Controls.Dock.Top> est <xref:System.Windows.Controls.Dock.Bottom>réglé ou, il positionne les éléments de l’enfant au-dessus ou en dessous de l’autre. Quand <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> est <xref:System.Windows.Controls.Dock.Left> réglé <xref:System.Windows.Controls.Dock.Right>ou, il positionne des éléments d’enfant à gauche ou à droite les uns des autres. La <xref:System.Windows.Controls.DockPanel.LastChildFill%2A> propriété détermine la position de l’élément <xref:System.Windows.Controls.DockPanel>final ajouté comme un enfant d’un .  
  
 Vous pouvez <xref:System.Windows.Controls.DockPanel> utiliser pour positionner un groupe de contrôles connexes, comme un ensemble de boutons. Alternativement, vous pouvez l’utiliser pour [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]créer un "paned", similaire à celui trouvé dans Microsoft Outlook.  
  
#### <a name="sizing-to-content"></a>Dimensionnement en fonction du contenu  
 Si <xref:System.Windows.FrameworkElement.Height%2A> son <xref:System.Windows.FrameworkElement.Width%2A> et ses <xref:System.Windows.Controls.DockPanel> propriétés ne sont pas spécifiées, les tailles de son contenu. La taille peut augmenter ou diminuer pour s’adapter à la taille de ses éléments enfants. Toutefois, lorsque ces propriétés sont spécifiées et qu’il <xref:System.Windows.Controls.DockPanel> n’y a plus de place pour le prochain élément enfant spécifié, ne présente pas cet élément enfant ou les éléments subséquents de l’enfant et ne mesure pas les éléments ultérieurs de l’enfant.  
  
#### <a name="lastchildfill"></a>Propriété LastChildFill  
 Par défaut, le dernier <xref:System.Windows.Controls.DockPanel> enfant d’un élément « remplira » l’espace restant non alloué. Si ce comportement n’est <xref:System.Windows.Controls.DockPanel.LastChildFill%2A> pas `false`souhaité, définissez la propriété à .  
  
#### <a name="defining-and-using-a-dockpanel"></a>Définition et utilisation d’un élément DockPanel  
 L’exemple suivant montre comment cloisonner l’espace à l’aide d’un <xref:System.Windows.Controls.DockPanel>. Cinq <xref:System.Windows.Controls.Border> éléments sont ajoutés <xref:System.Windows.Controls.DockPanel>comme enfants d’un parent . Chacun utilise une propriété de <xref:System.Windows.Controls.DockPanel> positionnement différente d’un espace de partition. Le dernier élément « remplit » l’espace non alloué restant.  
  
 [!code-cpp[DockPanelOvwSample#1](~/samples/snippets/cpp/VS_Snippets_Wpf/DockPanelOvwSample/CPP/DockPanel_Ovw_Sample.cpp#1)]
 [!code-csharp[DockPanelOvwSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/DockPanelOvwSample/CSharp/DockPanel_Ovw_Sample.cs#1)]
 [!code-vb[DockPanelOvwSample#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelOvwSample/VisualBasic/dockpanel_vb.vb#1)]
 [!code-xaml[DockPanelOvwSample#1](~/samples/snippets/xaml/VS_Snippets_Wpf/DockPanelOvwSample/XAML/default.xaml#1)]  
  
 L’application compilée produit une nouvelle IU qui ressemble à ceci :  
  
 ![Scénario DockPanel classique.](./media/panel-intro-dockpanel.PNG "panel_intro_dockpanel")  
  
<a name="Panels_overview_Grid_subsection"></a>
### <a name="grid"></a>Grille  
 L’élément <xref:System.Windows.Controls.Grid> fusionne la fonctionnalité d’un positionnement absolu et d’un contrôle des données tabulaires. A <xref:System.Windows.Controls.Grid> vous permet de positionner facilement et de styler les éléments. <xref:System.Windows.Controls.Grid>vous permet de définir des regroupements flexibles de lignes et de <xref:System.Windows.Controls.Grid> colonnes, et fournit même un mécanisme pour partager des informations de dimensionnement entre plusieurs éléments.  
  
#### <a name="how-is-grid-different-from-table"></a>En quoi un élément Grid diffère-t-il d’un élément Table ?  
 <xref:System.Windows.Documents.Table>et <xref:System.Windows.Controls.Grid> partager certaines fonctionnalités communes, mais chacun est le mieux adapté pour différents scénarios. A <xref:System.Windows.Documents.Table> est conçu pour une utilisation dans le contenu du flux (voir [Flow Document Aperçu](../advanced/flow-document-overview.md) pour plus d’informations sur le contenu du flux). Les grilles conviennent particulièrement aux formulaires (autrement dit, partout, sauf dans du contenu dynamique). Dans <xref:System.Windows.Documents.FlowDocument>un <xref:System.Windows.Documents.Table> , prend en charge les comportements de contenu de <xref:System.Windows.Controls.Grid> flux comme la pagination, le reflow de colonne, et la sélection de contenu tandis qu’un n’est pas. A <xref:System.Windows.Controls.Grid> d’autre part est mieux <xref:System.Windows.Documents.FlowDocument> utilisé en <xref:System.Windows.Controls.Grid> dehors d’un pour de <xref:System.Windows.Documents.Table> nombreuses raisons, y compris les éléments ajoutés basés sur une ligne et l’indice de colonne, ne. L’élément <xref:System.Windows.Controls.Grid> permet la superposition de contenu pour enfants, permettant à plus d’un élément d’exister dans une seule « cellule ». <xref:System.Windows.Documents.Table>ne prend pas en charge la superposition. Les éléments <xref:System.Windows.Controls.Grid> de l’enfant d’un peut être absolument positionné par rapport à la zone de leurs limites de « cellule ». <xref:System.Windows.Documents.Table>ne prend pas en charge cette fonctionnalité. Enfin, <xref:System.Windows.Controls.Grid> un est plus <xref:System.Windows.Documents.Table>léger poids que d’un .  
  
#### <a name="sizing-behavior-of-columns-and-rows"></a>Comportement de dimensionnement des colonnes et des lignes  
 Les colonnes et <xref:System.Windows.Controls.Grid> les lignes <xref:System.Windows.GridUnitType.Star> définies dans un peut profiter du dimensionnement afin de répartir l’espace restant proportionnellement. Lorsqu’elle <xref:System.Windows.GridUnitType.Star> est sélectionnée comme hauteur ou largeur d’une rangée ou d’une colonne, cette colonne ou cette ligne reçoit une proportion pondérée de l’espace disponible restant. Ceci est en <xref:System.Windows.GridUnitType.Auto>contraste avec , qui distribuera l’espace uniformément en fonction de la taille du contenu dans une colonne ou une rangée. Cette valeur est exprimée en tant que `*` ou `2*` lorsque [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] est utilisé. Dans le premier cas, la ligne ou la colonne reçoit une fois l’espace disponible, dans le deuxième cas, deux fois, et ainsi de suite. En combinant cette technique pour distribuer <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> proportionnellement `Stretch` l’espace avec un et la valeur de celui-ci est possible de partitionner l’espace de mise en page par pourcentage de l’espace d’écran. <xref:System.Windows.Controls.Grid>est le seul panneau de mise en page qui peut distribuer de l’espace de cette manière.  
  
#### <a name="defining-and-using-a-grid"></a>Définition et utilisation d’un élément Grid  
 L’exemple suivant montre comment [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] construire un semblable à celui trouvé sur le dialogue Run disponible sur le menu Windows Start.  
  
 [!code-csharp[GridRunDialog#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GridRunDialog/CSharp/window1.xaml.cs#1)]
 [!code-vb[GridRunDialog#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GridRunDialog/VisualBasic/grid_vb.vb#1)]  
  
 L’application compilée produit une nouvelle IU qui ressemble à ceci :  
  
 ![Élément de grille classique.](./media/avalon-run-dialog.PNG "avalon_run_dialog")  
  
<a name="Panels_overview_StackPanel_subsection"></a>
### <a name="stackpanel"></a>StackPanel  
 A <xref:System.Windows.Controls.StackPanel> vous permet de " empiler " les éléments dans une direction assignée. Le sens d’empilement par défaut est vertical. La <xref:System.Windows.Controls.StackPanel.Orientation%2A> propriété peut être utilisée pour contrôler le flux de contenu.  
  
#### <a name="stackpanel-vs-dockpanel"></a>StackPanel vs DockPanel  
 Bien <xref:System.Windows.Controls.DockPanel> que peut également "empiler" les éléments de l’enfant, <xref:System.Windows.Controls.DockPanel> et <xref:System.Windows.Controls.StackPanel> ne produisent pas de résultats analogues dans certains scénarios d’utilisation. Par exemple, l’ordre des éléments pour <xref:System.Windows.Controls.DockPanel> enfants peut <xref:System.Windows.Controls.StackPanel>affecter leur taille dans un, mais pas dans un . C’est <xref:System.Windows.Controls.StackPanel> parce que les mesures <xref:System.Double.PositiveInfinity>dans <xref:System.Windows.Controls.DockPanel> le sens de l’empilage à , alors que ne mesure que la taille disponible.  
  
 L’exemple suivant illustre cette différence clé.  
  
 [!code-cpp[StackPanelOvw4#1](~/samples/snippets/cpp/VS_Snippets_Wpf/StackPanelOvw4/CPP/StackPanel_Ovw_Sample4.cpp#1)]
 [!code-csharp[StackPanelOvw4#1](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanelOvw4/CSharp/StackPanel_Ovw_Sample4.cs#1)]
 [!code-vb[StackPanelOvw4#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelOvw4/VisualBasic/StackPanelSamp.vb#1)]
 [!code-xaml[StackPanelOvw4#1](~/samples/snippets/xaml/VS_Snippets_Wpf/StackPanelOvw4/XAML/default.xaml#1)]  
  
 La différence de comportement du rendu peut être observée dans cette image.  
  
 ![Capture d'écran : StackPanel et DockPanel](./media/layout-smiley-stackpanel.PNG "layout_smiley_stackpanel")  
  
#### <a name="defining-and-using-a-stackpanel"></a>Définition et utilisation d’un élément StackPanel  
 L’exemple suivant montre comment <xref:System.Windows.Controls.StackPanel> utiliser un pour créer un ensemble de boutons positionnés verticalement. Pour le positionnement horizontal, définissez la <xref:System.Windows.Controls.StackPanel.Orientation%2A> propriété à <xref:System.Windows.Controls.Orientation.Horizontal>.  
  
 [!code-csharp[StackPanel_ovw2#1](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanel_ovw2/CSharp/StackPanel_Ovw_Sample2.cs#1)]
 [!code-vb[StackPanel_ovw2#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanel_ovw2/VisualBasic/StackPanelOvw.vb#1)]  
  
 L’application compilée produit une nouvelle IU qui ressemble à ceci :  
  
 ![Élément StackPanel classique.](./media/panel-intro-stackpanel.PNG "panel_intro_stackpanel")  
  
<a name="Panels_overview_VirtualizingStackPanel_subsection"></a>
#### <a name="virtualizingstackpanel"></a>Élément VirtualizingStackPanel  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]fournit également une <xref:System.Windows.Controls.StackPanel> variante de l’élément qui « virtualise » automatiquement le contenu de l’enfant lié aux données. Dans ce contexte, le mot virtualiser fait référence à une technique par laquelle un sous-ensemble d’éléments est généré à partir d’un plus grand nombre d’éléments de données en fonction des éléments visibles à l’écran. La génération d’un grand nombre d'éléments d'interface utilisateur, alors que seul un certain nombre de ces éléments peut figurer à l'écran à un moment donné, entraîne une utilisation intensive de la mémoire et du processeur. <xref:System.Windows.Controls.VirtualizingStackPanel>(grâce à la <xref:System.Windows.Controls.VirtualizingPanel>fonctionnalité fournie par ) <xref:System.Windows.Controls.ItemContainerGenerator> calcule <xref:System.Windows.Controls.ItemsControl> les <xref:System.Windows.Controls.ListBox> éléments <xref:System.Windows.Controls.ListView>visibles et fonctionne avec le d’un (tel ou ) pour créer seulement des éléments pour les éléments visibles.  
  
 L’élément <xref:System.Windows.Controls.VirtualizingStackPanel> est automatiquement défini comme les <xref:System.Windows.Controls.ListBox>éléments hébergent pour les contrôles tels que le . Lors de l’hébergement d’une collecte de données liée, le contenu <xref:System.Windows.Controls.ScrollViewer>est automatiquement virtualisé, tant que le contenu est dans les limites d’un . Cela améliore considérablement les performances lorsque de nombreux éléments enfants sont hébergés.  
  
 La balisage suivante montre <xref:System.Windows.Controls.VirtualizingStackPanel> comment utiliser un hôte d’articles. La <xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizingProperty?displayProperty=nameWithType> propriété ci-jointe `true` doit être définie (par défaut) pour que la virtualisation se produise.  
  
 [!code-xaml[VirtualizingStackPanel_Intro#1](~/samples/snippets/csharp/VS_Snippets_Wpf/VirtualizingStackPanel_Intro/CS/default.xaml#1)]  
  
<a name="Panels_overview_WrapPanel"></a>
### <a name="wrappanel"></a>WrapPanel  
 <xref:System.Windows.Controls.WrapPanel>est utilisé pour positionner les éléments de l’enfant en position séquentielle de gauche à droite, brisant le contenu à la ligne suivante lorsqu’il atteint le bord de son contenant parent. Le contenu peut être orienté horizontalement ou verticalement. <xref:System.Windows.Controls.WrapPanel>est utile pour [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] des scénarios fluides simples. Il peut également être utilisé pour appliquer un dimensionnement uniforme à tous ses éléments enfants.  
  
 L’exemple suivant montre comment <xref:System.Windows.Controls.WrapPanel> créer <xref:System.Windows.Controls.Button> un contrôle d’affichage qui s’enroule lorsqu’ils atteignent le bord de leur conteneur.  
  
 [!code-cpp[WrapPanel_Intro#1](~/samples/snippets/cpp/VS_Snippets_Wpf/WrapPanel_Intro/CPP/WrapPanel_Code.cpp#1)]
 [!code-csharp[WrapPanel_Intro#1](~/samples/snippets/csharp/VS_Snippets_Wpf/WrapPanel_Intro/CSharp/WrapPanel_Code.cs#1)]
 [!code-vb[WrapPanel_Intro#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WrapPanel_Intro/VisualBasic/WrapPanel_vb.vb#1)]
 [!code-xaml[WrapPanel_Intro#1](~/samples/snippets/xaml/VS_Snippets_Wpf/WrapPanel_Intro/XAML/default.xaml#1)]  
  
 L’application compilée produit une nouvelle IU qui ressemble à ceci :  
  
 ![Élément WrapPanel classique.](./media/wrappanel-element.PNG "WrapPanel_Element")  
  
<a name="Panels_nested_panel_elements"></a>
## <a name="nested-panel-elements"></a>Éléments Panel imbriqués  
 <xref:System.Windows.Controls.Panel>les éléments peuvent être imbriqués les uns dans les autres afin de produire des dispositions complexes. Cela peut s’avérer très <xref:System.Windows.Controls.Panel> utile dans les [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]situations où l’on est idéal [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]pour une partie d’un , mais peut ne pas répondre aux besoins d’une partie différente de la .  
  
 Il n’existe aucune limite concernant le nombre d’imbrications que votre application peut prendre en charge. Toutefois, il est généralement préférable de limiter ces éléments Panel à ceux qui sont réellement nécessaires pour la disposition souhaitée. Dans de nombreux <xref:System.Windows.Controls.Grid> cas, un élément peut être utilisé au lieu de panneaux imbriqués en raison de sa flexibilité comme un récipient de mise en page. Cela peut accroître les performances au sein de votre application en laissant les éléments inutiles en dehors de l’arborescence.  
  
 L’exemple suivant montre comment [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] créer un qui <xref:System.Windows.Controls.Panel> tire parti des éléments imbriqués afin d’obtenir une mise en page spécifique. Dans ce cas <xref:System.Windows.Controls.DockPanel> particulier, un [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] élément est utilisé <xref:System.Windows.Controls.StackPanel> pour <xref:System.Windows.Controls.Grid>fournir la <xref:System.Windows.Controls.Canvas> structure, et les éléments <xref:System.Windows.Controls.DockPanel>imbriqués, a, et un sont utilisés pour positionner les éléments de l’enfant précisément au sein du parent .  
  
 [!code-csharp[Nested_Panels#1](~/samples/snippets/csharp/VS_Snippets_Wpf/Nested_Panels/CSharp/nestedpanels.cs#1)]
 [!code-vb[Nested_Panels#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Nested_Panels/VisualBasic/nestedpanels.vb#1)]  
  
 L’application compilée produit une nouvelle IU qui ressemble à ceci :  
  
 ![Interface utilisateur bénéficiant de volets imbriqués.](./media/nested-panels.PNG "nested_panels")  
  
<a name="Panels_custom_panel_elements"></a>
## <a name="custom-panel-elements"></a>Éléments Panel personnalisés  
 Bien [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] qu’il fournisse un éventail de contrôles de mise en <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> <xref:System.Windows.FrameworkElement.MeasureOverride%2A> page flexibles, des comportements de mise en page personnalisés peuvent également être atteints en l’emportent sur les méthodes et les méthodes. Un dimensionnement et un positionnement personnalisés peuvent être obtenus en définissant de nouveaux comportements de positionnement au sein de ces méthodes de remplacement.  
  
 De même, les comportements de mise <xref:System.Windows.Controls.Canvas> en <xref:System.Windows.Controls.Grid>page personnalisés basés sur <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> <xref:System.Windows.FrameworkElement.MeasureOverride%2A> des classes dérivées (comme ou ) peuvent être définis en l’avant de leurs méthodes et méthodes.  
  
 La balisage suivante montre comment <xref:System.Windows.Controls.Panel> créer un élément personnalisé. Ce <xref:System.Windows.Controls.Panel>nouveau , `PlotPanel`défini comme , soutient le positionnement des éléments de l’enfant par l’utilisation de *coordonnées x* et *y* codées en dur. Dans cet exemple, un <xref:System.Windows.Shapes.Rectangle> élément (non montré) est positionné au point de l’intrigue 50 (*x*), et 50 *(y*).  
  
 [!code-cpp[PlotPanel#1](~/samples/snippets/cpp/VS_Snippets_Wpf/PlotPanel/CPP/PlotPanel.cpp#1)]
 [!code-csharp[PlotPanel#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PlotPanel/CSharp/PlotPanel.cs#1)]
 [!code-vb[PlotPanel#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PlotPanel/VisualBasic/PlotPanel.vb#1)]  
  
 Pour voir une implémentation d’élément Panel personnalisé plus complexe, consultez [Créer un exemple de panneau d’agencement de contenu personnalisé](https://go.microsoft.com/fwlink/?LinkID=159979).  
  
<a name="Panels_global_localization"></a>
## <a name="localizationglobalization-support"></a>Prise en charge de la localisation/globalisation  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] prend en charge un certain nombre de fonctionnalités qui facilitent la création d’IU [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] localisables.  
  
 Tous les éléments du <xref:System.Windows.FrameworkElement.FlowDirection%2A> panneau prennent en charge la propriété, qui peut être utilisée pour réappavrer dynamiquement le contenu en fonction des paramètres locaux ou linguistiques d’un utilisateur. Pour plus d’informations, consultez <xref:System.Windows.FrameworkElement.FlowDirection%2A>.  
  
 La <xref:System.Windows.Window.SizeToContent%2A> propriété fournit un mécanisme qui permet aux [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]développeurs d’applications d’anticiper les besoins de localisés . En <xref:System.Windows.SizeToContent.WidthAndHeight> utilisant la valeur de <xref:System.Windows.Window> cette propriété, un parent taille toujours dynamiquement pour s’adapter au contenu et n’est pas limité par des restrictions artificielles de hauteur ou de largeur.  
  
 <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Grid>, <xref:System.Windows.Controls.StackPanel> et sont tous de [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]bons choix pour localizable . <xref:System.Windows.Controls.Canvas>n’est pas un bon choix, cependant, parce qu’il positionne le contenu absolument, ce qui rend difficile de localiser.  
  
 Pour plus d’informations sur la création [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] d’applications avec des interfaces utilisateur localisables (UIs), consultez [l’aperçu de la mise en page automatique d’utilisation](../advanced/use-automatic-layout-overview.md).  
  
## <a name="see-also"></a>Voir aussi

- [Procédure pas à pas : ma première application de bureau WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md)
- [Galerie de dispositions WPF, exemple](https://go.microsoft.com/fwlink/?LinkID=160054)
- [Disposition](../advanced/layout.md)
- [Exemple de galerie de contrôles WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/ControlsAndLayout)
- [Vue d'ensemble de l'alignement, des marges et du remplissage](../advanced/alignment-margins-and-padding-overview.md)
- [Créer un exemple de panneau d’agencement de contenu personnalisé](https://go.microsoft.com/fwlink/?LinkID=159979)
- [Vue d'ensemble des propriétés jointes](../advanced/attached-properties-overview.md)
- [Vue d'ensemble de l'utilisation de la disposition automatique](../advanced/use-automatic-layout-overview.md)
- [Disposition et conception](../advanced/optimizing-performance-layout-and-design.md)
