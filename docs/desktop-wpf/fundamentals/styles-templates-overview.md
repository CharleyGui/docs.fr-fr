---
title: Styles et modèles
description: En savoir plus sur les ressources XAML dans Windows Presentation Foundation (WPF) pour .NET Core. Comprendre les types de ressources XAML liées aux styles et aux thèmes.
author: thraka
ms.author: adegeo
ms.date: 09/09/2019
dev_langs:
- csharp
- vb
ms.openlocfilehash: f845e739ec3cae502d1e4fd6631f987c5364a42e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "82071884"
---
# <a name="styles-and-templates-in-wpf"></a>Styles et modèles dans WPF

Le style et le templating de la Windows Presentation Foundation (WPF) se réfèrent à une suite de fonctionnalités qui permettent aux développeurs et aux concepteurs de créer des effets visuellement convaincants et une apparence cohérente pour leur produit. Lorsque vous personnalisez l’apparence d’une application, vous voulez un solide style et un modèle de templating qui permet la maintenance et le partage de l’apparence à l’intérieur et entre les applications. WPF fournit ce modèle.

Une autre caractéristique du modèle de style WPF est la séparation de la présentation et de la logique. Les concepteurs peuvent travailler sur l’apparence d’une application en utilisant uniquement XAML en même temps que les développeurs travaillent sur la logique de programmation en utilisant C ou Visual Basic.

Cette vue d’ensemble se concentre sur le style et les aspects de l’application et ne traite pas de concepts de liaison de données. Pour plus d’informations sur la liaison de données, consultez [Vue d’ensemble de la liaison de données](../data/data-binding-overview.md).

Il est important de comprendre les ressources, qui sont ce qui permet de réutiliser les styles et les modèles. Pour plus d’informations sur les ressources, consultez [Ressources XAML](xaml-resources-define.md).

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="sample"></a>Exemple

Le code de l’échantillon fourni dans cette vue [d’ensemble](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating) est basé sur une simple application de navigation photo montrée dans l’illustration suivante.

![Vue de la liste mise en forme avec des styles](./media/styles-and-templates-overview/stylingintro-triggers.png "StylingIntro_triggers")

Cet exemple de photo simple utilise des styles et des modèles pour créer une expérience utilisateur visuellement attrayante. L’échantillon <xref:System.Windows.Controls.TextBlock> a deux <xref:System.Windows.Controls.ListBox> éléments et un contrôle qui est lié à une liste d’images.

Pour accéder à l’exemple complet, consultez la page [Introduction to Styling and Templating Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating) (Présentation d’un exemple de création de style et de modèle).

## <a name="styles"></a>Styles

Vous pouvez penser <xref:System.Windows.Style> à un moyen pratique d’appliquer un ensemble de valeurs de propriété à plusieurs éléments. Vous pouvez utiliser un style sur <xref:System.Windows.FrameworkElement> n’importe quel élément qui dérive ou <xref:System.Windows.FrameworkContentElement> tel que un <xref:System.Windows.Window> ou un <xref:System.Windows.Controls.Button>.

La façon la plus courante de déclarer `Resources` un style est comme une ressource dans la section dans un fichier XAML. Parce que les styles sont des ressources, ils obéissent aux mêmes règles de portée qui s’appliquent à toutes les ressources. En d’autres termes, où vous déclarez qu’un style affecte l’endroit où le style peut être appliqué. Par exemple, si vous déclarez le style dans l’élément racine de votre fichier XAML de définition d’application, le style peut être utilisé n’importe où dans votre application.

Par exemple, le code XAML suivant `TextBlock`déclare deux styles `TextBlock` pour un, l’un automatiquement appliqué à tous les éléments, et l’autre qui doit être explicitement référencé.

[!code-xaml[SnippetDefaultTextBlockStyleBasedOn](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window2.xaml#SnippetDefaultTextBlockStyleBasedOn)]

Voici un exemple des styles déclarés ci-dessus utilisés.

[!code-xaml[SnippetTextBlocksExplicit](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window2.xaml#SnippetTextBlocksExplicit)]

![Blocs de texte stylés](./media/styles-and-templates-overview/stylingintro-textblocks.png)

Pour plus d’informations, voir [Créer un style pour un contrôle](styles-templates-create-apply-style.md).

## <a name="controltemplates"></a>ControlTemplates

Dans WPF, <xref:System.Windows.Controls.ControlTemplate> le contrôle définit l’apparence du contrôle. Vous pouvez modifier la structure et l’apparence d’un contrôle en définissant un nouveau <xref:System.Windows.Controls.ControlTemplate> et en l’assignant à un contrôle. Dans de nombreux cas, les modèles vous donnent suffisamment de flexibilité pour ne pas avoir à écrire vos propres contrôles personnalisés.

Chaque contrôle a un modèle par défaut attribué à la propriété [Control.Template.](xref:System.Windows.Controls.Control.Template) Le modèle relie la présentation visuelle du contrôle avec les capacités du contrôle. Parce que vous définissez un modèle dans XAML, vous pouvez modifier l’apparence du contrôle sans écrire de code. Chaque modèle est conçu pour un <xref:System.Windows.Controls.Button>contrôle spécifique, tel qu’un .

Généralement, vous déclarez un `Resources` modèle comme une ressource sur la section d’un fichier XAML. Comme pour toutes les ressources, les règles de portée s’appliquent.

Les modèles de contrôle sont beaucoup plus impliqués qu’un style. C’est parce que le modèle de contrôle réécrit l’apparence visuelle de l’ensemble du contrôle, tandis qu’un style applique simplement des changements de propriété au contrôle existant. Cependant, puisque le modèle d’un contrôle est appliqué en définissant la propriété [Control.Template,](xref:System.Windows.Controls.Control.Template) vous pouvez utiliser un style pour définir ou définir un modèle.

Les concepteurs vous permettent généralement de créer une copie d’un modèle existant et de le modifier. Par exemple, dans le visual Studio `CheckBox` WPF designer, sélectionnez un contrôle, puis cliquez à droite et sélectionnez **Modifier le modèle** > **Créer une copie**. Cette commande génère un *style qui définit un modèle*.

```xaml
<Style x:Key="CheckBoxStyle1" TargetType="{x:Type CheckBox}">
    <Setter Property="FocusVisualStyle" Value="{StaticResource FocusVisual1}"/>
    <Setter Property="Background" Value="{StaticResource OptionMark.Static.Background1}"/>
    <Setter Property="BorderBrush" Value="{StaticResource OptionMark.Static.Border1}"/>
    <Setter Property="Foreground" Value="{DynamicResource {x:Static SystemColors.ControlTextBrushKey}}"/>
    <Setter Property="BorderThickness" Value="1"/>
    <Setter Property="Template">
        <Setter.Value>
            <ControlTemplate TargetType="{x:Type CheckBox}">
                <Grid x:Name="templateRoot" Background="Transparent" SnapsToDevicePixels="True">
                    <Grid.ColumnDefinitions>
                        <ColumnDefinition Width="Auto"/>
                        <ColumnDefinition Width="*"/>
                    </Grid.ColumnDefinitions>
                    <Border x:Name="checkBoxBorder" Background="{TemplateBinding Background}" BorderThickness="{TemplateBinding BorderThickness}" BorderBrush="{TemplateBinding BorderBrush}" HorizontalAlignment="{TemplateBinding HorizontalContentAlignment}" Margin="1" VerticalAlignment="{TemplateBinding VerticalContentAlignment}">
                        <Grid x:Name="markGrid">
                            <Path x:Name="optionMark" Data="F1 M 9.97498,1.22334L 4.6983,9.09834L 4.52164,9.09834L 0,5.19331L 1.27664,3.52165L 4.255,6.08833L 8.33331,1.52588e-005L 9.97498,1.22334 Z " Fill="{StaticResource OptionMark.Static.Glyph1}" Margin="1" Opacity="0" Stretch="None"/>
                            <Rectangle x:Name="indeterminateMark" Fill="{StaticResource OptionMark.Static.Glyph1}" Margin="2" Opacity="0"/>
                        </Grid>
                    </Border>
                    <ContentPresenter x:Name="contentPresenter" Grid.Column="1" Focusable="False" HorizontalAlignment="{TemplateBinding HorizontalContentAlignment}" Margin="{TemplateBinding Padding}" RecognizesAccessKey="True" SnapsToDevicePixels="{TemplateBinding SnapsToDevicePixels}" VerticalAlignment="{TemplateBinding VerticalContentAlignment}"/>
                </Grid>
                <ControlTemplate.Triggers>
                    <Trigger Property="HasContent" Value="true">
                        <Setter Property="FocusVisualStyle" Value="{StaticResource OptionMarkFocusVisual1}"/>
                        <Setter Property="Padding" Value="4,-1,0,0"/>

... content removed to save space ...
```

L’édition d’une copie d’un modèle est un excellent moyen d’apprendre comment fonctionnent les modèles. Au lieu de créer un nouveau modèle vierge, il est plus facile de modifier une copie et de modifier quelques aspects de la présentation visuelle.

Par exemple, voir [Créer un modèle pour un contrôle](../themes/how-to-create-apply-template.md).

### <a name="templatebinding"></a>TemplateBinding

Vous avez peut-être remarqué que la ressource de modèle définie dans la section précédente utilise [l’extension de markup TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md). A `TemplateBinding` est une forme optimisée d’une liaison pour les `{Binding RelativeSource={RelativeSource TemplatedParent}}`scénarios de modèle, analogue à une liaison construite avec . `TemplateBinding`est utile pour lier des parties du modèle aux propriétés du contrôle. Par exemple, chaque <xref:System.Windows.Controls.Control.BorderThickness> contrôle a une propriété. Utilisez `TemplateBinding` un pour gérer quel élément du modèle est affecté par ce paramètre de contrôle.

### <a name="contentcontrol-and-itemscontrol"></a>ContentControl et ItemsControl

Si <xref:System.Windows.Controls.ContentPresenter> un est <xref:System.Windows.Controls.ControlTemplate> déclaré <xref:System.Windows.Controls.ContentControl>dans <xref:System.Windows.Controls.ContentPresenter> le d’un <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> <xref:System.Windows.Controls.ContentControl.Content%2A> , le se lient automatiquement à la et les propriétés. De même, <xref:System.Windows.Controls.ItemsPresenter> un <xref:System.Windows.Controls.ControlTemplate> qui <xref:System.Windows.Controls.ItemsControl> est dans le <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> <xref:System.Windows.Controls.ItemsControl.Items%2A> d’un volonté se lient automatiquement à la et les propriétés.

## <a name="datatemplates"></a>Datatemplates

Dans cette application d’échantillon, il y a un <xref:System.Windows.Controls.ListBox> contrôle qui est lié à une liste de photos.

[!code-xaml[ListBox](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window3.xaml#SnippetListBox)]

Cela <xref:System.Windows.Controls.ListBox> ressemble actuellement à ce qui suit.

![ListBox avant application du modèle](./media/styles-and-templates-overview/stylingintro-listboxbefore.png "StylingIntro_ListBoxBefore")

La plupart des contrôles ont un type de contenu, et ce contenu provient souvent des données que vous liez à ces contrôles. Dans cet exemple, les données sont la liste de photos. Dans WPF, vous <xref:System.Windows.DataTemplate> utilisez un pour définir la représentation visuelle des données. Fondamentalement, ce que <xref:System.Windows.DataTemplate> vous mettez dans un détermine à quoi ressemblent les données dans l’application rendue.

Dans notre application d’échantillon, chaque objet personnalisé `Photo` a une `Source` propriété de chaîne de type qui spécifie le chemin de fichier de l’image. Actuellement, les objets photo apparaissent sous forme de chemins d’accès.

[!code-csharp[PhotoClass](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Photo.cs#PhotoClass)]
[!code-vb[PhotoClass](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/vb/Photo.vb#PhotoClass)]

Pour que les photos apparaissent sous <xref:System.Windows.DataTemplate> forme d’images, vous créez une ressource.

[!code-xaml[DataTemplate](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window4.xaml#SnippetDataTemplate)]

Notez <xref:System.Windows.DataTemplate.DataType%2A> que la propriété <xref:System.Windows.Style.TargetType%2A> est <xref:System.Windows.Style>similaire à la propriété de la . Si <xref:System.Windows.DataTemplate> vous êtes dans la section <xref:System.Windows.DataTemplate.DataType%2A> ressources, lorsque vous spécifiez la propriété à un type et ometez un `x:Key`, le <xref:System.Windows.DataTemplate> est appliqué chaque fois que ce type apparaît. Vous avez toujours la <xref:System.Windows.DataTemplate> possibilité `x:Key` d’attribuer le `StaticResource` avec un, <xref:System.Windows.DataTemplate> puis le <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> définir comme <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> un pour les propriétés qui prennent des types, tels que la propriété ou la propriété.

Essentiellement, <xref:System.Windows.DataTemplate> l’exemple ci-dessus définit que `Photo` chaque fois qu’il ya un objet, il doit apparaître comme un <xref:System.Windows.Controls.Image> dans un <xref:System.Windows.Controls.Border>. Avec <xref:System.Windows.DataTemplate>cela, notre application ressemble maintenant à ceci.

![Image photo](./media/styles-and-templates-overview/stylingintro-photosasimages.png "StylingIntro_PhotosAsImages")

Le modèle de création de modèles fournit d’autres fonctionnalités. Par exemple, si vous affichez des données <xref:System.Windows.Controls.HeaderedItemsControl> de collecte <xref:System.Windows.Controls.Menu> qui <xref:System.Windows.Controls.TreeView>contiennent d’autres collections à l’aide d’un type tel que a ou a , il ya le <xref:System.Windows.HierarchicalDataTemplate>. Une autre fonctionnalité de <xref:System.Windows.Controls.DataTemplateSelector>templating de données <xref:System.Windows.DataTemplate> est le , qui vous permet de choisir un à utiliser en fonction de la logique personnalisée. Pour plus d’informations, consultez l’article [Vue d'ensemble des modèles de données](../../framework/wpf/data/data-templating-overview.md), qui fournit une discussion plus approfondie sur les différentes fonctionnalités de création de modèles de données.

## <a name="triggers"></a>Déclencheurs

Un déclencheur définit des propriétés ou démarre des actions, par exemple une animation, lorsqu’une valeur de propriété change ou lorsqu’un événement est déclenché. <xref:System.Windows.Style>, <xref:System.Windows.Controls.ControlTemplate>et <xref:System.Windows.DataTemplate> tous `Triggers` ont une propriété qui peut contenir un ensemble de déclencheurs. Il existe plusieurs types de déclencheurs.

### <a name="propertytriggers"></a>PropriétéTriggers

Un <xref:System.Windows.Trigger> qui établit la valeur de propriété ou commence des actions basées sur la valeur d’une propriété est appelé un déclencheur de propriété.

Pour démontrer comment utiliser les déclencheurs <xref:System.Windows.Controls.ListBoxItem> de propriété, vous pouvez rendre chacun partiellement transparent à moins qu’il ne soit sélectionné. Le style suivant <xref:System.Windows.UIElement.Opacity%2A> définit <xref:System.Windows.Controls.ListBoxItem> la `0.5`valeur d’un à . Lorsque <xref:System.Windows.Controls.ListBoxItem.IsSelected%2A> la `true`propriété est, <xref:System.Windows.UIElement.Opacity%2A> cependant, `1.0`le est réglé à .

[!code-xaml[PropertyTrigger](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window5.xaml#SnippetPropertyTrigger)]

Cet exemple <xref:System.Windows.Trigger> utilise un pour définir une <xref:System.Windows.Trigger> valeur de <xref:System.Windows.TriggerBase.EnterActions%2A> propriété, mais notez que la classe a également le et <xref:System.Windows.TriggerBase.ExitActions%2A> les propriétés qui permettent à un déclencheur d’effectuer des actions.

Notez <xref:System.Windows.FrameworkElement.MaxHeight%2A> que la <xref:System.Windows.Controls.ListBoxItem> propriété `75`de la est définie à . Dans l’illustration suivante, le troisième élément est l’élément sélectionné.

![Vue de la liste mise en forme avec des styles](./media/styles-and-templates-overview/stylingintro-triggers.png "StylingIntro_triggers")

### <a name="eventtriggers-and-storyboards"></a>EventTriggers et tables de montage séquentiel

Un autre type <xref:System.Windows.EventTrigger>de déclencheur est le , qui commence un ensemble d’actions basées sur l’occurrence d’un événement. Par exemple, <xref:System.Windows.EventTrigger> les objets suivants spécifient que lorsque le pointeur de la souris entre dans le <xref:System.Windows.Controls.ListBoxItem>, la <xref:System.Windows.FrameworkElement.MaxHeight%2A> propriété est animée à une valeur de plus d’une `90` `0.2` deuxième période. Lorsque la souris s’éloigne de l’élément, la propriété retourne à sa valeur d’origine pendant une période de `1` seconde. Notez comment il n’est pas nécessaire de spécifier une <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> valeur pour l’animation. <xref:System.Windows.ContentElement.MouseLeave> L’animation est en effet capable d’effectuer le suivi de la valeur d’origine.

[!code-xaml[StyleEventTriggers](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window6.xaml#SnippetStyleEventTriggers)]

Pour plus d’informations, voir la [vue d’ensemble Storyboards](../../framework/wpf/graphics-multimedia/storyboards-overview.md).

Dans l’illustration suivante, la souris pointe vers le troisième élément.

![Capture d’écran d’échantillon de style](./media/styles-and-templates-overview/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")

### <a name="multitriggers-datatriggers-and-multidatatriggers"></a>MultiTriggers, DataTriggers et MultiDataTriggers

En plus <xref:System.Windows.Trigger> <xref:System.Windows.EventTrigger>de et , il existe d’autres types de déclencheurs. <xref:System.Windows.MultiTrigger>vous permet de définir les valeurs de propriété en fonction de plusieurs conditions. Vous <xref:System.Windows.DataTrigger> utilisez <xref:System.Windows.MultiDataTrigger> et lorsque la propriété de votre état est liée aux données.

## <a name="visual-states"></a>États visuels

Les contrôles sont toujours dans un **état**spécifique . Par exemple, lorsque la souris se déplace sur la surface d’un `MouseOver`contrôle, le contrôle est considéré comme étant dans un état commun de . Un contrôle sans état spécifique est considéré `Normal` comme étant dans l’état commun. Les États sont divisés en groupes, et les `CommonStates`États mentionnés précédemment font partie du groupe d’État . La plupart des contrôles `CommonStates` `FocusStates`ont deux groupes d’État: et . De chaque groupe d’État appliqué à un contrôle, un contrôle `CommonStates.MouseOver` `FocusStates.Unfocused`est toujours dans un état de chaque groupe, tel que et . Cependant, un contrôle ne peut pas être dans deux `CommonStates.Normal` états `CommonStates.Disabled`différents au sein d’un même groupe, tels que et . Voici un tableau des États que la plupart des contrôles reconnaissent et utilisent.

| Nom VisualState | Nom VisualStateGroup | Description |
| ---------------- | --------------------- | ----------- |
| Normal           | CommonStates          | État par défaut. |
| MouseOver        | CommonStates          | Le pointeur de souris est positionné sur le contrôle. |
| Appuyé          | CommonStates          | Le contrôle est enfoncé. |
| Désactivé         | CommonStates          | Le contrôle est désactivé. |
| Avec focus          | FocusStates           | Le contrôle a le focus. |
| Sans focus        | FocusStates           | Le contrôle n’a pas le focus. |

En définissant un <xref:System.Windows.VisualStateManager?displayProperty=fullName> élément sur la racine d’un modèle de contrôle, vous pouvez déclencher des animations lorsqu’un contrôle entre dans un état spécifique. Le `VisualStateManager` déclare quelles combinaisons et <xref:System.Windows.VisualStateGroup> <xref:System.Windows.VisualState> à regarder. Lorsque le contrôle entre dans un état `VisaulStateManager` surveillé, l’animation définie par le est commencé.

Par exemple, le code XAML suivant surveille l’état `CommonStates.MouseOver` pour `backgroundElement`animer la couleur de remplissage de l’élément nommé . Lorsque le contrôle `CommonStates.Normal` retourne à l’état, `backgroundElement` la couleur de remplissage de l’élément nommé est restaurée.

```xaml
<ControlTemplate x:Key="roundbutton" TargetType="Button">
    <Grid>
        <VisualStateManager.VisualStateGroups>
            <VisualStateGroup Name="CommonStates">
                <VisualState Name="Normal">
                    <ColorAnimation Storyboard.TargetName="backgroundElement"
                                    Storyboard.TargetProperty="(Shape.Fill).(SolidColorBrush.Color)"
                                    To="{TemplateBinding Background}"
                                    Duration="0:0:0.3"/>
                </VisualState>
                <VisualState Name="MouseOver">
                    <ColorAnimation Storyboard.TargetName="backgroundElement"
                                    Storyboard.TargetProperty="(Shape.Fill).(SolidColorBrush.Color)"
                                    To="Yellow"
                                    Duration="0:0:0.3"/>
                </VisualState>
            </VisualStateGroup>
        </VisualStateManager.VisualStateGroups>

        ...
```

Pour plus d’informations sur les storyboards, voir [Storyboards Aperçu](../../framework/wpf/graphics-multimedia/storyboards-overview.md).

## <a name="shared-resources-and-themes"></a>Ressources et thèmes partagés

Une application WPF typique peut avoir plusieurs ressources d’interface utilisateur qui sont appliquées dans l’ensemble de l’application. Collectivement, cet ensemble de ressources peut être considéré comme le thème de l’application. WPF fournit un soutien pour l’emballage des ressources d’interface utilisateur <xref:System.Windows.ResourceDictionary> comme un thème en utilisant un dictionnaire de ressources qui est encapsulé comme la classe.

Les thèmes WPF sont définis en utilisant le mécanisme de style et de templating que WPF expose pour personnaliser les visuels de n’importe quel élément.

Les ressources thématiques du WPF sont stockées dans des dictionnaires de ressources intégrés. Ces dictionnaires de ressources doivent être incorporés dans un assembly signé, et peuvent être incorporés dans le même assembly que le code lui-même, ou bien dans un assembly parallèle. Pour PresentationFramework.dll, l’assemblage qui contient des contrôles WPF, les ressources thématiques sont dans une série d’assemblages côte à côte.

Le thème est alors le dernier emplacement à consulter lors de la recherche du style d’un élément. Typiquement, la recherche commencera par marcher jusqu’à l’arbre élément à la recherche d’une ressource appropriée, puis regarder dans la collecte des ressources de l’application et enfin interroger le système. Cela donne aux développeurs d’applications une chance de redéfinir le style de tout objet au niveau de l’arbre ou de l’application avant d’atteindre le thème.

Vous pouvez définir les dictionnaires de ressources comme des fichiers individuels qui vous permettent de réutiliser un thème sur plusieurs applications. Vous pouvez également créer des thèmes permutables en définissant plusieurs dictionnaires de ressources qui fournissent les mêmes types de ressources mais avec des valeurs différentes. Redéfinir ces styles ou d’autres ressources au niveau de l’application est l’approche recommandée pour dépecer une application.

Pour partager un ensemble de ressources, y compris des styles et des modèles, <xref:System.Windows.ResourceDictionary> entre les `shared.xaml` applications, vous pouvez créer un fichier XAML et définir un qui inclut la référence à un fichier.

```xaml
<ResourceDictionary.MergedDictionaries>
  <ResourceDictionary Source="Shared.xaml" />
</ResourceDictionary.MergedDictionaries>
```

C’est le `shared.xaml`partage de , <xref:System.Windows.ResourceDictionary> qui définit lui-même un qui contient un ensemble de ressources de style et de pinceau, qui permet aux contrôles dans une application d’avoir un look cohérent.

Pour plus d’informations, voir [dictionnaires de ressources fusionnés](../../framework/wpf/advanced/merged-resource-dictionaries.md).

Si vous créez un thème pour votre contrôle personnalisé, consultez les **ressources De définition à la** section thème de l’aperçu de [l’auteur de contrôle](../../framework/wpf/controls/control-authoring-overview.md#defining-resources-at-the-theme-level).

## <a name="see-also"></a>Voir aussi

- [URI à en-tête pack dans WPF](../../framework/wpf/app-development/pack-uris-in-wpf.md)
- [Guide pratique pour rechercher des éléments générés par ControlTemplate](../../framework/wpf/controls/how-to-find-controltemplate-generated-elements.md)
- [Trouver des éléments générés par DataTemplate](../../framework/wpf/data/how-to-find-datatemplate-generated-elements.md)
