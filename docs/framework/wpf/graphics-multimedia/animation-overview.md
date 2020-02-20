---
title: Vue d'ensemble de l'animation
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Storyboards [WPF], animations
- animations [WPF], overview
ms.assetid: bd9ce563-725d-4385-87c9-d7ee38cf79ea
ms.openlocfilehash: 00f01b63cdf9397fe25f28fff08767dfc3a83e69
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77453115"
---
# <a name="animation-overview"></a>Vue d'ensemble de l'animation

<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fournit un ensemble puissant de fonctionnalités graphiques et de mise en page qui vous permettent de créer des interfaces utilisateur attrayantes et des documents attrayants. L’animation peut rendre une interface utilisateur attrayante encore plus spectaculaire et conviviale. En animant simplement une couleur d’arrière-plan ou en appliquant un <xref:System.Windows.Media.Transform>animé, vous pouvez créer des transitions d’écran spectaculaires ou fournir des signaux visuels utiles.

Cette vue d’ensemble fournit une introduction au système d’animation et de minutage de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Elle se concentre sur l’animation des objets [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] à l’aide de storyboards.

<a name="introducinganimations"></a>

## <a name="introducing-animations"></a>Présentation des animations

L’animation est une illusion créée en parcourant rapidement une série d’images, chacune légèrement différente de la précédente. Le cerveau perçoit le groupe d’images comme une seule scène qui change. Dans un film, cette illusion est créée à l’aide de caméras qui enregistrent plusieurs photos, ou frames, chaque seconde. Lorsque les images sont lues par un projecteur, le public voit une image en mouvement.

L’animation sur un ordinateur est similaire. Par exemple, un programme qui dessine un rectangle disparaissant en fondu peut fonctionner comme suit.

- Le programme crée une minuterie.

- Le programme vérifie la minuterie à intervalles définis pour voir combien de temps s’est écoulé.

- Chaque fois que le programme vérifie la minuterie, il calcule la valeur actuelle d’opacité du rectangle selon le temps écoulé.

- Ensuite, le programme met à jour le rectangle avec la nouvelle valeur et le redessine.

Avant de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], les développeurs Microsoft Windows devaient créer et gérer leurs propres systèmes de synchronisation ou utiliser des bibliothèques personnalisées spéciales. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] comprend un système de minutage efficace qui est exposé via du code managé et [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] et qui est profondément intégré à l’infrastructure [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. L’animation [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] facilite l’animation de contrôles et autres objets graphiques.

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] gère toutes les tâches en arrière-plan pour gérer un système de minutage et redessiner l’écran efficacement. Il fournit les classes de minuterie qui vous permettent de vous concentrer sur les effets que vous souhaitez créer, au lieu de la mécanique de la réalisation de ces effets. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] facilite également la création de vos propres animations en exposant les classes de base d’animation à partir desquelles vos classes peuvent hériter, pour produire des animations personnalisées. Ces animations personnalisées récupèrent nombre des avantages de performance des classes d’animation standard.

<a name="thewpftimingsystem"></a>

## <a name="wpf-property-animation-system"></a>Système d’animation de propriétés WPF

Si vous comprenez quelques concepts importants sur le système de minutage, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animations peuvent être plus faciles à utiliser. La plus importante est que, dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], vous animez des objets en appliquant une animation à leurs propriétés individuelles. Par exemple, pour augmenter la taille d’un élément d’infrastructure, vous animez ses propriétés <xref:System.Windows.FrameworkElement.Width%2A> et <xref:System.Windows.FrameworkElement.Height%2A>. Pour faire disparaître un objet de la vue, vous animez sa propriété <xref:System.Windows.UIElement.Opacity%2A>.

Pour qu’une propriété dispose de fonctionnalités d’animation, elle doit respecter les trois conditions suivantes :

- Il doit s’agir d’une propriété de dépendance.

- Elle doit appartenir à une classe qui hérite de <xref:System.Windows.DependencyObject> et implémente l’interface <xref:System.Windows.Media.Animation.IAnimatable>.

- Un type d’animation compatible doit être disponible. (Si [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] n’en fournit pas, vous pouvez créer votre propre. Consultez [vue d’ensemble des animations personnalisées](custom-animations-overview.md).)

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] contient de nombreux objets qui ont des propriétés de <xref:System.Windows.Media.Animation.IAnimatable>. Les contrôles tels que <xref:System.Windows.Controls.Button> et <xref:System.Windows.Controls.TabControl>, ainsi que les objets <xref:System.Windows.Controls.Panel> et <xref:System.Windows.Shapes.Shape> héritent de <xref:System.Windows.DependencyObject>. La plupart de leurs propriétés sont des propriétés de dépendance.

Vous pouvez utiliser des animations presque n’importe où, y compris dans les styles et modèles de contrôle. Les animations n’ont pas à être visuelles. Vous pouvez animer des objets qui ne font pas partie de l’interface utilisateur s’ils répondent aux critères décrits dans cette section.

<a name="storyboardwalkthrough"></a>

## <a name="example-make-an-element-fade-in-and-out-of-view"></a>Exemple : Création d’un fondu hors de l’affichage pour un élément

Cet exemple montre comment utiliser une animation [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pour animer la valeur d’une propriété de dépendance. Elle utilise un <xref:System.Windows.Media.Animation.DoubleAnimation>, qui est un type d’animation qui génère <xref:System.Double> valeurs, pour animer la propriété <xref:System.Windows.UIElement.Opacity%2A> d’un <xref:System.Windows.Shapes.Rectangle>. Par conséquent, le <xref:System.Windows.Shapes.Rectangle> apparaît et disparaît en fondu.

La première partie de l’exemple crée un élément <xref:System.Windows.Shapes.Rectangle>. Les étapes suivantes montrent comment créer une animation et l’appliquer à la propriété <xref:System.Windows.UIElement.Opacity%2A> du rectangle.

L’exemple suivant montre comment créer un élément <xref:System.Windows.Shapes.Rectangle> dans un <xref:System.Windows.Controls.StackPanel> en XAML.

[!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_1](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_1)]

L’exemple suivant montre comment créer un élément <xref:System.Windows.Shapes.Rectangle> dans un <xref:System.Windows.Controls.StackPanel> dans du code.

[!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_1](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Class1.cs#rectangleopacityfadeexamplecode_1)]
[!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/Class1.vb#rectangleopacityfadeexamplecode_1)]

<a name="opacity_animation_step1"></a>

### <a name="part-1-create-a-doubleanimation"></a>Partie 1 : Création d’un objet DoubleAnimation

L’une des façons de faire apparaître et disparaître un élément consiste à animer sa propriété <xref:System.Windows.UIElement.Opacity%2A>. Étant donné que la propriété <xref:System.Windows.UIElement.Opacity%2A> est de type <xref:System.Double>, vous avez besoin d’une animation qui produit des valeurs double. Une <xref:System.Windows.Media.Animation.DoubleAnimation> est une animation de ce type. Une <xref:System.Windows.Media.Animation.DoubleAnimation> crée une transition entre deux valeurs double. Pour spécifier sa valeur de départ, vous devez définir sa propriété <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>. Pour spécifier sa valeur de fin, vous devez définir sa propriété <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>.

1. Une valeur d’opacité de `1.0` rend l’objet complètement opaque et une valeur d’opacité de `0.0` le rend complètement invisible. Pour que l’animation passe de `1.0` à `0.0` vous définissez sa propriété <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> sur `1.0` et sa propriété <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> sur `0.0`. L’exemple suivant montre comment créer un <xref:System.Windows.Media.Animation.DoubleAnimation> en XAML.

    [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_2](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_2)]

    L’exemple suivant montre comment créer un <xref:System.Windows.Media.Animation.DoubleAnimation> dans le code.

    [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_2](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Class1.cs#rectangleopacityfadeexamplecode_2)]
    [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/Class1.vb#rectangleopacityfadeexamplecode_2)]

2. Ensuite, vous devez spécifier un <xref:System.Windows.Media.Animation.Timeline.Duration%2A>. La <xref:System.Windows.Media.Animation.Timeline.Duration%2A> d’une animation spécifie le temps nécessaire pour passer de sa valeur de départ à sa valeur de destination. L’exemple suivant montre comment définir le <xref:System.Windows.Media.Animation.Timeline.Duration%2A> à cinq secondes en XAML.

    [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_3](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_3)]

    L’exemple suivant montre comment définir le <xref:System.Windows.Media.Animation.Timeline.Duration%2A> à cinq secondes dans le code.

    [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_3](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Class1.cs#rectangleopacityfadeexamplecode_3)]
    [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/Class1.vb#rectangleopacityfadeexamplecode_3)]

3. Le code précédent affichait une animation qui passe de `1.0` à `0.0`, ce qui a pour effet que l’élément cible passe de complètement opaque à complètement invisible. Pour que l’élément repasse en affichage une fois qu’il a disparu, définissez la propriété <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> de l’animation sur `true`. Pour que l’animation se répète indéfiniment, définissez sa propriété <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> sur <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>. L’exemple suivant montre comment définir les propriétés <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> et <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> en XAML.

    [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_4](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_4)]

    L’exemple suivant montre comment définir les propriétés <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> et <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> dans le code.

    [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_4](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Class1.cs#rectangleopacityfadeexamplecode_4)]
    [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/Class1.vb#rectangleopacityfadeexamplecode_4)]

<a name="opacity_animation_step2"></a>

### <a name="part-2-create-a-storyboard"></a>Partie 2 : Création d’un storyboard

Pour appliquer une animation à un objet, vous créez une <xref:System.Windows.Media.Animation.Storyboard> et utilisez les propriétés jointes <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> et <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> pour spécifier l’objet et la propriété à animer.

1. Créez le <xref:System.Windows.Media.Animation.Storyboard> et ajoutez l’animation en tant qu’enfant. L’exemple suivant montre comment créer le <xref:System.Windows.Media.Animation.Storyboard> en XAML.

    [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_5](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_5)]

    Pour créer l' <xref:System.Windows.Media.Animation.Storyboard> dans le code, déclarez une variable <xref:System.Windows.Media.Animation.Storyboard> au niveau de la classe.

    [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_100](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_100)]
    [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_100)]

    Ensuite, initialisez le <xref:System.Windows.Media.Animation.Storyboard> et ajoutez l’animation en tant qu’enfant.

    [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_101](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_101)]
    [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_101)]

2. Le <xref:System.Windows.Media.Animation.Storyboard> doit savoir où appliquer l’animation. Utilisez la propriété jointe <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A?displayProperty=nameWithType> pour spécifier l’objet à animer. L’exemple suivant montre comment définir le nom cible du <xref:System.Windows.Media.Animation.DoubleAnimation> à `MyRectangle` en XAML.

    [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_6](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_6)]

    L’exemple suivant montre comment définir le nom cible du <xref:System.Windows.Media.Animation.DoubleAnimation> à `MyRectangle` dans le code.

    [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_102](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_102)]
    [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_102)]

3. Utilisez la propriété jointe <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> pour spécifier la propriété à animer. L’exemple suivant montre comment l’animation est configurée pour cibler la propriété <xref:System.Windows.UIElement.Opacity%2A> du <xref:System.Windows.Shapes.Rectangle> en XAML.

    [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_7](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_7)]

    L’exemple suivant montre comment l’animation est configurée pour cibler la propriété <xref:System.Windows.UIElement.Opacity%2A> du <xref:System.Windows.Shapes.Rectangle> dans le code.

    [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_103](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_103)]
    [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_103)]

Pour plus d’informations sur la syntaxe de <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> et pour obtenir des exemples supplémentaires, consultez [vue d’ensemble des storyboards](storyboards-overview.md).

<a name="opacity_animation_step3"></a>

### <a name="part-3-xaml-associate-the-storyboard-with-a-trigger"></a>Partie 3 (XAML) : Association du storyboard à un déclencheur

Le moyen le plus simple d’appliquer et de démarrer un <xref:System.Windows.Media.Animation.Storyboard> dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] consiste à utiliser un déclencheur d’événement. Cette section montre comment associer l' <xref:System.Windows.Media.Animation.Storyboard> à un déclencheur en XAML.

1. Créez un objet <xref:System.Windows.Media.Animation.BeginStoryboard> et associez-le à votre table de montage séquentiel. Un <xref:System.Windows.Media.Animation.BeginStoryboard> est un type de <xref:System.Windows.TriggerAction> qui applique et démarre un <xref:System.Windows.Media.Animation.Storyboard>.

    [!code-xaml[animation_ovws_snippet#RectangleOpacityFadeExampleInline_3](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/RectangleOpacityFadeExample.xaml#rectangleopacityfadeexampleinline_3)]

2. Créez un <xref:System.Windows.EventTrigger> et ajoutez le <xref:System.Windows.Media.Animation.BeginStoryboard> à sa collection de <xref:System.Windows.EventTrigger.Actions%2A>. Affectez à la propriété <xref:System.Windows.EventTrigger.RoutedEvent%2A> du <xref:System.Windows.EventTrigger> l’événement routé pour lequel vous souhaitez démarrer le <xref:System.Windows.Media.Animation.Storyboard>. (Pour plus d’informations sur les événements routés, consultez [vue d’ensemble des événements routés](../advanced/routed-events-overview.md).)

    [!code-xaml[animation_ovws_snippet#RectangleOpacityFadeExampleInline_2](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/RectangleOpacityFadeExample.xaml#rectangleopacityfadeexampleinline_2)]

3. Ajoutez le <xref:System.Windows.EventTrigger> à la collection de <xref:System.Windows.FrameworkElement.Triggers%2A> du rectangle.

    [!code-xaml[animation_ovws_snippet#RectangleOpacityFadeExampleInline_1](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/RectangleOpacityFadeExample.xaml#rectangleopacityfadeexampleinline_1)]

<a name="opacity_animation_step3code"></a>

### <a name="part-3-code-associate-the-storyboard-with-an-event-handler"></a>Partie 3 (Code) : Association du storyboard à un gestionnaire d’événements

Le moyen le plus simple d’appliquer et de démarrer un <xref:System.Windows.Media.Animation.Storyboard> dans le code consiste à utiliser un gestionnaire d’événements. Cette section montre comment associer l' <xref:System.Windows.Media.Animation.Storyboard> à un gestionnaire d’événements dans le code.

1. Inscrivez-vous pour l’événement <xref:System.Windows.FrameworkElement.Loaded> du rectangle.

    [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_104](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_104)]
    [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_104)]

2. Déclarez le gestionnaire d'événements. Dans le gestionnaire d’événements, utilisez la méthode <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> pour appliquer le Storyboard.

    [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_105](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_105)]
    [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_105](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_105)]

### <a name="complete-example"></a>Exemple complet

L’exemple suivant montre comment créer un rectangle qui apparaît en fondu dans et hors de l’affichage en XAML.

[!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml#rectangleopacityfadeexamplexaml)]

L’exemple suivant montre comment créer un rectangle avec un fondu dans et hors de l’affichage avec du code.

[!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode)]
[!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode)]

<a name="animationtypes"></a>

## <a name="animation-types"></a>Types d’animation

Étant donné que les animations génèrent des valeurs de propriété, différents types d’animation existent pour différents types de propriété. Pour animer une propriété qui prend une <xref:System.Double>, telle que la propriété <xref:System.Windows.FrameworkElement.Width%2A> d’un élément, utilisez une animation qui produit des valeurs de <xref:System.Double>. Pour animer une propriété qui prend un <xref:System.Windows.Point>, utilisez une animation qui produit des valeurs de <xref:System.Windows.Point>, et ainsi de suite. En raison du nombre de différents types de propriété, il existe plusieurs classes d’animation dans l’espace de noms <xref:System.Windows.Media.Animation>. Heureusement, ils suivent une convention d’appellation stricte qui facilite la différenciation :

- \<*Type*> Animation

  Appelées animations « From/To/By » ou « de base », elles animent entre une valeur de début et de destination, ou en ajoutant une valeur de décalage à la valeur initiale.

  - Pour spécifier une valeur de départ, définissez la propriété From de l’animation.

  - Pour spécifier une valeur finale, définissez la propriété To de l’animation.

  - Pour spécifier une valeur de décalage, définissez la propriété By de l’animation.

  Les exemples de cette vue d’ensemble utilisent ces animations, car elles sont plus simples à utiliser. Les animations from/to/by sont décrites en détail dans la vue d’ensemble des animations from/to/by.

- \<*Type*>AnimationUsingKeyFrames

  Les animations d’image clé sont plus puissantes que les animations From/To/By, car vous pouvez spécifier n’importe quel nombre de valeurs cibles et même contrôler leur méthode d’interpolation. Certains types ne peuvent être animés qu’avec des animations d’image clé. Les animations d’image clé sont décrites en détail dans la [vue d’ensemble des animations d’image clé](key-frame-animations-overview.md).

- \<*Type*>AnimationUsingPath

  Les animations de tracés permettent d’utiliser un tracé géométrique pour produire des valeurs animées.

- \<*Type*>AnimationBase

  Une classe abstraite qui, lorsque vous l’implémentez, anime un \<*Type*> value. Cette classe sert de classe de base pour les classes \<*Type*> Animation et \<*Type*> AnimationUsingKeyFrames. Vous devez vous charger directement de ces classes uniquement si vous souhaitez créer vos propres animations personnalisées. Sinon, utilisez une \<*Type*> Animation ou KeyFrame\<*Type*> Animation.

Dans la plupart des cas, vous pouvez utiliser le *type*de \<> des classes d’animation, telles que <xref:System.Windows.Media.Animation.DoubleAnimation> et <xref:System.Windows.Media.Animation.ColorAnimation>.

Le tableau suivant montre plusieurs types d’animations courants et certaines propriétés avec lesquelles ils sont utilisés.

|Type de propriété|Animation de base (From/To/By) correspondante|Animation d’image clé correspondante|Animation de tracé correspondante|Exemple d’utilisation|
|-------------------|----------------------------------------------------|---------------------------------------|----------------------------------|-------------------|
|<xref:System.Windows.Media.Color>|<xref:System.Windows.Media.Animation.ColorAnimation>|<xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames>|None|Animer le <xref:System.Windows.Media.SolidColorBrush.Color%2A> d’un <xref:System.Windows.Media.SolidColorBrush> ou d’un <xref:System.Windows.Media.GradientStop>.|
|<xref:System.Double>|<xref:System.Windows.Media.Animation.DoubleAnimation>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>|Animer le <xref:System.Windows.FrameworkElement.Width%2A> d’un <xref:System.Windows.Controls.DockPanel> ou de la <xref:System.Windows.FrameworkElement.Height%2A> d’un <xref:System.Windows.Controls.Button>.|
|<xref:System.Windows.Point>|<xref:System.Windows.Media.Animation.PointAnimation>|<xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>|<xref:System.Windows.Media.Animation.PointAnimationUsingPath>|Animer la position de <xref:System.Windows.Media.EllipseGeometry.Center%2A> d’un <xref:System.Windows.Media.EllipseGeometry>.|
|<xref:System.String>|None|<xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames>|None|Animer le <xref:System.Windows.Controls.TextBlock.Text%2A> d’un <xref:System.Windows.Controls.TextBlock> ou de la <xref:System.Windows.Controls.ContentControl.Content%2A> d’un <xref:System.Windows.Controls.Button>.|

<a name="animationsaretimelines"></a>

### <a name="animations-are-timelines"></a>Les animations sont des chronologies

Tous les types d’animation héritent de la classe <xref:System.Windows.Media.Animation.Timeline> ; par conséquent, toutes les animations sont des types de chronologies spécialisés. Un <xref:System.Windows.Media.Animation.Timeline> définit un segment de temps. Vous pouvez spécifier les *comportements de minutage* d’une chronologie : son <xref:System.Windows.Media.Animation.Timeline.Duration%2A>, le nombre de fois où il est répété, et même la vitesse à laquelle le temps rapide progresse.

Étant donné qu’une animation est un <xref:System.Windows.Media.Animation.Timeline>, elle représente également un segment de temps. Une animation calcule également les valeurs de sortie à mesure qu’elle progresse dans le segment de temps spécifié (ou <xref:System.Windows.Media.Animation.Timeline.Duration%2A>). Lorsque l’animation progresse, ou est « lue », elle met à jour la propriété qui lui est associée.

Trois propriétés de minutage fréquemment utilisées sont <xref:System.Windows.Media.Animation.Timeline.Duration%2A>, <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>et <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>.

#### <a name="the-duration-property"></a>La propriété Duration

Comme mentionné plus haut, une chronologie représente un segment de temps. La longueur de ce segment est déterminée par la <xref:System.Windows.Media.Animation.Timeline.Duration%2A> de la chronologie, qui est généralement spécifiée à l’aide d’une valeur de <xref:System.Windows.Duration.TimeSpan%2A>. Lorsqu’une chronologie atteint la fin de sa durée, elle a terminé une itération.

Une animation utilise sa propriété <xref:System.Windows.Media.Animation.Timeline.Duration%2A> pour déterminer sa valeur actuelle. Si vous ne spécifiez pas de valeur <xref:System.Windows.Media.Animation.Timeline.Duration%2A> pour une animation, elle utilise 1 seconde, qui est la valeur par défaut.

La syntaxe suivante montre une version simplifiée de la syntaxe d’attribut [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pour la propriété <xref:System.Windows.Media.Animation.Timeline.Duration%2A>.

*heures* `:` *minutes* `:` *secondes*

Le tableau suivant présente plusieurs paramètres de <xref:System.Windows.Duration> et leurs valeurs résultantes.

|Paramètre|Valeur correspondante|
|-------------|---------------------|
|0:0:5.5|5,5 secondes.|
|0:30:5.5|30 minutes et 5,5 secondes.|
|1:30:5.5|1 heure, 30 minutes, et 5,5 secondes.|

L’une des manières de spécifier un <xref:System.Windows.Duration> dans le code consiste à utiliser la méthode <xref:System.TimeSpan.FromSeconds%2A> pour créer un <xref:System.TimeSpan>, puis à déclarer une nouvelle structure <xref:System.Windows.Duration> à l’aide de cette <xref:System.TimeSpan>.

Pour plus d’informations sur les valeurs de <xref:System.Windows.Duration> et la syntaxe de [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] complète, consultez la structure <xref:System.Windows.Duration>.

#### <a name="autoreverse"></a>AutoReverse

La propriété <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> spécifie si une chronologie est lue en arrière après avoir atteint la fin de son <xref:System.Windows.Media.Animation.Timeline.Duration%2A>. Si vous définissez cette propriété d’animation sur `true`, une animation est inversée après avoir atteint la fin de son <xref:System.Windows.Media.Animation.Timeline.Duration%2A>, ce qui revient de sa valeur finale à sa valeur de départ. Par défaut, cette propriété est `false`.

#### <a name="repeatbehavior"></a>RepeatBehavior

La propriété <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> spécifie le nombre de fois qu’une chronologie est lue. Par défaut, les chronologies ont un nombre d’itérations de `1.0`, ce qui signifie qu’elles s’exécutent une seule fois et ne se répètent pas du tout.

Pour plus d’informations sur ces propriétés et d’autres, consultez la [vue d’ensemble des comportements de minutage](timing-behaviors-overview.md).

<a name="applyanimationstoproperty"></a>

## <a name="applying-an-animation-to-a-property"></a>Application d’une animation à une propriété

Les sections précédentes décrivent les différents types d’animations et leurs propriétés de minuterie. Cette section montre comment appliquer l’animation à la propriété que vous souhaitez animer. les objets <xref:System.Windows.Media.Animation.Storyboard> offrent un moyen d’appliquer des animations aux propriétés. Un <xref:System.Windows.Media.Animation.Storyboard> est une *chronologie de conteneur* qui fournit des informations de ciblage pour les animations qu’il contient.

### <a name="targeting-objects-and-properties"></a>Ciblage des objets et propriétés

La classe <xref:System.Windows.Media.Animation.Storyboard> fournit les propriétés jointes <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> et <xref:System.Windows.Media.Animation.Storyboard.TargetProperty>. En définissant ces propriétés sur une animation, vous dites à l’animation ce qu’elle doit animer. Toutefois, avant qu’une animation puisse cibler un objet, l’objet doit généralement obtenir un nom.

L’attribution d’un nom à un <xref:System.Windows.FrameworkElement> diffère de l’attribution d’un nom à un objet <xref:System.Windows.Freezable>. La plupart des contrôles et panneaux sont des éléments de framework. Toutefois, les objets purement graphiques, comme les pinceaux, les transformations et les géométries, sont des objets Freezable. Si vous ne savez pas si un type est un <xref:System.Windows.FrameworkElement> ou un <xref:System.Windows.Freezable>, reportez-vous à la section **hiérarchie d’héritage** de sa documentation de référence.

- Pour créer un <xref:System.Windows.FrameworkElement> une cible d’animation, vous lui donnez un nom en définissant sa propriété <xref:System.Windows.FrameworkElement.Name%2A>. Dans le code, vous devez également utiliser la méthode <xref:System.Windows.FrameworkElement.RegisterName%2A> pour inscrire le nom de l’élément avec la page à laquelle il appartient.

- Pour faire d’un objet <xref:System.Windows.Freezable> une cible d’animation dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], vous utilisez la [directive x :Name](../../../desktop-wpf/xaml-services/xname-directive.md) pour lui assigner un nom. Dans le code, vous utilisez simplement la méthode <xref:System.Windows.FrameworkElement.RegisterName%2A> pour inscrire l’objet avec la page à laquelle il appartient.

Les sections suivantes fournissent un exemple de dénomination d’un élément dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] et du code. Pour plus d’informations sur l’affectation de noms et le ciblage, consultez [vue d’ensemble des storyboards](storyboards-overview.md).

### <a name="applying-and-starting-storyboards"></a>Application et démarrage des storyboards

Pour démarrer une table de montage séquentiel dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], vous l’associez à une <xref:System.Windows.EventTrigger>. Un <xref:System.Windows.EventTrigger> est un objet qui décrit les actions à effectuer lorsqu’un événement spécifié se produit. L’une de ces actions peut être une action <xref:System.Windows.Media.Animation.BeginStoryboard>, que vous utilisez pour démarrer votre table de montage séquentiel. Les déclencheurs d’événements sont un concept similaire aux gestionnaires d’événements, car ils vous permettent de spécifier la façon dont votre application répond à un événement particulier. Contrairement aux gestionnaires d’événements, les déclencheurs d’événements peuvent être décrits en détail dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]; aucun autre code n’est requis.

Pour démarrer un <xref:System.Windows.Media.Animation.Storyboard> dans le code, vous pouvez utiliser une <xref:System.Windows.EventTrigger> ou utiliser la méthode <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> de la classe <xref:System.Windows.Media.Animation.Storyboard>.

<a name="controllingstoryboards"></a>

## <a name="interactively-control-a-storyboard"></a>Contrôler un storyboard de façon interactive

L’exemple précédent a montré comment démarrer un <xref:System.Windows.Media.Animation.Storyboard> lorsqu’un événement se produit. Vous pouvez également contrôler de manière interactive un <xref:System.Windows.Media.Animation.Storyboard> après son démarrage : vous pouvez suspendre, reprendre, arrêter, l’avancer jusqu’à sa période de remplissage, Rechercher et supprimer le <xref:System.Windows.Media.Animation.Storyboard>. Pour plus d’informations et pour obtenir un exemple qui montre comment contrôler de manière interactive une <xref:System.Windows.Media.Animation.Storyboard>, consultez [vue d’ensemble des storyboards](storyboards-overview.md).

<a name="fillbehaviorsection"></a>

## <a name="what-happens-after-an-animation-ends"></a>Que se passe-t-il après la fin d’une animation ?

La propriété <xref:System.Windows.Media.Animation.FillBehavior> spécifie le comportement d’une chronologie lorsqu’elle se termine. Par défaut, une chronologie démarre <xref:System.Windows.Media.Animation.ClockState.Filling> lorsqu’elle se termine. Une animation qui est <xref:System.Windows.Media.Animation.ClockState.Filling> contient sa valeur de sortie finale.

La <xref:System.Windows.Media.Animation.DoubleAnimation> dans l’exemple précédent ne se termine pas, car sa propriété <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> est définie sur <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>. L’exemple suivant anime un rectangle avec une animation semblable. Contrairement à l’exemple précédent, les propriétés <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> et <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> de cette animation sont laissées à leurs valeurs par défaut. Par conséquent, l’animation passe de 1 à 0 en cinq secondes et s’arrête.

[!code-xaml[animation_ovws_snippet#FillBehaviorExampleRectangleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/FillBehaviorExample.xaml#fillbehaviorexamplerectangleinline)]

[!code-csharp[animation_ovws_procedural_snip#FillBehaviorExampleRectangleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_procedural_snip/CSharp/FillBehaviorExample.cs#fillbehaviorexamplerectangleinline)]
[!code-vb[animation_ovws_procedural_snip#FillBehaviorExampleRectangleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws_procedural_snip/visualbasic/fillbehaviorexample.vb#fillbehaviorexamplerectangleinline)]

Étant donné que son <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> n’a pas été modifié par rapport à sa valeur par défaut, qui est <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>, l’animation conserve sa valeur finale, 0, lorsqu’elle se termine. Par conséquent, la <xref:System.Windows.UIElement.Opacity%2A> du rectangle reste à 0 après la fin de l’animation. Si vous définissez la <xref:System.Windows.UIElement.Opacity%2A> du rectangle sur une autre valeur, votre code semble n’avoir aucun effet, car l’animation affecte toujours la propriété <xref:System.Windows.UIElement.Opacity%2A>.

L’une des façons de reprendre le contrôle d’une propriété animée dans le code consiste à utiliser la méthode <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> et à spécifier null pour le paramètre <xref:System.Windows.Media.Animation.AnimationTimeline>. Pour plus d’informations et pour obtenir un exemple, consultez [définir une propriété après l’avoir animée avec un Storyboard](how-to-set-a-property-after-animating-it-with-a-storyboard.md).

Notez que, bien que la définition d’une valeur de propriété avec un <xref:System.Windows.Media.Animation.ClockState.Active> ou <xref:System.Windows.Media.Animation.ClockState.Filling> animation semble n’avoir aucun effet, la valeur de la propriété change. Pour plus d’informations, consultez [vue d’ensemble du système d’animation et de minutage](animation-and-timing-system-overview.md).

<a name="databindingAndAnimatingAnimationsSection"></a>

## <a name="data-binding-and-animating-animations"></a>Liaison de données et animation des animations

La plupart des propriétés d’animation peuvent être liées aux données ou animées ; par exemple, vous pouvez animer la propriété <xref:System.Windows.Media.Animation.Timeline.Duration%2A> d’un <xref:System.Windows.Media.Animation.DoubleAnimation>. Toutefois, en raison de la façon dont le système de minutage fonctionne, les données liées ou animations animées ne se comportent pas comme les autres données liées ou objets animés. Pour comprendre leur comportement, il est utile de comprendre ce que signifie l’application d’une animation à une propriété.

Reportez-vous à l’exemple de la section précédente qui a montré comment animer la <xref:System.Windows.UIElement.Opacity%2A> d’un rectangle. Lorsque le rectangle de l’exemple précédent est chargé, son déclencheur d’événements applique la <xref:System.Windows.Media.Animation.Storyboard>. Le système de minutage crée une copie du <xref:System.Windows.Media.Animation.Storyboard> et de son animation. Ces copies sont figées (en lecture seule) et <xref:System.Windows.Media.Animation.Clock> objets sont créés à partir de celles-ci. Ces horloges effectuent le travail réel de l’animation des propriétés ciblées.

Le système de minutage crée une horloge pour la <xref:System.Windows.Media.Animation.DoubleAnimation> et l’applique à l’objet et à la propriété spécifiés par le <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> et <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> du <xref:System.Windows.Media.Animation.DoubleAnimation>. Dans ce cas, le système de minutage applique l’horloge à la propriété <xref:System.Windows.UIElement.Opacity%2A> de l’objet nommé « MyRectangle ».

Bien qu’une horloge soit également créée pour le <xref:System.Windows.Media.Animation.Storyboard>, l’horloge n’est pas appliquée à toutes les propriétés. Son objectif est de contrôler son horloge enfant, l’horloge qui est créée pour le <xref:System.Windows.Media.Animation.DoubleAnimation>.

Pour qu’une animation reflète les modifications d’animation ou de liaison de données, son horloge doit être régénérée. Les horloges ne sont pas régénérées automatiquement pour vous. Pour qu’une animation reflète les modifications, réappliquez son Storyboard à l’aide d’une <xref:System.Windows.Media.Animation.BeginStoryboard> ou de la méthode <xref:System.Windows.Media.Animation.Storyboard.Begin%2A>. Lorsque vous utilisez une de ces méthodes, l’animation redémarre. Dans le code, vous pouvez utiliser la méthode <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> pour replacer le Storyboard à sa position précédente.

Pour obtenir un exemple d’animation liée aux données, consultez [exemple d’animation de spline clé](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/KeySplineAnimations). Pour plus d’informations sur le fonctionnement de l’animation et du système de minuterie, consultez [vue d’ensemble du système d’animation et de minutage](animation-and-timing-system-overview.md).

<a name="otherWaysToAnimateSection"></a>

## <a name="other-ways-to-animate"></a>Autres méthodes d’animation

Les exemples de cette vue d’ensemble montrent comment animer à l’aide de storyboards. Lorsque vous utilisez du code, vous pouvez animer de plusieurs autres façons. Pour plus d’informations, consultez la [vue d’ensemble des techniques d’animation de propriétés](property-animation-techniques-overview.md).

<a name="animation_samples"></a>

## <a name="animation-samples"></a>Exemples d’animation

Les exemples suivants peuvent vous aider à commencer à ajouter animation à vos applications.

- [Exemple de valeurs cibles d’animation From, To, and By Animation Target Values Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/TargetValues)

  Présente les différents paramètres From/To/By.

- [Animation Timing Behavior Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationTiming) (Exemple de comportement de minutage dans une animation)

  Montre les différentes façons, vous pouvez contrôler le comportement de minuterie d’une animation. Cet exemple également montre comment lier les données d’une valeur de destination d’animation.

<a name="related_topics"></a>

## <a name="related-topics"></a>Rubriques connexes

|Intitulé|Description|
|-----------|-----------------|
|[Vue d'ensemble de l'animation et du système de minutage](animation-and-timing-system-overview.md)|Décrit comment le système de minutage utilise les classes <xref:System.Windows.Media.Animation.Timeline> et <xref:System.Windows.Media.Animation.Clock>, qui vous permettent de créer des animations.|
|[Conseils et astuces sur les animations](animation-tips-and-tricks.md)|Répertorie des conseils utiles pour résoudre les problèmes d’animation, tels que les performances.|
|[Vue d'ensemble des animations personnalisées](custom-animations-overview.md)|Décrit comment étendre le système d’animation avec des images clés, des classes d’animation ou des rappels image par image.|
|[Vue d’ensemble des animations From/To/By](from-to-by-animations-overview.md)|Décrit comment créer une animation qui effectue la transition entre deux valeurs.|
|[Vue d'ensemble des animations d'image clé](key-frame-animations-overview.md)|Décrit comment créer une animation avec plusieurs valeurs cibles, notamment la possibilité de contrôler la méthode d’interpolation.|
|[Fonctions d'accélération](easing-functions.md)|Explique comment appliquer des formules mathématiques à vos animations pour obtenir un comportement réaliste, tel que rebondissement.|
|[Vue d'ensemble des animations de tracés](path-animations-overview.md)|Décrit comment déplacer ou faire pivoter un objet sur un tracé complexe.|
|[Vue d'ensemble des techniques d'animation de propriétés](property-animation-techniques-overview.md)|Décrit des animations de propriété à l’aide de storyboards, animations locales, horloges et des animations image par image.|
|[Vue d'ensemble des storyboards](storyboards-overview.md)|Décrit comment utiliser les storyboards avec plusieurs chronologies pour créer des animations complexes.|
|[Vue d’ensemble des comportements de minutage](timing-behaviors-overview.md)|Décrit les types de <xref:System.Windows.Media.Animation.Timeline> et les propriétés utilisés dans les animations.|
|[Vue d'ensemble des événements de minuterie](timing-events-overview.md)|Décrit les événements disponibles sur les objets <xref:System.Windows.Media.Animation.Timeline> et <xref:System.Windows.Media.Animation.Clock> pour exécuter du code à des points de la chronologie, tels que Begin, pause, Resume, Skip ou stop.|
|[Rubriques Comment](animation-and-timing-how-to-topics.md)|Contient des exemples de code pour l’utilisation des animations et des chronologies dans votre application.|
|[Guides pratiques relatifs aux objets Clock](clocks-how-to-topics.md)|Contient des exemples de code pour l’utilisation de l’objet <xref:System.Windows.Media.Animation.Clock> dans votre application.|
|[Guides pratiques relatifs aux images clés](key-frame-animation-how-to-topics.md)|Contient des exemples de code pour l’utilisation des animations d’image clé dans votre application.|
|[Guides pratiques relatifs aux animations de tracés](path-animation-how-to-topics.md)|Contient des exemples de code pour l’utilisation des animations de tracés dans votre application.|

<a name="reference"></a>

## <a name="reference"></a>Informations de référence

- <xref:System.Windows.Media.Animation.Timeline>

- <xref:System.Windows.Media.Animation.Storyboard>

- <xref:System.Windows.Media.Animation.BeginStoryboard>

- <xref:System.Windows.Media.Animation.Clock>
