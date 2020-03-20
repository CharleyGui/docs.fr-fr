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
ms.openlocfilehash: 727331adb41251460209f157d1804ff455bcf473
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186303"
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
 Lorsque vous <xref:System.Windows.Media.Brush> utilisez un <xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Shapes.Shape.Stroke%2A> pour définir le ou d’un élément, il est préférable de définir la <xref:System.Windows.Media.Brush.Opacity%2A?displayProperty=nameWithType> valeur plutôt que le réglage de la propriété de <xref:System.Windows.UIElement.Opacity%2A> l’élément. La modification de <xref:System.Windows.UIElement.Opacity%2A> la propriété [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] d’un élément peut entraîner la création d’une surface temporaire.  
  
<a name="Navigation_Objects"></a>
## <a name="navigation-to-object"></a>Navigation vers un objet  
 L’objet <xref:System.Windows.Navigation.NavigationWindow> dérive <xref:System.Windows.Window> et l’étend avec le support de <xref:System.Windows.Navigation.NavigationService> navigation de contenu, principalement en agrégeant et le journal. Vous pouvez mettre à <xref:System.Windows.Navigation.NavigationWindow> jour la zone client en spécifiant soit un identifiant de ressource uniforme (URI) ou un objet. L'exemple suivant illustre les deux méthodes :  
  
 [!code-csharp[Performance#PerformanceSnippet14](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/TestNavigation.xaml.cs#performancesnippet14)]
 [!code-vb[Performance#PerformanceSnippet14](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/testnavigation.xaml.vb#performancesnippet14)]  
  
 Chaque <xref:System.Windows.Navigation.NavigationWindow> objet dispose d’un journal qui enregistre l’historique de navigation de l’utilisateur dans cette fenêtre. Un des objectifs du journal est de permettre aux utilisateurs de retracer leurs étapes.  
  
 Lorsque vous naviguez à l’aide d’un identifiant de ressource uniforme (URI), le journal ne stocke que la référence uniforme d’identifiant de ressource (URI). Cela signifie que chaque fois que vous revisitez la page, elle est reconstruite dynamiquement, ce qui peut prendre beaucoup de temps selon la complexité de la page. Dans ce cas, le coût de stockage du journal est faible, mais le temps de reconstitution de la page est élevé.  
  
 Quand vous naviguez à l’aide d’un objet, le journal stocke intégralement l’arborescence de visuels de l’objet. Cela signifie que chaque fois que vous visitez la page, elle s’affiche immédiatement sans avoir à être reconstruite. Dans ce cas, le coût de stockage du journal est élevé, mais le temps de reconstitution de la page est faible.  
  
 Lorsque vous <xref:System.Windows.Navigation.NavigationWindow> utilisez l’objet, vous devez garder à l’esprit l’impact du support de journalisation sur les performances de votre application. Pour plus d’informations, voir [Aperçu de la navigation](../app-development/navigation-overview.md).  
  
<a name="Hit_Testing"></a>
## <a name="hit-testing-on-large-3d-surfaces"></a>Test de positionnement sur les grandes surfaces 3D  
 Le test de positionnement sur les grandes surfaces 3D est une opération qui affecte considérablement les performances en utilisant une grande part du processeur. Cela est particulièrement vrai quand la surface 3D est animée. Si vous n’avez pas besoin de tester le positionnement sur ces surfaces, désactivez le test de positionnement. Les objets dérivés peuvent <xref:System.Windows.UIElement> désactiver les <xref:System.Windows.UIElement.IsHitTestVisible%2A> essais `false`de frappe en définissant la propriété à .  
  
<a name="CompositionTarget_Rendering_Event"></a>
## <a name="compositiontargetrendering-event"></a>Événement CompositionTarget.Rendering  
 <xref:System.Windows.Media.CompositionTarget.Rendering?displayProperty=nameWithType> L’événement [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] provoque l’animation continue. Si vous utilisez cet événement, détacher-le dès que possible.  
  
<a name="Avoid_Using_ScrollBarVisibility"></a>
## <a name="avoid-using-scrollbarvisibilityauto"></a>Éviter l’utilisation de ScrollBarVisibility=Auto  
 Dans la mesure <xref:System.Windows.Controls.ScrollBarVisibility.Auto?displayProperty=nameWithType> du possible, `VerticalScrollBarVisibility` évitez d’utiliser la valeur et les `HorizontalScrollBarVisibility` propriétés. Ces propriétés <xref:System.Windows.Controls.RichTextBox>sont <xref:System.Windows.Controls.ScrollViewer>définies pour, et les <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.ListBox> objets, et comme une propriété attachée pour l’objet. Au lieu <xref:System.Windows.Controls.ScrollBarVisibility> <xref:System.Windows.Controls.ScrollBarVisibility.Disabled>de <xref:System.Windows.Controls.ScrollBarVisibility.Hidden>cela, réglé à , , ou <xref:System.Windows.Controls.ScrollBarVisibility.Visible>.  
  
 La <xref:System.Windows.Controls.ScrollBarVisibility.Auto> valeur est destinée aux cas où l’espace est limité et que les barres de défilement ne doivent être affichées que si nécessaire. Par exemple, il peut être <xref:System.Windows.Controls.ScrollBarVisibility> utile <xref:System.Windows.Controls.ListBox> d’utiliser cette valeur avec <xref:System.Windows.Controls.TextBox> un de 30 éléments par opposition à un avec des centaines de lignes de texte.  
  
<a name="FontCache"></a>
## <a name="configure-font-cache-service-to-reduce-start-up-time"></a>Configurer le service de mise en cache de polices pour réduire le temps de démarrage  
 Le service WPF Font Cache partage des données de police entre les applications WPF. La première application WPF que vous exécutez démarre ce service si le service n’est pas déjà en cours d’exécution. Si vous utilisez Windows Vista, vous pouvez définir le service "Windows Presentation Foundation (WPF) Font Cache 3.0.0.0" de "Manuel" (par défaut) à "Automatic (Delayed Start)" pour réduire le temps de démarrage initial des applications WPF.  
  
## <a name="see-also"></a>Voir aussi

- [Planification des performances des applications](planning-for-application-performance.md)
- [Tirer parti du matériel](optimizing-performance-taking-advantage-of-hardware.md)
- [Disposition et conception](optimizing-performance-layout-and-design.md)
- [Graphisme 2D et acquisition d’images](optimizing-performance-2d-graphics-and-imaging.md)
- [Comportement de l’objet](optimizing-performance-object-behavior.md)
- [Ressources d’application](optimizing-performance-application-resources.md)
- [Texte](optimizing-performance-text.md)
- [Liaison de données](optimizing-performance-data-binding.md)
- [Conseils et astuces sur les animations](../graphics-multimedia/animation-tips-and-tricks.md)
