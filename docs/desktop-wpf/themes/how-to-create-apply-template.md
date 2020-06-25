---
title: Créer un modèle dans WPF-.NET Desktop
description: Découvrez comment créer et référencer un modèle de contrôle dans Windows Presentation Foundation et .NET Core.
author: adegeo
ms.author: adegeo
ms.date: 11/15/2019
no-loc:
- <Window>
- <ControlTemplate>
- <Ellipse>
- <ContentPresenter>
- <Trigger>
- <Setter>
- <PropertyTrigger>
- <Grid>
- <VisualStateManager.VisualStateGroups>
- <VisualStateGroup>
- <VisualState>
- <Storyboard>
- SizeToContent
- MinWidth
- TargetType
- Title
helpviewer_keywords:
- control contract [WPF]
- controls [WPF], visual structure changes
- ControlTemplate [WPF], customizing for existing controls
- skinning controls [WPF]
- controls [WPF], appearance specified by state
- templates [WPF], custom for existing controls
ms.openlocfilehash: c372659676b450cde789c96e45c7ec5de2aea194
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325732"
---
# <a name="create-a-template-for-a-control"></a>Créer un modèle pour un contrôle

Avec Windows Presentation Foundation (WPF), vous pouvez personnaliser la structure visuelle et le comportement d’un contrôle existant avec votre propre modèle réutilisable. Les modèles peuvent être appliqués globalement à votre application, à vos fenêtres et à vos pages, ou directement à des contrôles. La plupart des scénarios qui requièrent la création d’un nouveau contrôle peuvent être couverts en créant à la place un nouveau modèle pour un contrôle existant.

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

Dans cet article, vous allez découvrir comment créer un nouveau <xref:System.Windows.Controls.ControlTemplate> pour le <xref:System.Windows.Controls.Button> contrôle.

## <a name="when-to-create-a-controltemplate"></a>Quand créer un ControlTemplate

Les contrôles ont de nombreuses propriétés, telles que <xref:System.Windows.Controls.Border.Background%2A> , <xref:System.Windows.Controls.Control.Foreground%2A> et <xref:System.Windows.Controls.Control.FontFamily%2A> . Ces propriétés contrôlent les différents aspects de l’apparence du contrôle, mais les modifications que vous pouvez apporter en définissant ces propriétés sont limitées. Par exemple, vous pouvez affecter la valeur <xref:System.Windows.Controls.Control.Foreground%2A> Blue à la propriété et la valeur <xref:System.Windows.Controls.Control.FontStyle%2A> italique à un <xref:System.Windows.Controls.CheckBox> . Si vous souhaitez personnaliser l’apparence du contrôle au-delà de ce que peut faire les autres propriétés du contrôle, vous créez un <xref:System.Windows.Controls.ControlTemplate> .

Dans la plupart des interfaces utilisateur, un bouton a la même apparence générale : un rectangle avec du texte. Si vous souhaitez créer un bouton arrondi, vous pouvez créer un nouveau contrôle qui hérite du bouton ou recrée les fonctionnalités du bouton. En outre, le nouveau contrôle utilisateur fournirait le visuel circulaire.

Vous pouvez éviter de créer de nouveaux contrôles en personnalisant la disposition visuelle d’un contrôle existant. Avec un bouton arrondi, vous créez un <xref:System.Windows.Controls.ControlTemplate> avec la disposition visuelle souhaitée.

En revanche, si vous avez besoin d’un contrôle avec de nouvelles fonctionnalités, des propriétés différentes et de nouveaux paramètres, vous devez créer un nouveau <xref:System.Windows.Controls.UserControl> .

## <a name="prerequisites"></a>Prérequis

Créez une application WPF et dans *MainWindow. Xaml* (ou une autre fenêtre de votre choix) définissez les propriétés suivantes sur l' **\<Window>** élément :

|     |     |
| --- | --- |
| **Title**         | `Template Intro Sample` |
| **SizeToContent** | `WidthAndHeight` |
| **MinWidth**      | `250` |

Définissez le contenu de l' **\<Window>** élément sur le code XAML suivant :

[!code-xaml[Initial](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window1.xaml#Initial)]

À la fin, le fichier *MainWindow. Xaml* doit ressembler à ce qui suit :

[!code-xaml[InitialWhole](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window1.xaml#InitialWhole)]

Si vous exécutez l’application, elle ressemble à ceci :

![Fenêtre WPF avec deux boutons sans style](media/create-apply-template/unstyled-button.png)

## <a name="create-a-controltemplate"></a>Créer un ControlTemplate

La méthode la plus courante pour déclarer un <xref:System.Windows.Controls.ControlTemplate> est en tant que ressource dans la `Resources` section d’un fichier XAML. Étant donné que les modèles sont des ressources, ils obéissent aux mêmes règles de portée qui s’appliquent à toutes les ressources. En d’autres termes, lorsque vous déclarez un modèle, vous affectez l’emplacement où le modèle peut être appliqué. Par exemple, si vous déclarez le modèle dans l’élément racine de votre fichier XAML de définition d’application, le modèle peut être utilisé n’importe où dans votre application. Si vous définissez le modèle dans une fenêtre, seuls les contrôles de cette fenêtre peuvent utiliser le modèle.

Pour commencer, ajoutez un `Window.Resources` élément à votre fichier *MainWindow. Xaml* :

[!code-xaml[WindowResStart](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window2.xaml#WindowResStart)]

Créez un nouveau **\<ControlTemplate>** avec les propriétés suivantes définies :

|     |     |
| --- | --- |
| **x:Key**         | `roundbutton` |
| **TargetType**    | `Button` |

Ce modèle de contrôle sera simple :

- élément racine pour le contrôle, un<xref:System.Windows.Controls.Grid>
- <xref:System.Windows.Shapes.Ellipse>pour dessiner l’apparence arrondie du bouton
- <xref:System.Windows.Controls.ContentPresenter>pour afficher le contenu du bouton spécifié par l’utilisateur

[!code-xaml[ControlTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window3.xaml#ControlTemplate)]

### <a name="templatebinding"></a>TemplateBinding

Quand vous créez un nouveau <xref:System.Windows.Controls.ControlTemplate> , vous pouvez toujours utiliser les propriétés publiques pour modifier l’apparence du contrôle. L’extension de balisage [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md) lie une propriété d’un élément qui se trouve dans <xref:System.Windows.Controls.ControlTemplate> à une propriété publique définie par le contrôle. Quand vous utilisez un [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md), vous activez les propriétés du contrôle pour agir en tant que paramètres du modèle. Autrement dit, quand une propriété sur un contrôle est définie, cette valeur est passée à l’élément qui a le [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md).

### <a name="ellipse"></a>Ellipse

Notez que les **:::no-loc text="Fill":::** **:::no-loc text="Stroke":::** Propriétés et de l' **\<Ellipse>** élément sont liées aux <xref:System.Windows.Controls.Control.Foreground> Propriétés et du contrôle <xref:System.Windows.Controls.Control.Background> .

### <a name="contentpresenter"></a>ContentPresenter

Un [\<ContentPresenter>](xref:System.Windows.Controls.ContentPresenter) élément est également ajouté au modèle. Étant donné que ce modèle est conçu pour un bouton, prenez en considération le fait que le bouton hérite de <xref:System.Windows.Controls.ContentControl> . Le bouton présente le contenu de l’élément. Vous pouvez définir tout ce qui se trouve à l’intérieur du bouton, comme du texte brut ou même un autre contrôle. Les deux types de boutons valides sont les suivants :

```xaml
<Button>My Text</Button>

<!-- and -->

<Button>
    <CheckBox>Checkbox in a button</CheckBox>
</Button>
```

Dans les deux exemples précédents, le texte et la case à cocher sont définis en tant que propriété [Button. Content](xref:System.Windows.Controls.ContentControl.Content) . Tout ce qui est défini en tant que contenu peut être présenté à l’aide d’un **\<ContentPresenter>** , ce que fait le modèle.

Si le <xref:System.Windows.Controls.ControlTemplate> est appliqué à un <xref:System.Windows.Controls.ContentControl> type, tel qu’un `Button` , une <xref:System.Windows.Controls.ContentPresenter> est recherchée dans l’arborescence d’éléments. Si le `ContentPresenter` est trouvé, le modèle lie automatiquement la propriété du contrôle <xref:System.Windows.Controls.ContentControl.Content> à `ContentPresenter` .

## <a name="use-the-template"></a>Utiliser le modèle

Recherchez les boutons qui ont été déclarés au début de cet article.

[!code-xaml[Initial](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window1.xaml#Initial)]

Définissez la propriété du deuxième bouton <xref:System.Windows.Controls.Control.Template> sur la `roundbutton` ressource :

[!code-xaml[StyledButton](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window3.xaml#StyledButton)]

Si vous exécutez le projet et regardez le résultat, vous verrez que le bouton a un arrière-plan arrondi.

![Fenêtre WPF avec un bouton ovale de modèle](media/create-apply-template/styled-button.png)

Vous avez peut-être remarqué que le bouton n’est pas un cercle, mais qu’il est incliné. En raison de la façon dont l' **\<Ellipse>** élément fonctionne, il se développe toujours pour occuper l’espace disponible. Définissez le cercle comme uniforme en remplaçant les propriétés et du bouton par **:::no-loc text="width":::** **:::no-loc text="height":::** la même valeur :

[!code-xaml[StyledButtonSize](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window3.xaml#StyledButtonSize)]

![Fenêtre WPF avec un seul modèle de bouton circulaire](media/create-apply-template/styled-uniform-button.png)

## <a name="add-a-trigger"></a>Ajouter un déclencheur

Même si un bouton avec un modèle appliqué semble différent, il se comporte comme n’importe quel autre bouton. Si vous appuyez sur le bouton, l' <xref:System.Windows.Controls.Primitives.ButtonBase.Click> événement se déclenche. Toutefois, vous avez peut-être remarqué que lorsque vous déplacez votre souris sur le bouton, les éléments visuels du bouton ne changent pas. Ces interactions visuelles sont toutes définies par le modèle.

Avec les systèmes d’événements et de propriétés dynamiques fournis par WPF, vous pouvez surveiller une propriété spécifique pour une valeur, puis restyleer le modèle lorsque cela est approprié. Dans cet exemple, vous allez surveiller la propriété du bouton <xref:System.Windows.UIElement.IsMouseOver> . Lorsque la souris se trouve sur le contrôle, Stylez **\<Ellipse>** avec une nouvelle couleur. Ce type de déclencheur est appelé *PropertyTrigger*.

Pour que cela fonctionne, vous devez ajouter un nom au **\<Ellipse>** que vous pouvez référencer. Donnez-lui le nom de **backgroundElement**.

[!code-xaml[EllipseName](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window4.xaml#EllipseName)]

Ensuite, ajoutez un nouveau <xref:System.Windows.Trigger> à la collection [ControlTemplate. Triggers](xref:System.Windows.Controls.ControlTemplate.Triggers) . Le déclencheur surveille l' `IsMouseOver` événement pour la valeur `true` .

[!code-xaml[ControlTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window4.xaml?name=ControlTemplate&highlight=6-10)]

Ajoutez ensuite un **\<Setter>** au **\<Trigger>** qui modifie la propriété **Fill** du **\<Ellipse>** en une nouvelle couleur.

[!code-xaml[MouseOver](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window5.xaml#MouseOver)]

Exécutez le projet. Notez que lorsque vous placez le pointeur de la souris sur le bouton, la couleur des **\<Ellipse>** modifications.

![la souris se déplace sur le bouton WPF pour modifier la couleur de remplissage](media/create-apply-template/mouse-move-over-button.gif)

## <a name="use-a-visualstate"></a>Utiliser un VisualState

Les États visuels sont définis et déclenchés par un contrôle. Par exemple, lorsque la souris est déplacée au-dessus du contrôle, l' `CommonStates.MouseOver` État est déclenché. Vous pouvez animer les modifications de propriété en fonction de l’état actuel du contrôle. Dans la section précédente, **\<PropertyTrigger>** a était utilisé pour remplacer le premier plan du bouton par `AliceBlue` lorsque la `IsMouseOver` propriété était `true` . Au lieu de cela, créez un état visuel qui anime la modification de cette couleur, en fournissant une transition lisse. Pour plus d’informations sur *VisualStates*, consultez [styles et modèles dans WPF](../fundamentals/styles-templates-overview.md#visual-states).

Pour convertir le **\<PropertyTrigger>** en un état visuel animé, commencez par supprimer l' **\<ControlTemplate.Triggers>** élément de votre modèle.

[!code-xaml[CleanTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window5.xaml#CleanTemplate)]

Ensuite, à la **\<Grid>** racine du modèle de contrôle, ajoutez l' **\<VisualStateManager.VisualStateGroups>** élément avec un **\<VisualStateGroup>** pour `CommonStates` . Définissez deux États, `Normal` et `MouseOver` .

[!code-xaml[VisualState](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window6.xaml#VisualState)]

Les animations définies dans un **\<VisualState>** sont appliquées lorsque cet État est déclenché. Créez des animations pour chaque État. Les animations sont placées à l’intérieur d’un **\<Storyboard>** élément. Pour plus d’informations sur les storyboards, consultez [vue d’ensemble des storyboards](../../framework/wpf/graphics-multimedia/storyboards-overview.md).

- Normal

  Cet État anime le remplissage de l’ellipse, en le restaurant à la `Background` couleur du contrôle.

  [!code-xaml[NormalState](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window6.xaml#NormalState)]

- MouseOver

  Cet État anime la `Background` couleur de l’ellipse avec une nouvelle couleur : `Yellow` .

  [!code-xaml[MouseOverState](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window6.xaml#MouseOverState)]

Le **\<ControlTemplate>** doit maintenant ressembler à ce qui suit.

[!code-xaml[FinalTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window7.xaml#FinalTemplate)]

Exécutez le projet. Notez que lorsque vous placez le pointeur de la souris sur le bouton, la couleur de l' **\<Ellipse>** Animation.

![la souris se déplace sur le bouton WPF pour modifier la couleur de remplissage](media/create-apply-template/mouse-move-over-button-visualstate.gif)

## <a name="next-steps"></a>Étapes suivantes

- [Créer un style pour un contrôle dans WPF](../fundamentals/styles-templates-create-apply-style.md)
- [Styles et modèles dans WPF](../fundamentals/styles-templates-overview.md)
- [Vue d’ensemble des ressources XAML](../fundamentals/xaml-resources-define.md)
