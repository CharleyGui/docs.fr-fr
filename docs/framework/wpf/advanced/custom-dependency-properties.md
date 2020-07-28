---
title: Propriétés de dépendance personnalisées
description: Découvrez les étapes à suivre pour implémenter une propriété dans Windows Presentation Foundation, ainsi que les options permettant d’améliorer les performances, la facilité d’utilisation ou la polyvalence de la propriété.
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
ms.openlocfilehash: b082340afb8b1a814fc5923126aa58183d43bc01
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168148"
---
# <a name="custom-dependency-properties"></a>Propriétés de dépendance personnalisées

Cette rubrique décrit les raisons pour lesquelles les développeurs d’applications et les auteurs de composants [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] peuvent souhaiter créer une propriété de dépendance personnalisée, et décrit les étapes d’implémentation ainsi que certaines options d’implémentation susceptibles d’améliorer les performances, l’utilisation ou la souplesse de la propriété.

<a name="prerequisites"></a>

## <a name="prerequisites"></a>Prérequis

Cette rubrique part du principe que vous maîtrisez les propriétés de dépendance du point de vue d’un consommateur de propriétés de dépendance existantes dans les classes [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], et que vous avez lu la rubrique [Vue d’ensemble des propriétés de dépendance](dependency-properties-overview.md). Pour pouvoir suivre les exemples de cette rubrique, vous devez également comprendre [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] et savoir comment écrire des applications [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

<a name="whatis"></a>

## <a name="what-is-a-dependency-property"></a>Qu’est ce qu’une propriété de dépendance ?

Vous pouvez activer ce qui serait autrement une propriété common language runtime (CLR) pour prendre en charge les styles, la liaison de données, l’héritage, les animations et les valeurs par défaut en les implémentant en tant que propriété de dépendance. Les propriétés de dépendance sont des propriétés inscrites auprès du [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] système de propriétés en appelant la <xref:System.Windows.DependencyProperty.Register%2A> méthode (ou <xref:System.Windows.DependencyProperty.RegisterReadOnly%2A> ) et qui sont sauvegardées par un <xref:System.Windows.DependencyProperty> champ d’identificateur. Les propriétés de dépendance peuvent être utilisées uniquement par <xref:System.Windows.DependencyObject> les types, mais elles <xref:System.Windows.DependencyObject> sont très élevées dans la [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hiérarchie de classes, de sorte que la majorité des classes disponibles dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] peuvent prendre en charge des propriétés de dépendance. Pour plus d’informations sur les propriétés de dépendance et sur la terminologie et les conventions utilisées pour les décrire dans ce kit de développement logiciel (SDK), consultez [vue d’ensemble des propriétés de dépendance](dependency-properties-overview.md).

<a name="example_dp"></a>

## <a name="examples-of-dependency-properties"></a>Exemples de propriétés de dépendance

Les exemples de propriétés de dépendance implémentées sur [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] les classes incluent la <xref:System.Windows.Controls.Control.Background%2A> propriété, la <xref:System.Windows.FrameworkElement.Width%2A> propriété et la <xref:System.Windows.Controls.TextBox.Text%2A> propriété, entre autres. Chaque propriété de dépendance exposée par une classe a un champ statique public correspondant de type <xref:System.Windows.DependencyProperty> exposé sur cette même classe. Il s’agit de l’identificateur de la propriété de dépendance. L’identificateur est nommé à l’aide d’une convention : le nom de la propriété de dépendance, auquel est ajoutée la chaîne `Property`. Par exemple, le <xref:System.Windows.DependencyProperty> champ d’identificateur correspondant pour la <xref:System.Windows.Controls.Control.Background%2A> propriété est <xref:System.Windows.Controls.Control.BackgroundProperty> . L’identificateur stocke les informations sur la propriété de dépendance telle qu’elle a été inscrite, et l’identificateur est ensuite utilisé ultérieurement pour d’autres opérations impliquant la propriété de dépendance, telles que l’appel de <xref:System.Windows.DependencyObject.SetValue%2A> .

Comme mentionné dans la [vue d’ensemble des propriétés de dépendance](dependency-properties-overview.md), toutes les propriétés de dépendance dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] (à l’exception de la plupart des propriétés jointes) sont également des propriétés CLR en raison de l’implémentation de « wrapper ». Par conséquent, à partir du code, vous pouvez récupérer ou définir des propriétés de dépendance en appelant des accesseurs CLR qui définissent les wrappers de la même manière que vous utilisez d’autres propriétés CLR. En tant que consommateur de propriétés de dépendance établies, vous n’utilisez généralement pas les <xref:System.Windows.DependencyObject> méthodes <xref:System.Windows.DependencyObject.GetValue%2A> et <xref:System.Windows.DependencyObject.SetValue%2A> , qui sont le point de connexion au système de propriétés sous-jacent. Au lieu de cela, l’implémentation existante des propriétés CLR aura déjà appelé <xref:System.Windows.DependencyObject.GetValue%2A> et <xref:System.Windows.DependencyObject.SetValue%2A> dans `get` les `set` implémentations de wrapper et de la propriété, en utilisant le champ d’identificateur de manière appropriée. Si vous implémentez une propriété de dépendance personnalisée vous-même, vous définirez le wrapper de la même façon.

<a name="backing_with_dp"></a>

## <a name="when-should-you-implement-a-dependency-property"></a>Quand faut-il implémenter une propriété de dépendance ?

Lorsque vous implémentez une propriété sur une classe, tant que la classe dérive de <xref:System.Windows.DependencyObject> , vous avez la possibilité de sauvegarder votre propriété avec un <xref:System.Windows.DependencyProperty> identificateur et de faire de ce fait une propriété de dépendance. Faire de votre propriété une propriété de dépendance n’est pas toujours nécessaire ni approprié. Cela dépend des besoins de votre scénario. Parfois, la technique classique qui consiste à stocker la propriété dans un champ privé est adéquate. Toutefois, vous devez implémenter votre propriété en tant que propriété de dépendance chaque fois que vous souhaitez qu’elle prenne en charge une ou plusieurs des fonctionnalités [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] suivantes :

- Vous souhaitez que votre propriété puisse être définie dans un style. Pour plus d’informations, consultez [Application d’un style et création de modèles](../../../desktop-wpf/fundamentals/styles-templates-overview.md).

- Vous souhaitez que votre propriété prenne en charge la liaison de données. Pour plus d’informations sur les propriétés de dépendance de liaison de données, consultez [Lier les propriétés de deux contrôles](../data/how-to-bind-the-properties-of-two-controls.md).

- Vous souhaitez que votre propriété puisse être définie avec une référence à une ressource dynamique. Pour plus d’informations, consultez [Ressources XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md).

- Vous voulez hériter automatiquement une valeur de propriété d’un élément parent dans l’arborescence d’éléments. Dans ce cas, inscrivez-vous à la <xref:System.Windows.DependencyProperty.RegisterAttached%2A> méthode, même si vous créez également un wrapper de propriété pour l’accès CLR. Pour plus d’informations, consultez [Héritage de valeur de propriété](property-value-inheritance.md).

- Vous souhaitez que votre propriété puisse être animée. Pour plus d’informations, consultez [vue d’ensemble](../graphics-multimedia/animation-overview.md)de l’animation.

- Vous souhaitez que le système de propriétés signale quand la valeur précédente de la propriété a été modifiée par des actions effectuées par le système de propriétés, l’environnement ou l’utilisateur, ou par la lecture et l’utilisation de styles. À l’aide des métadonnées de propriété, votre propriété peut spécifier une méthode de rappel qui sera appelée chaque fois que le système de propriétés détermine que la valeur de propriété a été modifiée de manière certaine. Le forçage de valeur de propriété est un concept connexe. Pour plus d’informations, consultez [Validation et rappels de propriétés de dépendance](dependency-property-callbacks-and-validation.md).

- Vous souhaitez utiliser des conventions de métadonnées établies qui sont également utilisées par des processus [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], par exemple signaler si la modification d’une valeur de propriété exige que le système de disposition recompose les visuels d’un élément. Ou vous souhaitez pouvoir utiliser des substitutions de métadonnées pour que les classes dérivées puissent changer des caractéristiques basées sur les métadonnées, telles que la valeur par défaut.

- Vous souhaitez que les propriétés d’un contrôle personnalisé reçoivent la prise en charge du Concepteur WPF Visual Studio, par exemple la modification de la fenêtre **Propriétés** . Pour plus d’informations, consultez [Vue d’ensemble de la création de contrôles](../controls/control-authoring-overview.md).

Quand vous examinez ces scénarios, vous devez également réfléchir si vous pouvez accomplir votre scénario en substituant les métadonnées d’une propriété de dépendance existante, plutôt qu’en implémentant une toute nouvelle propriété. Le fait qu’une substitution de métadonnées soit pratique ou non dépend de votre scénario et de sa ressemblance avec l’implémentation dans les classes et les propriétés de dépendance [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] existantes. Pour plus d’informations sur la substitution de métadonnées dans les propriétés existantes, consultez [Métadonnées de propriété de dépendance](dependency-property-metadata.md).

<a name="checklist"></a>

## <a name="checklist-for-defining-a-dependency-property"></a>Liste de vérification pour la définition d’une propriété de dépendance

La définition d’une propriété de dépendance implique quatre concepts distincts. Ces concepts ne sont pas des étapes procédurales nécessairement strictes, car certaines d’entre elles finissent par être combinées sur des lignes de code uniques dans l’implémentation :

- (Facultatif) Créez des métadonnées de propriété pour la propriété de dépendance.

- Inscrivez le nom de propriété auprès du système de propriétés, en spécifiant un type de propriétaire et le type de la valeur de propriété. Spécifiez également les métadonnées de propriété, si elles sont utilisées.

- Définissez un <xref:System.Windows.DependencyProperty> identificateur en tant que `public` `static` `readonly` champ sur le type de propriétaire.

- Définissez une propriété « wrapper » CLR dont le nom correspond au nom de la propriété de dépendance. Implémentez les accesseurs et de la propriété « wrapper » CLR `get` `set` pour vous connecter avec la propriété de dépendance qui le stocke.

<a name="registering"></a>

### <a name="registering-the-property-with-the-property-system"></a>Inscription de la propriété auprès du système de propriétés

Pour que votre propriété soit une propriété de dépendance, vous devez l’inscrire dans une table gérée par le système de propriétés et lui donner un identificateur unique utilisé comme qualificateur pour les opérations de système de propriétés ultérieures. Ces opérations peuvent être des opérations internes ou votre propre code appelant des API du système de propriétés. Pour inscrire la propriété, vous appelez la <xref:System.Windows.DependencyProperty.Register%2A> méthode dans le corps de votre classe (à l’intérieur de la classe, mais en dehors de toutes les définitions de membre). Le champ d’identificateur est également fourni par l' <xref:System.Windows.DependencyProperty.Register%2A> appel de méthode, comme valeur de retour. La raison pour laquelle l' <xref:System.Windows.DependencyProperty.Register%2A> appel est effectué en dehors d’autres définitions de membres est que vous utilisez cette valeur de retour pour assigner et créer un `public` `static` `readonly` champ de type dans <xref:System.Windows.DependencyProperty> le cadre de votre classe. Ce champ devient l’identificateur de votre propriété de dépendance.

[!code-csharp[WPFAquariumSln#RegisterAG](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#registerag)]
[!code-vb[WPFAquariumSln#RegisterAG](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#registerag)]

<a name="nameconventions"></a>

### <a name="dependency-property-name-conventions"></a>Conventions pour les noms des propriétés de dépendance

Il existe des conventions d’affectation de noms établies pour les propriétés de dépendance. Vous devez les respecter dans toutes les circonstances, sauf les plus exceptionnelles.

La propriété de dépendance elle-même aura un nom de base, « AquariumGraphic », comme dans cet exemple, qui est donné comme premier paramètre de <xref:System.Windows.DependencyProperty.Register%2A> . Ce nom doit être unique dans chaque type d’inscription. Les propriétés de dépendance héritées par l’intermédiaire des types de base sont considérées comme faisant déjà partie du type d’inscription ; les noms des propriétés héritées ne peuvent pas être réinscrits. Il existe toutefois une technique pour ajouter une classe en tant que propriétaire d’une propriété de dépendance, même quand celle-ci n’est pas héritée. Pour plus d’informations, consultez [Métadonnées de propriété de dépendance](dependency-property-metadata.md).

Quand vous créez le champ d’identificateur, affectez-lui le même nom que la propriété que vous avez inscrite, plus le suffixe `Property`. Ce champ est votre identificateur pour la propriété de dépendance, et il sera utilisé ultérieurement comme entrée pour le et les <xref:System.Windows.DependencyObject.SetValue%2A> <xref:System.Windows.DependencyObject.GetValue%2A> appels que vous allez effectuer dans les wrappers, par tout autre code qui accède à la propriété par votre propre code, par tout accès au code externe que vous autorisez, par le système de propriétés et potentiellement par les [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processeurs.

> [!NOTE]
> La définition de la propriété de dépendance dans le corps de la classe est l’implémentation type, mais vous pouvez aussi définir une propriété de dépendance dans le constructeur statique de classe. Cette approche peut être plus logique si vous avez besoin de plus d’une ligne de code pour initialiser la propriété de dépendance.

<a name="wrapper1"></a>

### <a name="implementing-the-wrapper"></a>Implémentation du « Wrapper »

Votre implémentation de wrapper doit appeler <xref:System.Windows.DependencyObject.GetValue%2A> dans l' `get` implémentation de et <xref:System.Windows.DependencyObject.SetValue%2A> dans l' `set` implémentation (l’appel d’inscription d’origine et le champ sont également affichés ici pour plus de clarté).

Dans toutes les circonstances sauf dans des circonstances exceptionnelles, vos implémentations de wrapper doivent exécuter uniquement les <xref:System.Windows.DependencyObject.GetValue%2A> <xref:System.Windows.DependencyObject.SetValue%2A> actions et, respectivement. La raison est expliquée dans la rubrique [Propriétés de dépendance et chargement XAML](xaml-loading-and-dependency-properties.md).

Toutes les propriétés de dépendance publiques existantes fournies dans les classes [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] utilisent ce modèle d’implémentation de wrapper simple. La plus grande partie de la complexité du fonctionnement des métadonnées de propriété est un comportement inhérent du système de propriétés ou est implémentée via d’autres concepts, tels que le forçage de type ou les rappels de changement de propriété par l’intermédiaire de métadonnées de propriété.

[!code-csharp[WPFAquariumSln#AGWithWrapper](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#agwithwrapper)]
[!code-vb[WPFAquariumSln#AGWithWrapper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#agwithwrapper)]

Là encore, par Convention, le nom de la propriété wrapper doit être le même que le nom choisi et donné comme premier paramètre de l' <xref:System.Windows.DependencyProperty.Register%2A> appel qui a inscrit la propriété. Si votre propriété ne respecte pas la convention, toutes les utilisations possibles ne sont pas nécessairement désactivées, mais vous rencontrerez plusieurs problèmes :

- Certains aspects des styles et modèles ne fonctionneront pas.

- La plupart des outils et concepteurs doivent s’appuyer sur les conventions d’affectation de noms pour sérialiser correctement [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], ou pour fournir l’assistance d’environnement de concepteur au niveau de chaque propriété.

- L’implémentation actuelle du [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] chargeur contourne entièrement les wrappers et s’appuie sur la Convention d’affectation de noms lors du traitement des valeurs d’attribut. Pour plus d’informations, consultez [Propriétés de dépendance et chargement XAML](xaml-loading-and-dependency-properties.md).

<a name="metadata"></a>

### <a name="property-metadata-for-a-new-dependency-property"></a>Métadonnées de propriété pour une nouvelle propriété de dépendance

Quand vous inscrivez une propriété de dépendance, l’inscription dans le système de propriétés crée un objet de métadonnées qui stocke les caractéristiques de la propriété. La plupart de ces caractéristiques ont des valeurs par défaut qui sont définies si la propriété est inscrite avec les signatures simples de <xref:System.Windows.DependencyProperty.Register%2A> . D’autres signatures de vous <xref:System.Windows.DependencyProperty.Register%2A> permettent de spécifier les métadonnées que vous souhaitez lorsque vous inscrivez la propriété. Les métadonnées les plus courantes pour les propriétés de dépendance consistent à leur attribuer une valeur par défaut qui est appliquée sur les nouvelles instances qui utilisent la propriété.

Si vous créez une propriété de dépendance qui existe sur une classe dérivée de <xref:System.Windows.FrameworkElement> , vous pouvez utiliser la classe de métadonnées plus spécialisée <xref:System.Windows.FrameworkPropertyMetadata> plutôt que la classe de base <xref:System.Windows.PropertyMetadata> . Le constructeur pour la <xref:System.Windows.FrameworkPropertyMetadata> classe a plusieurs signatures dans lesquelles vous pouvez spécifier différentes caractéristiques de métadonnées en combinaison. Si vous souhaitez spécifier la valeur par défaut uniquement, utilisez la signature qui accepte un seul paramètre de type <xref:System.Object> . Transmettez ce paramètre d’objet en tant que valeur par défaut spécifique au type pour votre propriété (la valeur par défaut fournie doit être le type que vous avez fourni comme `propertyType` paramètre dans l' <xref:System.Windows.DependencyProperty.Register%2A> appel).

Pour <xref:System.Windows.FrameworkPropertyMetadata> , vous pouvez également spécifier des indicateurs d’option de métadonnées pour votre propriété. Ces indicateurs sont convertis en propriétés discrètes dans les métadonnées de propriété après l’inscription, et sont utilisés pour spécifier certaines conditions à d’autres processus, tels que le moteur de disposition.

#### <a name="setting-appropriate-metadata-flags"></a>Définition des indicateurs de métadonnées appropriés

- Si votre propriété (ou les modifications de sa valeur) affecte le [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] et, en particulier, affecte la taille ou le rendu de votre élément par le système de disposition dans une page, définissez un ou plusieurs des indicateurs suivants : <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsMeasure> , <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsArrange> , <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsRender> .

  - <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsMeasure>indique qu’une modification de cette propriété nécessite une modification du [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] rendu où l’objet conteneur peut nécessiter plus ou moins d’espace dans le parent. Par exemple, cet indicateur doit être défini pour une propriété « Width ».

  - <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsArrange>indique qu’une modification de cette propriété nécessite une modification [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] du rendu qui ne nécessite généralement pas de modification de l’espace dédié, mais indique que le positionnement dans l’espace a changé. Par exemple, cet indicateur doit être défini pour une propriété « Alignment ».

  - <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsRender>indique qu’une autre modification a eu lieu et n’affecte pas la disposition et la mesure, mais exige un autre rendu. Un exemple serait une propriété qui change une couleur d’un élément existant, telle que « Background ».

  - Ces indicateurs sont souvent utilisés comme protocole dans les métadonnées pour vos propres implémentations de substitution de rappels de disposition ou de système de propriétés. Par exemple, vous pouvez avoir un <xref:System.Windows.DependencyObject.OnPropertyChanged%2A> rappel qui appellera <xref:System.Windows.UIElement.InvalidateArrange%2A> si une propriété de l’instance signale une modification de valeur et a <xref:System.Windows.FrameworkPropertyMetadata.AffectsArrange%2A> comme `true` dans ses métadonnées.

- Certaines propriétés peuvent affecter les caractéristiques de rendu de l’élément parent conteneur, au-delà des modifications de taille requise mentionnées ci-dessus. C’est le cas, par exemple, de la <xref:System.Windows.Documents.Paragraph.MinOrphanLines%2A> propriété utilisée dans le modèle de document dynamique, où les modifications apportées à cette propriété peuvent modifier le rendu global du document dynamique qui contient le paragraphe. Utilisez <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsParentArrange> ou <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsParentMeasure> pour identifier des cas similaires dans vos propres propriétés.

- Par défaut, les propriétés de dépendance prennent en charge la liaison de données. Vous pouvez désactiver délibérément la liaison de données, dans les cas où il n’existe aucun scénario réaliste pour elle, ou quand les performances de liaison de données pour un objet volumineux sont reconnues comme étant un problème.

- Par défaut, la liaison <xref:System.Windows.Data.Binding.Mode%2A> de données pour les propriétés de dépendance est définie par défaut sur <xref:System.Windows.Data.BindingMode.OneWay> . Vous pouvez toujours modifier la liaison pour qu’elle soit <xref:System.Windows.Data.BindingMode.TwoWay> par instance de liaison. pour plus d’informations, consultez [spécifier le sens de la liaison](../data/how-to-specify-the-direction-of-the-binding.md). Toutefois, en tant qu’auteur de la propriété de dépendance, vous pouvez choisir de faire en sorte que la propriété utilise le <xref:System.Windows.Data.BindingMode.TwoWay> mode de liaison par défaut. Un exemple de propriété de dépendance existante est <xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A?displayProperty=nameWithType> ; le scénario de cette propriété est que la <xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A> logique de paramétrage et la composition de <xref:System.Windows.Controls.MenuItem> interagissent avec le style de thème par défaut. La <xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A> logique de propriété utilise la liaison de données en mode natif pour conserver l’état de la propriété en fonction d’autres propriétés d’État et des appels de méthode. Un autre exemple de propriété qui crée une liaison <xref:System.Windows.Data.BindingMode.TwoWay> par défaut est <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> .

- Vous pouvez également activer l’héritage des propriétés dans une propriété de dépendance personnalisée en définissant l' <xref:System.Windows.FrameworkPropertyMetadataOptions.Inherits> indicateur. L’héritage de propriété est utile pour un scénario où des éléments parents et des éléments enfants ont une propriété en commun, et où il est logique que les éléments enfants aient la même valeur de propriété que le parent. Un exemple de propriété héritable est <xref:System.Windows.FrameworkElement.DataContext%2A> , qui est utilisé pour les opérations de liaison pour activer le scénario maître/détail important pour la présentation des données. En rendant <xref:System.Windows.FrameworkElement.DataContext%2A> héritable, tous les éléments enfants héritent également de ce contexte de données. En raison de l’héritage de valeur de propriété, vous pouvez spécifier un contexte de données à la racine de la page ou de l’application, et vous n’avez pas besoin de le respécifier pour les liaisons dans tous les éléments enfants possibles. <xref:System.Windows.FrameworkElement.DataContext%2A>est également un bon exemple pour illustrer que l’héritage remplace la valeur par défaut, mais qu’elle peut toujours être définie localement sur un élément enfant particulier ; Pour plus d’informations, consultez [utiliser le modèle maître/détail avec des données hiérarchiques](../data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md). L’héritage de valeur de propriété peut avoir un impact sur les performances, et doit donc être utilisé avec modération. Pour plus d’informations, consultez [Héritage de la valeur de propriété](property-value-inheritance.md).

- Définissez l' <xref:System.Windows.FrameworkPropertyMetadataOptions.Journal> indicateur pour indiquer si votre propriété de dépendance doit être détectée ou utilisée par les services de journalisation de navigation. C’est le cas, par exemple, de la <xref:System.Windows.Controls.Primitives.Selector.SelectedIndex%2A> propriété ; tout élément sélectionné dans un contrôle de sélection doit être rendu persistant lors de la navigation dans l’historique de journalisation.

<a name="RODP"></a>

## <a name="read-only-dependency-properties"></a>Propriétés de dépendance en lecture seule

Vous pouvez définir une propriété de dépendance en lecture seule. Toutefois, les scénarios pour lesquels vous pourriez définir la propriété en lecture seule sont quelque peu différents, tout comme la procédure pour les inscrire auprès du système de propriétés et exposer l’identificateur. Pour plus d’informations, consultez [Propriétés de dépendance en lecture seule](read-only-dependency-properties.md).

<a name="CTDP"></a>

## <a name="collection-type-dependency-properties"></a>Propriétés de dépendance de type collection

Pour les propriétés de dépendance de type collection, vous devrez prendre en compte certains autres aspects relatifs à l’implémentation. Pour plus d’informations, consultez [Propriétés de dépendance de type collection](collection-type-dependency-properties.md).

<a name="SecurityC"></a>

## <a name="dependency-property-security-considerations"></a>Considérations relatives à la sécurité des propriétés de dépendance

Les propriétés de dépendance doivent être déclarées en tant que propriétés publiques. Les champs d’identificateur de propriété de dépendance doivent être déclarés en tant que champs statiques publics. Même si vous tentez de déclarer d’autres niveaux d’accès (par exemple, protected), une propriété de dépendance est toujours accessible par le biais de l’identificateur en association avec les API du système de propriétés. Même un champ d’identificateur protégé est potentiellement accessible en raison des API de création de rapports de métadonnées ou de détermination de valeur qui font partie du système de propriétés, tel que <xref:System.Windows.LocalValueEnumerator> . Pour plus d’informations, consultez [Sécurité des propriétés de dépendance](dependency-property-security.md).

<a name="DPCtor"></a>

## <a name="dependency-properties-and-class-constructors"></a>Propriétés de dépendance et constructeurs de classe

Il existe un principe fondamental dans la programmation de code managé (souvent appliqué par des outils d’analyse de code tels que FxCop) selon lequel les constructeurs de classe ne doivent pas appeler de méthodes virtuelles. Cela est dû au fait que les constructeurs peuvent être appelés en tant qu’initialisation de base d’un constructeur de classe dérivée, et l’entrée dans la méthode virtuelle par l’intermédiaire du constructeur peut se produire à un état d’initialisation incomplet de l’instance d’objet en cours de construction. Lorsque vous dérivez d’une classe qui dérive déjà de <xref:System.Windows.DependencyObject> , vous devez savoir que le système de propriétés lui-même appelle et expose des méthodes virtuelles en interne. Ces méthodes virtuelles font partie des services du système de propriétés [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. La substitution des méthodes permet aux classes dérivées de participer à la détermination de valeur. Pour éviter les problèmes potentiels liés à l’initialisation au moment de l’exécution, vous ne devez pas définir de valeur de propriété de dépendance dans des constructeurs de classes, sauf si vous respectez un modèle de constructeur très spécifique. Pour plus d’informations, consultez [Modèles de constructeur sécurisé pour DependencyObjects](safe-constructor-patterns-for-dependencyobjects.md).

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des propriétés de dépendance](dependency-properties-overview.md)
- [Métadonnées de propriété de dépendance](dependency-property-metadata.md)
- [Vue d’ensemble de la création de contrôles](../controls/control-authoring-overview.md)
- [Propriétés de dépendance de type collection](collection-type-dependency-properties.md)
- [Sécurité de propriété de dépendance](dependency-property-security.md)
- [Propriétés de dépendance et chargement XAML](xaml-loading-and-dependency-properties.md)
- [Modèles de constructeur sécurisé pour DependencyObjects](safe-constructor-patterns-for-dependencyobjects.md)
