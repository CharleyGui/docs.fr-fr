---
title: Création d'un contrôle avec une apparence personnalisable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], customizing
- VisualStateManager [WPF], managing the state of a control
- ControlTemplate [WPF], customizing appearance
- controls [WPF], defining the visual structure and behavior of
- customizing appearance [WPF], ControlTemplate
- managing control states [WPF], VisualStateManager
- VisualStateManager [WPF], best practice
ms.assetid: 9e356d3d-a3d0-4b01-a25f-2d43e4d53fe5
ms.openlocfilehash: d9cf092cf47d4fb70b15033d039777d3279b633a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283570"
---
# <a name="creating-a-control-that-has-a-customizable-appearance"></a>Création d'un contrôle avec une apparence personnalisable

<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] vous donne la possibilité de créer un contrôle dont l’apparence peut être personnalisée. Par exemple, vous pouvez modifier l’apparence d’un <xref:System.Windows.Controls.CheckBox> au-delà de ce que les propriétés de paramètre feraient en créant une <xref:System.Windows.Controls.ControlTemplate>. L’illustration suivante montre une <xref:System.Windows.Controls.CheckBox> qui utilise un <xref:System.Windows.Controls.ControlTemplate> par défaut et un <xref:System.Windows.Controls.CheckBox> qui utilise une <xref:System.Windows.Controls.ControlTemplate>personnalisée.

![Case à cocher avec le modèle de contrôle par défaut.](./media/ndp-checkboxdefault.png "NDP_CheckBoxDefault")
Case à cocher qui utilise le modèle de contrôle par défaut

![Case à cocher avec un modèle de contrôle personnalisé.](./media/ndp-checkboxcustom.png "NDP_CheckBoxCustom")
Case à cocher qui utilise un modèle de contrôle personnalisé

Si vous suivez le modèle des parties et des États lorsque vous créez un contrôle, l’apparence de votre contrôle sera personnalisable. Les outils de conception tels que Blend pour Visual Studio prennent en charge le modèle des parties et des États. par conséquent, lorsque vous suivez ce modèle, votre contrôle est personnalisable dans ces types d’applications.  Cette rubrique décrit le modèle de composants et d’États et comment le suivre lorsque vous créez votre propre contrôle. Cette rubrique utilise un exemple de contrôle personnalisé, `NumericUpDown`, pour illustrer la philosophie de ce modèle.  Le contrôle `NumericUpDown` affiche une valeur numérique, qu’un utilisateur peut augmenter ou diminuer en cliquant sur les boutons du contrôle.  L’illustration suivante montre le contrôle `NumericUpDown` abordé dans cette rubrique.

![Contrôle personnalisé NumericUpDown.](./media/ndp-numericupdown.png "NDP_NumericUPDown")
Contrôle NumericUpDown personnalisé

Cette rubrique contient les sections suivantes :

- [Composants requis](#prerequisites)

- [Modèle des parties et des États](#parts_and_states_model)

- [Définition de la structure visuelle et du comportement visuel d’un contrôle dans un ControlTemplate](#defining_the_visual_structure_and_visual_behavior_of_a_control_in_a_controltemplate)

- [Utilisation de parties du ControlTemplate dans le code](#using_parts_of_the_controltemplate_in_code)

- [Fourniture du contrat de contrôle](#providing_the_control_contract)

- [Exemple complet](#complete_example)

<a name="prerequisites"></a>

## <a name="prerequisites"></a>Conditions préalables requises

Cette rubrique suppose que vous savez comment créer un <xref:System.Windows.Controls.ControlTemplate> pour un contrôle existant, que vous connaissez bien les éléments d’un contrat de contrôle et que vous comprenez les concepts abordés dans [créer un modèle pour un contrôle](../../../desktop-wpf/themes/how-to-create-apply-template.md).

> [!NOTE]
> Pour créer un contrôle dont l’apparence peut être personnalisée, vous devez créer un contrôle qui hérite de la classe <xref:System.Windows.Controls.Control> ou de l’une de ses sous-classes autres que <xref:System.Windows.Controls.UserControl>.  Un contrôle qui hérite de <xref:System.Windows.Controls.UserControl> est un contrôle qui peut être rapidement créé, mais il n’utilise pas de <xref:System.Windows.Controls.ControlTemplate> et vous ne pouvez pas personnaliser son apparence.

<a name="parts_and_states_model"></a>

## <a name="parts-and-states-model"></a>Modèle des parties et des États

Le modèle parties et États spécifie comment définir la structure visuelle et le comportement visuel d’un contrôle. Pour suivre le modèle des parties et des États, vous devez effectuer les opérations suivantes :

- Définir la structure visuelle et le comportement visuel dans le <xref:System.Windows.Controls.ControlTemplate> d’un contrôle.

- Suivez certaines meilleures pratiques lorsque la logique de votre contrôle interagit avec des parties du modèle de contrôle.

- Fournissez un contrat de contrôle pour spécifier ce qui doit être inclus dans le <xref:System.Windows.Controls.ControlTemplate>.

Lorsque vous définissez la structure visuelle et le comportement visuel dans le <xref:System.Windows.Controls.ControlTemplate> d’un contrôle, les créateurs d’applications peuvent modifier la structure visuelle et le comportement visuel de votre contrôle en créant un nouveau <xref:System.Windows.Controls.ControlTemplate> au lieu d’écrire du code.   Vous devez fournir un contrat de contrôle qui indique aux auteurs de l’application que <xref:System.Windows.FrameworkElement> objets et les États doivent être définis dans le <xref:System.Windows.Controls.ControlTemplate>. Vous devez suivre certaines meilleures pratiques lorsque vous interagissez avec les composants de la <xref:System.Windows.Controls.ControlTemplate> afin que votre contrôle gère correctement un <xref:System.Windows.Controls.ControlTemplate>incomplet.  Si vous suivez ces trois principes, les créateurs d’applications peuvent créer un <xref:System.Windows.Controls.ControlTemplate> pour votre contrôle tout aussi facilement que pour les contrôles fournis avec [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  La section suivante explique en détail chacune de ces recommandations.

<a name="defining_the_visual_structure_and_visual_behavior_of_a_control_in_a_controltemplate"></a>

## <a name="defining-the-visual-structure-and-visual-behavior-of-a-control-in-a-controltemplate"></a>Définition de la structure visuelle et du comportement visuel d’un contrôle dans un ControlTemplate

Lorsque vous créez votre contrôle personnalisé à l’aide du modèle de composants et d’États, vous définissez la structure visuelle et le comportement visuel du contrôle dans son <xref:System.Windows.Controls.ControlTemplate> plutôt que dans sa logique.  La structure visuelle d’un contrôle est l’composite d' <xref:System.Windows.FrameworkElement> objets qui composent le contrôle.  Le comportement visuel est le mode d’affichage du contrôle lorsqu’il est dans un certain état.   Pour plus d’informations sur la création d’un <xref:System.Windows.Controls.ControlTemplate> qui spécifie la structure visuelle et le comportement visuel d’un contrôle, consultez [créer un modèle pour un contrôle](../../../desktop-wpf/themes/how-to-create-apply-template.md).

Dans l’exemple du contrôle `NumericUpDown`, la structure visuelle comprend deux contrôles <xref:System.Windows.Controls.Primitives.RepeatButton> et un <xref:System.Windows.Controls.TextBlock>.  Si vous ajoutez ces contrôles dans le code du contrôle `NumericUpDown`, par exemple dans son constructeur, les positions de ces contrôles ne peuvent pas être modifiées.  Au lieu de définir la structure visuelle et le comportement visuel du contrôle dans son code, vous devez le définir dans l' <xref:System.Windows.Controls.ControlTemplate>.  Un développeur d’applications peut ensuite personnaliser la position des boutons et <xref:System.Windows.Controls.TextBlock> et spécifier le comportement qui se produit quand `Value` est négatif, car le <xref:System.Windows.Controls.ControlTemplate> peut être remplacé.

L’exemple suivant illustre la structure visuelle du contrôle `NumericUpDown`, qui comprend une <xref:System.Windows.Controls.Primitives.RepeatButton> pour augmenter `Value`, une <xref:System.Windows.Controls.Primitives.RepeatButton> pour réduire `Value`et une <xref:System.Windows.Controls.TextBlock> pour afficher `Value`.

[!code-xaml[VSMCustomControl#VisualStructure](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/window1.xaml#visualstructure)]

Un comportement visuel du contrôle `NumericUpDown` est que la valeur est en rouge si elle est négative.  Si vous modifiez la <xref:System.Windows.Controls.TextBlock.Foreground%2A> du <xref:System.Windows.Controls.TextBlock> dans le code lorsque le `Value` est négatif, le `NumericUpDown` affiche toujours une valeur négative rouge. Vous spécifiez le comportement visuel du contrôle dans le <xref:System.Windows.Controls.ControlTemplate> en ajoutant des objets <xref:System.Windows.VisualState> à la <xref:System.Windows.Controls.ControlTemplate>.  L’exemple suivant montre les objets <xref:System.Windows.VisualState> pour les États `Positive` et `Negative`.  `Positive` et `Negative` s’excluent mutuellement (le contrôle est toujours exactement dans l’un des deux), l’exemple place les objets <xref:System.Windows.VisualState> dans un <xref:System.Windows.VisualStateGroup>unique.  Lorsque le contrôle passe à l’État `Negative`, la <xref:System.Windows.Controls.TextBlock.Foreground%2A> du <xref:System.Windows.Controls.TextBlock> devient rouge.  Lorsque le contrôle est dans l’État `Positive`, le <xref:System.Windows.Controls.TextBlock.Foreground%2A> retourne à sa valeur d’origine.  Pour plus d’informations sur la définition d’objets <xref:System.Windows.VisualState> dans un <xref:System.Windows.Controls.ControlTemplate>, voir [créer un modèle pour un contrôle](../../../desktop-wpf/themes/how-to-create-apply-template.md).

> [!NOTE]
> Veillez à définir la propriété jointe <xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType> sur le <xref:System.Windows.FrameworkElement> racine de la <xref:System.Windows.Controls.ControlTemplate>.

[!code-xaml[VSMCustomControl#ValueStates](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/window1.xaml#valuestates)]

<a name="using_parts_of_the_controltemplate_in_code"></a>

## <a name="using-parts-of-the-controltemplate-in-code"></a>Utilisation de parties du ControlTemplate dans le code

Un auteur de <xref:System.Windows.Controls.ControlTemplate> peut omettre des objets <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.VisualState>, intentionnellement ou par erreur, mais la logique de votre contrôle peut avoir besoin de ces parties pour fonctionner correctement. Le modèle des parties et des États spécifie que votre contrôle doit être résilient à une <xref:System.Windows.Controls.ControlTemplate> qui manque <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.VisualState> objets.  Votre contrôle ne doit pas lever d’exception ou signaler une erreur si un <xref:System.Windows.FrameworkElement>, <xref:System.Windows.VisualState>ou <xref:System.Windows.VisualStateGroup> est manquant dans le <xref:System.Windows.Controls.ControlTemplate>. Cette section décrit les pratiques recommandées pour l’interaction avec les objets <xref:System.Windows.FrameworkElement> et la gestion des États.

### <a name="anticipate-missing-frameworkelement-objects"></a>Anticiper les objets FrameworkElement manquants

Lorsque vous définissez <xref:System.Windows.FrameworkElement> objets dans le <xref:System.Windows.Controls.ControlTemplate>, la logique de votre contrôle peut avoir besoin d’interagir avec certaines d’entre elles.  Par exemple, le contrôle `NumericUpDown` s’abonne à l’événement <xref:System.Windows.Controls.Primitives.ButtonBase.Click> buttons pour augmenter ou diminuer `Value` et définit la propriété <xref:System.Windows.Controls.TextBlock.Text%2A> de <xref:System.Windows.Controls.TextBlock> sur `Value`. Si une <xref:System.Windows.Controls.ControlTemplate> personnalisée omet le <xref:System.Windows.Controls.TextBlock> ou les boutons, il est acceptable que le contrôle perde certaines de ses fonctionnalités, mais vous devez vous assurer que votre contrôle ne provoque pas d’erreur. Par exemple, si un <xref:System.Windows.Controls.ControlTemplate> ne contient pas les boutons pour modifier `Value`, le `NumericUpDown` perd cette fonctionnalité, mais une application qui utilise le <xref:System.Windows.Controls.ControlTemplate> continuera à s’exécuter.

Les pratiques suivantes permettent de s’assurer que votre contrôle répond correctement aux objets <xref:System.Windows.FrameworkElement> manquants :

1. Définissez l’attribut `x:Name` pour chaque <xref:System.Windows.FrameworkElement> que vous devez référencer dans le code.

2. Définissez les propriétés privées de chaque <xref:System.Windows.FrameworkElement> avec lequel vous devez interagir.

3. Abonnez-vous et annulez l’abonnement des événements que votre contrôle gère dans l’accesseur Set de la propriété <xref:System.Windows.FrameworkElement>.

4. Définissez les propriétés de <xref:System.Windows.FrameworkElement> que vous avez définies à l’étape 2 dans la méthode <xref:System.Windows.FrameworkElement.OnApplyTemplate%2A>. C’est la première fois que le <xref:System.Windows.FrameworkElement> dans le <xref:System.Windows.Controls.ControlTemplate> est disponible pour le contrôle. Utilisez la `x:Name` du <xref:System.Windows.FrameworkElement> pour l’extraire du <xref:System.Windows.Controls.ControlTemplate>.

5. Vérifiez que le <xref:System.Windows.FrameworkElement> n’est pas `null` avant d’accéder à ses membres.  S’il s’agit d' `null`, ne signalez pas d’erreur.

Les exemples suivants montrent comment le contrôle `NumericUpDown` interagit avec les objets <xref:System.Windows.FrameworkElement> conformément aux recommandations de la liste précédente.

Dans l’exemple qui définit la structure visuelle du contrôle `NumericUpDown` dans le <xref:System.Windows.Controls.ControlTemplate>, l’attribut `x:Name` de la <xref:System.Windows.Controls.Primitives.RepeatButton> qui augmente `Value` a la valeur `UpButton`.  L’exemple suivant déclare une propriété appelée `UpButtonElement` qui représente le <xref:System.Windows.Controls.Primitives.RepeatButton> déclaré dans le <xref:System.Windows.Controls.ControlTemplate>. L’accesseur `set` se désabonne d’abord à l’événement <xref:System.Windows.Controls.Primitives.ButtonBase.Click> du bouton si `UpDownElement` n’est pas `null`, puis définit la propriété et s’abonne à l’événement <xref:System.Windows.Controls.Primitives.ButtonBase.Click>. Une propriété est également définie, mais elle n’est pas indiquée ici, pour l’autre <xref:System.Windows.Controls.Primitives.RepeatButton>, appelée `DownButtonElement`.

[!code-csharp[VSMCustomControl#UpButtonProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#upbuttonproperty)]
[!code-vb[VSMCustomControl#UpButtonProperty](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#upbuttonproperty)]

L’exemple suivant montre les <xref:System.Windows.FrameworkElement.OnApplyTemplate%2A> pour le contrôle `NumericUpDown`.  L’exemple utilise la méthode <xref:System.Windows.FrameworkElement.GetTemplateChild%2A> pour récupérer les objets <xref:System.Windows.FrameworkElement> à partir du <xref:System.Windows.Controls.ControlTemplate>.  Notez que l’exemple empêche les cas où <xref:System.Windows.FrameworkElement.GetTemplateChild%2A> trouve une <xref:System.Windows.FrameworkElement> avec le nom spécifié qui n’est pas du type attendu. Il est également conseillé d’ignorer les éléments qui ont le `x:Name` spécifié mais qui sont de type incorrect.

[!code-csharp[VSMCustomControl#ApplyTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#applytemplate)]
[!code-vb[VSMCustomControl#ApplyTemplate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#applytemplate)]

En suivant les pratiques présentées dans les exemples précédents, vous vous assurez que votre contrôle continuera à s’exécuter lorsque la <xref:System.Windows.Controls.ControlTemplate> ne dispose pas d’un <xref:System.Windows.FrameworkElement>.

### <a name="use-the-visualstatemanager-to-manage-states"></a>Utiliser le VisualStateManager pour gérer les États

Le <xref:System.Windows.VisualStateManager> effectue le suivi des États d’un contrôle et exécute la logique nécessaire pour passer d’un État à l’autre. Lorsque vous ajoutez des objets <xref:System.Windows.VisualState> à l' <xref:System.Windows.Controls.ControlTemplate>, vous les ajoutez à un <xref:System.Windows.VisualStateGroup> et vous ajoutez l' <xref:System.Windows.VisualStateGroup> à la propriété jointe <xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType> afin que le <xref:System.Windows.VisualStateManager> y ait accès.

L’exemple suivant répète l’exemple précédent qui montre les <xref:System.Windows.VisualState> objets qui correspondent aux États de `Positive` et de `Negative` du contrôle. La <xref:System.Windows.Media.Animation.Storyboard> dans le `Negative`<xref:System.Windows.VisualState> convertit la <xref:System.Windows.Controls.TextBlock.Foreground%2A> du <xref:System.Windows.Controls.TextBlock> rouge.   Lorsque le contrôle de `NumericUpDown` est dans l’État `Negative`, le Storyboard de l’état de `Negative` commence.  Ensuite, le <xref:System.Windows.Media.Animation.Storyboard> dans l’État `Negative` s’arrête lorsque le contrôle revient à l’État `Positive`.  Le <xref:System.Windows.VisualState> `Positive`n’a pas besoin de contenir un <xref:System.Windows.Media.Animation.Storyboard>, car lorsque le <xref:System.Windows.Media.Animation.Storyboard> pour le `Negative` s’arrête, le <xref:System.Windows.Controls.TextBlock.Foreground%2A> retourne à sa couleur d’origine.

[!code-xaml[VSMCustomControl#ValueStates](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/window1.xaml#valuestates)]

Notez que le <xref:System.Windows.Controls.TextBlock> reçoit un nom, mais le <xref:System.Windows.Controls.TextBlock> n’est pas dans le contrat de contrôle pour `NumericUpDown`, car la logique du contrôle ne fait jamais référence à l' <xref:System.Windows.Controls.TextBlock>.  Les éléments référencés dans le <xref:System.Windows.Controls.ControlTemplate> avoir des noms, mais n’ont pas besoin d’être inclus dans le contrat de contrôle, car il est possible qu’un nouveau <xref:System.Windows.Controls.ControlTemplate> pour le contrôle n’ait pas besoin de référencer cet élément.  Par exemple, une personne qui crée une nouvelle <xref:System.Windows.Controls.ControlTemplate> pour `NumericUpDown` peut décider de ne pas indiquer que `Value` est négatif en modifiant le <xref:System.Windows.Controls.Control.Foreground%2A>.  Dans ce cas, ni le code ni le <xref:System.Windows.Controls.ControlTemplate> ne référencent le <xref:System.Windows.Controls.TextBlock> par nom.

La logique du contrôle est responsable de la modification de l’état du contrôle. L’exemple suivant montre que le contrôle `NumericUpDown` appelle la méthode <xref:System.Windows.VisualStateManager.GoToState%2A> pour passer à l’État `Positive` lorsque `Value` a une valeur supérieure ou égale à 0, et l’État `Negative` lorsque `Value` est inférieur à 0.

[!code-csharp[VSMCustomControl#ValueStateChange](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#valuestatechange)]
[!code-vb[VSMCustomControl#ValueStateChange](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#valuestatechange)]

La méthode <xref:System.Windows.VisualStateManager.GoToState%2A> exécute la logique nécessaire pour démarrer et arrêter les storyboards de manière appropriée. Lorsqu’un contrôle appelle <xref:System.Windows.VisualStateManager.GoToState%2A> pour modifier son état, le <xref:System.Windows.VisualStateManager> effectue les opérations suivantes :

- Si le <xref:System.Windows.VisualState> que le contrôle va avoir un <xref:System.Windows.Media.Animation.Storyboard>, le Storyboard commence. Ensuite, si le <xref:System.Windows.VisualState> à partir duquel le contrôle provient a un <xref:System.Windows.Media.Animation.Storyboard>, le Storyboard se termine.

- Si le contrôle est déjà dans l’état spécifié, <xref:System.Windows.VisualStateManager.GoToState%2A> n’effectue aucune action et retourne `true`.

- Si l’état spécifié n’existe pas dans le <xref:System.Windows.Controls.ControlTemplate> de `control`, <xref:System.Windows.VisualStateManager.GoToState%2A> n’effectue aucune action et retourne `false`.

#### <a name="best-practices-for-working-with-the-visualstatemanager"></a>Meilleures pratiques pour l’utilisation du VisualStateManager

Il est recommandé d’effectuer les opérations suivantes pour conserver les États de votre contrôle :

- Utilisez les propriétés pour suivre son état.

- Créez une méthode d’assistance pour effectuer la transition entre les États.

Le contrôle `NumericUpDown` utilise sa propriété `Value` pour déterminer s’il est dans l’État `Positive` ou `Negative`.  Le contrôle `NumericUpDown` définit également les États `Focused` et `UnFocused` qui effectuent le suivi de la propriété <xref:System.Windows.UIElement.IsFocused%2A>. Si vous utilisez des États qui ne correspondent pas naturellement à une propriété du contrôle, vous pouvez définir une propriété privée pour effectuer le suivi de l’État.

Une méthode unique qui met à jour tous les États centralise les appels au <xref:System.Windows.VisualStateManager> et assure la gestion de votre code. L’exemple suivant illustre la méthode d’assistance du contrôle `NumericUpDown`, `UpdateStates`. Lorsque `Value` est supérieur ou égal à 0, le <xref:System.Windows.Controls.Control> est dans l’État `Positive`.  Lorsque `Value` est inférieur à 0, le contrôle est dans l’État `Negative`.  Lorsque <xref:System.Windows.UIElement.IsFocused%2A> est `true`, le contrôle est dans l’État `Focused` ; dans le cas contraire, il est dans l’État `Unfocused`.  Le contrôle peut appeler `UpdateStates` chaque fois qu’il doit modifier son état, quel que soit l’état modifié.

[!code-csharp[VSMCustomControl#UpdateStates](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#updatestates)]
[!code-vb[VSMCustomControl#UpdateStates](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#updatestates)]

Si vous transmettez un nom d’État à <xref:System.Windows.VisualStateManager.GoToState%2A> lorsque le contrôle est déjà dans cet État, <xref:System.Windows.VisualStateManager.GoToState%2A> ne fait rien, vous n’avez donc pas besoin de vérifier l’état actuel du contrôle.  Par exemple, si `Value` passe d’un nombre négatif à un autre nombre négatif, le Storyboard de l’état de `Negative` n’est pas interrompu et l’utilisateur ne voit pas de modification dans le contrôle.

L' <xref:System.Windows.VisualStateManager> utilise des objets <xref:System.Windows.VisualStateGroup> pour déterminer l’État à quitter lorsque vous appelez <xref:System.Windows.VisualStateManager.GoToState%2A>. Le contrôle est toujours dans un État pour chaque <xref:System.Windows.VisualStateGroup> défini dans son <xref:System.Windows.Controls.ControlTemplate> et ne quitte un État que lorsqu’il passe à un autre État du même <xref:System.Windows.VisualStateGroup>. Par exemple, le <xref:System.Windows.Controls.ControlTemplate> du contrôle `NumericUpDown` définit le `Positive` et `Negative`objets <xref:System.Windows.VisualState> dans une <xref:System.Windows.VisualStateGroup> et les objets `Focused` et `Unfocused`<xref:System.Windows.VisualState> dans un autre. (Vous pouvez voir les `Focused` et les `Unfocused`<xref:System.Windows.VisualState> définis dans la section [exemple complet](#complete_example) de cette rubrique lorsque le contrôle passe de l’État `Positive` à l’État `Negative`, ou vice versa, le contrôle reste dans l’État `Focused` ou `Unfocused`.

Il existe trois emplacements classiques où l’état d’un contrôle peut changer :

- Lorsque le <xref:System.Windows.Controls.ControlTemplate> est appliqué au <xref:System.Windows.Controls.Control>.

- Quand une propriété est modifiée.

- Lorsqu’un événement se produit.

Les exemples suivants illustrent la mise à jour de l’état du contrôle `NumericUpDown` dans ces cas.

Vous devez mettre à jour l’état du contrôle dans la méthode <xref:System.Windows.FrameworkElement.OnApplyTemplate%2A> pour que le contrôle s’affiche dans l’état correct lorsque le <xref:System.Windows.Controls.ControlTemplate> est appliqué. L’exemple suivant appelle `UpdateStates` dans <xref:System.Windows.FrameworkElement.OnApplyTemplate%2A> pour garantir que le contrôle est dans les États appropriés.  Supposons, par exemple, que vous créez un contrôle `NumericUpDown` et que vous affectez à son <xref:System.Windows.Controls.Control.Foreground%2A> la valeur vert et à la `Value` la valeur-5.  Si vous n’appelez pas `UpdateStates` lorsque le <xref:System.Windows.Controls.ControlTemplate> est appliqué au contrôle `NumericUpDown`, le contrôle n’est pas dans l’État `Negative` et la valeur est verte au lieu de rouge.  Vous devez appeler `UpdateStates` pour placer le contrôle dans l’État `Negative`.

[!code-csharp[VSMCustomControl#ApplyTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#applytemplate)]
[!code-vb[VSMCustomControl#ApplyTemplate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#applytemplate)]

Vous devez souvent mettre à jour les États d’un contrôle lorsqu’une propriété change. L’exemple suivant montre l’intégralité de la méthode `ValueChangedCallback`. Étant donné que `ValueChangedCallback` est appelé lorsque `Value` change, la méthode appelle `UpdateStates` au cas où `Value` passerait de positif à négatif, ou vice versa. Il est acceptable d’appeler `UpdateStates` lorsque `Value` change mais reste positif ou négatif, car dans ce cas, le contrôle ne change pas d’État.

[!code-csharp[VSMCustomControl#EntireValueChangedCallback](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#entirevaluechangedcallback)]
[!code-vb[VSMCustomControl#EntireValueChangedCallback](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#entirevaluechangedcallback)]

Vous devrez peut-être également mettre à jour les États lorsqu’un événement se produit. L’exemple suivant montre que le `NumericUpDown` appelle `UpdateStates` sur le <xref:System.Windows.Controls.Control> pour gérer l’événement <xref:System.Windows.UIElement.GotFocus>.

[!code-csharp[VSMCustomControl#OnGotFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#ongotfocus)]
[!code-vb[VSMCustomControl#OnGotFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#ongotfocus)]

Le <xref:System.Windows.VisualStateManager> vous aide à gérer les États de votre contrôle. En utilisant l' <xref:System.Windows.VisualStateManager>, vous vous assurez que votre contrôle passe correctement d’un État à l’autre.  Si vous suivez les recommandations décrites dans cette section pour utiliser le <xref:System.Windows.VisualStateManager>, le code de votre contrôle reste lisible et gérable.

<a name="providing_the_control_contract"></a>

## <a name="providing-the-control-contract"></a>Fourniture du contrat de contrôle

Vous fournissez un contrat de contrôle afin que <xref:System.Windows.Controls.ControlTemplate> auteurs sachent ce qu’il faut placer dans le modèle. Un contrat de contrôle comporte trois éléments :

- les éléments visuels utilisés par la logique du contrôle ;

- les états du contrôle et le groupe auquel appartient chaque état ;

- les propriétés publiques qui affectent visuellement le contrôle.

Une personne qui crée un <xref:System.Windows.Controls.ControlTemplate> doit savoir ce que <xref:System.Windows.FrameworkElement> objets utilisés par la logique du contrôle, le type de chaque objet et son nom. Un auteur de <xref:System.Windows.Controls.ControlTemplate> doit également connaître le nom de chaque état possible du contrôle, ainsi que l' <xref:System.Windows.VisualStateGroup> l’État.

Si vous revenez à l’exemple de `NumericUpDown`, le contrôle s’attend à ce que les <xref:System.Windows.Controls.ControlTemplate> aient les objets <xref:System.Windows.FrameworkElement> suivants :

- Une <xref:System.Windows.Controls.Primitives.RepeatButton> appelée `UpButton`.

- Une <xref:System.Windows.Controls.Primitives.RepeatButton> appelée `DownButton.`

 Le contrôle peut avoir les États suivants :

- Dans le `ValueStates`<xref:System.Windows.VisualStateGroup>

  - `Positive`

  - `Negative`

- Dans le `FocusStates`<xref:System.Windows.VisualStateGroup>

  - `Focused`

  - `Unfocused`

Pour spécifier les objets <xref:System.Windows.FrameworkElement> que le contrôle attend, vous utilisez le <xref:System.Windows.TemplatePartAttribute>, qui spécifie le nom et le type des éléments attendus.  Pour spécifier les États possibles d’un contrôle, vous utilisez l' <xref:System.Windows.TemplateVisualStateAttribute>, qui spécifie le nom de l’État et à quel <xref:System.Windows.VisualStateGroup> il appartient.  Placez le <xref:System.Windows.TemplatePartAttribute> et <xref:System.Windows.TemplateVisualStateAttribute> sur la définition de classe du contrôle.

Toute propriété publique qui affecte l’apparence de votre contrôle fait également partie du contrat de contrôle.

L’exemple suivant spécifie l’objet <xref:System.Windows.FrameworkElement> et les États du contrôle `NumericUpDown`.

[!code-csharp[VSMCustomControl#ControlContract](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#controlcontract)]
[!code-vb[VSMCustomControl#ControlContract](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#controlcontract)]

<a name="complete_example"></a>

## <a name="complete-example"></a>Exemple complet

L’exemple suivant est le <xref:System.Windows.Controls.ControlTemplate> entier pour le contrôle `NumericUpDown`.

[!code-xaml[VSMCustomControl#NUDTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/themes/generic.xaml#nudtemplate)]

L’exemple suivant illustre la logique de la `NumericUpDown`.

[!code-csharp[VSMCustomControl#ControlLogic](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#controllogic)]
[!code-vb[VSMCustomControl#ControlLogic](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#controllogic)]

## <a name="see-also"></a>Voir aussi

- [Créer un modèle pour un contrôle](../../../desktop-wpf/themes/how-to-create-apply-template.md)
- [Personnalisation des contrôles](control-customization.md)
