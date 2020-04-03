---
title: Vue d’ensemble des propriétés de dépendance
description: Une propriété qui repose sur le système de propriété WPF s’appelle une propriété de dépendance. Cette vue d’ensemble décrit le système de propriétés WPF et les fonctionnalités d’une propriété de dépendance.
ms.date: 06/06/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- properties [WPF], attached
- properties [WPF], overview
- styles [WPF]
- attached properties [WPF]
- data binding [WPF]
- dependency properties [WPF]
- resources [WPF], references to
ms.assetid: d119d00c-3afb-48d6-87a0-c4da4f83dee5
ms.openlocfilehash: 542e0a84e4c5cfc3750c33fe29cb40d3643e91e3
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/03/2020
ms.locfileid: "80636030"
---
# <a name="dependency-properties-overview"></a>Vue d’ensemble des propriétés de dépendance

WPF (Windows Presentation Foundation) fournit un ensemble de services qui permettent d’étendre la fonctionnalité de la [propriété](../../../standard/base-types/common-type-system.md#properties) d’un type. Ces services sont généralement regroupés sous le nom « système de propriétés WPF ». Une propriété qui repose sur le système de propriété WPF s’appelle une propriété de dépendance. Cette vue d’ensemble décrit le système de propriétés WPF et les fonctionnalités d’une propriété de dépendance. notamment comment utiliser les propriétés de dépendance existantes en XAML et dans le code. Elle introduit également des aspects spécialisés des propriétés de dépendance, tels que les métadonnées de propriétés de dépendance et comment créer votre propre propriété de dépendance dans une classe personnalisée.

## <a name="prerequisites"></a>Prérequis
Cette rubrique part du principe que vous avez des connaissances de base relatives au système de types .NET et à la programmation orientée objet. Pour pouvoir suivre les exemples de cette rubrique, vous devez également comprendre le langage XAML et savoir comment écrire des applications WPF. Pour plus d’informations, consultez [Procédure pas à pas : ma première application de bureau WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md).  
  
## <a name="dependency-properties-and-clr-properties"></a>Propriétés de dépendance et propriétés CLR
 Dans WPF, les propriétés sont généralement exposées en tant que [propriétés](../../../standard/base-types/common-type-system.md#properties) .NET standard. À un niveau basique, vous pourriez interagir directement avec ces propriétés et ne jamais savoir qu’elles sont implémentées en tant que propriétés de dépendance. Toutefois, vous devez vous familiariser avec une partie ou l’ensemble des fonctionnalités du système de propriétés WPF pour pouvoir tirer parti de ces fonctionnalités.

Les propriétés de dépendance ont pour but de fournir un moyen de calculer la valeur d’une propriété en fonction de la valeur d’autres entrées. Ces autres entrées peuvent inclure des propriétés système telles que des thèmes et des préférences de l’utilisateur, des mécanismes de détermination de propriété juste-à-temps tels que la liaison de données et les animations/plans conceptuels, des modèles à plusieurs usages comme les ressources et les styles, ou des valeurs connues par l’intermédiaire de relations parent-enfant avec d’autres éléments dans l’arborescence d’éléments. En outre, une propriété de dépendance peut être implémentée pour fournir une validation autonome, des valeurs par défaut, des rappels qui surveillent les modifications apportées à d’autres propriétés, et un système capable de forcer des valeurs de propriétés en fonction d’informations d’exécution potentielles. Les classes dérivées peuvent également changer certaines caractéristiques spécifiques d’une propriété existante en substituant les métadonnées de propriété de dépendance, plutôt qu’en substituant l’implémentation réelle des propriétés existantes ou en créant de nouvelles propriétés.

Dans la référence du SDK, vous pouvez identifier quelle propriété est une propriété de dépendance par la présence de la section Informations sur les propriétés de dépendance dans la page de référence managée de cette propriété. La section des informations sur les propriétés de dépendance comprend un lien vers l’identificateur de champ <xref:System.Windows.DependencyProperty> pour cette propriété de dépendance, ainsi qu’une liste d’options de métadonnées définies pour cette propriété, des informations de substitution par classe et d’autres détails.

## <a name="dependency-properties-back-clr-properties"></a>Les propriétés CLR reposent sur les propriétés de dépendance
Les propriétés de dépendance et le système de propriétés WPF étendent la fonctionnalité des propriétés en fournissant un type qui prend en charge une propriété, en tant qu’implémentation alternative du modèle standard de stockage de la propriété avec un champ privé. Le nom de ce type est <xref:System.Windows.DependencyProperty>. L’autre type important qui définit le système de propriétés WPF est <xref:System.Windows.DependencyObject>. <xref:System.Windows.DependencyObject> définit la classe de base qui peut inscrire et détenir une propriété de dépendance.

Voici une liste qui décrit la terminologie utilisée avec les propriétés de dépendance :

- **Propriété de dépendance :** propriété qui repose sur un <xref:System.Windows.DependencyProperty>.

- **Identificateur de propriété de dépendance :** instance de <xref:System.Windows.DependencyProperty> obtenue en tant que valeur retournée durant l’inscription d’une propriété de dépendance, puis stockée en tant que membre statique d’une classe. Cet identificateur est utilisé en tant que paramètre pour la plupart des API qui interagissent avec le système de propriétés WPF.

- **« wrapper » CLR :** implémentations get et set pour la propriété. Ces implémentations incorporent l’identificateur de propriété de dépendance en l’utilisant dans les appels de <xref:System.Windows.DependencyObject.GetValue%2A> et <xref:System.Windows.DependencyObject.SetValue%2A>, ce qui assure ainsi le stockage de la propriété à l’aide du système de propriétés WPF.

L’exemple suivant définit la propriété de dépendance `IsSpinning` et montre la relation entre l’identificateur <xref:System.Windows.DependencyProperty> et la propriété qu’il prend en charge.

[!code-csharp[PropertiesOvwSupport#DPFormBasic](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#dpformbasic)]
[!code-vb[PropertiesOvwSupport#DPFormBasic](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#dpformbasic)]  
  
La convention de nommage de la propriété et de son champ <xref:System.Windows.DependencyProperty> de stockage est importante. Le nom du champ est toujours le nom de la propriété, auquel est ajouté le suffixe `Property`. Pour plus d’informations sur cette convention et sur sa raison d’être, consultez [Propriétés de dépendance personnalisées](custom-dependency-properties.md).  

## <a name="setting-property-values"></a>Définition de valeurs de propriété
Vous pouvez définir des propriétés dans le code ou en XAML.

### <a name="setting-property-values-in-xaml"></a>Définition de valeurs de propriété en XAML
L’exemple XAML suivant spécifie le rouge comme couleur d’arrière-plan d’un bouton. Cet exemple illustre un cas où le type d’une valeur de chaîne simple d’un attribut XAML est converti par l’analyseur XAML WPF en type WPF (<xref:System.Windows.Media.Color> via <xref:System.Windows.Media.SolidColorBrush>) dans le code généré.

[!code-xaml[PropertiesOvwSupport#MostBasicProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/Page1.xaml#mostbasicproperty)]

XAML prend en charge diverses formes de syntaxe pour définir les propriétés. La syntaxe à utiliser pour une propriété particulière varie en fonction du type de valeur utilisé par une propriété, ainsi que d’autres facteurs tels que la présence d’un convertisseur de type. Pour plus d’informations sur la syntaxe XAML pour la définition de propriété, consultez [Vue d’ensemble du langage XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md) et [Syntaxe XAML en détail](xaml-syntax-in-detail.md).

En guise d’exemple de syntaxe de non-attribut, l’exemple XAML suivant montre un autre arrière-plan de bouton. Cette fois-ci, au lieu de définir une couleur unie, l’arrière-plan est défini sur une image, avec un élément représentant cette image et la source de cette image spécifiée en tant qu’attribut de l’élément imbriqué. Il s’agit d’un exemple de syntaxe d’éléments de propriété.

[!code-xaml[PropertiesOvwSupport#PESyntaxProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/Page1.xaml#pesyntaxproperty)]

### <a name="setting-properties-in-code"></a>Définition de propriétés dans le code
 Définir la valeur des propriétés de dépendance dans le code n’est généralement qu’un appel à la mise en œuvre définie exposée par le « wrapper » du CLR.

[!code-csharp[PropertiesOvwSupport#ProceduralPropertySet](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/Page1.xaml.cs#proceduralpropertyset)]
[!code-vb[PropertiesOvwSupport#ProceduralPropertySet](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page1.xaml.vb#proceduralpropertyset)]

Pour obtenir une valeur de propriété, il suffit aussi généralement d’appeler l’implémentation « wrapper » Get :

[!code-csharp[PropertiesOvwSupport#ProceduralPropertyGet](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/Page1.xaml.cs#proceduralpropertyget)]
 [!code-vb[PropertiesOvwSupport#ProceduralPropertyGet](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page1.xaml.vb#proceduralpropertyget)]

Vous pouvez également appeler le <xref:System.Windows.DependencyObject.GetValue%2A> <xref:System.Windows.DependencyObject.SetValue%2A> système de propriété API et directement. Ce n’est généralement pas nécessaire si vous utilisez les propriétés existantes (les emballages sont plus pratiques, et de fournir une meilleure exposition de la propriété pour les outils de développeur), mais appeler les API directement est approprié pour certains scénarios.

Vous pouvez aussi définir les propriétés en XAML et y accéder ultérieurement dans le code, par l’intermédiaire du code-behind. Pour plus d’informations, consultez [Code-behind et XAML dans WPF](code-behind-and-xaml-in-wpf.md).

## <a name="property-functionality-provided-by-a-dependency-property"></a>Fonctionnalité de propriété fournie par une propriété de dépendance
Une propriété de dépendance fournit une fonctionnalité qui étend la fonctionnalité d’une propriété, par opposition à une propriété qui est stockée par un champ. Souvent, une telle fonctionnalité représente ou prend en charge l’une des fonctionnalités spécifiques suivantes :

- [Ressources](#resources)

- [Liaison de données](#data-binding)

- [Styles](#styles)

- [Animations](#animations)

- [Substitutions de métadonnées](#metadata-overrides)

- [Héritage de valeur de propriété](#property-value-inheritance)

- [Intégration WPF Designer](#wpf-designer-integration)

### <a name="resources"></a>Ressources
Une valeur de propriété de dépendance peut être définie en référençant une ressource. Les ressources sont généralement spécifiées en tant que valeur de propriété `Resources` d’un élément racine de page ou de l’application (ces emplacements autorisent l’accès le plus commode à la ressource). L’exemple suivant montre comment définir une ressource <xref:System.Windows.Media.SolidColorBrush>.

[!code-xaml[PropertiesOvwSupport#ResourcesResource](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page2.xaml#resourcesresource)]

Une fois la ressource définie, vous pouvez la référencer et l’utiliser pour fournir une valeur de propriété :

[!code-xaml[PropertiesOvwSupport#ResourcesReference](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page2.xaml#resourcesreference)]

Cette ressource particulière est référencée en tant qu’[Extension de balisage DynamicResource](dynamicresource-markup-extension.md) (en XAML WPF, vous pouvez utiliser une référence de ressource statique ou dynamique). Pour utiliser une référence de ressource dynamique, vous devez définir une propriété de dépendance. Ainsi, l’utilisation de la référence de ressource dynamique est activée spécifiquement par le système de propriétés WPF. Pour plus d’informations, consultez [Ressources XAML](xaml-resources.md).

> [!NOTE]
> Les ressources sont traitées comme une valeur locale, ce qui signifie que si vous définissez une autre valeur locale, vous supprimez la référence de ressource. Pour plus d’informations, consultez [Priorité de la valeur de propriété de dépendance](dependency-property-value-precedence.md).

### <a name="data-binding"></a>Liaison de données
Une propriété de dépendance peut référencer une valeur par l’intermédiaire d’une liaison de données. La liaison de données fonctionne via une syntaxe d’extension de balisage spécifique en XAML, ou via l’objet <xref:System.Windows.Data.Binding> dans du code. Avec la liaison de données, la détermination de valeur de propriété finale est différée jusqu’au moment de l’exécution, quand la valeur est obtenue à partir d’une source de données.

L’exemple suivant définit la propriété <xref:System.Windows.Controls.ContentControl.Content%2A> de <xref:System.Windows.Controls.Button> à l’aide d’une liaison déclarée en XAML. La liaison utilise un contexte de données hérité et une source de données <xref:System.Windows.Data.XmlDataProvider> (non illustrée). La liaison proprement dite spécifie la propriété source souhaitée par <xref:System.Windows.Data.Binding.XPath%2A> dans la source de données.

[!code-xaml[PropertiesOvwSupport#BasicInlineBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#basicinlinebinding)]

> [!NOTE]
> Les liaisons sont traitées comme une valeur locale, ce qui signifie que si vous définissez une autre valeur locale, vous supprimez la liaison. Pour plus d’informations, consultez [Priorité de la valeur de propriété de dépendance](dependency-property-value-precedence.md).

Les propriétés de dépendance, ou la classe <xref:System.Windows.DependencyObject>, ne prennent pas en charge <xref:System.ComponentModel.INotifyPropertyChanged> de manière native afin de notifier les changements de valeurs de la propriété source <xref:System.Windows.DependencyObject> pour les opérations de liaison de données. Pour plus d’informations sur la façon de créer (pour une utilisation dans la liaison de données)' des propriétés capables de signaler des changements de cible de liaison de données, consultez [Vue d’ensemble de la liaison de données](../data/data-binding-overview.md).

### <a name="styles"></a>Styles
Les styles et modèles sont deux des principaux scénarios justifiant l’utilisation de propriétés de dépendance. Les styles sont particulièrement utiles pour configurer des propriétés qui définissent l’[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] de l’application. Ils sont généralement définis en tant que ressources en XAML. Ils interagissent avec le système de propriétés car ils contiennent généralement des « méthodes setter » pour des propriétés particulières, ainsi que des « déclencheurs » qui changent une valeur de propriété d’après la valeur en temps réel d’une autre propriété.

L’exemple suivant crée un style simple <xref:System.Windows.FrameworkElement.Resources%2A> (qui serait défini à l’intérieur <xref:System.Windows.FrameworkElement.Style%2A> d’un dictionnaire, non montré), puis applique ce style directement à la propriété pour un <xref:System.Windows.Controls.Button>. La méthode setter contenue dans le style définit la propriété <xref:System.Windows.Controls.Control.Background%2A> pour un <xref:System.Windows.Controls.Button> mis en vert.

[!code-xaml[PropertiesOvwSupport#SimpleStyleDef](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#simplestyledef)]

[!code-xaml[PropertiesOvwSupport#SimpleStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#simplestyle)]

Pour plus d’informations, consultez [Application d’un style et création de modèles](../controls/styling-and-templating.md).

### <a name="animations"></a>Animations
Les propriétés de dépendance peuvent être animées. Quand une animation est appliquée et s’exécute, la valeur animée opère à une priorité plus élevée que toute autre valeur (par exemple une valeur locale) qu’aurait normalement la propriété.

L’exemple suivant anime <xref:System.Windows.Controls.Control.Background%2A> sur une propriété <xref:System.Windows.Controls.Button> (techniquement, il anime <xref:System.Windows.Controls.Control.Background%2A> à l’aide de la syntaxe d’élément de propriété pour spécifier un <xref:System.Windows.Media.SolidColorBrush> vide en tant que <xref:System.Windows.Controls.Control.Background%2A>, puis la propriété <xref:System.Windows.Media.SolidColorBrush.Color%2A> de <xref:System.Windows.Media.SolidColorBrush> est directement animée).

[!code-xaml[PropertiesOvwSupport#MiniAnimate](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#minianimate)]

Pour plus d’informations sur l’animation de propriétés, consultez [Vue d’ensemble des animations](../graphics-multimedia/animation-overview.md) et [Vue d’ensemble des plans conceptuels](../graphics-multimedia/storyboards-overview.md).

### <a name="metadata-overrides"></a>Substitutions de métadonnées
Vous pouvez changer certains comportements d’une propriété de dépendance en substituant les métadonnées de cette propriété quand vous dérivez de la classe qui inscrit initialement la propriété de dépendance. La substitution de métadonnées repose sur l’identificateur <xref:System.Windows.DependencyProperty>. Les métadonnées primordiales ne nécessitent pas la réimplantation de la propriété. Le changement de métadonnées est géré de manière native par le système de propriétés. Chaque classe contient potentiellement des métadonnées individuelles pour toutes les propriétés qui sont héritées des classes de base, sur la base de chaque type.

L’exemple suivant remplace les métadonnées d’une propriété de dépendance <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A>. La substitution de ces métadonnées de propriété de dépendance particulières fait partie d’un modèle d’implémentation qui crée des contrôles capables d’utiliser les styles par défaut de thèmes.

[!code-csharp[PropertiesOvwSupport#OverrideMetadata](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml.cs#overridemetadata)]
[!code-vb[PropertiesOvwSupport#OverrideMetadata](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page3.xaml.vb#overridemetadata)]

Pour plus d’informations sur la substitution ou l’obtention de métadonnées de propriété, consultez [Métadonnées de propriété de dépendance](dependency-property-metadata.md).

### <a name="property-value-inheritance"></a>Héritage d’une valeur de propriété
Un élément peut hériter de la valeur d’une propriété de dépendance de son parent dans l’arborescence d’objets.

> [!NOTE]
> Le comportement d’héritage de valeur de propriété n’est pas activé globalement pour toutes les propriétés de dépendance, car le temps de calcul pour l’héritage a un certain impact sur les performances. L’héritage de valeur de propriété est en général activé uniquement pour les propriétés où un scénario particulier suggère que l’héritage de valeur de propriété est appropriée. Vous pouvez déterminer si une propriété de dépendance hérite en consultant la section **Informations sur les propriétés de dépendance** de cette propriété de dépendance dans la référence du SDK.

L’exemple suivant illustre une liaison et définit la propriété <xref:System.Windows.FrameworkElement.DataContext%2A> qui spécifie la source de la liaison, ce qui n’était pas montré dans l’exemple de liaison précédent. Les liaisons suivantes dans les objets enfants n’ont pas besoin de spécifier la source. Elles peuvent utiliser la valeur héritée de <xref:System.Windows.FrameworkElement.DataContext%2A> dans l’objet <xref:System.Windows.Controls.StackPanel> parent. (En guise d’alternative, un objet enfant peut choisir de spécifier directement son propre <xref:System.Windows.FrameworkElement.DataContext%2A> ou un <xref:System.Windows.Data.Binding.Source%2A> dans <xref:System.Windows.Data.Binding>, et d’éviter délibérément d’utiliser la valeur héritée pour le contexte de données de ses liaisons.)

[!code-xaml[PropertiesOvwSupport#InheritanceContext](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#inheritancecontext)]

Pour plus d’informations, consultez [Héritage de valeur de propriété](property-value-inheritance.md).

### <a name="wpf-designer-integration"></a>Intégration du concepteur WPF
Un contrôle personnalisé avec des propriétés qui sont mises en œuvre en tant que propriétés de dépendance recevra le concepteur WPF approprié pour le support visual studio. La possibilité de modifier des propriétés de dépendance directes et jointes avec la fenêtre **Propriétés** constitue un bon exemple. Pour plus d’informations, consultez [Vue d’ensemble de la création de contrôles](../controls/control-authoring-overview.md).

## <a name="dependency-property-value-precedence"></a>Priorité de la valeur d’une propriété de dépendance
Quand vous obtenez la valeur d’une propriété de dépendance, vous obtenez potentiellement une valeur définie pour cette propriété via l’une des autres entrées basées sur des propriétés qui participent au système de propriétés WPF. Il existe une priorité de valeur de propriété de dépendance, afin que différents scénarios d’obtention des valeurs par les propriétés puissent interagir de manière prévisible.

Considérez l'exemple suivant. L’exemple inclut un style qui s’applique à tous les boutons et à leurs propriétés <xref:System.Windows.Controls.Control.Background%2A>. Toutefois, il spécifie également un bouton avec une valeur <xref:System.Windows.Controls.Control.Background%2A> définie localement.

> [!NOTE]
> La documentation du SDK utilise les termes « valeur locale » ou « valeur localement définie » occasionnellement lors de la discussion des propriétés de dépendance. Une valeur localement définie est une valeur de propriété qui est définie directement sur une instance d’objet dans le code, ou en tant qu’attribut d’élément en XAML.  
  
En principe, pour le premier bouton, la propriété est définie à deux reprises, mais une seule valeur est applicable : celle ayant la priorité la plus élevée. Une valeur localement définie a la priorité la plus élevée (sauf une animation en cours d’exécution, mais aucune animation n’est applicable dans cet exemple). La valeur localement définie est donc utilisée au lieu de la valeur du Style Setter pour l’arrière-plan du premier bouton. Le deuxième bouton n’a aucune valeur locale (et aucune autre valeur ayant une priorité supérieure à celle d’un Style Setter). Par conséquent, l’arrière-plan de ce bouton provient du Style Setter.

[!code-xaml[PropertiesOvwSupport#MiniPrecedence](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#miniprecedence)]  

### <a name="why-does-dependency-property-precedence-exist"></a>Pourquoi la priorité des propriétés de dépendance existe-t-elle ?
Typiquement, vous ne voudriez pas que les styles s’appliquent toujours et obscurcissent même une valeur définie localement d’un élément individuel (sinon, il serait difficile d’utiliser des styles ou des éléments en général). Par conséquent, les valeurs qui proviennent de styles opèrent à une priorité plus faible que les valeurs définies localement. Pour obtenir une liste plus complète de propriétés de dépendance et pour savoir d’où la valeur effective d’une propriété de dépendance peut provenir, consultez [Priorité de la valeur de propriété de dépendance](dependency-property-value-precedence.md).

> [!NOTE]
> Un certain nombre de propriétés définies sur des éléments WPF ne sont pas des propriétés de dépendance. De manière générale, les propriétés ont été implémentées en tant que propriétés de dépendance uniquement quand il fallait prendre en charge au moins l’un des scénarios activés par le système de propriétés : liaison de données, styles, animation, prise en charge de valeur par défaut, héritage, propriétés jointes ou invalidation.

## <a name="learning-more-about-dependency-properties"></a>En savoir plus sur les propriétés de dépendance  

- Une propriété jointe est un type de propriété qui prend en charge une syntaxe spécialisée en XAML. Une propriété jointe n’a souvent pas de correspondance de 1:1 avec une propriété commune de temps d’exécution de langue (CLR), et n’est pas nécessairement une propriété de dépendance. Le but typique d’une propriété jointe est de permettre aux éléments pour enfants de déclarer la valeur des propriétés à un élément parent, même si l’élément parent et l’élément enfant ne possèdent pas tous les deux cette propriété dans le cadre des listes des membres du groupe. L’un des principaux scénarios consiste à permettre aux éléments enfants d’indiquer au parent comment ils doivent être présentés dans [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Pour obtenir un exemple, consultez <xref:System.Windows.Controls.DockPanel.Dock%2A> ou <xref:System.Windows.Controls.Canvas.Left%2A>. Pour plus d’informations, consultez [Vue d’ensemble des propriétés jointes](attached-properties-overview.md).

- Les développeurs de composants ou d’applications peuvent souhaiter créer leur propre propriété de dépendance, afin d’activer des fonctionnalités telles que la liaison de données ou la prise en charge des styles, ou pour prendre en charge l’invalidation et le forçage de valeur. Pour plus d’informations, consultez [Propriétés de dépendance personnalisées](custom-dependency-properties.md).

- Considérez les propriétés de dépendance comme des propriétés publiques, accessibles ou du moins détectables par tout appelant qui a accès à une instance. Pour plus d’informations, consultez [Sécurité des propriétés de dépendance](dependency-property-security.md).

## <a name="see-also"></a>Voir aussi

- [Propriétés de dépendance personnalisées](custom-dependency-properties.md)
- [Propriétés de dépendance en lecture seule](read-only-dependency-properties.md)
- [Vue d’ensemble du langage XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Architecture de WPF](wpf-architecture.md)
