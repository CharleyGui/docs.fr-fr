---
title: Styles et modèles
description: En savoir plus sur les ressources XAML dans Windows Presentation Foundation (WPF) pour .NET Core. Comprendre les types de ressources XAML en rapport avec les styles et les thèmes.
author: adegeo
ms.author: adegeo
ms.date: 09/09/2019
dev_langs:
- csharp
- vb
ms.openlocfilehash: 61cddfeb0d881ad2f2006db50ebb33f6a0c870ba
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90535434"
---
# <a name="styles-and-templates-in-wpf"></a>Styles et modèles dans WPF

Le style et la création de modèles de Windows Presentation Foundation (WPF) font référence à une suite de fonctionnalités qui permettent aux développeurs et aux concepteurs de créer des effets visuellement attrayants et une apparence cohérente pour leur produit. Lors de la personnalisation de l’apparence d’une application, vous voulez un modèle de création de styles et de modèles puissant qui permet la maintenance et le partage de l’apparence dans et entre les applications. WPF fournit ce modèle.

Une autre fonctionnalité du modèle de style WPF est la séparation de la présentation et de la logique. Les concepteurs peuvent travailler sur l’apparence d’une application en utilisant uniquement XAML en même temps que les développeurs travaillent sur la logique de programmation à l’aide de C# ou de Visual Basic.

Cette présentation se concentre sur les aspects de style et de création de modèles de l’application et n’aborde pas les concepts de liaison de données. Pour plus d’informations sur la liaison de données, consultez [Vue d’ensemble de la liaison de données](../data/data-binding-overview.md).

Il est important de comprendre les ressources, ce qui permet de réutiliser les styles et les modèles. Pour plus d’informations sur les ressources, consultez [Ressources XAML](xaml-resources-define.md).

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="sample"></a>Exemple

L’exemple de code fourni dans cette vue d’ensemble est basé sur une [simple application de navigation photo](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating) présentée dans l’illustration suivante.

![Vue de la liste mise en forme avec des styles](./media/styles-and-templates-overview/stylingintro-triggers.png "StylingIntro_triggers")

Cet exemple de photo simple utilise des styles et des modèles pour créer une expérience utilisateur visuellement attrayante. L’exemple comporte deux <xref:System.Windows.Controls.TextBlock> éléments et un <xref:System.Windows.Controls.ListBox> contrôle qui est lié à une liste d’images.

Pour accéder à l’exemple complet, consultez la page [Introduction to Styling and Templating Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating) (Présentation d’un exemple de création de style et de modèle).

## <a name="styles"></a>Styles

Vous pouvez considérer comme un <xref:System.Windows.Style> moyen pratique d’appliquer un ensemble de valeurs de propriété à plusieurs éléments. Vous pouvez utiliser un style sur tout élément qui dérive de <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement> tel qu’un <xref:System.Windows.Window> ou un <xref:System.Windows.Controls.Button> .

La méthode la plus courante pour déclarer un style est la ressource dans la `Resources` section d’un fichier XAML. Étant donné que les styles sont des ressources, ils obéissent aux mêmes règles de portée qui s’appliquent à toutes les ressources. En d’autres termes, lorsque vous déclarez un style affecte l’endroit où le style peut être appliqué. Par exemple, si vous déclarez le style dans l’élément racine de votre fichier XAML de définition d’application, le style peut être utilisé n’importe où dans votre application.

Par exemple, le code XAML suivant déclare deux styles pour un `TextBlock` , un appliqué automatiquement à tous les `TextBlock` éléments, et un autre qui doit être explicitement référencé.

[!code-xaml[SnippetDefaultTextBlockStyleBasedOn](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window2.xaml#SnippetDefaultTextBlockStyleBasedOn)]

Voici un exemple des styles déclarés ci-dessus en cours d’utilisation.

[!code-xaml[SnippetTextBlocksExplicit](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window2.xaml#SnippetTextBlocksExplicit)]

![TextBlocks stylisés](./media/styles-and-templates-overview/stylingintro-textblocks.png)

Pour plus d’informations, consultez [créer un style pour un contrôle](styles-templates-create-apply-style.md).

## <a name="controltemplates"></a>ControlTemplates

Dans WPF, le <xref:System.Windows.Controls.ControlTemplate> d’un contrôle définit l’apparence du contrôle. Vous pouvez modifier la structure et l’apparence d’un contrôle en définissant un nouveau et en l' <xref:System.Windows.Controls.ControlTemplate> assignant à un contrôle. Dans de nombreux cas, les modèles vous offrent suffisamment de souplesse pour que vous n’ayez pas à écrire vos propres contrôles personnalisés.

Chaque contrôle a un modèle par défaut affecté à la propriété [Control. Template](xref:System.Windows.Controls.Control.Template) . Le modèle connecte la présentation visuelle du contrôle avec les fonctionnalités du contrôle. Étant donné que vous définissez un modèle en XAML, vous pouvez modifier l’apparence du contrôle sans écrire de code. Chaque modèle est conçu pour un contrôle spécifique, tel qu’un <xref:System.Windows.Controls.Button> .

En général, vous déclarez un modèle en tant que ressource dans la `Resources` section d’un fichier XAML. Comme avec toutes les ressources, les règles de portée s’appliquent.

Les modèles de contrôle sont beaucoup plus impliqués qu’un style. Cela est dû au fait que le modèle de contrôle réécrit l’apparence visuelle de l’ensemble du contrôle, tandis qu’un style applique simplement des modifications de propriétés au contrôle existant. Toutefois, étant donné que le modèle d’un contrôle est appliqué en définissant la propriété [Control. Template](xref:System.Windows.Controls.Control.Template) , vous pouvez utiliser un style pour définir ou définir un modèle.

Les concepteurs vous permettent généralement de créer une copie d’un modèle existant et de le modifier. Par exemple, dans le Concepteur WPF Visual Studio, sélectionnez un `CheckBox` contrôle, puis cliquez avec le bouton droit et sélectionnez **modifier le modèle**  >  **créer une copie**. Cette commande génère un *style qui définit un modèle*.

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

La modification d’une copie d’un modèle est un excellent moyen d’apprendre comment les modèles fonctionnent. Au lieu de créer un nouveau modèle vide, il est plus facile de modifier une copie et de modifier quelques aspects de la présentation visuelle.

Pour obtenir un exemple, consultez [créer un modèle pour un contrôle](../themes/how-to-create-apply-template.md).

### <a name="templatebinding"></a>TemplateBinding

Vous avez peut-être remarqué que la ressource de modèle définie dans la section précédente utilise l' [extension de balisage TemplateBinding](/dotnet/desktop/wpf/advanced/templatebinding-markup-extension). Un `TemplateBinding` est une forme optimisée d’une liaison pour les scénarios de modèle, analogue à une liaison construite avec `{Binding RelativeSource={RelativeSource TemplatedParent}}` . `TemplateBinding` est utile pour lier des parties du modèle aux propriétés du contrôle. Par exemple, chaque contrôle possède une <xref:System.Windows.Controls.Control.BorderThickness> propriété. Utilisez un `TemplateBinding` pour gérer l’élément affecté par ce paramètre de contrôle à l’élément du modèle.

### <a name="contentcontrol-and-itemscontrol"></a>ContentControl et ItemsControl

Si un <xref:System.Windows.Controls.ContentPresenter> est déclaré dans le <xref:System.Windows.Controls.ControlTemplate> d’un <xref:System.Windows.Controls.ContentControl> , le crée <xref:System.Windows.Controls.ContentPresenter> automatiquement une liaison avec <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> les <xref:System.Windows.Controls.ContentControl.Content%2A> Propriétés et. De même, un <xref:System.Windows.Controls.ItemsPresenter> qui se trouve dans le <xref:System.Windows.Controls.ControlTemplate> d’un crée <xref:System.Windows.Controls.ItemsControl> automatiquement une liaison avec les <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> <xref:System.Windows.Controls.ItemsControl.Items%2A> Propriétés et.

## <a name="datatemplates"></a>DataTemplates

Dans cet exemple d’application, un <xref:System.Windows.Controls.ListBox> contrôle est lié à une liste de photos.

[!code-xaml[ListBox](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window3.xaml#SnippetListBox)]

Cela <xref:System.Windows.Controls.ListBox> ressemble à ce qui suit.

![ListBox avant application du modèle](./media/styles-and-templates-overview/stylingintro-listboxbefore.png "StylingIntro_ListBoxBefore")

La plupart des contrôles ont un type de contenu, et ce contenu provient souvent des données que vous liez à ces contrôles. Dans cet exemple, les données sont la liste de photos. Dans WPF, vous utilisez un <xref:System.Windows.DataTemplate> pour définir la représentation visuelle des données. Fondamentalement, ce que vous placez dans un <xref:System.Windows.DataTemplate> détermine à quoi ressemblent les données dans l’application rendue.

Dans notre exemple d’application, chaque `Photo` objet personnalisé a une `Source` propriété de type chaîne qui spécifie le chemin d’accès de l’image. Actuellement, les objets photo apparaissent sous forme de chemins d’accès.

[!code-csharp[PhotoClass](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Photo.cs#PhotoClass)]
[!code-vb[PhotoClass](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/vb/Photo.vb#PhotoClass)]

Pour que les photos apparaissent en tant qu’images, vous créez une <xref:System.Windows.DataTemplate> en tant que ressource.

[!code-xaml[DataTemplate](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window4.xaml#SnippetDataTemplate)]

Notez que la <xref:System.Windows.DataTemplate.DataType%2A> propriété est semblable à la <xref:System.Windows.Style.TargetType%2A> propriété de <xref:System.Windows.Style> . Si votre <xref:System.Windows.DataTemplate> se trouve dans la section des ressources, lorsque vous spécifiez la <xref:System.Windows.DataTemplate.DataType%2A> propriété d’un type et que vous omettez un `x:Key` , le <xref:System.Windows.DataTemplate> est appliqué chaque fois que ce type apparaît. Vous avez toujours la possibilité d’assigner le <xref:System.Windows.DataTemplate> à un, `x:Key` puis de le définir comme `StaticResource` pour les propriétés qui acceptent des <xref:System.Windows.DataTemplate> types, telles que la <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> propriété ou la <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> propriété.

Fondamentalement, le <xref:System.Windows.DataTemplate> dans l’exemple ci-dessus définit qu’à chaque fois qu’il y a un `Photo` objet, il doit apparaître comme un <xref:System.Windows.Controls.Image> dans un <xref:System.Windows.Controls.Border> . Avec cela <xref:System.Windows.DataTemplate> , notre application se présente maintenant comme suit.

![Image photo](./media/styles-and-templates-overview/stylingintro-photosasimages.png "StylingIntro_PhotosAsImages")

Le modèle de création de modèles fournit d’autres fonctionnalités. Par exemple, si vous affichez des données de collection qui contiennent d’autres collections à l’aide d’un <xref:System.Windows.Controls.HeaderedItemsControl> type tel qu’un <xref:System.Windows.Controls.Menu> ou un <xref:System.Windows.Controls.TreeView> , il y a le <xref:System.Windows.HierarchicalDataTemplate> . Une autre fonctionnalité de création de modèles de données est <xref:System.Windows.Controls.DataTemplateSelector> , qui vous permet de choisir un <xref:System.Windows.DataTemplate> à utiliser en fonction de la logique personnalisée. Pour plus d’informations, consultez l’article [Vue d'ensemble des modèles de données](/dotnet/desktop/wpf/data/data-templating-overview), qui fournit une discussion plus approfondie sur les différentes fonctionnalités de création de modèles de données.

## <a name="triggers"></a>Déclencheurs

Un déclencheur définit des propriétés ou démarre des actions, par exemple une animation, lorsqu’une valeur de propriété change ou lorsqu’un événement est déclenché. <xref:System.Windows.Style>, <xref:System.Windows.Controls.ControlTemplate> et <xref:System.Windows.DataTemplate> ont tous une `Triggers` propriété qui peut contenir un ensemble de déclencheurs. Il existe plusieurs types de déclencheurs.

### <a name="propertytriggers"></a>PropertyTriggers

Un <xref:System.Windows.Trigger> qui définit des valeurs de propriété ou démarre des actions basées sur la valeur d’une propriété est appelé un déclencheur de propriété.

Pour illustrer l’utilisation des déclencheurs de propriété, vous pouvez rendre chacun <xref:System.Windows.Controls.ListBoxItem> partiellement transparent, sauf s’il est sélectionné. Le style suivant affecte <xref:System.Windows.UIElement.Opacity%2A> à la valeur d’un la valeur <xref:System.Windows.Controls.ListBoxItem> `0.5` . <xref:System.Windows.Controls.ListBoxItem.IsSelected%2A>Toutefois, lorsque la propriété a la `true` <xref:System.Windows.UIElement.Opacity%2A> valeur `1.0` .

[!code-xaml[PropertyTrigger](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window5.xaml#SnippetPropertyTrigger)]

Cet exemple utilise un <xref:System.Windows.Trigger> pour définir une valeur de propriété, mais notez que la <xref:System.Windows.Trigger> classe possède également <xref:System.Windows.TriggerBase.EnterActions%2A> les <xref:System.Windows.TriggerBase.ExitActions%2A> Propriétés et qui permettent à un déclencheur d’effectuer des actions.

Notez que la <xref:System.Windows.FrameworkElement.MaxHeight%2A> propriété de <xref:System.Windows.Controls.ListBoxItem> a la valeur `75` . Dans l’illustration suivante, le troisième élément est l’élément sélectionné.

![Vue de la liste mise en forme avec des styles](./media/styles-and-templates-overview/stylingintro-triggers.png "StylingIntro_triggers")

### <a name="eventtriggers-and-storyboards"></a>EventTriggers et tables de montage séquentiel

Un autre type de déclencheur est <xref:System.Windows.EventTrigger> , qui démarre un ensemble d’actions en fonction de l’occurrence d’un événement. Par exemple, les <xref:System.Windows.EventTrigger> objets suivants spécifient que lorsque le pointeur de la souris entre dans le <xref:System.Windows.Controls.ListBoxItem> , la <xref:System.Windows.FrameworkElement.MaxHeight%2A> propriété s’anime sur une valeur `90` sur une `0.2` seconde période. Lorsque la souris s’éloigne de l’élément, la propriété retourne à sa valeur d’origine pendant une période de `1` seconde. Notez qu’il n’est pas nécessaire de spécifier une <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> valeur pour l' <xref:System.Windows.ContentElement.MouseLeave> Animation. L’animation est en effet capable d’effectuer le suivi de la valeur d’origine.

[!code-xaml[StyleEventTriggers](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window6.xaml#SnippetStyleEventTriggers)]

Pour plus d’informations, consultez [vue d’ensemble des storyboards](/dotnet/desktop/wpf/graphics-multimedia/storyboards-overview).

Dans l’illustration suivante, la souris pointe sur le troisième élément.

![Capture d’écran de l’exemple de style](./media/styles-and-templates-overview/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")

### <a name="multitriggers-datatriggers-and-multidatatriggers"></a>MultiTriggers, DataTriggers et MultiDataTriggers

Outre <xref:System.Windows.Trigger> et <xref:System.Windows.EventTrigger> , il existe d’autres types de déclencheurs. <xref:System.Windows.MultiTrigger> vous permet de définir des valeurs de propriété en fonction de plusieurs conditions. Vous utilisez <xref:System.Windows.DataTrigger> et <xref:System.Windows.MultiDataTrigger> lorsque la propriété de votre condition est liée aux données.

## <a name="visual-states"></a>États visuels

Les contrôles sont toujours dans un **État**spécifique. Par exemple, lorsque la souris se déplace sur la surface d’un contrôle, le contrôle est considéré comme étant dans un État commun de `MouseOver` . Un contrôle sans état spécifique est considéré comme étant dans l’État commun `Normal` . Les États sont divisés en groupes et les États mentionnés précédemment font partie du groupe d’États `CommonStates` . La plupart des contrôles ont deux groupes d’États : `CommonStates` et `FocusStates` . De chaque groupe d’États appliqué à un contrôle, un contrôle est toujours dans un état de chaque groupe, tel que `CommonStates.MouseOver` et `FocusStates.Unfocused` . Toutefois, un contrôle ne peut pas se trouver dans deux États différents au sein du même groupe, tels que `CommonStates.Normal` et `CommonStates.Disabled` . Voici un tableau des États que la plupart des contrôles reconnaissent et utilisent.

| Nom VisualState | Nom VisualStateGroup | Description |
| ---------------- | --------------------- | ----------- |
| Normal           | CommonStates          | État par défaut. |
| MouseOver        | CommonStates          | Le pointeur de souris est positionné sur le contrôle. |
| Appuyé          | CommonStates          | Le contrôle est enfoncé. |
| Désactivé         | CommonStates          | Le contrôle est désactivé. |
| Avec focus          | FocusStates           | Le contrôle a le focus. |
| Sans focus        | FocusStates           | Le contrôle n’a pas le focus. |

En définissant un <xref:System.Windows.VisualStateManager?displayProperty=fullName> sur l’élément racine d’un modèle de contrôle, vous pouvez déclencher des animations lorsqu’un contrôle passe à un état spécifique. `VisualStateManager`Déclare les combinaisons de <xref:System.Windows.VisualStateGroup> et <xref:System.Windows.VisualState> à surveiller. Lorsque le contrôle passe à l’État surveillé, l’animation définie par le `VisaulStateManager` est démarrée.

Par exemple, le code XAML suivant surveille l' `CommonStates.MouseOver` État pour animer la couleur de remplissage de l’élément nommé `backgroundElement` . Lorsque le contrôle retourne à l' `CommonStates.Normal` État, la couleur de remplissage de l’élément nommé `backgroundElement` est restaurée.

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

Pour plus d’informations sur les storyboards, consultez [vue d’ensemble des storyboards](/dotnet/desktop/wpf/graphics-multimedia/storyboards-overview).

## <a name="shared-resources-and-themes"></a>Ressources partagées et thèmes

Une application WPF type peut avoir plusieurs ressources d’interface utilisateur qui sont appliquées dans l’ensemble de l’application. Collectivement, cet ensemble de ressources peut être considéré comme le thème de l’application. WPF prend en charge l’empaquetage des ressources d’interface utilisateur en tant que thème à l’aide d’un dictionnaire de ressources encapsulé en tant que <xref:System.Windows.ResourceDictionary> classe.

Les thèmes WPF sont définis à l’aide du mécanisme de création de styles et de modèles que WPF expose pour la personnalisation des visuels de tout élément.

Les ressources de thème WPF sont stockées dans des dictionnaires de ressources incorporés. Ces dictionnaires de ressources doivent être incorporés dans un assembly signé, et peuvent être incorporés dans le même assembly que le code lui-même, ou bien dans un assembly parallèle. Pour PresentationFramework.dll, l’assembly qui contient des contrôles WPF, les ressources de thème se trouvent dans une série d’assemblys côte à côte.

Le thème est alors le dernier emplacement à consulter lors de la recherche du style d’un élément. En règle générale, la recherche commence en remontant l’arborescence d’éléments qui recherche une ressource appropriée, puis examine la collection de ressources d’application et enfin interroge le système. Cela permet aux développeurs d’applications de redéfinir le style d’un objet au niveau de l’arborescence ou de l’application avant d’atteindre le thème.

Vous pouvez définir des dictionnaires de ressources en tant que fichiers individuels qui vous permettent de réutiliser un thème sur plusieurs applications. Vous pouvez également créer des thèmes permutables en définissant plusieurs dictionnaires de ressources qui fournissent les mêmes types de ressources mais avec des valeurs différentes. La redéfinition de ces styles ou d’autres ressources au niveau de l’application est l’approche recommandée pour l’apparence d’une application.

Pour partager un ensemble de ressources, notamment des styles et des modèles, entre les applications, vous pouvez créer un fichier XAML et définir un <xref:System.Windows.ResourceDictionary> qui inclut une référence à un `shared.xaml` fichier.

```xaml
<ResourceDictionary.MergedDictionaries>
  <ResourceDictionary Source="Shared.xaml" />
</ResourceDictionary.MergedDictionaries>
```

C’est le partage de `shared.xaml` , qui définit lui-même un <xref:System.Windows.ResourceDictionary> qui contient un ensemble de ressources de style et de pinceau, qui permet aux contrôles d’une application d’avoir une apparence cohérente.

Pour plus d’informations, consultez [dictionnaires de ressources fusionnés](/dotnet/desktop/wpf/advanced/merged-resource-dictionaries).

Si vous créez un thème pour votre contrôle personnalisé, consultez la section **définition des ressources au niveau du thème** de la [vue d’ensemble](/dotnet/desktop/wpf/controls/control-authoring-overview#defining-resources-at-the-theme-level)de la création de contrôles.

## <a name="see-also"></a>Voir aussi

- [URI à en-tête pack dans WPF](/dotnet/desktop/wpf/app-development/pack-uris-in-wpf)
- [Procédure : rechercher des éléments générés par ControlTemplate](/dotnet/desktop/wpf/controls/how-to-find-controltemplate-generated-elements)
- [Rechercher des éléments générés par DataTemplate](/dotnet/desktop/wpf/data/how-to-find-datatemplate-generated-elements)
