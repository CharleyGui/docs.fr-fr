---
title: Vue d’ensemble de la création de contrôles
description: L’extensibilité des contrôles Windows Presentation Foundation réduit la nécessité de créer des contrôles personnalisés. Découvrez comment créer un nouveau contrôle, si nécessaire.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], authoring overview
- authoring overview for controls [WPF]
ms.assetid: 3d864748-cff0-4e63-9b23-d8e5a635b28f
ms.openlocfilehash: 600eb193613846d7eeeb626a6dfd317d2592f809
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166343"
---
# <a name="control-authoring-overview"></a>Vue d’ensemble de la création de contrôles

L’extensibilité du modèle de contrôle [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] réduit grandement la nécessité de créer un contrôle. Vous pouvez toutefois être amené, dans certains cas, à créer un contrôle personnalisé. Cette rubrique aborde les fonctionnalités qui limitent la nécessité de créer un contrôle personnalisé et les différents modèles de création de contrôles dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Cette rubrique montre également comment créer un contrôle.

<a name="when_to_write_a_new_control"></a>

## <a name="alternatives-to-writing-a-new-control"></a>Alternatives à l’écriture d’un nouveau contrôle

Par le passé, quand vous souhaitiez obtenir une expérience personnalisée à partir d’un contrôle existant, vous étiez limité à la modification des propriétés standard du contrôle (couleur d’arrière-plan, largeur de bordure, la taille de police, etc.). Si vous souhaitiez étendre l’apparence ou le comportement d’un contrôle au-delà de ces paramètres prédéfinis, vous deviez créer un contrôle, en procédant généralement par héritage d’un contrôle existant et par substitution de la méthode responsable du dessin du contrôle.  Bien que ce soit toujours possible, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vous permet de personnaliser des contrôles existants en utilisant son modèle de contenu riche, ses styles, ses modèles et ses déclencheurs. La liste suivante donne des exemples d’utilisation de ces fonctionnalités pour créer des expériences personnalisées et cohérentes sans devoir créer un contrôle.

- **Contenu riche.** De nombreux contrôles [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] standard prennent en charge le contenu riche. Par exemple, la propriété de contenu d’un <xref:System.Windows.Controls.Button> est de type <xref:System.Object> , donc théoriquement peut être affiché sur un <xref:System.Windows.Controls.Button> .  Pour qu’un bouton affiche une image et du texte, vous pouvez ajouter une image et un <xref:System.Windows.Controls.TextBlock> à un <xref:System.Windows.Controls.StackPanel> et assigner <xref:System.Windows.Controls.StackPanel> à la <xref:System.Windows.Controls.ContentControl.Content%2A> propriété. Étant donné que les contrôles peuvent afficher des éléments visuels [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et des données arbitraires, il est moins souvent nécessaire de créer un contrôle ou de modifier un contrôle existant pour prendre en charge une visualisation complexe. Pour plus d’informations sur le modèle de contenu pour <xref:System.Windows.Controls.Button> et d’autres modèles de contenu dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , consultez [modèle de contenu WPF](wpf-content-model.md).

- **Ils.** Un <xref:System.Windows.Style> est une collection de valeurs qui représentent les propriétés d’un contrôle. Grâce aux styles, vous pouvez créer une représentation réutilisable de l’apparence et du comportement souhaités d’un contrôle sans écrire un nouveau contrôle. Par exemple, supposons que vous voulez que tous vos <xref:System.Windows.Controls.TextBlock> contrôles aient une police rouge, Arial avec une taille de police de 14. Vous pouvez créer un style comme ressource et définir les propriétés appropriées en conséquence. Ensuite, chaque <xref:System.Windows.Controls.TextBlock> que vous ajoutez à votre application aura la même apparence.

- **Modèles de données.** Un <xref:System.Windows.DataTemplate> vous permet de personnaliser le mode d’affichage des données sur un contrôle. Par exemple, un <xref:System.Windows.DataTemplate> peut être utilisé pour spécifier la façon dont les données sont affichées dans un <xref:System.Windows.Controls.ListBox> .  Pour obtenir un exemple, consultez [Vue d’ensemble des modèles de données](../data/data-templating-overview.md).  Outre la personnalisation de l’apparence des données, un <xref:System.Windows.DataTemplate> peut inclure des éléments d’interface utilisateur, ce qui vous offre une grande flexibilité dans les interfaces utilisateur personnalisées.  Par exemple, en utilisant un <xref:System.Windows.DataTemplate> , vous pouvez créer un <xref:System.Windows.Controls.ComboBox> dans lequel chaque élément contient une case à cocher.

- **Modèles de contrôle.** De nombreux contrôles dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] utilisent un <xref:System.Windows.Controls.ControlTemplate> pour définir la structure et l’apparence du contrôle, qui sépare l’apparence d’un contrôle de la fonctionnalité du contrôle. Vous pouvez modifier radicalement l’apparence d’un contrôle en redéfinissant son <xref:System.Windows.Controls.ControlTemplate> .  Imaginons par exemple que vous souhaitiez créer un contrôle ressemblant à un feu rouge. Ce contrôle a une interface utilisateur et des fonctionnalités simples.  Il se compose de trois cercles, dont un seul peut être allumé à la fois. Après une réflexion, vous pouvez vous rendre compte qu’un <xref:System.Windows.Controls.RadioButton> n’offre les fonctionnalités d’un seul élément à la fois, mais l’apparence par défaut de l’n’est pas <xref:System.Windows.Controls.RadioButton> semblable aux lumières sur un feu rouge.  Étant donné que le <xref:System.Windows.Controls.RadioButton> utilise un modèle de contrôle pour définir son apparence, il est facile de redéfinir le afin qu’il <xref:System.Windows.Controls.ControlTemplate> corresponde aux spécifications du contrôle et d’utiliser des cases d’option pour créer votre feu rouge.

  > [!NOTE]
  > Bien qu’un <xref:System.Windows.Controls.RadioButton> puisse utiliser un <xref:System.Windows.DataTemplate> , un <xref:System.Windows.DataTemplate> n’est pas suffisant dans cet exemple.  <xref:System.Windows.DataTemplate>Définit l’apparence du contenu d’un contrôle. Dans le cas d’un <xref:System.Windows.Controls.RadioButton> , le contenu est tout ce qui apparaît à droite du cercle qui indique si <xref:System.Windows.Controls.RadioButton> est sélectionné.  Dans l’exemple du feu rouge, la case d’option doit simplement être un cercle capable de « s’allumer ». Étant donné que l’apparence requise pour le feu rouge est si différente de l’apparence par défaut du <xref:System.Windows.Controls.RadioButton> , il est nécessaire de redéfinir <xref:System.Windows.Controls.ControlTemplate> .  En général <xref:System.Windows.DataTemplate> , est utilisé pour définir le contenu (ou les données) d’un contrôle, et <xref:System.Windows.Controls.ControlTemplate> est utilisé pour définir la structure d’un contrôle.

- **Déclencheurs.** Un <xref:System.Windows.Trigger> vous permet de modifier dynamiquement l’apparence et le comportement d’un contrôle sans créer de nouveau contrôle. Par exemple, supposons que vous ayez plusieurs <xref:System.Windows.Controls.ListBox> contrôles dans votre application et que vous souhaitiez que les éléments de chacun <xref:System.Windows.Controls.ListBox> soient en gras et en rouge lorsqu’ils sont sélectionnés. Votre premier instinct peut être de créer une classe qui hérite de <xref:System.Windows.Controls.ListBox> et substitue la <xref:System.Windows.Controls.Primitives.Selector.OnSelectionChanged%2A> méthode pour modifier l’apparence de l’élément sélectionné, mais une meilleure approche consiste à ajouter un déclencheur à un style de <xref:System.Windows.Controls.ListBoxItem> qui modifie l’apparence de l’élément sélectionné. Un déclencheur vous permet de changer les valeurs des propriétés ou de prendre des mesures sur la base de la valeur d’une propriété. Un <xref:System.Windows.EventTrigger> vous permet d’effectuer des actions lorsqu’un événement se produit.

Pour plus d’informations sur les styles, modèles et déclencheurs, consultez [Application d’un style et création de modèles](../../../desktop-wpf/fundamentals/styles-templates-overview.md).

En général, si votre contrôle reflète les fonctionnalités d’un contrôle existant, mais que vous souhaitez qu’il ait un aspect différent, vous devez d’abord vous demander s’il est possible d’utiliser l’une des méthodes décrites dans cette section pour changer l’apparence du contrôle existant.

<a name="models_for_control_authoring"></a>

## <a name="models-for-control-authoring"></a>Modèles de création de contrôles

Le modèle de contenu riche, les styles, les modèles et les déclencheurs réduisent la nécessité de créer des contrôles. Toutefois, si vous devez créer un contrôle, il est important de comprendre les différents modèles de création de contrôles proposés dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] propose trois modèles généraux offrant chacun un jeu de fonctionnalités et un niveau de flexibilité différent. Les classes de base pour les trois modèles sont <xref:System.Windows.Controls.UserControl> , <xref:System.Windows.Controls.Control> et <xref:System.Windows.FrameworkElement> .

### <a name="deriving-from-usercontrol"></a>Dérivation de UserControl

La façon la plus simple de créer un contrôle dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] consiste à dériver de <xref:System.Windows.Controls.UserControl> . Quand vous générez un contrôle qui hérite de <xref:System.Windows.Controls.UserControl> , vous ajoutez des composants existants au <xref:System.Windows.Controls.UserControl> , nommez les composants et référencez les gestionnaires d’événements dans [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] . Vous pouvez ensuite référencer les éléments nommés et définir les gestionnaires d’événements dans le code. Ce modèle de développement ressemble fortement à celui utilisé pour le développement d’applications dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

En cas de génération correcte, un <xref:System.Windows.Controls.UserControl> peut tirer parti des avantages du contenu, des styles et des déclencheurs enrichis. Toutefois, si votre contrôle hérite de <xref:System.Windows.Controls.UserControl> , les personnes qui utilisent votre contrôle ne seront pas en mesure d’utiliser <xref:System.Windows.DataTemplate> ou <xref:System.Windows.Controls.ControlTemplate> de personnaliser son apparence.  Il est nécessaire de dériver de la <xref:System.Windows.Controls.Control> classe ou de l’une de ses classes dérivées (autres que <xref:System.Windows.Controls.UserControl> ) pour créer un contrôle personnalisé qui prend en charge les modèles.

#### <a name="benefits-of-deriving-from-usercontrol"></a>Avantages de la dérivation de UserControl

Envisagez de dériver de <xref:System.Windows.Controls.UserControl> si tous les éléments suivants s’appliquent :

- Vous souhaitez générer votre contrôle de la même façon que vous créez une application.

- Votre contrôle contient uniquement des composants existants.

- Vous n’avez pas besoin de prendre en charge une personnalisation complexe.

### <a name="deriving-from-control"></a>Dérivation de Control

La dérivation à partir de la <xref:System.Windows.Controls.Control> classe est le modèle utilisé par la plupart des [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] contrôles existants. Lorsque vous créez un contrôle qui hérite de la <xref:System.Windows.Controls.Control> classe, vous définissez son apparence à l’aide de modèles. En procédant ainsi, vous séparez la logique opérationnelle de la représentation visuelle. Vous pouvez également garantir le découplage de l’interface utilisateur et de la logique en utilisant des commandes et des liaisons plutôt que des événements et en évitant les éléments de référence dans le <xref:System.Windows.Controls.ControlTemplate> chaque fois que cela est possible.  Si l’interface utilisateur et la logique de votre contrôle sont correctement découplées, un utilisateur de votre contrôle peut redéfinir le contrôle <xref:System.Windows.Controls.ControlTemplate> pour personnaliser son apparence. Bien que la génération d’un personnalisé ne <xref:System.Windows.Controls.Control> soit pas aussi simple que la création d’un <xref:System.Windows.Controls.UserControl> , un personnalisé <xref:System.Windows.Controls.Control> offre la plus grande flexibilité.

#### <a name="benefits-of-deriving-from-control"></a>Avantages de la dérivation de Control

Envisagez de dériver de <xref:System.Windows.Controls.Control> au lieu d’utiliser la <xref:System.Windows.Controls.UserControl> classe si l’une des conditions suivantes s’applique :

- Vous souhaitez que l’apparence de votre contrôle soit personnalisable via le <xref:System.Windows.Controls.ControlTemplate> .

- Vous souhaitez que votre contrôle prenne en charge des thèmes différents.

### <a name="deriving-from-frameworkelement"></a>Dérivation de FrameworkElement

Les contrôles qui dérivent de <xref:System.Windows.Controls.UserControl> ou s' <xref:System.Windows.Controls.Control> appuient sur la composition d’éléments existants. Pour de nombreux scénarios, il s’agit d’une solution acceptable, car tout objet qui hérite de <xref:System.Windows.FrameworkElement> peut être dans un <xref:System.Windows.Controls.ControlTemplate> . Dans certains cas, l’apparence d’un contrôle nécessite toutefois des fonctionnalités autres que celles de la composition d’éléments simples. Pour ces scénarios, la base d’un composant sur <xref:System.Windows.FrameworkElement> est le bon choix.

Il existe deux méthodes standard pour les <xref:System.Windows.FrameworkElement> composants basés sur la génération : le rendu direct et la composition d’éléments personnalisés. Le rendu direct implique de remplacer la <xref:System.Windows.UIElement.OnRender%2A> méthode de <xref:System.Windows.FrameworkElement> et de fournir des <xref:System.Windows.Media.DrawingContext> opérations qui définissent explicitement les éléments visuels du composant. Il s’agit de la méthode utilisée par <xref:System.Windows.Controls.Image> et <xref:System.Windows.Controls.Border> . La composition d’éléments personnalisés implique l’utilisation d’objets de type <xref:System.Windows.Media.Visual> pour composer l’apparence de votre composant. Pour obtenir un exemple, consultez [Utilisation d’objets DrawingVisual](../graphics-multimedia/using-drawingvisual-objects.md). <xref:System.Windows.Controls.Primitives.Track>est un exemple de contrôle dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] qui utilise la composition d’éléments personnalisés. Il est également possible de combiner le rendu direct et la composition d’éléments personnalisés au sein du même contrôle.

#### <a name="benefits-of-deriving-from-frameworkelement"></a>Avantages de la dérivation de FrameworkElement

Envisagez de dériver de <xref:System.Windows.FrameworkElement> si l’une des conditions suivantes s’applique :

- Vous souhaitez avoir un contrôle précis sur l’apparence de votre contrôle au-delà des fonctionnalités proposées par la composition d’éléments simples.

- Vous souhaitez définir l’apparence de votre contrôle en définissant votre propre logique de rendu.

- Vous souhaitez composer des éléments existants de façon innovante, ce qui va au-delà de ce qui est possible avec <xref:System.Windows.Controls.UserControl> et <xref:System.Windows.Controls.Control> .

<a name="control_authoring_basics"></a>

## <a name="control-authoring-basics"></a>Notions de base de la création de contrôles

Comme nous l’avons vu précédemment, l’une des fonctionnalités les plus puissantes de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] est la possibilité d’aller au delà de la définition de propriétés de base d’un contrôle pour changer son apparence et son comportement, sans qu’il soit besoin de créer un contrôle personnalisé. Les fonctionnalités liées à la création de styles, à la liaison de données et aux déclencheurs sont rendues possibles par le système de propriétés [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et le système d’événements [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Les sections suivantes décrivent certaines pratiques à respecter, indépendamment du modèle que vous utilisez pour créer le contrôle personnalisé, afin que les utilisateurs de votre contrôle personnalisé puissent utiliser ces fonctionnalités comme ils le feraient pour un contrôle inclus dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

### <a name="use-dependency-properties"></a>Utiliser des propriétés de dépendance

Dans le cas d’une propriété de dépendance, il est possible d’effectuer les opérations suivantes :

- Définir la propriété dans un style

- Lier la propriété à une source de données

- Utiliser une ressource dynamique comme valeur de la propriété

- Animer la propriété

Si vous souhaitez qu’une propriété de votre contrôle prenne en charge l’une de ces fonctionnalités, vous devez l’implémenter comme propriété de dépendance. L’exemple suivant montre comment définir une propriété de dépendance appelée `Value` :

- Définissez un <xref:System.Windows.DependencyProperty> identificateur nommé `ValueProperty` en tant que `public` `static` `readonly` champ.

- Inscrivez le nom de la propriété auprès du système de propriétés, en appelant <xref:System.Windows.DependencyProperty.Register%2A?displayProperty=nameWithType> , pour spécifier les éléments suivants :

  - Nom de la propriété.

  - Type de la propriété.

  - Type qui possède la propriété.

  - Métadonnées de la propriété. Les métadonnées contiennent la valeur par défaut de la propriété, <xref:System.Windows.CoerceValueCallback> et <xref:System.Windows.PropertyChangedCallback> .

- Définissez une propriété de wrapper CLR nommée `Value` , qui est le même nom que celui utilisé pour inscrire la propriété de dépendance, en implémentant les `get` accesseurs et de la propriété `set` . Notez que les `get` `set` accesseurs et appellent uniquement <xref:System.Windows.DependencyObject.GetValue%2A> et <xref:System.Windows.DependencyObject.SetValue%2A> respectivement. Il est recommandé que les accesseurs des propriétés de dépendance ne contiennent pas de logique supplémentaire, car les clients et [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] peuvent ignorer les accesseurs et appeler <xref:System.Windows.DependencyObject.GetValue%2A> et <xref:System.Windows.DependencyObject.SetValue%2A> directement. Par exemple, quand une propriété est liée à une source de données, l’accesseur `set` de la propriété n’est pas appelé.  Au lieu d’ajouter une logique supplémentaire aux accesseurs d’obtenir et de définir, utilisez les <xref:System.Windows.ValidateValueCallback> <xref:System.Windows.CoerceValueCallback> délégués, et <xref:System.Windows.PropertyChangedCallback> pour répondre à ou vérifier la valeur lorsqu’elle change.  Pour plus d’informations sur ces rappels, consultez [Validation et rappels de propriétés de dépendance](../advanced/dependency-property-callbacks-and-validation.md).

- Définissez une méthode pour le <xref:System.Windows.CoerceValueCallback> nommé `CoerceValue` . `CoerceValue` garantit que `Value` est supérieur ou égal à `MinValue` et inférieur ou égal à `MaxValue`.

- Définissez une méthode pour le <xref:System.Windows.PropertyChangedCallback> , nommé `OnValueChanged` . `OnValueChanged`crée un <xref:System.Windows.RoutedPropertyChangedEventArgs%601> objet et se prépare à déclencher l' `ValueChanged` événement routé. Les événements routés sont traités dans la section suivante.

[!code-csharp[UserControlNumericUpDown#DependencyProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDown/CSharp/NumericUpDown.xaml.cs#dependencyproperty)]
[!code-vb[UserControlNumericUpDown#DependencyProperty](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UserControlNumericUpDown/visualbasic/numericupdown.xaml.vb#dependencyproperty)]

Pour plus d’informations, consultez [Propriétés de dépendance personnalisées](../advanced/custom-dependency-properties.md).

### <a name="use-routed-events"></a>Utiliser des événements routés

Tout comme les propriétés de dépendance étendent la notion de propriétés CLR avec des fonctionnalités supplémentaires, les événements routés étendent la notion d’événements CLR standard. Quand vous créez un contrôle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], il est également conseillé d’implémenter votre événement en tant qu’événement routé, car un tel événement prend en charge le comportement suivant :

- Vous pouvez gérer les événements sur le parent de plusieurs contrôles. Si un événement est un événement de propagation, un parent unique de l’arborescence d’éléments peut s’abonner à l’événement. Les auteurs d’applications peuvent ensuite utiliser un gestionnaire unique pour répondre à l’événement de plusieurs contrôles. Par exemple, si votre contrôle fait partie de chaque élément dans un <xref:System.Windows.Controls.ListBox> (parce qu’il est inclus dans un <xref:System.Windows.DataTemplate> ), le développeur d’applications peut définir le gestionnaire d’événements pour l’événement de votre contrôle sur le <xref:System.Windows.Controls.ListBox> . Chaque fois que l’événement se produit sur un des contrôles, le gestionnaire d’événements est appelé.

- Les événements routés peuvent être utilisés dans un <xref:System.Windows.EventSetter> , ce qui permet aux développeurs d’applications de spécifier le gestionnaire d’un événement dans un style.

- Les événements routés peuvent être utilisés dans un <xref:System.Windows.EventTrigger> , ce qui est utile pour animer des propriétés à l’aide de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] . Pour plus d’informations, consultez [vue d’ensemble](../graphics-multimedia/animation-overview.md)de l’animation.

L’exemple suivant montre comment définir un événement routé :

- Définissez un <xref:System.Windows.RoutedEvent> identificateur nommé `ValueChangedEvent` en tant que `public` `static` `readonly` champ.

- Enregistrez l’événement routé en appelant la <xref:System.Windows.EventManager.RegisterRoutedEvent%2A?displayProperty=nameWithType> méthode. L’exemple spécifie les informations suivantes quand il appelle <xref:System.Windows.EventManager.RegisterRoutedEvent%2A> :

  - Le nom de l’événement est `ValueChanged`.

  - La stratégie de routage est, ce qui <xref:System.Windows.RoutingStrategy.Bubble> signifie qu’un gestionnaire d’événements sur la source (l’objet qui déclenche l’événement) est appelé en premier, puis que les gestionnaires d’événements sur les éléments parents de la source sont appelés successivement, en commençant par le gestionnaire d’événements sur l’élément parent le plus proche.

  - Le type du gestionnaire d’événements est <xref:System.Windows.RoutedPropertyChangedEventHandler%601> , construit avec un <xref:System.Decimal> type.

  - Le type propriétaire de l’événement est `NumericUpDown`.

- Déclarez un événement public nommé `ValueChanged` et incluez des déclarations d’accesseurs d’événement. L’exemple appelle <xref:System.Windows.UIElement.AddHandler%2A> dans la `add` déclaration d’accesseur et <xref:System.Windows.UIElement.RemoveHandler%2A> dans la `remove` déclaration d’accesseur pour utiliser les [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] services d’événements.

- Créez une méthode virtuelle protégée nommée `OnValueChanged`, qui déclenche l’événement `ValueChanged`.

[!code-csharp[UserControlNumericUpDown#RoutedEvent](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDown/CSharp/NumericUpDown.xaml.cs#routedevent)]
[!code-vb[UserControlNumericUpDown#RoutedEvent](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UserControlNumericUpDown/visualbasic/numericupdown.xaml.vb#routedevent)]

Pour plus d’informations, consultez [Vue d’ensemble des événements routés](../advanced/routed-events-overview.md) et [Créer un événement routé personnalisé](../advanced/how-to-create-a-custom-routed-event.md).

### <a name="use-binding"></a>Utiliser la liaison

Pour découpler l’interface utilisateur de votre contrôle de sa logique, songez à utiliser la liaison de données. Cela est particulièrement important si vous définissez l’apparence de votre contrôle à l’aide d’un <xref:System.Windows.Controls.ControlTemplate> . L’utilisation de la liaison de données permet d’éviter de référencer des parties spécifiques de l’interface utilisateur à partir du code. Il est recommandé d’éviter de référencer des éléments qui se trouvent dans le, <xref:System.Windows.Controls.ControlTemplate> car lorsque le code fait référence à des éléments qui se trouvent dans <xref:System.Windows.Controls.ControlTemplate> et que le <xref:System.Windows.Controls.ControlTemplate> est modifié, l’élément référencé doit être inclus dans le nouveau <xref:System.Windows.Controls.ControlTemplate> .

L’exemple suivant met à jour le <xref:System.Windows.Controls.TextBlock> du `NumericUpDown` contrôle, en lui assignant un nom et en référençant la zone de texte par son nom dans le code.

[!code-xaml[UserControlNumericUpDownSimple#UIRefMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDownSimple/CSharp/NumericUpDown.xaml#uirefmarkup)]

[!code-csharp[UserControlNumericUpDownSimple#UIRefCode](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDownSimple/CSharp/NumericUpDown.xaml.cs#uirefcode)]
[!code-vb[UserControlNumericUpDownSimple#UIRefCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UserControlNumericUpDownSimple/VisualBasic/NumericUpDown.xaml.vb#uirefcode)]

L’exemple suivant utilise la liaison pour accomplir la même chose.

[!code-xaml[UserControlNumericUpDown#Binding](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDown/CSharp/NumericUpDown.xaml#binding)]

Pour plus d’informations sur la liaison de données, consultez [vue d’ensemble](../../../desktop-wpf/data/data-binding-overview.md)de la liaison de données.

### <a name="design-for-designers"></a>Conception pour les concepteurs

Pour recevoir la prise en charge des contrôles WPF personnalisés dans le Concepteur WPF pour Visual Studio (par exemple, la modification de propriétés avec le Fenêtre Propriétés), suivez ces instructions.  Pour plus d’informations sur le développement pour le Concepteur WPF, consultez [conception XAML dans Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio).

#### <a name="dependency-properties"></a>Propriétés de dépendance

Veillez à implémenter le CLR `get` et les `set` accesseurs comme décrit précédemment dans la section « utiliser les propriétés de dépendance ». Les concepteurs peuvent utiliser le wrapper pour détecter la présence d’une propriété de dépendance, mais, à l’instar de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et des clients du contrôle, ils ne sont pas tenus d’appeler les accesseurs durant l’obtention ou la définition de la propriété.

#### <a name="attached-properties"></a>Propriétés attachées

Pour implémenter des propriétés jointes sur des contrôles personnalisés, tenez compte des indications suivantes :

- Ont un `public` `static` `readonly` <xref:System.Windows.DependencyProperty> de la forme *PropertyName* créée `Property` à l’aide de la <xref:System.Windows.DependencyProperty.RegisterAttached%2A> méthode. Le nom de la propriété qui est passé à <xref:System.Windows.DependencyProperty.RegisterAttached%2A> doit correspondre à *PropertyName*.

- Implémentez une paire de méthodes CLR `public` `static` nommées `Set`*NomPropriété* et `Get`*NomPropriété*. Les deux méthodes doivent accepter une classe dérivée de <xref:System.Windows.DependencyProperty> comme leur premier argument. La méthode `Set`*NomPropriété* accepte également un argument dont le type correspond au type de données inscrit pour la propriété. La méthode `Get`*NomPropriété* doit retourner une valeur du même type. Si la méthode `Set`*NomPropriété* est manquante, la propriété est marquée en lecture seule.

- `Set`*PropertyName* et `Get` *PropertyName* doivent être routés directement vers les <xref:System.Windows.DependencyObject.GetValue%2A> <xref:System.Windows.DependencyObject.SetValue%2A> méthodes et sur l’objet de dépendance cible, respectivement. Les concepteurs peuvent accéder à la propriété jointe en l’appelant par le biais du wrapper de méthode ou en effectuant un appel direct à l’objet de dépendance cible.

Pour plus d’informations sur les propriétés jointes, consultez [Vue d’ensemble des propriétés jointes](../advanced/attached-properties-overview.md).

### <a name="define-and-use-shared-resources"></a>Définir et utiliser des ressources partagées

Vous pouvez inclure votre contrôle dans le même assembly que votre application, ou la mettre en package dans un assembly séparé qui peut être utilisé dans plusieurs applications. Pour la plupart, les informations abordées dans cette rubrique sont valables, quelle que soit la méthode que vous utilisez.  Toutefois, il existe une différence notable.  Quand vous placez un contrôle dans le même assembly qu’une application, vous êtes libre d’ajouter des ressources globales au fichier App.xaml. Mais un assembly qui contient uniquement des contrôles n’a pas d' <xref:System.Windows.Application> objet associé, un fichier app. XAML n’est donc pas disponible.

Quand une application recherche une ressource, elle examine trois niveaux dans l’ordre suivant :

1. Niveau de l’élément.

   Le système commence par l’élément qui référence la ressource, puis passe en revue les ressources du parent logique, et ainsi de suite, jusqu’à atteindre l’élément racine.

2. Niveau de l’application.

   Ressources définies par l' <xref:System.Windows.Application> objet.

3. Niveau du thème.

   Les dictionnaires au niveau du thème sont enregistrés dans un sous-dossier nommé Themes.  Les fichiers contenus dans ce dossier correspondent aux thèmes.  Par exemple, vous pouvez avoir Aero.NormalColor.xaml, Luna.NormalColor.xaml, Royale.NormalColor.xaml, etc.  Vous pouvez également avoir un fichier nommé generic.xaml.  Quand le système recherche une ressource au niveau des thèmes, il la cherche en premier lieu dans le fichier spécifique au thème, puis dans generic.xaml.

Si votre contrôle se trouve dans un assembly distinct de l’application, vous devez placer vos ressources globales au niveau de l’élément ou du thème. Les deux méthodes ont leurs avantages.

#### <a name="defining-resources-at-the-element-level"></a>Définition de ressources au niveau de l’élément

Vous pouvez définir des ressources partagées au niveau de l’élément en créant un dictionnaire de ressources personnalisé et en le fusionnant avec le dictionnaire de ressources de votre contrôle.  Quand vous utilisez cette méthode, vous pouvez donner à votre fichier de ressources le nom de votre choix, et il peut se trouver dans le même dossier que vos contrôles. Les ressources au niveau de l’élément peuvent également utiliser des chaînes simples comme clés. L’exemple suivant crée un <xref:System.Windows.Media.LinearGradientBrush> fichier de ressources nommé Dictionary1. Xaml.

[!code-xaml[SharedResources#1](~/samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/Dictionary1.xaml#1)]

Une fois que vous avez défini votre dictionnaire, vous devez le fusionner avec le dictionnaire de ressources de votre contrôle.  Pour cela, utilisez [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ou du code.

L’exemple suivant fusionne un dictionnaire de ressources en [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].

[!code-xaml[SharedResources#2](~/samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/ShapeResizer.xaml#2)]

L’inconvénient de cette approche est qu’un <xref:System.Windows.ResourceDictionary> objet est créé chaque fois que vous le référencez.  Par exemple, si vous avez 10 contrôles personnalisés dans votre bibliothèque et que vous fusionnez les dictionnaires de ressources partagées pour chaque contrôle à l’aide de XAML, vous créez 10 <xref:System.Windows.ResourceDictionary> objets identiques.  Vous pouvez éviter cela en créant une classe statique qui fusionne les ressources dans le code et retourne le résultant <xref:System.Windows.ResourceDictionary> .

L’exemple suivant crée une classe qui retourne un partagé <xref:System.Windows.ResourceDictionary> .

[!code-csharp[SharedResources#3](~/samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/SharedDictionaryManager.cs#3)]

L’exemple suivant fusionne la ressource partagée avec les ressources d’un contrôle personnalisé dans le constructeur du contrôle avant d’appeler `InitializeComponent`.  Étant donné que `SharedDictionaryManager.SharedDictionary` est une propriété statique, le <xref:System.Windows.ResourceDictionary> n’est créé qu’une seule fois. Comme le dictionnaire de ressources a été fusionné avant l’appel de `InitializeComponent`, les ressources sont mises à la disposition du contrôle dans son fichier [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].

[!code-csharp[SharedResources#4](~/samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/ShapeResizer.xaml.cs#4)]

#### <a name="defining-resources-at-the-theme-level"></a>Définition de ressources au niveau de l’élément

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vous permet de créer des ressources pour différents thèmes Windows.  En tant qu’auteur du contrôle, vous pouvez définir une ressource pour un thème spécifique pour changer l’apparence de votre contrôle selon le thème utilisé. Par exemple, l’apparence d’un <xref:System.Windows.Controls.Button> dans le thème Windows classique (le thème par défaut pour windows 2000) est différente de celle du <xref:System.Windows.Controls.Button> thème Windows Luna (thème par défaut pour Windows XP), car <xref:System.Windows.Controls.Button> utilise un différent <xref:System.Windows.Controls.ControlTemplate> pour chaque thème.

Les ressources spécifiques à un thème sont conservées dans un dictionnaire de ressources avec un nom de fichier spécifique. Ces fichiers doivent se trouver dans un dossier nommé `Themes`, qui est un sous-dossier du dossier qui contient le contrôle. Le tableau suivant répertorie les fichiers des dictionnaires de ressources et le thème associé à chaque fichier :

|Nom de fichier du dictionnaire de ressources|Thème Windows|
|-----------------------------------|-------------------|
|`Classic.xaml`|Aspect Windows 9x/2000 classique sur Windows XP|
|`Luna.NormalColor.xaml`|Thème bleu par défaut sur Windows XP|
|`Luna.Homestead.xaml`|Thème vert olive sur Windows XP|
|`Luna.Metallic.xaml`|Thème argent sur Windows XP|
|`Royale.NormalColor.xaml`|Thème par défaut sur Windows XP Édition Media Center|
|`Aero.NormalColor.xaml`|Thème par défaut sur Windows Vista|

Il n’est pas nécessaire de définir une ressource pour chaque thème. Si une ressource n’est pas définie pour un thème spécifique, le contrôle vérifie `Classic.xaml` pour la ressource. Si la ressource n’est pas définie dans le fichier correspondant au thème actif ou dans `Classic.xaml`, le contrôle utilise la ressource générique, qui se trouve dans un fichier de dictionnaire de ressources nommé `generic.xaml`.  Le fichier `generic.xaml` se trouve dans le même dossier que les fichiers de dictionnaire de ressources spécifiques au thème. Bien que `generic.xaml` ne corresponde pas à un thème spécifique de Windows, il s’agit néanmoins d’un dictionnaire au niveau du thème.

L’exemple de contrôle personnalisé NumericUpDown [C#](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp) ou [Visual Basic](https://github.com/dotnet/docs/tree/master/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic) avec le thème et la prise en charge d’UI Automation contient deux dictionnaires de ressources pour le `NumericUpDown` contrôle : l’un est dans Generic. xaml et l’autre dans Luna. NormalColor. Xaml.

Quand vous placez un <xref:System.Windows.Controls.ControlTemplate> dans un fichier de dictionnaire de ressources spécifique au thème, vous devez créer un constructeur statique pour votre contrôle et appeler la <xref:System.Windows.DependencyProperty.OverrideMetadata%28System.Type%2CSystem.Windows.PropertyMetadata%29> méthode sur <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> , comme illustré dans l’exemple suivant.

[!code-csharp[CustomControlNumericUpDownOneProject#StaticConstructor](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDownOneProject/CSharp/NumericUpDown.cs#staticconstructor)]
[!code-vb[CustomControlNumericUpDownOneProject#StaticConstructor](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDownOneProject/visualbasic/numericupdown.vb#staticconstructor)]

##### <a name="defining-and-referencing-keys-for-theme-resources"></a>Définition et référencement de clés pour les ressources de thème

Quand vous définissez une ressource au niveau de l’élément, vous pouvez assigner une chaîne comme clé et accéder à la ressource par le biais de la chaîne. Lorsque vous définissez une ressource au niveau du thème, vous devez utiliser <xref:System.Windows.ComponentResourceKey> comme clé.  L’exemple suivant définit une ressource dans generic.xaml.

[!code-xaml[ThemeResourcesControlLibrary#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ThemeResourcesControlLibrary/CS/Themes/generic.xaml#5)]

L’exemple suivant référence la ressource en spécifiant le <xref:System.Windows.ComponentResourceKey> comme clé.

[!code-xaml[ThemeResourcesControlLibrary#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ThemeResourcesControlLibrary/CS/NumericUpDown.xaml#6)]

##### <a name="specifying-the-location-of-theme-resources"></a>Spécification de l’emplacement des ressources des thèmes

Pour rechercher les ressources relatives à un contrôle, l’application d’hébergement doit savoir quel l’assembly contient des ressources spécifiques au contrôle. Pour ce faire, vous pouvez ajouter <xref:System.Windows.ThemeInfoAttribute> à l’assembly qui contient le contrôle. <xref:System.Windows.ThemeInfoAttribute>A une <xref:System.Windows.ThemeInfoAttribute.GenericDictionaryLocation%2A> propriété qui spécifie l’emplacement des ressources génériques et une <xref:System.Windows.ThemeInfoAttribute.ThemeDictionaryLocation%2A> propriété qui spécifie l’emplacement des ressources spécifiques au thème.

L’exemple suivant affecte aux <xref:System.Windows.ThemeInfoAttribute.GenericDictionaryLocation%2A> Propriétés et la <xref:System.Windows.ThemeInfoAttribute.ThemeDictionaryLocation%2A> valeur <xref:System.Windows.ResourceDictionaryLocation.SourceAssembly> pour spécifier que les ressources génériques et spécifiques au thème se trouvent dans le même assembly que le contrôle.

[!code-csharp[CustomControlNumericUpDown#ThemesSection](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/Properties/AssemblyInfo.cs#themessection)]
[!code-vb[CustomControlNumericUpDown#ThemesSection](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/my project/assemblyinfo.vb#themessection)]

## <a name="see-also"></a>Voir aussi

- [Concevoir en XAML dans Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [URI à en-tête pack dans WPF](../app-development/pack-uris-in-wpf.md)
- [Personnalisation des contrôles](control-customization.md)
