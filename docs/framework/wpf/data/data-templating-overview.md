---
title: Vue d'ensemble des modèles de données
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], templates
- binding data [WPF], templates
- templates [WPF], data
- data templates [WPF]
ms.assetid: 0f4d9f8c-0230-4013-bd7b-e8e7fed01b4a
ms.openlocfilehash: b9e55eac1c72cd3deec21754373da4364a7cfed2
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646462"
---
# <a name="data-templating-overview"></a>Vue d'ensemble des modèles de données
Le modèle de création de modèles de données WPF offre une grande souplesse pour définir la présentation des données. Les contrôles WPF possèdent des fonctionnalités intégrées permettant de prendre en charge la personnalisation de la présentation des données. Ce sujet montre d’abord <xref:System.Windows.DataTemplate> comment définir un, puis introduit d’autres fonctionnalités de templating de données, telles que la sélection de modèles basés sur la logique personnalisée et le support pour l’affichage des données hiérarchiques.

<a name="Prerequisites"></a>
## <a name="prerequisites"></a>Prérequis
 Cette rubrique porte sur les fonctionnalités de création de modèles de données ; elle ne constitue pas une introduction aux concepts de liaison de données. Pour plus d’informations sur les concepts de base de la liaison de données, consultez la [Vue d’ensemble de la liaison de données](../../../desktop-wpf/data/data-binding-overview.md).

 <xref:System.Windows.DataTemplate>est sur la présentation des données et est l’une des nombreuses fonctionnalités fournies par le style WPF et le modèle de templating. Pour une introduction du modèle de style WPF et de <xref:System.Windows.Style> templating, comme la façon d’utiliser un pour définir des propriétés sur les contrôles, voir le [thème Styling et Templating.](../../../desktop-wpf/fundamentals/styles-templates-overview.md)

 En outre, il est `Resources`important de comprendre , <xref:System.Windows.Style> qui <xref:System.Windows.DataTemplate> sont essentiellement ce qui permet à des objets tels que et d’être réutilisables. Pour plus d’informations sur les ressources, consultez la page [Ressources XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md).

<a name="DataTemplating_Basic"></a>
## <a name="data-templating-basics"></a>Informations de base sur la création de modèles de données

 Pour démontrer <xref:System.Windows.DataTemplate> pourquoi est important, passons par un exemple contraignant de données. Dans cet exemple, <xref:System.Windows.Controls.ListBox> nous avons un qui `Task` est lié à une liste d’objets. Chaque objet `Task` a un `TaskName` (chaîne), une `Description` (chaîne), une `Priority` (entier) et une propriété de type `TaskType`, qui est un `Enum` avec des valeurs `Home` et `Work`.

 [!code-xaml[DataTemplatingIntro_snip#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#resources)]
[!code-xaml[DataTemplatingIntro_snip#UI1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#ui1)]
[!code-xaml[DataTemplatingIntro_snip#UI2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#ui2)]

<a name="without_a_datatemplate"></a>
### <a name="without-a-datatemplate"></a>Sans DataTemplate
 Sans <xref:System.Windows.DataTemplate>un <xref:System.Windows.Controls.ListBox> , notre ressemble actuellement à ceci:

 ![Capture d’écran de l’échantillon de templating de données](./media/datatemplatingintro-fig1.png "DataTemplatingIntro_fig1")

 Ce qui se passe, c’est <xref:System.Windows.Controls.ListBox> que `ToString` sans instructions spécifiques, les appels par défaut lorsque vous essayez d’afficher les objets de la collection. Par conséquent, `Task` si l’objet l’emporte sur la `ToString` méthode, alors l’affichage <xref:System.Windows.Controls.ListBox> de la représentation de chaîne de chaque objet source dans la collection sous-jacente.

 Par exemple, si la classe `Task` remplace la méthode `ToString` de cette façon, où `name` correspond au champ de la propriété `TaskName` :

 [!code-csharp[DataTemplatingIntro_snip#ToString](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Data.cs#tostring)]
 [!code-vb[DataTemplatingIntro_snip#ToString](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataTemplatingIntro_snip/visualbasic/data.vb#tostring)]

 Ensuite, <xref:System.Windows.Controls.ListBox> le ressemble à ce qui suit:

 ![Capture d’écran de l’échantillon de templating de données](./media/datatemplatingintro-fig2.png "DataTemplatingIntro_fig2")

 Toutefois, cet affichage est restrictif et rigide. En outre, si vous êtes contraignant aux données XML, `ToString`vous ne seriez pas en mesure de remplacer .

<a name="defining_simple_datatemplate"></a>
### <a name="defining-a-simple-datatemplate"></a>Définir un DataTemplate simple
 La solution est <xref:System.Windows.DataTemplate>de définir un . Une façon de le faire <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> est <xref:System.Windows.Controls.ListBox> de <xref:System.Windows.DataTemplate>définir la propriété de la à un . Ce que vous <xref:System.Windows.DataTemplate> spécifiez dans votre devient la structure visuelle de votre objet de données. Ce <xref:System.Windows.DataTemplate> qui suit est assez simple. Nous donnons des instructions que <xref:System.Windows.Controls.TextBlock> chaque élément <xref:System.Windows.Controls.StackPanel>apparaît comme trois éléments dans un . Chaque <xref:System.Windows.Controls.TextBlock> élément est lié à `Task` une propriété de la classe.

 [!code-xaml[DataTemplatingIntro_snip#Inline](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#inline)]

 Les données sous-jacentes pour les exemples dans ce sujet est une collection d’objets CLR. Si vous êtes contraignant pour les données XML, les concepts fondamentaux sont les mêmes, mais il ya une légère différence syntaxique. Par exemple, au `Path=TaskName`lieu d’avoir , vous définiriez <xref:System.Windows.Data.Binding.XPath%2A> à `@TaskName` (si `TaskName` est un attribut de votre nœud XML).

 Maintenant, <xref:System.Windows.Controls.ListBox> notre ressemble à ce qui suit:

 ![Capture d’écran de l’échantillon de templating de données](./media/datatemplatingintro-fig3.png "DataTemplatingIntro_fig3")

<a name="defining_datatemplate_as_a_resource"></a>
### <a name="creating-the-datatemplate-as-a-resource"></a>Créer un DataTemplate comme ressource
 Dans l’exemple ci-dessus, nous avons défini l’inline. <xref:System.Windows.DataTemplate> Il est plus courant de le définir dans la section des ressources afin d’en faire un objet réutilisable, comme dans l’exemple suivant :

 [!code-xaml[DataTemplatingIntro_snip#R1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r1)]
[!code-xaml[DataTemplatingIntro_snip#AsResource](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#asresource)]
[!code-xaml[DataTemplatingIntro_snip#R2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r2)]

 Vous pouvez à présent utiliser `myTaskTemplate` comme ressource, comme dans l’exemple suivant :

 [!code-xaml[DataTemplatingIntro_snip#MyTaskTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#mytasktemplate)]

 Parce `myTaskTemplate` que c’est une ressource, vous pouvez maintenant l’utiliser sur d’autres contrôles qui ont une propriété qui prend un <xref:System.Windows.DataTemplate> type. Comme indiqué ci-dessus, <xref:System.Windows.Controls.ItemsControl> pour <xref:System.Windows.Controls.ListBox>les objets, tels que le , c’est la <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> propriété. Pour <xref:System.Windows.Controls.ContentControl> les objets, <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> c’est la propriété.

<a name="Styling_DataType"></a>
### <a name="the-datatype-property"></a>La propriété DataType
 La <xref:System.Windows.DataTemplate> classe <xref:System.Windows.DataTemplate.DataType%2A> a une propriété qui <xref:System.Windows.Style.TargetType%2A> est <xref:System.Windows.Style> très similaire à la propriété de la classe. Par conséquent, au `x:Key` lieu <xref:System.Windows.DataTemplate> de spécifier un pour l’exemple ci-dessus, vous pouvez faire ce qui suit:

 [!code-xaml[DataTemplatingIntro_snip#DataType](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#datatype)]

 Cela <xref:System.Windows.DataTemplate> est appliqué `Task` automatiquement à tous les objets. Notez que, dans ce cas, la `x:Key` est définie implicitement. Par conséquent, si <xref:System.Windows.DataTemplate> `x:Key` vous attribuez cette valeur, `x:Key` vous <xref:System.Windows.DataTemplate> l’emportez sur l’implicite et le ne serait pas appliqué automatiquement.

 Si vous <xref:System.Windows.Controls.ContentControl> liez une `Task` collection d’objets, <xref:System.Windows.Controls.ContentControl> le <xref:System.Windows.DataTemplate> ne fonctionne pas automatiquement. C’est parce que <xref:System.Windows.Controls.ContentControl> la liaison sur un besoin de plus d’informations pour distinguer si vous voulez lier à une collection entière ou les objets individuels. Si <xref:System.Windows.Controls.ContentControl> vous suivez la <xref:System.Windows.Controls.ItemsControl> sélection d’un <xref:System.Windows.Data.Binding.Path%2A> type, <xref:System.Windows.Controls.ContentControl> vous pouvez`/`définir la propriété de la liaison à " pour indiquer que vous êtes intéressé par l’élément actuel. Vous trouverez un exemple sur la page [Effectuer une liaison à une collection et afficher des informations en fonction de la sélection](how-to-bind-to-a-collection-and-display-information-based-on-selection.md). Dans le cas contraire, vous devez spécifier explicitement <xref:System.Windows.DataTemplate> en définissant la <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> propriété.

 La <xref:System.Windows.DataTemplate.DataType%2A> propriété est particulièrement <xref:System.Windows.Data.CompositeCollection> utile lorsque vous avez un des différents types d’objets de données. Vous trouverez un exemple sur la page [Implémenter une CompositeCollection](how-to-implement-a-compositecollection.md).

<a name="adding_more_to_datatemplate"></a>
## <a name="adding-more-to-the-datatemplate"></a>Ajouter d’autres informations au DataTemplate
 Actuellement, les données s’affichent avec les informations nécessaires, mais on peut sans problème aller plus loin. Améliorons la présentation en <xref:System.Windows.Controls.Border>ajoutant <xref:System.Windows.Controls.Grid>un <xref:System.Windows.Controls.TextBlock> , un , et certains éléments qui décrivent les données qui sont affichées.

 [!code-xaml[DataTemplatingIntro#AddingMore](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore)]
[!code-xaml[DataTemplatingIntro#AddingMore2](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore2)]

 La capture d’écran suivante montre le <xref:System.Windows.Controls.ListBox> avec ce modifié: <xref:System.Windows.DataTemplate>

 ![Capture d’écran de l’échantillon de templating de données](./media/datatemplatingintro-fig4.png "DataTemplatingIntro_fig4")

 Nous pouvons <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> <xref:System.Windows.HorizontalAlignment.Stretch> régler <xref:System.Windows.Controls.ListBox> sur le pour s’assurer que la largeur des éléments prend tout l’espace:

 [!code-xaml[DataTemplatingIntro_snip#Stretch](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#stretch)]

 Avec <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> la propriété <xref:System.Windows.HorizontalAlignment.Stretch>réglée <xref:System.Windows.Controls.ListBox> à , le ressemble maintenant à ceci:

 ![Capture d’écran de l’échantillon de templating de données](./media/datatemplatingintro-fig5.png "DataTemplatingIntro_fig5")

<a name="DataTrigger_to_Apply_Property_Values"></a>
### <a name="use-datatriggers-to-apply-property-values"></a>Utiliser DataTrigger pour appliquer des valeurs de propriété
 La présentation actuelle n’indique pas si une `Task` est une tâche privée ou une tâche professionnelle. N’oubliez pas que l’objet `Task` a une propriété `TaskType` de type `TaskType`, qui est une énumération avec les valeurs `Home` et `Work`.

 Dans l’exemple <xref:System.Windows.DataTrigger> suivant, <xref:System.Windows.Controls.Border.BorderBrush%2A> les définit `border` `Yellow` l’élément nommé à si la `TaskType` propriété est `TaskType.Home`.

 [!code-xaml[DataTemplatingIntro#DT](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#dt)]
[!code-xaml[DataTemplatingIntro#DataTrigger](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#datatrigger)]
[!code-xaml[DataTemplatingIntro#AddingMore2](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore2)]

 Notre application se présente maintenant ainsi. Les tâches privées apparaissent avec une bordure jaune et les tâches professionnelles avec une bordure cyan :

 ![Capture d’écran de l’échantillon de templating de données](./media/datatemplatingintro-fig6.png "DataTemplatingIntro_fig6")

 Dans cet <xref:System.Windows.DataTrigger> exemple, <xref:System.Windows.Setter> l’utilisation d’un pour définir une valeur de propriété. Les classes de <xref:System.Windows.TriggerBase.EnterActions%2A> déclenchement <xref:System.Windows.TriggerBase.ExitActions%2A> ont également le et les propriétés qui vous permettent de démarrer un ensemble d’actions telles que les animations. En outre, il <xref:System.Windows.MultiDataTrigger> existe également une classe qui vous permet d’appliquer des modifications basées sur plusieurs valeurs de propriété liées aux données.

 Une autre façon d’obtenir le <xref:System.Windows.Controls.Border.BorderBrush%2A> même effet `TaskType` est de lier la propriété à `TaskType` la propriété et d’utiliser un convertisseur de valeur pour retourner la couleur basée sur la valeur. Du point de vue des performances, il est légèrement plus efficace d’utiliser un convertisseur pour produire cet effet. En outre, le fait de créer votre propre convertisseur vous offre plus de souplesse, car vous fournissez votre propre logique. En somme, la technique choisie dépend du scénario et des préférences. Pour plus d’informations sur la <xref:System.Windows.Data.IValueConverter>façon d’écrire un convertisseur, voir .

<a name="what_belongs_in_datatemplate"></a>
### <a name="what-belongs-in-a-datatemplate"></a>Que contient un DataTemplate ?

Dans l’exemple précédent, nous <xref:System.Windows.DataTemplate> avons <xref:System.Windows.DataTemplate.Triggers%2A?displayProperty=nameWithType> placé le déclencheur dans l’utilisation de la propriété. Le <xref:System.Windows.Setter> déclencheur définit la valeur d’une propriété <xref:System.Windows.Controls.Border> d’un élément <xref:System.Windows.DataTemplate>(l’élément) qui est dans le . Toutefois, si les `Setters` propriétés qui vous concernent ne sont <xref:System.Windows.DataTemplate>pas des propriétés d’éléments qui <xref:System.Windows.Style> sont dans <xref:System.Windows.Controls.ListBoxItem> le courant, il peut <xref:System.Windows.Controls.ListBox>être plus approprié de définir les propriétés en utilisant un qui est pour la classe (si le contrôle que vous êtes contraignant est un ). Par exemple, si <xref:System.Windows.Trigger> vous voulez que <xref:System.Windows.UIElement.Opacity%2A> vous animiez la valeur de l’article lorsqu’une souris pointe vers un élément, vous définissez les déclencheurs dans un <xref:System.Windows.Controls.ListBoxItem> style. Vous trouverez un exemple sur la page [Présentation d’un exemple de création de style et de modèle](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).

 En général, gardez à <xref:System.Windows.DataTemplate> l’esprit que le <xref:System.Windows.Controls.ListBoxItem> est appliqué à chacun des produits générés <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> (pour plus d’informations sur la façon et où il est effectivement appliqué, voir la page.). Vous <xref:System.Windows.DataTemplate> ne vous préoccupez que de la présentation et de l’apparence des objets de données. Dans la plupart des cas, tous les autres aspects de la présentation, tels que ce qu’est un élément ressemble quand il est sélectionné ou comment l’exposer <xref:System.Windows.Controls.ListBox> les éléments, n’appartiennent pas à la définition d’un <xref:System.Windows.DataTemplate>. Vous trouverez un exemple dans la section [Création de styles et de modèles pour un ItemsControl](#DataTemplating_ItemsControl).

<a name="Styling_StyleSelection"></a>
## <a name="choosing-a-datatemplate-based-on-properties-of-the-data-object"></a>Choisir un DataTemplate en fonction des propriétés de l’objet de données
 Dans la section [La propriété DataType](#Styling_DataType), nous avons expliqué que vous pouvez définir différents modèles de données pour différents objets de données. C’est particulièrement utile <xref:System.Windows.Data.CompositeCollection> lorsque vous avez un de différents types ou collections avec des éléments de différents types. Dans la section [Données d’utilisation pour appliquer les valeurs de propriété,](#DataTrigger_to_Apply_Property_Values) nous avons montré que <xref:System.Windows.DataTemplate> si vous avez une collection du même type d’objets de données, vous pouvez créer un, puis utiliser des déclencheurs pour appliquer des modifications basées sur la valeur de propriété de chaque objet de données. Toutefois, si les déclencheurs vous permettent d’appliquer des valeurs de propriété ou de lancer des animations, ils ne vous donnent pas la possibilité de reconstruire la structure de vos objets de données. Certains scénarios peuvent vous obliger <xref:System.Windows.DataTemplate> à créer un autre pour les objets de données qui sont du même type, mais ont des propriétés différentes.

 Par exemple, lorsque un objet `Task` a une valeur `Priority` égale à `1`, vous avez la possibilité de lui donner un aspect différent qui vous servira d’alerte. Dans ce cas, <xref:System.Windows.DataTemplate> vous créez un pour `Task` l’affichage des objets hautement prioritaires. Ajoutons ce qui <xref:System.Windows.DataTemplate> suit à la section ressources :

 [!code-xaml[DataTemplatingIntro_snip#ImportantTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#importanttemplate)]

Cet exemple utilise la propriété [DataTemplate.Resources.](xref:System.Windows.FrameworkTemplate.Resources%2A) Les ressources définies dans cette section <xref:System.Windows.DataTemplate>sont partagées par les éléments du .

 Fournir la logique <xref:System.Windows.DataTemplate> pour choisir lequel `Priority` utiliser en fonction de la <xref:System.Windows.Controls.DataTemplateSelector> valeur de <xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A> l’objet de données, créer une sous-classe et passer outre la méthode. Dans l’exemple <xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A> suivant, la méthode fournit la logique de `Priority` retourner le modèle approprié basé sur la valeur de la propriété. Le modèle de retour se trouve dans les <xref:System.Windows.Window> ressources de l’élément enveloppant.

 [!code-csharp[DataTemplatingIntro_snip#DTSClass](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/TaskListDataTemplateSelector.cs#dtsclass)]
 [!code-vb[DataTemplatingIntro_snip#DTSClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataTemplatingIntro_snip/visualbasic/tasklistdatatemplateselector.vb#dtsclass)]

 On peut ensuite déclarer le `TaskListDataTemplateSelector` comme ressource :

 [!code-xaml[DataTemplatingIntro_snip#R1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r1)]
[!code-xaml[DataTemplatingIntro_snip#DTS](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#dts)]
[!code-xaml[DataTemplatingIntro_snip#R2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r2)]

 Pour utiliser la ressource de sélecteur de modèle, l’attribuer à la <xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A> propriété de la <xref:System.Windows.Controls.ListBox>. <xref:System.Windows.Controls.ListBox> L’appel <xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A> de `TaskListDataTemplateSelector` la méthode de la pour chacun des éléments de la collection sous-jacente. L’appel passe l’objet de données en paramètre d’élément. Le <xref:System.Windows.DataTemplate> qui est retourné par la méthode est ensuite appliqué à cet objet de données.

 [!code-xaml[DataTemplatingIntro_snip#ItemTemplateSelector](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#itemtemplateselector)]

 Avec le sélecteur <xref:System.Windows.Controls.ListBox> de modèle en place, le ressort maintenant comme suit :

 ![Capture d’écran de l’échantillon de templating de données](./media/datatemplatingintro-fig7.png "DataTemplatingIntro_fig7")

Ainsi se conclut notre étude de cet exemple. Vous trouverez l’exemple complet sur la page [Présentation d’un exemple de création de modèles de données](https://github.com/Microsoft/WPF-Samples/tree/master/Data%20Binding/DataTemplatingIntro).

<a name="DataTemplating_ItemsControl"></a>
## <a name="styling-and-templating-an-itemscontrol"></a>Création de styles et de modèles pour un ItemsControl
 Même si <xref:System.Windows.Controls.ItemsControl> le n’est pas le <xref:System.Windows.DataTemplate> seul type de contrôle que vous <xref:System.Windows.Controls.ItemsControl> pouvez utiliser un avec, il est un scénario très commun pour lier une collection. Dans la [section What Belongs in a DataTemplate,](#what_belongs_in_datatemplate) nous avons discuté du fait que la définition de votre <xref:System.Windows.DataTemplate> site ne devrait porter que sur la présentation des données. Afin de savoir quand il n’est pas approprié d’utiliser un, <xref:System.Windows.DataTemplate> il <xref:System.Windows.Controls.ItemsControl>est important de comprendre le style différent et les propriétés de modèle fournies par le . L’exemple suivant est conçu pour illustrer la fonction de chacune de ces propriétés. L’exemple <xref:System.Windows.Controls.ItemsControl> est lié à `Tasks` la même collection que dans l’exemple précédent. À des fins de démonstration, les styles et les modèles de cet exemple sont tous déclarés inline.

 [!code-xaml[DataTemplatingIntro_snip#ItemsControlProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#itemscontrolproperties)]

 Voici une capture d’écran du rendu de l’exemple :

 ![Capture d’écran : exemple de ItemsControl](./media/databinding-itemscontrolproperties.png "DataBinding_ItemsControlProperties")

 Notez qu’au <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>lieu d’utiliser le , vous pouvez utiliser le <xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A>. Vous trouverez un exemple dans la section précédente. De même, au <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>lieu d’utiliser le <xref:System.Windows.Controls.ItemsControl.ItemContainerStyleSelector%2A>, vous avez la possibilité d’utiliser le .

 Deux autres propriétés liées <xref:System.Windows.Controls.ItemsControl> au style de <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> <xref:System.Windows.Controls.ItemsControl.GroupStyleSelector%2A>ce qui ne sont pas montrés ici sont et .

<a name="DataTemplating_HeirarchicalDataTemplate"></a>
## <a name="support-for-hierarchical-data"></a>Prise en charge des données hiérarchiques
 Jusqu’à présent, nous avons seulement vu comment lier et afficher une collection unique. Une collection peut contenir d’autres collections. La <xref:System.Windows.HierarchicalDataTemplate> classe est conçue <xref:System.Windows.Controls.HeaderedItemsControl> pour être utilisée avec des types pour afficher de telles données. Dans l’exemple suivant, `ListLeagueList` est une liste d’objets `League`. Chaque objet `League` a un `Name` et une collection d’objets `Division`. Chaque `Division` a un `Name` et une collection d’objets `Team` et chaque objet `Team` a un `Name`.

 [!code-xaml[HierarchicalDataTemplateSnippet#HDT](~/samples/snippets/csharp/VS_Snippets_Wpf/HierarchicalDataTemplateSnippet/CS/window1.xaml#hdt)]

 L’exemple montre qu’avec l’utilisation de , vous pouvez facilement afficher des <xref:System.Windows.HierarchicalDataTemplate>données de liste qui contient d’autres listes. Voici une capture d’écran de l’exemple.

 ![HiérarchicalDataTemplate capture d’écran de l’échantillon](./media/databinding-hierarchicaldatatemplate.png "DataBinding_HierarchicalDataTemplate")

## <a name="see-also"></a>Voir aussi

- [Liaison de données](../advanced/optimizing-performance-data-binding.md)
- [Trouver des éléments générés par DataTemplate](how-to-find-datatemplate-generated-elements.md)
- [Application d’un style et création de modèles](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Aperçu de la liaison de données](../../../desktop-wpf/data/data-binding-overview.md)
- [Vue d’ensemble des modèles et styles d’en-tête de colonne GridView](../controls/gridview-column-header-styles-and-templates-overview.md)
