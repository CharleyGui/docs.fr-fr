---
title: Vue d'ensemble des storyboards
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Storyboard syntax [WPF]
- syntax [WPF], Storyboard
- timelines [WPF]
ms.assetid: 1a698c3c-30f1-4b30-ae56-57e8a39811bd
ms.openlocfilehash: 5c058dbaf2ae209a198a8299790d4002447ac443
ms.sourcegitcommit: f8c36054eab877de4d40a705aacafa2552ce70e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/31/2019
ms.locfileid: "75559688"
---
# <a name="storyboards-overview"></a>Vue d'ensemble des storyboards

Cette rubrique montre comment utiliser des objets <xref:System.Windows.Media.Animation.Storyboard> pour organiser et appliquer des animations. Il décrit comment manipuler de manière interactive des objets <xref:System.Windows.Media.Animation.Storyboard> et décrit la syntaxe de ciblage de propriété indirecte.

## <a name="prerequisites"></a>Configuration requise

Pour comprendre cette rubrique, vous devez connaître les différents types d’animations et leurs fonctions de base. Pour une introduction à l’animation, consultez [Vue d’ensemble de l’animation](animation-overview.md). Vous devez également savoir comment utiliser les propriétés jointes. Pour plus d’informations sur les propriétés jointes, consultez [Vue d’ensemble des propriétés jointes](../advanced/attached-properties-overview.md).

<a name="whatisatimeline"></a>

## <a name="what-is-a-storyboard"></a>Qu’est-ce qu’une table de montage séquentiel ?

Les animations ne sont pas le seul type utile de chronologie. D’autres classes de chronologie sont fournies pour vous aider à organiser des jeux de chronologies et à appliquer des chronologies aux propriétés. Les chronologies de conteneur dérivent de la classe <xref:System.Windows.Media.Animation.TimelineGroup> et incluent <xref:System.Windows.Media.Animation.ParallelTimeline> et <xref:System.Windows.Media.Animation.Storyboard>.

Un <xref:System.Windows.Media.Animation.Storyboard> est un type de chronologie de conteneur qui fournit des informations de ciblage pour les chronologies qu’il contient. Une table de montage séquentiel peut contenir n’importe quel type de <xref:System.Windows.Media.Animation.Timeline>, y compris d’autres chronologies de conteneur et animations. les objets <xref:System.Windows.Media.Animation.Storyboard> vous permettent de combiner des chronologies qui affectent une variété d’objets et de propriétés dans une arborescence de chronologie unique, ce qui facilite l’organisation et le contrôle des comportements de minutage complexes. Par exemple, supposons que vous souhaitiez disposer d’un bouton qui effectue les trois opérations suivantes.

- Développer et changer de couleur lorsque l’utilisateur sélectionne le bouton.

- Réduire puis revenir à la taille normale lorsque l’utilisateur clique dessus.

- Réduire et atténuer l’opacité en la définissant sur 50 % lorsque le bouton est désactivé.

Dans ce cas, vous avez plusieurs jeux d’animations qui s’appliquent au même objet, et vous souhaitez les jouer à différents moments, en fonction de l’état du bouton. les objets <xref:System.Windows.Media.Animation.Storyboard> vous permettent d’organiser les animations et de les appliquer dans des groupes à un ou plusieurs objets.

<a name="wherecanyouuseastoryboard"></a>

## <a name="where-can-you-use-a-storyboard"></a>Où pouvez-vous utiliser une table de montage séquentiel ?

Un <xref:System.Windows.Media.Animation.Storyboard> peut être utilisé pour animer des propriétés de dépendance de classes pouvant être animées (pour plus d’informations sur ce qui rend une classe animable, consultez [vue d’ensemble](animation-overview.md)de l’animation). Toutefois, étant donné que le Storyboard est une fonctionnalité au niveau de l’infrastructure, l’objet doit appartenir au <xref:System.Windows.NameScope> d’un <xref:System.Windows.FrameworkElement> ou d’un <xref:System.Windows.FrameworkContentElement>.

Par exemple, vous pouvez utiliser un <xref:System.Windows.Media.Animation.Storyboard> pour effectuer les opérations suivantes :

- Animer un <xref:System.Windows.Media.SolidColorBrush> (élément non-Framework) qui peint l’arrière-plan d’un bouton (type de <xref:System.Windows.FrameworkElement>),

- Animer un <xref:System.Windows.Media.SolidColorBrush> (élément non-Framework) qui peint le remplissage d’un <xref:System.Windows.Media.GeometryDrawing> (élément non-Framework) affiché à l’aide d’un <xref:System.Windows.Controls.Image> (<xref:System.Windows.FrameworkElement>).

- Dans le code, animez un <xref:System.Windows.Media.SolidColorBrush> déclaré par une classe qui contient également un <xref:System.Windows.FrameworkElement>, si le <xref:System.Windows.Media.SolidColorBrush> inscrit son nom auprès de ce <xref:System.Windows.FrameworkElement>.

Toutefois, vous ne pouviez pas utiliser de <xref:System.Windows.Media.Animation.Storyboard> pour animer un <xref:System.Windows.Media.SolidColorBrush> qui n’a pas inscrit son nom avec un <xref:System.Windows.FrameworkElement> ou un <xref:System.Windows.FrameworkContentElement>, ou n’a pas été utilisé pour définir une propriété d’un <xref:System.Windows.FrameworkElement> ou d’un <xref:System.Windows.FrameworkContentElement>.

<a name="applyanimationswithastoryboard"></a>

## <a name="how-to-apply-animations-with-a-storyboard"></a>Comment appliquer des animations avec une table de montage séquentiel

Pour utiliser une <xref:System.Windows.Media.Animation.Storyboard> pour organiser et appliquer des animations, vous ajoutez les animations en tant que chronologies enfants du <xref:System.Windows.Media.Animation.Storyboard>. La classe <xref:System.Windows.Media.Animation.Storyboard> fournit les propriétés jointes <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A?displayProperty=nameWithType> et <xref:System.Windows.Media.Animation.Storyboard.TargetProperty?displayProperty=nameWithType>. Vous définissez ces propriétés sur une animation pour spécifier sa propriété et son objet cibles.

Pour appliquer des animations à leurs cibles, commencez l' <xref:System.Windows.Media.Animation.Storyboard> à l’aide d’une action de déclencheur ou d’une méthode. Dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], vous utilisez un objet <xref:System.Windows.Media.Animation.BeginStoryboard> avec un <xref:System.Windows.EventTrigger>, <xref:System.Windows.Trigger>ou <xref:System.Windows.DataTrigger>. Dans le code, vous pouvez également utiliser la méthode <xref:System.Windows.Media.Animation.Storyboard.Begin%2A>.

Le tableau suivant présente les différents emplacements où chaque technique de <xref:System.Windows.Media.Animation.Storyboard> début est prise en charge : par instance, style, modèle de contrôle et modèle de données. « Par instance » fait référence à la technique consistant à appliquer une animation ou une table de montage séquentiel directement aux instances d’un objet, plutôt qu’à un style, un modèle de contrôle ou un modèle de données.

|La table de montage séquentiel démarre à l’aide de…|Par instance|Style|Modèle de contrôle|Modèle de données|Exemple|
|--------------------------------|-------------------|-----------|----------------------|-------------------|-------------|
|<xref:System.Windows.Media.Animation.BeginStoryboard> et un <xref:System.Windows.EventTrigger>|Oui|Oui|Oui|Oui|[Animer une propriété à l’aide d’une table de montage séquentiel](how-to-animate-a-property-by-using-a-storyboard.md)|
|<xref:System.Windows.Media.Animation.BeginStoryboard> et une propriété <xref:System.Windows.Trigger>|Non|Oui|Oui|Oui|[Déclencher une animation en cas de modification d’une valeur de propriété](how-to-trigger-an-animation-when-a-property-value-changes.md)|
|<xref:System.Windows.Media.Animation.BeginStoryboard> et un <xref:System.Windows.DataTrigger>|Non|Oui|Oui|Oui|[Comment : déclencher une animation en cas de modification de données](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa970679(v=vs.90))|
|Méthode <xref:System.Windows.Media.Animation.Storyboard.Begin%2A>|Oui|Non|Non|Non|[Animer une propriété à l’aide d’une table de montage séquentiel](how-to-animate-a-property-by-using-a-storyboard.md)|

L’exemple suivant utilise une <xref:System.Windows.Media.Animation.Storyboard> pour animer le <xref:System.Windows.FrameworkElement.Width%2A> d’un élément <xref:System.Windows.Shapes.Rectangle> et le <xref:System.Windows.Media.SolidColorBrush.Color%2A> d’un <xref:System.Windows.Media.SolidColorBrush> utilisé pour peindre ce <xref:System.Windows.Shapes.Rectangle>.

[!code-xaml[storyboards_ovw_snip_XAML#1](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#1)]

[!code-csharp[storyboards_ovw_snip#100](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#100)]

Les sections suivantes décrivent les <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> et <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> propriétés jointes plus en détail.

<a name="targetingelementsandfreezables"></a>

## <a name="targeting-framework-elements-framework-content-elements-and-freezables"></a>Ciblage des éléments d’infrastructure, des éléments de contenu d’infrastructure et des éléments Freezables

Dans la section précédente, il était mentionné que, pour qu’une animation trouve sa cible, elle devait connaître la propriété et le nom de la cible à animer. La spécification de la propriété à animer est directe : il suffit de définir <xref:System.Windows.Media.Animation.Storyboard.TargetProperty?displayProperty=nameWithType> avec le nom de la propriété à animer.  Vous spécifiez le nom de l’objet dont vous souhaitez animer la propriété en définissant la propriété <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A?displayProperty=nameWithType> sur l’animation.

Pour que la propriété <xref:System.Windows.Setter.TargetName%2A> fonctionne, l’objet ciblé doit avoir un nom. L’attribution d’un nom à un <xref:System.Windows.FrameworkElement> ou à un <xref:System.Windows.FrameworkContentElement> dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] est différente de l’attribution d’un nom à un objet <xref:System.Windows.Freezable>.

Les éléments de l’infrastructure sont les classes qui héritent de la classe <xref:System.Windows.FrameworkElement>. <xref:System.Windows.Window>, <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Button>et <xref:System.Windows.Shapes.Rectangle>sont des exemples d’éléments d’infrastructure. Essentiellement, tous les contrôles, panneaux et fenêtres sont des éléments. Les éléments de contenu d’infrastructure sont les classes qui héritent de la classe <xref:System.Windows.FrameworkContentElement>. <xref:System.Windows.Documents.FlowDocument> et <xref:System.Windows.Documents.Paragraph>sont des exemples d’éléments de contenu de Framework. Si vous ne savez pas si un type est un élément d’infrastructure ou un élément de contenu d’infrastructure, vérifiez s’il possède une propriété Nom. Si c’est le cas, il s’agit probablement d’un élément d’infrastructure ou d’un élément de contenu d’infrastructure. Pour vous en assurer, vérifiez la section Inheritance Hierarchy (Hiérarchie d’héritage) de sa page de type.

Pour activer le ciblage d’un élément d’infrastructure ou d’un élément de contenu d’infrastructure dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], vous définissez sa propriété <xref:System.Windows.FrameworkElement.Name%2A>. Dans le code, vous devez également utiliser la méthode <xref:System.Windows.NameScope.RegisterName%2A> pour enregistrer le nom de l’élément avec l’élément pour lequel vous avez créé une <xref:System.Windows.NameScope>.

L’exemple suivant, extrait de l’exemple précédent, attribue le nom `MyRectangle` un <xref:System.Windows.Shapes.Rectangle>, un type de <xref:System.Windows.FrameworkElement>.

[!code-xaml[storyboards_ovw_snip_XAML#2](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#2)]

[!code-csharp[storyboards_ovw_snip#102](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#102)]

Une fois qu’un nom a été assigné, vous pouvez animer une propriété de cet élément.

[!code-xaml[storyboards_ovw_snip_XAML#5](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#5)]

[!code-csharp[storyboards_ovw_snip#105](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#105)]

les types de <xref:System.Windows.Freezable> sont les classes qui héritent de la classe <xref:System.Windows.Freezable>. Voici quelques exemples de <xref:System.Windows.Freezable> : <xref:System.Windows.Media.SolidColorBrush>, <xref:System.Windows.Media.RotateTransform>et <xref:System.Windows.Media.GradientStop>.

Pour activer le ciblage d’un <xref:System.Windows.Freezable> par une animation dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], vous utilisez la [directive x :Name](../../../desktop-wpf/xaml-services/xname-directive.md) pour lui assigner un nom. Dans le code, vous utilisez la méthode <xref:System.Windows.NameScope.RegisterName%2A> pour inscrire son nom avec l’élément pour lequel vous avez créé une <xref:System.Windows.NameScope>.

L’exemple suivant affecte un nom à un objet <xref:System.Windows.Freezable>.

[!code-xaml[storyboards_ovw_snip_XAML#3](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#3)]

[!code-csharp[storyboards_ovw_snip#103](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#103)]

L’objet peut ensuite être ciblé par une animation.

[!code-xaml[storyboards_ovw_snip_XAML#7](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#7)]

[!code-csharp[storyboards_ovw_snip#107](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#107)]

les objets <xref:System.Windows.Media.Animation.Storyboard> utilisent des portées de nom pour résoudre la propriété <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>. Pour plus d’informations sur les portées de nom WPF, consultez [Portées de nom XAML WPF](../advanced/wpf-xaml-namescopes.md). Si la propriété <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> est omise, l’animation cible l’élément sur lequel elle est définie, ou, dans le cas des styles, l’élément stylisé.

Parfois, un nom ne peut pas être assigné à un objet <xref:System.Windows.Freezable>. Par exemple, si un <xref:System.Windows.Freezable> est déclaré en tant que ressource ou utilisé pour définir une valeur de propriété dans un style, il ne peut pas recevoir un nom. Comme il n’a pas de nom, il ne peut pas être ciblé directement, mais peut l’être indirectement. Les sections suivantes décrivent comment utiliser le ciblage indirect.

<a name="pathsyntaxforchangeable"></a>

## <a name="indirect-targeting"></a>Ciblage indirect

Il peut arriver qu’un <xref:System.Windows.Freezable> ne puisse pas être ciblé directement par une animation, par exemple lorsque le <xref:System.Windows.Freezable> est déclaré en tant que ressource ou utilisé pour définir une valeur de propriété dans un style. Dans ce cas, même si vous ne pouvez pas le cibler directement, vous pouvez toujours animer l’objet <xref:System.Windows.Freezable>. Au lieu de définir la propriété <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> avec le nom de l' <xref:System.Windows.Freezable>, vous lui donnez le nom de l’élément auquel le <xref:System.Windows.Freezable> « appartient ». Par exemple, un <xref:System.Windows.Media.SolidColorBrush> utilisé pour définir la <xref:System.Windows.Shapes.Shape.Fill%2A> d’un élément Rectangle appartient à ce rectangle. Pour animer le pinceau, vous devez définir le <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> de l’animation avec une chaîne de propriétés qui commence à la propriété de l’élément de l’infrastructure ou de l’élément de contenu de l’infrastructure, le <xref:System.Windows.Freezable> a été utilisé pour définir et se termine avec la propriété <xref:System.Windows.Freezable> à animer.

[!code-xaml[storyboards_ovw_snip_XAML#33](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#33)]

[!code-csharp[storyboards_ovw_snip#134](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#134)]

Notez que, si le <xref:System.Windows.Freezable> est figé, un clone est créé et ce clone est animé. Dans ce cas, la propriété <xref:System.Windows.Media.Animation.Animatable.HasAnimatedProperties%2A> de l’objet d’origine continue à retourner `false`, car l’objet d’origine n’est pas réellement animé. Pour plus d’informations sur le clonage, consultez [vue d’ensemble des objets Freezable](../advanced/freezable-objects-overview.md).

Notez également que, lorsque vous utilisez le ciblage de propriété indirect, il est possible de cibler des objets qui n’existent pas. Par exemple, vous pouvez supposer que le <xref:System.Windows.Controls.Control.Background%2A> d’un bouton particulier a été défini avec un <xref:System.Windows.Media.SolidColorBrush> et essayer d’animer sa couleur, en fait un <xref:System.Windows.Media.LinearGradientBrush> a été utilisé pour définir l’arrière-plan du bouton. Dans ce cas, aucune exception n’est levée. l’animation ne peut pas avoir un effet visible, car <xref:System.Windows.Media.LinearGradientBrush> ne réagit pas aux modifications apportées à la propriété <xref:System.Windows.Media.SolidColorBrush.Color%2A>.

Les sections suivantes décrivent plus en détail la syntaxe de ciblage de propriété indirect.

<a name="xamlsyntaxchangeableproperty"></a>

### <a name="indirectly-targeting-a-property-of-a-freezable-in-xaml"></a>Ciblage indirect d’une propriété d’un élément Freezable en XAML

Pour cibler une propriété d’un Freezable dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], utilisez la syntaxe suivante.

| |
|-|
|*ElementPropertyName* `.` *FreezablePropertyName*|

Où

- *ElementPropertyName* est la propriété de la <xref:System.Windows.FrameworkElement> laquelle la <xref:System.Windows.Freezable> est utilisée pour définir, et

- *FreezablePropertyName* est la propriété de l' <xref:System.Windows.Freezable> à animer.

Le code suivant montre comment animer le <xref:System.Windows.Media.SolidColorBrush.Color%2A> d’un <xref:System.Windows.Media.SolidColorBrush> utilisé pour définir la <xref:System.Windows.Shapes.Shape.Fill%2A> d’un élément Rectangle.

[!code-xaml[storyboards_ovw_snip_XAML#32](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#32)]

Vous devez parfois cibler un élément Freezable contenu dans une collection ou un tableau.

Pour cibler un élément Freezable contenu dans une collection, vous utilisez la syntaxe de chemin d’accès suivante.

| |
|-|
|*ElementPropertyName* `.Children[` *CollectionIndex* `].` *FreezablePropertyName*|

Où *CollectionIndex* est l’index de l’objet dans son tableau ou sa collection.

Par exemple, supposons qu’un rectangle a une ressource <xref:System.Windows.Media.TransformGroup> appliquée à sa propriété <xref:System.Windows.UIElement.RenderTransform%2A> et que vous souhaitez animer l’une des transformations qu’il contient.

[!code-xaml[storyboards_ovw_snip_XAML#34](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#34)]

Le code suivant montre comment animer la propriété <xref:System.Windows.Media.RotateTransform.Angle%2A> du <xref:System.Windows.Media.RotateTransform> présenté dans l’exemple précédent.

[!code-xaml[storyboards_ovw_snip_XAML#35](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#35)]

<a name="targetingpropertyofchangeableincode"></a>

### <a name="indirectly-targeting-a-property-of-a-freezable-in-code"></a>Ciblage indirect d’une propriété d’un élément Freezable dans le code

Dans le code, vous créez un objet <xref:System.Windows.PropertyPath>. Lorsque vous créez le <xref:System.Windows.PropertyPath>, vous spécifiez un <xref:System.Windows.PropertyPath.Path%2A> et <xref:System.Windows.PropertyPath.PathParameters%2A>.

Pour créer <xref:System.Windows.PropertyPath.PathParameters%2A>, vous créez un tableau de type <xref:System.Windows.DependencyProperty> qui contient une liste de champs d’identificateur de propriété de dépendance. Le premier champ d’identificateur est pour la propriété du <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement> que le <xref:System.Windows.Freezable> est utilisé pour définir. Le champ d’identificateur suivant représente la propriété de la <xref:System.Windows.Freezable> à cibler. Considérez-le comme une chaîne de propriétés qui connecte l' <xref:System.Windows.Freezable> à l’objet <xref:System.Windows.FrameworkElement>.

Voici un exemple de chaîne de propriété de dépendance qui cible le <xref:System.Windows.Media.SolidColorBrush.Color%2A> d’un <xref:System.Windows.Media.SolidColorBrush> utilisé pour définir la <xref:System.Windows.Shapes.Shape.Fill%2A> d’un élément Rectangle.

[!code-csharp[storyboards_ovw_snip#135](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#135)]

Vous devez également spécifier un <xref:System.Windows.PropertyPath.Path%2A>. Un <xref:System.Windows.PropertyPath.Path%2A> est un <xref:System.String> qui indique à l' <xref:System.Windows.PropertyPath.Path%2A> comment interpréter ses <xref:System.Windows.PropertyPath.PathParameters%2A>. Il utilise la syntaxe suivante.

| |
|-|
|`(` *OwnerPropertyArrayIndex* `).(` *FreezablePropertyArrayIndex* `)`|

Où

- *OwnerPropertyArrayIndex* est l’index du tableau de <xref:System.Windows.DependencyProperty> qui contient l’identificateur de la propriété de l’objet <xref:System.Windows.FrameworkElement> que le <xref:System.Windows.Freezable> est utilisé pour définir, et

- *FreezablePropertyArrayIndex* est l’index du tableau de <xref:System.Windows.DependencyProperty> qui contient l’identificateur de la propriété à cibler.

L’exemple suivant montre les <xref:System.Windows.PropertyPath.Path%2A> qui accompagnaient le <xref:System.Windows.PropertyPath.PathParameters%2A> défini dans l’exemple précédent.

[!code-csharp[storyboards_ovw_snip#PropertyChainAndPath](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#propertychainandpath)]

L’exemple suivant combine le code des exemples précédents pour animer le <xref:System.Windows.Media.SolidColorBrush.Color%2A> d’un <xref:System.Windows.Media.SolidColorBrush> utilisé pour définir la <xref:System.Windows.Shapes.Shape.Fill%2A> d’un élément Rectangle.

[!code-csharp[storyboards_ovw_snip#137](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#137)]

Vous devez parfois cibler un élément Freezable contenu dans une collection ou un tableau. Par exemple, supposons qu’un rectangle a une ressource <xref:System.Windows.Media.TransformGroup> appliquée à sa propriété <xref:System.Windows.UIElement.RenderTransform%2A> et que vous souhaitez animer l’une des transformations qu’il contient.

[!code-xaml[storyboards_ovw_snip#142](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml#142)]

Pour cibler un <xref:System.Windows.Freezable> contenu dans une collection, vous utilisez la syntaxe de chemin d’accès suivante.

| |
|-|
|`(` *OwnerPropertyArrayIndex* `).(` *CollectionChildrenPropertyArrayIndex* `)` `[` *CollectionIndex* `].(` *FreezablePropertyArrayIndex* `)`|

Où *CollectionIndex* est l’index de l’objet dans son tableau ou sa collection.

Pour cibler la propriété <xref:System.Windows.Media.RotateTransform.Angle%2A> du <xref:System.Windows.Media.RotateTransform>, la deuxième transformation dans le <xref:System.Windows.Media.TransformGroup>, vous utiliseriez le <xref:System.Windows.PropertyPath.Path%2A> et le <xref:System.Windows.PropertyPath.PathParameters%2A>suivants.

[!code-csharp[storyboards_ovw_snip#139](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#139)]

L’exemple suivant montre le code complet permettant d’animer le <xref:System.Windows.Media.RotateTransform.Angle%2A> d’un <xref:System.Windows.Media.RotateTransform> contenu dans un <xref:System.Windows.Media.TransformGroup>.

[!code-csharp[storyboards_ovw_snip#138](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#138)]

### <a name="indirectly-targeting-with-a-freezable-as-the-starting-point"></a>Ciblage indirect avec un élément Freezable comme point de départ

Les sections précédentes décrivaient comment cibler indirectement une <xref:System.Windows.Freezable> en commençant par une <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement> et en créant une chaîne de propriété pour une sous-propriété <xref:System.Windows.Freezable>. Vous pouvez également utiliser une <xref:System.Windows.Freezable> comme point de départ et cibler indirectement l’une de ses <xref:System.Windows.Freezable> sous-propriétés. Une restriction supplémentaire s’applique lors de l’utilisation d’un <xref:System.Windows.Freezable> comme point de départ pour le ciblage indirect : le <xref:System.Windows.Freezable> de départ et chaque <xref:System.Windows.Freezable> entre celui-ci et la sous-propriété indirectement ciblée ne doivent pas être figées.

<a name="controllable_storyboards"></a>

## <a name="interactively-controlling-a-storyboard-in-xaml"></a>Contrôle interactif d’une table de montage séquentiel en XAML

Pour démarrer une table de montage séquentiel dans [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], vous utilisez une action de déclencheur <xref:System.Windows.Media.Animation.BeginStoryboard>. <xref:System.Windows.Media.Animation.BeginStoryboard> distribue les animations aux objets et propriétés qu’ils animent, et démarre le Storyboard. (Pour plus d’informations sur ce processus, consultez [vue d’ensemble du système d’animation et de minutage](animation-and-timing-system-overview.md).) Si vous attribuez un nom à la <xref:System.Windows.Media.Animation.BeginStoryboard> en spécifiant sa propriété <xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A>, vous en faites une table de montage séquentiel contrôlable. Vous pouvez ensuite contrôler interactivement la table de montage séquentiel après son démarrage. Vous trouverez ci-dessous une liste d’actions de table de montage séquentiel contrôlable à utiliser avec des déclencheurs d’événements pour contrôler une table de montage séquentiel.

- <xref:System.Windows.Media.Animation.PauseStoryboard>: suspend le Storyboard.

- <xref:System.Windows.Media.Animation.ResumeStoryboard>: reprend un Storyboard suspendu.

- <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>: modifie la vitesse de la table de montage séquentiel.

- <xref:System.Windows.Media.Animation.SkipStoryboardToFill>: fait avancer un Storyboard jusqu’à la fin de sa période de remplissage, le cas échéant.

- <xref:System.Windows.Media.Animation.StopStoryboard>: arrête le Storyboard.

- <xref:System.Windows.Media.Animation.RemoveStoryboard>: supprime la table de montage séquentiel.

Dans l’exemple suivant, les actions de table de montage séquentiel contrôlable servent à contrôler interactivement une table de montage séquentiel.

[!code-xaml[animation_ovws_snip#ControllableStoryboardExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snip/CS/ControllableStoryboardExample.xaml#controllablestoryboardexamplewholepage)]

<a name="controllable_storyboards_procedural"></a>

## <a name="interactively-controlling-a-storyboard-by-using-code"></a>Contrôle interactif d’une table de montage séquentiel avec du code

Les exemples précédents ont montré comment animer à l’aide d’actions de déclencheur. Dans le code, vous pouvez également contrôler une table de montage séquentiel à l’aide de méthodes interactives de la classe <xref:System.Windows.Media.Animation.Storyboard>. Pour qu’un <xref:System.Windows.Media.Animation.Storyboard> soit rendu interactif dans le code, vous devez utiliser la surcharge appropriée de la méthode <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> de la table de montage séquentiel et spécifier `true` pour le rendre contrôlable. Pour plus d’informations, consultez la page <xref:System.Windows.Media.Animation.Storyboard.Begin%28System.Windows.FrameworkElement%2CSystem.Boolean%29>.

La liste suivante présente les méthodes qui peuvent être utilisées pour manipuler un <xref:System.Windows.Media.Animation.Storyboard> après son démarrage :

- <xref:System.Windows.Media.Animation.Storyboard.Pause%2A>

- <xref:System.Windows.Media.Animation.Storyboard.Resume%2A>

- <xref:System.Windows.Media.Animation.Storyboard.Seek%2A>

- <xref:System.Windows.Media.Animation.Storyboard.SkipToFill%2A>

- <xref:System.Windows.Media.Animation.Storyboard.Stop%2A>

- <xref:System.Windows.Media.Animation.Storyboard.Remove%2A>

L’avantage d’utiliser ces méthodes est que vous n’avez pas besoin de créer des objets <xref:System.Windows.Trigger> ou <xref:System.Windows.TriggerAction> ; vous avez simplement besoin d’une référence à l' <xref:System.Windows.Media.Animation.Storyboard> contrôlable que vous souhaitez manipuler.

> [!NOTE]
> Toutes les actions interactives effectuées sur un <xref:System.Windows.Media.Animation.Clock>et, par conséquent, sur un <xref:System.Windows.Media.Animation.Storyboard> se produisent sur le cycle suivant du moteur de minutage qui se produira peu de temps avant le rendu suivant. Par exemple, si vous utilisez la méthode <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> pour accéder à un autre point d’une animation, la valeur de la propriété ne change pas instantanément, plutôt que la valeur change sur le cycle suivant du moteur de minutage.

L’exemple suivant montre comment appliquer et contrôler des animations à l’aide des méthodes interactives de la classe <xref:System.Windows.Media.Animation.Storyboard>.

[!code-csharp[animation_ovws_procedural_snip#ControllableStoryboardExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_procedural_snip/CSharp/ControllableStoryboardExample.cs#controllablestoryboardexamplewholepage)]
[!code-vb[animation_ovws_procedural_snip#ControllableStoryboardExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws_procedural_snip/visualbasic/controllablestoryboardexample.vb#controllablestoryboardexamplewholepage)]

<a name="usingstoryboardsinstyles"></a>

## <a name="animate-in-a-style"></a>Animer dans un style

Vous pouvez utiliser des objets <xref:System.Windows.Media.Animation.Storyboard> pour définir des animations dans une <xref:System.Windows.Style>. L’animation avec une <xref:System.Windows.Media.Animation.Storyboard> dans un <xref:System.Windows.Style> est similaire à l’utilisation d’un <xref:System.Windows.Media.Animation.Storyboard> ailleurs, avec les trois exceptions suivantes :

- Vous ne spécifiez pas de <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>; le <xref:System.Windows.Media.Animation.Storyboard> cible toujours l’élément auquel le <xref:System.Windows.Style> est appliqué. Pour cibler des objets <xref:System.Windows.Freezable>, vous devez utiliser le ciblage indirect. Pour plus d’informations sur le ciblage indirect, consultez la section [ciblage indirect](#pathsyntaxforchangeable) .

- Vous ne pouvez pas spécifier de <xref:System.Windows.EventTrigger.SourceName%2A> pour un <xref:System.Windows.EventTrigger> ou un <xref:System.Windows.Trigger>.

- Vous ne pouvez pas utiliser des références de ressources dynamiques ou des expressions de liaison de données pour définir des <xref:System.Windows.Media.Animation.Storyboard> ou des valeurs de propriété d’animation. Cela est dû au fait que tout ce qui se trouve dans un <xref:System.Windows.Style> doit être thread-safe et que le système de minutage doit <xref:System.Windows.Freezable.Freeze%2A><xref:System.Windows.Media.Animation.Storyboard> objets pour les rendre thread-safe. Un <xref:System.Windows.Media.Animation.Storyboard> ne peut pas être figé si celui-ci ou ses chronologies enfants contiennent des références de ressources dynamiques ou des expressions de liaison de données. Pour plus d’informations sur la congélation et d’autres fonctionnalités de <xref:System.Windows.Freezable>, consultez la [vue d’ensemble des objets Freezable](../advanced/freezable-objects-overview.md).

- Dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], vous ne pouvez pas déclarer de gestionnaires d’événements pour les événements <xref:System.Windows.Media.Animation.Storyboard> ou d’animation.

Pour obtenir un exemple qui montre comment définir une table de montage séquentiel dans un style, consultez l’exemple [animer dans un style](how-to-animate-in-a-style.md) .

<a name="defineAStoryboardInAControlTemplateSection"></a>

## <a name="animate-in-a-controltemplate"></a>Effectuer une animation dans un ControlTemplate

Vous pouvez utiliser des objets <xref:System.Windows.Media.Animation.Storyboard> pour définir des animations dans une <xref:System.Windows.Controls.ControlTemplate>. L’animation avec une <xref:System.Windows.Media.Animation.Storyboard> dans un <xref:System.Windows.Controls.ControlTemplate> est similaire à l’utilisation d’un <xref:System.Windows.Media.Animation.Storyboard> ailleurs, avec les deux exceptions suivantes :

- La <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> ne peut faire référence qu’aux objets enfants du <xref:System.Windows.Controls.ControlTemplate>. Si <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> n’est pas spécifié, l’animation cible l’élément auquel le <xref:System.Windows.Controls.ControlTemplate> est appliqué.

- La <xref:System.Windows.EventTrigger.SourceName%2A> d’un <xref:System.Windows.EventTrigger> ou d’un <xref:System.Windows.Trigger> peut uniquement faire référence à des objets enfants de l' <xref:System.Windows.Controls.ControlTemplate>.

- Vous ne pouvez pas utiliser des références de ressources dynamiques ou des expressions de liaison de données pour définir des <xref:System.Windows.Media.Animation.Storyboard> ou des valeurs de propriété d’animation. Cela est dû au fait que tout ce qui se trouve dans un <xref:System.Windows.Controls.ControlTemplate> doit être thread-safe et que le système de minutage doit <xref:System.Windows.Freezable.Freeze%2A><xref:System.Windows.Media.Animation.Storyboard> objets pour les rendre thread-safe. Un <xref:System.Windows.Media.Animation.Storyboard> ne peut pas être figé si celui-ci ou ses chronologies enfants contiennent des références de ressources dynamiques ou des expressions de liaison de données. Pour plus d’informations sur la congélation et d’autres fonctionnalités de <xref:System.Windows.Freezable>, consultez la [vue d’ensemble des objets Freezable](../advanced/freezable-objects-overview.md).

- Dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], vous ne pouvez pas déclarer de gestionnaires d’événements pour les événements <xref:System.Windows.Media.Animation.Storyboard> ou d’animation.

Pour obtenir un exemple illustrant comment définir une table de montage séquentiel dans un <xref:System.Windows.Controls.ControlTemplate>, consultez l’exemple [animation dans un ControlTemplate](how-to-animate-in-a-controltemplate.md) .

<a name="animateWhenAPropertyValueChanges"></a>

## <a name="animate-when-a-property-value-changes"></a>Animer en cas de modification d’une valeur de propriété

Dans les styles et les modèles de contrôle, vous pouvez utiliser des objets Trigger pour démarrer une table de montage séquentiel en cas de modification d’une propriété. Pour obtenir des exemples, consultez [déclencher une animation quand une valeur de propriété change](how-to-trigger-an-animation-when-a-property-value-changes.md) et [animer dans un ControlTemplate](how-to-animate-in-a-controltemplate.md).

Les animations appliquées par les objets de <xref:System.Windows.Trigger> de propriété se comportent de manière plus complexe que <xref:System.Windows.EventTrigger> animations ou animations démarrées à l’aide de <xref:System.Windows.Media.Animation.Storyboard> méthodes.  Ils « sont remis » avec les animations définies par d’autres objets <xref:System.Windows.Trigger>, mais composent avec des animations <xref:System.Windows.EventTrigger> et déclenchées par une méthode.

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de l’animation](animation-overview.md)
- [Vue d’ensemble des techniques d’animation de propriétés](property-animation-techniques-overview.md)
- [Vue d’ensemble des objets Freezable](../advanced/freezable-objects-overview.md)
