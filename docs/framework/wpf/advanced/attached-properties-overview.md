---
title: Vue d'ensemble des propriétés jointes
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- attached properties [WPF Designer]
ms.assetid: 75928354-dc01-47e8-a018-8409aec1f32d
ms.openlocfilehash: 403c4e76e302536513b9de0694ab7b0de621d5d2
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73455520"
---
# <a name="attached-properties-overview"></a>Vue d'ensemble des propriétés jointes

Une propriété jointe est un concept défini par XAML. Elle est conçue pour être utilisée comme un type de propriété globale qui peut être défini sur tout objet. Dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], les propriétés jointes sont généralement définies comme une forme spécialisée de la propriété de dépendance qui n’a pas le « wrapper » de propriété classique.

## Conditions préalables<a name="prerequisites"></a>

Cette rubrique part du principe que vous savez ce que sont les propriétés de dépendance du point de vue d’un consommateur de propriétés de dépendance existantes sur les classes [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], et que vous avez lu la [Vue d’ensemble des propriétés de dépendance](dependency-properties-overview.md). Pour suivre les exemples de cette rubrique, vous devez également comprendre le XAML et savoir comment écrire des applications WPF.

## Pourquoi utiliser des propriétés jointes<a name="attached_properties_usage"></a>

Une des finalités d’une propriété jointe est de permettre à différents éléments enfants de spécifier des valeurs uniques pour une propriété définie en fait dans un élément parent. Une application spécifique de ce scénario est de faire en sorte que les éléments enfants informent l’élément parent sur la manière dont ils doivent être présentés dans l’[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. La propriété <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> en est un exemple. La propriété <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> est créée en tant que propriété jointe, car elle est conçue pour être définie sur les éléments contenus dans un <xref:System.Windows.Controls.DockPanel>, plutôt que sur <xref:System.Windows.Controls.DockPanel> elle-même. La classe <xref:System.Windows.Controls.DockPanel> définit le champ de <xref:System.Windows.DependencyProperty> statique nommé <xref:System.Windows.Controls.DockPanel.DockProperty>, puis fournit les méthodes <xref:System.Windows.Controls.DockPanel.GetDock%2A> et <xref:System.Windows.Controls.DockPanel.SetDock%2A> comme accesseurs publics pour la propriété jointe.

## Propriétés jointes en XAML<a name="attached_properties_xaml"></a>

En XAML, vous définissez des propriétés jointes à l’aide de la syntaxe *FournisseurPropriétéJointe*.*NomPropriété*

Voici un exemple de la façon dont vous pouvez définir <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> en XAML :

[!code-xaml[PropertiesOvwSupport#APBasicUsage](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml#apbasicusage)]

Notez que l’utilisation est quelque peu similaire à une propriété statique ; vous référencez toujours le type <xref:System.Windows.Controls.DockPanel> qui possède et inscrit la propriété jointe, plutôt que de faire référence à une instance spécifiée par Name.

En outre, comme une propriété jointe en XAML est un attribut que vous définissez dans le balisage, seule l’opération définie est pertinente. Vous ne pouvez pas obtenir directement une propriété en XAML, bien que des mécanismes indirects permettent de comparer des valeurs, telles que les déclencheurs dans les styles (pour plus d’informations, consultez [Application d’un style et création de modèles](../controls/styling-and-templating.md)).

### <a name="attached-property-implementation-in-wpf"></a>Implémentation des propriétés jointes dans WPF

Dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], la plupart des propriétés jointes qui existent sur les types WPF qui sont liées à la présentation de l’interface utilisateur sont implémentées en tant que propriétés de dépendance. Les propriétés jointes sont un concept XAML, tandis que les propriétés de dépendance sont un concept WPF. Étant donné que les propriétés jointes WPF sont des propriétés de dépendance, elles prennent en charge des concepts de propriété de dépendance tels que les métadonnées de propriété et les valeurs par défaut de ces métadonnées de propriété.

## Comment les propriétés jointes sont utilisées par le type propriétaire<a name="howused"></a>

Bien que les propriétés jointes puissent être définies sur tout objet, cela ne signifie pas systématiquement que leur définition produira un résultat concret ou que leur valeur sera jamais utilisée par un autre objet. En général, les propriétés jointes sont utilisées pour que les objets provenant de diverses relations logiques ou hiérarchies de classes possibles puissent chacun communiquer des informations communes au type qui définit la propriété jointe. Le type qui définit la propriété jointe suit en général l’un de ces modèles :

- Le type qui définit la propriété jointe est conçu pour pouvoir être l’élément parent des éléments qui définiront les valeurs de la propriété jointe. Le type itère ensuite ses objets enfants par le biais de la logique interne au sein d’une structure d’objets arborescente, obtient les valeurs et agit sur elles.

- Le type qui définit la propriété jointe est utilisé comme élément enfant pour divers éléments parents et modèles de contenu possibles.

- Le type qui définit la propriété jointe représente un service. D’autres types définissent les valeurs de la propriété jointe. Quand l’élément qui définit la propriété est évalué dans le contexte du service, les valeurs de la propriété jointe sont obtenues par le biais de la logique interne de la classe de service.

### <a name="an-example-of-a-parent-defined-attached-property"></a>Exemple d’une propriété jointe définie par le parent

Le scénario le plus courant dans lequel WPF définit une propriété jointe est lorsqu’un élément parent prend en charge une collection d’éléments enfants, et implémente également un comportement où les caractéristiques du comportement sont signalées individuellement pour chaque élément enfant.

<xref:System.Windows.Controls.DockPanel> définit la propriété jointe <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>, et <xref:System.Windows.Controls.DockPanel> contient du code de niveau classe dans le cadre de sa logique de rendu (plus précisément, <xref:System.Windows.Controls.DockPanel.MeasureOverride%2A> et <xref:System.Windows.Controls.DockPanel.ArrangeOverride%2A>). Une instance de <xref:System.Windows.Controls.DockPanel> vérifie toujours si l’un de ses éléments enfants immédiats a défini une valeur pour <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>. Si tel est le cas, ces valeurs sont entrées pour la logique de rendu appliquée à l’élément enfant en question. Les instances de <xref:System.Windows.Controls.DockPanel> imbriquées traitent chacune leurs propres collections d’éléments enfants immédiats, mais ce comportement est spécifique à l’implémentation de la manière dont <xref:System.Windows.Controls.DockPanel> traite les valeurs <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>. Il est théoriquement possible d’avoir des propriétés jointes qui influent sur les éléments au-delà du parent immédiat. Si la <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> propriété jointe est définie sur un élément qui n’a aucun <xref:System.Windows.Controls.DockPanel> élément parent pour agir dessus, aucune erreur ou exception n’est levée. Cela signifie simplement qu’une valeur de propriété globale a été définie, mais qu’elle n’a pas de parent <xref:System.Windows.Controls.DockPanel> en cours qui pourrait consommer les informations.

## Propriétés jointes dans le code<a name="attached_properties_code"></a>

Les propriétés jointes dans WPF n’ont pas les méthodes de « wrapper » CLR typiques pour un accès facile en obtenir/définir. Cela est dû au fait que la propriété jointe ne fait pas nécessairement partie de l’espace de noms CLR pour les instances où la propriété est définie. Toutefois, un processeur XAML doit pouvoir définir ces valeurs quand XAML est analysé. Pour prendre en charge l’utilisation d’une propriété jointe effective, le type de propriétaire de la propriété jointe doit implémenter des méthodes d’accesseur dédiées au format **Get_PropertyName_** et **Set_PropertyName_** . Ces méthodes d’accesseur dédiées sont également utiles pour obtenir ou définir la propriété jointe dans le code. Du point de vue du code, une propriété jointe s’apparente à un champ de stockage comportant des accesseurs de méthode au lieu d’accesseurs de propriété, et ce champ de stockage peut exister sur tout objet plutôt que devoir être défini de manière spécifique.

L’exemple suivant illustre la définition d’une propriété jointe dans le code. Dans cet exemple, `myCheckBox` est une instance de la classe <xref:System.Windows.Controls.CheckBox>.

[!code-csharp[PropertiesOvwSupport#APCode](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#apcode)]
[!code-vb[PropertiesOvwSupport#APCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#apcode)]

Semblable au cas XAML, si `myCheckBox` n’avait pas déjà été ajouté en tant qu’élément enfant de `myDockPanel` par la troisième ligne de code, la quatrième ligne de code ne lève pas d’exception, mais la valeur de propriété n’interagit pas avec un parent <xref:System.Windows.Controls.DockPanel> et par conséquent résultat. Seule une valeur <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> définie sur un élément enfant combiné avec la présence d’un élément parent <xref:System.Windows.Controls.DockPanel> entraîne un comportement effectif dans l’application rendue. (Dans ce cas, vous pourriez définir la propriété jointe, puis la joindre à l’arborescence. Vous pourriez également joindre la propriété à l’arborescence, puis la définir. Le résultat est le même, quel que soit l’ordre des actions.)

## Métadonnées de propriété jointe<a name="attached_properties_metadata"></a>

Lors de l’inscription de la propriété, <xref:System.Windows.FrameworkPropertyMetadata> est définie pour spécifier les caractéristiques de la propriété, par exemple si la propriété affecte le rendu, les mesures, etc. Les métadonnées d’une propriété jointe sont en général identiques à celles d’une propriété de dépendance. Si vous spécifiez une valeur par défaut dans une substitution des métadonnées d’une propriété jointe, cette valeur devient la valeur par défaut de la propriété jointe implicite sur les instances de la classe de substitution. Spécifiquement, votre valeur par défaut est signalée si un processus demande la valeur d’une propriété jointe par le biais de l’accesseur de méthode `Get` de cette propriété, en spécifiant une instance de la classe dans laquelle vous avez indiqué les métadonnées, et si la valeur de cette propriété jointe n’était autrement pas définie.

Si vous souhaitez activer l’héritage des valeurs de propriété sur une propriété, vous devez utiliser des propriétés jointes plutôt que des propriétés de dépendance non jointes. Pour plus d’informations, consultez [Héritage de la valeur de propriété](property-value-inheritance.md).

## Propriétés jointes personnalisées<a name="custom"></a>

### Quand créer une propriété jointe<a name="create_attached_properties"></a>

Vous pouvez créer une propriété jointe si un mécanisme de définition de propriété doit être disponible pour les classes autres que la classe de définition. Le scénario le plus courant à cette fin est la mise en page. <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType>et <xref:System.Windows.Controls.Canvas.Top%2A?displayProperty=nameWithType>sont des exemples de propriétés de disposition existantes. Le scénario activé ici implique que les éléments existant comme éléments enfants sur les éléments contrôlant la mise en page sont en mesure d’exprimer individuellement des spécifications de mise en page à leurs éléments parents de mise en page et chacun d’eux définit une valeur de propriété configurée par le parent en tant que propriété jointe.

Un autre scénario illustrant l’utilisation d’une propriété jointe s’applique quand votre classe représente un service et que vous voulez que les classes soient en mesure d’intégrer le service avec une plus grande transparence.

Toutefois, un autre scénario consiste à recevoir la prise en charge du Concepteur WPF Visual Studio, telle que la modification de la fenêtre **Propriétés** . Pour plus d’informations, consultez [Vue d’ensemble de la création de contrôles](../controls/control-authoring-overview.md).

Comme mentionné précédemment, vous devez enregistrer une propriété jointe si vous souhaitez utiliser l’héritage des valeurs de propriété.

### Comment créer une propriété jointe<a name="how_do_i_create_attached_properties"></a>

Si votre classe définit la propriété jointe strictement pour une utilisation sur d’autres types, la classe n’a pas à dériver de <xref:System.Windows.DependencyObject>. Toutefois, vous devez dériver de <xref:System.Windows.DependencyObject> si vous suivez le modèle WPF global qui consiste à faire en sorte que la propriété jointe soit également une propriété de dépendance.

Définissez votre propriété jointe en tant que propriété de dépendance en déclarant un champ `public static readonly` de type <xref:System.Windows.DependencyProperty>. Vous définissez ce champ à l’aide de la valeur de retour de la méthode <xref:System.Windows.DependencyProperty.RegisterAttached%2A>. Le nom du champ doit correspondre au nom de la propriété jointe, ajouté à la chaîne `Property`, pour suivre le modèle WPF établi pour nommer les champs d’identification et les propriétés qu’ils représentent. Le fournisseur de propriétés jointes doit également fournir des méthodes **Get_PropertyName_** et **Set_PropertyName_** statiques comme accesseurs pour la propriété jointe ; Si vous ne le faites pas, le système de propriétés ne pourra pas utiliser votre propriété jointe.

> [!NOTE]
> Si vous omettez l’accesseur Get de la propriété jointe, la liaison de données sur la propriété ne fonctionnera pas dans les outils de conception, tels que Visual Studio et Blend pour Visual Studio.

#### <a name="the-get-accessor"></a>Accesseur Get

La signature de l’accesseur **Get_PropertyName_** doit être :

`public static object GetPropertyName(object target)`

- L’objet `target` peut être défini comme un type plus spécifique dans votre implémentation. Par exemple, la méthode <xref:System.Windows.Controls.DockPanel.GetDock%2A?displayProperty=nameWithType> type le paramètre comme <xref:System.Windows.UIElement>, car la propriété jointe est uniquement destinée à être définie sur <xref:System.Windows.UIElement> instances.

- La valeur de retour peut être spécifiée comme un type plus spécifique dans votre implémentation. Par exemple, la méthode <xref:System.Windows.Controls.DockPanel.GetDock%2A> le tape comme <xref:System.Windows.Controls.Dock>, car la valeur ne peut être définie que sur cette énumération.

#### <a name="the-set-accessor"></a>Accesseur Set

La signature de l’accesseur **Set_PropertyName_** doit être :

`public static void SetPropertyName(object target, object value)`

- L’objet `target` peut être défini comme un type plus spécifique dans votre implémentation. Par exemple, la méthode <xref:System.Windows.Controls.DockPanel.SetDock%2A> le tape comme <xref:System.Windows.UIElement>, car la propriété jointe est uniquement destinée à être définie sur <xref:System.Windows.UIElement> instances.

- L’objet `value` peut être défini comme un type plus spécifique dans votre implémentation. Par exemple, la méthode <xref:System.Windows.Controls.DockPanel.SetDock%2A> le tape comme <xref:System.Windows.Controls.Dock>, car la valeur ne peut être définie que sur cette énumération. N’oubliez pas que la valeur de cette méthode est l’entrée provenant du chargeur XAML quand il rencontre votre propriété jointe dans une utilisation des propriétés jointes dans le balisage. Cette entrée est la valeur spécifiée comme valeur d’attribut XAML dans le balisage. Ainsi, la conversion de type, la sérialisation de valeur ou l’extension de balisage doit être prise en charge pour le type utilisé afin que le type approprié puisse être créé à partir de la valeur d’attribut (laquelle est en fin de compte une simple chaîne).

L’exemple suivant montre l’inscription de la propriété de dépendance (à l’aide de la méthode <xref:System.Windows.DependencyProperty.RegisterAttached%2A>), ainsi que les accesseurs **Get_PropertyName_** et **Set_PropertyName_** . Dans cet exemple, le nom de la propriété jointe est `IsBubbleSource`. Les accesseurs doivent donc être nommés `GetIsBubbleSource` et `SetIsBubbleSource`.

[!code-csharp[WPFAquariumSln#RegisterAttachedBubbler](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#registerattachedbubbler)]
[!code-vb[WPFAquariumSln#RegisterAttachedBubbler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#registerattachedbubbler)]

#### <a name="attached-property-attributes"></a>Attributs des propriétés jointes

WPF définit plusieurs [!INCLUDE[TLA2#tla_netframewkattr#plural](../../../../includes/tla2sharptla-netframewkattrsharpplural-md.md)] qui sont destinées à fournir des informations sur les propriétés jointes aux processus de réflexion, et aux utilisateurs typiques de la réflexion et des informations de propriété telles que les concepteurs. Les propriétés jointes ayant un type de portée illimitée, les concepteurs ont besoin d’un moyen d’éviter que les utilisateurs croulent sous une liste globale de toutes les propriétés jointes qui sont définies dans l’implémentation d’une technologie particulière utilisant XAML. Les [!INCLUDE[TLA2#tla_netframewkattr#plural](../../../../includes/tla2sharptla-netframewkattrsharpplural-md.md)] que WPF définit pour les propriétés jointes peuvent être utilisées pour définir la portée des situations où une propriété jointe donnée doit être affichée dans une fenêtre de propriétés. Vous pouvez également envisager l’application de ces attributs à vos propres propriétés jointes personnalisées. La finalité et la syntaxe des [!INCLUDE[TLA2#tla_netframewkattr#plural](../../../../includes/tla2sharptla-netframewkattrsharpplural-md.md)] sont décrites dans les pages de référence appropriées :

- <xref:System.Windows.AttachedPropertyBrowsableAttribute>

- <xref:System.Windows.AttachedPropertyBrowsableForChildrenAttribute>

- <xref:System.Windows.AttachedPropertyBrowsableForTypeAttribute>

- <xref:System.Windows.AttachedPropertyBrowsableWhenAttributePresentAttribute>

## En savoir plus sur les propriétés jointes<a name="more"></a>

- Pour plus d’informations sur la création d’une propriété jointe, consultez [Enregistrer une propriété jointe](how-to-register-an-attached-property.md).

- Pour obtenir des scénarios d’usage avancés des propriétés de dépendance et des propriétés jointes, consultez [Propriétés de dépendance personnalisées](custom-dependency-properties.md).

- Vous pouvez également enregistrer une propriété en tant que propriété jointe et que propriété de dépendance ; mais dans cette situation, vous exposez encore les implémentations de « wrapper ». Dans ce cas, vous pouvez définir la propriété soit sur cet élément, soit sur tout élément par le biais de la syntaxe de propriété jointe XAML. <xref:System.Windows.FrameworkElement.FlowDirection%2A?displayProperty=nameWithType>est un exemple de propriété avec un scénario approprié pour les utilisations standard et attachées.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.DependencyProperty>
- [Vue d’ensemble des propriétés de dépendance](dependency-properties-overview.md)
- [Propriétés de dépendance personnalisées](custom-dependency-properties.md)
- [Vue d’ensemble du langage XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Enregistrer une propriété jointe](how-to-register-an-attached-property.md)
