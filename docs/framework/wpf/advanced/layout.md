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
ms.openlocfilehash: 648adb34664ccb2a475e32aba4d0d76d99cf49d8
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666762"
---
# <a name="layout"></a>Mise en page
Cette rubrique décrit le système de disposition Windows Presentation Foundation (WPF). Il est essentiel de comprendre comment et quand les calculs de disposition se produisent sont essentiels pour créer des interfaces utilisateur dans WPF.  
  
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
 Lorsque vous réfléchissez à la disposition dans WPF, il est important de comprendre le cadre englobant qui entoure tous les éléments. Chaque <xref:System.Windows.FrameworkElement> consommé par le système de disposition peut être considéré comme un rectangle qui est fendu dans la disposition. La <xref:System.Windows.Controls.Primitives.LayoutInformation> classe retourne les limites de l’allocation de disposition d’un élément ou de l’emplacement. La taille du rectangle est déterminée en calculant l’espace d’écran disponible, la taille de toutes les contraintes, les propriétés spécifiques à la disposition (par exemple, marge et marge intérieure) et le comportement <xref:System.Windows.Controls.Panel> individuel de l’élément parent. En traitant ces données, le système de disposition est en mesure de calculer la position de tous les enfants <xref:System.Windows.Controls.Panel>d’un particulier. Il est important de se souvenir que les caractéristiques de dimensionnement définies sur l’élément parent <xref:System.Windows.Controls.Border>, telles que, affectent ses enfants.  
  
 L’illustration suivante représente une disposition simple.  
  
 ![Capture d’écran montrant une grille classique, sans cadre englobant superposé.](./media/layout/grid-no-bounding-box-superimpose.png)  
  
 Cette disposition peut être obtenue en utilisant le code [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] suivant.  
  
 [!code-xaml[LayoutInformation#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LayoutInformation/CSharp/Window1.xaml#1)]  
  
 Un élément <xref:System.Windows.Controls.TextBlock> unique est hébergé dans un <xref:System.Windows.Controls.Grid>. Tandis que le texte remplit uniquement l’angle supérieur gauche de la première colonne, l’espace alloué pour le <xref:System.Windows.Controls.TextBlock> est en fait bien plus grand. Le cadre englobant de tout <xref:System.Windows.FrameworkElement> peut être récupéré à l’aide <xref:System.Windows.Controls.Primitives.LayoutInformation.GetLayoutSlot%2A> de la méthode. L’illustration suivante montre le cadre englobant pour l' <xref:System.Windows.Controls.TextBlock> élément.  
  
 ![Capture d’écran montrant que le rectangle englobant TextBlock est maintenant visible.](./media/layout/visible-textblock-bounding-box.png)  
  
 Comme indiqué par le rectangle jaune, l’espace alloué pour l' <xref:System.Windows.Controls.TextBlock> élément est en fait bien plus grand qu’il n’apparaît. À mesure que des éléments supplémentaires sont <xref:System.Windows.Controls.Grid>ajoutés au, cette allocation peut être réduite ou développée, en fonction du type et de la taille des éléments ajoutés.  
  
 L’emplacement de disposition du <xref:System.Windows.Controls.TextBlock> est converti en un <xref:System.Windows.Shapes.Path> à l’aide <xref:System.Windows.Controls.Primitives.LayoutInformation.GetLayoutSlot%2A> de la méthode. Cette technique peut s’avérer utile pour afficher la zone englobante d’un élément.  
  
 [!code-csharp[LayoutInformation#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LayoutInformation/CSharp/Window1.xaml.cs#2)]
 [!code-vb[LayoutInformation#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/LayoutInformation/VisualBasic/Window1.xaml.vb#2)]  
  
<a name="LayoutSystem_Overview"></a>   
## <a name="the-layout-system"></a>Système de disposition  
 Pour schématiser, une disposition est un système récursif qui conduit au dimensionnement, au positionnement et au tracé d’un élément. Plus précisément, la disposition décrit le processus de mesure et d’organisation des membres de <xref:System.Windows.Controls.Panel> la collection <xref:System.Windows.Controls.Panel.Children%2A> d’un élément. La disposition est un processus intensif. Plus la <xref:System.Windows.Controls.Panel.Children%2A> collection est grande, plus le nombre de calculs à effectuer est élevé. La complexité peut également être introduite en fonction du comportement de disposition <xref:System.Windows.Controls.Panel> défini par l’élément qui possède la collection. Un peu plus <xref:System.Windows.Controls.Panel>simple, tel <xref:System.Windows.Controls.Canvas>que, peut avoir de meilleures performances qu’un <xref:System.Windows.Controls.Grid>plus <xref:System.Windows.Controls.Panel>complexe, par exemple.  
  
 Chaque fois qu’un enfant <xref:System.Windows.UIElement> change de position, il a la possibilité de déclencher une nouvelle passe par le système de disposition. Par conséquent, il est important de comprendre quels sont les événements qui peuvent appeler le système de disposition, car un appel inutile peut nuire aux performances de l’application. Le processus suivant décrit ce qui se produit quand le système de disposition est appelé.  
  
1. Un enfant <xref:System.Windows.UIElement> commence le processus de disposition en ayant d’abord mesuré ses propriétés principales.  
  
2. Les <xref:System.Windows.FrameworkElement> propriétés de dimensionnement définies sur sont évaluées, telles que <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.FrameworkElement.Height%2A>et <xref:System.Windows.FrameworkElement.Margin%2A>.  
  
3. <xref:System.Windows.Controls.Panel>la logique spécifique à est appliquée, telle <xref:System.Windows.Controls.Dock> que la direction ou <xref:System.Windows.Controls.StackPanel.Orientation%2A>la pile.  
  
4. Le contenu est réorganisé après que tous les enfants ont été mesurés.  
  
5. La <xref:System.Windows.Controls.Panel.Children%2A> collection est dessinée à l’écran.  
  
6. Le processus est à nouveau appelé si des <xref:System.Windows.Controls.Panel.Children%2A> ajouts supplémentaires sont ajoutés à la <xref:System.Windows.FrameworkElement.LayoutTransform%2A> collection, si est appliqué <xref:System.Windows.UIElement.UpdateLayout%2A> ou si la méthode est appelée.  
  
 Ce processus et la façon dont il est appelé sont décrits plus en détail dans les sections suivantes.  
  
<a name="LayoutSystem_Measure_Arrange"></a>   
## <a name="measuring-and-arranging-children"></a>Mesure et réorganisation d’enfants  
 Le système de disposition effectue deux passes pour chaque membre de <xref:System.Windows.Controls.Panel.Children%2A> la collection, une passe de mesure et une passe de réorganisation. Chaque enfant <xref:System.Windows.Controls.Panel> fournit ses propres <xref:System.Windows.FrameworkElement.MeasureOverride%2A> méthodes <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> et pour obtenir son propre comportement de disposition spécifique.  
  
 Au cours de la passe de mesure, chaque <xref:System.Windows.Controls.Panel.Children%2A> membre de la collection est évalué. Le processus commence par un appel à la <xref:System.Windows.UIElement.Measure%2A> méthode. Cette méthode est appelée dans l’implémentation de l’élément <xref:System.Windows.Controls.Panel> parent et n’a pas besoin d’être appelée explicitement pour que la disposition se produise.  
  
 Tout d’abord, les <xref:System.Windows.UIElement> propriétés de taille natives du sont évaluées, telles que <xref:System.Windows.UIElement.Clip%2A> et <xref:System.Windows.UIElement.Visibility%2A>. Cela génère une valeur nommée `constraintSize` qui est passée à <xref:System.Windows.FrameworkElement.MeasureCore%2A>.  
  
 Deuxièmement, les propriétés du Framework <xref:System.Windows.FrameworkElement> définies sur sont traitées, ce qui affecte `constraintSize`la valeur de. Ces propriétés décrivent généralement les caractéristiques de dimensionnement <xref:System.Windows.UIElement>du sous-jacent <xref:System.Windows.FrameworkElement.Height%2A>, <xref:System.Windows.FrameworkElement.Width%2A>telles <xref:System.Windows.FrameworkElement.Margin%2A>que, <xref:System.Windows.FrameworkElement.Style%2A>, et. Chacune de ces propriétés peut changer l’espace nécessaire à l’affichage de l’élément. <xref:System.Windows.FrameworkElement.MeasureOverride%2A>est ensuite appelé avec `constraintSize` comme paramètre.  
  
> [!NOTE]
>  Il existe une différence entre les propriétés de <xref:System.Windows.FrameworkElement.Height%2A> et <xref:System.Windows.FrameworkElement.Width%2A> de <xref:System.Windows.FrameworkElement.ActualHeight%2A> <xref:System.Windows.FrameworkElement.ActualWidth%2A>et de et. Par exemple, la <xref:System.Windows.FrameworkElement.ActualHeight%2A> propriété est une valeur calculée en fonction d’autres entrées de hauteur et du système de disposition. La valeur est définie par le système de disposition lui-même, en fonction d’une passe de rendu réelle, et peut par conséquent être légèrement en retard par <xref:System.Windows.FrameworkElement.Height%2A>rapport à la valeur définie des propriétés, telles que, qui constituent la base de la modification d’entrée.  
>   
>  Étant <xref:System.Windows.FrameworkElement.ActualHeight%2A> donné que est une valeur calculée, vous devez savoir qu’il peut y avoir des modifications multiples ou incrémentielles signalées à celle-ci suite à différentes opérations par le système de disposition. Celui-ci peut en effet calculer l’espace de mesure requis pour les éléments enfants, les contraintes de l’élément parent, et ainsi de suite.  
  
 L’objectif ultime de la passe de mesure est que l’enfant détermine son <xref:System.Windows.UIElement.DesiredSize%2A>, qui se produit pendant <xref:System.Windows.FrameworkElement.MeasureCore%2A> l’appel. La <xref:System.Windows.UIElement.DesiredSize%2A> valeur est stockée <xref:System.Windows.UIElement.Measure%2A> par pour être utilisée pendant la passe de réorganisation du contenu.  
  
 La passe de réorganisation commence par un appel <xref:System.Windows.UIElement.Arrange%2A> à la méthode. Pendant la passe de réorganisation, <xref:System.Windows.Controls.Panel> l’élément parent génère un rectangle qui représente les limites de l’enfant. Cette valeur est transmise à <xref:System.Windows.FrameworkElement.ArrangeCore%2A> la méthode pour traitement.  
  
 La <xref:System.Windows.FrameworkElement.ArrangeCore%2A> méthode évalue le <xref:System.Windows.UIElement.DesiredSize%2A> de l’enfant et évalue toutes les marges supplémentaires qui peuvent affecter la taille rendue de l’élément. <xref:System.Windows.FrameworkElement.ArrangeCore%2A>génère un `arrangeSize`, qui est passé à la <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> méthode de <xref:System.Windows.Controls.Panel> en tant que paramètre. <xref:System.Windows.FrameworkElement.ArrangeOverride%2A>génère le `finalSize` de l’enfant. Enfin, la <xref:System.Windows.FrameworkElement.ArrangeCore%2A> méthode effectue une évaluation finale des propriétés de décalage, telles que la marge et l’alignement, et place l’enfant dans son emplacement de disposition. L’enfant n’a pas besoin de remplir intégralement l’espace alloué (et souvent ne le remplit pas). Le contrôle est ensuite renvoyé au parent <xref:System.Windows.Controls.Panel> et le processus de disposition est terminé.  
  
<a name="LayoutSystem_PanelsCustom"></a>   
## <a name="panel-elements-and-custom-layout-behaviors"></a>Comportements des éléments de panneau et de disposition personnalisée  
WPF comprend un groupe d’éléments qui dérivent de <xref:System.Windows.Controls.Panel>. Ces <xref:System.Windows.Controls.Panel> éléments activent de nombreuses dispositions complexes. Par exemple, l’empilement d’éléments peut facilement être obtenu <xref:System.Windows.Controls.StackPanel> à l’aide de l’élément, alors que des dispositions plus complexes et plus dynamiques <xref:System.Windows.Controls.Canvas>sont possibles à l’aide d’un.  
  
 Le tableau suivant récapitule les éléments de disposition <xref:System.Windows.Controls.Panel> disponibles.  
  
|Nom du panneau|Description|  
|----------------|-----------------|  
|<xref:System.Windows.Controls.Canvas>|Définit une zone dans laquelle vous pouvez positionner explicitement des éléments enfants par coordonnées relatives à <xref:System.Windows.Controls.Canvas> la zone.|  
|<xref:System.Windows.Controls.DockPanel>|Définit une zone dans laquelle vous pouvez organiser des éléments enfants horizontalement ou verticalement, les uns par rapport aux autres.|  
|<xref:System.Windows.Controls.Grid>|Définit une zone de grille flexible composée de colonnes et de lignes.|  
|<xref:System.Windows.Controls.StackPanel>|Dispose des éléments enfants sur une seule ligne orientée horizontalement ou verticalement.|  
|<xref:System.Windows.Controls.VirtualizingPanel>|Fournit une infrastructure pour <xref:System.Windows.Controls.Panel> les éléments qui virtualisent leur collection de données enfants. Il s’agit d’une classe abstraite.|  
|<xref:System.Windows.Controls.WrapPanel>|Positionne des éléments enfants dans un ordre séquentiel de gauche à droite, en faisant passer le contenu à la ligne suivante au bord de la zone conteneur. Le classement suivant se produit séquentiellement de haut en bas ou de droite à gauche, selon la valeur de <xref:System.Windows.Controls.WrapPanel.Orientation%2A> la propriété.|  
  
 Pour les applications qui requièrent une disposition qui n’est pas possible à l’aide de l' <xref:System.Windows.Controls.Panel> un des éléments prédéfinis, les comportements de disposition personnalisés peuvent <xref:System.Windows.Controls.Panel> être obtenus en héritant <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> de et en substituant les <xref:System.Windows.FrameworkElement.MeasureOverride%2A> méthodes et.  
  
<a name="LayoutSystem_Performance"></a>   
## <a name="layout-performance-considerations"></a>Considérations sur les performances de disposition  
 La disposition est un processus récursif. Chaque élément enfant d’une <xref:System.Windows.Controls.Panel.Children%2A> collection est traité au cours de chaque appel du système de disposition. Par conséquent, il est préférable d’éviter de déclencher le système de disposition quand cela n’est pas nécessaire. Les considérations suivantes peuvent vous aider à bénéficier de meilleures performances.  
  
- Identifiez les changements de valeurs de propriétés qui forceront le système de disposition à procéder à une mise à jour récursive.  
  
     Les propriétés de dépendance dont les valeurs peuvent entraîner l’initialisation du système de disposition sont marquées avec des indicateurs publics. <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A>et <xref:System.Windows.FrameworkPropertyMetadata.AffectsArrange%2A> fournissent des indices utiles quant à la modification des valeurs de propriété qui forcera une mise à jour récursive par le système de disposition. En général, toute propriété qui peut affecter la taille du cadre englobant d’un élément doit avoir un <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A> indicateur défini sur true. Pour plus d’informations, consultez [Vue d’ensemble des propriétés de dépendance](dependency-properties-overview.md).  
  
- Lorsque cela est possible, <xref:System.Windows.UIElement.RenderTransform%2A> utilisez un au <xref:System.Windows.FrameworkElement.LayoutTransform%2A>lieu d’un.  
  
     Un <xref:System.Windows.FrameworkElement.LayoutTransform%2A> peut être un moyen très utile d’affecter le contenu d’un [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. Toutefois, si l’effet de la transformation n’a pas besoin d’influer sur la position d’autres éléments, il est préférable <xref:System.Windows.UIElement.RenderTransform%2A> d’utiliser à <xref:System.Windows.UIElement.RenderTransform%2A> la place, car n’appelle pas le système de disposition. <xref:System.Windows.FrameworkElement.LayoutTransform%2A>applique sa transformation et force une mise à jour de disposition récursive pour tenir compte de la nouvelle position de l’élément affecté.  
  
- Évitez les appels inutiles <xref:System.Windows.UIElement.UpdateLayout%2A>à.  
  
     La <xref:System.Windows.UIElement.UpdateLayout%2A> méthode force une mise à jour de disposition récursive et n’est généralement pas nécessaire. À moins d’être certain qu’une mise à jour complète est nécessaire, laissez le système de disposition appeler cette méthode à votre place.  
  
- Lorsque vous utilisez une grande <xref:System.Windows.Controls.Panel.Children%2A> collection, envisagez <xref:System.Windows.Controls.VirtualizingStackPanel> d’utiliser un au <xref:System.Windows.Controls.StackPanel>lieu d’un normal.  
  
     En virtualisant la collection enfant, le <xref:System.Windows.Controls.VirtualizingStackPanel> conserve uniquement les objets en mémoire qui se trouvent actuellement dans la fenêtre d’affichage du parent. De ce fait, les performances sont considérablement améliorées dans la plupart des scénarios.  
  
<a name="LayoutSystem_LayoutRounding"></a>   
## <a name="sub-pixel-rendering-and-layout-rounding"></a>Rendu d’une précision inférieure au pixel et arrondi de disposition  
 Le système graphique WPF utilise des unités indépendantes du périphérique pour permettre la résolution et l’indépendance des appareils. Chaque pixel indépendant du périphérique est automatiquement mis à l’échelle avec le paramètre points par pouce (dpi) du système. Cela permet aux applications WPF de mettre à l’échelle correctement les différents paramètres ppp et de rendre l’application compatible avec la résolution automatique.  
  
 Toutefois, cette indépendance ppp peut créer un rendu de périphérie irrégulier en raison de l’anticrénelage. Ces artefacts, qui se présentent généralement sous la forme de bords flous ou semi-transparents, peuvent apparaître quand l’emplacement d’un bord se trouve au milieu d’un pixel d’appareil et non entre des pixels d’appareil. Le système de disposition permet d’y remédier grâce à l’arrondi de disposition. L’arrondi de disposition intervient quand le système de disposition arrondit des valeurs de pixel non intégrales pendant la passe de disposition.  
  
 L’arrondi de disposition est désactivé par défaut. Pour activer l’arrondi de disposition, affectez à `true` la propriété <xref:System.Windows.FrameworkElement>la <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> valeur sur any. S’agissant d’une propriété de dépendance, la valeur se propage à tous les enfants de l’arborescence d’éléments visuels. Pour activer l’arrondi de disposition pour l’ensemble de l' <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> interface `true` utilisateur, affectez la valeur à sur le conteneur racine. Pour obtenir un exemple, consultez <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A>.  
  
<a name="LayoutSystem_whatsnext"></a>   
## <a name="whats-next"></a>Étapes suivantes  
 Pour bien comprendre en quoi consiste la disposition, il convient dans un premier temps de comprendre comment les éléments sont mesurés et organisés. Pour plus d’informations sur les <xref:System.Windows.Controls.Panel> éléments disponibles, consultez [vue d’ensemble des panneaux](../controls/panels-overview.md). Pour mieux comprendre les différentes propriétés de positionnement qui peuvent affecter la disposition, consultez [Vue d’ensemble de l’alignement, des marges et du remplissage](alignment-margins-and-padding-overview.md). Lorsque vous êtes prêt à tout réunir dans une application légère, consultez [procédure pas à pas: Ma première application](../getting-started/walkthrough-my-first-wpf-desktop-application.md)de bureau WPF.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.FrameworkElement>
- <xref:System.Windows.UIElement>
- [Vue d’ensemble de Panel](../controls/panels-overview.md)
- [Vue d'ensemble de l'alignement, des marges et du remplissage](alignment-margins-and-padding-overview.md)
- [Disposition et conception](optimizing-performance-layout-and-design.md)
