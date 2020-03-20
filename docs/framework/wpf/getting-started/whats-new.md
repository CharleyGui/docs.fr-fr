---
title: Nouveautés de WPF version 4.5
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Presentation Foundation [WPF], what's new
- WPF [WPF], what's new
ms.assetid: db086ae4-70bb-4862-95db-2eaca5216bc3
ms.openlocfilehash: 708b2fc231bfe7a9bc1f52872a0ec41c91931f26
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174704"
---
# <a name="whats-new-in-wpf-version-45"></a>Nouveautés de WPF version 4.5
<a name="introduction"></a>Ce sujet contient des informations [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] sur les fonctionnalités nouvelles et améliorées dans la version 4.5.  
  
 Cette rubrique contient les sections suivantes :  
  
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
 WPF 4.5 navires <xref:System.Windows.Controls.Ribbon.Ribbon> avec un contrôle qui héberge une barre d’outils d’accès rapide, menu d’application, et onglets.  Pour plus d’informations, consultez l’article [Vue d’ensemble du ruban](/visualstudio/vsto/ribbon-overview).  
  
<a name="grouped_virtualization"></a>
## <a name="improved-performance-when-displaying-large-sets-of-grouped-data"></a>Amélioration des performances lors de l’affichage de grands jeux de données groupées  
 La virtualisation de l’interface utilisateur survient lorsqu’un sous-ensemble d’éléments d’interface utilisateur sont générés à partir d’un plus grand nombre d’éléments de données, selon les éléments visibles à l’écran. Le <xref:System.Windows.Controls.VirtualizingPanel> définit <xref:System.Windows.Controls.VirtualizingPanel.IsVirtualizingWhenGrouping%2A> la propriété ci-jointe qui permet la virtualisation de l’interface utilisateur pour les données groupées.  Pour plus d’informations sur le regroupement de données, consultez Comment : trier et grouper des données à l’aide d’une vue en XAML.  Pour plus d’informations sur la <xref:System.Windows.Controls.VirtualizingPanel.IsVirtualizingWhenGrouping%2A> virtualisation des données groupées, voir la propriété ci-jointe.  
  
<a name="VirtualizingPanel"></a>
## <a name="new-features-for-the-virtualizingpanel"></a>Nouvelles fonctionnalités destinées au VirtualizingPanel  
  
1. Vous pouvez spécifier si un <xref:System.Windows.Controls.VirtualizingPanel>, comme le <xref:System.Windows.Controls.VirtualizingStackPanel>, affiche des éléments partiels en utilisant la <xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A> propriété ci-jointe. Si <xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A> elle <xref:System.Windows.Controls.ScrollUnit.Item>est <xref:System.Windows.Controls.VirtualizingPanel> configuré, la volonté n’affiche que les éléments qui sont complètement visibles. Si <xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A> elle <xref:System.Windows.Controls.ScrollUnit.Pixel>est <xref:System.Windows.Controls.VirtualizingPanel> configuré, la boîte peut afficher des éléments partiellement visibles.  
  
2. Vous pouvez spécifier la taille du cache <xref:System.Windows.Controls.VirtualizingPanel> avant et après <xref:System.Windows.Controls.VirtualizingPanel.CacheLength%2A> le viewport lorsque le viseur en utilisant la propriété ci-jointe.  Le cache est la quantité d’espace au-dessus ou au-dessous de la fenêtre d’affichage dans laquelle les éléments ne sont pas virtualisés.  L’utilisation d’un cache pour éviter de générer des éléments d’interface utilisateur à mesure qu’ils défilent peut améliorer les performances. Le cache est alimenté à un niveau de priorité inférieure afin que l’application ne cesse pas de répondre lors de l’opération. La <xref:System.Windows.Controls.VirtualizingPanel.CacheLengthUnit%2A?displayProperty=nameWithType> propriété détermine l’unité de <xref:System.Windows.Controls.VirtualizingPanel.CacheLength%2A?displayProperty=nameWithType>mesure qui est utilisée par .  
  
<a name="static_properties"></a>
## <a name="binding-to-static-properties"></a>Liaison aux propriétés statiques  
 Vous pouvez utiliser des propriétés statiques comme source d’une liaison de données. Le moteur de liaison de données reconnaît le changement de valeur d’une propriété lors du déclenchement d’un événement statique.  Par exemple, si la classe `SomeClass` définit une propriété statique appelée `MyProperty`, `SomeClass` peut définir un événement statique déclenché lorsque la valeur de `MyProperty` varie.  L’événement statique peut utiliser une des signatures suivantes.  
  
- `public static event EventHandler MyPropertyChanged;`  
  
- `public static event EventHandler<PropertyChangedEventArgs> StaticPropertyChanged;`  
  
 Notez que dans le premier cas, la classe expose <xref:System.EventArgs> un événement statique nommé *PropertyName* `Changed` qui passe au gestionnaire de l’événement.  Dans le deuxième cas, la classe `StaticPropertyChanged` expose <xref:System.ComponentModel.PropertyChangedEventArgs> un événement statique nommé qui passe au gestionnaire de l’événement. Une classe qui implémente la propriété statique peut choisir de déclencher des notifications de modification de propriété à l’aide d’une des deux méthodes.  
  
<a name="xthread_access"></a>
## <a name="accessing-collections-on-non-ui-threads"></a>Accès aux collections sur les threads sans interface utilisateur  
 WPF permet d’accéder et de modifier des collections de données sur des threads autres que celui qui a créé la collection.  Cela permet d’utiliser un thread d’arrière-plan pour recevoir des données provenant d’une source externe, comme une base de données et afficher les données sur le thread d’interface utilisateur.  En utilisant un autre thread pour modifier la collection, l’interface utilisateur reste réactive à une interaction utilisateur.  
  
<a name="INotifyDataErrorInfo"></a>
## <a name="synchronously-and-asynchronously-validating-data"></a>Validation des données de façon synchrone et asynchrone  
 L’interface <xref:System.ComponentModel.INotifyDataErrorInfo> permet aux classes d’entités de données de mettre en œuvre des règles de validation personnalisées et d’exposer les résultats de validation asynchronement. Cette interface prend également en charge les objets d’erreur personnalisés, plusieurs erreurs par propriété, les erreurs d’inter-propriétés et les erreurs au niveau de l’entité.  Pour plus d’informations, consultez <xref:System.ComponentModel.INotifyDataErrorInfo>.  
  
<a name="delay"></a>
## <a name="automatically-updating-the-source-of-a-data-binding"></a>Mise à jour automatique de la source d’une liaison de données  
 Si vous utilisez une liaison de données pour <xref:System.Windows.Data.BindingBase.Delay%2A> mettre à jour une source de données, vous pouvez utiliser la propriété pour spécifier un certain temps pour passer après les changements de propriété sur la cible avant que la source ne s’actualise.  Supposons, par exemple, <xref:System.Windows.Controls.Slider> que <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> vous avez un qui a ses données de <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> propriété dans <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>les deux sens liés à une propriété d’un objet de données et la propriété est définie à .  Dans cet exemple, lorsque <xref:System.Windows.Controls.Slider>l’utilisateur déplace le , <xref:System.Windows.Controls.Slider> la source met à jour pour chaque pixel que les mouvements.  L’objet source n’a généralement besoin de la <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> valeur du curseur que lorsque le curseur cesse de changer.  Pour éviter de mettre à <xref:System.Windows.Data.BindingBase.Delay%2A> jour la source trop souvent, utilisez pour spécifier que la source ne doit pas être mise à jour jusqu’à ce qu’une certaine quantité de temps s’écoule après que le pouce cesse de bouger.  
  
<a name="ICustomTypeProvider"></a>
## <a name="binding-to-types-that-implement-icustomtypeprovider"></a>Liaison aux types qui implémentent ICustomTypeProvider  
 WPF prend en charge <xref:System.Reflection.ICustomTypeProvider>la liaison de données aux objets qui implémentent , également connu sous le nom de types personnalisés.  Vous pouvez utiliser des types personnalisés dans les cas suivants.  
  
1. Comme <xref:System.Windows.PropertyPath> un dans une liaison de données. Par exemple, <xref:System.Windows.Data.Binding.Path%2A> la <xref:System.Windows.Data.Binding> propriété d’un peut faire référence à une propriété d’un type personnalisé.  
  
2. Comme la valeur <xref:System.Windows.DataTemplate.DataType%2A> de la propriété.  
  
3. Comme un type qui détermine les <xref:System.Windows.Controls.DataGrid>colonnes générées automatiquement dans un .  
  
<a name="binding_state"></a>
## <a name="retrieving-data-binding-information-from-a-binding-expression"></a>Récupération des informations de liaison de données à partir d’une expression de liaison  
 Dans certains cas, vous <xref:System.Windows.Data.BindingExpression> pouvez <xref:System.Windows.Data.Binding> obtenir l’information et avoir besoin d’informations sur la source et les objets cibles de la liaison.  De nouvelles API ont été ajoutées pour vous permettre d’obtenir l’objet source ou cible ou la propriété associée.  Lorsque vous <xref:System.Windows.Data.BindingExpression>avez un , utilisez les API suivantes pour obtenir des informations sur la cible et la source.  
  
|Pour trouver cette valeur de la liaison|Utilisez cette API|  
|---------------------------------------|------------------|  
|Objet cible|<xref:System.Windows.Data.BindingExpressionBase.Target%2A?displayProperty=nameWithType>|  
|Propriété cible|<xref:System.Windows.Data.BindingExpressionBase.TargetProperty%2A?displayProperty=nameWithType>|  
|Objet source|<xref:System.Windows.Data.BindingExpression.ResolvedSource%2A?displayProperty=nameWithType>|  
|Propriété source|<xref:System.Windows.Data.BindingExpression.ResolvedSourcePropertyName%2A?displayProperty=nameWithType>|  
|Si <xref:System.Windows.Data.BindingExpression> l’appartient à un<xref:System.Windows.Data.BindingGroup>|<xref:System.Windows.Data.BindingExpressionBase.BindingGroup%2A?displayProperty=nameWithType>|  
|Le propriétaire d’un<xref:System.Windows.Data.BindingGroup>|<xref:System.Windows.Data.BindingGroup.Owner%2A>|  
  
<a name="DisconnectedSource"></a>
## <a name="checking-for-a-valid-datacontext-object"></a>Vérification d’un objet DataContext valide  
 Il y a <xref:System.Windows.FrameworkElement.DataContext%2A> des cas où le conteneur d’objets dans un <xref:System.Windows.Controls.ItemsControl> devient déconnecté.  Un conteneur d’articles est l’élément <xref:System.Windows.Controls.ItemsControl>d’interface utilisateur qui affiche un élément dans un .  Lorsqu’une <xref:System.Windows.Controls.ItemsControl> donnée est liée à une collection, un conteneur d’objets est généré pour chaque élément. Dans certains cas, les conteneurs d’éléments sont supprimés de l’arborescence d’éléments visuels. Deux cas typiques où un conteneur d’objets est supprimé sont lorsqu’un élément <xref:System.Windows.Controls.ItemsControl>est retiré de la collection sous-jacente et lorsque la virtualisation est activée sur le . Dans ces cas, la <xref:System.Windows.FrameworkElement.DataContext%2A> propriété du conteneur d’objets sera réglée <xref:System.Windows.Data.BindingOperations.DisconnectedSource%2A?displayProperty=nameWithType> à l’objet sentinelle qui est retourné par la propriété statique.  Vous devez vérifier <xref:System.Windows.FrameworkElement.DataContext%2A> si le <xref:System.Windows.Data.BindingOperations.DisconnectedSource%2A> est égal <xref:System.Windows.FrameworkElement.DataContext%2A> à l’objet avant d’accéder à l’élément conteneur.  
  
<a name="live_shaping"></a>
## <a name="repositioning-data-as-the-datas-values-change-live-shaping"></a>Repositionnement des données au fur et à mesure du changement des valeurs des données (mise en forme active)  
 Une collection de données peut être regroupée, triée ou filtrée. WPF 4.5 permet la réorganisation des données lorsque les données sont modifiées. Supposons, par exemple, <xref:System.Windows.Controls.DataGrid> qu’une application utilise un pour répertorier les actions dans un marché boursier et que les actions sont triées par valeur boursière. Si le tri en direct <xref:System.Windows.Data.CollectionView>est activé sur les <xref:System.Windows.Controls.DataGrid> actions», la position d’une action dans les mouvements lorsque la valeur de l’action devient plus ou moins que la valeur d’une autre action.   Pour plus d’informations, voir l’interface. <xref:System.ComponentModel.ICollectionViewLiveShaping>  
  
<a name="weak_event_pattern"></a>
## <a name="improved-support-for-establishing-a-weak-reference-to-an-event"></a>Amélioration de la prise en charge pour l’établissement d’une référence faible à un événement  
 L’implémentation du modèle d’événement faible est désormais plus facile car les abonnés aux événements peuvent y participer sans avoir à implémenter d’interface supplémentaire.  La <xref:System.Windows.WeakEventManager> classe générique permet également aux abonnés de <xref:System.Windows.WeakEventManager> participer au faible modèle d’événement si un dédié n’existe pas pour un certain événement.  Pour plus d’informations, consultez [Modèles d’événement faible](../advanced/weak-event-patterns.md).  
  
<a name="async"></a>
## <a name="new-methods-for-the-dispatcher-class"></a>Nouvelles méthodes pour la classe Dispatcher  
 La classe Dispatcher définit de nouvelles méthodes pour les opérations synchrones et asynchrones.  La <xref:System.Windows.Threading.Dispatcher.Invoke%2A> méthode synchrone définit les surcharges <xref:System.Action> <xref:System.Func%601> qui prennent un ou un paramètre. La nouvelle méthode <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A>asynchrone, , <xref:System.Action> <xref:System.Func%601> prend également un ou <xref:System.Windows.Threading.DispatcherOperation> comme <xref:System.Windows.Threading.DispatcherOperation%601>le paramètre de rappel et retourne un ou .   Les <xref:System.Windows.Threading.DispatcherOperation> <xref:System.Windows.Threading.DispatcherOperation%601> classes et <xref:System.Threading.Tasks.Task> les classes définissent une propriété.  Lorsque vous <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A>appelez, vous `await` pouvez utiliser <xref:System.Windows.Threading.DispatcherOperation> le <xref:System.Threading.Tasks.Task>mot clé avec le ou l’associé . Si vous avez besoin d’attendre avec synchrone pour <xref:System.Threading.Tasks.Task> le qui est retourné par un <xref:System.Windows.Threading.DispatcherOperation> ou <xref:System.Windows.Threading.DispatcherOperation%601>, appelez la méthode d’extension. <xref:System.Windows.Threading.TaskExtensions.DispatcherOperationWait%2A> L’appel <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> entraînera une impasse si l’opération est alignée sur un fil d’appel. Pour plus d’informations sur l’utilisation d’un <xref:System.Threading.Tasks.Task> pour effectuer des opérations asynchrones, voir Le [parallélisme de tâche (Task Parallel Library)](../../../standard/parallel-programming/task-based-asynchronous-programming.md).  
  
<a name="events_markup_extenions"></a>
## <a name="markup-extensions-for-events"></a>Extensions de balisage pour les événements  
 WPF 4.5 prend en charge les extensions de balisage pour les événements.  Bien que WPF ne définisse pas d’extension de balisage à utiliser pour les événements, des tiers sont en mesure de créer une extension de balisage qui peut être utilisée avec les événements.  
  
## <a name="see-also"></a>Voir aussi

- [Quoi de neuf dans le cadre .NET](../../whats-new/index.md)
