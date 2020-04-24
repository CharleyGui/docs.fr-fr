---
title: Propriétés de dépendance personnalisées
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- implementing [WPF], wrappers
- registering properties [WPF]
- properties [WPF], metadata
- metadata [WPF], for properties
- custom dependency properties [WPF]
- properties [WPF], registering
- wrappers [WPF], implementing
- dependency properties [WPF], custom
ms.assetid: e6bfcfac-b10d-4f58-9f77-a864c2a2938f
ms.openlocfilehash: e4117d7add2a34d6d989d9222e7688361cf6b379
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646353"
---
# <a name="custom-dependency-properties"></a>Propriétés de dépendance personnalisées

Cette rubrique décrit les raisons pour lesquelles les développeurs d’applications et les auteurs de composants [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] peuvent souhaiter créer une propriété de dépendance personnalisée, et décrit les étapes d’implémentation ainsi que certaines options d’implémentation susceptibles d’améliorer les performances, l’utilisation ou la souplesse de la propriété.

<a name="prerequisites"></a>

## <a name="prerequisites"></a>Prérequis

Cette rubrique part du principe que vous maîtrisez les propriétés de dépendance du point de vue d’un consommateur de propriétés de dépendance existantes dans les classes [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], et que vous avez lu la rubrique [Vue d’ensemble des propriétés de dépendance](dependency-properties-overview.md). Pour pouvoir suivre les exemples de cette rubrique, vous devez également comprendre [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] et savoir comment écrire des applications [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

<a name="whatis"></a>

## <a name="what-is-a-dependency-property"></a>Qu’est ce qu’une propriété de dépendance ?

Vous pouvez activer ce qui serait autrement une propriété commune de temps d’exécution de langue (CLR) pour soutenir le style, la liaison de données, l’héritage, les animations, et les valeurs par défaut en la mettant en œuvre comme une propriété de dépendance. Les propriétés de dépendance [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sont des propriétés qui <xref:System.Windows.DependencyProperty.RegisterReadOnly%2A>sont enregistrées auprès <xref:System.Windows.DependencyProperty> du système de propriété en appelant la <xref:System.Windows.DependencyProperty.Register%2A> méthode (ou), et qui sont soutenus par un champ d’identification. Les propriétés de <xref:System.Windows.DependencyObject> dépendance ne <xref:System.Windows.DependencyObject> peuvent être [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] utilisées que par types, mais [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sont assez élevées dans la hiérarchie de classe, ainsi la majorité des classes disponibles dans peut soutenir des propriétés de dépendance. Pour plus d’informations sur les propriétés de dépendance et certaines des terminologies et des conventions utilisées pour les décrire dans ce SDK, voir [Dependency Properties Overview](dependency-properties-overview.md).

<a name="example_dp"></a>

## <a name="examples-of-dependency-properties"></a>Exemples de propriétés de dépendance

Des exemples de propriétés de dépendance qui sont mises en œuvre sur [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] les classes incluent la <xref:System.Windows.Controls.Control.Background%2A> propriété, la <xref:System.Windows.FrameworkElement.Width%2A> propriété, et la <xref:System.Windows.Controls.TextBox.Text%2A> propriété, parmi beaucoup d’autres. Chaque propriété de dépendance exposée par une classe <xref:System.Windows.DependencyProperty> a un champ statique public correspondant de type exposé sur cette même classe. Il s’agit de l’identificateur de la propriété de dépendance. L’identificateur est nommé à l’aide d’une convention : le nom de la propriété de dépendance, auquel est ajoutée la chaîne `Property`. Par exemple, <xref:System.Windows.DependencyProperty> le champ <xref:System.Windows.Controls.Control.Background%2A> d’identification correspondant pour la propriété est <xref:System.Windows.Controls.Control.BackgroundProperty>. L’identifiant stocke l’information sur la propriété de dépendance telle qu’elle a été enregistrée, et l’identifiant est ensuite utilisé plus tard pour d’autres opérations impliquant la propriété de dépendance, comme l’appel <xref:System.Windows.DependencyObject.SetValue%2A>.

Comme mentionné dans [l’aperçu des propriétés de dépendance](dependency-properties-overview.md), toutes les propriétés de dépendance dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] (sauf la plupart des propriétés attachées) sont également des propriétés CLR en raison de la mise en œuvre "wrapper". Par conséquent, à partir du code, vous pouvez obtenir ou définir des propriétés de dépendance en appelant les accesseurs CLR qui définissent les emballages de la même manière que vous utiliseriez d’autres propriétés CLR. En tant que consommateur de propriétés de <xref:System.Windows.DependencyObject> <xref:System.Windows.DependencyObject.GetValue%2A> dépendance <xref:System.Windows.DependencyObject.SetValue%2A>établies, vous n’utilisez généralement pas les méthodes et, qui sont le point de connexion au système de propriété sous-jacent. Au contraire, la mise en œuvre <xref:System.Windows.DependencyObject.GetValue%2A> <xref:System.Windows.DependencyObject.SetValue%2A> existante `get` des `set` propriétés CLR aura déjà appelé et dans les implémentations et l’emballage de la propriété, en utilisant le champ d’identification de manière appropriée. Si vous implémentez une propriété de dépendance personnalisée vous-même, vous définirez le wrapper de la même façon.

<a name="backing_with_dp"></a>

## <a name="when-should-you-implement-a-dependency-property"></a>Quand faut-il implémenter une propriété de dépendance ?

Lorsque vous implémentez une propriété sur une <xref:System.Windows.DependencyObject>classe, tant que votre classe <xref:System.Windows.DependencyProperty> dérive de, vous avez la possibilité de soutenir votre propriété avec un identifiant et donc d’en faire une propriété de dépendance. Faire de votre propriété une propriété de dépendance n’est pas toujours nécessaire ni approprié. Cela dépend des besoins de votre scénario. Parfois, la technique classique qui consiste à stocker la propriété dans un champ privé est adéquate. Toutefois, vous devez implémenter votre propriété en tant que propriété de dépendance chaque fois que vous souhaitez qu’elle prenne en charge une ou plusieurs des fonctionnalités [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] suivantes :

- Vous souhaitez que votre propriété puisse être définie dans un style. Pour plus d’informations, consultez [Application d’un style et création de modèles](../../../desktop-wpf/fundamentals/styles-templates-overview.md).

- Vous souhaitez que votre propriété prenne en charge la liaison de données. Pour plus d’informations sur les propriétés de dépendance de liaison de données, consultez [Lier les propriétés de deux contrôles](../data/how-to-bind-the-properties-of-two-controls.md).

- Vous souhaitez que votre propriété puisse être définie avec une référence à une ressource dynamique. Pour plus d’informations, consultez [Ressources XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md).

- Vous voulez hériter automatiquement une valeur de propriété d’un élément parent dans l’arborescence d’éléments. Dans ce cas, <xref:System.Windows.DependencyProperty.RegisterAttached%2A> inscrivez-vous avec la méthode, même si vous créez également un emballage de propriété pour l’accès CLR. Pour plus d’informations, consultez [Héritage de valeur de propriété](property-value-inheritance.md).

- Vous souhaitez que votre propriété puisse être animée. Pour plus d’informations, voir [Aperçu animation](../graphics-multimedia/animation-overview.md).

- Vous souhaitez que le système de propriétés signale quand la valeur précédente de la propriété a été modifiée par des actions effectuées par le système de propriétés, l’environnement ou l’utilisateur, ou par la lecture et l’utilisation de styles. À l’aide des métadonnées de propriété, votre propriété peut spécifier une méthode de rappel qui sera appelée chaque fois que le système de propriétés détermine que la valeur de propriété a été modifiée de manière certaine. Le forçage de valeur de propriété est un concept connexe. Pour plus d’informations, consultez [Validation et rappels de propriétés de dépendance](dependency-property-callbacks-and-validation.md).

- Vous souhaitez utiliser des conventions de métadonnées établies qui sont également utilisées par des processus [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], par exemple signaler si la modification d’une valeur de propriété exige que le système de disposition recompose les visuels d’un élément. Ou vous souhaitez pouvoir utiliser des substitutions de métadonnées pour que les classes dérivées puissent changer des caractéristiques basées sur les métadonnées, telles que la valeur par défaut.

- Vous voulez que les propriétés d’un contrôle personnalisé reçoivent le support Visual Studio WPF Designer, comme l’édition de fenêtre **Properties.** Pour plus d’informations, consultez [Vue d’ensemble de la création de contrôles](../controls/control-authoring-overview.md).

Quand vous examinez ces scénarios, vous devez également réfléchir si vous pouvez accomplir votre scénario en substituant les métadonnées d’une propriété de dépendance existante, plutôt qu’en implémentant une toute nouvelle propriété. Le fait qu’une substitution de métadonnées soit pratique ou non dépend de votre scénario et de sa ressemblance avec l’implémentation dans les classes et les propriétés de dépendance [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] existantes. Pour plus d’informations sur la substitution de métadonnées dans les propriétés existantes, consultez [Métadonnées de propriété de dépendance](dependency-property-metadata.md).

<a name="checklist"></a>

## <a name="checklist-for-defining-a-dependency-property"></a>Liste de vérification pour la définition d’une propriété de dépendance

La définition d’une propriété de dépendance implique quatre concepts distincts. Ces concepts ne sont pas des étapes procédurales nécessairement strictes, car certaines d’entre elles finissent par être combinées sur des lignes de code uniques dans l’implémentation :

- (Facultatif) Créez des métadonnées de propriété pour la propriété de dépendance.

- Inscrivez le nom de propriété auprès du système de propriétés, en spécifiant un type de propriétaire et le type de la valeur de propriété. Spécifiez également les métadonnées de propriété, si elles sont utilisées.

- Définissez <xref:System.Windows.DependencyProperty> un `public` `static` `readonly` identifiant comme un champ sur le type de propriétaire.

- Décrivez une propriété CLR "wrapper" dont le nom correspond au nom de la propriété de dépendance. Implémentez la propriété `get` et `set` les accesseurs CLR pour vous connecter à la propriété de dépendance qui la soutient.

<a name="registering"></a>

### <a name="registering-the-property-with-the-property-system"></a>Inscription de la propriété auprès du système de propriétés

Pour que votre propriété soit une propriété de dépendance, vous devez l’inscrire dans une table gérée par le système de propriétés et lui donner un identificateur unique utilisé comme qualificateur pour les opérations de système de propriétés ultérieures. Ces opérations peuvent être des opérations internes, ou votre propre code appelant les API système de propriété. Pour enregistrer la propriété, <xref:System.Windows.DependencyProperty.Register%2A> vous appelez la méthode dans le corps de votre classe (à l’intérieur de la classe, mais en dehors de toute définition des membres). Le champ d’identification <xref:System.Windows.DependencyProperty.Register%2A> est également fourni par l’appel de méthode, comme valeur de retour. La raison <xref:System.Windows.DependencyProperty.Register%2A> pour laquelle l’appel est fait en dehors des autres définitions des membres est parce que vous utilisez cette valeur de retour pour attribuer et créer un `public` `static` `readonly` champ de type <xref:System.Windows.DependencyProperty> dans le cadre de votre classe. Ce champ devient l’identificateur de votre propriété de dépendance.

[!code-csharp[WPFAquariumSln#RegisterAG](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#registerag)]
[!code-vb[WPFAquariumSln#RegisterAG](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#registerag)]

<a name="nameconventions"></a>

### <a name="dependency-property-name-conventions"></a>Conventions pour les noms des propriétés de dépendance

Il existe des conventions d’affectation de noms établies pour les propriétés de dépendance. Vous devez les respecter dans toutes les circonstances, sauf les plus exceptionnelles.

La propriété de dépendance elle-même aura un nom de base, "AquariumGraphic" <xref:System.Windows.DependencyProperty.Register%2A>comme dans cet exemple, qui est donné comme le premier paramètre de . Ce nom doit être unique dans chaque type d’inscription. Les propriétés de dépendance héritées par l’intermédiaire des types de base sont considérées comme faisant déjà partie du type d’inscription ; les noms des propriétés héritées ne peuvent pas être réinscrits. Il existe toutefois une technique pour ajouter une classe en tant que propriétaire d’une propriété de dépendance, même quand celle-ci n’est pas héritée. Pour plus d’informations, consultez [Métadonnées de propriété de dépendance](dependency-property-metadata.md).

Quand vous créez le champ d’identificateur, affectez-lui le même nom que la propriété que vous avez inscrite, plus le suffixe `Property`. Ce champ est votre identifiant pour la propriété de dépendance, <xref:System.Windows.DependencyObject.SetValue%2A> et <xref:System.Windows.DependencyObject.GetValue%2A> il sera utilisé plus tard comme une entrée pour les emballages et les appels que vous allez faire [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dans les emballages, par tout autre accès au code de la propriété par votre propre code, par n’importe quel accès de code externe que vous autorisez, par le système de propriété, et potentiellement par les processeurs.

> [!NOTE]
> La définition de la propriété de dépendance dans le corps de la classe est l’implémentation type, mais vous pouvez aussi définir une propriété de dépendance dans le constructeur statique de classe. Cette approche peut être plus logique si vous avez besoin de plus d’une ligne de code pour initialiser la propriété de dépendance.

<a name="wrapper1"></a>

### <a name="implementing-the-wrapper"></a>Implémentation du « Wrapper »

Votre mise en <xref:System.Windows.DependencyObject.GetValue%2A> œuvre d’emballage devrait faire appel à la `get` mise en œuvre, et <xref:System.Windows.DependencyObject.SetValue%2A> dans la `set` mise en œuvre (l’appel d’enregistrement d’origine et le champ sont montrés ici aussi pour plus de clarté).

Dans toutes les circonstances sauf exceptionnelles, vos <xref:System.Windows.DependencyObject.GetValue%2A> <xref:System.Windows.DependencyObject.SetValue%2A> implémentations d’emballage ne doivent effectuer que les actions et les actions, respectivement. La raison est expliquée dans la rubrique [Propriétés de dépendance et chargement XAML](xaml-loading-and-dependency-properties.md).

Toutes les propriétés de dépendance publiques existantes fournies dans les classes [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] utilisent ce modèle d’implémentation de wrapper simple. La plus grande partie de la complexité du fonctionnement des métadonnées de propriété est un comportement inhérent du système de propriétés ou est implémentée via d’autres concepts, tels que le forçage de type ou les rappels de changement de propriété par l’intermédiaire de métadonnées de propriété.

[!code-csharp[WPFAquariumSln#AGWithWrapper](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#agwithwrapper)]
[!code-vb[WPFAquariumSln#AGWithWrapper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#agwithwrapper)]

Encore une fois, par convention, le nom de la propriété de l’emballage <xref:System.Windows.DependencyProperty.Register%2A> doit être le même que le nom choisi et donné comme premier paramètre de l’appel qui a enregistré la propriété. Si votre propriété ne respecte pas la convention, toutes les utilisations possibles ne sont pas nécessairement désactivées, mais vous rencontrerez plusieurs problèmes :

- Certains aspects des styles et modèles ne fonctionneront pas.

- La plupart des outils et concepteurs doivent s’appuyer sur les conventions d’affectation de noms pour sérialiser correctement [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], ou pour fournir l’assistance d’environnement de concepteur au niveau de chaque propriété.

- La mise en [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] œuvre actuelle du chargeur contourne entièrement les emballages et repose sur la convention de nommage lors du traitement des valeurs d’attribut. Pour plus d’informations, consultez [Propriétés de dépendance et chargement XAML](xaml-loading-and-dependency-properties.md).

<a name="metadata"></a>

### <a name="property-metadata-for-a-new-dependency-property"></a>Métadonnées de propriété pour une nouvelle propriété de dépendance

Quand vous inscrivez une propriété de dépendance, l’inscription dans le système de propriétés crée un objet de métadonnées qui stocke les caractéristiques de la propriété. Beaucoup de ces caractéristiques ont des défauts qui sont définis si la propriété est enregistrée avec les signatures simples de <xref:System.Windows.DependencyProperty.Register%2A>. D’autres <xref:System.Windows.DependencyProperty.Register%2A> signatures vous permettent de spécifier les métadonnées que vous voulez lorsque vous enregistrez la propriété. Les métadonnées les plus courantes pour les propriétés de dépendance consistent à leur attribuer une valeur par défaut qui est appliquée sur les nouvelles instances qui utilisent la propriété.

Si vous créez une propriété de dépendance qui <xref:System.Windows.FrameworkElement>existe sur une classe dérivée <xref:System.Windows.FrameworkPropertyMetadata> de , <xref:System.Windows.PropertyMetadata> vous pouvez utiliser la classe de métadonnées plus spécialisées plutôt que la classe de base. Le constructeur de <xref:System.Windows.FrameworkPropertyMetadata> la classe a plusieurs signatures où vous pouvez spécifier diverses caractéristiques de métadonnées en combinaison. Si vous souhaitez spécifier uniquement la valeur par défaut, utilisez la signature qui prend un seul paramètre de type <xref:System.Object>. Passez ce paramètre d’objet comme valeur par défaut spécifique à votre propriété (la valeur par défaut fournie doit être le type que vous avez fourni comme `propertyType` paramètre dans l’appel). <xref:System.Windows.DependencyProperty.Register%2A>

Pour <xref:System.Windows.FrameworkPropertyMetadata>, vous pouvez également spécifier des indicateurs d’option de métadonnées pour votre propriété. Ces indicateurs sont convertis en propriétés discrètes dans les métadonnées de propriété après l’inscription, et sont utilisés pour spécifier certaines conditions à d’autres processus, tels que le moteur de disposition.

#### <a name="setting-appropriate-metadata-flags"></a>Définition des indicateurs de métadonnées appropriés

- Si votre propriété (ou change de [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]valeur) affecte le , et en particulier affecte la façon dont le système <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsMeasure>de <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsArrange> <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsRender>mise en page devrait tailler ou rendre votre élément dans une page, définissez un ou plusieurs des drapeaux suivants: , .

  - <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsMeasure>indique qu’un changement à cette [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] propriété nécessite une modification du rendu lorsque l’objet contenant pourrait nécessiter plus ou moins d’espace au sein du parent. Par exemple, cet indicateur doit être défini pour une propriété « Width ».

  - <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsArrange>indique qu’un changement à cette [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] propriété nécessite un changement à rendu qui ne nécessite généralement pas un changement dans l’espace dédié, mais indique que le positionnement dans l’espace a changé. Par exemple, cet indicateur doit être défini pour une propriété « Alignment ».

  - <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsRender>indique qu’un autre changement s’est produit qui n’affectera pas la disposition et la mesure, mais nécessite un autre rendu. Un exemple serait une propriété qui change une couleur d’un élément existant, telle que « Background ».

  - Ces indicateurs sont souvent utilisés comme protocole dans les métadonnées pour vos propres implémentations de substitution de rappels de disposition ou de système de propriétés. Par exemple, vous <xref:System.Windows.DependencyObject.OnPropertyChanged%2A> pourriez avoir un <xref:System.Windows.UIElement.InvalidateArrange%2A> rappel qui appellera si une <xref:System.Windows.FrameworkPropertyMetadata.AffectsArrange%2A> propriété `true` de l’instance signale un changement de valeur et a comme dans ses métadonnées.

- Certaines propriétés peuvent affecter les caractéristiques de rendu de l’élément parent conteneur, au-delà des modifications de taille requise mentionnées ci-dessus. Un exemple <xref:System.Windows.Documents.Paragraph.MinOrphanLines%2A> est la propriété utilisée dans le modèle de document de débit, où les modifications apportées à cette propriété peuvent modifier le rendu global du document de débit qui contient le paragraphe. Utilisez <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsParentArrange> <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsParentMeasure> ou identifiez des cas similaires dans vos propres propriétés.

- Par défaut, les propriétés de dépendance prennent en charge la liaison de données. Vous pouvez désactiver délibérément la liaison de données, dans les cas où il n’existe aucun scénario réaliste pour elle, ou quand les performances de liaison de données pour un objet volumineux sont reconnues comme étant un problème.

- Par défaut, <xref:System.Windows.Data.Binding.Mode%2A> la liaison de <xref:System.Windows.Data.BindingMode.OneWay>données pour les propriétés de dépendance est par défaut . Vous pouvez toujours modifier <xref:System.Windows.Data.BindingMode.TwoWay> la liaison pour être par instance contraignante; pour plus de détails, voir [Spécifier la direction de la liaison](../data/how-to-specify-the-direction-of-the-binding.md). Mais en tant qu’auteur de propriété de <xref:System.Windows.Data.BindingMode.TwoWay> dépendance, vous pouvez choisir de faire le mode de liaison d’utilisation de propriété par défaut. Un exemple d’une <xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A?displayProperty=nameWithType>propriété de dépendance existante est ; le scénario de cette <xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A> propriété est que la <xref:System.Windows.Controls.MenuItem> logique de réglage et le compositing d’interagir avec le style de thème par défaut. La <xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A> logique de propriété utilise des données liant nativement pour maintenir l’état de la propriété conformément à d’autres propriétés d’état et les appels de méthode. Un autre exemple <xref:System.Windows.Data.BindingMode.TwoWay> de propriété <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType>qui lie par défaut est .

- Vous pouvez également activer l’héritage de <xref:System.Windows.FrameworkPropertyMetadataOptions.Inherits> propriété dans une propriété de dépendance personnalisée en fixant le drapeau. L’héritage de propriété est utile pour un scénario où des éléments parents et des éléments enfants ont une propriété en commun, et où il est logique que les éléments enfants aient la même valeur de propriété que le parent. Un exemple de <xref:System.Windows.FrameworkElement.DataContext%2A>propriété héréditaire est , qui est utilisé pour les opérations de liaison pour permettre l’important scénario de master-détail pour la présentation des données. En <xref:System.Windows.FrameworkElement.DataContext%2A> rendant héréditaire, tous les éléments pour enfants héritent également de ce contexte de données. En raison de l’héritage de valeur de propriété, vous pouvez spécifier un contexte de données à la racine de la page ou de l’application, et vous n’avez pas besoin de le respécifier pour les liaisons dans tous les éléments enfants possibles. <xref:System.Windows.FrameworkElement.DataContext%2A>est également un bon exemple pour illustrer que l’héritage l’emporte sur la valeur par défaut, mais il peut toujours être fixé localement sur n’importe quel élément enfant particulier; pour plus de détails, voir [Utilisez le modèle Master-Detail avec données hiérarchiques](../data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md). L’héritage de valeur de propriété peut avoir un impact sur les performances, et doit donc être utilisé avec modération. Pour plus d’informations, consultez [Héritage de la valeur de propriété](property-value-inheritance.md).

- Réglez le <xref:System.Windows.FrameworkPropertyMetadataOptions.Journal> drapeau pour indiquer si votre propriété de dépendance doit être détectée ou utilisée par les services de journalage de navigation. Un exemple <xref:System.Windows.Controls.Primitives.Selector.SelectedIndex%2A> est la propriété; tout élément sélectionné dans un contrôle de sélection doit être persistant lorsque l’historique de la revue est navigué.

<a name="RODP"></a>

## <a name="read-only-dependency-properties"></a>Propriétés de dépendance en lecture seule

Vous pouvez définir une propriété de dépendance en lecture seule. Toutefois, les scénarios pour lesquels vous pourriez définir la propriété en lecture seule sont quelque peu différents, tout comme la procédure pour les inscrire auprès du système de propriétés et exposer l’identificateur. Pour plus d’informations, consultez [Propriétés de dépendance en lecture seule](read-only-dependency-properties.md).

<a name="CTDP"></a>

## <a name="collection-type-dependency-properties"></a>Propriétés de dépendance de type collection

Pour les propriétés de dépendance de type collection, vous devrez prendre en compte certains autres aspects relatifs à l’implémentation. Pour plus d’informations, consultez [Propriétés de dépendance de type collection](collection-type-dependency-properties.md).

<a name="SecurityC"></a>

## <a name="dependency-property-security-considerations"></a>Considérations relatives à la sécurité des propriétés de dépendance

Les propriétés de dépendance doivent être déclarées en tant que propriétés publiques. Les champs d’identificateur de propriété de dépendance doivent être déclarés en tant que champs statiques publics. Même si vous tentez de déclarer d’autres niveaux d’accès (tels que protégés), une propriété de dépendance peut toujours être consultée par l’identifiant en combinaison avec le système de propriété API. Même un champ d’identification protégé est potentiellement accessible en raison de la déclaration des <xref:System.Windows.LocalValueEnumerator>métadonnées ou de la détermination de la valeur API qui font partie du système de propriété, tels que . Pour plus d’informations, consultez [Sécurité des propriétés de dépendance](dependency-property-security.md).

<a name="DPCtor"></a>

## <a name="dependency-properties-and-class-constructors"></a>Propriétés de dépendance et constructeurs de classe

Il existe un principe fondamental dans la programmation de code managé (souvent appliqué par des outils d’analyse de code tels que FxCop) selon lequel les constructeurs de classe ne doivent pas appeler de méthodes virtuelles. Cela est dû au fait que les constructeurs peuvent être appelés en tant qu’initialisation de base d’un constructeur de classe dérivée, et l’entrée dans la méthode virtuelle par l’intermédiaire du constructeur peut se produire à un état d’initialisation incomplet de l’instance d’objet en cours de construction. Lorsque vous dérivez de n’importe quelle classe qui dérive déjà de <xref:System.Windows.DependencyObject>, vous devez être conscient que le système de propriété lui-même appelle et expose les méthodes virtuelles en interne. Ces méthodes virtuelles font partie des services du système de propriétés [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. La substitution des méthodes permet aux classes dérivées de participer à la détermination de valeur. Pour éviter les problèmes potentiels liés à l’initialisation au moment de l’exécution, vous ne devez pas définir de valeur de propriété de dépendance dans des constructeurs de classes, sauf si vous respectez un modèle de constructeur très spécifique. Pour plus d’informations, consultez [Modèles de constructeur sécurisé pour DependencyObjects](safe-constructor-patterns-for-dependencyobjects.md).

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des propriétés de dépendance](dependency-properties-overview.md)
- [Métadonnées de propriété de dépendance](dependency-property-metadata.md)
- [Vue d’ensemble de la création de contrôles](../controls/control-authoring-overview.md)
- [Propriétés de dépendance de type collection](collection-type-dependency-properties.md)
- [Sécurité de propriété de dépendance](dependency-property-security.md)
- [Propriétés de dépendance et chargement XAML](xaml-loading-and-dependency-properties.md)
- [Modèles de constructeur sécurisé pour DependencyObjects](safe-constructor-patterns-for-dependencyobjects.md)
