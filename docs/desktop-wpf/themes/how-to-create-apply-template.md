---
title: Créez un modèle dans WPF - .NET Desktop
description: Découvrez comment créer et référencer un modèle de contrôle dans Windows Presentation Foundation et .NET Core.
author: thraka
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
ms.openlocfilehash: c901864d387b8de976bbfa9a9b3c14a7d5a0b4d8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "82071247"
---
# <a name="create-a-template-for-a-control"></a>Créer un modèle pour un contrôle

Avec Windows Presentation Foundation (WPF), vous pouvez personnaliser la structure visuelle et le comportement d’un contrôle existant avec votre propre modèle réutilisable. Les modèles peuvent être appliqués globalement à votre application, fenêtres et pages, ou directement aux contrôles. La plupart des scénarios qui vous obligent à créer un nouveau contrôle peuvent être couverts par la création d’un nouveau modèle pour un contrôle existant.

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

Dans cet article, vous explorerez <xref:System.Windows.Controls.ControlTemplate> la <xref:System.Windows.Controls.Button> création d’un nouveau pour le contrôle.

## <a name="when-to-create-a-controltemplate"></a>Quand créer un ControlTemplate

Les contrôles ont de <xref:System.Windows.Controls.Border.Background%2A> <xref:System.Windows.Controls.Control.Foreground%2A>nombreuses <xref:System.Windows.Controls.Control.FontFamily%2A>propriétés, telles que , , et . Ces propriétés contrôlent différents aspects de l’apparence du contrôle, mais les modifications que vous pouvez apporter en définissant ces propriétés sont limitées. Par exemple, vous <xref:System.Windows.Controls.Control.Foreground%2A> pouvez définir <xref:System.Windows.Controls.Control.FontStyle%2A> la propriété en <xref:System.Windows.Controls.CheckBox>bleu et en italique sur un . Lorsque vous voulez personnaliser l’apparence du contrôle au-delà de ce que <xref:System.Windows.Controls.ControlTemplate>le réglage des autres propriétés sur le contrôle peut faire, vous créez un .

Dans la plupart des interfaces utilisateur, un bouton a la même apparence générale : un rectangle avec un certain texte. Si vous voulez créer un bouton arrondi, vous pouvez créer un nouveau contrôle qui hérite du bouton ou recrée la fonctionnalité du bouton. En outre, le nouveau contrôle de l’utilisateur fournirait le visuel circulaire.

Vous pouvez éviter de créer de nouveaux contrôles en personnalisant la disposition visuelle d’un contrôle existant. Avec un bouton arrondi, <xref:System.Windows.Controls.ControlTemplate> vous créez un avec la disposition visuelle désirée.

D’autre part, si vous avez besoin d’un contrôle avec de nouvelles <xref:System.Windows.Controls.UserControl>fonctionnalités, différentes propriétés, et de nouveaux paramètres, vous créeriez un nouveau .

## <a name="prerequisites"></a>Prérequis

Créez une nouvelle application WPF et dans *MainWindow.xaml* (ou une autre fenêtre de votre choix) définissez les propriétés suivantes sur ** \<l’élément window>** :

|     |     |
| --- | --- |
| **[!OP.NO-LOC(Title)]**         | `Template Intro Sample` |
| **[!OP.NO-LOC(SizeToContent)]** | `WidthAndHeight` |
| **[!OP.NO-LOC(MinWidth)]**      | `250` |

Définissez le ** \<** contenu de l’élément>de fenêtre à l’XAML suivant :

[!code-xaml[Initial](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window1.xaml#Initial)]

En fin de compte, le fichier *MainWindow.xaml* devrait ressembler à ce qui suit :

[!code-xaml[InitialWhole](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window1.xaml#InitialWhole)]

Si vous exécutez l’application, il ressemble à ce qui suit:

![Fenêtre WPF avec deux boutons non coiffés](media/create-apply-template/unstyled-button.png)

## <a name="create-a-controltemplate"></a>Créer un ControlTemplate

La façon la plus <xref:System.Windows.Controls.ControlTemplate> courante de déclarer `Resources` un est comme une ressource dans la section dans un fichier XAML. Étant donné que les modèles sont des ressources, ils obéissent aux mêmes règles d’établissement de la portée qui s’appliquent à toutes les ressources. En d’autres termes, l’endroit où vous déclarez qu’un modèle affecte l’endroit où le modèle peut être appliqué. Par exemple, si vous déclarez le modèle dans l’élément racine de votre fichier XAML de définition d’application, le modèle peut être utilisé n’importe où dans votre application. Si vous définissez le modèle dans une fenêtre, seuls les commandes de cette fenêtre peuvent utiliser le modèle.

Pour commencer, ajoutez `Window.Resources` un élément à votre fichier *MainWindow.xaml* :

[!code-xaml[WindowResStart](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window2.xaml#WindowResStart)]

Créez un nouveau ** \<>ControlTemplate** avec les propriétés suivantes :

|     |     |
| --- | --- |
| **x:Key**         | `roundbutton` |
| **TargetType**    | `Button` |

Ce modèle de contrôle sera simple :

- un élément racine pour le contrôle, un<xref:System.Windows.Controls.Grid>
- un <xref:System.Windows.Shapes.Ellipse> pour dessiner l’aspect arrondi du bouton
- a <xref:System.Windows.Controls.ContentPresenter> pour afficher le contenu du bouton spécifié par l’utilisateur

[!code-xaml[ControlTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window3.xaml#ControlTemplate)]

### <a name="templatebinding"></a>TemplateBinding

Lorsque vous créez <xref:System.Windows.Controls.ControlTemplate>un nouveau , vous pouvez toujours utiliser les propriétés publiques pour changer l’apparence du contrôle. L’extension de balisage [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md) lie une <xref:System.Windows.Controls.ControlTemplate> propriété d’un élément qui se trouve dans un bien public qui est défini par le contrôle. Lorsque vous utilisez un [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md), vous activez les propriétés sur le contrôle pour agir comme paramètres du modèle. Autrement dit, quand une propriété sur un contrôle est définie, cette valeur est passée à l’élément qui a le [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md).

### <a name="ellipse"></a>Ellipse

Notez **:::no-loc text="Fill":::** que **:::no-loc text="Stroke":::** les propriétés et les propriétés de l’Ellipse ** \<>** élément sont liés à ceux du contrôle et <xref:System.Windows.Controls.Control.Foreground> <xref:System.Windows.Controls.Control.Background> des propriétés.

### <a name="contentpresenter"></a>ContentPresenter

Un [ \<élément de>contentPresenter](xref:System.Windows.Controls.ContentPresenter) est également ajouté au modèle. Parce que ce modèle est conçu pour un bouton, <xref:System.Windows.Controls.ContentControl>prenez en considération que le bouton hérite de . Le bouton présente le contenu de l’élément. Vous pouvez définir n’importe quoi à l’intérieur du bouton, comme le texte simple ou même un autre contrôle. Les deux suivants sont des boutons valides :

```xaml
<Button>My Text</Button>

<!-- and -->

<Button>
    <CheckBox>Checkbox in a button</CheckBox>
</Button>
```

Dans les deux exemples précédents, le texte et la case à cocher sont définis comme la propriété [Button.Content.](xref:System.Windows.Controls.ContentControl.Content) Tout ce qui est défini car le contenu peut être présenté par un ** \<contentPresenter>**, ce qui est ce que le modèle fait.

Si <xref:System.Windows.Controls.ControlTemplate> le est <xref:System.Windows.Controls.ContentControl> appliqué à un `Button`type, tel qu’un , a <xref:System.Windows.Controls.ContentPresenter> est recherché dans l’arbre élément. Si `ContentPresenter` l’on le trouve, le modèle <xref:System.Windows.Controls.ContentControl.Content> lie `ContentPresenter`automatiquement la propriété du contrôle à la .

## <a name="use-the-template"></a>Utiliser le modèle

Trouvez les boutons qui ont été déclarés au début de cet article.

[!code-xaml[Initial](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window1.xaml#Initial)]

Réglez la <xref:System.Windows.Controls.Control.Template> propriété du `roundbutton` deuxième bouton à la ressource :

[!code-xaml[StyledButton](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window3.xaml#StyledButton)]

Si vous exécutez le projet et regardez le résultat, vous verrez que le bouton a un arrière-plan arrondi.

![Fenêtre WPF avec un bouton ovale de modèle](media/create-apply-template/styled-button.png)

Vous avez peut-être remarqué que le bouton n’est pas un cercle, mais est biaisé. En raison de la façon dont ** \<l’Ellipse>** élément fonctionne, il s’élargit toujours pour remplir l’espace disponible. Faites l’uniforme du cercle **:::no-loc text="width":::** en **:::no-loc text="height":::** changeant le bouton et les propriétés à la même valeur :

[!code-xaml[StyledButtonSize](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window3.xaml#StyledButtonSize)]

![Fenêtre WPF avec un bouton circulaire de modèle](media/create-apply-template/styled-uniform-button.png)

## <a name="add-a-trigger"></a>Ajouter un déclencheur

Même si un bouton avec un modèle appliqué semble différent, il se comporte de la même façon que n’importe quel autre bouton. Si vous appuyez <xref:System.Windows.Controls.Primitives.ButtonBase.Click> sur le bouton, l’événement s’allume. Cependant, vous avez peut-être remarqué que lorsque vous déplacez votre souris sur le bouton, les visuels du bouton ne changent pas. Ces interactions visuelles sont toutes définies par le modèle.

Avec l’événement dynamique et les systèmes de propriété que WPF fournit, vous pouvez regarder une propriété spécifique pour une valeur, puis relooker le modèle le cas échéant. Dans cet exemple, vous regarderez <xref:System.Windows.UIElement.IsMouseOver> la propriété du bouton. Lorsque la souris est sur le contrôle, le style de ** \<l’Ellipse>** avec une nouvelle couleur. Ce type de déclencheur est connu comme un *PropertyTrigger*.

Pour que cela fonctionne, vous devrez ajouter un nom à ** \<l’Ellipse>** que vous pouvez référencer. Donnez-lui le nom de **fondElement**.

[!code-xaml[EllipseName](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window4.xaml#EllipseName)]

Ensuite, ajoutez <xref:System.Windows.Trigger> un nouveau à la collection [ControlTemplate.Triggers.](xref:System.Windows.Controls.ControlTemplate.Triggers) La gâchette `IsMouseOver` regardera l’événement pour la valeur `true`.

[!code-xaml[ControlTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window4.xaml?name=ControlTemplate&highlight=6-10)]

Ensuite, ajoutez un ** \<>Setter** ** \<** à la>de déclenchement qui modifie la propriété **Fill** de ** \<l’Ellipse>** à une nouvelle couleur.

[!code-xaml[MouseOver](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window5.xaml#MouseOver)]

Exécutez le projet. Notez que lorsque vous déplacez la souris sur le bouton, la couleur de ** \<l’Ellipse>** change.

![la souris se déplace sur le bouton WPF pour changer la couleur de remplissage](media/create-apply-template/mouse-move-over-button.gif)

## <a name="use-a-visualstate"></a>Utiliser un VisualState

Les états visuels sont définis et déclenchés par un contrôle. Par exemple, lorsque la souris est déplacée `CommonStates.MouseOver` sur le dessus du contrôle, l’état est déclenché. Vous pouvez animer les changements de propriété en fonction de l’état actuel du contrôle. Dans la section précédente, `IsMouseOver` un `true` ** \<>PropertyTrigger** a été utilisé pour `AliceBlue` changer le premier plan du bouton à l’époque où la propriété était . Au lieu de cela, créer un état visuel qui anime le changement de cette couleur, offrant une transition en douceur. Pour plus d’informations sur *VisualStates*, voir [Styles et modèles dans WPF](../fundamentals/styles-templates-overview.md#visual-states).

Pour convertir le ** \<>PropertyTrigger** en un état visuel animé, d’abord, retirez ** \<l’élément ControlTemplate.Triggers>** de votre modèle.

[!code-xaml[CleanTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window5.xaml#CleanTemplate)]

Ensuite, dans ** \<** la grille>racine du modèle de contrôle, ajouter le `CommonStates` ** \<VisualStateManager.VisualStateGroups>** élément avec un ** \<visualStateGroup>** pour . Définir deux `Normal` états, et `MouseOver`.

[!code-xaml[VisualState](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window6.xaml#VisualState)]

Toutes les animations définies dans un ** \<>VisualState** sont appliquées lorsque cet état est déclenché. Créez des animations pour chaque état. Les animations sont ** \<** mises à l’intérieur d’un élément de>Storyboard. Pour plus d’informations sur les storyboards, voir [Storyboards Aperçu](../../framework/wpf/graphics-multimedia/storyboards-overview.md).

- Normal

  Cet état anime le remplissage de l’ellipse, `Background` la rétablissant à la couleur du contrôle.

  [!code-xaml[NormalState](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window6.xaml#NormalState)]

- MouseOver

  Cet état anime la couleur `Background` de l’ellipse à une nouvelle couleur : `Yellow`.

  [!code-xaml[MouseOverState](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window6.xaml#MouseOverState)]

Le ** \<ControlTemplate>** devrait maintenant ressembler à ce qui suit.

[!code-xaml[FinalTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window7.xaml#FinalTemplate)]

Exécutez le projet. Notez que lorsque vous déplacez la souris sur le bouton, la couleur de ** \<l’Ellipse>** anime.

![la souris se déplace sur le bouton WPF pour changer la couleur de remplissage](media/create-apply-template/mouse-move-over-button-visualstate.gif)

## <a name="next-steps"></a>Étapes suivantes

- [Créer un style pour un contrôle dans WPF](../fundamentals/styles-templates-create-apply-style.md)
- [Styles et modèles dans WPF](../fundamentals/styles-templates-overview.md)
- [Aperçu des ressources XAML](../fundamentals/xaml-resources-define.md)
