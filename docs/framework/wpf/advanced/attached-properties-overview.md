---
title: Vue d'ensemble des propriétés jointes
description: En savoir plus sur les propriétés jointes dans Windows Presentation Foundation, qui sont des propriétés globales définissables sur n’importe quel objet.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- attached properties [WPF Designer]
ms.assetid: 75928354-dc01-47e8-a018-8409aec1f32d
ms.openlocfilehash: 993f65024fcfc4f39a408c81af43b798360e6cf6
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168377"
---
# <a name="attached-properties-overview"></a>Vue d'ensemble des propriétés jointes

Une propriété jointe est un concept défini par XAML. Elle est conçue pour être utilisée comme un type de propriété globale qui peut être défini sur tout objet. Dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], les propriétés jointes sont généralement définies comme une forme spécialisée de la propriété de dépendance qui n’a pas le « wrapper » de propriété classique.

## <a name="prerequisites"></a>Conditions préalables<a name="prerequisites"></a>

Cet article suppose que vous comprenez les propriétés de dépendance du point de vue d’un consommateur de propriétés de dépendance existantes sur les [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] classes, et que vous avez lu la [vue d’ensemble des propriétés de dépendance](dependency-properties-overview.md). Pour suivre les exemples de cet article, vous devez également comprendre le XAML et savoir comment écrire des applications WPF.

## <a name="why-use-attached-properties"></a>Pourquoi utiliser des propriétés jointes<a name="attached_properties_usage"></a>

L’une des finalités d’une propriété jointe est de permettre à différents éléments enfants de spécifier des valeurs uniques pour une propriété définie dans un élément parent. Une application spécifique de ce scénario est de faire en sorte que les éléments enfants informent l’élément parent sur la manière dont ils doivent être présentés dans l’[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. La propriété en est un exemple <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> . La <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> propriété est créée en tant que propriété jointe, car elle est conçue pour être définie sur les éléments contenus dans un <xref:System.Windows.Controls.DockPanel> plutôt que sur <xref:System.Windows.Controls.DockPanel> lui-même. La <xref:System.Windows.Controls.DockPanel> classe définit le <xref:System.Windows.DependencyProperty> champ statique nommé <xref:System.Windows.Controls.DockPanel.DockProperty> , puis fournit les <xref:System.Windows.Controls.DockPanel.GetDock%2A> méthodes et <xref:System.Windows.Controls.DockPanel.SetDock%2A> comme accesseurs publics pour la propriété jointe.

## <a name="attached-properties-in-xaml"></a>Propriétés jointes en XAML<a name="attached_properties_xaml"></a>

En XAML, vous définissez des propriétés jointes à l’aide de la syntaxe *FournisseurPropriétéJointe*.*NomPropriété*

Voici un exemple de la façon dont vous pouvez définir <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> en XAML :

[!code-xaml[PropertiesOvwSupport#APBasicUsage](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml#apbasicusage)]

L’utilisation est quelque peu similaire à une propriété statique ; vous référencez toujours le type <xref:System.Windows.Controls.DockPanel> qui possède et inscrit la propriété jointe, plutôt que de faire référence à une instance spécifiée par Name.

En outre, comme une propriété jointe en XAML est un attribut que vous définissez dans le balisage, seule l’opération définie est pertinente. Vous ne pouvez pas obtenir directement une propriété en XAML, bien que des mécanismes indirects permettent de comparer des valeurs, telles que les déclencheurs dans les styles (pour plus d’informations, consultez [Application d’un style et création de modèles](../../../desktop-wpf/fundamentals/styles-templates-overview.md)).

### <a name="attached-property-implementation-in-wpf"></a>Implémentation des propriétés jointes dans WPF

Dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] , la plupart des propriétés associées à l’interface utilisateur sur les types WPF sont implémentées en tant que propriétés de dépendance. Les propriétés jointes sont un concept XAML, tandis que les propriétés de dépendance sont un concept WPF. Étant donné que les propriétés jointes WPF sont des propriétés de dépendance, elles prennent en charge des concepts de propriété de dépendance tels que les métadonnées de propriété et les valeurs par défaut de ces métadonnées de propriété.

## <a name="how-attached-properties-are-used-by-the-owning-type"></a>Comment les propriétés jointes sont utilisées par le type propriétaire<a name="howused"></a>

Bien que les propriétés jointes puissent être définies sur tout objet, cela ne signifie pas systématiquement que leur définition produira un résultat concret ou que leur valeur sera jamais utilisée par un autre objet. En général, les propriétés jointes sont utilisées pour que les objets provenant de diverses relations logiques ou hiérarchies de classes possibles puissent chacun communiquer des informations communes au type qui définit la propriété jointe. Le type qui définit la propriété jointe suit en général l’un de ces modèles :

- Le type qui définit la propriété jointe est conçu pour pouvoir être l’élément parent des éléments qui définiront les valeurs de la propriété jointe. Le type itère ensuite ses objets enfants par le biais de la logique interne au sein d’une structure d’objets arborescente, obtient les valeurs et agit sur elles.

- Le type qui définit la propriété jointe est utilisé comme élément enfant pour divers éléments parents et modèles de contenu possibles.

- Le type qui définit la propriété jointe représente un service. D’autres types définissent les valeurs de la propriété jointe. Quand l’élément qui définit la propriété est évalué dans le contexte du service, les valeurs de la propriété jointe sont obtenues par le biais de la logique interne de la classe de service.

### <a name="an-example-of-a-parent-defined-attached-property"></a>Exemple d’une propriété jointe définie par le parent

Le scénario le plus courant dans lequel WPF définit une propriété jointe est lorsqu’un élément parent prend en charge une collection d’éléments enfants, et implémente également un comportement où les caractéristiques du comportement sont signalées individuellement pour chaque élément enfant.

<xref:System.Windows.Controls.DockPanel>définit la <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> propriété jointe et <xref:System.Windows.Controls.DockPanel> a un code de niveau classe dans le cadre de sa logique de rendu (plus précisément, <xref:System.Windows.Controls.DockPanel.MeasureOverride%2A> et <xref:System.Windows.Controls.DockPanel.ArrangeOverride%2A> ). Une <xref:System.Windows.Controls.DockPanel> instance vérifie toujours si l’un de ses éléments enfants immédiats a défini une valeur pour <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> . Si tel est le cas, ces valeurs sont entrées pour la logique de rendu appliquée à l’élément enfant en question. <xref:System.Windows.Controls.DockPanel>Les instances imbriquées traitent chacune leurs propres collections d’éléments enfants immédiats, mais ce comportement est spécifique à l’implémentation de la façon dont <xref:System.Windows.Controls.DockPanel> traite les <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> valeurs. Il est théoriquement possible d’avoir des propriétés jointes qui influent sur les éléments au-delà du parent immédiat. Si la <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> propriété jointe est définie sur un élément qui n’a pas <xref:System.Windows.Controls.DockPanel> d’élément parent pour agir dessus, aucune erreur ou exception n’est levée. Cela signifie simplement qu’une valeur de propriété globale a été définie, mais qu’elle n’a pas de <xref:System.Windows.Controls.DockPanel> parent actuel pouvant consommer les informations.

## <a name="attached-properties-in-code"></a>Propriétés jointes dans le code<a name="attached_properties_code"></a>

Les propriétés jointes dans WPF n’ont pas les méthodes de « wrapper » CLR typiques pour un accès facile en obtenir/définir. Cela est dû au fait que la propriété jointe ne fait pas nécessairement partie de l’espace de noms CLR pour les instances où la propriété est définie. Toutefois, un processeur XAML doit pouvoir définir ces valeurs quand XAML est analysé. Pour prendre en charge l’utilisation d’une propriété jointe effective, le type de propriétaire de la propriété jointe doit implémenter des méthodes d’accesseur dédiées sous la forme **Get_PropertyName_** et **Set_PropertyName_**. Ces méthodes d’accesseur dédiées sont également utiles pour obtenir ou définir la propriété jointe dans le code. Du point de vue du code, une propriété jointe s’apparente à un champ de stockage comportant des accesseurs de méthode au lieu d’accesseurs de propriété, et ce champ de stockage peut exister sur tout objet plutôt que devoir être défini de manière spécifique.

L’exemple suivant illustre la définition d’une propriété jointe dans le code. Dans cet exemple, `myCheckBox` est une instance de la <xref:System.Windows.Controls.CheckBox> classe.

[!code-csharp[PropertiesOvwSupport#APCode](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#apcode)]
[!code-vb[PropertiesOvwSupport#APCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#apcode)]

Semblable au cas XAML, si `myCheckBox` n’avait pas déjà été ajouté en tant qu’élément enfant de `myDockPanel` par la quatrième ligne de code, la cinquième ligne de code ne lève pas d’exception, mais la valeur de la propriété n’interagit pas avec un <xref:System.Windows.Controls.DockPanel> parent et ne fait donc rien. Seule une <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> valeur définie sur un élément enfant associé à la présence d’un <xref:System.Windows.Controls.DockPanel> élément parent entraînera un comportement effectif dans l’application rendue. (Dans ce cas, vous pourriez définir la propriété jointe, puis la joindre à l’arborescence. Vous pourriez également joindre la propriété à l’arborescence, puis la définir. Le résultat est le même, quel que soit l’ordre des actions.)

## <a name="attached-property-metadata"></a>Métadonnées de propriété jointe<a name="attached_properties_metadata"></a>

Lors de l’inscription de la propriété, <xref:System.Windows.FrameworkPropertyMetadata> est défini pour spécifier les caractéristiques de la propriété, par exemple si la propriété affecte le rendu, les mesures, etc. Les métadonnées d’une propriété jointe sont en général identiques à celles d’une propriété de dépendance. Si vous spécifiez une valeur par défaut dans une substitution des métadonnées d’une propriété jointe, cette valeur devient la valeur par défaut de la propriété jointe implicite sur les instances de la classe de substitution. Spécifiquement, votre valeur par défaut est signalée si un processus demande la valeur d’une propriété jointe par le biais de l’accesseur de méthode `Get` de cette propriété, en spécifiant une instance de la classe dans laquelle vous avez indiqué les métadonnées, et si la valeur de cette propriété jointe n’était autrement pas définie.

Si vous souhaitez activer l’héritage des valeurs de propriété sur une propriété, vous devez utiliser des propriétés jointes plutôt que des propriétés de dépendance non jointes. Pour plus d’informations, consultez [Héritage de la valeur de propriété](property-value-inheritance.md).

## <a name="custom-attached-properties"></a>Propriétés jointes personnalisées<a name="custom"></a>

### <a name="when-to-create-an-attached-property"></a>Quand créer une propriété jointe<a name="create_attached_properties"></a>

Vous pouvez créer une propriété jointe si un mécanisme de définition de propriété doit être disponible pour les classes autres que la classe de définition. Le scénario le plus courant à cette fin est la mise en page. , Et sont des exemples de propriétés de disposition existantes <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType> <xref:System.Windows.Controls.Canvas.Top%2A?displayProperty=nameWithType> . Le scénario activé ici implique que les éléments existant comme éléments enfants sur les éléments contrôlant la mise en page sont en mesure d’exprimer individuellement des spécifications de mise en page à leurs éléments parents de mise en page et chacun d’eux définit une valeur de propriété configurée par le parent en tant que propriété jointe.

Un autre scénario illustrant l’utilisation d’une propriété jointe s’applique quand votre classe représente un service et que vous voulez que les classes soient en mesure d’intégrer le service avec une plus grande transparence.

Toutefois, un autre scénario consiste à recevoir la prise en charge du Concepteur WPF Visual Studio, telle que la modification de la fenêtre **Propriétés** . Pour plus d’informations, consultez [Vue d’ensemble de la création de contrôles](../controls/control-authoring-overview.md).

Comme mentionné précédemment, vous devez enregistrer une propriété jointe si vous souhaitez utiliser l’héritage des valeurs de propriété.

### <a name="how-to-create-an-attached-property"></a>Comment créer une propriété jointe<a name="how_do_i_create_attached_properties"></a>

Si votre classe définit la propriété jointe strictement pour une utilisation sur d’autres types, la classe n’a pas à dériver de <xref:System.Windows.DependencyObject> . Toutefois, vous devez dériver de <xref:System.Windows.DependencyObject> si vous suivez le modèle WPF global qui consiste à faire en sorte que la propriété jointe soit également une propriété de dépendance.

Définissez votre propriété jointe en tant que propriété de dépendance en déclarant un `public static readonly` champ de type <xref:System.Windows.DependencyProperty> . Vous définissez ce champ à l’aide de la valeur de retour de la <xref:System.Windows.DependencyProperty.RegisterAttached%2A> méthode. Le nom du champ doit correspondre au nom de la propriété jointe, ajouté à la chaîne `Property` , pour suivre le modèle WPF établi pour nommer les champs d’identification et les propriétés qu’ils représentent. Le fournisseur de propriétés jointes doit également fournir des méthodes **Get_PropertyName_** et **Set_PropertyName_** statiques comme accesseurs de la propriété jointe ; Si ce n’est pas le cas, le système de propriétés ne peut pas utiliser votre propriété jointe.

> [!NOTE]
> Si vous omettez l’accesseur Get de la propriété jointe, la liaison de données sur la propriété ne fonctionnera pas dans les outils de conception, tels que Visual Studio et Blend pour Visual Studio.

#### <a name="the-get-accessor"></a>Accesseur Get

La signature de l’accesseur **Get_PropertyName_** doit être :

`public static object GetPropertyName(object target)`

- L’objet `target` peut être défini comme un type plus spécifique dans votre implémentation. Par exemple, la <xref:System.Windows.Controls.DockPanel.GetDock%2A?displayProperty=nameWithType> méthode type le paramètre en tant que <xref:System.Windows.UIElement> , car la propriété jointe est uniquement destinée à être définie sur des <xref:System.Windows.UIElement> instances.

- La valeur de retour peut être spécifiée comme un type plus spécifique dans votre implémentation. Par exemple, la <xref:System.Windows.Controls.DockPanel.GetDock%2A> méthode le type comme <xref:System.Windows.Controls.Dock> , car la valeur ne peut être définie que sur cette énumération.

#### <a name="the-set-accessor"></a>Accesseur Set

La signature de l’accesseur **Set_PropertyName_** doit être :

`public static void SetPropertyName(object target, object value)`

- L’objet `target` peut être défini comme un type plus spécifique dans votre implémentation. Par exemple, la <xref:System.Windows.Controls.DockPanel.SetDock%2A> méthode le type comme <xref:System.Windows.UIElement> , car la propriété jointe est uniquement destinée à être définie sur des <xref:System.Windows.UIElement> instances.

- L’objet `value` peut être défini comme un type plus spécifique dans votre implémentation. Par exemple, la <xref:System.Windows.Controls.DockPanel.SetDock%2A> méthode le type comme <xref:System.Windows.Controls.Dock> , car la valeur ne peut être définie que sur cette énumération. N’oubliez pas que la valeur de cette méthode est l’entrée provenant du chargeur XAML quand il rencontre votre propriété jointe dans une utilisation des propriétés jointes dans le balisage. Cette entrée est la valeur spécifiée comme valeur d’attribut XAML dans le balisage. Ainsi, la conversion de type, la sérialisation de valeur ou l’extension de balisage doit être prise en charge pour le type utilisé afin que le type approprié puisse être créé à partir de la valeur d’attribut (laquelle est en fin de compte une simple chaîne).

L’exemple suivant montre l’inscription de la propriété de dépendance (à l’aide de la <xref:System.Windows.DependencyProperty.RegisterAttached%2A> méthode), ainsi que les accesseurs **Get_PropertyName_** et **Set_PropertyName_** . Dans cet exemple, le nom de la propriété jointe est `IsBubbleSource`. Les accesseurs doivent donc être nommés `GetIsBubbleSource` et `SetIsBubbleSource`.

[!code-csharp[WPFAquariumSln#RegisterAttachedBubbler](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#registerattachedbubbler)]
[!code-vb[WPFAquariumSln#RegisterAttachedBubbler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#registerattachedbubbler)]

#### <a name="attached-property-attributes"></a>Attributs des propriétés jointes

WPF définit plusieurs attributs .NET qui sont destinés à fournir des informations sur les propriétés jointes aux processus de réflexion, ainsi qu’aux utilisateurs typiques de la réflexion et des informations de propriété telles que les concepteurs. Les propriétés jointes ayant un type de portée illimitée, les concepteurs ont besoin d’un moyen d’éviter que les utilisateurs croulent sous une liste globale de toutes les propriétés jointes qui sont définies dans l’implémentation d’une technologie particulière utilisant XAML. Les attributs .NET que WPF définit pour les propriétés jointes peuvent être utilisés pour définir la portée des situations où une propriété jointe donnée doit être affichée dans une fenêtre de propriétés. Vous pouvez également envisager l’application de ces attributs à vos propres propriétés jointes personnalisées. L’objectif et la syntaxe des attributs .NET sont décrits dans les pages de référence appropriées :

- <xref:System.Windows.AttachedPropertyBrowsableAttribute>

- <xref:System.Windows.AttachedPropertyBrowsableForChildrenAttribute>

- <xref:System.Windows.AttachedPropertyBrowsableForTypeAttribute>

- <xref:System.Windows.AttachedPropertyBrowsableWhenAttributePresentAttribute>

## <a name="learning-more-about-attached-properties"></a>En savoir plus sur les propriétés jointes<a name="more"></a>

- Pour plus d’informations sur la création d’une propriété jointe, consultez [Enregistrer une propriété jointe](how-to-register-an-attached-property.md).

- Pour obtenir des scénarios d’usage avancés des propriétés de dépendance et des propriétés jointes, consultez [Propriétés de dépendance personnalisées](custom-dependency-properties.md).

- Vous pouvez également enregistrer une propriété en tant que propriété jointe et que propriété de dépendance ; mais dans cette situation, vous exposez encore les implémentations de « wrapper ». Dans ce cas, vous pouvez définir la propriété soit sur cet élément, soit sur tout élément par le biais de la syntaxe de propriété jointe XAML. Un exemple de propriété avec un scénario approprié pour les utilisations standard et attachées est <xref:System.Windows.FrameworkElement.FlowDirection%2A?displayProperty=nameWithType> .

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.DependencyProperty>
- [Vue d’ensemble des propriétés de dépendance](dependency-properties-overview.md)
- [Propriétés de dépendance personnalisées](custom-dependency-properties.md)
- [Vue d’ensemble du langage XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Enregistrer une propriété jointe](how-to-register-an-attached-property.md)
