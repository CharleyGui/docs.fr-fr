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
ms.openlocfilehash: 4f54596e1ce3ed40f3a029ea6703147a97be992f
ms.sourcegitcommit: 43761fcee10aeefcf851ea81cea3f3c691420856
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2019
ms.locfileid: "69545272"
---
# <a name="panels-overview"></a>Vue d'ensemble de Panel
<xref:System.Windows.Controls.Panel>les éléments sont des composants qui contrôlent le rendu des éléments (taille et dimensions, position et disposition de leur contenu enfant). Le [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fournit un certain nombre d' <xref:System.Windows.Controls.Panel> éléments prédéfinis, ainsi que la possibilité de construire <xref:System.Windows.Controls.Panel> des éléments personnalisés.  
  
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
 <xref:System.Windows.Controls.Panel>est la classe de base pour tous les éléments qui assurent [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]la prise en charge de la disposition dans. Les <xref:System.Windows.Controls.Panel> éléments dérivés sont utilisés pour positionner et organiser [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] les éléments dans et le code.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] comprend une suite complète d’implémentations Panel dérivées qui permettent la mise en œuvre de nombreuses dispositions complexes. Ces classes dérivées exposent des propriétés et des méthodes qui rendent possibles la plupart des scénarios [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] standard. Les développeurs qui ne parviennent pas à trouver un comportement de disposition d’enfant qui répond à leurs besoins peuvent créer de <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> nouvelles <xref:System.Windows.FrameworkElement.MeasureOverride%2A> dispositions en remplaçant les méthodes et. Pour plus d’informations sur les comportements de disposition personnalisés, consultez [Éléments Panel personnalisés](#Panels_custom_panel_elements).  
  
<a name="Panels_declared_members"></a>   
## <a name="panel-common-members"></a>Membres communs aux éléments Panel  
 Tous <xref:System.Windows.Controls.Panel> les éléments prennent en charge les propriétés de dimensionnement <xref:System.Windows.FrameworkElement>et de positionnement de base <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>définies <xref:System.Windows.FrameworkElement.Margin%2A>par, <xref:System.Windows.FrameworkElement.LayoutTransform%2A>notamment <xref:System.Windows.FrameworkElement.Height%2A>, <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>,,, et. Pour plus d’informations sur les propriétés de <xref:System.Windows.FrameworkElement>positionnement définies par, consultez [vue d’ensemble de l’alignement, des marges et du remplissage](../advanced/alignment-margins-and-padding-overview.md).  
  
 <xref:System.Windows.Controls.Panel>expose des propriétés supplémentaires qui revêtent une importance capitale pour la compréhension et l’utilisation de la disposition. La <xref:System.Windows.Controls.Panel.Background%2A> propriété est utilisée pour remplir la zone entre les limites d’un élément Panel dérivé avec un <xref:System.Windows.Media.Brush>. <xref:System.Windows.Controls.Panel.Children%2A>représente la collection enfant d’éléments dont le <xref:System.Windows.Controls.Panel> est composé. <xref:System.Windows.Controls.Panel.InternalChildren%2A>représente le contenu de la <xref:System.Windows.Controls.Panel.Children%2A> collection plus les membres générés par la liaison de données. Tous deux se composent d’un <xref:System.Windows.Controls.UIElementCollection> des éléments enfants hébergés dans le parent. <xref:System.Windows.Controls.Panel>  
  
 Le panneau expose également <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType> une propriété jointe qui peut être utilisée pour obtenir l’ordre superposé dans <xref:System.Windows.Controls.Panel>un dérivé. Les membres de la <xref:System.Windows.Controls.Panel.Children%2A> collection d’un panneau ayant une valeur supérieure apparaissent devant ceux dont la valeur est <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType> inférieure <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType> . Cela s’avère particulièrement utile pour les panneaux <xref:System.Windows.Controls.Canvas> tels <xref:System.Windows.Controls.Grid> que et qui permettent aux enfants de partager le même espace de coordonnées.  
  
 <xref:System.Windows.Controls.Panel>définit également la <xref:System.Windows.Controls.Panel.OnRender%2A> méthode, qui peut être utilisée pour substituer le comportement de présentation par défaut <xref:System.Windows.Controls.Panel>d’un.  
  
#### <a name="attached-properties"></a>Propriétés jointes  
 Les éléments Panel dérivés utilisent beaucoup les propriétés jointes. Une propriété jointe est une forme spécialisée de propriété de dépendance qui n’a pas le «wrapper» de propriété common language runtime (CLR) conventionnel. Les propriétés jointes présentent une syntaxe spécialisée dans [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], visible dans plusieurs des exemples qui suivent.  
  
 Une des finalités d’une propriété jointe est de permettre aux éléments enfants de stocker les valeurs uniques d’une propriété définie en fait par un élément parent. Une application de cette fonctionnalité est de faire en sorte que les éléments enfants informent le parent sur la manière dont ils doivent être présentés dans l’interface utilisateur (IU) [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)], ce qui est extrêmement utile pour la disposition de l’application. Pour plus d’informations, consultez [Vue d’ensemble des propriétés jointes](../advanced/attached-properties-overview.md).  
  
<a name="Panels_derived_elements"></a>   
## <a name="derived-panel-elements"></a>Éléments Panel dérivés  
 De nombreux objets dérivent de <xref:System.Windows.Controls.Panel>, mais tous ne sont pas destinés à être utilisés en tant que fournisseurs de disposition racine. Il existe six classes de panneau définies<xref:System.Windows.Controls.Canvas>( <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Grid>, <xref:System.Windows.Controls.StackPanel>, <xref:System.Windows.Controls.VirtualizingStackPanel>, et <xref:System.Windows.Controls.WrapPanel>) conçues spécifiquement pour la création de l' [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]application.  
  
 Chaque élément Panel encapsule sa propre fonctionnalité spéciale, comme indiqué dans le tableau suivant.  
  
|Nom de l'élément|Élément Panel d’IU ?|Description|  
|------------------|---------------|-----------------|  
|<xref:System.Windows.Controls.Canvas>|Oui|Définit une zone dans laquelle vous pouvez positionner explicitement des éléments enfants par coordonnées relatives à <xref:System.Windows.Controls.Canvas> la zone.|  
|<xref:System.Windows.Controls.DockPanel>|Oui|Définit une zone dans laquelle vous pouvez organiser des éléments enfants horizontalement ou verticalement, les uns par rapport aux autres.|  
|<xref:System.Windows.Controls.Grid>|Oui|Définit une zone de grille flexible composée de colonnes et de lignes. Les éléments enfants d' <xref:System.Windows.Controls.Grid> un peuvent être positionnés avec <xref:System.Windows.FrameworkElement.Margin%2A> précision à l’aide de la propriété.|  
|<xref:System.Windows.Controls.StackPanel>|Oui|Dispose des éléments enfants sur une seule ligne orientée horizontalement ou verticalement.|  
|<xref:System.Windows.Controls.Primitives.TabPanel>|Non|Gère la disposition des boutons d’onglet dans <xref:System.Windows.Controls.TabControl>un.|  
|<xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>|Non|Organise le contenu dans un <xref:System.Windows.Controls.ToolBar> contrôle.|  
|<xref:System.Windows.Controls.Primitives.UniformGrid>|Non|<xref:System.Windows.Controls.Primitives.UniformGrid>est utilisé pour organiser les enfants dans une grille avec toutes les tailles de cellule égales.|  
|<xref:System.Windows.Controls.VirtualizingPanel>|Non|Fournit une classe de base pour les éléments Panel qui peuvent « virtualiser » leur collection d’enfants.|  
|<xref:System.Windows.Controls.VirtualizingStackPanel>|Oui|Organise et virtualise un contenu sur une seule ligne orientée horizontalement ou verticalement.|  
|<xref:System.Windows.Controls.WrapPanel>|Oui|<xref:System.Windows.Controls.WrapPanel>positionne les éléments enfants dans un ordre séquentiel de gauche à droite, en fractionnant le contenu à la ligne suivante au bord de la zone conteneur. Le classement suivant se produit séquentiellement de haut en bas ou de droite à gauche, selon la valeur de <xref:System.Windows.Controls.WrapPanel.Orientation%2A> la propriété.|  
  
<a name="Panels_main_UI_elements"></a>   
## <a name="user-interface-panels"></a>Éléments Panel d’interface utilisateur  
 Six classes de panneau sont disponibles dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et sont optimisées pour [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] prendre en <xref:System.Windows.Controls.Canvas>charge <xref:System.Windows.Controls.DockPanel>les <xref:System.Windows.Controls.Grid> <xref:System.Windows.Controls.StackPanel>scénarios <xref:System.Windows.Controls.VirtualizingStackPanel>:,, <xref:System.Windows.Controls.WrapPanel>,, et. Ces éléments Panel sont simples d’utilisation, polyvalents et suffisamment extensibles pour la plupart des applications.  
  
 Chaque élément <xref:System.Windows.Controls.Panel> dérivé traite différemment les contraintes de dimensionnement. Le fait de <xref:System.Windows.Controls.Panel> comprendre comment un gère les contraintes dans le sens horizontal ou vertical peut rendre la disposition plus prévisible.  
  
|**Nom de l’élément Panel**|**Dimension x**|**Dimension y**|  
|--------------------|----------------------|----------------------|  
|<xref:System.Windows.Controls.Canvas>|Restreinte au contenu|Restreinte au contenu|  
|<xref:System.Windows.Controls.DockPanel>|Restreinte|Restreinte|  
|<xref:System.Windows.Controls.StackPanel>(Orientation verticale)|Restreinte|Restreinte au contenu|  
|<xref:System.Windows.Controls.StackPanel>(Orientation horizontale)|Restreinte au contenu|Restreinte|  
|<xref:System.Windows.Controls.Grid>|Restreinte|Avec restriction, sauf dans les cas où <xref:System.Windows.GridUnitType.Auto> s’appliquent aux lignes et aux colonnes|  
|<xref:System.Windows.Controls.WrapPanel>|Restreinte au contenu|Restreinte au contenu|  
  
 Vous trouverez des descriptions plus détaillées et des exemples d’utilisation de chacun de ces éléments ci-dessous.  
  
<a name="Panels_overview_Canvas_subsection"></a>   
### <a name="canvas"></a>Canvas  
 L' <xref:System.Windows.Controls.Canvas> élément permet de positionner le contenu en fonction des coordonnées absolues *x* et *y*. Les éléments peuvent être dessinés dans un emplacement unique, ou s’ils occupent les mêmes coordonnées, l’ordre dans lequel ils apparaissent dans le balisage détermine l’ordre dans lequel ils sont dessinés.  
  
 <xref:System.Windows.Controls.Canvas>fournit la prise en charge de disposition la <xref:System.Windows.Controls.Panel>plus flexible de n’importe laquelle. Les propriétés de hauteur et de largeur sont utilisées pour définir la zone du canevas, et les éléments à l’intérieur de sont des coordonnées absolues <xref:System.Windows.Controls.Canvas>relatives à la zone du parent. Quatre propriétés jointes <xref:System.Windows.Controls.Canvas.Left%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.Canvas.Top%2A?displayProperty=nameWithType> <xref:System.Windows.Controls.Canvas.Right%2A?displayProperty=nameWithType> , et <xref:System.Windows.Controls.Canvas.Bottom%2A?displayProperty=nameWithType>, permettent de contrôler précisément le positionnement des objets <xref:System.Windows.Controls.Canvas>dans un, ce qui permet au développeur de positionner et de réorganiser les éléments avec précision sur l’écran.  
  
#### <a name="cliptobounds-within-a-canvas"></a>Propriété ClipToBounds à l’intérieur d’un élément Canvas  
 <xref:System.Windows.Controls.Canvas>peut positionner des éléments enfants à n’importe quelle position sur l’écran, même aux coordonnées qui se trouvent en <xref:System.Windows.FrameworkElement.Height%2A> dehors <xref:System.Windows.FrameworkElement.Width%2A>de ses propres et. En outre <xref:System.Windows.Controls.Canvas> , n’est pas affecté par la taille de ses enfants. Par conséquent, il est possible qu’un élément enfant redessine d’autres éléments en dehors du rectangle englobant du parent <xref:System.Windows.Controls.Canvas>. Le comportement par défaut d' <xref:System.Windows.Controls.Canvas> un est de permettre aux enfants d’être dessinés en dehors des limites <xref:System.Windows.Controls.Canvas>du parent. Si ce comportement n’est pas souhaitable, <xref:System.Windows.UIElement.ClipToBounds%2A> la propriété peut avoir la `true`valeur. Cela a <xref:System.Windows.Controls.Canvas> pour effet de découper sa taille. <xref:System.Windows.Controls.Canvas>est le seul élément de disposition qui permet aux enfants d’être dessinés en dehors de ses limites.  
  
 Ce comportement est illustré en images dans l’[exemple de comparaison des propriétés Width](https://go.microsoft.com/fwlink/?LinkID=160050).  
  
#### <a name="defining-and-using-a-canvas"></a>Définition et utilisation d’un élément Canvas  
 Un <xref:System.Windows.Controls.Canvas> peut être instancié simplement à l’aide [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] de ou du code. L’exemple suivant montre comment utiliser <xref:System.Windows.Controls.Canvas> pour positionner de manière absolue le contenu. Ce code génère trois carrés de 100 pixels de côté. Le premier carré est rouge, et la position de son angle supérieur gauche (*x, y*) est définie sur (0, 0). Le deuxième carré est vert, et la position de son angle supérieur gauche est définie sur (100, 100), juste en dessous et à droite du premier carré. Le troisième carré est bleu, et la position de son angle supérieur gauche est définie sur (50, 50). Il englobe ainsi le quart inférieur droit du premier carré et le quart supérieur gauche du deuxième. Comme le troisième carré est disposé en dernier, il apparaît au-dessus des deux autres carrés, c’est-à-dire que les parties qui se chevauchent prennent la couleur de ce troisième carré.  
  
 [!code-csharp[CanvasOvwSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CanvasOvwSample/CSharp/Canvas_Ovw_Sample.cs#1)]
 [!code-vb[CanvasOvwSample#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasOvwSample/VisualBasic/canvas_vb.vb#1)]
 [!code-xaml[CanvasOvwSample#1](~/samples/snippets/xaml/VS_Snippets_Wpf/CanvasOvwSample/XAML/default.xaml#1)]  
  
 L’application compilée produit une nouvelle [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]IU qui ressemble à ceci.  
  
 ![Élément Canvas classique.](./media/panel-intro-canvas.PNG "panel_intro_canvas")  
  
<a name="Panels_overview_DockPanel_subsection"></a>   
### <a name="dockpanel"></a>DockPanel  
 L' <xref:System.Windows.Controls.DockPanel> élément utilise la <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> propriété jointe telle qu’elle est définie dans les éléments de contenu enfants pour positionner le contenu le long des bords d’un conteneur. Lorsque <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> a la <xref:System.Windows.Controls.Dock.Top> valeur ou <xref:System.Windows.Controls.Dock.Bottom>, il positionne les éléments enfants au-dessus ou en dessous des autres. Lorsque <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> a la <xref:System.Windows.Controls.Dock.Left> valeur ou <xref:System.Windows.Controls.Dock.Right>, il positionne les éléments enfants à gauche ou à droite l’un de l’autre. La <xref:System.Windows.Controls.DockPanel.LastChildFill%2A> propriété détermine la position du dernier élément ajouté en tant qu’enfant <xref:System.Windows.Controls.DockPanel>de.  
  
 Vous pouvez utiliser <xref:System.Windows.Controls.DockPanel> pour positionner un groupe de contrôles connexes, tel qu’un ensemble de boutons. Vous pouvez également l’utiliser pour créer un «volet» [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], similaire à celui qui se trouve dans Microsoft Outlook.  
  
#### <a name="sizing-to-content"></a>Dimensionnement en fonction du contenu  
 Si ses <xref:System.Windows.FrameworkElement.Height%2A> propriétés <xref:System.Windows.FrameworkElement.Width%2A> et ne sont pas spécifiées, <xref:System.Windows.Controls.DockPanel> la taille de son contenu est redimensionnée. La taille peut augmenter ou diminuer pour s’adapter à la taille de ses éléments enfants. Toutefois, lorsque ces propriétés sont spécifiées et qu’il n’y a plus d’espace pour l’élément <xref:System.Windows.Controls.DockPanel> enfant spécifié suivant, n’affiche pas cet élément enfant ou les éléments enfants suivants et ne mesure pas les éléments enfants suivants.  
  
#### <a name="lastchildfill"></a>Propriété LastChildFill  
 Par défaut, le dernier enfant d’un <xref:System.Windows.Controls.DockPanel> élément «remplit» l’espace non alloué restant. Si ce comportement n’est pas souhaité, affectez la `false`valeur à la <xref:System.Windows.Controls.DockPanel.LastChildFill%2A> propriété.  
  
#### <a name="defining-and-using-a-dockpanel"></a>Définition et utilisation d’un élément DockPanel  
 L’exemple suivant montre comment partitionner l’espace à <xref:System.Windows.Controls.DockPanel>l’aide d’un. Cinq <xref:System.Windows.Controls.Border> éléments sont ajoutés en tant qu’enfants d' <xref:System.Windows.Controls.DockPanel>un parent. Chaque utilise une propriété de positionnement différente de <xref:System.Windows.Controls.DockPanel> a pour partitionner l’espace. Le dernier élément « remplit » l’espace non alloué restant.  
  
 [!code-cpp[DockPanelOvwSample#1](~/samples/snippets/cpp/VS_Snippets_Wpf/DockPanelOvwSample/CPP/DockPanel_Ovw_Sample.cpp#1)]
 [!code-csharp[DockPanelOvwSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/DockPanelOvwSample/CSharp/DockPanel_Ovw_Sample.cs#1)]
 [!code-vb[DockPanelOvwSample#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelOvwSample/VisualBasic/dockpanel_vb.vb#1)]
 [!code-xaml[DockPanelOvwSample#1](~/samples/snippets/xaml/VS_Snippets_Wpf/DockPanelOvwSample/XAML/default.xaml#1)]  
  
 L’application compilée produit une nouvelle [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]IU qui ressemble à ceci.  
  
 ![Scénario classique d’utilisation de l’élément DockPanel.](./media/panel-intro-dockpanel.PNG "panel_intro_dockpanel")  
  
<a name="Panels_overview_Grid_subsection"></a>   
### <a name="grid"></a>Grille  
 L' <xref:System.Windows.Controls.Grid> élément fusionne les fonctionnalités d’un positionnement absolu et d’un contrôle de données tabulaires. Un <xref:System.Windows.Controls.Grid> vous permet de positionner et de style facilement des éléments. <xref:System.Windows.Controls.Grid>vous permet de définir des regroupements de lignes et de colonnes flexibles et fournit même un mécanisme pour partager des <xref:System.Windows.Controls.Grid> informations de dimensionnement entre plusieurs éléments.  
  
#### <a name="how-is-grid-different-from-table"></a>En quoi un élément Grid diffère-t-il d’un élément Table ?  
 <xref:System.Windows.Documents.Table>et <xref:System.Windows.Controls.Grid> partagent des fonctionnalités communes, mais chacune convient mieux à différents scénarios. Un <xref:System.Windows.Documents.Table> est conçu pour être utilisé dans le contenu dynamique (pour plus d’informations sur le contenu dynamique, consultez [vue d’ensemble des documents dynamiques](../advanced/flow-document-overview.md) ). Les éléments Grid sont mieux adaptés à une utilisation dans des formulaires (autrement dit, partout, sauf dans du contenu dynamique). Dans un <xref:System.Windows.Documents.FlowDocument>, <xref:System.Windows.Documents.Table> prend en charge les comportements de contenu de workflow tels que la pagination, le rechargement <xref:System.Windows.Controls.Grid> de colonnes et la sélection de contenu alors qu’un ne le fait pas. En revanche, il est préférable de l’utiliser en dehors <xref:System.Windows.Documents.FlowDocument> d’un pour de <xref:System.Windows.Controls.Grid> nombreuses raisons, <xref:System.Windows.Documents.Table> notamment l’ajout d’éléments basés sur un index de ligne et de colonne. <xref:System.Windows.Controls.Grid> L' <xref:System.Windows.Controls.Grid> élément permet la superposition de contenu enfant, ce qui permet à plusieurs éléments d’exister dans une même «cellule». <xref:System.Windows.Documents.Table>ne prend pas en charge la superposition. Les éléments enfants d' <xref:System.Windows.Controls.Grid> un peuvent être positionnés de façon absolue par rapport à la zone de leurs limites de «cellule». <xref:System.Windows.Documents.Table>ne prend pas en charge cette fonctionnalité. Enfin, un <xref:System.Windows.Controls.Grid> est plus léger qu’un. <xref:System.Windows.Documents.Table>  
  
#### <a name="sizing-behavior-of-columns-and-rows"></a>Comportement de dimensionnement des colonnes et des lignes  
 Les colonnes et les lignes définies <xref:System.Windows.Controls.Grid> dans un peuvent tirer <xref:System.Windows.GridUnitType.Star> parti du dimensionnement afin de répartir proportionnellement l’espace restant. Lorsque <xref:System.Windows.GridUnitType.Star> est sélectionné en tant que hauteur ou largeur d’une ligne ou d’une colonne, cette colonne ou cette ligne reçoit une proportion pondérée de l’espace disponible restant. Cela diffère de <xref:System.Windows.GridUnitType.Auto>, qui répartit uniformément l’espace en fonction de la taille du contenu dans une colonne ou une ligne. Cette valeur est exprimée en tant que `*` ou `2*` lorsque [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] est utilisé. Dans le premier cas, la ligne ou la colonne reçoit une fois l’espace disponible, dans le deuxième cas, deux fois, et ainsi de suite. En combinant cette technique pour répartir proportionnellement l’espace avec <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> un <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> et la `Stretch` valeur de, il est possible de partitionner l’espace de disposition par pourcentage de l’espace d’écran. <xref:System.Windows.Controls.Grid>est le seul panneau de disposition qui peut distribuer l’espace de cette manière.  
  
#### <a name="defining-and-using-a-grid"></a>Définition et utilisation d’un élément Grid  
 L’exemple suivant montre comment créer une IU [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] similaire à celle de la boîte de dialogue Exécuter disponible dans le menu Démarrer de [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)].  
  
 [!code-csharp[GridRunDialog#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GridRunDialog/CSharp/window1.xaml.cs#1)]
 [!code-vb[GridRunDialog#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GridRunDialog/VisualBasic/grid_vb.vb#1)]  
  
 L’application compilée produit une nouvelle [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]IU qui ressemble à ceci.  
  
 ![Élément Grid classique.](./media/avalon-run-dialog.PNG "avalon_run_dialog")  
  
<a name="Panels_overview_StackPanel_subsection"></a>   
### <a name="stackpanel"></a>StackPanel  
 Un <xref:System.Windows.Controls.StackPanel> vous permet de «empiler» des éléments dans une direction assignée. Le sens d’empilement par défaut est vertical. La <xref:System.Windows.Controls.StackPanel.Orientation%2A> propriété peut être utilisée pour contrôler le déroulement du contenu.  
  
#### <a name="stackpanel-vs-dockpanel"></a>Comparaison des éléments StackPanel et DockPanel  
 Bien <xref:System.Windows.Controls.DockPanel> qu’il puisse également «empiler <xref:System.Windows.Controls.DockPanel> » <xref:System.Windows.Controls.StackPanel> des éléments enfants, et ne produisent pas des résultats analogues dans certains scénarios d’utilisation. Par exemple, l’ordre des éléments enfants peut affecter leur taille dans un <xref:System.Windows.Controls.DockPanel> , mais pas dans <xref:System.Windows.Controls.StackPanel>un. Cela est dû <xref:System.Windows.Controls.StackPanel> au fait que mesure dans le sens de <xref:System.Double.PositiveInfinity>l’empilement à, tandis <xref:System.Windows.Controls.DockPanel> que mesure uniquement la taille disponible.  
  
 L’exemple suivant illustre cette différence clé.  
  
 [!code-cpp[StackPanelOvw4#1](~/samples/snippets/cpp/VS_Snippets_Wpf/StackPanelOvw4/CPP/StackPanel_Ovw_Sample4.cpp#1)]
 [!code-csharp[StackPanelOvw4#1](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanelOvw4/CSharp/StackPanel_Ovw_Sample4.cs#1)]
 [!code-vb[StackPanelOvw4#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelOvw4/VisualBasic/StackPanelSamp.vb#1)]
 [!code-xaml[StackPanelOvw4#1](~/samples/snippets/xaml/VS_Snippets_Wpf/StackPanelOvw4/XAML/default.xaml#1)]  
  
 La différence de comportement du rendu peut être observée dans cette image.  
  
 ![Capture d’écran Comparaison des éléments StackPanel et DockPanel](./media/layout-smiley-stackpanel.PNG "layout_smiley_stackpanel")  
  
#### <a name="defining-and-using-a-stackpanel"></a>Définition et utilisation d’un élément StackPanel  
 L’exemple suivant montre comment utiliser un <xref:System.Windows.Controls.StackPanel> pour créer un ensemble de boutons positionnés verticalement. Pour le positionnement horizontal, affectez la <xref:System.Windows.Controls.Orientation.Horizontal>valeur à la <xref:System.Windows.Controls.StackPanel.Orientation%2A> propriété.  
  
 [!code-csharp[StackPanel_ovw2#1](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanel_ovw2/CSharp/StackPanel_Ovw_Sample2.cs#1)]
 [!code-vb[StackPanel_ovw2#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanel_ovw2/VisualBasic/StackPanelOvw.vb#1)]  
  
 L’application compilée produit une nouvelle [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]IU qui ressemble à ceci.  
  
 ![Élément StackPanel standard.](./media/panel-intro-stackpanel.PNG "panel_intro_stackpanel")  
  
<a name="Panels_overview_VirtualizingStackPanel_subsection"></a>   
#### <a name="virtualizingstackpanel"></a>Élément VirtualizingStackPanel  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]fournit également une variante de l' <xref:System.Windows.Controls.StackPanel> élément qui «virtualise» automatiquement le contenu enfant lié aux données. Dans ce contexte, le mot virtualiser fait référence à une technique par laquelle un sous-ensemble d’éléments est généré à partir d’un plus grand nombre d’éléments de données en fonction des éléments visibles à l’écran. La génération d’un grand nombre d’éléments d’interface utilisateur, alors que seul un certain nombre de ces éléments peut figurer à l’écran à un moment donné, entraîne une utilisation intensive de la mémoire et du processeur. <xref:System.Windows.Controls.VirtualizingStackPanel>(par le biais de <xref:System.Windows.Controls.VirtualizingPanel>la fonctionnalité fournie par) calcule les éléments <xref:System.Windows.Controls.ItemContainerGenerator> visibles et <xref:System.Windows.Controls.ItemsControl> utilise le à partir <xref:System.Windows.Controls.ListView>d’un (tel que <xref:System.Windows.Controls.ListBox> ou) pour créer uniquement des éléments pour les éléments visibles.  
  
 L' <xref:System.Windows.Controls.VirtualizingStackPanel> élément est automatiquement défini comme hôte des éléments pour les contrôles tels <xref:System.Windows.Controls.ListBox>que. Lors de l’hébergement d’une collection liée aux données, le contenu est automatiquement virtualisé, à condition que le contenu se trouve dans <xref:System.Windows.Controls.ScrollViewer>les limites d’un. Cela améliore considérablement les performances lorsque de nombreux éléments enfants sont hébergés.  
  
 Le balisage suivant montre comment utiliser un <xref:System.Windows.Controls.VirtualizingStackPanel> comme hôte d’éléments. La <xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizingProperty?displayProperty=nameWithType> propriété jointe doit avoir la `true` valeur (valeur par défaut) pour que la virtualisation se produise.  
  
 [!code-xaml[VirtualizingStackPanel_Intro#1](~/samples/snippets/csharp/VS_Snippets_Wpf/VirtualizingStackPanel_Intro/CS/default.xaml#1)]  
  
<a name="Panels_overview_WrapPanel"></a>   
### <a name="wrappanel"></a>WrapPanel  
 <xref:System.Windows.Controls.WrapPanel>est utilisé pour positionner des éléments enfants dans un ordre séquentiel de gauche à droite, en scindant le contenu à la ligne suivante lorsqu’il atteint le bord de son conteneur parent. Le contenu peut être orienté horizontalement ou verticalement. <xref:System.Windows.Controls.WrapPanel>est utile pour les [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] scénarios de workflow simples. Il peut également être utilisé pour appliquer un dimensionnement uniforme à tous ses éléments enfants.  
  
 L’exemple suivant montre comment créer un <xref:System.Windows.Controls.WrapPanel> pour afficher <xref:System.Windows.Controls.Button> les contrôles qui sont renvoyés à la ligne lorsqu’ils atteignent le bord de leur conteneur.  
  
 [!code-cpp[WrapPanel_Intro#1](~/samples/snippets/cpp/VS_Snippets_Wpf/WrapPanel_Intro/CPP/WrapPanel_Code.cpp#1)]
 [!code-csharp[WrapPanel_Intro#1](~/samples/snippets/csharp/VS_Snippets_Wpf/WrapPanel_Intro/CSharp/WrapPanel_Code.cs#1)]
 [!code-vb[WrapPanel_Intro#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WrapPanel_Intro/VisualBasic/WrapPanel_vb.vb#1)]
 [!code-xaml[WrapPanel_Intro#1](~/samples/snippets/xaml/VS_Snippets_Wpf/WrapPanel_Intro/XAML/default.xaml#1)]  
  
 L’application compilée produit une nouvelle [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]IU qui ressemble à ceci.  
  
 ![Élément WrapPanel standard.](./media/wrappanel-element.PNG "WrapPanel_Element")  
  
<a name="Panels_nested_panel_elements"></a>   
## <a name="nested-panel-elements"></a>Éléments Panel imbriqués  
 <xref:System.Windows.Controls.Panel>les éléments peuvent être imbriqués les uns dans les autres afin de produire des dispositions complexes. Cela peut s’avérer très utile dans les situations <xref:System.Windows.Controls.Panel> où l’une d’elles est idéale [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]pour une partie d’un, mais peut ne pas répondre aux besoins [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]d’une autre partie du.  
  
 Il n’existe aucune limite concernant le nombre d’imbrications que votre application peut prendre en charge. Toutefois, il est généralement préférable de limiter ces éléments Panel à ceux qui sont réellement nécessaires pour la disposition souhaitée. Dans de nombreux cas, <xref:System.Windows.Controls.Grid> un élément peut être utilisé à la place de panneaux imbriqués en raison de sa flexibilité comme un conteneur de disposition. Cela peut accroître les performances au sein de votre application en laissant les éléments inutiles en dehors de l’arborescence.  
  
 L’exemple suivant montre comment créer un [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] qui tire parti des <xref:System.Windows.Controls.Panel> éléments imbriqués afin d’obtenir une disposition spécifique. Dans ce cas particulier, un <xref:System.Windows.Controls.DockPanel> élément est utilisé pour fournir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] la <xref:System.Windows.Controls.StackPanel> structure, et les éléments <xref:System.Windows.Controls.Grid>imbriqués, et <xref:System.Windows.Controls.Canvas> sont utilisés pour positionner des éléments enfants avec précision dans le <xref:System.Windows.Controls.DockPanel>parent.  
  
 [!code-csharp[Nested_Panels#1](~/samples/snippets/csharp/VS_Snippets_Wpf/Nested_Panels/CSharp/nestedpanels.cs#1)]
 [!code-vb[Nested_Panels#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Nested_Panels/VisualBasic/nestedpanels.vb#1)]  
  
 L’application compilée produit une nouvelle [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]IU qui ressemble à ceci.  
  
 ![IU tirant parti d’éléments Panel imbriqués.](./media/nested-panels.PNG "nested_panels")  
  
<a name="Panels_custom_panel_elements"></a>   
## <a name="custom-panel-elements"></a>Éléments Panel personnalisés  
 Tandis que [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit un tableau de contrôles de disposition flexibles, les comportements de disposition personnalisés peuvent également être obtenus en <xref:System.Windows.FrameworkElement.MeasureOverride%2A> remplaçant les <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> méthodes et. Un dimensionnement et un positionnement personnalisés peuvent être obtenus en définissant de nouveaux comportements de positionnement au sein de ces méthodes de remplacement.  
  
 De même, les comportements de disposition personnalisés basés sur des classes dérivées <xref:System.Windows.Controls.Canvas> ( <xref:System.Windows.Controls.Grid>telles que ou) peuvent être définis en <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> remplaçant <xref:System.Windows.FrameworkElement.MeasureOverride%2A> leurs méthodes et.  
  
 Le balisage suivant montre comment créer un élément <xref:System.Windows.Controls.Panel> personnalisé. Ce nouveau <xref:System.Windows.Controls.Panel>, défini en `PlotPanel`tant que, prend en charge le positionnement des éléments enfants à l’aide de coordonnées *x* et *y*codées en dur. Dans cet exemple, un <xref:System.Windows.Shapes.Rectangle> élément (non affiché) est positionné au niveau du traçage point 50 (*x*) et 50 (*y*).  
  
 [!code-cpp[PlotPanel#1](~/samples/snippets/cpp/VS_Snippets_Wpf/PlotPanel/CPP/PlotPanel.cpp#1)]
 [!code-csharp[PlotPanel#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PlotPanel/CSharp/PlotPanel.cs#1)]
 [!code-vb[PlotPanel#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PlotPanel/VisualBasic/PlotPanel.vb#1)]  
  
 Pour voir une implémentation d’élément Panel personnalisé plus complexe, consultez [Créer un exemple de panneau d’agencement de contenu personnalisé](https://go.microsoft.com/fwlink/?LinkID=159979).  
  
<a name="Panels_global_localization"></a>   
## <a name="localizationglobalization-support"></a>Prise en charge de la localisation/globalisation  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] prend en charge un certain nombre de fonctionnalités qui facilitent la création d’IU [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] localisables.  
  
 Tous les éléments Panel prennent en charge <xref:System.Windows.FrameworkElement.FlowDirection%2A> en mode natif la propriété, qui peut être utilisée pour réacheminer dynamiquement du contenu en fonction des paramètres régionaux ou des paramètres de langue d’un utilisateur. Pour plus d'informations, consultez <xref:System.Windows.FrameworkElement.FlowDirection%2A>.  
  
 La <xref:System.Windows.Window.SizeToContent%2A> propriété fournit un mécanisme qui permet aux développeurs d’applications d’anticiper les besoins [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]de localisation. À l' <xref:System.Windows.SizeToContent.WidthAndHeight> aide de la valeur de cette propriété <xref:System.Windows.Window> , un parent est toujours dimensionné dynamiquement pour s’adapter au contenu et n’est pas limité par des restrictions artificielles de hauteur ou de largeur.  
  
 <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Grid> [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]et <xref:System.Windows.Controls.StackPanel> sont tous des bons choix pour localisables. <xref:System.Windows.Controls.Canvas>n’est pas un bon choix, toutefois, car il positionne le contenu de manière absolue, ce qui rend difficile la localisation.  
  
 Pour plus d’informations sur la création d’applications [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] avec des interfaces utilisateur (IU) localisables [!INCLUDE[TLA#tla_ui#plural](../../../../includes/tlasharptla-uisharpplural-md.md)], consultez [Vue d’ensemble de l’utilisation de la disposition automatique](../advanced/use-automatic-layout-overview.md).  
  
## <a name="see-also"></a>Voir aussi

- [Procédure pas à pas : Ma première application de bureau WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md)
- [Galerie de dispositions WPF, exemple](https://go.microsoft.com/fwlink/?LinkID=160054)
- [Disposition](../advanced/layout.md)
- [Exemple de galerie de contrôles WPF](https://go.microsoft.com/fwlink/?LinkID=160053)
- [Vue d'ensemble de l'alignement, des marges et du remplissage](../advanced/alignment-margins-and-padding-overview.md)
- [Créer un exemple de panneau d’habillage du contenu personnalisé](https://go.microsoft.com/fwlink/?LinkID=159979)
- [Vue d'ensemble des propriétés jointes](../advanced/attached-properties-overview.md)
- [Vue d’ensemble de l’utilisation de la disposition automatique](../advanced/use-automatic-layout-overview.md)
- [Disposition et conception](../advanced/optimizing-performance-layout-and-design.md)
