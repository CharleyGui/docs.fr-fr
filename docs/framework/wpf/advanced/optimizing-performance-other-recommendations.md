---
title: 'Optimisation des performances : autres recommandations'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Terminal Services rendering [WPF]
- opacity [WPF]
- hit-test objects [WPF]
- ScrollBarVisibility enumeration [WPF]
- brushes [WPF], performance
ms.assetid: d028cc65-7e97-4a4f-9859-929734eaf40d
ms.openlocfilehash: 6b4a5379145ebdffde0d5b76d8c7b9ab57261007
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975790"
---
# <a name="optimizing-performance-other-recommendations"></a>Optimisation des performances : autres recommandations
<a name="introduction"></a> Cette rubrique fournit des recommandations pour améliorer les performances en plus de celles abordées dans les rubriques de la section [Optimisation des performances des applications WPF](optimizing-wpf-application-performance.md).  
  
 Cette rubrique contient les sections suivantes :  
  
- [Opacité au niveau des pinceaux et opacité au niveau des éléments](#Opacity)  
  
- [Navigation vers un objet](#Navigation_Objects)  
  
- [Test de positionnement sur les grandes surfaces 3D](#Hit_Testing)  
  
- [Événement CompositionTarget.Rendering](#CompositionTarget_Rendering_Event)  
  
- [Éviter l’utilisation de ScrollBarVisibility=Auto](#Avoid_Using_ScrollBarVisibility)  
  
- [Configurer le service de mise en cache de polices pour réduire le temps de démarrage](#FontCache)  
  
<a name="Opacity"></a>   
## <a name="opacity-on-brushes-versus-opacity-on-elements"></a>Opacité au niveau des pinceaux et opacité au niveau des éléments  
 Quand vous utilisez un <xref:System.Windows.Media.Brush> pour définir la <xref:System.Windows.Shapes.Shape.Fill%2A> ou la <xref:System.Windows.Shapes.Shape.Stroke%2A> d’un élément, il est préférable de définir la valeur <xref:System.Windows.Media.Brush.Opacity%2A?displayProperty=nameWithType> plutôt que la valeur de la propriété <xref:System.Windows.UIElement.Opacity%2A> de l’élément. La modification de la propriété <xref:System.Windows.UIElement.Opacity%2A> d’un élément peut entraîner la création d’une surface temporaire par [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
<a name="Navigation_Objects"></a>   
## <a name="navigation-to-object"></a>Navigation vers un objet  
 L’objet <xref:System.Windows.Navigation.NavigationWindow> dérive de <xref:System.Windows.Window> et l’étend avec la prise en charge de la navigation dans le contenu, principalement en regroupant <xref:System.Windows.Navigation.NavigationService> et le journal. Vous pouvez mettre à jour la zone cliente de <xref:System.Windows.Navigation.NavigationWindow> en spécifiant un URI (Uniform Resource Identifier) ou un objet. L'exemple suivant illustre les deux méthodes :  
  
 [!code-csharp[Performance#PerformanceSnippet14](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/TestNavigation.xaml.cs#performancesnippet14)]
 [!code-vb[Performance#PerformanceSnippet14](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/testnavigation.xaml.vb#performancesnippet14)]  
  
 Chaque objet <xref:System.Windows.Navigation.NavigationWindow> possède un journal qui enregistre l’historique de navigation de l’utilisateur dans cette fenêtre. Un des objectifs du journal est de permettre aux utilisateurs de retracer leurs étapes.  
  
 Lorsque vous naviguez à l’aide d’un URI (Uniform Resource Identifier), le journal stocke uniquement la référence URI (Uniform Resource Identifier). Cela signifie que chaque fois que vous revisitez la page, elle est reconstruite dynamiquement, ce qui peut prendre beaucoup de temps selon la complexité de la page. Dans ce cas, le coût de stockage du journal est faible, mais le temps de reconstitution de la page est élevé.  
  
 Quand vous naviguez à l’aide d’un objet, le journal stocke intégralement l’arborescence de visuels de l’objet. Cela signifie que chaque fois que vous visitez la page, elle s’affiche immédiatement sans avoir à être reconstruite. Dans ce cas, le coût de stockage du journal est élevé, mais le temps de reconstitution de la page est faible.  
  
 Lorsque vous utilisez l’objet <xref:System.Windows.Navigation.NavigationWindow>, vous devez garder à l’esprit la façon dont la prise en charge de la journalisation a un impact sur les performances de votre application. Pour plus d’informations, consultez [Vue d’ensemble de la navigation](../app-development/navigation-overview.md).  
  
<a name="Hit_Testing"></a>   
## <a name="hit-testing-on-large-3d-surfaces"></a>Test de positionnement sur les grandes surfaces 3D  
 Le test de positionnement sur les grandes surfaces 3D est une opération qui affecte considérablement les performances en utilisant une grande part du processeur. Cela est particulièrement vrai quand la surface 3D est animée. Si vous n’avez pas besoin de tester le positionnement sur ces surfaces, désactivez le test de positionnement. Les objets dérivés de <xref:System.Windows.UIElement> peuvent désactiver le test de positionnement en affectant à la propriété <xref:System.Windows.UIElement.IsHitTestVisible%2A> la valeur `false`.  
  
<a name="CompositionTarget_Rendering_Event"></a>   
## <a name="compositiontargetrendering-event"></a>Événement CompositionTarget.Rendering  
 L’événement <xref:System.Windows.Media.CompositionTarget.Rendering?displayProperty=nameWithType> entraîne l’animation continue [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Si vous utilisez cet événement, détacher-le dès que possible.  
  
<a name="Avoid_Using_ScrollBarVisibility"></a>   
## <a name="avoid-using-scrollbarvisibilityauto"></a>Éviter l’utilisation de ScrollBarVisibility=Auto  
 Dans la mesure du possible, évitez d’utiliser la valeur <xref:System.Windows.Controls.ScrollBarVisibility.Auto?displayProperty=nameWithType> pour les propriétés `HorizontalScrollBarVisibility` et `VerticalScrollBarVisibility`. Ces propriétés sont définies pour les objets <xref:System.Windows.Controls.RichTextBox>, <xref:System.Windows.Controls.ScrollViewer> et <xref:System.Windows.Controls.TextBox>, et en tant que propriété jointe pour l’objet <xref:System.Windows.Controls.ListBox>. Au lieu de cela, définissez <xref:System.Windows.Controls.ScrollBarVisibility> sur <xref:System.Windows.Controls.ScrollBarVisibility.Disabled>, <xref:System.Windows.Controls.ScrollBarVisibility.Hidden> ou <xref:System.Windows.Controls.ScrollBarVisibility.Visible>.  
  
 La valeur <xref:System.Windows.Controls.ScrollBarVisibility.Auto> est prévue dans le cas où l’espace est limité et que les barres de défilement doivent être affichées uniquement si nécessaire. Par exemple, il peut être utile d’utiliser cette valeur <xref:System.Windows.Controls.ScrollBarVisibility> avec un <xref:System.Windows.Controls.ListBox> de 30 éléments, par opposition à un <xref:System.Windows.Controls.TextBox> contenant des centaines de lignes de texte.  
  
<a name="FontCache"></a>   
## <a name="configure-font-cache-service-to-reduce-start-up-time"></a>Configurer le service de mise en cache de polices pour réduire le temps de démarrage  
 Le service de mise en cache de polices [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] partage les données de police entre les applications [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. La première application [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] que vous exécutez démarre ce service s’il n’est pas déjà en cours d’exécution. Si vous utilisez Windows Vista, vous pouvez définir le service « Windows Presentation Foundation (WPF) de cache de police 3.0.0.0 » à partir de « manuel » (par défaut) sur « automatique (début différé) » pour réduire le temps de démarrage initial des applications [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].  
  
## <a name="see-also"></a>Voir aussi

- [Planification des performances des applications](planning-for-application-performance.md)
- [Tirer parti du matériel](optimizing-performance-taking-advantage-of-hardware.md)
- [Disposition et conception](optimizing-performance-layout-and-design.md)
- [Graphiques 2D et acquisition d'images](optimizing-performance-2d-graphics-and-imaging.md)
- [Comportement de l’objet](optimizing-performance-object-behavior.md)
- [Ressources d'application](optimizing-performance-application-resources.md)
- [Texte](optimizing-performance-text.md)
- [Liaison de données](optimizing-performance-data-binding.md)
- [Conseils et astuces sur les animations](../graphics-multimedia/animation-tips-and-tricks.md)
