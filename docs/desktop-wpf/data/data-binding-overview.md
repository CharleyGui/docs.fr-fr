---
title: Vue d’ensemble de la liaison de données
description: Découvrez les différentes sources de données que vous pouvez ajouter à votre projet dans Windows Presentation Foundation pour .NET Core. Les sources de données peuvent être liées aux éléments XAML pour créer des applications dynamiques.
author: thraka
ms.date: 09/19/2019
ms.author: adegeo
dev_langs:
- csharp
- vb
ms.openlocfilehash: 7f17ff094a35c04ba880c87c6966d7d249817516
ms.sourcegitcommit: b75a45f0cfe012b71b45dd9bf723adf32369d40c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "82072010"
---
# <a name="data-binding-overview-in-wpf"></a>Aperçu de la liaison des données dans WPF

La liaison de données dans windows Presentation Foundation (WPF) fournit un moyen simple et cohérent pour les applications de présenter et d’interagir avec les données. Les éléments peuvent être liés aux données d’une variété de sources de données sous la forme d’objets .NET et XML. Tout <xref:System.Windows.Controls.ContentControl> tel <xref:System.Windows.Controls.Button> que <xref:System.Windows.Controls.ItemsControl>et <xref:System.Windows.Controls.ListBox> n’importe quel, tels que et <xref:System.Windows.Controls.ListView>, ont intégré la fonctionnalité pour permettre un style flexible d’éléments de données uniques ou des collections d’éléments de données. Des vues de tri, filtrage et groupage peuvent être générées sur la base des données.

La fonctionnalité de liaison de données dans WPF présente plusieurs avantages par rapport aux modèles traditionnels, y compris le support inhérent à la liaison des données par un large éventail de propriétés, la représentation flexible de l’interface utilisateur des données et la séparation propre de la logique commerciale de l’interface utilisateur.

Cet article traite d’abord des concepts fondamentaux de <xref:System.Windows.Data.Binding> la liaison des données WPF, puis couvre l’utilisation de la classe et d’autres fonctionnalités de liaison de données.

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="what-is-data-binding"></a>Qu’est-ce que la liaison de données ?

La liaison de données est le processus qui établit une connexion entre l’interface utilisateur de l’application et les données qu’elle affiche. Si la liaison est correctement paramétrée et si les données fournissent les notifications appropriées, lorsque les données changent de valeur, les éléments qui sont liés aux données reflètent automatiquement ces changements. La liaison de données peut également signifier que si une représentation externe des données dans un élément change, les données sous-jacentes peuvent être automatiquement mises à jour pour refléter les modifications. Par exemple, si l’utilisateur modifie `TextBox` la valeur d’un élément, la valeur de données sous-jacente est automatiquement mise à jour pour refléter cette modification.

Une utilisation typique de la liaison de données consiste à placer les données de configuration du serveur ou de la configuration locale sous forme ou dans d’autres contrôles d’interface utilisateur. Dans WPF, ce concept est élargi pour inclure la liaison d’un large éventail de propriétés à une variété de sources de données. Dans WPF, les propriétés de dépendance des éléments peuvent être liées à des objets .NET (y compris des objets ou des objets ADO.NET associés aux services Web et aux propriétés Web) et aux données XML.

Pour un exemple de liaison de données, jetez un oeil à l’interface utilisateur d’application suivante de la [démo de liaison de données][data-binding-demo], qui affiche une liste d’éléments d’enchères.

![Capture d’écran de l’échantillon de liaison de données](./media/data-binding-overview/demo.png "DataBinding_DataBindingDemo")

L’application démontre les fonctionnalités suivantes de la liaison de données :

- Le contenu de la ListBox est lié à une collection d’objets *AuctionItem.* Un objet *AuctionItem* a des propriétés telles que *description*, *StartPrice*, *StartDate*, *Catégorie*, *SpecialFeatures*, et ainsi de suite.

- Les données (objets*AuctionItem)* affichées dans le `ListBox` modèle de sorte que la description et le prix actuel sont affichés pour chaque élément. Le modèle est créé <xref:System.Windows.DataTemplate>en utilisant un . En outre, l’apparence de chaque élément varie selon la valeur de *SpecialFeatures* de *l’AuctionItem* affiché. Si la valeur *SpecialFeatures* de *AuctionItem* est *Color*, l’élément a une bordure bleue. Si la valeur est *Highlight*, l’élément a une bordure orange et une étoile. La section [Modèles de données](#data-templating) fournit des informations sur les modèles de données.

- L’utilisateur peut regrouper, filtrer ou `CheckBoxes` trier les données à l’aide de la fournie. Dans l’image ci-dessus, le **Groupe par catégorie** et Le tri par catégorie et la **date** `CheckBoxes` sont sélectionnés. Vous avez peut-être remarqué que les données sont regroupées en fonction de la catégorie de produit et que les noms de catégorie sont dans l’ordre alphabétique. Cela est difficile à observer sur l’image, mais les éléments sont également triés par date de début dans chaque catégorie. Le tri se fait à l’aide d’une *vue de collection*. La section [Liaison aux collections](#binding-to-collections) traite des vues de la collection.

- Lorsque l’utilisateur sélectionne un <xref:System.Windows.Controls.ContentControl> élément, il affiche les détails de l’élément sélectionné. Cette expérience est appelée le *scénario Master-detail*. La section [de scénario Master-detail](#master-detail-binding-scenario) fournit des informations sur ce type de liaison.

- Le type de la propriété <xref:System.DateTime> *StartDate* est , qui retourne une date qui comprend le temps à la milliseconde. Dans cette application, un convertisseur personnalisé a été utilisé de sorte qu’une chaîne de date plus courte est affichée. La section [de conversion de données](#data-conversion) fournit des informations sur les convertisseurs.

Lorsque l’utilisateur sélectionne le bouton Ajouter le *produit,* le formulaire suivant apparaît.

![Page Ajouter la liste de produits](./media/data-binding-overview/demo-addproductlisting.png "DataBinding_Demo_AddProductListing")

L’utilisateur peut modifier les champs sous la forme, prévisualiser la `Submit` liste du produit à l’aide des vitres de prévisualisation courtes ou détaillées, et choisir d’ajouter la nouvelle liste de produits. Tous les paramètres de regroupement, de filtrage et de tri existants s’appliqueront à la nouvelle entrée. Dans ce cas particulier, l’élément entré dans l’image ci-dessus s’affichera comme deuxième élément dans la catégorie *Computer*.

La logique de validation fournie dans la date de début n’est pas *indiquée* <xref:System.Windows.Controls.TextBox>dans cette image. Si l’utilisateur entre une date invalide (formatage invalide ou <xref:System.Windows.Controls.ToolTip> date passée), l’utilisateur sera <xref:System.Windows.Controls.TextBox>averti avec un point d’exclamation rouge et un point d’exclamation rouge à côté de la . La section [Validation des données](#data-validation) explique comment créer une logique de validation.

Avant d’entrer dans les différentes caractéristiques de la liaison des données décrites ci-dessus, nous discuterons d’abord des concepts fondamentaux qui sont essentiels à la compréhension de la liaison des données WPF.

## <a name="basic-data-binding-concepts"></a>Concepts de base de liaison de données

Quel que soit l’élément que vous liez et la nature de votre source de données, chaque liaison suit toujours le modèle illustré par le chiffre suivant.

![Diagramme qui montre le modèle de liaison de données de base.](./media/data-binding-overview/basic-data-binding-diagram.png)

Comme le montre le chiffre, la liaison de données est essentiellement le pont entre votre cible contraignante et votre source de liaison. Le chiffre démontre les concepts fondamentaux suivants de liaison des données WPF :

- Typiquement, chaque liaison comporte quatre composantes :

  - Un objet cible contraignant.
  - Une propriété cible.
  - Une source de liaison.
  - Un chemin vers la valeur dans la source de liaison à utiliser.
  
  > Par `TextBox` exemple, si vous souhaitez lier `Employee.Name` le contenu d’un `TextBox`à la propriété, votre objet cible est le , la propriété cible est la <xref:System.Windows.Controls.TextBox.Text%2A> propriété, la valeur à utiliser est *Nom*, et l’objet source est *l’objet employé.*

- La propriété cible doit être une propriété de dépendance. La <xref:System.Windows.UIElement> plupart des propriétés sont des propriétés de dépendance, et la plupart des propriétés de dépendance, à l’exception de la lecture seulement, prennent en charge les données contraignantes par défaut. (Seuls les <xref:System.Windows.DependencyObject> types dérivés peuvent <xref:System.Windows.UIElement> définir les `DependencyObject`propriétés de dépendance; et tous les types dérivent de .)

- Bien qu’il ne soit pas indiqué dans la figure, il convient de noter que l’objet source de liaison ne se limite pas à être un objet personnalisé .NET. La liaison de données WPF prend en charge les données sous la forme d’objets .NET et de XML. Pour donner quelques exemples, votre <xref:System.Windows.UIElement>source de liaison peut être un objet, n’importe quel objet de liste, un objet ADO.NET ou Web Services, ou un XmlNode qui contient vos données XML. Pour plus d’informations, voir [Aperçu des sources contraignantes](../../framework/wpf/data/binding-sources-overview.md).

Il est important de se rappeler que lorsque vous établissez une liaison, vous liez une cible contraignante *à* une source contraignante. Par exemple, si vous affichez certaines <xref:System.Windows.Controls.ListBox> données XML sous-jacentes dans une liaison de données à l’aide de données, vous liez vos `ListBox` données aux données XML.

Pour établir une liaison, <xref:System.Windows.Data.Binding> vous utilisez l’objet. Le reste de cet article traite de nombreux concepts associés et `Binding` de certaines propriétés et utilisation de l’objet.

### <a name="direction-of-the-data-flow"></a>Direction du flux de données

Comme indiqué par la flèche dans le chiffre précédent, le flux de données d’une liaison peut passer de la cible `TextBox`contraignante à la source de liaison (par exemple, la valeur source change quand un utilisateur modifie la valeur d’un ) et / ou de la source de liaison à la cible de liaison (par exemple, votre `TextBox` contenu est mis à jour avec des changements dans la source de liaison) si la source de liaison fournit les notifications appropriées.

Vous voudrez peut-être que votre application permette aux utilisateurs de modifier les données et de les propager vers l’objet source. Ou vous souhaitez peut-être ne pas permettre aux utilisateurs de mettre à jour la source de données. Vous pouvez contrôler le flux <xref:System.Windows.Data.Binding.Mode?displayProperty=nameWithType>de données en définissant le .

Ce chiffre illustre les différents types de flux de données :

![Flux de données de la liaison de données](./media/data-binding-overview/databinding-dataflow.png "DataBinding_DataFlow")

- <xref:System.Windows.Data.BindingMode.OneWay>la liaison provoque des modifications à la propriété source pour mettre à jour automatiquement la propriété cible, mais les modifications apportées à la propriété cible ne sont pas propagées à la propriété source. Ce type de liaison est approprié si le contrôle lié est implicitement en lecture seule. Par exemple, vous pouvez vous lier à une source telle qu’un ticker de stock, ou peut-être votre propriété cible n’a aucune interface de contrôle prévue pour faire des modifications, telles qu’une couleur de fond liée aux données d’une table. S’il n’est pas nécessaire de surveiller les modifications de la propriété cible, l’utilisation du mode de liaison <xref:System.Windows.Data.BindingMode.OneWay> permet d’éviter la surcharge du mode de liaison <xref:System.Windows.Data.BindingMode.TwoWay>.

- <xref:System.Windows.Data.BindingMode.TwoWay>la liaison provoque des modifications à la propriété source ou à la propriété cible pour mettre à jour automatiquement l’autre. Ce type de liaison est approprié pour les formulaires modifiables ou d’autres scénarios d’interface utilisateur entièrement interactifs. La plupart <xref:System.Windows.Data.BindingMode.OneWay> des propriétés par défaut à la liaison, mais <xref:System.Windows.Controls.TextBox.Text?displayProperty=nameWithType> certaines propriétés de dépendance <xref:System.Windows.Data.BindingMode.TwoWay> (généralement les propriétés des contrôles modifiables par l’utilisateur tels que le défaut et [CheckBox.IsChecked](xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked) à la liaison. Une façon programmatique de déterminer si une propriété de dépendance lie à sens unique ou <xref:System.Windows.DependencyProperty.GetMetadata%2A?displayProperty=nameWithType> bidirectionnel par défaut <xref:System.Windows.FrameworkPropertyMetadata.BindsTwoWayByDefault%2A?displayProperty=nameWithType> est d’obtenir les métadonnées de propriété avec et puis vérifier la valeur Boolean de la propriété.

- <xref:System.Windows.Data.BindingMode.OneWayToSource>est l’inverse de la <xref:System.Windows.Data.BindingMode.OneWay> liaison; il met à jour la propriété source lorsque la propriété cible change. Un scénario d’exemple est si vous avez seulement besoin de réévaluer la valeur source de l’interface utilisateur.

- Non illustré dans le <xref:System.Windows.Data.BindingMode.OneTime> chiffre est contraignant, ce qui provoque la propriété source à l’initialisation de la propriété cible, mais ne propage pas les changements ultérieurs. Si le contexte des données change ou si l’objet dans le contexte des données change, la modification *n’est pas* reflétée dans la propriété cible. Ce type de liaison est approprié si un instantané de l’état actuel est approprié ou si les données sont vraiment statiques. Ce type de liaison est également utile si vous souhaitez initialiser votre propriété cible avec une valeur d’une propriété source et que le contexte de données n’est pas connu à l’avance. Ce mode est essentiellement une <xref:System.Windows.Data.BindingMode.OneWay> forme plus simple de liaison qui offre de meilleures performances dans les cas où la valeur source ne change pas.

Pour détecter les changements <xref:System.Windows.Data.BindingMode.OneWay> <xref:System.Windows.Data.BindingMode.TwoWay> de source (applicables et les liaisons), <xref:System.ComponentModel.INotifyPropertyChanged>la source doit mettre en œuvre un mécanisme approprié de notification de changement de propriété tel que . Voir [comment : Implémenter la notification de modification de propriété](../../framework/wpf/data/how-to-implement-property-change-notification.md) pour un exemple de <xref:System.ComponentModel.INotifyPropertyChanged> mise en œuvre.

La <xref:System.Windows.Data.Binding.Mode?displayProperty=nameWithType> propriété fournit plus d’informations sur les modes de liaison et un exemple de la façon de spécifier l’orientation d’une liaison.

### <a name="what-triggers-source-updates"></a>Ce qui déclenche les mises à jour de source

Liaisons qui <xref:System.Windows.Data.BindingMode.TwoWay> <xref:System.Windows.Data.BindingMode.OneWayToSource> sont ou écouter les changements dans la propriété cible et les propager à la source, connu sous le nom de mise à jour de la source. Par exemple, vous pouvez modifier le texte d’une zone de texte pour modifier la valeur source sous-jacente.

Cependant, votre valeur source est-elle mise à jour pendant que vous modifiez le texte ou après avoir terminé l’édition du texte et le contrôle perd la mise au point? La <xref:System.Windows.Data.Binding.UpdateSourceTrigger?displayProperty=nameWithType> propriété détermine ce qui déclenche la mise à jour de la source. Les points des flèches droites dans la figure <xref:System.Windows.Data.Binding.UpdateSourceTrigger?displayProperty=nameWithType> suivante illustrent le rôle de la propriété.

![Diagramme qui montre le rôle de la propriété UpdateSourceTrigger.](./media/data-binding-overview/data-binding-updatesource-trigger.png)

Si `UpdateSourceTrigger` la <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged?displayProperty=nameWithType>valeur est, alors la valeur <xref:System.Windows.Data.BindingMode.TwoWay> indiquée <xref:System.Windows.Data.BindingMode.OneWayToSource> par la flèche droite ou les fixations est mise à jour dès que la propriété cible change. Toutefois, si `UpdateSourceTrigger` la <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>valeur est , alors cette valeur est seulement mise à jour avec la nouvelle valeur lorsque la propriété cible perd la mise au point.

Semblable à <xref:System.Windows.Data.Binding.Mode%2A> la propriété, différentes <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> propriétés de dépendance ont des valeurs par défaut différentes. La valeur par défaut de la plupart des propriétés de dépendance est <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>, tandis que celle de la propriété `TextBox.Text` a comme valeur par défaut <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>. `PropertyChanged`signifie que les mises à jour de source se produisent habituellement chaque fois que la propriété cible change. Les modifications instantanées sont très bien pour les CheckBoxes et autres contrôles simples. Cependant, pour les champs de texte, la mise à jour après chaque frappe peut diminuer les performances et prive l’utilisateur de la possibilité habituelle de backspace et de corriger les erreurs de frappe avant de s’engager à la nouvelle valeur.

Consultez <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> la page de propriété pour obtenir des renseignements sur la façon de trouver la valeur par défaut d’une propriété de dépendance.

Le tableau suivant fournit un <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> scénario <xref:System.Windows.Controls.TextBox> d’exemple pour chaque valeur en utilisant l’exemple.

| Valeur UpdateSourceTrigger | Lorsque la valeur source est mise à jour | Exemple de scénario pour TextBox |
| ------------------------- | ---------------------------------- | ---------------------------- |
| `LostFocus`(par <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType>défaut pour ) | Lorsque le contrôle TextBox perd la mise au point. | Une TextBox associée à la logique de validation (voir [Validation de données](#data-validation) ci-dessous). |
| `PropertyChanged` | Comme vous tapez dans le <xref:System.Windows.Controls.TextBox>. | TextBox contrôle dans une fenêtre de salle de chat. |
| `Explicit` | Lorsque l’application appelle <xref:System.Windows.Data.BindingExpression.UpdateSource%2A>. | TextBox contrôle sous un formulaire modifiable (mise à jour des valeurs de la source uniquement lorsque l’utilisateur clique sur le bouton soumettre). |

Par exemple, voir [comment : Contrôler lorsque le texte TextBox met à jour la source](../../framework/wpf/data/how-to-control-when-the-textbox-text-updates-the-source.md).

## <a name="creating-a-binding"></a>Création d’une liaison

Pour réaffirmer certains des concepts discutés dans les sections <xref:System.Windows.Data.Binding> précédentes, vous établissez une liaison à l’aide de l’objet, et chaque liaison comporte généralement quatre composantes : une cible contraignante, une propriété cible, une source contraignante et un chemin vers la valeur source à utiliser. Cette section explique comment configurer une liaison.

Prenons l’exemple suivant, dans lequel l’objet de source de liaison est une classe nommée *MyData* qui est définie dans l’espace de noms *SDKSample*. Pour des raisons de démonstration, *MyData* a une propriété à cordes nommée *ColorName* dont la valeur est définie à "Rouge". Par conséquent, cet exemple génère un bouton avec un arrière-plan rouge.

[!code-xaml[BindNonTextProperty](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/AutoConvertPropertyToColor.xaml#BindAutoConvertColor)]

Pour plus d’informations sur la syntaxe de déclaration contraignante et des exemples de la façon de mettre en place une liaison dans le code, voir [Aperçu des déclarations contraignantes](../../framework/wpf/data/binding-declarations-overview.md).

Si nous appliquons cet exemple à notre diagramme de base, l’illustration qui en résulte ressemble à ce qui suit. Ce chiffre décrit <xref:System.Windows.Data.BindingMode.OneWay> une liaison parce <xref:System.Windows.Data.BindingMode.OneWay> que la propriété Background prend en charge la liaison par défaut.

![Diagramme qui montre la propriété de fond de liaison de données.](./media/data-binding-overview/data-binding-button-background-example.png)

Vous pouvez vous demander pourquoi cette reliure fonctionne même si <xref:System.Windows.Controls.Control.Background%2A> la propriété <xref:System.Windows.Media.Brush> *ColorName* est de la chaîne de type tandis que la propriété est de type . Cette liaison utilise la conversion par défaut de type, qui est discutée dans la section [de conversion de données.](#data-conversion)

### <a name="specifying-the-binding-source"></a>Spécifier la source de liaison

Notez que dans l’exemple précédent, la source de liaison est spécifiée en définissant la propriété [DockPanel.DataContext.](xref:System.Windows.FrameworkElement.DataContext) Le <xref:System.Windows.Controls.Button> hérite <xref:System.Windows.FrameworkElement.DataContext%2A> alors de <xref:System.Windows.Controls.DockPanel>la valeur de l 'qui est son élément parent. Pour rappel, l’objet de source de liaison est un des quatre composants nécessaires d’une liaison. Par conséquent, sans objet de source de liaison spécifié, la liaison ne fait rien.

Il existe plusieurs façons de spécifier l’objet de source de liaison. L’utilisation de la <xref:System.Windows.FrameworkElement.DataContext%2A> propriété sur un élément parent est utile lorsque vous liez plusieurs propriétés à la même source. Cependant, il peut parfois être plus approprié de spécifier la source de liaison sur des déclarations de liaison individuelles. Pour l’exemple précédent, <xref:System.Windows.FrameworkElement.DataContext%2A> au lieu d’utiliser la propriété, vous pouvez spécifier la source de liaison en définissant la <xref:System.Windows.Data.Binding.Source%2A?displayProperty=nameWithType> propriété directement sur la déclaration contraignante du bouton, comme dans l’exemple suivant.

[!code-xaml[BindNonTextPropertyCompactBinding](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/AutoConvertPropertyToColor.xaml#BindAutoConvertColorCompactBinding)]

Outre le <xref:System.Windows.FrameworkElement.DataContext%2A> réglage direct de la propriété <xref:System.Windows.FrameworkElement.DataContext%2A> sur un élément, l’héritage de la valeur d’un ancêtre (comme <xref:System.Windows.Data.Binding.Source%2A?displayProperty=nameWithType> le bouton dans le premier exemple), et en spécifiant explicitement la source contraignante en définissant la propriété sur la liaison (comme le bouton le dernier exemple), vous pouvez également utiliser la <xref:System.Windows.Data.Binding.ElementName?displayProperty=nameWithType> propriété ou la <xref:System.Windows.Data.Binding.RelativeSource?displayProperty=nameWithType> propriété pour spécifier la source de liaison. La <xref:System.Windows.Data.Binding.ElementName%2A> propriété est utile lorsque vous vous liez à d’autres éléments de votre application, comme lorsque vous utilisez un curseur pour ajuster la largeur d’un bouton. La <xref:System.Windows.Data.Binding.RelativeSource%2A> propriété est utile lorsque la <xref:System.Windows.Controls.ControlTemplate> liaison <xref:System.Windows.Style>est spécifiée dans un ou un . Pour plus d’informations, voir [Comment : Spécifier la source de liaison](../../framework/wpf/data/how-to-specify-the-binding-source.md).

### <a name="specifying-the-path-to-the-value"></a>Spécifier le chemin vers la valeur

Si votre source de liaison est <xref:System.Windows.Data.Binding.Path?displayProperty=nameWithType> un objet, vous utilisez la propriété pour spécifier la valeur à utiliser pour votre liaison. Si vous êtes contraignant pour les <xref:System.Windows.Data.Binding.XPath?displayProperty=nameWithType> données XML, vous utilisez la propriété pour spécifier la valeur. Dans certains cas, il peut <xref:System.Windows.Data.Binding.Path%2A> être applicable d’utiliser la propriété même lorsque vos données sont XML. Par exemple, si vous souhaitez accéder à la propriété Nom d’un XmlNode retourné (à la suite d’une requête XPath), vous devez utiliser la <xref:System.Windows.Data.Binding.Path%2A> propriété en plus de la <xref:System.Windows.Data.Binding.XPath%2A> propriété.

Pour plus d’informations, voir le et <xref:System.Windows.Data.Binding.Path%2A> <xref:System.Windows.Data.Binding.XPath%2A> les propriétés.

Bien que nous <xref:System.Windows.Data.Binding.Path%2A> ayons souligné que la valeur à utiliser est l’un des quatre composants nécessaires d’une liaison, dans les scénarios que vous souhaitez lier à un objet entier, la valeur à utiliser serait la même que l’objet source contraignante. Dans ces cas, il s’agit de ne pas spécifier un <xref:System.Windows.Data.Binding.Path%2A>. Considérez l'exemple suivant.

[!code-xaml[EmptyBinding](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/EmptyBinding.xaml#EmptyBinding)]

L’exemple ci-dessus utilise la syntaxe de liaison vide : {Binding}. Dans ce cas, l’hérite <xref:System.Windows.Controls.ListBox> du dataContext d’un élément Parent DockPanel (non indiqué dans cet exemple). Lorsque le chemin d’accès n’est pas spécifié, le comportement par défaut consiste à lier à l’objet entier. En d’autres termes, dans cet exemple, le chemin <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> a été laissé de côté parce que nous lions la propriété à l’objet entier. (Voir la section [Liaison aux collections](#binding-to-collections) pour une discussion approfondie.)

En plus de la liaison à une collection, ce scénario est utile lorsque vous souhaitez lier un objet entier plutôt qu’une seule propriété d’un objet. Par exemple, si votre objet <xref:System.String>source est de type, vous pouvez simplement vous lier à la chaîne elle-même. Un autre scénario courant est lorsque vous souhaitez lier un élément à un objet avec plusieurs propriétés.

Vous devrez peut-être appliquer la logique personnalisée de sorte que les données soient significatives pour votre propriété cible liée. La logique personnalisée peut être sous la forme d’un convertisseur personnalisé si la conversion de type par défaut n’existe pas. Voir [la conversion de données](#data-conversion) pour obtenir des informations sur les convertisseurs.

### <a name="binding-and-bindingexpression"></a>Binding et BindingExpression

Avant d’entrer dans d’autres fonctionnalités et utilisations de la liaison de données, il est utile d’introduire la <xref:System.Windows.Data.BindingExpression> classe. Comme vous l’avez vu <xref:System.Windows.Data.Binding> dans les sections précédentes, la classe est la classe de haut niveau pour la déclaration d’une liaison; il fournit de nombreuses propriétés qui vous permettent de spécifier les caractéristiques d’une liaison. Une classe <xref:System.Windows.Data.BindingExpression>connexe, est l’objet sous-jacent qui maintient la connexion entre la source et la cible. Une liaison contient toutes les informations qui peuvent être partagées entre plusieurs expressions de liaison. A <xref:System.Windows.Data.BindingExpression> est une expression d’instance qui ne peut <xref:System.Windows.Data.Binding>pas être partagée et contient toutes les informations d’instance de la .

Prenons l’exemple `myDataObject` suivant, où `MyData` est `myBinding` un <xref:System.Windows.Data.Binding> cas de `MyData` la classe, est l’objet source, et est une classe définie qui contient une propriété à cordes nommée `MyDataProperty`. Cet exemple lie le `myText`contenu texte <xref:System.Windows.Controls.TextBlock>de `MyDataProperty`, une instance de , à .

[!code-csharp[CodeOnlyBinding](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/ManualBinding.cs#CodeOnlyBinding)]
[!code-vb[CodeOnlyBinding](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/ManualBinding.vb#CodeOnlyBinding)]

Vous pouvez utiliser le même objet *myBinding* pour créer d’autres liaisons. Par exemple, vous pouvez utiliser *l’objet myBinding* pour lier le contenu texte d’une case à cocher à *MyDataProperty*. Dans ce scénario, il y <xref:System.Windows.Data.BindingExpression> aura deux cas de partage de l’objet *myBinding.*

Un <xref:System.Windows.Data.BindingExpression> objet est <xref:System.Windows.Data.BindingOperations.GetBindingExpression%2A> retourné en faisant appel à un objet lié aux données. Les articles suivants démontrent certains des <xref:System.Windows.Data.BindingExpression> usages de la classe :

- [Obtenir l’objet de liaison d’une propriété cible liée](../../framework/wpf/data/how-to-get-the-binding-object-from-a-bound-target-property.md)

- [Contrôlez lorsque le texte TextBox met à jour la source](../../framework/wpf/data/how-to-control-when-the-textbox-text-updates-the-source.md)

## <a name="data-conversion"></a>Conversion de données

Dans la [section Création d’une reliure,](#creating-a-binding) le bouton est rouge parce que sa <xref:System.Windows.Controls.Control.Background%2A> propriété est liée à une propriété à cordes avec la valeur "Rouge". Cette valeur de chaîne fonctionne parce qu’un convertisseur de type est présent sur le <xref:System.Windows.Media.Brush> type pour convertir la valeur de la chaîne en un <xref:System.Windows.Media.Brush>.

Ajout de ces informations à la figure de la [création d’une](#creating-a-binding) section de liaison ressemble à ceci.

![Diagramme qui montre la propriété par défaut de liaison de données.](./media/data-binding-overview/data-binding-button-default-conversion.png)

Cependant, que faire si au lieu d’avoir une propriété de <xref:System.Windows.Media.Color>chaîne de type votre objet source de liaison a une propriété de *couleur* de type? Dans ce cas, pour que la liaison fonctionne, vous auriez besoin de <xref:System.Windows.Controls.Control.Background%2A> transformer d’abord la valeur de la propriété de *couleur* en quelque chose que la propriété accepte. Vous devez créer un convertisseur personnalisé <xref:System.Windows.Data.IValueConverter> en implémentant l’interface, comme dans l’exemple suivant.

[!code-csharp[CodeOnlyBinding](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/ColorBrushConverter.cs#ColorBrushConverter)]
[!code-vb[CodeOnlyBinding](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/ColorBrushConverter.vb#ColorBrushConverter)]

Consultez la rubrique <xref:System.Windows.Data.IValueConverter> (éventuellement en anglais) pour plus d'informations.

Maintenant, le convertisseur personnalisé est utilisé au lieu de la conversion par défaut, et notre diagramme ressemble à ceci.

![Diagramme qui montre le convertisseur personnalisé de liaison de données.](./media/data-binding-overview/data-binding-converter-color-example.png)

Pour rappel, des conversions par défaut peuvent être disponibles si des convertisseurs de type sont présents dans le type lié. Ce comportement dépendra des convertisseurs de type sont disponibles dans la cible. En cas de doute, créez votre propre convertisseur.

Voici quelques scénarios typiques où il est logique de mettre en œuvre un convertisseur de données :

- Vos données devraient s’afficher différemment, selon la culture. Par exemple, vous pouvez implémenter un convertisseur de devises ou un convertisseur de date/heure de calendrier basé sur les conventions utilisées dans une culture particulière.

- Les données utilisées ne sont pas nécessairement destinées à modifier la valeur du texte d’une propriété, mais plutôt à modifier une autre valeur, comme la source d’une image ou la couleur ou le style du texte affiché. Les convertisseurs peuvent être utilisés ici en convertissant la liaison d’une propriété qui peut ne pas sembler appropriée, comme la liaison d’un champ de texte à la propriété Background d’une cellule de tableau.

- Plus d’un contrôle ou plusieurs propriétés de contrôles sont liés aux mêmes données. Dans ce cas, la liaison principale peut afficher uniquement le texte, tandis que les autres liaisons gèrent des problèmes d’affichage spécifiques, mais utilisent toujours la même liaison comme informations source.

- Une propriété cible a une collection de <xref:System.Windows.Data.MultiBinding>fixations, qui est appelé . Pour <xref:System.Windows.Data.MultiBinding>, vous <xref:System.Windows.Data.IMultiValueConverter> utilisez une coutume pour produire une valeur finale à partir des valeurs des fixations. Par exemple, la couleur peut être calculée à partir des valeurs rouge, vert et bleu, qui peuvent être des valeurs à partir d’objets de source de liaison identiques ou différents. Voir <xref:System.Windows.Data.MultiBinding> pour les exemples et l’information.

## <a name="binding-to-collections"></a>Liaison aux collections

Un objet source contraignante peut être traité soit comme un seul objet dont les propriétés contiennent des données, soit comme une collecte de données d’objets polymorphes qui sont souvent regroupés (comme le résultat d’une requête à une base de données). Jusqu’à présent, nous n’avons discuté que de la liaison avec des objets uniques. Toutefois, la liaison à une collecte de données est un scénario courant. Par exemple, un scénario commun <xref:System.Windows.Controls.ItemsControl> est <xref:System.Windows.Controls.ListBox>d’utiliser un tel comme un , , <xref:System.Windows.Controls.ListView>ou <xref:System.Windows.Controls.TreeView> d’afficher une collecte de données, comme dans l’application montrée dans la section [Qu’est-ce qui est contraignant les données.](#what-is-data-binding)

Heureusement, notre diagramme de base est toujours applicable. Si vous liez une <xref:System.Windows.Controls.ItemsControl> collection, le diagramme ressemble à ceci.

![Diagramme qui montre l’objet de liaison de données ItemsControl.](./media/data-binding-overview/data-binding-itemscontrol.png)

Comme le montre ce diagramme, pour lier un objet de <xref:System.Windows.Controls.ItemsControl> collecte, <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A?displayProperty=nameWithType> la propriété est la propriété à utiliser. Vous pouvez `ItemsSource` penser comme le <xref:System.Windows.Controls.ItemsControl>contenu de la . La liaison <xref:System.Windows.Data.BindingMode.OneWay> est `ItemsSource` parce `OneWay` que la propriété prend en charge la liaison par défaut.

### <a name="how-to-implement-collections"></a>Comment mettre en œuvre les collections

Vous pouvez énumérer n’importe quelle <xref:System.Collections.IEnumerable> collection qui implémente l’interface. Toutefois, pour configurer des fixations dynamiques de manière à ce que les insertions <xref:System.Collections.Specialized.INotifyCollectionChanged> ou les suppressions dans la collection mettent automatiquement à jour l’interface, la collection doit implémenter l’interface. Cette interface expose un événement qui doit être déclenché chaque fois que la collection sous-jacente est modifiée.

WPF fournit <xref:System.Collections.ObjectModel.ObservableCollection%601> la classe, qui est une mise en œuvre intégrée d’une collecte de données qui expose l’interface. <xref:System.Collections.Specialized.INotifyCollectionChanged> Pour prendre pleinement en charge le transfert intégral des valeurs de données des objets <xref:System.ComponentModel.INotifyPropertyChanged> sources vers les cibles, chaque objet de votre collection qui prend en charge les propriétés li bindables doit également implémenter l’interface. Pour plus d’informations, voir [Aperçu des sources contraignantes](../../framework/wpf/data/binding-sources-overview.md).

Avant de mettre en œuvre votre propre collection, envisagez d’utiliser <xref:System.Collections.ObjectModel.ObservableCollection%601> ou l’une des classes de collecte existantes, telles que <xref:System.Collections.Generic.List%601>, <xref:System.Collections.ObjectModel.Collection%601>, et <xref:System.ComponentModel.BindingList%601>, parmi beaucoup d’autres. Si vous avez un scénario avancé et que <xref:System.Collections.IList>vous souhaitez implémenter votre propre collection, envisagez d’utiliser , qui fournit une collection non générique d’objets qui peuvent être consultés individuellement par l’index, et fournit ainsi les meilleures performances.

### <a name="collection-views"></a>Vues de collection

Une <xref:System.Windows.Controls.ItemsControl> fois que vous êtes lié à une collecte de données, vous pouvez trier, filtrer ou regrouper les données. Pour ce faire, vous utilisez des vues <xref:System.ComponentModel.ICollectionView> de collecte, qui sont des classes qui implémentent l’interface.

#### <a name="what-are-collection-views"></a>Quelles sont les vues de la collection?

Une vue de collection est une couche sur une collection de sources de liaison qui vous permet de parcourir et d’afficher la collection source sur la base de requêtes de tri, de filtrage et de groupage, sans avoir à modifier la collection source sous-jacente elle-même. Une vue de collection maintient également un pointeur vers l’élément actuel dans la collection. Si la collection source <xref:System.Collections.Specialized.INotifyCollectionChanged> implémente l’interface, les modifications soulevées par l’événement <xref:System.Collections.Specialized.INotifyCollectionChanged.CollectionChanged> sont propagées aux vues.

Étant donné que les vues ne modifient pas les collections source sous-jacentes, chaque collection source peut avoir plusieurs vues associées. Par exemple, vous pouvez avoir une collection d’objets *Task*. À l’aide de vues, vous pouvez afficher ces mêmes données de différentes façons. Par exemple, sur le côté gauche de votre page, vous souhaitez peut-être afficher les tâches triées par priorité et, sur le côté droit, les regrouper par domaine.

#### <a name="how-to-create-a-view"></a>Comment créer une vue

Un moyen de créer et utiliser une vue consiste à instancier l’objet de vue directement et de l’utiliser comme source de liaison. Par exemple, considérez l’application [de démonstration de liaison de données][data-binding-demo] indiquée dans la section [Qu’est-ce que la section de liaison de données.](#what-is-data-binding) L’application est implémentée de telle sorte que les <xref:System.Windows.Controls.ListBox> liaisons à une vue sur la collecte de données au lieu de la collecte de données directement. L’exemple suivant est extrait de l’application [de démonstration de liaison Data.][data-binding-demo] La <xref:System.Windows.Data.CollectionViewSource> classe est le proxy XAML d’une classe qui hérite de <xref:System.Windows.Data.CollectionView>. Dans cet exemple <xref:System.Windows.Data.CollectionViewSource.Source%2A> particulier, la vue est liée à la <xref:System.Collections.ObjectModel.ObservableCollection%601>collection *AuctionItems* (de type) de l’objet actuel de l’application.

[!code-xaml[CollectionView](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml#CollectionView)]

La ressource *listingDataView* sert alors de source contraignante pour <xref:System.Windows.Controls.ListBox>les éléments de l’application, tels que le .

[!code-xaml[ListBoxCollectionView](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml#ListBoxCollectionView)]

Pour créer une autre vue pour la <xref:System.Windows.Data.CollectionViewSource> même collection, `x:Key` vous pouvez créer une autre instance et lui donner un nom différent.

Le tableau suivant montre quels types de données de <xref:System.Windows.Data.CollectionViewSource> vue sont créés sous forme de vue de collecte par défaut ou en fonction du type de collecte source.

| Type de collection source                    | Type de vue de collection | Notes |
| ----------------------------------------- | -------------------- | ----- |
| <xref:System.Collections.IEnumerable>     | Un type interne basé sur<xref:System.Windows.Data.CollectionView> | Impossible de grouper les éléments. |
| <xref:System.Collections.IList>           | <xref:System.Windows.Data.ListCollectionView> | Le plus rapide. |
| <xref:System.ComponentModel.IBindingList> | <xref:System.Windows.Data.BindingListCollectionView> | |

#### <a name="using-a-default-view"></a>Utilisation d’une vue par défaut

La spécification d’une vue de collection comme source de liaison est un moyen de créer et utiliser une vue de collection. WPF crée également une vue de collection par défaut pour chaque collection utilisée comme source de liaison. Si vous liez directement à une collection, WPF crée une liaison sur sa vue par défaut. Cette vue par défaut est partagée par toutes les liaisons à la même collection, de sorte qu’une modification apportée à une vue par défaut par un contrôle ou un code lié (comme le tri ou une modification du pointeur d’élément actuel, discuté plus tard) est reflétée dans toutes les autres liaisons à la même collection.

Pour obtenir la vue par <xref:System.Windows.Data.CollectionViewSource.GetDefaultView%2A> défaut, vous utilisez la méthode. Par exemple, voir [Obtenez la vue par défaut d’une collecte de données](../../framework/wpf/data/how-to-get-the-default-view-of-a-data-collection.md).

#### <a name="collection-views-with-adonet-datatables"></a>Vues de collecte avec ADO.NET DataTables

Pour améliorer les performances, les <xref:System.Data.DataTable> vues <xref:System.Data.DataView> de collecte pour ADO.NET <xref:System.Data.DataView>ou objets déléguent le tri et le filtrage à la , ce qui provoque le tri et le filtrage d’être partagés sur toutes les vues de collecte de la source de données. Pour permettre à chaque vue de collection de trier et <xref:System.Data.DataView> de filtrer indépendamment, initialiser chaque vue de collection avec son propre objet.

#### <a name="sorting"></a>Tri

Comme mentionné précédemment, les vues peuvent appliquer un ordre de tri à une collection. Comme cela existe dans la collection sous-jacente, vos données peuvent avoir ou non un ordre inhérent pertinent. La vue sur la collection vous permet d’imposer un ordre, ou de modifier l’ordre par défaut, en fonction de critères de comparaison que vous fournissez. Comme il s’agit d’une vue de données côté client, un scénario courant est que l’utilisateur peut souhaiter trier les colonnes des données tabulaires par la valeur à laquelle la colonne correspond. À l’aide de vues, ce tri défini par l’utilisateur peut être appliqué, à nouveau sans apporter de modifications à la collection sous-jacente ou même avoir à redemander le contenu de la collection. Par exemple, voir [Sortez une colonne GridView lorsqu’un en-tête est cliqué](../../framework/wpf/controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md).

L’exemple suivant montre la logique de tri du <xref:System.Windows.Controls.CheckBox> "Sort by category and date" de l’interface utilisateur de l’application dans la section [Qu’est-ce que](#what-is-data-binding) la section de liaison de données.

[!code-csharp[AddSortChecked](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml.cs#AddSortChecked)]
[!code-vb[AddSortChecked](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/CollectionView.xaml.vb#AddSortChecked)]

#### <a name="filtering"></a>Filtrage

Les vues peuvent également appliquer un filtre à une collection, de sorte que la vue ne montre qu’un certain sous-ensemble de la collection complète. Vous pouvez filtrer sur une condition dans les données. Par exemple, comme le fait l’application dans la section [Qu’est-ce que](#what-is-data-binding) la liaison de données, le "Afficher uniquement les bonnes affaires" <xref:System.Windows.Controls.CheckBox> contient une logique pour filtrer les éléments qui coûtent 25 $ ou plus. Le code suivant est exécuté pour définir *ShowOnlyBargainsFilter* comme gestionnaire de l’événement <xref:System.Windows.Data.CollectionViewSource.Filter> lorsque cela <xref:System.Windows.Controls.CheckBox> est sélectionné.

[!code-csharp[ListingViewFilter](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml.cs#ListingViewFilter)]
[!code-vb[ListingViewFilter](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/CollectionView.xaml.vb#ListingViewFilter)]

Le gestionnaire *d’événements ShowOnlyBargainsFilter* a la mise en œuvre suivante.

[!code-csharp[FilterEvent](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml.cs#FilterEvent)]
[!code-vb[FilterEvent](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/CollectionView.xaml.vb#FilterEvent)]

Si vous utilisez l’une <xref:System.Windows.Data.CollectionView> des <xref:System.Windows.Data.CollectionViewSource>classes directement <xref:System.Windows.Data.CollectionView.Filter%2A> au lieu de , vous utiliseriez la propriété pour spécifier un rappel. Pour obtenir un exemple, consultez [Filtrer les données d'une vue](../../framework/wpf/data/how-to-filter-data-in-a-view.md).

#### <a name="grouping"></a>Regroupement

À l’exception de <xref:System.Collections.IEnumerable> la classe interne qui voit une collection, toutes les vues de collection prennent en charge le *regroupement,* ce qui permet à l’utilisateur de diviser la collection dans la vue de la collection en groupes logiques. Les groupes peuvent être explicites, si l’utilisateur fournit une liste de groupes, ou implicites, si les groupes sont générés dynamiquement en fonction des données.

L’exemple suivant montre la logique du <xref:System.Windows.Controls.CheckBox>"Groupe par catégorie" .

[!code-csharp[ListingGroupCheck](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml.cs#ListingGroupCheck)]
[!code-vb[ListingGroupCheck](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/CollectionView.xaml.vb#ListingGroupCheck)]

Pour un autre exemple de groupement, consultez [Grouper des éléments dans un ListView implémentant un GridView](../../framework/wpf/controls/how-to-group-items-in-a-listview-that-implements-a-gridview.md).

#### <a name="current-item-pointers"></a>Pointeurs d’élément actuels

Les vues prennent également en charge la notion d’élément actuel. Vous pouvez naviguer parmi les objets dans une vue de collection. Lorsque vous naviguez, vous déplacez un pointeur d’élément qui vous permet de récupérer l’objet qui existe à cet emplacement précis de la collection. Par exemple, voir [Naviguez à travers les objets dans une collection de donnéesView](../../framework/wpf/data/how-to-navigate-through-the-objects-in-a-data-collectionview.md).

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

Le pointeur d’élément actuel peut être affecté par tout tri ou filtrage appliqué à la collection. Le tri conserve le pointeur d’élément actuel sur le dernier élément sélectionné, mais la vue de collection est désormais restructurée autour du tri. (Peut-être l’élément sélectionné était au début de la liste avant, mais maintenant l’élément sélectionné pourrait être quelque part dans le milieu.) Le filtrage conserve l’élément sélectionné si cette sélection reste en vue après le filtrage. Sinon, le pointeur d’élément actuel est défini sur le premier élément de la vue de collection filtrée.

#### <a name="master-detail-binding-scenario"></a>Scénario de liaison Master-detail

La notion d’un élément actuel est utile non seulement pour le parcours d’éléments dans une collection, mais également pour le scénario de liaison maître/détail. Considérez l’interface utilisateur de l’application dans la section [Qu’est-ce que la liaison des données](#what-is-data-binding) à nouveau. Dans cette application, la <xref:System.Windows.Controls.ListBox> sélection dans le <xref:System.Windows.Controls.ContentControl>détermine le contenu montré dans le . Pour le dire d’une <xref:System.Windows.Controls.ListBox> autre manière, <xref:System.Windows.Controls.ContentControl> lorsqu’un élément est sélectionné, les détails de l’élément sélectionné.

Vous pouvez implémenter le scénario maître/détail simplement en ayant deux contrôles ou plus liés à la même vue. L’exemple suivant de la [démo de][data-binding-demo] <xref:System.Windows.Controls.ListBox> liaison <xref:System.Windows.Controls.ContentControl> de données montre la majoration de l’interface utilisateur et de l’utilisateur sur l’application dans la section [Qu’est-ce que](#what-is-data-binding) la liaison des données.

[!code-xaml[ListBoxContentControl](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml#ListBoxContentControl)]

Notez que les deux contrôles sont liés à la même source, la ressource statique *listDataView* (voir la définition de cette ressource dans la [façon de créer une section de vue](#how-to-create-a-view)). Cette liaison fonctionne parce que lorsqu’un objet singleton (le <xref:System.Windows.Controls.ContentControl> dans ce cas) <xref:System.Windows.Data.CollectionView.CurrentItem%2A> est lié à une vue de collection, il se lie automatiquement à la vue. Les <xref:System.Windows.Data.CollectionViewSource> objets synchronisent automatiquement la monnaie et la sélection. Si votre contrôle de liste <xref:System.Windows.Data.CollectionViewSource> n’est pas lié à un <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> objet `true` comme dans cet exemple, alors vous auriez besoin de définir sa propriété pour que cela fonctionne.

Pour d’autres exemples, voir [Bind à une collection et afficher des informations basées sur](../../framework/wpf/data/how-to-bind-to-a-collection-and-display-information-based-on-selection.md) la sélection et [utilisez le modèle de master-detail avec des données hiérarchiques](../../framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md).

Vous avez peut-être remarqué que l’exemple ci-dessus utilisait un modèle. En fait, les données ne seraient pas affichées comme nous le souhaitons <xref:System.Windows.Controls.ContentControl> sans l’utilisation de <xref:System.Windows.Controls.ListBox>modèles (celui explicitement utilisé par le et celui implicitement utilisé par le ). Nous passons maintenant aux modèles de données dans la section suivante.

## <a name="data-templating"></a>Modèles de données

Sans l’utilisation de modèles de données, notre interface utilisateur d’application dans la section [Ce qui est contraignant des données](#what-is-data-binding) ressemblerait à ce qui suit.

![Démo de liaison de données sans modèles de données](./media/data-binding-overview/demo-no-template.png)

Comme le montre l’exemple de <xref:System.Windows.Controls.ListBox> la section <xref:System.Windows.Controls.ContentControl> précédente, le contrôle et le sont liés à l’objet de collection entier (ou plus précisément, la vue sur l’objet de collection) de *AuctionItem*s. Sans instructions spécifiques sur la façon <xref:System.Windows.Controls.ListBox> d’afficher la collecte de données, la <xref:System.Windows.Controls.ContentControl> représentation des chaînes de chaque objet dans la collection sous-jacente, et les affiches la représentation de la chaîne de l’objet, il est lié à.

Pour résoudre ce problème, <xref:System.Windows.DataTemplate?text=DataTemplates>l’application définit . Comme le montre l’exemple de <xref:System.Windows.Controls.ContentControl> la section précédente, l’utilisation explicite du modèle *de donnéesProductListingTemplate.* Le <xref:System.Windows.Controls.ListBox> contrôle utilise implicitement le modèle de données suivant lors de l’affichage des objets *AuctionItem* dans la collection.

[!code-xaml[AuctionItemDataTemplate](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml#AuctionItemDataTemplate)]

Avec l’utilisation de ces deux DataTemplates, l’interface utilisateur qui en résulte est celle indiquée dans la section [Qu’est-ce qui est contraignante](#what-is-data-binding) par les données. Comme vous pouvez le voir à partir de cette capture d’écran, en plus de vous laisser placer des données dans vos contrôles, DataTemplates vous permettent de définir des visuels convaincants pour vos données. Par <xref:System.Windows.DataTrigger>exemple, s sont <xref:System.Windows.DataTemplate> utilisés dans ce qui précède de sorte que *AuctionItem*s avec la valeur *SpecialFeatures* de *HighLight* serait affiché avec une bordure orange et une étoile.

Pour plus d’informations sur les modèles de données, consultez [l’aperçu des données.](../../framework/wpf/data/data-templating-overview.md)

## <a name="data-validation"></a>Validation des données

La plupart des applications qui prennent l’entrée de l’utilisateur doivent avoir une logique de validation pour s’assurer que l’utilisateur a saisi les informations attendues. Les vérifications de validation peuvent être basées sur le type, la plage, le format ou d’autres exigences spécifiques à l’application. Cette section traite du fonctionnement de la validation des données dans WPF.

### <a name="associating-validation-rules-with-a-binding"></a>Associer les règles de validation à une

Le modèle de liaison de <xref:System.Windows.Data.Binding.ValidationRules%2A> données <xref:System.Windows.Data.Binding> WPF vous permet de vous associer à votre objet. Par exemple, l’exemple <xref:System.Windows.Controls.TextBox> suivant lie `StartPrice` une propriété <xref:System.Windows.Controls.ExceptionValidationRule> nommée <xref:System.Windows.Data.Binding.ValidationRules%2A?displayProperty=nameWithType> et ajoute un objet à la propriété.

[!code-xaml[TextboxStartPrice](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/DataValidation.xaml#TextboxStartPrice)]

Un <xref:System.Windows.Controls.ValidationRule> objet vérifie si la valeur d’une propriété est valide. WPF dispose de deux <xref:System.Windows.Controls.ValidationRule> types d’objets intégrés :

- Un <xref:System.Windows.Controls.ExceptionValidationRule> contrôle des exceptions jetées lors de la mise à jour de la propriété source de liaison. Dans l’exemple précédent, `StartPrice` est de type entier. Lorsque l’utilisateur entre une valeur qui ne peut pas être convertie en un entier, une exception est levée, ce qui marque la liaison comme étant non valide. Une autre syntaxe <xref:System.Windows.Controls.ExceptionValidationRule> à définir <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> le `true` explicitement <xref:System.Windows.Data.Binding> est <xref:System.Windows.Data.MultiBinding> de définir la propriété sur votre ou l’objet.

- Un <xref:System.Windows.Controls.DataErrorValidationRule> objet vérifie les erreurs qui sont <xref:System.ComponentModel.IDataErrorInfo> soulevées par des objets qui implémentent l’interface. Pour un exemple d’utilisation <xref:System.Windows.Controls.DataErrorValidationRule>de cette règle de validation, voir . Une autre syntaxe <xref:System.Windows.Controls.DataErrorValidationRule> à définir <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> le `true` explicitement <xref:System.Windows.Data.Binding> est <xref:System.Windows.Data.MultiBinding> de définir la propriété sur votre ou l’objet.

Vous pouvez également créer votre propre règle <xref:System.Windows.Controls.ValidationRule> de validation en <xref:System.Windows.Controls.ValidationRule.Validate%2A> provenant de la classe et en mettant en œuvre la méthode. L’exemple suivant montre la règle utilisée par <xref:System.Windows.Controls.TextBox> la liste de produits *Add* "Date de début" de la section [Qu’est-ce que](#what-is-data-binding) la liaison des données.

[!code-csharp[FutureDateRule](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/FutureDateRule.cs#FutureDateRule)]
[!code-vb[FutureDateRule](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/FutureDateRule.vb#FutureDateRule)]

Le *StartDateEntryForm* <xref:System.Windows.Controls.TextBox> utilise ce *FutureDateRule*, comme le montre l’exemple suivant.

[!code-xaml[TextboxStartDate](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/DataValidation.xaml#TextboxStartDate)]

Parce <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> que <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>la valeur est , le moteur de liaison met à jour <xref:System.Windows.Data.Binding.ValidationRules%2A> la valeur source sur chaque frappe, ce qui signifie qu’il vérifie également chaque règle dans la collection sur chaque frappe. Nous reviendrons plus tard là-dessus dans la section Processus de validation.

### <a name="providing-visual-feedback"></a>Fournir des commentaires visuels

Si l’utilisateur entre dans une valeur invalide, vous pouvez fournir des commentaires sur l’erreur sur l’interface utilisateur de l’application. Une façon de fournir une <xref:System.Windows.Controls.Validation.ErrorTemplate%2A?displayProperty=nameWithType> telle rétroaction est <xref:System.Windows.Controls.ControlTemplate>de définir la propriété ci-jointe à une coutume . Comme le montre la sous-section précédente, le *StartDateEntryForm* <xref:System.Windows.Controls.TextBox> utilise une <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> validation *appeléeTemplate*. L’exemple suivant montre la définition de *validationTemplate*.

[!code-xaml[ControlTemplate](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/DataValidation.xaml#ControlTemplate)]

L’élément <xref:System.Windows.Controls.AdornedElementPlaceholder> précise où le contrôle orné doit être placé.

En outre, vous pouvez <xref:System.Windows.Controls.ToolTip> également utiliser un pour afficher le message d’erreur. Le *StartDateEntryForm* et le *StartPriceEntryForm*<xref:System.Windows.Controls.TextBox>es utilisent le style <xref:System.Windows.Controls.ToolTip> *textStyleTextBox*, qui crée un message qui affiche le message d’erreur. L’exemple suivant montre la définition de *textStyleTextBox*. La propriété <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> `true` ci-jointe est lorsque l’une ou plusieurs des liaisons sur les propriétés de l’élément lié sont erronées.

[!code-xaml[TextBoxStyle](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/DataValidation.xaml#TextBoxStyle)]

Avec la <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> coutume <xref:System.Windows.Controls.ToolTip>et le , le *StartDateEntryForm* <xref:System.Windows.Controls.TextBox> ressemble à ce qui suit quand il ya une erreur de validation.

![Erreur de validation de la liaison de données](./media/data-binding-overview/demo-validation-date.png "DataBindingDemo_Validation")

Si <xref:System.Windows.Data.Binding> vous avez associé des règles <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> de validation mais que <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> vous ne spécifiez pas un contrôle sur la limite, un défaut sera utilisé pour informer les utilisateurs lorsqu’il y a une erreur de validation. La <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> valeur par défaut est un modèle de contrôle qui définit une bordure rouge dans la couche d’adorant. Avec la <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> valeur <xref:System.Windows.Controls.ToolTip>par défaut et le , l’interface utilisateur de la *StartPriceEntryForm* <xref:System.Windows.Controls.TextBox> ressemble à ce qui suit quand il ya une erreur de validation.

![Erreur de validation de la liaison de données](./media/data-binding-overview/demo-validation-price.png "DataBindingDemo_ValidationDefault")

Pour un exemple de la façon de fournir la logique pour valider tous les contrôles dans une boîte de dialogue, voir la section Boîtes de dialogue personnalisé dans [l’aperçu des boîtes de dialogue](../../framework/wpf/app-development/dialog-boxes-overview.md).

### <a name="validation-process"></a>Processus de validation

La validation se produit généralement lorsque la valeur d’une cible est transférée à la propriété de source de liaison. Ce transfert <xref:System.Windows.Data.BindingMode.TwoWay> se <xref:System.Windows.Data.BindingMode.OneWayToSource> produit sur et les fixations. Pour réitérer, ce qui provoque une <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> mise à jour source dépend de la valeur de la propriété, tel que décrit dans la section [Ce qui déclenche les mises à jour de source.](#what-triggers-source-updates)

Les éléments suivants décrivent le processus *de validation.* Si une erreur de validation ou un autre type d’erreur se produit à tout moment au cours de ce processus, le processus est interrompu :

1. Le moteur de liaison vérifie <xref:System.Windows.Controls.ValidationRule> s’il ya des objets personnalisés définis dont <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> il <xref:System.Windows.Controls.ValidationStep.RawProposedValue> est réglé pour cela , auquel cas il appelle la <xref:System.Windows.Data.Binding> <xref:System.Windows.Controls.ValidationRule.Validate%2A> méthode sur chacun <xref:System.Windows.Controls.ValidationRule> jusqu’à ce que l’un d’eux se heurte à une erreur ou jusqu’à ce que tous passent.

2. Le moteur de liaison appelle alors le convertisseur, s’il en existe un.

3. Si le convertisseur réussit, le moteur de <xref:System.Windows.Controls.ValidationRule> liaison <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> vérifie s’il y a des objets personnalisés définis à qui est réglé <xref:System.Windows.Controls.ValidationStep.ConvertedProposedValue> pour cela, auquel cas il appelle la <xref:System.Windows.Data.Binding> <xref:System.Windows.Controls.ValidationRule.Validate%2A> méthode sur chacun <xref:System.Windows.Controls.ValidationRule> qui a <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> mis à jusqu’à ce que l’un d’eux se heurte à une erreur ou jusqu’à <xref:System.Windows.Controls.ValidationStep.ConvertedProposedValue> ce que tous passent.

4. Le moteur de liaison définit la propriété source.

5. Le moteur de liaison vérifie <xref:System.Windows.Controls.ValidationRule> s’il ya des objets personnalisés définis <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> dont il est réglé <xref:System.Windows.Controls.ValidationStep.UpdatedValue> pour cela , auquel cas il appelle la <xref:System.Windows.Data.Binding> <xref:System.Windows.Controls.ValidationRule.Validate%2A> méthode sur chacun <xref:System.Windows.Controls.ValidationRule> qui a <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> mis à jusqu’à ce que l’un d’eux se heurte à une erreur ou jusqu’à <xref:System.Windows.Controls.ValidationStep.UpdatedValue> ce que tous passent. Si <xref:System.Windows.Controls.DataErrorValidationRule> un est associé à <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> une liaison et <xref:System.Windows.Controls.ValidationStep.UpdatedValue>son <xref:System.Windows.Controls.DataErrorValidationRule> est réglé à la valeur par défaut, , le est vérifié à ce stade. À ce stade, toute <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> liaison `true` qui a le set à est vérifiée.

6. Le moteur de liaison vérifie <xref:System.Windows.Controls.ValidationRule> s’il ya des objets personnalisés définis <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> dont il est réglé <xref:System.Windows.Controls.ValidationStep.CommittedValue> pour cela , auquel cas il appelle la <xref:System.Windows.Data.Binding> <xref:System.Windows.Controls.ValidationRule.Validate%2A> méthode sur chacun <xref:System.Windows.Controls.ValidationRule> qui a <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> mis à jusqu’à ce que l’un d’eux se heurte à une erreur ou jusqu’à <xref:System.Windows.Controls.ValidationStep.CommittedValue> ce que tous passent.

Si <xref:System.Windows.Controls.ValidationRule> un ne passe pas à tout moment tout <xref:System.Windows.Controls.ValidationError> au long de <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> ce processus, le moteur de liaison crée un objet et l’ajoute à la collection de l’élément lié. Avant que le <xref:System.Windows.Controls.ValidationRule> moteur de liaison ne exécute <xref:System.Windows.Controls.ValidationError> les objets à <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> une étape donnée, il supprime tout ce qui a été ajouté à la propriété ci-jointe de l’élément lié au cours de cette étape. Par exemple, <xref:System.Windows.Controls.ValidationRule> si <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> un <xref:System.Windows.Controls.ValidationStep.UpdatedValue> dont est réglé pour échouer, la prochaine fois <xref:System.Windows.Controls.ValidationError> que le <xref:System.Windows.Controls.ValidationRule> processus <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> de <xref:System.Windows.Controls.ValidationStep.UpdatedValue>validation se produit, le moteur de liaison supprime que immédiatement avant qu’il appelle tout ce qui a réglé à .

Quand <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> n’est <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> pas vide, la propriété `true`ci-jointe de l’élément est définie à . En outre, <xref:System.Windows.Data.Binding.NotifyOnValidationError%2A> si <xref:System.Windows.Data.Binding> la propriété `true`de la est <xref:System.Windows.Controls.Validation.Error?displayProperty=nameWithType> réglée à , alors le moteur de fixation soulève l’événement ci-joint sur l’élément.

Notez également qu’un transfert de valeur valide dans les deux <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> sens (cible à source ou source à cibler) efface la propriété ci-jointe.

Si la fixation <xref:System.Windows.Controls.ExceptionValidationRule> a une obligation associée <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> à elle, ou si la propriété est réglée `true` et une exception est lancée <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A>lorsque le moteur de fixation définit la source, le moteur de liaison vérifie s’il ya un . Vous avez la possibilité <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A> d’utiliser le rappel pour fournir un gestionnaire personnalisé pour le traitement des exceptions. Si <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A> un n’est <xref:System.Windows.Data.Binding>pas spécifié sur <xref:System.Windows.Controls.ValidationError> le , le moteur <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> de liaison crée un à l’exception et l’ajoute à la collection de l’élément lié.

## <a name="debugging-mechanism"></a>Mécanisme de débâage

Vous pouvez définir <xref:System.Diagnostics.PresentationTraceSources.TraceLevel%2A?displayProperty=nameWithType> la propriété ci-jointe sur un objet lié à la liaison pour recevoir des informations sur l’état d’une liaison spécifique.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Controls.DataErrorValidationRule>
- [Se lier aux résultats d’une requête LINQ](../../framework/wpf/data/how-to-bind-to-the-results-of-a-linq-query.md)
- [Liaison de données](../../framework/wpf/advanced/optimizing-performance-data-binding.md)
- [Démo de liaison de données][data-binding-demo]
- [Articles comment faire](../../framework/wpf/data/data-binding-how-to-topics.md)
- [Établir une liaison à une source de données ADO.NET](../../framework/wpf/data/how-to-bind-to-an-ado-net-data-source.md)

[data-binding-demo]: https://github.com/microsoft/WPF-Samples/tree/master/Sample%20Applications/DataBindingDemo "application de démonstration de liaison de données"
