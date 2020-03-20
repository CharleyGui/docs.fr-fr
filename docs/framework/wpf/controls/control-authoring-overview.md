---
title: Vue d’ensemble de la création de contrôles
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], authoring overview
- authoring overview for controls [WPF]
ms.assetid: 3d864748-cff0-4e63-9b23-d8e5a635b28f
ms.openlocfilehash: d5dd2d962c554b860fb6f68110945d56c4ee03ab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400154"
---
# <a name="control-authoring-overview"></a>Vue d’ensemble de la création de contrôles

L’extensibilité du modèle de contrôle [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] réduit grandement la nécessité de créer un contrôle. Vous pouvez toutefois être amené, dans certains cas, à créer un contrôle personnalisé. Cette rubrique aborde les fonctionnalités qui limitent la nécessité de créer un contrôle personnalisé et les différents modèles de création de contrôles dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Cette rubrique montre également comment créer un contrôle.

<a name="when_to_write_a_new_control"></a>

## <a name="alternatives-to-writing-a-new-control"></a>Alternatives à l’écriture d’un nouveau contrôle

Par le passé, quand vous souhaitiez obtenir une expérience personnalisée à partir d’un contrôle existant, vous étiez limité à la modification des propriétés standard du contrôle (couleur d’arrière-plan, largeur de bordure, la taille de police, etc.). Si vous souhaitiez étendre l’apparence ou le comportement d’un contrôle au-delà de ces paramètres prédéfinis, vous deviez créer un contrôle, en procédant généralement par héritage d’un contrôle existant et par substitution de la méthode responsable du dessin du contrôle.  Bien que ce soit toujours possible, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vous permet de personnaliser des contrôles existants en utilisant son modèle de contenu riche, ses styles, ses modèles et ses déclencheurs. La liste suivante donne des exemples d’utilisation de ces fonctionnalités pour créer des expériences personnalisées et cohérentes sans devoir créer un contrôle.

- **Contenu riche.** De nombreux contrôles [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] standard prennent en charge le contenu riche. Par exemple, la propriété <xref:System.Windows.Controls.Button> de <xref:System.Object>contenu d’un est de <xref:System.Windows.Controls.Button>type , donc théoriquement tout peut être affiché sur un .  Pour avoir un bouton afficher une image et un <xref:System.Windows.Controls.TextBlock> texte, vous pouvez ajouter une image et un à un <xref:System.Windows.Controls.StackPanel> et attribuer la <xref:System.Windows.Controls.StackPanel> <xref:System.Windows.Controls.ContentControl.Content%2A> propriété. Étant donné que les contrôles peuvent afficher des éléments visuels [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et des données arbitraires, il est moins souvent nécessaire de créer un contrôle ou de modifier un contrôle existant pour prendre en charge une visualisation complexe. Pour plus d’informations <xref:System.Windows.Controls.Button> sur le modèle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]de contenu et d’autres modèles de contenu dans , voir [WPF Content Model](wpf-content-model.md).

- **Styles.** A <xref:System.Windows.Style> est une collection de valeurs qui représentent des propriétés pour un contrôle. Grâce aux styles, vous pouvez créer une représentation réutilisable de l’apparence et du comportement souhaités d’un contrôle sans écrire un nouveau contrôle. Par exemple, supposons que <xref:System.Windows.Controls.TextBlock> vous voulez que tous vos contrôles aient rouge, la police d’Arial avec une taille de police de 14. Vous pouvez créer un style comme ressource et définir les propriétés appropriées en conséquence. Ensuite, <xref:System.Windows.Controls.TextBlock> chaque que vous ajoutez à votre application aura la même apparence.

- **Modèles de données.** A <xref:System.Windows.DataTemplate> vous permet de personnaliser la façon dont les données sont affichées sur un contrôle. Par exemple, <xref:System.Windows.DataTemplate> un peut être utilisé pour <xref:System.Windows.Controls.ListBox>spécifier comment les données sont affichées dans un .  Pour obtenir un exemple, consultez [Vue d’ensemble des modèles de données](../data/data-templating-overview.md).  En plus de personnaliser l’apparence <xref:System.Windows.DataTemplate> des données, un peut inclure des éléments d’interface utilisateur, ce qui vous donne beaucoup de flexibilité dans les UI personnalisées.  Par exemple, en <xref:System.Windows.DataTemplate>utilisant un <xref:System.Windows.Controls.ComboBox> , vous pouvez créer un élément dans lequel chaque élément contient une case à cocher.

- **Modèles de contrôle.** De nombreux [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] contrôles <xref:System.Windows.Controls.ControlTemplate> dans l’utilisation d’un pour définir la structure et l’apparence du contrôle, qui sépare l’apparence d’un contrôle de la fonctionnalité du contrôle. Vous pouvez changer radicalement l’apparence d’un contrôle en redéfinissant son <xref:System.Windows.Controls.ControlTemplate>.  Imaginons par exemple que vous souhaitiez créer un contrôle ressemblant à un feu rouge. Ce contrôle a une interface utilisateur et des fonctionnalités simples.  Il se compose de trois cercles, dont un seul peut être allumé à la fois. Après une réflexion, vous <xref:System.Windows.Controls.RadioButton> pourriez vous rendre compte qu’une offre la fonctionnalité d’un seul étant sélectionné à la fois, mais l’apparence par défaut de la <xref:System.Windows.Controls.RadioButton> ne ressemble en rien aux lumières sur un feu rouge.  Parce <xref:System.Windows.Controls.RadioButton> que l’utilisation d’un modèle de contrôle <xref:System.Windows.Controls.ControlTemplate> pour définir son apparence, il est facile de redéfinir le pour s’adapter aux exigences du contrôle, et utiliser des boutons radio pour faire votre feu rouge.

  > [!NOTE]
  > Bien <xref:System.Windows.Controls.RadioButton> qu’un <xref:System.Windows.DataTemplate>peut <xref:System.Windows.DataTemplate> utiliser un , a n’est pas suffisant dans cet exemple.  Le <xref:System.Windows.DataTemplate> définit l’apparence du contenu d’un contrôle. Dans le cas <xref:System.Windows.Controls.RadioButton>d’un , le contenu est tout ce <xref:System.Windows.Controls.RadioButton> qui apparaît à droite du cercle qui indique si le est sélectionné.  Dans l’exemple du feu rouge, la case d’option doit simplement être un cercle capable de « s’allumer ». Parce que l’exigence d’apparence pour le feu <xref:System.Windows.Controls.RadioButton>rouge est si différent <xref:System.Windows.Controls.ControlTemplate>de l’apparence par défaut de la , il est nécessaire de redéfinir le .  En général, un <xref:System.Windows.DataTemplate> est utilisé pour définir le contenu <xref:System.Windows.Controls.ControlTemplate> (ou les données) d’un contrôle, et un est utilisé pour définir comment un contrôle est structuré.

- **Déclenche.** A <xref:System.Windows.Trigger> vous permet de changer dynamiquement l’apparence et le comportement d’un contrôle sans créer un nouveau contrôle. Supposons, par exemple, que vous ayez plusieurs <xref:System.Windows.Controls.ListBox> <xref:System.Windows.Controls.ListBox> contrôles dans votre application et que vous souhaitez que les éléments de chacun d’eux soient audacieux et rouges lorsqu’ils sont sélectionnés. Votre premier instinct pourrait être de créer <xref:System.Windows.Controls.ListBox> une classe <xref:System.Windows.Controls.Primitives.Selector.OnSelectionChanged%2A> qui hérite et remplacer la méthode pour changer l’apparence de <xref:System.Windows.Controls.ListBoxItem> l’élément sélectionné, mais une meilleure approche est d’ajouter un déclencheur à un style d’un qui change l’apparence de l’élément sélectionné. Un déclencheur vous permet de changer les valeurs des propriétés ou de prendre des mesures sur la base de la valeur d’une propriété. Un <xref:System.Windows.EventTrigger> vous permet de prendre des mesures lorsqu’un événement se produit.

Pour plus d’informations sur les styles, modèles et déclencheurs, consultez [Application d’un style et création de modèles](styling-and-templating.md).

En général, si votre contrôle reflète les fonctionnalités d’un contrôle existant, mais que vous souhaitez qu’il ait un aspect différent, vous devez d’abord vous demander s’il est possible d’utiliser l’une des méthodes décrites dans cette section pour changer l’apparence du contrôle existant.

<a name="models_for_control_authoring"></a>

## <a name="models-for-control-authoring"></a>Modèles de création de contrôles

Le modèle de contenu riche, les styles, les modèles et les déclencheurs réduisent la nécessité de créer des contrôles. Toutefois, si vous devez créer un contrôle, il est important de comprendre les différents modèles de création de contrôles proposés dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] propose trois modèles généraux offrant chacun un jeu de fonctionnalités et un niveau de flexibilité différent. Les classes de base <xref:System.Windows.Controls.UserControl>pour <xref:System.Windows.Controls.Control>les <xref:System.Windows.FrameworkElement>trois modèles sont , , et .

### <a name="deriving-from-usercontrol"></a>Dérivation de UserControl

La façon la plus simple [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de créer <xref:System.Windows.Controls.UserControl>un contrôle est de dériver de . Lorsque vous construisez un <xref:System.Windows.Controls.UserControl>contrôle qui hérite de <xref:System.Windows.Controls.UserControl>, vous ajoutez des composants existants à la , nom des composants, et les gestionnaires d’événements de référence dans [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. Vous pouvez ensuite référencer les éléments nommés et définir les gestionnaires d’événements dans le code. Ce modèle de développement ressemble fortement à celui utilisé pour le développement d’applications dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

S’il est <xref:System.Windows.Controls.UserControl> construit correctement, a peut profiter des avantages d’un contenu riche, des styles et des déclencheurs. Toutefois, si votre contrôle <xref:System.Windows.Controls.UserControl>hérite de , les personnes qui <xref:System.Windows.DataTemplate> <xref:System.Windows.Controls.ControlTemplate> utilisent votre contrôle ne seront pas en mesure d’utiliser un ou de personnaliser son apparence.  Il est nécessaire de <xref:System.Windows.Controls.Control> dériver de la classe <xref:System.Windows.Controls.UserControl>ou l’une de ses classes dérivées (autre que ) pour créer un contrôle personnalisé qui prend en charge les modèles.

#### <a name="benefits-of-deriving-from-usercontrol"></a>Avantages de la dérivation de UserControl

Envisagez de <xref:System.Windows.Controls.UserControl> déduire si tous les éléments suivants s’appliquent :

- Vous souhaitez générer votre contrôle de la même façon que vous créez une application.

- Votre contrôle contient uniquement des composants existants.

- Vous n’avez pas besoin de prendre en charge une personnalisation complexe.

### <a name="deriving-from-control"></a>Dérivation de Control

Dérivé de la <xref:System.Windows.Controls.Control> classe est le modèle utilisé [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] par la plupart des contrôles existants. Lorsque vous créez un contrôle <xref:System.Windows.Controls.Control> qui hérite de la classe, vous définissez son apparence en utilisant des modèles. En procédant ainsi, vous séparez la logique opérationnelle de la représentation visuelle. Vous pouvez également assurer le découplage de l’interface utilisateur et la logique en utilisant <xref:System.Windows.Controls.ControlTemplate> des commandes et des fixations au lieu d’événements et en évitant le référencement des éléments dans la mesure du possible.  Si l’interface utilisateur et la logique de votre contrôle sont correctement découplées, un utilisateur de votre contrôle peut redéfinir le contrôle <xref:System.Windows.Controls.ControlTemplate> pour personnaliser son apparence. Bien que <xref:System.Windows.Controls.Control> la construction d’une <xref:System.Windows.Controls.UserControl>coutume <xref:System.Windows.Controls.Control> n’est pas aussi simple que la construction d’un , une coutume offre la plus grande flexibilité.

#### <a name="benefits-of-deriving-from-control"></a>Avantages de la dérivation de Control

Envisagez de <xref:System.Windows.Controls.Control> tirer de <xref:System.Windows.Controls.UserControl> la place au lieu d’utiliser la classe si l’un des éléments suivants s’applique :

- Vous voulez que l’apparence de votre <xref:System.Windows.Controls.ControlTemplate>contrôle soit personnalisable via le .

- Vous souhaitez que votre contrôle prenne en charge des thèmes différents.

### <a name="deriving-from-frameworkelement"></a>Dérivation de FrameworkElement

Contrôles qui <xref:System.Windows.Controls.UserControl> dérivent ou <xref:System.Windows.Controls.Control> reposent sur la composition d’éléments existants. Pour de nombreux scénarios, il s’agit d’une <xref:System.Windows.FrameworkElement> solution acceptable, parce que tout objet qui hérite de peut être dans un <xref:System.Windows.Controls.ControlTemplate>. Dans certains cas, l’apparence d’un contrôle nécessite toutefois des fonctionnalités autres que celles de la composition d’éléments simples. Pour ces scénarios, la base <xref:System.Windows.FrameworkElement> d’un composant est le bon choix.

Il existe deux méthodes <xref:System.Windows.FrameworkElement>standard pour la construction de composants basés sur la construction : le rendu direct et la composition d’éléments personnalisés. Le rendu direct implique <xref:System.Windows.UIElement.OnRender%2A> de <xref:System.Windows.FrameworkElement> dépasser <xref:System.Windows.Media.DrawingContext> la méthode et de fournir des opérations qui définissent explicitement les visuels des composants. C’est la <xref:System.Windows.Controls.Image> méthode <xref:System.Windows.Controls.Border>utilisée par et . La composition d’élément <xref:System.Windows.Media.Visual> personnalisé consiste à utiliser des objets de type pour composer l’apparence de votre composant. Pour obtenir un exemple, consultez [Utilisation d’objets DrawingVisual](../graphics-multimedia/using-drawingvisual-objects.md). <xref:System.Windows.Controls.Primitives.Track>est un exemple de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] contrôle qui utilise la composition des éléments personnalisés. Il est également possible de combiner le rendu direct et la composition d’éléments personnalisés au sein du même contrôle.

#### <a name="benefits-of-deriving-from-frameworkelement"></a>Avantages de la dérivation de FrameworkElement

Envisagez de <xref:System.Windows.FrameworkElement> tirer de l’application si l’un des éléments suivants s’applique :

- Vous souhaitez avoir un contrôle précis sur l’apparence de votre contrôle au-delà des fonctionnalités proposées par la composition d’éléments simples.

- Vous souhaitez définir l’apparence de votre contrôle en définissant votre propre logique de rendu.

- Vous voulez composer des éléments existants de nouvelles <xref:System.Windows.Controls.UserControl> <xref:System.Windows.Controls.Control>façons qui vont au-delà de ce qui est possible avec et .

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

- Définissez <xref:System.Windows.DependencyProperty> un `ValueProperty` identifiant `public` `static` `readonly` nommé comme un champ.

- Enregistrez le nom de propriété <xref:System.Windows.DependencyProperty.Register%2A?displayProperty=nameWithType>avec le système de propriété, en appelant, pour spécifier ce qui suit :

  - Nom de la propriété.

  - Type de la propriété.

  - Type qui possède la propriété.

  - Métadonnées de la propriété. Les métadonnées contiennent la valeur <xref:System.Windows.CoerceValueCallback> par <xref:System.Windows.PropertyChangedCallback>défaut de la propriété, a et a .

- Définir une propriété d’emballage CLR nommé `Value`, qui est le même nom qui est `get` `set` utilisé pour enregistrer la propriété de dépendance, en mettant en œuvre la propriété et les accesseurs. Notez `get` que `set` les accesseurs et les accesseurs n’appellent <xref:System.Windows.DependencyObject.GetValue%2A> que et <xref:System.Windows.DependencyObject.SetValue%2A> respectivement. Il est recommandé que les accesseurs des propriétés [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de dépendance ne <xref:System.Windows.DependencyObject.GetValue%2A> contiennent <xref:System.Windows.DependencyObject.SetValue%2A> pas de logique supplémentaire parce que les clients et peuvent contourner les accesseurs et appeler et directement. Par exemple, quand une propriété est liée à une source de données, l’accesseur `set` de la propriété n’est pas appelé.  Au lieu d’ajouter une logique supplémentaire aux <xref:System.Windows.ValidateValueCallback> <xref:System.Windows.CoerceValueCallback>accesseurs <xref:System.Windows.PropertyChangedCallback> d’accès et de configuration, utilisez le , et les délégués pour répondre ou vérifier la valeur quand il change.  Pour plus d’informations sur ces rappels, consultez [Validation et rappels de propriétés de dépendance](../advanced/dependency-property-callbacks-and-validation.md).

- Définir une méthode <xref:System.Windows.CoerceValueCallback> `CoerceValue`pour le nommé . `CoerceValue` garantit que `Value` est supérieur ou égal à `MinValue` et inférieur ou égal à `MaxValue`.

- Définir une méthode <xref:System.Windows.PropertyChangedCallback>pour `OnValueChanged`le , nommé . `OnValueChanged`crée <xref:System.Windows.RoutedPropertyChangedEventArgs%601> un objet et se `ValueChanged` prépare à élever l’événement routé. Les événements routés sont traités dans la section suivante.

[!code-csharp[UserControlNumericUpDown#DependencyProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDown/CSharp/NumericUpDown.xaml.cs#dependencyproperty)]
[!code-vb[UserControlNumericUpDown#DependencyProperty](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UserControlNumericUpDown/visualbasic/numericupdown.xaml.vb#dependencyproperty)]

Pour plus d’informations, consultez [Propriétés de dépendance personnalisées](../advanced/custom-dependency-properties.md).

### <a name="use-routed-events"></a>Utiliser des événements routés

Tout comme les propriétés de dépendance étendent la notion de propriétés CLR avec des fonctionnalités supplémentaires, les événements acheminés étendent la notion d’événements CLR standard. Quand vous créez un contrôle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], il est également conseillé d’implémenter votre événement en tant qu’événement routé, car un tel événement prend en charge le comportement suivant :

- Vous pouvez gérer les événements sur le parent de plusieurs contrôles. Si un événement est un événement de propagation, un parent unique de l’arborescence d’éléments peut s’abonner à l’événement. Les auteurs d’applications peuvent ensuite utiliser un gestionnaire unique pour répondre à l’événement de plusieurs contrôles. Par exemple, si votre contrôle fait partie <xref:System.Windows.Controls.ListBox> de chaque élément <xref:System.Windows.DataTemplate>dans un (parce qu’il est inclus dans <xref:System.Windows.Controls.ListBox>un ), le développeur d’applications peut définir le gestionnaire d’événement pour l’événement de votre contrôle sur le . Chaque fois que l’événement se produit sur un des contrôles, le gestionnaire d’événements est appelé.

- Les événements acheminés <xref:System.Windows.EventSetter>peuvent être utilisés dans un , qui permet aux développeurs d’applications de spécifier le gestionnaire d’un événement dans un style.

- Les événements acheminés <xref:System.Windows.EventTrigger>peuvent être utilisés dans un , [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]qui est utile pour animer les propriétés en utilisant . Pour plus d’informations, voir [Aperçu animation](../graphics-multimedia/animation-overview.md).

L’exemple suivant montre comment définir un événement routé :

- Définissez <xref:System.Windows.RoutedEvent> un `ValueChangedEvent` identifiant `public` `static` `readonly` nommé comme un champ.

- Enregistrez l’événement acheminé en appelant la <xref:System.Windows.EventManager.RegisterRoutedEvent%2A?displayProperty=nameWithType> méthode. L’exemple spécifie les <xref:System.Windows.EventManager.RegisterRoutedEvent%2A>informations suivantes lorsqu’il appelle :

  - Le nom de l’événement est `ValueChanged`.

  - La stratégie de <xref:System.Windows.RoutingStrategy.Bubble>routage est , ce qui signifie qu’un gestionnaire d’événements sur la source (l’objet qui soulève l’événement) est appelé d’abord, puis les gestionnaires d’événements sur les éléments parents de la source sont appelés successivement, en commençant par le gestionnaire d’événement sur l’élément parent le plus proche.

  - Le type de gestionnaire <xref:System.Windows.RoutedPropertyChangedEventHandler%601>d’événement <xref:System.Decimal> est, construit avec un type.

  - Le type propriétaire de l’événement est `NumericUpDown`.

- Déclarez un événement public nommé `ValueChanged` et incluez des déclarations d’accesseurs d’événement. L’exemple <xref:System.Windows.UIElement.AddHandler%2A> appelle `add` dans la <xref:System.Windows.UIElement.RemoveHandler%2A> déclaration `remove` d’accesseur [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et dans la déclaration de l’accesseur à utiliser les services d’événement.

- Créez une méthode virtuelle protégée nommée `OnValueChanged`, qui déclenche l’événement `ValueChanged`.

[!code-csharp[UserControlNumericUpDown#RoutedEvent](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDown/CSharp/NumericUpDown.xaml.cs#routedevent)]
[!code-vb[UserControlNumericUpDown#RoutedEvent](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UserControlNumericUpDown/visualbasic/numericupdown.xaml.vb#routedevent)]

Pour plus d’informations, consultez [Vue d’ensemble des événements routés](../advanced/routed-events-overview.md) et [Créer un événement routé personnalisé](../advanced/how-to-create-a-custom-routed-event.md).

### <a name="use-binding"></a>Utiliser la liaison

Pour découpler l’interface utilisateur de votre contrôle de sa logique, songez à utiliser la liaison de données. Ceci est particulièrement important si vous définissez <xref:System.Windows.Controls.ControlTemplate>l’apparence de votre contrôle en utilisant un . L’utilisation de la liaison de données permet d’éviter de référencer des parties spécifiques de l’interface utilisateur à partir du code. C’est une bonne idée d’éviter le <xref:System.Windows.Controls.ControlTemplate> référencement des éléments qui <xref:System.Windows.Controls.ControlTemplate> sont <xref:System.Windows.Controls.ControlTemplate> dans le parce que lorsque le code <xref:System.Windows.Controls.ControlTemplate>fait référence aux éléments qui sont dans le et le est changé, l’élément référencé doit être inclus dans le nouveau .

L’exemple suivant <xref:System.Windows.Controls.TextBlock> met `NumericUpDown` à jour le contrôle, lui assignant un nom et faisant référence à la boîte de texte par nom dans le code.

[!code-xaml[UserControlNumericUpDownSimple#UIRefMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDownSimple/CSharp/NumericUpDown.xaml#uirefmarkup)]

[!code-csharp[UserControlNumericUpDownSimple#UIRefCode](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDownSimple/CSharp/NumericUpDown.xaml.cs#uirefcode)]
[!code-vb[UserControlNumericUpDownSimple#UIRefCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UserControlNumericUpDownSimple/VisualBasic/NumericUpDown.xaml.vb#uirefcode)]

L’exemple suivant utilise la liaison pour accomplir la même chose.

[!code-xaml[UserControlNumericUpDown#Binding](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDown/CSharp/NumericUpDown.xaml#binding)]

Pour plus d’informations sur la liaison des données, voir [Aperçu de la liaison des données](../../../desktop-wpf/data/data-binding-overview.md).

### <a name="design-for-designers"></a>Conception pour les concepteurs

Pour recevoir un support pour les contrôles WPF personnalisés dans le WPF Designer for Visual Studio (par exemple, l’édition de propriété avec la fenêtre Propriétés), suivez ces lignes directrices.  Pour plus d’informations sur le développement pour le WPF Designer, voir [Design XAML dans Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio).

#### <a name="dependency-properties"></a>Propriétés de dépendance

Assurez-vous de `get` mettre `set` en œuvre CLR et les accesseurs comme décrit précédemment, dans "Use Dependency Properties." Les concepteurs peuvent utiliser le wrapper pour détecter la présence d’une propriété de dépendance, mais, à l’instar de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et des clients du contrôle, ils ne sont pas tenus d’appeler les accesseurs durant l’obtention ou la définition de la propriété.

#### <a name="attached-properties"></a>Propriétés jointes

Pour implémenter des propriétés jointes sur des contrôles personnalisés, tenez compte des indications suivantes :

- Avoir `public` `static` `readonly` <xref:System.Windows.DependencyProperty> un de la forme *PropertyName* `Property` qui a été la création en utilisant la <xref:System.Windows.DependencyProperty.RegisterAttached%2A> méthode. Le nom de propriété <xref:System.Windows.DependencyProperty.RegisterAttached%2A> qui est passé à doit correspondre *PropertyName*.

- Implémentez une paire de méthodes CLR `public` `static` nommées `Set`*NomPropriété* et `Get`*NomPropriété*. Les deux méthodes devraient <xref:System.Windows.DependencyProperty> accepter une classe dérivée de leur premier argument. La méthode `Set`*NomPropriété* accepte également un argument dont le type correspond au type de données inscrit pour la propriété. La méthode `Get`*NomPropriété* doit retourner une valeur du même type. Si la méthode `Set`*NomPropriété* est manquante, la propriété est marquée en lecture seule.

- `Set`*PropertyName* `Get`et *PropertyName* doivent <xref:System.Windows.DependencyObject.GetValue%2A> s’acheminer directement vers l’objet de dépendance cible, <xref:System.Windows.DependencyObject.SetValue%2A> respectivement. Les concepteurs peuvent accéder à la propriété jointe en l’appelant par le biais du wrapper de méthode ou en effectuant un appel direct à l’objet de dépendance cible.

Pour plus d’informations sur les propriétés jointes, consultez [Vue d’ensemble des propriétés jointes](../advanced/attached-properties-overview.md).

### <a name="define-and-use-shared-resources"></a>Définir et utiliser des ressources partagées

Vous pouvez inclure votre contrôle dans le même assembly que votre application, ou la mettre en package dans un assembly séparé qui peut être utilisé dans plusieurs applications. Pour la plupart, les informations abordées dans cette rubrique sont valables, quelle que soit la méthode que vous utilisez.  Toutefois, il existe une différence notable.  Quand vous placez un contrôle dans le même assembly qu’une application, vous êtes libre d’ajouter des ressources globales au fichier App.xaml. Mais un assemblage qui ne contient <xref:System.Windows.Application> que des contrôles n’a pas d’objet qui lui est associé, de sorte qu’un fichier App.xaml n’est pas disponible.

Quand une application recherche une ressource, elle examine trois niveaux dans l’ordre suivant :

1. Niveau de l’élément.

   Le système commence par l’élément qui référence la ressource, puis passe en revue les ressources du parent logique, et ainsi de suite, jusqu’à atteindre l’élément racine.

2. Niveau de l’application.

   Ressources définies <xref:System.Windows.Application> par l’objet.

3. Niveau du thème.

   Les dictionnaires au niveau du thème sont enregistrés dans un sous-dossier nommé Themes.  Les fichiers contenus dans ce dossier correspondent aux thèmes.  Par exemple, vous pouvez avoir Aero.NormalColor.xaml, Luna.NormalColor.xaml, Royale.NormalColor.xaml, etc.  Vous pouvez également avoir un fichier nommé generic.xaml.  Quand le système recherche une ressource au niveau des thèmes, il la cherche en premier lieu dans le fichier spécifique au thème, puis dans generic.xaml.

Si votre contrôle se trouve dans un assembly distinct de l’application, vous devez placer vos ressources globales au niveau de l’élément ou du thème. Les deux méthodes ont leurs avantages.

#### <a name="defining-resources-at-the-element-level"></a>Définition de ressources au niveau de l’élément

Vous pouvez définir des ressources partagées au niveau de l’élément en créant un dictionnaire de ressources personnalisé et en le fusionnant avec le dictionnaire de ressources de votre contrôle.  Quand vous utilisez cette méthode, vous pouvez donner à votre fichier de ressources le nom de votre choix, et il peut se trouver dans le même dossier que vos contrôles. Les ressources au niveau de l’élément peuvent également utiliser des chaînes simples comme clés. L’exemple suivant <xref:System.Windows.Media.LinearGradientBrush> crée un fichier de ressources nommé Dictionary1.xaml.

[!code-xaml[SharedResources#1](~/samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/Dictionary1.xaml#1)]

Une fois que vous avez défini votre dictionnaire, vous devez le fusionner avec le dictionnaire de ressources de votre contrôle.  Pour cela, utilisez [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ou du code.

L’exemple suivant fusionne un dictionnaire de ressources en [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].

[!code-xaml[SharedResources#2](~/samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/ShapeResizer.xaml#2)]

L’inconvénient de cette <xref:System.Windows.ResourceDictionary> approche est qu’un objet est créé chaque fois que vous le référencez.  Par exemple, si vous avez 10 contrôles personnalisés dans votre bibliothèque et que vous fusionnez les <xref:System.Windows.ResourceDictionary> dictionnaires de ressources partagés pour chaque contrôle en utilisant XAML, vous créez 10 objets identiques.  Vous pouvez éviter cela en créant une classe statique qui <xref:System.Windows.ResourceDictionary>fusionne les ressources dans le code et renvoie le résultat .

L’exemple suivant crée une <xref:System.Windows.ResourceDictionary>classe qui renvoie un partage .

[!code-csharp[SharedResources#3](~/samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/SharedDictionaryManager.cs#3)]

L’exemple suivant fusionne la ressource partagée avec les ressources d’un contrôle personnalisé dans le constructeur du contrôle avant d’appeler `InitializeComponent`.  Parce `SharedDictionaryManager.SharedDictionary` que le est <xref:System.Windows.ResourceDictionary> une propriété statique, le n’est créé qu’une seule fois. Comme le dictionnaire de ressources a été fusionné avant l’appel de `InitializeComponent`, les ressources sont mises à la disposition du contrôle dans son fichier [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].

[!code-csharp[SharedResources#4](~/samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/ShapeResizer.xaml.cs#4)]

#### <a name="defining-resources-at-the-theme-level"></a>Définition de ressources au niveau de l’élément

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vous permet de créer des ressources pour différents thèmes Windows.  En tant qu’auteur du contrôle, vous pouvez définir une ressource pour un thème spécifique pour changer l’apparence de votre contrôle selon le thème utilisé. Par exemple, l’apparition <xref:System.Windows.Controls.Button> d’un thème Windows Classic (le thème par défaut <xref:System.Windows.Controls.Button> pour Windows 2000) diffère d’un <xref:System.Windows.Controls.Button> thème <xref:System.Windows.Controls.ControlTemplate> Windows Luna (le thème par défaut pour Windows XP) parce que les utilisations d’un thème différent pour chaque thème.

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

Le contrôle personnalisé de [base de C ou](https://github.com/dotnet/samples/tree/master/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp) [visual](https://github.com/dotnet/samples/tree/master/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic) NumericUpDown avec l’échantillon `NumericUpDown` de support d’automatisation du thème et de l’interface utilisateur contient deux dictionnaires de ressources pour le contrôle : l’un est en generic.xaml, et l’autre est dans Luna.NormalColor.xaml.

Lorsque vous <xref:System.Windows.Controls.ControlTemplate> mettez un dans l’un des fichiers de dictionnaire de ressources spécifiques <xref:System.Windows.DependencyProperty.OverrideMetadata%28System.Type%2CSystem.Windows.PropertyMetadata%29> au thème, vous devez créer un constructeur statique pour votre contrôle et appeler la méthode sur le <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A>, comme indiqué dans l’exemple suivant.

[!code-csharp[CustomControlNumericUpDownOneProject#StaticConstructor](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDownOneProject/CSharp/NumericUpDown.cs#staticconstructor)]
[!code-vb[CustomControlNumericUpDownOneProject#StaticConstructor](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDownOneProject/visualbasic/numericupdown.vb#staticconstructor)]

##### <a name="defining-and-referencing-keys-for-theme-resources"></a>Définition et référencement de clés pour les ressources de thème

Quand vous définissez une ressource au niveau de l’élément, vous pouvez assigner une chaîne comme clé et accéder à la ressource par le biais de la chaîne. Lorsque vous définissez une ressource au niveau <xref:System.Windows.ComponentResourceKey> du thème, vous devez utiliser une clé.  L’exemple suivant définit une ressource dans generic.xaml.

[!code-xaml[ThemeResourcesControlLibrary#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ThemeResourcesControlLibrary/CS/Themes/generic.xaml#5)]

L’exemple suivant fait référence <xref:System.Windows.ComponentResourceKey> à la ressource en spécifiant la clé.

[!code-xaml[ThemeResourcesControlLibrary#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ThemeResourcesControlLibrary/CS/NumericUpDown.xaml#6)]

##### <a name="specifying-the-location-of-theme-resources"></a>Spécification de l’emplacement des ressources des thèmes

Pour rechercher les ressources relatives à un contrôle, l’application d’hébergement doit savoir quel l’assembly contient des ressources spécifiques au contrôle. Vous pouvez y parvenir <xref:System.Windows.ThemeInfoAttribute> en ajoutant l’assemblage qui contient le contrôle. Le <xref:System.Windows.ThemeInfoAttribute> a <xref:System.Windows.ThemeInfoAttribute.GenericDictionaryLocation%2A> une propriété qui spécifie <xref:System.Windows.ThemeInfoAttribute.ThemeDictionaryLocation%2A> l’emplacement des ressources génériques, et une propriété qui spécifie l’emplacement des ressources thématiques.

L’exemple suivant <xref:System.Windows.ThemeInfoAttribute.GenericDictionaryLocation%2A> <xref:System.Windows.ThemeInfoAttribute.ThemeDictionaryLocation%2A> définit <xref:System.Windows.ResourceDictionaryLocation.SourceAssembly>les propriétés et les propriétés à , pour spécifier que les ressources génériques et thématiques sont dans le même assemblage que le contrôle.

[!code-csharp[CustomControlNumericUpDown#ThemesSection](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/Properties/AssemblyInfo.cs#themessection)]
[!code-vb[CustomControlNumericUpDown#ThemesSection](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/my project/assemblyinfo.vb#themessection)]

## <a name="see-also"></a>Voir aussi

- [Concevoir en XAML dans Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [URI à en-tête pack dans WPF](../app-development/pack-uris-in-wpf.md)
- [Personnalisation des contrôles](control-customization.md)
