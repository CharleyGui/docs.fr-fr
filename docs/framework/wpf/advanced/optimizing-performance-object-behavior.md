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
ms.openlocfilehash: 67184db7fc1459e83ac7b1e6ff09ef56e43f0ca4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187074"
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
 En général, l’accès à <xref:System.Windows.DependencyObject> une propriété de dépendance d’a n’est pas plus lent que d’accéder à une propriété CLR. Tandis qu’il y a une petite tête-d’œil de performance pour fixer une valeur de propriété, obtenir une valeur est aussi rapide que d’obtenir la valeur d’une propriété de CLR. La légère baisse des performances s’explique par le fait que les propriétés de dépendance prennent en charge des fonctionnalités robustes, comme la liaison de données, l’animation, l’héritage et les styles. Pour plus d’informations, consultez [Vue d’ensemble des propriétés de dépendance](dependency-properties-overview.md).  
  
### <a name="dependencyproperty-optimizations"></a>Optimisations de DependencyProperty  
 Vous devez soigneusement définir les propriétés de dépendance dans votre application. Si <xref:System.Windows.DependencyProperty> vos effets ne rendent que les options de métadonnées de type, plutôt que d’autres options de métadonnées telles que <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A>, vous devriez le marquer en tant que tel en l’emportent sur ses métadonnées. Pour plus d’informations sur la substitution ou l’obtention de métadonnées de propriété, consultez [Métadonnées de propriété de dépendance](dependency-property-metadata.md).  
  
 Il peut être plus efficace d’avoir un gestionnaire de changement de propriété qui invalide manuellement les passes de mesure, d’organisation et d’affichage si tous les changements de propriété n’affectent pas réellement la mesure, l’organisation et l’affichage. Par exemple, vous pouvez décider de réafficher un arrière-plan uniquement quand une valeur est supérieure à une limite définie. Dans ce cas, votre gestionnaire de changement de propriété invalide l’affichage uniquement quand la valeur dépasse la limite définie.  
  
### <a name="making-a-dependencyproperty-inheritable-is-not-free"></a>Rendre une propriété de dépendance héritable n’est pas gratuit  
 Par défaut, les propriétés de dépendance inscrites ne sont pas héritables. Toutefois, vous pouvez explicitement rendre une propriété héritable. Bien qu’il s’agisse d’une fonctionnalité utile, la conversion d’une propriété pour qu’elle soit héritable affecte les performances en augmentant la durée d’invalidation de la propriété.  
  
### <a name="use-registerclasshandler-carefully"></a>Utiliser RegisterClassHandler avec précaution  
 Bien <xref:System.Windows.EventManager.RegisterClassHandler%2A> que l’appel vous permet d’enregistrer votre état d’instance, il est important d’être conscient que le gestionnaire est appelé sur chaque cas, ce qui peut causer des problèmes de performance. Utilisez <xref:System.Windows.EventManager.RegisterClassHandler%2A> uniquement lorsque votre application exige que vous enregistrez votre état d’instance.  
  
### <a name="set-the-default-value-for-a-dependencyproperty-during-registration"></a>Définir la valeur par défaut d’une propriété DependencyProperty pendant l’inscription  
 Lors de <xref:System.Windows.DependencyProperty> la création d’un qui nécessite une valeur par défaut, <xref:System.Windows.DependencyProperty.Register%2A> définissez <xref:System.Windows.DependencyProperty>la valeur à l’aide des métadonnées par défaut transmises comme un paramètre à la méthode de la . Utilisez cette technique au lieu de définir la valeur de propriété dans un constructeur ou sur chaque instance d’un élément.  
  
### <a name="set-the-propertymetadata-value-using-register"></a>Définir la valeur PropertyMetadata à l’aide du Registre  
 Lors de <xref:System.Windows.DependencyProperty>la création d’un <xref:System.Windows.PropertyMetadata> , <xref:System.Windows.DependencyProperty.Register%2A> vous <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> avez la possibilité de définir l’utilisation ou les méthodes. Bien que votre objet pourrait avoir <xref:System.Windows.DependencyProperty.OverrideMetadata%2A>un constructeur statique à appeler, ce n’est pas la solution optimale et aura un impact sur les performances. Pour les meilleures <xref:System.Windows.PropertyMetadata> performances, définissez le pendant l’appel à <xref:System.Windows.DependencyProperty.Register%2A>.  
  
<a name="Freezable_Objects"></a>
## <a name="freezable-objects"></a>Objets Freezable  
 A <xref:System.Windows.Freezable> est un type spécial d’objet qui a deux états: non gelé et congelé. Le fait de figer les objets chaque fois que cela est possible améliore les performances de votre application et réduit son jeu de travail. Pour plus d’informations, consultez [Vue d’ensemble des objets Freezable](freezable-objects-overview.md).  
  
 Chacun <xref:System.Windows.Freezable> a <xref:System.Windows.Freezable.Changed> un événement qui est soulevé chaque fois qu’il change. Toutefois, les notifications de changement détériorent les performances de l’application.  
  
 Prenons l’exemple suivant <xref:System.Windows.Shapes.Rectangle> dans <xref:System.Windows.Media.Brush> lequel chacun utilise le même objet :  
  
 [!code-csharp[Performance#PerformanceSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet2)]
 [!code-vb[Performance#PerformanceSnippet2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet2)]  
  
 Par [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] défaut, fournit un <xref:System.Windows.Media.SolidColorBrush> gestionnaire d’événement pour l’événement de <xref:System.Windows.Freezable.Changed> l’objet afin d’invalider la propriété de <xref:System.Windows.Shapes.Rectangle> <xref:System.Windows.Shapes.Shape.Fill%2A> l’objet. Dans ce cas, <xref:System.Windows.Media.SolidColorBrush> chaque fois <xref:System.Windows.Freezable.Changed> que le doit congédier son <xref:System.Windows.Shapes.Rectangle>événement, il est nécessaire d’invoquer la fonction de rappel pour chacun — l’accumulation de ces invocations de fonction de rappel imposent une pénalité de rendement importante. Par ailleurs, l’ajout et la suppression des gestionnaires à ce stade consomment une grande part des performances, car cette opération oblige l’application à parcourir l’intégralité de la liste. Si votre scénario de <xref:System.Windows.Media.SolidColorBrush>demande ne change jamais le <xref:System.Windows.Freezable.Changed> , vous paiera le coût de l’entretien des gestionnaires d’événements inutilement.  
  
 Le <xref:System.Windows.Freezable> gel d’un peut améliorer ses performances, car il n’a plus besoin de dépenser des ressources sur le maintien des notifications de changement. Le tableau ci-dessous montre <xref:System.Windows.Media.SolidColorBrush> la <xref:System.Windows.Freezable.IsFrozen%2A> taille d’un simple lorsque sa propriété est définie à `true`, par rapport à quand il n’est pas. Cela suppose l’application <xref:System.Windows.Shapes.Shape.Fill%2A> d’un <xref:System.Windows.Shapes.Rectangle> pinceau à la propriété de dix objets.  
  
|**État**|**Taille**|  
|---------------|--------------|  
|La Reine des neiges<xref:System.Windows.Media.SolidColorBrush>|212 octets|  
|Non congelé<xref:System.Windows.Media.SolidColorBrush>|972 octets|  
  
 L'exemple de code suivant illustre ce concept :  
  
 [!code-csharp[Performance#PerformanceSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet3)]
 [!code-vb[Performance#PerformanceSnippet3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet3)]  
  
### <a name="changed-handlers-on-unfrozen-freezables-may-keep-objects-alive"></a>Les gestionnaires de changement sur des Freezables non figés peuvent conserver les objets actifs  
 Le délégué qu’un <xref:System.Windows.Freezable> objet passe <xref:System.Windows.Freezable.Changed> à l’événement d’un objet est en fait une référence à cet objet. Par <xref:System.Windows.Freezable.Changed> conséquent, les gestionnaires d’événements peuvent garder les objets en vie plus longtemps que prévu. Lors du nettoyage d’un objet qui <xref:System.Windows.Freezable> s’est <xref:System.Windows.Freezable.Changed> inscrit pour écouter l’événement d’un objet, il est essentiel de supprimer ce délégué avant de libérer l’objet.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]connecte également <xref:System.Windows.Freezable.Changed> les événements en interne. Par exemple, toutes les <xref:System.Windows.Freezable> propriétés de <xref:System.Windows.Freezable.Changed> dépendance qui prennent comme valeur écouteront automatiquement les événements. La <xref:System.Windows.Shapes.Shape.Fill%2A> propriété, qui <xref:System.Windows.Media.Brush>prend un , illustre ce concept.  
  
 [!code-csharp[Performance#PerformanceSnippet4](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet4)]
 [!code-vb[Performance#PerformanceSnippet4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet4)]  
  
 Sur la `myBrush` cession `myRectangle.Fill`de , un <xref:System.Windows.Shapes.Rectangle> délégué pointant vers <xref:System.Windows.Media.SolidColorBrush> l’objet sera ajouté à l’événement de <xref:System.Windows.Freezable.Changed> l’objet. Cela signifie que le code suivant ne rend pas `myRect` éligible pour l’opération de garbage collection :  
  
 [!code-csharp[Performance#PerformanceSnippet5](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet5)]
 [!code-vb[Performance#PerformanceSnippet5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet5)]  
  
 Dans ce `myBrush` cas, `myRectangle` est toujours en cours et <xref:System.Windows.Freezable.Changed> rappellera à elle quand il tire son événement. Notez que `myBrush` l’attribution à la <xref:System.Windows.Shapes.Shape.Fill%2A> propriété d’un nouveau <xref:System.Windows.Shapes.Rectangle> va simplement ajouter un autre gestionnaire d’événements à `myBrush`.  
  
 La façon recommandée de nettoyer ces types <xref:System.Windows.Media.Brush> d’objets est de retirer la <xref:System.Windows.Shapes.Shape.Fill%2A> propriété, ce qui enlèvera à son tour le gestionnaire d’événements. <xref:System.Windows.Freezable.Changed>  
  
 [!code-csharp[Performance#PerformanceSnippet6](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet6)]
 [!code-vb[Performance#PerformanceSnippet6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet6)]  
  
<a name="User_Interface_Virtualization"></a>
## <a name="user-interface-virtualization"></a>Virtualisation de l'interface utilisateur  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]fournit également une <xref:System.Windows.Controls.StackPanel> variante de l’élément qui « virtualise » automatiquement le contenu de l’enfant lié aux données. Dans ce contexte, le mot virtualiser fait référence à une technique par laquelle une partie des objets est généré à partir d’un plus grand nombre d’éléments de données en fonction des éléments visibles à l’écran. La génération d’un grand nombre d'éléments d'interface utilisateur, alors que seul un certain nombre de ces éléments peut figurer à l'écran à un moment donné, entraîne une utilisation intensive de la mémoire et du processeur. <xref:System.Windows.Controls.VirtualizingStackPanel>(grâce à la <xref:System.Windows.Controls.VirtualizingPanel>fonctionnalité fournie par ) <xref:System.Windows.Controls.ItemContainerGenerator> calcule <xref:System.Windows.Controls.ItemsControl> les <xref:System.Windows.Controls.ListBox> éléments <xref:System.Windows.Controls.ListView>visibles et fonctionne avec le d’un (tel ou ) pour créer seulement des éléments pour les éléments visibles.  
  
 Pour optimiser les performances, des objets visuels pour ces éléments sont générés ou maintenus actifs uniquement s’ils sont visibles à l’écran. Quand ils ne sont plus dans la zone visible du contrôle, les objets visuels peuvent être supprimés. Cette virtualisation ne doit pas être confondue avec la virtualisation des données, où les objets de données ne sont pas tous présents dans la collection locale, mais diffusés selon les besoins.  
  
 Le tableau ci-dessous montre le temps écoulé ajoutant et <xref:System.Windows.Controls.TextBlock> rendant <xref:System.Windows.Controls.StackPanel> 5000 éléments à un et un <xref:System.Windows.Controls.VirtualizingStackPanel>. Dans ce scénario, les mesures représentent le temps entre <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> l’attachement d’une chaîne de texte à la propriété d’un <xref:System.Windows.Controls.ItemsControl> objet à l’heure où les éléments du panneau affichent la chaîne de texte.  
  
|**Panneau hôte**|**Temps d’affichage (ms)**|  
|--------------------|----------------------------|  
|<xref:System.Windows.Controls.StackPanel>|3210|  
|<xref:System.Windows.Controls.VirtualizingStackPanel>|46|  
  
## <a name="see-also"></a>Voir aussi

- [Optimisation des performances des applications WPF](optimizing-wpf-application-performance.md)
- [Planification des performances des applications](planning-for-application-performance.md)
- [Tirer parti du matériel](optimizing-performance-taking-advantage-of-hardware.md)
- [Disposition et conception](optimizing-performance-layout-and-design.md)
- [Graphisme 2D et acquisition d’images](optimizing-performance-2d-graphics-and-imaging.md)
- [Ressources d’application](optimizing-performance-application-resources.md)
- [Texte](optimizing-performance-text.md)
- [Liaison de données](optimizing-performance-data-binding.md)
- [Autres recommandations relatives aux performances](optimizing-performance-other-recommendations.md)
