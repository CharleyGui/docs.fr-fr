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
ms.openlocfilehash: d088342a08076c69b34f6c3d39dce076cb3890d4
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460046"
---
# <a name="data-templating-overview"></a>Vue d'ensemble des modèles de données
Le modèle de création de modèles de données WPF offre une grande souplesse pour définir la présentation des données. Les contrôles WPF possèdent des fonctionnalités intégrées permettant de prendre en charge la personnalisation de la présentation des données. Cette rubrique explique d’abord comment définir une <xref:System.Windows.DataTemplate>, puis introduit d’autres fonctionnalités de création de modèles de données, telles que la sélection de modèles en fonction de la logique personnalisée et la prise en charge de l’affichage des données hiérarchiques.  
  
<a name="Prerequisites"></a>   
## <a name="prerequisites"></a>Configuration requise  
 Cette rubrique porte sur les fonctionnalités de création de modèles de données ; elle ne constitue pas une introduction aux concepts de liaison de données. Pour plus d’informations sur les concepts de base de la liaison de données, consultez la [Vue d’ensemble de la liaison de données](../../../desktop-wpf/data/data-binding-overview.md).  
  
 <xref:System.Windows.DataTemplate> concerne la présentation des données et est l’une des nombreuses fonctionnalités fournies par le modèle de création de styles et de modèles WPF. Pour obtenir une présentation du modèle de création de styles et de modèles WPF, comme l’utilisation d’un <xref:System.Windows.Style> pour définir des propriétés sur les contrôles, consultez la rubrique [style et création de modèles](../controls/styling-and-templating.md) .  
  
 En outre, il est important de comprendre `Resources`, qui sont essentiellement ce qui permet de réutiliser des objets tels que des <xref:System.Windows.Style> et des <xref:System.Windows.DataTemplate>. Pour plus d’informations sur les ressources, consultez la page [Ressources XAML](../advanced/xaml-resources.md).  
  
<a name="DataTemplating_Basic"></a>   
## <a name="data-templating-basics"></a>Informations de base sur la création de modèles de données  
  
 Pour illustrer la raison pour laquelle <xref:System.Windows.DataTemplate> est important, passons en revue un exemple de liaison de données. Dans cet exemple, nous avons un <xref:System.Windows.Controls.ListBox> qui est lié à une liste d’objets `Task`. Chaque objet `Task` a un `TaskName` (chaîne), une `Description` (chaîne), une `Priority` (entier) et une propriété de type `TaskType`, qui est un `Enum` avec des valeurs `Home` et `Work`.  
  
 [!code-xaml[DataTemplatingIntro_snip#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#resources)]  
[!code-xaml[DataTemplatingIntro_snip#UI1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#ui1)]  
[!code-xaml[DataTemplatingIntro_snip#UI2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#ui2)]  
  
<a name="without_a_datatemplate"></a>   
### <a name="without-a-datatemplate"></a>Sans DataTemplate  
 Sans <xref:System.Windows.DataTemplate>, notre <xref:System.Windows.Controls.ListBox> se présente actuellement comme suit :  
  
 ![Capture d’écran exemple de création de modèles de données](./media/datatemplatingintro-fig1.png "DataTemplatingIntro_fig1")  
  
 Ce qui se passe est que sans instructions spécifiques, le <xref:System.Windows.Controls.ListBox> appelle par défaut `ToString` lors d’une tentative d’affichage des objets dans la collection. Par conséquent, si l’objet `Task` substitue la méthode `ToString`, le <xref:System.Windows.Controls.ListBox> affiche la représentation sous forme de chaîne de chaque objet source de la collection sous-jacente.  
  
 Par exemple, si la classe `Task` remplace la méthode `ToString` de cette façon, où `name` correspond au champ de la propriété `TaskName` :  
  
 [!code-csharp[DataTemplatingIntro_snip#ToString](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Data.cs#tostring)]
 [!code-vb[DataTemplatingIntro_snip#ToString](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataTemplatingIntro_snip/visualbasic/data.vb#tostring)]  
  
 Le <xref:System.Windows.Controls.ListBox> se présente comme suit :  
  
 ![Capture d’écran exemple de création de modèles de données](./media/datatemplatingintro-fig2.png "DataTemplatingIntro_fig2")  
  
 Toutefois, cet affichage est restrictif et rigide. En outre, si la liaison porte sur des données [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)], vous ne pourrez pas remplacer `ToString`.  
  
<a name="defining_simple_datatemplate"></a>   
### <a name="defining-a-simple-datatemplate"></a>Définir un DataTemplate simple  
 La solution consiste à définir un <xref:System.Windows.DataTemplate>. Pour ce faire, vous pouvez définir la propriété <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> du <xref:System.Windows.Controls.ListBox> sur un <xref:System.Windows.DataTemplate>. Ce que vous spécifiez dans votre <xref:System.Windows.DataTemplate> devient la structure visuelle de votre objet de données. La <xref:System.Windows.DataTemplate> suivante est relativement simple. Nous fournissons des instructions indiquant que chaque élément apparaît sous la forme de trois éléments <xref:System.Windows.Controls.TextBlock> au sein d’un <xref:System.Windows.Controls.StackPanel>. Chaque élément <xref:System.Windows.Controls.TextBlock> est lié à une propriété de la classe `Task`.  
  
 [!code-xaml[DataTemplatingIntro_snip#Inline](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#inline)]  
  
 Les données sous-jacentes pour les exemples de cette rubrique sont une collection d’objets CLR. si la liaison porte sur des données [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)], les concepts de base sont identiques, mais il y a une légère différence syntaxique. Par exemple, au lieu d’avoir `Path=TaskName`, vous devez définir <xref:System.Windows.Data.Binding.XPath%2A> sur `@TaskName` (si `TaskName` est un attribut de votre nœud [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]).  
  
 À présent, notre <xref:System.Windows.Controls.ListBox> se présente comme suit :  
  
 ![Capture d’écran exemple de création de modèles de données](./media/datatemplatingintro-fig3.png "DataTemplatingIntro_fig3")  
  
<a name="defining_datatemplate_as_a_resource"></a>   
### <a name="creating-the-datatemplate-as-a-resource"></a>Créer un DataTemplate comme ressource  
 Dans l’exemple ci-dessus, nous avons défini le <xref:System.Windows.DataTemplate> Inline. Il est plus courant de le définir dans la section des ressources afin d’en faire un objet réutilisable, comme dans l’exemple suivant :  
  
 [!code-xaml[DataTemplatingIntro_snip#R1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r1)]  
[!code-xaml[DataTemplatingIntro_snip#AsResource](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#asresource)]  
[!code-xaml[DataTemplatingIntro_snip#R2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r2)]  
  
 Vous pouvez à présent utiliser `myTaskTemplate` comme ressource, comme dans l’exemple suivant :  
  
 [!code-xaml[DataTemplatingIntro_snip#MyTaskTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#mytasktemplate)]  
  
 Étant donné que `myTaskTemplate` est une ressource, vous pouvez maintenant l’utiliser sur d’autres contrôles qui ont une propriété qui prend un type <xref:System.Windows.DataTemplate>. Comme indiqué ci-dessus, pour les objets <xref:System.Windows.Controls.ItemsControl>, tels que le <xref:System.Windows.Controls.ListBox>, il s’agit de la propriété <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>. Pour les objets <xref:System.Windows.Controls.ContentControl>, il s’agit de la propriété <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A>.  
  
<a name="Styling_DataType"></a>   
### <a name="the-datatype-property"></a>La propriété DataType  
 La classe <xref:System.Windows.DataTemplate> a une propriété <xref:System.Windows.DataTemplate.DataType%2A> qui est très similaire à la propriété <xref:System.Windows.Style.TargetType%2A> de la classe <xref:System.Windows.Style>. Par conséquent, au lieu de spécifier un `x:Key` pour le <xref:System.Windows.DataTemplate> dans l’exemple ci-dessus, vous pouvez effectuer les opérations suivantes :  
  
 [!code-xaml[DataTemplatingIntro_snip#DataType](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#datatype)]  
  
 Cette <xref:System.Windows.DataTemplate> est appliquée automatiquement à tous les objets `Task`. Notez que, dans ce cas, la `x:Key` est définie implicitement. Par conséquent, si vous assignez cette <xref:System.Windows.DataTemplate> une valeur `x:Key`, vous substituez le `x:Key` implicite et le <xref:System.Windows.DataTemplate> n’est pas appliqué automatiquement.  
  
 Si vous liez une <xref:System.Windows.Controls.ContentControl> à une collection d’objets `Task`, le <xref:System.Windows.Controls.ContentControl> n’utilise pas automatiquement les <xref:System.Windows.DataTemplate> ci-dessus. Cela est dû au fait que la liaison sur un <xref:System.Windows.Controls.ContentControl> a besoin d’informations supplémentaires pour distinguer si vous souhaitez effectuer une liaison à une collection entière ou aux objets individuels. Si votre <xref:System.Windows.Controls.ContentControl> effectue le suivi de la sélection d’un type de <xref:System.Windows.Controls.ItemsControl>, vous pouvez définir la propriété <xref:System.Windows.Data.Binding.Path%2A> de la liaison <xref:System.Windows.Controls.ContentControl> sur «`/`» pour indiquer que vous êtes intéressé par l’élément actuel. Vous trouverez un exemple sur la page [Effectuer une liaison à une collection et afficher des informations en fonction de la sélection](how-to-bind-to-a-collection-and-display-information-based-on-selection.md). Dans le cas contraire, vous devez spécifier le <xref:System.Windows.DataTemplate> explicitement en définissant la propriété <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A>.  
  
 La propriété <xref:System.Windows.DataTemplate.DataType%2A> est particulièrement utile lorsque vous avez une <xref:System.Windows.Data.CompositeCollection> de différents types d’objets de données. Vous trouverez un exemple sur la page [Implémenter une CompositeCollection](how-to-implement-a-compositecollection.md).  
  
<a name="adding_more_to_datatemplate"></a>   
## <a name="adding-more-to-the-datatemplate"></a>Ajouter d’autres informations au DataTemplate  
 Actuellement, les données s’affichent avec les informations nécessaires, mais on peut sans problème aller plus loin. Nous allons améliorer la présentation en ajoutant un <xref:System.Windows.Controls.Border>, un <xref:System.Windows.Controls.Grid>et certains éléments <xref:System.Windows.Controls.TextBlock> qui décrivent les données affichées.  
  
 [!code-xaml[DataTemplatingIntro#AddingMore](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore)]  
[!code-xaml[DataTemplatingIntro#AddingMore2](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore2)]  
  
 La capture d’écran suivante montre les <xref:System.Windows.Controls.ListBox> avec cette <xref:System.Windows.DataTemplate>modifiée :  
  
 ![Capture d’écran exemple de création de modèles de données](./media/datatemplatingintro-fig4.png "DataTemplatingIntro_fig4")  
  
 Nous pouvons définir <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> sur <xref:System.Windows.HorizontalAlignment.Stretch> sur le <xref:System.Windows.Controls.ListBox> pour vous assurer que la largeur des éléments occupe tout l’espace :  
  
 [!code-xaml[DataTemplatingIntro_snip#Stretch](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#stretch)]  
  
 Avec la propriété <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> définie sur <xref:System.Windows.HorizontalAlignment.Stretch>, le <xref:System.Windows.Controls.ListBox> se présente comme suit :  
  
 ![Capture d’écran exemple de création de modèles de données](./media/datatemplatingintro-fig5.png "DataTemplatingIntro_fig5")  
  
<a name="DataTrigger_to_Apply_Property_Values"></a>   
### <a name="use-datatriggers-to-apply-property-values"></a>Utiliser DataTrigger pour appliquer des valeurs de propriété  
 La présentation actuelle n’indique pas si une `Task` est une tâche privée ou une tâche professionnelle. N’oubliez pas que l’objet `Task` a une propriété `TaskType` de type `TaskType`, qui est une énumération avec les valeurs `Home` et `Work`.  
  
 Dans l’exemple suivant, le <xref:System.Windows.DataTrigger> définit le <xref:System.Windows.Controls.Border.BorderBrush%2A> de l’élément nommé `border` sur `Yellow` si la propriété `TaskType` est `TaskType.Home`.  
  
 [!code-xaml[DataTemplatingIntro#DT](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#dt)]  
[!code-xaml[DataTemplatingIntro#DataTrigger](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#datatrigger)]  
[!code-xaml[DataTemplatingIntro#AddingMore2](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore2)]  
  
 Notre application se présente maintenant ainsi. Les tâches privées apparaissent avec une bordure jaune et les tâches professionnelles avec une bordure cyan :  
  
 ![Capture d’écran exemple de création de modèles de données](./media/datatemplatingintro-fig6.png "DataTemplatingIntro_fig6")  
  
 Dans cet exemple, le <xref:System.Windows.DataTrigger> utilise une <xref:System.Windows.Setter> pour définir une valeur de propriété. Les classes de déclencheur possèdent également les propriétés <xref:System.Windows.TriggerBase.EnterActions%2A> et <xref:System.Windows.TriggerBase.ExitActions%2A> qui vous permettent de démarrer un ensemble d’actions, telles que des animations. En outre, il existe également une classe <xref:System.Windows.MultiDataTrigger> qui vous permet d’appliquer des modifications en fonction de plusieurs valeurs de propriété liées aux données.  
  
 Une autre façon d’obtenir le même effet consiste à lier la propriété <xref:System.Windows.Controls.Border.BorderBrush%2A> à la propriété `TaskType` et à utiliser un convertisseur de valeur pour retourner la couleur en fonction de la valeur de `TaskType`. Du point de vue des performances, il est légèrement plus efficace d’utiliser un convertisseur pour produire cet effet. En outre, le fait de créer votre propre convertisseur vous offre plus de souplesse, car vous fournissez votre propre logique. En somme, la technique choisie dépend du scénario et des préférences. Pour plus d’informations sur l’écriture d’un convertisseur, consultez <xref:System.Windows.Data.IValueConverter>.  
  
<a name="what_belongs_in_datatemplate"></a>   
### <a name="what-belongs-in-a-datatemplate"></a>Que contient un DataTemplate ?  

Dans l’exemple précédent, nous avons placé le déclencheur dans le <xref:System.Windows.DataTemplate> à l’aide de l' <xref:System.Windows.DataTemplate>.<xref:System.Windows.DataTemplate.Triggers%2A> . La <xref:System.Windows.Setter> du déclencheur définit la valeur d’une propriété d’un élément (l’élément <xref:System.Windows.Controls.Border>) qui se trouve dans le <xref:System.Windows.DataTemplate>. Toutefois, si les propriétés auxquelles votre `Setters` vous intéressent ne sont pas des propriétés des éléments qui se trouvent dans le <xref:System.Windows.DataTemplate>actuel, il peut être plus approprié de définir les propriétés à l’aide d’un <xref:System.Windows.Style> qui est pour la classe <xref:System.Windows.Controls.ListBoxItem> (si le contrôle que vous liez est un <xref:System.Windows.Controls.ListBox>). Par exemple, si vous souhaitez que votre <xref:System.Windows.Trigger> animer la valeur <xref:System.Windows.UIElement.Opacity%2A> de l’élément quand une souris pointe sur un élément, vous définissez des déclencheurs dans un style de <xref:System.Windows.Controls.ListBoxItem>. Vous trouverez un exemple sur la page [Présentation d’un exemple de création de style et de modèle](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).
  
 En général, gardez à l’esprit que le <xref:System.Windows.DataTemplate> est appliqué à chacune des <xref:System.Windows.Controls.ListBoxItem> générées (pour plus d’informations sur la façon et l’endroit où il est réellement appliqué, consultez la page <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>.). Votre <xref:System.Windows.DataTemplate> concerne uniquement la présentation et l’apparence des objets de données. Dans la plupart des cas, tous les autres aspects de la présentation, tels que l’apparence d’un élément quand il est sélectionné ou la manière dont le <xref:System.Windows.Controls.ListBox> présente les éléments, n’appartiennent pas à la définition d’une <xref:System.Windows.DataTemplate>. Vous trouverez un exemple dans la section [Création de styles et de modèles pour un ItemsControl](#DataTemplating_ItemsControl).  
  
<a name="Styling_StyleSelection"></a>   
## <a name="choosing-a-datatemplate-based-on-properties-of-the-data-object"></a>Choisir un DataTemplate en fonction des propriétés de l’objet de données  
 Dans la section [La propriété DataType](#Styling_DataType), nous avons expliqué que vous pouvez définir différents modèles de données pour différents objets de données. Cela s’avère particulièrement utile lorsque vous disposez d’un <xref:System.Windows.Data.CompositeCollection> de types ou de collections différents avec des éléments de types différents. Dans la section [utiliser DataTriggers pour appliquer des valeurs de propriété](#DataTrigger_to_Apply_Property_Values) , nous avons démontré que si vous disposez d’une collection du même type d’objets de données, vous pouvez créer un <xref:System.Windows.DataTemplate> puis utiliser des déclencheurs pour appliquer les modifications en fonction des valeurs de propriété de chaque objet de données. Toutefois, si les déclencheurs vous permettent d’appliquer des valeurs de propriété ou de lancer des animations, ils ne vous donnent pas la possibilité de reconstruire la structure de vos objets de données. Dans certains scénarios, vous devrez peut-être créer une <xref:System.Windows.DataTemplate> différente pour les objets de données du même type, mais avec des propriétés différentes.  
  
 Par exemple, lorsque un objet `Task` a une valeur `Priority` égale à `1`, vous avez la possibilité de lui donner un aspect différent qui vous servira d’alerte. Dans ce cas, vous créez une <xref:System.Windows.DataTemplate> pour l’affichage des objets de `Task` à priorité élevée. Nous allons ajouter les <xref:System.Windows.DataTemplate> suivantes à la section des ressources :  
  
 [!code-xaml[DataTemplatingIntro_snip#ImportantTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#importanttemplate)]  
  
 Notez que cet exemple utilise la <xref:System.Windows.DataTemplate>.<xref:System.Windows.FrameworkTemplate.Resources%2A> . Les ressources définies dans cette section sont partagées par les éléments de l' <xref:System.Windows.DataTemplate>.  
  
 Pour fournir une logique permettant de choisir les <xref:System.Windows.DataTemplate> à utiliser en fonction de la valeur `Priority` de l’objet de données, créez une sous-classe de <xref:System.Windows.Controls.DataTemplateSelector> et substituez la méthode <xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A>. Dans l’exemple suivant, la méthode <xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A> fournit une logique pour retourner le modèle approprié en fonction de la valeur de la propriété `Priority`. Le modèle à retourner se trouve dans les ressources de l’élément de <xref:System.Windows.Window> enveloppant.  
  
 [!code-csharp[DataTemplatingIntro_snip#DTSClass](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/TaskListDataTemplateSelector.cs#dtsclass)]
 [!code-vb[DataTemplatingIntro_snip#DTSClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataTemplatingIntro_snip/visualbasic/tasklistdatatemplateselector.vb#dtsclass)]  
  
 On peut ensuite déclarer le `TaskListDataTemplateSelector` comme ressource :  
  
 [!code-xaml[DataTemplatingIntro_snip#R1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r1)]  
[!code-xaml[DataTemplatingIntro_snip#DTS](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#dts)]  
[!code-xaml[DataTemplatingIntro_snip#R2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r2)]  
  
 Pour utiliser la ressource du sélecteur de modèle, affectez-la à la propriété <xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A> du <xref:System.Windows.Controls.ListBox>. Le <xref:System.Windows.Controls.ListBox> appelle la méthode <xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A> de l' `TaskListDataTemplateSelector` pour chacun des éléments de la collection sous-jacente. L’appel passe l’objet de données en paramètre d’élément. Le <xref:System.Windows.DataTemplate> retourné par la méthode est ensuite appliqué à cet objet de données.  
  
 [!code-xaml[DataTemplatingIntro_snip#ItemTemplateSelector](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#itemtemplateselector)]  
  
 Une fois le sélecteur de modèle en place, le <xref:System.Windows.Controls.ListBox> se présente désormais comme suit :  
  
 ![Capture d’écran exemple de création de modèles de données](./media/datatemplatingintro-fig7.png "DataTemplatingIntro_fig7")  

Ainsi se conclut notre étude de cet exemple. Vous trouverez l’exemple complet sur la page [Présentation d’un exemple de création de modèles de données](https://github.com/Microsoft/WPF-Samples/tree/master/Data%20Binding/DataTemplatingIntro).

<a name="DataTemplating_ItemsControl"></a>   
## <a name="styling-and-templating-an-itemscontrol"></a>Création de styles et de modèles pour un ItemsControl  
 Même si l' <xref:System.Windows.Controls.ItemsControl> n’est pas le seul type de contrôle avec lequel vous pouvez utiliser une <xref:System.Windows.DataTemplate>, il s’agit d’un scénario très courant pour lier un <xref:System.Windows.Controls.ItemsControl> à une collection. Dans la section qu’est- [ce qui appartient à un DataTemplate](#what_belongs_in_datatemplate) , nous avons parlé que la définition de votre <xref:System.Windows.DataTemplate> ne doit concerner que la présentation des données. Pour savoir quand il n’est pas judicieux d’utiliser un <xref:System.Windows.DataTemplate> il est important de comprendre les différentes propriétés de style et de modèle fournies par le <xref:System.Windows.Controls.ItemsControl>. L’exemple suivant est conçu pour illustrer la fonction de chacune de ces propriétés. Le <xref:System.Windows.Controls.ItemsControl> dans cet exemple est lié au même regroupement `Tasks` que dans l’exemple précédent. À des fins de démonstration, les styles et les modèles de cet exemple sont tous déclarés inline.  
  
 [!code-xaml[DataTemplatingIntro_snip#ItemsControlProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#itemscontrolproperties)]  
  
 Voici une capture d’écran du rendu de l’exemple :  
  
 ![Capture d’écran d’exemple ItemsControl](./media/databinding-itemscontrolproperties.png "DataBinding_ItemsControlProperties")  
  
 Notez qu’au lieu d’utiliser le <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>, vous pouvez utiliser le <xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A>. Vous trouverez un exemple dans la section précédente. De même, au lieu d’utiliser le <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>, vous avez la possibilité d’utiliser l' <xref:System.Windows.Controls.ItemsControl.ItemContainerStyleSelector%2A>.  
  
 Deux autres propriétés liées au style de la <xref:System.Windows.Controls.ItemsControl> qui ne sont pas présentées ici sont <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> et <xref:System.Windows.Controls.ItemsControl.GroupStyleSelector%2A>.  
  
<a name="DataTemplating_HeirarchicalDataTemplate"></a>   
## <a name="support-for-hierarchical-data"></a>Prise en charge des données hiérarchiques  
 Jusqu’à présent, nous avons seulement vu comment lier et afficher une collection unique. Une collection peut contenir d’autres collections. La classe <xref:System.Windows.HierarchicalDataTemplate> est conçue pour être utilisée avec les types de <xref:System.Windows.Controls.HeaderedItemsControl> pour afficher ces données. Dans l’exemple suivant, `ListLeagueList` est une liste d’objets `League`. Chaque objet `League` a un `Name` et une collection d’objets `Division`. Chaque `Division` a un `Name` et une collection d’objets `Team` et chaque objet `Team` a un `Name`.  
  
 [!code-xaml[HierarchicalDataTemplateSnippet#HDT](~/samples/snippets/csharp/VS_Snippets_Wpf/HierarchicalDataTemplateSnippet/CS/window1.xaml#hdt)]  
  
 L’exemple montre qu’avec l’utilisation de <xref:System.Windows.HierarchicalDataTemplate>, vous pouvez facilement afficher des données de liste qui contiennent d’autres listes. Voici une capture d’écran de l’exemple.  
  
 ![Capture d’écran exemple HierarchicalDataTemplate](./media/databinding-hierarchicaldatatemplate.png "DataBinding_HierarchicalDataTemplate")  
  
## <a name="see-also"></a>Voir aussi

- [Liaison de données](../advanced/optimizing-performance-data-binding.md)
- [Rechercher des éléments générés par DataTemplate](how-to-find-datatemplate-generated-elements.md)
- [Application d’un style et création de modèles](../controls/styling-and-templating.md)
- [Vue d’ensemble de la liaison de données](../../../desktop-wpf/data/data-binding-overview.md)
- [Vue d’ensemble des modèles et styles d’en-tête de colonne GridView](../controls/gridview-column-header-styles-and-templates-overview.md)
