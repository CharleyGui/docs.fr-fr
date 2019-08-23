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
ms.openlocfilehash: 63a0b724b71c4a4901c2dedcf502045a75ec405c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933732"
---
# <a name="customizing-the-appearance-of-an-existing-control-by-creating-a-controltemplate"></a>Personnalisation de l'apparence d'un contrôle existant en créant un ControlTemplate
<a name="introduction"></a>Un <xref:System.Windows.Controls.ControlTemplate> spécifie la structure visuelle et le comportement visuel d’un contrôle. Vous pouvez personnaliser l’apparence d’un contrôle en lui donnant un nouveau <xref:System.Windows.Controls.ControlTemplate>. Lorsque vous créez un <xref:System.Windows.Controls.ControlTemplate>, vous remplacez l’apparence d’un contrôle existant sans modifier sa fonctionnalité. Par exemple, vous pouvez faire en sorte que les boutons de votre application s’arrondissent au lieu de la forme carrée par défaut <xref:System.Windows.Controls.Primitives.ButtonBase.Click> , mais le bouton déclenchera toujours l’événement.  
  
 Cette rubrique explique les différentes parties d’un <xref:System.Windows.Controls.ControlTemplate>, illustre la création d' <xref:System.Windows.Controls.ControlTemplate> un simple <xref:System.Windows.Controls.Button>pour un et explique comment comprendre le contrat de contrôle d’un contrôle pour vous permettre de personnaliser son apparence. Étant donné que vous <xref:System.Windows.Controls.ControlTemplate> créez [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]un dans, vous pouvez modifier l’apparence d’un contrôle sans écrire de code. Vous pouvez également utiliser un concepteur, tel que Microsoft Expression Blend, pour créer des modèles de contrôle personnalisé. Cette rubrique présente des exemples de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] qui personnalisent l’apparence d' <xref:System.Windows.Controls.Button> un et répertorie l’exemple complet à la fin de la rubrique. Pour plus d’informations sur l’utilisation d’Expression Blend, consultez [Définition d’un style pour un contrôle prenant en charge les modèles](https://go.microsoft.com/fwlink/?LinkId=161153).  
  
 Les illustrations suivantes montrent un <xref:System.Windows.Controls.Button> qui utilise le <xref:System.Windows.Controls.ControlTemplate> créé dans cette rubrique.  
  
 ![Bouton avec un modèle de contrôle personnalisé.](./media/ndp-buttonnormal.png "NDP_ButtonNormal")  
Bouton qui utilise un modèle de contrôle personnalisé  
  
 ![Bouton avec une bordure rouge.](./media/ndp-buttonmouseover.png "NDP_ButtonMouseOver")  
Bouton qui utilise un modèle de contrôle personnalisé et sur lequel le pointeur de la souris se trouve  

<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Prérequis  
 Cette rubrique part du principe que vous savez comment créer et utiliser des contrôles et des styles, comme indiqué dans [Contrôles](index.md). Les concepts abordés dans cette rubrique s’appliquent aux éléments qui <xref:System.Windows.Controls.Control> héritent de la classe <xref:System.Windows.Controls.UserControl>, à l’exception de. Vous ne pouvez pas <xref:System.Windows.Controls.ControlTemplate> appliquer un <xref:System.Windows.Controls.UserControl>à un.  
  
<a name="when_you_should_create_a_controltemplate"></a>   
## <a name="when-you-should-create-a-controltemplate"></a>Quand créer un ControlTemplate  
 Les contrôles ont de nombreuses propriétés, <xref:System.Windows.Controls.Border.Background%2A>telles <xref:System.Windows.Controls.Control.Foreground%2A>que, <xref:System.Windows.Controls.Control.FontFamily%2A>et, que vous pouvez définir pour spécifier différents aspects de l’apparence du contrôle, mais les modifications que vous pouvez apporter en définissant ces propriétés sont limitées. Par exemple, vous pouvez affecter la <xref:System.Windows.Controls.Control.Foreground%2A> valeur Blue à la <xref:System.Windows.Controls.Control.FontStyle%2A> propriété et la valeur <xref:System.Windows.Controls.CheckBox>italique à un.  
  
 Si vous n’avez pas la possibilité <xref:System.Windows.Controls.ControlTemplate> de créer un pour les contrôles, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]tous les contrôles de chaque application basée sur l’application auront la même apparence générale, ce qui limiterait la possibilité de créer une application avec une apparence personnalisée. Par défaut, chaque <xref:System.Windows.Controls.CheckBox> a des caractéristiques similaires. Par exemple, le contenu du <xref:System.Windows.Controls.CheckBox> est toujours à droite de l’indicateur de sélection, et la coche est toujours utilisée pour indiquer que le <xref:System.Windows.Controls.CheckBox> est sélectionné.  
  
 Vous créez un <xref:System.Windows.Controls.ControlTemplate> lorsque vous souhaitez personnaliser l’apparence du contrôle au-delà de ce qui est défini par les autres propriétés du contrôle. Dans l’exemple de <xref:System.Windows.Controls.CheckBox>, supposons que vous souhaitiez que le contenu de la case à cocher se trouve au-dessus de l’indicateur de sélection et que vous souhaitiez qu’un X indique que l <xref:System.Windows.Controls.CheckBox> 'est sélectionné. Vous spécifiez ces modifications dans <xref:System.Windows.Controls.ControlTemplate> le <xref:System.Windows.Controls.CheckBox>de.  
  
 L’illustration suivante montre un <xref:System.Windows.Controls.CheckBox> qui utilise une valeur <xref:System.Windows.Controls.ControlTemplate>par défaut.  
  
 ![Case à cocher avec le modèle de contrôle par défaut.](./media/ndp-checkboxdefault.png "NDP_CheckBoxDefault")  
Case à cocher qui utilise le modèle de contrôle par défaut  
  
 L’illustration suivante montre un <xref:System.Windows.Controls.CheckBox> qui utilise un personnalisé <xref:System.Windows.Controls.ControlTemplate> pour <xref:System.Windows.Controls.CheckBox> placer le contenu du au-dessus de l’indicateur de sélection et affiche un <xref:System.Windows.Controls.CheckBox> X lorsque le est sélectionné.  
  
 ![Case à cocher avec un modèle de contrôle personnalisé.](./media/ndp-checkboxcustom.png "NDP_CheckBoxCustom")  
Case à cocher qui utilise un modèle de contrôle personnalisé  
  
 Pour le <xref:System.Windows.Controls.CheckBox> de cet exemple est relativement complexe, cette rubrique utilise un exemple plus simple de création d’un <xref:System.Windows.Controls.ControlTemplate> pour un <xref:System.Windows.Controls.Button>. <xref:System.Windows.Controls.ControlTemplate>  
  
<a name="changing_the_visual_structure_of_a_control"></a>   
## <a name="changing-the-visual-structure-of-a-control"></a>Changement de la structure visuelle d’un contrôle  
 Dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], un contrôle est souvent un objet <xref:System.Windows.FrameworkElement> composite. Lorsque vous créez un <xref:System.Windows.Controls.ControlTemplate>, vous combinez <xref:System.Windows.FrameworkElement> des objets pour générer un contrôle unique. Un <xref:System.Windows.Controls.ControlTemplate> doit avoir un <xref:System.Windows.FrameworkElement> seul en tant qu’élément racine. L’élément racine contient généralement d' <xref:System.Windows.FrameworkElement> autres objets. La combinaison d’objets constitue la structure visuelle du contrôle.  
  
 L’exemple suivant crée un personnalisé <xref:System.Windows.Controls.ControlTemplate> pour le <xref:System.Windows.Controls.Button>. Le <xref:System.Windows.Controls.ControlTemplate> crée la structure visuelle <xref:System.Windows.Controls.Button>de. Cet exemple ne change pas l’apparence du bouton si vous placez le pointeur de la souris dessus ou cliquez dessus. La modification de l’apparence du bouton quand celui-ci est dans un autre état est décrite plus loin dans cette rubrique.  
  
 Dans cet exemple, la structure visuelle se compose des parties suivantes :  
  
- Nommé qui sert de racine <xref:System.Windows.FrameworkElement>du modèle. `RootElement` <xref:System.Windows.Controls.Border>  
  
- Qui est un enfant de `RootElement`. <xref:System.Windows.Controls.Grid>  
  
- <xref:System.Windows.Controls.ContentPresenter> Qui affiche le contenu du bouton. <xref:System.Windows.Controls.ContentPresenter> Permet d’afficher tout type d’objet.  
  
 [!code-xaml[VSMButtonTemplate#BasicTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#basictemplate)]  
  
### <a name="preserving-the-functionality-of-a-controls-properties-by-using-templatebinding"></a>Conservation de la fonctionnalité des propriétés d’un contrôle en utilisant TemplateBinding  
 Quand vous créez un nouveau <xref:System.Windows.Controls.ControlTemplate>, vous pouvez toujours utiliser les propriétés publiques pour modifier l’apparence du contrôle. L’extension de balisage [TemplateBinding](../advanced/templatebinding-markup-extension.md) lie une propriété d’un élément qui se trouve <xref:System.Windows.Controls.ControlTemplate> dans à une propriété publique définie par le contrôle. Quand vous utilisez [TemplateBinding](../advanced/templatebinding-markup-extension.md), vous permettez aux propriétés sur le contrôle d’agir comme paramètres du modèle. Autrement dit, quand une propriété sur un contrôle est définie, cette valeur est passée à l’élément qui a le [TemplateBinding](../advanced/templatebinding-markup-extension.md).  
  
 L’exemple suivant répète la partie de l’exemple précédent qui utilise l’extension de balisage [TemplateBinding](../advanced/templatebinding-markup-extension.md) pour lier les propriétés des éléments qui se <xref:System.Windows.Controls.ControlTemplate> trouvent dans le à des propriétés publiques définies par le bouton.  
  
 [!code-xaml[VSMButtonTemplate#TemplateBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#templatebinding)]  
  
 Dans cet exemple, <xref:System.Windows.Controls.Grid> a son <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType> modèle de propriété lié à <xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType>. Étant <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType> donné que est lié par modèle, vous pouvez créer plusieurs boutons qui <xref:System.Windows.Controls.ControlTemplate> utilisent le même <xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType> et affecter aux valeurs différentes sur chaque bouton. Si <xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType> n’a pas de modèle lié à une propriété d’un élément <xref:System.Windows.Controls.ControlTemplate>dans le, <xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType> la définition du d’un bouton n’a aucun impact sur l’apparence du bouton.  
  
 Notez que les noms des deux propriétés n’ont pas besoin d’être identiques. Dans l’exemple précédent, la <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A?displayProperty=nameWithType> propriété <xref:System.Windows.Controls.Button> de est liée <xref:System.Windows.Controls.ContentPresenter>par modèle à la <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A?displayProperty=nameWithType> propriété de. Le contenu du bouton est ainsi positionné horizontalement. <xref:System.Windows.Controls.ContentPresenter>n’a pas de propriété nommée `HorizontalContentAlignment`, mais <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A?displayProperty=nameWithType> peut être liée à <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A?displayProperty=nameWithType>. Quand vous liez par modèle une propriété, vérifiez que les propriétés source et cible sont du même type.  
  
 La <xref:System.Windows.Controls.Control> classe définit plusieurs propriétés qui doivent être utilisées par le modèle de contrôle pour avoir un effet sur le contrôle lorsqu’elles sont définies. Le mode d’utilisation de la propriété dépend de la propriété. <xref:System.Windows.Controls.ControlTemplate> Le <xref:System.Windows.Controls.ControlTemplate> doit utiliser la propriété de l’une des manières suivantes:  
  
- Un élément dans le <xref:System.Windows.Controls.ControlTemplate> modèle est lié à la propriété.  
  
- Un élément dans le <xref:System.Windows.Controls.ControlTemplate> hérite de la propriété d’un <xref:System.Windows.FrameworkElement>parent.  
  
 Le tableau suivant répertorie les propriétés visuelles héritées par un <xref:System.Windows.Controls.Control> contrôle de la classe. Il indique également si le modèle de contrôle par défaut d’un contrôle utilise la valeur de la propriété héritée ou s’il doit être lié par modèle.  
  
|Propriété|Méthode d’utilisation|  
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
  
 Le tableau répertorie uniquement les propriétés visuelles héritées de la <xref:System.Windows.Controls.Control> classe. Outre les propriétés listées dans le tableau, un contrôle peut également hériter <xref:System.Windows.FrameworkElement.DataContext%2A>des propriétés, <xref:System.Windows.FrameworkElement.Language%2A>et <xref:System.Windows.Controls.TextBlock.TextDecorations%2A> de l’élément Framework parent.  
  
 En outre, si <xref:System.Windows.Controls.ContentPresenter> le se trouve <xref:System.Windows.Controls.ControlTemplate> dans le <xref:System.Windows.Controls.ContentControl>d’un <xref:System.Windows.Controls.ContentPresenter> , le se liera <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> automatiquement <xref:System.Windows.Controls.ContentControl.Content%2A> aux propriétés et. De même, <xref:System.Windows.Controls.ItemsPresenter> un qui se trouve <xref:System.Windows.Controls.ControlTemplate> dans le <xref:System.Windows.Controls.ItemsControl> d’un crée automatiquement une <xref:System.Windows.Controls.ItemsControl.Items%2A> liaison <xref:System.Windows.Controls.ItemsPresenter> avec les propriétés et.  
  
 L’exemple suivant crée deux boutons qui utilisent le <xref:System.Windows.Controls.ControlTemplate> défini dans l’exemple précédent. L’exemple définit les <xref:System.Windows.Controls.Control.Background%2A>propriétés <xref:System.Windows.Controls.Control.Foreground%2A>, et <xref:System.Windows.Controls.Control.FontSize%2A> sur chaque bouton. La définition <xref:System.Windows.Controls.Control.Background%2A> de la propriété a un effet, car il s’agit <xref:System.Windows.Controls.ControlTemplate>d’un modèle lié dans le. Même si les <xref:System.Windows.Controls.Control.Foreground%2A> propriétés <xref:System.Windows.Controls.Control.FontSize%2A> et ne sont pas liées par modèle, leur définition a un effet, car leurs valeurs sont héritées.  
  
 [!code-xaml[VSMButtonTemplate#ButtonDeclaration](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#buttondeclaration)]  
  
 L’exemple précédent produit une sortie similaire à celle de l’illustration suivante.  
  
 ![Deux boutons, un bleu et un violet.](./media/ndp-buttontwo.png "NDP_ButtonTwo")  
Deux boutons avec des couleurs d’arrière-plan différentes  
  
<a name="changing_the_appearance_of_a_control_depending_on_its_state"></a>   
## <a name="changing-the-appearance-of-a-control-depending-on-its-state"></a>Modification de l’apparence d’un contrôle en fonction de son état  
 La différence entre un bouton avec son apparence par défaut et le bouton de l’exemple précédent est que le bouton par défaut change légèrement selon son état. Par exemple, l’apparence du bouton par défaut change quand l’utilisateur clique dessus ou pointe sur lui. Bien que <xref:System.Windows.Controls.ControlTemplate> ne modifie pas la fonctionnalité d’un contrôle, il modifie le comportement visuel du contrôle. Un comportement visuel décrit l’apparence du contrôle quand ce dernier est dans un état particulier. Pour comprendre la différence entre la fonctionnalité et le comportement visuel d’un contrôle, considérez l’exemple du bouton. La fonctionnalité du bouton consiste à déclencher l' <xref:System.Windows.Controls.Primitives.ButtonBase.Click> événement lorsque l’utilisateur clique dessus, mais le comportement visuel du bouton a pour effet de modifier son apparence lorsqu’il est pointé ou enfoncé.  
  
 Vous utilisez <xref:System.Windows.VisualState> des objets pour spécifier l’apparence d’un contrôle lorsqu’il est dans un certain état. Un <xref:System.Windows.VisualState> contient un <xref:System.Windows.Media.Animation.Storyboard> qui modifie l’apparence des éléments qui se trouvent dans le <xref:System.Windows.Controls.ControlTemplate>. Vous n’avez pas à écrire de code pour que cela se produise, car la logique du contrôle modifie l' <xref:System.Windows.VisualStateManager>État à l’aide du. Lorsque le contrôle passe à l’état spécifié par la <xref:System.Windows.VisualState.Name%2A?displayProperty=nameWithType> propriété, le <xref:System.Windows.Media.Animation.Storyboard> commence. Lorsque le contrôle quitte l’État, le <xref:System.Windows.Media.Animation.Storyboard> s’arrête.  
  
 L’exemple suivant montre le <xref:System.Windows.VisualState> qui modifie l’apparence d’un <xref:System.Windows.Controls.Button> lorsque le pointeur de la souris se trouve sur celui-ci. Modifie la couleur `BorderBrush`de bordure du bouton en modifiant la couleur du. <xref:System.Windows.Media.Animation.Storyboard> Si vous faites référence à <xref:System.Windows.Controls.ControlTemplate> l’exemple au début de cette rubrique, vous vous rappelez `BorderBrush` que <xref:System.Windows.Media.SolidColorBrush> est le nom du assigné au <xref:System.Windows.Controls.Border.Background%2A> du <xref:System.Windows.Controls.Border>.  
  
 [!code-xaml[VSMButtonTemplate#4](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#4)]  
  
 Le contrôle est chargé de définir les états dans le cadre de son contrat de contrôle, lequel est décrit en détail dans [Personnalisation des autres contrôles grâce à une bonne compréhension du contrat de contrôle](#customizing_other_controls_by_understanding_the_control_contract), plus loin dans cette rubrique. Le tableau suivant répertorie les États spécifiés pour le <xref:System.Windows.Controls.Button>.  
  
|Nom VisualState|Nom VisualStateGroup|Description|  
|----------------------|---------------------------|-----------------|  
|Normale|CommonStates|État par défaut.|  
|MouseOver|CommonStates|Le pointeur de la souris est positionné sur le contrôle.|  
|Appuyé|CommonStates|Le contrôle est enfoncé.|  
|Désactivé|CommonStates|Le contrôle est désactivé.|  
|Avec focus|FocusStates|Le contrôle a le focus.|  
|Sans focus|FocusStates|Le contrôle n’a pas le focus.|  
  
 Le <xref:System.Windows.Controls.Button> définit deux groupes d’États: `CommonStates` le groupe contient `Normal`les `MouseOver`États `Pressed`,, `Disabled` et. le groupe `FocusStates` contient les états `Focused` et `Unfocused`. Les états d’un même groupe d’état s’excluent mutuellement. Le contrôle est toujours dans un état par groupe. Par exemple, un <xref:System.Windows.Controls.Button> peut avoir le focus même lorsque le pointeur de la souris ne se trouve pas <xref:System.Windows.Controls.Button> sur lui `Focused` , donc un dans l' `MouseOver`État peut être `Normal` dans l’État, `Pressed`ou.  
  
 Vous ajoutez <xref:System.Windows.VisualState> des objets <xref:System.Windows.VisualStateGroup> aux objets. Vous ajoutez <xref:System.Windows.VisualStateGroup> des objets à <xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType> la propriété jointe. L’exemple suivant définit les <xref:System.Windows.VisualState> objets pour les `Normal`États `MouseOver`, et `Pressed` , qui sont tous dans le `CommonStates` groupe. Le <xref:System.Windows.VisualState.Name%2A> de chaque <xref:System.Windows.VisualState> correspond au nom dans le tableau précédent. L’état `Disabled` et les états du groupe `FocusStates` sont omis pour que l’exemple reste concis, mais ils figurent dans l’exemple complet fourni à la fin de cette rubrique.  
  
> [!NOTE]
> Veillez à définir la <xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType> propriété jointe à la <xref:System.Windows.FrameworkElement> racine de <xref:System.Windows.Controls.ControlTemplate>.  
  
 [!code-xaml[VSMButtonTemplate#VisualStates](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#visualstates)]  
  
 L’exemple précédent produit une sortie similaire à celle des illustrations suivantes.  
  
 ![Bouton avec un modèle de contrôle personnalisé.](./media/ndp-buttonnormal.png "NDP_ButtonNormal")  
Bouton qui utilise un modèle de contrôle personnalisé dans l’état normal  
  
 ![Bouton avec une bordure rouge.](./media/ndp-buttonmouseover.png "NDP_ButtonMouseOver")  
Bouton qui utilise un modèle de contrôle personnalisé dans l’état de pointage avec la souris  
  
 ![La bordure est transparente sur un bouton appuyé.](./media/ndp-buttonpressed.png "NDP_ButtonPressed")  
Bouton qui utilise un modèle de contrôle personnalisé dans l’état enfoncé  
  
 Pour trouver les états visuels pour les contrôles inclus avec [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], consultez [Styles et modèles Control](control-styles-and-templates.md).  
  
<a name="specifying_the_behavior_of_a_control_when_it_transitions_between_states"></a>   
## <a name="specifying-the-behavior-of-a-control-when-it-transitions-between-states"></a>Spécification du comportement d’un contrôle durant les transitions entre états  
 Dans l’exemple précédent, l’apparence du bouton change également quand l’utilisateur clique dessus, mais à moins que le bouton ne soit enfoncé pendant une seconde complète, aucun effet n’est visible pour l’utilisateur. Par défaut, une seconde est nécessaire au déclenchement de l’animation. Étant donné que les utilisateurs sont susceptibles de cliquer et de relâcher un bouton en moins de temps, les commentaires visuels ne sont <xref:System.Windows.Controls.ControlTemplate> pas effectifs si vous laissez le dans son état par défaut.  
  
 Vous pouvez spécifier la durée nécessaire à l’animation pour faire passer en douceur un contrôle d’un État à un autre en ajoutant <xref:System.Windows.VisualTransition> des objets <xref:System.Windows.Controls.ControlTemplate>à. Lorsque vous créez un <xref:System.Windows.VisualTransition>, vous spécifiez un ou plusieurs des éléments suivants:  
  
- Temps nécessaire à une transition entre des états  
  
- Changements supplémentaires dans l’apparence du contrôle durant la transition  
  
- L’État auquel <xref:System.Windows.VisualTransition> le est appliqué.  
  
### <a name="specifying-the-duration-of-a-transition"></a>Spécification de la durée d’une transition  
 Vous pouvez spécifier la durée d’une transition en définissant <xref:System.Windows.VisualTransition.GeneratedDuration%2A> la propriété. L’exemple précédent a un <xref:System.Windows.VisualState> qui spécifie que la bordure du bouton devient transparente lorsque le bouton est enfoncé, mais que l’animation prend trop de temps pour être visible si le bouton est rapidement enfoncé et relâché. Vous pouvez utiliser un <xref:System.Windows.VisualTransition> pour spécifier la durée nécessaire pour que le contrôle passe à l’état enfoncé. L’exemple suivant spécifie que le contrôle passe à l’état Pressed après un centième de seconde.  
  
 [!code-xaml[VSMButtonTemplate#PressedTransition](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#pressedtransition)]  
  
### <a name="specifying-changes-to-the-controls-appearance-during-a-transition"></a>Spécification de changements de l’apparence du contrôle durant une transition  
 Le <xref:System.Windows.VisualTransition> contient un <xref:System.Windows.Media.Animation.Storyboard> qui commence lorsque le contrôle passe d’un État à un autre. Par exemple, vous pouvez spécifier qu’une animation particulière a lieu quand le contrôle passe de l’état `MouseOver` à l’état `Normal`. L’exemple suivant crée un <xref:System.Windows.VisualTransition> qui spécifie que lorsque l’utilisateur éloigne le pointeur de la souris du bouton, la bordure du bouton passe au bleu, puis au jaune, puis au noir en 1,5 secondes.  
  
 [!code-xaml[VSMButtonTemplate#8](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#8)]  
  
### <a name="specifying-when-a-visualtransition-is-applied"></a>Spécification du moment où VisualTransition est appliqué  
 Un <xref:System.Windows.VisualTransition> peut être limité pour ne s’appliquer qu’à certains États, ou il peut être appliqué chaque fois que le contrôle passe d’un État à un autre. Dans <xref:System.Windows.VisualTransition> l’exemple précédent, est appliqué lorsque le contrôle passe de l' `MouseOver` État à l' `Normal` État. dans l’exemple précédent, le <xref:System.Windows.VisualTransition> est appliqué lorsque le contrôle passe à l' `Pressed` État. Vous limitez le <xref:System.Windows.VisualTransition> moment où un est appliqué <xref:System.Windows.VisualTransition.To%2A> en <xref:System.Windows.VisualTransition.From%2A> définissant les propriétés et. Le tableau suivant décrit les niveaux de restriction, du plus restrictif au moins restrictif.  
  
|Type de restriction|Valeur de From|Valeur de To|  
|-------------------------|-------------------|-----------------|  
|D’un état spécifié à un autre état spécifié|Nom d’un<xref:System.Windows.VisualState>|Nom d’un<xref:System.Windows.VisualState>|  
|De n’importe quel état à un état spécifié|Non défini|Nom d’un<xref:System.Windows.VisualState>|  
|D’un état spécifié à n’importe quel état|Nom d’un<xref:System.Windows.VisualState>|Non défini|  
|De n’importe quel état à n’importe quel autre état|Non défini|Non défini|  
  
 Vous pouvez avoir plusieurs <xref:System.Windows.VisualTransition> objets dans un <xref:System.Windows.VisualStateGroup> qui font référence au même État, mais ils seront utilisés dans l’ordre que le tableau précédent spécifie. Dans l’exemple suivant, il y a <xref:System.Windows.VisualTransition> deux objets. Lorsque le contrôle passe de l' `Pressed` État à l’État, le <xref:System.Windows.VisualTransition> qui a à la <xref:System.Windows.VisualTransition.From%2A> `MouseOver` fois <xref:System.Windows.VisualTransition.To%2A> la valeur et l’État est utilisé. Quand le contrôle passe d’un état autre que `Pressed` à l’état `MouseOver`, l’autre état est utilisé.  
  
 [!code-xaml[VSMButtonTemplate#7](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#7)]  
  
 <xref:System.Windows.VisualStateGroup> <xref:System.Windows.VisualState> A une <xref:System.Windows.VisualStateGroup.Transitions%2A> propriété qui contient les <xref:System.Windows.VisualTransition> objets qui s’appliquent aux objets dans le. <xref:System.Windows.VisualStateGroup> En tant qu' <xref:System.Windows.VisualTransition> auteur,vousêteslibred'<xref:System.Windows.Controls.ControlTemplate> inclure votre choix. Toutefois, si les <xref:System.Windows.VisualTransition.To%2A> propriétés <xref:System.Windows.VisualTransition.From%2A> et ont pour valeur des noms d’état <xref:System.Windows.VisualStateGroup>qui ne se trouvent <xref:System.Windows.VisualTransition> pas dans, est ignoré.  
  
 L’exemple suivant montre le <xref:System.Windows.VisualStateGroup> pour le `CommonStates`. L’exemple définit une <xref:System.Windows.VisualTransition> pour chacune des transitions suivantes du bouton.  
  
- À l’état `Pressed`  
  
- À l’état `MouseOver`  
  
- De l’état `Pressed` à l’état `MouseOver`  
  
- De l’état `MouseOver` à l’état `Normal`  
  
 [!code-xaml[VSMButtonTemplate#VisualTransitions](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#visualtransitions)]  
  
<a name="customizing_other_controls_by_understanding_the_control_contract"></a>   
## <a name="customizing-other-controls-by-understanding-the-control-contract"></a>Personnalisation des autres contrôles grâce à une bonne compréhension du contrat de contrôle  
 Un contrôle qui utilise un <xref:System.Windows.Controls.ControlTemplate> pour spécifier sa structure visuelle (à l' <xref:System.Windows.FrameworkElement> aide d’objets) et le comportement visuel <xref:System.Windows.VisualState> (à l’aide d’objets) utilise le modèle de contrôle des parties. Bon nombre des contrôles inclus avec [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 4 utilisent ce modèle. Les parties qu’un <xref:System.Windows.Controls.ControlTemplate> auteur doit connaître sont communiquées par le biais du contrat de contrôle. Quand vous connaissez les composants d’un contrat de contrôle, vous pouvez personnaliser l’apparence de tout contrôle qui utilise le modèle de contrôle des composants.  
  
 Un contrat de contrôle comporte trois éléments :  
  
- les éléments visuels utilisés par la logique du contrôle ;  
  
- les états du contrôle et le groupe auquel appartient chaque état ;  
  
- les propriétés publiques qui affectent visuellement le contrôle.  
  
### <a name="visual-elements-in-the-control-contract"></a>Éléments visuels du contrat de contrôle  
 Parfois, la logique d’un contrôle interagit <xref:System.Windows.FrameworkElement> avec un qui se <xref:System.Windows.Controls.ControlTemplate>trouve dans le. Par exemple, le contrôle peut gérer un événement de l’un de ses éléments. Lorsqu’un contrôle s’attend à trouver un particulier <xref:System.Windows.FrameworkElement> dans le <xref:System.Windows.Controls.ControlTemplate>, il doit transmettre ces informations à l' <xref:System.Windows.Controls.ControlTemplate> auteur. Le contrôle utilise le <xref:System.Windows.TemplatePartAttribute> pour transmettre le type d’élément attendu, et le nom de l’élément. Le <xref:System.Windows.Controls.Button> n’a <xref:System.Windows.FrameworkElement> pas de parties dans son contrat de contrôle, contrairement à d’autres <xref:System.Windows.Controls.ComboBox>contrôles, tels que,.  
  
 L’exemple suivant montre les <xref:System.Windows.TemplatePartAttribute> objets spécifiés sur la <xref:System.Windows.Controls.ComboBox> classe. La logique de <xref:System.Windows.Controls.ComboBox> s’attend à trouver un <xref:System.Windows.Controls.TextBox> nommé `PART_EditableTextBox` et un <xref:System.Windows.Controls.Primitives.Popup> nommé `PART_Popup` dans son <xref:System.Windows.Controls.ControlTemplate>.  
  
 [!code-csharp[VSMButtonTemplate#ComboBoxContract](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/controlcontracts.cs#comboboxcontract)]
 [!code-vb[VSMButtonTemplate#ComboBoxContract](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmbuttontemplate/visualbasic/window1.xaml.vb#comboboxcontract)]  
  
 L’exemple suivant montre un simplifié <xref:System.Windows.Controls.ControlTemplate> pour le <xref:System.Windows.Controls.ComboBox> qui comprend les éléments spécifiés par les <xref:System.Windows.TemplatePartAttribute> objets sur la <xref:System.Windows.Controls.ComboBox> classe.  
  
 [!code-xaml[VSMButtonTemplate#ComboBoxTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/window1.xaml#comboboxtemplate)]  
  
### <a name="states-in-the-control-contract"></a>États du contrat de contrôle  
 Les états d’un contrôle font également partie du contrat de contrôle. L’exemple de création d' <xref:System.Windows.Controls.ControlTemplate> un pour <xref:System.Windows.Controls.Button> un montre comment spécifier l’apparence d’un <xref:System.Windows.Controls.Button> en fonction de ses États. Vous créez un <xref:System.Windows.VisualState> pour chaque état spécifié et placez tous <xref:System.Windows.VisualState> les objets qui partagent <xref:System.Windows.TemplateVisualStateAttribute.GroupName%2A> un dans <xref:System.Windows.VisualStateGroup>un, comme décrit dans [modification de l’apparence d’un contrôle en fonction de son état](#changing_the_appearance_of_a_control_depending_on_its_state) précédemment dans cette rubrique. Les <xref:System.Windows.TemplateVisualStateAttribute>contrôles tiers doivent spécifier des États à l’aide de, qui permet aux outils du concepteur, tels qu’Expression Blend, d’exposer les États du contrôle pour la création de modèles de contrôle.  
  
 Pour trouver le contrat de contrôle pour les contrôles inclus avec [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], consultez [Styles et modèles Control](control-styles-and-templates.md).  
  
### <a name="properties-in-the-control-contract"></a>Propriétés du contrat de contrôle  
 Les propriétés publiques qui affectent visuellement le contrôle sont également incluses dans le contrat de contrôle. Vous pouvez définir ces propriétés pour modifier l’apparence du contrôle sans créer de nouveau <xref:System.Windows.Controls.ControlTemplate>. Vous pouvez également utiliser l’extension de balisage [TemplateBinding](../advanced/templatebinding-markup-extension.md) pour lier les propriétés des éléments qui <xref:System.Windows.Controls.ControlTemplate> se trouvent dans le à des propriétés publiques <xref:System.Windows.Controls.Button>définies par le.  
  
 L’exemple suivant illustre le contrat de contrôle pour le bouton.  
  
 [!code-csharp[VSMButtonTemplate#ButtonContract](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/controlcontracts.cs#buttoncontract)]
 [!code-vb[VSMButtonTemplate#ButtonContract](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmbuttontemplate/visualbasic/window1.xaml.vb#buttoncontract)]  
  
 Lors de la <xref:System.Windows.Controls.ControlTemplate>création d’un, il est souvent plus facile de <xref:System.Windows.Controls.ControlTemplate> commencer avec un existant et d’y apporter des modifications. Pour modifier un existant <xref:System.Windows.Controls.ControlTemplate>, vous pouvez effectuer l’une des opérations suivantes:  
  
- Utiliser un concepteur, tel qu’Expression Blend, qui fournit une interface graphique utilisateur pour créer des modèles de contrôle. Pour plus d’informations, consultez [Définition d’un style pour un contrôle prenant en charge les modèles](https://go.microsoft.com/fwlink/?LinkId=161153).  
  
- Obtient la valeur <xref:System.Windows.Controls.ControlTemplate> par défaut et la modifie. Pour trouver les modèles de contrôle par défaut compris dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], consultez [Thèmes WPF par défaut](https://go.microsoft.com/fwlink/?LinkID=158252).  
  
<a name="complete_example"></a>   
## <a name="complete-example"></a>Exemple complet  
 L’exemple suivant illustre la totalité <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.ControlTemplate> de la décrite dans cette rubrique.  
  
 [!code-xaml[VSMButtonTemplate#3](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#3)]  
  
## <a name="see-also"></a>Voir aussi

- [Application d’un style et création de modèles](styling-and-templating.md)
