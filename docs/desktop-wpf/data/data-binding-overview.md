---
title: Vue d’ensemble de la liaison de données
description: En savoir plus sur les différentes sources de données que vous pouvez ajouter à votre projet dans Windows Presentation Foundation pour .NET Core. Les sources de données peuvent être liées à des éléments XAML pour créer des applications dynamiques.
author: adegeo
ms.date: 09/19/2019
ms.author: adegeo
dev_langs:
- csharp
- vb
ms.openlocfilehash: 829c93e97990b87e6e568614236de9708ef080d9
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325757"
---
# <a name="data-binding-overview-in-wpf"></a>Vue d’ensemble de la liaison de données dans WPF

La liaison de données dans Windows Presentation Foundation (WPF) offre un moyen simple et cohérent pour les applications de présenter et d’interagir avec les données. Les éléments peuvent être liés à des données provenant de diverses sources de données sous la forme d’objets .NET et XML. Tout comme <xref:System.Windows.Controls.ContentControl> <xref:System.Windows.Controls.Button> et tout <xref:System.Windows.Controls.ItemsControl> , tels que <xref:System.Windows.Controls.ListBox> et <xref:System.Windows.Controls.ListView> , ont des fonctionnalités intégrées permettant d’activer le style flexible des éléments de données uniques ou des collections d’éléments de données. Des vues de tri, filtrage et groupage peuvent être générées sur la base des données.

La fonctionnalité de liaison de données dans WPF présente plusieurs avantages par rapport aux modèles traditionnels, notamment la prise en charge inhérente de la liaison de données par un large éventail de propriétés, une représentation d’interface utilisateur flexible des données et une séparation nette de la logique métier de l’interface utilisateur.

Cet article aborde tout d’abord les concepts fondamentaux de la liaison de données WPF, puis couvre l’utilisation de la <xref:System.Windows.Data.Binding> classe et d’autres fonctionnalités de la liaison de données.

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="what-is-data-binding"></a>Qu’est-ce que la liaison de données ?

La liaison de données est le processus qui établit une connexion entre l’interface utilisateur de l’application et les données qu’elle affiche. Si la liaison est correctement paramétrée et si les données fournissent les notifications appropriées, lorsque les données changent de valeur, les éléments qui sont liés aux données reflètent automatiquement ces changements. La liaison de données peut également signifier que si une représentation externe des données dans un élément change, les données sous-jacentes peuvent être automatiquement mises à jour pour refléter les modifications. Par exemple, si l’utilisateur modifie la valeur dans un `TextBox` élément, la valeur de données sous-jacente est automatiquement mise à jour pour refléter cette modification.

Une utilisation classique de la liaison de données consiste à placer des données de configuration de serveur ou locales dans des formulaires ou d’autres contrôles d’interface utilisateur. Dans WPF, ce concept est étendu pour inclure la liaison d’une large gamme de propriétés à une variété de sources de données. Dans WPF, les propriétés de dépendance des éléments peuvent être liées aux objets .NET (y compris les objets ADO.NET ou les objets associés aux services Web et aux propriétés Web) et aux données XML.

Pour obtenir un exemple de liaison de données, jetez un coup d’œil à l’interface utilisateur de l’application suivante à partir de la [démonstration liaison de données][data-binding-demo], qui affiche la liste des éléments d’enchères.

![Capture d’écran exemple de liaison de données](./media/data-binding-overview/demo.png "DataBinding_DataBindingDemo")

L’application illustre les fonctionnalités de liaison de données suivantes :

- Le contenu de la zone de liste est lié à une collection d’objets *AuctionItem* . Un *objet AuctionItem* possède des propriétés telles que *Description*, *StartPrice*, *StartDate*, *Category*, *SpecialFeatures*, et ainsi de suite.

- Les données (objets*AuctionItem* ) affichées dans le `ListBox` sont basées sur un modèle, de sorte que la description et le prix actuel sont affichés pour chaque élément. Le modèle est créé à l’aide d’un <xref:System.Windows.DataTemplate> . En outre, l’apparence de chaque élément varie selon la valeur de *SpecialFeatures* de *l’AuctionItem* affiché. Si la valeur *SpecialFeatures* de *AuctionItem* est *Color*, l’élément a une bordure bleue. Si la valeur est *Highlight*, l’élément a une bordure orange et une étoile. La section [Modèles de données](#data-templating) fournit des informations sur les modèles de données.

- L’utilisateur peut regrouper, filtrer ou trier les données à l’aide du `CheckBoxes` fourni. Dans l’image ci-dessus, les catégories **Grouper par** et **Trier par catégorie et date** `CheckBoxes` sont sélectionnées. Vous avez peut-être remarqué que les données sont regroupées en fonction de la catégorie de produit et que les noms de catégorie sont dans l’ordre alphabétique. Cela est difficile à observer sur l’image, mais les éléments sont également triés par date de début dans chaque catégorie. Le tri s’effectue à l’aide d’une *vue de collection*. La section [liaison à des collections](#binding-to-collections) traite des vues de collection.

- Lorsque l’utilisateur sélectionne un élément, <xref:System.Windows.Controls.ContentControl> affiche les détails de l’élément sélectionné. Cette expérience est appelée *scénario maître/détail*. La section du [scénario maître/détail](#master-detail-binding-scenario) fournit des informations sur ce type de liaison.

- Le type de la propriété *StartDate* est <xref:System.DateTime> , qui retourne une date qui comprend l’heure à la milliseconde. Dans cette application, un convertisseur personnalisé a été utilisé afin d’afficher une chaîne de date plus petite. La section [conversion de données](#data-conversion) fournit des informations sur les convertisseurs.

Quand l’utilisateur sélectionne le bouton *Ajouter un produit* , le formulaire suivant apparaît.

![Page Ajouter la liste de produits](./media/data-binding-overview/demo-addproductlisting.png "DataBinding_Demo_AddProductListing")

L’utilisateur peut modifier les champs du formulaire, afficher un aperçu de la liste des produits à l’aide des volets d’aperçu courts ou détaillés, puis sélectionner `Submit` cette option pour ajouter la nouvelle liste de produits. Les paramètres de regroupement, de filtrage et de tri existants s’appliquent à la nouvelle entrée. Dans ce cas particulier, l’élément entré dans l’image ci-dessus s’affichera comme deuxième élément dans la catégorie *Computer*.

La logique de validation fournie dans la *Date de début* n’est pas illustrée dans cette image <xref:System.Windows.Controls.TextBox> . Si l’utilisateur entre une date non valide (mise en forme non valide ou date passée), l’utilisateur est averti avec un <xref:System.Windows.Controls.ToolTip> et un point d’exclamation rouge à côté de <xref:System.Windows.Controls.TextBox> . La section [Validation des données](#data-validation) explique comment créer une logique de validation.

Avant de passer aux différentes fonctionnalités de la liaison de données décrites ci-dessus, nous aborderons tout d’abord les concepts fondamentaux qui sont essentiels à la compréhension de la liaison de données WPF.

## <a name="basic-data-binding-concepts"></a>Concepts de base de la liaison de données

Quel que soit l’élément que vous liez et la nature de votre source de données, chaque liaison suit toujours le modèle illustré par la figure suivante.

![Diagramme qui montre le modèle de liaison de données de base.](./media/data-binding-overview/basic-data-binding-diagram.png)

Comme le montre la figure, la liaison de données est essentiellement le pont entre votre cible de liaison et votre source de liaison. La figure illustre les concepts fondamentaux de liaison de données WPF suivants :

- En règle générale, chaque liaison a quatre composants :

  - Objet de cible de liaison.
  - Propriété cible.
  - Une source de liaison.
  - Chemin d’accès à la valeur dans la source de liaison à utiliser.
  
  > Par exemple, si vous souhaitez lier le contenu d’un `TextBox` à la `Employee.Name` propriété, votre objet cible est `TextBox` , la propriété cible est la <xref:System.Windows.Controls.TextBox.Text%2A> propriété, la valeur à utiliser est *Name*et l’objet source est l’objet *Employee* .

- La propriété cible doit être une propriété de dépendance. La plupart des <xref:System.Windows.UIElement> propriétés sont des propriétés de dépendance, et la plupart des propriétés de dépendance, à l’exception de celles en lecture seule, prennent en charge la liaison de données par défaut. (Seuls les types dérivés de <xref:System.Windows.DependencyObject> peuvent définir des propriétés de dépendance, et tous les types dérivés <xref:System.Windows.UIElement> de `DependencyObject` .)

- Bien que cela ne soit pas illustré dans la figure, il convient de noter que l’objet de source de liaison n’est pas limité à un objet .NET personnalisé. La liaison de données WPF prend en charge les données sous la forme d’objets .NET et XML. Pour fournir quelques exemples, votre source de liaison peut être un objet de liste, un objet de <xref:System.Windows.UIElement> liste, un ADO.net ou un objet de services Web, ou un XmlNode qui contient vos données XML. Pour plus d’informations, consultez [vue d’ensemble des sources de liaison](../../framework/wpf/data/binding-sources-overview.md).

Il est important de se souvenir que lorsque vous établissez une liaison, vous liez une cible *de liaison à* une source de liaison. Par exemple, si vous affichez des données XML sous-jacentes dans un <xref:System.Windows.Controls.ListBox> à l’aide de la liaison de données, vous liez votre `ListBox` aux données XML.

Pour établir une liaison, vous utilisez l' <xref:System.Windows.Data.Binding> objet. Le reste de cet article traite de la plupart des concepts associés à et de certaines des propriétés et de l’utilisation de l' `Binding` objet.

### <a name="direction-of-the-data-flow"></a>Direction du Workflow

Comme indiqué par la flèche de la figure précédente, le workflow d’une liaison peut passer de la cible de liaison à la source de liaison (par exemple, la valeur source change lorsqu’un utilisateur modifie la valeur d’un `TextBox` ) et/ou de la source de liaison vers la cible de liaison (par exemple, votre `TextBox` contenu est mis à jour avec les modifications dans la source de liaison) si la source de liaison fournit les notifications appropriées.

Vous souhaiterez peut-être que votre application permette aux utilisateurs de modifier les données et de les propager vers l’objet source. Ou vous souhaitez peut-être ne pas permettre aux utilisateurs de mettre à jour la source de données. Vous pouvez contrôler le workflow de données en définissant <xref:System.Windows.Data.Binding.Mode?displayProperty=nameWithType> .

Cette figure illustre les différents types de workflows de données :

![Flux de données de la liaison de données](./media/data-binding-overview/databinding-dataflow.png "DataBinding_DataFlow")

- <xref:System.Windows.Data.BindingMode.OneWay>la liaison entraîne la mise à jour automatique de la propriété cible par les modifications apportées à la propriété source, mais les modifications apportées à la propriété cible ne sont pas propagées vers la propriété source. Ce type de liaison est approprié si le contrôle lié est implicitement en lecture seule. Par exemple, vous pouvez créer une liaison à une source telle qu’un ticker de stock ou peut-être que votre propriété cible n’a pas d’interface de contrôle fournie pour apporter des modifications, comme une couleur d’arrière-plan liée aux données d’une table. S’il n’est pas nécessaire de surveiller les modifications de la propriété cible, l’utilisation du mode de liaison <xref:System.Windows.Data.BindingMode.OneWay> permet d’éviter la surcharge du mode de liaison <xref:System.Windows.Data.BindingMode.TwoWay>.

- <xref:System.Windows.Data.BindingMode.TwoWay>la liaison entraîne la mise à jour automatique de l’autre des modifications apportées à la propriété source ou à la propriété cible. Ce type de liaison convient aux formulaires modifiables ou à d’autres scénarios d’interface utilisateur entièrement interactifs. La plupart des propriétés ont par défaut la <xref:System.Windows.Data.BindingMode.OneWay> liaison, mais certaines propriétés de dépendance (en général, les propriétés des contrôles modifiables par l’utilisateur, tels que <xref:System.Windows.Controls.TextBox.Text?displayProperty=nameWithType> et [CheckBox. IsChecked](xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked) ont par défaut la valeur <xref:System.Windows.Data.BindingMode.TwoWay> Binding. Un moyen de déterminer par programmation si une propriété de dépendance établit par défaut une liaison unidirectionnelle ou bidirectionnelle consiste à obtenir les métadonnées de propriété avec <xref:System.Windows.DependencyProperty.GetMetadata%2A?displayProperty=nameWithType> , puis à vérifier la valeur booléenne de la <xref:System.Windows.FrameworkPropertyMetadata.BindsTwoWayByDefault%2A?displayProperty=nameWithType> propriété.

- <xref:System.Windows.Data.BindingMode.OneWayToSource>est l’inverse de la <xref:System.Windows.Data.BindingMode.OneWay> liaison ; il met à jour la propriété source lorsque la propriété cible change. Voici un exemple de scénario : Si vous devez uniquement réévaluer la valeur source à partir de l’interface utilisateur.

- La liaison n’est pas illustrée dans la figure <xref:System.Windows.Data.BindingMode.OneTime> , ce qui amène la propriété source à initialiser la propriété cible, mais ne propage pas les modifications ultérieures. Si le contexte de données change ou si l’objet dans le contexte de données change, la modification n’est *pas* reflétée dans la propriété cible. Ce type de liaison est approprié si un instantané de l’état actuel est approprié ou si les données sont véritablement statiques. Ce type de liaison est également utile si vous souhaitez initialiser votre propriété cible avec une valeur d’une propriété source et que le contexte de données n’est pas connu à l’avance. Ce mode est essentiellement une forme de liaison plus simple <xref:System.Windows.Data.BindingMode.OneWay> qui offre de meilleures performances dans les cas où la valeur source ne change pas.

Pour détecter les modifications de la source (applicables aux <xref:System.Windows.Data.BindingMode.OneWay> <xref:System.Windows.Data.BindingMode.TwoWay> liaisons et), la source doit implémenter un mécanisme de notification de modification de propriété approprié, tel que <xref:System.ComponentModel.INotifyPropertyChanged> . Consultez [Comment : implémenter une notification de modification de propriété](../../framework/wpf/data/how-to-implement-property-change-notification.md) pour obtenir un exemple d' <xref:System.ComponentModel.INotifyPropertyChanged> implémentation.

La <xref:System.Windows.Data.Binding.Mode?displayProperty=nameWithType> propriété fournit des informations supplémentaires sur les modes de liaison et un exemple de spécification de la direction d’une liaison.

### <a name="what-triggers-source-updates"></a>Ce qui déclenche les mises à jour de la source

Les liaisons qui sont <xref:System.Windows.Data.BindingMode.TwoWay> ou <xref:System.Windows.Data.BindingMode.OneWayToSource> écoutent les modifications dans la propriété cible et les propagent vers la source, appelées mise à jour de la source. Par exemple, vous pouvez modifier le texte d’une zone de texte pour modifier la valeur source sous-jacente.

Toutefois, votre valeur source est-elle mise à jour lorsque vous modifiez le texte ou lorsque vous avez fini de modifier le texte et que le contrôle perd le focus ? La <xref:System.Windows.Data.Binding.UpdateSourceTrigger?displayProperty=nameWithType> propriété détermine ce qui déclenche la mise à jour de la source. Les points des flèches droite de la figure ci-dessous illustrent le rôle de la <xref:System.Windows.Data.Binding.UpdateSourceTrigger?displayProperty=nameWithType> propriété.

![Diagramme qui montre le rôle de la propriété UpdateSourceTrigger.](./media/data-binding-overview/data-binding-updatesource-trigger.png)

Si la `UpdateSourceTrigger` valeur est <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged?displayProperty=nameWithType> , la valeur vers laquelle pointe la flèche droite de <xref:System.Windows.Data.BindingMode.TwoWay> ou les <xref:System.Windows.Data.BindingMode.OneWayToSource> liaisons est mise à jour dès que la propriété cible change. Toutefois, si la `UpdateSourceTrigger` valeur est <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus> , cette valeur est mise à jour uniquement avec la nouvelle valeur lorsque la propriété cible perd le focus.

Comme pour la <xref:System.Windows.Data.Binding.Mode%2A> propriété, différentes propriétés de dépendance ont des valeurs par défaut différentes <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> . La valeur par défaut de la plupart des propriétés de dépendance est <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>, tandis que celle de la propriété `TextBox.Text` a comme valeur par défaut <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>. `PropertyChanged`signifie que les mises à jour de la source se produisent généralement chaque fois que la propriété cible change. Les modifications instantanées conviennent parfaitement aux cases à cocher et autres contrôles simples. Toutefois, pour les champs de texte, la mise à jour après chaque séquence de touches peut réduire les performances et la possibilité pour l’utilisateur d’effectuer un retour arrière et de corriger les erreurs de frappe avant de valider la nouvelle valeur.

<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>Pour plus d’informations sur la recherche de la valeur par défaut d’une propriété de dépendance, consultez la page de propriétés.

Le tableau suivant fournit un exemple de scénario pour chaque <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> valeur à l’aide de <xref:System.Windows.Controls.TextBox> comme exemple.

| Valeur UpdateSourceTrigger | Quand la valeur source est mise à jour | Exemple de scénario pour TextBox |
| ------------------------- | ---------------------------------- | ---------------------------- |
| `LostFocus`(valeur par défaut pour <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> ) | Lorsque le contrôle TextBox perd le focus. | Zone de texte associée à la logique de validation (voir [validation des données](#data-validation) ci-dessous). |
| `PropertyChanged` | À mesure que vous tapez dans le <xref:System.Windows.Controls.TextBox> . | Contrôles TextBox dans une fenêtre de la salle de conversation. |
| `Explicit` | Lorsque l’application appelle <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> . | Contrôles TextBox dans un formulaire modifiable (met à jour les valeurs sources uniquement lorsque l’utilisateur clique sur le bouton Envoyer). |

Pour obtenir un exemple, consultez [Comment : contrôler quand le texte TextBox met à jour la source](../../framework/wpf/data/how-to-control-when-the-textbox-text-updates-the-source.md).

## <a name="creating-a-binding"></a>Création d’une liaison

Pour réévaluer certains des concepts abordés dans les sections précédentes, vous établissez une liaison à l’aide de l' <xref:System.Windows.Data.Binding> objet, et chaque liaison a généralement quatre composants : une cible de liaison, une propriété cible, une source de liaison et un chemin d’accès à la valeur source à utiliser. Cette section explique comment configurer une liaison.

Prenons l’exemple suivant, dans lequel l’objet de source de liaison est une classe nommée *MyData* qui est définie dans l’espace de noms *SDKSample*. À des fins de démonstration, *MyData* a une propriété de type chaîne nommée *colorname* dont la valeur est définie sur « rouge ». Par conséquent, cet exemple génère un bouton avec un arrière-plan rouge.

[!code-xaml[BindNonTextProperty](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/AutoConvertPropertyToColor.xaml#BindAutoConvertColor)]

Pour plus d’informations sur la syntaxe de la déclaration de liaison et des exemples de configuration d’une liaison dans le code, consultez [vue d’ensemble des déclarations de liaison](../../framework/wpf/data/binding-declarations-overview.md).

Si nous appliquons cet exemple à notre diagramme de base, l’illustration qui en résulte ressemble à ce qui suit. Cette figure décrit une <xref:System.Windows.Data.BindingMode.OneWay> liaison, car la propriété Background prend en charge la <xref:System.Windows.Data.BindingMode.OneWay> liaison par défaut.

![Diagramme qui affiche la propriété d’arrière-plan de liaison de données.](./media/data-binding-overview/data-binding-button-background-example.png)

Vous vous demandez peut-être pourquoi cette liaison fonctionne bien que la propriété *colorname* soit de type chaîne alors que la <xref:System.Windows.Controls.Control.Background%2A> propriété est de type <xref:System.Windows.Media.Brush> . Cette liaison utilise la conversion de type par défaut, qui est décrite dans la section [conversion de données](#data-conversion) .

### <a name="specifying-the-binding-source"></a>Spécification de la source de liaison

Notez que dans l’exemple précédent, la source de liaison est spécifiée en définissant la propriété [DockPanel. DataContext](xref:System.Windows.FrameworkElement.DataContext) . <xref:System.Windows.Controls.Button>Hérite ensuite de la <xref:System.Windows.FrameworkElement.DataContext%2A> valeur de <xref:System.Windows.Controls.DockPanel> , qui est son élément parent. Pour rappel, l’objet de source de liaison est un des quatre composants nécessaires d’une liaison. Par conséquent, sans objet de source de liaison spécifié, la liaison ne fait rien.

Il existe plusieurs façons de spécifier l’objet de source de liaison. L’utilisation <xref:System.Windows.FrameworkElement.DataContext%2A> de la propriété sur un élément parent est utile lorsque vous liez plusieurs propriétés à la même source. Cependant, il peut parfois être plus approprié de spécifier la source de liaison sur des déclarations de liaison individuelles. Pour l’exemple précédent, au lieu d’utiliser la <xref:System.Windows.FrameworkElement.DataContext%2A> propriété, vous pouvez spécifier la source de liaison en définissant la <xref:System.Windows.Data.Binding.Source%2A?displayProperty=nameWithType> propriété directement sur la déclaration de liaison du bouton, comme dans l’exemple suivant.

[!code-xaml[BindNonTextPropertyCompactBinding](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/AutoConvertPropertyToColor.xaml#BindAutoConvertColorCompactBinding)]

En dehors de la définition directe de la <xref:System.Windows.FrameworkElement.DataContext%2A> propriété sur un élément, en héritant <xref:System.Windows.FrameworkElement.DataContext%2A> de la valeur d’un ancêtre (tel que le bouton dans le premier exemple) et en spécifiant explicitement la source de liaison en définissant la <xref:System.Windows.Data.Binding.Source%2A?displayProperty=nameWithType> propriété sur la liaison (tel que le bouton du dernier exemple), vous pouvez également utiliser la <xref:System.Windows.Data.Binding.ElementName?displayProperty=nameWithType> propriété ou la <xref:System.Windows.Data.Binding.RelativeSource?displayProperty=nameWithType> propriété pour spécifier la source de liaison. La <xref:System.Windows.Data.Binding.ElementName%2A> propriété est utile lorsque vous effectuez une liaison à d’autres éléments dans votre application, par exemple lorsque vous utilisez un curseur pour ajuster la largeur d’un bouton. La <xref:System.Windows.Data.Binding.RelativeSource%2A> propriété est utile lorsque la liaison est spécifiée dans un <xref:System.Windows.Controls.ControlTemplate> ou un <xref:System.Windows.Style> . Pour plus d’informations, consultez [Comment : spécifier la source de liaison](../../framework/wpf/data/how-to-specify-the-binding-source.md).

### <a name="specifying-the-path-to-the-value"></a>Spécification du chemin d’accès à la valeur

Si votre source de liaison est un objet, vous utilisez la <xref:System.Windows.Data.Binding.Path?displayProperty=nameWithType> propriété pour spécifier la valeur à utiliser pour votre liaison. Si vous effectuez une liaison à des données XML, vous utilisez la <xref:System.Windows.Data.Binding.XPath?displayProperty=nameWithType> propriété pour spécifier la valeur. Dans certains cas, il peut s’avérer nécessaire d’utiliser la <xref:System.Windows.Data.Binding.Path%2A> propriété même lorsque vos données sont XML. Par exemple, si vous souhaitez accéder à la propriété Name d’un XmlNode retourné (à la suite d’une requête XPath), vous devez utiliser la <xref:System.Windows.Data.Binding.Path%2A> propriété en plus de la <xref:System.Windows.Data.Binding.XPath%2A> propriété.

Pour plus d’informations, consultez <xref:System.Windows.Data.Binding.Path%2A> les <xref:System.Windows.Data.Binding.XPath%2A> Propriétés et.

Bien que nous ayons insisté sur le fait que la <xref:System.Windows.Data.Binding.Path%2A> valeur à utiliser est l’un des quatre composants nécessaires d’une liaison, dans les scénarios que vous souhaitez lier à un objet entier, la valeur à utiliser est la même que l’objet de source de liaison. Dans ce cas, il est applicable de ne pas spécifier de <xref:System.Windows.Data.Binding.Path%2A> . Considérez l'exemple suivant.

[!code-xaml[EmptyBinding](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/EmptyBinding.xaml#EmptyBinding)]

L’exemple ci-dessus utilise la syntaxe de liaison vide : {Binding}. Dans ce cas, le <xref:System.Windows.Controls.ListBox> hérite du DataContext d’un élément DockPanel parent (non illustré dans cet exemple). Lorsque le chemin d’accès n’est pas spécifié, le comportement par défaut consiste à lier à l’objet entier. En d’autres termes, dans cet exemple, le chemin d’accès a été omis, car la <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> propriété est liée à la totalité de l’objet. (Consultez la section [liaison à des regroupements](#binding-to-collections) pour une discussion approfondie.)

En plus de la liaison à une collection, ce scénario est utile lorsque vous souhaitez lier un objet entier plutôt qu’une seule propriété d’un objet. Par exemple, si votre objet source est de type <xref:System.String> , vous pouvez simplement effectuer une liaison à la chaîne elle-même. Un autre scénario courant est lorsque vous souhaitez lier un élément à un objet avec plusieurs propriétés.

Vous devrez peut-être appliquer une logique personnalisée afin que les données soient significatives pour votre propriété cible liée. La logique personnalisée peut se présenter sous la forme d’un convertisseur personnalisé si la conversion de type par défaut n’existe pas. Pour plus d’informations sur les convertisseurs, consultez [conversion de données](#data-conversion) .

### <a name="binding-and-bindingexpression"></a>Binding et BindingExpression

Avant d’entrer dans d’autres fonctions et utilisations de la liaison de données, il est utile d’introduire la <xref:System.Windows.Data.BindingExpression> classe. Comme vous l’avez vu dans les sections précédentes, la <xref:System.Windows.Data.Binding> classe est la classe de haut niveau pour la déclaration d’une liaison ; elle fournit de nombreuses propriétés qui vous permettent de spécifier les caractéristiques d’une liaison. Une classe connexe, <xref:System.Windows.Data.BindingExpression> , est l’objet sous-jacent qui gère la connexion entre la source et la cible. Une liaison contient toutes les informations qui peuvent être partagées entre plusieurs expressions de liaison. Un <xref:System.Windows.Data.BindingExpression> est une expression d’instance qui ne peut pas être partagée et qui contient toutes les informations d’instance de <xref:System.Windows.Data.Binding> .

Prenons l’exemple suivant, où `myDataObject` est une instance de la `MyData` classe, `myBinding` est l' <xref:System.Windows.Data.Binding> objet source et `MyData` est une classe définie qui contient une propriété de type chaîne nommée `MyDataProperty` . Cet exemple lie le contenu de texte d' `myText` une instance de <xref:System.Windows.Controls.TextBlock> à `MyDataProperty` .

[!code-csharp[CodeOnlyBinding](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/ManualBinding.cs#CodeOnlyBinding)]
[!code-vb[CodeOnlyBinding](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/ManualBinding.vb#CodeOnlyBinding)]

Vous pouvez utiliser le même objet *myBinding* pour créer d’autres liaisons. Par exemple, vous pouvez utiliser l’objet *myBinding* pour lier le contenu textuel d’une case à cocher à *MyDataProperty*. Dans ce scénario, il y aura deux instances de <xref:System.Windows.Data.BindingExpression> partage de l’objet *myBinding* .

Un <xref:System.Windows.Data.BindingExpression> objet est retourné en appelant <xref:System.Windows.Data.BindingOperations.GetBindingExpression%2A> sur un objet lié aux données. Les articles suivants illustrent certaines utilisations de la <xref:System.Windows.Data.BindingExpression> classe :

- [Obtenir l’objet de liaison d’une propriété cible liée](../../framework/wpf/data/how-to-get-the-binding-object-from-a-bound-target-property.md)

- [Contrôle quand le texte TextBox met à jour la source](../../framework/wpf/data/how-to-control-when-the-textbox-text-updates-the-source.md)

## <a name="data-conversion"></a>Conversion de données

Dans la section [création d’une liaison](#creating-a-binding) , le bouton est rouge, car sa <xref:System.Windows.Controls.Control.Background%2A> propriété est liée à une propriété de type chaîne avec la valeur « Red ». Cette valeur de chaîne fonctionne car un convertisseur de type est présent sur le <xref:System.Windows.Media.Brush> type pour convertir la valeur de chaîne en <xref:System.Windows.Media.Brush> .

L’ajout de ces informations à la figure de la section [création d’une liaison](#creating-a-binding) se présente comme suit.

![Diagramme qui affiche la propriété de liaison de données par défaut.](./media/data-binding-overview/data-binding-button-default-conversion.png)

Toutefois, que se passe-t-il si, au lieu d’avoir une propriété de type chaîne, votre objet de source de liaison a une propriété *Color* de type <xref:System.Windows.Media.Color> ? Dans ce cas, pour que la liaison fonctionne, vous devez d’abord transformer la valeur de la propriété *Color* en un nom que la <xref:System.Windows.Controls.Control.Background%2A> propriété accepte. Vous devez créer un convertisseur personnalisé en implémentant l' <xref:System.Windows.Data.IValueConverter> interface, comme dans l’exemple suivant.

[!code-csharp[CodeOnlyBinding](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/ColorBrushConverter.cs#ColorBrushConverter)]
[!code-vb[CodeOnlyBinding](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/ColorBrushConverter.vb#ColorBrushConverter)]

Consultez la rubrique <xref:System.Windows.Data.IValueConverter> (éventuellement en anglais) pour plus d'informations.

À présent, le convertisseur personnalisé est utilisé à la place de la conversion par défaut, et notre diagramme ressemble à ce qui suit.

![Diagramme qui montre le convertisseur personnalisé de liaison de données.](./media/data-binding-overview/data-binding-converter-color-example.png)

Pour rappel, des conversions par défaut peuvent être disponibles si des convertisseurs de type sont présents dans le type lié. Ce comportement dépendra des convertisseurs de type sont disponibles dans la cible. En cas de doute, créez votre propre convertisseur.

Voici quelques scénarios classiques dans lesquels il est logique d’implémenter un convertisseur de données :

- Vos données devraient s’afficher différemment, selon la culture. Par exemple, vous souhaiterez peut-être implémenter un convertisseur de devises ou un convertisseur de date/heure de calendrier en fonction des conventions utilisées dans une culture particulière.

- Les données utilisées ne sont pas nécessairement destinées à modifier la valeur du texte d’une propriété, mais plutôt à modifier une autre valeur, comme la source d’une image ou la couleur ou le style du texte affiché. Les convertisseurs peuvent être utilisés ici en convertissant la liaison d’une propriété qui peut ne pas sembler appropriée, comme la liaison d’un champ de texte à la propriété Background d’une cellule de tableau.

- Plusieurs contrôles ou plusieurs propriétés de contrôles sont liés aux mêmes données. Dans ce cas, la liaison principale peut afficher uniquement le texte, tandis que les autres liaisons gèrent des problèmes d’affichage spécifiques, mais utilisent toujours la même liaison comme informations source.

- Une propriété cible a une collection de liaisons, qui est appelée <xref:System.Windows.Data.MultiBinding> . Pour <xref:System.Windows.Data.MultiBinding> , vous utilisez un personnalisé <xref:System.Windows.Data.IMultiValueConverter> pour produire une valeur finale à partir des valeurs des liaisons. Par exemple, la couleur peut être calculée à partir des valeurs rouge, vert et bleu, qui peuvent être des valeurs à partir d’objets de source de liaison identiques ou différents. <xref:System.Windows.Data.MultiBinding>Pour obtenir des exemples et des informations, consultez.

## <a name="binding-to-collections"></a>Lier à des collections

Un objet de source de liaison peut être traité comme un objet unique dont les propriétés contiennent des données ou comme une collection de données d’objets polymorphes qui sont souvent regroupés (par exemple, le résultat d’une requête dans une base de données). Jusqu’à présent, nous avons abordé la liaison à des objets uniques. Toutefois, la liaison à une collecte de données est un scénario courant. Par exemple, un scénario courant consiste à utiliser un <xref:System.Windows.Controls.ItemsControl> type <xref:System.Windows.Controls.ListBox> , <xref:System.Windows.Controls.ListView> ou <xref:System.Windows.Controls.TreeView> pour afficher une collection de données, par exemple dans l’application présentée dans la section [qu’est-ce](#what-is-data-binding) que la liaison de données.

Heureusement, notre diagramme de base est toujours applicable. Si vous liez un <xref:System.Windows.Controls.ItemsControl> à une collection, le diagramme ressemble à ce qui suit.

![Diagramme qui affiche l’objet ItemsControl de liaison de données.](./media/data-binding-overview/data-binding-itemscontrol.png)

Comme indiqué dans ce diagramme, pour lier un <xref:System.Windows.Controls.ItemsControl> à un objet de collection, <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A?displayProperty=nameWithType> la propriété est la propriété à utiliser. Vous pouvez considérer `ItemsSource` comme le contenu du <xref:System.Windows.Controls.ItemsControl> . La liaison est <xref:System.Windows.Data.BindingMode.OneWay> due au fait que la `ItemsSource` propriété prend en charge la `OneWay` liaison par défaut.

### <a name="how-to-implement-collections"></a>Comment implémenter des regroupements

Vous pouvez énumérer n’importe quelle collection qui implémente l' <xref:System.Collections.IEnumerable> interface. Toutefois, pour configurer des liaisons dynamiques afin que les insertions ou les suppressions dans la collection mettent à jour l’interface utilisateur automatiquement, la collection doit implémenter l' <xref:System.Collections.Specialized.INotifyCollectionChanged> interface. Cette interface expose un événement qui doit être déclenché chaque fois que la collection sous-jacente est modifiée.

WPF fournit la <xref:System.Collections.ObjectModel.ObservableCollection%601> classe, qui est une implémentation intégrée d’une collection de données qui expose l' <xref:System.Collections.Specialized.INotifyCollectionChanged> interface. Pour prendre entièrement en charge le transfert des valeurs de données des objets source vers les cibles, chaque objet de votre collection qui prend en charge les propriétés pouvant être liées doit également implémenter l' <xref:System.ComponentModel.INotifyPropertyChanged> interface. Pour plus d’informations, consultez [vue d’ensemble des sources de liaison](../../framework/wpf/data/binding-sources-overview.md).

Avant d’implémenter votre propre collection, envisagez <xref:System.Collections.ObjectModel.ObservableCollection%601> d’utiliser ou une des classes de collection existantes, telles que <xref:System.Collections.Generic.List%601> , <xref:System.Collections.ObjectModel.Collection%601> et <xref:System.ComponentModel.BindingList%601> , parmi de nombreuses autres. Si vous avez un scénario avancé et que vous souhaitez implémenter votre propre collection, envisagez d’utiliser <xref:System.Collections.IList> , qui fournit une collection non générique d’objets accessibles individuellement par l’index, et fournit ainsi les meilleures performances.

### <a name="collection-views"></a>Vues de collection

Une fois que votre <xref:System.Windows.Controls.ItemsControl> est lié à une collection de données, vous souhaiterez peut-être Trier, filtrer ou regrouper les données. Pour ce faire, vous utilisez des vues de collection, qui sont des classes qui implémentent l' <xref:System.ComponentModel.ICollectionView> interface.

#### <a name="what-are-collection-views"></a>Que sont les vues de collection ?

Une vue de collection est une couche sur une collection de sources de liaison qui vous permet de parcourir et d’afficher la collection source sur la base de requêtes de tri, de filtrage et de groupage, sans avoir à modifier la collection source sous-jacente elle-même. Une vue de collection maintient également un pointeur vers l’élément actuel dans la collection. Si la collection source implémente l' <xref:System.Collections.Specialized.INotifyCollectionChanged> interface, les modifications déclenchées par l' <xref:System.Collections.Specialized.INotifyCollectionChanged.CollectionChanged> événement sont propagées aux vues.

Étant donné que les vues ne modifient pas les collections source sous-jacentes, chaque collection source peut avoir plusieurs vues associées. Par exemple, vous pouvez avoir une collection d’objets *Task*. À l’aide de vues, vous pouvez afficher ces mêmes données de différentes façons. Par exemple, sur le côté gauche de votre page, vous souhaitez peut-être afficher les tâches triées par priorité et, sur le côté droit, les regrouper par domaine.

#### <a name="how-to-create-a-view"></a>Comment créer une vue

Un moyen de créer et utiliser une vue consiste à instancier l’objet de vue directement et de l’utiliser comme source de liaison. Par exemple, considérez l’application de [démonstration liaison de données][data-binding-demo] présentée dans la section [qu’est-ce que la liaison de données](#what-is-data-binding) . L’application est implémentée de telle sorte que le <xref:System.Windows.Controls.ListBox> lie à une vue sur la collection de données plutôt que directement à la collection de données. L’exemple suivant est extrait de l’application de [démonstration liaison de données][data-binding-demo] . La <xref:System.Windows.Data.CollectionViewSource> classe est le proxy XAML d’une classe qui hérite de <xref:System.Windows.Data.CollectionView> . Dans cet exemple particulier, le <xref:System.Windows.Data.CollectionViewSource.Source%2A> de la vue est lié à la collection *AuctionItems* (de type <xref:System.Collections.ObjectModel.ObservableCollection%601> ) de l’objet d’application actuel.

[!code-xaml[CollectionView](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml#CollectionView)]

La ressource *listingDataView* sert ensuite de source de liaison pour les éléments de l’application, tels que <xref:System.Windows.Controls.ListBox> .

[!code-xaml[ListBoxCollectionView](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml#ListBoxCollectionView)]

Pour créer une autre vue pour la même collection, vous pouvez créer une autre <xref:System.Windows.Data.CollectionViewSource> instance et lui attribuer un `x:Key` nom différent.

Le tableau suivant répertorie les types de données d’affichage qui sont créés en tant que vue de collection par défaut ou en <xref:System.Windows.Data.CollectionViewSource> fonction du type de collection source.

| Type de collection source                    | Type de vue de collection | Notes |
| ----------------------------------------- | -------------------- | ----- |
| <xref:System.Collections.IEnumerable>     | Type interne basé sur<xref:System.Windows.Data.CollectionView> | Impossible de grouper les éléments. |
| <xref:System.Collections.IList>           | <xref:System.Windows.Data.ListCollectionView> | Le plus rapide. |
| <xref:System.ComponentModel.IBindingList> | <xref:System.Windows.Data.BindingListCollectionView> | |

#### <a name="using-a-default-view"></a>Utilisation d’une vue par défaut

La spécification d’une vue de collection comme source de liaison est un moyen de créer et utiliser une vue de collection. WPF crée également une vue de collection par défaut pour chaque collection utilisée comme source de liaison. Si vous liez directement à une collection, WPF crée une liaison sur sa vue par défaut. Cette vue par défaut est partagée par toutes les liaisons à la même collection. par conséquent, une modification apportée à une vue par défaut par un contrôle lié ou du code (par exemple, le tri ou une modification du pointeur d’élément actuel, abordé plus tard) est reflétée dans toutes les autres liaisons à la même collection.

Pour obtenir la vue par défaut, utilisez la <xref:System.Windows.Data.CollectionViewSource.GetDefaultView%2A> méthode. Pour obtenir un exemple, consultez [obtenir la vue par défaut d’une collection de données](../../framework/wpf/data/how-to-get-the-default-view-of-a-data-collection.md).

#### <a name="collection-views-with-adonet-datatables"></a>Vues de collection avec des DataTables ADO.NET

Pour améliorer les performances, les vues de collection pour les ADO.NET <xref:System.Data.DataTable> ou <xref:System.Data.DataView> les objets délèguent le tri et le filtrage au <xref:System.Data.DataView> , ce qui entraîne le partage du tri et du filtrage dans toutes les vues de collection de la source de données. Pour permettre à chaque vue de collection de trier et filtrer indépendamment, initialisez chaque vue de collection avec son propre <xref:System.Data.DataView> objet.

#### <a name="sorting"></a>Tri

Comme mentionné précédemment, les vues peuvent appliquer un ordre de tri à une collection. Comme cela existe dans la collection sous-jacente, vos données peuvent avoir ou non un ordre inhérent pertinent. La vue sur la collection vous permet d’imposer un ordre, ou de modifier l’ordre par défaut, en fonction de critères de comparaison que vous fournissez. Comme il s’agit d’une vue de données côté client, un scénario courant est que l’utilisateur peut souhaiter trier les colonnes des données tabulaires par la valeur à laquelle la colonne correspond. À l’aide de vues, ce tri défini par l’utilisateur peut être appliqué, à nouveau sans apporter de modifications à la collection sous-jacente ou même avoir à redemander le contenu de la collection. Pour obtenir un exemple, consultez [Trier une colonne GridView lors d’un clic sur un en-tête](../../framework/wpf/controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md).

L’exemple suivant illustre la logique de tri de la section « Trier par catégorie et date » <xref:System.Windows.Controls.CheckBox> de l’interface utilisateur de l’application dans la section [qu’est-ce que la liaison de données](#what-is-data-binding) .

[!code-csharp[AddSortChecked](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml.cs#AddSortChecked)]
[!code-vb[AddSortChecked](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/CollectionView.xaml.vb#AddSortChecked)]

#### <a name="filtering"></a>Filtrage

Les vues peuvent également appliquer un filtre à une collection, de sorte que la vue n’affiche qu’un certain sous-ensemble de la collection complète. Vous pouvez filtrer sur une condition dans les données. Par exemple, comme c’est le cas de l’application dans la section [qu’est-ce que la liaison de données](#what-is-data-binding) , la « afficher uniquement les bonnes affaires » <xref:System.Windows.Controls.CheckBox> contient une logique pour filtrer les éléments qui coûtent $25 ou plus. Le code suivant est exécuté pour définir *ShowOnlyBargainsFilter* comme <xref:System.Windows.Data.CollectionViewSource.Filter> Gestionnaire d’événements lorsque cette <xref:System.Windows.Controls.CheckBox> option est sélectionnée.

[!code-csharp[ListingViewFilter](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml.cs#ListingViewFilter)]
[!code-vb[ListingViewFilter](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/CollectionView.xaml.vb#ListingViewFilter)]

Le gestionnaire d’événements *ShowOnlyBargainsFilter* a l’implémentation suivante.

[!code-csharp[FilterEvent](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml.cs#FilterEvent)]
[!code-vb[FilterEvent](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/CollectionView.xaml.vb#FilterEvent)]

Si vous utilisez l’une des <xref:System.Windows.Data.CollectionView> classes directement au lieu de <xref:System.Windows.Data.CollectionViewSource> , vous pouvez utiliser la <xref:System.Windows.Data.CollectionView.Filter%2A> propriété pour spécifier un rappel. Pour obtenir un exemple, consultez [Filtrer les données d'une vue](../../framework/wpf/data/how-to-filter-data-in-a-view.md).

#### <a name="grouping"></a>Regroupement

À l’exception de la classe interne qui affiche une <xref:System.Collections.IEnumerable> collection, toutes les vues de collection prennent en charge le *regroupement*, ce qui permet à l’utilisateur de partitionner la collection de la vue de collection en groupes logiques. Les groupes peuvent être explicites, si l’utilisateur fournit une liste de groupes, ou implicites, si les groupes sont générés dynamiquement en fonction des données.

L’exemple suivant illustre la logique de la « regrouper par catégorie » <xref:System.Windows.Controls.CheckBox> .

[!code-csharp[ListingGroupCheck](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml.cs#ListingGroupCheck)]
[!code-vb[ListingGroupCheck](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/CollectionView.xaml.vb#ListingGroupCheck)]

Pour un autre exemple de groupement, consultez [Grouper des éléments dans un ListView implémentant un GridView](../../framework/wpf/controls/how-to-group-items-in-a-listview-that-implements-a-gridview.md).

#### <a name="current-item-pointers"></a>Pointeurs d’élément actuel

Les vues prennent également en charge la notion d’élément actuel. Vous pouvez naviguer parmi les objets dans une vue de collection. Lorsque vous naviguez, vous déplacez un pointeur d’élément qui vous permet de récupérer l’objet qui existe à cet emplacement précis de la collection. Pour obtenir un exemple, consultez [Parcourir les objets dans un CollectionView de données](../../framework/wpf/data/how-to-navigate-through-the-objects-in-a-data-collectionview.md).

Étant donné que WPF crée une liaison à une collection à l’aide d’une vue (une vue que vous spécifiez, ou la vue par défaut de la collection), toutes les liaisons à des collections ont un pointeur d’élément actuel. Lors de la liaison à une vue, la barre oblique (« / ») dans une valeur `Path` désigne l’élément actuel de la vue. Dans l’exemple suivant, le contexte de données est une vue de collection. La première ligne lie à la collection. La deuxième ligne lie à l’élément actuel dans la collection. La troisième ligne lie à la propriété `Description` de l’élément actuel dans la collection.

```xaml
<Button Content="{Binding }" />
<Button Content="{Binding Path=/}" />
<Button Content="{Binding Path=/Description}" />
```

La syntaxe de barre oblique et de propriété peut également être empilée pour parcourir une hiérarchie de collections. L’exemple suivant lie l’élément actuel d’une collection nommée `Offices`, qui est une propriété de l’élément actuel de la collection source.

```xaml
<Button Content="{Binding /Offices/}" />
```

Le pointeur d’élément actuel peut être affecté par tout tri ou filtrage appliqué à la collection. Le tri conserve le pointeur d’élément actuel sur le dernier élément sélectionné, mais la vue de collection est désormais restructurée autour du tri. (Peut-être que l’élément sélectionné était au début de la liste avant, mais à présent, l’élément sélectionné peut être quelque part au milieu.) Le filtrage conserve l’élément sélectionné si cette sélection reste affichée après le filtrage. Sinon, le pointeur d’élément actuel est défini sur le premier élément de la vue de collection filtrée.

#### <a name="master-detail-binding-scenario"></a>Scénario de liaison maître/détail

La notion d’un élément actuel est utile non seulement pour le parcours d’éléments dans une collection, mais également pour le scénario de liaison maître/détail. Examinez de nouveau l’interface utilisateur de l’application dans la section [qu’est-ce que la liaison de données](#what-is-data-binding) . Dans cette application, la sélection dans le <xref:System.Windows.Controls.ListBox> détermine le contenu affiché dans le <xref:System.Windows.Controls.ContentControl> . Pour le placer d’une autre façon, lorsqu’un <xref:System.Windows.Controls.ListBox> élément est sélectionné, le <xref:System.Windows.Controls.ContentControl> affiche les détails de l’élément sélectionné.

Vous pouvez implémenter le scénario maître/détail simplement en ayant deux contrôles ou plus liés à la même vue. L’exemple suivant de la [démonstration][data-binding-demo] de la liaison de données montre le balisage du et de l' <xref:System.Windows.Controls.ListBox> interface utilisateur de l' <xref:System.Windows.Controls.ContentControl> application dans la section [qu’est-ce que la liaison de données](#what-is-data-binding) .

[!code-xaml[ListBoxContentControl](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml#ListBoxContentControl)]

Notez que les deux contrôles sont liés à la même source, la ressource statique *listingDataView* (consultez la définition de cette ressource dans la [section How to Create a View](#how-to-create-a-view)). Cette liaison fonctionne, car lorsqu’un objet singleton ( <xref:System.Windows.Controls.ContentControl> dans ce cas) est lié à une vue de collection, il est automatiquement lié au <xref:System.Windows.Data.CollectionView.CurrentItem%2A> de la vue. Les <xref:System.Windows.Data.CollectionViewSource> objets synchronisent automatiquement la devise et la sélection. Si votre contrôle de liste n’est pas lié à un <xref:System.Windows.Data.CollectionViewSource> objet comme dans cet exemple, vous devez définir sa <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> propriété sur `true` pour que cela fonctionne.

Pour obtenir d’autres exemples, consultez [lier à une collection et afficher des informations basées sur la sélection](../../framework/wpf/data/how-to-bind-to-a-collection-and-display-information-based-on-selection.md) et [utiliser le modèle maître/détail avec des données hiérarchiques](../../framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md).

Vous avez peut-être remarqué que l’exemple ci-dessus utilisait un modèle. En fait, les données ne sont pas affichées comme nous le souhaitons sans l’utilisation de modèles (celui utilisé explicitement par le <xref:System.Windows.Controls.ContentControl> et celui utilisé implicitement par <xref:System.Windows.Controls.ListBox> ). Nous passons maintenant aux modèles de données dans la section suivante.

## <a name="data-templating"></a>Modèles de données

Sans l’utilisation de modèles de données, notre interface utilisateur d’application dans la section [qu’est-ce](#what-is-data-binding) que la liaison de données ressemble à ce qui suit.

![Démo de liaison de données sans modèles de données](./media/data-binding-overview/demo-no-template.png)

Comme indiqué dans l’exemple de la section précédente, le <xref:System.Windows.Controls.ListBox> contrôle et le <xref:System.Windows.Controls.ContentControl> sont liés à l’objet de collection entier (ou plus spécifiquement, la vue sur l’objet de collection) d' *AuctionItem*s. Sans instructions spécifiques sur l’affichage de la collection de données, le <xref:System.Windows.Controls.ListBox> affiche la représentation sous forme de chaîne de chaque objet dans la collection sous-jacente et le <xref:System.Windows.Controls.ContentControl> affiche la représentation sous forme de chaîne de l’objet auquel il est lié.

Pour résoudre ce problème, l’application définit <xref:System.Windows.DataTemplate?text=DataTemplates> . Comme indiqué dans l’exemple de la section précédente, le <xref:System.Windows.Controls.ContentControl> utilise explicitement le modèle de données *detailsProductListingTemplate* . Le <xref:System.Windows.Controls.ListBox> contrôle utilise implicitement le modèle de données suivant lors de l’affichage des objets *AuctionItem* dans la collection.

[!code-xaml[AuctionItemDataTemplate](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml#AuctionItemDataTemplate)]

Avec l’utilisation de ces deux DataTemplate, l’interface utilisateur obtenue est celle présentée dans la section [qu’est-ce que la liaison de données](#what-is-data-binding) . Comme vous pouvez le voir dans cette capture d’écran, en plus de vous permettre de placer des données dans vos contrôles, les DataTemplate vous permettent de définir des visuels attrayants pour vos données. Par exemple, <xref:System.Windows.DataTrigger> les objets sont utilisés dans les éléments ci-dessus <xref:System.Windows.DataTemplate> afin *SpecialFeatures* que les s d’un reflet avec la valeur de mise en surbrillance de la valeur de *mise en surbrillance* apparaissent avec une bordure orange et une étoile. *AuctionItem*

Pour plus d’informations sur les modèles de données, consultez [vue d’ensemble](../../framework/wpf/data/data-templating-overview.md)des modèles de données.

## <a name="data-validation"></a>Validation des données

La plupart des applications qui acceptent les entrées d’utilisateur doivent disposer d’une logique de validation pour s’assurer que l’utilisateur a entré les informations attendues. Les contrôles de validation peuvent être basés sur le type, la plage, le format ou d’autres spécifications spécifiques à l’application. Cette section décrit le fonctionnement de la validation des données dans WPF.

### <a name="associating-validation-rules-with-a-binding"></a>Association de règles de validation à une liaison

Le modèle de liaison de données WPF vous permet d’associer à <xref:System.Windows.Data.Binding.ValidationRules%2A> votre <xref:System.Windows.Data.Binding> objet. Par exemple, l’exemple suivant lie un <xref:System.Windows.Controls.TextBox> à une propriété nommée `StartPrice` et ajoute un <xref:System.Windows.Controls.ExceptionValidationRule> objet à la <xref:System.Windows.Data.Binding.ValidationRules%2A?displayProperty=nameWithType> propriété.

[!code-xaml[TextboxStartPrice](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/DataValidation.xaml#TextboxStartPrice)]

Un <xref:System.Windows.Controls.ValidationRule> objet vérifie si la valeur d’une propriété est valide. WPF dispose de deux types d’objets intégrés <xref:System.Windows.Controls.ValidationRule> :

- <xref:System.Windows.Controls.ExceptionValidationRule>Recherche les exceptions levées pendant la mise à jour de la propriété de source de liaison. Dans l’exemple précédent, `StartPrice` est de type entier. Lorsque l’utilisateur entre une valeur qui ne peut pas être convertie en un entier, une exception est levée, ce qui marque la liaison comme étant non valide. Une autre syntaxe pour définir <xref:System.Windows.Controls.ExceptionValidationRule> explicitement est de définir la <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> propriété `true` sur sur votre <xref:System.Windows.Data.Binding> objet ou <xref:System.Windows.Data.MultiBinding> .

- Un <xref:System.Windows.Controls.DataErrorValidationRule> objet recherche les erreurs déclenchées par les objets qui implémentent l' <xref:System.ComponentModel.IDataErrorInfo> interface. Pour obtenir un exemple d’utilisation de cette règle de validation, consultez <xref:System.Windows.Controls.DataErrorValidationRule> . Une autre syntaxe pour définir <xref:System.Windows.Controls.DataErrorValidationRule> explicitement est de définir la <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> propriété `true` sur sur votre <xref:System.Windows.Data.Binding> objet ou <xref:System.Windows.Data.MultiBinding> .

Vous pouvez également créer votre propre règle de validation en dérivant de la <xref:System.Windows.Controls.ValidationRule> classe et en implémentant la <xref:System.Windows.Controls.ValidationRule.Validate%2A> méthode. L’exemple suivant illustre la règle utilisée par la *liste ajouter un produit* « date de début » <xref:System.Windows.Controls.TextBox> de la section [qu’est-ce que la liaison de données](#what-is-data-binding) .

[!code-csharp[FutureDateRule](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/FutureDateRule.cs#FutureDateRule)]
[!code-vb[FutureDateRule](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/FutureDateRule.vb#FutureDateRule)]

*StartDateEntryForm* <xref:System.Windows.Controls.TextBox> utilise ce *FutureDateRule*, comme illustré dans l’exemple suivant.

[!code-xaml[TextboxStartDate](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/DataValidation.xaml#TextboxStartDate)]

Étant donné que la <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> valeur est <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged> , le moteur de liaison met à jour la valeur source à chaque séquence de touches, ce qui signifie qu’elle vérifie également chaque règle de la <xref:System.Windows.Data.Binding.ValidationRules%2A> collection à chaque séquence de touches. Nous reviendrons plus tard là-dessus dans la section Processus de validation.

### <a name="providing-visual-feedback"></a>Fournir des commentaires visuels

Si l’utilisateur entre une valeur non valide, vous souhaiterez peut-être fournir des commentaires sur l’erreur sur l’interface utilisateur de l’application. Une façon de fournir ces commentaires consiste à définir la <xref:System.Windows.Controls.Validation.ErrorTemplate%2A?displayProperty=nameWithType> propriété jointe sur un personnalisé <xref:System.Windows.Controls.ControlTemplate> . Comme indiqué dans la sous-section précédente, *StartDateEntryForm* <xref:System.Windows.Controls.TextBox> utilise <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> un *validationTemplate*appelé. L’exemple suivant illustre la définition de *validationTemplate*.

[!code-xaml[ControlTemplate](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/DataValidation.xaml#ControlTemplate)]

L' <xref:System.Windows.Controls.AdornedElementPlaceholder> élément spécifie où le contrôle qui est orné doit être placé.

En outre, vous pouvez également utiliser un <xref:System.Windows.Controls.ToolTip> pour afficher le message d’erreur. *StartDateEntryForm* et *StartPriceEntryForm* <xref:System.Windows.Controls.TextBox> es utilisent le style *textStyleTextBox*, qui crée un <xref:System.Windows.Controls.ToolTip> qui affiche le message d’erreur. L’exemple suivant montre la définition de *textStyleTextBox*. La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` quand une ou plusieurs liaisons sur les propriétés de l’élément lié sont erronées.

[!code-xaml[TextBoxStyle](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/DataValidation.xaml#TextBoxStyle)]

Avec les <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> et personnalisés <xref:System.Windows.Controls.ToolTip> , le *StartDateEntryForm* <xref:System.Windows.Controls.TextBox> ressemble à ce qui suit lorsqu’il y a une erreur de validation.

![Erreur de validation de la liaison de données](./media/data-binding-overview/demo-validation-date.png "DataBindingDemo_Validation")

Si votre <xref:System.Windows.Data.Binding> a des règles de validation associées mais que vous ne spécifiez pas <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> de sur le contrôle lié, une valeur par défaut est <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> utilisée pour avertir les utilisateurs en cas d’erreur de validation. La valeur par défaut <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> est un modèle de contrôle qui définit une bordure rouge dans la couche d’ornement. Avec la valeur par défaut <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> et <xref:System.Windows.Controls.ToolTip> , l’interface utilisateur du *StartPriceEntryForm* <xref:System.Windows.Controls.TextBox> se présente comme suit lorsqu’il existe une erreur de validation.

![Erreur de validation de la liaison de données](./media/data-binding-overview/demo-validation-price.png "DataBindingDemo_ValidationDefault")

Pour obtenir un exemple de la façon de fournir une logique pour valider tous les contrôles dans une boîte de dialogue, consultez la section boîtes de dialogue personnalisées dans la [vue d’ensemble des boîtes de dialogue](../../framework/wpf/app-development/dialog-boxes-overview.md).

### <a name="validation-process"></a>Processus de validation

La validation se produit généralement lorsque la valeur d’une cible est transférée à la propriété de source de liaison. Ce transfert se produit sur <xref:System.Windows.Data.BindingMode.TwoWay> les <xref:System.Windows.Data.BindingMode.OneWayToSource> liaisons et. Pour une réitération, ce qui provoque la mise à jour d’une source dépend de la valeur de la <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> propriété, comme décrit dans la section [qu’est-ce qui déclenche les mises à jour](#what-triggers-source-updates) de la source.

Les éléments suivants décrivent le processus de *validation* . Si une erreur de validation ou un autre type d’erreur se produit à tout moment au cours de ce processus, le processus est interrompu :

1. Le moteur de liaison vérifie s’il existe des <xref:System.Windows.Controls.ValidationRule> objets personnalisés définis <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> pour lesquels a <xref:System.Windows.Controls.ValidationStep.RawProposedValue> la valeur pour ce <xref:System.Windows.Data.Binding> , auquel cas il appelle la <xref:System.Windows.Controls.ValidationRule.Validate%2A> méthode sur chacun <xref:System.Windows.Controls.ValidationRule> d’eux jusqu’à ce que l’un d’eux s’exécute dans une erreur ou jusqu’à ce que tous les tests réussissent.

2. Le moteur de liaison appelle alors le convertisseur, s’il en existe un.

3. Si le convertisseur réussit, le moteur de liaison vérifie s’il existe des <xref:System.Windows.Controls.ValidationRule> objets personnalisés définis dont <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> a <xref:System.Windows.Controls.ValidationStep.ConvertedProposedValue> la valeur pour ce <xref:System.Windows.Data.Binding> , auquel cas il appelle la <xref:System.Windows.Controls.ValidationRule.Validate%2A> méthode sur chaque <xref:System.Windows.Controls.ValidationRule> qui a la <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> valeur <xref:System.Windows.Controls.ValidationStep.ConvertedProposedValue> jusqu’à ce que l’un d’eux s’exécute dans une erreur ou jusqu’à ce qu’ils soient tous passés.

4. Le moteur de liaison définit la propriété source.

5. Le moteur de liaison vérifie s’il existe des <xref:System.Windows.Controls.ValidationRule> objets personnalisés définis pour <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> lesquels a <xref:System.Windows.Controls.ValidationStep.UpdatedValue> la valeur pour ce <xref:System.Windows.Data.Binding> , auquel cas il appelle la <xref:System.Windows.Controls.ValidationRule.Validate%2A> méthode sur chaque <xref:System.Windows.Controls.ValidationRule> dont a défini la <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> valeur jusqu’à ce que <xref:System.Windows.Controls.ValidationStep.UpdatedValue> l’un d’eux s’exécute dans une erreur ou jusqu’à ce que tous les tests réussissent. Si un <xref:System.Windows.Controls.DataErrorValidationRule> est associé à une liaison et que <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> a la valeur par défaut, <xref:System.Windows.Controls.ValidationStep.UpdatedValue> , <xref:System.Windows.Controls.DataErrorValidationRule> est vérifié à ce stade. À ce stade, toutes les liaisons dont a la <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> valeur `true` est vérifiée.

6. Le moteur de liaison vérifie s’il existe des <xref:System.Windows.Controls.ValidationRule> objets personnalisés définis pour <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> lesquels a <xref:System.Windows.Controls.ValidationStep.CommittedValue> la valeur pour ce <xref:System.Windows.Data.Binding> , auquel cas il appelle la <xref:System.Windows.Controls.ValidationRule.Validate%2A> méthode sur chaque <xref:System.Windows.Controls.ValidationRule> dont a défini la <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> valeur jusqu’à ce que <xref:System.Windows.Controls.ValidationStep.CommittedValue> l’un d’eux s’exécute dans une erreur ou jusqu’à ce que tous les tests réussissent.

Si un <xref:System.Windows.Controls.ValidationRule> ne passe pas à un moment donné dans le cadre de ce processus, le moteur de liaison crée un <xref:System.Windows.Controls.ValidationError> objet et l’ajoute à la <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> collection de l’élément lié. Avant que le moteur de liaison n’exécute les <xref:System.Windows.Controls.ValidationRule> objets à une étape donnée, il supprime tous ceux <xref:System.Windows.Controls.ValidationError> qui ont été ajoutés à la <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> propriété jointe de l’élément lié pendant cette étape. Par exemple, si a <xref:System.Windows.Controls.ValidationRule> dont <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> a la valeur <xref:System.Windows.Controls.ValidationStep.UpdatedValue> failed, la prochaine fois que le processus de validation se produit, le moteur de liaison supprime immédiatement celui qui <xref:System.Windows.Controls.ValidationError> <xref:System.Windows.Controls.ValidationRule> a la <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> valeur <xref:System.Windows.Controls.ValidationStep.UpdatedValue> .

Lorsque <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> n’est pas vide, la <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe de l’élément a la valeur `true` . En outre, si la <xref:System.Windows.Data.Binding.NotifyOnValidationError%2A> propriété du <xref:System.Windows.Data.Binding> a la valeur `true` , le moteur de liaison déclenche l' <xref:System.Windows.Controls.Validation.Error?displayProperty=nameWithType> événement attaché sur l’élément.

Notez également qu’un transfert de valeur valide dans l’une ou l’autre direction (cible vers source ou source vers cible) efface la <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> propriété jointe.

Si la liaison est associée à une liaison ou si la <xref:System.Windows.Controls.ExceptionValidationRule> propriété a la <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> valeur et qu' `true` une exception est levée lorsque le moteur de liaison définit la source, le moteur de liaison vérifie s’il existe un <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A> . Vous avez la possibilité d’utiliser le <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A> rappel pour fournir un gestionnaire personnalisé pour la gestion des exceptions. Si un <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A> n’est pas spécifié sur <xref:System.Windows.Data.Binding> , le moteur de liaison crée un <xref:System.Windows.Controls.ValidationError> avec l’exception et l’ajoute à la <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> collection de l’élément lié.

## <a name="debugging-mechanism"></a>Mécanisme de débogage

Vous pouvez définir la propriété jointe <xref:System.Diagnostics.PresentationTraceSources.TraceLevel%2A?displayProperty=nameWithType> sur un objet lié à la liaison pour recevoir des informations sur l’état d’une liaison spécifique.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Controls.DataErrorValidationRule>
- [Lier aux résultats d’une requête LINQ](../../framework/wpf/data/how-to-bind-to-the-results-of-a-linq-query.md)
- [Liaison de données](../../framework/wpf/advanced/optimizing-performance-data-binding.md)
- [Démonstration de la liaison de données][data-binding-demo]
- [Articles de savoir-faire](../../framework/wpf/data/data-binding-how-to-topics.md)
- [Établir une liaison à une source de données ADO.NET](../../framework/wpf/data/how-to-bind-to-an-ado-net-data-source.md)

[data-binding-demo]: https://github.com/microsoft/WPF-Samples/tree/master/Sample%20Applications/DataBindingDemo "application de démonstration de liaison de données"
