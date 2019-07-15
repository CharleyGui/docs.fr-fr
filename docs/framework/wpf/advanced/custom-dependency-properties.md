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
ms.openlocfilehash: 659497543d40c8eda18b55b4d98feac976c5abf5
ms.sourcegitcommit: 83ecdf731dc1920bca31f017b1556c917aafd7a0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/12/2019
ms.locfileid: "67860244"
---
# <a name="custom-dependency-properties"></a>Propriétés de dépendance personnalisées

Cette rubrique décrit les raisons pour lesquelles les développeurs d’applications et les auteurs de composants [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] peuvent souhaiter créer une propriété de dépendance personnalisée, et décrit les étapes d’implémentation ainsi que certaines options d’implémentation susceptibles d’améliorer les performances, l’utilisation ou la souplesse de la propriété.

<a name="prerequisites"></a>

## <a name="prerequisites"></a>Prérequis

Cette rubrique part du principe que vous savez ce que sont les propriétés de dépendance du point de vue d’un consommateur de propriétés de dépendance existantes sur les classes [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], et que vous avez lu la rubrique [Vue d’ensemble des propriétés de dépendance](dependency-properties-overview.md). Pour pouvoir suivre les exemples de cette rubrique, vous devez également comprendre [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] et savoir comment écrire des applications [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

<a name="whatis"></a>

## <a name="what-is-a-dependency-property"></a>Qu’est ce qu’une propriété de dépendance ?

Vous pouvez permettre à ce qui serait normalement une propriété [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] de prendre en charge les styles, la liaison de données, l’héritage, les animations et les valeurs par défaut en l’implémentant en tant que propriété de dépendance. Propriétés de dépendance sont des propriétés qui sont inscrits avec le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] système de propriétés en appelant le <xref:System.Windows.DependencyProperty.Register%2A> (méthode) (ou <xref:System.Windows.DependencyProperty.RegisterReadOnly%2A>), et qui sont stockées par un <xref:System.Windows.DependencyProperty> champ d’identificateur. Propriétés de dépendance peuvent être utilisées uniquement par <xref:System.Windows.DependencyObject> types, mais <xref:System.Windows.DependencyObject> étant assez haut dans la [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hiérarchie de classes, donc la majorité des classes disponibles dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] peut prendre en charge les propriétés de dépendance. Pour plus d’informations sur les propriétés de dépendance et sur la terminologie et les conventions utilisées pour les décrire dans ce [!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)], consultez [Vue d’ensemble des propriétés de dépendance](dependency-properties-overview.md).

<a name="example_dp"></a>

## <a name="examples-of-dependency-properties"></a>Exemples de propriétés de dépendance

Exemples de propriétés de dépendance qui sont implémentées sur [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] classes incluent le <xref:System.Windows.Controls.Control.Background%2A> propriété, le <xref:System.Windows.FrameworkElement.Width%2A> propriété et le <xref:System.Windows.Controls.TextBox.Text%2A> propriété, entre autres. Chaque propriété de dépendance exposée par une classe a un champ statique public correspondant de type <xref:System.Windows.DependencyProperty> exposé sur cette même classe. Il s’agit de l’identificateur de la propriété de dépendance. L’identificateur est nommé à l’aide d’une convention : le nom de la propriété de dépendance, auquel est ajoutée la chaîne `Property`. Par exemple, correspondants <xref:System.Windows.DependencyProperty> champ d’identificateur pour le <xref:System.Windows.Controls.Control.Background%2A> propriété est <xref:System.Windows.Controls.Control.BackgroundProperty>. L’identificateur stocke les informations sur la propriété de dépendance comme elle a été inscrite, et l’identificateur est ensuite utilisé pour d’autres opérations impliquant la propriété de dépendance, comme l’appel <xref:System.Windows.DependencyObject.SetValue%2A>.

Comme mentionné dans la [Vue d’ensemble des propriétés de dépendance](dependency-properties-overview.md), toutes les propriétés de dépendance dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] (sauf la plupart des propriétés jointes) sont également des propriétés [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] à cause de l’implémentation « wrapper ». Ainsi, à partir du code, vous pouvez obtenir ou définir des propriétés de dépendance en appelant des accesseurs [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] qui définissent les wrappers de la même manière que vous utiliseriez d’autres propriétés [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]. En tant que consommateur de propriétés de dépendance établies, vous n’utilisez généralement pas le <xref:System.Windows.DependencyObject> méthodes <xref:System.Windows.DependencyObject.GetValue%2A> et <xref:System.Windows.DependencyObject.SetValue%2A>, qui sont le point de connexion au système de propriétés sous-jacent. Au lieu de cela, l’implémentation existante de la [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] propriétés a déjà appelé <xref:System.Windows.DependencyObject.GetValue%2A> et <xref:System.Windows.DependencyObject.SetValue%2A> au sein de la `get` et `set` des implémentations de wrapper de la propriété, via le champ d’identificateur de manière appropriée . Si vous implémentez une propriété de dépendance personnalisée vous-même, vous définirez le wrapper de la même façon.

<a name="backing_with_dp"></a>

## <a name="when-should-you-implement-a-dependency-property"></a>Quand faut-il implémenter une propriété de dépendance ?

Lorsque vous implémentez une propriété sur une classe, tant que votre classe dérive de <xref:System.Windows.DependencyObject>, vous avez la possibilité de stocker la propriété avec un <xref:System.Windows.DependencyProperty> identificateur et par conséquent, pour le rendre une propriété de dépendance. Faire de votre propriété une propriété de dépendance n’est pas toujours nécessaire ni approprié. Cela dépend des besoins de votre scénario. Parfois, la technique classique qui consiste à stocker la propriété dans un champ privé est adéquate. Toutefois, vous devez implémenter votre propriété en tant que propriété de dépendance chaque fois que vous souhaitez qu’elle prenne en charge une ou plusieurs des fonctionnalités [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] suivantes :

- Vous souhaitez que votre propriété puisse être définie dans un style. Pour plus d’informations, consultez [Application d’un style et création de modèles](../controls/styling-and-templating.md).

- Vous souhaitez que votre propriété prenne en charge la liaison de données. Pour plus d’informations sur les propriétés de dépendance de liaison de données, consultez [Lier les propriétés de deux contrôles](../data/how-to-bind-the-properties-of-two-controls.md).

- Vous souhaitez que votre propriété puisse être définie avec une référence à une ressource dynamique. Pour plus d’informations, consultez [Ressources XAML](xaml-resources.md).

- Vous voulez hériter automatiquement une valeur de propriété d’un élément parent dans l’arborescence d’éléments. Dans ce cas, inscrire avec le <xref:System.Windows.DependencyProperty.RegisterAttached%2A> (méthode), même si vous créez également un wrapper de propriété pour [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] accès. Pour plus d’informations, consultez [Héritage de valeur de propriété](property-value-inheritance.md).

- Vous souhaitez que votre propriété puisse être animée. Pour plus d’informations, consultez [Vue d’ensemble de l’animation](../graphics-multimedia/animation-overview.md).

- Vous souhaitez que le système de propriétés signale quand la valeur précédente de la propriété a été modifiée par des actions effectuées par le système de propriétés, l’environnement ou l’utilisateur, ou par la lecture et l’utilisation de styles. À l’aide des métadonnées de propriété, votre propriété peut spécifier une méthode de rappel qui sera appelée chaque fois que le système de propriétés détermine que la valeur de propriété a été modifiée de manière certaine. Le forçage de valeur de propriété est un concept connexe. Pour plus d’informations, consultez [Validation et rappels de propriétés de dépendance](dependency-property-callbacks-and-validation.md).

- Vous souhaitez utiliser des conventions de métadonnées établies qui sont également utilisées par des processus [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], par exemple signaler si la modification d’une valeur de propriété exige que le système de disposition recompose les visuels d’un élément. Ou vous souhaitez pouvoir utiliser des substitutions de métadonnées pour que les classes dérivées puissent changer des caractéristiques basées sur les métadonnées, telles que la valeur par défaut.

- Vous souhaitez que les propriétés d’un contrôle personnalisé pour recevoir le Concepteur de Visual Studio WPF prennent en charge, tel que **propriétés** édition de la fenêtre. Pour plus d’informations, consultez [Vue d’ensemble de la création de contrôles](../controls/control-authoring-overview.md).

Quand vous examinez ces scénarios, vous devez également réfléchir si vous pouvez accomplir votre scénario en substituant les métadonnées d’une propriété de dépendance existante, plutôt qu’en implémentant une toute nouvelle propriété. Le fait qu’une substitution de métadonnées soit pratique ou non dépend de votre scénario et de sa ressemblance avec l’implémentation dans les classes et les propriétés de dépendance [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] existantes. Pour plus d’informations sur la substitution de métadonnées dans les propriétés existantes, consultez [Métadonnées de propriété de dépendance](dependency-property-metadata.md).

<a name="checklist"></a>

## <a name="checklist-for-defining-a-dependency-property"></a>Liste de vérification pour la définition d’une propriété de dépendance

La définition d’une propriété de dépendance implique quatre concepts distincts. Ces concepts ne sont pas des étapes procédurales nécessairement strictes, car certaines d’entre elles finissent par être combinées sur des lignes de code uniques dans l’implémentation :

- (Facultatif) Créez des métadonnées de propriété pour la propriété de dépendance.

- Inscrivez le nom de propriété auprès du système de propriétés, en spécifiant un type de propriétaire et le type de la valeur de propriété. Spécifiez également les métadonnées de propriété, si elles sont utilisées.

- Définir un <xref:System.Windows.DependencyProperty> identificateur comme un `public` `static` `readonly` champ sur le type de propriétaire.

- Définissez une propriété « wrapper » [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] dont le nom correspond à celui de la propriété de dépendance. Implémentez les accesseurs `get` et `set` de la propriété « wrapper » [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] pour se connecter à la propriété de dépendance qui la stocke.

<a name="registering"></a>

### <a name="registering-the-property-with-the-property-system"></a>Inscription de la propriété auprès du système de propriétés

Pour que votre propriété soit une propriété de dépendance, vous devez l’inscrire dans une table gérée par le système de propriétés et lui donner un identificateur unique utilisé comme qualificateur pour les opérations de système de propriétés ultérieures. Ces opérations peuvent être des opérations internes ou votre propre code appelant les API du système de propriété. Pour inscrire la propriété, vous appelez le <xref:System.Windows.DependencyProperty.Register%2A> méthode dans le corps de votre classe (à l’intérieur de la classe, mais en dehors de toutes les définitions de membre). Le champ d’identificateur est également fourni par le <xref:System.Windows.DependencyProperty.Register%2A> appel de méthode, comme la valeur de retour. La raison qui le <xref:System.Windows.DependencyProperty.Register%2A> appel est effectué en dehors de l’autre membre de définitions se trouve, car vous utilisez cette valeur de retour pour assigner et créer un `public` `static` `readonly` champ de type <xref:System.Windows.DependencyProperty> dans le cadre de votre classe. Ce champ devient l’identificateur de votre propriété de dépendance.

[!code-csharp[WPFAquariumSln#RegisterAG](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#registerag)]
[!code-vb[WPFAquariumSln#RegisterAG](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#registerag)]

<a name="nameconventions"></a>

### <a name="dependency-property-name-conventions"></a>Conventions pour les noms des propriétés de dépendance

Il existe des conventions d’affectation de noms établies pour les propriétés de dépendance. Vous devez les respecter dans toutes les circonstances, sauf les plus exceptionnelles.

La propriété de dépendance proprement dite aura un nom de base, « AquariumGraphic » comme dans cet exemple, donné comme premier paramètre de <xref:System.Windows.DependencyProperty.Register%2A>. Ce nom doit être unique dans chaque type d’inscription. Les propriétés de dépendance héritées par l’intermédiaire des types de base sont considérées comme faisant déjà partie du type d’inscription ; les noms des propriétés héritées ne peuvent pas être réinscrits. Il existe toutefois une technique pour ajouter une classe en tant que propriétaire d’une propriété de dépendance, même quand celle-ci n’est pas héritée. Pour plus d’informations, consultez [Métadonnées de propriété de dépendance](dependency-property-metadata.md).

Quand vous créez le champ d’identificateur, affectez-lui le même nom que la propriété que vous avez inscrite, plus le suffixe `Property`. Ce champ est votre identificateur pour la propriété de dépendance, et il sera utilisé ultérieurement comme entrée pour le <xref:System.Windows.DependencyObject.SetValue%2A> et <xref:System.Windows.DependencyObject.GetValue%2A> autoriser les appels que vous vous permettront d’être dans les wrappers, par tout autre accès de code à la propriété par votre propre code, par tout accès de code externe , par le système de propriétés et potentiellement par [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processeurs.

> [!NOTE]
> La définition de la propriété de dépendance dans le corps de la classe est l’implémentation type, mais vous pouvez aussi définir une propriété de dépendance dans le constructeur statique de classe. Cette approche peut être plus logique si vous avez besoin de plus d’une ligne de code pour initialiser la propriété de dépendance.

<a name="wrapper1"></a>

### <a name="implementing-the-wrapper"></a>Implémentation du « Wrapper »

Votre implémentation de wrapper doit appeler <xref:System.Windows.DependencyObject.GetValue%2A> dans le `get` implémentation, et <xref:System.Windows.DependencyObject.SetValue%2A> dans le `set` implémentation (l’appel d’inscription et le champ d’origine sont affichés ici par souci de clarté).

Dans des circonstances exceptionnelles tout sauf vos implémentations de wrapper doivent exécuter uniquement le <xref:System.Windows.DependencyObject.GetValue%2A> et <xref:System.Windows.DependencyObject.SetValue%2A> actions, respectivement. La raison est expliquée dans la rubrique [Propriétés de dépendance et chargement XAML](xaml-loading-and-dependency-properties.md).

Toutes les propriétés de dépendance publiques existantes fournies dans les classes [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] utilisent ce modèle d’implémentation de wrapper simple. La plus grande partie de la complexité du fonctionnement des métadonnées de propriété est un comportement inhérent du système de propriétés ou est implémentée via d’autres concepts, tels que le forçage de type ou les rappels de changement de propriété par l’intermédiaire de métadonnées de propriété.

[!code-csharp[WPFAquariumSln#AGWithWrapper](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#agwithwrapper)]
[!code-vb[WPFAquariumSln#AGWithWrapper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#agwithwrapper)]

Là encore, par convention, le nom de la propriété wrapper doit être le même que le nom choisi et fourni comme premier paramètre de la <xref:System.Windows.DependencyProperty.Register%2A> appel qui inscrit la propriété. Si votre propriété ne respecte pas la convention, toutes les utilisations possibles ne sont pas nécessairement désactivées, mais vous rencontrerez plusieurs problèmes :

- Certains aspects des styles et modèles ne fonctionneront pas.

- La plupart des outils et concepteurs doivent s’appuyer sur les conventions d’affectation de noms pour sérialiser correctement [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], ou pour fournir l’assistance d’environnement de concepteur au niveau de chaque propriété.

- L’implémentation actuelle du chargeur [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ignore complètement les wrappers et utilise la convention d’affectation de noms lors du traitement des valeurs d’attributs. Pour plus d’informations, consultez [Propriétés de dépendance et chargement XAML](xaml-loading-and-dependency-properties.md).

<a name="metadata"></a>

### <a name="property-metadata-for-a-new-dependency-property"></a>Métadonnées de propriété pour une nouvelle propriété de dépendance

Quand vous inscrivez une propriété de dépendance, l’inscription dans le système de propriétés crée un objet de métadonnées qui stocke les caractéristiques de la propriété. La plupart de ces caractéristiques ont des valeurs par défaut qui sont définies si la propriété est inscrite avec les signatures simples de <xref:System.Windows.DependencyProperty.Register%2A>. D’autres signatures <xref:System.Windows.DependencyProperty.Register%2A> vous permettent de spécifier les métadonnées que vous souhaitez que vous inscrivez la propriété. Les métadonnées les plus courantes pour les propriétés de dépendance consistent à leur attribuer une valeur par défaut qui est appliquée sur les nouvelles instances qui utilisent la propriété.

Si vous créez une propriété de dépendance qui existe sur une classe dérivée de <xref:System.Windows.FrameworkElement>, vous pouvez utiliser la classe de métadonnées plus spécialisée <xref:System.Windows.FrameworkPropertyMetadata> au lieu de la base de <xref:System.Windows.PropertyMetadata> classe. Le constructeur de la <xref:System.Windows.FrameworkPropertyMetadata> classe a plusieurs signatures où vous pouvez spécifier différentes caractéristiques de métadonnées dans la combinaison. Si vous souhaitez spécifier la valeur par défaut uniquement, utilisez la signature qui accepte un seul paramètre de type <xref:System.Object>. Passez ce paramètre d’objet comme une valeur par défaut spécifique au type pour votre propriété (la valeur par défaut fournie doit être le type que vous avez fourni comme le `propertyType` paramètre dans le <xref:System.Windows.DependencyProperty.Register%2A> appeler).

Pour <xref:System.Windows.FrameworkPropertyMetadata>, vous pouvez également spécifier des indicateurs d’option de métadonnées pour votre propriété. Ces indicateurs sont convertis en propriétés discrètes dans les métadonnées de propriété après l’inscription, et sont utilisés pour spécifier certaines conditions à d’autres processus, tels que le moteur de disposition.

#### <a name="setting-appropriate-metadata-flags"></a>Définition des indicateurs de métadonnées appropriés

- Si votre propriété (ou les modifications de sa valeur) affecte la [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)], et en particulier, la manière dont le système de disposition doit dimensionner ou rendre l’élément dans une page, définissez un ou plusieurs des indicateurs suivants : <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsMeasure>, <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsArrange>, <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsRender>.

  - <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsMeasure> Indique qu’une modification de cette propriété nécessite une modification apportée à [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] rendu où l’objet conteneur peut nécessiter plus ou moins d’espace dans le parent. Par exemple, cet indicateur doit être défini pour une propriété « Width ».

  - <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsArrange> Indique qu’une modification de cette propriété nécessite une modification apportée à [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] généralement de rendu qui ne nécessite pas une modification dans l’espace dédié, mais n’indique que le positionnement dans l’espace a changé. Par exemple, cet indicateur doit être défini pour une propriété « Alignment ».

  - <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsRender> Indique qu’une autre modification s’est produite et n’affecteront pas disposition et la mesure, mais qu’un autre rendu est nécessaire. Un exemple serait une propriété qui change une couleur d’un élément existant, telle que « Background ».

  - Ces indicateurs sont souvent utilisés comme protocole dans les métadonnées pour vos propres implémentations de substitution de rappels de disposition ou de système de propriétés. Par exemple, vous pouvez avoir un <xref:System.Windows.DependencyObject.OnPropertyChanged%2A> rappel appellera <xref:System.Windows.UIElement.InvalidateArrange%2A> si n’importe quelle propriété de l’instance signale une modification de valeur et a <xref:System.Windows.FrameworkPropertyMetadata.AffectsArrange%2A> comme `true` dans ses métadonnées.

- Certaines propriétés peuvent affecter les caractéristiques de rendu de l’élément parent conteneur, au-delà des modifications de taille requise mentionnées ci-dessus. Par exemple, le <xref:System.Windows.Documents.Paragraph.MinOrphanLines%2A> propriété utilisée dans le modèle de document de flux, où les modifications à cette propriété peuvent changer l’ensemble du rendu du document dynamique qui contient le paragraphe. Utilisez <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsParentArrange> ou <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsParentMeasure> pour identifier des cas semblables dans vos propres propriétés.

- Par défaut, les propriétés de dépendance prennent en charge la liaison de données. Vous pouvez désactiver délibérément la liaison de données, dans les cas où il n’existe aucun scénario réaliste pour elle, ou quand les performances de liaison de données pour un objet volumineux sont reconnues comme étant un problème.

- Par défaut, la liaison de données <xref:System.Windows.Data.Binding.Mode%2A> pour les propriétés de dépendance est <xref:System.Windows.Data.BindingMode.OneWay>. Vous pouvez toujours modifier la liaison <xref:System.Windows.Data.BindingMode.TwoWay> par instance de liaison ; pour plus d’informations, consultez [spécifier le sens de la liaison](../data/how-to-specify-the-direction-of-the-binding.md). Mais en tant que créateur de propriété de dépendance, vous pouvez choisir d’utiliser la propriété <xref:System.Windows.Data.BindingMode.TwoWay> mode de liaison par défaut. Un exemple d’une propriété de dépendance existante est <xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A?displayProperty=nameWithType>; le scénario de cette propriété est que le <xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A> définition logique et la composition de <xref:System.Windows.Controls.MenuItem> interagir avec le style de thème par défaut. Le <xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A> logique de la propriété utilise la liaison de données en mode natif pour maintenir l’état de la propriété conformément à d’autres propriétés de l’état et les appels de méthode. Un autre exemple de propriété qui lie <xref:System.Windows.Data.BindingMode.TwoWay> par défaut est <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType>.

- Vous pouvez également activer l’héritage de propriété dans une propriété de dépendance personnalisée en définissant le <xref:System.Windows.FrameworkPropertyMetadataOptions.Inherits> indicateur. L’héritage de propriété est utile pour un scénario où des éléments parents et des éléments enfants ont une propriété en commun, et où il est logique que les éléments enfants aient la même valeur de propriété que le parent. Est un exemple de propriété pouvant être héritées <xref:System.Windows.FrameworkElement.DataContext%2A>, qui est utilisé pour la liaison des opérations pour activer le scénario maître / détail important pour la présentation des données. En rendant <xref:System.Windows.FrameworkElement.DataContext%2A> pouvant être héritées, tous les éléments enfants héritent de ce contexte de données également. En raison de l’héritage de valeur de propriété, vous pouvez spécifier un contexte de données à la racine de la page ou de l’application, et vous n’avez pas besoin de le respécifier pour les liaisons dans tous les éléments enfants possibles. <xref:System.Windows.FrameworkElement.DataContext%2A> est également un bon exemple pour illustrer que l’héritage remplace la valeur par défaut, mais il peut toujours être défini localement sur un élément enfant ; Pour plus d’informations, consultez [utiliser le modèle maître / détail avec des données hiérarchiques](../data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md). L’héritage de valeur de propriété peut avoir un impact sur les performances, et doit donc être utilisé avec modération. Pour plus d’informations, consultez [Héritage de la valeur de propriété](property-value-inheritance.md).

- Définir le <xref:System.Windows.FrameworkPropertyMetadataOptions.Journal> indicateur pour indiquer si votre propriété de dépendance doit être détectée ou utilisée par les services de journalisation de navigation. Par exemple, le <xref:System.Windows.Controls.Primitives.Selector.SelectedIndex%2A> propriété ; les éléments sélectionnés dans une sélection de contrôle doit être rendue persistante lorsque l’historique de journalisation.

<a name="RODP"></a>

## <a name="read-only-dependency-properties"></a>Propriétés de dépendance en lecture seule

Vous pouvez définir une propriété de dépendance en lecture seule. Toutefois, les scénarios pour lesquels vous pourriez définir la propriété en lecture seule sont quelque peu différents, tout comme la procédure pour les inscrire auprès du système de propriétés et exposer l’identificateur. Pour plus d’informations, consultez [Propriétés de dépendance en lecture seule](read-only-dependency-properties.md).

<a name="CTDP"></a>

## <a name="collection-type-dependency-properties"></a>Propriétés de dépendance de type collection

Pour les propriétés de dépendance de type collection, vous devrez prendre en compte certains autres aspects relatifs à l’implémentation. Pour plus d’informations, consultez [Propriétés de dépendance de type collection](collection-type-dependency-properties.md).

<a name="SecurityC"></a>

## <a name="dependency-property-security-considerations"></a>Considérations relatives à la sécurité des propriétés de dépendance

Les propriétés de dépendance doivent être déclarées en tant que propriétés publiques. Les champs d’identificateur de propriété de dépendance doivent être déclarés en tant que champs statiques publics. Même si vous tentez de déclarer des autres niveaux d’accès (tel que protégés), une propriété de dépendance est toujours accessible via l’identificateur en association avec les API du système de propriété. Même un champ d’identificateur protégé est potentiellement accessible en raison de métadonnées détermination de création de rapports ou valeur API qui font partie du système de propriétés, telles que <xref:System.Windows.LocalValueEnumerator>. Pour plus d’informations, consultez [Sécurité des propriétés de dépendance](dependency-property-security.md).

<a name="DPCtor"></a>

## <a name="dependency-properties-and-class-constructors"></a>Propriétés de dépendance et constructeurs de classe

Il existe un principe fondamental dans la programmation de code managé (souvent appliqué par des outils d’analyse de code tels que FxCop) selon lequel les constructeurs de classe ne doivent pas appeler de méthodes virtuelles. Cela est dû au fait que les constructeurs peuvent être appelés en tant qu’initialisation de base d’un constructeur de classe dérivée, et l’entrée dans la méthode virtuelle par l’intermédiaire du constructeur peut se produire à un état d’initialisation incomplet de l’instance d’objet en cours de construction. Lorsque vous dérivez à partir de n’importe quelle classe qui dérive déjà de <xref:System.Windows.DependencyObject>, vous devez être conscient que le système de propriétés lui-même appelle et expose des méthodes virtuelles en interne. Ces méthodes virtuelles font partie des services du système de propriétés [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. La substitution des méthodes permet aux classes dérivées de participer à la détermination de valeur. Pour éviter les problèmes potentiels liés à l’initialisation au moment de l’exécution, vous ne devez pas définir de valeur de propriété de dépendance dans des constructeurs de classes, sauf si vous respectez un modèle de constructeur très spécifique. Pour plus d’informations, consultez [Modèles de constructeur sécurisé pour DependencyObjects](safe-constructor-patterns-for-dependencyobjects.md).

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des propriétés de dépendance](dependency-properties-overview.md)
- [Métadonnées de propriété de dépendance](dependency-property-metadata.md)
- [Vue d’ensemble de la création de contrôles](../controls/control-authoring-overview.md)
- [Propriétés de dépendance de type collection](collection-type-dependency-properties.md)
- [Sécurité de propriété de dépendance](dependency-property-security.md)
- [Propriétés de dépendance et chargement XAML](xaml-loading-and-dependency-properties.md)
- [Modèles de constructeur sécurisé pour DependencyObjects](safe-constructor-patterns-for-dependencyobjects.md)
