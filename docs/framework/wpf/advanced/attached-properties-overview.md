---
title: Vue d'ensemble des propriétés jointes
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- attached properties [WPF Designer]
ms.assetid: 75928354-dc01-47e8-a018-8409aec1f32d
ms.openlocfilehash: b207db459776c9f8fa7ea247d01071eeb8c995cf
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739294"
---
# <a name="attached-properties-overview"></a>Vue d'ensemble des propriétés jointes

Une propriété jointe est un concept défini par XAML. Elle est conçue pour être utilisée comme un type de propriété globale qui peut être défini sur tout objet. Dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], les propriétés jointes sont généralement définies comme une forme spécialisée de la propriété de dépendance qui n’a pas le « wrapper » de propriété classique.

## <a name="prerequisites"></a>Conditions préalables<a name="prerequisites"></a>

Cet article suppose que vous comprenez les propriétés de dépendance [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] du point de vue d’un consommateur de propriétés de dépendance existantes sur les classes, et ont lu le [Aperçu des propriétés de dépendance](dependency-properties-overview.md). Pour suivre les exemples de cet article, vous devez également comprendre XAML et savoir écrire des applications WPF.

## <a name="why-use-attached-properties"></a>Pourquoi utiliser les propriétés ci-jointes<a name="attached_properties_usage"></a>

L’un des buts d’une propriété attachée est de permettre à différents éléments pour enfants de spécifier des valeurs uniques pour une propriété qui est définie dans un élément parent. Une application spécifique de ce scénario est de faire en sorte que les éléments enfants informent l’élément parent sur la manière dont ils doivent être présentés dans l’[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. Un exemple <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> est la propriété. La <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> propriété est créée comme une propriété attachée parce qu’elle <xref:System.Windows.Controls.DockPanel> est conçue <xref:System.Windows.Controls.DockPanel> pour être placée sur des éléments qui sont contenus dans un plutôt que sur lui-même. La <xref:System.Windows.Controls.DockPanel> classe définit <xref:System.Windows.DependencyProperty> le <xref:System.Windows.Controls.DockPanel.DockProperty>champ statique nommé, <xref:System.Windows.Controls.DockPanel.SetDock%2A> puis fournit le et les <xref:System.Windows.Controls.DockPanel.GetDock%2A> méthodes en tant qu’accesseurs publics pour la propriété ci-jointe.

## <a name="attached-properties-in-xaml"></a>Propriétés attachées dans XAML<a name="attached_properties_xaml"></a>

En XAML, vous définissez des propriétés jointes à l’aide de la syntaxe *FournisseurPropriétéJointe*.*NomPropriété*

Ce qui suit est un <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> exemple de la façon dont vous pouvez définir dans XAML:

[!code-xaml[PropertiesOvwSupport#APBasicUsage](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml#apbasicusage)]

L’utilisation est un peu similaire à une propriété statique; vous faites toujours <xref:System.Windows.Controls.DockPanel> référence au type qui possède et enregistre la propriété ci-jointe, plutôt que de se référer à n’importe quelle instance spécifiée par son nom.

En outre, comme une propriété jointe en XAML est un attribut que vous définissez dans le balisage, seule l’opération définie est pertinente. Vous ne pouvez pas obtenir directement une propriété en XAML, bien que des mécanismes indirects permettent de comparer des valeurs, telles que les déclencheurs dans les styles (pour plus d’informations, consultez [Application d’un style et création de modèles](../../../desktop-wpf/fundamentals/styles-templates-overview.md)).

### <a name="attached-property-implementation-in-wpf"></a>Implémentation des propriétés jointes dans WPF

Dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], la plupart des propriétés liées à l’interface utilisateur sur les types WPF sont mises en œuvre comme propriétés de dépendance. Les propriétés ci-jointes sont un concept XAML, tandis que les propriétés de dépendance sont un concept WPF. Étant donné que les propriétés attachées au WPF sont des propriétés de dépendance, ils prennent en charge les concepts de propriété de dépendance tels que les métadonnées de propriété, et les valeurs par défaut de ces métadonnées de propriété.

## <a name="how-attached-properties-are-used-by-the-owning-type"></a>Comment les propriétés ci-jointes sont utilisées par le type de propriétaire<a name="howused"></a>

Bien que les propriétés jointes puissent être définies sur tout objet, cela ne signifie pas systématiquement que leur définition produira un résultat concret ou que leur valeur sera jamais utilisée par un autre objet. En général, les propriétés jointes sont utilisées pour que les objets provenant de diverses relations logiques ou hiérarchies de classes possibles puissent chacun communiquer des informations communes au type qui définit la propriété jointe. Le type qui définit la propriété jointe suit en général l’un de ces modèles :

- Le type qui définit la propriété jointe est conçu pour pouvoir être l’élément parent des éléments qui définiront les valeurs de la propriété jointe. Le type itère ensuite ses objets enfants par le biais de la logique interne au sein d’une structure d’objets arborescente, obtient les valeurs et agit sur elles.

- Le type qui définit la propriété jointe est utilisé comme élément enfant pour divers éléments parents et modèles de contenu possibles.

- Le type qui définit la propriété jointe représente un service. D’autres types définissent les valeurs de la propriété jointe. Quand l’élément qui définit la propriété est évalué dans le contexte du service, les valeurs de la propriété jointe sont obtenues par le biais de la logique interne de la classe de service.

### <a name="an-example-of-a-parent-defined-attached-property"></a>Exemple d’une propriété jointe définie par le parent

Le scénario le plus typique où WPF définit une propriété attachée est quand un élément parent prend en charge une collection d’éléments pour enfants, et met également en œuvre un comportement où les spécificités du comportement sont rapportés individuellement pour chaque élément enfant.

<xref:System.Windows.Controls.DockPanel>définit la <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> propriété ci-jointe, et <xref:System.Windows.Controls.DockPanel> a le code de classe-niveau dans le cadre de sa logique de rendu (en particulier, <xref:System.Windows.Controls.DockPanel.MeasureOverride%2A> et <xref:System.Windows.Controls.DockPanel.ArrangeOverride%2A>). Une <xref:System.Windows.Controls.DockPanel> instance vérifiera toujours si l’un de ses <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>éléments immédiats de l’enfant a établi une valeur pour . Si tel est le cas, ces valeurs sont entrées pour la logique de rendu appliquée à l’élément enfant en question. Les <xref:System.Windows.Controls.DockPanel> instances imbriquées traitent chacune leurs propres collections immédiates d’éléments pour enfants, mais ce comportement est spécifique à la façon dont <xref:System.Windows.Controls.DockPanel> les processus évaluent. <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> Il est théoriquement possible d’avoir des propriétés jointes qui influent sur les éléments au-delà du parent immédiat. Si <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> la propriété ci-jointe est <xref:System.Windows.Controls.DockPanel> placée sur un élément qui n’a pas d’élément parent pour agir sur elle, aucune erreur ou exception n’est soulevée. Cela signifie simplement qu’une valeur de propriété <xref:System.Windows.Controls.DockPanel> globale a été définie, mais elle n’a pas de parent actuel qui pourrait consommer l’information.

## <a name="attached-properties-in-code"></a>Propriétés jointes dans le code<a name="attached_properties_code"></a>

Les propriétés jointes dans WPF n’ont pas les méthodes typiques d’emballage CLR pour un accès facile à l’accès. C’est parce que la propriété ci-jointe ne fait pas nécessairement partie de l’espace de nom CLR pour les cas où la propriété est définie. Toutefois, un processeur XAML doit pouvoir définir ces valeurs quand XAML est analysé. Pour soutenir une utilisation effective de la propriété attachée, le type de propriétaire de la propriété ci-jointe doit mettre en œuvre des méthodes d’accesseur dédiés sous la forme **Get_PropertyName_** et **Set_PropertyName_**. Ces méthodes d’accesseur dédiées sont également utiles pour obtenir ou définir la propriété jointe dans le code. Du point de vue du code, une propriété jointe s’apparente à un champ de stockage comportant des accesseurs de méthode au lieu d’accesseurs de propriété, et ce champ de stockage peut exister sur tout objet plutôt que devoir être défini de manière spécifique.

L’exemple suivant illustre la définition d’une propriété jointe dans le code. Dans cet `myCheckBox` exemple, est <xref:System.Windows.Controls.CheckBox> un cas de la classe.

[!code-csharp[PropertiesOvwSupport#APCode](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#apcode)]
[!code-vb[PropertiesOvwSupport#APCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#apcode)]

Semblable à l’affaire XAML, si n’avait `myCheckBox` `myDockPanel` pas déjà été ajouté comme élément enfant de par la quatrième ligne de code, la cinquième ligne de code ne soulèverait pas une exception, mais la valeur de la propriété n’interagirait pas avec un <xref:System.Windows.Controls.DockPanel> parent et ne ferait donc rien. Seule <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> une valeur fixée sur un élément <xref:System.Windows.Controls.DockPanel> enfant combiné à la présence d’un élément parent provoquera un comportement efficace dans l’application rendue. (Dans ce cas, vous pourriez définir la propriété jointe, puis la joindre à l’arborescence. Vous pourriez également joindre la propriété à l’arborescence, puis la définir. Le résultat est le même, quel que soit l’ordre des actions.)

## <a name="attached-property-metadata"></a>Métadonnées de propriété attachées<a name="attached_properties_metadata"></a>

Lors de l’enregistrement de la propriété, <xref:System.Windows.FrameworkPropertyMetadata> est configuré pour spécifier les caractéristiques de la propriété, telles que si la propriété affecte le rendu, la mesure, et ainsi de suite. Les métadonnées d’une propriété jointe sont en général identiques à celles d’une propriété de dépendance. Si vous spécifiez une valeur par défaut dans une substitution des métadonnées d’une propriété jointe, cette valeur devient la valeur par défaut de la propriété jointe implicite sur les instances de la classe de substitution. Spécifiquement, votre valeur par défaut est signalée si un processus demande la valeur d’une propriété jointe par le biais de l’accesseur de méthode `Get` de cette propriété, en spécifiant une instance de la classe dans laquelle vous avez indiqué les métadonnées, et si la valeur de cette propriété jointe n’était autrement pas définie.

Si vous souhaitez activer l’héritage des valeurs de propriété sur une propriété, vous devez utiliser des propriétés jointes plutôt que des propriétés de dépendance non jointes. Pour plus d’informations, consultez [Héritage de la valeur de propriété](property-value-inheritance.md).

## <a name="custom-attached-properties"></a>Propriétés personnalisées<a name="custom"></a>

### <a name="when-to-create-an-attached-property"></a>Quand créer une propriété attachée<a name="create_attached_properties"></a>

Vous pouvez créer une propriété jointe si un mécanisme de définition de propriété doit être disponible pour les classes autres que la classe de définition. Le scénario le plus courant à cette fin est la mise en page. Exemples de propriétés <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType>de <xref:System.Windows.Controls.Canvas.Top%2A?displayProperty=nameWithType>mise en page existantes sont <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>, , et . Le scénario activé ici implique que les éléments existant comme éléments enfants sur les éléments contrôlant la mise en page sont en mesure d’exprimer individuellement des spécifications de mise en page à leurs éléments parents de mise en page et chacun d’eux définit une valeur de propriété configurée par le parent en tant que propriété jointe.

Un autre scénario illustrant l’utilisation d’une propriété jointe s’applique quand votre classe représente un service et que vous voulez que les classes soient en mesure d’intégrer le service avec une plus grande transparence.

Encore un autre scénario est de recevoir Visual Studio WPF Designer soutien, tels que l’édition de fenêtre **Properties.** Pour plus d’informations, consultez [Vue d’ensemble de la création de contrôles](../controls/control-authoring-overview.md).

Comme mentionné précédemment, vous devez enregistrer une propriété jointe si vous souhaitez utiliser l’héritage des valeurs de propriété.

### <a name="how-to-create-an-attached-property"></a>Comment créer une propriété attachée<a name="how_do_i_create_attached_properties"></a>

Si votre classe définit la propriété attachée strictement pour une utilisation sur d’autres types, alors la classe n’a pas à dériver de <xref:System.Windows.DependencyObject>. Mais vous avez besoin <xref:System.Windows.DependencyObject> de dériver de si vous suivez le modèle global WPF d’avoir votre propriété attachée également être une propriété de dépendance.

Définissez votre propriété ci-jointe comme `public static readonly` une <xref:System.Windows.DependencyProperty>propriété de dépendance en déclarant un champ de type. Vous définissez ce champ en <xref:System.Windows.DependencyProperty.RegisterAttached%2A> utilisant la valeur de retour de la méthode. Le nom de champ doit correspondre au nom `Property`de propriété ci-joint, joint avec la chaîne, pour suivre le modèle WPF établi de nommer les champs d’identification par rapport aux propriétés qu’ils représentent. Le fournisseur de biens attenant doit également fournir des méthodes **statiques Get_PropertyName_** et **Set_PropertyName_** comme accesseurs pour la propriété ci-jointe; ne pas le faire, le système de propriété n’est pas en mesure d’utiliser votre propriété ci-jointe.

> [!NOTE]
> Si vous ometez l’accesseur de la propriété ci-jointe, la liaison de données sur la propriété ne fonctionnera pas dans les outils de conception, tels que Visual Studio et Blend for Visual Studio.

#### <a name="the-get-accessor"></a>Accesseur Get

La signature de **l’accesseur Get_PropertyName_** doit être :

`public static object GetPropertyName(object target)`

- L’objet `target` peut être défini comme un type plus spécifique dans votre implémentation. Par exemple, <xref:System.Windows.Controls.DockPanel.GetDock%2A?displayProperty=nameWithType> la méthode <xref:System.Windows.UIElement>tape le paramètre comme , parce <xref:System.Windows.UIElement> que la propriété ci-jointe est seulement destiné à être fixé sur les instances.

- La valeur de retour peut être spécifiée comme un type plus spécifique dans votre implémentation. Par exemple, <xref:System.Windows.Controls.DockPanel.GetDock%2A> la méthode <xref:System.Windows.Controls.Dock>le tape comme , parce que la valeur ne peut être réglée à cette énumération.

#### <a name="the-set-accessor"></a>Accesseur Set

La signature de **l’accesseur Set_PropertyName_** doit être :

`public static void SetPropertyName(object target, object value)`

- L’objet `target` peut être défini comme un type plus spécifique dans votre implémentation. Par exemple, <xref:System.Windows.Controls.DockPanel.SetDock%2A> la méthode <xref:System.Windows.UIElement>le tape comme , parce que <xref:System.Windows.UIElement> la propriété ci-jointe est seulement destiné à être fixé sur les instances.

- L’objet `value` peut être défini comme un type plus spécifique dans votre implémentation. Par exemple, <xref:System.Windows.Controls.DockPanel.SetDock%2A> la méthode <xref:System.Windows.Controls.Dock>le tape comme , parce que la valeur ne peut être réglée à cette énumération. N’oubliez pas que la valeur de cette méthode est l’entrée provenant du chargeur XAML quand il rencontre votre propriété jointe dans une utilisation des propriétés jointes dans le balisage. Cette entrée est la valeur spécifiée comme valeur d’attribut XAML dans le balisage. Ainsi, la conversion de type, la sérialisation de valeur ou l’extension de balisage doit être prise en charge pour le type utilisé afin que le type approprié puisse être créé à partir de la valeur d’attribut (laquelle est en fin de compte une simple chaîne).

L’exemple suivant montre l’enregistrement <xref:System.Windows.DependencyProperty.RegisterAttached%2A> des biens de dépendance (en utilisant la méthode), ainsi que les **Get_PropertyName_** et les accesseurs **Set_PropertyName_.** Dans cet exemple, le nom de la propriété jointe est `IsBubbleSource`. Les accesseurs doivent donc être nommés `GetIsBubbleSource` et `SetIsBubbleSource`.

[!code-csharp[WPFAquariumSln#RegisterAttachedBubbler](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#registerattachedbubbler)]
[!code-vb[WPFAquariumSln#RegisterAttachedBubbler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#registerattachedbubbler)]

#### <a name="attached-property-attributes"></a>Attributs des propriétés jointes

WPF définit plusieurs attributs .NET qui sont destinés à fournir des informations sur les propriétés attachées aux processus de réflexion, et aux utilisateurs typiques de réflexion et d’informations sur la propriété tels que les concepteurs. Les propriétés jointes ayant un type de portée illimitée, les concepteurs ont besoin d’un moyen d’éviter que les utilisateurs croulent sous une liste globale de toutes les propriétés jointes qui sont définies dans l’implémentation d’une technologie particulière utilisant XAML. Les attributs .NET que WPF définit pour les propriétés ci-jointes peuvent être utilisés pour établir la portée des situations où une propriété jointe donnée doit être indiquée dans une fenêtre de propriétés. Vous pouvez également envisager l’application de ces attributs à vos propres propriétés jointes personnalisées. Le but et la syntaxe des attributs .NET sont décrits sur les pages de référence appropriées :

- <xref:System.Windows.AttachedPropertyBrowsableAttribute>

- <xref:System.Windows.AttachedPropertyBrowsableForChildrenAttribute>

- <xref:System.Windows.AttachedPropertyBrowsableForTypeAttribute>

- <xref:System.Windows.AttachedPropertyBrowsableWhenAttributePresentAttribute>

## <a name="learning-more-about-attached-properties"></a>En savoir plus sur les propriétés ci-jointes<a name="more"></a>

- Pour plus d’informations sur la création d’une propriété jointe, consultez [Enregistrer une propriété jointe](how-to-register-an-attached-property.md).

- Pour obtenir des scénarios d’usage avancés des propriétés de dépendance et des propriétés jointes, consultez [Propriétés de dépendance personnalisées](custom-dependency-properties.md).

- Vous pouvez également enregistrer une propriété en tant que propriété jointe et que propriété de dépendance ; mais dans cette situation, vous exposez encore les implémentations de « wrapper ». Dans ce cas, vous pouvez définir la propriété soit sur cet élément, soit sur tout élément par le biais de la syntaxe de propriété jointe XAML. Un exemple d’une propriété avec un scénario approprié <xref:System.Windows.FrameworkElement.FlowDirection%2A?displayProperty=nameWithType>pour les usages standard et ci-joints est .

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.DependencyProperty>
- [Vue d’ensemble des propriétés de dépendance](dependency-properties-overview.md)
- [Propriétés de dépendance personnalisées](custom-dependency-properties.md)
- [Vue d’ensemble du langage XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Enregistrer une propriété jointe](how-to-register-an-attached-property.md)
