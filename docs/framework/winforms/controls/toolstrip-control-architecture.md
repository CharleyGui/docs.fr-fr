---
title: Architecture du contrôle ToolStrip
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStrip control [Windows Forms], architecture
ms.assetid: 71df2d18-862e-4701-9ff9-c1fe606f94f2
ms.openlocfilehash: d0a1441e9bae8d2c1f938e7399c11e736708da4d
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/20/2019
ms.locfileid: "68363825"
---
# <a name="toolstrip-control-architecture"></a>Architecture du contrôle ToolStrip

Les <xref:System.Windows.Forms.ToolStrip> classes <xref:System.Windows.Forms.ToolStripItem> et fournissent un système flexible et extensible pour l’affichage des barres d’outils, des États et des éléments de menu. Ces classes sont toutes contenues dans <xref:System.Windows.Forms> l’espace de noms et sont généralement nommées avec le préfixe «ToolStrip» <xref:System.Windows.Forms.ToolStripOverflow>(par exemple,) ou avec le suffixe « <xref:System.Windows.Forms.MenuStrip>Strip» (par exemple,).

## <a name="toolstrip"></a>ToolStrip

Les rubriques suivantes décrivent <xref:System.Windows.Forms.ToolStrip> et les contrôles qui dérivent de celui-ci.

<xref:System.Windows.Forms.ToolStrip>est la classe de base abstraite <xref:System.Windows.Forms.StatusStrip>pour <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.ContextMenuStrip>et. Le modèle objet suivant illustre la <xref:System.Windows.Forms.ToolStrip> hiérarchie d’héritage.

![Diagramme qui montre le modèle objet ToolStrip.](./media/toolstrip-control-architecture/toolstrip-object-model.gif)

Vous pouvez accéder à tous les éléments d' <xref:System.Windows.Forms.ToolStrip> un à <xref:System.Windows.Forms.ToolStrip.Items%2A> l’aide de la collection. Vous pouvez accéder à tous les éléments d' <xref:System.Windows.Forms.ToolStripDropDownItem> un à <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItems%2A> l’aide de la collection. Dans une classe dérivée <xref:System.Windows.Forms.ToolStrip>de, vous pouvez également utiliser <xref:System.Windows.Forms.ToolStrip.DisplayedItems%2A> la propriété pour accéder uniquement aux éléments qui sont actuellement affichés. Il s’agit des éléments qui ne sont pas actuellement dans un menu de dépassement de capacité.

Les éléments suivants sont spécialement conçus pour fonctionner de manière transparente avec <xref:System.Windows.Forms.ToolStripSystemRenderer> et <xref:System.Windows.Forms.ToolStripProfessionalRenderer> dans toutes les orientations. Ils sont disponibles par défaut au moment de la conception <xref:System.Windows.Forms.ToolStrip> pour le contrôle:

- <xref:System.Windows.Forms.ToolStripButton>

- <xref:System.Windows.Forms.ToolStripSeparator>

- <xref:System.Windows.Forms.ToolStripLabel>

- <xref:System.Windows.Forms.ToolStripDropDownButton>

- <xref:System.Windows.Forms.ToolStripSplitButton>

- <xref:System.Windows.Forms.ToolStripTextBox>

- <xref:System.Windows.Forms.ToolStripComboBox>

### <a name="menustrip"></a>MenuStrip

<xref:System.Windows.Forms.MenuStrip>est le conteneur de niveau supérieur qui remplace <xref:System.Windows.Forms.MainMenu>. Il fournit également la gestion des clés et les fonctionnalités d’interface multidocument (MDI). Fonctionnellement, <xref:System.Windows.Forms.ToolStripDropDownItem> et <xref:System.Windows.Forms.ToolStripMenuItem> fonctionnent avec <xref:System.Windows.Forms.MenuStrip>, bien qu’ils soient dérivés <xref:System.Windows.Forms.ToolStripItem>de.

Les éléments suivants sont spécialement conçus pour fonctionner de manière transparente avec <xref:System.Windows.Forms.ToolStripSystemRenderer> et <xref:System.Windows.Forms.ToolStripProfessionalRenderer> dans toutes les orientations. Ils sont disponibles par défaut au moment de la conception <xref:System.Windows.Forms.MenuStrip> pour le contrôle:

- <xref:System.Windows.Forms.ToolStripMenuItem>

- <xref:System.Windows.Forms.ToolStripTextBox>

- <xref:System.Windows.Forms.ToolStripComboBox>

### <a name="statusstrip"></a>StatusStrip

<xref:System.Windows.Forms.StatusStrip>remplace le <xref:System.Windows.Forms.StatusBar> contrôle. Les fonctionnalités spéciales <xref:System.Windows.Forms.StatusStrip> de incluent une disposition de table personnalisée, la prise en charge des poignées de dimensionnement et de `Spring` déplacement du formulaire, ainsi <xref:System.Windows.Forms.ToolStripStatusLabel> que la propriété qui permet à un de remplir automatiquement l’espace disponible.

Les éléments suivants sont spécialement conçus pour fonctionner de manière transparente avec <xref:System.Windows.Forms.ToolStripSystemRenderer> et <xref:System.Windows.Forms.ToolStripProfessionalRenderer> dans toutes les orientations. Ils sont disponibles par défaut au moment de la conception <xref:System.Windows.Forms.StatusStrip> pour le contrôle:

- <xref:System.Windows.Forms.ToolStripStatusLabel>

- <xref:System.Windows.Forms.ToolStripDropDownButton>

- <xref:System.Windows.Forms.ToolStripSplitButton>

- <xref:System.Windows.Forms.ToolStripProgressBar>

### <a name="contextmenustrip"></a>ContextMenuStrip

<xref:System.Windows.Forms.ContextMenuStrip> remplace <xref:System.Windows.Forms.ContextMenu>. Vous pouvez associer un <xref:System.Windows.Forms.ContextMenuStrip> à n’importe quel contrôle et cliquer sur le bouton droit de la souris pour afficher automatiquement le menu contextuel (ou le menu contextuel). Vous pouvez afficher un <xref:System.Windows.Forms.ContextMenuStrip> par programme à l’aide de <xref:System.Windows.Forms.ToolStripDropDown.Show%2A> la méthode. <xref:System.Windows.Forms.ContextMenuStrip>prend en charge <xref:System.Windows.Forms.ToolStripDropDown.Opening> les <xref:System.Windows.Forms.ToolStripDropDown.Closing> événements cancelable et pour gérer le remplissage dynamique et les scénarios de clic multiple. <xref:System.Windows.Forms.ContextMenuStrip>prend en charge les images, l’état de vérification des éléments de menu, le texte, les touches d’accès, les raccourcis et les menus en cascade.

Les éléments suivants sont spécialement conçus pour fonctionner de manière transparente avec <xref:System.Windows.Forms.ToolStripSystemRenderer> et <xref:System.Windows.Forms.ToolStripProfessionalRenderer> dans toutes les orientations. Ils sont disponibles par défaut au moment de la conception <xref:System.Windows.Forms.ContextMenuStrip> pour le contrôle:

- <xref:System.Windows.Forms.ToolStripMenuItem>

- <xref:System.Windows.Forms.ToolStripSeparator>

- <xref:System.Windows.Forms.ToolStripTextBox>

- <xref:System.Windows.Forms.ToolStripComboBox>

### <a name="toolstrip-generic-features"></a>Fonctionnalités génériques ToolStrip

Les rubriques suivantes décrivent les fonctionnalités et le comportement qui sont <xref:System.Windows.Forms.ToolStrip> génériques pour les contrôles dérivés et.

#### <a name="painting"></a>Peinture

Vous pouvez effectuer une peinture personnalisée <xref:System.Windows.Forms.ToolStrip> dans les contrôles de plusieurs façons. Comme avec d’autres contrôles de Windows Forms <xref:System.Windows.Forms.ToolStrip> , <xref:System.Windows.Forms.ToolStripItem> le et les deux `OnPaint` ont des `Paint` méthodes et des événements substituables. Comme pour la peinture normale, le système de coordonnées est relatif à la zone cliente du contrôle; autrement dit, le coin supérieur gauche du contrôle est 0,0. L' `Paint` événement et `OnPaint` la méthode d' <xref:System.Windows.Forms.ToolStripItem> un se comportent comme d’autres événements de peinture de contrôle.

Les <xref:System.Windows.Forms.ToolStrip> contrôles fournissent également un accès plus fin au rendu des éléments et des conteneurs par <xref:System.Windows.Forms.ToolStripRenderer> le biais de la classe, qui a des méthodes substituables pour peindre l’arrière-plan, l’arrière-plan de l’élément, l’image de l’élément, la flèche de l’élément, le texte de l’élément et la bordure du <xref:System.Windows.Forms.ToolStrip>. Les arguments d’événement pour ces méthodes exposent plusieurs propriétés telles que des rectangles, des couleurs et des formats de texte que vous pouvez ajuster comme vous le souhaitez.

Pour modifier uniquement quelques aspects de la façon dont un élément est peint, vous substituez généralement <xref:System.Windows.Forms.ToolStripRenderer>le.

Si vous écrivez un nouvel élément et que vous souhaitez contrôler tous les aspects de la peinture, substituez `OnPaint` la méthode. À partir de <xref:System.Windows.Forms.ToolStripRenderer> `OnPaint`, vous pouvez utiliser des méthodes de.

Par défaut, l' <xref:System.Windows.Forms.ToolStrip> <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> option est double mise en mémoire tampon, en tirant parti du paramètre.

#### <a name="parenting"></a>Parentage

Le concept de propriété et de parentage du conteneur est plus <xref:System.Windows.Forms.ToolStrip> complexe dans les contrôles que dans d’autres contrôles de conteneur Windows Forms. Cela est nécessaire pour prendre en charge des scénarios dynamiques tels que le dépassement de capacité, le <xref:System.Windows.Forms.ToolStrip> partage d’éléments de liste déroulante entre <xref:System.Windows.Forms.ContextMenuStrip> plusieurs éléments et la prise en charge de la génération d’un à partir d’un contrôle.

La liste suivante décrit les membres liés au parent et explique leur utilisation.

- <xref:System.Windows.Forms.ToolStripDropDown.OwnerItem%2A>accède à l’élément qui est la source de l’élément de liste déroulante. Cela est semblable à <xref:System.Windows.Forms.ContextMenuStrip.SourceControl%2A>, mais au lieu de retourner un contrôle, elle retourne <xref:System.Windows.Forms.ToolStripItem>un.

- <xref:System.Windows.Forms.ContextMenuStrip.SourceControl%2A>détermine le contrôle qui est la source du <xref:System.Windows.Forms.ContextMenuStrip> lorsque plusieurs contrôles partagent le même <xref:System.Windows.Forms.ContextMenuStrip>.

- <xref:System.Windows.Forms.ToolStripItem.GetCurrentParent%2A>est un accesseur en lecture seule à <xref:System.Windows.Forms.ToolStripItem.Parent%2A> la propriété. Un parent diffère d’un propriétaire en ce qu’un parent indique le actuel <xref:System.Windows.Forms.ToolStrip> retourné dans lequel l’élément est affiché, qui peut se trouver dans la zone de dépassement.

- <xref:System.Windows.Forms.ToolStripItem.Owner%2A>retourne le <xref:System.Windows.Forms.ToolStrip> dont la collection d’éléments contient <xref:System.Windows.Forms.ToolStripItem>le actuel. Il s’agit de la meilleure façon <xref:System.Windows.Forms.ToolStrip.ImageList%2A> de référencer ou d’autres propriétés dans <xref:System.Windows.Forms.ToolStrip> le niveau supérieur sans écrire de code spécial pour gérer le dépassement de capacité.

#### <a name="behavior-of-inherited-controls"></a>Comportement des contrôles hérités

Les contrôles suivants sont verrouillés chaque fois qu’ils sont utilisés dans l’héritage:

- <xref:System.Windows.Forms.ToolStrip>

- <xref:System.Windows.Forms.MenuStrip>

- <xref:System.Windows.Forms.ContextMenuStrip>

- <xref:System.Windows.Forms.StatusStrip>

- <xref:System.Windows.Forms.ToolStripPanel>Cela comprend les panneaux dans un <xref:System.Windows.Forms.ToolStripContainer> et également des <xref:System.Windows.Forms.ToolStripPanel> contrôles individuels.

Par exemple, créez une application Windows Forms à l’aide d’un ou plusieurs des contrôles de la liste précédente. Définissez le modificateur d’accès d’un ou de plusieurs `public` contrôles `protected`sur ou, puis générez le projet. Ajoutez un formulaire qui hérite du premier formulaire, puis sélectionnez un contrôle hérité. Le contrôle apparaît comme si son modificateur d’accès était `private`.

#### <a name="toolstripcontainer-support-of-inheritance"></a>Prise en charge par ToolStripContainer de l’héritage

Le <xref:System.Windows.Forms.ToolStripContainer> contrôle prend en charge des scénarios hérités limités, comme dans l’exemple suivant:

1. Créez une application Windows Forms.

2. Ajoutez un <xref:System.Windows.Forms.ToolStripContainer> au formulaire.

3. Affectez au modificateur d’accès <xref:System.Windows.Forms.ToolStripContainer> de `public` la `protected`valeur ou.

4. Ajoutez toute combinaison de <xref:System.Windows.Forms.ToolStrip>contrôles <xref:System.Windows.Forms.MenuStrip>, et <xref:System.Windows.Forms.ContextMenuStrip> aux <xref:System.Windows.Forms.ToolStripPanel> zones de <xref:System.Windows.Forms.ToolStripContainer>.

5. Générez le projet.

6. Ajoutez un formulaire qui hérite du premier formulaire.

7. Sélectionnez le hérité <xref:System.Windows.Forms.ToolStripContainer> sur le formulaire.

#### <a name="inherited-behavior-of-child-controls"></a>Comportement hérité des contrôles enfants

Une fois les étapes précédentes terminées, le comportement hérité suivant se produit:

- Dans le concepteur, le contrôle s’affiche avec une icône héritée.

- Les <xref:System.Windows.Forms.ToolStripPanel> contrôles sont verrouillés; vous ne pouvez pas sélectionner ou réorganiser leur contenu.

- Vous pouvez ajouter <xref:System.Windows.Forms.ToolStripContentPanel>des contrôles à <xref:System.Windows.Forms.ToolStripContentPanel>, déplacer les contrôles et en faire des contrôles enfants du.

- Vos modifications sont conservées après la génération du formulaire.

  > [!NOTE]
  > Supprimez les modificateurs d’accès <xref:System.Windows.Forms.ToolStripPanel> de tous les contrôles qui font <xref:System.Windows.Forms.ToolStripContainer>partie d’un. Le modificateur d’accès de <xref:System.Windows.Forms.ToolStripContainer> gère l’ensemble du contrôle.

#### <a name="partial-trust"></a>Confiance partielle

Les limitations des `ToolStrip`s en confiance partielle sont conçues pour empêcher l’entrée accidentelle d’informations personnelles qui peuvent être utilisées par des personnes ou services non autorisés. Les mesures de protection sont les suivantes:

- `ToolStripDropDown`les contrôles <xref:System.Security.Permissions.UIPermissionWindow.AllWindows> requièrent l’affichage d' <xref:System.Windows.Forms.ToolStripControlHost>éléments dans un. Cela s’applique aux deux contrôles intrinsèques <xref:System.Windows.Forms.ToolStripTextBox>tels <xref:System.Windows.Forms.ToolStripComboBox>que, <xref:System.Windows.Forms.ToolStripProgressBar> et, ainsi qu’aux contrôles créés par l’utilisateur. Si cette condition n’est pas remplie, ces éléments ne sont pas affichés. Aucune exception n'est levée.

- L’affectation <xref:System.Windows.Forms.ToolStripDropDown.AutoClose%2A> de la `false` valeur à la propriété n’est pas autorisée <xref:System.Windows.Forms.ToolStripDropDown.Closing> et le paramètre d’événement annulable est ignoré. Il n’est donc pas possible d’entrer plus d’une combinaison de touches sans fermer l’élément de liste déroulante. Si cette condition n’est pas remplie, ces éléments ne sont pas affichés. Aucune exception n'est levée.

- De nombreux événements de gestion de séquences de touches ne seront pas déclenchés s’ils se produisent <xref:System.Security.Permissions.UIPermissionWindow.AllWindows>dans des contextes de confiance partielle autres que.

- Les clés d’accès ne sont <xref:System.Security.Permissions.UIPermissionWindow.AllWindows> pas traitées lorsque n’est pas accordé.

#### <a name="usage"></a>Usage

Les modèles d’utilisation suivants ont une incidence <xref:System.Windows.Forms.ToolStrip> sur la disposition, l’interaction du clavier et le comportement de l’utilisateur final:

- Joint dans un<xref:System.Windows.Forms.ToolStripPanel>

  Le <xref:System.Windows.Forms.ToolStrip> peut être repositionné dans et entre <xref:System.Windows.Forms.ToolStripPanel> <xref:System.Windows.Forms.ToolStripPanel>les. La `Dock` propriété est ignorée et, si <xref:System.Windows.Forms.ToolStrip.Stretch%2A> la propriété `false`a la valeur, la <xref:System.Windows.Forms.ToolStrip> taille du s’agrandit au fur <xref:System.Windows.Forms.ToolStripPanel>et à mesure que des éléments sont ajoutés au. En général, <xref:System.Windows.Forms.ToolStrip> le ne fait pas partie de l’ordre de tabulation.

- Ancré

  Le <xref:System.Windows.Forms.ToolStrip> est placé d’un côté d’un conteneur dans une position fixe, et sa taille s’étend sur le bord entier auquel il est ancré. En général, <xref:System.Windows.Forms.ToolStrip> le ne fait pas partie de l’ordre de tabulation.

- Positionnement absolu

  Est semblable à d’autres contrôles, en ce sens qu’il est <xref:System.Windows.Forms.Control.Location%2A> placé par la propriété, a une taille fixe et participe généralement à l’ordre de tabulation. <xref:System.Windows.Forms.ToolStrip>

#### <a name="keyboard-interaction"></a>Interaction du clavier

##### <a name="access-keys"></a>Clés d’accès

Combiné avec ou après la touche ALT, les touches d’accès sont une façon d’activer un contrôle à l’aide du clavier. <xref:System.Windows.Forms.ToolStrip>prend en charge les clés d’accès explicites et implicites. La définition explicite utilise un caractère esperluette (&) qui précède la lettre. La définition implicite utilise un algorithme qui tente de trouver un élément correspondant en fonction de l’ordre des `Text` caractères dans une propriété donnée.

##### <a name="shortcut-keys"></a>Touches de raccourci

Les touches de raccourci utilisées par <xref:System.Windows.Forms.MenuStrip> un utilisent une combinaison de <xref:System.Windows.Forms.Keys> l’énumération (qui n’est pas spécifique à l’ordre) pour définir la touche de raccourci. Vous pouvez également utiliser la <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeyDisplayString%2A> propriété pour afficher une touche de raccourci avec du texte uniquement, par exemple en affichant «del» au lieu de «Delete».

##### <a name="navigation"></a>Navigation

La touche Alt active le <xref:System.Windows.Forms.MenuStrip> pointé par. <xref:System.Windows.Forms.Form.MainMenuStrip%2A> À partir de là, Ctrl + Tab permet <xref:System.Windows.Forms.ToolStrip> de naviguer `ToolStripPanel`entre les contrôles dans s. La touche TAB et les touches de direction du pavé numérique permettent de naviguer entre les <xref:System.Windows.Forms.ToolStrip>éléments d’un. Un algorithme spécial gère la navigation dans la région de dépassement de capacité. Espace sélectionne un <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripDropDownButton>un ou <xref:System.Windows.Forms.ToolStripSplitButton>un.

##### <a name="focus-and-validation"></a>Focus et validation

Lorsqu’il est activé par la touche Alt <xref:System.Windows.Forms.MenuStrip> , <xref:System.Windows.Forms.ToolStrip> ou ne prend pas et ne supprime pas le focus du contrôle qui a actuellement le focus. Si un contrôle est hébergé dans le <xref:System.Windows.Forms.MenuStrip> ou dans une liste déroulante <xref:System.Windows.Forms.MenuStrip>du, le contrôle obtient le focus lorsque l’utilisateur appuie sur la touche Tab. En général, les <xref:System.Windows.Forms.Control.GotFocus>événements <xref:System.Windows.Forms.Control.LostFocus> <xref:System.Windows.Forms.Control.Enter>,, et <xref:System.Windows.Forms.Control.Leave> de <xref:System.Windows.Forms.MenuStrip> ne peuvent pas être déclenchés lorsqu’ils sont activés par le clavier. Dans ce cas, utilisez les <xref:System.Windows.Forms.MenuStrip.MenuActivate> événements <xref:System.Windows.Forms.MenuStrip.MenuDeactivate> et à la place.

Par défaut, <xref:System.Windows.Forms.ToolStrip.CausesValidation%2A> est `false`. Appelez <xref:System.Windows.Forms.ContainerControl.Validate%2A> explicitement sur votre formulaire pour effectuer la validation.

#### <a name="layout"></a>Mise en page

Pour contrôler <xref:System.Windows.Forms.ToolStrip> la disposition, vous devez choisir l’un <xref:System.Windows.Forms.ToolStripLayoutStyle> des membres <xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A> de avec la propriété.

##### <a name="stack-layouts"></a>Dispositions de la pile

L’empilement est la réorganisation des éléments à côté des deux extrémités de <xref:System.Windows.Forms.ToolStrip>. La liste suivante décrit les dispositions de la pile.

- <xref:System.Windows.Forms.ToolStripLayoutStyle.StackWithOverflow>est la valeur par défaut. Ce paramètre entraîne la <xref:System.Windows.Forms.ToolStrip> modification automatique de sa disposition par le en fonction <xref:System.Windows.Forms.ToolStrip.Orientation%2A> de la propriété pour gérer les glisser-déplacer et les scénarios d’ancrage.

- <xref:System.Windows.Forms.ToolStripLayoutStyle.VerticalStackWithOverflow>génère le rendu <xref:System.Windows.Forms.ToolStrip> des éléments les uns à côté des autres verticalement.

- <xref:System.Windows.Forms.ToolStripLayoutStyle.HorizontalStackWithOverflow>restitue les <xref:System.Windows.Forms.ToolStrip> éléments à côté horizontalement.

##### <a name="other-features-of-stack-layouts"></a>Autres fonctionnalités des dispositions de la pile

<xref:System.Windows.Forms.ToolStripItem.Alignment%2A>détermine la fin du <xref:System.Windows.Forms.ToolStrip> auquel l’élément est aligné.

Lorsque les éléments ne tiennent pas dans <xref:System.Windows.Forms.ToolStrip>le, un bouton de dépassement de capacité s’affiche automatiquement. Le <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> paramètre de propriété détermine si un élément apparaît toujours dans la zone de dépassement de capacité, si nécessaire, ou jamais.

Dans l' <xref:System.Windows.Forms.ToolStrip.LayoutCompleted> événement, vous pouvez inspecter <xref:System.Windows.Forms.ToolStripItem.Placement%2A> la propriété pour déterminer si un élément a été placé sur <xref:System.Windows.Forms.ToolStrip>le principal, <xref:System.Windows.Forms.ToolStrip>le dépassement de capacité ou s’il n’apparaît pas du tout. Les raisons classiques pour lesquelles un élément n’est pas affiché sont que l’élément ne s’ajuste <xref:System.Windows.Forms.ToolStrip> pas à <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> la main et que <xref:System.Windows.Forms.ToolStripItemOverflow.Never>sa propriété a la valeur.

Rendez <xref:System.Windows.Forms.ToolStrip> un déplaçable en le plaçant dans <xref:System.Windows.Forms.ToolStripPanel> un et en <xref:System.Windows.Forms.ToolStrip.GripStyle%2A> affectant à <xref:System.Windows.Forms.ToolStripGripStyle.Visible>la valeur.

##### <a name="other-layout-options"></a>Autres options de disposition

Les autres options de disposition <xref:System.Windows.Forms.ToolStripLayoutStyle.Flow> sont <xref:System.Windows.Forms.ToolStripLayoutStyle.Table>et.

##### <a name="flow-layout"></a>Mise en page fluide

<xref:System.Windows.Forms.ToolStripLayoutStyle.Flow>la disposition est la valeur <xref:System.Windows.Forms.ContextMenuStrip>par <xref:System.Windows.Forms.ToolStripDropDownMenu>défaut pour <xref:System.Windows.Forms.ToolStripOverflow>, et. Elle est similaire à la <xref:System.Windows.Forms.FlowLayoutPanel>. Les fonctionnalités de <xref:System.Windows.Forms.ToolStripLayoutStyle.Flow> la disposition sont les suivantes:

- Toutes les fonctionnalités de <xref:System.Windows.Forms.FlowLayoutPanel> sont exposées par la <xref:System.Windows.Forms.ToolStrip.LayoutSettings%2A> propriété. Vous devez effectuer un <xref:System.Windows.Forms.LayoutSettings> cast de la <xref:System.Windows.Forms.FlowLayoutSettings> classe en une classe.

- Vous pouvez utiliser les <xref:System.Windows.Forms.ToolStripItem.Dock%2A> propriétés <xref:System.Windows.Forms.ToolStripItem.Anchor%2A> et dans le code pour aligner les éléments dans la ligne.

- La propriété <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> est ignorée.

- Dans l' <xref:System.Windows.Forms.ToolStrip.LayoutCompleted> événement, vous pouvez inspecter <xref:System.Windows.Forms.ToolStripItem.Placement%2A> la propriété pour déterminer si un élément a été placé sur <xref:System.Windows.Forms.ToolStrip> le principal ou s’il ne s’ajuste pas.

- La poignée n’est pas restituée et par <xref:System.Windows.Forms.ToolStrip> conséquent <xref:System.Windows.Forms.ToolStripLayoutStyle.Flow> , un dans le <xref:System.Windows.Forms.ToolStripPanel> style de disposition d’un ne peut pas être déplacé.

- Le <xref:System.Windows.Forms.ToolStrip> bouton de dépassement de capacité n’est <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> pas rendu et est ignoré.

##### <a name="table-layout"></a>Disposition du tableau

<xref:System.Windows.Forms.ToolStripLayoutStyle.Table>la disposition est la valeur <xref:System.Windows.Forms.StatusStrip>par défaut pour. Elle est similaire à <xref:System.Windows.Forms.TableLayoutPanel>. Les fonctionnalités de <xref:System.Windows.Forms.ToolStripLayoutStyle.Flow> la disposition sont les suivantes:

- Toutes les fonctionnalités de <xref:System.Windows.Forms.TableLayoutPanel> sont exposées par la <xref:System.Windows.Forms.ToolStrip.LayoutSettings%2A> propriété. Vous devez effectuer un <xref:System.Windows.Forms.LayoutSettings> cast de la <xref:System.Windows.Forms.TableLayoutSettings> classe en une classe.

- Vous pouvez utiliser les <xref:System.Windows.Forms.ToolStripItem.Dock%2A> propriétés <xref:System.Windows.Forms.ToolStripItem.Anchor%2A> et dans le code pour aligner les éléments dans la cellule de tableau.

- La propriété <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> est ignorée.

- Dans l' <xref:System.Windows.Forms.ToolStrip.LayoutCompleted> événement, vous pouvez inspecter <xref:System.Windows.Forms.ToolStripItem.Placement%2A> la propriété pour déterminer si un élément a été placé sur <xref:System.Windows.Forms.ToolStrip> le principal ou s’il ne s’ajuste pas.

- La poignée n’est pas restituée et par <xref:System.Windows.Forms.ToolStrip> conséquent <xref:System.Windows.Forms.ToolStripLayoutStyle.Table> , un dans le <xref:System.Windows.Forms.ToolStripPanel> style de disposition d’un ne peut pas être déplacé.

- Le <xref:System.Windows.Forms.ToolStrip> bouton de dépassement de capacité n’est <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> pas rendu et est ignoré.

## <a name="toolstripitem"></a>ToolStripItem

Les rubriques suivantes décrivent <xref:System.Windows.Forms.ToolStripItem> et les contrôles qui dérivent de celui-ci.

<xref:System.Windows.Forms.ToolStripItem>est la classe de base abstraite pour tous les éléments qui entrent <xref:System.Windows.Forms.ToolStrip>dans un. Le modèle objet suivant illustre la <xref:System.Windows.Forms.ToolStripItem> hiérarchie d’héritage.

![Diagramme qui montre le modèle objet ToolStripItem.](./media/toolstrip-control-architecture/toolstripitem-object-model.gif)

<xref:System.Windows.Forms.ToolStripItem>les classes héritent directement <xref:System.Windows.Forms.ToolStripItem>de, ou elles héritent indirectement <xref:System.Windows.Forms.ToolStripControlHost> de <xref:System.Windows.Forms.ToolStripDropDownItem>à l’aide de ou de <xref:System.Windows.Forms.ToolStripItem> .

<xref:System.Windows.Forms.ToolStripItem>les contrôles doivent être contenus dans <xref:System.Windows.Forms.ToolStrip> <xref:System.Windows.Forms.StatusStrip>, <xref:System.Windows.Forms.MenuStrip>, ou <xref:System.Windows.Forms.ContextMenuStrip> et ne peuvent pas être ajoutés directement à un formulaire. Les différentes classes de conteneur sont conçues pour contenir un sous- <xref:System.Windows.Forms.ToolStripItem> ensemble approprié de contrôles.

Le tableau suivant répertorie les <xref:System.Windows.Forms.ToolStripItem> contrôles de la stock et les conteneurs dans lesquels ils s’affichent le mieux. Bien que <xref:System.Windows.Forms.ToolStrip> tous les éléments puissent être hébergés dans n’importe quel <xref:System.Windows.Forms.ToolStrip>conteneur dérivé, ils ont été conçus pour s’afficher au mieux dans les conteneurs suivants:

> [!NOTE]
> <xref:System.Windows.Forms.ToolStripDropDown>n’apparaît pas dans la boîte à outils du concepteur.

|Élément contenu|ToolStrip|MenuStrip|ContextMenuStrip|StatusStrip|ToolStripDropDown|
|--------------------|---------------|---------------|----------------------|-----------------|-----------------------|
|<xref:System.Windows.Forms.ToolStripButton>|Oui|Non|Non|Non|Oui|
|<xref:System.Windows.Forms.ToolStripComboBox>|OUI|OUI|Oui|Non|Oui|
|<xref:System.Windows.Forms.ToolStripSplitButton>|Oui|Non|Non|Oui|OUI|
|<xref:System.Windows.Forms.ToolStripLabel>|Oui|Non|Non|Oui|OUI|
|<xref:System.Windows.Forms.ToolStripSeparator>|OUI|OUI|Oui|Non|Oui|
|<xref:System.Windows.Forms.ToolStripDropDownButton>|Oui|Non|Non|Oui|OUI|
|<xref:System.Windows.Forms.ToolStripTextBox>|OUI|OUI|Oui|Non|Oui|
|<xref:System.Windows.Forms.ToolStripMenuItem>|Non|Oui|Oui|Non|Non|
|<xref:System.Windows.Forms.ToolStripStatusLabel>|Non|Non|Non|Oui|Non|
|<xref:System.Windows.Forms.ToolStripProgressBar>|Oui|Non|Non|Oui|Non|
|<xref:System.Windows.Forms.ToolStripControlHost>|Oui|Oui|Non|Oui|Oui|

### <a name="toolstripbutton"></a>ToolStripButton

<xref:System.Windows.Forms.ToolStripButton>est l’élément de bouton <xref:System.Windows.Forms.ToolStrip>pour. Vous pouvez l’afficher avec différents styles de bordure et vous pouvez l’utiliser pour représenter et activer les États opérationnels. Vous pouvez également le définir de façon à ce qu’il ait le focus par défaut.

### <a name="toolstriplabel"></a>ToolStripLabel

Fournit <xref:System.Windows.Forms.ToolStripLabel> des fonctionnalités d’étiquette <xref:System.Windows.Forms.ToolStrip> dans les contrôles. Est semblable à un <xref:System.Windows.Forms.ToolStripButton> qui n’obtient pas le focus par défaut et qui n’est pas restitué comme ayant fait l’objet d’un push ou mis en surbrillance. <xref:System.Windows.Forms.ToolStripLabel>

<xref:System.Windows.Forms.ToolStripLabel>en tant qu’élément hébergé prend en charge les clés d’accès.

Utilisez les <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>propriétés <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A>, et <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A> sur <xref:System.Windows.Forms.ToolStripLabel> pour prendre en charge le contrôle de lien <xref:System.Windows.Forms.ToolStrip>dans un.

### <a name="toolstripstatuslabel"></a>ToolStripStatusLabel

<xref:System.Windows.Forms.ToolStripStatusLabel>est une version de <xref:System.Windows.Forms.ToolStripLabel> conçue spécifiquement pour une utilisation <xref:System.Windows.Forms.StatusStrip>dans. Les fonctionnalités spéciales incluent <xref:System.Windows.Forms.ToolStripStatusLabel.BorderStyle%2A>, <xref:System.Windows.Forms.ToolStripStatusLabel.BorderSides%2A>et <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A>.

### <a name="toolstripseparator"></a>ToolStripSeparator

Le <xref:System.Windows.Forms.ToolStripSeparator> ajoute une ligne verticale ou horizontale à une barre d’outils ou à un menu, en fonction de l’orientation. Il permet de regrouper ou de faire la distinction entre des éléments, tels que ceux d’un menu.

Vous pouvez ajouter un <xref:System.Windows.Forms.ToolStripSeparator> au moment du design en le sélectionnant dans une liste déroulante. Toutefois, vous pouvez également créer automatiquement un <xref:System.Windows.Forms.ToolStripSeparator> en tapant un trait d’Union (-) dans le nœud de modèle du concepteur <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A> ou dans la méthode.

### <a name="toolstripcontrolhost"></a>ToolStripControlHost

<xref:System.Windows.Forms.ToolStripControlHost>est la classe de base abstraite <xref:System.Windows.Forms.ToolStripTextBox>pour <xref:System.Windows.Forms.ToolStripComboBox>, <xref:System.Windows.Forms.ToolStripProgressBar>et. <xref:System.Windows.Forms.ToolStripControlHost>peut héberger d’autres contrôles, y compris des contrôles personnalisés, de deux manières:

- Construisez <xref:System.Windows.Forms.Control>avec une classe qui dérive de. <xref:System.Windows.Forms.ToolStripControlHost> Pour accéder pleinement au contrôle hébergé et aux propriétés, vous devez effectuer <xref:System.Windows.Forms.ToolStripControlHost.Control%2A> un cast de la propriété vers la classe réelle qu’elle représente.

- Étendez <xref:System.Windows.Forms.ToolStripControlHost>et, dans le constructeur sans paramètre de la classe héritée, appelez le constructeur de classe de base en passant <xref:System.Windows.Forms.Control>une classe qui dérive de. Cette option vous permet d’encapsuler les méthodes et les propriétés de contrôle <xref:System.Windows.Forms.ToolStrip>communes pour un accès facile dans un.

### <a name="toolstripcombobox"></a>ToolStripComboBox

<xref:System.Windows.Forms.ToolStripComboBox>est optimisé <xref:System.Windows.Forms.ComboBox> pour l’hébergement dans un <xref:System.Windows.Forms.ToolStrip>. Un sous-ensemble des propriétés et des événements du contrôle hébergé est exposé <xref:System.Windows.Forms.ToolStripComboBox> au niveau, mais le <xref:System.Windows.Forms.ComboBox> contrôle sous-jacent est entièrement <xref:System.Windows.Forms.ToolStripComboBox.ComboBox%2A> accessible via la propriété.

### <a name="toolstriptextbox"></a>ToolStripTextBox

<xref:System.Windows.Forms.ToolStripTextBox>est optimisé <xref:System.Windows.Forms.TextBox> pour l’hébergement dans un <xref:System.Windows.Forms.ToolStrip>. Un sous-ensemble des propriétés et des événements du contrôle hébergé est exposé <xref:System.Windows.Forms.ToolStripTextBox> au niveau, mais le <xref:System.Windows.Forms.TextBox> contrôle sous-jacent est entièrement <xref:System.Windows.Forms.ToolStripTextBox.TextBox%2A> accessible via la propriété.

### <a name="toolstripprogressbar"></a>ToolStripProgressBar

<xref:System.Windows.Forms.ToolStripProgressBar>est optimisé <xref:System.Windows.Forms.ProgressBar> pour l’hébergement dans un <xref:System.Windows.Forms.ToolStrip>. Un sous-ensemble des propriétés et des événements du contrôle hébergé est exposé <xref:System.Windows.Forms.ToolStripProgressBar> au niveau, mais le <xref:System.Windows.Forms.ProgressBar> contrôle sous-jacent est entièrement <xref:System.Windows.Forms.ToolStripProgressBar.ProgressBar%2A> accessible via la propriété.

### <a name="toolstripdropdownitem"></a>ToolStripDropDownItem

<xref:System.Windows.Forms.ToolStripDropDownItem>est la classe de base abstraite <xref:System.Windows.Forms.ToolStripDropDownButton>pour <xref:System.Windows.Forms.ToolStripMenuItem>, <xref:System.Windows.Forms.ToolStripSplitButton>et, qui peut héberger des éléments directement ou héberger des éléments supplémentaires dans un conteneur déroulant. Pour ce faire, affectez <xref:System.Windows.Forms.ToolStripDropDownItem.DropDown%2A> à la propriété la valeur <xref:System.Windows.Forms.ToolStrip.Items%2A> <xref:System.Windows.Forms.ToolStripDropDown>et définissez la propriété de. <xref:System.Windows.Forms.ToolStripDropDown> Accédez à ces éléments de liste déroulante <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItems%2A> directement par le biais de la propriété.

### <a name="toolstripmenuitem"></a>ToolStripMenuItem

<xref:System.Windows.Forms.ToolStripMenuItem>est un <xref:System.Windows.Forms.ToolStripDropDownItem> qui fonctionne avec <xref:System.Windows.Forms.ToolStripDropDownMenu> et <xref:System.Windows.Forms.ContextMenuStrip> pour gérer la mise en surbrillance spéciale, la disposition et la disposition des colonnes pour les menus.

### <a name="toolstripdropdownbutton"></a>ToolStripDropDownButton

<xref:System.Windows.Forms.ToolStripDropDownButton>ressemble à <xref:System.Windows.Forms.ToolStripButton>, mais affiche une zone de liste déroulante lorsque l’utilisateur clique dessus. Masquez ou affichez la flèche déroulante en <xref:System.Windows.Forms.ToolStripDropDownButton.ShowDropDownArrow%2A> définissant la propriété. <xref:System.Windows.Forms.ToolStripDropDownButton>héberge un <xref:System.Windows.Forms.ToolStripOverflowButton> qui affiche des éléments qui dépassent le <xref:System.Windows.Forms.ToolStrip>.

### <a name="toolstripsplitbutton"></a>ToolStripSplitButton

<xref:System.Windows.Forms.ToolStripSplitButton>combine les fonctionnalités du bouton et du bouton déroulant.

Utilisez la <xref:System.Windows.Forms.ToolStripSplitButton.DefaultItem%2A> propriété pour synchroniser <xref:System.Windows.Forms.Control.Click> l’événement de l’élément de liste déroulante choisi avec l’élément affiché sur le bouton.

### <a name="toolstripitem-generic-features"></a>Fonctionnalités génériques de ToolStripItem

<xref:System.Windows.Forms.ToolStripItem>fournit les fonctionnalités et options génériques suivantes pour hériter des contrôles:

- Événements principaux

- Gestion des images

- Alignement

- Relation de texte et d’image

- Style d’affichage

#### <a name="core-events"></a>Événements principaux

<xref:System.Windows.Forms.ToolStripItem>les contrôles reçoivent leurs propres événements Click, Mouse et Paint, et peuvent également effectuer des prétraitements du clavier.

#### <a name="image-handling"></a>Gestion des images

Les <xref:System.Windows.Forms.ToolStripItem.Image%2A>propriétés <xref:System.Windows.Forms.ToolStripItem.ImageAlign%2A> ,<xref:System.Windows.Forms.ToolStripItem.ImageKey%2A>,, et<xref:System.Windows.Forms.ToolStripItem.ImageScaling%2A> se rapportent à différents aspects de la gestion d’images. <xref:System.Windows.Forms.ToolStripItem.ImageIndex%2A> Utilisez des images <xref:System.Windows.Forms.ToolStrip> dans les contrôles en définissant ces propriétés directement ou en définissant la propriété <xref:System.Windows.Forms.ToolStrip.ImageList%2A> Runtime only.

La mise à l’échelle des images est déterminée par l’interaction <xref:System.Windows.Forms.ToolStrip> des <xref:System.Windows.Forms.ToolStripItem>propriétés dans et, comme suit:

- <xref:System.Windows.Forms.ToolStrip.ImageScalingSize%2A>est l’échelle de l’image finale, telle que déterminée par la combinaison du <xref:System.Windows.Forms.ToolStripItem.ImageScaling%2A> paramètre de l’image et du paramètre du <xref:System.Windows.Forms.ToolStrip.AutoSize%2A> conteneur.

  - Si <xref:System.Windows.Forms.ToolStrip.AutoSize%2A> <xref:System.Windows.Forms.ToolStripItemImageScaling> est `true` (valeur par défaut) et <xref:System.Windows.Forms.ToolStripItemImageScaling.SizeToFit>a la valeur, aucune mise à l’échelle <xref:System.Windows.Forms.ToolStrip> de l’image n’est effectuée et la taille est celle de l’élément le plus grand, ou une taille minimale prescrite.

  - Si <xref:System.Windows.Forms.ToolStrip.AutoSize%2A> est `false` et est<xref:System.Windows.Forms.ToolStripItemImageScaling> <xref:System.Windows.Forms.ToolStrip> , ni l’image ni la mise à l’échelle ne se produisent. <xref:System.Windows.Forms.ToolStripItemImageScaling.None>

#### <a name="alignment"></a>Alignement

La valeur de la <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> propriété détermine la fin <xref:System.Windows.Forms.ToolStrip> du au niveau duquel un élément apparaît. La <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> propriété fonctionne uniquement lorsque le style <xref:System.Windows.Forms.ToolStrip> de disposition du est défini sur l’une des valeurs de dépassement de capacité de la pile.

Les éléments sont placés <xref:System.Windows.Forms.ToolStrip> dans l’ordre dans lequel les éléments apparaissent dans la collection Items. Pour modifier par programmation l’emplacement où un élément est disposé, utilisez la <xref:System.Windows.Forms.ToolStripItemCollection.Insert%2A> méthode pour déplacer l’élément dans la collection. Cette méthode déplace l’élément, mais ne le duplique pas.

#### <a name="text-and-image-relationship"></a>Relation de texte et d’image

La <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A> propriété définit le positionnement relatif de l’image par rapport au texte sur un <xref:System.Windows.Forms.ToolStripItem>. Les éléments qui ne possèdent pas d’image, de texte ou les deux sont traités comme des <xref:System.Windows.Forms.ToolStripItem> cas spéciaux afin que le n’affiche pas de place vide pour l’élément ou les éléments manquants.

#### <a name="display-style"></a>Style d’affichage

<xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A>vous permet de définir les valeurs des propriétés Text et image d’un élément tout en affichant uniquement ce que vous souhaitez. Il est généralement utilisé pour modifier uniquement le style d’affichage lors de l’affichage du même élément dans un contexte différent.

## <a name="accessory-classes"></a>Classes d’accessoire

Les classes qui fournissent différentes fonctionnalités sont les suivantes:

- <xref:System.Windows.Forms.ToolStripManager>prend <xref:System.Windows.Forms.ToolStrip>en charge les tâches relatives à l’ensemble des applications, telles que la fusion, les paramètres et les options de convertisseur.

- <xref:System.Windows.Forms.ToolStripRenderer>vous permet d’appliquer <xref:System.Windows.Forms.ToolStrip> facilement un style ou un thème particulier.

- <xref:System.Windows.Forms.ToolStripProfessionalRenderer>crée des stylets et des pinceaux basés sur une table de<xref:System.Windows.Forms.ProfessionalColorTable>couleurs remplaçable ().

- <xref:System.Windows.Forms.ToolStripSystemRenderer>applique les couleurs système et un style visuel plat <xref:System.Windows.Forms.ToolStrip> aux applications.

- <xref:System.Windows.Forms.ToolStripContainer>est semblable à <xref:System.Windows.Forms.SplitContainer>. Il utilise quatre panneaux latéraux ancrés (instances de <xref:System.Windows.Forms.ToolStripPanel>) et un panneau central (une instance de <xref:System.Windows.Forms.ToolStripContentPanel>) pour créer une organisation typique. Vous ne pouvez pas supprimer les panneaux latéraux, mais vous pouvez les masquer. Vous ne pouvez ni supprimer ni masquer le panneau central. Vous pouvez réorganiser un ou <xref:System.Windows.Forms.ToolStrip>plusieurs <xref:System.Windows.Forms.MenuStrip>contrôles, <xref:System.Windows.Forms.StatusStrip> ou dans les panneaux latéraux, et vous pouvez utiliser le panneau central pour d’autres contrôles. Le <xref:System.Windows.Forms.ToolStripContentPanel> fournit également un moyen d’obtenir une prise en charge du convertisseur dans le corps de votre formulaire pour une apparence cohérente. <xref:System.Windows.Forms.ToolStripContainer>ne prend pas en charge l’interface multidocument (MDI).

- <xref:System.Windows.Forms.ToolStripPanel>fournit de l’espace pour le déplacement <xref:System.Windows.Forms.ToolStrip> et la réorganisation des contrôles. Vous ne pouvez utiliser qu’un seul panneau si vous le souhaitez <xref:System.Windows.Forms.ToolStripPanel> , et fonctionne bien dans les scénarios MDI.

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble du contrôle ToolStrip](toolstrip-control-overview-windows-forms.md)
- [Résumé de la technologie ToolStrip](toolstrip-technology-summary.md)
- [Contrôle ToolStrip](toolstrip-control-windows-forms.md)
- [MenuStrip, contrôle](menustrip-control-windows-forms.md)
- [StatusStrip, contrôle](statusstrip-control.md)
- [ContextMenuStrip, contrôle](contextmenustrip-control.md)
- [BindingNavigator, contrôle](bindingnavigator-control-windows-forms.md)
