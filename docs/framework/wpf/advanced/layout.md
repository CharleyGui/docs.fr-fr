---
title: Mise en page
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WPF layout system [WPF]
- controls [WPF], layout system
- layout system [WPF]
ms.assetid: 3eecdced-3623-403a-a077-7595453a9221
ms.openlocfilehash: 93556d8345b09dcd196354e618f4d20f5db68998
ms.sourcegitcommit: 127343afce8422bfa944c8b0c4ecc8f79f653255
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2019
ms.locfileid: "67348523"
---
# <a name="layout"></a>Mise en page
Cette rubrique décrit le système de disposition de [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Pour créer des interfaces utilisateur dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], il est essentiel de comprendre quand et comment interviennent les calculs de disposition.  
  
 Cette rubrique contient les sections suivantes :  
  
- [Zones englobantes d’élément](#LayoutSystem_BoundingBox)  
  
- [Système de disposition](#LayoutSystem_Overview)  
  
- [Mesure et réorganisation d’enfants](#LayoutSystem_Measure_Arrange)  
  
- [Comportements des éléments de panneau et de disposition personnalisée](#LayoutSystem_PanelsCustom)  
  
- [Considérations sur les performances de disposition](#LayoutSystem_Performance)  
  
- [Rendu d’une précision inférieure au pixel et arrondi de disposition](#LayoutSystem_LayoutRounding)  
  
- [Étapes suivantes](#LayoutSystem_whatsnext)  
  
<a name="LayoutSystem_BoundingBox"></a>   
## <a name="element-bounding-boxes"></a>Zones englobantes d’élément  
 Avant de considérer la disposition dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], il est important de comprendre ce qu’est la zone englobante qui entoure tous les éléments. Chaque <xref:System.Windows.FrameworkElement> consommé par la mise en page système peut être considéré comme un rectangle qui est intégré dans la disposition. Le <xref:System.Windows.Controls.Primitives.LayoutInformation> classe retourne les limites d’allocation de disposition d’un élément, ou emplacement. La taille du rectangle est déterminée en calculant l’espace disponible à l’écran, la taille de toutes les contraintes, les propriétés spécifiques à la disposition (par exemple, marge et marge intérieure) et le comportement individuel du parent <xref:System.Windows.Controls.Panel> élément. Traitement des données, le système de disposition est en mesure de calculer la position de tous les enfants d’un particulier <xref:System.Windows.Controls.Panel>. Il est important de se rappeler que caractéristiques de dimensionnement définies sur l’élément parent, comme un <xref:System.Windows.Controls.Border>, affectent ses enfants.  
  
 L’illustration suivante représente une disposition simple.  
  
 ![Capture d’écran qui affiche une grille classique, sans cadre englobant superposé.](./media/layout/grid-no-bounding-box-superimpose.png)  
  
 Cette disposition peut être obtenue en utilisant le code [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] suivant.  
  
 [!code-xaml[LayoutInformation#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LayoutInformation/CSharp/Window1.xaml#1)]  
  
 Un seul <xref:System.Windows.Controls.TextBlock> élément est hébergé dans un <xref:System.Windows.Controls.Grid>. Tandis que le texte remplit uniquement l’angle supérieur gauche de la première colonne, l’espace alloué pour le <xref:System.Windows.Controls.TextBlock> est en fait beaucoup plus important. La zone englobante de n’importe quel <xref:System.Windows.FrameworkElement> peuvent être récupérées à l’aide de la <xref:System.Windows.Controls.Primitives.LayoutInformation.GetLayoutSlot%2A> (méthode). L’illustration suivante montre le cadre englobant pour le <xref:System.Windows.Controls.TextBlock> élément.  
  
 ![Capture d’écran montrant que la zone englobante du TextBlock est maintenant visible.](./media/layout/visible-textblock-bounding-box.png)  
  
 Comme indiqué par le rectangle jaune, l’espace alloué pour le <xref:System.Windows.Controls.TextBlock> élément est en fait bien plus important qu’il s’affiche. Comme les éléments supplémentaires sont ajoutés à la <xref:System.Windows.Controls.Grid>, cette allocation pourrait réduire ou développer, selon le type et la taille des éléments qui sont ajoutés.  
  
 L’emplacement de disposition de la <xref:System.Windows.Controls.TextBlock> est traduite en une <xref:System.Windows.Shapes.Path> à l’aide de la <xref:System.Windows.Controls.Primitives.LayoutInformation.GetLayoutSlot%2A> (méthode). Cette technique peut s’avérer utile pour afficher la zone englobante d’un élément.  
  
 [!code-csharp[LayoutInformation#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LayoutInformation/CSharp/Window1.xaml.cs#2)]
 [!code-vb[LayoutInformation#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/LayoutInformation/VisualBasic/Window1.xaml.vb#2)]  
  
<a name="LayoutSystem_Overview"></a>   
## <a name="the-layout-system"></a>Système de disposition  
 Pour schématiser, une disposition est un système récursif qui conduit au dimensionnement, au positionnement et au tracé d’un élément. Plus précisément, disposition décrit le processus de mesure et réorganisation des membres d’un <xref:System.Windows.Controls.Panel> l’élément <xref:System.Windows.Controls.Panel.Children%2A> collection. La disposition est un processus intensif. Le plus grand le <xref:System.Windows.Controls.Panel.Children%2A> collection, plus le nombre de calculs qui doivent être effectuées. Complexité peut également être introduite en fonction du comportement de disposition défini par le <xref:System.Windows.Controls.Panel> élément auquel appartient la collection. Relativement simple <xref:System.Windows.Controls.Panel>, tel que <xref:System.Windows.Controls.Canvas>, peut avoir de bien meilleures performances qu’un type plus complexe <xref:System.Windows.Controls.Panel>, tel que <xref:System.Windows.Controls.Grid>.  
  
 Chaque fois qu’enfant <xref:System.Windows.UIElement> change de position, il a la possibilité de déclencher une nouvelle passe par le système de disposition. Par conséquent, il est important de comprendre quels sont les événements qui peuvent appeler le système de disposition, car un appel inutile peut nuire aux performances de l’application. Le processus suivant décrit ce qui se produit quand le système de disposition est appelé.  
  
1. Un enfant <xref:System.Windows.UIElement> commence le processus de disposition en faisant d’abord ses propriétés principales mesurées.  
  
2. Propriétés de dimensionnement définies sur <xref:System.Windows.FrameworkElement> sont évaluées, telles que <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.FrameworkElement.Height%2A>, et <xref:System.Windows.FrameworkElement.Margin%2A>.  
  
3. <xref:System.Windows.Controls.Panel>-logique spécifique est appliquée, tel que <xref:System.Windows.Controls.Dock> direction ou empilement <xref:System.Windows.Controls.StackPanel.Orientation%2A>.  
  
4. Le contenu est réorganisé après que tous les enfants ont été mesurés.  
  
5. Le <xref:System.Windows.Controls.Panel.Children%2A> collection est dessinée à l’écran.  
  
6. Le processus est encore appelé si supplémentaires <xref:System.Windows.Controls.Panel.Children%2A> sont ajoutés à la collection, un <xref:System.Windows.FrameworkElement.LayoutTransform%2A> est appliqué, ou la <xref:System.Windows.UIElement.UpdateLayout%2A> méthode est appelée.  
  
 Ce processus et la façon dont il est appelé sont décrits plus en détail dans les sections suivantes.  
  
<a name="LayoutSystem_Measure_Arrange"></a>   
## <a name="measuring-and-arranging-children"></a>Mesure et réorganisation d’enfants  
 Le système de disposition effectue deux passes pour chaque membre de la <xref:System.Windows.Controls.Panel.Children%2A> collection, une passe de mesure et une passe de réorganisation. Chaque enfant <xref:System.Windows.Controls.Panel> fournit son propre <xref:System.Windows.FrameworkElement.MeasureOverride%2A> et <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> permet d’obtenir son propre comportement de disposition spécifique.  
  
 Pendant la passe de mesure, chaque membre de la <xref:System.Windows.Controls.Panel.Children%2A> regroupement est évalué. Le processus commence par un appel à la <xref:System.Windows.UIElement.Measure%2A> (méthode). Cette méthode est appelée dans l’implémentation du parent <xref:System.Windows.Controls.Panel> élément et n’a pas à être appelée explicitement pour la disposition se produise.  
  
 Propriétés de taille tout d’abord, native de la <xref:System.Windows.UIElement> sont évaluées, telles que <xref:System.Windows.UIElement.Clip%2A> et <xref:System.Windows.UIElement.Visibility%2A>. Cela génère une valeur nommée `constraintSize` qui est passé à <xref:System.Windows.FrameworkElement.MeasureCore%2A>.  
  
 Deuxièmement, les propriétés de l’infrastructure définis sur <xref:System.Windows.FrameworkElement> sont traitées, ce qui affecte la valeur de `constraintSize`. Ces propriétés décrivent généralement les caractéristiques de dimensionnement de sous-jacent <xref:System.Windows.UIElement>, telles que son <xref:System.Windows.FrameworkElement.Height%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.FrameworkElement.Margin%2A>, et <xref:System.Windows.FrameworkElement.Style%2A>. Chacune de ces propriétés peut changer l’espace nécessaire à l’affichage de l’élément. <xref:System.Windows.FrameworkElement.MeasureOverride%2A> est ensuite appelée avec `constraintSize` en tant que paramètre.  
  
> [!NOTE]
>  Il existe une différence entre les propriétés de <xref:System.Windows.FrameworkElement.Height%2A> et <xref:System.Windows.FrameworkElement.Width%2A> et <xref:System.Windows.FrameworkElement.ActualHeight%2A> et <xref:System.Windows.FrameworkElement.ActualWidth%2A>. Par exemple, le <xref:System.Windows.FrameworkElement.ActualHeight%2A> propriété est une valeur calculée basée sur les autres entrées de hauteur et le système de disposition. La valeur est définie par le système de disposition lui-même, selon une passe de rendu et peut donc rester légèrement derrière la valeur définie des propriétés, telles que <xref:System.Windows.FrameworkElement.Height%2A>, qui constituent la base de la modification d’entrée.  
>   
>  Étant donné que <xref:System.Windows.FrameworkElement.ActualHeight%2A> est une valeur calculée, vous devez être conscient qu’il peut y avoir plusieurs ou incrémentielles signalées modifications à la suite de diverses opérations par le système de disposition. Celui-ci peut en effet calculer l’espace de mesure requis pour les éléments enfants, les contraintes de l’élément parent, et ainsi de suite.  
  
 L’objectif ultime de la passe de mesure est pour l’enfant de déterminer sa <xref:System.Windows.UIElement.DesiredSize%2A>, qui se produit pendant la <xref:System.Windows.FrameworkElement.MeasureCore%2A> appeler. Le <xref:System.Windows.UIElement.DesiredSize%2A> valeur est stockée par <xref:System.Windows.UIElement.Measure%2A> pour une utilisation pendant la passe de réorganisation du contenu.  
  
 La passe de réorganisation commence par un appel à la <xref:System.Windows.UIElement.Arrange%2A> (méthode). Pendant la passe de réorganisation, le parent <xref:System.Windows.Controls.Panel> élément génère un rectangle qui représente les limites de l’enfant. Cette valeur est passée à la <xref:System.Windows.FrameworkElement.ArrangeCore%2A> méthode pour le traitement.  
  
 Le <xref:System.Windows.FrameworkElement.ArrangeCore%2A> méthode évalue le <xref:System.Windows.UIElement.DesiredSize%2A> de l’enfant et évalue les marges supplémentaires qui peuvent affecter la taille rendue de l’élément. <xref:System.Windows.FrameworkElement.ArrangeCore%2A> génère un `arrangeSize`, qui est transmis à la <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> méthode de la <xref:System.Windows.Controls.Panel> en tant que paramètre. <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> génère le `finalSize` de l’enfant. Enfin, le <xref:System.Windows.FrameworkElement.ArrangeCore%2A> méthode effectue une dernière évaluation des propriétés de décalage, telles que la marge et l’alignement et place l’enfant dans son emplacement de disposition. L’enfant n’a pas besoin de remplir intégralement l’espace alloué (et souvent ne le remplit pas). Contrôle est ensuite renvoyé au parent <xref:System.Windows.Controls.Panel> et le processus de disposition est terminé.  
  
<a name="LayoutSystem_PanelsCustom"></a>   
## <a name="panel-elements-and-custom-layout-behaviors"></a>Comportements des éléments de panneau et de disposition personnalisée  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] inclut un groupe d’éléments qui dérivent de <xref:System.Windows.Controls.Panel>. Ces <xref:System.Windows.Controls.Panel> éléments permettent de nombreuses dispositions complexes. Par exemple, empiler des éléments peut facilement être obtenue à l’aide de la <xref:System.Windows.Controls.StackPanel> élément, tandis que les dispositions de flux plus complexes et libres sont possibles en utilisant un <xref:System.Windows.Controls.Canvas>.  
  
 Le tableau suivant récapitule la mise en page disponible <xref:System.Windows.Controls.Panel> éléments.  
  
|Nom du panneau|Description|  
|----------------|-----------------|  
|<xref:System.Windows.Controls.Canvas>|Définit une zone dans laquelle vous pouvez positionner explicitement des éléments enfants par les coordonnées sont relatives à la <xref:System.Windows.Controls.Canvas> zone.|  
|<xref:System.Windows.Controls.DockPanel>|Définit une zone dans laquelle vous pouvez organiser des éléments enfants horizontalement ou verticalement, les uns par rapport aux autres.|  
|<xref:System.Windows.Controls.Grid>|Définit une zone de grille flexible composée de colonnes et de lignes.|  
|<xref:System.Windows.Controls.StackPanel>|Dispose des éléments enfants sur une seule ligne orientée horizontalement ou verticalement.|  
|<xref:System.Windows.Controls.VirtualizingPanel>|Fournit une infrastructure pour <xref:System.Windows.Controls.Panel> éléments qui virtualisent leur collection de données enfants. Il s’agit d’une classe abstraite.|  
|<xref:System.Windows.Controls.WrapPanel>|Positionne des éléments enfants dans un ordre séquentiel de gauche à droite, en faisant passer le contenu à la ligne suivante au bord de la zone conteneur. Classement continue ensuite séquentiellement de haut en bas ou de droite à gauche, selon la valeur de la <xref:System.Windows.Controls.WrapPanel.Orientation%2A> propriété.|  
  
 Pour les applications qui requièrent une disposition qui n’est pas possible à l’aide des prédéfinis <xref:System.Windows.Controls.Panel> éléments, des comportements de disposition personnalisée peuvent être obtenus en héritant de <xref:System.Windows.Controls.Panel> et en remplaçant le <xref:System.Windows.FrameworkElement.MeasureOverride%2A> et <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> méthodes. Pour obtenir un exemple, consultez [Exemple de panneau radial personnalisé](https://go.microsoft.com/fwlink/?LinkID=159982).  
  
<a name="LayoutSystem_Performance"></a>   
## <a name="layout-performance-considerations"></a>Considérations sur les performances de disposition  
 La disposition est un processus récursif. Chaque élément enfant dans un <xref:System.Windows.Controls.Panel.Children%2A> collection est traitée pendant chaque appel du système de disposition. Par conséquent, il est préférable d’éviter de déclencher le système de disposition quand cela n’est pas nécessaire. Les considérations suivantes peuvent vous aider à bénéficier de meilleures performances.  
  
- Identifiez les changements de valeurs de propriétés qui forceront le système de disposition à procéder à une mise à jour récursive.  
  
     Les propriétés de dépendance dont les valeurs peuvent entraîner l’initialisation du système de disposition sont marquées avec des indicateurs publics. <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A> et <xref:System.Windows.FrameworkPropertyMetadata.AffectsArrange%2A> fournissent des indications utiles concernant la propriété des modifications de valeur forcera une récursive mettre à jour par le système de disposition. En règle générale, toute propriété qui peut affecter la taille du cadre englobant d’un élément doit avoir un <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A> l’indicateur est défini sur true. Pour plus d’informations, consultez [Vue d’ensemble des propriétés de dépendance](dependency-properties-overview.md).  
  
- Si possible, utilisez un <xref:System.Windows.UIElement.RenderTransform%2A> au lieu d’un <xref:System.Windows.FrameworkElement.LayoutTransform%2A>.  
  
     Un <xref:System.Windows.FrameworkElement.LayoutTransform%2A> peut être un moyen très utile pour affecter le contenu d’un [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. Toutefois, si l’effet de la transformation n’a pas d’impact sur la position d’autres éléments, il est préférable d’utiliser un <xref:System.Windows.UIElement.RenderTransform%2A> au lieu de cela, étant donné que <xref:System.Windows.UIElement.RenderTransform%2A> n’appelle pas le système de disposition. <xref:System.Windows.FrameworkElement.LayoutTransform%2A> s’applique sa transformation et force une mise à jour de disposition récursive pour prendre en compte la nouvelle position de l’élément affecté.  
  
- Évitez les appels inutiles à <xref:System.Windows.UIElement.UpdateLayout%2A>.  
  
     Le <xref:System.Windows.UIElement.UpdateLayout%2A> méthode force une mise à jour de disposition récursive et n’est pas souvent nécessaire. À moins d’être certain qu’une mise à jour complète est nécessaire, laissez le système de disposition appeler cette méthode à votre place.  
  
- Lorsque vous travaillez avec un grand <xref:System.Windows.Controls.Panel.Children%2A> collection, envisagez d’utiliser un <xref:System.Windows.Controls.VirtualizingStackPanel> au lieu d’une expression régulière <xref:System.Windows.Controls.StackPanel>.  
  
     En virtualisant la collection enfant, le <xref:System.Windows.Controls.VirtualizingStackPanel> conserve uniquement les objets en mémoire qui se trouvent actuellement dans la fenêtre d’affichage du parent. De ce fait, les performances sont considérablement améliorées dans la plupart des scénarios.  
  
<a name="LayoutSystem_LayoutRounding"></a>   
## <a name="sub-pixel-rendering-and-layout-rounding"></a>Rendu d’une précision inférieure au pixel et arrondi de disposition  
 Le système graphique [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] utilise des unités indépendantes de l’appareil pour assurer une indépendance de la résolution et de l’appareil. Chaque pixel indépendant de l’appareil s’ajuste automatiquement au paramètre [!INCLUDE[TLA#tla_dpi](../../../../includes/tlasharptla-dpi-md.md)] du système. Cela permet aux applications [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de s’ajuster correctement aux différents paramètres [!INCLUDE[TLA2#tla_dpi](../../../../includes/tla2sharptla-dpi-md.md)] et de prendre automatiquement en charge [!INCLUDE[TLA2#tla_dpi](../../../../includes/tla2sharptla-dpi-md.md)].  
  
 Cependant, cette indépendance [!INCLUDE[TLA2#tla_dpi](../../../../includes/tla2sharptla-dpi-md.md)] peut générer un rendu irrégulier des bords en raison de l’anticrénelage. Ces artefacts, qui se présentent généralement sous la forme de bords flous ou semi-transparents, peuvent apparaître quand l’emplacement d’un bord se trouve au milieu d’un pixel d’appareil et non entre des pixels d’appareil. Le système de disposition permet d’y remédier grâce à l’arrondi de disposition. L’arrondi de disposition intervient quand le système de disposition arrondit des valeurs de pixel non intégrales pendant la passe de disposition.  
  
 L’arrondi de disposition est désactivé par défaut. Pour activer l’arrondi de disposition, définissez la <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> propriété `true` sur n’importe quel <xref:System.Windows.FrameworkElement>. S’agissant d’une propriété de dépendance, la valeur se propage à tous les enfants de l’arborescence d’éléments visuels. Pour activer l’arrondi de disposition pour l’interface utilisateur entière, définissez <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> à `true` sur le conteneur racine. Pour obtenir un exemple, consultez <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A>.  
  
<a name="LayoutSystem_whatsnext"></a>   
## <a name="whats-next"></a>Étapes suivantes  
 Pour bien comprendre en quoi consiste la disposition, il convient dans un premier temps de comprendre comment les éléments sont mesurés et organisés. Pour plus d’informations sur la disposition <xref:System.Windows.Controls.Panel> éléments, consultez [vue d’ensemble de panneaux](../controls/panels-overview.md). Pour mieux comprendre les différentes propriétés de positionnement qui peuvent affecter la disposition, consultez [Vue d’ensemble de l’alignement, des marges et du remplissage](alignment-margins-and-padding-overview.md). Pour obtenir un exemple de personnalisé <xref:System.Windows.Controls.Panel> élément, consultez [exemple de panneau Radial personnalisé](https://go.microsoft.com/fwlink/?LinkID=159982). Lorsque vous êtes prêt à tout mettre ensemble dans une application légère, consultez [procédure pas à pas : Ma première application de bureau WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.FrameworkElement>
- <xref:System.Windows.UIElement>
- [Vue d’ensemble de Panel](../controls/panels-overview.md)
- [Vue d'ensemble de l'alignement, des marges et du remplissage](alignment-margins-and-padding-overview.md)
- [Disposition et conception](optimizing-performance-layout-and-design.md)
