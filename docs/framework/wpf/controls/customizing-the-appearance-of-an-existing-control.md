---
title: Personnalisation de l'apparence d'un contrôle existant en créant un ControlTemplate
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- control contract [WPF]
- controls [WPF], visual structure changes
- ControlTemplate [WPF], customizing for existing controls
- skinning controls [WPF]
- controls [WPF], appearance specified by state
- templates [WPF], custom for existing controls
ms.assetid: 678dd116-43a2-4b8c-82b5-6b826f126e31
ms.openlocfilehash: 6d7401f9614e663351968dc6a2f85548735a176d
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460416"
---
# <a name="customizing-the-appearance-of-an-existing-control-by-creating-a-controltemplate"></a>Personnalisation de l'apparence d'un contrôle existant en créant un ControlTemplate
<a name="introduction"></a><xref:System.Windows.Controls.ControlTemplate> spécifie la structure visuelle et le comportement visuel d’un contrôle. Vous pouvez personnaliser l’apparence d’un contrôle en lui donnant un nouveau <xref:System.Windows.Controls.ControlTemplate>. Lorsque vous créez un <xref:System.Windows.Controls.ControlTemplate>, vous remplacez l’apparence d’un contrôle existant sans modifier sa fonctionnalité. Par exemple, vous pouvez faire en sorte que les boutons de votre application s’arrondissent au lieu de la forme carrée par défaut, mais le bouton déclenchera toujours l’événement <xref:System.Windows.Controls.Primitives.ButtonBase.Click>.

 Cette rubrique explique les différentes parties d’un <xref:System.Windows.Controls.ControlTemplate>, illustre la création d’un <xref:System.Windows.Controls.ControlTemplate> simple pour un <xref:System.Windows.Controls.Button>et explique comment comprendre le contrat de contrôle d’un contrôle pour vous permettre de personnaliser son apparence. Étant donné que vous créez un <xref:System.Windows.Controls.ControlTemplate> dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], vous pouvez modifier l’apparence d’un contrôle sans écrire de code. Vous pouvez également utiliser un concepteur, tel que Blend pour Visual Studio, pour créer des modèles de contrôle personnalisés. Cette rubrique présente des exemples de la [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] qui personnalisent l’apparence d’un <xref:System.Windows.Controls.Button> et répertorie l’exemple complet à la fin de la rubrique. Pour plus d’informations sur l’utilisation de Blend pour Visual Studio, consultez [stylisation d’un contrôle qui prend en charge les modèles](https://go.microsoft.com/fwlink/?LinkId=161153).

 Les illustrations suivantes montrent une <xref:System.Windows.Controls.Button> qui utilise le <xref:System.Windows.Controls.ControlTemplate> créé dans cette rubrique.

 ![Bouton avec un modèle de contrôle personnalisé.](./media/ndp-buttonnormal.png "NDP_ButtonNormal")
Bouton qui utilise un modèle de contrôle personnalisé

 ![Bouton avec une bordure rouge.](./media/ndp-buttonmouseover.png "NDP_ButtonMouseOver")
Bouton qui utilise un modèle de contrôle personnalisé et sur lequel le pointeur de la souris se trouve

<a name="prerequisites"></a>
## <a name="prerequisites"></a>Configuration requise
 Cette rubrique part du principe que vous savez comment créer et utiliser des contrôles et des styles, comme indiqué dans [Contrôles](index.md). Les concepts abordés dans cette rubrique s’appliquent aux éléments qui héritent de la classe <xref:System.Windows.Controls.Control>, à l’exception du <xref:System.Windows.Controls.UserControl>. Vous ne pouvez pas appliquer un <xref:System.Windows.Controls.ControlTemplate> à un <xref:System.Windows.Controls.UserControl>.

<a name="when_you_should_create_a_controltemplate"></a>
## <a name="when-you-should-create-a-controltemplate"></a>Quand créer un ControlTemplate
 Les contrôles ont de nombreuses propriétés, telles que <xref:System.Windows.Controls.Border.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>et <xref:System.Windows.Controls.Control.FontFamily%2A>, que vous pouvez définir pour spécifier différents aspects de l’apparence du contrôle, mais les modifications que vous pouvez apporter en définissant ces propriétés sont limitées. Par exemple, vous pouvez définir la propriété <xref:System.Windows.Controls.Control.Foreground%2A> sur Blue et <xref:System.Windows.Controls.Control.FontStyle%2A> sur Italic sur un <xref:System.Windows.Controls.CheckBox>.

 Si vous n’avez pas la possibilité de créer un <xref:System.Windows.Controls.ControlTemplate> pour les contrôles, tous les contrôles de chaque application basée sur [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]auront la même apparence générale, ce qui limiterait la possibilité de créer une application avec une apparence et une convivialité personnalisées. Par défaut, chaque <xref:System.Windows.Controls.CheckBox> a des caractéristiques similaires. Par exemple, le contenu du <xref:System.Windows.Controls.CheckBox> est toujours à droite de l’indicateur de sélection, et la coche est toujours utilisée pour indiquer que la <xref:System.Windows.Controls.CheckBox> est sélectionnée.

 Vous créez une <xref:System.Windows.Controls.ControlTemplate> lorsque vous souhaitez personnaliser l’apparence du contrôle au-delà de ce qui est défini par les autres propriétés du contrôle. Dans l’exemple de la <xref:System.Windows.Controls.CheckBox>, supposons que vous souhaitiez que le contenu de la case à cocher se trouve au-dessus de l’indicateur de sélection et que vous souhaitiez qu’un X indique que le <xref:System.Windows.Controls.CheckBox> est sélectionné. Vous spécifiez ces modifications dans le <xref:System.Windows.Controls.ControlTemplate> du <xref:System.Windows.Controls.CheckBox>.

 L’illustration suivante montre une <xref:System.Windows.Controls.CheckBox> qui utilise un <xref:System.Windows.Controls.ControlTemplate>par défaut.

 ![Case à cocher avec le modèle de contrôle par défaut.](./media/ndp-checkboxdefault.png "NDP_CheckBoxDefault")
Case à cocher qui utilise le modèle de contrôle par défaut

 L’illustration suivante montre une <xref:System.Windows.Controls.CheckBox> qui utilise un <xref:System.Windows.Controls.ControlTemplate> personnalisé pour placer le contenu du <xref:System.Windows.Controls.CheckBox> au-dessus de l’indicateur de sélection et affiche un X lorsque la <xref:System.Windows.Controls.CheckBox> est sélectionnée.

 ![Case à cocher avec un modèle de contrôle personnalisé.](./media/ndp-checkboxcustom.png "NDP_CheckBoxCustom")
Case à cocher qui utilise un modèle de contrôle personnalisé

 La <xref:System.Windows.Controls.ControlTemplate> pour les <xref:System.Windows.Controls.CheckBox> de cet exemple est relativement complexe. cette rubrique utilise donc un exemple plus simple de création d’un <xref:System.Windows.Controls.ControlTemplate> pour un <xref:System.Windows.Controls.Button>.

<a name="changing_the_visual_structure_of_a_control"></a>
## <a name="changing-the-visual-structure-of-a-control"></a>Changement de la structure visuelle d’un contrôle
 Dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], un contrôle est souvent un objet <xref:System.Windows.FrameworkElement> composite. Lorsque vous créez un <xref:System.Windows.Controls.ControlTemplate>, vous combinez des objets <xref:System.Windows.FrameworkElement> pour générer un contrôle unique. Un <xref:System.Windows.Controls.ControlTemplate> doit avoir une seule <xref:System.Windows.FrameworkElement> en tant qu’élément racine. L’élément racine contient généralement d’autres objets <xref:System.Windows.FrameworkElement>. La combinaison d’objets constitue la structure visuelle du contrôle.

 L’exemple suivant crée une <xref:System.Windows.Controls.ControlTemplate> personnalisée pour le <xref:System.Windows.Controls.Button>. L' <xref:System.Windows.Controls.ControlTemplate> crée la structure visuelle du <xref:System.Windows.Controls.Button>. Cet exemple ne change pas l’apparence du bouton si vous placez le pointeur de la souris dessus ou cliquez dessus. La modification de l’apparence du bouton quand celui-ci est dans un autre état est décrite plus loin dans cette rubrique.

 Dans cet exemple, la structure visuelle se compose des parties suivantes :

- <xref:System.Windows.Controls.Border> nommé `RootElement` qui sert de <xref:System.Windows.FrameworkElement>racine du modèle.

- <xref:System.Windows.Controls.Grid> qui est un enfant de `RootElement`.

- <xref:System.Windows.Controls.ContentPresenter> qui affiche le contenu du bouton. Le <xref:System.Windows.Controls.ContentPresenter> permet d’afficher tout type d’objet.

 [!code-xaml[VSMButtonTemplate#BasicTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#basictemplate)]

### <a name="preserving-the-functionality-of-a-controls-properties-by-using-templatebinding"></a>Conservation de la fonctionnalité des propriétés d’un contrôle en utilisant TemplateBinding
 Lorsque vous créez un <xref:System.Windows.Controls.ControlTemplate>, vous pouvez toujours utiliser les propriétés publiques pour modifier l’apparence du contrôle. L’extension de balisage [TemplateBinding](../advanced/templatebinding-markup-extension.md) lie une propriété d’un élément qui se trouve dans le <xref:System.Windows.Controls.ControlTemplate> à une propriété publique définie par le contrôle. Quand vous utilisez [TemplateBinding](../advanced/templatebinding-markup-extension.md), vous permettez aux propriétés sur le contrôle d’agir comme paramètres du modèle. Autrement dit, quand une propriété sur un contrôle est définie, cette valeur est passée à l’élément qui a le [TemplateBinding](../advanced/templatebinding-markup-extension.md).

 L’exemple suivant répète la partie de l’exemple précédent qui utilise l’extension de balisage [TemplateBinding](../advanced/templatebinding-markup-extension.md) pour lier les propriétés des éléments qui se trouvent dans le <xref:System.Windows.Controls.ControlTemplate> aux propriétés publiques définies par le bouton.

 [!code-xaml[VSMButtonTemplate#TemplateBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#templatebinding)]

 Dans cet exemple, le <xref:System.Windows.Controls.Grid> a son <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType> modèle de propriété lié à <xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType>. Étant donné que <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType> est lié à un modèle, vous pouvez créer plusieurs boutons qui utilisent le même <xref:System.Windows.Controls.ControlTemplate> et définir la <xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType> sur différentes valeurs sur chaque bouton. Si <xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType> n’était pas un modèle lié à une propriété d’un élément dans la <xref:System.Windows.Controls.ControlTemplate>, la définition de la <xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType> d’un bouton n’aurait aucun impact sur l’apparence du bouton.

 Notez que les noms des deux propriétés n’ont pas besoin d’être identiques. Dans l’exemple précédent, la propriété <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A?displayProperty=nameWithType> de la <xref:System.Windows.Controls.Button> est liée par modèle à la propriété <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A?displayProperty=nameWithType> de l' <xref:System.Windows.Controls.ContentPresenter>. Le contenu du bouton est ainsi positionné horizontalement. <xref:System.Windows.Controls.ContentPresenter> n’a pas de propriété nommée `HorizontalContentAlignment`, mais <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A?displayProperty=nameWithType> peut être lié à <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A?displayProperty=nameWithType>. Quand vous liez par modèle une propriété, vérifiez que les propriétés source et cible sont du même type.

 La classe <xref:System.Windows.Controls.Control> définit plusieurs propriétés qui doivent être utilisées par le modèle de contrôle pour avoir un effet sur le contrôle lorsqu’elles sont définies. La façon dont le <xref:System.Windows.Controls.ControlTemplate> utilise la propriété dépend de la propriété. Le <xref:System.Windows.Controls.ControlTemplate> doit utiliser la propriété de l’une des manières suivantes :

- Un élément dans le modèle <xref:System.Windows.Controls.ControlTemplate> est lié à la propriété.

- Un élément dans le <xref:System.Windows.Controls.ControlTemplate> hérite de la propriété d’un <xref:System.Windows.FrameworkElement>parent.

 Le tableau suivant répertorie les propriétés visuelles héritées par un contrôle de la classe <xref:System.Windows.Controls.Control>. Il indique également si le modèle de contrôle par défaut d’un contrôle utilise la valeur de la propriété héritée ou s’il doit être lié par modèle.

|Property|Méthode d’utilisation|
|--------------|------------------|
|<xref:System.Windows.Controls.Control.Background%2A>|Liaison de modèle|
|<xref:System.Windows.Controls.Control.BorderThickness%2A>|Liaison de modèle|
|<xref:System.Windows.Controls.Control.BorderBrush%2A>|Liaison de modèle|
|<xref:System.Windows.Controls.Control.FontFamily%2A>|Héritage de propriété ou liaison de modèle|
|<xref:System.Windows.Controls.Control.FontSize%2A>|Héritage de propriété ou liaison de modèle|
|<xref:System.Windows.Controls.Control.FontStretch%2A>|Héritage de propriété ou liaison de modèle|
|<xref:System.Windows.Controls.Control.FontWeight%2A>|Héritage de propriété ou liaison de modèle|
|<xref:System.Windows.Controls.Control.Foreground%2A>|Héritage de propriété ou liaison de modèle|
|<xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A>|Liaison de modèle|
|<xref:System.Windows.Controls.Control.Padding%2A>|Liaison de modèle|
|<xref:System.Windows.Controls.Control.VerticalContentAlignment%2A>|Liaison de modèle|

 Le tableau répertorie uniquement les propriétés visuelles héritées de la classe <xref:System.Windows.Controls.Control>. Outre les propriétés listées dans le tableau, un contrôle peut également hériter des propriétés <xref:System.Windows.FrameworkElement.DataContext%2A>, <xref:System.Windows.FrameworkElement.Language%2A>et <xref:System.Windows.Controls.TextBlock.TextDecorations%2A> de l’élément Framework parent.

 En outre, si le <xref:System.Windows.Controls.ContentPresenter> se trouve dans le <xref:System.Windows.Controls.ControlTemplate> d’un <xref:System.Windows.Controls.ContentControl>, le <xref:System.Windows.Controls.ContentPresenter> est automatiquement lié aux propriétés <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> et <xref:System.Windows.Controls.ContentControl.Content%2A>. De même, un <xref:System.Windows.Controls.ItemsPresenter> qui se trouve dans le <xref:System.Windows.Controls.ControlTemplate> d’un <xref:System.Windows.Controls.ItemsControl> est automatiquement lié aux propriétés <xref:System.Windows.Controls.ItemsControl.Items%2A> et <xref:System.Windows.Controls.ItemsPresenter>.

 L’exemple suivant crée deux boutons qui utilisent le <xref:System.Windows.Controls.ControlTemplate> défini dans l’exemple précédent. L’exemple définit les propriétés <xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>et <xref:System.Windows.Controls.Control.FontSize%2A> sur chaque bouton. La définition de la propriété <xref:System.Windows.Controls.Control.Background%2A> a un effet, car elle est liée par modèle dans le <xref:System.Windows.Controls.ControlTemplate>. Même si les propriétés <xref:System.Windows.Controls.Control.Foreground%2A> et <xref:System.Windows.Controls.Control.FontSize%2A> ne sont pas liées par modèle, leur définition a un effet, car leurs valeurs sont héritées.

 [!code-xaml[VSMButtonTemplate#ButtonDeclaration](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#buttondeclaration)]

 L’exemple précédent produit une sortie similaire à celle de l’illustration suivante.

 ![Deux boutons, un bleu et un violet.](./media/ndp-buttontwo.png "NDP_ButtonTwo")
Deux boutons avec des couleurs d’arrière-plan différentes

<a name="changing_the_appearance_of_a_control_depending_on_its_state"></a>
## <a name="changing-the-appearance-of-a-control-depending-on-its-state"></a>Modification de l’apparence d’un contrôle en fonction de son état
 La différence entre un bouton avec son apparence par défaut et le bouton de l’exemple précédent est que le bouton par défaut change légèrement selon son état. Par exemple, l’apparence du bouton par défaut change quand l’utilisateur clique dessus ou pointe sur lui. Bien que le <xref:System.Windows.Controls.ControlTemplate> ne modifie pas la fonctionnalité d’un contrôle, il modifie le comportement visuel du contrôle. Un comportement visuel décrit l’apparence du contrôle quand ce dernier est dans un état particulier. Pour comprendre la différence entre la fonctionnalité et le comportement visuel d’un contrôle, considérez l’exemple du bouton. La fonctionnalité du bouton consiste à déclencher l’événement <xref:System.Windows.Controls.Primitives.ButtonBase.Click> lorsque l’utilisateur clique dessus, mais le comportement visuel du bouton a pour effet de modifier son apparence lorsqu’il est pointé ou enfoncé.

 Vous utilisez <xref:System.Windows.VisualState> objets pour spécifier l’apparence d’un contrôle lorsqu’il est dans un certain état. Une <xref:System.Windows.VisualState> contient une <xref:System.Windows.Media.Animation.Storyboard> qui modifie l’apparence des éléments qui se trouvent dans le <xref:System.Windows.Controls.ControlTemplate>. Vous n’avez pas à écrire de code pour que cela se produise, car la logique du contrôle modifie l’État à l’aide de l' <xref:System.Windows.VisualStateManager>. Lorsque le contrôle passe à l’état spécifié par la propriété <xref:System.Windows.VisualState.Name%2A?displayProperty=nameWithType>, le <xref:System.Windows.Media.Animation.Storyboard> commence. Lorsque le contrôle quitte l’État, le <xref:System.Windows.Media.Animation.Storyboard> s’arrête.

 L’exemple suivant montre le <xref:System.Windows.VisualState> qui modifie l’apparence d’un <xref:System.Windows.Controls.Button> lorsque le pointeur de la souris se trouve sur celui-ci. Le <xref:System.Windows.Media.Animation.Storyboard> modifie la couleur de bordure du bouton en modifiant la couleur du `BorderBrush`. Si vous vous référez au <xref:System.Windows.Controls.ControlTemplate> exemple au début de cette rubrique, vous vous souviendrez que `BorderBrush` est le nom de la <xref:System.Windows.Media.SolidColorBrush> qui est assignée au <xref:System.Windows.Controls.Border.Background%2A> du <xref:System.Windows.Controls.Border>.

 [!code-xaml[VSMButtonTemplate#4](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#4)]

 Le contrôle est chargé de définir les états dans le cadre de son contrat de contrôle, lequel est décrit en détail dans [Personnalisation des autres contrôles grâce à une bonne compréhension du contrat de contrôle](#customizing_other_controls_by_understanding_the_control_contract), plus loin dans cette rubrique. Le tableau suivant répertorie les États spécifiés pour le <xref:System.Windows.Controls.Button>.

|Nom VisualState|Nom VisualStateGroup|Description|
|----------------------|---------------------------|-----------------|
|Normale|CommonStates|État par défaut.|
|MouseOver|CommonStates|Le pointeur de souris est positionné sur le contrôle.|
|Appuyé|CommonStates|Le contrôle est enfoncé.|
|Disabled|CommonStates|Le contrôle est désactivé.|
|Avec focus|FocusStates|Le contrôle a le focus.|
|Sans focus|FocusStates|Le contrôle n’a pas le focus.|

 Le <xref:System.Windows.Controls.Button> définit deux groupes d’États : le groupe `CommonStates` contient les États `Normal`, `MouseOver`, `Pressed`et `Disabled`. le groupe `FocusStates` contient les états `Focused` et `Unfocused`. Les états d’un même groupe d’état s’excluent mutuellement. Le contrôle est toujours dans un état par groupe. Par exemple, une <xref:System.Windows.Controls.Button> peut avoir le focus même lorsque le pointeur de la souris ne se trouve pas sur celle-ci, donc un <xref:System.Windows.Controls.Button> dans l’état du `Focused` peut être dans l’État `MouseOver`, `Pressed`ou `Normal`.

 Vous ajoutez des objets <xref:System.Windows.VisualState> aux objets <xref:System.Windows.VisualStateGroup>. Vous ajoutez des objets <xref:System.Windows.VisualStateGroup> à la propriété jointe <xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType>. L’exemple suivant définit les objets <xref:System.Windows.VisualState> pour les États `Normal`, `MouseOver`et `Pressed`, qui se trouvent tous dans le groupe `CommonStates`. Le <xref:System.Windows.VisualState.Name%2A> de chaque <xref:System.Windows.VisualState> correspond au nom dans le tableau précédent. L’état `Disabled` et les états du groupe `FocusStates` sont omis pour que l’exemple reste concis, mais ils figurent dans l’exemple complet fourni à la fin de cette rubrique.

> [!NOTE]
> Veillez à définir la propriété jointe <xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType> sur le <xref:System.Windows.FrameworkElement> racine de la <xref:System.Windows.Controls.ControlTemplate>.

 [!code-xaml[VSMButtonTemplate#VisualStates](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#visualstates)]

 L’exemple précédent produit une sortie similaire à celle des illustrations suivantes.

 ![Bouton avec un modèle de contrôle personnalisé.](./media/ndp-buttonnormal.png "NDP_ButtonNormal")
Bouton qui utilise un modèle de contrôle personnalisé dans l’état normal

 ![Bouton avec une bordure rouge.](./media/ndp-buttonmouseover.png "NDP_ButtonMouseOver")
Bouton qui utilise un modèle de contrôle personnalisé dans l’état de pointage avec la souris

 ![Bordure transparente sur un bouton enfoncé.](./media/ndp-buttonpressed.png "NDP_ButtonPressed")
Bouton qui utilise un modèle de contrôle personnalisé dans l’état enfoncé

 Pour trouver les états visuels pour les contrôles inclus avec [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], consultez [Styles et modèles Control](control-styles-and-templates.md).

<a name="specifying_the_behavior_of_a_control_when_it_transitions_between_states"></a>
## <a name="specifying-the-behavior-of-a-control-when-it-transitions-between-states"></a>Spécification du comportement d’un contrôle durant les transitions entre états
 Dans l’exemple précédent, l’apparence du bouton change également quand l’utilisateur clique dessus, mais à moins que le bouton ne soit enfoncé pendant une seconde complète, aucun effet n’est visible pour l’utilisateur. Par défaut, une seconde est nécessaire au déclenchement de l’animation. Étant donné que les utilisateurs sont susceptibles de cliquer et de relâcher un bouton en moins de temps, la rétroaction visuelle n’est pas efficace si vous laissez la <xref:System.Windows.Controls.ControlTemplate> dans son état par défaut.

 Vous pouvez spécifier la durée nécessaire à l’animation pour faire passer sans heurt un contrôle d’un État à un autre en ajoutant <xref:System.Windows.VisualTransition> objets au <xref:System.Windows.Controls.ControlTemplate>. Lorsque vous créez un <xref:System.Windows.VisualTransition>, vous spécifiez un ou plusieurs des éléments suivants :

- Temps nécessaire à une transition entre des états

- Changements supplémentaires dans l’apparence du contrôle durant la transition

- À quel état la <xref:System.Windows.VisualTransition> est appliquée.

### <a name="specifying-the-duration-of-a-transition"></a>Spécification de la durée d’une transition
 Vous pouvez spécifier la durée d’une transition en définissant la propriété <xref:System.Windows.VisualTransition.GeneratedDuration%2A>. L’exemple précédent a une <xref:System.Windows.VisualState> qui spécifie que la bordure du bouton devient transparente lorsque le bouton est enfoncé, mais que l’animation prend trop de temps pour être perceptible si le bouton est rapidement enfoncé et relâché. Vous pouvez utiliser une <xref:System.Windows.VisualTransition> pour spécifier la durée pendant laquelle le contrôle passe à l’état enfoncé. L’exemple suivant spécifie que le contrôle passe à l’état Pressed après un centième de seconde.

 [!code-xaml[VSMButtonTemplate#PressedTransition](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#pressedtransition)]

### <a name="specifying-changes-to-the-controls-appearance-during-a-transition"></a>Spécification de changements de l’apparence du contrôle durant une transition
 Le <xref:System.Windows.VisualTransition> contient une <xref:System.Windows.Media.Animation.Storyboard> qui commence lorsque le contrôle passe d’un État à un autre. Par exemple, vous pouvez spécifier qu’une animation particulière a lieu quand le contrôle passe de l’état `MouseOver` à l’état `Normal`. L’exemple suivant crée une <xref:System.Windows.VisualTransition> qui spécifie que lorsque l’utilisateur éloigne le pointeur de la souris du bouton, la bordure du bouton passe au bleu, puis au jaune, puis au noir en 1,5 secondes.

 [!code-xaml[VSMButtonTemplate#8](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#8)]

### <a name="specifying-when-a-visualtransition-is-applied"></a>Spécification du moment où VisualTransition est appliqué
 Un <xref:System.Windows.VisualTransition> peut être limité pour ne s’appliquer qu’à certains États, ou il peut être appliqué chaque fois que le contrôle passe d’un État à un autre. Dans l’exemple précédent, le <xref:System.Windows.VisualTransition> est appliqué lorsque le contrôle passe de l’État `MouseOver` à l’État `Normal` ; dans l’exemple qui précède, le <xref:System.Windows.VisualTransition> est appliqué lorsque le contrôle passe à l’État `Pressed`. Vous limitez le moment auquel une <xref:System.Windows.VisualTransition> est appliquée en définissant les propriétés <xref:System.Windows.VisualTransition.To%2A> et <xref:System.Windows.VisualTransition.From%2A>. Le tableau suivant décrit les niveaux de restriction, du plus restrictif au moins restrictif.

|Type de restriction|Valeur de From|Valeur de To|
|-------------------------|-------------------|-----------------|
|D’un état spécifié à un autre état spécifié|Nom d’un <xref:System.Windows.VisualState>|Nom d’un <xref:System.Windows.VisualState>|
|De n’importe quel état à un état spécifié|Non défini|Nom d’un <xref:System.Windows.VisualState>|
|D’un état spécifié à n’importe quel état|Nom d’un <xref:System.Windows.VisualState>|Non défini|
|De n’importe quel état à n’importe quel autre état|Non défini|Non défini|

 Vous pouvez avoir plusieurs objets <xref:System.Windows.VisualTransition> dans un <xref:System.Windows.VisualStateGroup> qui font référence au même État, mais ils seront utilisés dans l’ordre indiqué par le tableau précédent. Dans l’exemple suivant, il existe deux objets <xref:System.Windows.VisualTransition>. Lorsque le contrôle passe de l’État `Pressed` à l’État `MouseOver`, le <xref:System.Windows.VisualTransition> qui a à la fois le <xref:System.Windows.VisualTransition.From%2A> et le jeu de <xref:System.Windows.VisualTransition.To%2A> est utilisé. Quand le contrôle passe d’un état autre que `Pressed` à l’état `MouseOver`, l’autre état est utilisé.

 [!code-xaml[VSMButtonTemplate#7](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#7)]

 La <xref:System.Windows.VisualStateGroup> a une propriété <xref:System.Windows.VisualStateGroup.Transitions%2A> qui contient les objets <xref:System.Windows.VisualTransition> qui s’appliquent aux objets <xref:System.Windows.VisualState> dans le <xref:System.Windows.VisualStateGroup>. En tant que <xref:System.Windows.Controls.ControlTemplate> auteur, vous êtes libre d’inclure les <xref:System.Windows.VisualTransition> souhaitées. Toutefois, si les propriétés <xref:System.Windows.VisualTransition.To%2A> et <xref:System.Windows.VisualTransition.From%2A> sont définies sur des noms d’État qui ne sont pas dans le <xref:System.Windows.VisualStateGroup>, la <xref:System.Windows.VisualTransition> est ignorée.

 L’exemple suivant montre les <xref:System.Windows.VisualStateGroup> pour le `CommonStates`. L’exemple définit une <xref:System.Windows.VisualTransition> pour chacune des transitions suivantes du bouton.

- À l’état `Pressed`

- À l’état `MouseOver`

- De l’état `Pressed` à l’état `MouseOver`

- De l’état `MouseOver` à l’état `Normal`

 [!code-xaml[VSMButtonTemplate#VisualTransitions](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#visualtransitions)]

<a name="customizing_other_controls_by_understanding_the_control_contract"></a>
## <a name="customizing-other-controls-by-understanding-the-control-contract"></a>Personnalisation des autres contrôles grâce à une bonne compréhension du contrat de contrôle
 Un contrôle qui utilise une <xref:System.Windows.Controls.ControlTemplate> pour spécifier sa structure visuelle (à l’aide d’objets <xref:System.Windows.FrameworkElement>) et le comportement visuel (à l’aide d’objets <xref:System.Windows.VisualState>) utilise le modèle de contrôle des parties. Bon nombre des contrôles inclus avec [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 4 utilisent ce modèle. Les parties qu’un <xref:System.Windows.Controls.ControlTemplate> auteur doit connaître sont communiquées par le biais du contrat de contrôle. Quand vous connaissez les composants d’un contrat de contrôle, vous pouvez personnaliser l’apparence de tout contrôle qui utilise le modèle de contrôle des composants.

 Un contrat de contrôle comporte trois éléments :

- les éléments visuels utilisés par la logique du contrôle ;

- les états du contrôle et le groupe auquel appartient chaque état ;

- les propriétés publiques qui affectent visuellement le contrôle.

### <a name="visual-elements-in-the-control-contract"></a>Éléments visuels du contrat de contrôle
 Parfois, la logique d’un contrôle interagit avec un <xref:System.Windows.FrameworkElement> qui se trouve dans le <xref:System.Windows.Controls.ControlTemplate>. Par exemple, le contrôle peut gérer un événement de l’un de ses éléments. Lorsqu’un contrôle s’attend à trouver un <xref:System.Windows.FrameworkElement> particulier dans le <xref:System.Windows.Controls.ControlTemplate>, il doit transmettre ces informations à l’auteur de la <xref:System.Windows.Controls.ControlTemplate>. Le contrôle utilise la <xref:System.Windows.TemplatePartAttribute> pour communiquer le type d’élément attendu et le nom de l’élément. Le <xref:System.Windows.Controls.Button> n’a pas de parties <xref:System.Windows.FrameworkElement> dans son contrat de contrôle, mais d’autres contrôles, tels que le <xref:System.Windows.Controls.ComboBox>, font.

 L’exemple suivant montre les objets <xref:System.Windows.TemplatePartAttribute> spécifiés sur la classe <xref:System.Windows.Controls.ComboBox>. La logique de <xref:System.Windows.Controls.ComboBox> s’attend à trouver un <xref:System.Windows.Controls.TextBox> nommé `PART_EditableTextBox` et un <xref:System.Windows.Controls.Primitives.Popup> nommé `PART_Popup` dans son <xref:System.Windows.Controls.ControlTemplate>.

 [!code-csharp[VSMButtonTemplate#ComboBoxContract](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/controlcontracts.cs#comboboxcontract)]
 [!code-vb[VSMButtonTemplate#ComboBoxContract](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmbuttontemplate/visualbasic/window1.xaml.vb#comboboxcontract)]

 L’exemple suivant montre une <xref:System.Windows.Controls.ControlTemplate> simplifiée pour le <xref:System.Windows.Controls.ComboBox> qui comprend les éléments spécifiés par les objets <xref:System.Windows.TemplatePartAttribute> sur la classe <xref:System.Windows.Controls.ComboBox>.

 [!code-xaml[VSMButtonTemplate#ComboBoxTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/window1.xaml#comboboxtemplate)]

### <a name="states-in-the-control-contract"></a>États du contrat de contrôle
 Les états d’un contrôle font également partie du contrat de contrôle. L’exemple de création d’une <xref:System.Windows.Controls.ControlTemplate> pour un <xref:System.Windows.Controls.Button> montre comment spécifier l’apparence d’un <xref:System.Windows.Controls.Button> en fonction de ses États. Vous créez un <xref:System.Windows.VisualState> pour chaque état spécifié et placez tous les objets <xref:System.Windows.VisualState> qui partagent un <xref:System.Windows.TemplateVisualStateAttribute.GroupName%2A> dans une <xref:System.Windows.VisualStateGroup>, comme décrit dans [modification de l’apparence d’un contrôle en fonction de son état](#changing_the_appearance_of_a_control_depending_on_its_state) précédemment dans cette rubrique. Les contrôles tiers doivent spécifier des États à l’aide de l' <xref:System.Windows.TemplateVisualStateAttribute>, qui permet aux outils du concepteur, tels que les [Concepteur XAML](/visualstudio/xaml-tools/designing-xaml-in-visual-studio) dans Visual Studio et Blend pour Visual Studio, d’exposer les États du contrôle pour la création de modèles de contrôle.

 Pour trouver le contrat de contrôle pour les contrôles inclus avec [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], consultez [Styles et modèles Control](control-styles-and-templates.md).

### <a name="properties-in-the-control-contract"></a>Propriétés du contrat de contrôle
 Les propriétés publiques qui affectent visuellement le contrôle sont également incluses dans le contrat de contrôle. Vous pouvez définir ces propriétés pour modifier l’apparence du contrôle sans créer de <xref:System.Windows.Controls.ControlTemplate>. Vous pouvez également utiliser l’extension de balisage [TemplateBinding](../advanced/templatebinding-markup-extension.md) pour lier les propriétés des éléments qui se trouvent dans le <xref:System.Windows.Controls.ControlTemplate> aux propriétés publiques définies par l' <xref:System.Windows.Controls.Button>.

 L’exemple suivant illustre le contrat de contrôle pour le bouton.

 [!code-csharp[VSMButtonTemplate#ButtonContract](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/controlcontracts.cs#buttoncontract)]
 [!code-vb[VSMButtonTemplate#ButtonContract](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmbuttontemplate/visualbasic/window1.xaml.vb#buttoncontract)]

 Lors de la création d’un <xref:System.Windows.Controls.ControlTemplate>, il est souvent plus facile de commencer avec un <xref:System.Windows.Controls.ControlTemplate> existant et d’y apporter des modifications. Pour modifier un <xref:System.Windows.Controls.ControlTemplate>existant, vous pouvez effectuer l’une des opérations suivantes :

- Utilisez un concepteur, tel que Blend pour Visual Studio, qui fournit une interface utilisateur graphique pour la création de modèles de contrôle. Pour plus d’informations, consultez [Définition d’un style pour un contrôle prenant en charge les modèles](https://go.microsoft.com/fwlink/?LinkId=161153).

- Récupérez le <xref:System.Windows.Controls.ControlTemplate> par défaut et modifiez-le. Pour trouver les modèles de contrôle par défaut compris dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], consultez [Thèmes WPF par défaut](https://go.microsoft.com/fwlink/?LinkID=158252).

<a name="complete_example"></a>
## <a name="complete-example"></a>Exemple complet
 L’exemple suivant montre le <xref:System.Windows.Controls.Button>complet<xref:System.Windows.Controls.ControlTemplate> abordé dans cette rubrique.

 [!code-xaml[VSMButtonTemplate#3](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#3)]

## <a name="see-also"></a>Voir aussi

- [Application d’un style et création de modèles](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
