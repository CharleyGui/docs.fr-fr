---
title: Architecture du contrôle ToolStrip
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStrip control [Windows Forms], architecture
ms.assetid: 71df2d18-862e-4701-9ff9-c1fe606f94f2
ms.openlocfilehash: 5c500e68013bbacbb1fb3aaaeb37402942a3eaef
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67663896"
---
# <a name="toolstrip-control-architecture"></a>Architecture du contrôle ToolStrip

Le <xref:System.Windows.Forms.ToolStrip> et <xref:System.Windows.Forms.ToolStripItem> classes fournissent un système flexible et extensible pour afficher des éléments de menu, l’état et la barre d’outils. Ces classes sont toutes contenues dans le <xref:System.Windows.Forms> espace de noms et ils sont généralement nommés avec le préfixe « ToolStrip » (tel que <xref:System.Windows.Forms.ToolStripOverflow>) ou avec le suffixe « Strip » (tel que <xref:System.Windows.Forms.MenuStrip>).

## <a name="toolstrip"></a>ToolStrip

Les rubriques suivantes décrivent <xref:System.Windows.Forms.ToolStrip> et les contrôles qui en dérivent.

<xref:System.Windows.Forms.ToolStrip> est la classe de base abstraite pour <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.StatusStrip>, et <xref:System.Windows.Forms.ContextMenuStrip>. Modèle objet du suivant illustre le <xref:System.Windows.Forms.ToolStrip> hiérarchie d’héritage.

![Diagramme illustrant le modèle d’objet ToolStrip.](./media/toolstrip-control-architecture/toolstrip-object-model.gif)

Vous pouvez accéder à tous les éléments dans un <xref:System.Windows.Forms.ToolStrip> via la <xref:System.Windows.Forms.ToolStrip.Items%2A> collection. Vous pouvez accéder à tous les éléments dans un <xref:System.Windows.Forms.ToolStripDropDownItem> via la <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItems%2A> collection. Dans une classe dérivée de <xref:System.Windows.Forms.ToolStrip>, vous pouvez également utiliser le <xref:System.Windows.Forms.ToolStrip.DisplayedItems%2A> propriété à accéder uniquement aux éléments qui sont actuellement affichés. Voici les éléments qui ne sont pas actuellement dans un menu de dépassement de capacité.

Les éléments suivants sont spécifiquement conçus pour fonctionner en toute transparence avec les deux <xref:System.Windows.Forms.ToolStripSystemRenderer> et <xref:System.Windows.Forms.ToolStripProfessionalRenderer> dans toutes les orientations. Ils sont disponibles par défaut au moment du design pour le <xref:System.Windows.Forms.ToolStrip> contrôle :

- <xref:System.Windows.Forms.ToolStripButton>

- <xref:System.Windows.Forms.ToolStripSeparator>

- <xref:System.Windows.Forms.ToolStripLabel>

- <xref:System.Windows.Forms.ToolStripDropDownButton>

- <xref:System.Windows.Forms.ToolStripSplitButton>

- <xref:System.Windows.Forms.ToolStripTextBox>

- <xref:System.Windows.Forms.ToolStripComboBox>

### <a name="menustrip"></a>MenuStrip

<xref:System.Windows.Forms.MenuStrip> est le conteneur de niveau supérieur qui remplace <xref:System.Windows.Forms.MainMenu>. Il fournit également la gestion des clés et document plusieurs fonctionnalités d’interface (multidocument MDI). Point de vue fonctionnel, <xref:System.Windows.Forms.ToolStripDropDownItem> et <xref:System.Windows.Forms.ToolStripMenuItem> fonctionnent avec <xref:System.Windows.Forms.MenuStrip>, même si elles sont dérivées de <xref:System.Windows.Forms.ToolStripItem>.

Les éléments suivants sont spécifiquement conçus pour fonctionner en toute transparence avec les deux <xref:System.Windows.Forms.ToolStripSystemRenderer> et <xref:System.Windows.Forms.ToolStripProfessionalRenderer> dans toutes les orientations. Ils sont disponibles par défaut au moment du design pour le <xref:System.Windows.Forms.MenuStrip> contrôle :

- <xref:System.Windows.Forms.ToolStripMenuItem>

- <xref:System.Windows.Forms.ToolStripTextBox>

- <xref:System.Windows.Forms.ToolStripComboBox>

### <a name="statusstrip"></a>StatusStrip

<xref:System.Windows.Forms.StatusStrip> remplace le <xref:System.Windows.Forms.StatusBar> contrôle. Fonctionnalités spéciales de <xref:System.Windows.Forms.StatusStrip> incluent une disposition de table personnalisée, la prise en charge de la forme de dimensionnement et de déplacement des poignées et le `Spring` propriété, ce qui permet un <xref:System.Windows.Forms.ToolStripStatusLabel> de remplir automatiquement l’espace disponible.

Les éléments suivants sont spécifiquement conçus pour fonctionner en toute transparence avec les deux <xref:System.Windows.Forms.ToolStripSystemRenderer> et <xref:System.Windows.Forms.ToolStripProfessionalRenderer> dans toutes les orientations. Ils sont disponibles par défaut au moment du design pour le <xref:System.Windows.Forms.StatusStrip> contrôle :

- <xref:System.Windows.Forms.ToolStripStatusLabel>

- <xref:System.Windows.Forms.ToolStripDropDownButton>

- <xref:System.Windows.Forms.ToolStripSplitButton>

- <xref:System.Windows.Forms.ToolStripProgressBar>

### <a name="contextmenustrip"></a>ContextMenuStrip

<xref:System.Windows.Forms.ContextMenuStrip> remplace <xref:System.Windows.Forms.ContextMenu>. Vous pouvez associer un <xref:System.Windows.Forms.ContextMenuStrip> avec n’importe quel contrôle et un droit de la souris cliquez automatiquement s’affiche dans le menu contextuel (ou le menu contextuel). Vous pouvez afficher un <xref:System.Windows.Forms.ContextMenuStrip> par programmation en utilisant le <xref:System.Windows.Forms.ToolStripDropDown.Show%2A> (méthode). <xref:System.Windows.Forms.ContextMenuStrip> prend en charge annulable <xref:System.Windows.Forms.ToolStripDropDown.Opening> et <xref:System.Windows.Forms.ToolStripDropDown.Closing> événements pour gérer l’alimentation dynamique et cliquez sur plusieurs scénarios. <xref:System.Windows.Forms.ContextMenuStrip> prend en charge les images, élément de menu vérifier l’état, texte, les clés d’accès, les raccourcis et des menus en cascade.

Les éléments suivants sont spécifiquement conçus pour fonctionner en toute transparence avec les deux <xref:System.Windows.Forms.ToolStripSystemRenderer> et <xref:System.Windows.Forms.ToolStripProfessionalRenderer> dans toutes les orientations. Ils sont disponibles par défaut au moment du design pour le <xref:System.Windows.Forms.ContextMenuStrip> contrôle :

- <xref:System.Windows.Forms.ToolStripMenuItem>

- <xref:System.Windows.Forms.ToolStripSeparator>

- <xref:System.Windows.Forms.ToolStripTextBox>

- <xref:System.Windows.Forms.ToolStripComboBox>

### <a name="toolstrip-generic-features"></a>Fonctionnalités génériques de ToolStrip

Les rubriques suivantes décrivent les fonctionnalités et le comportement qui sont génériques pour le <xref:System.Windows.Forms.ToolStrip> et contrôles dérivés.

#### <a name="painting"></a>Peinture

Vous pouvez effectuer une peinture personnalisée <xref:System.Windows.Forms.ToolStrip> contrôles de plusieurs façons. Comme avec d’autres contrôles Windows Forms, le <xref:System.Windows.Forms.ToolStrip> et <xref:System.Windows.Forms.ToolStripItem> ont tous deux substituable `OnPaint` méthodes et `Paint` événements. Comme avec la peinture ordinaire, le système de coordonnées est relatif à la zone cliente du contrôle ; Autrement dit, le coin supérieur gauche du contrôle est 0, 0. Le `Paint` événement et `OnPaint` méthode pour un <xref:System.Windows.Forms.ToolStripItem> se comportent comme d’autres événements de peinture du contrôle.

Le <xref:System.Windows.Forms.ToolStrip> contrôles fournissent également un accès plus précis au rendu des éléments et du conteneur via la <xref:System.Windows.Forms.ToolStripRenderer> (classe), qui a des méthodes substituables pour peindre l’arrière-plan d’arrière-plan d’élément, image de l’élément, élément flèche, texte de l’élément et la bordure de la <xref:System.Windows.Forms.ToolStrip>. Les arguments d’événement pour ces méthodes exposent plusieurs propriétés telles que des rectangles, des couleurs et des formats de texte que vous pouvez ajuster comme vous le souhaitez.

Pour ajuster uniquement quelques aspects de la peinture d’un élément, vous substituez en général la <xref:System.Windows.Forms.ToolStripRenderer>.

Si vous écrivez un nouvel élément et souhaitez contrôler tous les aspects de la peinture, substituez le `OnPaint` (méthode). Depuis `OnPaint`, vous pouvez utiliser les méthodes à partir de la <xref:System.Windows.Forms.ToolStripRenderer>.

Par défaut, le <xref:System.Windows.Forms.ToolStrip> double est mis en mémoire tampon, en tirant parti de la <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> paramètre.

#### <a name="parenting"></a>Parentage

Le concept de parentage et propriété de conteneur est plus complexe dans <xref:System.Windows.Forms.ToolStrip> contrôle que dans d’autres contrôles de conteneur Windows Forms. Qui est nécessaire pour prendre en charge des scénarios dynamiques telles que de dépassement de capacité, partage des éléments déroulants entre plusieurs <xref:System.Windows.Forms.ToolStrip> éléments et pour prendre en charge la génération d’un <xref:System.Windows.Forms.ContextMenuStrip> à partir d’un contrôle.

La liste suivante décrit les membres associés au parentage et explique leur utilisation.

- <xref:System.Windows.Forms.ToolStripDropDown.OwnerItem%2A> accède à l’élément qui est la source de l’élément de liste déroulante. Cela revient à <xref:System.Windows.Forms.ContextMenuStrip.SourceControl%2A>, mais au lieu de retourner un contrôle, elle retourne un <xref:System.Windows.Forms.ToolStripItem>.

- <xref:System.Windows.Forms.ContextMenuStrip.SourceControl%2A> Détermine le contrôle qui est la source de la <xref:System.Windows.Forms.ContextMenuStrip> lorsque plusieurs contrôles partagent le même <xref:System.Windows.Forms.ContextMenuStrip>.

- <xref:System.Windows.Forms.ToolStripItem.GetCurrentParent%2A> est un accesseur en lecture seule à la <xref:System.Windows.Forms.ToolStripItem.Parent%2A> propriété. Un parent est différent d’un propriétaire dénote actuel retourné <xref:System.Windows.Forms.ToolStrip> dans lequel l’élément est affiché, qui peut être dans la zone de débordement.

- <xref:System.Windows.Forms.ToolStripItem.Owner%2A> Retourne le <xref:System.Windows.Forms.ToolStrip> dont la collection Items contient actuel <xref:System.Windows.Forms.ToolStripItem>. Ceci est le meilleur moyen pour faire référence à <xref:System.Windows.Forms.ToolStrip.ImageList%2A> ou d’autres propriétés dans le niveau supérieur <xref:System.Windows.Forms.ToolStrip> sans écrire de code spécial pour gérer le dépassement de capacité.

#### <a name="behavior-of-inherited-controls"></a>Comportement des contrôles hérités

Les contrôles suivants sont verrouillés chaque fois qu’ils sont utilisés dans l’héritage :

- <xref:System.Windows.Forms.ToolStrip>

- <xref:System.Windows.Forms.MenuStrip>

- <xref:System.Windows.Forms.ContextMenuStrip>

- <xref:System.Windows.Forms.StatusStrip>

- <xref:System.Windows.Forms.ToolStripPanel> qui inclut les panneaux dans un <xref:System.Windows.Forms.ToolStripContainer> et également individuels <xref:System.Windows.Forms.ToolStripPanel> contrôles.

Par exemple, créer une application Windows Forms à l’aide d’un ou plusieurs des contrôles dans la liste précédente. Définir le modificateur d’accès d’un ou plusieurs contrôles à `public` ou `protected`, puis générez le projet. Ajoutez un formulaire qui hérite de la première forme, puis sélectionnez un contrôle hérité. Le contrôle apparaît verrouillé et se comporte comme si son modificateur d’accès a été `private`.

#### <a name="toolstripcontainer-support-of-inheritance"></a>Prise en charge ToolStripContainer d’héritage

Le <xref:System.Windows.Forms.ToolStripContainer> contrôle prend en charge les scénarios hérités limités, semblables à l’exemple suivant :

1. Créez une application Windows Forms.

2. Ajoutez un <xref:System.Windows.Forms.ToolStripContainer> au formulaire.

3. Définir le modificateur d’accès de la <xref:System.Windows.Forms.ToolStripContainer> à `public` ou `protected`.

4. Ajouter n’importe quelle combinaison de <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, et <xref:System.Windows.Forms.ContextMenuStrip> de contrôles à la <xref:System.Windows.Forms.ToolStripPanel> régions de la <xref:System.Windows.Forms.ToolStripContainer>.

5. Générez le projet.

6. Ajoutez un formulaire qui hérite du premier formulaire.

7. Sélectionnez héritées <xref:System.Windows.Forms.ToolStripContainer> sur le formulaire.

#### <a name="inherited-behavior-of-child-controls"></a>Comportement hérité des contrôles enfants

Après avoir terminé les étapes précédentes, le comportement hérité suivant se produit :

- Dans le concepteur, le contrôle s’affiche avec une icône héritée.

- Le <xref:System.Windows.Forms.ToolStripPanel> contrôles sont verrouillées ; vous ne pouvez pas sélectionner ou réorganiser leur contenu.

- Vous pouvez ajouter des contrôles à la <xref:System.Windows.Forms.ToolStripContentPanel>, déplacer les contrôles et faire des contrôles enfants de la <xref:System.Windows.Forms.ToolStripContentPanel>.

- Vos modifications sont conservées après la génération de l’écran.

  > [!NOTE]
  > Supprimez les modificateurs d’accès de tous les <xref:System.Windows.Forms.ToolStripPanel> contrôles qui font partie d’un <xref:System.Windows.Forms.ToolStripContainer>. Le modificateur d’accès de la <xref:System.Windows.Forms.ToolStripContainer> régit l’ensemble du contrôle.

#### <a name="partial-trust"></a>Confiance partielle

Les limitations de `ToolStrip`sous confiance partielle sont conçues pour empêcher toute entrée inopportune d’informations personnelles qui peuvent être utilisées par des personnes non autorisées ou des services. Les mesures de protection sont les suivantes :

- `ToolStripDropDown` les contrôles nécessitent <xref:System.Security.Permissions.UIPermissionWindow.AllWindows> pour afficher les éléments dans un <xref:System.Windows.Forms.ToolStripControlHost>. Cela s’applique aux deux contrôles intrinsèques, tels que <xref:System.Windows.Forms.ToolStripTextBox>, <xref:System.Windows.Forms.ToolStripComboBox>, et <xref:System.Windows.Forms.ToolStripProgressBar> en tant qu’ainsi qu’aux créés par l’utilisateur des contrôles. Si cette condition n’est pas remplie, ces éléments ne sont pas affichés. Aucune exception n'est levée.

- Définition de la <xref:System.Windows.Forms.ToolStripDropDown.AutoClose%2A> propriété `false` n’est pas autorisée et l’annulable <xref:System.Windows.Forms.ToolStripDropDown.Closing> paramètre d’événement est ignoré. Cela rend impossible d’entrer plus d’une séquence de touches sans fermer l’élément de liste déroulante. Si cette condition n’est pas remplie, les éléments de ce type ne sont pas affichés. Aucune exception n'est levée.

- Nombreux gestion des événements de séquence de touches n’est pas déclenché si elles se produisent dans des contextes de confiance partielle, autre que <xref:System.Security.Permissions.UIPermissionWindow.AllWindows>.

- Clés d’accès ne sont pas traités lorsque <xref:System.Security.Permissions.UIPermissionWindow.AllWindows> n’est pas accordée.

#### <a name="usage"></a>Utilisation

Les modèles d’utilisation suivants ont une incidence sur <xref:System.Windows.Forms.ToolStrip> disposition, interaction du clavier et le comportement de l’utilisateur final :

- Joint un <xref:System.Windows.Forms.ToolStripPanel>

  Le <xref:System.Windows.Forms.ToolStrip> peut être repositionné dans le <xref:System.Windows.Forms.ToolStripPanel> et à travers <xref:System.Windows.Forms.ToolStripPanel>s. Le `Dock` propriété est ignorée et si le <xref:System.Windows.Forms.ToolStrip.Stretch%2A> propriété est `false`, la taille de la <xref:System.Windows.Forms.ToolStrip> augmente à mesure que les éléments sont ajoutés à la <xref:System.Windows.Forms.ToolStripPanel>. En règle générale, le <xref:System.Windows.Forms.ToolStrip> ne participe pas à l’ordre de tabulation.

- Ancré

  Le <xref:System.Windows.Forms.ToolStrip> est placé sur le côté « un » d’un conteneur dans une position fixe, et sa taille se développe sur l’intégralité du bord auquel elle est ancrée. En règle générale, le <xref:System.Windows.Forms.ToolStrip> ne participe pas à l’ordre de tabulation.

- Positionné de façon absolue

  Le <xref:System.Windows.Forms.ToolStrip> est comme les autres contrôles, car elle est placée par le <xref:System.Windows.Forms.Control.Location%2A> propriété, a une taille fixe et participe en général à l’ordre de tabulation.

#### <a name="keyboard-interaction"></a>Interaction du clavier

##### <a name="access-keys"></a>Clés d’accès

Combiné avec ou après la touche ALT, clés d’accès sont permettent d’activer un contrôle à l’aide du clavier. <xref:System.Windows.Forms.ToolStrip> prend en charge les clés d’accès explicites et implicites. Définition explicite utilise un caractère esperluette (&) avant la lettre. Une définition implicite utilise un algorithme qui tente de trouver un élément correspondant basé sur l’ordre des caractères dans une donnée `Text` propriété.

##### <a name="shortcut-keys"></a>Touches de raccourci

Les touches de raccourci utilisées par un <xref:System.Windows.Forms.MenuStrip> utilisent une combinaison de la <xref:System.Windows.Forms.Keys> énumération (qui n’est pas spécifique à une commande) pour définir la touche de raccourci. Vous pouvez également utiliser le <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeyDisplayString%2A> propriété pour afficher une touche de raccourci avec du texte uniquement, telles que l’affichage « Del » au lieu de « Delete ».

##### <a name="navigation"></a>Navigation

La touche ALT active le <xref:System.Windows.Forms.MenuStrip> vers lequel pointe <xref:System.Windows.Forms.Form.MainMenuStrip%2A>. À partir de là, CTRL + TAB navigue entre <xref:System.Windows.Forms.ToolStrip> contrôles `ToolStripPanel`s. La touche TAB et les touches de direction sur le pavé numérique naviguer entre les éléments dans un <xref:System.Windows.Forms.ToolStrip>. Un algorithme spécial gère la navigation dans la région de dépassement de capacité. ESPACE sélectionne un <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripDropDownButton>, ou <xref:System.Windows.Forms.ToolStripSplitButton>.

##### <a name="focus-and-validation"></a>Le focus et Validation

Lorsque activé par la touche ALT, la <xref:System.Windows.Forms.MenuStrip> ou <xref:System.Windows.Forms.ToolStrip> généralement ni prendre ni supprimer le focus du contrôle qui a actuellement le focus. Si un contrôle est hébergé dans le <xref:System.Windows.Forms.MenuStrip> ou une liste déroulante de la <xref:System.Windows.Forms.MenuStrip>, le contrôle obtient le focus lorsque l’utilisateur appuie sur la touche TAB. En règle générale, le <xref:System.Windows.Forms.Control.GotFocus>, <xref:System.Windows.Forms.Control.LostFocus>, <xref:System.Windows.Forms.Control.Enter>, et <xref:System.Windows.Forms.Control.Leave> événements de <xref:System.Windows.Forms.MenuStrip> ne peuvent pas être déclenchés lorsqu’ils sont activés par le clavier. Dans ce cas, utilisez le <xref:System.Windows.Forms.MenuStrip.MenuActivate> et <xref:System.Windows.Forms.MenuStrip.MenuDeactivate> événements à la place.

Par défaut, <xref:System.Windows.Forms.ToolStrip.CausesValidation%2A> est `false`. Appelez <xref:System.Windows.Forms.ContainerControl.Validate%2A> explicitement sur votre formulaire pour effectuer la validation.

#### <a name="layout"></a>Mise en page

Vous contrôlez <xref:System.Windows.Forms.ToolStrip> mise en page en choisissant un des membres de <xref:System.Windows.Forms.ToolStripLayoutStyle> avec le <xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A> propriété.

##### <a name="stack-layouts"></a>Dispositions de pile

L’empilement est la réorganisation des éléments entre eux aux deux extrémités de la <xref:System.Windows.Forms.ToolStrip>. La liste suivante décrit les dispositions de pile.

- <xref:System.Windows.Forms.ToolStripLayoutStyle.StackWithOverflow> est la valeur par défaut. Ce paramètre entraîne la <xref:System.Windows.Forms.ToolStrip> de modifier sa disposition automatiquement conformément à la <xref:System.Windows.Forms.ToolStrip.Orientation%2A> propriété pour gérer le déplacement et d’ancrage de scénarios.

- <xref:System.Windows.Forms.ToolStripLayoutStyle.VerticalStackWithOverflow> restitue le <xref:System.Windows.Forms.ToolStrip> verticalement les éléments entre eux.

- <xref:System.Windows.Forms.ToolStripLayoutStyle.HorizontalStackWithOverflow> restitue le <xref:System.Windows.Forms.ToolStrip> horizontalement les éléments entre eux.

##### <a name="other-features-of-stack-layouts"></a>Autres fonctionnalités des dispositions de pile

<xref:System.Windows.Forms.ToolStripItem.Alignment%2A> Détermine la fin de la <xref:System.Windows.Forms.ToolStrip> sur lequel l’élément est aligné.

Lorsque les éléments ne tiennent pas dans le <xref:System.Windows.Forms.ToolStrip>, un bouton de dépassement de capacité apparaît automatiquement. Le <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> paramètre de propriété détermine si un élément apparaît dans la zone de débordement toujours, en fonction des besoins, ou jamais.

Dans le <xref:System.Windows.Forms.ToolStrip.LayoutCompleted> événement, vous pouvez inspecter les <xref:System.Windows.Forms.ToolStripItem.Placement%2A> propriété afin de déterminer si un élément a été placé sur le principal <xref:System.Windows.Forms.ToolStrip>, le dépassement de capacité <xref:System.Windows.Forms.ToolStrip>, ou si elle ne s’affichent pas du tout. Les raisons courantes pour lesquelles un élément n’est pas affiché sont que l’élément ne tiennent pas sur le principal <xref:System.Windows.Forms.ToolStrip> et son <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> propriété a été définie sur <xref:System.Windows.Forms.ToolStripItemOverflow.Never>.

Rendre un <xref:System.Windows.Forms.ToolStrip> mobile en le plaçant un <xref:System.Windows.Forms.ToolStripPanel> et en définissant son <xref:System.Windows.Forms.ToolStrip.GripStyle%2A> à <xref:System.Windows.Forms.ToolStripGripStyle.Visible>.

##### <a name="other-layout-options"></a>Autres Options de disposition

Les autres options de disposition sont <xref:System.Windows.Forms.ToolStripLayoutStyle.Flow> et <xref:System.Windows.Forms.ToolStripLayoutStyle.Table>.

##### <a name="flow-layout"></a>Mise en page fluide

<xref:System.Windows.Forms.ToolStripLayoutStyle.Flow> mise en page est la valeur par défaut pour <xref:System.Windows.Forms.ContextMenuStrip>, <xref:System.Windows.Forms.ToolStripDropDownMenu>, et <xref:System.Windows.Forms.ToolStripOverflow>. Elle est similaire à la <xref:System.Windows.Forms.FlowLayoutPanel>. Les fonctionnalités de <xref:System.Windows.Forms.ToolStripLayoutStyle.Flow> mise en page sont les suivantes :

- Toutes les fonctionnalités de <xref:System.Windows.Forms.FlowLayoutPanel> sont exposées par le <xref:System.Windows.Forms.ToolStrip.LayoutSettings%2A> propriété. Vous devez caster la <xref:System.Windows.Forms.LayoutSettings> classe à une <xref:System.Windows.Forms.FlowLayoutSettings> classe.

- Vous pouvez utiliser la <xref:System.Windows.Forms.ToolStripItem.Dock%2A> et <xref:System.Windows.Forms.ToolStripItem.Anchor%2A> propriétés dans le code pour aligner les éléments figurant dans la ligne.

- La propriété <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> est ignorée.

- Dans le <xref:System.Windows.Forms.ToolStrip.LayoutCompleted> événement, vous pouvez inspecter les <xref:System.Windows.Forms.ToolStripItem.Placement%2A> propriété afin de déterminer si un élément a été placé sur le principal <xref:System.Windows.Forms.ToolStrip> ou ne tenaient pas.

- La poignée n’est pas restituée et par conséquent un <xref:System.Windows.Forms.ToolStrip> dans <xref:System.Windows.Forms.ToolStripLayoutStyle.Flow> style de disposition dans un <xref:System.Windows.Forms.ToolStripPanel> ne peut pas être déplacé.

- Le <xref:System.Windows.Forms.ToolStrip> bouton de dépassement de capacité n’est pas restitué, et <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> est ignoré.

##### <a name="table-layout"></a>Disposition de table

<xref:System.Windows.Forms.ToolStripLayoutStyle.Table> mise en page est la valeur par défaut pour <xref:System.Windows.Forms.StatusStrip>. Elle est similaire à <xref:System.Windows.Forms.TableLayoutPanel>. Les fonctionnalités de <xref:System.Windows.Forms.ToolStripLayoutStyle.Flow> mise en page sont les suivantes :

- Toutes les fonctionnalités de <xref:System.Windows.Forms.TableLayoutPanel> sont exposées par le <xref:System.Windows.Forms.ToolStrip.LayoutSettings%2A> propriété. Vous devez caster la <xref:System.Windows.Forms.LayoutSettings> classe à une <xref:System.Windows.Forms.TableLayoutSettings> classe.

- Vous pouvez utiliser la <xref:System.Windows.Forms.ToolStripItem.Dock%2A> et <xref:System.Windows.Forms.ToolStripItem.Anchor%2A> propriétés dans le code pour aligner les éléments dans la cellule du tableau.

- La propriété <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> est ignorée.

- Dans le <xref:System.Windows.Forms.ToolStrip.LayoutCompleted> événement, vous pouvez inspecter les <xref:System.Windows.Forms.ToolStripItem.Placement%2A> propriété afin de déterminer si un élément a été placé sur le principal <xref:System.Windows.Forms.ToolStrip> ou ne tenaient pas.

- La poignée n’est pas restituée et par conséquent un <xref:System.Windows.Forms.ToolStrip> dans <xref:System.Windows.Forms.ToolStripLayoutStyle.Table> style de disposition dans un <xref:System.Windows.Forms.ToolStripPanel> ne peut pas être déplacé.

- Le <xref:System.Windows.Forms.ToolStrip> bouton de dépassement de capacité n’est pas restitué, et <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> est ignoré.

## <a name="toolstripitem"></a>ToolStripItem

Les rubriques suivantes décrivent <xref:System.Windows.Forms.ToolStripItem> et les contrôles qui en dérivent.

<xref:System.Windows.Forms.ToolStripItem> est la classe de base abstraite pour tous les éléments qui entrent dans un <xref:System.Windows.Forms.ToolStrip>. Modèle objet du suivant illustre le <xref:System.Windows.Forms.ToolStripItem> hiérarchie d’héritage.

![Diagramme illustrant le modèle d’objet ToolStripItem.](./media/toolstrip-control-architecture/toolstripitem-object-model.gif)

<xref:System.Windows.Forms.ToolStripItem> les classes qui héritent directement de <xref:System.Windows.Forms.ToolStripItem>, ou dont ils héritent indirectement <xref:System.Windows.Forms.ToolStripItem> via <xref:System.Windows.Forms.ToolStripControlHost> ou <xref:System.Windows.Forms.ToolStripDropDownItem>.

<xref:System.Windows.Forms.ToolStripItem> les contrôles doivent être contenus dans un <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.StatusStrip>, ou <xref:System.Windows.Forms.ContextMenuStrip> et ne peut pas être ajouté directement à un formulaire. Les différentes classes de conteneur sont conçues pour contenir un sous-ensemble approprié de <xref:System.Windows.Forms.ToolStripItem> contrôles.

Le tableau suivant répertorie le stock <xref:System.Windows.Forms.ToolStripItem> contrôles et les conteneurs dans lesquels ils recherche les meilleures. Bien que les <xref:System.Windows.Forms.ToolStrip> élément permettre être hébergé dans toute <xref:System.Windows.Forms.ToolStrip>-dérivée de conteneur, ces éléments ont été conçus pour mieux dans les conteneurs suivants :

> [!NOTE]
> <xref:System.Windows.Forms.ToolStripDropDown> n’apparaît pas dans la boîte à outils Concepteur.

|Élément relation contenant-contenu|ToolStrip|MenuStrip|ContextMenuStrip|StatusStrip|ToolStripDropDown|
|--------------------|---------------|---------------|----------------------|-----------------|-----------------------|
|<xref:System.Windows.Forms.ToolStripButton>|Oui|Non|Non|Non|Oui|
|<xref:System.Windows.Forms.ToolStripComboBox>|Oui|Oui|Oui|Non|Oui|
|<xref:System.Windows.Forms.ToolStripSplitButton>|Oui|Non|Non|Oui|Oui|
|<xref:System.Windows.Forms.ToolStripLabel>|Oui|Non|Non|Oui|Oui|
|<xref:System.Windows.Forms.ToolStripSeparator>|Oui|Oui|Oui|Non|Oui|
|<xref:System.Windows.Forms.ToolStripDropDownButton>|Oui|Non|Non|Oui|Oui|
|<xref:System.Windows.Forms.ToolStripTextBox>|Oui|Oui|Oui|Non|Oui|
|<xref:System.Windows.Forms.ToolStripMenuItem>|Non|Oui|Oui|Non|Non|
|<xref:System.Windows.Forms.ToolStripStatusLabel>|Non|Non|Non|Oui|Non|
|<xref:System.Windows.Forms.ToolStripProgressBar>|Oui|Non|Non|Oui|Non|
|<xref:System.Windows.Forms.ToolStripControlHost>|Oui|Oui|Non|Oui|Oui|

### <a name="toolstripbutton"></a>ToolStripButton

<xref:System.Windows.Forms.ToolStripButton> est l’élément de bouton pour <xref:System.Windows.Forms.ToolStrip>. Vous pouvez l’afficher avec différents styles de bordure, et vous pouvez l’utiliser pour représenter et activer des états opérationnels. Vous pouvez également définir comme ayant le focus par défaut.

### <a name="toolstriplabel"></a>ToolStripLabel

Le <xref:System.Windows.Forms.ToolStripLabel> fournit des fonctionnalités d’étiquette dans <xref:System.Windows.Forms.ToolStrip> contrôles. Le <xref:System.Windows.Forms.ToolStripLabel> est similaire à un <xref:System.Windows.Forms.ToolStripButton> qui n’obtient pas le focus par défaut et qui ne s’affichent pas comme envoyées ou en surbrillance.

<xref:System.Windows.Forms.ToolStripLabel> en tant qu’élément hébergé prend en charge les clés d’accès.

Utilisez le <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>, <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A>, et <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A> propriétés sur un <xref:System.Windows.Forms.ToolStripLabel> pour prendre en charge le contrôle de lien dans un <xref:System.Windows.Forms.ToolStrip>.

### <a name="toolstripstatuslabel"></a>ToolStripStatusLabel

<xref:System.Windows.Forms.ToolStripStatusLabel> est une version de <xref:System.Windows.Forms.ToolStripLabel> conçu spécifiquement pour une utilisation dans <xref:System.Windows.Forms.StatusStrip>. Les fonctionnalités spéciales incluent <xref:System.Windows.Forms.ToolStripStatusLabel.BorderStyle%2A>, <xref:System.Windows.Forms.ToolStripStatusLabel.BorderSides%2A>, et <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A>.

### <a name="toolstripseparator"></a>ToolStripSeparator

Le <xref:System.Windows.Forms.ToolStripSeparator> ajoute une ligne verticale ou horizontale à une barre d’outils ou un menu, selon l’orientation. Il fournit le regroupement d’ou de la distinction entre les éléments, tels que ceux d’un menu.

Vous pouvez ajouter un <xref:System.Windows.Forms.ToolStripSeparator> au moment du design en la sélectionnant dans une liste déroulante. Toutefois, vous pouvez également créer automatiquement un <xref:System.Windows.Forms.ToolStripSeparator> en tapant un trait d’union (-) dans le nœud de modèle du concepteur ou dans le <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A> (méthode).

### <a name="toolstripcontrolhost"></a>ToolStripControlHost

<xref:System.Windows.Forms.ToolStripControlHost> est la classe de base abstraite pour <xref:System.Windows.Forms.ToolStripComboBox>, <xref:System.Windows.Forms.ToolStripTextBox>, et <xref:System.Windows.Forms.ToolStripProgressBar>. <xref:System.Windows.Forms.ToolStripControlHost> peut héberger d’autres contrôles, y compris les contrôles personnalisés, de deux manières :

- Construire un <xref:System.Windows.Forms.ToolStripControlHost> avec une classe qui dérive de <xref:System.Windows.Forms.Control>. Pour accéder pleinement les propriétés et le contrôle hébergé, vous devez caster la <xref:System.Windows.Forms.ToolStripControlHost.Control%2A> propriété à la véritable classe il représente.

- Étendre <xref:System.Windows.Forms.ToolStripControlHost>et dans le constructeur par défaut de la classe héritée, appelez le constructeur de classe de base en passant une classe qui dérive de <xref:System.Windows.Forms.Control>. Cette option vous permet d’encapsuler des méthodes de contrôle et des propriétés pour un accès facile dans un <xref:System.Windows.Forms.ToolStrip>.

### <a name="toolstripcombobox"></a>ToolStripComboBox

<xref:System.Windows.Forms.ToolStripComboBox> est le <xref:System.Windows.Forms.ComboBox> optimisée pour l’hébergement dans un <xref:System.Windows.Forms.ToolStrip>. Un sous-ensemble de propriétés et les événements du contrôle hébergé est exposé au <xref:System.Windows.Forms.ToolStripComboBox> niveau mais sous-jacent <xref:System.Windows.Forms.ComboBox> contrôle est accessible via la <xref:System.Windows.Forms.ToolStripComboBox.ComboBox%2A> propriété.

### <a name="toolstriptextbox"></a>ToolStripTextBox

<xref:System.Windows.Forms.ToolStripTextBox> est le <xref:System.Windows.Forms.TextBox> optimisée pour l’hébergement dans un <xref:System.Windows.Forms.ToolStrip>. Un sous-ensemble de propriétés et les événements du contrôle hébergé est exposé au <xref:System.Windows.Forms.ToolStripTextBox> niveau mais sous-jacent <xref:System.Windows.Forms.TextBox> contrôle est accessible via la <xref:System.Windows.Forms.ToolStripTextBox.TextBox%2A> propriété.

### <a name="toolstripprogressbar"></a>ToolStripProgressBar

<xref:System.Windows.Forms.ToolStripProgressBar> est le <xref:System.Windows.Forms.ProgressBar> optimisée pour l’hébergement dans un <xref:System.Windows.Forms.ToolStrip>. Un sous-ensemble de propriétés et les événements du contrôle hébergé est exposé au <xref:System.Windows.Forms.ToolStripProgressBar> niveau mais sous-jacent <xref:System.Windows.Forms.ProgressBar> contrôle est accessible via la <xref:System.Windows.Forms.ToolStripProgressBar.ProgressBar%2A> propriété.

### <a name="toolstripdropdownitem"></a>ToolStripDropDownItem

<xref:System.Windows.Forms.ToolStripDropDownItem> est la classe de base abstraite pour <xref:System.Windows.Forms.ToolStripMenuItem>, <xref:System.Windows.Forms.ToolStripDropDownButton>, et <xref:System.Windows.Forms.ToolStripSplitButton>, qui peuvent héberger des éléments directement ou héberger des éléments supplémentaires dans un conteneur de liste déroulante. Ce faire, vous devez définir le <xref:System.Windows.Forms.ToolStripDropDownItem.DropDown%2A> propriété à un <xref:System.Windows.Forms.ToolStripDropDown> et en définissant le <xref:System.Windows.Forms.ToolStrip.Items%2A> propriété de la <xref:System.Windows.Forms.ToolStripDropDown>. Accéder à ces éléments de liste déroulante directement via le <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItems%2A> propriété.

### <a name="toolstripmenuitem"></a>ToolStripMenuItem

<xref:System.Windows.Forms.ToolStripMenuItem> est un <xref:System.Windows.Forms.ToolStripDropDownItem> qui fonctionne avec les <xref:System.Windows.Forms.ToolStripDropDownMenu> et <xref:System.Windows.Forms.ContextMenuStrip> pour gérer la disposition de la mise en surbrillance, de mise en page et de colonne spéciale pour les menus.

### <a name="toolstripdropdownbutton"></a>ToolStripDropDownButton

<xref:System.Windows.Forms.ToolStripDropDownButton> ressemble à <xref:System.Windows.Forms.ToolStripButton>, mais affiche une zone de liste déroulante lorsque l’utilisateur clique dessus. Masquer ou afficher la flèche de déroulement en définissant le <xref:System.Windows.Forms.ToolStripDropDownButton.ShowDropDownArrow%2A> propriété. <xref:System.Windows.Forms.ToolStripDropDownButton> hôtes un <xref:System.Windows.Forms.ToolStripOverflowButton> qui affiche les éléments dépassant la <xref:System.Windows.Forms.ToolStrip>.

### <a name="toolstripsplitbutton"></a>ToolStripSplitButton

<xref:System.Windows.Forms.ToolStripSplitButton> combine les fonctions de bouton et bouton de liste déroulante.

Utilisez le <xref:System.Windows.Forms.ToolStripSplitButton.DefaultItem%2A> propriété pour synchroniser le <xref:System.Windows.Forms.Control.Click> événements de l’élément de liste déroulante choisi avec l’élément affiché sur le bouton.

### <a name="toolstripitem-generic-features"></a>Fonctionnalités génériques de ToolStripItem

<xref:System.Windows.Forms.ToolStripItem> fournit les options de l’héritage des contrôles et fonctionnalités génériques suivantes :

- Événements de noyau

- Gestion des images

- Alignement

- Relation de type text et image

- Style d’affichage

#### <a name="core-events"></a>Événements de noyau

<xref:System.Windows.Forms.ToolStripItem> contrôles recevoir leurs propres cliquez, les souris et les événements paint et peuvent effectuer certains clavier prétraitement également.

#### <a name="image-handling"></a>Gestion des images

Le <xref:System.Windows.Forms.ToolStripItem.Image%2A>, <xref:System.Windows.Forms.ToolStripItem.ImageAlign%2A>, <xref:System.Windows.Forms.ToolStripItem.ImageIndex%2A>, <xref:System.Windows.Forms.ToolStripItem.ImageKey%2A>, et <xref:System.Windows.Forms.ToolStripItem.ImageScaling%2A> propriétés relatives à divers aspects de la gestion des images. Utiliser des images dans <xref:System.Windows.Forms.ToolStrip> contrôles en définissant ces propriétés directement ou en définissant l’exécution-heure uniquement <xref:System.Windows.Forms.ToolStrip.ImageList%2A> propriété.

Mise à l’échelle de l’image est déterminé par l’interaction des propriétés dans les deux <xref:System.Windows.Forms.ToolStrip> et <xref:System.Windows.Forms.ToolStripItem>, comme suit :

- <xref:System.Windows.Forms.ToolStrip.ImageScalingSize%2A> échelle de l’image finale, tel que déterminé par la combinaison de l’image <xref:System.Windows.Forms.ToolStripItem.ImageScaling%2A> paramètre et du conteneur <xref:System.Windows.Forms.ToolStrip.AutoSize%2A> paramètre.

  - Si <xref:System.Windows.Forms.ToolStrip.AutoSize%2A> est `true` (la valeur par défaut) et <xref:System.Windows.Forms.ToolStripItemImageScaling> est <xref:System.Windows.Forms.ToolStripItemImageScaling.SizeToFit>, aucune image mise à l’échelle se produit et le <xref:System.Windows.Forms.ToolStrip> taille est celle de l’élément plus grand, ou une taille minimale recommandée.

  - Si <xref:System.Windows.Forms.ToolStrip.AutoSize%2A> est `false` et <xref:System.Windows.Forms.ToolStripItemImageScaling> est <xref:System.Windows.Forms.ToolStripItemImageScaling.None>, aucune image ni <xref:System.Windows.Forms.ToolStrip> mise à l’échelle se produit.

#### <a name="alignment"></a>Alignement

La valeur de la <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> propriété détermine la fin de la <xref:System.Windows.Forms.ToolStrip> à laquelle un élément apparaît. Le <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> propriété fonctionne uniquement lorsque le style de disposition la <xref:System.Windows.Forms.ToolStrip> est définie sur une des valeurs de dépassement de capacité de pile.

Les éléments sont placés dans le <xref:System.Windows.Forms.ToolStrip> dans l’ordre dans lequel les éléments apparaissent dans la collection d’éléments. Pour modifier par programmation dans lequel un élément est disposé, utilisez la <xref:System.Windows.Forms.ToolStripItemCollection.Insert%2A> méthode pour déplacer l’élément dans la collection. Cette méthode déplace l’élément, mais n’existe pas déjà.

#### <a name="text-and-image-relationship"></a>Texte et Image relation

Le <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A> propriété définit le positionnement relatif de l’image en ce qui concerne le texte sur un <xref:System.Windows.Forms.ToolStripItem>. Les éléments qui ne disposent pas d’une image, texte ou les deux sont traités comme des cas spéciaux afin que le <xref:System.Windows.Forms.ToolStripItem> n’affiche pas un emplacement vide pour l’ou les éléments manquants.

#### <a name="display-style"></a>Style d’affichage

<xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> vous permet de définir les valeurs des propriétés de texte et l’Image d’un élément tout en affichant uniquement ce que vous souhaitez. Cela sert généralement à modifier le style d’affichage lors de l’affichage du même élément dans un contexte différent.

## <a name="accessory-classes"></a>Classes d’accessoires

Les classes qui fournissent de nombreuses autres fonctionnalités incluent :

- <xref:System.Windows.Forms.ToolStripManager> prend en charge <xref:System.Windows.Forms.ToolStrip>-réalisation des tâches pour des applications entières, telles que les options de fusion, de paramètres et de convertisseur.

- <xref:System.Windows.Forms.ToolStripRenderer> vous permet d’appliquer un style ou thème particulier à un <xref:System.Windows.Forms.ToolStrip> facilement.

- <xref:System.Windows.Forms.ToolStripProfessionalRenderer> crée des stylets et des pinceaux basée sur une table des couleurs remplaçable (<xref:System.Windows.Forms.ProfessionalColorTable>).

- <xref:System.Windows.Forms.ToolStripSystemRenderer> applique des couleurs système et un style visuel en deux dimensions à <xref:System.Windows.Forms.ToolStrip> applications.

- <xref:System.Windows.Forms.ToolStripContainer> est similaire à <xref:System.Windows.Forms.SplitContainer>. Il utilise quatre panneaux latéraux ancrés (instances de <xref:System.Windows.Forms.ToolStripPanel>) et un panneau central (une instance de <xref:System.Windows.Forms.ToolStripContentPanel>) pour créer une disposition classique. Vous ne pouvez pas supprimer les panneaux latéraux, mais vous pouvez les masquer. Vous ne pouvez ni supprimer ni masquer le panneau central. Vous pouvez réorganiser un ou plusieurs <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, ou <xref:System.Windows.Forms.StatusStrip> contrôles dans les panneaux de côté et vous peuvent utiliser le panneau central pour d’autres contrôles. Le <xref:System.Windows.Forms.ToolStripContentPanel> offre également un moyen pour obtenir un support technique de rendu dans le corps de votre formulaire pour un aspect cohérent. <xref:System.Windows.Forms.ToolStripContainer> ne prend pas en charge l’interface multidocument (MDI).

- <xref:System.Windows.Forms.ToolStripPanel> fournit un espace pour déplacer et réorganiser <xref:System.Windows.Forms.ToolStrip> contrôles. Vous pouvez utiliser qu’un seul panneau si vous le souhaitez, et <xref:System.Windows.Forms.ToolStripPanel> fonctionne bien dans les scénarios MDI.

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble du contrôle ToolStrip](toolstrip-control-overview-windows-forms.md)
- [Résumé de la technologie ToolStrip](toolstrip-technology-summary.md)
- [Contrôle ToolStrip](toolstrip-control-windows-forms.md)
- [MenuStrip, contrôle](menustrip-control-windows-forms.md)
- [StatusStrip, contrôle](statusstrip-control.md)
- [ContextMenuStrip, contrôle](contextmenustrip-control.md)
- [BindingNavigator, contrôle](bindingnavigator-control-windows-forms.md)
