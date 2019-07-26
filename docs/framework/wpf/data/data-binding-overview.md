---
title: Vue d’ensemble de la liaison de données
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data conversion for binding [WPF]
- binding data [WPF], about data binding
- data binding [WPF], about data binding
- conversion for data binding [WPF]
ms.assetid: c707c95f-7811-401d-956e-2fffd019a211
ms.openlocfilehash: e1fbb46c76fbc729818b6ff24b55c0d18f6b05df
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68400702"
---
# <a name="data-binding-overview"></a>Vue d’ensemble de la liaison de données
La liaison de données [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] offre un moyen simple et cohérent pour les applications de présenter les données et d’interagir avec elles. Les éléments peuvent être liés à des données provenant de diverses sources de données sous la forme d’objets common language runtime (CLR [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)]) et. <xref:System.Windows.Controls.ContentControl>tels que <xref:System.Windows.Controls.Button> et <xref:System.Windows.Controls.ItemsControl>, tels <xref:System.Windows.Controls.ListBox> que<xref:System.Windows.Controls.ListView> et, ont des fonctionnalités intégrées permettant d’activer le style flexible des éléments de données uniques ou des collections d’éléments de données. Des vues de tri, filtrage et groupage peuvent être générées sur la base des données.  
  
 La fonctionnalité de liaison de données dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] présente plusieurs avantages par rapport aux modèles traditionnels, notamment une large gamme de propriétés qui prennent en charge par nature la liaison de données, une représentation [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] flexible des données et une séparation nette de la logique métier de [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
 Cette rubrique aborde en premier les concepts [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fondamentaux de la liaison de données, puis passe à <xref:System.Windows.Data.Binding> l’utilisation de la classe et d’autres fonctionnalités de la liaison de données.  

<a name="what_is_data_binding"></a>   
## <a name="what-is-data-binding"></a>Qu’est-ce que la liaison de données ?  
 La liaison de données est le processus qui établit une connexion entre [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] de l’application et logique métier. Si la liaison est correctement paramétrée et si les données fournissent les notifications appropriées, lorsque les données changent de valeur, les éléments qui sont liés aux données reflètent automatiquement ces changements. La liaison de données peut également signifier que si une représentation externe des données dans un élément change, les données sous-jacentes peuvent être automatiquement mises à jour pour refléter les modifications. Par exemple, si l’utilisateur modifie la valeur dans un <xref:System.Windows.Controls.TextBox> élément, la valeur de données sous-jacente est automatiquement mise à jour pour refléter cette modification.  
  
 Une utilisation typique de la liaison de données consiste à placer des données de configuration locale ou de serveur dans des formulaires ou d’autres contrôles [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], ce concept est développé pour inclure la liaison d’une large gamme de propriétés à diverses sources de données. Dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], les propriétés de dépendance des éléments peuvent être liées aux objets CLR (y compris les objets ADO.net ou les objets associés aux services Web [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] et aux propriétés Web) et aux données.  
  
 Pour obtenir un exemple de liaison de données, examinons l’application [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] suivante de la [Démonstration de la liaison de données](https://go.microsoft.com/fwlink/?LinkID=163703) :  
  
 ![Capture d’écran exemple de liaison de données](./media/databinding-databindingdemo.png "DataBinding_DataBindingDemo")  
  
 Ce qui précède est le [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] d’une application qui affiche une liste d’éléments de vente aux enchères. L’application illustre les fonctionnalités suivantes de la liaison de données :  
  
- Le contenu de <xref:System.Windows.Controls.ListBox> est lié à une collection d’objets *AuctionItem* . An objet *AuctionItem* a des propriétés telles que *Description*, *StartPrice*, *StartDate*, *Category*, *SpecialFeatures*, etc.  
  
- Les données (objets*AuctionItem* ) affichées dans le <xref:System.Windows.Controls.ListBox> sont basées sur un modèle, de sorte que la description et le prix actuel sont affichés pour chaque élément. Pour ce faire, utilisez <xref:System.Windows.DataTemplate>un. En outre, l’apparence de chaque élément varie selon la valeur de *SpecialFeatures* de *l’AuctionItem* affiché. Si la valeur *SpecialFeatures* de *AuctionItem* est *Color*, l’élément a une bordure bleue. Si la valeur est *Highlight*, l’élément a une bordure orange et une étoile. La section [Modèles de données](#data_templating) fournit des informations sur les modèles de données.  
  
- L’utilisateur peut regrouper, filtrer ou trier les données à <xref:System.Windows.Controls.CheckBox>l’aide des es fournies. Dans l’image ci-dessus, l’option «regrouper par catégorie» et «trier <xref:System.Windows.Controls.CheckBox>par catégorie et date» sont sélectionnées. Vous avez peut-être remarqué que les données sont regroupées en fonction de la catégorie de produit et que les noms de catégorie sont dans l’ordre alphabétique. Cela est difficile à observer sur l’image, mais les éléments sont également triés par date de début dans chaque catégorie. Cette opération est effectuée à l’aide d’une *vue de collection*. La section [Lier à des collections](#binding_to_collections) traite des vues de collection.  
  
- Lorsque l’utilisateur sélectionne un élément, <xref:System.Windows.Controls.ContentControl> affiche les détails de l’élément sélectionné. Il s’agit du *Scénario maître/détail*. La section [Scénario maître/détail](#master_detail_scenario) fournit des informations sur ce type de scénario de liaison.  
  
- Le type de la propriété *StartDate* est <xref:System.DateTime>, qui retourne une date qui comprend l’heure à la milliseconde. Dans cette application, un convertisseur personnalisé a été utilisé afin qu’une chaîne de date courte soit affichée. La section [Conversion de données](#data_conversion) fournit des informations sur les convertisseurs.  
  
 Lorsque l’utilisateur clique sur le bouton *Ajouter un produit*, le formulaire suivant s’affiche :  
  
 ![Page Ajouter la liste de produits](./media/databinding-demo-addproductlisting.png "DataBinding_Demo_AddProductListing")  
  
 L’utilisateur peut modifier les champs dans le formulaire, consulter la liste de produits à l’aide de l’aperçu court et des volets d’aperçu plus détaillés, puis cliquer sur *Envoyer* pour ajouter la nouvelle liste de produits. Tout regroupement, filtrage ou tri existant sera appliqué à la nouvelle entrée. Dans ce cas particulier, l’élément entré dans l’image ci-dessus s’affichera comme deuxième élément dans la catégorie *Computer*.  
  
 La logique de validation fournie dans la *Date* <xref:System.Windows.Controls.TextBox>de début n’est pas illustrée dans cette image. Si l’utilisateur entre une date non valide (mise en forme non valide ou date passée), l’utilisateur est averti avec <xref:System.Windows.Controls.ToolTip> un et un point <xref:System.Windows.Controls.TextBox>d’exclamation rouge à côté de. La section [Validation des données](#data_validation) explique comment créer une logique de validation.  
  
 Avant d’aborder les différentes fonctionnalités de liaison de données décrites ci-dessus, nous couvrirons d’abord dans la section suivante les concepts fondamentaux qui sont critiques pour la compréhension de la liaison de données [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
## <a name="basic-data-binding-concepts"></a>Concepts de liaison de données de base  
  
 Quels que soient l’élément que vous liez et la nature de votre source de données, chaque liaison suit toujours le modèle illustré par l’illustration suivante :  
  
 ![Diagramme qui montre le modèle de liaison de données de base.](./media/data-binding-overview/basic-data-binding-diagram.png)  
  
 Comme présenté sur l’illustration ci-dessus, la liaison de données est essentiellement la passerelle entre votre cible de liaison et de votre source de liaison. L’illustration présente les concepts de liaison de données [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] essentiels suivants :  
  
- En général, chaque liaison possède ces quatre composants : un objet de cible de liaison, une propriété cible, une source de liaison et un chemin vers la valeur de la source de liaison à utiliser. Par exemple, si vous souhaitez lier le contenu d' <xref:System.Windows.Controls.TextBox> un à la propriété *Name* d’un objet *Employee* , votre objet Target est le <xref:System.Windows.Controls.TextBox>, la propriété Target est la <xref:System.Windows.Controls.TextBox.Text%2A> propriété, la valeur à utiliser est *Name*et le l’objet source est  l’objet Employee.  
  
- La propriété cible doit être une propriété de dépendance. La <xref:System.Windows.UIElement> plupart des propriétés sont des propriétés de dépendance et la plupart des propriétés de dépendance, à l’exception de celles en lecture seule, prennent en charge la liaison de données par défaut. (Seuls <xref:System.Windows.DependencyObject> les types peuvent définir des propriétés de <xref:System.Windows.UIElement>dépendance et tous <xref:System.Windows.DependencyObject>les dérivés de.)  
  
- Bien que cela ne soit pas spécifié dans la figure, il convient de noter que l’objet de source de liaison n’est pas limité à un objet CLR personnalisé. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]la liaison de données prend en charge les données sous la [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]forme d’objets CLR et. Pour fournir quelques exemples, votre source de liaison peut être <xref:System.Windows.UIElement>un, n’importe quel objet de liste, un objet CLR associé à des données ADO.net ou des services Web, ou un [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] XMLNode qui contient vos données. Pour plus d’informations, consultez [Vue d’ensemble de la liaison de ressources](binding-sources-overview.md).  
  
 Lorsque vous lisez les autres rubriques [!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)], il est important de vous rappeler que lorsque vous établissez une liaison, vous liez une cible de liaison *à* une source de liaison. Par exemple, si vous affichez des données [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] sous-jacentes <xref:System.Windows.Controls.ListBox> dans un à l’aide de la [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] liaison <xref:System.Windows.Controls.ListBox> de données, vous liez votre aux données.  
  
 Pour établir une liaison, vous utilisez l' <xref:System.Windows.Data.Binding> objet. Le reste de cette rubrique traite de la plupart des concepts associés à et de certaines des propriétés et de l’utilisation <xref:System.Windows.Data.Binding> de l’objet.  
  
<a name="direction_of_data_flow"></a>   
### <a name="direction-of-the-data-flow"></a>Direction du flux de données  
 Comme mentionné précédemment et comme indiqué par la flèche de la figure ci-dessus, le workflow d’une liaison peut passer de la cible de liaison à la source de liaison (par exemple, la valeur source change quand un utilisateur modifie la valeur <xref:System.Windows.Controls.TextBox>d’un) et/ou de la source de liaison à la cible de liaison (par exemple, <xref:System.Windows.Controls.TextBox> votre contenu est mis à jour avec les modifications dans la source de liaison) si la source de liaison fournit les notifications appropriées.  
  
 Vous souhaiterez peut-être que votre application permette aux utilisateurs de modifier les données et les propager à nouveau vers l’objet source. Ou vous souhaitez peut-être ne pas permettre aux utilisateurs de mettre à jour la source de données. Vous pouvez contrôler cela en définissant <xref:System.Windows.Data.Binding.Mode%2A> la propriété de <xref:System.Windows.Data.Binding> votre objet. L’exemple suivant illustre les différents types de flux de données :  
  
 ![Flux de données de liaison de données](./media/databinding-dataflow.png "DataBinding_DataFlow")  
  
- <xref:System.Windows.Data.BindingMode.OneWay>la liaison entraîne la mise à jour automatique de la propriété cible par les modifications apportées à la propriété source, mais les modifications apportées à la propriété cible ne sont pas propagées vers la propriété source. Ce type de liaison est approprié si le contrôle lié est implicitement en lecture seule. Par exemple, vous pouvez lier à une source comme un affichage de cotations boursières, ou il se peut que votre propriété cible ne possède aucune interface de contrôle pour apporter des modifications, comme une couleur d’arrière-plan liée aux données d’une table. S’il n’est pas nécessaire de surveiller les modifications de la propriété cible, l’utilisation du mode de liaison <xref:System.Windows.Data.BindingMode.OneWay> permet d’éviter la surcharge du mode de liaison <xref:System.Windows.Data.BindingMode.TwoWay>.  
  
- <xref:System.Windows.Data.BindingMode.TwoWay>la liaison entraîne la mise à jour automatique de l’autre des modifications apportées à la propriété source ou à la propriété cible. Ce type de liaison convient aux formulaires modifiables ou à d’autres scénarios [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] entièrement interactifs. La plupart des propriétés <xref:System.Windows.Data.BindingMode.OneWay> ont par défaut la liaison, mais certaines propriétés de dépendance (en général, les propriétés <xref:System.Windows.Controls.TextBox.Text%2A> des contrôles modifiables par l’utilisateur, tels que la propriété de <xref:System.Windows.Controls.TextBox> et la propriété de <xref:System.Windows.Controls.CheckBox>) ont par défaut la <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> valeur <xref:System.Windows.Data.BindingMode.TwoWay> liaison. Un moyen de déterminer par programmation si une propriété de dépendance établit par défaut une liaison unidirectionnelle ou bidirectionnelle consiste à obtenir les métadonnées de la propriété à l’aide de <xref:System.Windows.DependencyProperty.GetMetadata%2A>, puis à vérifier la valeur booléenne de la propriété <xref:System.Windows.FrameworkPropertyMetadata.BindsTwoWayByDefault%2A>.  
  
- <xref:System.Windows.Data.BindingMode.OneWayToSource>est l’inverse de <xref:System.Windows.Data.BindingMode.OneWay> la liaison; il met à jour la propriété source lorsque la propriété cible change. Un exemple de scénario est si vous devez seulement réévaluer la valeur source à partir de [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
- La liaison n’est <xref:System.Windows.Data.BindingMode.OneTime> pas illustrée dans la figure, ce qui amène la propriété source à initialiser la propriété cible, mais les modifications ultérieures ne se propagent pas. Cela signifie que si le contexte de données subit une modification ou que l’objet dans le contexte des données change, la modification n'est pas répercutée dans la propriété cible. Ce type de liaison est approprié si vous utilisez des données réellement statiques ou qui se prêtent à l’utilisation d’un instantané de l’état actuel. Ce type de liaison est également utile si vous souhaitez initialiser votre propriété cible avec une valeur d’une propriété source et que le contexte de données n’est pas connu à l’avance. Il s’agit essentiellement d’une forme simplifiée de la liaison <xref:System.Windows.Data.BindingMode.OneWay> qui offre de meilleures performances dans les cas où la valeur source ne change pas.  
  
 Notez que pour détecter les modifications de la source <xref:System.Windows.Data.BindingMode.OneWay> ( <xref:System.Windows.Data.BindingMode.TwoWay> applicables aux liaisons et), la source doit implémenter un mécanisme de notification de <xref:System.ComponentModel.INotifyPropertyChanged>modification de propriété approprié, tel que. Pour [](how-to-implement-property-change-notification.md) obtenir un exemple d' <xref:System.ComponentModel.INotifyPropertyChanged> implémentation, consultez implémenter la notification de modification de propriété.  
  
 La <xref:System.Windows.Data.Binding.Mode%2A> page de propriétés fournit des informations supplémentaires sur les modes de liaison et un exemple de spécification de la direction d’une liaison.  
  
<a name="what_triggers_source_updates"></a>   
### <a name="what-triggers-source-updates"></a>Ce qui déclenche les mises à jour de la source  
 Les liaisons qui sont <xref:System.Windows.Data.BindingMode.TwoWay> ou <xref:System.Windows.Data.BindingMode.OneWayToSource> écoutent les modifications dans la propriété cible et les propagent vers la source. On appelle cela la mise à jour de la source. Par exemple, vous pouvez modifier le texte d’une zone de texte pour modifier la valeur source sous-jacente. Comme décrit dans la dernière section, la direction du workflow est déterminée par la valeur de la <xref:System.Windows.Data.Binding.Mode%2A> propriété de la liaison.  
  
 Toutefois, est-ce que votre valeur source est mise à jour lorsque vous modifiez le texte ou après avoir fini de modifier le texte et pointé votre souris en dehors de la zone de texte ? La <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> propriété de la liaison détermine ce qui déclenche la mise à jour de la source. Les points des flèches droite de la figure suivante illustrent le rôle de la <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> propriété:  
  
 ![Diagramme qui montre le rôle de la propriété UpdateSourceTrigger.](./media/data-binding-overview/data-binding-updatesource-trigger.png)  
  
 Si la <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> valeur est <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>, la valeur désignée par la flèche droite de <xref:System.Windows.Data.BindingMode.TwoWay> ou les <xref:System.Windows.Data.BindingMode.OneWayToSource> liaisons est mise à jour dès que la propriété cible est modifiée. Toutefois, si la <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> valeur est <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>, cette valeur est uniquement mise à jour avec la nouvelle valeur lorsque la propriété cible perd le focus.  
  
 Comme pour la <xref:System.Windows.Data.Binding.Mode%2A> propriété, différentes propriétés de dépendance ont des <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> valeurs par défaut différentes. La valeur par défaut de la plupart des propriétés de dépendance est <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>, tandis que celle de la propriété <xref:System.Windows.Controls.TextBox.Text%2A> a comme valeur par défaut <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>. Cela signifie que les mises à jour de la source se produisent généralement chaque fois que la propriété cible <xref:System.Windows.Controls.CheckBox>change, ce qui est parfait pour es et d’autres contrôles simples. Toutefois, pour les champs de texte, la mise à jour après chaque frappe de clavier peut réduire les performances et empêche l’utilisateur de revenir en arrière pour corriger les fautes de frappe avant de valider la nouvelle valeur. C’est la raison <xref:System.Windows.Controls.TextBox.Text%2A> pour laquelle la propriété a une <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus> valeur par <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>défaut au lieu de.  
  
 Pour plus <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> d’informations sur la recherche de la valeur par défaut <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> d’une propriété de dépendance, consultez la page de propriétés.  
  
 Le tableau suivant fournit un exemple de scénario pour <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> chaque valeur à <xref:System.Windows.Controls.TextBox> l’aide de la comme exemple:  
  
|Valeur UpdateSourceTrigger|Quand la valeur source est mise à jour|Exemple de scénario pour TextBox|  
|-------------------------------|----------------------------------------|----------------------------------|  
|LostFocus (valeur par <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType>défaut pour)|Lorsque le contrôle TextBox perd le focus|Qui <xref:System.Windows.Controls.TextBox> est associé à la logique de validation (voir la section Validation des données)|  
|PropertyChanged|À mesure que vous tapez dans la<xref:System.Windows.Controls.TextBox>|<xref:System.Windows.Controls.TextBox>contrôles dans une fenêtre de salle de conversation|  
|Explicit|Lorsque l’application appelle<xref:System.Windows.Data.BindingExpression.UpdateSource%2A>|<xref:System.Windows.Controls.TextBox>contrôles dans un formulaire modifiable (met à jour les valeurs sources uniquement lorsque l’utilisateur clique sur le bouton Envoyer)|  
  
 Pour un exemple, consultez [Contrôler quand le texte TextBox met à jour la source](how-to-control-when-the-textbox-text-updates-the-source.md).  
  
<a name="creating_a_binding"></a>   
## <a name="creating-a-binding"></a>Création d’une liaison  
  
 Pour récapituler certains des concepts abordés dans les sections précédentes, vous établissez une liaison à l' <xref:System.Windows.Data.Binding> aide de l’objet, et chaque liaison a généralement quatre composants: la cible de liaison, la propriété cible, la source de liaison et un chemin d’accès à la valeur source à utiliser. Cette section explique comment configurer une liaison.  
  
 Prenons l’exemple suivant, dans lequel l’objet de source de liaison est une classe nommée *MyData* qui est définie dans l’espace de noms *SDKSample*. À des fins de démonstration, la classe *MyData* a une propriété de chaîne nommée *ColorName*, dont la valeur est définie sur « Rouge ». Par conséquent, cet exemple génère un bouton avec un arrière-plan rouge.  
  
 [!code-xaml[BindNonTextProperty#1](~/samples/snippets/csharp/VS_Snippets_Wpf/BindNonTextProperty/CS/Page1.xaml#1)]  
  
 Pour plus d’informations sur la syntaxe de déclaration de liaison et pour obtenir des exemples montrant comment définir une liaison dans le code, consultez [Vue d'ensemble des déclarations de liaison](binding-declarations-overview.md).  
  
 Si nous appliquons cet exemple à notre diagramme de base, l’illustration qui en résulte ressemble à ce qui suit. Il s’agit <xref:System.Windows.Data.BindingMode.OneWay> d’une liaison, car la <xref:System.Windows.Data.BindingMode.OneWay> propriété Background prend en charge la liaison par défaut.  
  
 ![Diagramme qui affiche la propriété d’arrière-plan de liaison de données.](./media/data-binding-overview/data-binding-button-background-example.png)  
  
 Vous vous demandez peut-être pourquoi cela fonctionne même si la propriété *colorname* est de type <xref:System.Windows.Controls.Control.Background%2A> chaîne alors que la <xref:System.Windows.Media.Brush>propriété est de type. Il s’agit de la conversion de type par défaut en action, et nous l’évoquons dans la section [Conversion de données](#data_conversion).  
  
<a name="specifying_the_binding_source"></a>   
### <a name="specifying-the-binding-source"></a>Spécifier la source de liaison  
 Notez que dans l’exemple précédent, la source de liaison est spécifiée en définissant la <xref:System.Windows.FrameworkElement.DataContext%2A> propriété sur l' <xref:System.Windows.Controls.DockPanel> élément. Hérite <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.DockPanel>ensuite de la valeurde,quiest<xref:System.Windows.FrameworkElement.DataContext%2A> son élément parent. Pour rappel, l’objet de source de liaison est un des quatre composants nécessaires d’une liaison. Par conséquent, sans objet de source de liaison spécifié, la liaison ne fait rien.  
  
 Il existe plusieurs façons de spécifier l’objet de source de liaison. L’utilisation <xref:System.Windows.FrameworkElement.DataContext%2A> de la propriété sur un élément parent est utile lorsque vous liez plusieurs propriétés à la même source. Cependant, il peut parfois être plus approprié de spécifier la source de liaison sur des déclarations de liaison individuelles. Pour l’exemple précédent, au lieu d’utiliser <xref:System.Windows.FrameworkElement.DataContext%2A> la propriété, vous pouvez spécifier la source de liaison en <xref:System.Windows.Data.Binding.Source%2A> définissant la propriété directement sur la déclaration de liaison du bouton, comme dans l’exemple suivant:  
  
 [!code-xaml[BindNonTextProperty#BackgroundBindingCompact](~/samples/snippets/csharp/VS_Snippets_Wpf/BindNonTextProperty/CS/Page2.xaml#backgroundbindingcompact)]  
  
 En dehors de la <xref:System.Windows.FrameworkElement.DataContext%2A> définition directe de la propriété sur un élément, <xref:System.Windows.FrameworkElement.DataContext%2A> en héritant de la valeur d’un ancêtre (tel que le bouton dans le premier exemple) et en spécifiant explicitement <xref:System.Windows.Data.Binding.Source%2A> la source de liaison en définissant la propriété sur <xref:System.Windows.Data.Binding> (tel que le bouton du dernier exemple), vous pouvez également utiliser la <xref:System.Windows.Data.Binding.ElementName%2A> propriété ou la <xref:System.Windows.Data.Binding.RelativeSource%2A> propriété pour spécifier la source de liaison. La <xref:System.Windows.Data.Binding.ElementName%2A> propriété est utile lorsque vous effectuez une liaison à d’autres éléments dans votre application, par exemple lorsque vous utilisez un curseur pour ajuster la largeur d’un bouton. La <xref:System.Windows.Data.Binding.RelativeSource%2A> propriété est utile lorsque la liaison est spécifiée dans un <xref:System.Windows.Controls.ControlTemplate> ou un <xref:System.Windows.Style>. Pour plus d’informations, consultez [Spécifier la source de liaison](how-to-specify-the-binding-source.md).  
  
<a name="specifying_the_path_to_the_value"></a>   
### <a name="specifying-the-path-to-the-value"></a>Spécification du chemin vers la valeur  
 Si votre source de liaison est un objet, vous utilisez <xref:System.Windows.Data.Binding.Path%2A> la propriété pour spécifier la valeur à utiliser pour votre liaison. Si vous effectuez une liaison [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] à des données, vous <xref:System.Windows.Data.Binding.XPath%2A> utilisez la propriété pour spécifier la valeur. Dans certains cas, il peut s’avérer nécessaire d’utiliser <xref:System.Windows.Data.Binding.Path%2A> la propriété même lorsque vos données [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]sont. Par exemple, si vous souhaitez accéder à la propriété Name d’un XmlNode retourné (à la suite d’une requête XPath), vous devez utiliser la <xref:System.Windows.Data.Binding.Path%2A> propriété en plus de la <xref:System.Windows.Data.Binding.XPath%2A> propriété.  
  
 Pour obtenir des informations de syntaxe et des <xref:System.Windows.Data.Binding.Path%2A> exemples <xref:System.Windows.Data.Binding.XPath%2A> , consultez les pages de propriétés et.  
  
 Notez que, bien que nous ayons insisté <xref:System.Windows.Data.Binding.Path%2A> sur le fait que la valeur à utiliser est l’un des quatre composants nécessaires d’une liaison, dans les scénarios que vous souhaitez lier à un objet entier, la valeur à utiliser serait la même que l’objet de source de liaison. Dans ce cas, il est applicable de ne pas spécifier <xref:System.Windows.Data.Binding.Path%2A>de. Prenons l'exemple suivant :  
  
 [!code-xaml[MasterDetail#EmptyBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/MasterDetail/CSharp/Page1.xaml#emptybinding)]  
  
 L’exemple ci-dessus utilise la syntaxe de liaison vide : {Binding}. Dans ce cas, le <xref:System.Windows.Controls.ListBox> hérite du DataContext d’un élément DockPanel parent (non illustré dans cet exemple). Lorsque le chemin d’accès n’est pas spécifié, le comportement par défaut consiste à lier à l’objet entier. En d’autres termes, dans cet exemple, le chemin d’accès a été omis, car la <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> propriété est liée à la totalité de l’objet. (Voir la section [Lier à des collections](#binding_to_collections) pour une discussion détaillée.)  
  
 En plus de la liaison à une collection, ce scénario est utile lorsque vous souhaitez lier un objet entier plutôt qu’une seule propriété d’un objet. Par exemple, si votre objet source est simplement de type chaîne et que vous souhaitez lier la chaîne elle-même. Un autre scénario courant est lorsque vous souhaitez lier un élément à un objet avec plusieurs propriétés.  
  
 Notez que vous devrez peut-être appliquer une logique personnalisée afin que les données soient significatives pour votre propriété cible liée aux données. La logique personnalisée peut être sous la forme d’un convertisseur personnalisé (si la conversion de type par défaut n’existe pas). Consultez [Conversion de données](#data_conversion) pour plus d’informations sur les convertisseurs.  
  
<a name="binding_bindingexpression"></a>   
### <a name="binding-and-bindingexpression"></a>Binding et BindingExpression  
 Avant d’entrer dans d’autres fonctionnalités et utilisations de la liaison de données, il serait utile d' <xref:System.Windows.Data.BindingExpression> introduire la classe. Comme vous l’avez vu dans les sections précédentes <xref:System.Windows.Data.Binding> , la classe est la classe de haut niveau pour la déclaration d’une liaison <xref:System.Windows.Data.Binding> ; la classe fournit de nombreuses propriétés qui vous permettent de spécifier les caractéristiques d’une liaison. Une classe connexe <xref:System.Windows.Data.BindingExpression>,, est l’objet sous-jacent qui gère la connexion entre la source et la cible. Une liaison contient toutes les informations qui peuvent être partagées entre plusieurs expressions de liaison. Un <xref:System.Windows.Data.BindingExpression> est une expression <xref:System.Windows.Data.Binding>d’instance qui ne peut pas être partagée et qui contient toutes les informations d’instance de.  
  
 Par exemple, considérez les éléments suivants, où *myDataObject* est une instance de la classe *MyData* , *myBinding* est l’objet source <xref:System.Windows.Data.Binding> et la classe *MyData* est une classe définie qui contient une propriété de type chaîne nommée  *MyDataProperty*. Cet exemple lie le contenu de texte de *mytext*, une instance de <xref:System.Windows.Controls.TextBlock>, à *MyDataProperty*.  
  
 [!code-csharp[CodeOnlyBinding#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#1)]
 [!code-vb[CodeOnlyBinding#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#1)]  
  
 Vous pouvez utiliser le même objet *myBinding* pour créer d’autres liaisons. Par exemple, vous pouvez utiliser l’objet *myBinding* pour lier le contenu textuel d’une case à cocher à *MyDataProperty*. Dans ce scénario, il y aura deux instances de <xref:System.Windows.Data.BindingExpression> partage de l’objet *myBinding* .  
  
 Un <xref:System.Windows.Data.BindingExpression> objet peut être obtenu via la valeur de retour de <xref:System.Windows.Data.BindingOperations.GetBindingExpression%2A> l’appel de sur un objet lié aux données. Les rubriques suivantes montrent quelques-unes des utilisations de la <xref:System.Windows.Data.BindingExpression> classe:  
  
- [Obtenir l'objet de liaison d'une propriété cible liée aux données](how-to-get-the-binding-object-from-a-bound-target-property.md)  
  
- [Contrôler quand le texte TextBox met à jour la source](how-to-control-when-the-textbox-text-updates-the-source.md)  
  
<a name="data_conversion"></a>   
## <a name="data-conversion"></a>Conversion de données  
 Dans l’exemple précédent, le bouton est rouge, car <xref:System.Windows.Controls.Control.Background%2A> sa propriété est liée à une propriété de type chaîne avec la valeur «Red». Cela fonctionne, car un convertisseur de type est présent <xref:System.Windows.Media.Brush> sur le type pour convertir la valeur <xref:System.Windows.Media.Brush>de chaîne en.  
  
 Pour ajouter ces informations à l’illustration dans la section [Création d’une liaison](#creating_a_binding), le diagramme présente l’aspect suivant :  
  
 ![Diagramme qui affiche la propriété de liaison de données par défaut.](./media/data-binding-overview/data-binding-button-default-conversion.png)  
  
 Toutefois, que se passe-t-il si, au lieu d’avoir une propriété de  type chaîne, votre <xref:System.Windows.Media.Color>objet de source de liaison a une propriété Color de type? Dans ce cas, pour que la liaison fonctionne, vous devez d’abord transformer la valeur de la propriété *Color* en un nom que <xref:System.Windows.Controls.Control.Background%2A> la propriété accepte. Vous devez créer un convertisseur personnalisé en implémentant l' <xref:System.Windows.Data.IValueConverter> interface, comme dans l’exemple suivant:  
  
 [!code-csharp[ColorPicker_snip#16](~/samples/snippets/csharp/VS_Snippets_Wpf/ColorPicker_snip/CSharp/ColorPickerLib/ColorPicker.cs#16)]
 [!code-vb[ColorPicker_snip#16](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ColorPicker_snip/visualbasic/colorpickerlib/colorpicker.vb#16)]  
  
 La <xref:System.Windows.Data.IValueConverter> page de référence fournit plus d’informations.  
  
 Maintenant, le convertisseur personnalisé est utilisé au lieu de la conversion par défaut, et notre diagramme ressemble à ceci :  
  
 ![Diagramme qui montre le convertisseur personnalisé de liaison de données.](./media/data-binding-overview/data-binding-converter-color-example.png)  
  
 Pour rappel, des conversions par défaut peuvent être disponibles si des convertisseurs de type sont présents dans le type lié. Ce comportement dépendra des convertisseurs de type sont disponibles dans la cible. En cas de doute, créez votre propre convertisseur.  
  
 Voici quelques scénarios classiques où il est préférable d’implémenter un convertisseur de données :  
  
- Vos données devraient s’afficher différemment, selon la culture. Par exemple, vous souhaitez peut-être implémenter un convertisseur de devise ou un convertisseur de date/heure de calendrier en fonction des valeurs ou des normes utilisées dans une culture particulière.  
  
- Les données utilisées ne sont pas nécessairement destinées à modifier la valeur du texte d’une propriété, mais plutôt à modifier une autre valeur, comme la source d’une image ou la couleur ou le style du texte affiché. Les convertisseurs peuvent être utilisés ici en convertissant la liaison d’une propriété qui peut ne pas sembler appropriée, comme la liaison d’un champ de texte à la propriété Background d’une cellule de tableau.  
  
- Plusieurs contrôles ou propriétés de contrôles sont liés aux mêmes données. Dans ce cas, la liaison principale peut afficher uniquement le texte, tandis que les autres liaisons gèrent des problèmes d’affichage spécifiques, mais utilisent toujours la même liaison comme informations source.  
  
- Jusqu’à présent, nous n’avons <xref:System.Windows.Data.MultiBinding>pas encore abordé, où une propriété cible a une collection de liaisons. Dans le cas d’un <xref:System.Windows.Data.MultiBinding>, vous utilisez un personnalisé <xref:System.Windows.Data.IMultiValueConverter> pour produire une valeur finale à partir des valeurs des liaisons. Par exemple, la couleur peut être calculée à partir des valeurs rouge, vert et bleu, qui peuvent être des valeurs à partir d’objets de source de liaison identiques ou différents. Pour obtenir <xref:System.Windows.Data.MultiBinding> des exemples et des informations, consultez la page de la classe.  
  
<a name="binding_to_collections"></a>   
## <a name="binding-to-collections"></a>Lier à des collections  
  
 Un objet de source de liaison peut être traité comme un objet unique dont les propriétés contiennent des données, ou comme une collection de données d’objets polymorphiques souvent regroupées ensemble (par exemple, le résultat d’une requête sur une base de données). Jusqu'à présent, nous avons seulement vu la liaison à des objets individuels, mais la liaison à une collection de données est un scénario courant. Par exemple, un scénario courant consiste à utiliser un <xref:System.Windows.Controls.ItemsControl> tel <xref:System.Windows.Controls.ListBox>que, <xref:System.Windows.Controls.ListView>ou <xref:System.Windows.Controls.TreeView> pour afficher une collection de données, par exemple dans l’application indiquée dans la section [qu’est-ce que la liaison de données?](#what_is_data_binding) .  
  
 Heureusement, notre diagramme de base est toujours applicable. Si vous liez un <xref:System.Windows.Controls.ItemsControl> à une collection, le diagramme se présente comme suit:  
  
 ![Diagramme qui affiche l’objet ItemsControl de liaison de données.](./media/data-binding-overview/data-binding-itemscontrol.png)  
  
 Comme indiqué dans ce diagramme, pour lier un <xref:System.Windows.Controls.ItemsControl> à un objet de collection <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> , la propriété est la propriété à utiliser. Vous pouvez considérer <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> la propriété comme le contenu <xref:System.Windows.Controls.ItemsControl>du. Notez que la liaison est <xref:System.Windows.Data.BindingMode.OneWay> due au <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> fait que <xref:System.Windows.Data.BindingMode.OneWay> la propriété prend en charge la liaison par défaut.  
  
<a name="how_to_implement_collections"></a>   
### <a name="how-to-implement-collections"></a>Guide d’implémentation des collections  
 Vous pouvez énumérer n’importe quelle collection qui implémente <xref:System.Collections.IEnumerable> l’interface. Toutefois, pour configurer des liaisons dynamiques afin que les insertions ou les suppressions dans la collection [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] mettent à jour automatiquement, la collection <xref:System.Collections.Specialized.INotifyCollectionChanged> doit implémenter l’interface. Cette interface expose un événement qui doit être déclenché chaque fois que la collection sous-jacente est modifiée.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]fournit la <xref:System.Collections.ObjectModel.ObservableCollection%601> classe, qui est une implémentation intégrée d’une collection de données qui expose l' <xref:System.Collections.Specialized.INotifyCollectionChanged> interface. Notez que pour prendre entièrement en charge le transfert des valeurs de données des objets source vers les cibles, chaque objet de votre collection qui prend en <xref:System.ComponentModel.INotifyPropertyChanged> charge les propriétés pouvant être liées doit également implémenter l’interface. Pour plus d’informations, consultez [Vue d’ensemble de la liaison de ressources](binding-sources-overview.md).  
  
 Avant d’implémenter votre propre collection, <xref:System.Collections.ObjectModel.ObservableCollection%601> envisagez d’utiliser ou une des classes de <xref:System.Collections.Generic.List%601>collection existantes, <xref:System.ComponentModel.BindingList%601>telles que, <xref:System.Collections.ObjectModel.Collection%601>et, parmi de nombreuses autres. Si vous avez un scénario avancé et que vous souhaitez implémenter votre propre collection, <xref:System.Collections.IList>envisagez d’utiliser, qui fournit une collection non générique d’objets accessibles individuellement par index, et donc des performances optimales.  
  
<a name="collection_views"></a>   
### <a name="collection-views"></a>Vues de collection  
 Une fois <xref:System.Windows.Controls.ItemsControl> que votre est lié à une collection de données, vous souhaiterez peut-être Trier, filtrer ou regrouper les données. Pour ce faire, vous utilisez des vues de collection, qui sont des classes <xref:System.ComponentModel.ICollectionView> qui implémentent l’interface.  

#### <a name="what-are-collection-views"></a>Que sont les vues de collection ?  
 Une vue de collection est une couche sur une collection de sources de liaison qui vous permet de parcourir et d’afficher la collection source sur la base de requêtes de tri, de filtrage et de groupage, sans avoir à modifier la collection source sous-jacente elle-même. Une vue de collection maintient également un pointeur vers l’élément actuel dans la collection. Si la collection source implémente l' <xref:System.Collections.Specialized.INotifyCollectionChanged> interface, les modifications déclenchées par <xref:System.Collections.Specialized.INotifyCollectionChanged.CollectionChanged> l’événement sont propagées aux vues.  
  
 Étant donné que les vues ne modifient pas les collections source sous-jacentes, chaque collection source peut avoir plusieurs vues associées. Par exemple, vous pouvez avoir une collection d’objets *Task*. À l’aide de vues, vous pouvez afficher ces mêmes données de différentes façons. Par exemple, sur le côté gauche de votre page, vous souhaitez peut-être afficher les tâches triées par priorité et, sur le côté droit, les regrouper par domaine.  
  
<a name="how_to_create_a_view"></a>   
#### <a name="how-to-create-a-view"></a>Guide de création d’une vue  
 Un moyen de créer et utiliser une vue consiste à instancier l’objet de vue directement et de l’utiliser comme source de liaison. Par exemple, considérez l’application [Démonstration de liaison de données](https://go.microsoft.com/fwlink/?LinkID=163703) présentée dans la section [Qu’est-ce que la liaison de données ?](#what_is_data_binding). L’application est implémentée de telle <xref:System.Windows.Controls.ListBox> sorte que le lie à une vue sur la collection de données plutôt que directement à la collection de données. L’exemple suivant est extrait de l’application [Démonstration de liaison de données](https://go.microsoft.com/fwlink/?LinkID=163703). La <xref:System.Windows.Data.CollectionViewSource> classe est le [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] proxy d’une classe qui hérite de <xref:System.Windows.Data.CollectionView>. Dans cet exemple particulier, le <xref:System.Windows.Data.CollectionViewSource.Source%2A> de la vue est lié à la collection *AuctionItems* (de type <xref:System.Collections.ObjectModel.ObservableCollection%601>) de l’objet d’application actuel.  
  
 [!code-xaml[DataBindingLab#WindowResources1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#windowresources1)]  
[!code-xaml[DataBindingLab#CollectionViewSource](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#collectionviewsource)]  
[!code-xaml[DataBindingLab#WindowResources2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#windowresources2)]  
  
 La ressource *listingDataView* sert ensuite de source de liaison pour les éléments de l’application, tels que <xref:System.Windows.Controls.ListBox>:  
  
 [!code-xaml[DataBindingLab#Master1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#master1)]  
[!code-xaml[DataBindingLab#Master2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#master2)]  
  
 Pour créer une autre vue pour la même collection, vous pouvez créer <xref:System.Windows.Data.CollectionViewSource> une autre instance et lui attribuer `x:Key` un nom différent.  
  
 Le tableau suivant répertorie les types de données d’affichage qui sont créés en tant que <xref:System.Windows.Data.CollectionViewSource> vue de collection par défaut ou en fonction du type de collection source.  
  
|Type de collection source|Type de vue de collection|Notes|  
|----------------------------|--------------------------|-----------|  
|<xref:System.Collections.IEnumerable>|Type interne basé sur<xref:System.Windows.Data.CollectionView>|Impossible de grouper les éléments.|  
|<xref:System.Collections.IList>|<xref:System.Windows.Data.ListCollectionView>|Le plus rapide.|  
|<xref:System.ComponentModel.IBindingList>|<xref:System.Windows.Data.BindingListCollectionView>||  
  
##### <a name="using-a-default-view"></a>Utilisation d’une vue par défaut  
 La spécification d’une vue de collection comme source de liaison est un moyen de créer et utiliser une vue de collection. WPF crée également une vue de collection par défaut pour chaque collection utilisée comme source de liaison. Si vous liez directement à une collection, WPF crée une liaison sur sa vue par défaut. Notez que cette vue par défaut est partagée par toutes les liaisons à la même collection, ainsi une modification apportée à une vue par défaut par un code ou contrôle lié (par exemple avec un tri ou une modification du pointeur d’élément actuel, dont nous parlons plus loin) se répercute dans toutes les autres liaisons à la même collection.  
  
 Pour obtenir la vue par défaut, utilisez la <xref:System.Windows.Data.CollectionViewSource.GetDefaultView%2A> méthode. Pour un exemple, consultez [Obtenir la vue par défaut d'une collection de données](how-to-get-the-default-view-of-a-data-collection.md).  
  
##### <a name="collection-views-with-adonet-datatables"></a>Vues de collection avec ADO.NET DataTables  
 Pour améliorer les performances, les vues de <xref:System.Data.DataTable> collection <xref:System.Data.DataView> pour les ADO.net ou les objets délèguent le tri et le <xref:System.Data.DataView>filtrage à. Cela entraîne le partage du tri et du filtrage sur toutes les vues de collection de la source de données. Pour permettre à chaque vue de collection de trier et filtrer indépendamment, initialisez chaque vue de collection <xref:System.Data.DataView> avec son propre objet.  
  
#### <a name="sorting"></a>Tri  
 Comme mentionné précédemment, les vues peuvent appliquer un ordre de tri à une collection. Comme cela existe dans la collection sous-jacente, vos données peuvent avoir ou non un ordre inhérent pertinent. La vue sur la collection vous permet d’imposer un ordre, ou de modifier l’ordre par défaut, en fonction de critères de comparaison que vous fournissez. Comme il s’agit d’une vue de données côté client, un scénario courant est que l’utilisateur peut souhaiter trier les colonnes des données tabulaires par la valeur à laquelle la colonne correspond. À l’aide de vues, ce tri défini par l’utilisateur peut être appliqué, à nouveau sans apporter de modifications à la collection sous-jacente ou même avoir à redemander le contenu de la collection. Pour un exemple, consultez [Trier une colonne GridView lors d'un clic sur un en-tête](../controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md).  
  
 L’exemple suivant illustre la logique de tri de la section «Trier par catégorie et <xref:System.Windows.Controls.CheckBox> date» de [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] l’application dans la section [qu’est-ce que la liaison de données?](#what_is_data_binding) :  
  
 [!code-csharp[DataBindingLab#8](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#8)]
 [!code-vb[DataBindingLab#8](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#8)]  
  
#### <a name="filtering"></a>Filtrage  
 Les vues peuvent également appliquer un filtre à une collection. Cela signifie que même si un élément peut exister dans la collection, cette vue particulière est destinée à afficher uniquement un sous-ensemble spécifique de la collection complète. Vous pouvez filtrer sur une condition dans les données. Par exemple, comme c’est le cas de l’application dans la section [qu’est-ce que la liaison de données?](#what_is_data_binding) , <xref:System.Windows.Controls.CheckBox> le «afficher uniquement les bonnes affaires» contient une logique pour filtrer les éléments qui coûtent $25 ou plus. Le code suivant est exécuté pour définir *ShowOnlyBargainsFilter* comme <xref:System.Windows.Data.CollectionViewSource.Filter> gestionnaire d’événements lorsque cette <xref:System.Windows.Controls.CheckBox> option est sélectionnée:  
  
 [!code-csharp[DataBindingLab#10](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#10)]
 [!code-vb[DataBindingLab#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#10)]  
  
 Le gestionnaire d’événements *ShowOnlyBargainsFilter* présente l’implémentation suivante :  
  
 [!code-csharp[DataBindingLab#5](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#5)]
 [!code-vb[DataBindingLab#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#5)]  
  
 Si vous utilisez l’une des <xref:System.Windows.Data.CollectionView> classes directement au lieu de <xref:System.Windows.Data.CollectionViewSource>, vous pouvez utiliser la <xref:System.Windows.Data.CollectionView.Filter%2A> propriété pour spécifier un rappel. Pour obtenir un exemple, consultez [Filtrer les données d'une vue](how-to-filter-data-in-a-view.md).  
  
#### <a name="grouping"></a>Regroupement  
 À l’exception de la classe interne qui <xref:System.Collections.IEnumerable> affiche une collection, toutes les vues de collection prennent en charge la fonctionnalité de regroupement, qui permet à l’utilisateur de partitionner la collection de la vue de collection en groupes logiques. Les groupes peuvent être explicites, si l’utilisateur fournit une liste de groupes, ou implicites, si les groupes sont générés dynamiquement en fonction des données.  
  
 L’exemple suivant illustre la logique de la «regrouper par <xref:System.Windows.Controls.CheckBox>catégorie»:  
  
 [!code-csharp[DataBindingLab#6](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#6)]
 [!code-vb[DataBindingLab#6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#6)]  
  
 Pour un autre exemple de groupement, consultez [Grouper des éléments dans un ListView implémentant un GridView](../controls/how-to-group-items-in-a-listview-that-implements-a-gridview.md).  
  
#### <a name="current-item-pointers"></a>Pointeurs d’élément actuel  
 Les vues prennent également en charge la notion d’élément actuel. Vous pouvez naviguer parmi les objets dans une vue de collection. Lorsque vous naviguez, vous déplacez un pointeur d’élément qui vous permet de récupérer l’objet qui existe à cet emplacement précis de la collection. Pour un exemple, consultez [Naviguer dans les objets d'un CollectionView de données](how-to-navigate-through-the-objects-in-a-data-collectionview.md).  
  
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
  
 Le pointeur d’élément actuel peut être affecté par tout tri ou filtrage appliqué à la collection. Le tri conserve le pointeur d’élément actuel sur le dernier élément sélectionné, mais la vue de collection est désormais restructurée autour du tri. (Par exemple, l’élément sélectionné était avant au début de la liste, mais il peut maintenant se trouver quelque part au milieu.) Le filtrage conserve l’élément sélectionné si cette sélection reste dans la vue après le filtrage. Sinon, le pointeur d’élément actuel est défini sur le premier élément de la vue de collection filtrée.  
  
<a name="master_detail_scenario"></a>   
#### <a name="master-detail-binding-scenario"></a>Scénario de liaison maître/détail  
 La notion d’un élément actuel est utile non seulement pour le parcours d’éléments dans une collection, mais également pour le scénario de liaison maître/détail. Considérez à nouveau l’application [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] dans la section [Qu’est-ce que la liaison de données ?](#what_is_data_binding). Dans cette application, la sélection dans le <xref:System.Windows.Controls.ListBox> détermine le contenu affiché dans le <xref:System.Windows.Controls.ContentControl>. Pour le placer d’une autre façon, lorsqu' <xref:System.Windows.Controls.ListBox> un élément est sélectionné, <xref:System.Windows.Controls.ContentControl> le affiche les détails de l’élément sélectionné.  
  
 Vous pouvez implémenter le scénario maître/détail simplement en ayant deux contrôles ou plus liés à la même vue. L’exemple suivant de la [démonstration](https://go.microsoft.com/fwlink/?LinkID=163703) de la liaison de données montre le <xref:System.Windows.Controls.ListBox> balisage <xref:System.Windows.Controls.ContentControl> du et du que vous [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] voyez sur l’application dans la section [qu’est-ce que la liaison de données?](#what_is_data_binding) :  
  
 [!code-xaml[DataBindingLab#Master1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#master1)]  
[!code-xaml[DataBindingLab#Master2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#master2)]  
[!code-xaml[DataBindingLab#Detail](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#detail)]  
  
 Notez que les deux contrôles sont liés à la même source, la ressource statique *listingDataView* (voir la définition de cette ressource dans [la section Guide de création d’une vue](#how_to_create_a_view)). Cela fonctionne parce que lorsqu’un objet singleton ( <xref:System.Windows.Controls.ContentControl> dans ce cas) est lié à une vue de collection, il est automatiquement lié à <xref:System.Windows.Data.CollectionView.CurrentItem%2A> l’de la vue. Notez que <xref:System.Windows.Data.CollectionViewSource> les objets synchronisent automatiquement la devise et la sélection. Si votre contrôle de liste n’est pas lié <xref:System.Windows.Data.CollectionViewSource> à un objet comme dans cet exemple, vous devez définir sa <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> propriété sur `true` pour que cela fonctionne.  
  
 Pour obtenir des exemples, consultez [Effectuer une liaison à une collection et afficher des informations basées sur la sélection](how-to-bind-to-a-collection-and-display-information-based-on-selection.md) et [Utiliser le modèle maître/détail avec des données hiérarchiques](how-to-use-the-master-detail-pattern-with-hierarchical-data.md).  
  
 Vous avez peut-être remarqué que l’exemple ci-dessus utilisait un modèle. En fait, les données ne sont pas affichées comme nous le souhaitons sans l’utilisation de modèles (celui utilisé explicitement par le <xref:System.Windows.Controls.ContentControl> et celui utilisé implicitement <xref:System.Windows.Controls.ListBox>par). Nous passons maintenant aux modèles de données dans la section suivante.  
  
<a name="data_templating"></a>   
## <a name="data-templating"></a>Modèles de données  
 Sans l’utilisation de modèles de données, notre application [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] dans la section [Qu’est-ce que la liaison de données ?](#what_is_data_binding) se présente comme suit :  
  
 ![Démo de liaison de données sans modèles de données](./media/data-binding-overview/data-binding-demo-templates.png)  
  
 Comme indiqué dans l’exemple de la section précédente, le <xref:System.Windows.Controls.ListBox> contrôle et le <xref:System.Windows.Controls.ContentControl> sont liés à l’objet de collection entier (ou plus spécifiquement, la vue sur l’objet de collection) d' *AuctionItem*s. Sans instructions spécifiques sur l’affichage de la collection de données, <xref:System.Windows.Controls.ListBox> le affiche une représentation sous forme de chaîne de chaque objet dans la collection <xref:System.Windows.Controls.ContentControl> sous-jacente et le affiche une représentation sous forme de chaîne de l’objet auquel il est lié.  
  
 Pour résoudre ce problème, l’application définit <xref:System.Windows.DataTemplate>s. Comme indiqué dans l’exemple de la section précédente, le <xref:System.Windows.Controls.ContentControl> utilise explicitement *detailsProductListingTemplate*<xref:System.Windows.DataTemplate>. Le <xref:System.Windows.Controls.ListBox> contrôle utilise implicitement les éléments <xref:System.Windows.DataTemplate> suivants lors de l’affichage des objets *AuctionItem* dans la collection:  
  
 [!code-xaml[DataBindingLab#AuctionItemDataTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#auctionitemdatatemplate)]  
  
 Avec l’utilisation de ces deux <xref:System.Windows.DataTemplate>, l’interface utilisateur obtenue est celle qui est indiquée dans la section [qu’est-ce que la liaison de données?](#what_is_data_binding) . Comme vous pouvez le voir dans cette capture d’écran, en plus de vous permettre de placer des <xref:System.Windows.DataTemplate>données dans vos contrôles, vous pouvez définir des visuels attrayants pour vos données. Par exemple, <xref:System.Windows.DataTrigger>les objets sont utilisés dans les <xref:System.Windows.DataTemplate> éléments ci-dessus *afin que les*s d’un reflet avec *la valeur de* mise en surbrillance de la valeur de *mise* en surbrillance apparaissent avec une bordure orange et une étoile.  
  
 Pour plus d’informations sur les modèles de données, consultez [Vue d’ensemble des modèles de données](data-templating-overview.md).  
  
<a name="data_validation"></a>   
## <a name="data-validation"></a>Validation de données  
  
 La plupart des applications qui acceptent l’entrée d’utilisateur doivent avoir une logique de validation pour vérifier que l’utilisateur a entré les informations attendues. Les contrôles de validation peuvent reposer sur un type, une plage, un format ou autres conditions requises spécifiques à l’application. Cette section traite du fonctionnement de la validation des données dans le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
### <a name="associating-validation-rules-with-a-binding"></a>Associer des règles de validation à une liaison  
 Le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] modèle de liaison de données vous permet <xref:System.Windows.Data.Binding.ValidationRules%2A> d’associer <xref:System.Windows.Data.Binding> à votre objet. Par exemple, l’exemple suivant lie <xref:System.Windows.Controls.TextBox> un à une propriété nommée `StartPrice` et ajoute un <xref:System.Windows.Controls.ExceptionValidationRule> objet à la <xref:System.Windows.Data.Binding.ValidationRules%2A?displayProperty=nameWithType> propriété.  
  
 [!code-xaml[DataBindingLab#DefaultValidation](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/AddProductWindow.xaml#defaultvalidation)]  
  
 Un <xref:System.Windows.Controls.ValidationRule> objet vérifie si la valeur d’une propriété est valide. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]contient les deux types d' <xref:System.Windows.Controls.ValidationRule> objets intégrés suivants:  
  
- <xref:System.Windows.Controls.ExceptionValidationRule> Recherche les exceptions levées pendant la mise à jour de la propriété de source de liaison. Dans l’exemple précédent, `StartPrice` est de type entier. Lorsque l’utilisateur entre une valeur qui ne peut pas être convertie en un entier, une exception est levée, ce qui marque la liaison comme étant non valide. Une autre <xref:System.Windows.Controls.ExceptionValidationRule> syntaxe pour définir explicitement est de définir la <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> propriété `true` sur sur votre <xref:System.Windows.Data.Binding> objet ou <xref:System.Windows.Data.MultiBinding> .  
  
- Un <xref:System.Windows.Controls.DataErrorValidationRule> objet recherche les erreurs déclenchées par les objets qui implémentent <xref:System.ComponentModel.IDataErrorInfo> l’interface. Pour obtenir un exemple d’utilisation de cette règle de <xref:System.Windows.Controls.DataErrorValidationRule>validation, consultez. Une autre <xref:System.Windows.Controls.DataErrorValidationRule> syntaxe pour définir explicitement est de définir la <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> propriété `true` sur sur votre <xref:System.Windows.Data.Binding> objet ou <xref:System.Windows.Data.MultiBinding> .  
  
 Vous pouvez également créer votre propre règle de validation en dérivant de la <xref:System.Windows.Controls.ValidationRule> classe et en implémentant la <xref:System.Windows.Controls.ValidationRule.Validate%2A> méthode. L’exemple suivant illustre la règle utilisée par la *liste ajouter un produit* «date de <xref:System.Windows.Controls.TextBox> début» de la section [qu’est-ce que la liaison de données?](#what_is_data_binding) :  
  
 [!code-csharp[DataBindingLab#2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/FutureDateRule.cs#2)]
 [!code-vb[DataBindingLab#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/FutureDateRule.vb#2)]  
  
 StartDateEntryForm<xref:System.Windows.Controls.TextBox> utilise ce *FutureDateRule*, comme illustré dans l’exemple suivant:  
  
 [!code-xaml[DataBindingLab#CustomValidation](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/AddProductWindow.xaml#customvalidation)]  
  
 Notez que, étant <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> donné que <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>la valeur est, le moteur de liaison met à jour la valeur source à chaque séquence de touches, ce qui signifie <xref:System.Windows.Data.Binding.ValidationRules%2A> qu’il vérifie également chaque règle de la collection à chaque séquence de touches. Nous reviendrons plus tard là-dessus dans la section Processus de validation.  
  
<a name="invalidation_feedback"></a>   
### <a name="providing-visual-feedback"></a>Fourniture de commentaires visuels  
 Si l’utilisateur entre une valeur non valide, vous souhaiterez peut-être fournir des commentaires sur l’erreur sur l’application [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Une façon de fournir ces commentaires consiste à définir la <xref:System.Windows.Controls.Validation.ErrorTemplate%2A?displayProperty=nameWithType> propriété jointe sur un <xref:System.Windows.Controls.ControlTemplate>personnalisé. Comme indiqué dans la sous-section précédente, *StartDateEntryForm* <xref:System.Windows.Controls.TextBox> utilise <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> un *validationTemplate*appelé. L’exemple suivant montre la définition de *validationTemplate* :  
  
 [!code-xaml[DataBindingLab#1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/AddProductWindow.xaml#1)]  
  
 L' <xref:System.Windows.Controls.AdornedElementPlaceholder> élément spécifie où le contrôle qui est orné doit être placé.  
  
 En outre, vous pouvez également utiliser un <xref:System.Windows.Controls.ToolTip> pour afficher le message d’erreur. *StartDateEntryForm* et *StartPriceEntryForm*<xref:System.Windows.Controls.TextBox>es utilisent le style *textStyleTextBox*, qui crée un qui affiche le <xref:System.Windows.Controls.ToolTip> message d’erreur. L’exemple suivant montre la définition de *textStyleTextBox*. La propriété <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jointe `true` est quand une ou plusieurs liaisons sur les propriétés de l’élément lié sont erronées.  
  
 [!code-xaml[DataBindingLab#14](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#14)]  
  
 Avec les <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> <xref:System.Windows.Controls.TextBox> et personnalisés, le StartDateEntryForm ressemble à ce qui suit lorsqu’il existe une erreur de validation:  <xref:System.Windows.Controls.ToolTip>  
  
 ![Erreur de validation de liaison de données](./media/databindingdemo-validation.PNG "DataBindingDemo_Validation")  
  
 Si votre <xref:System.Windows.Data.Binding> a des règles <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> de validation associées mais que vous ne spécifiez pas de sur le contrôle <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> lié, une valeur par défaut est utilisée pour avertir les utilisateurs en cas d’erreur de validation. La valeur <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> par défaut est un modèle de contrôle qui définit une bordure rouge dans la couche d’ornement. Avec la valeur <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> par défaut <xref:System.Windows.Controls.ToolTip>et, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] le de l' *StartPriceEntryForm* <xref:System.Windows.Controls.TextBox> ressemble à ce qui suit lorsqu’il existe une erreur de validation:  
  
 ![Erreur de validation de liaison de données](./media/databindingdemo-validationdefault.PNG "DataBindingDemo_ValidationDefault")  
  
 Pour obtenir un exemple montrant comment fournir une logique pour valider tous les contrôles dans une boîte de dialogue, consultez la section Boîtes de dialogue personnalisées dans [Vue d'ensemble des boîtes de dialogue](../app-development/dialog-boxes-overview.md).  
  
### <a name="validation-process"></a>Processus de validation  
 La validation se produit généralement lorsque la valeur d’une cible est transférée à la propriété de source de liaison. Cela se produit <xref:System.Windows.Data.BindingMode.TwoWay> sur <xref:System.Windows.Data.BindingMode.OneWayToSource> les liaisons et. Pour une réitération, ce qui provoque la mise à jour d’une source <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> dépend de la valeur de la propriété, comme décrit dans la section [qu’est-ce qui déclenche les mises à jour](#what_triggers_source_updates) de la source.  
  
 La section suivante décrit le processus de *validation*. Notez que si une erreur de validation ou un autre type d’erreur se produit à tout moment au cours de ce processus, le processus est interrompu.  
  
1. Le moteur de liaison vérifie s’il existe des <xref:System.Windows.Controls.ValidationRule> objets personnalisés <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> définis pour <xref:System.Windows.Controls.ValidationStep.RawProposedValue> lesquels a la valeur <xref:System.Windows.Data.Binding>pour ce, auquel cas il appelle <xref:System.Windows.Controls.ValidationRule.Validate%2A> la méthode sur <xref:System.Windows.Controls.ValidationRule> chacune d’elles jusqu’à ce que l’une d’entre elles s’exécute dans une erreur. ou jusqu’à ce qu’elles soient toutes passées.  
  
2. Le moteur de liaison appelle alors le convertisseur, s’il en existe un.  
  
3. Si le convertisseur est correctement exécuté, le moteur de liaison vérifie s’il existe <xref:System.Windows.Controls.ValidationRule> des objets personnalisés <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> définis dont a <xref:System.Windows.Controls.ValidationStep.ConvertedProposedValue> la valeur <xref:System.Windows.Data.Binding>pour ce, auquel cas il appelle <xref:System.Windows.Controls.ValidationRule.Validate%2A> la méthode sur <xref:System.Windows.Controls.ValidationRule> chaque qui a affectezlavaleurjusqu’àcequel’uned’elless’exécuteenerreuroujusqu’àcequ’ellessoienttoutespassées.<xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> <xref:System.Windows.Controls.ValidationStep.ConvertedProposedValue>  
  
4. Le moteur de liaison définit la propriété source.  
  
5. Le moteur de liaison vérifie s’il existe des <xref:System.Windows.Controls.ValidationRule> objets personnalisés <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> définis pour lesquels a <xref:System.Windows.Controls.ValidationStep.UpdatedValue> la valeur <xref:System.Windows.Data.Binding>pour ce, auquel cas il appelle <xref:System.Windows.Controls.ValidationRule.Validate%2A> la méthode sur <xref:System.Windows.Controls.ValidationRule> chaque dont <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> a affecté la valeur <xref:System.Windows.Controls.ValidationStep.UpdatedValue> jusqu’à ce que l’un d’eux s’exécute dans une erreur ou jusqu’à ce qu’ils soient tous réussis. Si un <xref:System.Windows.Controls.DataErrorValidationRule> est associé à une liaison <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> et que a <xref:System.Windows.Controls.DataErrorValidationRule> la valeur par défaut, <xref:System.Windows.Controls.ValidationStep.UpdatedValue>, est vérifié à ce stade. C’est également le moment où les liaisons qui ont la <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> `true` valeur sont vérifiées.  
  
6. Le moteur de liaison vérifie s’il existe des <xref:System.Windows.Controls.ValidationRule> objets personnalisés <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> définis pour lesquels a <xref:System.Windows.Controls.ValidationStep.CommittedValue> la valeur <xref:System.Windows.Data.Binding>pour ce, auquel cas il appelle <xref:System.Windows.Controls.ValidationRule.Validate%2A> la méthode sur <xref:System.Windows.Controls.ValidationRule> chaque dont <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> a affecté la valeur <xref:System.Windows.Controls.ValidationStep.CommittedValue> jusqu’à ce que l’un d’eux s’exécute dans une erreur ou jusqu’à ce qu’ils soient tous réussis.  
  
 Si un <xref:System.Windows.Controls.ValidationRule> ne passe pas à un moment donné dans le cadre de ce processus, le <xref:System.Windows.Controls.ValidationError> moteur de liaison crée un objet <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> et l’ajoute à la collection de l’élément lié. Avant que le moteur de liaison <xref:System.Windows.Controls.ValidationRule> n’exécute les objets à une étape donnée, <xref:System.Windows.Controls.ValidationError> il supprime tous ceux qui <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> ont été ajoutés à la propriété jointe de l’élément lié pendant cette étape. Par exemple, si a <xref:System.Windows.Controls.ValidationRule> <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> ayant la valeur <xref:System.Windows.Controls.ValidationStep.UpdatedValue> failed, la prochaine fois que le processus de validation se produit, le <xref:System.Windows.Controls.ValidationRule> moteur <xref:System.Windows.Controls.ValidationError> de liaison supprime immédiatement celui qui a <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> défini sur <xref:System.Windows.Controls.ValidationStep.UpdatedValue>.  
  
 Lorsque <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> n’est pas vide, <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> la propriété jointe de `true`l’élément a la valeur. En outre, si <xref:System.Windows.Data.Binding.NotifyOnValidationError%2A> la propriété <xref:System.Windows.Data.Binding> du a la valeur `true`, le moteur de liaison déclenche l' <xref:System.Windows.Controls.Validation.Error?displayProperty=nameWithType> événement attaché sur l’élément.  
  
 Notez également qu’un transfert de valeur valide dans l’une ou l’autre direction (cible vers source ou source vers <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> cible) efface la propriété jointe.  
  
 Si la liaison est associée à <xref:System.Windows.Controls.ExceptionValidationRule> une liaison ou si la propriété a <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> la valeur `true` et qu’une exception est levée lorsque le moteur de liaison définit la source, le moteur de liaison vérifie s’il existe un <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A>. Vous avez la possibilité d’utiliser le <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A> rappel pour fournir un gestionnaire personnalisé pour la gestion des exceptions. Si un <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A> n’est pas spécifié <xref:System.Windows.Data.Binding>sur, le moteur de liaison crée <xref:System.Windows.Controls.ValidationError> un avec l’exception et l’ajoute à <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> la collection de l’élément lié.  
  
## <a name="debugging-mechanism"></a>Mécanisme de débogage  
 Vous pouvez définir la propriété <xref:System.Diagnostics.PresentationTraceSources.TraceLevel%2A?displayProperty=nameWithType> jointe sur un objet lié à la liaison pour recevoir des informations sur l’état d’une liaison spécifique.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Controls.DataErrorValidationRule>
- [Nouveautés de WPF version 4.5](../getting-started/whats-new.md)
- [Effectuer une liaison avec les résultats d'une requête LINQ](how-to-bind-to-the-results-of-a-linq-query.md)
- [Liaison de données](../advanced/optimizing-performance-data-binding.md)
- [Démonstration de la liaison de données](https://go.microsoft.com/fwlink/?LinkID=163703)
- [Rubriques de guide pratique](data-binding-how-to-topics.md)
- [Effectuer une liaison à une source de données ADO.NET](how-to-bind-to-an-ado-net-data-source.md)
