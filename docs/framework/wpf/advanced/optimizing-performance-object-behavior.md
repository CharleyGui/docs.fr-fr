---
title: "Optimisation des performances : comportement d'objets"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- user interface virtualization [WPF]
- dependency properties [WPF], performance
- event handlers [WPF]
- object performance considerations [WPF]
- Freezable objects [WPF], performance
ms.assetid: 73aa2f47-1d73-439a-be1f-78dc4ba2b5bd
ms.openlocfilehash: 64e567cd28e9458b483b0963e0dedd924ad23bab
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094486"
---
# <a name="optimizing-performance-object-behavior"></a>Optimisation des performances : comportement d'objets
Une bonne compréhension du comportement intrinsèque des objets [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vous permet de choisir le bon compromis entre fonctionnalités et performances.  

<a name="Not_Removing_Event_Handlers"></a>   
## <a name="not-removing-event-handlers-on-objects-may-keep-objects-alive"></a>Le fait de ne pas supprimer les gestionnaires d’événements sur les objets permet de conserver les objets actifs  
 Le délégué qu’un objet passe à son événement est une référence à cet objet. Par conséquent, les gestionnaires d’événements peuvent conserver les objets actifs plus longtemps que prévu. Quand vous nettoyez un objet inscrit pour détecter l’événement d’un objet, il est essentiel de supprimer ce délégué avant de libérer l’objet. La conservation d’objets actifs inutiles augmente l’utilisation de mémoire de l’application. Cela est particulièrement vrai quand l’objet est la racine d’une arborescence logique ou d’une arborescence de visuels.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] introduit un modèle de détecteur d’événements faibles qui peut être utile quand les relations de durée de vie d’objet entre la source et l’écouteur sont difficiles à suivre. Certains événements [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] existants utilisent ce modèle. Si vous implémentez des objets avec des événements personnalisés, ce modèle peut vous être utile. Pour plus d’informations, consultez [Modèles d’événement faible](weak-event-patterns.md).  
  
 Il existe plusieurs outils, comme le profileur CLR et la visionneuse de jeux de travail, qui peuvent fournir des informations sur l’utilisation de mémoire d’un processus spécifié. Le profileur CLR inclut un nombre de vues très utiles du profil d’allocation, notamment un histogramme des types alloués, des graphiques d’allocation et d’appels, une chronologie montrant les opérations de garbage collection de diverses générations et l’état obtenu du tas managé après ces collections, ainsi qu’une arborescence des appels présentant les allocations par méthode et les chargements d’assembly. Pour plus d’informations, consultez [Performances](https://docs.microsoft.com/previous-versions/aa497289(v=msdn.10)).  
  
<a name="DPs_and_Objects"></a>   
## <a name="dependency-properties-and-objects"></a>Propriétés de dépendance et objets  
 En général, l’accès à une propriété de dépendance d’un <xref:System.Windows.DependencyObject> n’est pas plus lent que l’accès à une propriété CLR. Bien qu’il existe une petite surcharge de performances pour la définition d’une valeur de propriété, l’obtention d’une valeur est aussi rapide que l’obtention de la valeur d’une propriété CLR. La légère baisse des performances s’explique par le fait que les propriétés de dépendance prennent en charge des fonctionnalités robustes, comme la liaison de données, l’animation, l’héritage et les styles. Pour plus d’informations, consultez [Vue d’ensemble des propriétés de dépendance](dependency-properties-overview.md).  
  
### <a name="dependencyproperty-optimizations"></a>Optimisations de DependencyProperty  
 Vous devez soigneusement définir les propriétés de dépendance dans votre application. Si votre <xref:System.Windows.DependencyProperty> affecte uniquement les options de métadonnées de type Render, plutôt que d’autres options de métadonnées telles que <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A>, vous devez la marquer comme telle en remplaçant ses métadonnées. Pour plus d’informations sur la substitution ou l’obtention de métadonnées de propriété, consultez [Métadonnées de propriété de dépendance](dependency-property-metadata.md).  
  
 Il peut être plus efficace d’avoir un gestionnaire de changement de propriété qui invalide manuellement les passes de mesure, d’organisation et d’affichage si tous les changements de propriété n’affectent pas réellement la mesure, l’organisation et l’affichage. Par exemple, vous pouvez décider de réafficher un arrière-plan uniquement quand une valeur est supérieure à une limite définie. Dans ce cas, votre gestionnaire de changement de propriété invalide l’affichage uniquement quand la valeur dépasse la limite définie.  
  
### <a name="making-a-dependencyproperty-inheritable-is-not-free"></a>Rendre une propriété de dépendance héritable n’est pas gratuit  
 Par défaut, les propriétés de dépendance inscrites ne sont pas héritables. Toutefois, vous pouvez explicitement rendre une propriété héritable. Bien qu’il s’agisse d’une fonctionnalité utile, la conversion d’une propriété pour qu’elle soit héritable affecte les performances en augmentant la durée d’invalidation de la propriété.  
  
### <a name="use-registerclasshandler-carefully"></a>Utiliser RegisterClassHandler avec précaution  
 Quand vous appelez <xref:System.Windows.EventManager.RegisterClassHandler%2A> vous permet d’enregistrer l’état de votre instance, il est important de savoir que le gestionnaire est appelé sur chaque instance, ce qui peut entraîner des problèmes de performances. Utilisez uniquement <xref:System.Windows.EventManager.RegisterClassHandler%2A> lorsque votre application nécessite l’enregistrement de l’état de votre instance.  
  
### <a name="set-the-default-value-for-a-dependencyproperty-during-registration"></a>Définir la valeur par défaut d’une propriété DependencyProperty pendant l’inscription  
 Lorsque vous créez un <xref:System.Windows.DependencyProperty> qui requiert une valeur par défaut, définissez la valeur à l’aide des métadonnées par défaut passées en tant que paramètre à la méthode <xref:System.Windows.DependencyProperty.Register%2A> de l' <xref:System.Windows.DependencyProperty>. Utilisez cette technique au lieu de définir la valeur de propriété dans un constructeur ou sur chaque instance d’un élément.  
  
### <a name="set-the-propertymetadata-value-using-register"></a>Définir la valeur PropertyMetadata à l’aide du Registre  
 Lorsque vous créez un <xref:System.Windows.DependencyProperty>, vous avez la possibilité de définir le <xref:System.Windows.PropertyMetadata> à l’aide des méthodes <xref:System.Windows.DependencyProperty.Register%2A> ou <xref:System.Windows.DependencyProperty.OverrideMetadata%2A>. Bien que votre objet puisse avoir un constructeur statique pour appeler <xref:System.Windows.DependencyProperty.OverrideMetadata%2A>, il ne s’agit pas de la solution optimale et aura un impact sur les performances. Pour des performances optimales, définissez la <xref:System.Windows.PropertyMetadata> lors de l’appel à <xref:System.Windows.DependencyProperty.Register%2A>.  
  
<a name="Freezable_Objects"></a>   
## <a name="freezable-objects"></a>Objets Freezable  
 Un <xref:System.Windows.Freezable> est un type spécial d’objet qui a deux États : non figé et figé. Le fait de figer les objets chaque fois que cela est possible améliore les performances de votre application et réduit son jeu de travail. Pour plus d’informations, consultez [Vue d’ensemble des objets Freezable](freezable-objects-overview.md).  
  
 Chaque <xref:System.Windows.Freezable> a un événement <xref:System.Windows.Freezable.Changed> qui est déclenché chaque fois qu’il change. Toutefois, les notifications de changement détériorent les performances de l’application.  
  
 Prenons l’exemple suivant dans lequel chaque <xref:System.Windows.Shapes.Rectangle> utilise le même objet <xref:System.Windows.Media.Brush> :  
  
 [!code-csharp[Performance#PerformanceSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet2)]
 [!code-vb[Performance#PerformanceSnippet2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet2)]  
  
 Par défaut, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit un gestionnaire d’événements pour l’événement <xref:System.Windows.Freezable.Changed> de l’objet <xref:System.Windows.Media.SolidColorBrush> afin d’invalider la propriété <xref:System.Windows.Shapes.Shape.Fill%2A> de l’objet <xref:System.Windows.Shapes.Rectangle>. Dans ce cas, chaque fois que l' <xref:System.Windows.Media.SolidColorBrush> doit déclencher son événement <xref:System.Windows.Freezable.Changed>, il est nécessaire d’appeler la fonction de rappel pour chaque <xref:System.Windows.Shapes.Rectangle>. l’accumulation de ces appels de fonction de rappel entraîne une baisse significative des performances. Par ailleurs, l’ajout et la suppression des gestionnaires à ce stade consomment une grande part des performances, car cette opération oblige l’application à parcourir l’intégralité de la liste. Si votre scénario d’application ne modifie jamais le <xref:System.Windows.Media.SolidColorBrush>, vous payez le coût de la maintenance des gestionnaires d’événements <xref:System.Windows.Freezable.Changed> inutilement.  
  
 Le gel d’un <xref:System.Windows.Freezable> peut améliorer ses performances, car il n’a plus besoin d’étendre des ressources sur la gestion des notifications de modifications. Le tableau ci-dessous montre la taille d’un <xref:System.Windows.Media.SolidColorBrush> simple lorsque sa propriété <xref:System.Windows.Freezable.IsFrozen%2A> a la valeur `true`, par rapport à quand ce n’est pas le cas. Cela suppose l’application d’un pinceau à la propriété <xref:System.Windows.Shapes.Shape.Fill%2A> de dix objets <xref:System.Windows.Shapes.Rectangle>.  
  
|**State**|**Taille**|  
|---------------|--------------|  
|<xref:System.Windows.Media.SolidColorBrush> figé|212 octets|  
|<xref:System.Windows.Media.SolidColorBrush> non figé|972 octets|  
  
 L'exemple de code suivant illustre ce concept :  
  
 [!code-csharp[Performance#PerformanceSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet3)]
 [!code-vb[Performance#PerformanceSnippet3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet3)]  
  
### <a name="changed-handlers-on-unfrozen-freezables-may-keep-objects-alive"></a>Les gestionnaires de changement sur des Freezables non figés peuvent conserver les objets actifs  
 Le délégué qu’un objet passe à l’événement <xref:System.Windows.Freezable.Changed> d’un objet <xref:System.Windows.Freezable> est effectivement une référence à cet objet. Par conséquent, <xref:System.Windows.Freezable.Changed> gestionnaires d’événements peuvent conserver les objets actifs plus longtemps que prévu. Lorsque vous effectuez le nettoyage d’un objet qui s’est inscrit pour écouter l’événement <xref:System.Windows.Freezable.Changed> d’un objet <xref:System.Windows.Freezable>, il est essentiel de supprimer ce délégué avant de libérer l’objet.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] raccorde également les événements <xref:System.Windows.Freezable.Changed> en interne. Par exemple, toutes les propriétés de dépendance qui acceptent <xref:System.Windows.Freezable> comme valeur écoutent automatiquement les événements <xref:System.Windows.Freezable.Changed>. La propriété <xref:System.Windows.Shapes.Shape.Fill%2A>, qui prend un <xref:System.Windows.Media.Brush>, illustre ce concept.  
  
 [!code-csharp[Performance#PerformanceSnippet4](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet4)]
 [!code-vb[Performance#PerformanceSnippet4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet4)]  
  
 Lors de l’assignation de `myBrush` à `myRectangle.Fill`, un délégué qui pointe vers l’objet <xref:System.Windows.Shapes.Rectangle> sera ajouté à l’événement <xref:System.Windows.Freezable.Changed> de l’objet <xref:System.Windows.Media.SolidColorBrush>. Cela signifie que le code suivant ne rend pas `myRect` éligible pour l’opération de garbage collection :  
  
 [!code-csharp[Performance#PerformanceSnippet5](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet5)]
 [!code-vb[Performance#PerformanceSnippet5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet5)]  
  
 Dans ce cas `myBrush` conserve toujours `myRectangle` actif et le rappelle lorsqu’il déclenche son événement <xref:System.Windows.Freezable.Changed>. Notez que l’affectation de `myBrush` à la propriété <xref:System.Windows.Shapes.Shape.Fill%2A> d’un nouveau <xref:System.Windows.Shapes.Rectangle> ajoutera simplement un autre gestionnaire d’événements à `myBrush`.  
  
 La méthode recommandée pour nettoyer ces types d’objets consiste à supprimer le <xref:System.Windows.Media.Brush> de la propriété <xref:System.Windows.Shapes.Shape.Fill%2A>, ce qui a pour conséquence de supprimer le gestionnaire d’événements <xref:System.Windows.Freezable.Changed>.  
  
 [!code-csharp[Performance#PerformanceSnippet6](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet6)]
 [!code-vb[Performance#PerformanceSnippet6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet6)]  
  
<a name="User_Interface_Virtualization"></a>   
## <a name="user-interface-virtualization"></a>Virtualisation de l'interface utilisateur  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit également une variante de l’élément <xref:System.Windows.Controls.StackPanel> qui « virtualise » automatiquement le contenu enfant lié aux données. Dans ce contexte, le mot virtualiser fait référence à une technique par laquelle une partie des objets est généré à partir d’un plus grand nombre d’éléments de données en fonction des éléments visibles à l’écran. La génération d’un grand nombre d’éléments d’interface utilisateur, alors que seul un certain nombre de ces éléments peut figurer à l’écran à un moment donné, entraîne une utilisation intensive de la mémoire et du processeur. <xref:System.Windows.Controls.VirtualizingStackPanel> (via la fonctionnalité fournie par <xref:System.Windows.Controls.VirtualizingPanel>) calcule les éléments visibles et fonctionne avec le <xref:System.Windows.Controls.ItemContainerGenerator> à partir d’un <xref:System.Windows.Controls.ItemsControl> (tel que <xref:System.Windows.Controls.ListBox> ou <xref:System.Windows.Controls.ListView>) pour créer uniquement des éléments pour les éléments visibles.  
  
 Pour optimiser les performances, des objets visuels pour ces éléments sont générés ou maintenus actifs uniquement s’ils sont visibles à l’écran. Quand ils ne sont plus dans la zone visible du contrôle, les objets visuels peuvent être supprimés. Cette virtualisation ne doit pas être confondue avec la virtualisation des données, où les objets de données ne sont pas tous présents dans la collection locale, mais diffusés selon les besoins.  
  
 Le tableau ci-dessous montre le temps écoulé pour l’ajout et le rendu des éléments de <xref:System.Windows.Controls.TextBlock> 5000 sur un <xref:System.Windows.Controls.StackPanel> et un <xref:System.Windows.Controls.VirtualizingStackPanel>. Dans ce scénario, les mesures représentent le temps entre l’attachement d’une chaîne de texte à la propriété <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> d’un objet <xref:System.Windows.Controls.ItemsControl> à l’heure à laquelle les éléments de panneau affichent la chaîne de texte.  
  
|**Panneau hôte**|**Durée d’affichage (ms)**|  
|--------------------|----------------------------|  
|<xref:System.Windows.Controls.StackPanel>|3210|  
|<xref:System.Windows.Controls.VirtualizingStackPanel>|46|  
  
## <a name="see-also"></a>Voir aussi

- [Optimisation des performances des applications WPF](optimizing-wpf-application-performance.md)
- [Planification des performances des applications](planning-for-application-performance.md)
- [Tirer parti du matériel](optimizing-performance-taking-advantage-of-hardware.md)
- [Disposition et conception](optimizing-performance-layout-and-design.md)
- [Graphiques 2D et acquisition d'images](optimizing-performance-2d-graphics-and-imaging.md)
- [Ressources d’application](optimizing-performance-application-resources.md)
- [Text](optimizing-performance-text.md)
- [Liaison de données](optimizing-performance-data-binding.md)
- [Autres recommandations relatives aux performances](optimizing-performance-other-recommendations.md)
