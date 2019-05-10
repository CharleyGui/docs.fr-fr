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
ms.openlocfilehash: 9bd2af8cd74c32bcda3a6105f39af470f961289d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64625725"
---
# <a name="panels-overview"></a>Vue d'ensemble de Panel
<xref:System.Windows.Controls.Panel> les éléments sont des composants qui contrôlent le rendu des éléments : leur taille et dimensions, leur position et la disposition de leur contenu enfant. Le [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fournit un certain nombre de prédéfinis <xref:System.Windows.Controls.Panel> éléments, ainsi que la possibilité de construire personnalisé <xref:System.Windows.Controls.Panel> éléments.  
  
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
 <xref:System.Windows.Controls.Panel> est la classe de base pour tous les éléments qui fournissent une disposition prise en charge dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Dérivés <xref:System.Windows.Controls.Panel> éléments sont utilisés pour positionner et organiser les éléments dans [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] et le code.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] comprend une suite complète d’implémentations Panel dérivées qui permettent la mise en œuvre de nombreuses dispositions complexes. Ces classes dérivées exposent des propriétés et des méthodes qui rendent possibles la plupart des scénarios [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] standard. Les développeurs qui ne peuvent pas trouver le comportement de disposition enfant répondant à leurs besoins permettre créer de nouvelles dispositions en remplaçant le <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> et <xref:System.Windows.FrameworkElement.MeasureOverride%2A> méthodes. Pour plus d’informations sur les comportements de disposition personnalisés, consultez [Éléments Panel personnalisés](#Panels_custom_panel_elements).  
  
<a name="Panels_declared_members"></a>   
## <a name="panel-common-members"></a>Membres communs aux éléments Panel  
 Tous les <xref:System.Windows.Controls.Panel> éléments prennent en charge de la base de dimensionnement et de propriétés de positionnement définies par <xref:System.Windows.FrameworkElement>, y compris <xref:System.Windows.FrameworkElement.Height%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>, <xref:System.Windows.FrameworkElement.Margin%2A>, et <xref:System.Windows.FrameworkElement.LayoutTransform%2A>. Pour plus d’informations sur les propriétés de positionnement définies par <xref:System.Windows.FrameworkElement>, consultez [l’alignement, marges et remplissage de vue d’ensemble](../advanced/alignment-margins-and-padding-overview.md).  
  
 <xref:System.Windows.Controls.Panel> expose des propriétés supplémentaires qui sont très important de comprendre et à l’aide de la mise en page. Le <xref:System.Windows.Controls.Panel.Background%2A> propriété est utilisée pour remplir la zone entre les limites d’un élément panel dérivé avec un <xref:System.Windows.Media.Brush>. <xref:System.Windows.Controls.Panel.Children%2A> représente la collection enfant d’éléments qui le <xref:System.Windows.Controls.Panel> se compose de. <xref:System.Windows.Controls.Panel.InternalChildren%2A> représente le contenu de la <xref:System.Windows.Controls.Panel.Children%2A> collection ainsi que les membres générés par la liaison de données. Ces contrôles se composent d’un <xref:System.Windows.Controls.UIElementCollection> d’éléments enfants hébergés dans le parent <xref:System.Windows.Controls.Panel>.  
  
 Le Panel expose également une <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType> propriété qui peut être utilisée pour effectuer un ordre superposé dans une dérivée jointe <xref:System.Windows.Controls.Panel>. Les membres d’un panneau <xref:System.Windows.Controls.Panel.Children%2A> collection avec un degré plus élevé <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType> valeur apparaissent devant ceux avec une priorité plus faible <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType> valeur. Cela est particulièrement utile pour les panneaux comme <xref:System.Windows.Controls.Canvas> et <xref:System.Windows.Controls.Grid> qui permettent aux enfants de partager le même espace de coordonnées.  
  
 <xref:System.Windows.Controls.Panel> définit également le <xref:System.Windows.Controls.Panel.OnRender%2A> (méthode), qui peut être utilisé pour remplacer le comportement de présentation par défaut d’un <xref:System.Windows.Controls.Panel>.  
  
#### <a name="attached-properties"></a>Propriétés jointes  
 Les éléments Panel dérivés utilisent beaucoup les propriétés jointes. Une propriété jointe constitue une forme spécialisée de la propriété de dépendance qui n’a pas le « wrapper » de propriété [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] classique. Les propriétés jointes présentent une syntaxe spécialisée dans [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], visible dans plusieurs des exemples qui suivent.  
  
 Une des finalités d’une propriété jointe est de permettre aux éléments enfants de stocker les valeurs uniques d’une propriété définie en fait par un élément parent. Une application de cette fonctionnalité est de faire en sorte que les éléments enfants informent le parent sur la manière dont ils doivent être présentés dans l’interface utilisateur (IU) [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)], ce qui est extrêmement utile pour la disposition de l’application. Pour plus d’informations, consultez [Vue d’ensemble des propriétés jointes](../advanced/attached-properties-overview.md).  
  
<a name="Panels_derived_elements"></a>   
## <a name="derived-panel-elements"></a>Éléments Panel dérivés  
 De nombreux objets dérivent <xref:System.Windows.Controls.Panel>, mais pas toutes sont destinées à utiliser en tant que fournisseurs de disposition racine. Il existe six classes panel définies (<xref:System.Windows.Controls.Canvas>, <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Grid>, <xref:System.Windows.Controls.StackPanel>, <xref:System.Windows.Controls.VirtualizingStackPanel>, et <xref:System.Windows.Controls.WrapPanel>) qui sont conçues spécifiquement pour la création d’application [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
 Chaque élément Panel encapsule sa propre fonctionnalité spéciale, comme indiqué dans le tableau suivant.  
  
|Nom de l'élément|Élément Panel d’IU ?|Description|  
|------------------|---------------|-----------------|  
|<xref:System.Windows.Controls.Canvas>|Oui|Définit une zone dans laquelle vous pouvez positionner explicitement des éléments enfants par les coordonnées sont relatives à la <xref:System.Windows.Controls.Canvas> zone.|  
|<xref:System.Windows.Controls.DockPanel>|Oui|Définit une zone dans laquelle vous pouvez organiser des éléments enfants horizontalement ou verticalement, les uns par rapport aux autres.|  
|<xref:System.Windows.Controls.Grid>|Oui|Définit une zone de grille flexible composée de colonnes et de lignes. Éléments enfants d’un <xref:System.Windows.Controls.Grid> peuvent être positionnés avec précision à l’aide de la <xref:System.Windows.FrameworkElement.Margin%2A> propriété.|  
|<xref:System.Windows.Controls.StackPanel>|Oui|Dispose des éléments enfants sur une seule ligne orientée horizontalement ou verticalement.|  
|<xref:System.Windows.Controls.Primitives.TabPanel>|Non|Gère la disposition des boutons d’onglet dans un <xref:System.Windows.Controls.TabControl>.|  
|<xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>|Non|Réorganise le contenu dans un <xref:System.Windows.Controls.ToolBar> contrôle.|  
|<xref:System.Windows.Controls.Primitives.UniformGrid>|Non|<xref:System.Windows.Controls.Primitives.UniformGrid> est utilisé pour organiser les enfants dans une grille avec toutes les tailles de cellule égales.|  
|<xref:System.Windows.Controls.VirtualizingPanel>|Non|Fournit une classe de base pour les éléments Panel qui peuvent « virtualiser » leur collection d’enfants.|  
|<xref:System.Windows.Controls.VirtualizingStackPanel>|Oui|Organise et virtualise un contenu sur une seule ligne orientée horizontalement ou verticalement.|  
|<xref:System.Windows.Controls.WrapPanel>|Oui|<xref:System.Windows.Controls.WrapPanel> Positionne des éléments enfants dans un ordre séquentiel de gauche à droite, en faisant passer le contenu à la ligne suivante à la périphérie de la zone conteneur. Classement continue ensuite séquentiellement de haut en bas ou de droite à gauche, selon la valeur de la <xref:System.Windows.Controls.WrapPanel.Orientation%2A> propriété.|  
  
<a name="Panels_main_UI_elements"></a>   
## <a name="user-interface-panels"></a>Éléments Panel d’interface utilisateur  
 Il existe six classes panel dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] qui sont optimisés pour prendre en charge [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] scénarios : <xref:System.Windows.Controls.Canvas>, <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Grid>, <xref:System.Windows.Controls.StackPanel>, <xref:System.Windows.Controls.VirtualizingStackPanel>, et <xref:System.Windows.Controls.WrapPanel>. Ces éléments Panel sont simples d’utilisation, polyvalents et suffisamment extensibles pour la plupart des applications.  
  
 Chaque dérivée <xref:System.Windows.Controls.Panel> élément traite différemment les contraintes de dimensionnement. Comprendre comment un <xref:System.Windows.Controls.Panel> gère les contraintes dans le sens horizontal ou vertical peuvent rendre la disposition plus prévisible.  
  
|**Nom de l’élément Panel**|**Dimension x**|**Dimension y**|  
|--------------------|----------------------|----------------------|  
|<xref:System.Windows.Controls.Canvas>|Restreinte au contenu|Restreinte au contenu|  
|<xref:System.Windows.Controls.DockPanel>|Restreinte|Restreinte|  
|<xref:System.Windows.Controls.StackPanel> (Orientation verticale)|Restreinte|Restreinte au contenu|  
|<xref:System.Windows.Controls.StackPanel> (Orientation horizontale)|Restreinte au contenu|Restreinte|  
|<xref:System.Windows.Controls.Grid>|Restreinte|Limité, sauf dans les cas où <xref:System.Windows.GridUnitType.Auto> s’appliquent aux lignes et colonnes|  
|<xref:System.Windows.Controls.WrapPanel>|Restreinte au contenu|Restreinte au contenu|  
  
 Vous trouverez des descriptions plus détaillées et des exemples d’utilisation de chacun de ces éléments ci-dessous.  
  
<a name="Panels_overview_Canvas_subsection"></a>   
### <a name="canvas"></a>Canvas  
 Le <xref:System.Windows.Controls.Canvas> élément permet de positionner du contenu selon *x -* et *y*coordonnées. Les éléments peuvent être dessinés dans un emplacement unique, ou s’ils occupent les mêmes coordonnées, l’ordre dans lequel ils apparaissent dans le balisage détermine l’ordre dans lequel ils sont dessinés.  
  
 <xref:System.Windows.Controls.Canvas> Fournit la prise en charge de mise en page plus souple de n’importe quel <xref:System.Windows.Controls.Panel>. Propriétés de hauteur et la largeur sont utilisées pour définir la zone de dessin, et des coordonnées absolues relatives à la zone du parent sont affectées aux éléments à l’intérieur de <xref:System.Windows.Controls.Canvas>. Quatre propriétés jointes, <xref:System.Windows.Controls.Canvas.Left%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.Canvas.Top%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.Canvas.Right%2A?displayProperty=nameWithType> et <xref:System.Windows.Controls.Canvas.Bottom%2A?displayProperty=nameWithType>, assurent un contrôle précis du placement des objets au sein d’un <xref:System.Windows.Controls.Canvas>, ce qui permet au développeur de positionner et organiser les éléments avec précision sur l’écran.  
  
#### <a name="cliptobounds-within-a-canvas"></a>Propriété ClipToBounds à l’intérieur d’un élément Canvas  
 <xref:System.Windows.Controls.Canvas> positionner des éléments enfants à n’importe quelle position dans l’écran, même à des coordonnées qui sont en dehors de son propre défini <xref:System.Windows.FrameworkElement.Height%2A> et <xref:System.Windows.FrameworkElement.Width%2A>. En outre, <xref:System.Windows.Controls.Canvas> n’est pas affectée par la taille de ses enfants. Par conséquent, il est possible pour un élément enfant de superposer d’autres éléments en dehors du rectangle englobant du parent <xref:System.Windows.Controls.Canvas>. Le comportement par défaut d’un <xref:System.Windows.Controls.Canvas> consiste à autoriser les enfants d’être dessinés en dehors des limites du parent <xref:System.Windows.Controls.Canvas>. Si ce comportement est indésirable, le <xref:System.Windows.UIElement.ClipToBounds%2A> propriété peut être définie sur `true`. Cela entraîne <xref:System.Windows.Controls.Canvas> à découper à sa taille. <xref:System.Windows.Controls.Canvas> est le seul élément de disposition qui permet aux enfants d’être dessinés en dehors de ses limites.  
  
 Ce comportement est illustré en images dans l’[exemple de comparaison des propriétés Width](https://go.microsoft.com/fwlink/?LinkID=160050).  
  
#### <a name="defining-and-using-a-canvas"></a>Définition et utilisation d’un élément Canvas  
 Un <xref:System.Windows.Controls.Canvas> peut être instancié en utilisant simplement [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ou du code. L’exemple suivant montre comment utiliser <xref:System.Windows.Controls.Canvas> pour positionner le contenu absolument. Ce code génère trois carrés de 100 pixels de côté. Le premier carré est rouge, et la position de son angle supérieur gauche (*x, y*) est définie sur (0, 0). Le deuxième carré est vert, et la position de son angle supérieur gauche est définie sur (100, 100), juste en dessous et à droite du premier carré. Le troisième carré est bleu, et la position de son angle supérieur gauche est définie sur (50, 50). Il englobe ainsi le quart inférieur droit du premier carré et le quart supérieur gauche du deuxième. Comme le troisième carré est disposé en dernier, il apparaît au-dessus des deux autres carrés, c’est-à-dire que les parties qui se chevauchent prennent la couleur de ce troisième carré.  
  
 [!code-csharp[CanvasOvwSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CanvasOvwSample/CSharp/Canvas_Ovw_Sample.cs#1)]
 [!code-vb[CanvasOvwSample#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasOvwSample/VisualBasic/canvas_vb.vb#1)]
 [!code-xaml[CanvasOvwSample#1](~/samples/snippets/xaml/VS_Snippets_Wpf/CanvasOvwSample/XAML/default.xaml#1)]  
  
 L’application compilée produit une nouvelle [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]IU qui ressemble à ceci.  
  
 ![Élément Canvas classique.](./media/panel-intro-canvas.PNG "panel_intro_canvas")  
  
<a name="Panels_overview_DockPanel_subsection"></a>   
### <a name="dockpanel"></a>DockPanel  
 Le <xref:System.Windows.Controls.DockPanel> élément utilise le <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> propriété jointe en tant que jeu dans les éléments de contenu enfants pour positionner le contenu le long des bords d’un conteneur. Lorsque <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> a la valeur <xref:System.Windows.Controls.Dock.Top> ou <xref:System.Windows.Controls.Dock.Bottom>, il positionne les éléments enfants au-dessus ou au-dessous de l’autre. Lorsque <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> a la valeur <xref:System.Windows.Controls.Dock.Left> ou <xref:System.Windows.Controls.Dock.Right>, il positionne les éléments enfants à gauche ou à droite de l’autre. Le <xref:System.Windows.Controls.DockPanel.LastChildFill%2A> propriété détermine la position du dernier élément ajouté en tant qu’enfant d’un <xref:System.Windows.Controls.DockPanel>.  
  
 Vous pouvez utiliser <xref:System.Windows.Controls.DockPanel> pour positionner un groupe de contrôles connexes, tel qu’un ensemble de boutons. Vous pouvez également l’utiliser pour créer une IU « à volets » [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] similaire à celle de [!INCLUDE[TLA#tla_outlook](../../../../includes/tlasharptla-outlook-md.md)].  
  
#### <a name="sizing-to-content"></a>Dimensionnement en fonction du contenu  
 Si son <xref:System.Windows.FrameworkElement.Height%2A> et <xref:System.Windows.FrameworkElement.Width%2A> propriétés ne sont pas spécifiées, <xref:System.Windows.Controls.DockPanel> tailles à son contenu. La taille peut augmenter ou diminuer pour s’adapter à la taille de ses éléments enfants. Toutefois, lorsque ces propriétés sont spécifiées et qu’il n’est plus local pour l’élément enfant spécifié suivant, <xref:System.Windows.Controls.DockPanel> n’affiche pas cet élément enfant ou les éléments enfants suivants et ne mesure pas les éléments enfants suivants.  
  
#### <a name="lastchildfill"></a>Propriété LastChildFill  
 Par défaut, le dernier enfant d’un <xref:System.Windows.Controls.DockPanel> élément « remplit » le restante, l’espace non alloué. Si ce comportement n’est pas souhaité, définissez la <xref:System.Windows.Controls.DockPanel.LastChildFill%2A> propriété `false`.  
  
#### <a name="defining-and-using-a-dockpanel"></a>Définition et utilisation d’un élément DockPanel  
 L’exemple suivant montre comment partitionner l’espace à l’aide un <xref:System.Windows.Controls.DockPanel>. Cinq <xref:System.Windows.Controls.Border> éléments sont ajoutés en tant qu’enfants d’un parent <xref:System.Windows.Controls.DockPanel>. Chacun utilise une autre propriété de positionnement d’un <xref:System.Windows.Controls.DockPanel> pour partitionner l’espace. Le dernier élément « remplit » l’espace non alloué restant.  
  
 [!code-cpp[DockPanelOvwSample#1](~/samples/snippets/cpp/VS_Snippets_Wpf/DockPanelOvwSample/CPP/DockPanel_Ovw_Sample.cpp#1)]
 [!code-csharp[DockPanelOvwSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/DockPanelOvwSample/CSharp/DockPanel_Ovw_Sample.cs#1)]
 [!code-vb[DockPanelOvwSample#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelOvwSample/VisualBasic/dockpanel_vb.vb#1)]
 [!code-xaml[DockPanelOvwSample#1](~/samples/snippets/xaml/VS_Snippets_Wpf/DockPanelOvwSample/XAML/default.xaml#1)]  
  
 L’application compilée produit une nouvelle [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]IU qui ressemble à ceci.  
  
 ![Scénario classique d’utilisation de l’élément DockPanel.](./media/panel-intro-dockpanel.PNG "panel_intro_dockpanel")  
  
<a name="Panels_overview_Grid_subsection"></a>   
### <a name="grid"></a>Grille  
 Le <xref:System.Windows.Controls.Grid> élément réunit les fonctionnalités d’un positionnement absolu et le contrôle de données tabulaires. Un <xref:System.Windows.Controls.Grid> vous permet de facilement position des éléments de style. <xref:System.Windows.Controls.Grid> vous permet de définir des regroupements de colonnes et de lignes flexibles et fournit même un mécanisme pour partager des informations de dimensionnement entre plusieurs <xref:System.Windows.Controls.Grid> éléments.  
  
#### <a name="how-is-grid-different-from-table"></a>En quoi un élément Grid diffère-t-il d’un élément Table ?  
 <xref:System.Windows.Documents.Table> et <xref:System.Windows.Controls.Grid> partagent des fonctionnalités communes, mais chacun est idéale pour différents scénarios. Un <xref:System.Windows.Documents.Table> est conçu pour être utilisé dans du contenu dynamique (voir [vue d’ensemble du Document de flux](../advanced/flow-document-overview.md) pour plus d’informations sur le contenu dynamique). Les éléments Grid sont mieux adaptés à une utilisation dans des formulaires (autrement dit, partout, sauf dans du contenu dynamique). Au sein d’un <xref:System.Windows.Documents.FlowDocument>, <xref:System.Windows.Documents.Table> les comportements de contenu tels que la pagination, Redisposition et lors de la sélection de contenu de flux prend en charge un <xref:System.Windows.Controls.Grid> pas. Un <xref:System.Windows.Controls.Grid> quant à eux, est mieux utilisées en dehors d’un <xref:System.Windows.Documents.FlowDocument> pour de nombreuses raisons, y compris <xref:System.Windows.Controls.Grid> ajoute des éléments basés sur un index de ligne et de colonne, <xref:System.Windows.Documents.Table> pas. Le <xref:System.Windows.Controls.Grid> élément autorise la superposition de contenu enfant, et plusieurs éléments d’exister dans une même « cellule ». <xref:System.Windows.Documents.Table> ne prend pas en charge la superposition. Éléments enfants d’un <xref:System.Windows.Controls.Grid> peuvent être positionnés par rapport à la zone de leurs limites de « cellule ». <xref:System.Windows.Documents.Table> ne prend pas en charge cette fonctionnalité. Enfin, un <xref:System.Windows.Controls.Grid> est plus légère qu’une <xref:System.Windows.Documents.Table>.  
  
#### <a name="sizing-behavior-of-columns-and-rows"></a>Comportement de dimensionnement des colonnes et des lignes  
 Colonnes et lignes définies dans un <xref:System.Windows.Controls.Grid> peuvent tirer parti de <xref:System.Windows.GridUnitType.Star> dimensionnement pour distribuer proportionnellement l’espace restant. Lorsque <xref:System.Windows.GridUnitType.Star> est sélectionné en tant que la hauteur ou la largeur d’une ligne ou une colonne, que la colonne ou ligne reçoit une proportion pondérée d’espace disponible restant. Il s’agit Contrairement à <xref:System.Windows.GridUnitType.Auto>, qui répartit l’espace uniformément en fonction de la taille du contenu au sein d’une colonne ou ligne. Cette valeur est exprimée en tant que `*` ou `2*` lorsque [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] est utilisé. Dans le premier cas, la ligne ou la colonne reçoit une fois l’espace disponible, dans le deuxième cas, deux fois, et ainsi de suite. En associant cette technique pour répartir proportionnellement l’espace avec une <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> et <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> valeur `Stretch` il est possible de l’espace de disposition de partition par pourcentage d’espace à l’écran. <xref:System.Windows.Controls.Grid> est le seul panneau de disposition qui peut distribuer l’espace de cette manière.  
  
#### <a name="defining-and-using-a-grid"></a>Définition et utilisation d’un élément Grid  
 L’exemple suivant montre comment créer une IU [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] similaire à celle de la boîte de dialogue Exécuter disponible dans le menu Démarrer de [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)].  
  
 [!code-csharp[GridRunDialog#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GridRunDialog/CSharp/window1.xaml.cs#1)]
 [!code-vb[GridRunDialog#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GridRunDialog/VisualBasic/grid_vb.vb#1)]  
  
 L’application compilée produit une nouvelle [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]IU qui ressemble à ceci.  
  
 ![Élément Grid classique.](./media/avalon-run-dialog.PNG "avalon_run_dialog")  
  
<a name="Panels_overview_StackPanel_subsection"></a>   
### <a name="stackpanel"></a>StackPanel  
 Un <xref:System.Windows.Controls.StackPanel> vous permet de « empiler » des éléments dans un sens défini. Le sens d’empilement par défaut est vertical. Le <xref:System.Windows.Controls.StackPanel.Orientation%2A> propriété peut être utilisée pour contrôler le flux de contenu.  
  
#### <a name="stackpanel-vs-dockpanel"></a>Comparaison des éléments StackPanel et DockPanel  
 Bien que <xref:System.Windows.Controls.DockPanel> peut également « empiler » des éléments enfants, <xref:System.Windows.Controls.DockPanel> et <xref:System.Windows.Controls.StackPanel> ne produisent pas des résultats analogues dans certains scénarios d’utilisation. Par exemple, l’ordre des éléments enfants peut affecter leur taille dans un <xref:System.Windows.Controls.DockPanel> , mais pas dans un <xref:System.Windows.Controls.StackPanel>. Il s’agit, car <xref:System.Windows.Controls.StackPanel> mesures dans le sens de l’empilement en <xref:System.Double.PositiveInfinity>, tandis que <xref:System.Windows.Controls.DockPanel> mesure uniquement la taille disponible.  
  
 L’exemple suivant illustre cette différence clé.  
  
 [!code-cpp[StackPanelOvw4#1](~/samples/snippets/cpp/VS_Snippets_Wpf/StackPanelOvw4/CPP/StackPanel_Ovw_Sample4.cpp#1)]
 [!code-csharp[StackPanelOvw4#1](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanelOvw4/CSharp/StackPanel_Ovw_Sample4.cs#1)]
 [!code-vb[StackPanelOvw4#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelOvw4/VisualBasic/StackPanelSamp.vb#1)]
 [!code-xaml[StackPanelOvw4#1](~/samples/snippets/xaml/VS_Snippets_Wpf/StackPanelOvw4/XAML/default.xaml#1)]  
  
 La différence de comportement du rendu peut être observée dans cette image.  
  
 ![Capture d’écran : Comparaison des éléments StackPanel et DockPanel](./media/layout-smiley-stackpanel.PNG "layout_smiley_stackpanel")  
  
#### <a name="defining-and-using-a-stackpanel"></a>Définition et utilisation d’un élément StackPanel  
 L’exemple suivant montre comment utiliser un <xref:System.Windows.Controls.StackPanel> pour créer un ensemble de boutons positionnés verticalement. Pour un positionnement horizontal, définissez la <xref:System.Windows.Controls.StackPanel.Orientation%2A> propriété <xref:System.Windows.Controls.Orientation.Horizontal>.  
  
 [!code-csharp[StackPanel_ovw2#1](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanel_ovw2/CSharp/StackPanel_Ovw_Sample2.cs#1)]
 [!code-vb[StackPanel_ovw2#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanel_ovw2/VisualBasic/StackPanelOvw.vb#1)]  
  
 L’application compilée produit une nouvelle [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]IU qui ressemble à ceci.  
  
 ![Élément StackPanel standard.](./media/panel-intro-stackpanel.PNG "panel_intro_stackpanel")  
  
<a name="Panels_overview_VirtualizingStackPanel_subsection"></a>   
#### <a name="virtualizingstackpanel"></a>Élément VirtualizingStackPanel  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit également une variante de la <xref:System.Windows.Controls.StackPanel> élément qui « virtualise » automatiquement contenu enfant lié aux données. Dans ce contexte, le mot virtualiser fait référence à une technique par laquelle un sous-ensemble d’éléments est généré à partir d’un plus grand nombre d’éléments de données en fonction des éléments visibles à l’écran. La génération d’un grand nombre d’éléments d’interface utilisateur, alors que seul un certain nombre de ces éléments peut figurer à l’écran à un moment donné, entraîne une utilisation intensive de la mémoire et du processeur. <xref:System.Windows.Controls.VirtualizingStackPanel> (via la fonctionnalité fournie par <xref:System.Windows.Controls.VirtualizingPanel>) calcule les éléments visibles et utilise le <xref:System.Windows.Controls.ItemContainerGenerator> à partir d’un <xref:System.Windows.Controls.ItemsControl> (telles que <xref:System.Windows.Controls.ListBox> ou <xref:System.Windows.Controls.ListView>) pour créer uniquement des éléments pour les éléments visibles.  
  
 Le <xref:System.Windows.Controls.VirtualizingStackPanel> élément est automatiquement défini comme les éléments hôtes pour les contrôles tels que le <xref:System.Windows.Controls.ListBox>. Lors de l’hébergement une liée aux données collection, contenu est automatiquement virtualisé, tant que le contenu est dans les limites d’un <xref:System.Windows.Controls.ScrollViewer>. Cela améliore considérablement les performances lorsque de nombreux éléments enfants sont hébergés.  
  
 Le balisage suivant montre comment utiliser un <xref:System.Windows.Controls.VirtualizingStackPanel> comme un hôte d’éléments. Le <xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizingProperty?displayProperty=nameWithType> propriété jointe doit être définie sur `true` (valeur par défaut) pour la virtualisation ait lieu.  
  
 [!code-xaml[VirtualizingStackPanel_Intro#1](~/samples/snippets/csharp/VS_Snippets_Wpf/VirtualizingStackPanel_Intro/CS/default.xaml#1)]  
  
<a name="Panels_overview_WrapPanel"></a>   
### <a name="wrappanel"></a>WrapPanel  
 <xref:System.Windows.Controls.WrapPanel> est utilisé pour positionner des éléments enfants dans un ordre séquentiel de gauche à droite, en envoyant le contenu à la ligne suivante lorsqu’il atteint le bord de son conteneur parent. Le contenu peut être orienté horizontalement ou verticalement. <xref:System.Windows.Controls.WrapPanel> est utile pour le simple flux [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] scénarios. Il peut également être utilisé pour appliquer un dimensionnement uniforme à tous ses éléments enfants.  
  
 L’exemple suivant montre comment créer un <xref:System.Windows.Controls.WrapPanel> à afficher <xref:System.Windows.Controls.Button> contrôles qui encapsulent lorsqu’ils atteignent le bord de leur conteneur.  
  
 [!code-cpp[WrapPanel_Intro#1](~/samples/snippets/cpp/VS_Snippets_Wpf/WrapPanel_Intro/CPP/WrapPanel_Code.cpp#1)]
 [!code-csharp[WrapPanel_Intro#1](~/samples/snippets/csharp/VS_Snippets_Wpf/WrapPanel_Intro/CSharp/WrapPanel_Code.cs#1)]
 [!code-vb[WrapPanel_Intro#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WrapPanel_Intro/VisualBasic/WrapPanel_vb.vb#1)]
 [!code-xaml[WrapPanel_Intro#1](~/samples/snippets/xaml/VS_Snippets_Wpf/WrapPanel_Intro/XAML/default.xaml#1)]  
  
 L’application compilée produit une nouvelle [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]IU qui ressemble à ceci.  
  
 ![Élément WrapPanel standard.](./media/wrappanel-element.PNG "WrapPanel_Element")  
  
<a name="Panels_nested_panel_elements"></a>   
## <a name="nested-panel-elements"></a>Éléments Panel imbriqués  
 <xref:System.Windows.Controls.Panel> éléments peuvent être imbriqués dans d’autres afin de produire des dispositions complexes. Cela peut s’avérer très utile dans les situations où un <xref:System.Windows.Controls.Panel> est idéal pour une partie d’un [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], mais ne répond ne pas aux besoins d’une autre partie de la [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
 Il n’existe aucune limite concernant le nombre d’imbrications que votre application peut prendre en charge. Toutefois, il est généralement préférable de limiter ces éléments Panel à ceux qui sont réellement nécessaires pour la disposition souhaitée. Dans de nombreux cas, un <xref:System.Windows.Controls.Grid> élément peut être utilisé au lieu de panneaux imbriqués en raison de sa flexibilité qu’un conteneur de disposition. Cela peut accroître les performances au sein de votre application en laissant les éléments inutiles en dehors de l’arborescence.  
  
 L’exemple suivant montre comment créer un [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] que tire parti d’imbriqué <xref:System.Windows.Controls.Panel> éléments afin d’obtenir une disposition spécifique. Dans ce cas particulier, un <xref:System.Windows.Controls.DockPanel> élément est utilisé pour fournir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] structurer et imbriqués <xref:System.Windows.Controls.StackPanel> éléments, un <xref:System.Windows.Controls.Grid>et un <xref:System.Windows.Controls.Canvas> sont utilisés pour positionner des éléments enfants avec précision dans le parent <xref:System.Windows.Controls.DockPanel>.  
  
 [!code-csharp[Nested_Panels#1](~/samples/snippets/csharp/VS_Snippets_Wpf/Nested_Panels/CSharp/nestedpanels.cs#1)]
 [!code-vb[Nested_Panels#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Nested_Panels/VisualBasic/nestedpanels.vb#1)]  
  
 L’application compilée produit une nouvelle [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]IU qui ressemble à ceci.  
  
 ![IU tirant parti d’éléments Panel imbriqués.](./media/nested-panels.PNG "nested_panels")  
  
<a name="Panels_custom_panel_elements"></a>   
## <a name="custom-panel-elements"></a>Éléments Panel personnalisés  
 Bien que [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit un tableau de contrôles de disposition flexible, disposition personnalisée comportements peuvent également être obtenus en remplaçant le <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> et <xref:System.Windows.FrameworkElement.MeasureOverride%2A> méthodes. Un dimensionnement et un positionnement personnalisés peuvent être obtenus en définissant de nouveaux comportements de positionnement au sein de ces méthodes de remplacement.  
  
 De même, les comportements de disposition personnalisés basés sur des classes dérivées (telles que <xref:System.Windows.Controls.Canvas> ou <xref:System.Windows.Controls.Grid>) peuvent être définis en substituant leurs <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> et <xref:System.Windows.FrameworkElement.MeasureOverride%2A> méthodes.  
  
 Le balisage suivant montre comment créer un personnalisé <xref:System.Windows.Controls.Panel> élément. Cette nouvelle <xref:System.Windows.Controls.Panel>, défini comme `PlotPanel`, prend en charge le positionnement des éléments enfants via l’utilisation de codées en dur *x -* et *y*coordonnées. Dans cet exemple, un <xref:System.Windows.Shapes.Rectangle> élément (non illustré) est positionné sur des points de tracé 50 (*x*) et 50 (*y*).  
  
 [!code-cpp[PlotPanel#1](~/samples/snippets/cpp/VS_Snippets_Wpf/PlotPanel/CPP/PlotPanel.cpp#1)]
 [!code-csharp[PlotPanel#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PlotPanel/CSharp/PlotPanel.cs#1)]
 [!code-vb[PlotPanel#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PlotPanel/VisualBasic/PlotPanel.vb#1)]  
  
 Pour voir une implémentation d’élément Panel personnalisé plus complexe, consultez [Créer un exemple de panneau d’agencement de contenu personnalisé](https://go.microsoft.com/fwlink/?LinkID=159979).  
  
<a name="Panels_global_localization"></a>   
## <a name="localizationglobalization-support"></a>Prise en charge de la localisation/globalisation  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] prend en charge un certain nombre de fonctionnalités qui facilitent la création d’IU [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] localisables.  
  
 Tous les éléments panel prennent nativement en charge le <xref:System.Windows.FrameworkElement.FlowDirection%2A> propriété, qui peut être utilisée pour redisposer dynamiquement du contenu selon les paramètres de langue ou de paramètres régionaux d’un utilisateur. Pour plus d'informations, consultez <xref:System.Windows.FrameworkElement.FlowDirection%2A>.  
  
 Le <xref:System.Windows.Window.SizeToContent%2A> propriété fournit un mécanisme qui permet aux développeurs d’applications d’anticiper les besoins de localisé [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. À l’aide de la <xref:System.Windows.SizeToContent.WidthAndHeight> valeur de cette propriété, un parent <xref:System.Windows.Window> toujours redimensionne dynamiquement en fonction du contenu et n’est pas limité par des restrictions de hauteur ou largeur artificielles.  
  
 <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Grid>, et <xref:System.Windows.Controls.StackPanel> sont tous des choix judicieux pour localisables [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. <xref:System.Windows.Controls.Canvas> n’est pas un bon choix, cependant, car il positionne le contenu de façon absolue, le rendant difficile à localiser.  
  
 Pour plus d’informations sur la création d’applications [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] avec des interfaces utilisateur (IU) localisables [!INCLUDE[TLA#tla_ui#plural](../../../../includes/tlasharptla-uisharpplural-md.md)], consultez [Vue d’ensemble de l’utilisation de la disposition automatique](../advanced/use-automatic-layout-overview.md).  
  
## <a name="see-also"></a>Voir aussi

- [Procédure pas à pas : Ma première application de bureau WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md)
- [Galerie de dispositions WPF, exemple](https://go.microsoft.com/fwlink/?LinkID=160054)
- [Disposition](../advanced/layout.md)
- [Exemple de galerie de contrôles WPF](https://go.microsoft.com/fwlink/?LinkID=160053)
- [Vue d'ensemble de l'alignement, des marges et du remplissage](../advanced/alignment-margins-and-padding-overview.md)
- [Créer un exemple de panneau d’agencement de contenu personnalisé](https://go.microsoft.com/fwlink/?LinkID=159979)
- [Vue d'ensemble des propriétés jointes](../advanced/attached-properties-overview.md)
- [Vue d’ensemble de l’utilisation de la disposition automatique](../advanced/use-automatic-layout-overview.md)
- [Disposition et conception](../advanced/optimizing-performance-layout-and-design.md)
