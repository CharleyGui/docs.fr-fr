---
title: Nouveautés de WPF version 4.5
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Presentation Foundation [WPF], what's new
- WPF [WPF], what's new
ms.assetid: db086ae4-70bb-4862-95db-2eaca5216bc3
ms.openlocfilehash: 8eff8da7746047c450b2e23af63d43b13f3b970c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746918"
---
# <a name="whats-new-in-wpf-version-45"></a>Nouveautés de WPF version 4.5
<a name="introduction"></a>Cette rubrique contient des informations sur les fonctionnalités nouvelles et améliorées de [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] version 4,5.  
  
 Cette rubrique contient les sections suivantes :  
  
- [Contrôle de ruban](#ribbon_control)  
  
- [Amélioration des performances lors de l’affichage de grands jeux de données groupées](#grouped_virtualization)  
  
- [Nouvelles fonctionnalités destinées au VirtualizingPanel](#VirtualizingPanel)  
  
- [Liaison aux propriétés statiques](#static_properties)  
  
- [Accès aux collections sur les threads sans interface utilisateur](#xthread_access)  
  
- [Validation des données de façon synchrone et asynchrone](#INotifyDataErrorInfo)  
  
- [Mise à jour automatique de la source d’une liaison de données](#delay)  
  
- [Liaison aux types qui implémentent ICustomTypeProvider](#ICustomTypeProvider)  
  
- [Récupération des informations de liaison de données à partir d’une expression de liaison](#binding_state)  
  
- [Vérification d’un objet DataContext valide](#DisconnectedSource)  
  
- [Repositionnement des données au fur et à mesure du changement des valeurs des données (mise en forme active)](#live_shaping)  
  
- [Amélioration de la prise en charge pour l’établissement d’une référence faible à un événement](#weak_event_pattern)  
  
- [Nouvelles méthodes pour la classe Dispatcher](#async)  
  
- [Extensions de balisage pour les événements](#events_markup_extenions)  
  
<a name="ribbon_control"></a>   
## <a name="ribbon-control"></a>Contrôle de ruban  
 WPF 4,5 est fourni avec un contrôle de <xref:System.Windows.Controls.Ribbon.Ribbon> qui héberge une barre d’outils accès rapide, un menu d’application et des onglets.  Pour plus d’informations, consultez l’article [Vue d’ensemble du ruban](/visualstudio/vsto/ribbon-overview).  
  
<a name="grouped_virtualization"></a>   
## <a name="improved-performance-when-displaying-large-sets-of-grouped-data"></a>Amélioration des performances lors de l’affichage de grands jeux de données groupées  
 La virtualisation de l’interface utilisateur survient lorsqu’un sous-ensemble d’éléments d’interface utilisateur sont générés à partir d’un plus grand nombre d’éléments de données, selon les éléments visibles à l’écran. L' <xref:System.Windows.Controls.VirtualizingPanel> définit la propriété jointe <xref:System.Windows.Controls.VirtualizingPanel.IsVirtualizingWhenGrouping%2A> qui permet la virtualisation de l’interface utilisateur pour les données groupées.  Pour plus d’informations sur le regroupement de données, consultez Comment : trier et grouper des données à l’aide d’une vue en XAML.  Pour plus d’informations sur la virtualisation des données groupées, consultez la <xref:System.Windows.Controls.VirtualizingPanel.IsVirtualizingWhenGrouping%2A> propriété jointe.  
  
<a name="VirtualizingPanel"></a>   
## <a name="new-features-for-the-virtualizingpanel"></a>Nouvelles fonctionnalités destinées au VirtualizingPanel  
  
1. Vous pouvez spécifier si un <xref:System.Windows.Controls.VirtualizingPanel>, tel que le <xref:System.Windows.Controls.VirtualizingStackPanel>, affiche des éléments partiels à l’aide de la propriété jointe <xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A>. Si <xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A> est défini sur <xref:System.Windows.Controls.ScrollUnit.Item>, le <xref:System.Windows.Controls.VirtualizingPanel> affichera uniquement les éléments qui sont entièrement visibles. Si <xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A> est défini sur <xref:System.Windows.Controls.ScrollUnit.Pixel>, le <xref:System.Windows.Controls.VirtualizingPanel> peut afficher des éléments partiellement visibles.  
  
2. Vous pouvez spécifier la taille du cache avant et après la fenêtre d’affichage lorsque le <xref:System.Windows.Controls.VirtualizingPanel> est virtualisé à l’aide de la propriété jointe <xref:System.Windows.Controls.VirtualizingPanel.CacheLength%2A>.  Le cache est la quantité d’espace au-dessus ou au-dessous de la fenêtre d’affichage dans laquelle les éléments ne sont pas virtualisés.  L’utilisation d’un cache pour éviter de générer des éléments d’interface utilisateur à mesure qu’ils défilent peut améliorer les performances. Le cache est alimenté à un niveau de priorité inférieure afin que l’application ne cesse pas de répondre lors de l’opération. La propriété <xref:System.Windows.Controls.VirtualizingPanel.CacheLengthUnit%2A?displayProperty=nameWithType> détermine l’unité de mesure utilisée par <xref:System.Windows.Controls.VirtualizingPanel.CacheLength%2A?displayProperty=nameWithType>.  
  
<a name="static_properties"></a>   
## <a name="binding-to-static-properties"></a>Liaison aux propriétés statiques  
 Vous pouvez utiliser des propriétés statiques comme source d’une liaison de données. Le moteur de liaison de données reconnaît le changement de valeur d’une propriété lors du déclenchement d’un événement statique.  Par exemple, si la classe `SomeClass` définit une propriété statique appelée `MyProperty`, `SomeClass` peut définir un événement statique déclenché lorsque la valeur de `MyProperty` varie.  L’événement statique peut utiliser une des signatures suivantes.  
  
- `public static event EventHandler MyPropertyChanged;`  
  
- `public static event EventHandler<PropertyChangedEventArgs> StaticPropertyChanged;`  
  
 Notez que dans le premier cas, la classe expose un événement statique nommé *PropertyName*`Changed` qui transmet <xref:System.EventArgs> au gestionnaire d’événements.  Dans le deuxième cas, la classe expose un événement statique nommé `StaticPropertyChanged` qui passe <xref:System.ComponentModel.PropertyChangedEventArgs> au gestionnaire d’événements. Une classe qui implémente la propriété statique peut choisir de déclencher des notifications de modification de propriété à l’aide d’une des deux méthodes.  
  
<a name="xthread_access"></a>   
## <a name="accessing-collections-on-non-ui-threads"></a>Accès aux collections sur les threads sans interface utilisateur  
 WPF permet d’accéder et de modifier des collections de données sur des threads autres que celui qui a créé la collection.  Cela permet d’utiliser un thread d’arrière-plan pour recevoir des données provenant d’une source externe, comme une base de données et afficher les données sur le thread d’interface utilisateur.  En utilisant un autre thread pour modifier la collection, l’interface utilisateur reste réactive à une interaction utilisateur.  
  
<a name="INotifyDataErrorInfo"></a>   
## <a name="synchronously-and-asynchronously-validating-data"></a>Validation des données de façon synchrone et asynchrone  
 L’interface <xref:System.ComponentModel.INotifyDataErrorInfo> permet aux classes d’entité de données d’implémenter des règles de validation personnalisées et d’exposer les résultats de validation de manière asynchrone. Cette interface prend également en charge les objets d’erreur personnalisés, plusieurs erreurs par propriété, les erreurs d’inter-propriétés et les erreurs au niveau de l’entité.  Pour plus d'informations, consultez <xref:System.ComponentModel.INotifyDataErrorInfo>.  
  
<a name="delay"></a>   
## <a name="automatically-updating-the-source-of-a-data-binding"></a>Mise à jour automatique de la source d’une liaison de données  
 Si vous utilisez une liaison de données pour mettre à jour une source de données, vous pouvez utiliser la propriété <xref:System.Windows.Data.BindingBase.Delay%2A> pour spécifier une durée à passer après la modification de la propriété sur la cible avant la mise à jour de la source.  Par exemple, supposons que vous disposiez d’un <xref:System.Windows.Controls.Slider> dont les données de propriété <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> sont liées à une propriété d’un objet de données et que la propriété <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> est définie sur <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.  Dans cet exemple, lorsque l’utilisateur déplace le <xref:System.Windows.Controls.Slider>, la source est mise à jour pour chaque pixel que le <xref:System.Windows.Controls.Slider> déplace.  L’objet source a généralement besoin de la valeur du curseur uniquement lorsque le <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> du curseur cesse de changer.  Pour empêcher la mise à jour de la source trop souvent, utilisez <xref:System.Windows.Data.BindingBase.Delay%2A> pour spécifier que la source ne doit pas être mise à jour jusqu’à ce qu’un certain laps de temps s’écoule après l’arrêt du déplacement du curseur.  
  
<a name="ICustomTypeProvider"></a>   
## <a name="binding-to-types-that-implement-icustomtypeprovider"></a>Liaison aux types qui implémentent ICustomTypeProvider  
 WPF prend en charge la liaison de données aux objets qui implémentent <xref:System.Reflection.ICustomTypeProvider>, également appelés types personnalisés.  Vous pouvez utiliser des types personnalisés dans les cas suivants.  
  
1. En tant que <xref:System.Windows.PropertyPath> dans une liaison de données. Par exemple, la propriété <xref:System.Windows.Data.Binding.Path%2A> d’un <xref:System.Windows.Data.Binding> peut faire référence à une propriété d’un type personnalisé.  
  
2. Comme valeur de la propriété <xref:System.Windows.DataTemplate.DataType%2A>.  
  
3. En tant que type qui détermine les colonnes générées automatiquement dans un <xref:System.Windows.Controls.DataGrid>.  
  
<a name="binding_state"></a>   
## <a name="retrieving-data-binding-information-from-a-binding-expression"></a>Récupération des informations de liaison de données à partir d’une expression de liaison  
 Dans certains cas, vous pouvez obtenir le <xref:System.Windows.Data.BindingExpression> d’un <xref:System.Windows.Data.Binding> et besoin d’informations sur les objets source et cible de la liaison.  De nouvelles API ont été ajoutées pour vous permettre d’obtenir l’objet source ou cible ou la propriété associée.  Lorsque vous disposez d’un <xref:System.Windows.Data.BindingExpression>, utilisez les API suivantes pour obtenir des informations sur la cible et la source.  
  
|Pour trouver cette valeur de la liaison|Utilisez cette API|  
|---------------------------------------|------------------|  
|Objet cible|<xref:System.Windows.Data.BindingExpressionBase.Target%2A?displayProperty=nameWithType>|  
|Propriété cible|<xref:System.Windows.Data.BindingExpressionBase.TargetProperty%2A?displayProperty=nameWithType>|  
|Objet source|<xref:System.Windows.Data.BindingExpression.ResolvedSource%2A?displayProperty=nameWithType>|  
|Propriété source|<xref:System.Windows.Data.BindingExpression.ResolvedSourcePropertyName%2A?displayProperty=nameWithType>|  
|Indique si le <xref:System.Windows.Data.BindingExpression> appartient à un <xref:System.Windows.Data.BindingGroup>|<xref:System.Windows.Data.BindingExpressionBase.BindingGroup%2A?displayProperty=nameWithType>|  
|Propriétaire d’un <xref:System.Windows.Data.BindingGroup>|<xref:System.Windows.Data.BindingGroup.Owner%2A>|  
  
<a name="DisconnectedSource"></a>   
## <a name="checking-for-a-valid-datacontext-object"></a>Vérification d’un objet DataContext valide  
 Dans certains cas, la <xref:System.Windows.FrameworkElement.DataContext%2A> d’un conteneur d’éléments dans un <xref:System.Windows.Controls.ItemsControl> est déconnectée.  Un conteneur d’éléments est l’élément d’interface utilisateur qui affiche un élément dans un <xref:System.Windows.Controls.ItemsControl>.  Lorsqu’un <xref:System.Windows.Controls.ItemsControl> est lié aux données d’une collection, un conteneur d’éléments est généré pour chaque élément. Dans certains cas, les conteneurs d’éléments sont supprimés de l’arborescence d’éléments visuels. Dans les deux cas, un conteneur d’éléments est supprimé lorsqu’un élément est supprimé de la collection sous-jacente et lorsque la virtualisation est activée sur le <xref:System.Windows.Controls.ItemsControl>. Dans ces cas, la propriété <xref:System.Windows.FrameworkElement.DataContext%2A> du conteneur d’élément est définie sur l’objet Sentinel retourné par la propriété statique <xref:System.Windows.Data.BindingOperations.DisconnectedSource%2A?displayProperty=nameWithType>.  Vous devez vérifier si la <xref:System.Windows.FrameworkElement.DataContext%2A> est égale à l’objet <xref:System.Windows.Data.BindingOperations.DisconnectedSource%2A> avant d’accéder à la <xref:System.Windows.FrameworkElement.DataContext%2A> d’un conteneur d’éléments.  
  
<a name="live_shaping"></a>   
## <a name="repositioning-data-as-the-datas-values-change-live-shaping"></a>Repositionnement des données au fur et à mesure du changement des valeurs des données (mise en forme active)  
 Une collection de données peut être regroupée, triée ou filtrée. WPF 4.5 permet la réorganisation des données lorsque les données sont modifiées. Par exemple, supposons qu’une application utilise un <xref:System.Windows.Controls.DataGrid> pour répertorier les actions d’un marché boursier et les stocks sont triés par valeur boursière. Si le tri actif est activé sur la <xref:System.Windows.Data.CollectionView>des actions, la position d’un stock dans le <xref:System.Windows.Controls.DataGrid> se déplace lorsque la valeur du stock devient supérieure ou inférieure à la valeur d’une autre action.   Pour plus d’informations, consultez l’interface <xref:System.ComponentModel.ICollectionViewLiveShaping>.  
  
<a name="weak_event_pattern"></a>   
## <a name="improved-support-for-establishing-a-weak-reference-to-an-event"></a>Amélioration de la prise en charge pour l’établissement d’une référence faible à un événement  
 L’implémentation du modèle d’événement faible est désormais plus facile car les abonnés aux événements peuvent y participer sans avoir à implémenter d’interface supplémentaire.  La classe de <xref:System.Windows.WeakEventManager> générique permet également aux abonnés de participer au modèle d’événement faible si un <xref:System.Windows.WeakEventManager> dédié n’existe pas pour un certain événement.  Pour plus d’informations, consultez [Modèles d’événement faible](../advanced/weak-event-patterns.md).  
  
<a name="async"></a>   
## <a name="new-methods-for-the-dispatcher-class"></a>Nouvelles méthodes pour la classe Dispatcher  
 La classe Dispatcher définit de nouvelles méthodes pour les opérations synchrones et asynchrones.  La méthode <xref:System.Windows.Threading.Dispatcher.Invoke%2A> synchrone définit des surcharges qui prennent un paramètre <xref:System.Action> ou <xref:System.Func%601>. La nouvelle méthode asynchrone, <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A>, prend également un <xref:System.Action> ou <xref:System.Func%601> comme paramètre de rappel et retourne une <xref:System.Windows.Threading.DispatcherOperation> ou une <xref:System.Windows.Threading.DispatcherOperation%601>.   Les classes <xref:System.Windows.Threading.DispatcherOperation> et <xref:System.Windows.Threading.DispatcherOperation%601> définissent une propriété <xref:System.Threading.Tasks.Task>.  Lorsque vous appelez <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A>, vous pouvez utiliser le mot clé `await` avec le <xref:System.Windows.Threading.DispatcherOperation> ou le <xref:System.Threading.Tasks.Task>associé. Si vous devez attendre de façon synchrone le <xref:System.Threading.Tasks.Task> retourné par un <xref:System.Windows.Threading.DispatcherOperation> ou <xref:System.Windows.Threading.DispatcherOperation%601>, appelez la méthode d’extension <xref:System.Windows.Threading.TaskExtensions.DispatcherOperationWait%2A>. L’appel de <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> provoque un interblocage si l’opération est mise en file d’attente sur un thread appelant. Pour plus d’informations sur l’utilisation d’un <xref:System.Threading.Tasks.Task> pour effectuer des opérations asynchrones, consultez [parallélisme des tâches (bibliothèque parallèle de tâches)](../../../standard/parallel-programming/task-based-asynchronous-programming.md).  
  
<a name="events_markup_extenions"></a>   
## <a name="markup-extensions-for-events"></a>Extensions de balisage pour les événements  
 WPF 4.5 prend en charge les extensions de balisage pour les événements.  Bien que WPF ne définisse pas d’extension de balisage à utiliser pour les événements, des tiers sont en mesure de créer une extension de balisage qui peut être utilisée avec les événements.  
  
## <a name="see-also"></a>Voir aussi

- [Nouveautés dans le .NET Framework](../../whats-new/index.md)
