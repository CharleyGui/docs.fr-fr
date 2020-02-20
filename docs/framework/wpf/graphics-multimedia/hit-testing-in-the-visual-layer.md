---
title: Test de positionnement dans la couche visuelle
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hit testing functionality [WPF]
- visual layer [WPF], hit testing functionality
ms.assetid: b1a64b61-14be-4d75-b89a-5c67bebb2c7b
ms.openlocfilehash: 28ae983923c985050ac589166023e483721028d3
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452615"
---
# <a name="hit-testing-in-the-visual-layer"></a>Test de positionnement dans la couche visuelle
Cette rubrique fournit une vue d’ensemble de la fonctionnalité de test de positionnement fournie par la couche visuelle. La prise en charge du test de positionnement vous permet de déterminer si une géométrie ou une valeur de point se trouve dans le contenu rendu d’un <xref:System.Windows.Media.Visual>, ce qui vous permet d’implémenter le comportement de l’interface utilisateur, par exemple un rectangle de sélection pour sélectionner plusieurs objets.  

<a name="hit_testing_scenarios"></a>   
## <a name="hit-testing-scenarios"></a>Scénarios de test de positionnement  
 La classe <xref:System.Windows.UIElement> fournit la méthode <xref:System.Windows.UIElement.InputHitTest%2A>, qui vous permet d’effectuer un test de positionnement sur un élément à l’aide d’une valeur de coordonnée donnée. Dans de nombreux cas, la méthode <xref:System.Windows.UIElement.InputHitTest%2A> fournit les fonctionnalités souhaitées pour l’implémentation du test de positionnement des éléments. Toutefois, il existe plusieurs scénarios dans lesquels vous devrez peut-être implémenter le test de positionnement sur la couche visuelle.  
  
- Test de positionnement sur des objets non-<xref:System.Windows.UIElement> : cela s’applique si vous effectuez un test de positionnement sur des objets non<xref:System.Windows.UIElement>, tels que des objets <xref:System.Windows.Media.DrawingVisual> ou Graphics.  
  
- Test de positionnement à l’aide d’une géométrie : cela s’applique si vous avez besoin d’effectuer un test de positionnement à l’aide d’un objet géométrique plutôt que la valeur des coordonnées d’un point.  
  
- Test de positionnement sur plusieurs objets : cela s’applique lorsque vous devez effectuer un test de positionnement sur plusieurs objets, tels que des objets superposés. Vous pouvez obtenir des résultats pour tous les objets visuels croisant une géométrie ou un point, pas seulement le premier.  
  
- Stratégie de test de positionnement <xref:System.Windows.UIElement> ignorée : cela s’applique lorsque vous devez ignorer la stratégie de test de positionnement <xref:System.Windows.UIElement>, qui prend en considération des facteurs tels que la désactivation ou l’invisibilité d’un élément.  
  
> [!NOTE]
> Pour un exemple de code complet illustrant le test de positionnement sur la couche visuelle, consultez [Test de positionnement à l’aide de l’exemple DrawingVisuals](https://github.com/Microsoft/WPF-Samples/tree/master/Visual%20Layer/DrawingVisual) et [Test de positionnement avec l’exemple Interopérabilité Win32](https://github.com/microsoft/WPF-Samples/tree/master/Visual%20Layer/VisualsHitTesting).  
  
<a name="hit_testing_support"></a>   
## <a name="hit-testing-support"></a>Prise en charge du test de positionnement  
 L’objectif des méthodes <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> dans la classe <xref:System.Windows.Media.VisualTreeHelper> consiste à déterminer si une géométrie ou une valeur de coordonnée de point se trouve dans le contenu rendu d’un objet donné, tel qu’un contrôle ou un élément graphique. Par exemple, vous pouvez utiliser le test de positionnement pour déterminer si un clic de souris dans le rectangle englobant d’un objet se trouve dans la géométrie d’un cercle. Vous pouvez également choisir de substituer l’implémentation par défaut du test de positionnement pour effectuer vos propres calculs de test de positionnement personnalisés.  
  
 L’illustration suivante montre la relation entre la région d’un objet non rectangulaire et son rectangle englobant.  
  
 ![Diagramme de la région de test de positionnement valide](./media/wcpsdk-mmgraphics-visuals-hittest-1.png "wcpsdk_mmgraphics_visuals_hittest_1")  
Diagramme de la région de test de positionnement valide  
  
<a name="hit_testing_and_z-order"></a>   
## <a name="hit-testing-and-z-order"></a>Test de positionnement et ordre de plan  
 La couche visuelle [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] prend en charge le test de positionnement sur tous les objets sous un point ou une géométrie, pas seulement l’objet de niveau supérieur. Les résultats sont retournés dans l’ordre de plan. Toutefois, l’objet visuel que vous transmettez en tant que paramètre à la méthode <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> détermine la partie de l’arborescence d’éléments visuels qui fera l’objet d’un test de positionnement. Vous pouvez effectuer un test de positionnement sur l’arborescence visuelle entière ou une portion de celle-ci.  
  
 Dans l’illustration suivante, l’objet cercle est au-dessus des objets carré et triangle. Si vous êtes uniquement intéressé par le test de positionnement de l’objet visuel dont la valeur de l’ordre de plan est la plus haute, vous pouvez définir l’énumération du test de positionnement visuel pour retourner <xref:System.Windows.Media.HitTestResultBehavior.Stop> à partir de la <xref:System.Windows.Media.HitTestResultCallback> pour arrêter le parcours du test de positionnement après le premier élément.  
  
 ![Diagramme de l’ordre de plan d’une arborescence d’éléments visuels](./media/wcpsdk-mmgraphics-visuals-hittest-2.png "wcpsdk_mmgraphics_visuals_hittest_2")  
Diagramme de l’ordre de plan d’une arborescence d’éléments visuels  
  
 Si vous souhaitez énumérer tous les objets visuels sous un point ou une géométrie spécifique, retournez <xref:System.Windows.Media.HitTestResultBehavior.Continue> à partir du <xref:System.Windows.Media.HitTestResultCallback>. Cela signifie que vous pouvez effectuer un test de positionnement pour des objets visuels situés sous d’autres objets, même s’ils sont complètement masqués. Pour plus d’informations, consultez l’exemple de code dans la section « Utilisation du rappel des résultats d’un test de positionnement ».  
  
> [!NOTE]
> Un objet visuel transparent peut également être l’objet d’un test de positionnement.  
  
<a name="using_default_hit_testing"></a>   
## <a name="using-default-hit-testing"></a>Utilisation du test de positionnement par défaut  
 Vous pouvez déterminer si un point se trouve dans la géométrie d’un objet visuel, en utilisant la méthode <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> pour spécifier un objet visuel et une valeur de coordonnée de point à tester. Le paramètre de l’objet visuel identifie le point de départ dans l’arborescence visuelle pour la recherche du test de positionnement. Si un objet visuel est trouvé dans l’arborescence d’éléments visuels dont la géométrie contient la coordonnée, il est défini sur la propriété <xref:System.Windows.Media.HitTestResult.VisualHit%2A> d’un objet <xref:System.Windows.Media.HitTestResult>. La <xref:System.Windows.Media.HitTestResult> est ensuite retournée par la méthode <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>. Si le point n’est pas contenu dans la sous-arborescence visuelle sur laquelle vous effectuez un test de positionnement, <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> retourne `null`.  
  
> [!NOTE]
> Le test de positionnement par défaut retourne toujours l’objet de plus haut niveau dans l’ordre de plan. Afin d’identifier tous les objets visuels, y compris ceux partiellement ou entièrement cachés, utilisez un rappel des résultats du test de positionnement.  
  
 La valeur de coordonnée que vous transmettez comme paramètre de point pour la méthode <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> doit être relative à l’espace de coordonnées de l’objet visuel sur lequel vous effectuez le test de positionnement. Par exemple, si vous avez imbriqué des objets visuels définis sur (100, 100) dans l’espace des coordonnées du parent, alors le test de positionnement sur un objet visuel enfant à (0, 0) est équivalent au test de positionnement sur (100, 100) dans l’espace des coordonnées du parent.  
  
 Le code suivant montre comment configurer des gestionnaires d’événements de souris pour un objet <xref:System.Windows.UIElement> utilisé pour capturer des événements utilisés pour le test de positionnement.  
  
 [!code-csharp[HitTestingOverview#100](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#100)]
 [!code-vb[HitTestingOverview#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#100)]  
  
### <a name="how-the-visual-tree-affects-hit-testing"></a>Impact de l’arborescence visuelle sur le test de positionnement  
 Le point de départ dans l’arborescence visuelle détermine quels objets sont retournés lors de l’énumération du test de positionnement des objets. Si vous avez plusieurs objets sur lesquels vous voulez effectuer un test de positionnement, l’objet visuel utilisé comme point de départ de l’arborescence visuelle doit être l’ancêtre commun de tous les objets concernés. Par exemple, si vous voulez effectuer un test de positionnement sur l’élément bouton et l’objet visuel de dessin dans le diagramme suivant, vous devez définir le point de départ dans l’arborescence visuelle sur l’ancêtre commun des deux. Dans ce cas, l’élément canevas est l’ancêtre commun de l’élément bouton et de l’objet visuel de dessin.  
  
 ![Diagramme d’une hiérarchie d’arborescence d’éléments visuels](./media/wcpsdk-mmgraphics-visuals-overview-01.gif "wcpsdk_mmgraphics_visuals_overview_01")  
Diagramme d’une hiérarchie d’arborescence d’éléments visuels  
  
> [!NOTE]
> La propriété <xref:System.Windows.UIElement.IsHitTestVisible%2A> obtient ou définit une valeur qui déclare si un objet dérivé de <xref:System.Windows.UIElement>peut éventuellement être retourné comme résultat d’un test de positionnement à partir d’une partie de son contenu rendu. Cela vous permet de modifier de manière sélective l’arborescence visuelle afin de déterminer les objets visuels impliqués dans un test de positionnement.  
  
<a name="using_a_hit_test_result_callback"></a>   
## <a name="using-a-hit-test-result-callback"></a>Utilisation d’un rappel des résultats du test de positionnement  
 Vous pouvez énumérer tous les objets visuels dans une arborescence visuelle dont la géométrie contient une valeur des coordonnées spécifiée. Cela vous permet d’identifier tous les objets visuels, y compris ceux partiellement ou entièrement cachés par d’autres objets visuels. Pour énumérer des objets visuels dans une arborescence d’éléments visuels, utilisez la méthode <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> avec une fonction de rappel de test de positionnement. La fonction de rappel du test de positionnement est appelée par le système lorsque la valeur des coordonnées que vous spécifiez est contenue dans un objet visuel.  
  
 Lors de l’énumération des résultats du test de positionnement, vous ne devez effectuer aucune opération susceptible de modifier l’arborescence visuelle. L’ajout ou la suppression d’un objet dans l’arborescence visuelle pendant qu’il est parcouru peut entraîner un comportement imprévisible. Vous pouvez modifier en toute sécurité l’arborescence d’éléments visuels après le retour de la méthode <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>. Vous pouvez fournir une structure de données, telle qu’une <xref:System.Collections.ArrayList>, pour stocker des valeurs pendant l’énumération des résultats du test de positionnement.  
  
 [!code-csharp[HitTestingOverview#101](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#101)]
 [!code-vb[HitTestingOverview#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#101)]  
  
 La méthode de rappel du test de positionnement définit les actions que vous effectuez lorsqu’un test de positionnement est identifié sur un objet visuel particulier dans l’arborescence visuelle. Après avoir effectué les actions, vous retournez une valeur <xref:System.Windows.Media.HitTestResultBehavior> qui détermine s’il faut continuer l’énumération de tous les autres objets visuels.  
  
 [!code-csharp[HitTestingOverview#102](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#102)]
 [!code-vb[HitTestingOverview#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#102)]  
  
> [!NOTE]
> L’ordre d’énumération des objets visuels de positionnement se fait selon l’ordre de plan. L’objet visuel au niveau de l’ordre de plan le plus élevé est le premier objet énuméré. Les autres objets visuels énumérés le sont dans l’ordre de plan décroissant. Cet ordre d’énumération correspond à l’ordre de rendu des objets visuels.  
  
 Vous pouvez arrêter l’énumération des objets visuels à tout moment dans la fonction de rappel du test de positionnement en retournant <xref:System.Windows.Media.HitTestResultBehavior.Stop>.  
  
 [!code-csharp[HitTestingOverview#103](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#103)]
 [!code-vb[HitTestingOverview#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#103)]  
  
<a name="using_a_hit_test_filter_callback"></a>   
## <a name="using-a-hit-test-filter-callback"></a>Utilisation d’un rappel de filtre du test de positionnement  
 Vous pouvez utiliser un filtre de test de positionnement facultatif pour restreindre les objets transmis aux résultats du test de positionnement. Ceci vous permet d’ignorer les parties de l’arborescence d’éléments visuels que vous ne souhaitez pas traiter dans vos résultats de test de positionnement. Pour implémenter un filtre de test de positionnement, vous devez définir une fonction de rappel de filtre de test de positionnement et la passer en tant que valeur de paramètre lorsque vous appelez la méthode <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>.  
  
 [!code-csharp[HitTestingOverview#104](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#104)]
 [!code-vb[HitTestingOverview#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#104)]  
  
 Si vous ne souhaitez pas fournir la fonction de rappel de filtre de test de positionnement facultative, transmettez une valeur `null` en tant que paramètre pour la méthode <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>.  
  
 [!code-csharp[HitTestingOverview#105](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#105)]
 [!code-vb[HitTestingOverview#105](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#105)]  
  
 ![Élagage d’une arborescence d’éléments visuels à l’aide d’un filtre de test de positionnement](./media/filteredvisualtree-01.png "FilteredVisualTree_01")  
Élagage d’une arborescence visuelle  
  
 La fonction de rappel de filtre de test de positionnement permet d’énumérer tous les objets visuels dont le contenu rendu contient les coordonnées que vous spécifiez. Toutefois, vous pouvez ignorer certaines branches de l’arborescence d’éléments visuels que vous ne souhaitez pas traiter dans votre fonction de rappel des résultats de test de positionnement. La valeur de retour de la fonction de rappel de filtre de test de positionnement détermine le type d’action que l’énumération des objets visuels doit prendre. Par exemple, si vous retournez la valeur, <xref:System.Windows.Media.HitTestFilterBehavior.ContinueSkipSelfAndChildren>, vous pouvez supprimer l’objet visuel actuel et ses enfants de l’énumération des résultats du test de positionnement. Cela signifie que la fonction de rappel des résultats de test de positionnement ne verra pas ces objets dans son énumération. L’élagage des objets dans l’arborescence visuelle diminue la quantité de traitement au cours de la passe de l’énumération des résultats de test de positionnement. Dans l’exemple de code suivant, le filtre ignore les étiquettes et leurs descendants et effectue un test de positionnement sur tout le reste.  
  
 [!code-csharp[HitTestingOverview#106](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#106)]
 [!code-vb[HitTestingOverview#106](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#106)]  
  
> [!NOTE]
> Le rappel de filtre du test de positionnement est parfois appelé dans les cas où le rappel des résultats du test d’atteinte n’est pas appelé.  
  
<a name="overriding_default_hit_testing"></a>   
## <a name="overriding-default-hit-testing"></a>Substitution du test de positionnement par défaut  
 Vous pouvez substituer la prise en charge du test de positionnement par défaut d’un objet visuel en substituant la méthode <xref:System.Windows.Media.Visual.HitTestCore%2A>. Cela signifie que lorsque vous appelez la méthode <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>, votre implémentation substituée de <xref:System.Windows.Media.Visual.HitTestCore%2A> est appelée. Votre méthode substituée est appelée lorsqu’un test de positionnement se situe dans le rectangle englobant de l’objet visuel, même si les coordonnées se situent en dehors du contenu rendu de l’objet visuel.  
  
 [!code-csharp[HitTestingOverview#107](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#107)]
 [!code-vb[HitTestingOverview#107](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#107)]  
  
 Vous voudrez parfois effectuer un nouveau test de positionnement sur le rectangle englobant et le contenu rendu d’un objet visuel. En utilisant la valeur de paramètre `PointHitTestParameters` dans votre méthode <xref:System.Windows.Media.Visual.HitTestCore%2A> substituée comme paramètre de la méthode de base <xref:System.Windows.Media.Visual.HitTestCore%2A>, vous pouvez effectuer des actions en fonction d’un accès au rectangle englobant d’un objet visuel, puis effectuer un deuxième test de positionnement sur le contenu rendu de l’objet visuel.  
  
 [!code-csharp[HitTestingOverview#108](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#108)]
 [!code-vb[HitTestingOverview#108](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#108)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>
- <xref:System.Windows.Media.HitTestResult>
- <xref:System.Windows.Media.HitTestResultCallback>
- <xref:System.Windows.Media.HitTestFilterCallback>
- <xref:System.Windows.UIElement.IsHitTestVisible%2A>
- [Test de positionnement à l’aide de DrawingVisuals, exemple](https://github.com/Microsoft/WPF-Samples/tree/master/Visual%20Layer/DrawingVisual)
- [Exemple d’interopérabilité de test de positionnement avec Win32](https://github.com/microsoft/WPF-Samples/tree/master/Visual%20Layer/VisualsHitTesting)
- [Effectuer un test de positionnement avec Geometry dans un Visual](how-to-hit-test-geometry-in-a-visual.md)
- [Test de positionnement à l’aide d’un conteneur hôte Win32](how-to-hit-test-using-a-win32-host-container.md)
