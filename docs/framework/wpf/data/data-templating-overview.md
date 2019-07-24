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
ms.openlocfilehash: 556ce7b42f13d7c5ba7fba36b09277cda9bcae5d
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68400661"
---
# <a name="data-templating-overview"></a>Vue d'ensemble des modèles de données
Le modèle de création de modèles de données WPF offre une grande souplesse pour définir la présentation des données. Les contrôles WPF possèdent des fonctionnalités intégrées permettant de prendre en charge la personnalisation de la présentation des données. Cette rubrique explique d’abord comment définir un <xref:System.Windows.DataTemplate> , puis introduit d’autres fonctionnalités de création de modèles de données, telles que la sélection de modèles en fonction de la logique personnalisée et la prise en charge de l’affichage des données hiérarchiques.  
  
<a name="Prerequisites"></a>   
## <a name="prerequisites"></a>Prérequis  
 Cette rubrique porte sur les fonctionnalités de création de modèles de données ; elle ne constitue pas une introduction aux concepts de liaison de données. Pour plus d’informations sur les concepts de base de la liaison de données, consultez la [Vue d’ensemble de la liaison de données](data-binding-overview.md).  
  
 <xref:System.Windows.DataTemplate>concerne la présentation des données et est l’une des nombreuses fonctionnalités fournies par le modèle de création de styles et de modèles WPF. Pour une introduction au modèle de création de styles et de modèles WPF, comme l’utilisation d' <xref:System.Windows.Style> un pour définir des propriétés sur les contrôles, consultez la rubrique [style et création de modèles](../controls/styling-and-templating.md) .  
  
 En outre, il est important de comprendre `Resources`, ce qui est essentiellement ce qui permet de <xref:System.Windows.Style> réutiliser des objets tels que et <xref:System.Windows.DataTemplate> . Pour plus d’informations sur les ressources, consultez la page [Ressources XAML](../advanced/xaml-resources.md).  
  
<a name="DataTemplating_Basic"></a>   
## <a name="data-templating-basics"></a>Informations de base sur la création de modèles de données  
  
 Pour illustrer <xref:System.Windows.DataTemplate> la raison pour laquelle est important, examinons un exemple de liaison de données. Dans cet exemple, nous avons un <xref:System.Windows.Controls.ListBox> qui est lié à une liste d' `Task` objets. Chaque objet `Task` a un `TaskName` (chaîne), une `Description` (chaîne), une `Priority` (entier) et une propriété de type `TaskType`, qui est un `Enum` avec des valeurs `Home` et `Work`.  
  
 [!code-xaml[DataTemplatingIntro_snip#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#resources)]  
[!code-xaml[DataTemplatingIntro_snip#UI1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#ui1)]  
[!code-xaml[DataTemplatingIntro_snip#UI2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#ui2)]  
  
<a name="without_a_datatemplate"></a>   
### <a name="without-a-datatemplate"></a>Sans DataTemplate  
 Sans a <xref:System.Windows.DataTemplate>, notre <xref:System.Windows.Controls.ListBox> ressemble actuellement à ce qui suit:  
  
 ![Capture d’écran exemple de création de modèles de données](./media/datatemplatingintro-fig1.png "DataTemplatingIntro_fig1")  
  
 Ce qui se passe est que, sans instructions spécifiques, <xref:System.Windows.Controls.ListBox> le appelle `ToString` par défaut lors de la tentative d’affichage des objets dans la collection. Par conséquent, si `Task` l’objet substitue la `ToString` méthode, le <xref:System.Windows.Controls.ListBox> affiche la représentation sous forme de chaîne de chaque objet source de la collection sous-jacente.  
  
 Par exemple, si la classe `Task` remplace la méthode `ToString` de cette façon, où `name` correspond au champ de la propriété `TaskName` :  
  
 [!code-csharp[DataTemplatingIntro_snip#ToString](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Data.cs#tostring)]
 [!code-vb[DataTemplatingIntro_snip#ToString](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataTemplatingIntro_snip/visualbasic/data.vb#tostring)]  
  
 L' <xref:System.Windows.Controls.ListBox> exemple ressemble à ce qui suit:  
  
 ![Capture d’écran exemple de création de modèles de données](./media/datatemplatingintro-fig2.png "DataTemplatingIntro_fig2")  
  
 Toutefois, cet affichage est restrictif et rigide. En outre, si la liaison porte sur des données [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)], vous ne pourrez pas remplacer `ToString`.  
  
<a name="defining_simple_datatemplate"></a>   
### <a name="defining-a-simple-datatemplate"></a>Définir un DataTemplate simple  
 La solution consiste à définir un <xref:System.Windows.DataTemplate>. Pour ce faire, vous pouvez affecter la valeur <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> à la propriété <xref:System.Windows.Controls.ListBox> de <xref:System.Windows.DataTemplate>. Ce que vous spécifiez <xref:System.Windows.DataTemplate> dans votre devient la structure visuelle de votre objet de données. Les éléments <xref:System.Windows.DataTemplate> suivants sont assez simples. Nous offrons des instructions indiquant que chaque élément apparaît sous <xref:System.Windows.Controls.TextBlock> la forme de <xref:System.Windows.Controls.StackPanel>trois éléments dans un. Chaque <xref:System.Windows.Controls.TextBlock> élément est lié à une propriété de la `Task` classe.  
  
 [!code-xaml[DataTemplatingIntro_snip#Inline](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#inline)]  
  
 Les données sous-jacentes pour les exemples de cette rubrique sont une collection d’objets CLR. si la liaison porte sur des données [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)], les concepts de base sont identiques, mais il y a une légère différence syntaxique. Par exemple, au lieu d' `Path=TaskName`avoir, vous devez <xref:System.Windows.Data.Binding.XPath%2A> affecter `@TaskName` à la `TaskName` valeur (si est un [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] attribut de votre nœud).  
  
 À présent <xref:System.Windows.Controls.ListBox> , notre ressemble à ceci:  
  
 ![Capture d’écran exemple de création de modèles de données](./media/datatemplatingintro-fig3.png "DataTemplatingIntro_fig3")  
  
<a name="defining_datatemplate_as_a_resource"></a>   
### <a name="creating-the-datatemplate-as-a-resource"></a>Créer un DataTemplate comme ressource  
 Dans l’exemple ci-dessus, nous <xref:System.Windows.DataTemplate> avons défini l’Inline. Il est plus courant de le définir dans la section des ressources afin d’en faire un objet réutilisable, comme dans l’exemple suivant :  
  
 [!code-xaml[DataTemplatingIntro_snip#R1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r1)]  
[!code-xaml[DataTemplatingIntro_snip#AsResource](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#asresource)]  
[!code-xaml[DataTemplatingIntro_snip#R2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r2)]  
  
 Vous pouvez à présent utiliser `myTaskTemplate` comme ressource, comme dans l’exemple suivant :  
  
 [!code-xaml[DataTemplatingIntro_snip#MyTaskTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#mytasktemplate)]  
  
 Étant `myTaskTemplate` donné que est une ressource, vous pouvez maintenant l’utiliser sur d’autres contrôles qui ont une propriété <xref:System.Windows.DataTemplate> qui prend un type. Comme indiqué ci-dessus <xref:System.Windows.Controls.ItemsControl> , pour les objets, <xref:System.Windows.Controls.ListBox>tels que, il <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> s’agit de la propriété. Pour <xref:System.Windows.Controls.ContentControl> les objets, il s' <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> agit de la propriété.  
  
<a name="Styling_DataType"></a>   
### <a name="the-datatype-property"></a>La propriété DataType  
 La <xref:System.Windows.DataTemplate> classe a une <xref:System.Windows.DataTemplate.DataType%2A> propriété qui est très similaire à la <xref:System.Windows.Style.TargetType%2A> propriété de la <xref:System.Windows.Style> classe. Par conséquent, au lieu de `x:Key` spécifier un <xref:System.Windows.DataTemplate> pour le dans l’exemple ci-dessus, vous pouvez effectuer les opérations suivantes:  
  
 [!code-xaml[DataTemplatingIntro_snip#DataType](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#datatype)]  
  
 Cette <xref:System.Windows.DataTemplate> valeur est appliquée automatiquement à `Task` tous les objets. Notez que, dans ce cas, la `x:Key` est définie implicitement. Par conséquent, si vous affectez `x:Key` cette <xref:System.Windows.DataTemplate> valeur, vous substituez le implicite `x:Key` et <xref:System.Windows.DataTemplate> le n’est pas appliqué automatiquement.  
  
 Si vous liez <xref:System.Windows.Controls.ContentControl> un à une collection d' `Task` objets, le <xref:System.Windows.Controls.ContentControl> n’utilise pas automatiquement les éléments <xref:System.Windows.DataTemplate> ci-dessus. Cela est dû au fait que la <xref:System.Windows.Controls.ContentControl> liaison sur un nécessite davantage d’informations pour distinguer si vous souhaitez effectuer une liaison à une collection entière ou aux objets individuels. Si votre <xref:System.Windows.Controls.ContentControl> effectue le suivi de la sélection <xref:System.Windows.Controls.ItemsControl> d’un type, vous pouvez <xref:System.Windows.Data.Binding.Path%2A> définir la propriété <xref:System.Windows.Controls.ContentControl> de la liaison`/`sur «» pour indiquer que vous êtes intéressé par l’élément actuel. Vous trouverez un exemple sur la page [Effectuer une liaison à une collection et afficher des informations en fonction de la sélection](how-to-bind-to-a-collection-and-display-information-based-on-selection.md). Dans le cas contraire, vous devez <xref:System.Windows.DataTemplate> spécifier explicitement en définissant la <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> propriété.  
  
 La <xref:System.Windows.DataTemplate.DataType%2A> propriété est particulièrement utile lorsque vous avez un <xref:System.Windows.Data.CompositeCollection> des différents types d’objets de données. Vous trouverez un exemple sur la page [Implémenter une CompositeCollection](how-to-implement-a-compositecollection.md).  
  
<a name="adding_more_to_datatemplate"></a>   
## <a name="adding-more-to-the-datatemplate"></a>Ajouter d’autres informations au DataTemplate  
 Actuellement, les données s’affichent avec les informations nécessaires, mais on peut sans problème aller plus loin. Nous allons améliorer la présentation en ajoutant un <xref:System.Windows.Controls.Border>, un <xref:System.Windows.Controls.Grid>et certains <xref:System.Windows.Controls.TextBlock> éléments qui décrivent les données affichées.  
  
 [!code-xaml[DataTemplatingIntro#AddingMore](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore)]  
[!code-xaml[DataTemplatingIntro#AddingMore2](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore2)]  
  
 La capture d’écran suivante <xref:System.Windows.Controls.ListBox> montre le avec <xref:System.Windows.DataTemplate>ce modifié:  
  
 ![Capture d’écran exemple de création de modèles de données](./media/datatemplatingintro-fig4.png "DataTemplatingIntro_fig4")  
  
 Nous pouvons définir <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> <xref:System.Windows.HorizontalAlignment.Stretch> sur sur <xref:System.Windows.Controls.ListBox> pour s’assurer que la largeur des éléments occupe tout l’espace:  
  
 [!code-xaml[DataTemplatingIntro_snip#Stretch](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#stretch)]  
  
 La propriété <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> ayant la valeur <xref:System.Windows.HorizontalAlignment.Stretch>, <xref:System.Windows.Controls.ListBox> se présente désormais comme suit:  
  
 ![Capture d’écran exemple de création de modèles de données](./media/datatemplatingintro-fig5.png "DataTemplatingIntro_fig5")  
  
<a name="DataTrigger_to_Apply_Property_Values"></a>   
### <a name="use-datatriggers-to-apply-property-values"></a>Utiliser DataTrigger pour appliquer des valeurs de propriété  
 La présentation actuelle n’indique pas si une `Task` est une tâche privée ou une tâche professionnelle. N’oubliez pas que l’objet `Task` a une propriété `TaskType` de type `TaskType`, qui est une énumération avec les valeurs `Home` et `Work`.  
  
 Dans l’exemple suivant, le <xref:System.Windows.DataTrigger> définit le <xref:System.Windows.Controls.Border.BorderBrush%2A> de l’élément nommé `border` sur `Yellow` si la `TaskType` propriété a `TaskType.Home`la valeur.  
  
 [!code-xaml[DataTemplatingIntro#DT](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#dt)]  
[!code-xaml[DataTemplatingIntro#DataTrigger](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#datatrigger)]  
[!code-xaml[DataTemplatingIntro#AddingMore2](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore2)]  
  
 Notre application se présente maintenant ainsi. Les tâches privées apparaissent avec une bordure jaune et les tâches professionnelles avec une bordure cyan :  
  
 ![Capture d’écran exemple de création de modèles de données](./media/datatemplatingintro-fig6.png "DataTemplatingIntro_fig6")  
  
 Dans cet exemple <xref:System.Windows.DataTrigger> , utilise un <xref:System.Windows.Setter> pour définir une valeur de propriété. Les classes de déclencheur ont <xref:System.Windows.TriggerBase.EnterActions%2A> également <xref:System.Windows.TriggerBase.ExitActions%2A> les propriétés et qui vous permettent de démarrer un ensemble d’actions, telles que des animations. En outre, il existe également une <xref:System.Windows.MultiDataTrigger> classe qui vous permet d’appliquer des modifications en fonction de plusieurs valeurs de propriété liées aux données.  
  
 Une autre façon d’obtenir le même effet consiste à lier la <xref:System.Windows.Controls.Border.BorderBrush%2A> propriété à la `TaskType` propriété et à utiliser un convertisseur de valeur pour retourner la couleur en `TaskType` fonction de la valeur. Du point de vue des performances, il est légèrement plus efficace d’utiliser un convertisseur pour produire cet effet. En outre, le fait de créer votre propre convertisseur vous offre plus de souplesse, car vous fournissez votre propre logique. En somme, la technique choisie dépend du scénario et des préférences. Pour plus d’informations sur l’écriture d’un convertisseur <xref:System.Windows.Data.IValueConverter>, consultez.  
  
<a name="what_belongs_in_datatemplate"></a>   
### <a name="what-belongs-in-a-datatemplate"></a>Que contient un DataTemplate ?  

Dans l’exemple précédent, nous avons placé le déclencheur <xref:System.Windows.DataTemplate> dans le <xref:System.Windows.DataTemplate>à l’aide du.<xref:System.Windows.DataTemplate.Triggers%2A> . Le <xref:System.Windows.Setter> du déclencheur définit la valeur d’une propriété d’un élément (l' <xref:System.Windows.Controls.Border> élément) qui se trouve dans <xref:System.Windows.DataTemplate>le. Toutefois, `Setters` si les propriétés qui vous intéressent ne sont pas des propriétés des éléments qui se trouvent dans le actuel <xref:System.Windows.DataTemplate>, il peut être plus approprié de définir les propriétés à l’aide d' <xref:System.Windows.Controls.ListBoxItem> un <xref:System.Windows.Style> qui est pour la classe (si le contrôle que vous liez est <xref:System.Windows.Controls.ListBox>un). Par exemple, si vous souhaitez que <xref:System.Windows.Trigger> votre effectue l' <xref:System.Windows.UIElement.Opacity%2A> animation de la valeur de l’élément quand une souris pointe sur un élément, vous définissez des <xref:System.Windows.Controls.ListBoxItem> déclencheurs dans un style. Vous trouverez un exemple sur la page [Présentation d’un exemple de création de style et de modèle](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).
  
 En général, gardez à l’esprit que <xref:System.Windows.DataTemplate> le est appliqué à chacun des générés <xref:System.Windows.Controls.ListBoxItem> (pour plus d’informations sur la façon et l’endroit où il est réellement <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> appliqué, consultez la page.) Vous <xref:System.Windows.DataTemplate> vous intéressez uniquement à la présentation et à l’apparence des objets de données. Dans la plupart des cas, tous les autres aspects de la présentation, tels que l’apparence d’un élément quand il est <xref:System.Windows.Controls.ListBox> sélectionné ou la manière dont le dispose les éléments, n’appartiennent pas <xref:System.Windows.DataTemplate>à la définition d’un. Vous trouverez un exemple dans la section [Création de styles et de modèles pour un ItemsControl](#DataTemplating_ItemsControl).  
  
<a name="Styling_StyleSelection"></a>   
## <a name="choosing-a-datatemplate-based-on-properties-of-the-data-object"></a>Choisir un DataTemplate en fonction des propriétés de l’objet de données  
 Dans la section [La propriété DataType](#Styling_DataType), nous avons expliqué que vous pouvez définir différents modèles de données pour différents objets de données. Cela s’avère particulièrement utile lorsque vous avez <xref:System.Windows.Data.CompositeCollection> un de types différents ou des collections avec des éléments de types différents. Dans la section [utiliser DataTriggers pour appliquer des valeurs de propriété](#DataTrigger_to_Apply_Property_Values) , nous avons montré que si vous disposez d’une collection du même type d’objets de données, <xref:System.Windows.DataTemplate> vous pouvez créer un, puis utiliser des déclencheurs pour appliquer les modifications en fonction des valeurs de propriété de chaque objet de données. Toutefois, si les déclencheurs vous permettent d’appliquer des valeurs de propriété ou de lancer des animations, ils ne vous donnent pas la possibilité de reconstruire la structure de vos objets de données. Dans certains scénarios, vous devrez peut-être <xref:System.Windows.DataTemplate> créer un autre pour les objets de données du même type, mais avec des propriétés différentes.  
  
 Par exemple, lorsque un objet `Task` a une valeur `Priority` égale à `1`, vous avez la possibilité de lui donner un aspect différent qui vous servira d’alerte. Dans ce cas, vous créez un <xref:System.Windows.DataTemplate> pour l’affichage des objets de priorité `Task` haute. Nous allons ajouter ce qui <xref:System.Windows.DataTemplate> suit à la section des ressources:  
  
 [!code-xaml[DataTemplatingIntro_snip#ImportantTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#importanttemplate)]  
  
 Notez que <xref:System.Windows.DataTemplate>cet exemple utilise.<xref:System.Windows.FrameworkTemplate.Resources%2A> . Les ressources définies dans cette section sont partagées par les éléments <xref:System.Windows.DataTemplate>dans le.  
  
 Pour fournir une logique permettant de <xref:System.Windows.DataTemplate> choisir celle qui doit être `Priority` utilisée en fonction de la valeur de l’objet de données <xref:System.Windows.Controls.DataTemplateSelector> , créez une sous <xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A> -classe de et substituez la méthode. Dans l’exemple suivant, la <xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A> méthode fournit une logique pour retourner le modèle approprié en fonction de la valeur `Priority` de la propriété. Le modèle à retourner se trouve dans les ressources de l' <xref:System.Windows.Window> élément enveloppant.  
  
 [!code-csharp[DataTemplatingIntro_snip#DTSClass](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/TaskListDataTemplateSelector.cs#dtsclass)]
 [!code-vb[DataTemplatingIntro_snip#DTSClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataTemplatingIntro_snip/visualbasic/tasklistdatatemplateselector.vb#dtsclass)]  
  
 On peut ensuite déclarer le `TaskListDataTemplateSelector` comme ressource :  
  
 [!code-xaml[DataTemplatingIntro_snip#R1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r1)]  
[!code-xaml[DataTemplatingIntro_snip#DTS](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#dts)]  
[!code-xaml[DataTemplatingIntro_snip#R2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r2)]  
  
 Pour utiliser la ressource du sélecteur de modèle, assignez-la <xref:System.Windows.Controls.ListBox>à la <xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A> propriété de. Appelle la <xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A> méthode de`TaskListDataTemplateSelector` pour chacun des éléments de la collection sous-jacente. <xref:System.Windows.Controls.ListBox> L’appel passe l’objet de données en paramètre d’élément. Le <xref:System.Windows.DataTemplate> retourné par la méthode est ensuite appliqué à cet objet de données.  
  
 [!code-xaml[DataTemplatingIntro_snip#ItemTemplateSelector](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#itemtemplateselector)]  
  
 Une fois le sélecteur de modèle en place <xref:System.Windows.Controls.ListBox> , le s’affiche désormais comme suit:  
  
 ![Capture d’écran exemple de création de modèles de données](./media/datatemplatingintro-fig7.png "DataTemplatingIntro_fig7")  

Ainsi se conclut notre étude de cet exemple. Vous trouverez l’exemple complet sur la page [Présentation d’un exemple de création de modèles de données](https://github.com/Microsoft/WPF-Samples/tree/master/Data%20Binding/DataTemplatingIntro).

<a name="DataTemplating_ItemsControl"></a>   
## <a name="styling-and-templating-an-itemscontrol"></a>Création de styles et de modèles pour un ItemsControl  
 Même si <xref:System.Windows.Controls.ItemsControl> n’est pas le seul type de contrôle avec lequel vous pouvez <xref:System.Windows.DataTemplate> utiliser un avec, il s’agit d’un scénario très <xref:System.Windows.Controls.ItemsControl> courant pour lier un à une collection. Dans la section qu’est- [ce qui appartient à un DataTemplate](#what_belongs_in_datatemplate) , nous avons <xref:System.Windows.DataTemplate> parlé que la définition de votre doit uniquement se préoccuper de la présentation des données. Pour savoir quand il n’est pas approprié d’utiliser un <xref:System.Windows.DataTemplate> , il est important de comprendre les différentes propriétés de style et de modèle fournies par le. <xref:System.Windows.Controls.ItemsControl> L’exemple suivant est conçu pour illustrer la fonction de chacune de ces propriétés. Dans cet exemple, est lié à la même `Tasks` collection que dans l’exemple précédent. <xref:System.Windows.Controls.ItemsControl> À des fins de démonstration, les styles et les modèles de cet exemple sont tous déclarés inline.  
  
 [!code-xaml[DataTemplatingIntro_snip#ItemsControlProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#itemscontrolproperties)]  
  
 Voici une capture d’écran du rendu de l’exemple :  
  
 ![Capture d’écran de l’exemple ItemsControl](./media/databinding-itemscontrolproperties.png "DataBinding_ItemsControlProperties")  
  
 Notez qu’au lieu d' <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>utiliser, vous pouvez utiliser le. <xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A> Vous trouverez un exemple dans la section précédente. De même, au lieu d’utiliser <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>le, vous avez la possibilité d' <xref:System.Windows.Controls.ItemsControl.ItemContainerStyleSelector%2A>utiliser.  
  
 Les deux autres propriétés liées au <xref:System.Windows.Controls.ItemsControl> style de qui ne sont pas indiquées ici sont <xref:System.Windows.Controls.ItemsControl.GroupStyleSelector%2A> <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> et.  
  
<a name="DataTemplating_HeirarchicalDataTemplate"></a>   
## <a name="support-for-hierarchical-data"></a>Prise en charge des données hiérarchiques  
 Jusqu’à présent, nous avons seulement vu comment lier et afficher une collection unique. Une collection peut contenir d’autres collections. La <xref:System.Windows.HierarchicalDataTemplate> classe est conçue pour être utilisée avec <xref:System.Windows.Controls.HeaderedItemsControl> des types pour afficher ces données. Dans l’exemple suivant, `ListLeagueList` est une liste d’objets `League`. Chaque objet `League` a un `Name` et une collection d’objets `Division`. Chaque `Division` a un `Name` et une collection d’objets `Team` et chaque objet `Team` a un `Name`.  
  
 [!code-xaml[HierarchicalDataTemplateSnippet#HDT](~/samples/snippets/csharp/VS_Snippets_Wpf/HierarchicalDataTemplateSnippet/CS/window1.xaml#hdt)]  
  
 L’exemple montre qu’avec l’utilisation de <xref:System.Windows.HierarchicalDataTemplate>, vous pouvez facilement afficher des données de liste qui contiennent d’autres listes. Voici une capture d’écran de l’exemple.  
  
 ![Capture d’écran exemple HierarchicalDataTemplate](./media/databinding-hierarchicaldatatemplate.png "DataBinding_HierarchicalDataTemplate")  
  
## <a name="see-also"></a>Voir aussi

- [Liaison de données](../advanced/optimizing-performance-data-binding.md)
- [Rechercher des éléments générés par DataTemplate](how-to-find-datatemplate-generated-elements.md)
- [Application d’un style et création de modèles](../controls/styling-and-templating.md)
- [Vue d’ensemble de la liaison de données](data-binding-overview.md)
- [Vue d’ensemble des modèles et styles d’en-tête de colonne GridView](../controls/gridview-column-header-styles-and-templates-overview.md)
