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
ms.openlocfilehash: 4d5a5ee3f1fcbd09fad9e25773d0e508209e1492
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855837"
---
# <a name="storyboards-overview"></a>Vue d'ensemble des storyboards

Cette rubrique montre comment utiliser <xref:System.Windows.Media.Animation.Storyboard> des objets pour organiser et appliquer des animations. Il décrit comment manipuler <xref:System.Windows.Media.Animation.Storyboard> des objets de manière interactive et décrit la syntaxe de ciblage de propriété indirecte.

## <a name="prerequisites"></a>Prérequis

Pour comprendre cette rubrique, vous devez connaître les différents types d’animations et leurs fonctions de base. Pour une introduction à l’animation, consultez [Vue d’ensemble de l’animation](animation-overview.md). Vous devez également savoir comment utiliser les propriétés jointes. Pour plus d’informations sur les propriétés jointes, consultez [Vue d’ensemble des propriétés jointes](../advanced/attached-properties-overview.md).

<a name="whatisatimeline"></a>

## <a name="what-is-a-storyboard"></a>Qu’est-ce qu’une table de montage séquentiel ?

Les animations ne sont pas le seul type utile de chronologie. D’autres classes de chronologie sont fournies pour vous aider à organiser des jeux de chronologies et à appliquer des chronologies aux propriétés. Les chronologies de conteneur dérivent de la <xref:System.Windows.Media.Animation.TimelineGroup> classe <xref:System.Windows.Media.Animation.Storyboard>et incluent <xref:System.Windows.Media.Animation.ParallelTimeline> et.

Un <xref:System.Windows.Media.Animation.Storyboard> est un type de chronologie de conteneur qui fournit des informations de ciblage pour les chronologies qu’il contient. Une table de montage séquentiel peut contenir <xref:System.Windows.Media.Animation.Timeline>tout type de, y compris d’autres chronologies de conteneur et animations. <xref:System.Windows.Media.Animation.Storyboard>les objets vous permettent de combiner des chronologies qui affectent une variété d’objets et de propriétés dans une arborescence de chronologie unique, ce qui facilite l’organisation et le contrôle des comportements de minutage complexes. Par exemple, supposons que vous souhaitiez disposer d’un bouton qui effectue les trois opérations suivantes.

- Développer et changer de couleur lorsque l’utilisateur sélectionne le bouton.

- Réduire puis revenir à la taille normale lorsque l’utilisateur clique dessus.

- Réduire et atténuer l’opacité en la définissant sur 50 % lorsque le bouton est désactivé.

Dans ce cas, vous avez plusieurs jeux d’animations qui s’appliquent au même objet, et vous souhaitez les jouer à différents moments, en fonction de l’état du bouton. <xref:System.Windows.Media.Animation.Storyboard>les objets vous permettent d’organiser les animations et de les appliquer dans des groupes à un ou plusieurs objets.

<a name="wherecanyouuseastoryboard"></a>

## <a name="where-can-you-use-a-storyboard"></a>Où pouvez-vous utiliser une table de montage séquentiel ?

Un <xref:System.Windows.Media.Animation.Storyboard> peut être utilisé pour animer des propriétés de dépendance de classes pouvant être animées (pour plus d’informations sur ce qui rend une classe animable, consultez [vue d’ensemble](animation-overview.md)de l’animation). Toutefois, étant donné que le Storyboard est une fonctionnalité au niveau de l’infrastructure, l’objet <xref:System.Windows.NameScope> doit appartenir <xref:System.Windows.FrameworkElement> au d' <xref:System.Windows.FrameworkContentElement>un ou d’un.

Par exemple, vous pouvez utiliser un <xref:System.Windows.Media.Animation.Storyboard> pour effectuer les opérations suivantes :

- Animer <xref:System.Windows.Media.SolidColorBrush> un (élément non-Framework) qui peint l’arrière-plan d’un bouton ( <xref:System.Windows.FrameworkElement>type de),

- Animer <xref:System.Windows.Media.SolidColorBrush> un (élément non-Framework) qui peint le remplissage d' <xref:System.Windows.Media.GeometryDrawing> un (élément non-Framework) affiché à <xref:System.Windows.Controls.Image> l'<xref:System.Windows.FrameworkElement>aide d’un ().

- Dans le code, <xref:System.Windows.Media.SolidColorBrush> animez un déclaré par une classe qui contient également un <xref:System.Windows.FrameworkElement>, <xref:System.Windows.Media.SolidColorBrush> si le nom de celui <xref:System.Windows.FrameworkElement>-ci est inscrit avec.

Toutefois, vous ne pouviez pas utiliser <xref:System.Windows.Media.Animation.Storyboard> un pour animer un <xref:System.Windows.Media.SolidColorBrush> qui n’a pas inscrit son <xref:System.Windows.FrameworkElement> nom <xref:System.Windows.FrameworkContentElement>avec un ou un, ou n’a pas été utilisé <xref:System.Windows.FrameworkElement> pour <xref:System.Windows.FrameworkContentElement>définir une propriété d’un ou d’un.

<a name="applyanimationswithastoryboard"></a>

## <a name="how-to-apply-animations-with-a-storyboard"></a>Comment appliquer des animations avec une table de montage séquentiel

Pour utiliser un <xref:System.Windows.Media.Animation.Storyboard> pour organiser et appliquer des animations, vous ajoutez les animations en tant que chronologies <xref:System.Windows.Media.Animation.Storyboard>enfants de. La <xref:System.Windows.Media.Animation.Storyboard> classe fournit les <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A?displayProperty=nameWithType> propriétés <xref:System.Windows.Media.Animation.Storyboard.TargetProperty?displayProperty=nameWithType> jointes et. Vous définissez ces propriétés sur une animation pour spécifier sa propriété et son objet cibles.

Pour appliquer des animations à leurs cibles, commencez l' <xref:System.Windows.Media.Animation.Storyboard> utilisation d’une action de déclencheur ou d’une méthode. Dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], vous utilisez un <xref:System.Windows.Media.Animation.BeginStoryboard> objet avec un <xref:System.Windows.EventTrigger>, <xref:System.Windows.Trigger>ou <xref:System.Windows.DataTrigger>. Dans le code, vous pouvez également utiliser <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> la méthode.

Le tableau suivant présente les différents emplacements où chaque <xref:System.Windows.Media.Animation.Storyboard> technique de début est prise en charge : par instance, style, modèle de contrôle et modèle de données. « Par instance » fait référence à la technique consistant à appliquer une animation ou une table de montage séquentiel directement aux instances d’un objet, plutôt qu’à un style, un modèle de contrôle ou un modèle de données.

|La table de montage séquentiel démarre à l’aide de…|Par instance|Style|Modèle de contrôle|Modèle de données|Exemple|
|--------------------------------|-------------------|-----------|----------------------|-------------------|-------------|
|<xref:System.Windows.Media.Animation.BeginStoryboard>et un<xref:System.Windows.EventTrigger>|Oui|OUI|OUI|Oui|[Animer une propriété à l’aide d’une table de montage séquentiel](how-to-animate-a-property-by-using-a-storyboard.md)|
|<xref:System.Windows.Media.Animation.BeginStoryboard>et une propriété<xref:System.Windows.Trigger>|Non|Oui|OUI|Oui|[Déclencher une animation en cas de modification d’une valeur de propriété](how-to-trigger-an-animation-when-a-property-value-changes.md)|
|<xref:System.Windows.Media.Animation.BeginStoryboard>et un<xref:System.Windows.DataTrigger>|Non|Oui|OUI|Oui|[Guide pratique pour Déclencher une animation en cas de modification des données](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa970679(v=vs.90))|
|Méthode <xref:System.Windows.Media.Animation.Storyboard.Begin%2A>|Oui|Non|Non|Non|[Animer une propriété à l’aide d’une table de montage séquentiel](how-to-animate-a-property-by-using-a-storyboard.md)|

L’exemple suivant utilise un <xref:System.Windows.Media.Animation.Storyboard> pour animer <xref:System.Windows.FrameworkElement.Width%2A> le d' <xref:System.Windows.Shapes.Rectangle> un élément et <xref:System.Windows.Media.SolidColorBrush.Color%2A> le d' <xref:System.Windows.Media.SolidColorBrush> un utilisé pour peindre <xref:System.Windows.Shapes.Rectangle>ce.

[!code-xaml[storyboards_ovw_snip_XAML#1](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#1)]

[!code-csharp[storyboards_ovw_snip#100](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#100)]

Les sections suivantes décrivent <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> les <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> propriétés et jointes plus en détail.

<a name="targetingelementsandfreezables"></a>

## <a name="targeting-framework-elements-framework-content-elements-and-freezables"></a>Ciblage des éléments d’infrastructure, des éléments de contenu d’infrastructure et des éléments Freezables

Dans la section précédente, il était mentionné que, pour qu’une animation trouve sa cible, elle devait connaître la propriété et le nom de la cible à animer. La spécification de la propriété à animer est directe : <xref:System.Windows.Media.Animation.Storyboard.TargetProperty?displayProperty=nameWithType> il suffit de définir le nom de la propriété à animer.  Vous spécifiez le nom de l’objet dont vous souhaitez animer la propriété en <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A?displayProperty=nameWithType> définissant la propriété sur l’animation.

Pour que <xref:System.Windows.Setter.TargetName%2A> la propriété fonctionne, l’objet ciblé doit avoir un nom. L’attribution d’un nom à <xref:System.Windows.FrameworkElement> un ou <xref:System.Windows.FrameworkContentElement> un [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dans est différente de l’attribution d’un nom <xref:System.Windows.Freezable> à un objet.

Les éléments de l’infrastructure sont les classes qui <xref:System.Windows.FrameworkElement> héritent de la classe. Les exemples d’éléments d' <xref:System.Windows.Window>infrastructure <xref:System.Windows.Controls.DockPanel>incluent <xref:System.Windows.Controls.Button>,, <xref:System.Windows.Shapes.Rectangle>et. Essentiellement, tous les contrôles, panneaux et fenêtres sont des éléments. Les éléments de contenu de l’infrastructure sont les classes <xref:System.Windows.FrameworkContentElement> qui héritent de la classe. Les exemples d’éléments de contenu <xref:System.Windows.Documents.FlowDocument> de <xref:System.Windows.Documents.Paragraph>Framework incluent et. Si vous ne savez pas si un type est un élément d’infrastructure ou un élément de contenu d’infrastructure, vérifiez s’il possède une propriété Nom. Si c’est le cas, il s’agit probablement d’un élément d’infrastructure ou d’un élément de contenu d’infrastructure. Pour vous en assurer, vérifiez la section Inheritance Hierarchy (Hiérarchie d’héritage) de sa page de type.

Pour activer le ciblage d’un élément d’infrastructure ou d’un élément de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]contenu d’infrastructure dans <xref:System.Windows.FrameworkElement.Name%2A> , vous devez définir sa propriété. Dans le code, vous devez également utiliser la <xref:System.Windows.NameScope.RegisterName%2A> méthode pour enregistrer le nom de l’élément avec l’élément pour lequel vous avez créé <xref:System.Windows.NameScope>un.

L’exemple suivant, extrait de l’exemple précédent, assigne le nom `MyRectangle` a <xref:System.Windows.Shapes.Rectangle>, un type <xref:System.Windows.FrameworkElement>.

[!code-xaml[storyboards_ovw_snip_XAML#2](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#2)]

[!code-csharp[storyboards_ovw_snip#102](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#102)]

Une fois qu’un nom a été assigné, vous pouvez animer une propriété de cet élément.

[!code-xaml[storyboards_ovw_snip_XAML#5](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#5)]

[!code-csharp[storyboards_ovw_snip#105](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#105)]

<xref:System.Windows.Freezable>les types sont les classes qui héritent <xref:System.Windows.Freezable> de la classe. Exemples de <xref:System.Windows.Freezable> include <xref:System.Windows.Media.SolidColorBrush>, <xref:System.Windows.Media.RotateTransform>et <xref:System.Windows.Media.GradientStop>.

Pour activer le ciblage d’un <xref:System.Windows.Freezable> par une animation dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], vous utilisez la [directive x :Name](../../xaml-services/x-name-directive.md) pour lui assigner un nom. Dans le code, vous utilisez <xref:System.Windows.NameScope.RegisterName%2A> la méthode pour enregistrer son nom avec l’élément pour lequel vous avez créé <xref:System.Windows.NameScope>un.

L’exemple suivant affecte un nom à un <xref:System.Windows.Freezable> objet.

[!code-xaml[storyboards_ovw_snip_XAML#3](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#3)]

[!code-csharp[storyboards_ovw_snip#103](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#103)]

L’objet peut ensuite être ciblé par une animation.

[!code-xaml[storyboards_ovw_snip_XAML#7](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#7)]

[!code-csharp[storyboards_ovw_snip#107](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#107)]

<xref:System.Windows.Media.Animation.Storyboard>les objets utilisent des portées de nom <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> pour résoudre la propriété. Pour plus d’informations sur les portées de nom WPF, consultez [Portées de nom XAML WPF](../advanced/wpf-xaml-namescopes.md). Si la <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> propriété est omise, l’animation cible l’élément sur lequel elle est définie, ou, dans le cas des styles, l’élément stylisé.

Parfois, un nom ne peut pas être <xref:System.Windows.Freezable> assigné à un objet. Par exemple, si un <xref:System.Windows.Freezable> est déclaré en tant que ressource ou utilisé pour définir une valeur de propriété dans un style, il ne peut pas recevoir un nom. Comme il n’a pas de nom, il ne peut pas être ciblé directement, mais peut l’être indirectement. Les sections suivantes décrivent comment utiliser le ciblage indirect.

<a name="pathsyntaxforchangeable"></a>

## <a name="indirect-targeting"></a>Ciblage indirect

Il peut arriver qu' <xref:System.Windows.Freezable> un ne puisse pas être ciblé directement par une animation, par <xref:System.Windows.Freezable> exemple lorsque le est déclaré en tant que ressource ou utilisé pour définir une valeur de propriété dans un style. Dans ce cas, même si vous ne pouvez pas le cibler directement, vous pouvez toujours <xref:System.Windows.Freezable> animer l’objet. Au lieu de définir <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> la propriété avec le nom <xref:System.Windows.Freezable>du, vous lui donnez le nom de l’élément auquel le <xref:System.Windows.Freezable> « appartient ». Par exemple, un <xref:System.Windows.Media.SolidColorBrush> utilisé pour définir le <xref:System.Windows.Shapes.Shape.Fill%2A> d’un élément Rectangle appartient à ce rectangle. Pour animer le pinceau, vous devez définir les éléments <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> de l’animation avec une chaîne de propriétés qui commence à la propriété de l’élément de l’infrastructure <xref:System.Windows.Freezable> ou de l’élément de contenu de l' <xref:System.Windows.Freezable> infrastructure que le a utilisé pour définir et se termine avec la propriété à animer.

[!code-xaml[storyboards_ovw_snip_XAML#33](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#33)]

[!code-csharp[storyboards_ovw_snip#134](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#134)]

Notez que, si le <xref:System.Windows.Freezable> est figé, un clone est créé et ce clone est animé. Dans ce cas, la propriété de <xref:System.Windows.Media.Animation.Animatable.HasAnimatedProperties%2A> l’objet d’origine continue à retourner `false`, car l’objet d’origine n’est pas réellement animé. Pour plus d’informations sur le clonage, consultez [vue d’ensemble des objets Freezable](../advanced/freezable-objects-overview.md).

Notez également que, lorsque vous utilisez le ciblage de propriété indirect, il est possible de cibler des objets qui n’existent pas. Par exemple, vous pouvez supposer que le <xref:System.Windows.Controls.Control.Background%2A> d’un bouton particulier a été défini avec <xref:System.Windows.Media.SolidColorBrush> un et essayer d’animer sa couleur, alors qu' <xref:System.Windows.Media.LinearGradientBrush> en fait un a été utilisé pour définir l’arrière-plan du bouton. Dans ce cas, aucune exception n’est levée. l’animation ne peut pas avoir d’effet visible <xref:System.Windows.Media.LinearGradientBrush> , car ne réagit pas aux <xref:System.Windows.Media.SolidColorBrush.Color%2A> modifications apportées à la propriété.

Les sections suivantes décrivent plus en détail la syntaxe de ciblage de propriété indirect.

<a name="xamlsyntaxchangeableproperty"></a>

### <a name="indirectly-targeting-a-property-of-a-freezable-in-xaml"></a>Ciblage indirect d’une propriété d’un élément Freezable en XAML

Pour cibler une propriété d’un Freezable dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], utilisez la syntaxe suivante.

| |
|-|
|*ElementPropertyName* `.` *FreezablePropertyName*|

Where

- *ElementPropertyName* est la propriété du <xref:System.Windows.FrameworkElement> qui <xref:System.Windows.Freezable> est utilisé pour définir, et

- *FreezablePropertyName* est la propriété du <xref:System.Windows.Freezable> à animer.

Le code suivant montre comment animer le <xref:System.Windows.Media.SolidColorBrush.Color%2A> d’un <xref:System.Windows.Media.SolidColorBrush> utilisé pour définir le <xref:System.Windows.Shapes.Shape.Fill%2A> d’un élément Rectangle.

[!code-xaml[storyboards_ovw_snip_XAML#32](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#32)]

Vous devez parfois cibler un élément Freezable contenu dans une collection ou un tableau.

Pour cibler un élément Freezable contenu dans une collection, vous utilisez la syntaxe de chemin d’accès suivante.

| |
|-|
|*ElementPropertyName* `.Children[` *CollectionIndex* `].` *FreezablePropertyName*|

Où *CollectionIndex* est l’index de l’objet dans son tableau ou sa collection.

Par exemple, supposons qu’un rectangle a <xref:System.Windows.Media.TransformGroup> une ressource appliquée à <xref:System.Windows.UIElement.RenderTransform%2A> sa propriété et que vous souhaitez animer l’une des transformations qu’il contient.

[!code-xaml[storyboards_ovw_snip_XAML#34](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#34)]

Le code suivant montre comment animer la <xref:System.Windows.Media.RotateTransform.Angle%2A> propriété de l' <xref:System.Windows.Media.RotateTransform> exemple indiqué dans l’exemple précédent.

[!code-xaml[storyboards_ovw_snip_XAML#35](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#35)]

<a name="targetingpropertyofchangeableincode"></a>

### <a name="indirectly-targeting-a-property-of-a-freezable-in-code"></a>Ciblage indirect d’une propriété d’un élément Freezable dans le code

Dans le code, vous créez <xref:System.Windows.PropertyPath> un objet. Lorsque vous créez le <xref:System.Windows.PropertyPath>, vous spécifiez <xref:System.Windows.PropertyPath.Path%2A> un <xref:System.Windows.PropertyPath.PathParameters%2A>et un.

Pour créer <xref:System.Windows.PropertyPath.PathParameters%2A>, vous créez un tableau de type <xref:System.Windows.DependencyProperty> qui contient une liste de champs d’identificateur de propriété de dépendance. Le premier champ d’identificateur est pour la propriété du <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement> que le <xref:System.Windows.Freezable> est utilisé pour définir. Le champ d’identificateur suivant représente la propriété du <xref:System.Windows.Freezable> à cibler. Considérez-le comme une chaîne de propriétés qui connecte <xref:System.Windows.Freezable> à l' <xref:System.Windows.FrameworkElement> objet.

Voici un exemple de chaîne de propriété de dépendance qui cible le <xref:System.Windows.Media.SolidColorBrush.Color%2A> d’un <xref:System.Windows.Media.SolidColorBrush> utilisé pour définir le <xref:System.Windows.Shapes.Shape.Fill%2A> d’un élément Rectangle.

[!code-csharp[storyboards_ovw_snip#135](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#135)]

Vous devez également spécifier un <xref:System.Windows.PropertyPath.Path%2A>. Un <xref:System.Windows.PropertyPath.Path%2A> est un <xref:System.String> qui indique <xref:System.Windows.PropertyPath.Path%2A> à comment interpréter son <xref:System.Windows.PropertyPath.PathParameters%2A>. Il utilise la syntaxe suivante.

| |
|-|
|`(` *OwnerPropertyArrayIndex* `).(` *FreezablePropertyArrayIndex* `)`|

Where

- *OwnerPropertyArrayIndex* est l’index du <xref:System.Windows.DependencyProperty> tableau qui contient l’identificateur de la <xref:System.Windows.FrameworkElement> propriété de l’objet que le <xref:System.Windows.Freezable> est utilisé pour définir, et

- *FreezablePropertyArrayIndex* est l’index du <xref:System.Windows.DependencyProperty> tableau qui contient l’identificateur de la propriété à cibler.

L’exemple suivant montre le <xref:System.Windows.PropertyPath.Path%2A> qui s’accompagnerait <xref:System.Windows.PropertyPath.PathParameters%2A> du défini dans l’exemple précédent.

[!code-csharp[storyboards_ovw_snip#PropertyChainAndPath](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#propertychainandpath)]

L’exemple suivant combine le code des exemples précédents pour animer le <xref:System.Windows.Media.SolidColorBrush.Color%2A> d’un <xref:System.Windows.Media.SolidColorBrush> utilisé pour définir le <xref:System.Windows.Shapes.Shape.Fill%2A> d’un élément Rectangle.

[!code-csharp[storyboards_ovw_snip#137](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#137)]

Vous devez parfois cibler un élément Freezable contenu dans une collection ou un tableau. Par exemple, supposons qu’un rectangle a <xref:System.Windows.Media.TransformGroup> une ressource appliquée à <xref:System.Windows.UIElement.RenderTransform%2A> sa propriété et que vous souhaitez animer l’une des transformations qu’il contient.

[!code-xaml[storyboards_ovw_snip#142](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml#142)]

Pour cibler un <xref:System.Windows.Freezable> contenu dans une collection, vous utilisez la syntaxe de chemin d’accès suivante.

| |
|-|
|`(` *OwnerPropertyArrayIndex* `).(` *CollectionChildrenPropertyArrayIndex* `)` `[` *CollectionIndex* `].(` *FreezablePropertyArrayIndex* `)`|

Où *CollectionIndex* est l’index de l’objet dans son tableau ou sa collection.

Pour cibler la <xref:System.Windows.Media.RotateTransform.Angle%2A> propriété <xref:System.Windows.Media.RotateTransform>du, la deuxième transformation dans le <xref:System.Windows.Media.TransformGroup>, utilisez les éléments suivants <xref:System.Windows.PropertyPath.Path%2A> et <xref:System.Windows.PropertyPath.PathParameters%2A>.

[!code-csharp[storyboards_ovw_snip#139](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#139)]

L’exemple suivant montre le code complet pour animer le <xref:System.Windows.Media.RotateTransform.Angle%2A> d’un <xref:System.Windows.Media.RotateTransform> contenu dans un <xref:System.Windows.Media.TransformGroup>.

[!code-csharp[storyboards_ovw_snip#138](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#138)]

### <a name="indirectly-targeting-with-a-freezable-as-the-starting-point"></a>Ciblage indirect avec un élément Freezable comme point de départ

Les sections précédentes décrivaient comment cibler indirectement un <xref:System.Windows.Freezable> en commençant par un <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement> et en créant une chaîne de propriétés <xref:System.Windows.Freezable> à une sous-propriété. Vous pouvez également utiliser un <xref:System.Windows.Freezable> comme point de départ et cibler indirectement l’une de <xref:System.Windows.Freezable> ses sous-propriétés. Une restriction supplémentaire s’applique lors de <xref:System.Windows.Freezable> l’utilisation d’un comme point de départ pour le <xref:System.Windows.Freezable> ciblage indirect <xref:System.Windows.Freezable> : la sous-propriété de départ et toutes les entre et la sous-propriété indirectement ciblée ne doivent pas être figées.

<a name="controllable_storyboards"></a>

## <a name="interactively-controlling-a-storyboard-in-xaml"></a>Contrôle interactif d’une table de montage séquentiel en XAML

Pour démarrer une table de [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]montage séquentiel dans, <xref:System.Windows.Media.Animation.BeginStoryboard> vous utilisez une action de déclencheur. <xref:System.Windows.Media.Animation.BeginStoryboard>distribue les animations aux objets et propriétés qu’elles animent, et démarre le Storyboard. (Pour plus d’informations sur ce processus, consultez [vue d’ensemble du système d’animation et de minutage](animation-and-timing-system-overview.md).) Si vous donnez <xref:System.Windows.Media.Animation.BeginStoryboard> un nom à un nom en <xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A> spécifiant sa propriété, vous en faites une table de montage séquentiel contrôlable. Vous pouvez ensuite contrôler interactivement la table de montage séquentiel après son démarrage. Vous trouverez ci-dessous une liste d’actions de table de montage séquentiel contrôlable à utiliser avec des déclencheurs d’événements pour contrôler une table de montage séquentiel.

- <xref:System.Windows.Media.Animation.PauseStoryboard>: Suspend le Storyboard.

- <xref:System.Windows.Media.Animation.ResumeStoryboard>: Reprend une table de montage séquentiel suspendue.

- <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>: Modifie la vitesse de la table de montage séquentiel.

- <xref:System.Windows.Media.Animation.SkipStoryboardToFill>: Fait avancer un Storyboard jusqu’à la fin de sa période de remplissage, le cas échéant.

- <xref:System.Windows.Media.Animation.StopStoryboard>: Arrête le Storyboard.

- <xref:System.Windows.Media.Animation.RemoveStoryboard>: Supprime la table de montage séquentiel.

Dans l’exemple suivant, les actions de table de montage séquentiel contrôlable servent à contrôler interactivement une table de montage séquentiel.

[!code-xaml[animation_ovws_snip#ControllableStoryboardExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snip/CS/ControllableStoryboardExample.xaml#controllablestoryboardexamplewholepage)]

<a name="controllable_storyboards_procedural"></a>

## <a name="interactively-controlling-a-storyboard-by-using-code"></a>Contrôle interactif d’une table de montage séquentiel avec du code

Les exemples précédents ont montré comment animer à l’aide d’actions de déclencheur. Dans le code, vous pouvez également contrôler une table de montage séquentiel à <xref:System.Windows.Media.Animation.Storyboard> l’aide de méthodes interactives de la classe. Pour qu' <xref:System.Windows.Media.Animation.Storyboard> un soit rendu interactif dans le code, vous devez utiliser la surcharge appropriée de la <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> méthode de la table `true` de montage séquentiel et spécifier pour le rendre contrôlable. Pour plus <xref:System.Windows.Media.Animation.Storyboard.Begin%28System.Windows.FrameworkElement%2CSystem.Boolean%29> d’informations, consultez la page.

La liste suivante présente les méthodes qui peuvent être utilisées pour manipuler un <xref:System.Windows.Media.Animation.Storyboard> après son démarrage :

- <xref:System.Windows.Media.Animation.Storyboard.Pause%2A>

- <xref:System.Windows.Media.Animation.Storyboard.Resume%2A>

- <xref:System.Windows.Media.Animation.Storyboard.Seek%2A>

- <xref:System.Windows.Media.Animation.Storyboard.SkipToFill%2A>

- <xref:System.Windows.Media.Animation.Storyboard.Stop%2A>

- <xref:System.Windows.Media.Animation.Storyboard.Remove%2A>

L’avantage de l’utilisation de ces méthodes est que vous n’avez <xref:System.Windows.Trigger> pas <xref:System.Windows.TriggerAction> besoin de créer des objets ou ; vous avez simplement besoin <xref:System.Windows.Media.Animation.Storyboard> d’une référence au contrôlable que vous souhaitez manipuler.

> [!NOTE]
> Toutes les actions interactives <xref:System.Windows.Media.Animation.Clock>effectuées sur un et, par <xref:System.Windows.Media.Animation.Storyboard> conséquent, sur un se produisent sur le cycle suivant du moteur de minutage qui se produira peu de temps avant le rendu suivant. Par exemple, si vous utilisez la <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> méthode pour accéder à un autre point d’une animation, la valeur de la propriété ne change pas instantanément, plutôt que la valeur change sur le cycle suivant du moteur de minutage.

L’exemple suivant montre comment appliquer et contrôler des animations à l’aide des méthodes interactives de la <xref:System.Windows.Media.Animation.Storyboard> classe.

[!code-csharp[animation_ovws_procedural_snip#ControllableStoryboardExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_procedural_snip/CSharp/ControllableStoryboardExample.cs#controllablestoryboardexamplewholepage)]
[!code-vb[animation_ovws_procedural_snip#ControllableStoryboardExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws_procedural_snip/visualbasic/controllablestoryboardexample.vb#controllablestoryboardexamplewholepage)]

<a name="usingstoryboardsinstyles"></a>

## <a name="animate-in-a-style"></a>Animer dans un style

Vous pouvez utiliser <xref:System.Windows.Media.Animation.Storyboard> des objets pour définir des animations <xref:System.Windows.Style>dans un. L’animation avec un <xref:System.Windows.Media.Animation.Storyboard> dans un <xref:System.Windows.Style> est semblable à l’utilisation <xref:System.Windows.Media.Animation.Storyboard> d’un autre emplacement, avec les trois exceptions suivantes :

- Vous ne spécifiez <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>pas un <xref:System.Windows.Media.Animation.Storyboard> ; le cible toujours l’élément auquel <xref:System.Windows.Style> le est appliqué. Pour cibler <xref:System.Windows.Freezable> des objets, vous devez utiliser le ciblage indirect. Pour plus d’informations sur le ciblage indirect, consultez la section [ciblage indirect](#pathsyntaxforchangeable) .

- Vous ne pouvez pas <xref:System.Windows.EventTrigger.SourceName%2A> spécifier un <xref:System.Windows.EventTrigger> pour un <xref:System.Windows.Trigger>ou un.

- Vous ne pouvez pas utiliser des références de ressources dynamiques ou des <xref:System.Windows.Media.Animation.Storyboard> expressions de liaison de données pour définir ou animations des valeurs de propriété. Cela est dû au fait que <xref:System.Windows.Style> tout ce qui se trouve dans un doit être thread- <xref:System.Windows.Freezable.Freeze%2A> safe et que le système de minutage doit <xref:System.Windows.Media.Animation.Storyboard> les objets pour les rendre thread-safe. Un <xref:System.Windows.Media.Animation.Storyboard> ne peut pas être figé s’il ou ses chronologies enfants contiennent des références de ressources dynamiques ou des expressions de liaison de données. Pour plus d’informations sur le gel <xref:System.Windows.Freezable> et d’autres fonctionnalités, consultez la [vue d’ensemble des objets Freezable](../advanced/freezable-objects-overview.md).

- Dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], vous ne pouvez pas déclarer de gestionnaires <xref:System.Windows.Media.Animation.Storyboard> d’événements pour les événements d’animation ou.

Pour obtenir un exemple qui montre comment définir une table de montage séquentiel dans un style, consultez l’exemple [animer dans un style](how-to-animate-in-a-style.md) .

<a name="defineAStoryboardInAControlTemplateSection"></a>

## <a name="animate-in-a-controltemplate"></a>Effectuer une animation dans un ControlTemplate

Vous pouvez utiliser <xref:System.Windows.Media.Animation.Storyboard> des objets pour définir des animations <xref:System.Windows.Controls.ControlTemplate>dans un. L’animation avec un <xref:System.Windows.Media.Animation.Storyboard> dans un <xref:System.Windows.Controls.ControlTemplate> est semblable à l’utilisation <xref:System.Windows.Media.Animation.Storyboard> d’un autre emplacement, avec les deux exceptions suivantes :

- Peut uniquement faire référence aux objets enfants <xref:System.Windows.Controls.ControlTemplate>de. <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> Si <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> n’est pas spécifié, l’animation cible l’élément <xref:System.Windows.Controls.ControlTemplate> auquel est appliqué.

- Pour un <xref:System.Windows.EventTrigger> ou un<xref:System.Windows.Trigger> peut uniquement faire référence aux objets enfants de. <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.EventTrigger.SourceName%2A>

- Vous ne pouvez pas utiliser des références de ressources dynamiques ou des <xref:System.Windows.Media.Animation.Storyboard> expressions de liaison de données pour définir ou animations des valeurs de propriété. Cela est dû au fait que <xref:System.Windows.Controls.ControlTemplate> tout ce qui se trouve dans un doit être thread- <xref:System.Windows.Freezable.Freeze%2A> safe et que le système de minutage doit <xref:System.Windows.Media.Animation.Storyboard> les objets pour les rendre thread-safe. Un <xref:System.Windows.Media.Animation.Storyboard> ne peut pas être figé s’il ou ses chronologies enfants contiennent des références de ressources dynamiques ou des expressions de liaison de données. Pour plus d’informations sur le gel <xref:System.Windows.Freezable> et d’autres fonctionnalités, consultez la [vue d’ensemble des objets Freezable](../advanced/freezable-objects-overview.md).

- Dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], vous ne pouvez pas déclarer de gestionnaires <xref:System.Windows.Media.Animation.Storyboard> d’événements pour les événements d’animation ou.

Pour obtenir un exemple illustrant comment définir une table de <xref:System.Windows.Controls.ControlTemplate>montage séquentiel dans un, consultez l’exemple [animation dans un ControlTemplate](how-to-animate-in-a-controltemplate.md) .

<a name="animateWhenAPropertyValueChanges"></a>

## <a name="animate-when-a-property-value-changes"></a>Animer en cas de modification d’une valeur de propriété

Dans les styles et les modèles de contrôle, vous pouvez utiliser des objets Trigger pour démarrer une table de montage séquentiel en cas de modification d’une propriété. Pour obtenir des exemples, consultez [déclencher une animation quand une valeur de propriété change](how-to-trigger-an-animation-when-a-property-value-changes.md) et [animer dans un ControlTemplate](how-to-animate-in-a-controltemplate.md).

Les animations appliquées par <xref:System.Windows.Trigger> les objets de propriété se comportent <xref:System.Windows.EventTrigger> de manière plus complexe que <xref:System.Windows.Media.Animation.Storyboard> les animations ou les animations démarrées à l’aide de méthodes.  Ils « sont remis » avec les animations définies <xref:System.Windows.Trigger> par d’autres objets, mais <xref:System.Windows.EventTrigger> composent avec les animations déclenchées par la méthode et.

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de l’animation](animation-overview.md)
- [Vue d’ensemble des techniques d’animation de propriétés](property-animation-techniques-overview.md)
- [Vue d’ensemble des objets Freezable](../advanced/freezable-objects-overview.md)
