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
ms.openlocfilehash: 86178f3e49dc25bee57b0896f2ebc2cf729b69bd
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68238478"
---
# <a name="data-binding-overview"></a>Vue d’ensemble de la liaison de données
La liaison de données [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] offre un moyen simple et cohérent aux applications de présenter et d’interagir avec les données. Les éléments peuvent être liés à des données émanant de diverses sources de données sous la forme d’objets [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] et de [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)]. <xref:System.Windows.Controls.ContentControl>s comme <xref:System.Windows.Controls.Button> et <xref:System.Windows.Controls.ItemsControl>s comme <xref:System.Windows.Controls.ListBox> et <xref:System.Windows.Controls.ListView> possèdent des fonctionnalités intégrées permettant de style flexible des éléments de données uniques ou des collections d’éléments de données. Des vues de tri, filtrage et groupage peuvent être générées sur la base des données.  
  
 La fonctionnalité de liaison de données dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] présente plusieurs avantages par rapport aux modèles traditionnels, notamment une large gamme de propriétés qui prennent en charge par nature la liaison de données, une représentation [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] flexible des données et une séparation nette de la logique métier de [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
 Cette rubrique traite d’abord des concepts fondamentaux [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] liaison de données, puis traite ensuite de l’utilisation de la <xref:System.Windows.Data.Binding> classe et autres fonctionnalités de liaison de données.  

<a name="what_is_data_binding"></a>   
## <a name="what-is-data-binding"></a>Qu’est-ce que la liaison de données ?  
 La liaison de données est le processus qui établit une connexion entre [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] de l’application et logique métier. Si la liaison est correctement paramétrée et si les données fournissent les notifications appropriées, lorsque les données changent de valeur, les éléments qui sont liés aux données reflètent automatiquement ces changements. La liaison de données peut également signifier que si une représentation externe des données dans un élément change, les données sous-jacentes peuvent être automatiquement mises à jour pour refléter les modifications. Par exemple, si l’utilisateur modifie la valeur dans un <xref:System.Windows.Controls.TextBox> élément, la valeur de données sous-jacente est automatiquement mis à jour pour refléter cette modification.  
  
 Une utilisation typique de la liaison de données consiste à placer des données de configuration locale ou de serveur dans des formulaires ou d’autres contrôles [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], ce concept est développé pour inclure la liaison d’une large gamme de propriétés à diverses sources de données. Dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], les propriétés de dépendance d’éléments peuvent être liées à [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] objets (y compris les objets ADO.NET ou les objets associés aux Services Web et les propriétés Web) et [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] données.  
  
 Pour obtenir un exemple de liaison de données, examinons l’application [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] suivante de la [Démonstration de la liaison de données](https://go.microsoft.com/fwlink/?LinkID=163703) :  
  
 ![Capture d’écran de données liaison exemple](./media/databinding-databindingdemo.png "DataBinding_DataBindingDemo")  
  
 Ce qui précède est le [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] d’une application qui affiche une liste d’éléments de vente aux enchères. L’application illustre les fonctionnalités suivantes de la liaison de données :  
  
- Le contenu de la <xref:System.Windows.Controls.ListBox> est lié à une collection de *AuctionItem* objets. An objet *AuctionItem* a des propriétés telles que *Description*, *StartPrice*, *StartDate*, *Category*, *SpecialFeatures*, etc.  
  
- Les données (*AuctionItem* objets) affichées dans le <xref:System.Windows.Controls.ListBox> est basé sur un modèle afin que la description et le prix actuel soient affichés pour chaque élément. Cette opération est effectuée à l’aide un <xref:System.Windows.DataTemplate>. En outre, l’apparence de chaque élément varie selon la valeur de *SpecialFeatures* de *l’AuctionItem* affiché. Si la valeur *SpecialFeatures* de *AuctionItem* est *Color*, l’élément a une bordure bleue. Si la valeur est *Highlight*, l’élément a une bordure orange et une étoile. La section [Modèles de données](#data_templating) fournit des informations sur les modèles de données.  
  
- L’utilisateur peut grouper, filtrer ou trier les données à l’aide de la <xref:System.Windows.Controls.CheckBox>es fournis. Dans l’image ci-dessus, « Grouper par catégorie » et « Trier par catégorie et date » <xref:System.Windows.Controls.CheckBox>sont sélectionnés. Vous avez peut-être remarqué que les données sont regroupées en fonction de la catégorie de produit et que les noms de catégorie sont dans l’ordre alphabétique. Cela est difficile à observer sur l’image, mais les éléments sont également triés par date de début dans chaque catégorie. Cette opération est effectuée à l’aide d’une *vue de collection*. La section [Lier à des collections](#binding_to_collections) traite des vues de collection.  
  
- Lorsque l’utilisateur sélectionne un élément, le <xref:System.Windows.Controls.ContentControl> affiche les détails de l’élément sélectionné. Il s’agit du *Scénario maître/détail*. La section [Scénario maître/détail](#master_detail_scenario) fournit des informations sur ce type de scénario de liaison.  
  
- Le type de la *StartDate* propriété est <xref:System.DateTime>, qui retourne une date incluant l’heure à la milliseconde près. Dans cette application, un convertisseur personnalisé a été utilisé afin qu’une chaîne de date courte soit affichée. La section [Conversion de données](#data_conversion) fournit des informations sur les convertisseurs.  
  
 Lorsque l’utilisateur clique sur le bouton *Ajouter un produit*, le formulaire suivant s’affiche :  
  
 ![Page Ajouter la liste de produits](./media/databinding-demo-addproductlisting.png "DataBinding_Demo_AddProductListing")  
  
 L’utilisateur peut modifier les champs dans le formulaire, consulter la liste de produits à l’aide de l’aperçu court et des volets d’aperçu plus détaillés, puis cliquer sur *Envoyer* pour ajouter la nouvelle liste de produits. Tout regroupement, filtrage ou tri existant sera appliqué à la nouvelle entrée. Dans ce cas particulier, l’élément entré dans l’image ci-dessus s’affichera comme deuxième élément dans la catégorie *Computer*.  
  
 Ne pas illustré dans cette image est la logique de validation fournie dans le *Start Date* <xref:System.Windows.Controls.TextBox>. Si l’utilisateur entre un non valide date (mise en forme non valide ou une date passée), l’utilisateur sera notifié avec un <xref:System.Windows.Controls.ToolTip> et un point d’exclamation rouge à côté du <xref:System.Windows.Controls.TextBox>. La section [Validation des données](#data_validation) explique comment créer une logique de validation.  
  
 Avant d’aborder les différentes fonctionnalités de liaison de données décrites ci-dessus, nous couvrirons d’abord dans la section suivante les concepts fondamentaux qui sont critiques pour la compréhension de la liaison de données [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
## <a name="basic-data-binding-concepts"></a>Concepts de liaison de données de base  
  
 Quels que soient l’élément que vous liez et la nature de votre source de données, chaque liaison suit toujours le modèle illustré par l’illustration suivante :  
  
 ![Diagramme illustrant le modèle de liaison de données de base.](./media/data-binding-overview/basic-data-binding-diagram.png)  
  
 Comme présenté sur l’illustration ci-dessus, la liaison de données est essentiellement la passerelle entre votre cible de liaison et de votre source de liaison. L’illustration présente les concepts de liaison de données [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] essentiels suivants :  
  
- En général, chaque liaison possède ces quatre composants : un objet de cible de liaison, une propriété cible, une source de liaison et un chemin vers la valeur de la source de liaison à utiliser. Par exemple, si vous souhaitez lier le contenu d’un <xref:System.Windows.Controls.TextBox> à la *nom* propriété d’un *employé* de l’objet, votre objet cible est la <xref:System.Windows.Controls.TextBox>, la propriété cible est le <xref:System.Windows.Controls.TextBox.Text%2A> propriété, la valeur à utiliser est *nom*, et l’objet source est le *employé* objet.  
  
- La propriété cible doit être une propriété de dépendance. La plupart des <xref:System.Windows.UIElement> propriétés sont des propriétés de dépendance et la plupart des propriétés de dépendance, sauf celles qui sont en lecture seule, prennent en charge la liaison de données par défaut. (Uniquement <xref:System.Windows.DependencyObject> les types peuvent définir des propriétés de dépendance et tous les <xref:System.Windows.UIElement>s dérivent <xref:System.Windows.DependencyObject>.)  
  
- Bien que cela n’est pas spécifié sur l’illustration, il convient de noter que l’objet de source de liaison n’est pas limité à un objet [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] personnalisé. La liaison de données [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] prend en charge les données sous forme d’objets [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] et [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]. Pour fournir des exemples, votre source de liaison peut être un <xref:System.Windows.UIElement>, n’importe quel objet de liste, un [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] objet associé aux données ADO.NET ou des Services Web, ou un XmlNode qui contient votre [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] données. Pour plus d’informations, consultez [Vue d’ensemble de la liaison de ressources](binding-sources-overview.md).  
  
 Lorsque vous lisez les autres rubriques [!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)], il est important de vous rappeler que lorsque vous établissez une liaison, vous liez une cible de liaison *à* une source de liaison. Par exemple, si vous affichez des sous-jacent [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] les données dans un <xref:System.Windows.Controls.ListBox> à l’aide de la liaison de données, vous liez votre <xref:System.Windows.Controls.ListBox> à la [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] données.  
  
 Pour établir une liaison, vous utilisez le <xref:System.Windows.Data.Binding> objet. Le reste de cette rubrique traite de nombreux concepts associés et certaines des propriétés et l’utilisation de la <xref:System.Windows.Data.Binding> objet.  
  
<a name="direction_of_data_flow"></a>   
### <a name="direction-of-the-data-flow"></a>Direction du flux de données  
 Comme mentionné précédemment et comme indiqué par la flèche dans la figure ci-dessus, le flux de données d’une liaison peut devenir la cible de liaison à la source de liaison (par exemple, la valeur source change lorsqu’un utilisateur modifie la valeur d’un <xref:System.Windows.Controls.TextBox>) et/ou à partir de la source de liaison à la cible de liaison (par exemple, votre <xref:System.Windows.Controls.TextBox> contenu est mis à jour avec les modifications dans la source de liaison) si la source de liaison fournit les notifications appropriées.  
  
 Vous souhaiterez peut-être que votre application permette aux utilisateurs de modifier les données et les propager à nouveau vers l’objet source. Ou vous souhaitez peut-être ne pas permettre aux utilisateurs de mettre à jour la source de données. Vous pouvez contrôler ceci en définissant le <xref:System.Windows.Data.Binding.Mode%2A> propriété de votre <xref:System.Windows.Data.Binding> objet. L’exemple suivant illustre les différents types de flux de données :  
  
 ![Flux de données de liaison de données](./media/databinding-dataflow.png "DataBinding_DataFlow")  
  
- <xref:System.Windows.Data.BindingMode.OneWay> liaison de toute modification apportée à la propriété source pour automatiquement mettre à jour la propriété cible, mais les modifications apportées à la propriété cible ne sont pas propagées à la propriété source. Ce type de liaison est approprié si le contrôle lié est implicitement en lecture seule. Par exemple, vous pouvez lier à une source comme un affichage de cotations boursières, ou il se peut que votre propriété cible ne possède aucune interface de contrôle pour apporter des modifications, comme une couleur d’arrière-plan liée aux données d’une table. S’il n’est pas nécessaire de surveiller les modifications de la propriété cible, l’utilisation du mode de liaison <xref:System.Windows.Data.BindingMode.OneWay> permet d’éviter la surcharge du mode de liaison <xref:System.Windows.Data.BindingMode.TwoWay>.  
  
- <xref:System.Windows.Data.BindingMode.TwoWay> liaison de toute modification apportée à la propriété source ou la propriété cible pour mettre à jour automatiquement l’autre. Ce type de liaison convient aux formulaires modifiables ou à d’autres scénarios [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] entièrement interactifs. La plupart des propriétés par défaut <xref:System.Windows.Data.BindingMode.OneWay> liaison, mais certaines propriétés de dépendance (généralement des propriétés de contrôles modifiables par l’utilisateur tel que le <xref:System.Windows.Controls.TextBox.Text%2A> propriété de <xref:System.Windows.Controls.TextBox> et le <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> propriété de <xref:System.Windows.Controls.CheckBox>) par défaut pour <xref:System.Windows.Data.BindingMode.TwoWay> liaison. Un moyen de déterminer par programmation si une propriété de dépendance établit par défaut une liaison unidirectionnelle ou bidirectionnelle consiste à obtenir les métadonnées de la propriété à l’aide de <xref:System.Windows.DependencyProperty.GetMetadata%2A>, puis à vérifier la valeur booléenne de la propriété <xref:System.Windows.FrameworkPropertyMetadata.BindsTwoWayByDefault%2A>.  
  
- <xref:System.Windows.Data.BindingMode.OneWayToSource> est l’inverse du <xref:System.Windows.Data.BindingMode.OneWay> liaison ; il met à jour la propriété source lorsque la propriété cible change. Un exemple de scénario est si vous devez seulement réévaluer la valeur source à partir de [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
- Ne pas illustré dans la figure est <xref:System.Windows.Data.BindingMode.OneTime> de liaison, ce qui entraîne la propriété source initialiser la propriété cible, mais les modifications ultérieures apportées ne se propagent pas. Cela signifie que si le contexte de données subit une modification ou que l’objet dans le contexte des données change, la modification n'est pas répercutée dans la propriété cible. Ce type de liaison est approprié si vous utilisez des données réellement statiques ou qui se prêtent à l’utilisation d’un instantané de l’état actuel. Ce type de liaison est également utile si vous souhaitez initialiser votre propriété cible avec une valeur d’une propriété source et que le contexte de données n’est pas connu à l’avance. Il s’agit essentiellement d’une forme simplifiée de la liaison <xref:System.Windows.Data.BindingMode.OneWay> qui offre de meilleures performances dans les cas où la valeur source ne change pas.  
  
 Notez que pour détecter les modifications de source (applicables à <xref:System.Windows.Data.BindingMode.OneWay> et <xref:System.Windows.Data.BindingMode.TwoWay> liaisons), la source doit implémenter un mécanisme de notification de modification de propriété approprié tel que <xref:System.ComponentModel.INotifyPropertyChanged>. Consultez [Notification de modification de propriété implémenter](how-to-implement-property-change-notification.md) pour obtenir un exemple d’un <xref:System.ComponentModel.INotifyPropertyChanged> implémentation.  
  
 Le <xref:System.Windows.Data.Binding.Mode%2A> page de propriétés fournit plus d’informations sur les modes de liaison et un exemple montrant comment spécifier la direction d’une liaison.  
  
<a name="what_triggers_source_updates"></a>   
### <a name="what-triggers-source-updates"></a>Ce qui déclenche les mises à jour de la source  
 Les liaisons sont <xref:System.Windows.Data.BindingMode.TwoWay> ou <xref:System.Windows.Data.BindingMode.OneWayToSource> écoutent les modifications de la propriété cible et les propagent à la source. On appelle cela la mise à jour de la source. Par exemple, vous pouvez modifier le texte d’une zone de texte pour modifier la valeur source sous-jacente. Comme décrit dans la dernière section, la direction du flux de données est déterminée par la valeur de la <xref:System.Windows.Data.Binding.Mode%2A> propriété de la liaison.  
  
 Toutefois, est-ce que votre valeur source est mise à jour lorsque vous modifiez le texte ou après avoir fini de modifier le texte et pointé votre souris en dehors de la zone de texte ? Le <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> propriété de la liaison détermine ce qui déclenche la mise à jour de la source. Les points des flèches droites dans l’illustration suivante montrent le rôle de la <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> propriété :  
  
 ![Diagramme montrant le rôle de la propriété UpdateSourceTrigger.](./media/data-binding-overview/data-binding-updatesource-trigger.png)  
  
 Si le <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> valeur est <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>, puis la valeur vers laquelle pointe la flèche droite de <xref:System.Windows.Data.BindingMode.TwoWay> ou <xref:System.Windows.Data.BindingMode.OneWayToSource> liaisons est mis à jour dès que la propriété cible change. Toutefois, si le <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> valeur est <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>, puis cette valeur uniquement est mis à jour avec la nouvelle valeur lorsque la propriété cible perd le focus.  
  
 Similaire à la <xref:System.Windows.Data.Binding.Mode%2A> propriété, propriétés de dépendance ont par défaut différente <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> valeurs. La valeur par défaut de la plupart des propriétés de dépendance est <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>, tandis que celle de la propriété <xref:System.Windows.Controls.TextBox.Text%2A> a comme valeur par défaut <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>. Cela signifie que les mises à jour de la source se produisent habituellement chaque fois que la propriété cible change, ce qui est parfait pour <xref:System.Windows.Controls.CheckBox>es et autres contrôles simples. Toutefois, pour les champs de texte, la mise à jour après chaque frappe de clavier peut réduire les performances et empêche l’utilisateur de revenir en arrière pour corriger les fautes de frappe avant de valider la nouvelle valeur. C’est pourquoi le <xref:System.Windows.Controls.TextBox.Text%2A> propriété a la valeur par défaut <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus> au lieu de <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.  
  
 Consultez le <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> page de propriétés pour plus d’informations sur la recherche de la valeur par défaut <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> valeur d’une propriété de dépendance.  
  
 Le tableau suivant fournit un exemple de scénario pour chaque <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> valeur à l’aide de la <xref:System.Windows.Controls.TextBox> par exemple :  
  
|Valeur UpdateSourceTrigger|Quand la valeur source est mise à jour|Exemple de scénario pour TextBox|  
|-------------------------------|----------------------------------------|----------------------------------|  
|LostFocus (valeur par défaut pour <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType>)|Lorsque le contrôle TextBox perd le focus|Un <xref:System.Windows.Controls.TextBox> qui est associé à la logique de validation (voir la section de Validation des données)|  
|PropertyChanged|À mesure que vous tapez dans la <xref:System.Windows.Controls.TextBox>|<xref:System.Windows.Controls.TextBox> contrôles dans une fenêtre de salle de conversation|  
|Explicit|Lorsque l’application appelle <xref:System.Windows.Data.BindingExpression.UpdateSource%2A>|<xref:System.Windows.Controls.TextBox> contrôles dans un formulaire modifiable (met à jour les valeurs source uniquement lorsque l’utilisateur clique sur le bouton Envoyer)|  
  
 Pour un exemple, consultez [Contrôler quand le texte TextBox met à jour la source](how-to-control-when-the-textbox-text-updates-the-source.md).  
  
<a name="creating_a_binding"></a>   
## <a name="creating-a-binding"></a>Création d’une liaison  
  
 Pour récapituler quelques-uns des concepts étudiés dans les sections précédentes, vous établissez une liaison à l’aide de la <xref:System.Windows.Data.Binding> objet et généralement de chaque liaison possède quatre composants : liaison cible, la propriété cible, source de liaison et un chemin d’accès à la valeur de la source à utiliser. Cette section explique comment configurer une liaison.  
  
 Prenons l’exemple suivant, dans lequel l’objet de source de liaison est une classe nommée *MyData* qui est définie dans l’espace de noms *SDKSample*. À des fins de démonstration, la classe *MyData* a une propriété de chaîne nommée *ColorName*, dont la valeur est définie sur « Rouge ». Par conséquent, cet exemple génère un bouton avec un arrière-plan rouge.  
  
 [!code-xaml[BindNonTextProperty#1](~/samples/snippets/csharp/VS_Snippets_Wpf/BindNonTextProperty/CS/Page1.xaml#1)]  
  
 Pour plus d’informations sur la syntaxe de déclaration de liaison et pour obtenir des exemples montrant comment définir une liaison dans le code, consultez [Vue d'ensemble des déclarations de liaison](binding-declarations-overview.md).  
  
 Si nous appliquons cet exemple à notre diagramme de base, l’illustration qui en résulte ressemble à ce qui suit. Il s’agit d’un <xref:System.Windows.Data.BindingMode.OneWay> , car la propriété Background prend en charge la liaison <xref:System.Windows.Data.BindingMode.OneWay> liaison par défaut.  
  
 ![Diagramme illustrant la propriété d’arrière-plan de la liaison de données.](./media/data-binding-overview/data-binding-button-background-example.png)  
  
 Vous vous demanderez peut-être pourquoi cela fonctionne même si le *ColorName* propriété est de type chaîne alors que le <xref:System.Windows.Controls.Control.Background%2A> propriété est de type <xref:System.Windows.Media.Brush>. Il s’agit de la conversion de type par défaut en action, et nous l’évoquons dans la section [Conversion de données](#data_conversion).  
  
<a name="specifying_the_binding_source"></a>   
### <a name="specifying-the-binding-source"></a>Spécifier la source de liaison  
 Notez que dans l’exemple précédent, la source de liaison est spécifiée en définissant le <xref:System.Windows.FrameworkElement.DataContext%2A> propriété sur le <xref:System.Windows.Controls.DockPanel> élément. Le <xref:System.Windows.Controls.Button> hérite ensuite le <xref:System.Windows.FrameworkElement.DataContext%2A> valeur à partir de la <xref:System.Windows.Controls.DockPanel>, qui est son élément parent. Pour rappel, l’objet de source de liaison est un des quatre composants nécessaires d’une liaison. Par conséquent, sans objet de source de liaison spécifié, la liaison ne fait rien.  
  
 Il existe plusieurs façons de spécifier l’objet de source de liaison. À l’aide de la <xref:System.Windows.FrameworkElement.DataContext%2A> propriété sur un élément parent est utile lorsque vous liez plusieurs propriétés à la même source. Cependant, il peut parfois être plus approprié de spécifier la source de liaison sur des déclarations de liaison individuelles. Pour l’exemple précédent, au lieu d’utiliser le <xref:System.Windows.FrameworkElement.DataContext%2A> propriété, vous pouvez spécifier la source de liaison en définissant le <xref:System.Windows.Data.Binding.Source%2A> propriété directement sur la déclaration de liaison du bouton, comme dans l’exemple suivant :  
  
 [!code-xaml[BindNonTextProperty#BackgroundBindingCompact](~/samples/snippets/csharp/VS_Snippets_Wpf/BindNonTextProperty/CS/Page2.xaml#backgroundbindingcompact)]  
  
 Paramètre autre que le <xref:System.Windows.FrameworkElement.DataContext%2A> propriété sur un élément directement, héritant la <xref:System.Windows.FrameworkElement.DataContext%2A> valeur à partir d’un ancêtre (par exemple, le bouton dans le premier exemple) et en spécifiant explicitement la source de liaison en définissant le <xref:System.Windows.Data.Binding.Source%2A> propriété sur le <xref:System.Windows.Data.Binding> (par exemple, le bouton de l’exemple précédent), vous pouvez également utiliser le <xref:System.Windows.Data.Binding.ElementName%2A> propriété ou le <xref:System.Windows.Data.Binding.RelativeSource%2A> propriété pour spécifier la source de liaison. Le <xref:System.Windows.Data.Binding.ElementName%2A> propriété est utile lorsque vous liez à d’autres éléments dans votre application, comme lorsque vous utilisez un curseur pour ajuster la largeur d’un bouton. Le <xref:System.Windows.Data.Binding.RelativeSource%2A> propriété est utile lorsque la liaison est spécifiée dans un <xref:System.Windows.Controls.ControlTemplate> ou un <xref:System.Windows.Style>. Pour plus d’informations, consultez [Spécifier la source de liaison](how-to-specify-the-binding-source.md).  
  
<a name="specifying_the_path_to_the_value"></a>   
### <a name="specifying-the-path-to-the-value"></a>Spécification du chemin vers la valeur  
 Si votre source de liaison est un objet, vous utilisez le <xref:System.Windows.Data.Binding.Path%2A> propriété pour spécifier la valeur à utiliser pour votre liaison. Si vous liez à [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] données, que vous utilisez le <xref:System.Windows.Data.Binding.XPath%2A> propriété pour spécifier la valeur. Dans certains cas, il peut être nécessaire d’utiliser le <xref:System.Windows.Data.Binding.Path%2A> propriété même lorsque vos données sont [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]. Par exemple, si vous souhaitez accéder à la propriété de nom d’un XmlNode retourné (suite à une requête XPath), vous devez utiliser le <xref:System.Windows.Data.Binding.Path%2A> propriété outre le <xref:System.Windows.Data.Binding.XPath%2A> propriété.  
  
 Pour plus d’informations sur la syntaxe et des exemples, consultez le <xref:System.Windows.Data.Binding.Path%2A> et <xref:System.Windows.Data.Binding.XPath%2A> pages de propriétés.  
  
 Notez que bien que nous avons souligné que le <xref:System.Windows.Data.Binding.Path%2A> à la valeur à utiliser est un des quatre composants nécessaires d’une liaison, dans les scénarios où vous souhaitez lier à un objet entier, la valeur à utiliser est le même que l’objet de source de liaison. Dans ce cas, il convient de ne pas spécifier un <xref:System.Windows.Data.Binding.Path%2A>. Prenons l'exemple suivant :  
  
 [!code-xaml[MasterDetail#EmptyBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/MasterDetail/CSharp/Page1.xaml#emptybinding)]  
  
 L’exemple ci-dessus utilise la syntaxe de liaison vide : {Binding}. Dans ce cas, le <xref:System.Windows.Controls.ListBox> hérite du DataContext d’un élément de DockPanel parent (non illustré dans cet exemple). Lorsque le chemin d’accès n’est pas spécifié, le comportement par défaut consiste à lier à l’objet entier. En d’autres termes, dans cet exemple, le chemin d’accès a été omis parce que nous effectuons une liaison le <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> propriété à l’objet entier. (Voir la section [Lier à des collections](#binding_to_collections) pour une discussion détaillée.)  
  
 En plus de la liaison à une collection, ce scénario est utile lorsque vous souhaitez lier un objet entier plutôt qu’une seule propriété d’un objet. Par exemple, si votre objet source est simplement de type chaîne et que vous souhaitez lier la chaîne elle-même. Un autre scénario courant est lorsque vous souhaitez lier un élément à un objet avec plusieurs propriétés.  
  
 Notez que vous devrez peut-être appliquer une logique personnalisée afin que les données soient significatives pour votre propriété cible liée aux données. La logique personnalisée peut être sous la forme d’un convertisseur personnalisé (si la conversion de type par défaut n’existe pas). Consultez [Conversion de données](#data_conversion) pour plus d’informations sur les convertisseurs.  
  
<a name="binding_bindingexpression"></a>   
### <a name="binding-and-bindingexpression"></a>Binding et BindingExpression  
 Avant d’aborder d’autres fonctionnalités et utilisations de liaison de données, il serait utile d’introduire la <xref:System.Windows.Data.BindingExpression> classe. Comme vous l’avez vu dans les sections précédentes, le <xref:System.Windows.Data.Binding> classe est la classe de haut niveau pour la déclaration d’une liaison ; la <xref:System.Windows.Data.Binding> classe fournit de nombreuses propriétés qui vous permettent de spécifier les caractéristiques d’une liaison. Une classe connexe, <xref:System.Windows.Data.BindingExpression>, est l’objet sous-jacent qui gère la connexion entre la source et la cible. Une liaison contient toutes les informations qui peuvent être partagées entre plusieurs expressions de liaison. Un <xref:System.Windows.Data.BindingExpression> est une expression d’instance qui ne peut pas être partagée et contient toutes les informations d’instance de la <xref:System.Windows.Data.Binding>.  
  
 Par exemple, considérez la commande suivante, où *myDataObject* est une instance de *MyData* (classe), *myBinding* est la source <xref:System.Windows.Data.Binding> objet et *MyData* classe est une classe définie qui contient une propriété de chaîne nommée *MyDataProperty*. Cet exemple lie le contenu textuel de *mytext*, une instance de <xref:System.Windows.Controls.TextBlock>à *MyDataProperty*.  
  
 [!code-csharp[CodeOnlyBinding#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#1)]
 [!code-vb[CodeOnlyBinding#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#1)]  
  
 Vous pouvez utiliser le même objet *myBinding* pour créer d’autres liaisons. Par exemple, vous pouvez utiliser l’objet *myBinding* pour lier le contenu textuel d’une case à cocher à *MyDataProperty*. Dans ce scénario, il y aura deux instances de <xref:System.Windows.Data.BindingExpression> partage le *myBinding* objet.  
  
 Un <xref:System.Windows.Data.BindingExpression> objet peut être obtenu via la valeur de retour de l’appel <xref:System.Windows.Data.BindingOperations.GetBindingExpression%2A> sur un objet lié aux données. Les rubriques suivantes montrent quelques-unes des utilisations de la <xref:System.Windows.Data.BindingExpression> classe :  
  
- [Obtenir l'objet de liaison d'une propriété cible liée aux données](how-to-get-the-binding-object-from-a-bound-target-property.md)  
  
- [Contrôler quand le texte TextBox met à jour la source](how-to-control-when-the-textbox-text-updates-the-source.md)  
  
<a name="data_conversion"></a>   
## <a name="data-conversion"></a>Conversion de données  
 Dans l’exemple précédent, le bouton est rouge parce que son <xref:System.Windows.Controls.Control.Background%2A> propriété est liée à une propriété de chaîne avec la valeur « Rouge ». Cela fonctionne car un convertisseur de type est présent sur le <xref:System.Windows.Media.Brush> type vers lequel convertir la valeur de chaîne à un <xref:System.Windows.Media.Brush>.  
  
 Pour ajouter ces informations à l’illustration dans la section [Création d’une liaison](#creating_a_binding), le diagramme présente l’aspect suivant :  
  
 ![Diagramme illustrant la propriété par défaut de la liaison de données.](./media/data-binding-overview/data-binding-button-default-conversion.png)  
  
 Toutefois, que se passe-t-il si, au lieu d’avoir une propriété de type chaîne, votre objet de source de liaison a un *couleur* propriété de type <xref:System.Windows.Media.Color>? Dans ce cas, afin que la liaison fonctionne vous devrez premier tour le *couleur* valeur de propriété en quelque chose qui le <xref:System.Windows.Controls.Control.Background%2A> accepte de propriété. Vous devez créer un convertisseur personnalisé en implémentant le <xref:System.Windows.Data.IValueConverter> interface, comme dans l’exemple suivant :  
  
 [!code-csharp[ColorPicker_snip#16](~/samples/snippets/csharp/VS_Snippets_Wpf/ColorPicker_snip/CSharp/ColorPickerLib/ColorPicker.cs#16)]
 [!code-vb[ColorPicker_snip#16](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ColorPicker_snip/visualbasic/colorpickerlib/colorpicker.vb#16)]  
  
 Le <xref:System.Windows.Data.IValueConverter> page de référence fournit des informations supplémentaires.  
  
 Maintenant, le convertisseur personnalisé est utilisé au lieu de la conversion par défaut, et notre diagramme ressemble à ceci :  
  
 ![Diagramme illustrant le convertisseur personnalisé de liaison de données.](./media/data-binding-overview/data-binding-converter-color-example.png)  
  
 Pour rappel, des conversions par défaut peuvent être disponibles si des convertisseurs de type sont présents dans le type lié. Ce comportement dépendra des convertisseurs de type sont disponibles dans la cible. En cas de doute, créez votre propre convertisseur.  
  
 Voici quelques scénarios classiques où il est préférable d’implémenter un convertisseur de données :  
  
- Vos données devraient s’afficher différemment, selon la culture. Par exemple, vous souhaitez peut-être implémenter un convertisseur de devise ou un convertisseur de date/heure de calendrier en fonction des valeurs ou des normes utilisées dans une culture particulière.  
  
- Les données utilisées ne sont pas nécessairement destinées à modifier la valeur du texte d’une propriété, mais plutôt à modifier une autre valeur, comme la source d’une image ou la couleur ou le style du texte affiché. Les convertisseurs peuvent être utilisés ici en convertissant la liaison d’une propriété qui peut ne pas sembler appropriée, comme la liaison d’un champ de texte à la propriété Background d’une cellule de tableau.  
  
- Plusieurs contrôles ou propriétés de contrôles sont liés aux mêmes données. Dans ce cas, la liaison principale peut afficher uniquement le texte, tandis que les autres liaisons gèrent des problèmes d’affichage spécifiques, mais utilisent toujours la même liaison comme informations source.  
  
- Jusqu'à présent, nous n'avons pas encore traité <xref:System.Windows.Data.MultiBinding>, où une propriété cible possède une collection de liaisons. Dans le cas d’un <xref:System.Windows.Data.MultiBinding>, vous utilisez un <xref:System.Windows.Data.IMultiValueConverter> pour produire une valeur finale à partir des valeurs des liaisons. Par exemple, la couleur peut être calculée à partir des valeurs rouge, vert et bleu, qui peuvent être des valeurs à partir d’objets de source de liaison identiques ou différents. Consultez le <xref:System.Windows.Data.MultiBinding> page pour plus d’informations et des exemples de la classe.  
  
<a name="binding_to_collections"></a>   
## <a name="binding-to-collections"></a>Lier à des collections  
  
 Un objet de source de liaison peut être traité comme un objet unique dont les propriétés contiennent des données, ou comme une collection de données d’objets polymorphiques souvent regroupées ensemble (par exemple, le résultat d’une requête sur une base de données). Jusqu'à présent, nous avons seulement vu la liaison à des objets individuels, mais la liaison à une collection de données est un scénario courant. Par exemple, un scénario courant consiste à utiliser un <xref:System.Windows.Controls.ItemsControl> comme un <xref:System.Windows.Controls.ListBox>, <xref:System.Windows.Controls.ListView>, ou <xref:System.Windows.Controls.TreeView> pour afficher une collection de données, comme dans l’application représentée dans le [qu’est la liaison de données ?](#what_is_data_binding) section.  
  
 Heureusement, notre diagramme de base est toujours applicable. Si vous liez un <xref:System.Windows.Controls.ItemsControl> à une collection, le diagramme ressemble à ceci :  
  
 ![Diagramme qui affiche l’objet ItemsControl de liaison de données.](./media/data-binding-overview/data-binding-itemscontrol.png)  
  
 Comme illustré dans ce diagramme, pour lier un <xref:System.Windows.Controls.ItemsControl> à un objet de collection, <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> propriété est la propriété à utiliser. Vous pouvez considérer <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> propriété en tant que le contenu de la <xref:System.Windows.Controls.ItemsControl>. Notez que la liaison est <xref:System.Windows.Data.BindingMode.OneWay> , car le <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> prend en charge de la propriété <xref:System.Windows.Data.BindingMode.OneWay> liaison par défaut.  
  
<a name="how_to_implement_collections"></a>   
### <a name="how-to-implement-collections"></a>Guide d’implémentation des collections  
 Vous pouvez énumérer toute collection qui implémente le <xref:System.Collections.IEnumerable> interface. Toutefois, pour définir des liaisons dynamiques afin que les insertions ou les suppressions dans la collection de mettre à jour le [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] automatiquement, la collection doit implémenter le <xref:System.Collections.Specialized.INotifyCollectionChanged> interface. Cette interface expose un événement qui doit être déclenché chaque fois que la collection sous-jacente est modifiée.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit le <xref:System.Collections.ObjectModel.ObservableCollection%601> (classe), qui est une implémentation intégrée d’une collection de données qui expose le <xref:System.Collections.Specialized.INotifyCollectionChanged> interface. Notez que pour prendre en charge le transfert des valeurs de données à partir d’objets de source aux cibles, chaque objet dans votre collection qui prend en charge des propriétés pouvant être liées doit aussi implémenter le <xref:System.ComponentModel.INotifyPropertyChanged> interface. Pour plus d’informations, consultez [Vue d’ensemble de la liaison de ressources](binding-sources-overview.md).  
  
 Avant d’implémenter votre propre collection, envisagez d’utiliser <xref:System.Collections.ObjectModel.ObservableCollection%601> ou une des collections existantes classes, telles que <xref:System.Collections.Generic.List%601>, <xref:System.Collections.ObjectModel.Collection%601>, et <xref:System.ComponentModel.BindingList%601>, entre autres. Si vous avez un scénario avancé et que vous souhaitez implémenter votre propre collection, envisagez d’utiliser <xref:System.Collections.IList>, qui fournit une collection non générique d’objets accessibles séparément par index et assure donc les meilleures performances.  
  
<a name="collection_views"></a>   
### <a name="collection-views"></a>Vues de collection  
 Une fois votre <xref:System.Windows.Controls.ItemsControl> est lié à une collection de données, vous souhaiterez trier, filtrer ou regrouper les données. Pour ce faire, vous utilisez des vues de collection, qui sont des classes qui implémentent le <xref:System.ComponentModel.ICollectionView> interface.  

#### <a name="what-are-collection-views"></a>Que sont les vues de collection ?  
 Une vue de collection est une couche sur une collection de sources de liaison qui vous permet de parcourir et d’afficher la collection source sur la base de requêtes de tri, de filtrage et de groupage, sans avoir à modifier la collection source sous-jacente elle-même. Une vue de collection maintient également un pointeur vers l’élément actuel dans la collection. Si la collection source implémente le <xref:System.Collections.Specialized.INotifyCollectionChanged> interface, les modifications déclenchées par le <xref:System.Collections.Specialized.INotifyCollectionChanged.CollectionChanged> événement sont propagées aux vues.  
  
 Étant donné que les vues ne modifient pas les collections source sous-jacentes, chaque collection source peut avoir plusieurs vues associées. Par exemple, vous pouvez avoir une collection d’objets *Task*. À l’aide de vues, vous pouvez afficher ces mêmes données de différentes façons. Par exemple, sur le côté gauche de votre page, vous souhaitez peut-être afficher les tâches triées par priorité et, sur le côté droit, les regrouper par domaine.  
  
<a name="how_to_create_a_view"></a>   
#### <a name="how-to-create-a-view"></a>Guide de création d’une vue  
 Un moyen de créer et utiliser une vue consiste à instancier l’objet de vue directement et de l’utiliser comme source de liaison. Par exemple, considérez l’application [Démonstration de liaison de données](https://go.microsoft.com/fwlink/?LinkID=163703) présentée dans la section [Qu’est-ce que la liaison de données ?](#what_is_data_binding). L’application est implémentée telles que le <xref:System.Windows.Controls.ListBox> se lie à une vue directement au-dessus de la collecte de données au lieu de la collecte de données. L’exemple suivant est extrait de l’application [Démonstration de liaison de données](https://go.microsoft.com/fwlink/?LinkID=163703). Le <xref:System.Windows.Data.CollectionViewSource> classe est la [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] proxy d’une classe qui hérite de <xref:System.Windows.Data.CollectionView>. Dans cet exemple particulier, le <xref:System.Windows.Data.CollectionViewSource.Source%2A> de la vue est liée à la *AuctionItems* collection (de type <xref:System.Collections.ObjectModel.ObservableCollection%601>) de l’objet d’application actuel.  
  
 [!code-xaml[DataBindingLab#WindowResources1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#windowresources1)]  
[!code-xaml[DataBindingLab#CollectionViewSource](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#collectionviewsource)]  
[!code-xaml[DataBindingLab#WindowResources2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#windowresources2)]  
  
 La ressource *listingDataView* sert ensuite de la source de liaison pour les éléments dans l’application, telles que le <xref:System.Windows.Controls.ListBox>:  
  
 [!code-xaml[DataBindingLab#Master1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#master1)]  
[!code-xaml[DataBindingLab#Master2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#master2)]  
  
 Pour créer une autre vue pour la même collection, vous pouvez créer un autre <xref:System.Windows.Data.CollectionViewSource> de l’instance et lui donner un autre `x:Key` nom.  
  
 Le tableau suivant présente les types de données de vue sont créés comme vue de collection par défaut ou par <xref:System.Windows.Data.CollectionViewSource> en fonction du type de la collection source.  
  
|Type de collection source|Type de vue de collection|Notes|  
|----------------------------|--------------------------|-----------|  
|<xref:System.Collections.IEnumerable>|Un type interne basé sur <xref:System.Windows.Data.CollectionView>|Impossible de grouper les éléments.|  
|<xref:System.Collections.IList>|<xref:System.Windows.Data.ListCollectionView>|Le plus rapide.|  
|<xref:System.ComponentModel.IBindingList>|<xref:System.Windows.Data.BindingListCollectionView>||  
  
##### <a name="using-a-default-view"></a>Utilisation d’une vue par défaut  
 La spécification d’une vue de collection comme source de liaison est un moyen de créer et utiliser une vue de collection. WPF crée également une vue de collection par défaut pour chaque collection utilisée comme source de liaison. Si vous liez directement à une collection, WPF crée une liaison sur sa vue par défaut. Notez que cette vue par défaut est partagée par toutes les liaisons à la même collection, ainsi une modification apportée à une vue par défaut par un code ou contrôle lié (par exemple avec un tri ou une modification du pointeur d’élément actuel, dont nous parlons plus loin) se répercute dans toutes les autres liaisons à la même collection.  
  
 Pour obtenir la vue par défaut, vous utilisez le <xref:System.Windows.Data.CollectionViewSource.GetDefaultView%2A> (méthode). Pour un exemple, consultez [Obtenir la vue par défaut d'une collection de données](how-to-get-the-default-view-of-a-data-collection.md).  
  
##### <a name="collection-views-with-adonet-datatables"></a>Vues de collection avec ADO.NET DataTables  
 Pour améliorer les performances, les vues de collection pour ADO.NET <xref:System.Data.DataTable> ou <xref:System.Data.DataView> objets délèguent le tri et filtrage pour le <xref:System.Data.DataView>. Cela entraîne le partage du tri et du filtrage sur toutes les vues de collection de la source de données. Pour permettre à chaque vue de collection trier et filtrer indépendamment, initialisez chaque vue de collection avec son propre <xref:System.Data.DataView> objet.  
  
#### <a name="sorting"></a>Tri  
 Comme mentionné précédemment, les vues peuvent appliquer un ordre de tri à une collection. Comme cela existe dans la collection sous-jacente, vos données peuvent avoir ou non un ordre inhérent pertinent. La vue sur la collection vous permet d’imposer un ordre, ou de modifier l’ordre par défaut, en fonction de critères de comparaison que vous fournissez. Comme il s’agit d’une vue de données côté client, un scénario courant est que l’utilisateur peut souhaiter trier les colonnes des données tabulaires par la valeur à laquelle la colonne correspond. À l’aide de vues, ce tri défini par l’utilisateur peut être appliqué, à nouveau sans apporter de modifications à la collection sous-jacente ou même avoir à redemander le contenu de la collection. Pour un exemple, consultez [Trier une colonne GridView lors d'un clic sur un en-tête](../controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md).  
  
 L’exemple suivant illustre la logique de tri de la « trier par catégorie et date » <xref:System.Windows.Controls.CheckBox> de l’application [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] dans le [qu’est la liaison de données ?](#what_is_data_binding) section :  
  
 [!code-csharp[DataBindingLab#8](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#8)]
 [!code-vb[DataBindingLab#8](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#8)]  
  
#### <a name="filtering"></a>Filtrage  
 Les vues peuvent également appliquer un filtre à une collection. Cela signifie que même si un élément peut exister dans la collection, cette vue particulière est destinée à afficher uniquement un sous-ensemble spécifique de la collection complète. Vous pouvez filtrer sur une condition dans les données. Par exemple, comme le fait par l’application dans le [qu’est la liaison de données ?](#what_is_data_binding) section, « Afficher uniquement coûtant » <xref:System.Windows.Controls.CheckBox> contient la logique permettant de filtrer les articles coûtant 25 $ ou plus. Le code suivant est exécuté pour définir *ShowOnlyBargainsFilter* en tant que le <xref:System.Windows.Data.CollectionViewSource.Filter> Gestionnaire d’événements lorsque que <xref:System.Windows.Controls.CheckBox> est sélectionné :  
  
 [!code-csharp[DataBindingLab#10](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#10)]
 [!code-vb[DataBindingLab#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#10)]  
  
 Le gestionnaire d’événements *ShowOnlyBargainsFilter* présente l’implémentation suivante :  
  
 [!code-csharp[DataBindingLab#5](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#5)]
 [!code-vb[DataBindingLab#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#5)]  
  
 Si vous utilisez l’une de le <xref:System.Windows.Data.CollectionView> classes directement au lieu de <xref:System.Windows.Data.CollectionViewSource>, vous utiliseriez le <xref:System.Windows.Data.CollectionView.Filter%2A> propriété pour spécifier un rappel. Pour obtenir un exemple, consultez [Filtrer les données d'une vue](how-to-filter-data-in-a-view.md).  
  
#### <a name="grouping"></a>Regroupement  
 À l’exception de la classe interne qui affiche une <xref:System.Collections.IEnumerable> collection, toutes les vues de collection prennent en charge la fonctionnalité de regroupement, ce qui permet à l’utilisateur de partitionner la collection dans la vue de collection en groupes logiques. Les groupes peuvent être explicites, si l’utilisateur fournit une liste de groupes, ou implicites, si les groupes sont générés dynamiquement en fonction des données.  
  
 L’exemple suivant illustre la logique de « Grouper par catégorie » <xref:System.Windows.Controls.CheckBox>:  
  
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
 La notion d’un élément actuel est utile non seulement pour le parcours d’éléments dans une collection, mais également pour le scénario de liaison maître/détail. Considérez à nouveau l’application [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] dans la section [Qu’est-ce que la liaison de données ?](#what_is_data_binding). Dans cette application, la sélection dans le <xref:System.Windows.Controls.ListBox> détermine le contenu affiché dans le <xref:System.Windows.Controls.ContentControl>. Pour le placer dans une autre manière, quand un <xref:System.Windows.Controls.ListBox> élément est sélectionné, le <xref:System.Windows.Controls.ContentControl> affiche les détails de l’élément sélectionné.  
  
 Vous pouvez implémenter le scénario maître/détail simplement en ayant deux contrôles ou plus liés à la même vue. L’exemple suivant tiré le [démonstration de liaison de données](https://go.microsoft.com/fwlink/?LinkID=163703) affiche le balisage de la <xref:System.Windows.Controls.ListBox> et le <xref:System.Windows.Controls.ContentControl> vous voyez dans l’application [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] dans le [qu’est la liaison de données ?](#what_is_data_binding) section :  
  
 [!code-xaml[DataBindingLab#Master1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#master1)]  
[!code-xaml[DataBindingLab#Master2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#master2)]  
[!code-xaml[DataBindingLab#Detail](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#detail)]  
  
 Notez que les deux contrôles sont liés à la même source, la ressource statique *listingDataView* (voir la définition de cette ressource dans [la section Guide de création d’une vue](#how_to_create_a_view)). Cela fonctionne car lorsqu’un objet singleton (le <xref:System.Windows.Controls.ContentControl> dans ce cas) est lié à une vue de collection, il se lie automatiquement à la <xref:System.Windows.Data.CollectionView.CurrentItem%2A> de la vue. Notez que <xref:System.Windows.Data.CollectionViewSource> objets à synchroniser automatiquement la sélection et la devise. Si votre contrôle de liste n’est pas lié à un <xref:System.Windows.Data.CollectionViewSource> objet comme dans cet exemple, vous devez définir ses <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> propriété `true` pour ce faire.  
  
 Pour obtenir des exemples, consultez [Effectuer une liaison à une collection et afficher des informations basées sur la sélection](how-to-bind-to-a-collection-and-display-information-based-on-selection.md) et [Utiliser le modèle maître/détail avec des données hiérarchiques](how-to-use-the-master-detail-pattern-with-hierarchical-data.md).  
  
 Vous avez peut-être remarqué que l’exemple ci-dessus utilisait un modèle. En fait, les données ne seraient pas affichées comme nous le souhaitons sans l’utilisation de modèles (celui utilisé explicitement par le <xref:System.Windows.Controls.ContentControl> et celui utilisé implicitement par la <xref:System.Windows.Controls.ListBox>). Nous passons maintenant aux modèles de données dans la section suivante.  
  
<a name="data_templating"></a>   
## <a name="data-templating"></a>Modèles de données  
 Sans l’utilisation de modèles de données, notre application [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] dans la section [Qu’est-ce que la liaison de données ?](#what_is_data_binding) se présente comme suit :  
  
 ![Démo de liaison de données sans modèles de données](./media/data-binding-overview/data-binding-demo-templates.png)  
  
 Comme indiqué dans l’exemple dans la section précédente, à la fois le <xref:System.Windows.Controls.ListBox> contrôle et le <xref:System.Windows.Controls.ContentControl> sont liés à l’objet de collection entier (ou plus spécifiquement, la vue sur l’objet de collection) de *AuctionItem*s. Sans instructions spécifiques afficher la collecte de données, le <xref:System.Windows.Controls.ListBox> affiche une représentation de chaîne de chaque objet dans la collection sous-jacente et le <xref:System.Windows.Controls.ContentControl> affiche une représentation de chaîne de l’objet auquel il est lié.  
  
 Pour résoudre ce problème, l’application définit <xref:System.Windows.DataTemplate>s. Comme indiqué dans l’exemple dans la section précédente, le <xref:System.Windows.Controls.ContentControl> utilise explicitement le *detailsProductListingTemplate*<xref:System.Windows.DataTemplate>. Le <xref:System.Windows.Controls.ListBox> contrôle utilise implicitement les éléments suivants <xref:System.Windows.DataTemplate> lors de l’affichage le *AuctionItem* objets dans la collection :  
  
 [!code-xaml[DataBindingLab#AuctionItemDataTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#auctionitemdatatemplate)]  
  
 Avec l’utilisation de ces deux <xref:System.Windows.DataTemplate>s, l’interface utilisateur obtenue est celle représentée dans le [qu’est la liaison de données ?](#what_is_data_binding) section. Comme vous pouvez le voir dans cette capture d’écran, en plus de vous permettant de placer des données dans vos contrôles, <xref:System.Windows.DataTemplate>vous permettent de définir des éléments visuels agréables pour vos données. Par exemple, <xref:System.Windows.DataTrigger>s sont utilisés dans l’exemple ci-dessus <xref:System.Windows.DataTemplate> afin que *AuctionItem*s avec *SpecialFeatures* valeur *mettre en surbrillance* s’affichent avec un bordure orange et une étoile.  
  
 Pour plus d’informations sur les modèles de données, consultez [Vue d’ensemble des modèles de données](data-templating-overview.md).  
  
<a name="data_validation"></a>   
## <a name="data-validation"></a>Validation de données  
  
 La plupart des applications qui acceptent l’entrée d’utilisateur doivent avoir une logique de validation pour vérifier que l’utilisateur a entré les informations attendues. Les contrôles de validation peuvent reposer sur un type, une plage, un format ou autres conditions requises spécifiques à l’application. Cette section traite du fonctionnement de la validation des données dans le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
### <a name="associating-validation-rules-with-a-binding"></a>Associer des règles de validation à une liaison  
 Le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] modèle de liaison de données vous permet d’associer <xref:System.Windows.Data.Binding.ValidationRules%2A> avec votre <xref:System.Windows.Data.Binding> objet. Par exemple, l’exemple suivant lie un <xref:System.Windows.Controls.TextBox> à une propriété nommée `StartPrice` et ajoute un <xref:System.Windows.Controls.ExceptionValidationRule> de l’objet à le <xref:System.Windows.Data.Binding.ValidationRules%2A?displayProperty=nameWithType> propriété.  
  
 [!code-xaml[DataBindingLab#DefaultValidation](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/AddProductWindow.xaml#defaultvalidation)]  
  
 Un <xref:System.Windows.Controls.ValidationRule> objet vérifie si la valeur d’une propriété est valide. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a les deux types suivants d’intégré <xref:System.Windows.Controls.ValidationRule> objets :  
  
- Un <xref:System.Windows.Controls.ExceptionValidationRule> vérifie les exceptions levées pendant la mise à jour de la propriété de source de liaison. Dans l’exemple précédent, `StartPrice` est de type entier. Lorsque l’utilisateur entre une valeur qui ne peut pas être convertie en un entier, une exception est levée, ce qui marque la liaison comme étant non valide. Une autre syntaxe pour définir le <xref:System.Windows.Controls.ExceptionValidationRule> explicitement consiste à définir le <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> propriété `true` sur votre <xref:System.Windows.Data.Binding> ou <xref:System.Windows.Data.MultiBinding> objet.  
  
- Un <xref:System.Windows.Controls.DataErrorValidationRule> objet vérifie les erreurs déclenchées par les objets qui implémentent le <xref:System.ComponentModel.IDataErrorInfo> interface. Pour obtenir un exemple d’utilisation de cette règle de validation, consultez <xref:System.Windows.Controls.DataErrorValidationRule>. Une autre syntaxe pour définir le <xref:System.Windows.Controls.DataErrorValidationRule> explicitement consiste à définir le <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> propriété `true` sur votre <xref:System.Windows.Data.Binding> ou <xref:System.Windows.Data.MultiBinding> objet.  
  
 Vous pouvez également créer vos propres règles de validation en dérivant le <xref:System.Windows.Controls.ValidationRule> classe et implémenter la <xref:System.Windows.Controls.ValidationRule.Validate%2A> (méthode). L’exemple suivant montre la règle utilisée par le *ajouter une liste de produits* « Date de début » <xref:System.Windows.Controls.TextBox> à partir de la [qu’est la liaison de données ?](#what_is_data_binding) section :  
  
 [!code-csharp[DataBindingLab#2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/FutureDateRule.cs#2)]
 [!code-vb[DataBindingLab#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/FutureDateRule.vb#2)]  
  
 Le *StartDateEntryForm* <xref:System.Windows.Controls.TextBox> utilise cette *FutureDateRule*, comme illustré dans l’exemple suivant :  
  
 [!code-xaml[DataBindingLab#CustomValidation](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/AddProductWindow.xaml#customvalidation)]  
  
 Notez que, comme le <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> valeur est <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>, le moteur de liaison met à jour la valeur source après chaque frappe au clavier, ce qui signifie qu’il vérifie également chaque règle dans le <xref:System.Windows.Data.Binding.ValidationRules%2A> collecte sur chaque frappe au clavier. Nous reviendrons plus tard là-dessus dans la section Processus de validation.  
  
<a name="invalidation_feedback"></a>   
### <a name="providing-visual-feedback"></a>Fourniture de commentaires visuels  
 Si l’utilisateur entre une valeur non valide, vous souhaiterez peut-être fournir des commentaires sur l’erreur sur l’application [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Une façon de fournir de tels commentaires consiste à définir le <xref:System.Windows.Controls.Validation.ErrorTemplate%2A?displayProperty=nameWithType> propriété jointe sur personnalisé <xref:System.Windows.Controls.ControlTemplate>. Comme indiqué dans la section précédente, le *StartDateEntryForm* <xref:System.Windows.Controls.TextBox> utilise un <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> appelé *validationTemplate*. L’exemple suivant montre la définition de *validationTemplate* :  
  
 [!code-xaml[DataBindingLab#1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/AddProductWindow.xaml#1)]  
  
 Le <xref:System.Windows.Controls.AdornedElementPlaceholder> élément spécifie où le contrôle orné doit être placé.  
  
 En outre, vous pouvez également utiliser un <xref:System.Windows.Controls.ToolTip> pour afficher le message d’erreur. Les deux le *StartDateEntryForm* et le *StartPriceEntryForm*<xref:System.Windows.Controls.TextBox>es utilisent le style *textStyleTextBox*, ce qui crée un <xref:System.Windows.Controls.ToolTip> qui Affiche le message d’erreur. L’exemple suivant montre la définition de *textStyleTextBox*. La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` lorsqu’un ou plusieurs des liaisons sur les propriétés de l’élément lié sont dans l’erreur.  
  
 [!code-xaml[DataBindingLab#14](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#14)]  
  
 Avec personnalisé <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> et <xref:System.Windows.Controls.ToolTip>, le *StartDateEntryForm* <xref:System.Windows.Controls.TextBox> ressemble à ceci lorsqu’il existe une erreur de validation :  
  
 ![Erreur de validation de liaison de données](./media/databindingdemo-validation.PNG "DataBindingDemo_Validation")  
  
 Si votre <xref:System.Windows.Data.Binding> est associé à des règles de validation, mais vous ne spécifiez pas un <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> sur le contrôle lié, une valeur par défaut <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> sera utilisé pour informer les utilisateurs lorsqu’il existe une erreur de validation. La valeur par défaut <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> est un modèle de contrôle qui définit une bordure rouge dans la couche d’ornement. Avec la valeur par défaut <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> et <xref:System.Windows.Controls.ToolTip>, le [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] de la *StartPriceEntryForm* <xref:System.Windows.Controls.TextBox> ressemble à ceci lorsqu’il existe une erreur de validation :  
  
 ![Erreur de validation de liaison de données](./media/databindingdemo-validationdefault.PNG "DataBindingDemo_ValidationDefault")  
  
 Pour obtenir un exemple montrant comment fournir une logique pour valider tous les contrôles dans une boîte de dialogue, consultez la section Boîtes de dialogue personnalisées dans [Vue d'ensemble des boîtes de dialogue](../app-development/dialog-boxes-overview.md).  
  
### <a name="validation-process"></a>Processus de validation  
 La validation se produit généralement lorsque la valeur d’une cible est transférée à la propriété de source de liaison. Cela se produit sur <xref:System.Windows.Data.BindingMode.TwoWay> et <xref:System.Windows.Data.BindingMode.OneWayToSource> liaisons. Pour rappel, ce qui entraîne une mise à jour de la source dépend de la valeur de la <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> propriété, comme décrit dans la [les déclencheurs les mises à jour de la Source](#what_triggers_source_updates) section.  
  
 La section suivante décrit le processus de *validation*. Notez que si une erreur de validation ou un autre type d’erreur se produit à tout moment au cours de ce processus, le processus est interrompu.  
  
1. Le moteur de liaison vérifie s’il existe toute personnalisé <xref:System.Windows.Controls.ValidationRule> objets définis dont la propriété <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> a la valeur <xref:System.Windows.Controls.ValidationStep.RawProposedValue> pour qui <xref:System.Windows.Data.Binding>, auquel cas il appelle la <xref:System.Windows.Controls.ValidationRule.Validate%2A> méthode sur chaque <xref:System.Windows.Controls.ValidationRule> jusqu'à ce qu’un d’eux rencontre une erreur ou jusqu'à ce que toutes passent.  
  
2. Le moteur de liaison appelle alors le convertisseur, s’il en existe un.  
  
3. Si le convertisseur réussit, le moteur de liaison vérifie s’il existe toute personnalisé <xref:System.Windows.Controls.ValidationRule> objets définis dont la propriété <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> a la valeur <xref:System.Windows.Controls.ValidationStep.ConvertedProposedValue> pour qui <xref:System.Windows.Data.Binding>, auquel cas il appelle la <xref:System.Windows.Controls.ValidationRule.Validate%2A> méthode sur chaque <xref:System.Windows.Controls.ValidationRule> qui a <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> défini sur <xref:System.Windows.Controls.ValidationStep.ConvertedProposedValue> jusqu'à ce qu’un d’eux rencontre une erreur ou jusqu'à ce que toutes passent.  
  
4. Le moteur de liaison définit la propriété source.  
  
5. Le moteur de liaison vérifie s’il existe toute personnalisé <xref:System.Windows.Controls.ValidationRule> objets définis dont la propriété <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> a la valeur <xref:System.Windows.Controls.ValidationStep.UpdatedValue> pour qui <xref:System.Windows.Data.Binding>, auquel cas il appelle la <xref:System.Windows.Controls.ValidationRule.Validate%2A> méthode sur chaque <xref:System.Windows.Controls.ValidationRule> qui a <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> défini sur <xref:System.Windows.Controls.ValidationStep.UpdatedValue> jusqu'à ce qu’un d’eux rencontre une erreur ou jusqu'à ce que toutes passent. Si un <xref:System.Windows.Controls.DataErrorValidationRule> est associé à une liaison et son <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> est la valeur par défaut, <xref:System.Windows.Controls.ValidationStep.UpdatedValue>, le <xref:System.Windows.Controls.DataErrorValidationRule> est vérifiée à ce stade. Il s’agit également du point lorsque liaisons qui ont le <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> la valeur `true` sont vérifiées.  
  
6. Le moteur de liaison vérifie s’il existe toute personnalisé <xref:System.Windows.Controls.ValidationRule> objets définis dont la propriété <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> a la valeur <xref:System.Windows.Controls.ValidationStep.CommittedValue> pour qui <xref:System.Windows.Data.Binding>, auquel cas il appelle la <xref:System.Windows.Controls.ValidationRule.Validate%2A> méthode sur chaque <xref:System.Windows.Controls.ValidationRule> qui a <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> défini sur <xref:System.Windows.Controls.ValidationStep.CommittedValue> jusqu'à ce qu’un d’eux rencontre une erreur ou jusqu'à ce que toutes passent.  
  
 Si un <xref:System.Windows.Controls.ValidationRule> ne passe pas à tout moment tout au long de ce processus, le moteur de liaison crée un <xref:System.Windows.Controls.ValidationError> de l’objet et l’ajoute à la <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> collection de l’élément lié. Avant la liaison moteur exécute le <xref:System.Windows.Controls.ValidationRule> objets à un moment donné, il supprime toute <xref:System.Windows.Controls.ValidationError> qui a été ajouté à la <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> propriété jointe de l’élément lié au cours de cette étape. Par exemple, si un <xref:System.Windows.Controls.ValidationRule> dont <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> a la valeur <xref:System.Windows.Controls.ValidationStep.UpdatedValue> a échoué, la prochaine fois que le processus de validation se produit, le moteur de liaison supprime ce <xref:System.Windows.Controls.ValidationError> immédiatement avant d’appeler toute <xref:System.Windows.Controls.ValidationRule> qui a <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> défini sur <xref:System.Windows.Controls.ValidationStep.UpdatedValue>.  
  
 Lorsque <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> n’est pas vide, le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> a la valeur de propriété jointe de l’élément `true`. En outre, si le <xref:System.Windows.Data.Binding.NotifyOnValidationError%2A> propriété de la <xref:System.Windows.Data.Binding> a la valeur `true`, le moteur de liaison déclenche le <xref:System.Windows.Controls.Validation.Error?displayProperty=nameWithType> joint des événements sur l’élément.  
  
 Notez également qu’un transfert de valeur valide dans les deux directions (cible vers source ou source vers cible) efface le <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> propriété jointe.  
  
 Si la liaison est un <xref:System.Windows.Controls.ExceptionValidationRule> associée ou avait la <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> propriété est définie sur `true` et une exception est levée lorsque le moteur de liaison définit la source, le moteur de liaison vérifie s’il existe un <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A>. Vous avez la possibilité d’utiliser le <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A> rappel à fournir un gestionnaire personnalisé pour gérer les exceptions. Si un <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A> n’est pas spécifié sur le <xref:System.Windows.Data.Binding>, le moteur de liaison crée un <xref:System.Windows.Controls.ValidationError> avec l’exception et l’ajoute à la <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> collection de l’élément lié.  
  
## <a name="debugging-mechanism"></a>Mécanisme de débogage  
 Vous pouvez définir la propriété jointe <xref:System.Diagnostics.PresentationTraceSources.TraceLevel%2A?displayProperty=nameWithType> sur un objet lié à la liaison pour recevoir des informations sur l’état d’une liaison spécifique.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Controls.DataErrorValidationRule>
- [Nouveautés de WPF version 4.5](../getting-started/whats-new.md)
- [Effectuer une liaison avec les résultats d'une requête LINQ](how-to-bind-to-the-results-of-a-linq-query.md)
- [Liaison de données](../advanced/optimizing-performance-data-binding.md)
- [Démonstration de liaison de données](https://go.microsoft.com/fwlink/?LinkID=163703)
- [Rubriques de guide pratique](data-binding-how-to-topics.md)
- [Effectuer une liaison à une source de données ADO.NET](how-to-bind-to-an-ado-net-data-source.md)
